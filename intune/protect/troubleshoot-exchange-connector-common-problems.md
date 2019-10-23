---
title: Intune Exchange connector に関する一般的な問題のトラブルシューティング
titleSuffix: Microsoft Intune
description: 内部設置型の Microsoft Intune Exchange connector に関する一般的な問題をトラブルシューティングして解決します。
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/02/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e9542212e1b75d97c96c024eed20e20e610e2b5d
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72503655"
---
# <a name="resolve-common-problems-with-the-intune-exchange-connector"></a>Intune Exchange connector に関する一般的な問題を解決する
 
この記事は、intune 管理者が Intune Exchange connector の操作に関する一般的な問題を解決するのに役立ちます。  

トラブルシューティングを開始する前に、コネクタに関する基本的な情報について、「 [Intune On-premises Exchange connector のトラブルシューティング](troubleshoot-exchange-connector.md)」を参照してください。 コネクタ構成の一般的な問題についても確認してください。 

## <a name="an-exchange-activesync-device-isnt-discovered-from-exchange"></a>Exchange ActiveSync デバイスが Exchange から検出されない

Exchange ActiveSync デバイスが exchange から検出されない場合は、exchange connector の[アクティビティを監視](exchange-connector-install.md#on-premises-intune-exchange-connector-high-availability-support)して、exchange Connector が exchange server と同期しているかどうかを確認します。 デバイスが参加してから同期が行われなかった場合は、同期ログを収集し、サポート要求に添付します。 デバイスが参加してから完全同期またはクイック同期が正常に完了した場合は、次の問題を確認してください。 

- ユーザーが Intune のライセンスを持っていることを確認します。 そうでない場合、Exchange connector はデバイスを検出しません。  

- ユーザーのプライマリ SMTP アドレスが Azure Active Directory (Azure AD) のユーザー プリンシパル名 (UPN) と異なる場合、Exchange Connector は、そのユーザーのデバイスを検出しません。 この問題を解決するのには、プライマリ SMTP アドレスを修正します。  

- 環境内に Exchange 2010 メールボックス サーバーと Exchange 2013 メールボックス サーバーが両方ともある場合は、Exchange Connector を Exchange 2013 クライアント アクセス サーバー (CAS) にポイントすることをお勧めします。 Exchange Connector が Exchange 2010 CAS と通信するように設定されていると、Exchange Connector は Exchange 2013 のユーザー デバイスを検出しません。  

- Exchange Online 専用環境では、初期セットアップ時に、Exchange connector が専用環境の exchange 2013 CAS (Exchange 2010 CA ではない) を指すようにする必要があります。 コネクタは、PowerShell コマンドレットを実行するときに、Exchange 2013 の CA とのみ通信します。  


## <a name="problems-with-the-notification-email-message"></a>通知電子メールメッセージに関する問題  

Android Knox を実行していないデバイス上のオンプレミスのメールボックスに対する条件付きアクセスをサポートするには、intune Exchange connector によって送信される "今すぐ開始" 電子メールメッセージから Intune の登録が開始されていることを確認します。 メッセージから登録を開始すると、デバイスはすべてのプラットフォーム (Exchange、Azure AD、Intune) で一意の Activescid を確実に受信できるようになります。  

次の理由により、ユーザーが通知電子メールメッセージを受信できない可能性があります。  

- 通知アカウントが正しく設定されていません。
- 通知アカウントの自動検出に失敗しました。
- 電子メールメッセージを送信するための Exchange Web サービス (EWS) 要求が失敗しました。

電子メール通知の問題のトラブルシューティングを行うには、次のセクションを参照してください。

### <a name="check-the-notification-account-that-retrieves-autodiscover-settings"></a>自動検出の設定を取得する通知アカウントを確認する
1. 自動検出サービスと EWS が Exchange クライアント アクセス サービスで構成されていることを確認します。 詳細については、「Exchange Server の[クライアントアクセスサービス](https://docs.microsoft.com/Exchange/architecture/client-access/client-access)と[自動検出サービス](https://docs.microsoft.com/Exchange/architecture/client-access/autodiscover?view=exchserver-2019)」を参照してください。


2. 通知アカウントが次の要件を満たしていることを確認します。

   - このアカウントには、Exchange on-premises サーバーによってホストされているアクティブなメールボックスがあります。  

   - アカウント UPN は SMTP アドレスと一致します。

3. 自動検出を行うには、Exchange クライアントアクセスサーバーを指す**Autodiscover.SMTPdomain.com** (Autodiscover.contoso.com など) の dns レコードを持つ dns サーバーが必要です。 レコードを確認するには、 *Autodiscover.SMTPdomain.com*の代わりに FQDN を指定し、次の手順を実行します。

   1. コマンドプロンプトで、「 *NSLOOKUP*」と入力します。  

   2. 「 *Autodiscover.SMTPdomain.com*」と入力します。 出力は次の図のようになります。  
      ![Nslookup 結果](./media/troubleshoot-exchange-connector-common-problems/nslookup-results.png
)

   また、 https://testconnectivity.microsoft.com でインターネットから自動検出サービスをテストすることもできます。 または、Microsoft Connectivity Analyzer ツールを使用してローカルドメインからテストします。 詳細については、「 [Microsoft Connectivity Analyzer ツール](https://docs.microsoft.com/en-us/previous-versions/office/exchange-remote-connectivity/jj851141(v=exchg.80))」を参照してください。 必要に応じ[て、Microsoft Connectivity Analyzer ツールをダウンロード](https://go.microsoft.com/fwlink/?LinkID=313782)します。


### <a name="check-autodiscovery"></a>自動検出の確認  

自動検出が失敗した場合は、次の手順を試してください。
1. [有効な自動検出 DNS レコードを構成](https://docs.microsoft.com/previous-versions/exchange-server/exchange-150/mt473798(v=exchg.150))してください。 

2. Intune Exchange connector 構成ファイルで、EWS URL をハードコーディングします。

   1. EWS URL を確認します。 Exchange の既定の EWS URL は `https://<mailServerFQDN>/ews/exchange.asmx` ですが、URL が異なる場合があります。 Exchange 管理者に問い合わせて、使用している環境の正しい URL を確認してください。

   2. *OnPremisesExchangeConnectorServiceConfiguration.xml*ファイルを編集します。 既定では、ファイルは Exchange connector を実行するコンピューターの *%ProgramData%\Microsoft\Windows Intune Exchange Connector*にあります。 ファイルをテキストエディターで開き、環境の EWS URL を反映するように次の行を変更します。 `<ExchangeWebServiceURL> https://<YourExchangeHOST>/EWS/Exchange.asmx</ExchangeWebServiceURL>`
    

3. ファイルを保存し、コンピューターを再起動するか、Microsoft Intune Exchange コネクタ サービスを再起動します。

>[!NOTE]
> この構成では、Intune Exchange connector は自動検出の使用を停止し、代わりに EWS の URL に直接接続します。

## <a name="next-steps"></a>次の手順  

特定のエラーに関するヘルプを表示するには、 [Intune Exchange connector の一般的なエラーを解決](troubleshoot-exchange-connector-common-errors.md)してください。

サポートを受けるには、または Intune コミュニティから支援を受けるには:
- Intune コンソールを使用して問題のトラブルシューティングを行う、または Microsoft のサポートケースを開く方法については、「[サポートを受ける](../fundamentals/get-support.md)」を参照してください。 
- [Microsoft Intune フォーラム](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod)に問題を投稿してください。  
