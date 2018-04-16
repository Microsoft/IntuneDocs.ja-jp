---
title: Intune Mobile Threat Defense
description: "デバイスのリスクに基づいて、会社のリソースへのアクセスを保護します。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/01/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 08d87906-8158-4d5e-a49d-ad919efef3d1
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 97711301422dd86ed0a76375add54987809c07b7
ms.sourcegitcommit: 2459bfda07a2afd2cfcd94a1972a3fb2e565ce8d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/22/2018
---
# <a name="intune-mobile-threat-defense-connectors"></a>Intune Mobile Threat Defense コネクター

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Intune Mobile Threat Defense コネクターを使用すると、選択した Mobile Threat Defense ベンダーをコンプライアンス ポリシーと条件付きアクセス規則の情報ソースとして活用できます。 これにより、IT 管理者が、具体的に危険にさらさモバイル デバイスから、Exchange、Sharepoint などの企業リソースに保護レイヤーを追加することができます。

## <a name="what-problem-does-this-solve"></a>これはどのような問題を解決しますか。

会社は物理的な脅威、アプリ ベースの脅威、ネットワーク ベースの脅威などの新種の脅威やオペレーティング システムの脆弱性から機密データを守る必要があります。
これまで、企業は PC の防御を積極的に行ってきましたが、モバイル デバイスは監視や保護のない状態が続いています。 モバイル プラットフォームには、アプリの分離や検証済みコンシューマー アプリ ストアなどの防御手法が組み込まれていますが、依然として高度な攻撃を受けやすい状態にあります。 現在、モバイル デバイスを仕事に利用し、機密情報にアクセスする社員が増えています。 増え続ける高度な攻撃からモバイル デバイスを守る必要があります。

## <a name="how-the-intune-mobile-threat-defense-connectors-work"></a>Intune Mobile Threat Defense コネクターのしくみ

このコネクターは、Intune と選択した Mobile Threat Defense ベンダーの間の通信チャネルを作成することで、会社のリソースを保護します。 Intune Mobile Threat Defense パートナーは、直感的で簡単に展開できるモバイル デバイス向けアプリケーションを提供します。これらのアプリケーションは、脅威情報を積極的にスキャンして分析し、レポートや強制を目的として Intune と共有します。 たとえば、Mobile Threat Defense アプリが、電話またはネットワークが Man in the Middle 攻撃に対して脆弱なネットワークに接続されていることを Mobile Threat Defense ベンダーに報告した場合、この情報は共有されて適切なリスク レベル (低/中/高) に分類されます。その後、Intune で構成済みのリスク レベル許容度と比較されて、デバイスが侵害されたときに選択した特定のリソースへのアクセスを無効にする必要があるかどうかが判断されます。

## <a name="sample-scenarios"></a>サンプル事例

Mobile Threat Defense ソリューションによってデバイスが感染したと見なされた場合

![Mobile Threat Defense と感染しているデバイス](../media/mtp/MTD-image-1.png)

デバイスが修復されたときにアクセスが許可されます。

![Mobile Threat Defense とアクセス付与](../media/mtp/MTD-image-2.png)

## <a name="mobile-threat-defense-partners"></a>Mobile Threat Defense パートナー

デバイス、ネットワーク、アプリケーションのリスクに基づいて、会社のリソースへのアクセスを保護する方法について説明します。次のものを使用します。

- [Lookout](/intune-classic/deploy-use/lookout-mobile-threat-defense-connector)
- [Skycure](/intune-classic/deploy-use/skycure-mobile-threat-defense-connector)
