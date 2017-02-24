---
title: "モバイル デバイス管理機関の設定"
titleSuffix: Intune Azure preview
description: "Intune Azure プレビュー: Intune でモバイル デバイス管理機関を設定する方法について説明します。 "
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 01/06/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8deff871-5dff-4767-9484-647428998d82
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 9d7a1a934188f0a40553d3c6b8b567ba8f6af034

---

# <a name="set-the-mobile-device-management-authority"></a>モバイル デバイス管理機関の設定 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

モバイル デバイス管理機関の設定によってデバイスの管理方法が決まります。 考えられる構成は以下のとおりです。

- **Intune スタンドアロン** - Azure Portal を利用して構成する、クラウドのみの管理。 Intune で提供される機能がすべて含まれます。

- **Intune ハイブリッド** - Intune クラウド ソリューションと System Center Configuration Manager の統合。 Configuration Manager コンソールを使用して Intune を構成します。

- **Office 365 のモバイル デバイス管理** - Office 365 と Intune クラウド ソリューションの統合。 Office 365 管理センターから Intune を構成します。 Intune スタンドアロンで利用できる機能の一部が含まれます。

>[!IMPORTANT]
>いったん設定したモバイル デバイス管理機関を変更するには、[Microsoft サポート](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune)への問い合わせが必要になるため、選択は慎重に行ってください。

**モバイル デバイス管理機関を設定するには、以下の手順に従います。**

1. Azure Portal で、**[その他のサービス]** > **[監視 + 管理]** > **[Intune]** を選択します。

2. [Intune] ブレードで **[デバイスの登録]** を選択し、**[概要]** を選択します。

3. **[デバイスの管理を開始する]** ブレードで、**[MDM 機関を Intune に設定する]** を選択します。 MDM 機関が Intune に正しく設定されたことを示すメッセージが表示されます。



<!--HONumber=Feb17_HO3-->


