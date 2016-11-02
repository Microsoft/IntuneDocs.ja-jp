---
title: "Windows 8.1 または Windows RT 8.1 デバイスを登録する | Microsoft Intune"
description: "Intune に Windows 8.1 または Windows RT 8.1 デバイスを登録する方法について説明します"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 09/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 28984f26-1070-4f7a-877c-669a59375c0c
ms.reviewer: priyar
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7eefcefa5e1cd0f789c77bf020c256e449099273
ms.openlocfilehash: 53e9313bc85c149960fa985b655a22065b55b8a0


---


# <a name="enroll-your-windows-81-or-windows-rt-81-device-in-intune"></a>Intune に Windows 8.1 または Windows RT 8.1 デバイスを登録する

職場または学校が Microsoft Intune を使用している場合は、お使いのデバイスを登録して、会社の電子メール、ファイル、またその他のリソースにアクセスできます。 デバイスを登録すると、組織は会社のデータをセキュリティで保護することができます。 登録の詳細については、「[ポータル サイト アプリをインストールし、Intune にデバイスを登録するとどうなるか](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-windows.md)」と「[What your IT administrator can and can't see on your device](what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows.md)」 (IT 管理者がお客様のデバイスに関して確認できる情報と確認できない情報) を参照してください。


Windows 8.1 または Windows RT 8.1 デバイスを登録するには、次の手順を実行します。

1.  デバイスで、**[設定]** &gt; **[PC 設定]** &gt; **[ネットワーク]** &gt; **[社内]** の順にタップします。

    ![nav-to-workplace](./media/W81-1-workplacejoin.png)

2.  必要に応じて、ユーザー ID に職場または学校のメール アドレスを入力し、**[参加]** をタップします。

    ユーザー ID が必要ない場合は、このデバイスへのサインイン時に入力した電子メール アドレスが使用されます。

3.  職場または学校の電子メールのパスワードを入力します。

    ![type-password](./media/W81-2-workplacesettings_signin.png)

4.  **[デバイスの管理をオンにする]** で、**[オンにする]** をタップします。

    ![turn-on-device-management](./media/W81-3-dev-mgt-turn-on.png)

5.  **[IT 管理者によるアプリやサービスの管理を許可する]** ダイアログ ボックスで、**[同意する]** チェック ボックスをオンにし、**[オンにする]** をタップします。

    ![turn-on-allow-apps-services](./media/W81-4-agree-allow-apps-services.png)

    登録に成功すると、次の画面が表示されます。

    ![enrollment-complete](./media/W81-5-enrolled-done.png)

さらに、ポータル サイト アプリをインストールすることもお勧めします。これにより、自分や自分の役割に関連する会社のアプリを簡単に識別して、取得できます。 会社での Intune のセットアップ方法に応じて、ポータル サイト アプリが登録プロセスの一部としてインストールされていることもあります。 アプリがあるかどうかを確認するには、アプリ一覧で、**[ポータル サイト]** を検索します。 アプリの一覧で、[ポータル サイト] が表示されない場合は、次の手順に従ってインストールします。

1.  **[スタート]** &gt; **[ストア]** をタップします。

2.  **[検索]** をタップし、「**ポータル サイト**」と入力します。

3.  結果の一覧で、**[ポータル サイト]** をタップします。

4.  **[インストール]** または **[無料]** をタップします。 表示されるオプションは、会社がどのようにアプリをセットアップしたかによって異なります。

サポートが必要な場合は、 IT 管理者にお問い合わせください。 連絡先情報については、[ポータル サイト Web サイト](http://portal.manage.microsoft.com)をご確認ください。



<!--HONumber=Oct16_HO2-->


