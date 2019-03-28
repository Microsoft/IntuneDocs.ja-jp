---
title: クイック スタート - Intune でカスタム ロールを作成して割り当てる
description: クイック スタート - リモート デバイス マネージャーのカスタム ロールを作成して割り当てます。
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.localizationpriority: high
ms.topic: quickstart
ms.date: 09/21/2018
ms.author: erikje
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: be3ef61d3bdce2f1ad74a388a2ec50691313a1d1
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2019
ms.locfileid: "57400290"
---
# <a name="quickstart-create-and-assign-a-custom-role"></a>クイック スタート:カスタム ロールを作成して割り当てる

この Intune のクイック スタートでは、セキュリティ オペレーション部門用に特定のアクセス許可のあるカスタム ロールを作成します。 次に、このようなオペレーターのグループにロールを割り当てます。 すぐに使用できる既定のロールがいくつかあります。 しかし、このようなカスタム ロールを作成することで、モバイル デバイス管理システムのすべての部分に対して細かいアクセス制御ができるようになります。

Intune サブスクリプションがない場合は、[無料試用版アカウントにサインアップ](free-trial-sign-up.md)します。

## <a name="prerequisites"></a>必要条件

- このクイック スタートを完了するには、[グループを作成する](quickstart-create-group.md)必要があります。

## <a name="sign-in-to-intune"></a>Intune にサインインする

グローバル管理者または Intune サービス管理者として [Intune](https://aka.ms/intuneportal) にサインインします。

## <a name="create-a-custom-role"></a>カスタム ロールを作成する

カスタム ロールを作成するときに、さまざまなアクションに対してアクセス許可を設定できます。 セキュリティ オペレーションのロールに対し、オペレーターがデバイスの構成とポリシーを確認できるように、いくつかの読み取りアクセス許可を設定します。

1. Intune で、**[ロール]** > **[すべてのロール]** > **[追加]** の順に選択します。
![ブラウザー](media/quickstart-create-custom-role/add-custom-role.png)
2. **[カスタム ロールの追加]** の下の **[名前]** ボックスに、「*セキュリティ オペレーション*」と入力します。
3. **[説明]** ボックスに、「*このロールは、セキュリティ オペレーターがデバイス構成とコンプライアンス情報を監視できるようにします。*」と入力します。
4. **[構成]** > **[業務用デバイスの ID]** > **[読み取り]** の横の **[はい]** > **[OK]** の順に選択します。
![ブラウザー](media/quickstart-create-custom-role/corp-device-id-read.png)
5. **[デバイス コンプライアンス ポリシー]** > **[読み取り]** の横の **[はい]** > **[OK]** の順に選択します。
6. **[デバイスの構成]** > **[読み取り]** の横の **[はい]** > **[OK]** の順に選択します。
7. **[組織]** > **[読み取り]** の横の **[はい]** > **[OK]** の順に選択します。
8. **[OK]** > **[作成]** の順に選択します。

## <a name="assign-the-role-to-a-group"></a>ロールをグループに割り当てる

セキュリティ オペレーターが、新しいアクセス許可を使用できるようになるには、事前にそのロールをセキュリティ ユーザーを含むグループに割り当てる必要があります。

1. Intune で、**[ロール]** > **[すべてのロール]** > **[Security operations]** \(セキュリティ操作\) の順に選択します。
2. **[Intune ロール]** の下で、**[割り当て]** > **[割り当てる]** の順に選択します。
3. **[割り当て名]** ボックスに、「*Sec ops*」と入力します。
4. **[メンバー (グループ)]** > **[追加]** の順に選択します。
5. **[Contoso テスト担当者]** グループを選択します。
6. **[選択]** > **[OK]** の順に選択します。
7. **[スコープ (グループ)]** > **[含めるグループを選択]** > **[Contoso テスト担当者]** の順に選択します。
8. **[選択]** > **[OK]** > **[OK]** の順に選択します。

これで、グループ内のすべてのユーザーが*セキュリティ オペレーション* ロールのメンバーとなり、デバイスに関する次の情報を確認することができます。業務用デバイスの ID、デバイス コンプライアンス ポリシー、デバイスの構成、および組織情報。

## <a name="clean-up-resources"></a>リソースをクリーンアップする

新しいカスタム ロールを使用しなくなった場合は、削除することができます。 **[ロール]** > **[すべてのロール]** の順に選択し、ロールの横にある省略記号を選択し、**[削除]** を選択します。

## <a name="next-steps"></a>次の手順

このクイック スタートでは、カスタム セキュリティ オペレーション ロールを作成し、それをグループに割り当てました。 Intune のロールの詳細については、「[Microsoft Intune でのロール ベースの管理制御 (RBAC)](role-based-access-control.md)」を参照してください。

この一連の Intune のクイック スタートに従うには、次のクイック スタートに進んでください。

> [!div class="nextstepaction"]
> [クイック スタート: iOS 用の電子メール デバイス プロファイルを作成する](quickstart-email-profile.md)
