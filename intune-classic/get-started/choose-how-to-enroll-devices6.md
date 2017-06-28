---
title: "モバイル デバイスの登録方法の選択"
description: "いくつかの簡単な質問に答えることによって、Intune でモバイル デバイスを登録する方法を決定する"
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 03/27/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 40262e47-1ab4-437d-8ca5-c89b5022f91f
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: dagerrit
ms.custom: intune-classic EXPIERIMENT
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: 8fe7b2bb58655374d3e92391cd0a37aeda3062d4
ms.contentlocale: ja-jp
ms.lasthandoff: 06/08/2017


---
# <a name="choose-how-to-enroll-mobile-devices"></a>モバイル デバイスの登録方法の選択

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

次の一連の質問に答えることで、管理するデバイスの最適な登録方法が決まります。

## <a name="how-will-you-manage-dedicated-corporate-owned-devices"></a>**企業所有の専用デバイスはどのような方法で管理しますか。**

  > [!div class="button"]
[iOS DEP >](/intune-classic/deploy-use/ios-device-enrollment-program-in-microsoft-intune)  
> [!div class="button"]
[iOS のセットアップ アシスタント >](/intune-classic/deploy-use/ios-setup-assistant-enrollment-in-microsoft-intune)
> [!div class="button"]
[IMEI によるタグ付け >](/intune-classic/deploy-use/specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers)

  次のようにして、会社が所有するデバイスを専用ユーザーに登録できます。

  - **Apple のデバイス登録プログラム (DEP)** - DEP で購入し、管理している iOS デバイスが対象となります。登録プロファイルが利用されます。 利用者がデバイスの電源を初めて入れると、デバイスは DEP プロファイルをダウンロードして、Intune に登録します。

  - **Mac の Apple Configurator** - Apple Configurator は Mac PC で実行される Apple アプリケーションです。 USB ケーブルで iOS デバイスを Mac に接続し、デバイスに登録プロファイルをインストールできます。 デバイスを工場出荷時にリセットして登録できる場合、セットアップ アシスタント登録を使用します。

  - **IMEI 番号でのタグ付け** - 会社所有デバイスの IMEI (携帯機器の国際的な識別番号) をインポートすることで、Intune でデバイスに会社所有のタグを付けることができます。 これは、専用の ("シングル ユーザー" の) Windows および Android デバイスを会社所有として識別する唯一の方法です。 Apple のデバイス登録プログラムまたは Apple Configurator に登録されない iOS デバイスを、IMEI 番号でタグ付けすることもできます。 デバイスを事前宣言することで "会社" としてタグ付けした後で、ユーザーに配布できます。 その後、ユーザーがポータル サイトをインストールすることで自分のデバイスを専用デバイスとして登録し、電子メール、アプリ、データなど、会社のリソースにアクセスできます。

> [!div class="button"]
[< 戻る](choose-how-to-enroll-devices3.md)

