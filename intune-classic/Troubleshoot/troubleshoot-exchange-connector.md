---
title: "Exchange Connector に関するトラブルシューティング"
description: "Intune Exchange Connector に関連する問題のトラブルシューティングを行います。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 07/26/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c5cb5465-fd8e-4524-83b9-ccdf3393b6dc
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 08a21197fd7c67aff037396e86a1555a8033daac
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/10/2017
---
# <a name="troubleshoot-the-exchange-connector"></a>Exchange Connector のトラブルシューティングを行う

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

このトピックでは、Intune Exchange Connector に関連する可能性のある問題のトラブルシューティングを行う方法について説明します。

## <a name="steps-for-checking-the-connector-configuration"></a>Connector の構成を確認する手順 

Exchange Connector の構成を調べて、問題を解決できるかどうかを確認します。

- Exchange Connector の初期セットアップで、通知アカウントを指定したことを確認します。
- Exchange Connector サービス アカウントに、Exchange Connector によって使用される PowerShell コマンドレットを実行するための適切なアクセス許可が必要です。
- Exchange Connector を構成するときに、Exchange Connector をホストするサーバーに近接するクライアント アクセス サーバー (CAS) を指定します。 特に O365 Dedicated を使用している場合は、CAS と Exchange Connector 間の通信の遅延によってデバイスの検出が遅くなる可能性があります。
- Exchange Connector と Exchange CAS の同期にはタイム ラグがあることに注意してください。 完全同期は 1 日に 1 回実行され、差分 (クイック) 同期は 2 時間間隔で実行されます。 新しく登録されたデバイスを持つユーザーは、アクセスの取得が遅れる可能性があります。
- 
## <a name="exchange-activesync-device-not-discovered-from-exchange"></a>Exchange ActiveSync device not discovered from Exchange (Exchange ActiveSync デバイスが Exchange から検出されない)
Exchange Connector が Exchange サーバーと同期しているかどうかを調べます。 これを行うには、ログで完全同期または差分同期を探します。Exchange Connector のログを確認します。 デバイスの参加以降、完全同期または差分同期が正常に完了している場合は、問題の原因から同期を排除します。 同期が行われていない場合は、同期ログを収集し、サポート依頼に添付してください。

- ユーザーが Intune ライセンスを持っていない場合、Exchange Connector は、それらのユーザーのデバイスを検出しません。
- ユーザーのプライマリ SMTP アドレスが AAD の UPN と異なる場合、Exchange Connector は、その Intune/AAD ユーザーのデバイスを検出しません。 プライマリ SMTP アドレスを修正してください。
- 検出サイクル中に Exchange Connector が通信する CAS が Exchange 2010 CAS のときに、Exchange 2010 と 2013 のメールボックス サーバーの両方がある場合、Exchange Connector は、Exchange 2013 ユーザーのデバイスを検出しません。 これを解決するには、Exchange 2013 CAS をポイントするように Exchange Connector を構成します。  この問題は主に O365 Dedicated のトポロジに関係していますが、ベスト プラクティスとして、その他のトポロジでも Exchange 2013 CAS をポイントすることを勧めします。
- Exchange Dedicated (O365 Dedicated) 環境では、初期セットアップ中に Exchange Connector が専用環境内の (2010 ではなく) Exchange 2013 CAS をポイントするように構成する必要があります。理由は、Exchange Connector は、Powershell コマンドレットを実行するときに、この CAS のみと通信するためです。


## <a name="using-powershell-to-get-more-data-on-exchange-connector-issues"></a>Powershell を使用して Exchange Connector の問題に関するより多くのデータを取得する
- メールボックスのすべてのモバイル デバイスの一覧を取得するには、Get-ActiveSyncDeviceStatistics -mailbox mbx を使用します。
- メールボックスの SMTP アドレスの一覧を取得するには、Get-Mailbox -Identity user | select emailaddresses | fl を使用します。
- デバイスのアクセス状態に関する詳細情報を取得するには、Get-CASMailbox <upn> | fl を使用します。

### <a name="next-steps"></a>次のステップ
このトラブルシューティング情報を使っても問題が解決しない場合は、「[Microsoft Intune のサポートを受ける方法](how-to-get-support-for-microsoft-intune.md)」の説明に従って Microsoft サポートにお問い合わせください。
