---
title: Microsoft Intune を使ってデバイスの名前を変更する - Azure | Microsoft Docs
description: Microsoft Intune を使ってデバイスの名前を変更します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/05/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 35fae5ea1b3294772db4f4db51179892e08ed5d1
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2019
ms.locfileid: "71728508"
---
# <a name="rename-a-device-in-intune"></a>Intune 上でデバイスの名前を変更する


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

**デバイス名の変更**アクションによって、Intune に登録されているデバイスの名前を変更できます。 デバイスの名前は、Intune 内とデバイス上で変更されます。

次の種類のデバイス名を変更できます。
- 企業所有の Windows 
- 監視下にある iOS
- 企業所有の MacOS 10

この機能では、ハイブリッド Azure AD Windows デバイスの名前変更は現在サポートされていません。

## <a name="rename-a-device"></a>デバイスの名前を変更する

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインします。
3. **[デバイス]** > **[すべてのデバイス]** > デバイスの選択 > **[その他]** > **[デバイスの名前を変更]** の順に選択します。
4. **[デバイスの名前を変更]** ブレードで、テキスト ボックスに新しい名前を入力します。 文字、数字、ハイフンを使用できます。 名前には、少なくとも 1 つの文字またはハイフンを含める必要があります。
5. 名前の変更後、デバイスを再起動する場合、**[名前を変更したら再起動する]** の横の **[はい]** を選択します。
6. **[名前の変更]** を選択します。



## <a name="next-steps"></a>次の手順

**[名前の変更]** デバイス アクションの状態を表示するには、デバイスの **[概要]** ページを確認します。
