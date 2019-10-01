---
title: Power BI でデータ ウェアハウスに接続する
titleSuffix: Microsoft Intune
description: Microsoft Power BI で使用するファイルをダウンロードし、Microsoft Intune テナントに合わせて動的に生成されるインタラクティブなレポートを読み込むことができます。
keywords: Intune データ ウェアハウス
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/14/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 5E5A35D3-88F8-441B-8A0B-C5D7A1E5137B
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7bc3247399341a59533e87fc5e21a44c061acddd
ms.sourcegitcommit: b30a2ba2b67aa2fc3421f0b2f6c5f361a0de612a
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 08/14/2019
ms.locfileid: "71303199"
---
# <a name="connect-to-the-data-warehouse-with-power-bi"></a>Power BI でデータ ウェアハウスに接続する

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Power BI コンプライアンス アプリを使用すると、Intune テナントに関する対話型で動的に生成されたレポートを読み込むことができます。 さらに、OData リンクを使用して Power BI にテナント データを読み込むことができます。 Intune にはテナントへの接続設定機能があるので、以下に関連するサンプル レポートとグラフを表示することができます。  

- [デバイス]
- 登録
- アプリ保護ポリシー
- コンプライアンス ポリシー
- デバイスの構成プロファイル
- ソフトウェア更新プログラム
- デバイス インベントリ

また、登録、コンプライアンス、デバイス構成プロファイル、ソフトウェア更新プログラムの強調表示された傾向も確認できます。 サンプル グラフとレポートでは、わかりやすいフィルターをキャンバスに適用できます。 高度なフィルターを使用するには、Power BI Desktop の **[フィルター]** ウィンドウを確認します。

Power BI ファイルをダウンロードする方法と、Power BI で OData リンクを使用する方法については、次の手順を参照してください。

[!INCLUDE [reports-credential-reqs](./includes/reports-credential-reqs.md)]

## <a name="install-power-bi"></a>Power BI をインストールする

最新バージョンの [Power BI Desktop](https://aka.ms/intune/datawarehouseapi/installpowerbi) をインストールします。 詳細については、「[Power BI Desktop](https://powerbi.microsoft.com/desktop)」を参照してください。

## <a name="load-the-data-and-reports-using-the-power-bi-intune-compliance-data-warehouse-app"></a>Power BI の Intune Compliance Data Warehouse アプリを使用してデータとレポートを読み込む

Power BI の [Intune Compliance (Data Warehouse)](https://aka.ms/intune/datawarehouseapi/getpowerbiapp) アプリには、テナントの接続情報と、データ ウェアハウス データ モデルに基づいた構築済みのレポートのセットが含まれています。

1. インストール プロセスを開始するには、[Intune Compliance (Data Warehouse)](https://aka.ms/intune/datawarehouseapi/getpowerbiapp) アプリの **[AppSource]** ページに移動します。
2. **[今すぐ入手]** する ボタンをクリックし、 **[続行]** をクリックします。
3. Power BI アプリのインストールを求めるメッセージが表示されたら、 **[インストール]** をクリックします。
4. インストールが完了したら、[ **Intune コンプライアンス (データウェアハウス)** アプリ] タイルをクリックします。
5. **[接続]** ボタンをクリックします。 **[Connect to Intune Compliance (Data Warehouse)]\(Intune Compliance (Data Warehouse) への接続\)** ダイアログが表示されます。
6. **[サインイン]** ボタンをクリックします。
7. 表示するレポートがあるテナントの Intune データ ウェアハウスにアクセスできるユーザー アカウントでサインインします。
8. 含まれているダッシュボードを表示するには、 **[ダッシュボード]** タブをクリックし、 **[コンプライアンスの概要]** ダッシュボードをクリックします。
9. 使用できるすべてのレポートを表示するには、 **[レポート]** タブをクリックし、 **[対応]** v1.0 レポートをクリックします。 下部にあるタブをクリックして、レポートのページを参照します。
10. 後でこれらのレポートに簡単に戻ることができるようにするには、 **[Compliance V1.0]** レポートの横にある星をクリックします。 これで、Power BI のお気に入りにレポートが追加されます。

また、Intune ポータルからアプリをインストールすることもできます。

1. Azure Portal にサインインし、 **[監視 + 管理]**  >  **[Intune]** の順に選択します。 Intune のリソースを検索することもできます。
2. **[Intune データ ウェアハウスの設定]** ブレードを開きます。
3. **[Get Power BI App]\(Power BI アプリの取得\)** を選択して、ブラウザーでテナント用に事前に作成された Power BI レポートにアクセスおよび共有します。
4. 上記の手順 2-10 を実行します。

## <a name="load-the-data-in-power-bi-using-the-odata-link"></a>OData リンクを使用して Power BI でデータを読み込む

Azure AD に対してクライアントが認証されていると、OData URL は、データ ウェアハウス API で、データ モデルをレポート クライアントに公開している RESTful エンドポイントに接続します。 Power BI Desktop を使用して接続して独自のレポートを作成するするには、次の手順を実行します。 OAUTH2.0 認証と OData v4.0 標準をサポートしているクライアントであれば、Power BI Desktop だけでなく、OData URL にお気に入りの分析ツールを使用できます。

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインします。
2. 概要 ブレードの右側にある **その他のタスク** セクションで、**Intune データウェアハウスのセットアップ** をクリックします。 **Intune データウェアハウス**ブレードが表示されます。
3. たとえば、`https://fef.{yourinfo}.manage.microsoft.com/ReportingService/DataWarehouseFEService/dates?api-version=v1.0` などのレポート ブレードからカスタム フィード URL を取得します。
4. **Power BI Desktop** を開きます。
5. **[ホーム]**  >  **[データの取得]** を選択します。 **[OData フィード]** を選択します。
6. **[基本]** を選択します。
7. [URL] ボックスに **[OData URL]** を入力するか貼り付けます。
8. **[OK]** を選択します。
9. Power BI Desktop クライアントからテナントの Azure AD に対して認証されていない場合は、資格情報を入力します。 データにアクセスするには、OAuth 2.0 を使って Azure Active Directory (Azure AD) で認証を行う必要があります。  
    1. **[組織のアカウント]** を選択します。  
    2. ユーザー名とパスワードを入力します。  
    3. **[サインイン]** を選択します。  
    4. **[接続]** を選択します。  
10. **[読み込み]** を選択します。

## <a name="next-steps"></a>次の手順

過去 1 週間に登録されたデバイス数/日など、環境について知りたい情報が見つかります。 Azure のブレードから取得した Intune データ ウェアハウス Power BI レポートを使用して、Intune テナントとクライアント数を分析できます。 また、Intune には、データを拡張または再利用することができる機能が多数あります。 Power BI と Intune Data Warehouse API には、以下のような追加の機能があります。

<!-- - You can use Power BI Desktop to create additional report types with your data. For example, you could create a custom chart representing the ratio of device manufactures in your enterprise. For more information about creating custom reports with Power BI and the Intune Data Warehouse, see `BLOG POST ON POWER BI`. -->
- テナント データを整理し、データを基に分析しやすくすることができます。 データの整理方法については、「[Data Warehouse Data Model](reports-ref-data-model.md)」(データ ウェアハウス データ モデル) を参照してください。
- RESTful インターフェイスからデータにアクセスし、データを自分のアプリに組み込むこともできます。 詳細については、「[REST クライアントを使用してのデータ ウェアハウス API からのデータの取得](reports-proc-data-rest.md)」を参照してください。
