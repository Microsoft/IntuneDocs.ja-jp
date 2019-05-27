---
title: Microsoft Intune で Windows 10 デバイスに PowerShell スクリプトを追加する - Azure | Microsoft Docs
description: Microsoft Intune で Windows 10 デバイスに対して、PowerShell スクリプトの作成および実行、Azure Active Directory グループへのスクリプト ポリシーの割り当て、レポートを使用したスクリプトの監視、追加したスクリプトの削除を行います。 一般的な問題とその解決策についても説明します。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/14/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 768b6f08-3eff-4551-b139-095b3cfd1f89
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6b7ea047daca5dad327b431986840a59074614d1
ms.sourcegitcommit: f8bbd9bac2016a77f36461bec260f716e2155b4a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/16/2019
ms.locfileid: "65732634"
---
# <a name="use-powershell-scripts-on-windows-10-devices-in-intune"></a>Intune で Windows 10 デバイスに対して PowerShell スクリプトを使用する

Windows 10 デバイスで実行するために Intune に PowerShell スクリプトをアップロードするには、Microsoft Intune 管理拡張機能を使用します。 管理拡張機能は Windows 10 モバイル デバイス管理 (MDM) を拡張するもので、最新の管理に簡単に移行できます。

この機能は、以下に適用されます。

- Windows 10 以降

## <a name="move-to-modern-management"></a>最新の管理への移行

エンドユーザーのコンピューティングはデジタル変換を経ています。 従来の IT 担当者は、単一のデバイス プラットフォーム、企業所有のデバイス、オフィスで働くユーザー、および手動で事後対応型の多様な IT プロセスに重点を置きます。 最近の職場では、ユーザーと企業の両方が所有する多数のプラットフォームが使用され、ユーザーがどこからでも作業できるようにして、自動化された事前対応型の IT プロセスを提供しています。

Microsoft Intune などの MDM サービスでは、Windows 10 を実行するモバイル デバイスとデスクトップ デバイスを管理できます。 組み込みの Windows 10 管理クライアントは、Intune と通信してエンタープライズ管理タスクを実行します。 高度なデバイス構成やトラブルシューティングなど、必要な場合があるタスクがいくつかあります。 Win32 アプリの管理の場合、ご自分の Windows 10 デバイス上の [Win32 アプリの管理](apps-win32-app-management.md)機能を使えます。

Intune 管理拡張機能は、Windows 10 MDM の標準機能を補完するものです。 PowerShell スクリプトを作成して、Windows 10 デバイスで実行することができます。 たとえば、高度なデバイス構成を行う PowerShell スクリプトを作成し、スクリプトを Intune にアップロードして、スクリプトを Azure Active Directory (AD) グループに割り当て、スクリプトを実行することができます。 スクリプトの実行状態を最初から完了まで監視できます。

## <a name="prerequisites"></a>必要条件

Intune 管理拡張機能には次の前提条件があります。

- デバイスは Azure AD に参加しているか登録されている必要があり、さらに Azure AD と Intune は [自動登録](quickstart-setup-auto-enrollment.md)に構成されている必要があります。 Intune 管理拡張機能では、Azure AD 参加済み、ハイブリッド Azure AD ドメイン参加済み、および共同管理登録済みの Windows デバイスがサポートされます。
- デバイスは Windows 10 バージョン 1607 以降を実行している必要があります。
- PowerShell スクリプトまたは Win32 アプリをユーザーまたはデバイスのセキュリティ グループに展開すると、Intune 管理拡張機能エージェントがインストールされます。

## <a name="create-a-script-policy"></a>スクリプト ポリシーを作成する 

