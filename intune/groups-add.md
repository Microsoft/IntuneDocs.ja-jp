---
title: ユーザーとデバイスを整理するためのグループを追加する
titlesuffix: Microsoft Intune
description: 地理、部門、またはハードウェアの特性ごとにユーザーとデバイスを整理するためのグループを追加します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f0a2b858-a824-4598-ab81-bdd8e62ac3b3
ms.reviewer: amyros
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 613d64e396e969b8b6bde76ee6c4474a60be8ba9
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="add-groups-to-organize-users-and-devices"></a>ユーザーとデバイスを整理するためのグループを追加する
Intune では、デバイスとユーザーの管理に Azure Active Directory (AD) のグループを使用します。 Intune 管理者は、組織のニーズに合ったグループをセットアップできます。 地理的な場所、部門、ハードウェアの特性ごとにグループを作成して、ユーザーまたはデバイスを整理します。 大規模なタスクを管理するには、グループを使用します。 多数のユーザーにポリシーを設定したり、一連のデバイスにアプリを展開したりする場合などです。

このトピックでは、Intune で使用するグループを追加する方法を説明します。

次の種類のグループを追加できます。
- **[割り当てられたグループ]**: ユーザーまたはデバイスを静的なグループに手動で追加します。
- **[Dynamic groups]\(動的グループ\)**: (Azure Active Directory Premium を使用) 単純なまたは高度な規則のいずれかを使って、動的にユーザーまたはデバイス グループのいずれかを構築します

## <a name="add-a-new-group"></a>新しいグループを追加する

新しいグループを作成するには、次の手順に従います。
1. サインイン、 [Azure ポータル](https://portal.azure.com)します。
2. **[すべてのサービス]**、**[Intune]** の順に選択します。 Intune は **[監視 + 管理]** セクションにあります。
3. **[Intune]** ウィンドウで **[グループ]** を選択し、**[すべてのグループ]** ウィンドウで **[新しいグループ]** を選択します。
   ![[新しいグループ] が選択された Azure Portal のスクリーンショット](./media/groups-add-new.png)
4. 新しいグループの **[グループの種類]**、**[名前]**、**[説明]** を指定します。 これらのプロパティは、管理ポータルのみに表示され、ユーザーには表示されません。

5. **[メンバーシップの種類]** を選択します。
   - 手動で割り当てられたメンバーからグループを作成するには、**[割り当て済み]** を選択します。 詳細については、「[Azure Active Directory でグループを作成し、メンバーを追加する](https://docs.microsoft.com/azure/active-directory/active-directory-groups-create-azure-portal)」を参照してください。
   - **[Dynamic query]/(動的クエリ)/** で定義したユーザー グループを作成するには、**[動的なユーザー]** を使用します。
   - **[Dynamic query]/(動的クエリ)/** で定義したデバイス グループを作成するには、**[Dynamic Device]/(動的なデバイス)/** を使用します。

   ![Intune の [グループ] プロパティのスクリーンショット](./media/groups-add-properties.png)

   Azure AD では、メンバーシップを定義するルールを使用して動的なグループを作成できます。 属性を使用した動的グループを作成する方法については、[こちら](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal)を参照してください。

6. **[Office の機能を有効にしますか?]** を選択すると、ユーザー グループのメンバーに共有 Office 365 アプリへのアクセスを付与できます。 詳細については、「[Office 365 グループの概要](https://support.office.com/article/Learn-about-Office-365-groups-b565caa1-5c40-40ef-9915-60fdb2d97fa2)」を参照してください。
7. **[作成]** を選択し、新しいグループを追加します。

## <a name="see-also"></a>関連項目
- [Azure Active Directory のグループによるリソースへのアクセス管理](https://docs.microsoft.com/azure/active-directory/active-directory-manage-groups)
- [Azure Portal での Intune クラシック グループ](groups-get-started.md)
