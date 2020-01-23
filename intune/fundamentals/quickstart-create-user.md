---
title: クイック スタート - Intune でユーザーを作成する
description: クイック スタート - Intune でユーザーを作成します。
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.topic: quickstart
ms.date: 03/25/2019
ms.author: erikje
ms.manager: dougeby
ms.assetid: 820fcb18-0927-4ebd-be79-dce92b51c261
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: fdd97e69c97df5a266e147381d94b3d4419bab34
ms.sourcegitcommit: 52475fcd8d05d2f6b858d780ebb3d88eaadb0849
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/15/2020
ms.locfileid: "76036567"
---
# <a name="quickstart-create-a-user-in-intune-and-assign-them-a-license"></a>クイック スタート:Intune でユーザーを作成してライセンスを割り当てる

このクイック スタートでは、ユーザーを作成して Intune ライセンスを割り当てます。 Intune を使用する場合、会社のデータにアクセスできるようにしたい各ユーザーが独自のユーザー アカウントを持っている必要があります。 Intune 管理者は後からユーザーを構成して、アクセスの制御を管理できます。

Intune サブスクリプションがない場合は、[無料試用版アカウントにサインアップ](free-trial-sign-up.md)します。

## <a name="sign-in-to-intune"></a>Intune にサインインする

[グローバル管理者または Intune サービス管理者](users-add.md#types-of-administrators)として [Intune](https://aka.ms/intuneportal) にサインインします。 Intune の試用版サブスクリプションを作成した場合、サブスクリプションを作成したアカウントがグローバル管理者になります。

## <a name="create-a-user"></a>ユーザーを作成する

Intune デバイス管理に登録するユーザーには、ユーザー アカウントが必要です。 新しいユーザーを作成するには:

1. Intune で、 **[ユーザー]**  >  **[すべてのユーザー]**  >  **[新しいユーザー]** の順に選択します。
![ブラウザー](./media/quickstart-create-user/create-user.png)
2. **[名前]** ボックスに、「*Dewey Kellum*」のように名前を入力します。
3. **[ユーザー名]** ボックスに Dewey@contoso.onmicrosoft.com などのユーザー ID を入力します。

    > [!NOTE]
    > カスタム ドメイン名を構成していない場合、Intune のサブスクリプション (または[無料試用版](free-trial-sign-up.md#sign-up-for-a-microsoft-intune-free-trial)) を作成するために使用した確認済みのドメイン名を使用します。 

4. **[パスワードの表示]** を選択し、テスト デバイスにサインインできるように、自動生成されたパスワードをメモしてをおきます。
5. **[作成]** を選択します。

## <a name="assign-a-license-to-the-user"></a>ユーザーにライセンスを割り当てる

ユーザーを作成したら、[Microsoft 365 管理センター](https://go.microsoft.com/fwlink/p/?LinkId=698854)を使ってそのユーザーに Intune ライセンスを割り当てる必要があります。 ユーザーは、ライセンスを割り当てられないと、各自のデバイスを Intune に登録できません。 

ユーザーに Intune ライセンスを割り当てるには:

1. Intune にサインインしたときに使用した同じ資格情報で [Microsoft 365 管理センター](https://go.microsoft.com/fwlink/p/?LinkId=698854)にサインインします。
2. **[ユーザー]**  >  **[アクティブなユーザー]** の順に選択し、作成したユーザーを選択します。
3. **[製品ライセンス]** の隣の **[編集]** を選択します。
4. **[場所]** の下で、ユーザーの場所を選択します。
5. Intune のライセンス (または、ご自分が保有している Intune を含むその他のライセンス) の横の **[オン]** をクリックします。 表示された[製品名](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)** が Azure の管理でサービス プランとして使用されます。 

   > [!NOTE]
   > この設定では、所持しているライセンスの 1 つがこのユーザーに使用されます。 試用版環境を使用している場合、ライブ環境で実際のユーザーにこのライセンスを後で再割り当てします。
6. **[保存]**  >  **[閉じる]** の順に選択します。

新しいアクティブな Intune ユーザーが、**Intune** のライセンスを使用していると表示されます。

## <a name="clean-up-resources"></a>リソースをクリーンアップする

このユーザーをもう使用しない場合、[Microsoft 365 管理センター](https://go.microsoft.com/fwlink/p/?LinkId=698854)に移動し、 **[ユーザー]** から **[アクティブなユーザー]** に進み、一覧内のユーザーを選択し、 **[ユーザーの削除]** 、 **[ユーザーの削除]** 、 **[変更の確認]** 、 **[閉じる]** の順に選択します。

## <a name="next-steps"></a>次のステップ

このクイック スタートでは、ユーザーを作成し、そのユーザーに Intune ライセンスを割り当てました。 Intune へのユーザーの追加について詳しくは、「[Intune にユーザーを追加して管理アクセス許可を付与する](users-add.md)」をご覧ください。

この一連の Intune のクイック スタートに従うには、次のクイック スタートに進んでください。

> [!div class="nextstepaction"]
> [クイック スタート: ユーザーを管理するグループを作成する](../quickstart-create-group.md)
