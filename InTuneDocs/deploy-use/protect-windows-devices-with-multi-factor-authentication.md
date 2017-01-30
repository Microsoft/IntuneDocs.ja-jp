---
title: "Windows の多要素認証 | Microsoft Docs"
description: "Intune には多要素認証 (MFA) 機能があり、会社のリソースのセキュリティ保護に利用できます。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9b4f197d-bc10-4bee-91c9-19bcc8287d36
ms.reviewer: vinaybha
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e7d1760a10e63233fe7cc7f6fd57a68c5283647c
ms.openlocfilehash: cc60ffb2cd7a1d0cad141712ba7e2341954b1f02


---

# <a name="protect-windows-devices-with-multi-factor-authentication"></a>Protect Windows devices with multi-factor authentication

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune には多要素認証 (MFA) 機能があり、会社のリソースをセキュリティ保護に利用できます。 MFA には、ユーザー名とパスワードだけでなくテキスト認証などの認証の要素が必要です。 Intune では、Windows 8.1 以降、Windows Phone 8.1、Windows 10 のデスクトップとモバイル デバイスの登録で、MFA を利用できます。

>[!NOTE]
>
>MFA は、ADFS サーバーでユーザーまたはグループごとに要求されます。  


## <a name="on-premises-infrastructure-requirements-for-adfs-mfa"></a>内部設置型インフラストラクチャの ADFS MFA の要件
Multi-Factor Authentication をセットアップするうえで必要なものは次のとおりです。

-   「[Windows デバイスの管理をセットアップする](set-up-windows-device-management-with-microsoft-intune.md)」に説明されている自動登録。
-   **ADFS サーバーが参加している Active Directory ドメイン。**

-   **MFA 用に構成された Active Directory フェデレーション サービス (ADFS) サーバー。** Windows Server 2012 R2 を実行し、ADFS サーバーとしてセットアップされたサーバー。 詳細については、「[Secure cloud and on-premises resources using Azure Multi-Factor Authentication Server with Windows Server 2012 R2 AD FS (Azure Multi-Factor Authentication Server と Windows Server 2012 R2 AD FS を使用したクラウド リソースと社内リソースのセキュリティ保護)](https://azure.microsoft.com/en-us/documentation/articles/multi-factor-authentication-get-started-adfs-w2k12/)」を参照してください。

サーバーは、「[Windows Server 2012 R2 のシステム要件とインストール情報](http://technet.microsoft.com/library/dn303418.aspx)」に記載されているシステム要件を満たす必要があります。

 


#### <a name="mfa-with-intune"></a>MFA (Intune あり)
組織に Active Directory フェデレーション サービス (ADFS) が構成された Active Directory ドメインを含むオンプレミスの IT インフラストラクチャが存在する場合、フェデレーション サーバーで MFA をセットアップして、Intune 登録のために MFA を有効にできます。 Intune で MFA を構成すると、ユーザーは登録時に一度認証すれば、その後、毎回 MFA プロセスを繰り返さなくても、企業リソースを使用できます。

>[!NOTE]
>
>MFA は、ADFS サーバーでユーザーまたはグループごとに要求されます。  

#### <a name="mfa-without-intune"></a>MFA (Intune なし)
フェデレーション サーバーで MFA をセットアップしても、Intune 登録のために MFA を有効にしていない場合、ユーザーは (デバイス登録時だけでなく) 企業リソースにアクセスするたびに MFA を使用する必要があります。

また、Azure Active Directory (Azure AD) MFA を使用し、ユーザーが企業リソースにアクセスするたびに、ユーザーごとに MFA を要求することもできます。 Azure AD MFA は、オンプレミスの IT インフラストラクチャを一切必要としないクラウド サービスです。 Azure AD MFA 設定の詳細については、「[クラウドでの Azure Multi-Factor Authentication Server の概要](https://azure.microsoft.com/en-us/documentation/articles/multi-factor-authentication-get-started-cloud/)」をご覧ください。

## <a name="requiring-adfs-mfa-during-enrollment-of-windows-devices"></a>Windows デバイスの登録時に ADFS MFA が必要である
ADFS で MFA を有効にする方法の詳細については、「 [追加の多要素認証による個人情報アプリケーションのリスク管理](http://technet.microsoft.com/library/dn280949.aspx)」を参照してください。

## <a name="set-up-device-enrollment-mfa-in-intune"></a>Intune でデバイス登録 MFA をセットアップする
>[!Important]  
>Windows デバイスの Intune 登録で MFA を必要とするには、Azure AD テナントまたはオンプレミス環境で MFA を有効にします。 有効にしない場合は、Azure AD 参加中の自動登録がセットアップされていると、ユーザーが Windows デバイスを登録しようとしたとき、またはデバイスを Azure AD に参加させようとしたときに、エラー メッセージが表示されます。

1.  Intune 管理コンソールで、**[管理]** &gt; **[モバイル デバイス管理]** &gt; **[多要素認証]** の順に選びます。

2.  **[多要素認証の構成]** を選び、**[多要素認証の有効化]** を選びます。



<!--HONumber=Dec16_HO5-->


