---
title: Intune モバイル デバイス管理の移行ガイド
titlesuffix: Microsoft Intune
description: このガイドは、サードパーティの MDM プロバイダーからの Microsoft Intune への移行に関連したさまざまな詳細情報を説明します。
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: dcfc21f9-1bcd-4371-a46d-f2e18154ec50
ms.reviewer: dagerrit
ms.suite: ems
ms.openlocfilehash: 9bfefff2ef5960b6e52a8a37c2fd31466d16cbff
ms.sourcegitcommit: e30fb2375fb79f67e5c1e4ed7b2c21fb9ca80c59
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/17/2018
ms.locfileid: "29960969"
---
# <a name="intune-migration-guide"></a>Intune 移行ガイド

![Microsoft Intune MDM 移行ガイド図](./media/MDM-migration-guide-art.PNG)

Microsoft Intune への移行を成功させるには、まず現在のモバイル デバイス管理 (MDM) 環境、ビジネスの目標、および技術面の要件を考慮した、しっかりした計画を立てる必要があります。 また、移行計画を支援し協力する関係者を含めることも重要です。

このガイドは、サードパーティの MDM プロバイダーからの Intune への移行に関連したさまざまな詳細情報を説明します。

## <a name="whats-included-in-this-guide"></a>このガイドに含まれるもの

このガイドは移行を 2 つのフェーズに分けます。各フェーズには、Intune MDM への移行プロセス全体を理解するうえで役立つタスク、戦略、および戦術的ガイダンスが含まれます。

-   [フェーズ 1: モバイル デバイス管理の Intune を準備する](migration-guide-prepare.md)

    -   [MDM 移行要件を評価する](migration-guide-prepare.md#assess-mdm-requirements)

    -   [基本的なセットアップ](migration-guide-setup.md)

    -   [デバイスおよびアプリ管理のポリシー](migration-guide-configure-policies.md)

    -   [アプリ保護ポリシーの構成](migration-guide-app-protection-policies.md)

    -   [特殊な移行に関する考慮事項](migration-guide-considerations.md)

-   [フェーズ 2: 移行のキャンペーン](migration-guide-campaign.md)

    -   [情報伝達計画](migration-guide-communication-plan.md)

    -   [条件付きアクセスでエンド ユーザーの導入を推進する](migration-guide-drive-adoption.md)

    -   [標準的な移行サイクル](migration-guide-cycle.md)
        -   [移行の監視](migration-guide-cycle.md#monitoring-migration)
        -   [移行後](migration-guide-cycle.md#post-migration)

## <a name="assumptions"></a>前提条件

-   概念実証 (PoC) 環境で既に Intune を評価し、組織で MDM ソリューションとして使用することを決定している。

-   Intune とその機能について、既によく理解している。

## <a name="before-you-begin"></a>始める前に

新しい Intune 展開は、以前の MDM 展開とは異なる可能性があることを認識することが重要です。 従来の MDM サービスとは異なり、Intune では ID ドリブンのアクセス制御に重点を置いているため、組織のネットワーク境界外で使用されるモバイル デバイスから企業データへのアクセスを制御するネットワーク プロキシ アプライアンスは不要です。 Microsoft は、密接に統合されたクラウド サービス スイートである "Enterprise Mobility + Security" を通じて、クラウド内のデータ サービスを保護するソリューションを提供します。

-   [Intune の一般的な使用方法](common-scenarios.md)を確認してください。

## <a name="next-steps"></a>次の手順

[フェーズ 1: モバイル デバイス管理の Intune を準備する](migration-guide-prepare.md)
