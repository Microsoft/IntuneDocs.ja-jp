---
title: "アプリ ラッピング ツールで Android アプリをラップする |Microsoft Intune"
description: "このトピックの情報を使用して、アプリ自体のコードを変更することなく、Android アプリをラップする方法について説明します。 モバイル アプリ管理ポリシーを適用できるように、アプリを準備します。"
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e9c349c8-51ae-4d73-b74a-6173728a520b
ms.reviewer: oldang
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: fe3a9f2fd9ce9a3c3f776dcfd9ad3347a63d0fc1
ms.openlocfilehash: e623755cf926020bcb66d8a6d40e5cce9b46b0ae


---

# Intune アプリ ラッピング ツールでモバイル アプリケーションを管理するために Android アプリを準備する
**Android 用 Microsoft Intune アプリ ラッピング ツール**を使用して社内 Android アプリの動作を変更すれば、アプリ自体のコードを変更しなくてもアプリの機能を制限できます。

このツールは、PowerShell で実行される Windows のコマンドライン アプリケーションであり、Android アプリの "ラッパー" を作成します。 アプリがラッピングされると、Intune で[モバイル アプリケーション管理ポリシー](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md)を構成することによって、アプリの機能を変更できます。


このツールを実行する前に、「[アプリ ラッピング ツールを実行するうえでのセキュリティ上の考慮事項](#security-considerations-for-running-the-app-wrapping-tool)」を確認してください。 このツールをダウンロードするには、GitHub の「[Microsoft Intune App Wrapping Tool for Android](https://github.com/msintuneappsdk/intune-app-wrapping-tool-android)」 (Android 用 Microsoft Intune アプリ ラッピング ツール) にアクセスしてください。



## 手順 1: アプリ ラッピング ツールを使用するための前提条件を満たす

-   Windows 7 以降を実行している Windows コンピューターでアプリ ラッピング ツールを実行する必要があります。

-   入力アプリは、有効な Android アプリケーション パッケージであり、かつそのファイル拡張子が **.apk** であるだけでなく、次の要件を満たしている必要があります。

    -   暗号化できない

    -   Intune アプリ ラッピング ツールでまだラップされていない
    -   Android 4.0 以降を対象に記述されている

-   このアプリは、自社で開発されているか、自社向けに開発されている必要があります。 Google Play ストアからダウンロードしたアプリでこのツールを使用することはできません。

-   アプリ ラッピング ツールを実行するには、最新バージョンの [Java ランタイム環境](http://java.com/download/)をインストールし、Java の path 変数が Windows 環境変数で **C:\ProgramData\Oracle\Java\javapath** に設定されている必要があります。 詳細については、[Java のドキュメント](http://java.com/download/help/)を参照してください。

    > [!NOTE]
    > 場合によっては、32 ビット バージョンの Java を使用すると、メモリに関連した問題が発生する可能性があります。 代わりに、64 ビット バージョンをインストールすることをお勧めします。

- Android では、すべてのアプリ パッケージ (.apks) が署名されている必要があります。 ラッピングされた出力アプリへの署名に必要な資格情報を生成するには、Java キー ツールを使用します。 たとえば、次のコマンドは、Java 実行可能ファイル **keytool.exe** を使用して、ラッピングされた出力アプリの署名のため、アプリ ラッピング ツールによる署名に使用できるキーを生成します。

    ```
    keytool.exe -genkeypair -v -keystore mykeystorefile -alias mykeyalias -keyalg RSA -keysize 2048 -validity 50000
    ```
    この例では、RSA アルゴリズムを使用してキー ペア (公開キーとそれに関連付けられたサイズ 2048 ビットの秘密キー) を生成した後、X.509 v3 自己署名証明書に公開キーをラッピングします。この証明書は単一要素の証明書チェーンとして格納されます。 この証明書チェーンと秘密キーは、"mykeystorefile" という名前の新しいキーストア エントリに格納され、エイリアス "mykeyalias" によって識別されます。 キーストア エントリは 50,000 日間有効です。

    このコマンドでは、キーストアとキーのパスワードの指定を求められます。 安全で推測されにくいパスワードを使用しますが、後でアプリ ラッピング ツールを実行するときに必要になるので憶えておく必要があります。

    Java [keytool](http://docs.oracle.com/javase/6/docs/technotes/tools/windows/keytool.html) と Java [KeyStore](https://docs.oracle.com/javase/7/docs/api/java/security/KeyStore.html) の詳細については、Oracle のドキュメント Web サイトを参照してください。

## 手順 2: アプリ ラッピング ツールをインストールする

1.  [GitHub リポジトリ](https://github.com/msintuneappsdk/intune-app-wrapping-tool-android)から Android 用 Intune アプリ ラッピング ツールのインストール ファイル **InstallAWT.exe** を Windows コンピューターにダウンロードして開きます。

2.  ライセンス条項に同意し、インストールを完了します。

このツールをインストールしたフォルダーをメモしておきます。 既定の場所は、**C:\Program Files (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool** です。

## 手順 3: アプリ ラッピング ツールを実行する

1.  アプリ ラッピング ツールをインストールした Windows コンピューターで、管理者モードで PowerShell ウィンドウを開きます。

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
|**-OutputPath**&lt;String&gt;|"出力先" の Android のアプリへのパス。 InputPath と同じディレクトリ パスを指定した場合、パッケージ化は失敗します。| |
|**-KeyStorePath**&lt;String&gt;|署名用の公開/秘密キーのペアを含むキーストア ファイルへのパス。|既定では、キーストア ファイルは "C:\Program Files (x86)\Java\jreX.X.X_XX\bin" に格納されます。 |
|**-KeyStorePassword**&lt;SecureString&gt;|キーストアの暗号化を解除するために使用するパスワード。 Android では、すべてのアプリケーション パッケージ (.apk) に署名する必要があります。 Java キー ツールを使用して KeyStorePassword を生成できます。 詳細については、こちらの Java [keystore](https://docs.oracle.com/javase/7/docs/api/java/security/KeyStore.html) を参照してください。| |
|**-KeyAlias**&lt;String&gt;|署名に使用するキーの名前。| |
|**-KeyPassword**&lt;SecureString&gt;|署名に使用する秘密キーの暗号化を解除するために使用するパスワード。| |
|**-SigAlg**&lt;SecureString&gt;| (省略可能) 署名に使用する署名アルゴリズムの名前。 アルゴリズムは秘密キーと互換性を持つ必要があります。|例: SHA256withRSA、SHA1withRSA、MD5withRSA|
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
ネイティブ アプリ **HelloWorld.apk** に対してアプリ ラッピング ツールを実行します。 
```
invoke-AppWrappingTool -InputPath .\app\HelloWorld.apk -OutputPath .\app_wrapped\HelloWorld_wrapped.apk -KeyStorePath "C:\Program Files (x86)\Java\jre1.8.0_91\bin\mykeystorefile" -keyAlias mykeyalias -SigAlg SHA1withRSA -Verbose
```

**KeyStorePassword** と **KeyPassword**の入力を求められます。 キーストア ファイルの作成に使用した資格情報を入力します。

ラップされたアプリは、指定した出力パスにログ ファイルと共に生成されて保存されます。

## アプリ ラッピング ツールを実行するうえでのセキュリティ上の考慮事項
スプーフィング、情報漏えい、および権限の昇格攻撃の可能性を抑制するには、次の手順に従います。

-   入力基幹業務 (LOB) アプリケーション、出力アプリケーション、Java KeyStore が、アプリ ラッピング ツールを実行している Windows コンピューター上に存在することを確認します。

-   このツールを実行しているコンピューター上の Intune コンソールに出力アプリケーションをインポートします。 Java の keytool の詳細については、「[keytool](https://docs.oracle.com/javase/8/docs/technotes/tools/unix/keytool.html)」を参照してください。

-   出力アプリケーションとツールが汎用名前付け規則 (UNC) パスにあり、ツールと入力ファイルを同じコンピューター上で実行していない場合、 [インターネット プロトコル セキュリティ (IPsec)](http://en.wikipedia.org/wiki/IPsec) または [サーバー メッセージ ブロック (SMB) 署名](https://support.microsoft.com/en-us/kb/887429)を使用して環境をセキュリティで保護します。

-   アプリケーションが信頼されたソースからのものであることを確認します。

-   ラップされたアプリが格納されている出力ディレクトリをセキュリティで保護します。 出力にユーザー レベルのディレクトリを使用することを検討します。



### 関連項目
- [Microsoft Intune によるモバイル アプリケーション管理のためにアプリを準備する方法を決める](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md)

- [Use the SDK to enable apps for mobile application management (アプリでモバイル アプリケーション管理を実行できるよう SDK を使用する)](use-the-sdk-to-enable-apps-for-mobile-application-management.md)



<!--HONumber=Oct16_HO2-->


