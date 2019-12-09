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
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: pjain
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3ca83287c58f8d2fb7c8eec5f8cc793e2c67b77a
ms.sourcegitcommit: 2fddb293d37453736ffa54692d03eca642f3ab58
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74390698"
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

5. **[アクセス許可]** ブレードで、このロールで使用するアクセス許可を選択します。

6. **[スコープ (タグ)]** ブレードで、このロールのタグを選択します。 このロールでは、これらのタグも設定されているリソースにアクセスできます。

7. 終了したら、 **[OK]** を選択します。

8. **[カスタム ロールの追加]** ブレードで、 **[作成]** をクリックします。 新しいロールが **[Intune の役割 - すべてのロール]** ブレード上の一覧に表示されます。


## <a name="copy-a-role"></a>ロールをコピーする

既存のロールをコピーすることもできます。

1. Intune 資格情報で [Azure Portal](https://portal.azure.com) にサインインし、 **[Intune]** を選択します。

2. **[ロール]** 、 **[すべてのロール]** の順に選択し、一覧からロールを選択し、 **[複製]** を選択します。

3. **[ロールの複製]** で名前を入力します。 必ず一意の名前を使用してください。

4. 元のロールからのアクセス許可とスコープ タグはすべて既に選択されています。 重複するロールの **[名前]** 、 **[説明]** 、 **[アクセス許可]** 、 **[スコープ (タグ)]** は後で変更できます。

5. **[作成]** を選択します。 

## <a name="next-steps"></a>次の手順
- [ロールをユーザーに割り当てる](assign-role.md)
- [Intune でのロール ベースの管理制御について学習する](role-based-access-control.md)
