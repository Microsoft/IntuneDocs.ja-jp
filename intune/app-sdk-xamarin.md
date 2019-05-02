---
title: Microsoft Intune App SDK Xamarin バインディング
description: Intune App SDK Xamarin バインディングを利用すると、Xamarin でビルドされた iOS アプリと Android アプリで Intune アプリ保護ポリシーが有効になります。
keywords: sdk, Xamarin, intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/08/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 275d574b-3560-4992-877c-c6aa480717f4
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: d42fab929d6fa3e7fbaed8e9557573ebbaa1f3ad
ms.sourcegitcommit: 364a7dbc7eaa414c7a9c39cf53eb4250e1ad3151
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59292352"
---
# <a name="microsoft-intune-app-sdk-xamarin-bindings"></a>Microsoft Intune App SDK Xamarin バインディング

> [!NOTE]
> 最初に、[Intune アプリ SDK の概要](app-sdk-get-started.md)に関する記事に目を通すことをお勧めします。このガイドでは、サポートする各プラットフォームで統合のための準備をする方法について説明しています。

## <a name="overview"></a>概要
[Intune App SDK Xamarin バインディング](https://github.com/msintuneappsdk/intune-app-sdk-xamarin)を利用すると、Xamarin でビルドされた iOS アプリと Android アプリで [Intune アプリ保護ポリシー](app-protection-policy.md)が有効になります。 このバインディングを利用すると、開発者は Intune のアプリ保護機能を Xamarin ベースのアプリに簡単に組み込むことができます。

Microsoft Intune App SDK Xamarin バインディングを利用すると、Intune アプリ保護ポリシー (別名、APP または MAM ポリシー) を Xamarin で開発したアプリに組み込むことができます。 MAM 対応のアプリケーションが Intune App SDK に統合されています。 Intune で積極的にアプリを管理している場合、IT 管理者はモバイル アプリにアプリ保護ポリシーを展開できます。

## <a name="whats-supported"></a>サポートされる内容

### <a name="developer-machines"></a>開発者のコンピューター
* Windows (Visual Studio バージョン 15.7 以降)
* macOS

### <a name="mobile-app-platforms"></a>モバイル アプリのプラットフォーム
* Android
* iOS

### <a name="intune-mobile-application-management-scenarios"></a>Intune モバイル アプリケーション管理のシナリオ

* Intune APP-WE (デバイス登録なし)
* Intune MDM 登録デバイス
* サードパーティ製の EMM 登録デバイス

Intune App SDK Xamarin バインディングで開発された Xamarin アプリでは、モバイル デバイス管理 (MDM) に登録しているデバイスと登録していないデバイスの両方で、Intune アプリ保護ポリシーを受け取るようになりました。

## <a name="prerequisites"></a>必要条件

[ライセンス条項](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/blob/master/Microsoft%20License%20Terms%20Intune%20App%20SDK%20Xamarin%20Component.pdf)を確認します。 記録用にライセンス条項を印刷し、保持します。 Intune App SDK Xamarin バインディングをダウンロードし、使用すると、このライセンス条項に同意したことになります。 本ライセンス条項に同意されない場合、お客様は本ソフトウェアを使用できません。

SDK では、その[認証](https://azure.microsoft.com/documentation/articles/active-directory-authentication-scenarios/)と条件付き起動シナリオを [Active Directory 認証ライブラリ (ADAL)](https://azure.microsoft.com/documentation/articles/active-directory-authentication-libraries/) に依存しているため、[Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-whatis/) を使用してアプリを構成する必要があります。 

アプリケーションが ADAL または MSAL を使用するように既に構成されており、独自のカスタム クライアント ID が Azure Active Directory での認証に利用される場合は、Intune モバイル アプリケーション管理 (MAM) サービスへのアクセス許可を Xamarin アプリに付与するための手順に従っていることを確認します。 [Intune SDK の概要ガイド](app-sdk-get-started.md#give-your-app-access-to-the-intune-app-protection-service-optional)の[アプリに対する Intune アプリ保護サービスへのアクセス権の付与](app-sdk-get-started.md)に関するセクションに記載されている手順を使用します。

## <a name="enabling-intune-app-protection-polices-in-your-ios-mobile-app"></a>iOS モバイル アプリで Intune アプリ保護ポリシーを有効にする
1. [Microsoft.Intune.MAM.Xamarin.iOS NuGet パッケージ](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.iOS)を Xamarin.iOS プロジェクトに追加します。
2.  iOS モバイル アプリに Intune App SDK を統合するのに必要な、一般的な手順に従います。 [iOS 用 Intune App SDK 開発者ガイド](app-sdk-ios.md#build-the-sdk-into-your-mobile-app)にある統合の手順 (手順 3) から開始できます。 IntuneMAMConfigurator を実行するセクションの最後の手順は、省略できます。このツールは Microsoft.Intune.MAM.Xamarin.iOS パッケージに含まれており、ビルド時に自動的に実行されるからです。
    **重要**: Visual Studio と Xcode とでは、アプリのキーチェーンの共有を有効にする方法が少し異なります。 アプリの Entitlements plist を開き、[キーチェーンを有効にする] オプションが有効になっていることと、適切なキーチェーンの共有グループがそのセクションに追加されていることを確認します。 次に、すべての構成およびプラットフォームの適切な組み合わせに対して、プロジェクトの [iOS バンドル署名] オプションの [カスタム エンタイトルメント] フィールドに、その Entitlements plist が指定されていることを確認します。
3.  バインディングが追加され、アプリが正しく構成されると、お使いのアプリで Intune SDK の API を使用できるようになります。 これを行うには、次の名前空間を含める必要があります。

      ```csharp
      using Microsoft.Intune.MAM;
      ```
4. アプリ保護ポリシーを受信するには、Intune MAM サービスにアプリを登録する必要があります。 アプリがユーザーの認証に [Azure Active Directory Authentication Library](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) (ADAL) または [Microsoft Authentication Library](https://www.nuget.org/packages/Microsoft.Identity.Client) (MSAL) を使用しておらず、Intune SDK で認証を処理したい場合、アプリは IntuneMAMEnrollmentManager の LoginAndEnrollAccount メソッドにユーザーの UPN を提供する必要があります:
      ```csharp
       IntuneMAMEnrollmentManager.Instance.LoginAndEnrollAccount([NullAllowed] string identity);
      ```
      呼び出し時にユーザーの UPN が不明な場合、アプリは null を渡すことがあります。 この場合、ユーザーはメール アドレスとパスワードの両方を入力するよう求められます。
      
      アプリが既に ADAL または MSAL を使用してユーザーを認証している場合は、アプリと Intune SDK 間のシングルサインオン (SSO) エクスペリエンスを構成できます。 まず、Intune Xamarin Bindings for iOS (com.microsoft.adalcache) で使用されているものと同じキーチェーン アクセス グループにトークンを格納するように ADAL/MSAL を構成する必要があります。 ADAL の場合、この処理を行うには、[AuthenticationContext の KeychainSecurityGroup プロパティを設定します](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet/wiki/Token-cache-serialization#enable-token-cache-sharing-across-ios-applications)。 MSAL の場合、[PublicClientApplication の KeychainSecurityGroup プロパティを設定する](https://github.com/AzureAD/microsoft-authentication-library-for-dotnet/wiki/msal-net-2-released#you-can-now-enable-sso-between-adal-and-msal-apps-on-xamarinios)必要があります。 次に、Intune SDK で使用される既定の AAD 設定をアプリの設定でオーバーライドする必要があります。 これを行うには、[iOS 用 Intune App SDK 開発者ガイド](app-sdk-ios.md#configure-settings-for-the-intune-app-sdk)で説明しているように、アプリの Info.plist 内にある IntuneMAMSettings ディクショナリを利用できます。または IntuneMAMPolicyManager インスタンスで AAD の override プロパティを使用することも可能です。 ADAL 設定が静的なアプリケーションでは Info.plist を使用する方法をお勧めしますが、実行時にその値が決定されるアプリケーションでは override プロパティをお勧めします。 すべての SSO 設定が構成されたら、アプリが正常に認証された後、IntuneMAMEnrollmentManager の RegisterAndEnrollAccount メソッドにユーザーの UPN を指定する必要があります。
      ```csharp
      IntuneMAMEnrollmentManager.Instance.RegisterAndEnrollAccount(string identity);
      ```
      アプリは、IntuneMAMEnrollmentDelegate のサブクラスに EnrollmentRequestWithStatus メソッドを実装し、IntuneMAMEnrollmentManager の Delegate プロパティをそのクラスのインスタンスに設定することで、登録試行の結果を判断できます。 例として、[サンプル Xamarin.iOS アプリケーション](https://github.com/msintuneappsdk/sample-intune-xamarin-ios)に関するページを参照してください。

      登録が成功すると、アプリケは次のプロパティのクエリを実行することで、登録されているアカウント (以前は不明だった場合) の UPN を特定できます。 
      ```csharp
       string enrolledAccount = IntuneMAMEnrollmentManager.Instance.EnrolledAccount;
      ```      
> [!NOTE] 
> iOS 用の remapper はありません。 Xamarin.Forms アプリへの統合は、通常の Xamarin.iOS プロジェクトと同様に行います。 

## <a name="enabling-intune-app-protection-policies-in-your-android-mobile-app"></a>Android モバイル アプリで Intune のアプリ保護ポリシーを有効にする

1. [Microsoft.Intune.MAM.Xamarin.Android NuGet パッケージ](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.Android)を Xamarin.Android プロジェクトに追加します。
    1. Xamarin.Forms アプリでは、追加、 [Microsoft.Intune.MAM.Remapper.Tasks NuGet パッケージ](https://www.nuget.org/packages/Microsoft.Intune.MAM.Remapper.Tasks)も Xamarin.Android プロジェクトにします。 
2. 必要な一般的な手順に従います[、Intune アプリ SDK を統合する](app-sdk-android.md)詳細については、このドキュメントを参照しながら Android モバイル アプリにします。

### <a name="xamarinandroid-integration"></a>Xamarin.Android の統合

Intune アプリ SDK を統合するための完全な概要が記載されて、 [Android 開発者ガイド用の Microsoft Intune アプリ SDK](app-sdk-android.md)します。 番組ガイドを読んで、Xamarin アプリで Intune アプリ SDK を統合すると次のセクションでは、Java で開発されたネイティブの Android アプリで開発された Xamarin アプリの実装の違いを強調表示するためのものがC#します。 これらのセクションでは、補足として扱う必要があるし、ガイド全体を読み取るための代替として機能できません。

#### <a name="renamed-methodsapp-sdk-androidmdrenamed-methods"></a>[名前が変更されたメソッド](app-sdk-android.md#renamed-methods)
多くの場合、Android のクラスで使用できるメソッドが、MAM の置換クラスで最終版としてマークされています。 この場合、MAM 置換クラスによって、似た名前のメソッド (`MAM` というサフィックスが付いている) が提供され、これをオーバーライドする必要があります。 たとえば、`MAMActivity` から派生する場合は、`OnCreate()` をオーバーライドして `base.OnCreate()` を呼び出すのではなく、`Activity` で `OnMAMCreate()` をオーバーライドし、`base.OnMAMCreate()` を呼び出す必要があります。

#### <a name="mam-applicationapp-sdk-androidmdmamapplication"></a>[MAM アプリケーション](app-sdk-android.md#mamapplication)
アプリを定義する必要があります、`Android.App.Application`クラスから継承する`MAMApplication`します。 必ずサブクラスを `[Application]` 属性で適切に修飾し、`(IntPtr, JniHandleOwnership)` コンストラクターをオーバーライドします。
```csharp
    [Application]
    class TaskrApp : MAMApplication
    {
    public TaskrApp(IntPtr handle, JniHandleOwnership transfer)
        : base(handle, transfer) { }
```
> [!NOTE]
> MAM の Xamarin バインドの問題には、アプリケーションがデバッグ モードで配置するときにクラッシュする可能性があります。 回避策として、`Debuggable=false`に属性を追加する必要があります、`Application`クラスおよび`android:debuggable="true"`フラグは、手動で設定されている場合、マニフェストから削除する必要があります。

#### <a name="enable-features-that-require-app-participationapp-sdk-androidmdenable-features-that-require-app-participation"></a>[アプリによる処理を必要とする機能の有効化](app-sdk-android.md#enable-features-that-require-app-participation)
例: PIN がアプリケーションに必要なかどうかを確認します。
```csharp
MAMPolicyManager.GetPolicy(currentActivity).IsPinRequired;
```
例: プライマリ Intune ユーザーを判別します。
```csharp
IMAMUserInfo info = MAMComponents.Get<IMAMUserInfo>();
return info?.PrimaryUser;
```
例: デバイスまたはクラウド ストレージへの保存が許可されているかどうかを判断します。
```csharp
MAMPolicyManager.GetPolicy(currentActivity).GetIsSaveToLocationAllowed(SaveLocation service, String username);
```

#### <a name="register-for-notifications-from-the-sdkapp-sdk-androidmdregister-for-notifications-from-the-sdk"></a>[SDK からの通知への登録](app-sdk-android.md#register-for-notifications-from-the-sdk)
アプリは、`MAMNotificationReceiver` を作成して `MAMNotificationReceiverRegistry` に登録することで、SDK からの通知に登録する必要があります。 これは、次の例に示すように、受信側と、`App.OnMAMCreate` で必要な通知の種類を指定することで行います。
```csharp
public override void OnMAMCreate()
{
    // Register the notification receivers
    IMAMNotificationReceiverRegistry registry = MAMComponents.Get<IMAMNotificationReceiverRegistry>();
    foreach (MAMNotificationType notification in MAMNotificationType.Values())
    {
    registry.RegisterReceiver(new ToastNotificationReceiver(this), notification);
    }
    ...
```

#### <a name="mam-enrollment-managerapp-sdk-androidmdmamenrollmentmanager"></a>[MAM 登録マネージャー](app-sdk-android.md#mamenrollmentmanager)
```csharp
IMAMEnrollmentManager mgr = MAMComponents.Get<IMAMEnrollmentManager>();
```

### <a name="xamarinforms-integration"></a>Xamarin.Forms の統合

`Xamarin.Forms`アプリケーションが用意されています、`Microsoft.Intune.MAM.Remapper`を挿入することで自動的に MAM に代わってクラス置換を実行するパッケージ`MAM`クラスの階層構造によく使用されるクラス`Xamarin.Forms`クラス。 

> [!NOTE]
> Xamarin.Forms の統合は、また上述 Xamarin.Android 統合するためには。

プロジェクトに追加すると、Remapper MAM の同等の置換を実行する必要があります。 たとえば、`FormsAppCompatActivity`と`FormsApplicationActivity`に用意されているアプリケーションは使用を続行できます`OnCreate`と`OnResume`は同等の MAM に置き換えられます`OnMAMCreate`と`OnMAMResume`それぞれします。

```csharp
    public class MainActivity : global::Xamarin.Forms.Platform.Android.FormsAppCompatActivity
    {
        protected override void OnMAMCreate(Bundle savedInstanceState)
        {
            base.OnMAMCreate(savedInstanceState);
            global::Xamarin.Forms.Forms.Init(this, savedInstanceState);
            LoadApplication(new App());
        }
```
置換が行われていない場合、置換を行うまで、次のコンパイル エラーを発生可能性があります。
* [コンパイラ エラー CS0239](https://docs.microsoft.com/dotnet/csharp/misc/cs0239):  このエラーは次の形式でよく見られます: 「``'MainActivity.OnCreate(Bundle)': cannot override inherited member 'MAMAppCompatActivityBase.OnCreate(Bundle)' because it is sealed``」。
これは Remapper によって Xamarin クラスの継承が変更されるために発生する可能性があり、特定の関数が `sealed` になり、代わりにオーバーライドするための新しい MAM バリアントが追加されます。
* [コンパイラ エラー CS0507](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0507): このエラーは、このフォームでよく見られます``'MyActivity.OnRequestPermissionsResult()' cannot change access modifiers when overriding 'public' inherited member ...``します。 Remapper によっていくつかの Xamarin クラスの継承が変更されるときに、特定のメンバー関数が `public` に変更されます。 これらの関数をオーバーライドする場合は、これらのアクセス修飾子をオーバーライドする設定を変更する必要があります。`public`もします。

> [!NOTE]
> Remapper IntelliSense オート コンプリートに Visual Studio を使用する依存関係を再書き込みします。 そのため、再読み込みして、IntelliSense の変更が正しく認識するため、Remapper が追加されたときに、プロジェクトをリビルドする必要があります。

## <a name="support"></a>Support
組織が Intune の既存顧客の場合、Microsoft サポートの担当者と共にサポート チケットを開き、[Github の問題ページ](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/issues)で問題を作成してください。Microsoft ができるだけ早くサポートを提供します。 
