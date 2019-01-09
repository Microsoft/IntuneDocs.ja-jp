---
title: データ ウェアハウス データ モデル
titlesuffix: Microsoft Intune
description: Microsoft Intune データ ウェアハウスは、データを毎日サンプリングし、常に変化するモバイル環境の履歴ビューを提供します。
keywords: Intune データ ウェアハウス
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/20/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4D04D3D9-4B6C-41CD-AAF8-466AF8FA6032
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: ce4689aaecd40d7d44f0064b1e951823fa0bb2c2
ms.sourcegitcommit: 279f923b1802445e501324a262d14e8bfdddabde
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2018
ms.locfileid: "53738003"
---
# <a name="microsoft-intune-data-warehouse-data-model"></a>Microsoft Intune データ ウェアハウスのデータ モデル

Intune データ ウェアハウスは、データを毎日サンプリングし、常に変化するモバイル デバイス環境の履歴ビューを提供します。 ビューは時間に関連のあるエンティティで構成されます。

## <a name="entities-entity-sets"></a>エンティティ:エンティティ セット

このウェアハウスは、次の上位領域のデータを公開します。

  -  アプリ保護が有効なアプリと使用状況
  -  登録済みデバイス、プロパティ、インベントリ
  -  アプリとソフトウェアのインベントリ
  -  デバイスの構成とコンプライアンス ポリシー

これらの領域には、お使いの Intune 環境にとって重要なエンティティが含まれます。 エンティティ セットの詳細については、次の各トピックをご覧ください。

  -  [アプリケーション](reports-ref-application.md)
  -  [日付](reports-ref-date.md)
  -  [デバイス](reports-ref-devices.md)
  -  [Intune の管理拡張](reports-ref-intunemanagementextension.md)
  -  [ポリシー](reports-ref-policy.md)
  -  [モバイル アプリ管理 (MAM)](reports-ref-mobile-app-management.md)
  -  [ユーザー](reports-ref-user.md)
  -  [現在のユーザー](reports-ref-current-user.md)
  -  [ユーザー デバイスの関連付け](reports-ref-user-device.md)

## <a name="relationships-star-schema-model"></a>リレーションシップ:スタースキーマ モデル

このウェアハウスでは、エンティティがリレーションシップに分類されます。リレーションシップは、尋ねる質問の種類に応じたものです。 たとえば、社内で開発された Android アプリケーションのインストールの数を確認できます。 データ ウェアハウスの構造を使用して、モバイル環境を分析できます。 また、Microsoft Power BI などの分析ツールでデータ ウェアハウス データ モデルを使用して、視覚化と動的ダッシュボードを作成できます。

エンティティとリレーションシップは、スタースキーマ モデルを使用します。 スタースキーマは、時間のディメンションを超えてファクトを関連付けます。 モデルのコンテキストで*ファクト*とは、デバイス数、アプリ数、登録時間などの量的単位です。 ファクト テーブルには大量のデータが保存されます。 ファクト テーブルは非常に大きくなる場合があるため、通常、情報が 30 日間に制限されます。 *ディメンション*はファクトにコンテキストを提供します。 ファクトが発生した事象を測定し、ディメンションが誰に対して発生したかを示します。 **ユーザー** テーブルなどのディメンション テーブルは小さくなり、ファクト テーブルよりも長期間データをリトレインできます。 

スタースキーマ モデルは、柔軟性とデータ分析に合わせて最適化されているため、進化するモバイル環境を理解するために必要なレポートを作成できます。

## <a name="time-daily-snapshots"></a>時刻:毎日のスナップショット

このウェアハウスは、Intune データのダウンストリームです。 Intune では、午前 0 時 (UTC) に毎日のスナップショットを取得し、ウェアハウスにスナップショットを保存します。 スナップショットの保有期間はファクト テーブルによって異なります。 7 日間や 30 日間、またはさらに長い期間のものもあります。

## <a name="next-steps"></a>次の手順

 - データ ウェアハウスが Intune のユーザーの有効期間を追跡する方法の詳細については、「[Intune データ ウェアハウスのユーザー有効期間の表記](reports-ref-user-timeline.md)」をご覧ください。
 - データ ウェアハウスの操作に関する詳細については、[最初のデータ ウェアハウスの作成](https://www.codeproject.com/Articles/652108/Create-First-Data-WareHouse)に関するページをご覧ください。
 - Power BI とデータ ウェアハウスの操作の詳細については、[データセットをインポートして新しい Power BI レポートを作成する](https://powerbi.microsoft.com/documentation/powerbi-service-create-a-new-report/)に関するページをご覧ください。 
