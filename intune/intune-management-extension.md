---
title: Windows 10 デバイスに向けて Microsoft Intune で PowerShell スクリプトを追加する - Azure | Microsoft Docs
description: Microsoft Intune で Windows 10 デバイスに対して、PowerShell スクリプトの追加、Azure Active Directory グループへのスクリプト ポリシーの割り当て、レポートを使用したスクリプトの監視、スクリプトを削除する手順の確認を行います。 一般的な問題とその解決策についても説明します。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/03/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 768b6f08-3eff-4551-b139-095b3cfd1f89
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 444fd63f8c582d35891dfa5aedb9eadd6626e541
ms.sourcegitcommit: 4bd992da609b8bcc85edc2d64fe8128546aa4617
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2019
ms.locfileid: "55303397"
---
# <a name="manage-powershell-scripts-in-intune-for-windows-10-devices"></a>Windows 10 デバイスの Intune で PowerShell スクリプトを管理する

Windows 10 デバイスで実行するために Intune に PowerShell スクリプトをアップロードするには、Intune 管理拡張機能を使用します。 管理拡張機能は Windows 10 モバイル デバイス管理 (MDM) を拡張するもので、最新の管理に簡単に移行できます。

## <a name="moving-to-modern-management"></a>最新の管理への移行

エンドユーザーのコンピューティングはデジタル変換を経ています。 従来の IT 担当者は、単一のデバイス プラットフォーム、企業所有のデバイス、オフィスで働くユーザー、および手動で事後対応型の多様な IT プロセスに重点を置きます。 最近の職場では、ユーザーと企業の両方が所有する多数のプラットフォームが使用され、ユーザーがどこからでも作業できるようにして、自動化された事前対応型の IT プロセスを提供しています。

Microsoft Intune などの MDM サービスでは、Windows 10 を実行するモバイル デバイスとデスクトップ デバイスを管理できます。 組み込みの Windows 10 管理クライアントは、Intune と通信してエンタープライズ管理タスクを実行します。 高度なデバイスの構成、トラブルシューティング、Windows 10 MDM では現在使用できないレガシ Win32 アプリ管理など、必要になる場合があるタスクがいくつかあります。 このような機能のために、Windows 10 デバイスで Intune ソフトウェア クライアントを実行することができます。 「[Windows PC のコンピューターとしての管理とモバイル デバイスとしての管理の比較](pc-management-comparison.md)」は優れたリソースです。

Intune 管理拡張機能は、Windows 10 MDM の標準機能を補完するものです。 PowerShell スクリプトを作成して、Windows 10 デバイスで実行することができます。 たとえば、レガシ Win32 アプリをインストールする PowerShell スクリプトを作成し、スクリプトを Intune にアップロードし、スクリプトを Azure Active Directory (AD) グループに割り当てて、スクリプトを実行することができます。 スクリプトの実行状態を最初から完了まで監視できます。

## <a name="prerequisites"></a>必要条件

Intune 管理拡張機能には次の前提条件があります。

