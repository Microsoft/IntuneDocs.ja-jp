---
title: Microsoft Intune で秘密キーと公開キーの証明書を使用する - Azure | Microsoft Docs
description: Microsoft Intune で公開キー暗号化標準 (PKCS) 証明書を使用する これには、ルート証明書と証明書テンプレートの使用、Intune Certificate Connector (NDES) のインストール、PKCS 証明書のデバイス構成プロファイルの使用が含まれます。
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
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3db085e6e88f8f57eb0276afa77290df8574568f
ms.sourcegitcommit: b5e719fb507b1bc4774674e76c856c435e69f68c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/08/2019
ms.locfileid: "73801700"
---
# <a name="configure-and-use-pkcs-certificates-with-intune"></a>Intune で PKCS 証明書を構成して使用する

Intune では、秘密キーと公開キーのペア (PKCS) の証明書の使用がサポートされています。 この記事は、オンプレミスの証明書コネクタなどの必要なインフラストラクチャを構成し、PKCS 証明書をエクスポートして、Intune デバイス構成プロファイルに証明書を追加するのに役立ちます。

Microsoft Intune には、組織のリソースへのアクセスと認証に PKCS 証明書を使用するための組み込みの設定が含まれています。 証明書により、VPN や WiFi ネットワークなど、企業リソースへのアクセスが認証され、セキュリティで保護されます。 Intune でデバイス構成プロファイルを使用してこれらの設定をデバイスに展開します。

インポートした PKCS 証明書の使用については、[インポートした PFX 証明書](certificates-imported-pfx-configure.md)に関する記事をご覧ください。


## <a name="requirements"></a>要件

Intune で PKCS 証明書を使用するには、次のインフラストラクチャが必要です。

