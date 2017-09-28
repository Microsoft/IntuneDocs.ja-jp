---
title: "Intune を使用した Zimperium MTD コネクタ"
titleSuffix: Intune on Azure
description: "Zimperium コネクタと Intune の統合"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 09/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 975d8d84-792a-41ad-925a-4a7f1ae4dcaf
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 78214293a66784d4bc05e441c2c1cdbf718b0a9a
ms.sourcegitcommit: d434dfab7ef7a6c4082d675717fa22d5581b4f51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2017
---
# <a name="zimperium-mobile-threat-defense-connector-with-intune"></a>Zimperium Mobile Threat Defense コネクタと Intune

Microsoft Intune に統合された Mobile Threat Defense (MTD) ソリューションである Zimperium によって実行されるリスク評価に基づき、条件付きアクセスを利用し、モバイル デバイスから会社のリソースへのアクセスを制御できます。 リスクは、Zimperium アプリを実行するデバイスから収集される製品利用統計情報に基づいて評価されます。

Intune デバイス コンプライアンス ポリシーで有効にした Zimperium リスク評価に基づき、条件付きアクセスのポリシーを構成できます。Intune デバイス コンプライアンス ポリシーは、検出された脅威に基づき、非準拠デバイスから企業リソースへのアクセスを許可したり、拒否したりするために利用できます。

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

![検出された悪意のあるアプリ](./media/Maliciousapps_blocked_Zimperium.png)

**修復時に付与されるアクセス権:**

![悪意のあるアプリの検出、アクセス権](./media/maliciousapps_unblocked_Zimperium.png)

### <a name="control-access-based-on-threat-to-network"></a>ネットワークに対する脅威に基づいてアクセスを制御する

ネットワークで **Man-in-the-middle** のような脅威を検出し、デバイスのリスクに基づいて Wi-Fi ネットワークへのアクセスを保護します。

**Wi-Fi 経由のネットワーク アクセスをブロックする:**

![Wi-Fi 経由のネットワーク アクセスをブロックする](./media/network_wifi_blocked_Zimperium.png)

**修復時に付与されるアクセス権:**

![修復するとアクセス権が付与される](./media/network_wifi_unblocked_Zimperium.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>ネットワークに対する脅威に基づいて SharePoint Online へのアクセスを制御する

ネットワークで **Man-in-the-middle** のような脅威を検出し、デバイスのリスクに基づいて会社内のファイルの同期を阻止します。

**ネットワークの脅威が検出されたときに SharePoint Online をブロック:**

![ネットワークの脅威が検出されたときに SharePoint Online をブロック](./media/network_spo_blocked_Zimperium.png)

**修復時に付与されるアクセス権:**

![SharePoint で修復時にアクセス権を付与する例](./media/network_spo_unblocked_Zimperium.png)

## <a name="supported-platforms"></a>サポートされているプラットフォーム

-   **Android 4.1 以降**

-   **iOS 8 以降**

## <a name="prerequisites"></a>必要条件

-   Azure Active Directory Premium

-   Microsoft Intune サブスクリプション

-   Zimperium Mobile Threat Defense サブスクリプション

    -   詳細については、[Zimperium Web サイト](https://www.zimperium.com/zips-mobile-ips)を参照してください。

## <a name="next-steps"></a>次のステップ

- [Zimperium を Intune と統合する](zimperium-mtd-connector-integration.md)

- [Zimperium アプリを設定する](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [Zimperium デバイス コンプライアンス ポリシーを作成する](mtd-device-compliance-policy-create.md)

- [Zimperium MTD コネクタを有効にする](mtd-connector-enable.md)
