---
title: クイック スタート - ユーザーを管理するグループを作成する
titleSuffix: Microsoft Intune
description: このクイック スタートでは、Microsoft Intune を使用して、既存のユーザーに基づいてグループを作成します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/25/2019
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 723f4b4e-3090-4811-84ff-6af652abea5a
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7cbfe19e4f7aea28c16cae50c9b79336be81c8fa
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61511395"
---
# <a name="quickstart-create-a-group-to-manage-users"></a>クイック スタート:ユーザーを管理するグループを作成する

このクイック スタートでは、Intune を使用して、既存のユーザーに基づいてグループを作成します。 グループは、ユーザーを管理し、会社のリソースへの従業員のアクセスを制御するために使用されます。 これらのリソースは、会社のインターネットの一部である場合もあれば、SharePoint サイト、SaaS アプリ、または Web アプリなど、外部リソースの場合もあります。

Intune サブスクリプションがない場合は、[無料試用版アカウントにサインアップ](free-trial-sign-up.md)します。

>[!NOTE]
>Intune では、便利なように、最適化が組み込まれた **[すべてのユーザー]** グループと **[すべてのデバイス]** グループがコンソールで提供されています。

## <a name="prerequisites"></a>必要条件

- このクイック スタートを完了するには、[ユーザーを作成する](quickstart-create-user.md)必要があります。

## <a name="sign-in-to-intune"></a>Intune にサインインする

[全体管理者または Intune サービス管理者](users-add.md#types-of-administrators)として、[Intune](https://aka.ms/intuneportal) ポータルにサインインします。 Intune の試用版サブスクリプションを作成した場合、サブスクリプションを作成したアカウントがグローバル管理者になります。

## <a name="create-a-group"></a>グループの作成

このクイックスタート シリーズの後半で使用するグループを作成します。 グループを作成するには:

1. **[Microsoft Intune]** ウィンドウを開いたら、**[グループ]** > **[新しいグループ]** の順に選択します。
2. **[グループの種類]** ドロップダウン ボックスで **[セキュリティ]** を選択します。
3. **[グループ名]** フィールドに新しいグループの名前を入力します (例: **Contoso Testers**)。
4. グループの **[説明]** を追加します。
5. **[メンバーシップの種類]** を **[割り当て済み]** に設定します。 
6. **[メンバー]** をクリックし、一覧からグループのメンバーを 1 人または複数人選択します。

    ![Microsoft Intune でのグループ作成のスクリーンショット](./media/quickstart-use-groups-01.png)

7. **[選択]**、**[作成]** の順にクリックします。

グループが正常に作成されると、**[すべてのグループ]** の一覧にそのグループが表示されます。 

## <a name="next-steps"></a>次の手順

このクイック スタートでは、Intune を使用して、既存のユーザーに基づいてグループを作成しました。 Intune へのグループの追加について詳しくは、「[ユーザーとデバイスを整理するためのグループを追加する](groups-add.md)」をご覧ください。

この一連の Intune のクイック スタートに従うには、次のクイック スタートに進んでください。

> [!div class="nextstepaction"]
> [クイック スタート: Windows 10 デバイスの自動登録を設定する](quickstart-setup-auto-enrollment.md)
