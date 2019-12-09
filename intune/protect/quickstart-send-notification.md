---
title: クイック スタート - 非準拠デバイスに通知を送信する
titleSuffix: Microsoft Intune
description: このクイックスタートでは、Microsoft Intune を使用して、非準拠デバイスにメール通知を送信します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/21/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a1b89f2d-7937-46bb-926b-b05f6fa9c749
ms.reviewer: jinyoon
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6d89cfcafd5452b990509e0fa6fd431a614ee5c1
ms.sourcegitcommit: a7b479c84b3af5b85528db676594bdb3a1ff6ec6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74410252"
---
# <a name="quickstart-send-notifications-to-noncompliant-devices"></a>クイック スタート:非準拠デバイスに通知を送信する

このクイックスタートでは、Microsoft Intune を使用して、非準拠デバイスを使用している従業員のメンバーにメール通知を送信します。

既定では、Intune は、準拠していないデバイスを検出すると、直ちにコンプライアンス違反としてマークします。 その後、Azure Active Directory (Azure AD) の[条件付きアクセス](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)によってデバイスがブロックされます。 Intune では、準拠していないデバイスに対して行う追加アクションを柔軟に決定できます。 たとえば、非準拠デバイスをブロックする前に、準拠するための猶予期間をユーザーに与えることができます。

デバイスがコンプライアンスに対応していないときに行うアクションの 1 つは、デバイスのユーザーにメールを送ることです。 送信する前にメール通知をカスタマイズすることもできます。 具体的には、受信者、件名、メッセージ本文のほか、会社のロゴ、連絡先情報をカスタマイズできます。 Intune では、非準拠デバイスについての詳細もメール通知に含まれます。

Intune サブスクリプションがない場合は、[無料試用版アカウントにサインアップ](../fundamentals/free-trial-sign-up.md)します。

## <a name="prerequisites"></a>必要条件

デバイス コンプライアンス ポリシーを使ってデバイスを企業リソースからブロックする場合は、Azure AD の条件付きアクセスを設定する必要があります。 「[デバイス コンプライアンス ポリシーの作成](quickstart-set-password-length-android.md)」クイックスタートを完了している場合は、Azure Active Directory を使用しています。 Azure AD について詳しくは、[Azure Active Directory での条件付きアクセス](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)および [Intune で条件付きアクセスを使用する一般的な方法](../protect/conditional-access-intune-common-ways-use.md)に関する記事をご覧ください。

## <a name="sign-in-to-intune"></a>Intune にサインインする

