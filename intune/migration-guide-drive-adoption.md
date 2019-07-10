---
title: 条件付きアクセスでエンドユーザーの導入を推進する
titleSuffix: Microsoft Intune
description: Microsoft Intune でドライブ登録への条件付きアクセスを使用する方法について説明します。
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c2d7ce3f-fe97-4044-ad9e-25ac8fa301c9
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 40e78d85c215bbb5cc126705f26041ce4f7786f4
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2019
ms.locfileid: "67549453"
---
# <a name="drive-end-user-adoption-with-conditional-access-in-microsoft-intune"></a>Microsoft Intune で条件付きアクセスでエンド ユーザーの導入を推進する

Intune で条件付きアクセス機能を有効にする (未登録のデバイスの電子メールをブロックするなど) ことにより、登録とコンプライアンスを推進できますが、移行の成功において必須ではありません。 移行の成功は、移行導入の目標とセキュリティ要件によって決まります。

## <a name="migration-campaign-with-conditional-access"></a>条件付きアクセスを使用した移行キャンペーン

条件付きアクセスを使用して移行キャンペーンを強化するための一般的な方法を次に示します。

1. 以前の MDM プロバイダーからの移行が必要なユーザーを除くすべてのユーザーに対して条件付きアクセス規則が適用されるように設定します。 条件付きアクセスから除外されたすべてのユーザーで構成された、Azure AD ユーザー グループを作成することができます。

2. ユーザーの移行が済んだら、条件付きアクセスから除外されたグループから削除します。

3. 移行が完了したら、Intune がアクセスを許可する場合を除き、既定では条件付きアクセス ポリシーによってアクセスがブロックされるように構成します。

### <a name="advantages"></a>長所

- 新しいユーザー アカウントや、以前のソリューションで管理されなかったユーザー アカウントに対するアクセス制御を提供します。

- 以前のソリューションのユーザーに対して、移行の猶予期間が提供されます。

- 生産性の低下を最小限に抑えます。

### <a name="disadvantages"></a>短所

- 条件付きアクセスが有効になるまでは、以前のソリューションのユーザーが管理されていないデバイスを使用してリソースにアクセスする可能性があります。


数多くの方法のうち 1 つを紹介します。 すべてのフェーズで登録の指示を行うまでは条件付きアクセスを延期する簡単なプロセスを選択するか、最初から条件付きアクセスを適用して、すべてのアクセスにおいて完全な準拠を要求する厳格なプロセスを選択することができます。

- 詳しくは、「[Microsoft Intune で電子メール、Office 365、およびその他のサービスへのアクセスを制限する](conditional-access.md)」をご覧ください。

## <a name="task-list-for-conditional-access"></a>条件付きアクセスのタスク一覧

### <a name="task-1-decide-how-you-are-going-to-implement-conditional-access"></a>タスク 1: 条件付きアクセスを実装する方法の決定

[条件付きアクセスの一般的な使用方法](conditional-access-intune-common-ways-use.md)

### <a name="task-2-set-up-intune-conditional-access"></a>タスク 2: Intune の条件付きアクセスの設定

次のいずれかのオプションを選択します。

- [Azure Active Directory の条件付きアクセスを構成する](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)

- [Intune で On-Premises Exchange Connector をインストールする](exchange-connector-install.md)

- [Exchange Online 用にアプリベースの条件付きアクセス ポリシーを設定する](app-based-conditional-access-intune-create.md)

- [SharePoint Online のアプリベースの条件付きアクセス ポリシーを設定する](app-based-conditional-access-intune-create.md)

- [先進認証 (ADAL) を使用していないアプリをブロックする](app-modern-authentication-block.md)

## <a name="next-steps"></a>次の手順

[一般的な移行サイクル](migration-guide-cycle.md)について学習します。
