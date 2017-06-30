---
title: "アプリ情報と割り当てを監視する方法"
titleSuffix: Intune on Azure
description: "ユーザーまたはデバイスにアプリを割り当てた後は、この情報を参考にして、その状態を監視できます。&quot;"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 64e5133d-1e23-4ee6-b556-f5d32c0e95da
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: d588ecc8f2e211b5a8ccdfe7b7720869cc6327b8
ms.contentlocale: ja-jp
ms.lasthandoff: 06/08/2017

---

# <a name="how-to-monitor-app-information-and-assignments-with-microsoft-intune"></a>Microsoft Intune でアプリ情報と割り当てを監視する方法

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune には、管理しているアプリのプロパティと、割り当ての状態を監視する方法が複数あります。

1. **[モバイル アプリ]** ワークロードで、**[管理]** > **[アプリ]** の順に選択します。
2. アプリの一覧ブレードで、情報を表示するアプリを選択します。 [*<アプリ名*> **デバイスのインストール状態]** ブレードが表示されます。![[アプリ インストールの状態] ブレード。](./media/monitor-apps.png)

次に、以下のいずれかの操作を実行して、アプリとその割り当てに関する情報を取得します。

## <a name="general"></a>全般

- **概要** - アプリの基本的な概要と、そのアプリの割り当ての状態に関する情報が表示されます。 いずれかのグラフを選択して、**[デバイスのインストール状態]** ブレードまたは **[ユーザーのインストール状態]** ブレードを開き、詳細情報を表示することもできます。

## <a name="manage"></a>コンピューターの

- **プロパティ** - 選択したアプリに関する情報を表示および変更することができます。 アプリのプロパティの詳細については、「[アプリを Microsoft Intune に追加する方法](apps-add.md)」を参照してください。
- **割り当て** - このアプリの割り当てに関する情報が表示されます。 詳細については、「[How to assign apps to groups with Microsoft Intune (Microsoft Intune を使ってアプリをグループに割り当てる方法)](apps-deploy.md)」を参照してください。

## <a name="monitor"></a>モニター

- **デバイスのインストール状態** - デバイス名、オペレーティング システム、デバイスの最終チェックイン時刻、アプリ インストールの状態など、選択したアプリに割り当てられている各デバイスの詳細情報が表示されます。
- **ユーザーのインストール状態** - ユーザーがすべてのデバイスにインストールしているアプリ数、インストールエラーに関する情報など、選択したアプリに割り当てられているユーザーの詳細情報が表示されます。
