---
title: Unenroll your device from Intune if you declined "Terms of Use" | Microsoft Intune
description: "利用規約を拒否し、ポータル サイト アプリにサインインできない場合に、Android デバイスを Intune から登録解除する方法について説明します。"
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4278f000-0258-4de5-93a1-195b48e5061e
ms.reviewer: chrisbal
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 0d32aa982cf9d45da36f71be5554f31375521e35
ms.openlocfilehash: 4f5088bc645fed0451885078f5ab0dcd04a33d81


---


# "利用規約" を拒否した場合に Intune からデバイスの登録を解除する

Android デバイスの登録を解除する方法として最も良いのは、利用規約を受け入れ、ポータル サイト アプリにサインインしてから、[こちらの手順](unenroll-your-device-from-intune-android.md)を使用して登録を解除する方法です。 ただし、ポータル サイト アプリへのサインインの試行中に利用規約を拒否した場合は、次回以降、ポータル サイト アプリにサインインできなくなります。 その場合は、"回避策" の手順を使用してデバイス登録を解除する必要があります。

ポータル サイト アプリをアンインストールすると、Intune からそのデバイスの登録も解除されます。 デバイスは会社のリソースにアクセスできなくなります。 登録解除した場合の詳細については、「[Intune からデバイスの登録を解除するとどうなるか](what-happens-if-you-unenroll-your-device-from-intune-android.md)」を参照してください。

会社のポータル アプリをアンインストールするには、最初に **[Device administrators]** 設定に進み、**[会社のポータル]** をオフにします。 使用している Android デバイスによっては、手順が多少異なる場合があります。

Intune からデバイスの登録を解除し、会社のポータル アプリをアンインストールするには

1.  **[設定]** &gt; **[セキュリティ &amp; 画面のロック]** &gt;**[デバイス管理者]** の順に進みます。

    この手順は、デバイスの登録を解除したらすぐに実行します。

2.  **[会社のポータル]** の横のチェック ボックスの選択を解除 (オフに) します。

    これで、会社のポータル アプリをアンインストールできます。

サポートが必要な場合は、 IT 管理者に問い合わせるか (連絡先情報については[ポータル サイト Web サイト](http://portal.manage.microsoft.com)をご確認ください)、または Microsoft Android チーム (wintunedroidfbk@microsoft.com) にご連絡ください。



<!--HONumber=Oct16_HO2-->


