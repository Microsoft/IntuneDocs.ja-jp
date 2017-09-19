---
title: "紛失した iOS デバイスを Intune で検索する"
titlesuffix: Azure portal
description: "紛失したまたは盗まれた iOS デバイスを Intune で検索する方法について説明します。\""
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3e544286-12ad-4a3a-86f8-d2cf16940b1f
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 9d03555e91a9e759e62b829576a0d39f957ab430
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2017
---
# <a name="locate-lost-or-stolen-ios-devices-with-intune"></a>紛失したまたは盗まれた iOS デバイスを Intune で検索する


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

この**[デバイスを検索する]** デバイス アクションは、紛失したまたは盗まれた iOS デバイスの場所をマップに表示します。 会社所有の iOS デバイスを DEP で登録し、監視モードに設定している必要があります。 このアクションを使用するには、デバイスが[紛失モード](/intune-azure/manage-devices/lost-mode.md)に設定されている必要があります。

## <a name="supported-platforms"></a>サポートされているプラットフォーム

- Windows - サポートされていません
- Windows Phone - サポートされていません
- iOS - 監視されている企業所有の iOS 9.3 以降 (紛失モード) でサポートされています
- macOS - サポートされていません
- Android - サポートされていません

## <a name="how-to-locate-a-lost-or-stolen-device"></a>紛失または盗難にあったデバイスを見つける方法

1. Azure ポータルにサインインします。
2. **[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
3. **[Intune]** ブレードで、**[デバイス]** を選択します。
4. **[デバイスとグループ]** ブレードで、**[すべてのデバイス]** を選択します。
5. 管理するデバイスの一覧から iOS デバイスを選択し、その後**[デバイスを検索する]** リモート アクションを選択します。
6. デバイスの位置が特定されると、その場所が **[デバイスを探索する]** ブレードに表示されます。
    ![[デバイスを検索する] ブレード](./media/locate-device.png)

>[!NOTE]
>プライバシーのために、マップでズームインできる距離は制限されています。

## <a name="security-and-privacy-information-for-the-lost-mode-and-locate-device-actions"></a>紛失モードとデバイスを探索するアクションのセキュリティおよびプライバシー情報
- このアクションを有効にするまで、デバイスの位置情報は Intune に送信されません。
- デバイスを探索するアクションを使用した場合、デバイスの緯度と経度の座標が Intune に送信され、Azure Portal に表示されます。
- データは 24 時間保管されてから、削除されます。 位置データを手動で削除することはできません。
- 位置データは、保管中も、転送中も暗号化されます。
- 紛失モードを構成する場合、ロック画面に表示するメッセージの入力時に、デバイスを見つけた人がデバイスを返すのに役立つ情報を含めることをお勧めします。


## <a name="next-steps"></a>次のステップ

実行したアクションの状態を確認するには、**[デバイスとグループ]** ブレードで **[デバイス アクション]** を選択します。