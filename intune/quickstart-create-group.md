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
ms.openlocfilehash: 3a4468f2e6919349095d934790740afc8c347282
ms.sourcegitcommit: 27eed5aba5c8bfafb079171081b68f75a6cbffaf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/22/2018
ms.locfileid: "46581664"
---
# <a name="quickstart-create-a-group-to-manage-users"></a>クイック スタート: ユーザーを管理するグループを作成する

このクイック スタートでは、Intune を使用して、既存のユーザーに基づいてグループを作成します。 グループは、ユーザーを管理し、会社のリソースへの従業員のアクセスを制御するために使用されます。 これらのリソースは、会社のインターネットの一部である場合もあれば、SharePoint サイト、SaaS アプリ、または Web アプリなど、外部リソースの場合もあります。

Intune サブスクリプションがない場合は、[無料試用版アカウントにサインアップ](free-trial-sign-up.md)します。

>[!NOTE]
>Intune では、便利なように、最適化が組み込まれた **[すべてのユーザー]** グループと **[すべてのデバイス]** グループがコンソールで提供されています。

## <a name="prerequisites"></a>必要条件

- このクイック スタートを完了するには、[ユーザーを作成する](quickstart-create-user.md)必要があります。

## <a name="sign-in-to-intune"></a>Intune にサインインする

グローバル管理者または Intune サービス管理者として [Intune](https://aka.ms/intuneportal) にサインインします。 Intune には、Azure portal で **[すべてのサービス]** > **[Intune]** を選択してアクセスします。 Intune は **[監視 + 管理]** セクションにあります。

## <a name="create-a-group"></a>グループの作成
1. **[Microsoft Intune]** ウィンドウを開いたら、**[グループ]** >  **[新しいグループ]** の順に選択します。
2. **[グループ]** ウィンドウで、**[グループの種類]** > **[セキュリティ]** の順に選択します。
3. **[名前]** を「Contoso テスト担当者」に設定し、グループの**説明**を追加します。
4. **[メンバーシップの種類]** に **[割り当て済み]** を設定します。 
5. **[メンバー]** をクリックして、既存の一覧からグループの**メンバー**を選択します。

    ![Microsoft Intune でのグループ作成のスクリーンショット](./media/quickstart-use-groups-01.png)

6. **[選択]** をクリックします。
7. **[作成]** をクリックします。

グループが正常に作成されると、**[すべてのグループ]** の一覧にそのグループが表示されます。 

## <a name="next-steps"></a>次の手順

このクイック スタートでは、Intune を使用して、既存のユーザーに基づいてグループを作成しました。

> [!div class="nextstepaction"]
> [デバイス コンプライアンス ポリシーの作成](quickstart-create-policy.md)
