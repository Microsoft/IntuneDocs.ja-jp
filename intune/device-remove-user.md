---
title: "Microsoft Intune を使用して iOS デバイスからユーザーを削除する"
titlesuffix: 
description: "Intune を使用して共有の iOS デバイスからユーザーを削除する方法について説明します。"
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2ea5941c-a69b-4e1c-b42c-a1fc0c3a7de7
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1b2321de0c0541111fdf6f18345bd952ca8b5448
ms.sourcegitcommit: aafed032492c1b5861d7097a335f9bbb29ce3221
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/02/2018
---
# <a name="remove-a-user-from-a-shared-ios-device"></a>共有の iOS デバイスからユーザーを削除する


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

**[ユーザーの削除]** アクションにより、[iOS 教育プロファイル](education-settings-configure-ios.md)を使用して iOS Classroom アプリを管理するように構成されている共有の iPad デバイスのローカル キャッシュからユーザーを選択して削除することができます。 

## <a name="supported-platforms"></a>サポートされているプラットフォーム

- Windows - サポートされていません
- Windows Phone - サポートされていません
- iOS - iOS 9.3 以降 (共有 iPad デバイスのみ) でサポートされています
- macOS - サポートされていません
- Android - サポートされていません

## <a name="how-to-remove-a-user"></a>ユーザーを削除する方法

1. サインイン、 [Azure ポータル](https://portal.azure.com)します。
2. **[すべてのサービス]** > **[Intune]** の順に選択します。 Intune は、**[監視 + 管理]** セクションにあります。
3. **[Intune]** ブレードで、**[デバイス]** を選択します。
4. **[デバイス]** ブレードで、**[すべてのデバイス]** を選択します。
5. 管理するデバイスの一覧で、iOS デバイスを選択します。
6. そのデバイスのブレードで、**[ユーザー]** を選択します。
7. 一覧で、削除するユーザーを右クリックして、**[ユーザーの削除]** を選択します。

## <a name="next-steps"></a>次の手順

実行したアクションの状態を確認するには、**[デバイス]** ブレードで **[デバイス アクション]** を選択します。
