---
title: "Power BI で OData フィードからレポートを作成する | Microsoft Docs"
description: "Power BI Desktop と Intune データ ウェアハウス API の対話型フィルターを使って、ツリーマップの視覚化を作成します。"
keywords: "Intune データ ウェアハウス"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 10/18/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: A2C8A336-29D3-47DF-BB4A-62748339391D
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 1e0ffcaa2ff8bd9e622c1d27f27564bd78df0276
ms.sourcegitcommit: ce35790090ebe768d5f75c108e8d5934fd19c8c7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="create-a-report-from-the-odata-feed-with-power-bi"></a>Power BI で OData フィードからレポートを作成する

このチュートリアルでは、Power BI Desktop と対話型フィルターを使って、ツリーマップの視覚化を作成します。 たとえば、CFO がデバイスの全体的な分布を会社所有デバイスと個人デバイスで比較したいような場合です。 ツリーマップを使用すると、デバイスの種類の合計数に関する洞察が得られます。 会社所有または個人所有の iOS、Android、Windows デバイスの数がわかります。

### <a name="overview-of-creating-the-chart"></a>グラフ作成の概要

このグラフを作成するには、次のようにします。
1. まだの場合は Power BI Desktop をインストールします。
2. Intune データ ウェアハウス データ モデルに接続し、モデルの現在のデータを取得します。
3. データ モデル間のリレーションシップを作成または管理します。
4. **デバイス** テーブルのデータでグラフを作成します。
5. 対話型フィルターを作成します。
6. 完成したグラフを表示します。

### <a name="a-note-about-tables-and-entities"></a>テーブルとエンティティに関する注意事項

Power BI でテーブルを処理します。 テーブルにはデータ フィールドが含まれます。 各データ フィールドにはデータ型があります。 フィールドには、そのデータ型のデータのみを格納できます。 データ型は、数値、文字列、日付などです。 Power BI のテーブルには、モデルを読み込むときにテナントから最近の履歴データが入力されます。 個々のデータは時間と共に変化しますが、テーブルの構造は、基になっているデータ モデルが更新されない限り変わりません。

"_エンティティ_" と "_テーブル_" という用語が混同される場合があります。 データ モデルには、OData フィードを使ってアクセスします。 Power BI でテーブルと呼ばれるコンテナーが、OData ではエンティティと呼ばれます。 これらの用語はどちらも、データを保持する同じものを指しています。

## <a name="install-power-bi-desktop"></a>Power BI Desktop をインストールする

