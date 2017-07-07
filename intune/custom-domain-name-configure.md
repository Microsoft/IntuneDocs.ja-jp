---
title: "カスタムのドメイン名を構成する"
description: "Intune サブスクリプションのカスタム ドメイン名を追加します"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 06/07/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2382f36f-13d8-4a32-81ad-6cfa604889c3
ms.reviewer: angerobe
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d75292ce60eb1db232aed12fc80a7cbccc063fb4
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2017
---
# <a name="configure-a-custom-domain-name"></a>カスタムのドメイン名を構成する

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

このトピックでは、管理者が DNS CNAME を作成して、ログオン エクスペリエンスの簡略化とカスタマイズを行う方法を説明します。

組織が Intune などの Microsoft クラウド ベース サービスにサインアップすると、**yourdomain.onmicrosoft.com** のように Azure Active Directory (AD) でホストされる最初のドメイン名が付与されます。 この例で、**yourdomain** はサインアップ時に選択したドメイン名、**onmicrosoft.com** はサブスクリプションに追加するアカウントに割り当てられるサフィックスです。 組織でカスタムのドメインを保有している場合、Intune のインスタンスを構成して、サブスクリプションで提供されたドメイン名ではなく、カスタムのドメインを使用できます。

ユーザー アカウントを作成する、またはオンプレミスの Active Directory を同期する前に、.onmicrosoft.com ドメインのみを使用するか、1 つ以上のカスタム ドメイン名を追加するかを決定することを強くお勧めします。 ユーザーを追加する前にカスタム ドメインの構成を行い、他のドメイン リソースにアクセスするときと同じ資格情報でユーザーがサインインできるようにしておくと、サブスクリプションのユーザー ID 管理を単純化できます。

Microsoft のクラウドベースのサービスにサブスクライブすると、そのサービスのインスタンスが Microsoft [Azure AD テナント](http://technet.microsoft.com/library/jj573650.aspx#BKMK_WhatIsAnAzureADTenant)になり、Azure AD によって、クラウドベースのサービスの ID サービスとディレクトリ サービスが提供されます。 Intune で組織のカスタム ドメイン名の使用を構成するタスクは、他の Azure AD テナントの場合と同じため、[ドメインの追加](https://azure.microsoft.com/documentation/articles/active-directory-add-domain/)に関する記事の情報と手順を利用できます。

> [!TIP]
> Microsoft のクラウドベースのサービスでカスタム ドメインを使用する方法の詳細については、「[Azure Active Directory でのカスタム ドメイン名の概念の概要](https://azure.microsoft.com/documentation/articles/active-directory-add-domain-concepts/)」をご覧ください。

この最初のドメイン名を変更または削除することはできません。 ただし、Intune で使用するカスタム ドメイン名を追加、確認、または削除することはできます。カスタム ドメインがあると、ビジネス アイデンティティを維持するために役立ちます。

## <a name="to-add-and-verify-your-custom-domain"></a>カスタム ドメインを追加して確認するには

1. [Office 365 管理ポータル](https://portal.office.com/Admin/Default.aspx)を開き、管理者アカウントにサインインします。

2. ナビゲーション ウィンドウの **[設定]** &gt; **[ドメイン]** を選択します。

3. **[ドメインの追加]** を選択し、カスタム ドメイン名を入力します。

4. **[ドメインの確認]** ダイアログ ボックスが開き、DNS ホスティング プロバイダーに TXT レコードを作成する値が表示されます。
    - **GoDaddy ユーザー**: Office 365 管理ポータルから GoDaddy のログイン ページにリダイレクトされます。 資格情報を入力し、ドメインの変更アクセス許可に同意すると、TXT レコードが自動的に作成されます。 または [TXT レコードを作成](https://support.office.com/article/Create-DNS-records-at-GoDaddy-for-Office-365-f40a9185-b6d5-4a80-bb31-aa3bb0cab48a)できます。
    - **Register.com ユーザー**: この[ステップ バイ ステップの指示](https://support.office.com/article/Create-DNS-records-at-Register-com-for-Office-365-55bd8c38-3316-48ae-a368-4959b2c1684e#BKMK_verify)に従って、TXT レコードを作成します。

カスタム ドメインを追加し、確認する手順は、[Azure Active Directory でも実行](https://azure.microsoft.com/documentation/articles/active-directory-add-domain/)できます。

詳しくは、「[Office 365 の最初の onmicrosoft.com ドメインの概要](https://support.office.com/article/About-your-initial-onmicrosoft-com-domain-in-Office-365-B9FC3018-8844-43F3-8DB1-1B3A8E9CFD5A)」をご覧ください
