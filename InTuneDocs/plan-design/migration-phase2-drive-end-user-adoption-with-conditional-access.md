---
title: "条件付きアクセスでエンド ユーザーの導入を推進する | Microsoft Docs"
description: "この記事では、条件付きアクセスを利用して Intune 登録を推進する方法を詳しく説明します。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c2d7ce3f-fe97-4044-ad9e-25ac8fa301c9
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: ab5aa4e12d951d818c5afb4e1ac5e866b05733fb
ms.openlocfilehash: 26d11bc64802005bcce8cc1962d531af6ffe5cd5
ms.lasthandoff: 03/27/2017


---

# <a name="phase-2-drive-end-user-adoption-with-conditional-access"></a>フェーズ 2: 条件付きアクセスでエンド ユーザーの導入を推進する

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

Intune で条件付きアクセス機能を有効にする (未登録のデバイスの電子メールをブロックするなど) ことにより、登録とコンプライアンスを推進できますが、移行の成功において必須ではありません。 移行の成功は、移行導入の目標とセキュリティ要件によって決まります。

## <a name="migration-campaign-with-conditional-access"></a>条件付きアクセスを使用した移行キャンペーン

条件付きアクセスを使用して移行キャンペーンを強化するための一般的な方法を次に示します。

1.  以前の MDM プロバイダーからの移行が必要なユーザーを除くすべてのユーザーに対して条件付きアクセス規則が適用されるように設定します。 条件付きアクセスから除外されたすべてのユーザーで構成された、Azure AD ユーザー グループを作成することができます。

2.  ユーザーの移行が済んだら、条件付きアクセスから除外されたグループから削除します。

3.  移行が完了したら、Intune がアクセスを許可する場合を除き、既定では条件付きアクセス ポリシーによってアクセスがブロックされるように構成します。

### <a name="advantages"></a>長所

-   新しいユーザー アカウントや、以前のソリューションで管理されなかったユーザー アカウントに対するアクセス制御を提供します。

-   以前のソリューションのユーザーに対して、移行の猶予期間が提供されます。

-   生産性の低下を最小限に抑えます。

### <a name="disadvantages"></a>短所

-   条件付きアクセスが有効になるまでは、以前のソリューションのユーザーが管理されていないデバイスを使用してリソースにアクセスする可能性があります。

> [!TIP] 
> 数多くの方法のうち 1 つを紹介します。 すべてのフェーズで登録の指示を行うまでは条件付きアクセスを延期する簡単なプロセスを選択するか、最初から条件付きアクセスを適用して、すべてのアクセスにおいて完全な準拠を要求する厳格なプロセスを選択することができます。

-   条件付きアクセスの詳細については、[ここ](https://docs.microsoft.com/intune-azure/conditional-access/what-is-conditional-access)をご覧ください。

## <a name="task-list-for-conditional-access"></a>条件付きアクセスのタスク一覧

### <a name="task-1-get-ready-for-intune-conditional-access"></a>タスク 1: Intune の条件付きアクセスの準備をする

-   条件付きアクセスを構成する方法については、[こちら](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune)を参照してください。

### <a name="task-2-setup-intune-conditional-access"></a>タスク 2: Intune の条件付きアクセスのセットアップ

詳細については、次の条件付きアクセス ポリシーの種類のいずれかを選択します。

-   [Exchange Online と新しい Exchange Online Dedicated](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune)

-   [Exchange On-Premises と以前の Exchange Online Dedicated](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-exchange-onpremises-with-microsoft-intune)

-   [SharePoint Online](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune)

-   [Skype for Business Online](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-skype-for-business-online-with-microsoft-intune)

-   [Dynamics CRM Online](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-dynamics-crm-online-with-microsoft-intune)

-   [電子メール アクセスのシナリオの例](https://docs.microsoft.com/intune/deploy-use/restrict-email-access-example-scenarios)

## <a name="next-steps"></a>次のステップ

[フェーズ 2: 標準的な移行サイクル](https://docs.microsoft.com/intune/plan-design/migration-phase2-typical-migration-cycle)

