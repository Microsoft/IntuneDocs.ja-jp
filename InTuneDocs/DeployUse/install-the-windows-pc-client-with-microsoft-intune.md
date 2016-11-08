---

title: "PC クライアント ソフトウェアをインストールする | Microsoft Intune"
description: "このガイドは、Microsoft Intune クライアント ソフトウェアによって、Windows PC を管理させる場合に役立ちます。"
keywords: 
author: NathBarn
manager: arob98
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 64c11e53-8d64-41b9-9550-4b4e395e8c52
ms.reviewer: owenyen
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eba2421fb929d21eb36c273eb6cb43a06ac03cb4
ms.openlocfilehash: ed92874cce2877d31d83a619ec8ffb63a57cd5c3


---

# <a name="install-the-intune-software-client-on-windows-pcs"></a>Windows PC に Intune ソフトウェア クライアントをインストールする
Intune クライアント ソフトウェアをインストールして Windows PC を登録します。 Intune クライアント ソフトウェアは、次の方法でインストールできます。

- 手動インストール
- グループ ポリシーを使用したインストール
- ディスク イメージに含める
- ユーザーによるインストール

最初にダウンロードされる Intune ソフトウェア クライアントには、Intune 管理で PC を登録するために必要な最小限のソフトウェアが含まれます。 PC の登録後、Intune ソフトウェア クライアントは、PC の管理に必要な完全なクライアント ソフトウェアをダウンロードします。

この一連のダウンロードでは、Intune に PC を最初に登録するために必要な時間が最小限に抑えられます。 また、2 回目のダウンロードが完了した後、クライアントで最新のソフトウェアが利用できるようにします。

## <a name="download-the-intune-client-software"></a>Intune クライアント ソフトウェアのダウンロード

ユーザー自身が Intune クライアント ソフトウェアをインストールする場合を除き、ソフトウェアをダウンロードして、展開する必要があります。

1.  [Microsoft Intune 管理コンソール](https://manage.microsoft.com/)で、**[管理]** &gt; **[クライアント ソフトウェアのダウンロード]** をクリックします。

  ![Intune PC クライアントのダウンロード](../media/pc-sa-client-download.png)

2.  [**クライアント ソフトウェアのダウンロード**] ページで、[**クライアント ソフトウェアのダウンロード**] をクリックします。 ソフトウェアが含まれている **Microsoft_Intune_Setup.zip** パッケージをネットワーク上のセキュリティで保護された場所に保存します。

    > [!NOTE]
    > Intune クライアント ソフトウェアのインストール パッケージには、アカウントの情報が含まれています。 許可されていないユーザーがインストール パッケージにアクセスした場合は、埋め込み証明書に示されているアカウントにそのコンピューターを登録できることになり、会社のリソースへのアクセスが行われる可能性があります。

3.  インストール パッケージの内容をネットワーク上の安全な場所に抽出します。

    > [!IMPORTANT]
    > 抽出した **ACCOUNTCERT** ファイルを削除したり、名前を変更したりすると、クライアント ソフトウェアをインストールできなくなります。

## <a name="deploy-the-client-software-manually"></a>クライアント ソフトウェアを手動で展開する

コンピューター上で、クライアント ソフトウェアのインストール ファイルが置かれているフォルダーに移動します。 **Microsoft_Intune_Setup.exe** を実行して、クライアント ソフトウェアをインストールします。

    > [!NOTE]
    > The status of the installation is displayed when you hover over the icon in the taskbar on the client computer.

## <a name="deploy-the-client-software-by-using-group-policy"></a>グループ ポリシーを使ってクライアント ソフトウェアを展開する

1.  **Microsoft_Intune_Setup.exe** と **MicrosoftIntune.accountcert** というファイルを含むフォルダーで、次のコマンドを実行して、32 ビットおよび 64 ビット コンピューター用の Windows インストーラーベースのインストール プログラムを抽出します。

    ```
    Microsoft_Intune_Setup.exe/Extract <destination folder>
    ```

2.  **Microsoft_Intune_x86.msi** ファイル、**Microsoft_Intune_x64.msi** ファイル、および **MicrosoftIntune.accountcert** ファイルを、クライアント ソフトウェアをインストールする予定のすべてのコンピューターからアクセスできるネットワーク上の場所にコピーします。

    > [!IMPORTANT]
    > ファイルの名前を変更すると、クライアント ソフトウェアをインストールできなくなります。

3.  グループ ポリシーを使用して、ネットワーク上のコンピューターにソフトウェアを展開します。

    グループ ポリシーを使用してソフトウェアを自動的に展開する方法の詳細については、Windows Server のマニュアルを参照してください。

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

## <a name="instruct-users-to-selfenroll"></a>自分で登録するユーザーへの指示

ユーザーは、[ポータル Web サイト](http://portal..manage.microsoft.com)に移動して、Intune クライアント ソフトウェアをインストールできます。 デバイスが Windows PC であることを Web ポータルが検出できる場合、ユーザーは Intune ソフトウェア クライアントをダウンロードして、PC を登録するように求められます。 ソフトウェアがダウンロードされたら、ユーザーはインストールして、PC を管理できます。

![Intune ポータルが Intune ソフトウェア クライアントをダウンロードするように要求する](../media/software-client-download.png)

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


### <a name="see-also"></a>関連項目
[Microsoft Intune を使用して Windows PC を管理する](manage-windows-pcs-with-microsoft-intune.md)
[Microsoft Intune でのクライアント セットアップのトラブルシューティング](../troubleshoot/troubleshoot-client-setup-in-microsoft-intune.md)



<!--HONumber=Nov16_HO1-->


