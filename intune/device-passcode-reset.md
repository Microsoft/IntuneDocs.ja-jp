---
title: "Microsoft Intune でデバイス パスコードをリセットする - Azure | Microsoft Docs"
description: "Intune で管理または監視しているデバイスに [パスコード コードの削除] アクションを使用してパスコードを削除またはリセットします。"
keywords: 
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/06/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 47181d19-4049-4c7a-a8de-422206c4027e
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8f23a79bbe72d12750ef642226aefd1e11dcac24
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2018
---
# <a name="reset-or-remove-a-device-passcode-in-intune"></a>Intune でデバイスのパスコードをリセットまたは削除する

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

デバイス用に新しいパスコードを作成するには、**[パスコードの削除]** アクションを使用します。

## <a name="supported-platforms"></a>サポートされているプラットフォーム

- Windows Phone 8.1 から Azure AD に参加していない Windows 10 Creators Update まで、および Windows 10 Creators Update 以降
- iOS
- Android 7 より前の Android バージョン

次のシステムについては、この機能はサポート**されません**。

- Windows
- macOS
- Android for Work

## <a name="reset-a-passcode"></a>パスコードのリセット

1. [Azure ポータル](https://portal.azure.com)にサインインします。
2. **[すべてのサービス]** を選択し、**[Intune]** をフィルターとして適用し、**[Microsoft Intune]** を選択します。
3. **[デバイス]**、**[すべてのデバイス]** の順に選択します。
4. 管理するデバイスの一覧からデバイスを選択し、**[詳細]**、**[パスコードの削除]** デバイス リモート アクションの順に選択します。

## <a name="next-steps"></a>次の手順

実行したアクションの状態を確認するには、**[デバイス]** で **[デバイス アクション]** を選択します。
