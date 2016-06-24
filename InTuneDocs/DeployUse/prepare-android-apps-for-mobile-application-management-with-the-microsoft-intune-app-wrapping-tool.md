---
# required metadata

title: アプリ ラッピング ツールで管理するために Android アプリを準備する | Microsoft Intune | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: e9c349c8-51ae-4d73-b74a-6173728a520b

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Intune アプリ ラッピング ツールでモバイル アプリケーションを管理するために Android アプリを準備する
**Android 用 Microsoft Intune アプリ ラッピング ツール**を使用して社内 Android アプリの動作を変更すると、アプリ自体のコードを変更しなくてもアプリの機能を構成できます。

このツールは、PowerShell で実行される Windows のコマンドライン アプリケーションであり、アプリの "ラッパー" を作成します。 アプリが処理されたら、ユーザーが構成する[モバイル アプリケーション管理ポリシー](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md)を利用してアプリの機能を変更できます。

アプリで Azure Active Directory Authentication Library (ADAL) を使用している場合は、アプリをラップする前に「[Azure Active Directory Library を使用するアプリをラップする方法](#how-to-wrap-apps-that-use-the-azure-active-directory-library)」の手順を完了する必要があります。 自分のアプリでこのライブラリが使用されているかどうかがわからない場合、アプリの開発者にお問い合わせください。

このツールを実行する前に、「[アプリ ラッピング ツールを実行するうえでのセキュリティ上の考慮事項](#security-considerations-for-running-the-app-wrapping-tool)」を確認してください。 このツールをダウンロードするには、「[Android 用 Microsoft Intune アプリ ラッピング ツール](https://www.microsoft.com/download/details.aspx?id=47267)」を参照してください。.

## 手順 1: アプリ ラッピング ツールを使用するための前提条件を満たす

-   Windows 7 以降を実行している Windows コンピューターでアプリ ラッピング ツールを実行する必要があります。

-   入力アプリは、拡張子が **.apk** のファイルを備えた有効な Android アプリケーション パッケージであると同時に、次の要件を満たしている必要があります。

    -   暗号化できない

    -   アプリ ラッピング ツールでまだラップされていない

    -   Android 4.0 以降を対象に記述されている

-   このアプリは、自社で開発されているか、自社向けに開発されている必要があります。 このツールを使用して、Google Play ストアからダウンロードしたアプリを処理することはできません。

-   アプリ ラッピング ツールを実行するには、最新バージョンの [Java ランタイム環境](http://java.com/download/)をインストールし、Java の path 変数がWindows 環境変数で **C:\ProgramData\Oracle\Java\javapath** に設定されている必要があります。 詳細については、[Java のドキュメント](http://java.com/download/help/)を参照してください。.

    > [!NOTE]
    > 場合によっては、32 ビット バージョンの Java を使用すると、メモリに関連した問題が発生する可能性があります。 代わりに、64 ビット バージョンをインストールすることをお勧めします。

## 手順2: アプリ ラッピング ツールをインストールする

1.  Microsoft ダウンロード センターからアプリ ラッピング ツールのインストール ファイルを Windows コンピューターにダウンロードして開きます。

2.  ライセンス条項に同意し、インストールを完了します。

このツールをインストールしたフォルダーをメモしておきます。 既定の場所は、**C:\Program Files (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool** です。.

## 手順 3: アプリ ラッピング ツールを実行する

1.  アプリ ラッピング ツールをインストールした Windows コンピューターで PowerShell ウィンドウを開きます。

2.  ツールをインストールしたフォルダーから、アプリ ラッピング ツールの PowerShell モジュールをインポートします。

    ```
    Import-Module .\IntuneAppWrappingTool.psm1
    ```

3.  **invoke-AppWrappingTool** コマンドを次のパラメーターと共に使用してツールを実行します。 "省略可能" と示されているパラメーターは、Azure Active Directory Library (ADAL) を使用するアプリ用のパラメーターです。 詳細については、「[Azure Active Directory Library を使用するアプリをラップする方法](#how-to-wrap-apps-that-use-the-azure-active-directory-library)」を参照してください。.

|パラメーター|詳細情報|例|
|-------------|--------------------|---------|
|**-InputPath**&lt;String&gt;|ソースの Android アプリ (.apk) のパス。| |
|**-OutputPath**&lt;String&gt;|"出力先" の Android のアプリへのパス。 InputPath と同じディレクトリ パスを指定した場合、パッケージ化は失敗します。| |
|**-KeyStorePath**&lt;String&gt;|署名用の公開/秘密キーのペアを含むキーストア ファイルへのパス。| |
|**-KeyStorePassword**&lt;SecureString&gt;|キーストアの暗号化を解除するために使用するパスワード。| |
|**-KeyAlias**&lt;String&gt;|署名に使用するキーの名前。| |
|**-KeyPassword**&lt;SecureString&gt;|署名に使用する秘密キーの暗号化を解除するために使用するパスワード。| |
|**-SigAlg**&lt;SecureString&gt;|署名に使用する署名アルゴリズムの名前。 アルゴリズムは秘密キーと互換性を持つ必要があります。|例: SHA256withRSA、SHA1withRSA、MD5withRSA|
|**-ClientID**&lt;GUID&gt;|入力アプリの Azure Active Directory クライアント ID (省略可能)。| |
|**-AuthorityURI**&lt;Uri&gt;|入力アプリの Azure Active Directory 証明機関 URI (省略可能)。| |
|**-SkipBroker**&lt;Boolean&gt;|入力アプリケーションがデバイス全体にわたる仲介型シングル サインオンをサポートするかどうかを示します (省略可能)。 |**True** - 入力アプリケーションはデバイス全体にわたる仲介型シングル サインオンをサポートしません。 NonBrokerRedirectURI パラメーターを使用します。 **False** - 入力アプリケーションはデバイス全体にわたる仲介型シングル サインオンをサポートします。|
|**-NonBrokerRedirectURI**&lt;URI&gt;|SkipBroker が true の場合に使用する Azure Active Directory リダイレクト URI (省略可能)。|  |


**&lt;CommonParameters&gt;**
    (省略可能 – verbose、debug などの一般的な PowerShell パラメーターをサポートします)。

- 共通パラメーターの一覧については、「[Microsoft スクリプト センター](https://technet.microsoft.com/library/hh847884.aspx)」を参照してください。.

- ツールのヘルプを表示するには、次のコマンドを入力します。

    ```
    Help Invoke-AppWrappingTool
    ```
- Azure Active Directory (AAD) の統合の詳細については、「[Azure Active Directory Library を使用するアプリをラップする方法](#how-to-wrap-apps-that-use-the-azure-active-directory-library)」を参照してください。.

**例:**


    Import-Module "C:\Program Files (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool\IntuneAppWrappingTool.psm1"
    Invoke-AppWrappingTool –InputPath <input-app.apk> -OutputPath <output-app.apk> -KeyStorePath <path-to-signing.keystore> -KeyAlias <signing-key-name> -ClientID <xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx> -AuthorityURI <http://AzureActiveDirectory.Authority.URL> -SkipBroker<$True|$False> -NonBrokerRedirectURI <urn:xxx:xx:xxxx:xx:xxx>

**KeyStorePassword** と **KeyPassword** の入力を求められます。.

ラップされたアプリは、指定した出力パスにログ ファイルと共に生成されて保存されます。

## アプリ ラッピング ツールを実行するうえでのセキュリティ上の考慮事項
スプーフィング、情報漏えい、および権限の昇格攻撃の可能性を抑制するには、次の手順に従います。

-   入力基幹業務アプリケーション、出力アプリケーション、Java KeyStore がアプリ ラッピング ツールを実行しているのと同じコンピューターに存在することを確認します。

-   このツールを実行しているのと同じコンピューター上の Intune コンソールに出力アプリケーションをインポートします。

-   出力アプリケーションとツールが汎用名前付け規則 (UNC) パスにあり、ツールと入力ファイルを同じコンピューター上で実行していない場合、[インターネット プロトコル セキュリティ (IPsec)](http://en.wikipedia.org/wiki/IPsec) または [サーバー メッセージ ブロック (SMB) 署名](https://support.microsoft.com/en-us/kb/887429)を使用して環境をセキュリティで保護します。.

-   Azure Active Directory (AAD) を使用していて、実行時にアプリケーションから AAD トークンにアクセスできる可能性がある場合は特に、そのアプリケーションが信頼されたソースから入手されていることを確認します。

-   ラップされたアプリが格納されている出力ディレクトリをセキュリティで保護します。 出力にユーザー レベルのディレクトリを使用することを検討します。

## Azure Active Directory Library を使用するアプリをラップする方法
アプリで Azure Active Directory Authentication Library (ADAL) を使用している場合は、アプリをラップする前にこれらの手順を完了する必要があります。

### 手順 1: ADAL の要件を満たしていることを確認する
ADAL を使用するアプリの場合、次を満たす必要があります。

-   アプリは 1.0.2 以上のバージョンの ADAL を組み込む必要があります。

-   開発者は、「[手順 3: AAD でモバイル アプリ管理へのアクセスを構成する](#step-3-configure-access-to-mobile-app-management-in-aad)」の説明に従って、Intune モバイル アプリケーション管理リソースに対するアクセス権をアプリに付与する必要があります。.

### 手順 2: アプリを登録するときに取得する必要のある識別子を確認する
次の手順では、Azure 管理ポータルを使用して、次の表に示されている一意の識別子を取得するために、(Azure Active Directory (AAD) と共に ADAL を使用している) アプリを登録します。 ADAL をアプリと統合するときに、これらの識別子を開発者に渡します。

|識別子|説明|既定値|
|--------------|--------------------|-----------------|
|**クライアント ID**|AAD での登録後にアプリに対して生成される一意の GUID 識別子。<br /><br />アプリのクライアント ID がわかっている場合は、その値を指定します。 わからない場合は、既定値を使用します。|6c7e8096-f593-4d72-807f-a5f86dcc9c77|
|**証明機関 URI**|AAD のオブジェクト (ユーザーやグループなど) に対する証明機関の URI (Uniform Resource Identifier)。<br /><br />AuthorityURI パラメーターは、アプリ ラッピング ツールに対しては省略可能です。 このパラメーターを使用しない場合は、既定の URI が使用されます。||
|**SkipBroker**|会社ポータルをブローカーとして使用するかどうかを示す値。<br /><br />**True** – ADAL の認証に会社ポータルを使用しません。<br /><br />**False** – ADAL の認証に会社ポータルを使用します。 ポータル サイトでは、登録済みのユーザーをシングル サインオンの目的で使用します。||
|**非ブローカーのリダイレクト URI**|ADAL でブローカー アプリ (Intune ポータル サイト) を使用しない場合に使用されるログイン URI。|urn:ietf:wg:oauth:2.0:oob|
|**リソース ID**|アプリの AAD リソースへのポインター。||

### 手順 3: AAD でモバイル アプリ管理へのアクセスを構成する
アプリ ラッピング ツールでアプリの AAD 登録値を使用する前に、アプリ開発者は次の手順に従って、そのアプリのアクセス権限を Intune Mobile Application Management リソースに与える必要があります。

1.  Azure 管理ポータルで既存の AAD アカウントにログインします。

2.  **[既存の LOB アプリケーションの登録]** を選択します。.

3.  **構成**セクションで、**[他のアプリケーションの Web API へのアクセスの構成]** を選択します。.

4.  **[他のアプリケーションへのアクセス許可]** セクションの最初のドロップダウン リストから **[Intune モバイル アプリケーション管理]** を選択します。.

これで、アプリ ラッピング ツールでアプリのクライアント ID を使用できるようになります。 「[手順 2: アプリを登録するときに取得する必要のある識別子を確認する](#step-2-review-the-identifiers-you-need-to-get-when-you-register-the-app)」の表で説明したように、クライアント ID は Azure Active Directory の管理ポータルに表示されます。.

### 手順 4: アプリ ラッピング ツールで AAD 識別子の値を使用する
登録プロセスから取得した識別子の値を、アプリ ラッピング ツールでコマンド ライン プロパティとして入力します。 エンドユーザーが正しくアプリを認証できるように、表に示されるすべての値を指定する必要があります。 値を指定しない場合は、既定の値が使用されます。

|識別子|パラメーター|
|--------------|-------------|
|クライアント ID|ClientID|
|証明機関 URI|Authority-URI|
|SkipBroker|SkipBroker|
|非ブローカーのリダイレクト URI|NonBrokerRedirectURI|
|リソース ID|ResourceID|
アプリをラッピングするときには、次の点に注意してください。

-   アプリ ラッピング ツールでは、アプリ内の ADAL バイナリ (存在する場合) が検索されません。 アプリが古くなったバージョンのバイナリにリンクする場合、認証ポリシーが有効になっていると、ログイン中にランタイム エラーが発生することがあります。

-   認証が成功したことを確認するために、
  [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] MAM リソース ID に関連付けられている AAD トークンが取得されます。 ただし、このトークンは、さらにトークンの有効性を確認する呼び出しで使用されることはありません。 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] サインインしているユーザーのユーザー プリンシパル名 (UPN) のみを読み取って、アプリのアクセス許可を決定します。 AAD トークンはその他のサービスの呼び出しには使用されません。

-   認証トークンは、共有キーチェーンに保存されているため、同じ公開元からのアプリの間で共有されます。 特定のアプリを分離する場合は、そのアプリに別の署名証明書、プロビジョニング プロファイル キーストア、およびキー エイリアスを使用する必要があります。

-   クライアント アプリケーションのクライアント ID と証明機関 URI を提供する場合、ダブル ログイン プロンプトは回避されます。 AAD ダッシュ ボードで、公開された [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] MAM リソース ID にアクセスするには、クライアント ID を登録して有効にする必要があります。 クライアント ID を登録しないと、アプリの実行時にユーザーがログインに失敗します。


### 関連項目
- [Microsoft Intune によるモバイル アプリケーション管理のためにアプリを準備する方法を決める](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md)

- [Use the SDK to enable apps for mobile application management (アプリでモバイル アプリケーション管理を実行できるよう SDK を使用する)](use-the-sdk-to-enable-apps-for-mobile-application-management.md)


<!--HONumber=May16_HO1-->


