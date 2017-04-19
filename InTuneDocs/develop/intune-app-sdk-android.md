---
title: "Android 用 Microsoft Intune アプリ SDK 開発者ガイド | Microsoft Docs"
description: "Android 用 Microsoft Intune アプリ SDK を使用すると、Android アプリに Intune モバイル アプリ管理 (MAM) を組み込むことができます。"
keywords: SDK
author: mtillman
manager: angrobe
ms.author: mtillman
ms.date: 12/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0100e1b5-5edd-4541-95f1-aec301fb96af
ms.reviewer: oydang
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 905be6a926dc5bab8e9b1016ba82751ee47313e5
ms.openlocfilehash: 178fbaeb1d3235a81cb4da49b7a955f6999c49a2
ms.lasthandoff: 02/18/2017


---


# <a name="microsoft-intune-app-sdk-for-android-developer-guide"></a>Android 用 Microsoft Intune アプリ SDK 開発者ガイド

> [!NOTE]
> まず、[Intune アプリ SDK の概要](intune-app-sdk.md)に目を通すことをお勧めします。このガイドでは、SDK の最新機能と、サポートされる各プラットフォームで統合のための準備をする方法について説明しています。

Android 用 Microsoft Intune アプリ SDK を使用すると、Android アプリに Intune モバイル アプリ管理 (MAM) を組み込むことができます。 MAM 対応のアプリケーションが Intune App SDK に統合されています。 それにより、Intune で積極的にアプリを管理するとき、IT 監理者はモバイル アプリにポリシーを展開できます。

## <a name="whats-in-the-sdk"></a>SDK の機能

Android 用 Intune アプリ SDK は、外部依存関係のない標準の Android ライブラリです。 SDK は次のもので構成されます。  

* **Microsoft.Intune.MAM.SDK.jar**: Intune ポータル サイト アプリとの相互運用性および MAM を有効にするために必要なインターフェイスです。 アプリでこれを Android ライブラリ参照として指定する必要があります。

* **Microsoft.Intune.MAM.SDK.Support.v4.jar**: Android v4 サポート ライブラリを使用するアプリで MAM を有効にするために必要なインターフェイスです。 このサポートを必要とするアプリは、JAR ファイルを直接参照する必要があります。

* **Microsoft.Intune.MAM.SDK.Support.v7.jar**: Android v7 サポート ライブラリを使用するアプリで MAM を有効にするために必要なインターフェイスです。 このサポートを必要とするアプリは、JAR ファイルを直接参照する必要があります。

* **リソース ディレクトリ**: SDK が依存するリソース (文字列など)。

* **Microsoft.Intune.MAM.SDK.aar**: Support.V4 と Support.V7 JAR ファイルを除く SDK コンポーネントです。 このファイルは、ビルド システムが AAR ファイルをサポートしている場合、個々のコンポーネントの代わりに使用できます。

* **AndroidManifest.xml**: その他のエントリ ポイントとライブラリの要件です。

* **THIRDPARTYNOTICES.TXT**:  アプリにコンパイルされるサード パーティや OSS のコードを確認する属性通知です。

## <a name="requirements"></a>要件

Intune アプリ SDK は、コンパイル済みの Android プロジェクトです。 その結果、最小またはターゲットの API バージョンに関して、アプリが使用する Android のバージョンにはほとんど影響を受けません。 この SDK は Android API 14 (Android 4.0+) から Android API 24 までをサポートしています。

Android 用の Intune アプリ SDK で MAM ポリシーを有効にするには、デバイスに[ポータル サイト](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) アプリが存在する必要があります。 デバイス登録が不要な MAM の場合は、ユーザーがポータル サイト アプリを使用してデバイスを登録する必要は*ありません*。


## <a name="how-the-intune-app-sdk-works"></a>Intune アプリ SDK のしくみ

###<a name="entry-points"></a>エントリ ポイント

Intune アプリ SDK では、Intune アプリ管理ポリシーを有効にするために、アプリのソース コードを変更する必要があります。 このことは、Android の基底クラスを同等の Intune の基底クラス (名前にプレフィックス `MAM` が付いている) に置き換えることで行われます。 SDK クラスは、Android の基底クラスと、アプリ独自のそのクラスの派生バージョンの間に位置します。 例としてアクティビティを使用すると、最終的な継承階層は、`Activity` > `MAMActivity` > `AppSpecificActivity` のようになります。

たとえば、`AppSpecificActivity` がその親と対話する場合 (たとえば、`super.onCreate()` を呼び出して)、`MAMActivity` がスーパー クラスとなります。

