---
title: チュートリアル - Intune マネージド デバイス上で Exchange Online の電子メールを保護する
titleSuffix: Microsoft Intune
description: iOS Intune コンプライアンス ポリシーと Azure AD の条件付きアクセスを使用してマネージド デバイスと Outlook アプリを必要とすることで Exchange Online をセキュリティ保護する方法を説明します。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/26/2019
ms.topic: tutorial
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f4a8e873c48ceb59bfb8ac98fec9a29fa51d6cd3
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/01/2019
ms.locfileid: "58799770"
---
# <a name="tutorial-protect-exchange-online-email-on-managed-devices"></a>チュートリアル: マネージド デバイス上で Exchange Online の電子メールを保護する
デバイス コンプライアンス ポリシーと条件付きアクセスを使用して、iOS デバイスが Intune によって管理され、承認されたメール アプリを使用している場合にのみ、Exchange Online のメールにアクセスできるようにする方法を説明します。 

このチュートリアルでは、次の方法について説明します。 
> [!div class="checklist"]
> * Intune iOS デバイス コンプライアンス ポリシーを作成して、デバイスが準拠済みと見なされるために満たす必要のある条件を設定します。
> * iOS デバイスが Intune に登録されていて、Intune のポリシーに準拠し、Exchange Online のメールにアクセスするために承認された Outlook モバイル アプリを使用していることを必要とする、Azure Active Directory (Azure AD) の条件付きアクセス ポリシーを作成します。

Intune サブスクリプションがない場合は、[無料試用版アカウントにサインアップ](free-trial-sign-up.md)します。

