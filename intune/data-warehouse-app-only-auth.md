---
title: Intune データ ウェアハウス アプリケーションのみの認証
titleSuffix: Microsoft Intune
description: このトピックでは、データ ウェアハウス アプリケーションのみの認証について説明します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/13/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d7166563-6bb5-4624-b8c8-6b300a997c3a
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: b72a0bf1a5f5c996ad299bd84ff6f927ef780059
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2018
ms.locfileid: "52185204"
---
# <a name="intune-data-warehouse-application-only-authentication"></a>Intune データ ウェアハウス アプリケーションのみの認証

Azure Active Directory (Azure AD) を使用してアプリケーションを設定し、Intune データ ウェアハウスに対する認証を実行できます。 このプロセスは、設定したアプリケーションにユーザー資格情報へのアクセス権を与えるべきではない Web サイト、アプリ、およびバック グラウンド プロセスで役に立ちます。 次の手順に従い、Azure AD で OAuth 2.0 を使用してアプリケーションを承認します。

## <a name="authorization"></a>承認

Azure Active Directory (Azure AD) では、OAuth 2.0 を使用して Azure AD テナントの Web アプリケーションと Web API へのアクセスを承認できます。 このガイドでは、C# を使用してアプリケーションを認証する方法について説明します。 OAuth 2.0 承認コード フローについては、OAuth 2.0 仕様のセクション 4.1 を参照してください。 詳細については、「[OAuth 2.0 と Azure Active Directory を使用した Web アプリケーションへのアクセスの承認](https://docs.microsoft.com/azure/active-directory/develop/active-directory-protocols-oauth-code)」を参照してください。


## <a name="azure-keyvault"></a>Azure KeyVault

