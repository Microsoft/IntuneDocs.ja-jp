---
title: "IMEI 識別子を Intune に追加する"
titleSuffix: Intune Azure preview
description: "Intune Azure プレビュー: 企業 ID (IMEI 番号) を Microsoft Intune に追加する方法について説明します。 "
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 566ed16d-8030-42ee-bac9-5f8252a83012
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 0d7c8eedbdad917a43d43d2e79ead5663e8e2871
ms.lasthandoff: 02/18/2017

---

# <a name="add-corporate-identifiers"></a>企業 ID を追加する

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

International Mobile Equipment Identity (IMEI) 番号の一覧を作成して、企業デバイスを特定できます。 これらのデバイスは登録されている場合と、されていない場合があり、"登録済み" と "未接続" のいずれかの状態になります。 "未接続" の場合、デバイスは Intune サービスでチェックインしません。

リストを作成するには、ヘッダーなしの&2; 列のコンマ区切り値 (.csv) リストを作成します。 IMEI 識別子を左側の列に、詳細を右側の列に追加します。 リストで許可されている現在の最大行数は 500 行です。

この .csv リストをテキスト エディターで表示すると次のようになります。

01 234567 890123,デバイスの詳細</br>
02 234567 890123,デバイスの詳細

**企業 ID の .csv リストを追加するには**

1. Azure Portal で、**[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。

2. [Intune] ブレードで **[デバイスの登録]** を選択してから、**[業務用デバイスの ID]** を選択します。

3. 新しい詳細情報が含まれるファイルをインポートする場合、そしてその情報で既存の情報が上書きされる場合は、**[既存の ID の詳細を上書きします]** を選択して、既存の詳細情報が、新しい詳細情報で置き換えられるようにします。

4. IMEI CSV ファイルに移動して、**[追加]** を選択します。

**企業 ID の .csv リストを削除するには**

1. Azure Portal で、**[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。

2. [Intune] ブレードで **[デバイスの登録]** を選択してから、**[業務用デバイスの ID]** を選択します。

3. **[削除]** を選択します。