## <a name="prerequisites"></a>必要条件
  - このチュートリアルでは、次のサブスクリプションのあるテスト テナントが必要です。
    - Azure Active Directory Premium ([無料試用版](https://azure.microsoft.com/free/?WT.mc_id=A261C142F))
    - Exchange を含む Office 365 Business サブスクリプション ([無料試用版](https://go.microsoft.com/fwlink/p/?LinkID=510938))
  - 始める前に、「[クイック スタート:iOS 用の電子メール デバイス プロファイルを作成する](quickstart-email-profile.md)」の手順に従って、iOS デバイス用のテスト デバイス プロファイルを作成します。

## <a name="sign-in-to-intune"></a>Intune にサインインする

グローバル管理者または Intune サービス管理者として [Intune](https://aka.ms/intuneportal) にサインインします。 Intune の試用版サブスクリプションを作成した場合、サブスクリプションを作成したアカウントがグローバル管理者になります。

## <a name="create-the-ios-device-compliance-policy"></a>iOS デバイスのコンプライアンス ポリシーを作成する
Intune デバイス コンプライアンス ポリシーを設定して、デバイスが準拠済みと見なされるために満たす必要のある条件を設定します。 このチュートリアルでは、iOS デバイス用のデバイス コンプライアンス ポリシーを作成します。 コンプライアンス ポリシーはプラットフォームに固有なので、評価するデバイス プラットフォームごとに独立したコンプライアンス ポリシーが必要です。

1.  Intune で、**[デバイスのポリシー準拠]** > **[ポリシー]** > **[ポリシーの作成]** の順に選択します。
2.  **[名前]** に「**iOS compliance policy test**」と入力します。 
3.  **[説明]** に「**iOS compliance policy test**」と入力します。
4.  **[プラットフォーム]** で **[iOS]** を選択します。 
5.  **[設定]** > **[電子メール]** を選択します。 
     
    1.  **[モバイル デバイスは管理されているメール プロファイルを持つことが必要]** の隣の **[必要]** を選択します。
    2. **[OK]** を選択します。

    ![管理されたメール プロファイルを必要とするように電子メール コンプライアンス ポリシーを設定する](media/tutorial-protect-email-on-enrolled-devices/ios-compliance-policy-email.png)
    
6.  **[デバイスの正常性]** を選択します。 **[脱獄されたデバイス]** の隣の **[ブロックする]** を選択して、**[OK]** を選択します。
7.  **[システム セキュリティ]** を選択して、**[パスワード]** の設定を入力します。 このチュートリアルでは、次の推奨設定を選択します。
     
    - **[モバイル デバイスのロック解除にパスワードを必要とする]** で、**[必要]** を選択します。
    - **[単純なパスワード]** で、**[ブロックする]** を選択します。
    - **[パスワードの最小文字数]** に、「**4**」と入力します。
    - **[必要なパスワードの種類]** で、**[英数字]** を選択します。
    - **[画面ロック後にパスワードが要求されるまでの最長時間 (分)]** で、**[即時]** を選択します。
    - **[パスワードの有効期限 (日数)]** に、「**41**」と入力します。
    - **[再使用を禁止するパスワード世代数]** に、「**5**」と入力します。
 
    ![電子メール コンプライアンス ポリシーのパスワードの設定を設定する](media/tutorial-protect-email-on-enrolled-devices/ios-compliance-policy-system-security.png)

8.  **[OK]** を選択し、**[OK]** をもう一度選択します。
9.  **[作成]** を選択します。

## <a name="create-the-conditional-access-policy"></a>条件付きアクセス ポリシーを作成する
次に、すべてのデバイス プラットフォームに対し、Exchange Online にアクセスするためには、Intune に登録することと、Intune コンプライアンス ポリシーに準拠することを要求する、条件付きアクセス ポリシーを作成します。 また、メールへのアクセスには Outlook アプリを使用することも要求します。 条件付きアクセス ポリシーは、Azure AD ポータルまたは Intune ポータルのいずれかで構成できます。 既に Intune ポータルにいるので、ここでポリシーを作成します。
1.  Intune で、**[条件付きアクセス]** > **[ポリシー]** > **[新しいポリシー]** の順に選択します。
1.  **[名前]** に「**Test policy for Office 365 email**」と入力します。 
3.  **[割り当て]** で、**[ユーザーとグループ]** を選択します。 **[含む]** タブで **[すべてのユーザー]** を選択して、**[完了]** を選択します。

4.  **[割り当て]** で、**[クラウド アプリ]** を選択します。 Office 365 Exchange Online のメールを保護するので、次の手順で選択します。
     
    1. **[含む]** タブで、**[アプリを選択]** を選択します。
    2. **[選択]** を選択します。 
    3. アプリケーションの一覧で **Office 365 Exchange Online** を選択し、**[選択]** を選択します。 
    4. **[完了]** を選びます。
  
    ![Office 365 Exchange Online アプリを選択する](media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-cloud-apps.png)

5.  **[割り当て]** で、**[条件]** > **[デバイス プラットフォーム]** を選択します。
     
    1. **[構成]** で、**[はい]** を選択します。
    2. **[含む]** タブで **[任意のデバイス]** を選択してから、**[完了]** を選択します。 
    3. **[完了]** をもう一度選択します。
   
    ![Office 365 Exchange Online アプリを選択する](media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-cloud-device-platforms.png)

6.  **[割り当て]** で、**[条件]** > **[クライアント アプリ]** の順に選択します。
     
    1. **[構成]** で、**[はい]** を選択します。
    2. このチュートリアルでは、**[モバイル アプリとデスクトップ クライアント]** と **[先進認証クライアント]** (これは、Outlook for iOS や Outlook for Android のようなアプリを示します) を選択します。 他のチェック ボックスはすべてオフにします。
    3. **[完了]** を選択し、**[完了]** をもう一度選択します。
    
    ![Office 365 Exchange Online アプリを選択する](media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-client-apps.png)

7.  **[アクセス制御]** で **[許可]** を選択します。 
     
    1. **[許可]** ウィンドウで、**[アクセス権の付与]** を選択します。
    2. **[デバイスは準拠としてマーク済みである必要があります]** を選択します。 
    3. **[承認されたクライアント アプリが必要です]** を選択します。
    4. **[複数のコントロールの場合]** で、**[選択したコントロールすべてが必要]** を選択します。 この設定により、デバイスがメールへのアクセスを試みるときに、選択した両方の要件が適用されます。
    5. **[選択]** を選択します。
     
    ![Office 365 Exchange Online アプリを選択する](media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-grant-access.png)

8.  **[ポリシーを有効にする]** で、**[オン]** を選択します。
     
    ![Office 365 Exchange Online アプリを選択する](media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-enable-policy.png)

9.  **[作成]** を選択します。

## <a name="try-it-out"></a>試してみましょう
作成したポリシーでは、Office 365 のメールにサインインしようとするすべての iOS デバイスは、Intune に登録されていて、iOS 用 Outlook モバイル アプリを使用している必要があります。 iOS デバイスでこのシナリオをテストするには、テスト テナントのユーザーの資格情報を使用して、Exchange Online へのサインインを試みます。 デバイスを登録し、Outlook モバイル アプリをインストールするよう求めるメッセージが表示されます。
1. iPhone でテストするには、**[Settings]\(設定\)** > **[Passwords & Accounts]\(パスワードとアカウント\)** > **[Add Account]\(アカウントの追加\)** > **[Exchange]** に移動します。
2. テスト テナント内のユーザーのメール アドレスを入力し、**[次へ]** を選択します。
3. **[サインイン]** を選択します。
4. テスト ユーザーのパスワードを入力して、**[サインイン]** を選択します。
5. デバイスのリソース アクセスを管理する必要があるというメッセージと、登録のオプションが表示されます。 

## <a name="clean-up-resources"></a>リソースをクリーンアップする
テスト ポリシーが必要なくなった場合は削除できます。
1. グローバル管理者または Intune サービス管理者として [Intune](https://aka.ms/intuneportal) にサインインします。
2. **[デバイスのポリシー準拠]** > **[ポリシー]** の順に選択します。
3. **[ポリシー名]** ボックスの一覧で、お使いのテスト ポリシーのコンテキスト メニュー **[...]** を選択し、**[削除]** を選択します。 **[OK]** を選択して確定します。
4. **[条件付きアクセス]** > **[ポリシー]** の順に選択します。
5. **[ポリシー名]** ボックスの一覧で、お使いのテスト ポリシーのコンテキスト メニュー **[...]** を選択し、**[削除]** を選択します。 **[はい]** をクリックして操作を確定します。

 ## <a name="next-steps"></a>次の手順 
このチュートリアルでは、iOS デバイスに対して、Intune に登録することと、Outlook アプリを使用して Exchange Online のメールにアクセスすることを要求する、ポリシーを作成しました。 Exchange ActiveSync クライアントや Office 365 Exchange Online などの他のアプリやサービスを保護するために条件付きアクセスで Intune を使用する方法については、「[条件付きアクセスの設定](conditional-access.md)」をご覧ください。
