---
title: Microsoft Intune のオンプレミス Exchange Connector をセットアップする
titleSuffix: Microsoft Intune
description: Intune の登録と Exchange Active Sync (EAS) に基づいて、Exchange メールボックスへのデバイス アクセスを管理するには、オンプレミスの Exchange Connector を使います。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/22/2019
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
ms.openlocfilehash: da828b162e008541cb5cb2b5d15092d0fce417c5
ms.sourcegitcommit: ede86a3cb094c12e3e218b956abb9935bec76902
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/05/2019
ms.locfileid: "67572532"
---
# <a name="set-up-the-intune-on-premises-exchange-connector-in-microsoft-intune"></a>Microsoft Intune で Intune のオンプレミス Exchange コネクタを設定する
この記事の情報は、Intune 用の Exchange Active Sync オンプレミス コネクタをインストールして監視するのに役立ちます。  Intune オンプレミス Exchange コネクタを[条件付きアクセス ポリシーと一緒に使用して、ご利用の Exchange オンプレミス メールボックスへのアクセスを許可またはブロックします](conditional-access-exchange-create.md)。 

デバイスによって、ご利用のオンプレミス Exchange へのアクセスが試みられると、Exchange コネクタでは Exchange Serve 内の Exchange Active Sync (EAS) レコードが Intune レコードに割り当てられて、デバイスが Intune に登録されているかどうか、およびご利用のデバイス コンプライアンス ポリシーに準拠しているかどうかが確認されます。 ご利用の条件付きアクセス ポリシーに応じて、デバイスからのアクセスは許可またはブロックされます。 詳細については、「[Intune での条件付きアクセスの一般的な使用方法](conditional-access-intune-common-ways-use.md)」を参照してください。

Intune では、サブスクリプションごとに複数のオンプレミス Exchange コネクタをインストールすることがサポートされています。 オンプレミス Exchange 組織が複数ある場合、それぞれにコネクタを個別に設定できます。 ただし、個々の Exchange 組織用にインストールできるコネクタは 1 つだけです。 

Intune とオンプレミス Exchange Server が通信できるようにするための接続を設定する一般的な手順を次に示します。

1. Intune ポータルから、Intune のオンプレミス Exchange コネクタをダウンロードします。
2. オンプレミス Exchange 組織のコンピューターに Exchange コネクタをインストールし、構成します。
3. Exchange 接続を確認します。
4. Intune と接続させる追加の Exchange 組織ごとに以上の手順を繰り返します。

## <a name="intune-on-premises-exchange-connector-requirements"></a>Intune オンプレミス Exchange コネクタの要件
コネクタが Exchange に接続するために使用できる Intune ライセンスを持つアカウントが必要です。 アカウントは、コネクタをインストールするときに指定します。  

以下の表に、オンプレミス Exchange コネクタをインストールするコンピューターの要件を示します。  

|  要件  |   詳細情報     |
|---------------|------------------------|
|  Operating systems        | Intune は、Windows Server 2008 SP2 64 ビット、Windows Server 2008 R2、Windows Server 2012、Windows Server 2012 R2、または Windows Server 2016 の任意のエディションを実行しているコンピューター上のオンプレミス Exchange コネクタをサポートします。<br /><br />Server Core インストールでは、コネクタはサポートされません。  |
| Microsoft Exchange          | オンプレミス コネクタには、Microsoft Exchange 2010 SP3 以降または従来の Exchange Online Dedicated が必要です。 Exchange Online Dedicated 環境が<strong>新しい</strong>構成か<strong>従来の</strong>構成かを確認するには、アカウント マネージャーに問い合わせてください。 |
| モバイル デバイス管理機関           | [モバイル デバイス管理機関を Intune に設定します](mdm-authority-set.md)。 |
| ハードウェア              | コネクタをインストールするコンピューターには、1.6 GHz の CPU と 2 GB の RAM と 10 GB の空きディスク容量が必要です。 |
|  Active Directory の同期             | コネクタを使用して Intune を Exchange Server に接続するには、[Active Directory の同期をセットアップ](users-add.md)して、ローカル ユーザーとセキュリティ グループが Azure Active Directory のインスタンスと同期されるようにする必要があります。 |
| その他のソフトウェア         | コネクタをホストするコンピューターに、Microsoft .NET Framework 4.5 および Windows PowerShell 2.0 の完全インストールがインストールされている必要があります。 |
| ネットワーク               | コネクタをインストールするコンピューターは、Exchange Server をホストするドメインと信頼関係があるドメインに参加している必要があります。<br /><br />コンピューターは、ポート 80 と 443 でファイアウォールとプロキシ サーバー経由で Intune サービスにアクセスできるように構成する必要があります。 Intune によって使用されるドメインには、manage.microsoft.com、&#42;manage.microsoft.com、および &#42;.manage.microsoft.com が含まれます。 |

