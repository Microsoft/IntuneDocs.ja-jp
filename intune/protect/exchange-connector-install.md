---
title: Microsoft Intune Exchange Connector を設定する
titleSuffix: Microsoft Intune
description: Intune の登録と Exchange Active Sync (EAS) に基づいて、Exchange メールボックスへのデバイス アクセスを管理するには、オンプレミスの Intune Exchange Connector を使用します。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/28/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a0376ea1-eb13-4f13-84da-7fd92d8cd63c
ms.reviewer: demerson
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f4751b77362567ad18f5b775e5bda9c1081dd181
ms.sourcegitcommit: 78f9750712c254d8b123ef15b74f30ca999aa128
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2019
ms.locfileid: "71911196"
---
# <a name="set-up-the-on-premises-intune-exchange-connector"></a>オンプレミスの Intune Exchange Connector を設定する
Exchange へのアクセスを保護するために、Intune は Microsoft Intune Exchange Connector というオンプレミスのコンポーネントに依存しています。 このコネクタは、Intune コンソールの一部の場所では *[Exchange ActiveSync のオンプレミス コネクタ]* とも表示されます。 

この記事の情報は、Intune Exchange Connector のインストールと監視に役立ちます。 コネクタと[条件付きアクセス ポリシー](conditional-access-exchange-create.md)を使用して、Exchange On-Premises メールボックスへのアクセスを許可またはブロックすることができます。 

オンプレミスのハードウェアにコネクタがインストールされ、実行されます。 Exchange に接続し、デバイス情報を Intune サービスに伝達するデバイスが検出されます。 コネクタでは、デバイスが登録され、準拠しているかどうかに基づいて、デバイスが許可またはブロックされます。 これらの通信には HTTPS プロトコルが使用されます。

デバイスからオンプレミスの Exchange サーバーにアクセスしようとすると、Exchange Connector によって Exchange Server の Exchange ActiveSync (EAS) レコードが Intune レコードにマップされ、確実にデバイスが Intune に登録され、デバイスのポリシーに準拠した状態になります。 条件付きアクセス ポリシーに応じて、デバイスは許可またはブロックされます。 詳細については、「[Intune での条件付きアクセスの一般的な使用方法](conditional-access-intune-common-ways-use.md)」を参照してください。

標準の Exchange PowerShell コマンドレットを使用して、"*検出*" 操作と "*許可およびブロック*" 操作の両方が実行されます。 これらの操作には、Exchange Connector が最初にインストールされたときに指定されたサービス アカウントが使用されます。 

Intune では、サブスクリプションごとに複数の Intune Exchange Connector のインストールがサポートされています。 オンプレミス Exchange 組織が複数ある場合、それぞれにコネクタを個別に設定できます。 ただし、Exchange 組織ごとにインストールできるコネクタは 1 つのみです。  

以下の一般的な手順に従って、Intune とオンプレミス Exchange サーバーが通信できるように接続を設定します。

1. Intune ポータルからオンプレミス コネクタをダウンロードします。
2. オンプレミス Exchange 組織のコンピューターに Exchange コネクタをインストールし、構成します。
3. Exchange 接続を確認します。
4. Intune と接続させる追加の Exchange 組織ごとに以上の手順を繰り返します。

## <a name="intune-exchange-connector-requirements"></a>Intune Exchange Connector の要件

Exchange に接続するには、コネクタが使用できる Intune ライセンスを持つアカウントが必要です。 コネクタをインストールするときに、アカウントを指定します。  

以下の表に、Intune Exchange Connector をインストールするコンピューターの要件を示します。  

