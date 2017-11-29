---
title: "Intune で Windows 情報保護 (WIP) アプリ保護ポリシーを作成して展開する"
titlesuffix: Azure portal
description: "Intune で WIP アプリ保護ポリシーを作成して展開します"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 11/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4e3627bd-a9fd-49bc-b95e-9b7532f0ed55
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ab0456b58704f17d3dc5885ab5ae6b902c9ef152
ms.sourcegitcommit: dc2595bec05206a826cd10cb834bf6043145c917
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/14/2017
---
# <a name="create-and-deploy-windows-information-protection-wip-app-protection-policy-with-intune"></a>Intune で Windows 情報保護 (WIP) アプリ保護ポリシーを作成して展開する

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune 1704 リリース以降では、Windows 10 でアプリ保護ポリシーを使用して、デバイスを登録せずにアプリを保護できます。

## <a name="before-you-begin"></a>始める前に

WIP ポリシーを追加するときのいくつかの概念について説明します。

### <a name="list-of-allowed-and-exempt-apps"></a>許可されているアプリと適用から除外されるアプリの一覧

-   **[許可されているアプリ]**: このポリシーに準拠する必要があるアプリです。

-   **[適用から除外されるアプリ]**: これらのアプリはこのポリシーから除外され、制限なしに企業データにアクセスできます。

### <a name="types-of-apps"></a>アプリの種類

-   **おすすめのアプリ:** ポリシーに簡単にインポートできるようにあらかじめ設定されている (ほとんどは Microsoft Office) アプリの一覧です。 <!---I really don't know what you mean by "easily import into policy"--->

-   **ストア アプリ:** Windows ストアからポリシーに任意のアプリを追加できます。

-   **Windows デスクトップ アプリ:** 従来の Windows デスクトップ アプリをポリシーに追加できます (exe、dll など)。

## <a name="pre-requisites"></a>前提条件

