---
title: "Intune でのアプリ ベースの条件付きアクセス"
description: "Intune でのアプリ ベースの条件付きアクセスがどのように機能するのかについて、その概念を説明します。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 05/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b399fba0-5dd4-4777-bc9b-856af038ec41
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0a813dbaff7db5bf07e3573fb9bf539f6a4676f0
ms.sourcegitcommit: 82088d297eef629e3da6011681ead442ae7e25f7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2017
---
# <a name="app-based-conditional-access-with-intune"></a>Intune でのアプリ ベースの条件付きアクセス

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

[Intune アプリ保護ポリシー](app-protection-policy.md)を使用すると、Intune に登録されているデバイス上の会社のデータを保護できます。 Intune での管理対象に登録されていない従業員所有のデバイスでも、アプリ保護ポリシーを使用できます。 この場合、会社はデバイスを管理しなくても、会社のデータとリソースが保護されるようにする必要はあります。

アプリ ベースの条件付きアクセスとモバイル アプリ管理は、Intune アプリ保護ポリシーをサポートするモバイル アプリのみが Exchange Online やその他の Office 365 サービスにアクセスできるようにすることで、セキュリティ層を追加します。

> [!NOTE]
> 管理対象アプリは、アプリ保護ポリシーが適用されたアプリであり、Intune で管理できます。

Microsoft Outlook アプリのみが Exchange Online にアクセスできるようにすると、iOS や Android 上の組み込みメール アプリをブロックできます。 また、Intune アプリ保護ポリシーを適用していないアプリが SharePoint Online にアクセスするのをブロックできます。

## <a name="prerequisites"></a>必要条件
アプリ ベースの条件付きアクセス ポリシーを作成するには、以下を保有している必要があります。

- **Enterprise Mobility + Security (EMS)** または **Azure Active Directory (AD) Premium サブスクリプション**
- ユーザーは、EMS または Azure AD のライセンスを取得している必要があります

詳細については、「[Enterprise Mobility pricing](https://www.microsoft.com/cloud-platform/enterprise-mobility-pricing)」(Enterprise Mobility の価格) または「[Azure Active Directory の価格](https://azure.microsoft.com/pricing/details/active-directory/)」を参照してください。

## <a name="supported-apps"></a>サポートされているアプリ

アプリ ベースの条件付きアクセスをサポートしているアプリのリストについては、「[Azure Active Directory の条件付きアクセスに関するテクニカル リファレンス」のドキュメント](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-technical-reference)をご覧ください。

アプリ ベースの条件付きアクセスは[基幹業務 (LOB) アプリもサポート](https://docs.microsoft.com/intune-classic/deploy-use/block-apps-with-no-modern-authentication)していますが、LOB アプリが [Office 365 の先進認証](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a)を使用している必要があります。

## <a name="how-app-based-conditional-access-works"></a>アプリ ベースの条件付きアクセスのしくみ

この例では、管理者は Outlook アプリにアプリ保護ポリシーを適用し、その後、会社の電子メールへのアクセス時に使用できるアプリの承認済みリストに Outlook アプリを追加する条件付きアクセス ルールを適用しています。

> [!NOTE]
> 下のフローチャートの構造は、他の管理対象アプリでも使用できます。

![Intune フローチャートを使用したアプリ ベースの条件付きアクセス](./media/ca-intune-common-ways-3.png)

1.  ユーザーは、Outlook アプリから Azure AD の認証を試みます。

2.  ユーザーは、初回認証時、ブローカー アプリのインストールのためにアプリ ストアにリダイレクトされます。 ブローカー アプリは、iOS の場合は Microsoft Authenticator、Android デバイスの場合は Microsoft ポータル サイトになります。

 ユーザーがネイティブの電子メール アプリを使おうとすると、アプリ ストアにリダイレクトされ、その後 Outlook アプリのインストールにリダイレクトされます。

3.  ブローカー アプリがデバイスにインストールされます。

4.  ブローカー アプリが、Azure AD にデバイス レコードを作成する Azure AD 登録プロセスを開始します。 これは、モバイル デバイス管理 (MDM) の登録プロセスとは異なりますが、条件付きアクセス ポリシーをデバイスに適用するためにこのレコードが必要となります。

5.  ブローカー アプリがアプリの ID を確認します。 セキュリティ層があるため、ブローカー アプリはユーザーによるアプリの使用が認証されているかどうかを検証できます。

6.  ブローカー アプリが、ポリシーの承認済みリストに登録されているかどうかをチェックするユーザー認証プロセスの一部として、App Client ID を Azure AD に送信します。

7.  Azure AD が、ポリシーの承認済みリストに基づいて、ユーザーによるアプリの認証と使用を許可します。 アプリがリストに登録されていない場合、Azure AD はそのアプリへのアクセスを拒否します。

8.  Outlook アプリが Outlook クラウド サービスと通信して、Exchange Online との通信を開始します。

9.  Outlook クラウド サービスが Azure AD と通信して、ユーザーの Exchange Online サービス アクセス トークンを取得します。

10.  Outlook アプリが Exchange Online と通信して、ユーザーの会社の電子メールを取得します。

11.  会社の電子メールは、ユーザーのメールボックスに配信されています。

## <a name="next-steps"></a>次のステップ
[アプリベースの条件付きアクセス ポリシーを作成する](app-based-conditional-access-intune-create.md)

[最新の認証を使用していないアプリをブロックする](app-modern-authentication-block.md)
