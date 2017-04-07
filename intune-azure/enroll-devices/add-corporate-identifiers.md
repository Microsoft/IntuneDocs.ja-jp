---
title: "IMEI 識別子を Intune に追加する"
titleSuffix: Intune Azure preview
description: "Intune Azure プレビュー: 企業 ID (IMEI 番号) を Microsoft Intune に追加する方法について説明します。 "
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 03/22/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 566ed16d-8030-42ee-bac9-5f8252a83012
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 4ebd74c77145464574a1fed878ec4dbc2eb3c271
ms.openlocfilehash: 7bb8168c442a3340e8c185f1908acd9be15cab05
ms.lasthandoff: 04/05/2017

---

# <a name="add-corporate-identifiers"></a>企業 ID を追加する

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

IT 管理者は、会社所有のデバイスを識別するための International Mobile Equipment Identity (IMEI) を記載しているコンマ区切り (.csv) ファイルを作成し、インポートできます。 各 IMEI 番号の一覧には管理目的で詳細を追加できます。

会社所有の iOS デバイスのシリアル番号をアップロードする場合は、企業登録プロファイルとペアにする必要があります。 したがって、デバイスを Apple の DEP (Device Enrollment Program) または Apple Configurator を使用して登録し、会社所有であることを示す必要があります。 

## <a name="create-a-csv-file"></a>.csv ファイルを作成する
リストを作成するには、ヘッダーなしの 2 列のコンマ区切り値 (.csv) リストを作成します。 IMEI 識別子を左側の列に、詳細を右側の列に追加します。 詳細の長さは、128 文字を上限とします。 現在の上限は .csv ファイルあたり 500 行です。

**シリアル番号が含まれている .csv ファイルをアップロード** – csv ファイル 1 つあたりデバイス 5,000 個または 5 MB を上限とする、2 つの列を持つヘッダーなしのコンマ区切り値のリスト (.csv) を作成します。

|||
|-|-|
|&lt;IMEI #1&gt;|&lt;デバイス 1 の詳細&gt;|
|&lt;IMEI #2&gt;|&lt;デバイス 2 の詳細&gt;|

    This .csv file when viewed in a text editor appears as:

    ```
    01 234567 890123,device details
    02 234567 890123,device details
    ```

**企業 ID の .csv リストを追加するには**

1. Azure Portal で、**[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。

2. [Intune] ブレードで **[デバイスの登録]** を選択してから、**[業務用デバイスの ID]** を選択します。

3. 新しい詳細情報が含まれるファイルをインポートする場合、そしてその情報で既存の情報が上書きされる場合は、**[既存の ID の詳細を上書きします]** を選択して、既存の詳細情報が、新しい詳細情報で置き換えられるようにします。

4. IMEI CSV ファイルに移動して、**[追加]** を選択します。

> [!IMPORTANT]
> 一部の Android デバイスには複数の IMEI 番号があります。 Intune は、1 台のデバイスにつき 1 つの IMEI 番号をインベントリします。 IMEI 番号をインポートするときに、その番号が Intune にインベントリされている IMEI ではない場合、デバイスは会社所有のデバイスではなく個人のデバイスとして分類されます。 1 台のデバイスに複数の IMEI 番号をインポートすると、インベントリされていない番号の登録状態は **[不明]** と表示されます。

インポート後、これらのデバイスは登録されている場合と、されていない場合があり、**登録済み** と **未接続** のいずれかの状態になります。 **未接続** の場合、デバイスは Intune サービスで通信に使われていません。

## <a name="delete-a-csv-list"></a>.csv リストを削除する

1. Azure Portal で、**[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。

2. [Intune] ブレードで **[デバイスの登録]** を選択してから、**[業務用デバイスの ID]** を選択します。

3. **[削除]** を選択します。

International Mobile Equipment Identifier の詳しい仕様については、「[3GGPP TS 23.003](https://portal.3gpp.org/desktopmodules/Specifications/SpecificationDetails.aspx?specificationId=729)」を参照してください。

