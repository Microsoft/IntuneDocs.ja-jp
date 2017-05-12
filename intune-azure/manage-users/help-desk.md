---
title: "ヘルプ デスクのトラブルシューティング ポータル |Microsoft Docs"
titleSuffix: Intune Azure preview
description: "ヘルプ デスクのスタッフが、トラブルシューティング ポータルを使用して、ユーザーの技術的な問題を解決する"
keywords: 
author: NathBarn
ms.author: NathBarn
manager: angrobe
ms.date: 03/18/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1f39c02a-8d8a-4911-b4e1-e8d014dbce95
ms.reviewer: sumitp
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 3758df744311392528be01c826527c2a9d879975
ms.openlocfilehash: 8cf12e434518c9f06c105a22f3b7aef2613fcdb0
ms.contentlocale: ja-jp
ms.lasthandoff: 05/10/2017

---
# <a name="help-users-with-the-troubleshooting-portal-in-microsoft-intune"></a>Microsoft Intune のトラブルシューティング ポータルでユーザーをサポートする

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

トラブルシューティング ポータルを使用すると、ヘルプ デスクと Intune 管理者は、ユーザーと彼らのデバイスを表示して、Intune の技術的な問題を解決するタスクを実行できます。

## <a name="add-help-desk-operators"></a>ヘルプ デスクの追加
Intune 管理者は、ヘルプ デスクのアクセス許可をユーザーに割り当てることができます。 すると、ヘルプ デスク ユーザーは Intune ポータルを表示できるようになりますが、トラブルシューティングに関係しない管理者タスクの表示と実行はできません。

1. Intune 管理者として [Azure Portal](https:portal.azure.com) にログインし、**[その他のサービス]**  >  **[監視 + 管理]**  >  **[Intune]** と選択します。
2. 左側のナビゲーション ブレードで、**[Intune の役割]** を選択します。
3. **[Intune の役割]** ワークロードで **[ヘルプ デスク]** を選択し、**[割り当て]** を選択します。
4. **[割り当て名]** (必須)、**[割り当ての説明]** (オプション) を入力し、**[メンバー (グループ)]** と **[スコープ (グループ)]** を割り当てます。
5. これで、ヘルプ デスク ロールのメンバーは、トラブルシューティング ポータルを使用できます。

Intune の役割の詳細については、「[Microsoft Intune の Intune ロール (RBAC)](../access-control/role-based-access-control.md)」をご覧ください。

## <a name="access-the-troubleshooting-portal"></a>トラブルシューティング ポータルにアクセスする

ヘルプ デスクのスタッフや Intune 管理者は、2 つの方法でトラブルシューティング ポータルにアクセスできます。
- [Azure Portal](https://portal.azure.com) で、**[その他のサービス]**  >  **[監視 + 管理]**  >  **[Intune]** と選択し、左側のナビゲーション ブレードで **[トラブルシューティング]** を選択します。 左側のナビゲーション ブレードには他のワークロードが表示されますが、使用はできません。

![Intune のトラブルシューティング ワークロードとユーザー選択リンクのスクリーンショット](media/help-desk-user.png)
- Web ブラウザーで [http://aka.ms/intunetroubleshooting](http://aka.ms/intunetroubleshooting) を開きます。 トラブルシューティング ポータルのみが表示されます。

## <a name="use-the-troubleshooting-portal"></a>トラブルシューティング ポータルを使用する

トラブルシューティング ポータルで **[ユーザーの選択]** を選択して、ユーザーの情報を表示できます。 ユーザー情報は、ユーザーと彼らのデバイスの現在の状態を理解するのに役立ちます。 トラブルシューティング ポータルでは、Intune ユーザーとデバイスについて以下の詳細が表示されます。
- ユーザー アカウント情報
- ユーザー グループのメンバーシップ
- デバイスの詳細

ヘルプ デスク ユーザーは、デバイス上で**リモート ロック**などのリモート タスクも実行できます。

