---
title: "Intune を使用してデバイスを同期する"
titlesuffix: Azure portal
description: "デバイスを Intune と同期して最新のポリシーとアクションを取得する方法を説明します。\""
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 02ad249e-f098-421f-861f-6b2ff733ac7c
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ab24b147b32c94ba51728c0c223de3e6c92dd215
ms.sourcegitcommit: cf7f7e7c9e9cde5b030cf5fae26a5e8f4d269b0d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/14/2017
---
# <a name="sync-devices-with-intune-to-get-the-latest-policies-and-actions"></a>デバイスを Intune と同期して最新のポリシーとアクションを取得する


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

デバイスの**同期**のアクションは、選択したデバイスの Intune との即座の同期を強制的に実行します。 チェックインしたデバイスには、それに対して保留中のアクションまたはポリシーが即座に割り当てられます。  このアクションにより、次のスケジュールされたチェックインを待つことなく、割り当てられたポリシーの検証およびトラブルシューティングを即座に実行できるようになります。

## <a name="supported-platforms"></a>サポートされているプラットフォーム

- Windows - サポートされています
- Windows Phone - サポートされています
- iOS - サポートされています
- macOS - サポートされています
- Android - サポートされています

## <a name="how-to-sync-a-device"></a>デバイスを同期する方法

1. Azure ポータルにサインインします。
2. **[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
3. **[Intune]** ブレードで、**[デバイス]** を選択します。
4. **[デバイスとグループ]** ブレードで、**[すべてのデバイス]** を選択します。
5. 管理するデバイスの一覧からデバイスを選択し、その後 **[同期]** リモート操作を選択します。
7. **[はい]** を選んで操作を確定します。

## <a name="next-steps"></a>次のステップ

**[デバイス アクション]** を選択して同期操作の状態を表示します。 
