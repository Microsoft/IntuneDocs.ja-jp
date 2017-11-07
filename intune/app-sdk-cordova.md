---
title: "Microsoft Intune App SDK Cordova プラグイン"
description: 
keywords: sdk, Cordova, intune
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bb940cb9-d43f-45ca-b065-ac0adc61dc6f
ms.reviewer: oydang
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: fd4cedd20f427966dc3cfb7c2748f57b4d0746ab
ms.sourcegitcommit: 94d3d86f8ae9f82a9872384bbaae53580036a4ff
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2017
---
# <a name="microsoft-intune-app-sdk-cordova-plugin"></a>Microsoft Intune App SDK Cordova プラグイン

> [!NOTE]
> 最初に、[Intune アプリ SDK の概要](app-sdk-get-started.md)に関する記事に目を通すことをお勧めします。このガイドでは、サポートする各プラットフォームで統合のための準備をする方法について説明しています。

## <a name="overview"></a>概要

iOS アプリおよび Android アプリの [Intune App SDK Cordova プラグイン](/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune) は、Cordova を使用してビルドされています。 このプラグインを開発者が利用すると、Intune のアプリとデータの保護機能を Cordova 基盤のアプリに統合できます。

SDK の機能は、アプリの動作を変更せずに有効にできます。 iOS または Android アプリにプラグインを組み込むと、Microsoft Intune 管理者は Intune アプリの保護ポリシーを展開できるようになります。保護ポリシーは多様なデータ保護機能で構成されます。 このプラグインは、Cordova ビルド プロセスで多くの手順が自動的に実行されるように開発されました。 そのため、アプリの保護をすぐに有効にすることができます。 最初に、対象プラットフォームに基づき、下の手順を実行します。

## <a name="supported-platforms"></a>サポートされるプラットフォーム

* このプラグインは、Windows、Mac、Linux OS で動作します。
* このプラグインは、`minSdkVersion` が 14 以上、`targetSdkVersion` が 24 以下の Android アプリで動作します。
* このプラグインは 9.0 以降の iOS をターゲットとする iOS アプリで動作します。

## <a name="intune-mobile-application-management-scenarios"></a>Intune モバイル アプリケーション管理のシナリオ

* Intune MDM 登録デバイス
* サードパーティ製の EMM 登録デバイス
* 管理されていないデバイス (MDM に登録されていない)

Intune App SDK Cordova プラグインで開発された Cordova アプリでは、モバイル デバイス管理 (MDM) に登録しているデバイスと登録していないデバイスの両方で、Intune アプリ保護ポリシーを受け取るようになりました。

## <a name="prerequisites"></a>必要条件

### <a name="android"></a>Android

* 常に最新の Microsoft Intune Company Portal アプリをデバイスにインストールする必要があります。
* このプラグインを使用する場合、Cordova ビルドを実行するパス上に Java 7 以降がインストールされている必要があります。

### <a name="ios"></a>iOS

* MDM 機能を使用するには、最新の Microsoft Intune Company Portal アプリをデバイスにインストールする必要があります。 デバイス登録機能を使用しない場合、Intune アプリ保護ポリシーには必要*ありません*。

### <a name="both-platforms"></a>両方のプラットフォーム

