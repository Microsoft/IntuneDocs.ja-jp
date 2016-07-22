---
title: "iOS および Mac の管理をセットアップする | Microsoft Intune"
description: 
keywords: 
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dc451224-1372-4b84-b641-cfa67cb3849b
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: bb44d53c87bec1b6892bf49a65f3df684199ed08
ms.openlocfilehash: 9766b6e64259d809b04e6f6004c25ed88ad72659


---

# iOS および Mac のデバイス管理をセットアップする
Microsoft Intune を使用すると、iOS および Mac OS X デバイスを登録し、iPhone、iPad、Mac のユーザーが会社の電子メールとアプリにアクセスできるようにして、BYOD ("Bring Your Own Device") を実現できます。 有効にすると、ユーザーは Intune のポータル サイト アプリをインストールでき、Intune 管理コンソールを使用して、ユーザーのデバイスをポリシーの対象にできます。

Intune で iOS デバイスを管理するには、デバイスが Intune と通信できる必要があります。 Apple では、Apple Push Notification サービス (APNs) 証明書をインポートすることによって確立された Intune との信頼関係を必要としています。

1.  **Intune をセットアップする**<br>
    **Microsoft Intune** を[モバイル デバイス管理機関に設定](get-ready-to-enroll-devices-in-microsoft-intune.md#set-mobile-device-management-authority)して、MDM の設定を行うことにより、モバイル デバイス管理を準備します (この作業をまだ行っていない場合)。

2.  **証明書署名要求を取得する**<br>
    管理者として [Microsoft Intune 管理コンソール](http://manage.microsoft.com)を開き、**[管理]** &gt; **[モバイル デバイス管理]** &gt;**[iOS および Mac OS X]** &gt; **[APNs 証明書のアップロード]** の順に移動して、**[APNs 証明書要求のダウンロード]** をクリックします。 証明書署名要求 (.csr) ファイルをローカルに保存します。 .csr ファイルは、Apple Push Certificates Portal からの信頼関係証明書を要求するために使用します。

    ![[APNs 証明書のアップロード] ダイアログ ボックス](../media/Intune-iOS-enrollment-with-apns.png)

3.  **Apple Push Notification サービス証明書を取得する**<br>
    [Apple Push Certificates Portal](http://go.microsoft.com/fwlink/?LinkId=269844) に移動します。会社の Apple ID でサインインし、.csr ファイルを使用して APNs 証明書を作成します。 Apple の Push Certificate Portal で **[Upload]** (アップロード) をクリックすると、APNs に使用できない .json ファイルを受け取ります。 ダウンロードが完了したら、Apple Push Certificates Portal に戻り、**[Certificates for Third-Party Servers]** (サード パーティのサーバーの証明書) で、**[Download]** (ダウンロード) をクリックします。

    APNs (.pem) 証明書をダウンロードして、ファイルをローカルに保存します。 この Apple ID は、将来 APNs 証明書を更新するときにも使用する必要があります。

4.  **APNs 証明書を Intune に追加する**<br>
    [Microsoft Intune 管理コンソール](http://manage.microsoft.com)で、**[管理]** &gt; **[モバイル デバイス管理]** &gt; **[iOS および Mac OS X]** &gt; **[APNs 証明書のアップロード]** の順に移動して、**[APNs 証明書のアップロード]** をクリックします。 証明書 (.pem) ファイルを**参照** し、[ **開く** ] をクリックして、 **Apple ID**を入力します。 この APNs 証明書を使用して、Intune はモバイル デバイスを登録し、登録したモバイル デバイスにポリシーを適用して iOS デバイスを管理できます。

5.  **ポータル サイトで会社のリソースにアクセスする方法をユーザーに通知する**<br>
    ユーザーは自分のデバイスを登録する方法とデバイスが管理されるとどうなるかを知る必要があります。 [Microsoft Intune の使用に関するエンドユーザーへの通知内容](what-to-tell-your-end-users-about-using-microsoft-intune.md)

会社または組織でユーザーのために iOS デバイスを購入した場合は、それらのデバイスも[会社所有の iOS デバイス](enroll-corporate-owned-ios-devices-in-microsoft-intune.md)として管理対象に登録できます。

### 関連項目
[Microsoft Intune にデバイスを登録する準備](get-ready-to-enroll-devices-in-microsoft-intune.md)



<!--HONumber=Jun16_HO4-->


