---
title: 管理者の役割用のコンソール ビューをカスタマイズする
description: このトピックは、Intune 管理コンソール ビューをフィルター処理して、管理者がそれぞれの役割に応じて必要な項目のみが表示されるように設定するときに役立ちます。
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 12/27/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e0783eaa-67dc-410e-9e80-4d3aa72f36d8
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9baa0325a90e152ffd6cf6a31cdd0a458588758a
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2018
---
# <a name="customize-intune-console-views-according-to-admin-roles"></a>管理者の役割に応じて Intune コンソール ビューをカスタマイズする

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune 管理コンソール ビューをフィルター処理して、管理者がそれぞれの役割に応じて確認する必要がある項目のみが表示されるように設定できます。 たとえば、管理コンソールのオペレーターにのみ、マルウェア定義の更新やデバイスのパスコードのリセットを許可できます。 これは、特定のユーザーに割り当てる事前設定された**指定**を使用することで行います。 これらのユーザーが管理コンソールにアクセスすると、そのユーザーに対する指定に応じて、特定のアイテムだけが表示されます。

## <a name="to-create-a-custom-view"></a>カスタム ビューを作成するには

1.  [Microsoft Intune 管理コンソール](https://manage.microsoft.com)で、**[管理]** &gt; **[サービス管理者]** をクリックします。

2.  サービス管理者の一覧から、指定を変更するユーザーを選択し、**[アクセスの管理]** をクリックします。

3.  **[アクセスの管理]** ダイアログ ボックスで、選択したユーザーに付与するアクセス レベルを選択します。 次の項目から選択できます。

    -   **フル アクセス**
    -   **読み取り専用アクセス**
    -   **ヘルプデスク - グループ ノード**

    フル アクセスと読み取り専用アクセスは、特に説明することはありません。 <!--- **Helpdesk - Groups Node** allows users to choose from one of the following designations that provide custom levels of access to the Intune admin console:--->

    **ヘルプデスク - グループ ノード**は、次に示す管理者が確認できる項目と実行できる操作を制限します。

    -   ユーザーとデバイスの一覧を表示する。 管理者は、フィルターを使用してビューを変更することはできません。 ただし、グループ フィルターを使用して、管理者に表示される内容を変更できます。 詳しくは、「[Microsoft Intune でユーザーとデバイスの管理にグループを使用する](use-groups-to-manage-users-and-devices-with-microsoft-intune.md)」を参照してください。

    -   ユーザーとデバイスの一覧を印刷する。

    -   ユーザーとデバイスの一覧をエクスポートする。

    -   ユーザーまたはデバイスのプロパティを表示する。

    -   次のリモート タスクを実行する。

        -   マルウェアのフル スキャンの実行

        -   マルウェアのクイック スキャンの実行

        -   コンピューターの再起動

        -   マルウェア定義の更新

        -   ポリシーの更新

        -   インベントリの更新

        -   デバイスのリモート ロック

        -   パスコードのリセット

構成した管理者が次に Intune 管理コンソールを開いたとき、指定したアクセス レベルが与えられます。
