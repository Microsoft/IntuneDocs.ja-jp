---
title: "クライアント ソフトウェアを使用して PC を管理する |Microsoft Intune"
description: "Intune クライアント ソフトウェアをインストールして Windows PC を管理します。"
keywords: 
author: nathbarn
manager: angrobe
ms.date: 08/30/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b8d22fe-c318-4796-b760-44f1ccf34312
ms.reviewer: owenyen
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a4cc8b7e34e8809eebd7fdec8ffac0599c96d309
ms.openlocfilehash: ce27fc737fdf47903d7554eb15f24f07b3524406


---

# Intune PC クライアント ソフトウェアを使用して Windows PC を管理する
[モバイル デバイスとして Windows PC を登録する](set-up-windows-device-management-with-microsoft-intune.md)代わりに、Intune クライアント ソフトウェアをインストールすることで Windows PC を登録して管理することができます。

Intune では、Windows Server における Active Directory ドメイン サービス (AD DS) グループ ポリシー オブジェクト (GPO) と似た方法でポリシーを使用して Windows PC を管理します。 Active Directory ドメインに参加しているコンピューターを Intune で管理する場合は、[Intune のポリシーが組織で設定されているどの GPO とも競合しないようにしてください](resolve-gpo-and-microsoft-intune-policy-conflicts.md)。

Intune ソフトウェア クライアントでは、ソフトウェアの更新、Windows ファイアウォール、および Endpoint Protection を管理することで [PC の保護に役立つ管理機能](policies-to-protect-windows-pcs-in-microsoft-intune.md)がサポートされますが、Intune ソフトウェア クライアントで管理される PC を、モバイル デバイス管理に特化した **Windows** ポリシー設定などの他の Intune ポリシーの対象とすることはできません。

> [!NOTE]
> Windows 8.1 以降を実行しているデバイスを Intune クライアントで、またはモバイル デバイスとして管理できます。 このトピックは、Intune ソフトウェア クライアントを実行しているコンピューターに適用されます。 Intune クライアントのインストールとモバイル デバイス管理の登録はサポートされません。

## Intune PC クライアント管理の要件

**ハードウェア**: 次に、Intune クライアントをインストールするハードウェアの最小要件を示します。

|要件|説明|
|---------------|--------------------|
|ネットワーク|クライアントでは、PC がインターネット接続できる必要があります。|
|プロセッサとメモリ|PC のオペレーティング システムに対するプロセッサ要件と RAM 要件を参照してください。|
|ディスク領域|クライアント ソフトウェアをインストールする前に、200 MB の空きディスク領域が必要です。|

**ソフトウェア**: 次に、クライアントをインストールするソフトウェアの要件を示します。

|要件|説明|
|---------------|--------------------|
|オペレーティング システム | Windows Vista 以降を実行している Windows デバイスであること。 Home エディションのバージョンはサポートされていません。|
|管理者のアクセス許可|クライアント ソフトウェアをインストールするアカウントは、そのデバイスのローカル管理者のアクセス許可を持っている必要があります。|
|Windows インストーラー 3.1|PC には Windows インストーラー 3.1 以降がインストールされている必要があります。<br /><br />PC で Windows インストーラーのバージョンを確認するには<br /><br />-   PC で、**%windir%\System32\msiexec.exe** を右クリックし、**[プロパティ]** をクリックします。<br /><br />最新バージョンの Windows インストーラーは、Microsoft Developer Network Web サイトの「 [Windows Installer Redistributables (Windows インストーラー再頒布可能パッケージ)](http://go.microsoft.com/fwlink/?LinkID=234258) 」からダウンロードできます。|
|互換性のないクライアント ソフトウェアを削除する|Intune クライアント ソフトウェアをインストールする前に、その PC から Configuration Manager または System Management Server クライアント ソフトウェアをアンインストールする必要があります。|

## Intune コンピューター クライアントを使用したコンピューター管理
Intune クライアント ソフトウェアのインストール後は、[アプリケーション管理](deploy-apps-in-microsoft-intune.md)、[リアルタイム監視と Endpoint Protection](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md)、[Windows ファイアウォール設定管理](help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md)、ハードウェアおよびソフトウェアのインベントリ、リモート制御 (リモート アシスタンス要求を使用)、[ソフトウェア更新設定](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md)、コンプライアンス設定レポートなどの管理機能を使用できます。

モバイル デバイスとして管理されている PC に使用できる管理オプションは、以下を含むソフトウェア クライアントが管理する PC には使用できません。

-   フル ワイプ (選択的ワイプは使用可能)
-   条件付きアクセス
-   **コンピューターの管理**ポリシー以外の Windows ポリシー

![Windows PC のポリシー テンプレート](../media/pc_policy_template.png)

各コンピューターでローカルに実行される Intune クライアント エージェントの操作以外にも、以下に示すような、クライアントがインストールされている Windows PC に対する[一般的なコンピューター管理タスク](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)を Intune 管理者コンソールから実行できます。

-   管理対象コンピューターに関するハードウェアおよびソフトウェアのインベントリの表示

-   リモートからのコンピューターの再起動

-   コンピューターの使用を停止するための、クライアント ソフトウェアのアンインストールと、Intune による管理からの削除

-   特定の管理対象コンピューターへのユーザーの関連付け

-   リモート アシスタンス要求への応答

Intune のクライアント エージェントは通常、ユーザー操作やトラブルシューティングをほとんど必要とせずに、バック グラウンドで実行されます。 ただし、コンピューター管理に関する問題についてサポートが必要になった場合は、[解決に役立つリソース](/intune/troubleshoot/troubleshoot-client-setup-in-microsoft-intune)が用意されています。



<!--HONumber=Sep16_HO2-->


