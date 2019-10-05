---
title: ユーザー デバイスの関連付け - Intune データ ウェアハウス
titleSuffix: Microsoft Intune
description: UserDeviceAssociation エンティティには、組織内のユーザー デバイスの関連付けが含まれています。
keywords: Intune データ ウェアハウス
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/23/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 777484A7-09CE-4409-987F-76B3F87DFE93
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 780422c176b7ab27baf3b6025a42179508e117ff
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2019
ms.locfileid: "71733180"
---
# <a name="reference-for-user-device-association-entity"></a>ユーザー デバイスの関連付けエンティティのリファレンス

**userDeviceAssociation** エンティティには、組織内のユーザー デバイスの関連付けが含まれています。

## <a name="userdeviceassociations"></a>userDeviceAssociations


|        名前        |                                           説明                                            |        例         |
|--------------------|--------------------------------------------------------------------------------------------------|------------------------|
|      userKey       |              データ ウェアハウス内のユーザーを示す一意識別子 (代理キー)。               |          123           |
|     deviceKey      |                      データ ウェアハウス内のデバイスを示す一意識別子。                      |          123           |
| createdDateTimeUTC |           ユーザー デバイスの関連付けが作成されたときの日時。 UTC 形式を使用します。           | 11/23/2016 12:00:00 AM |
|     isDeleted      | ユーザーがそのデバイスを登録解除し、その関連付けが最新でなくなったことを示します。 |       真/偽       |
|  endedDateTimeUTC  |              IsDeleted が <strong>True</strong> に変更されたときの日時 (UTC)。               | 06/23/2017 12:00:00 AM |

## <a name="next-steps"></a>次の手順

- [Intune データ ウェアハウス](../reports-nav-create-intune-reports.md)について確認してください。
