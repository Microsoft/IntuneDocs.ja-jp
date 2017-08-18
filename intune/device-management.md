---
title: "Intune を使用してデバイスを管理する"
titleSuffix: Intune on Azure
description: "Intune で管理するデバイスを確認し、そのデバイスで各種操作を実行する方法について説明します。\""
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d2412418-d91a-4767-a3d6-bc88bb29caa2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e0fc5337b92ac604a448038f685b27623b6153f9
ms.sourcegitcommit: ee7f69efe9f32a1d6bdeb1fab73d03dbfe1ae58c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/09/2017
---
# <a name="what-is-microsoft-intune-device-management"></a>Microsoft Intune デバイスの管理とは


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

**[デバイス]** ワークロードでは、管理対象のデバイスについての情報が得られ、そのデバイスでリモート タスクを実行できます。 このワークロードにアクセスするには、以下の手順に従います。

1. Azure ポータルにサインインします。
2. **[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
3. **[Intune]** ブレードで、**[デバイス]** を選択します。
4. ここで、表示されているリモート デバイスの操作を行うことができます。 表示されるアクションは、デバイス プラットフォームやデバイスの構成によって異なります。

## <a name="available-device-actions"></a>行えるデバイス アクション

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
    - [Windows 10 の PIN のリセット](device-windows-pin-reset.md)
    - [Android のリモート コントロール](device-profile-android-teamviewer.md)
    - [同期デバイス](device-sync.md)


## <a name="next-steps"></a>次のステップ

- 管理しているデバイスで実行されているアクションの状態を確認するには、**[デバイス アクション]** を選びます。 
![デバイス アクションの監視](./media/monitor-device-actions.png)
