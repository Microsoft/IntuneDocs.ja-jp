---
title: "Intune 通信費管理サービスに iOS デバイスを登録する"
description: "通信費管理サービスに iOS デバイスを登録する方法について説明します。"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 04/19/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6d8c6372-f2ce-4558-8886-1d7c1966699c
searchScope: User help
ROBOTS: 
ms.reviewer: sumitp
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 13f284c62e1232a560ec9e5186de4055d616ef3a
ms.sourcegitcommit: f2f147a1177d1cf5bbc8001701eb8f44dd833b7d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/12/2017
---
# <a name="enroll-your-ios-device-in-telecom-expense-management"></a>通信費管理サービスに iOS デバイスを登録する

データおよび音声プランが許容範囲内で使用されていることを確認するために、通信費管理ソフトウェアを使用している組織もあります。 デバイスの登録後、そのデバイスに最適なカテゴリを選択するよう求められます。

  ![iOS デバイス上の "デバイスの最適なカテゴリの選択" 画面のスクリーンショット。 選択された企業または個人の登録が表示されています。](./media/ios-enroll-10-tem-select-best-category.png)

適切なオプションを選択すると、App Store から [__Datalert__](https://itunes.apple.com/app/datalert/id771029268?mt=8) アプリをインストールするように通知されます。 Datalert アプリを使用すると、組織のデータ使用量を測定できます。 組織で Microsoft の職場または学校の登録オプションが構成されている場合は、職場または学校のアカウントでログインする必要があります。 これが有効になっていない場合は、電話番号などの情報を入力し、コードを使用してデバイスを確認して、アプリから Datalert サービスに登録する必要があります。

  ![Datalert アプリの [ようこそ] 画面のスクリーンショット。Datalert でデータ プランを最大限に活用する方法に関する簡単な説明のあと、次の画面に移動するように求められます。](./media/ios-enroll-11-tem-datalert-setup.png)

## <a name="enroll-into-datalert-using-your-microsoft-work-or-school-account"></a>職場または学校の Microsoft アカウントを使用して Datalert に登録する

> [!NOTE]
> この方法で登録するには、お使いの電話に [Microsoft Authenticator](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) アプリがインストールされアクティブになっている必要があります。

1. __[Enroll with Microsoft account]\(Microsoft アカウントでの登録)__ を選択します。

  ![Datalert アプリの [設定] 画面の画像。画面の上半分ではデバイスを登録するための[電話番号] フィールドが提供され、Microsoft Office 365 アカウントと Intune サブスクリプションがある場合は、画面下部で "Microsoft アカウントでの登録" が提供されます。](./media/ios-enroll-11a-tem-datalert-enroll-msft-account.png)

2. __"Datalert" が "Authenticator" を開こうとしている__、という通知を受け取ります。 __[開く]__ を選択します。

  ![Datalert アプリの要求で認証アプリを開くことを求めるポップアップ画面のイメージ。](./media/ios-enroll-11b-tem-datalert-open-authenticator.png)

3. __Microsoft の学校または職場のアカウント__ でサインインします。 しばらくの間 Datalert セットアップが実行され、完了します。 完了したら __[完了]__ をタップします。

## <a name="enroll-into-datalert-using-your-phone-number"></a>電話番号を使用して Datalert に登録する

1. デバイスの電話番号を提供します。

  ![Datalert アプリが電話番号を要求している画面のスクリーンショット。](./media/ios-enroll-12-tem-datalert-phone-number.png)

2. 次に SMS メッセージで確認コードを受信します。 コードを入力して __[OK]__ をタップします。

  ![Datalert アプリが SMS 確認コードを要求している画面のスクリーンショット。](./media/ios-enroll-13-tem-datalert-sms.png)

3. 確認コードを入力すると、Datalert のセットアップが完了します。 __[完了]__ をタップすると、Datalert アプリからデータを監視できるようになります。

  ![Datalert アプリが当日分のデータ使用状況を監視している画面のスクリーンショット。](./media/ios-enroll-14-tem-datalert-monitoring-active.png)

登録が完了すると、Datalert アプリでデータ使用量が表示されるようになります。

サポートが必要な場合は、 社内サポートに問い合わせてください。 連絡先情報については、[ポータル サイト Web サイト](https://portal.manage.microsoft.com#HelpDeskDialog)をご確認ください。