### <a name="exchange-cmdlet-requirements"></a>Exchange コマンドレットの要件

オンプレミス Exchange コネクタが使用する Active Directory ユーザー アカウントを作成します。 アカウントには、次の必須の Windows PowerShell Exchange コマンドレットを実行するための権限が必要です。


 - Get-ActiveSyncOrganizationSettings, Set-ActiveSyncOrganizationSettings
 - Get-CasMailbox、Set-CasMailbox
 - Get-ActiveSyncMailboxPolicy、Set-ActiveSyncMailboxPolicy、New-ActiveSyncMailboxPolicy、Remove-ActiveSyncMailboxPolicy
 - Get-ActiveSyncDeviceAccessRule、Set-ActiveSyncDeviceAccessRule、New-ActiveSyncDeviceAccessRule、Remove-ActiveSyncDeviceAccessRule
 - Get-ActiveSyncDeviceStatistics
 - Get-ActiveSyncDevice
 - Get-ExchangeServer
 - Get-ActiveSyncDeviceClass
 - Get-Recipient
 - Clear-ActiveSyncDevice、Remove-ActiveSyncDevice
 - Set-ADServerSettings
 - Get-Command

## <a name="download-the-on-premises-exchange-connector-software-installation-package"></a>オンプレミス Exchange コネクタ ソフトウェア インストール パッケージのダウンロード

