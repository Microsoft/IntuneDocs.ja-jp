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
ms.openlocfilehash: 080205e601b857d4765eb6b97eeeeeb8f4e6fc1b
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2018
ms.locfileid: "52187159"
---
# <a name="use-scope-tags-to-filter-policies"></a>スコープのタグを使用してポリシーをフィルター処理する

スコープのタグを使用すると、作成したカスタム タグを使ってポリシーをフィルター処理できます。

たとえば、"エンジニアリング部門" と呼ばれるスコープのタグを作成し、エンジニアリング部門に関連する構成プロファイルに割り当てます。 その同じタグを "エンジニアリング管理者" ロールに割り当てます。 "エンジニアリング部門" タグを含むポリシーのみが表示されます。

## <a name="to-create-a-scope-tag"></a>スコープのタグを作成するには

**[ロール]** > **[スコープ (タグ)]** > **[作成]** の順に選択します。

## <a name="to-add-a-scope-tag-to-a-configuration-profile"></a>スコープのタグを構成プロファイルに追加するには

**[デバイス構成]** > **[プロファイル]** の順に選択し、プロファイルを選択して **[プロパティ]** > **[スコープ (タグ)]** の順に選択します。

## <a name="to-assign-a-scope-tag-to-a-role"></a>スコープのタグをロールに割り当てるには

**[ロール]** > **[すべてのロール]** > **[Policy and Profile Manager]\(ポリシーとプロファイル マネージャー\)** > **[割り当て]** > **[スコープ (タグ)]** の順に選択します。

## <a name="next-steps"></a>次の手順

ご自分の[ロール](role-based-access-control.md)と[プロファイル](device-profile-assign.md)を管理します。

