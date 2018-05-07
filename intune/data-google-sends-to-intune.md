---
title: Google から Intune に送られるデータ
titleSuffix: Microsoft Intune
description: Google から Intune に送られるデータの一覧。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: c379c8db-788a-454e-9098-665ea3bc7b56
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 368205b63fcd360adf66f964c6cae087f6da3dfc
ms.sourcegitcommit: 2162ed46d939b4a9b85fa4e7e9943f2fb5948f1e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/20/2018
---
# <a name="data-google-sends-to-intune"></a>Google から Intune に送られるデータ

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

デバイスで Android エンタープライズ デバイスの管理が有効になっている場合、Microsoft Intune は Google との接続を確立し、ユーザーとデバイスの情報が Intune と Google 間で共有されます。 Microsoft Intune が接続を確立する前に、Google アカウントを作成する必要があります。

次の表は、デバイスでデバイス管理が有効になっているときに Google が Intune に送信するデータの一覧です。


| Google から Intune に送られるデータ | 説明 | 使用目的 | 例 |
|:---:|:---:|:---:|:---:|
| エンタープライズ データ | Google の顧客のエンタープライズ ID | Intune と Google 間で顧客の情報をリンクします。 | **enterpriseId** の例: LC04eik8a6。<br>**名前**。 Android エンタープライズを設定するときに入力した管理者名。 例: Joe Smith。<br>**管理者の電子メール**。 Android エンタープライズの構成時に使用した YourAdmin@gmail.com。 |
| アプリケーション データ | 管理されている Play ストア アプリケーションのデータ。 | 利用可能または必要なユーザーまたはデバイスへのアプリケーションのターゲット設定。 | **アプリケーション名**の例: Contoso Warehouse Inventory Application。<br>**アプリケーションを表す一意の識別子**の例: app: com.Contoso.Warehouse.InventoryTracking |
| サービス アカウント | 特定の顧客の通話に使用する固有の内部 Google サービス アカウント。 | 顧客の代わりに Google に電話をかけるために使用します (アプリ、端末などを表示するため) | **名前**の例: InternalAccount@InternalService.com。<br>**キー**の例: ServiceAccountPassword |


Microsoft Intune で Android エンタープライズ デバイス管理の使用を停止してデータを削除するには、Microsoft Intune の Android エンタープライズ デバイス管理を無効にし、Google アカウントも削除する必要があります。 詳細については、Google アカウントのアカウントの管理方法を参照してください。


