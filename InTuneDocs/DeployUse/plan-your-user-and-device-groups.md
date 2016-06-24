---
# required metadata

title: ユーザーとデバイス グループを計画する | Microsoft Intune
description:
keywords:
author: SanchuSa
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: f11bb256-1094-4f7e-b826-1314c57f3356

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# ユーザーとデバイス グループを計画する
Intune の [グループ] を使用すると、デバイスとユーザーを非常に柔軟に管理できます。 次の条件に従って、組織のニーズに適合するグループをセットアップすることができます。

- 地理的な場所
- department
- ハードウェアの特性
- オペレーティング システム
- デバイスはユーザー所有のものか、それとも会社所有のものか


## Intune グループのしくみ


Intune 管理コンソールの [グループ] ノードの既定のビューは次のようになります。

![Intune コンソールの [グループ] ノードの既定のビューのスナップショット](/intune/media/Group-planning/Intune_Planning_Groups_Default_small.png)

ポリシーがグループ上に展開されるため、グループの階層は設計上の重要な考慮事項の 1 つです。 グループをいったん作成すると、そのグループの親グループを変更できないことを理解しておくことも重要です。そのため、グループの設計は、Intune サービスの使用開始時点から非常に重要になります。 ここでは、組織のニーズに基づくグループ階層を設計する上でお勧めする方法をいくつか説明します。

## グループ メンバーシップの規則

1. 1 つのグループに、ユーザーのみ、またはデバイスのみを含めることができます。両方を混ぜることはできません。

    * **デバイス グループ:** コンピューターとモバイル デバイスの両方を含みます。 コンピューターをグループに追加する前に、グループを登録する必要があります。 モバイル デバイスをグループに追加する前に、モバイル デバイスをサポートするように環境を構成し、デバイスを登録するか、Exchange ActiveSync から検出する必要があります。

    * **ユーザー グループ:** グループにはセキュリティ グループからユーザーを追加することができます。セキュリティ グループは、Active Directory から同期するグループです。 Active Directory 同期を使用しない場合、手動でグループを作成できます。

2. 1 台のデバイスまたは 1 人のユーザーを、複数のグループに所属させることができます。

3. グループには、次のメンバーシップの規則に基づいて追加および除外することができます。

    * **メンバーシップの基準:** Intune がメンバーの追加または除外に使用する動的な規則です。 これらの基準では、ローカルの Active Directory (AD) から同期した**セキュリティ グループ**とその他の情報を使用します。 セキュリティ グループまたはデータが変更されると、AD と同期したときにグループのメンバーシップも変わります。

    * **ダイレクト メンバーシップ:** 明示的にメンバーを追加または除外する静的な規則です。 メンバーシップの一覧は静的です。

4. Active Directory ドメイン サービス (AD DS) は、ユーザー グループ、またはコンピューターを含めるデバイス グループの作成には必要ありませんが、モバイル デバイスを含むデバイス グループを作成する場合は、モバイル デバイスをサポートするように環境を構成する必要があります。

    また、デバイスを検出し、Intune に追加する必要があります。

## グループ関係のルール

1. 作成するすべてのグループには親グループが必要です。また、グループの作成後にグループの親グループを変更することはできません。

2. ユーザーまたはデバイスを子グループに追加する場合:

    * 子グループは常に親グループのサブセットです。

    * 子グループに追加した新規メンバーは、グループの親グループにも自動的に追加されます。

    * 親グループから除外したメンバーを子グループに追加することはできません。

3. 親グループのメンバーシップによって、子グループのメンバーになれるユーザーやデバイスが決まります。

4. 親グループを削除すると、すべての子グループが削除されます。

5. 子グループへの展開を除外するときに、親グループにコンテンツとポリシーを展開できます。

6. 親グループのメンバーではない特定のユーザーまたはデバイスを、子グループに追加できます。 この場合、新しいグループ メンバーは親グループに追加されます。

    ただし、親グループから除外したメンバーを子グループに追加することはできません。

7. グループ メンバーシップは再帰的です。 たとえば、

    * **佐藤** さんは、 **Laptop Users** セキュリティ グループというグループにのみ属するメンバーです。

    * **Laptop Users** グループは、 **Approved Users** セキュリティ グループのメンバーです。

    * Intune で、**Approved Users** グループのメンバーを含む動的メンバーシップのクエリを使用するグループを作成します。 結果として、Intune ユーザー グループに**佐藤さん**が追加されます。.

