---
title: Microsoft Intune で変更とイベントを監査する - Azure | Microsoft Docs
description: Microsoft Intune のアクティビティを記録する監査ログを確認する方法について説明します。
keywords: ''
ms.author: dougeby
author: dougeby
manager: dougeby
ms.date: 03/18/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6ee841cc-5694-4ba1-8f66-1d58edec30a4
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: fd00a0ae4cb6c3b150fe40cfc6cd7b71cfa973f3
ms.sourcegitcommit: 0be25b59c8e386f972a855712fc6ec3deccede86
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2019
ms.locfileid: "72585242"
---
# <a name="use-audit-logs-to-track-and-monitor-events-in-microsoft-intune"></a>監査ログを使用し、Microsoft Intune のイベントを追跡し、監視する

監査ログには、Microsoft Intune で変更を行うアクティビティが含まれています。 ほとんどの Intune ワークロードについて管理者が確認できる監査イベントは、作成、更新 (編集)、削除、割り当て、リモートの操作によって作成できます。 既定では、すべてのお客様に対して監査が有効です。 無効にすることはできません。

> [!NOTE]
> 監査イベントは、2017 年 12 月の機能リリースで記録が開始されました。 それ以前のイベントは入手できません。

## <a name="who-can-access-the-data"></a>データにアクセスできるユーザー

次のアクセス許可を持つユーザーが監査ログを確認できます。

- グローバル管理者
- Intune サービス管理者
- **監査データ** - **読み取り**アクセス許可を持つ、Intune ロールに割り当てられた管理者

## <a name="audit-logs-for-intune-workloads"></a>Intune ワークロードの監査ログ

各 Intune ワークロードの監視グループで監査ログを確認できます。

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインします。
2. 監査ログを確認するワークロードを選択します。 たとえば、 **[デバイス]** を選択します。
3. **[監視]** の下で **[監査ログ]** を選択します。

## <a name="route-logs-to-azure-monitor"></a>ログを Azure Monitor にルーティングする

監査ログと操作ログは Azure Monitor に転送することもできます。 **[監査ログ]** で **[データ設定のエクスポート]** を選択します。

![Intune で [データ設定のエクスポート] を選択し、Azure Monitor にログ データをエクスポートします。](./media/monitor-audit-logs/audit-logs-export-data-settings.png)

> [!NOTE]
> この機能の詳細と、それを使用するための前提条件を確認するには、「[ストレージ、イベントハブ、またはログ分析にログデータを送信する](review-logs-using-azure-monitor.md)」を参照してください。

## <a name="review-audit-events"></a>監査イベントの確認

![Intune で監査ログを選択し、イベントが発生したときのアクションと日付を表示する](./media/monitor-audit-logs/monitor-audit-logs.png "監査ログ")

監査ログには、次の項目を表示する既定のリスト ビューがあります。

- 発生した日時
- 開始者 (アクター)
- アプリケーション名
- アクティビティ
- ターゲット
- Category
- 状態

イベントのさらに具体的な情報を見るには、一覧で項目を選択します。

![Intune の監査ログで操作者および操作内容についてさらに具体的な情報を得る](./media/monitor-audit-logs/monitor-audit-log-detail.png "|::ref2::|")

> [!NOTE]
> **開始者 (アクター)** には、タスクの実行者と、実行された場所についての情報が含まれます。 たとえば、Azure portal で Intune のアクティビティを実行する場合、 **[アプリケーション]** には常に **[Microsoft Intune portal extension]\(Microsoft Intune ポータル拡張機能\)** が表示され、 **[アプリケーション ID]** には常に同じ GUID が使用されます。
>
> **[ターゲット]** セクションには、複数のターゲットとその変更されたプロパティが一覧表示されます。  

## <a name="filter-audit-events"></a>監査イベントのフィルター

各ワークロードには、そのウィンドウに関連付けられた監査イベントのカテゴリを事前にフィルターするメニュー項目があります。 別個のフィルター オプションを使用すると、別のカテゴリに変更したり、そのカテゴリ内のイベント アクションの詳細に変更したりできます。 そのアクションを行ったユーザーなどを UPN で検索することができます。 日付範囲フィルターは、24 時間、7 日間、または 30 日間から選べます。 既定では、過去 30 日の監査イベントが表示されます。

## <a name="use-graph-api-to-retrieve-audit-events"></a>Graph API を使用した監査イベントの取得

Graph API を使用した、最長 1 年間の監査イベントを取得に関する詳細については、「[auditEvents のリスト](https://docs.microsoft.com/graph/api/intune-auditing-auditevent-list?view=graph-rest-1.0)」を参照してください。

## <a name="next-steps"></a>次の手順

[Intune でストレージ、イベントハブ、または Log Analytics にログ データを送信する (プレビュー)](review-logs-using-azure-monitor.md)。

[クライアント アプリの保護ログを確認します](../apps/app-protection-policy-settings-log.md)。
