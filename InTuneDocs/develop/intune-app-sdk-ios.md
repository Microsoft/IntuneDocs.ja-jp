---
title: "iOS 用 Microsoft Intune アプリ SDK 開発者ガイド | Microsoft Intune"
description: 
keywords: 
author: Msmbaldwin
manager: jeffgilb
ms.date: 09/08/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8e280d23-2a25-4a84-9bcb-210b30c63c0b
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 975708b5204ab83108a9174083bb87dfeb04a063
ms.openlocfilehash: 52ad28686fa279a7ec251d073283c3554d1c81fc


---

# iOS 用 Microsoft Intune アプリ SDK 開発者ガイド

> [!NOTE]
> 最初に、「[Intune アプリ SDK の概要ガイド](intune-app-sdk-get-started.md)」に目を通すことをお勧めします。このガイドでは、サポートする各プラットフォームで統合のための準備をする方法について説明しています。* 

iOS 用 Microsoft Intune アプリ SDK を使用すると、iOS アプリに Intune モバイル アプリ管理 (MAM) を組み込むことができます。 MAM 対応アプリケーションは Intune アプリ SDK に統合され、これにより IT 管理者は、Intune によってアプリをアクティブに管理する場合にモバイル アプリにポリシーを展開できます。


# SDK の機能 

iOS 用 Intune アプリ SDK には、スタティック ライブラリ、リソース ファイル、API ヘッダー、デバッグ設定 plist および構成ツールが含まれています。 ほとんどのポリシー適用では、モバイル アプリに単にリソース ファイルを含め、ライブラリに静的にリンクできます。 高度な Intune MAM 機能は、API を介して適用されます。

このガイドでは、iOS 用 Intune アプリ SDK の次のコンポーネントの使用方法について説明します。

* **libIntuneMAM.a**: Intune アプリ SDK の静的ライブラリ。 アプリで拡張機能を使用しない場合は、このライブラリをプロジェクトにリンクして、アプリで Intune モバイル アプリケーション管理を行えるようにします。 手順については、「Intune アプリ SDK を使用したアプリのビルド」セクションを参照してください。

* **IntuneMAM.framework**: Intune アプリ SDK フレームワーク。 アプリで Intune モバイル アプリケーション管理を行えるようにするには、このフレームワークをプロジェクトにリンクします。 アプリで拡張機能を使用する場合は、静的ライブラリではなくフレームワークを使用して、プロジェクトが静的ライブラリの複数のコピーを作成しないようにします。

* **IntuneMAMResources.bundle**: SDK が依存するリソースが含まれているリソース バンドル。 

* **ヘッダー**: Intune アプリ SDK の API を表示します。 API を使用する場合は、API を含むヘッダー ファイルをインクルードする必要があります。 次のヘッダー ファイルには、Intune アプリ SDK の機能を有効にするために必要な API 関数呼び出しが含まれます。 
    
    * IntuneMAMAsyncResult.h
    * IntuneMAMDataProtectionInfo.h
    * IntuneMAMDataProtectionManager.h
    * IntuneMAMFileProtectionInfo.h
    * IntuneMAMFileProtectionManager.h
    * IntuneMAMPolicyDelegate.h
    * IntuneMAMLogger.h 


# Intune アプリ SDK のしくみ

iOS 用 Intune アプリ SDK の目的は、最小限のコード変更で iOS アプリケーションに管理機能を追加することです。 コードの変更が少ないほど短期間で製品化でき、引き続きモバイル アプリケーションの一貫性と安定性が保証されます。 

アプリケーションをスタティック ライブラリにリンクして、リソース バンドルを含める必要があります。 MAMDebugSettings.plist ファイルはオプションです。Microsoft Intune を使用してアプリケーションを展開する必要なく、アプリケーションに適用される MAM ポリシーをシミュレートするために、パッケージに含めることができます。 さらに、デバッグ ビルドでは、iTunes のファイル共有を使用してアプリの Documents ディレクトリに MAMDebugSettings.plist ファイルを転送することで、ファイル内のポリシーを適用できます。

# モバイル アプリとして SDK をビルドする 

Intune アプリ SDK を有効にするには、次の手順に従います。

1. **オプション 1**: 次の手順に従って、`libIntuneMAM.a` ライブラリにリンクします。

    `libIntuneMAM.a` ライブラリをプロジェクト ターゲットの [Linked Frameworks and Libraries] (リンク先フレームワークおよびライブラリ) ボックスの一覧にドラッグ アンド ドロップします。
    ![Intune アプリ SDK iOS - リンク先フレームワークおよびライブラリ](../media/intune-app-sdk-ios-linked-frameworks-and-libraries.png) 

    **注**: アプリをアプリ ストアにリリースする場合は、デバッグ バージョンではなく、リリース用に構築された `libIntuneMAM.a` のバージョンを使用してください。 リリース バージョンは、"release" フォルダーにあります。 デバッグ バージョンには、Intune アプリ SDK での問題のデバッグに役立つ詳細な出力があります。
    
    **オプション 2**: `IntuneMAM.framework` をプロジェクトにリンクします。 `IntuneMAM.framework` をプロジェクト ターゲットの [Linked Frameworks and Libraries] (リンク先フレームワークおよびライブラリ) ボックスの一覧にドラッグ アンド ドロップします。
    
    **注**: フレームワークを使用する場合は、アプリ ストアにアプリを送信する前に、ユニバーサル フレームワークからシミュレーター アーキテクチャを手動で除去する必要があります。 「アプリ ストアにアプリを送信する」セクションを参照してください。

2. 次の iOS フレームワークをプロジェクトに追加します。
    * MessageUI.framework
    * Security.framework
    * MobileCoreServices.framework
    * SystemConfiguration.framework
    * libsqlite3.dylib
    * libc++.dylib
    * ImageIO.framework
    * LocalAuthentication.framework
    * AudioToolbox.framework

    **注**: アプリケーションの対象が iOS 7 の場合は、`LocalAuthentication.framework` の "Status" 属性を "Optional" に設定します。 "Status" が設定されていない場合、アプリケーションは iOS 7 の起動に失敗します。

    **注**: Xcode 7 は `.dylib` 拡張子が `.tbd`。

