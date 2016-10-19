---
title: "iOS および Mac の管理をセットアップする | Microsoft Intune"
description: "Microsoft Intune で、iPad や iPhone だけでなく Mac OS X デバイスを含む iOS デバイスのモバイル デバイス管理 (MDM) を有効にします。"
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dc451224-1372-4b84-b641-cfa67cb3849b
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c880bd9dfb998355a18e78af898a96d4cee393f7
ms.openlocfilehash: 263fb9add8d30c0f98af46e46b566f15513db109


---

# iOS および Mac のデバイス管理をセットアップする
iOS または Mac デバイスのセットアップについては、[こちら](../enduser/using-your-ios-or-mac-os-x-device-with-intune.md)をご覧ください。

Intune では、iPad、iPhone、および Mac OS X デバイスのモバイルデバイス管理が有効にされ、会社の電子メールおよびアプリへのアクセス権がユーザーに付与されます。 Intune で iOS および Mac デバイスを管理するには、Apple Push Notification サービス (APNs) 証明書が必要です。 証明書を Intune に追加すると、ユーザーが会社のポータル アプリをインストールして自分のデバイスを登録できます。または管理者が[企業所有の iOS デバイス管理](enroll-corporate-owned-ios-devices-in-microsoft-intune.md)をセットアップできます。

1.  **Intune をセットアップする**<br>
    **Microsoft Intune** を[モバイル デバイス管理機関に設定](prerequisites-for-enrollment.md#set-mobile-device-management-authority)して、MDM の設定を行うことにより、モバイル デバイス管理を準備します (この作業をまだ行っていない場合)。

2.  **証明書署名要求を取得する**<br>
    管理者として [Microsoft Intune 管理コンソール](http://manage.microsoft.com)を開き、**[管理]** &gt; **[モバイル デバイス管理]** &gt;**[iOS および Mac OS X]** &gt; **[APNs 証明書のアップロード]** の順に移動して、**[APNs 証明書要求のダウンロード]** をクリックします。 証明書署名要求 (.csr) ファイルをローカルに保存します。 .csr ファイルは、Apple Push Certificates Portal からの信頼関係証明書を要求するために使用します。

    ![[APNs 証明書のアップロード] ダイアログ ボックス](../media/Intune-iOS-enrollment-with-apns.png)

3.  **Apple Push Notification サービス証明書を取得する**<br>
    [Apple Push Certificates Portal](http://go.microsoft.com/fwlink/?LinkId=269844) に移動します。会社の Apple ID でサインインし、.csr ファイルを使用して APNs 証明書を作成します。 Apple の Push Certificate Portal で **[Upload]** (アップロード) をクリックすると、APNs に使用できない .json ファイルを受け取ります。 ダウンロードが完了したら、Apple Push Certificates Portal に戻り、**[Certificates for Third-Party Servers]** (サード パーティのサーバーの証明書) で、**[Download]** (ダウンロード) をクリックします。

    APNs (.pem) 証明書をダウンロードして、ファイルをローカルに保存します。 この Apple ID は、将来 APNs 証明書を更新するときにも使用する必要があります。

4.  **APNs 証明書を Intune に追加する**<br>
    [Microsoft Intune 管理コンソール](http://manage.microsoft.com)で、**[管理]** &gt; **[モバイル デバイス管理]** &gt; **[iOS および Mac OS X]** &gt; **[APNs 証明書のアップロード]** の順に移動して、**[APNs 証明書のアップロード]** をクリックします。 証明書 (.pem) ファイルを**参照** し、[ **開く** ] をクリックして、 **Apple ID**を入力します。 この APNs 証明書を使用して、Intune はモバイル デバイスを登録し、登録したモバイル デバイスにポリシーを適用して iOS デバイスを管理できます。

5.  **ポータル サイトで会社のリソースにアクセスする方法をユーザーに通知する**<br>
    ユーザーは自分のデバイスを登録する方法とデバイスが管理されるとどうなるかを知る必要があります。
    - [Microsoft Intune の使用に関するエンドユーザーへの通知内容](what-to-tell-your-end-users-about-using-microsoft-intune.md)
    - [IOS および Mac デバイス向けのエンド ユーザー ガイダンス](../enduser/using-your-ios-or-mac-os-x-device-with-intune.md)

会社または組織でユーザーのために iOS デバイスを購入した場合は、それらのデバイスも[会社所有の iOS デバイス](enroll-corporate-owned-ios-devices-in-microsoft-intune.md)として管理対象に登録できます。

### 関連項目
[Microsoft Intune で登録するための前提条件](prerequisites-for-enrollment.md)



<!--HONumber=Sep16_HO4-->


