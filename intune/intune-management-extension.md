---
title: Windows 10 デバイスに向けて Microsoft Intune で PowerShell スクリプトを追加する - Azure | Microsoft Docs
description: Microsoft Intune で Windows 10 デバイスに対して、PowerShell スクリプトの追加、Azure Active Directory グループへのスクリプト ポリシーの割り当て、レポートを使用したスクリプトの監視、スクリプトを削除する手順の確認を行います。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/30/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 768b6f08-3eff-4551-b139-095b3cfd1f89
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2046a928525e974eee5f63d772d46864b21f0267
ms.sourcegitcommit: 2061f7a442efc96c8afd5db764d11531563c7e39
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34583674"
---
# <a name="manage-powershell-scripts-in-intune-for-windows-10-devices"></a>Windows 10 デバイスの Intune で PowerShell スクリプトを管理する
Intune 管理拡張機能を使用すると、Windows 10 デバイスで実行されている Intune で PowerShell スクリプトをアップロードできます。 この管理拡張機能は Windows 10 モバイル デバイス管理 (MDM) 機能を補完するもので、最新の管理に簡単に移行できます。

## <a name="moving-to-modern-management"></a>最新の管理への移行
エンドユーザーのコンピューティングはデジタル変換を経ています。 従来の IT 担当者は、単一のデバイス プラットフォーム、企業所有のデバイス、オフィスで働くユーザー、および手動で事後対応型の多様な IT プロセスに重点を置きます。 一方、最近の職場では、ユーザーと企業の両方が所有する複数のデバイス プラットフォームに対応し、ユーザーがどこからでも作業できるようにして、自動化された事前対応型の IT プロセスを提供しています。 

Microsoft Intune などの MDM サービスは、MDM プロトコルを使用して Windows 10 デバイスを管理できます。 組み込みの Windows 10 管理クライアントは、Intune と通信してエンタープライズ管理タスクを実行できます。 そのため、Windows 10 デバイスで最新の管理に移行できます。 ただし、高度なデバイスの構成、トラブルシューティング、Windows 10 MDM では現在使用できないレガシ Win32 アプリ管理など、特定の機能が必要な場合があります。 このような機能のために、Windows 10 デバイスで Intune ソフトウェア クライアントを実行することができます。 その場合は、Windows 10 MDM が提供する新しい機能を使用できません。 [Intune ソフトウェア クライアントと Windows 10 MDM の違いを比較してください](https://docs.microsoft.com/intune-classic/deploy-use/pc-management-comparison)。

Intune 管理拡張機能は、インボックス Windows 10 MDM 機能を補完するものです。 必要な機能を提供する PowerShell スクリプトを作成して、Windows 10 デバイスで実行することができます。 たとえば、Windows 10 デバイスにレガシ Win32 アプリをインストールする PowerShell スクリプトを作成し、スクリプトを Intune にアップロードし、スクリプトを Azure Active Directory (AD) グループに割り当て、Windows 10 デバイスでスクリプトを実行することができます。 Windows 10 デバイスでスクリプトの実行状態を最初から完了まで監視できます。

## <a name="prerequisites"></a>必要条件
Intune 管理拡張機能には次の前提条件があります。
- デバイスを Azure AD に参加させる必要があります。 これには、ハイブリッド AD 参加済みデバイスは含まれません。
- デバイスは Windows 10 バージョン 1607 以降を実行している必要があります。
- MDM の自動登録が [Azure AD で有効](https://docs.microsoft.com/intune/windows-enroll#enable-windows-10-automatic-enrollment)になっており、デバイスが Intune に自動登録される必要があります。

## <a name="create-a-powershell-script-policy"></a>PowerShell スクリプト ポリシーを作成する 
1. [Azure ポータル](https://portal.azure.com)にサインインします。
2. **[すべてのサービス]** を選択し、**[Intune]** をフィルターとして適用し、**[Microsoft Intune]** を選択します。
3. **[デバイス構成]** > **[PowerShell スクリプト]** > **[追加]** の順に選択します。
4. PowerShell スクリプトの**名前**と**説明**を入力します。 **[スクリプトの場所]** で、PowerShell スクリプトを参照します。 スクリプトのサイズは、200 KB (ASCII) または 100 KB (Unicode) 未満とする必要があります。
5. **[構成]** を選択します。 次に、デバイスでのスクリプトの実行にユーザーの資格情報を使用する (**[はい]**) を選択するか、またはシステム コンテキストを使用する (**[いいえ]**) を選択します。 既定で、スクリプトはシステム コンテキストで実行されます。 システム コンテキストでスクリプトを実行する必要がある場合以外は、**[はい]** を選択してください。 
  ![[PowerShell スクリプトの追加] ウィンドウ](./media/mgmt-extension-add-script.png)
6. 信頼された発行者がスクリプトに署名する必要がある (**[はい]**) かどうかを選択します。 既定で、スクリプトに署名する要件はありません。 
7. **[OK]** を選択してから **[作成]** を選択し、スクリプトを保存します。

## <a name="assign-a-powershell-script-policy"></a>PowerShell スクリプト ポリシーを割り当てる
1. **[PowerShell スクリプト]** で、割り当てるスクリプトを選択し、**[管理]** > **[割り当て]** を選択します。
  ![[PowerShell スクリプトの追加] ウィンドウ](./media/mgmt-extension-assignments.png)
 
2. **[グループの選択]** を選択して、使用できる Azure AD グループの一覧を表示します。 
3. スクリプトを受信するデバイスを持つユーザーが属する 1 つまたは複数のグループを選択します。 **[選択]** をクリックして、選択したグループにポリシーを割り当てます。

Intune 管理拡張機能は、1 時間に 1 回 Intune と同期します。 ポリシーを Azure AD グループに割り当てた後に、PowerShell スクリプトを実行すると、実行結果がレポートされます。 
 
## <a name="monitor-run-status-for-powershell-scripts"></a>PowerShell スクリプトの実行ステータスを監視する
Azure Portal でユーザーとデバイスの PowerShell スクリプトの実行状態を監視できます。

**[PowerShell スクリプト]** で、監視するスクリプトを選択し、**[監視]** を選択し、次のいずれかのレポートを選択します。
   - **デバイスの状態**
   - **ユーザーの状態**

## <a name="delete-a-powershell-script"></a>Powershell スクリプトを削除する
**PowerShell スクリプト**で、スクリプトを右クリックし、**[削除]** を選択します。
