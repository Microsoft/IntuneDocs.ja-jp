---
title: iOS デバイスのユーザーをログアウトする
titlesuffix: Microsoft Intune
description: Intune で iOS デバイスの現在のユーザーをログアウトする方法について説明します。"
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 702bc46c-1a6f-4689-bd53-3b778a447baa
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 68c22c8fb966fe3ad4e821dd7e61510e0a519a82
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2019
ms.locfileid: "55835710"
---
# <a name="logout-the-current-user-on-intune-managed-ios-devices"></a>Intune で管理される iOS デバイスの現在のユーザーをログアウトする


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

**[現在のユーザーのログアウト]** アクションでは、共有の iPad デバイスの現在のユーザーがログアウトされます。 

## <a name="supported-platforms"></a>サポートされているプラットフォーム

- Windows - サポートされていません
- Windows Phone - サポートされていません
- iOS - iOS 9.3 以降 (共有 iPad デバイスのみ) でサポートされています
- macOS - サポートされていません
- Android - サポートされていません

## <a name="how-to-log-out-the-current-user"></a>現在のユーザーをログアウトする

1.  Azure Portal にサインインします。
2.  **[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
3.  **[Intune]** ブレードで、**[デバイス]** を選択します。
4.  **[デバイスとグループ]** ブレードで、**[すべてのデバイス]** を選択します。
5.  管理するデバイスの一覧から iOS デバイスを選択して、**[現在のユーザーのログアウト]** のデバイス リモート アクションを選択します。

## <a name="next-steps"></a>次の手順

実行したアクションの状態を確認するには、**[デバイスとグループ]** ブレードで **[デバイス アクション]** を選択します。
