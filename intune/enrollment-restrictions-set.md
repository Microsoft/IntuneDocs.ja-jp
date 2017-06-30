---
title: "Intune で登録制限を設定する"
titleSuffix: Intune on Azure
description: "Intune でプラットフォームごとに登録を制限し、デバイス登録の上限数を設定します。 &quot;"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 05/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: b13ec0113096e4efc83463ed09e4c0db7fd7d6e1
ms.contentlocale: ja-jp
ms.lasthandoff: 06/08/2017

---

# <a name="set-enrollment-restrictions"></a>登録制限を設定する

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

登録を許可するデバイスの種類と最大数を設定することができます。 [登録の制限] ブレードでは、次のことを設定できます。

- 登録を許可されるプラットフォームと、Android および iOS の個人所有デバイスの登録をブロックするかどうか。

- ユーザーが登録できるデバイスの最大数。

## <a name="set-device-type-restrictions"></a>デバイスの種類の制限を設定する

1. Intune ポータルで **[デバイスの登録]** を選択し、**[登録の制限]** を選択します。

2. **[デバイスの種類の制限]** で、**[既定]** を選択します。

3. **[すべてのユーザー]** ブレードで、**[プラットフォーム]** を選択します。

4. Intune で登録できるようにするプラットフォームに対して、**[許可]** を選択します。 登録できないようにするプラットフォームに対しては、**[ブロック]** を選択します。 プラットフォームは規定で **[許可]** に設定されます。

    >[!NOTE]
    >これらの設定は、Intune ソフトウェア クライアントを使って行われる Windows の登録に適用されたり、登録をブロックしたりすることはありません。 これらの設定は、モバイル デバイス管理を使う登録にのみ影響します。

6. **[保存]** を選択します。

7. **[プラットフォーム構成]** を選択します。

8. 個人所有の iOS および Android デバイスの登録を **[許可]** するか **[ブロック]** するかを選びます。

9. **[保存]** を選択します。

## <a name="set-device-limit-restrictions"></a>デバイス数の制限を設定する

1. Intune ポータルで **[デバイスの登録]** を選択し、**[登録の制限]** を選択します。

3. **[デバイス数の制限]** で、**[既定]** を選択します。

4. **[すべてのユーザー]** ブレードで、**[デバイスの上限数]** を選択します。

5. ユーザーが登録できるデバイスの最大数を選択し、**[保存]** を選択します。

