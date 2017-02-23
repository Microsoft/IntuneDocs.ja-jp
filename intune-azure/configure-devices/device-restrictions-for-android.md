---
title: "Android 向けの Intune デバイスの制限設定 | Intune Azure プレビュー | Microsoft Docs"
description: "Intune Azure プレビュー: Android デバイスのデバイス設定と機能を制御するために使用できる Intune 設定について説明します。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/23/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6bdf714a-5d93-485c-8b52-513635c60cb6
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 74023866802eb4c13e7e9ff97e8048afe7d62409
ms.openlocfilehash: 40e04f1f8e7972bcd72cceae272d8295a496df7a


---

# <a name="android-and-samsung-knox-standard-device-restriction-settings-in-intune-azure-preview"></a>Intune Azure プレビューでの Android および Samsung KNOX Standard デバイスの制限設定

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

## <a name="general"></a>全般
-   **[カメラ]** - デバイスのカメラを使用できるようにします。
-   **[コピー/貼り付け]** - デバイスでコピー/貼り付け機能を使用できるようにします。
-   **[アプリ間のクリップボードの共有]** - クリップボードを使用してアプリ間でコピー/貼り付けを実行できるようにします (Samsung KNOX Standard のみ)。
-   **[診断データの送信]** - ユーザーがデバイスから診断データを送信できないようにします。    
-   **[工場出荷時の設定へのリセット]** - ユーザーがデバイスを出荷時の設定に戻せるようにします。
-   **[位置情報]** - デバイスで位置情報を使用できるようにします (Samsung KNOX Standard のみ)。
-   **[電源オフ]** - ユーザーがデバイスの電源を切ることを許可します。<br>この設定が無効になっている場合、Samsung KNOX Standard デバイスの **[デバイスがワイプされるまでのサインイン失敗回数]** 設定は機能しません。
-   **[画面キャプチャ]** - ユーザーが画面のコンテンツを画像としてキャプチャできるようにします。
-   **[音声アシスタント]** - デバイスで音声アシスタント ソフトウェアを使用できるようにします (Samsung KNOX Standard のみ)。
-   **[YouTube]** - デバイスで YouTube アプリを使用できるようにします (Samsung KNOX Standard のみ)。

## <a name="password"></a>パスワード
-   **[パスワードが必要です]** - エンド ユーザーがデバイスにアクセスする際にパスワードの入力を要求します。
-   **[パスワードの最小文字数]** - ユーザーが構成する必要があるパスワードの最小文字数 (4 ～ 16 文字) を入力します。
-   **[画面がロックされるまでの非アクティブな最長時間 (分)]** - デバイスの非アクティブ状態が許容される時間 (分) を指定します。この時間を超えると、デバイスは自動的にロックされます。
-   **[デバイスがワイプされるまでのサインイン失敗回数]** - デバイスをワイプするまでのサインイン エラーの数を指定します。
-   **[パスワードの有効期限 (日数)]** - デバイスのパスワードの変更が必要になるまでの日数を指定します。
-   **[必要なパスワードの種類]** - 必要なレベルのパスワードの複雑さと、生体認証デバイスを使用できるかどうかを選択します。
-   **[Prevent reuse of previous passwords (前のパスワードを再利用できないようにする)]** - エンド ユーザーが以前に使用したことのあるパスワードを作成できないようにします。
-   **[指紋によるロック解除]** - 指紋を使用して、サポートされているデバイスのロックを解除できるようにします。
-   **[Smart Lock などの信頼できるエージェント]** - 互換性のある Android デバイス (Samsung KNOX Standard 5.0 以降) で Smart Lock 機能を制御できるようにします。 信頼エージェントとも呼ばれるこの電話機能では、デバイスが信頼できる場所にある場合 (デバイスが特定の Bluetooth デバイスに接続したときや、NFC タグの近くにある場合など)、デバイスのロック画面のパスワードを無効化またはバイパスすることができます。この設定を使用して、ユーザーが SmartLock を構成することを禁止できます。
-   **[暗号化]** - デバイス上のファイルを暗号化することを要求します。

## <a name="google-play-store"></a>Google Play ストア

-   **[Google Play ストア]** - ユーザーがデバイス上で Google Play ストアにアクセスできるようにします (Samsung KNOX Standard のみ)。

## <a name="restricted-apps"></a>制限付きアプリ

制限付きアプリの一覧では、次の一覧のいずれかを構成できます。

