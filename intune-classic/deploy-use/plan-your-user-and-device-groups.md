---
title: "ユーザーとデバイス グループを計画する"
description: "組織のニーズを満たすグループを計画します。"
keywords: 
author: sanchusa
manager: angrobe
ms.date: 10/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f11bb256-1094-4f7e-b826-1314c57f3356
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: lpatha
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 679399f306f3837a010cc01799c7567c1e5b5b39
ms.sourcegitcommit: 2459bfda07a2afd2cfcd94a1972a3fb2e565ce8d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/22/2018
---
# <a name="plan-your-user-and-device-groups"></a>ユーザーとデバイス グループを計画する

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Intune の [グループ] を使用すると、デバイスとユーザーを柔軟に管理できます。 次の条件に従って、組織のニーズに適合するグループをセットアップすることができます。

- 地理的な場所
- department
- ハードウェアの特性
- オペレーティング システム
- デバイスはユーザー所有のものか、それとも会社所有のものか


## <a name="how-intune-groups-work"></a>Intune グループのしくみ


次に示すのは、Intune 管理コンソールの **[グループ]** ノードの既定のビューです。

![Intune コンソールの [グループ] ノードの既定のビューのスナップショット](../media/Intune_Planning_Groups_Default_small.png)

ポリシーがグループ上に展開されるため、グループの階層は設計上の重要な考慮事項の 1 つです。 グループを作成した後ではグループの親グループを変更できないことを理解しておく必要があります。 グループの設計方法は、Intune サービスの使用を開始する時点から非常に重要です。 ここでは、組織のニーズに基づくグループ階層を設計する上でお勧めする方法をいくつか説明します。

## <a name="group-membership-rules"></a>グループ メンバーシップの規則

- 1 つのグループに、ユーザーのみ、またはデバイスのみを含めることができます。両方を混ぜることはできません。

    * **デバイス グループ**。 コンピューターとモバイル デバイスを含みます。 コンピューターをグループに追加する前に、グループを登録する必要があります。 モバイル デバイスをグループに追加する前に、モバイル デバイスをサポートするように環境を構成し、デバイスを登録するか、Exchange ActiveSync から検出する必要があります。

    * **ユーザー グループ**。 グループはセキュリティ グループからのユーザーを含むことができます。 セキュリティ グループは Active Directory のインスタンスと同期します。 Active Directory と同期しない場合は、手動でグループを作成できます。

- 1 台のデバイスまたは 1 人のユーザーを、複数のグループに所属させることができます。

- グループには、次のメンバーシップの規則に基づいて追加および除外することができます。

    * **メンバーシップの基準**。 Intune がメンバーの追加または除外に使用する動的な規則です。 これらの基準では、Active Directory のローカル インスタンスと同期されたセキュリティ グループとその他の情報を使用します。 セキュリティ グループまたはデータが変更されると、Active Directory と同期したときにグループのメンバーシップも変わります。

    * **ダイレクト メンバーシップ**。 明示的にメンバーを追加または除外する静的な規則です。 メンバーシップの一覧は静的です。

-   ユーザーまたはコンピューターを含むユーザー グループまたはデバイス グループを作成するときは、Active Directory ドメイン サービス (AD DS) は必要ありません。 ただし、デバイス グループがモバイル デバイスを含む場合は、モバイル デバイスをサポートするように環境を構成する必要があります。

    また、デバイスを検出し、Intune に追加する必要があります。

## <a name="group-relationship-rules"></a>グループ関係のルール

- 作成する各グループには親グループが必要です。 グループを作成した後では、グループの親グループを変更できません。

- ユーザーまたはデバイスを子グループに追加する場合:

    * 子グループは、常に親グループのサブセットです。

    * 子グループに追加した新規メンバーは、グループの親グループにも自動的に追加されます。

    * 親グループから除外したメンバーを子グループに追加することはできません。

- 親グループのメンバーシップによって、子グループのメンバーになれるユーザーやデバイスが決まります。

- 親グループを削除すると、すべての子グループが削除されます。

- 親グループにはコンテンツとポリシーを展開できますが、子グループへの展開は除きます。

- 親グループのメンバーではない特定のユーザーまたはデバイスを、子グループに追加できます。 これを行うと、子グループの新しいメンバーが親グループに追加されます。

    ただし、メンバーが親グループから除外された場合は、そのメンバーを子グループに追加することはできません。

- グループ メンバーシップは再帰的です。 次に例を示します。

    * **佐藤** さんは、 **Laptop Users** セキュリティ グループというグループにのみ属するメンバーです。

    * **Laptop Users** グループは、 **Approved Users** セキュリティ グループのメンバーです。

    * Intune で、**Approved Users** グループのメンバーを含む動的メンバーシップのクエリを使用するグループを作成します。 結果として、Intune ユーザー グループに**佐藤**さんが追加されます。

