---
title: Microsoft Intune のオンプレミス Exchange Connector をセットアップする
titleSuffix: ''
description: Intune の登録と Exchange Active Sync (EAS) に基づいて、Exchange メールボックスへのデバイス アクセスを管理するには、オンプレミスの Exchange Connector を使います。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/08/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a0376ea1-eb13-4f13-84da-7fd92d8cd63c
ms.reviewer: chrisgre
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 019f09444f96d8bb3bca046ef5be20af373a3bff
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2018
ms.locfileid: "52183709"
---
# <a name="set-up-the-intune-on-premises-exchange-connector-in-microsoft-intune-azure"></a>Microsoft Intune Azure で Intune のオンプレミス Exchange コネクタをセットアップする

オンプレミス Exchange Server 環境では、Intune の条件付きアクセスを利用し、Exchange のオンプレミス メールボックスへのアクセスを許可または禁止できます。 Exchange Active Sync オンプレミス コネクタを使用し、Exchange 組織に Intune を接続し、デバイスのコンプライアンス ポリシーと共に Intune の条件付きアクセスを設定します。 次に、デバイスが Exchange に接続しようとすると、Intune はそのデバイスが Intune に登録されているか、基準に準拠しているか判断します。 Intune に登録されているデバイスを判断するために、オンプレミス Exchange コネクタは Exchange Server の Exchange Active Sync (EAS) レコードを Intune レコードにマッピングします。 このしくみについては、「[Intune での条件付きアクセスの一般的な使用方法](conditional-access-intune-common-ways-use.md)」を参照してください。

> [!IMPORTANT]
> Intune は、サブスクリプションあたり複数のオンプレミス Exchange コネクタに対応できるようになりました。 オンプレミス Exchange 組織が複数になる場合、Exchange 組織別にコネクタを設定できます。

オンプレミス Exchange Server と通信するために Microsoft Intune を有効にする接続を設定するには、概して次のような手順を行います。

1.  Intune オンプレミス Exchange コネクタを Azure Portal からダウンロードします。
2.  オンプレミス Exchange 組織のコンピューターに Exchange コネクタをインストールし、構成します。
3.  Exchange 接続を確認します。
4. Intune と接続させる Exchange 組織ごとに以上の手順を繰り返します。

## <a name="intune-on-premises-exchange-connector-requirements"></a>Intune オンプレミス Exchange コネクタの要件
以下の表に、オンプレミス Exchange コネクタをインストールするコンピューターの要件を示します。


