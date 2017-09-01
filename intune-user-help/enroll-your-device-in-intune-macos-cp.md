---
title: "ポータル サイトで Intune に macOS デバイスを登録する | Microsoft Docs"
description: "ポータル サイト アプリを利用し、Intune に macOS デバイスを登録する方法について説明します"
keywords: Mac OS X, macOS, OS X
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 08/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3bb659cc-9b57-4d19-8631-2c26749fa71c
searchScope: User help
ROBOTS: 
ms.reviewer: elocholi
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 1b177b05f065f66deb8c60be768c123fc7991937
ms.sourcegitcommit: 091f7b34f1fbf73db2bed5b46d92a78ba0dad1e4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/23/2017
---
# <a name="enroll-your-macos-device-in-intune-with-the-company-portal-app"></a>ポータル サイト アプリで Intune に macOS デバイスを登録する

[!INCLUDE[macos-preview-1708](./includes/macos-preview-1708.md)]

組織のアプリ、データ、リソースにアクセスできれば、業務の遂行が簡単になります。 組織は Intune を利用して[リソースへのアクセスを管理](what-happens-if-you-install-the-Company-Portal-app-and-enroll-your-device-in-intune-ios.md)しています。そのために、macOS 向けポータル サイト アプリをダウンロードする必要があります。 以下の指示は、OS X El Capitan 10.11 以降を搭載した macOS 向けです。

  > [!NOTE]
  > iPhone や iPad などの iOS デバイスを登録する場合、[代わりにこちらの説明をご覧ください](enroll-your-device-in-intune-ios.md)。

1. __Dock__ で __Safari__ を見つけ、[Microsoft ダウンロード センター](https://www.microsoft.com/download/details.aspx?id=55770) ページを開き、macOS 向けポータル サイト アプリを探します。

2. アプリをダウンロードします。 ダウンロードした **CompanyPortal.dmg** は安全に開けることを Mac が確認します。 **[ダウンロード]** フォルダーから開いたら、**[アプリケーション]** フォルダーに**ポータル サイト** アプリをドラッグします。

3. **[アプリケーション]** フォルダーまたは**スタート パッド**を開き、**ポータル サイト**を開きます。

4. **"CompanyPortal" がインターネットからダウンロードしたアプリケーションであることを伝え、これを開くかどうかを確認するメッセージ**が Mac に表示されます。 **[開く]** をクリックします。

  > [!NOTE]
  > Intune は、ユーザーのコンピューターにアクセスして、そのデバイスが組織のリソースにアクセスしても十分に安全であることを確認する必要があります。 ポータル サイト アプリの起動をコンピューターが拒否した場合、[Gatekeeper をオフに](https://support.apple.com/HT202491)してからアプリを開いてみてください。

6. ポータル サイト アプリの最初の画面で、ポータル Web サイトへのログインに使用したものと同じ職場または学校のアカウントで**サインイン**するように求められます。

7. ポータル サイトはアカウント情報を確認し、**デバイス登録**状況と**デバイス コンプライアンス**状況を表示します。 黄色の三角形が表示されますが、これは Mac を職場で使用しても問題がないことを確認するために行わなければならない措置を伝えるものです。 **[開始]** をクリックし、[デバイスを管理登録](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md)します。

8. Mac は管理登録を開始します。 この間、コンピューターのログイン情報を求められることがあります。 登録には数分かかる場合があります。 この間、コンピューターで他の作業を行っても構いません。 会社アクセス設定が完了すると、完了を知らせるメッセージが表示されます。

サポートが必要な場合は、 IT 管理者に問い合わせてください。 連絡先の情報は、[会社のポータル Web サイト](http://portal.manage.microsoft.com)でわかります。
