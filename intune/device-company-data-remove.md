---
title: "Intune でデバイスから会社のデータを削除する"
titleSuffix: Intune on Azure
description: "Intune で管理するデバイスから会社のデータのみを削除する方法について説明します。\""
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/27/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f021e95f-157f-4e8a-9253-1cff03d6ee3e
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 39acd12333e9685f94d23416fb1a61ce93f45476
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2017
---
# <a name="remove-company-data-from-intune-managed-devices"></a>Intune で管理するデバイスから会社のデータを削除する


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

**[会社データを削除する]** を選択すると、Intune で管理されているデバイスから会社のデータのみが削除されます。 デバイスから個人データが削除されることはありません。 デバイスは Intune で管理されなくなり、会社のリソースにはアクセスできなくなります (Azure Active Directory に参加している Windows デバイス向けにはサポートされていません)。

1. Azure ポータルにサインインします。
2. **[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
3. **[Intune]** ブレードで、**[デバイス]** を選択します。
4. **[デバイスとグループ]** ブレードで、**[すべてのデバイス]** を選択します。
5. 管理するデバイスの一覧からデバイスを選択し、その後 **[会社データを削除する]** デバイス リモート アクションを選択します。

実行したアクションの状態を確認するには、**[デバイスとグループ]** ブレードで **[デバイス アクション]** を選択します。
