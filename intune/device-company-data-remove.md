---
title: "Intune でデバイスから会社のデータを削除する"
titleSuffix: Intune on Azure
description: "Intune で管理するデバイスから会社のデータのみを削除する方法について説明します。\""
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f021e95f-157f-4e8a-9253-1cff03d6ee3e
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8074d6e7cc0a061a6708f8c8bfae1a4dfcb6daa3
ms.sourcegitcommit: 10e3ab2aeb79a1fb2243bef2748ccc003fdd4cc7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2017
---
# <a name="remove-company-data-from-intune-managed-devices"></a>Intune で管理するデバイスから会社のデータを削除する


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

**[会社データを削除する]** のデバイス操作を選択すると、Intune で管理されているデバイスから会社のデータのみが削除されます。 この操作によってデバイスから個人データが削除されることはありません。 削除後、デバイスは Intune の管理の対象ではなくなり、企業リソースにアクセスすることはできなくなります。

## <a name="supported-platforms"></a>サポートされているプラットフォーム

- Windows - サポートされています (Azure Active Directory に参加している Windows デバイスではサポートされません)
- Windows Phone - サポートされています
- iOS - サポートされています
- macOS - サポートされています
- Android - サポートされています

## <a name="how-to-remove-company-data"></a>会社のデータを削除する方法

1. Azure ポータルにサインインします。
2. **[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
3. **[Intune]** ブレードで、**[デバイス]** を選択します。
4. **[デバイスとグループ]** ブレードで、**[すべてのデバイス]** を選択します。
5. 管理するデバイスの一覧からデバイスを選択し、その後 **[会社データを削除する]** デバイス リモート アクションを選択します。

## <a name="next-steps"></a>次のステップ

実行したアクションの状態を確認するには、**[デバイスとグループ]** ブレードで **[デバイス アクション]** を選択します。
