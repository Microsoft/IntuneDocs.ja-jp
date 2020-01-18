---
title: デバイスを登録した場合に会社が確認できる情報
description: IT 部門でマネージド デバイスについて確認できることとできないことについて説明します。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/31/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 12655728-a1af-4d89-97bc-925fe36c0dc4
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.collection: ''
ms.openlocfilehash: 24601ef5c7a6451e2abfa64da37b21912d3cbace
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2020
ms.locfileid: "75858796"
---
# <a name="what-information-can-my-organization-see-when-i-enroll-my-device"></a>デバイスを登録した場合に組織が確認できる情報

Microsoft Intune にデバイスを登録しても、組織はユーザーの個人情報を閲覧できません。 デバイスを登録すると、デバイスのモデルやシリアル番号など、デバイスに関する特定の情報を閲覧するアクセス許可が組織に付与されます。 組織はこの情報を使用して、デバイス上の会社データを保護します。

**組織が閲覧できない情報:**

- 通話と Web 閲覧の履歴
- 電子メールとテキスト メッセージ
- 連絡先
- 予定表
- パスワード
- フォト アプリやカメラ ロールの内容を含む、画像
- ファイル

**組織が常に閲覧できる情報:**

- デバイス モデル (例: Google Pixel)
- デバイスの製造元 (例: Microsoft)
- オペレーティング システムとバージョン (例: iOS 12.0.1)
- アプリ インベントリとアプリの名前 (Microsoft Word など)。 個人用デバイス上では、組織はマネージド アプリ インベントリのみを閲覧できます。 会社が所有しているデバイスでは、組織はすべてのアプリ インベントリを閲覧できます。
- デバイスの所有者
- デバイス名
- デバイスのシリアル番号
- IMEI

**組織が閲覧できる可能性がある情報:**

- 電話番号:会社所有のデバイスの場合、ユーザーの完全な電話番号を確認できます。 個人所有のデバイスの場合、組織が確認できるのは、ユーザーの電話番号の最後の 4 桁のみです。 **デバイスの詳細**ページで、個々のデバイスの所有権の種類を確認できます。
- デバイスの記憶域スペース: 必要なアプリをインストールできない場合、組織がユーザーのデバイスの記憶域の容量を確認し、容量が少なすぎるかどうかを判断することがあります。  
- 場所:失われた監視対象の iOS デバイスを復旧する必要がある場合を除いて、組織がユーザーのデバイスの場所を確認することは絶対にできません。 監視対象のデバイスに関する詳細については、[Apple iOS のドキュメント](https://go.microsoft.com/fwlink/?linkid=853816)を確認してください。  
- アプリ インベントリの詳細:組織が Mobile Threat Defense を使用している場合、ユーザーの iOS デバイス上にあるアプリの詳細を閲覧することができます。 Mobile Threat Defense の詳細については、[こちら](you-are-prompted-to-install-mtd-ios.md)をご覧ください。 個人用デバイスを使用している場合、組織はマネージド アプリ インベントリのみを閲覧できます。 会社所有のデバイスを使用している場合、組織はすべてのアプリ インベントリを閲覧できます。
- ネットワーク情報: Android デバイスのネットワーク接続情報の一部は、組織のサポートが入手できる場合があります。 たとえば、デバイスを特定の建物内に維持するように組織が定めている場合、デバイスでは接続先のネットワークが識別されます。 
