---
title: Microsoft Intune で紛失 iOS デバイスを検索する | Microsoft Docs
description: Microsoft Intune のデバイスの検索機能を使用して、紛失したまたは盗まれた iOS デバイスを検索します。 デバイスの検索アクションを使用する場合は、セキュリティおよびプライバシーに関する詳細な情報を取得します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3e544286-12ad-4a3a-86f8-d2cf16940b1f
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 96d4143b5105a174ba47c8c7a713ae7bee9bcb94
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2019
ms.locfileid: "55835737"
---
# <a name="locate-lost-or-stolen-ios-devices-with-intune"></a>紛失したまたは盗まれた iOS デバイスを Intune で検索する

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

紛失したまたは盗まれた iOS デバイスの位置をマップに表示するには、**[デバイスを検索する]** アクションを使用します。 デバイスが監視モードである必要があります。 このアクションを使用する前に、デバイスが[紛失モード](device-lost-mode.md)になっていることを確認してください。

## <a name="supported-platforms"></a>サポートされているプラットフォーム

- iOS 9.3 以降

次のシステムについては、この機能はサポートされません。 
- Windows
- Windows Phone
- macOS
- Android

## <a name="locate-a-lost-or-stolen-device"></a>紛失したまたは盗まれたデバイスを見つける方法

1. [Azure ポータル](https://portal.azure.com)にサインインします。
2. **[すべてのサービス]** を選択し、**[Intune]** をフィルターとして適用し、**[Microsoft Intune]** を選択します。
3. **[デバイス]**、**[すべてのデバイス]** の順に選択します。
4. 管理対象のデバイスのリストから、iOS デバイスを選択して **[...詳細を表示]** を選択します。 次に、**[デバイスを検索する]** リモート アクションを選択します。
5. デバイスが見つかると、**[デバイスを検索する]** にその位置が表示されます。
    ![Azure で Intune を使用しているときの [デバイスを検索する] のスクリーンショット](./media/locate-device.png)

>[!NOTE]
>プライバシー上の理由から、マップでズームインできる距離は、半径 300 メートルに制限されています。

## <a name="activate-lost-mode-sound-alert-on-an-ios-device"></a>iOS デバイスで紛失モード サウンド アラートをアクティブにする

ユーザーが iOS 9.3 以降のデバイスを紛失した場合、ユーザーがデバイスを見つけられるように、遠隔操作でデバイスのアラート サウンドの再生をトリガーすることができます。 デバイスが[紛失モード](device-lost-mode.md)になっている必要があります。

[Azure Portal の Intune](https://aka.ms/intuneportal) で、**[デバイス]** > **[すべてのデバイス]** の順に選び、iOS デバイスを選んでから、**[概要]** > **[詳細]** > **[Play Lost mode sound (supervise only)]\(紛失モードのサウンドを再生する (監視のみ)\)** を選びます。

サウンドの再生は、ユーザーがデバイスでサウンドを無効にするまで、またはデバイスの紛失モードが解除されるまで続きます。


## <a name="security-and-privacy-information-for-lost-mode-and-locate-device-actions"></a>紛失モードとデバイスを探索するアクションのセキュリティおよびプライバシー情報
- このアクションを有効にするまで、デバイスの位置情報は Intune に送信されません。
- デバイスの検索アクションを使用した場合、Graph API を使用することでデバイスの緯度と経度の座標を取得できます。
- データは 24 時間保管されてから、削除されます。 位置データを手動で削除することはできません。
- 位置データは、保管中であっても転送中であっても暗号化されます。
- 紛失モードを構成するときは、ロック画面に表示されるメッセージをカスタマイズできます。 このメッセージには、ユーザーがデバイスを容易に検索できるように、紛失したデバイスが戻ってくるようにするための特定の詳細情報を必ず含めます。

## <a name="next-steps"></a>次の手順

デバイスの検索の有効化の状態を表示するには、**[デバイス]** を開き、**[デバイス アクション]** を選択します。
