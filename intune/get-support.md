---
title: Microsoft Intune のサポートを受ける方法 | Microsoft Intune
description: Microsoft Intune の有料サブスクリプションと試用版サブスクリプションについて、オンラインと電話によるサポートを受けます。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/09/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 7fc95d17-098e-4da5-8a09-a96476569dd9
ms.reviewer: cacamp
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: 11bcf3742270a3f32919b133efdc2ab3f0c4d2d1
ms.sourcegitcommit: 4a7421470569ce4efe848633bd36d5946f44fc8d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2019
ms.locfileid: "54203350"
---
# <a name="how-to-get-support-for-microsoft-intune"></a>Microsoft Intune のサポートを受ける方法

[!INCLUDE [azure_portal](./includes/note-for-both-portals.md)]

Microsoft サポートは、Microsoft Intune に世界的な技術、購入前、請求、およびサブスクリプションのサポートを提供しています。 有料サブスクリプションと試用版サブスクリプションについて、オンラインと電話によるサポートを利用できます。 オンライン テクニカル サポートは、英語と日本語で提供されています。 電話によるサポートとオンライン課金サポートは、他の言語でも利用できます。

>[!IMPORTANT]  
> Intune と連携するサードパーティ製品 (Saaswedo、Cisco、Lookout など) のテクニカル サポートについては、まず、その製品の提供元に連絡してください。 Intune サポート要求を開始する前に、その他の製品が正しく構成されていることを確認します。
>
> Microsoft Intune に関連する問題のトラブルシューティングについては、Intune のドキュメントの[トラブルシューティングに関するセクション](help-desk-operators.md)を参照してください。

IT 管理者は、**[ヘルプとサポート]** オプションを使用して、Azure portal から Intune 用のオンライン サポート チケットを提出することができます。 サポート チケットを作成するには、ご利用のアカウントを次のいずれかの [Azure Active Directory での管理者ロール](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal)に割り当てる必要があります。

- Intune 管理者
- 全体管理者
- サービス管理者  


