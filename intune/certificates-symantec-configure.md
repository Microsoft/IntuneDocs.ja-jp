---
title: "Intune を使用して Symantec PKCS 証明書を発行する"
titlesuffix: Azure portal
description: "Intune Certificate Connector をインストールし、Intune 管理対象デバイスに、Symantec PKI Manager Web サービスから PKCS 証明書を発行するように構成する"
keywords: 
author: MicrosoftGuyJFlo
ms.author: joflore
manager: angrobe
ms.date: 11/17/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 31e48d84ec7044102575a6c49837330c139e993c
ms.sourcegitcommit: 520eb7712625e129b781e2f2b9fe16f9b9f3d08a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2017
---
# <a name="set-up-intune-certificate-connector-for-symantec-pki-manager-web-service"></a>Intune Certificate Connector を Symantec PKI Manager Web サービス向けに設定する

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

この記事では、Intune Certificate Connector をインストールして、Intune 管理対象デバイスに、Symantec PKI Manager Web サービスから PKCS 証明書を発行するように構成する方法について説明します。

この記事を通して、Symantec PKI Manager Web サービスを Symantec CA と呼びます。 Microsoft 証明機関 (CA) から PKCS 証明書および SCEP 証明書を発行するように Intune Certificate Connector を構成済みの場合、同じ Certificate Connector を使用して Symantec CA の PKCS 証明書を構成し発行できます。 この場合、Intune Certificate Connector では以下の証明書を発行できます。

* Microsoft CA からの PKCS 証明書
* Microsoft CA からの SCEP 証明書
* Symantec CA からの PKCS 証明書

Microsoft CA 用および Symantec CA 用に Intune Certificate Connector を使用する場合は、まず Microsoft CA 向けの Intune Certificate Connector の構成を完了してから、以下の Symantec CA 向けの構成手順を実施する必要があります。  Microsoft CA 向けの Intune Certificate Connector の構成方法の詳細については、「[Microsoft Intune で証明書を構成する方法](certificates-configure.md)」を参照してください。

## <a name="prepare-to-install-intune-certificate-connector"></a>Intune Certificate Connector のインストールの準備

既存の Microsoft CA 用に既に Intune Certificate Connector を使用しており、Symantec CA サポートを追加する場合はこの手順をスキップし、Intune 管理ポータルから最新の Intune Certificate Connector をインストールしてから、残りの手順を実行してください。 この手順は、Symantec CA スタンドアロン用に Intune Certificate Connector を使用する場合のみ必要になります。

1. 次の一覧からいずれかの Windows オペレーティング システムのバージョンを選択し、コンピューターにインストールします。
   * Windows Server 2012 R2 Datacenter
   * Windows Server 2012 R2 Standard
   * Windows Server 2016 Datacenter
   * Windows Server 2016 Standard

2. 管理特権を持つユーザーを作成し、このユーザーで以下の手順を実行します。

3. 最新の Windows Update を確認し、利用できる場合はインストールします。

   > [!IMPORTANT]
   > Windows Update のインストール後、コンピューターを再起動します。

4. .NET Framework 3.5 をインストールします。

    a. **[コントロール パネル]** > **[プログラムと機能]** > **[Windows の機能の有効化または無効化]** の順に選択します。

    b. **[.NET Framework 3.5]** を選択してインストールします。

## <a name="install-the-symantec-registration-authorization-certificate"></a>Symantec 登録承認証明書のインストール

次のステップに従い、Symantec CA から登録承認 (RA) 証明書を取得します。 RA 証明書を取得するには、Symantec CA のアクティブなサブスクリプションが必要です。

1. 次のコード スニペットを **certreq.ini** という名前のファイルに保存し、必要に応じて更新します (*Subject name in CN format* (共通名形式のサブジェクト名) など)。

   ```
    [Version] 
    Signature="$Windows NT$" 

    [NewRequest] 
    ;Change to your,country code, company name and common name 
    Subject = "Subject Name in CN format"

    KeySpec = 1 
    KeyLength = 2048 
    Exportable = TRUE 
    MachineKeySet = TRUE 
    SMIME = False 
    PrivateKeyArchive = FALSE 
    UserProtected = FALSE 
    UseExistingKeySet = FALSE 
    ProviderName = "Microsoft RSA SChannel Cryptographic Provider" 
    ProviderType = 12 
    RequestType = PKCS10 
    KeyUsage = 0xa0 

    [EnhancedKeyUsageExtension] 
    OID=1.3.6.1.5.5.7.3.2 ; Client Authentication  // Uncomment if you need a mutual TLS authentication

    ;----------------------------------------------- 
   ```

