---
title: "Windows PC のハードウェアとソフトウェアのインベントリを表示する"
description: "Intune ソフトウェア クライアントで PC として管理する Windows デスクトップに関するハードウェアとソフトウェアの情報を表示する方法。"
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 12/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3c10f4c9-520b-4864-92fc-a45a9f640ad4
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: 0fdb49e8742fa49f1c0c1b24d5f09bcaf08a0f0a
ms.contentlocale: ja-jp
ms.lasthandoff: 06/08/2017


---

# <a name="view-hardware-and-software-inventory-for-windows-pcs"></a>Windows PC のハードウェアとソフトウェアのインベントリを表示する

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune は、Intune ソフトウェア クライアントを使用して PC として管理されるデスクトップのハードウェアおよびソフトウェアに関する詳細情報を収集します。 以下の手順を参照して、次の項目を作成する方法を確認してください:

-   管理する PC のハードウェア性能に関する情報を一覧にしたレポート。

-   各 PC にインストールされているソフトウェアを一覧にしたレポート。

-   PC のインベントリを更新して、レポートのデータを最新の状態に保つ方法。

## <a name="to-display-information-about-pcs-you-manage"></a>管理する PC に関する情報を表示するには

1.  [Microsoft Intune 管理コンソール](https://manage.microsoft.com/)で、**[レポート]** &gt; **[コンピューター インベントリ レポート]** を選択します。

2.  **[新しいレポートの作成]** ページで、既定値をそのまま使用するか、カスタマイズして、レポートで返される結果をフィルター処理します。 たとえば、Windows 8.1 を実行する PC だけをレポートに表示するように選択できます。

3.  **[レポートの表示]** を選択すると、**[コンピューター インベントリ レポート]** が新しいウィンドウで開きます。

    レポートは、列見出し (**[名前]**、**[シャーシの種類]**、**[製造元]** など) を選択して並べ替えることができます。

## <a name="to-display-software-installed-on-pcs-you-manage"></a>管理する PC にインストールされているソフトウェアを表示するには

1.  [Microsoft Intune 管理コンソール](https://manage.microsoft.com/)で、**[レポート]** &gt; **[検出されたソフトウェアのレポート]** を選択します。

2.  **[新しいレポートの作成]** ページで、既定値をそのまま使用するか、カスタマイズして、レポートで返される結果をフィルター処理します。 たとえば、Microsoft が発行したソフトウェアだけをレポートに表示するように選択できます。

3.  **[レポートの表示]** を選択すると、**[検出されたソフトウェアのレポート]** が新しいウィンドウで開きます。

    レポートは、列見出し (**[名前]**、**[発行元]**、**[カテゴリ]** など) を選択して並べ替えることができます。 一覧の項目に付いている矢印を選択すると、一覧が展開して、更新プログラムの詳細 (更新プログラムがインストールされている PC など) が表示されます。

## <a name="to-refresh-computer-inventory-to-ensure-it-is-current"></a>コンピューターのインベントリを更新して最新の状態に保つには

1.  [Microsoft Intune 管理コンソール](https://manage.microsoft.com/)で、**[グループ]** &gt; **[すべてのデバイス]** (または、インベントリを更新する PC が含まれる別のグループ) を選択します。

2.  PC を 1 台選択するか、**Ctrl** キーを押しながら複数選択します。

3.  タスク バーで、**[リモート タスク]** &gt; **[インベントリの更新]** を選択します。

4.  タスクの状態を表示するには、ページの右下隅にある **[リモート タスク]** を選択します。

    **[タスクの状態]** ダイアログ ボックスが開き、現在のリモート タスク、タスクの状態、デバイス名、発生したエラーと、該当する場合は、トラブルシューティング情報へのリンクが表示されます。

### <a name="see-also"></a>関連項目

[Intune ソフトウェア クライアントを使用した一般的な Windows PC 管理タスク](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)
