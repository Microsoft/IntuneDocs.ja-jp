---
title: "ポータル サイト Web サイトからデバイスをリモートでロックする | Microsoft Intune"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 09/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: adc6af23-b22f-42e5-955a-4dffbdb8b42b
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mamoriss
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9ddbcde20fac83289c4622f69538ff00fa0cb65b
ms.openlocfilehash: 31b3f4c556c27de7a1793bfe84a1d3eb12302424


---


# <a name="remotely-lock-a-device-from-the-company-portal-website"></a>ポータル サイト Web サイトからデバイスをリモートでロックする

デバイスを紛失した、またはデバイスが盗難にあった場合、[ポータル サイト Web サイト](http://portal.manage.microsoft.com)のリモート ロック オプションを使用してデバイスをロックすることができます。 リモート ロックは、次の種類のデバイスで機能します。

プラットフォーム  |サポートの詳細  
---------|---------
Android | サポート       
iOS | サポート
[Windows] 10 Mobile | 電話でパスコードが設定されている場合のみサポート     
[Windows] 10 Desktop | サポートされていません  
Windows Phone 8。1 | 電話でパスコードが設定されている場合のみサポート
PC (Windows 8.0 以前) | サポートされていません       
PC (Windows 8.1) | サポートされていません

</br>
リモート ロックを使用してデバイスをロックするには:

1.  [ポータル サイト Web サイト](http://portal.manage.microsoft.com)で、ロックするデバイスの名前をタップします。

2.  **[リモート ロック]** をタップします。

    ![remote-lock-option-on-company-portal-website](./media/iwp-screen-with-all-options.png)

3.  デバイスをロックしようとしていることを示す警告メッセージを確認した後、**[リモート ロック]** をタップすると、ポータル Web サイトがデバイスのロックを試みます。

    **[リモート ロック]** をタップすると、“リモート ロック保留中“ 状態が表示されます。  リモート ロックが成功した場合、状態が ”リモート ロック成功” に変わります。

    リモート ロックの状態は次の 3 つの場所に表示されます。

    * Web サイトの通知領域。
    * デバイスの [詳細] ページ。
    * ページの [デバイス] セクションのデバイス名を表示するタイル。

    ”リモート ロックに失敗しました” の通知が表示される場合は、数分待ってから、もう一度デバイスのロックを試みてください。 タップして再試行すると、状態が ”リモート ロック保留中” に戻ります。

    再試行できない場合は、IT 管理者に問い合わせてください。 デバイスが見つかった場合は、パスコードを入力するだけでリモート ロックしたデバイスのロックを解除できます。

サポートが必要な場合は、 IT 管理者にお問い合わせください。 連絡先情報については、[ポータル サイト Web サイト](http://portal.manage.microsoft.com)をご確認ください。




<!--HONumber=Nov16_HO1-->


