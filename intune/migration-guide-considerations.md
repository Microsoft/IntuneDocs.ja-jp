---
title: "移行において特に考慮すべき事項"
description: "この記事では、移行のキャンペーンを開始する前に、移行に関して特に考慮すべき事項について説明します。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f29d2894-e98b-4f2c-b444-a8ccc1b7efdd
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 1911c8a2460a98218027c40a26d81f1ca4c482f5
ms.openlocfilehash: bc39ffd3a4f11a4c2b32f75dc5befcd8ce42f43e
ms.contentlocale: ja-jp
ms.lasthandoff: 06/13/2017


---

# <a name="special-migration-considerations"></a>移行において特に考慮すべき事項

[!INCLUDE[note for both-portals](./includes/note-for-both-portals.md)]

既存の MDM プロバイダー環境に応じて該当する可能性のある、移行において特に考慮すべき事項があります。

## <a name="factory-reset-for-apples-device-enrollment-program-dep"></a>Apple の Device Enrollment Program (DEP) を出荷時の設定に戻す

Apple の Device Enrollment Program (DEP) のデバイス構成は、エンド ユーザーが削除できない設定になっています。 DEP の高度な管理機能を保持するには、デバイスを出荷時の設定にリセットして既定の (新品の) 状態に戻してから、Intune に登録する必要があります。

DEP の使用を続行して Intune でデバイスを管理するには、[Device Enrollment Program で iOS デバイスの登録をセットアップします](/intune/device-enrollment-program-enroll-ios)。


## <a name="next-steps"></a>次のステップ 

[フェーズ 2: 移行のキャンペーン](migration-guide-campaign.md)

