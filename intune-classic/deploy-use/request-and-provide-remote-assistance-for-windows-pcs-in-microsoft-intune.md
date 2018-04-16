---
title: "Windows PC のリモート アシスタンス要求と提供"
description: "PC として管理されている Windows デスクトップにリモート アシスタントを提供し、PC をリモートで起動するためにエンドユーザーまたは IT 監理者が行う手順について説明します。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 12/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c2654491-5144-408a-a45a-644eb91ac1bb
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 245d18b89be9b9884df6c7ee41436e747c0557fe
ms.sourcegitcommit: 2459bfda07a2afd2cfcd94a1972a3fb2e565ce8d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/22/2018
---
# <a name="request-and-provide-remote-assistance-for-windows-pcs"></a>Windows PC のリモート アシスタンス要求と提供

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

このトピックの情報は、Intune ソフトウェア クライアントを使用して PC として管理している Windows デスクトップにのみ適用されます。

Intune では別売りの [TeamViewer](https://www.teamviewer.com) ソフトウェアを利用し、Intune ソフトウェア クライアントを実行するユーザーにリモート アシスタンス ヘルプを与えます。 ユーザーが Microsoft Intune Center のヘルプを要求すると、通知が届きます。要求を承諾し、アシスタンスを提供できます。 この機能は Intune の既存の Windows リモート アシスタンス機能に換わるものです。


## <a name="before-you-start"></a>開始する前に

リモート アシスタンス要求の確立または応答を開始する前に、次の前提条件が満たされていることを確認します。

- TeamViewer Web サイトにログインするために、[TeamViewer アカウントにサインアップ](https://login.teamviewer.com/LogOn#register)している必要があります。
- 管理する Windows PC を [Windows ソフトウェア クライアントで管理](manage-windows-pcs-with-microsoft-intune.md)する必要があります。
- Intune でサポートされているすべての Windows PC オペレーティング システムを管理できます。

## <a name="configure-the-teamviewer-connector"></a>TeamViewer Connector を構成する

1. [Microsoft Intune 管理コンソール](https://manage.microsoft.com)で、**[管理者]** を選択します。
2. **[管理者]** ワークスペースで、**[TeamViewer]** を選択します。
3. **[TeamViewer]** ページの **[TeamViewer Connector]** で、**[有効化]** を選択します。
4. **[TeamViewer の有効化]** ダイアログ ボックスで、ライセンス条項を **[承諾]** します。 TeamViewer ライセンスをまだ所有していない場合、**[TeamViewer ライセンスの購入]** を選択します。
5. TeamViewer ブラウザー ウィンドウが開いたら、TeamViewer 資格情報でサイトにサインインします。
6. TeamViewer サイトで、Intune で TeamViewer に接続するためのオプションを読み、承諾します。
7. Intune コンソールで、**[TeamViewer Connector]** アイテムに **[有効]** が表示されていることを確認します。


## <a name="open-a-remote-assistance-request-end-user"></a>リモート アシスタンス要求を登録する (エンド ユーザー)

1. クライアント Windows PC で、**[Microsoft Intune Center]** を開きます。
2. **[リモート アシスタンス]** で、**[リモート アシスタンスの要求]** を選択します。
3. 要求を承認すると (下図参照)、クライアントで TeamViewer が開きます。 Web ブラウザーが TeamViewer アプリケーションを開こうとしているというメッセージが表示されたら、ユーザーはそれを承諾する必要があります。
4. ユーザーには、管理者がユーザーの PC を操作してよいのか尋ねるメッセージが表示されます。 続行するには、ユーザーはメッセージを承諾する必要があります。
5. リモート アシスタンス セッション中、管理者が接続されていることを示すウィンドウがユーザーに表示されます。 ユーザーがこのウィンドウを閉じると、リモート セッションが終了します。

## <a name="respond-to-a-remote-assistance-request"></a>リモート アシスタンス要求に応答する

1. ユーザーがリモート アシスタンス要求を送信すると、**[アラート]** ワークスペースの **[管理]**  >  **[リモート アシスタンス]** に要求が表示されます。 次に例を示します。
   > ![リモート アシスタンス要求のスクリーンショット](./media/team-viewer.png)

<br>未応答のまま 4 時間以上経過すると、要求は削除されます。
2. 要求を承諾するには、**[要求を承認してリモート アシスタンスを開始する]** を選択します。
3. **[リモート アシスタンスの新しい要求が保留中]** ダイアログ ボックスで、**[リモート アシスタンスの要求を受け入れる]** を選択します。 まだインストールされていない場合、TeamViewer は PC に必要なアプリをインストールします。
4. TeamViewer は、管理者がエンド ユーザーの PC を操作することをエンド ユーザーに通知します。 ユーザーがこの要求を承諾すると、TeamViewer ウィンドウが開き、管理者は PC を操作できます。

リモート アシスタンス セッション中、リモート PC を操作するためのあらゆる TeamViewer コマンドを使用できます。 コマンドの詳細については、TeamViewer Web サイトから [[リモート コントロールのマニュアル]](http://www.teamviewer.com/en/support/documents/) をダウンロードしてください。

## <a name="close-the-remote-assistance-session"></a>リモート アシスタンス セッションを閉じる

**[TeamViewer]** ウィンドウの **[アクション]** メニューから **[セッションの終了]** を選択します。

## <a name="remotely-restart-a-windows-pc"></a>Windows PC をリモートで再起動する
問題を解決するためにユーザーをサポートする際、ユーザーの PC のリモート再起動が必要になる場合があります。 次の手順で Windows PC をリモート再起動します。

1.  [Microsoft Intune 管理コンソール](https://manage.microsoft.com/)で、**[グループ]** &gt; **[すべてのデバイス]** (または、再起動する PC が含まれる別のグループ) を選択します。

2.  1 つまたは複数の PC を選択し、**[リモート タスク]** &gt; **[コンピューターの再起動]** を選択します。

3.  タスクの状態を表示するには、ページの右下隅にある **[リモート タスク]** を選択します。

4.  **[タスクの状態]** ダイアログ ボックスで、現在のリモート タスク、タスクの状態、デバイス名、発生したエラーを確認します。

### <a name="see-also"></a>関連項目

[Intune ソフトウェア クライアントを使用した一般的な Windows PC 管理タスク](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)