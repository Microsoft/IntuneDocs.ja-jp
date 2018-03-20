---
title: "Microsoft Intune で紛失 iOS デバイスを検索する | Microsoft Docs"
description: "Microsoft Intune の [デバイスを検索する] 機能を使用して、紛失したまたは盗まれた iOS デバイスを検索するか場所を特定します。[デバイスを検索する] アクションを使用する場合は、セキュリティおよびプライバシーに関する詳細な情報を取得します。"
keywords: 
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3e544286-12ad-4a3a-86f8-d2cf16940b1f
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4bc51ef7f9af9cc97fd4c11408a1857679aee665
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2018
---
# <a name="locate-lost-or-stolen-ios-devices-with-intune"></a>紛失したまたは盗まれた iOS デバイスを Intune で検索する

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

紛失したまたは盗まれた iOS デバイスの位置をマップに表示するには、**[デバイスを検索する]** アクションを使用します。 デバイスは、Device Enrollment Program (DEP) で登録された会社所有の iOS デバイスであり、かつ監視モードに設定されている必要があります。 このアクションを使用する前に、デバイスが[紛失モード](device-lost-mode.md)になっていることを確認してください。

## <a name="supported-platforms"></a>サポートされているプラットフォーム

- iOS 9.3 以降

次のシステムについては、この機能はサポート**されません**。 
- Windows
- Windows Phone
- macOS
- Android

## <a name="locate-a-lost-or-stolen-device"></a>紛失したまたは盗まれたデバイスを見つける方法

1. [Azure ポータル](https://portal.azure.com)にサインインします。
2. **[すべてのサービス]** を選択し、**[Intune]** をフィルターとして適用し、**[Microsoft Intune]** を選択します。
3. **[デバイス]**、**[すべてのデバイス]** の順に選択します。
4. 管理するデバイスの一覧から iOS デバイスを選択し、**[詳細]**、**[デバイスを検索する]** リモート アクションの順に選択します。
5. デバイスが見つかると、**[デバイスを検索する]** にその位置が表示されます。
    ![Azure で Intune を使用してデバイスを検索する](./media/locate-device.png)

>[!NOTE]
>プライバシーのために、マップでズームインできる距離は制限されています。

## <a name="security-and-privacy-information-for-lost-mode-and-locate-device-actions"></a>紛失モードとデバイスを探索するアクションのセキュリティおよびプライバシー情報
- このアクションを有効にするまで、デバイスの位置情報は Intune に送信されません。
- デバイスを探索するアクションを使用した場合、デバイスの緯度と経度の座標が Intune に送信され、Azure Portal に表示されます。
- データは 24 時間保管されてから、削除されます。 位置データを手動で削除することはできません。
- 位置データは、保管中も、転送中も暗号化されます。
- 紛失モードを構成するときは、ロック画面に表示されるメッセージをカスタマイズできます。 このメッセージには、ユーザーがデバイスを容易に検索できるように、紛失したデバイスが戻ってくるようにするための特定の詳細情報を必ず含めます。

## <a name="next-steps"></a>次の手順

[デバイスを検索する] の有効化の状態を表示するには、**[デバイス]** を開き、**[デバイス アクション]** を選択します。
