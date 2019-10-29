---
title: Microsoft Edge for Windows 10 を Microsoft Intune に追加する
titleSuffix: ''
description: Microsoft Edge for Windows を Microsoft Intune に追加する方法について説明します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/09/2019
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
ms.openlocfilehash: 492feb3f2ef5f5bbbc1537d4c60ac12d5fd6bdcd
ms.sourcegitcommit: 0be25b59c8e386f972a855712fc6ec3deccede86
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2019
ms.locfileid: "72585606"
---
# <a name="add-microsoft-edge-for-windows-10-to-microsoft-intune"></a>Microsoft Edge for Windows 10 を Microsoft Intune に追加する

アプリの展開、構成、監視、または保護を行うには、対象のアプリを事前に Intune に追加しておく必要があります。 使用可能な[アプリの種類](~/apps/apps-add.md#app-types-in-microsoft-intune)の 1 つに、Microsoft Edge *バージョン 77 以降*があります。 Intune でこの種類のアプリを選択することで、Windows 10 を実行し、自分で管理しているデバイスに Microsoft Edge *バージョン 77 以降*を割り当て、インストールできます。

> [!IMPORTANT]
> このアプリの種類は**パブリック プレビュー**段階で、Windows 10 向けの Developer Channel と Beta Channel が提供されています。 展開は英語版 (EN) のみですが、エンド ユーザーはブラウザーの **[設定]**  >  **[言語]** で表示言語を変更することができます。 Microsoft Edge はアーキテクチャに合わせてインストールされる Win32 アプリです (x86 OS の場合は x86、x64 OS の場合は x64)。 さらに、Edge の自動更新は既定で**オン**になっています。また、Edge はアンインストールできません。

> [!NOTE]
> macOS では、Microsoft Edge *バージョン 77 以降*も利用できます。
> 
> ワークプレースに参加させるコンピューターに Microsoft Edge の組み込みのアプリケーション展開を使用することはできません。 組み込みのアプリケーション展開には、Intune 管理拡張機能が必要ですが、これは AAD 参加済みデバイスにのみ存在します。 **クライアント アプリ**にアップロードされた *.msi* を使用すれば、引き続き Microsoft Edge *バージョン 77 以降*を展開することができます。「[Windows の基幹業務アプリを Microsoft Intune に追加する](~/apps/lob-apps-windows.md)」を参照してください。

## <a name="prerequisites"></a>必要条件
- Windows 10 RS2 以上が必要です。
- **Developer** Channel と **Beta** Channel 向けにユーザー コンテキストでプレインストールされた Microsoft Edge *バージョン 77 以降*のバージョンはすべて、システム コンテキストでインストールされた Edge で上書きされます。

## <a name="configure-the-app-in-intune"></a>Intune でアプリを構成する
Microsoft Edge バージョン 77 以降を Intune に追加するには、次の手順を行います。

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインします。
2. **[Intune]** ウィンドウで、 **[クライアント アプリ]**  >  **[アプリ]**  >  **[追加]** を選択します。
3. **Microsoft Edge バージョン 77 以降**の **[アプリの種類]** リストで、 **[Windows 10]** を選択します。

## <a name="configure-app-information"></a>アプリ情報の構成
この手順では、このアプリの展開に関する情報を指定します。 この情報は、Intune でアプリを識別する場合に役立ち、会社のポータルでユーザーがアプリを探す場合にも役立ちます。

1. **[アプリ情報]** をクリックして **[アプリ情報]** ブレードを表示します。
2. **[アプリ情報]** ブレードで、このアプリの展開に関する情報を指定します。 この情報は、Intune でアプリを識別する場合に役立ち、会社のポータルでユーザーがアプリを探す場合にも役立ちます。
    - **名前**: アプリの名前を入力します。この名前は会社のポータルに表示されます。 すべての名前が一意であることを確認します。 同じアプリ名が 2 つ存在する場合、会社のポータルではそのいずれかのみがユーザーに表示されます。
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

## <a name="configure-app-settings"></a>アプリの設定の構成
この手順では、アプリのインストール オプションを構成します。

1. **[アプリの追加]** ブレードで **[アプリの設定]** を選択します。
2. **[アプリの設定]** ブレードで、 **[Channel]** リストから **[Beta]** または **[Dev]** を選択して、アプリの展開元となる Edge Channel を決定します。
    - **[Beta]** Channel は、Microsoft Edge の最も安定したプレビュー エクスペリエンスであり、組織内での完全なパイロットに最適な選択肢です。 6 週間ごとにメジャー アップデートが行われ、各リリースには、Dev Channel の学習と改良が組み込まれています。
    - **[Dev]** Channel は、Windows、Windows Server、macOS に関するエンタープライズ フィードバックの準備ができています。 毎週更新され、最新の機能強化と修正が含まれています。

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
アプリの構成が完了したら、 **[アプリの追加]** ブレードから **[追加]** を選択します。 

作成したアプリはアプリの一覧に表示され、選択したグループに割り当てることができるようになります。 

> [!NOTE]
> 現時点では、Microsoft Edge の展開の割り当てを解除すると、デバイスに残ります。

## <a name="troubleshooting"></a>トラブルシューティング
**Windows 10 向け Microsoft Edge バージョン 77 以降:**<br>
Intune では、Intune 管理拡張機能を使用して、割り当て済みの Windows 10 デバイスに Microsoft Edge インストーラーがダウンロードされて展開され、その後、展開設定が Microsoft Edge インストーラーに伝えられます。このインストーラーによって、Microsoft Edge ブラウザーが CDN から直接ダウンロードされてインストールされます。 [Intune 管理拡張機能の前提条件](~/apps/intune-management-extension.md#prerequisites)と、Azure Update Service と CDN へのアクセスで説明されているベスト プラクティスを参照して、ご自分のネットワーク構成において Windows 10 デバイスでこれらの場所へのアクセスが確実に許可されるようにします。

## <a name="next-steps"></a>次の手順
- [アプリをグループに割り当てる](~/apps/apps-deploy.md)
