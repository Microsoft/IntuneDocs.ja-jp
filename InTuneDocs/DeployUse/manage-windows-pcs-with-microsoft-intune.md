---
title: "Intune を使用して Windows PC を管理する | Microsoft Intune"
description: 
keywords: 
author: nathbarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b8d22fe-c318-4796-b760-44f1ccf34312
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 0335b80afa8e330263baad054f0e902f019f75bb
ms.openlocfilehash: 92f4ddde3336fd4cf07c701596f5ebe4c0aeb49f


---

# Microsoft Intune を使用して Windows PC を管理する
Intune を使用すると、デバイスを登録するだけでなく、Intune Windows PC クライアント ソフトウェアを使用して、サポートされるオペレーティング システムを実行する Windows PC も管理できます。 コンピューター クライアントを実行するためのハードウェアとソフトウェアの要件は最小限に抑えられており、基本的には、Windows 7 以降を実行できるすべてのシステムがサポートされます。  また、クライアント ソフトウェアは、(任意のドメイン内の) ドメインに参加しているコンピューターとドメインに参加していないコンピューターのどちらにも簡単にインストールできます。

Intune では、Windows Server における Active Directory ドメイン サービス (AD DS) グループ ポリシー オブジェクト (GPO) と似た方法でポリシーを使用して Windows PC を管理します。 Active Directory ドメインに参加しているコンピューターを Intune で管理する場合は、[Intune のポリシーが組織で設定されているどの GPO とも競合しないようにしてください](resolve-gpo-and-microsoft-intune-policy-conflicts.md)。

> [!NOTE]
> スタンドアロン サービスとしての Microsoft Intune は、コンピューターを管理するために以下の機能を提供します。 Windows 8.1 を実行しているデバイスは、Intune クライアントを使用して管理できるほか、モバイル デバイスとして登録することもできます。 以下は、Intune クライアントを実行するコンピューターに適用される情報です。

## Intune PC 管理の要件

**ハードウェア**: 次に、Intune クライアントをインストールするハードウェアの最小要件を示します。

|要件|説明|
|---------------|--------------------|
|ネットワーク|クライアントでは、PC がインターネット接続できる必要があります。|
|プロセッサとメモリ|PC のオペレーティング システムに対するプロセッサ要件と RAM 要件を参照してください。|
|ディスク領域|クライアント ソフトウェアをインストールする前に、200 MB の空きディスク領域が必要です。|

**ソフトウェア**: 次に、クライアントをインストールするソフトウェアの要件を示します。

|要件|説明|
|---------------|--------------------|
|管理者のアクセス許可|クライアント ソフトウェアをインストールするアカウントは、その PC のローカル管理者のアクセス許可を持っている必要があります。|
|Windows インストーラー 3.1|PC には Windows インストーラー 3.1 以降がインストールされている必要があります。<br /><br />PC で Windows インストーラーのバージョンを確認するには<br /><br />-   PC で、**%windir%\System32\msiexec.exe** を右クリックし、**[プロパティ]** をクリックします。<br /><br />最新バージョンの Windows インストーラーは、Microsoft Developer Network Web サイトの「 [Windows Installer Redistributables (Windows インストーラー再頒布可能パッケージ)](http://go.microsoft.com/fwlink/?LinkID=234258) 」からダウンロードできます。|
|互換性のないクライアント ソフトウェアを削除する|Intune クライアント ソフトウェアをインストールする前に、その PC から Configuration Manager または System Management Server クライアント ソフトウェアをアンインストールする必要があります。|

## Intune コンピューター クライアントのインストール
Intune で Windows PC を管理する最初の手順は、クライアントのインストールです。 PC が Intune サービスによる管理に登録されていれば、次のいずれかの方法でクライアント ソフトウェアをインストールできます。

-   [Microsoft Intune クライアント ソフトウェアを手動で展開](install-the-windows-pc-client-with-microsoft-intune.md#to-manually-deploy-the-client-software)できます。 この種類の展開では、管理者は Intune クライアント ソフトウェアをダウンロードし、手動で各 PC にインストールします。

    Intune クライアント ソフトウェアをダウンロードするには、Intune 管理コンソールを開いて、[クライアント ソフトウェアのダウンロード] 領域でクライアント ソフトウェア パッケージをダウンロードします。 クライアント ソフトウェアのインストール後、コンピューターを管理するために必要な追加のソフトウェアが Intune によって自動的にインストールされます。

-   Intune クライアントを手動でインストールする場合にダウンロードするのと同じファイルを使用して、[ドメインに参加しているコンピューターに Active Directory GPO を使ってクライアントを展開できます](install-the-windows-pc-client-with-microsoft-intune.md#to-automatically-deploy-the-client-software-by-using-group-policy)。

-   [エンド ユーザーは、Intune ポータル サイトで自分の各コンピューターを自己登録できます](install-the-windows-pc-client-with-microsoft-intune.md#how-users-can-self-enroll-their-computers)。 登録されたコンピューターは、Intune クライアント ソフトウェアをインストールするときに使用したユーザー アカウントに自動的に関連付けられます。

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



<!--HONumber=Jun16_HO4-->


