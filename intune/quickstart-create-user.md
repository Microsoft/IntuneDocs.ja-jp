---
title: クイック スタート - Intune でユーザーを作成する
description: クイック スタート - Intune でユーザーを作成します。
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: quickstart
ms.date: 09/21/2018
ms.author: erikje
ms.openlocfilehash: 6a1d591e635dccd99551d9b8d40e099724a85d77
ms.sourcegitcommit: 27eed5aba5c8bfafb079171081b68f75a6cbffaf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/22/2018
ms.locfileid: "46581676"
---
# <a name="quickstart-create-a-user-and-assign-a-license-to-it"></a>クイック スタート: ユーザーを作成してライセンスを割り当てる

このクイック スタートでは、ユーザーを作成してライセンスを割り当てます。 Intune を使用する場合、会社のデータへのアクセス権を付与する各ユーザーには、ユーザー アカウントが必要です。 Intune 管理者は、このようなユーザーを構成してアクセス制御を管理できます。

Intune サブスクリプションがない場合は、[無料試用版アカウントにサインアップ](free-trial-sign-up.md)します。

## <a name="sign-in-to-intune"></a>Intune にサインインする

グローバル管理者または Intune サービス管理者として [Intune](https://aka.ms/intuneportal) にサインインします。

## <a name="create-a-user"></a>ユーザーを作成する

Intune デバイス管理に登録するユーザーには、ユーザー アカウントが必要です。

1. Intune で、**[ユーザー]** > **[すべてのユーザー]** > **[新しいユーザー]** の順に選択します。
![ブラウザー](media/quickstart-create-user/create-user.png)
2. **[名前]** ボックスに、「*Dewey Kellum*」と入力します。
3. **[ユーザー名]** ボックスに、「*Dewey@contoso.onmicrosoft.com*」を入力します。
4. **[グループ]** > **[Everyone]** > **[選択]** の順に選択します。
5. **[パスワードの表示]** を選択し、テスト デバイスにサインインできるように、自動生成されたパスワードをメモしてをおきます。
6. **[作成]** を選択します。

## <a name="assign-a-license-to-the-user"></a>ユーザーにライセンスを割り当てる

ユーザーを作成したら、[Office 365 ポータル](http://go.microsoft.com/fwlink/p/?LinkId=698854)を利用し、Intune ライセンスをそのユーザーに割り当てる必要があります。 ライセンスを割り当てないと、ユーザーは自分のデバイスを Intune に登録できません。 

1. Intune にサインインしたときに使用したものと同じ資格情報で [Office 365 ポータル](http://go.microsoft.com/fwlink/p/?LinkId=698854)にサインインします。
2. **[ユーザー]** > **[アクティブなユーザー]** の順に選択し、作成したユーザーを選択します。
3. **[場所]** の下で、ユーザーの場所を選択します。
3. **[製品ライセンス]** を選択し、**[Enterprise Mobility + Security E3]** (または Intune を含むお持ちの別のライセンス) を **[オン]** に設定します。
   > [!NOTE]
   > このとき、このユーザーのライセンスの 1 つが使用されます。 ライブ環境を利用している場合、後でこのライセンスの使用をオフにし、実際のユーザーに再度割り当てることができます。
5. **[保存]** を選びます。

## <a name="clean-up-resources"></a>リソースをクリーンアップする

このユーザーが必要なくなった場合は、削除することができます。削除するには、**[ユーザー]** > **[すべてのユーザー]** を選択し、一覧でそのユーザーを選択してから **[ユーザーの削除]** > **[はい]** の順に選択します。

## <a name="next-steps"></a>次の手順

このクイック スタートでは、ユーザーを作成してライセンスを割り当てました。 これでそのユーザーをグループに割り当てることができます。

> [!div class="nextstepaction"]
> [グループの作成](quickstart-create-group.md)
