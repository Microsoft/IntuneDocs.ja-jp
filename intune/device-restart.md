---
title: "Intune でデバイスをリモートで再起動する"
titlesuffix: Azure portal
description: "デバイスの再起動アクションを使用して、デバイスをリモートで再起動する方法について説明します。\""
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 11/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c707e0c4-391a-4bad-9dfd-9a7799c48dd5
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a49f95ce81f750c539959674a15df41118f20aaa
ms.sourcegitcommit: eac89306d1391a6d3ae1179612b0820b19c2baa6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/23/2018
---
# <a name="remotely-restart-devices-with-intune"></a>Intune でデバイスをリモートで再起動する


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

**[再起動]** デバイス アクションでは、選択したデバイスが再起動されます。 デバイスの所有者には再起動の自動通知が行われないため、作業内容が失われる可能性があります。

## <a name="supported-platforms"></a>サポートされているプラットフォーム

- Windows - Windows 8.1 以降でサポートされています
- Windows Phone - Windows Phone 8.1 以降でサポートされています
- iOS - サポートされています

    > [!Note]  
    > このコマンドは、監視されているデバイスと**デバイス ロック** アクセス権を要求します。 デバイスがすぐに再起動します。 パスコードでロックされている iOS デバイスが再起動後に Wi-Fi ネットワークに再び参加することはありません。再起動後、サーバーと通信できないことがあります。
- macOS - サポートされていません
- Android - サポートされていません

## <a name="how-to-restart-a-device"></a>デバイスを再起動する方法

1. サインイン、 [Azure ポータル](https://portal.azure.com)します。
2. **[すべてのサービス]** > **[Intune]** の順に選択します。 Intune は **[監視 + 管理]** セクションにあります。
3. **[Intune]** ブレードで、**[デバイス]** を選択します。
4. **[デバイス]** ブレードで、**[すべてのデバイス]** を選択します。
5. 管理するデバイスの一覧からデバイスを選択し、**[詳細]**、**[再起動]** デバイス リモート アクションの順に選択します。

## <a name="next-steps"></a>次の手順

実行したアクションの状態を確認するには、**[デバイス]** ブレードで **[デバイス アクション]** を選択します。
