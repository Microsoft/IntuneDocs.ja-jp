---
title: アプリ保護ポリシーのセットアップを検証する
titleSuffix: Microsoft Intune
description: アプリ保護ポリシーが正しくセットアップされ、動作していることをテストする方法について説明します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/13/2018
ms.prod: ''
ms.service: microsoft-intune
ms.topic: article
ms.technology: ''
ms.assetid: 15f8a838-0b69-412b-a42e-c6edb61f0cae
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 60cf35814f64f2f237c3f2ec3ea8f4d56460dd71
ms.sourcegitcommit: e9ba1280b95565a5c5674b825881655d0303e688
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/15/2019
ms.locfileid: "54297215"
---
# <a name="how-to-validate-your-app-protection-policy-setup"></a>アプリ保護ポリシーの設定を検証する方法

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

アプリ保護ポリシーが正しくセットアップされ、動作していることを検証します。 このガイドは、Azure Portal のアプリ保護ポリシーに適用されます。

## <a name="checking-for-symptoms"></a>現象の確認
アプリ保護はデータ保護ツールであるため、ユーザーが問題を報告することはほとんどありません。 アプリ保護の構成に問題がある場合、ユーザーは、アプリ保護がない場合と同じようにアクセスの制限を受けないため、問題があることがわかりません。 この理由により、アプリ保護の制限を意図的にテストできるユーザーの小規模なグループでアプリ保護ポリシーをパイロット運用して、アプリ保護の構成を検証することをお勧めします。


## <a name="what-to-check"></a>確認項目

テストの結果、アプリ保護ポリシーが予期しない動作をしていることがわかった場合は、以下の項目を確認します。

- ユーザーはアプリ保護のライセンスを取得していますか。
- ユーザーは O365 のライセンスを取得していますか。
- 各ユーザーのアプリ保護アプリの状態。 アプリの状態は、**[確認済み]** か **[未確認]** のはずです。

### <a name="user-app-protection-status"></a>ユーザーのアプリ保護の状態
1. [Azure ポータル](https://portal.azure.com) にサインインします。
2. **[すべてのサービス]** > **[Intune]** の順に選択します。 Intune は **[監視 + 管理]** セクションにあります。
3. **[クライアント アプリ]** > **[モニター]** >  **[アプリの保護状態]** を選択した後、**[割り当てられたユーザー]** タイルを選択します。 
4. **[アプリ レポート]** ページ上で、**[ユーザーの選択]** を選択してユーザーとグループの一覧を表示させます。 
5. 一覧からユーザーを検索して選択し、**[ユーザーの選択]** を選択します。 **[アプリ レポート]** ページの上部で、ユーザーがアプリ保護のライセンスを取得しているかどうかを確認できます。 また、ユーザーが O365 のライセンスを取得しているかどうか、およびすべてのユーザーのデバイスのアプリの状態を確認できます。



## <a name="what-to-do"></a>対処
ユーザーの状態に基づいて実行するアクションを次に示します。

- ユーザーがアプリ保護のラインセンスを取得していない場合は、Intune ライセンスをそのユーザーに割り当てます。
- ユーザーが O365 のライセンスを取得していない場合、ライセンスを取得します。
- ユーザーのアプリが **[チェックインされていません]** という状態で一覧に表示される場合は、そのアプリのアプリ保護ポリシーを正しく構成したかどうかを確認します。
- アプリ保護ポリシーを適用するすべてのユーザー全体に、これらの条件が適用されていることを確認します。

## <a name="see-also"></a>関連項目

[Intune アプリ保護ポリシーとは](app-protection-policies.md)
