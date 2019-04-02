---
title: 変更と Microsoft Intune - Azure でのイベントの監査 |Microsoft Docs
description: Microsoft Intune のアクティビティを記録する監査ログを確認する方法について説明します。
keywords: ''
ms.author: dougeby
author: dougeby
manager: dougeby
ms.date: 03/18/2019
ms.topic: troubleshooting
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6ee841cc-5694-4ba1-8f66-1d58edec30a4
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 93072ba4730de0252f54d93fa1169062d496ce38
ms.sourcegitcommit: 1069b3b1ed593c94af725300aafd52610c7d8f04
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2019
ms.locfileid: "58394903"
---
# <a name="use-audit-logs-to-track-and-monitor-events-in-microsoft-intune"></a>監査ログを使用して追跡し、Microsoft Intune でのイベントを監視するには

監査ログには、Microsoft Intune で変更を行うアクティビティが含まれています。 作成、更新 (編集)、削除、割り当て、およびリモートの操作はすべて Intune ワークロードのほとんどの管理者が確認できるイベントの監査を作成します。 既定では、すべてのお客様の監査が有効です。 無効にすることはできません。

> [!NOTE]
> 監査イベントは、2017 年 12 月の機能のリリースでの記録を開始します。 前のイベントを使用できません。

## <a name="who-can-access-the-data"></a>データにアクセスできるユーザー

次のアクセス許可を持つユーザーが監査ログを確認できます。

- グローバル管理者
- Intune サービス管理者
- **監査データ** - **読み取り**アクセス許可を持つ、Intune ロールに割り当てられた管理者

## <a name="audit-logs-for-intune-workloads"></a>Intune ワークロードの監査ログ

各 Intune ワークロードの監視グループで監査ログを確認できます。

1. [Azure portal](https://portal.azure.com/) で、**[すべてのサービス]** を選択し、**Intune** でフィルター処理して、**[Intune]** を選択します。
2. 監査ログを確認するワークロードを選択します。 たとえば、**デバイス**します。
3. **監視**、選択**監査ログ**します。

## <a name="route-logs-to-azure-monitor"></a>ログを Azure Monitor にルーティングする

Azure Monitor には、監査ログと運用ログをルーティングすることもできます。 **監査ログ**、**データ設定のエクスポート**:

![ログ データを Azure にエクスポートします Intune でのデータ設定のエクスポートを選択してモニター。](./media/audit-logs-export-data-settings.png)

この機能について詳しくは、[ストレージ、イベント ハブ、またはログ分析へのログ データの送信](review-logs-using-azure-monitor.md)に関する記事をご覧ください。

## <a name="review-audit-events"></a>監査イベントの確認

![アクションとイベントが発生したときの日付を表示するために Intune での監査ログの選択](./media/monitor-audit-logs.png "監査ログ")

監査ログには、次の項目を表示する既定のリスト ビューがあります。

- 発生した日時
- 開始者 (アクター)
- アプリケーション名
- アクティビティ
- ターゲット
- Category
- 状態

イベントに関する詳細情報を表示するには、一覧で項目を選択します。

![Intune でログに監査を行ったかに関する具体的な情報を取得](./media/monitor-audit-log-detail.png "監査ログの詳細")

> [!NOTE]
> **開始者 (アクター)** タスクを実行したユーザーで実行された情報が含まれます。 たとえば、Azure portal で Intune のアクティビティを実行する場合、**[アプリケーション]** には常に **[Microsoft Intune portal extension]\(Microsoft Intune ポータル拡張機能\)** が表示され、**[アプリケーション ID]** には常に同じ GUID が使用されます。
> 
> **[ターゲット]** セクションには、複数のターゲットとその変更されたプロパティが一覧表示されます。  

## <a name="filter-audit-events"></a>監査イベントのフィルター

各ワークロードには、そのウィンドウに関連付けられた監査イベントのカテゴリを事前にフィルターするメニュー項目があります。 別個のフィルター オプションを使用すると、別のカテゴリに変更したり、そのカテゴリ内のイベント アクションの詳細に変更したりできます。 アクションを行ったユーザーなど、UPN で検索できます。 日付範囲フィルターは、24 時間、7 日間、または 30 日間から選べます。 既定では、過去 30 日の監査イベントが表示されます。

## <a name="use-graph-api-to-retrieve-audit-events"></a>Graph API を使用した監査イベントの取得

Graph API を使用して、1 年間の監査イベントを取得する方法の詳細については、次を参照してください。 [auditEvents の一覧を表示](https://docs.microsoft.com/graph/api/intune-auditing-auditevent-list?view=graph-rest-1.0)します。

## <a name="next-steps"></a>次の手順

[ストレージ、event hubs にログ データを送信またはログ分析](review-logs-using-azure-monitor.md)します。

[クライアント アプリの保護ログを確認します](app-protection-policy-settings-log.md)。
