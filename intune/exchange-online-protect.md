---
title: デバイス管理なしの Exchange
titleSuffix: Microsoft Intune
description: Microsoft Intune を使用し、デバイス管理システムを構築せずに、Office 365 Exchange Online 電子メールへのアクセスを社員に与えます。
keywords: Office 365 Exchange 電子メール アクセス
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/31/2017
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.topic: archived
ms.technology: ''
ms.assetid: 88a0d3b9-2622-403b-8374-1396afd8066e
ms.reviewer: pchacon
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 30c0e5af6d7ff0467383294c071d0ffdb96c5dc1
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66041849"
---
# <a name="protect-office-365-exchange-online-without-requiring-device-management"></a>デバイス管理を要求せずに Office 365 Exchange Online を保護する

デバイス管理システムを構築せずに、職場のメールへのアクセスを社員に与えることができます。 Intune 経由で Office 365 Exchange Online へのアクセスを与えることができます。 必要な手順を完了する前に、Microsoft 365 または Azure Active Directory (プレミアム) と Intune のライセンスがあることを確認します。 社員には、[サポートされている iOS または Android デバイス](supported-devices-browsers.md)を与える必要があります。 

デバイス管理システムを設定することもできます。 この種類のアプリ保護は、デバイス管理とは独立して動作します。 

## <a name="action-plan"></a>行動計画

1. [条件付きアクセスについて学習します](conditional-access.md)。 
2. [アプリベースの条件付きアクセスについて学習します](app-based-conditional-access-intune.md)。
3. [Exchange Online のアプリベースの条件付きアクセス ポリシーを設定します](app-based-conditional-access-intune-create.md)。
4. [管理できないアプリをブロックします](app-modern-authentication-block.md)。特に、Azure Active Directory Authentication Library (ADAL) を使用しないアプリをブロックします。
5. (任意) [SharePoint Online のアプリベースの条件付きアクセス ポリシーを設定します](app-based-conditional-access-intune-create.md)。 このポリシーは、管理できないアプリやセキュリティ対策を施せないアプリから会社のデータへのアクセスをブロックします。 このポリシーは、SharePoint モバイルからのアクセスも制限します。 

## <a name="what-to-tell-employees-and-students"></a>社員や学生に伝えること

* Microsoft Outlook または Microsoft SharePoint をダウンロードしてインストールするように社員や学生に伝えます。iOS の場合は Apple App Store を、Android の場合は Google Play Store をご利用ください。 
* 最新の認証方法を利用しないアプリへのアクセスを禁止する場合、社員や学生にこの制限のことを知らせます。 

## <a name="next-steps"></a>次の手順

アプリベースの条件付きアクセスを利用し、会社データのセキュリティを強化しました。 次の手順として、会社データの保護機能を上げる他の方法について学習できます。次のようなものがあります。 

* [Active Directory や Azure Active Directory でデバイス コンプライアンス、デバイス リスク、場所、ユーザー属性に基づいて条件付きアクセス](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)を設定します。  
* アプリ保護ポリシーを設定し、意図的な、あるいは意図しないデータ漏洩から会社のデータを守ります。 
* Azure Information Protection を活用し、ネットワークの外にある会社データを守ります。 

EMS または Office 365 のさまざまなシナリオを有効にする支援をご希望ですか? Microsoft 365、Enterprise Mobility + Security、または Azure Active Directory Premium のライセンスを 150 以上お持ちでしたら、[FastTrack の特典](https://docs.microsoft.com/enterprise-mobility-security/solutions/enterprise-mobility-fasttrack-program)をご利用いただけます。 
