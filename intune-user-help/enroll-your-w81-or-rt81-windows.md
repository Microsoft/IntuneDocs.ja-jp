---
title: "Windows 8.1 または Windows RT 8.1 デバイスを登録する方法 | Microsoft Docs"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 01/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 28984f26-1070-4f7a-877c-669a59375c0c
searchScope: User help
ROBOTS: 
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: f3b5a93d204926e476ff5c001a4b597c74929ec0
ms.sourcegitcommit: f2f147a1177d1cf5bbc8001701eb8f44dd833b7d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/12/2017
---
# <a name="how-to-enroll-your-windows-81-or-windows-rt-81-device-in-intune"></a>Intune に Windows 8.1 または Windows RT 8.1 デバイスを登録する方法

職場または学校が Microsoft Intune を使用している場合は、お使いのデバイスを登録して、会社の電子メール、ファイル、またその他のリソースにアクセスできます。 デバイスを登録すると、組織は会社のデータをセキュリティで保護することができます。 登録の詳細については、「[ポータル サイト アプリをインストールし、Intune にデバイスを登録するとどうなるか](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-windows.md)」と[会社のサポートがユーザーのデバイスに関して確認できる情報と確認できない情報](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md)に関するページを参照してください。


Windows 8.1 または Windows RT 8.1 デバイスを登録するには、次の手順を実行します。

1.  デバイスで、**[設定]** &gt; **[PC 設定]** &gt; **[ネットワーク]** &gt; **[社内]** の順にタップします。

    ![nav-to-workplace](./media/W81-1-workplacejoin.png)

2.  必要に応じて、ユーザー ID に職場または学校のメール アドレスを入力し、**[参加]** をタップします。

    ユーザー ID が必要ない場合は、このデバイスへのサインイン時に入力した電子メール アドレスが使用されます。

3.  職場または学校の電子メールのパスワードを入力します。

    ![type-password](./media/W81-2-workplacesettings_signin.png)

4.  **[デバイスの管理をオンにする]** で、**[オンにする]** をタップします。

    ![turn-on-device-management](./media/W81-3-dev-mgt-turn-on.png)

5.  **[Allow apps and services from company support]\(会社のサポートによるアプリやサービスの管理を許可する\)** ダイアログ ボックスで、**[同意する]** チェック ボックスをオンにし、**[オンにする]** をタップします。

    ![turn-on-allow-apps-services](./media/W81-4-agree-allow-apps-services.png)

    登録に成功すると、次の画面が表示されます。

    ![enrollment-complete](./media/W81-5-enrolled-done.png)

さらに、ポータル サイト アプリをインストールすることもお勧めします。これにより、自分や自分の役割に関連する会社のアプリを簡単に識別して、取得できます。 会社での Intune のセットアップ方法に応じて、ポータル サイト アプリが登録プロセスの一部としてインストールされていることもあります。 アプリがあるかどうかを確認するには、アプリ一覧で、**[ポータル サイト]** を検索します。 アプリの一覧で、[ポータル サイト] が表示されない場合は、次の手順に従ってインストールします。

1.  **[スタート]** &gt; **[ストア]** をタップします。

2.  **[検索]** をタップし、「**ポータル サイト**」と入力します。

3.  結果の一覧で、**[ポータル サイト]** をタップします。

4.  **[インストール]** または **[無料]** をタップします。 表示されるオプションは、会社がどのようにアプリをセットアップしたかによって異なります。

サポートが必要な場合は、 社内サポートに問い合わせてください。 連絡先情報については、[ポータル サイト Web サイト](https://portal.manage.microsoft.com#HelpDeskDialog)をご確認ください。
