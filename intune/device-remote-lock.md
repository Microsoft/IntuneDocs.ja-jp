---
title: "管理されたデバイスを Intune でリモートからロックする"
titlesuffix: Azure portal
description: "Intune を使用して管理対象デバイスをリモートからロックする方法について説明します。\""
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b67f285-229d-4a0f-ae34-0402a20b4518
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 585c9ba232f8a1d9c7bb529d6d260165c2d0883d
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2017
---
# <a name="remotely-lock-managed-devices-with-intune"></a>管理されたデバイスを Intune でリモートからロックする


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

**リモート ロック**を使用して、選択したデバイスをロックできます。 デバイスの所有者は、ロックを解除するためにパスコードを使用する必要があります。 PIN またはパスワードが設定されているデバイスに限り、リモートでロックできます。

## <a name="supported-platforms"></a>サポートされているプラットフォーム

- Windows - サポートされていません
- Windows Phone - Windows Phone 8.1 以降でサポートされています
- iOS - サポートされています
- macOS - サポートされていません
- Android - サポートされています

## <a name="how-to-remote-lock-a-device"></a>デバイスをリモート ロックする方法

1. Azure ポータルにサインインします。
2. **[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
3. **[Intune]** ブレードで、**[デバイス]** を選択します。
4. **[デバイスとグループ]** ブレードで、**[すべてのデバイス]** を選択します。
5. 管理するデバイスの一覧からデバイスを選択し、その後 **[リモート ロック]** デバイス リモート アクションを選択します。

## <a name="next-steps"></a>次のステップ

実行したアクションの状態を確認するには、**[デバイスとグループ]** ブレードで **[デバイス アクション]** を選択します。
