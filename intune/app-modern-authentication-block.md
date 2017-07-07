---
title: "最新の認証を使用していないアプリを Intune でブロックする"
description: 
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 05/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 73db3070-d033-40fb-a8f1-58b9d198021e
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3fbdb9d6e7e1869aba12b3639b8e887401491a79
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2017
---
# <a name="block-apps-that-do-not-use-modern-authentication-adal"></a>最新の認証を使用していないアプリをブロックする (ADAL)

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

アプリ保護ポリシーを使用したアプリ ベースの条件付きアクセスは、OAuth2 の実装である[最新の認証](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a)を使用するアプリケーションに依存しています。 最新の Office モバイル アプリとデスクトップ アプリケーションは最新の認証を使用していますが、基本認証やフォームベースの認証など、他の認証方式を使用しているサードパーティ製アプリや古い Office アプリもあります。

このようなアプリに対するアクセスをブロックするには、以下を推奨します。

* 最新ではない認証プロトコルをブロックするように ADFS 要求規則を設定します。 詳しい手順は、シナリオ 3 の[ブラウザー ベースのアプリケーションを除く Office 365 への外部アクセスをすべてブロックする方法](https://technet.microsoft.com/library/dn592182.aspx)に関するページを参照してください。
* **SharePoint Online** では、PowerShell コマンドレット [Set-SPOTenant](https://technet.microsoft.com/library/fp161390.aspx) を使用して従来の認証プロトコルのプロパティを false に設定することで、SharePoint Online サービスの最新ではない認証を無効にします。

```
 Set-SPOTenant -LegacyAuthProtocolsEnabled $false

```


>[!IMPORTANT]
>アプリ ベースの CA は、Azure Active Directory (Azure AD) 証明書ベースの認証と併用することはできません。 同時に使用できるのは、いずれかの構成のみです。

### <a name="see-also"></a>関連項目
[Intune を使用したアプリ ベースの条件付きアクセス](app-based-conditional-access-intune.md)
