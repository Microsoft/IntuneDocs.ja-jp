---
title: "SharePoint Online のアプリベースの条件付きアクセス ポリシーを作成する"
description: 
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 05/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 531b09bb-ddfd-498f-8ee3-6675d2466208
ms.reviewer: chrisgre
ms.suite: ems
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 2d9065281436d4c44e6af7d7a4401786a2a01965
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017


---

# <a name="set-up-app-based-conditional-access-ca-policies-for-sharepoint-online"></a>SharePoint Online のアプリベースの条件付きアクセス (CA) ポリシーを設定する

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

ここでは、SharePoint Online のアプリベースの条件付きアクセス ポリシーを設定する方法のガイダンスを提供します。 管理者は、アプリベースの CA を使用して、Intune App 保護ポリシーが適用されているモバイル アプリのみを許可することができます。

## <a name="to-create-the-app-based-ca-policy-for-sharepoint-online"></a>SharePoint Online のアプリベースの CA ポリシーを作成するには

1. [Azure Portal](https://portal.azure.com) に移動し、自分の資格情報でサインインします。

    > [!NOTE]
    > Azure Portal を初めて使用する場合は、[アプリ保護ポリシーの Azure Portal](azure-portal-for-microsoft-intune-mam-policies.md) に関するトピックをご覧ください。

2. 左側のメニューから **[その他のサービス]** を選択し、テキスト ボックス フィルターに「**Intune**」と入力します。

3. **[Intune アプリ保護]** > **[Intune モバイル アプリケーション管理]** > **[すべての設定]** の順に選択します。

4. [Intune モバイル アプリケーション管理] ブレードで [SharePoint Online] タイルを選択します。

5. **[許可されているアプリ]** ブレードの **[Intune アプリ ポリシーをサポートするアプリを許可する]** オプションを選択して、Intune アプリ保護ポリシーでサポートされているアプリにのみ許可します。

    > [!NOTE] 
    > Intune アプリ保護ポリシーでサポートされているアプリのみを許可するオプションを選択すると、サポートされているアプリ**のみ**を含む一覧が表示されます。

    ![アプリの一覧を示す [許可されたアプリ] ブレードのスクリーンショット](../media/mam-ca-spo-allowed-apps.png)

## <a name="to-assign-app-based-ca-policies-to-your-users"></a>アプリベースの CA ポリシーをユーザーに割り当てるには

1. **[制限対象のユーザー グループ]** ブレードを開き、**[ユーザー グループの追加]** を選択します。

2. このポリシーを適用する 1 つまたは複数のユーザー グループを選択します。

    ![[ユーザー グループの追加] オプションが強調表示されている [制限対象のユーザー グループ] ブレードのスクリーンショット](../media/mam-ca-spo-restricted-groups.png)

    > [!IMPORTANT] 
    > 前の手順で選択したユーザー グループのうち、このポリシーの影響を受けないようにするユーザーがいるとします。 このような場合、ユーザーのグループを除外ユーザー グループ一覧に追加します。 

3. **[SharePoint Online]** ブレードの **[Exempted user groups] (除外するユーザー グループ)** を選択し、**[ユーザー グループの追加]** を選択してユーザー グループの一覧を開きます。

4. このポリシーから除外するグループを選択します。  

## <a name="to-modify-or-delete-user-groups-from-an-existing-app-based-ca-policy"></a>既存のアプリベースの CA ポリシーからユーザー グループを変更または削除するには

1. **[制限対象のユーザー グループ]** ブレードを開き、削除するユーザー グループを選択します。
2. 省略記号をクリックすると、削除のオプションが表示されます。
3. **[削除]** を選択すると、一覧からユーザー グループが削除されます。

> [!NOTE] 
> 手順は、**[制限対象のユーザー グループ]** 一覧からユーザー グループを削除する手順と同じです。

## <a name="next-steps"></a>次のステップ

[最新の認証を使用していないアプリをブロックする](block-apps-with-no-modern-authentication.md)

## <a name="see-also"></a>関連項目

[アプリ保護ポリシーを使用したアプリ データの保護](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)

[Exchange Online のアプリベースの CA を構成する](mam-ca-for-exchange-online.md)