2. 管理者特権でのコマンド プロンプトを開き、次のコマンドにより CSR コンテンツを生成します。

   `Certreq.exe -new certreq.ini request.csr`

3. メモ帳で request.csr ファイルを開き、次の形式の CSR コンテンツをコピーします。

    ```
    -----BEGIN NEW CERTIFICATE REQUEST-----
    MIID8TCCAtkCAQAwbTEMMAoGA1UEBhMDVVNBMQswCQYDVQQIDAJXQTEQMA4GA1UE
    …
    …
    fzpeAWo=
    -----END NEW CERTIFICATE REQUEST-----
    ```

4. Symantec CA にログオンし、[Tasks]\(タスク\) から **[Get an RA Cert]\(RA 証明書の取得\)** に移動します。

   a. 表示されたテキスト ボックスにステップ 3 の CSR のコンテンツを入力します。

   b. 表示されたテキスト ボックスに証明書のフレンドリ名を入力します。

   c. **[続行]** をクリックします。

      RA 証明書のダウンロード リンクが表示されます。

   d. RA 証明書をローカル コンピューターにダウンロードします。

5. Windows 証明書ストアに RA 証明書をインポートします。

    a. MMC コンソールを開きます。

    b. **[ファイル]** > **[スナップインの追加と削除]** > **[証明書]** > **[追加]** の順にクリックします。

    c. **[コンピューター アカウント]** を選択し **[次へ]** をクリックします。

    d. **[ローカル コンピューター]** を選択し、**[完了]** をクリックします。

    e. **[スナップインの追加と削除]** ウィンドウで **[OK]** をクリックします。**[証明書 (ローカル コンピューター)]** > **[個人]** > **[証明書]** の順に展開します。

    f. **[証明書]** ノードを右クリックし、**[すべてのタスク]** > **[インポート]** の順にクリックします。

    g. Symantec CA and からダウンロードした RA 証明書の場所を選択し、**[次へ]** をクリックします。

    h. **[個人用証明書ストア]** を選択して **[次へ]** をクリックします。

    i. **[Finish]** をクリックします。 RA 証明書が、秘密キーとともにローカル コンピューターの [個人] ストアにインストールされます。  

6. 秘密キー証明書をエクスポートしインポートします。

    a. **[証明書 (ローカル コンピューター)]** > **[個人]** > **[証明書]** の順に展開します。

    b. 前のステップでインポートした証明書を選択します。

    c. インポートした証明書を右クリックし、**[すべてのタスク]** > **[エクスポート]** の順に選択します。

    d. **[次へ]** をクリックし、パスワードを入力します。

    e. エクスポート先を選択し、**[完了]** をクリックします。

    f. ステップ 5 と同じ手順を実行して、ローカル コンピューターの [個人] ストアに秘密キー証明書をインポートします。

7. スペースを除いて RA 証明書のサムプリントをコピーします。  次にサムプリントの例を示します。

   ```
   RA Cert Thumbprint: “EA7A4E0CD1A4F81CF0740527C31A57F6020C17C5”
   ```


   > [!NOTE]
   > Symantec CA からの RA 証明書の取得で問題が発生した場合は、Symantec のカスタマー サポートに問い合わせてください。

## <a name="install-intune-certificate-connector"></a>Intune Certificate Connector のインストール

既存の Microsoft CA 用に最新の Intune Certificate Connector を既に使用しており Symantec CA サポートを追加する場合、この手順はスキップします。 それ以外の場合は、Intune の管理ポータルから最新の Intune Certificate Connector をインストールし、次の手順に実行します。

