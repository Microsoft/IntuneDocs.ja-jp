---
title: "iOS のボリューム購入アプリの管理 | Microsoft Docs"
titlesuffix: Azure portal
description: "iOS ストアからボリューム購入したアプリを Intune に同期し、その使用状況を管理および追跡する方法について説明します。\""
keywords: 
author: erikre
ms.author: erikre
manager: angrobe
ms.date: 12/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 51d45ce2-d81b-4584-8bc4-568c8c62653d
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f820be41c532384f9f2db57e0e0e497a05307d73
ms.sourcegitcommit: 06abc5ccc8b868c9ff3ad3f8f62473a87b2da481
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2017
---
# <a name="how-to-manage-ios-apps-purchased-through-a-volume-purchase-program-with-microsoft-intune"></a>Volume Purchase Program で購入した iOS アプリを Microsoft Intune で管理する方法


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

iOS アプリ ストアでは、社内で実行するアプリの複数のライセンスを購入できます。 複数のコピーを購入すると、会社でのアプリ管理を効率的に行うことができます。

Microsoft Intune では、以下を行うことにより、このプログラムを通して購入されたアプリの複数のコピーを管理できます。

- アプリ ストアからライセンス情報を報告する。
- 使用しているライセンスの数を追跡記録する。
- 自分が所有している以上のアプリのコピーをインストールしないようにする。

ボリューム購入アプリを割り当てるには 2 つの方法があります。

### <a name="device-licensing"></a>デバイス ライセンス

デバイスにアプリを割り当てると、1 つのアプリ ライセンスが使用されて、割り当てたデバイスに関連付けられたままになります。

ボリューム購入アプリをデバイスに割り当てた場合、デバイスのエンド ユーザーは、ストアにアクセスするために Apple ID を指定する必要はありません。

### <a name="user-licensing"></a>ユーザー ライセンス

ユーザーにアプリを割り当てると、1 つのアプリ ライセンスが使われて、ユーザーに関連付けられます。 ユーザーが所有する複数のデバイスでアプリを実行できます (上限は Apple により制御)。

ボリューム購入アプリをユーザーに割り当てた場合、各エンド ユーザーは、アプリ ストアにアクセスするために一意の有効な Apple ID が必要です。

さらに、Apple ボリューム購入プログラム (VPP) ストアから購入した本と Intune との間で同期、管理、割り当てを行うことができます。 詳細については、「[Volume Purchase Program で購入した iOS 電子ブックを管理する方法](vpp-ebooks-ios.md)」を参照してください。

## <a name="manage-volume-purchased-apps-for-ios-devices"></a>iOS デバイス用のボリューム購入アプリの管理

### <a name="supports-apple-volume-purchase-program-volume-purchased-apps-for-ios-devices"></a>Apple Volume Purchase Program の iOS デバイス用のボリューム購入アプリをサポート

