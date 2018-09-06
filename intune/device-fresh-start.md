---
title: Microsoft Intune で Windows 10 デバイスをリセットする - Azure | Microsoft Docs
description: Microsoft Intune を使用して、Windows 10 PC 上のアプリを削除またはアンインストールするには、[新たに開始] を使用します。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/09/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5aa5cfa3-c483-4099-b40f-578ff8dca425
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6b66cd00f734cab3ca85f6d87f056f8c482a377d
ms.sourcegitcommit: 2811df0f851ca6b08f6ae8c926fb2e6971c41690
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/13/2018
ms.locfileid: "40251927"
---
# <a name="use-fresh-start-to-reset-windows-10-devices-with-intune"></a>[新たに開始] を使用して Intune が稼働する Windows 10 デバイスをリセットする


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

**[新たに開始]** デバイス操作は、Windows 10 バージョン 1703 以降を実行している PC にインストールされているすべてのアプリを削除します。 [新たに開始] は、一般的に新しい PC にプレインストールされている (OEM) アプリケーションを削除するために役立ちます。  

1. [Azure Portal](https://portal.azure.com) にサインインし、**[Microsoft Intune]** > **[デバイス]** > **[すべてのデバイス]** に移動します。
2. 管理するデバイスの一覧から Windows 10 デスクトップ デバイスを選択します。
3. **[新たに開始]** をクリックします。 
4. 以下の目的で **[このデバイスにあるユーザー データを保持する]** を選択します。
   * Azure AD に参加したデバイスを保持します。
    * モバイル デバイス管理に登録されているデバイスを保持します。 
    * デバイス ユーザーのホーム フォルダーの内容を保持し、アプリと設定を削除します。  
  > [!IMPORTANT]
 > ユーザー データを保持しない場合、デバイスは既定の状態に復元されます。 Azure AD とモバイル デバイス管理から登録解除されます。 
 
5. **[OK]** をクリックします。   
6. この操作の状態を確認するには、**[デバイス]** に戻り、**[デバイス アクション]** をクリックします。  
