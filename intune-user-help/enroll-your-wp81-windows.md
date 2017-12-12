---
title: "Intune に Windows Phone 8.1 デバイスを登録する | Microsoft Docs"
description: "Intune に Windows Phone 8.1 デバイスを登録する方法について説明します"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 01/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4a120c3d-d520-4d48-ae4c-3338ca4e7bde
searchScope: User help
ROBOTS: 
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 30980072cfb1c98ab7755206b24497a356ebfff3
ms.sourcegitcommit: f2f147a1177d1cf5bbc8001701eb8f44dd833b7d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/12/2017
---
# <a name="enroll-your-windows-phone-81-device-in-intune"></a>Intune に Windows Phone 8.1 デバイスを登録する

職場または学校が Microsoft Intune を使用している場合は、お使いのデバイスを登録して、会社の電子メール、ファイル、またその他のリソースにアクセスできます。 デバイスを登録すると、組織は会社のデータをセキュリティで保護することができます。 登録の詳細については、「[ポータル サイト アプリをインストールし、Intune にデバイスを登録するとどうなるか](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-windows.md)」と[会社のサポートがユーザーのデバイスに関して確認できる情報と確認できない情報](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md)に関するページを参照してください。


Intune に Phone 8.1 デバイスを登録するには、自分の職場または学校に当てはまる手順に従ってください。

-   [会社で Microsoft ストアからポータル サイトを使用できるようにする場合](#if-your-company-lets-you-use-the-company-portal-from-the-windows-store)

-   [Windows Phone から Microsoft ストアへのアクセスが許可されていない場合、または Microsoft アカウントを所有していない場合](#if-you-are-not-allowed-to-access-the-windows-store-from-your-windows-phone-or-if-you-do-not-have-a-microsoft-account)

## <a name="if-your-company-lets-you-use-the-company-portal-from-the-microsoft-store"></a>会社で Microsoft ストアからポータル サイトを使用できる場合
ポータル サイト アプリをデバイスにインストールします。

1.  **[スタート]** &gt; **[ストア]** をタップします。

2.  **[検索]** をタップし、「**ポータル サイト**」と入力します。

3.  結果の一覧で、**[ポータル サイト]** をタップします。

    ![会社のポータルの検索結果](./media/WP81-1-CP-search-store-v2.png)

4.  **[ポータル サイト]** &gt; **[インストール]** を順にタップします。

    ![ポータル サイトのインストール](./media/WP81-2-CP-install-v2.png)

デバイスを登録するには、次の手順を実行します。

1.  デバイスで、**Microsoft Intune ポータル サイト** アプリを開きます。

2.  資格情報を入力します。 会社の使用条件に同意するように求められる場合があります。

3.  **[マイ デバイス]** までスワイプします。

4.  **[このデバイスを登録または特定するには、タップしてください]** をタップします。

    ![[このデバイスを登録または特定するには、タップしてください] 画面](./media/WP81-enroll-1-swipe-my-devices.png)

5.  **[このデバイスの登録]** をタップします。

    ![[このデバイスの登録] 画面](./media/WP81-enroll-2-enroll-this-device.png)

6.  **[アカウントの追加]** をタップします。

    ![[ワークプレース] 設定画面](./media/WP81-enroll-3-workplace-add-acct.png)

7.  要求された追加情報を入力し、**[サインイン]** をタップして、登録を完了します。 **[設定]** &gt; **[ワークプレース]** ページに社内アカウントが表示されているはずです。

    ![追加されたアカウントの画面](./media/WP81-enroll-4-account-added.png)

## <a name="if-you-are-not-allowed-to-access-the-microsoft-store-from-your-windows-phone-or-if-you-do-not-have-a-microsoft-account"></a>Windows Phone から Microsoft ストアへのアクセスが許可されていない場合、または Microsoft アカウントを所有していない場合

1.  **[設定]** &gt; **[社内]** の順にタップします。

2.  **[アカウントの追加]** をタップし、仕事用アカウントを使用してサインインします。

3.  要求された追加情報を入力し、**[サインイン]** をタップして、登録を完了します。

4.  会社のアプリまたはハブをインストールするように求められたら、関連するボックスがオンになっていることを確認し、**[完了]** をタップします。

会社のサポートによって、登録時に Intune ポータル サイトがインストールされるようにセットアップされている場合は、その Intune ポータル サイトがアプリの一覧に表示されることがわかります。

サポートが必要な場合は、 社内サポートに問い合わせてください。 連絡先情報については、[ポータル サイト Web サイト](https://portal.manage.microsoft.com#HelpDeskDialog)をご確認ください。
