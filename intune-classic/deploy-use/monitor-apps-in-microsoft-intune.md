---
title: "アプリの展開を監視する"
description: "Intune を使用して展開したアプリを監視する方法について説明します。"
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 11/10/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5daad56d-71c8-455b-8a55-f8b33e279a8a
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f583dba7e5ade0e06bc68589623558de0de667c8
ms.sourcegitcommit: 2459bfda07a2afd2cfcd94a1972a3fb2e565ce8d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/22/2018
---
# <a name="monitor-app-deployments-in-microsoft-intune"></a>Microsoft Intune でアプリの展開を監視する

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

## <a name="monitor-an-app-deployment"></a>アプリの展開を監視する
Intune 管理コンソールで管理対象アプリの展開の状態を確認できます。 <!---App status is displayed in real-time. You don't have to wait for the device to check-in before you can see this.--->

### <a name="to-view-apps-that-you-manage-and-their-status"></a>管理するアプリとその状態を確認するには
**[アプリ]** ワークスペースで、**[アプリ]** ノードを選択し、**[アプリ]** を選択します。

管理しているアプリの一覧が表示されます。 コンソール ウィンドウの下のウィンドウでアプリを選択すると、インストール状態が表示されます。 さらに詳細を表示するには、この状態を選択します。 たとえば、状態に **[1 人のユーザーがこのソフトウェアを利用しています]** と表示されている場合、そのメッセージを選択すると、ユーザーの名前を確認できます。

> [!TIP]
> **[フィルター]** ドロップダウン リストを利用すると、インストールできなかったアプリや正常に展開されたアプリなど、指定した基準に一致するアプリのみを表示できます。
>
> ![アプリ フィルターの例](./media/app-filters.png)

また、**[ダッシュボード]** ワークスペースには、アプリの状態の概要が表示されます。 概要内のどこでもよいのでクリックすると、アプリの一覧が表示されます。

## <a name="to-view-more-detailed-information-about-an-app"></a>アプリに関する詳細を表示するには
アプリの一覧で、アプリを選択し、**[プロパティの表示]** を選択します。

アプリの **[ソフトウェア プロパティ]** ページで、次のいずれかのタブを選択します。**[全般]** - アプリとそのインストール状態に関する一般的な情報が表示されます。**[デバイス]** - アプリの対象となる展開が正常にインストールされているデバイスが表示されます。**[ユーザー]** - アプリの対象となる展開が正常にインストールされているデバイスのユーザーが表示されます。

前述のように、**[フィルター]** ドロップダウン リストを利用し、各タブに表示される値を構成できます。
