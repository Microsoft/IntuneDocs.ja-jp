---
title: "Mobile Threat Defense と Intune"
titleSuffix: Azure portal
description: "デバイスのリスクに基づいて、会社のリソースへのアクセスを保護します"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 11/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ac77b590-a7ec-45a0-9516-ebf5243b6210
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 16402b30895e61d9a4ff8393fd4d4c6efa061e9e
ms.sourcegitcommit: 520eb7712625e129b781e2f2b9fe16f9b9f3d08a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2017
---
# <a name="mobile-threat-defense-integration-with-intune"></a>Mobile Threat Defense の Intune との統合


Intune Mobile Threat Defense コネクターを使用すると、選択した Mobile Threat Defense ベンダーをコンプライアンス ポリシーと条件付きアクセス規則の情報ソースとして活用できます。 これにより、IT 管理者が、特に危険にさらされたモバイル デバイスから、Exchange、Sharepoint などの企業リソースに保護レイヤーを追加することができます。

## <a name="what-problem-does-this-solve"></a>どのような問題がこれにより解決されますか?

会社は物理的な脅威、アプリ ベースの脅威、ネットワーク ベースの脅威などの新種の脅威やオペレーティング システムの脆弱性から機密データを守る必要があります。

これまで、企業は PC の防御を積極的に行ってきましたが、モバイル デバイスは監視や保護のない状態が続いています。 モバイル プラットフォームには、アプリの分離や検証済みコンシューマー アプリ ストアなどの防御手法が組み込まれていますが、依然として高度な攻撃を受けやすい状態にあります。 現在、モバイル デバイスを仕事に利用し、機密情報にアクセスする社員が増えています。 増え続ける高度な攻撃からモバイル デバイスを守る必要があります。

## <a name="how-the-intune-mobile-threat-defense-connectors-work"></a>Intune Mobile Threat Defense コネクターのしくみ

このコネクターは、Intune と選択した Mobile Threat Defense ベンダーの間の通信チャネルを作成することで、会社のリソースを保護します。 Intune Mobile Threat Defense パートナーは、直感的で簡単に展開できるモバイル デバイス向けアプリケーションを提供します。これらのアプリケーションは、脅威情報を積極的にスキャンして分析し、レポートや強制を目的として Intune と共有します。 

たとえば、Mobile Threat Defense アプリが、電話またはネットワークが Man in the Middle 攻撃に対して脆弱なネットワークに接続されていることを Mobile Threat Defense ベンダーに報告した場合、この情報は共有されて適切なリスク レベル (低/中/高) に分類されます。その後、Intune で構成済みのリスク レベル許容度と比較されて、デバイスが侵害されたときに選択した特定のリソースへのアクセスを無効にする必要があるかどうかが判断されます。

## <a name="what-data-does-intune-collect-for-mobile-threat-defense"></a>Intune は Mobile Threat Defense のためにどのようなデータを収集しますか?

Intune は個人のデバイスと会社所有のデバイスの両方からアプリ インベントリ情報を収集し、Lookout for Work など、MTD (Mobile Thread Defense) プロバイダーが取得できるようにします。 iOS 11 以降のデバイスを所有するユーザーからアプリ インベントリを収集できます。

**アプリ インベントリ**  
iOS 11 以降を内蔵した会社所有デバイスと個人所有デバイスの両方からのインベントリが MTD サービス プロバイダーに送信されます。 アプリ インベントリのデータ:

 - アプリ ID
 - アプリ バージョン
 - アプリ バージョン (短い形式)
 - アプリ名
 - アプリ バンドル サイズ
 - アプリの動的サイズ
 - アプリの有効性が確認されているかどうか
 - アプリが管理されているかどうか

## <a name="sample-scenarios"></a>サンプル事例

Mobile Threat Defense ソリューションによってデバイスが感染したと見なされた場合

![Mobile Threat Defense と感染しているデバイス](./media/MTD-image-1.png)

デバイスが修復されたときにアクセスが許可されます。

![Mobile Threat Defense とアクセス付与](./media/MTD-image-2.png)

> [!NOTE] 
> Intune で複数の Mobile Threat Defense ベンダーを使用することは、サポートされていません。 複数の MTD ツールが有効になると、すべての MTD アプリがインストールされ、脅威を検出するためにデバイスにまたがるスキャンが実行されます。

## <a name="mobile-threat-defense-partners"></a>Mobile Threat Defense パートナー

デバイス、ネットワーク、アプリケーションのリスクに基づいて、会社のリソースへのアクセスを保護する方法について説明します。次のものを使用します。

- [Lookout](lookout-mobile-threat-defense-connector.md)
- [Skycure](skycure-mobile-threat-defense-connector.md)
- [Check Point SandBlast Mobile](checkpoint-sandblast-mobile-mobile-threat-defense-connector.md)
- [Zimperium](zimperium-mobile-threat-defense-connector.md)
