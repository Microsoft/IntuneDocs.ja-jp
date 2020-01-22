---
title: Intune で Wandera モバイル セキュリティを設定する
titleSuffix: Intune on Azure
description: Microsoft Intune で Wandera モバイル セキュリティを設定し、会社のリソースに対するモバイル デバイスのアクセスを制御する方法。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 50973d883a3d31089e16dca5a9021643a821a3fb
ms.sourcegitcommit: 52475fcd8d05d2f6b858d780ebb3d88eaadb0849
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/15/2020
ms.locfileid: "76036631"
---
# <a name="wandera-mobile-threat-defense-connector-with-intune"></a>Wandera Mobile Threat Defense コネクタと Intune  

Wandera によって実施されるリスク評価に基づく条件付きアクセスを使って、会社のリソースに対するモバイル デバイスのアクセスを制御します。 Wandera は、Microsoft Intune と統合されている Mobile Threat Defense (MTD) ソリューションです。  リスクは、Wandera サービスによりデバイスから収集される次のようなテレメトリに基づいて評価されます。
- オペレーティング システムの脆弱性
- インストールされた悪意のあるアプリ
- 悪意のあるネットワーク プロファイル
- クリプトジャッキング

Intune のデバイス コンプライアンス ポリシーを通じて有効にすることで、Wandera のリスク評価に基づく "*条件付きアクセス*" ポリシーを構成できます。 リスク評価ポリシーは、検出された脅威に基づき、非準拠デバイスの企業リソースへのアクセスを許可またはブロックすることができます。  


## <a name="how-do-intune-and-wandera-mobile-threat-defense-help-protect-your-company-resources"></a>Intune および Wandera Mobile Threat Defense が会社のリソースの保護に役立つしくみ  

Wandera のモバイル アプリは、Microsoft Intune を使用してシームレスにインストールされます。 このアプリにより、ファイル システム、ネットワーク スタック、デバイスとアプリケーションのテレメトリ (入手できる場合) がキャプチャされます。 この情報は Wandera のクラウド サービスと同期され、モバイルの脅威に対するデバイスのリスクが評価されます。 これらのリスク レベルの分類は、Wandera のコンソールである RADAR で、ご自身のニーズに合わせて構成できます。

Intune のコンプライアンス ポリシーには、Wandera のリスク評価に基づく MTD のルールが含まれています。 このルールを有効にすると、Intune は、有効にされたポリシーに基づいてデバイスの準拠状態を評価します。

非準拠のデバイスについては、Office 365 などのリソースへのアクセスをブロックできます。 ブロックされたデバイスを使っているユーザーには、問題を解決してアクセスを回復するためのガイダンスが Wandera アプリから届きます。

## <a name="supported-platforms"></a>サポートされているプラットフォーム  

Intune に登録したとき、Wandera では次のプラットフォームがサポートされます。

- Android 5.0 以降  
- iOS 10.2 以降  

プラットフォームとデバイスについて詳しくは、[Wandera の Web サイト](https://www.wandera.com/classic-help-center/)をご覧ください。

## <a name="prerequisites"></a>[前提条件]  

- Microsoft Intune サブスクリプション  
- Azure Active Directory  
- Wandera Mobile Threat Defense (旧称 Wandera Secure)  

詳細については、[Wandera モバイル セキュリティ](https://www.wandera.com/mobile-security/)に関するページをご覧ください。
 
## <a name="sample-scenarios"></a>サンプル事例

Intune で Wandera MTD を使用する場合の一般的なシナリオを次に示します。

### <a name="control-access-based-on-threats-from-malicious-apps"></a>悪意のあるアプリの脅威に基づいてアクセスを制御する  

マルウェアなどの悪意のあるアプリがデバイス上で検出された場合、脅威を解決できるまで、デバイスでの一般的なツールの使用をブロックすることができます。 一般的なブロック対象には次が含まれます。  
- 会社の電子メールに接続する  
- OneDrive for Work アプリを使用して会社のファイルを同期する  
- 会社のアプリにアクセスする  

**悪意のあるアプリが検出されたときにブロックする**:

![検出された悪意のあるアプリの概念図](./media/wandera-mtd-connector/wandera-malicious-apps-blocked.png)  

**修復するとアクセス権が付与される**: 

![修復後に付与されたアクセス権の概念図](./media/wandera-mtd-connector/wandera-malicious-apps-unblocked.png)


### <a name="control-access-based-on-threat-to-network"></a>ネットワークに対する脅威に基づいてアクセスを制御する  

中間者攻撃などのネットワークに対する脅威を検出し、デバイスのリスクに基づいて Wi-Fi ネットワークへのアクセスを保護します。  

**Wi-Fi 経由のネットワーク アクセスをブロックする**:  

![Wi-Fi 経由のネットワーク アクセスをブロックする](./media/wandera-mtd-connector/wandera-network-wifi-blocked.png)

**修復するとアクセス権が付与される**:  

![修復後に許可されるアクセス](./media/wandera-mtd-connector/wandera-network-wifi-unblocked.png)  

## <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>ネットワークへの脅威に基づいて SharePoint Online へのアクセスを制御する

Man-in-the-middle 攻撃のようなネットワークの脅威を検出し、デバイス リスクに基づき、企業ファイルの同期を制限します。

**ネットワークの脅威が検出されたときに SharePoint Online をブロック**:  

![ネットワークの脅威が検出されたときに SharePoint Online をブロック](./media/wandera-mtd-connector/wandera-network-spo-blocked.png)  


**修復するとアクセス権が付与される**:  

![SharePoint で修復時にアクセス権が付与される例](./media/wandera-mtd-connector/wandera-network-spo-unblocked.png)  

## <a name="next-steps"></a>次のステップ

- [Wandera を Intune と統合する](wandera-mtd-connector-integration.md)
- [Wandera アプリの設定](mtd-apps-ios-app-configuration-policy-add-assign.md)
- [Wandera デバイス コンプライアンス ポリシーの作成](mtd-device-compliance-policy-create.md)
- [Wandera MTD コネクタを有効にする](mtd-connector-enable.md)
