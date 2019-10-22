---
title: Power BI で OData フィードから Intune レポートを作成する
titleSuffix: Microsoft Intune
description: Power BI Desktop と Intune データ ウェアハウス API の対話型フィルターを使って、ツリーマップの視覚化を作成します。
keywords: Intune データ ウェアハウス
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/15/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: A2C8A336-29D3-47DF-BB4A-62748339391D
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: d00ae284ff4ea911cecb571cfe765eafe32fac02
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72490479"
---
# <a name="create-an-intune-report-from-the-odata-feed-with-power-bi"></a>Power BI で OData フィードから Intune レポートを作成する

この記事では、ユーザーが対話型のフィルターを使用して、Power BI Desktop を使用して Intune データのツリーマップの視覚化を作成する方法について説明します。 たとえば、CFO は、デバイスの全体的な分散が会社所有のデバイスと個人のデバイスとどのように比較されるかを知りたいと考えています。 ツリーマップを使用すると、デバイスの種類の合計数に関する洞察が得られます。 会社所有または個人所有の iOS、Android、Windows デバイスの数がわかります。

## <a name="overview-of-creating-the-chart"></a>グラフ作成の概要

このグラフを作成するには、次のようにします。
1. まだの場合は Power BI Desktop をインストールします。
2. Intune データ ウェアハウス データ モデルに接続し、モデルの現在のデータを取得します。
3. データ モデル間のリレーションシップを作成または管理します。
4. **デバイス** テーブルのデータでグラフを作成します。
5. 対話型フィルターを作成します。
6. 完成したグラフを表示します。

### <a name="a-note-about-tables-and-entities"></a>テーブルとエンティティに関する注意事項

Power BI でテーブルを処理します。 テーブルにはデータ フィールドが含まれます。 各データ フィールドにはデータ型があります。 フィールドには、そのデータ型のデータのみを格納できます。 データ型は、数値、文字列、日付などです。 Power BI のテーブルには、モデルを読み込むときにテナントから最近の履歴データが入力されます。 個々のデータは時間と共に変化しますが、テーブルの構造は、基になっているデータ モデルが更新されない限り変わりません。

"*エンティティ*" と "*テーブル*" という用語が混同される場合があります。 データモデルには、OData (Open Data Protocol) フィードを介してアクセスできます。 Power BI でテーブルと呼ばれるコンテナーが、OData ではエンティティと呼ばれます。 これらの用語はどちらも、データを保持する同じものを指しています。 OData の詳細については、「 [odata の概要](/odata/overview)」を参照してください。

## <a name="install-power-bi-desktop"></a>Power BI Desktop をインストールする

