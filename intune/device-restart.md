---
title: Microsoft Intune - Azure でデバイスを再起動する | Microsoft Docs
description: 再起動リモート アクションを使用して、Azure Portal で Microsoft Intune を使用している Windows および iOS デバイスを再起動します。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: c707e0c4-391a-4bad-9dfd-9a7799c48dd5
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 98b3403e3f45e1aa7169937a05692686d97d7362
ms.sourcegitcommit: 390a4be5aa36007c36fb6a5abcfe8d20bc862a4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2018
---
# <a name="remotely-restart-devices-with-intune"></a>Intune でデバイスをリモートで再起動する


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

**[再起動]** デバイス アクションでは、選択したデバイスが再起動されます。 デバイスの所有者に再起動の自動通知が行われないため、作業内容が失われる可能性があります。

## <a name="supported-platforms"></a>サポートされているプラットフォーム

- Windows - Windows 8.1 以降でサポートされています
- Windows Phone - Windows Phone 8.1 以降でサポートされています
- iOS - サポートされています

    > [!Note]  
    > このコマンドは、監視されているデバイスと**デバイス ロック** アクセス権を要求します。 デバイスがすぐに再起動します。 パスコードがロックされている iOS デバイスは、再起動後に Wi-Fi ネットワークに再度参加しません。 再起動後に、デバイスがサーバーと通信できない場合があります。
- macOS - サポートされていません
- Android - サポートされていません

## <a name="restart-a-device"></a>デバイスを再起動する

1. [Azure ポータル](https://portal.azure.com)にサインインします。
2. **[すべてのサービス]** を選択し、**[Intune]** をフィルターとして適用し、**[Microsoft Intune]** を選択します。
3. **[デバイス]** > **[すべてのデバイス]** の順に選択します。
4. 管理するデバイスの一覧で、デバイスを選択して、**[詳細]** を選択し、**[再起動]** デバイス リモート アクションを選択します。

## <a name="next-steps"></a>次の手順

- **[再起動]** デバイス アクションの状態を表示するには、**[デバイス]** > **[デバイス アクション]** の順に選択します。
