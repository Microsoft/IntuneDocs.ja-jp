---
title: "Intune の基本的なセットアップ"
description: "この記事では、Microsoft Intune のセットアップに必要な手順について説明します。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 60cfa440-0723-4ea0-bacf-3c5d26f9a1d3
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: c3129b2a8d93e91493455da5f3e5fd1a59dd77bb
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2017
---
# <a name="basic-setup"></a>基本的なセットアップ

[!INCLUDE[note for both-portals](./includes/note-for-both-portals.md)]

環境を評価したら、Intune をセットアップします。

## <a name="external-dependencies-for-an-intune-deployment"></a>Intune の展開に関する外部依存関係

### <a name="identity"></a>ID

Intune では、ID プロバイダーおよびユーザー グループ化のプロバイダーとして Azure Active Directory (Azure AD) が必要です。

-   [ID の要件](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-overview#design-considerations-overview)についてはこちらをご覧ください。

-   [ディレクトリ同期の要件](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-directory-sync-requirements)についてはこちらをご覧ください。

-   [多要素認証の要件](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-multifactor-auth-requirements)についてはこちらをご覧ください。

-   [ユーザーとデバイス グループの計画](/intune/users-permissions-add)についてはこちらをご覧ください。

-   [ユーザーとデバイス グループを作成する方法](/intune/groups-get-started)についてはこちらをご覧ください。

組織が Office 365 を既に使っている場合は、Intune でも同じ Azure Active Directory 環境を使うことが重要です。

### <a name="pki-optional"></a>PKI (省略可能)

VPN、Wi-Fi、または Intune でのメール プロファイルで証明書ベースの認証を使うことを計画している場合は、サポートされる [PKI インフラストラクチャが存在](/intune/certificates-configure)し、証明書プロファイルを作成して展開する準備ができていることを、確認する必要があります。

Intune で証明書を構成する方法の詳細については、以下をご覧ください。

-   [SCEP 用の証明書インフラストラクチャを構成する方法](/intune/certificates-scep-configure)についてはこちらをご覧ください。

-   [PFX 用の証明書インフラストラクチャを構成する方法](/intune/certficates-pfx-configure)についてはこちらをご覧ください。


## <a name="task-list-for-an-intune-setup"></a>Intune セットアップのタスク一覧

### <a name="task-1-intune-subscription"></a>タスク 1: Intune のサブスクリプション

Intune に移行するには、Intune サブスクリプションが必要です。

-   次の手順を説明する、[こちらのページ](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0)を参照してください。

    -   新しい AAD テナントにリンクされた新しい Intune サブスクリプションを作成する。

    -   既存の AAD テナントにサインインして、Intune サブスクリプションをリンクする。

### <a name="task-2-assign-intune-user-licenses"></a>タスク 2: Intune ユーザー ライセンスを割り当てる

-   Intune ユーザー ライセンスを割り当てる方法については、[こちら](licenses-assign.md)を参照してください。

-   新しい Azure Active Directory テナントを作成した場合は、[新しいユーザーを作成したり、オンプレミスの Active Directory (AD) からユーザーを同期する方法](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)を参照してください。

### <a name="task-3-set-your-mdm-authority-to-intune"></a>タスク 3: MDM 機関を Intune に設定する

Intune は、Azure Portal や Configuration Manager の Current Branch コンソールから管理できます。 Configuration Manager の現在のブランチの展開と Intune を統合する必要がある場合を除き、Intune は [Azure Portal](https://portal.azure.com) から管理することをお勧めします。

MDM 機関を **Intune** に設定して、Intune Azure Portal を有効にします。 異なる MDM 機関を使用すると、Intune は代替の Microsoft 管理コンソールに MDM 管理を転送します。 このようなケースは一般的ではありません。

> [!IMPORTANT]
> モバイル デバイス管理を Intune に初めて転送する場合は、MDM 機関を Intune に設定する必要があります。

-   モバイル管理機関を設定する方法については、[こちら](/intune/mdm-authority-set)を参照してください。

## <a name="next-step"></a>次の手順

[デバイスおよびアプリ管理のポリシー](migration-guide-configure-policies.md)
