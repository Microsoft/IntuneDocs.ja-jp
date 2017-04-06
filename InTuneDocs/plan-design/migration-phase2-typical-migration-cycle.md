---
title: "標準的な Intune 移行サイクルのしくみ | Microsoft Docs"
description: "この記事では、Intune 移行サイクルのしくみを説明し、移行サイクルの対応方法の例を示します。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3688b724-9521-4210-bf4d-bcf47d8d4ca0
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: ab5aa4e12d951d818c5afb4e1ac5e866b05733fb
ms.openlocfilehash: aa8fb215772b6e8d3a913d929c030d68e363970b
ms.lasthandoff: 03/27/2017


---

# <a name="phase-2-typical-migration-cycle"></a>フェーズ 2: 標準的な移行サイクル

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

通常、組織は、IT 部門の一部のユーザーを対象とした、小規模なパイロットで Intune 移行を開始します。 また、組織で変更に対するグループの意志、ユーザー数、複雑さ、要件、場所、およびビジネス上のリスクなどの要因について話し合い、移行期間の決定に役立てる必要があります。

対象グループのスケジュール例を次に示します。

  | **移行対象グループ** | **期間 1** | **期間 2** | **期間 3** | **期間 4** | **...**
|:---:|:---:|:---:|:---:|:---:|:---:|
| 限定パイロット運用の IT 部門 (50 ユーザー) | 計画の発表 | 登録の指示 | 期限の設定 | 条件付きアクセスを強制的に適用 |  |                                                        
| 拡張パイロット運用の IT 部門 (200 ユーザー) |  | 計画の発表 | 登録の指示 | 期限の設定 | 条件付きアクセスを強制的に適用 | 
| 移行フェーズ 1 技術に精通したユーザー (2000人) |  |  | 計画の発表 | 登録の指示 | 期限の設定 | 
| 移行フェーズ 2 米国東部 |  |  |  | 計画の発表 | 登録の指示 | 
| すべての地域 |  |  |  |  | 計画の発表 | 

## <a name="customer-migration-case-study"></a>お客様の移行のケース スタディ

### <a name="adatum-corporation"></a>Adatum Corporation

- [Adatum Corporation のサード パーティ MDM プロバイダーから Intune への移行プロセス](https://gallery.technet.microsoft.com/Intune-migration-guide-893a95e3?redir=0)をご覧ください。

## <a name="monitoring-migration"></a>移行の監視

Microsoft Intune は、移行を監視する方法をいくつか用意しています。

1.  Intune ユーザー グループのビュー

2.  組み込みレポートのセット

3.  コンソール内のアラート

各フェーズ後にデバイスを登録したユーザー数を追跡することで、次のことができます。

-   情報伝達計画の効果を評価する。

-   条件付きアクセスの強制的な適用の影響を評価する。

Intune 移行の監視方法は、[こちら](https://docs.microsoft.com/intune/deploy-use/understand-microsoft-intune-operations-by-using-reports)を参照してください。

## <a name="post-migration"></a>Post-migration

Intune への移行後に、以前の MDM プロバイダーをインベントリから削除したり、サービスの購読を解除する必要があります。 また、MDM プロバイダーの指示に従って、不要なインフラストラクチャの要件を削除する必要があります。

