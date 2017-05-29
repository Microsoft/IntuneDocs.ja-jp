---
title: "モバイル デバイス管理機関の設定"
titleSuffix: Intune Azure preview
description: "Intune Azure プレビュー: Intune でモバイル デバイス管理機関を設定する方法について説明します。 "
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 04/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8deff871-5dff-4767-9484-647428998d82
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: c36ddef7e53d6f4f15c82c97dc6d18863e6859f1
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017

---

# <a name="set-the-mobile-device-management-authority"></a>モバイル デバイス管理機関の設定

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

モバイル デバイス管理 (MDM) 機関の設定によって、デバイスの管理方法が決まります。 IT 管理者が MDM 機関を設定してからでないと、ユーザーは管理対象のデバイスを登録できません。

可能な構成は以下のとおりです。

- **Intune スタンドアロン** - Azure Portal を利用して構成する、クラウドのみの管理。 Intune で提供される機能がすべて含まれます。 [Intune コンソールで MDM 機関を設定](#mdm-authority-set-to-intune)します。

- **Intune ハイブリッド** - Intune クラウド ソリューションと System Center Configuration Manager の統合。 Configuration Manager コンソールを使用して Intune を構成します。 [Configuration Manager で MDM 機関を設定](https://docs.microsoft.com/sccm/mdm/deploy-use/configure-intune-subscription)します。

- **Office 365 のモバイル デバイス管理** - Office 365 と Intune クラウド ソリューションの統合。 Office 365 管理センターから Intune を構成します。 Intune スタンドアロンで利用できる機能の一部が含まれます。 Office 365 管理センターで MDM 機関を設定します。

>[!IMPORTANT]
>いったん設定したモバイル デバイス管理機関を変更するには、[Microsoft サポート](https://docs.microsoft.com/intune-classic/troubleshoot/get-support)への問い合わせが必要になるため、選択は慎重に行ってください。

## <a name="set-mdm-authority-to-intune"></a>MDM 機関を Intune に設定する

1. Azure Portal で、**[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
  ![Intune のトラブルシューティング ワークロードとユーザー選択リンクのスクリーンショット](media/set-mdm-auth.png)
2. [Intune] ブレードで **[デバイスの登録]** を選択し、**[概要]** を選択します。

3. **[デバイスの管理を開始する]** ブレードで、**[MDM 機関を Intune に設定する]** を選択します。 MDM 機関が Intune に正しく設定されたことを示すメッセージが表示されます。

