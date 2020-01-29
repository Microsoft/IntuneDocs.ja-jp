---
title: iOS 用 Microsoft Intune App SDK 開発者ガイド
description: iOS 用 Microsoft Intune App SDK を使用すると、ネイティブ iOS アプリに Intune アプリ保護ポリシー (APP ポリシーまたは MAM ポリシーともいう) を組み込むことができます。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/02/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 8e280d23-2a25-4a84-9bcb-210b30c63c0b
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: f6edf3fd8d6c6aeefeb1e34c5b390360e7215f21
ms.sourcegitcommit: 822a70c61f5d644216ccc401b8e8949bc39e8d4a
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2020
ms.locfileid: "76125295"
---
# <a name="microsoft-intune-app-sdk-for-ios-developer-guide"></a>iOS 用 Microsoft Intune App SDK 開発者ガイド

> [!NOTE]
> [Intune App SDK ガイドの概要](app-sdk-get-started.md)に関する記事を読むことを検討してください。このガイドでは、サポートされる各プラットフォームで統合のための準備をする方法について説明しています。

iOS 用 Microsoft Intune App SDK を使用すると、ネイティブ iOS アプリに Intune アプリ保護ポリシー (APP ポリシーまたは MAM ポリシーともいう) を組み込むことができます。 MAM 対応のアプリケーションが Intune アプリ SDK に統合されています。 Intune で積極的にアプリを管理している場合、IT 管理者はモバイル アプリにアプリ保護ポリシーを展開できます。

## <a name="prerequisites"></a>[前提条件]

* OS X 10.8.5 以降を実行していて、また Xcode 9 以降もインストールされている Mac OS コンピューターが必要になります。

* アプリは iOS 11 以降を対象としている必要があります。

* [iOS 用の Intune アプリ SDK のライセンス条項](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios/blob/master/Microsoft%20License%20Terms%20Intune%20App%20SDK%20for%20iOS.pdf)を読みます。 記録としてライセンス条項を印刷し、保管します。 iOS 用の Intune App SDK をダウンロードし、使用すると、このライセンス条項に同意したことになります。  本ライセンス条項に同意されない場合、本ソフトウェアを使用することはできません。

* [GitHub](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios) で iOS 用 Intune アプリ SDK のファイルをダウンロードします。

## <a name="whats-in-the-sdk-repository"></a>SDK リポジトリの内容

以下のファイルは、Swift コードを含まないアプリや拡張機能に関連しているか、または 10.2 より前のバージョンの Xcode でコンパイルされています。

* **IntuneMAM.framework**:Intune アプリ SDK フレームワーク。 このフレームワークをアプリまたは拡張機能にリンクして、Intune クライアント アプリケーションの管理を有効にすることをお勧めします。 ただし、開発者によっては、スタティック ライブラリのパフォーマンス上の利点が優先される場合があります。 以下をご覧ください。

* **libIntuneMAM.a**:Intune アプリ SDK の静的ライブラリ。 開発者は、フレームワークではなく、スタティック ライブラリをリンクすることを選択できます。 スタティック ライブラリはビルド時にアプリまたは拡張機能のバイナリに直接埋め込まれるため、スタティック ライブラリを使用すると起動時のパフォーマンスが若干よくなります。 ただし、それをアプリに統合するプロセスはより複雑です。 アプリに拡張機能が含まれている場合、スタティック ライブラリをアプリと拡張機能にリンクすると、アプリのバンドルのサイズが大きくなります。スタティック ライブラリがアプリと拡張機能の各バイナリに埋め込まれるためです。 フレームワークを使用すると、アプリと拡張機能は同じ Intune SDK バイナリを共有でき、その結果、アプリのサイズが小さくなります。

* **IntuneMAMResources.bundle**:SDK が依存するリソースが含まれているリソース バンドル。 リソース バンドルは、スタティック ライブラリ (libIntuneMAM.a) を統合するアプリに対してのみ必要です。

以下のファイルは、Swift コードを含むアプリと拡張機能に関連し、Xcode 10.2 以降を使用してコンパイルされます。

* **IntuneMAMSwift.framework**: Intune App SDK Swift フレームワーク。 このフレームワークには、アプリで呼び出される API のすべてのヘッダーが含まれています。 Intune クライアント アプリケーションの管理を有効にするには、このフレームワークをアプリまたは拡張機能にリンクします。

* **IntuneMAMSwiftStub.framework**: Intune App SDK Swift スタブ フレームワーク。 これは、アプリおよび拡張機能をリンクする必要がある IntuneMAMSwift.framework の必須の依存関係です。


以下のファイルは、すべてのアプリと拡張機能に関係しています。

* **IntuneMAMConfigurator**: Intune の管理に対する変更を必要最小限にして、アプリまたは拡張機能の Info.plist を構成するために使用されるツール。 アプリまたは拡張機能の機能によっては、Info.plist を手動でさらに変更することが必要な場合があります。

* **ヘッダー**:パブリックな Intune アプリ SDK の API を表示します。 これらのヘッダーは IntuneMAM および IntuneMAMSwift フレームワーク内に含まれているので、いずれかのフレームワークを使用する開発者は、ヘッダーをプロジェクトに手動で追加する必要はありません。 スタティック ライブラリ (libIntuneMAM.a) へのリンクを選択した開発者は、これらのヘッダーをプロジェクトに手動で含める必要があります。

次のヘッダー ファイルには、Intune App SDK から開発者に提供されている API、データ型、プロトコルが含まれています。

-  IntuneMAMAppConfig.h
-  IntuneMAMAppConfigManager.h
-  IntuneMAMDataProtectionInfo.h
-  IntuneMAMDataProtectionManager.h
-  IntuneMAMDefs.h
-  IntuneMAMDiagnosticConsole.h
-  IntuneMAMEnrollmentDelegate.h
-  IntuneMAMEnrollmentManager.h
-  IntuneMAMEnrollmentStatus.h
-  IntuneMAMFileProtectionInfo.h
-  IntuneMAMFileProtectionManager.h
-  IntuneMAMLogger.h
-  IntuneMAMPolicy.h
-  IntuneMAMPolicyDelegate.h
-  IntuneMAMPolicyManager.h
-  IntuneMAMVersionInfo.h

開発者は、IntuneMAM.h をインポートするだけで、前のすべてのヘッダーの内容を使用可能にすることができます


## <a name="how-the-intune-app-sdk-works"></a>Intune アプリ SDK のしくみ

iOS 用 Intune アプリ SDK の目的は、最小限のコード変更で iOS アプリケーションに管理機能を追加することです。 コードの変更が少ないほど、市場投入までの時間が短くなりますが、モバイル アプリケーションの一貫性と安定性に影響を出ることはありません。


## <a name="build-the-sdk-into-your-mobile-app"></a>モバイル アプリとして SDK をビルドする

Intune アプリ SDK を有効にするには、次の手順を実行します。

