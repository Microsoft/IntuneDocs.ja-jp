---
title: "Intune を使用したアプリ ベースの条件付きアクセス ポリシー"
description: "このトピックでは、Intune を使用したアプリベースの条件付きアクセス ポリシーを構成する方法について説明します。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d1693515-de18-4553-91ef-801976cd3ec7
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 88db3730be62a9b481d924b4f09b70be775cb067
ms.sourcegitcommit: 4dc5bed94cc965a54eacac2d87fb2d49c9300c3a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/25/2017
---
# <a name="set-up-app-based-conditional-access-policies"></a>アプリベースの条件付きアクセス ポリシーの設定

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

このトピックでは、承認済みアプリに含まれるアプリにアプリベースの条件付きアクセス ポリシーを設定する方法を紹介します。 承認済みのアプリの一覧は、Microsoft によってテストされたアプリで構成されます。

> [!IMPORTANT]
> このトピックでは、Exchange Online を利用し、アプリベースの条件付きアクセス ポリシーを追加する手順について段階的に説明しますが、SharePoint Online や Microsoft Teams など、他のアプリを承認済みアプリの一覧から追加するときでも同じ手順を利用できます。

## <a name="to-create-an-app-based-conditional-access-policy"></a>アプリベースの条件付きアクセス ポリシーを作成するには
1.  [Azure Portal](https://portal.azure.com) に移動し、自分の資格情報でサインインします。

2.  **[その他のサービス]** を選択し、"Intune" と入力します。

3.  **[Intune アプリ保護]** を選択します。

4.  **[Intune モバイル アプリケーション管理]** ブレードで **[すべての設定]** を選択します。

5.  **[条件付きアクセス]** セクションで、**[Exchange Online]** を選択します。

    ![[条件付きアクセス] セクションの [Exchange Online] オプションが強調表示された設定ブレードのスクリーンショット](./media/MAM-conditional-access-1.png)

6. **[許可されているアプリ]** ブレードの **[Allow apps that support Intune app policies]** (Intune アプリ ポリシーをサポートするアプリを許可する) オプションを選択して、Exchange Online へのアクセスを Intune アプリ保護ポリシーでサポートされているアプリにのみ許可します。 このオプションを選択すると、サポートされるアプリの一覧が表示されます。

    > [!NOTE]
    > iOS と Android の組み込みのメール クライアントを含め、Exchange Online に接続するすべての Exchange Active Sync メール クライアントは、電子メールを送受信できなくなります。 ユーザーには、Outlook メール アプリを使用する必要があることを知らせる 1 通の電子メールが送信されます。

7. このポリシーをユーザーに適用するには、**[制限対象のユーザー グループ]** ブレードを開き、**[ユーザー グループの追加]** を選択します。 このポリシーを適用する 1 つまたは複数のユーザー グループを選択します。

    ![[ユーザー グループの追加] オプションが強調表示されている [制限対象のユーザー グループ] ブレードのスクリーンショット](./media/mam-ca-add-user-group.png)

8. 前の手順で選択したユーザー グループのうち、このポリシーの影響を受けないようにするユーザーがいるとします。 このような場合、ユーザーのグループを除外ユーザー グループ一覧に追加します。 **[Exchange Online]** ブレードで、**[Exempted user groups]** (除外するユーザー グループ) を選択します。 **[ユーザー グループの追加]** を選択してユーザー グループの一覧を開きます。 このポリシーから除外するグループを選択します。

## <a name="to-modify-or-delete-user-groups-from-an-existing-app-based-ca-policy"></a>既存のアプリベースの CA ポリシーからユーザー グループを変更または削除するには

1. **[制限対象のユーザー グループ]** ブレードを開き、削除するユーザー グループを選択します。
2. 省略記号をクリックすると、削除のオプションが表示されます。
3. **[削除]** を選択すると、一覧からユーザー グループが削除されます。

## <a name="create-app-based-conditional-access-policies-in-azure-ad-workload"></a>Azure AD ワークロードでアプリベースの条件付きアクセス ポリシーを作成する

Intune 1708 リリース以降、IT 管理者は Azure AD ワークロードからアプリベースの条件付きアクセス ポリシーを作成できます。 Azure と Intune のワークロードを切り替える必要がなくなり、便利です。

> [!IMPORTANT]
> Intune Azure Portal から Azure AD の条件付きアクセス ポリシーを作成するには、Azure AD Premium ライセンスが必要です。

### <a name="to-create-an-app-based-conditional-access-policy"></a>アプリベースの条件付きアクセス ポリシーを作成するには

> [!IMPORTANT]
> アプリベースの条件付きアクセス ポリシーを利用するには、先に、[Intune アプリ保護ポリシー](app-protection-policies.md)をアプリに適用する必要があります。

1. **Intune ダッシュボード**で、**[条件付きアクセス]** を選びます。

2. **[ポリシー]** ブレードで、**[新しいポリシー]** を選択し、新しいアプリベースの条件付きアクセス ポリシーを作成します。

4. ポリシー名を入力し、**[割り当て]** セクションで利用できる設定を構成したら、**[アクセスの制御]** セクションで **[許可]** を選択します。

5. **[承認されたクライアント アプリが必要です]** を選択し、**[選択]** を選択し、**[OK]** を選択して新しいポリシーを保存します。

## <a name="next-steps"></a>次のステップ
[最新の認証を使用していないアプリをブロックする](app-modern-authentication-block.md)

### <a name="see-also"></a>関連項目

[アプリ保護ポリシーでアプリ データを保護する](app-protection-policies.md)
[Azure Active Directory の条件付きアクセス](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)
