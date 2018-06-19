---
title: ポータル サイト アプリにサインインする方法 | Microsoft Docs
description: 複数のプラットフォームでポータル サイト アプリにサインインする方法を確認します。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: cfd214bc-f072-4808-af2e-a3cbf7af9bca
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 84f8e70d8321ca27d689d13472b69007a1d6c186
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31019230"
---
# <a name="how-do-i-sign-in-to-the-company-portal-app---user-story-1132123--"></a>ポータル サイト アプリにサインインするには <!--User Story 1132123-->

電子メールやビジネス アプリなどの会社のリソースにアクセスする場合、ポータル サイト アプリを使用します。 ポータル サイトにサインインする方法は主に 2 つあります。

* 会社の電子メール アドレスとパスワードを使用する
* 別のデバイスからサインインする

次の画像は iOS のものですが、Android や Windows デバイスでもプロセスはほとんど同じです。

## <a name="signing-in-with-your-email-address-and-password"></a>電子メール アドレスとパスワードを使用したサインイン

1. お使いのデバイスでポータル サイト アプリを開いて、**[サインイン]** をタップします。

   ![Web サイトのイメージ図の前にユーザーのアイコンが表示されたポータル サイトのサインイン ページ。 下に "Get access to company resources and keep them secure"\(会社のリソースへのアクセスを取得し、セキュリティで保護する\) というテキストと "サインイン" ボタンがあります。 下部にあるリンクから Microsoft のプライバシーと Cookie に関する情報にアクセスできます。](/intune-user-help/media/cp_ios_aad_signin_after_1804_001.png)

   ポータル サイト アプリがない場合は、 [iOS](install-and-sign-in-to-the-intune-company-portal-app-ios.md) または [Android](install-the-company-portal-app-android.md) でのインストールおよびダウンロード方法を確認してください。

2. **職場または学校のアカウント**を入力して、**[次へ]** をタップします。

   ![画面は同じですが電子メールとパスワードではなく、電子メールのみを入力するように要求されます。](/intune-user-help/media/cp_ios_aad_signin_after_1804_002.png)

3. パスワードを入力し、**[サインイン]** をタップします。

   ![電子メールが承認されると、パスワードの入力が要求されます。](/intune-user-help/media/cp_ios_aad_signin_after_1804_003.png)

4. ポータル サイトでログインが承認されたら、サインインし、会社のリソースにアクセスできるようになります。   

   ![認証プロセスが終了すると、ポータル サイト アプリはサインインを行い、読み込みバーが表示されます。](/intune-user-help/media/cp_ios_aad_signin_after_1804_004.png)

## <a name="signing-in-with-certificate-based-authentication"></a>証明書ベースの認証によるサインイン

1.  デバイス上でポータル サイト アプリを開きます。

2.  **職場または学校アカウント**を入力します。

3.  **[Sign in with a certificate]\(証明書を使用してサインイン\)** をタップします。

4.  **[続行]** をタップして証明書を使用します。

## <a name="signing-in-from-another-device"></a>別のデバイスからサインインする

会社のリソースへのサインインにパスワードを使用しない場合は、適切なアクセス レベルを持つ適切なユーザーであることを確認するために別のデバイスを使用することができます。 会社がコンピューターへのアクセスにスマートカードを使用している場合は、別のデバイスを使用してサインインしなければならない可能性があります。

1. 電子メール アドレスを入力する代わりに、電子メールのテキスト ボックスの下にある **[別のデバイスからサインインする]** を選択します。

   ![ポータル サイトのサインイン ページで、メール アドレスの入力がユーザーに求められます。  下に "次へ" ボタンと "別のデバイスからサインインする" のリンクがあります。 "アカウントにアクセスできない場合" のリンクもあります。 下部にあるリンクから Microsoft のプライバシーと Cookie に関する情報にアクセスできます。](/intune-user-help/media/cp_ios_aad_signin_after_1804_005.png)

2. ポータル サイトにサインインするための、一意のワンタイム コードを受け取ります。

   ![会社のコンピューターから固有のパスワードで https://microsoft.com/devicelogin ページにアクセスし、コードを使用してサインインするように指示されます。](/intune-user-help/media/cp_ios_aad_signin_after_1804_006.png)

3. 他のデバイスでブラウザーを開き、[https://microsoft.com/devicelogin](https://microsoft.com/devicelogin) に移動し、コードを入力します。

   ![ポータル サイト アプリの画像ではなく会社のコンピューターのブラウザーの画像です。 [デバイス ログイン] ページが表示され、ポータル サイト アプリで取得したコードを入力するように要求されます。](/intune/media/cp_ios_aad_signin_from_another_device_after_1704_004.png)

4. **[デバイス ログイン]** ページでコードが確認されたら、__[続行]__ を選択して、別のデバイスでのポータル サイトのサインインを許可します。

   ![固有のコードをフィールドに入力すると、[デバイス ログイン] サイトから、Intune ポータル サイトがサインインを許可してよい適切なアプリであることを確認されます。](/intune/media/cp_ios_aad_signin_from_another_device_after_1704_005.png)

5. コードが確認されたら、ウィンドウを閉じることができます。

   ![デバイスでポータル サイト アプリへのログインが完了したことと、このページを閉じることができることを示す確認ページ。](/intune/media/cp_ios_aad_signin_from_another_device_after_1704_006.png)

6. 元のデバイスで、ポータル サイト アプリのサインインが開始します。

   ![認証プロセスが終了すると、ポータル サイト アプリはサインインを行い、進捗を示す読み込みバーが表示されます。](/intune-user-help/media/cp_ios_aad_signin_after_1804_007.png)

サポートが必要な場合は、 社内サポートに問い合わせてください。 連絡先情報については、[ポータル サイト Web サイト](https://portal.manage.microsoft.com#HelpDeskDialog)をご確認ください。
