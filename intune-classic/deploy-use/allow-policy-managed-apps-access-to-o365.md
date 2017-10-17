---
title: "アプリ ベースの O365 に対する条件付きアクセス"
description: "MAM CA を利用して、O365 サービスに対してアクセス権を持つアプリを制御する方法の概念について説明します。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/05/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bd6bee60-5e39-42c8-a2e9-f5865ac3573f
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 7ad33ba7020f418f4894a689d5d66a74e4b8c10e
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/10/2017
---
# <a name="allow-only-mobile-apps-that-support-intune-app-protection-policies-to-access-office-365-services"></a>Intune アプリ保護ポリシーをサポートするモバイル アプリのみが Office 365 サービスにアクセスできるようにする

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

[Intune アプリ保護ポリシー](protect-apps-and-data-with-microsoft-intune.md)を使用すると、Intune の管理対象に登録されているデバイス上の会社のデータを保護できます。 **Intune の監視対象に登録されていない従業員が所有するデバイス**に対して、アプリ保護ポリシーを使用することもできます。  この場合、デバイスを管理しなくても、会社のデータとリソースが保護されていることを確認する必要があります。 MAM とアプリ ベースの条件付きアクセスを使用すると、Exchange Online などの Office 365 サービスにアクセスするための Intune アプリ保護ポリシーをサポートするモバイル アプリのみに許可するポリシーを作成できます。

たとえば、Exchange Online へのアクセスを **Microsoft Outlook アプリ**のみに許可すると、**Exchange Online** からから電子メールを取得するように Intune MAM ポリシーのデータ保護を受けていない **iOS と Android の組み込み電子メール アプリをブロックできます**。 あるいは Intune MAM サポートのないモバイル アプリの **SharePoint Online** へのアクセスをブロックできます。

次の図は、アプリ ベースの条件付きアクセス ポリシーがアクセスを許可するかブロックするかを決定するために使用するフローです。![アクセスを許可するかブロックするかを決定するための多様な条件を示す図](../media/mam-ca-decision-flow_simple.png)。

図に使用されている省略語の説明は次のとおりです。
* **CP**: ポータル サイト アプリ
* **AA**: Azure Authenticator アプリ
* **AAD**: Azure Active Directory
* **EAS**: Exchange Active Sync

## <a name="prerequisites"></a>必要条件
アプリ ベースの条件付きアクセス ポリシーを作成する**前に**、**Enterprise Mobility + Security または Azure Active Directory Premium サブスクリプション**を用意する必要があります。また、ユーザーに EMS または Azure AD のライセンスが付与される必要があります。 詳細については、「[Enterprise Mobility pricing page](https://www.microsoft.com/cloud-platform/enterprise-mobility-pricing)」 (Enterprise Mobility の価格) ページまたは「[Azure Active Directory の価格](https://azure.microsoft.com/pricing/details/active-directory/)」ページを参照してください。


## <a name="supported-apps"></a>サポートされているアプリ
**Exchange Online**:
* Android 用と iOS 用 **Microsoft Outlook**

**SharePoint Online**
* iOS 用と Android 用の Microsoft Word
* iOS 用と Android 用の Microsoft Excel
* iOS 用と Android 用の Microsoft PowerPoint
* iOS 用と Android 用の Microsoft OneDrive for Business
* iOS 用の Microsoft OneNote

>[!IMPORTANT]
>Android デバイスでは、OneDrive アプリまたは Outlook アプリのいずれかにログインして、最初にデバイス登録を実行する必要があります。 Android 用の OneNote アプリは、登録なしでの MAM をまだサポートしていません。

アプリ ベースの条件付きアクセス ポリシーがあるアプリのユーザー エクスペリエンスの詳細については、「[What to expect when using an app with MAM CA](use-apps-with-mam-ca.md)」(アプリと MAM CA を使用する場合の結果) を参照してください。


## <a name="next-steps"></a>次のステップ
[MAM アプリ用の Exchange Online ポリシーを作成する](mam-ca-for-exchange-online.md)

[MAM アプリ用の SharePoint Online ポリシーを作成する](mam-ca-for-sharepoint-online.md)

[最新の認証を使用していないアプリをブロックする](block-apps-with-no-modern-authentication.md)

### <a name="see-also"></a>関連項目

[アプリ保護ポリシーを使用したアプリ データの保護](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)
