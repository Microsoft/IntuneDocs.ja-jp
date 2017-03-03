---
title: "デバイスの防御ルールを有効にする | Microsoft Docs"
description: "デバイスのコンプライアンス ポリシーでモバイル脅威防御ルールを有効にします。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c951692d-6538-46c0-a9f0-d607ded189ae
ms.reviewer: sandera
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 9f05e516723976dcf6862475dbb78f9dce2913be
ms.openlocfilehash: 08edca426901eda3017bf17dda3b330dd186ce58


---

# <a name="enable-device-threat-protection-rule-in-the-compliance-policy"></a>コンプライアンス ポリシーでデバイスの脅威防御ルールを有効にする

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune と Lookout Mobile Threat Protection を使用することで、モバイル デバイスの脅威を検出し、デバイスのリスクを評価することができます。 リスクを評価するコンプライアンス ポリシー ルールを作成すれば、デバイスがポリシーに準拠しているかどうかを判断できます。 条件付きアクセス ポリシーを使用すれば、デバイスのコンプライアンスに基づいて、サービスへのアクセスを禁止できます。

Lookout デバイス脅威保護を含むコンプライアンス ポリシーに関する前提条件:

- [Lookout デバイス脅威保護サブスクリプションをセットアップする](set-up-your-subscription-with-lookout-mtp.md)
- [Intune で Lookout の接続を有効にする](enable-lookout-mtp-connection-in-intune.md)
- [Lookout for Work アプリを構成する](configure-and-deploy-lookout-for-work-apps.md)

Lookout デバイス脅威保護をセットアップするときに、[Lookout コンソール](https://aad.lookout.com)で、さまざまな脅威を高、中、低として分類するポリシーを作成しました。 Intune のコンプライアンス ポリシーでは、許容される最大脅威レベルを設定します。

1. [Intune 管理者コンソール](https://manage.microsoft.com)で、**[コンプライアンス ポリシー]** ページに移動します。 既存のコンプライアンス ポリシーを使用することも、新たに作成することもできます。 **[デバイスのヘルス]** に移動して、**[デバイス脅威保護]** を有効にします。
  ![デバイス脅威防御ルールの設定を示すスクリーンショット ](../media/mtp/mtp-compliance-policy-rule.png)

2. **[許容される驚異の最大レベル]** を選択します。
  * **[なし (セキュリティ保護)]**: これはセキュリティ上最も安全です。  デバイスにいかなる脅威も存在できず、デバイスからは引き続き会社のリソースにアクセスできます。  いずれかの脅威が見つかった場合、デバイスは非準拠と評価されます。  
  * **[低]**: 存在する脅威が低レベルの場合のみ、デバイスは準拠しています。 低レベルより高い脅威が存在する場合、デバイスは非準拠状態になります。
  * **[中]**: デバイスに存在する脅威が低レベルまたは中レベルの場合、デバイスは準拠しています。 高レベルの脅威が検出された場合は、デバイスは非準拠と判定されます。
  * **[High]** (高): 最も安全性の低い状態です。 この場合、すべての脅威レベルが許可され、レポート目的のみで Lookout Mobile Threat Protection が使用されます。

![デバイス脅威防御ルール設定の脅威レベル オプションを示すスクリーンショット](../media/mtp/mtp-compliance-policy-setting.png)

Office 365 またはその他のサービスに対する条件付きアクセス ポリシーを作成すると、このコンプライアンス評価が適用され、非準拠デバイスは脅威が解決されるまでサービスへのアクセスは禁止されます。

## <a name="monitor-device-threats"></a>デバイス脅威の監視
デバイスのコンプライアンス状態を確認するには、**Intune 管理者コンソール**に移動し、[[すべてのデバイス]](https://manage.microsoft.com) を表示します。

![デバイスのコンプライアンス状態が表示されている Intune 管理者コンソールのデバイス ページのスクリーンショット](../media/mtp/mtp-device-status-intune-console.png)

## <a name="next-steps"></a>次のステップ
* 条件付きアクセス ポリシーを作成します
  * [Exchange Online](restrict-access-to-exchange-online-with-microsoft-intune.md)
  * [Exchange On-premises](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
  * [SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md)
  * [Skype for Business Online](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)
  * [Dynamics CRM](restrict-access-to-dynamics-crm-online-with-microsoft-intune.md)



<!--HONumber=Jan17_HO4-->


