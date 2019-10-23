---
title: クイック スタート - 非準拠デバイスに通知を送信する
titleSuffix: Microsoft Intune
description: このクイック スタートでは、Microsoft Intune を使用して、非準拠デバイスにメール通知を送信します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/24/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a1b89f2d-7937-46bb-926b-b05f6fa9c749
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8f8de97178beedf7e5017330bae106824c329b32
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72504225"
---
# <a name="quickstart-send-notifications-to-noncompliant-devices"></a>クイック スタート:非準拠デバイスに通知を送信する

このクイック スタートでは、Microsoft Intune を使用して、非準拠デバイスを使用している従業員のメンバーにメール通知を送信します。

既定では、Intune は、準拠していないデバイスを検出すると、直ちにコンプライアンス違反としてマークします。 その後、Azure Active Directory (AAD) の[条件付きアクセス](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)でデバイスがブロックされます。 デバイスが準拠していない場合は、Intune で非準拠に対するアクションを追加し、対処方法を柔軟に決定できます。 たとえば、非準拠デバイスをブロックする前に、準拠するための猶予期間をユーザーに与えることができます。

デバイスがコンプライアンスを満たしていないときに実行できるアクションの 1 つは、エンド ユーザーにメールを送ることです。 エンド ユーザーに送信する前に、メール通知をカスタマイズすることもできます。 具体的には、受信者、件名、メッセージ本文のほか、会社のロゴ、連絡先情報をカスタマイズできます。 Intune では、非準拠デバイスについての詳細もメール通知に追加されます。

Intune サブスクリプションがない場合は、[無料試用版アカウントにサインアップ](../fundamentals/free-trial-sign-up.md)します。

## <a name="prerequisites"></a>必要条件
- デバイス コンプライアンス ポリシーを使ってデバイスを企業リソースからブロックする場合は、AAD の条件付きアクセスを設定する必要があります。 「[デバイス コンプライアンス ポリシーを作成する](quickstart-set-password-length-android.md)」クイック スタートを完了している場合は、Azure Active Directory を使用しています。 AAD の詳細については、「[Azure Active Directory の条件付きアクセスとは](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)」および「[Intune での条件付きアクセスの一般的な使用方法](../protect/conditional-access-intune-common-ways-use.md)」を参照してください。

## <a name="sign-in-to-intune"></a>Intune にサインインする

