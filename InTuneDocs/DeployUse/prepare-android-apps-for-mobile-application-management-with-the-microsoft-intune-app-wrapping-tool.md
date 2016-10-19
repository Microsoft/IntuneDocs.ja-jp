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
ms.sourcegitcommit: 45c6622624230e3486d2498b1b023f2efcdc2970
ms.openlocfilehash: ea1a6ef60b6a9cdd64559f67276280a4f491e30e


---

# Intune アプリ ラッピング ツールでモバイル アプリケーションを管理するために Android アプリを準備する
**Android 用 Microsoft Intune アプリ ラッピング ツール**を使用して社内 Android アプリの動作を変更すると、アプリ自体のコードを変更しなくてもアプリの機能を構成できます。

このツールは、PowerShell で実行される Windows のコマンドライン アプリケーションであり、アプリの "ラッパー" を作成します。 アプリが処理されたら、ユーザーが構成する[モバイル アプリケーション管理ポリシー](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md)を利用してアプリの機能を変更できます。


このツールを実行する前に、「[アプリ ラッピング ツールを実行するうえでのセキュリティ上の考慮事項](#security-considerations-for-running-the-app-wrapping-tool)」を確認してください。 このツールをダウンロードするには、「[Android 用 Microsoft Intune アプリ ラッピング ツール](https://www.microsoft.com/download/details.aspx?id=47267)」を参照してください。

>[!IMPORTANT]
>Intune に登録されていないデバイスをサポートするこのアプリ ラッピング ツールのバージョンは、パブリック プレビューで提供されています。 パブリック プレビューへの参加を希望する場合、Android 向けについては[この GitHub サイト](https://github.com/msintuneappsdk/intune-app-wrapper-android-preview)からツールをダウンロードします。

シナリオについては、「[Microsoft Intune に登録されていないデバイスの基幹業務アプリとデータを保護する](protect-line-of-business-apps-and-data-on-devices-not-enrolled-in-microsoft-intune.md)」トピックに説明されています。


## 手順 1: アプリ ラッピング ツールを使用するための前提条件を満たす

-   Windows 7 以降を実行している Windows コンピューターでアプリ ラッピング ツールを実行する必要があります。

-   入力アプリは、拡張子が **.apk** のファイルを備えた有効な Android アプリケーション パッケージであると同時に、次の要件を満たしている必要があります。

    -   暗号化できない

    -   アプリ ラッピング ツールでまだラップされていない

    -   Android 4.0 以降を対象に記述されている

-   このアプリは、自社で開発されているか、自社向けに開発されている必要があります。 このツールを使用して、Google Play ストアからダウンロードしたアプリを処理することはできません。

-   アプリ ラッピング ツールを実行するには、最新バージョンの [Java ランタイム環境](http://java.com/download/)をインストールし、Java の path 変数がWindows 環境変数で **C:\ProgramData\Oracle\Java\javapath** に設定されている必要があります。 詳細については、 [Java のドキュメント](http://java.com/download/help/)を参照してください。

    > [!NOTE]
    > 場合によっては、32 ビット バージョンの Java を使用すると、メモリに関連した問題が発生する可能性があります。 代わりに、64 ビット バージョンをインストールすることをお勧めします。

## 手順2: アプリ ラッピング ツールをインストールする

1.  Microsoft ダウンロード センターからアプリ ラッピング ツールのインストール ファイルを Windows コンピューターにダウンロードして開きます。

2.  ライセンス条項に同意し、インストールを完了します。

このツールをインストールしたフォルダーをメモしておきます。 既定の場所は、**C:\Program Files (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool** です。

## 手順 3: アプリ ラッピング ツールを実行する

1.  アプリ ラッピング ツールをインストールした Windows コンピューターで、管理者モードで PowerShell ウィンドウを開きます。

2.  ツールをインストールしたフォルダーから、アプリ ラッピング ツールの PowerShell モジュールをインポートします。

    ```
    Import-Module .\IntuneAppWrappingTool.psm1
    ```

3.  **invoke-AppWrappingTool** コマンドを次のパラメーターと共に使用してツールを実行します。

|パラメーター|詳細情報|例|
|-------------|--------------------|---------|
|**-InputPath**&lt;String&gt;|ソースの Android アプリ (.apk) のパス。| |
|**-OutputPath**&lt;String&gt;|"出力先" の Android のアプリへのパス。 InputPath と同じディレクトリ パスを指定した場合、パッケージ化は失敗します。| |
|**-KeyStorePath**&lt;String&gt;|署名用の公開/秘密キーのペアを含むキーストア ファイルへのパス。| |
|**-KeyStorePassword**&lt;SecureString&gt;|キーストアの暗号化を解除するために使用するパスワード。 Android では、すべてのアプリケーション パッケージ (.apk) に署名する必要があります。 Java キー ツールを使用すると、この例のように、KeyStorePassword を生成できます。 詳細については、「[keystore](https://docs.oracle.com/javase/7/docs/api/java/security/KeyStore.html)」をご覧ください。|keytool.exe -genkey -v -keystore keystorefile -alias ks -keyalg RSA -keysize 2048 -validity 50000 |
|**-KeyAlias**&lt;String&gt;|署名に使用するキーの名前。| |
|**-KeyPassword**&lt;SecureString&gt;|署名に使用する秘密キーの暗号化を解除するために使用するパスワード。| |
|**-SigAlg**&lt;SecureString&gt;|署名に使用する署名アルゴリズムの名前。 アルゴリズムは秘密キーと互換性を持つ必要があります。|例: SHA256withRSA、SHA1withRSA、MD5withRSA|


**&lt;CommonParameters&gt;**
    (省略可能 – verbose、debug などの一般的な PowerShell パラメーターをサポートします)。

- 共通パラメーターの一覧については、 [Microsoft スクリプト センター](https://technet.microsoft.com/library/hh847884.aspx)を参照してください。

- ツールのヘルプを表示するには、次のコマンドを入力します。

    ```
    Help Invoke-AppWrappingTool
    ```

**例:**


    Import-Module "C:\Program Files (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool\IntuneAppWrappingTool.psm1"
    invoke-AppWrappingTool -InputPath .\app\HelloWorld.apk -OutputPath .\app.wrapped\HelloWorld_wrapped2.apk -KeyStorePath "C:\Program Files (x86)\Java\jre1.8.0_91\bin\keystorefile" -keyAlias ks -SigAlg SHA1withRSA -Verbose

**KeyStorePassword** と **KeyPassword**の入力を求められます。

ラップされたアプリは、指定した出力パスにログ ファイルと共に生成されて保存されます。

## アプリ ラッピング ツールを実行するうえでのセキュリティ上の考慮事項
スプーフィング、情報漏えい、および権限の昇格攻撃の可能性を抑制するには、次の手順に従います。

-   入力基幹業務アプリケーション、出力アプリケーション、Java KeyStore がアプリ ラッピング ツールを実行しているのと同じコンピューターに存在することを確認します。

-   このツールを実行しているのと同じコンピューター上の Intune コンソールに出力アプリケーションをインポートします。 Java の keytool の詳細については、「[keytool](https://docs.oracle.com/javase/8/docs/technotes/tools/unix/keytool.html)」を参照してください。

-   出力アプリケーションとツールが汎用名前付け規則 (UNC) パスにあり、ツールと入力ファイルを同じコンピューター上で実行していない場合、 [インターネット プロトコル セキュリティ (IPsec)](http://en.wikipedia.org/wiki/IPsec) または [サーバー メッセージ ブロック (SMB) 署名](https://support.microsoft.com/en-us/kb/887429)を使用して環境をセキュリティで保護します。

-   実行時にアプリケーションから AAD トークンにアクセスできる可能性がある場合は、そのアプリケーションが信頼されたソースから入手されていることを確認します。

-   ラップされたアプリが格納されている出力ディレクトリをセキュリティで保護します。 出力にユーザー レベルのディレクトリを使用することを検討します。



### 関連項目
- [Microsoft Intune によるモバイル アプリケーション管理のためにアプリを準備する方法を決める](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md)

- [Use the SDK to enable apps for mobile application management (アプリでモバイル アプリケーション管理を実行できるよう SDK を使用する)](use-the-sdk-to-enable-apps-for-mobile-application-management.md)



<!--HONumber=Sep16_HO2-->


