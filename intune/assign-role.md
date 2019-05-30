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
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: a22fef1c04ae52a8a4cc65eaadc1ef6fcd524c19
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66043593"
---
# <a name="assign-a-role-to-an-intune-user"></a>Intune ユーザーにロールを割り当てる

[組み込み](role-based-access-control.md#built-in-roles)ロールまたは[カスタム](create-custom-role.md) ロールを Intune ユーザーに割り当てることができます。

ロールを作成、編集、または割り当てるには、アカウントに Azure AD の次のいずれかのアクセス許可が必要です。
- **グローバル管理者**
- **Intune サービス管理者**

各組み込みロールのアクセス許可の完全な一覧は、「[Intune RBAC Table](https://gallery.technet.microsoft.com/Intune-RBAC-table-2e3c9a1a)」を参照してください。

1. サインイン、 [Azure ポータル](https://portal.azure.com)します。

2. **[すべてのサービス]** > **[Intune]** の順に選択します。 Intune は **[監視 + 管理]** セクションにあります。

3. **[Intune]** ブレード上で、**[ロール]** > **[すべてのロール]** の順に選択します。

4. **[Intune の役割 - すべてのロール]** ブレード上で、割り当てる組み込みロールを選択します。

5. **[<"*ロール名*"> - 概要]** ブレード上で、**[管理]** > **[割り当て]** の順に選択します。

6. [カスタム ロール] ブレードで、**[割り当て]** を選択します。

7. **[ロールの割り当て]** ブレード上で、割り当てに対する **[割り当て名]** と、必要に応じて **[割り当ての説明]** を入力します。

8. **[メンバー (グループ)]** については、アクセス許可を付与するユーザーを含むグループを選択します。

9. **[スコープ (グループ)]** については、上記のメンバーが管理できるユーザー/デバイスを含むグループを選択します。

10. **[スコープ (タグ)]** については、このロールの割り当てが適用されるタグを選択します。

11. 終了したら、**[OK]** を選択します。 新しい割り当てが割り当ての一覧に表示されます。


## <a name="next-steps"></a>次の手順
- [Intune でのロール ベースの管理制御について学習する](role-based-access-control.md)
- [カスタム ロールを作成する](create-custom-role.md)
