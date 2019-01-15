---
title: Better Mobile Threat Defense コネクタと Intune
titleSuffix: Intune on Azure
description: Better Mobile Threat Defense コネクタを Intune で設定します。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/25/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.openlocfilehash: 313c20699c30d20d1bbc9bb6aea9189a83b61f53
ms.sourcegitcommit: bee072b61cf8a1b8ad8d736b5f5aa9bc526e07ec
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53816635"
---
# <a name="better-mobile-threat-defense-connector-with-intune"></a>Better Mobile Threat Defense コネクタと Intune

Microsoft Intune に統合された Mobile Threat Defense (MTD) ソリューションである Better Mobile によって実行されるリスク評価に基づき、条件付きアクセスを利用し、モバイル デバイスから会社のリソースへのアクセスを制御できます。 リスクは、Better Mobile アプリを実行するデバイスから収集される製品利用統計情報に基づいて評価されます。

Intune デバイス コンプライアンス ポリシーで有効にした Better Mobile リスク評価に基づき、条件付きアクセスのポリシーを構成できます。Intune デバイス コンプライアンス ポリシーは、検出された脅威に基づき、非準拠デバイスから企業リソースへのアクセスを許可したり、拒否したりするために利用できます。

## <a name="how-do-intune-and-better-mobile-help-protect-your-company-resources"></a>Intune と Better Mobile が会社のリソースを保護する方法

Better Mobile のアプリは、モバイル デバイスにインストールされ、実行されます。 このアプリは、利用できる場合、ファイル システム、ネットワーク スタック、デバイスとアプリケーションの製品利用統計情報を記録し、Better Mobile クラウド サービスにデータを送信し、モバイル デバイスの脅威に対するリスクを評価します。

Intune デバイス コンプライアンス ポリシーには、Better Mobile リスク評価に基づく、Mobile Threat Defense のルールが含まれています。 このルールを有効にすると、Intune は、有効にされたポリシーに基づいてデバイスの準拠状態を評価します。 デバイスが準拠していないことが判明した場合、ユーザーは Exchange Online や SharePoint Online などの会社リソースへのアクセスをブロックされます。 また、ユーザーは、デバイスにインストールされている Better Mobile アプリから、問題を解決して会社リソースへのアクセスを回復するための案内を受け取ります。

## <a name="sample-scenarios"></a>サンプル事例

一般的なシナリオを次に示します。

### <a name="control-access-based-on-threats-from-malicious-apps"></a>悪意のあるアプリの脅威に基づいてアクセスを制御する

マルウェアなどの悪意のあるアプリがデバイスで検出されると、脅威が解決されるまで、デバイスで次の行為が禁止されます。

-   会社の電子メールに接続する

-   OneDrive for Work アプリを使用して会社のファイルを同期する

-   会社のアプリにアクセスする

**悪意のあるアプリが検出されたときにブロックする:**

![検出された悪意のあるアプリを示す画像](./media/better_mobile_maliciousapps_blocked.png)

**修復後、アクセスが与えられる:**

![悪意のあるアプリの検出、アクセス権](./media/better_mobile_maliciousapps_unblocked.png)

### <a name="control-access-based-on-threat-to-network"></a>ネットワークに対する脅威に基づいてアクセスを制御する

**Man-in-the-middle** 攻撃など、ネットワークに対する脅威を検出し、デバイスのリスクに基づいて Wi-Fi ネットワークへのアクセスを保護します。

**Wi-Fi 経由のネットワーク アクセスをブロックする:**

![Wi-Fi 経由のネットワーク アクセスをブロックする](./media/better_mobile_network_wifi_blocked.png)

**修復後、アクセスが与えられる:**

![修復時にアクセス権が付与されたことを示す画像](./media/better_mobile_network_wifi_unblocked.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>ネットワークに対する脅威に基づいて SharePoint Online へのアクセスを制御する

**Man-in-the-middle** 攻撃など、ネットワークに対する脅威を検出し、デバイスのリスクに基づいて会社内のファイルの同期を阻止します。

**ネットワークの脅威が検出されたときに SharePoint Online をブロック:**

![ネットワークの脅威が検出されたときに SharePoint Online をブロック](./media/better_mobile_network_spo_blocked.png)

**修復後、アクセスが与えられる:**

![SharePoint で修復時にアクセス権を付与する例](./media/better_mobile_network_spo_unblocked.png)

## <a name="supported-platforms"></a>サポートされているプラットフォーム

-   **Android 4.1 以降**

-   **iOS 8.0 以降**

## <a name="prerequisites"></a>必要条件

-   Azure Active Directory Premium

-   Microsoft Intune サブスクリプション

-   Better Mobile Threat Defense サブスクリプション

    -   詳細については、[Better Mobile の Web サイト](https://www.better.mobi/)を参照してください。

## <a name="next-steps"></a>次の手順

- [Better Mobile と Intune を統合する](better-mobile-mtd-connector-integration.md)

- [Better Mobile アプリを設定する](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [Better Mobile デバイスのコンプライアンス ポリシーを作成する](mtd-device-compliance-policy-create.md)

- [Better Mobile MTD コネクタを有効にする](mtd-connector-enable.md)