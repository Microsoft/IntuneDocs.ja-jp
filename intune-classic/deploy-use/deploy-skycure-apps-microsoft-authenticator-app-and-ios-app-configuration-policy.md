---
title: "Skycure アプリ、Microsoft Authenticator アプリ、iOS 構成ポリシーを展開する"
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
ms.openlocfilehash: 60f4ab5a656a2e253d82971d7bea6b3a6c9eb25a
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2017
---
# <a name="deploy-skycure-apps-microsoft-authenticator-app-and-ios-app-configuration-policy"></a>Skycure アプリ、Microsoft Authenticator アプリ、iOS アプリ構成ポリシーの展開

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

## <a name="before-you-begin"></a>始める前に

-   [Intune クラシック コンソール](https://manage.microsoft.com/)で以下の手順を完了する必要があります。

-   Skycure 管理コンソールで以前に構成したものと同じ Azure AD アカウントを使用します。これは、Intune クラシック コンソールにログインするためのものと同じアカウントにする必要があります。

-   次のプロセスをよく理解している必要があります。

    -   [Intune でアプリを展開する](/intune-classic/deploy-use/deploy-apps-in-microsoft-intune)。

    -   [iOS アプリ構成ポリシーを展開する](/intune-classic/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune)。

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

[Skycure と Intune の統合をセットアップする](/intune-classic/deploy-use/setup-the-skycure-integration-with-Intune)
