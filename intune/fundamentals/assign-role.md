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
ms.openlocfilehash: c82805bf70259d43d738644e5663b93533bcb56a
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207164"
---
# <a name="assign-a-role-to-an-intune-user"></a>Intune ユーザーにロールを割り当てる

[組み込み](role-based-access-control.md#built-in-roles)ロールまたは[カスタム](create-custom-role.md) ロールを Intune ユーザーに割り当てることができます。

ロールを作成、編集、または割り当てるには、アカウントに Azure AD の次のいずれかのアクセス許可が必要です。
- **グローバル管理者**
- **Intune サービス管理者**

1. [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) で、 **[ロール]** ** > [すべてのロール]** を選択します。

2. **[Intune の役割 - すべてのロール]** ブレード上で、割り当てる組み込みロールを選択します。

3. **[<"*ロール名*"> - 概要]** ブレード上で、 **[管理]**  >  **[割り当て]** の順に選択します。

4. [カスタム ロール] ブレードで、 **[割り当て]** を選択します。

5. **[ロールの割り当て]** ブレード上で、割り当てに対する **[割り当て名]** と、必要に応じて **[割り当ての説明]** を入力します。

6. **[メンバー (グループ)]** については、アクセス許可を付与するユーザーを含むグループを選択します。

7. **[スコープ (グループ)]** については、上記のメンバーが管理できるユーザー/デバイスを含むグループを選択します。

8. **[スコープ (タグ)]** については、このロールの割り当てが適用されるタグを選択します。

9. 終了したら、 **[OK]** を選択します。 新しい割り当てが割り当ての一覧に表示されます。


## <a name="next-steps"></a>次のステップ
- [Intune でのロール ベースの管理制御について学習する](role-based-access-control.md)
- [カスタム ロールを作成する](create-custom-role.md)
