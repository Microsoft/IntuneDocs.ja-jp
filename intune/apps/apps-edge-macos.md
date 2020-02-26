---
title: Microsoft Intune を使用して Microsoft Edge を macOS デバイスに追加する
titleSuffix: ''
description: Microsoft Intune を使用して、macOS デバイスに Microsoft Edge を追加する方法について説明します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/21/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: kellieei
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6ebcb81cd0f186a3fd23e0701d12ea871eab129a
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912574"
---
# <a name="add-microsoft-edge-to-macos-devices-using-microsoft-intune"></a>Microsoft Intune を使用して Microsoft Edge を macOS デバイスに追加する

アプリの展開、構成、監視、または保護を行うには、対象のアプリを事前に Intune に追加しておく必要があります。 使用可能な[アプリの種類](~/apps/apps-add.md#app-types-in-microsoft-intune)の 1 つに、Microsoft Edge *バージョン 77 以降*があります。 Intune でこの種類のアプリを選択することで、macOS を実行し、自分で管理しているデバイスに Microsoft Edge *バージョン 77 以降*を割り当て、インストールできます。 このアプリの種類を使用すると、macOS アプリ ラッピング ツールを使用しなくても、macOS デバイスに Microsoft Edge を簡単に割り当てることができます。 アプリのセキュリティを強化し、最新の状態に保つために、これらのアプリには Microsoft AutoUpdate (MAU) が付属しています。

> [!IMPORTANT]
> このアプリの種類は**パブリック プレビュー**段階で、macOS 向けの Developer Channel と Beta Channel が提供されています。 展開は英語版 (EN) のみですが、エンド ユーザーはブラウザーの **[設定]**  >  **[言語]** で表示言語を変更することができます。 

> [!NOTE]
> Windows 10 では、Microsoft Edge *バージョン 77 以降*も利用できます。

## <a name="prerequisites"></a>[前提条件]
- Microsoft Edge をインストールする前に、macOS デバイスで macOS 10.12 以降が実行されている必要があります。

## <a name="add-microsoft-edge-to-intune"></a>Microsoft Edge を Intune に追加する
Microsoft Edge バージョン 77 以降を Intune に追加するには、次の手順を行います。

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。
2. **[アプリ]**  >  **[すべてのアプリ]**  >  **[追加]** の順に選択します。
3. **Microsoft Edge バージョン 77 以降**の **[アプリの種類]** リストで、**[macOS]** を選択します。

## <a name="configure-app-information"></a>アプリ情報の構成
この手順では、このアプリの展開に関する情報を指定します。 この情報は、Intune でアプリを識別する場合に役立ち、会社のポータルでユーザーがアプリを探す場合にも役立ちます。

1. **[アプリ情報]** をクリックして **[アプリ情報]** ウィンドウを表示します。
2. **[アプリ情報]** ウィンドウで、このアプリの展開に関する情報を指定します。 この情報は、Intune でアプリを識別する場合に役立ち、会社のポータルでユーザーがアプリを探す場合にも役立ちます。
    - **名前**:アプリの名前を入力します。この名前は会社のポータルに表示されます。 すべての名前が一意であることを確認します。 同じアプリ名が 2 つ存在する場合、会社のポータルではそのいずれかのみがユーザーに表示されます。
    - **説明**:アプリの説明を入力します。 たとえば、説明にターゲット ユーザーを一覧表示することができます。
    - **[発行元]** : Microsoft が発行者として表示されます。
    - **[カテゴリ]** : (省略可能) 1 つ以上の組み込みアプリ カテゴリ、または作成したカテゴリを選択します。 この設定を行うと、会社のポータルを閲覧するときに、ユーザーがアプリを探しやすくなります。
    - **[会社のポータルでおすすめアプリとして表示します]** : ユーザーがアプリを参照するとき、会社のポータルのメイン ページにアプリが目立つように表示するには、このオプションを選びます。
    - **[情報 URL]** : このアプリに関する情報が含まれる Web サイトの URL を入力することもできます。 この URL は会社のポータルでユーザーに表示されます。
    - **[プライバシー URL]** : このアプリのプライバシー情報が含まれる Web サイトの URL を入力することもできます。 この URL は会社のポータルでユーザーに表示されます。
    - **[開発者]** : Microsoft が開発者として表示されます。
    - **[所有者]** : Microsoft が所有者として表示されます。
    - **[メモ]** : (省略可能) このアプリに関連付けるメモを入力します。
3. **[OK]** を選択します。

## <a name="configure-microsoft-edge-settings"></a>Microsoft Edge の設定の構成
この手順では、アプリのインストール オプションを構成します。

1. **[アプリの追加]** ウィンドウで、 **[アプリ設定]** を選びます。
2. **[アプリ設定]** ウィンドウで、 **[チャネル]** リストから **[安定]** 、 **[Beta]** 、 **[Dev]** のいずれかを選択して、アプリの展開元となる Edge チャネルを決定します。

    - **[安定]** チャネルは、エンタープライズ環境で幅広く展開する場合に推奨されるチャネルです。 6 週間ごとに更新されます。各リリースには Beta チャネルの機能強化が組み込まれています。
    - **[Beta]** チャネルは、Microsoft Edge の最も安定したプレビュー エクスペリエンスであり、組織内での完全なパイロットに最適な選択肢です。 6 週間ごとにメジャー アップデートが行われ、各リリースには、Dev チャネルの学習と改良が組み込まれています。
    - **[Dev]** チャネルは、Windows、Windows Server、macOS に関するエンタープライズ フィードバックのためにあります。 毎週更新され、最新の機能強化と修正が含まれています。

    > [!NOTE]
    > Microsoft Edge ブラウザー ロゴは、ユーザーが会社のポータルを閲覧するときに、アプリに表示されるロゴです。

3.  **[OK]** を選択します。

## <a name="select-scope-tags-optional"></a>スコープのタグを選択する (省略可能)
スコープのタグを使って、Intune のクライアント アプリの情報を表示できるユーザーを決定することができます。 スコープのタグの詳細については、分散 IT のためのロールベースのアクセス制御とスコープのタグの使用に関するページをご覧ください。
1.  **[スコープ (タグ)]**  >  **[追加]** を選択します。
2.  **[選択]** ボックスを使ってスコープのタグを検索します。
3.  このアプリに割り当てるスコープのタグの横にあるチェック ボックスをオンにします。
4.  **[選択]**  >  **[OK]** の順に選択します。

## <a name="add-the-app"></a>アプリを追加する
構成が完了したら、 **[アプリの追加]** ウィンドウから **[追加]** を選択します。 

作成したアプリはアプリの一覧に表示され、選択したグループに割り当てることができるようになります。 

> [!NOTE]
> 現在、Apple では、Intune で macOS デバイス上の Microsoft Edge をアンインストールする方法を提供していません。

## <a name="next-steps"></a>次のステップ
- macOS デバイスで Microsoft Edge を構成する方法については、[macOS デバイスでの Microsoft Edge の構成](https://docs.microsoft.com/deployedge/configure-microsoft-edge-on-mac)に関するページを参照してください。
- アプリ割り当てをユーザーのグループに追加したり、除外したりする方法については、「[アプリ割り当ての組み込みと除外](~/apps/apps-inc-exl-assignments.md)」を参照してください。
- [アプリをグループに割り当てる](~/apps/apps-deploy.md)

