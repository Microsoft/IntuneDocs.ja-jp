---
title: "Skycure Mobile Threat Defense コネクター | Microsoft Docs"
description: "Skycure Mobile Threat Defense コネクターと Intune を使用して、デバイス、ネットワーク、アプリケーションのリスクを基にして会社のリソースへのアクセスを保護します。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7a004e6c-604a-448c-bfb8-cfda63749f5b
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 86fd9d7212277f9524eb4d7f225df2c7beda1313
ms.openlocfilehash: 219369dfdf9d7a82159563d3fe16bb287bc414d7
ms.lasthandoff: 03/21/2017


---

# <a name="skycure-mobile-threat-defense-connector"></a>Skycure Mobile Threat Defense コネクター

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune に統合されたモバイル脅威保護ソリューションである Skycure によって実行されるリスク評価に基づき、条件付きアクセスを利用し、モバイル デバイスから会社のリソースへのアクセスを制御できます。 リスクは、Skycure を実行するデバイスから収集される製品利用統計情報に基づいて以下のとおり評価されます。

-   物理的防御

-   ネットワーク防御

-   アプリケーション防御

-   脆弱性防御

Intune デバイス コンプライアンス ポリシーで有効にした Skycure リスク評価に基づき、条件付きアクセスのポリシーを構成できます。Intune デバイス コンプライアンス ポリシーは、検出された脅威に基づき、非準拠デバイスから企業リソースへのアクセスを許可したり、拒否したりするために利用できます。

## <a name="how-do-intune-and-skycure-help-protect-your-company-resources"></a>Intune と Skycure を利用し、会社のリソースをどのように保護しますか?

Android または iOS 向け Skycure モバイル アプリは、ファイル システム、ネットワーク スタック、デバイスとアプリケーションの製品利用統計情報を可能な限り記録し、Skycure クラウド サービスに送信し、モバイル デバイスの脅威に対するリスクを評価します。

Intune デバイス コンプライアンス ポリシーには、Skycure リスク評価に基づく、Skycure モバイル脅威防御のルールが含まれています。 このルールを有効にすると、Intune は、有効にされたポリシーに基づいてデバイスの準拠状態を評価します。

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

![検出された悪意のあるアプリ](../media/mtp/skycure-arch-1.png)

**修復時に付与されるアクセス権:**

![悪意のあるアプリの検出、アクセス権](../media/mtp/skycure-arch-2.png)

### <a name="control-access-based-on-threat-to-network"></a>ネットワークに対する脅威に基づいてアクセスを制御する

ネットワークで **Man-in-the-middle** のような脅威を検出し、デバイスのリスクに基づいて Wi-Fi ネットワークへのアクセスを保護します。

**Wi-Fi 経由のネットワーク アクセスをブロックする:**

![Wi-Fi 経由のネットワーク アクセスをブロックする](../media/mtp/skycure-arch-3.png)

**修復時に付与されるアクセス権:**

![修復するとアクセス権が付与される](../media/mtp/skycure-arch-4.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>ネットワークに対する脅威に基づいて SharePoint Online へのアクセスを制御する

ネットワークで **Man-in-the-middle** のような脅威を検出し、デバイスのリスクに基づいて会社内のファイルの同期を阻止します。

**ネットワークの脅威が検出されたときに SharePoint Online をブロック:**

![ネットワークの脅威が検出されたときに SharePoint Online をブロック](../media/mtp/skycure-arch-5.png)

**修復時に付与されるアクセス権:**

![SharePoint で修復時にアクセス権を付与する例](../media/mtp/skycure-arch-6.png)

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

1.  [Azure Active Directory シングル サインオン (SSO) を使用するように Skycure を構成する](https://docs.microsoft.com/intune/deploy-use/configure-skycure-to-use-azure-active-directory-single-sign-on)

2.  [Skycure iOS アプリ構成ポリシーをダウンロードする](https://docs.microsoft.com/intune/deploy-use/download-skycure-ios-app-configuration-policy)

3.  [Skycure アプリ、Microsoft Authenticator、iOS アプリ構成ポリシーを追加する](https://docs.microsoft.com/intune/deploy-use/add-skycure-apps-microsoft-authenticator-and-ios-app-configuration-policy)

4.  [Skycure アプリ、Microsoft Authenticator、iOS アプリ構成ポリシーを展開する](https://docs.microsoft.com/intune/deploy-use/deploy-skycure-apps-microsoft-authenticator-app-and-ios-app-configuration-policy)

5.  [Skycure と Intune の統合をセットアップする](https://docs.microsoft.com/intune/deploy-use/setup-the-skycure-integration-with-Intune)

6.  [Intune で Skycure Mobile Threat Defense を有効にする](https://docs.microsoft.com/intune/deploy-use/enable-skycure-mobile-threat-defense-in-intune)

7.  [Intune で Skycure Mobile Threat Defense コンプライアンス ポリシーを作成する](https://docs.microsoft.com/intune/deploy-use/create-skycure-mobile-threat-defense-compliance-policy)

