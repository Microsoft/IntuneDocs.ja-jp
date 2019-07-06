---
title: iOS 用 Microsoft Intune App SDK 開発者ガイド
description: iOS 用 Microsoft Intune App SDK を使用すると、ネイティブ iOS アプリに Intune アプリ保護ポリシー (APP ポリシーまたは MAM ポリシーともいう) を組み込むことができます。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/10/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 8e280d23-2a25-4a84-9bcb-210b30c63c0b
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9ec0ab28f2b32cf3c60d6d674cfac5a5b21d094d
ms.sourcegitcommit: cb4e71cd48311ea693001979ee59f621237a6e6f
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2019
ms.locfileid: "67558405"
---
# <a name="microsoft-intune-app-sdk-for-ios-developer-guide"></a>iOS 用 Microsoft Intune App SDK 開発者ガイド

> [!NOTE]
> [Intune App SDK ガイドの概要](app-sdk-get-started.md)に関する記事を読むことを検討してください。このガイドでは、サポートされる各プラットフォームで統合のための準備をする方法について説明しています。

iOS 用 Microsoft Intune App SDK を使用すると、ネイティブ iOS アプリに Intune アプリ保護ポリシー (APP ポリシーまたは MAM ポリシーともいう) を組み込むことができます。 MAM 対応のアプリケーションが Intune App SDK に統合されています。 Intune で積極的にアプリを管理している場合、IT 管理者はモバイル アプリにアプリ保護ポリシーを展開できます。

## <a name="prerequisites"></a>必要条件

* OS X 10.8.5 以降を実行していて、また Xcode 9 以降もインストールされている Mac OS コンピューターが必要になります。

* アプリは iOS 10 以降を対象としている必要があります。

* [iOS 用の Intune アプリ SDK のライセンス条項](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios/blob/master/Microsoft%20License%20Terms%20Intune%20App%20SDK%20for%20iOS.pdf)を読みます。 記録としてライセンス条項を印刷し、保管します。 iOS 用の Intune App SDK をダウンロードし、使用すると、このライセンス条項に同意したことになります。  本ライセンス条項に同意されない場合、本ソフトウェアを使用することはできません。

* [GitHub](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios) で iOS 用 Intune アプリ SDK のファイルをダウンロードします。

## <a name="whats-in-the-sdk-repository"></a>SDK リポジトリには

次のファイルを Swift コードが含まれていないか、10.2 より前の Xcode のバージョンでコンパイルされたアプリ/拡張機能に関連します。

* **IntuneMAM.framework**: Intune アプリ SDK フレームワーク。 このフレームワークは、Intune のクライアント アプリケーションの管理を有効にする、アプリ拡張/にリンクすることをお勧めします。 ただし、静的ライブラリのパフォーマンスの利点を好む開発者も可能性があります。 以下をご覧ください。

* **libIntuneMAM.a**: Intune アプリ SDK の静的ライブラリ。 開発者は、フレームワークではなくスタティック ライブラリをリンクすることができます。 スタティック ライブラリがビルド時にバイナリ アプリ/拡張に直接埋め込まれているために、スタティック ライブラリを使用するいくつかの起動時のパフォーマンスの利点があります。 ただし、アプリに統合することより複雑なプロセスです。 場合は、アプリに含まれるすべての拡張機能、スタティック ライブラリをアプリにリンクして、拡張機能と、アプリ バンドル サイズを大きく、スタティック ライブラリとしてに埋め込まれる各アプリ/拡張機能バイナリ。 フレームワークを使用して、アプリと拡張機能はアプリのサイズを小さくしてその結果、同じ Intune SDK バイナリを共有できます。

* **IntuneMAMResources.bundle**: SDK が依存するリソースが含まれているリソース バンドル。 リソース バンドルは、スタティック ライブラリ (libIntuneMAM.a) を統合することがアプリにのみ必要です。

次のファイルは、Swift コードを含むことが Xcode 10.2 + でコンパイルされたアプリ/拡張機能に関連します。

* **IntuneMAMSwift.framework**: The Intune アプリ SDK の Swift フレームワーク。 このフレームワークには、Api は、アプリを呼び出すためのすべてのヘッダーが含まれています。 アプリ/拡張機能に Intune のクライアント アプリケーションの管理を有効にするには、このフレームワークをリンクします。

* **IntuneMAMSwiftStub.framework**: The Intune App SDK Swift スタブ フレームワーク。 これは、アプリ/拡張機能にリンクする必要があります IntuneMAMSwift.framework の依存関係が必要です。


次のファイルがすべてのアプリ/拡張機能に関連します。

* **IntuneMAMConfigurator**: Intune 管理の必要な最低限の変更をアプリまたは拡張機能の Info.plist の構成に使用するツール。 アプリまたは拡張機能の機能によっては、Info.plist に追加の手動変更を加える必要があります。

* **ヘッダー**: パブリックな Intune アプリ SDK の API を表示します。 これらのヘッダーは、ので、フレームワークのいずれかを利用する開発者は、そのプロジェクトにヘッダーを手動で追加する必要はありません、IntuneMAM/IntuneMAMSwift フレームワーク内に含まれています。 リンク、スタティック ライブラリ (libIntuneMAM.a) を選択する開発者は、そのプロジェクトに手動でこれらのヘッダーを含める必要があります。