- デバイスは Azure AD に参加するか登録されている必要があり、Azure AD は [Intune に自動登録する](windows-enroll.md#enable-windows-10-automatic-enrollment)ように構成されている必要があります。 Intune 管理拡張機能では、Azure AD 参加済み、ハイブリッド ドメイン参加済み、および共同管理登録済みの Windows デバイスがサポートされます。
- デバイスは Windows 10 バージョン 1607 以降を実行している必要があります。
- PowerShell スクリプトまたは Win32 アプリをユーザーまたはデバイスのセキュリティ グループに展開すると、Intune 管理拡張機能エージェントがインストールされます。

## <a name="create-a-powershell-script-policy"></a>PowerShell スクリプト ポリシーを作成する 

1. [Azure portal](https://portal.azure.com) で、**[すべてのサービス]** を選択し、**Intune** でフィルター処理して、**Microsoft Intune** を選びます。
2. **[デバイス構成]** > **[PowerShell スクリプト]** > **[追加]** の順に選択します。
3. PowerShell スクリプトの**名前**と**説明**を入力します。 **[スクリプトの場所]** で、PowerShell スクリプトを参照します。 スクリプトはサイズが 200 KB (ASCII) または 100 KB (Unicode) 未満である必要があります。
4. **[構成]** を選択します。 次に、デバイスでのスクリプトの実行にユーザーの資格情報を使用する (**[はい]**) を選択するか、またはシステム コンテキストを使用する (**[いいえ]**) を選択します。 既定で、スクリプトはシステム コンテキストで実行されます。 システム コンテキストでスクリプトを実行する必要がある場合以外は、**[はい]** を選択してください。 
  ![[PowerShell スクリプトの追加] ウィンドウ](./media/mgmt-extension-add-script.png)
5. 信頼された発行者がスクリプトに署名する必要がある (**[はい]**) かどうかを選択します。 既定で、スクリプトに署名する要件はありません。 
6. **[OK]** を選択してから **[作成]** を選択し、スクリプトを保存します。

## <a name="assign-a-powershell-script-policy"></a>PowerShell スクリプト ポリシーを割り当てる

1. **[PowerShell スクリプト]** で、割り当てるスクリプトを選択し、**[管理]** > **[割り当て]** を選択します。

    ![[PowerShell スクリプトの追加] ウィンドウ](./media/mgmt-extension-assignments.png)

2. **[グループの選択]** を選択して、使用できる Azure AD グループの一覧を表示します。 
3. スクリプトを受信するデバイスを持つユーザーが属する 1 つまたは複数のグループを選択します。 **[選択]** をクリックして、選択したグループにポリシーを割り当てます。

> [!NOTE]
> - エンド ユーザーは、PowerShell スクリプトを実行するためにデバイスにサインインする必要はありません。
> - Intune 内の PowerShell スクリプトは、Azure AD デバイスのセキュリティ グループを対象にすることができます。
> - Intune 内の PowerShell スクリプトは、Azure AD ユーザーのセキュリティ グループを対象にすることができます。

Intune 管理拡張機能クライアントは、1 時間に 1 回 Intune を確認します。 ポリシーを Azure AD グループに割り当てた後に、PowerShell スクリプトを実行すると、実行結果がレポートされます。

## <a name="monitor-run-status-for-powershell-scripts"></a>PowerShell スクリプトの実行ステータスを監視する

Azure Portal でユーザーとデバイスの PowerShell スクリプトの実行状態を監視できます。

**[PowerShell スクリプト]** で、監視するスクリプトを選択し、**[監視]** を選択し、次のいずれかのレポートを選択します。

- **デバイスの状態**
- **ユーザーの状態**

## <a name="troubleshoot-powershell-scripts"></a>PowerShell スクリプトをトラブルシューティングする

クライアント コンピューター上のエージェント ログは、一般的に `\ProgramData\Microsoft\IntuneManagementExtension\Logs` にあります。 [CMTrace.exe](https://docs.microsoft.com/sccm/core/support/tools) を使用してこれらのログ ファイルを表示できます。 

![エージェント ログのスクリーンショット](./media/apps-win32-app-10.png)  

## <a name="delete-a-powershell-script"></a>Powershell スクリプトを削除する

**PowerShell スクリプト**で、スクリプトを右クリックし、**[削除]** を選択します。

## <a name="common-issues-and-resolutions"></a>よくある問題と解決策

PowerShell スクリプトは、サインインのたびには実行されません。 再起動の後、または **Microsoft Intune 管理拡張機能**サービスが再起動された場合にのみ、実行されます。 Intune 管理拡張機能クライアントは、1 時間に 1 回、Intune でスクリプトまたはポリシーに変更があったかどうかを確認します。

#### <a name="issue-intune-management-extension-doesnt-download"></a>問題:Intune 管理拡張機能をダウンロードできない

**考えられる解決策**:

- デバイスが Azure AD に自動登録されることを確認します。 確認するには、デバイスで次のようにします。 

  1. **[設定]** > **[アカウント]** > **[職場または学校にアクセスする]** の順に移動します。
  2. 参加済みアカウントを選択し、**[情報]** します。
  3. **[Advanced Diagnostic Report]\(高度な診断レポート\)** で、**[レポートの作成]** を選択します。
  4. `MDMDiagReport` を Web ブラウザーで開き、**[Enrolled configuration sources]\(登録済み構成ソース\)** セクションに移動します。
  5. **MDMDeviceWithAAD** プロパティを探します。 このプロパティが存在しない場合、お使いのデバイスは自動登録されません。

    手順については、「[Windows 10 の自動登録を有効にする](windows-enroll.md#enable-windows-10-automatic-enrollment)」をご覧ください。

#### <a name="issue-the-powershell-scripts-do-not-run"></a>問題:PowerShell スクリプトが実行されない

**考えられる解決策**:

- Intune 管理拡張機能が `%ProgramFiles(x86)%\Microsoft Intune Management Extension` にダウンロードされていることを確認します。
- Surface Hub 上ではスクリプトは実行しません。
- `\ProgramData\Microsoft\IntuneManagementExtension\Logs` のログでエラーを確認します。
- アクセス許可の問題の可能性がある場合は、PowerShell スクリプトのプロパティが `Run this script using the logged on credentials` に設定されていることを確認します。 また、サインインしているユーザーがスクリプトを実行するための適切なアクセス許可を持っていることも確認します。
- スクリプトに関する問題を分離するには、サンプル スクリプトを実行します。 たとえば、`C:\Scripts` ディレクトリを作成し、すべてのユーザーにフル コントロールを付与します。 以下のスクリプトを実行します。

  ```powershell
  write-output "Script worked" | out-file c:\Scripts\output.txt
  ```

  成功すると、output.txt が作成されて、"Script worked" というテキストが含まれるはずです。

- Intune なしでスクリプトの実行をテストするには、[psexec ツール](https://docs.microsoft.com/sysinternals/downloads/psexec)をローカル環境で使用し、システム コンテキストでスクリプトを実行します。

  `psexec -i -s`

## <a name="next-steps"></a>次の手順

プロファイルを[監視](device-profile-monitor.md)して[トラブルシューティング](device-profile-troubleshoot.md)します。
