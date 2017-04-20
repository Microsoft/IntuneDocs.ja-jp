---
title: "Microsoft Intune を使用して Windows デバイスの管理をセットアップする | Microsoft Docs"
description: "Microsoft Intune で Windows デバイスのモバイル デバイス管理 (MDM) を有効にします。"
keywords: 
author: NathBarn
manager: angrobe
ms.date: 03/20/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9a18c0fe-9f03-4e84-a4d0-b63821bf5d25
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 771aed4e1c57171183b9a9ea7d9e0f702dc1859c
ms.openlocfilehash: f6014c5500b05762d123b2285ef859d67382e402
ms.lasthandoff: 04/06/2017


---

# <a name="set-up-windows-device-management"></a>Windows デバイスの管理をセットアップする

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Windows デバイスの登録を設定するには、以下のいずれかの方法を使用します。

- [**Azure Active Directory Premium による Windows 10 の自動登録**](#set-up-windows-10-and-windows-10-mobile-automatic-enrollment-with-azure-active-directory-premium)
 -  この方法は、Windows 10 デバイスでのみ使用できます。
 -  この方法を使用するには、Azure Active Directory Premium を所有している必要があります。
 -  自動登録を有効にしない場合は、Windows 8.1 および Windows Phone 8.1 向けの登録方法を使用してください。

- [**Azure AD Premium 自動登録なしで登録する**](#enable-windows-enrollment-without-azure-ad-premium)
 - Windows 8.1 および Windows Phone 8.1 デバイスを登録するには、この方法を使用する必要があります。
 - Azure Active Directory (AD) Premium を使用しない場合、Windows 8.1 以降のデバイスにはこの方法を利用できます。

[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## <a name="enable-windows-enrollment-without-automatic-enrollment"></a>自動登録なしの Windows 登録を有効にする
Azure AD Premium の自動登録なしで、ユーザー自身でデバイスをインストールおよび登録させることができます。 ライセンスをユーザーのアカウントに割り当てると、ユーザーはそのアカウントを Windows デバイスに追加してそのデバイスを管理対象に登録できるようになります。 DNS の CNAME リソース レコードを作成すると、ユーザーはサーバー名を入力することなく Intune に接続して登録できるようになります。

**手順 1: CNAME を作成する** (省略可能)<br>
会社のドメインの CNAME DNS リソース レコードを作成します。 たとえば、会社の Web サイトが contoso.com の場合、EnterpriseEnrollment.contoso.com を enterpriseenrollment-s.manage.microsoft.com にリダイレクトする CNAME を DNS に作成します。

CNAME DNS エントリの作成は省略可能ですが、CNAME レコードにより登録が簡単になります。 CNAME レコードの登録が見つからない場合、ユーザーは手動で MDM サーバー名 enrollment.manage.microsoft.com を入力するように求められます。

検証済みドメインが複数ある場合、ドメインごとに CNAME レコードを作成します。 CNAME リソース レコードには次の情報を含める必要があります。

CNAME リソース レコードには次の情報を含める必要があります。

|種類:|ホスト名|指定先|TTL|
|--------|-------------|-------------|-------|
|CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 時間|
|CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 時間|

`EnterpriseEnrollment-s.manage.microsoft.com` – Intune サービスへのリダイレクトと電子メールのドメイン名によるドメイン認識をサポートします

会社でユーザーの資格情報に複数のドメインを使用する場合は、各ドメインに CNAME レコードを作成します。

たとえば、会社の Web サイトが contoso.com の場合、EnterpriseEnrollment.contoso.com を EnterpriseEnrollment-s.manage.microsoft.com にリダイレクトする CNAME を DNS に作成します。 DNS レコードの変更が反映されるまでには、最大で 72 時間かかります。 DNS レコードの変更が反映されるまで、Intune で DNS の変更を確認することはできません。

**手順 2: CNAME を確認する** (省略可能)<br>
[Intune 管理コンソール](http://manage.microsoft.com)で、**[管理]** &gt; **[モバイル デバイス管理]** &gt; **[Windows]** の順に選択します。 **[検証済みドメイン名の指定]** ボックスに会社の Web サイトの検証済みドメインの URL を入力し、**[自動検出のテスト]** を選択します。

## <a name="tell-users-how-to-enroll-windows-devices"></a>Windows デバイスの登録方法をユーザーに通知する
ユーザーに、Windows デバイスを登録する方法とデバイスが管理されるとどうなるかを伝えます。
エンドユーザー用の登録手順については、「[Intune に Windows デバイスを登録する](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-windows)」を参照してください。 また、ユーザーには、[IT 管理者がユーザーのデバイスに関して確認できる情報](https://docs.microsoft.com/intune/enduser/what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows)に関するページを案内してください。

エンドユーザー タスクの詳細については、「[Microsoft Intune を使用したエンドユーザー エクスペリエンスに関するリソース](https://docs.microsoft.com/intune/deploy-use/how-to-educate-your-end-users-about-microsoft-intune)」を参照してください。

### <a name="see-also"></a>関連項目
[Microsoft Intune でデバイスを登録するための前提条件](prerequisites-for-enrollment.md)

