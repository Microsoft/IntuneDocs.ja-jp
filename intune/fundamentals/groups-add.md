---
title: ユーザーとデバイスを整理するためのグループを追加する
titleSuffix: Microsoft Intune
description: 地理、部門、またはハードウェアの特性ごとにユーザーとデバイスを整理するためのグループを追加します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/20/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f0a2b858-a824-4598-ab81-bdd8e62ac3b3
ms.reviewer: altsou
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6e3219e32ef9bea838f0c19258d0b22a99083a12
ms.sourcegitcommit: 1a22b8b31424847d3c86590f00f56c5bc3de2eb5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2019
ms.locfileid: "74261573"
---
# <a name="add-groups-to-organize-users-and-devices"></a>ユーザーとデバイスを整理するためのグループを追加する

Intune では、デバイスとユーザーの管理に Azure Active Directory (Azure AD) のグループが使用されます。 Intune 管理者は、組織のニーズに合ったグループをセットアップできます。 地理的な場所、部門、ハードウェアの特性ごとにグループを作成して、ユーザーまたはデバイスを整理します。 大規模なタスクを管理するには、グループを使用します。 たとえば、多数のユーザーに対するポリシーを設定したり、デバイスのセットにアプリを展開したりできます。

次の種類のグループを追加できます。

- **割り当てられたグループ**: ユーザーまたはデバイスを静的なグループに手動で追加します。 
- **動的なグループ** (Azure AD Premium が必要) - ご自分で作成した式に基づいてユーザー グループまたはデバイス グループにユーザーまたはデバイスを自動的に追加します。

  たとえば、マネージャーのタイトルを持つユーザーが追加されると、そのユーザーは **[すべてのマネージャー]** というユーザー グループに自動的に追加されます。 また、デバイスの OS の種類が iOS デバイスである場合、そのデバイスは **[すべての iOS デバイス]** というデバイス グループに自動的に追加されます。

## <a name="add-a-new-group"></a>新しいグループを追加する

新しいグループを作成するには、次の手順に従います。

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。
2. **[グループ]**  >  **[新しいグループ]** を選択します。

   ![[新しいグループ] が選択された Azure portal のスクリーンショット](./media/groups-add/groups-add-new.png)

3. **[グループの種類]** で、次のいずれかのオプションを選択します。

    - **[セキュリティ]** :セキュリティ グループは、だれがリソースにアクセスできるかを定義するものであり、Intune 内のグループ用に推奨されます。 たとえば、**シャーロットの全従業員**や **Contoso のすべての女性**などのユーザーのグループを作成できます。 または、デバイスのグループを作成します。たとえば、**すべての iOS デバイス**や、**すべての Windows 10 Student デバイス**などです。

        > [!TIP]
        > 作成したユーザーとグループは、[Microsoft 365 管理センター](https://admin.microsoft.com)、Azure Active Directory 管理センター、[Azure portal 上の Microsoft Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にも表示されます。 組織のテナントでは、これらのすべての領域でグループを作成および管理できます。
        >
        > プライマリ ロールがデバイス管理の場合は、[Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)を使用することをお勧めします。

    - **[Office 365]** : Office 365 リソースに対するアクセスと共有を制御するように設計されているグループです。 たとえば、Outlook の受信トレイまたは予定表を共有する Office 365 グループを作成できます。 詳細については、「[Office 365 グループの概要](https://support.office.com/article/learn-about-office-365-groups-b565caa1-5c40-40ef-9915-60fdb2d97fa2)」を参照してください。

4. 新しいグループの **[グループ名]** と **[グループの説明]** を入力します。 他のユーザーがそのグループの目的を理解できるように、具体的な情報にしてください。

    たとえば、グループ名として「**すべての Windows 10 Student デバイス**」と入力し、グループの説明として「**Contoso 高校の第 9 学年から第 12 学年までの学生が使用するすべての Windows 10 デバイス**」と入力します。

5. **[メンバーシップの種類]** を入力します。 次のようなオプションがあります。

    - **割り当て済み**:管理者は、ユーザーまたはデバイスを手動でこのグループに割り当て、ユーザーまたはデバイスを手動で削除します。
    - **動的ユーザー**: 管理者は、自動的にメンバーを追加および削除するためのメンバーシップの規則を作成します。
    - **動的デバイス**: 管理者は、自動的にデバイスを追加および削除するための動的なグループ規則を作成します。

        ![Intune の [グループ] プロパティのスクリーンショット](./media/groups-add/groups-add-properties.png)

    これらのメンバーシップの種類の詳細と動的な式の作成については、以下を参照してください。

    - [Azure AD を使用して基本グループを作成してメンバーを追加する](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal)
    - [Azure AD の動的グループ メンバーシップ ルール](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership)

    > [!NOTE]
    > この管理センターでは、ユーザーまたはグループを作成するときに、**Azure Active Directory** のブランド表示がない場合があります。 しかし、それは使用されています。

6. **[作成]** を選択し、新しいグループを追加します。 一覧にグループが表示されます。

> [!TIP]
> 作成できる他の動的ユーザー グループおよび動的デバイス グループとして、次のようなグループが考えられます。
>
> - Contoso 高校のすべての学生
> - すべての Android Enterprise デバイス
> - すべての iOS 11 およびそれ以前のデバイス
> - Marketing
> - 人事
> - シャーロットの全従業員
> - ワシントン州の全従業員

## <a name="groups-and-policies"></a>グループとポリシー

組織のリソースへのアクセスは、作成したユーザーとグループによって制御されます。

グループを作成するときは、[コンプライアンス ポリシー](../protect/device-compliance-get-started.md)と[構成プロファイル](../configuration/device-profiles.md)を適用する方法を検討してください。 たとえば、次のようなものが考えられます。

- デバイスのオペレーティング システムに固有のポリシー。
- 組織内のさまざまなロールに固有のポリシー。
- Active Directory に定義した組織単位に固有のポリシー。

組織の基本的なコンプライアンス要件を確立するには、すべてのグループとデバイスに適用される既定のポリシーを作成します。 その後、ユーザーやデバイスの広範なカテゴリを対象にした、より具体的なポリシーを作成します。 たとえば、デバイスのオペレーティング システムごとに電子メール ポリシーを作成する場合があります。

構成プロファイルに関する推奨事項とガイダンスについては、[ユーザー グループまたはデバイス グループへのポリシーの割り当て](../configuration/device-profile-assign.md#user-groups-vs-device-groups)に関するページと、[プロファイルに関する推奨事項](../configuration/device-profile-create.md#recommendations)の説明を参照してください。

## <a name="see-also"></a>関連項目

- [Microsoft Intune でのロールベースのアクセス制御 (RBAC)](role-based-access-control.md)
- [Azure AD グループを使用してリソースへのアクセス権を管理する](https://docs.microsoft.com/azure/active-directory/active-directory-manage-groups)
