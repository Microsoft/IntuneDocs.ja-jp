---
title: Intune ユーザーにロールを割り当てる
description: Microsoft Intune で組み込みロールまたはカスタム ロールをユーザーに割り当てる方法を学習します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: pjain
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 19fff092f7eccfc6de2a027c7834c52698176cbf
ms.sourcegitcommit: 5881979c45fc973cba382413eaa193d369b8dcf6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/24/2020
ms.locfileid: "77569168"
---
# <a name="assign-a-role-to-an-intune-user"></a>Intune ユーザーにロールを割り当てる

[組み込み](role-based-access-control.md#built-in-roles)ロールまたは[カスタム](create-custom-role.md) ロールを Intune ユーザーに割り当てることができます。

ロールを作成、編集、または割り当てるには、アカウントに Azure AD の次のいずれかのアクセス許可が必要です。
- **グローバル管理者**
- **Intune サービス管理者**

1. [Microsoft Endpoint Manager admin center](https://go.microsoft.com/fwlink/?linkid=2109431) で、 **[テナント管理]**  >  **[ロール]**  >  **[すべてのロール]** を選択します。

2. **[Intune の役割 - すべてのロール]** ブレード上で、割り当てる組み込みロールを選択し、 **[割り当て]**  >  **[割り当て]** の順に選択します。

5. **[基本]** ページで、**割り当て名**と省略可能な**割り当ての説明**を入力し、 **[次へ]** を選択します。

6. **[管理グループ]** ページで、アクセス許可を付与するユーザーを含むグループを選択します。 **[次へ]** を選択します。

7. **[スコープ (グループ)]** ページで、上記のメンバーが管理できるユーザーまたはデバイスを含むグループを選択します。 **[次へ]** を選択します。

8. **[スコープ (タグ)]** ページで、このロールの割り当てが適用されるタグを選択します。 **[次へ]** を選択します。

9. **[確認および作成]** ページで、完了したら、 **[作成]** を選択します。 新しい割り当てが割り当ての一覧に表示されます。

## <a name="next-steps"></a>次のステップ
- [Intune でのロール ベースの管理制御について学習する](role-based-access-control.md)
- [カスタム ロールを作成する](create-custom-role.md)


