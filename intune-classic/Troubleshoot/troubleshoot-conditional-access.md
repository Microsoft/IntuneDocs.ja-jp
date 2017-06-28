---
title: "条件付きアクセスに関するトラブルシューティング"
description: "ユーザーが Intune の条件付きアクセスでリソースにアクセスできない場合の対処方法。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 10/24/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 433fc32c-ca9c-4bad-9616-852c72faf996
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: 04b1785c0b75d4668879488e5221d8b8c2794834
ms.contentlocale: ja-jp
ms.lasthandoff: 06/08/2017


---

# <a name="troubleshoot-conditional-access"></a>条件付きアクセスに関するトラブルシューティング

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

通常、ユーザーは電子メールまたは SharePoint にアクセスしようとし、登録を要求されます。 そのプロンプトからユーザーはポータル サイトに移動します。

このトピックでは、ユーザーが Intune の条件付きアクセスでリソースにアクセスできない場合の対処方法について説明します。


## <a name="the-basics-for-success-in-conditional-access"></a>条件付きアクセスが機能するための基礎

条件付きアクセスを機能させるには、次の要件を満たす必要があります。

-   デバイスを Intune で管理する必要がある
-   デバイスを Azure Active Directory (AAD) に登録する必要がある。 通常の状況下では、この登録は Intune の登録時に自動的に行われます
-   デバイスはデバイスおよびそのデバイスのユーザーの Intune コンプライアンス ポリシーに準拠している必要がある。  コンプライアンス ポリシーが存在しない場合は、Intune の登録で十分です。
-   ユーザーが Outlook ではなくデバイスのネイティブ メール クライアントを利用してメールを取得する場合、Exchange ActiveSync をデバイスで有効にする必要がある。     これは、iOS、Windows Phone、および Android/KNOX 標準デバイスで自動的に発生します。
-   Intune Exchange Connector を適切に構成する必要がある。 詳細については、[Microsoft Intune での Exchange Connector のトラブルシューティング](troubleshoot-exchange-connector.md)に関するページを参照してください。

各デバイスのこれらの状態は、Azure 管理ポータルまたはデバイスのインベントリ レポートで確認できます。

## <a name="enrollment-issues"></a>登録に関する問題

 -  デバイスが登録されていません。登録することで問題が解消されます。
 -  ユーザーがデバイスを登録しましたが、社内参加できませんでした。 ユーザーはポータル サイトから登録を更新する必要があります。

## <a name="compliance-issues"></a>ポリシー準拠の問題

 -  デバイスが Intune ポリシーに準拠していません。 一般的な問題は暗号化とパスワードの要件です。 ユーザーはポータル サイトにリダイレクトされます。ポータル サイトでデバイスがポリシーに準拠するように設定できます。
 -  デバイスのコンプライアンス情報が登録されるまで時間がかかることがあります。 しばらく待ってからもう一度お試しください。
 -  iOS デバイスの場合:
     -   ユーザーによって作成された既存の電子メール プロファイルは、Intune の管理者が作成したプロファイルの展開をブロックします。 これは一般的な問題です。iOS ユーザーは通常、電子メール プロファイルを作成し、それから登録するためです。 ポータル サイトは、手動で設定した電子メール プロファイルに起因してポリシーに準拠していないことをユーザーに通知し、そのプロファイルを取り除くようにユーザーに要求します。Intune プロファイルを展開できるように、ユーザーは電子メール プロファイルを取り除く必要があります。 この問題を防ぐには、電子メール プロファイルを設定せずに登録し、Intune によるプロファイルの展開を許可するようにユーザーに指示します。
     -   iOS デバイスがポリシー準拠状況の確認中の状態でスタックし、ユーザーが別のチェックインを開始できません。 ポータル サイトの再起動で解決することがあり、ポリシー準拠の状態が Intune のデバイスの状態を反映します。 デバイスの同期からすべてのデータが収集された後、ポリシー準拠の確認は平均して 0.5 秒で完了します。

        通常、デバイスがこの状態にあるのは、サービスの接続に問題があるか、同期に時間がかかっていることが原因です。  別のネットワーク構成 (携帯電話、Wi-Fi、VPN) を使用、デバイスを再起動、およびデバイスの SSP が最新であることを確認しても問題が解決しない場合は、「[Microsoft Intune のサポート受ける方法](how-to-get-support-for-microsoft-intune.md)」に従って Microsoft サポートにお問い合わせください。

 - Android デバイスの場合:
    - 一部の Android デバイスは暗号化されているように見えることがありますが、ポータル サイト アプリでは、このようなデバイスを暗号化されていないデバイスと認識します。 
    
        -   この状態のデバイスでは、ユーザーが安全なスタートアップ パスコードを設定する必要があります。 ユーザーには、ポータル サイト アプリから、デバイスのスタートアップ パスコードを設定するように求めるデバイス通知が表示されます。 デバイス通知をタップし、既存の PIN またはパスワードを確認した後に、**[Secure start-up]** (安全な起動) 画面で **[Require PIN to start device]** (デバイスの起動に PIN が必要) を選択します。 ポータル サイト アプリからデバイスの **[ポリシー準拠状況の確認]** ボタンをタップします。 デバイスは暗号化済みとして検出されるようになります。
    
        -   デバイスの製造元によっては、ユーザーが設定したシークレット PIN ではなく既定の PIN を使用してデバイスを暗号化する場合があります。 Intune は、既定の PIN を使用した暗号化を安全ではないと認識します。この方法の暗号化では、悪意のあるユーザーがデバイスに物理的にアクセスできる場合、デバイス上のデータが危険な状態になるためです。 この問題が生じた場合は、[アプリの保護ポリシー](/intune-classic/deploy-use/azure-portal-for-microsoft-intune-mam-policies)を使用することを検討してください。