1. [Azure portal](https://portal.azure.com) で、**[すべてのサービス]** を選択し、**Intune** でフィルター処理して、**[Intune]** を選択します。
2. **[デバイス構成]** > **[PowerShell スクリプト]** > **[追加]** の順に選択します。
3. 次のプロパティを入力します。
    - **名前**: PowerShell スクリプトの名前を入力します。 
    - **説明**:PowerShell スクリプトの説明を入力します。 この設定は省略可能ですが、推奨されます。 
    - **スクリプトの場所**: PowerShell スクリプトを参照します。 スクリプトは 200 KB (ASCII) 未満とする必要があります。
4. **[構成]** を選択し、次のプロパティを入力します。
    - **このスクリプトをログオンしたユーザーの資格情報を使用して実行する**: **[はい]** を選択すると、デバイス上でユーザーの資格情報を使用してスクリプトが実行されます。 **[いいえ]** (既定) を選択すると、システム コンテキストでスクリプトが実行されます。 管理者の多くは、**[はい]** を選択します。 システム コンテキストでスクリプトを実行する必要がある場合は、**[いいえ]** を選択します。
    - **[スクリプト署名チェックを強制]**: 信頼された発行者がスクリプトに署名する必要がある場合は、**[はい]** を選択します。 スクリプトに署名する要件がない場合は、**[いいえ]** (既定) を選択します。 
    - **64 ビットの PowerShell ホストでスクリプトを実行する**: **[はい]** を選択すると、64 ビット クライアント アーキテクチャ上の 64 ビット PowerShell (PS) ホストでスクリプトが実行されます。 **[いいえ]** (既定値) を選択すると、32 ビット PowerShell ホストでスクリプトが実行されます。

      **[はい]** または **[いいえ]** に設定する場合は、次の表を使用して新しいポリシー動作と既存のポリシー動作を確認してください。

      | 64 ビットの PS ホストでスクリプトを実行する | クライアント アーキテクチャ | 新しい PS スクリプト | 既存のポリシー PS スクリプト |
      | --- | --- | --- | --- | 
      | [いいえ] | 32 ビット  | 32 ビットの PS ホストがサポートされる | 32 ビットおよび 64 ビットのアーキテクチャで動作する 32 ビット PS ホストでのみ実行されます。 |
      | はい | 64 ビット | 64 ビット アーキテクチャ用の 64 ビットの PS ホストでスクリプトが実行されます。 32 ビット上で実行した場合、スクリプトは 32 ビットの PS ホストで実行されます。 | 32 ビットの PS ホストでスクリプトが実行されます。 この設定が 64 ビットに変更されると、スクリプトは 64 ビットの PS ホストで開き (実行されない)、スクリプトから結果がレポートされます。 32 ビット上で実行した場合、スクリプトは 32 ビットの PS ホストで実行されます。 |

    ![Microsoft Intune で PowerShell スクリプトを追加および使用する](./media/mgmt-extension-add-script.png)
5. **[OK]** > **[作成]** の順に選択してスクリプトを保存します。

> [!NOTE]
> PowerShell スクリプトがユーザー コンテキストに設定され、デバイスのエンド ユーザーが管理特権を持っている場合、スクリプトは (既定で) 管理特権で実行されます。

## <a name="assign-the-policy"></a>ポリシーを割り当てる

1. **[PowerShell スクリプト]** で、割り当てるスクリプトを選択し、**[管理]** > **[割り当て]** を選択します。

    ![Microsoft Intune で、PowerShell スクリプトをデバイス グループに割り当てる、またはデプロイする](./media/mgmt-extension-assignments.png)

2. **[グループの選択]** を選択して、使用できる Azure AD グループの一覧を表示します。 
3. スクリプトを受信するデバイスを持つユーザーが属する 1 つまたは複数のグループを選択します。 **[選択]** をクリックして、選択したグループにポリシーを割り当てます。

> [!NOTE]
> - エンド ユーザーは、PowerShell スクリプトを実行するためにデバイスにサインインする必要はありません。
> - Intune 内の PowerShell スクリプトは、Azure AD デバイスのセキュリティ グループを対象にすることができます。
> - Intune 内の PowerShell スクリプトは、Azure AD ユーザーのセキュリティ グループを対象にすることができます。

Intune 管理拡張機能のクライアントでは、1 時間ごとに、または Intune での再起動のたびに、新しいスクリプトまたは変更が存在しないかどうかが確認されます。 ポリシーを Azure AD グループに割り当てた後に、PowerShell スクリプトを実行すると、実行結果がレポートされます。 スクリプトは一度実行されると、スクリプトまたはポリシーに変更が発生するまで、再実行されません。

## <a name="monitor-run-status"></a>実行状態を監視する

Azure Portal でユーザーとデバイスの PowerShell スクリプトの実行状態を監視できます。

**[PowerShell スクリプト]** で、監視するスクリプトを選択し、**[監視]** を選択し、次のいずれかのレポートを選択します。

- **デバイスの状態**
- **ユーザーの状態**

## <a name="troubleshoot-scripts"></a>スクリプトのトラブルシューティング

クライアント コンピューター上のエージェント ログは、一般的に `\ProgramData\Microsoft\IntuneManagementExtension\Logs` にあります。 [CMTrace.exe](https://docs.microsoft.com/sccm/core/support/tools) を使用してこれらのログ ファイルを表示できます。 

![Microsoft Intune での cmtrace エージェント ログのスクリーンショットまたはサンプル](./media/apps-win32-app-10.png)  

## <a name="delete-a-script"></a>スクリプトを削除する

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

#### <a name="issue-powershell-scripts-do-not-run"></a>問題:PowerShell スクリプトが実行されない

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
