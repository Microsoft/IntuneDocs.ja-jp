---
title: "iOS の紛失モードを Intune でアクティブ化する"
titleSuffix: Intune on Azure
description: "Intune を使用して、紛失したまたは盗まれた iOS デバイスの紛失モードをアクティブ化する方法について説明します。&quot;"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/27/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 126a7489-fe3e-43fd-a681-defb2fe0bb66
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: a34d008ae76355578c6f24a932c9e1e501d5b46b
ms.contentlocale: ja-jp
ms.lasthandoff: 06/08/2017


---

# <a name="activate-lost-mode-on-ios-devices"></a>iOS デバイスの紛失モードをアクティブ化する


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

**紛失モード**のデバイス アクションを使用すると、紛失したまたは盗まれた iOS デバイスの紛失モードを有効にできます。 このモードでは、デバイスのロック画面に表示されるメッセージと電話番号を指定できます。

1. Azure ポータルにサインインします。
2. **[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
3. **[Intune]** ブレードで、**[デバイス]** を選択します。
4. **[デバイスとグループ]** ブレードで、**[すべてのデバイス]** を選択します。
5. 管理するデバイスの一覧から iOS デバイスを選択し、**[紛失モード]** のリモート アクションを選択します。
6. **[紛失モード]** ブレードで、紛失モードを有効にし、表示されるメッセージと、必要に応じて、連絡先の電話番号を入力します。
7. **[OK]**をクリックします。

紛失モードを有効にすると、デバイスのすべての利用がブロックされます。 エンド ユーザーは、紛失モードを無効にするまでデバイスにアクセスできなくなります。 紛失モードを有効にした場合、**[デバイスを検索する]** アクションを使って、デバイスの場所を検索できます。
会社所有の iOS デバイスを DEP で登録し、監視モードに設定していなければ、紛失モードは利用できません。

実行したアクションの状態を確認するには、**[デバイスとグループ]** ブレードで **[デバイス アクション]** を選択します。

## <a name="security-and-privacy-information-for-the-lost-mode-and-locate-device-actions"></a>紛失モードとデバイスを探索するアクションのセキュリティおよびプライバシー情報
- このアクションを有効にするまで、デバイスの位置情報は Intune に送信されません。
- デバイスを探索するアクションを使用した場合、デバイスの緯度と経度の座標が Intune に送信され、Azure Portal に表示されます。
- データは 24 時間保管されてから、削除されます。 位置データを手動で削除することはできません。
- 位置データは、保管中も、転送中も暗号化されます。
- 紛失モードを構成する場合、ロック画面に表示するメッセージの入力時に、デバイスを見つけた人がデバイスを返すのに役立つ情報を含めることをお勧めします。


