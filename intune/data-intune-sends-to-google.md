---
title: Intune から Google に送られるデータ
titleSuffix: Microsoft Intune
description: Intune から Google に送られるデータの一覧。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a5c3bec4-18ed-11e8-accf-0ed5f89f718b
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 78fef57849b8742bb10ece1717234af5cce3f4ba
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="data-intune-sends-to-google"></a>Intune から Google に送られるデータ

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

デバイスで Android デバイスの管理が有効になっている場合、Microsoft Intune は Google との接続を確立し、ユーザーとデバイスの情報を Google と共有します。 Microsoft Intune が接続を確立する前に、Google アカウントを作成する必要があります。

次の表は、デバイスでデバイス管理が有効になっているときに Microsoft Intune が Google に送信するデータの一覧です。


| Google に送信されるデータ | 説明 | 使用目的 | 例 |
|:---:|:---:|:---:|:---:|
| EnterpriseId | Gmail アカウントを Intune にバインドするときに、Google で開始されます。 | Intune と Google の間の通信に使用されるプライマリ識別子。  この通信には、ポリシーの設定、デバイスの管理、Android エンタープライズと Intune のバインド/バインド解除が含まれます。 | 一意の識別子 (形式の例: LC04eik8a6) |
| ポリシーの本文 | 新しいアプリや構成ポリシーを保存するときに、Intune で開始されます。 | デバイスにポリシーを適用します。 | アプリケーションまたは構成ポリシーのすべての構成済み設定のコレクションです。 ポリシーの一部として提供される場合、ネットワーク名、アプリケーション名、アプリ固有の設定など、顧客情報が含まれる可能性があります。 |
| デバイス データ | 仕事用プロファイルのデバイスのシナリオは、Intune への登録から始まります。 管理対象デバイスのデバイスのシナリオは、Google への登録から始まります。 | Intune と Google 間で、ポリシーの適用、デバイスの管理、一般的なレポート処理など、さまざまな操作のためにデバイス データ情報が送信されます。 | **デバイス名を表す一意の識別子。** 例: enterprises/LC04ebru7b/devices/3592d971168f9ae4<br>**ユーザー名を表す一意の識別子。** 例: Enterprises/LC04ebru7b/users/116838519924207449711<br>**デバイスの状態。** 例: アクティブ、無効、プロビジョニング。<br>**コンプライアンスの状態。** 例: 設定はサポートされていません、必要なアプリがありません<br>**ソフトウェア情報。** 例: ソフトウェアのバージョン、パッチ レベル。<br>**ネットワーク情報。** 例: IMEI、MEID、WifiMacAddress<br>**デバイスの設定。** 例: 暗号化レベルの情報、デバイスが不明なアプリを許可するかどうかの情報<br> JSON メッセージの例については後述します。 |
| newPassword | Intune で開始されます。 | デバイスのパスコードをリセットします。 | 新しいパスワードを表す文字列。 |
| Google ユーザー | Google | 仕事用プロファイル (BYOD) シナリオの場合に仕事用プロファイルを管理します。 | リンクされている Gmail アカウントを表す一意の識別子。 例: 114223373813435875042 |
| アプリケーション データ | アプリケーション ポリシーを保存するときに Intune で開始されます。 |  | アプリケーション名の文字列。 例: app:com.microsoft.windowsintune.companyportal |
| エンタープライズ サービス アカウント | Intune の要求時に Google で開始されます。 | このユーザーが関係するトランザクションに対して Intune と Google 間の認証に使用されます。 | 複数の部分に分かれています。<br> **エンタープライズ ID**: 以前に説明されています。<br>**UPN**: ユーザーの代理で認証に使用される UPN が生成されます。<br>例: w49d77900526190e26708c31c9e8a0@pfwp-commicrosoftonedfmdm2.google.com.iam.gserviceaccount.com<br>**キー**: 認証要求で使用され、暗号化されてサービスに格納された Base64 でエンコードされた BLOB ですが、次のような BLOB です。<br> ユーザーのキーを表す一意の識別子<br>例: a70d4d53eefbd781ce7ad6a6495c65eb15e74f1f |

