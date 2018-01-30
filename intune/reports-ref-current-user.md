---
title: "現在のユーザー - Intune データ ウェアハウス | Microsoft Docs"
description: "Intune データ ウェアハウス API のエンティティ コレクションのユーザー カテゴリに関するリファレンス トピック。"
keywords: "Intune データ ウェアハウス"
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 12/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: C10E6752-E925-40AD-ABBF-6B621FB7AFC4
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d25825910e878d428bde72414c4bbee2d5092a89
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="reference-for-current-user-entity"></a>現在のユーザー エンティティのリファレンス

**現在のユーザー** カテゴリには、データ モデルのユーザー プロパティが含まれています。 **現在のユーザー** エンティティ コレクションは、現在アクティブなユーザーに限られています。 エンティティには、現在ライセンスが割り当てられているすべての Azure Active Directory ユーザーが含まれています。 ライセンスは、Intune ライセンス、ハイブリッド ライセンス、または Microsoft Office 365 ライセンスです。 ユーザーは削除されると、現在のユーザー コレクションに表示されなくなります。 ユーザー状態の変更の履歴を含むコレクションについては、「[ユーザー エンティティのリファレンス](reports-ref-user.md)」をご覧ください。


## <a name="current-user"></a>現在のユーザー

**Current User** エンティティには、社内のすべての Azure Active Directory (Azure AD) ユーザーと、割り当てられているライセンスが表示されます。

| プロパティ  | 説明 | 例 |
|---------|------------|--------|
| UserKey |データ ウェアハウス内のユーザーを示す一意識別子 - 代理キー。 |123 |
| UserId |ユーザーを示す一意識別子 - UserKey と似ていますが、ナチュラル キーです。 |b66bc706-ffff-7437-0340-032819502773 |
| UserEmail |ユーザーの電子メール アドレス。 |John@constoso.com |
| UPN | ユーザーのユーザー プリンシパル名。 | John@constoso.com |
| 表示名 |ユーザーの表示名。 |John |
| IntuneLicensed |ユーザーに Intune のライセンスがあるかどうかを示します。 |真/偽 |
| StartDateInclusiveUTC |このユーザーがデータ ウェアハウスで作成されたときの UTC 日時。 |11/23/2016 12:00:00 AM |
| RowLastModifiedDateTimeUTC |このユーザーがデータ ウェアハウスで最後に変更されたときの UTC 日時。 |11/23/2016 12:00:00 AM |

## <a name="next-steps"></a>次の手順
 - **ユーザー** エンティティ コレクションを使用して、ユーザー データを現在アクティブでないユーザーにまで拡張できます。 詳細については、「[ユーザー エンティティのリファレンス](reports-ref-user.md)」をご覧ください。
 - データ ウェアハウスが Intune のユーザーの有効期間を追跡する方法の詳細については、「[Intune データ ウェアハウスのユーザー有効期間の表記](reports-ref-user-timeline.md)」をご覧ください。
