---
title: "Microsoft Intune を使用して Windows デバイスの管理をセットアップする | Microsoft Docs"
description: "Microsoft Intune で Windows デバイスのモバイル デバイス管理 (MDM) を有効にします。"
keywords: 
author: staciebarker
manager: stabar
ms.date: 02/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9a18c0fe-9f03-4e84-a4d0-b63821bf5d25
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 45c32cf08e4d6fd570af287ed64411edc9d9b394
ms.openlocfilehash: e020ac2a4f600a94e7409e04c4c48f0c405c56cf


---

# <a name="set-up-windows-device-management"></a>Windows デバイスの管理をセットアップする

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Windows デバイスの登録を設定するには、以下のいずれかの方法を使用します。

- **[Azure Active Directory Premium による Windows 10 と Windows 10 Mobile の自動登録](#set-up-windows-10-and-windows-10-mobile-automatic-enrollment-with-azure-active-directory-premium)** 
 -  この方法は、Windows 10 および Windows 10 Mobile デバイスにのみ適用できます。
 -  この方法を使用するには、Azure Active Directory Premium を所有している必要があります。 所有していない場合は、Windows 8.1 および Windows Phone 8.1 向けの登録方法を使用してください。
 -  自動登録を有効にしない場合は、Windows 8.1 および Windows Phone 8.1 向けの登録方法を使用してください。


- **[CNAME の構成による Windows 8.1 および Windows Phone 8.1 の登録](#set-up-windows-8--1-and-windows-phone-8--1-enrollment-by-configuring-cname)** 
 - Windows 8.1 および Windows Phone 8.1 デバイスを登録するには、この方法を使用する必要があります。

[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## <a name="set-up-windows-81-and-windows-phone-81-enrollment-by-configuring-cname"></a>CNAME の構成によって Windows 8.1 および Windows Phone 8.1 の登録を設定する
Intune ポータル サイトを使用することで、ユーザーがデバイスをインストールして登録できるようにします。 DNS の CNAME リソース レコードを作成すると、ユーザーはサーバー名を入力することなく Intune に接続して登録できるようになります。

1. **Intune をセットアップする**<br>
**Microsoft Intune** を[モバイル デバイス管理 (MDM) 機関に設定](prerequisites-for-enrollment.md#step-2-set-mdm-authority)して、MDM の設定を行うことにより、モバイル デバイス管理を準備します (この作業をまだ行っていない場合)。

2. **CNAME を作成する** (省略可能)<br>
会社のドメインの **CNAME** DNS リソース レコードを作成します。 たとえば、会社の Web サイトが contoso.com の場合、EnterpriseEnrollment.contoso.com を enterpriseenrollment-s.manage.microsoft.com にリダイレクトする CNAME を DNS に作成します。

    CNAME DNS エントリの作成は省略可能ですが、CNAME レコードにより登録が簡単になります。 CNAME レコードの登録が見つからない場合、ユーザーは手動で MDM サーバー名 enrollment.manage.microsoft.com を入力するように求められます。    

    EnterpriseEnrollment.contoso.com を manage.microsoft.com にリダイレクトする CNAME が DNS に既にある場合は、その CNAME を、EnterpriseEnrollment.contoso.com を enterpriseenrollment-s.manage.microsoft.com にリダイレクトする CNAME に置き換えることをお勧めします。 manage.microsoft.com endpoint エンドポイントは将来のリリースで登録に使用されなくなる予定であるため、このように変更することが推奨されます。

    CNAME リソース レコードには次の情報を含める必要があります。

  |種類:|ホスト名|指定先|TTL|
  |--------|-------------|-------------|-------|
  |CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 時間|
  |CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 時間|

  `EnterpriseEnrollment-s.manage.microsoft.com` – Intune サービスへのリダイレクトと電子メールのドメイン名によるドメイン認識をサポートします

  `EnterpriseRegistration.windows.net` – 職場または学校のアカウントを使用して Azure Active Directory に登録される Windows 8.1 および Windows 10 Mobile デバイスをサポートします

  会社でユーザーの資格情報に複数のドメインを使用する場合は、各ドメインに CNAME レコードを作成します。

  たとえば、会社の Web サイトが contoso.com の場合、EnterpriseEnrollment.contoso.com を EnterpriseEnrollment-s.manage.microsoft.com にリダイレクトする CNAME を DNS に作成します。 DNS レコードの変更が反映されるまでには、最大で 72 時間かかります。 DNS レコードの変更が反映されるまで、Intune で DNS の変更を確認することはできません。

3.  **CNAME を確認する**<br>[Intune 管理コンソール](http://manage.microsoft.com)で、**[管理]** &gt; **[モバイル デバイス管理]** &gt; **[Windows]** の順に選択します。 **[検証済みドメイン名の指定]** ボックスに会社の Web サイトの検証済みドメインの URL を入力し、**[自動検出のテスト]** を選択します。

4.  **ユーザーに、デバイスを登録する方法とデバイスが管理されるとどうなるかを伝える**

    エンドユーザー用の登録手順については、「[Intune に Windows デバイスを登録する](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-windows)」を参照してください。

    エンドユーザー タスクの詳細については、「[Microsoft Intune を使用したエンドユーザー エクスペリエンスに関するリソース](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune)」を参照してください。


### <a name="see-also"></a>関連項目
[Microsoft Intune でデバイスを登録するための前提条件](prerequisites-for-enrollment.md)



<!--HONumber=Feb17_HO2-->


