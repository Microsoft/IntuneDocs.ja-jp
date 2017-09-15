---
title: "Skycure アプリ、Microsoft Authenticator アプリ、iOS 構成ポリシーを展開する"
description: "Skycure アプリ、Microsoft Authenticator アプリ、iOS 構成ポリシーを Intune クラシック ポータルに展開します。"
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
ms.openlocfilehash: 6334686f350c54e11ef4ef5cbacf39a81e6a1a7e
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/09/2017
---
# <a name="deploy-skycure-apps-microsoft-authenticator-app-and-ios-app-configuration-policy"></a>Skycure アプリ、Microsoft Authenticator アプリ、iOS アプリ構成ポリシーの展開

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

## <a name="before-you-begin"></a>始める前に

-   [Intune クラシック ポータル](https://manage.microsoft.com/)で以下の手順を完了する必要があります。

-   Skycure 管理コンソールで以前に構成したものと同じ Azure AD アカウントを使います。これは、Intune クラシック ポータルにログインするためのものと同じアカウントにする必要があります。

-   次のプロセスをよく理解している必要があります。

    -   [Intune でアプリを展開する](/intune-classic/deploy-use/deploy-apps-in-microsoft-intune)。

    -   [iOS アプリ構成ポリシーを展開する](/intune-classic/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune)。

## <a name="to-deploy-skycure-apps-microsoft-authenticator-app-and-the-ios-app-configuration-policy"></a>Skycure アプリ、Microsoft Authenticator アプリ、iOS アプリ構成ポリシーを展開するには

1.  Intune クラシック ポータルで **[アプリ]** &gt; **[アプリ]** の順に選び、管理できるアプリの一覧を表示します。

2.  次のアプリを選択します。

    a.  Microsoft Authenticator

    b.  Android 向け Skycure アプリ

    c.  iOS 向け Skycure アプリ

       ![Intune クラシック ポータルの展開するすべてのアプリ](../media/mtp/skycure-deploy-app-1.png)

3.  **[展開の管理]** を選択し、Skycure ユーザーが含まれる Azure AD セキュリティ グループを選択し、**[次へ]** をクリックします。

4.  **[展開アクション]** ページで、**[承認]** ドロップダウン リストから **[必須のインストール]** オプションを選択し、**[次へ]** をクリックします。

    ![Intune クラシック ポータルの展開アクション](../media/mtp/skycure-deploy-app-2.png)

5.  **[VPN プロファイル]** ページで、**[VPN ポリシー]** ドロップダウン リストから **[なし]** オプションを選択し、**[次へ]** をクリックします。

6.  **[モバイル アプリ構成]** ページで、**[アプリ構成ポリシー]** ドロップダウン リストから、前に作成した iOS アプリ構成ポリシーを選択し、**[完了]** をクリックします。

    ![Intune クラシック ポータルのモバイル アプリ構成](../media/mtp/skycure-deploy-app-3.png)

## <a name="next-steps"></a>次のステップ

[Skycure と Intune の統合をセットアップする](/intune-classic/deploy-use/setup-the-skycure-integration-with-Intune)
