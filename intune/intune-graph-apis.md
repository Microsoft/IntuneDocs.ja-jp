---
title: "Azure AD を使用して Intune Graph API にアクセスする方法"
description: "アプリで Azure AD を使用して Intune Graph API にアクセスするために必要な手順について説明します"
keywords: "intune graphapi c# powershell アクセス許可の役割"
author: vhorne
manager: angrobe
ms.author: victorh
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 79A67342-C06D-4D20-A447-678A6CB8D70A
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 351a066c8852125b6fbf26c039dd3718b63f8980
ms.sourcegitcommit: 3b397b1dcb780e2f82a3d8fba693773f1a9fcde1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/12/2017
---
# <a name="how-to-use-azure-ad-to-access-the-intune-graph-api"></a>Azure AD を使用して Intune Graph API にアクセスする方法

[Microsoft Graph API](https://developer.microsoft.com/graph/) が Microsoft Intune に対応し、固有の API とアクセス許可の役割を利用できるようになりました。  Graph API は、認証とアクセスの制御に Azure Active Directory (Azure AD) を使用します。  
Intune Graph API へのアクセスには以下が必要です。

- アプリケーション ID と、

    - Azure AD および Graph API を呼び出すアクセス許可。
    - 特定のアプリケーション タスクに関連したアクセス許可スコープ。

- ユーザー資格情報と、

    - アプリケーションに関連付けられている Azure AD テナントへのアクセス許可。
    - アプリケーションのアクセス許可スコープをサポートするために必要な役割のアクセス許可。

- Azure テナントのアプリケーション タスク実行に必要なアクセス許可をアプリに付与するエンド ユーザー。

この記事の内容:

- Graph API と関連するアクセス許可の役割にアクセスできるアプリケーションを登録する方法について説明します。

- Intune Graph API のアクセス許可の役割について説明します。

- C# および PowerShell の Intune Graph API 認証例を提供します。

- 複数のテナントをサポートする方法について説明します。

詳細については、次を参照してください。

- [OAuth 2.0 と Azure Active Directory を使用した Web アプリケーションへのアクセスの承認](https://docs.microsoft.com/azure/active-directory/develop/active-directory-protocols-oauth-code)
- [Azure AD 認証の概要](https://www.visualstudio.com/docs/integrate/get-started/auth/oauth)
- [Azure Active Directory とアプリケーションの統合](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications)
- [OAuth 2.0 について知る](https://oauth.net/2/)

## <a name="register-apps-to-use-graph-api"></a>Graph API を使用するアプリを登録する

Graph API を使用するアプリを登録するには、次の作業を行います。

1.  管理者資格情報を使って、[Azure Portal](https://portal.azure.com) にサインインします。

    必要に応じて、次を使用することができます。
    - テナントの管理者アカウント。
    - **[ユーザーはアプリケーションを登録できる]** の設定が有効になっている、テナントのユーザー アカウント。

2.  メニューで、**[Azure Active Directory]** &gt; **[アプリの登録]** の順に選択します。

    <img src="./media/azure-ad-app-reg.png" width="157" height="170" alt="The App registrations menu command" />

3.  **[新しいアプリケーションの登録]** を選択して新しいアプリケーションを作成するか、または既存のアプリケーションを選択します。  (既存のアプリケーションを選択した場合は、次の手順をスキップします。)

4.  **[作成]** ブレードで、次を指定します。

    1.  アプリケーションの **[名前]**\(ユーザーがサインインするときに表示されます\)。

    2.  **[アプリケーションの種類]** と **[リダイレクト URI]** の値。

        これらは要件によって異なります。 たとえば Azure AD [Authentication Library](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) (ADAL) を使用している場合、**[アプリケーションの種類]** は `Native` に、**[リダイレクト URI]** は `urn:ietf:wg:oauth:2.0:oob` に設定します。

        <img src="media/azure-ad-app-new.png" width="209" height="140" alt="New app properties and values" />

        詳細については、「[Azure AD の認証シナリオ](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios)」をご覧ください。

5.  [アプリケーション] ブレードで、次の作業を行います。

    1.  **[アプリケーション ID]** の値をメモします。

    2.  **[設定]** &gt; **[API アクセス]** &gt; **[必要なアクセス許可]** の順に選択します。

    <img src="media/azure-ad-req-perm.png" width="483" height="186" alt="The Required permissions setting" />

6.  **[必要なアクセス許可]** ブレードで、**[追加]** &gt; **[API アクセスの追加]** &gt; **[API を選択します]** の順に選択します。

    <img src="media/azure-ad-add-graph.png" width="436" height="140" alt="The Microsoft Graph setting" />

7.  **[API を選択します]** ブレードで、**[Microsoft Graph]** &gt; **[選択]** の順に選択します。  **[アクセスの有効化]** ブレードが開き、アプリケーションで使用できるアクセス許可スコープが一覧表示されます。

    <img src="media/azure-ad-perm-scopes.png" width="489" height="248" alt="Intune Graph API permission scopes" />

    関連する名前の左側にチェックを入れ、アプリに必要な役割を選択します。  Intune に固有のアクセス許可スコープの詳細については、「[Intune permission scopes (Intune のアクセス許可スコープ)](#user-content-intune-permission-scopes)」をご覧ください。  Graph API の他のアクセス許可スコープの詳細については、「[Microsoft Graph のアクセス許可のリファレンス](https://developer.microsoft.com/graph/docs/concepts/permissions_reference)」をご覧ください。

    最善の結果を得るには、アプリケーションの実装に必要な最小限の役割を選択します。

    完了したら、**[選択]** と **[完了]** を選択して変更を保存します。

この時点で、次も実行できます。

- すべてのテナント アカウントに、資格情報を入力せずにアプリを使用するアクセス許可を付与することを選択します。  

    これを実行するには、**[アクセス許可の付与]** を選択し、確認プロンプトに同意します。

    初めてアプリケーションを実行すると、選択した役割を実行できるアクセス許可をアプリに付与するように求められます。

    <img src="media/azure-ad-grant-perm.png" width="351" height="162" alt="The Grant permissions button" />

- テナントの外部ユーザーがアプリを使用できるようにします。  (これは通常、複数のテナント/組織をサポートするパートナーにのみ必要です。)  

    これを実行するには、次のようにします。

    1. [アプリケーション] ブレードで **[マニフェスト]** を選択すると、**[マニフェストの編集]** ブレードが開きます。

    <img src="media/azure-ad-edit-mft.png" width="295" height="114" alt="The Edit manifest blade" />

    2. `availableToOtherTenants` 設定の値を `true` に変更します。

    3. 変更を保存します。

## <a name="intune-permission-scopes"></a>Intune のアクセス許可スコープ

Azure AD と Graph API では、アクセス許可スコープを使用して企業リソースへのアクセスを制御します。  

アクセス許可スコープ (_OAuth スコープ_とも呼ばれます) は、特定の Intune エンティティとそのプロパティへのアクセスを制御します。 このセクションでは、Intune Graph API の機能に対するアクセス許可スコープの概要について説明します。

詳細については、次をご覧ください。
- [Azure AD 認証](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-pass-through-authentication)
- [アプリケーションのアクセス許可スコープ](https://docs.microsoft.com/azure/active-directory/develop/active-directory-v2-scopes)

Graph API へのアクセス許可を付与する場合は、次のスコープを指定して Intune の機能へのアクセスを制御できます。次の表に、Intune Graph API のアクセス許可スコープをまとめています。  1 番目の列には Azure Portal に表示される機能名を示し、2 番目の列にはアクセス許可スコープ名を掲載しています。

_[アクセスを有効にする]_ 設定 | スコープ名
:--|:--
__Microsoft Intune デバイスでユーザーに影響を与えるリモート操作を実行する__ | [DeviceManagementManagedDevices.PrivilegedOperations.All](#user-content-mgd-po)
__Microsoft Intune デバイスの読み取りおよび書き込み__ | [DeviceManagementManagedDevices.ReadWrite.All](#mgd-rw)
__Microsoft Intune デバイスの読み取り__ | [DeviceManagementManagedDevices.Read.All](#mgd-ro)
__Microsoft Intune RBAC の設定の読み取りおよび書き込み__ | [DeviceManagementRBAC.ReadWrite.All](#rac-rw)
__Microsoft Intune RBAC の設定の読み取り__ | [DeviceManagementRBAC.Read.All](#rac=ro)
__Microsoft Intune アプリの読み取りおよび書き込み__ | [DeviceManagementApps.ReadWrite.All](#app-rw)
__Microsoft Intune アプリの読み取り__ | [DeviceManagementApps.Read.All](#app-ro)
__Microsoft Intune のデバイスの構成とポリシーの読み取りおよび書き込み__ | [DeviceManagementConfiguration.ReadWrite.All](#cfg-rw)
__Microsoft Intune のデバイスの構成とポリシーの読み取り__ | [DeviceManagementConfiguration.Read.All](#cfg-ro)
__Microsoft Intune の構成の読み取りおよび書き込み__ | [DeviceManagementServiceConfig.ReadWrite.All](#svc-rw)
__Microsoft Intune の構成の読み取り__ | [DeviceManagementServiceConfig.Read.All](#svc-ra)

表は、Azure Portal に表示される順序で設定を一覧表示しています。 次のセクションでは、スコープについてアルファベット順に説明します。

この時点では、Intune のすべてのアクセス許可スコープに管理者のアクセス権が必要です。  つまり、Intune Graph API のリソースにアクセスするアプリまたはスクリプトを実行する場合は、対応する資格情報が必要になります。

### <a name="app-ro"></a>DeviceManagementApps.Read.All

- **[アクセスを有効にする]** 設定: __Microsoft Intune アプリの読み取り__

- 次のエンティティのプロパティとステータスへの読み取りアクセスを許可します。
    - モバイル アプリ
    - モバイル アプリ カテゴリ
    - アプリ保護ポリシー
    - アプリの構成

### <a name="app-rw"></a>DeviceManagementApps.ReadWrite.All

- **[アクセスを有効にする]** 設定: __Microsoft Intune アプリの読み取りおよび書き込み__

- __DeviceManagementApps.Read.All__ と同じ操作を許可します。

- また、次のエンティティに対する変更を許可します。

    - モバイル アプリ
    - モバイル アプリ カテゴリ
    - アプリ保護ポリシー
    - アプリの構成

### <a name="cfg-ro"></a>DeviceManagementConfiguration.Read.All

- **[アクセスを有効にする]** 設定: __Microsoft Intune のデバイスの構成とポリシーの読み取り__

- 次のエンティティのプロパティとステータスへの読み取りアクセスを許可します。
    - デバイス構成
    - デバイス コンプライアンス ポリシー
    - 通知メッセージ

### <a name="cfg-ra"></a>DeviceManagementConfiguration.ReadWrite.All

- **[アクセスを有効にする]** 設定: __Microsoft Intune のデバイスの構成とポリシーの読み取りおよび書き込み__

- __DeviceManagementConfiguration.Read.All__ と同じ操作を許可します。

- また、アプリでは次のエンティティを作成、割り当て、削除、および変更できます。
    - デバイス構成
    - デバイス コンプライアンス ポリシー
    - 通知メッセージ

### <a name="mgd-po"></a>DeviceManagementManagedDevices.PrivilegedOperations.All

- **[アクセスを有効にする]** 設定: __Microsoft Intune デバイスでユーザーに影響を与えるリモート操作を実行する__

- 管理されたデバイスへの次のリモート操作を許可します。
    - インベントリから削除
    - ワイプ
    - パスコードのリセット/復旧
    - リモート ロック
    - 紛失モードの有効/無効
    - PC のクリーンアップ
    - 再起動
    - 共有デバイスからのユーザーの削除

### <a name="mgd-ro"></a>DeviceManagementManagedDevices.Read.All

- **[アクセスを有効にする]** 設定: __Microsoft Intune デバイスの読み取り__

- 次のエンティティのプロパティとステータスへの読み取りアクセスを許可します。
    - 管理されたデバイス
    - デバイスのカテゴリ
    - 検出されたアプリ
    - リモート操作
    - マルウェア情報

### <a name="mgd-rw"></a>DeviceManagementManagedDevices.ReadWrite.All

- **[アクセスを有効にする]** 設定: __Microsoft Intune デバイスの読み取りおよび書き込み__

- __DeviceManagementManagedDevices.Read.All__ と同じ操作を許可します。

- また、アプリでは次のエンティティを作成、削除、変更できます。
    - 管理されたデバイス
    - デバイスのカテゴリ

- 次のリモート操作も実行できます。
    - デバイスの検索
    - アクティベーション ロックのバイパス
    - リモート アシスタンスの要求

### <a name="rac-ro"></a>DeviceManagementRBAC.Read.All

- **[アクセスを有効にする]** 設定: __Microsoft Intune RBAC の設定の読み取り__

- 次のエンティティのプロパティとステータスへの読み取りアクセスを許可します。
    - ロールの割り当て
    - ロールの定義
    - リソースの操作

### <a name="rac-rw"></a>DeviceManagementRBAC.ReadWrite.All

- **[アクセスを有効にする]** 設定: __Microsoft Intune RBAC の設定の読み取りおよび書き込み__

- __DeviceManagementRBAC.Read.All__ と同じ操作を許可します。

- また、アプリでは次のエンティティを作成、割り当て、削除、および変更できます。
    - ロールの割り当て
    - ロールの定義

### <a name="svc-ro"></a>DeviceManagementServiceConfig.Read.All

- **[アクセスを有効にする]** 設定: __Microsoft Intune の構成の読み取り__

- 次のエンティティのプロパティとステータスへの読み取りアクセスを許可します。
    - デバイスの登録
    - Apple Push Notification 証明書
    - Apple Device Enrollment Program
    - Apple Volume Purchase Program
    - Exchange Connector
    - 使用条件
    - 通信経費管理
    - クラウド PKI
    - ブランド化
    - Mobile Threat Defense

### <a name="svc-rw"></a>DeviceManagementServiceConfig.ReadWrite.All

- **[アクセスを有効にする]** 設定: __Microsoft Intune の構成の読み取りおよび書き込み__

- DeviceManagementServiceConfig.Read.All と同じ操作を許可します。

- また、アプリでは Intune の次の機能を構成できます。
    - デバイスの登録
    - Apple Push Notification 証明書
    - Apple Device Enrollment Program
    - Apple Volume Purchase Program
    - Exchange Connector
    - 使用条件
    - 通信経費管理
    - クラウド PKI
    - ブランド化
    - Mobile Threat Defense

## <a name="azure-ad-authentication-examples"></a>Azure AD 認証の例

このセクションでは、Azure AD を C# プロジェクトや PowerShell プロジェクトに組み込む方法について説明します。

それぞれの例で、少なくとも前述のアクセス許可スコープ `DeviceManagementManagedDevices.Read.All` を持つアプリケーション ID を指定する必要があります。

いずれかの例をテストすると、次のような HTTP ステータス 403 (禁止されています) のエラーが表示されることがあります。

``` javascript
{
  "error": {
    "code": "Forbidden",
    "message": "Application is not authorized to perform this operation - Operation ID " +
       "(for customer support): 00000000-0000-0000-0000-000000000000 - " +
       "Activity ID: cc7fa3b3-bb25-420b-bfb2-1498e598ba43 - " +
       "Url: https://example.manage.microsoft.com/" +
       "Service/Resource/RESTendpoint?" +
       "api-version=2017-03-06 - CustomApiErrorPhrase: ",
    "innerError": {
      "request-id": "00000000-0000-0000-0000-000000000000",
      "date": "1980-01-0112:00:00"
    }
  }
}
```

この場合は、次の点を確認します。

- Graph API とアクセス許可スコープ `DeviceManagementManagedDevices.Read.All` の使用が承認されたアプリケーション ID に更新している。

- テナントの資格情報は、管理機能をサポートしている。

- 表示されているサンプルと同様のコードを使用している。


### <a name="authenticate-azure-ad-in-c"></a>Azure AD の認証 (C\#)

この例では、C# を使用して、Intune アカウントに関連付けられているデバイスの一覧を取得する方法を説明します。

1.  Visual Studio を起動して、新しい Visual C# コンソール アプリ (.NET Framework) プロジェクトを作成します。

2.  プロジェクトの名前を入力し、必要に応じて他の詳細情報を入力します。

    <img src="media/aad-auth-cpp-new-console.png" width="624" height="433" alt="Creating a C# console app project in Visual Studio"  />

3.  ソリューション エクスプローラーを使用して、プロジェクトに Microsoft ADAL NuGet パッケージを追加します。

    1.  ソリューション エクスプローラーを右クリックします。
    2.  **[NuGet パッケージの管理...]**  &gt; **[参照]** を選択します。
    3.  `Microsoft.IdentityModel.Clients.ActiveDirectory` を選択して、**[インストール]** を選択します。

    <img src="media/aad-auth-cpp-install-package.png" width="624" height="458" alt="Selecting the Azure AD identity model module" />

4.  **Program.cs** の先頭に、次のステートメントを追加します。

    ``` csharp
    using Microsoft.IdentityModel.Clients.ActiveDirectory;</p>
    using System.Net.Http;
    ```

5.  Authorization ヘッダーを作成するメソッドを追加します。

    ``` csharp
    private static async Task<string> GetAuthorizationHeader()
    {
        string applicationId = "<Your Application ID>";
        string authority = "https://login.microsoftonline.com/common/";
        Uri redirectUri = new Uri("urn:ietf:wg:oauth:2.0:oob");
        AuthenticationContext context = new AuthenticationContext(authority);
        AuthenticationResult result = await context.AcquireTokenAsync(
            "https://graph.microsoft.com",
            applicationId, redirectUri,
            new PlatformParameters(PromptBehavior.Auto));
        return result.CreateAuthorizationHeader();
    ```

    前述のとおり、`application_ID` の値を、少なくともアクセス許可スコープ `DeviceManagementManagedDevices.Read.All` が付与されたものと一致するように変更してください。

6. デバイスの一覧を取得するメソッドを追加します。

    ``` csharp
    private static async Task<string> GetMyManagedDevices()
    {
        string authHeader = await GetAuthorizationHeader();
        HttpClient graphClient = new HttpClient();
        graphClient.DefaultRequestHeaders.Add("Authorization", authHeader);
        return await graphClient.GetStringAsync(
            "https://graph.microsoft.com/beta/me/managedDevices");
    }
    ```

7.  **Main** を **GetMyManagedDevices** を呼び出すように更新します。

    ``` csharp
    string devices = GetMyManagedDevices().GetAwaiter().GetResult();
    Console.WriteLine(devices);
    ```

8.  プログラムをコンパイルし、実行します。  

初めてプログラムを実行すると、2 つのプロンプトが表示されます。  1 つ目は資格情報を要求し、2 つ目は `managedDevices` 要求に対するアクセス許可を付与します。  

参考までに、完成したプログラムを次に示します。

``` csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using System;
using System.Net.Http;
using System.Threading.Tasks;

namespace IntuneGraphExample
{
    class Program
    {
        static void Main(string[] args)
        {
            string devices = GetMyManagedDevices().GetAwaiter().GetResult();
            Console.WriteLine(devices);
        }

        private static async Task<string> GetAuthorizationHeader()
        {
            string applicationId = "<Your Application ID>";
            string authority = "https://login.microsoftonline.com/common/";
            Uri redirectUri = new Uri("urn:ietf:wg:oauth:2.0:oob");
            AuthenticationContext context = new AuthenticationContext(authority);
            AuthenticationResult result = await context.AcquireTokenAsync("https://graph.microsoft.com", applicationId, redirectUri, new PlatformParameters(PromptBehavior.Auto));
            return result.CreateAuthorizationHeader();
        }

        private static async Task<string> GetMyManagedDevices()
        {
            string authHeader = await GetAuthorizationHeader();
            HttpClient graphClient = new HttpClient();
            graphClient.DefaultRequestHeaders.Add("Authorization", authHeader);
            return await graphClient.GetStringAsync("https://graph.microsoft.com/beta/me/managedDevices");
        }
    }
}
```

### <a name="authenticate-azure-ad-powershell"></a>Azure AD の認証 (PowerShell)

次の PowerShell スクリプトでは、認証のために AzureAD PowerShell モジュールを使用します。  詳細については、「[Azure Active Directory PowerShell Version 2 (Azure Active Directory PowerShell バージョン 2)](https://docs.microsoft.co/powershell/azure/install-adv2?view=azureadps-2.0)」と「[Intune PowerShell examples (Intune PowerShell の例)](https://github.com/microsoftgraph/powershell-intune-samples)」をご覧ください。

この例では、`$clientID` の値を、有効なアプリケーション ID と一致するように更新します。

``` powershell
function Get-AuthToken {
    [cmdletbinding()]
    param
    (
        [Parameter(Mandatory = $true)]
        $User
    )

    $userUpn = New-Object "System.Net.Mail.MailAddress" -ArgumentList $User
    $tenant = $userUpn.Host

    Write-Host "Checking for AzureAD module..."

    $AadModule = Get-Module -Name "AzureAD" -ListAvailable
    if ($AadModule -eq $null) {
        Write-Host "AzureAD PowerShell module not found, looking for AzureADPreview"
        $AadModule = Get-Module -Name "AzureADPreview" -ListAvailable
    }

    if ($AadModule -eq $null) {
        write-host
        write-host "AzureAD Powershell module not installed..." -f Red
        write-host "Install by running 'Install-Module AzureAD' or 'Install-Module AzureADPreview' from an elevated PowerShell prompt" -f Yellow
        write-host "Script can't continue..." -f Red
        write-host
        exit
    }

    # Getting path to ActiveDirectory Assemblies
    # If the module count is greater than 1 find the latest version

    if ($AadModule.count -gt 1) {
        $Latest_Version = ($AadModule | select version | Sort-Object)[-1]
        $aadModule = $AadModule | ? { $_.version -eq $Latest_Version.version }
        $adal = Join-Path $AadModule.ModuleBase "Microsoft.IdentityModel.Clients.ActiveDirectory.dll"
        $adalforms = Join-Path $AadModule.ModuleBase "Microsoft.IdentityModel.Clients.ActiveDirectory.Platform.dll"
    }

    else {
        $adal = Join-Path $AadModule.ModuleBase "Microsoft.IdentityModel.Clients.ActiveDirectory.dll"
        $adalforms = Join-Path $AadModule.ModuleBase "Microsoft.IdentityModel.Clients.ActiveDirectory.Platform.dll"
    }

    [System.Reflection.Assembly]::LoadFrom($adal) | Out-Null
    [System.Reflection.Assembly]::LoadFrom($adalforms) | Out-Null

    $clientId = "<Your Application ID>"
    $redirectUri = "urn:ietf:wg:oauth:2.0:oob"
    $resourceAppIdURI = "https://graph.microsoft.com"
    $authority = "https://login.microsoftonline.com/$Tenant"

    try {
        $authContext = New-Object "Microsoft.IdentityModel.Clients.ActiveDirectory.AuthenticationContext" -ArgumentList $authority
        # https://msdn.microsoft.com/library/azure/microsoft.identitymodel.clients.activedirectory.promptbehavior.aspx
        # Change the prompt behaviour to force credentials each time: Auto, Always, Never, RefreshSession
        $platformParameters = New-Object "Microsoft.IdentityModel.Clients.ActiveDirectory.PlatformParameters" -ArgumentList "Auto"
        $userId = New-Object "Microsoft.IdentityModel.Clients.ActiveDirectory.UserIdentifier" -ArgumentList ($User, "OptionalDisplayableId")
        $authResult = $authContext.AcquireTokenAsync($resourceAppIdURI, $clientId, $redirectUri, $platformParameters, $userId).Result
        # If the accesstoken is valid then create the authentication header
        if ($authResult.AccessToken) {
            # Creating header for Authorization token
            $authHeader = @{
                'Content-Type' = 'application/json'
                'Authorization' = "Bearer " + $authResult.AccessToken
                'ExpiresOn' = $authResult.ExpiresOn
            }
            return $authHeader
        }
        else {
            Write-Host
            Write-Host "Authorization Access Token is null, please re-run authentication..." -ForegroundColor Red
            Write-Host
            break
        }
    }
    catch {
        write-host $_.Exception.Message -f Red
        write-host $_.Exception.ItemName -f Red
        write-host
        break
    }   
}

$authToken = Get-AuthToken -User "<Your AAD Username>"

try {
    $uri = "https://graph.microsoft.com/beta/me/managedDevices"
    Write-Verbose $uri
    (Invoke-RestMethod -Uri $uri –Headers $authToken –Method Get).Value
}
catch {
    $ex = $_.Exception
    $errorResponse = $ex.Response.GetResponseStream()
    $reader = New-Object System.IO.StreamReader($errorResponse)
    $reader.BaseStream.Position = 0
    $reader.DiscardBufferedData()
    $responseBody = $reader.ReadToEnd();
    Write-Host "Response content:`n$responseBody" -f Red
    Write-Error "Request to $Uri failed with HTTP Status $($ex.Response.StatusCode) $($ex.Response.StatusDescription)"
    write-host
    break
}
```

## <a name="support-multiple-tenants-and-partners"></a>複数のテナントとパートナーのサポート

独自の Azure AD テナントがある組織をサポートする組織の場合、それぞれのテナントでアプリケーションを使用するようにクライアントを許可する必要があることがあります。

これを実行するには、次のようにします。

1.  対象の Azure AD テナントに、クライアントのアカウントが存在することを確認します。

2.  テナント アカウントが、ユーザーによるアプリケーションの登録を許可していることを確認します (**ユーザー設定** をご覧ください)。

3.  各テナント間のリレーションシップを確立します。  

    そのためには、次のいずれかを実行します。

    a. [Microsoft Partner Center](https://partnercenter.microsoft.com/) を使用して、クライアントとそのメール アドレスのリレーションシップを定義します。

    b. ユーザーを招待して、テナントのゲストにします。

ユーザーを招待してテナントのゲストにするには、次を実行します。

1.  **[クイック タスク]** パネルで、**[ゲスト ユーザーの追加]** を選択します。

    <img src="media/azure-ad-add-guest.png" width="448" height="138" alt="Use Quick Tasks to add a guest user" />

2.  クライアントのメール アドレスを入力し、(必要に応じて) 招待状に個人的なメッセージを追加します。

    <img src="media/azure-ad-guest-invite.png" width="203" height="106" alt="Inviting an external user as a guest" />

3.  **[招待する]** を選択します。

これにより、ユーザーに招待状が送信されます。

   <img src="media/aad-multiple-tenant-invitation.png" width="624" height="523" alt="A sample guest invitation" />

   ユーザーは **[開始]** リンクを選択して、招待を承諾する必要があります。

リレーションシップが確立されると (または招待が承諾されると)、**[ディレクトリ ロール]** にユーザー アカウントが追加されます。

必要に応じて、そのほかのロールにユーザーを追加するようにします。 たとえば、ユーザーに Intune の設定の管理を許可する場合、ユーザーは **[グローバル管理者]** または **[Intune サービス管理者]** のいずれかである必要があります。

また、

- http://portal.office.com を使用して、ユーザー アカウントに Intune のライセンスを割り当てます。

- 自身ではなく、クライアントの Azure AD テナントのドメインに対する認証のためにアプリケーション コードを更新します。

    たとえば、自身のテナントのドメインが `contosopartner.onmicrosoft.com`、クライアントのテナントのドメインが `northwind.onmicrosoft.com` で、クライアントのテナントを認証するためにコードを更新するとします。

    先ほどの例に基づき C# アプリケーションでこれを実行するには、変数 `authority` の値を変更します。

    ``` csharp
    string authority = "https://login.microsoftonline.com/common/";
    ```

    を

    ``` csharp
    string authority = "https://login.microsoftonline.com/northwind.onmicrosoft.com/";
    ```
