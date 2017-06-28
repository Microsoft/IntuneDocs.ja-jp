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
ms.assetid: ed9250aa-e894-4eac-92b8-5f1a3748e255
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: dagerrit
ms.custom: intune-classic EXPIERIMENT
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: e978a9df5d0c0e2e94f484c5e683a970f66dc945
ms.contentlocale: ja-jp
ms.lasthandoff: 06/08/2017


---
# <a name="choose-how-to-enroll-mobile-devices"></a>モバイル デバイスの登録方法の選択

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

次の一連の質問に答えることで、管理するデバイスの最適な登録方法が決まります。

## <a name="how-will-you-manage-shared-ios-devices"></a>**共有 iOS デバイスはどのような方法で管理しますか。**

> [!div class="button"]
[iOS の DEP 登録 >](/intune-classic/deploy-use/ios-device-enrollment-program-in-microsoft-intune)
> [!div class="button"]
[iOS の直接登録 >](/intune-classic/deploy-use/ios-direct-enrollment-in-microsoft-intune)
> [!div class="button"]
[DEM 登録 >](/intune-classic/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune)

  - **Apple のデバイス登録プログラム (DEP)** - DEP で購入し、管理している iOS デバイスが対象となります。登録プロファイルが利用されます。 利用者がデバイスの電源を初めて入れると、デバイスが DEP プロファイルをダウンロードし、プロファイル DEP で登録します。

  - **Mac の Apple Configurator** - Apple Configurator は Mac PC で実行される Apple アプリケーションです。 USB ケーブルで iOS デバイスを Mac に接続し、デバイスに登録プロファイルをインストールできます。 デバイスを工場出荷時にリセットして登録できる場合、セットアップ アシスタント登録を使用します。 デバイスを工場出荷時にリセットしない場合、直接登録を使用します。

  - **デバイス登録マネージャー** - Intune のデバイス登録マネージャー (DEM) を使用して、管理者は 1 つのユーザー アカウントに多数のモバイル デバイスを登録できます。 これらのデバイスは、ユーザー アフィニティ (つまり専用ユーザー) を持つことはできず、ポータル サイト アプリをインストールしてサインインすることで登録する必要があります。

> [!div class="button"]
[< 戻る](choose-how-to-enroll-devices3.md)

