---
title: クイック スタート - Intune でユーザーを作成する
description: クイック スタート - Intune でユーザーを作成します。
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.topic: quickstart
ms.date: 01/17/2020
ms.author: erikje
ms.manager: dougeby
ms.assetid: 820fcb18-0927-4ebd-be79-dce92b51c261
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: f6aa57b71e052e3fc8566fcdff8bdd9ef5d1c39e
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/26/2020
ms.locfileid: "76754492"
---
# <a name="quickstart-create-a-user-in-intune-and-assign-the-user-a-license"></a>クイック スタート:Intune でユーザーを作成してそのユーザーにライセンスを割り当てる

このクイックスタートでは、ユーザーを作成してそのユーザーに Intune ライセンスを割り当てます。 Intune を使用する場合、会社のデータにアクセスできるようにしたい各ユーザーが独自のユーザー アカウントを持っている必要があります。 Intune 管理者は後からユーザーを構成して、アクセスの制御を管理できます。

## <a name="prerequisites"></a>[前提条件]

- Microsoft Intune サブスクリプション。 [無料試用版アカウントにサイン アップします](../fundamentals/free-trial-sign-up.md)。

## <a name="sign-in-to-intune-in-microsoft-endpoint-manager"></a>Microsoft Endpoint Manager で Intune にサインインする

[全体管理者または Intune サービス管理者](users-add.md#types-of-administrators)として、[Microsoft Endpoint Manager admin center](https://go.microsoft.com/fwlink/?linkid=2109431) にサインインします。 Intune の無料試用版サブスクリプションを作成した場合、サブスクリプションを作成したアカウントがグローバル管理者になります。

## <a name="create-a-user"></a>ユーザーを作成する

Intune デバイス管理に登録するユーザーには、ユーザー アカウントが必要です。 新しいユーザーを作成するには:

1. Microsoft エンドポイント マネージャーで、 **[ユーザー]** > **[すべてのユーザー]** > **[新しいユーザー]** を選択します。![Microsoft Endpoint Manager で、[新しいユーザー] を選択する](./media/quickstart-create-user/create-user.png)
2. **[名前]** ボックスに、「*Dewey Kellum*」のように名前を入力します。![ユーザーの詳細を追加する](./media/quickstart-create-user/create-user-02.png)
3. **[ユーザー名]** ボックスに「Dewey@contoso.onmicrosoft.com」のようにユーザー ID を入力します。

    > [!NOTE]
    > カスタム ドメイン名を構成していない場合、Intune のサブスクリプション (または[無料試用版](free-trial-sign-up.md#sign-up-for-a-microsoft-intune-free-trial)) を作成するために使用した確認済みのドメイン名を使用します。 

4. **[パスワードの表示]** を選択して自動生成されたパスワードを記憶し、テスト デバイスにサインインできるようにします。
5. **[作成]** を選択します。

## <a name="assign-a-license-to-the-user"></a>ユーザーにライセンスを割り当てる

ユーザーを作成したら、[Microsoft 365 管理センター](https://go.microsoft.com/fwlink/p/?LinkId=698854)を使ってそのユーザーに Intune ライセンスを割り当てる必要があります。 ユーザーは、ライセンスを割り当てられないと、各自のデバイスを Intune に登録できません。

ユーザーに Intune ライセンスを割り当てるには:

1. Intune にサインインしたときに使用した同じ資格情報で [Microsoft 365 管理センター](https://go.microsoft.com/fwlink/p/?LinkId=698854)にサインインします。
2. **[ユーザー]**  >  **[アクティブ ユーザー]** を選択し、作成したユーザーを選択します。
3. **[ライセンスとアプリ]** タブを選択します。
4. **[場所の選択]** で、ユーザーの場所を選択します (まだ設定されていない場合)。
2. **[ライセンス]** セクションの **[Intune]** チェック ボックスをオンにします。 別のライセンスに Intune が含まれている場合は、そのライセンスを選択できます。 表示された[製品名](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)が Azure の管理でサービス プランとして使用されます。

    ![場所と Intune ライセンスを選択する](./media/quickstart-create-user/create-user-03.png)

   > [!NOTE]
   > この設定では、所持しているライセンスの 1 つがこのユーザーに使用されます。 試用版環境を使用している場合、ライブ環境で実際のユーザーにこのライセンスを後で再割り当てします。

6. **[変更の保存]** を選択します。

新しいアクティブな Intune ユーザーが、**Intune** のライセンスを使用していると表示されます。

## <a name="clean-up-resources"></a>リソースをクリーンアップする

このユーザーが不要になった場合は、[[Microsoft 365 管理センター]](https://go.microsoft.com/fwlink/p/?LinkId=698854) に移動し、 **[ユーザー]**  >  *<そのユーザー>*  > *ユーザーの削除アイコン* >  **[ユーザーの削除]**  >  **[閉じる]** を選択します。

   ![削除アイコンを選択する](./media/quickstart-create-user/create-user-04.png)

## <a name="next-steps"></a>次のステップ

このクイックスタートでは、ユーザーを作成し、そのユーザーに Intune ライセンスを割り当てました。 Intune へのユーザーの追加について詳しくは、「[Intune にユーザーを追加して管理アクセス許可を付与する](users-add.md)」をご覧ください。

この Intune クイックスタート シリーズを続行するには、次のクイックスタートに進んでください。

> [!div class="nextstepaction"]
> [クイック スタート: ユーザーを管理するグループを作成する](../quickstart-create-group.md)
