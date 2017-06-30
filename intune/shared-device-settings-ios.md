---
title: "iOS 用 Intune 共有デバイス構成設定"
titleSuffix: Intune on Azure
description: "iOS デバイスのロック画面に情報を表示するために使用できる Intune 設定について説明します。&quot;"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f122e4ee-90e7-4b42-b801-8c1c7c0a5bf7
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: 31e7f0d56d3fd6e637671b3bf551708eb626f5dc
ms.contentlocale: ja-jp
ms.lasthandoff: 06/08/2017


---

# <a name="shared-device-configuration-settings-to-display-messages-on-the-ios-device-lock-screen"></a>iOS デバイスのロック画面にメッセージを表示する共有デバイス構成設定

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

共有デバイス構成設定では、ログイン ウィンドウやロック画面に表示する任意のテキストを指定できます (たとえば、"If Lost, Return to (忘れ物として見つけた場合の返却先)" メッセージや資産タグなど)。 

>[!IMPORTANT]
> この機能は、iOS 9.3 以降を実行している監視対象デバイスでサポートされます。

1. **[デバイス機能]** ブレードで **[共有デバイスの構成 (監視のみ)]** を選択します。
2. **[共有デバイスの構成 (監視のみ)]** ブレードで、以下を構成します。
    - **[資産タグ情報]** - デバイスの資産タグに関する情報を入力します。 例: **Contoso Corp によって所有されている**。入力した情報は、このプロファイルを割り当てるすべてのデバイスに適用されます。
    - **[ロック画面の脚注]** - デバイスの紛失または盗難時に、返却に役立つようなメモを入力します。 例: **拾った方はこの番号 (xxx-xxx-xxx) にご連絡ください**。
3. 完了したら、**[プロファイルの作成]** ブレードに戻るまで **[OK]** を選択し、ブレードに戻ったら **[作成]** を選択します。 

