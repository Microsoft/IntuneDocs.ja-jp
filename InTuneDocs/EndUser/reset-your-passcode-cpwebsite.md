---
title: "ポータル サイト Web サイトからデバイスのパスコードをリセットする | Microsoft Intune"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 09/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4fa3255b-9d1e-42d5-bd8b-70963dcf2d86
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mamoriss
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9ddbcde20fac83289c4622f69538ff00fa0cb65b
ms.openlocfilehash: b3a3b7c2a983776f79ffa8562e130bb11e714e29


---


# <a name="reset-your-device-passcode-from-the-company-portal-website"></a>ポータル サイト Web サイトからデバイスのパスコードをリセットする

Intune に登録したデバイスの PIN またはパスワードを紛失した場合は、[ポータル サイト web サイト](http://portal.manage.microsoft.com)からリセットすることができます。 会社のポータル Web サイトを使用すると、Intune に登録したコンピューターとデバイスを管理し、会社のポータル アプリを使用する場合とほぼ同じタスクを実行できます。

> [!NOTE]
> IT 管理者の Intune の構成によっては、ポータル サイト Web サイトに **[パスコードのリセット]** ボタンが表示されない場合があります。 Windows 8.1 デバイスでは、パスコードのリセットがサポートされていません。

パスコードをリセットするには:

1.  [会社のポータル Web サイト](http://portal.manage.microsoft.com)を開き、パスコードをリセットするデバイスを選択します。

2.  **[パスコードのリセット]** を選択します。

    ![[パスコードのリセット] ボタンとデバイスの詳細](./media/iwp-screen-with-all-options.png)

3.  **[サインアウト]** を選択し、職場または学校の資格情報でサインインし直します。 サインインは 5 分以内に行う必要があります。

    ![サインアウト ボタンでメッセージをリセットする](./media/iwp-2-sign-out.png)

4.  **[パスコードのリセット]** を選択します。

    ![パスコードをリセットすると何が起きるのかを説明するメッセージ](./media/iwp-3-tap-reset-passcode-after-signin.png)

    デバイスで**パスコードをリセット**した場合の影響については、次の表を確認してください。

    |プラットフォーム|Support|
    |------------|-----------|
    |Android|英数字の一時パスコードが作成されます。|
    |iOS|デバイスからパスコードが削除され、一時パスコードは作成されません。 Touch ID を使用している場合、パスコードをリセットすると、Tech ID が削除されるため、デバイスで再度セットアップする必要があります。|
    |Windows 10 (モバイル デバイスのみ)|英数字の一時パスコードが作成されます。 Windows Hello がサポートされています。|
    |Windows Phone 8。1|数字の一時パスコードが作成されます。|
    デバイスのロックを解除した後、デバイスの **[設定]** から新しいパスコードを設定することができます。

5.  デバイスのロックを解除したら、新しいパスコードを設定するか、デバイスの **[設定]** で一時パスコードを変更することができます。

    パスコードが正常にリセットされたことを確認する通知を表示するには、ポータル サイト Web サイトの右上にある通知フラグをクリックします。

サポートが必要な場合は、 IT 管理者にお問い合わせください。 連絡先情報については、[ポータル サイト Web サイト](http://portal.manage.microsoft.com)をご確認ください。



<!--HONumber=Nov16_HO2-->


