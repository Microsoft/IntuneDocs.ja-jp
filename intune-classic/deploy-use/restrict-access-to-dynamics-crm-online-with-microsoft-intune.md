---
title: "Dynamics CRM Online を保護する"
description: "条件付きアクセスで Dynamics CRM Online へのアクセスを保護および制御します。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 01/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f1c4522b-5a34-4f5a-89d2-7809c4352af7
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: e2f720c8a6613884397111c2a421fa1cfdc0eb53
ms.sourcegitcommit: 2459bfda07a2afd2cfcd94a1972a3fb2e565ce8d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/22/2018
---
# <a name="protect-access-to-dynamics-crm-online-with-intune"></a>Intune で Dynamics CRM Online へのアクセスを保護する

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Microsoft Intune の条件付きアクセスを使用して、iOS および Android デバイスから Microsoft Dynamics CRM Online へのアクセスを制御できます。  Intune の条件付きアクセスには、次の 2 つのコンポーネントがあります。
* [デバイス コンプライアンス ポリシー](introduction-to-device-compliance-policies-in-microsoft-intune.md)。準拠したデバイスと見なされるには、このポリシーに準拠している必要があります。
* [条件付きアクセス ポリシー](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)。デバイスがサービスにアクセスするために満たす必要のある条件を指定します。

条件付きアクセスの動作の詳細については、「[Microsoft Intune で電子メール、Office 365、およびその他のサービスへのアクセスを制限する](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)」という記事をご覧ください。

