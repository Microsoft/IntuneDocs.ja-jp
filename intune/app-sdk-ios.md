---
title: "iOS 用 Microsoft Intune App SDK 開発者ガイド"
description: "iOS 用 Microsoft Intune App SDK を使用すると、モバイル アプリ管理 (MAM) という形式で iOS アプリに Intune アプリ保護ポリシーを組み込むことができます。"
keywords: 
author: erikre
manager: angrobe
ms.author: erikre
ms.date: 11/10/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8e280d23-2a25-4a84-9bcb-210b30c63c0b
ms.reviewer: oydang
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 6ff0e98c710676c257822c14661e6908849ae053
ms.sourcegitcommit: 67ec0606c5440cffa7734f4eefeb7121e9d4f94f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="microsoft-intune-app-sdk-for-ios-developer-guide"></a>iOS 用 Microsoft Intune App SDK 開発者ガイド

> [!NOTE]
> 最初に、[Intune App SDK ガイドの概要](app-sdk-get-started.md)に関する記事に目を通すことをお勧めします。このガイドでは、サポートする各プラットフォームで統合のための準備をする方法について説明しています。

iOS 用 Microsoft Intune App SDK を使用すると、ネイティブ iOS アプリに Intune アプリ保護ポリシー (**APP** ポリシーまたは **MAM** ポリシーともいう) を組み込むことができます。 MAM 対応のアプリケーションが Intune App SDK に統合されています。 Intune で積極的にアプリを管理している場合、IT 管理者はモバイル アプリにアプリ保護ポリシーを展開できます。

## <a name="prerequisites"></a>必要条件

* OS X 10.8.5 以降を実行し、Xcode 8 以降がインストールされている Mac OS コンピューターが必要になります。

* アプリは iOS 9 以降を対象としている必要があります。

* [iOS 用の Intune アプリ SDK のライセンス条項](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios/blob/master/Microsoft%20License%20Terms%20Intune%20App%20SDK%20for%20iOS%20.pdf)を読みます。 記録用にライセンス条項を印刷し、保持します。 iOS 用の Intune App SDK をダウンロードし、使用すると、このライセンス条項に同意したことになります。  本ライセンス条項に同意されない場合、お客様は本ソフトウェアを使用できません。

* [GitHub](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios) で iOS 用 Intune アプリ SDK のファイルをダウンロードします。

## <a name="whats-in-the-sdk"></a>SDK の機能

iOS 用 Intune App SDK には、スタティック ライブラリ、リソース ファイル、API ヘッダー、デバッグ設定 plist ファイルおよび構成ツールが含まれています。 ほとんどのポリシー適用では、モバイル アプリに単にリソース ファイルを含め、ライブラリに静的にリンクできます。 高度な Intune MAM 機能は、API を介して適用されます。

このガイドでは、iOS 用 Intune App SDK の次のコンポーネントの使用方法について説明します。

* **libIntuneMAM.a**: Intune アプリ SDK の静的ライブラリ。 アプリで拡張機能を使用しない場合は、このライブラリをプロジェクトにリンクして、アプリで Intune モバイル アプリケーション管理を行えるようにします。

* **IntuneMAM.framework**: Intune アプリ SDK フレームワーク。 アプリで Intune モバイル アプリケーション管理を行えるようにするには、このフレームワークをプロジェクトにリンクします。 アプリで拡張機能を使用する場合は、静的ライブラリではなくフレームワークを使用して、プロジェクトが静的ライブラリの複数のコピーを作成しないようにします。

* **IntuneMAMResources.bundle**: SDK が依存するリソースが含まれているリソース バンドル。

* **ヘッダー**: Intune アプリ SDK の API を表示します。 API を使用する場合は、API を含むヘッダー ファイルをインクルードする必要があります。 次のヘッダー ファイルには、Intune App SDK から開発者に提供されている API、データ型、プロトコルが含まれています。

    * IntuneMAMAppConfig.h
    * IntuneMAMAppConfigManager.h
    * IntuneMAMDataProtectionInfo.h
    * IntuneMAMDataProtectionManager.h
    * IntuneMAMDefs.h
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
    
開発者は、IntuneMAM.h をインポートするだけで上記のすべてのヘッダーの内容が使用できるようにすることができます。


## <a name="how-the-intune-app-sdk-works"></a>Intune アプリ SDK のしくみ

iOS 用 Intune アプリ SDK の目的は、最小限のコード変更で iOS アプリケーションに管理機能を追加することです。 コードの変更が少ないほど、モバイル アプリケーションの一貫性と安定性に与える影響がなくなり、短期間で製品化できます。


## <a name="build-the-sdk-into-your-mobile-app"></a>モバイル アプリとして SDK をビルドする

Intune App SDK を有効にするには、次の手順を実行します。

