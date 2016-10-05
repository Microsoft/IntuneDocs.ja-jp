---
title: "Windows 10 Mobile と Windows Phone の管理をセットアップする | Microsoft Intune"
description: "Microsoft Intune を使用して Windows 10 Mobile または Windows Phone デバイスのモバイル デバイス管理 (MDM) を有効にします。"
keywords: 
author: NathBarn
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f5615051-2dd1-453b-9872-d3fdcefb2cb8
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c880bd9dfb998355a18e78af898a96d4cee393f7
ms.openlocfilehash: d88405e913fe61cef2c297f9d50408e10674cf3f


---


# Microsoft Intune を使用して Windows Phone と Windows 10 Mobile の管理をセットアップする

Intune 管理者として、以下の 2 つの方法で Windows 10 Mobile および Windows Phone デバイスの登録と管理を有効にできます。

- **[Azure AD での自動登録](#azure-active-directory-enrollment)** - Windows 10 および Windows 10 Mobile のユーザーが職場または学校のアカウントを追加することでデバイスを登録します。
- **[ポータル サイト登録](#company-portal-app-enrollment)** - ポータル サイト アプリをダウンロードおよびインストールして、職場または学校のアカウント資格情報を入力し、Windows Phone 8.1 以降のデバイスを登録します。


[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## ポータル サイト アプリの登録
Intune ポータル サイト アプリをデバイスにインストールして、登録することによって、ユーザーはデバイスを登録できます。 DNS の CNAME を作成すると、ユーザーはサーバー名を入力せずに Intune に接続して登録できるようになります。 また、Windows Phone 8.0 デバイスを管理する場合や、Windows Phone デバイスにポータル サイトを展開する必要がある場合は、ポータル サイト アプリをダウンロードして署名する必要があります。 「[Windows Phone 8.0 の管理をセットアップする](set-up-windows-phone-8.0-management-with-microsoft-intune.md)」を参照してください。

1.  **Intune をセットアップする**<br>**Microsoft Intune** を[モバイル デバイス管理機関に設定](prerequisites-for-enrollment.md#set-mobile-device-management-authority)して、MDM の設定を行うことにより、モバイル デバイス管理を準備します (この作業をまだ行っていない場合)。

2.  **CNAME を作成する** (省略可能)<br>会社のドメインの **CNAME** DNS リソース レコードを作成します。 たとえば、会社の Web サイトが contoso.com の場合、EnterpriseEnrollment.contoso.com を manage.microsoft.com にリダイレクトする CNAME を DNS に作成します。 検証済みドメインが複数ある場合、ドメインごとに CNAME レコードを作成します。 CNAME リソース レコードには次の情報を含める必要があります。

  |種類:|ホスト名|指定先|TTL|
  |--------|-------------|-------------|-------|
  |CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 時間|
  |CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 時間|
  DNS レコードの変更が反映されるまでには、最大で 72 時間かかります。 DNS レコードの変更が反映されるまで、Intune で DNS の変更を確認することはできません。

  `EnterpriseEnrollment-s.manage.microsoft.com` – Intune サービスへのリダイレクトと電子メールのドメイン名によるドメイン認識をサポートします。

  `EnterpriseRegistration.windows.net` – 職場または学校のアカウントを使用して Azure Active Directory に登録される Windows 8.1 および Windows 10 Mobile デバイスをサポートします。

  会社でユーザーの資格情報に複数のドメインを使用する場合は、各ドメインに CNAME レコードを作成します。

  たとえば、会社の Web サイトが contoso.com の場合、EnterpriseEnrollment.contoso.com を EnterpriseEnrollment-s.manage.microsoft.com にリダイレクトする CNAME を DNS に作成します。 DNS レコードの変更が反映されるまでには、最大で 72 時間かかります。 DNS レコードの変更が反映されるまで、Intune で DNS の変更を確認することはできません。

3.  **CNAME を確認する**<br>[Intune 管理コンソール](http://manage.microsoft.com)で、**[管理]** &gt; **[モバイル デバイス管理]** &gt; **[Windows Phone]** の順にクリックします。 **[検証済みドメイン名の指定]** ボックスに会社の Web サイトの検証済みドメインの URL を入力し、**[自動検出のテスト]** をクリックします。

    ![[Windows 用モバイル デバイス管理のセットアップ] ダイアログ ボックス](../media/windows-phone-enrollment.png)

4.  **オプションの手順**<br>**サイドローディング キーの追加**の手順は、Windows 10 には必要ありません。 **コード署名証明書のアップロード**の手順は、Windows ストアから使用できないデバイスに基幹業務 (LOB) アプリを配信する場合にのみ必要です。 [詳細情報](set-up-windows-phone-8.0-management-with-microsoft-intune.md)

5.  **ユーザーに通知する**<br>ユーザーは自分のデバイスを登録する方法とデバイスが管理されるとどうなるかを知る必要があります。
    - [Microsoft Intune の使用に関するエンドユーザーへの通知内容](what-to-tell-your-end-users-about-using-microsoft-intune.md)
    - [Windows デバイス向けエンド ユーザー ガイダンス](../enduser/using-your-windows-device-with-intune.md)

デバイスにポータル サイトを展開する場合を除き、追加の作業は必要ありません。  管理コンソールでの手順 2. および 3. は、無視してかまいません。



<!--HONumber=Sep16_HO4-->


