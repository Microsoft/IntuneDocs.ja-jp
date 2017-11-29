---
title: "データ ウェアハウスのユーザー エンティティ タイムライン | Microsoft Docs"
description: "Intune のデータ ウェアハウスは、タイムライン内のユーザーを表します。"
keywords: "Intune データ ウェアハウス"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 11/14/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 363D148E-688F-4830-B6DE-AB4FE3648817
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: ce43234003da859b81dd499f22f7280db5bda41b
ms.sourcegitcommit: d26930f45ba9e6292a49bcb08defb5b3f14b704b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2017
---
# <a name="user-lifetime-representation-in-the-intune-data-warehouse"></a>Intune データ ウェアハウスのユーザー有効期間の表記

時間ベースの傾向に関する疑問の答えを知るには、Intune データ ウェアハウスに格納されたデータ スナップショットの月を使用することができます。 たとえば、1 か月の間に追加されるユーザーの数を確認できます。 システムから削除されたユーザーの数を知ることもできます。

この情報を提供するために、データ ウェアハウスには履歴情報が格納されています。 すなわち、エンティティの有効期間を追跡することができます。 ウェアハウスでは、エンティティが作成された時、エンティティの状態が変更された時、エンティティが削除された時が記録されます。 毎日の定量的測定のスナップショットでキャプチャされた履歴を使用して、ある 1 日をその前日と比較したりできます。

エンティティの状態は変わっていくため、エンティティの有効期間の取り扱いは複雑になる場合があります。 つまり、30 日目のスナップショットを参照する場合、ユーザー レコードがデータ内でアクティブな状態で存在していない可能性があります。 28 日目と 29 日目には、エンティティ レコードはアクティブで存在している可能性があります。 そして 28 日目より前には、ユーザーはまったく存在していませんでした。

エンティティの有効期間の説明では、このことがわかりやすくなります。

2017 年 6 月 1 日にライセンスを割り当てられる **John Smith** というユーザーがいるとすると、**ユーザー** テーブルには次のエントリが表示されます。 
 
| 表示名 | IsDeleted | StartDateInclusiveUTC | EndDateExclusiveUTC | IsCurrent 
| -- | -- | -- | -- | -- |
| John Smith | FALSE | 06/01/2017 | 12/31/9999 | TRUE
 
John Smith は、2017 年 7 月 25 日に自分のライセンスを破棄します。 **ユーザー** テーブルには次のエントリが表示されます。 既存のレコード中の変更内容は `marked` です。 

| 表示名 | IsDeleted | StartDateInclusiveUTC | EndDateExclusiveUTC | IsCurrent 
| -- | -- | -- | -- | -- |
| John Smith | FALSE | 06/01/2017 | `07/26/2017` | `FALSE` 
| John Smith | TRUE | 07/26/2017 | 12/31/9999 | TRUE 

最初の行は、John Smith が 2017 年 6 月 1 日から 2017 年 7 月 25 日まで Intune に存在していたことを示しています。 2 番目のレコードは、ユーザーが 2017 年 7 月 25 日に削除され、Intune にもう存在していないことを示しています。

2017 年 8 月 31 日に新しいライセンスを割り当てられる John Smith というユーザーがいるとすると、ユーザー テーブルには次のエントリが表示されます。
 
| 表示名 | IsDeleted | StartDateInclusiveUTC | EndDateExclusiveUTC | IsCurrent 
| -- | -- | -- | -- | -- |
| John Smith | FALSE | 06/01/2017 | 07/26/2017 | FALSE 
| John Smith | TRUE | 07/26/2017 | `08/31/2017` | `FALSE` 
| John Smith | FALSE | 08/31/2017 | 12/31/9999 | TRUE 
 
すべてのユーザーの現在の状態を確認する場合は、`IsCurrent = TRUE` を使用するフィルターを適用します。 
 
存在しているユーザーのみを確認する場合は、`IsCurrent = TRUE AND IsDeleted = FALSE` を使用するフィルターを適用します。

## <a name="dimension-tables-in-the-entity-lifetime"></a>エンティティの有効期間のディメンション テーブル

エンティティの状態の変更履歴を格納するため、Intune はレコードを削除しません。 代わりに、レコードを削除済みとしてマークします。 これは、ソフト削除と呼ばれます。 ディメンション テーブルでは、さまざまなメタデータ列を使用して、レコードの有効期間を追跡します。 

最もよく使用されるメタデータ列は次のとおりです。 

| メタデータ プロパティ名  | 値の意味 |
|--|--|
| IsDeleted | Intune で、エンティティが削除されたかどうかを示します。 |
| StartDateInclusiveUTC  | エンティティが Intune データ ウェアハウスに読み込まれたときの UTC 日付。 エンティティは、Intune データ ウェアハウスにインポートされる前に作成されている可能性があります。 |
| DeletedDateUTC  | Intune でエンティティが削除されたときの UTC 日付。 |  

プレフィックス **Row** で始まるすべてのメタデータ列 (**RowLastModifiedDateTimeUTC** など) は、Intune データ ウェアハウスでレコードが作成または変更された時を示します。 ウェアハウスは、Intune 内のデータに対してダウンストリームです。 この値には、Intune でのエンティティの有効期間との関係はありません。  
 
現在存在するディメンション エンティティのみを確認する場合は、**IsDeleted = FALSE** を使用するフィルターを適用します。

## <a name="next-steps"></a>次のステップ

 - **現在のユーザー** エンティティの詳細については、「[現在のユーザー エンティティのリファレンス](reports-ref-current-user.md)」をご覧ください。
 - **ユーザー** エンティティの詳細については、「[ユーザー エンティティのリファレンス](reports-ref-user.md)」をご覧ください。