1. **オプション 1 - フレームワーク (推奨)** :Xcode 10.2 + を使用していて、アプリまたは拡張機能に Swift コードが含まれている場合は、`IntuneMAMSwift.framework` と `IntuneMAMSwiftStub.framework` をターゲットにリンクします。プロジェクトのターゲットの **[Embedded Binaries]\(埋め込みバイナリ\)** の一覧に、`IntuneMAMSwift.framework` と `IntuneMAMSwiftStub.framework` をドラッグします。

    それ以外の場合は、ターゲットに `IntuneMAM.framework` をリンクします。`IntuneMAM.framework` をプロジェクト ターゲットの**埋め込みバイナリ**の一覧にドラッグします。

   > [!NOTE]
   > フレームワークを使用する場合は、App Store にアプリを送信する前に、ユニバーサル フレームワークからシミュレーター アーキテクチャを手動で除去する必要があります。 詳細については、「[iOS 用 Microsoft Intune App SDK 開発者ガイド](#submit-your-app-to-the-app-store)」を参照してください。

   **オプション 2 - スタティック ライブラリ**: このオプションは、Swift コードが含まれないアプリや拡張機能、または 10.2 未満の Xcode でビルドされたアプリや拡張機能でのみ使用できます。 `libIntuneMAM.a` ライブラリにリンクします。 `libIntuneMAM.a` ライブラリをプロジェクト ターゲットの **[Linked Frameworks and Libraries]** (リンク先フレームワークおよびライブラリ) ボックスの一覧にドラッグします。

    ![Intune App SDK iOS: リンク先フレームワークおよびライブラリ](./media/app-sdk-ios/intune-app-sdk-ios-linked-frameworks-and-libraries.png)

    `-force_load {PATH_TO_LIB}/libIntuneMAM.a` を次のいずれかに追加します。`{PATH_TO_LIB}` は、Intune アプリ SDK の場所に置き換えてください。
   * プロジェクトの `OTHER_LDFLAGS` ビルド構成設定。
   * Xcode UI の **[その他のリンカー フラグ]** 。

     > [!NOTE]
     > `PATH_TO_LIB` を検索するには、`libIntuneMAM.a` ファイルを選択し、 **[ファイル]** メニューの **[情報の取得]** を選択します。 **[情報]** ウィンドウの **[全般]** セクションから、 **[場所]** 情報 (パス) をコピーして貼り付けます。

     **[ビルド フェーズ]** の **[Copy Bundle Resources (バンドル リソースのコピー)]** にあるリソース バンドルをドラッグして、`IntuneMAMResources.bundle` リソース バンドルをプロジェクトに追加します。

     ![Intune App SDK iOS: バンドル リソースのコピー](./media/app-sdk-ios/intune-app-sdk-ios-copy-bundle-resources.png)
         
2. 次の iOS フレームワークをプロジェクトに追加します。  
-  MessageUI.framework  
-  Security.framework  
-  MobileCoreServices.framework  
-  SystemConfiguration.framework  
-  libsqlite3.tbd  
-  libc++.tbd  
-  ImageIO.framework  
-  LocalAuthentication.framework  
-  AudioToolbox.framework  
-  QuartzCore.framework  
-  WebKit.framework

3. 各プロジェクト ターゲットの **[機能]** を選択し、 **[Keychain Sharing]** (キーチェーン共有) スイッチを有効にして、キーチェーン共有を有効にします (まだ有効になっていない場合)。 次の手順に進むには、キーチェーン共有が必要です。

   > [!NOTE]
   > プロビジョニング プロファイルで新しいキーチェーン共有値がサポートされている必要があります。 キーチェーン アクセス グループは、ワイルドカード文字をサポートする必要があります。 これを確認するには、テキスト エディターで .mobileprovision ファイルを開いて **keychain-access-groups** を検索し、ワイルドカード文字があることを確認します。 次に例を示します。
   >
   >  ```xml
   >  <key>keychain-access-groups</key>
   >  <array>
   >  <string>YOURBUNDLESEEDID.*</string>
   >  </array>
   >  ```

4. キーチェーン共有を有効にした後、次の手順に従って、Intune App SDK がデータを格納する個別のアクセス グループを作成します。 キーチェーン アクセス グループを作成するには、UI を使用するか、権利ファイルを使用します。 キーチェーン アクセス グループを作成する UI を使用している場合、次の手順を実行してください。

     」を参照します。 モバイル アプリでキーチェーン アクセス グループが定義されていない場合は、アプリのバンドル ID を**最初**のグループとして追加します。
    
    b. 共有キーチェーン グループ `com.microsoft.intune.mam` を既存のアクセス グループに追加します。 このアクセス グループは、Intune アプリ SDK でデータを格納するために使用されます。
    
    c. `com.microsoft.adalcache` を既存のアクセス グループに追加します。
    
      ![Intune App SDK iOS: キーチェーン共有](./media/app-sdk-ios/intune-app-sdk-ios-keychain-sharing.png)
    
    d. 前に示したキーチェーン アクセス グループを作成する Xcode UI を使用するのではなく、権利ファイルを直接編集している場合、キーチェーン アクセス グループの先頭に `$(AppIdentifierPrefix)` を追加します (Xcode ではこの処理が自動的に行われます)。 次に例を示します。
    
      - `$(AppIdentifierPrefix)com.microsoft.intune.mam`
      - `$(AppIdentifierPrefix)com.microsoft.adalcache`
    
      > [!NOTE]
      > 権利ファイルとは、自分のモバイル アプリケーションに固有の XML ファイルです。 iOS アプリで特別なアクセス許可と機能を指定するために使用されます。 お使いのアプリにあらかじめ権利ファイルが無かった場合、キーチェーンの共有 (手順 3) を有効にすると Xcode によってアプリ用に権利ファイルが生成されます。 アプリのバンドル ID が一覧の最初のエントリであることを確認します。

5. アプリが `UIApplication canOpenURL` に渡す各プロトコルを、アプリの Info.plist ファイルの `LSApplicationQueriesSchemes` 配列に含めます。 次の手順に進む前に、変更内容を必ず保存してください。

6. アプリでまだ FaceID が使用されていない場合、既定のメッセージと共に [NSFaceIDUsageDescription Info.plist キー](https://developer.apple.com/library/archive/documentation/General/Reference/InfoPlistKeyReference/Articles/CocoaKeys.html#//apple_ref/doc/uid/TP40009251-SW75)が確実に構成されているようにします。 これは、iOS がアプリでの FaceID の用途をユーザーに通知するために必要です。 Intune アプリ保護ポリシー設定では、IT 管理者が構成している場合、アプリにアクセスするための手段として FaceID を使用することが許可されています。

7. [SDK のリポジトリ](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios)に含まれる IntuneMAMConfigurator ツールを使用して、アプリの Info.plist の構成を終了します。 このツールには、次の 3 つのパラメーターがあります。

   |プロパティ|使用方法|
   |---------------|--------------------------------|
   |- i |  `<Path to the input plist>` |
   |- e | `<Path to the entitlements file>` |
   |- o |  (省略可能) `<Path to the output plist>` |

"-o" パラメーターが指定されていない場合、入力ファイルはインプレースで変更されます。 このツールにはべき等性があるため、アプリの Info.plist や権利に変更が入った場合は再実行してください。 また、Intune SDK を更新する際は、ツールの最新バージョンをダウンロードして実行してください。これは、Info.plist の構成要件が、最新のリリースで変更されている場合があるためです。

## <a name="configure-adalmsal"></a>ADAL/MSAL を構成する

Intune App SDK では、認証と条件付き起動のシナリオに対し、[Azure Active Directory 認証ライブラリ](https://github.com/AzureAD/azure-activedirectory-library-for-objc)または [Microsoft 認証ライブラリ](https://github.com/AzureAD/microsoft-authentication-library-for-objc)のいずれかを使用できます。 また、デバイスを登録しないで管理するために MAM サービスにユーザー ID を登録する場合も、ADAL/MSAL を利用します。

通常、ADAL/MSAL では、アプリに付与されるトークンのセキュリティを保証するために、アプリを Azure Active Directory (AAD) に登録し、一意のクライアント ID とリダイレクト URI を作成する必要があります。 アプリで既に ADAL または MSAL を使ってユーザーを認証している場合、そのアプリではその既存の登録値を使い、Intune App SDK の既定値をオーバーライドする必要があります。 これにより、ユーザーに認証が 2 回 (Intune アプリ SDK で 1 回、アプリで 1 回) 求められることがなくなります。

アプリで ADAL または MSAL をまだ使用しておらず、どの AAD リソースにもアクセスする必要がない場合は、ADAL の統合を選択した場合でも、AAD でクライアント アプリの登録を設定する必要はありません。 MSAL を統合する場合は、アプリの登録を構成し、既定の Intune クライアント ID とリダイレクト URI をオーバーライドする必要があります。  

アプリでは [ADAL](https://github.com/AzureAD/azure-activedirectory-library-for-objc/releases) または [MSAL](https://github.com/AzureAD/microsoft-authentication-library-for-objc/releases) の最新リリースにリンクすることをお勧めします。

### <a name="link-to-adal-or-msal-binaries"></a>ADAL または MSAL のバイナリにリンクする

**オプション 1 -** [こちらの手順](https://github.com/AzureAD/azure-activedirectory-library-for-objc#download)に従って、アプリを ADAL バイナリにリンクします。

**オプション 2 -** または、[こちらの説明](https://github.com/AzureAD/microsoft-authentication-library-for-objc#installation)に従って、アプリを MSAL バイナリにリンクすることもできます。

1. アプリでキーチェーン アクセス グループが定義されていない場合は、アプリのバンドル ID を最初のグループとして追加します。

2. `com.microsoft.adalcache` をキーチェーン アクセス グループに追加することによって、ADAL/MSAL シングル サインオン (SSO) を有効にします。

3. ADAL 共有キャッシュ キーチェーン グループを明示的に設定している場合は、`<appidprefix>.com.microsoft.adalcache` に設定されていることを確認します。 オーバーライドしない限り ADAL はこれを自動的に設定します。 カスタム キーチェーン グループを指定して `com.microsoft.adalcache` を置き換える場合は、Info.plist ファイルの IntuneMAMSettings でキー `ADALCacheKeychainGroupOverride` を使用して指定します。

### <a name="configure-adalmsal-settings-for-the-intune-app-sdk"></a>Intune App SDK の ADAL/MSAL 設定を構成する

アプリで既に認証用に ADAL または MSAL を使っていて、独自の Azure Active Directory 設定がある場合は、AAD に対する認証中に同じ設定を使うよう Intune App SDK に強制することができます。 これで、アプリがユーザーに重複して認証を求めないようになります。 次の設定の構成については、「[Intune App SDK の設定を構成する](#configure-settings-for-the-intune-app-sdk)」を参照してください。  

* ADALClientId
* ADALAuthority
* ADALRedirectUri
* ADALRedirectScheme
* ADALCacheKeychainGroupOverride

アプリで既に ADAL または MSAL を使っている場合、次の構成が必要です。

1. プロジェクトの Info.plist ファイルの **IntuneMAMSettings** ディクショナリで、キー名 `ADALClientId` を使用して、ADAL 呼び出しに使用するクライアント ID を指定します。

2. また、**IntuneMAMSettings** ディクショナリで、キー名 `ADALAuthority` を使用して Azure AD 機関を指定します。

3. さらに、**IntuneMAMSettings** ディクショナリで、キー名 `ADALRedirectUri` を使用して、ADAL 呼び出しに使用するリダイレクト URI を指定します。 また、アプリケーションのリダイレクト URI の形式が `scheme://bundle_id` の場合は、代わりに `ADALRedirectScheme` を指定することもできます。

さらに、アプリは、実行時にこれらの Azure AD 設定をオーバーライドすることができます。 上書きするには、`IntuneMAMPolicyManager` インスタンスの `aadAuthorityUriOverride`、`aadClientIdOverride`、および `aadRedirectUriOverride` プロパティを設定します。

4. iOS のアプリにアプリ保護ポリシー (APP) サービスへのアクセス許可を付与するための手順に従っていることを確認します。 [Intune SDK ガイドの概要](app-sdk-get-started.md#next-steps-after-integration)に関するページの「[Intune アプリ保護サービスへのアクセス権をアプリに付与する (省略可能)](app-sdk-get-started.md#give-your-app-access-to-the-intune-app-protection-service-optional)」の下に記載されている手順を使用します。  

> [!NOTE]
> Info.plist アプローチは、静的で、かつ実行時に定義する必要がないあらゆる設定に推奨されます。 `IntuneMAMPolicyManager` のプロパティに割り当てられた値は、Info.plist で指定された対応するどの値よりも優先され、アプリの再起動後も保持されます。 ユーザーの登録が解除されるまで、あるいは値が消去または変更されるまで、SDK は引き続きこの値を使用してポリシーのチェックインを行います。

### <a name="if-your-app-does-not-use-adal-or-msal"></a>アプリで ADAL または MSAL を使用していない場合

前に説明したように、Intune App SDK では、認証と条件付き起動のシナリオに対し、[Azure Active Directory 認証ライブラリ](https://github.com/AzureAD/azure-activedirectory-library-for-objc)または [Microsoft 認証ライブラリ](https://github.com/AzureAD/microsoft-authentication-library-for-objc)のいずれかを使用できます。 また、デバイスを登録しないで管理するために MAM サービスにユーザー ID を登録する場合も、ADAL/MSAL を利用します。 **アプリで独自の認証メカニズム用に ADAL または MSAL を使用しない**場合、統合することを選択した認証ライブラリによっては、カスタム AAD の設定を構成することが必要な場合があります。   

ADAL - Intune App SDK により ADAL パラメーターの既定値が指定され、Azure AD に対する認証が処理されます。 開発者は、前に説明した ADAL の設定に値を指定する必要はありません。 

MSAL - 開発者は、[こちら](https://github.com/AzureAD/microsoft-authentication-library-for-objc/wiki/Migrating-from-ADAL-Objective-C-to-MSAL-Objective-C#app-registration-migration)で指定されている形式のカスタム リダイレクト URI を使用して、AAD でのアプリの登録を作成する必要があります。 開発者は、前に説明した `ADALClientID` および `ADALRedirectUri` の設定、または `IntuneMAMPolicyManager` インスタンスの `aadClientIdOverride` および `aadRedirectUriOverride` のプロパティを設定する必要があります。 また、開発者は、前のセクションのステップ 4 に従って、アプリの登録に Intune App Protection サービスへのアクセスを許可する必要があります。

### <a name="special-considerations-when-using-msal"></a>MSAL を使用する場合の特別な考慮事項 

1. **Web ビューを確認する** - アプリケーションでは、アプリによって開始される MSAL 対話型認証操作用の Web ビューとして、SFSafariViewController、SFAuthSession、または ASWebAuthSession を使用しないことをお勧めします。 何らかの理由で、対話型 MSAL 認証操作用にこれらの Web ビューのいずれかをアプリで使用する必要がある場合は、アプリケーションの Info.plist の `IntuneMAMSettings` ディクショナリで `SafariViewControllerBlockedOverride` を `true` に設定する必要もあります。 警告: このようにすると、Intune の SafariViewController フックが無効になり、認証セッションが有効になります。 アプリケーションで会社のデータを表示するために SafariViewController を使用している場合、これによりアプリの他の場所でデータがリークする恐れがあるので、アプリケーションでは、これらの Web ビューの種類のいずれでも会社のデータを表示しないようにする必要があります。
2. **ADAL と MSAL の両方をリンクする** - 開発者は、このシナリオの Intune で ADAL より MSAL を優先するかどうかを選択する必要があります。 両方が実行時にリンクされている場合、既定の Intune では、サポートされる MSAL バージョンより、サポートされる ADAL バージョンが優先されます。 Intune では、Intune の最初の認証操作のときに、`NSUserDefaults` で `IntuneMAMUseMSALOnNextLaunch` が `true` に設定されている場合にのみ、サポートされる MSAL バージョンが優先されます。 `IntuneMAMUseMSALOnNextLaunch` が `false` であるか設定されていない場合、Intune は既定の動作に戻ります。 名前が示すように、`IntuneMAMUseMSALOnNextLaunch` に対する変更は、次回の起動時に有効になります。


## <a name="configure-settings-for-the-intune-app-sdk"></a>Intune App SDK の設定を構成する

アプリケーションの Info.plist ファイルの **IntuneMAMSettings** ディクショナリを使用し、Intune App SDK をセットアップして構成することができます。 IntuneMAMSettings ディクショナリが Info.plist ファイルに表示されない場合は、作成する必要があります。

IntuneMAMSettings ディクショナリの下に、次のサポートされる設定を使用して Intune App SDK を構成することができます。

これらの設定の一部は前のセクションで説明しています。一部の設定はすべてのアプリには適用されません。

設定  | Type  | 定義 | 必須
--       |  --   |   --       |  --
ADALClientId  | 文字列型  | アプリの Azure AD クライアント識別子。 | MSAL を使用するすべてのアプリと、Intune 以外の AAD リソースにアクセスするすべての ADAL アプリに必要です。 |
ADALAuthority | 文字列型 | 使用されているアプリの Azure AD 機関。 AAD アカウントが構成されている独自の環境を使用する必要があります。 | アプリで ADAL または MSAL を使用して Intune 以外の AAD リソースにアクセスする場合に必要です。 この値が存在しない場合は、Intune の既定値が使用されます。|
ADALRedirectUri  | 文字列型  | アプリの Azure AD リダイレクト URI。 | ADALRedirectUri または ADALRedirectScheme は、MSAL を使用するすべてのアプリと、Intune 以外の AAD リソースにアクセスするすべての ADAL アプリに必要です。  |
ADALRedirectScheme  | 文字列型  | アプリの Azure AD リダイレクト スキーム。 アプリケーションのリダイレクト URI が `scheme://bundle_id` 形式の場合は、ADALRedirectUri の代わりにこれを使用できます。 | ADALRedirectUri または ADALRedirectScheme は、MSAL を使用するすべてのアプリと、Intune 以外の AAD リソースにアクセスするすべての ADAL アプリに必要です。 |
ADALLogOverrideDisabled | ブール型  | SDK によって、すべての ADAL/MSAL ログ (アプリからの ADAL 呼び出しがある場合はこれを含む) が独自のログ ファイルにルーティングされるかどうかを指定します。 既定は [いいえ] です。 アプリで独自の ADAL/MSAL ログ コールバックを設定する場合は、[はい] に設定します。 | 任意。 |
ADALCacheKeychainGroupOverride | 文字列型  | "com.microsoft.adalcache" の代わりに ADAL/MSAL キャッシュに使用するキーチェーン グループを指定します。 これにはアプリ ID プレフィックスは含まれないことに注意してください。 実行時に指定された文字列の前に付加されます。 | 任意。 |
AppGroupIdentifiers | 文字列の配列  | アプリの権利 com.apple.security.application-groups セクションのアプリケーション グループの配列。 | アプリでアプリケーション グループを使用する場合は必須です。 |
ContainingAppBundleId | 文字列型 | アプリケーションを含む拡張機能のバンドル ID を指定します。 | iOS の拡張機能に必要です。 |
DebugSettingsEnabled| ブール型 | YES に設定すると、Settings バンドル内のテスト ポリシーを適用できます。 この設定を有効にしたままアプリケーションを出荷しては*なりません*。 | 任意。 既定値は [いいえ] です。 |
AutoEnrollOnLaunch| ブール型| 既存の管理対象の ID が検出され、それがまだ登録されていない場合、起動時に自動登録を試みるかどうかを指定します。 既定は [いいえ] です。 <br><br> 注:マネージド ID が検出されない場合、またはその ID に対する有効なトークンが ADAL/MSAL キャッシュ内に存在しない場合は、アプリで MAMPolicyRequired も [はい] に設定されていない限り、資格情報を求めるメッセージを表示することなく登録の試みは失敗します。 | 任意。 既定値は [いいえ] です。 |
MAMPolicyRequired| ブール型| アプリに Intune アプリ保護ポリシーがない場合に、アプリの起動をブロックするかどうかを指定します。 既定は [いいえ] です。 <br><br> 注:MAMPolicyRequired を [はい] に設定した状態でアプリを App Store に送信することはできません。 MAMPolicyRequired を YES に設定した場合は、AutoEnrollOnLaunch も YES に設定する必要があります。 | 任意。 既定値は [いいえ] です。 |
MAMPolicyWarnAbsent | ブール型| アプリに Intune アプリ保護ポリシーがない場合に、アプリの起動時にユーザーに警告するかどうかを指定します。 <br><br> 注:警告を無視した後、ユーザーはポリシーなしで引き続きアプリを使用することができます。 | 任意。 既定値は [いいえ] です。 |
MultiIdentity | ブール型| アプリが複数 ID 対応かどうかを指定します。 | 任意。 既定値は [いいえ] です。 |
SafariViewControllerBlockedOverride | ブール型| Intune の SafariViewController フックを無効にして、SFSafariViewController、SFAuthSession、または ASWebAuthSession による MSAL 認証を有効にします。 | 任意。 既定値は [いいえ] です。 警告: 不適切に使用した場合、データがリークする可能性があります。 どうしても必要な場合にのみ有効にします。 詳しくは、「[MSAL を使用する場合の特別な考慮事項](#special-considerations-when-using-msal)」をご覧ください。  |
SplashIconFile <br>SplashIconFile~ipad | 文字列型  | Intune スプラッシュ (起動) アイコン ファイルを指定します。 | 任意。 |
SplashDuration | 数値 | アプリケーションの起動時に Intune 起動画面が表示される最短時間 (秒)。 既定値は 1.5 です。 | 任意。 |
BackgroundColor| 文字列型| Intune SDK の UI コンポーネントの背景色を指定します。 #XXXXXX の形式の 16 進 RGB 文字列を受け付けます。X には 0 ～ 9 または A ～ F を使用できます。 シャープ記号は省略してもかまいません。   | 任意。 既定では、システムの背景色が使用されます。これは、iOS のバージョンと、iOS のダーク モードの設定によって異なる場合があります。 |
ForegroundColor| 文字列型| テキストの色など、Intune SDK の UI コンポーネントの前景色を指定します。 #XXXXXX の形式の 16 進 RGB 文字列を受け付けます。X には 0 ～ 9 または A ～ F を使用できます。 シャープ記号は省略してもかまいません。  | 任意。 既定では、システムのラベルの色が使用されます。これは、iOS のバージョンと、iOS のダーク モードの設定によって異なる場合があります。 |
AccentColor | 文字列型| ボタン テキストの色や PIN ボックスの強調表示色など、Intune SDK の UI コンポーネントのアクセント カラーを指定します。 #XXXXXX の形式の 16 進 RGB 文字列を受け付けます。X には 0 ～ 9 または A ～ F を使用できます。 シャープ記号は省略してもかまいません。| 任意。 既定値はシステムの青です。 |
SupportsDarkMode| ブール型 | BackgroundColor、ForegroundColor、AccentColor に対して明示的な値が設定されていない場合、Intune SDK の UI の配色をシステムのダーク モードの設定に合わせるかどうかを指定します | 任意。 既定値は [はい] です。 |
MAMTelemetryDisabled| ブール型| SDK に製品利用統計情報データをバックエンドに送信させないかどうかを指定します。| 任意。 既定値は [いいえ] です。 |
MAMTelemetryUsePPE | ブール型 | MAM SDK にデータを PPE テレメトリ バックエンドに送信させるかどうかを指定します。 テスト用テレメトリ データが顧客データと混ざらないように Intune ポリシーでアプリをテストするときに使用します。 | 任意。 既定値は [いいえ] です。 |
MaxFileProtectionLevel | 文字列型 | 任意。 アプリがサポートできる `NSFileProtectionType` の最大値を指定できるようにします。 レベルがアプリケーションによりサポートされるレベルよりも高い場合、この値がサービスによって送信されたポリシーをオーバーライドします。 有効値は、`NSFileProtectionComplete`、`NSFileProtectionCompleteUnlessOpen`、`NSFileProtectionCompleteUntilFirstUserAuthentication`、`NSFileProtectionNone` です。|
OpenInActionExtension | ブール型 | Open in Action 拡張を [はい] に設定します。 詳細については、「Sharing Data via UIActivityViewController」 (UIActivityViewController によるデータの共有) セクションを参照してください。 |
WebViewHandledURLSchemes | 文字列の配列 | アプリの WebView で処理する URL スキームを指定します。 | リンクや JavaScript で URL を処理する WebView をアプリが使用する場合は、必須です。 |

## <a name="receive-app-protection-policy"></a>アプリの保護ポリシーを受信する

### <a name="overview"></a>概要

Intune アプリの保護ポリシーを受信するには、アプリで Intune MAM サービスの登録要求を開始する必要があります。 アプリは、デバイス登録の有無を問わず、アプリの保護ポリシーを受信するように Intune コンソールで構成できます。 登録のないアプリ保護ポリシー (**APP-WE** または MAM-WE とも呼ばれる) では、デバイスが Intune モバイル デバイス管理 (MDM) に登録されていなくても Intune でアプリを管理できます。 いずれの場合も、ポリシーを受信するには、Intune MAM サービスへの登録が必須となります。

> [!Important]
> アプリ保護ポリシーによって暗号化が有効にされた場合、iOS 用 Intune App SDK では 256 ビットの暗号化キーが使用されます。 すべてのアプリでは、保護されたデータの共有を許可するために、最新の SDK バージョンが必要になります。

### <a name="apps-that-already-use-adal-or-msal"></a>ADAL または MSAL を既に使用しているアプリ

既に ADAL または MSAL を使用しているアプリの場合、ユーザーが正常に認証された後に、`IntuneMAMEnrollmentManager` インスタンスで `registerAndEnrollAccount` メソッドが呼び出されます。

```objc
/*
 *  This method will add the account to the list of registered accounts.
 *  An enrollment request will immediately be started.
 *  @param identity The UPN of the account to be registered with the SDK
 */

(void)registerAndEnrollAccount:(NSString *)identity;
```

`registerAndEnrollAccount` メソッドを呼び出すことにより、SDK はユーザー アカウントを登録し、このアカウントの代わりにアプリを登録しようとします。 何らかの理由で登録が失敗した場合、SDK は 24 時間後に自動的に登録を再試行します。 デバッグのため、アプリは登録要求の結果についての[通知](#status-result-and-debug-notifications)をデリゲート経由で受け取ることができます。

この API が呼び出された後、アプリは通常どおりに機能し続けることができます。 登録が成功した場合、SDK はアプリの再起動が必要であることをユーザーに通知します。 その時点で、ユーザーはすぐにアプリを再起動できます。

```objc
[[IntuneMAMEnrollmentManager instance] registerAndEnrollAccount:@”user@foo.com”];
```

### <a name="apps-that-do-not-use-adal-or-msal"></a>ADAL または MSAL を使用していないアプリ

ADAL または MSAL を使用してユーザーをサインインしないアプリでも、API を呼び出して SDK にその認証を処理させることにより、Intune MAM サービスからアプリ保護ポリシーを受け取ることができます。 Azure AD でユーザーを認証していないが、データを保護するためにアプリ保護ポリシーを受け取る必要がある場合は、アプリでこの手法を利用してください。 たとえば、別の認証サービスがアプリのサインインに使用されている場合やアプリがサインインにまったく対応していない場合です。 これを行うには、アプリケーションは `IntuneMAMEnrollmentManager` インスタンスの `loginAndEnrollAccount` メソッドを呼び出すことができます。

```objc
/**
 *  Creates an enrollment request which is started immediately.
 *  If no token can be retrieved for the identity, the user will be prompted
 *  to enter their credentials, after which enrollment will be retried.
 *  @param identity The UPN of the account to be logged in and enrolled.
 */
 (void)loginAndEnrollAccount: (NSString *)identity;
```

このメソッドを呼び出すと、既存のトークンが見つからない場合、SDK はユーザーに資格情報を求めます。 次に SDK は、提供されたユーザー アカウントの代わりに、アプリを Intune MAM サービスに登録しようとします。 このメソッドは ID に "nil" を指定して呼び出すことができます。 そうすると、SDK は、デバイス上の既存の管理されたユーザーで登録するか (MDM の場合)、または既存ユーザーが見つからない場合はユーザーにユーザー名の入力を求めます。

登録が失敗した場合、エラーの詳細によっては、アプリは後で再びこの API を呼び出す必要があります。 アプリは登録要求の結果についての[通知](#status-result-and-debug-notifications)をデリゲート経由で受け取ることができます。

この API が呼び出された後、アプリは通常どおりに機能し続けることができます。 登録が成功した場合、SDK はアプリの再起動が必要であることをユーザーに通知します。

例:

```objc
[[IntuneMAMEnrollmentManager instance] loginAndEnrollAccount:@”user@foo.com”];
```

### <a name="let-intune-handle-authentication-and-enrollment-at-launch"></a>Intune で起動時に認証と登録を処理できるようにする

Intune SDK で、アプリの起動が完了する前に ADAL/MSAL を使用するすべての認証と登録を処理する必要があり、アプリで常に APP ポリシーが必要な場合、`loginAndEnrollAccount` API を使用する必要はありません。 アプリの Info.plist の IntuneMAMSettings ディクショナリで以下の 2 つの設定を YES に設定するだけです。

設定  | Type  | 定義 |
--       |  --   |   --       |  
AutoEnrollOnLaunch| ブール型| 既存の管理対象の ID が検出され、それがまだ登録されていない場合、起動時に自動登録を試みるかどうかを指定します。 既定は [いいえ] です。 <br><br> 注:マネージド ID が検出されない場合、またはその ID に対する有効なトークンが ADAL/MSAL キャッシュ内に存在しない場合は、アプリで MAMPolicyRequired も [はい] に設定されていない限り、資格情報を求めるメッセージを表示することなく登録の試みは失敗します。 |
MAMPolicyRequired| ブール型| アプリに Intune アプリ保護ポリシーがない場合に、アプリの起動をブロックするかどうかを指定します。 既定は [いいえ] です。 <br><br> 注:MAMPolicyRequired を [はい] に設定した状態でアプリを App Store に送信することはできません。 MAMPolicyRequired を YES に設定した場合は、AutoEnrollOnLaunch も YES に設定する必要があります。 |

自分のアプリにこのオプションを選択する場合、登録した後にアプリを再起動する必要はありません。

### <a name="deregister-user-accounts"></a>ユーザー アカウントの登録を解除する

ユーザーがアプリからサインアウトする前に、アプリは SDK からユーザーを登録解除する必要があります。 これにより次のことが保証されます。

1. そのユーザーのアカウントに対して登録の再試行が行われなくなります。

2. アプリ保護ポリシーが削除されます。

3. アプリが選択的ワイプ (オプション) を開始すると、企業データはすべて削除されます。

ユーザーがサインアウトする前に、`IntuneMAMEnrollmentManager` インスタンスの次のメソッドがアプリによって呼び出される必要があります。

```objc
/*
 *  This method will remove the provided account from the list of
 *  registered accounts.  Once removed, if the account has enrolled
 *  the application, the account will be un-enrolled.
 *  @note In the case where an un-enroll is required, this method will block
 *  until the Intune APP AAD token is acquired, then return.  This method must be called before  
 *  the user is removed from the application (so that required AAD tokens are not purged
 *  before this method is called).
 *  @param identity The UPN of the account to be removed.
 *  @param doWipe   If YES, a selective wipe if the account is un-enrolled
 */
(void)deRegisterAndUnenrollAccount:(NSString *)identity withWipe:(BOOL)doWipe;
```

ユーザー アカウントの Azure AD トークンが削除される前に、このメソッドを呼び出す必要があります。 SDK はユーザーの代わりに、ユーザー アカウントの AAD トークンで Intune MAM サービスに対する特定の要求を行う必要があります。

アプリ自体がユーザーの企業データを削除する場合は、`doWipe` フラグを false に設定できます。 設定しない場合、アプリで SDK による選択的ワイプの開始が可能になります。 結果的に、アプリの選択的ワイプのデリゲートが呼び出されます。

例:

```objc
[[IntuneMAMEnrollmentManager instance] deRegisterAndUnenrollAccount:@”user@foo.com” withWipe:YES];
```

## <a name="status-result-and-debug-notifications"></a>状態、結果、およびデバッグ通知

アプリは、Intune MAM サービスに対する次の要求についての状態、結果、およびデバッグ通知を受け取ることができます。

* 登録要求
* ポリシー更新要求
* 登録解除要求

通知は、`IntuneMAMEnrollmentDelegate.h` にあるデリゲート メソッドを使用して取得できます。

```objc
/**
 *  Called when an enrollment request operation is completed.
 * @param status status object containing debug information
 */

(void)enrollmentRequestWithStatus:(IntuneMAMEnrollmentStatus *)status;

/**
 *  Called when a MAM policy request operation is completed.
 *  @param status status object containing debug information
 */
(void)policyRequestWithStatus:(IntuneMAMEnrollmentStatus *)status;

/**
 *  Called when a un-enroll request operation is completed.
 *  @Note: when a user is un-enrolled, the user is also de-registered with the SDK
 *  @param status status object containing debug information
 */

(void)unenrollRequestWithStatus:(IntuneMAMEnrollmentStatus *)status;
```

これらのデリゲート メソッドは、次の情報を含む `IntuneMAMEnrollmentStatus` オブジェクトを返します。

* 要求に関連付けられているアカウントの ID
* 要求の結果を示す状態コード
* エラー文字列とステータス コードの説明
* `NSError` オブジェクトです。 このオブジェクトは、返される可能性のある特定のステータス コードと共に `IntuneMAMEnrollmentStatus.h` で定義されています。

### <a name="sample-code"></a>サンプル コード

デリゲート メソッドの実装例を次に示します。

```objc
- (void)enrollmentRequestWithStatus:(IntuneMAMEnrollmentStatus*)status
{
    NSLog(@"enrollment result for identity %@ with status code %ld", status.identity, (unsigned long)status.statusCode);
    NSLog(@"Debug Message: %@", status.errorString);
}

- (void)policyRequestWithStatus:(IntuneMAMEnrollmentStatus*)status
{
    NSLog(@"policy check-in result for identity %@ with status code %ld", status.identity, (unsigned long)status.statusCode);
    NSLog(@"Debug Message: %@", status.errorString);
}

- (void)unenrollRequestWithStatus:(IntuneMAMEnrollmentStatus*)status
{
    NSLog(@"un-enroll result for identity %@ with status code %ld", status.identity, (unsigned long)status.statusCode);
    NSLog(@"Debug Message: %@", status.errorString);
}
```

## <a name="application-restart"></a>アプリケーションの再起動

アプリは、MAM ポリシーを初めて受け取ったときに、必要なフックを適用するために再起動する必要があります。 再起動が必要になった場合に、これをアプリに通知するメソッドは、`IntuneMAMPolicyDelegate.h` で SDK によりデリゲート メソッドが提供されます。

```objc
 - (BOOL) restartApplication
```

このメソッドの戻り値は SDK に、アプリケーションが必要な再起動を処理する必要があるかどうかを通知します。

* true が返された場合は、アプリケーションは再起動を処理する必要があります。

* false が返された場合は、SDK はこのメソッドから返った後でアプリケーションを再起動します。 SDK はすぐにダイアログ ボックスを表示し、アプリケーションを再起動するようにユーザーに通知します。

## <a name="customize-your-apps-behavior-with-apis"></a>API でアプリの動作をカスタマイズする

Intune App SDK にはいくつかの API が用意されています。これらを呼び出すことで、アプリに展開されている Intune APP ポリシーに関する情報を得ることができます。 このデータを使用して、アプリの動作をカスタマイズすることができます。 次の表では、使用するいくつかの重要な Intune クラスに関する情報を示しています。

インスタンス | [説明]
----- | -----------
IntuneMAMPolicyManager.h | IntuneMAMPolicyManager クラスでは、アプリケーションに展開された Intune APP ポリシーを公開します。 特に、[複数 ID を有効にする](app-sdk-ios.md#enable-multi-identity-optional)のに役立つ API を公開します。 |
IntuneMAMPolicy.h | IntuneMAMPolicy クラスでは、アプリに適用される MAM ポリシー設定を公開します。 これらのポリシー設定は公開されるため、アプリでその UI をカスタマイズできます。 ポリシー設定のほとんどは、アプリではなく、SDK によって適用されます。 アプリで実装する必要があるのは、名前を付けて保存のコントロールのみです。 このクラスでは、名前を付けて保存を実装する必要がある API を公開します。 |
IntuneMAMFileProtectionManager.h | IntuneMAMFileProtectionManager クラスでは、指定した ID に基づいてファイルとディレクトリを明示的にセキュリティで保護するために、アプリで使用できる API を公開します。 ID は Intune によって管理される場合と、管理されない場合があり、SDK で適切な MAM ポリシーが適用されます。 このクラスの使用は省略可能です。 |
IntuneMAMDataProtectionManager.h | IntuneMAMDataProtectionManager クラスでは、指定された ID を指定するデータ バッファーをセキュリティで保護するために、アプリで使用できる API を公開します。 ID は Intune によって管理される場合と、管理されない場合があり、SDK で暗号化が適切に適用されます。 |

## <a name="implement-save-as-and-open-from-controls"></a>save-as コントロールと open-from コントロールを実装する

Intune では、IT 管理者は、マネージド アプリでデータの保存先またはデータを開く場所として使用できるストレージの場所を選択できます。 アプリでは、`IntuneMAMPolicy.h` で定義されている `isSaveToAllowedForLocation` API を使用して、許可された save-to のストレージの場所を、Intune MAM SDK で照会することができます。 また、アプリでは、`IntuneMAMPolicy.h` で定義されている `isOpenFromAllowedForLocation` API を使用して、許可された open-from のストレージの場所を、Intune MAM SDK で照会することができます。

アプリでマネージド データをクラウドの記憶域またはローカルの場所に保存するには、`isSaveToAllowedForLocation` API を使用し、IT 管理者がその場所にデータを保存できるかどうかを確認する必要があります。
アプリでデータをクラウド ストレージまたはローカルの場所から開くには、`isOpenFromAllowedForLocation` API を確認して、IT 管理者がその場所からデータを開くことが許可されているかどうかを調べる必要があります。

アプリで `isSaveToAllowedForLocation` または `isOpenFromAllowedForLocation` API を使用する場合、ストレージの場所の UPN を渡す必要があります (使用可能な場合)。

### <a name="supported-save-locations"></a>サポートされている保存場所

`isSaveToAllowedForLocation` API は、`IntuneMAMPolicy.h` で定義されている次の場所にデータを保存することを IT 監理者が許可しているかどうかを確認するための定数を提供します。

* IntuneMAMSaveLocationOther
* IntuneMAMSaveLocationOneDriveForBusiness
* IntuneMAMSaveLocationSharePoint
* IntuneMAMSaveLocationLocalDrive
* IntuneMAMSaveLocationAccountDocument

アプリでは、`isSaveToAllowedForLocation` で定数を使用して、OneDrive for Business などの "マネージド" の場所、または "個人用" の場所にデータを保存できるかどうかを確認する必要があります。 さらに、アプリが場所について "管理対象" か "個人用" かを確認できない場合は、API を使用する必要があります。

アプリでデータをローカル デバイス上の任意の場所に保存する場合は、`IntuneMAMSaveLocationLocalDrive` 定数を使用する必要があります。

保存先の場所のアカウントが不明な場合は、`nil` を渡す必要があります。 `IntuneMAMSaveLocationLocalDrive` の場所は、常に `nil` アカウントとペアにする必要があります。

### <a name="supported-open-locations"></a>サポートされている開く場所

`isOpenFromAllowedForLocation` API では、`IntuneMAMPolicy.h` で定義されている次の場所からデータを開くことを IT 監理者が許可しているかどうかを確認するための定数が提供されます。

* IntuneMAMOpenLocationOther
* IntuneMAMOpenLocationOneDriveForBusiness
* IntuneMAMOpenLocationSharePoint
* IntuneMAMOpenLocationCamera
* IntuneMAMOpenLocationLocalStorage
* IntuneMAMOpenLocationAccountDocument

アプリでは、`isOpenFromAllowedForLocation` の定数を使用して、OneDrive for Business などの "マネージド" の場所、または "個人用" の場所からデータを開くことができるかどうかを確認する必要があります。 さらに、場所が "マネージド" か "個人用" かをアプリで確認できない場合は、API を使用する必要があります。

アプリでカメラまたはフォト アルバムからデータを開いているときは、`IntuneMAMOpenLocationCamera` 定数を使用する必要があります。

アプリでデータをローカル デバイス上の任意の場所から開く場合は、`IntuneMAMOpenLocationLocalStorage` 定数を使用する必要があります。

アプリでマネージド アカウント ID を持つドキュメントを開いている場合は、`IntuneMAMOpenLocationAccountDocument` 定数を使用する必要があります (後の「共有データ」セクションを参照)

開く元の場所のアカウントが不明な場合は、`nil` を渡す必要があります。 `IntuneMAMOpenLocationLocalStorage` と `IntuneMAMOpenLocationCamera` の場所は、常に `nil` アカウントとペアにする必要があります。

### <a name="unknown-or-unlisted-locations"></a>不明な場所または一覧にない場所

目的の場所が `IntuneMAMSaveLocation` または `IntuneMAMOpenLocation` の列挙型の一覧にない場合、または不明な場合は、2 つの場所のどちらかを使用する必要があります。
* 保存場所がマネージド アカウントでアクセスされている場合は、`IntuneMAMSaveLocationAccountDocument` の場所を使用する必要があります (開く場合は `IntuneMAMOpenLocationAccountDocument`)。
* それ以外の場合は、`IntuneMAMSaveLocationOther` の場所を使用します (開く場合は `IntuneMAMOpenLocationOther`)。

マネージド アカウントと、マネージド アカウントの UPN を共有するアカウントの区別を明確にすることが重要です。 たとえば、OneDrive にサインインしている UPN が "user@contoso.com" のマネージド アカウントは、Dropbox にサインインしている UPN が "user@contoso.com" のアカウントと同じではありません。 不明サービスまたは一覧にないサービスが、マネージド アカウントにサインインすることによってアクセスされた場合 (たとえば、OneDrive にサインインした "user@contoso.com")、`AccountDocument` の場所によって表される必要があります。 不明サービスまたは一覧にないサービスが別のアカウントを使用してサインインした場合は (たとえば、Dropbox にサインインした "user@contoso.com")、マネージド アカウントで場所にアクセスしていないので、`Other` の場所で表される必要があります。

### <a name="sharing-blocked-alert"></a>ブロックされたアラートの共有

`isSaveToAllowedForLocation` または `isOpenFromAllowedForLocation` API が呼び出されて、保存または開くアクションをブロックされた場合は、UI ヘルパー関数を使用できます。 アクションがブロックされたことをアプリでユーザーに通知する場合は、`IntuneMAMUIHelper.h` で定義されている `showSharingBlockedMessage` API を呼び出して、汎用メッセージを含むアラート ビューを提示できます。

## <a name="share-data-via-uiactivityviewcontroller"></a>UIActivityViewController によるデータの共有

リリース 8.0.2 以降、Intune App SDK では、Intune 管理対象の共有場所のみを選択できるように、`UIActivityViewController` アクションをフィルター処理できます。 この動作は、アプリケーション データ転送ポリシーによって制御されます。

### <a name="copy-to-actions"></a>‘コピー先’ アクション

`UIActivityViewController` と `UIDocumentInteractionController` で文書を共有するとき、iOS では、共有されている文書を開くことができるアプリケーションごとの ‘コピー先’ アクションが表示されます。 アプリケーションでは、その Info.plist の `CFBundleDocumentTypes` 設定を介してサポートされる文書の種類が宣言されます。 管理されていないアプリケーションとの共有がポリシーで禁止されている場合、この種類の共有は今後、利用できなくなります。 代わりに、ユーザーは非 UI の Action Extension をアプリケーションに追加し、Intune App SDK にリンクする必要があります。 Action Extension は単なるスタブです。 SDK では、ファイル共有動作が実装されます。 次の手順に従います。

1. アプリケーションの Info.plist `CFBundleURLTypes` に schemeURL が少なくとも 1 つ定義されている必要があります。

2. アプリケーションと Action Extension では少なくとも 1 つの App Group を共有する必要があります。App Group は、アプリと拡張 IntuneMAMSettings ディクショナリの下にある `AppGroupIdentifiers` 配列に一覧表示する必要があります。

3. Action Extension に “Open in” という名前を付け、名前の後ろにアプリケーション名を追加します。 必要に応じて、Info.plist をローカライズします。

4. [Apple の開発者向け文書](https://developer.apple.com/ios/human-interface-guidelines/extensions/sharing-and-actions/)の説明に基づいて拡張のテンプレート アイコンを提供します。 あるいは、IntuneMAMConfigurator ツールを使用し、アプリケーションの .app ディレクトリからこれらの画像を生成できます。 これを行うには、次を実行します。

    ```bash
    IntuneMAMConfigurator -generateOpenInIcons /path/to/app.app -o /path/to/output/directory
    ```

5. 拡張の Info.plist の IntuneMAMSettings で、`OpenInActionExtension` という名前のブール値設定を追加し、値を YES に設定します。

6. `com.microsoft.intune.mam` というプレフィックスの付いたアプリケーションの `CFBundleDocumentTypes` から単一ファイルとすべてのタイプをサポートするように、`NSExtensionActivationRule` を構成します。 たとえば、アプリケーションで public.text と public.image がサポートされている場合、アクティブ化ルールは次のようになります。

    ```objc
    SUBQUERY (
        extensionItems,
        $extensionItem,
        SUBQUERY (
            $extensionItem.attachments,
            $attachment,
            ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.text” ||
            ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.image”).@count == 1
    ).@count == 1
    ```

### <a name="update-existing-share-and-action-extensions"></a>既存の Share Extension と Action Extension の更新

アプリに Share Extension または Action Extension が既に含まれている場合、Intune タイプを許可するように `NSExtensionActivationRule` を修正する必要があります。 拡張でサポートされている種類ごとに、`com.microsoft.intune.mam` というプレフィックスの付いた種類を追加します。 たとえば、既存のアクティブ化ルールが次の場合、  

```objc
SUBQUERY (
    extensionItems,
    $extensionItem,
    SUBQUERY (
        $extensionItem.attachments,
        $attachment,
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.url" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.plain-text" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.image" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.data"
    ).@count > 0
).@count > 0
```

次のように変更します。

```objc
SUBQUERY (
    extensionItems,
    $extensionItem,
    SUBQUERY (
        $extensionItem.attachments,
        $attachment,
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.url" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.plain-text" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.image" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.data" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.url" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.plain-text" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.image" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.data"
    ).@count > 0
).@count > 0
```

> [!NOTE]
> IntuneMAMConfigurator ツールを使用し、Intune タイプをアクティブ化ルールに追加できます。 既存のアクティブ化ルールで事前定義された文字列定数が使用されている場合 (NSExtensionActivationSupportsFileWithMaxCount や NSExtensionActivationSupportsText など)、述語の構文がかなり複雑になることがあります。 IntuneMAMConfigurator ツールを使用すれば、Intune タイプを追加するとき、アクティブ化ルールを文字列定数から述語文字列に変更することもできます。

### <a name="what-the-ui-should-look-like"></a>UI の外観

従来の UI:

![データの共有 - iOS の従来の共有 UI](./media/app-sdk-ios/sharing-UI-old.png)

新しい UI:

![データの共有 - iOS の新しい共有 UI](./media/app-sdk-ios/sharing-UI-new.png)

## <a name="enable-targeted-configuration-appmam-app-config-for-your-ios-applications"></a>iOS アプリケーションに対して対象の構成 (APP/MAM アプリ構成) を有効にする

MAM 対象の構成 (MAM アプリ構成とも呼ばれる) により、アプリは Intune SDK から構成データを受け取ることができます。 このデータの形式とバリエーションは、アプリの所有者/開発者が定義して Intune のユーザーに通知する必要があります。

Intune の管理者は、Intune Azure portal と Intune Graph API を使って、構成データの対象設定と展開を行うことができます。 Intune App SDK for iOS の バージョン 7.0.1 以降では、MAM 対象構成に入っているアプリに MAM サービス経由で MAM 対象構成データを与えることができます。 アプリケーション構成データは、MDM チャネルではなく MAM サービスを通して直接アプリにプッシュされます。 Intune App SDK は、これらのコンソールから取得されたデータにアクセスするためのクラスを提供します。 次の項目が前提条件です。

* MAM 対象構成 UI にアクセスする前に、アプリを Intune MAM サービスに登録する必要があります。 詳細については、「[アプリの保護ポリシーを受信する](#receive-app-protection-policy)」を参照してください。

* アプリのソース ファイルに `IntuneMAMAppConfigManager.h` を追加します。

* `[[IntuneMAMAppConfigManager instance] appConfigForIdentity:]` を呼び出し、アプリ構成オブジェクトを取得します。

* `IntuneMAMAppConfig` オブジェクトで適切なセレクターを呼び出します。 たとえば、アプリケーションのキーが文字列の場合、`stringValueForKey` や `allStringsForKey` を使用します。 戻り値とエラー条件の詳細については、`IntuneMAMAppConfig.h` を参照してください。

Graph API の機能に関する詳細については、[Graph API のリファレンス](https://developer.microsoft.com/graph/docs/concepts/overview) ページを参照してください。

iOS で MAM 対象アプリ構成ポリシーを作成する方法については、「[iOS 用 Microsoft Intune アプリ構成ポリシーを使用する方法](../apps/app-configuration-policies-use-ios.md)」の MAM 対象アプリ構成セクションを参照してください。

## <a name="telemetry"></a>製品利用統計情報

iOS 用 Intune App SDK では、既定で、次のイベントのタイプに関する製品利用統計情報が収集されます。

* **アプリの起動**:Microsoft Intune が MAM 対応アプリの使用状況を管理タイプ別に確認するために役立ちます (MDM を使用した MAM、MDM 登録を使用しない MAM など)。

* **登録呼び出し**:Microsoft Intune がクライアント側から開始された登録呼び出しの成功率と他のパフォーマンス指標を確認するのに役立ちます。

* **Intune の操作**:問題の診断に役立て、Intune の機能を確認するために、Microsoft では Intune SDK の操作に関する情報を収集します。

> [!NOTE]
> モバイル アプリケーションから Intune App SDK の製品利用統計情報を Microsoft Intune に送信しない場合は、Intune App SDK 製品利用統計情報のキャプチャを無効にする必要があります。 IntuneMAMSettings ディクショナリで、プロパティ `MAMTelemetryDisabled` を [はい] に設定します。

## <a name="enable-multi-identity-optional"></a>複数 ID を有効にする (省略可能)

既定では、SDK はポリシーをアプリ全体に適用します。 複数 ID は、ID 別レベルでのポリシー適用を可能にする MAM の機能です。 これには、他の MAM 機能より多くのアプリの参加が必要です。

アプリは、アクティブな ID を変更するときにアプリ SDK に通知する必要があります。 また、SDK は ID の変更が必要なときにもアプリに通知します。 現時点では、サポートされる管理対象 ID は 1 つだけです。 ユーザーがデバイスまたはアプリを登録すると、SDK はこの ID を使用し、それをプライマリ管理対象 ID であると判断します。 アプリの他のユーザーは、無制限のポリシー設定を持つ管理対象外として扱われます。

ID は文字列として簡単に定義されることに注意してください。 ID の大文字と小文字は区別されません。 SDK に ID を要求すると返される ID は、大文字と小文字の使い分けが ID 設定時の本来のものと異なる可能性があります。

### <a name="identity-overview"></a>ID の概要

ID は、単にアカウントのユーザー名です (例: user@contoso.com)。 開発者は、次のレベルでアプリの ID を設定できます。

* **プロセス ID**:プロセス全体に通用する ID を設定します。これは主として単一 ID のアプリケーションに使用されます。 この ID は、すべてのタスク、ファイル、UI に適用されます。

* **UI ID**:切り取り/コピー/貼り付け、PIN、認証、データ共有など、メイン スレッドでの UI タスクに適用されるポリシーを決定します。 UI ID は、ファイル タスク (暗号化やバックアップなど) には適用されません。

* **スレッド ID**:現在のスレッドに適用されるポリシーに影響を与えます。 この ID は、すべてのタスク、ファイル、UI に適用されます。

ユーザーが管理されているかどうかにかかわらず、アプリは ID を適切に設定する役目を担います。

常に、すべてのスレッドは UI タスクとファイル タスクのための有効な ID を持っています。 これは、適用する必要があるポリシー (ある場合) を確認するために使用される ID です。 ID が "ID なし" の場合、またはユーザーが管理されていない場合は、ポリシーは適用されません。 次の図は、有効な ID がどのように特定されるかを示しています。

  ![Intune App SDK iOS:ID 決定のプロセス](./media/app-sdk-ios/ios-thread-identities.png)

### <a name="thread-queues"></a>スレッド キュー

アプリは、多くの場合、スレッド キューに対して非同期タスクと同期タスクをディスパッチします。 SDK は、Grand Central Dispatch (GCD) 呼び出しをインターセプトして、現在のスレッド ID をディスパッチされたタスクに関連付けます。 タスクの完了時に、SDK はスレッド ID をタスクに関連付けられた ID に一時的に変更し、タスクを完了してから、元のスレッド ID に戻します。


`NSOperationQueue` は GCD を基にして作成されているので、`NSOperations` はタスクが `NSOperationQueue` に追加されるときにスレッドの ID で実行されます。 GCD を直接使用してディスパッチされた `NSOperations` または関数も、実行時に現在のスレッド ID を変更できます。 この ID は、ディスパッチ スレッドから継承された ID をオーバーライドします。

### <a name="file-owner"></a>ファイルの所有者

SDK は、ローカル ファイル所有者の ID を追跡し、適宜、ポリシーを適用します。 ファイルの所有者は、ファイルが作成されるとき、またはファイルが切り捨てモードで開かれるときに、設定されます。 所有者は、タスクを実行するスレッドの有効なファイル タスク ID に設定されます。

または、アプリで `IntuneMAMFilePolicyManager` を使用してファイル所有者 ID を明示的に設定することもできます。 アプリでは、`IntuneMAMFilePolicyManager` を使用してファイルの所有者を取得し、ファイルの内容を表示する前に UI ID を設定することができます。

### <a name="shared-data"></a>共有データ

管理対象ユーザーと管理対象外ユーザーの両方のデータを含むファイルをアプリが作成する場合、管理対象ユーザーのデータの暗号化はアプリで行います。 `IntuneMAMDataProtectionManager` で `protect` API と `unprotect` API を利用し、データを暗号化できます。

`protect` メソッドに渡す ID は、管理対象ユーザーまたは管理対象外ユーザーのどちらでもかまいません。 ユーザーが管理されている場合、データは暗号化されます。 ユーザーが管理されていない場合は、ヘッダーがデータに追加されて ID はエンコードされますが、データは暗号化されません。 `protectionInfo` メソッドを使用し、データの所有者を取得できます。

### <a name="share-extensions"></a>共有拡張機能

アプリに共有拡張機能が含まれている場合、`IntuneMAMDataProtectionManager` の `protectionInfoForItemProvider` メソッドを使用して共有対象アイテムの所有者を取得できます。 共有対象アイテムがファイルの場合は、SDK がファイル所有者の設定を処理します。 共有対象アイテムがデータの場合、そのデータがファイルに保持される場合にファイル所有者を設定することとそのデータを UI に表示する前に `setUIPolicyIdentity` API を呼び出すことがアプリの役目になります。

### <a name="turn-on-multi-identity"></a>複数の ID を有効にする

既定では、アプリは単一 ID として見なされます。 SDK は、登録ユーザーにプロセス ID を設定します。 複数 ID のサポートを有効にするには、アプリの Info.plist ファイルの IntuneMAMSettings ディクショナリに名前が `MultiIdentity`、値が YES のブール型設定を追加します。

> [!NOTE]
> 複数 ID を有効にすると、プロセス ID、UI ID、スレッド ID は nil に設定されます。 これらを適切に設定する役目をアプリが担います。

### <a name="switch-identities"></a>ID を切り替える

* **アプリで開始する ID の切り替え**:

    複数 ID アプリは、起動時には、不明の管理対象外アカウントで実行されているものと見なされます。 条件付き起動 UI は実行せず、アプリに対してポリシーは適用されません。 ID を変更する必要があるときは常に、アプリが SDK に通知します。 通常、この処理は、アプリが特定のユーザー アカウントのデータを表示するときに行われます。

    たとえば、ユーザーがドキュメント、メールボックス、またはノートブックのタブを開こうとしたときなどです。 アプリは、ファイル、メールボックス、またはタブが実際に開かれる前に、SDK に通知する必要があります。 これを行うには、`IntuneMAMPolicyManager` の API `setUIPolicyIdentity` を使用します。 ユーザーが管理されているかどうかにかかわらず、この API を呼び出す必要があります。 ユーザーが管理されている場合、SDK は条件付き起動確認を行います (改造の検出、PIN、認証など)。

    ID 切り替えの結果は、完了ハンドラーを介して非同期的にアプリに返されます。 アプリは、ドキュメント、メールボックス、タブを開くのを、成功結果コードが返されるまで延期する必要があります。 ID の切り替えが失敗した場合、アプリはタスクをキャンセルする必要があります。

* **SDK によって開始される ID の切り替え**:

    SDK が特定の ID への切り替えをアプリに要求することが必要になる場合があります。 複数 ID アプリは、この要求を処理するために `IntuneMAMPolicyDelegate` の `identitySwitchRequired` メソッドを実装する必要があります。

    このメソッドが呼び出されるとき、指定された ID への切り替え要求をアプリが処理できる場合、アプリは `IntuneMAMAddIdentityResultSuccess` を完了ハンドラーに渡す必要があります。 ID の切り替えを処理できない場合、アプリは完了ハンドラーに `IntuneMAMAddIdentityResultFailed` を渡す必要があります。

    アプリは、この呼び出しに応答して `setUIPolicyIdentity` を呼び出す必要はありません。 アプリが管理されていないユーザー アカウントに切り替える必要がある場合は、`identitySwitchRequired` の呼び出しに空の文字列が渡されます。

* **選択的ワイプ**:

    アプリが選択的にワイプされる場合、SDK は `IntuneMAMPolicyDelegate` の `wipeDataForAccount` メソッドを呼び出します。 アプリは、指定されたユーザーのアカウントとそれに関連付けられているすべてのデータを削除する必要があります。 SDK は、ユーザーが所有するすべてのファイルを削除できます。アプリが `wipeDataForAccount` の呼び出しから FALSE を返した場合はすべてのファイルを削除します。

    このメソッドはバックグラウンド スレッドから呼び出されることに注意してください。 (アプリが FALSE を返す場合のファイルを除き) ユーザーのすべてのデータが削除されるまでアプリは値を返すことはできません。

## <a name="ios-best-practices"></a>iOS ベスト プラクティス

iOS 向けの開発に推奨されるベスト プラクティスを次に示します。

* iOS ファイル システムでは大文字と小文字が区別されます。 `libIntuneMAM.a` や `IntuneMAMResources.bundle` のようなファイル名で大文字/小文字の使い方が正しいことを確認します。

* Xcode で `libIntuneMAM.a` が見つからない場合は、リンカー検索パスにこのライブラリへのパスを追加して問題を解決できます。

## <a name="faqs"></a>よく寄せられる質問

### <a name="are-all-of-the-apis-addressable-through-native-swift-or-the-objective-c-and-swift-interoperability"></a>すべての API は、ネイティブ Swift または Objective-C と Swift の相互運用でアドレス可能ですか

Intune App SDK の API は、Objective-C でのみ使用でき、**ネイティブ** Swift はサポートしていません。 Objective-C との相互運用性が必要です。

### <a name="do-all-users-of-my-application-need-to-be-registered-with-the-app-we-service"></a>アプリケーションのすべてのユーザーを APP-WE サービスに登録する必要がありますか

いいえ。 実際には、Intune アプリ SDK に登録する必要があるのは職場または学校アカウントのみです。 アプリでは、職場または学校のコンテキストでアカウントが使用されるかどうかを判断する必要があります。

### <a name="what-about-users-that-have-already-signed-in-to-the-application-do-they-need-to-be-enrolled"></a>アプリケーションに既にサインインしているユーザーはどうなりますか 登録する必要がありますか

ユーザーが正常に認証されると、アプリによりユーザーが登録されます。 アプリケーションが MDM のない MAM 機能を使用する前に存在していた可能性がある既存のアカウントの登録もアプリケーションが行います。

これを行うには、アプリケーションは `registeredAccounts:` メソッドを使用する必要があります。 このメソッドは、Intune MAM サービスに登録されているすべてのアカウントを含む NSDictionary を返します。 アプリケーションの既存のアカウントがこの一覧に存在しない場合、アプリケーションは `registerAndEnrollAccount:` を使用してそれらのアカウントを登録する必要があります。

### <a name="how-often-does-the-sdk-retry-enrollments"></a>SDK はどのような頻度で登録を再試行しますか

SDK は、以前に失敗したすべての登録を 24 時間ごとに自動的に再試行します。 SDK はこれにより、ユーザーがアプリケーションにサインインした後でユーザーの組織が MAM を有効にしてあり、ユーザーが正常に登録してポリシーを受け取れるかどうかを確認します。

ユーザーがアプリケーションを正常に登録したことを検出した場合、SDK は再試行を停止します。 これは、アプリケーションを登録できるのは一度に 1 人のユーザーだけであるためです。 ユーザーが登録解除された場合、同じ 24 時間間隔で再試行が開始されます。

### <a name="why-does-the-user-need-to-be-deregistered"></a>ユーザーを登録解除する必要があるのはなぜですか

SDK は、次の操作をバックグラウンドで定期的に実行します。

* アプリケーションがまだ登録されていない場合、SDK は 24 時間ごとにリストにあるすべてのアカウントの登録を試みます。
* アプリケーションが登録されている場合は、SDK は 8 時間ごとに MAM ポリシーの更新を確認します。

ユーザーを登録解除すると、ユーザーがアプリケーションを使用しなくなり、そのユーザー アカウントに対する定期的イベントを SDK は停止できることが SDK に通知されます。 また、必要に応じて、アプリの登録解除と選択的ワイプもトリガーします。

### <a name="should-i-set-the-dowipe-flag-to-true-in-the-deregister-method"></a>登録解除メソッドでは doWipe フラグを true に設定する必要がありますか

このメソッドは、ユーザーがアプリケーションからサインアウトする前に呼び出す必要があります。  サインアウトの一環としてユーザーのデータがアプリケーションから削除される場合は、`doWipe` を false に設定できます。 ただし、アプリケーションがユーザーのデータを削除しない場合は、SDK がデータを削除できるように、`doWipe` を true に設定する必要があります。

### <a name="are-there-any-other-ways-that-an-application-can-be-un-enrolled"></a>アプリケーションを登録解除できる他の方法はありますか

はい。IT 管理者は選択的ワイプ コマンドをアプリケーションに送信できます。 このコマンドを送信すると、ユーザーは登録を解除されて、ユーザーのデータはワイプされます。 SDK は自動的にこのシナリオを処理し、登録解除デリゲート メソッドで通知を送信します。

### <a name="is-there-a-sample-app-that-demonstrates-how-to-integrate-the-sdk"></a>SDK を統合する方法を示すサンプル アプリはありますか

はい、ご利用いただけます。 最近、オープンソースのサンプル アプリ [Wagr for iOS](https://github.com/Microsoft/Wagr-Sample-Intune-iOS-App) を改良したばかりです。 Wagr は Intune App SDK を使用してアプリ保護ポリシーで使用できるようになりました。

### <a name="how-can-i-troubleshoot-my-app"></a>アプリをトラブルシューティングするにはどうすればよいですか

iOS 9.0.3 以降用の Intune SDK では、ポリシーをテストしてエラーをログに記録するために、モバイル アプリ内に診断コンソールを追加する機能がサポートされています。 `IntuneMAMDiagnosticConsole.h` で定義されている `IntuneMAMDiagnosticConsole` クラス インターフェイスを使用すると、開発者は Intune 診断コンソールを表示できます。 これにより、エンド ユーザーまたはテスト中の開発者は、Intune のログを収集して共有し、発生している問題の診断に役立てることができます。 この API は、インテグレーターに対してはオプションです。

## <a name="submit-your-app-to-the-app-store"></a>App Store にアプリを送信する

Intune App SDK の静的ライブラリおよびフレームワークのビルドはどちらもユニバーサル バイナリです。 これはデバイスとシミュレーターのすべてのアーキテクチャ用のコードが含まれていることを意味します。 Apple は、App Store に送信されたアプリにシミュレーターのコードが含まれていると、そのアプリを拒否します。 デバイス専用ビルドのスタティック ライブラリ用にコンパイルするとき、リンカーは自動的にシミュレーター コードを削除します。 以下の手順に従って、アプリ ストアにアプリをアップロードする前にすべてのシミュレーター コードが削除されていることを確認します。

1. `IntuneMAM.framework` がデスクトップにあることを確認します。

2. これらのコマンドを実行します。

    ```bash
    lipo ~/Desktop/IntuneMAM.framework/IntuneMAM -remove i386 -remove x86_64 -output ~/Desktop/IntuneMAM.device_only
    ```

    ```bash
    cp ~/Desktop/IntuneMAM.device_only ~/Desktop/IntuneMAM.framework/IntuneMAM
    ```

    最初のコマンドは、フレームワークの DYLIB ファイルからシミュレーター アーキテクチャを削除します。 2 番目のコマンドは、デバイス専用の DYLIB ファイルをフレームワークのディレクトリにコピーします。
