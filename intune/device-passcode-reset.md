---
title: "Intune でデバイスのパスコードをリセットする"
titlesuffix: Azure portal
description: "Intune で管理するデバイスのパスコードをリセットする方法について説明します。\""
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 47181d19-4049-4c7a-a8de-422206c4027e
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3defec3624944918d14b9c4527487c368c487dd6
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2017
---
# <a name="reset-the-passcode-on-intune-managed-devices"></a>Intune で管理するデバイスのパスコードをリセットする


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

**[パスコードのリセット]** アクションは、デバイスの新しいパスコードを生成します。新しいパスコードは、[<*デバイス名*> **概要**] ブレードに表示されます。

## <a name="supported-platforms"></a>サポートされているプラットフォーム

- Windows - サポートされていません
- Windows Phone - Windows Phone 8.1 から Azure AD に参加していない Windows 10 Creators Update まで、Windows 10 Creators Update 以降でサポートされています
- iOS - サポートされています
- macOS - サポートされていません
- Android - Android 7 より前の Android バージョンでサポートされています。 Android for Work はサポートされていません。

## <a name="how-to-reset-a-passcode"></a>パスコードをリセットする方法

1. Azure ポータルにサインインします。
2. **[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
3. **[Intune]** ブレードで、**[デバイス]** を選択します。
4. **[デバイスとグループ]** ブレードで、**[すべてのデバイス]** を選択します。
5. 管理するデバイスの一覧からデバイスを選択し、その後 **[パスコードのリセット]** デバイス リモート アクションを選択します。

## <a name="next-steps"></a>次のステップ

実行したアクションの状態を確認するには、**[デバイスとグループ]** ブレードで **[デバイス アクション]** を選択します。
