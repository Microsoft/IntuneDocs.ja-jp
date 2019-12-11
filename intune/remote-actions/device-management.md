---
title: Microsoft Intune でデバイスを管理する - Azure | Microsoft Docs
description: デバイス一覧の csv 形式へのエクスポートなど、Microsoft Intune で管理するデバイスを確認します。また、Azure Active Directory に参加しているデバイスを表示したり、TeamViewer Connector を使用して IT 管理者がリモートで Android デバイスのトラブルシューティングを行えるようにしたり、デバイスで実行できるすべての操作を表示します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/14/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d2412418-d91a-4767-a3d6-bc88bb29caa2
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: b957857702de10e10c581364f2c34c869026810d
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74819750"
---
# <a name="what-is-microsoft-intune-device-management"></a>Microsoft Intune デバイスの管理とは

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

IT 管理者はデータをリスクから保護しながら、ユーザーが自分の作業に必要なリソースがマネージド デバイスから提供されるようにする必要があります。

**[デバイス]** ワークロードでは、管理対象のデバイスについての情報が得られ、そのデバイスでリモート タスクを実行できます。

## <a name="get-to-your-devices"></a>デバイスにアクセスする

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。
3. **[デバイス]** を選択します。 このビューには、次のような、個々のデバイスの詳細情報と、デバイスでできることが示されます。

   - **[概要]** には登録済みデバイスのビジュアル スナップショットが表示されます。また、Android、iOS などのさまざまなプラットフォームを使用しているデバイスの数が表示されます。
   - **[すべてのデバイス]** には、管理する登録済みデバイスの一覧が示されます。

     **エクスポート**機能を使用して、10,000 単位 (Internet Explorer) または 30,000 単位 (Microsoft Edge、Chrome) ですべてのデバイスの .csv 一覧を作成します。

     任意のデバイスを選択し、ハードウェアの詳細、インストールされているアプリ、そのコンプライアンス ポリシーの状態など、[デバイスに関する追加の詳細情報を表示](device-inventory.md)します。

   - **[Azure AD デバイス]** には、Azure Active Directory (Azure AD) に登録されている、または参加しているデバイスの一覧が示されます。 Azure AD のデバイス管理の概要については、[こちら](https://docs.microsoft.com/azure/active-directory/device-management-introduction)を参照してください。
   - **[デバイス アクション]** には、アクション、その状態、アクションを開始したユーザー、時刻など、さまざまなデバイスで実行されたリモート アクションの履歴が含まれます。

     ![デバイス アクションの監視のスクリーンショット](./media/device-management/monitor-device-actions.png)

   - **[監査ログ]** は、Intune で変更を行うアクティビティのレコードです。 [[監査ログ]](../fundamentals/monitor-audit-logs.md) には詳細が示されます。
   - **[TeamViewer Connector]** は、Intune で管理されている Android デバイスのユーザーが、IT 管理者からリモート アシスタンスを受けられるようにするサービスです。 TeamViewer については、[こちら](teamviewer-support.md)を参照してください。
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
  - [Android のリモート コントロール](teamviewer-support.md)
  - [同期デバイス](device-sync.md)
  - [デバイス名の変更](device-rename.md)
  - [カスタム通知の送信](custom-notifications.md#send-a-custom-notification-to-a-single-device) (Android、iOS)
  - [BitLocker キーの交換](../protect/encrypt-devices.md#rotate-bitlocker-recovery-keys) (Windows のみ)

## <a name="next-steps"></a>次の手順

- **[すべてのデバイス]** で、デバイスを選択し、その特定のデバイスに関する詳細情報を表示します。
- 管理しているデバイスで実行されているアクションの状態を確認するには、 **[デバイス アクション]** を選びます。
