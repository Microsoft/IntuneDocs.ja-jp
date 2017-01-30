---
title: "Microsoft Intune での MAM ポリシーの監視 | Microsoft Docs"
description: "ポリシーを持つユーザー数を確認し、詳細を調べるためにドリルダウンします。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d3aa6c74-6b5d-4b50-aa66-a040ec44393e
ms.reviewer: joglocke
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9e208608d50c9b5f7fe66743de0d3c7e741dbfbd
ms.openlocfilehash: 2a18ad7226c6fc6de0277f1f20443ea64dc8b918


---

# <a name="monitor-mobile-app-management-policies-with-microsoft-intune"></a>Microsoft Intune でのモバイル アプリ管理ポリシーの監視

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

モバイル アプリ管理 (MAM) ポリシーをセットアップしてユーザーに適用した後は、[Azure Portal](https://portal.azure.com) でコンプライアンスの状態を監視できます。 Azure ポータルには、ポリシーによって影響を受けるユーザー、コンプライアンスの状態、ユーザーに対して発生する可能性がある問題に関する情報が含まれます。
## <a name="summary-view"></a>概要ビュー
**[Intune モバイル アプリケーション管理]** ブレードでは、コンプライアンス状態の概要を確認できます。


![[Intune モバイル アプリケーション管理] ブレードの [概要] タイル](../media/mam-azure-portal-user-status-summary.png)

-   **[ユーザー]**: ポリシーに関連付けられているアプリを使用している社内ユーザーの合計数。

-   **[ポリシーによって管理されています]**: 作業コンテキストで少なくとも 1 つのアプリを使用したユーザーの数。

-   **[ポリシーなし]**: ポリシーに関連付けられたアプリを使用しているが、ポリシーの対象にはなっていないユーザーの数。 これらのユーザーをポリシーに追加することを検討できます。

- **[フラグ付きのユーザー]**: 問題が発生しているユーザーの数。 **[フラグ付きのユーザー]** では、現時点で脱獄されたデバイスを使用しているユーザーのみが報告されます。


## <a name="detailed-view"></a>詳細ビュー
**[ユーザーの状態]** タイルおよび **[フラグ付きのユーザー]** タイルを選択すると、概要の詳細ビューを表示できます。

### <a name="user-status"></a>ユーザーの状態
1 人のユーザーを検索し、そのユーザーのコンプライアンス状態を確認できます。 **[アプリ レポート]** ブレードには、選択したユーザーの次の情報が表示されます。
- ユーザー アカウントに関連付けられているデバイス

- デバイスのアプリと MAM ポリシー

- 状態:

  - **[チェックイン済み]**: ポリシーはユーザーに展開され、アプリが 1 回以上作業コンテキストで使用されました。

  - **[チェックインされていません]**: ポリシーはユーザーに展開されましたが、それ以降にアプリが作業コンテキストで使用されていません。

>[!NOTE]
> 検索したユーザーに MAM ポリシーが展開されていない場合は、そのユーザーがいずれのアプリ ポリシーの対象でもないことを知らせるメッセージが表示されます。

ユーザーのレポートを表示するには次のようにします。

1.  ユーザーを選択するには、**[概要]** タイルを選択するか、**[設定]** ブレードで **[ユーザーによるアプリ レポート]** オプションを選択します。

    ![[設定] ブレードのアプリ レポート オプション](../media/mam-azure-portal-app-reporting-by-user-settings-blade.png)

2. 表示される **[アプリ レポート]** ブレードで、**[ユーザーの選択]** を選択して Azure Active Directory ユーザーを検索します。

    ![[アプリ レポート] ブレードのユーザー選択オプション](../media/mam-azure-portal-app-reporting-select-user.png)

3. リストからユーザーを選択します。 そのユーザーのコンプライアンス状態の詳細が表示されます。

    ![アプリ レポートの詳細](../media/mam-azure-portal-app-reporting-by-user.png)

### <a name="flagged-users"></a>フラグ付きのユーザー
詳細ビューには、エラー メッセージ、エラー発生時にアクセスされていたアプリ、デバイスのプラットフォーム、タイムスタンプが表示されます。  

### <a name="see-also"></a>関連項目
[iOS アプリ間のデータ転送を管理する](manage-data-transfer-between-ios-apps-with-microsoft-intune.md)

* [MAM ポリシーを使用して Android アプリを管理するときの注意点](user-experience-for-mam-enabled-android-apps-with-microsoft-intune.md)
* [MAM ポリシーを使用して iOS アプリを管理するときの注意点](user-experience-for-mam-enabled-ios-apps-with-microsoft-intune.md)



<!--HONumber=Dec16_HO3-->


