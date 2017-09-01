---
title: "アプリ ラッピング ツールで Android アプリをラップする"
description: "この記事の情報を使用して、アプリ自体のコードを変更することなく、Android アプリをラップする方法について説明します。 モバイル アプリ管理ポリシーを適用できるように、アプリを準備します。"
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 07/07/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e9c349c8-51ae-4d73-b74a-6173728a520b
ms.reviewer: oldang
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: e8707253139ee5a12a48d38a333ae49fbb4d3ead
ms.sourcegitcommit: 4dc5bed94cc965a54eacac2d87fb2d49c9300c3a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/25/2017
---
# <a name="prepare-android-apps-for-app-protection-policies-with-the-intune-app-wrapping-tool"></a>Intune アプリ ラッピング ツールでアプリ保護ポリシーを利用するために Android アプリを準備する

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

Android 用 Microsoft Intune アプリ ラッピング ツールを使用して社内 Android アプリの動作を変更すれば、アプリ自体のコードを変更しなくてもアプリの機能を制限できます。

このツールは、PowerShell で実行される Windows のコマンドライン アプリケーションであり、Android アプリのラッパーを作成します。 アプリがラッピングされた後は、Intune で[モバイル アプリケーション管理ポリシー](/intune-classic/deploy-use/configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console)を構成することによって、アプリの機能を変更できます。


