---
title: Microsoft Intune のアクティビティの監査ログ
description: Microsoft Intune のアクティビティを記録する監査ログを確認する方法について説明します。
keywords: ''
ms.author: dougeby
author: dougeby
manager: dougeby
ms.date: 02/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6ee841cc-5694-4ba1-8f66-1d58edec30a4
search.appverid: MET150
ms.openlocfilehash: d9ecfa44e2619e5e123c9e8af169b6a8a95ee466
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2018
ms.locfileid: "52183895"
---
# <a name="audit-logs-for-intune-activities"></a>Intune のアクティビティの監査ログ
監査ログには、Microsoft Intune で変更を行うアクティビティが記録されます。 作成、更新 (編集)、削除、割り当ての操作またはリモート タスクが実行されると、確認可能な監査イベントが生成されます。 Intune ワークロードの監査ログの大半を確認できます。 すべてのユーザーは既定で監査が有効になっています。無効にすることはできません。 監査イベントは、2017 年 12 月の機能リリース日から記録が開始されました。これよりも前の監査イベントは利用できません。

## <a name="who-can-access-the-data"></a>データにアクセスできるユーザー
次のアクセス許可を持つユーザーが監査ログを確認できます。
- グローバル管理者
- Intune サービス管理者
- **監査データ** - **読み取り**アクセス許可を持つ、Intune ロールに割り当てられた管理者

## <a name="audit-logs-for-intune-workloads"></a>Intune ワークロードの監査ログ
各 Intune ワークロードの監視グループで監査ログを確認できます。  
1. [Azure ポータル](https://portal.azure.com) にサインインします。
2. **すべてのサービス** > **Intune** の順に選択します。 Intune は **[監視 + 管理]** セクションにあります。
3. **[Intune]** ウィンドウで、**[デバイス]** などの監査ログを確認するワークロードを選択します。
4. ワークロードの**監視**グループで、**[監査ログ]** を選択します。

## <a name="review-audit-events"></a>監査イベントの確認
![監査ログ](./media/monitor-audit-logs.png "監査ログ")

監査ログには、次の項目を表示する既定のリスト ビューがあります。    

- イベントが発生した日時
- 開始者 (アクター)
- アプリケーション名
- アクティビティ
- ターゲット
- Category
- 状態

リスト ビュー内の項目をクリックすると、それに関するすべての利用可能な詳細が表示されます。

![監査ログ](./media/monitor-audit-log-detail.png "監査ログ")

> [!Note]    
> 監査ログの詳細の **[開始者 (アクター)]** セクションには、アクティビティを実行したユーザーとアクティビティが実行された場所に関する情報が表示されます。 たとえば、Azure Portal で Intune のアクティビティを実行した場合、**[アプリケーション]** には常に "**Microsoft Intune ポータル拡張機能**" が表示され、**[アプリケーション ID]** には常に同じ GUID が使用されます。 
>    
> **[ターゲット]** セクションには、複数のターゲットとその変更されたプロパティを表示できます。  


## <a name="filter-audit-events"></a>監査イベントのフィルター
各ワークロードには、そのウィンドウに関連付けられた監査イベントのカテゴリを事前にフィルターするメニュー項目があります。 別個のフィルター オプションを使用すると、別のカテゴリに変更したり、そのカテゴリ内のイベント アクションの詳細に変更したりできます。 UPN (そのアクションを行ったユーザーなど) で検索することができます。 日付範囲フィルターは、24 時間、7 日間、または 30 日間から選べます。 既定では、過去 30 日の監査イベントが表示されます。

## <a name="use-graph-api-to-retrieve-audit-events"></a>Graph API を使用した監査イベントの取得
Graph API を使用して、最長 1 年間の監査イベントを取得する方法の詳細については、「[List auditEvents (auditEvents の一覧)](https://developer.microsoft.com/en-us/graph/docs/api-reference/beta/api/intune_auditing_auditevent_list)」をご覧ください。