---
title: Microsoft Intune で SCEP にサード パーティの CA を使用する - Azure | Microsoft Docs
description: Microsoft Intune では、ベンダーまたはサード パーティの証明機関 (CA) を追加し、SCEP プロトコルを使ってモバイル デバイスに証明書を発行することができます。 この概要では、Azure Active Directory (Azure AD) アプリケーションが、証明書を検証するアクセス許可を Microsoft Intune に付与します。 その後、SCEP サーバーのセットアップに含まれる AAD アプリケーションのアプリケーション ID、認証キー、テナント ID を使って、証明書を発行します。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 07/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ee5a39ee8a146fbc6a85a9f4438b8e14a408a735
ms.sourcegitcommit: e8e8164586508f94704a09c2e27950fe6ff184c3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/27/2018
ms.locfileid: "39321728"
---
# <a name="add-partner-certification-authority-in-intune-using-scep"></a>SCEP を使用して Intune でパートナーの証明機関を追加する

Microsoft Intune では、サード パーティの証明機関 (CA) を追加できます。 これらの CA は、Simple Certificate Enrollment Protocol (SCEP) を使ってモバイル デバイスに証明書を提供できます。 この機能は、Windows、iOS、Android、macOS デバイスで新しい証明書を発行し、証明書を更新することができます。

この機能の使用には、オープン ソース API と Intune 管理者タスクの 2 つの部分があります。

**パート 1 - オープン ソース API を使用する**  
Microsoft が作成した API は、Intune と統合して、証明書を検証し、成功または失敗の通知を送信し、SSL (具体的には SSL ソケット ファクトリ) を使って Intune と通信します。

