---
title: Microsoft Intune でスコープのタグを使ってポリシーをフィルター処理する - Azure | Microsoft Docs
description: スコープのタグを使用して、構成プロファイルを特定のロールにフィルター処理します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/29/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 0da6861b6c49fc37691b8c6e464a506670643fa3
ms.sourcegitcommit: 4a7421470569ce4efe848633bd36d5946f44fc8d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2019
ms.locfileid: "54203333"
---
# <a name="use-scope-tags-to-filter-policies"></a>スコープのタグを使用してポリシーをフィルター処理する

スコープのタグを使用すると、作成したカスタム タグを使ってポリシーをフィルター処理できます。 スコープ タグはロールとアプリに適用できます。

たとえば、"エンジニアリング部門" と呼ばれるスコープのタグを作成し、エンジニアリング部門に関連する構成プロファイルに割り当てます。 その同じタグを "エンジニアリング管理者" ロールに割り当てます。 "エンジニアリング部門" タグを含むポリシーのみが表示されます。

## <a name="to-create-a-scope-tag"></a>スコープのタグを作成するには

**[ロール]** > **[スコープ (タグ)]** > **[作成]** の順に選択します。

## <a name="to-add-a-scope-tag-to-a-configuration-profile"></a>スコープのタグを構成プロファイルに追加するには

**[デバイス構成]** > **[プロファイル]** の順に選択し、プロファイルを選択して **[プロパティ]** > **[スコープ (タグ)]** の順に選択します。

## <a name="to-assign-a-scope-tag-to-a-role"></a>スコープのタグをロールに割り当てるには

**[ロール]** > **[すべてのロール]** > **[Policy and Profile Manager]\(ポリシーとプロファイル マネージャー\)** > **[割り当て]** > **[スコープ (タグ)]** の順に選択します。

## <a name="to-assign-a-scope-tag-to-an-app"></a>スコープ タグをアプリに割り当てるには

**[クライアント アプリ]** > **[アプリ]** でアプリを選択し、**[プロパティ]** > **[スコープ (タグ)]** > **[追加]** でタグを選択して、**[選択]** > **[OK]** > **[保存]** を選択します。


## <a name="next-steps"></a>次の手順

ご自分の[ロール](role-based-access-control.md)と[プロファイル](device-profile-assign.md)を管理します。

