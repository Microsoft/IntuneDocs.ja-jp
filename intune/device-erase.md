---
title: "MacOS デバイスを消去する"
titlesuffix: Azure portal
description: "macOS デバイスからオペレーティング システムを含むすべてのデータを消去する方法を説明します。"
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/31/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ab396092-907a-44b7-a157-aabee62176a9
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 81f328004863e812b706174e74a9b74d0bdf80b6
ms.sourcegitcommit: a6fd6b3df8e96673bc2ea48a2b9bda0cf0a875ae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="erase-all-data-from-a-macos-device"></a>MacOS デバイスからすべてのデータを消去する

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

macOS デバイスから、オペレーティング システムを含むすべてのデータを消去することができます。 デバイスは Intune の管理からも削除されます。 エンド ユーザーに警告は表示されません。

1. [Azure Portal の Intune](https://aka.ms/intuneportal) で、**[デバイス]** > **[すべてのデバイス]** の順に選び、消去するデバイスを選びます。
![スクリーンショット](./media/device-erase/choosedevice.png)
2. **[その他]** > **[消去]** の順にクリックし、**[Recovery Pin]\(回復用 PIN\)** に 6 桁の数字を入力します。 これは、ユーザーが自分のデバイスにオペレーティング システムを再インストールできるようにユーザーに与える必要がある PIN です。 この PIN は、消去操作が完了した後では表示できないので、必ず書き留めておいてください。
![スクリーンショット](./media/device-erase/providepin.png)
3. **[OK]** をクリックしてデバイスを消去します。
