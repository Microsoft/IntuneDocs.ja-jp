---
title: "Android 用 Microsoft Intune アプリ SDK 開発者ガイド | Microsoft Intune"
description: 
keywords: 
author: Msmbaldwin
manager: jeffgilb
ms.date: 09/08/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0100e1b5-5edd-4541-95f1-aec301fb96af
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 952cfa4f23f8ba080ce53f6785baceb8a0a367c6
ms.openlocfilehash: 829ba47807b3b773c810be290b636d9f18e9c2bd


---

# Android 用 Microsoft Intune アプリ SDK 開発者ガイド

> [!NOTE]
> まず [Intune アプリ SDK の概要](intune-app-sdk.md)に目を通すことをお勧めします。このガイドでは、SDK の最新機能と、サポートする各プラットフォームで統合のための準備をする方法について説明しています。 

## SDK 

Android 用 Intune アプリ SDK は、外部依存関係のない標準の Android ライブラリです。 SDK は次のもので構成されます。  

* **`Microsoft.Intune MAM.SDK.jar`**: Microsoft Intune ポータル サイト アプリとの相互運用性を有効にするだけでなく、アプリで MAM を有効にするために必要なインターフェイスです。 アプリでこれを Android ライブラリ参照として指定する必要があります。

* **`Microsoft.Intune.MAM.SDK.Support.v4.jar`**: Android v4 サポート ライブラリを利用するアプリで MAM を有効にするために必要なインターフェイスです。  このサポートを必要とするアプリは、jar ファイルを直接参照する必要があります。 

* **`Microsoft.Intune.MAM.SDK.Support.v7.jar`**: Android v7 サポート ライブラリを利用するアプリで MAM を有効にするために必要なインターフェイスです。   このサポートを必要とするアプリは、jar ファイルを直接参照する必要があります。

* **リソース ディレクトリ**: SDK が依存するリソース (文字列など)。 

* **`Microsoft.Intune.MAM.SDK.aar`**: Support.V4 と Support.V7 jar ファイルを除く SDK コンポーネントです。 このファイルは、ビルド システムが AAR ファイルをサポートしている場合、個々のコンポーネントの代わりに使用できます。

* **`AndroidManifest.xml`**: その他のエントリ ポイントとライブラリの要件です。 

* **`THIRDPARTYNOTICES.TXT`**: アプリにコンパイルされるサード パーティや OSS のコードを確認する属性通知です。 

## 要件 

Intune アプリ SDK は、コンパイル済みの Android プロジェクトです。 その結果、最小またはターゲットの API バージョンに関して、アプリが使用する Android のバージョンにはほとんど依存しません。 この SDK は Android API 14 (Android 4.0+) から Android 24 までをサポートしています。 

## Intune アプリ SDK のしくみ 

Intune アプリ SDK では、アプリ管理ポリシーを有効にするために、アプリのソース コードを変更する必要があります。 このことは、Android の基底クラスを同等の管理されたクラス (ドキュメント内でプレフィックス `MAM` を付けて記載されている) に置き換えることで行われます。 SDK クラスは、Android の基底クラスと、アプリ独自のそのクラスの派生バージョンの間に位置します。  例としてアクティビティを使用すると、最終的な継承階層は、`Activity ->MAMActivity->AppSpecificActivity` のようになります。

`AppSpecificActivity` がその親、たとえば `super.onCreate())` と対話する必要がある場合、`MAMActivity` は、継承階層にあり、いくつかのメソッドを置き換えるにもかかわらず、スーパー クラスとなります。 Android アプリはモードが 1 つで、コンテキスト オブジェクトを使用してシステム全体にアクセスできます。  一方、Intune アプリ SDK が組み込まれたアプリはデュアル モードで、アプリはコンテキスト オブジェクトを使用してシステムにアクセスしますが、使用する基本アクティビティに応じて、コンテキスト オブジェクトは、Android によって提供されるか、または、システムの制限付きビューと Android から提供されるコンテキストの間でインテリジェントに多重化されます。

