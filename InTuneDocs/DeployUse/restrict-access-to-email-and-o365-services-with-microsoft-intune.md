---
title: "電子メールおよび O365 サービスへのアクセスを制限する | Microsoft Intune"
description: "このトピックでは、条件式を使用して、準拠デバイスのみに SharePoint Online およびその他のサービスの会社の電子メールや会社データへのアクセスを許可する方法について説明します。"
keywords: 
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 07/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c564d292-b83b-440d-bf08-3f5b299b7a5e
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 99b01f5ca5bb389fc8a9d87e956796823fee6c0d
ms.openlocfilehash: 6e11d71265f01ae31ab3124a46aaa544ad2f453a


---

# Microsoft Intune で電子メール、O365、およびその他のサービスへのアクセスを制限する
Intune の条件付きアクセスを使用して、会社の電子メールおよび O365 サービスへのアクセスを制限することができます。 Intune の条件付きアクセス機能により、会社の電子メールおよび O365 サービスへのアクセスを、設定した規則に準拠するデバイスに制限することができます。
## 条件付きアクセスのしくみ
コンプライアンス ポリシーの設定は、デバイスのコンプライアンスの評価に使用されます。 条件付きアクセス ポリシーは、この評価を使用して、特定のサービスへのアクセスを制限または許可します。 条件付きアクセス ポリシーがコンプライアンス ポリシーとの組み合わせで使用される場合、準拠するデバイスのみがサービスへのアクセスを許可されます。 コンプライアンス ポリシーと条件付きアクセス ポリシーはユーザーに対して展開されます。 サービスへのアクセスにユーザーが使用するすべてのデバイスは、ポリシーによってコンプライアンスがチェックされます。

デバイスを使用しているユーザーは、デバイスのコンプライアンスを評価するため、ユーザーにコンプライアンス ポリシーを展開しておく必要があることに注意してください。
コンプライアンス ポリシーがユーザーに展開されていない場合、デバイスは準拠したものと見なされ、アクセス制限は適用されません。

ポリシーに設定した条件をデバイスが満たしていない場合、デバイスの登録と、デバイスが準拠デバイスとなることを妨げている問題の修正を行うプロセスがエンド ユーザーに案内されます。

条件付きアクセスの一般的なフロー:

![図は、デバイスがサービスへのアクセスを許可されているか、またはブロックされているかを決定するために使用する判断ポイントを示しています](../media/ConditionalAccess4.png)

## 条件付きアクセスを構成する方法
条件付きアクセスを使用して管理できるのは、Microsoft **Exchange On-premises**、**Exchange Online**、**Exchange Online Dedicated**、**SharePoint Online**、および **Skype for Business Online** です。

条件付きアクセスを設定するには、デバイスのコンプライアンス ポリシーと条件付きアクセス ポリシーを構成します。

コンプライアンス ポリシーには、パスコード、暗号化、デバイスの脱獄の有無といった設定が含まれています。 準拠したデバイスと見なされるには、これらの規則を満たす必要があります。

次に基づいてアクセスを制限するための条件付きアクセス ポリシーを設定することができます。
- デバイスのコンプライアンス状態。
- デバイスで実行されているプラットフォーム。
- サービスにアクセスするために使用するアプリの種類。

他の Intune ポリシーとは異なり、条件付きアクセス ポリシーは展開しません。 代わりに、ポリシーを構成して、そのポリシーが必要なユーザーを選択すると、ポリシーがすべての対象ユーザーに適用されます。 ユーザーがポリシーの対象となる場合、ユーザーに使用される各デバイスがリソースにアクセスするには、ポリシーを遵守している必要があります。


## 次のステップ
1. [デバイスのコンプライアンス ポリシーとそのしくみについて理解する ](introduction-to-device-compliance-policies-in-microsoft-intune.md)

2. [コンプライアンス ポリシーの作成](create-a-device-compliance-policy-in-microsoft-intune.md)

2.  次のいずれかの条件付きアクセス ポリシーを作成します。
> [!div class="op_single_selector"]
  - [Exchange Online の条件付きアクセス ポリシーを作成する](restrict-access-to-exchange-online-with-microsoft-intune.md)
  - [Exchange On-premises の条件付きアクセス ポリシーを作成する](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
  - [Exchange Online Dedicated の条件付きアクセス ポリシーを作成する](restrict-access-to-exchange-online-with-microsoft-intune.md)
  - [古い Exchange Online Dedicated の条件付きアクセス ポリシーを作成する](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
  - [SharePoint Online の条件付きアクセス ポリシーを作成する](restrict-access-to-sharepoint-online-with-microsoft-intune.md)
  - [Skype for Business Online の条件付きアクセス ポリシーを作成する](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)
  - [Dynamics CRM Online の条件付きアクセス ポリシーを作成する](restrict-access-to-dynamics-crm-online-with-microsoft-intune.md)



<!--HONumber=Sep16_HO3-->


