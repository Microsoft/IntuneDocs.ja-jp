---
title: Intune を使用した Zimperium MTD コネクタ
titleSuffix: Intune on Azure
description: モバイル デバイスから会社のリソースへのアクセスを制御するための Intune と Zimperium Mobile Threat Defense の統合について説明します。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/29/2017
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 975d8d84-792a-41ad-925a-4a7f1ae4dcaf
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a5cb4758cefc1a206e8dae32dfa31994814b3f06
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2019
ms.locfileid: "57395481"
---
# <a name="zimperium-mobile-threat-defense-connector-with-intune"></a>Zimperium Mobile Threat Defense コネクタと Intune

Microsoft Intune に統合された Mobile Threat Defense (MTD) ソリューションである Zimperium によって実行されるリスク評価に基づき、条件付きアクセスを利用し、モバイル デバイスから会社のリソースへのアクセスを制御できます。 リスクは、Zimperium アプリを実行するデバイスから収集される製品利用統計情報に基づいて評価されます。

Intune のデバイス コンプライアンス ポリシーにより有効になった Zimperium のリスク評価に基づいて、条件付きアクセス ポリシーを構成できます。 リスク評価ポリシーは、検出された脅威に基づき、非準拠デバイスの企業リソースへのアクセスを許可またはブロックすることができます。

## <a name="how-do-intune-and-zimperium-help-protect-your-company-resources"></a>Intune と Zimperium を利用し、会社のリソースをどのように保護しますか?

Android および iOS 向け Zimperium アプリは、ファイル システム、ネットワーク スタック、デバイスとアプリケーションの製品利用統計情報を可能な限り記録し、Zimperium クラウド サービスにテレメトリ データを送信し、モバイル デバイスの脅威に対するリスクを評価します。

Intune デバイス コンプライアンス ポリシーには、Zimperium リスク評価に基づく、Zimperium Mobile Threat Defense のルールが含まれています。 このルールを有効にすると、Intune は、有効にされたポリシーに基づいてデバイスの準拠状態を評価します。 デバイスが準拠していないことが判明した場合、ユーザーは Exchange Online や SharePoint Online などの会社リソースへのアクセスをブロックされます。 また、ユーザーは、デバイスにインストールされている Zimperium アプリから、問題を解決して会社リソースへのアクセスを回復するための案内を受け取ります。

## <a name="sample-scenarios"></a>サンプル事例

Intune と Zimperium を統合する場合のシナリオのいくつかを、下記で参照してください。

### <a name="control-access-based-on-threats-from-malicious-apps"></a>悪意のあるアプリの脅威に基づいてアクセスを制御する

マルウェアなどの悪意のあるアプリがデバイスで検出されると、脅威が解決されるまで、デバイスで次の行為が禁止されます。

-   会社の電子メールに接続する

-   OneDrive for Work アプリを使用して会社のファイルを同期する

-   会社のアプリにアクセスする

**悪意のあるアプリが検出されたときにブロックする:**

![検出された悪意のあるアプリの概念図](./media/Maliciousapps_blocked_Zimperium.png)

**修復後、アクセスが与えられる:**

![修復後に付与されたアクセス権の概念図](./media/maliciousapps_unblocked_Zimperium.png)

### <a name="control-access-based-on-threat-to-network"></a>ネットワークに対する脅威に基づいてアクセスを制御する

ネットワークで **中間者攻撃** のような脅威を検出し、デバイスのリスクに基づいて Wi-Fi ネットワークへのアクセスを保護します。

**Wi-Fi 経由のネットワーク アクセスをブロックする:**

![Wi-Fi 経由のネットワーク アクセスをブロックする](./media/network_wifi_blocked_Zimperium.png)

**修復後、アクセスが与えられる:**

![修復するとアクセス権が付与される](./media/network_wifi_unblocked_Zimperium.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>ネットワークに対する脅威に基づいて SharePoint Online へのアクセスを制御する

ネットワークで **中間者攻撃** のような脅威を検出し、デバイスのリスクに基づいて会社内のファイルの同期を阻止します。

**ネットワークの脅威が検出されたときに SharePoint Online をブロック:**

![ネットワークの脅威が検出されたときに SharePoint Online をブロック](./media/network_spo_blocked_Zimperium.png)

**修復後、アクセスが与えられる:**

![SharePoint で修復時にアクセス権を付与する例](./media/network_spo_unblocked_Zimperium.png)

## <a name="supported-platforms"></a>サポートされているプラットフォーム

-   **Android 4.1 以降**

-   **iOS 8 以降**

## <a name="prerequisites"></a>必要条件

-   Azure Active Directory Premium

-   Microsoft Intune サブスクリプション

-   Zimperium Mobile Threat Defense サブスクリプション

    -   詳細については、 [Zimperium の Web サイト](https://www.zimperium.com/zips-mobile-ips)を参照してください。

## <a name="next-steps"></a>次の手順

- [Zimperium を Intune と統合する](zimperium-mtd-connector-integration.md)

- [Zimperium アプリを設定する](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [Zimperium デバイス コンプライアンス ポリシーを作成する](mtd-device-compliance-policy-create.md)

- [Zimperium MTD コネクタを有効にする](mtd-connector-enable.md)
