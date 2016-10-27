---
title:
- "MAM 設定の確認 | Microsoft Intune"
description: "このトピックでは、MAM ポリシーが正しく設定され、想定通りに動作するかをテストし、確認する方法を説明します。"
keywords: 
author: karthikaraman
ms.author: karaman
manager: angerobe
ms.date: 08/16/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 41d82597-e13e-4c3e-9151-e71392236ca0
ms.reviewer: joglocke
translationtype: Human Translation
ms.sourcegitcommit: 0736b5f24065f55d8fbd312395e4bb7226ebf619
ms.openlocfilehash: 5b6253d3d4c969b6947d83b5c8695a484f8c1d27


---

# モバイル アプリケーション管理のセットアップの検証

このトピックでは、モバイル アプリケーション管理 (MAM) を設定した後の問題の確認について説明します。 このガイドは、Azure Portal の MAM ポリシーに適用されます。

### 現象の確認
MAM はデータ保護ツールであるため、ユーザーが問題を報告しない可能性があります。 MAM の構成に問題がある場合でも、MAM がない場合と同じようにユーザーはアクセスに制限を受けず、問題が発生していることに気付かない可能性があります。 このため、MAM の制限を意図的にテストできるユーザーの小規模なグループに MAM ポリシーをパイロット運用して、MAM 構成を確認することをお勧めします。


### 確認項目

テストの結果、MAM ポリシーの動作が予想通りではない場合は、以下の内容を確認することをお勧めします。

- ユーザーは MAM のライセンスを取得していますか。
- ユーザーは O365 のライセンスを取得していますか。
- 各ユーザーの MAM アプリの状態。 アプリの状態は、**[確認済み]** か **[未確認]** のはずです。

#### ユーザーの MAM の状態
1. Azure Portal で、**[Intune mobile application management (Intune モバイル アプリケーション管理)]** > **[設定]** > **[アプリ管理]** > **[すべての設定]** > **[App reporting by user (ユーザーによるアプリ レポート)]** > **[ユーザー]**を選択します。

2. 一覧からユーザーを選択または検索し、ユーザーを選択して、**[ユーザーの選択]** を選択します。 **アプリ レポート**列の最上部で、ユーザーが MAM のライセンスを取得しているかどうかを確認します。 その下に、ユーザーが O365 のライセンスを取得しているかどうか、またすべてのユーザーのデバイスのアプリの状態が表示されます。

![MAM のアプリの状態](..\media\ts-mam-user-apps.png) 

### 対処
ユーザーの状態に基づいて実行するアクションを次に示します。

- ユーザーが MAM のライセンスを取得していない場合、「[Intune のライセンスを管理する](..\get-started\start-with-a-paid-subscription-to-microsoft-intune)」の説明に従って、ユーザーに Intune のライセンスを割り当てます。
- ユーザーが O365 のライセンスを取得していない場合、ライセンスを取得します。
- ユーザーのアプリが **[未確認]** として一覧表示される場合、そのアプリの MAM ポリシーを正しく構成したかどうかを確認します。
- MAM ポリシーを適用するすべてのユーザーに、これらの条件が適用されていることを確認します。

### 関連項目
[Microsoft Intune でのモバイル アプリ管理ポリシーの作成および展開](..\deploy-use\get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune)

[Microsoft Intune でモバイル アプリケーション管理ポリシーを使用してデータを保護する](..\deploy-use\protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)



<!--HONumber=Oct16_HO1-->


