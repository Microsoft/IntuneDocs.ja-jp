---
title: Intune を使用してアプリベースの条件付きアクセス ポリシーを設定する
titleSuffix: Microsoft Intune
description: Intune でアプリベースの条件付きアクセス ポリシーを作成する方法について説明します。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d1693515-de18-4553-91ef-801976cd3ec7
ms.reviewer: chrisgre
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 94e9fcc77f8260c4a63150b5d0aef033677c524a
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509680"
---
# <a name="set-up-app-based-conditional-access-policies-with-intune"></a>Intune を使用してアプリベースの条件付きアクセス ポリシーを設定する

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

承認済みアプリの一覧に含まれるアプリに適用されるアプリベースの条件付きアクセス ポリシーを設定します。 承認済みのアプリの一覧は、Microsoft によってテストされたアプリで構成されます。

> [!IMPORTANT]
> この記事では、アプリベースの条件付きアクセス ポリシーを追加する手順について説明します。 承認済みアプリのリストから SharePoint Online、Microsoft Teams、Microsoft Exchange Online などのアプリを追加するときと同じ手順を使用できます。

## <a name="create-app-based-conditional-access-policies"></a>アプリベースの条件付きアクセス ポリシーを作成する
条件付きアクセスは、Azure Active Directory (Azure AD) テクノロジです。 *Intune* からアクセスされる条件付きアクセス ノードは、*Azure AD* からアクセスされるノードと同じです。 つまり、ポリシーを構成するために、Intune と Azure AD の間を切り替える必要はありません。

> [!IMPORTANT]
> Intune ポータルから条件付きアクセス ポリシーを作成するには、Azure AD Premium ライセンスが必要です。

### <a name="to-create-an-app-based-conditional-access-policy"></a>アプリベースの条件付きアクセス ポリシーを作成するには

> [!IMPORTANT]
> アプリベースの条件付きアクセス ポリシーを使用する前に、[Intune アプリ保護ポリシー](../apps/app-protection-policies.md)をアプリに適用する必要があります。

1. **Intune ダッシュボード**で、 **[条件付きアクセス]** を選択します。

2. **[ポリシー]** ウィンドウで、 **[新しいポリシー]** を選択し、新しいアプリベースの条件付きアクセス ポリシーを作成します。

4. ポリシー名を入力し、 **[割り当て]** セクションで利用できる設定を構成したら、 **[アクセスの制御]** セクションで **[許可]** を選択します。

5. **[承認されたクライアント アプリが必要です]** を選択して、 **[選択]** を選択し、 **[作成]** を選択して新しいポリシーを保存します。

## <a name="next-steps"></a>次の手順
[最新の認証を使用していないアプリをブロックする](app-modern-authentication-block.md)

## <a name="see-also"></a>関連項目

[アプリ保護ポリシーでアプリ データを保護する](../apps/app-protection-policies.md)
[Azure Active Directory の条件付きアクセス](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)
