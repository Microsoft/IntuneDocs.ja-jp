---
title: "TeamViewer を使用してデバイスをリモート管理する方法"
titlesuffix: Azure portal
description: "TeamViewer を使用してデバイスをリモート管理する方法について説明します。"
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 12/14/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 72cdd888-efca-46e6-b2e7-fb9696bb2fba
ms.reviewer: davidra
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 46e850cdda27444d18354b972d10b0cd02c036d9
ms.sourcegitcommit: 000684953cbb3ceae0e2bcaa51186c9221f7aa86
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2017
---
# <a name="provide-remote-assistance-for-intune-managed-devices"></a>Intune で管理されたデバイスにリモート アシスタンスを提供する

Intune では、別売りの [TeamViewer](https://www.teamviewer.com) ソフトウェアを使って、管理対象のデバイスのユーザーにリモート アシスタンスを提供できます。 このトピックの情報を活用して作業を開始してください。

## <a name="before-you-start"></a>開始する前に

### <a name="supported-devices"></a>サポートされるデバイス

Intune で管理された Android デバイスと Windows デバイスでは、リモート管理がサポートされます。

>[!NOTE]
>Windows Holographic (HoloLens)、Windows Team (Surface Hub)、Windows 10 S は、TeamViewer ソフトウェアではサポートされません。 引き続き Intune クラシック ポータルの [PC クライアント](/intune-classic/deploy-use/pc-management-comparison?toc=/intune/toc.json)を使用して、デバイスを管理する必要があります。



### <a name="required-permissions"></a>必要なアクセス許可

Azure Portal のユーザーが [Intune ロール](https://docs.microsoft.com/intune-azure/access-control/role-based-access-control)として次のアクセス許可を割り当てられていることを確認します。
- 管理者が TeamViewer Connector の設定を変更できるようにするには、**リモート アシスタンスの更新**のアクセス許可を付与します。
- 管理者が新しいリモート アシスタンス要求を開始できるようにするには、**リモート アシスタンスの要求**のアクセス許可を付与します。 **リモート アシスタンスの要求**のアクセス許可を持つユーザーは、どのユーザーに対してもセッションの開始を要求できます。 Intune ロールの割り当てスコープによって制限されることはありません。 Intune のロールの割り当て範囲によって、リモート アシスタンス要求を開始できるデバイスやユーザーが制限されることはありません。

>[!NOTE]
>TeamViewer を有効にすると、Intune コネクタ用 TeamViewer での TeamViewer セッションの作成、Active Directory データの読み取り、TeamViewer アカウント アクセス トークンの保存を許可することになります。

### <a name="configure-the-intune-teamviewer-connector"></a>Intune TeamViewer Connector の構成

デバイスにリモート アシスタンスを提供する前に、以下の手順で Intune TeamViewer コネクタを構成する必要があります。


1. Azure Portal にサインインします。
2. **[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
3. **[Intune]** ブレードで、**[デバイス]** を選択します。
4. **[デバイスとグループ]** ブレードで、**[セットアップ]** > **[TeamViewer Connector]** の順に選択します。
5. **[TeamViewer Connector]** ブレードで、**[有効化]** をクリックし、TeamViewer サービス使用許諾契約書を表示して承認します。
6. **[TeamViewer にログインして承認する]** を選択します。
7. TeamViewer サイトの Web ページが開きます。 TeamViewer ライセンスの資格情報を入力し、**[サインイン]** をクリックします。


## <a name="how-to-remotely-administer-a-device"></a>デバイスのリモート管理方法

1. Azure Portal にサインインします。
2. **[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
3. **[Intune]** ブレードで、**[デバイス]** を選択します。
4. **[デバイス]** ブレードで、**[管理]** > **[すべてのデバイス]** の順に選択します。
5. リモート管理するデバイスを選択し、[デバイスのプロパティ] ブレードで **[詳細]** > **[新しいリモート アシスタンス セッション]** の順に選択します。
6. Intune を TeamViewer サービスに接続すると、デバイスの情報が表示されます。 **[接続]** を選択して、リモート セッションを開始します。

![Android の TeamViewer の例](./media/android-teamviewer.png)

TeamViewer ウィンドウで、さまざまなデバイスのリモート操作 (デバイスのリモート制御など) を行うことができます。 実行できる操作の詳細については、[TeamViewer のドキュメント](https://www.teamviewer.com/support/documents/)をご覧ください。

設定が完了したら、TeamViewer ウィンドウを閉じます。

## <a name="next-steps"></a>次の手順

デバイス上のポータル サイト アプリのアイコンに通知フラグが表示され、エンド ユーザーはアプリを開くと通知を確認できます。 その後、リモート アシスタンス要求を受け入れることができます。
