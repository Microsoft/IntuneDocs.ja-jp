---
title: "Intune で iOS デバイスのユーザーをログアウトする"
titlesuffix: Azure portal
description: "Intune で iOS デバイスの現在のユーザーをログアウトする方法について説明します。\""
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 07/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 702bc46c-1a6f-4689-bd53-3b778a447baa
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5e59eee3660f56fdd967237563e69324b8307e3a
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="logout-the-current-user-on-intune-managed-ios-devices"></a>Intune で管理される iOS デバイスの現在のユーザーをログアウトする


[!INCLUDE[azure_portal](./includes/azure_portal.md)]


**[現在のユーザーのログアウト]** アクションにより、[iOS 教育プロファイル](education-settings-configure-ios.md)を使用して iOS Classroom アプリを管理するように構成されている共有の iPad デバイスから現在のユーザーがログアウトします。 

## <a name="supported-platforms"></a>サポートされているプラットフォーム

- Windows - サポートされていません
- Windows Phone - サポートされていません
- iOS - iOS 9.3 以降 (共有 iPad デバイスのみ) でサポートされています
- macOS - サポートされていません
- Android - サポートされていません

## <a name="how-to-logout-the-current-user"></a>現在のユーザーをログアウトする方法

1.  Azure Portal にサインインします。
2.  **[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
3.  **[Intune]** ブレードで、**[デバイス]** を選択します。
4.  **[デバイスとグループ]** ブレードで、**[すべてのデバイス]** を選択します。
5.  管理するデバイスの一覧から iOS デバイスを選択して、**[現在のユーザーのログアウト]** のデバイス リモート アクションを選択します。

## <a name="next-steps"></a>次の手順

実行したアクションの状態を確認するには、**[デバイスとグループ]** ブレードで **[デバイス アクション]** を選択します。
