---
title: Microsoft Intune の使用条件の設定
titlesuffix: ''
description: Intune 用ポータル サイトでユーザーに表示する使用条件を設定します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/20/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4a3a11a8-9c0c-4334-8c6b-6fea4d0a2efb
ms.reviewer: amyro
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: d126852366ff67adbbfecd2eb5ebe14a129c5945
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2019
ms.locfileid: "55839232"
---
# <a name="terms-and-conditions-for-user-access"></a>ユーザー アクセスに関する使用条件

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune 管理者は、ユーザーがポータル サイトを使用して以下の操作を行う前に、会社の使用条件に同意することを必須にすることができます。
- デバイスを登録する
- 会社のアプリやメールなどのリソースにアクセスする。    
使用条件の構成は任意です。

複数の条件セットを作成し、異なるグループに割り当てることができます。それにより、たとえば、さまざまな言語をサポートします。

会社の使用条件を作成する方法は 2 つあります。
- この記事で説明されているように Intune を使用する。
- [Azure Active Directory の使用条件機能](https://docs.microsoft.com/azure/active-directory/governance/active-directory-tou)を使用する。どちらの方法が最適かについては、[「Choosing the right Terms solution for your organization」(組織に適した使用条件ソリューションの選択) のブログ記事](https://go.microsoft.com/fwlink/?linkid=2010506&clcid=0x409)を参照してください。 

## <a name="create-terms-and-conditions"></a>使用条件を作成する
次の手順で使用条件を作成します。 表示名と説明は管理目的で使用されます。条件のプロパティはポータル サイトでユーザーに表示されます。

1. [Azure ポータル](https://portal.azure.com) にサインインします。
2. **すべてのサービス** > **Intune** の順に選択します。 Intune は **[監視 + 管理]** セクションにあります。
3. **[Intune]** ウィンドウで **[デバイスの登録]** > **[使用条件]** の順に選択します。
2. **[作成]** を選択します。
![Azure Portal のスクリーンショット。使用条件の [作成] ボタンを確認できます。](media/terms-create-terms.png)
3. ウィンドウを展開し、次の情報を指定します。

   - **[表示名]**:Azure portal における条件の名前。 ユーザーにはこの名前は表示されません。

   - **説明**:Azure portal 上でこの条件セットの識別に役立つ任意の説明。

4. **[Define terms of use]\(使用条件を定義する\)** の横にある矢印を選択し、[使用条件] ウィンドウを開いて次の情報を入力します。

   ![エンド ユーザーの使用条件の同意画面と条件の概要のスクリーンショット](./media/terms-summary-create.png)

   - **[タイトル]**:ポータル サイト上で **[概要]** の上に表示される使用条件の名前。
   - **[使用条件の概要]**:使用条件に対するユーザーの同意が意味することを説明するテキスト。 たとえば、「デバイスを登録すると、Contoso が定めている利用規約に同意することになります。 条件をよく読んでから続行してください。」のように入力します。
   - **[使用条件]**:ユーザーに確認と承諾または拒否を求める使用条件。

5. **[OK]** > **[作成]** の順に選択します。

## <a name="see-how-terms-are-displayed-to-your-users"></a>ユーザーにどのように条項が表示されるか確認する
次の例は、管理コンソールとポータル サイトに表示される **[タイトル]** と **[使用条件の概要]** です。

![管理コンソールとポータル サイトに表示されるタイトルと使用条件の概要のスクリーンショット。](./media/terms-summary-terms.png)

次の例は、管理コンソールとポータル サイトに表示される使用条件です。

![管理コンソールとポータル サイトに表示される使用条件のスクリーンショット。](./media/terms-properties-terms.png)

## <a name="assign-terms-and-conditions"></a>使用条件を割り当てる

ポータル サイトを利用する前に承諾を求めるユーザー グループに使用条件を割り当てることができます。

1. Azure Portal で **[デバイスの登録]** を選択し、**[使用条件]** を選択します。
2. 使用条件の一覧で、割り当てる条件を選択し、**[管理]** > **[割り当て]** の順に選択します。
![Azure Portal の [グループの割り当て] ウィンドウのスクリーンショット。使用条件割り当てのための [グループの選択] ボタンと [選択] ボタンを確認できます。](media/terms-assign-groups.png)
3. **[含めるグループを選択]** を選択し、使用条件を割り当てるグループを選択し、**[選択]** を選択します。 動的なグループには使用条件を割り当てることができません。
4. **[割り当てられたグループ]** ウィンドウで、**[保存]** を選択します。  これで使用条件が選択したグループのユーザーに割り当てられました。 次回ポータル サイトにアクセスしたとき、条件の承諾がユーザーに求められます。 使用条件に同意する必要があるのは一度のみです。 複数のデバイスを持つユーザーは、各デバイスで同意する必要はありません。


## <a name="monitor-terms-and-conditions"></a>使用条件の監視

1. Azure Portal で、**[すべてのサービス]**、**[監視 + 管理]**、**[Intune]** の順に選択します。 
1. [Intune] ウィンドウで **[デバイスの登録]** > **[使用条件]** の順に選択します。
2. 使用条件の一覧で、承諾を表示する条件を選択し、**[Acceptance Reporting]\(承諾報告\)** を選択します。

## <a name="work-with-multiple-versions-of-terms-and-conditions"></a>使用条件の複数のバージョンを使用する
使用条件を編集し、そのバージョンを管理できます。 使用条件に重大な変更を加えるたびに、以下を行うようにします。
- バージョン番号を増やします。
- ユーザーが新しい使用条件に同意することを必須にします。入力ミスの修正時や書式の変更時などには、現在のバージョン番号を維持します。

1. Azure Portal で、**[すべてのサービス]**、**[監視 + 管理]**、**[Intune]** の順に選択します。

2. [Intune] ウィンドウで、**[デバイスの登録]** > **[使用条件]** の順に選択し、変更する使用条件を選択し、**[プロパティ]** を選択します。

4. **[プロパティ]** ウィンドウで、**[使用条件]** を選択し、必要に応じて **[タイトル]**、**[使用条件の概要]**、**[使用条件]** を変更します。 変更を加えた結果、ユーザーが新しい条件を承諾する必要が生じた場合は、**[ユーザーに対してもう一度同意を求めて、バージョン番号を <番号> に上げます。]** を選択します。

4.  **[OK]** > **[保存]** の順に選択します。

ユーザーは、更新された使用条件に 1 回だけ同意する必要があります。 複数のデバイスを持つユーザーは、各デバイスで使用条件に同意する必要はありません。