標準的な Android アプリはモードが 1 つで、[コンテキスト](https://developer.android.com/reference/android/content/Context.html) オブジェクトを使用してシステムにアクセスできます。 一方、Intune アプリ SDK が組み込まれたアプリはデュアル モードになります。 これらのアプリは引き続き `Context` オブジェクトを通じてシステムにアクセスします。 使用する基本 `Activity` に応じて、`Context` オブジェクトが Android によって提供されるか、システムの制限付きビューと Android から提供される `Context` の間でインテリジェントに多重化されます。

Android の[エントリ ポイント](https://developer.android.com/guide/components/fundamentals.html)が同等の MAM で上書きされている場合、エントリ ポイントのライフ サイクルの MAM バージョンを使用する必要があります (`MAMApplication` クラスを除く)。

たとえば、`MAMActivity` から派生する場合は、`onCreate` をオーバーライドして `super.onCreate` を呼び出すのではなく、`Activity` で `onMAMCreate` をオーバーライドし、`super.onMAMCreate` を呼び出す必要があります。 これにより、Intune で特定の場合に(特に) `Activity` の起動を制限できます。


###<a name="sdk-permissions"></a>SDK のアクセス許可

Intune アプリ SDK では、統合するアプリに対する次の 3 つの [Android システムのアクセス許可](https://developer.android.com/guide/topics/security/permissions.html)が必要になります。

* `android.permission.GET_ACCOUNTS`  (必要に応じて実行時に要求)

* `android.permission.MANAGE_ACCOUNTS`

* `android.permission.USE_CREDENTIALS`

Azure Active Directory Authentication Library ([ADAL](https://azure.microsoft.com/en-us/documentation/articles/active-directory-authentication-libraries/)) では、仲介型認証を実行する場合にこれらのアクセス許可が必要になります。 これらのアクセス許可がアプリに付与されていない場合や、ユーザーによって取り消された場合、ブローカー (ポータル サイト アプリ) を必要とする認証フローは無効になります。


###<a name="company-portal-app"></a>ポータル サイト アプリ

ポータル サイト アプリが必要な理由 ポータル サイト アプリがデバイスにインストールされており、Intune サービスからユーザーのアプリケーション制限ポリシーが取得されている場合、SDK エントリ ポイントは非同期的に初期化されます。 初期化は、Android によって最初にプロセスが作成される場合にのみ必要です。 初期化中に、ポータル サイト アプリとの接続が確立され、アプリからポリシーが取得されます。  

> [!NOTE]
> デバイスにポータル サイト アプリが存在しないと、Intune が有効になっているアプリの動作は変更されず、通常のアプリのように動作します。


## <a name="how-to-integrate-with-the-intune-app-sdk"></a>Intune アプリ SDK を統合する方法

前述のとおり、この SDK では、アプリ管理ポリシーを有効にするために、アプリのソース コードを変更する必要があります。 アプリで MAM を有効にするために必要な手順を次に示します。

### <a name="replace-classes-methods-and-activities-with-their-mam-equivalent-required"></a>クラス、メソッド、およびアクティビティを、同等の MAM に置き換えます (必須)。

Android の基底クラスを、それぞれ対応する同等の MAM に置き換える必要があります。 これを行うには、次の表にリスト表示されているクラスのすべてのインスタンスを見つけて同等の Intune アプリ SDK に置き換えます。

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
| とroid.app.NativeActivity | MAMNativeActivity |
| とroid.app.PendingIntent | MAMPendingIntent* |
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
| とroid.provider.DocumentsProvider | MAMDocumentsProvider |
| とroid.preference.PreferenceActivity | MAMPreferenceActivity |


**Microsoft.Intune.MAM.SDK.Suppまたはt.v4.jar**:

| Android クラス Intune MAM | Intune アプリ SDK の代替物 |
|--|--|
| とroid.suppまたはt.v4.app.DialogFragment | MAMDialogFragment
| とroid.suppまたはt.v4.app.FragmentActivity | MAMFragmentActivity
| とroid.suppまたはt.v4.app.Fragment | MAMFragment
| とroid.suppまたはt.v4.app.TaskStackBuilder | MAMTaskStackBuilder
| とroid.suppまたはt.v4.content.FileProvider | MAMFileProvider

**Microsoft.Intune.MAM.SDK.Suppまたはt.v7.jar**:

|Android クラス | Intune アプリ SDK の代替物 |
|--|--|
|とroid.suppまたはt.v7.app.ActionBarActivity | MAMActionBarActivity |

>[!NOTE]
>注: Android の[エントリ ポイント](https://developer.android.com/guide/components/fundamentals.html)が同等の MAM で上書きされている場合、エントリ ポイントのライフ サイクルの MAM バージョンを使用する必要があります (`MAMApplication` クラスを除く)。
>
>たとえば、`MAMActivity` から派生する場合は、`onCreate` をオーバーライドして `super.onCreate` を呼び出すのではなく、`Activity` で `onMAMCreate` をオーバーライドし、`super.onMAMCreate` を呼び出す必要があります。 これにより、Intune で特定の場合に(特に) `Activity` の起動を制限できます。

#### <a name="pendingintent-classes-and-renamed-methods"></a>PendingIntent クラスおよび renamed メソッド

MAM のエントリ ポイントのいずれかから派生させた後、通常どおり `Context` を使用できます (たとえば、`Activity` クラスを開始して `PackageManager` を使用する場合など)。  

`PendingIntent` クラスは、このルールの例外です。 このようなクラスを呼び出すときは、クラス名を変更する必要があります。 たとえば、`PendingIntent.get*` の代わりに `MAMPendingIntent.get*` メソッドを使用する必要があります。 その後、通常どおり、結果の `PendingIntent` を使用できます。

場合によっては、Android のクラスで使用できるメソッドが、MAM の置換クラスで最終版としてマークされています。 この場合、MAM 置換クラスによって、似た名前のメソッド (通常は `MAM` というサフィックスが付いている) が提供され、これをオーバーライドする必要があります。 たとえば、`ContentProvider.query` をオーバーライドする代わりに、`MAMContentProvider.queryMAM` をオーバーライドします。 同等の MAM でなく、元のメソッドが偶発的にオーバーライドされることを防ぐために、Java コンパイラによって、最終的な制限が強制されます。

###<a name="enable-features-that-require-app-participation"></a>アプリによる処理を必要とする機能の有効化

一部のポリシーは、SDK 自体に実装できません。 アプリではいくつかの API を使用して、これらの機能を実行するために動作を制御することができます。この API は以下の `AppPolicy` インターフェイスで見つけることができます。

```
/**
 * External facing application policies.
 */
public interface AppPolicy {

/**
 * Restrict where an app can save personal data.
 * <strong>This function is now deprecated. Please use {@link #getIsSaveToLocationAllowed(SaveLocation, String)} instead</strong>
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
 *           the username/email associated with the cloud service being saved to. Use null if a mapping between the AAD username and the cloud service username does not exist or the username is not known.
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
 * Return the policy in string format to the app.
 *  
 * @return The string representing the policy.
 */
String toString();


}

```

### <a name="enable-it-control-over-app-saving-behavior"></a>IT 部門でアプリの保存動作を制御できるようにする

多くのアプリでは、ユーザーがローカルまたはクラウド ストレージ サービスにファイルを保存できる機能を実装しています。 Intune アプリ SDK は、IT 管理者が組織に合ったポリシー制限を適用し、データの漏えいを防ぐのに役立ちます。  IT 部門で制御できるポリシーの 1 つに、ユーザーが "個人用" の管理対象外のデータ ストアに保存できるかどうかというものがあります。 これには、ローカルの場所、SD カード、またはサード パーティ バックアップ サービスへの保存が含まれます。

この機能を有効にするには、アプリによる処理が必要です。 アプリから直接個人またはクラウドの場所に保存することをアプリで許可する場合は、IT 管理者がある場所への保存を許可するかどうかを制御できるように、この機能を実装する必要があります。   

ポリシーが適用されるかどうかを判断するために、アプリでは次の呼び出しを行うことができます。 この呼び出しにより、アプリは、現在の Intune 管理者のポリシーで個人用ストアへの保存が許可されているかどうかを判断できます。 これにより、ユーザーがアプリを介して個人用データ ストアを使用できることを認識できるため、アプリでポリシーを適用できます。

```
MAMComponents.get(AppPolicy.class).getIsSaveToPersonalAllowed();
```

> [!NOTE]
> `MAMComponents.get(AppPolicy.class)` は、デバイスまたはアプリが Intune 管理ポリシーに従わない場合でも、常に null 以外のアプリ ポリシーを返します。

### <a name="let-the-app-detect-if-a-pin-policy-is-required"></a>PIN ポリシーが必要かどうかをアプリで検出できるようにする

一部の Intune アプリ制限では、Intune アプリ SDK での機能と重複しないように、アプリでその機能の一部を無効にする必要がある場合があります。 たとえば、SDK が、ユーザーが PIN を入力することを要求するようにセットアップされている場合、アプリ独自の PIN ユーザー エクスペリエンスを無効にする必要がある場合があります。

起動時にアプリ PIN を要求するように Intune PIN ポリシーがセットアップされているかどうかを判断するために、アプリで次の呼び出しを行うことができます。

```
MAMComponents.get(AppPolicy.class).getIsPinRequired();
```

### <a name="register-for-notifications-from-the-sdk"></a>SDK からの通知への登録  

Intune アプリ SDK を使用すると、IT 管理者が選択的ワイプなどの特定のポリシーを展開したときに、アプリで動作を制御することできます。 IT 管理者がそのようなポリシーを展開すると、Intune サービスは SDK に通知を送信します。

アプリは、`MAMNotificationReceiver` クラスを作成して `MAMNotificationReceiverRegistry` に登録することで、SDK からの通知に登録する必要があります。 これは、次の例に示すように、受信側と、`App.onCreate` で必要な通知の種類を指定することで行います。

```
@Override
public void onCreate() {
    super.onCreate();
    MAMComponents.get(MAMNotificationReceiverRegistry.class)
.registerReceiver(
                new ToastNotificationReceiver(),
MAMNotificationType.WIPE_USER_DATA);
    }
```

`MAMNotificationReceiver` では、単に Intune サービスからの通知を受信します。 SDK はいくつかの通知を直接処理します。 その他の通知はアプリで処理する必要があります。

アプリでは、通知から true または false を返す*必要があります*。 通知の結果として実行しようとした何らかのアクションが失敗した場合を除き、常に true を返す必要があります。 この失敗は、Intune サービスにレポートされる場合があります。 レポートのシナリオ例として、IT 管理者がワイプを開始した後に、アプリがユーザー データのワイプに失敗した場合などがあります。

`MAMNotificationReceiver.onReceive` でブロックすることが安全です。これは、このコールバックは UI スレッドで実行されないためです。

次の `MAMNotificationReceiver` インターフェイスは SDK で定義されます。

```
/**
 * The SDK is signaling that a WG event has occurred.
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

###<a name="types-of-notifications"></a>通知の種類

次の通知はアプリに送信されます。 一部はアプリでの処理が必要な場合があります。

* **`WIPE_USER_DATA`**: この通知は、`MAMUserNotification` クラスで送信されます。 この通知を受信すると、アプリでは `MAMUserNotification` で渡された "企業" ID に関連するすべてのデータを削除する必要があります。 この通知は、現在、Intune サービスの登録解除中に送信されます。 ユーザーのプライマリ名は、通常、登録プロセス中に指定されます。 この通知に登録する場合、アプリがすべてのユーザー データが削除されたことを確認する必要があります。 登録しない場合、アプリでは既定の選択的ワイプの動作が実行されます。

* **`WIPE_USER_AUXILIARY_DATA`**: Intune アプリ SDK に対して既定の選択的ワイプの実行を求めるが、ワイプが発生したときにいくつかの補助的なデータを引き続き削除する必要があるアプリは、この通知に登録できます。  

* **`REFRESH_POLICY`**: この通知は、`MAMUserNotification` で送信されます。 この通知を受信した場合、キャッシュ済みの Intune ポリシーを無効にして更新する必要があります。 通常、SDK がこのタスクを処理します。 ただし、ポリシーが何らかの永続的な方法で使用される場合は、アプリでこのタスクを処理する必要があります。



### <a name="protection-of-backup-data"></a>バックアップ データの保護

Android Marshmallow (API 23) 以降、Android ではアプリのデータをバックアップする方法が 2 つになりました。 各オプションはアプリで使用でき、Intune データ保護が正しく実装されていることを確認するには異なる手順が必要になります。 バックアップ方法の詳細については、[Android API ガイド](http://developer.android.com/guide/topics/data/backup.html)を参照してください。

#### <a name="automatic-backup-for-apps"></a>アプリの自動バックアップ

Android では、アプリのターゲット API に関係なく、Android Marshmallow デバイス上のアプリに対して、[自動完全バックアップ](https://developer.android.com/guide/topics/data/autobackup.html)が提供されるようになりました。 AndroidManifest.xml ファイルで、明示的に `android:allowBackup` を false に設定すると、アプリは Android でバックアップのためにキューに入れられなくなり、"企業" データはアプリ内に残ります。 この場合、これ以上何もする必要はありません。

`android:allowBackup` がマニフェスト ファイルで指定されていない場合でも、`android:allowBackup` 属性は既定で true に設定されます。 つまり、すべてのアプリ データがユーザーの Google ドライブ アカウントに自動的にバックアップされます。これは既定の動作で、*データ漏えいのリスク*を引き起こすものです。 データ保護が確実に適用されるように、SDK を次のように変更する必要があります。 アプリを Android Marshmallow デバイスで実行する場合は、以下のガイドラインに従って、顧客データを適切に保護することが重要です。  

`MAMBackupAgent` または `MAMBackupAgentHelper` を使用してアプリをバックアップするためにバックアップ エージェントを記述していない場合は、自動バックアップでのアプリ データのアップロード方法を考慮し、制御する必要があります。 Intune では、XML でのカスタム ルールの定義機能を含む、Android から使用可能な[自動バックアップ機能](https://developer.android.com/guide/topics/data/autobackup.html)をすべて使用できます。 ただし、以下の手順に従ってデータを保護できるようにする必要があります。

1. 既定の `MAMBackupAgent` を使用して、Intune ポリシー準拠の自動完全バックアップを許可します。 アプリ マニフェストに `android:backupAgent="com.microsoft.intune.mam.client.app.backup.MAMDefaultBackupAgent"` を配置します。

2. アプリで受信する必要がある完全バックアップの種類 (フィルター適用なし、フィルター適用、なし) を決定する際に、アプリで属性 `android:fullBackupContent` を true、false、または XML リソースに設定します。 `android:fullBackupContent` に配置するものはすべて、`com.microsoft.intune.mam.FullBackupContent` という名前のメタデータ タグにコピーします。

    たとえば、アプリで XML ファイルのカスタム ルールに従って完全バックアップを使用する場合は、マニフェストで `com.microsoft.intune.mam.FullBackupContent` メタデータ タグの下に次のようにリソースを指定します。
    ```
    <meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:resource="@xml/my_scheme" />  
    ```



#### <a name="keyvalue-backup"></a>キー/値のバックアップ

キー/値のバックアップ オプションはすべての API で使用でき、`BackupAgentHelper` と `BackupAgent` が使用されます。

##### <a name="backupagenthelper"></a>BackupAgentHelper

`BackupAgentHelper` の実装は、Android のネイティブな機能と MAM 統合の両方の面で、`BackupAgent` よりもとても簡単です。 `BackupAgentHelper` では、ファイル全体と共有設定を `FileBackupHelper` または `SharedPreferencesBackupHelper` にそれぞれ登録できます。 その後、これらは作成時に `BackupAgentHelper` に追加されます。

##### <a name="backupagent"></a>BackupAgent

`BackupAgent` では、バックアップの対象とするデータをより明示的に指定することができます。 ただし、このオプションを使用すると、Android のバックアップのフレームワークを活用することができません。 実装の担当者の場合、MAM からの適切なデータ保護を適用するために必要な手順が増えるためです。 作業のほとんどを開発者が行う必要があるため、MAM 統合は少し複雑になります。

###### <a name="app-does-not-have-a-backup-agent"></a>アプリにバックアップ エージェントがない場合

`android:allowBackup =true` の場合、次の開発者オプションがあります。

####### <a name="full-backup-according-to-a-configuration-file"></a>構成ファイルに従った完全バックアップ

マニフェストで `com.microsoft.intune.mam.FullBackupContent` メタデータ タグの下にリソースを指定します。 例:     `<meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:resource="@xml/my_scheme" />`

`<application>` タグに属性 `android:fullBackupContent="@xml/my_scheme"` を追加します。ここで、`my_scheme` はアプリの XML リソースです。

####### <a name="full-backup-without-exclusions"></a>除外のない完全バックアップ

マニフェストに、`<meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:value="true" />` のようなタグを指定します。

`<application>` タグに次の属性を追加します。`android:fullBackupContent="true"`

###### <a name="app-has-a-backup-agent"></a>アプリにバックアップ エージェントがある場合

`BackupAgent` および `BackupAgentHelper` については、このガイドの前述の推奨事項に従ってください。

Android Marshmallow でのバックアップが簡易化される、`MAMDefaultFullBackupAgent` の使用に切り替えることを検討してください。

##### <a name="before-your-backup"></a>バックアップの前に

バックアップを開始する前に、バックアップを計画しているファイルまたはデータ バッファーのバックアップが許可されていることを確認する必要があります。 ここでは `MAMFileProtectionManager` および `MAMDataProtectionManager` で `isBackupAllowed` 関数を使用して、これを確認します。 ファイルまたはデータ バッファーのバックアップが許可されていない場合、バックアップで使用しようとしないでください。

バックアップ中のある時点で、手順 1 で確認したファイルの ID をバックアップする場合は、データの抽出元ファイルで `backupMAMFileIdentity(BackupDataOutput data, File … files)` を呼び出す必要があります。 これにより、自動的に新しいバックアップ エンティティが作成され、`BackupDataOutput` に書き込まれます。 これらのエンティティは、復元時に自動的に使用されます。

#### <a name="azure-directory-authentication-library-setup"></a>Azure Directory 認証ライブラリのセットアップ  

SDK は認証と条件付き起動シナリオで ADAL を利用します。 これらのシナリオでは、アプリに Azure Active Directory (Azure AD) 構成がある程度必要になります。 構成値は、 `AndroidManifest` メタデータを使用して SDK に伝達されます。

アプリをセットアップして適切な認証を有効にするには、`AndroidManifest` のアプリ ノードに次の内容を追加します。 これらの構成の一部は、通常、アプリで認証のために ADAL を使用する場合にのみ必要になります。 その場合、Azure AD でのアプリ自体の登録時に使用した特定の値が必要になります。 これにより、Azure AD で 2 つ (アプリと SDK から 1 つずつ) の個別の登録値が認識されるため、ユーザーに対して認証が 2 回求められることがなくなります。

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

##### <a name="common-adal-configurations"></a>ADAL の一般的な構成

上記で説明した値の一般的な構成を次に示します。

###### <a name="app-does-not-integrate-adal"></a>アプリに ADAL が統合されない場合

* Azure AD アカウントがセットアップされている、目的の環境に権限を設定する必要があります。

* SkipBroker を true に設定する必要があります。

###### <a name="app-integrates-adal"></a>アプリに ADAL が統合される場合

* Azure AD アカウントがセットアップされている、目的の環境に権限を設定する必要があります。

* クライアント ID は、アプリのクライアント ID に設定する必要があります。

* `NonBrokerRedirectURI` をアプリの有効なリダイレクト URI に設定する必要があります。 または、有効な Azure AD リダイレクト URI として `urn:ietf:wg:oauth:2.0:oob` をセットアップする必要があります。

* SkipBroker は false に設定する (または存在しない) 必要があります。

* Azure AD は、ブローカーのリダイレクト URI を受け入れるようにセットアップする必要があります。

###### <a name="app-integrates-adal-but-does-not-support-the-azure-ad-authenticator-app"></a>アプリに ADAL が統合されるが、Azure AD 認証アプリがサポートされない場合

* Azure AD アカウントがセットアップされている、目的の環境に権限を設定する必要があります。

* クライアント ID は、アプリのクライアント ID に設定する必要があります。

* `NonBrokerRedirectURI` をアプリの有効なリダイレクト URI に設定する必要があります。 または、有効な Azure AD リダイレクト URI として `urn:ietf:wg:oauth:2.0:oob` をセットアップする必要があります。

#### <a name="logging-in-the-sdk"></a>SDK でのログ記録

ログ記録は、 `java.util.logging` フレームワークを介して実行されます。 ログを受信するには、[Java テクニカル ガイド](http://docs.oracle.com/javase/6/docs/technotes/guides/logging/overview.html)の説明に従って、グローバル ログを設定します。 アプリによっては、`App.onCreate` はログ記録を開始する場所として一般的に最適です。 ログ メッセージはクラス名によってキー指定され、非表示になる場合があることに注意してください。

###<a name="multi-identity"></a>複数の ID

既定では、Intune アプリ SDK はポリシーをアプリ全体に適用します。 複数 ID は、ID 別レベルでのポリシー適用を可能にする MAM の機能です。 これには、他の MAM 機能よりはるかに多くのアプリの参加が必要です。 アプリは、アクティブな ID を変更するときにアプリ SDK に通知する必要があります。 また、SDK は ID の変更が必要なときにもアプリに通知する必要があります。

現時点では、サポートされる管理対象 ID は 1 つだけです。 ユーザーがデバイスまたはアプリを登録すると、SDK はこの ID を使用し、それをプライマリ管理対象 ID であると判断します。 アプリの他のユーザーは、無制限のポリシー設定を持つ管理対象外として扱われます。

ID は文字列として簡単に定義されることに注意してください。 ID の大文字と小文字は区別されません。 SDK に ID を要求すると返される ID は、大文字と小文字の使い分けが ID 設定時の本来のものと異なる可能性があります。

####<a name="enabling-multi-identity"></a>複数 ID を有効にする

既定では、すべてのアプリが単一 ID アプリと見なされます。 アプリは、Android マニフェストで以下のメタデータを配置することで複数 ID に対応していることを宣言します。

```
<meta-data
            android:name="com.microsoft.intune.mam.MAMMultiIdentity"
            android:value="true" />
```
####<a name="setting-the-identity"></a>ID の設定

次のレベルでアプリの ID を設定できます。

1. プロセス レベル

2. コンテキスト (通常は `Activity`) レベル

3. スレッド レベル

スレッド レベルで設定された ID は、プロセス レベルで設定された ID よりも優先される `Context` レベルで設定された ID よりも優先されます。 `Context` で設定された ID は、適切な場合にのみ使用されます。 ファイル I/O タスクなどに `Context` は関連付けられません。 `MAMPolicyManager` の次のメソッドは、ID を設定し、以前に設定された ID 値を取得する場合に使用できます。

```
public static void setUIPolicyIdentity(final Context context, final String identity, final MAMSetUIIdentityCallback mamSetUIIdentityCallback);

public static String getUIPolicyIdentity(final Context context);

public static MAMIdentitySwitchResult setProcessIdentity(final String identity);

public static String getProcessIdentity();

public static MAMIdentitySwitchResult setCurrentThreadIdentity(final String identity);

public static String getCurrentThreadIdentity();

/**
 * Get the currently applicable app policy. Same as MAMComponents.get(AppPolicy.class). This method does
    not take the context identity into account.
 */
public static AppPolicy getPolicy();

/**
 * Get the currently applicable app policy, taking the context
 * identity into account.
 */
public static AppPolicy getPolicy(final Context context);


public static AppPolicy getPolicyForIdentity(final String identity);

public static boolean getIsIdentityManaged(final String identity);

```
null に設定することで、アプリの ID をクリアすることもできます。 無制限の ID として空の文字列を使用することができます。 ID を設定するすべてのメソッドは、``` MAMIdentitySwitchResult``` を使用して結果の値を返します。 次の 4 つの値を返すことができます。

* **SUCCEEDED**: ID 変更が正常に行われました。

* **NOT_ALLOWED**: ID は変更できません。 これは、登録済みユーザーとして同じ会社に属している別の企業ユーザーに切り替えようとした場合に発生します。 また、現在のスレッドに別の ID が設定されている状態で UI (`Context`) ID を設定しようした場合にも発生します。

* **CANCELLED**: ユーザーが ID 変更を取り消しました。通常、この取り消しは、PIN/auth プロンプトで [戻る] ボタンを選択して行われます。

* **FAILED**: 不明な理由により、ID 変更が失敗しました。

`Context` ID を設定する場合、結果は非同期的にレポートされます。 `Context` が `Activity` クラスの場合、条件付き起動が完了するまで、ID 変更が正常に行われたかどうかは認識されません。 条件付き起動の場合、ユーザーが PIN または完全な会社の資格情報を入力する必要があります。 このパラメーターに null を渡すことができても、アプリはこの結果を受信するために ```MAMSetUIIdentityCallback``` の実装が必要になります。

```
public interface MAMSetUIIdentityCallback {
    void notifyIdentityResult(MAMIdentitySwitchResult identitySwitchResult);
}
```

アクティビティの ID は、`MAMActivity` を呼び出す代わりに ```MAMPolicyManager.setUIPolicyIdentity``` のメソッドを使用して直接設定することもできます。 次のメソッドを使用してこれを行うことができます。

 ```public final void switchMAMIdentity(final String newIdentity);```

アプリは、アクティビティの ID 変更の試行結果通知を受けるために `MAMActivity` のメソッドを上書きすることもできます。

```public void onSwitchMAMIdentityComplete(final MAMIdentitySwitchResult result);```

> [!NOTE]
> ID の切り替えには、アクティビティの再作成が必要になる場合があります。 その場合、```onSwitchMAMIdentityComplete``` コールバックはアクティビティの新しいインスタンスに配信されます。


####<a name="implicit-identity-changes"></a>暗黙的な ID 変更

アプリで ID を設定できるだけでなく、スレッドまたはコンテキストの ID は、別の MAM が有効なアプリからのデータに基づいて変更できます。 たとえば、アクティビティが別の MAM アプリによって送信された `Intent` クラスから起動された場合、そのアクティビティの ID は、`Intent` クラスの送信時に他のアプリで有効な ID に基づいて設定されます。

サービスについては、スレッドの ID は、`onStart` または `onBind` 呼び出しの期間に同様に設定されます。 `onBind` から返される `Binder` の呼び出しでも、スレッド ID が一時的に設定されます。 ```ContentProvider``` の呼び出しでは同様に、それらの期間にスレッド ID を設定します。

さらに、アクティビティとのユーザー対話により、暗黙的な ID 切り替えが行われる場合があります。 たとえば、ユーザーが ```Resume``` 中に認証プロンプトを取り消した場合、空の ID に暗黙的に切り替えられます。
アプリはこれらの変更を認識し、場合によっては、必要に応じて禁止することができます。 ```MAMService``` および ```MAMContentProvider``` は、サブクラスで上書きできる以下のメソッドを公開します。

```
public void onMAMIdentitySwitchRequired(final String identity,
    final AppIdentitySwitchResultCallback callback);
```
```MAMActivity``` の場合、メソッドには次の追加のパラメーターがあります。
```
public void onMAMIdentitySwitchRequired(final String identity,
    final AppIdentitySwitchReason reason,
    final AppIdentitySwitchResultCallback callback);
```
```AppIdentitySwitchReason``` 部分は、暗黙的な切り替えのソースをキャプチャします。 受け入れられる値は ```CREATE```、```RESUME_CANCELLED```、および ```NEW_INTENT``` です。  ```RESUME_CANCELLED``` の理由は、アクティビティの再開時に、PIN、認証、または他のコンプライアンス UI が表示され、ユーザーがその UI を取り消そうとした場合 (通常は、[戻る] ボタンを使用) に使用されます。
```AppIdentitySwitchResultCallback``` は次のとおりです。
```
public interface AppIdentitySwitchResultCallback {
    /**
     * @param result
     *            whether the identity switch can proceed.
     */
    void reportIdentitySwitchResult(AppIdentitySwitchResult result);
}
```
```AppIdentitySwitchResult``` は ```SUCCESS``` または ```FAILURE``` です。

```MAMService.onMAMBind``` から返される `Binder` クラスによるものを除く、すべての暗黙的な ID 変更に対してメソッド ```onMAMIdentitySwitchRequired``` が呼び出されます。 ```onMAMIdentitySwitchRequired``` の既定の実装では、理由が ```RESUME_CANCELLED``` の場合、直ちに ```reportIdentitySwitchResult(FAILURE)``` を呼び出し、それ以外の場合は ```reportIdentitySwitchResult(SUCCESS)``` を呼び出します。

ほとんどのアプリでは、別の方法で ID 切り替えをブロックしたり遅らせたりする必要はおそらくありません。 ただし、アプリで必要な場合は、次の点を考慮してください。

* ID 切り替えがブロックされている場合、```Receive``` 共有設定でデータ受信が禁止されている場合と同じ結果になります。

* サービスがメイン スレッドで実行されている場合、```reportIdentitySwitchResult``` を同期的に呼び出す*必要があります*。そうしないと、UI スレッドがハングします。

* ```Activity``` 作成の場合、```onMAMCreate``` の前に ```onMAMIdentitySwitchRequired``` が呼び出されます。 アプリで ID 切り替えを許可するかどうかを確認するために UI を表示する必要がある場合、その UI を別のアクティビティを使用して表示する必要があります。

* ```Activity``` では、```RESUME_CANCELLED``` と同等の理由で空の ID への切り替えが要求された場合、アプリは再開されたアクティビティを変更し、その ID 切り替えに適したデータを表示する必要があります。 これができない場合、アプリは切り替えを拒否する必要があります。 ユーザーは再開 ID のポリシーへの準拠を再度求められます (たとえば、PIN 入力画面が表示されます)。

> [!NOTE]
> 複数 ID のアプリは常に、管理対象と管理対象外の両方のアプリからデータを受信します。 アプリは、管理された方法で管理対象 ID からのデータを処理する必要があります。 要求された ID が管理対象の ```(MAMPolicyManager.getIsIdentityManaged)``` であるが、アプリでそのアカウントを使用できない場合 (電子メール アカウントなどのアカウントはアプリで最初にセットアップする必要があるなどの理由で)、ID 切り替えを拒否する必要があります。

###<a name="file-protection"></a>ファイル保護

すべてのファイルに、スレッドとプロセス ID に基づいて作成時に関連付けられた ID があります。 この ID は、ファイルの暗号化と選択的ワイプの両方に使用されます。 ID に暗号化を必要とするポリシーがあるファイルのみが暗号化されます。 SDK の既定の選択的ワイプでは、ワイプが要求されている ID に関連付けられたファイルのみがワイプされます。 アプリでは ```MAMFileProtectionManager``` を使用して、ファイルの ID の照会または変更を行うことができます。
```
public final class MAMFileProtectionManager {

    /**
     * Protect a file. This will synchronously trigger whatever protection is required for the file, and will tag the file for
     * future protection changes.
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
     * Get the protection info on a file.
     *
     * @param file
     *            File or directory to get information on.
     * @return File protection info, or null if there is no protection info.
     * @throws IOException
     *             If the file cannot be read or opened.
     */
    public static MAMFileProtectionInfo getProtectionInfo(final File file) throws IOException;
}

public interface MAMFileProtectionInfo {
String getIdentity();
}
```

> [!NOTE]
> ファイルの ID タグ付けはオフライン モードに依存します。 次の点を考慮してください。
> * ポータル サイト アプリをインストールしていない場合は、ファイルに ID タグを付けることはできません。
>
> * ポータル サイト アプリをインストールしていても、アプリにポリシーがない場合は、ファイルに確実に ID タグを付けることはできません。
>
> * ファイルに ID タグを付けられるようになると、以前に作成されたすべてのファイルは、アプリが単一 ID で管理されるアプリとしてインストールされている場合を除き、個人用 (空の文字列 ID に属する) として扱われます。 その場合、ファイルは登録済みユーザーに属するものとして扱われます。

####<a name="data-protection"></a>データの保護

複数 ID に属しているものとしてファイルにタグを付けることはできません。 同じファイル内の別のユーザーに属しているデータを格納する必要があるアプリでは、```MAMDataProtectionManager``` で提供される機能を使用して手動でこれを行うことができます。 これにより、アプリではデータを暗号化し、特定のユーザーに関連付けることができます。 暗号化されたデータは、ファイルのディスクへの格納に適しています。 ID に関連付けられているデータを照会することができ、後でデータの暗号化を解除することができます。

```
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
###<a name="content-providers"></a>コンテンツ プロバイダー

アプリでは、```ParcelFileDescriptor``` ではなく ```ContentProvider``` を使用して企業データを提供する可能性がある場合、```MAMContentProvider``` メソッド ```isProvideContentAllowed(String)``` を呼び出して、コンテンツの所有者 ```UPN``` を渡す必要があります。 この関数で false が返されると、コンテンツを呼び出し元に返すことはできません。 コンテンツ プロバイダーから返されたファイル記述子は、ファイル ID に基づいて自動的に処理されます。

###<a name="selective-wipe"></a>選択的ワイプ

アプリを ```WIPE_USER_DATA``` 通知に登録すると、SDK の既定の選択的ワイプ動作の利点が得られなくなります。 複数 ID 対応アプリの場合、MAM の既定の選択的ワイプではワイプ対象の ID と一致するファイルのみがワイプされるため、これがとても重要になることがあります。

複数 ID 対応アプリを構築する場合は、```WIPE_USER_AUXILIARY_DATA``` に登録できます。 この通知では、SDK の既定のワイプ動作を活用できます。 この通知は、SDK の既定の選択的ワイプを実行する直前に送信されます。 アプリは ```WIPE_USER_DATA``` と ```WIPE_USER_AUXILIARY_DATA``` の両方に登録できないことに注意してください。

### <a name="known-platform-limitations"></a>既知のプラットフォームの制限事項

#### <a name="file-size-limitations"></a>ファイル サイズの制限

Android では、Dalvik 実行可能ファイル形式の制限が、ProGuard なしで実行される大規模なコード ベースにおいて問題になる場合があります。 具体的には、次の制限事項が発生する可能性があります。

* フィールドの 65,000 の制限

* メソッドの 65,000 の制限

多くのプロジェクトを含める場合は、すべての `android:package` で R のコピーが取得されます。これによるライブラリの追加に伴ってフィールドの数が大幅に増加します。 次の推奨事項は、この制限の緩和に役立つ場合があります。

* ライブラリのすべてのプロジェクトで、可能な限り同じ `android:package` を共有するようにしてください。 これにより、散発的にフィールドのエラーが発生することはありません。純粋にビルド時の問題であるためです。 さらに、より新しいバージョンの Android SDK では、DEX ファイルを前処理して冗長性の一部を取り除きます。 これにより、さらにフィールドからの距離が削減されます。

* 使用可能な最新の Android SDK ビルド ツールを使用します。

* 不要な使用しないすべてのライブラリを削除します (`android.support.v4` など)。

#### <a name="policy-enforcement-limitations"></a>ポリシーの適用の制限事項

**画面キャプチャ**: SDK は `Activity.onCreate` が既に終了した `Activity` クラスに対し、新しい画面キャプチャの設定値を適用することができません。 これにより、アプリがスクリーン ショットを無効にするようセットアップされているものの、スクリーン ショットを引き続き作成できる期間が発生する場合があります。

**コンテンツ リゾルバー**: 転送ポリシーまたは受信ポリシーにより、別のアプリのコンテンツ プロバイダーにアクセスするためのコンテンツ リゾルバーの使用がブロックされるか、部分的にブロックされる場合があります。 この場合、`ContentResolver` メソッドが null を返すか、失敗値をスローします  (たとえば、ブロックされている場合、`openOutputStream` は `FileNotFoundException` をスローします)。アプリは次の呼び出しを行って、コンテンツ リゾルバーを介してデータを書き込めなかったのはポリシーが原因 (あるいは原因である可能性がある) かどうかを確認できます。

    MAMComponents.get(AppPolicy.class).getIsSaveToLocationAllowed(contentURI)

**エクスポートされたサービス**: Intune アプリ SDK に含まれる `AndroidManifest.xml` ファイルには `MAMNotificationReceiverService` があります。 これは、ポータル サイト アプリから対応アプリに通知を送信できるようにする、エクスポートされたサービスである必要があります。 このサービスでは、ポータル サイト アプリのみが通知の送信を許可されるように、呼び出し元を確認します。

### <a name="android-best-practices"></a>Android のベスト プラクティス

Intune SDK は Android API によって提供されるコントラクトを維持します。ただし、ポリシーの適用の結果として、エラー状態がより頻繁にトリガーされる可能性があります。 これらの Android のベスト プラクティスにより、エラーの可能性が減少します。

* null を返す可能性のある Android SDK 関数で、null が返される可能性が高くなりました。 問題を最小限に抑えるため、null チェックが適切な場所にあることを確認します。

* 確認できる機能については、SDK API を使用して確認します。

* すべての派生関数はそのスーパークラスのバージョンを介して呼び出しを行う必要があります。

* あいまいな方法で API を使用することを回避します。 たとえば、`requestCode` を確認しないで `Activity.startActivityForResult/onActivityResult` を使用すると、予想外の動作が発生します。