3. [Build Phases] (ビルド フェーズ) の [Copy Bundle Resources] (バンドル リソースのコピー) にあるリソース バンドルをドラッグして、`IntuneMAMResources.bundle` リソース バンドルをプロジェクトに追加します。
![Intune アプリ SDK iOS - バンドル リソースのコピー](../media/intune-app-sdk-ios-copy-bundle-resources.png)
 
4. `-force_load {PATH_TO_LIB}/libIntuneMAM.a` を次のいずれかに追加して、`{PATH_TO_LIB}` を Intune アプリ SDK の場所に置き換えます。
    * プロジェクトの `OTHER_LDFLAGS` ビルド構成設定 
    * UI の [その他のリンカー フラグ]<br>

    **注**: `PATH_TO_LIB` を検索するには、`libIntuneMAM.a` ファイルを選択し、[ファイル] メニューの [情報の取得] を選択します。 [Info] (情報 ) ウィンドウの [General] (全般) セクションから、[Where] (場所) 情報 (パス) をコピーして貼り付けます。

5. モバイル アプリの Info.plist でメイン Nib またはストーリーボードが定義されている場合、メイン ストーリーボードまたはメイン Nib ファイルのフィールドを削除します。 必要に応じて、以前に削除したストーリーボードまたは Nib の値を IntuneMAMSettings という名前の新しいディクショナリの下に次のキー名で追加します。
    * MainStoryboardFile
    * MainStoryboardFile~ipad
    * MainNibFile
    * MainNibFile~ipad
    
   **注**: モバイル アプリの nfo.plist でメイン Nib またはストーリーボードが定義されていない場合、これらの設定は**不要**です。 

    **注**: (キー名を確認するために) Info.plist を未処理の形式で表示するには、ドキュメント本文の任意の場所を右クリックし、ビューの種類を [Show Raw Keys/Values] ( 生のキー/値の表示) に変更します。

6. 各プロジェクト ターゲットの [Capabilities] (機能) をクリックし、[Keychain Sharing] (キーチェーン共有) スイッチを有効にして、キーチェーン共有を有効にします (まだ有効になっていない場合)。 次の手順に進むには、キーチェーン共有が必要です。

    **注**: プロビジョニング プロファイルで新しいキーチェーン共有値がサポートされている必要があります。 キーチェーン アクセス グループは、ワイルドカード文字をサポートする必要があります。 これを確認するには、テキスト エディターで .mobileprovision ファイルを開いて "keychain-access-groups" を検索し、次のようなワイルド カードがあることを確認します。 
    ```
    <key>keychain-access-groups</key>
    <array>
    <string>YOURBUNDLESEEDID.*</string>
    </array>
    ```
7. キーチェーン共有を有効にした後、次の手順に従って、Intune アプリ SDK のデータを格納する個別のアクセス グループを作成します。 キーチェーン アクセス グループを作成するには、UI を使用するか、権利ファイルを使用します。

    UI を使用してキーチェーン アクセス グループを作成する場合は、次の手順を実行します。 
    
    * モバイル アプリでキーチェーン アクセス グループが定義されていない場合は、アプリのバンドル ID を最初のグループとして追加します。
    * 共有キーチェーン グループ `com.microsoft.intune.mam` を追加します。 Intune アプリ SDK はこのアクセス グループを使用してデータを格納します。  
    * `com.microsoft.adalcache` を既存のアクセス グループに追加します。 

    ![Intune アプリ SDK iOS - キーチェーン共有](../media/intune-app-sdk-ios-keychain-sharing.png) 

    正規の UI ではなく、権利ファイルを使用してキーチェーン アクセス グループを作成する場合は、権利ファイルでキーチェーン アクセス グループの先頭に `$(AppIdentifierPrefix)` を追加する必要があります。 たとえば、  
    * `$(AppIdentifierPrefix)com.microsoft.intune.mam` 
    * `$(AppIdentifierPrefix)com.microsoft.adalcache`

    **注**: 権利ファイルは、iOS アプリ内で特殊なアクセス許可と機能を指定するために使用されるモバイル アプリケーションに固有の XML ファイルです。

8. アプリの Info.plist ファイルで URL スキームが定義されている場合は、`-intunemam` サフィックスを指定して別のスキームを各 URL スキームに追加します。

9. iOS 9 以降用に開発されているモバイル アプリの場合は、アプリが `UIApplication canOpenURL` に渡す各プロトコルを、アプリの Info.plist ファイルの `LSApplicationQueriesSchemes` 配列に含める必要があります。 さらに、表示されているプロトコルごとに新しいプロトコルを追加し、 `-intunemam`。 `http-intunemam`、`https-intunemam`、および `ms-outlook-intunemam` を配列に含める必要もあります。 

10. アプリケの権利でアプリ グループが定義されている場合は、それらのグループを IntuneMAMSettings ディクショナリの `AppGroupIdentitifiers` キーの下に文字列の配列として追加します。

