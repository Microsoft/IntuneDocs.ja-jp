---
title: Microsoft Intune で SCEP にサード パーティの証明機関 (CA) を使用する - Azure | Microsoft Docs
description: Microsoft Intune では、ベンダーまたはサード パーティの証明機関 (CA) を追加し、SCEP プロトコルを使ってモバイル デバイスに証明書を発行することができます。 この概要では、Azure Active Directory (Azure AD) アプリケーションが、証明書を検証するアクセス許可を Microsoft Intune に付与します。 その後、SCEP サーバーのセットアップに含まれる AAD アプリケーションのアプリケーション ID、認証キー、テナント ID を使って、証明書を発行します。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 61771ce2b6179b2e74a4d13f72794ece97907034
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502574"
---
# <a name="add-partner-certification-authority-in-intune-using-scep"></a>SCEP を使用して Intune でパートナーの証明機関を追加する

Intune でサード パーティの証明機関 (CA) を使用します。 サード パーティの CA では、Simple Certificate Enrollment Protocol (SCEP) を使って新しい証明書または更新された証明書でモバイル デバイスをプロビジョニングすることができ、Windows、iOS、Android、macOS のデバイスをサポートできます。

この機能の使用には、オープン ソース API と Intune 管理者タスクの 2 つの部分があります。

**パート 1 - オープン ソース API を使用する**  
Intune と統合するための API が、Microsoft によって作成されています。 その API を使うと、証明書を検証し、成功または失敗の通知を送信し、SSL (具体的には SSL ソケット ファクトリ) を使って Intune と通信することができます。

この API は、[Intune SCEP API パブリック GitHub リポジトリ](https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)からダウンロードして、ソリューションで使用できます。 SCEP によってデバイスに証明書がプロビジョニングされる前に、この API をサード パーティの SCEP サーバーで使って、Intune に対してカスタム チャレンジの検証を実行します。

[Intune SCEP 管理ソリューションとの統合](scep-libraries-apis.md)に関するページでは、API の使用、そのメソッド、作成したソリューションのテストに関して、さらに詳しく説明されています。

**パート 2 - アプリケーションとプロファイルを作成する**  
Azure Active Directory (Azure AD) アプリケーションを使って、デバイスから受け取った SCEP 要求を処理する権限を Intune に委任できます。 Azure AD アプリケーションに含まれるアプリケーション ID と認証キーの値を、開発者が作成する API ソリューション内で使います。 その後、管理者は、Intune を使って SCEP 証明書プロファイルを作成して展開し、デバイスでの展開の状態に関するレポートを表示できます。

この記事では、Azure AD アプリケーションの作成など、この機能の概要を管理者の観点から説明します。

## <a name="overview"></a>概要

以下の手順では、Intune での SCEP 証明書の使用の概要を示します。

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

![サード パーティの SCEP 証明機関を Microsoft Intune に統合する方法](./media/certificate-authority-add-scep-overview/scep-certificate-vendor-integration.png)

## <a name="set-up-third-party-ca-integration"></a>サード パーティの CA の統合をセットアップする

### <a name="validate-third-party-certification-authority"></a>サード パーティの証明機関を検証する

