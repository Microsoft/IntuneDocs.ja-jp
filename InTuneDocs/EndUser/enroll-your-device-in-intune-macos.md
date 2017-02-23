---
title: "Intune に macOS デバイスを登録する | Microsoft Docs"
description: "Intune に macOS デバイスを登録する方法について説明します"
keywords: Mac OS X, macOS, OS X
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 11/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 58eb0e7a-1321-4c66-a281-88fb01e72c1c
searchScope:
- Company Portal
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
translationtype: Human Translation
ms.sourcegitcommit: 9530eb45bf027c66c4a36e4cea1ec05c5f15a6e5
ms.openlocfilehash: 60879acf553934d246c662060e3d57ec50c51658


---

# <a name="enroll-your-macos-device-in-intune"></a>Intune に macOS デバイスを登録する

組織のアプリ、データ、リソースにアクセスできれば、業務を遂行することができます。 仕事に macOS デバイスを使用している場合、そのためには__管理プロファイル__をインストールする必要があります。 管理プロファイルは IT 管理者によってセットアップされるファイルにすぎず、設定とアクセス情報を Mac に読み込みます。 詳細については、 [ポータル サイト アプリをインストールし、Intune にデバイスを登録するとどうなるか](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-ios.md)に関するページをご覧ください。

  > [!NOTE]
  > iPhone や iPad などの iOS デバイスを実際に登録してみる場合は、[代わりにこちらの説明をご覧ください](enroll-your-device-in-intune-ios.md)。

1. __Dock__ で __Safari__ を起動し、新しいウィンドウを開いてから、[会社のポータル Web サイト](http://portal.manage.microsoft.com)を開きます。
2. 職場や学校のアカウントで会社のポータル Web サイトにログインします。

  [!INCLUDE[wit_nextref](../includes/end-user-password-guidance.md)]

3. ログインすると、利用できる__アプリ__、__デバイス__、IT スタッフの__連絡先情報__が表示されます。 ページの先頭に次のように表示されます。"**このデバイスはまだ登録されていないか、ポータル サイトで特定できません。別のデバイスを選択するには、<u>ここをタップ</u>してください。**" __[ここをタップ]__ をクリックします。

 ![macOS の会社のポータル ランディング ページ](./media/macOS_enroll_001_landing_page.png)

4. __このデバイスを特定または登録する__理由についての簡単な説明がポップアップ ウィンドウに表示されます。 それを確認した後、__[登録]__ をクリックして続けます。

 ![このデバイスの macOS の特定または登録](./media/macOS_enroll_002_IDenroll_popup.png)

5. 別のポップアップ ウィンドウが開き、__このデバイスを登録__した場合についての簡単な説明が表示されます。 それを確認した後、__[インストール]__ をクリックして続けます。

 ![このデバイスの macOS を登録する](./media/macOS_enroll_003_enroll_popup.png)

  > [!NOTE]
  > Intune は、ユーザーのコンピューターにアクセスして、そのデバイスが組織のリソースにアクセスしても十分に安全であることを確認する必要があります。 「[ポータル サイト アプリをインストールし、Intune に iOS または Mac OS X デバイスを登録するとどうなりますか](what-happens-if-you-install-the-Company-Portal-app-and-enroll-your-device-in-intune-ios.md)」をご覧ください。

6. __[システム環境設定]__ が開き、__"管理プロファイル" をインストール__するかどうかの確認を求められます。 __[インストール]__ をクリックして続行するか、__[プロファイルの表示]__ をクリックして詳細を確認します。

 ![管理プロファイルをインストールする](./media/macOS_enroll_004_sysprefs_mgmt_profile.png)

7. macOS のポップアップ ウィンドウが表示されます。 使用するコンピューターの __[ユーザー名]__ と __[パスワード]__ を入力して __[OK]__ をクリックし、変更を行うことを確認します。 これにより、管理プロファイルが Mac にインストールされます。

 ![macOS のプロファイル インストール ポップアップ](./media/macOS_enroll_005_sysprefs_admin_login.png)

8. プロファイルの詳細または__インストール__の確認についての追加メッセージが Mac から表示される場合があります。 __[続行]__ および __[インストール]__ をクリックして処理を続けます。 インストールが終了すると、新しくインストールした__管理プロファイル__を __[デバイス プロファイル]__ の一覧で確認できます。

 ![インストールされた macOS プロファイル](./media/macOS_enroll_006_sysprefs_installed_profile.png)

サポートが必要な場合は、 IT 管理者に問い合わせてください。 連絡先の情報は、[会社のポータル Web サイト](http://portal.manage.microsoft.com)でわかります。



<!--HONumber=Feb17_HO2-->


