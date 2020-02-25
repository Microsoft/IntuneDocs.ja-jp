---
title: Microsoft Intune を使った iOS/iPadOS 紛失モードの有効化 - Azure | Microsoft Docs
description: 紛失した、または盗難にあった iOS/iPadOS デバイスのロック画面に表示されるメッセージをカスタマイズする場合は、Microsoft Intune を使用して紛失モードをオンにするか開始します。 紛失モード アクションを使用する場合は、セキュリティおよびプライバシーに関する詳細な情報を取得します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/25/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 126a7489-fe3e-43fd-a681-defb2fe0bb66
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9a4103c819c0d4bd377b9c6ab2359cb7465cdd9c
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415592"
---
# <a name="enable-lost-mode-on-iosipados-devices-with-intune"></a>Intune を使って iOS/iPadOS デバイスの紛失モードを有効にする

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

**紛失モード**のデバイス アクションを使用すると、紛失した、または盗難にあった iOS/iPadOS デバイスの紛失モードを有効にできます。 このモードでは、デバイスのロック画面に表示されるメッセージと電話番号を入力できます。 紛失モードを使用するには、デバイスが監視モードにある企業所有の iOS/iPadOS デバイスである必要があります。

## <a name="supported-platforms"></a>サポートされているプラットフォーム

- iOS/iPadOS 9.3 以降

以下については、この機能はサポートされません。 
- Windows
- Windows Phone
- macOS
- Android

## <a name="enable-lost-mode"></a>紛失モードを有効にする

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。
3. **[デバイス]** 、 **[すべてのデバイス]** の順に選択します。
4. 管理するデバイスの一覧から iOS/iPadOS デバイスを選択した後、 **[紛失モード (監視モードのみ)]** を選択します。
5. **[紛失モード]** の下で **[有効]** を選択します。
6. **[Message to display on lock screen]\(ロック画面に表示するメッセージ\)** に、デバイスのロック画面に表示されるメッセージを入力します。
7. 必要に応じて、 **[表示する電話番号]** ボックスに電話番号を入力します。
6. **[OK]** を選択して変更を保存します。

紛失モードを有効にすると、デバイスのすべての利用がブロックされます。 エンド ユーザーは、紛失モードを無効にするまでデバイスにアクセスできなくなります。 紛失モードを有効にした場合は、[[デバイスを検索する]](device-locate.md) アクションを使用してデバイスを検索します。

## <a name="security-and-privacy-information-for-the-lost-mode-and-locate-device-actions"></a>紛失モードとデバイスを探索するアクションのセキュリティおよびプライバシー情報
- このアクションを有効にするまで、デバイスの位置情報は Intune に送信されません。
- デバイスの検索アクションを使用した場合、デバイスの緯度と経度の座標が Intune に送信され、Azure Portal に表示されます。
- データは 24 時間保管されてから、削除されます。 位置データを手動で削除することはできません。
- 位置データは、保管中も、転送中も暗号化されます。
- ロック画面に表示するメッセージを入力するときには、紛失したデバイスが戻るように特定の詳細情報を必ず含めてください。

## <a name="next-steps"></a>次のステップ

紛失モードの有効化の状態を確認するには、 **[デバイス]** を開き、 **[デバイス アクション]** を選択します。
