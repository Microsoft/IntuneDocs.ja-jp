---
title: Intune でカスタム ロールを作成する
description: Microsoft Intune でカスタム ロールを作成する方法について学習します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/26/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: f7e1e67f617c0a345b17aa731fd193e611eba71e
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61508239"
---
# <a name="create-a-custom-role-in-intune"></a>Intune でカスタム ロールを作成する

特定のジョブ機能に必要なアクセス許可をすべて含むカスタム Intune ロールを作成できます。 たとえば、IT 部門の 1 つのグループがアプリケーション、ポリシー、構成プロファイルを管理している場合は、これらのアクセス許可をすべて 1 つのカスタム ロールに追加できます。 カスタム ロールを作成したら、それをこれらのアクセス許可を必要とする任意のユーザーに[割り当てる](assign-role.md)ことができます。

ロールを作成、編集、または割り当てるには、アカウントに Azure AD の次のいずれかのアクセス許可が必要です。
- **グローバル管理者**
- **Intune サービス管理者**

## <a name="to-create-a-custom-role"></a>カスタム ロールを作成するには

1. Intune 資格情報で [Azure Portal](https://portal.azure.com) にサインインします。

2. 左側のメニューから **[すべてのサービス]** を選択し、テキスト ボックス フィルターに「**Intune**」と入力します。

3. **[Intune]** > **[ロール]** > **[すべてのロール]** > **[追加]** の順に選択します。

4. **[カスタム ロールの追加]** ブレードで、新しいロールの名前と説明を入力し、**[アクセス許可]** をクリックします。

5. **[アクセス許可]** ブレードで、このロールで使用するアクセス許可を選択します。 [Intune RBAC テーブル](https://gallery.technet.microsoft.com/Intune-RBAC-table-2e3c9a1a)を使用すると、適用するアクセス許可を決めるのに役立ちます。

6. **[スコープ (タグ)]** ブレードで、このロールのタグを選択します。 このロールでは、これらのタグも設定されているリソースにアクセスできます。

7. 終了したら、**[OK]** を選択します。

8. **[カスタム ロールの追加]** ブレードで、**[作成]** をクリックします。 新しいロールが **[Intune の役割 - すべてのロール]** ブレード上の一覧に表示されます。

## <a name="next-steps"></a>次の手順
- [ロールをユーザーに割り当てる](assign-role.md)
- [Intune でのロール ベースの管理制御について学習する](role-based-access-control.md)