## <a name="policy-issues"></a>ポリシーの問題

コンプライアンス ポリシーを作成し、それを電子メール ポリシーにリンクするとき、両方のポリシーを同じユーザーに展開する必要があります。そのため、どのポリシーをどのグループに展開するか計画するときは注意が必要です。 ユーザーにポリシーが 1 つだけ適用されている場合、そのユーザーのデバイスはおそらくポリシー非準拠となります。


## <a name="exchange-activesync-issues"></a>Exchange ActiveSync の問題

### <a name="compliant-android-device-gets-quarantine-notice"></a>対応する Android デバイスが検疫通知を受け取る
- 登録され、ポリシーに準拠している Android デバイスでも、企業のリソースにアクセスしようとしたとき、検疫通知を受け取ることができます。 **[開始]** と記載されたリンクを選択する前に、リソースにアクセスしようとしたとき、ポータル サイトが開いていなかったことをユーザーは確認する必要があります。 ユーザーはポータル サイトを閉じ、リソースへのアクセスをもう一度試し、それから **[開始]** リンクを選択します。

### <a name="retired-device-continues-to-have-access"></a>使用中止となったデバイスで引き続きアクセスできる
- Exchange Online を使用すると、使用中止となったデバイスでも使用中止後の数時間はアクセスできることがあります。 これは Exchange がアクセス権を 6 時間キャッシュするためです。 このシナリオでは、使用中止となったデバイスのデータの保護には別の手段を検討してください。

### <a name="device-is-compliant-and-registered-with-aad-but-still-blocked"></a>デバイスが AAD に準拠し登録されているがまだブロックされている
- Exchange ActiveSync ID (EASID) から AAD へのプロビジョニングが遅延することがあります。 この問題の一般的な原因は調整です。しばらく待ってからもう一度お試しください。

### <a name="device-blocked"></a>デバイスがブロックされている

デバイスは、ライセンス認証の電子メールを受信することなく条件付きアクセスからブロックされることがあります。

- デバイスを検疫またはブロックする既定の Exchange ルールはありますか。 既定のルールがデバイスをブロックまたは検疫する場合、デバイスは Exchange Connector からライセンス認証の電子メールを受信できません。 これは仕様です。
- 通知アカウントは基本構成で説明されているとおりに適切に構成されていますか。
- デバイスは Intune 管理コンソールに Exchange ActiveSync デバイスとして存在しますか。 存在しない場合、Exchange Connector の同期の問題でデバイスの検出が失敗している可能性があります。 「Exchange ActiveSync device not discovered from Exchange」 (Exchange ActiveSync デバイスが Exchange から検出されない問題) を参照してください。
- Exchange Connector のログで sendemail アクティビティにエラーがないかを確認します。 検索するコマンドの例は、「SendEmail from notification account to useremail」です。
- Exchange Connector はデバイスをブロックする前に、ライセンス認証の電子メールを送信します。 デバイスがオフラインである場合、ライセンス認証の電子メールを受信できない可能性があります。 デバイスの電子メール クライアントがポーリングでなくプッシュを使用して電子メールを取得しているかどうかを確認します。ユーザーが電子メールを受信しない可能性があるためです。 ポーリングに切り替え、デバイスが電子メールを受信することを確認してください。

## <a name="non-compliant-device-not-blocked"></a>非対応のデバイスがブロックされていない

非対応のデバイスで引き続きアクセス可能なデバイスが見つかった場合は、次の手順を実行します。

- ターゲット グループと除外グループを確認します。 ユーザーが正しいターゲット グループにいない、または除外グループにいる場合、ユーザーはブロックされません。 ターゲット グループ内のユーザーのデバイスのみが対応しているかどうかチェックされます。
- デバイスが検出されていることを確認します。 ユーザーが Exchange 2013 Server を使用しているにもかかわらず、Exchange Connector が Exchange 2010 CAS を指していませんか。 このケースでは、ユーザーがターゲット グループに存在する場合でも、既定の Exchange 規則が [許可] であれば、Intune は Exchange へのデバイスの接続を認識しません。
- Exchange で次のようにデバイスの存在とアクセスの状態を確認します。
    - PowerShell コマンドレット "Get-ActiveSyncDeviceStatistics -mailbox mbx" を使用してメールボックスのすべてのモバイル デバイスの一覧を取得します。 デバイスが一覧に表示されない場合、デバイスは Exchange にアクセスしていません。
    - デバイスが一覧に表示されている場合は、Get-CASmailbox -identity:’upn’ | fl コマンドレットを使用してアクセスの状態に関する詳細情報を取得し、その情報を Microsoft サポートに提供します。

