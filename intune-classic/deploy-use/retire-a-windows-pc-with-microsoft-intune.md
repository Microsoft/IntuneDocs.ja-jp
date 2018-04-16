---
title: "Windows PC をインベントリから削除する"
description: "Intune で管理されている Windows PC をインベントリから削除する方法。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 12/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5c916182-d99c-44c5-a779-3f596f261c40
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 99dc86bf20a50710cf1661702d46a3124861a619
ms.sourcegitcommit: 2459bfda07a2afd2cfcd94a1972a3fb2e565ce8d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/22/2018
---
# <a name="retire-a-windows-pc"></a>Windows PC をインベントリから削除する

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Intune ソフトウェア クライアントを実行して PC として管理しているデスクトップは、次の手順でインベントリから削除します。 PC をインベントリから削除すると、Intune 管理から除外されます。 Intune から PC をリセットし、工場出荷時の設定に戻すことはできません。

1.  [Microsoft Intune 管理コンソール](https://manage.microsoft.com/)で、**[グループ]** &gt; **[すべてのデバイス]** (または、インベントリから削除する PC が含まれる別のグループ) を選択します。

2.  削除するデバイスを選択し、**[インベントリからの削除/ワイプ]** を選択します。

PC を Intune に再登録する場合は、「[Microsoft Intune を使用して Windows PC クライアントをインストールする](install-the-windows-pc-client-with-microsoft-intune.md)」を参照して、その PC にソフトウェア クライアントを再度インストールしてください。

PC が Intune に接続できない場合、**[ダッシュボード]** ワークスペースにメッセージが表示されます。

PC をインベントリから削除した場合:

-   PC は Intune の管理とインベントリから削除され、そのコンピューターに関連付けられていたライセンスは再利用できます。 削除/ワイプを行うと、PC から Intune ソフトウェア クライアントが削除されますが、アプリまたはデータは削除されません。 削除すると、PC でフル ワイプは実行されません。

-   そのコンピューターの状態は、Intune コンソールに表示されなくなります。

-   Intune によって、PC からソフトウェア クライアントが削除されます。 PC が Intune サービスに接続していない場合、ソフトウェア クライアントは、次に接続したときに削除されます。

-   PC から Microsoft Intune Endpoint Protection が削除されます。 PC に他のエンドポイント保護アプリケーションがインストールされ、無効になっている場合は、Microsoft Intune Endpoint Protection が削除された後で、そのアプリケーションを再び有効にして、PC を保護できます。

-   すべてのポリシーが PC から削除され、ポリシーによって設定された値は変更されます。

-   PC は、ソフトウェアの更新プログラムや、マルウェアの定義の更新を Intune サービスから受信しなくなります。

-   PC がどのように構成されているかによって異なりますが、Windows Server Update Services、Windows Update、または Microsoft Update を使用して、引き続き更新プログラムを受信できます。

    > [!IMPORTANT]
    > クライアント ソフトウェアがグループ ポリシー オブジェクト (GPO) を使用してインストールされている場合、ソフトウェアが再インストールされることを防ぐため、クライアント ソフトウェアを削除する前に、グループ ポリシー オブジェクト (GPO) を削除する必要があります。

    Endpoint Protection クライアントのアンインストールに失敗する場合は、「[Endpoint Protection に関するトラブルシューティング](/intune-classic/troubleshoot/troubleshoot-endpoint-protection-in-microsoft-intune)」で詳細を確認してください。

### <a name="see-also"></a>関連項目

[Intune ソフトウェア クライアントを使用した一般的な Windows PC 管理タスク](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)