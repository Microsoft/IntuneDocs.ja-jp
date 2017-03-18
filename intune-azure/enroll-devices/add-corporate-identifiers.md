---
title: "IMEI 識別子を Intune に追加する"
titleSuffix: Intune Azure preview
description: "Intune Azure プレビュー: 企業 ID (IMEI 番号) を Microsoft Intune に追加する方法について説明します。 "
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 03/08/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 566ed16d-8030-42ee-bac9-5f8252a83012
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: d8cb15d1b8c1c100f15084e43d2c3c4633fd64b5
ms.openlocfilehash: f12d538b1f4cd327b893d234f2b558185cdd9d85
ms.lasthandoff: 03/09/2017

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

> [!IMPORTANT]
> 一部の Android デバイスには複数の IMEI 番号があります。 Intune は、1 台のデバイスにつき&1; つの IMEI 番号をインベントリします。 IMEI 番号をインポートするときに、その番号が Intune にインベントリされている IMEI ではない場合、デバイスは会社所有のデバイスではなく個人のデバイスとして分類されます。 1 台のデバイスに複数の IMEI 番号をインポートすると、インベントリされていない番号の登録状態は **[不明]** と表示されます。

**企業 ID の .csv リストを削除するには**

1. Azure Portal で、**[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。

2. [Intune] ブレードで **[デバイスの登録]** を選択してから、**[業務用デバイスの ID]** を選択します。

3. **[削除]** を選択します。