1. Intune のテナント管理者の資格情報を使用して https://portal.azure.com にサインインして、Intune リソースを検索します。
2. **[Microsoft Intune]** > **[デバイス構成]** > **[証明機関]** > **[Certificate Connector のダウンロード]** リンクから NDESConnectorSetup.exe をダウンロードします。
3. 管理特権で NDESConnectorSetup.exe を実行します。

    a. **[インストール オプション]** 画面で、以下のスクリーン ショットのように **[PFX Distribution]\(PFX の配布\)** を選択します。  残りのセットアップを、既定の選択内容のままで完了します。

   > [!IMPORTANT]
   > Microsoft CA および Symantec CA から証明書を発行するように Intune Certificate Connector を構成する場合は、**[SCEP および PFX プロファイルの配布]** を選択します。 残りのセットアップを、既定の選択内容のままで完了します。

   ![Connector のインストール][InstallConnector]
 
## <a name="configure-intune-certificate-connector"></a>Intune Certificate Connector の構成

既定では、Intune Certificate Connector は `%ProgramFiles%\Microsoft Intune` にインストールされます。

1. メモ帳で %ProgramFiles%\Microsoft Intune\NDESConnectorSvc\NDESConnector.exe.config ファイルを開きます。

    a. RACertThumbprint キーの値を、前のセクションでコピーした証明書のサムプリントで更新します。  次に例を示します。

   ```
   <add key="RACertThumbprint"
   value="EA7A4E0CD1A4F81CF0740527C31A57F6020C17C5"/>
   ```

    b. ファイルを保存し、閉じます。

2. services.msc を開きます。

    a. **[Intune Connector Service]** を選択します。

    b. サービスを停止し、その後開始します。

    c. [サービス] ウィンドウを閉じます。

## <a name="setup-the-intune-administrator-account"></a>Intune 管理者アカウントのセットアップ

既存の Microsoft CA 用に Intune Certificate Connector を既に使用しており Symantec CA サポートを追加する場合、この手順はスキップして残りの手順を実行します。 

1. ` %ProgramFiles%\Microsoft Intune\NDESConnectorUI\NDESConnectorUI.exe ` で NDES Connector のユーザー インターフェイスを起動します。

    a. **[登録]** タブをクリックし、**[サインイン]** をクリックします。

    b. 表示されたテキスト ボックスに、Intune のテナント管理者の資格情報を入力します。

    c. **[サインイン]** をクリックします。  次のスクリーン ショットのように、確認のダイアログ ボックスが開き "**正常に登録されました**" というメッセージが表示されます。
2. NDES Connector のユーザー インターフェイスを終了します。

![Connector の構成][ConfigureConnector]
 
## <a name="create-a-trusted-certificate-profile"></a>信頼済み証明書プロファイルの作成

Intune 管理対象デバイスに展開する PKCS 証明書は、信頼されたルート証明書にチェーンする必要があります。 これを行うには、Symantec CA から取得したルート証明書を使用して Intune の信頼済み証明書プロファイルを作成する必要があります

1. Symantec CA から信頼されたルート証明書を取得します。

    a. Symantec CA 管理ポータルにログオンします。

    b. [タスク]\(タスク\) の [Manage CAs]\(証明機関の管理\) をクリックします。

    c. CA の一覧から目的の CA を選択します。

    d. [Download root certificate]\(ルート証明書のダウンロード\) をクリックして、信頼されたルート証明書をダウンロードします。

