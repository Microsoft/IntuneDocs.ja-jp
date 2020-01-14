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
ms.openlocfilehash: 68c2dc7df123593513c14e16e2626c7426f50b01
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207419"
---
# <a name="create-a-custom-role-in-intune"></a>Intune でカスタム ロールを作成する

特定のジョブ機能に必要なアクセス許可をすべて含むカスタム Intune ロールを作成できます。 たとえば、IT 部門の 1 つのグループがアプリケーション、ポリシー、構成プロファイルを管理している場合は、これらのアクセス許可をすべて 1 つのカスタム ロールに追加できます。 カスタム ロールを作成したら、それをこれらのアクセス許可を必要とする任意のユーザーに[割り当てる](assign-role.md)ことができます。

ロールを作成、編集、または割り当てるには、アカウントに Azure AD の次のいずれかのアクセス許可が必要です。
- **グローバル管理者**
- **Intune サービス管理者**

## <a name="to-create-a-custom-role"></a>カスタム ロールを作成するには

1. [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) で、 **[ロール]** ** > [すべてのロール]**  >  **[追加]** を選択します。

2. **[カスタム ロールの追加]** ブレードで、新しいロールの名前と説明を入力し、 **[アクセス許可]** をクリックします。

3. **[アクセス許可]** ブレードで、このロールで使用するアクセス許可を選択します。

4. **[スコープ (タグ)]** ブレードで、このロールのタグを選択します。 このロールでは、これらのタグも設定されているリソースにアクセスできます。

5. 終了したら、 **[OK]** を選択します。

6. **[カスタム ロールの追加]** ブレードで、 **[作成]** をクリックします。 新しいロールが **[Intune の役割 - すべてのロール]** ブレード上の一覧に表示されます。


## <a name="copy-a-role"></a>ロールをコピーする

既存のロールをコピーすることもできます。

1. [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) で、 **[ロール]** ** > [すべてのロール]** を選択し、一覧でロールを選択して、 **[重複]** を選択します。

2. **[ロールの複製]** で名前を入力します。 必ず一意の名前を使用してください。

3. 元のロールからのアクセス許可とスコープ タグはすべて既に選択されています。 重複するロールの **[名前]** 、 **[説明]** 、 **[アクセス許可]** 、 **[スコープ (タグ)]** は後で変更できます。

4. **[作成]** を選択します。 

## <a name="next-steps"></a>次のステップ
- [ロールをユーザーに割り当てる](assign-role.md)
- [Intune でのロール ベースの管理制御について学習する](role-based-access-control.md)
