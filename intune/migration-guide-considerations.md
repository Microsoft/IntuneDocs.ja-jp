---
title: 移行において特に考慮すべき事項
titlesuffix: Microsoft Intune
description: この記事では、Microsoft Intune への移行キャンペーンを開始する前の特別な移行に関する考慮事項を示します。
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f29d2894-e98b-4f2c-b444-a8ccc1b7efdd
ms.reviewer: dagerrit
ms.suite: ems
ms.openlocfilehash: bd59cf3a4764cc66d0e7d1f47e69c2ff93352387
ms.sourcegitcommit: 21db583d6a9d3c15a8a8ee5579309dff1cfe1f8b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/16/2018
ms.locfileid: "29925983"
---
# <a name="special-migration-considerations"></a>移行において特に考慮すべき事項

既存の MDM プロバイダー環境に応じて該当する可能性のある、移行において特に考慮すべき事項があります。

## <a name="factory-reset-for-apples-device-enrollment-program-dep"></a>Apple の Device Enrollment Program (DEP) を出荷時の設定に戻す

Apple の Device Enrollment Program (DEP) のデバイス構成は、エンド ユーザーが削除できない設定になっています。 DEP の高度な管理機能を保持するには、デバイスを出荷時の設定にリセットして既定の (新品の) 状態に戻してから、Intune に登録する必要があります。

DEP の使用を続行して Intune でデバイスを管理するには、[Device Enrollment Program で iOS デバイスの登録をセットアップします](device-enrollment-program-enroll-ios.md)。


## <a name="next-steps"></a>次の手順

[フェーズ 2: 移行のキャンペーン](migration-guide-campaign.md)
