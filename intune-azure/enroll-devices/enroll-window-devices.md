---
title: "Windows デバイスを登録する | Intune Azure プレビュー | Microsoft Docs"
description: "Intune Azure プレビュー: Windows デバイスの Intune モバイル デバイス管理 (MDM) を有効にします。"
keywords: 
author: staciebarker
manager: stabar
ms.date: 02/09/17
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f94dbc2e-a855-487e-af6e-8d08fabe6c3d
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 45c32cf08e4d6fd570af287ed64411edc9d9b394
ms.openlocfilehash: ec623e7d102e8a8ddf1cc86a750f592ca765cfce


---

# <a name="enroll-windows-devices"></a>Windows デバイスの登録 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Windows デバイスの登録を設定するには、以下のいずれかの方法を使用します。

- **[Azure Active Directory Premium による Windows 10 と Windows 10 Mobile の自動登録](#set-up-windows-10-and-windows-10-mobile-automatic-enrollment-with-azure-active-directory-premium)** 
 -  この方法は、Windows 10 および Windows 10 Mobile デバイスにのみ適用できます。
 -  この方法を使用するには、Azure Active Directory Premium を所有している必要があります。 所有していない場合は、Windows 8.1 および Windows Phone 8.1 向けの登録方法を使用してください。
 -  自動登録を有効にしない場合は、Windows 8.1 および Windows Phone 8.1 向けの登録方法を使用してください。


- **[CNAME の構成による Windows 8.1 および Windows Phone 8.1 の登録](#set-up-windows-8.1-and-windows-phone-8.1-enrollment-by-configuring-cname)** 
 - Windows 8.1 および Windows Phone 8.1 デバイスを登録するには、この方法を使用する必要があります。


## <a name="prerequisites"></a>必要条件

次の前提条件の一部が Intune Azure プレビューにまだ存在しない場合は、従来の Intune 管理コンソールから操作を行う必要があります。

- [カスタムのドメイン名を構成する](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-2)
- [モバイル デバイス管理 (MDM) 機関](set-mdm-authority.md)を **Microsoft Intune** に設定する
- [ポータル サイト アプリを構成する](/intune-azure/manage-apps/company-portal-app.md)
- ユーザーにライセンスを割り当てる

[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## <a name="set-up-windows-81-and-windows-phone-81-enrollment-by-configuring-cname"></a>CNAME の構成によって Windows 8.1 および Windows Phone 8.1 の登録を設定する

Intune ポータル サイトを使用することで、ユーザーがデバイスをインストールして登録できるようにします。 DNS の CNAME リソース レコードを作成すると、ユーザーはサーバー名を入力することなく Intune に接続して登録できるようになります。

1. **CNAME を作成する** (省略可能)<br>
 会社のドメインの **CNAME** DNS リソース レコードを作成します。 たとえば、会社の Web サイトが contoso.com の場合、EnterpriseEnrollment.contoso.com を enterpriseenrollment-s.manage.microsoft.com にリダイレクトする CNAME を DNS に作成します。

    CNAME DNS エントリの作成は省略可能ですが、CNAME レコードにより登録が簡単になります。 CNAME レコードの登録が見つからない場合、ユーザーは手動で MDM サーバー名 enrollment.manage.microsoft.com を入力するように求められます。

    EnterpriseEnrollment.contoso.com を manage.microsoft.com にリダイレクトする CNAME が DNS に既にある場合は、その CNAME を、EnterpriseEnrollment.contoso.com を enterpriseenrollment-s.manage.microsoft.com にリダイレクトする CNAME に置き換えることをお勧めします。 manage.microsoft.com endpoint エンドポイントは将来のリリースで登録に使用されなくなる予定であるため、このように変更することが推奨されます。

    検証済みドメインが複数ある場合、ドメインごとに CNAME レコードを作成します。 CNAME リソース レコードには次の情報を含める必要があります。

    CNAME リソース レコードには次の情報を含める必要があります。

  |種類:|ホスト名|指定先|TTL|
  |--------|-------------|-------------|-------|
  |CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 時間|
  |CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 時間|

  `EnterpriseEnrollment-s.manage.microsoft.com` – Intune サービスへのリダイレクトと電子メールのドメイン名によるドメイン認識をサポートします

  `EnterpriseRegistration.windows.net` – 職場または学校のアカウントを使用して Azure Active Directory に登録される Windows 8.1 および Windows 10 Mobile デバイスをサポートします

  会社でユーザーの資格情報に複数のドメインを使用する場合は、各ドメインに CNAME レコードを作成します。

  たとえば、会社の Web サイトが contoso.com の場合、EnterpriseEnrollment.contoso.com を EnterpriseEnrollment-s.manage.microsoft.com にリダイレクトする CNAME を DNS に作成します。 DNS レコードの変更が反映されるまでには、最大で 72 時間かかります。 DNS レコードの変更が反映されるまで、Intune で DNS の変更を確認することはできません。

2.  **CNAME を確認する**<br>[Intune 管理コンソール](http://manage.microsoft.com)で、**[管理]** &gt; **[モバイル デバイス管理]** &gt; **[Windows Phone]** の順に選択します。 **[検証済みドメイン名の指定]** ボックスに会社の Web サイトの検証済みドメインの URL を入力し、**[自動検出のテスト]** を選択します。

3.  **オプションの手順**<br>**サイドローディング キーの追加**の手順は、Windows 10 には必要ありません。 <br>**コード署名証明書のアップロード**の手順は、Windows ストアでは入手できない基幹業務 (LOB) アプリをデバイスに配信する場合にのみ必要です。

4.  **ユーザーに、デバイスを登録する方法とデバイスが管理されるとどうなるかを伝えます**。

    エンドユーザー用の登録手順については、「[Intune に Windows デバイスを登録する](https://docs.microsoft.com/en-us/intune/enduser/enroll-your-device-in-intune-windows)」を参照してください。 また、ユーザーには、[IT 管理者がユーザーのデバイスに関して確認できる情報](https://docs.microsoft.com/intune/enduser/what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows)に関するページを案内してください。

    エンドユーザー タスクの詳細については、「[Microsoft Intune を使用したエンドユーザー エクスペリエンスに関するリソース](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune)」を参照してください。

デバイスにポータル サイトを展開する場合を除き、追加の作業は必要ありません。  管理コンソールでの手順 2. および 3. は、無視してかまいません。



<!--HONumber=Feb17_HO2-->


