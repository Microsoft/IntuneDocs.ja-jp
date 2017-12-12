---
title: "Intune 通信費管理サービスに Android デバイスを登録する"
description: "通信費管理サービスに Android デバイスを登録する方法について説明します。"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 04/19/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 26aa3698-7e4d-453a-8852-ab75e72b6485
searchScope: User help
ROBOTS: 
ms.reviewer: sumitp
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 4d8bf1304d0a7b1f007c85befa3565b519719dbd
ms.sourcegitcommit: f2f147a1177d1cf5bbc8001701eb8f44dd833b7d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/12/2017
---
# <a name="enroll-your-android-device-in-telecom-expense-management"></a>通信費管理サービスに Android デバイスを登録する

データおよび音声プランが許容範囲内で使用されていることを確認するために、通信費管理ソフトウェアを使用している組織もあります。 デバイスの登録後、そのデバイスに最適なカテゴリを選択するよう求められます。

![iOS デバイス上の "デバイスの最適なカテゴリの選択" 画面のスクリーンショット。 選択された企業または個人の登録が表示されています。](./media/and-enroll-11-tem-select-best-category.png)

適切なオプションを選択すると、Google Play Store の [__Datalert__](https://play.google.com/store/apps/details?id=fr.memobox.databox) アプリをインストールするように通知されます。 Datalert アプリを使用すると、組織のデータ使用量を測定できます。 組織で職場または学校の登録オプションが構成されている場合は、職場または学校のアカウントを使用してログインする必要があります。 これが有効になっていない場合は、電話番号などの情報を入力し、コードを使用してデバイスを確認して、アプリから Datalert サービスに登録する必要があります。

画面の右上隅にある __[次へ]__ の矢印をタップして進みます。 会社のサポートから、__職場または学校の Microsoft アカウント__、または__電話番号__のいずれかを使用してサインインするように指示されます。

  ![Datalert アプリの [ようこそ] 画面のスクリーンショット。Datalert でデータ プランを最大限に活用する方法に関する簡単な説明のあと、次の画面に移動するように求められます。](./media/and-enroll-12-tem-datalert-setup.png)

## <a name="enroll-into-datalert-using-your-microsoft-work-or-school-account"></a>職場または学校の Microsoft アカウントを使用して Datalert に登録する

1. __[Enroll with Microsoft account]\(Microsoft アカウントでの登録)__ を選択します。

  ![Datalert アプリの [設定] 画面の画像。Microsoft Office 365 アカウントと Intune サブスクリプションがある場合は、画面の上半分でデバイスを登録するための [電話番号] フィールドが提供され、画面の下半分で "Microsoft アカウントでの登録" が提供されます。](./media/and-enroll-12a-tem-datalert-enroll-msft-account.png)

2. 利用可能なアカウントから職場または学校のアカウントを選択します。 自分のアカウントが一覧にない場合は、**[アカウントの追加]** ボタンを使用してアカウントにサインインできます。

  ![サンプル アカウントと [アカウントの追加] ボタンを示す "アカウントの選択" 画面のスクリーンショット。](./media/and-enroll-12b-tem-datalert-enroll-select-msft-account.png)

3. しばらくの間 Datalert セットアップが実行され、完了します。 完了したら __[完了]__ をタップします。

## <a name="enroll-into-datalert-using-your-phone-number"></a>電話番号を使用して Datalert に登録する

1. デバイスの電話番号を提供します。

  ![Datalert アプリが電話番号を要求している画面のスクリーンショット。](./media/and-enroll-13-tem-datalert-phone-number.png)

2. 次に SMS メッセージで確認コードを受信します。 コードを入力して __[OK]__ をタップします。

  ![Datalert アプリが SMS 確認コードを要求している画面のスクリーンショット。](./media/and-enroll-14-tem-datalert-sms.png)

3. 確認コードを入力すると、Datalert のセットアップが完了します。 __[完了]__ をタップすると、Datalert アプリからデータを監視できるようになります。

  ![Datalert アプリが当日分のデータ使用状況を監視している画面のスクリーンショット。](./media/and-enroll-15-tem-datalert-monitoring-active.png)

登録が完了すると、Datalert アプリでデータ使用量が表示されるようになります。

サポートが必要な場合は、 社内サポートに問い合わせてください。 連絡先情報については、[ポータル サイト Web サイト](https://portal.manage.microsoft.com#HelpDeskDialog)をご確認ください。
