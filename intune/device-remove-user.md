---
title: "Intune を使用して iOS デバイスからユーザーを削除する"
titleSuffix: Intune on Azure
description: "Intune を使用して共有の iOS デバイスからユーザーを削除する方法について説明します。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 07/13/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2ea5941c-a69b-4e1c-b42c-a1fc0c3a7de7
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5ed66c47215a9e1c1ab28f2e30a3663d0287869d
ms.sourcegitcommit: be12974a7eaa4ce9cffe45aabe456c858d582e20
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/14/2017
---
# <a name="remove-a-user-from-a-shared-ios-device-with-intune"></a>Intune を使用して共有の iOS デバイスからユーザーを削除する


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

**[ユーザーの削除]** アクションにより、[iOS 教育プロファイル](education-settings-configure-ios.md)を使用して iOS Classroom アプリを管理するように構成されている共有の iPad デバイスのローカル キャッシュからユーザーを選択して削除することができます。 

1. Azure ポータルにサインインします。
2. **[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
3. **[Intune]** ブレードで、**[デバイス]** を選択します。
4. **[デバイス]** ブレードで、**[すべてのデバイス]** を選択します。
5. 管理するデバイスの一覧で、iOS デバイスを選択します。
6. そのデバイスのブレードで、**[ユーザー]** を選択します。
7. 一覧で、削除するユーザーを右クリックして、**[ユーザーの削除]** を選択します。

## <a name="next-steps"></a>次のステップ

実行したアクションの状態を確認するには、**[デバイスとグループ]** ブレードで **[デバイス アクション]** を選択します。