1. オンプレミス Exchange コネクタのサポートされている Windows Server オペレーティング システムで、Exchange Server を使用するライセンスを持つオンプレミス Exchange Server 内の管理者であるユーザー アカウントを使用して、[Azure Portal](https://portal.azure.com) を開きサインインします。

2. **[Intune]**  >  **[Exchange へのアクセス]** の順に移動します。  

3. **[セットアップ]** で、 **[Exchange ActiveSync のオンプレミス コネクタ]** を選択してから **[追加]** を選択します。

4. **[コネクタの追加]** ページで、 **[オンプレミス コネクタをダウンロードします]** を選択します。 オンプレミス Exchange コネクタは、開いたり保存したりできる圧縮 (.zip) フォルダー内にあります。 **[ファイルのダウンロード]** ダイアログ ボックスで **[保存]** を選んで、圧縮フォルダーを安全な場所に保存します。

    > [!IMPORTANT]
    > オンプレミス Exchange コネクタ フォルダー内のファイルの名前を変更したり、ファイルを移動したりしないでください。 フォルダーの内容を移動したり、名前を変更したりすると、Exchange コネクタのインストールが失敗します。

## <a name="install-and-configure-the-intune-on-premises-exchange-connector"></a>Intune のオンプレミス Exchange コネクタのインストールと構成
次の手順を実行して、Intune のオンプレミス Exchange コネクタをインストールします。 Exchange 組織が複数ある場合、設定する追加 Exchange コネクタごとに以上の手順を繰り返します。

1. オンプレミス Exchange コネクタのサポートされているオペレーティング システムで、**Exchange_Connector_Setup.zip** のファイルを安全な場所に抽出します。

2. ファイルが抽出されたら、抽出されたフォルダーを開き、**Exchange_Connector_Setup.exe** をダブルクリックしてオンプレミス Exchange コネクタをインストールします。

   > [!IMPORTANT]
   > 抽出先のフォルダーが安全な場所ではない場合、オンプレミス コネクタのインストールを完了したとき、**MicrosoftIntune.accountcert** という証明書ファイルを削除してください。

3. **[Microsoft Intune Exchange Connector]** ダイアログ ボックスで、 **[内部設置型 Microsoft Exchange Server]** または **[ホストされた Microsoft Exchange Server]** を選択します。

   ![Exchange Server の種類を選択する場所を示す画像](./media/intune-sa-exchange-connector-config.png)

   社内の Exchange Server の場合、**クライアント アクセス サーバー** ロールをホストする Exchange サーバーのサーバー名または完全修飾ドメイン名を指定します。

   ホスト型 Exchange Server の場合、Exchange Server のアドレスを指定します。 ホスト型 Exchange サーバーの URL を見つけるには:

   1. Office 365 の Outlook on the web を開きます。

   2. 左上の **?** アイコンを選択し、 **[バージョン情報]** を選択します。

   3. **[POP 外部サーバー]** の値を探します。

   4. **[プロキシ サーバー]** を選んで、ホスト型 Exchange サーバーのプロキシ サーバー設定を指定します。
       1. **[モバイル デバイス情報を同期するときにプロキシ サーバーを使用する]** を選択します。

       2. サーバーへのアクセスに使用する **[プロキシ サーバー名]** と **[ポート番号]** を入力します。

       3. プロキシ サーバーにアクセスできるユーザーの資格情報を指定する必要がある場合は、 **[資格情報を使用してプロキシ サーバーに接続する]** を選択します。 次に、**ドメイン\ユーザー**と**パスワード**を入力します。

       4. **[OK]** を選びます。

4. **[ユーザー (ドメイン\ユーザー)]** フィールドと **[パスワード]** フィールドに、Exchange Server への接続に必要な資格情報を入力します。 指定したアカウントには Intune を使用するためのライセンスが含まれている必要があります。 

5. ユーザーの Exchange Server メールボックスに通知を送信するために必要な資格情報を指定します。 このユーザーは通知専用でもかまいません。 通知ユーザーには、メールで通知を送信するための Exchange メールボックスが必要です。 これらの通知は、Intune で条件付きアクセス ポリシーにより構成できます。  

       Ensure that the Autodiscover service and Exchange Web Services are configured on the Exchange Client Access Server. For more information, see [Client Access server](https://technet.microsoft.com/library/dd298114.aspx).

6. **[パスワード]** フィールドに、このアカウントで Intune から Exchange Server にアクセスするのに必要なパスワードを入力します。

7. **[接続]** を選びます。

   > [!NOTE]
   > 接続が構成されるまでに数分かかることがあります。

構成中、Exchange コネクタはインターネットへのアクセスを有効にする目的でプロキシ設定が保存します。 プロキシ設定が変更された場合、更新後のプロキシ設定が Exchange コネクタに適用されるよう、Exchange コネクタをもう一度構成する必要があります。

Exchange コネクタが接続を設定すると、Exchange で管理されているユーザーに関連付けられたモバイル デバイスが自動的に同期され、Exchange コネクタに追加されます。 この同期が完了するまで時間がかかる場合があります。

> [!NOTE]
> オンプレミス Exchange コネクタをインストールしているとき、ある時点で Exchange 接続を削除した場合、インストールされていたコンピューターからオンプレミス Exchange コネクタをアンインストールする必要があります。



## <a name="install-connectors-for-multiple-exchange-organizations"></a>複数の Exchange 組織にコネクタをインストールする
Intune は、サブスクリプションあたり複数のオンプレミス Exchange コネクタに対応できます。 Exchange 組織が複数あるテナントの場合、Exchange 組織ごとにコネクタを設定できますが、1 つの組織に対して設定できるコネクタは 1 つのみとなります。 

複数の Exchange 組織に接続するためにコネクタを複数インストールする場合は、.zip フォルダーを 1 回ダウンロードしてから、インストールする各コネクタに対してその同じダウンロードを再利用します。 追加するコネクタごとに、前セクションの手順に従って、Exchange 組織内のサーバー上で設定プログラムを抽出し、実行してください。

後続のセクションで説明する高可用性、監視、手動同期といった機能は、Intune に接続している Exchange 組織ごとにサポートされています。

## <a name="on-premises-exchange-connector-high-availability-support"></a>オンプレミスの Exchange Connector の高可用性のサポート 
オンプレミス Exchange コネクタの高可用性とは、コネクタで使用されている Exchange クライアント アクセス サーバー (CAS) が利用できなくなった場合に、その Exchange 組織用の別の CAS を使用するようにコネクタで切り替えを行えることを意味します。 Exchange コネクタ自体では、高可用性はサポートされていません。 コネクタが失敗した場合、自動フェールオーバーは行われませんので、[新しいコネクタをインストール](#reinstall-the-on-premises-exchange-connector)することで、問題のコネクタを交換する必要があります。 

フェールオーバーを達成するために、コネクタでは指定された CAS を使用して Exchange への接続に成功すると、その Exchange 組織用の他の CAS が検出されます。 他の CAS に関する知識を活用してコネクタは、プライマリ CAS が利用できるようになるまで、別の CAS (利用可能な場合) にフェールオーバーすることができます。 既定では、他の CAS の検出は有効になっています。 フェールオーバーを無効にするには、次の手順に従います。  
1. Exchange コネクタがインストールされているサーバー上で、%*ProgramData*%\Microsoft\Windows Intune Exchange Connector にアクセスします。 
2. テキスト エディターを使用して、**OnPremisesExchangeConnectorServiceConfiguration.xml** を開きます。
3. &lt;IsCasFailoverEnabled&gt;**true**&lt;/IsCasFailoverEnabled&gt; を &lt;IsCasFailoverEnabled&gt;**false**&lt;/IsCasFailoverEnabled&gt; に変更して、機能を無効にします。    
 

## <a name="reinstall-the-on-premises-exchange-connector"></a>オンプレミス Exchange コネクタの再インストール
Exchange コネクタの再インストールが必要な場合があります。 各 Exchange 組織に対して接続がサポートされるコネクタは 1 つだけであるため、組織用に 2 つ目のコネクタをインストールすると、元のコネクタは、インストールした新しいコネクタに置き換えられます。

1. 「[Intune のオンプレミス Exchange コネクタのインストールと構成](#install-and-configure-the-intune-on-premises-exchange-connector)」の手順を使用して、新しいコネクタのインストールを開始します。 
2. プロンプトが表示されたら、 **[置換]** を選択して新しいコネクタをインストールします。  
   ![コネクタを置換するかどうかを確認する構成プロンプト](./media/exchange-connector-install/prompt-to-replace.png)

3. 引き続き前述の手順を使用して、Intune にもう一度ログインします。
4. 最後の画面が表示されたら、 **[閉じる]** を選択してインストールを完了します。  
   ![設定を完了する](./media/exchange-connector-install/successful-reinstall.png)
 

## <a name="monitor-the-exchange-connector-activity"></a>Exchange Connector アクティビティを監視する

Exchange コネクタの構成が正常に行えたら、接続の状態と前回成功した同期の試行を表示できます。 Exchange コネクタの接続を確認するには:

1. Intune ダッシュ ボードで、 **[Exchange へのアクセス]** を選択します。
2. **[Exchange On-Premises のアクセス]** を選択して、Exchange コネクタごとに接続状態を確認します。

また、前回いつ同期が完了したかも確認することができます。
--> 

### <a name="system-center-operations-manager-management-pack"></a>System Center Operations Manager 管理パック

Intune 1710 リリース以降では、[Exchange Connector および Intune の Operations Manager 管理パック](https://www.microsoft.com/download/details.aspx?id=55990&751be11f-ede8-5a0c-058c-2ee190a24fa6=True&e6b34bbe-475b-1abd-2c51-b5034bcdd6d2=True&fa43d42b-25b5-4a42-fe9b-1634f450f5ee=True)を使用できます。 管理パックを使用すれば、問題のトラブルシューティングを行う必要がある場合にさまざまな方法で Exchange コネクタを監視できます。

## <a name="manually-force-a-quick-sync-or-full-sync"></a>クイック同期または完全同期を手動で強制する
オンプレミス Exchange コネクタは、EAS と Intune デバイス レコードを定期的に自動同期します。 デバイスのコンプライアンス状態が変わった場合、自動同期プロセスによって定期的にレコードが更新され、デバイス アクセスをブロックまたは許可できます。

   - **クイック同期**は定期的に、1 日に数回実行されます。 クイック同期では、Intune のライセンスが与えられ、オンプレミス Exchange に条件付きでアクセスするユーザーのデバイスに関する情報が前回の同期以降に変更された部分だけ取得されます。

   - **完全同期**は既定で 1 日に 1 回実行されます。 完全同期では、Intune のライセンスが与えられ、オンプレミス Exchange に条件付きでアクセスするすべてのユーザーのデバイスに関する情報が取得されます。 完全同期の場合、Exchange サーバーの情報も取得され、Azure Portal の Intune によって指定された構成が Exchange サーバーで更新されます。 


Intune ダッシュボードで **[クイック同期]** または **[完全同期]** オプションを使用し、同期を実行するようにコネクタに強制できます。手順は次のようになります。

   1. Intune ダッシュ ボードで、 **[Exchange へのアクセス]** を選択します。
   2. **[Exchange On-Premises のアクセス]** を選択します。
   3. 同期するコネクタを選択し、 **[クイック同期]** または **[完全同期]** を選択します。

## <a name="next-steps"></a>次の手順
[Exchange On-premises の条件付きアクセス ポリシーを作成する](conditional-access-exchange-create.md)
