---
title: "Windows デバイスの登録"
titleSuffix: Intune Azure preview
description: "Intune Azure プレビュー: Windows デバイスの Intune モバイル デバイス管理 (MDM) を有効にします。"
keywords: 
author: nathbarn
manager: nathbarn
ms.date: 03/21/17
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f94dbc2e-a855-487e-af6e-8d08fabe6c3d
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 771aed4e1c57171183b9a9ea7d9e0f702dc1859c
ms.openlocfilehash: b62a5704605f5cf89efb4052180f09f88eb788e1
ms.lasthandoff: 04/06/2017


---

# <a name="enroll-windows-devices"></a>Windows デバイスの登録

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

このトピックは IT 管理者がユーザーの Windows の登録を簡略化する際に役立ちます。  Windows デバイスは追加の手順なしに登録できますが、ユーザーのため、登録をより簡単にすることができます。

2 つの要素によって、Windows デバイスの登録方法が決まります。
- **Azure Active Directory Premium を使用していますか?** <br>[Azure AD Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) は、Enterprise Mobility + Security およびその他のライセンス プランに付属します。
- **どのバージョンの Windows クライアントが登録されますか?** <br>Windows 10 デバイスは、職場または学校のアカウントを追加すると自動的に登録できます。 以前のバージョンでは、会社ポータル アプリを使用して登録する必要があります。

||**Azure AD Premium**|**その他の AD**|
|----------|---------------|---------------|  
|**Windows 10**|[自動登録](#enable-windows-10-automatic-enrollment) |[ユーザー登録](#enable-windows-enrollment-without-azure-ad-premium)|
|**以前の Windows バージョン**|[ユーザー登録](#enable-windows-enrollment-without-azure-ad-premium)|[ユーザー登録](#enable-windows-enrollment-without-azure-ad-premium)|

[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## <a name="enable-windows-enrollment-without-azure-ad-premium"></a>Azure AD Premium なしの Windows 登録を有効にする
Azure AD Premium の自動登録なしで、ユーザー自身にデバイスを登録させることができます。 ライセンスをユーザーのアカウントに割り当てると、ユーザーはそのアカウントを Windows デバイスに追加してそのデバイスを管理対象に登録できるようになります。 DNS エイリアス (CNAME レコード タイプ) を作成すると、ユーザーがデバイスを簡単に登録できるようになります。 DNS の CNAME リソース レコードを作成すると、ユーザーは Intune サーバー名を入力することなく Intune に接続して登録できるようになります。

**手順 1: CNAME を作成する** (省略可能)<br>
会社のドメインの CNAME DNS リソース レコードを作成します。 たとえば、会社の Web サイトが contoso.com の場合、EnterpriseEnrollment.contoso.com を enterpriseenrollment-s.manage.microsoft.com にリダイレクトする CNAME を DNS に作成します。

CNAME DNS エントリの作成は省略可能ですが、CNAME レコードにより登録が簡単になります。 CNAME レコードの登録が見つからない場合、ユーザーは手動で MDM サーバー名 enrollment.manage.microsoft.com を入力するように求められます。

|型|ホスト名|指定先|TTL|  
|----------|---------------|---------------|---|
|CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com| 1 時間|

複数の UPN サフィックスがある場合は、各ドメイン名について 1 つの CNAME レコードを作成し、それぞれで EnterpriseEnrollment s.manage.microsoft.com をポイントする必要があります。 たとえば、Contoso 社でユーザーが name@contoso.com を使用しており、電子メール/UPN として name@us.contoso.com と name@eu.constoso.com も使用している場合、Contoso の DNS 管理者は次の CNAME を作成する必要があります。

|型|ホスト名|指定先|TTL|  
|----------|---------------|---------------|---|
|CNAME|EnterpriseEnrollment.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com|1 時間|
|CNAME|EnterpriseEnrollment.us.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com|1 時間|
|CNAME|EnterpriseEnrollment.eu.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com| 1 時間|

`EnterpriseEnrollment-s.manage.microsoft.com` – Intune サービスへのリダイレクトと電子メールのドメイン名によるドメイン認識をサポートします

DNS レコードの変更が反映されるまでには、最大で 72 時間かかります。 DNS レコードの変更が反映されるまで、Intune で DNS の変更を確認することはできません。

**手順 2: CNAME を確認する** (省略可能)<br>
Azure Intune ポータルで、**[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。 [Intune] ブレードで、**[デバイスの登録]**  >  **[Windows Enrollment (Windows 登録)]** を選択します。 **[検証済みドメイン名の指定]** ボックスに会社の Web サイトの検証済みドメインの URL を入力し、**[自動検出のテスト]** を選択します。

## <a name="tell-users-how-to-enroll-windows-devices"></a>Windows デバイスの登録方法をユーザーに通知する
ユーザーに、Windows デバイスを登録する方法とデバイスが管理されるとどうなるかを伝えます。 エンドユーザー用の登録手順については、「[Intune に Windows デバイスを登録する](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-windows)」を参照してください。 また、ユーザーには、[IT 管理者がユーザーのデバイスに関して確認できる情報](https://docs.microsoft.com/intune/enduser/what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows)に関するページも案内してください。

エンドユーザー タスクの詳細については、「[Microsoft Intune を使用したエンドユーザー エクスペリエンスに関するリソース](https://docs.microsoft.com/intune/deploy-use/how-to-educate-your-end-users-about-microsoft-intune)」を参照してください。

