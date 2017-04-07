---
title: "Skycure Mobile Threat Defense コンプライアンス ポリシーを作成する | Microsoft Docs"
description: "Intune クラシック コンソールで Skycure Mobile Threat Defense コンプライアンス ポリシーを作成します。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 56ff1728-1119-4e8a-aae6-ed5c7fafa052
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: e76d66768ac58df25313e102b7f60d2bc7bbc59b
ms.openlocfilehash: 3a7322bd389b6d2ca72108b9f54318000857895b
ms.lasthandoff: 03/22/2017


---

# <a name="create-skycure-mobile-threat-defense-compliance-policy"></a>Skycure Mobile Threat Defense コンプライアンス ポリシーを作成する

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune と Skycure Mobile Threat Defense を使用することで、モバイル デバイスの脅威を検出し、デバイスのリスクを評価することができます。 リスクを評価する Intune コンプライアンス ポリシー ルールを作成すれば、デバイスがポリシーに準拠しているかどうかを判断できます。 条件付きアクセス ポリシーを使用すれば、デバイスのコンプライアンスに基づいて、サービスへのアクセスを禁止できます。

## <a name="before-you-begin"></a>始める前に

Skycure デバイス脅威保護を含むコンプライアンス ポリシーに関する前提条件:

-   [Skycure と Intune の統合をセットアップする](https://docs.microsoft.com/en-us/intune/deploy-use/setup-the-skycure-integration-with-Intune)

-   [Intune で Skycure の接続を有効にする](https://docs.microsoft.com/intune/deploy-use/enable-skycure-mobile-threat-defense-in-intune)

Skycure Mobile Threat Defense をセットアップするときに、Skycure コンソールで、さまざまな脅威を高、中、低として分類するポリシーを作成しました。 Intune コンプライアンス ポリシーでは、許容される最大脅威レベルを設定する必要があります。

## <a name="to-create-skycure-compliance-policy"></a>Skycure コンプライアンス ポリシーを作成するには

1.  [Intune クラシック コンソール](https://manage.microsoft.com/)に進み、資格情報を入力します。

2.  **[ポリシー]** &gt; **[コンプライアンス ポリシー]** の順に選択します。 既存のコンプライアンス ポリシーを使用することも、新たに作成することもできます。

3.  **[追加]** &gt; **[デバイスのヘルス]** の順に選択し、**[デバイス脅威保護]** を有効にします。

4.  **[許容される驚異の最大レベル]** を選択します。

    a.  **[なし (セキュリティ保護)]**: これはセキュリティ上最も安全です。 デバイスにいかなる脅威も存在できず、デバイスからは引き続き会社のリソースにアクセスできます。 いずれかの脅威が見つかった場合、デバイスは非準拠と評価されます。

    b.  **[低]**: 存在する脅威が低レベルの場合のみ、デバイスは準拠しています。 低レベルより高い脅威が存在する場合、デバイスは非準拠状態になります。

    c.  **[中]**: デバイスに存在する脅威が低レベルまたは中レベルの場合、デバイスは準拠しています。 高レベルの脅威が検出された場合は、デバイスは非準拠と判定されます。

    d.  **[High]** (高): 最も安全性の低い状態です。 この場合、すべての脅威レベルが許可され、レポート目的のみで Skycure Mobile Threat Defense が使用されます。

> [!IMPORTANT] 
> Office 365 またはその他のサービスに対する条件付きアクセス ポリシーを作成すると、このコンプライアンス評価が適用され、非準拠デバイスは脅威が解決されるまでサービスへのアクセスは禁止されます。

## <a name="span-idmonitor-device-threats-classanchorspan-idnext-steps-classanchorspan-idtoc477360344-classanchorspanspanspannext-steps"></a><span id="monitor-device-threats" class="anchor"><span id="next-steps" class="anchor"><span id="_Toc477360344" class="anchor"></span></span></span>次の手順

-   次の条件付きアクセス ポリシーを作成します。

    -   [Exchange Online](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune)
    -   [Exchange On-premises](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-exchange-onpremises-with-microsoft-intune)
    -   [SharePoint Online](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune)
    -   [Skype for Business Online](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-skype-for-business-online-with-microsoft-intune)
    -   [Dynamics CRM](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-dynamics-crm-online-with-microsoft-intune)