**デバイス データの例**

Google の JSON デバイス メッセージの例を次に示します。



```
'{
  "name": "enterprises/LC02dhxx1r/devices/3195483be017acdc",
  "userId": "114223373813435875042",
  "adminType": "DEVICE_OWNER",
  "state": "ACTIVE",
  "appliedState": "ACTIVE",
  "policyCompliant": true,
  "enrollmentTime": "2017-10-06T15:17:41.702Z",
  "lastStatusReportTime": "2017-10-06T15:18:10.325Z",
  "lastPolicyComplianceReportTime": "2017-10-06T15:18:11.665Z",
  "lastPolicySyncTime": "2017-10-06T15:18:07.852Z",
  "appliedPolicyVersion": "2",
  "apiLevel": 26,
  "enrollmentTokenData": "brew 30 day token",
  "enrollmentTokenId": "yXdtW0_0L7c7Yo9DtRhEfPi3PcMqTorF3V1bTAw_eRs",
  "softwareInfo": {
    "androidVersion": "8.0.0",
    "cloudDpcVersionCode": 55314,
    "cloudDpcVersionName": "bv00553-rc14",
    "androidBuildNumber": "OPR4.170623.009",
    "deviceKernelVersion": "3.10.73-ga51b1600b7f8",
    "bootloaderVersion": "BHZ21c",
    "androidBuildTime": "2017-08-28T18:57:48Z",
    "securityPatchLevel": "2017-10-05",
    "androidBuildType": "user",
    "buildUser": "android-build"
  },
  "hardwareInfo": {
    "brand": "google",
    "hardware": "bullhead",
    "deviceBasebandVersion": "M8994F-2.6.39.3.03",
    "manufacturer": "LGE",
    "serialNumber": "01ed07873b3c20cd",
    "model": "Nexus 5X",
    "batteryShutdownTemperatures": [60.0],
    "batteryThrottlingTemperatures": [-3.4028235E38],
    "cpuShutdownTemperatures": [115.0, 115.0, 115.0, 115.0, 115.0, 115.0],
    "cpuThrottlingTemperatures": [60.0, 60.0, 60.0, 60.0, 60.0, 60.0],
    "gpuShutdownTemperatures": [-3.4028235E38],
    "gpuThrottlingTemperatures": [-3.4028235E38],
    "skinShutdownTemperatures": [-3.4028235E38],
    "skinThrottlingTemperatures": [37.0]
  },
  "displays": [{
    "name": "Built-in Screen",
    "refreshRate": 60,
    "state": "ON",
    "width": 1080,
    "height": 1920,
    "density": 420
  }],
  "appliedPolicyName": "enterprises/LC02dhxx1r/policies/default",
  "networkInfo": {
    "imei": "353626070676775",
    "wifiMacAddress": "02:00:00:00:00:00"
  },
  "memoryInfo": {
    "totalRam": "1902936064",
    "totalInternalStorage": "3169611776"
  },
  "memoryEvents": [{
    "eventType": "EXTERNAL_STORAGE_DETECTED",
    "createTime": "2017-10-06T15:18:09.959Z",
    "byteCount": "26720919552"
  }],
  "powerManagementEvents": [{
    "eventType": "BATTERY_LEVEL_COLLECTED",
    "createTime": "2017-10-06T15:18:09.939Z",
    "batteryLevel": 95.0
  }],
  "userName": "enterprises/LC02dhxx1r/users/114223373813435875042",
  "enrollmentTokenName": "enterprises/LC02dhxx1r/enrollmentTokens/yXdtW0_0L7c7Yo9DtRhEfPi3PcMqTorF3V1bTAw_eRs"
}'
```

Microsoft Intune で Android デバイス管理の使用を停止してデータを削除するには、Microsoft Intune の Android デバイス管理を無効にし、Google アカウントも削除する必要があります。 詳細については、Google アカウントのアカウントの管理方法を参照してください。


