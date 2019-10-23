---
title: 米国政府機関のネットワーク エンドポイントのデプロイ - Microsoft Intune
titleSuffix: ''
description: Intune の米国政府機関のエンドポイントを確認します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5f6682cb-5fcd-4018-b7f7-71768ad3152e
ms.reviewer: kerimh
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: a5e52d1967ff6f5cf97334c099bc2b5b854ae87c
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502689"
---
# <a name="us-government-endpoints-for-microsoft-intune"></a>Microsoft Intune の米国政府機関のエンドポイント

このページには、Intune のデプロイでのプロキシ設定に必要な米国政府機関エンドポイントがリストされています。

ファイアウォールとプロキシ サーバーの背後にあるデバイスを管理するには、Intune に対する通信を有効にする必要があります。

- Intune クライアントは、**HTTP (80)** と **HTTPS (443)** を使用しているため、プロキシ サーバーは両方のプロトコルをサポートする必要があります
- Intune では、一部のタスク (ソフトウェア更新プログラムのダウンロードなど) で、manage.microsoft.com への認証されていないプロキシ サーバー アクセスが必要です

個々のクライアント コンピューターでプロキシ サーバーの設定を変更できます。 また、グループ ポリシーの設定を使用して、指定したプロキシ サーバーの背後にあるすべてのクライアント コンピューターの設定を変更することもできます。

マネージド デバイスは、 **[すべてのユーザー]** がファイアウォール経由でサービスにアクセスできるように構成する必要があります。

次の表は、Intune クライアントがアクセスするポートとサービスの一覧です。

|**エンドポイント**|**IP アドレス**|
|---------------------|-----------|
|*.manage.microsoft.us | 52.243.26.209 <br> 52.247.173.11 <br> 52.227.183.12 <br>52.227.180.205 <br> 52.227.178.107 <br> 13.72.185.168 <br> 52.227.173.179 <br> 52.227.175.242 <br> 13.72.39.209 <br> 52.243.26.209 <br> 52.247.173.11 |
| enterpriseregistration.microsoftonline.us | 13.72.188.239 <br> 13.72.55.179 |

## <a name="us-government-customer-designated-endpoints"></a>米国政府機関のお客様によって指定されたエンドポイント:
- Azure portal: https:\//portal.azure.us/ 
- Office 365: https:\//portal.office365.us/ 
- Intune ポータル サイト: https:\//portal.manage.microsoft.us/ 

## <a name="partner-service-endpoints-that-intune-depends-on"></a>Intune が依存するパートナー サービス エンドポイント:
- AAD Sync サービス: https:\//syncservice.gov.us.microsoftonline.com/DirectoryService.svc
- Evo STS: https:\//login.microsoftonline.us
- Directory プロキシ: https:\//directoryproxy.microsoftazure.us/DirectoryProxy.svc
- AAD Graph: https:\//directory.microsoftazure.us と https:\//graph.microsoftazure.us
- MS Graph: https:\//graph.microsoft.us
- ADRS: https:\//enterpriseregistration.microsoftonline.us