最新バージョンの Power BI Desktop をインストールします。 Power BI Desktop は [PowerBI.microsoft.com](https://powerbi.microsoft.com/desktop) からダウンロードできます。

## <a name="connect-to-the-odata-feed-for-the-intune-data-warehouse-for-your-tenant"></a>テナントの Intune データ ウェアハウスの OData フィードに接続する

> [!Note]  
> Intune の**レポート**に対するアクセス許可が必要です。 詳細については、「[承認](../reports-api-url.md)」を参照してください。

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインします。
2. **[Microsoft Intune - 概要]** ブレードの右側にある **[その他のタスク]** のデータ ウェアハウス リンクを選択して、 **[Intune データ ウェアハウス]** ウィンドウを開きます。
3. カスタム フィードの URL をコピーします。 例: `https://fef.tenant.manage.microsoft.com/ReportingService/DataWarehouseFEService?api-version=beta`
4. Power BI Desktop を開きます。
5. メニューバーで、**ファイル** >  **Odata フィード** > **データの取得** を選択します。
6. 前の手順でコピーしたカスタムフィード URL を **OData フィード** ウィンドウの url ボックスに貼り付けます。
7. **[基本]** を選択します。

    ![テナントの Intune データ ウェアハウスの OData フィード](./media/reports-proc-create-with-odata/reports-create-01-odatafeed.png)

8. **[OK]** を選択します。
9. **[組織のアカウント]** を選択し、Intune の資格情報でサインインします。

    ![組織のアカウントの資格情報](./media/reports-proc-create-with-odata/reports-create-02-org-account.png)

10. **[接続]** を選択します。 ナビゲーターが開き、Intune データ ウェアハウスのテーブルの一覧が表示されます。

    ![ナビゲーターのスクリーンショット - Data Warehouse のテーブル一覧](./media/reports-proc-create-with-odata/reports-create-02-loadentities.png)

11. **devices** テーブルと **ownerTypes** テーブルを選択します。  **[読み込み]** を選択します。 Power BI がモデルにデータを読み込みます。

## <a name="create-a-relationship"></a>リレーションシップを作成する

複数のテーブルをインポートして、1 つのテーブル内のデータだけでなく、複数のテーブルの関連するデータを分析することができます。 Power BI には**自動検出**と呼ばれる機能があり、リレーションシップの自動的な検索と作成が試みられます。 データ ウェアハウスのテーブルは、Power BI の自動検出機能と連動するように構築されています。 ただし、Power BI がリレーションシップを自動的に検索しない場合でも、そのリレーションシップを管理することは可能です。

![テーブル間の関連データのリレーションシップの管理](./media/reports-proc-create-with-odata/reports-create-03-managerelationships.png)

1. **[リレーションシップの管理]** を選択します。
2. Power BI でリレーションシップがまだ検出されていない場合は、 **[自動検出...]** を選択します。

リレーションシップの追加元と宛先の列が表示されます。 この例では、**devices** テーブルのデータ フィールド **ownerTypeKey** が、**ownerTypes** テーブルのデータ フィールド **ownerTypeKey** にリンクしています。 このリレーションシップを使って、**devices** テーブルに含まれているデバイスの種類コードの名前を調べます。

## <a name="create-a-treemap-visualization"></a>ツリーマップ視覚化を作成する

ツリーマップ グラフには、ボックス内のボックスとして階層データが示されます。 階層の各分岐は、サブ分岐を示す小さいボックスが含まれているボックスです。 Power BI デスクトップを使用して、デバイスの製造元の種類の相対的な量を示す、Intune テナントデータのツリーマップを作成できます。

![Power BI ツリーマップの視覚化](./media/reports-proc-create-with-odata/reports-create-03-treemap.png)

1. **[視覚化]** ウィンドウで、 **[ツリーマップ]** を見つけて選択します。 **ツリーマップ**グラフがレポートキャンバスに追加されます。
2. **[フィールド]** ウィンドウで、`devices` テーブルを見つけます。
3. `devices` テーブルを展開し、[`manufacturer` データ] フィールドを選択します。
4. [`manufacturer` データ] フィールドをレポートキャンバスにドラッグし、**ツリーマップ**グラフにドロップします。
5. `devices` テーブルの [`deviceKey` データ] フィールドを **[視覚化]** ウィンドウにドラッグし、 **[データフィールドの追加]** というラベルの付いた **[値]** セクションの下にドロップします。  

組織内のデバイスの製造元の分布を示すビジュアルが作成されます。

![ツリーマップとデータ - デバイスの製造元の分布](./media/reports-proc-create-with-odata/reports-create-06-treemapwdata.png)

## <a name="add-a-filter"></a>フィルターを追加する

アプリを使った追加の質問に回答できるように、ツリーマップにフィルターを追加できます。

1. フィルターを追加するには、レポート キャンバスを選択し、 **[視覚化]** の下の**スライサー アイコン** (![データ モデルとサポートされているリレーションシップが示されたツリーマップ](./media/reports-proc-create-with-odata/reports-create-slicer.png)) を選択します。 空の**スライサー**視覚エフェクトがキャンバスに表示されます。
2. **[フィールド]** ウィンドウで、`ownerTypes` テーブルを見つけます。
3. `ownerTypes` テーブルを展開し、[`ownerTypeName` データ] フィールドを選択します。
4. [`onwerTypeName` データ] フィールドを `ownerTypes` テーブルから **[フィルター]** ペインにドラッグし、 **[データフィールドの追加]** というラベルの付いた **[このページのフィルター]** セクションの下にドロップします。  

   `OwnerTypes` テーブルの下には、デバイスが会社所有または個人のどちらであるかを示すデータを含む `OwnerTypeKey`that というデータフィールドがあります。 このフィルターにはフレンドリ名を表示したいので、`ownerTypes` テーブルを探し、**ownerTypeName** をスライサーにドラッグします。 この例では、データ モデルがテーブル間のリレーションシップをサポートする方法を示します。

![ツリーマップとフィルター - テーブル間のリレーションシップのサポート](./media/reports-proc-create-with-odata/reports-create-08_ownertype.png)

会社所有デバイスと個人所有デバイスを切り替えることができる対話型フィルターができました。 このフィルターを使って、分布の違いを見ることができます。

1. スライサー内の**company**を選択すると、会社所有のデバイスの分布が表示されます。
2. スライサー内で**Personal**を選択して、個人所有のデバイスを表示します。

## <a name="next-steps"></a>次の手順

- Power BI のドキュメントで、Power BI Desktop での[リレーションシップの作成と管理](https://powerbi.microsoft.com/documentation/powerbi-desktop-create-and-manage-relationships/)についてさらに学習してください。
- [Intune データ ウェアハウス モデル](reports-ref-data-model.md)を確認してください。