**[禁止されているアプリ]** の一覧 - ユーザーによるインストールと実行が許可されていないアプリ (Intune で管理されていない) アプリを一覧表示します。
**[承認済みアプリ]** の一覧 - ユーザーによるインストールが許可されているアプリを一覧表示します。 準拠性を維持するため、ユーザーは一覧表示されていないアプリをインストールできません。 管理対象アプリは Intune で自動的に許可されます。
制限付きアプリの設定を含むデバイス プロファイルは、ユーザーのグループに展開する必要があります。

この一覧を構成するには、**[追加]** をクリックし、任意の名前、アプリの発行元 (省略可能)、アプリ ストアでのアプリの URL を指定します。

### <a name="how-to-specify-the-url-to-an-app-in-the-store"></a>ストアにおけるアプリの URL を指定する方法

準拠アプリと非準拠アプリの一覧でアプリの URL を指定するには、次の手順を実行します。

[Google Play の [アプリ] セクション](https://play.google.com/store/apps)で、使用するアプリを検索します。

アプリのインストール ページを開き、URL をクリップボードにコピーします。 準拠アプリおよび非準拠アプリの一覧で URL として使用できるようになります。

例: Google Play で Microsoft Office Mobile を検索します。 **https://play.google.com/store/apps/details?id=com.microsoft.office.officehub** という URL を使用します。

### <a name="additional-options"></a>追加オプション

**[インポート]** をクリックして "<*アプリ URL*>, <*アプリ名*>, <*アプリの発行元*>" 形式の csv ファイルから一覧に値を設定したり、**[エクスポート]** をクリックして、制限付きアプリの一覧の内容を含む csv ファイルを同じ形式で作成したりすることもできます。      

## <a name="browser"></a>ブラウザー
-   **[Web ブラウザー]** - デバイスの既定の Web ブラウザーを使用できるようにするかどうかを指定します。
-   **[オートフィル]** - Web ブラウザーでオートコンプリート機能を使用できるようにします。
-   **[Cookie]** - デバイスの Web ブラウザーで Cookie を使用できるようにします。
-   **[JavaScript]** - JavaScript をデバイスの Web ブラウザーで実行できるようにします。
-   **[ポップアップ]** - Web ブラウザーでポップアップ ブロックを使用できるようにします。

## <a name="cloud-and-storage"></a>クラウドとストレージ
-   **[Google バックアップ]** - Google へのバックアップを使用できるようにします。
-   **[Google アカウントの自動同期]** - Google アカウントの設定を自動的に同期できるようにします。
-   **[リムーバブル記憶域]** - デバイスで SD カードなどのリムーバブル記憶域を使用できるようにします (Samsung KNOX Standard のみ)。
-   **[メモリ カードでの暗号化]** - デバイスのメモリ カードを暗号化する必要があるかどうかを指定します。

## <a name="cellular-and-connectivity"></a>携帯ネットワークと接続性
-   **[データ ローミング]** - デバイスが移動体通信ネットワーク上にある場合はデータ ローミングを使用できるようにします (Samsung KNOX Standard のみ)。
-   **[SMS/MMS メッセージング]** - デバイスで SMS と MMS メッセージングを使用できるようにします (Samsung KNOX Standard のみ)。
-   **[音声ダイヤル]** - デバイスの音声ダイヤル機能を有効または無効にします (Samsung KNOX Standard のみ)。
-   **[音声通話ローミング]** - デバイスが移動体通信ネットワーク上にある場合は音声通話ローミングを使用できるようにします (Samsung KNOX Standard のみ)。
-   **[Bluetooth]** - デバイスで Bluetooth を使用できるようにします (Samsung KNOX Standard のみ)。
-   **[NFC]** - デバイスでサポートされている場合、近距離無線通信を使用する操作を許可します (Samsung KNOX Standard のみ)。
-   **[Wi-Fi]** - デバイスで Wi-Fi 機能を使用できるようにします (Samsung KNOX Standard のみ)。
-   **[Wi-Fi テザリング]** - デバイスで Wi-Fi テザリングを使用できるようにします (Samsung KNOX Standard のみ)。

## <a name="kiosk"></a>キオスク
-   **[Select a managed app (管理対象アプリを選択します)]** - [参照] を選択して、デバイスがキオスク モードのときに実行できる管理対象アプリを選択します (ストアへのリンクとして指定されたアプリは現在サポートされていません)。 他のアプリはデバイスでの実行が許可されません。
-   **[画面スリープ ボタン]** - デバイスの画面スリープ ウェイク ボタンを有効または無効にします。
-   **ボリューム ボタン** - デバイスのボリューム ボタンの使用を有効または無効にします。



<!--HONumber=Feb17_HO1-->


