---
title: "Intune データ ウェアハウス API | Microsoft Docs"
description: "API を使用して、企業のモバイル環境を分析するレポートを構築することができます。"
keywords: "Intune データ ウェアハウス"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 701D6CE9-43F6-4A29-8E84-E2B59931C635
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 5f03fd3a1557ef5d013fe695016ed0e3b119ee62
ms.sourcegitcommit: addf6a40caa22c22adfd2e2eff7d666cd1877e3c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2017
---
#  <a name="intune-data-warehouse-api"></a>Intune データ ウェアハウス API

Intune データ ウェアハウス API を使用すると、コンピューターで読み取ることができる Intune データにアクセスし、普段使用する分析ツールに利用することができます。 API を使用して、企業のモバイル環境を分析するレポートを構築することができます。 API では OData プロトコルを使用しています。OData プロトコルは次の標準のパターンに従います。

  -   要求および応答のヘッダー
  -   状態コード
  -   HTTP メソッド
  -   URL の表記規則
  -   メディアの種類
  -   ペイロード形式
  -   クエリ オプション

OData (Open Data Protocol) は、RESTful API を構築し、使用する際のベスト プラクティスが定義されている Organization for the Advancement of Structured Information Standards (OASIS) 標準です。 Intune データ ウェアハウスでは、OData バージョン 4.0 を使用しています。

この参照セクションでは、エンドポイント、サポートされる HTTP メソッド、戻り値のペイロードの形式、Intune データ ウェアハウス データ モデルのドキュメントの概要について説明します。

> [!Important]  
> データ ウェアハウスの最新機能については、ベータ バージョンを使用して試すことができます。 ベータ バージョンを使用するには、URL にクエリ パラメーター `api-version=beta` を含める必要があります。 ベータ バージョンは、サポートされるサービスとして一般公開される前の機能を提供しています。 Intune に新しい機能が追加されると、ベータ バージョンの動作とデータ コントラクトが変わる可能性があります。 カスタム コードまたはレポート ツールがベータ バージョンに依存していると、今後の更新プログラムで使用できなくなる可能性があります。 <!--If you experience problems with the beta service, follow [link to feedback process]() to report the issue or provide feedback.-->

<!-- ## OData custom client

You can access the Intune Data Warehouse data model through RESTful endpoints. To gain access to your data, your client must authorize with Microsoft Azure Active Directory (Azure AD) using OAuth 2.0. You first set up a web app and a client app in Azure, grant permissions to the client. Your local client will get authorization, can then communicate with the Data Warehouse endpoints.

For more information, see [Get data from the Data Warehouse API with a REST client](Get-data-REST.md) -->

## <a name="interacting-with-the-api"></a>API との対話

API を使用するには Azure AD による承認が必要です。 Azure AD は OAuth 2.0 を使用します。 承認が完了すると、HTTP GET 動詞を使用し、公開されているエンティティ コレクションに接続して、API からデータを取得できます。 詳細については、次のページを参照してください。

 -  [承認](reports-api-url.md)
 -  [API URL 構造](reports-api-url.md)

## <a name="intune-data-warehouse-data-model"></a>Intune データ ウェアハウスのデータ モデル

OData で抽象データ モデルとプロトコルを定義し、任意のデータ ソースが公開している情報に任意のクライアントがアクセスできるようにします。 データ モデルのドキュメント トピックでは、Intune データ ウェアハウス データ モデルの名前空間、エンティティ、リターン オブジェクトについて説明しています。 詳細については、「[Data Warehouse Data Model](reports-ref-data-model.md)」(データ ウェアハウスのデータ モデル) を参照してください。

## <a name="for-more-information"></a>詳細情報

[Azure AD の認証シナリオ](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios)  
[odata.org](http://www.odata.org)  
[OData Version 4.0](http://docs.oasis-open.org/odata/odata/v4.0/odata-v4.0-part1-protocol.html)  
