---
title: "Windows デバイスを手動で同期する | Microsoft Docs"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 05/19/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 443c6de7-5187-4dc4-b844-6085a0c659bd
searchScope: User help
ROBOTS: 
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 1c1ade50ff6a458633598d2788d176dd79cbfebd
ms.sourcegitcommit: f2f147a1177d1cf5bbc8001701eb8f44dd833b7d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/12/2017
---
# <a name="sync-your-windows-device-manually"></a>Windows デバイスを手動で同期する

Windows デバイスにアプリをインストールしようとしたとき、予想より長くかかることがあります。 その場合は、手動で Windows デバイスの同期を試みることができます。 同期すると、インストールが速くなる可能性があります。

> [!Note]
> 低速のネットワークを使っている場合、または同時に多数のデバイスにコンテンツをダウンロードする場合は、アプリのインストールに少し時間がかかることがあります。

次のバージョンの Windows は手動で同期できます。 残念ながら、他のバージョンの Windows をデバイスが使っている場合は、手動同期を開始できません。

* [Windows 10 Desktop を同期する](#windows-10-desktop)
* [Windows 10 Mobile を同期する](#windows-10-mobile)
* [Windows Phone 8.1 を同期する](#windows-phone-81)

## <a name="windows-10-desktop"></a>Windows 10 Desktop
Windows 10 には複数のバージョンがあるため、2 つの手順があります。 スクリーンショットを確認し、お使いのデバイスの表示画面に近い方の手順に従ってください。

1. **[スタート]** ボタンを選択し、**[設定]** を選択します。

    ![[スタート] ボタン](./media/win10pc-sync-1-start-button.png)

2. **[設定]** ページで、**[アカウント]** をクリックします。

    ![[設定] ページの [アカウント] の選択](./media/win10pc-sync-2-settings-accounts.png)

3. 次の 2 つの画面を見て、お使いのデバイスの表示画面に似ている方をご確認ください。 お使いのデバイスの表示画面に対応する手順に従います。

    [職場または学校にアクセスする] の画面が表示されている場合は、「[[職場または学校にアクセスする] が表示されている場合の手順](#steps-to-follow-if-you-see-access-work-or-school)」にある指示に従います。

    ![[職場または学校にアクセスする] が表示されている場合の同期手順](./media/w10-enroll-rs1-connect-to-work-or-school.png)

    [職場のアクセス] の画面が表示されている場合は、「[[職場のアクセス] が表示されている場合の手順](#steps-to-follow-if-you-see-work-access)」にある指示に従います。

    ![アカウントの種類として職場のアクセスを選択する](./media/win10pc-sync-3-work-access.png)

### <a name="steps-to-follow-if-you-see-access-work-or-school"></a>[職場または学校にアクセスする] が表示されている場合の手順

1. **[アカウント]** ページで、**[職場または学校にアクセスする]** を選択します。

    ![[職場または学校にアクセスする] を選択する](./media/w10-enroll-rs1-connect-to-work-or-school.png)

2. 職場または学校のアカウントを選択します。 会社のサポートが行った設定に応じて、以下に示す例のような 2 種類のアカウントが表示されます。 1 つのアカウントの横にはブリーフケースがあり、もう 1 つのアカウントの横には Microsoft のロゴがあります。

    - ブリーフケースが表示されているアカウントがある場合はそれを選択し、その下に **[情報]** ボタンが表示されていることを確認します。
    - Microsoft のロゴが表示されているアカウントしかない場合はそのアカウントを選択して、その下に **[情報]** ボタンが表示されていることを確認します。

    ![ブリーフケースまたは Microsoft のロゴの横にあるアカウント名を選択する](./media/win10pc-rs1-sync-info-button.png)

3. **[情報]** ボタンを選択します。 次の例のようなダイアログ ボックスが開きます。

    ![ブリーフケースまたは Microsoft のロゴの横にあるアカウント名を選択する](./media/win10pc-rs1-sync-button.png)

4. **[同期]** ボタンを選択します。 デバイスと Intune が同期されます。

### <a name="steps-to-follow-if-you-see-work-access"></a>[職場のアクセス] が表示されている場合の手順

1. **[アカウント]** ページで、**[職場のアクセス]** を選択します。

    ![アカウントの種類として職場のアクセスを選択する](./media/win10pc-sync-3-work-access.png)

2. **[Enroll in to device management]** (デバイス管理に登録する) セクションで、会社名を選択します。

    ![デバイス管理の会社名の選択](./media/win10pc-sync-4-tap-com-name.png)

3. **[同期]** ボタンを選択します。

    ![[同期] ボタンの選択](./media/win10pc-sync-5-tap-sync.png)

   同期が完了するまで、このボタンは灰色表示になります。

### <a name="windows-10-mobile"></a>[Windows] 10 Mobile
アプリのインストールを高速化するために Windows 10 Mobile デバイスを手動で同期するには:

   1. **[すべてのアプリ]** > **[設定]** > **[アカウント]** の順にタップします。

       ![[設定] 画面の [アカウント] の選択](./media/win10m-sync-1-settings-accounts.png)

   2. **[職場のアクセス]** を選択します。

       ![アカウントの種類として職場のアクセスを選択する](./media/win10m-sync-2-work-access.png)

   3. **[デバイス管理に登録する]** で、会社名を選択します。

       ![デバイス管理の会社名の選択](./media/win10m-sync-3-tap-comp-name.png)

   4. **[同期]** アイコンを選択します。

       ![[同期] アイコンの選択](./media/win10m-sync-4-tap-sync.png)

       画面の上部に、"アカウントを同期中" というメッセージが表示されます。 同期が完了するまで、**[同期]** ボタンは灰色表示になります。

## <a name="windows-phone-81"></a>Windows Phone 8。1
アプリのインストールを高速化するために Windows Phone 8.1 デバイスを手動で同期するには:

1. **[すべてのアプリ]** > **[設定]** > **[会社アカウント]** の順にタップします。

    ![設定の一覧](./media/wp81-1-sync-settings-workplace.png)

2. 会社名を選択します。

    ![職場のアカウントの会社名の選択](./media/wp81-2-sync-tap-compname.png)

3. **[同期]** アイコンを選択します。

    ![[同期] アイコンの選択](./media/wp81-3-sync-tap-sync-button.png)

   デバイスで同期が完了するまでの間、画面の上部に、"アカウントを同期中" というメッセージが表示されます。

サポートが必要な場合は、 社内サポートに問い合わせてください。 連絡先情報については、[ポータル サイト Web サイト](https://portal.manage.microsoft.com#HelpDeskDialog)をご確認ください。
