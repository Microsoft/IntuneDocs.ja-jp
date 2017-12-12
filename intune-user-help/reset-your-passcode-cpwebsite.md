---
title: "ポータル Web サイトからパスコードをリセットする方法 | Microsoft Docs"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 06/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4fa3255b-9d1e-42d5-bd8b-70963dcf2d86
searchScope: User help
ROBOTS: 
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 43460cb18681c47e14c89c8dbeb70a4ae006eb7d
ms.sourcegitcommit: f2f147a1177d1cf5bbc8001701eb8f44dd833b7d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/12/2017
---
# <a name="how-to-reset-your-device-passcode-from-the-company-portal-website"></a>ポータル サイト Web サイトからデバイスのパスコードをリセットする方法

Intune に登録したデバイスの PIN またはパスワードを紛失した場合は、[ポータル サイト web サイト](https://portal.manage.microsoft.com#HelpDeskDialog)からリセットすることができます。 会社のポータル Web サイトを使用すると、Intune に登録したコンピューターとデバイスを管理し、会社のポータル アプリを使用する場合とほぼ同じタスクを実行できます。

> [!NOTE]
> 会社に登録されたデバイスを使用している場合、ポータル サイト Web サイトに [パスコードのリセット] ボタンが表示されないことがあります。 表示されない場合は、会社のサポートにパスコードのリセットを依頼する必要があります。

パスコードをリセットするには:

1.  [ポータル Web サイト](https://portal.manage.microsoft.com#HelpDeskDialog)で、__メニュー__ ボタン ![3 つの横棒が並行に積み上げられている、メニュー ボタンの小さな画像](/intune/media/CP_hamburger_menu.png) をタップしてから、__[デバイス]__ を選択します。

2. __[デバイス]__ ページで、パスコードをリセットするデバイスの名前を選択します。

  ![リスト表示されていないデバイスの登録または不明なデバイスの識別を求めるバナーの上に 2 つの不明なデバイスが示された、[デバイス] ページのスクリーンショット。](./media/macOS_enroll_002_tap_here_banner.png)

3.  デバイスがポップアップ ウィンドウに開きます。 **[パスコードのリセット]** ボタンを選択します。

    ![[名前の変更]、[削除]、[デバイスのリセット]、[パスコードのリセット]、[リモート ロック] を含む、ポータル Web サイト上の選択されたデバイスに対するすべてのオプション。 ](./media/iwp-screen-with-all-options.png)

4.  パスコードをリセットすることと、リセット後にデバイスからサインアウトすることの確認を求めるバナーが表示されます。 再度サインインするには、5 分間待つ必要があります。

  ![デバイスのパスコードのリセットとユーザーのログアウトに関する警告が示されている、リセットのパスコード バナー。ユーザー入力用のボタンは、[サインアウト] と [キャンセル] です。](./media/iwp-reset-passcode-popup.png)

5.  **[サインアウト]** を選択すると、デバイスのパスコードが削除されることを知らせる最終メッセージが表示されます。 デバイスを携帯しない場合は、パスコードを削除しないでください。削除すると、デバイスに物理的にアクセスできるユーザーは誰でも、デバイス上のほとんどの (個人または会社の) 情報にアクセスできるようになります。 

  ![デバイスのパスコードのリセットとデバイスからのパスコードの削除に関する警告が示されている、2 番目のリセットのパスコード バナー。 また、デバイスの設定に移動して、新しいパスコードを設定する方法も示されます。](./media/iwp-reset-passcode-2nd-popup.png)

  デバイスによってパスコードの種類が異なります。

  **Android**: 既存のパスコードが削除され、文字と数字の両方で仮のパスコードが作成されます。 
  
  > [!NOTE]
  > Android 7.0 以降のデバイスのパスコードはリセットできません。 そのようなデバイスでパスコードを忘れた場合は、工場出荷時の設定にリセットする必要があります。

  **iOS**: 既存のパスコードが削除されます。一時パスコードは作成されません。 Touch ID 指紋スキャナーでデバイスを開いたり、商品を購入したりしている場合、Touch ID をもう一度設定する必要があります。

  **Windows 10 Mobile**: 既存のパスコードが削除され、文字と数字の両方で仮のパスコードが作成されます。 Windows Hello 顔認識でログインしている場合、その機能を引き続き利用できます。
    
  **Windows Phone 8.1**: 既存のパスコードが削除され、数字で仮のパスコードが作成されます。

  Android および Windows デバイスの場合は、一時パスワードが **[デバイスの詳細]** に表示されます。 

6.  デバイスのロックを解除したら、新しいパスコードを設定するか、デバイスの **[設定]** で一時パスコードを変更することができます。

パスコードが正常にリセットされたことを確認する通知を表示するには、ポータル サイト Web サイトの右上にある通知フラグをクリックします。

サポートが必要な場合は、 社内サポートに問い合わせてください。 連絡先情報については、[ポータル サイト Web サイト](https://portal.manage.microsoft.com#HelpDeskDialog)をご確認ください。
