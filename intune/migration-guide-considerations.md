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
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f29d2894-e98b-4f2c-b444-a8ccc1b7efdd
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6f700a93c9640381e33b4b1d1fd442f9442acbe1
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66050521"
---
# <a name="special-migration-considerations"></a>移行において特に考慮すべき事項

既存の MDM プロバイダー環境に応じて該当する可能性のある、移行において特に考慮すべき事項があります。

## <a name="wipe-for-apples-device-enrollment-program-dep"></a>Apple の Device Enrollment Program (DEP) のワイプ

Apple の Device Enrollment Program (DEP) のデバイス構成は、エンド ユーザーが削除できない設定になっています。 DEP の高度な管理機能を保持するには、デバイスをワイプして箱から取り出したときの (新品の) 状態に戻してから、Intune に登録する必要があります。

DEP の使用を続行して Intune でデバイスを管理するには、[Device Enrollment Program で iOS デバイスの登録をセットアップします](device-enrollment-program-enroll-ios.md)。


## <a name="next-steps"></a>次の手順

[フェーズ 2:移行のキャンペーン](migration-guide-campaign.md)
