---
title: "Skycure アプリ、Microsoft Authenticator アプリ、iOS 構成ポリシーの追加"
description: "Skycure アプリ、Microsoft Authenticator アプリ、iOS 構成ポリシーを Intune クラシック コンソールに追加します。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 018d26f4-4a75-4e27-bb04-54f54106cb2f
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: 425b86e92281bb6e3657a6c806be269ccae94311
ms.contentlocale: ja-jp
ms.lasthandoff: 06/08/2017


---

# <a name="add-skycure-apps-microsoft-authenticator-app-and-ios-configuration-policy"></a>Skycure アプリ、Microsoft Authenticator アプリ、iOS 構成ポリシーの追加

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

脅威がモバイル デバイスで特定されたときにエンドユーザーが通知を受け取れるように、また、脅威を除去するための手引きが受けられるように、Intune を利用して Skycure アプリを追加して展開する必要があります。

また、[Microsoft Authenticator](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) と iOS アプリ構成ポリシーが必要になります。Microsoft Authenticator を使用すると、Azure AD によってユーザーの ID の確認が行われます。iOS アプリ構成ポリシーは、Intune と Azure AD のシングル サインオン (SSO) を使用するように Skycure iOS アプリに信号を送るため、ユーザーは Skycure アプリにログインするたびにユーザー名とパスワードを入力する必要がありません。

## <a name="before-you-begin"></a>始める前に

-   [Intune クラシック コンソール](https://manage.microsoft.com/)で以下の手順を完了する必要があります。

-   Skycure 管理コンソールで以前に構成したものと同じ Azure AD アカウントを使用します。これは、Intune クラシック コンソールにログインするためのものと同じアカウントにする必要があります。

-   Skycure 統合ファイルを利用できる状態にしておく必要があります。 これは以前、Skycure 管理コンソールからダウンロードしておいた .zip ファイルです。**skycure\_configuration.plist** というファイルと iOS アプリ構成ポリシー パラメーターが含まれています。

-   次のプロセスをよく理解している必要があります。

    -   [Intune にアプリを追加する](/intune-classic/deploy-use/add-apps)。

    -   [iOS アプリ構成ポリシーを Intune に追加する](/intune-classic/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune)。

## <a name="to-add-the-skycure-app-for-android"></a>Android 向け Skycure アプリを追加するには

1.  Intune クラシック コンソールで、**[アプリ]** &gt; **[アプリの追加]** の順に選択して Intune ソフトウェア パブリッシャーを起動し、**[次へ]** をクリックします。

2.  **[ソフトウェア セットアップ]** ページで **[外部リンク]** を選択し、**[URL の指定]** に [Android 向け Skycure アプリの URL](https://play.google.com/store/apps/details?id=com.skycure.skycure) を貼り付けます。

    ![Intune ソフトウェア パブリッシャーの [URL の指定]](../media/mtp/skycure-add-apps-1.png)

3.  **[ソフトウェアの説明]** ページの **[発行元]**、**[名前]**、**[説明]** に入力し、**[このアプリをポータル サイトでおすすめアプリとして強調表示します]** オプションを選択し、**[次へ]** をクリックします。

    ![Intune ソフトウェア パブリッシャーの [ソフトウェアの説明]](../media/mtp/skycure-add-apps-2.png)

4.  **[アップロード]** をクリックし、**[閉じる]** をクリックします。

## <a name="to-add-the-skycure-app-for-ios"></a>iOS 向け Skycure アプリを追加するには

1.  Intune クラシック コンソールで、**[アプリ]** &gt; **[アプリの追加]** の順に選択して Intune ソフトウェア パブリッシャーを起動し、**[次へ]** をクリックします。

2.  **[ソフトウェア セットアップ]** ページで **[App Store の管理されている iOS アプリ]** を選択し、**[URL の指定]** に [iOS 向け Skycure アプリの URL](https://itunes.apple.com/us/app/skycure/id695620821?mt=8) を貼り付けます。

    ![Intune ソフトウェア パブリッシャーの管理対象 iOS アプリ](../media/mtp/skycure-add-apps-3.png)

3.  **[ソフトウェアの説明]** ページの **[発行元]**、**[名前]**、**[説明]** に入力し、**[このアプリをポータル サイトでおすすめアプリとして強調表示します]** オプションを選択し、**[次へ]** をクリックします。

    ![Intune ソフトウェア パブリッシャーのオプション](../media/mtp/skycure-add-apps-4.png)

4.  **[要件]** ページの **[モバイル デバイスの種類]** で **[すべて]** オプションを選択し、**[次へ]** をクリックします。

5.  **[アップロード]** をクリックし、**[閉じる]** をクリックします。

## <a name="to-add-the-microsoft-authenticator-app-for-ios"></a>iOS 向けの Microsoft Authenticator アプリを追加するには

1.  Intune クラシック コンソールで、**[アプリ]** &gt; **[アプリの追加]** の順に選択して Intune ソフトウェア パブリッシャーを起動し、**[次へ]** をクリックします。

2.  **[ソフトウェア セットアップ]** ページで **[App Store の管理されている iOS アプリ]** を選択し、**[URL の指定]** に [iOS 向け Microsoft Authenticator アプリの URL](https://itunes.apple.com/us/app/microsoft-authenticator/id983156458?mt=8) を貼り付けます。

    ![Intune ソフトウェア パブリッシャーの管理対象 iOS アプリ 2](../media/mtp/skycure-add-apps-5.png)

3.  **[ソフトウェアの説明]** ページの **[発行元]**、**[名前]**、**[説明]** に入力し、**[このアプリをポータル サイトでおすすめアプリとして強調表示します]** オプションを選択し、**[次へ]** をクリックします。

    ![Intune ソフトウェア パブリッシャーの管理対象 iOS アプリ 3](../media/mtp/skycure-add-apps-6.png)

4.  **[要件]** ページの **[モバイル デバイスの種類]** で **[すべて]** オプションを選択し、**[次へ]** をクリックします。

5.  **[アップロード]** をクリックし、**[閉じる]** をクリックします。

## <a name="to-add-the-skycure-ios-app-configuration-policy"></a>Skycure iOS アプリ構成ポリシーを追加するには

1.  Intune クラシック コンソールで、**[ポリシー]** &gt; **[概要] &gt; [ポリシーの追加]** の順に選択します。

2.  ポリシーの一覧で、**[iOS]**を展開し、**[モバイル アプリ構成ポリシー (iOS 8.0 以降)]**、**[ポリシーの作成]** の順に選択します。

    ![iOS アプリ構成ポリシー](../media/mtp/skycure-add-apps-7.png)

3.  **[ポリシーの作成]** ページの **[全般]** セクションで、iOS アプリ構成ポリシーの名前と説明を指定します。説明は省略可能です。

    a.  メモ帳のようなテキスト エディターで **skycure\_configuration.plist** ファイルを開き、その内容をコピーして**モバイル アプリ構成ポリシー**の本文に貼り付け、**[検証]**、**[ポリシーの保存]** の順に選択します。

       ![iOS アプリ構成ポリシー 2](../media/mtp/skycure-add-apps-8.png)

## <a name="next-steps"></a>次のステップ

[Skycure アプリ、Microsoft Authenticator アプリ、iOS アプリ構成ポリシーの展開](/intune-classic/deploy-use/deploy-skycure-apps-microsoft-authenticator-app-and-ios-app-configuration-policy)

