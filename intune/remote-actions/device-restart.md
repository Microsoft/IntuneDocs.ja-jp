---
title: Microsoft Intune - Azure でデバイスを再起動する | Microsoft Docs
description: 再起動リモート アクションを使用して、Azure Portal で Microsoft Intune を使用している Windows および iOS デバイスを再起動します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/21/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c707e0c4-391a-4bad-9dfd-9a7799c48dd5
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 82ebf35d0eb435f2df4e6cf55274808e6fa690f4
ms.sourcegitcommit: af384c46ec8d8def6aa32c3b89947748dc6fd28f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/22/2020
ms.locfileid: "76517543"
---
# <a name="remotely-restart-devices-with-intune"></a>Intune でデバイスをリモートで再起動する


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

**[再起動]** デバイス アクションでは、選択したデバイスが (5 分以内に) 再起動されます。 デバイスの所有者に再起動の自動通知が行われないため、作業内容が失われる可能性があります。

## <a name="supported-platforms"></a>サポートされているプラットフォーム

- Windows - Windows 8.1 以降でサポートされています
- Windows Phone - Windows Phone 8.1 以降でサポートされています
- Android キオスク デバイス - Android 7.0 以降でサポートされています
- iOS - サポートされています

    > [!Note]  
    > このコマンドは、監視されているデバイスと**デバイス ロック** アクセス権を要求します。 デバイスがすぐに再起動します。 パスコードがロックされている iOS デバイスは、再起動後に Wi-Fi ネットワークに再度参加しません。 再起動後に、デバイスがサーバーと通信できない場合があります。
- macOS - サポートされていません
- Android および Android 仕事用プロファイル デバイス - サポートされていません

## <a name="restart-a-device"></a>デバイスを再起動する

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。
3. **[デバイス]**  >  **[すべてのデバイス]** の順に選択します。
4. 管理するデバイスのリストで、デバイスを選び、 **[再起動]**  >  **[はい]** の順に選択します。

## <a name="next-steps"></a>次のステップ

- **[再起動]** デバイス アクションの状態を表示するには、 **[デバイス]**  >  **[デバイス アクション]** の順に選択します。
