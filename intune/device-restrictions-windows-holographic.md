---
title: "Windows Holographic for Business の Intune デバイス制限設定"
titlesuffix: Azure portal
description: "Windows Holographic for Business デバイスでデバイスの設定と機能を制御するために使用できる Intune 設定について説明します。"
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 1/19/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 300ddb15f2d7b8f2fc6ab4a0e9e32852e0604e0a
ms.sourcegitcommit: 93622d740cbd12043eedc25a9699cc4256e23e7e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2018
---
# <a name="windows-holographic-for-business-device-restriction-settings-in-microsoft-intune"></a>Microsoft Intune での Windows Holographic for Business デバイスの制限設定

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Microsoft Hololens など、Windows Holographic for Business を実行しているデバイスでは、以下のデバイス制限設定がサポートされます。

## <a name="general"></a>全般

- **[手動での登録解除]** - ユーザーがデバイスから会社アカウントを手動で削除できるようにします。
- **[Cortana]** - Cortana による音声アシスタントを有効または無効にします。
- **[位置情報]** - デバイスが位置情報サービスの情報を使用できるかどうかを指定します。



## <a name="password"></a>パスワード
-   **[パスワード]** - エンド ユーザーがデバイスにアクセスする際にパスワードの入力を要求します。
    -   **[デバイスがアイドル状態から戻るときにパスワードを必須にする]** - ユーザーがデバイスのロックを解除するときにパスワードの入力を必須にします。



## <a name="app-store"></a>アプリ ストア

-   **[アプリ ストア]** - デバイスでのアプリ ストアの使用を有効にするかブロックします。
-   **[ストア アプリの自動更新]** - Microsoft ストアからインストールされたアプリの自動更新を許可します。
-   **[信頼できるアプリのインストール]** - 信頼済み証明書で署名されたアプリのサイドロードを許可します。
-   **[開発者によるロック解除]** - サイドロードしたアプリのエンド ユーザーによる変更を許可するなど、Windows 開発者の設定を許可します。

## <a name="edge-browser"></a>Microsoft Edge ブラウザー

-   **[Microsoft Edge ブラウザー]** - デバイスで Edge Web ブラウザーを使用できるようにします。
-   **[Cookie]** - ブラウザーがインターネット Cookie をデバイスに保存するように設定します。
-   **[ポップアップ]** - ブラウザー内のポップアップ ウィンドウをブロックします (Windows 10 デスクトップのみに適用)。
-   **[検索候補]** - 検索語句を入力したときに、検索エンジンからサイトが提案されるようになります。
-   **[パスワード マネージャー]** - Microsoft Edge Password Manager 機能を有効または無効にします。
- **[トラッキング拒否ヘッダーを送信する]** - ユーザーがアクセスする Web サイトに Do Not Track ヘッダーを送信するように、Microsoft Edge ブラウザーを構成します。

## <a name="windows-defender-smart-screen"></a>Windows Defender SmartScreen

- **[SmartScreen for Microsoft Edge]** - サイトへのアクセスとファイルのダウンロードに対して Edge の SmartScreen を有効にします。

## <a name="search"></a>検索
- **[Search location]\(場所の検索\)** - 検索で場所を使用できるかどうかを指定します。 情報


## <a name="cloud-and-storage"></a>クラウドとストレージ
-   **[Microsoft アカウント]** - ユーザーがデバイスに Microsoft アカウントを関連付けられるようにします。

## <a name="cellular-and-connectivity"></a>携帯ネットワークと接続性

-   **[Bluetooth]** - ユーザーがデバイスの Bluetooth を有効にして構成できるようにするかどうかを制御します。
-   **[Bluetooth の検出可能性]** - その他の Bluetooth 対応デバイスにより、デバイスが検出されるようにします。
-   **[Bluetooth 広告]** - デバイスが Bluetooth 経由で広告を受信できるようにします。

## <a name="control-panel-and-settings"></a>コントロール パネルと設定

- **[システム時刻の変更]** - エンド ユーザーがデバイスの日付と時刻を変更することを防止します。

## <a name="reporting-and-telemetry"></a>レポートとテレメトリ

- **[使用状況データの共有]** - 診断データの送信レベルを選択します。