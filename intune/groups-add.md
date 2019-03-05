---
title: ユーザーとデバイスを整理するためのグループを追加する
titlesuffix: Microsoft Intune
description: 地理、部門、またはハードウェアの特性ごとにユーザーとデバイスを整理するためのグループを追加します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/13/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f0a2b858-a824-4598-ab81-bdd8e62ac3b3
ms.reviewer: amyros
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b6e7d45c4f1c990123e310c8910e9b7bd3cf0ce4
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/02/2019
ms.locfileid: "57235057"
---
# <a name="add-groups-to-organize-users-and-devices"></a>ユーザーとデバイスを整理するためのグループを追加する
Intune では、デバイスとユーザーの管理に Azure Active Directory (AD) のグループを使用します。 Intune 管理者は、組織のニーズに合ったグループをセットアップできます。 地理的な場所、部門、ハードウェアの特性ごとにグループを作成して、ユーザーまたはデバイスを整理します。 大規模なタスクを管理するには、グループを使用します。 多数のユーザーにポリシーを設定したり、一連のデバイスにアプリを展開したりする場合などです。

次の種類のグループを追加できます。
- **[割り当てられたグループ]**: ユーザーまたはデバイスを静的なグループに手動で追加します。
- **[Dynamic groups]\(動的グループ\)**: (Azure Active Directory Premium を使用) 単純なまたは高度な規則のいずれかを使って、動的にユーザーまたはデバイス グループのいずれかを構築します

## <a name="add-a-new-group"></a>新しいグループを追加する

新しいグループを作成するには、次の手順に従います。
1. [Azure ポータル](https://portal.azure.com) にサインインします。
2. **すべてのサービス** > **Intune** の順に選択します。 Intune は **[監視 + 管理]** セクションにあります。
3. **[Intune]** ウィンドウで **[グループ]** を選択し、**[すべてのグループ]** ウィンドウで **[新しいグループ]** を選択します。
   ![[新しいグループ] が選択された Azure Portal のスクリーンショット](./media/groups-add-new.png)
4. **[グループの種類]** で、次のいずれかのオプションを選択します。
    - **[セキュリティ]**:セキュリティ グループは、ユーザー グループを設定するときに使用するのに適したリソースです。 セキュリティ グループではどのユーザーがどのリソースにアクセスできるかが定義されているので、セキュリティ グループは Intune ユーザー グループに変換できます。 Active Directory から Azure Active Directory に同期されたセキュリティ グループや、Office 365 管理センター、または Azure ポータルで Azure Active Directory に直接作成されたセキュリティ グループは、Intune でユーザー グループを作成するときに使用できます。
    - **Office 365**

5. 新しいグループの **[名前]** と **[説明]** を入力します。 これらのプロパティは、管理ポータルのみに表示され、ユーザーには表示されません。

6. **[メンバーシップの種類]** を選択します。
   - 手動で割り当てられたメンバーからグループを作成するには、**[割り当て済み]** を選択します。 詳細については、「[Azure Active Directory でグループを作成し、メンバーを追加する](https://docs.microsoft.com/azure/active-directory/active-directory-groups-create-azure-portal)」を参照してください。
   - **[Dynamic query]/(動的クエリ)/** で定義したユーザー グループを作成するには、**[動的なユーザー]** を使用します。
   - **[Dynamic query]/(動的クエリ)/** で定義したデバイス グループを作成するには、**[Dynamic Device]/(動的なデバイス)/** を使用します。

   ![Intune の [グループ] プロパティのスクリーンショット](./media/groups-add-properties.png)

   Azure AD では、メンバーシップを定義するルールを使用して動的なグループを作成できます。 属性を使用した動的グループを作成する方法については、[こちら](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal)を参照してください。

7. **[Office の機能を有効にしますか?]** を選択すると、ユーザー グループのメンバーに共有 Office 365 アプリへのアクセスを付与できます。 詳細については、「[Office 365 グループの概要](https://support.office.com/article/Learn-about-Office-365-groups-b565caa1-5c40-40ef-9915-60fdb2d97fa2)」を参照してください。
8. **[作成]** を選択し、新しいグループを追加します。

## <a name="groups-and-policies"></a>グループとポリシー

グループを作成するときは、[ポリシー](device-compliance-get-started.md)を適用する方法を考慮します。 たとえば、デバイスのオペレーティング システムに固有のポリシー、組織のさまざまなロールに固有のポリシー、Active Directory で既に定義されている組織単位に固有のポリシーなどがある場合があります。 iOS、Android、Windows で異なるデバイス グループや、組織のロールごとのユーザー グループを作成すると、便利な場合があります。

また通常は、すべてのグループとデバイスに適用される既定のポリシーを作成して、組織の基本的なコンプライアンス要件を確立します。 その後は、ユーザーやデバイスの広範なカテゴリに個別のポリシーを作成できます。 たとえば、デバイスのオペレーティング システムごとに電子メール ポリシーを作成する場合があります。



## <a name="see-also"></a>関連項目
- [Azure Active Directory のグループによるリソースへのアクセス管理](https://docs.microsoft.com/azure/active-directory/active-directory-manage-groups)
- [Azure Portal での Intune クラシック グループ](groups-get-started.md)
