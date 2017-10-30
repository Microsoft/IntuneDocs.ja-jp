---
title: "データ ウェアハウス データ モデル | Microsoft Docs"
description: "Intune データ ウェアハウスは、データを毎日サンプリングし、常に変化するモバイル環境の履歴ビューを提供します。"
keywords: "Intune データ ウェアハウス"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4D04D3D9-4B6C-41CD-AAF8-466AF8FA6032
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d52e240763263ac4f761a8635ee6694a45168354
ms.sourcegitcommit: bb2c181fd6de929cf1e5d3856e048d617eb72063
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/20/2017
---
# <a name="data-warehouse-data-model"></a>データ ウェアハウス データ モデル

Intune データ ウェアハウスは、データを毎日サンプリングし、常に変化するモバイル環境の履歴ビューを提供します。

テナントから取得したデータは、データ ウェアハウスに追加されます。 ウェアハウスは、知りたい問題の種類に利用できるエンティティとリレーションシップのセットです。 たとえば、社内で開発した Android アプリケーションの 1 日のインストール数を過去 1 週間分確認し、インストール数の増加傾向があるかどうかを評価できます。 データ ウェアハウスの構造を使用して、モバイル環境を分析できます。 また、Microsoft Power BI などの分析ツールでデータ ウェアハウス データ モデルを使用して、視覚化と動的ダッシュボードを作成できます。

Intune データ ウェアハウス構造では、スタースキーマ モデルを使用します。 スタースキーマは、時間のディメンションでファクトを整理します。 モデルのコンテキストで*ファクト*とは、デバイス数、アプリ数、登録時間などの量的単位です。 モデルのコンテキストで*ディメンション*とは、カテゴリとその階層関係のセットです。 たとえば、日は月にグループ化され、月は年にグループ化されます。 スタースキーマ モデルは、柔軟性とデータ分析に合わせて最適化されているため、進化するモバイル環境を理解するために必要なレポートを作成できます。

ウェアハウスは、次の上位カテゴリでデータを公開します。
  -  アプリ保護が有効なアプリと使用状況
  -  登録済みデバイス、プロパティ、インベントリ
  -  アプリとソフトウェアのインベントリ
  -  デバイスの構成とコンプライアンス ポリシー

**データ モデルのエンティティ セット**

エンティティ セットは、データ モデル内にあるエンティティの名前付きコレクションです。 これらのセットには、モデルで収集されたデータを定義するエンティティが含まれています。 各エンティティ セットには、データ ウェアハウス データ モデルへのアクセス ポイントがあります。 エンティティの各カテゴリの詳細については、以下の各リンクを参照してください。

  -  [日付](reports-ref-date.md)
  -  [ユーザー](reports-ref-user.md)
  -  [モバイル アプリ管理 (MAM)](reports-ref-mobile-app-management.md)
  -  [デバイス](reports-ref-devices.md)
  -  [アプリケーション](reports-ref-application.md)
  -  [ポリシー](reports-ref-policy.md)
  -  [ユーザー デバイスの関連付け](reports-ref-userdeviceassociations.md)

<!-- ## Data Model relationships

For more information on the relationships in the data model, see [Relationships of Entities](reports-api-entity-relationships.md). -->