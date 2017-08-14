---
title: "IMEI 識別子を Intune に追加する"
titleSuffix: Intune on Azure
description: "企業 ID (IMEI 番号) を Microsoft Intune に追加する方法について説明します。 \""
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 07/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 566ed16d-8030-42ee-bac9-5f8252a83012
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6b38bf2da70537d07a050fa21be9a2a3062ca84b
ms.sourcegitcommit: 79116d4c7f11bafc7c444fc9f5af80fa0b21224e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2017
---
# <a name="add-corporate-identifiers"></a>企業 ID を追加する

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune 管理者は、International Mobile Equipment Identifier (IMEI) 番号またはシリアル番号を記載しているコンマ区切り値 (.csv) ファイルを作成し、インポートできます。 Intune は、この識別子を使用して、デバイスの所有権を会社として指定します。 サポートされているすべてのプラットフォームの IMEI 番号を宣言できます。 iOS および Android デバイスのシリアル番号のみ宣言できます。 各 IMEI またはシリアル番号の一覧には管理目的で詳細を追加できます。

<!-- When you upload serial numbers for company-owned iOS devices, they must be paired with a corporate enrollment profile. Devices must then be enrolled using either Apple’s device enrollment program (DEP) or Apple Configurator to have them appear as company-owned. -->

Apple デバイスのシリアル番号の検索方法については、[こちら](https://support.apple.com/HT204308)をご覧ください。<br>
Android デバイスのシリアル番号の検索方法については、[こちら](https://support.google.com/store/answer/3333000)をご覧ください。

## <a name="add-corporate-identifiers"></a>企業 ID を追加する
リストを作成するには、ヘッダーなしの 2 列のコンマ区切り値 (.csv) リストを作成します。 IMEI またはシリアル番号を左側の列に、詳細を右側の列に追加します。 1 つの .csv ファイルにインポートできるのは、1 種類の ID、IMEI、またはシリアル番号のみです。 詳細の上限は 128 文字です。また、管理者のみが使用できます。 詳細はデバイスに表示されません。 現在の上限は .csv ファイルあたり 500 行です。

**シリアル番号が含まれている .csv ファイルをアップロード** – csv ファイル 1 つあたりデバイス 5,000 個または 5 MB を上限とする、2 つの列を持つヘッダーなしのコンマ区切り値のリスト (.csv) を作成します。

|||
|-|-|
|&lt;ID #1&gt;|&lt;デバイス 1 の詳細&gt;|
|&lt;ID #2&gt;|&lt;デバイス 2 の詳細&gt;|

この .csv ファイルをテキスト エディターで開くと、次のように表示されます。

```
01234567890123,device details
02234567890123,device details
```

> [!IMPORTANT]
> 一部の Android デバイスには複数の IMEI 番号があります。 Intune は、登録済みデバイスごとに 1 つの IMEI 番号のみを読み取ります。 IMEI 番号をインポートするときに、その番号が Intune にインベントリされている IMEI ではない場合、デバイスは会社所有のデバイスではなく個人のデバイスとして分類されます。 1 台のデバイスに複数の IMEI 番号をインポートすると、インベントリされていない番号の登録状態は **[不明]** と表示されます。<br>
>注: Android のシリアル番号は一意であることと存在することが保証されていません。 シリアル番号が信頼できるデバイス ID であるかどうかは、デバイスの供給元にご確認ください。
>デバイスから Intune に報告されたシリアル番号は、Android デバイスの [設定]/[バージョン情報] メニューに表示される ID と一致しない場合があります。 デバイスの製造元から報告されたシリアル番号の種類をご確認ください。


**企業 ID の .csv リストを追加するには**

1. Intune ポータルで **[デバイスの登録]**  >  **[登録の制限]** の順に選択し、**[業務用デバイスの ID]** を選択して、**[追加]** をクリックします。

 ![[追加] ボタンが強調表示された、[業務用デバイス ID] ワークスペースのスクリーンショット。](./media/add-corp-id.png)

2. **[ID の追加]** ブレードで **[IMEI]** または **[シリアル]** の ID の種類を指定します。 以前にインポートした番号が **[既存の ID の詳細を上書きします]** を適用するかどうかを指定できます。

3. フォルダー アイコンをクリックし、インポートするリストのパスを指定します。 .csv ファイルに移動して、**[追加]** を選択します。 **[更新]** をクリックすると、新しいデバイス ID が表示されます。

インポートされたデバイスが必ずしも登録されているとは限りません。 デバイスは **[登録済み]** または**[未接続]** のどちらかの状態になります。 **未接続** の場合、デバイスは Intune サービスで通信に使われていません。

## <a name="delete-corporate-identifiers"></a>企業 ID を削除する

1. Intune ポータルで **[デバイスの登録]**  >  **[登録の制限]** の順に選択し、**[業務用デバイスの ID]** を選択して、**[削除]** を選択します。

3. **[Delete Identifiers (ID の削除)]** ブレードで削除するデバイス ID の .csv ファイルを参照し、**[削除]** をクリックします。

## <a name="imei-specifications"></a>IMEI の仕様
International Mobile Equipment Identifier の詳しい仕様については、「[3GGPP TS 23.003](https://portal.3gpp.org/desktopmodules/Specifications/SpecificationDetails.aspx?specificationId=729)」を参照してください。
