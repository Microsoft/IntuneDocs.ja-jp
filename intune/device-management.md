---
title: "Intune を使用してデバイスを管理する"
titlesuffix: Azure portal
description: "Intune で管理するデバイスを確認し、そのデバイスで各種操作を実行する方法について説明します。\""
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 08/31/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d2412418-d91a-4767-a3d6-bc88bb29caa2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ca40eee8a53fa3e8b2610ce414f0037180d4beaf
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/09/2017
---
# <a name="what-is-microsoft-intune-device-management"></a>Microsoft Intune デバイスの管理とは


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

**[デバイス]** ワークロードでは、管理対象のデバイスについての情報が得られ、そのデバイスでリモート タスクを実行できます。 このワークロードにアクセスするには、以下の手順に従います。

1. Azure ポータルにサインインします。
2. **[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
3. **[Intune]** ブレードで、**[デバイス]** を選択します。
4. デバイスに関する情報を表示したり、一覧にあるリモート デバイス アクションを実行したりできます。

## <a name="available-device-actions"></a>行えるデバイス アクション
表示されるアクションは、デバイス プラットフォームやデバイスの構成によって異なります。

- [デバイス インベントリを表示する](device-inventory.md)
- 以下のリモート デバイス アクションを実行します。
    - [会社データの削除](devices-wipe.md#remove-company-data)
    - [出荷時の設定に戻す](devices-wipe.md#factory-reset)
    - [リモート ロック](device-remote-lock.md)
    - [パスコードのリセット](device-passcode-reset.md)
    - [アクティブ化ロックをバイパスする](device-activation-lock-bypass.md) (iOS のみ)
    - [新たに開始](device-fresh-start.md) (Windows のみ)
    - [紛失モード](device-lost-mode.md) (iOS のみ)
    - [デバイスを検索する](device-locate.md) (iOS のみ)
    - [再起動](device-restart.md) (Windows のみ)
    - [Windows 10 の PIN のリセット](device-windows-pin-reset.md)
    - [Android のリモート コントロール](device-profile-android-teamviewer.md)
    - [同期デバイス](device-sync.md)


## <a name="next-steps"></a>次のステップ

- 管理しているデバイスで実行されているアクションの状態を確認するには、**[デバイス アクション]** を選びます。
![デバイス アクションの監視](./media/monitor-device-actions.png)
