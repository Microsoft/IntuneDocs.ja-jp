---
title: Exchange Connector に関するトラブルシューティング
description: Intune のオンプレミス Exchange Connector に関連する問題のトラブルシューティングを行います。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 6/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a7e3c742-295b-40bb-9afa-17f243062500
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 85b4764ef5797ad592744e3c519f82f3f1cdd1bb
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2018
ms.locfileid: "52190067"
---
# <a name="troubleshoot-the-intune-on-premises-exchange-connector"></a>Intune のオンプレミス Exchange Connector のトラブルシューティング

この記事では、Intune のオンプレミス Exchange Connector に関連する問題のトラブルシューティングを行う方法について説明します。

## <a name="steps-for-checking-the-connector-configuration"></a>Connector の構成を確認する手順 

[Intune オンプレミス Exchange Connector の設定](exchange-connector-install.md)を調べて、Connector が正しく構成されているかどうかを確認します。 一般的ないくつかの問題を次に示します。 修正を行ったら、問題が解決されているかどうかを確認します。

 - [Microsoft Intune Exchange Connector] ダイアログ ボックスで、[必須の Windows PowerShell Exchange コマンドレット](exchange-connector-install.md#exchange-cmdlet-requirements)を実行するための適切なアクセス許可を持つユーザー アカウントが指定されていることを確認します。
- 通知を有効にし、通知アカウントを指定します。
 - Exchange Connector を構成するときに、Exchange Connector をホストするサーバーに近接するクライアント アクセス サーバー (CAS) を指定します。 特に Exchange Online Dedicated を使用している場合は、CAS と Exchange Connector 間の通信の遅延によってデバイスの検出が遅くなる可能性があります。
 - 新しく登録されたデバイスを持つユーザーは、Exchange Connector が Exchange CAS と同期するまで、アクセスに遅延が生じる可能性があります。 完全同期は 1 日に 1 回実行され、差分 (クイック) 同期は 1 日に数回実行されます。  遅延を最小限に抑えるために、[クイック同期または完全同期を手動で適用](exchange-connector-install.md#manually-force-a-quick-sync-or-full-sync)することができます。
 
## <a name="exchange-activesync-device-not-discovered-from-exchange"></a>Exchange ActiveSync device not discovered from Exchange (Exchange ActiveSync デバイスが Exchange から検出されない)
[Exchange Connector のアクティビティを監視](exchange-connector-install.md#on-premises-exchange-connector-high-availability-support)することで、Exchange Connector が Exchange Server と同期しているかどうかを調べます。 デバイスの参加以降、完全同期またはクイック同期が正常に完了した場合は、以下に一覧した他に考えられる問題が発生していないか確認できます。 同期が行われていない場合は、同期ログを収集し、サポート依頼に添付してください。

 - ユーザーが Intune ライセンスを持っていることを確認します。そうでない場合、Exchange Connector は、それらのユーザーのデバイスを検出しません。
 - ユーザーのプライマリ SMTP アドレスが Azure Active Directory (Azure AD) の UPN と異なる場合、Exchange Connector は、そのユーザーのデバイスを検出しません。 この問題を解決するのには、プライマリ SMTP アドレスを修正します。
 - 環境内に Exchange 2010 メールボックス サーバーと Exchange 2013 メールボックス サーバーが両方ともある場合は、Exchange Connector を Exchange 2013 CAS にポイントすることをお勧めします。 それ以外の場合、Exchange Connector は、Exchange 2010 CAS と通信するように設定されていると、Exchange 2013 ユーザーのデバイスを検出しません。 
- Exchange Online Dedicated 環境の場合、初期セットアップ中に Exchange Connector を専用環境内の (Exchange 2010 CAS ではなく) Exchange 2013 CAS にポイントする必要があります。これは、Connector が、PowerShell コマンドレットを実行するときに、この CAS のみと通信するからです。


## <a name="using-powershell-to-get-more-data-on-exchange-connector-issues"></a>Powershell を使用して Exchange Connector の問題に関するより多くのデータを取得する
- メールボックスのすべてのモバイル デバイスの一覧を取得するには、Get-ActiveSyncDeviceStatistics -mailbox mbx を使用します。
- メールボックスの SMTP アドレスの一覧を取得するには、Get-Mailbox -Identity user | select emailaddresses | fl を使用します。
- デバイスのアクセス状態に関する詳細情報を取得するには、Get-CASMailbox <upn> | fl を使用します。

### <a name="next-steps"></a>次の手順
この情報を使っても問題が解決しない場合は、[Microsoft Intune のサポートを受ける](get-support.md)こともできます。
