---
title: "ユーザー - Intune データ ウェアハウス | Microsoft Docs"
description: "Intune データ ウェアハウス API のエンティティ コレクションのユーザー カテゴリに関するリファレンス トピック。"
keywords: "Intune データ ウェアハウス"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: C29A6EEA-72B7-427E-9601-E05B408F3BB0
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 8088127f5968c0b4f07f83b1dad02ba90f4e6b9a
ms.sourcegitcommit: e9f9fccccef691333143b7523d1b325ee7d1915a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/02/2017
---
# <a name="reference-for-user-entity"></a>User エンティティのリファレンス

**ユーザー** カテゴリには、データ モデルのユーザーとエージェントのプロパティを定義する **[ユーザー]** エンティティが含まれています。

**ユーザー**

**User** エンティティには、社内のすべての Azure Active Directory (Azure AD) ユーザーと割り当てられているライセンスが表示されます。

| プロパティ  | 説明 | 例 |
|---------|------------|--------|
| UserKey |データ ウェアハウス内のユーザーを示す一意識別子 - 代理キー。 |123 |
| UserId |ユーザーを示す一意識別子 - UserKey と似ていますが、ナチュラル キーです。 |b66bc706-ffff-7437-0340-032819502773 |
| UserEmail |ユーザーの電子メール アドレス。 |John@constoso.com |
| 表示名 |ユーザーの表示名。 |John |
| IntuneLicensed |ユーザーに Intune のライセンスがあるかどうかを示します。 |真/偽 |
| IsDeleted |このユーザー レコードが更新されているかどうかを示します。  True - このユーザーには新しいレコードがあり、そのフィールドはこのテーブルで更新されています。 False - このユーザーの最新のレコード。 |真/偽 |
| StartDateInclusiveUTC |このユーザーがデータ ウェアハウスで作成されたときの UTC 日時。 |11/23/2016 12:00:00 AM |
| EndDateExclusiveUTC |IsDeleted が True に変更されたときの UTC 日時。 |11/23/2016 12:00:00 AM |
| IsCurrent |データ ウェアハウス内のこのユーザー レコードが最新かどうかを示します。 |真/偽 |
| RowLastModifiedDateTimeUTC |このユーザーがデータ ウェアハウスで最後に変更されたときの UTC 日時。 |11/23/2016 12:00:00 AM |