> [!TIP]
> グループを作成するときは、ポリシーを適用するしくみについて検討します。 たとえば、デバイスのオペレーティング システムに固有のポリシーのほか、組織のさまざまなロール固有のポリシーか、Active Directory に既に定義している組織単位固有のポリシーがあるとします。 各組織のロール用のユーザー グループだけでなく、iOS、Android、Windows に固有のデバイス グループを作成すると便利になると考えられます。

<!--- should we just link to a policies topic at this point and remove this? Ask Rob
 You'll probably want to create a default policy that applies to all groups and devices, to establish the basic compliance requirements of your company. Then create more specific policies for the broadest categories of users and devices, for example, email policies for each of the device operating systems.

 Be careful naming your policies so that you can easily identify them later. For example, a good, descriptive policy name is **WP Email Policy for Entire Company**.

 Each time you create a restrictive policy you'll want to communicate it to your users, so after you create the more general groups and policies pay attention to how you create smaller groups so that you can reduce unnecessary communication.--->

## 組み込みグループ
Intune には、編集または削除できない組み込みのグループが 9 個用意されています。 <!--maybe a screen shot would be best?-->

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
> "*シンプルに*" をモットーにする必要があります。 以下に説明するような特定のニーズが組織にはない場合、設計を単純にし、既定のグループ構造とポリシーを採用すると、長期に渡ってより管理しやすいサービスになります。 グループごとの差異が小さくユーザーを等しく扱うことができれば、メンテナンスは容易になりますし、管理するポリシーも少なくなります。


### 組織内のすべてのユーザーとデバイス
組織内のすべてのユーザーとデバイスに適用されるポリシーを持つ可能性が高いため、そのすべてに親グループを定義します。 Intune の既定の**すべてのユーザー**グループと**すべてのデバイス**グループをそのために使用できます。 ユーザー所有のデバイス (BYOD) を取り込む場合のグループや企業所有のデバイス (CO) 用のグループなど、詳細に従ってデバイスを整理するサブグループは、**すべてのユーザー**の親グループおよび**すべてのデバイス**の親グループの子とすることができます。

## 組織に合わせてグループをカスタマイズする

### BYOD および企業所有デバイス
組織が、従業員に仕事で個人所有 (BYOD) のデバイスを使用することを許可するか、企業所有 (CO) デバイスを提供するか、またはその両方の組み合わせとする場合、デバイスの 2 つのカテゴリに基づくポリシーを適用するようお勧めします。

BYOD または混在のケースでは、ローカル プライバシー規則を侵害しないようにポリシーを慎重に計画してください。 個人所有のデバイスを持ち込むすべてのユーザーに対する親グループを作成します。 このグループは、このカテゴリに属するすべてのユーザーに適用されるポリシーを適用するために使用されます。

![BYOD 親グループの作成のスクリーン ショット](/intune/media/Group-planning/Intune_Planning_Groups_BYOD_small.png)

同様に、組織内の CO ユーザーに対するグループを作成することができます。

![BYOD と CO の兄弟ユーザー グループのスクリーン ショット](/intune/media/Group-planning/Intune_Planning_Groups_BYOD_Hierachy_View_small.png)

<!---START HERE--->

### 地理的領域のグループ
組織が特定の地域に対するポリシーを必要としている場合、地理的領域に基づいてグループを作成できます。 Active Directory (AD) で既に作成されている可能性のある地域グループをポリシーの基礎とし、ポリシーを Azure AD に同期することができます。 Azure AD で直接作成することもできます。

以下のスクリーン ショットは、オンプレミス AD から同期されたグループに基づく Intune グループを作成する方法を示しています。 この例では、"**US Users Group**" と呼ばれる AD セキュリティ グループがあると想定しています。.

1. まず、一般的な情報を入力します。

    ![[グループの編集] 領域のスクリーン ショット](/intune/media/PlanDesign/Group-planning/Intune_Planning_Groups_AD_General_small.png)

メンバーシップの基準の下で、メンバーシップ規則の下で使用するセキュリティ グループとして、AD から同期された "**US Users Group**" を選びます。

![[グループの編集] ダイアログ ボックス](/intune/media/Intune_Planning_Groups_AD_Criteria_small.png)

情報を再確認し、**[完了]** を選択してグループの作成を完了します。

![[グループの編集] ダイアログ ボックス](/intune/media/Intune_Planning_Groups_AD_Summary_small.png)

この例では、"Middle East and Asia (MEA)" グループも作成しました。

