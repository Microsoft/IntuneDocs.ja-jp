---
title: "管理されたデバイスを Intune でリモートからロックする"
titlesuffix: Azure portal
description: "Intune を使用して管理対象デバイスをリモートからロックする方法について説明します。\""
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 01/22/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b67f285-229d-4a0f-ae34-0402a20b4518
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0a8f3c93507cde4363570a9a39f8b3b1f69c07df
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2018
---
# <a name="remotely-lock-managed-devices-with-intune"></a>管理されたデバイスを Intune でリモートからロックする


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

**リモート ロック**を使用して、選択したデバイスをロックできます。 デバイスの所有者は、ロックを解除するためにパスコードを使用する必要があります。 PIN またはパスワードが設定されているデバイスに限り、リモートでロックできます。

## <a name="supported-platforms"></a>サポートされているプラットフォーム

リモート ロックは、次のプラットフォームでサポートされます。

|プラットフォーム|サポートの状態|
|---|---|
|Android|はい|
|iOS|はい|
|macOS|はい|
|Windows 10 Desktop|[いいえ]|
|Windows 10 Mobile|はい|
|Windows Phone|はい。Windows Phone 8.1 以降の場合|

> [!NOTE]  
> macOS デバイスの場合は、6 桁の回復用 PIN を設定します。 ロックされているとき、別のデバイス アクションが送信されるまで、**デバイス概要**ブレードにその PIN が表示されます。

## <a name="how-to-remote-lock-a-device"></a>デバイスをリモート ロックする方法

1. サインイン、 [Azure ポータル](https://portal.azure.com)します。
2. **[すべてのサービス]** > **[Intune]** の順に選択します。 Intune は **[監視 + 管理]** セクションにあります。
3. **[Intune]** ブレードで、**[デバイス]** を選択します。
4. **[デバイス]** ブレードで、**[すべてのデバイス]** を選択します。
5. 管理するデバイスの一覧からデバイスを選択し、その後 **[リモート ロック]** デバイス リモート アクションを選択します。

## <a name="next-steps"></a>次の手順

実行したアクションの状態を確認するには、**[デバイス]** ブレードで **[デバイス アクション]** を選択します。
