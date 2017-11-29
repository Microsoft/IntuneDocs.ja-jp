---
title: "デバイスを登録した場合に会社が確認できる情報 | Microsoft Docs"
description: "IT 管理者が管理対象デバイスについて確認できることとできないことのリスト。"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 11/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 12655728-a1af-4d89-97bc-925fe36c0dc4
searchScope: User help
ROBOTS: 
ms.reviewer: esmich
ms.suite: ems
ms.openlocfilehash: 6595382606b9c53083e7beec9ca02a314abb5899
ms.sourcegitcommit: dc2595bec05206a826cd10cb834bf6043145c917
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/14/2017
---
# <a name="what-information-can-my-company-see-when-i-enroll-my-device"></a>デバイスを登録した場合に会社が確認できる情報

デバイスを管理対象として登録すると、デバイス上の特定の情報を表示する権限を会社に与えることになります。これは、デバイス上の会社のデータを保護するのに役立ちます。

**会社が確認できない情報**

- 通話と Web 閲覧の履歴
- 電子メールとテキスト メッセージ
- 連絡先
- 予定表
-   パスワード
- フォト アプリやカメラ ロールの内容を含む、画像

**会社が常に確認できる情報**

- デバイス モデル (例: Google Pixel)
- 製造元 (例: Microsoft)
- オペレーティング システム (例: iOS)
- アプリ名 (例: Microsoft Word)
- デバイスの所有者
- デバイス名
- シリアル番号

**会社が確認できる場合がある情報**

-  電話番号: **会社**が所有するデバイスの場合は、ユーザーの電話番号を確認できます。 **個人**が所有するデバイスの場合は、会社が確認できるのは、ユーザーの電話番号の最後の 4 桁のみです。 個々のデバイスの**所有権の種類**を確認するには、デバイスの **[デバイスの詳細]** ページを開きます。
-  場所: 監視対象となっている iOS デバイスを紛失した場合を除き、会社はユーザーのデバイスの場所を確認できません。 [確認方法](https://go.microsoft.com/fwlink/?linkid=853816)
- アプリ インベントリ: 会社で Mobile Threat Defense を使っている場合、iOS デバイス上のアプリの詳細を見ることができます。 Mobile Threat Defense の詳細については、[こちら](you-are-prompted-to-install-mtd-ios.md)をご覧ください。
- ネットワーク情報: Android デバイスのネットワーク接続情報の一部は、社内サポートが確認できる場合があります。 たとえば、デバイスを特定の建物内に維持するように会社が定めている場合、デバイスでは接続先のネットワークが識別されます。 
