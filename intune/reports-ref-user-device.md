---
title: ユーザー デバイスの関連付け - Intune データ ウェアハウス
titlesuffix: Microsoft Intune
description: UserDeviceAssociation エンティティには、組織内のユーザー デバイスの関連付けが含まれています。
keywords: Intune データ ウェアハウス
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 777484A7-09CE-4409-987F-76B3F87DFE93
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 341895e1de718f1bebdf840c3eabf79b67db9cf6
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2019
ms.locfileid: "55833895"
---
# <a name="reference-for-user-device-association-entity"></a>ユーザー デバイスの関連付けエンティティのリファレンス

**UserDeviceAssociation** エンティティには、組織内のユーザー デバイスの関連付けが含まれています。

## <a name="userdeviceassociation"></a>UserDeviceAssociation


|        名前        |                                           説明                                            |        例         |
|--------------------|--------------------------------------------------------------------------------------------------|------------------------|
|      UserKey       |              データ ウェアハウス内のユーザーを示す一意識別子 (代理キー)。               |          123           |
|     DeviceKey      |                      データ ウェアハウス内のデバイスを示す一意識別子。                      |          123           |
| CreatedDateTimeUTC |           ユーザー デバイスの関連付けが作成されたときの日時。 UTC 形式を使用します。           | 11/23/2016 12:00:00 AM |
|     IsDeleted      | ユーザーがそのデバイスを登録解除し、その関連付けが最新でなくなったことを示します。 |       真/偽       |
|  EndedDateTimeUTC  |              IsDeleted が <strong>True</strong> に変更されたときの日時 (UTC)。               | 06/23/2017 12:00:00 AM |

## <a name="next-steps"></a>次の手順

- [Intune データ ウェアハウス](reports-nav-create-intune-reports.md)について確認してください。
