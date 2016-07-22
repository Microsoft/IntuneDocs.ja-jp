---
title: "ポータル サイト Web サイトからデバイスのパスコードをリセットする | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4fa3255b-9d1e-42d5-bd8b-70963dcf2d86
ms.reviewer: mamoriss
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e52ebdd62ca68f1d9226def654961075400184a8
ms.openlocfilehash: 31023a2d51d4dd4cb854c1fa077f5a9910232bb4


---


# ポータル サイト Web サイトからデバイスのパスコードをリセットする

Intune に登録したデバイスの PIN またはパスワードを紛失した場合は、[ポータル サイト web サイト](http://portal.manage.microsoft.com)からリセットすることができます。 ポータル サイト Web サイトは、Intune に登録したコンピューターとデバイスを管理し、ポータル サイト アプリを使用する場合とほぼ同じタスクを実行できる Web ページです。

> [!NOTE] 
> IT 管理者の Intune の構成によっては、ポータル サイト Web サイトに [パスコードのリセット] ボタンが表示されない場合があります。 Windows 8.1 と Windows RT のデバイスでは、パスコードのリセットがサポートされていません。

パスコードをリセットするには:

1.  [ポータル サイト Web サイト](http://portal.manage.microsoft.com)を開き、パスコードをリセットするデバイスをタップします。

2.  **[パスコードのリセット]** をタップします。

    ![tap-passcode-to-reset](./media/iwp-1-tap-reset-passcode.png)

3.  **[サインアウト]** をタップし、職場または学校の資格情報でサインインし直します。 サインインは 5 分以内に行う必要があります。

    ![sign-out-sign-back-in](./media/iwp-2-sign-out.png)

4.  **[パスコードのリセット]** をタップします。

    ![tap-reset-passcode](./media/iwp-3-tap-reset-passcode-after-signin.png)

    デバイスでパスコードをリセットした場合の影響については、次の表を確認してください。

    |プラットフォーム|Support|
    |------------|-----------|
    |Android|英数字の一時パスコードが新しく作成されます。|
    |iOS|デバイスからパスコードが削除され、新しい一時パスコードは作成されません。 Touch ID を使用している場合、パスコードをリセットすると、Tech ID が削除されるため、デバイスで再度セットアップする必要があります。|
    |Windows 10 (モバイル デバイスのみ)|英数字の一時パスコードが新しく作成されます。 Windows Hello がサポートされています。|
    |Windows Phone 8。1|数字の一時パスコードが新しく作成されます。|
    デバイスのロックを解除した後、デバイスの **[設定]** から新しいパスコードを設定することができます。

5.  デバイスのロックを解除したら、新しいパスコードを設定するか、デバイスの **[設定]** で一時パスコードを変更することができます。

    パスコードが正常にリセットされたことを確認する通知を表示するには、ポータル サイト Web サイトの右上にある通知フラグをクリックします。

サポートが必要な場合は、 IT 管理者にお問い合わせください。 連絡先情報については、[ポータル サイト Web サイト](http://portal.manage.microsoft.com)をご確認ください。

### 関連項目
[Intune ポータル サイト Web サイトの使用](using-the-intune-company-portal-website.md)


<!--HONumber=Jun16_HO4-->


