---
title: "Exchange で管理されているモバイル デバイスのワイプ | Microsoft Docs"
description: "Microsoft Intune では、Exchange ActiveSync (EAS) と Intune Exchange Connector を使って管理されているモバイル デバイスをワイプまたはリセットすることができます"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e116b620-1e12-4b5c-9905-2f7acf2ae530
ms.reviewer: lancecra
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 4b0914ab12456fd3ad5f957d68a59df9de539176
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017


---


# <a name="wipe-for-exchange-managed-mobile-devices"></a>Wipe for [Exchange]-managed mobile devices

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune では、Exchange ActiveSync (EAS) と Intune Exchange Connector を使って管理されているモバイル デバイスをワイプまたはリセットすることができます。 次の表に、Exchange ActiveSync で利用できるインベントリからのワイプ機能を説明します。

|ワイプの種類|Windows 8.1 および Windows RT 8.1|iOS|Android|
|----------------|----------------------------------|--------------|-------------------|-------|-----------|
|フル ワイプ|メール アカウントとキャッシュ済みメールを削除します。|出荷時の設定に戻します。|出荷時の設定に戻します。|
|選択的なワイプ/電子メール|電子メール アカウントを削除します。|サポートされていません。|サポートされていません。|
|選択的なワイプ/ポリシー|ポリシーの強制は削除されますが、設定は変更されません|ポリシーの強制は削除されますが、設定は変更されません。|ポリシーの強制は削除されますが、設定は変更されません|

