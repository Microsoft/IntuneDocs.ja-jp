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
ms.sourcegitcommit: 15415f9f31d520d66257df3a7e134e4b1de8467c
ms.openlocfilehash: 8c9e6b39ee01697d993e5738ec35e8a64fc8e236
ms.lasthandoff: 04/07/2017

---

# <a name="add-corporate-identifiers"></a>企業 ID を追加する

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

IT 管理者は、会社所有のデバイスを識別するための International Mobile Equipment Identity (IMEI) を記載しているコンマ区切り (.csv) ファイルを作成し、インポートできます。 各 IMEI 番号の一覧には管理目的で詳細を追加できます。

<!-- When you upload serial numbers for company-owned iOS devices, they must be paired with a corporate enrollment profile. Devices must then be enrolled using either Apple’s device enrollment program (DEP) or Apple Configurator to have them appear as company-owned. -->

## <a name="add-corporate-identifiers"></a>企業 ID を追加する
リストを作成するには、ヘッダーなしの 2 列のコンマ区切り値 (.csv) リストを作成します。 IMEI 識別子を左側の列に、詳細を右側の列に追加します。 詳細の上限は 128 文字です。また、管理者のみが使用できます。 詳細はデバイスに表示されません。 現在の上限は .csv ファイルあたり 500 行です。

**シリアル番号が含まれている .csv ファイルをアップロード** – csv ファイル 1 つあたりデバイス 5,000 個または 5 MB を上限とする、2 つの列を持つヘッダーなしのコンマ区切り値のリスト (.csv) を作成します。 

|||
|-|-|
|&lt;IMEI #1&gt;|&lt;デバイス 1 の詳細&gt;|
|&lt;IMEI #2&gt;|&lt;デバイス 2 の詳細&gt;|

この .csv ファイルをテキスト エディターで開くと、次のように表示されます。

```
01234567890123,device details
02234567890123,device details
```


> [!IMPORTANT]
> 一部の Android デバイスには複数の IMEI 番号があります。 Intune は、1 台のデバイスにつき 1 つの IMEI 番号をインベントリします。 IMEI 番号をインポートするときに、その番号が Intune にインベントリされている IMEI ではない場合、デバイスは会社所有のデバイスではなく個人のデバイスとして分類されます。 1 台のデバイスに複数の IMEI 番号をインポートすると、インベントリされていない番号の登録状態は **[不明]** と表示されます。

**企業 ID の .csv リストを追加するには**

1. Azure Portal で、**[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。

2. Intune ブレードで **[デバイスの登録]** > **[登録の制限]** の順に選び、**[業務用デバイスの ID]** を選択して、**[追加]** をクリックします。

3. **[ID の追加]** ブレードで識別子を指定し、**[IMEI]** を入力します。 以前にインポートした番号が **[既存の ID の詳細を上書きします]** を適用するかどうかを指定できます。  

4. フォルダー アイコンをクリックし、インポートするリストのパスを指定します。 IMEI CSV ファイルに移動して、**[追加]** を選択します。

インポート後、これらのデバイスは登録されている場合と、されていない場合があり、**登録済み** と **未接続** のいずれかの状態になります。 **未接続** の場合、デバイスは Intune サービスで通信に使われていません。

## <a name="delete--corporate-identifiers"></a>企業 ID を削除する

1. Azure Portal で、**[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。

2. Intune ブレードで **[デバイスの登録]** > **[登録の制限]** の順に選び、**[業務用デバイスの ID]** を選び、**[削除]** を選びます。

3. **[Delete Identifiers (ID の削除)]** ブレードで削除するデバイス ID の .csv ファイルを参照し、**[削除]** をクリックします。

## <a name="imei-specifications"></a>IMEI の仕様
International Mobile Equipment Identifier の詳しい仕様については、「[3GGPP TS 23.003](https://portal.3gpp.org/desktopmodules/Specifications/SpecificationDetails.aspx?specificationId=729)」を参照してください。

