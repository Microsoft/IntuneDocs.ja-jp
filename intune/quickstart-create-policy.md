---
title: 'クイック スタート: Windows 10 デバイスのデバイス コンプライアンス ポリシーを追加する'
description: このクイック スタートでは、会社のデータの保護と、エンド ユーザーが会社のリソースにアクセスするときに使用するデバイスの管理に役立つポリシーを作成します。 次に、グループにポリシーを割り当てます。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/17/2018
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1ac74ba5-7441-44ac-98b5-9d8bb8899747
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 9d9169ab353da30e0f7b292cea4f5b9c93e316aa
ms.sourcegitcommit: 2e88ec7a412a2db35034d30a70d20a5014ddddee
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2018
ms.locfileid: "49391554"
---
# <a name="quickstart-add-a-device-compliance-policy-for-a-windows-10-device"></a>クイック スタート: Windows 10 デバイスのデバイス コンプライアンス ポリシーを追加する
Windows の Intune デバイス コンプライアンス ポリシーでは、準拠しているものと見なされるために Windows デバイスが満たす必要のあるルールと設定を指定します。 このようなポリシーを[条件付きアクセス](https://docs.microsoft.com/intune/conditional-access)と一緒に使用することにより、会社のリソースへのアクセスを許可または阻止することができます。 コンプライアンス違反に対して、デバイス レポートを取得したり、是正措置を取ったりすることもできます。

このクイック スタートでは、Windows 10 デバイスのデバイス コンプライアンス ポリシーを作成し、デバイス グループをそのポリシーに割り当てます。

Intune サブスクリプションがない場合は、[無料試用版アカウントにサインアップ](free-trial-sign-up.md)します。

## <a name="prerequisites"></a>必要条件
- このクイック スタートを完了するには、まず[ユーザーを作成](quickstart-create-user.md)し、[グループを作成](quickstart-create-group.md)する必要があります。


## <a name="sign-in-to-intune"></a>Intune にサインインする
グローバル管理者または Intune サービス管理者として [Intune](https://aka.ms/intuneportal) にサインインします。

## <a name="create-a-device-compliance-policy"></a>デバイス コンプライアンス ポリシーの作成
1. **[デバイスのポリシー準拠]** > **[ポリシー]** > **[ポリシーの作成]** の順に選択します。
2. **[名前]** に「**Windows 10 コンプライアンス**」、**[説明]** に「**Windows 10 のサンプル コンプライアンス ポリシー**」と入力します。
3. **[プラットフォーム]** では、**[Windows 10 以降]** を選択します。
4. **[設定]** で **[システム セキュリティ]** を選択し、**[モバイル デバイスのロック解除にパスワードを必要とする]** を **[必要]** に設定します。 ポリシーの設定が完了したら、**[OK]** を選択します。
   ![コンプライアンス ポリシー](/intune/media/quickstart-create-policy/compliance-policy.png)
5. **[Windows 10 コンプライアンス ポリシー]** ウィンドウを閉じます。 
6. **[ポリシーの作成]** ウィンドウで **[作成]** を選択します。 この手順ではポリシーを作成し、**[デバイス コンプライアンス]** > **[ポリシー]** の順に選択してポリシーを一覧表示します。
7. 新しいポリシーを選択し、**[割り当て]** を選択します。 Azure Active Directory (AD) のセキュリティ グループは、含めることも除外することもできます。
8. **[選択したグループ]** を選択すると、既存の Azure AD セキュリティ グループが表示されます。 **[Contoso Testers]** を選択し、**[保存]** を選択してグループ内のユーザーにポリシーを展開します。 [グループの作成](quickstart-create-group.md)手順でこのグループを作成しなかった場合は、任意のグループを使用できます。 

## <a name="clean-up-resources"></a>リソースをクリーンアップする
不要になったら、ポリシーを削除します。 この場合、**[Windows 10 コンプライアンス]** ポリシーを選択し、**[削除]** をクリックします。 

## <a name="next-steps"></a>次の手順
このクイック スタートでは、単純なデバイス コンプライアンス ポリシーを作成して割り当てました。 このポリシーを適用する Windows 10 デバイスを登録するには、自動登録を設定するクイック スタートに進んでください。 
 
> [!div class="nextstepaction"]
> [デバイスのパスワードの長さを設定する](quickstart-set-password-length-android.md)