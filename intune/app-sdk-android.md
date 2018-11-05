---
title: Android 用 Microsoft Intune アプリ SDK 開発者ガイド
description: Android 用 Microsoft Intune アプリ SDK を使用すると、Android アプリに Intune モバイル アプリ管理 (MAM) を組み込むことができます。
keywords: SDK
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/03/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 0100e1b5-5edd-4541-95f1-aec301fb96af
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 4a588af375ef690d45e067dfc4261fbeb551755c
ms.sourcegitcommit: 2d30ec70b85f49a7563adcab864c1be5a63b9947
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/08/2018
ms.locfileid: "48863214"
---
# <a name="microsoft-intune-app-sdk-for-android-developer-guide"></a>Android 用 Microsoft Intune アプリ SDK 開発者ガイド

> [!NOTE]
> まず、[Intune アプリ SDK の概要](app-sdk.md)に目を通すことをお勧めします。このガイドでは、SDK の最新機能と、サポートされる各プラットフォームで統合のための準備をする方法について説明しています。

Android 用 Microsoft Intune アプリ SDK を使用すると、ネイティブ Android アプリに Intune アプリ保護ポリシー (**APP** または MAM ポリシー) を組み込むことができます。 Intune の管理対象アプリケーションは、Intune App SDK に統合されています。 Intune で積極的にアプリを管理している場合、Intune 管理者は Intune の管理対象アプリにアプリ保護ポリシーを簡単に展開できます。


## <a name="whats-in-the-sdk"></a>SDK の機能

Intune App SDK は、次のファイルで構成されます。

