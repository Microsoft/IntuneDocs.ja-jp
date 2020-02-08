---
title: Microsoft Intune App SDK Xamarin バインディング
description: Intune App SDK Xamarin バインディングを利用すると、Xamarin でビルドされた iOS アプリと Android アプリで Intune アプリ保護ポリシーが有効になります。
keywords: sdk, Xamarin, intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/04/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 275d574b-3560-4992-877c-c6aa480717f4
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: 10f3d4c54d9a8fcb797ae3359b1a833ac9080548
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912701"
---
# <a name="microsoft-intune-app-sdk-xamarin-bindings"></a>Microsoft Intune App SDK Xamarin バインディング

> [!NOTE]
> 最初に、[Intune アプリ SDK の概要](app-sdk-get-started.md)に関する記事に目を通すことをお勧めします。このガイドでは、サポートする各プラットフォームで統合のための準備をする方法について説明しています。

## <a name="overview"></a>概要
[Intune App SDK Xamarin バインディング](https://github.com/msintuneappsdk/intune-app-sdk-xamarin)を利用すると、Xamarin でビルドされた iOS アプリと Android アプリで [Intune アプリ保護ポリシー](../apps/app-protection-policy.md)が有効になります。 このバインディングを利用すると、開発者は Intune のアプリ保護機能を Xamarin ベースのアプリに簡単に組み込むことができます。

Microsoft Intune App SDK Xamarin バインディングを利用すると、Intune アプリ保護ポリシー (別名、APP または MAM ポリシー) を Xamarin で開発したアプリに組み込むことができます。 MAM 対応のアプリケーションが Intune アプリ SDK に統合されています。 Intune で積極的にアプリを管理している場合、IT 管理者はモバイル アプリにアプリ保護ポリシーを展開できます。

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

## <a name="prerequisites"></a>[前提条件]

[ライセンス条項](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/blob/master/Microsoft%20License%20Terms%20Intune%20App%20SDK%20Xamarin%20Component.pdf)を確認します。 記録用にライセンス条項を印刷し、保持します。 Intune App SDK Xamarin バインディングをダウンロードし、使用すると、このライセンス条項に同意したことになります。 本ライセンス条項に同意されない場合、本ソフトウェアを使用することはできません。

Intune SDK では、その[認証](https://azure.microsoft.com/documentation/articles/active-directory-authentication-scenarios/)と条件付き起動シナリオを [Active Directory 認証ライブラリ (ADAL)](https://azure.microsoft.com/documentation/articles/active-directory-authentication-libraries/) に依存しているため、[Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-whatis/) を使用してアプリを構成する必要があります。 

アプリケーションが ADAL または MSAL を使用するように既に構成されており、独自のカスタム クライアント ID が Azure Active Directory での認証に利用される場合は、Intune モバイル アプリケーション管理 (MAM) サービスへのアクセス許可を Xamarin アプリに付与するための手順に従っていることを確認します。 [Intune SDK の概要ガイド](app-sdk-get-started.md#give-your-app-access-to-the-intune-app-protection-service-optional)の[アプリに対する Intune アプリ保護サービスへのアクセス権の付与](app-sdk-get-started.md)に関するセクションに記載されている手順を使用します。

## <a name="security-considerations"></a>セキュリティに関する考慮事項

スプーフィング、情報漏えい、および権限の昇格攻撃の可能性を抑制するには、次の手順に従います。

* Xamarin アプリの開発が、セキュリティで保護されたワーク ステーションで確実に行われるようにします。
* バインドが有効な Microsoft ソースからのものであることを確実にします。
  * [MS Intune App SDK の NuGet プロファイル](https://www.nuget.org/profiles/msintuneappsdk)
  * [Intune App SDK Xamarin の GitHub リポジトリ](https://github.com/msintuneappsdk/intune-app-sdk-xamarin)
* プロジェクトの NuGet 構成を、署名済みの変更されていない NuGet パッケージを信頼するように構成します。
詳細については、[署名済みパッケージのインストール](https://docs.microsoft.com/nuget/consume-packages/installing-signed-packages)に関するページを参照してください。
* Xamarin アプリを含む出力ディレクトリをセキュリティで保護します。 出力にユーザー レベルのディレクトリを使用することを検討します。


## <a name="enabling-intune-app-protection-polices-in-your-ios-mobile-app"></a>iOS モバイル アプリで Intune アプリ保護ポリシーを有効にする
1. [Microsoft.Intune.MAM.Xamarin.iOS NuGet パッケージ](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.iOS)を Xamarin.iOS プロジェクトに追加します。
2. iOS モバイル アプリに Intune App SDK を統合するのに必要な、一般的な手順に従います。 [iOS 用 Intune App SDK 開発者ガイド](app-sdk-ios.md#build-the-sdk-into-your-mobile-app)にある統合の手順 (手順 3) から開始できます。 IntuneMAMConfigurator を実行するセクションの最後の手順は、省略できます。このツールは Microsoft.Intune.MAM.Xamarin.iOS パッケージに含まれており、ビルド時に自動的に実行されるからです。
    **重要**:Visual Studio と Xcode とでは、アプリのキーチェーンの共有を有効にする方法が少し異なります。 アプリの Entitlements plist を開き、[キーチェーンを有効にする] オプションが有効になっていることと、適切なキーチェーンの共有グループがそのセクションに追加されていることを確認します。 次に、すべての構成およびプラットフォームの適切な組み合わせに対して、プロジェクトの [iOS バンドル署名] オプションの [カスタム エンタイトルメント] フィールドに、その Entitlements plist が指定されていることを確認します。
3. バインディングが追加され、アプリが正しく構成されると、お使いのアプリで Intune SDK の API を使用できるようになります。 これを行うには、次の名前空間を含める必要があります。

      ```csharp
      using Microsoft.Intune.MAM;
      ```

4. アプリ保護ポリシーを受信するには、Intune MAM サービスにアプリを登録する必要があります。 アプリがユーザーの認証に [Azure Active Directory Authentication Library](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) (ADAL) または [Microsoft Authentication Library](https://www.nuget.org/packages/Microsoft.Identity.Client) (MSAL) を使用しておらず、Intune SDK で認証を処理したい場合、アプリは IntuneMAMEnrollmentManager の LoginAndEnrollAccount メソッドにユーザーの UPN を提供する必要があります:

      ```csharp
       IntuneMAMEnrollmentManager.Instance.LoginAndEnrollAccount([NullAllowed] string identity);
      ```

      呼び出し時にユーザーの UPN が不明な場合、アプリは null を渡すことがあります。 この場合、ユーザーはメール アドレスとパスワードの両方を入力するよう求められます。
      
      アプリが既に ADAL または MSAL を使用してユーザーを認証している場合は、アプリと Intune SDK 間のシングルサインオン (SSO) エクスペリエンスを構成できます。 まず、Intune SDK で使用される既定の AAD 設定を、使用するアプリの設定でオーバーライドする必要があります。 これを行うには、[iOS 用 Intune App SDK 開発者ガイド](app-sdk-ios.md#configure-settings-for-the-intune-app-sdk)で説明しているように、アプリの Info.plist 内にある IntuneMAMSettings ディクショナリを利用できます。または、IntuneMAMSettings クラスの AAD のオーバーライド プロパティを使用し、コードでこれを実行することもできます。 ADAL 設定が静的なアプリケーションでは Info.plist を使用する方法をお勧めしますが、実行時にその値が決定されるアプリケーションでは override プロパティをお勧めします。 すべての SSO 設定が構成されたら、アプリが正常に認証された後、IntuneMAMEnrollmentManager の RegisterAndEnrollAccount メソッドにユーザーの UPN を指定する必要があります。

      ```csharp
      IntuneMAMEnrollmentManager.Instance.RegisterAndEnrollAccount(string identity);
      ```

      アプリは、IntuneMAMEnrollmentDelegate のサブクラスに EnrollmentRequestWithStatus メソッドを実装し、IntuneMAMEnrollmentManager の Delegate プロパティをそのクラスのインスタンスに設定することで、登録試行の結果を判断できます。 

      登録が成功すると、アプリケは次のプロパティのクエリを実行することで、登録されているアカウント (以前は不明だった場合) の UPN を特定できます。 

      ```csharp
       string enrolledAccount = IntuneMAMEnrollmentManager.Instance.EnrolledAccount;
      ```      
### <a name="sample-applications"></a>サンプル アプリケーション
Xamarin.iOS アプリの MAM 機能を強調表示したサンプル アプリケーションは、[GitHub](https://github.com/msintuneappsdk/sample-intune-xamarin-ios) から入手できます。

> [!NOTE] 
> iOS 用の remapper はありません。 Xamarin.Forms アプリへの統合は、通常の Xamarin.iOS プロジェクトと同様に行います。 

## <a name="enabling-intune-app-protection-policies-in-your-android-mobile-app"></a>Android モバイル アプリで Intune のアプリ保護ポリシーを有効にする
1. [Microsoft.Intune.MAM.Xamarin.Android NuGet パッケージ](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.Android)を Xamarin.Android プロジェクトに追加します。
    1. Xamarin.Forms アプリの場合は、[Microsoft.Intune.MAM.Remapper.Tasks NuGet パッケージ](https://www.nuget.org/packages/Microsoft.Intune.MAM.Remapper.Tasks)も Xamarin.Android プロジェクトに追加します。 
2. 詳細についてこのドキュメントを参照しながら、Android モバイル アプリへの [Intune App SDK の統合](app-sdk-android.md)に必要な一般的な手順に従います。

### <a name="xamarinandroid-integration"></a>Xamarin.Android の統合

Intune App SDK を統合するための完全な概要については、「[Microsoft Intune App SDK for Android developer guide](app-sdk-android.md)」 (Android 用 Microsoft Intune App SDK 開発者ガイド) を参照してください。 ガイドに目を通して、Intune App SDK をご利用の Xamarin アプリに統合するときに、Java で開発されたネイティブの Android アプリと、C# で開発された Xamarin アプリでは実装に違いがあり、以降のセクションは、それを明らかにすることを目的としています。 これらのセクションは、補足情報として扱うべきもので、ガイド全体に目を通すことの代わりとなるものではありません。

#### <a name="remapper"></a>Remapper
1\.4428.1 リリース以降、MAM クラス、メソッド、システム サービスの置換を実行するための[ビルド ツール](app-sdk-android.md#build-tooling)として、`Microsoft.Intune.MAM.Remapper` パッケージを Xamarin Android アプリケーションに追加できるようになりました。 Remapper が含まれている場合、「名前が変更されたメソッド」と「MAM アプリケーション」セクションの MAM に相当する置換部分は、アプリケーションのビルド時に自動的に実行されます。

Remapper によって MAM-ification からクラスを除外するには、次のプロパティを自分のプロジェクトの `.csproj` ファイルに追加します。

```xml
  <PropertyGroup>
    <ExcludeClasses>Semicolon separated list of relative class paths to exclude from MAM-ification</ExcludeClasses>
  </PropertyGroup>
```

> [!NOTE]
> 現在、Remapper では、Xamarin Android アプリでのデバッグを禁止しています。 アプリケーションをデバッグするには、手動で統合することをお勧めします。

#### <a name="renamed-methodsapp-sdk-androidmdrenamed-methods"></a>[名前が変更されたメソッド](app-sdk-android.md#renamed-methods)
多くの場合、Android のクラスで使用できるメソッドが、MAM の置換クラスで最終版としてマークされています。 この場合、MAM 置換クラスによって、似た名前のメソッド (`MAM` というサフィックスが付いている) が提供され、これをオーバーライドする必要があります。 たとえば、`MAMActivity` から派生する場合は、`OnCreate()` をオーバーライドして `base.OnCreate()` を呼び出すのではなく、`Activity` で `OnMAMCreate()` をオーバーライドし、`base.OnMAMCreate()` を呼び出す必要があります。

#### <a name="mam-applicationapp-sdk-androidmdmamapplication"></a>[MAM アプリケーション](app-sdk-android.md#mamapplication)
アプリで `Android.App.Application` クラスを定義する必要があります。 MAM を手動で統合する場合は、`MAMApplication` から継承する必要があります。 必ずサブクラスを `[Application]` 属性で適切に修飾し、`(IntPtr, JniHandleOwnership)` コンストラクターをオーバーライドします。

```csharp
    [Application]
    class TaskrApp : MAMApplication
    {
    public TaskrApp(IntPtr handle, JniHandleOwnership transfer)
        : base(handle, transfer) { }
```

> [!NOTE]
> MAM の Xamarin バインドの問題により、アプリケーションをデバッグ モードで展開したときにクラッシュする可能性があります。 回避策として、`Debuggable=false` 属性を `Application` クラスに追加して、`android:debuggable="true"` フラグをマニフェストから削除 (手動で設定されている場合) する必要があります。

#### <a name="enable-features-that-require-app-participationapp-sdk-androidmdenable-features-that-require-app-participation"></a>[アプリによる処理を必要とする機能の有効化](app-sdk-android.md#enable-features-that-require-app-participation)
例:PIN がアプリケーションに必要なかどうかを確認する

```csharp
MAMPolicyManager.GetPolicy(currentActivity).IsPinRequired;
```

例:プライマリ Intune ユーザーを判別する

```csharp
IMAMUserInfo info = MAMComponents.Get<IMAMUserInfo>();
return info?.PrimaryUser;
```

例:デバイスまたはクラウド ストレージへの保存が許可されているかどうかを判断する

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

`Xamarin.Forms` アプリケーションの場合、一般的に使用されている `Xamarin.Forms` クラスのクラス階層に `MAM` クラスを挿入することで、`Microsoft.Intune.MAM.Remapper` パッケージによって MAM クラスの置き換えが自動的に実行されます。 

> [!NOTE]
> Xamarin.Forms の統合は、前述した Xamarin.Android 統合に加えて行われる必要があります。 Remapper の動作は、Xamarin.Forms アプリによって異なります。そのため、手動による MAM の置換を引き続き行う必要があります。

Remapper をプロジェクトに追加すると、MAM に相当する置換を実行する必要があります。 たとえば、`FormsAppCompatActivity` と `FormsApplicationActivity` は、`OnCreate` と `OnResume` へのオーバーライドが MAM に相当する `OnMAMCreate` と `OnMAMResume` にそれぞれ置き換えられた場合は、引き続き使用することができます。

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

置換が行われていない場合は、置換を行うまで次のコンパイル エラーが発生する可能性があります。
* [コンパイラ エラー CS0239](https://docs.microsoft.com/dotnet/csharp/misc/cs0239): このエラーは次の形式でよく見られます: 「``'MainActivity.OnCreate(Bundle)': cannot override inherited member 'MAMAppCompatActivityBase.OnCreate(Bundle)' because it is sealed``」。
これは Remapper によって Xamarin クラスの継承が変更されるために発生する可能性があり、特定の関数が `sealed` になり、代わりにオーバーライドするための新しい MAM バリアントが追加されます。
* [コンパイラ エラー CS0507](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0507):このエラーは次の形式でよく見られます: 「``'MyActivity.OnRequestPermissionsResult()' cannot change access modifiers when overriding 'public' inherited member ...``」。 Remapper によっていくつかの Xamarin クラスの継承が変更されるときに、特定のメンバー関数が `public` に変更されます。 これらの関数のいずれかをオーバーライドする場合は、これらのオーバーライドのアクセス修飾子も同じく `public` に変更する必要があります。

> [!NOTE]
> Remapper により、Visual Studio で IntelliSense のオートコンプリートに使用する依存関係が再度書き込まれます。 そのため、変更が正しく認識されるように IntelliSense に Remapper が追加されるときに、場合によっては、プロジェクトを再度読み込んでリビルドする必要があります。

#### <a name="troubleshooting"></a>トラブルシューティング
* 起動時にアプリケーションで空白の白い画面が表示された場合は、メイン スレッドでナビゲーション呼び出しを強制的に実行する必要がある場合があります。
* Intune SDK Xamarin バインディングでは、MvvmCross と Intune MAM クラス間の競合のため、MvvmCross などのクロスプラットフォーム フレームワークを使用しているアプリはサポートされません。 一部のお客様はアプリをプレーンな Xamarin.Forms に移行した後に、統合に成功されている可能性がありますが、MvvmCross を使用するアプリ開発者に向けた明示的なガイダンスやプラグインは提供されません。

### <a name="company-portal-app"></a>ポータル サイト アプリ
Intune SDK Xamarin バインディングでアプリ保護ポリシーを有効にするには、デバイスに[ポータル サイト](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) Android アプリが存在する必要があります。 ポータル サイトは、Intune サービスからアプリ保護ポリシーを取得します。 アプリが初期化されるときに、ポータル サイトからポリシーとコードを読み込み、そのポリシーを適用します。 ユーザーはサインインする必要はありません。

> [!NOTE]
> ポータル サイト アプリが **Android** デバイス上にない場合、Intune で管理されているアプリは、Intune アプリ保護ポリシーをサポートしていない通常のアプリと同様に動作します。

デバイス登録が不要なアプリ保護の場合は、ユーザーがポータル サイト アプリを使用してデバイスを登録する必要は _**ありません**_ 。

### <a name="sample-applications"></a>サンプル アプリケーション
Xamarin Android アプリと Xamarin. Forms アプリの MAM 機能を強調表示したサンプル アプリケーションは、[GitHub](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Xamarin-Android-Apps) から入手できます。

## <a name="support"></a>サポート
お客様の組織が既に Intune をご利用の場合は、Microsoft のサポート担当者と連携してサポート チケットを開き、[GitHub のイシュー ページで](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/issues)イシューを作成してください。 できるだけ早くお手伝いします。 
