---
title: Microsoft Intune App SDK Xamarin バインディング
description: Intune App SDK Xamarin バインディングを利用すると、Xamarin でビルドされた iOS アプリと Android アプリで Intune アプリ保護ポリシーが有効になります。
keywords: sdk, Xamarin, intune
author: Erikre
manager: dougeby
ms.author: erikre
ms.date: 03/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 275d574b-3560-4992-877c-c6aa480717f4
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 5c9f81761e7e24393471f44da4cf619f017e9bbd
ms.sourcegitcommit: 4c06fa8e9932575e546ef2e880d96e96a0618673
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="microsoft-intune-app-sdk-xamarin-bindings"></a>Microsoft Intune App SDK Xamarin バインディング

> [!NOTE]
> 最初に、[Intune アプリ SDK の概要](app-sdk-get-started.md)に関する記事に目を通すことをお勧めします。このガイドでは、サポートする各プラットフォームで統合のための準備をする方法について説明しています。

## <a name="overview"></a>概要
[Intune App SDK Xamarin バインディング](https://github.com/msintuneappsdk/intune-app-sdk-xamarin)を利用すると、Xamarin でビルドされた iOS アプリと Android アプリで [Intune アプリ保護ポリシー](/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)が有効になります。 このバインディングを利用すると、開発者は Intune のアプリ保護機能を Xamarin ベースのアプリに簡単に組み込むことができます。

Microsoft Intune App SDK Xamarin バインディングを利用すると、Intune アプリ保護ポリシー (別名、APP または MAM ポリシー) を Xamarin で開発したアプリに組み込むことができます。 MAM 対応のアプリケーションが Intune App SDK に統合されています。 Intune で積極的にアプリを管理している場合、IT 管理者はモバイル アプリにアプリ保護ポリシーを展開できます。

## <a name="whats-supported"></a>サポートされる内容

### <a name="developer-machines"></a>開発者のコンピューター
* Windows
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

## <a name="enabling-intune-app-protection-polices-in-your-ios-mobile-app"></a>iOS モバイル アプリで Intune アプリ保護ポリシーを有効にする
1. [Microsoft.Intune.MAM.Xamarin.iOS NuGet パッケージ](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.iOS)を Xamarin.iOS プロジェクトに追加します。
2.  iOS モバイル アプリに Intune App SDK を統合するのに必要な、一般的な手順に従います。 [iOS 用 Intune App SDK 開発者ガイド](app-sdk-ios.md#build-the-sdk-into-your-mobile-app)にある統合の手順 (手順 3) から開始できます。 IntuneMAMConfigurator を実行するセクションの最後の手順は、省略できます。このツールは Microsoft.Intune.MAM.Xamarin.iOS パッケージに含まれており、ビルド時に自動的に実行されるからです。
    **重要**: Visual Studio と Xcode とでは、アプリのキーチェーンの共有を有効にする方法が少し異なります。 アプリの Entitlements plist を開き、[キーチェーンを有効にする] オプションが有効になっていることと、適切なキーチェーンの共有グループがそのセクションに追加されていることを確認します。 次に、すべての構成およびプラットフォームの適切な組み合わせに対して、プロジェクトの [iOS バンドル署名] オプションの [カスタム エンタイトルメント] フィールドに、その Entitlements plist が指定されていることを確認します。
3.  バインディングが追加され、アプリが正しく構成されると、お使いのアプリで Intune SDK の API を使用できるようになります。 これを行うには、次の名前空間を含める必要があります。

      ```csharp
      using Microsoft.Intune.MAM;
      ```
4. アプリ保護ポリシーを受信するには、Intune MAM サービスにアプリを登録する必要があります。 お使いのアプリで、Azure Active Directory 認証ライブラリ (ADAL) を使用したユーザー認証を既に行っている場合、認証が成功した後に IntuneMAMEnrollmentManager の registerAndEnrollAccount メソッドに対して、ユーザーの UPN を渡す必要があります。
      ```csharp
      IntuneMAMEnrollmentManager.Instance.RegisterAndEnrollAccount(string identity);
      ```
      **重要**: Intune APP SDK の既定の ADAL 設定を、お使いのアプリの設定で上書きしてください。 これを行うには、[iOS 用 Intune App SDK 開発者ガイド](app-sdk-ios.md#configure-settings-for-the-intune-app-sdk)で説明しているように、アプリの Info.plist 内にある IntuneMAMSettings ディクショナリを利用できます。または IntuneMAMPolicyManager インスタンスで AAD の override プロパティを使用することも可能です。 ADAL 設定が静的なアプリケーションでは Info.plist を使用する方法をお勧めしますが、実行時にその値が決定されるアプリケーションでは override プロパティをお勧めします。 
      
      アプリで ADAL を使用せず、Intune SDK で認証を処理する場合は、アプリで IntuneMAMEnrollmentManager の loginAndEnrollAccount メソッドを呼び出す必要があります。
      ```csharp
       IntuneMAMEnrollmentManager.Instance.LoginAndEnrollAccount([NullAllowed] string identity);
      ```

## <a name="enabling-intune-app-protection-policies-in-your-android-mobile-app"></a>Android モバイル アプリで Intune のアプリ保護ポリシーを有効にする

### <a name="xamarinandroid-integration"></a>Xamarin.Android の統合

1. [Microsoft.Intune.MAM.Xamarin.Android NuGet パッケージ](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.Android)の最新バージョンを Xamarin.Android プロジェクトに追加します。 これにより、Intune がアプリケーションを有効にするために必要な参照が提供されます。

2. [Android 用 Microsoft Intune アプリ SDK 開発者ガイド](app-sdk-android.md)をよく読み、その内容に従ってください。特に、次の内容に注意してください。
    1. [クラスとメソッド全体の置き換えに関するセクション](app-sdk-android.md#replace-classes-methods-and-activities-with-their-mam-equivalent)。 
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

## <a name="support"></a>Support

組織が Intune の既存顧客の場合、Microsoft サポートの担当者と共にサポート チケットを開き、[Github の問題ページ](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/issues)で問題を作成してください。Microsoft ができるだけ早くサポートを提供します。 