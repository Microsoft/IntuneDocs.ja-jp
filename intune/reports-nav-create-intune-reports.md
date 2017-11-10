---
title: "Intune データ ウェアハウスを使用する | Microsoft Docs"
description: "Intune データ ウェアハウスを使用して、社内のモバイル環境を分析できるレポートを構築します。"
keywords: "Intune データ ウェアハウス"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 10/18/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 57019B11-DF9B-4D8A-95FE-254C75398DDE
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d485f0d53ac57a2f159ebd56b6b3823a8a49d5ad
ms.sourcegitcommit: e9f9fccccef691333143b7523d1b325ee7d1915a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/02/2017
---
# <a name="use-the-intune-data-warehouse"></a>Intune データ ウェアハウスを使用する

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune データ ウェアハウスを使用して、社内のモバイル環境を分析できるレポートを構築します。 たとえば、次のようなレポートがあります。
-   ライセンス購入の最適化に利用できる Intune に登録されているユーザーの傾向
-   モバイル デバイスの状態を確認できるアプリと OS バージョンの内訳
-   ポリシーの更新をスムーズにロールアウトできる登録とデバイス コンプライアンスの傾向

データ ウェアハウスを使用すると、モバイル環境について Azure Portal よりも詳細な情報にアクセスできます。 Intune データ ウェアハウスでは、次の情報にアクセスできます。

  -  Intune の履歴データ
  -  日単位の更新データ
  -  OData 標準を使用するデータ モデル

> [!Note]
> System Center Configuration Manager と Microsoft Intune でハイブリッド モバイル デバイス管理 (MDM) を使用している場合は、SCCM からデータを取得することができます。 Intune データが含まれるのは Intune データ ウェアハウスのみです。 カスタム レポートには SCCM Power BI ダッシュボードを使用できます。 詳細については、「[Announcing the Power BI solution template for System Center Configuration Manager]( https://powerbi.microsoft.com/blog/sccm-solution-template)」(System Center Configuration Manager 用 Power BI ソリューション テンプレートの発表) と 「[Create a Power BI report and dashboard](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/analytics/create-powerbi-report-dashboard)」(Power BI レポートとダッシュボードの作成) を参照してください。


> [!Important]  
> データ ウェアハウスの最新機能については、ベータ バージョンを使用して試すことができます。 ベータ バージョンを使用するには、URL にクエリ パラメーター `api-version=beta` を含める必要があります。 ベータ バージョンは、サポートされるサービスとして一般公開される前の機能を提供しています。 Intune に新しい機能が追加されると、ベータ バージョンの動作とデータ コントラクトが変わる可能性があります。 カスタム コードまたはレポート ツールがベータ バージョンに依存していると、今後の更新プログラムで使用できなくなる可能性があります。

**次のステップ**

- リンクを取得し、Power BI を使用して分析します。 手順については、「[Connect to the Intune Data Warehouse with Power BI](reports-proc-get-a-link-powerbi.md)」(Power BI で Intune データ ウェアハウスに接続する) を参照してください。
- リンクを使用して Power BI でカスタム レポートを作成します。 方法は、「[Power BI で OData フィードからレポートを作成する](reports-proc-create-with-odata.md)」を参照してください。
- Intune データ ウェアハウス API、データ モデル、エンティティ間の関係の詳細については、<!-- , and an example of creating a custom client to retrieve data,-->「[Intune データ ウェアハウス API](reports-nav-intune-data-warehouse.md)」を参照してください。