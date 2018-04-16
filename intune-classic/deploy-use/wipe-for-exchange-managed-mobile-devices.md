---
title: "Exchange で管理されているモバイル デバイスのワイプ"
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
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: lancecra
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 753e5e9dac7199dff18d110808524f05aa669036
ms.sourcegitcommit: 2459bfda07a2afd2cfcd94a1972a3fb2e565ce8d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/22/2018
---
# <a name="wipe-for-exchange-managed-mobile-devices"></a>Wipe for [Exchange]-managed mobile devices

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Microsoft Intune では、Exchange ActiveSync (EAS) と Intune Exchange Connector を使って管理されているモバイル デバイスをワイプまたはリセットすることができます。 次の表に、Exchange ActiveSync で利用できるインベントリからのワイプ機能を説明します。


|      ワイプの種類       |              Windows 8.1 および Windows RT 8.1              |                            iOS                             |                          Android                          |
|-------------------------|----------------------------------------------------------|------------------------------------------------------------|-----------------------------------------------------------|
|        フル ワイプ        |          メール アカウントとキャッシュ済みメールを削除します。           |                      出荷時の設定に戻します。                       |                      出荷時の設定に戻します。                       |
|  選択的なワイプ/電子メール   |                  電子メール アカウントを削除します。                  |                       サポートされていません。                       |                      サポートされていません。                       |
| 選択的なワイプ/ポリシー | ポリシーの強制は削除されますが、設定は変更されません | ポリシーの強制は削除されますが、設定は変更されません。 | ポリシーの強制は削除されますが、設定は変更されません |