Android 用の Intune アプリ SDK は、MAM ポリシーを有効にするには、デバイスにポータル サイト アプリが存在する必要があります。 ポータル サイト アプリが存在しないと、MAM が有効になっているアプリの動作は変更されず、他のモバイル アプリのように機能します。 ポータル サイトがインストールされ、かつユーザーのポリシーがある場合は、SDK のエントリ ポイントが非同期的に初期化されます。 初期化は、Android によって最初にプロセスが作成される場合にのみ必要です。 初期化中に、ポータル サイト アプリとの接続が確立され、アプリの制限ポリシーがダウンロードされます。  

## Intune アプリ SDK を統合する方法
 
先に触れたとおり、この SDK では、アプリ管理ポリシーを有効にするために、アプリのソース コードを変更する必要があります。 アプリで MAM を有効にするために必要な手順を次に示します。 

### クラス、メソッド、およびアクティビティを、同等の MAM に置き換えます (必須)。 

* Android の基底クラスを、同等の MAM に置き換える必要があります。 これを行うには、次の表に記載されているクラスのすべてのインスタンスを見つけて同等の Intune アプリ SDK に置き換えます。  

    | Android クラス | Intune アプリ SDK の代替物 |
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
    | とroid.app.NativeActivity | MAMNativeActivity |
    | とroid.app.PendingIntent | MAMPendingIntent |
    | とroid.app.Service | MAMService |
    | とroid.app.TabActivity | MAMTabActivity |
    | とroid.app.TaskStackBuilder | MAMTaskStackBuilder |
    | とroid.app.backup.BackupAgent | MAMBackupAgent |
    | とroid.app.backup.BackupAgentHelper | MAMBackupAgentHelper |
    | とroid.app.backup.FileBackupHelper | MAMFileBackupHelper |
    | とroid.app.backup.SharePreferencesBackupHelper | MAMSharedPreferencesBackupHelper |
    | とroid.content.BroadcastReceiver | MAMBroadcastReceiver |
    | とroid.content.ContentProvider | MAMContentProvider |
    | とroid.os.Binder | MAMBinder* |
    | とroid.provider.DocumentsProvider | MAMDocumentsProvider |
    | とroid.preference.PreferenceActivity | MAMPreferenceActivity |

    *Binder が AIDL インターフェイスから生成されていない場合にのみ、Binder を MAMBinder に置き換える必要があります。

    **Microsoft.Intune.MAM.SDK.Suppまたはt.v4.jar**:

    | Android クラス Intune MAM | SDK の代替物 |
    |--|--|
    | とroid.suppまたはt.v4.app.DialogFragment | MAMDialogFragment
    | とroid.suppまたはt.v4.app.FragmentActivity | MAMFragmentActivity
    | とroid.suppまたはt.v4.app.Fragment | MAMFragment
    | とroid.suppまたはt.v4.app.TaskStackBuilder | MAMTaskStackBuilder
    | とroid.suppまたはt.v4.content.FileProvider | MAMFileProvider
    
    **Microsoft.Intune.MAM.SDK.Suppまたはt.v7.jar**:

    |Android クラス | Intune MAM SDK の代替物 |
    |--|--|
    |とroid.suppまたはt.v7.app.ActionBarActivity | MAMActionBarActivity |


* 等価な MAM でオーバーライドされている Android のエントリ ポイントを使用する場合、エントリ ポイントのライフ サイクルの別のバージョンを使用する必要があります ( `MAMApplication`クラスを除く)。

    たとえば、`MAMActivity` から派生する場合は、`onCreate` をオーバーライドして `super.onCreate` を呼び出すのではなく、アクティビティで `onMAMCreate` をオーバーライドし、`uper.onMAMCreate` を呼び出す必要があります。 これにより、アクティビティの起動が (特に) 特定の場合に制限されるようにできます。 

### アプリによる処理を必要とする機能の有効化 