> [!IMPORTANT]
> 条件付きアクセスを展開するには、Intune および Azure Active Directory Premium のサブスクリプションが必要です。ユーザーに両方のライセンスが付与されている必要があります。 **Enterprise Mobility + Security (EMS) のサブスクリプション**には、Intune および Azure Active Directory Premium のサブスクリプションが両方とも含まれます。 詳細については、「[Enterprise Mobility pricing page](https://www.microsoft.com/cloud-platform/enterprise-mobility-pricing)」 (Enterprise Mobility の価格) ページを参照してください。 EMS のサブスクリプションを持っていない場合は、Azure Active Directory Premium のサブスクリプションを取得できます。 「[Azure Active Directory の価格](https://azure.microsoft.com/pricing/details/active-directory/)」ページを参照してください。

対象となるユーザーがデバイスで Dynamics CRM アプリを使用しようとすると、次の評価が行われます。

![図は、デバイスがサービスへのアクセスを許可されているか、またはブロックされているかを決定するために使用する判断ポイントを示しています](../media/mdm-ca-dynamics-crm-flow-diagram.png)

Dynamics CRM Online にアクセスするデバイスは、次の条件を満たしている必要があります。
* **Android** デバイスまたは **iOS** デバイスである。
* Intune に**登録**されている。
* 展開されているすべての Intune コンプライアンス ポリシーに**準拠**している。

デバイスの状態は Azure Active Directory に格納され、指定した条件に基づいて、アクセスが許可されたりブロックされたりします。

条件が満たされない場合、ユーザーにはサインイン時に以下のうちのいずれかのメッセージが表示されます。
* デバイスが Intune または Azure Active Directory に登録されていない場合は、会社ポータルのアプリをインストールおよび登録する手順を含むメッセージが表示されます。
* デバイスが準拠していない場合は、Microsoft Intune のポータル Web サイトまたはポータル サイト アプリにユーザーを誘導するメッセージが表示されます。このポータルで、ユーザーは問題とその解決方法に関する情報を確認できます。

## <a name="configure-conditional-access-for-dynamics-crm-online"></a>Dynamics CRM Online の条件付きアクセスの構成  
### <a name="step-1-configure-active-directory-security-groups"></a>手順 1. Active Directory セキュリティ グループを構成する

開始する前に、条件付きアクセス ポリシーの Azure Active Directory セキュリティ グループを構成します。 これらのグループは、**Office 365 管理センター**で構成できます。 これらのグループは、ユーザーをポリシーの対象とするか、または除外するために使用されます。 ユーザーがポリシーの対象となる場合、ユーザーに使用される各デバイスがリソースにアクセスするには、ポリシーを遵守している必要があります。

Dynamics CRM ポリシーに使用する 2 つのグループの種類を指定できます。
* **対象グループ**。 ポリシーを適用するユーザーのグループが含まれます。
* **例外グループ**。 ポリシーから除外されるユーザーのグループが含まれます。

ユーザーが両方のグループに含まれている場合は、ポリシーから除外されます。

### <a name="step-2-configure-and-deploy-a-compliance-policy"></a>手順 2. コンプライアンス ポリシーを構成し、展開する
コンプライアンス ポリシーを[作成](create-a-device-compliance-policy-in-microsoft-intune.md)し、ポリシーによって影響を受けるすべてのデバイスに[展開](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md)します。 これは、対象グループ内のユーザーによって使用されるすべてのデバイスです。

> [!NOTE]
> コンプライアンス ポリシーは Intune グループに展開されますが、条件付きアクセス ポリシーは、Azure Active Directory セキュリティ グループを対象とします。

> [!IMPORTANT]
> コンプライアンス ポリシーを展開していない場合は、デバイスがポリシーに準拠しているものと見なされます。

準備ができたら、手順 3 に進みます。
### <a name="step-3-configure-the-dynamics-crm-policy"></a>手順 3: Dynamics CRM ポリシーを構成する
次に、管理デバイスおよび準拠デバイスのみが Dynamics CRM にアクセスできるように必要なポリシーを構成します。 このポリシーは、Azure Active Directory に格納されます。

1. Intune 管理コンソールで、**[ポリシー]、[条件付きアクセス]、[Dynamics CRM Online ポリシー]** の順に選択します。

   ![Dynamics CRM Online の条件付きアクセス ポリシー ページのスクリーンショット](../media/mdm-ca-dynamics-crm-policy-configuration.png)

2. **[条件付きアクセス ポリシーを有効にする]** を選択します。
3. **[アプリケーション アクセス]** で、条件付きアクセス ポリシーを適用する対象を次のように選ぶことができます。
   * **Android**
   * **Android**
4. **[対象グループ]**で、**[変更]** を選択して、ポリシーを適用する Azure Active Directory セキュリティ グループを選択します。 すべてのユーザーを対象にすることも、選んだユーザーのグループのみを対象にすることもできます。
5. **[例外グループ]**で、必要に応じて **[変更]** を選択して、このポリシーから除外する Azure Active Directory セキュリティ グループを選択します。
6. 終了したら、 **[保存]**をクリックします。

これで、Dynamics CRM の条件付きアクセスの構成が完了しました。 条件付きアクセス ポリシーを展開する必要はありません。直ちに有効になります。
##  <a name="monitor-the-compliance-and-conditional-access-policies"></a>コンプライアンスと条件付きアクセス ポリシーを監視する

**[グループ]** ワークスペースで、デバイスの条件付きアクセスの状態を表示できます。

モバイル デバイス グループを選択し、**[デバイス]** タブで、次の **[フィルター]**のいずれかを選択します。
* **AAD に登録されていないデバイス**。 これらのデバイスは Dynamics CRM からブロックされます。
* **準拠していないデバイス**。 これらのデバイスは Dynamics CRM からブロックされます。
* **AAD に登録され、準拠しているデバイス**。 これらのデバイスで Dynamics CRM にアクセスできます。

##  <a name="next-steps"></a>次の手順
* [Exchange Online へのアクセスを保護する](restrict-access-to-exchange-online-with-microsoft-intune.md)

* [Exchange On-Premises へのアクセスを保護する](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
* [SharePoint Online へのアクセスを保護する](restrict-access-to-sharepoint-online-with-microsoft-intune.md)

* [Skype for Business Online へのアクセスを保護する](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)
