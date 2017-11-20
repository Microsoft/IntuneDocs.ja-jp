---
title: "Power BI でデータ ウェアハウスに接続する | Microsoft Docs"
description: "Microsoft Power BI で使用するファイルをダウンロードし、Intune テナントに合わせて動的に生成されるインタラクティブなレポートを読み込むことができます。"
keywords: "Intune データ ウェアハウス"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 10/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5E5A35D3-88F8-441B-8A0B-C5D7A1E5137B
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: aa559d946456f215d4db925c8a2e8a42cfacf209
ms.sourcegitcommit: ce35790090ebe768d5f75c108e8d5934fd19c8c7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="connect-to-the-data-warehouse-with-power-bi"></a>Power BI でデータ ウェアハウスに接続する

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Microsoft Power BI で使用するファイルをダウンロードし、Intune テナントに合わせて動的に生成されるインタラクティブなレポートを読み込むことができます。 データ ウェアハウス Power BI ファイル (pbix) には、テナントへの接続設定と、次のサンプル レポートとグラフが含まれています。  

  -  [デバイス]
  -  登録
  -  アプリ保護ポリシー
  -  コンプライアンス ポリシー
  -  デバイスの構成プロファイル
  -  ソフトウェア更新プログラム
  -  デバイス インベントリ

また、登録、コンプライアンス、デバイス構成プロファイル、ソフトウェア更新プログラムの強調表示された傾向も確認できます。 サンプル グラフとレポートでは、わかりやすいフィルターをキャンバスに適用できます。 高度なフィルターを使用するには、Power BI Desktop の **[フィルター]** ウィンドウを確認します。

Power BI ファイルをダウンロードする方法と、Power BI で OData リンクを使用する方法については、次の手順を参照してください。

[!INCLUDE[reports-credential-reqs](./includes/reports-credential-reqs.md)]

## <a name="install-power-bi"></a>Power BI をインストールする

最新バージョンの Power BI Desktop をインストールします。 Power BI Desktop は [PowerBI.microsoft.com](https://powerbi.microsoft.com/en-us/desktop) からダウンロードできます。

## <a name="load-the-data-and-reports-using-the-power-bi-file-pbix"></a>Power BI ファイル (pbix) を使用してデータとレポートを読み込む

Power BI ファイル (pbix) には、テナントの接続情報と、データ ウェアハウス データ モデルに基づいて構築済みのレポートのセットが含まれています。 Power BI Desktop でファイルを開き、Azure AD にサインインします。 レポートでは Intune テナントからデータが読み込まれます。

> [!Important]  
> 各 Power BI ファイル (pbix) は、テナントの場所によって異なる場合があります。 複数の Intune テナントを管理している場合は、必ずそのテナントにログインした状態で Azure Portal からダウンロードしたファイルを使用します。  

1.  Azure Portal にサインインし、**[監視 + 管理]** > **[Intune]** の順に選択します。 **Intune** のリソースを検索することもできます。  
2.  **[Microsoft Intune データ ウェアハウス API (プレビュー)]** ブレードを開きます。
3.  **[Power BI ファイルのダウンロード]** を選択します。 拡張子が pbix のファイルが、指定した場所にダウンロードされます。
4.  Power BI でファイルを開きます。 *Intune データ ウェアハウス レポート*が読み込まれますが、テナント データの取得に少し時間がかかる可能性があります。
5.  **[更新]** を選択してテナント データを読み込み、レポートを確認します。
6.  Power BI が Azure Active Directory の資格情報で認証されていない場合は、資格情報の入力を求められます。 資格情報を選択するときに、認証方法として **[組織アカウント]** を選択します。

## <a name="load-the-data-in-power-bi-using-the-odata-link"></a>OData リンクを使用して Power BI でデータを読み込む

Azure AD に対してクライアントが認証されていると、OData URL は、データ ウェアハウス API で、データ モデルをレポート クライアントに公開している RESTful エンドポイントに接続します。 Power BI Desktop を使用して接続して独自のレポートを作成するするには、次の手順を実行します。 OAUTH2.0 認証と OData v4.0 標準をサポートしているクライアントであれば、Power BI Desktop だけでなく、OData URL にお気に入りの分析ツールを使用できます。

1.  Azure Portal にサインインし、**[監視 + 管理]** > **[Intune]** の順に選択します。 **Intune** のリソースを検索することもできます。  
2.  **[Microsoft Intune データ ウェアハウス API (プレビュー)]** ブレードを開きます。
3. たとえば、`https://fef.{yourinfo}.manage.microsoft.com/ReportingService/DataWarehouseFEService/dates?api-version=beta` などのレポート ブレードからカスタム フィード URL を取得します。
4. **Power BI Desktop** を開きます。
5. **[ホーム]** > **[データの取得]** を選択します。 **[OData フィード]** を選択します。
6. **[基本]** を選択します。
7. [URL] ボックスに **[OData URL]** を入力するか貼り付けます。
8. **[OK]** を選択します。
9. Power BI Desktop クライアントからテナントの Azure AD に対して認証されていない場合は、資格情報を入力します。 データにアクセスするには、OAuth 2.0 を使って Azure Active Directory (Azure AD) で認証を行う必要があります。  
    1.  **[組織のアカウント]** を選択します。  
    2.  ユーザー名とパスワードを入力します。  
    3.  **[サインイン]** を選択します。  
    4.  **[接続]** を選択します。  
10. **[読み込み]** を選択します。

## <a name="next-steps"></a>次のステップ

過去 1 週間に登録されたデバイス数/日など、環境について知りたい情報が見つかります。 Azure のブレードから取得した Intune データ ウェアハウス Power BI ファイル (pbix) を使用したレポートで、Intune テナントとクライアント数を分析できます。 また、Intune には、データを拡張または再利用することができる機能が多数あります。 Power BI と Intune データ ウェアハウス API を使用すると、次のようにさまざまな処理を実行できます。

<!-- -  You can use Power BI Desktop to create additional report types with your data. For example, you could create a custom chart representing the ratio of device manufactures in your enterprise. For more information about creating custom reports with Power BI and the Intune Data Warehouse, see `BLOG POST ON POWER BI`. -->
 -  テナント データを整理し、データを基に分析しやすくすることができます。 データの整理方法については、「[Data Warehouse Data Model](reports-ref-data-model.md)」(データ ウェアハウス データ モデル) を参照してください。
 -  RESTful インターフェイスからデータにアクセスし、データを自分のアプリに組み込むこともできます。 詳細については、「[REST クライアントを使用してのデータ ウェアハウス API からのデータの取得](reports-proc-data-rest.md)」を参照してください。
