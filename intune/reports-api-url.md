---
title: Intune データ ウェアハウス API エンドポイント
titlesuffix: Microsoft Intune
description: リファレンス トピックでは Intune データ ウェアハウス API URL 構造について説明します。
keywords: Intune データ ウェアハウス
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/25/2018
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: A7A174EC-109D-4BB8-B460-F53AA2D033E6
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 05251e3aeb0c290a51c378f8c67f3d55149b63dc
ms.sourcegitcommit: e6013abd9669ddd0d6449f5c129d5b8850ea88f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/25/2018
ms.locfileid: "39254503"
---
# <a name="intune-data-warehouse-api-endpoint"></a>Intune データ ウェアハウス API エンドポイント

特定のロールベースのアクセス制御と Azure Active Directory 資格情報を使用するアカウントに、Intune データ ウェアハウス API を使用できます。 次に、OAuth 2.0 を使用して Azure AD に対して REST クライアントを承認します。 最後に、データ ウェアハウス リソースを呼び出すことができる有効な URL を形成します。

[!INCLUDE [reports-credential-reqs](./includes/reports-credential-reqs.md)]

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

| 要素 | 例 | 説明 |
|-------------------|------------|--------------------------------------------------------------------------------------------------------------------|
| location | msua06 | Azure Portal でデータ ウェアハウス API ブレードを表示すると、ベース URL を確認できます。 |
| entity-collection | dates | OData エンティティ コレクションの名前。 データ モデルのコレクションとエンティティの詳細については、「[Data Model](reports-ref-data-model.md)」(データ モデル) を参照してください。 |
| api-version | beta | Version はアクセスする API のバージョンです。 詳細については、「[API のバージョン情報](#API-version-information)」を参照してください。 |
| maxhistorydays | 7 | (省略可能) 取得する履歴の最大日数。 このパラメーターは任意のコレクションに適用できますが、キー プロパティの一部として `dateKey` を含むコレクションにのみ影響します。 詳細については、「[DateKey 範囲のフィルター](reports-api-url.md#datekey-range-filters)」を参照してください。 |

## <a name="api-version-information"></a>API のバージョン情報

API の現在のバージョンは `beta` です。 

## <a name="odata-query-options"></a>OData クエリのオプション

現在のバージョンは、OData クエリ パラメーター `$filter, $orderby, $select, $skip,` と `$top` をサポートしています。

## <a name="datekey-range-filters"></a>DateKey 範囲のフィルター

`DateKey` 範囲のフィルターは、キー プロパティとして `dateKey` を使用して一部のコレクションをダウンロードするデータ量を制限するために使用できます。 `DateKey` フィルターを使用すると、次の `$filter` クエリ パラメーターを指定することによって、サービス パフォーマンスを最適化できます。

1.  `$filter` 内で単独の `DateKey` は、`lt/le/eq/ge/gt` 演算子をサポートし、論理演算子 `and` と結合されます。これらは開始日や終了日にマッピングされることがあります。
2.  `maxhistorydays` は、カスタム クエリ オプションとして提供されます。<br>

## <a name="filter-examples"></a>フィルターの例

> [!NOTE]
> フィルターの例では、今日を 2018 年 2 月 21 日と想定しています。

|                             フィルター                             |           パフォーマンスの最適化           |                                          説明                                          |
|:--------------------------------------------------------------:|:--------------------------------------------:|:---------------------------------------------------------------------------------------------:|
|    `maxhistorydays=7`                                            |    フル                                      |    `DateKey` が 20180214 から 20180221 の間のデータを返します。                                     |
|    `$filter=DateKey eq 20180214`                                 |    フル                                      |    `DateKey` が 20180214 のデータを返します。                                                    |
|    `$filter=DateKey ge 20180214 and DateKey lt 20180221`         |    フル                                      |    `DateKey` が 20180214 から 20180220 の間のデータを返します。                                     |
|    `maxhistorydays=7&$filter=Id gt 1`                            |    部分、Id gt 1 は最適化されません    |    `DateKey` が 20180214 から 20180221 の間で、Id が 1 より大きい値のデータを返します。             |
|    `maxhistorydays=7&$filter=DateKey eq 20180214`                |    フル                                      |    `DateKey` が 20180214 のデータを返します。 `maxhistorydays` は無視されます。                            |
|    `$filter=DateKey eq 20180214 and Id gt 1`                     |    なし                                      |    `DateKey` 範囲のフィルターとして扱われないため、パフォーマンスは向上されません。                              |
|    `$filter=DateKey ne 20180214`                                 |    なし                                      |    `DateKey` 範囲のフィルターとして扱われないため、パフォーマンスは向上されません。                              |
|    `maxhistorydays=7&$filter=DateKey eq 20180214 and Id gt 1`    |    なし                                      |    `DateKey` 範囲のフィルターとして扱われないため、パフォーマンスは向上されません。 `maxhistorydays` は無視されます。    |
