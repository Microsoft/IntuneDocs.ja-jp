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
ms.openlocfilehash: bfa2758546595d1e6237d88e128958c50759eb04
ms.sourcegitcommit: 5881979c45fc973cba382413eaa193d369b8dcf6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/24/2020
ms.locfileid: "77569185"
---
# <a name="create-a-custom-role-in-intune"></a>Intune でカスタム ロールを作成する

特定のジョブ機能に必要なアクセス許可をすべて含むカスタム Intune ロールを作成できます。 たとえば、IT 部門の 1 つのグループがアプリケーション、ポリシー、構成プロファイルを管理している場合は、これらのアクセス許可をすべて 1 つのカスタム ロールに追加できます。 カスタム ロールを作成したら、それをこれらのアクセス許可を必要とする任意のユーザーに[割り当てる](assign-role.md)ことができます。

ロールを作成、編集、または割り当てるには、アカウントに Azure AD の次のいずれかのアクセス許可が必要です。
- **グローバル管理者**
- **Intune サービス管理者**

## <a name="to-create-a-custom-role"></a>カスタム ロールを作成するには

1. [Microsoft Endpoint Manager admin center](https://go.microsoft.com/fwlink/?linkid=2109431) で、 **[テナント管理]**  >  **[ロール]**  >  **[すべてのロール]**  >  **[作成]** を選択します。

2. **[基本]** ページで、新しいロールに名前と説明を入力して、 **[次へ]** を選択します。

3. **[アクセス許可]** ページで、このロールで使用するアクセス許可を選択します。

4. **[スコープ (タグ)]** ページで、このロールのタグを選択します。 このロールでは、これらのタグも設定されているリソースにアクセスできます。 **[次へ]** を選択します。

5. **[確認および作成]** ページで、完了したら、 **[作成]** を選択します。 新しいロールが **[Intune の役割 - すべてのロール]** ブレード上の一覧に表示されます。

## <a name="copy-a-role"></a>ロールをコピーする

既存のロールをコピーすることもできます。

1. [Microsoft Endpoint Manager admin center](https://go.microsoft.com/fwlink/?linkid=2109431) で、 **[テナント管理]**  >  **[ロール]**  >  **[すべてのロール]** を選択し、一覧でロールのチェック ボックスをオンにして、 **[重複]** を選択します。

2. **[基本]** ページで、名前を入力します。 必ず一意の名前を使用してください。

3. 元のロールからのアクセス許可とスコープ タグはすべて既に選択されています。 重複するロールの **[名前]** 、 **[説明]** 、 **[アクセス許可]** 、 **[スコープ (タグ)]** は後で変更できます。

4. 必要な変更をすべて行ったら、 **[次へ]** を選択して、 **[確認および作成]** ページに移動します。 **[作成]** を選択します。 

## <a name="next-steps"></a>次のステップ
- [ロールをユーザーに割り当てる](assign-role.md)
- [Intune でのロール ベースの管理制御について学習する](role-based-access-control.md)


