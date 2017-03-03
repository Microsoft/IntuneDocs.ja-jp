---
title: "30 日間の無料試用版にサインアップする"
titleSuffix: Intune Azure preview
description: "Intune Azure プレビュー: Azure で Intune にサインアップする方法。"
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 01/11/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 195931c0-8208-43bd-b0af-b1f8e469a32c
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 29b33341b136c8e8d76b666f94a9f620212944c5
ms.lasthandoff: 02/18/2017


---

# <a name="sign-up-for-a-microsoft-intune-free-trial-for-the-azure-portal-preview"></a>Azure Portal プレビューの Microsoft Intune 無料試用版にサインアップする

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

この記事では、Azure Portal プレビューの Intune スタンドアロンの試用版にサインアップする方法について説明します。 <!---and prepares your trial with some users so that you can then follow the associated evaluation guide to see how Intune manages mobile devices. ---> <!---or app data when devices are not enrolled in Intune.--->

<!--- ## Assumptions
This sign-up article and the evaluation guide assume you are using the trial for evaluation purposes only and intend to start with a clean environment when you subscribe.

To make it easy for you to get started with the trial, we are setting up a very simple environment that uses only Intune and assumes it will be your sole method of managing devices (known as the mobile device management authority). However, throughout the guide we will point you to deeper technical content if you want to explore farther.

You can do everything in the trial version that you can do in a subscription version; the only difference is you are limited to 100 user accounts in the trial.--->

