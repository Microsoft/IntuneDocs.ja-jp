---
title: "移行において特に考慮すべき事項"
description: "この記事では、移行キャンペーンを開始する前の特別な移行に関する考慮事項を示します。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 07/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f29d2894-e98b-4f2c-b444-a8ccc1b7efdd
ms.reviewer: dagerrit
ms.suite: ems
ms.openlocfilehash: 7ff1180275fddc7f0d6ef957c4680d7c34ad471e
ms.sourcegitcommit: 388c5f59bc992375ac63968fd7330af5d84a1348
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/12/2017
---
# <a name="special-migration-considerations"></a>移行において特に考慮すべき事項

既存の MDM プロバイダー環境に応じて該当する可能性のある、移行において特に考慮すべき事項があります。

## <a name="factory-reset-for-apples-device-enrollment-program-dep"></a>Apple の Device Enrollment Program (DEP) を出荷時の設定に戻す

Apple の Device Enrollment Program (DEP) のデバイス構成は、エンド ユーザーが削除できない設定になっています。 DEP の高度な管理機能を保持するには、デバイスを出荷時の設定にリセットして既定の (新品の) 状態に戻してから、Intune に登録する必要があります。

DEP の使用を続行して Intune でデバイスを管理するには、[Device Enrollment Program で iOS デバイスの登録をセットアップします](device-enrollment-program-enroll-ios.md)。


## <a name="next-steps"></a>次のステップ

[フェーズ 2: 移行のキャンペーン](migration-guide-campaign.md)
