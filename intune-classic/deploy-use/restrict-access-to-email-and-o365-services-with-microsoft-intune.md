---
title: "電子メールおよび Office 365 を保護する"
description: "このトピックでは、条件付きアクセスを使用し、準拠デバイスのみに SharePoint Online およびその他のサービスの会社の電子メールや会社データへのアクセスを許可する方法について説明します。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 01/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c564d292-b83b-440d-bf08-3f5b299b7a5e
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: e121a3aaf4988bd92c36eb79131b2205263fb309
ms.sourcegitcommit: 2459bfda07a2afd2cfcd94a1972a3fb2e565ce8d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/22/2018
---
# <a name="protect-access-to-email-office-365-and-other-services-with-microsoft-intune"></a>Microsoft Intune で電子メール、Office 365、およびその他のサービスへのアクセスを保護する

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

会社の電子メールへのアクセス、**Exchange On-premises**、**Exchange Online**、**Exchange Online Dedicated**、**SharePoint Online**、**Skype for Business Online** のような Office 365 サービスへのアクセス、その他のサービスへのアクセスを Enterprise Mobility + Security (EMS) 条件付きアクセスで保護できます。 この機能では、会社の電子メールや Office 365 サービスへのアクセスを、Intune 管理コンソールまたは Azure クラシック ポータルで設定した条件付きアクセス ルールに準拠するデバイスに限定できます。
## <a name="how-does-conditional-access-work"></a>条件付きアクセスのしくみ
コンプライアンス ポリシーの設定を利用し、デバイスのコンプライアンスを評価できます。 条件付きアクセス ポリシーは、この評価を使用して、特定のサービスへのアクセスを制限または許可します。 条件付きアクセス ポリシーがデバイス コンプライアンス ポリシーとの組み合わせで使用される場合、準拠するデバイスのみがサービスへのアクセスを許可されます。 コンプライアンス ポリシーと条件付きアクセス ポリシーはユーザーに対して展開されます。 サービスへのアクセスにユーザーが使用するすべてのデバイスは、ポリシーによってコンプライアンスがチェックされます。

> [!IMPORTANT]
> デバイスを使用しているユーザーは、デバイスのコンプライアンスを評価するため、ユーザーにコンプライアンス ポリシーを展開しておく必要があることに注意してください。
> コンプライアンス ポリシーがユーザーに展開されていない場合、デバイスは準拠したものと見なされ、アクセス制限は適用されません。

ポリシーに設定した条件をデバイスが満たしていない場合、デバイスの登録と、デバイスが準拠デバイスとなることを妨げている問題の修正を行うプロセスがエンド ユーザーに案内されます。

条件付きアクセスの一般的なフロー:

![図は、デバイスがサービスへのアクセスを許可されているか、またはブロックされているかを決定するために使用する判断ポイントを示しています](../media/ConditionalAccess4.png)

## <a name="setup-considerations"></a>セットアップに関する注意点

### <a name="licensing"></a>ライセンス

Microsoft Intune と Azure Active Directory (Azure AD) Premium はシームレスに連動し、EMS 条件付きアクセスで複数のコントロール層を提供します。Intune で条件付きアクセス ポリシーを展開する場合、両方の製品のライセンスが必要です。

**Azure AD Premium ライセンス**はスタンドアロン サービスとして購入するか、Enterprise Agreement の一部として (Intune と共に) 購入できます。 Intune で条件付きアクセス ポリシーを展開した場合、適切な Azure AD Premium または **EMS のライセンス**を取得していることを確認してください。

- 詳細については、[Enterprise Mobility の価格に関するページ](https://www.microsoft.com/cloud-platform/enterprise-mobility-pricing)または [Azure Active Directory の価格に関するページ](https://azure.microsoft.com/pricing/details/active-directory/)を参照してください。

また、条件付きアクセス ポリシーを適用する予定のユーザーに [Azure AD Premium または EMS のライセンスが割り当てられている](/intune/licenses-assign)ことを確認してください。

### <a name="device-compliance-settings"></a>デバイス コンプライアンス設定

条件付きアクセスを設定するには、デバイスのコンプライアンス ポリシーと条件付きアクセス ポリシーを構成します。 コンプライアンス ポリシーには、パスコード、暗号化、デバイスの脱獄の有無といった設定が含まれています。 準拠したデバイスと見なされるには、これらの規則を満たす必要があります。

- [デバイス コンプライアンス ポリシーとそのしくみについて理解する](introduction-to-device-compliance-policies-in-microsoft-intune.md)。

### <a name="conditional-access-policy"></a>条件付きアクセス ポリシー

次に基づいてアクセスを保護するための条件付きアクセス ポリシーを設定することができます。
- デバイスのコンプライアンス状態。
- デバイスで実行されているプラットフォーム。
- サービスにアクセスするために使用するアプリの種類。

他の Intune ポリシーとは異なり、条件付きアクセス ポリシーは展開しません。 代わりに、ポリシーを構成して、そのポリシーが必要なユーザーを選択すると、ポリシーがすべての対象ユーザーに適用されます。 ユーザーがポリシーの対象となる場合、ユーザーに使用される各デバイスがリソースにアクセスするには、ポリシーを遵守している必要があります。


## <a name="next-steps"></a>次の手順


2. [デバイス コンプライアンス ポリシーの作成](create-a-device-compliance-policy-in-microsoft-intune.md)。

3. 次の Microsoft クラウド サービス/製品のいずれかの条件付きアクセス ポリシーを作成します。

   - [Exchange Online の条件付きアクセス ポリシーを作成する](restrict-access-to-exchange-online-with-microsoft-intune.md)
   - [Exchange On-premises の条件付きアクセス ポリシーを作成する](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
   - [Exchange Online Dedicated の条件付きアクセス ポリシーを作成する](restrict-access-to-exchange-online-with-microsoft-intune.md)
   - [古い Exchange Online Dedicated の条件付きアクセス ポリシーを作成する](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
   - [SharePoint Online の条件付きアクセス ポリシーを作成する](restrict-access-to-sharepoint-online-with-microsoft-intune.md)
   - [Skype for Business Online の条件付きアクセス ポリシーを作成する](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)
   - [Dynamics CRM Online の条件付きアクセス ポリシーを作成する](restrict-access-to-dynamics-crm-online-with-microsoft-intune.md)
