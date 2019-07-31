---
title: クイック スタート - アプリ保護ポリシーを作成して割り当てる
titleSuffix: Microsoft Intune
description: このクイック スタートでは、Microsoft Intune を使用して、アプリ保護ポリシーを作成および割り当てます。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/24/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2586fce0-5dca-4686-b9c4-791778838401
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 626c5d49c4f6bc7fef5f4f29c2397fafead50fda
ms.sourcegitcommit: d2ac912b834c4840de9cc92ba1815b6ecfbfb52b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/25/2019
ms.locfileid: "68482995"
---
# <a name="quickstart-create-and-assign-an-app-protection-policy"></a>クイック スタート:アプリ保護ポリシーを作成して割り当てる

このクイック スタートでは、Intune を使用してエンドユーザーのデバイス上のクライアント アプリにアプリ保護ポリシーを作成および割り当てます。 Intune では、アプリ保護ポリシーを使用し、ご使用のアプリが組織のデータ保護要件を満たしていることを確認します。

Intune サブスクリプションがない場合は、[無料試用版アカウントにサインアップ](free-trial-sign-up.md)します。

## <a name="prerequisites"></a>必要条件

- このクイック スタートを完了するには、[ユーザーの作成](quickstart-create-user.md)、[グループの作成](quickstart-create-group.md)、[デバイスの登録](quickstart-setup-auto-enrollment.md)、および[アプリの追加および割り当て](quickstart-add-assign-app.md)を行う必要があります。

## <a name="sign-in-to-intune"></a>Intune にサインインする

[グローバル管理者または Intune サービス管理者](users-add.md#types-of-administrators)として [Intune](https://aka.ms/intuneportal) にサインインします。 Intune の試用版サブスクリプションを作成した場合、サブスクリプションを作成したアカウントがグローバル管理者になります。

## <a name="create-an-app-protection-policy"></a>アプリ保護ポリシーを作成する

次の手順に従って、アプリ保護ポリシーを作成します。

1. [Intune](https://aka.ms/intuneportal) で、 **[クライアント アプリ]**  >  **[アプリ保護ポリシー]**  >  **[ポリシーの作成]** の順に選択します。 
2. 次の詳細を入力します。 

    - **名前**: *Windows 10 コンテンツの保護*
    - **説明**:*このポリシーが関連付けられているユーザーは、デバイス上の割り当てられているアプリと管理対象外のアプリ間で、いかなるコンテンツも切り取ったり、コピーしたり、貼り付けることはできません。*
    - **[プラットフォーム]** :*Windows 10*
    - **[登録の状態]** :*登録済み*

3. **[Protected apps]** \(保護されているアプリ\) を選択し、このポリシーに従う必要のあるアプリを選択します。
4. **[アプリの追加]** をクリックします。
5. **[おすすめのアプリ]** から **[Word Mobile]** を選択します。
5. **[OK]**  >  **[OK]** の順にクリックします。 
6. **[必須の設定]** を選択して、そのアプリを設定します。
7. **[オーバーライドの許可]** をクリックして、Windows Information Protection モードを設定します。 このオプションを選択すると、エンタープライズ データが保護されているアプリから出ることをブロックします。
8. **[OK]**  >  **[作成]** の順にクリックします。

これで Intune にアプリ保護ポリシーが表示されます。

### <a name="assign-the-app-protection-policy"></a>アプリ保護ポリシーを割り当てる

Intune でアプリ保護ポリシーを作成したら、グループに割り当てることができます。 

アプリ保護ポリシーは、次の手順で割り当てます。

1. [Intune](https://aka.ms/intuneportal) で、 **[Intune]**  >  **[クライアント アプリ]**  >  **[アプリ保護ポリシー]** の順に選択します。 
2. 前に作成したアプリ保護ポリシーを選択します。 このクイック スタートでは、そのポリシーは「**Windows 10 コンテンツの保護**」になります。
3. **[割り当て]** を選択します。
4. **[含める]** タブで **[含めるグループを選択]** を選択します。
5. 含めるグループとして **[Contoso テスト担当者]** を選択します。
6. **[選択]**  >  **[保存]** の順にクリックします。 

これでアプリ保護ポリシーが割り当てられました。

> [!NOTE]
> アプリ保護ポリシーは、デバイスを含むグループには適用できず、ユーザーを含むグループにしか適用できません。

## <a name="next-steps"></a>次の手順

このクイック スタートでは、アプリ保護ポリシーを作成して割り当てました。 このポリシーが割り当てられているユーザーは、デバイス上の割り当てられているアプリと管理対象外のアプリ間で、いかなるコンテンツも切り取ったり、コピーしたり、貼り付けることはできません。 この種類の保護は、ご自分の組織データを保護するのに役立ちます。 Intune のアプリ保護ポリシーの詳細については、「[アプリ保護ポリシーとは](app-protection-policy.md)」をご覧ください。

この一連の Intune のクイック スタートに従うには、次のクイック スタートに進んでください。

> [!div class="nextstepaction"]
> [クイック スタート: カスタム ロールの作成および割り当て](quickstart-create-custom-role.md)