iOS アプリの複数のライセンスを[ビジネス向け Apple Volume Purchase Program](http://www.apple.com/business/vpp/) 経由または[教育向け Apple Volume Purchase Program](http://volume.itunes.apple.com/us/store) 経由で購入します。 このためには、Apple Web サイトから Apple VPP アカウントをセットアップし、Apple VPP トークンを Intune にアップロードする必要があります。  その後、ボリューム購入情報を Intune と同期し、ボリューム購入アプリの使用を追跡することができます。

### <a name="supports-business-to-business-volume-purchased-apps-for-ios-devices"></a>iOS デバイス用の企業間ボリューム購入アプリをサポート

また、サードパーティの開発者も、iTunes Connect に指定されているビジネス メンバーに、認められたボリューム購入プログラムにプライベートでアプリを配布できます。 VPP for Business のメンバーは、Volume Purchase Program App Store にサインインし、アプリを購入できます。 エンド ユーザーが購入した VPP for Business アプリはそのユーザーの Intune テナントに同期されます。

## <a name="before-you-start"></a>開始する前に
開始する前に、Apple から VPP トークンを取得し、それを Intune アカウントにアップロードする必要があります。 さらに、次の条件を理解する必要があります。

* 複数の VPP トークンを Intune アカウントに関連付けることができます。
* 以前に異なる製品で VPP トークンを使用していた場合は、Intune で使用するための新しい VPP トークンを生成する必要があります。
* 各トークンは、1 年間有効です。
* 既定では、Intune は 1 日に 2 回、Apple VPP サービスと同期します。 いつでも手動での同期を開始できます。
* Intune で Apple VPP を使い始める前に、他のモバイル デバイス管理 (MDM) ベンダーで作成された既存の VPP ユーザー アカウントを削除してください。 Intune では、セキュリティ対策として、そのようなユーザー アカウントは Intune と同期されません。 Intune では、Intune で作成された Apple VPP サービスからのデータのみが同期されます。
* Intune は最大 256 VPP トークンの追加をサポートしています。
* Apple の Device Enrollment Profile (DEP) プログラムは、モバイル デバイス管理 (MDM) 登録を自動化します。 DEP を利用すれば、触れることなく企業のデバイスを構成できます。 Apple の VPP で使用したものと同じプログラム エージェント アカウントを利用し、DEP プログラムに登録できます。 Apple 展開プログラム ID は [Apple 展開プログラム](https://deploy.apple.com) Web サイトに記載されているプログラムに固有であり、iTunes ストアなど、Apple サービスのログインには利用できません。
* ユーザー ライセンス モデルを利用する VPP アプリをユーザーまたは (ユーザー アフィニティのある) デバイスに割り当てるとき、デバイスで Apple の利用規約に同意するときのために、各 Intune ユーザーを一意の Apple ID またはメール アドレスに関連付ける必要があります。 新しい Intune ユーザーにデバイスを設定するとき、そのユーザーの一意の Apple ID またはメール アドレスで構成する必要があります。 Apple ID またはメール アドレスと Intune ユーザーで一意のペアを形成し、最大 5 台のデバイスで使用できます。
* VPP トークンは、一度に 1 つの Intune アカウントでのみ使用できます。 複数の Intune テナントに同じ VPP トークンを再利用することはしないでください。
* ユーザー ライセンス モデルを利用する VPP アプリをユーザーまたは (ユーザー アフィニティのある) デバイスに割り当てるとき、デバイスで Apple の利用規約に同意するときのために、各 Intune ユーザーを一意の Apple ID またはメール アドレスに関連付ける必要があります。
新しい Intune ユーザーにデバイスを設定するとき、そのユーザーの一意の Apple ID またはメール アドレスで構成する必要があります。 Apple ID またはメール アドレスと Intune ユーザーで一意のペアを形成し、最大 5 台のデバイスで使用できます。

>[!IMPORTANT]
>Intune に VPP トークンをインポートした後、同じトークンを他のデバイス管理ソリューションにインポートすることはできません。 これを行うと、ライセンスの割り当てとユーザー レコードが失われる恐れがあります。

## <a name="to-get-and-upload-an-apple-vpp-token"></a>Apple VPP トークンを取得およびアップロードするには

1. Azure Portal にサインインします。
2. **[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
1.  **[Intune]** ブレードで、**[セットアップ]** の **[モバイル アプリ]** > **[iOS VPP トークン]** を選択します。
2.  VPP トークンの一覧ブレードで、**[作成]** を選択します。
4. **[VPP トークンの作成]** ブレードで、次の情報を指定します。
    - **[VPP トークン ファイル]** - サインアップしていない場合は、ビジネス向け Volume Purchase Program または教育向けプログラムにサインアップします。 サインアップした後、アカウントの Apple VPP トークンをダウンロードし、ここで選択します。
    - **[Apple ID]** - Volume Purchase Program に関連付けられているアカウントの Apple ID を入力します。
    - **[Country/Region]\(国/地域\)** - VPP 国別ストアを選びます。  指定された VPP 国別ストアにある全ロケールに対応した VPP アプリが、Intune によって同期されます。
        > [!WARNING]  
        > 国を変更すると、このトークンで作成されたアプリが Apple サービスと次に同期するときに、アプリのメタデータとストアの URL が更新されます。 新しい国別ストアに存在しない場合、アプリは更新されません。

    - **[VPP アカウントの種類]** - **[ビジネス]** または **[教育]** を選択します。
    - **アプリの自動更新** - **[オン]** か **[オフ]** を選択し、自動更新を有効/無効にします。 有効にすると、Intune は、デバイスのチェックイン時に Intune サービスを介し、指定されたトークンに対象に購入されたすべてのアプリを更新します。
アプリ ストア内の VPP アプリ更新プログラムを検出し、デバイスのチェックイン時に自動的にデバイスにプッシュします。
4. 終了したら、**[アップロード]** を選択します。

トークンがトークンの一覧ブレードに表示されます。

**[今すぐ同期]** を選択すると、いつでも、Apple が保持しているデータと Intune を同期することができます。

## <a name="to-assign-a-volume-purchased-app"></a>ボリューム購入アプリを割り当てるには

1.  **[Intune]** ブレードの  > [管理]** で、**[モバイル アプリ]**、**[アプリ]** の順に選択します。
2.  アプリの一覧ブレードで、割り当てるアプリを選択し、**[割り当て]** を選択します。
3.  ***アプリの名前***  -  **[割り当て]** ブレードで **[グループの選択]** を選択し、**[グループの選択]** ブレードでアプリを割り当てる Azure AD ユーザーまたはデバイス グループを選択します。
5.  選択したグループごとに、次の設定を選択します。
    - **[種類]** - アプリが **[使用可能]** (エンド ユーザーは Intune ポータル サイトからアプリをインストールできます) か、**[必須]** (エンド ユーザーのデバイスにアプリが自動的にインストールされ) かを選びます。
    - **[ライセンスの種類]** - **[ユーザー ライセンス]** または **[デバイス ライセンス]** を選びます。
6.  完了したら、**[保存]** を選択します。


>[!NOTE]
>表示されるアプリの一覧はトークンに関連付けられます。 アプリが複数の VPP に関連付けられている場合、複数回表示されます。同じアプリがトークンごとに 1 回です。

## <a name="end-user-prompts-for-vpp"></a>VPP のエンド ユーザー プロンプト

エンド ユーザーには、さまざまなシナリオで VPP アプリ インストールのプロンプトが表示されます。 次の表は、各条件を説明したものです。

| # | 通信の種類                                | Apple VPP プログラムへの招待                              | アプリ インストールのプロンプト | Apple ID のプロンプト |
|---|--------------------------------------------------|-------------------------------------------------------------------------------------------------|---------------------------------------------|-----------------------------------|
| 1 | BYOD – ユーザー ライセンスあり                             | Y                                                                                               | Y                                           | Y                                 |
| 2 | Corp – ユーザー ライセンスあり (非監視対象デバイス)     | Y                                                                                               | Y                                           | Y                                 |
| 3 | Corp – ユーザー ライセンスあり (監視対象デバイス)         | Y                                                                                               | N                                           | Y                                 |
| 4 | BYOD – デバイス ライセンスあり                           | N                                                                                               | Y                                           | N                                 |
| 5 | CORP – デバイス ライセンスあり (非監視対象デバイス)                           | N                                                                                               | Y                                           | N                                 |
| 6 | CORP – デバイス ライセンスあり (監視対象デバイス)                           | N                                                                                               | N                                           | N                                 |
| 7 | キオスク モード (監視対象デバイス) – デバイス ライセンスあり | N                                                                                               | N                                           | N                                 |
| 8 | キオスク モード (監視対象デバイス) – ユーザー ライセンスあり   | --- | ---                                          | ---                                |

> [!Note]  
> VPP ユーザー ライセンスを使ってキオスク モード デバイスに VPP アプリを割り当てることは推奨されません。

## <a name="further-information"></a>詳細情報

ライセンスを再利用するには、割り当てアクションを **[アンインストール]** に変更する必要があります。 アプリをアンインストールすると、ライセンスは回収されます。 ユーザーに割り当てられたアプリを削除すると、Intune は、そのユーザーに関連付けられているすべてのアプリ ライセンスの回収を試行します。

<!-- 820879 -->You can delete a iOS Volume Purchasing Program (VPP) token using the console. This may be necessary when you have duplicate instances of a VPP token. Deleting a token will also delete any associated apps and assignment. However, deleting a token does not revoke app licenses. Intune cannot revoke app licenses after a token has been deleted. 

対象となるデバイスを持つユーザーが初めて VPP アプリをデバイスにインストールしようとすると、Apple Volume Purchase Program に参加するように求められます。 アプリのインストールを実行する前に、このプログラムに参加する必要があります。 Apple Volume Purchase Program への参加招待を行うには、ユーザーが iOS デバイスで iTunes アプリを使用できる必要があります。 iTunes Store アプリを無効にするようにポリシーを設定した場合、VPP アプリのユーザーベース ライセンスは機能しません。 この問題を解決するには、ポリシーを削除して iTunes アプリを許可するか、デバイス ベースのライセンスを使用します。

## <a name="next-steps"></a>次の手順

アプリの割り当てを監視するのに役立つ情報については、[アプリを監視する方法](apps-monitor.md)に関する記事を参照してください。