> [!TIP]
> グループを作成するときは、ポリシーを適用する方法を考慮します。 たとえば、デバイスのオペレーティング システムに固有のポリシー、または Active Directory サービスで既に定義してあるさまざまなロールまたは組織単位に固有のポリシーがあるものとします。 iOS、Android、および Windows に固有のデバイス グループを作成すると便利な場合があります。 これは、各組織ロールのユーザー グループの作成に対する追加です。

<!--- should we just link to a policies topic at this point and remove this? Ask Rob
 You'll probably want to create a default policy that applies to all groups and devices, to establish the basic compliance requirements of your organization. Then, you create more specific policies for the broadest categories of users and devices, for example, email policies for each of the device operating systems.

 Be careful when you name your policies, so that you can easily identify them later. For example, a good, descriptive policy name is **WP Email Policy for Entire Company**.

 Each time you create a restrictive policy, you'll want to communicate it to your users. After you create the more general groups and policies, pay attention to how you create smaller groups so that you can reduce unnecessary communication.--->

## <a name="built-in-groups"></a>組み込みグループ
Intune には、編集または削除できない組み込みのグループが 9 個用意されています。<!--maybe a screen shot would be best?-->

-   **すべてのユーザー**
    -   グループに属していないユーザー
-   **すべてのデバイス**
    -   すべてのコンピューター
    -   すべてのモバイル デバイス
        -   ダイレクト管理されているすべてのデバイス
        -   Exchange ActiveSync で管理されているすべてのデバイス
    -   すべての企業所有のデバイス
    -   グループに属していないデバイス

> [!NOTE]
> "*シンプルに*" をモットーにする必要があります。 以下のセクションに説明するような特定のニーズが組織にはない場合、設計を単純にし、既定のグループ構造とポリシーを採用します。 こうすると、長期に渡ってより管理しやすいサービスになります。 ユーザーを一様に扱うことができれば、メンテナンスが容易になります。 グループ単位の差別化が小さければ、維持するポリシーが少なくなります。


### <a name="all-users-and-devices-in-your-organization"></a>組織内のすべてのユーザーとデバイス
組織内のすべてのユーザーとデバイスの親グループを定義します。 すべてに適用するポリシーがある可能性があります。 Intune の既定の**すべてのユーザー** グループと**すべてのデバイス** グループをそのために使用できます。 ユーザー所有のデバイス (BYOD) を取り込む場合のグループや企業所有 (CO) デバイス用のグループなど、詳細に従ってデバイスを整理するサブグループは、**すべてのユーザー**親グループおよび**すべてのデバイス**親グループの子グループとすることができます。

## <a name="customize-groups-for-your-organization"></a>組織に合わせてグループをカスタマイズする

### <a name="byod-and-corporate-owned-devices"></a>BYOD および企業所有デバイス
組織が、従業員に個人所有デバイスを使用することを許可するか、企業所有デバイスを提供するか、またはその両方の組み合わせとする場合、これらのデバイス カテゴリに異なるポリシーを適用することをお勧めします。

BYOD または混在のケースでは、ローカル プライバシー規則を侵害しないようにポリシーを慎重に計画してください。 個人所有のデバイスを持ち込むすべてのユーザーに対する親グループを作成します。 このグループを使用して、このカテゴリに属するすべてのユーザーに適用されるポリシーを適用できます。

![BYOD 親グループの作成](../media/Intune_Planning_Groups_BYOD_small.png)

同様に、組織内の CO デバイス ユーザーに対するグループを作成することができます。

![BYOD デバイスと CO デバイスの兄弟ユーザー グループ](../media/Intune_Planning_Groups_BYOD_Hierachy_View_small.png)

<!---START HERE--->

### <a name="groups-for-geographic-regions"></a>地理的領域のグループ
組織が特定の地域に対するポリシーを必要としている場合、地理的領域に基づいてグループを作成できます。 既に Active Directory のインスタンスで作成して Azure Active Directory サービスと同期してある領域グループを基にできます。 Azure Active Directory で領域グループを直接作成することもできます。

次のスクリーンショットでは、オンプレミスの Active Directory インスタンスと同期されたグループに基づいて Intune グループを作成する方法を示します。 この例では、"**US Users Group**" と呼ばれる Active Directory セキュリティ グループがあると想定しています。

まず、一般的な情報を入力します。

![[グループの編集] 領域のスクリーン ショット](../media/Intune_Planning_Groups_AD_General_small.png)

**[メンバーシップの基準]** で、メンバーシップ規則の下で使用するセキュリティ グループとして、Active Directory と同期された "**US Users Group**" を選びます。

![[グループの編集] ダイアログ ボックスのスクリーン ショット](../media/Intune_Planning_Groups_AD_Criteria_small.png)

入力内容を確認し、**[完了]** を選んでグループを作成します。

![[グループの編集] ダイアログ ボックスのスクリーン ショット](../media/Intune_Planning_Groups_AD_Summary_small.png)

