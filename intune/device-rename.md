---
title: Microsoft Intune で Windows デバイスの名前を変更する - Azure | Microsoft Docs
description: Microsoft Intune を使用して Windows デバイスの名前を変更する
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/26/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8dfdc3641d583fc045346034ee8543feff1e7cbf
ms.sourcegitcommit: 1144247aa7f042eb1b99d8fd8dd17b909eae38c5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/28/2019
ms.locfileid: "59567102"
---
# <a name="rename-a-windows-device-in-intune"></a>Intune で Windows デバイスの名前を変更する


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

**デバイスの名前を変更**アクションにより、Intune で登録されている企業所有の Windows デバイスの名前を変更できます。 デバイスの名前は、Intune 内とデバイス上で変更されます。 

この機能では、ハイブリッド Azure AD Windows デバイスの名前変更は現在サポートされていません。

## <a name="rename-a-device"></a>デバイスの名前を変更する

1. [Azure ポータル](https://portal.azure.com)にサインインします。
2. **[すべてのサービス]** を選択し、 **[Intune]** をフィルターとして適用し、 **[Microsoft Intune]** を選択します。
3. **[デバイス]**  >  **[すべてのデバイス]** > Windows デバイスの選択 >  **[その他]**  >  **[デバイスの名前を変更]** の順に選択します。
4. **[デバイスの名前を変更]** ブレードで、テキスト ボックスに新しい名前を入力します。 文字、数字、ハイフンを使用できます。 名前には、少なくとも 1 つの文字またはハイフンを含める必要があります。
5. 名前の変更後、デバイスを再起動する場合、 **[名前を変更したら再起動する]** の横の **[はい]** を選択します。
6. **[名前の変更]** を選択します。



## <a name="next-steps"></a>次の手順

**[名前の変更]** デバイス アクションの状態を表示するには、デバイスの **[概要]** ページを確認します。
