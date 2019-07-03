---
title: Microsoft Intune を使用した Lookout MTD コネクタ
titleSuffix: Microsoft Intune
description: モバイル デバイスから会社のリソースへのアクセスを制御するための Intune と Lookout Mobile Threat Defense (MTD) の統合について説明します。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/11/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3a730a5d-2a90-42b0-aa28-aadfc7a18788
ms.reviewer: davera
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a6dfce050726cfddadc493f73c91701021dc21ea
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2019
ms.locfileid: "67529818"
---
# <a name="lookout-mobile-endpoint-security-connector-with-intune"></a>Lookout Mobile Endpoint Security コネクタと Intune

Microsoft Intune に統合された Mobile Threat Defense ソリューションである Lookout によって実行されるリスク評価に基づいて、モバイル デバイスから会社のリソースへのアクセスを制御することができます。 リスクは、Lookout サービスによりデバイスから収集される次のような製品利用統計情報に基づいて評価されます。
- オペレーティング システムの脆弱性
- インストールされた悪意のあるアプリ
- 悪意のあるネットワーク プロファイル

Intune コンプライアンス ポリシーにより有効になった Lookout のリスク評価に基づいて条件付きアクセス ポリシーを構成できます。 設定により、検出された脅威に基づいて非準拠デバイスを許可したり、ブロックしたりできます。

## <a name="how-do-intune-and-lookout-mobile-endpoint-security-help-protect-company-resources"></a>Intune と Lookout Mobile Endpoint Security で会社リソースを保護する方法
Lookout のモバイル アプリ、**Lookout for work** は、モバイル デバイスにインストールされ、実行されます。 このアプリは、利用できる場合、ファイル システム、ネットワーク スタック、デバイスとアプリケーションの製品利用統計情報を記録し、Lookout クラウド サービスに送信し、モバイル デバイスの脅威に対するリスクを評価します。 Lookout コンソールでは、要件に合わせ、脅威に対するリスク レベルの分類を変更できます。  

Intune のコンプライアンス ポリシーには、Lookout のリスク評価に基づく Lookout Mobile Threat Defense のルールが含まれています。 このルールを有効にすると、Intune は、有効にされたポリシーに基づいてデバイスの準拠状態を評価します。

デバイスが準拠していないことが判明した場合、Exchange Online や SharePoint Online などのリソースに対するアクセスをブロックできます。 ブロックされたデバイスのユーザーには、問題を解決し、アクセスを回復するための手順が与えられます。 ガイダンスは Lookout for work アプリから起動されます。

## <a name="supported-platforms"></a>サポートされているプラットフォーム  
Intune に登録するとき、Lookout では次のプラットフォームがサポートされます。
* **Android 4.1 以降**  
* **iOS 8 以降**  

プラットフォームと言語サポートの詳細については、[Lookout Web サイト](https://personal.support.lookout.com/hc/articles/114094140253)を参照してください。  

## <a name="prerequisites"></a>必要条件
* Lookout Mobile EndPoint Security エンタープライズ サブスクリプション  
* Microsoft Intune サブスクリプション
* Azure Active Directory Premium
* ユーザーにライセンスが割り当てられている Enterprise Mobility and Security (EMS) E3 または E5。  

詳細については、「[Lookout Mobile Endpoint Security](https://www.lookout.com/products/mobile-endpoint-security)」を参照してください。

## <a name="sample-scenarios"></a>サンプル事例

Intune で Mobile Endpoint Security を使用する場合の一般的なシナリオを次に示します。

### <a name="control-access-based-on-threats-from-malicious-apps"></a>悪意のあるアプリの脅威に基づいてアクセスを制御する
マルウェアなどの悪意のあるアプリがデバイスで検出されると、脅威が解決されるまで、デバイスで次の行為が禁止されます。
* 会社の電子メールに接続する
* OneDrive for Work アプリを使用して会社のファイルを同期する
* 会社のアプリにアクセスする

**悪意のあるアプリが検出されたときにブロックする:**

![悪意のあるアプリによるアクセスをブロックするポリシーの概念図](./media/malicious-apps-blocked.png)

**修復後、アクセスが与えられる:**

![修復後にデバイスに付与されるアクセスを示す概念図](./media/malicious-apps-unblocked.png)

### <a name="control-access-based-on-threat-to-network"></a>ネットワークに対する脅威に基づいてアクセスを制御する
Man-in-the-middle 攻撃など、ネットワークに対する脅威を検出し、デバイスのリスクに基づいて WiFi ネットワークへのアクセスを保護します。

**Wi-Fi 経由のネットワーク アクセスをブロックする:**

![ネットワークの脅威に基づいた WiFi アクセスのブロックを示す画像](./media/network-wifi-blocked.png)

**修復後、アクセスが与えられる:**

![修復後にアクセスを許可する条件付きアクセスの概念図](./media/network-wifi-unblocked.png)
### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>ネットワークに対する脅威に基づいて SharePoint Online へのアクセスを制御する

Man-in-the-middle 攻撃など、ネットワークに対する脅威を検出し、デバイスのリスクに基づいて会社内のファイルの同期を阻止します。

**ネットワークの脅威が検出されたときに SharePoint Online をブロック:**

![SharePoint Online へのアクセスをブロックする概念図](./media/network-spo-blocked.png)


**修復後、アクセスが与えられる:**

![ネットワークの脅威の修復後にアクセスを許可する概念図](./media/network-spo-unblocked.png)

## <a name="next-steps"></a>次の手順
このソリューションを実装するために実行する必要がある主な手順を次に示します。
1. [Lookout 統合を設定する](lookout-mtd-connector-integration.md)
2. [Intune で Mobile Endpoint Security を有効にする](mtd-connector-enable.md)
3. [Lookout for Work アプリを追加して割り当てる](mtd-apps-ios-app-configuration-policy-add-assign.md)
4. [Lookout デバイス コンプライアンス ポリシーを構成する](mtd-device-compliance-policy-create.md)