このツールを実行する前に、「[アプリ ラッピング ツールを実行するうえでのセキュリティ上の考慮事項](#security-considerations-for-running-the-app-wrapping-tool)」を確認してください。 このツールをダウンロードするには、GitHub の「[Microsoft Intune App Wrapping Tool for Android](https://github.com/msintuneappsdk/intune-app-wrapping-tool-android)」 (Android 用 Microsoft Intune アプリ ラッピング ツール) にアクセスしてください。



## <a name="fulfill-the-prerequisites-for-using-the-app-wrapping-tool"></a>ラッピング ツールを使用するための前提条件を満たす

-   Windows 7 以降を実行している Windows コンピューターでアプリ ラッピング ツールを実行する必要があります。

-   入力アプリは、有効な Android アプリケーション パッケージであり、かつそのファイル拡張子が .apk であるだけでなく、次の要件を満たしている必要があります。

    -   暗号化できない。
    -   Intune アプリ ラッピング ツールでまだラップされていない。
    -   Android 4.0 以降を対象に記述されている。

-   このアプリは、自社で開発されているか、自社向けに開発されている必要があります。 Google Play ストアからダウンロードしたアプリでこのツールを使用することはできません。

-   アプリ ラッピング ツールを実行するには、最新バージョンの [Java ランタイム環境](http://java.com/download/)をインストールし、Java の path 変数が Windows 環境変数で C:\ProgramData\Oracle\Java\javapath に設定されている必要があります。 詳細については、[Java のドキュメント](http://java.com/download/help/)を参照してください。

    > [!NOTE]
    > 場合によっては、32 ビット バージョンの Java を使用すると、メモリに関連した問題が発生する可能性があります。 64 ビット バージョンをインストールすることをお勧めします。

- Android では、すべてのアプリ パッケージ (.apk) が署名されている必要があります。 既存の証明書の**再利用**と署名証明書の全体的なガイダンスについては、「[署名証明書とラッピング アプリの再利用](https://docs.microsoft.com/en-us/intune/app-wrapper-prepare-android#reusing-signing-certificates-and-wrapping-apps)」を参照してください。 ラッピングされた出力アプリへの署名に必要な**新しい**資格情報を生成するには、Java の実行可能ファイル keytool.exe を使います。 設定するパスワードはすべて安全である必要がありますが、後でアプリ ラッピング ツールを実行するときに必要になるので記録しておきます。

## <a name="install-the-app-wrapping-tool"></a>アプリ ラッピング ツールをインストールする

1.  [GitHub リポジトリ](https://github.com/msintuneappsdk/intune-app-wrapping-tool-android)から Android 用 Intune アプリ ラッピング ツールのインストール ファイル InstallAWT.exe を Windows コンピューターにダウンロードします。 インストール ファイルを開きます。

2.  ライセンス条項に同意し、インストールを完了します。

このツールをインストールしたフォルダーをメモしておきます。 既定の場所は、C:\Program Files (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool です。

## <a name="run-the-app-wrapping-tool"></a>アプリ ラッピング ツールを実行する

1.  アプリ ラッピング ツールをインストールした Windows コンピューターで PowerShell ウィンドウを開きます。

2.  ツールをインストールしたフォルダーから、アプリ ラッピング ツールの PowerShell モジュールをインポートします。

    ```
    Import-Module .\IntuneAppWrappingTool.psm1
    ```

3.  **invoke-AppWrappingTool** コマンドを使用してツールを実行します。コマンドの構文は次のとおりです。
    ```
    Invoke-AppWrappingTool [-InputPath] <String> [-OutputPath] <String> -KeyStorePath <String> -KeyStorePassword <SecureString>
    -KeyAlias <String> -KeyPassword <SecureString> [-SigAlg <String>] [<CommonParameters>]
    ```

 **invoke-AppWrappingTool** コマンドのプロパティの詳細を次の表に示します。

|プロパティ|説明|例|
|-------------|--------------------|---------|
|**-InputPath**&lt;String&gt;|ソースの Android アプリ (.apk) のパス。| |
|**-OutputPath**&lt;String&gt;|出力先の Android のアプリへのパス。 InputPath と同じディレクトリ パスを指定した場合、パッケージ化は失敗します。| |
|**-KeyStorePath**&lt;String&gt;|署名用の公開/秘密キーのペアを含むキーストア ファイルへのパス。|既定では、キーストア ファイルは "C:\Program Files (x86)\Java\jreX.X.X_XX\bin" に格納されます。 |
|**-KeyStorePassword**&lt;SecureString&gt;|キーストアの暗号化を解除するために使用するパスワード。 Android では、すべてのアプリケーション パッケージ (.apk) に署名する必要があります。 Java キーツールを使用して KeyStorePassword を生成できます。 詳細については、こちらの Java [KeyStore](https://docs.oracle.com/javase/7/docs/api/java/security/KeyStore.html) を参照してください。| |
|**-KeyAlias**&lt;String&gt;|署名に使用するキーの名前。| |
|**-KeyPassword**&lt;SecureString&gt;|署名に使用する秘密キーの暗号化を解除するために使用するパスワード。| |
|**-SigAlg**&lt;SecureString&gt;| (省略可能) 署名に使用する署名アルゴリズムの名前。 アルゴリズムは秘密キーと互換性を持つ必要があります。|例: SHA256withRSA、SHA1withRSA|
| **&lt;CommonParameters&gt;** | (省略可能) コマンドは、verbose、debug などの一般的な PowerShell パラメーターをサポートします。 |


- 共通パラメーターの一覧については、 [Microsoft スクリプト センター](https://technet.microsoft.com/library/hh847884.aspx)を参照してください。

- ツールの詳細な使用方法を確認するには、次のコマンドを入力します。

    ```
    Help Invoke-AppWrappingTool
    ```

**例:**

PowerShell モジュールをインポートします。
```
Import-Module "C:\Program Files (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool\IntuneAppWrappingTool.psm1"
```
ネイティブ アプリ HelloWorld.apk に対してアプリ ラッピング ツールを実行します。
```
invoke-AppWrappingTool -InputPath .\app\HelloWorld.apk -OutputPath .\app_wrapped\HelloWorld_wrapped.apk -KeyStorePath "C:\Program Files (x86)\Java\jre1.8.0_91\bin\mykeystorefile" -keyAlias mykeyalias -SigAlg SHA1withRSA -Verbose
```

**KeyStorePassword** と **KeyPassword** の入力を求められます。 キーストア ファイルの作成に使用した資格情報を入力します。

ラップされたアプリとログ ファイルが生成されて、指定した出力パスに保存されます。

## <a name="reusing-signing-certificates-and-wrapping-apps"></a>署名証明書とラッピング アプリの再利用
Android では、Android デバイスにインストールするために、すべてのアプリを有効な証明書で署名する必要があります。

ラップされたアプリは、ラッピング処理の一部、または既存の署名ツール (ラッピングが破棄される前のアプリの署名情報) を使用したラッピングの*後*のいずれかに署名できます。
 
可能であれば、ビルド処理中に既に使用されている署名情報を、ラッピング中に使用する必要があります。 特定の組織では、キーストア情報 (例: アプリのビルド チーム) を所有するユーザーと共同作業する必要がある場合があります。 

以前の署名証明書を使用できない、またはアプリを以前に展開していない場合は、[Android 開発者ガイド](https://developer.android.com/studio/publish/app-signing.html#signing-manually)の手順に従って、新しい署名証明書を作成できます。

アプリが別の署名証明書を使って以前に展開されている場合、アップグレード後にアプリを Intune コンソールにアップロードすることはできません。 アプリをビルドした証明書ではなく、別の証明書を使ってアプリが署名されている場合、アプリのアップグレード シナリオは中断されます。 このように、新しい署名証明書は、アプリのアップグレード用に保持される必要があります。 

## <a name="security-considerations-for-running-the-app-wrapping-tool"></a>アプリ ラッピング ツールを実行するうえでのセキュリティ上の考慮事項
スプーフィング、情報漏えい、および権限の昇格攻撃の可能性を抑制するには、次の手順に従います。

-   入力基幹業務 (LOB) アプリケーション、出力アプリケーション、Java KeyStore が、アプリ ラッピング ツールを実行している Windows コンピューター上に存在することを確認します。

-   このツールを実行しているコンピューター上の Intune コンソールに出力アプリケーションをインポートします。 Java キーツールについて詳しくは、[キーツール](https://docs.oracle.com/javase/8/docs/technotes/tools/unix/keytool.html)に関するページをご覧ください。

-   出力アプリケーションとツールが汎用名前付け規則 (UNC) パスにあり、ツールと入力ファイルを同じコンピューター上で実行していない場合、[インターネット プロトコル セキュリティ (IPsec)](http://wikipedia.org/wiki/IPsec) または[サーバー メッセージ ブロック (SMB) 署名](https://support.microsoft.com/kb/887429)を使用して環境をセキュリティで保護します。

-   アプリケーションが信頼されたソースからのものであることを確認します。

-   ラップされたアプリが格納されている出力ディレクトリをセキュリティで保護します。 出力にユーザー レベルのディレクトリを使用することを検討します。

### <a name="see-also"></a>関連項目
- [Microsoft Intune によるモバイル アプリケーション管理のためにアプリを準備する方法を決める](apps-prepare-mobile-application-management.md)

- [SDK を使用してモバイル アプリケーション管理に対応する](/intune/classic/deploy-use/use-the-sdk-to-enable-apps-for-mobile-application-management)