WIP アプリ保護ポリシーを作成する前に、MAM プロバイダーを構成する必要があります。 [Intune で MAM プロバイダーを構成する方法](https://docs.microsoft.com/app-protection-policies-configure-windows-10.md)を理解します。

さらに、次のものが必要です。

-   [Azure AD Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) ライセンス。
-   [Windows Creators Update](https://blogs.windows.com/windowsexperience/2017/04/11/how-to-get-the-windows-10-creators-update/#o61bC2PdrHslHG5J.97)

> [!IMPORTANT]
> WIP は複数の ID をサポートしていません。存在できる管理対象 ID は一度に 1 つだけです。
<!---Should you be linking to a topic that explains what multi-identity is?--->

## <a name="to-add-a-wip-policy"></a>WIP ポリシーを追加するには

組織で Intune を設定した後は、[Azure Portal](https://docs.microsoft.com/intune-classic/deploy-use/azure-portal-for-microsoft-intune-mam-policies) を使用して WIP 固有のポリシーを作成できます。 <!---Is there an azure topic you can use instead of a classic? if not, should this topic be moved into the azure docset?--->

1.  **Intune モバイル アプリケーション管理ダッシュボード**に移動し、**[すべての設定]** > **[アプリに関するポリシー]** を選択します。

2.  **[アプリに関するポリシー]** ブレードで **[ポリシーの追加]** を選び、次の値を入力します。

    a.  **[名前]:** (必須) 新しいポリシーの名前を入力します。

    b.  **[説明]:** 必要に応じて説明を入力します。

    c.  **[プラットフォーム]:** アプリ保護ポリシーのサポート対象プラットフォームとして **[Windows 10]** を選択します。

    d.  **[登録の状態]:** ポリシーの登録状態として、**[未登録]** を選択します。

3.  **[作成]** を選択します。 ポリシーが作成されて、**[アプリに関するポリシー]** ブレードのテーブルに表示されます。

## <a name="to-add-recommended-apps-to-your-allowed-apps-list"></a>許可されているアプリの一覧におすすめのアプリを追加するには

1.  **[アプリに関するポリシー]** ブレードでポリシーの名前を選び、**[ポリシーの追加]** ブレードで **[許可されているアプリ]** を選びます。 **[許可されているアプリ]** ブレードが開き、このアプリ保護ポリシーの一覧に既に含まれているすべてのアプリが表示されます。

2.  **[許可されているアプリ]** ブレードで、**[アプリの追加]** を選択します。 **[アプリの追加]** ブレードが開き、この一覧に含まれるすべてのアプリが表示されます。

3.  企業データへのアクセスを許可する各アプリを選択し、**[OK]** を選択します。 **[許可されているアプリ]** ブレードが更新され、選択したすべてのアプリが表示されます。

## <a name="add-a-store-app-to-your-allowed-apps-list"></a>許可されているアプリの一覧にストア アプリを追加する

**ストア アプリを追加するには**

1.  **[アプリに関するポリシー]** ブレードで、ポリシーの名前を選び、このアプリ保護ポリシーの一覧に既に含まれているすべてのアプリが表示されるメニューから **[許可されているアプリ]** を選びます。

2.  **[許可されているアプリ]** ブレードで、**[アプリの追加]** を選択します。

3.  **[アプリの追加]** ブレードで、ドロップダウン リストから **[ストア アプリ]** を選択します。 ブレードが変化し、**パブリッシャー**とアプリの**名前**を追加するためのボックスが表示されます。

4.  アプリの名前とパブリッシャーの名前を入力し、**[OK]** を選択します。

    > [!TIP]
    > たとえば、**パブリッシャー**には「*CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US*」と、製品の**名前**には「*Microsoft.MicrosoftAppForWindows*」と入力します。

5.  フィールドに情報を入力した後、**[OK]** を選択して **[許可されているアプリ]** の一覧にアプリを追加します。

> [!NOTE]
> 同時に複数のストア アプリを追加するには、アプリ行の末尾にあるメニュー **[...]** をクリックし、アプリの追加を続けます。 終了したら、**[OK]** を選択します。

## <a name="add-a-desktop-app-to-your-allowed-apps-list"></a>許可されているアプリの一覧にデスクトップ アプリを追加する

**デスクトップ アプリを追加するには**

1.  **[アプリに関するポリシー]** ブレードでポリシーの名前を選び、**[許可されているアプリ]** を選びます。 **[許可されているアプリ]** ブレードが開き、このアプリ保護ポリシーの一覧に既に含まれているすべてのアプリが表示されます。

2.  **[許可されているアプリ]** ブレードで、**[アプリの追加]** を選択します。

3.  **[アプリの追加]** ブレードで、ドロップダウン リストから **[デスクトップ アプリ]** を選択します。

4.  フィールドに情報を入力した後、**[OK]** を選択して **[許可されているアプリ]** の一覧にアプリを追加します。

> [!NOTE]
> 同時に複数の**デスクトップ アプリ**を追加するには、アプリ行の末尾にあるメニュー **[...]** をクリックし、アプリの追加を続けます。 終了したら、**[OK]** を選択します。

## <a name="wip-learning"></a>WIP の学習
<!---You've already defined WIP earlier in the topic. You don't need to keep doing so. --->
WIP で保護するアプリを追加した後は、**[WIP の学習]** を使って保護モードを適用する必要があります。

### <a name="before-you-begin"></a>始める前に

WIP の学習は、WIP にとって不明なアプリを監視できるようにするレポートです。 不明アプリは、組織の IT 部門によって展開されていないアプリです。 "ブロック" モードで WIP を適用する前に、レポートからこのようなアプリをエクスポートして WIP ポリシーに追加することで、生産性の阻害を回避できます。

最初は **[サイレント]** または **[上書きの許可]** を使用し、許可されているアプリの一覧に適切なアプリが含まれる小規模なグループで確認することをお勧めします。 それが済んだ後、最終的な適用ポリシーである **[ブロック]** に変更できます。

### <a name="what-are-the-protection-modes"></a>保護モードの種類

#### <a name="block"></a>ブロック
WIP は不適切なデータ共有行為を検索し、ユーザーが操作を完了できないようにします。 これには、会社で保護されていないアプリ間での情報の共有や、組織外の他のユーザーやデバイス間での会社データの共有などが含まれます。

#### <a name="allow-overrides"></a>上書きの許可
WIP は不適切なデータ共有を検索し、ユーザーが危険なことを行うと警告します。 ただし、このモードでは、ユーザーはポリシーを上書きしてデータを共有することができ、その操作は監査ログに記録されます。

#### <a name="silent"></a>サイレント
WIP はサイレントで実行し、不適切なデータ共有をログに記録します。"上書きの許可" モードで従業員にメッセージが表示される行為もブロックしません。 ネットワーク リソースや WIP で保護されたデータへのアプリによる不適切なアクセスの試みなど、許可されていない操作は停止されます。

#### <a name="off-not-recommended"></a>オフ (非推奨)
WIP は無効になり、データの保護または監査には役立ちません。

WIP を無効にすると、ローカルに接続されたドライブ上の WIP でタグ付けされたファイルを復号化する試みが行われます。 WIP 保護を有効に戻しても、以前の復号化およびポリシーの情報は自動的に再適用されないことに注意してください。

### <a name="add-a-protection-mode"></a>保護モードを追加する

1.  **[アプリに関するポリシー]** ブレードでポリシーの名前を選び、**[必須の設定]** を選びます。

    ![学習モードのスクリーンショット](./media/learning-mode-sc1.png)

1.  **[保存]** を選びます。

### <a name="use-wip-learning"></a>WIP の学習を使用する

1. Azure ポータルを開きます。 **[その他のサービス]** を選択します。 テキスト ボックス フィルターに「**Intune**」と入力します。

3. **[Intune]**、**[モバイル アプリ]** の順に選択します。

4. **[アプリの保護状態]** > **[レポート]** > **[Windows 情報保護の学習]** の順に選択します。  
 
    WIP の学習のログ レポートにアプリが表示されたら、それをアプリ保護ポリシーに追加できます。

## <a name="deploy-your-wip-app-protection-policy"></a>WIP アプリ保護ポリシーを展開する

> [!IMPORTANT]
> これはデバイス登録なしの WIP に適用されます。

<!---not sure why you need the Important note. Isn't this what the topic is about? app protection w/o enrollment?--->

WIP アプリ保護ポリシーを作成した後、MAM を使ってポリシーを組織に展開する必要があります。

1.  **[アプリに関するポリシー]** ブレードで新しく作成したアプリ保護ポリシーを選択し、**[ユーザー グループ]**、**[ユーザー グループの追加]** の順に選択します。

    Azure Active Directory 内のすべてのセキュリティ グループで構成されるユーザー グループの一覧が、**[ユーザー グループの追加]** ブレードで開きます。

1.  ポリシーを適用するグループを選び、**[選択]** を選んでポリシーを展開します。
