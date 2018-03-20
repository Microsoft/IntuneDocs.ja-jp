---
title: "Microsoft Intune でデバイスをロックする - Azure | Microsoft Docs"
description: "PIN またはパスワードで保護されているデバイスをロックするには、Microsoft Intune のリモート ロック アクションを使用します。"
keywords: 
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b67f285-229d-4a0f-ae34-0402a20b4518
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 59a55de54a5a18f5fd1080fefa15c0e4801a1456
ms.sourcegitcommit: 9cf05d3cb8099e4a238dae9b561920801ad5cdc6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2018
---
# <a name="remotely-lock-devices-with-intune"></a>デバイスを Intune でリモートからロックする

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

**リモート ロック** を使用して、デバイスをロックできます。 ロックを解除するには、デバイスの所有者がパスコードを入力する必要があります。 PIN またはパスワードが設定されているデバイスをリモートでロックすることができます。 PIN またはパスコードがないデバイスは、リモートでロックできません。

## <a name="supported-platforms"></a>サポートされているプラットフォーム

リモート ロックは、次のプラットフォームでサポートされます。

- Android
- iOS
- macOS
- Windows 10 Mobile
- Windows Phone 8.1 以降

次のデバイスでは**サポートされていません**。
- Windows 10 Desktop

> [!NOTE]
> macOS デバイスの場合は、6 桁の回復用 PIN を設定します。 ロックされているときは、別のデバイス アクションが送信されるまで、**[デバイス概要]** にその PIN が表示されます。

## <a name="remote-lock-a-device"></a>デバイスのリモート ロック

1. [Azure ポータル](https://portal.azure.com)にサインインします。
2. **[すべてのサービス]** を選択し、**[Intune]** をフィルターとして適用し、**[Microsoft Intune]** を選択します。
3. **[デバイス]**、**[すべてのデバイス]** の順に選択します。
4. デバイスの一覧からデバイスを選択し、**[リモート ロック]** アクションを選択します。

## <a name="next-steps"></a>次の手順

このアクションのステータスを表示するには、**[デバイス アクション]** を開きます ([Microsoft Intune] > [デバイス])。 デバイスの管理に役立つその他のアクションについては、[使用できるアクション](device-management.md)に関するページを参照してください。