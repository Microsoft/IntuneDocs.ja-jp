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
ms.openlocfilehash: d876c0268f38a09ea3729a7e19ee00b321ae897a
ms.sourcegitcommit: edd06a494a241d198ca9b0d3030c92195976e0d3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2019
ms.locfileid: "75000399"
---
# <a name="us-government-endpoints-for-microsoft-intune"></a>Microsoft Intune の米国政府機関のエンドポイント

このページには、Intune のデプロイでのプロキシ設定に必要な米国政府機関エンドポイントがリストされています。

ファイアウォールとプロキシ サーバーの背後にあるデバイスを管理するには、Intune に対する通信を有効にする必要があります。

- Intune クライアントは、**HTTP (80)** と **HTTPS (443)** を使用しているため、プロキシ サーバーは両方のプロトコルをサポートする必要があります
- Intune では、一部のタスク (ソフトウェア更新プログラムのダウンロードなど) で、manage.microsoft.com への認証されていないプロキシ サーバー アクセスが必要です

個々のクライアント コンピューターでプロキシ サーバーの設定を変更できます。 また、グループ ポリシーの設定を使用して、指定したプロキシ サーバーの背後にあるすべてのクライアント コンピューターの設定を変更することもできます。

マネージド デバイスは、**[すべてのユーザー]** がファイアウォール経由でサービスにアクセスできるように構成する必要があります。

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

## <a name="windows-push-notification-services"></a>Windows プッシュ通知サービス
モバイル デバイス管理 (MDM) を使用して管理されている Intune マネージド デバイスでは、デバイス アクションとその他の即時アクティビティに Windows プッシュ通知サービス (WNS) が必要です。 詳細については、「[WNS トラフィックをサポートするためのエンタープライズ ファイアウォールとプロキシ構成](https://docs.microsoft.com/windows/uwp/design/shell/tiles-and-notifications/firewall-allowlist-config)」を参照してください。

## <a name="apple-device-network-information"></a>Apple デバイス ネットワークの情報

|**使用目的**|**ホスト名 (IP アドレス/サブネット)**|**プロトコル**|**ポート**|
|------------|-----------|------------|-----------|
|Apple サーバーからコンテンツを取得して表示する|itunes.apple.com<br>\*.itunes.apple.com<br>\*.mzstatic.com<br>\*.phobos.apple.com<br>\*.phobos.itunes-apple.com.akadns.net|HTTP|80|
|APNS サーバーとの通信|#-courier.push.apple.com<br>'#' は、0 から 50 の乱数です。|TCP|5223 および 443|
|各種の関数には、インターネット、iTunes Store、macOS アプリ ストア、iCloud、メッセージングなどへのアクセスが含まれます。|phobos.apple.com<br>ocsp.apple.com<br>ax.itunes.apple.com<br>ax.itunes.apple.com.edgesuite.net|HTTP/HTTPS|80 または 443|

詳細については、次をご覧ください。

- [Apple ソフトウェア製品に使用される TCP ポートと UDP ポート](https://support.apple.com/HT202944)
- [macOS、iOS、iTunes のサーバホスト接続と iTunes のバックグラウンドプロセスについて](https://support.apple.com/HT201999)
- [macOS および iOS クライアントで Apple プッシュ通知が届かない場合](https://support.apple.com/HT203609)

## <a name="next-steps"></a>次の手順
[Microsoft Intune のネットワーク エンドポイント](intune-endpoints.md)

[Windows 10 の自動登録とデバイス登録](../enrollment/windows-enroll.md#registration-and-enrollment-cnames)