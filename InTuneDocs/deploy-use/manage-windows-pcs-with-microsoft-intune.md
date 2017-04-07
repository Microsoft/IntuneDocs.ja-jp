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
translationtype: Human Translation
ms.sourcegitcommit: c66226b7fc31f91669c4f4f0693ccbd7c679189f
ms.openlocfilehash: 74f2848dcd2863022dac44cf302b330a99cf1a55
ms.lasthandoff: 03/29/2017


---

# <a name="manage-windows-pcs-with-intune-pc-client-software"></a>Intune PC クライアント ソフトウェアを使用して Windows PC を管理する
[モバイル デバイスとしての Windows PC の登録](set-up-windows-device-management-with-microsoft-intune.md)は、Intune に Windows PC を登録する際の推奨される方法ですが、このトピックで説明するように、IT 管理者として Intune クライアント ソフトウェアをインストールすることによって Windows PC を登録して管理することもできます。 Intune ソフトウェア クライアントは、モバイル デバイスとしての登録がサポートされていません。

Intune では、Windows Server における Active Directory Domain Services (AD DS) グループ ポリシー オブジェクト (GPO) と似た方法でポリシーを使用して Windows PC を管理します。 Active Directory ドメインに参加しているコンピューターを Intune で管理する場合は、[Intune のポリシーが組織で設定されているどの GPO とも競合しないようにしてください](resolve-gpo-and-microsoft-intune-policy-conflicts.md)。 GPO の詳細は、[ここ](https://technet.microsoft.com/library/hh147307.aspx)で確認できます。

## <a name="policies-and-app-deployments-for-the-intune-software-client"></a>Intune ソフトウェア クライアントに対するポリシーとアプリの展開

Intune クライアント ソフトウェアでは、ソフトウェアの更新、Windows ファイアウォール、および Endpoint Protection を管理することで [PC の保護に役立つ管理機能](policies-to-protect-windows-pcs-in-microsoft-intune.md)がサポートされますが、Intune クライアント ソフトウェアで管理される PC を、モバイル デバイス管理に特化した **Windows** ポリシー設定などの他の Intune ポリシーの対象とすることはできません。

Intune クライアント ソフトウェアを使って Windows PC を管理する場合は、**[コンピューター管理]** セクションに表示されているポリシーのみを使うことができます。

  ![新しい Windows PC ポリシーのテンプレートの選択](../media/select-template-for-pc-policy.png)

設定できるポリシーの詳細な説明については、次を参照してください。

- [Intune クライアント ソフトウェアを実行する Windows PC の保護に有用なポリシーを使用する](https://docs.microsoft.com/intune/deploy-use/policies-to-protect-windows-pcs-in-microsoft-intune)
- [Microsoft Intune でソフトウェア更新プログラムを使用して Windows PC を最新の状態に保つ](https://docs.microsoft.com/intune/deploy-use/keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune)
- [Microsoft Intune で Windows ファイアウォール ポリシーを使用して Windows PC を保護する](https://docs.microsoft.com/intune/deploy-use/help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune)
- [Microsoft Intune の Endpoint Protection を使用して Windows PC を保護する](https://docs.microsoft.com/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)

さらに、アプリを展開するときは、Windows インストーラー (.exe、.msi) のみを使用できます。

  ![PC クライアント ソフトウェア ファイルのプラットフォームと場所を選択します](../media/select-platform-of-software-files-for-pc-agent.png)

> [!NOTE]
> Windows 8.1 以降のデバイスは、Intune クライアント ソフトウェアを使って PC として、またはモバイル デバイス管理 (MDM) 機能を使ってモバイル デバイスとして、管理できます。 両方の方法を一緒に使うことはできません。そのため、Intune クライアント ソフトウェアを使って PC を管理する前に、どちらを選ぶかを慎重に検討してください。 このトピックでは、Intune クライアント ソフトウェアを実行してデバイスを PC として管理する方法についてのみ説明します。

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

## <a name="computer-management-capabilities-with-the-intune-client-software"></a>Intune クライアント ソフトウェアを使ったコンピューター管理機能

Intune クライアント ソフトウェアをインストールすると、以下の管理機能を使うことができます。

- [アプリケーション管理](deploy-apps-in-microsoft-intune.md)

- [リアルタイム監視と Endpoint Protection](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md) - Endpoint Protection は Windows Defender と同じものです。 Endpoint Protection は、Windows 7 および Windows 8 で利用できます。 Windows 10 以降では、製品名が Windows Defender に変更されています。

- [Windows ファイアウォールの設定の管理](help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md)、ハードウェアおよびソフトウェアのインベントリ、リモート コントロール (リモート アシスタンス要求を介して)

- [ソフトウェア更新設定](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md)

- コンプライアンス設定レポート

[更新]、[保護]、[ライセンス] などの特定のセクションは、Intune クライアント ソフトウェアを使ってデバイスを登録した場合にのみ Intune 管理コンソールに表示されます。

  ![PC クライアントにのみ表示される管理コンソールの項目](../media/admin-console-settings-only-for-pc-agent.png)

Intune 管理コンソールを使って、クライアントがインストールされている Windows PC で他の一般的なコンピューター管理タスクを実行することもできます。

-   管理対象コンピューターに関するハードウェアおよびソフトウェアのインベントリの表示
-   リモートからのコンピューターの再起動
-   コンピューターの使用を停止するための、クライアント ソフトウェアのアンインストールと、Intune による管理からの削除
-   特定の管理対象コンピューターへのユーザーの関連付け
-   リモート アシスタンス要求への応答

上記のタスクについて詳しくは、[一般的なコンピューター管理タスクに関するページ](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)をご覧ください。

## <a name="management-limitations-of-the-intune-client-software"></a>Intune クライアント ソフトウェアの管理の制限

PC をモバイル デバイスとして管理するために使うことができる一部の管理オプションは、Intune クライアント ソフトウェアで管理されている PC には使えません。

-   フル ワイプ (選択的ワイプは使用可能)

-   条件付きアクセス

## <a name="help-with-troubleshooting"></a>トラブルシューティングに関するヘルプ

Intune のクライアント ソフトウェアは通常、ユーザー操作やトラブルシューティングをほとんど必要とせずに、バック グラウンドで実行されます。 PC 管理の問題を解決する必要がある場合は、ログを確認できます。 Intune クライアント ソフトウェアおよび対応するログは、%Program Files%\Microsoft\OnlineManagement ディレクトリの下にインストールされます。

また、「[Microsoft Intune でのクライアント セットアップのトラブルシューティング](/intune/troubleshoot/troubleshoot-client-setup-in-microsoft-intune)」で、発生する可能性のある問題と、解決策または回避策を確認することもできます。