|  要件  |   詳細情報     |
|---------------|------------------------|
|  Operating systems        | Intune は、Windows Server 2008 SP2 64 ビット、Windows Server 2008 R2、Windows Server 2012、Windows Server 2012 R2、または Windows Server 2016 の任意のエディションを実行しているコンピューター上の Intune Exchange Connector をサポートします。<br /><br />Server Core インストールでは、コネクタはサポートされません。  |
| Microsoft Exchange          | オンプレミス コネクタには、Microsoft Exchange 2010 SP3 以降または従来の Exchange Online Dedicated が必要です。 Exchange Online Dedicated 環境が*新しい*構成か*従来の*構成かを確認するには、アカウント マネージャーに問い合わせてください。 |
| モバイル デバイス管理機関           | [モバイル デバイス管理機関を Intune に設定します](../fundamentals/mdm-authority-set.md)。 |
| ハードウェア              | コネクタをインストールするコンピューターには、1.6 GHz の CPU と 2 GB の RAM と 10 GB の空きディスク容量が必要です。 |
|  Active Directory の同期             | コネクタを使用して Intune を Exchange サーバーに接続する前に、[Active Directory の同期を設定](../fundamentals/users-add.md)します。 ローカル ユーザーとセキュリティ グループは、Azure Active Directory のインスタンスと同期する必要があります。 |
| その他のソフトウェア         | コネクタをホストするコンピューターには、Microsoft .NET Framework 4.5 および Windows PowerShell 2.0 の完全なインストールが必要です。 |
| ネットワーク               | コネクタをインストールするコンピューターは、Exchange サーバーをホストするドメインと信頼関係があるドメインに参加している必要があります。<br /><br />ポート 80 および 443 を介してファイアウォールとプロキシ サーバー経由で Intune サービスにアクセスできるようにコンピューターを構成します。 Intune では、次のドメインを使用します。 <br> - manage.microsoft.com <br> - \*manage.microsoft.com<br> - \*.manage.microsoft.com <br><br> Intune Exchange Connector は、次のサービスと通信します。 <br> - Intune サービス:HTTPS ポート 443 <br> - Exchange クライアント アクセス サーバー (CAS):WinRM サービス ポート 443<br> - Exchange Autodiscover 443<br> - Exchange Web サービス (EWS) 443  |

### <a name="exchange-cmdlet-requirements"></a>Exchange コマンドレットの要件

Intune Exchange Connector 用に Active Directory ユーザー アカウントを作成します。 アカウントには、次の Windows PowerShell Exchange コマンドレットを実行できるアクセス許可が必要です。  

- `Get-ActiveSyncOrganizationSettings`、`Set-ActiveSyncOrganizationSettings`
- `Get-CasMailbox`、`Set-CasMailbox`
- `Get-ActiveSyncMailboxPolicy`、`Set-ActiveSyncMailboxPolicy`、`New-ActiveSyncMailboxPolicy`、`Remove-ActiveSyncMailboxPolicy`
- `Get-ActiveSyncDeviceAccessRule`、`Set-ActiveSyncDeviceAccessRule`、`New-ActiveSyncDeviceAccessRule`、`Remove-ActiveSyncDeviceAccessRule`
- `Get-ActiveSyncDeviceStatistics`
- `Get-ActiveSyncDevice`
- `Get-ExchangeServer`
- `Get-ActiveSyncDeviceClass`
- `Get-Recipient`
- `Clear-ActiveSyncDevice`、`Remove-ActiveSyncDevice`
- `Set-ADServerSettings`
- `Get-Command`

## <a name="download-the-installation-package"></a>インストール パッケージをダウンロードする

