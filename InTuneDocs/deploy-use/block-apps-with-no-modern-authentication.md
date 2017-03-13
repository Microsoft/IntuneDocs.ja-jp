---
title: "最新の認証を使用していないアプリをブロックする | Microsoft Docs"
description: 
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 098b652c-01e0-45d1-a731-620b0d3dc7c1
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: e55cf608c2e5157feeb40ba20d3988b5b35064db
ms.openlocfilehash: b2d708e35a7993ff7c5e3db170b1025794b33baf
ms.lasthandoff: 02/25/2017


---

# <a name="block-apps-that-do-not-use-modern-authentication-adal"></a>最新の認証を使用していないアプリをブロックする (ADAL)

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

アプリ保護ポリシーを使用したアプリ ベースの条件付きアクセスは、OAuth2 の実装である[最新の認証](https://support.office.com/en-US/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a)を使用するアプリケーションに依存しています。 最新の Office モバイル アプリとデスクトップ アプリケーションは最新の認証を使用していますが、基本認証やフォームベースの認証など、他の認証方式を使用しているサードパーティ製アプリや古い Office アプリもあります。

このようなアプリに対するアクセスをブロックするには、以下を推奨します。

* 最新ではない認証プロトコルをブロックするように ADFS 要求規則を設定します。 詳しい手順は、シナリオ 3 の[ブラウザー ベースのアプリケーションを除く Office 365 への外部アクセスをすべてブロックする方法](https://technet.microsoft.com/library/dn592182.aspx)に関するページを参照してください。

>[!IMPORTANT]
>アプリ ベースの CA は、Azure Active Directory (Azure AD) 証明書ベースの認証と併用することはできません。 同時に使用できるのは、いずれかの構成のみです。

### <a name="see-also"></a>関連項目
[Intune でサポートされているアプリにのみ Office&365; サービスへのアクセスを許可する](allow-policy-managed-apps-access-to-o365.md)

