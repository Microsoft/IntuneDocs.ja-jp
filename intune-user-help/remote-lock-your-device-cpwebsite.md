---
title: "ポータル サイトからデバイスをロックする | Microsoft Docs"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: adc6af23-b22f-42e5-955a-4dffbdb8b42b
searchScope: User help
ROBOTS: 
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: f5c2536e4566baa2661b77f5574085410784a787
ms.sourcegitcommit: f2f147a1177d1cf5bbc8001701eb8f44dd833b7d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/12/2017
---
# <a name="remotely-lock-your-device-from-the-company-portal-website"></a>ポータル サイト Web サイトからデバイスをリモートでロックする

不測の事態が起こり、デバイスをなくしてしまうことがあります。 デバイスをなくした、または盗まれた場合、そのデバイスがどこにあろうと、最初に心配することは、おそらく、デバイスに入っている情報を他人に見られることでしょう。

[!INCLUDE[wit_nextref](includes/end-user-password-guidance.md)]

[ポータル サイト Web サイト](https://portal.manage.microsoft.com#HelpDeskDialog)のリモート ロック オプションを利用すれば、安全のためにデバイスをロックできます。 リモート ロックの対象 OS:

* Android
* iOS
* macOS
* Windows 10 Mobile (デバイスにパスコードが設定されている場合)
* Windows Phone 8.1 (デバイスにパスコードが設定されている場合)

## <a name="to-use-remote-lock-to-lock-your-device"></a>リモート ロックを使用してデバイスをロックするには

1.  [ポータル Web サイト](https://portal.manage.microsoft.com#HelpDeskDialog)で、__メニュー__ ボタン ![3 つの横棒が並行に積み上げられている、メニュー ボタンの小さな画像](/Intune/whats-new/media/CP_hamburger_menu.png) をタップしてから、__[デバイス]__ を選択します。

  ![[ホーム]、[すべてのアプリ]、[デバイス]、[ヘルプデスク]、[サインアウト] の各ボタンが示され、画面の左側にサイド メニューが展開されたポータル Web サイトのイメージ。](/media/iwp-expanded-sidebar.png)

2. __[デバイス]__ ページで、ロックするデバイスの名前を選択します。

  ![リスト表示されていないデバイスの登録または不明なデバイスの識別を求めるバナーの上に 2 つの不明なデバイスが示された、[デバイス] ページのスクリーンショット。](./media/macOS_enroll_002_tap_here_banner.png)

3.  デバイスがポップアップ ウィンドウに開きます。 **[リモート ロック]** ボタンをタップします。

    ![[名前の変更]、[削除]、[デバイスのリセット]、[パスコードのリセット]、[リモート ロック] を含む、ポータル Web サイト上の選択されたデバイスに対するすべてのオプション。 ](./media/iwp-screen-with-all-options.png)

4.  デバイスをロックしようとしていることを伝える警告が画面に表示されます。 **[リモート ロック]** をタップすると、ポータル サイト Web サイトはデバイスのロックを試行します。

    **[リモート ロック]** を選択すると、"リモート ロック保留中" というメッセージが表示されます。  リモート ロックが成功した場合、状態が ”リモート ロック成功” に変わります。

    リモート ロックの状態は次の 3 つの場所に表示されます。

    * Web サイトの通知領域。
    * デバイスの **[詳細]** ページ。
    * ページの **[デバイス]** セクションのデバイス名を表示するタイル。

> [!Note]
> "リモート ロックに失敗しました" の通知が表示される場合は、数分待ってから、もう一度デバイスのロックを試みてください。 再試行を開始すると、状態が "リモート ロック保留中" に戻ります。 再試行でもロックできない場合、会社のサポートの支援を求めてください。

デバイスが見つかった場合は、パスコードを入力するだけでリモート ロックしたデバイスのロックを解除できます。

サポートが必要な場合は、 社内サポートに問い合わせてください。 連絡先情報については、[ポータル サイト Web サイト](https://portal.manage.microsoft.com#HelpDeskDialog)をご確認ください。
