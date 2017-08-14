---
title: "Windows 10 Team 向けの Intune デバイス制限"
titleSuffix: Intune on Azure
description: "Windows 10 Team デバイスで使用できるデバイス制限について説明します。\""
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/01/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 677c41a2-5344-4c52-85f0-809dce3a5d5b
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: abb5e181430b267ca2267bb7209687177ae5fde2
ms.sourcegitcommit: 79116d4c7f11bafc7c444fc9f5af80fa0b21224e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2017
---
# <a name="windows-10-team-device-restriction-settings-in-microsoft-intune"></a>Microsoft Intune での Windows 10 Team デバイスの制限設定

[!INCLUDE[azure_portal](./includes/azure_portal.md)]


## <a name="apps-and-experience"></a>アプリとエクスペリエンス

- **[ユーザーの入室時に画面のスリープ状態を解除する]** - 部屋にだれかがいるとセンサーで検出したときに、デバイスのスリープ状態を自動的に解除します。
- **[ようこそ画面に表示される会議情報]** - このオプションを有効にすると、ようこそ画面の [Meetings (会議)] タイルに表示される情報を選択できます。 次の操作を行います。
    - **[開催者と時刻のみの表示]**
    - **[開催者、時刻、議題の表示 (非公開なミーティングの場合は議題を非表示)]**
- **[ようこそ画面の背景画像の URL]** - Windows 10 Team デバイスの**ようこそ**画面に指定した URL のカスタム背景を表示する場合は、この設定を有効にします。<br>画像は PNG 形式である必要があり、URL は **https://** で始まっている必要があります。

## <a name="azure-operational-insights"></a>Azure Operational Insights

- **[Azure Operational Insights]** - Microsoft Operations Manager Suite の一部である Azure Operational Insights は、Windows 10 Team デバイスからログ ファイルのデータを収集、格納、分析します。
Azure Operational insights に接続するには、**ワークスペース ID** と **ワークスペース キー**を指定する必要があります。

## <a name="maintenance"></a>メンテナンス

- **[更新プログラムのメンテナンス期間]** - デバイスで更新を実行する期間を構成します。 期間の **[開始時刻]** と **[期間 (時間単位)]** (1 時間から 5 時間) を構成できます。

## <a name="wireless-projection"></a>ワイヤレス投影

- **[ワイヤレス投影の PIN]** - デバイスのワイヤレス投影機能を使用する前に暗証番号 (PIN) を入力しなければならないかどうかを指定します。
- **[Miracast ワイヤレス投影]** - Windows 10 Team デバイスで Miracast が有効になっているデバイスを使用して投影する場合は、このオプションを選択します。
- **[Miracast ワイヤレス投影チャネル]** - 接続を確立するために使用される Miracast チャネルを選択します。


## <a name="next-steps"></a>次のステップ

「[Microsoft Intune でデバイスの制限設定を構成する方法](device-restrictions-configure.md)」の情報を使って、プロファイルを保存し、ユーザーとデバイスに割り当てます。
