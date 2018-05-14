---
title: Microsoft Intune を使用した Symantec コネクタ
titlesuffix: ''
description: モバイル デバイスから会社のリソースへのアクセスを制御するための Intune と Symantec Endpoint Protection Mobile の統合について説明します。
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 12/09/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: df4ce3f6-a093-432c-ab86-7a83865e389e
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 577eff3a5f3965065a4066973ea8c61160ab4563
ms.sourcegitcommit: 401cedcd7acc6cb3a6f18d4679bdadb0e0cdf443
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="symantec-endpoint-protection-mobile-connector"></a>Symantec Endpoint Protection Mobile コネクタ

Microsoft Intune に統合された Mobile Threat Defense ソリューションである Symantec Endpoint Protection Mobile (SEP Mobile) によって実行されるリスク評価に基づき、条件付きアクセスを利用し、モバイル デバイスから会社のリソースへのアクセスを制御できます。 リスクは、SEP Mobile を実行するデバイスから収集される次のような製品利用統計情報に基づいて評価されます。

-   物理的防御

-   ネットワーク防御

-   アプリケーション防御

-   脆弱性防御

Intune デバイス コンプライアンス ポリシーで SEP Mobile のリスク評価を有効にした後、条件付きアクセスのポリシーを使って、検出された脅威に基づき、非準拠デバイスから企業リソースへのアクセスを許可または拒否できます。

## <a name="how-do-intune-and-sep-mobile-help-protect-your-company-resources"></a>Intune と SEP Mobile が会社のリソースを保護する方法

Android または iOS 向け SEP Mobile モバイル アプリは、ファイル システム、ネットワーク スタック、デバイスとアプリケーションの製品利用統計情報を可能な限り記録し、SEP Mobile クラウド サービスに送信し、モバイル デバイスの脅威に対するリスクを評価します。

Intune デバイス コンプライアンス ポリシーには、SEP Mobile のリスク評価に基づく、SEP Mobile に関するルールが含まれています。 このルールを有効にすると、Intune は、有効にされたポリシーに基づいてデバイスの準拠状態を評価します。

デバイスが準拠していないことが判明した場合、Exchange Online や SharePoint Online などのリソースに対するアクセスがブロックされます。 デバイスがブロックされたユーザーには SEP Mobile アプリから手引きが届きます。それを見て問題を解決し、企業リソースへのアクセスを回復できます。

Intune では、SEP Mobile との統合に 2 つのモードがあります。

-   **基本セットアップ**は読み取り専用モードであり、SEP Mobile は Intune のデバイスを表示できます。

-   **完全統合**の場合、SEP Mobile から、デバイスのリスクとセキュリティ インシデントの詳細を Intune に報告できます。

## <a name="sample-scenarios"></a>サンプル事例

一般的なシナリオを次に示します。

### <a name="control-access-based-on-threats-from-malicious-apps"></a>悪意のあるアプリの脅威に基づいてアクセスを制御する

マルウェアなどの悪意のあるアプリがデバイスで検出されると、脅威が解決されるまで、デバイスで次の行為が禁止されます。

-   会社の電子メールに接続する

-   OneDrive for Work アプリを使用して会社のファイルを同期する

-   会社のアプリにアクセスする

**悪意のあるアプリが検出されたときにブロックする:**

![検出された悪意のあるアプリ](./media/symantec-arch-1.png)

**修復後、アクセスが与えられる:**

![悪意のあるアプリが検出された後、修復するとアクセス権が付与される](./media/symantec-arch-2.png)

### <a name="control-access-based-on-threat-to-network"></a>ネットワークに対する脅威に基づいてアクセスを制御する

ネットワークで **Man-in-the-middle** のような脅威を検出し、デバイスのリスクに基づいて Wi-Fi ネットワークへのアクセスを保護します。

**Wi-Fi 経由のネットワーク アクセスをブロックする:**

![Wi-Fi 経由のネットワーク アクセスをブロックする](./media/symantec-arch-3.png)

**修復後、アクセスが与えられる:**

![修復するとアクセス権が付与される](./media/symantec-arch-4.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>ネットワークに対する脅威に基づいて SharePoint Online へのアクセスを制御する

ネットワークで **Man-in-the-middle** のような脅威を検出し、デバイスのリスクに基づいて会社内のファイルの同期を阻止します。

**ネットワークの脅威が検出されたときに SharePoint Online をブロック:**

![ネットワークの脅威が検出されたときに SharePoint Online をブロック](./media/symantec-arch-5.png)

**修復後、アクセスが与えられる:**

![SharePoint で修復時にアクセス権を付与する例](./media/symantec-arch-6.png)

## <a name="supported-platforms"></a>サポートされているプラットフォーム

-   **Android 4.1 以降**

-   **iOS 8 以降**

## <a name="pre-requisites"></a>前提条件

-   Azure Active Directory Premium

-   Microsoft Intune サブスクリプション

-   Symantec Endpoint Protection Mobile のサブスクリプション

詳しくは、[Symantec の Web サイト](https://www.skycure.com/skycure-microsoft-integration/)をご覧ください。

## <a name="next-steps"></a>次の手順

Intune と SEP Mobile の統合は次の手順で行います。

- [SEP Mobile と Intune の統合をセットアップする](skycure-mtd-connector-integration.md)

- [SEP Mobile アプリ、Microsoft Authenticator、iOS アプリ構成ポリシーを追加して割り当てる](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [Intune で SEP Mobile デバイスのコンプライアンス ポリシーを作成する](mtd-device-compliance-policy-create.md)

- [Intune で SEP Mobile MTD コネクタを有効にする](mtd-connector-enable.md)
