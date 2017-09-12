---
title: "Intune を使用してデバイスを同期する"
titlesuffix: Azure portal
description: "デバイスを Intune と同期して最新のポリシーとアクションを取得する方法を説明します。\""
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 02ad249e-f098-421f-861f-6b2ff733ac7c
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3906b567935f026202ccf0e81424a1bb36e376ef
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/09/2017
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
