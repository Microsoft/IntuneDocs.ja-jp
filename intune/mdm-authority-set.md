---
title: "モバイル デバイス管理機関の設定"
titleSuffix: Intune on Azure
description: "Intune でモバイル デバイス管理機関を設定する方法について説明します。 \""
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 05/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8deff871-5dff-4767-9484-647428998d82
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 449c45e0edcc0d0a33352ba154ad68fa6c4725c0
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2017
---
# <a name="set-the-mobile-device-management-authority"></a>モバイル デバイス管理機関の設定

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

モバイル デバイス管理 (MDM) 機関の設定によって、デバイスの管理方法が決まります。 IT 管理者が MDM 機関を設定してからでないと、ユーザーは管理対象のデバイスを登録できません。

可能な構成は以下のとおりです。

- **Intune スタンドアロン** - Azure Portal を利用して構成する、クラウドのみの管理。 Intune で提供される機能がすべて含まれます。 [Intune コンソールで MDM 機関を設定](#mdm-authority-set-to-intune)します。

- **Intune ハイブリッド** - Intune クラウド ソリューションと System Center Configuration Manager の統合。 Configuration Manager コンソールを使用して Intune を構成します。 [Configuration Manager で MDM 機関を設定](https://docs.microsoft.com/sccm/mdm/deploy-use/configure-intune-subscription)します。

- **Office 365 のモバイル デバイス管理** - Office 365 と Intune クラウド ソリューションの統合。 Office 365 管理センターから Intune を構成します。 Intune スタンドアロンで利用できる機能の一部が含まれます。 Office 365 管理センターで MDM 機関を設定します。

>[!IMPORTANT]    
Configuration Manager 1610 以降のバージョンと Microsoft Intune バージョン 1705 では、MDM 機関の変更にあたって Microsoft サポートに問い合わせる必要はありません。また、既存の管理されたデバイスの登録を解除して再登録する必要もありません。 詳細については、「[不適切な MDM 機関の設定を選択した場合の対処方法](/intune-classic/deploy-use/prerequisites-for-enrollment#what-to-do-if-you-choose-the-wrong-mdm-authority-setting)」を参照してください。

## <a name="set-mdm-authority-to-intune"></a>MDM 機関を Intune に設定する

1. Azure Portal で、**[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
  ![Intune のトラブルシューティング ワークロードとユーザー選択リンクのスクリーンショット](media/set-mdm-auth.png)
2. [Intune] ブレードで **[デバイスの登録]** を選択し、**[概要]** を選択します。

3. **[デバイスの管理を開始する]** ブレードで、**[MDM 機関を Intune に設定する]** を選択します。 MDM 機関が Intune に正しく設定されたことを示すメッセージが表示されます。

## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>MDM 証明書の有効期限が切れた後のモバイル デバイスのクリーンアップ

MDM 証明書は、モバイル デバイスが Intune サービスと通信しているときに自動的に更新されます。 モバイル デバイスがワイプされたり、一定の時間 Intune サービスとモバイル デバイスが通信できなかったりすると、MDM 証明書は更新されません。 デバイスは、MDM 証明書の有効期限が切れてから 180 日後に、Azure Portal から削除されます。
