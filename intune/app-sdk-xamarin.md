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
ms.openlocfilehash: 4ef0f754980a9bc2823129c62f7100edbcdc7524
ms.sourcegitcommit: 67ec0606c5440cffa7734f4eefeb7121e9d4f94f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
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
1.  Intune App SDK を初期化するには、`AppDelegate.cs` クラスで何らかの API を呼び出す必要があります。 たとえば、

      ```csharp
      public override bool FinishedLaunching (UIApplication application, NSDictionary launchOptions)
      {
            Console.WriteLine ("Is Managed: {0}", IntuneMAMPolicyManager.Instance.PrimaryUser != null);
            return true;
      }

      ```

2.  コンポーネントが追加され、初期化されたので、App SDK を iOS モバイル アプリに組み込むための一般的な手順を実行できます。 ネイティブ iOS アプリを有効にする方法は、「[iOS 用 Intune アプリ SDK 開発者ガイド](app-sdk-ios.md)」にすべて記載されています。
3. **重要**: Xamarin 基盤の iOS アプリに固有の変更がいくつかあります。 たとえば、キーチェーン グループを有効にするとき、以下を追加し、コンポーネントに含めた Xamarin サンプル アプリを含めます。 以下は、キーチェーン アクセス グループで利用されるようなグループの例です。

      ```xml
      <?xml version="1.0" encoding="UTF-8"?>
      <!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
      <plist version="1.0">
            <dict>
                  <key>keychain-access-groups</key>
                  <array>
                        <string>$(AppIdentifierPrefix)com.xamarin.microsoftintunesample</string>
                        <string>$(AppIdentifierPrefix)com.xamarin.microsoftintunesample.intunemam</string>
                        <string>$(AppIdentifierPrefix)com.microsoft.intune.mam</string>
                        <string>$(AppIdentifierPrefix)com.microsoft.adalcache</string>
                  </array>
            </dict>
      </plist>
      ```

Xamarin 基盤の iOS アプリにコンポーネントを組み込むための手順が完了しました。 プロジェクトの開発に Xcode を利用している場合、`Intune App SDK Settings.bundle` を利用できます。 プロジェクトを開発するとき、テストやデバッグのために Intune ポリシー設定のオン/オフを切り替えることができます。 このバンドルを活用するには、「[iOS 用 Intune アプリ SDK 開発者ガイド](app-sdk-ios.md)」の手順に従い、[Xcode デバッグ](app-sdk-ios.md#status-result-and-debug-notifications)に関するセクションをお読みください。

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

## <a name="next-steps"></a>次のステップ

コンポーネントをアプリに組み込む基本的な手順を完了しました。 これで、Xamarin Android サンプル アプリに含まれている手順を実行できます。 サンプルは 2 つあります。Xamarin.Forms 用が 1 つ、Android 用が 1 つです。
