---
title: Microsoft Intune で Windows 10 デバイスに PowerShell スクリプトを追加する - Azure | Microsoft Docs
description: Microsoft Intune で Windows 10 デバイスに対して、PowerShell スクリプトの作成および実行、Azure Active Directory グループへのスクリプト ポリシーの割り当て、レポートを使用したスクリプトの監視、追加したスクリプトの削除を行います。 一般的な問題とその解決策についても説明します。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 768b6f08-3eff-4551-b139-095b3cfd1f89
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: cbf2031a316b1f7c2e22d165363cca12cfd70291
ms.sourcegitcommit: 27e63a96d15bc4062af68c2764905631bd928e7b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2019
ms.locfileid: "71061577"
---
# <a name="use-powershell-scripts-on-windows-10-devices-in-intune"></a>Intune で Windows 10 デバイスに対して PowerShell スクリプトを使用する

Windows 10 デバイスで実行するために Intune に PowerShell スクリプトをアップロードするには、Microsoft Intune 管理拡張機能を使用します。 管理拡張機能は Windows 10 モバイル デバイス管理 (MDM) を拡張するもので、最新の管理に簡単に移行できます。

この機能は、以下に適用されます。

- Windows 10 以降

## <a name="move-to-modern-management"></a>最新の管理への移行

エンドユーザーのコンピューティングはデジタル変換を経ています。 従来の IT 担当者は、単一のデバイス プラットフォーム、企業所有のデバイス、オフィスで働くユーザー、および手動で事後対応型の多様な IT プロセスに重点を置きます。 最近の職場では、ユーザーと企業の両方が所有する多数のプラットフォームが使用され、ユーザーがどこからでも作業できるようにして、自動化された事前対応型の IT プロセスを提供しています。

Microsoft Intune などの MDM サービスでは、Windows 10 を実行するモバイル デバイスとデスクトップ デバイスを管理できます。 組み込みの Windows 10 管理クライアントは、Intune と通信してエンタープライズ管理タスクを実行します。 高度なデバイス構成やトラブルシューティングなど、必要な場合があるタスクがいくつかあります。 Win32 アプリの管理の場合、ご自分の Windows 10 デバイス上の [Win32 アプリの管理](apps-win32-app-management.md)機能を使えます。

Intune 管理拡張機能は、Windows 10 MDM の標準機能を補完するものです。 PowerShell スクリプトを作成し、Windows 10 デバイスで実行することができます。 たとえば、高度なデバイス構成を行う PowerShell スクリプトを作成します。 その後、スクリプトを Intune にアップロードし、Azure Active Directory (AD) グループにスクリプトを割り当てて、スクリプトを実行します。 スクリプトの実行状態を最初から完了まで監視できます。

## <a name="prerequisites"></a>必要条件

Intune 管理拡張機能には次の前提条件があります。 前提条件が満たされると、PowerShell スクリプトまたは Win32 アプリがユーザーやデバイスに割り当てられたときに、Intune 管理拡張機能が自動的にインストールされます。

- Windows 10 バージョン 1607 以降を実行しているデバイス。 デバイスが[一括自動登録](windows-bulk-enroll.md)を使用して登録される場合は、Windows 10 バージョン 1703 以降でデバイスを実行する必要があります。 Intune 管理拡張機能は S モードの Windows 10 ではサポートされません。S モードではストア以外にあるアプリの実行が許可されないためです。 
  
- 次を含む、Azure Active Directory (AD) に参加しているデバイス:  
  
  - Hybrid Azure AD 参加済み: Azure Active Directory (AD) だけでなく、オンプレミスの Active Directory (AD) にも参加しているデバイス。 [Hybrid Azure Active Directory 参加の実装の計画](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-plan)について、ガイダンスを参照してください。