* **Microsoft.Intune.MAM.SDK.aar**: サポート ライブラリ JAR ファイルを除く、SDK コンポーネントです。
* **Microsoft.Intune.MAM.SDK.Support.v4.jar**: Android v4 サポート ライブラリを使用するアプリで MAM を有効にするために必要なクラスです。
* **Microsoft.Intune.MAM.SDK.Support.v7.jar**: Android v7 サポート ライブラリを使用するアプリで MAM を有効にするために必要なクラスです。
* **Microsoft.Intune.MAM.SDK.Support.v17.jar**: Android v17 サポート ライブラリを使用するアプリで MAM を有効にするために必要なクラスです。 
* **Microsoft.Intune.MAM.SDK.Support.Text.jar**: `android.support.text` パッケージで Android サポート ライブラリを使用するアプリで MAM を有効にするために必要なクラスです。
* **Microsoft.Intune.MDM.SDK.DownlevelStubs.jar**: この jar には、新しいデバイス上にのみ存在し、MAMActivity 内のメソッドによって参照される Android システム クラスのためのスタブが含まれています。 新しいデバイスでは、これらのスタブ クラスを無視します。 この jar が必要になるのは、MAMActivity から派生したクラスに対してリフレクションを実行する場合のみであり、ほとんどのアプリにはこの jar を含める必要がありません。 この jar を使用している場合、そのすべてのクラスを ProGuard から除外する操作は慎重に行う必要があります。 それはすべて "android" ルート パッケージの下にあります。
* **com.microsoft.intune.mam.build.jar**: [SDK の統合を補助する](#build-tooling) Gradle のプラグインです。
* **CHANGELOG.txt**: 各 SDK バージョンに加えた変更の記録を提供します。
* **THIRDPARTYNOTICES.TXT**:  アプリにコンパイルされるサード パーティや OSS のコードを確認する属性通知です。

## <a name="requirements"></a>要件

この SDK は Android API 19 (Android 4.4 以降) から Android API 28 (Android 8.0) までをサポートしています。


### <a name="company-portal-app"></a>ポータル サイト アプリ
Android 用の Intune アプリ SDK でアプリ保護ポリシーを有効にするには、デバイスに[ポータル サイト](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) アプリが存在する必要があります。 ポータル サイトは、Intune サービスからアプリ保護ポリシーを取得します。 アプリが初期化されるときに、ポータル サイトからポリシーとコードを読み込み、そのポリシーを適用します。

> [!NOTE]
> ポータル サイト アプリがデバイス上にない場合は、Intune の管理対象アプリが Intune アプリ保護ポリシーをサポートしていない通常のアプリと同様に動作します。

デバイス登録が不要なアプリ保護の場合は、ユーザーがポータル サイト アプリを使用してデバイスを登録する必要は_**ありません**_。

## <a name="sdk-integration"></a>SDK 統合

### <a name="referencing-intune-app-libraries"></a>Intune アプリのライブラリを参照する

Intune アプリ SDK は、外部依存関係のない標準の Android ライブラリです。 **Microsoft.Intune.MAM.SDK.aar** には、アプリ保護ポリシーの有効化に必要なインターフェイスと Microsoft Intune ポータル サイト アプリとの対話操作に必要なコードの両方が含まれています。

**Microsoft.Intune.MAM.SDK.aar** は、Android ライブラリの参照として指定する必要があります。 これを行うには、Android Studio でアプリ プロジェクトを開き、**[File]**、New、New module の順に選択し、**[Import .JAR/.AAR Package]** を選択します。 次に、Android アーカイブ パッケージ Microsoft.Intune.MAM.SDK.aar を選択して、.AAR のモジュールを作成します。 アプリ コードを含むモジュールを右クリックし、**[モジュール設定]** > **[依存関係] タブ** > **[+] アイコン** > **[モジュールの依存関係]** の順に移動して、作成した MAM SDK AAR モジュール、**[OK]** の順に選択します。 これで、プロジェクトのビルド時にモジュールが MAM SDK でコンパイルされるようになります。

さらに、**Microsoft.Intune.MAM.SDK.Support.XXX.jar** ライブラリには、対応する `android.support.XXX` ライブラリの Intune バリアントが含まれます。 これらは、アプリがサポート ライブラリに依存する必要がない場合に備えて、Microsoft.Intune.MAM.SDK.aar には組み込まれていません。

#### <a name="proguard"></a>ProGuard

[ProGuard](http://proguard.sourceforge.net/) (または任意のその他の圧縮/難読化メカニズム) がビルド ステップとして使用される場合、SDK には追加の構成ルールを含める必要があります。 .aar をご自分のビルドに含めると、ルールが自動的に ProGuard ステップに統合され、必要なクラス ファイルが保持されます。

Azure Active Directory 認証ライブラリ (ADAL) には、独自の ProGuard の制限がある場合があります。 アプリが ADAL を統合する場合、これらの制限について ADAL のドキュメントに従う必要があります。

### <a name="build-tooling"></a>ビルド ツール
Intune App SDK は Android ライブラリで、これにより、ご自分のアプリで Intune ポリシーの強制のサポートと参加を行うことができます。 一部のポリシーには、[強制するためにアプリからの明示的な参加](#enable-features-that-require-app-participation)が必要ですが、ほとんどが半自動的に強制されます。 この自動強制には、アプリでいくつかの Android の基底クラスからの継承を同等の MAM からの継承に置き換え、同様に特定の Android システム サービス クラスへの呼び出しを同等の MAM への呼び出しに置き換える必要があります。 必要な特定の置換の詳細は、[以下](#class-and-method-replacements)のとおりです。

これらの置換を手動で実行することは、面倒なプロセスになる場合があります。 代わりに、SDK ではビルドツールが提供されます (Gradle ビルド用のプラグインと Gradle 以外のビルド用のコマンド ライン ツール)。これにより、自動的に置換が実行されます。 これらのツールによって、Java のコンパイルによって生成されたクラス ファイルが変換され、元のソース コードへの変更は行われません。

このツールでは[直接の置換](#class-and-method-replacements)のみが実行されます。 これにより、[ポリシーとして保存](#enable-features-that-require-app-participation)、[複数 ID](#multi-identity-optional)、[App-WE の登録](#app-protection-policy-without-device-enrollment)、[Android のマニフェストの変更](#manifest-replacements)または[ADAL の構成](#configure-azure-active-directory-authentication-library-adal)など、さらに複雑な SDK の統合が実行されることはないため、これらはご利用のアプリで完全に Intune を有効にする前に完了する必要があります。 ご利用のアプリに関連する統合ポイントのために、このドキュメントの残りの部分を慎重に確認してください。

> [!NOTE]
> 既に部分的に実行されている、または手動の置換によって MAM SDK のソースの統合を完了するプロジェクトに対してツールを実行しても構いません。 ご自分のプロジェクトでは、依存関係として MAM SDK を引き続き一覧する必要があります。

### <a name="gradle-build-plugin"></a>Gradle のビルド プラグイン
Gradle でアプリをビルドしていない場合は、[コマンド ライン ツールでの統合](#command-line-build-tool)に関する記事にスキップしてください。 

App SDK プラグインは、SDK の一部として **GradlePlugin/com.microsoft.intune.mam.build.jar** で配布されます。 Gradle でプラグインを見つけることができるようにするには、これをビルドスクリプトのクラスパスに追加する必要があります。 プラグインは [Javassist](http://jboss-javassist.github.io/javassist/) に依存し、これも追加する必要があります。 これらをクラスパスに追加するには、ご自分のルート `build.gradle` に以下を追加します。

```groovy
buildscript {
    repositories {
        jcenter()
    }
    dependencies {
        classpath "org.javassist:javassist:3.22.0-GA"
        classpath files("$PATH_TO_MAM_SDK/GradlePlugin/com.microsoft.intune.mam.build.jar")
    }
}
```

次に、ご自分の APK プロジェクトに対する `build.gradle` ファイルで、次のようにプラグインを適用するだけです。
```groovy
apply plugin: 'com.microsoft.intune.mam'
```

既定では、プラグインは `project` 依存関係で**のみ**動作します。
テストのコンパイルは影響を受けません。 構成は一覧するために提供される場合があります。
*  除外するプロジェクト
*  [含める外部依存関係](#usage-of-includeexternallibraries) 
*  処理から除外する特定のクラス
*  処理から除外するバリアント これらは完全なバリアント名または単一のフレーバーのいずれかを参照できます。 例
     * ご利用のアプリにフレーバー {`savory`, `sweet`} と {`vanilla`, `chocolate`} を含むビルドの種類 `debug` と `release` がある場合は、指定できます。
     * savory フレーバーを含むバリアントをすべて除外するには `savory`、正確なバリアントのみを除外するには `savoryVanillaRelease`。

#### <a name="example-partial-buildgradle"></a>部分的な build.gradle の例

```groovy

apply plugin: 'com.microsoft.intune.mam'

dependencies {
    implementation project(':product:FooLib')
    implementation project(':product:foo-project')
    implementation fileTree(dir: "libs", include: ["bar.jar"])
    implementation fileTree(dir: "libs", include: ["zap.jar"])
    implementation "com.contoso.foo:zap-artifact:1.0.0"
    implementation "com.microsoft.bar:baz:1.0.0"

    // Include the MAM SDK
    implementation files("$PATH_TO_MAM_SDK/Microsoft.Intune.MAM.SDK.aar")
}
intunemam {
    excludeProjects = [':product:FooLib']
    includeExternalLibraries = ['bar.jar', "com.contoso.foo:zap-artifact", "com.microsoft.*"]
    excludeClasses = ['com.contoso.SplashActivity']
    excludeVariants=['savory']
}

```
これにより、次の効果があります。
* `:product:FooLib` は `excludeProjects` に含まれるため、上書きされません。
* `excludeClasses` に含まれるためにスキップされる `com.contoso.SplashActivity` を除き、`:product:foo-project` は上書きされます。
* `bar.jar` は `includeExternalLibraries` に含まれるため、上書きされます。
* `zap.jar` はプロジェクトではなく、`includeExternalLibraries` に含まれないため、上書きされ**ません**。
* `com.contoso.foo:zap-artifact:1.0.0` は `includeExternalLibraries` に含まれるため、上書きされます。
* `com.microsoft.bar:baz:1.0.0` はワイルドカード (`com.microsoft.*`) によって `includeExternalLibraries` に含まれるため、上書きされます。

#### <a name="usage-of-includeexternallibraries"></a>includeExternalLibraries の使い方

既定でプラグインはプロジェクトの依存関係でのみ動作するため (通常、`project()` 関数で指定される)、`fileTree(...)` によって指定された、または Maven やその他のパッケージ ソース (例: "`com.contoso.bar:baz:1.2.0`") から取得した任意の依存関係は、その MAM 処理が以下で説明される条件に基づいて必要な場合は、`includeExternalLibraries` プロパティに提供される必要があります。 ワイルドカード ("*") がサポートされます。

成果物で外部の依存関係を指定している場合、`includeExternalLibraries` 値のバージョン コンポーネントを省略することをお勧めします。 バージョンを含める場合は、正確なバージョンである必要があります。 ダイナミック バージョンの定義 (例: `1.+`) はサポートされません。

`includeExternalLibraries` にライブラリを含める必要があるかどうかを判断するために使用する必要がある一般的なルールは、次の 2 つの質問に基づいています。
1. ライブラリにはクラスが含まれ、それに対して同等の MAM がありますか?  例: `Activity`、`Fragment`、`ContentProvider`、`Service` など。
2. はいの場合、ご利用のアプリでそれらのクラスを活用しますか? 

これらの質問の答えが両方 "はい" の場合は、そのライブラリを `includeExternalLibraries` に含める必要があります。 

| 通信の種類 | 含める必要があるか? |
|--|--|
| ユーザーが PDF を表示しようとしたときに、ご利用のアプリに PDF ビューアー ライブラリを含めて、ご利用のアプリケーションでビューアー `Activity` を使用します | はい |
| Web パフォーマンスを強化するために、ご利用のアプリに HTTP ライブラリを含めます | [いいえ] |
| `Activity`、`Application` および `Fragment` から派生したクラスを含む React Native などのライブラリを含めて、ご利用のアプリでそれらのクラスを使用したり、さらに派生させたりします | はい |
| `Activity`、`Application` および `Fragment` から派生したクラスを含む React Native などのライブラリを含めますが、静的なヘルパーまたはユーティリティ クラスのみを使用します | [いいえ] |
| `TextView` から派生したビュー クラスを含むライブラリを含めて、ご利用のアプリでそれらのクラスを使用したり、さらに派生させたりします | はい |


#### <a name="dependencies"></a>依存関係

Gradle のプラグインには、(上述のとおり) Gradle の依存関係の解決に利用できる必要がある [Javassist](http://jboss-javassist.github.io/javassist/) に依存関係があります。 Javassist は、プラグインを実行しているときのビルド時に単独で使用されます。 Javassist コードはご自分のアプリには追加されません。

> [!NOTE]
> Android Gradle プラグインのバージョン 3.0 以降および Gradle 4.1 以降を使用している必要があります。

### <a name="command-line-build-tool"></a>コマンド ラインのビルド ツール
ビルドに Gradle を使用する場合は、[次のセクション](#class-and-method-replacements)にスキップしてください。

コマンド ラインのビルド ツールは、SDK ドロップの `BuildTool` フォルダーで入手できます。 これにより、上述の Gradle プラグインと同じ関数が実行されますが、カスタムまたは Gradle 以外のビルド システムに統合できます。 これはより汎用的で、呼び出しがより複雑になるため、可能な場合は Gradle プラグインを使用する必要があります。

#### <a name="using-the-command-line-tool"></a>コマンド ライン ツールを使用する

コマンド ライン ツールは、`BuildTool\bin` ディレクトリに配置された指定のヘルパー スクリプトを使用して呼び出すことができます。

このツールには、次のパラメーターが必要です。
| パラメーター | 説明 |
| -- | -- |
| `--input` | jar ファイルと変更するクラス ファイルのディレクトリのセミコロン区切りの一覧。 これは上書きしようとするすべての jars/ディレクトリを含む必要があります。 |
| `--output` | jar ファイルと変更されたクラスを格納するディレクトリのセミコロン区切りの一覧。 入力エントリごとに 1 つの出力エントリがあり、順番に一覧される必要があります。 |
| `--classpath` | ビルドのクラスパス。 ここには jar とクラス ディレクトリの両方を含めることができます。 |
| `--excludeClasses`| 上書きから除外される必要があるクラスの名前を含むセミコロン区切りの一覧。 |

省略可能な `--excludeClasses` を除く、すべてのパラメーターが必須です。

#### <a name="example-command-line-tool-invocation"></a>コマンド ライン ツールの呼び出しの例

``` batch
> BuildTool\bin\BuildTool.bat --input build\product-foo-project;libs\bar.jar --output mam-build\product-foo-project;mam-build\libs\bar.jar --classpath build\zap.jar;libs\Microsoft.Intune.MAM.SDK\classes.jar;%ANDROID_SDK_ROOT%\platforms\android-27\android.jar --excludeClasses com.contoso.SplashActivity
```

これにより、次の効果があります。

* `product-foo-project` ディレクトリは `mam-build\product-foo-project` に上書きされます
* `bar.jar` は `mam-build\libs\bar.jar` に上書きされます
* `zap.jar` は `--classpath` にのみ一覧されるため、上書きされ**ません**
* `com.contoso.SplashActivity` クラスは `--input` 内にあっても、上書きされ**ません**

> [!NOTE] 
> 現在、ビルド ツールでは aar ファイルをサポートしていません。 aar ファイルを取り扱っているときに、ご利用のビルド システムでまだ `classes.jar` を抽出していない場合は、ビルド ツールを呼び出す前に抽出する必要があります。


## <a name="class-and-method-replacements"></a>クラスとメソッドの置換

Intune 管理を有効にするために、Android の基底クラスを、それぞれ対応する同等の MAM に置き換える必要があります。 SDK クラスは、Android の基底クラスと、アプリ独自のそのクラスの派生バージョンの間に位置します。 たとえば、アプリ アクティビティを使用すると、最終的な継承階層は、`Activity` > `MAMActivity` >
`AppSpecificActivity` のようになります。 世界中のマネージド ビューでアプリをシームレスに提供するために、MAM レイヤーではシステム操作への呼び出しをフィルター処理します。

基底クラスに加えて、ご自分のアプリで派生することなく使用する可能性がある一部のクラス (例: `MediaPlayer`) には、同等の MAM も必要で、[一部のメソッドも置き換える必要があります](#wrapped-system-services)。 以下に正確な詳細を示します。

このセクションで詳述されている置換はすべて、SDK [ビルド ツール](#build-tooling)によって自動的に実行される場合がります。 



| Android の基底クラス | Intune アプリ SDK の代替物 |
|--|--|
| とroid.app.Activity | MAMActivity |
| とroid.app.ActivityGroup | MAMActivityGroup |
| とroid.app.AliasActivity | MAMAliasActivity |
| とroid.app.Application | MAMApplication |
| とroid.app.DialogFragment | MAMDialogFragment |
| とroid.app.ExpとableListActivity | MAMExpとableListActivity |
| とroid.app.Fragment | MAMFragment |
| とroid.app.IntentService | MAMIntentService |
| とroid.app.LauncherActivity | MAMLauncherActivity |
| とroid.app.ListActivity | MAMListActivity |
| android.app.ListFragment | MAMListFragment |
| とroid.app.NativeActivity | MAMNativeActivity |
| とroid.app.PendingIntent | MAMPendingIntent (「[PendingIntent](#pendingintent)」を参照) |
| とroid.app.Service | MAMService |
| とroid.app.TabActivity | MAMTabActivity |
| とroid.app.TaskStackBuilder | MAMTaskStackBuilder |
| とroid.app.backup.BackupAgent | MAMBackupAgent |
| とroid.app.backup.BackupAgentHelper | MAMBackupAgentHelper |
| とroid.app.backup.FileBackupHelper | MAMFileBackupHelper |
| とroid.app.backup.SharePreferencesBackupHelper | MAMSharedPreferencesBackupHelper |
| とroid.content.BroadcastReceiver | MAMBroadcastReceiver |
| とroid.content.ContentProvider | MAMContentProvider |
| とroid.os.Binder | MAMBinder (Android インターフェイス定義言語 (AIDL) インターフェイスから Binder が生成されない場合にのみ必要) |
| android.media.MediaPlayer | MAMMediaPlayer |
| android.media.MediaMetadataRetriever | MAMMediaMetadataRetriever |
| とroid.provider.DocumentsProvider | MAMDocumentsProvider |
| とroid.preference.PreferenceActivity | MAMPreferenceActivity |
| android.support.multidex.MultiDexApplication | MAMMultiDexApplication |
| android.widget.TextView | MAMTextView |
| android.widget.AutoCompleteTextView | MAMAutoCompleteTextView |
| android.widget.CheckedTextView | MAMCheckedTextView |
| android.widget.EditText | MAMEditText |
| android.inputmethodservice.ExtractEditText | MAMExtractEditText |
| android.widget.MultiAutoCompleteTextView | MAMMultiAutoCompleteTextView |

> [!NOTE]
> アプリケーションが独自に派生した `Application` クラスを必要としていなくても、下記の「[`MAMApplication`](#mamapplication)」を参照してください。

### <a name="microsoftintunemamsdksupportv4jar"></a>Microsoft.Intune.MAM.SDK.Support.v4.jar:

| Android クラス | Intune アプリ SDK の代替物 |
|--|--|
| とroid.suppまたはt.v4.app.DialogFragment | MAMDialogFragment
| とroid.suppまたはt.v4.app.FragmentActivity | MAMFragmentActivity
| とroid.suppまたはt.v4.app.Fragment | MAMFragment
| android.support.v4.app.JobIntentService | MAMJobIntentService
| とroid.suppまたはt.v4.app.TaskStackBuilder | MAMTaskStackBuilder
| とroid.suppまたはt.v4.content.FileProvider | MAMFileProvider
| android.support.v4.content.WakefulBroadcastReceiver | MAMWakefulBroadcastReceiver

### <a name="microsoftintunemamsdksupportv7jar"></a>Microsoft.Intune.MAM.SDK.Support.v7.jar:

|Android クラス | Intune アプリ SDK の代替物 |
|--|--|
|android.support.v7.app.AppCompatActivity | MAMAppCompatActivity |
| android.support.v7.widget.AppCompatAutoCompleteTextView | MAMAppCompatAutoCompleteTextView |
| android.support.v7.widget.AppCompatCheckedTextView | MAMAppCompatCheckedTextView |
| android.support.v7.widget.AppCompatEditText | MAMAppCompatEditText |
| android.support.v7.widget.AppCompatMultiAutoCompleteTextView | MAMAppCompatMultiAutoCompleteTextView |
| android.support.v7.widget.AppCompatTextView | MAMAppCompatTextView |

### <a name="microsoftintunemamsdksupportv17jar"></a>Microsoft.Intune.MAM.SDK.Support.v17.jar:
|Android クラス | Intune アプリ SDK の代替物 |
|--|--|
| android.support.v17.leanback.widget.SearchEditText | MAMSearchEditText |

### <a name="microsoftintunemamsdksupporttextjar"></a>Microsoft.Intune.MAM.SDK.Support.Text.jar:
|Android クラス | Intune アプリ SDK の代替物 |
|--|--|
| android.support.text.emoji.widget.EmojiAppCompatEditText | MAMEmojiAppCompatEditText |
| android.support.text.emoji.widget.EmojiAppCompatTextView | MAMEmojiAppCompatTextView |
| android.support.text.emoji.widget.EmojiEditText | MAMEmojiEditText |
| android.support.text.emoji.widget.EmojiTextView | MAMEmojiTextView |

### <a name="renamed-methods"></a>名前が変更されたメソッド
多くの場合、Android のクラスで使用できるメソッドが、MAM の置換クラスで最終版としてマークされています。 この場合、MAM 置換クラスによって、似た名前のメソッド (`MAM` というサフィックスが付いている) が提供され、これをオーバーライドする必要があります。 たとえば、`MAMActivity` から派生する場合は、`onCreate()` をオーバーライドして `super.onCreate()` を呼び出すのではなく、`Activity` で `onMAMCreate()` をオーバーライドし、`super.onMAMCreate()` を呼び出す必要があります。 同等の MAM でなく、元のメソッドが偶発的にオーバーライドされることを防ぐために、Java コンパイラによって、最終的な制限が強制されます。

### <a name="mamapplication"></a>MAMApplication
アプリで `android.app.Application` のサブクラスを作成する場合は、代わりに `com.microsoft.intune.mam.client.app.MAMApplication` のサブクラスを作成する**必要**があります。 アプリで `android.app.Application` のサブクラスを作成しない場合は、AndroidManifest.xml の `<application>` タグに `"android:name"` 属性として `"com.microsoft.intune.mam.client.app.MAMApplication"` を設定する**必要**があります。
### <a name="pendingintent"></a>PendingIntent
`PendingIntent.get*` の代わりに `MAMPendingIntent.get*` メソッドを使用する必要があります。 その後、通常どおり、結果の `PendingIntent` を使用できます。

### <a name="wrapped-system-services"></a>ラップされたシステム サービス
一部のシステム サービス クラスでは、サービス インスタンスで目的のメソッドを直接呼び出す代わりに、MAM ラッパー クラスで静的メソッドを呼び出す必要がります。 たとえば、`getSystemService(ClipboardManager.class).getPrimaryClip()` への呼び出しは、`MAMClipboardManager.getPrimaryClip(getSystemService(ClipboardManager.class)` への呼び出しになる必要があります。 手動でこれらの置換を行うことはお勧めできません。 代わりに、BuildPlugin でこの操作を行います。

| Android クラス | Intune アプリ SDK の代替物 |
|--|--|
| android.content.ClipboardManager | MAMClipboard |
| android.content.pm.PackageManager | MAMPackageManagement |
| android.app.DownloadManager | MAMDownloadManagement |
### <a name="manifest-replacements"></a>マニフェストの置換
場合によっては、マニフェストと共に Java コードでも上記の一部のクラスの置換を実行する必要があります。 注意: 
* `android.support.v4.content.FileProvider` を参照するマニフェストは、`com.microsoft.intune.mam.client.support.v4.content.MAMFileProvider` に置き換える必要があります。

## <a name="androidx-libraries"></a>AndroidX ライブラリ
Android P と共に、Google は AndroidX と呼ばれるサポート ライブラリの新しい (名前が変更された) セットを発表しており、バージョン 28 が既存の android.support ライブラリの最新のメジャー リリースです。

Android サポート ライブラリとは異なり、Microsoft が AndroidX ライブラリの MAM バリアントを提供することはありません。 代わりに、AndroidX は任意のその他の外部ライブラリとしてテストする必要があり、ビルド プラグイン/ツールによって上書きされるように構成する必要があります。 Gradle のビルドでは、プラグイン構成の `includeExternalLibraries` フィールドに `androidx.*` を含めることによってこれを行うことができます。コマンド ライン ツールの呼び出しは、jar ファイルがすべて明示的に一覧表示されている必要があります。
## <a name="sdk-permissions"></a>SDK のアクセス許可

Intune アプリ SDK では、統合するアプリに対する次の 3 つの [Android システムのアクセス許可](https://developer.android.com/guide/topics/security/permissions.html)が必要になります。

* `android.permission.GET_ACCOUNTS` (必要に応じて実行時に要求)

* `android.permission.MANAGE_ACCOUNTS`

* `android.permission.USE_CREDENTIALS`

Azure Active Directory Authentication Library ([ADAL](https://azure.microsoft.com/documentation/articles/active-directory-authentication-libraries/)) では、仲介型認証を実行する場合にこれらのアクセス許可が必要になります。 これらのアクセス許可がアプリに付与されていない場合や、ユーザーによって取り消された場合、ブローカー (ポータル サイト アプリ) を必要とする認証フローは無効になります。

## <a name="logging"></a>ログ記録

ログに記録されたデータを最も有効に活用するには、ログを早い段階で初期化する必要があります。 一般的にログを初期化するには、`Application.onMAMCreate()` が最も効果的です。

アプリで MAM ログを受信するには、[Java ハンドラー](http://docs.oracle.com/javase/7/docs/api/java/util/logging/Handler.html)を作成、それを `MAMLogHandlerWrapper` に追加します。 これにより、すべてのログ メッセージに対してアプリケーション ハンドラーで `publish()` を呼び出します。

```java
/**
 * Global log handler that enables fine grained PII filtering within MAM logs.  
 *
 * To start using this you should build your own log handler and add it via
 * MAMComponents.get(MAMLogHandlerWrapper.class).addHandler(myHandler, false);  
 *
 * You may also remove the handler entirely via
 * MAMComponents.get(MAMLogHandlerWrapper.class).removeHandler(myHandler);
 */
public interface MAMLogHandlerWrapper {
    /**
     * Add a handler, PII can be toggled.
     *
     * @param handler handler to add.
     * @param wantsPII if PII is desired in the logs.    
     */
    void addHandler(final Handler handler, final boolean wantsPII);

    /**
     * Remove a handler.
     *
     * @param handler handler to remove.
     */
    void removeHandler(final Handler handler);
}
```



## <a name="enable-features-that-require-app-participation"></a>アプリによる処理を必要とする機能の有効化

アプリケーション保護ポリシーの中には、SDK 自体に実装できないものがいくつかあります。 アプリではいくつかの API を使用して、これらの機能を実行するために動作を制御することができます。この API は以下の `AppPolicy` インターフェイスで見つけることができます。 `AppPolicy` インスタンスを取得するには、`MAMPolicyManager.getPolicy` を使用します。

```java
/**
 * External facing application policies.
 */
public interface AppPolicy {

/**
 * Restrict where an app can save personal data.
 * This function is now deprecated. Please use getIsSaveToLocationAllowed(SaveLocation, String) instead
 * @return True if the app is allowed to save to personal data stores; false otherwise.
 */
@Deprecated
boolean getIsSaveToPersonalAllowed();

/**
 * Check if policy prohibits saving to a content provider location.
 *
 * @param location
 *            a content URI to check
 * @return True if location is not a content URI or if policy does not prohibit saving to the content location.
 */
boolean getIsSaveToLocationAllowed(Uri location);

/**
 * Determines if the SaveLocation passed in can be saved to by the username associated with the cloud service.
 *
 * @param service
 *           see {@link SaveLocation}.
 * @param username
 *           the username/email associated with the cloud service being saved to. Use null if a mapping between
 *           the AAD username and the cloud service username does not exist or the username is not known.
 * @return true if the location can be saved to by the identity, false if otherwise.
 */
boolean getIsSaveToLocationAllowed(SaveLocation service, String username);

/**
 * Whether the SDK PIN prompt is enabled for the app.
 *
 * @return True if the PIN is enabled. False otherwise.
 */
boolean getIsPinRequired();

/**
 * Whether the Intune Managed Browser is required to open web links.
 * @return True if the Managed Browser is required, false otherwise
 */
boolean getIsManagedBrowserRequired();

/**
 * Check if policy allows Contact sync to local contact list.
 *
 * @return True if Contact sync is allowed to save to local contact list; false otherwise.
 */
boolean getIsContactSyncAllowed();

/**
 * This method is intended for diagnostic/telemetry purposes only. It can be used to discover whether
 * file encryption is in use. File encryption is transparent to the app, and the app should not need
 * to make any business logic decisions based on this.
 * 
 * @return True if file encryption is in use.
 */
boolean diagnosticIsFileEncryptionInUse();

/**
 * Return the policy in string format to the app.
 *  
 * @return The string representing the policy.
 */
String toString();

}
```

> [!NOTE]
> `MAMPolicyManager.getPolicy` は、デバイスまたはアプリが Intune 管理ポリシーに従わない場合でも、常に null 以外のアプリ ポリシーを返します。

### <a name="example-determine-if-pin-is-required-for-the-app"></a>例: PIN がアプリケーションに必要なかどうかを確認します。

アプリケーションに独自の PIN ユーザー エクスペリエンスがあり、IT 管理者がアプリの PIN の入力を求めるように SDK を構成している場合は、それを無効にしたいことがあります。 IT 管理者が、現在のエンドユーザーのアプリ PIN ポリシーをこのアプリに展開したかどうかを判断するには、次のメソッドを呼び出します。

```java

MAMPolicyManager.getPolicy(currentActivity).getIsPinRequired();
```

### <a name="example-determine-the-primary-intune-user"></a>例: プライマリ Intune ユーザーを判別します。

AppPolicy で公開される API に加えて、ユーザー プリンシパル名で (**UPN**) も `MAMUserInfo`インターフェイス内で定義された `getPrimaryUser()` API によって公開されます。 UPN を取得するには、次のように呼び出します。

```java
MAMUserInfo info = MAMComponents.get(MAMUserInfo.class);
if (info != null) return info.getPrimaryUser();
```

MAMUserInfo インターフェイスの完全な定義を次に示します。

```java
/**
 * External facing user informations.
 *
 */
public interface MAMUserInfo {
       /**
        * Get the primary user name.
        *
        * @return the primary user name or null if the device is not enrolled.
        */
       String getPrimaryUser();
}
```

### <a name="example-determine-if-saving-to-device-or-cloud-storage-is-permitted"></a>例: デバイスまたはクラウド ストレージへの保存が許可されているかどうかを判断します。

多くのアプリでは、エンドユーザーがローカルまたはクラウド ストレージ サービスにファイルを保存する機能を実装しています。 Intune アプリ SDK を使用することで、データの漏えいを防ぐために、IT 管理者が組織に合ったポリシー制限を適用できます。  IT 部門で制御できるポリシーの 1 つとして、エンドユーザーが "個人用" の管理対象外データ ストアに保存できるかどうかというものがあります。 これには、ローカルの場所、SD カード、またはサード パーティ バックアップ サービスへの保存が含まれます。

**この機能を有効にするには、アプリによる処理が必要です。** アプリから直接個人またはクラウドの場所に保存することをアプリで許可する場合は、IT 管理者がある場所への保存を許可するかどうか制御できるように、この機能を実装する必要があります。 次の API では、現在の Intune 管理者のポリシーに従い、個人用ストアへの保存が許可されるかどうかを、アプリに知らせています。 これにより、エンドユーザーがアプリを介して個人のデータ ストアを使用できることをアプリで認識できるため、アプリでポリシーを適用できます。  

ポリシーが適用されているかどうかを判断するために、次の呼び出しを行います。

```java
MAMPolicyManager.getPolicy(currentActivity).getIsSaveToLocationAllowed(
SaveLocation service, String username);
```

`service` には、次の SaveLocations のうちいずれかを指定します。


    * SaveLocation.ONEDRIVE_FOR_BUSINESS
    * SaveLocation.LOCAL
    * SaveLocation.SHAREPOINT

ユーザーのポリシーがさまざまな場所にデータを保存することを許可するかどうかを判断する前のメソッドは、同じ **AppPolicy** クラス内の `getIsSaveToPersonalAllowed()` です。 この関数は現在**非推奨**になっており、使用しないようにする必要があります。次の呼び出しは `getIsSaveToPersonalAllowed()` と同じです：

```java
MAMPolicyManager.getPolicy(currentActivity).getIsSaveToLocationAllowed(SaveLocation.LOCAL, userNameInQuestion);
```

>[!NOTE]
> 問題の場所が、**SaveLocations** 列挙型に表示されない場合は、`SaveLocation.OTHER` を使用します。


## <a name="register-for-notifications-from-the-sdk"></a>SDK からの通知への登録

### <a name="overview"></a>概要
Intune アプリ SDK を使用すると、IT 管理者が選択的ワイプなどの特定のポリシーを展開したときに、アプリで動作を制御することできます。 IT 管理者がそのようなポリシーを展開すると、Intune サービスは SDK に通知を送信します。

アプリは、`MAMNotificationReceiver` を作成して `MAMNotificationReceiverRegistry` に登録することで、SDK からの通知に登録する必要があります。 これは、次の例に示すように、受信側と、`App.onCreate` で必要な通知の種類を指定することで行います。

```java
@Override
public void onCreate() {
  super.onCreate();
  MAMComponents.get(MAMNotificationReceiverRegistry.class)
    .registerReceiver(
      new ToastNotificationReceiver(),
      MAMNotificationType.WIPE_USER_DATA);
  }
```

### <a name="mamnotificationreceiver"></a>MAMNotificationReceiver

`MAMNotificationReceiver` インターフェイスでは、単に Intune サービスからの通知を受信します。 通知の中には、SDK によって直接処理されるものと、アプリによる処理が必要なものがあります。 アプリでは、通知から true または false を返す**必要があります**。 通知の結果として実行しようとした何らかのアクションが失敗した場合を除き、常に true を返す必要があります。

* この失敗は、Intune サービスにレポートされる場合があります。 レポートのシナリオ例として、IT 管理者がワイプを開始した後に、アプリがユーザー データのワイプに失敗した場合などがあります。

>[!NOTE]
> `MAMNotificationReceiver.onReceive` でブロックすることが安全です。これは、このコールバックは UI スレッドで実行されないためです。

SDK で定義されている `MAMNotificationReceiver` インターフェイスを以下に示します。

```java
/**
 * The SDK is signaling that a MAM event has occurred.
 *
 */
public interface MAMNotificationReceiver {

    /**
     * A notification was received.
     *
     * @param notification
     *            The notification that was received.
     * @return The receiver should return true if it handled the
     *   notification without error (or if it decided to ignore the
     *   notification). If the receiver tried to take some action in
     *   response to the notification but failed to complete that
     *   action it should return false.
     */
    boolean onReceive(MAMNotification notification);
}
```

### <a name="types-of-notifications"></a>通知の種類

アプリに次の通知が送信されます。その一部によって、アプリによる処理が要求される場合があります。

* **WIPE_USER_DATA**: この通知は、`MAMUserNotification` クラスで送信されます。 この通知を受信すると、アプリでは `MAMUserNotification` で渡された "企業" ID に関連するすべてのデータを削除する必要があります。 この通知は、現在、APP-WE サービスの登録解除中に送信されます。 ユーザーのプライマリ名は、通常、登録プロセス中に指定されます。 この通知に登録する場合、アプリがすべてのユーザー データが削除されたことを確認する必要があります。 登録しない場合、既定の選択的ワイプの動作が実行されます。

* **WIPE_USER_AUXILIARY_DATA**: Intune アプリ SDK に対して既定の選択的ワイプの実行を求めるが、ワイプが発生したときにいくつかの補助的なデータを削除する必要があるアプリは、この通知に登録できます。 この通知は単一 ID アプリには利用できません。複数 ID アプリにのみ送信されます。

* **REFRESH_POLICY**: この通知は、`MAMUserNotification` で送信されます。 この通知を受信した場合、キャッシュ済みの Intune ポリシーを無効にして更新する必要があります。 これは SDK によって処理されますが、何らかの永続的な方法で、ポリシーを使用する場合は、アプリによって処理する必要があります。

* **MANAGEMENT_REMOVED**: この通知は、`MAMUserNotification` で送信され、管理対象外になることをアプリに直前に通知します。 管理対象外になると、暗号化されたファイルの読み取り、MAMDataProtectionManager で暗号化されたデータの読み取り、暗号化されたクリップボードとの対話、それ以外の管理対象アプリのエコシステムへの参加ができなくなります。


> [!NOTE]
> アプリは `WIPE_USER_DATA` と `WIPE_USER_AUXILIARY_DATA` の両方の通知に登録することはできません。


## <a name="configure-azure-active-directory-authentication-library-adal"></a>Azure Active Directory Authentication Library (ADAL) の構成

まず、[GitHub の ADAL リポジトリ](https://github.com/AzureAD/azure-activedirectory-library-for-android)にある ADAL の統合ガイドラインを参照してください。

SDK では[認証](https://azure.microsoft.com/documentation/articles/active-directory-authentication-scenarios/)と条件付き起動シナリオを [ADAL](https://azure.microsoft.com/documentation/articles/active-directory-authentication-libraries/) に依存するため、アプリを [Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-whatis/) を使用して構成する必要があります。 構成値は、AndroidManifest メタデータを使用して SDK に伝達されます。

アプリを構成して適切な認証を有効にするには、AndroidManifest.xml のアプリのノードに次の内容を追加します。 これらの構成の中には、アプリで通常の認証に ADAL が使用される場合にのみ必要となるものがあります。この場合、アプリによって AAD への登録に使用される特定の値が必要になります。 これにより、AAD により 2 つ (アプリと SDK から 1 つずつ) の個別の登録値が認識されることによってエンドユーザーに対して認証が 2 回求められることがなくなります。

```xml
<meta-data
    android:name="com.microsoft.intune.mam.aad.Authority"
    android:value="https://AAD authority/" />
<meta-data
    android:name="com.microsoft.intune.mam.aad.ClientID"
    android:value="your-client-ID-GUID" />
<meta-data
    android:name="com.microsoft.intune.mam.aad.NonBrokerRedirectURI"
    android:value="your-redirect-URI" />
<meta-data
    android:name="com.microsoft.intune.mam.aad.SkipBroker"
    android:value="[true | false]" />
```

### <a name="adal-metadata"></a>ADAL メタデータ

* **Authority** は、使用中の AAD 機関です。 この値が存在しない場合は、AAD のパブリック環境が使用されます。
> [!NOTE]
> アプリケーションがソブリン クラウド対応である場合は、このフィールドを設定しないでください。

* **ClientID** は、使用する AAD ClientID です。 Azure AD に登録されている場合は、独自のアプリの ClientID を使用してください。 この値が存在しない場合は、Intune の既定値が使用されます。

* **NonBrokerRedirectURI** は、ブローカーを使用しない場合に使用する AAD リダイレクト URI です。 指定しない場合は、既定値の `urn:ietf:wg:oauth:2.0:oob` が使用されます。 この既定値は、ほとんどのアプリケーションに適しています。

* **SkipBroker** は、ブローカーのリダイレクト URI を使用するように ClientID が構成されていない場合に使用されます。 既定値は "false" です。
    * **ADAL を統合しない**アプリおよび**デバイス全体の仲介型の認証/SSO に参加しないアプリ**の場合、このプロパティを "true" に設定する必要があります。 この値が "true" の場合は、使用されるリダイレクト URI は、NonBrokerRedirectURI のみです。

    * デバイス全体にわたる SSO ブローカーをサポートしているアプリの場合、これを "false" にする必要があります。 値が "false" の場合、SDK はシステムでのブローカーの可用性を基にして、[`com.microsoft.aad.adal.AuthenticationContext.getRedirectUriForBroker()`](https://github.com/AzureAD/azure-activedirectory-library-for-android) の結果と NonBrokerRedirectURI の間のブローカーを選択します。 一般に、ブローカーはポータル サイト アプリまたは Azure Authenticator アプリから利用可能になります。

### <a name="common-adal-configurations"></a>ADAL の一般的な構成

ADAL を使用してアプリを構成する一般的な方法を次に示します。 アプリの構成を検索し、ADAL メタデータ パラメーター (上述) を必要な値に設定したことを確認します。 いずれの場合も、既定以外の環境では必要でも、一般的には不要である場合、Authority を指定できます。

1. **アプリに ADAL が統合されない場合:**

追加のマニフェスト値を構成する必要はありません。

2. **アプリに ADAL が統合される場合:**

    |必須の ADAL パラメーター| 値 |
    |--|--|
    | ClientID | アプリの ClientID (アプリが登録されるときに Azure AD によって生成される) |
    | SkipBroker | False |

必要に応じて、Authority と NonBrokerRedirectURI を指定できます。

次の手順を使用して Azure AD でアプリを登録します。

Azure portal で次の操作を行います。
1.  **[Azure Active Directory]** ブレードに移動します。
2.  **[アプリの登録]** を選択してアプリケーションを設定します。
3.  **[API アクセス]** 見出しの下の **[設定]** で、**必要なアクセス許可**を選択します。 
4.  **[+ 追加]** をクリックします。
5.  **[API を選択します]** をクリックします。 
6.  検索ボックスに「**Microsoft Mobile Application Management**」と入力します。
7.  API の一覧で **[Microsoft Mobile Application Management]** を選択し、[選択] をクリックします。
8.  **[Read and Write the User’s App Management Data]\(ユーザーのアプリ管理データの読み取りと書き込み\)** を選択します。
9.  **[完了]** をクリックします。
10. **[アクセス許可の付与]** をクリックして、**[はい]** をクリックします。 

Azure AD へのアプリケーションの登録については、[こちら](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications)を参照してください。 

以下の「[条件付きアクセス](#conditional-access)」の要件も参照してください。

3. **アプリは ADAL を統合しますが、仲介型認証/デバイス全体にわたる SSO をサポートしていません。**

    |必須の ADAL パラメーター| 値 |
    |--|--|
    | ClientID | アプリの ClientID (アプリが登録されるときに Azure AD によって生成される) |
    | SkipBroker | **True** |
    
    必要に応じて、Authority と NonBrokerRedirectURI を指定できます。


### <a name="conditional-access"></a>条件付きアクセス
条件付きアクセス (CA) は Azure Active Directory の[機能](https://docs.microsoft.com/azure/active-directory/develop/active-directory-conditional-access-developer)です。これを使用して、AAD リソースへのアクセスを制御できます。  [Intune 管理者は、CA ルールを定義できます](https://docs.microsoft.com/intune/conditional-access)。このルールで、Intune によって管理されるデバイスまたはアプリのみからのリソース アクセスを許可します。 必要に応じてアプリが確実にリソースにアクセスできるようにするには、以下の手順に従う必要があります。 アプリで AAD アクセス トークンを取得しないか、CA で保護できないリソースのみにアクセスする場合は、これらの手順をスキップしてもかまいません。
1. [ADAL の統合に関するガイドライン](https://github.com/AzureAD/azure-activedirectory-library-for-android#how-to-use-this-library)に従ってください。 
   特にブローカーの使用に関する手順 11 を参照してください。

2. [Azure Active Directory にアプリケーションを登録します](https://docs.microsoft.com/azure/active-directory/active-directory-app-registration)。 リダイレクト URI は、上記の ADAL の統合に関するガイドラインで確認できます。

3. 上記の項目 2 の [ADAL の一般的な構成](#common-adal-configurations)ごとにマニフェスト メタデータ パラメーターを設定します。

4. すべて正しく構成されていることをテストします。その場合、[Azure portal](https://portal.azure.com/#blade/Microsoft_Intune_DeviceSettings/ExchangeConnectorMenu/aad/connectorType/2) から[デバイス ベースの CA](https://docs.microsoft.com/intune/conditional-access-intune-common-ways-use) を有効にして、以下を確認します。
* アプリへのサインイン時に Intune ポータル サイトのインストールと登録が求められる
* 登録後、アプリへのサインインが正常に完了する。

5. アプリで Intune APP SDK の統合が提供されたら、msintuneappsdk@microsoft.com に連絡して、[アプリベース条件付きアクセス](https://docs.microsoft.com/intune/conditional-access-intune-common-ways-use#app-based-conditional-access)の承認済みアプリ リストへの追加を依頼します。

6. アプリが承認済みリストに追加されたら、[アプリベースの CA を構成](https://docs.microsoft.com/intune/app-based-conditional-access-intune-create)し、アプリへのサインインが正常に完了したことを確認して検証します。


## <a name="app-protection-policy-without-device-enrollment"></a>デバイス登録が不要なアプリの保護ポリシー

### <a name="overview"></a>概要
デバイス登録のない Intune アプリ保護ポリシー (APP-WE または MAM-WE とも呼ばれる) では、デバイスが Intune MDM に登録されていなくても Intune でアプリを管理できます。 デバイス登録の有無にかかわらず、APP-WE は動作します。 ポータル サイトは、デバイスにインストールするために必要ですが、ユーザーがポータル サイトにサインインし、デバイスを登録する必要はありません。

> [!NOTE]
> すべてのアプリは、デバイスの登録なしで、アプリの保護ポリシーをサポートする必要があります。

### <a name="workflow"></a>ワークフロー

アプリでは、新しいユーザー アカウントを作成するときにIntune アプリ SDK で管理するためにアカウントを登録する必要があります。 SDK は、APP-WE サービスでのアプリの登録の詳細を処理し、失敗した場合は、必要に応じて適切な時間間隔で登録を再試行します。

アプリは、Intune App SDK に対するクエリを実行して、登録済みユーザーのステータスを調べ、ユーザーが会社のコンテンツへのアクセスをブロックするかどうかを判断することもできます。 複数のアカウントを管理のために登録できますが、現在 APP-WE サービスに一度にアクティブに登録できるのは 1 つのアカウントのみです。 つまり、アプリでアプリ保護ポリシーを受け取ることができるのは一度に 1 つのアカウントのみです。

SDK の代わりに Azure Active Directory Authentication Library (ADAL) から適切なアクセス トークンを取得するコールバックを提供するには、アプリが必要です。 アプリがユーザー認証および独自のアクセス トークンを取得するために既に ADAL を使用していると見なされます。

アプリがアカウントを完全に削除するときは、アプリがそのユーザーのポリシーをこれ以上適用しないことを示すためにそのアカウントを登録解除する必要があります。 MAM サービスにユーザーが登録されていた場合、ユーザーの登録が解除され、アプリは消去されます。


### <a name="overview-of-app-requirements"></a>アプリの要件の概要

APP-WE 統合を実装するには、アプリが MAM SDK にユーザー アカウントを登録する必要があります。

1. アプリは、`MAMServiceAuthenticationCallback` インターフェイスのインスタンスを実装および登録_する必要があります_。 コールバック インスタンスをアプリケーションのライフ サイクルでできるだけ早い段階で登録する必要があります (通常はアプリケーション クラスの `onMAMCreate()` メソッド)。

2. ユーザー アカウントが作成され、ユーザーが正常に ADAL にサインインしたときに、アプリは、`registerAccountForMAM()` を呼び出す_必要があります_。

3. ユーザー アカウントが完全に削除されたときには、アプリは、`unregisterAccountForMAM()` を呼び出して Intune 管理からアカウントを削除する必要があります。

    > [!NOTE]
    > ユーザーがアプリから一時的にサインアウトする場合、アプリは `unregisterAccountForMAM()` を呼び出す必要はありません。 呼び出しでは、ユーザーの会社のデータを完全に削除するワイプを開始できます。


### <a name="mamenrollmentmanager"></a>MAMEnrollmentManager

すべての必要な認証および登録 API は、`MAMEnrollmentManager` インターフェイスにあります。 `MAMEnrollmentManager` の参照は、次のように取得できます。

```java
MAMEnrollmentManager mgr = MAMComponents.get(MAMEnrollmentManager.class);

// make use of mgr
```

返された `MAMEnrollmentManager` インスタンスは、null ではないことが保証されます。 API メソッドは、**認証**と**アカウント登録**という 2 つのカテゴリに分類されます。

> [!NOTE]
> `MAMEnrollmentManager` には、すぐに非推奨となる API メソッドがいくつか含まれています。 わかりやすくするために、次のコード ブロックでは、関連するメソッドと結果のコードのみを示します。

```java
package com.microsoft.intune.mam.policy;

public interface MAMEnrollmentManager {
    public enum Result {
        AUTHORIZATION_NEEDED,
        NOT_LICENSED,
        ENROLLMENT_SUCCEEDED,
        ENROLLMENT_FAILED,
        WRONG_USER,
        MDM_ENROLLED,
        UNENROLLMENT_SUCCEEDED,
        UNENROLLMENT_FAILED,
        PENDING,
        COMPANY_PORTAL_REQUIRED;
    }

    //Authentication methods
    interface MAMServiceAuthenticationCallback {
        String acquireToken(String upn, String aadId, String resourceId);
    }
    void registerAuthenticationCallback(MAMServiceAuthenticationCallback callback);
    void updateToken(String upn, String aadId, String resourceId, String token);

    //Registration methods
    void registerAccountForMAM(String upn, String aadId, String tenantId);
    void registerAccountForMAM(String upn, String aadId, String tenantId, String authority);
    void unregisterAccountForMAM(String upn);
    Result getRegisteredAccountStatus(String upn);
}
```

### <a name="account-authentication"></a>アカウントの認証

このセクションでは、`MAMEnrollmentManager` の認証 API メソッドとそれらの使用方法について説明します。

```java
interface MAMServiceAuthenticationCallback {
        String acquireToken(String upn, String aadId, String resourceId);
}
void registerAuthenticationCallback(MAMServiceAuthenticationCallback callback);
void updateToken(String upn, String aadId, String resourceId, String token);
```

1. アプリは、`MAMServiceAuthenticationCallback` インターフェイスを実装し、SDK が特定のユーザーの ADAL トークンとリソース ID を要求できるようにする必要があります。 `registerAuthenticationCallback()` メソッドを呼び出すことでコールバック インスタンスを `MAMEnrollmentManager` に提供する必要があります。 アプリのライフサイクルの早い段階で、登録の再試行またはアプリ保護ポリシーの更新チェックインのためにトークンが必要になることがあるので、コールバックの登録の理想的な場所は、アプリの `MAMApplication` サブクラスの `onMAMCreate()` メソッドです。

2. `acquireToken()` メソッドは、特定のユーザーの要求されたリソース ID のアクセス トークンを取得する必要があります。 要求されたトークンを取得できない場合は、null を返す必要があります。

3. SDK が `acquireToken()` を呼び出すときにアプリがトークンを提供することができない場合 (たとえば、サイレント認証が失敗し、UI を表示するには不都合な期間である場合)、アプリは、`updateToken()` メソッドを呼び出すことによって後でトークンを提供できます。 `acquireToken()` の前回の呼び出しで要求されたものと同じ UPN、AAD ID、およびリソース ID を最後に取得されたトークンと合わせて `updateToken()` に渡す必要があります。 アプリは、指定されたコールバックから null が戻された後に、できるだけ早く、このメソッドを呼び出す必要があります。

> [!NOTE]
> SDK は、トークンを取得するために `acquireToken()` を定期的に呼び出すので、`updateToken()` の呼び出しは厳密には必須ではありません。 ただし、これは登録とアプリ保護ポリシーのチェックインを適切なタイミングで完了するためには役立つので推奨されます。


### <a name="account-registration"></a>アカウントの登録

このセクションでは、`MAMEnrollmentManager` のアカウント登録 API メソッドとそれらの使用方法について説明します。

```java
void registerAccountForMAM(String upn, String aadId, String tenantId);
void registerAccountForMAM(String upn, String aadId, String tenantId, String authority);
void unregisterAccountForMAM(String upn);
Result getRegisteredAccountStatus(String upn);
```

1. アカウントを管理用に登録するには、アプリで `registerAccountForMAM()` を呼び出す必要があります。 ユーザー アカウントは UPN と AAD ユーザー ID の両方で識別されます。 登録データをユーザーの AAD テナントと関連付けるには、テナント ID も必要です。 ユーザーの機関は特定のソブリン クラウドに対する登録を許可するために指定することもできます。詳細については、「[ソブリン クラウドの登録](#sovereign-cloud-registration)」を参照してください。  SDK は MAM サービスで特定のユーザー向けにアプリを登録しようとする場合があります。登録が失敗した場合、アカウントが登録されるまで定期的に登録を再試行します。 再試行の期間は通常 12 ～ 24 時間です。 SDK は、通知を使用して非同期的に登録の試行の状態を示します。

2. AAD 認証が必要なため、ユーザー アカウントを登録する最適なタイミングは、ユーザーがアプリケーションにサインインし、ADAL を使用して正常に認証した後です。
    * [`AuthenticationResult`](https://github.com/AzureAD/azure-activedirectory-library-for-android) オブジェクトの一部として、ユーザーの AAD ID とテナント ID が ADAL 認証呼び出しから返されます。 テナント ID は、`AuthenticationResult.getTenantID()` メソッドから取得されます。
    * ユーザーに関する情報は、`AuthenticationResult.getUserInfo()` から取得される `UserInfo` 型のサブオブジェクトで見つかり、AAD ユーザー ID は `UserInfo.getUserId()` を呼び出すオブジェクトから取得されます。

3. アカウントを Intune 管理から登録解除するには、アプリで `unregisterAccountForMAM()` を呼び出す必要があります。 アカウントが正常に登録されて管理される場合、SDK は、アカウントの登録を解除し、そのデータを消去します。 アカウントの定期的な登録の再試行は停止されます。 SDK は、通知を使用して非同期的に登録の試行の状態を示します。

### <a name="sovereign-cloud-registration"></a>ソブリン クラウドの登録

[ソブリン クラウド対応](https://www.microsoft.com/en-us/trustcenter/cloudservices/nationalcloud)のアプリケーションでは、`authority` を `registerAccountForMAM()` に指定する**必要**があります。  これは、ADAL の [1.14.0 以上](https://github.com/AzureAD/azure-activedirectory-library-for-android/releases/tag/v1.14.0)の acquireToken extraQueryParameters で `instance_aware=true` を指定してから、AuthenticationCallback AuthenticationResult で `getAuthority()` を呼び出すことで取得できます。

```
mAuthContext.acquireToken(this, RESOURCE_ID, CLIENT_ID, REDIRECT_URI, PromptBehavior.FORCE_PROMPT, "instance_aware=true",
        new AuthenticationCallback<AuthenticationResult>() {
            @Override
            public void onError(final Exception exc) {
                // authentication failed
            }

            @Override
            public void onSuccess(final AuthenticationResult result) {
                mAuthority = result.getAuthority();
                // handle other parts of the result
            }
        });
```

> [!NOTE]
> AndroidManifest.xml メタデータ機関は設定しないでください。
<br/>
```
<meta-data
    android:name="com.microsoft.intune.mam.aad.Authority"
    android:value="https://AAD authority/" />
```

> [!NOTE]
> `MAMServiceAuthenticationCallback::acquireToken()` メソッドに機関が正しく設定されていることを確認してください。


#### <a name="currently-supported-sovereign-clouds"></a>現在サポートされているソブリン クラウド

1. アーリントン

### <a name="important-implementation-notes"></a>実装に関する重要なメモ

#### <a name="authentication"></a>認証

* アプリが `registerAccountForMAM()` を呼び出したときに、`MAMServiceAuthenticationCallback` インターフェイスで直後に異なるスレッドでコールバックを受け取る場合があります。 **MAMService トークン**の取得を早めるために、アプリがアカウントを登録する前に ADAL から専用のトークンを取得しているの理想的です。 アプリが、コールバックから有効なトークンを返す場合は、登録処理が続行され、アプリが通知を使用して最終的な結果を取得します。

* アプリが有効な AAD トークンを返さない場合、登録の試行の最終的な結果は `AUTHENTICATION_NEEDED` になります。 アプリが通知を介してこの結果を受信する場合、アプリは、**MAMService トークン**を取得して `updateToken()` メソッドを呼び出してもう一度登録プロセスを開始することで登録プロセスを早めます。 ただし、SDK は登録を定期的に再試行してトークンを取得するためのコールバックを呼び出すので、これは確実な要件_ではありません_。

* アプリの登録済みの `MAMServiceAuthenticationCallback` は、定期的なアプリ保護ポリシー更新チェックイン時にトークンを取得するためにも呼び出されます。アプリが要求されたときにトークンを提供できない場合、通知は得られませんが、トークンの取得を試行する必要があり、チェックイン プロセスの時間を短縮するために次の便利な時刻に `updateToken()` を呼び出す必要があります。 トークンが提供されていない場合、次のチェックインの試行時にコールバックも引き続き呼び出されます。

* ソブリン クラウドのサポートには、機関の指定が必要です。
#### <a name="registration"></a>登録

* 参考までに、登録メソッドはべき等です。たとえば、`registerAccountForMAM()` はアカウントのみを登録し、アカウントがまだ登録されていない場合はアプリを登録しようとします。`unregisterAccountForMAM()` はアカウントが現在登録されている場合にのみ登録解除します。 後続の呼び出しは操作不要なので、これらのメソッドを複数回呼び出しても弊害はありません。 さらに、これらのメソッドの呼び出しと結果の通知の対応は保証されません。つまり、既に登録されている ID のために `registerAccountForMAM` が呼び出された場合、その ID の通知は再び送信されないことがあります。 SDK では、バック グラウンドで定期的に登録を試みることがあり、登録は、Intune サービスから受信したワイプ要求によって発生する可能性があるので、これらのメソッドへの呼び出しに対応していない通知が送信される可能性があります。

* 登録メソッドは、任意の数の異なる ID のために呼び出すことができますが、現在、正常に登録できるのは、1 つのユーザー アカウントだけです。 Intune のライセンスが付与され、アプリの保護ポリシーの対象となる複数のユーザー アカウントが登録される場合、またはほとんど同じ時刻に登録される場合、どのアカウントが競合に勝つかは保証されていません。

* 最後に、`MAMEnrollmentManager` に対してクエリを実行し、特定のアカウントが登録されているかどうかを確認し、`getRegisteredAccountStatus` メソッドを使用して現在のステータスを取得することができます。 指定したアカウントが登録されていない場合、このメソッドは **null** を返します。 アカウントが登録されている場合、このメソッドは、`MAMEnrollmentManager.Result` 列挙のいずれかのメンバーとしてアカウントのステータスを返します。

### <a name="result-and-status-codes"></a>結果とステータス コード

アカウントが最初に登録されているときに、`PENDING` 状態で始まり、最初の MAM サービスの登録の試行が完了したことを示します。 登録の試行が終了すると、次の表の結果コードのいずれかで通知が送信されます。 さらに、`getRegisteredAccountStatus()` メソッドは、アカウントのステータスを返すので、アプリは、そのユーザーの会社のコンテンツへのアクセスがブロックされているかどうかを常に特定できます。 登録の試行に失敗した場合、アカウントのステータスは、バック グラウンドで SDK が登録を再試行するときに随時変更される可能性があります。

|結果コード | 説明 |
| -- | -- |
|AUTHORIZATION_NEEDED | この結果は、トークンがアプリの登録済みの `MAMServiceAuthenticationCallback` インスタンスによって提供されていないこと、または指定されたトークンが無効なことを示します。  アプリは、可能な場合は、有効なトークンを取得し、`updateToken()` を呼び出す必要があります |
| NOT_LICENSED | Intune で、ユーザーがライセンスされていない、または Intune MAM サービスへの接続に失敗しました。  管理されていない (標準の) 状態で、アプリが続行され、ユーザーがブロックされていない必要があります。  将来的にユーザーがライセンスされる場合、登録が定期的に再試行されます。 |
| ENROLLMENT_SUCCEEDED | 登録の試行が成功したか、ユーザーが既に登録されています。  登録に成功する場合は、この通知の前にポリシーの更新通知が送信されます。  会社のデータへのアクセスが許可されます。 |
| ENROLLMENT_FAILED | 登録の試行が失敗しました。  さらに詳細な情報がデバイス ログにあります。  ユーザーが Intune にライセンスされていることが以前に判断されたために、アプリはこの状態で、会社へのアクセスを許可しません。|
| WRONG_USER | デバイスごとに 1 つのユーザーだけが、MAM サービスにアプリを登録できます。  別のユーザーとして正常に登録するためには、登録されているすべてのアプリが最初に登録解除される必要があります。  それ以外の場合、このアプリは、プライマリ ユーザーとして登録する必要があります。  このチェックは、ライセンスチェックの後に実行されるので、アプリが正常に登録されるまで、ユーザーは企業データへのアクセスをブロックされる必要があります。|
| UNENROLLMENT_SUCCEEDED | 登録解除が正常に完了しました。|
| UNENROLLMENT_FAILED | 登録解除要求が失敗しました。  さらに詳細な情報がデバイス ログにあります。 |
| PENDING | ユーザーの初期登録の試行が進行中です。  アプリは、登録の結果がわかるまで、会社のデータへのアクセスをブロックできますが、この処理は必須ではありません。 |
| COMPANY_PORTAL_REQUIRED | Intune でユーザーがライセンスされていますが、ポータル サイト アプリがデバイスにインストールされるまで、アプリを登録することはできません。 Intune アプリ SDK は、特定のユーザーのアプリへのアクセスをブロックし、ポータル サイト アプリ (詳細については以下を参照してください) をインストールすることをユーザーに指示します。 |


### <a name="company-portal-requirement-prompt-override-optional"></a>ポータル サイトの要件のプロンプトのオーバーライド (省略可能)

`COMPANY_PORTAL_REQUIRED` の結果が受信された場合、SDK は登録が要求された対象の ID を使用したアクティビティの使用をブロックします。 代わりに、SDK は、それらアクティビティでポータル サイトをダウンロードするためのプロンプトを表示させます。 アプリでこの動作を回避する場合は、アクティビティで `MAMActivity.onMAMCompanyPortalRequired` を実装できます。

このメソッドは、SDK が既定の UI のブロックを表示する前に呼び出されます。 アプリが、アクティビティ ID を変更するか、登録しようとしたユーザーの登録を解除した場合、SDK は、アクティビティはブロックしません。 この場合、会社のデータのリークを防ぐことはアプリの責任です。 アクティビティ ID を変更できるのは、(後述の) 複数 ID アプリのみであることに注意してください。

(ビルド ツールによってその変更が行われるため) 明示的に `MAMActivity` を継承しませんが、引き続きこの通知を処理する必要がある場合、代わりに `MAMActivityBlockingListener` を実装できます。

### <a name="notifications"></a>通知

登録要求が完了したことをアプリに通知するために新しい種類の `MAMNotification` が追加されました。  「[SDK からの通知の登録](#register-for-notifications-from-the-sdk)」 セクションで説明されているように、`MAMNotificationReceiver` インターフェイスから `MAMEnrollmentNotification` を受信します。

```java
public interface MAMEnrollmentNotification extends MAMUserNotification {
    MAMEnrollmentManager.Result getEnrollmentResult();
}
```

`getEnrollmentResult()` メソッドは、登録要求の結果を返します。  `MAMEnrollmentNotification` は、`MAMUserNotification` を拡張するので、登録が試行されたユーザーの ID も利用できます。 アプリは、これらの通知を受信するために `MAMNotificationReceiver` インターフェイスを実装する必要があります。詳細については、「[SDK からの通知の登録](#register-for-notifications-from-the-sdk)」セクションを参照してください。

登録通知を受け取ると、登録済みユーザーのアカウントのステータスが変更されることがありますが、場合によっては変更されないことがあります (たとえば、`WRONG_USER` などのより多くの情報がある結果の後に `AUTHORIZATION_NEEDED` 通知を受信した場合、より多くの情報がある結果がアカウントのステータスとして維持されます)。


## <a name="protecting-backup-data"></a>バックアップ データの保護

Android Marshmallow (API 23) 以降、Android ではアプリのデータをバックアップする方法が 2 つになりました。 各オプションはアプリで使用でき、Intune データ保護が正しく実装されていることを確認するには異なる手順が必要になります。 適切なデータ保護の動作に必要な、対応するアクションについては、次の表で確認することができます。  バックアップ方法の詳細については、[Android API ガイド](http://developer.android.com/guide/topics/data/backup.html)を参照してください。

### <a name="auto-backup-for-apps"></a>アプリの自動バックアップ

Android では、アプリのターゲット API に関係なく、Android Marshmallow デバイス上のアプリのために、[自動完全バックアップ](https://developer.android.com/guide/topics/data/autobackup.html)が Google Drive に提供されるようになりました。 AndroidManifest.xml で、明示的に `android:allowBackup` を **false** に設定すると、アプリは Android でバックアップのためにキューに入れられなくなり、"企業" データはアプリ内に残ります。 この場合、これ以上何もする必要はありません。

ただし、`android:allowBackup` がマニフェスト ファイルで指定されていない場合でも、`android:allowBackup` 属性は既定で true に設定されます。 つまり、すべてのアプリ データがユーザーの Google ドライブ アカウントに自動的にバックアップされます。これは既定の動作で、**データ漏えいのリスク**を引き起こすものです。 したがって、データ保護が適用されるようにするために、SDK を変更する必要があります。その概要について以下に示します。  アプリを Android Marshmallow デバイスで実行する場合は、以下のガイドラインに従って、顧客データを適切に保護することが重要です。  

Intune では、XML でカスタム ルールを定義する機能など、Android から利用可能な[自動バックアップ機能](https://developer.android.com/guide/topics/data/autobackup.html)を利用できますが、データを保護するには以下の手順に従う必要があります。

1. アプリで専用のカスタム BackupAgent を使用**しない**場合、既定の MAMBackupAgent を使用して、Intune ポリシー準拠の自動完全バックアップを可能にすることができます。 アプリのマニフェストに次を配置します。

    ```xml
    android:fullBackupOnly="true"
    android:backupAgent="com.microsoft.intune.mam.client.app.backup.MAMDefaultBackupAgent"
    ```


2. **[省略可能]** 省略可能なカスタム BackupAgent を実装した場合は、MAMBackupAgent または MAMBackupAgentHelper を使用することを確認する必要があります。 次のセクションを参照してください。 Android M 以上でのバックアップが簡易化される、Intune の **MAMDefaultFullBackupAgent** (手順 1 で説明) の使用に切り替えることを検討してください。

3. アプリで受信する必要がある完全バックアップの種類 (フィルター適用なし、フィルター適用、なし) を決定する際に、アプリで属性 `android:fullBackupContent` を true、false、または XML リソースに設定する必要があります。

4. その後で、マニフェストで `android:fullBackupContent` に配置するものはすべて、`com.microsoft.intune.mam.FullBackupContent` という名前のメタデータにコピー_**する必要があります**_。

    **例 1**: 例外なしにアプリで完全バックアップを実行する場合、`android:fullBackupContent` 属性と `com.microsoft.intune.mam.FullBackupContent` メタデータ タグの両方を **true** に設定します。

    ```xml
    android:fullBackupContent="true"
    ...
    <meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:value="true" />  
    ```

    **例 2**: アプリでカスタム BackupAgent を使用して、完全な Intune ポリシー互換の自動バックアップを停止する場合は、この属性とメタデータ タグを **false** に設定する必要があります。

    ```xml
    android:fullBackupContent="false"
    ...
    <meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:value="false" />  
    ```

    **例 3**: アプリで XML ファイルで定義したカスタム ルールに従って完全バックアップを使用する場合は、この属性とメタデータ タグを同じ XML リソースに設定してください。

    ```xml
    android:fullBackupContent="@xml/my_scheme"
    ...
    <meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:resource="@xml/my_scheme" />  
    ```


### <a name="keyvalue-backup"></a>キー/値のバックアップ

すべての API 8+ で[キー/値のバックアップ](https://developer.android.com/guide/topics/data/keyvaluebackup.html) オプションを使用して、アプリ データを [Android バックアップ サービス](https://developer.android.com/google/backup/index.html)にアップロードすることができます。 アプリのユーザーごとのデータの量は 5 MB に制限されています。 キー/値のバックアップを使用する場合、**BackupAgentHelper** または **BackupAgent** を使用する必要があります。

### <a name="backupagenthelper"></a>BackupAgentHelper

Android のネイティブな機能と Intune MAM 統合の両方の面で、BackupAgentHelper の実装は BackupAgent よりも簡単です。 BackupAgentHelper を使用すると、開発者は、**FileBackupHelper** および **SharedPreferencesBackupHelper** に、それぞれ、ファイル全体または共有の設定を登録することができ、これらは、作成時に BackupAgentHelper に追加されます。 Intune MAM で、BackupAgentHelper を使用するには、次の手順に従います。

1. BackupAgentHelper で従って、複数 ID のバックアップを使用するには、「[Extending BackupAgentHelper](https://developer.android.com/guide/topics/data/keyvaluebackup.html#BackupAgentHelper)」(BackupAgent の拡張) についての Android のガイドに従います。

2. クラスで BackupAgentHelper、FileBackupHelper、および SharedPreferencesBackupHelper と同等の MAM を拡張します。

|Android クラス | MAM の同等クラス |
|--|--|
|BackupAgentHelper |MAMBackupAgentHelper |
|FileBackupHelper | MAMFileBackupHelper
|SharedPreferencesBackupHelper| MAMSharedPreferencesBackupHelper|

複数 ID のバックアップと復元を正常に実行するために、以下のガイドラインに従います。

### <a name="backupagent"></a>BackupAgent

BackupAgent を使用すると、バックアップの対象とするデータをより明示的に指定することができます。 実装に対する開発者の責任が大きくなるため、Intune からの適切なデータ保護を適用するために必要となる手順が増加します。 開発者が作業のほとんどを担うことで、Intune 統合は少し複雑になります。

**MAM の統合:**

1. [キー/値のバックアップ](https://developer.android.com/guide/topics/data/keyvaluebackup.html)に関する Android ガイド (特に「[Extending BackupAgent](https://developer.android.com/guide/topics/data/keyvaluebackup.html#BackupAgent)」(BackupAgent の拡張) セクション) をよく読み、BackupAgent の実装が Android のガイドラインに従っていることを確認してください。

2. クラスで `MAMBackupAgent` を拡張します。

**複数 ID のバックアップ:**

1. バックアップを開始する前に、バックアップする予定のファイルまたはデータのバッファーの**複数 ID によるバックアップが実際に IT 管理者によって許可されている**ことを確認してください。 これを判断するために、`MAMFileProtectionManager` および `MAMDataProtectionManager` で `isBackupAllowed` 関数を提供しています。 ファイルまたはデータ バッファーのバックアップが許可されていない場合、バックアップに引き続き含まれないようにする必要があります。

2. バックアップ中のある時点で、手順 1 で確認したファイルの ID をバックアップする場合は、データの抽出元ファイルで `backupMAMFileIdentity(BackupDataOutput data, File … files)` を呼び出す必要があります。 これにより、自動的に新しいバックアップ エンティティが作成され、 `BackupDataOutput` に書き込まれます。 これらのエンティティは、復元時に自動的に使用されます。

**複数 ID による復元:**

データのバックアップ ガイドは、アプリケーションのデータを復元するための一般的なアルゴリズムを指定し、「[Extending BackupAgent](https://developer.android.com/guide/topics/data/keyvaluebackup.html#BackupAgent)」(BackupAgent の拡張) セクションでサンプル コードを提供します。 複数 ID による復元を正常に実行するは、次の点に特に注意して、このコード サンプルで提供される一般的な構造に従う必要があります。

1. `while(data.readNextHeader())`* ループを使用して、バックアップ エンティティを処理する必要があります。

2. `data.getKey()`* が `onBackup` で記述したキーに一致しない場合は、`data.skipEntityData()`* を呼び出す必要があります。 この手順を実行しないと、復元が失敗することがあります。

3. 自動的に記述するエンティティが失われるので、`while(data.readNextHeader())`* 構造体内のバックアップのエンティティを消費しているときに返されないようにします。

* ここで `data` は、復元時にご利用のアプリに渡す **MAMBackupDataInput** のローカル変数の名前です。

## <a name="multi-identity-optional"></a>複数 ID (省略可能)

### <a name="overview"></a>概要
既定では、Intune アプリ SDK はポリシーをアプリ全体に適用します。 複数 ID は、ID 単位のレベルでポリシーを適用できるようにするオプションの Intune アプリ保護機能です。 これには、他のアプリ保護機能よりはるかに多くのアプリの参加が必要です。
> [!NOTE]
>  適切なアプリの参加が不足していると、データのリークや他のセキュリティの問題が発生する場合があります。

ユーザーがデバイスまたはアプリを登録すると、SDK はこの ID を登録し、それをプライマリ Intune 管理対象 ID であると判断します。 アプリの他のユーザーは、無制限のポリシー設定を持つ管理対象外として扱われます。

> [!NOTE]
> 現時点では、サポートされる Intune 管理対象 ID はデバイスあたり 1 つだけです。

ID は文字列として簡単に定義されます。 ID は**大文字と小文字を区別されず**、SDK に ID を要求すると返される ID は、大文字と小文字の使い分けが ID 設定時の本来のものと異なる可能性があります。

アプリは、アクティブな ID を変更しようとするときに、SDK に通知する*必要があります*。 また、場合によっては、SDK は ID の変更が必要なときにもアプリに通知します。 ただし、ほとんどの場合、MAM は UI で表示されているデータまたは指定された時刻のスレッドに使用されるデータを把握することはできません。データのリークを避けるために、適切な ID の設定はアプリに依存します。 後続のセクションでは、アプリのアクションを必要とするいくつかの特定のシナリオが呼び出されます。
### <a name="enabling-multi-identity"></a>複数 ID を有効にする

既定では、すべてのアプリが単一 ID アプリと見なされます。 AndroidManifest.xml に次のメタデータを配置することでアプリが複数 ID に対応していることを宣言できます。

```xml
  <meta-data
    android:name="com.microsoft.intune.mam.MAMMultiIdentity"
    android:value="true" />
```

### <a name="setting-the-identity"></a>ID の設定

開発者は、次のレベルで降順にアプリ ユーザーの ID を設定できます。

  1. スレッド レベル
  2. コンテキスト (通常はアクティビティ) レベル
  3. プロセス レベル

スレッド レベルで設定された ID は、プロセス レベルで設定された ID よりも優先されるコンテキスト レベルで設定された ID よりも優先されます。 コンテキストで設定された ID は、適切な関連するシナリオにのみ使用されます。 ファイル IO 操作などにコンテキストは関連付けられません。 ほとんどの場合、アプリはアクティビティのコンテキスト ID を設定します。 アプリは、アクティビティの ID が同じ ID に設定されない限り、管理されている ID のデータを表示*できません*。 一般に、プロセス レベル ID は、アプリがすべてのスレッドで一度に単一のユーザーだけが操作する場合にのみ役立ちます。 多くのアプリは、この ID を利用する必要がない可能性があります。

`MAMPolicyManager` の次のメソッドは、ID を設定し、以前に設定された ID 値を取得するために使用できます。

```java
  public static void setUIPolicyIdentity(final Context context, final String identity, final MAMSetUIIdentityCallback mamSetUIIdentityCallback);

  public static String getUIPolicyIdentity(final Context context);

  public static MAMIdentitySwitchResult setProcessIdentity(final String identity);

  public static String getProcessIdentity();

  public static MAMIdentitySwitchResult setCurrentThreadIdentity(final String identity);

  public static String getCurrentThreadIdentity();

/**
   * Get the current app policy. This does NOT take the UI (Context) identity into account.
   * If the current operation has any context (e.g. an Activity) associated with it, use the overload below.
   */
  public static AppPolicy getPolicy();

  /**
  * Get the current app policy. This DOES take the UI (Context) identity into account.
   * If the current operation has any context (e.g. an Activity) associated with it, use this function.
   */
  public static AppPolicy getPolicy(final Context context);


  public static AppPolicy getPolicyForIdentity(final String identity);

  public static boolean getIsIdentityManaged(final String identity);
  ```

>[!NOTE]
> null に設定することで、アプリの ID をクリアすることができます。
>
> アプリ保護ポリシーがない ID として空の文字列を使用することができます。

#### <a name="results"></a>結果
ID を設定するために使用されるすべてのメソッドは、`MAMIdentitySwitchResult` を使用して結果の値を返します。 返される値は次の 4 つです。

| 戻り値 | 通信の種類 |
|--|--|
| SUCCEEDED | ID 変更が正常に行われました。 |
| NOT_ALLOWED  | ID は変更できません。 これは、現在のスレッドに別の ID が設定されているときに、UI (コンテキスト) ID を設定しようした場合にも発生します。 |
| CANCELLED | ユーザーが ID 変更を取り消しました。通常、この取り消しは、PIN または認証プロンプトで [戻る] ボタンを押して行われます。 |
| FAILED | 不明な理由により、ID 変更が失敗しました。|

アプリは、企業データを表示または使用する前に、ID の切り替えが成功していることを確認する*必要があります*。 現時点では、プロセスとスレッド ID の切り替えは、常に複数の ID が有効なアプリに対して成功しますが、エラー条件を追加するための権限を予約します。 UI ID の切り替えは、スレッド ID と競合している場合、またはユーザーが条件付きの起動要件によって取り消した場合に (PIN 画面で戻るボタンを押すなど)、無効な引数で失敗する可能性があります。


コンテキスト ID を設定する場合、結果は非同期的にレポートされます。 コンテキストがアクティビティの場合、ユーザーが PIN または企業資格情報の入力が必要になる可能性がある条件付きの起動が実行されるまで、SDK は ID 変更が正常に行われたかどうかがわかりません。 アプリはこの結果を受信するために `MAMSetUIIdentityCallback` の実装が必要になります。このパラメーターに null を渡すことができます。

```java
    public interface MAMSetUIIdentityCallback {
        void notifyIdentityResult(MAMIdentitySwitchResult identitySwitchResult);
  }
```

アクティビティの ID は、`MAMActivity` を呼び出す代わりに `MAMPolicyManager.setUIPolicyIdentity` のメソッドを使用して直接設定することもできます。 これを行うには、次のメソッドを使用します。

```java
     public final void switchMAMIdentity(final String newIdentity);
```

アプリでアクティビティの ID 変更の試行結果通知を受ける必要がある場合は、`MAMActivity` のメソッドをオーバーライドすることもできます。

``` java
    public void onSwitchMAMIdentityComplete(final MAMIdentitySwitchResult result);
```

>[!NOTE]
> ID の切り替えには、アクティビティの再作成が必要になる場合があります。 その場合、`onSwitchMAMIdentityComplete` コールバックはアクティビティの新しいインスタンスに配信されます。


### <a name="implicit-identity-changes"></a>暗黙的な ID 変更

アプリで ID を設定できるだけでなく、スレッドまたはコンテキストの ID は、アプリ保護ポリシーが適用されている別の Intune の管理対象アプリのデータに基づいて変更できます。

#### <a name="examples"></a>例

  1. アクティビティが別の MAM アプリによって送信された`Intent`から起動された場合、そのアクティビティの ID は、`Intent`の送信時に他のアプリで有効な ID に基づいて設定されます。

  2.  サービスについては、スレッドの ID は、`onStart` または `onBind` 呼び出しの期間に同様に設定されます。 `onBind` から返される `Binder` の呼び出しでも、スレッド ID が一時的に設定されます。

  3. `ContentProvider` の呼び出しでは同様に、それらの期間にスレッド ID を設定します。


  さらに、アクティビティとのユーザー対話により、暗黙的な ID 切り替えが行われる場合があります。

  **例:** ユーザーが `Resume` 中に認証プロンプトを取り消した場合、空の ID に暗黙的に切り替えられます。

  アプリはこれらの変更を認識し、必要に応じて禁止することができます。 `MAMService` および `MAMContentProvider` は、サブクラスでオーバーライドできる以下のメソッドを公開します。

  ```java
  public void onMAMIdentitySwitchRequired(final String identity,
    final AppIdentitySwitchResultCallback callback);
  ```

  `MAMActivity` クラスでは、メソッドには次の追加のパラメーターがあります。

  ```java
  public void onMAMIdentitySwitchRequired(final String identity,
    final AppIdentitySwitchReason reason,
    final AppIdentitySwitchResultCallback callback);
  ```

  * `AppIdentitySwitchReason` は、暗黙的な切り替えのソースをキャプチャし、値 `CREATE`、`RESUME_CANCELLED`、および `NEW_INTENT` を受け入れることができます。  `RESUME_CANCELLED` の理由は、アクティビティの再開時に、PIN、認証、または他のコンプライアンス UI が表示され、ユーザーがその UI を取り消そうとした場合 (通常は、[戻る] ボタンを使用) に使用されます。


  * `AppIdentitySwitchResultCallback` は次のとおりです。

    ```java
    public interface AppIdentitySwitchResultCallback {
        /**
         * @param result
         *            whether the identity switch can proceed.
         */
        void reportIdentitySwitchResult(AppIdentitySwitchResult result);
    }
    ```

    ここで ```AppIdentitySwitchResult``` は SUCCESS または FAILURE です。

`MAMService.onMAMBind` から返される Binder によるものを除く、すべての暗黙的な ID 変更に対してメソッド `onMAMIdentitySwitchRequired` が呼び出されます。 `onMAMIdentitySwitchRequired` の既定の実装は次のメソッドを直ちに呼び出します。

* 理由が RESUME_CANCELLED の場合は `reportIdentitySwitchResult(FAILURE)`。

* 他のすべての場合は `reportIdentitySwitchResult(SUCCESS)`。

  ほとんどのアプリでは別の方法で ID 切り替えをブロックしたり、遅延させたりする必要はありませんが、アプリで必要な場合は次の点を考慮する必要があります。

  * ID 切り替えがブロックされている場合、`Receive` 共有設定でデータ受信が禁止されている場合と同じ結果になります。

  * サービスがメイン スレッドで実行されている場合、`reportIdentitySwitchResult` を同期的に呼び出す**必要があります**。そうしないと、UI スレッドがハングします。

  * **アクティビティ**作成の場合、`onMAMCreate` の前に `onMAMIdentitySwitchRequired` が呼び出されます。 アプリで ID 切り替えを許可するかどうかを判断するために UI を表示する必要がある場合、その UI を*別*のアクティビティを使用して表示する必要があります。

  * **アクティビティ**では、RESUME_CANCELLED という理由で空の ID への切り替えが要求された場合、アプリは再開されたアクティビティを変更し、その ID 切り替えに適したデータを表示する必要があります。  これができない場合、アプリは切り替えを拒否する必要があり、ユーザーは再開 ID のポリシーへの準拠を再度求められます (たとえば、アプリの PIN 入力画面が表示されます)。

    > [!NOTE]
    > 複数 ID のアプリは常に、管理対象と管理対象外の両方のアプリからデータを受信します。 アプリは、管理された方法で管理対象 ID からのデータを処理する必要があります。

  要求された ID が管理対象 (`MAMPolicyManager.getIsIdentityManaged` を使用して確認します) であるが、アプリでそのアカウントを使用できない場合 (電子メール アカウントなどのアカウントはアプリで最初にセットアップする必要があるなどの理由で)、ID 切り替えを拒否する必要があります。
#### <a name="build-plugin--tool-considerations"></a>ビルド プラグイン / ビルド ツールの考慮事項
(ビルド ツールでその変更を行うようにできるため) 明示的に `MAMActivity`、`MAMService`、または `MAMContentProvider` から継承しませんが、引き続き ID の切り替えを処理する必要がある場合、代わりに `MAMActivityIdentityRequirementListener` (アクティビティ用) または `MAMIdentityRequirementListener` (サービスと ContentProvider 用) を実装できます。 `MAMActivity.onMAMIdentitySwitchRequired` に対する既定の動作には、静的メソッド `MAMActivity.defaultOnMAMIdentitySwitchRequired(activity, identity,
reason, callback)` を呼び出すことによってアクセスできます。

同様に、`MAMActivity.onSwitchMAMIdentityComplete` をオーバーライドする必要がある場合は、明示的に `MAMActivity` から継承することなく、`MAMActivityIdentitySwitchListener` を実装できます。

### <a name="preserving-identity-in-async-operations"></a>非同期操作での ID の保持
UI スレッドに対する操作は、バック グラウンド タスクを別のスレッドにディスパッチするのが一般的です。 マルチ ID アプリでは、このようなバック グラウンド タスクが適切な ID で動作していることを確認する必要があります。多くの場合は、バック グラウンド タスクをディスパッチしたアクティビティで使用される ID と同じものになります。 MAM SDK では、ID を保持するのに便利な機能として `MAMAsyncTask` と `MAMIdentityExecutors` を提供しています。
#### <a name="mamasynctask"></a>MAMAsyncTask

`MAMAsyncTask` を使用するには、AsyncTask ではなく MAMAsyncTask を継承し、`doInBackground` のオーバーライドを `doInBackgroundMAM` に、`onPreExecute` のオーバーライドを `onPreExecuteMAM` に置換するだけです。 `MAMAsyncTask` コンストラクターは、アクティビティ コンテキストを取ります。 次に例を示します。

```java
  AsyncTask<Object, Object, Object> task = new MAMAsyncTask<Object, Object, Object>(thisActivity) {

    @Override
    protected Object doInBackgroundMAM(final Object[] params) {
        // Do operations.
    }

    @Override
    protected void onPreExecuteMAM() {
        // Do setup.
    };
```

### <a name="mamidentityexecutors"></a>MAMIdentityExecutors
`MAMIdentityExecutors` では、`wrapExecutor` メソッドと `wrapExecutorService` メソッドを使用して、既存の `Executor` インスタンスまたは `ExecutorService` インスタンスを ID 保持 `Executor`/`ExecutorService` としてラップすることができます。 例

```java
  Executor wrappedExecutor = MAMIdentityExecutors.wrapExecutor(originalExecutor, activity);
  ExecutorService wrappedService = MAMIdentityExecutors.wrapExecutorService(originalExecutorService, activity);
```
### <a name="file-protection"></a>ファイル保護

すべてのファイルに、スレッドとプロセス ID に基づいて作成時に関連付けられた ID があります。 この ID は、ファイルの暗号化と選択的ワイプの両方に使用されます。 ID が管理され、暗号化を必要とするポリシーがあるファイルのみが暗号化されます。 SDK の既定の選択機能ワイプでは、ワイプが要求されている管理対象の ID に関連付けられたファイルのみがワイプされます。 アプリでは `MAMFileProtectionManager` クラスを使用して、ファイルの ID の照会または変更を行うことができます。

  ```java
    public final class MAMFileProtectionManager {

        /**
         * Protect a file. This will synchronously trigger whatever protection is required for the 
         * file, and will tag the file for future protection changes.
         *
         * @param identity
         *            Identity to set.
         * @param file
         *            File to protect.
         * @throws IOException
         *             If the file cannot be changed.
         */
        public static void protect(final File file, final String identity) throws IOException;

       /**
         * Protect a file obtained from a content provider. This is intended to be used for
         * sdcard (whether internal or removable) files accessed through the Storage Access Framework.
         * It may also be used with descriptors referring to private files owned by this app.
         * It is not intended to be used for files owned by other apps and such usage will fail. If
         * creating a new file via a content provider exposed by another MAM-integrated app, the new
         * file identity will automatically be set correctly if the ContentResolver in use was
         * obtained via a Context with an identity or if the thread identity is set.
         *
         * This will synchronously trigger whatever protection is required for the file, and will tag
         * the file for future protection changes. If an identity is set on a directory, it is set
         * recursively on all files and subdirectories. If MAM is operating in offline mode, this
         * method will silently do nothing.
         *
         * @param identity
         *            Identity to set.
         * @param file
         *            File to protect.
         *
         * @throws IOException
         *             If the file cannot be protected.
         */
        public static void protect(final ParcelFileDescriptor file, final String identity) throws IOException;

       /**
        * Get the protection info on a file.
        *
        * @param file
        *            File or directory to get information on.
        * @return File protection info, or null if there is no protection info.
        * @throws IOException
        *             If the file cannot be read or opened.
        */
        public static MAMFileProtectionInfo getProtectionInfo(final File file) throws IOException;

       /**
        * Get the protection info on a file.
        *
        * @param file
        *            File or directory to get information on.
        * @return File protection info, or null if there is no protection info.
        * @throws IOException
        *             If the file cannot be read or opened.
        */
        public static MAMFileProtectionInfo getProtectionInfo(final ParcelFileDescriptor file) throws IOException;

    }

    public interface MAMFileProtectionInfo {
        String getIdentity();
    }
  ```
#### <a name="app-responsibility"></a>アプリの責任
MAM では、読み取られているファイルと `Activity` に表示されているデータの関係を自動的に推測することはできません。 アプリは、企業データを表示する前に、UI ID を適切に設定する*必要があります*。 これには、ファイルから読み取られたデータが含まれます。 ファイルがアプリの外部 (`ContentProvider` または公開されている書き込み可能な場所のいずれか) からのものである場合、アプリはファイルから読み取った情報を表示する前に、(`MAMFileProtectionManager.getProtectionInfo` を使用して) ファイル ID の判断を試みる*必要があります*。 `getProtectionInfo` が null 以外 (空ではない ID) をレポートする場合は、UI ID を (`MAMActivity.switchMAMIdentity` または `MAMPolicyManager.setUIPolicyIdentity` を使用して) この ID に一致するように設定する*必要があります*。 ID の切り替えが失敗した場合、ファイルのデータは表示*できません*。

フローの例は、次のようになります。
  * ユーザーが、アプリで開くドキュメントを選択します
  * 開いているフローで、ディスクからデータを読み取る前に、アプリはコンテンツを表示するために使用する ID を確認します
    * MAMFileProtectionInfo info = MAMFileProtectionManager.getProtectionInfo(docPath)
    * if(info)   MAMPolicyManager.setUIPolicyIdentity(activity, info.getIdentity(), callback)
    * アプリは、結果がコールバックにレポートされるまで待機します
    * レポートされた結果が失敗の場合、アプリでドキュメントが表示されません
  * アプリを開き、ファイルが表示されます

#### <a name="offline-scenarios"></a>オフラインのシナリオ

ファイルの ID タグ付けはオフライン モードに依存します。 次の点を考慮する必要があります。

  * ポータル サイトをインストールしていない場合は、ファイルに ID タグを付けることはできません。

  * ポータル サイトをインストールしていても、アプリに Intune MAM ポリシーがない場合は、ファイルに確実に ID タグを付けることはできません。

  * ファイルに ID タグを付けられるようになると、以前に作成されたすべてのファイルは、アプリが単一 ID で管理されるアプリとしてインストールされている (ファイルが登録済みユーザーに属するものとして扱われる) 場合を除き、個人用/管理対象外 (空の文字列 ID に属する) として扱われます。

### <a name="directory-protection"></a>ディレクトリの保護

ファイルを保護するのと同じ `protect` メソッドを使用して、ディレクトリを保護することができます。 ディレクトリの保護は、そのディレクトリ含まれているすべてのファイルとサブディレクトリおよびディレクトリ内で作成された新しいファイルに再帰的に適用されます。 ディレクトリ保護は再帰的に適用されるので、大きなディレクトリの場合、`protect` の呼び出しの完了に時間がかかることがあります。 そのため、多数のファイルが含まれるディレクトリに保護を適用するアプリでは、バックグラウンドのスレッドで `protect` を非同期的に実行することもできます。

### <a name="data-protection"></a>データ保護

複数 ID に属しているものとしてファイルにタグを付けることはできません。 同じファイル内の別のユーザーに属しているデータを格納する必要があるアプリでは、`MAMDataProtectionManager` で提供される機能を使用して手動でこれを行うことができます。 これにより、アプリではデータを暗号化し、特定のユーザーに関連付けることができます。 暗号化されたデータは、ファイルのディスクへの格納に適しています。 ID に関連付けられているデータを照会することができ、後でデータの暗号化を解除することができます。

`MAMDataProtectionManager` を使用するアプリは、`MANAGEMENT_REMOVED` 通知のレシーバーを実装する必要があります。 このクラスを使用してバッファーが保護されていたときにファイルの暗号化が有効になっていた場合、この通知が完了した後に、保護されていたバッファーは読み取りできなくなります。 アプリは、この通知中にすべてのバッファーで MAMDataProtectionManager.unprotect を呼び出すことによってこのような状況を修復することができます。 ID 情報を保持する必要がある場合、この通知中に保護を呼び出しても安全です。暗号化は通知中に無効になることが保証されます。

```java

public final class MAMDataProtectionManager {
    /**
     * Protect a stream. This will return a stream containing the protected
     * input.
     *
     * @param identity
     *            Identity to set.
     * @param input
     *            Input data to protect, read sequentially. This function
     *            will change the position of the stream but may not have
     *            read the entire stream by the time it returns. The
     *            returned stream will wrap this one. Calls to read on the
     *            returned stream may cause further reads on the original
     *            input stream. Callers should not expect to read directly
     *            from the input stream after passing it to this method.
     *            Calling close on the returned stream will close this one.
     * @return Protected input data.
     * @throws IOException
     *             If the data could not be protected
     */
    public static InputStream protect(final InputStream input, final String identity);

    /**
     * Protect a byte array. This will return protected bytes.
     *
     * @param identity
     *            Identity to set.
     * @param input
     *            Input data to protect.
     * @return Protected input data.
     * @throws IOException
     *             If the data could not be protected
     */
    public static byte[] protect(final byte[] input, final String identity) throws IOException;

    /**
     * Unprotect a stream. This will return a stream containing the
     * unprotected input.
     *
     * @param input
     *            Input data to protect, read sequentially.
     * @return Protected input data.
     * @throws IOException
     *             If the data could not be unprotected
     */
    public static InputStream unprotect(final InputStream input) throws IOException;

    /**
     * Unprotect a byte array. This will return unprotected bytes.
     *
     * @param input
     *            Input data to protect.
     * @return Protected input data.
     * @throws IOException
     *             If the data could not be unprotected
     */
    public static byte[] unprotect(final byte[] input) throws IOException;

    /**
     * Get the protection info on a stream.
     *
     * @param input
     *            Input stream to get information on. Either this input
     *            stream must have been returned by a previous call to
     *            protect OR input.markSupported() must return true.
     *            Otherwise it will be impossible to get protection info
     *            without advancing the stream position. The stream must be
     *            positioned at the beginning of the protected data.
     * @return Data protection info, or null if there is no protection
     *            info.
     * @throws IOException
     *             If the input cannot be read.
     */
    public static MAMDataProtectionInfo getProtectionInfo(final InputStream input) throws IOException;

    /**
     * Get the protection info on a stream.
     *
     * @param input
     *            Input bytes to get information on. These must be bytes
     *            returned by a previous call to protect() or a copy of
     *            such bytes.
     * @return Data protection info, or null if there is no protection
     *            info.
     * @throws IOException
     *             If the input cannot be read.
     */
    public static MAMDataProtectionInfo getProtectionInfo(final byte[] input) throws IOException;
}
```

### <a name="content-providers"></a>コンテンツ プロバイダー

アプリが **ContentProvider** を通じて **ParcelFileDescriptor** 以外の会社データを提供する場合、アプリは `MAMContentProvider` でメソッド `isProvideContentAllowed(String)` を呼び出し、コンテンツの所有者 ID の UPN (ユーザー プリンシパル名) を渡す必要があります。 この関数で false が返されると、コンテンツを呼び出し元に返すことは "*できません*"。 コンテンツ プロバイダーから返されたファイル記述子は、ファイル ID に基づいて自動的に処理されます。

### <a name="selective-wipe"></a>選択的なワイプ

複数 ID アプリを `WIPE_USER_DATA` 通知に登録する場合、ワイプするユーザーのすべてのデータをそのアプリで削除する必要があります。データには、そのユーザーに属しているものとして ID タグが付けられたすべてのファイルが含まれます。 アプリでファイルからユーザー データを削除するが、そのファイルの他のデータはそのままにしておきたい場合は、(空の ID または個人ユーザーに対する `MAMFileProtectionManager.protect` を使用して) ファイルの ID を変更する*必要* があります。 暗号化ポリシーを使用している場合、ワイプするユーザーに属している残りのファイルの暗号化は解除されず、ワイプ後にアプリにアクセスできなくなります。

`WIPE_USER_DATA` に登録しているアプリは、SDK の既定の選択的ワイプ動作の利点が得られなくなります。 複数 ID 対応アプリの場合、MAM の既定の選択的ワイプではワイプ対象の ID のファイルのみがワイプされるため、この損失がとても重要になることがあります。 複数 ID 対応アプリケーションで MAM の既定の選択的ワイプを実行し、_**さらに**_ 独自のアクションを実行する場合、`WIPE_USER_AUXILIARY_DATA` 通知に登録する必要があります。 この通知は、MAM の既定の選択的ワイプを実行する直前に SDK によって送信されます。 アプリは、WIPE_USER_DATA と WIPE_USER_AUXILIARY_DATA の両方に登録しないようにする必要があります。


## <a name="enabling-mam-targeted-configuration-for-your-android-applications-optional"></a>Android アプリケーションの MAM 対象の構成を有効にする (省略可能)
アプリケーション固有のキーと値のペアは、Intune コンソールで構成することはできません。 これらのキーと値のペアが、Intune で解釈されることはありませんが、単にアプリに渡されます。 このような構成を受信する必要があるアプリケーションは、この操作を行うために `MAMAppConfigManager` と `MAMAppConfig` クラスを使用できます。 複数のポリシーが同じアプリで対象となっている場合は、同じキーに使用できる複数の値が競合している可能性があります。

### <a name="example"></a>例
```
MAMAppConfigManager configManager = MAMComponents.get(MAMAppConfigManager.class);
String identity = "user@contoso.com"
MAMAppConfig appConfig = configManager.getAppConfig(identity);
LOGGER.info("App Config Data = " + (appConfig == null ? "null" : appConfig.getFullData()));
String valueToUse = null;
if (appConfig.hasConflict("foo")) {
    List<String> values = appConfig.getAllStringsForKey("foo");
    for (String value : values) {
        if (isCorrectValue(value)) {
            valueToUse = value;
        }
    }
} else {
    valueToUse = appConfig.getStringForKey("foo", MAMAppConfig.StringQueryType.Any);
}
LOGGER.info("Found value " + valueToUse);
```

### <a name="mamappconfig-reference"></a>MAMAppConfig 参照

```
public interface MAMAppConfig {
    /**
     * Conflict resolution types for Boolean values.
     */
    enum BooleanQueryType {
        /**
         * In case of conflict, arbitrarily picks one. This is not guaranteed to return the same value every time.
         */
        Any,
        /**
         * In case of conflict, returns true if any of the values are true.
         */
        Or,
        /**
         * In case of conflict, returns false if any of the values are false.
         */
        And
    }

    /**
     * Conflict resolution types for integer and double values.
     */
    enum NumberQueryType {
        /**
         * In case of conflict, arbitrarily picks one. This is not guaranteed to return the same value every time.
         */
        Any,
        /**
         * In case of conflict, returns the minimum Integer.
         */
        Min,
        /**
         * In case of conflict, returns the maximum Integer.
         */
        Max
    }

    /**
     * Conflict resolution types for Strings.
     */
    enum StringQueryType {
        /**
         * In case of conflict, arbitrarily picks one. This is not guaranteed to return the same value every time.
         */
        Any,
        /**
         * In case of conflict, returns the first result ordered alphabetically.
         */
        Min,
        /**
         * In case of conflict, returns the last result ordered alphabetically.
         */
        Max
    }

    /**
     * Retrieve the List of Dictionaries containing all the custom
     *  config data sent by the MAMService. This will return every
     * Application Configuration setting available for this user, one
     *  mapping for each policy applied to the user.
     */
    List<Map<String, String>> getFullData();

    /**
     * Returns true if there is more than one targeted custom config setting for the key provided. 
     */
    boolean hasConflict(String key);

    /**
     * @return a Boolean value for the given key if it can be coerced into a Boolean, or 
     * null if none exists or it cannot be coerced.
     */
    Boolean getBooleanForKey(String key, BooleanQueryType queryType);

    /**
     * @return a Long value for the given key if it can be coerced into a Long, or null if none exists or it cannot be coerced.
     */
    Long getIntegerForKey(String key, NumberQueryType queryType);

    /**
     * @return a Double value for the given key if it can be coerced into a Double, or null if none exists or it cannot be coerced.
     */
    Double getDoubleForKey(String key, NumberQueryType queryType);

    /**
     * @return a String value for the given key, or null if none exists.
     */
    String getStringForKey(String key, StringQueryType queryType);

    /**
     * Like getBooleanForKey except returns all values if multiple are present.
     */
    List<Boolean> getAllBooleansForKey(String key);

    /**
     * Like getIntegerForKey except returns all values if multiple are present.
     */
    List<Long> getAllIntegersForKey(String key);

    /**
     * Like getDoubleForKey except returns all values if multiple are present.
     */
    List<Double> getAllDoublesForKey(String key);

    /**
     * Like getStringForKey except returns all values if multiple are present.
     */
    List<String> getAllStringsForKey(String key);
}
```

### <a name="notification"></a>通知
アプリの構成で新しい通知の種類を追加します。
* **REFRESH_APP_CONFIG**: この通知は、`MAMUserNotification` で送信され、アプリに新しいアプリの構成データを使用できることを通知します。

Graph API の機能に関する詳細については、[Graph API のリファレンス](https://developer.microsoft.com/graph/docs/concepts/overview) ページを参照してください。 <br>

Android で MAM 対象アプリ構成ポリシーを作成する方法については、「[Android for Work の Microsoft Intune アプリ構成ポリシーを使用する方法](https://docs.microsoft.com/intune/app-configuration-policies-use-android)」の MAM 対象アプリ構成セクションを参照してください。

## <a name="style-customization-optional"></a>スタイルのカスタマイズ (省略可能)

MAM SDK によって生成されるビューは、統合されたアプリとより厳密に一致するように視覚的にカスタマイズできます。 アプリのロゴのサイズに加え、プライマリ、セカンダリ、および背景の色をカスタマイズすることができます。 このスタイルのカスタマイズは省略可能であり、カスタム スタイルが構成されていない場合、既定値が使用されます。


### <a name="how-to-customize"></a>カスタマイズする方法
スタイルの変更を Intune MAM のビューに適用するには、まず、スタイルのオーバーライドの XML ファイルを作成する必要があります。 このファイルは、アプリの "res/xml" ディレクトリに配置する必要があり、自由に名前を付けることができます。 このファイルが従う必要がある形式の例を以下に示します。
```xml
<?xml version="1.0" encoding="utf-8"?>
<styleOverrides>
    <item
        name="foreground_color"
        resource="@color/red"/>
    <item
        name="accent_color"
        resource="@color/blue"/>
    <item
        name="background_color"
        resource="@color/green"/>
    <item
        name="logo_image"
        resource="@drawable/app_logo"/>
</styleOverrides>
```

アプリ内に既に存在するリソースを再利用する必要があります。 たとえば、colors.xml ファイルで緑の色を定義し、ここで参照する必要があります。 16 進カラー コード "#0000ff" を使用することはできません。 アプリのロゴの最大サイズは、110 dip (dp) です。 小さなロゴの画像を使用することができますが、最大サイズに準拠すると、最適な結果が得られます。 110 dip の制限を超えると、画像は縮小され、ぼやけた画像になる可能性があります。

以下に、許可されているスタイル属性、それらで制御する UI 要素、XML 属性の項目名、およびそれぞれに必要なリソースの種類の完全な一覧を示します。

|スタイル属性 | 影響を受ける UI 要素 | 属性項目名 | 必要なリソースの種類 |
| -- | -- | -- | -- |
| 背景の色 | PIN 画面の背景色 <Br>PIN ボックスの塗りつぶしの色 | background_color | 色 |
| 背景色 | 背景のテキストの色 <br> PIN ボックスの枠線の既定の状態 <br> ユーザーが PIN を入力するときの PIN ボックスの文字 (暗号化された文字を含む)| foreground_color | 色|
| アクセント カラー | 強調表示したときの PIN ボックスの枠線 <br> ハイパーリンク |accent_color | 色 |
| アプリのロゴ | Intune アプリの PIN 画面に表示される大きなアイコン | logo_image | Drawable |

## <a name="default-enrollment-optional"></a>既定の登録 (オプション)
<!-- Requiring user login prompt for an automatic APP-WE service enrollment, requiring Intune app protection policies in order to use your SDK-integrated Android LOB app, and enabling ADAL SSO (optional) -->

ここでは、自動 APP-WE サービス登録の場合にアプリの起動時にユーザー プロンプトを必須にする (このセクションでは、**既定の登録**と呼びます) 場合と、Intune で保護されたユーザーにのみ SDK に統合された Android LOB アプリの使用を許可する Intune アプリ保護ポリシーを必須にする場合のガイダンスを示します。 また、SDK に統合された Android LOB アプリで SSO を有効にする方法についても説明します。 Intune 以外のユーザーが使用できるストア アプリでは、この方法は**サポートされません**。

> [!NOTE] 
> **既定の登録**の利点には、デバイス上のアプリの APP-WE サービスからポリシーを取得する方法が簡単なことなどがあります。

### <a name="general-requirements"></a>一般的な要件
* 「[ADAL の一般的な構成](https://docs.microsoft.com/intune/app-sdk-android#common-adal-configurations)」の 2. の手順に従って、自分のアプリが Intune モバイル アプリケーション管理サービスで登録されていることを確認します。

### <a name="working-with-the-intune-sdk"></a>Intune SDK の使用
これらの手順は、エンド ユーザー デバイスで使用するアプリのために Intune アプリ保護ポリシーが必要なすべての Android および Xamarin アプリの開発者向けです。

1. [Android 用 Intune SDK ガイド](https://docs.microsoft.com/intune/app-sdk-android#configure-azure-active-directory-authentication-library-adal)のセクションで定義されている手順を使用して ADAL を構成します。
   > [!NOTE] 
   > アプリに関連付けられている "クライアント ID" という用語は、Azure Portal の用語 "アプリケーション ID" と同じです。 
2. SSO を有効にするには、「ADAL の一般的な構成」の 2. が必要です。

3. マニフェストに次の値を入力して、既定の登録を有効にします。```xml <meta-data android:name="com.microsoft.intune.mam.DefaultMAMServiceEnrollment" android:value="true" />```
   > [!NOTE] 
   > これは、アプリ内での唯一の MAM-WE 統合である必要があります。 MAMEnrollmentManager API を呼び出す他の試行がある場合、競合が発生する可能性があります。

4. マニフェストに次の値を入力して、必要な MAM ポリシーを有効にします。```xml <meta-data android:name="com.microsoft.intune.mam.MAMPolicyRequired" android:value="true" />```
   > [!NOTE] 
   > その結果、ユーザーの使用前に、デバイスにポータル サイトをダウンロードし、既定の登録フローを完了することを強制します。

> [!NOTE]
    > これは、アプリ内での唯一の MAM-WE 統合である必要があります。 MAMEnrollmentManager API を呼び出す他の試行がある場合、競合が発生します。

3. マニフェストに次の値を入力して、必要な MAM ポリシーを有効にします。
```xml
<meta-data android:name="com.microsoft.intune.mam.MAMPolicyRequired" android:value="true" />
```

> [!NOTE] 
> その結果、ユーザーの使用前に、デバイスにポータル サイトをダウンロードし、既定の登録フローを完了することを強制します。

## <a name="limitations"></a>制限事項

### <a name="file-size-limitations"></a>ファイル サイズの制限

[ProGuard](http://proguard.sourceforge.net/) なしに実行される大規模なコード ベースにおいて Dalvik 実行可能ファイル形式の制限が問題になります。 具体的には、次の制限事項が発生する可能性があります。

1.  フィールドの 65 K の制限。
2.  メソッドの 65 K の制限。

### <a name="policy-enforcement-limitations"></a>ポリシーの適用の制限事項

* **画面キャプチャ**: SDK は Activity.onCreate が既に終了したアクティビティに対し、新しい画面キャプチャの設定値を適用することができません。 これにより、アプリがスクリーン ショットを無効にするよう構成されているものの、スクリーン ショットを引き続き実行できる期間が発生します。

* **コンテンツ リゾルバーの使用**: "転送ポリシーまたは受信" Intune ポリシーにより、別のアプリのコンテンツ プロバイダーにアクセスするためのコンテンツ リゾルバーの使用がブロックされるか、部分的にブロックされる場合があります。 これにより、ContentResolver メソッドによって null が返されるか、失敗値がスローされます (例: ブロックされている場合、`openOutputStream` によって `FileNotFoundException` がスローされる)。 アプリでは、次の呼び出しを行って、コンテンツ リゾルバーを介したデータの書き込みのエラーが、ポリシーによって発生した (またはポリシーによって発生する) かどうかを確認できます。
    ```java
    MAMPolicyManager.getPolicy(currentActivity).getIsSaveToLocationAllowed(contentURI);
    ```
    または、関連するアクティビティがない場合

    ```java
    MAMPolicyManager.getPolicy().getIsSaveToLocationAllowed(contentURI);
    ```

    この 2 番目のケースでは、複数の ID のアプリは、スレッド ID を適切に設定する (または、明示的に ID を `getPolicy` 呼び出しに渡す) 必要があります。

### <a name="exported-services"></a>エクスポートされたサービス

 Intune アプリ SDK に含まれる AndroidManifest.xml ファイルには **MAMNotificationReceiverService** が含まれます。これは、ポータル サイト アプリから管理対象アプリに通知を送信できるようにする、エクスポートされたサービスである必要があります。 このサービスでは、ポータル サイト アプリのみが通知の送信を許可されるように、呼び出し元を確認します。

### <a name="reflection-limitations"></a>リフレクションの制限事項
MAM の基底クラス (MAMActivity、MAMDocumentsProvider など) の一部には、特定の API レベルより上にあるパラメーターまたは戻り値の型のみを使用するメソッド (Android の元の基底クラスに基づく) が含まれています。 このため、リフレクションを使用して、常にアプリ コンポーネントのすべてのメソッドを列挙できるとは限りません。 この制限は MAM に限定されるものではなく、アプリ自体が、Android 基底クラスからのこのようなメソッドを実装する場合にも同じ制限が適用されます。

### <a name="robolectric"></a>Robolectric
Robolectric での MAM SDK 動作のテストはサポートされていません。 実際のデバイスやエミュレーターでは正確に模倣されない Roboelectric に存在する動作による、Roboelectric での MAM SDK の実行に関する既知の問題があります。

Roboelectric でアプリケーションをテストする必要がある場合に推奨される回避策は、アプリケーション クラスのロジックをヘルパーに移動し、MAMApplication から継承しないアプリケーション クラスで単体テスト apk を生成することです。
## <a name="expectations-of-the-sdk-consumer"></a>SDK コンシューマーの要望

Intune SDK は Android API によって提供されるコントラクトを維持します。ただし、ポリシーの適用の結果として、エラー状態がより頻繁にトリガーされる可能性があります。 これらの Android のベスト プラクティスにより、エラーの可能性が減少します。

* null を返す可能性のある android SDK 関数で、null が返される可能性が高くなりました。  問題を最小限に抑えるため、null チェックが適切な場所にあることを確認します。

* チェックできる機能は、MAM 置換 API を介してチェックする必要があります。

* すべての派生関数はそのスーパークラスのバージョンを介して呼び出しを行う必要があります。

* あいまいな方法で API を使用することを回避します。 たとえば、requestCode を確認しないで `Activity.startActivityForResult` を使用すると、予想外の動作が発生します。

## <a name="telemetry"></a>製品利用統計情報

Intune App SDK for Android は、アプリからのデータ収集を制御しません。 ポータル サイト アプリケーションでは、既定で、製品利用統計情報がログに記録されます。 このデータは、Microsoft Intune に送信されます。 Microsoft ポリシーに基づき、個人を特定できる情報 (PII) は収集しません。

> [!NOTE]
> エンド ユーザーがこのデータの送信を選択しない場合、ポータル サイト アプリの [設定] で製品利用統計情報をオフにする必要があります。 詳しくは、「[Microsoft による使用状況データの収集を無効にする](https://docs.microsoft.com/intune-user-help/turn-off-microsoft-usage-data-collection-android)」をご覧ください。 

## <a name="recommended-android-best-practices"></a>推奨される Android のベスト プラクティス

* ライブラリのすべてのプロジェクトで、可能な限り同じ android:package を共有するようにしてください。 これにより、実行時に散発的に失敗することはありません。これは純粋にビルド時の問題です。 Intune アプリ SDK の新しいバージョンでは、冗長性のいくつか削除されます。

* 最新の Android SDK ビルド ツールを使用します。

* 使用しない不要なすべてのライブラリ (例: android.support.v4) を削除します。
