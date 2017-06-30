---
title: "Intune を使用してデバイスを管理する"
titleSuffix: Intune on Azure
description: "Intune で管理するデバイスを確認し、そのデバイスで各種操作を実行する方法について説明します。&quot;"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/27/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d2412418-d91a-4767-a3d6-bc88bb29caa2
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 76bda2a2045c99923d4b667d30b6a3d6474a10d3
ms.openlocfilehash: 8f17a67e18a3e8434f2dadd8bf6fa79bedbffe86
ms.contentlocale: ja-jp
ms.lasthandoff: 06/09/2017


---

# <a name="what-is-microsoft-intune-device-management"></a>Microsoft Intune デバイスの管理とは


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

**[デバイス]** ワークロードでは、管理対象のデバイスについての情報が得られ、そのデバイスでリモート タスクを実行できます。 このワークロードにアクセスするには、以下の手順に従います。

1. Azure ポータルにサインインします。
2. **[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
3. **[Intune]** ブレードで、**[デバイス]** を選択します。

次のアクションを実行できるようになります。 詳しくは、関連するリンクのいずれかをクリックしてください。

- [デバイス インベントリを表示する](device-inventory.md)
- 以下のリモート デバイス アクションを実行します。
    - [会社データの削除](device-company-data-remove.md) 
    - [出荷時の設定に戻す](device-factory-reset.md)
    - [リモート ロック](device-remote-lock.md)
    - [パスコードのリセット](device-passcode-reset.md)
    - [アクティブ化ロックのバイパス](device-activation-lock-bypass.md)
    - [新しく開始](device-fresh-start.md)
    - [紛失モード](device-lost-mode.md)
    - [デバイスを検索する](device-locate.md)
    - [再起動](device-restart.md)
    - [Android のリモート コントロール](device-profile-android-teamviewer.md)
- **[デバイス アクション]** を選択して、管理するデバイスで実行されたデバイス アクションの一覧と、それらのアクションの現在の状態を表示します。 
![デバイス アクションの監視](./media/monitor-device-actions.png)
