---
title: ポータル サイトで Intune に macOS デバイスを登録する | Microsoft Docs
description: ポータル サイト アプリを利用し、Intune に macOS デバイスを登録する方法について説明します
keywords: Mac OS X, macOS, OS X
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/11/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3bb659cc-9b57-4d19-8631-2c26749fa71c
searchScope:
- User help
ROBOTS: ''
ms.reviewer: elocholi
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 3dac9446d7a1097f5be4d0851cd78e8cbb86cc4e
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="enroll-your-macos-device-in-intune-with-the-company-portal-app"></a>ポータル サイト アプリで Intune に macOS デバイスを登録する

組織のアプリ、データ、リソースにアクセスできれば、業務の遂行が簡単になります。 組織は Intune を利用して[リソースへのアクセスを管理](what-happens-if-you-install-the-Company-Portal-app-and-enroll-your-device-in-intune-macos.md)しています。そのために、macOS 向けポータル サイト アプリをダウンロードする必要があります。 以下の指示は、OS X El Capitan 10.11 以降を搭載した macOS 向けです。


1. __Dock__ で __Safari__ を起動し、新しいウィンドウを開いてから、[会社のポータル Web サイト](https://portal.manage.microsoft.com)を開きます。

2. 職場や学校のアカウントで会社のポータル Web サイトにログインします。

   [!INCLUDE [wit_nextref](includes/end-user-password-guidance.md)]


3. ログインした後、ページの左上隅の **[メニュー]** をクリックして、**[デバイス]** を選びます。

   ![アプリをまだインストールできないことと、下に [デバイス] ボタンが示されている Web ポータルのランディング ページのスクリーンショット。](./media/macOS_enroll_001_landing_page.png)

4. __[デバイス]__ ページには、登録済みのデバイスのリスト、またはバナーのみが表示されます。 デバイスが既に登録されている場合や macOS などの場合は表示内容が異なります。 リストされていないデバイスを登録するには、[__If your device is listed, tap here to identify it.You can also tap here to enroll your device if it is not listed. (デバイスがリストに表示されている場合は、ここをタップして特定してください。リストに含まれていない場合は、ここをタップするとデバイスを登録できます)__] という内容のバナーを選択します。 登録済みデバイスがない場合は、バナーに **[登録されているデバイスはありません。ここをタップしてこのデバイスを登録してください。]** と表示されます。

    ![リスト表示されていないデバイスの登録または不明なデバイスの識別を求めるバナーの上に 2 つの不明なデバイスが示された、[デバイス] ページのスクリーンショット。](./media/macOS_enroll_002_tap_here_banner.png)

5. macOS デバイスにポータル サイト アプリをダウンロードして登録を続行します。

    ![ユーザーに macOS ポータル サイト アプリのダウンロードを求める通知。 この通知では、右下隅の [ダウンロード] ボタンの上に手順のテキストが示されます。](./media/macOS_enroll_IWP_CP_app_notice.png)

6. Mac で、ダウンロードした **CompanyPortal.pkg** が安全に開けることが確認されます。 インストーラーを開き、インストール プロセスを実行します。

7. インストーラーが完了したら、**[アプリケーション]** フォルダーまたは**スタート パッド**を開き、**ポータル サイト**を開きます。

8. **"CompanyPortal" がインターネットからダウンロードしたアプリケーションであることを伝え、これを開くかどうかを確認するメッセージ**が Mac に表示されます。 **[開く]** をクリックします。

   > [!NOTE]
   > Intune は、ユーザーのコンピューターにアクセスして、そのデバイスが組織のリソースにアクセスしても十分に安全であることを確認する必要があります。 ポータル サイト アプリの起動をコンピューターが拒否した場合、[Gatekeeper をオフに](https://support.apple.com/HT202491)してからアプリを開いてみてください。

9. ポータル サイト アプリの最初の画面で、ポータル Web サイトへのログインに使用したものと同じ職場または学校のアカウントで**サインイン**するように求められます。

10. ポータル サイトはアカウント情報を確認し、**デバイス登録**状況と**デバイス コンプライアンス**状況を表示します。 黄色の三角形が表示されますが、これは Mac を職場で使用しても問題がないことを確認するために行わなければならない措置を伝えるものです。 **[開始]** をクリックし、[デバイスを管理登録](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md)します。

11. Mac は管理登録を開始します。 この間、コンピューターのログイン情報を求められることがあります。 登録には数分かかる場合があります。 この間、コンピューターで他の作業を行っても構いません。 会社アクセス設定が完了すると、完了を知らせるメッセージが表示されます。

サポートが必要な場合は、 会社のサポートに問い合わせてください。 連絡先の情報は、[会社のポータル Web サイト](https://portal.manage.microsoft.com#HelpDeskDialog)でわかります。