ポリシーの中には、SDK 自体に実装できないものがいくつかあります。 これらの機能の動作をアプリで制御できるようにするために、いくつかの API を公開しています。それらは下に含まれている `AppPolicy` インターフェイスで見つかります。  

    /**
     * External facing app policies.
     */
    public interface AppPolicy {
        /**
         * Restrict where an app can save personal data.
         * 
         * @return True if the app is allowed to save to personal data stores;
         *         false otherwise.
         */
        boolean getIsSaveToPersonalAllowed();
    
        /**
         * Check if policy prohibits saving to a content provider location.
         * 
         * @param location
         *            a content URI to check
         * @return True if location is not a content URI or if policy does not 
         *         prohibit saving to the content location.
         */
        boolean getIsSaveToLocationAllowed(android.net.Uri location); 
    
        /**
         * Whether the SDK PIN prompt is enlightened for the app.
         * 
         * @return True if the PIN is enabled. False otherwise.
         */
        boolean getIsPinRequired();
        /**
         * Whether the Intune Managed Browser is required to open web links.
         *
         * @return True if the Managed Browser is required, false otherwise
         */
        boolean getIsManagedBrowserRequired();
    }

### IT 管理者がアプリの保存動作を制御できるようにする

多くのアプリでは、エンドユーザーがローカルまたは別のサービスにファイルを保存する機能を実装しています。 Intune アプリ SDK を使用することで、データの漏えいを防ぐために、IT 管理者が組織に合ったポリシー制限を適用できます。  管理者が制御できるポリシーとして、エンドユーザーが個人のデータ ストアに保存できるかどうかというものがあります。 これには、ローカルの場所、SD カード、またはバックアップ サービスへの保存が含まれます。 この機能を有効にするには、アプリによる処理が必要です。 アプリから直接個人またはクラウドの場所に保存することをアプリで許可する場合は、IT 管理者がある場所への保存を許可するかどうか制御できるように、この機能を実装する必要があります。 次の API では、現在の管理ポリシーに従い、個人用ストアへの保存が許可されるかどうかを、アプリに知らせています。 これにより、エンドユーザーがアプリを介して個人のデータ ストアを使用できることをアプリで認識できるため、アプリでポリシーを適用できます。  

ポリシーが適用されるかどうかを判断するために、アプリでは次の呼び出しを行うことができます。 

    MAMComponents.get(AppPolicy.class).getIsSaveToPersonalAllowed();

**注**: MAMComponents.get(AppPolicy.class) は、デバイスまたはアプリが管理下にない場合も、常に、null 以外のアプリ ポリシーを返します。 

### PIN ポリシーが必要かどうかをアプリで検出できるようにする
 
 Intune アプリ SDK での機能と重複しないように、追加のポリシーの機能の一部を無効にすることが必要になる場合があります。 たとえば、SDK が、エンドユーザーが PIN を入力することを要求するように構成されている場合、アプリ独自の PIN ユーザー エクスペリエンスを無効にする必要がある場合があります。 

定期的に PIN の入力を要求するように PIN ポリシーが構成されているかどうかを判断するために、アプリで、次の呼び出しを行うことができます。 

    MAMComponents.get(AppPolicy.class).getIsPinRequired();

### SDK からの通知への登録  

Intune アプリ SDK を使用すると、IT 管理者がリモート ワイプ ポリシーなどの特定のポリシーを使用したときに、アプリによって動作が制御されるようにできます。 これを行うには、`MAMNotificationReceiver` クラスを作成して `MAMNotificationReceiverRegistry` に登録することで、SDK からの通知に登録することが必要となります。 これは、次の例に示すように、受信側と、受信側で  `App.onCreate`に受信する必要がある通知のタイプを指定することで行います。
 
    @Override
      public void onCreate() {
            super.onCreate();
    MAMComponents.get(MAMNotificationReceiverRegistry.class).registerReceiver(
    new ToastNotificationReceiver(), MAMNotificationType.WIPE_USER_DATA);
    }

`MAMNotificationReceiver` は、単に通知を受信します。 通知の中には、SDK によって直接処理されるものと、アプリによる処理が必要なものがあります。 アプリでは、通知から true または false を返す必要があります。 通知の結果として実行しようとした何らかのアクションが失敗した場合を除き、常に true を返す必要があります。 ユーザー データをワイプできなかったことがアプリによって示された場合などには、このエラーは Intune サービスに報告されます。 `MAMNotificationReceiver.onReceive` でブロックすることが安全です。これは、このコールバックは UI スレッドで実行されないためです。 

以下では、SDK の定義に従い、MAMNotificationReceiver インターフェイスが含まれています。 

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

