---
title: "Android デバイスは暗号化されるように見えるが、ポータル サイトではそのように認識されていない"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 02/22/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ba593c08-1a78-4013-8525-b45a948772ec
searchScope:
- Company Portal
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
translationtype: Human Translation
ms.sourcegitcommit: 92dd0cedb0e70bb1bd2e4de0b0284fe33fcbeddc
ms.openlocfilehash: 661b4fbfd08f2e29af997d848dc44e22013d263f
ms.lasthandoff: 02/23/2017


---


# <a name="your-android-device-seems-to-be-encrypted-but-company-portal-says-otherwise"></a>Android デバイスは暗号化されるように見えるが、ポータル サイトではそのように認識されていない

デバイスを暗号化する場合、自分しか知らない秘密キーを使用してデバイス上の情報をエンコードするため、承認されていないユーザーはアクセスできません。 ユーザーの情報を確実にセキュリティで保護するために、組織ではまず、企業のファイル、電子メール、またはデータにアクセスする前にユーザーに Android デバイスを暗号化するよう求める必要があります。

バージョン 7.0 以上の一部の Android デバイスでは、特定の Android プラットフォームの標準に準拠していない方法でデータを暗号化します。 これらのデバイスは既定で暗号化されているように見えますが、Intune ではこのような方法は、デバイスに物理的にアクセスできる悪意のあるユーザーがデバイスの情報を盗み出す危険性があると認識されます。

> [!Note]
> Microsoft では、これらの問題を解決するために製造元のリストを作成し、適宜、更新する予定です。 

## <a name="an-incomplete-list-of-devices"></a>デバイスの不完全なリスト

次のデバイスのいずれかの場合は、この問題が発生します。

- [Huawei Honor 8](http://consumer.huawei.com/en/support/mobile-phones/honor8_en-sup.htm)
- [Huawei P9](http://consumer.huawei.com/mobile-phones/p9/index.html)

## <a name="solutions"></a>ソリューション

デバイスで Android 6.0 以降にダウングレードできる場合は、ダウングレードします。 デバイスのダウングレードには、データ損失のリスクがあります。 そのため、IT 管理者に問い合わせて、この問題を解決することをお勧めします。 IT 管理者の連絡先情報は、[ポータル Web サイト](http://portal.manage.microsoft.com)で入手できます。

