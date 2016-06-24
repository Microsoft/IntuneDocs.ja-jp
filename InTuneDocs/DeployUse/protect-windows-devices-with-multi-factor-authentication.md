---
# required metadata

title: 多要素認証を使用して Windows デバイスを保護する | Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 9b4f197d-bc10-4bee-91c9-19bcc8287d36

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Protect Windows devices with multi-factor authentication
Microsoft Intune には多要素認証 (MFA) 機能があり、会社のリソースをセキュリティ保護に利用できます。 MFA では、ユーザー名とパスワードだけでなく、テキスト認証などの認証要素が要求されます。 Intune では、Windows 8.1 以降、Windows Phone 8.1、Windows 10 のデスクトップとモバイル デバイスの登録で、MFA を利用できます。 

## 内部設置型インフラストラクチャの ADFS MFA の要件
Multi-Factor Authentication をセットアップするうえで必要なものは次のとおりです。

-   **ADFS サーバーが参加している Active Directory ドメイン。**

-   **Active Directory フェデレーション サービス (ADFS)、構成されているサーバー MFA のです。** ADFS サーバーとしてセットアップされた、Windows Server 2012 R2 を実行しているサーバー。 詳細については、「[Secure cloud and on-premises resources using Azure Multi-Factor Authentication Server with Windows Server 2012 R2 AD FS (Azure Multi-Factor Authentication Server と Windows Server 2012 R2 AD FS を使用したクラウド リソースと社内リソースのセキュリティ保護)](https://azure.microsoft.com/en-us/documentation/articles/multi-factor-authentication-get-started-adfs-w2k12/)」を参照してください。

上記のすべてのサーバーは、「[Windows Server 2012 R2 のシステム要件とインストール情報](http://technet.microsoft.com/library/dn303418.aspx)」に記載されているシステム要件を満たす必要があります。.

#### MFA (Intune あり)
組織に Active Directory フェデレーション サービス (ADFS) が構成された Active Directory ドメインを含む内部設置型の IT インフラストラクチャが存在する場合、フェデレーション サーバーで MFA を構成して、Intune 登録のために MFA を有効にできます。 Intune で MFA を構成すると、登録時にユーザーは一度認証すれば、その後、毎回 MFA プロセスを繰り返さなくても、企業リソースにアクセスできます。

>[!NOTE]
>MFA は、ADFS サーバーでユーザーまたはグループごとに要求されます。  

#### MFA (Intune なし)
フェデレーション サーバーで MFA を構成しても、Intune 登録のために MFA を有効にしていない場合、ユーザーは (デバイス登録時だけでなく) 企業リソースにアクセスするたびに MFA を使用する必要があります。

また、Azure Active Directory (AAD) MFA を使用し、ユーザーが企業リソースにアクセスするたびに MFA を要求することもできます。この要求はユーザーごとに有効にできます。 AAD MFA は、内部設置型の IT インフラストラクチャを一切必要としないクラウド サービスです。 AAD MFA 設定の詳細については、「[クラウドでの Azure Multi-Factor Authentication Server の概要](https://azure.microsoft.com/en-us/documentation/articles/multi-factor-authentication-get-started-cloud/)」をご覧ください。」を参照してください。.

## Windows デバイスの登録時に ADFS MFA が必要である
ADFS で MFA を有効にする方法の詳細については、「[追加の多要素認証による個人情報アプリケーションのリスク管理](http://technet.microsoft.com/library/dn280949.aspx)」を参照してください。.

## Intune でデバイス登録 MFA をセットアップする
>[!Important]  
>Windows デバイスの Intune 登録で MFA を必要とするには、Azure AD テナントまたはオンプレミス環境で MFA を有効にします。 有効にしないと、Windows デバイスを登録しようとしたユーザーに、あるいは (Azure AD 参加中の自動登録が構成されているとき) デバイスを Azure AD に参加させようとしたユーザーにエラー メッセージが表示されます。

1.  Intune 管理コンソールで、**[管理者]** &gt; **[モバイル デバイス管理]** &gt; **[多要素認証]** の順にクリックします。.

2.  **[多要素認証の構成]** をクリックし、**[多要素認証の有効化]** をクリックします。.



<!--HONumber=May16_HO1-->