|            要件             |                                                                                                                                                                                                        詳細情報                                                                                                                                                                                                        |
|------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|         Operating systems          |                                                               Intune は、Windows Server 2008 SP2 64 ビット、Windows Server 2008 R2、Windows Server 2012、Windows Server 2012 R2、または Windows Server 2016 の任意のエディションを実行しているコンピューター上のオンプレミス Exchange コネクタをサポートします。<br /><br />Server Core インストールでは、コネクタはサポートされません。                                                                |
|         Microsoft Exchange         |                                                                           オンプレミス コネクタには、Microsoft Exchange 2010 SP3 以降または従来の Exchange Online Dedicated が必要です。 Exchange Online Dedicated 環境が<strong>新しい</strong>構成か<strong>従来の</strong>構成かを確認するには、アカウント マネージャーに問い合わせてください。                                                                           |
| モバイル デバイス管理機関 |                                                                                                                              [モバイル デバイス管理機関を Intune に設定します](https://docs.microsoft.com/intune-classic/deploy-use/prerequisites-for-enrollment#step-2-mdm-authority-set)。                                                                                                                               |
|              ハードウェア              |                                                                                                                                                     コネクタをインストールするコンピューターには、1.6 GHz の CPU と 2 GB の RAM と 10 GB の空きディスク容量が必要です。                                                                                                                                                      |
|  Active Directory の同期  |                                                                                      コネクタを使用して Intune を Exchange Server に接続するには、[Active Directory の同期をセットアップ](users-add.md)して、ローカル ユーザーとセキュリティ グループが Azure Active Directory のインスタンスと同期されるようにする必要があります。                                                                                      |
|        その他のソフトウェア         |                                                                                                                                           コネクタをホストするコンピューターに、Microsoft .NET Framework 4.5 および Windows PowerShell 2.0 の完全インストールがインストールされている必要があります。                                                                                                                                           |
|              ネットワーク               | コネクタをインストールするコンピューターは、Exchange Server をホストするドメインと信頼関係があるドメインに参加している必要があります。<br /><br />コンピューターは、ポート 80 と 443 でファイアウォールとプロキシ サーバー経由で Intune サービスにアクセスできるように構成する必要があります。 Intune によって使用されるドメインには、manage.microsoft.com、&#42;manage.microsoft.com、および &#42;.manage.microsoft.com が含まれます。 |

### <a name="exchange-cmdlet-requirements"></a>Exchange コマンドレットの要件

オンプレミス Exchange コネクタが使用する Active Directory ユーザー アカウントを作成する必要があります。 アカウントには、次の必須の Windows PowerShell Exchange コマンドレットを実行するための権限が必要です。


 -   Get-ActiveSyncOrganizationSettings, Set-ActiveSyncOrganizationSettings
 -   Get-CasMailbox、Set-CasMailbox
 -   Get-ActiveSyncMailboxPolicy、Set-ActiveSyncMailboxPolicy、New-ActiveSyncMailboxPolicy、Remove-ActiveSyncMailboxPolicy
 -   Get-ActiveSyncDeviceAccessRule、Set-ActiveSyncDeviceAccessRule、New-ActiveSyncDeviceAccessRule、Remove-ActiveSyncDeviceAccessRule
 -   Get-ActiveSyncDeviceStatistics
 -   Get-ActiveSyncDevice
 -   Get-ExchangeServer
 -   Get-ActiveSyncDeviceClass
 -   Get-Recipient
 -   Clear-ActiveSyncDevice、Remove-ActiveSyncDevice
 -   Set-ADServerSettings
 -   Get-Command

## <a name="download-the-on-premises-exchange-connector-software-installation-package"></a>オンプレミス Exchange コネクタ ソフトウェア インストール パッケージのダウンロード

1. オンプレミス Exchange コネクタのサポートされている Windows Server オペレーティング システムで、Exchange Server を使用するライセンスを持つオンプレミス Exchange Server 内の管理者であるユーザー アカウントを使用して、[Azure portal](http://portal.azure.com) を開きサインインします。

2. 左側のメニューから **[すべてのサービス]** を選択し、テキスト ボックス フィルターに「**Intune**」と入力します。

3. **[Intune]** を選択し、Intune ダッシュボードが開いたら、**[オンプレミス アクセス]** を選択します。

4. **[セットアップ]** の下で **[Exchange ActiveSync のコネクタ]** を選択し、**[オンプレミス コネクタをダウンロードします]** を選択します。

5.  オンプレミス Exchange コネクタは、開いたり保存したりできる圧縮 (.zip) フォルダーに含まれています。 **[ファイルのダウンロード]** ダイアログ ボックスで **[保存]** を選んで、圧縮フォルダーを安全な場所に保存します。

    > [!IMPORTANT]
    > オンプレミス Exchange コネクタ フォルダー内のファイルの名前を変更したり、ファイルを移動したりしないでください。 フォルダーの内容を移動したり、名前を変更したりすると、Exchange コネクタのインストールが失敗します。

## <a name="install-and-configure-the-intune-on-premises-exchange-connector"></a>Intune のオンプレミス Exchange コネクタのインストールと構成
次の手順を実行して、Intune のオンプレミス Exchange コネクタをインストールします。 Exchange 組織が複数ある場合、設定する追加 Exchange コネクタごとに以上の手順を繰り返します。

1. オンプレミス Exchange コネクタのサポートされているオペレーティング システムで、**Exchange_Connector_Setup.zip** のファイルを安全な場所に抽出します。

2. ファイルが抽出されたら、抽出されたフォルダーを開き、**Exchange_Connector_Setup.exe** をダブルクリックしてオンプレミス Exchange コネクタをインストールします。

   > [!IMPORTANT]
   > 抽出先のフォルダーが安全な場所ではない場合、オンプレミス コネクタのインストールを完了したとき、**MicrosoftIntune.accountcert** という証明書ファイルを削除してください。

3. **[Microsoft Intune Exchange Connector]** ダイアログ ボックスで、**[内部設置型 Microsoft Exchange Server]** または **[ホストされた Microsoft Exchange Server]** を選択します。

   ![Exchange Server の種類を選択する場所を示す画像](./media/intune-sa-exchange-connector-config.png)

   オンプレミス Exchange サーバーの場合、**クライアント アクセス サーバー** ロールをホストする Exchange サーバーのサーバー名または完全修飾ドメイン名を指定します。

   ホスト型 Exchange Server の場合、Exchange Server のアドレスを指定します。 ホスト型 Exchange サーバーの URL を見つけるには:

   1. Office 365 の Outlook on the web を開きます。

   2. 左上の **?**  アイコンを選択し、**[バージョン情報]** を選択します。

   3. **[POP 外部サーバー]** の値を探します。

   4. **[プロキシ サーバー]** を選んで、ホスト型 Exchange サーバーのプロキシ サーバー設定を指定します。
       1. **[モバイル デバイス情報を同期するときにプロキシ サーバーを使用する]** を選択します。

       2. サーバーへのアクセスに使用する **[プロキシ サーバー名]** と **[ポート番号]** を入力します。

       3. プロキシ サーバーにアクセスできるユーザーの資格情報を指定する必要がある場合は、**[資格情報を使用してプロキシ サーバーに接続する]** を選択します。 次に、**ドメイン\ユーザー**と**パスワード**を入力します。

       4. **[OK]** を選びます。

   5. **[ユーザー (ドメイン\ユーザー)]** フィールドと **[パスワード]** フィールドに、Exchange Server への接続に必要な資格情報を入力します。

   6.  ユーザーの Exchange Server メールボックスに通知を送信するために必要な資格情報を指定します。 このユーザーは通知専用でもかまいません。 通知ユーザーには、メールで通知を送信できるように Exchange メールボックスが必要です。 これらの通知は、Intune で条件付きアクセス ポリシーにより構成できます。  

       自動検出サービスと Exchange Web Services が Exchange クライアント アクセス サーバーで構成されていることを確認します。 詳細については、「[クライアント アクセス サーバー](https://technet.microsoft.com/library/dd298114.aspx)」を参照してください。

   7.  **[パスワード]** フィールドに、このアカウントで Intune から Exchange Server にアクセスするのに必要なパスワードを入力します。

   8. **[接続]** を選びます。

   > [!NOTE]
   > 接続が構成されるまでに数分かかることがあります。

構成中、Exchange コネクタはインターネットへのアクセスを有効にする目的でプロキシ設定が保存します。 プロキシ設定が変更された場合、更新後のプロキシ設定が Exchange コネクタに適用されるよう、Exchange コネクタをもう一度構成する必要があります。

Exchange コネクタが接続を設定すると、Exchange で管理されているユーザーに関連付けられたモバイル デバイスが自動的に同期され、Exchange コネクタに追加されます。 この同期が完了するまで時間がかかる場合があります。

> [!NOTE]
> オンプレミス Exchange コネクタをインストールしているとき、ある時点で Exchange 接続を削除した場合、インストールされていたコンピューターからオンプレミス Exchange コネクタをアンインストールする必要があります。

## <a name="install-connectors-for-multiple-exchange-organizations"></a>複数の Exchange 組織にコネクタをインストールする
Intune は、サブスクリプションあたり複数のオンプレミス Exchange コネクタに対応できます。 Exchange 組織が複数あるテナントには、組織ごとにコネクタを 1 つ設定できます。 .zip フォルダーを 1 回ダウンロードし、Exchange 組織ごとに前セクションの手順を行い、組織のサーバーでセットアップ プログラムを抽出し、実行してください。

後続のセクションで説明する高可用性、監視、手動同期といった機能は、Intune に接続している Exchange 組織ごとにサポートされています。

## <a name="on-premises-exchange-connector-high-availability-support"></a>オンプレミスの Exchange Connector の高可用性のサポート 
Exchange Connector によって、指定の CAS で Exchange への接続が作成された後、コネクタで別の CAS も検出することができます。 メインの CAS が利用できなくなった場合、再度利用可能になるまで、コネクタが別の CAS (ある場合) にフェールオーバーします。 この機能は、既定で有効になっています。 この機能を無効にするには、次の手順に従います。
1. Exchange Connector がインストールされているサーバーで、%*ProgramData*%\Microsoft\Windows Intune Exchange Connector にアクセスします。 
2. テキスト エディターを使用して、**OnPremisesExchangeConnectorServiceConfiguration.xml** を開きます。
3. &lt;IsCasFailoverEnabled&gt;**true**&lt;/IsCasFailoverEnabled&gt; を &lt;IsCasFailoverEnabled&gt;**false**&lt;/IsCasFailoverEnabled&gt; に変更して、機能を無効にします。    


## <a name="monitor-the-exchange-connector-activity"></a>Exchange Connector アクティビティを監視する

Exchange コネクタを正常に構成したら、接続のステータスと前回の成功した同期の試行を表示できます。 Exchange コネクタ接続を確認するには:

1. Intune ダッシュボードで、**[オンプレミス アクセス]** を選択します。
2. **[セットアップ]** の下で **[Exchange ActiveSync のコネクタ]** を選択し、各 Exchange コネクタの接続状態を確認します。

また、前回いつ同期が完了したかも確認することができます。

### <a name="system-center-operations-manager-scom-management-pack"></a>System Center Operations Manager (SCOM) 管理パック

Intune 1710 リリース以降では、[Exchange Connector および Intune の SCOM 管理パック](https://www.microsoft.com/download/details.aspx?id=55990&751be11f-ede8-5a0c-058c-2ee190a24fa6=True&e6b34bbe-475b-1abd-2c51-b5034bcdd6d2=True&fa43d42b-25b5-4a42-fe9b-1634f450f5ee=True)を使用できます。 問題のトラブルシューティングを行う必要がある場合、これにより別の方法で Exchange Connector を監視できます。

## <a name="manually-force-a-quick-sync-or-full-sync"></a>クイック同期または完全同期を手動で強制する
オンプレミス Exchange コネクタは、EAS と Intune デバイス レコードを定期的に自動同期します。 デバイスのコンプライアンス状態が変わった場合、自動同期プロセスによって定期的にレコードが更新され、デバイス アクセスを適宜、禁止または許可できます。

   - **クイック同期**は定期的に、1 日に数回実行されます。 クイック同期では、Intune のライセンスが与えられ、オンプレミス Exchange に条件付きでアクセスするユーザーのデバイスに関する情報が前回の同期以降に変更された部分だけ取得されます。

   - **完全同期**は既定で 1 日に 1 回実行されます。 完全同期では、Intune のライセンスが与えられ、オンプレミス Exchange に条件付きでアクセスするすべてのユーザーのデバイスに関する情報が取得されます。 完全同期の場合、Exchange サーバーの情報も取得され、Azure Portal の Intune によって指定された構成が Exchange サーバーで更新されます。 

Intune ダッシュボードで **[クイック同期]** または **[完全同期]** オプションを使用し、同期を実行するようにコネクタに強制できます。手順は次のようになります。

   1. Intune ダッシュボードで、**[オンプレミス アクセス]** を選択します。
   2. **[セットアップ]** で **[Exchange Active Sync のコネクタ]** を選択します。
   3. 同期するコネクタを選択し、**[クイック同期]** または **[完全同期]** を選択します。

## <a name="next-steps"></a>次の手順
[Exchange On-premises の条件付きアクセス ポリシーを作成する](conditional-access-exchange-create.md)
