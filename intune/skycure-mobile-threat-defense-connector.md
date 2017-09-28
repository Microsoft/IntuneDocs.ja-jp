---
title: "Intune を使用した Skycure コネクタ"
titlesuffix: Azure portal
description: "Skycure コネクタを Intune と統合します。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: df4ce3f6-a093-432c-ab86-7a83865e389e
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 47df2c4a909c397ac5a6c0f736d11344de44736e
ms.sourcegitcommit: d434dfab7ef7a6c4082d675717fa22d5581b4f51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2017
---
# <a name="skycure-mobile-threat-defense-connector"></a>Skycure Mobile Threat Defense コネクター

Microsoft Intune に統合されたモバイル脅威保護ソリューションである Skycure によって実行されるリスク評価に基づき、条件付きアクセスを利用し、モバイル デバイスから会社のリソースへのアクセスを制御できます。 リスクは、Skycure を実行するデバイスから収集される製品利用統計情報に基づいて以下のとおり評価されます。

-   物理的防御

-   ネットワーク防御

-   アプリケーション防御

-   脆弱性防御

Intune デバイス コンプライアンス ポリシーで有効にした Skycure リスク評価に基づき、条件付きアクセスのポリシーを構成できます。Intune デバイス コンプライアンス ポリシーは、検出された脅威に基づき、非準拠デバイスから企業リソースへのアクセスを許可したり、拒否したりするために利用できます。

## <a name="how-do-intune-and-skycure-help-protect-your-company-resources"></a>Intune と Skycure を利用し、会社のリソースをどのように保護しますか?

Android または iOS 向け Skycure モバイル アプリは、ファイル システム、ネットワーク スタック、デバイスとアプリケーションの製品利用統計情報を可能な限り記録し、Skycure クラウド サービスに送信し、モバイル デバイスの脅威に対するリスクを評価します。

Intune デバイス コンプライアンス ポリシーには、Skycure リスク評価に基づく、Skycure Mobile Threat Defense のルールが含まれています。 このルールを有効にすると、Intune は、有効にされたポリシーに基づいてデバイスの準拠状態を評価します。

デバイスが準拠していないことが判明した場合、Exchange Online や SharePoint Online などのリソースに対するアクセスがブロックされます。 デバイスがブロックされたユーザーには Skycure モバイル アプリから手引きが届きます。それを見て問題を解決し、企業リソースへのアクセスを回復できます。

Intune では、Skycure との統合に 2 つのモードがあります。

-   **基本セットアップ**は読み取り専用モードであり、Skycure は Intune のデバイスを表示できます。

-   **完全統合**の場合、Skycure から、デバイスのリスクとセキュリティ インシデントの詳細を Intune に報告できます。

## <a name="sample-scenarios"></a>サンプル事例

一般的なシナリオを次に示します。

### <a name="control-access-based-on-threats-from-malicious-apps"></a>悪意のあるアプリの脅威に基づいてアクセスを制御する

マルウェアなどの悪意のあるアプリがデバイスで検出されると、脅威が解決されるまで、デバイスで次の行為が禁止されます。

-   会社の電子メールに接続する

-   OneDrive for Work アプリを使用して会社のファイルを同期する

-   会社のアプリにアクセスする

**悪意のあるアプリが検出されたときにブロックする:**

![検出された悪意のあるアプリ](./media/skycure-arch-1.png)

**修復時に付与されるアクセス権:**

![悪意のあるアプリの検出、アクセス権](./media/skycure-arch-2.png)

### <a name="control-access-based-on-threat-to-network"></a>ネットワークに対する脅威に基づいてアクセスを制御する

ネットワークで **Man-in-the-middle** のような脅威を検出し、デバイスのリスクに基づいて Wi-Fi ネットワークへのアクセスを保護します。

**Wi-Fi 経由のネットワーク アクセスをブロックする:**

![Wi-Fi 経由のネットワーク アクセスをブロックする](./media/skycure-arch-3.png)

**修復時に付与されるアクセス権:**

![修復するとアクセス権が付与される](./media/skycure-arch-4.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>ネットワークに対する脅威に基づいて SharePoint Online へのアクセスを制御する

ネットワークで **Man-in-the-middle** のような脅威を検出し、デバイスのリスクに基づいて会社内のファイルの同期を阻止します。

**ネットワークの脅威が検出されたときに SharePoint Online をブロック:**

![ネットワークの脅威が検出されたときに SharePoint Online をブロック](./media/skycure-arch-5.png)

**修復時に付与されるアクセス権:**

![SharePoint で修復時にアクセス権を付与する例](./media/skycure-arch-6.png)

## <a name="supported-platforms"></a>サポートされているプラットフォーム

-   **Android 4.1 以降**

-   **iOS 8 以降**

## <a name="pre-requisites"></a>前提条件

-   Azure Active Directory Premium

-   Microsoft Intune サブスクリプション

-   Skycure Mobile Threat Defense サブスクリプション

詳細については、[Skycure Web サイト](https://www.skycure.com/skycure-microsoft-integration/)をご覧ください。

## <a name="next-steps"></a>次のステップ

Intune と Skycure の統合は次の手順で行います。

- [Skycure と Intune の統合をセットアップする](skycure-mtd-connector-integration.md)

- [Skycure アプリ、Microsoft Authenticator、iOS アプリ構成ポリシーを追加して割り当てる](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [Intune で Skycure デバイスのコンプライアンス ポリシーを作成する](mtd-device-compliance-policy-create.md)

- [Intune で Skycure MTD コネクタを有効にする](mtd-connector-enable.md)