- **Active Directory ドメイン**:  
  このセクションで示されているすべてのサーバーは、Active Directory ドメインに参加する必要があります。

  Active Directory Domain Services (AD DS) をインストールして構成する詳細については、「[Active Directory の設計と計画について](https://docs.microsoft.com/windows-server/identity/ad-ds/plan/ad-ds-design-and-planning)」を参照してください。

- **証明機関**:  
   エンタープライズ証明機関 (CA)。

  Active Directory 証明書サービス (AD CS) のインストールおよび構成の詳細については、「[Active Directory 証明書サービス ステップ バイ ステップ ガイド](https://technet.microsoft.com/library/cc772393)」を参照してください。

  > [!WARNING]  
  > Intune ではスタンドアロン CA ではなく、エンタープライズ証明機関 (CA) の AD CS を実行する必要があります。

- **クライアント**:  
  エンタープライズ CA に接続する。

- **ルート証明書**:  
  エンタープライズ CA のルート証明書のエクスポートされたコピーです。

- **Microsoft Intune Certificate Connector** ("*NDES 証明書コネクタ*" とも呼ばれます):  
  Intune ポータルで、 **[デバイス構成]**  >  **[証明書コネクタ]**  >  **[追加]** の順に移動して、*PKCS #12 用コネクタをインストールする手順*に従います。 ポータルのダウンロード リンクを使用して、証明書コネクタのインストーラー **NDESConnectorSetup.exe** のダウンロードを開始します。  

  Intune では、テナントごとにこのコネクタのインスタンスが最大 100 サポートされます。 コネクタの各インスタンスは、別個の Windows サーバー上に置く必要があります。 このコネクタのインスタンスは、Microsoft Intune 用の PFX Certificate Connector のインスタンスと同じサーバー上にインストールできます。 複数のコネクタを使用する場合、コネクタのインフラストラクチャでは、使用可能なコネクタ インスタンスによって PKCS 証明書要求を処理できるため、高可用性と負荷分散がサポートされます。 

  このコネクタは、認証または S/MIME メールの署名で使用される PKCS 証明書の要求を処理します。

  Microsoft Intune Certificate Connector では、Federal Information Processing Standard (FIPS) モードもサポートされています。 FIPS は必須ではありませんが、有効になっている場合は、証明書の発行および失効を行うことができます。

- **PFX Certificate Connector for Microsoft Intune**:  
  S/MIME メールの暗号化の使用を計画している場合は、Intune ポータルを使用して、PFX 証明書のインポートをサポートする *PFX Certificate Connector* をダウンロードします。  **[デバイス構成]**  >  **[証明書コネクタ]**  >  **[追加]** の順に移動して、*インポートした PFX 証明書用コネクタをインストールする手順*に従います。 ポータルのダウンロード リンクを使用して、インストーラー **PfxCertificateConnectorBootstrapper.exe** のダウンロードを開始します。 

  各 Intune テナントでは、このコネクタの 1 つのインスタンスがサポートされます。 Microsoft Intune Certificate Connector のインスタンスと同じサーバー上に、このコネクタをインストールできます。

  このコネクタでは、特定のユーザーを対象にした S/MIME メールの暗号化のために Intune にインポートされる PFX ファイルに対する要求を処理します。  

  このコネクタは、新しいバージョンが利用可能になったときに自動更新することができます。 更新機能を使用するには、次の操作を実行する必要があります。
  - PFX Certificate Connector for Microsoft Intune をサーバーにインストールします。  
  - 重要な更新プログラムを自動的に受け取るには、確実にファイアウォールがオープンになっていることを確認し、コネクタがポート **443** で **autoupdate.msappproxy.net** にコンタクトできるようにします。   

  Intune とコネクタでアクセスするネットワーク エンドポイントについて詳しくは、「[Microsoft Intune のネットワーク エンドポイント](../fundamentals/intune-endpoints.md)」をご覧ください。

- **Windows Server**:  
  Windows Server をホストに使用します。

  - 認証および S/MIME メールの署名のシナリオ用の Microsoft Intune Certificate Connector
  - S/MIME メールの暗号化シナリオ用の PFX Certificate Connector for Microsoft Intune

  Intune では、*Microsoft Intune Certificate Connector* と同じサーバー上に *PFX Certificate Connector* をインストールすることができます。
  
## <a name="export-the-root-certificate-from-the-enterprise-ca"></a>エンタープライズ CA からルート証明書をエクスポートする

VPN、WiFi、またはその他のリソースを使用してデバイスを認証するには、デバイスにルートまたは中間の CA 証明書が必要です。 次の手順では、エンタープライズ CA から必要な証明書を取得する方法について説明します。

**コマンド ラインの使用**:  
1. 管理者アカウントでルート証明機関サーバーにログインします。
 
2. **[スタート]**  >  **[実行]** の順に移動し、「**Cmd**」を入力してコマンド プロンプトを開きます。 
    
3. **certutil -ca.cert ca_name.cer** を指定して、ルート証明書を *ca_name.cer* という名前のファイルとしてエクスポートします。



## <a name="configure-certificate-templates-on-the-ca"></a>CA 上で証明書テンプレートを構成する

1. 管理特権があるアカウントでエンタープライズ CA にサインインします。
2. **[証明機関]** コンソールで **[証明書テンプレート]** を右クリックして **[管理]** を選択します。
3. **User** 証明書テンプレートを探して右クリックし、 **[テンプレートの複製]** を選択して **[新しいテンプレートのプロパティ]** を開きます。

    > [!NOTE]
    > S/MIME メールの署名と暗号化のシナリオの場合、管理者の多くは、署名と暗号化に対して別々の証明書を使用します。 Microsoft Active Directory Certificate Services を使用している場合、S/MIME メールの署名証明書には **[Exchange 署名のみ]** テンプレートを使用し、S/MIME 暗号化証明書には **[Exchange ユーザー]** テンプレートを使用することができます。  サード パーティ証明機関を使用している場合は、該当するガイダンスを確認して署名および暗号化のテンプレートを設定することをお勧めします。

4. **[互換性]** タブで:

    - **[証明機関]** に **[Windows Server 2008 R2]** を設定します。
    - **[証明書の受信者]** に **[Windows 7 / Server 2008 R2]** を設定します。

5. **[全般]** タブで、 **[テンプレート表示名]** にわかりやすい名前を設定します。

    > [!WARNING]
    > 既定では、 **[テンプレート名]** は **[テンプレート表示名]** (*スペースなし*) と同じです。 テンプレートの名前をメモします。後で必要になります。

6. **[要求処理]** で、 **[プライベート キーのエクスポートを許可する]** を選択します。
7. **[暗号化]** で、 **[最小キー サイズ]** が 2048 に設定されていることを確認します。
8. **[サブジェクト名]** で **[要求に含まれる]** を選択します。
9. **[拡張子]** で、 **[アプリケーション ポリシー]** に暗号化ファイル システム、セキュリティで保護された電子メール、クライアント認証が表示されていることを確認します。

    > [!IMPORTANT]
    > iOS の証明書テンプレートの場合、 **[拡張]** タブで、 **[キー使用法]** を更新し、 **[署名は発行元の証明である]** が選択されていないことを確認します。

10. **[セキュリティ]** で、Microsoft Intune Certificate Connector をインストールするサーバーのコンピューター アカウントを追加します。 このアカウントに、**読み取り**と**登録**のアクセス許可を割り当てます。
11. **[適用]**  >  **[OK]** をクリックして証明書テンプレートを保存します。 **証明書テンプレート コンソール**を閉じます。
12. **[証明機関]** コンソールで **[証明書テンプレート]** を右クリックして、 **[新規作成]**  >  **[発行する証明書テンプレート]** をクリックします。 上記の手順で作成したテンプレートを選択します。 **[OK]** を選択します。
13. 登録されたデバイスとユーザーの証明書をサーバーで管理する場合は、次の手順を使用します。

    1. 証明機関を右クリックして、 **[プロパティ]** を選択します。
    2. [セキュリティ] タブで、コネクタ (**Microsoft Intune Certificate Connector** または **PFX Certificate Connector for Microsoft Intune**) を実行するサーバーのコンピューター アカウントを追加します。 
    3. このコンピューター アカウントに、**証明書の発行と管理**と**証明書の要求**のアクセス許可を付与します。

14. エンタープライズ CA からサインアウトします。

## <a name="download-install-and-configure-the-microsoft-intune-certificate-connector"></a>Microsoft Intune Certificate Connector のダウンロード、インストール、および構成

> [!IMPORTANT]  
> Microsoft Intune Certificate Connector を、発行元証明機関 (CA) にインストールすることはできません。代わりに、別の Windows サーバーにインストールする必要があります。  

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。

2. **[テナント管理]** 、 **[コネクタとトークン]** 、 **[証明書のコネクタ]** 、 **[+ 追加]** の順に選択します。

3. PKCS #12 のコネクタの *[Certificate Connector ソフトウェアをネットワーク上のセキュリティで保護された場所にダウンロード]* をクリックし、コネクタのインストール先となるサーバーからアクセスできる場所にファイルを保存します。

   ![Microsoft Intune Certificate Connector のダウンロード](./media/certficates-pfx-configure/download-ndes-connector.png)
 
4. ダウンロードが完了したら、サーバーにサインインします。 次のことを行います。

    1. .NET Framework 4.5 以降がインストールされていることを確認します。NDES 証明書コネクタで必要となるからです。 .NET Framework 4.5 は、Windows Server 2012 R2 およびそれ以降の新しいバージョンには自動的に含められます。
    2. インストーラー (NDESConnectorSetup.exe) を実行し、既定の場所を受け入れます。 コネクターは `\Program Files\Microsoft Intune\NDESConnectorUI` にインストールされます。 [インストーラー オプション] で **[PFX の配布]** を選択します。 インストールを継続し完了させます。
    3. 既定では、コネクタ サービスはローカル システム アカウントの下で実行されます。 インターネットにアクセスするのにプロキシが必要な場合は、ローカル サービス アカウントがサーバー上のプロキシ設定にアクセスできることを確認します。

5. Microsoft Intune Certificate Connector 上で、 **[登録]** タブが開かれます。Intune への接続を有効にするには、 **[サインイン]** を選択し、グローバル管理アクセス許可を持つアカウントを入力します。
6. **[詳細設定]** タブでは、 **[このコンピューターの SYSTEM アカウントを使用する (既定)]** をオンのままにすることをお勧めします。
7. **[適用]**  >  **[閉じる]** を選択します
8. Intune ポータルに戻ります ( **[Intune]**  >  **[デバイス構成]**  >  **[証明書のコネクタ]** )。 しばらくすると、緑のチェックマークが表示され、 **[接続の状態]** が **[アクティブ]** になります。 これでコネクタ サーバーは Intune と通信できます。
9. ご利用のネットワーク環境に Web プロキシがある場合、コネクタが動作するように追加の構成が必要になる可能性があります。 詳細については、Azure Active Directory ドキュメントの「[既存のオンプレミス プロキシ サーバーと連携する](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-configure-connectors-with-proxy-servers)」を参照してください。

> [!NOTE]  
> Microsoft Intune Certificate Connector では、TLS 1.2 がサポートされています。 TLS 1.2 がコネクタをホストするサーバーにインストールされている場合、コネクタは TLS 1.2 を使用します。 それ以外の場合は、TLS 1.1 が使用されます。 現在、デバイスとサーバー間の認証には、TLS 1.1 が使用されています。

## <a name="create-a-trusted-certificate-profile"></a>信頼済み証明書プロファイルを作成する

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。

2. **[デバイス]** 、 **[構成プロファイル]** 、 **[プロファイルの作成]** の順に選択します。

   ![Intune に移動して信頼済み証明書用に新しいプロファイルを作成する](./media/certficates-pfx-configure/certificates-pfx-configure-profile-new.png)

3. 次のプロパティを入力します。

    - プロファイルの**名前**
    - オプションで説明を設定
    - プロファイルをデプロイする**プラットフォーム**
    - **[プロファイルの種類]** に **[信頼済み証明書]** を設定

4. **[設定]** を選択し、以前エクスポートした .cer ファイルのルート CA 証明書を指定します。

   > [!NOTE]
   > **手順 2** で選択したプラットフォームに応じて、証明書の**保存先ストア**を選択するオプションが使用できる場合と使用できない場合があります。

   ![プロファイルを作成し、信頼済み証明書をアップロードする](./media/certficates-pfx-configure/certificates-pfx-configure-profile-fill.png)

5. **[OK]**  >  **[作成]** を選択してプロファイルを保存します。

6. 1 つ以上のデバイスに新しいプロファイルを割り当てる場合は、[Microsoft Intune のデバイス プロファイルの割り当て](../configuration/device-profile-assign.md)に関するページをご覧ください。

## <a name="create-a-pkcs-certificate-profile"></a>PKCS 証明書プロファイルを作成する

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。

2. **[デバイス]** 、 **[構成プロファイル]** 、 **[プロファイルの作成]** の順に移動します。

3. 次のプロパティを入力します。

    - プロファイルの**名前**
    - オプションで説明を設定
    - プロファイルをデプロイする**プラットフォーム**
    - **[プロファイルの種類]** に **[PKCS 証明書]** を設定

4. **[設定]** を選択し、選択したプラットフォームに適用されるプロパティを構成します。
   
   |設定     | プラットフォーム     | 説明   |
   |------------|------------|------------|
   |**[更新しきい値 (%)]**        |すべて         |推奨値は 20% です  | 
   |**[証明書の有効期間]**  |すべて         |証明書テンプレートを変更していない場合、このオプションはおそらく 1 年に設定されています。 |
   |**キー記憶域プロバイダー (KSP)**   |Windows 10  | Windows では、デバイス上のキーを格納する場所を選択します。 |
   |**証明機関**      |すべて         |エンタープライズ CA の内部完全修飾ドメイン名 (FQDN) が表示されます。  |
   |**証明機関名** |すべて         |"Contoso Certification Authority" など、エンタープライズ CA の名前が一覧表示されます。 |
   |**証明書の種類**             |macOS       |種類の選択: <br> **-** **ユーザー**証明書では、証明書のサブジェクトと SAN 内にユーザー属性とデバイス属性の両方を含めることができます。 <br><br>**-** **[デバイス]** 証明書では、証明書のサブジェクトと SAN にデバイスの属性を含めることができます。 キオスクやその他の共有デバイスなど、ユーザーのいないデバイスなどのシナリオには、[デバイス] を使用します。  <br><br> この選択は、サブジェクト名の形式に影響します。 |
   |**[サブジェクト名の形式]**          |すべて         |ほとんどのプラットフォームでは、特に指定がない限り、このオプションは**共通名**に設定します。<br><br>macOS の場合、サブジェクト名の形式は証明書の種類によって決まります。 この記事の後半に登場するセクション「[macOS のサブジェクト名の形式](#subject-name-format-for-macos)」を参照してください。 |
   |**[サブジェクトの別名]**     |すべて         |特に指定がない限り、このオプションは**ユーザー プリンシパル名 (UPN)** に設定します。 |
   |**[拡張キー使用法]**           |**-** Android デバイス管理者 <br>**-** Android エンタープライズ (*デバイス所有者*、*仕事用プロファイル*) <br> **-** Windows 10 |ユーザーまたはデバイスがサーバーに対して認証できるように、証明書には通常、 *[クライアント認証]* が必要です。 |
   |**[すべてのアプリが秘密キーにアクセスできるようにする]** |macOS  |**[有効にする]** に設定すると、PKCS 証明書の秘密キーへのアクセスが関連 mac デバイスに構成されているアプリに与えられます。 <br><br> この設定の詳細については、Apple 開発者ドキュメントにある「[Configuration Profile Reference](https://developer.apple.com/business/documentation/Configuration-Profile-Reference.pdf)」の「Certificate Payload」セクションに記載されている *AllowAllAppsAccess* を参照してください。 |
   |**ルート証明書**             |**-** Android デバイス管理者 <br> **-** Android エンタープライズ (*デバイス所有者*、*仕事用プロファイル*) |前に割り当てられたルート CA 証明書プロファイルを選択します。 |

5. **[OK]**  >  **[作成]** を選択してプロファイルを保存します。

6. 1 つ以上のデバイスに新しいプロファイルを割り当てる場合は、[Microsoft Intune のデバイス プロファイルの割り当て](../configuration/device-profile-assign.md)に関するページをご覧ください。

   > [!NOTE]
   > Android エンタープライズ プロファイルを使用しているデバイスでは、PKCS 証明書プロファイルを使用してインストールされた証明書は、デバイス上に表示されません。 証明書の展開に成功したことを確認するには、Intune コンソール上でプロファイルの状態を確認します。

### <a name="subject-name-format-for-macos"></a>macOS のサブジェクト名の形式

macOS PKCS 証明書プロファイルを作成するとき、サブジェクト名の形式のオプションは、選択した証明書の種類 ( **[ユーザー]** または **[デバイス]** ) によって異なります。  

> [!NOTE]  
> PKCS を使用した証明書の取得について、生成される証明書署名要求 (CSR) 内のサブジェクト名に次の文字のいずれかがエスケープ文字 (前にバックスラッシュ \\ が付く) として含まれていた場合に関する既知の問題があります。[SCEP でも同じ問題が確認されています](certificates-profile-scep.md#avoid-certificate-signing-requests-with-escaped-special-characters)。
> - \+
> - ;
> - 、
> - =

- **ユーザー証明書の種類**  
  *[サブジェクト名の形式]* の形式オプションが 2 つあります。**共通名 (CN)** と**電子メール (E)** ) をサポートしています。 **共通名 (CN)** は、次のいずれかの変数に設定できます。

  - **CN={{UserName}}** : janedoe@contoso.com など、ユーザーのユーザー プリンシパル名。
  - **CN={{AAD_Device_ID}}** : Azure Active Directory (AD) にデバイスを登録するときに割り当てられた ID。 通常、この ID は Azure AD での認証に使われます。
  - **CN={{SERIALNUMBER}}** : 一意のシリアル番号 (SN)。通常はデバイスを識別するために製造元によって使われます。
  - **CN={{IMEINumber}}** : 携帯電話の識別に使用される IMEI (International Mobile Equipment Identity) の一意の番号です。
  - **CN={{OnPrem_Distinguished_Name}}** : コンマで区切られた相対識別名のシーケンスです (*CN=Jane Doe,OU=UserAccounts,DC=corp,DC=contoso,DC=com* など)。

    *{{OnPrem_Distinguished_Name}}* 変数を使用するには、[Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) を使用して、*onpremisesdistinguishedname* ユーザー属性をご自分の Azure AD に同期してください。

  - **CN={{onPremisesSamAccountName}}** : 管理者は、Azure AD Connect を使用して、Active Directory の samAccountName 属性を、Azure AD の *onPremisesSamAccountName* という属性に同期できます。 Intune では、証明書のサブジェクト内の証明書発行要求の一部として、その変数を置き換えることができます。 samAccountName 属性は、以前のバージョンの Windows (windows 2000 より前) のクライアントとサーバーをサポートするために使われるユーザー サインイン名です。 ユーザー サインイン名の形式は次のとおりです。*DomainName\testUser*、または *testUser* のみ。

    *{{onPremisesSamAccountName}}* 変数を使用するには、[Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) を使用して、*onPremisesSamAccountName* ユーザー属性をご自分の Azure AD に同期してください。

  これらの変数と静的文字列の 1 つまたは複数を組み合わせて使用することで、次のようなサブジェクト名のカスタム形式を作成できます。  
  - **CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US**
  
  その例には、CN 変数と E 変数に加えて、組織単位、組織、場所、州、国の各値を表す文字列を使用するサブジェクト名形式が含まれています。 [CertStrToName 関数](https://msdn.microsoft.com/library/windows/desktop/aa377160.aspx)の記事では、この関数とそのサポートされる文字列について説明されています。

- **デバイス証明書の種類**  
  サブジェクト名の形式のフォーマットオプションには、次の変数が含まれます。 
  - **{{AAD_Device_ID}}**
  - **{{Device_Serial}}**
  - **{{Device_IMEI}}**
  - **{{SerialNumber}}**
  - **{{IMEINumber}}**
  - **{{AzureADDeviceId}}**
  - **{{WiFiMacAddress}}**
  - **{{IMEI}}**
  - **{{DeviceName}}**
  - **{{FullyQualifiedDomainName}}** *(Windows およびドメインに参加しているデバイスにのみ適用)*
  - **{{MEID}}**

  これらの変数は、テキスト ボックスで指定し、その後に変数のテキストを続けることができます。 たとえば、*Device1* という名前のデバイスの共通名は、**CN={{DeviceName}}Device1** として追加できます。

  > [!IMPORTANT]  
  > - 変数を指定する場合は、エラーが発生しないように、例に示すように、変数名を中かっこ { } で囲みます。  
  > - デバイス証明書の "*サブジェクト*" または *SAN* で使用されるデバイス プロパティ (**IMEI**、**SerialNumber**、**FullyQualifiedDomainName** など) は、デバイスへのアクセス権を持つユーザーによってスプーフィングされる可能性のあるプロパティです。
  > - 証明書プロファイルをデバイスにインストールする場合は、そのプロファイルで指定されたすべての変数が該当するデバイスでサポートされている必要があります。  たとえば、 **{{IMEI}}** が SCEP プロファイルのサブジェクト名に使用されていて、IMEI 番号を持たないデバイスに割り当てられている場合、プロファイルのインストールは失敗します。  
 


## <a name="whats-new-for-connectors"></a>コネクタの新機能

2 つの証明書コネクタの更新プログラムは、定期的にリリースされます。 コネクタが更新された場合、その変更についてここから確認することができます。

*PFX Certificates Connector for Microsoft Intune* が[自動更新をサポート](#requirements)しているのに対し、*Intune Certificate Connector* は手動で更新されます。

### <a name="may-17-2019"></a>2019 年 5 月 17 日

- **PFX Certificate Connector for Microsoft Intune - バージョン 6.1905.0.404**  
  このリリースの変更点:  
  - コネクタで新しい要求の処理が停止される原因となる、既存の PFX 証明書の再処理が続行される問題を修正しました。 

### <a name="may-6-2019"></a>2019 年 5 月 6 日

- **PFX Certificate Connector for Microsoft Intune - バージョン 6.1905.0.402**  
  このリリースの変更点:  
  - コネクタのポーリング間隔が、5 分から 30 秒に短縮されました。
 
### <a name="april-2-2019"></a>2019 年 4 月 2 日

- **Intune Certificate Connector - バージョン 6.1904.1.0**  
  このリリースの変更点:  
  - グローバル管理者アカウントを使用してコネクタにサインインした後に、コネクタが Intune への登録に失敗することがある問題を修正しました。  
  - 証明書の失効への信頼性の修正が含まれています。  
  - PKCS 証明書の要求の処理速度を向上するパフォーマンスの修正が含まれています。  

- **PFX Certificate Connector for Microsoft Intune - バージョン 6.1904.0.401**
  > [!NOTE]  
  > PFX コネクタのこのバージョンの自動更新は、2019 年 4 月 11 日まで使用できません。  

  このリリースの変更点:  
  - グローバル管理者アカウントを使用してコネクタにサインインした後に、コネクタが Intune への登録に失敗することがある問題を修正しました。  


## <a name="next-steps"></a>次の手順

プロファイルは作成されましたが、まだ何も行われていません。 次に、[プロファイルを割り当て](../configuration/device-profile-assign.md)、[その状態を監視](../configuration/device-profile-monitor.md)します。

[証明書に SCEP を使用](certificates-scep-configure.md)するか、[Symantec PKI マネージャー Web サービスから PKCS 証明書を発行](certificates-digicert-configure.md)します。