[全体管理者](../fundamentals/users-add.md#types-of-administrators)または Intune [サービス管理者](../fundamentals/users-add.md#types-of-administrators)として、[Intune](https://aka.ms/intuneportal) ポータルにサインインします。 Intune の試用版サブスクリプションを作成した場合、サブスクリプションを作成したアカウントがグローバル管理者になります。

## <a name="create-a-notification-message-template"></a>通知メッセージ テンプレートを作成する

ユーザーにメールを送信するには、通知メッセージ テンプレートを作成します。 デバイスがコンプライアンスに違反している場合、テンプレートに入力した詳細が、ユーザーに送信されたメールに表示されます。

1. Intune で、 **[デバイスのポリシー準拠]**  >  **[通知]**  >  **[通知の作成]** の順に選択します。 
2. 次の情報を入力します。

   - **名前**: *Contoso 管理者*
   - **[件名]** : *デバイスのポリシー準拠*
   - **[メッセージ]** :"*現在、あなたのデバイスは組織のコンプライアンス要件を満たしていません。* "
   - **電子メール ヘッダー - 会社のロゴを含める**:組織のロゴを表示するには、 **[有効]** に設定します。
   - **電子メール フッター - 会社名を含める**:組織名を表示するには、 **[有効]** に設定します。
   - **電子メール フッター - 連絡先情報を含める**:組織名の連絡先情報を表示するには、 **[有効]** に設定します。

   ![Intune でのコンプライアンス準拠通知メッセージの例](./media/quickstart-send-notification/quickstart-send-notification-01.png)

3. 情報の追加が完了したら、 **[作成]** を選択します。 通知メッセージ テンプレートが使用できるようになります。

    > [!NOTE]
    > また、以前に作成した通知テンプレートを編集することもできます。

会社名、会社の連絡先情報、会社のロゴの設定について詳しくは、「[会社の情報とプライバシーに関する声明](../apps/company-portal-app.md#company-information-and-privacy-statement)」、「[サポート情報](../apps/company-portal-app.md#support-information)」、および「[会社 ID のブランドのカスタマイズ](../apps/company-portal-app.md#company-identity-branding-customization)」をご覧ください。 

## <a name="add-a-noncompliance-policy"></a>非準拠ポリシーを追加する

デバイス コンプライアンス ポリシーを作成するときに、Intune によって、コンプライアンス違反に対するアクションが自動的に作成されます。 デバイスがコンプライアンス ポリシーを満たしていない場合、Intune は自動的にデバイスを非準拠としてマークします。 デバイスが非準拠としてマークされるまでの期間をカスタマイズできます。 コンプライアンス ポリシーを作成するとき、または既存のコンプライアンス ポリシーを更新するときに、別のアクションを追加することもできます。 

次の手順では、Windows 10 デバイス用のコンプライアンス ポリシーを作成します。

1. Intune で、 **[デバイスのポリシー準拠]** を選択します。
2. **[ポリシー]**  >  **[ポリシーの作成]** を選択します。
3. 次の情報を入力します。

   - **名前**: *Windows 10 コンプライアンス*
   - **説明**:*Windows 10 のコンプライアンス ポリシー*
   - **[プラットフォーム]** :Windows 10 以降

4. **[設定]**  >  **[システム セキュリティ]** を選択し、デバイス セキュリティ関連の設定を表示します。
5. **[モバイル デバイスのロック解除にパスワードを必要とする]** を **[必要]** に設定します。 ユーザーが自分のモバイル デバイスの情報にアクセスするときにパスワードを入力する必要があるかどうかを指定します。 
6. **[パスワードの最小文字数]** を「**6**」に設定します。 パスワードに最低限必要な数字または文字の数を指定します。

    <img alt="System Security settings for a new compliance policy" src="./media/quickstart-send-notification/quickstart-send-notification-01.png" width="600">

7. **[OK]**  >  **[OK]**  >  **[作成]** の順に選択して、コンプライアンス ポリシーを作成します。
8. **[プロパティ]**  >  **[Action for noncompliance]\(非準拠のアクション\)**  >  **[追加]** を選択します。
9. **[アクション]** ドロップダウン ボックスで、 **[メールをエンド ユーザーに送信する]** が選択されていることを確認します。
10. **[メッセージ テンプレート]**  > "**Contoso 管理者**" >  **[選択]** を選択して、このトピックで前に作成したメッセージ テンプレートを選択します。
11. **[追加]**  >  **[OK]**  >  **[保存]** の順に選択して、変更を保存します。

## <a name="assign-the-policy"></a>ポリシーを割り当てる

特定のユーザー グループまたはすべてのユーザーに、コンプライアンス ポリシーを割り当てることができます。 デバイスが非準拠であることを Intune が認識すると、コンプライアンス ポリシーを満たすようにデバイスを更新する必要があることがユーザーに通知されます。 次の手順のようにして、ポリシーを割り当てることができます。

1. 前に作成した "**Windows 10 コンプライアンス**" ポリシーを選択します。
2. **[割り当て]** を選択します。
3. **[Assign to]\(割り当て先\)** ドロップダウン ボックスで、 **[すべてのユーザー]** を選択します。 これにより、すべてのユーザーが選択されます。 このコンプライアンス ポリシーを満たしていない **Windows 10 以降**のデバイスを持つすべてのユーザーに通知されます。

    > [!NOTE]
    > コンプライアンス ポリシーを割り当てるときに、包含または除外するグループを指定できます。

4. **[Save]** (保存) をクリックします。

ポリシーを正常に作成して保存すると、 **[デバイスのポリシー準拠 - ポリシー]** の一覧に表示されます。 一覧で **[割り当て済み]** が **[はい]** に設定されていることに注意してください。

## <a name="next-steps"></a>次の手順

このクイック スタートでは、Intune を使用して、6 文字以上の長さのパスワードが必要なように、従業員の Windows 10 デバイス用のコンプライアンス ポリシーを作成して割り当てました。 Windows デバイス用のコンプライアンス ポリシーの作成について詳しくは、「[Intune で Windows デバイス用のデバイス コンプライアンス ポリシーを追加する](compliance-policy-create-windows.md)」をご覧ください。

この一連の Intune のクイック スタートに従うには、次のクイック スタートに進んでください。

> [!div class="nextstepaction"]
> [クイック スタート: クライアント アプリの追加および割り当て](../apps/quickstart-add-assign-app.md)
