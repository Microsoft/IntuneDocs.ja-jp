---
title: Microsoft Intune - Azure でデバイスをリモートで管理する | Microsoft Docs
description: TeamViewer を使用するために必要なロールの表示、TeamViewer コネクタのインストール方法、Azure Portal で Microsoft Intune を使用してデバイスをリモートで管理する方法の段階的なガイダンス
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/12/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 72cdd888-efca-46e6-b2e7-fb9696bb2fba
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 7cb7c23e673c9e0c074f45991333fde9bfc8e930
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2018
ms.locfileid: "52186190"
---
# <a name="use-teamviewer-to-remotely-administer-intune-devices"></a>TeamViewer を使用して、Intune デバイスをリモートで管理する

Intune で管理されているデバイスは、[TeamViewer](https://www.teamviewer.com) を使用してリモートで管理できます。 TeamViewer は、個別に購入するサード パーティ プログラムです。 このトピックでは、Intune 内で TeamViewer を構成して、リモートでデバイスを管理する方法を示します。 

## <a name="prerequisites"></a>必要条件

- サポートされているデバイスを使用します。 Intune で管理された Android デバイス、Windows デバイス、iOS デバイス、macOS デバイスでは、リモート管理がサポートされます。 TeamViewer で Windows Holographic (HoloLens)、Windows Team (Surface Hub)、または Windows 10 S がサポートされない場合があります。サポートについては、[TeamViewer](https://www.teamviewer.com) で更新情報を確認してください。

- Azure Portal 内の Intune 管理者には、次の [Intune ロール](role-based-access-control.md)が必要です。  

    - **リモート アシスタンスの更新**: 管理者に TeamViewer コネクタの設定の変更を許可します。
    - **リモート アシスタンスの要求**: 管理者にすべてのユーザーに対して新しいリモート アシスタンス セッションを開始することを許可します。 このロールを持つユーザーは、スコープ内のどの Intune ロールにも制限されません。 また、スコープ内で Intune ロールが割り当てられたユーザーまたはデバイス グループも、リモート アシスタンスを要求することができます。 

- サインイン資格情報を持つ [TeamViewer](https://www.teamviewer.com) アカウント

TeamViewer を使用すると、Intune コネクタ用 TeamViewer での TeamViewer セッションの作成、Active Directory データの読み取り、TeamViewer アカウント アクセス トークンの保存を許可することになります。

## <a name="configure-the-teamviewer-connector"></a>TeamViewer コネクタの構成

デバイスにリモート アシスタンスを提供するには、以下の手順で Intune TeamViewer コネクタを構成します。

1. [Azure Portal](https://portal.azure.com) で、**[すべてのサービス]** を選択し、**Microsoft Intune** を検索します。
2. **Microsoft Intune** で、**[デバイス]**、**[TeamViewer Connector]** の順に選択します。
3. **[接続]** を選択し、使用許諾契約書に同意します。
4. **[TeamViewer にログインして承認する]** を選択します。
5. TeamViewer サイトの Web ページが開きます。 TeamViewer ライセンスの資格情報を入力して、**サインイン**します。

## <a name="remotely-administer-a-device"></a>デバイスをリモートで管理する

コネクタを構成したら、デバイスをリモートで管理する準備ができました。 次の手順を使用します。 

1. [Azure Portal](https://portal.azure.com) で、**[すべてのサービス]** を選択し、**Microsoft Intune** を検索します。
2. **Microsoft Intune** で、**[デバイス]**、**[すべてのデバイス]** の順に選択します。
3. リストから、リモートで管理するデバイスを選択します。 デバイスのプロパティで、**[新しいリモート アシスタンス セッション]** を選択します。
4. Intune を TeamViewer サービスに接続すると、デバイスの情報が表示されます。 **接続**してリモート セッションを開始します。

![TeamViewer を使用して Android デバイスをリモート管理する - 例](./media/android-teamviewer.png)

リモート セッションを開始すると、ユーザーのデバイス上で、ポータル サイト アプリのアイコンに通知フラグが表示されます。 通知は、アプリを開いたときにも表示されます。 これで、ユーザーはリモート アシスタンス要求を受け入れられるようになります。

> [!NOTE]
> DEM や WCD など、"ユーザーレス" メソッドを使用して登録された Windows デバイスの場合、ポータル サイト アプリに TeamViewer 通知が表示されません。 このようなシナリオでは、TeamViewer ポータルを使用してセッションを生成することをお勧めします。

TeamViewer では、デバイスの制御など、デバイスでさまざまな操作を完了できます。 実行できる操作の詳細については、[TeamViewer ガイダンス](https://www.teamviewer.com/support/documents/)を参照してください。

完了したら、TeamViewer ウィンドウを閉じます。
