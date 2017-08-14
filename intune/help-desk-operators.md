---
title: "ヘルプ デスクのトラブルシューティング ポータル"
titleSuffix: Intune on Azure
description: "ヘルプ デスクのスタッフが、トラブルシューティング ポータルを使用して、ユーザーの技術的な問題を解決する"
keywords: 
author: NathBarn
ms.author: NathBarn
manager: angrobe
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1f39c02a-8d8a-4911-b4e1-e8d014dbce95
ms.reviewer: sumitp
ms.custom: intune-azure
ms.openlocfilehash: 7aad054f0861522174faa01b979083a818c106af
ms.sourcegitcommit: 79116d4c7f11bafc7c444fc9f5af80fa0b21224e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2017
---
# <a name="help-users-with-the-troubleshooting-portal-in-microsoft-intune"></a>Microsoft Intune のトラブルシューティング ポータルでユーザーをサポートする

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

トラブルシューティング ポータルでは、ヘルプ デスクと Intune の管理者が、ユーザーのヘルプ要求の解決のためにユーザー情報を表示することができます。 スタッフ内にヘルプ デスクが含まれる組織は、**[ヘルプ デスク]** をユーザーのグループに割り当てることができます。これにより、ヘルプ デスクは [トラブルシューティング] のブレードを使用してユーザーのサポートができるようになります。

たとえば、ユーザーが Intune で技術的な問題をサポートに連絡すると、ヘルプ デスクがそのユーザーの名前を入力します。 Intune には、次のような階層 1 の多くの問題を解決するのに役立つデータが示されます。
- ユーザーの状態
- ［割り当て］
- アプリのインスタンス エラー
- ポリシー準拠の問題
- デバイスが応答しない
-   デバイスが VPN または Wi-Fi の設定を取得できない
-   アプリのインストールの失敗


## <a name="add-help-desk-operators"></a>ヘルプ デスクの追加
Intune 管理者は、ユーザー グループに [ヘルプ デスク] のロールを割り当てることができます。 そのグループのメンバーは管理ポータルを使用して、ユーザーの問題をトラブルシューティングすることができます。 ヘルプ デスクには、それぞれ Intune ポータルにアクセスするための Intune のライセンスが必要です。 Intune のライセンスを割り当てる方法については、[こちら](licenses-assign.md)を参照してください。

ヘルプ デスク ユーザーを追加するには
1. 必要に応じて、[Intune にユーザーを追加します](users-add.md)。
2. [ヘルプ デスク グループを作成](groups-add.md)して、ユーザーをグループに追加します。
3. [RBAC ヘルプ デスク オペレーターのロールを割り当てる](role-based-access-control.md#built-in-roles)か、以下のアクセス許可を持つ[カスタム ロールを作成](role-based-access-control.md#custom-roles)します。
  - MobileApps: 読み取り
  - ManagedApps: 読み取り
  - ManagedDevices: 読み取り
  - Organization: 読み取り
  - DeviceCompliancePolices: 読み取り
  - DeviceConfigurations: 読み取り

  ![[Intune の役割] の強調表示および [ヘルプ デスク] を含む組み込みのロールの一覧が示されている Intune ポータルのスクリーンショット](./media/help-desk-user-add.png)

4. サービスの正常性を確認し、Intune のサポート チケットを開くためのヘルプ デスク オペレーターのアクセス許可を与えるには、**サービス管理者**としての[管理者アクセス許可をユーザーに付与](https://docs.microsoft.com/azure/active-directory/active-directory-users-assign-role-azure-portal)します。 このディレクトリ ロールには、ヘルプ デスク オペレーターで必要とされる以上のアクセス許可があるため、**Intune サービス管理者**のアクセス許可は与えないでください。

## <a name="access-the-troubleshooting-portal"></a>トラブルシューティング ポータルにアクセスする

ヘルプ デスクのスタッフや Intune 管理者は、2 つの方法でトラブルシューティング ポータルにアクセスできます。
- Web ブラウザーで [http://aka.ms/intunetroubleshooting](http://aka.ms/intunetroubleshooting) を開き、トラブルシューティング ポータルのみを表示します。
  ![トラブルシューティング コンソールのスクリーン ショット](./media/help-desk-console.png)
- Azure ポータルにサインインして、**[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択し、**[ヘルプとサポート]** > **[トラブルシューティング]** の順に移動します。

**[ユーザーの選択]** をクリックして、ユーザーとそのユーザーの詳細を表示します。

![Intune のトラブルシューティング ワークロードとユーザー選択リンクのスクリーンショット](media/help-desk-user.png)

## <a name="use-the-troubleshooting-portal"></a>トラブルシューティング ポータルを使用する

トラブルシューティング ポータルでは、**[ユーザーの選択]** を選択して、ユーザーの情報を表示できます。 ユーザー情報は、ユーザーと彼らのデバイスの現在の状態を理解するのに役立ちます。 トラブルシューティング ポータルでは、トラブルシューティングに関する以下の詳細が表示されます。
- **アカウントの状態**
- **ユーザーの状態**
- **デバイス**とデバイス アクション
- **グループのメンバーシップ**
- **アプリの保護の状態**
