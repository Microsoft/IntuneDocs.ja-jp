---
title: Intune 移行キャンペーンを開始する
titleSuffix: Microsoft Intune
description: この記事では、Microsoft Intune の移行キャンペーンの開始方法に関するガイダンスを提供します。
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f781b029-50f2-46ee-8ff7-03b4a6719e80
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: db56bbc180a84e8b3972ffc6473126efd366faa8
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61508191"
---
# <a name="phase-2-migration-campaign"></a>フェーズ 2:移行のキャンペーン

組織のニーズに最適な移行アプローチを選択し、組織固有の要件に基づいて導入戦略を調整します。 このガイドの残りの部分では、ユーザーのデバイスを Intune に登録するという目標を達成するために必要な手段について説明します。

## <a name="keys-to-a-successful-migration"></a>移行を成功させるカギ

サード パーティの MDM プロバイダーから Intune への移行を成功させるには、以下のことが重要です。

-   明確で有益な通信は、エンドユーザーのダウンタイムと不満足を最小限に抑えるのに役立ちます。

-   個別的かつ具体的な移行指示を行うようにします。

-   Intune に登録する前に、すべてのマネージド デバイスを既存の MDM プロバイダーから登録解除する必要があります。

-   デバイスの登録解除の方法については、既存の MDM プロバイダーからのガイダンスをエンド ユーザーに提供します。

-   段階的なアプローチを使用します。 パイロット ユーザーで構成された小規模なグループで開始して、全面的な展開に達するまで段階的にユーザー グループを追加していきます。

-   各サイクルで、ヘルプ デスクの負荷と登録の完了を監視します。 スケジュールに余裕を持たせ、各グループの成功基準を評価してから次のグループで移行を開始するようにします。 パイロット展開では次の点を検証する必要があります。

    -   登録の成功率と失敗率が想定内であること。

    -   ユーザーの生産性:

        -   VPN、Wi-Fi、電子メール、および証明書などの会社のリソースが機能している。

        -   プロビジョニング済みのアプリにアクセスできる。

    -   データ セキュリティ:

        -   コンプライアンス レポートが行われる。

        -   モバイル アプリ保護が適用される。

移行の最初のフェーズに満足したら、次のフェーズの[移行サイクル](migration-guide-cycle.md)を繰り返します。

-   すべてのユーザーが Intune に移行するまで、段階的なサイクルを繰り返します。

-   移行キャンペーン中に、ヘルプ デスク チームがエンド ユーザーに対応できているか確認します。 サポート コールのワークロードを見積もることができるまでは、自主的な移行を実施します。

-   ヘルプ デスクが残りのユーザーに対応できるまでは、登録期限を設定しないようにします。

> [!IMPORTANT]
> Exchange や SharePoint Online などのリソースへのアクセス制御を適用するために、Intune と既存のサードパーティ MDM ソリューションの両方を構成しないでください。 また、同時に複数のソリューションにデバイスを登録しないでください。

## <a name="next-steps"></a>次の手順

[情報伝達計画](migration-guide-communication-plan.md)を作成します。
