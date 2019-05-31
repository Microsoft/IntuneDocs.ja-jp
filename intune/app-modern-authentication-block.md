---
title: 最新の認証を使用していないアプリを Intune でブロックする
titleSuffix: Microsoft Intune
description: Microsoft Intune を使用したアプリと先進認証 (ADAL) について説明します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/03/2019
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.topic: conceptual
ms.technology: ''
ms.assetid: 73db3070-d033-40fb-a8f1-58b9d198021e
ms.reviewer: chrisgre
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9ca96f36f8813d80c7ebb07bfb3bd65f8aa0b392
ms.sourcegitcommit: 71314481e644025c005019b478b4cbeaf2390ea9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/05/2019
ms.locfileid: "59569104"
---
# <a name="block-apps-that-dont-use-modern-authentication-adal"></a>先進認証 (ADAL) を使用していないアプリをブロックする

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

アプリ保護ポリシーを使用したアプリ ベースの条件付きアクセスは、[先進認証](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a)を使用するアプリケーションに依存しています。これは OAuth2 の実装です。 最新のモバイルおよびデスクトップ用 Office アプリケーションでは、先進認証が使用されています。 しかし、基本認証やフォームベースの認証など、他の認証方式を使用しているサードパーティ製アプリや古い Office アプリもあります。

## <a name="block-access-to-apps"></a>アプリへのアクセスをブロックする

先進認証を使用していないアプリへのアクセスをブロックするには、Intune アプリ保護ポリシーを使用して、条件付きアクセスを実装します。 詳細については、「[Intune でのアプリ ベースの条件付きアクセス](app-based-conditional-access-intune.md)」を参照してください。

## <a name="additional-information"></a>追加情報

Azure AD 条件付きアクセスの詳細については、次のトピックを参照してください。
- [Azure Active Directory の条件付きアクセスとは](https://docs.microsoft.com/azure/active-directory/conditional-access/overview)
- [アプリベースの条件付きアクセスのしくみ](app-based-conditional-access-intune.md#how-app-based-conditional-access-works)
- [SharePoint Online と Exchange Online に Azure Active Directory の条件付きアクセスを設定する](https://docs.microsoft.com/azure/active-directory/conditional-access/conditional-access-for-exo-and-spo)

## <a name="next-steps"></a>次の手順

- [Intune を使用したアプリ ベースの条件付きアクセス](app-based-conditional-access-intune.md)
