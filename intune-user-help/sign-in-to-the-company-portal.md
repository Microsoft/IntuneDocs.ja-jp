---
title: ポータル サイト アプリにサインインする方法 | Microsoft Docs
description: 複数のプラットフォームでポータル サイト アプリにサインインする方法を確認します。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 09/18/2019
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
ms.collection: M365-identity-device-management
ms.openlocfilehash: 16d7142e6dc38a177f8820f60e7335b8b23a1eeb
ms.sourcegitcommit: 8934b1abec96e18cee15a77107d37551766f7666
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2019
ms.locfileid: "71099795"
---
# <a name="sign-in-to-company-portal"></a>ポータルサイトにサインインします  

ポータルサイトアプリにサインインするには、次の3つの方法があります。

* 仕事用メール アドレスとパスワードを使ってサインインする。  
* 証明書ベースの認証を使ってサインインする。  
* 別のデバイスからサインインする。    


## <a name="sign-in-with-your-email-address-and-password"></a>メール アドレスとパスワードを使ったサインイン
次の手順では、iOS 用のポータルサイトのスクリーンショットを示します。  

1. デバイスでアプリを開き、 **[サインイン]** をタップします。  

   [![ポータルサイトサインインページのスクリーンショットの例。](/intune-user-help/media/intune-ios-cp-signin-1908.png)](/intune-user-help/media/intune-ios-cp-signin-lightbox-1908.png#lightbox)  


2. **職場または学校のアカウント**を入力して、 **[次へ]** をタップします。

   ![画面は同じですが電子メールとパスワードではなく、電子メールのみを入力するように要求されます。](/intune-user-help/media/cp_ios_aad_signin_after_1804_002.png)

3. パスワードを入力し、 **[サインイン]** をタップします。

   ![電子メールが承認されると、パスワードの入力が要求されます。](/intune-user-help/media/cp_ios_aad_signin_after_1804_003.png)

4. アプリによって資格情報が検証されます。 完了すると、組織のリソースにアクセスして、利用可能なアプリをインストールできます。  

   ![認証プロセスが終了すると、ポータル サイト アプリでサインインが行われ、読み込みバーが表示されます。](/intune-user-help/media/cp_ios_aad_signin_after_1804_004.png)

## <a name="sign-in-with-certificate-based-authentication"></a>証明書ベースの認証を使ってサインインする

1. デバイス上でポータル サイト アプリを開きます。  

2. **職場または学校アカウント**を入力します。  

3. **[Sign in with a certificate]\(証明書を使用してサインイン\)** をタップします。  

4. **[続行]** をタップして証明書を使用します。  

## <a name="sign-in-from-another-device"></a>別のデバイスからサインインする

会社がスマートカードを使用してコンピューターにアクセスしている場合は、別のデバイスからサインインすることで認証が必要になる可能性があります。  

1. デバイス上でポータル サイト アプリを開きます。 職場のリソースにアクセスするために使用するデバイスであることを確認します。       

1. **[別のデバイスからサインインする]** を選択します。  

   ![ポータル サイトのサインイン ページで、メール アドレスの入力がユーザーに求められます。  [次へ] ボタンと [別のデバイスからサインインする] リンクが表示されます。 "アカウントにアクセスできない場合" のリンクもあります。 下部にあるリンクから Microsoft のプライバシーと Cookie に関する情報にアクセスできます。](/intune-user-help/media/cp_ios_aad_signin_after_1804_005.png)

2. ポータル サイトにサインインするための、一意のワンタイム コードを受け取ります。 コードをコピーします。

   ![会社のコンピューターから固有のパスワードで https://microsoft.com/devicelogin ページにアクセスし、コードを使用してサインインするように指示されます。](/intune-user-help/media/cp_ios_aad_signin_after_1804_006.png)

3. 他のデバイス (認証に使用しているデバイス) で、ブラウザーを開き、に[https://microsoft.com/devicelogin](https://microsoft.com/devicelogin)アクセスします。 コードを入力するか、貼り付けます。  

   ![ポータル サイト アプリの画像ではなく会社のコンピューターのブラウザーの画像です。 [デバイス ログイン] ページが表示され、ポータル サイト アプリで取得したコードを入力するように要求されます。](/intune/media/cp_ios_aad_signin_from_another_device_after_1704_004.png)

4. [__続行__] を選択して、ポータルサイトが職場のデバイスにサインインできるようにします。   

   ![固有のコードをフィールドに入力すると、[デバイス ログイン] サイトから、Intune ポータル サイトがサインインを許可してよい適切なアプリであることを確認されます。](/intune/media/cp_ios_aad_signin_from_another_device_after_1704_005.png)

5. コードが確認されたら、ウィンドウを閉じることができます。  

   ![デバイスでポータル サイト アプリへのログインが完了したことと、このページを閉じることができることを示す確認ページ。](/intune/media/cp_ios_aad_signin_from_another_device_after_1704_006.png)

6. ポータルサイトアプリが仕事用デバイスにサインインします。  

   ![認証プロセスが終了すると、ポータル サイト アプリはサインインを行い、進捗を示す読み込みバーが表示されます。](/intune-user-help/media/cp_ios_aad_signin_after_1804_007.png)

サポートが必要な場合は、 社内サポートに問い合わせてください。 連絡先情報については、[ポータル サイト Web サイト](https://go.microsoft.com/fwlink/?linkid=2010980)をご確認ください。  
