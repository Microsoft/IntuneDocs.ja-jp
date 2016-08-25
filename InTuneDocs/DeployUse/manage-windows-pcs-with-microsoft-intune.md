---
title: "Intune クライアントを使用して Windows PC を管理する | Microsoft Intune"
description: "Intune クライアント ソフトウェアをインストールして Windows PC を管理します。"
keywords: 
author: nathbarn
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b8d22fe-c318-4796-b760-44f1ccf34312
ms.reviewer: owenyen
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: aa1d6105a5be9c329c75681857a9d6e553088b65
ms.openlocfilehash: be45b2ffb99eb75e71c0d591fc84089b83735905


---

# Intune PC クライアント ソフトウェアを使用して Windows PC を管理する
[モバイル デバイスとして Windows PC を登録する](set-up-windows-device-management-with-microsoft-intune.md)代わりに、Intune クライアント ソフトウェアをインストールして Windows PC を管理することができます。

Intune では、Windows Server における Active Directory ドメイン サービス (AD DS) グループ ポリシー オブジェクト (GPO) と似た方法でポリシーを使用して Windows PC を管理します。 Active Directory ドメインに参加しているコンピューターを Intune で管理する場合は、[Intune のポリシーが組織で設定されているどの GPO とも競合しないようにしてください](resolve-gpo-and-microsoft-intune-policy-conflicts.md)。

Intune クライアンでは、ソフトウェアの更新、Windows ファイアウォール、および Endpoint Protection を管理することで [PC の保護に役立つポリシー](policies-to-protect-windows-pcs-in-microsoft-intune.md)がサポートされますが、Intune クライアントで管理される PC を他の Intune ポリシーの対象とすることはできません。

> [!NOTE]
> Windows 8.1 以降を実行しているデバイスは、Intune クライアントを使用して管理できるほか、モバイル デバイスとして登録することもできます。 以下は、Intune クライアントを実行するコンピューターに適用される情報です。 Intune PC クライアントとモバイル デバイス管理用の Windows デバイス登録の両方のインストールはサポートされません。

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
|オペレーティング システム | Windows 7.0 以降を実行している Windows デバイスであること。 |
|管理者のアクセス許可|クライアント ソフトウェアをインストールするアカウントは、そのデバイスのローカル管理者のアクセス許可を持っている必要があります。|
|Windows インストーラー 3.1|PC には Windows インストーラー 3.1 以降がインストールされている必要があります。<br /><br />PC で Windows インストーラーのバージョンを確認するには<br /><br />-   PC で、**%windir%\System32\msiexec.exe** を右クリックし、**[プロパティ]** をクリックします。<br /><br />最新バージョンの Windows インストーラーは、Microsoft Developer Network Web サイトの「 [Windows Installer Redistributables (Windows インストーラー再頒布可能パッケージ)](http://go.microsoft.com/fwlink/?LinkID=234258) 」からダウンロードできます。|
|互換性のないクライアント ソフトウェアを削除する|Intune クライアント ソフトウェアをインストールする前に、その PC から Configuration Manager または System Management Server クライアント ソフトウェアをアンインストールする必要があります。|

## Intune コンピューター クライアントのインストール
Intune クライアント ソフトウェアは、次の方法のいずれかでインストールできます。

-   [Microsoft Intune クライアント ソフトウェアを手動で展開します](install-the-windows-pc-client-with-microsoft-intune.md#to-manually-deploy-the-client-software)。 この種類の展開では、管理者は Intune クライアント ソフトウェアをダウンロードし、手動で各 PC にインストールします。

  Intune クライアント ソフトウェアをダウンロードするには、[Intune 管理コンソール](https://manage.microsoft.com)を開いて、**[管理]**  >  **[クライアント ソフトウェアのダウンロード]** の順に選択し、**[クライアント ソフトウェアのダウンロード]** をクリックします。

-   Intune クライアントを手動でインストールする場合にダウンロードするのと同じファイルを使用して、[ドメインに参加しているコンピューターに Active Directory GPO を使ってクライアントを展開できます](install-the-windows-pc-client-with-microsoft-intune.md#to-automatically-deploy-the-client-software-by-using-group-policy)。

-   Intune クライアント ソフトウェアを、[オペレーティング システム展開](install-the-windows-pc-client-with-microsoft-intune.md#install-the-microsoft-intune-client-software-as-part-of-an-image)の一部としてコンピューターに展開することもできます。

## Intune コンピューター クライアントを使用したコンピューター管理
Intune クライアントのインストール後は、[アプリケーション管理](deploy-apps-in-microsoft-intune.md)、Endpoint Protection、ハードウェアおよびソフトウェアのインベントリ、リモート制御 (リモート アシスタンス要求を使用)、ソフトウェア更新プログラム、コンプライアンス設定レポートなど、クライアント ソフトウェアが備えるさまざまなコンピューター管理機能を使用できます。

コンピューター クライアントで実行できる各種コンピューター管理タスクは、次のような Intune ポリシーを使用して管理されます。

-   管理対象コンピューターの [Windows ファイアウォール設定](help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md)の構成

-   管理対象コンピューターが必須のソフトウェア更新プログラムを確認してダウンロードするための[ソフトウェア更新設定](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md)の構成

-   管理対象コンピューターを脅威や悪意のあるソフトウェアから保護するための、[リアルタイム監視と Endpoint Protection](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md) 管理によるサポート

各コンピューターでローカルに実行される Intune クライアント エージェントの操作以外にも、以下に示すような、クライアントがインストールされている Windows PC に対する[一般的なコンピューター管理タスク](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)を Intune 管理者コンソールから実行できます。

-   管理対象コンピューターに関するハードウェアおよびソフトウェアのインベントリの表示

-   リモートからのコンピューターの再起動

-   コンピューターの使用を停止するための、クライアント ソフトウェアのアンインストールと、Intune による管理からの削除

-   特定の管理対象コンピューターへのユーザーの関連付け

-   リモート アシスタンス要求への応答

Intune のクライアント エージェントは通常、ユーザー操作やトラブルシューティングをほとんど必要とせずに、バック グラウンドで実行されます。 ただし、コンピューター管理に関する問題についてサポートが必要になった場合は、[解決に役立つリソース](/intune/troubleshoot/troubleshoot-client-setup-in-microsoft-intune)が用意されています。



<!--HONumber=Aug16_HO1-->


