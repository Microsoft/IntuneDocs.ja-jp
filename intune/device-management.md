---
title: "Intune を使用してデバイスを管理する"
titleSuffix: Intune on Azure
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
ms.openlocfilehash: 0686b3ece3a929cb06a29f4e58046872b70ec926
ms.sourcegitcommit: b8987b8dfb009ea55678d7f640ac5f18a6ab167e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2017
---
# <a name="what-is-microsoft-intune-device-management"></a>Microsoft Intune デバイスの管理とは


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

IT 管理者はデータをリスクから保護しながら、エンド ユーザーが自分の作業に必要なリソースが管理されたデバイスから提供されるようにする必要があります。

**[デバイス]** ワークロードでは、管理対象のデバイスについての情報が得られ、そのデバイスでリモート タスクを実行できます。 このワークロードにアクセスするには、以下の手順に従います。

1. Azure ポータルにサインインします。
2. **[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
3. **[Intune]** で、**[デバイス]** を選択します。
4. 次のデバイスに関する情報を確認して、リモート デバイスの操作を実行することができます。
    - **[概要]** - 管理可能な登録済みデバイスのスナップショット。
    - **[すべてのデバイス]** - 管理する登録済みデバイスの一覧。 表示する情報を絞り込むには、**[フィルター]** または **[列]** を選択します。 [デバイス インベントリを表示する](device-inventory.md)には、デバイスを選択します。
    - **[Azure AD デバイス]** - Azure Active Directory (AD) に登録されている、または参加しているデバイスの一覧。 Azure AD のデバイス管理の概要については、[こちら](https://docs.microsoft.com/azure/active-directory/device-management-introduction)を参照してください。
    - **[デバイス アクション]** - アクション、その状態、アクションを開始したユーザー、時刻などの、デバイスに実行されたリモート アクションの履歴。

    ![デバイス アクションの監視](./media/monitor-device-actions.png)

    - **[TeamViewer]** - TeamViewer サービスを使用すると、Intune で管理されている Android デバイスのユーザーが、IT 管理者からリモート アシスタンスを受けられるようになります。 TeamViewer については、[こちら](device-profile-android-teamviewer.md)を参照してください。

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
