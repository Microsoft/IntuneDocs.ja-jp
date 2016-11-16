---
title: "デバイス脅威保護を使用してアクセスを制限する | Microsoft Intune"
description: "デバイス、ネットワーク、アプリケーションのリスクに基づいて、会社のリソースへのアクセスを制限します。"
keywords: 
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 725d9e40-e70c-461a-9413-72ff1b89a938
ms.reviewer: sandera
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d4cd3d28a9e4c80fb6a2e17856f6dc9230429e70
ms.openlocfilehash: cbd223560810ee1b97966b8bf8da7206cc2a7955


---

# <a name="restrict-access-to-company-resource-based-on-device-network-and-application-risk"></a>デバイス、ネットワーク、アプリケーションのリスクに基づいて、会社のリソースへのアクセスを制限します。
Microsoft Intune に統合されたデバイス脅威保護ソリューションである Lookout によって実行されるリスク評価に基づいて、モバイル デバイスから会社のリソースへのアクセスを制御することができます。 リスクの判断材料となるのは、Lookout サービスが、オペレーティング システム (OS) の脆弱性、インストール済みの悪意のあるアプリケーションと悪意のあるネットワーク プロファイルについてデバイスから収集したテレメトリです。 Intune コンプライアンス ポリシーで有効にした Lookout のリスク評価のレポートに基づいて、Intune 内で条件付きアクセス ポリシーを構成し、脅威が検出されたために非準拠と見なされたデバイスを許可するかブロックするかを決めることができます。  

## <a name="what-problem-does-this-solve"></a>どのような問題がこれにより解決されますか?
企業および組織は、物理的なアプリ ベースの脅威、ネットワーク ベースの脅威、OS の脆弱性など、新たな脅威から機密データを保護する必要があります。

これまで、企業や組織は、悪意のある攻撃からコンピューターを保護することに積極的に取り組んできました。 モバイルは、保護されていない状態で使用されることが多い、発展途上の領域です。 モバイル プラットフォームは、アプリの分離や検証済みコンシューマー アプリ ストアなどの手法を使用した OS における組み込み保護を備えていますが、依然として高度な攻撃を受けやすい状態にあります。 モバイル デバイスは、従業員によって仕事で使用されるケースがますます増えており、機密性の高い貴重な情報へのアクセスを必要としています。このため、これらのデバイスはさまざまな高度な攻撃から保護する必要があるのです。

Intune では、Lookout のようなデバイス脅威保護ソリューションで提供されているリスク評価に基づいて、会社のリソースおよびデータへのアクセスを制御する機能を提供しています。

## <a name="how-do-intune-and-lookout-device-threat-protection-help-protect-company-resources"></a>Intune および Lookout のデバイス脅威保護は会社リソースの保護にどのように役立ちますか?
モバイル デバイス上で実行されている Lookout のモバイル アプリ (Lookout for work) は、ファイル システム、ネットワーク スタック、デバイスおよびアプリケーションのテレメトリ (使用可能な場合) を取得し、それを Lookout デバイス脅威保護クラウド サービスに送信して、モバイル脅威に対するデバイスの総合的なリスクを算出します。 Lookout コンソールでは要件に合わせて、脅威に対するリスク レベルの分類を変更することもできます。  

Intune のコンプライアンス ポリシーには、Lookout デバイス脅威のリスク評価に基づく Lookout モバイル脅威保護の新しいルールが含まれています。 このルールを有効にすると、Microsoft Intune は、有効にされたポリシーに基づいてデバイスの準拠状態を評価します。

