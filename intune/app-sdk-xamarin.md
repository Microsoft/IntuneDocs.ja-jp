---
title: "Microsoft Intune App SDK Xamarin コンポーネント"
description: 
keywords: sdk, Xamarin, intune
author: erikre
manager: angrobe
ms.author: erikre
ms.date: 11/01/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 275d574b-3560-4992-877c-c6aa480717f4
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: ae53ced489542ba7e675e547740f1858d761c7ab
ms.sourcegitcommit: 833b1921ced35be140f0107d0b4205ecacd2753b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/04/2018
---
# <a name="microsoft-intune-app-sdk-xamarin-component"></a>Microsoft Intune App SDK Xamarin コンポーネント

> [!NOTE]
> 最初に、[Intune アプリ SDK の概要](app-sdk-get-started.md)に関する記事に目を通すことをお勧めします。このガイドでは、サポートする各プラットフォームで統合のための準備をする方法について説明しています。



## <a name="overview"></a>概要
[Intune App SDK Xamarin コンポーネント](https://components.xamarin.com/view/microsoft.intune.mam)を利用すると、Xamarin でビルドされた iOS アプリと Android アプリで [Intune アプリ SDK Xamarin コンポーネント](/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)が有効になります。 このコンポーネントを利用すると、開発者は Intune のアプリ保護機能を Xamarin ベースのアプリに簡単に組み込むことができます。

> [!NOTE]
> Intune SDK for Xamarin のサポートは現在、プレビュー版で利用できます。 

Microsoft Intune App SDK Xamarin コンポーネントを利用すると、Intune アプリ保護ポリシー (別名、APP または MAM ポリシー) を Xamarin で開発したアプリに組み込むことができます。 MAM 対応のアプリケーションが Intune App SDK に統合されています。 Intune で積極的にアプリを管理している場合、IT 管理者はモバイル アプリにアプリ保護ポリシーを展開できます。

## <a name="whats-supported"></a>サポートされる内容

### <a name="developer-machines"></a>開発者のコンピューター
* macOS


### <a name="mobile-app-platforms"></a>モバイル アプリのプラットフォーム
* Android
* iOS


### <a name="intune-mobile-application-management-scenarios"></a>Intune モバイル アプリケーション管理のシナリオ

* Intune MDM 登録デバイス
* サードパーティ製の EMM 登録デバイス
* 管理されていないデバイス (MDM に登録されていない)

Intune App SDK Xamarin コンポーネントで開発された Xamarin アプリでは、モバイル デバイス管理 (MDM) に登録しているデバイスと登録していないデバイスの両方で、Intune アプリ保護ポリシーを受け取るようになりました。

## <a name="prerequisites"></a>必要条件

* **[Android のみ]** 最新の Microsoft Intune Company Portal アプリをデバイスにインストールする必要があります。

## <a name="get-started"></a>作業開始

1.  **Xamarin-component.exe** を[ここ](https://components.xamarin.com/submit/xpkg)からダウンロードし、抽出します。

2. Microsoft Intune MAM Xamarin コンポーネントの[ライセンス条項](https://components.xamarin.com/license/microsoft.intune.mam)を読みます。

3.  [GitHub](https://github.com/msintuneappsdk/intune-app-sdk-xamarin) または [Xamarin](https://components.xamarin.com/license/microsoft.intune.mam) から Intune App SDK Xamarin コンポーネント フォルダーをダウンロードし、抽出します。 手順 1 と手順 3 でダウンロードしたファイルを両方とも同じディレクトリ レベルに配置する必要があります。

4.  監理者として起動したコマンド ラインで、`Xamarin.Component.exe install <.xam> file` を実行します。

5.  Visual Studio で、前に作成した Xamarin プロジェクトの**コンポーネント**を右クリックします。

6.  **[コンポーネントの編集]** を選択し、コンピューターにローカル ダウンロードした Intune App SDK コンポーネントを追加します。



## <a name="enabling-intune-app-protection-polices-in-your-ios-mobile-app"></a>iOS モバイル アプリで Intune アプリ保護ポリシーを有効にする
1.  iOS モバイル アプリに Intune App SDK を統合するのに必要な、一般的な手順に従います。 [iOS 用 Intune App SDK 開発者ガイド](app-sdk-ios.md#build-the-sdk-into-your-mobile-app)にある統合の手順 (手順 3) から開始できます。
    **重要**: Visual Studio と Xcode とでは、アプリのキーチェーンの共有を有効にする方法が少し異なります。 アプリの Entitlements plist を開き、[キーチェーンを有効にする] オプションが有効になっていることと、適切なキーチェーンの共有グループがそのセクションに追加されていることを確認します。 次に、すべての構成およびプラットフォームの適切な組み合わせに対して、プロジェクトの [iOS バンドル署名] オプションの [カスタム エンタイトルメント] フィールドに、その Entitlements plist が指定されていることを確認します。
2.  コンポーネントが追加され、アプリが正しく構成されると、お使いのアプリで Intune SDK の API を使用できるようになります。 これを行うには、次の名前空間を含める必要があります。
      ```csharp
      using Microsoft.Intune.MAM;
      ```
3.    アプリ保護ポリシーを受信するには、Intune MAM サービスにアプリを登録する必要があります。 お使いのアプリで、Azure Active Directory 認証ライブラリ (ADAL) を使用したユーザー認証を既に行っている場合、認証が成功した後に IntuneMAMEnrollmentManager の registerAndEnrollAccount メソッドに対して、ユーザーの UPN を渡す必要があります。
      ```csharp
      IntuneMAMEnrollmentManager.Instance.RegisterAndEnrollAccount(string identity);
      ```
      **重要**: Intune APP SDK の既定の ADAL 設定を、お使いのアプリの設定で上書きしてください。 これを行うには、[iOS 用 Intune App SDK 開発者ガイド](app-sdk-ios.md#configure-settings-for-the-intune-app-sdk)で説明しているように、アプリの Info.plist 内にある IntuneMAMSettings ディクショナリを利用できます。または IntuneMAMPolicyManager インスタンスで AAD の override プロパティを使用することも可能です。 ADAL 設定が静的なアプリケーションでは Info.plist を使用する方法をお勧めしますが、実行時にその値が決定されるアプリケーションでは override プロパティをお勧めします。 
      
      アプリで ADAL を使用せず、Intune SDK で認証を処理する場合は、アプリで IntuneMAMEnrollmentManager の loginAndEnrollAccount メソッドを呼び出す必要があります。
      ```csharp
       IntuneMAMEnrollmentManager.Instance.LoginAndEnrollAccount([NullAllowed] string identity);
      ```

## <a name="enabling-app-protection-policies-in-your-android-mobile-app"></a>Android モバイル アプリでアプリ保護ポリシーを有効にする
UI フレームワークを利用しない Xamarin 基盤の Android アプリの場合、「[Android 用 Intune アプリ SDK 開発者ガイド](app-sdk-android.md)」をお読みいただき、それに沿う必要があります。 Xamarin 基盤の Android アプリの場合、ガイドに含まれる[表](app-sdk-android.md#replace-classes-methods-and-activities-with-their-mam-equivalent)に基づき、クラス、メソッド、アクティビティを MAM のそれらと置換する必要があります。 アプリで `android.app.Application` クラスが定義されない場合、それを作成し、`MAMApplication` から継承するように設定する必要があります。

Xamarin Forms とその他の UI フレームワークの場合、「`MAM.Remapper`」と呼ばれているツールがあります。 このツールは、ユーザーに代わってクラス置換を実行します。 ただし、次の手順を実行する必要があります。

1.  `Microsoft.Intune.MAM.Remapper.Tasks` NuGet パッケージ バージョン 0.1.0.0 以降の参照を追加します。

2.  Android csproj に次の行を追加します。
  ```xml
  <Import
  Project="$(NugetPack)\\Microsoft.Intune.MAM.Remapper.Tasks.0.1.X.X\\build\\MonoAndroid10\\Microsoft.Intune.MAM.Remapper.targets" />
  ```

3.  追加した `remapping-config.json` ファイルのビルド アクションを **RemappingConfigFile** に設定します。 追加した `remapping-config.json` は、Xamarin.Forms とのみ連動します。 その他の UI フレームワークの場合、Remapper NuGet に付属する Readme を参照してください。

## <a name="next-steps"></a>次の手順

コンポーネントをアプリに組み込む基本的な手順を完了しました。 これで、Xamarin Android サンプル アプリに含まれている手順を実行できます。 サンプルは 2 つあります。Xamarin.Forms 用が 1 つ、Android 用が 1 つです。