[全体管理者](../fundamentals/users-add.md#types-of-administrators)または Intune [サービス管理者](../fundamentals/users-add.md#types-of-administrators)として、[Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。 Intune の試用版サブスクリプションを作成した場合、サブスクリプションを作成したアカウントがグローバル管理者になります。

## <a name="create-a-notification-message-template"></a>通知メッセージ テンプレートを作成する

ユーザーにメールを送信するには、通知メッセージ テンプレートを作成します。 デバイスがコンプライアンスに違反している場合、テンプレートに入力した詳細が、ユーザーに送信されたメールに表示されます。

1. Intune で、 **[デバイス]**  >  **[コンプライアンス ポリシー]**  >  **[通知]**  >  **[通知の作成]** の順に選択します。
2. 次の情報を入力します。

   - **名前**: *Contoso 管理者*
   - **[件名]** : *デバイスのポリシー準拠*
   - **[メッセージ]** :"*現在、あなたのデバイスは組織のコンプライアンス要件を満たしていません。* "
   - **電子メール ヘッダー - 会社のロゴを含める**:組織のロゴを表示するには、 **[有効]** に設定します。
   - **電子メール フッター - 会社名を含める**:組織名を表示するには、 **[有効]** に設定します。
   - **電子メール フッター - 連絡先情報を含める**:組織名の連絡先情報を表示するには、 **[有効]** に設定します。

   ![Intune でのコンプライアンス準拠通知メッセージの例](./media/quickstart-send-notification/quickstart-send-notification-01.png)

3. **[次へ]** を選択し、通知を確認します。 **[作成]** を選択すると、通知メッセージ テンプレートが使用できるようになります。

   > [!NOTE]
   > また、以前に作成した通知テンプレートを編集することもできます。

会社名、会社の連絡先情報、会社のロゴの設定について詳しくは、次の記事をご覧ください。

- [会社の情報とプライバシーに関する声明](../apps/company-portal-app.md#company-information-and-privacy-statement)
- [サポート情報](../apps/company-portal-app.md#support-information)
- [会社 ID のブランドのカスタマイズ](../apps/company-portal-app.md#company-identity-branding-customization)。

## <a name="add-a-noncompliance-policy"></a>非準拠ポリシーを追加する

デバイス コンプライアンス ポリシーを作成するときに、Intune によって、コンプライアンス違反に対するアクションが自動的に作成されます。 その後、Intune では、コンプライアンス ポリシーを満たしていないデバイスは非準拠としてマークされます。 デバイスが非準拠としてマークされるまでの期間をカスタマイズできます。 コンプライアンス ポリシーを作成するとき、または既存のコンプライアンス ポリシーを更新するときに、別のアクションを追加することもできます。

次の手順では、Windows 10 デバイス用のコンプライアンス ポリシーを作成します。

1. Intune で、 **[デバイス]**  >  **[コンプライアンス ポリシー]**  >  **[ポリシーの作成]** の順に選択します。

2. 次の情報を入力します。

   - **名前**: *Windows 10 コンプライアンス*
   - **説明**:*Windows 10 のコンプライアンス ポリシー*
   - **[プラットフォーム]** :Windows 10 以降

3. **[設定]**  >  **[システム セキュリティ]** を選択し、デバイス セキュリティ関連の設定を表示します。

4. 次のオプションを構成します。

   - **[モバイル デバイスのロック解除にパスワードを必要とする]** を **[必要]** に設定します。 ユーザーが自分のモバイル デバイスの情報にアクセスするときにパスワードを入力する必要があるかどうかを指定します。

   - **[パスワードの最小文字数]** を「**6**」に設定します。 パスワードに最低限必要な数字または文字の数を指定します。

   ![新しいコンプライアンス ポリシーのシステム セキュリティ設定](./media/quickstart-send-notification/system-security-settings-01.png)

5. **[OK]**  >  **[OK]**  >  **[作成]** の順に選択して、コンプライアンス ポリシーを作成します。

6. **[プロパティ]**  >  **[Action for noncompliance]\(非準拠のアクション\)**  >  **[追加]** を選択します。

7. **[アクション]** ドロップダウン ボックスで、 **[メールをエンド ユーザーに送信する]** が選択されていることを確認します。

8. **[メッセージ テンプレート]** を選択し、この記事で前に作成したテンプレートを選択し、 **[選択]** を選択してメッセージ テンプレートを選択します。

9. **[追加]**  >  **[OK]**  >  **[保存]** の順に選択して、変更を保存します。

## <a name="assign-the-policy"></a>ポリシーを割り当てる

特定のユーザー グループまたはすべてのユーザーに、コンプライアンス ポリシーを割り当てることができます。 デバイスが非準拠であることが Intune で認識されると、コンプライアンス ポリシーを満たすようにデバイスを更新する必要があることがユーザーに通知されます。 次の手順のようにしてポリシーを割り当てます。

1. Intune で、 **[デバイス]**  >  **[コンプライアンス ポリシー]** を選択し、前に作成した **Windows 10 コンプライアンス** ポリシーを選択します。

2. **[割り当て]** を選択します。

3. **[Assign to]\(割り当て先\)** ドロップダウン ボックスで、 **[すべてのユーザー]** を選択します。 これにより、すべてのユーザーが選択されます。 このコンプライアンス ポリシーを満たしていない **Windows 10 以降**のデバイスを持つすべてのユーザーに通知されます。

    > [!NOTE]
    > コンプライアンス ポリシーを割り当てるときに、包含または除外するグループを指定できます。

4. **[Save]** (保存) をクリックします。

ポリシーを正しく作成して保存すると、 **[コンプライアンス ポリシー - ポリシー]** の一覧に表示されます。 一覧で **[割り当て済み]** が **[はい]** に設定されていることに注意してください。

## <a name="next-steps"></a>次の手順

このクイック スタートでは、Intune を使用して、6 文字以上の長さのパスワードが必要なように、従業員の Windows 10 デバイス用のコンプライアンス ポリシーを作成して割り当てました。 Windows デバイス用のコンプライアンス ポリシーの作成について詳しくは、「[Intune で Windows デバイス用のデバイス コンプライアンス ポリシーを追加する](compliance-policy-create-windows.md)」をご覧ください。

この一連の Intune のクイック スタートに従うには、次のクイック スタートに進んでください。

> [!div class="nextstepaction"]
> [クイック スタート: クライアント アプリの追加および割り当て](../apps/quickstart-add-assign-app.md)
