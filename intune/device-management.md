---
title: Microsoft Intune でデバイスを管理する - Azure | Microsoft Docs
description: デバイス一覧の csv 形式へのエクスポートなど、Microsoft Intune で管理するデバイスを確認します。また、Azure Active Directory に参加しているデバイスを表示したり、TeamViewer Connector を使用して IT 管理者がリモートで Android デバイスのトラブルシューティングを行えるようにしたり、デバイスで実行できるすべての操作を表示します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/02/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d2412418-d91a-4767-a3d6-bc88bb29caa2
ms.suite: ems
ms.custom: intune-azure; get-started
ms.openlocfilehash: 891b50b2280636c7a5df8ecc1a01bb10723122b5
ms.sourcegitcommit: d8edd1c3d24123762dd6d14776836df4ff2a31dd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2018
ms.locfileid: "51576736"
---
# <a name="what-is-microsoft-intune-device-management"></a>Microsoft Intune デバイスの管理とは

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

IT 管理者はデータをリスクから保護しながら、ユーザーが自分の作業に必要なリソースがマネージド デバイスから提供されるようにする必要があります。

**[デバイス]** ワークロードでは、管理対象のデバイスについての情報が得られ、そのデバイスでリモート タスクを実行できます。

## <a name="get-to-your-devices"></a>デバイスにアクセスする

1. [Azure ポータル](https://portal.azure.com)にサインインします。
2. **[すべてのサービス]** を選択し、**[Intune]** をフィルターとして適用し、**[Microsoft Intune]** を選択します。
3. **[デバイス]** を選択します。 このビューには、次のような、個々のデバイスの詳細情報と、デバイスでできることが示されます。

   - **[概要]** には登録済みデバイスのビジュアル スナップショットが表示されます。また、Android、iOS などのさまざまなプラットフォームを使用しているデバイスの数が表示されます。
   - **[すべてのデバイス]** には、管理する登録済みデバイスの一覧が示されます。

     **エクスポート**機能を使用して、10,000 単位 (Internet Explorer) または 30,000 単位 (Microsoft Edge、Chrome) ですべてのデバイスの .csv 一覧を作成します。

     任意のデバイスを選択し、ハードウェアの詳細、インストールされているアプリ、そのコンプライアンス ポリシーの状態など、[デバイスに関する追加の詳細情報を表示](device-inventory.md)します。

   - **[Azure AD デバイス]** には、Azure Active Directory (Azure AD) に登録されている、または参加しているデバイスの一覧が示されます。 Azure AD のデバイス管理の概要については、[こちら](https://docs.microsoft.com/azure/active-directory/device-management-introduction)を参照してください。
   - **[デバイス アクション]** には、アクション、その状態、アクションを開始したユーザー、時刻など、さまざまなデバイスで実行されたリモート アクションの履歴が含まれます。

     ![デバイス アクションの監視のスクリーンショット](./media/monitor-device-actions.png)

   - **[監査ログ]** は、Intune で変更を行うアクティビティのレコードです。 [[監査ログ]](monitor-audit-logs.md) には詳細が示されます。
   - **[TeamViewer Connector]** は、Intune で管理されている Android デバイスのユーザーが、IT 管理者からリモート アシスタンスを受けられるようにするサービスです。 TeamViewer については、[こちら](device-profile-android-teamviewer.md)を参照してください。
   - **[ヘルプとサポート]** では、トラブルシューティングのヒント、サポートの依頼、Intune の状態の確認に関するショートカットが提供されます。

## <a name="available-device-actions"></a>行えるデバイス アクション
表示されるアクションは、デバイス プラットフォームやデバイスの構成によって異なります。

- [デバイス インベントリを表示する](device-inventory.md)
- 以下のリモート デバイス アクションを実行します。
    - [削除](devices-wipe.md#retire)
    - [ワイプ](devices-wipe.md#wipe)
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

## <a name="next-steps"></a>次の手順

- **[すべてのデバイス]** で、デバイスを選択し、その特定のデバイスに関する詳細情報を表示します。
- 管理しているデバイスで実行されているアクションの状態を確認するには、**[デバイス アクション]** を選びます。
