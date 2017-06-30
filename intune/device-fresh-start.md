---
title: "Intune が稼働する Windows 10 デバイスのリセット"
titleSuffix: Intune on Azure
description: "[新たに開始] を使用して、Intune が稼働する Windows 10 PC をリセットする方法について説明します。&quot;"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/27/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5aa5cfa3-c483-4099-b40f-578ff8dca425
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: 590472c0ab9f0103d72730b8ab01dc324c852a7a
ms.contentlocale: ja-jp
ms.lasthandoff: 06/08/2017


---

# <a name="use-fresh-start-to-reset-windows-10-devices-with-intune"></a>[新たに開始] を使用して Intune が稼働する Windows 10 デバイスをリセットする


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

**[新たに開始]** デバイス アクションを実行すると、Creators Update が稼働する Windows 10 PC にインストールされているすべてのアプリが削除され、PC が Windows の最新バージョンに自動的に更新されます。
この機能は、新しい PC に付属することの多い事前インストール済み (OEM) アプリを削除するのに使うことができます。 このデバイス アクションを発行するときにユーザー データを保持するかどうかを構成できます。 この場合、アプリと設定は削除されますが、ユーザーのホーム フォルダーの内容は保持されます。

1. Azure ポータルにサインインします。
2. **[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
3. **[Intune]** ブレードで、**[デバイス]** を選択します。
4. **[デバイスとグループ]** ブレードで、**[すべてのデバイス]** を選択します。
5. 管理するデバイスの一覧から Windows 10 デスクトップ デバイスを選択し、その後 **[新たに開始]** デバイス リモート アクションを選択します。

実行したアクションの状態を確認するには、**[デバイスとグループ]** ブレードで **[デバイス アクション]** を選択します。


