---
title: "PC クライアント ソフトウェアをインストールする"
description: "このガイドは、Microsoft Intune クライアント ソフトウェアによって、Windows PC を管理させる場合に役立ちます。"
keywords: 
author: nathbarn
ms.author: nathbarn
ms.date: 07/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 64c11e53-8d64-41b9-9550-4b4e395e8c52
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9316f78155b38f74765a353186a29dc90afce547
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/10/2017
---
# <a name="install-the-intune-software-client-on-windows-pcs"></a>Windows PC に Intune ソフトウェア クライアントをインストールする

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune クライアント ソフトウェアをインストールして Windows PC を登録します。 Intune クライアント ソフトウェアは、次の方法を使用してインストールできます。

- IT 管理者の場合、次のうちいずれか 1 つの方法でインストール: 手動インストール、グループ ポリシーを使用したインストール、またはディスク イメージに含まれるインストール

- エンド ユーザーの場合: クライアント ソフトウェアを手動でインストール

Intune クライアント ソフトウェアには、Intune 管理で PC を登録するために必要な最小限のソフトウェアが含まれます。 PC の登録後、Intune クライアント ソフトウェアは、PC の管理に必要な完全版クライアント ソフトウェアをダウンロードします。

このようにダウンロードを分割することで、ネットワークの帯域幅への影響が抑えられ、PC を Intune に最初に登録するのに要する時間が最短になります。 また、2 回目のダウンロードが完了した後、クライアントで最新のソフトウェアが利用できるようにします。

1 つの Intune ライセンスで、最大 5 台の PC に Intune クライアント ソフトウェアをインストールできます。

## <a name="download-the-intune-client-software"></a>Intune クライアント ソフトウェアのダウンロード

ユーザー自身が Intune クライアント ソフトウェアをインストールする場合を除き、すべての方法で、IT 管理者が初めにソフトウェアをダウンロードし、その後エンド ユーザーに展開する必要があります。

