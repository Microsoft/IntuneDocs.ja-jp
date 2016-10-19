---
title: "モバイル デバイスを登録してアプリをインストールする | Microsoft Intune"
description: "モバイル デバイスを登録して、Intune 登録デバイスにアプリをインストールする方法を説明します"
keywords: 
author: barlanmsft
manager: angrobe
ms.date: 08/29/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5d3215e7-0a5c-44bd-afb0-aeafce98c43f
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c880bd9dfb998355a18e78af898a96d4cee393f7
ms.openlocfilehash: 4c72b39296c9c2f0fe435d57f1e829ba3114fc61


---

# モバイル デバイスを登録してアプリをインストールする
Intune を使用してモバイル デバイス管理をセットアップするには、まずモバイル デバイス管理機関を設定し、デバイス プラットフォームの管理を有効にして、ポータル サイト アプリでデバイスを登録する必要があります。 その後、手順 6. で発行した Microsoft Skype アプリケーションを展開できます。

## デバイス管理を有効にして、デバイスを登録する

1.  **Intune をモバイル デバイス管理機関にする** [Intune 管理コンソール](https://manage.microsoft.com/)で、**[管理者]** > **[モバイル デバイス管理]** の順に選択し、**[タスク]** で **[MDM 機関の設定]** を選択します。  MDM 機関ダイアログ ボックスで **[はい]** をクリックします。
    ![管理コンソール。 MDM を Intune に設定](./media/mdmAuthority.png)

2.  **デバイス プラットフォームの MDM を有効にする** 管理対象のデバイス プラットフォームに対してモバイル デバイス管理を有効にします。 要件はプラットフォームによって異なります。

    -   **iOS および Mac OS X**: 「[Microsoft Intune を使用して iOS および Mac の管理をセットアップする](/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune)」を参照してください。

    -   **Windows Phone**: 「[Microsoft Intune を使用して Windows Phone の管理をセットアップする](/intune/deploy-use/set-up-windows-phone-management-with-microsoft-intune)」を参照してください。

    -   **Android**: Android モバイル デバイスは、ユーザーが、[Google Play](https://play.google.com/store/apps/details?id=com.skype.raider) から入手できるポータル サイト アプリを使用して登録できます。 Intune での追加構成は不要です。

3.  **デバイスを登録する**

    -   **Android** - [Google Play](http://go.microsoft.com/fwlink/p/?LinkId=386612) から Microsoft Corporation の **Intune ポータル サイト** アプリをインストールし、前述の手順で追加した Intune ユーザー資格情報を使用してサインインします。

    -   **iOS および Mac OS X** - App Store から Microsoft Corporation の **Microsoft Intune ポータル サイト** アプリをインストールし、前述の手順で追加した Intune ユーザー資格情報を使用してサインインします。 **[登録済みデバイス]** を表示して、デバイスを追加します。

    -   **Windows Phone 8.1** - Windows Phone ストアから Microsoft Corporation の**ポータル サイト** アプリをインストールし、前述の手順で追加した Intune ユーザー資格情報を使用してサインインします。  **[登録済みデバイス]** を表示して、デバイスを追加します。

    -   **Windows Phone 8.0** - **[システム設定]**&gt;**[業務用アプリ]** の順に選択し、前述の手順で追加した Intune ユーザー資格情報を使用してサインインします。 ポータル サイト アプリがお使いの電話に展開されます。

    **サーバー アドレス**の入力を求めるメッセージが表示された場合は、「manage.microsoft.com」と入力します。

## 登録済みのデバイスにアプリをインストールする
このクイック スタート ガイドの[手順 6.](start-with-a-paid-subscription-to-microsoft-intune-step-6.md) では、カスタムの Intune ユーザー グループに Skype アプリを発行しました。 そのため、新しく登録したデバイスにそのアプリをインストールできます。

登録済みのモバイル デバイスでポータル サイトを開き、**[アプリ]** を選択して、**Microsoft Skype** をインストールします。

[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] を使用したモバイル デバイス管理の詳細については、「[Intune でデバイスを登録するための前提条件](/intune/deploy-use/prerequisites-for-enrollment.md)」を参照してください。


### 次のステップ
これで終了です。 *Intune のクイック スタート ガイド*の最後の手順が完了しました。 これで初期構成が完了したので、追加の MDM 機能の有効化を検討できます。

>[!div class="step-by-step"]

>[&larr; **デバイスを登録する**](.\start-with-a-paid-subscription-to-microsoft-intune-step-8.md)     [**構成後のタスク** &rarr;](.\post-configuration-tasks.md)  



<!--HONumber=Sep16_HO4-->