## <a name="help-and-support-experience"></a>ヘルプとサポート エクスペリエンス
> [!TIP]   
> 2019 年 1 月、すべてのテナントに新しいヘルプとサポート エクスペリエンスがロールアウトされます。 テナントがこの新しいエクスペリエンスをまだ備えていない場合は、この記事にある「[Azure のヘルプとサポート エクスペリエンス](#azure-help-+-support-experience)」で、以前のエクスペリエンスに関する情報を確認できます。  

Intune のヘルプとサポート エクスペリエンスは、[Microsoft 365 デバイス管理ポータル](http://devicemanagement.microsoft.com)、および Azure portal の Intune のすべてのブレード (またはページ) から使用できます。 

![Intune のブレード](./media/get-support/intune-blades.png)


この新しいエクスペリエンスは、[Microsoft 365 管理センター](https://portal.office.com/AdminPortal/Home)で見られるエクスペリエンスと類似しており、[以前のヘルプとサポート エクスペリエンス](#azure-help-+-and-support-experience)に取って代わります。 

[ヘルプとサポート] にアクセスするには、次の手順に従います。  
- **デバイス管理ダッシュボード:**
   - **[ヘルプとサポート]** の使用可能な任意のオプションを選択する
   - ポータルの右上隅にある **[?]**  アイコンを選択する

- **Azure ポータル:**
   - Intune の任意のブレードまたはページから **[ヘルプとサポート]** を選択する

   右上隅にある **[?]**  アイコン、または Azure portal の任意の場所にある左側のナビゲーション ウィンドウで **[ヘルプとサポート]** を選択すると、Azure の *[ヘルプとサポート]* が開きます。 最良のエクスペリエンスを得るには、Intune のブレードにある *[ヘルプとサポート]* を使用します。  

新しいエクスペリエンスでは、次のデバイス管理ダッシュボードの画像のように、**[ヘルプが必要ですか?]** ビューにアクセスできます。  
![デバイス管理ダッシュボードと [ヘルプが必要ですか?] ページ](./media/get-support/help-support-dashboard.png)

このビューでは、以下の操作を行うことができます。

1. ヘルプが必要な特定の問題について[詳細を指定する](#specify-details-about-an-issue)  
2. 指定した詳細に基づき、[状況依存のヘルプ](#view-context-sensitive-help)と関連ソリューションを表示する  
3. 電子メールや電話を利用して[サポートを受ける](#get-support)  
4. この新しいワークフローを利用して前に[サポート ケース](#view-support-cases)を登録している場合、それを表示する  

### <a name="specify-details-about-an-issue"></a>問題に関する詳細を指定する
新しいエクスペリエンスでサポートされている場所から [ヘルプとサポート] を開くと、**[ヘルプが必要ですか?]** ページが  開きます。 このページで、問題の詳細を指定できます。 詳細を入力すると、使用したキーワードに基づき、よくある問い合わせがコンソールから提示されます。 提案を選択するか、自分で問題を説明できます。 自分で説明を入力する場合、**[ヘルプを表示]** を選択して送信します。 問い合わせを送信すると、問題の解決に役立つ可能性がある状況依存情報がコンソールから返されます。

次は、送信することがある問い合わせの例です。
  
- *iOS デバイスを復元できません*  
- *条件付きアクセス ポリシーを作成できません*  

![[ヘルプが必要ですか?] ページで問題を指定する](./media/get-support/describe-the-issue.png)

### <a name="view-context-sensitive-help"></a>状況依存のヘルプを表示する
提案を選択するか、独自の問い合わせを送信すると、**[ソリューションの表示]** の下に状況依存の結果が表示されます。 これらの結果には、Intune 固有のセルフヘルプ ガイダンスと、クエリ条件に基づく Web 検索から返された追加の結果の両方が含まれます。  
![結果の表示](./media/get-support/view-results.png)

### <a name="get-support"></a>サポートを受ける
セルフヘルプまたは Web ベースのガイダンスでは問題が解決されない場合、コンソールを使用し、電子メールまたは電話でサポートを受けることができます。  
**[ヘルプが必要ですか?]** ページで、使用するオプションを選択します。  

- 電子メールで依頼する場合、自分の電子メール アドレスを入力してください。任意で、提出に添付ファイルを追加できます。 **[送信]** を選択し、依頼を登録します。  

  ![電子メールによる依頼](./media/get-support/email-support.png)
  
- 電話で依頼する場合、自分の電話番号を入力してください。 任意で、自分の電子メール アドレスを含めたり、提出に添付ファイルを追加したりできます。 [電話で連絡] を選択し、依頼を提出します。  

   ![電話で依頼](./media/get-support/phone-support.png)

### <a name="view-support-cases"></a>サポート ケースを表示する
[履歴] ボタンを選択すると、作成したサポート インシデントが表示されます。  

![サポート ケースを表示する](./media/get-support/view-support-tickets.png)

- 新しいワークフローを使用して登録したサポート ケースだけがこのワークフロー内から表示されます。 サポート ケースを表示するには、デバイス管理コンソール、または Azure portal にある Intune のブレードで、[ヘルプとサポート] ビューを使用します。 これらのケースには 8 桁の数字が与えられます。 これらのケースは Microsoft 365 管理センターからも表示できます。  

- Intune のヘルプとサポート エクスペリエンスを使用していないときに開いたケースは、変更ありません。 そのようなケースを表示するには、Intune エクスペリエンスに含まれない [ヘルプとサポート] ビュー、またはデバイス管理ダッシュボードを使用する必要があります。 これらのケースには **117** または **118** で始まる 15 桁の数字が与えられます。 管理共有を表示するには

    1. Intune 管理者資格情報を使用して Azure (<https://portal.azure.com>) にサインインして、*[?]* を選択します。 アイコンを選択し、*[ヘルプとサポート]* を選択して、[Azure のヘルプとサポート](https://ms.portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/overview)のページに移動します。

    2. **ヘルプとサポート**のページでは、**最近のサポート要求**の一覧を表示し、さらにそれらを選択して詳細を確認することができます。


## <a name="azure-help--support-experience"></a>Azure のヘルプとサポート エクスペリエンス
次のセクションでは、左側のナビゲーション ウィンドウで **[ヘルプとサポート]** を使用するか、Azure portal の右上隅にある **[?]**  オプションを使用して、Azure portal から引き続きアクセスできる Azure のヘルプとサポート エクスペリエンスについて説明します。 2019 年 1 月より、Intune のブレードにある *[ヘルプとサポート]* から Azure の*ヘルプとサポート* エクスペリエンスにアクセスできなくなります。  

### <a name="create-an-online-support-ticket"></a>オンライン サポート チケットの作成

1. Intune 管理者資格情報を使用して Azure portal (<https://portal.azure.com>) にサインインして、**[?]** を選択します。 アイコンを選択し、**[ヘルプとサポート]** を選択して、[Azure のヘルプとサポート](https://ms.portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/overview)のページに移動します。

   ![[ヘルプとサポート] のリンクが強調表示された疑問符マークの画像](./media/azure-get-support.png)

2. Azure の **[ヘルプとサポート]** のページ上で、**[新しいサポート要求]** を選択します。

   ![[ヘルプとサポート] ページで [新しいサポート要求] のリンクが強調表示された画像](media/azure-support-ticket-link.png)

3. Intune のほとんどのテクニカル サポートの問題では、**[基本]** タブ上で、次のオプションを選択します。
   - **問題の種類**: **テクニカル**
   - **サブスクリプション**: <"*お使いのサブスクリプション*">
   - **サービス**:**Microsoft Intune**
   - **[問題の種類]**: ドロップダウン メニューから、問題の種類を選択します。
   - **[問題のサブタイプ]**: ドロップダウン メニューから、問題のサブタイプを選択します。
   - **[件名]**: 発生している問題を簡単に説明します。

   ![[ヘルプとサポート] の [基本] タブの画像 - [新しいサポート要求] ページ](./media/get-support/help-new-support-case-basics.png)

   **[Next: Solutions]\(次へ: ソリューション\)** を選択して続行します。
4. **[ソリューション]** タブ上で、チケットを提出しなくても問題の解決に役立つ可能性がある推奨手順を確認します。 手順を確認した後に、やはりサポート要求を作成することにした場合は、**[Next: Details]\(次へ: 詳細\)** をクリックします。

   ![[ヘルプとサポート] の [ソリューション] タブの画像 - [新しいサポート要求] ページ](./media/get-support/help-new-support-case-solutions.png)
5. **[詳細]** タブ上で、問題の詳細、サポートの方法、お客様の連絡先情報を入力してから、**[Next: Review + create]\(次へ: 確認と作成\)** をクリックします。

   ![[ヘルプとサポート] の [詳細] タブの画像 - [新しいサポート要求] ページ](./media/get-support/help-new-support-case-details.png)
6. 情報を見直して、正しいことを確認してから、**[作成]** を選択してサポート要求を送信します。

   ![[新しいサポート要求] ページの [review + create]\(確認と作成\) タブの画像](./media/get-support/help-new-support-case-create.png)

<!--
  - **Support plan**: **Technical support - included** (for Intune technical issues, support is complimentary) or **Premier**
     >[!IMPORTANT]
     >- If you are a **Premier customer** and don't see **Support plan: Premier**, contact your Technical Account Manager for help linking your contract and tenant.
     >- Support for Intune, and for Intune when used with Configuration Manager, is free of charge. To review details of the Premier Support offering, see the [Description of Services](https://enterprise.microsoft.com/en-us/services/services-list/) documentation, section 5.3.3 "Advisory Services."

4. On the **Problem** blade, to make sure your request is addressed by the right subject matter expert for your problem, select the following options:

   - **Severity**
   - **Problem type**
   - **Category**

     These details also let us provide **Related help** that might solve your problem without filing a ticket.

     ![Screenshot of Azure portal help and support page with Problem items filled out and displaying solutions based on your problem](./media/support-need-solutions.png)

     To help the support team research and resolve your problem, enter the following information:
    
   - **Details**
   - **Date**
   - **Time**
   - **Supplemental data**

   Choose **Next**.

5. Provide **Contact information** for this support request. Microsoft support uses this information to contact you.
6. Choose **Create** to submit your support request.
-->
>[!IMPORTANT]
>請求やサブスクリプションの質問がある場合は、ケースを開いて [Office 管理センター](https://portal.office.com/Support/SupportEntry.aspx)からサポートを受けることができます。

### <a name="view-support-requests"></a>サポート要求を表示する
Azure portal 内からサポート要求を表示できます。 これを実行するには、次のようにします。

1. Intune 管理者資格情報を使用して Azure (<https://portal.azure.com>) にサインインして、**[?]** を選択します。 アイコンを選択し、**[ヘルプとサポート]** を選択して、[Azure のヘルプとサポート](https://ms.portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/overview)のページに移動します。

2. **ヘルプとサポート**のページでは、**最近のサポート要求**の一覧を表示し、さらにそれらを選択して詳細を確認することができます。

## <a name="additional-resources"></a>その他のリソース
- [Microsoft Intune のサポートの電話番号](phone-support-contact.md)
- [課金とサブスクリプション管理のサポート](https://support.office.com/article/Contact-Office-365-for-business-support-Admin-Help-32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)
- [ボリューム ライセンス](https://go.microsoft.com/fwlink/p/?LinkID=282015)
- [Intune の問題のトラブルシューティング](help-desk-operators.md)