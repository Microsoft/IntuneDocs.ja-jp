---
title: アプリ保護ポリシーのセットアップを検証する
titleSuffix: Microsoft Intune
description: Microsoft Intune でアプリ保護ポリシーが正しくセットアップされ、動作していることをテストする方法について説明します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/08/2019
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.topic: conceptual
ms.technology: ''
ms.assetid: 15f8a838-0b69-412b-a42e-c6edb61f0cae
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 760ff85bc31cf66e66a3bf98f7da22d5ce48eee0
ms.sourcegitcommit: 364a7dbc7eaa414c7a9c39cf53eb4250e1ad3151
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59569442"
---
# <a name="how-to-validate-your-app-protection-policy-setup-in-microsoft-intune"></a>Microsoft Intune でアプリ保護ポリシーの設定を検証する方法

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

アプリ保護ポリシーが正しくセットアップされ、動作していることを検証します。 このガイドは、Azure Portal のアプリ保護ポリシーに適用されます。

## <a name="checking-for-symptoms"></a>現象の確認
アプリ保護はデータ保護ツールであるため、ユーザーが問題を報告することはほとんどありません。 アプリ保護の構成に問題がある場合、ユーザーは、アプリ保護がない場合と同じようにアクセスの制限を受けないため、問題があることがわかりません。 この理由により、アプリ保護の制限を意図的にテストできるユーザーの小規模なグループでアプリ保護ポリシーをパイロット運用して、アプリ保護の構成を検証することをお勧めします。

## <a name="what-to-check"></a>確認項目

テストの結果、アプリ保護ポリシーの動作が期待どおりに機能していないことがわかった場合は、以下の項目を確認します。

- ユーザーはアプリ保護のライセンスを取得していますか。
- ユーザーは O365 のライセンスを取得していますか。
- 各ユーザーのアプリ保護アプリの状態は期待どおりですか。 アプリの状態は、 **[確認済み]** か **[未確認]** のはずです。

### <a name="user-app-protection-status"></a>ユーザーのアプリ保護の状態
1. [Azure ポータル](https://portal.azure.com) にサインインします。
2. **[すべてのサービス]**  >  **[Intune]** の順に選択します。 Intune は **[監視 + 管理]** セクションにあります。
3. **[クライアント アプリ]**  >   **[アプリの保護状態]** を選択し、 **[割り当てられたユーザー]** タイルを選択します。 
4. **[アプリ レポート]** ページ上で、 **[ユーザーの選択]** を選択してユーザーとグループの一覧を表示させます。 
5. 一覧からユーザーを検索して選択し、 **[ユーザーの選択]** を選択します。 **[アプリ レポート]** ページの上部で、ユーザーがアプリ保護のライセンスを取得しているかどうかを確認できます。 また、ユーザーが O365 のライセンスを取得しているかどうか、およびすべてのユーザーのデバイスのアプリの状態を確認できます。

## <a name="what-to-do"></a>対処
ユーザーの状態に基づいて実行するアクションを次に示します。

- ユーザーがアプリ保護のライセンスを取得していない場合は、[Intune ライセンス](licenses.md)をそのユーザーに割り当てます。
- ユーザーが O365 のライセンスを取得していない場合、そのユーザーの[ライセンス](licenses.md)を取得します。
- ユーザーのアプリが **[チェックインされていません]** という状態で一覧に表示される場合は、そのアプリの[アプリ保護ポリシー](app-protection-policies-validate.md)を正しく構成したかどうかを確認します。
- [アプリ保護ポリシー](app-protection-policies-monitor.md)を適用するすべてのユーザー全体に、これらの条件が適用されていることを確認します。

## <a name="see-also"></a>関連項目

- [Intune アプリ保護ポリシーとは](app-protection-policies.md)
- [Intune を含むライセンス](licenses.md)
- [Intune にデバイスを登録できるようにライセンスをユーザーに割り当てる](licenses-assign.md)
- [アプリ保護ポリシーの設定を検証する方法](app-protection-policies-validate.md)
- [アプリ保護ポリシーを監視する方法](app-protection-policies-monitor.md)

