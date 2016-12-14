---
title: "Windows 10 Mobile と Windows Phone の管理をセットアップする | Microsoft Intune"
description: "Microsoft Intune を使用して Windows 10 Mobile または Windows Phone デバイスのモバイル デバイス管理 (MDM) を有効にします。"
keywords: 
author: staciebarker
manager: angrobe
ms.date: 11/10/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f5615051-2dd1-453b-9872-d3fdcefb2cb8
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c59707ba2967b069dc30aee71d2642e91d71b23b
ms.openlocfilehash: 3141d4b2ad1a21e2ac5ba7b6cafb74f567d07f7a


---


# <a name="set-up-windows-phone-and-windows-10-mobile-management-with-microsoft-intune"></a>Microsoft Intune を使用して Windows Phone と Windows 10 Mobile の管理をセットアップする

Intune 管理者として、以下の 2 つの方法で Windows 10 Mobile および Windows Phone デバイスの登録と管理を有効にできます。

- **[Azure Active Directory での自動登録](#azure-active-directory-enrollment)** - Windows 10 および Windows 10 Mobile のユーザーが職場または学校のアカウントを追加することでデバイスを登録します。
- **[ポータル サイト登録](#company-portal-app-enrollment)** - Windows Phone 8.1 以降のユーザーがポータル サイト アプリをダウンロードおよびインストールして、職場または学校のアカウント資格情報を入力することでデバイスを登録します。


[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## <a name="company-portal-app-enrollment"></a>ポータル サイト アプリの登録
Intune ポータル サイト アプリをデバイスにインストールして登録することによって、ユーザーはデバイスを登録できます。 DNS の CNAME リソース レコードを作成すると、ユーザーはサーバー名を入力するとなく Intune に接続して登録できるようになります。

1.  **Intune をセットアップする**<br>**Microsoft Intune** を[モバイル デバイス管理 (MDM) 機関に設定](prerequisites-for-enrollment.md#step-2-set-mdm-authority)して、MDM の設定を行うことにより、モバイル デバイス管理を準備します (この作業をまだ行っていない場合)。

2.  **CNAME を作成する** (省略可能)<br>会社のドメインの **CNAME** DNS リソース レコードを作成します。 たとえば、会社の Web サイトが contoso.com の場合、EnterpriseEnrollment.contoso.com を enterpriseenrollment-s.manage.microsoft.com にリダイレクトする CNAME を DNS に作成します。

    CNAME DNS エントリの作成は省略可能ですが、CNAME レコードにより登録が簡単になります。 CNAME レコードの登録が見つからない場合、ユーザーは手動で MDM サーバー名 https://manage.microsoft.com を入力するように求められます。

    EnterpriseEnrollment.contoso.com を manage.microsoft.com にリダイレクトする CNAME が DNS に既にある場合は、その CNAME を、EnterpriseEnrollment.contoso.com を enterpriseenrollment-s.manage.microsoft.com にリダイレクトする CNAME に置き換えることをお勧めします。 manage.microsoft.com endpoint エンドポイントは将来のリリースで登録に使用されなくなる予定であるため、このように変更することが推奨されます。

    検証済みドメインが複数ある場合、ドメインごとに CNAME レコードを作成します。 CNAME リソース レコードには次の情報を含める必要があります。

  |種類:|ホスト名|指定先|TTL|
  |--------|-------------|-------------|-------|
  |CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 時間|
  |CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 時間|

  `EnterpriseEnrollment-s.manage.microsoft.com` – Intune サービスへのリダイレクトと電子メールのドメイン名によるドメイン認識をサポートします

  `EnterpriseRegistration.windows.net` – 職場または学校のアカウントを使用して Azure Active Directory に登録される Windows 8.1 および Windows 10 Mobile デバイスをサポートします

  会社でユーザーの資格情報に複数のドメインを使用する場合は、各ドメインに CNAME レコードを作成します。

  たとえば、会社の Web サイトが contoso.com の場合、EnterpriseEnrollment.contoso.com を EnterpriseEnrollment-s.manage.microsoft.com にリダイレクトする CNAME を DNS に作成します。 DNS レコードの変更が反映されるまでには、最大で 72 時間かかります。 DNS レコードの変更が反映されるまで、Intune で DNS の変更を確認することはできません。

3.  **CNAME を確認する**<br>[Intune 管理コンソール](http://manage.microsoft.com)で、**[管理]** &gt; **[モバイル デバイス管理]** &gt; **[Windows Phone]** の順に選択します。 **[検証済みドメイン名の指定]** ボックスに会社の Web サイトの検証済みドメインの URL を入力し、**[自動検出のテスト]** を選択します。

    ![[Windows 用モバイル デバイス管理のセットアップ] ダイアログ ボックス](../media/windows-phone-enrollment.png)

4.  **オプションの手順**<br>**サイドローディング キーの追加**の手順は、Windows 10 には必要ありません。 **コード署名証明書のアップロード**の手順は、Windows ストアでは使用できない基幹業務 (LOB) アプリをデバイスに配信する場合にのみ必要です。

5.  **デバイスを登録して会社のリソースへのアクセスを取得する方法をユーザーに知らせる**

    エンドユーザー用の登録手順については、「[Intune に Windows デバイスを登録する](../enduser/enroll-your-device-in-intune-windows.md)」を参照してください。 また、[デバイスを Intune に登録した場合に IT 管理者が確認できるもの](../enduser/what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows.md)も知らせることをお勧めします。

    その他のエンドユーザー タスクの詳細については、次の記事を参照してください。
    - [Microsoft Intune の使用に関するエンドユーザーへの通知内容](what-to-tell-your-end-users-about-using-microsoft-intune.md)
    - [Windows デバイス向けエンド ユーザー ガイダンス](../enduser/using-your-windows-device-with-intune.md)

デバイスにポータル サイトを展開する場合を除き、追加の作業は必要ありません。  管理コンソールでの手順 2. および 3. は、無視してかまいません。



<!--HONumber=Dec16_HO2-->


