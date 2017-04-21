---
title: "Lookout Mobile Threat Defense コネクター | Microsoft Docs"
description: "Lookout Mobile Threat Defense コネクターと Intune を使用して、デバイス、ネットワーク、アプリケーションのリスクを基にして会社のリソースへのアクセスを保護します。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 01/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 725d9e40-e70c-461a-9413-72ff1b89a938
ms.reviewer: sandera
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: ab6d9b6b296fb4e1fb0aaa9496fede28976728dc
ms.openlocfilehash: 47645e1f133b172d059f849e2f73e59e115046c6
ms.lasthandoff: 04/14/2017


---

# <a name="lookout-mobile-threat-defense-connector-with-intune"></a>Lookout Mobile Threat Defense コネクターと Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune に統合された Mobile Threat Defense ソリューションである Lookout によって実行されるリスク評価に基づいて、モバイル デバイスから会社のリソースへのアクセスを制御することができます。 リスクは、Lookout サービスによりデバイスから収集される次のような製品利用統計情報に基づいて評価されます。
- オペレーティング システムの脆弱性
- インストールされた悪意のあるアプリ
- 悪意のあるネットワーク プロファイル

Intune コンプライアンス ポリシーにより有効になった Lookout のリスク評価に基づいて条件付きアクセス ポリシーを構成できます。 設定により、検出された脅威に基づいて非準拠デバイスを許可したり、ブロックしたりできます。

## <a name="how-do-intune-and-lookout-mobile-threat-defense-help-protect-company-resources"></a>Intune および Lookout の Mobile Threat Defense は会社リソースの保護にどのように役立ちますか?
Lookout のモバイル アプリ、**Lookout for work** は、モバイル デバイスにインストールされ、実行されます。 このアプリは、利用できる場合、ファイル システム、ネットワーク スタック、デバイスとアプリケーションの製品利用統計情報を記録し、Lookout クラウド サービスに送信し、モバイル デバイスの脅威に対するリスクを評価します。 Lookout コンソールでは、要件に合わせ、脅威に対するリスク レベルの分類を変更できます。  

Intune のコンプライアンス ポリシーには、Lookout のリスク評価に基づく Lookout Mobile Threat Defense のルールが含まれています。 このルールを有効にすると、Intune は、有効にされたポリシーに基づいてデバイスの準拠状態を評価します。

デバイスが準拠していないことが判明した場合、Exchange Online や SharePoint Online などのリソースに対するアクセスをブロックできます。 ブロックされたデバイスのユーザーには、問題を解決し、アクセスを回復するための手順が与えられます。 ガイダンスは Lookout for work アプリから起動されます。

## <a name="supported-platforms"></a>サポートされているプラットフォーム:
Intune に登録するとき、Lookout では次のプラットフォームがサポートされます。
* **Android 4.1 以降**
* **iOS 8 以降** プラットフォームと言語サポートの詳細については、[Lookout Web サイト](https://personal.support.lookout.com/hc/articles/114094140253)をご覧ください。

## <a name="prerequisites"></a>前提条件:
* Microsoft Intune サブスクリプション
* Azure Active Directory
* Lookout Mobile EndPoint Security エンタープライズ サブスクリプション  

詳細については、「[Lookout Mobile Endpoint Security](https://www.lookout.com/products/mobile-endpoint-security)」を参照してください。

## <a name="sample-scenarios"></a>サンプル事例
一般的なシナリオを次に示します。

### <a name="control-access-based-on-threats-from-malicious-apps"></a>悪意のあるアプリの脅威に基づいてアクセスを制御する
マルウェアなどの悪意のあるアプリがデバイスで検出されると、脅威が解決されるまで、デバイスで次の行為が禁止されます。
* 会社の電子メールに接続する
* OneDrive for Work アプリを使用して会社のファイルを同期する
* 会社のアプリにアクセスする

**悪意のあるアプリが検出されたときのブロック:**
![悪意のあるアプリが検出されたことからデバイスが非準拠状態と判断された場合に、アクセスをブロックする条件付きアクセス ポリシーを示す図](../media/mtp/malicious-apps-blocked.png)

**修復時に付与されるアクセス権:**

![修復後、デバイスが準拠状態にあると判断された場合にアクセス権を付与する条件付きアクセス ポリシーを示す図](../media/mtp/malicious-apps-unblocked.png)

### <a name="control-access-based-on-threat-to-network"></a>ネットワークに対する脅威に基づいてアクセスを制御する
Man-in-the-middle 攻撃など、ネットワークに対する脅威を検出し、デバイスのリスクに基づいて WiFi ネットワークへのアクセスを保護します。

**WiFi 経由でネットワークにアクセスする行為のブロック:**
![ネットワークの脅威に基づいて WiFi アクセスをブロックする条件付きアクセスを示す図](../media/mtp/network-wifi-blocked.png)

**修復時に付与されるアクセス権:**

![脅威の修復時にアクセスを許可する条件付きアクセスを示す図](../media/mtp/network-wifi-unblocked.png)
### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>ネットワークに対する脅威に基づいて SharePoint Online へのアクセスを制御する

Man-in-the-middle 攻撃など、ネットワークに対する脅威を検出し、デバイスのリスクに基づいて会社内のファイルの同期を阻止します。

**ネットワークの脅威が検出されたときに SharePoint Online をブロック:**

![検出した脅威に基づいて SharePoint Online へのデバイスのアクセスをブロックする条件付きアクセスを示す図](../media/mtp/network-spo-blocked.png)


**修復時に付与されるアクセス権:**

![ネットワークの脅威が修復された後でアクセスを許可する条件付きアクセスを示す図](../media/mtp/network-spo-unblocked.png)

## <a name="next-steps"></a>次のステップ
このソリューションを実装するために実行する必要がある主な手順を次に示します。
1.    [Lookout サブスクリプションを設定する](device-threat-protection-subscription-setup.md)
2.    [Intune で Lookout Mobile Threat Defense を有効にする](device-threat-protection-enable.md)
3.  [Lookout Mobile Threat Defense アプリを構成し、展開する](device-threat-protection-apps.md)
4.    [Lookout デバイス コンプライアンス ポリシーを構成する](device-threat-protection-policy.md)
5.    [Lookout Mobile Threat Defense 統合の問題を解決する](http://docs.microsoft.com/intune/troubleshoot/device-threat-protection-troubleshooting)