1. Intune Exchange Connector をサポートできる Windows サーバーで、[Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインします。 オンプレミスの Exchange サーバーの管理者であり、Exchange Server を使用するライセンスを持つアカウントを使用します。

2. **[Intune]**  >  **[Exchange へのアクセス]** に移動します。  

3. **[セットアップ]** で、 **[Exchange ActiveSync のオンプレミス コネクタ]** を選択してから **[追加]** を選択します。

4. **[コネクタの追加]** ページで、 **[オンプレミス コネクタをダウンロードします]** を選択します。 Intune Exchange Connector は、開いたり保存したりできる圧縮 (.zip) フォルダー内にあります。 **[ファイルのダウンロード]** ダイアログ ボックスで **[保存]** を選んで、圧縮フォルダーを安全な場所に保存します。


## <a name="install-and-configure-the-intune-exchange-connector"></a>Intune Exchange Connector をインストールして構成する

Intune Exchange Connector をインストールするには、次の手順を実行します。 Exchange 組織が複数ある場合、設定する Exchange Connector ごとにこの手順を繰り返します。

1. Intune Exchange Connector のサポートされているオペレーティング システムで、**Exchange_Connector_Setup.zip** のファイルを安全な場所に抽出します。
   > [!IMPORTANT]
   > *Exchange_Connector_Setup* フォルダー内のファイルの名前を変更したり、移動したりしないでください。 これらの変更によって、コネクタのインストールが失敗する可能性があります。

2. ファイルが抽出されたら、抽出されたフォルダーを開き、**Exchange_Connector_Setup.exe** をダブルクリックしてコネクタをインストールします。

   > [!IMPORTANT]
   > 対象のフォルダーが安全な場所にない場合は、オンプレミス コネクタのインストールが完了したら、証明書ファイル *MicrosoftIntune.accountcert* を削除します。

3. **[Microsoft Intune Exchange Connector]** ダイアログ ボックスで、 **[内部設置型 Microsoft Exchange Server]** または **[ホストされた Microsoft Exchange Server]** を選択します。

   ![Exchange Server の種類を選択する場所を示す画像](./media/exchange-connector-install/intune-sa-exchange-connector-config.png)

   社内の Exchange Server の場合、**クライアント アクセス サーバー** ロールをホストする Exchange サーバーのサーバー名または完全修飾ドメイン名を指定します。

   ホスト型 Exchange Server の場合、Exchange Server のアドレスを指定します。 ホスト型 Exchange サーバーの URL を見つけるには:

   1. Outlook for Office 365 を開きます。

   2. 左上の **?** アイコンを選択し、 **[バージョン情報]** を選択します。

   3. **[POP 外部サーバー]** の値を探します。

   4. **[プロキシ サーバー]** を選んで、ホスト型 Exchange サーバーのプロキシ サーバー設定を指定します。

       1. **[モバイル デバイス情報を同期するときにプロキシ サーバーを使用する]** を選択します。

       1. サーバーへのアクセスに使用する **[プロキシ サーバー名]** と **[ポート番号]** を入力します。

       1. プロキシ サーバーへのアクセスにユーザーの資格情報が必要な場合は、 **[プロキシ サーバーへの接続に資格情報を使用する]** を選択します。 次に、**ドメイン\ユーザー**と**パスワード**を入力します。

       1. **[OK]** を選びます。

4. **[ユーザー (ドメイン\ユーザー)]** および **[パスワード]** フィールドに、Exchange サーバーへの接続に使用する資格情報を入力します。 指定したアカウントには Intune を使用するためのライセンスが含まれている必要があります。 

5. ユーザーの Exchange Server メールボックスに通知を送信するための資格情報を指定します。 このユーザーは通知専用でもかまいません。 通知ユーザーには、メールで通知を送信するための Exchange メールボックスが必要です。 これらの通知は、Intune で条件付きアクセス ポリシーを使用して構成できます。  

   Exchange CAS 上で自動検出サービスと Exchange Web サービスが構成されていることを確認します。 詳細については、「[クライアント アクセス サーバー](https://technet.microsoft.com/library/dd298114.aspx)」を参照してください。

6. **[パスワード]** フィールドに、このアカウントで Intune から Exchange サーバーにアクセスするために必要なパスワードを入力します。

   > [!NOTE]
   > テナントへのサインインに使用するアカウントは、少なくとも Intune サービス管理者である必要があります。 この管理者アカウントがないと、次のエラーで接続が失敗します。"リモート サーバーが次のエラーを返しました:(400) 正しくない要求"。

7. **[接続]** を選びます。

   > [!NOTE]
   > 接続の構成には数分かかる場合があります。

構成中、Exchange Connector はインターネットへのアクセスを有効にする目的でプロキシ設定が保存します。 プロキシ設定が変更された場合、更新後のプロキシ設定が Exchange Connector に適用されるよう、Exchange Connector をもう一度構成します。

Exchange Connector が接続を設定すると、Exchange で管理されているユーザーに関連付けられたモバイル デバイスが自動的に同期され、Exchange Connector に追加されます。 この同期が完了するまで時間がかかる場合があります。

> [!NOTE]
> Intune Exchange Connector をインストールし、後で Exchange 接続を削除する必要がある場合は、コネクタをインストールしたコンピューターからアンインストールする必要があります。



## <a name="install-connectors-for-multiple-exchange-organizations"></a>複数の Exchange 組織にコネクタをインストールする

Intune は、サブスクリプションごとに複数の Intune Exchange Connector をサポートします。 Exchange 組織が複数あるテナントには、組織ごとにコネクタを 1 つのみ設定できます。 

複数の Exchange 組織に接続するコネクタをインストールするには、.zip フォルダーを 1 回ダウンロードします。 インストールするコネクタごとに同じダウンロードを再利用します。 追加するコネクタごとに、前セクションの手順に従って、Exchange 組織内のサーバー上で設定プログラムを抽出し、実行してください。

Intune に接続する各 Exchange 組織は、高可用性、監視、および手動の同期をサポートしています。以降のセクションでは、これらの機能について説明します。

## <a name="on-premises-intune-exchange-connector-high-availability-support"></a>オンプレミスの Intune Exchange Connector の高可用性のサポート  

オンプレミス コネクタの場合、高可用性とは、コネクタが使用する Exchange CAS が使用不可になった場合に、その Exchange 組織の別の CA に切り替えることができることを意味します。 Exchange Connector 自体では、高可用性はサポートされていません。 コネクタが失敗した場合、自動フェールオーバーは行われません。 失敗したコネクタを置き換えるには、[新しいコネクタをインストール](#reinstall-the-intune-exchange-connector)する必要があります。 

フェールオーバーするために、コネクタでは、指定された CAS を使用して Exchange への正常な接続を作成します。 次に、その Exchange 組織の追加の CAS が検出されます。 この検出により、プライマリ CA が使用可能になるまで、コネクタを別の使用可能な CA にフェールオーバーできます。 

既定では、他の CAS の検出は有効になっています。 フェールオーバーを無効にする必要がある場合:  
1. Exchange Connector がインストールされているサーバー上で、 **%*ProgramData*%\Microsoft\Windows Intune Exchange Connector** にアクセスします。 
2. テキスト エディターを使用して、**OnPremisesExchangeConnectorServiceConfiguration.xml** を開きます。
3. **\<IsCasFailoverEnabled>*true*\</IsCasFailoverEnabled>** を **\<IsCasFailoverEnabled>*false*\</IsCasFailoverEnabled>** に変更します。  
 
## <a name="performance-tune-the-exchange-connector-optional"></a>Exchange Connector のパフォーマンス調整 (省略可能)

Exchange ActiveSync が 5,000 以上のデバイスをサポートする場合は、コネクタのパフォーマンスを向上させる省略可能な設定を構成できます。 Exchange で PowerShell コマンドの実行スペースの複数のインスタンスを使用できるようにすることで、パフォーマンスを向上させます。 

この変更を行う前に、Exchange コネクタの実行に使用するアカウントが、他の Exchange 管理の目的で使用されていないことを確認してください。 Exchange アカウントの実行スペースは数が限られており、そのほとんどがコネクタに使用されます。 

パフォーマンスの調整は、古いハードウェアまたは低速のハードウェアで実行されるコネクタには適していません。  

Exchange Connector のパフォーマンスを向上させるには: 

1. コネクタがインストールされているサーバーで、コネクタのインストール ディレクトリを開きます。  既定の場所は、*C:\ProgramData\Microsoft\Windows Intune Exchange Connector* です。 
2. *OnPremisesExchangeConnectorServiceConfiguration.xml* ファイルを編集します。
3. **EnableParallelCommandSupport** を探し、値を **true** に設定します。  
     
   \<EnableParallelCommandSupport>true\</EnableParallelCommandSupport>
4. ファイルを保存し、Microsoft Intune Exchange コネクタ サービスを再起動します。

## <a name="reinstall-the-intune-exchange-connector"></a>Intune Exchange Connector を再インストールする

Intune Exchange Connector の再インストールが必要な場合があります。 各 Exchange 組織に接続できるコネクタは 1 つのみなので、組織用に 2 つ目のコネクタをインストールすると、元のコネクタは、インストールした新しいコネクタに置き換えられます。

1. 新しいコネクタをインストールするには、[Exchange Connector のインストールと構成に関する](#install-and-configure-the-intune-exchange-connector)セクションの手順に従います。 
2. プロンプトが表示されたら、 **[置換]** を選択して新しいコネクタをインストールします。  
   ![コネクタを置き換える構成の警告](./media/exchange-connector-install/prompt-to-replace.png)

3. 「[Intune Exchange Connector をインストールして構成する](#install-and-configure-the-intune-exchange-connector)」セクションの手順を継続し、Intune にもう一度サインインします。
4. 最後のウィンドウで、 **[閉じる]** を選択してインストールを完了します。  
   ![セットアップを完了する](./media/exchange-connector-install/successful-reinstall.png)
 

## <a name="monitor-an-exchange-connector"></a>Exchange Connector を監視する

Exchange Connector の構成が正常に行えたら、接続の状態と前回成功した同期の試行を表示できます。 

Exchange コネクタの接続を確認するには:

1. Intune ダッシュ ボードで、 **[Exchange へのアクセス]** を選択します。
2. **[Exchange On-Premises のアクセス]** を選択して、Exchange コネクタごとに接続状態を確認します。

また、前回いつ同期が完了したかも確認することができます。

Intune 1710 リリース以降では、[Exchange Connector および Intune の System Center Operations Manager 管理パック](https://www.microsoft.com/download/details.aspx?id=55990&751be11f-ede8-5a0c-058c-2ee190a24fa6=True&e6b34bbe-475b-1abd-2c51-b5034bcdd6d2=True&fa43d42b-25b5-4a42-fe9b-1634f450f5ee=True)を使用できます。 管理パックには、問題をトラブルシューティングする必要があるときに Exchange Connector を監視するためのさまざまな方法が用意されています。

## <a name="manually-force-a-quick-sync-or-full-sync"></a>クイック同期または完全同期を手動で強制する

Intune Exchange コネクタは、EAS と Intune デバイス レコードを定期的に自動同期します。 デバイスのコンプライアンス状態が変わった場合、自動同期プロセスによって定期的にレコードが更新され、デバイス アクセスをブロックまたは許可できます。

- **クイック同期**は定期的に、1 日に数回実行されます。 クイック同期では、Intune のライセンスが与えられ、オンプレミス Exchange に条件付きでアクセスするユーザーのデバイスに関する情報が前回の同期以降に変更された部分だけ取得されます。

- **完全な同期**は、既定で毎日 1 回発生します。 完全同期では、条件付きアクセスの対象となっているすべての Intune ライセンス ユーザーとオンプレミス Exchange ユーザーのデバイス情報が取得されます。 完全同期の場合、Exchange サーバーの情報も取得され、Azure portal の Intune によって指定された構成が Exchange サーバーで更新されます。 


Intune ダッシュボードで **[クイック同期]** または **[完全同期]** オプションを使用し、同期を実行するようにコネクタに強制できます。

   1. Intune ダッシュ ボードで、 **[Exchange へのアクセス]** を選択します。
   2. **[Exchange On-Premises のアクセス]** を選択します。
   3. 同期するコネクタを選択し、 **[クイック同期]** または **[完全同期]** を選択します。

## <a name="next-steps"></a>次の手順

[オンプレミス Exchange サーバーの条件付きアクセス ポリシー](conditional-access-exchange-create.md)を作成します。
