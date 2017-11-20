---
title: "アプリ情報と割り当てを監視する方法"
titlesuffix: Azure portal
description: "ユーザーまたはデバイスにアプリを割り当てた後は、この情報を参考にして、その状態を監視できます。\""
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 10/20/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 64e5133d-1e23-4ee6-b556-f5d32c0e95da
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3736b6d43f5cd3b6c75097a2ceabebffd75f0caa
ms.sourcegitcommit: e9f9fccccef691333143b7523d1b325ee7d1915a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/02/2017
---
# <a name="how-to-monitor-app-information-and-assignments-with-microsoft-intune"></a>Microsoft Intune でアプリ情報と割り当てを監視する方法

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune には、管理しているアプリのプロパティと、割り当ての状態を監視する方法が複数あります。

1. Azure ポータルにサインインします。
2. **[その他のサービス]** > **[監視 + 管理]** + **[Intune]** の順に選択します。
3. **[モバイル アプリ]** ワークロードで、**[管理]** グループの **[アプリ]** を選択します。
     
    ![[アプリ インストールの状態] ブレード。](./media/monitor-apps.png)
5. アプリ ブレードの一覧で、アプリを選択します。 [<*アプリ名*> **デバイスのインストール状態]** ブレードが表示されます。

デバイスのインストール状態レポートには、次の列があります。

1.  **デバイス名**: デバイスの種類の名前。
2.  **ユーザー名**: ユーザーの名前。
3.   **プラットフォーム**: デバイスにインストールされているオペレーティング システム。
4.  **バージョン**: アプリケーションのバージョン番号。
5.   **状態**: アプリの状態として、**[インストール済み]**、**[未インストール]**、**[インストール保留中です]**、**[エラー]** があります。
6. **状態の詳細**: デバイスのアプリの状態に関する読み取り可能な説明。
7. **最後のチェックイン**: デバイスが Intune に最後にチェックインした時刻。

次に、以下のいずれかの操作を実行して、アプリとその割り当てに関する情報を取得します。

## <a name="general"></a>全般

- **概要** - アプリの基本的な概要と、そのアプリの割り当ての状態に関する情報が表示されます。 いずれかのグラフを選択して、**[デバイスのインストール状態]** ブレードまたは **[ユーザーのインストール状態]** ブレードを開き、詳細情報を表示することもできます。

## <a name="manage"></a>コンピューターの

- **プロパティ** - 選択したアプリに関する情報を表示および変更することができます。 アプリのプロパティの詳細については、「[アプリを Microsoft Intune に追加する方法](apps-add.md)」を参照してください。
- **割り当て** - このアプリの割り当てに関する情報が表示されます。 詳細については、「[How to assign apps to groups with Microsoft Intune (Microsoft Intune を使ってアプリをグループに割り当てる方法)](apps-deploy.md)」を参照してください。

## <a name="monitor"></a>モニター

- **デバイスのインストール状態** - デバイス名、オペレーティング システム、デバイスの最終チェックイン時刻、アプリ インストールの状態など、選択したアプリに割り当てられている各デバイスの詳細情報が表示されます。
- **ユーザーのインストール状態** - ユーザーがすべてのデバイスにインストールしているアプリ数、インストールエラーに関する情報など、選択したアプリを割り当てられているユーザーの詳細情報が表示されます。