11. モバイル アプリケーションを Azure Directory Authentication Library (ADAL) にリンクします。 Objective C の ADAL ライブラリは、[Github で利用可能です](https://github.com/AzureAD/azure-activedirectory-library-for-objc)。

    **注**: Intune アプリ SDK は、2015 年 6 月 19 日から ADAL のブローカーの支店コードに対してテストされています。 最新の/作業バージョンの ADAL のライブラリにリンクしていることを確認してください。

12. [Build Phases] (ビルド フェーズ) の [Copy Bundle Resources] (バンドル リソースのコピー) にあるリソース バンドルをドラッグして、`ADALiOSBundle.bundle` リソース バンドルをプロジェクトに含めます。

13. ライブラリにリンクするときは `-force_load PATH_TO_ADAL_LIBRARY` リンカー オプションを使用します。

    `-force_load {PATH_TO_LIB}/libADALiOS.a` をプロジェクトの `OTHER_LDFLAGS` ビルド構成設定または UI の [Other Linker Flags] (その他のリンカー フラグ) に追加します。 `PATH_TO_LIB` は、ADAL バイナリの場所に置き換える必要があります。 

# アプリで Azure Directory Authentication Library (ADAL) の設定を構成する 

Intune アプリ SDK では認証と条件付き起動シナリオに ADAL を使用します。 また、デバイスを登録しないで管理するために MAM サービスにユーザー ID を登録する場合も、ADAL を利用します。 

通常、ADAL では、アプリに付与されるトークンのセキュリティを保証するために、アプリを登録し ClientID と呼ばれる一意の ID および他の識別子を取得する必要があります。 Intune アプリ SDK では、Azure Active Directory に接続するときに既定の登録値が使用されます。  

アプリ自体が認証シナリオで ADAL を使用する場合、アプリでは既存の登録値を使用して Intune アプリ SDK の既定値を上書きし、エンド ユーザーが認証を 2 回 (1 回は Intune アプリ SDK によって、もう 1 回はアプリによって) 求められないようにする必要があります。 

##ADAL のよく寄せられる質問

**どのような ADAL バイナリを使用する必要がありますか** 

現在、Intune アプリ SDK は、条件付きアクセス (したがって、Microsoft Authenticator アプリに依存するアプリ) を必要とするアプリをサポートするために、[GitHub の ADAL](https://github.com/AzureAD/azure-activedirectory-library-for-objc) のブローカー ブランチを使用しています。 ただし、ADAL のマスター ブランチとの互換性もまだあります。 アプリに適合するブランチを使用してください。

**どのようにして ADAL バイナリにリンクしますか**

`-force_load {PATH_TO_LIB}/libADALiOS.a` をプロジェクトの `OTHER_LDFLAGS` ビルド構成設定または UI の [Other Linker Flags] (その他のリンカー フラグ) に追加します。 `PATH_TO_LIB` は、ADAL バイナリの場所に置き換える必要があります。 また、必ず ADAL バンドルをアプリにコピーしてください。  

詳細については、[Github の ADAL](https://github.com/AzureAD/azure-activedirectory-library-for-objc) の説明を参照してください。


**同じプロビジョニング プロファイルを使用して署名されている他のアプリと ADAL キャッシュを共有するにはどうすればよいですか**

アプリでキーチェーン アクセス グループが定義されていない場合は、アプリのバンドル ID を最初のグループとして追加します。
キーチェーン権利に `com.microsoft.adalcache` および `com.microsoft.workplacejoin` アクセス グループを追加することによって、ADAL SSO を有効にします。 

ADAL 共有キャッシュ キーチェーン グループを明示的に設定している場合は、`<app_id_prefix>.com.microsoft.adalcache` に設定されていることを確認します。 上書きしない限り ADAL はこれを自動的に設定します。 カスタム キーチェーン グループを指定して `com.microsoft.adalcache` を置き換える場合は、Info.plist の "IntuneMAMSettings" でキー `ADALCacheKeychainGroupOverride` を使用して指定してください。

**アプリで既に使用している ADAL の設定を Intune アプリ SDK にも適用するにはどうすればよいですか** 

アプリが既に ADAL を使用している場合は、次の IntuneMAMSettings のセクションで設定する情報を確認してください。  

* ADALClientId
* ADALRedirectUri
* ADALRedirectScheme
* ADALCacheKeychainGroupOverride

**AAD の運用環境と内部テスト環境を切り替えるにはどうすればよいですか**

`MAMPolicies.plist` の `AadAuthorityURI` の設定を使用して、ADAL の呼び出しに使用される AAD の環境を指定できます。 上書きしない限り、現在は既定で AAD 実稼働前環境 (PPE) を使用するように設定されています。
    
PPE でテストするには、コンパイル時スイッチまたは実行時スイッチを使用できます。 

MAM サービス URL および AAD のコンパイル時環境スイッチの場合は、MAMEnvironment.plist で `UsePPE` ブール型フラグを true に設定します (**注**: Info.plist でこれを行うことはできません)。 

実行時環境スイッチでPPE を使用するには、標準ユーザーの既定値で `com.microsoft.intune.mam.useppe` を "1" に設定します。 これにより、既存の `com.microsoft.intune.mam.AADAuthorityEnvironment` 設定が置き換えられます。 

**AAD 機関 URL を実行時に指定されるテナント固有の URL で上書きするにはどうすればよいですか** 

IntuneMAMPolicyManager インスタンスで `aadAuthorityUriOverride` プロパティを設定します。

**注**: デバイス登録のない MAM で SDK がアプリによってフェッチされる ADAL 更新トークンを再利用できるようにするには、この設定が必要です。

**注:** この値をクリアまたは変更しない場合、SDK はポリシーの更新およびその後の登録要求に対して引き続きこの機関 URL を使用します。  したがって、社内ではユーザーがアプリからサインアウトするときにこの値をクリアし、新しいユーザーがサインインするときにリセットすることが重要です。


**アプリ自体が認証に ADAL を使用している場合はどうすればよいでしょうか**

アプリが既に認証のために ADAL を利用している場合は、次の手順が必要となります。 アプリが ADAL を使用していない場合は、Intune サービスに登録する方法に関するセクションを確認してください。

* プロジェクトの Info.plist の IntuneMAMSettings ディクショナリで、キー名 `ADALClientId` を使用して、ADAL 呼び出しに使用する ClientID を指定します。 

* プロジェクトの Info.plist の IntuneMAMSettings ディクショナリで、キー名 `ADALRedirectUri` を使用して、ADAL 呼び出しに使用するリダイレクト URI を指定します。 アプリのリダイレクト URI の形式によっては、 `ADALRedirectScheme` も指定する必要がある場合があります。



#MAM サービスにアプリを登録する 

## API を使用する
Intune アプリ SDK では、MDM を Intune に登録しなくても iOS が Intune から MAM ポリシーを受け取れるようになりました。 アプリは SDK の新しい API を使用して MAM ポリシーを受け取ることができます。 新しい API を使用するには、次のようにします。

1. デバイス登録の有無に関わらずアプリの管理をサポートする、Intune アプリ SDK の最新リリースを使用します。 この機能のない古いバージョンの SDK をアプリが使用している場合は、Intune MAM ライブラリを更新するだけでなく、Headers フォルダーを最新の SDK のヘッダーで更新する必要があります。

2. API を呼び出すすべてのファイルに IntuneMAMEnrollment.h を追加します。 

3. PPE でテストするには、コンパイル時スイッチまたは実行時スイッチを使用できます。 

    MAM サービス URL および AAD のコンパイル時環境スイッチの場合は、MAMEnvironment.plist で `UsePPE` ブール型フラグを true に設定します (**注**: Info.plist でこれを行うことはできません)。 

    実行時環境スイッチでPPE を使用するには、標準ユーザーの既定値で `com.microsoft.intune.mam.useppe` を "1" に設定します。 これにより、既存の `com.microsoft.intune.mam.AADAuthorityEnvironment` 設定が置き換えられます。 


##アカウントを登録する 

指定されたユーザー アカウントの代わりにアプリが登録されている場合、アプリは Intune サービスから MAM ポリシーを受信できます。  新しくサインインしたユーザーを Intune アプリ SDK に登録するのはアプリの役目です。  新しいユーザー アカウントが認証された後、アプリは Headers/IntuneMAMEnrollment.h の `registerAndEnrollAccount` メソッドを呼び出す必要があります。 

```
/** 


 *  This method will add the account to the list of registered accounts. 
 *  An enrollment request will immediately be started.
 *  @param identity The UPN of the account to be registered with the SDK 
 */ 

(void)registerAndEnrollAccount:(NSString *)identity; 

```
上のメソッドを呼び出すことにより、SDK はユーザー アカウントを登録し、このアカウントの代わりにアプリを登録しようとします。  何らかの理由で登録が失敗した場合、SDK は 24 時間後に自動的に登録を再試行します。  デバッグのため、アプリは登録要求の結果についての通知をデリゲート経由で受け取ることができます (詳細は以下を参照)。

この API が呼び出された後、アプリケーションは通常どおりに機能し続けることができます。  登録が成功した場合、SDK はアプリの再起動が必要であることをユーザーに通知します。  その時点で、ユーザーはすぐにアプリを再起動できます。


##アカウントを登録解除する 


ユーザーがアプリからサインアウトする前に、アプリは SDK からユーザーを登録解除する必要があります。  これにより次のことが保証されます。 

1. そのユーザーのアカウントに対して登録の再試行が行われなくなります。 
2. ユーザーがアプリケーションに正常に登録していた場合、ユーザーとアプリは Intune MAM サービスから登録解除され、MAM ポリシーは削除されます。
3. 必要に応じて、選択的ワイプを開始し、職場または学校に関するデータを削除できます。 

ユーザーがサイン会うとする前に、アプリはHeaders/IntuneMAMEnrollment.h にある次の API を呼び出す必要があります。 

```
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

ユーザー アカウントの AAD トークンが削除される前に、このメソッドを呼び出す必要があります。  ユーザーのアプリ トークンが、ユーザーの代わりに Intune MAM サービスに対して特定の要求を行う必要があります。 

アプリ自体がユーザーの職場または学校関連データを削除する場合は、`doWipe` フラグを false に設定できます。  そうでない場合、アプリは SDK に選択的ワイプを開始させることができます。それにより、アプリの選択的ワイプ デリゲートが呼び出されます。 

```
[[IntuneMAMEnrollmentManager instance] deRegisterAndUnenrollAccount:@”user@foo.com” withWipe:YES]; 
```


##事前にサインインしないで登録する 

Azure Active Directory でユーザーをサインインしないアプリでも、次の API を呼び出して SDK にその認証を処理させることにより、Intune サービスから MAM ポリシーを受け取ることができます。 アプリは、AAD でユーザーを認証していなくても、アプリ内のデータを保護するために MAM ポリシーを取得する必要がある場合、この方法を使用する必要があります。たとえば、別の認証サービスをアプリのログインに使用している場合や、アプリがサインインをまったくサポートしていない場合などです。 これを行うには、アプリケーションで Headers/IntuneMAMEnrollment.h にある`loginAndEnrollAccount` メソッドを呼び出す必要があります。

```
/** 
 *  Creates an enrollment request which is started immediately. 
 *  If no token can be retrieved for the identity, the user will be prompted 
 *  to enter their credentials, after which enrollment will be retried. 
 *  @param identity The UPN of the account to be logged in and enrolled. 
 */ 
 (void)loginAndEnrollAccount: (NSString *)identity; 

```
このメソッドを呼び出すと、SDK は、既存のトークンが見つからない場合はユーザーに資格情報の入力を要求した後、そのアカウントの代わりにアプリケーションの登録を試みます。 このメソッドは、ID として "nil" を指定して呼び出すことができます。そうすると、SDK は、デバイス上の既存の MAM ユーザーで登録するか、または既存ユーザーが見つからない場合はユーザーにユーザー名の入力を求めます。 

登録が失敗した場合、エラーの詳細によっては、アプリは後で再びこの API を呼び出す必要があります。 アプリは登録要求の結果についての通知をデリゲート経由で受け取ることができます (詳細を参照)。 

この API が呼び出された後、アプリは通常どおりに機能し続けることができます。  登録が成功した場合は、アカウントの登録に関する前のセクションで示したように、SDK はアプリの再起動が必要であることをユーザーに通知します。 

##デバッグに関する情報 

アプリは、Intune MAM サービスに対する次の要求についてのデバッグ通知を受け取ることができます。 

 - 登録要求 
 - ポリシー更新要求 
 - 登録解除要求 

通知は、Headers/IntuneMAMEnrollmentDelegate.h に含まれるデリゲート メソッドを使用して取得できます。 

```
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

これらのデリゲート メソッドは、次の情報を含む ```IntuneMAMEnrollmentStatus``` をオブジェクトを返します。 

- 要求に関連付けられているアカウントの ID 
- 要求の結果を示すステータス コード 
- エラー文字列とステータス コードの説明 
- NSError オブジェクト 

このオブジェクトは、返される可能性のある特定のステータス コードと共に Headers/IntuneMAMEnrollmentStatus.h で定義されています。 

この情報はデバッグ専用であり、アプリのビジネス ロジックでこれらの通知を利用してはならないことに注意することが重要です。  アプリでは、デバッグまたは監視を目的としてテレメトリ サービスにこの情報を送信できます。 


##サンプル コード 

デリゲート メソッドの実装例を次に示します。 

```
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


##アプリの再起動 

アプリは、MAM ポリシーを初めて受け取ったときに、必要なフックを適用するために再起動する必要があります。  再起動が必要であることをアプリに通知するためのメソッドは、Headers/IntuneMAMPolicyDelegate.h で提供されています。 
```
 - (BOOL) restartApplication 
```
このメソッドの戻り値は SDK に、アプリケーションが必要な再起動を処理するかどうかを通知します。   

 - true が返された場合は、アプリケーションが再起動を処理する責任があります。   
 - false が返された場合は、SDK はこのメソッドから返った後でアプリケーションを再起動します。  SDK は直ちに、アプリケーションを再起動する必要があることをユーザーに伝えるダイアログを表示します。 



# Intune アプリ SDK 設定の構成

アプリケーションの Info.plist 内に含まれている IntuneMAMSettings ディクショナリは、Intune アプリ SDK を構成するために使用します。 サポートされているすべての設定の一覧を次に示します。 

これらの設定の一部は前のセクションで説明しています。一部の設定はすべてのアプリには適用されません。 

Setting  | 型  | 定義 | 必須
--       |  --   |   --       |  --
ADALClientId  | 文字列型  | アプリの AAD クライアント識別子。 | アプリが ADAL を使用する場合に必要です。
ADALRedirectUri  | 文字列型  | アプリの AAD リダイレクト URI。 | アプリが ADAL を使用する場合は、ADALRedirectUri または ADALRedirectScheme が必要です。 
ADALRedirectScheme  | 文字列型  | アプリの AAD リダイレクト スキーム。 アプリケーションのリダイレクト URI が `scheme://bundle_id` 形式の場合は、ADALRedirectUri の代わりにこれを使用できます。 | アプリが ADAL を使用する場合は、ADALRedirectUri または ADALRedirectScheme が必要です。 
ADALLogOverrideDisabled | ブール型  | SDK がすべての ADAL ログ (アプリからの ADAL 呼び出しがある場合はこれを含む) をログ ファイルにルーティングするかどうかを指定します。 既定は [いいえ] です。 アプリで独自の ADAL ログ コールバックを設定する場合は [はい] に設定します。 | 任意。
ADALCacheKeychainGroupOverride | 文字列型  | "com.microsoft.adalcache" の代わりに ADAL キャッシュに使用するキーチェーン グループを指定します。 これにはアプリ ID プレフィックスは含まれないことに注意してください。 実行時に指定された文字列の前に付加されます。 | 任意。
AppGroupIdentifiers | 文字列の配列  | アプリの権利 com.apple.security.application-groups セクションのアプリケーション グループの配列。 | アプリでアプリケーション グループを使用する場合は必須です。
ContainingAppBundleId | 文字列型 | アプリケーションを含む拡張機能のバンドル ID を指定します。 | iOS の拡張機能に必要です。
DebugSettingsEnabled| ブール型 | YES に設定すると、Settings バンドル内のテスト ポリシーを適用できます。 この設定を有効にしたままアプリケーションを出荷しては**なりません**。 | 任意。
MainNibFile<br>MainNibFile~ipad  | 文字列型  | この設定には、アプリケーションのメイン nib ファイル名を含める必要があります。  | アプリケーションの Info.plist で MainNibFile が定義されている場合は必須です。
MainStoryboardFile<br>MainStoryboardFile~ipad  | 文字列型  | この設定には、アプリケーションのメインのストーリーボードのファイル名を含める必要があります。 | アプリケーションの Info.plist で UIMainStoryboardFile が定義されている場合は必須です。
MAMPolicyRequired| ブール型| アプリに Intune MAM ポリシーがない場合、アプリの起動をブロックするかどうかを指定します。 既定値は "no" です。 
MAMPolicyWarnAbsent | ブール型| アプリに Intune MAM ポリシーがない場合、アプリの起動時にユーザーに警告するかどうかを指定します。 注: この設定を YES にした状態でアプリをストアに送信することはできません | 任意。
MultiIdentity | ブール型| アプリが複数 ID 対応かどうかを指定します。 | 任意。
SplashIconFile <br>SplashIconFile~ipad | 文字列型  | Intune スプラッシュ アイコン ファイルを指定します。 詳細については、このガイドの「スタートアップ時のイメージ ファイル」のセクションを参照してください。 | 任意。
SplashDuration | 数値 | アプリケーションの起動時に Intune スプラッシュ画面が表示される最短時間 (秒)。 既定値は 1.5 です。 | 任意。
BackgroundColor| 文字列型| スプラッシュ画面と PIN 画面の背景色を指定します。 "#XXXXXX" の形式の 16 進 RGB 文字列を受け付けます。"X" には 0 ～ 9 または A ～ F を使用できます。 シャープ記号は省略してもかまいません。   | 省略可能で、既定値は明るい灰色です。
ForegroundColor| 文字列型| スプラッシュ画面と PIN 画面の前景色を指定します。テキストの色などです。 "#XXXXXX" の形式の 16 進 RGB 文字列を受け付けます。"X" には 0 ～ 9 または A ～ F を使用できます。 シャープ記号は省略してもかまいません。  | 省略可能で、既定値は黒です。
AccentColor | 文字列型| PIN 画面のアクセント カラーを指定します。ボタン テキストの色やボックスの強調表示色などです。  "#XXXXXX" の形式の 16 進 RGB 文字列を受け付けます。"X" には 0 ～ 9 または A ～ F を使用できます。 シャープ記号は省略してもかまいません。| 省略可能で、既定値はシステムの青です。
MAMTelemetryDisabled| ブール型| SDK がテレメトリ データをバックエンドに返送しないかどうかを指定します。| 任意。
MAMTelemetryUsePPE | ブール型 | SDK が実稼働前環境 (PPE) バックエンドにデータを送信するかどうかを指定します。 テスト用テレメトリ データが顧客データと混ざらないように Intune ポリシーでアプリをテストするときに使用します。 | 任意。

## 製品利用統計情報 

iOS 用 Intune アプリ SDK では、既定で、使用状況イベントに関する製品利用統計情報がログに記録され、Microsoft Intune に送信されます。 次の使用状況イベントのデータがログに記録されます。 

1. **アプリの起動:** Microsoft Intune が MAM 対応アプリの使用状況を管理タイプ別に確認するために役立ちます (MDM を使用した MAM、MDM 登録を使用しない MAM など)。

2. **enrollApplication API の呼び出し:** Microsoft Intune がクライアント側からの `enrollApplication` 呼び出しの成功率と他のさまざまなパフォーマンス指標を確認するのに役立ちます。

**注**: モバイル アプリケーションから Intune アプリ SDK の製品利用統計情報を Microsoft Intune に送信しない場合は、IntuneMAMSettings ディクショナリのプロパティ `MAMTelemetryDisabled` を "YES" に設定して、Intune アプリ SDK 製品利用統計情報のキャプチャを無効にする必要があります。


## 拡張機能として SDK をビルドする (省略可能) 

拡張機能を構築する場合は、「モバイル アプリとして SDK を構築する」のセクションで説明した、モバイル アプリを構築する場合と同じ手順に従います。 さらに、IntuneMAMSettings ディクショナリで `ContainingAppBundleId` キーを、含まれるアプリケーションのバンドル ID の値を使用して追加することにより、各拡張機能の Info.plist ファイルを更新します。

## フレームワークとして SDK をビルドする (省略可能)

Intune アプリ SDK の最新の更新により、モバイル アプリに埋め込みアプリケーション フレームワークが含まれている場合、特定のリンカー フラグを使用してモバイル アプリケーションをコンパイルする必要はありません。 

## スタートアップ時のイメージ ファイル (省略可能)

MAM 対応アプリを Microsoft Intune でアクティブに管理する場合、Intune アプリ SDK はアプリの起動時にスタートアップ画面を表示して、アプリが管理されていることをユーザーに示します。 必要に応じて、イメージ ファイルを追加して、[会社によって管理されています] スタートアップ ページを表示できます。 イメージに関する次のガイドラインを使用します。

* アプリの Info.plist の IntuneMAMSettings ディクショナリで、キー名 `SplashIconFile` および `SplashIconFile~ipad` を使用してファイル名を追加します。 

* イメージのサイズと要件:

    * iPhone 6s Plus と iPhone 6 Plus は 180x180、その他の iPhone モデルは 120x120、iPad は 152x152。 
    
    * ファイル名から .png 拡張子を削除します。 
    
    * ライブラリにリンクするときは `@2x` サフィックスを使用し、3 倍スケール バージョンに `@3x` サフィックスを使用します。 イメージが適切なサイズでない場合は、画面に合わせて拡大縮小されます。 SplashIconFile の値が指定されていない場合、Intune アプリ SDK によってアプリのいずれかのアイコン (すべての iPhone で 60x60、iPad で 76x76) が選択されます。

**注**: この画面は起動によってトリガーされますが、ユーザーが完全に破棄することができます。



#複数 ID を有効にする (省略可能)

既定では、SDK はポリシーをアプリ全体に適用します。 複数 ID は、ID 単位のレベルでポリシーを適用できるようにする MAM の機能です。  これには、他の MAM 機能より多くのアプリの参加が必要です。 

アプリは、アクティブな ID を変更するときにアプリ SDK に通知する必要があります。 また、SDK は ID の変更が必要なときにもアプリに通知します。 現時点では、サポートされる管理対象 ID は 1 つだけです。 ユーザーがデバイスまたはアプリを登録すると、SDK はこの ID を使用し、それをプライマリ管理対象 ID であると判断します。 アプリの他のユーザーは、無制限のポリシー設定を持つ管理対象外として扱われます。 

ID は文字列として簡単に定義されることに注意してください。 ID は大文字と小文字を区別されず、SDK に ID を要求すると返される ID は、大文字と小文字の使い分けが ID 設定時の本来のものと異なる可能性があります。


##ID について 
  
ID は、アカウントのユーザー名です (例: user@contoso.com)。 開発者は、次のさまざまなレベルでアプリの ID を設定できます。 

* **プロセス ID**: プロセス ID はプロセス全体に通用する ID を設定し、主として単一の ID アプリケーションに使用されます。 この ID は、すべての操作、ファイル、UI に適用されます。
* **UI ID**: 切り取り/コピー/貼り付け、PIN、認証、データ共有など、メイン スレッドでの UI 操作に適用されるポリシーを決定します。UI ID は、ファイル操作 (暗号化、バックアップなど) には適用されません。 
* **スレッド ID**: スレッド ID は、現在のスレッドに適用されるポリシーを決定します。 これは、すべての操作、ファイル、UI に反映されます。

ユーザーが管理されているかどうかに関わらず、アプリは ID を適切に設定する必要があります。

常に、すべてのスレッドは UI 操作およびファイル操作のための有効な ID を持っています。 これは、適用する必要があるポリシー (ある場合) を決定するために使用される ID です。 ID が "ID なし" の場合、またはユーザーが管理されていない場合は、ポリシーは適用されません。 
 
 

##スレッド キュー
 
アプリは、多くの場合、スレッド キューに対して非同期タスクと同期タスクをディスパッチします。 SDK は、Grand Central Dispatch (GCD) 呼び出しをインターセプトして、現在のスレッド ID をディスパッチされたタスクに関連付けます。 タスクの実行時に、SDK はスレッド ID をタスクに関連付けられた ID に一時的に変更し、タスクを実行してから、元のスレッド ID に戻します。 `NSOperationQueue` は GCD を基にして作成されているので、`NSOperations` は `NSOperationQueue` に追加されるときにスレッドの ID で実行します。 GCD を直接使用してディスパッチされた `NSOperations` または関数も、実行時に現在のスレッド ID を変更できます。 この ID は、ディスパッチ スレッドから継承された ID を上書きします。 

##ファイルの所有者
 
SDK は、ローカル ファイル所有者の ID を追跡し、それに従ってポリシーを適用します。 ファイルの所有者は、ファイルが作成されるとき、またはファイルが切り捨てモードで開かれるときに、設定されます。 所有者は、操作を実行するスレッドの有効なファイル操作 ID に設定されます。 または、アプリで `IntuneMAMFilePolicyManager` を使用してファイル所有者 ID を明示的に設定することもできます。 アプリでは、`IntuneMAMFilePolicyManager` を使用してファイルの所有者を取得し、ファイルの内容を表示する前に UI ID を設定することができます。


##共有データ ファイル
 
管理対象ユーザーと管理対象外ユーザー両方のデータを含むファイルをアプリが作成する場合、管理対象ユーザーのデータの暗号化はアプリで行う必要があります。 データの暗号化は、`IntuneMAMDataProtectionManager` の API の `protect` および `unprotect` を使用して行うことができます。 `protect` メソッドに渡す ID は、管理対象ユーザーまたは管理対象外ユーザーのどちらでもかまいません。 ユーザーが管理されている場合、データは暗号化されます。 ユーザーが管理されていない場合は、ヘッダーがデータに追加されて ID はエンコードされますが、データは暗号化されません。  `protectionInfo` メソッドを使用すると、データの所有者を取得できます。

##共有拡張機能
 
アプリに共有拡張機能が含まれている場合、`IntuneMAMDataProtectionManager` の `protectionInfoForItemProvider` メソッドを使用して共有対象アイテムの所有者を取得できます。 共有対象アイテムがファイルの場合は、SDK がファイル所有者の設定を処理します。 共有対象アイテムがデータの場合は、そのデータがファイルに保存される場合のファイル所有者の設定はアプリで行う必要があり、アプリはそのデータを UI で表示する前に `setUIPolicyIdentity` API (後述) を呼び出す必要があります。
 
#複数 ID を有効にする
 
既定では、アプリは 1 つの ID と見なされ、SDK はプロセス ID を登録済みのユーザーに設定します。 複数 ID のサポートを有効にするには、ブール型設定 "MultiIdentity" の値を "YES" に設定して、アプリの Info.plist ファイルの IntuneMAMSettings ディクショナリに追加する必要があります。 複数 ID を有効にすると、プロセス ID、UI ID、スレッド ID は nil に設定され、これらの適切な設定はアプリで行う必要があります。

 
##ID の切り替え
 
###アプリで開始する ID の切り替え
複数 ID アプリは、起動時には、不明の管理対象外アカウントで実行されているものと見なされます。 条件付き起動 UI は実行せず、アプリに対してポリシーは適用されません。 Id を変更する必要があるときは常に、アプリが SDK に通知する必要があります。 通常、この処理は、アプリが特定のユーザー アカウントのデータを表示するときに行われます。

たとえば、ユーザーがドキュメント、メールボックス、またはノートブックのタブを開こうとしたときなどです。 アプリは、ファイル、メールボックス、またはタブが実際に開かれる前に、SDK に通知する必要があります。 これを行うには、`IntuneMAMPolicyManager` の API `setUIPolicyIdentity` を使用します。 ユーザーが管理されているかどうかに関わらず、この API を呼び出す必要があります。 ユーザーが管理されている場合、SDK は条件付き起動確認を行います (改造の検出、PIN、認証など)。 ID 切り替えの結果は、完了ハンドラーを介して非同期的にアプリに返されます。 アプリは、ドキュメント、メールボックス、タブなどを開くのを、 成功結果コードが返されるまで延期する必要があります。 ID の切り替えが失敗した場合、アプリは操作をキャンセルする必要があります。 

###SDK によって開始される ID の切り替え
SDK が特定の ID への切り替えをアプリに要求することが必要になる場合があります。 複数 ID アプリは、この要求を処理するために `IntuneMAMPolicyDelegate` の `identitySwitchRequired` メソッドを実装する必要があります。 アプリは、このメソッドを呼び出すとき、指定された ID への切り替え要求を処理できる場合は、`IntuneMAMAddIdentityResultSuccess` を完了ハンドラーに渡す必要があります。 ID の切り替えを処理できない場合、アプリは完了ハンドラーに `IntuneMAMAddIdentityResultFailed` を渡す必要があります。 アプリは、この呼び出しに応答して `setUIPolicyIdentity` を呼び出す必要はありません。 アプリが管理されていないユーザー アカウントに切り替える必要がある場合は、`identitySwitchRequired` の呼び出しに空の文字列が渡されます。 
 
###選択的ワイプ
アプリが選択的にワイプされる場合、SDK は `IntuneMAMPolicyDelegate` の `wipeDataForAccount` メソッドを呼び出します。 アプリは、指定されたユーザーのアカウントとそれに関連付けられているすべてのデータを削除する必要があります。 SDK は、ユーザーが所有するすべてのファイルを削除でき、アプリが `wipeDataForAccount` の呼び出しから "FALSE" を返した場合はすべてのファイルを削除します。 注意: このメソッドはバックグラウンド スレッドから呼び出され、アプリは (アプリが "FALSE" を返す場合のファイルを除き) ユーザーのすべてのデータが削除されるまで返ることはできません。

# Xcode での Intune アプリ SDK のデバッグ

Microsoft Intune で MAM 対応アプリを手動でテストする前に、Xcode で **Settings.bundle** ファイルを使用できます。 これにより、Intune に接続しなくてもテスト ポリシーを設定できます。 有効にするには、次の手順を実行します。

* プロジェクトの最上位フォルダーを右クリックして Settings.bundle ファイルを追加します。 メニューから [追加] -> [新しいファイル] を選択します。 追加する [リソース] の下にある "設定バンドル" テンプレートを選択します。

* デバッグ ビルドでのみ、MAMDebugSettings.plist を Settings.bundle にコピーします。

* Root.plist (Settings.bundle 内あります) に、"Type" = Child Pane および "FileName" = MAMDebugSettings の設定を追加します。

* **[設定] -> <アプリ名>** で、[Enable Test Policies] (テスト ポリシーを有効にする) をオンにします。

* アプリを起動します (Xcode の内部または外部)。 

* **[設定] -> <アプリ名> -> [Enable Test Policies] (テスト ポリシーを有効にする)** で、"PIN" などのポリシーをオンにします。

* アプリを起動します (Xcode の内部または外部)。 PIN が期待どおりに機能することを確認します。

> [!NOTE]
> **[設定] -> <アプリ名> -> [Enable Test Policies] (テスト ポリシーを有効にする)** を使用して設定を有効にしたり切り替えたりできるようになりました。

# 推奨される iOS のベスト プラクティス

iOS 向けの開発時に推奨されるベスト プラクティスを次に示します。

iOS ファイル システムでは大文字と小文字が区別されます。 `libIntuneMAM.a` や `IntuneMAMResources.bundle` などのファイル名で大文字と小文字が正しいことを確認します。

Xcode で `libIntuneMAM.a`が見つからない場合は、リンカー検索パスにこのライブラリへのパスを追加して問題を解決できます。



##FAQ 

 **アプリケーションのすべてのユーザーを MAM サービスに登録する必要がありますか**

いいえ。  実際には、Intune アプリ SDK に登録する必要があるのは職場または学校アカウントのみです。  アプリでは、職場または学校のコンテキストでアカウントが使用されるかどうかを判断する必要があります。   
 
**アプリケーションに既にサインインしているユーザーはどうなりますか。  登録する必要がありますか** 

アプリケーションは、ユーザーが正常に認証された後でユーザーを登録する必要がありますが、アプリケーションが MDM のない MAM 機能を使用する前に存在していた可能性がある既存のアカウントを登録する必要もあります。   


これを行うには、アプリケーションは `registeredAccounts:` メソッドを使用する必要があります。  このメソッドは、Intune MAM サービスに登録されているすべてのアカウントを含む NSDictionary を返します。  アプリケーションの既存のアカウントがこの一覧に存在しない場合、アプリケーションは `registerAndEnrollAccount:` を使用してそれらのアカウントを登録する必要があります。 


 

**SDK はどのような頻度で登録を再試行しますか** 

SDK は、以前に失敗したすべての登録を 24 時間ごとに自動的に再試行します。  SDK はこれにより、ユーザーがアプリケーションにサインインした後でユーザーの組織が MAM を有効にしてあり、ユーザーが正常に登録してポリシーを受け取れるかどうかを確認します。 

ユーザーがアプリケーションを正常に登録したことを検出した場合、SDK は再試行を停止します。  これは、アプリケーションを登録できるのは一度に 1 人のユーザーだけであるためです。 ユーザーが登録解除された場合、同じ 24 時間間隔内に再試行が再び開始されます。 


 
**ユーザーを登録解除する必要があるのはなぜですか** 

SDK は、次の操作をバックグラウンドで定期的に実行します。

 - アプリケーションがまだ登録されていない場合、SDK は 24 時間ごとにリストにあるすべてのアカウントの登録を試みます。 
 - アプリケーションが登録されている場合は、SDK は 8 時間ごとに MAM ポリシーの更新を確認します。 

ユーザーを登録解除することで、アプリケーションは、ユーザーがアプリケーションを使用しなくなり、そのユーザー アカウントに対する上記の定期的イベントを停止できることを SDK に通知します。  また、必要に応じて、アプリの登録解除と選択的ワイプもトリガーします。 

**登録解除メソッドでは doWipe フラグを true に設定する必要がありますか** このメソッドは、ユーザーがアプリケーションからサインアウトする前に呼び出す必要があります。  サインアウトの一環としてユーザーのデータがアプリケーションから削除される場合は、`doWipe` を false に設定できます。  ただし、アプリケーションがユーザーのデータを実際に削除しない場合は、SDK がデータを削除できるように、このフラグを true に設定する必要があります。 

**アプリケーションを登録解除できる他の方法はありますか** はい。IT 管理者は選択的ワイプ コマンドをアプリケーションに送信できます。このコマンドを送信すると、ユーザーは登録を解除されて、ユーザーのデータはワイプされます。  SDK は自動的にこのシナリオを処理し、登録解除デリゲート メソッドで通知を送信します。 

#アプリ ストアにアプリを送信する
Intune アプリ SDK の静的ライブラリおよびフレームワークのビルドはどちらもユニバーサル バイナリであり、これはデバイスとシミュレーターのすべてのアーキテクチャ用のコードが含まれていることを意味します。 Apple は、App Store に送信されたアプリにシミュレーターのコードが含まれていると、そのアプリを拒否します。 デバイス専用ビルドの静的ライブラリ用にコンパイルするとき、リンカーは自動的にシミュレーター コードを削除します。

アプリが Intune アプリ SDK の**フレームワーク ビルド**を使用する場合は、アプリ ストアにアプリを送信する前に、ユニバーサル フレームワークからシミュレーター アーキテクチャを手動で除去する必要があります。 次の手順を参考にしてください。

1. `IntuneMAM.framework` がデスクトップにあることを確認します。
2. 次のコマンドを実行します。
    
    ```
    lipo ~/Desktop/IntuneMAM.framework/IntuneMAM -remove i386 -remove x86_64 -output ~/Desktop/IntuneMAM.device_only
    ```
    最初のコマンドは、フレームワークの dylib からシミュレーター アーキテクチャを削除します。
    ```
    cp ~/Desktop/IntuneMAM.device_only ~/Desktop/IntuneMAM.framework/IntuneMAM 
    ```
    2 番目のコマンドは、デバイス専用の dylib をフレームワークのディレクトリにコピーします。



<!--HONumber=Sep16_HO4-->


