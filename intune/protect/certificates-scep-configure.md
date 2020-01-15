---
title: Microsoft Intune を使用して SCEP 証明書プロファイルをサポートするようにインフラストラクチャを構成する - Azure | Microsoft Docs
description: SCEP を Microsoft Intune で使うには、オンプレミスの AD ドメインを構成し、証明機関を作成し、NDES サーバーを設定して、Intune Certificate Connector をインストールします。
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
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 501bfcbef0dd46f6021fc5db16cf3b9e2f2cd0c0
ms.sourcegitcommit: 2506cdbfccefd42587a76f14ee50c3849dad1708
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/11/2020
ms.locfileid: "75886004"
---
# <a name="configure-infrastructure-to-support-scep-with-intune"></a>Intune を使用して SCEP をサポートするようにインフラストラクチャを構成する

Intune では、[アプリと企業リソースへの接続を認証する](certificates-configure.md)ために Simple Certificate Enrollment Protocol (SCEP) の使用がサポートされています。 SCEP では、証明機関 (CA) 証明書を使用して、証明書署名要求 (CSR) のメッセージ交換をセキュリティで保護します。 ご使用のインフラストラクチャで SCEP がサポートされている場合は、Intune *SCEP 証明書*プロファイル (Intune のデバイス プロファイルの種類) を使用して、証明書をご使用のデバイスに展開することができます。 Active Directory 証明書サービス証明機関を使用する場合、Intune で SCEP 証明書プロファイルを使用するには、Microsoft Intune Certificate Connector が必要です。 [サードパーティの証明機関](certificate-authority-add-scep-overview.md#set-up-third-party-ca-integration)を使用する場合、コネクタは必要ありません。 

この記事の情報は、Active Directory 証明書サービスを使用する場合に、SCEP をサポートするようにインフラストラクチャを構成するのに役立ちます。 インフラストラクチャを構成したら、Intune で [SCEP 証明書プロファイルを作成して展開](certificates-profile-scep.md)できます。

> [!TIP]
> Intune では、[Public Key Cryptography Standards #12 証明書](certficates-pfx-configure.md)の使用もサポートされています。

## <a name="prerequisites-for-using-scep-for-certificates"></a>証明書に SCEP を使用するための前提条件

続行する前に、[*信頼済み証明書*プロファイルを作成し、SCEP 証明書プロファイルを使用するデバイスに展開](certificates-configure.md#export-the-trusted-root-ca-certificate)していることを確認してください。 SCEP 証明書プロファイルでは、信頼されたルート CA 証明書を使用してデバイスをプロビジョニングするために使用する、信頼済み証明書プロファイルが直接参照されます。

### <a name="servers-and-server-roles"></a>サーバーとサーバー ロール

次のオンプレミス インフラストラクチャは、Active Directory にドメイン参加しているサーバー (Web アプリケーション プロキシ サーバーを除く) で実行する必要があります。

- **証明機関** – Windows Server 2008 R2 Service Pack 1 以降の Enterprise エディション上で実行する Microsoft Active Directory 証明書サービスのエンタープライズ証明機関 (CA) を使用します。 使用する Windows Server のバージョンが、Microsoft によって引き続きサポートされている必要があります。 スタンドアロン CA はサポートされません。 詳細については、「[証明機関のインストール](https://technet.microsoft.com/library/jj125375.aspx)」を参照してください。 ご使用の CA で Windows Server 2008 R2 SP1 が実行されている場合は、[KB2483564 の修正プログラムをインストール](https://support.microsoft.com/kb/2483564/)する必要があります。

- **NDES サーバー ロール** – Windows Server 2012 R2 以降で、ネットワーク デバイス登録サービス (NDES) サーバー ロールを構成する必要があります。 [NDES のインストール](#set-up-ndes)については、この記事内の後のセクションで説明します。

  - NDES をホストするサーバーは、ドメインに参加している必要があり、ご使用のエンタープライズ CA と同じフォレストにある必要があります。
  - エンタープライズ CA をホストするサーバーにインストールされている NDES を使用することはできません。
  - NDES をホストしているのと同じサーバーに、Microsoft Intune Certificate Connector をインストールします。

  NDES の詳細については、Windows Server のドキュメントの「[ネットワーク デバイス登録サービスのガイダンス](https://technet.microsoft.com/library/hh831498.aspx)」、および「[ポリシー モジュールとネットワーク デバイス登録サービスの使用](https://technet.microsoft.com/library/dn473016.aspx)」を参照してください。

- **Microsoft Intune Certificate Connector** – Intune で SCEP 証明書プロファイルを使用するには、Microsoft Intune Certificate Connector が必要です。 この記事では、[このコネクタをインストールする](#install-the-intune-certificate-connector)手順について説明します。

  コネクタでは、Federal Information Processing Standards (FIPS) モードがサポートされています。 FIPS は必須ではありませんが、有効になっている場合は、証明書の発行および失効を行うことができます。
  - コネクタは、NDES サーバー ロールと同じサーバー (Windows Server 2012 R2 以降が実行されているサーバー) 上で実行する必要があります。
  - コネクタで必要な .NET 4.5 Framework は、Windows Server 2012 R2 に自動的に含まれます。
  - Internet Explorer セキュリティ強化の構成は、[NDES と Microsoft Intune Certificate Connector をホストするサーバーで無効にする必要があります](https://technet.microsoft.com/library/cc775800(v=WS.10).aspx)。

次のオンプレミス インフラストラクチャは省略可能です。

インターネット上のデバイスで証明書を取得できるようにするには、企業ネットワークの外部に NDES URL を発行する必要があります。 Azure AD アプリケーション プロキシ、Web アプリケーション プロキシ サーバー、別のリバース プロキシのいずれかを使用できます。

- **Azure AD アプリケーション プロキシ** (省略可能) – 専用 Web アプリケーション プロキシ (WAP) サーバーの代わりに Azure AD アプリケーション プロキシを使用して、NDES URL をインターネットに公開することができます。 これにより、イントラネットとインターネットに接続するどちらのデバイスでも証明書を取得できるようになります。 詳細については、「[オンプレミス アプリケーションへの安全なリモート アクセスを実現する方法](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy)」を参照してください。

- **Web アプリケーション プロキシ サーバー** (省略可能) - NDES URL をインターネットに公開するには、Windows Server 2012 R2 以降を実行しているサーバーを Web アプリケーション プロキシ (WAP) サーバーとして使用します。  これにより、イントラネットとインターネットに接続するどちらのデバイスでも証明書を取得できるようになります。

  WAP をホストするサーバーは、ネットワーク デバイス登録サービスで使用される長い URL のサポートを有効にする [更新プログラムをインストールする](https://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx) 必要があります。 この更新プログラムは、 [2014 年 12 月の更新プログラムのロールアップ](https://support.microsoft.com/kb/3013769)に含まれます。または、 [KB3011135](https://support.microsoft.com/kb/3011135)から個別に入手できます。

  WAP サーバーは、外部クライアントに公開されている名前と一致する SSL 証明書を持ち、NDES サービスをホストするコンピューターで使用されている SSL 証明書を信頼する必要があります。 これらの証明書を使用すると、WAP サーバーがクライアントからの SSL 接続を終了して、NDES サービスへの新しい SSL 接続を作成できるようになります。

  詳しくは、[Plan certificates for WAP](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383650(v=ws.11)#plan-certificates) (WAP の証明書の計画) に関するページおよび [general information about WAP servers](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn584113(v=ws.11)) (WAP サーバーについての一般情報) に関するページをご覧ください。

### <a name="accounts"></a>[アカウント]

- **NDES サービス アカウント** - NDES を設定する前に、NDES サービス アカウントとして使用するドメイン ユーザー アカウントを指定します。 このアカウントは、NDES を構成する前に、発行元 CA でテンプレートを構成するときに指定します。

  このアカウントは、NDES をホストするサーバーに対して次の権限を持っている必要があります。

  - **ローカルでのログオン**
  - **サービスとしてログオン**
  - **バッチ ジョブとしてログオン**

  詳細については、[NDES サービス アカウントとして動作するドメイン ユーザー アカウントの作成](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831498(v=ws.11)#to-create-a-domain-user-account-to-act-as-the-ndes-service-account)に関するセクションを参照してください。

- **NDES サービスをホストするコンピューターへのアクセス** - NDES をインストールするサーバーに Windows サーバー ロールをインストールして構成するアクセス許可を持つドメイン ユーザー アカウントが必要です。

- **証明機関へのアクセス** - 証明機関を管理する権限を持つドメイン ユーザー アカウントが必要です。

### <a name="network-requirements"></a>ネットワークの要件

NDES サービスは、[Azure AD アプリケーション プロキシ、Web アクセス プロキシ](https://azure.microsoft.com/documentation/articles/active-directory-application-proxy-publish/)、サード パーティ製のプロキシなどのリバース プロキシを通じて公開することをお勧めします。 リバース プロキシを使用しない場合は、インターネット上のすべてのホストおよび IP アドレスからポート 443 上の NDES サーバーへの TCP トラフィックを許可します。

NDES サービスと、環境内でサポートされている任意のインフラストラクチャとの間の通信に必要なすべてのポートとプロトコルを許可します。 たとえば、NDES サービスをホストするコンピューターは、CA、DNS サーバー、ドメイン コントローラー、Configuration Manager などの、環境内のその他のサービスやサーバーと通信する必要があります。

### <a name="certificates-and-templates"></a>証明書とテンプレート

SCEP を使用する場合は、次の証明書とテンプレートが使用されます。

|オブジェクト    |詳細    |
|----------|-----------|
|**SCEP 証明書テンプレート**         |デバイスの SCEP 要求を満たすために使用される発行元 CA で構成するテンプレート。 |
|**クライアント認証証明書** |発行元 CA またはパブリック CA から要求されます。<br /> この証明書は、NDES サービスをホストするコンピューターにインストールします。これは Intune Certificate Connector によって使用されます。<br /> この証明書を発行するために使用する CA テンプレートで、証明書に*クライアント*と*サーバーの認証*キーの使用法 (**拡張キー使用法**) が設定されている場合は、 サーバーとクライアントの認証に同じ証明書を使用できます。 |
|**サーバー認証証明書** |発行元 CA またはパブリック CA から要求される Web サーバー証明書。<br /> この SSL 証明書は、NDES をホストするコンピューターの IIS にインストールしてバインドします。<br />この証明書を発行するために使用する CA テンプレートで、証明書に*クライアント*と*サーバーの認証*キーの使用法 (**拡張キー使用法**) が設定されている場合は、 サーバーとクライアントの認証に同じ証明書を使用できます。 |
|**信頼されたルート CA 証明書**       |SCEP 証明書プロファイルを使用するには、デバイスで信頼されたルート証明機関 (CA) を信頼する必要があります。 Intune で*信頼済み証明書プロファイル*を使用して、信頼されたルート CA 証明書をユーザーとデバイスにプロビジョニングします。 <br/><br/> **-** オペレーティング システムのプラットフォームごとに 1 つの信頼されたルート CA 証明書を使用し、作成する各信頼済み証明書プロファイルにその証明書を関連付けます。 <br /><br /> **-** 必要に応じて、信頼されたルート CA 証明書を追加して使用できます。 たとえば、追加の証明書を使用して、Wi-Fi アクセス ポイント用のサーバー認証証明書に署名する CA の信頼性を担保することができます。 CA を発行するための追加の信頼されたルート CA 証明書を作成します。  Intune で作成する SCEP 証明書プロファイルでは、発行元 CA の信頼されたルート CA プロファイルを必ず指定します。<br/><br/> 信頼済み証明書プロファイルの詳細については、*Intune での認証に証明書を使用*に関するページの「[信頼されたルート CA 証明書をエクスポートする](certificates-configure.md#export-the-trusted-root-ca-certificate)」と「[信頼済み証明書プロファイルを作成する](certificates-configure.md#create-trusted-certificate-profiles)」を参照してください。 |

## <a name="configure-the-certification-authority"></a>証明機関を構成する

以降のセクションでは、次のことを行います。

- NDES に必要なテンプレートを構成して発行する。
- 証明書の失効に必要なアクセス許可を設定する。

以降のセクションでは、Windows Server 2012 R2 以降と Active Directory 証明書サービス (AD CS) についての知識が必要となります。

### <a name="access-your-issuing-ca"></a>発行元 CA にアクセスする

1. CA を管理するのに十分な権限を持つドメイン アカウントを使用して、発行元 CA にサインインします。

2. 証明機関の Microsoft 管理コンソール (MMC) を開きます。 'certsrv.msc' を**実行**するか、**サーバー マネージャー**で **[ツール]** をクリックし、 **[証明機関]** をクリックします。

3. **[証明書テンプレート]** ノードを選択し、 **[アクション]**  >  **[管理]** をクリックします。

### <a name="create-the-scep-certificate-template"></a>SCEP 証明書テンプレートを作成する

1. SCEP 証明書テンプレートとして使用する v2 証明書テンプレート (Windows 2003 の互換性あり) を作成します。 次の操作を行います。

   - *証明書テンプレート* スナップインを使用して、新しいカスタム テンプレートを作成します。
   - 既存のテンプレート (ユーザー テンプレートなど) をコピーしてから、NDES テンプレートとして使用するためにコピーを更新します。

2. テンプレートの指定されたタブで、次の設定を構成します。

   - **全般**:

     - **[Active Directory で証明書を発行する]** をオフにします。
     - 後でこのテンプレートを識別できるように、わかりやすい**テンプレート表示名**を指定します。

   - **サブジェクト名**:

     - **[要求に含まれる]** を選択します。 セキュリティは、NDES の Intune ポリシー モジュールによって適用されます。

       ![テンプレート、[サブジェクト名] タブ](./media/certificates-scep-configure/scep-ndes-subject-name.jpg)

   - **[拡張機能]** :

     - **[アプリケーション ポリシーの説明]** に **[クライアント認証]** が含まれていることを確認します。

       > [!IMPORTANT]
       > 必要なアプリケーション ポリシーのみを追加します。 セキュリティ管理者の選択を確定します。

     - iOS および macOS の証明書テンプレートの場合、 **[キー使用法]** も編集し、 **[署名は発行元の証明である]** がオンになっていないことを確認します。

     ![テンプレート、[拡張] タブ](./media/certificates-scep-configure/scep-ndes-extensions.jpg)  

   - **[セキュリティ]** :

     - **NDES サービス アカウント**を追加します。 このアカウントには、このテンプレートに対する**読み取り**と**登録**のアクセス許可が必要です。

     - SCEP プロファイルを作成する Intune 管理者のアカウントを追加します。 これらのアカウントには、SCEP プロファイルの作成中にこれらの管理者がこのテンプレートを参照できるようにするために、テンプレートに対する**読み取り**アクセス許可が必要です。

     ![テンプレート、[セキュリティ] タブ](./media/certificates-scep-configure/scep-ndes-security.jpg)

   - **要求処理**:

     次の図に例を示します。 ご使用の構成によって異なる場合があります。  

     ![テンプレート、[要求処理] タブ](./media/certificates-scep-configure/scep-ndes-request-handling.png)

   - **発行要件**:

     次の図に例を示します。 ご使用の構成によって異なる場合があります。

     ![テンプレート、[発行要件] タブ](./media/certificates-scep-configure/scep-ndes-issuance-reqs.jpg)

3. 証明書テンプレートを保存します。

### <a name="create-the-client-certificate-template"></a>クライアント証明書テンプレートを作成する

Intune certificate Connector には、*クライアント認証*の拡張キー使用法とサブジェクト名 (コネクタがインストールされているコンピューターの FQDN と同じ) を持つ証明書が必要です。 次のプロパティを持つテンプレートが必要です。

- **[拡張機能]**  >  **[アプリケーション ポリシー]** に **[クライアント認証]** を含める必要がある
- **[サブジェクト名]**  >  **[要求に含まれる]**

これらのプロパティを含むテンプレートが既にある場合は、それを再利用できます。それ以外の場合は、既存のテンプレートを複製するか、カスタム テンプレートを作成することで、新しいテンプレートを作成します。

### <a name="create-the-server-certificate-template"></a>サーバー証明書テンプレートを作成する

NDES サーバーでのマネージド デバイスと IIS 間の通信では HTTPS が使用され、これには証明書を使用する必要があります。 この証明書を発行するには、**Web サーバー**証明書テンプレートを使用できます。 または、専用のテンプレートを使用する場合は、次のプロパティが必要です。

- **[拡張機能]**  >  **[アプリケーション ポリシー]** に **[サーバー認証]** を含める必要がある
- **[サブジェクト名]**  >  **[要求に含まれる]**

> [!NOTE]
> クライアント証明書テンプレートとサーバー証明書テンプレートの両方の要件を満たす証明書がある場合は、1 つの証明書を IIS と Intune Certificate Connector の両方に使用できます。

### <a name="grant-permissions-for-certificate-revocation"></a>証明書失効のためのアクセス許可を付与する

不要になった証明書を Intune で失効できるようにするには、証明機関でアクセス許可を付与する必要があります。

Intune Certificate Connector では、NDES サーバーの**システム アカウント**または **NDES サービス アカウント**などの特定のアカウントを使用できます。

1. 証明機関コンソールで、CA 名を右クリックし、 **[プロパティ]** を選択します。

2. **[セキュリティ]** タブで **[追加]** をクリックします。

3. **証明書の発行と管理**のアクセス許可を付与します。

   - NDES サーバーの**システム アカウント**を使用することを選択した場合は、NDES サーバーにアクセス許可を付与します。
   - **NDES サービス アカウント**を使用することを選択した場合は、代わりにそのアカウントにアクセス許可を付与します。

### <a name="modify-the-validity-period-of-the-certificate-template"></a>証明書テンプレートの有効期間を変更する

証明書テンプレートの有効期間を変更することはオプションです。  

[SCEP 証明書テンプレートを作成](#create-the-scep-certificate-template)したら、テンプレートを編集して **[全般]** タブで**有効期間**を確認できます。

既定では、Intune はテンプレートで構成されている値を使用します。 ただし、要求元が異なる値を入力できるように CA を構成して、その値を Intune 管理者コンソール内から設定できるようにすることができます。

> [!IMPORTANT]
> iOS と macOS では、常にテンプレートで設定された値を使用します。

#### <a name="to-configure-a-value-that-can-be-set-from-within-the-intune-console"></a>Intune コンソール内から設定できる値を構成するには

1. CA で次のコマンドを実行します。

   -**certutil -setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE**
   -**net stop certsvc**
   -**net start certsvc**

2. 発行元 CA で、証明機関スナップインを使用して証明書テンプレートを発行します。 **[証明書テンプレート]** ノードを選択し、 **[アクション]**  >  **[新規]**  >  **[発行する証明書テンプレート]** の順に選択して、前のセクションで作成した証明書テンプレートを選択します。

3. **[証明書テンプレート]** フォルダー内にテンプレートが表示されていることで、テンプレートが発行されたことを確認します。

## <a name="set-up-ndes"></a>NDES を設定する

次の手順は、Intune で使用するネットワーク デバイス登録サービス (NDES) を構成するのに役立ちます。 NDES の詳細については、「[ネットワーク デバイス登録サービスのガイダンス](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831498(v%3dws.11))」を参照してください。

### <a name="install-the-ndes-service"></a>NDES サービスをインストールする

1. NDES サービスをホストするサーバーに**エンタープライズ管理者**としてサインインし、[役割と機能の追加ウィザード](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831809(v=ws.11))を使用して NDES をインストールします。

   1. ウィザードで、 **[Active Directory 証明書サービス]** を選択して AD CS 役割サービスにアクセスできるようにします。 **[ネットワーク デバイス登録サービス]** を選択し、 **[証明機関]** をオフにして、ウィザードを完了します。

      > [!TIP]
      > **[インストールの進行状況]** では、 **[閉じる]** を選択しないでください。 代わりに、 **[対象サーバーに Active Directory 証明書サービスを構成する]** リンクを選択します。 **AD CS の構成**ウィザードが開きます。これはこの記事の次の手順、「*NDES サービスを構成する*」で使用します。 [AD CS の構成] が開いた後は、役割と機能の追加ウィザードを閉じてかまいません。

   2. NDES がサーバーに追加されるときに、ウィザードは IIS もインストールします。 IIS が次の構成になっていることを確認します。

      - **[Web サーバー]**  >  **[セキュリティ]**  >  **[要求のフィルタリング]**
      - **[Web サーバー]**  >  **[アプリケーション開発]**  >  **[ASP.NET 3.5]**

        ASP.NET 3.5 をインストールすると、.NET Framework 3.5 がインストールされます。 .NET Framework 3.5 をインストールするとき、 **[.NET Framework 3.5]** のコア機能および **[HTTP アクティブ化]** の両方をインストールします。

      - **[Web サーバー]**  >  **[アプリケーション開発]**  >  **[ASP.NET 4.5]**

        ASP.NET 4.5 をインストールすると、.NET Framework 4.5 がインストールされます。 .NET Framework 4.5 をインストールするときに、 **[.NET Framework 4.5]** のコア機能、 **[ASP.NET 4.5]** 、および **[WCF サービス]**  >  **[HTTP アクティブ化]** 機能をインストールします。

      - **[管理ツール]**  >  **[IIS 6 と互換性のある管理]**  >  **[IIS 6 メタベース互換]**
      - **[管理ツール]**  >  **[IIS 6 と互換性のある管理]**  >  **[IIS 6 WMI 互換性]**
      - サーバーで、ローカルの **IIS_IUSR** グループのメンバーとして NDES サービス アカウントを追加します。

2. NDES サービスをホストするコンピューターで、管理者特権でのコマンド プロンプトから次のコマンドを実行します。 次のコマンドにより、NDES サービス アカウントの SPN が設定されます。

   `setspn -s http/<DNS name of the computer that hosts the NDES service> <Domain name>\<NDES Service account name>`

   たとえば、NDES サービスをホストするコンピューターの名前が **Server01**、ドメインが **Contoso.com**、サービス アカウントが **NDESService** の場合は、次を使用します。

   `setspn –s http/Server01.contoso.com contoso\NDESService`  

### <a name="configure-the-ndes-service"></a>NDES サービスを構成する

1. NDES サービスをホストするコンピューターで、**AD CS の構成**ウィザードを開き、次の更新を行います。

   > [!TIP]
   > 最後の手順から続けていて、 **[対象サーバーに Active Directory 証明書サービスを構成する]** リンクをクリックした場合、このウィザードは既に開かれているはずです。 それ以外の場合、サーバー マネージャーを開いて Active Directory 証明書サービスの展開後構成にアクセスします。

   - **[役割サービス]** で、 **[ネットワーク デバイス登録サービス]** を選択します。
   - **[NDES のサービス アカウント]** で、NDES サービス アカウントを指定します。
   - **[NDES 用の CA]** で、 **[選択]** をクリックして、証明書テンプレートを構成した発行元 CA を選択します。
   - **[NDES の暗号化]** で、会社の要件を満たすキーの長さを設定します。
   - **[確認]** で、 **[構成]** を選択してウィザードを完了します。

2. ウィザードが完了したら、NDES サービスをホストするコンピューターで、次のレジストリ キーを更新します。

   `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP\`

   このキーを更新するには、証明書テンプレートの**目的**を明らかにします ( **[要求の処理]** タブでわかります)。 次に、既存のデータを、[証明書テンプレートの作成時](#create-the-scep-certificate-template)に指定した証明書テンプレートの (表示名ではなく) 名前に置き換えることで、対応するレジストリ エントリを更新します。

   次の表では、証明書テンプレートの目的とレジストリの値の対応を示します。

   |証明書テンプレートの目的 ([要求の処理] タブ)|編集するレジストリ値|SCEP プロファイルについて Intune 管理コンソールに表示される値|
   |------------------------|-------------------------|---|
   |署名               |SignatureTemplate        |デジタル署名 |
   |暗号化              |EncryptionTemplate       |キーの暗号化  |
   |署名と暗号化|GeneralPurposeTemplate   |キーの暗号化 <br/> デジタル署名 |

   たとえば、証明書テンプレートの目的が **[暗号化]** の場合、 **EncryptionTemplate** の値を証明書テンプレートの名前に編集します。

3. IIS の要求フィルター処理を構成して、NDES サービスが受信する長い URL (クエリ) 用に IIS にサポートを追加します。

   1. IIS マネージャーで、 **[既定の Web サイト]**  >  **[要求のフィルタリング]**  >  **[機能設定の編集]** の順に選択して、 **[要求フィルター設定の編集]** ページを開きます。

   2. 次の設定を構成します。

      - **URL の最大長 (バイト)** = 65534
      - **クエリ文字列の最大長 (バイト)** = 65534

   3. **[OK]** を選択してこの構成を保存し、IIS マネージャーを閉じます。

   4. 次のレジストリ キーを表示して、指定された値があることを確認して、この構成を検証します。

      `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\HTTP\Parameters`

      次の値がダブルワード エントリとして設定されていることを確認します。

      - 名前:**MaxFieldLength**、十進数 **65534**
      - 名前:**MaxRequestBytes**、十進数 **65534**

4. NDES サービスをホストするサーバーを再起動します。 **iisreset** は使用しないでください。iireset では必要な変更が完了しません。

5. *http://* Server_FQDN */certsrv/mscep/mscep.dll* に移動します。 次の画像のような NDES ページが表示されます。

   ![NDES のテスト](./media/certificates-scep-configure/scep-ndes-url.png)

   Web アドレスで "**503 サービスを利用できません**" が返される場合は、コンピューターのイベント ビューアーを確認します。 このエラーは一般的に、[NDES サービス アカウントに対するアクセス許可](#accounts)がないためにアプリケーション プールが停止した場合に発生します。
  
### <a name="install-and-bind-certificates-on-the-server-that-hosts-ndes"></a>NDES をホストするサーバーに証明書をインストールしてバインドする

> [!TIP]
> 次の手順では、証明書が "*サーバー認証*" と "*クライアント認証*" の両方の使用条件を満たすように構成されている場合には、1 つの証明書を両方の認証に使用できます。 それぞれの使用条件は、次の手順 1 と 3 で説明されています。

1. 内部 CA またはパブリック CA から**サーバー認証**証明書を要求してから、サーバーに証明書をインストールします。

   サーバーで 1 つのネットワーク アドレスに対して外部名と内部名が使用されている場合、サーバー認証証明書には次のものが必要です。

   - 外部パブリック サーバー名を含む **[サブジェクト名]** 。
   - 内部サーバー名を含む **[サブジェクトの別名]** 。

2. IIS でサーバー認証証明書をバインドします。

   1. サーバー認証証明書をインストールした後、**IIS マネージャー**を開き、 **[既定の Web サイト]** を選択します。 **[操作]** ウィンドウで、 **[バインド]** を選択します。

   1. **[追加]** をクリックし、 **[種類]** を **[https]** に設定して、ポートが **443** であることを確認します。
   
   1. **[SSL 証明書]** で、サーバー認証証明書を指定します。

3. NDES サーバーで、内部 CA またはパブリック CA に **クライアント認証** 証明書を要求してインストールします。

   クライアント認証証明書には次のプロパティが必要です。

   - **拡張キー使用法**: この値には、**クライアント認証** を含める必要があります。
   - **サブジェクト名**: この値は、証明書をインストールするサーバー (NDES サーバー) の DNS 名と同じにする必要があります。

4. NDES サービスをホストするサーバーで、Intune Certificate Connector をサポートする準備ができました。

## <a name="install-the-intune-certificate-connector"></a>Intune Certificate Connector をインストールする

Microsoft Intune Certificate Connector は、NDES サービスが実行されているサーバーにインストールされます。 発行元の証明機関 (CA) と同じサーバーで NDES または Intune Certificate Connector を使用することはサポートされていません。

### <a name="to-install-the-certificate-connector"></a>Certificate Connector をインストールするには

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。

2. **[テナント管理]** 、 **[コネクタとトークン]** 、 **[証明書のコネクタ]** 、 **[追加]** の順に選択します。

3. SCEP ファイル用のコネクタをダウンロードして保存します。 コネクタをインストールするサーバーからアクセスできる場所に保存します。

   ![ConnectorDownload](./media/certificates-scep-configure/download-certificates-connector.png)

4. ダウンロードが完了した後、ネットワーク デバイス登録サービス (NDES) の役割をホストしているサーバーに移動します。 次のことを行います。

   1. .NET Framework 4.5 がインストールされていることを確認します。これは Intune Certificate Connector で必要となります。 .NET Framework 4.5 は、Windows Server 2012 R2 以降の新しいバージョンには自動的に含まれています。

   2. インストーラーを実行します (**NDESConnectorSetup.exe**)。 インストーラーによって、NDES のポリシー モジュールと IIS 証明書登録ポイント (CRP) Web サービスもインストールされます。 CRP Web サービス *CertificateRegistrationSvc* は、IIS でアプリケーションとして実行されます。

      スタンドアロン Intune の NDES をインストールする場合、CRP サービスは証明書コネクタと共に自動的にインストールされます。

5. Certificate Connector のクライアント証明書の入力を求められたら、 **[選択]** を選び、この記事で前述した「[NDES をホストするサーバーに証明書をインストールしてバインドする](#install-and-bind-certificates-on-the-server-that-hosts-ndes)」の手順 3 で NDES サーバーにインストールした**クライアント認証**証明書を選択します。

   クライアント認証証明書を選択すると、 **[Microsoft Intune Certificate Connector のクライアント証明書]** 画面に戻ります。 選択した証明書は表示されませんが、 **[次へ]** を選択してその証明書のプロパティを表示します。 **[次へ]** を選択して、 **[インストール]** を選択します。

6. ウィザードが完了した後、ウィザードを閉じる前に、**証明書コネクタの UI を起動**します。

   証明書コネクタの UI を起動する前にウィザードを閉じた場合は、次のコマンドを実行して再び開くことができます。

   *<install_Path>\NDESConnectorUI\NDESConnectorUI.exe*

7. **証明書コネクタ** UI で:

   1. **[サインイン]** を選択し、Intune サービス管理者の資格情報、またはグローバル管理アクセス許可を持つテナント管理者の資格情報を入力します。

   2. 使用するアカウントには、有効な Intune ライセンスが割り当てられている必要があります。

   3. サインインすると、Intune Certificate Connector によって Intune から証明書がダウンロードされます。 この証明書は、コネクタと Intune 間の認証に使用されます。 使用したアカウントに Intune ライセンスがない場合、コネクタ (NDESConnectorUI.exe) は、Intune から証明書を取得できません。  

      組織でプロキシ サーバーを使用していて、NDES サーバーがインターネットにアクセスするためにプロキシが必要な場合は、 **[プロキシ サーバーを使用する]** を選択します。 次に、接続するためのプロキシ サーバーの名前、ポート、およびアカウント資格情報を入力します。

   4. **[詳細設定]** タブを選択し、発行元 CA で**証明書の発行と管理**アクセス許可を持つアカウントの資格情報を入力します。 変更を**適用**します。  

    5. これで、証明書コネクタ UI を閉じることができます。

8. コマンド プロンプトを開き、「**services.msc**」と入力して、**Enter** キーを押します。 **[Intune コネクタ サービス]**  >  **[再起動]** の順に右クリックします。

サービスが実行していることを確認するには、ブラウザーを開き、次の URL を入力します。 **403** エラー: `https://<FQDN_of_your_NDES_server>/certsrv/mscep/mscep.dll` が返されます。

> [!NOTE]
> Intune Certificate Connector では、TLS 1.2 がサポートされています。 このコネクタをホストするサーバーが TLS 1.2 をサポートしている場合は、TLS 1.2 が使用されます。 サーバーが TLS 1.2 をサポートしない場合、TLS 1.1 が使用されます。 現在、デバイスとサーバー間の認証には、TLS 1.1 が使用されています。

## <a name="next-steps"></a>次のステップ

[SCEP 証明書プロファイルを作成する](certificates-profile-scep.md)  
[Intune Certificate Connector の問題のトラブルシューティング](troubleshoot-certificate-connector-events.md)
