---
title: Microsoft Intune で Windows 10 デバイスをリセットする - Azure | Microsoft Docs
description: Microsoft Intune を使用して、Windows 10 PC 上のアプリを削除またはアンインストールするには、[新たに開始] を使用します。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5aa5cfa3-c483-4099-b40f-578ff8dca425
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5658bf2e1ee250ef9fd405b3f7ec1772b166f338
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31020998"
---
# <a name="use-fresh-start-to-reset-windows-10-devices-with-intune"></a>[新たに開始] を使用して Intune が稼働する Windows 10 デバイスをリセットする


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

**[新たに開始]** デバイス アクションは、Creators Update を実行している Windows 10 PC にインストールされているすべてのアプリを削除します。 次に、最新バージョンの Windows に自動的に PC を更新します。

この操作は、一般的に新しい PC にプレインストールされている (OEM) アプリケーションを削除するために役立ちます。 ユーザーのホーム フォルダーの内容を保持し、アプリと設定のみを削除するには、`if user data is retained` 設定を使用します。

> [!IMPORTANT]
> [新たに開始] は、Intune からデバイスを登録解除しますが、デバイスは Azure Active Directory にまだ参加しています。

## <a name="use-fresh-start"></a>新たに開始

1. [Azure ポータル](https://portal.azure.com)にサインインします。
2. **[すべてのサービス]** を選択し、**[Intune]** をフィルターとして適用し、**[Microsoft Intune]** を選択します。
3. **[デバイス]**、**[すべてのデバイス]** の順に選択します。
4. 管理するデバイスの一覧から Windows 10 デスクトップ デバイスを選択し、その後 **[新たに開始]** を選択します。

## <a name="next-steps"></a>次の手順

このアクションのステータスを表示するには、**[デバイス アクション]** を選択します (**Microsoft Intune** > **デバイス**)。