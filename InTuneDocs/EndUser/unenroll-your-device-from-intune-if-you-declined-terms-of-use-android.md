---
title: "利用規約を拒否した場合に Intune からデバイスの登録を解除する | Microsoft Intune"
description: 
keywords: 
author: staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4278f000-0258-4de5-93a1-195b48e5061e
ms.reviewer: chrisbal
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e52ebdd62ca68f1d9226def654961075400184a8
ms.openlocfilehash: abcb7dbe4f3423fcba108a7ea0c4b2efa295c970


---


# 利用規約を拒否した場合に Intune からデバイスの登録を解除する

Android デバイスの登録を解除する方法として最も良いのは、利用規約を受け入れ、ポータル サイト アプリにサインインしてから、[こちらの手順](unenroll-your-device-from-intune-android.md)を使用して登録を解除する方法です。 ただし、ポータル サイト アプリへのサインインの試行中に利用規約を拒否した場合は、次回以降、ポータル サイト アプリにサインインできなくなるため、デバイスの登録を解除するときは次の "回避策" の手順を実施する必要があります。

会社のポータル アプリをアンインストールする場合は、Intune からもデバイスの登録を解除するため、デバイスから会社のリソースにはアクセスできなくなります。  登録解除した場合の詳細については、「[Intune からデバイスの登録を解除するとどうなるか](what-happens-if-you-unenroll-your-device-from-intune-android.md)」を参照してください。

会社のポータル アプリをアンインストールするには、最初に **[Device administrators]** 設定に進み、**[会社のポータル]** をオフにします。 使用している Android デバイスによっては、手順が多少異なる場合があります。

Intune からデバイスの登録を解除し、会社のポータル アプリをアンインストールするには

1.  **[設定]** &gt; **[セキュリティ &amp; 画面のロック]** &gt;**[デバイス管理者]** の順に進みます。

    この手順は、デバイスの登録を解除したらすぐに実行します。

2.  **[会社のポータル]** の横のチェック ボックスをクリアして、オフにします。

    これで、会社のポータル アプリをアンインストールできます。

サポートが必要な場合は、 IT 管理者にお問い合わせください。 連絡先情報については、[ポータル サイト Web サイト](http://portal.manage.microsoft.com)をご確認ください。

### 関連項目
[Android デバイスを Intune で使用する](using-your-android-device-with-intune.md)


<!--HONumber=Jun16_HO4-->


