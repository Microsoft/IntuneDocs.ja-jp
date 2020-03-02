---
title: コンプライアンスのために Jamf Pro を Microsoft Intune と統合する
titleSuffix: Microsoft Intune
description: Microsoft Intune コンプライアンス ポリシーと Azure Active Directory の条件付きアクセスを使って、Jamf でマネージド デバイスを統合し、セキュリティで保護できます。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/18/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4b6dcbcc-4661-4463-9a36-698d673502c6
ms.reviewer: jinyoon
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9dab1025e283ed1591c22b03ed4e3a61d40a20c3
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/20/2020
ms.locfileid: "77515086"
---
# <a name="integrate-jamf-pro-with-intune-for-compliance"></a>コンプライアンスのために Jamf Pro を Intune と統合する

組織で [Jamf Pro](https://www.jamf.com) を使用して macOS デバイスを管理している場合、Azure Active Directory (Azure AD) 条件付きアクセスと共に Microsoft Intune コンプライアンス ポリシーを使用することで、組織内のデバイスから会社のリソースにアクセスする前に、準拠していることを確認できるようになります。 この記事では、Jamf と Intune の統合を構成する方法について説明します。

Jamf Pro を Intune と統合すると、Azure AD を使用して、macOS デバイスからのインベントリ データを Intune と同期できるようになります。 Intune のコンプライアンス エンジンでは、インベントリ データが分析され、レポートが生成されます。 Intune の分析がデバイス ユーザーの Azure AD ID に関するインテリジェンスと組み合わされ、条件付きアクセスによる適用が促進されます。 条件付きアクセス ポリシーに準拠しているデバイスは、保護された会社のリソースにアクセスできます。

統合を構成した後は、Jamf によって管理されているデバイスに[条件付きアクセスにコンプライアンスを適用するように Jamf と Intune を構成](conditional-access-assign-jamf.md)します。

## <a name="prerequisites"></a>[前提条件]

### <a name="products-and-services"></a>製品とサービス

Jamf Pro で条件付きアクセスを構成するには、次のものが必要です。

- Jamf Pro 10.1.0 以降
- [macOS 用ポータル サイト アプリ](https://aka.ms/macoscompanyportal)
- OS X 10.12 Yosemite 以降を使用する macOS デバイス

### <a name="network-ports"></a>ネットワーク ポート

<!-- source: https://support.microsoft.com/en-us/help/4519171/troubleshoot-problems-when-integrating-jamf-with-microsoft-intune -->
Jamf と Intune を適切に統合するには、次のポートにアクセスできる必要があります。

- **Intune**:ポート 443
- **Apple**:ポート 2195、2196、および 5223 (Intune へのプッシュ通知)
- **Jamf**:ポート 80 および 5223

APNs がネットワーク上で正常に機能するには、以下への送信接続と以下からのリダイレクトも有効にする必要があります。

- すべてのクライアント ネットワークからの TCP ポート 5223 および 443 上の Apple 17.0.0.0/8 ブロック。
- Jamf Pro サーバーからのポート 2195 および 2196。  

これらのポートの詳細については、次の記事を参照してください。

- [Intune のネットワーク構成の要件と帯域幅](../fundamentals/network-bandwidth-use.md)。
- jamf.com 上で [Jamf Pro に使用されるネットワーク ポート](https://www.jamf.com/jamf-nation/articles/34/network-ports-used-by-jamf-pro)。
- support.apple.com 上で [Apple ソフトウェア製品に使用される TCP ポートと UDP ポート](https://support.apple.com/HT202944)

## <a name="connect-intune-to-jamf-pro"></a>Intune を Jamf Pro に接続する

Intune を Jamf Pro に接続するには:

1. Azure 内で新しいアプリケーションを作成します。
2. Intune の Jamf Pro との統合を有効にします。
3. Jamf Pro 内で条件付きアクセスを構成します。

### <a name="create-an-application-in-azure-active-directory"></a>Azure Active Directory でアプリケーションを作成する

1. [Azure portal](https://portal.azure.com) で、 **[Azure Active Directory]**  >  **[アプリの登録]** に移動し、 **[New registration]\(新規登録\)** を選択します。

2. **[アプリケーションの登録]** ページで、次の詳細を指定します。

   - **[名前]** セクションで、わかりやすいアプリケーション名を入力します (例: **Jamf 条件付きアクセス**)。
   - **[サポートされているアカウントの種類]** セクションで、 **[任意の組織のディレクトリ内のアカウント]** を選択します。
   - **[リダイレクト URI]** については、既定値の [Web] のままにして、Jamf Pro インスタンスの URL を指定します。

3. **[登録]** を選択してアプリケーションを作成し、新しいアプリの **[概要]** ページを開きます。

4. アプリの **[概要]** ページで、 **[Application (client) ID]\(アプリケーション \(クライアント\) ID\)** の値をコピーし、後で使うので記録しておきます。 この値は後の手順で必要になります。

5. **[管理]** の **[証明書とシークレット]** を選択します。 **[New client secret]\(新しいクライアント シークレット\)** ボタンを選択します。 **[説明]** に値を入力し、 **[有効期限]** で任意のオプションを選択して、 **[追加]** を選択します。

   > [!IMPORTANT]
   > このページを終了する前に、クライアント シークレットの値をコピーし、後で使うので記録しておきます。 この値は後の手順で必要になります。 この値は、アプリの登録を作り直さない限り、再び入手することはできません。

6. **[管理]** で **[API のアクセス許可]** を選択します。 

7. [API のアクセス許可] ページで、既存の各アクセス許可の横にある **[...]** アイコンを選択することで、このアプリからすべてのアクセス許可を削除します。 これは必須です。このアプリの登録で、予期しない追加のアクセス許可がある場合、統合は成功しません。

8. 次に、デバイス属性を更新するアクセス許可を追加します。 **[API のアクセス許可]** ページの左上で、 **[アクセス許可の追加]** を選択して新しいアクセス許可を追加します。 

9. **[API アクセス許可の要求]** ページで、 **[Intune]** を選択して、 **[アプリケーションのアクセス許可]** を選択します。 **update_device_attributes** のチェック ボックスだけをオンにして、新しいアクセス許可を保存します。

10. 次に、 **[API のアクセス許可]** ページの左上にある **[ _\<テナント> に管理者の同意を与えます_** ] を選択して、このアプリに管理者の同意を付与します。 新しいウィンドウで自分のアカウントを再認証し、プロンプトに従って、アプリケーションにアクセス権限を付与する必要がある場合があります。  

11. ページの上部にある **[更新]** ボタンをクリックしてページを更新してください。 **update_device_attributes** アクセス許可に対して管理者の同意が与えられていることを確認します。 

12. アプリが正常に登録されると、API アクセス許可に含まれるアクセス許可は **update_device_attributes** だけになり、次のように表示されるはずです。

   ![成功したアクセス許可](./media/conditional-access-integrate-jamf/sucessfull-app-registration.png)

   Azure AD でのアプリの登録プロセスは完了です。

    > [!NOTE]
    > クライアント シークレットの有効期限が切れた場合は、Azure で新しいクライアント シークレットを作成し、Jamf Pro で条件付きアクセス データを更新する必要があります。 Azure では、サービスの中断を防ぐため、古いシークレットと新しいキーの両方をアクティブにすることができます。

### <a name="enable-intune-to-integrate-with-jamf-pro"></a>Intune の Jamf Pro との統合を有効にする

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。

2. **[テナント管理]**  >  **[コネクタとトークン]**  >  **[パートナー デバイスの管理]** の順に選択します。

3. 前の手順の間に保存したアプリケーション ID を **[Jamf の Azure Active Directory アプリ ID を指定します]** フィールドに貼り付けることによって、 *[Jamf の準拠コネクタ]* を有効にします。

4. **[保存]** を選択します。

### <a name="configure-microsoft-intune-integration-in-jamf-pro"></a>Jamf Pro で Microsoft Intune 統合を構成する

1. Jamf Pro コンソールで接続をアクティブにします。

   1. Jamf Pro コンソールを開き、 **[グローバル管理]**  >  **[条件付きアクセス]** の順に移動します。 **[macOS Intune Integration]\(macOS Intune 統合\)** タブの **[編集]** ボタンをクリックします。
   2. **[Enable Intune Integration for macOS]\(macOS の Intune 統合の有効化\)** チェック ボックスをオンにします。
   3. **場所**、**ドメイン名**、**アプリケーション ID**、およびアプリを作成するときに Azure AD に保存した*クライアント シークレット*の値など、Azure テナントについての必要な情報を入力します。
   4. **[保存]** を選択します。 Jamf Pro によって設定がテストされ、成功したことが確認されます。

   Intune の **[パートナー デバイスの管理]** ページに戻り、構成を完了します。

2. Intune で、 **[パートナー デバイスの管理]** ページに移動します。 **[コネクタの設定]** で、割り当てのグループを構成します。

   - Jamf で macOS 登録の対象にするユーザー グループを指定するには、 **[含める]** を選択します。
   - Jamf で登録せず、mac を直接、Intune で登録するユーザー グループを選択するには、 **[除外する]** を選択します。

   *[除外する]* は *[含める]* より優先されます。つまり、両方のグループに属するデバイスは Jamf から除外され、Intune で登録されます。

   >[!NOTE]
   > ユーザー グループを含めるか除外するこの手法は、ユーザーの登録体験に影響を与えます。 既に Jamf か Intune に mac を登録しているユーザーが他の MDM による登録の対象になった場合、デバイスの登録を解除し、新しい MDM で再登録しないとデバイスの管理が正しく機能しません。

3. **[評価]** を選択すると、グループ構成に基づき、Jamf で登録されるデバイスの数が決定されます。

4. 構成を適用する準備ができたら、 **[保存]** を選択します。

5. 続行するには、次に、ユーザーが自分のデバイスを Intune に登録できるように、[Jamf を使用してポータル サイトを mac 用に展開する](conditional-access-assign-jamf.md#deploy-the-company-portal-app-for-macos-in-jamf-pro)必要があります。

## <a name="set-up-compliance-policies-and-register-devices"></a>コンプライアンス ポリシー設定してデバイスを登録する

Intune と Jamf の統合を構成したら、[Jamf で管理されたデバイスにコンプライアンス ポリシーを適用する](conditional-access-assign-jamf.md)必要があります。

## <a name="disconnect-jamf-pro-and-intune"></a>Jamf Pro と Intune を切断する

Jamf Pro を使用して組織内の Mac を管理しなくなった場合、ユーザーを Intune で管理するには、Jamf Pro と Intune 間の接続を削除する必要があります。 Jamf Pro コンソールを使用して接続を削除します。

1. Jamf Pro で、 **[グローバル管理]**  >  **[条件付きアクセス]** に移動します。 **[macOS Intune Integration]\(macOS Intune 統合\)** タブで、 **[編集]** を選択します。

2. **[Enable Intune Integration for macOS]\(macOS の Intune 統合の有効化\)** チェック ボックスをオフにします。

3. **[保存]** を選択します。 Jamf Pro によって構成が Intune に送信され、統合が終了します。

4. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。

5. **[テナント管理]**  >  **[コネクタとトークン]**  >  **[パートナー デバイスの管理]** の順に選択して、状態が **[終了]** になっていることを確認します。

   > [!NOTE]
   > 組織の Mac デバイスは、コンソールに表示されている日付 (3 か月後) に削除されます。

## <a name="next-steps"></a>次のステップ

- [Jamf で管理されたデバイスにコンプライアンス ポリシーを適用する](conditional-access-assign-jamf.md)
- [Jamf から Intune に送られるデータ](data-jamf-sends-to-intune.md)
