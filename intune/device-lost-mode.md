---
title: "Microsoft Intune を使った iOS 紛失モードの有効化 - Azure | Microsoft Docs"
description: "紛失したまたは盗まれた iOS デバイスのロック画面に表示されるメッセージをカスタマイズするために、Microsoft Intune を使って紛失モードをオンにするか開始します。 紛失モード アクションを使用する場合は、セキュリティおよびプライバシーに関する詳細な情報を取得します。"
keywords: 
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 126a7489-fe3e-43fd-a681-defb2fe0bb66
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 47d6314dfaed546e5b4cff7f93a5540ba512bde9
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2018
---
# <a name="enable-lost-mode-on-ios-devices-with-intune"></a>Intune を使って iOS デバイスの紛失モードを有効にする

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

**紛失モード**のデバイス アクションを使用すると、紛失したまたは盗まれた iOS デバイスの紛失モードを有効にできます。 このモードでは、デバイスのロック画面に表示されるメッセージと電話番号を入力できます。 紛失モードを使用するには、デバイスが監視モードにある企業所有の iOS デバイスである必要があります。

## <a name="supported-platforms"></a>サポートされているプラットフォーム

- iOS 9.3 以降

次のシステムについては、この機能はサポート**されません**。 
- Windows
- Windows Phone
- macOS
- Android

## <a name="enable-lost-mode"></a>紛失モードを有効にする

1. サインイン、 [Azure ポータル](https://portal.azure.com)します。
2. **[すべてのサービス]** を選択し、**[Intune]** をフィルターとして適用し、**[Microsoft Intune]** を選択します。
3. **[デバイス]**、**[すべてのデバイス]** の順に選択します。
4. 管理するデバイスの一覧から iOS デバイスを選択し、**[詳細]**、**[紛失モード]** リモート操作の順に選択します。
5. **[紛失モード]** で、この機能を有効にします。 次に、表示するメッセージを入力し、連絡先の電話番号を入力します。
6. **[OK]** を選択して変更を保存します。

紛失モードを有効にすると、デバイスのすべての利用がブロックされます。 エンド ユーザーは、紛失モードを無効にするまでデバイスにアクセスできなくなります。 紛失モードを有効にした場合は、[[デバイスを検索する]](device-locate.md) アクションを使用してデバイスを検索します。

## <a name="security-and-privacy-information-for-the-lost-mode-and-locate-device-actions"></a>紛失モードとデバイスを探索するアクションのセキュリティおよびプライバシー情報
- このアクションを有効にするまで、デバイスの位置情報は Intune に送信されません。
- デバイスを探索するアクションを使用した場合、デバイスの緯度と経度の座標が Intune に送信され、Azure Portal に表示されます。
- データは 24 時間保管されてから、削除されます。 位置データを手動で削除することはできません。
- 位置データは、保管中も、転送中も暗号化されます。
- ロック画面に表示するメッセージを入力するときには、紛失したデバイスが戻るように特定の詳細情報を必ず含めます。

## <a name="next-steps"></a>次の手順

紛失モードの有効化の状態を確認するには、**[デバイス]** を開き、**[デバイス アクション]** を選択します。