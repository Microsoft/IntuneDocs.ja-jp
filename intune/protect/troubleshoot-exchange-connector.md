---
title: Exchange Connector に関するトラブルシューティング
titleSuffix: Microsoft Intune
description: Intune のオンプレミス Exchange Connector に関連する問題のトラブルシューティングを行います。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/02/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: a7e3c742-295b-40bb-9afa-17f243062500
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d3d9473b68f0420670130203409abf477355d93f
ms.sourcegitcommit: 2506cdbfccefd42587a76f14ee50c3849dad1708
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 01/11/2020
ms.locfileid: "75885530"
---
# <a name="troubleshoot-the-intune-exchange-connector"></a>Intune Exchange Connector に関するトラブルシューティング

この記事では、Intune Exchange Connector に関連するイシューのトラブルシューティングを行う方法について説明します。

## <a name="before-you-start"></a>開始する前に

Intune で Exchange Connector の問題のトラブルシューティングを開始する前に、基本的な情報を収集して、堅固な基盤で作業しています。 この方法は、問題の性質をより深く理解し、より迅速に解決するのに役立ちます。

- プロセスがインストール要件を満たしていることを確認します。 「[オンプレミスの Intune Exchange Connector を設定する](exchange-connector-install.md)」をご覧ください。
- アカウントに Exchange と Intune の両方の管理者権限があることを確認します。
- 完全で正確なエラーメッセージのテキスト、詳細、およびメッセージが表示される場所に注意してください。
- 問題がいつ開始されたかを判断します。 
  - コネクタを初めて設定していますか? 
  - コネクタが正常に動作して失敗したか。
  - 動作していた場合、Intune 環境、Exchange 環境、またはコネクタソフトウェアを実行するコンピューターでどのような変更が発生したか。
- MDM 機関とは
- どのバージョンの Exchange を使用しますか?

### <a name="use-powershell-to-get-more-data-on-exchange-connector-issues"></a>PowerShell を使用して Exchange Connector のイシューに関するより多くのデータを取得する

- メールボックスのすべてのモバイルデバイスの一覧を取得するには、`Get-ActiveSyncDeviceStatistics -mailbox mbx` を使用します。
- メールボックスの SMTP アドレスの一覧を取得するには、`Get-Mailbox -Identity user | select emailaddresses | fl` を使用します。
- デバイスのアクセス状態に関する詳細情報を取得するには、`Get-CASMailbox <upn> | fl` を使用します

## <a name="review-the-connector-configuration"></a>コネクタの構成を確認する

[内部設置型 Exchange connector の要件](exchange-connector-install.md#intune-exchange-connector-requirements)を確認して、環境とコネクタが正しく構成されていることを確認します。 

### <a name="general-considerations-for-the-connector"></a>コネクタに関する一般的な考慮事項

- ファイアウォールとプロキシサーバーが、Intune Exchange Connector と Intune サービスをホストするサーバー間の通信を許可していることを確認します。

- Intune Exchange Connector と Exchange クライアントアクセスサーバー (CAS) をホストするコンピューターは、ドメインに参加しており、同じ LAN 上にある必要があります。 Intune Exchange connector によって使用されるアカウントに必要なアクセス許可が追加されていることを確認します。

- 通知アカウントは、*自動検出*の設定を取得するために使用されます。 Exchange での Autodisover の詳細については、「 [Exchange Server の自動検出サービス](https://docs.microsoft.com/exchange/architecture/client-access/autodiscover?view=exchserver-2016)」を参照してください。

- Intune Exchange Connector は、通知アカウントの資格情報を使用して、通知電子メールメッセージを [*開始*] リンクと共に送信することで、EWS URL に要求を送信します (intune に登録する場合)。 Android 非 Knox デバイスの場合は、*はじめ*に」リンクを使用して登録する必要があります。 それ以外の場合、これらのデバイスは条件付きアクセスによってブロックされます。

### <a name="common-issues-for-connector-configurations"></a>コネクタ構成に関する一般的な問題

- **アカウントのアクセス許可**:[Microsoft Intune Exchange Connector] ダイアログ ボックスで、[必須の Windows PowerShell Exchange コマンドレット](exchange-connector-install.md#exchange-cmdlet-requirements)を実行するための適切なアクセス許可を持つユーザー アカウントが指定されていることを確認します。
- **通知電子メールメッセージ**: 通知を有効にし、通知アカウントを指定します。
- **クライアントアクセスサーバーの同期**: exchange connector を構成するときに、exchange connector をホストしているサーバーに対して可能なネットワーク待ち時間が最も短い ca を指定します。 特に Exchange Online Dedicated を使用している場合は、CAS と Exchange Connector 間の通信の遅延によってデバイスの検出が遅くなる可能性があります。
- **同期スケジュール**:新しく登録されたデバイスを持つユーザーは、Exchange Connector が Exchange CAS と同期するまで、アクセスに遅延が生じる可能性があります。 完全同期は 1 日に 1 回実行され、差分 (クイック) 同期は 1 日に数回実行されます。 遅延を最小限に抑えるために、[クイック同期または完全同期を手動で適用](exchange-connector-install.md#manually-force-a-quick-sync-or-full-sync)することができます。

## <a name="next-steps"></a>次のステップ
次の記事は、一般的な問題と特定のエラーを解決するのに役立ちます。

- [Intune Exchange Connector の一般的な問題を解決](troubleshoot-exchange-connector-common-problems.md)します。
- [Intune Exchange Connector の一般的なエラーを解決](troubleshoot-exchange-connector-common-errors.md)します。

サポートまたは Intune コミュニティから支援を受ける:

- 「Intune コンソールを使用して問題のトラブルシューティングを行う」また[は「Microsoft](../fundamentals/get-support.md)でサポートケースを開く」を参照してください。 
- [Microsoft Intune フォーラム](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod)に問題を投稿してください。  
