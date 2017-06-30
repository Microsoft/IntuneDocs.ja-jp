---
title: "ヘルプ デスクのトラブルシューティング ポータル"
titleSuffix: Intune on Azure
description: "ヘルプ デスクのスタッフが、トラブルシューティング ポータルを使用して、ユーザーの技術的な問題を解決する"
keywords: 
author: NathBarn
ms.author: NathBarn
manager: angrobe
ms.date: 05/30/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1f39c02a-8d8a-4911-b4e1-e8d014dbce95
ms.reviewer: sumitp
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: fcf14d2ed8a91f37ad286c84df889d02cbf7063e
ms.contentlocale: ja-jp
ms.lasthandoff: 06/08/2017

---
# <a name="help-users-with-the-troubleshooting-portal-in-microsoft-intune"></a>Microsoft Intune のトラブルシューティング ポータルでユーザーをサポートする

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

トラブルシューティング ポータルを使用すると、ヘルプ デスクと Intune 管理者は、ユーザーと彼らのデバイスを表示して、Intune の技術的な問題を解決するタスクを実行できます。

## <a name="add-help-desk-operators"></a>ヘルプ デスクの追加
Intune 管理者は、ヘルプ デスクのアクセス許可をユーザーに割り当てることができます。 すると、ヘルプ デスク ユーザーは Intune ポータルを表示できるようになりますが、トラブルシューティングに関係しない管理者タスクの表示と実行はできません。

1. Intune 管理者として Intune ポータルにログインし、**[Intune の役割]** を選択します。
3. **[Intune の役割]** ワークロードで **[ヘルプ デスク]** を選択し、**[割り当て]** を選択します。
4. **[割り当て名]** (必須)、**[割り当ての説明]** (オプション) を入力し、**[メンバー (グループ)]** と **[スコープ (グループ)]** を割り当てます。
5. これで、ヘルプ デスク ロールのメンバーは、トラブルシューティング ポータルを使用できます。

Intune の役割の詳細については、「[Microsoft Intune の Intune ロール (RBAC)](role-based-access-control.md)」をご覧ください。

## <a name="access-the-troubleshooting-portal"></a>トラブルシューティング ポータルにアクセスする

ヘルプ デスクのスタッフや Intune 管理者は、2 つの方法でトラブルシューティング ポータルにアクセスできます。
- Intune ポータルで、**[トラブルシューティング]** を選択します。 左側のナビゲーション ブレードには他のワークロードが表示されますが、使用はできません。

![Intune のトラブルシューティング ワークロードとユーザー選択リンクのスクリーンショット](media/help-desk-user.png)
- Web ブラウザーで [http://aka.ms/intunetroubleshooting](http://aka.ms/intunetroubleshooting) を開きます。 トラブルシューティング ポータルのみが表示されます。

## <a name="use-the-troubleshooting-portal"></a>トラブルシューティング ポータルを使用する

トラブルシューティング ポータルでは、**[ユーザーの選択]** を選択して、ユーザーの情報を表示できます。 ユーザー情報は、ユーザーと彼らのデバイスの現在の状態を理解するのに役立ちます。 トラブルシューティング ポータルでは、トラブルシューティングに関する以下の詳細が表示されます。
- **テナントの状態**
- **ユーザーの状態**
- **デバイス**
- **グループのメンバーシップ**
- **アプリの保護の状態**

ヘルプ デスク ユーザーは、デバイス上で**リモート ロック**などのリモート タスクも実行できます。

