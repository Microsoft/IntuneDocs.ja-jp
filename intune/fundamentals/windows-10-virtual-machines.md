---
title: Microsoft Intune での Windows 10 仮想マシンの使用
titleSuffix: ''
description: Microsoft Intune での Windows 10 仮想マシンの使用に関するガイドライン
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/20/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9afaf2c8a63bfaed1fdb593baf42c8fa258d7893
ms.sourcegitcommit: 1a22b8b31424847d3c86590f00f56c5bc3de2eb5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2019
ms.locfileid: "74263118"
---
# <a name="using-windows-10-virtual-machines-with-intune"></a>Intune での Windows 10 仮想マシンの使用

Intune では、Windows 10 Enterprise を実行する仮想マシンの管理が、一定の制限付きでサポートされています。 Intune の管理は、同じ仮想マシンの Windows Virtual Desktop 管理に依存したり、干渉したりすることはありません。

Intune で Windows 10 VM を管理する場合は、次の点に注意してください。

## <a name="enrollment"></a>登録
- Intune を使用してオンデマンドのセッション ホスト仮想マシンを管理することはお勧めしません。 各 VM は、作成時に登録する必要があります。 また、VM を定期的に削除すると、[クリーンアップ](../remote-actions/devices-wipe.md#automatically-delete-devices-with-cleanup-rules)されるまで、孤立したデバイス レコードが Intune に残ります。 
- Windows Autopilot 自己展開モードは、トラステッド プラットフォーム モジュール (TPM) を必要とするため、サポートされていません。 
- Out of Box Experience (OOBE) 登録は、RDP を使用してのみアクセスできる VM (Azure でホストされている VM など) ではサポートされていません。 この制限は次のことを意味します。
    - Windows Autopilot と商用 OOBE はサポートされていません。
    - デバイス コンテキスト ポリシーの登録状態ページ オプションはサポートされていません。

## <a name="configuration"></a>構成
Intune では、トラステッド プラットフォーム モジュールまたはハードウェア管理を利用する構成はサポートされていません。これには次のものが含まれます。
- [BitLocker 設定](../configuration/device-profiles.md#endpoint-protection)
- [デバイス ファームウェア構成インターフェイス設定](../configuration/device-profiles.md#device-firmware-configuration-interface)

## <a name="reporting"></a>レポート
Intune により仮想マシンが自動的に検出され、 **[デバイス]**  >  **[すべてのデバイス]** > デバイスを選択 > **[概要]**  >  **[モデル]** フィールドに "仮想マシン" として報告されます。 

割り当て解除された仮想マシンは、[Intune サービスにチェックイン](../configuration/device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned)できないため、非準拠デバイス レポートの原因になる可能性があります。

## <a name="retirement"></a>使用停止
RDP アクセスのみが可能な場合は、[ワイプ アクション](../remote-actions/devices-wipe.md#wipe)を使用しないでください。 ワイプ アクションを実行すると、仮想マシンの RDP 設定が削除され、再び接続することはできなくなります。


