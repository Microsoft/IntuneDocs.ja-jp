---
title: "Skycure アプリ、Microsoft Authenticator アプリ、iOS 構成ポリシーの展開 | Microsoft Docs"
description: "Skycure アプリ、Microsoft Authenticator アプリ、iOS 構成ポリシーを Intune クラシック コンソールに展開します。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 45826fbc-6df5-41b2-8e80-d1353f904b43
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 86fd9d7212277f9524eb4d7f225df2c7beda1313
ms.openlocfilehash: 9f09a070ec120064bdd64bfb05a39ec9e484606c
ms.lasthandoff: 03/21/2017


---

# <a name="deploy-skycure-apps-microsoft-authenticator-app-and-ios-app-configuration-policy"></a>Skycure アプリ、Microsoft Authenticator アプリ、iOS アプリ構成ポリシーの展開

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

## <a name="before-you-begin"></a>始める前に

-   [Intune クラシック コンソール](https://manage.microsoft.com/)で以下の手順を完了する必要があります。

-   Skycure 管理コンソールで以前に構成したものと同じ Azure AD アカウントを使用します。これは、Intune クラシック コンソールにログインするためのものと同じアカウントにする必要があります。

-   次のプロセスをよく理解している必要があります。

    -   [Intune でアプリを展開する](https://docs.microsoft.com/intune/deploy-use/deploy-apps-in-microsoft-intune)。

    -   [iOS アプリ構成ポリシーを展開する](https://docs.microsoft.com/intune/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune)。

## <a name="to-deploy-skycure-apps-microsoft-authenticator-app-and-the-ios-app-configuration-policy"></a>Skycure アプリ、Microsoft Authenticator アプリ、iOS アプリ構成ポリシーを展開するには

1.  Intune のクラシック コンソールで **[アプリ]** &gt; **[アプリ]** の順に選択し、管理可能なアプリの一覧を表示します。

2.  次のアプリを選択します。

    a.  Microsoft Authenticator

    b.  Android 向け Skycure アプリ

    c.  iOS 向け Skycure アプリ

       ![Intune クラシック コンソールと展開するすべてのアプリ](../media/mtp/skycure-deploy-app-1.png)

3.  **[展開の管理]** を選択し、Skycure ユーザーが含まれる Azure AD セキュリティ グループを選択し、**[次へ]** をクリックします。

4.  **[展開アクション]** ページで、**[承認]** ドロップダウン リストから **[必須のインストール]** オプションを選択し、**[次へ]** をクリックします。

    ![Intune クラシック コンソールの展開アクション](../media/mtp/skycure-deploy-app-2.png)

5.  **[VPN プロファイル]** ページで、**[VPN ポリシー]** ドロップダウン リストから **[なし]** オプションを選択し、**[次へ]** をクリックします。

6.  **[モバイル アプリ構成]** ページで、**[アプリ構成ポリシー]** ドロップダウン リストから、前に作成した iOS アプリ構成ポリシーを選択し、**[完了]** をクリックします。

    ![Intune クラシック コンソールとモバイル アプリ構成](../media/mtp/skycure-deploy-app-3.png)

## <a name="next-steps"></a>次のステップ

[Skycure と Intune の統合をセットアップする](https://docs.microsoft.com/intune/deploy-use/setup-the-skycure-integration-with-Intune)