デバイスがコンプライアンス ポリシーに準拠していないと判断された場合、Exchange Online や SharePoint Online のようなリソースへのアクセスは条件付きアクセス ポリシーによってブロックすることができます。 アクセスがブロックされている場合、エンドユーザーは提供されているチュートリアルを参照して、問題を解決し、会社のリソースへのアクセス権を取得します。 このチュートリアルは作業用 Loogout アプリを介して起動されます。
## <a name="supported-platforms"></a>サポートされているプラットフォーム:
* Microsoft Intune に登録済みの **Android 4.1 以降**。
* Microsoft Intune に登録済みの **iOS 8 以降**。
Lookout がサポートするプラットフォームと言語については、[こちらの記事](https://personal.support.lookout.com/hc/en-us/articles/114094140253)を参照してください。

## <a name="prerequisites"></a>前提条件:
* Microsoft Intune のサブスクリプションおよび Azure Active Directory。
* Lookout Mobile EndPoint Security のエンタープライズ サブスクリプション。  詳細については、「[Lookout Mobile Endpoint Security](https://www.lookout.com/products/mobile-endpoint-security)」を参照してください。

## <a name="example-scenarios"></a>シナリオ例
一般的なシナリオを次に示します。
### <a name="control-access-based-on-threat-from-malicious-apps"></a>悪意のあるアプリの脅威に基づいてアクセスを制御する:
マルウェアなどの悪意のあるアプリがデバイス上で検出された場合、該当するデバイスの以下の動作をブロックすることができます。
* 脅威が排除される前に会社の電子メールに接続する。
* OneDrive for Work アプを使用して会社のファイルを同期する。
* ビジネス クリティカルなアプリにアクセスする。

**悪意のあるアプリが検出されたときにブロックされるアクセス:**
![悪意のあるアプリが検出されたことからデバイスが非準拠状態と判断された場合に、アクセスをブロックする条件付きアクセス ポリシーを示す図](../media/mtp/malicious-apps-blocked.png)

**脅威が修復されると、デバイスはブロックが解除され、会社のリソースにアクセスできるようになる:**

![修復後、デバイスが準拠状態にあると判断された場合にアクセス権を付与する条件付きアクセス ポリシーを示す図](../media/mtp/malicious-apps-unblocked.png)
### <a name="control-access-based-on-threat-to-network"></a>ネットワークに対する脅威に基づいてアクセスを制御する:
Man-in-the-middle 攻撃など、ネットワークに対する脅威を検出し、デバイスのリスクに基づいて WiFi ネットワークへのアクセスを制限します。

**WiFi 経由のネットワークへのアクセスがブロックされている:**
![ネットワークの脅威に基づいて WiFi アクセスをブロックする条件付きアクセスを示す図](../media/mtp/network-wifi-blocked.png)

**修復時に付与されるアクセス権:**

![脅威の修復時にアクセスを許可する条件付きアクセスを示す図](../media/mtp/network-wifi-unblocked.png)
### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>ネットワークに対する脅威に基づいて SharePoint Online へのアクセスを制御する:

Man-in-the-middle 攻撃など、ネットワークに対する脅威を検出し、デバイスのリスクに基づいて会社内のファイルの同期を阻止します。

**デバイス上で検出されたネットワークの脅威に基づいてアクセスがブロックされた SharePoint Online:**

![検出した脅威に基づいて SharePoint Online へのデバイスのアクセスをブロックする条件付きアクセスを示す図](../media/mtp/network-spo-blocked.png)


**修復時に付与されるアクセス権:**

![ネットワークの脅威が修復された後でアクセスを許可する条件付きアクセスを示す図](../media/mtp/network-spo-unblocked.png)

## <a name="next-steps"></a>次のステップ
このソリューションを実装するために実行する必要がある主な手順を次に示します。
1.  [Lookout モバイル脅威保護を使用してサブスクリプションを設定する](set-up-your-subscription-with-lookout-mtp.md)
2.  [Intune で Lookout MTP の接続を有効にする](enable-lookout-mtp-connection-in-intune.md)
3.  [Lookout for work アプリを構成および展開する](configure-and-deploy-lookout-for-work-apps.md)
4.  [コンプライアンス ポリシーの構成](enable-device-threat-protection-rule-in-compliance-policy.md)
5.  [Lookout の統合に関するトラブルシューティング](http://docs.microsoft.com/en-us/intune/troubleshoot/troubleshooting-lookout-integration)



<!--HONumber=Nov16_HO1-->


