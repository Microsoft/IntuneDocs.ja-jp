---
# required metadata

title: Microsoft Intune を使用して Windows デバイスの管理をセットアップする | Microsoft Intune
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

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

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

    DNS record changes might take up to 72 hours to propagate. You cannot verify the DNS change in Intune until the DNS record propagates.

    **EnterpriseEnrollment-s.manage.microsoft.com** – Supports a redirect to the Intune service with domain recognition from the email’s domain name

    **EnterpriseRegistration.windows.net** – Supports Windows 8.1 and Windows 10 Mobile devices that will register with Azure Active Directory using their work or school account

  2.  [Intune 管理コンソール](http://manage.microsoft.com)で、**[管理]** &gt; **[モバイル デバイス管理]** &gt; **[Windows]** の順にクリックします。.
  ![Windows デバイスの管理ダイアログ ボックス](../media/enroll-intune-winenr.png)
  3.  **[検証済みドメイン名の指定]** ボックスに会社の Web サイトの検証済みドメインの URL を入力し、**[自動検出のテスト]** をクリックします。.

### 関連項目
[Microsoft Intune にデバイスを登録する準備](get-ready-to-enroll-devices-in-microsoft-intune.md)


<!--HONumber=May16_HO1-->