次のヘッダー ファイルには、Intune App SDK から開発者に提供されている API、データ型、プロトコルが含まれています。

    * IntuneMAMAppConfig.h
    * IntuneMAMAppConfigManager.h
    * IntuneMAMDataProtectionInfo.h
    * IntuneMAMDataProtectionManager.h
    * IntuneMAMDefs.h
    * IntuneMAMDiagnosticConsole.h
    * IntuneMAMEnrollmentDelegate.h
    * IntuneMAMEnrollmentManager.h
    * IntuneMAMEnrollmentStatus.h
    * IntuneMAMFileProtectionInfo.h
    * IntuneMAMFileProtectionManager.h
    * IntuneMAMLogger.h
    * IntuneMAMPolicy.h
    * IntuneMAMPolicyDelegate.h
    * IntuneMAMPolicyManager.h
    * IntuneMAMVersionInfo.h

開発者は、IntuneMAM.h をインポートするだけで、前のすべてのヘッダーの内容を使用可能にすることができます


## <a name="how-the-intune-app-sdk-works"></a>Intune アプリ SDK のしくみ

iOS 用 Intune アプリ SDK の目的は、最小限のコード変更で iOS アプリケーションに管理機能を追加することです。 コードの変更が少ないほど、市場投入までの時間が短くなりますが、モバイル アプリケーションの一貫性と安定性に影響を出ることはありません。


## <a name="build-the-sdk-into-your-mobile-app"></a>モバイル アプリとして SDK をビルドする

Intune App SDK を有効にするには、次の手順を実行します。