1.  [Microsoft Intune 管理コンソール](https://manage.microsoft.com/)で、**[管理]** &gt; **[クライアント ソフトウェアのダウンロード]** をクリックします。

  ![Intune PC クライアントのダウンロード](../media/pc-sa-client-download.png)

2. [**クライアント ソフトウェアのダウンロード**] ページで、[**クライアント ソフトウェアのダウンロード**] をクリックします。 ソフトウェアが含まれている **Microsoft_Intune_Setup.zip** パッケージをネットワーク上のセキュリティで保護された場所に保存します。

  Intune クライアント ソフトウェアのインストール パッケージにはお客様のアカウントに固有の情報が含まれており、これらの情報は埋め込み証明書に記載されています。 許可されていないユーザーがインストール パッケージにアクセスした場合は、埋め込み証明書に示されているアカウントに PC を登録できることになり、会社のリソースへのアクセスが行われる可能性があります。

3. インストール パッケージの内容をネットワーク上の安全な場所に抽出します。

    > [!IMPORTANT]
    > 抽出した **ACCOUNTCERT** ファイルを削除したり、名前を変更したりすると、クライアント ソフトウェアをインストールできなくなります。

## <a name="deploy-the-client-software-manually"></a>クライアント ソフトウェアを手動で展開する

クライアント ソフトウェアをインストールするコンピューターで、クライアント ソフトウェアのインストール ファイルが存在するフォルダーに移動します。 **Microsoft_Intune_Setup.exe** を実行して、クライアント ソフトウェアをインストールします。

> [!NOTE]
> クライアント PC のタスク バーに表示されるアイコンにマウスをポイントすると、インストールの状態が表示されます。

## <a name="deploy-the-client-software-by-using-group-policy"></a>グループ ポリシーを使ってクライアント ソフトウェアを展開する

1.  **Microsoft_Intune_Setup.exe** と **MicrosoftIntune.accountcert** というファイルを含むフォルダーで、次のコマンドを実行して、32 ビットおよび 64 ビット コンピューター用の Windows インストーラーベースのインストール プログラムを抽出します。

    ```
    Microsoft_Intune_Setup.exe/Extract <destination folder>
    ```

2.  **Microsoft_Intune_x86.msi** ファイル、**Microsoft_Intune_x64.msi** ファイル、および **MicrosoftIntune.accountcert** ファイルを、クライアント ソフトウェアをインストールする予定のすべてのコンピューターからアクセスできるネットワーク上の場所にコピーします。

    > [!IMPORTANT]
    > ファイルの名前を変更すると、クライアント ソフトウェアをインストールできなくなります。

3.  グループ ポリシーを使用して、ネットワーク上のコンピューターにソフトウェアを展開します。

    グループ ポリシーを使用してソフトウェアを自動的に展開する方法の詳細については、「[初心者向けのグループ ポリシー](https://technet.microsoft.com/library/hh147307.aspx)」を参照してください。

## <a name="deploy-the-client-software-as-part-of-an-image"></a>システム イメージの一部としてクライアント ソフトウェアを展開する
Intune クライアント ソフトウェアは、次の手順に従って、オペレーティング システム イメージの一部としてコンピューターに展開できます。

1.  クライアント インストール ファイルの **Microsoft_Intune_Setup.exe** と **MicrosoftIntune.accountcert** を、基準コンピューターの **%Systemdrive%\Temp\Microsoft_Intune_Setup** フォルダーにコピーします。

2.  次のコマンドを **SetupComplete.cmd** スクリプトに追加して、 **WindowsIntuneEnrollPending** レジストリのエントリを作成します。

    ```
    %windir%\system32\reg.exe add HKEY_LOCAL_MACHINE\Software\Microsoft\Onlinemanagement\Deployment /v
    WindowsIntuneEnrollPending /t REG_DWORD /d 1
    ```

3.  **setupcomplete.cmd** に次のコマンドを追加して、/PrepareEnroll コマンド ライン引数を使用して登録パッケージが実行されるようにします。

    ```
    %systemdrive%\temp\Microsoft_Intune_Setup\Microsoft_Intune_Setup.exe /PrepareEnroll
    ```
    > [!TIP]
    > **SetupComplete.cmd** スクリプトを使用すると、ユーザーがサインオンする前に、Windows セットアップによってシステムを変更できます。 **/PrepareEnroll** というコマンド ライン引数は、Windows セットアップの実行後に、対象のコンピューターが Intune に自動的に登録されるようにする引数です。

4.  **SetupComplete.cmd** を、基準コンピューターの **%Windir%\Setup\Scripts** フォルダーに配置します。

5.  基準コンピューターのイメージをキャプチャして、対象のコンピューターに展開します。

    対象のコンピューターで Windows セットアップの実行が完了し、コンピューターが再起動すると、 **WindowsIntuneEnrollPending** レジストリ キーが作成されます。 登録パッケージによって、コンピューターが登録されたかどうかがチェックされます。 登録されている場合は、何も行われません。 登録されていない場合は、Microsoft Intune への自動登録タスクが作成されます。

    スケジュールに従って、次回の自動登録タスクが実行されると、 **indowsIntuneEnrollPending** レジストリ値が存在するかどうかがチェックされ、対象の PC が Intune に登録されます。 登録できなかった場合は、このタスクが次回実行されるときに登録されます。 再試行は 1 か月間継続されます。

    登録が正常に完了するか、1 か月後に (どちらか早い方)、対象のコンピューターから Intune への自動登録タスク、**WindowsIntuneEnrollPending** レジストリ値、およびアカウント証明書が削除されます。

## <a name="instruct-users-to-self-enroll"></a>自分で登録するユーザーへの指示

ユーザーは、[ポータル Web サイト](https://portal.manage.microsoft.com)に移動して、Intune クライアント ソフトウェアをインストールします。 Web ポータルでユーザーに対して実際に表示される情報は、アカウントの MDM 機関およびユーザーの PC の OS プラットフォーム/バージョンによって異なります。

ユーザーに Intune ライセンスが割り当てられていない場合や、組織の MDM 機関が Intune に設定されていない場合、ユーザーには登録するためのオプションが表示されません。

ユーザーに Intune ライセンスが割り当てられており、組織の MDM 機関が Intune に設定されている場合は、次のようになります。

- Windows 7 または Windows 8 PC のユーザーには、組織に一意の PC クライアント ソフトウェアをダウンロードし、インストールして Intune に登録するオプションのみが表示されます。

- Windows 10 または Windows 8.1 PC のユーザーには、次の 2 つの登録オプションが表示されます。

  -  **PC をモバイル デバイスとして登録**: ユーザーは **[登録方法を表示]** ボタンを選択します。そうすると、PC をモバイル デバイスとして登録する方法の手順が示されます。 MDM 登録は既定の推奨登録オプションと見なされるため、このボタンは目立つように表示されます。 ただし、ここでは MDM オプションは適用されません。クライアント ソフトウェア インストールについてのみ説明します。
  - **Intune クライアント ソフトウェアを使用して PC を登録**: ユーザーに **[ダウンロードするには、ここをクリックします]** のリンクを選択するように指示する必要があります。ユーザーは、このリンクを選択してクライアント ソフトウェアをインストールします。

次の表に、オプションの概要を示します。

  ![プラットフォームごとの既定の登録オプション](../media/default-enrollment-options-table.png)

次のスクリーンショットは、ソフトウェア クライアントを使用してデバイスを登録する場合に、ユーザーに表示される内容を示しています。

最初に、デバイスを特定または登録するよう求められます。

  ![デバイスの特定または登録](../media/identify-device-or-enroll.png)

ユーザーに PC クライアント ソフトウェアをインストールさせるには、**[ダウンロードするには、ここをクリックします]** リンクを選択するように指示する必要があります。このリンクを選択すると、ユーザーは PC クライアント ソフトウェアをダウンロードできます。その際に、インストール プロセスが示されます。 **[登録方法を表示]** ボタンをクリックすると、MDM 登録を使用する登録方法に関するドキュメントが表示されます。これは、ソフトウェア クライアントの手順とは関係ありません。

  ![[ダウンロードするには、ここをクリックします] リンクの選択](../media/enroll-your-windows-device.png)

ユーザーがリンクをクリックすると、**[ソフトウェアのダウンロード]** ボタンが表示されます。これを選択して、PC クライアント ソフトウェアのインストールを開始します。

  ![[ソフトウェアのダウンロード] ボタンの選択](../media/download-pc-client-software.png)

その後、会社の資格情報を使用してサインインするよう求められます。

  ![資格情報を使用してサインイン](../media/sign-in-to-intune.png)

インストールのウェルカム ページが開きます。

  ![PC クライアント インストールのウェルカム ページ](../media/welcome-to-pc-agent-install-wizard.png)

**[次へ]** を選択すると、インストールが開始されます。

  ![PC クライアント インストールのウェルカム ページ](../media/welcome-to-pc-agent-install-wizard.png)

インストールが完了したら、**[完了]** を選択します。

  ![PC クライアント インストールの完了](../media/completed-the-setup-wizard.png)

Intune PC クライアント ソフトウェアを使用して既に登録されている PC をモバイル デバイスとして登録しようとすると、次のエラー画面が表示されます。

  ![PC が既に登録されている場合に表示される画面](../media/page-shown-if-pc-already-enrolled.png)

## <a name="monitor-and-validate-successful-client-deployment"></a>クライアントの正常展開の監視と確認
次のいずれかの手順を使用して、クライアントの正常展開を監視および確認できます。

### <a name="to-verify-the-installation-of-the-client-software-from-the-microsoft-intune-administrator-console"></a>Microsoft Intune 管理コンソールでクライアント ソフトウェアのインストールを確認するには

1.  [Microsoft Intune 管理コンソール](https://manage.microsoft.com/)で、**[グループ]** &gt; **[すべてのデバイス]** &gt; **[すべてのコンピューター]** をクリックします。

2.  一覧内で、Intune と通信しているコンピューターを見つけるか、または、**[デバイスの検索]** ボックスにコンピューターの名前 (または名前の一部) を入力して、特定の管理対象コンピューターを検索します。

3.  コンソールの下部ウィンドウに表示されるコンピューターの状態を確認します。 エラーがあれば解決します。

### <a name="to-create-a-computer-inventory-report-to-display-all-enrolled-computers"></a>登録されているすべてのコンピューターを表示する、コンピューターのインベントリ レポートを作成するには

1.  [Microsoft Intune 管理コンソール](https://manage.microsoft.com/)で、**[レポート]** &gt; **[コンピューター インベントリ レポート]** をクリックします。

2.  **[新しいレポートの作成]** ページで、(フィルターを適用しない場合は) すべてのフィールドを既定値のままにして、**[レポートの表示]**をクリックします。

3.  新しいウィンドウで **[コンピューター インベントリ レポート]** ページが開き、Intune に登録されているすべてのコンピューターが表示されます。

    > [!TIP]
    > レポートの列見出しをクリックすると、列の内容で一覧が並べ替えられます。

## <a name="uninstall-the-windows-client-software"></a>Windows クライアント ソフトウェアをアンインストールする

Windows クライアント ソフトウェアは 2 通りの方法で登録解除できます。

- Intune 管理コンソールから (推奨される方法)
- クライアントのコマンド プロンプトから

### <a name="unenroll-by-using-the-intune-admin-console"></a>Intune 管理コンソールを使用して登録解除する

Intune 管理コンソールを使用してソフトウェア クライアントの登録を解除するには、**[グループ]**、**[すべてのコンピューター]**、**[デバイス]** の順に進みます。 クライアントを右クリックし、**[インベントリからの削除/ワイプ]** を選択します。

### <a name="unenroll-by-using-a-command-prompt-on-the-client"></a>クライアントでコマンド プロンプトを使用して登録解除する

管理者特権のコマンド プロンプトで、次のいずれかのコマンドを実行します。

**方法 1**:

    "C:\Program Files\Microsoft\OnlineManagement\Common\ProvisioningUtil.exe" /UninstallAgents /MicrosoftIntune

**方法 2**<br>Windows のすべての SKU でこれらのエージェントがすべてインストールされていることに注意してください。

    wmic product where name="Microsoft Endpoint Protection Management Components" call uninstall<br>
    wmic product where name="Microsoft Intune Notification Service" call uninstall<br>
    wmic product where name="System Center 2012 - Operations Manager Agent" call uninstall<br>
    wmic product where name="Microsoft Online Management Policy Agent" call uninstall<br>
    wmic product where name="Microsoft Policy Platform" call uninstall<br>
    wmic product where name="Microsoft Security Client" call uninstall<br>
    wmic product where name="Microsoft Online Management Client" call uninstall<br>
    wmic product where name="Microsoft Online Management Client Service" call uninstall<br>
    wmic product where name="Microsoft Easy Assist v2" call uninstall<br>
    wmic product where name="Microsoft Intune Monitoring Agent" call uninstall<br>
    wmic product where name="Windows Intune Endpoint Protection Agent" call uninstall<br>
    wmic product where name="Windows Firewall Configuration Provider" call uninstall<br>
    wmic product where name="Microsoft Intune Center" call uninstall<br>
    wmic product where name="Microsoft Online Management Update Manager" call uninstall<br>
    wmic product where name="Microsoft Online Management Agent Installer" call uninstall<br>
    wmic product where name="Microsoft Intune" call uninstall<br>
    wmic product where name="Windows Endpoint Protection Management Components" call uninstall<br>
    wmic product where name="Windows Intune Notification Service" call uninstall<br>
    wmic product where name="System Center 2012 - Operations Manager Agent" call uninstall<br>
    wmic product where name="Windows Online Management Policy Agent" call uninstall<br>
    wmic product where name="Windows Policy Platform" call uninstall<br>
    wmic product where name="Windows Security Client" call uninstall<br>
    wmic product where name="Windows Online Management Client" call uninstall<br>
    wmic product where name="Windows Online Management Client Service" call uninstall<br>
    wmic product where name="Windows Easy Assist v2" call uninstall<br>
    wmic product where name="Windows Intune Monitoring Agent" call uninstall<br>
    wmic product where name="Windows Intune Endpoint Protection Agent" call uninstall<br>
    wmic product where name="Windows Firewall Configuration Provider" call uninstall<br>
    wmic product where name="Windows Intune Center" call uninstall<br>
    wmic product where name="Windows Online Management Update Manager" call uninstall<br>
    wmic product where name="Windows Online Management Agent Installer" call uninstall<br>
    wmic product where name="Windows Intune" call uninstall

> [!TIP]
> クライアントの登録を解除すると、関連するクライアントの無効になったサーバー側レコードが残ります。 登録解除プロセスは非同期です。9 つのエージェントをアンインストールする場合、完了に最大 30 分かかることがあります。

### <a name="check-the-unenrollment-status"></a>登録解除状態を確認する

"%ProgramFiles%\Microsoft\OnlineManagement" を確認し、次のディレクトリのみが左に表示されていることを確認します。

- AgentInstaller
- ログ
- Updates
- 共通

### <a name="remove-the-onlinemanagement-folder"></a>OnlineManagement フォルダーを削除する

登録解除プロセスでは、OnlineManagement フォルダーが削除されません。 アンインストール後、30 分待ち、このコマンドを実行します。 30 分待たずに実行した場合、アンインストールの状態がわからなくなる可能性があります。 フォルダーを削除するには、プロンプトを管理者特権で開き、次を実行します。

    "rd /s /q %ProgramFiles%\Microsoft\OnlineManagement".

### <a name="next-steps"></a>次のステップ
[Microsoft Intune を使用して Windows PC を管理する](manage-windows-pcs-with-microsoft-intune.md)
[Microsoft Intune でのクライアント セットアップのトラブルシューティング](../troubleshoot/troubleshoot-client-setup-in-microsoft-intune.md)