2. Intune 管理ポータルで、信頼済み証明書プロファイルを作成します。

    a. Intune のテナント管理者の資格情報を使用して [Azure Portal](https://portal.azure.com) にサインインして、Intune リソースを検索します。

    b. **[Microsoft Intune]** > **[デバイス構成]** - **[プロファイル]** > **[プロファイルの作成]** で信頼済み証明書プロファイルを作成します。

    c. **[名前]** フィールドおよび **[説明]** フィールドに必要な情報を入力し、対象のプラットフォームを選択します。 

    d. [プロファイルの種類] ドロップダウン リストで [信頼済み証明書プロファイル] を選択します。

    e. 前のステップで Symantec CA から取得した信頼されたルート証明書をアップロードします。

    f. プロファイル作成の残りの手順を完了します。 

    g. **[割り当て]** をクリックして、適切なグループを選択します。  割り当てるグループには、1 名以上のユーザーまたは 1 台以上のデバイスが含まれている必要があります。

## <a name="get-the-certificate-profile-oid"></a>証明書プロファイル OID の取得

Symantec CA の証明書プロファイル テンプレートには、証明書プロファイル OID が関連付けられています。  Intune 管理ポータルで PKCS 証明書プロファイルを作成するには、証明書テンプレート名を、Symantec CA の証明書テンプレートに関連付けられている証明書プロファイル OID の形式で指定する必要があります。

1. Symantec CA 管理ポータルにログオンします。
2. [Manage Certificate Profiles]\(証明書プロファイルの管理\) をクリックします。
3. 使用する証明書プロファイルを選択します。
4. 証明書プロファイル OID をコピーします。 これは次の例のようなものです。

   ```
   Certificate Profile OID = 2.16.840.1.113733.1.16.1.2.3.1.1.47196109 
   ```

   > [!NOTE]
   > 証明書プロファイル OID の取得で問題が生じた場合は、Symantec のカスタマー サポートに問い合わせください。

## <a name="create-a-pkcs-certificate-profile"></a>PKCS 証明書プロファイルの作成

1. Intune のテナント管理者の資格情報を使用して [Azure Portal](https://portal.azure.com) にサインインして、Intune リソースを検索します。
2. **[Microsoft Intune]** > **[デバイス構成] - [プロファイル]** > **[プロファイルの作成]** > **[PKCS 証明書]** で PKCS 証明書プロファイルを作成します。

    a. **[名前]** フィールドおよび **[説明]** フィールドに必要な情報を入力し、対象のプラットフォームを選択します。

    b. **[プロファイルの種類]** ドロップダウン リストで **[PKCS 証明書プロファイル]** を選択します。  

    c. 残りの手順を完了して、プロファイルを作成します。

   ![プロファイルの構成][ConfigureProfile]

   > [!IMPORTANT]
   > Intune Certificate Connector を介して Symantec CA から PKCS 証明書を発行するには、PKCS 証明書プロファイルの以下のパラメーターを、スクリーン ショットで示すように次の表の指定された値に設定する必要があります。 

    |PKCS 証明書のパラメーター | 値 | 説明 |
    | --- | --- | --- |
    | 証明機関 | pki ws.symauth.com | この値には、末尾のスラッシュを除いた Symantec CA のベース サービス FQDN を指定する必要があります。  この値が Symantec CA サブスクリプションの正確なベース サービス FQDN であるか不明な場合は、Symantec カスタマー サポートに問い合わせてください。 <br><br> この FQDN が間違っている場合、Intune Certificate Connector では Symantec CA から PKCS 証明書が発行されません。| 
    | 証明機関の名前 | Symantec | この値には、文字列 **Symantec** を指定する必要があります。 <br><br> この値を変更すると、Intune Certificate Connector で Symantec CA から PKCS 証明書が発行されなくなります。|
    | 証明書テンプレート名 | Symantec CA からの証明書プロファイル OID。 <br><br> 例: `2.16.840.1.113733.1.16.1.2.3.1.1.61904612`| この値には、前のセクションで Symantec CA 証明書プロファイル テンプレートから取得した証明書プロファイル OID を指定する必要があります。 <br><br> Intune Certificate Connector で、Symantec CA 内にこの証明書プロファイル OID に関連付けられている証明書テンプレートが見つからない場合、Symantec CA から PKCS 証明書が発行されません。|

   > [!NOTE]
   > Windows プラットフォーム用の PKCS 証明書プロファイルを、信頼済み証明書プロファイルに関連付ける必要はありません。 ただし、Android など、Windows 以外のプラットフォームのプロファイルでは必要になります。

3. **[割り当て]** をクリックして、適切なグループを選択します。  割り当てるグループには、1 名以上のユーザーまたは 1 台以上のデバイスが含まれている必要があります。
 
前のステップを完了すると、Intune Certificate Connector により、割り当てたグループの Intune 管理対象デバイスへ Symantec CA の PKCS 証明書が発行されます。 これらの証明書は、Intune 管理対象デバイスの [現在のユーザー] 証明書ストアの [個人] ストアで使用できるようになります。

### <a name="pkcs-certificate-profile-supported-attributes"></a>PKCS 証明書プロファイルでサポートされる属性

|属性 | Intune でサポートされる形式 | Symantec Cloud CA でサポートされる形式 | Result |
| --- | --- | --- | --- |
| サブジェクト名 |Intune では、次の 3 つの形式のサブジェクト名のみがサポートされています。 <br><br> 1.共通名 <br> 2.電子メールを含む共通名 <br> 3.電子メールとしての共通名 <br><br> 次に例を示します。 <br><br> `CN = IWUser0 <br><br> E = IWUser0@samplendes.onmicrosoft.com` | Symantec CA では、追加の属性がサポートされます。  追加の属性を選択する場合は、Symantec 証明書プロファイル テンプレートでそれらの属性に固定値を定義する必要があります。| ここでは、PKCS 証明書の要求の共通名または電子メールを使用します。 <br><br> Intune 証明書プロファイルと Symantec 証明書プロファイル テンプレートでの属性の選択内容に不一致がある場合、Symantec CA から証明書が発行されません。|
| SAN | Intune では、次の SAN フィールド値のみがサポートされています。 <br><br> AltNameTypeEmail <br><br> AltNameTypeUpn <br><br> AltNameTypeOtherName (エンコードされた値) | これらのパラメーターは Symantec Cloud CA でもサポートされています。 追加の属性を選択する場合は、Symantec 証明書プロファイル テンプレートでそれらの属性に固定値を定義する必要があります。 <br><br> AltNameTypeEmail: SAN でこのタイプが見つからない場合、AltNameTypeUpn の値が使用されます。  SAN 内に AltNameTypeUpn も見つからない場合、サブジェクト名が電子メール形式であればその値が使用されます。  電子メール形式のサブジェクト名も存在しない場合、Intune Certificate Connector は証明書に接続できません。 <br><br> 例: `RFC822 Name=IWUser0@ndesvenkatb.onmicrosoft.com`  <br><br> AltNameTypeUpn: SAN でこのタイプが見つからない場合、AltNameTypeEmail の値が使用されます。 SAN 内に AltNameTypeEmail も見つからない場合は、サブジェクト名が電子メール形式であればその値が使用されます。  電子メール形式のサブジェクト名も存在しない場合、Intune Certificate Connector は証明書に接続できません。  <br><br> 例: `Other Name: Principal Name=IWUser0@ndesvenkatb.onmicrosoft.com` <br><br> AltNameTypeOtherName: SAN 内にこのタイプが見つからない場合、Intune Certificate Connector は証明書に接続できません。 <br><br> 例: `Other Name: DS Object Guid=04 12 b8 ba 65 41 f2 d4 07 41 a9 f7 47 08 f3 e4 28 5c ef 2c` <br><br>  **重要:** Symantec CA では、このフィールドの値についてはエンコードされた形式 (16 進値) のみがサポートされます。 このため、このフィールドの値はすべて、証明書の要求の送信前に Intune Certificate Connector により base 64 エンコードに変換されます。 **Intune Certificate Connector では、この値がエンコード済みかどうかの確認は行われません。** | None |

## <a name="troubleshooting"></a>トラブルシューティング

Intune Certificate Connector サービスのログは、NDES Connector コンピューターの `%ProgramFiles%\Microsoft Intune\NDESConnectorSvc\Logs\Logs` にあります。 [SvcTraceViewer](https://docs.microsoft.com/dotnet/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe) でこのログを開き、例外またはエラー メッセージを検索します。

| 問題/エラー メッセージ | 解消手順 |
| --- | --- |
| Intune テナント管理者アカウントを使用して NDES Connector UI にサインインできない | この問題は、Intune 管理ポータルでオンプレミスの Certificate Connector が有効になっていない場合に発生します。 この問題を解決するには、次の手順を使用します。 <br><br> Silverlight UI の場合: <br> 1.[Intune 管理ポータル](https://admin.manage.microsoft.com)にログオンします。 <br> 2.[管理] をクリックします。 <br> 3.[モバイル デバイス管理] > [Certificate Connector] の順にクリックします。 <br> 4.**[On-premises Certificate Connector の構成]** をクリックします。 <br> 5.**[Certificate Connector を有効にする]** チェックボックスをオンにします。 <br> 6.**[OK]**をクリックします。 <br><br>または <br><br> Azure Portal UI の場合: <br> 1.[Azure Portal](https://portal.azure.com) にサインインします。 <br> 2.Microsoft Intune にアクセスします。 <br> 3.**[デバイス構成]** > **[証明機関]** の順に選択します。 <br> 4.**[有効にする]** をクリックします。 <br><br> Silverlight UI または Azure Portal のいずれかで上記の手順を完了してから、同じ Intune テナント管理者アカウントを使用して NDES Connector UI にサインインしてください。 |
| NDES Connector 証明書が見つかりませんでした。 <br><br> System.ArgumentNullException: 値を null にすることはできません。 | Intune テナント管理者アカウントで NDES Connector UI へサインインしたことがない場合、Intune Certificate Connector にはこのエラーが表示されます。 <br><br> このエラーが引き続き発生する場合は、Intune Service Connector を再起動してください。 <br><br> 1.services.msc を開きます。 <br> 2.**[Intune Connector Service]** を選択します。 <br> 3.右クリックして **[再起動]** を選択します。|
| NDES Connector - IssuePfx -一般的な例外: <br> System.NullReferenceException: オブジェクト参照がオブジェクトのインスタンスに設定されていません。 | このエラーは一時的なものです。 Intune サービス コネクタを再起動してください。 <br><br> 1.services.msc を開きます。 <br> 2.**[Intune Connector Service]** を選択します。 <br> 3.右クリックして **[再起動]** を選択します。 |
| Symantec プロバイダー - Symantec ポリシーを取得できません “操作がタイムアウトになりました” | Intune Certificate Connector で、Symantec CA との通信中に操作のタイムアウト エラーが発生しました。 このエラーが続く場合は、接続タイムアウトの値を増やしてからやり直してください。 <br><br> 接続のタイムアウト時間を延ばすには次の手順を実行します。 <br> 1.NDES Connector コンピューターにアクセスします。 <br>2.メモ帳で `%ProgramFiles%\Microsoft Intune\NDESConnectorSvc\NDESConnector.exe.config` ファイルを開きます。 <br> 3.次のパラメーターのタイムアウト値を増やします。 <br><br> `CloudCAConnTimeoutInMilliseconds` <br><br> 4.Intune コネクタ サービスを再起動します。 <br><br> 問題が解決しない場合は、Symantec カスタマー サポートに問い合わせてください。 |
| Symantec プロバイダー - クライアント証明書を取得できません | Intune Certificate Connector が、ローカル コンピューターの [個人] 証明書ストアからリソース承認証明書を取得できませんでした。 この問題を解決するには、ローカル コンピューターの [個人] 証明書ストアにリソース承認証明書とその秘密キーをインストールします。 <br><br> **注:** リソース承認証明書は Symantec CA から取得する必要があります。 詳細については、Symantec カスタマー サポートに問い合わせてください。 | 
| Symantec プロバイダー - Symantec ポリシーを取得できません “要求は中止されました: SSL/TLS のセキュリティで保護されているチャネルを作成できませんでした。” | このエラーは、次のようなシナリオで発生します。 <br><br> 1.Intune Certificate Connector サービスに、ローカル コンピューターの [個人] ストアのリソース承認証明書とその秘密キーを読み取る十分な権限が設定されていません。 この問題を解決するには、services.msc でコネクタ サービスが実行されているコンテキスト アカウントを確認します。 コネクタ サービスは、NT AUTHORITY\SYSTEM コンテキストで実行する必要があります。 <br><br> 2.Intune 管理ポータルの PKCS 証明書プロファイルに無効な Symantec CA ベース サービス FQDN が設定されている可能性があります。 FQDN は `pki-ws.symauth.com` のように設定します。 この問題を解決するには、この URL が使用中のサブスクリプションに合っているかどうかを Symantec カスタマー サポートに確認してください。 <br><br> 3.Intune Certificate Connector が秘密キーを取得できないため、リソース承認証明書を使用して Symantec CA を認証できません。 この問題を解決するには、ローカル コンピューターの [個人] 証明書ストアにリソース承認証明書とその秘密キーをインストールします。 <br><br> 問題が解決しない場合は、Symantec カスタマー サポートに問い合わせてください。 |
| Symantec プロバイダー - Symantec ポリシーを取得できません “要求の要素を認識できません。” | クライアント プロファイル OID と Intune 証明書プロファイルが一致しないため、Intune Certificate Connector で Symantec 証明書プロファイル テンプレートを取得できませんでした。 もしくは、Intune Certificate Connector が、Symantec CA で指定のクライアント プロファイル OID に関連付けられている証明書プロファイル テンプレートを見つけられませんでした。 <br><br> この問題を解決するには、Symantec CA の Symantec 証明書テンプレートから適切なクライアント プロファイル OID を取得します。 Intune 管理ポータルで PKCS 証明書プロファイルを更新します。 <br><br> Symantec CA から証明書プロファイル OID を取得します。 <br> 1.Symantec CA 管理ポータルにログオンします。 <br> 2.[Manage Certificate Profiles]\(証明書プロファイルの管理\) をクリックします。 <br> 3.使用する証明書プロファイルを選択します。 <br> 4.証明書プロファイル OID を取得します。 これは次の例のようなものです。 <br> `Certificate Profile OID = 2.16.840.1.113733.1.16.1.2.3.1.1.47196109` <br><br> 適切な証明書プロファイル OID で PKCS 証明書プロファイルを更新します。 <br>1.Intune 管理ポータルにログオンします。 <br> 2.PKCS 証明書プロファイルを選択し、**[編集]** をクリックします。 <br> 3.[証明書テンプレート名] フィールドの証明書プロファイル OID を更新します。 <br> 4.PKCS 証明書プロファイルを保存します。 |
| Symantec プロバイダー - ポリシーの検証に失敗しました。 <br><br> Symantec でサポートされる証明書テンプレートの属性一覧に属性が含まれていません | Symantec 証明書プロファイル テンプレートと Intune 証明書プロファイルに不一致がある場合、Symantec CA によりこのメッセージが表示されます。 この問題の原因は、SubjectName 属性または SubjectAltName 属性の不一致であると考えられます。 <br><br> この問題を解決するには、Symantec 証明書プロファイル テンプレートの SubjectName および SubjectAltName に対して Intune でサポートされる属性を選択します。 詳細については、証明書パラメーターに関するセクションで Intune でサポートされる属性をご覧ください。 |
| 一部のユーザー デバイスで、Symantec CA から PKCS 証明書が受信されません。 | この問題は、ユーザー UPN にアンダースコアなどの特殊文字 (例: `global_admin@intune.onmicrosoft.com`) が含まれている場合に発生します。 <br><br> Symantec CA の mail_firstname および mail_lastname では特殊文字はサポートされません。 <br><br> この問題を解決するには、次の手順を実行します。 <br><br> 1. Symantec CA 管理ポータルにログオンします。 <br> 2.[Manage Certificate Profiles]\(証明書プロファイルの管理\) に移動します。 <br> 3. Intune で使用している証明書プロファイルをクリックします。 <br> 4.[Customize options]\(カスタマイズ オプション\) リンクをクリックします。 <br> 5. [Advanced options]\(詳細オプション\) ボタンをクリックします。 <br> 6.証明書の [Subject DN]\(サブジェクト DN\) フィールドの下に [Common Name (CN)]\(共通名 (CN)\) フィールドを追加し、既存の [Common Name (CN)]\(共通名 (CN)\) フィールドを削除します。 追加と削除は一度に実行する必要があります。 <br> 7.  [Save] をクリックします。 <br><br> 上記の変更により、Symantec 証明書プロファイルでは mail_firstname と mail_lastname の代わりに “CN=<upn>” が要求されるようになります。 |
| ユーザーが、展開済みの証明書をデバイスから手動で削除しました。 | Intune により、次のチェックイン時またはポリシー適用中に同一の証明書が再展開されます。 この場合、NDES Connector は PKCS 証明書要求を受信しません。 |

## <a name="next-steps"></a>次のステップ

- この記事の情報と「[Microsoft Intune のデバイス プロファイルとは](device-profiles.md)」の情報を合わせて、組織のデバイスとその証明書を管理します。

[InstallConnector]:  ./media/certificates-symantec-connector-install.png "Intune Certificate Connector のインストールおよび [PFX Distribution]\(PFX の配布\) の選択"
[ConfigureConnector]: ./media/certificates-symantec-configure-connector-configure.png "Intune Certificate Connector の構成"
[ConfigureProfile]: ./media/certificates-symantec-pkcs-example.png "Azure Portal での PKCS 証明書プロファイルの作成"