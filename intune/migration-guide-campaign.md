---
title: "Intune 移行キャンペーンを開始する"
description: "この記事では、移行キャンペーンを開始する方法について説明します。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f781b029-50f2-46ee-8ff7-03b4a6719e80
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9690572fd5f17fece0de7b533c98bfc52d77615b
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2017
---
# <a name="phase-2-migration-campaign"></a>フェーズ 2: 移行のキャンペーン

[!INCLUDE[note for both-portals](./includes/note-for-both-portals.md)]

組織では、ニーズに最適な移行アプローチを取り、組織固有の要件に基づいて導入戦略を調整する必要があります。 このガイドの残りの部分では、ユーザーのデバイスを Intune に登録するという目標を達成するために必要な手段について説明します。

## <a name="keys-to-a-successful-migration"></a>移行を成功させるカギ

サードパーティの MDM プロバイダーから Intune への移行時に得られた主な教訓は次のとおりです。

-   エンド ユーザーのダウンタイムを最小限に抑えつつ、満足度を向上させるカギは情報伝達です。

-   個別的かつ具体的な移行指示を行うようにします。

-   Intune に登録する前に、すべての管理対象デバイスを既存の MDM プロバイダーから登録解除する必要があります。

-   デバイスの登録解除の方法については、既存の MDM プロバイダーからのガイダンスをエンド ユーザーに提供します。

-   段階的なアプローチを使用します。 パイロット ユーザーで構成された小規模なグループで開始して、全面的な展開に達するまで段階的にユーザー グループを追加していきます。

-   各サイクルで、ヘルプ デスクの負荷と登録の完了を監視します。 スケジュールに余裕を持たせ、各グループの成功基準を評価してから次のグループで移行を開始するようにします。 パイロット展開では次の点を検証する必要があります。

    -   登録の成功率と失敗率が想定内であること。

    -   ユーザーの生産性:

        -   VPN、Wi-Fi、電子メール、および証明書などの会社のリソースが機能している。

        -   プロビジョニング済みのアプリにアクセスできる。

    -   データ セキュリティ:

        -   コンプライアンス対応レポート

        -   モバイル アプリ保護の適用

-   移行の最初のフェーズに満足したら、次のフェーズの移行サイクル (「標準的な移行サイクル」の下のところで説明しています) を繰り返します。

-   すべてのユーザーが Intune に移行するまで、段階的なサイクルを繰り返します。

-   移行キャンペーン中に、ヘルプ デスク チームがエンド ユーザーに対応できているか確認します。 サポート コールのワークロードを見積もることができるまでは、自主的な移行を実施します。

-   ヘルプ デスクが残りのユーザーに対応できるまでは、登録期限を設定しないようにします。

> [!IMPORTANT] 
> Exchange や SharePoint Online などのリソースへのアクセス制御を適用するために、Intune と既存のサードパーティ MDM ソリューションの両方を構成しないでください。 また、同時に複数のソリューションにデバイスを登録しないでください。

## <a name="next-steps"></a>次のステップ

[情報伝達計画](migration-guide-communication-plan.md)
