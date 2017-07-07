---
title: "Intune でデバイスを出荷時の設定にリセットする"
titleSuffix: Intune on Azure
description: "Intune で管理するデバイスを、出荷時の設定にリセットする方法について説明します。\""
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/27/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8eff9b53-eef2-4c50-8aee-556bc49d69f2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a8862f19198295541a88c7240c448af0b75613c4
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2017
---
# <a name="reset-intune-managed-devices-to-factory-settings"></a>Intune で管理するデバイスを出荷時の設定にリセットする


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

**[工場出荷時の設定へのリセット]** では、デバイスが既定の設定に戻されます。 デバイスは Intune で管理されなくなり、会社のデータと個人データが両方とも削除されます。 この操作を取り消すことはできません。

1. Azure ポータルにサインインします。
2. **[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
3. **[Intune]** ブレードで、**[デバイス]** を選択します。
4. **[デバイスとグループ]** ブレードで、**[すべてのデバイス]** を選択します。
5. 管理するデバイスの一覧からデバイスを選択し、その後**[工場出荷時の設定へのリセット]** デバイス リモート アクションを選択します。

実行したアクションの状態を確認するには、**[デバイスとグループ]** ブレードで **[デバイス アクション]** を選択します。

