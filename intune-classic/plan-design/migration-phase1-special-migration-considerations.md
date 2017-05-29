---
title: "移行において特に考慮すべき事項 | Microsoft Docs"
description: "この記事では、移行のキャンペーンを開始する前に、移行に関して特に考慮すべき事項について説明します。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f29d2894-e98b-4f2c-b444-a8ccc1b7efdd
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 7e0adb862d8c60805b3b34406e193df5a93be381
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017


---

# <a name="phase-1-special-migration-considerations"></a>フェーズ 1: 移行において特に考慮すべき事項

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

既存の MDM プロバイダー環境に応じて該当する可能性のある、移行において特に考慮すべき事項があります。

## <a name="factory-reset-for-apples-device-enrollment-program-dep"></a>Apple の Device Enrollment Program (DEP) を出荷時の設定に戻す

Apple の Device Enrollment Program (DEP) のデバイス構成は、エンド ユーザーが削除できない設定になっています。 DEP の高度な管理機能を保持するには、デバイスを出荷時の設定にリセットして既定の (新品の) 状態に戻してから、Intune に登録する必要があります。

引き続き DEP を使用して Intune でデバイスを管理するには、次の手順を実行します。

1.  [DEP を Intune に](/intune-classic/deploy-use/ios-device-enrollment-program-in-microsoft-intune)登録する

2.  Apple DEP アカウントに移動し、既存の MDM プロバイダーから Intune に [DEP デバイスのシリアル番号を再割り当て](https://help.apple.com/deployment/business/#/tesf9562af26)します。

3.  DEP アカウントを Intune と[同期する](/intune-classic/deploy-use/ios-device-enrollment-program-in-microsoft-intune)

4.  適切な DEP 登録プロファイルを[作成し、Intune のシリアル番号に割り当て](/intune-classic/deploy-use/ios-device-enrollment-program-in-microsoft-intune)ます。

5.  デバイスを出荷時の設定にリセットする (現在の MDM プロバイダーからリモートに、または各デバイスで手動で)

6.  エンド ユーザーにデバイスを配布します。

## <a name="next-steps"></a>次のステップ 

[フェーズ 2: 移行のキャンペーン](/intune-classic/plan-design/migration-phase2-migration-campaign)

