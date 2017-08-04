---
title: "Windows 8.1 の Intune デバイス制限設定"
titleSuffix: Intune on Azure
description: "Windows 8.1 デバイスでデバイスの設定と機能を制御するために使用できる Intune 設定について説明します。\""
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/01/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fe5785e9-8d35-4ad7-95e8-d50f8d87154a
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 56a133105df88d0efede1dd8829285cc845d3621
ms.sourcegitcommit: 79116d4c7f11bafc7c444fc9f5af80fa0b21224e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2017
---
# <a name="windows-81-and-later-device-restriction-settings-in-microsoft-intune"></a>Microsoft Intune での Windows 8.1 以降のデバイスの制限設定

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="general"></a>全般

-   **[診断データの送信]** - デバイスが Microsoft に診断情報を送信できるようにします。
-   **[ファイアウォール]** - Windows ファイアウォールを有効にすることを要求します。
-   **[ユーザー アカウント制御]** - デバイス上のユーザー アカウント制御 (UAC) の使用を必須とします。

## <a name="password"></a>パスワード
-   **[必要なパスワードの種類]** - エンド ユーザーがデバイスにアクセスする際にパスワードの入力を要求します。
-   **[パスワードの最小文字数]** - パスワードに必要な最小の長さ (文字数) を構成します。
-   **[デバイスがワイプされるまでのサインイン失敗回数]** - サインインの試みがこの回数だけ失敗した場合は、デバイスがワイプされます。
-   **[画面がロックされるまでの非アクティブな最長時間 (分)]** - デバイスのアイドル状態が許容される時間 (分) を指定します。この時間を超えると、ロックを解除するためにパスワードが必要となります。
-   **[パスワードの有効期限 (日数)]** - デバイスのパスワードの変更が必要になるまでの日数を指定します。
-   **[Prevent reuse of previous passwords (前のパスワードを再利用できないようにする)]** - 過去に使用したパスワードをユーザーが構成できるかどうかを指定します。
-   **[ピクチャ パスワードと PIN]** - ピクチャ パスワードと PIN を使用できるようにします。 ピクチャ パスワードが許可されている場合、ユーザーは画像に対するジェスチャーでサインインすることができます。 PIN が許可されている場合、ユーザーは 4 桁のコードを使用してすばやくサインインできます。
-   **[暗号化]** - デバイス上のファイルを暗号化することを要求します。<br>Windows 8.1 が実行されているデバイスで暗号化を適用するには、 [Windows の 2014 年 12 月付け MDM クライアント更新プログラム](https://support.microsoft.com/kb/3013816) を各デバイスにインストールする必要があります。
Windows 8.1 デバイスに対してこの設定を有効にすると、デバイスのすべてのユーザーに Microsoft アカウントが必要になります。
暗号化を機能させるには、デバイスが Microsoft [InstantGo](https://blogs.windows.com/windowsexperience/2014/06/19/instantgo-a-better-way-to-sleep/#IBHULcTfI4PokO8X.97) ハードウェア認定要件を満たしている必要があります。
デバイスで暗号化を適用すると、回復キーは、ユーザーの Microsoft アカウントからしかアクセスできなくなります。また、OneDrive アカウントからアクセスする必要があります。 ユーザーの代わりにこのキーを回復することはできません。     



## <a name="browser"></a>ブラウザー
-   **[オートフィル]** - ユーザーがブラウザーのオートコンプリートの設定を変更できるようにします。
-   **[不正行為の警告]** - 詐欺目的の疑いがある Web サイトの警告を有効または無効にします。
-   **[SmartScreen]** - 詐欺目的の疑いがある Web サイトの警告を有効または無効にします。
-   **[JavaScript]** - ブラウザーで JavaScript などのスクリプトを実行できるようにします。
-   **[ポップアップ]** - ブラウザーのポップアップ ブロックを有効または無効にします。
-   **[トラッキング拒否ヘッダーを送信する]** - Internet Explorer で、訪問したサイトに Do Not Track ヘッダーを送信します。
-   **[プラグイン]** - ユーザーが Internet Explorer にプラグインを追加できるようにします。
-   **[イントラネット サイトにおける 1 単語の入力]** - Bing など、1 つの単語を使用して Internet Explorer に移動先の Web サイトを指示できるようにします。
-   **[イントラネット サイトの自動検出]** - Internet Explorer でイントラネット サイト用にセキュリティを構成できるようにします。
-   **[インターネット セキュリティ レベル]** - インターネット サイトに対する Internet Explorer のセキュリティ レベルを設定します。
-   **[Intranet security level (イントラネット セキュリティ レベル)]** - イントラネット サイトに対する Internet Explorer のセキュリティ レベルを設定します。
-   **[信頼されているサイトのセキュリティ レベル]** - 信頼済みサイト ゾーンのセキュリティ レベルを構成します。
-   **[制限付きサイトの高度なセキュリティ]** - 制限付きサイト ゾーンのセキュリティ レベルを構成します。
-   **[エンタープライズ モード メニュー アクセス]** - Internet Explorer からエンタープライズ モード メニュー オプションへのアクセスをユーザーに許可します。
この設定を選択した場合は、さらに **[ログ レポートの場所]** を指定できます。これは、エンタープライズ モード アクセスが有効にされた Web サイトの記録となるレポートの URL を表します。
-   **[エンタープライズ モードのサイト一覧の場所]** - エンタープライズ モードがアクティブな場合に使用する Web サイトの一覧の場所を指定します。

## <a name="cellular"></a>移動体通信
-   **[データ ローミング]** - デバイスが移動体通信ネットワーク上にある場合はデータ ローミングを使用できるようにします。

## <a name="cloud-and-storage"></a>クラウドとストレージ
-   **[作業フォルダーの URL]** - 作業フォルダーの URL を設定して、デバイス間でドキュメントを同期できるようにします。
-   **[Microsoft アカウントを使用せずに Windows Mail アプリにアクセスする]** - Microsoft アカウントを使用せずに Windows メール アプリケーションにアクセスできるようにします。    