1. **オプション 1 - (推奨) Framework**: Xcode 10.2 + を使用しているアプリ/拡張機能には、Swift コードが含まれている場合は、リンク`IntuneMAMSwift.framework`と`IntuneMAMSwiftStub.framework`ターゲット: ドラッグ`IntuneMAMSwift.framework`と`IntuneMAMSwiftStub.framework`を**埋め込みバイナリ**プロジェクト ターゲットの一覧。

    それ以外の場合、リンク`IntuneMAM.framework`ターゲット: ドラッグ`IntuneMAM.framework`を**埋め込みバイナリ**プロジェクト ターゲットの一覧。

   > [!NOTE]
   > フレームワークを使用する場合は、アプリ ストアにアプリを送信する前に、ユニバーサル フレームワークからシミュレーター アーキテクチャを手動で除去する必要があります。 詳細については、「[iOS 用 Microsoft Intune App SDK 開発者ガイド](#submit-your-app-to-the-app-store)」を参照してください。

   **オプション 2 - スタティック ライブラリ**: このオプションは Swift コードが含まれていない、または Xcode でビルドされたアプリ/拡張機能の使用のみ < 10.2 します。 `libIntuneMAM.a` ライブラリにリンクします。 `libIntuneMAM.a` ライブラリをプロジェクト ターゲットの **[Linked Frameworks and Libraries]** (リンク先フレームワークおよびライブラリ) ボックスの一覧にドラッグします。

    ![Intune App SDK iOS: リンク先フレームワークおよびライブラリ](./media/intune-app-sdk-ios-linked-frameworks-and-libraries.png)

    `-force_load {PATH_TO_LIB}/libIntuneMAM.a` を次のいずれかに追加して、`{PATH_TO_LIB}` を Intune アプリ SDK の場所に置き換えます。
   * プロジェクトの `OTHER_LDFLAGS` ビルド構成設定。
   * Xcode UI の **[その他のリンカー フラグ]** 。

     > [!NOTE]
     > `PATH_TO_LIB` を検索するには、`libIntuneMAM.a` ファイルを選択し、 **[ファイル]** メニューの **[情報の取得]** を選択します。 **[Info]** (情報 ) ウィンドウの **[General]** (全般) セクションから、 **[Where]** (場所) 情報 (パス) をコピーして貼り付けます。

     **[ビルド フェーズ]** の **[Copy Bundle Resources]** (バンドル リソースのコピー) にあるリソース バンドルをドラッグして、`IntuneMAMResources.bundle` リソース バンドルをプロジェクトに追加します。

     ![Intune App SDK iOS: バンドル リソースのコピー](./media/intune-app-sdk-ios-copy-bundle-resources.png)
     
2. Swift からの Intune Api を呼び出す必要がある場合、アプリ/拡張機能を OBJECTIVE-C ブリッジ ヘッダーを使用して必要な Intune SDK のヘッダーをインポートする必要があります。 アプリ/拡張機能が既にを OBJECTIVE-C ブリッジ ヘッダーを含めない場合を使用していずれかを指定、`SWIFT_OBJC_BRIDGING_HEADER`ビルド構成設定または Xcode UI の**OBJECTIVE-C Bridging Header**フィールド。 ブリッジのヘッダーは、このようなものになります。

   ```objc
      #import <IntuneMAMSwift/IntuneMAM.h>
   ```
   
   これにより、Intune SDK のすべての Api 使用可能なすべてのソースの Swift ファイル全体でアプリ/拡張機能。 
   
    > [!NOTE]
    > * ブリッジ特定 Intune SDK のヘッダーだけ包括的 IntuneMAM.h ではなく、Swift にすることができます。
    > * 統合したら、フレームワークまたは静的ライブラリに応じて、ヘッダー ファイルへのパスが異なる場合があります。
    > * Intune SDK の Api で利用可能に Swift モジュールのインポート ステートメントを使用して (例: IntuneMAMSwift をインポート) は現在サポートされていません。 推奨される方法を OBJECTIVE-C ブリッジ ヘッダーを使用します。
    
3. 次の iOS フレームワークをプロジェクトに追加します。  
    * MessageUI.framework  
    * Security.framework  
    * MobileCoreServices.framework  
    * SystemConfiguration.framework  
    * libsqlite3.tbd  
    * libc++.tbd  
    * ImageIO.framework  
    * LocalAuthentication.framework  
    * AudioToolbox.framework  
    * QuartzCore.framework  
    * WebKit.framework

4. 各プロジェクト ターゲットの **[機能]** を選択し、 **[Keychain Sharing]** (キーチェーン共有) スイッチを有効にして、キーチェーン共有を有効にします (まだ有効になっていない場合)。 次の手順に進むには、キーチェーン共有が必要です。

   > [!NOTE]
   > プロビジョニング プロファイルで新しいキーチェーン共有値がサポートされている必要があります。 キーチェーン アクセス グループは、ワイルドカード文字をサポートする必要があります。 これを確認するには、テキスト エディターで .mobileprovision ファイルを開いて **keychain-access-groups** を検索し、ワイルドカード文字があることを確認します。 次に例を示します。
   >  ```xml
   >  <key>keychain-access-groups</key>
   >  <array>
   >  <string>YOURBUNDLESEEDID.*</string>
   >  </array>
   >  ```

5. キーチェーン共有を有効にした後、次の手順に従って、Intune App SDK がデータを格納する個別のアクセス グループを作成します。 キーチェーン アクセス グループを作成するには、UI を使用するか、権利ファイルを使用します。 キーチェーン アクセス グループを作成する UI を使用している場合、次の手順を実行してください。

     」を参照します。 モバイル アプリでキーチェーン アクセス グループが定義されていない場合は、アプリのバンドル ID を**最初**のグループとして追加します。
    
    b. 共有キーチェーン グループ `com.microsoft.intune.mam` を既存のアクセス グループに追加します。 Intune App SDK はこのアクセス グループを使用してデータを格納します。
    
    c. `com.microsoft.adalcache` を既存のアクセス グループに追加します。
    
        ![Intune App SDK iOS: keychain sharing](./media/intune-app-sdk-ios-keychain-sharing.png)
    
    d. 前に示したキーチェーン アクセス グループを作成する Xcode UI を使用するのではなく、権利ファイルを直接編集している場合、キーチェーン アクセス グループの先頭に `$(AppIdentifierPrefix)` を追加します (Xcode ではこの処理が自動的に行われます)。 次に例を示します。
    
        - `$(AppIdentifierPrefix)com.microsoft.intune.mam`
        - `$(AppIdentifierPrefix)com.microsoft.adalcache`
    
        > [!NOTE]
        > An entitlements file is an XML file that is unique to your mobile application. It is used to specify special permissions and capabilities in your iOS app. If your app did not previously have an entitlements file, enabling keychain sharing (step 3) should have caused Xcode to generate one for your app. Ensure the app's bundle ID is the first entry in the list.

6. アプリが `UIApplication canOpenURL` に渡す各プロトコルを、アプリの Info.plist ファイルの `LSApplicationQueriesSchemes` 配列に含めます。 次の手順に進む前に、変更内容を必ず保存してください。

7. アプリでまだ FaceID が使用されていない場合、既定のメッセージと共に [NSFaceIDUsageDescription Info.plist キー](https://developer.apple.com/library/archive/documentation/General/Reference/InfoPlistKeyReference/Articles/CocoaKeys.html#//apple_ref/doc/uid/TP40009251-SW75)が確実に構成されているようにします。 これは、iOS がアプリでの FaceID の用途をユーザーに通知するために必要です。 Intune アプリ保護ポリシー設定では、IT 管理者が構成している場合、アプリにアクセスするための手段として FaceID を使用することが許可されています。

8. [SDK のリポジトリ](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios)に含まれる IntuneMAMConfigurator ツールを使用して、アプリの Info.plist の構成を終了します。 このツールには、次の 3 つのパラメーターがあります。

   |プロパティ|使用方法|
   |---------------|--------------------------------|
   |- i |  `<Path to the input plist>` |
   |- e | `<Path to the entitlements file>` |
   |- o |  (省略可能) `<Path to the output plist>` |

"-o" パラメーターが指定されていない場合、入力ファイルはインプレースで変更されます。 このツールにはべき等性があるため、アプリの Info.plist や権利に変更が入った場合は再実行してください。 また、Intune SDK を更新する際は、ツールの最新バージョンをダウンロードして実行してください。これは、Info.plist の構成要件が、最新のリリースで変更されている場合があるためです。

## <a name="configure-azure-active-directory-authentication-library-adal"></a>Azure Active Directory Authentication Library (ADAL) の構成

Intune App SDK は、認証と条件に基づく起動シナリオに [Azure Active Directory Authentication Library](https://github.com/AzureAD/azure-activedirectory-library-for-objc) を使用しています。 また、デバイスを登録せずに管理するために MAM サービスにユーザー ID を登録する場合も、ADAL を利用します。

通常、ADAL では、アプリに付与されるトークンのセキュリティを保証するために、アプリを Azure Active Directory (AAD) に登録し、一意の ID (クライアント ID) と他の識別子を取得する必要があります。 Intune App SDK では、指定していない限り、Azure AD に接続するときに既定の登録値が使用されます。  

アプリでユーザーの認証に ADAL が使用している場合、アプリではその既存登録値を利用し、Intune App SDK 既定値をオーバーライドする必要があります。 これにより、ユーザーに認証が 2 回 (Intune App SDK で 1 回、アプリで 1 回) 求められることがなくなります。

アプリからは、マスター ブランチ上の[最新バージョンの ADAL](https://github.com/AzureAD/azure-activedirectory-library-for-objc/releases) にリンクすることをお勧めします。 現在、Intune App SDK では、条件付きアクセスを必要とするアプリをサポートするために、ADAL のブローカー ブランチが使用されています。 (したがって、このようなアプリは Microsoft Authenticator アプリに依存します。)ただし、SDK には ADAL のマスター ブランチとの互換性もまだあります。 アプリに適合するブランチを使用してください。

### <a name="link-to-adal-binaries"></a>ADAL バイナリへのリンク

以下の手順に従って、アプリを ADAL バイナリにリンクしてください。

1. GitHub から [Azure Active Directory Authentication Library (ADAL) for Objective-C](https://github.com/AzureAD/azure-activedirectory-library-for-objc) をダウンロードし、[手順](https://github.com/AzureAD/azure-activedirectory-library-for-objc#download)に従って、Git サブモジュールまたは CocoaPods を使用してダウンロードしてください。

2. ADAL フレームワーク (オプション 1)、またはスタティック ライブラリ (オプション 2) をプロジェクトに追加します。

3. アプリでキーチェーン アクセス グループが定義されていない場合は、アプリのバンドル ID を最初のグループとして追加します。

4. `com.microsoft.adalcache` をキーチェーン アクセス グループに追加することによって、ADAL シングル サインオン (SSO) を有効にします。

5. ADAL 共有キャッシュ キーチェーン グループを明示的に設定している場合は、`<appidprefix>.com.microsoft.adalcache` に設定されていることを確認します。 オーバーライドしない限り ADAL はこれを自動的に設定します。 カスタム キーチェーン グループを指定して `com.microsoft.adalcache` を置き換える場合は、Info.plist ファイルの IntuneMAMSettings でキー `ADALCacheKeychainGroupOverride` を使用して指定します。

### <a name="configure-adal-settings-for-the-intune-app-sdk"></a>Intune App SDK の ADAL 設定を構成する

アプリで既に認証用に ADAL を使用し、独自の ADAL 設定がある場合、Azure Active Directory に対して認証するときは同じ設定を使用するように Intune App SDK を強制することができます。 これで、アプリがユーザーに重複して認証を求めないようになります。 次の設定の構成については、「[Intune App SDK の設定を構成する](#configure-settings-for-the-intune-app-sdk)」を参照してください。  

* ADALClientId
* ADALAuthority
* ADALRedirectUri
* ADALRedirectScheme
* ADALCacheKeychainGroupOverride

アプリが既に ADAL を使用している場合、次の構成が必要です。

1. プロジェクトの Info.plist ファイルの **IntuneMAMSettings** ディクショナリで、キー名 `ADALClientId` を使用して、ADAL 呼び出しに使用するクライアント ID を指定します。

2. また、**IntuneMAMSettings** ディクショナリで、キー名 `ADALAuthority` を使用して Azure AD 機関を指定します。

3. さらに、**IntuneMAMSettings** ディクショナリで、キー名 `ADALRedirectUri` を使用して、ADAL 呼び出しに使用するリダイレクト URI を指定します。 また、アプリケーションのリダイレクト URI の形式が `scheme://bundle_id` の場合は、代わりに `ADALRedirectScheme` を指定することもできます。

さらに、アプリは、実行時にこれらの Azure AD 設定をオーバーライドすることができます。 上書きするには、`IntuneMAMPolicyManager` インスタンスの `aadAuthorityUriOverride`、`aadClientIdOverride`、および `aadRedirectUriOverride` プロパティを設定します。

4. iOS のアプリにアプリ保護ポリシー (APP) サービスへのアクセス許可を付与するための手順に従っていることを確認します。 [Intune SDK ガイドの概要](https://docs.microsoft.com/intune/app-sdk-get-started#next-steps-after-integration)に関するページ内の「Give your app access to the Intune app protection service (optional)」(Intune アプリ保護サービスへのアクセス権をアプリに付与する (省略可能)) の下に記載されている手順を使用します。  

> [!NOTE]
> Info.plist アプローチは、静的で、かつ実行時に定義する必要がないあらゆる設定に推奨されます。 `IntuneMAMPolicyManager` のプロパティに割り当てられた値は、Info.plist で指定された対応するどの値よりも優先され、アプリの再起動後も保持されます。 ユーザーの登録が解除されるまで、あるいは値が消去または変更されるまで、SDK は引き続きこの値を使用してポリシーのチェックインを行います。

### <a name="if-your-app-does-not-use-adal"></a>アプリが ADAL を使用していない場合

先に述べたように、Intune App SDK は、認証と条件に基づく起動シナリオに [Azure Active Directory 認証ライブラリ](https://github.com/AzureAD/azure-activedirectory-library-for-objc)を使用しています。 また、デバイスを登録しないで管理するために MAM サービスにユーザー ID を登録する場合も、ADAL を利用します。 **アプリがその認証メカニズムに ADAL を使用していない場合**、Intune App SDK が ADAL パラメーターの既定値を提供し、Azure AD に対する認証を処理します。 上記の ADAL 設定の値は指定する必要がありません。 アプリで使用されている認証メカニズムが存在する場合、それが ADAL のプロンプトの一番上に表示されます。 

## <a name="configure-settings-for-the-intune-app-sdk"></a>Intune App SDK の設定を構成する

アプリケーションの Info.plist ファイルの **IntuneMAMSettings** ディクショナリを使用し、Intune App SDK をセットアップして構成することができます。 IntuneMAMSettings ディクショナリが Info.plist ファイルに表示されない場合は、作成する必要があります。

IntuneMAMSettings ディクショナリの下に、次のサポートされる設定を使用して Intune App SDK を構成することができます。

これらの設定の一部は前のセクションで説明しています。一部の設定はすべてのアプリには適用されません。

Setting  | Type  | 定義 | 必須
--       |  --   |   --       |  --
ADALClientId  | 文字列型  | アプリの Azure AD クライアント識別子。 | アプリが ADAL を使用する場合に必要です。 |
ADALAuthority | 文字列型 | 使用されているアプリの Azure AD 機関。 AAD アカウントが構成されている独自の環境を使用する必要があります。 | アプリが ADAL を使用する場合に必要です。 この値が存在しない場合は、Intune の既定値が使用されます。|
ADALRedirectUri  | 文字列型  | アプリの Azure AD リダイレクト URI。 | アプリが ADAL を使用する場合は、ADALRedirectUri または ADALRedirectScheme が必要です。  |
ADALRedirectScheme  | 文字列型  | アプリの Azure AD リダイレクト スキーム。 アプリケーションのリダイレクト URI が `scheme://bundle_id` 形式の場合は、ADALRedirectUri の代わりにこれを使用できます。 | アプリが ADAL を使用する場合は、ADALRedirectUri または ADALRedirectScheme が必要です。 |
ADALLogOverrideDisabled | ブール型  | SDK がすべての ADAL ログ (アプリからの ADAL 呼び出しがある場合はこれを含む) をログ ファイルにルーティングするかどうかを指定します。 既定は [いいえ] です。 アプリで独自の ADAL ログ コールバックを設定する場合は [はい] に設定します。 | 任意。 |
ADALCacheKeychainGroupOverride | 文字列型  | "com.microsoft.adalcache" の代わりに ADAL キャッシュに使用するキーチェーン グループを指定します。 これにはアプリ ID プレフィックスは含まれないことに注意してください。 実行時に指定された文字列の前に付加されます。 | 任意。 |
AppGroupIdentifiers | 文字列配列  | アプリの権利 com.apple.security.application-groups セクションのアプリケーション グループの配列。 | アプリでアプリケーション グループを使用する場合は必須です。 |
ContainingAppBundleId | 文字列型 | アプリケーションを含む拡張機能のバンドル ID を指定します。 | iOS の拡張機能に必要です。 |
DebugSettingsEnabled| ブール型 | YES に設定すると、Settings バンドル内のテスト ポリシーを適用できます。 この設定を有効にしたままアプリケーションを出荷しては*なりません*。 | 任意。 既定値は [いいえ] です。|
MainNibFile <br> MainNibFile~ipad  | 文字列型  | この設定には、アプリケーションのメイン nib ファイル名を含める必要があります。  | アプリケーションの Info.plist で MainNibFile が定義されている場合は必須です。 |
MainStoryboardFile <br> MainStoryboardFile~ipad  | 文字列型  | この設定には、アプリケーションのメインのストーリーボードのファイル名を含める必要があります。 | アプリケーションの Info.plist で UIMainStoryboardFile が定義されている場合は必須です。 |
MAMPolicyRequired| ブール型| アプリに Intune APP ポリシーがない場合、アプリの起動をブロックするかどうかを指定します。 既定は [いいえ] です。 <br><br> 注: MAMPolicyRequired を YES に設定した状態でアプリを App Store に送信することはできません。 | 任意。 既定値は [いいえ] です。|
MAMPolicyWarnAbsent | ブール型| アプリに Intune APP ポリシーがない場合、アプリの起動時にユーザーに警告するかどうかを指定します。 <br><br> 注: ユーザーは警告を無視しても、ポリシーなしでアプリの使用が許可されます。 | 任意。 既定値は [いいえ] です。 |
MultiIdentity | ブール型| アプリが複数 ID 対応かどうかを指定します。 | 任意。 既定値は [いいえ] です。 |
SplashIconFile <br> SplashIconFile~ipad | 文字列型  | Intune スプラッシュ (起動) アイコン ファイルを指定します。 | 任意。 |
SplashDuration | 数値 | アプリケーションの起動時に Intune 起動画面が表示される最短時間 (秒)。 既定値は 1.5 です。 | 任意。 |
BackgroundColor| 文字列型| 起動画面と PIN 画面の背景色を指定します。 #XXXXXX の形式の 16 進 RGB 文字列を受け付けます。X には 0 ～ 9 または A ～ F を使用できます。 シャープ記号は省略してもかまいません。   | 任意。 既定値は明るい灰色です。 |
ForegroundColor| 文字列型| テキストの色など、起動画面と PIN 画面の前景色を指定します。 #XXXXXX の形式の 16 進 RGB 文字列を受け付けます。X には 0 ～ 9 または A ～ F を使用できます。 シャープ記号は省略してもかまいません。  | 任意。 既定値は黒です。 |
AccentColor | 文字列型| PIN 画面のアクセント カラーを指定します。ボタン テキストの色やボックスの強調表示色などです。 #XXXXXX の形式の 16 進 RGB 文字列を受け付けます。X には 0 ～ 9 または A ～ F を使用できます。 シャープ記号は省略してもかまいません。| 任意。 既定値はシステムの青です。 |
MAMTelemetryDisabled| ブール型| SDK に製品利用統計情報データをバックエンドに送信させないかどうかを指定します。| 任意。 既定値は [いいえ] です。 |
MAMTelemetryUsePPE | ブール型 | MAM SDK にデータを PPE テレメトリ バックエンドに送信させるかどうかを指定します。 テスト用テレメトリ データが顧客データと混ざらないように Intune ポリシーでアプリをテストするときに使用します。 | 任意。 既定値は [いいえ] です。 |
MaxFileProtectionLevel | 文字列型 | 任意。 アプリがサポートできる `NSFileProtectionType` の最大値を指定できるようにします。 レベルがアプリケーションによりサポートされるレベルよりも高い場合、この値がサービスによって送信されたポリシーをオーバーライドします。 有効値は、`NSFileProtectionComplete`、`NSFileProtectionCompleteUnlessOpen`、`NSFileProtectionCompleteUntilFirstUserAuthentication`、`NSFileProtectionNone` です。|
OpenInActionExtension | ブール型 | Open in Action 拡張を [はい] に設定します。 詳細については、「Sharing Data via UIActivityViewController」 (UIActivityViewController によるデータの共有) セクションを参照してください。 |
WebViewHandledURLSchemes | 文字列の配列 | アプリの WebView で処理する URL スキームを指定します。 | リンクや JavaScript で URL を処理する WebView をアプリが使用する場合は、必須です。 |

## <a name="receive-app-protection-policy"></a>アプリの保護ポリシーを受信する

### <a name="overview"></a>概要

Intune アプリの保護ポリシーを受信するには、アプリで Intune MAM サービスの登録要求を開始する必要があります。 アプリは、デバイス登録の有無を問わず、アプリの保護ポリシーを受信するように Intune コンソールで構成できます。 登録のないアプリ保護ポリシー (**APP-WE** または MAM-WE とも呼ばれる) では、デバイスが Intune モバイル デバイス管理 (MDM) に登録されていなくても Intune でアプリを管理できます。 いずれの場合も、ポリシーを受信するには、Intune MAM サービスへの登録が必須となります。

### <a name="apps-that-use-adal"></a>ADAL を使用するアプリ

既に ADAL を使用しているアプリの場合、ユーザーが正常に認証された後に、`IntuneMAMEnrollmentManager` インスタンスで `registerAndEnrollAccount` メソッドを呼び出します。

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

### <a name="apps-that-do-not-use-adal"></a>ADAL を使用していないアプリ

ADAL を使用してユーザーをサインインしないアプリでも、API を呼び出して SDK にその認証を処理させることにより、Intune MAM サービスからアプリ保護ポリシーを受け取ることができます。 Azure AD でユーザーを認証していないが、データを保護するためにアプリ保護ポリシーを受け取る必要がある場合は、アプリでこの手法を利用してください。 たとえば、別の認証サービスがアプリのサインインに使用されている場合やアプリがサインインにまったく対応していない場合です。 これを行うには、アプリケーションは `IntuneMAMEnrollmentManager` インスタンスの `loginAndEnrollAccount` メソッドを呼び出すことができます。

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

Intune SDK でアプリの起動が完了する前に ADAL を使用するすべての認証と登録を処理する必要があり、アプリで常に APP ポリシーが必要な場合、`loginAndEnrollAccount` API を使用する必要はありません。 アプリの Info.plist の IntuneMAMSettings ディクショナリで以下の 2 つの設定を YES に設定するだけです。

Setting  | Type  | 定義 |
--       |  --   |   --       |  
AutoEnrollOnLaunch| ブール型| 既存の管理対象の ID が検出され、それがまだ登録されていない場合、起動時に自動登録を試みるかどうかを指定します。 既定は [いいえ] です。 <br><br> 注意: マネージド ID が検出されない場合、またはその ID に対する有効なトークンが ADAL キャッシュ内に存在しない場合、アプリで MAMPolicyRequired も YES に設定されていなければ、資格情報を求めることなく登録の試みは失敗します。 |
MAMPolicyRequired| ブール型| アプリに Intune アプリ保護ポリシーがない場合に、アプリの起動をブロックするかどうかを指定します。 既定は [いいえ] です。 <br><br> 注: MAMPolicyRequired を YES に設定した状態でアプリを App Store に送信することはできません。 MAMPolicyRequired を YES に設定した場合は、AutoEnrollOnLaunch も YES に設定する必要があります。 |

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

> [!NOTE]
> この情報はデバッグ目的にのみ使用できます。 アプリのビジネス ロジックは、これらの通知に基づく必要はありません。 この情報は、デバッグまたは監視を目的としてテレメトリ サービスに送信できます。

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

インスタンス | 説明
----- | -----------
IntuneMAMPolicyManager.h | IntuneMAMPolicyManager クラスでは、アプリケーションに展開された Intune APP ポリシーを公開します。 特に、[複数 ID を有効にする](app-sdk-ios.md#enable-multi-identity-optional)のに役立つ API を公開します。 |
IntuneMAMPolicy.h | IntuneMAMPolicy クラスでは、アプリに適用される MAM ポリシー設定を公開します。 これらのポリシー設定は公開されるため、アプリでその UI をカスタマイズできます。 ポリシー設定のほとんどは、アプリではなく、SDK によって適用されます。 アプリで実装する必要があるのは、名前を付けて保存のコントロールのみです。 このクラスでは、名前を付けて保存を実装する必要がある API を公開します。 |
IntuneMAMFileProtectionManager.h | IntuneMAMFileProtectionManager クラスでは、指定した ID に基づいてファイルとディレクトリを明示的にセキュリティで保護するために、アプリで使用できる API を公開します。 ID は Intune によって管理される場合と、管理されない場合があり、SDK で適切な MAM ポリシーが適用されます。 このクラスの使用は省略可能です。 |
IntuneMAMDataProtectionManager.h | IntuneMAMDataProtectionManager クラスでは、指定された ID を指定するデータ バッファーをセキュリティで保護するために、アプリで使用できる API を公開します。 ID は Intune によって管理される場合と、管理されない場合があり、SDK で暗号化が適切に適用されます。 |

## <a name="implement-save-as-controls"></a>名前を付けて保存コントロールの実装

IT 管理者は Intune を使用して、管理対象アプリでのデータの保存先として利用可能な記憶域の場所を選択できます。 アプリでは、`IntuneMAMPolicy.h` で定義されている `isSaveToAllowedForLocation` API を使用して、許可された記憶域の場所を Intune App SDK に照会することができます。

アプリでマネージド データをクラウドの記憶域またはローカルの場所に保存するには、`isSaveToAllowedForLocation` API を使用し、IT 管理者がその場所にデータを保存できるかどうかを確認する必要があります。

アプリで `isSaveToAllowedForLocation` API を使用する場合、記憶域の場所の UPN を渡す必要があります (使用可能な場合)。

### <a name="supported-save-locations"></a>サポートされている保存場所

`isSaveToAllowedForLocation` API は、`IntuneMAMPolicy.h` で定義されている次の場所にデータを保存することを IT 監理者が許可しているかどうかを確認するための定数を提供します。

* IntuneMAMSaveLocationOther
* IntuneMAMSaveLocationOneDriveForBusiness
* IntuneMAMSaveLocationSharePoint
* IntuneMAMSaveLocationLocalDrive

アプリでは、`isSaveToAllowedForLocation` で定数を使用して、OneDrive for Business などの "マネージド" の場所、または "個人用" の場所にデータを保存できるかどうかを確認する必要があります。 さらに、アプリが場所について "管理対象" か "個人用" かを確認できない場合は、API を使用する必要があります。

"個人用" と認識される場所は、`IntuneMAMSaveLocationOther` 定数で表されます。

アプリでデータをローカル デバイス上の任意の場所に保存する場合は、`IntuneMAMSaveLocationLocalDrive` 定数を使用する必要があります。

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
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.data
    ).@count > 0
).@count > 0
```

> [!NOTE]
> IntuneMAMConfigurator ツールを使用し、Intune タイプをアクティブ化ルールに追加できます。 既存のアクティブ化ルールで事前定義された文字列定数が使用されている場合 (NSExtensionActivationSupportsFileWithMaxCount や NSExtensionActivationSupportsText など)、述語の構文がかなり複雑になることがあります。 IntuneMAMConfigurator ツールを使用すれば、Intune タイプを追加するとき、アクティブ化ルールを文字列定数から述語文字列に変更することもできます。

### <a name="what-the-ui-should-look-like"></a>UI の外観

従来の UI:

![データの共有 - iOS の従来の共有 UI](./media/sharing-UI-old.png)

新しい UI:

![データの共有 - iOS の新しい共有 UI](./media/sharing-UI-new.png)

## <a name="enable-targeted-configuration-appmam-app-config-for-your-ios-applications"></a>iOS アプリケーションに対して対象の構成 (APP/MAM アプリ構成) を有効にする

MAM 対象の構成 (MAM アプリ構成とも呼ばれる) により、アプリは Intune SDK から構成データを受け取ることができます。 このデータの形式とバリエーションは、アプリの所有者/開発者が定義して Intune のユーザーに通知する必要があります。

Intune の管理者は、Intune Azure portal と Intune Graph API を使って、構成データの対象設定と展開を行うことができます。 Intune App SDK for iOS の バージョン 7.0.1 以降では、MAM 対象構成に入っているアプリに MAM サービス経由で MAM 対象構成データを与えることができます。 アプリケーション構成データは、MDM チャネルではなく MAM サービスを通して直接アプリにプッシュされます。 Intune App SDK は、これらのコンソールから取得されたデータにアクセスするためのクラスを提供します。 次の項目が前提条件です。

* MAM 対象構成 UI にアクセスする前に、アプリを Intune MAM サービスに登録する必要があります。 詳細については、「[アプリの保護ポリシーを受信する](#receive-app-protection-policy)」を参照してください。

* アプリのソース ファイルに `IntuneMAMAppConfigManager.h` を追加します。

* `[[IntuneMAMAppConfigManager instance] appConfigForIdentity:]` を呼び出し、アプリ構成オブジェクトを取得します。

* `IntuneMAMAppConfig` オブジェクトで適切なセレクターを呼び出します。 たとえば、アプリケーションのキーが文字列の場合、`stringValueForKey` や `allStringsForKey` を使用します。 戻り値とエラー条件の詳細については、`IntuneMAMAppConfig.h` を参照してください。

Graph API の機能に関する詳細については、[Graph API のリファレンス](https://developer.microsoft.com/graph/docs/concepts/overview) ページを参照してください。

iOS で MAM 対象アプリ構成ポリシーを作成する方法については、「[iOS 用 Microsoft Intune アプリ構成ポリシーを使用する方法](https://docs.microsoft.com/intune/app-configuration-policies-use-ios)」の MAM 対象アプリ構成セクションを参照してください。

## <a name="telemetry"></a>製品利用統計情報

iOS 用 Intune App SDK では、既定で、次のイベントのタイプに関する製品利用統計情報が収集されます。

* **アプリの起動:** Microsoft Intune が MAM 対応アプリの使用状況を管理タイプ別に確認するために役立ちます (MDM を使用した MAM、MDM 登録を使用しない MAM など)。

* **登録呼び出し:** Microsoft Intune がクライアント側から開始された登録呼び出しの成功率と他のパフォーマンス指標を確認するのに役立ちます。

* **Intune の操作**: 問題の診断に役立て、Intune の機能を確認するために、Microsoft では Intune SDK の操作に関する情報を収集します。

> [!NOTE]
> モバイル アプリケーションから Intune App SDK の製品利用統計情報を Microsoft Intune に送信しない場合は、Intune App SDK 製品利用統計情報のキャプチャを無効にする必要があります。 IntuneMAMSettings ディクショナリで、プロパティ `MAMTelemetryDisabled` を [はい] に設定します。

## <a name="enable-multi-identity-optional"></a>複数 ID を有効にする (省略可能)

既定では、SDK はポリシーをアプリ全体に適用します。 複数 ID は、ID 別レベルでのポリシー適用を可能にする MAM の機能です。 これには、他の MAM 機能より多くのアプリの参加が必要です。

アプリは、アクティブな ID を変更するときにアプリ SDK に通知する必要があります。 また、SDK は ID の変更が必要なときにもアプリに通知します。 現時点では、サポートされる管理対象 ID は 1 つだけです。 ユーザーがデバイスまたはアプリを登録すると、SDK はこの ID を使用し、それをプライマリ管理対象 ID であると判断します。 アプリの他のユーザーは、無制限のポリシー設定を持つ管理対象外として扱われます。

ID は文字列として簡単に定義されることに注意してください。 ID の大文字と小文字は区別されません。 SDK に ID を要求すると返される ID は、大文字と小文字の使い分けが ID 設定時の本来のものと異なる可能性があります。

### <a name="identity-overview"></a>ID の概要

ID は、単にアカウントのユーザー名です (例: user@contoso.com)。 開発者は、次のレベルでアプリの ID を設定できます。

* **プロセス ID**: プロセス全体に通用する ID を設定し、主として単一の ID アプリケーションに使用されます。 この ID は、すべてのタスク、ファイル、UI に適用されます。

* **UI ID**: 切り取り/コピー/貼り付け、PIN、認証、データ共有など、メイン スレッドでの UI タスクに適用されるポリシーを決定します。 UI ID は、ファイル タスク (暗号化やバックアップなど) には適用されません。

* **スレッド ID**: 現在のスレッドに適用されるポリシーを決定します。 この ID は、すべてのタスク、ファイル、UI に適用されます。

ユーザーが管理されているかどうかにかかわらず、アプリは ID を適切に設定する役目を担います。

常に、すべてのスレッドは UI タスクとファイル タスクのための有効な ID を持っています。 これは、適用する必要があるポリシー (ある場合) を確認するために使用される ID です。 ID が "ID なし" の場合、またはユーザーが管理されていない場合は、ポリシーは適用されません。 次の図は、有効な ID がどのように特定されるかを示しています。

  ![Intune App SDK iOS: ID 決定のプロセス](./media/ios-thread-identities.png)

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

    たとえば、ユーザーがドキュメント、メールボックス、またはノートブックのタブを開こうとしたときなどです。 アプリは、ファイル、メールボックス、またはタブが実際に開かれる前に、SDK に通知する必要があります。 これを行うには、`IntuneMAMPolicyManager` の API `setUIPolicyIdentity` を使用します。 ユーザーが管理されているかどうかに関わらず、この API を呼び出す必要があります。 ユーザーが管理されている場合、SDK は条件付き起動確認を行います (改造の検出、PIN、認証など)。

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

### <a name="how-can-i-troubleshoot-my-app"></a>アプリをトラブルシューティングする方法は?

IOS 9.0.3+ 用 Intune SDK では、ポリシーのテストとエラーのログ記録用のモバイル アプリ内の診断コンソールに追加する機能をサポートします。 `IntuneMAMDiagnosticConsole.h` 定義、`IntuneMAMDiagnosticConsole`クラス インターフェイスは、開発者が Intune 診断コンソールの表示に使用できます。 エンドユーザーや開発者がテストを収集し、生じる可能性のある問題の診断に役立つ Intune ログを共有できます。 この API は、インテグレーターの省略可能です。

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
