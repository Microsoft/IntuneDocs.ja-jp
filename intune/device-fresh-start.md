---
title: "Intune が稼働する Windows 10 デバイスのリセット"
titlesuffix: Azure portal
description: "[新たに開始] を使用して、Intune が稼働する Windows 10 PC をリセットする方法について説明します。\""
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 08/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5aa5cfa3-c483-4099-b40f-578ff8dca425
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c45d3e47c90ca7739b3aa6eee1bf31d787a82264
ms.sourcegitcommit: eac89306d1391a6d3ae1179612b0820b19c2baa6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/23/2018
---
# <a name="use-fresh-start-to-reset-windows-10-devices-with-intune"></a>[新たに開始] を使用して Intune が稼働する Windows 10 デバイスをリセットする


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

**[新たに開始]** デバイス アクションを実行すると、Creators Update が稼働する Windows 10 PC にインストールされているすべてのアプリが削除され、PC が Windows の最新バージョンに自動的に更新されます。
この操作は、新しい PC に付属することの多い事前インストール済み (OEM) アプリを削除するのに使うことができます。 このデバイス アクションを発行するときにユーザー データを保持するかどうかを構成できます。 この場合、アプリと設定は削除されますが、ユーザーのホーム フォルダーの内容は保持されます。

## <a name="how-to-use-fresh-start"></a>新たに開始の使用方法

1. サインイン、 [Azure ポータル](https://portal.azure.com)します。
2. **[すべてのサービス]** > **[Intune]** の順に選択します。 Intune は **[監視 + 管理]** セクションにあります。
3. **[Intune]** ウィンドウで、**[デバイス]** を選択します。
4. **[デバイス]** ウィンドウで、**[すべてのデバイス]** を選択します。
5. 管理するデバイスの一覧から Windows 10 デスクトップ デバイスを選択し、その後 **[新たに開始]** デバイス リモート アクションを選択します。

## <a name="next-steps"></a>次の手順

実行したアクションの状態を確認するには、**[デバイス]** ウィンドウで **[デバイス アクション]** を選択します。

