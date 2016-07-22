---
title: "カスタムのドメイン名を構成する | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2382f36f-13d8-4a32-81ad-6cfa604889c3
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed26d65b98a0ae1bbc4fbac682fb53fddd50b4e5
ms.openlocfilehash: a202f06fef0bc8b7eec730728ec10e5fbf234902


---


# カスタムのドメイン名を構成する

既定では、Intune は、最初にサービスをサブスクライブしたときに作成された **<domain>.onmicrosoft.com** ドメイン名を使用します。 組織でカスタムのドメインを保有している場合、Intune のインスタンスを構成して、サブスクリプションで提供されたドメイン名ではなく、カスタムのドメインを使用できます。

新しいユーザー アカウントを作成する、または、オンプレミスの Active Directory からアカウントを同期する前に、.onmicrosoft.com ドメインのみを使用するか、1 つまたは複数のカスタム ドメイン名を使用するかを決定することを強くお勧めします。 ユーザーを追加する前にカスタム ドメインの構成を行い、他のドメイン リソースにアクセスするときと同じ資格情報でユーザーがサインインできるようにしておくと、サブスクリプションのユーザー ID 管理を単純化できます。

Microsoft のクラウドベースのサービスにサブスクライブすると、そのサービスのインスタンスが Microsoft [Azure AD テナント](http://technet.microsoft.com/library/jj573650.aspx#BKMK_WhatIsAnAzureADTenant)になり、Azure AD によって、クラウドベースのサービスの ID サービスとディレクトリ サービスが提供されます。 Intune で組織のカスタム ドメイン名の使用を構成するタスクは、他の Azure AD テナントの場合と同じため、[ドメインの追加](https://azure.microsoft.com/documentation/articles/active-directory-add-domain/)に関する記事の情報と手順を利用できます。

> [!TIP]
> Microsoft のクラウドベースのサービスでカスタム ドメインを使用する方法の詳細については、「[Azure Active Directory でのカスタム ドメイン名の概念の概要](https://azure.microsoft.com/documentation/articles/active-directory-add-domain-concepts/)」をご覧ください。

### 次の手順
これで終了です。 *Intune のクイック スタート ガイド*の手順 2 が完了しました。

>[!div class="step-by-step"]

>[&larr;**Intune にサインインする**](.\start-with-a-paid-subscription-to-microsoft-intune-step-1.md)     [**Intune にユーザーを追加する** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-3.md)  



<!--HONumber=Jun16_HO4-->


