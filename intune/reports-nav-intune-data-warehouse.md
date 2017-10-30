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
ms.openlocfilehash: a0d6bcb4ccac3563dd642ec0ad621645b7053dea
ms.sourcegitcommit: bb2c181fd6de929cf1e5d3856e048d617eb72063
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/20/2017
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

## <a name="odata-custom-client"></a>OData カスタム クライアント

RESTful エンドポイント経由で Intune データ ウェアハウスのデータ モデルにアクセスします。 データにアクセスするには、OAuth 2.0 を利用し、Azure Active Directory (Azure AD) でクライアントを認証する必要があります。 最初に Azure で Web アプリとクライアント アプリを設定し、クライアントにアクセス許可を与えます。 ローカル クライアントに承認が与えられ、データ ウェアハウスのエンドポイントと通信できるようになります。

詳細については、「[REST クライアントを使用してのデータ ウェアハウス API からのデータの取得](reports-proc-data-rest.md)」を参照してください。

> [!Note]  
> コードのサンプルは、Github の [GitHub Intune データ ウェアハウス リポジトリ](https://github.com/Microsoft/Intune-Data-Warehouse)で入手できます。

## <a name="interacting-with-the-api"></a>API との対話

API を使用するには Azure AD による承認が必要です。 Azure AD は OAuth 2.0 を使用します。 承認が完了すると、HTTP GET 動詞を使用し、公開されているエンティティ コレクションに接続して、API からデータを取得できます。 詳細については、次のページを参照してください。

 -  [承認](reports-api-url.md)
 -  [API URL 構造](reports-api-url.md)

## <a name="intune-data-warehouse-data-model"></a>Intune データ ウェアハウスのデータ モデル

OData で抽象データ モデルとプロトコルを定義し、任意のデータ ソースが公開している情報に任意のクライアントがアクセスできるようにします。 データ モデルのドキュメント トピックでは、Intune データ ウェアハウス データ モデルの名前空間、エンティティ、リターン オブジェクトについて説明しています。 詳細については、「[Data Warehouse Data Model](reports-ref-data-model.md)」(データ ウェアハウスのデータ モデル) を参照してください。

## <a name="next-steps"></a>次のステップ

「[Azure AD の認証シナリオ](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios)」を読んで、Azure AD の操作についてさらに詳しく学習します。

[odata.org](http://www.odata.org) で OData のリソースを探します。
  
「[OData Version 4.0] (http://docs.oasis-open.org/odata/odata/v4.0/odata-v4.0-part1-protocol.html)」で OData Version 4.0 標準を確認します  
