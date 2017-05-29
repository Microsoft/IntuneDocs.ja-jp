---
title: "クライアント ソフトウェアを使用して PC を管理する |Microsoft Docs"
description: "Intune クライアント ソフトウェアをインストールして Windows PC を管理します。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 03/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b8d22fe-c318-4796-b760-44f1ccf34312
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 6bd4e3315fd27201e8005b1053fa6e15bf2c21b5
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017


---

# <a name="manage-windows-pcs-as-computers-via-intune-software-client"></a>Intune ソフトウェア クライアントを使用して Windows PC をコンピューターとして管理する

Intune は、モバイル デバイス管理するための組織向けの包括的なソリューションを提供します。 Intune は、Windows 10 オペレーティング システムに組み込まれている最新のデバイス管理機能を使用して、モバイル デバイスとして Windows PC を管理できます。 組織の管理ニーズを満たすため、Intune は、Intune ソフトウェア クライアントでコンピューターとして Windows PC を管理することもできます。 この管理方法は、従来の Windows オペレーティング システムでのコンピューター管理機能を使います。

Intune ソフトウェア クライアントは、モバイル デバイスとして管理することができない Windows 7 などの従来のオペレーティング システムを搭載する Windows PC に最も適しています。 Intune ソフトウェア クライアントは、グループ ポリシーのような管理機能を使って、クラウドから PC を管理します。

Intune は、ソフトウェア クライアントを使って、最大 7,000 台の Windows PC をコンピューターとして管理できます。 大規模な展開の場合は、モバイル デバイスとして Windows 10 PC を管理します。 Intune の各リリースおよび Windows 10 の更新プログラムには、モバイル デバイス管理アーキテクチャに基づく管理機能が含まれます。 モバイル デバイスとして管理される Windows 10 に組織を移行することを強くお勧めします。


> [!NOTE]
> Windows 8.1 以降のデバイスは、Intune クライアント ソフトウェアを使って PC として、またはモバイル デバイスとして、管理できます。 同じデバイスで両方の方法を使うことはできません。 Intune クライアント ソフトウェアで PC を管理することを決定する前に、慎重に検討してください。 このトピックでは、Intune クライアント ソフトウェアを実行してデバイスを PC として管理する方法についてのみ説明します。

## <a name="requirements-for-intune-pc-client-management"></a>Intune PC クライアント管理の要件

**ハードウェア**: 次に、Intune クライアント ソフトウェアをインストールするハードウェアの最小要件を示します。

|要件|説明|
|---------------|--------------------|
|ネットワーク|クライアントでは、PC がインターネット接続できる必要があります。|
|プロセッサとメモリ|PC のオペレーティング システムに対するプロセッサ要件と RAM 要件を参照してください。|
|ディスク領域|クライアント ソフトウェアをインストールする前に、200 MB の空きディスク領域が必要です。|

**ソフトウェア**: 次に、クライアント ソフトウェアをインストールするソフトウェアの要件を示します。

