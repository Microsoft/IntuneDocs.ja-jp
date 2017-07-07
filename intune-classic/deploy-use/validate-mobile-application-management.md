---
title: "MAM 設定を確認する"
description: "このトピックでは、MAM ポリシーが正しく設定され、想定通りに動作するかをテストし、確認する方法を説明します。"
keywords: 
author: andredm7
ms.author: andredm
manager: angerobe
ms.date: 12/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 41d82597-e13e-4c3e-9151-e71392236ca0
ms.reviewer: joglocke
ms.custom: intune-classic
ms.openlocfilehash: 1e22be7b238cce195ee88c938b1cca009c0b21d3
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2017
---
# <a name="validating-your-mobile-application-management-setup"></a>モバイル アプリケーション管理のセットアップの検証

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

このトピックでは、モバイル アプリケーション管理 (MAM) を設定した後の問題の確認について説明します。 このガイドは、Azure Portal の MAM ポリシーに適用されます。

### <a name="checking-for-symptoms"></a>現象の確認
MAM はデータ保護ツールであるため、ユーザーが問題を報告しない可能性があります。 MAM の構成に問題がある場合でも、MAM がない場合と同じようにユーザーはアクセスに制限を受けず、問題が発生していることに気付かない可能性があります。 このため、MAM の制限を意図的にテストできるユーザーの小規模なグループに MAM ポリシーをパイロット運用して、MAM 構成を確認することをお勧めします。


### <a name="what-to-check"></a>確認項目

テストの結果、MAM ポリシーの動作が予想通りではない場合は、以下の内容を確認することをお勧めします。

- ユーザーは MAM のライセンスを取得していますか。
- ユーザーは O365 のライセンスを取得していますか。
- 各ユーザーの MAM アプリの状態。 アプリの状態は、**[確認済み]** か **[未確認]** のはずです。

#### <a name="user-mam-status"></a>ユーザーの MAM の状態
1. Azure Portal で、**[Intune mobile application management (Intune モバイル アプリケーション管理)]** > **[設定]** > **[アプリ管理]** > **[すべての設定]** > **[App reporting by user (ユーザーによるアプリ レポート)]** > **[ユーザー]**を選択します。

2. 一覧からユーザーを選択または検索し、ユーザーを選択して、**[ユーザーの選択]** を選択します。 **アプリ レポート**列の最上部で、ユーザーが MAM のライセンスを取得しているかどうかを確認します。 その下に、ユーザーが O365 のライセンスを取得しているかどうか、またすべてのユーザーのデバイスのアプリの状態が表示されます。

![MAM のアプリの状態](..\media\ts-mam-user-apps.png)

### <a name="what-to-do"></a>対処
ユーザーの状態に基づいて実行するアクションを次に示します。

- ユーザーが MAM のライセンスを取得していない場合、「[Intune のライセンスを管理する](/intune/setup-steps)」の説明に従って、ユーザーに Intune のライセンスを割り当てます。
- ユーザーが O365 のライセンスを取得していない場合、ライセンスを取得します。
- ユーザーのアプリが **[未確認]** として一覧表示される場合、そのアプリの MAM ポリシーを正しく構成したかどうかを確認します。
- MAM ポリシーを適用するすべてのユーザーに、これらの条件が適用されていることを確認します。

### <a name="see-also"></a>関連項目
[Microsoft Intune でのモバイル アプリ管理ポリシーの作成および展開](..\deploy-use\get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)

[Microsoft Intune でモバイル アプリケーション管理ポリシーを使用してデータを保護する](..\deploy-use\protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)