この API は、[Intune SCEP API パブリック GitHub リポジトリ](http://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)からダウンロードして、ソリューションで使用できます。 この API をサード パーティの SCEP サーバーで使って、証明書をデバイスに提供する前に、Intune に対してカスタム チャレンジの検証を実行します。

[Intune SCEP 管理ソリューションとの統合](scep-libraries-apis.md)に関するページでは、API の使用、そのメソッド、作成したソリューションのテストに関して、さらに詳しく説明されています。

**パート 2 - アプリケーションとプロファイルを作成する**  
Azure Active Directory (Azure AD) アプリケーションを使って、デバイスから受け取った SCEP 要求を処理する権限を Intune に委任できます。 Azure AD アプリケーションに含まれるアプリケーション ID と認証キーの値を、開発者が作成する API ソリューション内で使います。 その後、管理者は Intune を使って、SCEP 証明書プロファイルを作成して展開できます。 また、デバイスでの展開の状態に関するレポートを見ることもできます。

この記事では、Azure AD アプリケーションの作成など、この機能の概要を管理者の観点から説明します。

## <a name="overview"></a>概要

以下の手順では、Intune での SCEP 証明書の発行の概要を示します。

1. 管理者が、Intune で SCEP 証明書プロファイルを作成して、ユーザーまたはデバイスをプロファイルの対象にします。
2. デバイスが Intune にチェックインします。
3. Intune が、一意の SCEP チャレンジを作成します。 また、他の整合性チェックの情報 (予想されるサブジェクトや必要な SAN など) も追加します。
4. Intune が、チャレンジと整合性チェックの情報を暗号化して署名し、この情報を SCEP 要求でデバイスに送信します。
5. デバイスが、Intune からプッシュされた SCEP 証明書プロファイルに基づいて、証明書署名要求 (CSR) とデバイスでの公開/秘密キー ペアを生成します。
6. CSR と暗号化/署名されたチャレンジが、サード パーティの SCEP サーバー エンドポイントに送信されます。
7. SCEP サーバーが、Intune に CSR とチャレンジを送信します。 Intune が署名を検証し、ペイロードを解読して、CSR を整合性チェック情報と比較します。
8. Intune が SCEP サーバーに応答を送り返し、チャレンジの検証が成功したかどうかを示します。  
9. チャレンジの検証が成功した場合、SCEP サーバーはデバイスに証明書を発行します。

次の図では、サード パーティの SCEP と Intune の統合の詳細なフローを示します。

![サード パーティの SCEP 証明機関を Microsoft Intune に統合する方法](./media/scep-certificate-vendor-integration.png)

## <a name="set-up-third-party-ca-integration"></a>サード パーティの CA の統合をセットアップする

### <a name="validate-third-party-certification-authority"></a>サード パーティの証明機関を検証する

サード パーティの証明機関を Intune と統合する前に、使っている CA が Intune をサポートすることを確認します。 「[サード パーティの証明機関パートナー](#third-party-certification-authority-partners)」 (この記事) に一覧が含まれています。 証明機関のガイダンスで詳細を確認することもできます。 CA には、その実装に固有のセットアップ手順が含まれることがあります。

### <a name="authorize-communication-between-ca-and-intune"></a>CA と Intune の間の通信を承認する

サード パーティの SCEP サーバーが Intune でカスタム チャレンジの検証を実行できるようにするには、Azure AD でアプリを作成します。 このアプリは、SCEP 要求を検証する権限を Intune に委任します。

Azure AD アプリを登録するのに必要なアクセス許可があることを確認してください。 「[必要なアクセス許可](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal#required-permissions)」で手順が示されています。

**ステップ 1: Azure AD アプリケーションを作成する**

1. [Azure ポータル](https://portal.azure.com)にサインインします。
2. **[Azure Active Directory]** > **[アプリの登録]** > **[新しいアプリケーションの登録]** の順に選択します。
3. 名前とサインオン URL を入力します。 アプリケーションの種類として **[Web アプリ/API]** を選択します。
4. **[作成]** を選択します。

URL と名前に関するヒントなど、アプリ作成のガイダンスについては、「[Azure Active Directory とアプリケーションの統合](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications)」をご覧ください。

**ステップ 2: アクセス許可を付与する**

アプリケーションを作成した後、Microsoft Intune API に必要なアクセス許可を付与します。

1. Azure AD アプリで、**[設定]** > **[必要なアクセス許可]** を開きます。  
2. **[追加]** > **[API を選択します]** を選択し、**[Microsoft Intune API]** > **[選択]** を選択します。
3. **[アクセス許可の選択]** で、**[SCEP challenge validation]\(SCEP チャレンジの検証\)** > **[選択]** を選択します。
4. **[完了]** を選択して変更を保存します。

**ステップ 3: アプリケーション ID と認証キーを取得する**

次に、Azure AD アプリケーションの ID とキーの値を取得します。 次の値が必要です。

- アプリケーション ID
- 認証キー
- テナント ID

**アプリケーション ID と認証キーを取得するには**:

1. Azure AD で、新しいアプリケーションを選択します (**[アプリの登録]**)。
2. **[アプリケーション ID]** をコピーし、アプリケーションのコードに格納します。
3. 次に、認証キーを生成します。 Azure AD アプリで、**[設定]** > **[キー]** を開きます。
4. **[パスワード]** で、説明を入力し、キーの有効期間を選択します。 変更内容を**保存**します。 示されている値をコピーして保存します。

    > [!IMPORTANT]
    > 1 回しか表示されないので、すぐにそのキーをコピーして保存します。 このキーの値は、サード パーティの CA の実装で必要です。 サード パーティのガイダンスで、アプリケーション ID、認証キー、テナント ID の必要な構成方法を確認してください。

**テナント ID** は、アカウントで @ 記号の後にあるドメイン テキストです。 たとえば、アカウントが `admin@name.onmicrosoft.com` の場合、テナント ID は **name.onmicrosoft.com** です。

これらの値を取得する手順および Azure AD アプリの詳細については、「[アプリケーション ID と認証キーを取得する](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal#get-application-id-and-authentication-key)」をご覧ください。

### <a name="configure-and-deploy-a-scep-certificate-profile"></a>SCEP 証明書プロファイルを構成して展開する
管理者として、SCEP 証明書プロファイルを作成し、ユーザーまたはデバイスを対象にします。 次に、プロファイルを割り当てます。

- [SCEP 証明書プロファイルを作成する](certificates-scep-configure.md#create-a-scep-certificate-profile)

- [証明書プロファイルを割り当てる](certificates-scep-configure.md#assign-the-certificate-profile)

## <a name="removing-certificates"></a>証明書の削除

デバイスを登録解除またはワイプすると、証明書は削除されます。 証明書が取り消されることはありません。

## <a name="third-party-certification-authority-partners"></a>サード パーティの証明機関パートナー
次のサード パーティ証明機関が Intune をサポートしています。

- [Entrust Datacard](http://www.entrustdatacard.com/resource-center/documents/documentation)

自社の製品と Intune の統合に関心をお持ちのサード パーティ CA は、API のガイダンスを確認してください。

- [Intune SCEP API の GitHub リポジトリ](http://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)
- [サード パーティ CA 向けの Intune SCEP API ガイダンス](scep-libraries-apis.md)

## <a name="see-also"></a>関連項目

- [証明書プロファイルを構成する](certificates-scep-configure.md)
- [Intune SCEP API の GitHub リポジトリ](http://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)
- [サード パーティ CA 向けの Intune SCEP API ガイダンス](scep-libraries-apis.md)
