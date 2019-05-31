---
title: Mobile Threat Defense と Microsoft Intune
titleSuffix: Microsoft Intune
description: Mobile Threat Defense パートナーで Intune Mobile Threat Defense (MTD) 使用し、デバイスのリスクに基づいて会社のリソースへのアクセスを保護します。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 04/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ac77b590-a7ec-45a0-9516-ebf5243b6210
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5329e23ee6307f86c7b1fcaead0cb24b8271443c
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66041616"
---
# <a name="what-is-mobile-threat-defense-integration-with-intune"></a>Mobile Threat Defense の Intune との統合
Intune を使用すると、Mobile Threat Defense ベンダーからのデータを、コンプライアンス ポリシーおよび条件付きアクセス規則の情報ソースとして統合することができます。 この情報を使用すれば、危険にさらされたモバイル デバイスからのアクセスをブロックすることで、Exchange や SharePoint などの会社リソースを容易に保護することができます。  

## <a name="what-problem-does-this-solve"></a>どのような問題がこれにより解決されますか?
Mobile Threat Defense ベンダーからの情報を統合することは、モバイル プラットフォームに影響する脅威から会社のリソースを保護する場合に役立ちます。  

通常、会社は PC を脆弱性や攻撃から保護することには積極的ですが、一方で、モバイル デバイスは多くの場合、監視や保護のない状態が続きます。 モバイル プラットフォームには、アプリの分離や検証済みコンシューマー アプリ ストアなどの防御手法が組み込まれていますが、依然として高度な攻撃を受けやすい状態にあります。 仕事用のデバイスを使用して機密情報にアクセスする従業員が増えるにつれて、ますます高度化する攻撃からご利用のデバイスとリソースを保護するのに Mobile Threat Defense ベンダーからの情報が役立ちます。  

## <a name="how-do-the-intune-mobile-threat-defense-connectors-work"></a>Intune Mobile Threat Defense コネクターのしくみ

Intune では、Mobile Threat Defense コネクタを使用して、Intune と選択した Mobile Threat Defense ベンダーとの間に通信チャネルが作成されます。 Intune Mobile Threat Defense パートナーからは、モバイル デバイス用のアプリケーションをデプロイするための直感的で容易な方法が提供されています。 これらのアプリケーションでは積極的にスキャンが行われ、Intune と共有する脅威の情報が分析されます。 Intune では、この情報をレポートや強制を目的として使用できます。  

次に例を示します。接続された Mobile Threat Defense アプリからは、ご利用のネットワーク上の電話が中間者攻撃に対して脆弱なネットワークに現在接続されていることが Mobile Threat Defense ベンダーに報告されます。 この情報は適切なリスク レベル (低、中、高) に分類されます。 次にこのリスク レベルが、Intune に設定したリスク レベル許容値と比較されます。 この比較に基づいて、デバイスが侵害されている間は、選択した特定のリソースへのアクセスを取り消すことができます。

## <a name="what-data-does-intune-collect-for-mobile-threat-defense"></a>Intune は Mobile Threat Defense のためにどのようなデータを収集しますか?

有効になっている場合、Intune は個人のデバイスと会社所有のデバイスの両方からアプリ インベントリ情報を収集し、Lookout for Work など、MTD (Mobile Thread Defense) プロバイダーが取得できるようにします。 iOS デバイスを所有するユーザーからアプリ インベントリを収集できます。

これは、オプトインのサービスです。既定で共有されるインベントリ情報はありません。 アプリのインベントリ情報を共有する前に、Intune 管理者は、サービス設定で iOS デバイスのアプリの同期を有効にする必要があります。

**アプリ インベントリ**  
iOS デバイスのアプリの同期を有効にした場合、iOS を内蔵した会社所有デバイスと個人所有デバイスの両方からのインベントリが MTD サービス プロバイダーに送信されます。 アプリ インベントリのデータ:

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

![Mobile Threat Defense と感染しているデバイスを示す画像](./media/MTD-image-1.png)

デバイスが修復されたときにアクセスが許可されます。

![Mobile Threat Defense とアクセス付与を示す画像](./media/MTD-image-2.png)

> [!NOTE] 
> Intune で複数の Mobile Threat Defense ベンダーを使用することは、サポートされていません。 複数の MTD ツールが有効になると、すべての MTD アプリがインストールされ、脅威を検出するためにデバイスにまたがるスキャンが実行されます。

## <a name="mobile-threat-defense-partners"></a>Mobile Threat Defense パートナー

デバイス、ネットワーク、アプリケーションのリスクに基づいて、会社のリソースへのアクセスを保護する方法について説明します。次のものを使用します。

- [Lookout](lookout-mobile-threat-defense-connector.md)
- [Symantec Endpoint Protection Mobile](skycure-mobile-threat-defense-connector.md)
- [Check Point SandBlast Mobile](checkpoint-sandblast-mobile-mobile-threat-defense-connector.md)
- [Zimperium](zimperium-mobile-threat-defense-connector.md)
- [Pradeo](pradeo-mobile-threat-defense-connector.md)
- [Better Mobile](better-mobile-threat-defense-connector.md)
- [Sophos Mobile](sophos-mtd-connector.md)
- Wandera (詳細は近日公開予定)
