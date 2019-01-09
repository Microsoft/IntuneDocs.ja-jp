---
title: 最新の認証を使用していないアプリを Intune でブロックする
titleSuffix: Microsoft Intune
description: Microsoft Intune を使用した先進認証 (ADAL) を使用していないアプリのブロックについて説明します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 73db3070-d033-40fb-a8f1-58b9d198021e
ms.reviewer: chrisgre
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: dc9318d46892eab21e81c7eb2992f3476720abd1
ms.sourcegitcommit: 4e69a8664c289263490daa4c02bc6b81c33196e5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2018
ms.locfileid: "53642457"
---
# <a name="block-apps-that-do-not-use-modern-authentication-adal"></a>最新の認証を使用していないアプリをブロックする (ADAL)

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

アプリ保護ポリシーを使用したアプリ ベースの条件付きアクセスは、[先進認証](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a)を使用するアプリケーションに依存しています。これは OAuth2 の実装です。 最新のモバイルおよびデスクトップ用 Office アプリケーションでは、先進認証が使用されています。 しかし、基本認証やフォームベースの認証など、他の認証方式を使用しているサードパーティ製アプリや古い Office アプリもあります。

## <a name="block-apps"></a>アプリをブロックする

先進認証を使用していないアプリへのアクセスをブロックするには、次の方法をお勧めします。

- 最新ではない認証プロトコルをブロックするように ADFS 要求規則を設定します。 詳しい手順は、シナリオ 3 の[ブラウザー ベースのアプリケーションを除く Office 365 への外部アクセスをすべてブロックする方法](https://technet.microsoft.com/library/dn592182.aspx)に関するページを参照してください。
- **Exchange Online と SharePoint Online** では、Azure Active Directory の条件付きアクセスを使用し、SharePoint Online に対して PowerShell コマンドレット Set-SPOTenant を使用します。 手順について詳しくは、「[SharePoint Online と Exchange Online に Azure Active Directory の条件付きアクセスを設定する](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-no-modern-authentication#legacy-authentication-protocols)」をご覧ください。


>[!IMPORTANT]
>アプリ ベースの CA は、Azure Active Directory (Azure AD) 証明書ベースの認証と併用することはできません。 同時に使用できるのは、いずれかの構成のみです。

## <a name="next-steps"></a>次の手順

- [Intune を使用したアプリ ベースの条件付きアクセス](app-based-conditional-access-intune.md)
