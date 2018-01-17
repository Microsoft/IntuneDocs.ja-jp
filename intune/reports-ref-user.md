---
title: "ユーザー - Intune データ ウェアハウス | Microsoft Docs"
description: "Intune データ ウェアハウス API のエンティティ コレクションのユーザー カテゴリに関するリファレンス トピック。"
keywords: "Intune データ ウェアハウス"
author: erikre
ms.author: erikre
manager: angrobe
ms.date: 12/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: C29A6EEA-72B7-427E-9601-E05B408F3BB0
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 917c9585ffe17f9d090c519f716d284aa1b932b8
ms.sourcegitcommit: b2467a653ffd36c2248a30b69cb88e3dc7cca2ed
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/14/2017
---
# <a name="reference-for-user-entity"></a>User エンティティのリファレンス

**ユーザー** カテゴリには、データ モデルのユーザーのプロパティを定義する **User** エンティティが含まれています。

## <a name="user"></a>User

**User** エンティティには、社内のすべての Azure Active Directory (Azure AD) ユーザーと割り当てられているライセンスが表示されます。

**User** エンティティ コレクションにはユーザー データが含まれています。 これらのレコードには、ユーザーが削除されている場合でも、データ コレクション期間中のユーザーの状態が含まれます。 たとえば、ユーザーが Intune に追加され、過去 1 か月の過程で削除されたとします。 このユーザーがレポートの時点では存在しない一方で、ユーザーと状態は先月のデータに存在します。 データ内のユーザーの履歴における存在の期間を示すレポートを作成できます。

| プロパティ  | 説明 | 例 |
|---------|------------|--------|
| UserKey |データ ウェアハウス内のユーザーを示す一意識別子 - 代理キー。 |123 |
| UserId |ユーザーを示す一意識別子 - UserKey と似ていますが、ナチュラル キーです。 |b66bc706-ffff-7437-0340-032819502773 |
| UserEmail |ユーザーの電子メール アドレス。 |John@constoso.com |
| UPN | ユーザーのユーザー プリンシパル名。 | John@constoso.com |
| 表示名 |ユーザーの表示名。 |John |
| IntuneLicensed |ユーザーに Intune のライセンスがあるかどうかを示します。 |真/偽 |
| IsDeleted | そのユーザーのすべてのライセンスの期限が切れているかどうか、および、そのユーザーがそのため Intune から削除されたかどうかを示します。 1 つのレコードでは、このフラグは変更されません。 代わりに、新しいユーザー状態用の新しいレコードが作成されます。 |真/偽 |
| StartDateInclusiveUTC |IsDeleted = FALSE の場合、ユーザーがライセンスを割り当てられ、Intune で存在し始めたときの UTC 日時。 IsDeleted = TRUE の場合、ユーザーのライセンスの期限が切れ、Intune から削除されたときの UTC 日時。 |11/23/2016 12:00:00 AM |
| EndDateExclusiveUTC |IsDeleted = FALSE の場合、ユーザーのライセンスの期限が切れ、Intune から削除されたときの UTC 日時。 ライセンスは、前日のどこかの時点で期限が切れました。 IsDeleted = TRUE の場合、ユーザーが新しいライセンスを再取得し、Intune で再作成されたときの UTC 日時。  |11/23/2016 12:00:00 AM |
| IsCurrent |このレコードがユーザーの最新の状態を表しているかどうかを示します。 1 人のユーザーに対し複数のレコードが存在している場合がありますが、現在の状態を表すものは 1 つだけです。  |真/偽 |
| RowLastModifiedDateTimeUTC |レコードがデータ ウェアハウスで最後に変更されたときの UTC 日時  |11/23/2016 12:00:00 AM |

## <a name="next-steps"></a>次の手順
 - **現在のユーザー** エンティティ コレクションを使用して、現在アクティブなユーザーにユーザー データを制限することができます。 詳細については、「[現在のユーザー エンティティのリファレンス](reports-ref-current-user.md)」をご覧ください。
 - データ ウェアハウスで Intune のユーザーの有効期間を追跡する方法の詳細については、「[Intune データ ウェアハウスのユーザー有効期間の表記](reports-ref-user-timeline.md)」をご覧ください。