最新バージョンの Power BI Desktop をインストールします。 Power BI Desktop は [PowerBI.microsoft.com](https://powerbi.microsoft.com/desktop) からダウンロードできます。

## <a name="connect-to-the-odata-feed-for-the-intune-data-warehouse-for-your-tenant"></a>テナントの Intune データ ウェアハウスの OData フィードに接続する

> [!Note]  
> Intune の**レポート**に対するアクセス許可が必要です。 詳細については、「[承認](reports-api-url.md)」を参照してください。

1. Azure ポータルにサインインします。
2. **[その他のサービス]** > **[監視 + 管理]** + **[Intune]** の順に選択します。
3. **[Intune データ ウェアハウス]** ブレードを開きます。
4. カスタム フィードの URL をコピーします。 例: `https://fef.tenant.manage.microsoft.com/ReportingService/DataWarehouseFEService?api-version=beta`
5. Power BI Desktop を開きます。
6. **[データの取得]** > **[Odata フィード]** を選びます。
7. **[OData フィード]** ウィンドウの [URL] ボックスにカスタム フィードの URL を貼り付けます。
8. **[基本]** を選択します。

    ![OData フィード](media/reports-create-01-odatafeed.png)

9. **[OK]** を選択します。
10. **[組織のアカウント]** を選択し、Intune の資格情報でサインインします。 

    ![組織のアカウントの資格情報](media/reports-create-02-org-account.png)

11. **[接続]** を選択します。 ナビゲーターが開き、Intune データ ウェアハウスのテーブルの一覧が表示されます。 

    ![ナビゲーター](media/reports-create-02-loadentities.png)

12. **devices** テーブルと **ownerTypes** テーブルを選択します。  **[読み込み]** を選択します。 Power BI がモデルにデータを読み込みます。

## <a name="create-a-relationship"></a>リレーションシップを作成する 

複数のテーブルをインポートして、1 つのテーブル内のデータだけでなく、複数のテーブルの関連するデータを分析することができます。  PowerBI には**自動検出**と呼ばれる機能があり、リレーションシップの自動的な検索と作成を試みます。 データ ウェアハウスのテーブルは、PowerBI の自動検出が機能するように作成されています。 ただし、PowerBI がリレーションシップを自動的に検索しない場合でも、リレーションシップを管理することは可能です。

![リレーションシップを管理する](media/reports-create-03-managerelationships.png)

1. **[リレーションシップの管理]** を選択します。
2. PowerBI でリレーションシップがまだ検出されていない場合は、**[自動検出]** を選択します。  
リレーションシップの追加元と宛先の列が表示されます。 この例では、**devices** テーブルのデータ フィールド **ownerTypeKey** が、**ownerTypes** テーブルのデータ フィールド **ownerTypeKey** にリンクしています。 リレーションシップを使って、**devices** テーブルのデバイス種類コードの一般的な名前を調べます。

## <a name="create-a-treemap-visualization"></a>ツリーマップ視覚化を作成する

ツリーマップ グラフには、ボックス内のボックスとして階層データが示されます。 階層の各分岐は、サブ分岐を示す小さいボックスが含まれているボックスです。 Power BI Desktop を使用して、Intune データのツリーマップを作成できます。

![視覚化 > ツリーマップ](media/reports-create-03-treemap.png)

1. グラフの種類を選びます。 **[Treemap]** を選びます。
2. データ モデルで、**devices** テーブルを探します。
3. **devices テーブル**を展開し、**[フィールド]** パネルで **manufacturer** データ フィールドを選択します。
4. **manufacturer** データ フィールドをレポート キャンバスのツリーマップ グラフにドラッグします。
5. **devices** テーブルの **deviceKey** データ フィールドを、**[視覚化]** ウィンドウの **[値]** セクションにドラッグして、**[データ フィールドをここにドラッグ]** ボックスにドロップします。  
組織内のデバイスの製造元の分布を示すビジュアルが作成されます。

![ツリーマップとデータ](media/reports-create-06-treemapwdata.png)

## <a name="add-a-filter"></a>フィルターを追加する

アプリを使った追加の質問に回答できるように、ツリーマップにフィルターを追加できます。 

1. レポート キャンバスを選択し、**[視覚化]** の**スライサー アイコン** (![ツリーマップとデータ](media/reports-create-slicer.png)) を選択してフィルターを追加します。
2. **ownerTypes** テーブルを探し、**ownerTypeName** データ フィールドを **[視覚化]** パネルの **[フィルター]** セクションにドラッグします。  
   devices テーブルに、デバイスが会社所有か個人所有かを示すコードを含む **OwnerTypeKey** データ フィールドがあります。 このフィルターにはフレンドリー名を表示したいので、**ownerTypes** テーブルを探し、**ownerTypeName** をドラッグします。 これは、データ モデルがテーブル間のリレーションシップをサポートする方法の例です。

![ツリーマップとフィルター](media/reports-create-08_ownertype.png)

会社所有デバイスと個人所有デバイスを切り替えて分布の違いを見ることができる対話型フィルターができました。

1. 会社所有デバイスの分布を表示するには **Company** を選択します。
2. 個人所有デバイスを表示するには **Personal** を選択します。

## <a name="next-steps"></a>次のステップ

 - Power BI のドキュメントで、Power BI Desktop での[リレーションシップの作成と管理](https://powerbi.microsoft.com/documentation/powerbi-desktop-create-and-manage-relationships/)についてさらに学習してください。
 - [Intune データ ウェアハウス モデル](https://docs.microsoft.com/intune/reports-ref-data-model)を確認してください。