## <a name="before-you-open-a-support-ticket"></a>サポート チケットを開く前に
これらのトラブルシューティング手順で問題が解決しない場合、OWA メールボックスのログや Exchange Connector のログなどの情報の提供を Microsoft サポートに求められることがあります。

### <a name="collecting-owa-mailbox-logs"></a>OWA メールボックス ログオンの回収

1. OWA 経由でログオンし、右上隅の自分の名前の隣にある設定 (歯車) のアイコンを選択します。
2. **[オプション]** を選択します。
3. 左側の列の **[電話]** (**[モバイル デバイス]** と表記されている場合もあります) を選択します。
4. 上部のメニューから **[モバイル デバイス]** を選択します。
5. 一覧からデバイスを選択し、**[ログの開始]** を選択します。
6. プロンプトされたら、ポップアップ ダイアログで **[はい]** を選択します。
7. 問題を引き起こした操作を実行し、再現します。
8. 1、2 分待ち、OWA の電話番号の一覧に戻ります。 一覧で電話が選択し、上部のメニューから **[ログの取得]** を選択します。
9. これで自身から添付ファイル付きの電子メールが届きます。 サポート チケットを開くとき、Microsoft サポートに電子メールの内容を提供します。

### <a name="exchange-connector-logs"></a>Exchange Connector のログ

#### <a name="general-log-information"></a>一般的なログ情報
Exchange Connector のログを表示するには、[サーバー トレース ビューアー ツール] (サーバー トレース ビューアー ツール (https://msdn.microsoft.com/ja-jp/library/ms732023(v=vs.110).aspx) を使用します。 このツールを使用するには、Windows Server SDK をダウンロードする必要があります。

>[!NOTE]
>ログは C:\ProgramData\Microsoft\Windows Intune Exchange Connector\Logs に置かれます。 ログは *Connector0.log* から *Connector29.log* までの 30 個の一連のログ ファイルで格納されます。 10MB のデータが蓄積されると次のログにロールオーバーします。 ログが Connector29 に達すると、Connector0 から再開され、以前のログが上書きされます。

#### <a name="locating-sync-logs"></a>同期ログを特定する

-    ログ内で **full sync** を検索して完全同期を探します。 完全同期の開始は、次のテキストでマークされます。

    'Handling command: Getting the mobile device list without a time filter (full sync) for <number> users`

    完全同期のログの末尾は、次のようになります。

    Getting the mobile device list without a time filter (full sync) for 4 users completed successfully. Details: Inventory command result - Devices synced: 0 Commmand ID: commandIDGUID' Exchange health: 'Server health 'Name: 'PowerShellExchangeServer: <Name=mymailservername>' Status: Connected','

-   ログ内で **quick sync** を検索してクイック (デルタ) 同期を探します。

##### <a name="exceptions-in-get-next-command"></a>Get next コマンドの例外
Exchange Connector ログで **Get next コマンド**の例外を確認し、それらを Microsoft サポートに提供します。

#### <a name="verbose-logging"></a>詳細ログ記録

詳細ログ記録を有効にするには:

1.  Exchange Connector のトレース構成ファイルを開きます。 ファイルは、%ProgramData%\Microsoft\Windows Intune Exchange Connector\TracingConfiguration.xml に置かれます。
2.  キー OnPremisesExchangeConnectorService を使用して、TraceSourceLine を探します。
3.  **SourceLevel** ノードの値を、以下のように **Warning ActivityTracing** (既定値) から **Verbose ActivityTracing** に変更します。

    <TraceSourceLine>
          <Key xsi:type="xsd:string">OnPremisesExchangeConnectorService</Key>
          <Value xsi:type="TraceSource">
            <SourceLevel>All</SourceLevel>
            <Listeners>
              <Listener>
                <ListenerType>CircularTraceListener</ListenerType>
                <SourceLevel>Verbose ActivityTracing</SourceLevel>
                <FileSizeQuotaInBytes>10000000</FileSizeQuotaInBytes>
                <FileName>Microsoft\Windows Intune Exchange Connector\Logs\Connector.svclog</FileName>
                <FileQuota>30</FileQuota>
              </Listener>
            </Listeners>
          </Value>
    </TraceSourceLine>



### <a name="next-steps"></a>次のステップ
このトラブルシューティング情報を使っても問題が解決しない場合は、「[Microsoft Intune のサポートを受ける方法](how-to-get-support-for-microsoft-intune.md)」の説明に従って Microsoft サポートにお問い合わせください。

