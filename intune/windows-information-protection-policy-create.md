---
title: Windows 情報保護 (WIP) アプリ保護ポリシーを作成して展開する | Microsoft Intune
description: Microsoft Intune で Windows 情報保護 (WIP) アプリ保護ポリシーを作成して展開する
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4e3627bd-a9fd-49bc-b95e-9b7532f0ed55
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 57d0aaebd0ed07a78b32eec64a6dc2817bf5e7f5
ms.sourcegitcommit: bee072b61cf8a1b8ad8d736b5f5aa9bc526e07ec
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53817315"
---
# <a name="create-and-deploy-windows-information-protection-wip-app-protection-policy-with-intune"></a>Intune で Windows 情報保護 (WIP) アプリ保護ポリシーを作成して展開する

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Windows 10 アプリでアプリ保護ポリシーを使用して、デバイスを登録せずにアプリを保護できます。

## <a name="before-you-begin"></a>始める前に

WIP ポリシーを追加するときのいくつかの概念について理解する必要があります。

### <a name="list-of-allowed-and-exempt-apps"></a>許可されているアプリと適用から除外されるアプリの一覧

-   **[Protected apps]\(保護されたアプリ\)**:このポリシーに準拠する必要があるアプリです。

-   **[適用から除外されるアプリ]**:これらのアプリはこのポリシーから除外され、制限なしに企業データにアクセスできます。

### <a name="types-of-apps"></a>アプリの種類

-   **おすすめのアプリ:** ポリシーに簡単にインポートできるようにあらかじめ設定されている (ほとんどは Microsoft Office) アプリの一覧です。
-   **ストア アプリ:** Windows ストアからポリシーに任意のアプリを追加できます。
-   **Windows デスクトップ アプリ:** 従来の Windows デスクトップ アプリをポリシーに追加できます (exe、dll など)。

## <a name="prerequisites"></a>必要条件

WIP アプリ保護ポリシーを作成する前に、MAM プロバイダーを構成する必要があります。 [Intune で MAM プロバイダーを構成する方法](app-protection-policies-configure-windows-10.md)を理解します。  

> [!IMPORTANT]
> WIP は複数の ID をサポートしていません。存在できる管理対象 ID は一度に 1 つだけです。

さらに、次のライセンスと更新プログラムが必要です。

