---
title: Microsoft Intune を使用して DigiCert PKCS 証明書を発行する
titleSuffix: Microsoft Intune
description: Intune Certificate Connector をインストールし、DigiCert PKI Platform から Intune マネージド デバイスに PKCS 証明書を発行するように構成します。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ca76ffe0c8fa42f1c2cf24fcdefd287140231220
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "73801650"
---
# <a name="set-up-intune-certificate-connector-for-digicert-pki-platform"></a>DigiCert PKI Platform 用に Intune Certificate Connector をセットアップする

Intune Certificate Connector を使用して、DigiCert PKI Platform から Intune マネージド デバイスに PKCS 証明書を発行します。 コネクタは、DigiCert 証明機関 (CA) のみ、または DigiCert CA と Microsoft CA の両方で使用できます。

> [!TIP]
> DigiCert は Symantec の Web サイト セキュリティおよび関連する PKI ソリューション ビジネスを獲得しました。 この変更の詳細については、[Symantec のテクニカル サポート記事](https://support.symantec.com/en_US/article.INFO4722.html)をご覧ください。

PKCS または System Center Endpoint Protection を使用して Microsoft CA から証明書を発行するために Intune Certificate Connector を既に使用している場合は、その同じコネクタを使用して、DigiCert CA から PKCS 証明書を構成し、発行することができます。 DigiCert CA をサポートするための構成を完了すると、Intune Certificate Connector で次の証明書を発行できます。

* Microsoft CA からの PKCS 証明書
* DigiCert CA からの PKCS 証明書
* Microsoft CA からの Endpoint Protection 証明書

コネクタはインストールされていないけれども、Microsoft CA と DigiCert CA の両方に使用する予定がある場合は、まず Microsoft CA 用のコネクタの構成を完了してください。 次に、この記事に戻り、DigiCert もサポートするように構成します。 証明書プロファイルとコネクタについて詳しくは、[Microsoft Intune でのデバイス用の証明書プロファイルの構成](certificates-configure.md)に関する記事をご覧ください。  

コネクタを DigiCert CA のみで使用する場合は、この記事の手順に従ってコネクタをインストールした後、構成することができます。

## <a name="prerequisites"></a>必要条件

- **DigiCert CA でのアクティブなサブスクリプション**: DigiCert CA から登録機関 (RA) 証明書を取得するには、サブスクリプションが必要です。

## <a name="install-the-digicert-ra-certificate"></a>DigiCert RA 証明書をインストールする

1. 次のコード スニペットを **certreq.ini** という名前のファイルに保存し、必要に応じて更新します (例:*CN 形式のサブジェクト名*)。

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

2. 管理者特権でのコマンド プロンプトを開き、次のコマンドを使用して証明書署名要求 (CSR) を生成します。

   `Certreq.exe -new certreq.ini request.csr`

3. メモ帳で request.csr ファイルを開き、次の形式の CSR コンテンツをコピーします。

        -----BEGIN NEW CERTIFICATE REQUEST-----
        MIID8TCCAtkCAQAwbTEMMAoGA1UEBhMDVVNBMQswCQYDVQQIDAJXQTEQMA4GA1UE
        …
        …
        fzpeAWo=
        -----END NEW CERTIFICATE REQUEST-----


4. DigiCert CA にサインインし、タスクから **[Get an RA Cert]\(RA 証明書の取得\)** を参照します。

   」を参照します。 テキスト ボックスに、ステップ 3 の CSR コンテンツを入力します。

   b. 証明書のフレンドリ名を指定します。

   c. **[続行]** を選択します。

   d. 提供されたリンクを使用して、RA 証明書をローカル コンピューターにダウンロードします。

5. Windows 証明書ストアに RA 証明書をインポートします。

   」を参照します。 MMC コンソールを開きます。

   b. **[ファイル]**  >  **[スナップインの追加と削除]**  >  **[証明書]**  >  **[追加]** の順に選択します。

   c. **[コンピューター アカウント]**  >  **[次へ]** を選択します。

   d. **[ローカル コンピューター]**  >  **[完了]** を選択します。

   e. **[スナップインの追加と削除]** ウィンドウで、 **[OK]** を選択します。 **[証明書 (ローカル コンピューター)]**  >  **[個人]**  >  **[証明書]** の順に展開します。

   f. **[証明書]** ノードを右クリックし、 **[すべてのタスク]**  >  **[インポート]** の順にクリックします。

   g. DigiCert CA からダウンロードした RA 証明書の場所を選択し、 **[次へ]** を選択します。

   h. **[Personal Certificate Store]\(個人証明書ストア\)**  >  **[次へ]** を選択します。

   i. **[完了]** を選択して、RA 証明書とその秘密キーを**ローカル コンピューターの個人**ストアにインポートします。

6. 秘密キー証明書をエクスポートしインポートします。

   」を参照します。 **[証明書 (ローカル コンピューター)]**  >  **[個人]**  >  **[証明書]** の順に展開します。

   b. 前のステップでインポートした証明書を選択します。

   c. インポートした証明書を右クリックし、 **[すべてのタスク]**  >  **[エクスポート]** の順に選択します。

   d. **[次へ]** を選択し、パスワードを入力します。

   e. エクスポート先の場所を選択し、 **[完了]** を選択します。

   f. ステップ 5 の手順を使用して、**ローカル コンピューターの個人**ストアに秘密キー証明書をインポートします。

   g. スペースを除いて RA 証明書のサムプリントのコピーを記録します。 次にサムプリントの例を示します。

        RA Cert Thumbprint: “EA7A4E0CD1A4F81CF0740527C31A57F6020C17C5”

    > [!NOTE]
    > DigiCert CA から RA 証明書を取得する方法については、[DigiCert のカスタマー サポート](mailto:enterprise-pkisupport@digicert.com)にお問い合わせください。

## <a name="prepare-to-install-intune-certificate-connector"></a>Intune Certificate Connector のインストールの準備

> [!TIP]
> このセクションは、DigiCert CA のみで Intune Certificate Connector を使用する場合に適用されます。 Microsoft CA で Intune Certificate Connector を使用し、DigiCert CA のサポートを追加する場合は、「[DigiCert をサポートするようにコネクタを構成する](#configure-the-connector-to-support-digicert)」に進んでください。

1. 次の一覧からいずれかの Windows オペレーティング システムのバージョンを選択し、コンピューターにインストールします。
   * Windows Server 2012 R2 Datacenter
   * Windows Server 2012 R2 Standard
   * Windows Server 2016 Datacenter
   * Windows Server 2016 Standard

2. 管理特権を持つユーザーを作成し、このユーザーで以下の手順を実行します。

3. 最新の Windows 更新プログラムを確認し、利用できる場合はインストールします。 Windows 更新プログラムをインストールした後、コンピューターを再起動します。

4. .NET Framework 3.5 をインストールします。

   」を参照します。 **[コントロール パネル]**  >  **[プログラムと機能]**  >  **[Windows の機能の有効化または無効化]** の順に開きます。

   b. **[.NET Framework 3.5]** を選択してインストールします。

## <a name="install-intune-certificate-connector-for-use-with-digicert"></a>DigiCert で使用するための Intune Certificate Connector をインストールする

> [!TIP]
> Microsoft CA で Intune Certificate Connector を使用し、DigiCert CA のサポートを追加する場合は、「[DigiCert をサポートするようにコネクタを構成する](#configure-the-connector-to-support-digicert)」に進んでください。

Intune 管理ポータルから Intune Certificate Connector の最新バージョンをダウンロードし、次の手順のようにします。

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。

2. **[テナント管理]** 、 **[コネクタとトークン]** 、 **[証明書のコネクタ]** 、 **[+ 追加]** の順に選択します。

3. PKCS #12 のコネクタの *[Certificate Connector ソフトウェアをネットワーク上のセキュリティで保護された場所にダウンロード]* をクリックし、コネクタのインストール先となるサーバーからアクセスできる場所にファイルを保存します。

   ![コネクタ ソフトウェアをダウンロードする](./media/certificates-digicert-configure/connector-download.png)

4. コネクタをインストールするサーバーで、昇格された特権を使用して **NDESConnectorSetup.exe** を実行します。

5. **[Installation Options]\(インストール オプション\)** ページで、 **[PFX Distribution]\(PFX の配布\)** を選択します。

   ![[PFX Distribution]\(PFX の配布\) を選択する](./media/certificates-digicert-configure/digicert-ca-connector-install.png)

   > [!IMPORTANT]
   > Intune Certificate Connector を使用して Microsoft CA および DigiCert CA から証明書を発行する場合は、 **[SCEP および PFX プロファイルの配布]** を選択します。

6. 既定の選択を使用して、コネクタの設定を完了します。

## <a name="configure-the-connector-to-support-digicert"></a>DigiCert をサポートするようにコネクタを構成する

既定では、Intune Certificate Connector は **%ProgramFiles%\Microsoft Intune\NDESConnectorSvc** にインストールされます。

1. **NDESConnectorSvc** フォルダーの **NDESConnector.exe.config** ファイルをメモ帳で開きます。

   」を参照します。 `RACertThumbprint` キーの値を、前のセクションでコピーした証明書のサムプリントで更新します。 次に例を示します。

        <add key="RACertThumbprint"
        value="EA7A4E0CD1A4F81CF0740527C31A57F6020C17C5"/>

   b. ファイルを保存して閉じます。

2. **services.msc** を開きます。

   」を参照します。 **[Intune Connector Service]** を選択します。

   b. サービスを停止し、その後開始します。

   c. サービスのウィンドウを閉じます。

## <a name="set-up-the-intune-administrator-account"></a>Intune 管理者アカウントを設定する  

> [!TIP]
> Microsoft CA で Intune Certificate Connector を使用し、DigiCert CA のサポートを追加する場合は、「[信頼済み証明書プロファイルを作成する](#create-a-trusted-certificate-profile)」に進んでください。
 
1. NDES Connector のユーザー インターフェイスを **%ProgramFiles%\Microsoft Intune\NDESConnectorUI\NDESConnectorUI.exe** から開きます。

2. **[Enrollment]\(登録\)** タブで、 **[Sign In]\(サインイン\)** を選択します。

3. Intune のテナント管理者の資格情報を入力します。

4. **[Sign In]\(サインイン\)** を選択し、 **[OK]** を選択して、正常に登録されたことを確認します。 その後は、NDES Connector のユーザー インターフェイスを閉じてかまいません。

   !["登録成功" のメッセージが表示された NDES Connector のインターフェイス](./media/certificates-digicert-configure/certificates-digicert-configure-connector-configure.png)

## <a name="create-a-trusted-certificate-profile"></a>信頼済み証明書プロファイルを作成する

Intune マネージド デバイスに展開する PKCS 証明書は、信頼されたルート証明書にチェーンされている必要があります。 このチェーンを確立するには、DigiCert CA からのルート証明書を使用して、Intune の信頼済み証明書プロファイルを作成する必要があります。

1. DigiCert CA から信頼されたルート証明書を取得します。

   」を参照します。 DigiCert CA 管理ポータルにサインインします。

   b. **[Tasks]\(タスク\)** の **[Manage CAs]\(証明機関の管理\)** を選択します。

   c. 一覧から適切な CA を選択します。

   d. **[Download root certificate]\(ルート証明書のダウンロード\)** を選択して、信頼されたルート証明書をダウンロードします。

2. Intune ポータルで、信頼済み証明書プロファイルを作成します。

   」を参照します。 [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。

   b. **[デバイス]** 、 **[構成プロファイル]** 、 **[プロファイルの作成]** の順に選択します。

   c. 次のプロパティを入力します。

      - プロファイルの**名前**
      - オプションで**説明**を設定
      - プロファイルをデプロイする**プラットフォーム**
      - **[プロファイルの種類]** に **[信頼済み証明書]** を設定

   d. **[設定]** を選択し、この証明書プロファイルと共に使用する目的でエクスポートした、信頼されたルート CA 証明書 .cer ファイルを参照し、 **[OK]** を選択します。

   e. Windows 8.1 および Windows 10 デバイスの場合のみ、信頼された証明書の**保存先ストア**を以下から選択します。
      - **コンピューター証明書ストア - ルート**
      - **コンピューター証明書ストア - 中間**
      - **ユーザー証明書ストア - 中間**

   f. 完了したら、 **[OK]** を選択し、 **[プロファイルの作成]** ウィンドウに戻り、 **[作成]** を選択します。  

  プロファイルは **[デバイス構成 - プロファイル]** ウィンドウのプロファイル一覧に、 **[信頼済み証明書]** のプロファイルの種類と共に表示されます。  このプロファイルは必ず、証明書を受け取るデバイスに割り当ててください。 プロファイルをグループに割り当てる場合は、[デバイス プロファイルの割り当て](../configuration/device-profile-assign.md)に関するページを参照してください。


## <a name="get-the-certificate-profile-oid"></a>証明書プロファイル OID を取得する  

DigiCert CA の証明書プロファイル テンプレートには、証明書プロファイル OID が関連付けられています。 Intune で PKCS 証明書プロファイルを作成するには、証明書テンプレートの名前が、DigiCert CA の証明書テンプレートに関連付けられている証明書プロファイル OID の形式になっている必要があります。

1. DigiCert CA 管理ポータルにサインインします。
2. **[Manage Certificate Profiles]\(証明書プロファイルの管理\)** を選択します。
3. 使用する証明書プロファイルを選択します。
4. 証明書プロファイル OID をコピーします。 これは次の例のようなものです。

       Certificate Profile OID = 2.16.840.1.113733.1.16.1.2.3.1.1.47196109 

> [!NOTE]
> 証明書プロファイル OID の取得に関してサポートが必要な場合は、[DigiCert のカスタマー サポート](mailto:enterprise-pkisupport@digicert.com)にお問い合わせください。

## <a name="create-a-pkcs-certificate-profile"></a>PKCS 証明書プロファイルを作成する

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。

2. **[デバイス]** 、 **[構成プロファイル]** 、 **[プロファイルの作成]** の順に選択します。

3. 次のプロパティを入力します。

   - プロファイルの**名前**
   - オプションで**説明**を設定
   - プロファイルをデプロイする**プラットフォーム**
   - **[プロファイルの種類]** に **[PKCS 証明書]** を設定

4. **[PKCS 証明書]** ウィンドウで、次の表の値を使用してパラメーターを構成します。 これらの値は、Intune Certificate Connector を介して DigiCert CA から PKCS 証明書を発行するために必要です。

   |PKCS 証明書のパラメーター | 値 | 説明 |
   | --- | --- | --- |
   | 証明機関 | pki ws.symauth.com | この値には、末尾のスラッシュを除いた DigiCert CA のベース サービス FQDN を指定する必要があります。 この値が DigiCert CA サブスクリプションの正確なベース サービス FQDN であるか不明な場合は、DigiCert のカスタマー サポートに問い合わせてください。 <br><br>"*Symantec から DigiCert に変わっても、この URL は変更されていません*"。 <br><br> この FQDN が間違っている場合、Intune Certificate Connector では DigiCert CA から PKCS 証明書が発行されません。| 
   | 証明機関の名前 | Symantec | この値には、文字列 **Symantec** を指定する必要があります。 <br><br> この値を変更すると、Intune Certificate Connector で DigiCert CA から PKCS 証明書が発行されなくなります。|
   | 証明書テンプレート名 | DigiCert CA からの証明書プロファイル OID。 次に例を示します。**2.16.840.1.113733.1.16.1.2.3.1.1.61904612**| この値には、DigiCert CA 証明書プロファイル テンプレートから[前のセクションで取得した](#get-the-certificate-profile-oid)証明書プロファイル OID を指定する必要があります。 <br><br> Intune Certificate Connector で、DigiCert CA 内にこの証明書プロファイル OID に関連付けられている証明書テンプレートが見つからない場合、DigiCert CA から PKCS 証明書が発行されません。|

   ![CA と証明書テンプレートの選択](./media/certificates-digicert-configure/certificates-digicert-pkcs-example.png)

   > [!NOTE]
   > Windows プラットフォーム用の PKCS 証明書プロファイルを、信頼済み証明書プロファイルに関連付ける必要はありません。 ただし、Android など、Windows 以外のプラットフォームのプロファイルでは必要になります。

5. ビジネス ニーズに合わせてプロファイルの構成を完了した後、 **[作成]** を選択してプロファイルを保存します。

6. 新しいプロファイルの *[概要]* ページで **[割り当て]** を選択し、このプロファイルを受け取る適切なグループを構成します。 割り当てるグループには、1 名以上のユーザーまたは 1 台以上のデバイスが含まれている必要があります。
 
前のステップを完了すると、Intune Certificate Connector により、割り当てたグループの Intune マネージド デバイスに DigiCert CA から PKCS 証明書が発行されます。 これらの証明書は、Intune マネージド デバイスの **[現在のユーザー]** 証明書ストアの **[個人]** ストアで使用できるようになります。

### <a name="supported-attributes-for-the-pkcs-certificate-profile"></a>PKCS 証明書プロファイルでサポートされる属性

|属性 | Intune でサポートされる形式 | DigiCert Cloud CA でサポートされる形式 | 結果 |
| --- | --- | --- | --- |
| サブジェクト名 |Intune では、次の 3 つの形式のサブジェクト名のみがサポートされています。 <br><br> 1.一般的な名前 <br> 2.メール アドレスを含む共通名 <br> 3.メール アドレスとしての共通名 <br><br> 次に例を示します。 <br><br> `CN = IWUser0 <br><br> E = IWUser0@samplendes.onmicrosoft.com` | DigiCert CA では、さらに多くの属性がサポートされています。  他の属性を選択する場合は、DigiCert 証明書プロファイル テンプレートでそれらの属性に固定値を定義する必要があります。| ここでは、PKCS 証明書の要求の共通名またはメール アドレスを使用します。 <br><br> Intune 証明書プロファイルと DigiCert 証明書プロファイル テンプレートでの属性の選択内容に不一致がある場合、DigiCert CA から証明書が発行されません。|
| SAN | Intune では、次の SAN フィールド値のみがサポートされています。 <br><br> **AltNameTypeEmail** <br> **AltNameTypeUpn** <br> **AltNameTypeOtherName** (エンコードされた値) | これらのパラメーターは DigiCert Cloud CA でもサポートされています。 他の属性を選択する場合は、DigiCert 証明書プロファイル テンプレートでそれらの属性に固定値を定義する必要があります。 <br><br> **AltNameTypeEmail**: この種類が SAN で見つからない場合、Intune Certificate Connector では **AltNameTypeUpn** の値が使用されます。  SAN で **AltNameTypeUpn** も見つからない場合、Intune Certificate Connector ではサブジェクト名がメール アドレス形式であればその値が使用されます。  それでも種類が見つからない場合、Intune Certificate Connector による証明書の発行は失敗します。 <br><br> 例: `RFC822 Name=IWUser0@ndesvenkatb.onmicrosoft.com`  <br><br> **AltNameTypeUpn**: この種類が SAN で見つからない場合、Intune Certificate Connector では **AltNameTypeEmail** の値が使用されます。 SAN で **AltNameTypeEmail** も見つからない場合、Intune Certificate Connector ではサブジェクト名がメール アドレス形式であればその値が使用されます。 それでも種類が見つからない場合、Intune Certificate Connector による証明書の発行は失敗します。  <br><br> 例: `Other Name: Principal Name=IWUser0@ndesvenkatb.onmicrosoft.com` <br><br> **AltNameTypeOtherName**: SAN でこの種類が見つからない場合、Intune Certificate Connector による証明書の発行は失敗します。 <br><br> 例: `Other Name: DS Object Guid=04 12 b8 ba 65 41 f2 d4 07 41 a9 f7 47 08 f3 e4 28 5c ef 2c` <br><br>  DigiCert CA では、このフィールドの値についてはエンコードされた形式 (16 進値) のみがサポートされます。 このフィールドの値はすべて、証明書の要求の送信前に Intune Certificate Connector により base 64 エンコードに変換されます。 *Intune Certificate Connector では、この値がエンコード済みかどうかの確認は行われません。* | なし |

## <a name="troubleshooting"></a>トラブルシューティング

Intune Certificate Connector のサービス ログは、NDES Connector コンピューターの **%ProgramFiles%\Microsoft Intune\NDESConnectorSvc\Logs\Logs** にあります。 [SvcTraceViewer](https://docs.microsoft.com/dotnet/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe) でこのログを開き、例外またはエラー メッセージを検索します。

| 問題/エラー メッセージ | 解消手順 |
| --- | --- |
| Unable to sign in with the Intune tenant admin account on NDES Connector UI. (NDES Connector UI では Intune テナント管理者アカウントを使用してサインインできません。) | この問題は、Microsoft Endpoint Manager 管理センターでオンプレミスの Certificate Connector が有効になっていない場合に発生します。 この問題の解決策は、以下のとおりです。 <br><br> 1.[Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。 <br> 2. **[テナント管理]** 、 **[コネクタとトークン]** 、 **[証明書のコネクタ]** の順に選択します。 <br> 3.証明書コネクタを見つけ、有効になっていることを確認します。 <br><br> 上記の手順を完了してから、同じ Intune テナント管理者アカウントを使用して NDES Connector UI にサインインします。 |
| NDES Connector 証明書が見つかりませんでした。 <br><br> System.ArgumentNullException:値を null にすることはできません。 | Intune テナント管理者アカウントで NDES Connector UI へサインインしたことがない場合、Intune Certificate Connector にはこのエラーが表示されます。 <br><br> このエラーが引き続き発生する場合は、Intune Service Connector を再起動してください。 <br><br> 1.**services.msc** を開きます。 <br> 2. **[Intune Connector Service]** を選択します。 <br> 3.右クリックして **[再起動]** を選択します。|
| NDES Connector - IssuePfx -一般的な例外: <br> System.NullReferenceException:オブジェクト参照がオブジェクトのインスタンスに設定されていません。 | このエラーは一時的なものです。 Intune Service Connector を再起動してください。 <br><br> 1.**services.msc** を開きます。 <br> 2. **[Intune Connector Service]** を選択します。 <br> 3.右クリックして **[再起動]** を選択します。 |
| DigiCert プロバイダー - DigiCert ポリシーを取得できませんでした。 <br><br>"操作がタイムアウトしました。" | Intune Certificate Connector で、DigiCert CA との通信中に操作のタイムアウト エラーが発生しました。 このエラーが続く場合は、接続タイムアウトの値を増やしてからやり直してください。 <br><br> 接続タイムアウトを長くするには: <br> 1.NDES Connector コンピューターにアクセスします。 <br>2.メモ帳で **%ProgramFiles%\Microsoft Intune\NDESConnectorSvc\NDESConnector.exe.config** ファイルを開きます。 <br> 3.次のパラメーターのタイムアウト値を増やします。 <br><br> `CloudCAConnTimeoutInMilliseconds` <br><br> 4.Intune Certificate Connector サービスを再起動します。 <br><br> 問題が解決しない場合は、DigiCert カスタマー サポートに問い合わせてください。 |
| DigiCert プロバイダー - クライアント証明書を取得できません。 | Intune Certificate Connector が、ローカル コンピューターの個人証明書ストアからリソース承認証明書を取得できませんでした。 この問題を解決するには、ローカル コンピューターの個人証明書ストアにリソース承認証明書とその秘密キーをインストールします。 <br><br> リソース承認証明書は DigiCert CA から取得する必要があります。 詳細については、DigiCert カスタマー サポートに問い合わせてください。 | 
| DigiCert プロバイダー - DigiCert ポリシーを取得できませんでした。 <br><br>"要求が中止されました: SSL/TLS のセキュリティで保護されたチャネルを作成できませんでした。" | このエラーは、次のようなシナリオで発生します。 <br><br> 1.Intune Certificate Connector サービスに、ローカル コンピューターの個人ストアのリソース承認証明書とその秘密キーを読み取るためのアクセス許可が設定されていません。 この問題を解決するには、services.msc でコネクタ サービスが実行されているコンテキスト アカウントを確認します。 コネクタ サービスは、NT AUTHORITY\SYSTEM コンテキストで実行する必要があります。 <br><br> 2.Intune 管理ポータルの PKCS 証明書プロファイルに無効な DigiCert CA のベース サービス FQDN が設定されている可能性があります。 FQDN は **pki-ws.symauth.com** のようなものです。 この問題を解決するには、この URL が使用中のサブスクリプションに合っているかどうかを DigiCert カスタマー サポートに確認してください。 <br><br> 3.Intune Certificate Connector が、秘密キーを取得できないため、リソース承認証明書を使用して DigiCert CA で認証を行うことができません。 この問題を解決するには、ローカル コンピューターの個人証明書ストアにリソース承認証明書とその秘密キーをインストールします。 <br><br> 問題が解決しない場合は、DigiCert カスタマー サポートに問い合わせてください。 |
| DigiCert プロバイダー - DigiCert ポリシーを取得できませんでした。 <br><br>"要求要素が認識されていません。" | クライアント プロファイル OID と Intune 証明書プロファイルが一致しないため、Intune Certificate Connector で DigiCert 証明書プロファイル テンプレートを取得できませんでした。 または、Intune Certificate Connector が、DigiCert CA のクライアント プロファイル OID に関連付けられている証明書プロファイル テンプレートを見つけられません。 <br><br> この問題を解決するには、DigiCert CA の DigiCert 証明書テンプレートから適切なクライアント プロファイル OID を取得します。 Intune 管理ポータルで PKCS 証明書プロファイルを更新します。 <br><br> DigiCert CA からクライアント プロファイル OID を取得します。 <br> 1.DigiCert CA 管理ポータルにサインインします。 <br> 2. **[Manage Certificate Profiles]\(証明書プロファイルの管理\)** を選択します。 <br> 3.使用する証明書プロファイルを選択します。 <br> 4.証明書プロファイル OID を取得します。 これは次の例のようなものです。 <br> `Certificate Profile OID = 2.16.840.1.113733.1.16.1.2.3.1.1.47196109` <br><br> 適切な証明書プロファイル OID で PKCS 証明書プロファイルを更新します。 <br>1.Intune 管理ポータルにサインインします。 <br> 2.PKCS 証明書プロファイルに移動し、 **[編集]** を選択します。 <br> 3.証明書テンプレート名のフィールドの証明書プロファイル OID を更新します。 <br> 4.PKCS 証明書プロファイルを保存します。 |
| DigiCert プロバイダー - ポリシーの検証に失敗しました。 <br><br> The attribute doesn't fall under the DigiCert supported certificate template attributes list. (DigiCert でサポートされる証明書テンプレートの属性一覧に属性が含まれていません。) | DigiCert 証明書プロファイル テンプレートと Intune 証明書プロファイルに不一致がある場合、DigiCert CA によりこのメッセージが表示されます。 この問題の原因は、**SubjectName** 属性または **SubjectAltName** 属性の不一致であると考えられます。 <br><br> この問題を解決するには、DigiCert 証明書プロファイル テンプレートの **SubjectName** および **SubjectAltName** に対して Intune でサポートされる属性を選択します。 詳細については、**証明書パラメーター**に関するセクションで Intune でサポートされる属性をご覧ください。 |
| Some user devices are not receiving PKCS certificates from the DigiCert CA. (一部のユーザー デバイスで、DigiCert CA から PKCS 証明書が受信されません。) | この問題は、ユーザー UPN にアンダースコアなどの特殊文字 (例: `global_admin@intune.onmicrosoft.com`) が含まれている場合に発生します。 <br><br> DigiCert CA の **mail_firstname** および **mail_lastname** では特殊文字はサポートされません。 <br><br> この問題を解決するには、次の手順を実行します。 <br><br> 1.DigiCert CA 管理ポータルにサインインします。 <br> 2. **[Manage Certificate Profiles]\(証明書プロファイルの管理\)** に移動します。 <br> 3.Intune で使用している証明書プロファイルを選択します。 <br> 4. **[Customize options]\(カスタマイズ オプション\)** リンクを選択します。 <br> 5. **[Advanced options]\(詳細オプション\)** ボタンを選択します。 <br> 6. **[Certificate fields – Subject DN]\(証明書のフィールド – サブジェクト DN\)** で、 **[Common Name (CN)]\(共通名 (CN)\)** フィールドを追加し、既存の **[Common Name (CN)]\(共通名 (CN)\)** フィールドを削除します。 追加と削除の操作は一度に実行する必要があります。 <br> 7. **[保存]** を選択します。 <br><br> 上記の変更により、DigiCert 証明書プロファイルでは **mail_firstname** と **mail_lastname** の代わりに **"CN=<upn>"** が要求されるようになります。 |
| ユーザーが、展開済みの証明書をデバイスから手動で削除しました。 | Intune により、次のチェックイン時またはポリシー適用中に同一の証明書が再展開されます。 この場合、NDES Connector は PKCS 証明書要求を受信しません。 |

## <a name="next-steps"></a>次の手順

この記事の情報と [Microsoft Intune のデバイス プロファイル](../configuration/device-profiles.md)に関する記事の情報を合わせて、組織のデバイスとその証明書を管理します。
