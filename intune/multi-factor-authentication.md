---
title: "Intune へのデバイスの登録での多要素認証"
titlesuffix: Azure portal
description: "デバイス登録で Azure AD の多要素認証を要求する方法。"
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 94280c73-c05c-4e72-b0dd-a7cb997782f9
ROBOTS: 
ms.custom: intune-azure
ms.openlocfilehash: a3aabe77257fd7e6964dd7bd83035c8a491a58b4
ms.sourcegitcommit: 94d3d86f8ae9f82a9872384bbaae53580036a4ff
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2017
---
# <a name="multi-factor-authentication-for-intune-device-enrollments"></a>Intune へのデバイスの登録での多要素認証

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune では、デバイス登録に Azure Active Directory (AD) 多要素認証 (MFA) 機能を利用し、会社のリソースを守ります。

MFA は、次の確認方法のうち 2 つ以上を必須にすることで機能します。

- ユーザーが知っている情報 (通常はパスワードまたは PIN)。
- ユーザーの所持品 (電話など、容易には複製できない、信頼済みのデバイス)。
- ユーザー自身 (指紋など、生体認証)

MFA は、iOS、Android、Windows 8.1 以上、Windows Phone 8.1 以上、Windows 10 Mobile 以上のデバイスでサポートされています。

MFA を有効にするには、エンド ユーザーは 2 種類の資格情報を提供し、デバイスを登録する必要があります。

## <a name="configure-intune-to-require-multi-factor-authentication-at-device-enrollment"></a>デバイス登録時に多要素認証を要求するように Intune を構成する

デバイスの登録時に MFA を要求するには、次の手順に従います。

>[!Important]
>Microsoft Intune 登録には、**デバイス ベースのアクセス規則**を構成しないでください。

1. 資格情報を利用し、[Microsoft Azure Portal](https://portal.azure.com) にサインインします。
2. ポータルで、**[Azure Active Directory]** を選択します。
2. **[Azure Active Directory]** で、**[管理]** > **[エンタープライズ アプリケーション]** の順に選択します。
3. **[エンタープライズ アプリケーション]** で、**[管理]** > **[すべてのアプリケーション]** の順に選択します。 管理するすべての Azure アプリの一覧が表示されます。
3. この一覧から、**[Microsoft Intune enrollment]\(Microsoft Intune 登録\)** を選択します。
4. **[Microsoft Intune Enrollment]\(Microsoft Intune 登録\)** で、**[セキュリティ]** > **[条件付きアクセス]** の順に選択します。
5. **[新しいポリシー]** を選びます。
6. **[新しいポリシー]** で、ポリシーのわかりやすい名前を入力します。
7. **[割り当て]** セクションで、**[ユーザーとグループ]** を選択します。
8. **[ユーザーとグループ]** で、このポリシーを受けるユーザーまたはグループを選択し、**[完了]** を選択します。
9. **[割り当て]** セクションで、**[クラウド アプリ]** を選択します。
10. **[クラウド アプリ]** の **[挿入]** タブで、**[アプリを選択]** を選択し、**[選択]** > **[Microsoft Intune Enrollment]\(Microsoft Intune 登録\)** の順に選択し、**[完了]** を選択します。
11. **[割り当て]** セクションで、**[条件]** を選択します。
12. **[条件]** では、MFA 設定を構成する必要はありません。
13. **[アクセス制御]** セクションで、**[許可]** を選択します。
14. **[許可]** で、**[アクセス権の付与]** を選択し、**[多要素認証を要求する]** を選択します。
    **[デバイスは準拠としてマーク済みである必要があります]** は選択しないでください。登録されるまで、デバイスの準拠状態は評価できません。
15. **[選択]** を選択します。
16. **[新しいポリシー]** で、**[ポリシーを有効にする]** > **[オン]** の順に選択し、**[作成]** を選択します。



## <a name="next-steps"></a>次のステップ

エンド ユーザーがデバイスを登録するとき、PIN、スマートフォン、生体認証など、2 つ目の識別形態で認証する必要があります。
