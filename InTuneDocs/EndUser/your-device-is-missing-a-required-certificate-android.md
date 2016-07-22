---
title: "デバイスに必要な証明書がない | Microsoft Intune"
description: 
keywords: 
author: staciebarker
manager: jeffgilb
ms.date: 05/31/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9081b1d8-50e8-4bc2-ba37-766421364213
ms.reviewer: arnab
ms.suite: ems
ms.sourcegitcommit: 0bb435b87c937ea118a0794c8332b9a8f268d36e
ms.openlocfilehash: 6e887d226228d073dc136b50ba9320ada996a6cd


---


# デバイスに必要な証明書がない
Android デバイスが Intune に登録されておらず、電話に通常インストールされる証明書がない場合は、Android ポータル サイト アプリにサインインすることはできません。 サインインしようとすると、次のメッセージが表示されます。

![andr-cert-install-cert-missing](./media/andr-cert_install-1-cert_missing.png)

この問題を解決し、必要な証明書を取得するには:

1.  ブラウザーで、この [Digicert 証明書ページ](https://www.digicert.com/digicert-root-certificates.htm)に移動します。

2.  Baltimore CyberTrust Root 証明書を検索してダウンロードします (https://www.digicert.com/CACerts/BaltimoreCyberTrustRoot.crt)。

3.  上から下へドラッグして、通知を開き、通知の一覧で **[BaltimoreCyberTrustRoot.crt]** をタップします。

4.  **[証明書の名前指定]** ダイアログで、既定の証明書名を受け入れます。

5. **[認証情報の使用]** が **[VPN とアプリ]** に設定されていることを確認し、**[OK]** をタップします。

    ![andr-cert-install-add-cert-name](./media/andr-cert_install-2-add_cert_name.png)

6. Web ブラウザーと会社のポータル アプリを閉じます。

7. 会社のポータル アプリをもう一度開きます。 これで、会社のポータル アプリにサインインできるようになりました。 サポートが必要な場合は、IT 管理者に問い合わせてください。

サポートが必要な場合は、 IT 管理者にお問い合わせください。 連絡先情報については、[ポータル サイト Web サイト](http://portal.manage.microsoft.com)をご確認ください。


<!--HONumber=Jun16_HO4-->


