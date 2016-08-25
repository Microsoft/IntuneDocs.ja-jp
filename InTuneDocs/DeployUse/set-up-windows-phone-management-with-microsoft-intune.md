---
title: "Windows 10 Mobile と Windows Phone の管理をセットアップする | Microsoft Intune"
description: "Microsoft Intune を使用して Windows 10 Mobile または Windows Phone デバイスのモバイル デバイス管理 (MDM) を有効にします。"
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f5615051-2dd1-453b-9872-d3fdcefb2cb8
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 06d6c8ce97ba6a259055e94f0eba87f7c5a96531
ms.openlocfilehash: 344f1cf4367deb12288f9c361e043d345f9846bb


---


# Microsoft Intune を使用して Windows Phone と Windows 10 Mobile の管理をセットアップする
Windows デバイスのセットアップについては、[こちら](../enduser/using-your-windows-device-with-intune.md)をご覧ください。

Microsoft Intune で Windows 10 Mobile または Windows Phone デバイスを管理するには、デバイスが Intune と通信できる必要があります。 これを簡略化する方法として、DNS レコードを作成できます。そうすると、ユーザーはサーバー アドレスを入力する必要がなくなります。 次の手順では、ユーザーの登録を簡略化する方法について説明します。  

ほとんどのシナリオでは、ユーザーは Windows ストアからポータル サイト アプリをインストールできます。 また、Windows Phone 8.0 デバイスを管理する場合や、Windows Phone デバイスにポータル サイトを展開する必要がある場合は、ポータル サイト アプリをダウンロードして署名する必要があります。 「[Windows Phone 8.0 の管理をセットアップする](set-up-windows-phone-8.0-management-with-microsoft-intune.md)」を参照してください。

1.  **Intune をセットアップする** **Microsoft Intune** を[モバイル デバイス管理機関に設定](get-ready-to-enroll-devices-in-microsoft-intune.md#set-mobile-device-management-authority)して、MDM の設定を行うことにより、モバイル デバイス管理を準備します (この作業をまだ行っていない場合)。

2.  **登録サーバーのアドレスの DNS エイリアスを設定する** (オプション)

    DNS エイリアス (CNAME レコード タイプ) を作成すると、ユーザーがデバイスを簡単に登録できるようになります。 CNAME DNS エントリは Windows デバイス登録では省略可能ですが、Windows デバイスの登録プロセス中にわかりやすくするために、必要なときは 1 つまたは複数のレコードを作成することをお勧めします。 CNAME レコードが検出されない場合は、MDM サーバー名を手動で入力するように求められます。

  1.  会社のドメインの **CNAME** DNS リソース レコードを作成します。 たとえば、会社の Web サイトが contoso.com の場合、EnterpriseEnrollment.contoso.com を manage.microsoft.com にリダイレクトする CNAME を DNS に作成します。 検証済みドメインが複数ある場合、ドメインごとに CNAME レコードを作成します。CNAME リソース レコードには次の情報を含める必要があります。

      |種類:|ホスト名|指定先|TTL|
      |--------|-------------|-------------|-------|
      |CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 時間|
      |CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 時間|

      DNS レコードの変更が反映されるまでには、最大で 72 時間かかります。 DNS レコードの変更が反映されるまで、Intune で DNS の変更を確認することはできません。

      **EnterpriseEnrollment-s.manage.microsoft.com** – Intune サービスへのリダイレクトと電子メールのドメイン名によるドメイン認識をサポートします。

      **EnterpriseRegistration.windows.net** – 職場または学校のアカウントを使用して Azure Active Directory に登録される Windows 8.1 および Windows 10 Mobile デバイスをサポートします。

    2.  [Intune 管理コンソール](http://manage.microsoft.com)で、**[管理]** &gt; **[モバイル デバイス管理]** &gt; **[Windows Phone]** の順にクリックします。

      ![[Windows 用モバイル デバイス管理のセットアップ] ダイアログ ボックス](../media/windows-device-enrollment.png)

    3.  **[検証済みドメイン名の指定]** ボックスに会社の Web サイトの検証済みドメインの URL を入力し、**[自動検出のテスト]** をクリックします。

    4.  ユーザーは自分のデバイスを登録する方法とデバイスが管理されるとどうなるかを知る必要があります。
        - [Microsoft Intune の使用に関するエンドユーザーへの通知内容](what-to-tell-your-end-users-about-using-microsoft-intune.md)
        - [Windows デバイス向けエンド ユーザー ガイダンス](../enduser/using-your-windows-device-with-intune.md)



デバイスにポータル サイトを展開する場合を除き、追加の作業は必要ありません。  管理コンソールでの手順 2. および 3. は、無視してかまいません。



<!--HONumber=Aug16_HO1-->