次のプロセスでは、プライベート メソッドを使用して、アプリ キーの処理および変換を行います。 このプライベート メソッドには SecureString という名前が付けられています。 別の方法として、Azure KeyVault を使用してアプリ キーを格納することも可能です。 詳細については、[Key Vault](https://azure.microsoft.com/services/key-vault/)に関するページを参照してください。

## <a name="create-a-web-app"></a>Web アプリの作成

このセクションでは、Intune でポイントする Web アプリについて詳細を説明します。 Web アプリはクライアント/サーバー アプリケーションです。 サーバーから Web アプリが提供されます。これには UI、コンテンツ、および機能が含まれます。 この種のアプリは Web 上で個別に維持されます。 Intune を使用して Web アプリに Intune へのアクセス権を付与します。 データ フローは、Web アプリによって開始されます。 

1.  [Azure ポータル](https://portal.azure.com)にサインインします。
2.  Azure ポータルの上部付近にある **[リソース、サービス、ドキュメントを検索します]** フィールドを使用して、**[Azure Active Directory]** を検索します。
3.  ドロップダウン メニューで、**[サービス]** の **[Azure Active Directory]** を選択します。
4.  **[アプリの登録する]** を選択します。
5.  **[新しいアプリケーションの登録]** をクリックして、**[作成]** ブレードを表示します。
6.  **[作成]** ブレードで、アプリの詳細を追加します:

    - *Intune App-Only Auth* などのアプリ名。
    - **アプリケーションの種類**。 **[Web アプリ/API]** を選択して、Web アプリケーション、Web API、またはその両方を表すアプリを追加します。
    - アプリケーションの**サインオン URL**。 ここは、認証プロセス中にユーザーが自動的に移動する場所です。 ユーザーは身元の証明を求められます。 詳細については、「[Azure Active Directory のアプリケーション アクセスとシングル サインオンとは](https://docs.microsoft.com/azure/active-directory/active-directory-appssoaccess-whatis)」を参照してください。

7.  **[作成]** ブレードの下にある **[作成]** をクリックします。

    >[!NOTE] 
    > 後で使用するために、**[登録されているアプリ]** から **[アプリケーション ID]** をコピーします。

## <a name="create-a-key"></a>キーの作成

このセクションでは、Azure AD でアプリのキー値を生成します。

1.  **[アプリ登録]** ブレードで、新規に作成したアプリを選択してアプリ ブレードを表示します。
2.  ブレードの上部付近にある **[設定]** を選択して、**[設定]** ブレードを表示します。
3.  **[設定]** ブレードで **[キー]** を選択します。
4.  キーの**説明**、**有効期間**、およびキーの**値**を追加します。
5.  **[保存]** をクリックして、アプリケーションのキーを保存および更新します。
6.  生成されたキーの値 (Base64 エンコード) をコピーする必要があります。

    >[!NOTE] 
    > **[キー]** ブレードから移動すると、キーの値は非表示になります。 このブレードから後でキーを取得することはできません。 後で使用するためにコピーしておきます。

## <a name="grant-application-permissions"></a>アプリケーションへのアクセス許可の付与

このセクションでは、アプリケーションにアクセス許可を付与します。

1.  **[設定]** ブレードで **[必要なアクセス許可]** を選択します。
2.  **[追加]** をクリックします。
3.  **[API の追加]** を選択して **[API の選択]** ブレードを表示します。
4.  **[Microsoft Intune API (MicrosoftIntuneAPI)]** を選択し、**[API の選択]** ブレードで **[選択]** をクリックします。 **[アクセス許可の選択]** 手順が選択され、**[アクセスの有効化]** ブレードが表示されます。
5.  **[アプリケーションのアクセス許可]** セクションで、**[Get data warehouse information from Microsoft Intune]\(Microsoft Intune からデータ ウェアハウスの情報を取得する\)** オプションを選択します。
6.  **[アクセスの有効化]** ブレードで **[選択]** をクリックします。
7.  **[API アクセスの追加]** ブレードで **[完了]** をクリックします。
8.  **[必要なアクセス許可]** ブレードで **[アクセス許可の付与]** をクリックします。このアプリケーションに既に付与されている既存のアクセス許可を更新するように促されたら **[はい]** をクリックします。

## <a name="generate-token"></a>トークンの生成

.NET Framework をサポートし、コーディング言語として C# を使用するコンソール アプリ (.NET Framework) プロジェクトを、Visual Studio を使用して作成します。

1.  **[ファイル]** > **[新規]** > **[プロジェクト]** を選択して、**[新しいプロジェクト]** ダイアログ ボックスを表示します。
2.  左側で、**[Visual C#]** を選択して、すべての .NET Framework プロジェクトを表示します。
3.  **[コンソール アプリ (.NET Framework)]** を選択し、アプリ名を追加し、**[OK]** をクリックして、アプリを作成します。
4.  **ソリューション エクスプローラー**で **[Program.cs]** を選択してコードを表示します。
5.  ポップアップ メニューで、**[追加]** > **[新しい項目]** を選択します。 **[新しい項目の追加]** ダイアログ ボックスが表示されます。
6.  左側にある **[Visual C#]** で **[コード]** を選択します。
7.  **[クラス]** を選択し、クラスの名前を "*IntuneDataWarehouseClass.cs*" に変更し、**[追加]** をクリックします。
8.  <code>Main</code> メソッドに次のコードを追加します。

    ``` csharp
         var applicationId = ConfigurationManager.AppSettings["appId"].ToString();
         SecureString applicationSecret = ConvertToSecureStr(ConfigurationManager.AppSettings["appKey"].ToString()); // Load as SecureString from configuration file or secret store (i.e. Azure KeyVault)
         var tenantDomain = ConfigurationManager.AppSettings["tenantDomain"].ToString();
         var adalContext = new AuthenticationContext($"https://login.windows.net/" + tenantDomain + "/oauth2/token");
    
         AuthenticationResult authResult = adalContext.AcquireTokenAsync(
             resource: "https://api.manage.microsoft.com/",
             clientCredential: new ClientCredential(
                 applicationId,
                 new SecureClientSecret(applicationSecret))).Result;
    ``` 

9. コード ファイルの先頭に次のコードを追加して、追加の名前空間を追加します。

    ``` csharp
     using System.Security;
     using Microsoft.IdentityModel.Clients.ActiveDirectory;
     using System.Configuration;
    ``` 

10. <code>Main</code> メソッドの後に、次のプライベート メソッドを追加して、アプリ キーの処理および変換を行います。

    ``` csharp
    private static SecureString ConvertToSecureStr(string appkey)
    {
        if (appkey == null)
            throw new ArgumentNullException("AppKey must not be null.");
    
        var secureAppKey = new SecureString();
    
        foreach (char c in appkey)
            secureAppKey.AppendChar(c);
    
        secureAppKey.MakeReadOnly();
        return secureAppKey;
    }
    ```

11. **ソリューション エクスプローラー**で、**[参照]** を右クリックし、**[NuGet パッケージの管理]** をクリックします。
12. *Microsoft.IdentityModel.Clients.ActiveDirectory* を検索し、関連する Microsoft NuGet パッケージをインストールします。
13. **ソリューション エクスプローラー**で、*App.config* ファイルを選択して開きます。
14. xml が次のように表示されるように、<code>appSettings</code> セクションを追加します。

    ``` xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
        <startup> 
            <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6.1" />
        </startup>
        <appSettings>
          <add key="appId" value="App ID created from 'Create a Web App' procedure"/>
          <add key="appKey" value="Key created from 'Create a key' procedure" />
          <add key="tenantDomain" value="contoso.onmicrosoft.com"/>
        </appSettings>
    </configuration>
    ``` 

15. 一意のアプリ関連の値に一致するように、<code>appId</code>、<code>appKey</code>、<code>tenantDomain</code> の各値を更新します。
16. アプリをビルドします。

    >[!NOTE] 
    > その他の実装コードについては、[Intune データ ウェアハウスのコード例](https://github.com/Microsoft/Intune-Data-Warehouse/tree/master/Samples/CSharp )に関するページを参照してください。

## <a name="next-steps"></a>次の手順
Azure Key Vault の詳細については、「[Azure Key Vault とは](https://docs.microsoft.com/azure/key-vault/key-vault-whatis)」を参照してください。