アプリに次の通知が送信されます。その一部によって、アプリによる処理が要求される場合があります。 

* **`WIPE_USER_DATA` 通知**: この通知は、`MAMUserNotification` クラスで送信されます。 この通知を受信すると、アプリでは `MAMUserNotification` で渡された ID に関連するすべてのデータを削除する必要があります。 この通知は、現在、Intune サービスの登録解除中に送信されます。 ユーザーのプライマリ名は、通常、登録プロセス中に指定されます。 この通知に登録する場合、アプリがすべてのユーザー データが削除されたことを確認する必要があります。 登録しない場合、既定の選択的ワイプの動作が実行されます。 

* **`WIPE_USER_AUXILIARY_DATA` 通知**: Intune アプリ SDK に対して既定ワイプの実行を求め、かつ、ワイプが発生したときにいくつかの補助的なデータを削除する必要があるアプリは、この通知に登録できます。  

* **`REFRESH_POLICY` 通知**: この通知は追加情報なしに MAMNotification で送信されます。 この通知を受信した場合、キャッシュされたすべてのポリシーは有効でなくなったとみなす必要があり、そのため、ポリシーがどのようなものかを確認する必要があります。 これは一般に SDK によって処理されますが、何らかの永続的な方法で、ポリシーを使用する場合は、アプリによって処理する必要があります。 

### 保留中のインテントとメソッド 

MAM エントリ ポイントのいずれかから派生させた後、 `PackageManager`などを使用してアクティビティを開始するために、通常どおり、コンテキストを使用することができます。  `PendingIntents` は、このルールの例外です。 このようなクラスを呼び出すときは、クラス名を変更する必要があります。 たとえば、`PendingIntent.get*` を使用する代わりに、`MAMPendingIntents.get*` を使用する必要があります。 

場合によっては、Android のクラスで使用できるメソッドが、MAM の置換クラスで最終版としてマークされています。 この場合、MAM 置換クラスによって、似た名前のメソッド (通常は "MAM" というサフィックスが付いている) が提供され、これをオーバーライドする必要があります。 たとえば、`ContentProvider.query` をオーバーライドする代わりに、`MAMContentProvider.queryMAM` をオーバーライドします。 同等の MAM でなく、元のメソッドが偶発的にオーバーライドされることを防ぐために、Java コンパイラによって、最終的な制限が強制されます。 

## バックアップ データの保護 