> [!NOTE]
> グループのメンバーシップがセキュリティ グループ メンバーシップに基づいて設定されていない場合、Intune ライセンスをこれらのメンバーに割り当てたことをご確認ください。

### 特定のハードウェア用のグループ
特定のハードウェアの種類に適用するポリシーが組織で必要な場合、この要件に基づくグループを作成できます。 オンプレミスの AD で既に作成されている特定のグループをポリシーの基礎とし、ポリシーを Azure AD に同期することができます。 Azure AD で直接作成することもできます。 この例では、"**US Users Group**" を "**Laptop Users**" グループに対する親として使用します。

![[セキュリティ グループの選択] ダイアログ ボックス](/intune/media/Intune_Planning_Groups_Laptop_small.png)

この時点では、グループ階層が次のように表示されます。 表示のように、Intune グループ "**Laptop Users**" にはメンバーが含まれています。 このグループに適用されるどのポリシーも、米国地域の BYOD ノート PC ユーザーに適用されます。

![ノート PC ユーザー グループの表示](/intune/media/Group-planning/Intune_Planning_Groups_Laptop_Hierarchy_small.png)

### 特定のオペレーティング システム用のグループ
Android、iOS、Windows などの特定のオペレーティング システムに適用するポリシーが組織で必要な場合は、この要件に基づくグループを作成できます。 前の例と同様に、オンプレミスの AD で既に作成されている OS 固有のグループをポリシーの基礎とし、ポリシーを Azure AD に同期することができます。 Azure AD で直接作成することもできます。

前の例と同じ方法に従えば、 <!--devices?--> 特定の OS プラットフォームを使用するユーザーに基づいてグループを作成することができます。

> [!NOTE]
> 複数のモバイル プラットフォームまたはオペレーティング システムを使用しているユーザーがいるものの、Android ユーザー、iOS ユーザー、Windows ユーザーとして自動的に分類する方法がない場合、デバイス レベルでポリシーを適用することを検討します。こうすることで、OS 固有のポリシーを適用する面で柔軟性が向上します。
>
> デバイスの OS に基づくグループを動的にプロビジョニングすることはできません。 この操作は、AD または AAD セキュリティ グループを使用して行います。

![ノート PC ユーザー グループの表示](/intune/media/Intune_Planning_Groups_OS_Hierachy_small.png)

これらの組織の要件に基づいて、すべてのユーザー グループを設定した後、グループ階層は次のようになります。

![グループ階層ビュー](/intune/media/Intune_Planning_Groups_Midpoint_Hierachy_small.png)

組織のポリシーを適切に適用するためにこの階層を使用できます。

### Device groups
次に示すように、BYOD のシナリオで、従業員が所有するすべてのデバイスを含む広範なグループから始めて、デバイス用の類似したグループを作成することもできます。

![[グループの作成] ダイアログ ボックス](/intune/media/Intune_Planning_Groups_Device_General_small.png)

グループにすべての BYO デバイスが含まれるように、**[すべてのデバイス (コンピューターとモバイル)]** を選択してください。

![[メンバーシップの基準の定義] ページ](/intune/media/Intune_Planning_Groups_Device_Criteria_small.png)

情報を再確認し、**[完了]** を選択して BYOD グループを作成します。

![[グループの作成] ダイアログ ボックス](/intune/media/Intune_Planning_Groups_Device_Summary_small.png)

デバイス グループの作成を続けて、ユーザー グループ階層と同様のデバイス グループの階層を完成させます。 完成すると、Intune コンソールでグループ ノードは次のように表示されます。

![Intune グループ階層ビュー](/intune/media/Intune_Groups_Hierarchy_Final_Small.png)

## グループ階層と名前付け規則
ポリシーの管理を容易にするために、各ポリシーに適用される目的、プラットフォーム、範囲に基づいて名前を付けることをお勧めします。 この命名基準は、ポリシーを適用するための準備で作成したグループの構造に従う必要があります。

たとえば、適用範囲が全社、Android モバイル デバイス、US 地域レベルの Android ポリシーは、次のように名付けることができます。
**CO_US_Mob_Android_General**.

![Android 用のポリシーの作成](/intune/media/Intune_planning_policy_android_small.png)

この方法でポリシーを名付けると、コンソールのポリシー ノードから、ポリシー、その使用目的、範囲を次のようにすばやく識別できます。

![Intune ポリシー一覧](/intune/media/Intune_planning_policy_view_small.png)

## 次のステップ
[グループの作成](use-groups-to-manage-users-and-devices-with-microsoft-intune.md)


<!--HONumber=May16_HO1-->


