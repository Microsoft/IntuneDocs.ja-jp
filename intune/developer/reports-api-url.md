---
title: Intune データ ウェアハウス API エンドポイント
titleSuffix: Microsoft Intune
description: このリファレンス トピックでは Microsoft Intune データ ウェアハウス API URL 構造について説明します。 フィルターの例が提供されます。
keywords: Intune データ ウェアハウス
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/03/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: A7A174EC-109D-4BB8-B460-F53AA2D033E6
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: e19cc606792c59d2f5676aeca41d862308f1ab32
ms.sourcegitcommit: 8d7406b75ef0d75cc2ed03b1a5e5f74ff10b98c0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 01/03/2020
ms.locfileid: "75654143"
---
# <a name="intune-data-warehouse-api-endpoint"></a>Intune データ ウェアハウス API エンドポイント

特定のロールベースのアクセス制御と Azure Active Directory 資格情報を使用するアカウントに、Intune データ ウェアハウス API を使用できます。 次に、OAuth 2.0 を使用して Azure AD に対して REST クライアントを承認します。 最後に、データ ウェアハウス リソースを呼び出すことができる有効な URL を形成します。

[!INCLUDE [reports-credential-reqs](../includes/reports-credential-reqs.md)]

## <a name="authorization"></a>承認

Azure Active Directory (Azure AD) では、OAuth 2.0 を使用して Azure AD テナントの Web アプリケーションと Web API へのアクセスを承認できます。 このガイドは言語に依存していません。いずれのオープンソース ライブラリも使用せずに、HTTP メッセージを送受信する方法について説明します。 OAuth 2.0 承認コード フローについては、OAuth 2.0 仕様の[セクション 4.1](https://tools.ietf.org/html/rfc6749#section-4.1) を参照してください。

詳細については、「[OAuth 2.0 と Azure Active Directory を使用した Web アプリケーションへのアクセスの承認](https://docs.microsoft.com/azure/active-directory/develop/active-directory-protocols-oauth-code)」を参照してください。

## <a name="api-url-structure"></a>API URL 構造

データ ウェアハウス API エンドポイントは、各セットのエンティティを読み取ります。 API は、**GET** HTTP 動詞と、クエリ オプションのサブセットをサポートしています。

Intune の URL は、次の書式を使用しています。  
`https://fef.{location}.manage.microsoft.com/ReportingService/DataWarehouseFEService/{entity-collection}?api-version={api-version}`

> [!NOTE]
> 上記の URL では、次の表に示されている詳細に基づいて `{location}`、`{entity-collection}`、`{api-version}` を置き換えます。

URL には、次の要素が含まれています。

| 要素 | 例 | [説明] |
|-------------------|------------|--------------------------------------------------------------------------------------------------------------------|
| location | msua06 | Azure Portal でデータ ウェアハウス API ブレードを表示すると、ベース URL を確認できます。 |
| entity-collection | devicePropertyHistories | OData エンティティ コレクションの名前。 データ モデルのコレクションとエンティティの詳細については、「[Data Model](reports-ref-data-model.md)」(データ モデル) を参照してください。 |
| api-version | beta | Version はアクセスする API のバージョンです。 詳細については、「[API のバージョン情報](reports-api-url.md#api-version-information)」を参照してください。 |
| maxhistorydays | 7 | (省略可能) 取得する履歴の最大日数。 このパラメーターは任意のコレクションに適用できますが、キー プロパティの一部として `dateKey` を含むコレクションにのみ影響します。 詳細については、「[DateKey 範囲のフィルター](reports-api-url.md#datekey-range-filters)」を参照してください。 |

## <a name="api-version-information"></a>API のバージョン情報

クエリ パラメーター  `api-version=v1.0` を設定することにより、Intune データ ウェアハウスの v1.0 バージョンを使用できるようになりました。 Data Warehouse 内のコレクションに対する更新は本質的に追加であり、既存のシナリオが使用できなくなることはありません。

データ ウェアハウスの最新機能については、ベータ バージョンを使用して試すことができます。 ベータ バージョンを使用するには、URL にクエリ パラメーター  `api-version=beta` を含める必要があります。 ベータ バージョンは、サポートされるサービスとして一般公開される前の機能を提供しています。 Intune に新しい機能が追加されると、ベータ バージョンの動作とデータ コントラクトが変わる可能性があります。 カスタム コードまたはレポート ツールがベータ バージョンに依存していると、今後の更新プログラムで使用できなくなる可能性があります。

## <a name="odata-query-options"></a>OData クエリのオプション

現在のバージョンは、OData クエリ パラメーター `$filter`、`$select`、`$skip,`、および `$top` をサポートしています。 `$filter` では、列が該当する場合は `DateKey` または `RowLastModifiedDateTimeUTC` のみがサポートされ、その他のプロパティでは正しくない要求がトリガーされます。

## <a name="datekey-range-filters"></a>DateKey 範囲のフィルター

`DateKey` 範囲のフィルターは、キー プロパティとして `dateKey` を使用して一部のコレクションをダウンロードするデータ量を制限するために使用できます。 `DateKey` フィルターを使用すると、次の `$filter` クエリ パラメーターを指定することによって、サービス パフォーマンスを最適化できます。

1. `$filter` 内で単独の `DateKey` は、`lt/le/eq/ge/gt` 演算子をサポートし、論理演算子 `and` と結合されます。これらは開始日や終了日にマッピングされることがあります。
2. `maxhistorydays` は、カスタム クエリ オプションとして提供されます。<br>

## <a name="filter-examples"></a>フィルターの例

> [!NOTE]
> フィルターの例では、今日を 2019 年 2 月 21 日と想定しています。

|                             フィルター                             |           パフォーマンスの最適化           |                                          [説明]                                          |
|:--------------------------------------------------------------:|:--------------------------------------------:|:---------------------------------------------------------------------------------------------:|
|    `maxhistorydays=7`                                            |    完全                                      |    `DateKey` が 20180214 から 20180221 の間のデータを返します。                                     |
|    `$filter=DateKey eq 20180214`                                 |    完全                                      |    `DateKey` が 20180214 のデータを返します。                                                    |
|    `$filter=DateKey ge 20180214 and DateKey lt 20180221`         |    完全                                      |    `DateKey` が 20180214 から 20180220 の間のデータを返します。                                     |
|    `maxhistorydays=7&$filter=DateKey eq 20180214`                |    完全                                      |    `DateKey` が 20180214 のデータを返します。 `maxhistorydays` は無視されます。                            |
|    `$filter=RowLastModifiedDateTimeUTC ge 2018-02-21T23:18:51.3277273Z`                                |    完全                                       |    `RowLastModifiedDateTimeUTC` が `2018-02-21T23:18:51.3277273Z` 以上のデータを返します                             |
