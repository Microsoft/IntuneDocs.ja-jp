---
title: "Windows PC 管理機能 | Microsoft Intune"
description: "Intune クライアント ソフトウェアによって Windows PC を管理する場合の Intune の機能について説明します。"
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 08/04/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 77fa5c66-a87c-47df-964c-800eea509b33
ms.reviewer: owenyen
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a6caef9e0f4d6235ecf1a89c1765d6c8e6ce1a7b
ms.openlocfilehash: e5e3833a38434d4fe55cae554fc49f567b606ad8


---

# Windows PC 管理機能 (Microsoft Intune PC クライアント使用)
ほとんどのシナリオでは、デバイスを Microsoft Intune に登録します。そうすることで、Intune PC クライアントよりも多くの機能を利用できます。 ただし PC の管理には、Intune PC クライアントを使用することもできます。Intune PC クライアントでは、次の機能が利用できます。

-   **ソフトウェア更新プログラムの管理。**PC を最新の状態に保ち、更新プログラムを適用する時間を決定できます。

-   **Windows ファイアウォールのポリシー。**この機能により、会社で使用する PC に、非アクティブまたは適切でない構成の Windows ファイアウォールが存在しないようにします。

-   **マルウェア対策。**Intune には、マルウェアから PC を保護するのに役立つ Endpoint Protection が含まれています。

-   **リモート アシスタンス。**ユーザーは Intune を使用して、IT サポート スタッフに連絡できます。IT サポート スタッフは、Intune に含まれているリモート デスクトップ機能を使用してサポートを提供できます (TeamViewer ソフトウェアが必要)。

-   **ソフトウェア ライセンス管理。**使用可能なソフトウェア ライセンスの数と、そのうちの使用中のライセンスの数を追跡します。
-   **アプリの展開。**管理対象の PC にソフトウェアを展開します。 クライアント ソフトウェアを使用して PC を管理するときは、一部のアプリ管理機能が利用できません。


Intune は、最大 7,000 台の Windows デバイスへの PC クライアント ソフトウェアのインストールをサポートしています。

## オペレーティング システムの要件
Intune では、次の Windows バージョンを実行する PC を管理できます (32 ビットと 64 ビットの両方)。


-   **Windows Vista** - Business、Enterprise、および Ultimate バージョン

-   **Windows 7** - Pro、Enterprise、および Ultimate バージョン (Service Pack なし、または SP1)

-   **Windows 8** - Pro および Enterprise バージョン

-   **Windows 8.1** - Pro および Enterprise バージョン

- **Windows 10** - Pro、Education、および Enterprise バージョン


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



<!--HONumber=Aug16_HO3-->