この例では、中東とアジアの **MEA**と呼ばれるグループも作成しました。

> [!NOTE]
> グループのメンバーシップがセキュリティ グループ メンバーシップに基づいて設定されていない場合は、Intune ライセンスをグループ メンバーに割り当てたことを確認します。

### <a name="groups-for-specific-hardware"></a>特定のハードウェア用のグループ
特定のハードウェアの種類に適用するポリシーが組織で必要な場合、この要件に基づくグループを作成できます。 Active Directory のオンプレミスのインスタンスで既に作成してある特定のグループを基にしてポリシーを作成した後、Azure Active Directory と同期することができます。 Azure Active Directory でグループを直接作成することもできます。 この例では、"**US Users Group**" を "**Laptop Users**" グループに対する親グループとして使用します。

![[セキュリティ グループの選択] ダイアログ ボックス](../media/Intune_Planning_Groups_Laptop_small.png)

この時点で、グループの階層構造は次のスクリーンショットのようになります。 Intune グループ "**Laptop Users**" にメンバーが含まれることがわかります。 このグループに適用されるどのポリシーも、米国地域の BYOD ノート PC ユーザーに適用されます。

![ノート PC ユーザー グループの表示](../media/Intune_Planning_Groups_Laptop_Hierarchy_small.png)

### <a name="groups-for-specific-operating-systems"></a>特定のオペレーティング システム用のグループ
Android、iOS、Windows などの特定のオペレーティング システムに適用するポリシーが組織で必要な場合は、この要件に基づくグループを作成できます。 前の例のように、Active Directory のオンプレミスのインスタンスで既に作成してある OS 固有のグループを基にしてポリシーを作成し、Azure Active Directory と同期することができます。 Azure Active Directory のインスタンスで直接作成することもできます。

前の例と同じ方法を使用することで、特定のオペレーティング システム プラットフォームを使用するユーザー <!--devices?-->に基づいてグループを作成できます。

> [!NOTE]
> 複数のモバイル プラットフォームまたはオペレーティング システムを使用しているユーザーがいるものの、Android ユーザー、iOS ユーザー、Windows ユーザーとして自動的に分類する方法がない場合、デバイス レベルでポリシーを適用することを検討します。 このようにすると、オペレーティング システムに固有のポリシーを適用する柔軟性が向上します。
>
> デバイスのオペレーティング システムに基づくグループを動的にプロビジョニングすることはできません。 代わりに、Active Directory または Azure Active Directory のセキュリティ グループを使用して行います。

![ラップトップ ユーザー グループ](../media/Intune_Planning_Groups_OS_Hierachy_small.png)

これらの組織の要件に基づいて、すべてのユーザー グループを設定した後、グループ階層は次のようになります。

![グループ階層ビュー](../media/Intune_Planning_Groups_Midpoint_Hierachy_small.png)

この階層を使用して、組織のポリシーを適用できます。

### <a name="device-groups"></a>Device groups
次に示すように、BYOD のシナリオで、従業員が所有するすべてのデバイスを含む広範なグループから始めて、デバイス用の類似したグループを作成することもできます。

![[グループの作成] ダイアログ ボックス](../media/Intune_Planning_Groups_Device_General_small.png)

グループにすべての BYO デバイスが含まれるように、**[すべてのデバイス (コンピューターとモバイル)]** を選択してください。

![[メンバーシップの基準の定義] ページ](../media/Intune_Planning_Groups_Device_Criteria_small.png)

入力内容を確認し、**[完了]** を選んで BYOD グループを作成します。

![[グループの作成] ダイアログ ボックス](../media/Intune_Planning_Groups_Device_Summary_small.png)

デバイス グループの作成を続けて、ユーザー グループ階層と同様のデバイス グループの階層を完成させます。 完成すると、Intune コンソールでグループ ノードは次のように表示されます。

![Intune グループ階層ビュー](../media/Intune_Groups_Hierarchy_Final_Small.png)

## <a name="group-hierarchies-and-naming-conventions"></a>グループ階層と名前付け規則
ポリシーの管理を容易にするために、各ポリシーに適用される目的、プラットフォーム、範囲に基づいて名前を付けることをお勧めします。 ポリシーを適用する準備をしたときに作成したグループ構造に従った名前付け標準を使用します。

たとえば、適用範囲が全社、Android モバイル デバイス、米国地域レベルの Android ポリシーは、**CO_US_Mob_Android_General** と名付けることができます。

![Android 用のポリシーの作成](../media/Intune_planning_policy_android_small.png)

この方法でポリシーに名前を付けると、**[ポリシー]** ノードから、ポリシー、その使用目的、範囲を次のようにすばやく識別できます。

![Intune ポリシー一覧](../media/Intune_planning_policy_view_small.png)

## <a name="next-steps"></a>次の手順
[グループの作成](use-groups-to-manage-users-and-devices-with-microsoft-intune.md)
