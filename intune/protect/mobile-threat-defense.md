---
title: Mobile Threat Defense と Microsoft Intune
titleSuffix: Microsoft Intune
description: Mobile Threat Defense パートナーで Intune Mobile Threat Defense (MTD) 使用し、デバイスのリスクに基づいて会社のリソースへのアクセスを保護します。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/29/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ac77b590-a7ec-45a0-9516-ebf5243b6210
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b67e3b14fd94376fb6dacad88fa58ddc460a6bc5
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "73057581"
---
# <a name="mobile-threat-defense-integration-with-intune"></a>Mobile Threat Defense の Intune との統合

Intune を使用すると、Mobile Threat Defense (MTD) ベンダーからのデータを、デバイス コンプライアンス ポリシーおよびデバイス条件付きアクセス規則の情報ソースとして統合することができます。 この情報を使用すれば、危険にさらされたモバイル デバイスからのアクセスをブロックすることで、Exchange や SharePoint などの会社リソースを容易に保護することができます。

Intune では、Intune アプリ保護ポリシーを使用して、未登録デバイスに対するソースと同じデータを使用できます。 そのため、管理者は、この情報を使用して、[Microsoft Intune の保護されたアプリ](~/apps/apps-supported-intune-apps.md)内の企業データを保護し、ブロックまたは選択的ワイプを発行することができます。

## <a name="protect-corporate-resources"></a>会社のリソースを保護する

MTD ベンダーからの情報を統合することは、モバイル プラットフォームに影響を与える脅威から会社のリソースを保護するのに役立ちます。  

通常、会社は PC を脆弱性や攻撃から保護することには積極的ですが、一方で、モバイル デバイスは多くの場合、監視や保護のない状態が続きます。 モバイル プラットフォームには、アプリの分離や検証済みコンシューマー アプリ ストアなどの防御手法が組み込まれていますが、依然として高度な攻撃を受けやすい状態にあります。 仕事用のデバイスを使用して機密情報にアクセスする従業員が増えるにつれて、ますます高度化する攻撃からご利用のデバイスとリソースを保護するのに MTD ベンダーからの情報が役立ちます。

## <a name="intune-mobile-threat-defense-connectors"></a>Intune Mobile Threat Defense コネクター

Intune では、Mobile Threat Defense コネクタを使用して、Intune と選択した MTD ベンダーとの間に通信チャネルが作成されます。 Intune MTD パートナーからは、モバイル デバイス用の、直感的でデプロイしやすいアプリケーションが提供されています。 これらのアプリケーションでは積極的にスキャンが行われ、Intune と共有する脅威の情報が分析されます。 Intune では、この情報をレポートや強制を目的として使用できます。

次に例を示します。接続された MTD アプリから MTD ベンダーに対して、ご利用のネットワーク上の電話が、中間者攻撃に対して脆弱なネットワークに現在接続されていることが報告されます。 この情報は適切なリスク レベル (低、中、高) に分類されます。 次にこのリスク レベルが、Intune に設定したリスク レベル許容値と比較されます。 この比較に基づいて、デバイスが侵害されている間は、選択した特定のリソースへのアクセスを取り消すことができます。

## <a name="data-that-intune-collects-for-mobile-threat-defense"></a>Mobile Threat Defense のために Intune によって収集されるデータ

有効になっている場合、Intune によって、個人所有のデバイスと会社所有のデバイスの両方からアプリ インベントリ情報が収集され、Lookout for Work などの MTD プロバイダーが取得できるようになります。 iOS デバイスを所有するユーザーからアプリ インベントリを収集できます。

これは、オプトインのサービスです。既定で共有されるインベントリ情報はありません。 アプリのインベントリ情報を共有する前に、Intune 管理者は、Mobile Threat Defense コネクタの設定で **iOS デバイスのアプリの同期**を有効にする必要があります。

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

## <a name="sample-scenarios-for-enrolled-devices-using-device-compliance-policies"></a>デバイス コンプライアンス ポリシーを使用する登録済みデバイスのサンプル シナリオ

Mobile Threat Defense ソリューションによってデバイスが感染したと見なされた場合

![Mobile Threat Defense と感染しているデバイスを示す画像](./media/mobile-threat-defense/MTD-image-1.png)

デバイスが修復されたときにアクセスが許可されます。

![Mobile Threat Defense とアクセス付与を示す画像](./media/mobile-threat-defense/MTD-image-2.png)

## <a name="sample-scenarios-for-unenrolled-devices-using-intune-app-protection-policies"></a>Intune アプリ保護ポリシーを使用する未登録デバイスのサンプル シナリオ

Mobile Threat Defense ソリューションによってデバイスが感染したと見なされた場合<br>
![Mobile Threat Defense と感染しているデバイスを示す画像](./media/mobile-threat-defense/MTD-image-3.png)

デバイスが修復されたときにアクセスが許可されます。<br>
![Mobile Threat Defense とアクセス付与を示す画像](./media/mobile-threat-defense/MTD-image-4.png)

> [!NOTE]
> 1 つの Intune テナントで、複数の Mobile Defense ベンダーを使用することができます。 ただし、2 つ以上のベンダーが同じプラットフォームでの使用向けに構成されている場合、そのプラットフォームを実行するすべてのデバイスで、各 MTD アプリをインストールし、脅威をスキャンする必要があります。 構成された任意のアプリからスキャンの送信に失敗すると、そのデバイスは非準拠としてマークされます。 

## <a name="mobile-threat-defense-partners"></a>Mobile Threat Defense パートナー

デバイス、ネットワーク、アプリケーションのリスクに基づいて、会社のリソースへのアクセスを保護する方法について説明します。次のものを使用します。

- [Lookout for Work](lookout-mobile-threat-defense-connector.md)
- [Symantec Endpoint Protection Mobile](skycure-mobile-threat-defense-connector.md)
- [Check Point SandBlast Mobile](checkpoint-sandblast-mobile-mobile-threat-defense-connector.md)
- [Zimperium](zimperium-mobile-threat-defense-connector.md)
- [Pradeo](pradeo-mobile-threat-defense-connector.md)
- [Better Mobile](better-mobile-threat-defense-connector.md)
- [Sophos Mobile](sophos-mtd-connector.md)
- [Wandera Mobile Threat Defense](wandera-mtd-connector.md)
