---
title: "Windows PC 管理機能 | Microsoft Intune"
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 77fa5c66-a87c-47df-964c-800eea509b33
ms.reviewer: owenyen
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 665e4a1aa7ee22db91b47660a179384f7c3e4393
ms.openlocfilehash: 9e7a2f5cb2afdeca737c0c8b1b91418352ad5539


---

# Windows PC 管理機能 (Microsoft Intune PC クライアント使用)
ほとんどのシナリオでは、デバイスを Microsoft Intune に登録します。そうすることで、Intune PC クライアントよりも多くの機能を利用できます。 ただし PC の管理には、Intune PC クライアントを使用することもできます。Intune PC クライアントでは、次の機能が利用できます。

-   **ソフトウェア更新プログラムの管理。**PC を最新の状態に保ち、更新プログラムを適用する時間を管理できます。

-   **Windows ファイアウォールのポリシー。**この機能により、会社で使用する PC に、非アクティブまたは適切でない構成の Windows ファイアウォールが存在しないようにします。

-   **マルウェア対策。**Intune には、マルウェアから PC を保護するのに役立つ Endpoint Protection が含まれています。

-   **リモート アシスタンス。**ユーザーは Intune を使用して、IT サポート スタッフに連絡できます。IT サポート スタッフは、Intune に含まれているリモート デスクトップ機能を使用してサポートを提供できます<!--- (requires TeamViewer software)--->。

-   **ソフトウェア ライセンス管理。**使用可能なソフトウェア ライセンスの数と、そのうちの使用中のライセンスの数を追跡します。
-   **アプリの展開。**管理対象の PC にソフトウェアを展開します。 クライアント ソフトウェアを使用して PC を管理するときは、一部のアプリ管理機能が利用できません。


Intune は、最大 7,000 台の Windows デバイスへの PC クライアント ソフトウェアのインストールをサポートしています。

## オペレーティング システムの要件
Intune では、次の Windows バージョンを実行する PC を管理できます (x86 と x64 のいずれも可)。


-   **Windows Vista** - Business、Enterprise、および Ultimate バージョン

-   **Windows 7** - Pro、Enterprise、および Ultimate バージョン (Service Pack なし、または SP1)

-   **Windows 8** - Pro および Enterprise バージョン

-   **Windows 8.1** - Pro および Enterprise バージョン

- **Windows 10** - Home、Pro、Education、および Enterprise バージョン


## ハードウェアに最低限必要な条件
次に、Intune PC クライアントをインストールするハードウェアの最小要件を示します。

|要件|説明|
|---------------|--------------------|
|Network (ネットワーク)|クライアントでは、PC がインターネット接続できる必要があります。|
|プロセッサとメモリ|PC のオペレーティング システムに対するプロセッサ要件と RAM 要件を参照してください。|
|ディスク領域|クライアント ソフトウェアをインストールする前に、200 MB の空きディスク領域が必要です。|

## その他の要件
以下に、Intune クライアントをインストールする場合のソフトウェアの要件を示します。

|要件|説明|
|---------------|--------------------|
|管理者のアクセス許可|クライアント ソフトウェアをインストールするアカウントは、その PC のローカル管理者のアクセス許可を持っている必要があります。|
|Windows インストーラー 3.1|PC には Windows インストーラー 3.1 以降がインストールされている必要があります。|
|互換性のないクライアント ソフトウェアを削除する|Intune PC クライアント ソフトウェアをインストールする前に、その PC から次のクライアント ソフトウェアをアンインストールする必要があります。<br /><br />-   Configuration Manager のすべてのバージョン<br />-   Microsoft Systems Management Server (SMS) のすべてのバージョン|

### 関連項目
[Microsoft Intune のモバイル デバイス管理機能](./mobile-device-management-capabilities-in-microsoft-intune.md)



<!--HONumber=Jun16_HO4-->