- 次を含む、Intune に登録されたデバイス:

  - グループ ポリシー (GPO) に登録されたデバイス。 ガイダンスについては、「[Enroll a Windows 10 device automatically using Group Policy](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy)」(グループ ポリシーを使用して Windows 10 デバイスを自動的に登録する) を参照してください。
  
  - 次の状況で、Intune に手動で登録されたデバイス:
  
    - Azure AD では、[Intune への自動登録](quickstart-setup-auto-enrollment.md)が有効です。 エンド ユーザーは、ローカル ユーザー アカウントを使用してデバイスにサインインし、手動でデバイスを Azure AD に参加させてから、自分の Azure AD アカウントを使用してデバイスにサインインします。
    
    または  
    
    - ユーザーが自分の Azure AD アカウントを使用してデバイスにサインインし、Intune に登録している。

  - Configuration Manager と Intune を使用して共同管理しているデバイス。 **[クライアント アプリ]** ワークロードが **[Pilot Intune]\(パイロット Intune\)** または **[Intune]** に設定されていることを確認します。 ガイダンスについては、次の記事を参照してください。 
  
    - [共同管理とは](https://docs.microsoft.com/sccm/comanage/overview) 
    - [クライアント アプリ ワークロード](https://docs.microsoft.com/sccm/comanage/workloads#client-apps)
    - [Configuration Manager のワークロードを Intune に切り替える](https://docs.microsoft.com/sccm/comanage/how-to-switch-workloads)
  
> [!TIP]
> 必ずデバイスを Azure AD に[参加](https://docs.microsoft.com/azure/active-directory/user-help/user-help-join-device-on-network)させます。 Azure AD への[登録](https://docs.microsoft.com/azure/active-directory/user-help/user-help-register-device-on-network)のみが行われているデバイスは、スクリプトを受信しません。

## <a name="create-a-script-policy-and-assign-it"></a>スクリプト ポリシーを作成して割り当てる

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインします。
2. **[デバイス構成]**  >  **[PowerShell スクリプト]**  >  **[追加]** の順に選択します。

    ![Microsoft Intune で PowerShell スクリプトを追加および使用する](./media/mgmt-extension-add-script.png)

3. **[基本]** で、次のプロパティを入力し、 **[次へ]** を選択します。
    - **名前**: PowerShell スクリプトの名前を入力します。 
    - **説明**:PowerShell スクリプトの説明を入力します。 この設定は省略可能ですが、推奨されます。
4. **[スクリプト設定]** で、次のプロパティを入力し、 **[次へ]** を選択します。
    - **スクリプトの場所**: PowerShell スクリプトを参照します。 スクリプトは 200 KB (ASCII) 未満とする必要があります。
    - **このスクリプトをログオンしたユーザーの資格情報を使用して実行する**: **[はい]** を選択すると、デバイス上でユーザーの資格情報を使用してスクリプトが実行されます。 **[いいえ]** (既定) を選択すると、システム コンテキストでスクリプトが実行されます。 管理者の多くは、 **[はい]** を選択します。 システム コンテキストでスクリプトを実行する必要がある場合は、 **[いいえ]** を選択します。
    - **[スクリプト署名チェックを強制]** : 信頼された発行者がスクリプトに署名する必要がある場合は、 **[はい]** を選択します。 スクリプトに署名する要件がない場合は、 **[いいえ]** (既定) を選択します。 
    - **64 ビットの PowerShell ホストでスクリプトを実行する**: **[はい]** を選択すると、64 ビット クライアント アーキテクチャ上の 64 ビット PowerShell (PS) ホストでスクリプトが実行されます。 **[いいえ]** (既定値) を選択すると、32 ビット PowerShell ホストでスクリプトが実行されます。

      **[はい]** または **[いいえ]** に設定する場合は、次の表を使用して新しいポリシー動作と既存のポリシー動作を確認してください。

      | 64 ビットの PS ホストでスクリプトを実行する | クライアント アーキテクチャ | 新しい PS スクリプト | 既存のポリシー PS スクリプト |
      | --- | --- | --- | --- | 
      | [いいえ] | 32 ビット  | 32 ビットの PS ホストがサポートされる | 32 ビットおよび 64 ビットのアーキテクチャで動作する 32 ビット PS ホストでのみ実行されます。 |
      | はい | 64 ビット | 64 ビット アーキテクチャ用の 64 ビットの PS ホストでスクリプトが実行されます。 32 ビット上で実行した場合、スクリプトは 32 ビットの PS ホストで実行されます。 | 32 ビットの PS ホストでスクリプトが実行されます。 この設定が 64 ビットに変更されると、スクリプトは 64 ビットの PS ホストで開き (実行されない)、スクリプトから結果がレポートされます。 32 ビット上で実行した場合、スクリプトは 32 ビットの PS ホストで実行されます。 |

5. **[スコープ タグ]** を選択します。 スコープ タグは省略可能です。 「[Use role-based access control (RBAC) and scope tags for distributed IT](scope-tags.md)」 (分散 IT にロールベースのアクセス制御 (RBAC) とスコープ タグを使用する) に詳細情報が含まれています。

    スコープ タグを追加するには、次のようにします。

    1. **[スコープ タグを選択]** を選び、リストから既存のスコープ タグを選択し、 **[選択]** を選びます。

    2. 完了したら、 **[次へ]** を選択します。

6. **[割り当て]**  >  **[含めるグループを選択]** の順に選択します。 Azure AD グループの既存のリストが表示されます。

    1. スクリプトを受信するデバイスを持つユーザーが属する 1 つまたは複数のグループを選択します。 **[選択]** を選択します。 選択したグループがリストに表示され、ポリシーが示されます。

        > [!NOTE]
        > Intune 内の PowerShell スクリプトは、Azure AD デバイスのセキュリティ グループ、または Azure AD ユーザー セキュリティ グループを対象にすることができます。

    2. **[次へ]** を選択します。

        ![Microsoft Intune で、PowerShell スクリプトをデバイス グループに割り当てる、またはデプロイする](./media/mgmt-extension-assignments.png)

7. **[確認 + 追加]** で、構成した設定の概要が表示されます。 **[追加]** を選択してスクリプトを保存します。 **[追加]** を選択すると、選択したグループにポリシーが展開されます。

## <a name="important-considerations"></a>重要な考慮事項

- スクリプトがユーザー コンテキストに設定され、エンド ユーザーに管理者権限がある場合、既定で PowerShell スクリプトは管理者特権で実行されます。

- エンド ユーザーは、PowerShell スクリプトを実行するためにデバイスにサインインする必要はありません。

- Intune 管理拡張機能のクライアントでは、Intune で 1 時間ごと、および再起動のたびに、新しいスクリプトまたは変更がないか確認されます。 ポリシーを Azure AD グループに割り当てた後に、PowerShell スクリプトを実行すると、実行結果がレポートされます。 スクリプトは一度実行されると、スクリプトまたはポリシーに変更が発生するまで、再実行されません。

## <a name="monitor-run-status"></a>実行状態を監視する

Azure Portal でユーザーとデバイスの PowerShell スクリプトの実行状態を監視できます。

**[PowerShell スクリプト]** で、監視するスクリプトを選択し、 **[監視]** を選択し、次のいずれかのレポートを選択します。

- **デバイスの状態**
- **ユーザーの状態**

## <a name="intune-management-extension-logs"></a>Intune 管理拡張機能のログ

クライアント コンピューター上のエージェント ログは、一般的に `\ProgramData\Microsoft\IntuneManagementExtension\Logs` にあります。 [CMTrace.exe](https://docs.microsoft.com/sccm/core/support/tools) を使用してこれらのログ ファイルを表示できます。 

![Microsoft Intune での cmtrace エージェント ログのスクリーンショットまたはサンプル](./media/apps-win32-app-10.png)  

## <a name="delete-a-script"></a>スクリプトを削除する

**PowerShell スクリプト**で、スクリプトを右クリックし、 **[削除]** を選択します。

## <a name="common-issues-and-resolutions"></a>よくある問題と解決策

### <a name="issue-intune-management-extension-doesnt-download"></a>問題:Intune 管理拡張機能をダウンロードできない

**考えられる解決策**:

- デバイスが Azure AD に参加していない。 デバイスが (この記事の) [前提条件](#prerequisites)を満たしていることを確認します。 
- ユーザーまたはデバイスが属しているグループに PowerShell スクリプトまたは Win32 アプリが割り当てられていない。
- インターネット アクセスがない、Windows プッシュ通知サービス (WNS) にアクセスしていない、などの理由でデバイスが Intune サービスにチェックインできない。
- デバイスが S モードである。 Intune 管理拡張機能は、S モードで実行されているデバイスではサポートされません。 

デバイスが自動登録されているかどうかを確認するには、次の手順を実行します。

  1. **[設定]**  >  **[アカウント]**  >  **[職場または学校にアクセスする]** の順に移動します。
  2. 参加済みアカウントを選択し、 **[情報]** します。
  3. **[Advanced Diagnostic Report]\(高度な診断レポート\)** で、 **[レポートの作成]** を選択します。
  4. Web ブラウザーで、`MDMDiagReport` を開きます。
  5. **MDMDeviceWithAAD** プロパティを探します。 プロパティが存在する場合は、デバイスが自動登録されています。 プロパティが存在しない場合、デバイスは自動登録されません。

「[Windows 10 の自動登録を有効にする](windows-enroll.md#enable-windows-10-automatic-enrollment)」には、Intune で自動登録を構成するための手順が含まれています。

### <a name="issue-powershell-scripts-do-not-run"></a>問題:PowerShell スクリプトが実行されない

**考えられる解決策**:

- PowerShell スクリプトは、サインインのたびには実行されません。 次の場合に実行されます。

  - スクリプトがデバイスに割り当てられるとき
  - スクリプトを変更し、アップロードし、ユーザーまたはデバイスにそのスクリプトを割り当てるとき
  
    > [!TIP]
    > **Microsoft Intune 管理拡張機能**はサービス アプリ (services.msc) に表示されているその他のサービスと同様、デバイスで実行されるサービスです。 デバイスが再起動した後、このサービスも再開する可能性があります。Intune サービスで割り当てられている PowerShell スクリプトがないかを確認してください。 **Microsoft Intune 管理拡張機能**サービスが手動に設定されている場合は、デバイスの再起動後にサービスが再開しない可能性があります。

- 必ずデバイスを [Azure AD に参加](https://docs.microsoft.com/azure/active-directory/user-help/user-help-join-device-on-network)させます。 職場や組織にのみ参加しているデバイス ([Azure AD に登録されている](https://docs.microsoft.com/azure/active-directory/user-help/user-help-register-device-on-network)) はスクリプトを受信しません。
- Intune 管理拡張機能クライアントは、1 時間に 1 回、Intune でスクリプトまたはポリシーに変更があったかどうかを確認します。
- Intune 管理拡張機能が `%ProgramFiles(x86)%\Microsoft Intune Management Extension` にダウンロードされていることを確認します。
- Surface Hub または S モードの Windows 10 ではスクリプトは実行しません。
- ログでエラーを確認します。 「[Intune 管理拡張機能のログ](#intune-management-extension-logs)」 (この記事内) を参照してください。
- アクセス許可の問題の可能性がある場合は、PowerShell スクリプトのプロパティが `Run this script using the logged on credentials` に設定されていることを確認します。 また、サインインしているユーザーがスクリプトを実行するための適切なアクセス許可を持っていることも確認します。

- スクリプトに関する問題を分離するには、次の操作を行います。

  - デバイスの PowerShell の実行構成を確認します。 [PowerShell の実行ポリシー](https://docs.microsoft.com/powershell/module/microsoft.powershell.security/set-executionpolicy?view=powershell-6)について、ガイダンスを参照してください。
  - Intune 管理拡張機能を使用するサンプル スクリプトを実行します。 たとえば、`C:\Scripts` ディレクトリを作成し、すべてのユーザーにフル コントロールを付与します。 以下のスクリプトを実行します。

    ```powershell
    write-output "Script worked" | out-file c:\Scripts\output.txt
    ```

    成功すると、output.txt が作成されて、"Script worked" というテキストが含まれるはずです。

  - Intune なしでスクリプトの実行をテストするには、[psexec ツール](https://docs.microsoft.com/sysinternals/downloads/psexec)をローカル環境で使用し、システム アカウントでスクリプトを実行します。

    `psexec -i -s`  
    
  - スクリプトによって成功が報告されても、実際には成功していなかった場合は、ウイルス対策サービスによって AgentExecutor がサンドボックス化されている可能性があります。 次のスクリプトでは、常に Intune のエラーが報告されます。 テストとして、次のスクリプトを使用できます。
  
    ```powershell
    Write-Error -Message "Forced Fail" -Category OperationStopped
    mkdir "c:\temp" 
    echo "Forced Fail" | out-file c:\temp\Fail.txt
    ```

    スクリプトで成功が報告された場合は、`AgentExecutor.log` を参照してエラー出力を確認します。 スクリプトを実行する場合、長さは 2 より大きくする必要があります。

  - .error ファイルと .output ファイルをキャプチャするには、次のスニペットを使用して、AgentExecutor を通じて PSx86(`C:\Windows\SysWOW64\WindowsPowerShell\v1.0`) にスクリプトを実行します。 これにより、確認のためのログが保持されます。 Intune 管理拡張機能では、スクリプトの実行後にログがクリーンアップされることに注意してください。
  
    ```powershell
    $scriptPath = read-host "Enter the path to the script file to execute"
    $logFolder = read-host "Enter the path to a folder to output the logs to"
    $outputPath = $logFolder+"\output.output"
    $errorPath =  $logFolder+"\error.error"
    $timeoutPath =  $logFolder+"\timeout.timeout"
    $timeoutVal = 60000 
    $PSFolder = "C:\Windows\SysWOW64\WindowsPowerShell\v1.0"
    $AgentExec = "C:\Program Files (x86)\Microsoft Intune Management Extension\agentexecutor.exe"
    &$AgentExec -powershell  $scriptPath $outputPath $errorPath $timeoutPath $timeoutVal $PSFolder 0 0
    ```

## <a name="next-steps"></a>次の手順

プロファイルを[監視](device-profile-monitor.md)して[トラブルシューティング](device-profile-troubleshoot.md)します。
