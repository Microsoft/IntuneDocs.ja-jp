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
ms.openlocfilehash: 7a61c3703cd1016ef63c8baa371c3a21dca127fc
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2017
---
# <a name="help-users-with-the-troubleshooting-portal-in-microsoft-intune"></a>Microsoft Intune のトラブルシューティング ポータルでユーザーをサポートする

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

トラブルシューティング ポータルでは、ヘルプ デスクと Intune の管理者が、ユーザーのヘルプ要求の解決のためにユーザー情報を表示することができます。 スタッフ内にヘルプ デスクが含まれる組織は、**[ヘルプ デスク]** をユーザーのグループに割り当てることができます。これにより、ヘルプ デスクは [トラブルシューティング] のブレードを使用してユーザーのサポートができるようになります。

たとえば、ユーザーが Intune で技術的な問題をサポートに連絡すると、ヘルプ デスクがそのユーザーの名前を入力します。 Intune には、ユーザーの状態、アプリのインストールの失敗、コンプライアンスの問題などの、階層 1 の多くの問題の解決に役立つ関連情報が表示されます。 次のような問題が対処されます。
- デバイスが応答しない
-   デバイスが VPN または Wi-Fi の設定を取得できない
-   アプリのインストールの失敗


## <a name="add-help-desk-operators"></a>ヘルプ デスクの追加
Intune 管理者は、[ヘルプ デスク] のアクセス許可を次の 2 つの方法でユーザーに割り当てることができます。
- 組み込みの **[ヘルプ デスク]** のロールを割り当てる
- カスタム ロールを作成して割り当てる

## <a name="assign-help-desk-operator-role"></a>ヘルプ デスクのロールを割り当てる
Intune 管理者は、ユーザー グループに [ヘルプ デスク] のロールを割り当てることができます。 そのグループのメンバーは、管理ポータルを使用できます。 ヘルプ デスクには、それぞれ Intune ポータルにアクセスするための Intune のライセンスが必要です。 Intune のライセンスを割り当てる方法については、[こちら](licenses-assign.md)を参照してください。

1. Intune 管理者として Intune ポータルにログインし、**[Intune の役割]** を選択します。
2. **[Intune の役割]** ワークロードで **[ヘルプ デスク]** > **[割り当て]** を選択して、**[割り当て]** を選択します。
  ![[Intune の役割] の強調表示、[ヘルプ デスク] を含む組み込みのロールの一覧、[割り当て] の強調表示、赤く囲まれた [割り当て] が示されている Intune ポータルのスクリーンショット](./media/help-desk-user-assign.png)
3. **[割り当て名]** (必須)、**[割り当ての説明]** (オプション) を入力し、**[メンバー (グループ)]** と **[スコープ (グループ)]** を割り当てます。
4. これで、ヘルプ デスク ロールのメンバーは、トラブルシューティング ポータルを使用できます。

Intune の役割の詳細については、「[Microsoft Intune の Intune ロール (RBAC)](role-based-access-control.md)」をご覧ください。

## <a name="create-a-custom-role-for-troubleshooting"></a>トラブルシューティングのためのカスタム ロールを作成する
Intune 管理者は、組織のニーズに応じたアクセス許可でユーザーがトラブルシューティングのポータルを使用できるようなカスタム ロールを作成できます。 Intune の役割の詳細については、「[Microsoft Intune の Intune ロール (RBAC)](role-based-access-control.md)」をご覧ください。

![[Intune の役割] の強調表示および [ヘルプ デスク] を含む組み込みのロールの一覧が示されている Intune ポータルのスクリーンショット](./media/help-desk-user-add.png)

Intune コンソールをヘルプ デスクビューで使用するには、カスタム ヘルプ デスクのロールに次のアクセス許可が必要です。
- MobileApps: 読み取り
- ManagedApps: 読み取り
- ManagedDevices: 読み取り
- Organization: 読み取り

## <a name="access-the-troubleshooting-portal"></a>トラブルシューティング ポータルにアクセスする

ヘルプ デスクのスタッフや Intune 管理者は、2 つの方法でトラブルシューティング ポータルにアクセスできます。
- Web ブラウザーで [http://aka.ms/intunetroubleshooting](http://aka.ms/intunetroubleshooting) を開きます。
- Intune ポータルで、**[ヘルプとサポート]** > **[トラブルシューティング]** に移動します。

![Intune のトラブルシューティング ワークロードとユーザー選択リンクのスクリーンショット](media/help-desk-user.png)

## <a name="use-the-troubleshooting-portal"></a>トラブルシューティング ポータルを使用する

トラブルシューティング ポータルでは、**[ユーザーの選択]** を選択して、ユーザーの情報を表示できます。 ユーザー情報は、ユーザーと彼らのデバイスの現在の状態を理解するのに役立ちます。 トラブルシューティング ポータルでは、トラブルシューティングに関する以下の詳細が表示されます。
- **テナントの状態**
- **ユーザーの状態**
- **デバイス**とデバイス アクション
- **グループのメンバーシップ**
- **アプリの保護の状態**
