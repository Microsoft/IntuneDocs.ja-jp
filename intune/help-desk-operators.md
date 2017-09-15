---
title: "ヘルプ デスクのトラブルシューティング ポータル"
titlesuffix: Azure portal
description: "ヘルプ デスクのスタッフが、トラブルシューティング ポータルを使用して、ユーザーの技術的な問題を解決する"
keywords: 
author: NathBarn
ms.author: NathBarn
manager: angrobe
ms.date: 08/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1f39c02a-8d8a-4911-b4e1-e8d014dbce95
ms.reviewer: sumitp
ms.custom: intune-azure
ms.openlocfilehash: 14b47727428fcd6a16f9960e21f70ee64c7757d1
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/09/2017
---
# <a name="use-the-troubleshooting-portal-to-help-users"></a>トラブルシューティング ポータルを使用してユーザーをサポートする

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

トラブルシューティング ポータルでは、ヘルプ デスクのオペレーターや Intune の管理者が、ユーザーのヘルプ要求に対処するためにユーザー情報を表示することができます。 スタッフ内にヘルプ デスクが含まれる組織は、**[ヘルプ デスク]** をユーザーのグループに割り当てることができます。これにより、ヘルプ デスクは [トラブルシューティング] のブレードを使用してユーザーのサポートができるようになります。

たとえば、ユーザーが Intune で技術的な問題をサポートに連絡すると、ヘルプ デスクがそのユーザーの名前を入力します。 Intune には、次のような階層 1 の多くの問題を解決するのに役立つデータが示されます。
- ユーザーの状態
- ［割り当て］
- ポリシー準拠の問題
- デバイスが応答しない
-   デバイスが VPN または Wi-Fi の設定を取得できない
-   アプリのインストールの失敗

## <a name="add-help-desk-operators"></a>ヘルプ デスクの追加
Intune 管理者は、ユーザー グループに [ヘルプ デスク] のロールを割り当てることができます。 そのグループのメンバーは Azure Portal を使用して、ユーザーの問題をトラブルシューティングすることができます。 ヘルプ デスク オペレーターには、それぞれ Azure Portal にアクセスするための Intune のライセンスが必要です。 Intune のライセンスを割り当てる方法については、[こちら](licenses-assign.md)を参照してください。

ヘルプ デスク ユーザーを追加するには
1. 必要に応じて、[Intune にユーザーを追加します](users-add.md)。
2. [ヘルプ デスク グループを作成](groups-add.md)して、ユーザーをグループに追加します。
3. [RBAC ヘルプ デスク オペレーターのロールを割り当てます](role-based-access-control.md#built-in-roles)。

  ![Intune ロールが強調表示され、ヘルプ デスク オペレーターなどの組み込みロールの一覧を示す Azure Portal のスクリーンショット](./media/help-desk-user-add.png) ヘルプ デスクのオペレーターにアクセス権を付与するようにさらに変更できる、[カスタム ロールを作成する](role-based-access-control.md#custom-roles)こともできます。  ヘルプ デスクのオペレーターは、ユーザーの問題のトラブルシューティングをサポートするために、次のアクセス許可が必要です。
    - MobileApps: 読み取り
    - ManagedApps: 読み取り
    - ManagedDevices: 読み取り
    - Organization: 読み取り
    - DeviceCompliancePolices: 読み取り
    - DeviceConfigurations: 読み取り

4. サービスの正常性を確認し、Intune のサポート チケットを開くためのヘルプ デスク オペレーターのアクセス許可を与えるには、**サービス管理者**としての[管理者アクセス許可をユーザーに付与](https://docs.microsoft.com/azure/active-directory/active-directory-users-assign-role-azure-portal)します。 このディレクトリ ロールには、ヘルプ デスク オペレーターで必要とされる以上のアクセス許可があるため、**Intune サービス管理者**のアクセス許可は与えないでください。

## <a name="access-the-troubleshooting-portal"></a>トラブルシューティング ポータルにアクセスする

ヘルプ デスクのスタッフや Intune 管理者は、2 つの方法でトラブルシューティング ポータルにアクセスできます。
- Web ブラウザーで [http://aka.ms/intunetroubleshooting](http://aka.ms/intunetroubleshooting) を開き、トラブルシューティング ポータルのみを表示します。
  ![トラブルシューティング コンソールのスクリーン ショット](./media/help-desk-console.png)
- Azure ポータルにサインインして、**[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択し、**[ヘルプとサポート]** > **[トラブルシューティング]** の順に移動します。

**[ユーザーの選択]** をクリックして、ユーザーとそのユーザーの詳細を表示します。

## <a name="use-the-troubleshooting-portal"></a>トラブルシューティング ポータルを使用する

トラブルシューティング ポータルでは、**[ユーザーの選択]** を選択して、ユーザーの情報を表示できます。 ユーザー情報は、ユーザーと彼らのデバイスの現在の状態を理解するのに役立ちます。 トラブルシューティング ポータルでは、トラブルシューティングに関する以下の詳細が表示されます。
- **アカウントの状態**
- **ユーザーの状態**
- **デバイス**とデバイス アクション
- **グループのメンバーシップ**
- **アプリの保護の状態**
