---
title: クイック スタート - ユーザーを管理するグループを作成する
titlesuffix: Microsoft Intune
description: このクイック スタートでは、Microsoft Intune を使用して、既存のユーザーに基づいてグループを作成します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/21/2018
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 723f4b4e-3090-4811-84ff-6af652abea5a
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2b52265bb9b3df800c0e13450a2154e46098a933
ms.sourcegitcommit: 9d08545727543b434dd270371fa50233470f2bce
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50410822"
---
# <a name="quickstart-create-a-group-to-manage-users"></a>クイック スタート: ユーザーを管理するグループを作成する

このクイック スタートでは、Intune を使用して、既存のユーザーに基づいてグループを作成します。 グループは、ユーザーを管理し、会社のリソースへの従業員のアクセスを制御するために使用されます。 これらのリソースは、会社のインターネットの一部である場合もあれば、SharePoint サイト、SaaS アプリ、または Web アプリなど、外部リソースの場合もあります。

Intune サブスクリプションがない場合は、[無料試用版アカウントにサインアップ](free-trial-sign-up.md)します。

>[!NOTE]
>Intune では、便利なように、最適化が組み込まれた **[すべてのユーザー]** グループと **[すべてのデバイス]** グループがコンソールで提供されています。

## <a name="prerequisites"></a>前提条件

- このクイック スタートを完了するには、[ユーザーを作成する](quickstart-create-user.md)必要があります。

## <a name="sign-in-to-intune"></a>Intune にサインインする

[グローバル管理者または Intune サービス管理者](users-add.md#types-of-administrators)として [Intune](https://aka.ms/intuneportal) にサインインします。 Intune の試用版サブスクリプションを作成した場合、サブスクリプションを作成したアカウントがグローバル管理者になります。

## <a name="create-a-group"></a>グループの作成

このクイックスタート シリーズの後半で使用するグループを作成します。

1. **[Microsoft Intune]** ウィンドウを開いたら、**[グループ]** >  **[新しいグループ]** の順に選択します。
2. **[グループの種類]** ドロップダウン ボックスで **[セキュリティ]** を選択します。
3. **[名前]** を「Contoso テスト担当者」に設定し、グループの**説明**を追加します。
4. **[メンバーシップの種類]** を **[割り当て済み]** に設定します。 
5. **[メンバー]** をクリックし、既存の一覧からグループのメンバーを 1 人または複数選択します。

    ![Microsoft Intune でのグループ作成のスクリーンショット](./media/quickstart-use-groups-01.png)

6. **[選択]**、**[作成]** の順にクリックします。

グループが正常に作成されると、**[すべてのグループ]** の一覧にそのグループが表示されます。 

## <a name="next-steps"></a>次の手順

このクイック スタートでは、Intune を使用して、既存のユーザーに基づいてグループを作成しました。

> [!div class="nextstepaction"]
> [デバイス コンプライアンス ポリシーの作成](quickstart-create-policy.md)
