---
title: "Intune の概要"
titleSuffix: Intune on Azure
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 06/27/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6bfab644-c1e2-4154-a254-e95b9a1d75f2
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ef58e46118a0a44609abba5de4986b5a1526a151
ms.sourcegitcommit: fd2e8f6f8761fdd65b49f6e4223c2d4a013dd6d9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2017
---
# <a name="what-is-microsoft-intune"></a>Microsoft Intune とは

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

![Azure Portal の Microsoft Intune](./media/generic-intune-azure.png)

Microsoft Intune は Azure の最新サービスの 1 つです。 組織のモバイル デバイス、PC、[定期的に更新される](whats-new.md)アプリを管理するためのツールを備えています。 現代的な Azure コンソール以外に、Intune では、クラシック コンソールも利用できます。 クラシック コンソールは最初のバージョンの Intune です。このコンソールで引き続き [Intune ソフトウェア クライアントを内蔵している Windows PC を管理](/intune-classic/deploy-use/pc-management-comparison.md)できます。 クラシック ポータルは Silverlight で構築されており、少数のタスクに利用されます。 モバイル デバイスやアプリの管理を含む、それ以外のすべては Azure Portal で行います。 この概要ガイドでは、基本的なタスクを紹介します。Azure Portal で Intune を利用するために完了する必要があります。

![ヘルプとサポートのブレードは、Intune の左サイドバーのアクション リストの下にあります。](./media/intune-azure-help-support-closeup.png)

## <a name="what-does-intune-in-the-azure-portal-provide"></a>Azure Portal の Intune でできること

Azure Portal の Intune の機能:

* すべての [Enterprise Mobility + Security (EMS) コンポーネント](https://docs.microsoft.com/enterprise-mobility-security)用の統合コンソール
* [現代的な Web ブラウザー](supported-devices-browsers.md)をサポートする Web 標準で構築された HTML ベースのコンソール
* [Azure Active Directory グループ](groups-get-started.md)によってすべての Azure アプリケーション間での互換性を提供
* [Microsoft Graph API](intune-graph-apis.md) による自動化

## <a name="prerequisites"></a>必要条件

始める前に、Intune の管理者/テナント アカウントを有効にしておく必要があります。 アカウントは[ここ](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20)で新規登録できます。 現行のサブスクライバーも、ライブ テナントで以上の作業を完了できます。 テスト デバイスで作業していることを確認してください。

また、ガイドにある全タスクを完了するために、ユーザーが組織のグローバル管理者になっていることを確認する必要があります。
