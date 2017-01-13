---
title: "デバイスに証明書がない | Microsoft Docs"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 01/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: df973b18-9166-417d-8aa3-49edd2bda256
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: arnab
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d6fcfac7c8bd469f5163ec9b4017ae8c3d486428
ms.openlocfilehash: e0aaa48e46e547d4853478fdbb80711700a9c22a

---

# <a name="your-android-device-is-missing-a-certificate-that-usually-comes-installed-on-your-phone"></a>電話に通常インストールされている証明書が Android デバイスにない

デバイスが Intune に登録されておらず、電話に通常インストールされる証明書がない場合は、ポータル サイト アプリにサインインすることはできません。 サインインしようとすると、次のメッセージが表示されます。

![screenshot-error-message-about-missing-certificate](./media/andr-cert_install-1-cert_missing.png)

この問題は、必要な証明書を [Digicert の証明書ページ](https://www.digicert.com/digicert-root-certificates.htm)から取得することで解決できます。

1. __Baltimore CyberTrust Root__ 証明書を見つけてダウンロードします。 直接[こちら](https://www.digicert.com/CACerts/BaltimoreCyberTrustRoot.crt)からダウンロードすることもできます。

2. 画面の上から下へドラッグして最近の通知の一覧を表示し、**[BaltimoreCyberTrustRoot.crt]** をタップします。

3. デバイスに**証明書の命名**を求めるメッセージが表示されます。 表示された既定の証明書名を変更しないでください。

4. **[認証情報の使用]** が **[VPN とアプリ]** に設定されていることを確認し、**[OK]** をタップします。

    ![screenshot-certificate-name-dialog-showing-baltimore-certificate-name](./media/andr-cert_install-2-add_cert_name.png)

5. ブラウザーとポータル サイト アプリを閉じます。

6. 会社のポータル アプリをもう一度開きます。 これで、会社のポータル アプリにサインインできるようになりました。 ポータル サイト アプリを使用できるようにならない場合は、[ポータル Web サイト](http://portal.manage.microsoft.com)に記載の情報を参考に、詳細な手順について IT 管理者にお問い合わせください。

>[!NOTE]
> この証明書をインストールしても問題が解決せず、別の "証明書が見つかりません" というメッセージが表示される場合は、[不足している証明書をインストールする](your-device-is-missing-an-IT-required-certificate-android.md)別の手順を実行する必要があります。

サポートが必要な場合は、 IT 管理者にお問い合わせください。 連絡先情報については、[ポータル サイト Web サイト](http://portal.manage.microsoft.com)をご確認ください。



<!--HONumber=Jan17_HO1-->