* [Cordova 向け Azure Active Directory 認証ライブラリ (ADAL) プラグイン](https://github.com/AzureAD/azure-activedirectory-library-for-cordova)のバージョン 0.8.0 以降が必要です。

> [!NOTE]
> [ここ](https://issues.apache.org/jira/browse/CB-6227?jql=text%20~%20%22plugin%20dependency%22)に提出されている Apache Cordova バグに起因し、プラグイン依存性が既に存在するアプリの場合、要求したバージョンにプラグインが自動アップグレードされません。



## <a name="quick-start"></a>クイック スタート

1. ADAL のバージョンを更新する:

  ```shell
  cordova plugin remove cordova-plugin-ms-adal
  cordova plugin add cordova-plugin-ms-adal@0.8.x
  ```

2. Cordova 向け Intune App SDK プラグインを追加する:

  ```shell
  cordova plugin add cordova-plugin-ms-intune-mam
  ```

## <a name="build-the-plugin-into-your-ios-app"></a>iOS アプリにプラグインを組み込む

アプリで Intune アプリ保護ポリシーを使用できるようにするには、いくつかの手順を実行する必要があります。 便宜上、これらの手順はビルド前フックとして Cordova ビルド プロセスで自動実行されます。 結果として、この自動手順により、プロジェクト構成に関連付けられている `*.pbxproj`、`*-Info.plist`、`*.entitlements` ファイルが変更されます。 プロジェクトに権利ファイルが含まれていない場合、プラグインにより権利ファイルが自動作成されます。

このセットアップでサポートされる対象は 1 つだけです。複数の対象が見つかった場合、最初の対象で構成が実行されます。 プロセスが失敗した場合、次を確認してください。

1. アプリの Xcode プロジェクトは `[name].xcodeproj` です。`[name]` は `config.xml` に定義されている値です。
2. プロジェクトで[標準の Cordova アプリ ディレクトリ構造](https://cordova.apache.org/docs/en/latest/reference/cordova-cli/index.html#directory-structure)が利用されます。

## <a name="build-the-plugin-into-your-android-app"></a>Android アプリにプラグインを組み込む

1. 最新の Cordova ツールでこのプラグインをインポートします。 このプラグインは `after_compile` 手順として自動的に呼び出されます。

2. このプラグインでは、ビルド プロセスの終わりに、ビルド APK の Intune 対応バージョン (Android API 14 以降) が作成されます。 ビルド出力には `[Project]-intunewrapped-[Build_Configuration].apk` が含まれます (例: `helloWorld-intunewrapped-debug.apk`)。

> [!NOTE]
> このプラグインは、Gradle ビルドにのみ対応しています。

[ここ](https://issues.apache.org/jira/browse/CB-9434)に提出されている Cordova バグに起因し、`cordova run` で一部の Cordova フックが無視されるため、ラップされたアプリをコマンド ラインから実行するには、次を行う必要があります。

```shell
$ cordova build
$ cordova run --nobuild
```

## <a name="sign-your-android-app"></a>Android アプリの署名

このプラグインで、次の場所の Cordova に提供した署名情報が自動的に認識されます。

* platforms/android/debug-signing.properties
* platforms/android/release-signing.properties
* res/native/android/ant.properties

使用できる書式については、「[Cordova gradle signing information](https://cordova.apache.org/docs/en/latest/guide/platforms/android/#using-gradle)」(Cordova gradle の署名情報) を参照してください。

現在、Cordova ビルドへのパラメーターを使用して、`build.json` で署名情報または任意の場所情報を提供する機能をサポートしていません。

## <a name="debugging-from-visual-studio"></a>Visual Studio からデバッグする

アプリを初めて起動すると、アプリが Intune で管理されていることを知らせるダイアログが表示されるはずです。 "次からは表示しない" を押し、VS からデバッグ/実行ボタンをもう一度クリックし、ブレークポイントにヒットさせます。

## <a name="known-limitations"></a>既知の制限

### <a name="android"></a>Android

* MultiDex のサポートが不完全です。
* アプリには 14 以上の `minSdkVersion`、および 24 以下の `targetSdkVersion` が必要です。 現在、API 25 をターゲットとするアプリはサポートしてません。
* V2 署名方式で署名されたアプリに再署名することはできません。 V2 で署名されたアプリをプラグインでラップすると、ラップされた出力の .apk は署名なしになります。
*
  * Cordova の既定の V2 署名を無効にするには、以下を `build-extras.gradle` ファイルに追加します。

  ```gradle
  android {
      signingConfigs {
          release {
              v2SigningEnabled false
          }
          debug {
              v2SigningEnabled false
          }
      }
      buildTypes {
          release {
              signingConfig signingConfigs.release
          }
          debug {
              signingConfig signingConfigs.debug
          }
      }
  }
  ```

### <a name="ios"></a>iOS

* **Info.plist** ファイルの **CFBundleDocumentTypes** ノードの下で UTI の一覧を変更した場合、再構築する前に、同じ plist ファイル (**UTImportedTypeDeclarations** node) のインポートされた UTI セクションで Intune UTI を消去する必要があります。 Intune UTI はすべてプレフィックス `com.microsoft.intune.mam` で始める必要があります。

* Cordova プロジェクトから Cordova 用 Intune App SDK プラグインを削除する場合、iOS プラットフォームも削除し、もう一度追加し、.xcodeproj ファイルと .plist ファイルで一部の Intune 設定を元に戻す必要があります。
