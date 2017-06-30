---
title: "Intune デバイス インベントリの表示"
titleSuffix: Intune on Azure
description: "Intune で管理するデバイスを表示して、ハードウェアとインストールされているアプリを把握する方法について説明します。&quot;"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/27/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e71c6bdb-d75c-404f-8e38-24a663be81c2
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: c1e7356e27a8e146b9629c4c2f13f0b1f6861e84
ms.contentlocale: ja-jp
ms.lasthandoff: 06/08/2017


---

# <a name="how-to-view-intune-device-inventory"></a>Intune デバイス インベントリを表示する方法


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

**デバイス** ワークロードでは、ハードウェアの機能やインストールされているアプリなど、管理するデバイスを把握することができます。 

デバイス インベントリを表示するには、以下を行います。

1. Azure ポータルにサインインします。
2. **[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
3. **[Intune]** ブレードで、**[デバイス]** を選択します。

ここで、以下のいずれかを選択します。

- **[概要]** 登録したデバイスと、各デバイスで実行されているオペレーティング システムについての情報が得られます。
- **[管理]** - **[すべてのデバイス]** を選択すると、管理しているすべてのデバイスの一覧が表示されます。
    一覧からいずれかのデバイスを選択すると、[<*デバイス名*> **概要]** ブレードが開き、以下のいずれかを選択できます。
    - **[概要]** - デバイスの名前、所有者、BYOD デバイスかどうか、最終チェックイン日時など、デバイスについての一般情報が表示されます。

    - **[ハードウェア]** - デバイスの記憶域の空き容量、モデル、製造元など、デバイスについてのさらに詳細な情報が表示されます。
    ![管理対象デバイスのハードウェア インベントリ](./media/hardware-inventory.png)
    - **[検出されたアプリケーション]** - Intune でデバイスにインストールされていると判断されたすべてのアプリの一覧が表示されます。
    ![[検出されたアプリケーション] ノード](./media/detected-applications.png)
- **[監視]** - **[デバイス アクション]** を選択すると、管理対象のデバイスで実行されたデバイス アクションの一覧と、それらのアクションの現在の状態が表示されます。
![デバイス アクションの監視](./media/monitor-device-actions.png)




