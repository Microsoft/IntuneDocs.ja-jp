---
title: Microsoft Intune App SDK Xamarin バインディング
description: Intune App SDK Xamarin バインディングを利用すると、Xamarin でビルドされた iOS アプリと Android アプリで Intune アプリ保護ポリシーが有効になります。
keywords: sdk, Xamarin, intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/16/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 275d574b-3560-4992-877c-c6aa480717f4
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.openlocfilehash: a698d7a57c59a27dbd39036b1e2607e80570029f
ms.sourcegitcommit: 513c59a23ca5dfa80a3ba6fc84068503a4158757
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/11/2019
ms.locfileid: "54210773"
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
    **重要**:Visual Studio と Xcode とでは、アプリのキーチェーンの共有を有効にする方法が少し異なります。 アプリの Entitlements plist を開き、[キーチェーンを有効にする] オプションが有効になっていることと、適切なキーチェーンの共有グループがそのセクションに追加されていることを確認します。 次に、すべての構成およびプラットフォームの適切な組み合わせに対して、プロジェクトの [iOS バンドル署名] オプションの [カスタム エンタイトルメント] フィールドに、その Entitlements plist が指定されていることを確認します。
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

UI フレームワークを利用しない Xamarin 基盤の Android アプリの場合、「[Android 用 Intune アプリ SDK 開発者ガイド](app-sdk-android.md)」をお読みいただき、それに沿う必要があります。 Xamarin ベースの Android アプリの場合、ガイドに含まれている[クラスとメソッドの置換に関する表](app-sdk-android.md#class-and-method-replacements)に基づいて、クラス、メソッド、アクティビティをその MAM の同等のものと置換する必要があります。 アプリで `android.app.Application` クラスが定義されない場合、それを作成し、`MAMApplication` から継承するように設定する必要があります。 ADAL の構成値は、AndroidManifest メタデータを使用して SDK に伝達されます。 [お使いのアプリへの ADAL の構成](app-sdk-android.md#configure-azure-active-directory-authentication-library-adal)に関するドキュメントを参照してください。

### <a name="xamarinandroid-integration"></a>Xamarin.Android の統合

1. [Microsoft.Intune.MAM.Xamarin.Android NuGet パッケージ](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.Android)の最新バージョンを Xamarin.Android プロジェクトに追加します。 これにより、Intune がアプリケーションを有効にするために必要な参照が提供されます。

2. [Android 用 Microsoft Intune アプリ SDK 開発者ガイド](app-sdk-android.md)をよく読み、その内容に従ってください。特に、次の内容に注意してください。

    1. [クラスとメソッド全体の置き換えに関するセクション](app-sdk-android.md#class-and-method-replacements)。 
    2. [MAMApplication のセクション](app-sdk-android.md#mamapplication)。 必ずサブクラスを `[Application]` 属性で適切に修飾し、`(IntPtr, JniHandleOwnership)` コンストラクターをオーバーライドします。
    3. アプリが AAD に対して認証を実行する場合は、[ADAL の統合に関するセクション](app-sdk-android.md#configure-azure-active-directory-authentication-library-adal)。 
    4. アプリケーションの MAM サービスからポリシーを取得する予定の場合は、[MAM-WE の登録に関するセクション](app-sdk-android.md#app-protection-policy-without-device-enrollment)。

> [!NOTE]
> `Microsoft.Intune.MAM.Xamarin.Android` バインディングで [Android 用 Microsoft Intune アプリ SDK 開発者ガイド](app-sdk-android.md)の同等の API を見つけるとき、あるいはこのガイドのコード変換スニペットを見つけるとき、Xamarin のバインディング ジェネレーターによって次のような目立つ方法で Android API が修飾されることにご注意ください。
> * すべての識別子が Pascal 表記に変換される (com.foo.bar -> Com.Foo.Bar)。
> * すべての get/set 操作がプロパティ操作に変換される (例: Foo.getBar() -> Foo.Bar、Foo.setBar("zap") -> Foo.Bar = "zap")
> * すべてのインターフェイスで、名前の前に 'I' という文字が付けられる (FooInterface -> IFooInterface)

### <a name="xamarinforms-integration"></a>Xamarin.Forms の統合

`Xamarin.Forms` アプリケーションの場合、**上記のすべての手順を実行するだけでなく**、`Microsoft.Intune.MAM.Remapper` パッケージも使用します。 このパッケージは、`FormsAppCompatActivity` や `FormsApplicationActivity` のように一般的に使用される `Xamarin.Forms` クラスのクラス階層に `MAM` クラスを挿入することでクラスの置換を実行します。その結果、`OnMAMCreate` や `OnMAMResume` などの MAM の相当する関数のオーバーライドが提供されるので、これらのクラスを引き続き使用できます。 これを使う場合は、以下の手順に従います。

1.  [Microsoft.Intune.MAM.Remapper.Tasks](https://www.nuget.org/packages/Microsoft.Intune.MAM.Remapper.Tasks) NuGet パッケージを自分のプロジェクトに追加します。 Intune APP SDK Xamarin のバインディングをまだ追加していない場合は、自動的に追加されます。

2.  前述の手順 2.2 で作成した `MAMApplication` クラスの `OnMAMCreate` 関数に `Xamarin.Forms.Forms.Init(Context, Bundle)` の呼び出しを追加します。 Intune 管理を使用してアプリケーションがバックグラウンドで起動される可能性があるため、この処理が必要です。

> [!NOTE]
> この操作で、Visual Studio が Intellisense のオートコンプリートに使用する依存関係が書き換えられるため、Intellisense に変更を正しく認識させるには、remapper を初めて実行した後は Visual Studio を再起動する必要があります。 

コンポーネントをアプリに組み込む基本的な手順を完了しました。 これで、Xamarin Android サンプル アプリに含まれている手順を実行できます。 サンプルは 2 つあります。Xamarin.Forms 用が 1 つ、Android 用が 1 つです。

## <a name="requiring-intune-app-protection-policies-in-order-to-use-your-xamarin-based-android-lob-app-optional"></a>Xamarin ベースの Android LOB アプリを使用するために Intune アプリ保護ポリシーを必須にする (省略可能) 

以下のガイダンスは、デバイス上の Intune で保護されたユーザーのみが Xamarin ベースの Android LOB アプリを使用できるようにするためのものです。 
    
### <a name="working-with-the-intune-sdk"></a>Intune SDK の使用
これらの手順は、エンド ユーザー デバイスで使用するために Intune アプリ保護ポリシーが必要なすべての Android および Xamarin アプリ向けです。

1. [Android 用 Intune SDK ガイド](app-sdk-android.md#configure-azure-active-directory-authentication-library-adal)のセクションで定義されている手順を使用して ADAL を構成します。
> [!NOTE] 
> "クライアント ID" という用語は、アプリに関連付けられている Azure portal の用語 "アプリケーション ID" と同じです。 
* SSO を有効にするには、「ADAL の一般的な構成」の 2. が必要です。

2. マニフェストに次の値を入力して、既定の登録を有効にします。```xml <meta-data android:name="com.microsoft.intune.mam.DefaultMAMServiceEnrollment" android:value="true" />```
> [!NOTE] 
> これは、アプリ内での唯一の MAM-WE 統合である必要があります。 MAMEnrollmentManager API を呼び出す他の試行がある場合、競合が発生する可能性があります。

3. マニフェストに次の値を入力して、必要な MAM ポリシーを有効にします。```xml <meta-data android:name="com.microsoft.intune.mam.MAMPolicyRequired" android:value="true" />```
> [!NOTE] 
> これにより、使用前に、アプリによってデバイスにポータル サイトがダウンロードされ、既定の登録フローが完了します。

### <a name="working-with-adal"></a>ADAL の操作
これらの手順は、エンド ユーザー デバイスで使用するために Intune アプリ保護ポリシーが必要な .NET/Xamarin アプリの要件です。

1. ADAL ドキュメントの「[Brokered Authentication for Android](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet/tree/dev/adal#brokered-authentication-for-android)」(Android 用の仲介型認証) に定義されているすべての手順に従います。
> [!NOTE] 
> .NET ADAL が次にリリースするバージョン (3.17.4) には、それを機能させるために必要な修正プログラムが含められる予定です。

## <a name="support"></a>Support
組織が Intune の既存顧客の場合、Microsoft サポートの担当者と共にサポート チケットを開き、[Github の問題ページ](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/issues)で問題を作成してください。Microsoft ができるだけ早くサポートを提供します。 
