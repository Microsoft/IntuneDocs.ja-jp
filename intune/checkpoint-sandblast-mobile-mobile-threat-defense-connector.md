---
title: "Microsoft Intune で Point SandBlast MTD を確認する"
titlesuffix: 
description: "モバイル デバイスから会社のリソースへのアクセスを制御するための Intune と Check Point SandBlast Mobile Threat Defense の統合について説明します。"
keywords: 
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 07/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 706a4228-9bdf-41e0-b8d1-64c923dd2d2b
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a0dad532511b87b7856bb2e293707ac5311eb773
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2018
---
# <a name="check-point-sandblast-mobile-threat-defense-connector-with-intune"></a>Intune との Check Point SandBlast Mobile Threat Defense コネクタ

Microsoft Intune に統合された Mobile Threat Defense ソリューションであるチェック ポイントの SandBlast Mobile によって実行されるリスク評価に基づき、条件付きアクセスを利用し、モバイル デバイスから会社のリソースへのアクセスを制御できます。 リスクは、チェック ポイントの SandBlast Mobile アプリを実行するデバイスから収集される製品利用統計情報に基づいて評価されます。

Intune デバイス コンプライアンス ポリシーで有効にした Check Point SandBlast Mobile リスク評価に基づき、条件付きアクセスのポリシーを構成できます。Intune デバイス コンプライアンス ポリシーは、検出された脅威に基づき、非準拠デバイスから企業リソースへのアクセスを許可したり、拒否したりするために利用できます。

## <a name="how-do-intune-and-check-point-sandblast-mobile-help-protect-your-company-resources"></a>Intune と Check Point SandBlast Mobile を利用し、会社のリソースをどのように保護しますか?

Android および iOS 向け Check Point Sandblast Mobile アプリは、ファイル システム、ネットワーク スタック、デバイスとアプリケーションの製品利用統計情報を可能な限り記録し、Check Point SandBlast クラウド サービスにテレメトリ データを送信し、モバイル デバイスの脅威に対するリスクを評価します。

Intune デバイス コンプライアンス ポリシーには、Check Point SandBlast リスク評価に基づく、Check Point SandBlast Mobile Threat Defense のルールが含まれています。 このルールを有効にすると、Intune は、有効にされたポリシーに基づいてデバイスの準拠状態を評価します。 デバイスが準拠していないことが判明した場合、ユーザーは Exchange Online や SharePoint Online などの会社リソースへのアクセスをブロックされます。 また、ユーザーは、デバイスにインストールされている Check Point SandBlast Mobile アプリから、問題を解決して会社リソースへのアクセスを回復するための案内を受け取ります。

<!-- ## Sample scenarios 
closing syntax for comment above is missing. Please insert closing syntax at intended location. -->

一般的なシナリオを次に示します。

### <a name="control-access-based-on-threats-from-malicious-apps"></a>悪意のあるアプリの脅威に基づいてアクセスを制御する

マルウェアなどの悪意のあるアプリがデバイスで検出されると、脅威が解決されるまで、デバイスで次の行為が禁止されます。

-   会社の電子メールに接続する

-   OneDrive for Work アプリを使用して会社のファイルを同期する

-   会社のアプリにアクセスする

**悪意のあるアプリが検出されたときにブロックする:**

![Check Point MTD - 悪意のあるアプリが検出されたときにブロック](./media/checkpoint-MTD-2.PNG)

**修復後、アクセスが与えられる:**

![Check Point MTD - アクセスを許可](./media/checkpoint-MTD-3.PNG)

### <a name="control-access-based-on-threat-to-network"></a>ネットワークに対する脅威に基づいてアクセスを制御する

ネットワークで **Man-in-the-middle** のような脅威を検出し、デバイスのリスクに基づいて Wi-Fi ネットワークへのアクセスを保護します。

**Wi-Fi 経由のネットワーク アクセスをブロックする:**

![Check Point MTD - Wi-Fi 経由のネットワーク アクセスをブロック](./media/checkpoint-MTD-4.PNG)

**修復後、アクセスが与えられる:**

![Check Point MTD - Wi-Fi アクセスを許可](./media/checkpoint-MTD-5.PNG)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>ネットワークに対する脅威に基づいて SharePoint Online へのアクセスを制御する

ネットワークで **Man-in-the-middle** のような脅威を検出し、デバイスのリスクに基づいて会社内のファイルの同期を阻止します。

**ネットワークの脅威が検出されたときに SharePoint Online をブロック:**

![Check Point MTD - SharePoint Online アクセスをブロック](./media/checkpoint-MTD-6.PNG)

**修復後、アクセスが与えられる:**

![Check Point MTD - SharePoint Online アクセスを許可](./media/checkpoint-MTD-7.PNG)

## <a name="supported-platforms"></a>サポートされているプラットフォーム

-   **Android 4.1 以降**

-   **iOS 8 以降**

## <a name="pre-requisites"></a>前提条件

-   Azure Active Directory Premium

-   Microsoft Intune サブスクリプション

-   Check Point SandBlast Mobile Threat Defense サブスクリプション
    -   詳細については、[Check Point SandBlast の Web サイト](https://www.checkpoint.com/)を参照してください。

## <a name="next-steps"></a>次の手順

- [Check Point SandBlast Mobile と Intune を統合する](checkpoint-sandblast-mobile-mtd-connector-integration.md)

- [Check Point SandBlast Mobile アプリをセットアップする](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [Check Point SandBlast Mobile のデバイス コンプライアンス ポリシーを作成する](mtd-device-compliance-policy-create.md)

- [Check Point SandBlast Mobile MTD コネクタを有効にする](mtd-connector-enable.md)