Android Marshmallow (API 23) 以降、Android ではアプリのデータをバックアップする方法が 2 つになりました。 これらのオプションはアプリで使用でき、MAM データ保護が適切に適用されるようにするために、異なる手順が必要となります。 適切なデータ保護の動作に必要な、対応するアクションの概要は、次の表で確認することができます。  また、Android のバックアップの詳細については、「[Android 開発者のデータ バックアップ ガイド](http://developer.android.com/guide/topics/data/backup.html)」も参照してください。 

### 自動完全バックアップ

Android M から、Android M デバイスで実行されているアプリに対して、ターゲット API に関係なく、自動完全バックアップが提供されるようになりました。 `android:allowBackup` 属性が false でない限り、アプリはその完全なフィルター処理されないバックアップを受信します。 これにより、データの漏えいのリスクが発生するため、データ保護が適用されるようにするために、SDK を変更する必要があります。次の表でその概要を説明します。  顧客データを適切に保護するために、次のガイドラインに従うことが重要です。  `android:allowBackup=false` を設定すると、アプリはオペレーティング システムによるバックアップのキューに入ることがなくなり、バックアップが発生しないため、MAM に対するそれ以上の操作はありません。
 
 ## "key/value" バックアップ

このオプションはすべての API で使用でき、`BackupAgent` と `BackupAgentHelper` が使用されます。 

#### BackupAgentHelper の使用

`BackupAgentHelper` の実装は、Android のネイティブな機能と MAM 統合の両方の面で、`BackupAgent` よりも非常に簡単です。 `BackupAgentHelper` を使用すると、開発者は、`FileBackupHelper` または `SharedPreferencesBackupHelper` それぞれに、ファイル全体または共有の設定を登録することができます。また、これらは作成時に `BackupAgentHelper` に追加されます。 

#### BackupAgent の使用

`BackupAgent` を使用すると、バックアップの対象とするデータをより明示的に指定することができます。 ただし、このオプションを使用すると、Android のバックアップのフレームワークを活用することができません。  実装に対する開発者の責任が大きくなるため、MAM からの適切なデータ保護を適用するために必要となる手順が増加します。 開発者が作業のほとんどを担うことで、MAM 統合は少し複雑になります。 

##### アプリにバックアップ エージェントがない場合
  
`Android:allowbBackup =true` の場合、次の開発者オプションがあります。

###### 構成ファイルに従った完全バックアップ: 

マニフェストで `com.microsoft.intune.mam.FullBackupContent` メタデータ タグの下にリソースを指定します。 次に例を示します。
    `<meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:resource="@xml/my_scheme" />`

`<application>` タグに属性 `android:fullBackupContent="@xml/my_scheme"` を追加します。ここで、`my_scheme` はアプリの XML リソースです。 

###### 除外のない完全バックアップ 

マニフェストに次のようなタグを指定します。 `<meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:value="true" />` 
 
`<application>` タグに次の属性を追加します。`android:fullBackupContent="true"`

##### アプリにバックアップ エージェントがある場合

上記の `BackupAgent` と `BackupAgentHelper` のセクションの推奨事項に従います。 

Android M でのバックアップが簡易化される、 `MAMDefaultFullBackupAgent`を使用することを検討してください。 

#### バックアップの前に

バックアップを開始する前に、バックアップを計画しているファイルまたはデータ バッファーのバックアップが実際に許可されていることを確認する必要があります。 このことを判断するために、 `isBackupAllowed` および `MAMFileProtectionManager` と `MAMDataProtectionManager` 関数を提供しています。 ファイルまたはデータ バッファーのバックアップが許可されていない場合、バックアップで BackupAgent を使用しようとしないでください。

バックアップ中のある時点で、手順 1 でバックアップ対象としてチェックしたファイルの ID が必要となった場合、データの抽出元ファイルで `backupMAMFileIdentity(BackupDataOutput data, File … files)` を呼び出す必要があります。 これにより、自動的に新しいバックアップ エンティティが作成され、 `BackupDataOutput` に書き込まれます。 これらのエンティティは、復元時に自動的に使用されます。 

### Azure Directory Authentication Library (ADAL) の構成  

SDK では 認証と条件付き起動シナリオを ADAL に依存するため、アプリにある程度の Azure Active Directory 構成が必要となります。 構成値は、 `AndroidManifest` メタデータを使用して SDK に伝達されます。 アプリを構成して適切な認証を有効にするには、`AndroidManifest` のアプリのノードに次の内容を追加します。 これらの構成の中には、アプリで通常の認証に ADAL が使用される場合にのみ必要となるものがあります。この場合、アプリによって AAD への登録に使用される特定の値が必要になります。 これにより、AAD により 2 つ (アプリと SDK から 1 つずつ) の個別の登録値が認識されることによってエンドユーザーに対して認証が 2 回求められることがなくなります。 

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

GUID の前後に中かっこは必要ありません。

#### ADAL の一般的な構成 

上記で説明した値の一般的な構成を次に示します。 

##### アプリに ADAL が統合されない場合

* AAD アカウントが構成されている、目的の環境に権限を設定する必要があります。

* SkipBroker を true に設定する必要があります。

##### アプリに ADAL が統合される場合

* AAD アカウントが構成されている、目的の環境に権限を設定する必要があります。

* クライアント ID は、アプリのクライアント ID に設定する必要があります。

* `NonBrokerRedirectURI` をアプリの有効なリダイレクト URI に設定する必要があります。
    * Or `urn:ietf:wg:oauth:2.0:oob` を有効な AAD リダイレクト URI として構成する必要があります。

* SkipBroker は false に設定する (または存在しない) 必要があります。

* AAD は、ブローカーのリダイレクト URI を受け入れるように構成する必要があります。

##### アプリに ADAL が統合されるが、AAD 認証アプリがサポートされない場合

* AAD アカウントが構成されている、目的の環境に権限を設定する必要があります。

* クライアント ID は、アプリのクライアント ID に設定する必要があります。

* `NonBrokerRedirectURI` をアプリの有効なリダイレクト URI に設定する必要があります。

    * Or `urn:ietf:wg:oauth:2.0:oob` を有効な AAD リダイレクト URI として構成する必要があります。

### SDK でのログ記録を有効にする方法 

ログ記録は、 `java.util.logging` フレームワークを介して実行されます。 ログを受信するには、[Java テクニカル ガイド](http://docs.oracle.com/javase/6/docs/technotes/guides/logging/overview.html)の説明に従って、グローバル ログを設定します。 アプリによっては、 `App.onCreate` はログ記録を開始する場所として一般的に最適です。 ログ メッセージはクラス名によってキー指定され、難読化されることに注意してください。

## 既知のプラットフォームの制限事項 

### ファイル サイズの制限 

Android では、Dalvik 実行可能ファイル形式の制限が、ProGuard なしに実行される大規模なコード ベースにおいて問題になる場合があります。 具体的には、次の制限事項が発生する可能性があります。 

* フィールドの 65 K の制限。

* メソッドの 65 K の制限。

多くのプロジェクトを含むすべての android:package では、R のコピーを取得し、これによるライブラリの追加に伴ってフィールドの数が大幅に増加します。 次の推奨事項は、この制限の緩和に役立ちます。
 
* ライブラリのすべてのプロジェクトで、可能な限り同じ android:package を共有するようにしてください。 これにより、散発的にフィールドのエラーが発生することはありません。純粋にビルド時の問題であるためです。   さらに、より新しいバージョンの Android SDK では、DEX ファイルを前処理して冗長性の一部を取り除きます。 これにより、さらにフィールドからの距離が削減されます。

* 使用可能な最新の Android SDK ビルド ツールを使用します。

* 不要な使用しないすべてのライブラリを削除します (例: `android.support.v4`)。

### ポリシーの適用の制限事項

**画面キャプチャ**: SDK は Activity.onCreate が既に終了したアクティビティに対し、新しい画面キャプチャの設定値を適用することができません。 これにより、アプリがスクリーン ショットを無効にするよう構成されているものの、スクリーン ショットを引き続き実行できる期間が発生します。

**コンテンツ リゾルバーの使用*: 転送ポリシーまたは受信ポリシーにより、別のアプリのコンテンツ プロバイダーにアクセスするためのコンテンツ リゾルバーの使用がブロックされるか、部分的にブロックされます。 これにより、ContentResolver メソッドによって null が返されるか、失敗値がスローされます (例: ブロックされている場合、 `openOutputStream` によって `FileNotFoundException` がスローされる)。 アプリでは、次の呼び出しを行って、コンテンツ リゾルバーを介したデータの書き込みのエラーが、ポリシーによって発生した (またはポリシーによって発生する) かどうかを確認できます。

    MAMComponents.get(AppPolicy.class).getIsSaveToLocationAllowed(contentURI)

**エクスポートされた サービス**: Intune アプリ SDK に含まれる `AndroidManifest.xml` ファイルには `MAMNotificationReceiverService`が含まれます。これは、ポータル サイト アプリから対応のアプリに通知を送信できるようにする、エクスポートされたサービスである必要があります。 このサービスでは、ポータル サイト アプリのみが通知の送信を許可されるように、呼び出し元を確認します。 

## 推奨される Android のベスト プラクティス 

Intune SDK は Android API によって提供されるコントラクトを維持します。ただし、ポリシーの適用の結果として、エラー状態がより頻繁にトリガーされる可能性があります。 これらの Android のベスト プラクティスにより、エラーの可能性が減少します。 

* null を返す可能性のある android SDK 関数で、null が返される可能性が高くなりました。  問題を最小限に抑えるため、null チェックが適切な場所にあることを確認します。

* チェックできる機能は、その SDK API を介してチェックする必要があります。

* すべての派生関数はそのスーパークラスのバージョンを介して呼び出しを行う必要があります。

* あいまいな方法で API を使用することを回避します。 たとえば、requestCode を確認しないで `Activity.startActivityForResult/onActivityResult` を使用すると、予想外の動作が発生します。



<!--HONumber=Sep16_HO2-->