1. **オプション 1 (推奨)**: `IntuneMAM.framework` をプロジェクトにリンクします。 プロジェクトのターゲットの **[Embedded Binaries]** (埋め込みバイナリ) の一覧に `IntuneMAM.framework` をドラッグします。

    > [!NOTE]
    > フレームワークを使用する場合は、アプリ ストアにアプリを送信する前に、ユニバーサル フレームワークからシミュレーター アーキテクチャを手動で除去する必要があります。 詳細については、「[iOS 用 Microsoft Intune App SDK 開発者ガイド](#Submit-your-app-to-the-App-Store)」を参照してください。

2. **オプション 2**: `libIntuneMAM.a` ライブラリにリンクします。 `libIntuneMAM.a` ライブラリをプロジェクト ターゲットの **[Linked Frameworks and Libraries]** (リンク先フレームワークおよびライブラリ) ボックスの一覧にドラッグします。

    ![Intune App SDK iOS: リンク先フレームワークおよびライブラリ](./media/intune-app-sdk-ios-linked-frameworks-and-libraries.png)

    `-force_load {PATH_TO_LIB}/libIntuneMAM.a` を次のいずれかに追加して、`{PATH_TO_LIB}` を Intune アプリ SDK の場所に置き換えます。
      * プロジェクトの `OTHER_LDFLAGS` ビルド構成設定
      * UI の **その他のリンカー フラグ**

        > [!NOTE]
        > `PATH_TO_LIB` を検索するには、`libIntuneMAM.a` ファイルを選択し、**[ファイル]** メニューの **[情報の取得]** を選択します。 **[Info]** (情報 ) ウィンドウの **[General]** (全般) セクションから、**[Where]** (場所) 情報 (パス) をコピーして貼り付けます。

    **[ビルド フェーズ]** の **[Copy Bundle Resources]** (バンドル リソースのコピー) にあるリソース バンドルをドラッグして、`IntuneMAMResources.bundle` リソース バンドルをプロジェクトに追加します。

    ![Intune App SDK iOS: バンドル リソースのコピー](./media/intune-app-sdk-ios-copy-bundle-resources.png)

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

4. モバイル アプリの Info.plist ファイルでメイン Nib またはストーリーボード ファイルが定義されている場合、**メイン ストーリーボード**または**メイン Nib** フィールドを切り取ります。 必要に応じて、Info.plist でこれらのフィールドと相当する値を **IntuneMAMSettings** という名前の新しいディクショナリの下に次のキー名で貼り付けます。
    * MainStoryboardFile
    * MainStoryboardFile~ipad
    * MainNibFile
    * MainNibFile~ipad
    > [!NOTE]
  > モバイル アプリの Info.plist ファイルでメイン nib またはストーリーボードが定義されない場合、これらの設定は不要です。

    (キー名を確認するために) Info.plist を未処理の形式で表示するには、ドキュメント本文の任意の場所を右クリックし、ビューの種類を **[Show Raw Keys/Values]** (生のキー/値の表示) に変更します。

5. 各プロジェクト ターゲットの **[機能]** を選択し、**[Keychain Sharing]** (キーチェーン共有) スイッチを有効にして、キーチェーン共有を有効にします (まだ有効になっていない場合)。 次の手順に進むには、キーチェーン共有が必要です。

  > [!NOTE]
    > プロビジョニング プロファイルで新しいキーチェーン共有値がサポートされている必要があります。 キーチェーン アクセス グループは、ワイルドカード文字をサポートする必要があります。 これを確認するには、テキスト エディターで .mobileprovision ファイルを開いて **keychain-access-groups** を検索し、ワイルド カードがあることを確認します。 たとえば、
    ```xml
    <key>keychain-access-groups</key>
    <array>
    <string>YOURBUNDLESEEDID.*</string>
    </array>
    ```

6. キーチェーン共有を有効にした後、次の手順に従って、Intune App SDK がデータを格納する個別のアクセス グループを作成します。 キーチェーン アクセス グループを作成するには、UI を使用するか、権利ファイルを使用します。 キーチェーン アクセス グループを作成する UI を使用している場合、次の手順を実行してください。

    1. モバイル アプリでキーチェーン アクセス グループが定義されていない場合は、アプリのバンドル ID を最初のグループとして追加します。

    2. 共有キーチェーン グループ `com.microsoft.intune.mam` を既存のアクセス グループに追加します。 Intune App SDK はこのアクセス グループを使用してデータを格納します。

    3. `com.microsoft.adalcache` を既存のアクセス グループに追加します。

        ![Intune App SDK iOS: キーチェーン共有](./media/intune-app-sdk-ios-keychain-sharing.png)

    4. 前に示したキーチェーン アクセス グループを作成する Xcode UI を使用するのではなく、権利ファイルを直接編集している場合、キーチェーン アクセス グループの先頭に `$(AppIdentifierPrefix)` を追加します (Xcode ではこの処理が自動的に行われます)。 たとえば、

            * `$(AppIdentifierPrefix)com.microsoft.intune.mam`
            * `$(AppIdentifierPrefix)com.microsoft.adalcache`

    > [!NOTE]
    > 権利ファイルとは、自分のモバイル アプリケーションに固有の XML ファイルです。 iOS アプリで特別なアクセス許可と機能を指定するために使用されます。 お使いのアプリにあらかじめ権利ファイルが無かった場合、キーチェーンの共有 (手順 6) を有効にすると Xcode によってアプリ用に権利ファイルが生成されます。

7. アプリの Info.plist ファイルで URL スキームが定義されている場合は、`-intunemam` サフィックスを指定して別のスキームを各 URL スキームに追加します。

8. アプリで、その Info.plist ファイルにドキュメント型が定義されている場合は、各アイテムの "ドキュメントのコンテンツ タイプの UTI" 配列の各文字列に "com.microsoft.intune.mam" プレフィックスの重複エントリを 追加します。

9. iOS 9 以降用に開発されたモバイル アプリの場合は、アプリが `UIApplication canOpenURL` に渡す各プロトコルを、アプリの Info.plist ファイルの `LSApplicationQueriesSchemes` 配列に含めます。 さらに、表示されているプロトコルごとに新しいプロトコルを追加し、それに `-intunemam` を付加します。 `http-intunemam`、`https-intunemam`、および `ms-outlook-intunemam` を配列に含める必要もあります。

10. アプリケの権利でアプリ グループが定義されている場合は、それらのグループを **IntuneMAMSettings** ディクショナリの `AppGroupIdentifiers` キーの下に文字列の配列として追加します。

## <a name="using-the-intune-mam-configurator-tool"></a>Intune MAM 構成ツールを使用する

SDK の手動統合に必要なすべての info.plist 操作が Intune MAM 構成ツールで処理されるようになりました。 Intune App SDK for iOS のリポジトリにあります。 マルチ ID、AAD 設定など、その他のアプリ固有の設定はこのツールでは処理されません。 このツールには 3 つのパラメーターが含まれています。
 
|プロパティ|使用方法|
|---------------|--------------------------------|
|- i |  `<Path to the input plist>` |
|- e | 権利ファイル |
|- o |  (省略可能) `<Path for the changed input plist>` |
    
Intune MAM 構成ツールは次の更新に利用できます。
* アプリのメイン ストーリーボード ファイルやメイン Nib ファイルを IntuneMAMSettings に更新します。
* Info.plist ファイルに定義されているアプリの URL スキームを、URL スキームごとに、-intunemam サフィックスで更新します。
* アプリでその Info.plist ファイルにドキュメント型が定義されている場合は、各アイテムの "ドキュメントのコンテンツ タイプの UTI" 配列の各文字列に "com.microsoft.intune.mam" プレフィックスの重複エントリを 追加します。
* アプリの権利でアプリ グループが定義されている場合は、それらのグループを IntuneMAMSettings ディクショナリの AppGroupIdentifiers キーの下に文字列の配列として追加します。
    
> [!Note]
> 手動の info.plist 操作ではなく、このツールを使用する場合は、アプリの info.plist か権利が変更されるたびに再実行することをお勧めします。

## <a name="configure-azure-active-directory-authentication-library-adal"></a>Azure Active Directory Authentication Library (ADAL) の構成

Intune App SDK は、認証と条件に基づく起動シナリオに [Azure Active Directory Authentication Library](https://github.com/AzureAD/azure-activedirectory-library-for-objc) を使用しています。 また、デバイスを登録しないで管理するために MAM サービスにユーザー ID を登録する場合も、ADAL を利用します。

通常、ADAL では、アプリに付与されるトークンのセキュリティを保証するために、アプリを Azure Active Directory (AAD) に登録し、一意の ID (クライアント ID) と他の識別子を取得する必要があります。 Intune App SDK では、指定していない限り、Azure AD に接続するときに既定の登録値が使用されます。  

アプリでユーザーの認証に ADAL が使用している場合、アプリではその既存登録値を利用し、Intune App SDK 既定値を上書きする必要があります。 これにより、ユーザーに認証が 2 回 (Intune App SDK で 1 回、アプリで 1 回) 求められることがなくなります。

### <a name="recommendations"></a>推奨事項

アプリからは、マスター ブランチ上の[最新バージョンの ADAL](https://github.com/AzureAD/azure-activedirectory-library-for-objc/releases) にリンクすることをお勧めします。 現在、Intune App SDK は、条件付きアクセスを必要とするアプリをサポートするために、ADAL のブローカー ブランチを使用しています。 (したがって、このようなアプリは Microsoft Authenticator アプリに依存します。)ただし、SDK には ADAL のマスター ブランチとの互換性もまだあります。 アプリに適合するブランチを使用します。

### <a name="link-to-adal-binaries"></a>ADAL バイナリへのリンク

以下の手順に従って、アプリを ADAL バイナリにリンクしてください。

1. GitHub から [Azure Active Directory Authentication Library (ADAL) for Objective-C](https://github.com/AzureAD/azure-activedirectory-library-for-objc) をダウンロードし、[手順](https://github.com/AzureAD/azure-activedirectory-library-for-objc/blob/master/README.md)に従って、Git サブモジュールまたは CocoaPods を使用してダウンロードしてください。

2. **[Build Phases]** (ビルド フェーズ) の **[Copy Bundle Resources]** (バンドル リソースのコピー) にあるリソース バンドルをドラッグして、`ADALiOSBundle.bundle` リソース バンドルをプロジェクトに含めます。

3. `-force_load {PATH_TO_LIB}/libADALiOS.a` をプロジェクトの `OTHER_LDFLAGS` ビルド構成設定または UI の **[Other Linker Flags]** (その他のリンカー フラグ) に追加します。 `PATH_TO_LIB` は、ADAL バイナリの場所に置き換える必要があります。



### <a name="share-the-adal-token-cache-with-other-apps-signed-with-the-same-provisioning-profile"></a>同じプロビジョニング プロファイルを使用して署名されている他のアプリと ADAL トークン キャッシュを共有する**

同じプロビジョニング プロファイルで署名されたアプリ間で ADAL トークンを共有する場合、以下の手順を実行します。

1. アプリでキーチェーン アクセス グループが定義されていない場合は、アプリのバンドル ID を最初のグループとして追加します。

2. キーチェーン権利に `com.microsoft.adalcache` および `com.microsoft.workplacejoin` アクセス グループを追加することによって、ADAL シングル サインオン (SSO) を有効にします。

3. ADAL 共有キャッシュ キーチェーン グループを明示的に設定している場合は、`<app_id_prefix>.com.microsoft.adalcache` に設定されていることを確認します。 上書きしない限り ADAL はこれを自動的に設定します。 カスタム キーチェーン グループを指定して `com.microsoft.adalcache` を置き換える場合は、Info.plist ファイルの IntuneMAMSettings でキー `ADALCacheKeychainGroupOverride` を使用して指定します。

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

3. さらに、**IntuneMAMSettings** ディクショナリで、キー名 `ADALRedirectUri` を使用して、ADAL 呼び出しに使用するリダイレクト URI を指定します。 アプリのリダイレクト URI の形式によっては、`ADALRedirectScheme` も指定する必要がある場合があります。


また、Azure AD 機関 URL を実行時に指定されるテナント固有の URL で上書きすることができます。 上書きするには、`IntuneMAMPolicyManager` インスタンスの `aadAuthorityUriOverride` プロパティを設定します。

> [!NOTE]
> AAD 機関 URL の設定は、[デバイス登録のない APP](#App-protection-policy-without-device-enrollment) で、アプリによってフェッチされる ADAL 更新トークンを SDK が再利用するために必要です。

この値をクリアまたは変更しない場合、SDK はポリシーの更新およびその後の登録要求に対して引き続きこの機関 URL を使用します。  したがって、管理対象ユーザーがアプリからサインアウトするときにこの値をクリアし、新しい管理対象ユーザーがサインインするときに値をリセットすることが重要です。

### <a name="if-your-app-does-not-use-adal"></a>アプリが ADAL を使用していない場合

アプリで ADAL を使用していない場合、Intune App SDK が ADAL パラメーターの既定値を提供し、Azure AD に対する認証を処理します。 上記の ADAL 設定の値は指定する必要がありません。

## <a name="app-protection-policy-without-device-enrollment"></a>デバイス登録が不要なアプリの保護ポリシー

### <a name="overview"></a>概要
デバイス登録のない Intune アプリ保護ポリシー (**APP-WE** または MAM-WE とも呼ばれる) では、デバイスが Intune モバイル デバイス管理 (MDM) に登録されていなくても Intune でアプリを管理できます。 この新しい機能をサポートするために、アプリを管理用のユーザー アカウントに登録する必要があります。 新しい API を使用するには、次の手順を実行します。

1. デバイス登録の有無にかかわらずアプリの管理をサポートする、Intune App SDK の最新リリースを使用します。

2. API を呼び出すすべてのファイルに IntuneMAMEnrollment.h を追加します。

### <a name="register-user-accounts"></a>ユーザー アカウントを登録する

指定されたユーザー アカウントの代わりにアプリが APP-WE サービスに登録されている場合、アプリは Intune サービスからアプリ保護ポリシーを受け取ることができます。 新しくサインインしたユーザーを SDK に登録するのはアプリの役目です。 新しいユーザー アカウントが認証された後、アプリは Headers/IntuneMAMEnrollment.h の `registerAndEnrollAccount` メソッドを呼び出す必要があります。

```objc
/**


 *  This method will add the account to the list of registered accounts.
 *  An enrollment request will immediately be started.
 *  @param identity The UPN of the account to be registered with the SDK
 */

(void)registerAndEnrollAccount:(NSString *)identity;

```
`registerAndEnrollAccount` メソッドを呼び出すことにより、SDK はユーザー アカウントを登録し、このアカウントの代わりにアプリを登録しようとします。 何らかの理由で登録が失敗した場合、SDK は 24 時間後に自動的に登録を再試行します。 デバッグのため、アプリは登録要求の結果についての通知をデリゲート経由で受け取ることができます。

この API が呼び出された後、アプリは通常どおりに機能し続けることができます。 登録が成功した場合、SDK はアプリの再起動が必要であることをユーザーに通知します。 その時点で、ユーザーはすぐにアプリを再起動できます。

### <a name="deregister-user-accounts"></a>ユーザー アカウントの登録を解除する

ユーザーがアプリからサインアウトする前に、アプリは SDK からユーザーを登録解除する必要があります。 これにより次のことが保証されます。

1. そのユーザーのアカウントに対して登録の再試行が行われなくなります。

2. アプリ保護ポリシーが削除されます。

3. アプリが選択的ワイプ (オプション) を開始すると、企業データはすべて削除されます。

ユーザーがサインアウトする前に、`Headers/IntuneMAMEnrollment.h` にある次の API がアプリによって呼び出される必要があります。

```objc
/*
 *  This method will remove the provided account from the list of
 *  registered accounts.  Once removed, if the account has enrolled
 *  the application, the account will be un-enrolled.
 *  @note In the case where an un-enroll is required, this method will block
 *  until the Intune MAM AAD token is acquired, then return.  This method must be called before  
 *  the user is removed from the application (so that required AAD tokens are not purged
 *  before this method is called).
 *  @param identity The UPN of the account to be removed.
 *  @param doWipe   If YES, a selective wipe if the account is un-enrolled
 */

(void)deRegisterAndUnenrollAccount:(NSString *)identity withWipe:(BOOL)doWipe;
```

ユーザー アカウントの Azure AD トークンが削除される前に、このメソッドを呼び出す必要があります。 SDK はユーザーの代わりに、ユーザー アカウントの AAD トークンで APP-WE サービスに対する特定の要求を行う必要があります。

アプリ自体がユーザーの企業データを削除する場合は、`doWipe` フラグを false に設定できます。 設定しない場合、SDK が選択的ワイプを開始することがアプリで可能になります。 結果的に、アプリの選択的ワイプのデリゲートが呼び出されます。

```objc
[[IntuneMAMEnrollmentManager instance] deRegisterAndUnenrollAccount:@”user@foo.com” withWipe:YES];
```

### <a name="apps-that-do-not-use-adal"></a>ADAL を使用していないアプリ

ADAL を使用してユーザーをサインインしないアプリでも、API を呼び出して SDK にその認証を処理させることにより、Intune サービスからアプリ保護ポリシーを受け取ることができます。 Azure AD でユーザーを認証していないが、データを保護するためにアプリ保護ポリシーを受け取る必要がある場合は、アプリでこの手法を利用してください。 たとえば、別の認証サービスがアプリのサインインに使用されている場合やアプリがサインインにまったく対応していない場合です。 これを行うには、アプリケーションで Headers/IntuneMAMEnrollment.h にある`loginAndEnrollAccount` メソッドを呼び出す必要があります。

```objc
/**
 *  Creates an enrollment request which is started immediately.
 *  If no token can be retrieved for the identity, the user will be prompted
 *  to enter their credentials, after which enrollment will be retried.
 *  @param identity The UPN of the account to be logged in and enrolled.
 */
 (void)loginAndEnrollAccount: (NSString *)identity;

```

このメソッドを呼び出すと、既存のトークンが見つからない場合、SDK はユーザーに資格情報を求めます。 次に SDK は、提供されたユーザー アカウントの代わりに、アプリを APP-WE サービスに登録しようとします。 このメソッドは ID に "nil" を指定して呼び出すことができます。 そうすると、SDK は、デバイス上の既存の管理されたユーザーで登録するか、または既存ユーザーが見つからない場合はユーザーにユーザー名の入力を求めます。

登録が失敗した場合、エラーの詳細によっては、アプリは後で再びこの API を呼び出す必要があります。 アプリは登録要求の結果についての[通知](#Status-result-and-debug-notifications)をデリゲート経由で受け取ることができます。

この API が呼び出された後、アプリは通常どおりに機能し続けることができます。 登録が成功した場合、SDK はアプリの再起動が必要であることをユーザーに通知します。

## <a name="status-result-and-debug-notifications"></a>状態、結果、およびデバッグ通知

アプリは、Intune MAM サービスに対する次の要求についての状態、結果、およびデバッグ通知を受け取ることができます。

 - 登録要求
 - ポリシー更新要求
 - 登録解除要求

通知は、`Headers/IntuneMAMEnrollmentDelegate.h` にあるデリゲート メソッドを使用して取得できます。

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

- 要求に関連付けられているアカウントの ID
- 要求の結果を示す状態コード
- エラー文字列とステータス コードの説明
- `NSError` オブジェクト

このオブジェクトは、返される可能性のある特定のステータス コードと共に `IntuneMAMEnrollmentStatus.h` で定義されています。


### <a name="sample-code"></a>サンプル コード

デリゲート メソッドの実装例を次に示します。

```objc
- (void)enrollmentRequestWithStatus:(IntuneMAMEnrollmentStatus *)status
{
    NSLog(@"enrollment result for identity %@ with status code %ld", status.identity, (unsigned long)status.statusCode);
    NSLog(@"Debug Message: %@", status.errorString);
}


- (void)policyRequestWithStatus:(IntuneMAMEnrollmentStatus *)status
{
    NSLog(@"policy check-in result for identity %@ with status code %ld", status.identity, (unsigned long)status.statusCode);
    NSLog(@"Debug Message: %@", status.errorString);
}

- (void)unenrollRequestWithStatus:(IntuneMAMEnrollmentStatus *)status
{
    NSLog(@"un-enroll result for identity %@ with status code %ld", status.identity, (unsigned long)status.statusCode);
    NSLog(@"Debug Message: %@", status.errorString);
}

```

## <a name="app-restart"></a>アプリの再起動

アプリはアプリ保護ポリシーを初めて受け取ったときに、必要なフックを適用するために再起動する必要があります。 再起動が必要になった場合に、これをアプリに通知するメソッドは、Headers/IntuneMAMPolicyDelegate.h で SDK によりデリゲート メソッドが提供されます。

```objc
 - (BOOL) restartApplication
```
このメソッドの戻り値は SDK に、アプリケーションが必要な再起動を処理する必要があるかどうかを通知します。   

 - true が返された場合は、アプリケーションは再起動を処理する必要があります。   

 - false が返された場合は、SDK はこのメソッドから返った後でアプリケーションを再起動します。 SDK はすぐにダイアログ ボックスを表示し、アプリケーションを再起動するようにユーザーに通知します。

## <a name="customize-your-apps-behavior"></a>アプリの動作をカスタマイズする

Intune App SDK にはいくつかの API が用意されています。これらを呼び出すことで、アプリに展開されている Intune アプリ保護ポリシーに関する情報を得ることができます。 このデータを使用して、アプリの動作をカスタマイズすることができます。 アプリ保護ポリシーのほとんどの設定は、アプリケーションではなく、SDK で自動的に適用されます。 アプリで実装する必要がある設定は、名前を付けて保存のコントロールのみです。

### <a name="get-app-protection-policy"></a>アプリ保護ポリシーを取得する

#### <a name="intunemampolicymanagerh"></a>IntuneMAMPolicyManager.h
IntuneMAMPolicyManager クラスでは、アプリケーションに展開された Intune アプリ保護ポリシーを公開します。 特に、[複数 ID を有効にする](#-enable-multi-identity-optional)のに役立つ API を公開します。

#### <a name="intunemampolicyh"></a>IntuneMAMPolicy.h
IntuneMAMPolicy クラスでは、アプリケーションに展開された Intune アプリ保護ポリシーを公開します。 このクラスで公開されるほとんどのポリシー設定は SDK で適用されますが、ポリシー設定の適用方法に基づいて、アプリの動作をいつでもカスタマイズすることができます。

このクラスでは、名前を付けて保存コントロールの実装に必要ないくつかの API を公開します。これについては、次のセクションで詳しく説明します。

### <a name="implement-save-as-controls"></a>名前を付けて保存コントロールの実装

IT 管理者は Intune を使用して、管理対象アプリでのデータの保存先として利用可能な記憶域の場所を選択できます。 アプリでは **isSaveToAllowedForLocation** API を使用して、**IntuneMAMPolicy.h** で定義されている、許可された記憶域の場所を Intune App SDK に照会することができます。

アプリで管理対象データをクラウドの記憶域またはローカルの場所に保存するには、**isSaveToAllowedForLocation** API を使用し、IT 管理者がその場所にデータを保存できるかどうかを確認する必要があります。

アプリで **isSaveToAllowedForLocation** API を使用する場合、記憶域の場所の UPN を渡す必要があります (使用可能な場合)。

#### <a name="supported-save-locations"></a>サポートされている保存場所

**isSaveToAllowedForLocation** API は、IntuneMAMPolicy.h で定義されている次の場所にデータを保存することを IT 監理者が許可しているかどうかを確認するための定数を提供します。

* IntuneMAMSaveLocationOther
* IntuneMAMSaveLocationOneDriveForBusiness
* IntuneMAMSaveLocationSharePoint
* IntuneMAMSaveLocationLocalDrive

アプリでは、**isSaveToAllowedForLocation** API で定数を使用して、OneDrive for Business などの "管理対象" の場所、または "個人用" の場所にデータを保存できるかどうかを確認する必要があります。 さらに、アプリが場所について "管理対象" か "個人用" かを確認できない場合は、API を使用する必要があります。

"個人用" と認識される場所は、`IntuneMAMSaveLocationOther` 定数で表されます。

アプリでデータをローカル デバイス上の任意の場所に保存する場合は、`IntuneMAMSaveLocationLocalDrive` 定数を使用する必要があります。

## <a name="configure-settings-for-the-intune-app-sdk"></a>Intune App SDK の設定を構成する

アプリケーションの Info.plist ファイルの **IntuneMAMSettings** ディクショナリを使用し、Intune App SDK をセットアップして構成することができます。 IntuneMAMSettings ディクショナリが Info.plist file に表示されない場合は、アプリの Info.plist に "IntuneMAMSettings" の名前でディクショナリを作成する必要があります。

IntuneMAMSettings ディクショナリの下に、構成設定のキー列/値列を追加して SDK を構成することができます。 サポートされているすべての設定の一覧を次の表に示します。

これらの設定の一部は前のセクションで説明しています。一部の設定はすべてのアプリには適用されません。

Setting  | 型  | 定義 | 必須
--       |  --   |   --       |  --
ADALClientId  | 文字列型  | アプリの Azure AD クライアント識別子。 | アプリが ADAL を使用する場合に必要です。 |
ADALAuthority | 文字列型 | 使用されているアプリの Azure AD 機関。 AAD アカウントが構成されている独自の環境を使用する必要があります。 | アプリが ADAL を使用する場合に必要です。 この値が存在しない場合は、Intune の既定値が使用されます。|
ADALRedirectUri  | 文字列型  | アプリの Azure AD リダイレクト URI。 | アプリが ADAL を使用する場合は、ADALRedirectUri または ADALRedirectScheme が必要です。  |
ADALRedirectScheme  | 文字列型  | アプリの Azure AD リダイレクト スキーム。 アプリケーションのリダイレクト URI が `scheme://bundle_id` 形式の場合は、ADALRedirectUri の代わりにこれを使用できます。 | アプリが ADAL を使用する場合は、ADALRedirectUri または ADALRedirectScheme が必要です。 |
ADALLogOverrideDisabled | ブール型  | SDK がすべての ADAL ログ (アプリからの ADAL 呼び出しがある場合はこれを含む) をログ ファイルにルーティングするかどうかを指定します。 既定は [いいえ] です。 アプリで独自の ADAL ログ コールバックを設定する場合は [はい] に設定します。 | 任意。 |
ADALCacheKeychainGroupOverride | 文字列型  | "com.microsoft.adalcache" の代わりに ADAL キャッシュに使用するキーチェーン グループを指定します。 これにはアプリ ID プレフィックスは含まれないことに注意してください。 実行時に指定された文字列の前に付加されます。 | 任意。 |
AppGroupIdentifiers | 文字列の配列  | アプリの権利 com.apple.security.application-groups セクションのアプリケーション グループの配列。 | アプリでアプリケーション グループを使用する場合は必須です。 |
ContainingAppBundleId | 文字列型 | アプリケーションを含む拡張機能のバンドル ID を指定します。 | iOS の拡張機能に必要です。 |
DebugSettingsEnabled| ブール型 | YES に設定すると、Settings バンドル内のテスト ポリシーを適用できます。 この設定を有効にしたままアプリケーションを出荷しては*なりません*。 | 任意。 |
MainNibFile<br>MainNibFile~ipad  | 文字列型  | この設定には、アプリケーションのメイン nib ファイル名を含める必要があります。  | アプリケーションの Info.plist で MainNibFile が定義されている場合は必須です。 |
MainStoryboardFile<br>MainStoryboardFile~ipad  | 文字列型  | この設定には、アプリケーションのメインのストーリーボードのファイル名を含める必要があります。 | アプリケーションの Info.plist で UIMainStoryboardFile が定義されている場合は必須です。 |
AutoEnrollOnLaunch| ブール型| 既存の管理対象の ID が検出され、それがまだ登録されていない場合、起動時に自動登録を試みるかどうかを指定します。 既定は [いいえ] です。 <br><br> 注意: 管理対象の ID が検出されない場合、またはその ID に対する有効なトークンが ADAL キャッシュ内に存在しない場合、アプリで MAMPolicyRequired も YES に設定されていなければ、資格情報を求めることなく登録の試みは失敗します。 | 任意。 |
MAMPolicyRequired| ブール型| アプリに Intune アプリ保護ポリシーがない場合に、アプリの起動をブロックするかどうかを指定します。 既定は [いいえ] です。 <br><br> 注: MAMPolicyRequired を YES にした状態でアプリを App Store に送信することはできません。 MAMPolicyRequired を YES に設定した場合は、AutoEnrollOnLaunch も YES に設定する必要があります。 | 任意。 |
MAMPolicyWarnAbsent | ブール型| アプリに Intune アプリ保護ポリシーがない場合に、アプリの起動時にユーザーに警告するかどうかを指定します。 <br><br> 注: ユーザーは警告を無視しても、ポリシーなしでアプリの使用が許可されます。 | 任意。 |
MultiIdentity | ブール型| アプリが複数 ID 対応かどうかを指定します。 | 任意。 |
SplashIconFile <br>SplashIconFile~ipad | 文字列型  | Intune スプラッシュ (起動) アイコン ファイルを指定します。 | 任意。 |
SplashDuration | 数値 | アプリケーションの起動時に Intune 起動画面が表示される最短時間 (秒)。 既定値は 1.5 です。 | 任意。 |
BackgroundColor| 文字列型| 起動画面と PIN 画面の背景色を指定します。 #XXXXXX の形式の 16 進 RGB 文字列を受け付けます。X には 0 ～ 9 または A ～ F を使用できます。 シャープ記号は省略してもかまいません。   | 任意。 既定値は明るい灰色です。 |
ForegroundColor| 文字列型| テキストの色など、起動画面と PIN 画面の前景色を指定します。 #XXXXXX の形式の 16 進 RGB 文字列を受け付けます。X には 0 ～ 9 または A ～ F を使用できます。 シャープ記号は省略してもかまいません。  | 任意。 既定値は黒です。 |
AccentColor | 文字列型| PIN 画面のアクセント カラーを指定します。ボタン テキストの色やボックスの強調表示色などです。 #XXXXXX の形式の 16 進 RGB 文字列を受け付けます。X には 0 ～ 9 または A ～ F を使用できます。 シャープ記号は省略してもかまいません。| 任意。 既定値はシステムの青です。 |
MAMTelemetryDisabled| ブール型| SDK に製品利用統計情報データをバックエンドに送信させないかどうかを指定します。| 任意。 |
WebViewHandledURLSchemes | 文字列の配列 | アプリの WebView で処理する URL スキームを指定します。 | リンクや JavaScript で URL を処理する WebView をアプリが使用する場合は、必須です。 |  

> [!NOTE]
> アプリが App Store にリリースされる場合は、App Store の標準に従って、`MAMPolicyRequired` を "NO" に設定する必要があります。

## <a name="enabling-mam-targeted-configuration-for-your-ios-applications"></a>iOS アプリケーションの MAM 対象の構成を有効にする
MAM 対象の構成により、アプリは Intune App SDK から構成データを受け取ることができます。 このデータの形式とバリエーションは、アプリケーションの所有者/開発者が定義して Intune のユーザーに通知する必要があります。 Intune の管理者は、Intune Azure Portal を使って、構成データの対象設定と展開を行うことができます。 Intune App SDK for iOS (v 7.0.1) の一部として、MAM 対象構成に入っているアプリに MAM サービス経由で MAM 対象構成データを与えることができます。 アプリケーション構成データは、MDM チャネルではなく MAM サービスを通して直接アプリにプッシュされます。 Intune App SDK は、これらのコンソールから取得されたデータにアクセスするためのクラスを提供します。 次を前提条件として考慮してください。 <br>
* MAM 対象構成 UI にアクセスする前に、アプリを MAM-WE 登録する必要があります。 MAM-WE に関する詳細については、Intune App SDK ガイドの「[デバイス登録が不要なアプリの保護ポリシー](https://docs.microsoft.com/en-us/intune/app-sdk-ios#app-protection-policy-without-device-enrollment)」を参照してください。
* アプリのソース ファイルに ```IntuneMAMAppConfigManager.h``` を追加します。
* ```[[IntuneMAMAppConfig instance] appConfigForIdentity:]``` を呼び出し、アプリ構成オブジェクトを取得します。
* ```IntuneMAMAppConfig``` オブジェクトで適切なセレクターを呼び出します。 たとえば、アプリケーションのキーが文字列の場合、```stringValueForKey``` や ```allStringsForKey``` を使用します。 ```IntuneMAMAppConfig.h header``` ファイルには、戻り値/エラー条件が記載されています。

MAM 対象の構成値に関する Graph API の機能について詳しくは、[Graph API リファレンスの MAM 対象の構成](https://graph.microsoft.io/en-us/docs/api-reference/beta/api/intune_mam_targetedmanagedappconfiguration_create)に関するページをご覧ください。 <br>

iOS で MAM 対象アプリ構成ポリシーを作成する方法については、「[iOS 用 Microsoft Intune アプリ構成ポリシーを使用する方法](https://docs.microsoft.com/en-us/intune/app-configuration-policies-use-ios)」の MAM 対象アプリ構成セクションを参照してください。

## <a name="telemetry"></a>製品利用統計情報

iOS 用 Intune App SDK では、既定で、次の使用状況イベントに関する製品利用統計情報がログに記録されます。 このデータは、Microsoft Intune に送信されます。

* **アプリの起動:** Microsoft Intune が MAM 対応アプリの使用状況を管理タイプ別に確認するために役立ちます (MDM を使用した MAM、MDM 登録を使用しない MAM など)。

* **登録呼び出し:** Microsoft Intune がクライアント側から開始された登録呼び出しの成功率と他のパフォーマンス指標を確認するのに役立ちます。

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

  ![Intune App SDK iOS: リンク先フレームワークおよびライブラリ](./media/ios-thread-identities.png)

### <a name="thread-queues"></a>スレッド キュー

アプリは、多くの場合、スレッド キューに対して非同期タスクと同期タスクをディスパッチします。 SDK は、Grand Central Dispatch (GCD) 呼び出しをインターセプトして、現在のスレッド ID をディスパッチされたタスクに関連付けます。 タスクの完了時に、SDK はスレッド ID をタスクに関連付けられた ID に一時的に変更し、タスクを完了してから、元のスレッド ID に戻します。


`NSOperationQueue` は GCD を基にして作成されているので、`NSOperations` はタスクが `NSOperationQueue` に追加されるときにスレッドの ID で実行されます。 GCD を直接使用してディスパッチされた `NSOperations` または関数も、実行時に現在のスレッド ID を変更できます。 この ID は、ディスパッチ スレッドから継承された ID を上書きします。

### <a name="file-owner"></a>ファイルの所有者

SDK は、ローカル ファイル所有者の ID を追跡し、適宜、ポリシーを適用します。 ファイルの所有者は、ファイルが作成されるとき、またはファイルが切り捨てモードで開かれるときに、設定されます。 所有者は、タスクを実行するスレッドの有効なファイル タスク ID に設定されます。

または、アプリで `IntuneMAMFilePolicyManager` を使用してファイル所有者 ID を明示的に設定することもできます。 アプリでは、`IntuneMAMFilePolicyManager` を使用してファイルの所有者を取得し、ファイルの内容を表示する前に UI ID を設定することができます。

### <a name="shared-data"></a>共有データ

管理対象ユーザーと管理対象外ユーザーの両方のデータを含むファイルをアプリが作成する場合、管理対象ユーザーのデータの暗号化はアプリで行います。 `IntuneMAMDataProtectionManager` で `protect` API と `unprotect` API を利用し、データを暗号化できます。

`protect` メソッドに渡す ID は、管理対象ユーザーまたは管理対象外ユーザーのどちらでもかまいません。 ユーザーが管理されている場合、データは暗号化されます。 ユーザーが管理されていない場合は、ヘッダーがデータに追加されて ID はエンコードされますが、データは暗号化されません。 `protectionInfo` メソッドを使用し、データの所有者を取得できます。

### <a name="share-extensions"></a>共有拡張機能

アプリに共有拡張機能が含まれている場合、`IntuneMAMDataProtectionManager` の `protectionInfoForItemProvider` メソッドを使用して共有対象アイテムの所有者を取得できます。 共有対象アイテムがファイルの場合は、SDK がファイル所有者の設定を処理します。 共有対象アイテムがデータの場合、そのデータがファイルに保持される場合にファイル所有者を設定することとそのデータを UI に表示する前に `setUIPolicyIdentity` API を呼び出すことがアプリの役目になります。

### <a name="turning-on-multi-identity"></a>複数の ID を有効にする

既定では、アプリは単一 ID として見なされます。 SDK は、登録ユーザーにプロセス ID を設定します。 複数 ID のサポートを有効にするには、アプリの Info.plist ファイルの IntuneMAMSettings ディクショナリに名前が `MultiIdentity`、値が YES のブール型設定を追加します。

> [!NOTE]
> 複数 ID を有効にすると、プロセス ID、UI ID、スレッド ID は nil に設定されます。 これらを適切に設定する役目をアプリが担います。

### <a name="switching-identities"></a>ID の切り替え

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

## <a name="test-app-protection-policy-settings-in-xcode"></a>Xcode のアプリ保護ポリシー設定をテストする

運用環境で Intune 対応アプリを手動でテストする前に、Xcode で Settings.bundle ファイルを使用できます。 この方法で、Intune に接続することなく、アプリの保護ポリシーを設定し、テストすることができます。

### <a name="enable-policy-testing"></a>ポリシー テストを有効にする

以下の手順を実行し、Xcode でポリシー テストを有効にします。

1. この操作は、デバッグ ビルドで実行してください。 プロジェクトの最上位フォルダーを右クリックして Settings.bundle ファイルを追加します。 メニューから **[追加]**、**[新しいファイル]** を選択します。 **[リソース]** の下で、**[設定バンドル]** テンプレートを選択します。

2.  次のブロックをデバッグ ビルドの Settings.bundle/**Root.plist** ファイルにコピーします。
    ```xml
    <key>PreferenceSpecifiers</key>
    <array>
        <dict>
            <key>Type</key>
            <string>PSChildPaneSpecifier</string>
            <key>Title</key>
            <string>MDM Debug Settings</string>
            <key>Key</key>
            <string>MAMDebugSettings</string>
            <key>File</key>
            <string>MAMDebugSettings</string>
        </dict>
    </array>
    ```

3. アプリの Info.plist の **IntuneMAMSettings** ディクショナリで、"DebugSettingsEnabled" というブール値を追加します。 DebugSettingsEnabled の値を "YES" に設定します。



### <a name="app-protection-policy-settings"></a>アプリ保護ポリシー設定

以下の表は、MAMDebugSettings.plist を使用してテストできるアプリ保護ポリシー設定についてまとめた一覧です。 設定を有効にするには、MAMDebugSettings.plist に追加してください。

| ポリシー設定の名前 | 説明 | 設定可能な値 |
| -- | -- | -- |
| AccessRecheckOfflineTimeout | 認証が有効な場合に、アプリがオフラインになって Intune がアプリの起動や再開をブロックできる期間 (分) | 0 よりも大きい任意の整数 |
|   AccessRecheckOnlineTimeout | 起動または再開時に、ユーザーが PIN または認証情報の入力を求められるまでに、アプリを起動できる分数 (アクセスに認証または PIN が有効な場合)。 | 0 よりも大きい任意の整数 |
| AppSharingFromLevel | このアプリがデータを受け取ることができることを示します。 | 0 = |
## <a name="ios-best-practices"></a>iOS ベスト プラクティス

iOS 向けの開発に推奨されるベスト プラクティスを次に示します。

* iOS ファイル システムでは大文字と小文字が区別されます。 `libIntuneMAM.a` や `IntuneMAMResources.bundle` のようなファイル名で大文字/小文字の使い方が正しいことを確認します。

* Xcode で `libIntuneMAM.a` が見つからない場合は、リンカー検索パスにこのライブラリへのパスを追加して問題を解決できます。

## <a name="faqs"></a>よく寄せられる質問


**すべての API は、ネイティブ Swift または Objective-C と Swift の相互運用でアドレス可能ですか。**

Intune App SDK の API は、Objective-C でのみ使用でき、**ネイティブ** Swift はサポートしていません。 Objective-C との相互運用性が必要です。


**アプリケーションのすべてのユーザーを APP-WE サービスに登録する必要がありますか。**

いいえ。 実際には、Intune アプリ SDK に登録する必要があるのは職場または学校アカウントのみです。 アプリでは、職場または学校のコンテキストでアカウントが使用されるかどうかを判断する必要があります。   

**アプリケーションに既にサインインしているユーザーはどうなりますか?登録する必要がありますか。**

ユーザーが正常に認証されると、アプリによりユーザーが登録されます。 アプリケーションが MDM のない MAM 機能を使用する前に存在していた可能性がある既存のアカウントの登録もアプリケーションが行います。   

これを行うには、アプリケーションは `registeredAccounts:` メソッドを使用する必要があります。 このメソッドは、Intune MAM サービスに登録されているすべてのアカウントを含む NSDictionary を返します。 アプリケーションの既存のアカウントがこの一覧に存在しない場合、アプリケーションは `registerAndEnrollAccount:` を使用してそれらのアカウントを登録する必要があります。

**SDK はどのような頻度で登録を再試行しますか。**

SDK は、以前に失敗したすべての登録を 24 時間ごとに自動的に再試行します。 SDK はこれにより、ユーザーがアプリケーションにサインインした後でユーザーの組織が MAM を有効にしてあり、ユーザーが正常に登録してポリシーを受け取れるかどうかを確認します。

ユーザーがアプリケーションを正常に登録したことを検出した場合、SDK は再試行を停止します。 これは、アプリケーションを登録できるのは一度に 1 人のユーザーだけであるためです。 ユーザーが登録解除された場合、同じ 24 時間間隔で再試行が開始されます。

**ユーザーを登録解除する必要があるのはなぜですか?**

SDK は、次の操作をバックグラウンドで定期的に実行します。

 - アプリケーションがまだ登録されていない場合、SDK は 24 時間ごとにリストにあるすべてのアカウントの登録を試みます。
 - アプリケーションが登録されている場合、SDK は 8 時間ごとにアプリ保護ポリシーの更新を確認します。

ユーザーを登録解除すると、ユーザーがアプリケーションを使用しなくなり、そのユーザー アカウントに対する定期的イベントを SDK は停止できることが SDK に通知されます。 また、必要に応じて、アプリの登録解除と選択的ワイプもトリガーします。

**登録解除メソッドでは doWipe フラグを true に設定する必要がありますか。**

このメソッドは、ユーザーがアプリケーションからサインアウトする前に呼び出す必要があります。  サインアウトの一環としてユーザーのデータがアプリケーションから削除される場合は、`doWipe` を false に設定できます。 ただし、アプリケーションがユーザーのデータを削除しない場合は、SDK がデータを削除できるように、`doWipe` を true に設定する必要があります。

**アプリケーションを登録解除できる他の方法はありますか。**

はい。IT 管理者は選択的ワイプ コマンドをアプリケーションに送信できます。 このコマンドを送信すると、ユーザーは登録を解除されて、ユーザーのデータはワイプされます。 SDK は自動的にこのシナリオを処理し、登録解除デリゲート メソッドで通知を送信します。



## <a name="submit-your-app-to-the-app-store"></a>App Store にアプリを送信する

Intune App SDK の静的ライブラリおよびフレームワークのビルドはどちらもユニバーサル バイナリです。 これはデバイスとシミュレーターのすべてのアーキテクチャ用のコードが含まれていることを意味します。 Apple は、App Store に送信されたアプリにシミュレーターのコードが含まれていると、そのアプリを拒否します。 デバイス専用ビルドの静的ライブラリ用にコンパイルするとき、リンカーは自動的にシミュレーター コードを削除します。 以下の手順に従って、アプリ ストアにアプリをアップロードする前にすべてのシミュレーター コードが削除されていることを確認します。

1. `IntuneMAM.framework` がデスクトップにあることを確認します。

2. これらのコマンドを実行します。

    ```bash
    lipo ~/Desktop/IntuneMAM.framework/IntuneMAM -remove i386 -remove x86_64 -output ~/Desktop/IntuneMAM.device_only
    ```

    ```bash
    cp ~/Desktop/IntuneMAM.device_only ~/Desktop/IntuneMAM.framework/IntuneMAM
    ```
    最初のコマンドは、フレームワークの DYLIB ファイルからシミュレーター アーキテクチャを削除します。 2 番目のコマンドは、デバイス専用の DYLIB ファイルをフレームワークのディレクトリにコピーします。
