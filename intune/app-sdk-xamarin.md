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
ms.openlocfilehash: 9f9cc117925f59c9fb7c55d0ff10aedf09d26f93
ms.sourcegitcommit: b727b6bd6f138c5def7ac7bf1658068db30a0ec3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2018
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

## <a name="enabling-app-protection-policies-in-your-android-mobile-app"></a>Android モバイル アプリでアプリ保護ポリシーを有効にする
[Microsoft.Intune.MAM.Xamarin.Android NuGet パッケージ](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.Android)を Xamarin.Android プロジェクトに追加します。

Xamarin.Android アプリの場合、[Android 用 Microsoft Intune アプリ SDK 開発者ガイド](app-sdk-android.md)を読み、すべてこのガイドどおりに行う必要があります。たとえば、クラス、メソッド、アクティビティを、このガイドに含まれている[表](app-sdk-android.md#replace-classes-methods-and-activities-with-their-mam-equivalent)を基づき、MAM のクラス、メソッド、アクティビティに置換します。 

> [!NOTE]
> アプリで `android.app.Application` クラスが定義されない場合、それを作成し、`MAMApplication` から継承するように設定する必要があります。

> [!NOTE]
> `Microsoft.Intune.MAM.Xamarin.Android` バインディングで [Android 用 Microsoft Intune アプリ SDK 開発者ガイド](app-sdk-android.md)の同等の API を見つけるとき、あるいはこのガイドのコード変換スニペットを見つけるとき、Xamarin のバインディング ジェネレーターによって次のような目立つ方法で Android API が修飾されることにご注意ください。
> * すべての識別子がパスカル ケースに変換される (com.microsoft.foo -> Com.Microsoft.Foo)
> * すべての get/set 操作がプロパティ操作に変換される (例: Foo.getBar() -> Foo.Bar、Foo.setBar("zap") -> Foo.Bar = "zap")
> * すべてのインターフェイスで、名前の前に 'I' という文字が付けられる (FooInterface -> IFooInterface)

Xamarin.Forms またはその他の UI フレームワークを活用するアプリについては、`Microsoft.Intune.MAM.Remapper` という名前のツールを提供しています。 このツールは、ユーザーに代わってクラス置換を実行します。 これを使う場合は、以下の手順に従います。

1.  [Microsoft.Intune.MAM.Remapper.Tasks](https://www.nuget.org/packages/Microsoft.Intune.MAM.Remapper.Tasks) NuGet パッケージを自分のプロジェクトに追加します。

2.  Nuget パッケージに付属する `remapping-config.json` ファイルのビルド アクションを **RemappingConfigFile** に設定します。 追加した `remapping-config.json` は、Xamarin.Forms とのみ連動します。 その他の UI フレームワークの場合、Remapper NuGet に付属する Readme を参照してください。

3.  Intune 管理では、アプリケーションをバックグラウンドで起動できるため、MAM アプリケーションの OnMAMCreate 関数に Xamarin.Forms.Forms.Init(Context, Bundle) の呼び出しを追加します。

4.  [Android 用 Microsoft Intune アプリ SDK 開発者ガイド](app-sdk-android.md)の自分のアプリに該当する手順の残りを実行します。

> [!NOTE]
> ビルド失敗の原因となる Microsoft.Intune.MAM.Remapper.Tasks パッケージを更新すると、remapping-config.json のビルド アクションをリセットできることがあります。

## <a name="next-steps"></a>次の手順

Intune 管理のアプリ設定の基本手順を完了しました。 これで、上記の各プラットフォームに対して、統合ガイドに含まれる手順を実行できます。

組織が Intune の既存顧客の場合、Microsoft サポートの担当者と共にサポート チケットを開き、[Github の問題ページ](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/issues)で問題を作成してください。Microsoft ができるだけ早くサポートを提供します。 