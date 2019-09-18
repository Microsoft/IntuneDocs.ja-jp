---
title: Intune でカスタム ロールを作成する
description: Microsoft Intune でカスタム ロールを作成する方法について学習します。
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
ms.reviewer: pjain
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 10366a41be05dbedee5cd84a1222a727a02a1b93
ms.sourcegitcommit: 74911a263944f2dbd9b754415ccda6c68dae0759
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2019
ms.locfileid: "71071476"
---
# <a name="create-a-custom-role-in-intune"></a>Intune でカスタム ロールを作成する

特定のジョブ機能に必要なアクセス許可をすべて含むカスタム Intune ロールを作成できます。 たとえば、IT 部門の 1 つのグループがアプリケーション、ポリシー、構成プロファイルを管理している場合は、これらのアクセス許可をすべて 1 つのカスタム ロールに追加できます。 カスタム ロールを作成したら、それをこれらのアクセス許可を必要とする任意のユーザーに[割り当てる](assign-role.md)ことができます。

ロールを作成、編集、または割り当てるには、アカウントに Azure AD の次のいずれかのアクセス許可が必要です。
- **グローバル管理者**
- **Intune サービス管理者**

## <a name="to-create-a-custom-role"></a>カスタム ロールを作成するには

1. Intune 資格情報で [Azure Portal](https://portal.azure.com) にサインインします。

2. 左側のメニューから **[すべてのサービス]** を選択し、テキスト ボックス フィルターに「**Intune**」と入力します。

3. **[Intune]**  >  **[ロール]**  >  **[すべてのロール]**  >  **[追加]** の順に選択します。

4. **[カスタム ロールの追加]** ブレードで、新しいロールの名前と説明を入力し、 **[アクセス許可]** をクリックします。

5. **[アクセス許可]** ブレードで、このロールで使用するアクセス許可を選択します。 [Intune RBAC テーブル](https://gallery.technet.microsoft.com/Intune-RBAC-table-2e3c9a1a)を使用すると、適用するアクセス許可を決めるのに役立ちます。

6. **[スコープ (タグ)]** ブレードで、このロールのタグを選択します。 このロールでは、これらのタグも設定されているリソースにアクセスできます。

7. 終了したら、 **[OK]** を選択します。

8. **[カスタム ロールの追加]** ブレードで、 **[作成]** をクリックします。 新しいロールが **[Intune の役割 - すべてのロール]** ブレード上の一覧に表示されます。

## <a name="next-steps"></a>次の手順
- [ロールをユーザーに割り当てる](assign-role.md)
- [Intune でのロール ベースの管理制御について学習する](role-based-access-control.md)
