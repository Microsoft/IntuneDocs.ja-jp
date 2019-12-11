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
ms.openlocfilehash: d6af0718f2b926383bb943b6321b4d5839346ce7
ms.sourcegitcommit: df8e2c052fafb2d5d4e9b4fcd831ae0ecf7f8d16
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991980"
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

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。
2. [**テナント管理** > **監査ログ**] を選択します。
3. 結果をフィルター処理するには、 **[フィルター]** を選択し、次のオプションを使用して結果を絞り込みます。
    - **カテゴリ**:**コンプライアンス**、**デバイス**、**ロール**など。
    - **アクティビティ**: ここに示されているオプションは、 **[カテゴリ]** で選択したオプションによって制限されます。
    - **[日付範囲]** : 前の月、週、または日のログを選択できます。
4. **[適用]** を選択します。
4. リスト内の項目を選択すると、アクティビティの詳細が表示されます。

## <a name="route-logs-to-azure-monitor"></a>ログを Azure Monitor にルーティングする

監査ログと操作ログは Azure Monitor に転送することもできます。 **[監査ログ]** で **[データ設定のエクスポート]** を選択します。

![Intune で [データ設定のエクスポート] を選択し、Azure Monitor にログ データをエクスポートします。](./media/monitor-audit-logs/audit-logs-export-data-settings.png)

> [!NOTE]
> この機能の詳細と、それを使用するための前提条件を確認するには、「[ストレージ、イベントハブ、またはログ分析にログデータを送信する](review-logs-using-azure-monitor.md)」を参照してください。

> [!NOTE]
> **開始者 (アクター)** には、タスクの実行者と、実行された場所についての情報が含まれます。 たとえば、Azure portal で Intune のアクティビティを実行する場合、 **[アプリケーション]** には常に **[Microsoft Intune portal extension]\(Microsoft Intune ポータル拡張機能\)** が表示され、 **[アプリケーション ID]** には常に同じ GUID が使用されます。
>
> **[ターゲット]** セクションには、複数のターゲットとその変更されたプロパティが一覧表示されます。  

## <a name="use-graph-api-to-retrieve-audit-events"></a>Graph API を使用した監査イベントの取得

Graph API を使用した、最長 1 年間の監査イベントを取得に関する詳細については、「[auditEvents のリスト](https://docs.microsoft.com/graph/api/intune-auditing-auditevent-list?view=graph-rest-1.0)」を参照してください。

## <a name="next-steps"></a>次の手順

[Intune でストレージ、イベントハブ、または Log Analytics にログ データを送信する (プレビュー)](review-logs-using-azure-monitor.md)。

[クライアント アプリの保護ログを確認します](../apps/app-protection-policy-settings-log.md)。