サード パーティの証明機関を Intune と統合する前に、使っている CA が Intune をサポートすることを確認します。 「[サード パーティの証明機関パートナー](#third-party-certification-authority-partners)」 (この記事) に一覧が含まれています。 証明機関のガイダンスで詳細を確認することもできます。 CA には、その実装に固有のセットアップ手順が含まれることがあります。

### <a name="authorize-communication-between-ca-and-intune"></a>CA と Intune の間の通信を承認する

サード パーティの SCEP サーバーが Intune でカスタム チャレンジの検証を実行できるようにするには、Azure AD でアプリを作成します。 このアプリは、SCEP 要求を検証する権限を Intune に委任します。

Azure AD アプリを登録するのに必要なアクセス許可があることを確認してください。 Azure AD ドキュメントの「[必要なアクセス許可](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal#required-permissions)」をご覧ください。

#### <a name="create-an-application-in-azure-active-directory"></a>Azure Active Directory でアプリケーションを作成する  

1. [Azure portal](https://portal.azure.com) で、 **[Azure Active Directory]**  >  **[アプリの登録]** に移動し、 **[New registration]\(新規登録\)** を選択します。  

2. **[アプリケーションの登録]** ページで、次の詳細を指定します。  
   - **[名前]** セクションで、わかりやすいアプリケーション名を入力します。  
   - **[サポートされているアカウントの種類]** セクションで、 **[任意の組織のディレクトリ内のアカウント]** を選択します。  
   - **[リダイレクト URI]** については、既定値の [Web] のままにして、サード パーティの SCEP サーバーのサインオン URL を指定します。  

3. **[登録]** を選択してアプリケーションを作成し、新しいアプリの [概要] ページを開きます。  

4. アプリの **[概要]** ページで、 **[Application (client) ID]\(アプリケーション \(クライアント\) ID\)** の値をコピーし、後で使うので記録しておきます。 この値は後で必要になります。  

5. アプリのナビゲーション ウィンドウで、 **[管理]** の **[証明書とシークレット]** に移動します。 **[New client secret]\(新しいクライアント シークレット\)** ボタンを選択します。 [説明] に値を入力し、 **[有効期限]** で任意のオプションを選択してから、 **[追加]** を選択して、クライアント シークレットの "*値*" を生成します。 
   > [!IMPORTANT]  
   > このページを終了する前に、クライアント シークレットの値をコピーし、後でサード パーティの CA の実装に使うので記録しておきます。 この値は、二度と表示されません。 アプリケーション ID、認証キー、テナント ID の必要な構成方法については、サード パーティの CA のガイダンスを確認してください。  

6. **テナント ID** を記録しておきます。 テナント ID は、アカウントで @ 記号の後にあるドメイン テキストです。 たとえば、アカウントが *admin@name.onmicrosoft.com* の場合、テナント ID は **name.onmicrosoft.com** です。  

7. アプリのナビゲーション ウィンドウで、 **[管理]** の **[API のアクセス許可]** に移動し、 **[アクセス許可の追加]** を選択します。  

8. **[API アクセス許可の要求]** ページで、 **[Intune]** を選択して、 **[アプリケーションのアクセス許可]** を選択します。 **scep_challenge_provider** (SCEP チャレンジの検証) のチェック ボックスをオンにします。  

   **[アクセス許可の追加]** を選択して、この構成を保存します。  

9. **[API のアクセス許可]** ページで、 **[Microsoft に管理者の同意を与えます]** を選択して、 **[はい]** を選択します。  
   
   Azure AD でのアプリの登録プロセスは完了です。





### <a name="configure-and-deploy-a-scep-certificate-profile"></a>SCEP 証明書プロファイルを構成して展開する
管理者として、SCEP 証明書プロファイルを作成し、ユーザーまたはデバイスを対象にします。 次に、プロファイルを割り当てます。

- [SCEP 証明書プロファイルを作成する](certificates-profile-scep.md#create-a-scep-certificate-profile)

- [証明書プロファイルを割り当てる](certificates-profile-scep.md#assign-the-certificate-profile)

## <a name="removing-certificates"></a>証明書の削除

デバイスを登録解除またはワイプすると、証明書は削除されます。 証明書が取り消されることはありません。

## <a name="third-party-certification-authority-partners"></a>サード パーティの証明機関パートナー
次のサード パーティ証明機関が Intune をサポートしています。

- [Entrust Datacard](https://info.entrustdatacard.com/pki-eval-tool)
- [EJBCA GitHub オープンソース バージョン](https://github.com/agerbergt/intune-ejbca-connector)
- [EverTrust](https://evertrust.fr/en/products/)
- [GlobalSign](https://downloads.globalsign.com/acton/attachment/2674/f-6903f60b-9111-432d-b283-77823cc65500/1/-/-/-/-/globalsign-aeg-microsoft-intune-integration-guide.pdf)
- [IDnomic](https://www.idnomic.com/)
- [Sectigo](https://sectigo.com/products)
- [DigiCert](https://knowledge.digicert.com/tutorials/microsoft-intune.html)
- [Venafi](https://www.venafi.com/platform/enterprise-mobility)
- [SCEPman](https://azuremarketplace.microsoft.com/marketplace/apps/gluckkanja.scepman)

自社の製品と Intune の統合に関心をお持ちのサード パーティ CA は、API のガイダンスを確認してください。

- [Intune SCEP API の GitHub リポジトリ](https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)
- [サード パーティ CA 向けの Intune SCEP API ガイダンス](scep-libraries-apis.md)

## <a name="see-also"></a>関連項目

- [証明書プロファイルを構成する](certificates-scep-configure.md)
- [Intune SCEP API の GitHub リポジトリ](https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)
- [サード パーティ CA 向けの Intune SCEP API ガイダンス](scep-libraries-apis.md)
