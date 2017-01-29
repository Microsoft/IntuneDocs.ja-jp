---
title: "Microsoft Intune App SDK Cordova プラグイン | Microsoft Docs"
description: 
keywords: sdk, Cordova, intune
author: oydang
manager: angrobe
ms.author: oydang
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bb940cb9-d43f-45ca-b065-ac0adc61dc6f
ms.reviewer: oydang
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 613e293d9bd853d6de7cdc0d753cc8473afc180b
ms.openlocfilehash: 9ef09f43e6c878af689a500457bab578149de499


---
# <a name="microsoft-intune-app-sdk-cordova-plugin"></a>Microsoft Intune App SDK Cordova プラグイン

> [!NOTE]
> 最初に、[Intune アプリ SDK の概要](intune-app-sdk-get-started.md)に関する記事に目を通すことをお勧めします。このガイドでは、サポートする各プラットフォームで統合のための準備をする方法について説明しています。


## <a name="overview"></a>概要

[Intune App SDK Cordova プラグイン](https://github.com/msintuneappsdk/cordova-plugin-ms-intune-mam)を利用すると、Cordova で開発された iOS アプリと Android アプリで [Intune モバイル アプリ管理機能](/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)が有効になります。 このプラグインを開発者が利用すると、Intune のアプリとデータの保護機能を Cordova 基盤のアプリに統合できます。

SDK の機能は、アプリの動作を変更せずに有効にできます。 iOS または Android アプリにプラグインを組み込むと、IT 監理者は、Microsoft Intune モバイル アプリケーション管理 (MAM) を使用してポリシーを展開し、さまざまなデータ保護機能をサポートすることができます。 このプラグインは、Cordova ビルド プロセスで多くの手順が自動的に実行されるように開発されました。 結果として、アプリの管理をすぐに有効にできるはずです。 最初に、対象プラットフォームに基づき、下の手順を実行します。




## <a name="whats-supported"></a>サポートされる内容

### <a name="developer-machines"></a>開発者のコンピューター
* Windows
* Mac OS


### <a name="mobile-app-platforms"></a>モバイル アプリのプラットフォーム
* Android 4.0 以降
* iOS

### <a name="intune-mobile-application-management-scenarios"></a>Intune モバイル アプリケーション管理のシナリオ

* Intune MDM 登録デバイス
* サードパーティ製の EMM 登録デバイス
* 管理されていないデバイス (MDM に登録されていない)

Intune App SDK Cordova プラグインで開発された Cordova アプリでは、モバイル デバイス管理 (MDM) に登録しているデバイスと登録していないデバイスの両方で、Intune モバイル アプリケーション管理 (MAM) ポリシーを受け取るようになりました。



## <a name="prerequisites"></a>必要条件

### <a name="technical-prerequisites"></a>技術的な前提条件

* **[Android のみ]** 常に最新の Microsoft Intune Company Portal アプリをデバイスにインストールする必要があります。


* [Cordova 向け Azure Active Directory 認証ライブラリ (ADAL) プラグイン](https://github.com/AzureAD/azure-activedirectory-library-for-cordova)のバージョン 0.8.0 以降が必要です。
  * **重要:** [ここに](https://issues.apache.org/jira/browse/CB-6227?jql=text%20~%20%22plugin%20dependency%22)記載されている Apache Cordova のバグにより、プラグインの依存関係が既に存在するアプリの場合、要求したバージョンにプラグインが自動アップグレードされません。


### <a name="before-you-install-and-use-microsoft-intune-app-sdk-cordova-plugin-you-must"></a>Microsoft Intune App SDK Cordova プラグインをインストールし、使用する前に、**必ず行うこと**:

* [Intune App SDK Cordova プラグインのライセンス条項](https://github.com/msintuneappsdk/cordova-plugin-ms-intune-mam/blob/master/Intune_App_SDK_Cordova_plugin_RTM_license.pdf)を読みます。

* 記録用にライセンス条項を印刷し、保持します。 Intune App SDK Cordova プラグインをダウンロードし、使用すると、このライセンス条項に同意したことになります。  本ライセンス条項に同意されない場合、お客様は本ソフトウェアを使用できません。


## <a name="quick-start"></a>クイック スタート

1. ADAL のバージョンを更新する:

    ```
    cordova plugin remove cordova-plugin-ms-adal
    cordova plugin add cordova-plugin-ms-adal@0.8.x
    ```

2. Cordova 向け Intune App SDK プラグインを追加する:

    ```
    cordova plugin add cordova-plugin-ms-intune-mam
    ```

## <a name="how-to-build-the-plugin-into-your-ios-app"></a>iOS アプリにプラグインを組み込む方法

アプリで Intune MAM を有効にするには、いくつかの手順を完了する必要があります。 便宜上、これらの手順はビルド前フックとして Cordova ビルド プロセスで自動実行されます。 結果として、この自動手順により、プロジェクト構成に関連付けられている `*.pbxproj`、`*-Info.plist`、`*.entitlements` ファイルが変更されます。 プロジェクトに権利ファイルが含まれていない場合、プラグインにより権利ファイルが自動作成されます。

このセットアップでサポートされる対象は&1; つだけです。複数の対象が見つかった場合、最初の対象で構成が実行されます。 プロセスが失敗した場合、次を確認してください。

1. アプリの Xcode プロジェクトは `[name].xcodeproj` です。`[name]` は `config.xml` に定義されている値です。
2. プロジェクトで[標準の Cordova アプリ ディレクトリ構造](https://cordova.apache.org/docs/en/latest/reference/cordova-cli/index.html#directory-structure)が利用されます。

## <a name="how-to-build-the-plugin-into-your-android-app"></a>Android アプリにプラグインを組み込む方法

1. 最新の Cordova ツールでこのプラグインをインポートします。 このプラグインは `after_compile` 手順として自動的に呼び出されます。

2. このプラグインでは、ビルド プロセスの終わりに、ビルド APK の MAM 対応バージョン (Android API 14+) が作成されます。 ビルド出力には `[Project]-intunewrapped-[Build_Configuration].apk` が含まれます (例: `helloWorld-intunewrapped-debug.apk`)。

このプラグインは、Gradle ビルドにのみ対応しています。

[ここ](https://issues.apache.org/jira/browse/CB-9434)に提出されている Cordova バグに起因し、`cordova run` で一部の Cordova フックが無視されるため、ラップされたアプリをコマンド ラインから実行するには、次を行う必要があります。

```
$ cordova build
$ cordova run --nobuild
```


### <a name="signing-your-android-app"></a>Android アプリの署名
ラップされた APK に署名情報を追加するには、署名情報を追加するときに通常行うように `build.json` を編集します。 たとえば、
```json
{
  "android": {
    "release": {
      "keystore": "your.keystore",
      "storePassword": "yourpassword",
      "alias": "youralias",
      "password" : "yourpassword",
      "keystoreType": ""
    }
  }
}
```

### <a name="build-for-android-test-only"></a>Android テストのみのビルド

1. `AndroidManifest.xml` ファイルのアプリケーション ノードに `android:testOnly="true"` を追加します。


2. **Cordova 6.x.x:** `[PROJECT_ROOT]/platforms/android/cordova/lib/Adb.js` で、行 60 を変更します。

    ```javascript
    var args = ['-s', target, 'install'];
    ```
    を
    ```javascript
    var args = ['-s', target, 'install', '-t'];
    ```

この変更の結果、"-t" フラグを付けて `adb install` が実行されます。これがないと、`testOnly` アプリをインストールできないためです。

### <a name="debugging-from-visual-studio"></a>Visual Studio からデバッグする
アプリを初めて起動すると、アプリが Intune で管理されていることを知らせるダイアログが表示されるはずです。 "次からは表示しない" を押し、VS からデバッグ/実行ボタンをもう一度クリックし、ブレークポイントにヒットさせます。

## <a name="known-limitations"></a>既知の制限
### <a name="android"></a>Android
* MultiDex のサポートが不完全です。
* アプリは Android 4.0 (Android API 14) 以上を対象にする必要があります。

### <a name="ios"></a>iOS
* **Info.plist** ファイルの **CFBundleDocumentTypes** ノードの下で UTI の一覧を変更した場合、再構築する前に、同じ plist ファイル (**UTImportedTypeDeclarations** node) のインポートされた UTI セクションで Intune UTI を消去する必要があります。 Intune UTI はすべてプレフィックス `com.microsoft.intune.mam` で始める必要があります。

* Cordova プロジェクトから Intune プラグインを削除する場合、iOS プラットフォームも削除し、もう一度追加し、.xcodeproj ファイルと .plist ファイルで一部の Intune 設定を元に戻す必要があります。



<!--HONumber=Dec16_HO2-->