|要件|説明|
|---------------|--------------------|
|オペレーティング システム | Windows Vista 以降を実行している Windows デバイスであること。 </br></br>**Home エディションのバージョンはサポートされていません。**|
|管理者のアクセス許可|クライアント ソフトウェアをインストールするアカウントは、そのデバイスのローカル管理者のアクセス許可を持っている必要があります。|
|Windows インストーラー 3.1|PC には Windows インストーラー 3.1 以降がインストールされている必要があります。<br /><br />PC で Windows インストーラーのバージョンを確認するには<br /><br />  PC で、**%windir%\System32\msiexec.exe** を右クリックし、**[プロパティ]** をクリックします。<br /><br />最新バージョンの Windows インストーラーは、Microsoft Developer Network Web サイトの「 [Windows Installer Redistributables (Windows インストーラー再頒布可能パッケージ)](http://go.microsoft.com/fwlink/?LinkID=234258) 」からダウンロードできます。|
|互換性のないクライアント ソフトウェアを削除する|Intune クライアント ソフトウェアをインストールする前に、その PC から Configuration Manager、Operations Manager、Operations Management Suite、および Service Manager のクライアント ソフトウェアをアンインストールします。|

## <a name="deploying-the-intune-software-client"></a>Intune ソフトウェア クライアントの展開
Intune 管理者は、さまざまな方法でユーザーが Intune ソフトウェア クライアントを利用できるようにすることができます。 方法については、「[Windows PC に Intune ソフトウェア クライアントをインストールする](install-the-windows-pc-client-with-microsoft-intune.md)」をご覧ください。

## <a name="computer-management-capabilities-with-the-intune-client-software"></a>Intune クライアント ソフトウェアを使ったコンピューター管理機能
ほとんどのシナリオでは、デバイスを Microsoft Intune に登録します。そうすることで、さらに多くの機能を使用できるようになります。 ただし、PC の管理には、Intune ソフトウェアを使用することもできます。このソフトウェアでは、次の機能が利用できます。

-   **[ソフトウェア更新プログラムの管理](/intune-classic/deploy-use/keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune)** - PC を最新の状態に保ち、更新プログラムを適用する時間を決定できます。

-   **[Windows ファイアウォールのポリシー](/intune-classic/deploy-use/help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune)** - この機能により、会社で使用する PC に、非アクティブまたは適切でない構成の Windows ファイアウォールが存在しないようにします。

-   **[マルウェア対策](/intune-classic/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)** - Intune には、マルウェアから PC を保護するのに役立つ Endpoint Protection が含まれています。

-   **[リモート アシスタンス](/intune-classic/deploy-use/common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client#request-and-provide-remote-assistance-to-windows-pcs-that-use-the-intune-client-software )** - ユーザーは Intune を使用して、IT サポート スタッフに連絡できます。IT サポート スタッフは、Intune に含まれているリモート デスクトップ機能を使用してサポートを提供できます (TeamViewer ソフトウェアが必要)。

-   **[ソフトウェア ライセンス管理](/intune-classic/deploy-use/manage-license-agreements-for-windows-pc-software-in-microsoft-intune)** - 使用可能なソフトウェア ライセンスの数と、そのうちの使用中のライセンスの数を追跡します。
-   **[アプリの展開](/intune-classic/deploy-use/add-apps-for-windows-pcs-in-microsoft-intune)** - 管理対象の PC にソフトウェアを展開します。 ソフトウェア クライアントを使用して PC を管理する場合、一部のアプリ管理機能は利用できません。

<!-- - **Compliance settings reporting** -->

## <a name="policies-and-app-deployments-for-the-intune-software-client"></a>Intune ソフトウェア クライアントに対するポリシーとアプリの展開

Intune クライアント ソフトウェアでは、ソフトウェアの更新、Windows ファイアウォール、および Endpoint Protection を管理することで [PC の保護に役立つ管理機能](policies-to-protect-windows-pcs-in-microsoft-intune.md)がサポートされますが、Intune クライアント ソフトウェアで管理される PC を、モバイル デバイス管理に特化した **Windows** ポリシー設定などの他の Intune ポリシーの対象とすることはできません。

Intune クライアント ソフトウェアを使って Windows PC を管理する場合は、**[コンピューター管理]** セクションに表示されているポリシーのみを使うことができます。

Intune では、Windows Server における Active Directory ドメイン サービス (AD DS) グループ ポリシー オブジェクト (GPO) と似た方法で、ポリシーを使って Windows PC を管理します。Active Directory ドメインに参加しているコンピューターを Intune で管理する場合は、組織で使われている他の GPO と Intune のポリシーが競合しないようにしてください。 詳しくは、「[初心者向けのグループ ポリシー](https://technet.microsoft.com/library/hh147307.aspx)」をご覧ください。

  ![新しい Windows PC ポリシーのテンプレートの選択](../media/select-template-for-pc-policy.png)

アプリを展開するときは、Windows インストーラー (.exe、.msi) のみを使用できます。

  ![PC クライアント ソフトウェア ファイルのプラットフォームと場所を選択します](../media/select-platform-of-software-files-for-pc-agent.png)

## <a name="common-tasks-for-windows-pcs"></a>Windows PC でよく行うタスク

Intune 管理コンソールを使って、クライアントがインストールされている Windows PC で他の一般的なコンピューター管理タスクを実行できます。
- [ポリシーを使用して PC 管理を簡略化する](use-policies-to-simplify-windows-pc-management.md) - Intune の**コンピューター管理**ポリシーについて説明し、Microsoft Intune Center の設定の一覧を示します。

- [View hardware and software inventory for Windows PCs](view-hardware-and-software-inventory-for-windows-pcs-in-microsoft-intune.md) (Windows PC のハードウェアおよびソフトウェア インベントリを表示する) - PC のハードウェア性能および PC にインストールされているソフトウェアに関する情報を一覧表示するレポートを作成する方法について説明します。 また、PC インベントリを更新して最新の状態にする方法についても説明します。
- [Retire a Windows PC](retire-a-windows-pc-with-microsoft-intune.md) (Windows PC をインベントリから削除する) - Windows PC をインベントリから削除する手順を示し、PC を削除すると起きることについて説明します。
- [Windows PC に対するユーザー デバイスの関連付けを管理する](manage-user-device-linking-for-windows-pcs-with-microsoft-intune.md) - ユーザーにソフトウェアを展開する前に PC にユーザーを関連付ける必要がある状況と方法について説明します。
- [Windows PC のリモート アシスタンス要求と提供](request-and-provide-remote-assistance-for-windows-pcs-in-microsoft-intune.md) - Intune PC ユーザーがリモート アシスタンスのヘルプを入手する方法、および前提条件と TeamViewer のセットアップについて説明します。

上記のタスクについて詳しくは、[一般的なコンピューター管理タスクに関するページ](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)をご覧ください。

## <a name="management-limitations-of-the-intune-client-software"></a>Intune クライアント ソフトウェアの管理の制限

PC をモバイル デバイスとして管理するために使うことができる一部の管理オプションは、Intune クライアント ソフトウェアで管理されている PC には使えません。

-   フル ワイプ (選択的ワイプは使用可能)
-   条件付きアクセス

また、**[更新]**、**[保護]**、**[ライセンス]** などの特定のセクションは、Intune クライアント ソフトウェアを使ってデバイスを登録した場合にのみ Intune 管理コンソールに表示されることにも注意してください。

  ![PC クライアントにのみ表示される管理コンソールの項目](../media/admin-console-settings-only-for-pc-agent.png)

## <a name="help-with-troubleshooting"></a>トラブルシューティングに関するヘルプ

Intune のクライアント ソフトウェアは通常、ユーザー操作やトラブルシューティングをほとんど必要とせずに、バック グラウンドで実行されます。 PC 管理の問題を解決する必要がある場合は、ログを確認できます。 Intune クライアント ソフトウェアおよび対応するログは、%Program Files%\Microsoft\OnlineManagement ディレクトリの下にインストールされます。

また、「[Microsoft Intune でのクライアント セットアップのトラブルシューティング](/intune-classic/troubleshoot/troubleshoot-client-setup-in-microsoft-intune)」で、発生する可能性のある問題と、解決策または回避策を確認することもできます。

