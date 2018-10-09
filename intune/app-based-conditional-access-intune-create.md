---
title: Intune を使用してアプリベースの条件付きアクセス ポリシーをセットアップする
description: Intune を使用してアプリベースの条件付きアクセス ポリシーを作成する方法について説明します。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 05/17/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d1693515-de18-4553-91ef-801976cd3ec7
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2d6d67454409cf8a8749d28cba6ac76f591da9e3
ms.sourcegitcommit: fffa64f28278573dc83a846b647315def2108781
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48231289"
---
# <a name="set-up-app-based-conditional-access-policies-with-intune"></a>Intune を使用してアプリ ベースの条件付きアクセス ポリシーをセットアップする

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

この記事では、承認済みアプリの一覧に含まれるアプリにアプリベースの条件付きアクセス ポリシーをセットアップする方法について説明します。 承認済みのアプリの一覧は、Microsoft によってテストされたアプリで構成されます。

> [!IMPORTANT]
> この記事では、アプリベースの条件付きアクセス ポリシーを追加する手順について説明します。 承認済みアプリのリストから SharePoint Online、Microsoft Teams、Microsoft Exchange Online などのアプリを追加するときと同じ手順を使用できることに注意してください。

## <a name="create-app-based-conditional-access-policies-in-azure-ad-workload"></a>Azure AD ワークロードでアプリベースの条件付きアクセス ポリシーを作成する

IT 管理者は、Azure AD ワークロードからアプリベースの条件付きアクセス ポリシーを作成することができます。 Azure と Intune のワークロードを切り替える必要がなくなり、便利です。

> [!IMPORTANT]
> Intune Azure Portal から Azure AD の条件付きアクセス ポリシーを作成するには、Azure AD Premium ライセンスが必要です。

### <a name="to-create-an-app-based-conditional-access-policy"></a>アプリベースの条件付きアクセス ポリシーを作成するには

> [!IMPORTANT]
> アプリベースの条件付きアクセス ポリシーを利用するには、先に、[Intune アプリ保護ポリシー](app-protection-policies.md)をアプリに適用する必要があります。

1. **Intune ダッシュボード**で、**[条件付きアクセス]** を選びます。

2. **[ポリシー]** ウィンドウで、**[新しいポリシー]** を選択し、新しいアプリベースの条件付きアクセス ポリシーを作成します。

4. ポリシー名を入力し、**[割り当て]** セクションで利用できる設定を構成したら、**[アクセスの制御]** セクションで **[許可]** を選択します。

5. **[承認されたクライアント アプリが必要です]** を選択して、**[選択]** を選択し、**[作成]** を選択して新しいポリシーを保存します。

## <a name="next-steps"></a>次の手順
[最新の認証を使用していないアプリをブロックする](app-modern-authentication-block.md)

### <a name="see-also"></a>関連項目

[アプリ保護ポリシーでアプリ データを保護する](app-protection-policies.md)
[Azure Active Directory の条件付きアクセス](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)
