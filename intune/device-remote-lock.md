---
title: "管理されたデバイスを Intune でリモートからロックする"
titleSuffix: Intune on Azure
description: "Intune を使用して管理対象デバイスをリモートからロックする方法について説明します。\""
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/27/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b67f285-229d-4a0f-ae34-0402a20b4518
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5e6a372d6512c68ef7eb7df5796f91d8259d024b
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2017
---
# <a name="remotely-lock-managed-devices-with-intune"></a>管理されたデバイスを Intune でリモートからロックする


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

**リモート ロック**を使用して、選択したデバイスをロックできます。 デバイスの所有者は、ロックを解除するためにパスコードを使用する必要があります。 PIN またはパスワードが設定されているデバイスに限り、リモートでロックできます。

1. Azure ポータルにサインインします。
2. **[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
3. **[Intune]** ブレードで、**[デバイス]** を選択します。
4. **[デバイスとグループ]** ブレードで、**[すべてのデバイス]** を選択します。
5. 管理するデバイスの一覧からデバイスを選択し、その後 **[リモート ロック]** デバイス リモート アクションを選択します。

実行したアクションの状態を確認するには、**[デバイスとグループ]** ブレードで **[デバイス アクション]** を選択します。