-   [Azure AD Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) ライセンス
-   [Windows Creators Update](https://blogs.windows.com/windowsexperience/2017/04/11/how-to-get-the-windows-10-creators-update/#o61bC2PdrHslHG5J.97)





## <a name="to-add-a-wip-app-protection-policy"></a>WIP アプリ保護ポリシーを追加するには

組織で Intune を設定した後は、WIP 固有のポリシーを作成できます。

> [!TIP]  
> 利用可能な設定とその構成方法を含む、Intune の WIP ポリシーの作成に関する情報については、Windows セキュリティ ドキュメント ライブラリの「[Azure Portal での Microsoft Intune を使用して MAM で Windows 情報保護 (WIP) ポリシーを作成する](https://docs.microsoft.com/windows/security/information-protection/windows-information-protection/create-wip-policy-using-mam-intune-azure)」を参照してください。 


1. [Azure ポータル](https://portal.azure.com)にサインインします。
2. **[すべてのサービス]** > **[Intune]** の順に選択します。
3. **[Microsoft Intune]** ブレードで **[クライアント アプリ]** を選択します。
4. **[クライアント アプリ]** ブレードで、**[アプリ保護ポリシー]** を選択します。
5. **[ポリシーの追加]** を選択して、**[ポリシーの追加]** ブレードを表示します。
6. 次の値を追加します。
    - **[名前]:**(必須) 新しいポリシーの名前を入力します。
    - **説明:**(省略可能) 説明を入力します。
    - **[プラットフォーム]:** アプリ保護ポリシーのサポート対象プラットフォームとして **[Windows 10]** を選択します。
    - **[登録の状態]:** ポリシーの登録状態として、**[未登録]** を選択します。
7.  [**作成**] を選択します。 ポリシーが作成されて、**[アプリ保護ポリシー]** ブレードのテーブルに表示されます。

## <a name="to-add-recommended-apps-to-your-protected-apps-list"></a>おすすめのアプリを保護されたアプリの一覧に追加するには

1. **[Microsoft Intune]** ブレードで **[クライアント アプリ]** を選択します。
2. **[クライアント アプリ]** ブレードで、**[アプリ保護ポリシー]** を選択します。
3. **[アプリ保護ポリシー]** ブレードで、変更するポリシーを選択します。 **[Intune App Protection]** ブレードが表示されます。
4. **[Intune App Protection]** ブレードで **[Protected apps]\(保護されたアプリ\)** を選択します。 **[Protected apps]\(保護されたアプリ\)** ブレードが開き、このアプリ保護ポリシーの一覧に既に含まれているすべてのアプリが表示されます。
5. **[アプリの追加]** を選択します。 **[アプリの追加]** の情報には、フィルターが適用されたアプリの一覧が表示されます。 ブレード上部の一覧では、一覧のフィルターを変更することができます。
6. 会社のデータへのアクセスを許可する各アプリを選択します。
7. **[OK]** をクリックします。 **[Protected apps]\(保護されたアプリ\)** ブレードが更新され、選択したすべてのアプリが表示されます。
8. **[Save]**(保存) をクリックします。

## <a name="add-a-store-app-to-your-protected-apps-list"></a>ストア アプリを保護されたアプリの一覧に追加する

**ストア アプリを追加するには**
1. **[Microsoft Intune]** ブレードで **[クライアント アプリ]** を選択します。
2. **[クライアント アプリ]** ブレードで、**[アプリ保護ポリシー]** を選択します。
3. **[アプリ保護ポリシー]** ブレードで、変更するポリシーを選択します。 **[Intune App Protection]** ブレードが表示されます。
4. **[Intune App Protection]** ブレードで **[Protected apps]\(保護されたアプリ\)** を選択します。 **[Protected apps]\(保護されたアプリ\)** ブレードが開き、このアプリ保護ポリシーの一覧に既に含まれているすべてのアプリが表示されます。
5. **[アプリの追加]** を選択します。 **[アプリの追加]** の情報には、フィルターが適用されたアプリの一覧が表示されます。 ブレード上部の一覧では、一覧のフィルターを変更することができます。
6. 一覧から **[ストア アプリ]** を選択します。
7. **[名前]**、**[公開元]**、**[製品名]**、**[アクション]** に値を入力します。 アプリが会社のデータにアクセスできるように、**[アクション]** の値を **[許可]** に設定してください。
9. **[OK]** をクリックします。 **[Protected apps]\(保護されたアプリ\)** ブレードが更新され、選択したすべてのアプリが表示されます。
10. **[Save]**(保存) をクリックします。

## <a name="add-a-desktop-app-to-your-protected-apps-list"></a>デスクトップ アプリを保護されたアプリの一覧に追加する

**デスクトップ アプリを追加するには**
1. **[Microsoft Intune]** ブレードで **[クライアント アプリ]** を選択します。
2. **[クライアント アプリ]** ブレードで、**[アプリ保護ポリシー]** を選択します。
3. **[アプリ保護ポリシー]** ブレードで、変更するポリシーを選択します。 **[Intune App Protection]** ブレードが表示されます。
4. **[Intune App Protection]** ブレードで **[Protected apps]\(保護されたアプリ\)** を選択します。 **[Protected apps]\(保護されたアプリ\)** ブレードが開き、このアプリ保護ポリシーの一覧に既に含まれているすべてのアプリが表示されます。
5. **[アプリの追加]** を選択します。 **[アプリの追加]** の情報には、フィルターが適用されたアプリの一覧が表示されます。 ブレード上部の一覧では、一覧のフィルターを変更することができます。
6. 一覧から **[デスクトップ アプリ]** を選択します。
7. **[名前]**、**[公開元]**、**[製品名]**, **[ファイル]**、**[最小バージョン]**、**[最大バージョン]**、**[アクション]** に値を入力します。 アプリが会社のデータにアクセスできるように、**[アクション]** の値を **[許可]** に設定してください。
9. **[OK]** をクリックします。 **[Protected apps]\(保護されたアプリ\)** ブレードが更新され、選択したすべてのアプリが表示されます。
10. **[Save]**(保存) をクリックします。

## <a name="wip-learning"></a>WIP の学習
WIP で保護するアプリを追加した後は、**[WIP の学習]** を使って保護モードを適用する必要があります。

### <a name="before-you-begin"></a>始める前に

WIP の学習は、WIP が有効なアプリおよび WIP にとって不明なアプリを監視できるようにするレポートです。 不明アプリは、組織の IT 部門によって展開されていないアプリです。 "ブロック" モードで WIP を適用する前に、レポートからこのようなアプリをエクスポートして WIP ポリシーに追加することで、生産性の阻害を回避できます。

<!-- 1631908 --> WIP が有効になっているアプリの情報を表示できるだけでなく、作業データを Web サイトで共有しているデバイスの概要も表示できます。 この情報を使用して、グループおよびユーザーの WIP ポリシーに追加する Web サイトを判断できます。 概要には、WIP が有効なアプリからアクセスされる Web サイトの URL が示されます。

WIP が有効なアプリおよび WIP にとって不明なアプリを使用する場合は、まず、**[サイレント]** または **[オーバーライドの許可]** を使用し、保護されたアプリの一覧に適切なアプリが含まれる小規模なグループで確認することをお勧めします。 それが済んだ後、最終的な適用ポリシーである **[ブロック]** に変更できます。

### <a name="what-are-the-protection-modes"></a>保護モードの種類

#### <a name="block"></a>ブロック
WIP は不適切なデータ共有行為を検索し、ユーザーが操作を完了できないようにします。 ブロック対象のアクションには、会社で保護されていないアプリ間での情報の共有や、組織外の他のユーザーやデバイス間での企業データの共有などが含まれます。

#### <a name="allow-overrides"></a>オーバーライドの許可
WIP は不適切なデータ共有を検索し、ユーザーが危険なことを行うと警告します。 ただし、このモードでは、ユーザーはポリシーをオーバーライドしてデータを共有することができ、その操作は監査ログに記録されます。

#### <a name="silent"></a>サイレント
WIP はサイレントで実行し、不適切なデータ共有をログに記録します。"オーバーライドの許可" モードで従業員にメッセージが表示される行為もブロックしません。 ネットワーク リソースや WIP で保護されたデータへのアプリによる不適切なアクセスの試みなど、許可されていない操作は停止されます。

#### <a name="off-not-recommended"></a>オフ (非推奨)
WIP は無効になり、データの保護または監査には役立ちません。

WIP を無効にすると、ローカルに接続されたドライブ上の WIP でタグ付けされたファイルを復号化する試みが行われます。 WIP 保護を有効に戻しても、以前の復号化およびポリシーの情報は自動的に再適用されないことに注意してください。

### <a name="add-a-protection-mode"></a>保護モードを追加する

1.  **[アプリに関するポリシー]** ブレードでポリシーの名前を選び、**[必須の設定]** を選びます。

    ![[学習モード] ウィンドウのスクリーンショット](./media/learning-mode-sc1.png)

1.  設定を選択して、**[保存]** を選びます。

### <a name="use-wip-learning"></a>WIP の学習を使用する

1. [Azure Portal](https://portal.azure.com) を開きます。 **[すべてのサービス]** を選択します。 テキスト ボックス フィルターに「**Intune**」と入力します。

3. **[Intune]** > **[クライアント アプリ]** の順に選択します。

4. **[アプリの保護状態]** > **[レポート]** > **[Windows 情報保護の学習]** の順に選択します。  

    WIP の学習のログ レポートにアプリが表示されたら、それをアプリ保護ポリシーに追加できます。

## <a name="allow-windows-search-indexer-to-search-encrypted-items"></a>暗号化されたアイテムの検索を Windows Search Indexer に許可する
アイテムのインデックス作成を許可または禁止します。 これは Windows Search Indexer 用のスイッチです。Windows 情報保護 (WIP) で保護されたファイルなど、暗号化されたアイテムにインデックスを付けるかどうかを制御します。

このアプリの保護ポリシー オプションは、Windows 情報保護ポリシーの **[詳細設定]** にあります。 アプリの保護ポリシーは、*[Windows 10]* プラットフォームに設定し、アプリ ポリシーの **[登録状態]** は **[登録済み]** に設定する必要があります。

このポリシーが有効な場合、WIP で保護されたアイテムにインデックスが付けられ、それらのメタデータは暗号化されていない場所に保存されます。 メタデータには、ファイル パスや変更日などがあります。

このポリシーが無効な場合、WIP で保護されたアイテムにはインデックスが付けられず、Cortana またはエクスプローラーの結果に表示されません。 また、デバイスに WIP で保護されたメディア ファイルが多数ある場合は、写真や Groove アプリのパフォーマンスにも影響が出る可能性があります。

## <a name="add-encrypted-file-extensions"></a>暗号化されたファイルの拡張子を追加する

**[Allow Windows Search Indexer to search encrypted items]\(暗号化されたアイテムの検索を Windows Search Indexer に許可する\)** オプションの設定に加え、ファイル拡張子の一覧を指定することができます。 これらの拡張子を持つファイルは、ネットワークの場所一覧で定義されている会社の境界内のサーバー メッセージ ブロック (SMB) 共有からコピーするときに暗号化されます。 このポリシーを指定しない場合、既存の自動暗号化動作が適用されます。 このポリシーを構成すると、一覧内の拡張子を持つファイルのみが暗号化されます。

## <a name="deploy-your-wip-app-protection-policy"></a>WIP アプリ保護ポリシーを展開する

> [!IMPORTANT]
> この情報はデバイス登録なしの WIP に適用されます。

<!---not sure why you need the Important note. Isn't this what the topic is about? app protection w/o enrollment?--->

WIP アプリ保護ポリシーを作成した後、MAM を使ってポリシーを組織に展開する必要があります。

1.  **[アプリに関するポリシー]** ブレードで新しく作成したアプリ保護ポリシーを選択し、**[ユーザー グループ]**、**[ユーザー グループの追加]** の順に選択します。

    Azure Active Directory 内のすべてのセキュリティ グループで構成されるユーザー グループの一覧が、**[ユーザー グループの追加]** ブレードで開きます。

2.  ポリシーを適用するグループを選び、**[選択]** を選んでポリシーを展開します。

## <a name="next-steps"></a>次の手順

Windows 情報保護の詳細については、「[Protect your enterprise data using Windows Information Protection (WIP)](https://docs.microsoft.com/windows/security/information-protection/windows-information-protection/protect-enterprise-data-using-wip)」(Windows 情報保護 (WIP) を使用してエンタープライズ データを保護する) を参照してください。