<!--- ## Sign up for your trial--->
1. [Intune サインアップ](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20) ページにアクセスしてフォームに入力し、試用版サブスクリプションにサインアップします。

 <!--- If you have a work or school account and want to use that for your Intune trial, follow [these sign-in instructions](https://docs.microsoft.com/en-us/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-1) instead. However, this article assumes that you are not using such an account.---><br/> ![サインアップ ページの画像](./media/1-clicking-try.png)

 > [!TIP]
> IT 運用チームやユーザーの大半が自分と異なるロケールに属している場合は、そのロケールを **[Where's your company located? (会社の所在地はどこですか?)]** で選択することをお勧めします。

2. サインアップ プロセスの最後に、新しいアカウントの情報を含むメッセージが表示されます。 <br/> ![アカウント情報の画像](./media/2-end-of-sign-up-process.png) <br/>この時点で **[You're ready to go (準備完了)]** をクリックすると、Office 365 管理センターが表示されるので、そこでテスト環境にユーザーを追加できます。 <br/><br/>ただし、Intune Azure Portal プレビューに直接アクセスしたい場合は、新しいブラウザー ウィンドウを開き、アドレス バーに「**https://portal.azure.com**」と入力します。 Azure サインイン ページが表示されるので、提供されている資格情報を使用してサインインします。 Intune 試用版にサインインする際は常にこのアドレスを使用してください。 <br/> ![Azure Portal のサインイン ページの画像](./media/azure-portal-signin.png)

Intune Azure プレビューに初めてサインオンすると、Azure ダッシュボードに Intune が表示されないことがあります。 Intune サービスを Azure ダッシュボードに追加するには:
1. ダッシュボードの左にある Azure サービスの一覧で **[その他のサービス >]** を選択し、検索ボックスに「**Intune**」と入力します。
2. 一覧から **[Intune]** を選択し、星を選択してサービスの一覧にサービスを追加します。<br/> ![サービス一覧から Intune を選択する画像](./media/azure-add-intune1.png)
3. サービス一覧から **[Intune]** を選択し、Intune ダッシュボードを開きます。

試用版にサインアップすると、アカウント情報の記載された電子メール メッセージが、サインアップ プロセス中に指定した電子メール アドレスに送信されます。 このメールで、評価版がアクティブになったことが確認されます。


<!--- ## Add users
Before you leave the Office 365 Admin center for Intune, you need to add some users to your trial account.

In the Office 365 Admin center, you can add users individually or in bulk by uploading a .csv file. We will do both to set up your trial. However, in your production environment, you will probably want to take advantage of your Azure Active Directory user accounts, which you can learn more about in our [Getting Started guide](https://docs.microsoft.com/en-us/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-3) and in the [Next steps](#Next-steps) section of this article.

### Add an individual user
1. Choose either of the options to add a use to open a form that allows you to create a user. Only the items starred with an asterisk (\*) are required.
![Image of add user button options](./media/sign-up/add-user.png)


2.  When you add the user, the final step will be to send the user an email with their temporary Intune password. For the purposes of this evaluation, use your own work email address so you will receive the log-on information and see the email your users will get. You can then use these user identities to enroll test devices.<br/>

 ![Image of add user final step](./media/sign-up/new-user-2.png)

3. If you want to assign a user an admin role after you create it, you can edit the role in the Office 365 Admin center by selecting the user name from your list of users, and then choosing **Edit** in the Role line to see the list of user roles you can select from and assign to that user.

 ![Image of user  role options](./media/sign-up/change-user-role.png)

### Import multiple users
1. You will find the wizard for importing multiple users in the **More** list.

 ![Image of option to add multiple users](./media/sign-up/add-multiple-users.png)

2. To help you set up your .csv file correctly, you can download a template file to populate with your user data. Download the .csv file that contains headers and sample user information to see exactly the kind of data is needed for each field.

 ![Image of first step in bulk enrollment wizard](./media/sign-up/bulk-enroll-step-1.png)


3. After you’ve created and saved your .csv file, choose **Browse** to select the file. Verify, and choose **Next**. Your users will be uploaded and added to your list of active users.

> [!NOTE]
> Your users won't show up in Intune until they've enrolled a device to be managed.

Now it’s time to head over to Intune to start managing your users, their devices, and their apps.--->

## <a name="keeping-the-admin-experiences-straight"></a>管理者の経験を続ける
<!---### Classic Intune
There are two portals you will use for classic Intune:
- The Office 365 Admin center ([portal.office.com](https://portal.office.com))
- The Intune administration console ([manage.microsoft.com](https://manage.microsoft.com))

Normally, you’ll do your work in the Intune administration console, shown below. This is the site where you set up and manage your groups, policies, devices, and apps.

![Image of Intune administration console](./media/sign-up/intune-admin-console.png)

However, you will use the Office 365 Admin center, shown below, to add and manage your users and other aspects of your account, including billing and support.

![Image of Office 365 Admin center](./media/sign-up/office-admin-center.png)

You can navigate from the Office 365 Admin center to the Intune admin console. The admin centers are under the last item in the left navigation pane. Choose **Intune** to open the Intune admin console in a new tab.

![Image of link to Intune administration console](./media/sign-up/link-to-intune.png)

To get from Intune back to the Office 365 Admin center, choose the **Add Users** task on the Groups Overview page.

![Image of link back to Office 365  Admin center](./media/sign-up/task-add-users.png)--->

<!---### Intune Azure preview--->
Intune Azure プレビューで使用するポータルは&3; つあります。
- Azure ([portal.azure.com](https://portal.azure.com)) の Intune ダッシュボードでは、[Azure Portal にある Intune の各機能](what-is-microsoft-intune.md)を確認できます。
- Office 365 管理センター ([portal.office.com](https://portal.office.com)) では、ユーザーの追加と管理ができます (Azure Active Directory を使用していない場合)。 また、課金やサポートなど、アカウントのその他の要素を管理することもできます。
- クラシック Intune 管理コンソール ([manage.microsoft.com](https://manage.microsoft.com)) では、まだ Azure に追加されていない機能を確認できます。

通常、次のように、Intune ダッシュボードで作業します。 これがグループ、ポリシー、デバイス、アプリを設定し、管理する場所となります。

ダッシュボードからクラシック Intune 管理コンソールを開くには、**[クラシック Intune ポータルを開く]** タイルを選択します。

Intune Azure プレビューに戻るには、ブラウザーのアドレス バーに「https://portal.azure.com」と入力し、サービス一覧から **[Intune]** をもう一度選択します。

 ![Intune ダッシュボードの画像](./media/intune-azure-dashboard.png)


ただし、次に示すように、ユーザーを追加したり、ユーザーやアカウントのその他の設定 (請求やサポートなど) を管理したりするときは、Office 365 管理センターを利用します。

![Office 365 管理センターの画像](./media/office-admin-center.png)

Office 365 管理センターから Intune ダッシュボードに移動するには、ブラウザーのアドレス バーに「https://portal.azure.com」と入力します。 サービス一覧から **[Intune]** を選択します。

Intune から Office 365 管理センターに戻るには、ブラウザーのアドレス バーに「https://portal.office.com」と入力します。 既に Intune にログインしている場合は、Office 365 管理センターがそのまま表示されます。

## <a name="next-steps"></a>次のステップ

### <a name="intune-azure-preview"></a>Intune Azure プレビュー
詳細については、「[Intune in the Azure portal preview](what-is-microsoft-intune.md)」(Azure プレビュー ポータルの Intune) を参照してください。
### <a name="classic-intune"></a>クラシック Intune
評価シナリオ: [Microsoft Intune でモバイル デバイス管理を評価する](https://docs.microsoft.com/intune/understand-explore/mobile-device-management-trial-guide-microsoft-intune)

### <a name="integration-with-other-products"></a>他の製品との統合
Intune で Azure Active Directory ユーザー アカウントを使用する方法に関するページ:
- [ID の要件](https://docs.microsoft.com/en-us/active-directory/active-directory-hybrid-identity-design-considerations-overview#design-considerations-overview)
- [ディレクトリ同期の要件](https://docs.microsoft.com/en-us/active-directory/active-directory-hybrid-identity-design-considerations-directory-sync-requirements)
- [多要素認証の要件](https://docs.microsoft.com/en-us/active-directory/active-directory-hybrid-identity-design-considerations-multifactor-auth-requirements)

[Intune と System Center Configuration Manager](https://docs.microsoft.com/en-us/sccm/mdm/understand/hybrid-mobile-device-management) を使用する方法に関するページ

