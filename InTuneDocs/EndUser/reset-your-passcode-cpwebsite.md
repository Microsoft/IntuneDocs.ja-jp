---
title: "ポータル Web サイトからパスコードをリセットする方法 | Microsoft Docs"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 01/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4fa3255b-9d1e-42d5-bd8b-70963dcf2d86
searchScope:
- Company Portal
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mamoriss
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a87fe0cf9591040f1455d71b1f40cd0705ba8abf
ms.openlocfilehash: a8ce59755a74199eda6865feda68c0613d10c2a7


---

# <a name="how-to-reset-your-device-passcode-from-the-company-portal-website"></a>ポータル サイト Web サイトからデバイスのパスコードをリセットする方法

Intune に登録したデバイスの PIN またはパスワードを紛失した場合は、[ポータル サイト web サイト](http://portal.manage.microsoft.com)からリセットすることができます。 会社のポータル Web サイトを使用すると、Intune に登録したコンピューターとデバイスを管理し、会社のポータル アプリを使用する場合とほぼ同じタスクを実行できます。

> [!NOTE]
> ポータル サイト Web サイトに **[パスコードのリセット]** ボタンが表示されないことがあります。 表示されない場合、ポータル サイト Web サイトで IT 管理者にサポートを依頼してください。

パスコードをリセットするには:

1.  [会社のポータル Web サイト](http://portal.manage.microsoft.com)を開き、パスコードをリセットするデバイスを選択します。

2.  **[パスコードのリセット]** を選択します。

    ![[パスコードのリセット] ボタンとデバイスの詳細](./media/iwp-screen-with-all-options.png)

3.  **[サインアウト]** を選択し、職場または学校の資格情報でサインインし直します。 サインインは&5; 分以内に行う必要があります。

    ![サインアウト ボタンでメッセージをリセットする](./media/iwp-2-sign-out.png)

4.  **[パスコードのリセット]** を選択します。

    ![パスコードをリセットすると何が起きるのかを説明するメッセージ](./media/iwp-3-tap-reset-passcode-after-signin.png)

    デバイスで**パスコードをリセット**した場合の影響については、次の表を確認してください。

    |デバイスの種類|リセットの結果|
    |------------|-----------|
    |Android|既存のパスコードが削除され、文字と数字の両方で仮のパスコードが作成されます。|
    |iOS|既存のパスコードが削除されます。一時パスコードは作成されません。 Touch ID 指紋スキャナーでデバイスを開いたり、商品を購入したりしている場合、Touch ID をもう一度設定する必要があります。|
    |[Windows] 10 Mobile|既存のパスコードが削除され、文字と数字の両方で仮のパスコードが作成されます。 Windows Hello 顔認識でログインしている場合、その機能を引き続け利用できます。|
    |Windows Phone 8。1|既存のパスコードが削除され、数字で仮のパスコードが作成されます。|

    5.  デバイスのロックを解除したら、新しいパスコードを設定するか、デバイスの **[設定]** で一時パスコードを変更することができます。

    パスコードが正常にリセットされたことを確認する通知を表示するには、ポータル サイト Web サイトの右上にある通知フラグをクリックします。

サポートが必要な場合は、 IT 管理者にお問い合わせください。 連絡先情報については、[ポータル サイト Web サイト](http://portal.manage.microsoft.com)をご確認ください。



<!--HONumber=Jan17_HO5-->


