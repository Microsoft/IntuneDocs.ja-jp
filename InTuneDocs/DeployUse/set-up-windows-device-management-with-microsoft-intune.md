---
title: "Microsoft Intune を使用して Windows デバイスの管理をセットアップする | Microsoft Intune"
description: 
keywords: 
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9a18c0fe-9f03-4e84-a4d0-b63821bf5d25
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6951ccdb0e37489217ef939f0cbf6fc1133a6d3c
ms.openlocfilehash: c18445385e8361cf01948b583f08e992658a8762


---

# Windows デバイスの管理をセットアップする
Intune を使用すると、Windows PC デバイスを登録し、会社の電子メールとアプリにアクセスできるようにして、BYOD ("Bring Your Own Device") を実現できます。 Azure Active Directory と共に使用すると、すばやく自動的に新しい Windows 10 デバイスを管理対象に登録し、コンピューターを再イメージ化することなく、会社のリソースにアクセスできるようになります。 登録すると、ユーザーがログインでき、Intune 管理コンソールを使用して、ユーザーのデバイスをポリシー、アプリ、および設定の対象にできます。 また、[Microsoft Intune を使用して Windows Phone の管理をセットアップする](set-up-windows-phone-management-with-microsoft-intune.md)ことや、Intune クライアントを使用して [Intune クライアント ソフトウェアを搭載したコンピューターを管理する](manage-windows-pcs-with-microsoft-intune.md)こともできます。

DNS の CNAME を作成すると、ユーザーはサーバー名を入力せずに Intune に接続して登録できるようになります。

### Windows デバイスの管理をセットアップする

  1.  会社のドメインの **CNAME** DNS リソース レコードを作成します。 たとえば、会社の Web サイトが contoso.com の場合、EnterpriseEnrollment.contoso.com を EnterpriseEnrollment-s.manage.microsoft.com にリダイレクトする CNAME を DNS に作成します。 検証済みドメインが複数ある場合、ドメインごとに CNAME レコードを作成します。CNAME リソース レコードには次の情報を含める必要があります。

  |種類:|ホスト名|指定先|TTL|
  |--------|-------------|-------------|-------|
  |CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 時間|
  |CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 時間|

    DNS レコードの変更が反映されるまでには、最大で 72 時間かかります。 DNS レコードの変更が反映されるまで、Intune で DNS の変更を確認することはできません。

    **EnterpriseEnrollment-s.manage.microsoft.com** – Intune サービスへのリダイレクトと電子メールのドメイン名によるドメイン認識をサポートします。

    **EnterpriseRegistration.windows.net** – 職場または学校のアカウントを使用して Azure Active Directory に登録される Windows 8.1 および Windows 10 Mobile デバイスをサポートします。

  2.  [Intune 管理コンソール](http://manage.microsoft.com)で、**[管理]** &gt; **[モバイル デバイス管理]** &gt; **[Windows]** の順にクリックします。
  ![Windows デバイスの管理ダイアログ ボックス](../media/enroll-intune-winenr.png)
  3.  **[検証済みドメイン名の指定]** ボックスに会社の Web サイトの検証済みドメインの URL を入力し、**[自動検出のテスト]** をクリックします。

### 関連項目
[Microsoft Intune にデバイスを登録する準備](get-ready-to-enroll-devices-in-microsoft-intune.md)



<!--HONumber=Jun16_HO4-->


