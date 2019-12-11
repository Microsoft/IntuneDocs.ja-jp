---
title: 移行において特に考慮すべき事項
titleSuffix: Microsoft Intune
description: この記事では、Microsoft Intune への移行キャンペーンを開始する前の特別な移行に関する考慮事項を示します。
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f29d2894-e98b-4f2c-b444-a8ccc1b7efdd
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 86cef30c31b53c6bfd1873390fb7546cbeab2a53
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "72510025"
---
# <a name="special-migration-considerations"></a>移行において特に考慮すべき事項

既存の MDM プロバイダー環境に応じて該当する可能性のある、移行において特に考慮すべき事項があります。

## <a name="wipe-for-apples-device-enrollment-program-dep"></a>Apple の Device Enrollment Program (DEP) のワイプ

Apple の Device Enrollment Program (DEP) のデバイス構成は、エンド ユーザーが削除できない設定になっています。 DEP の高度な管理機能を保持するには、デバイスをワイプして箱から取り出したときの (新品の) 状態に戻してから、Intune に登録する必要があります。

DEP の使用を続行して Intune でデバイスを管理するには、[Device Enrollment Program で iOS デバイスの登録をセットアップします](../enrollment/device-enrollment-program-enroll-ios.md)。


## <a name="next-steps"></a>次の手順

[フェーズ 2:移行のキャンペーン](../migration-guide-campaign.md)
