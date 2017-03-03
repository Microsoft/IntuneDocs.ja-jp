---
title: "アプリ ベースの O365 に対する条件付きアクセス | Microsoft Docs"
description: "MAM CA を利用して、O365 サービスに対してアクセス権を持つアプリを制御する方法の概念について説明します。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 10/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bd6bee60-5e39-42c8-a2e9-f5865ac3573f
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: b6d5ea579b675d85d4404f289db83055642ffddd
ms.openlocfilehash: 2babdeaaf10e9a58716d299cbde0babe45967fb1


---

# <a name="allow-only-mobile-apps-that-support-intune-mam-policies-to-access-office-365-services"></a>Intune MAM ポリシーをサポートするモバイル アプリケーションのみが Office 365 サービスにアクセスできるようにする

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

[Intune モバイル アプリ管理 (MAM) ポリシー](protect-apps-and-data-with-microsoft-intune.md)を使用すると、Intune の管理対象に登録されているデバイス上の会社のデータを保護できます。 **Intune の監視対象に登録されていない従業員が所有するデバイス**に対して、MAM ポリシーを使用することもできます。  この場合、デバイスを管理しなくても、会社のデータとリソースが保護されていることを確認する必要があります。 MAM の条件付きアクセス (MAM CA) を使用すると、Exchange Online などの Office 365 サービスへのアクセスを、Intune MAM ポリシーをサポートするモバイル アプリのみに許可するポリシーを作成できます。

たとえば、Exchange Online へのアクセスを **Microsoft Outlook アプリ**のみに許可すると、**Exchange Online** からから電子メールを取得するように Intune MAM ポリシーのデータ保護を受けていない **iOS と Android の組み込み電子メール アプリをブロックできます**。

次の図は、MAM CA がアクセスを許可するかブロックするかを決定するために使用するフローです。![アクセスを許可するかブロックするかを決定するための多様な条件を示す図](../media/mam-ca-decision-flow_simple.png)。

図に使用されている省略語の説明は次のとおりです。
* **CP**: ポータル サイト アプリ
* **AA**: Azure Authenticator アプリ
* **AAD**: Azure Active Directory
* **EAS**: Exchange Active Sync

## <a name="prerequisites"></a>必要条件
MAM CA ポリシーを構成する**前に**、**Enterprise Mobility + Security または Azure Active Directory Premium サブスクリプション**を用意する必要があります。また、ユーザーに EMS または Azure AD のライセンスが付与される必要があります。 詳細については、「[Enterprise Mobility pricing page](https://www.microsoft.com/en-us/cloud-platform/enterprise-mobility-pricing)」 (Enterprise Mobility の価格) ページまたは「[Azure Active Directory の価格](https://azure.microsoft.com/en-us/pricing/details/active-directory/)」ページを参照してください。


## <a name="supported-apps"></a>サポートされているアプリ
**Exchange Online**: Android および iOS 用 **Microsoft Outlook**。

MAM CA ポリシーがあるアプリのユーザー エクスペリエンスの詳細については、「[What to expect when using an app with MAM CA](use-apps-with-mam-ca.md)」(アプリと MAM CA を使用する場合の結果) を参照してください。


## <a name="next-steps"></a>次のステップ
[MAM アプリ用の Exchange Online ポリシーを作成する](mam-ca-for-exchange-online.md)

[最新の認証を使用していないアプリをブロックする](block-apps-with-no-modern-authentication.md)

### <a name="see-also"></a>関連項目

[MAM ポリシーでアプリ データを保護する](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Dec16_HO2-->


