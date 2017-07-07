---
title: "Android デバイスが暗号化されているように見える"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 05/25/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ba593c08-1a78-4013-8525-b45a948772ec
searchScope: User help
ROBOTS: 
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 269ad7968242f8f5ce7095c9c73347987675e846
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2017
---
# <a name="your-android-device-seems-to-be-encrypted-but-company-portal-says-otherwise"></a>Android デバイスは暗号化されるように見えるが、ポータル サイトではそのように認識されていない

デバイスを暗号化する場合、自分しか知らない秘密キーを使用してデバイス上の情報をエンコードするため、承認されていないユーザーはデバイスにアクセスできません。 ユーザーの情報を確実にセキュリティで保護するために、組織ではまず、企業のファイル、電子メール、またはデータにアクセスする前にユーザーに Android デバイスを暗号化するよう求める必要があります。

## <a name="common-issues"></a>一般的な問題

新しいバージョンの Android、特に v7.0 以降では、デバイスが完全に暗号化されているかどうかを確認するスタートアップ パスコードが必要です。 デバイスの製造元によって、スタートアップ パスコードに関する説明と場所は異なります。 ほとんどの場合、この機能は「安全な起動」と呼ばれています。 

## <a name="solutions"></a>ソリューション

### <a name="add-a-startup-pin"></a>スタートアップ PIN の追加

いくつかの Android デバイスでは、デバイスがセキュリティ保護されていることを確認するためにスタートアップ PIN を作成する必要があります。 異なる製造元によるさまざまな Android のバージョンが存在します。 このオプションを有効にする設定アプリで場所を見つけることにより、この問題を解決できます。 たとえば、Samsung Galaxy S7 では、**[設定]** > **[ロック画面とセキュリティ]** > **[安全な起動]** と移動して、安全なスタートアップを有効にします。  

### <a name="downgrade-your-version-of-android"></a>Android のバージョンのダウングレード
デバイスで Android 6.0 以降にダウングレードできる場合は、ダウングレードします。 デバイスのダウングレードには、データ損失のリスクがあります。 そのため、IT 管理者に問い合わせて、この問題を解決することをお勧めします。 IT 管理者の連絡先情報は、[ポータル Web サイト](http://portal.manage.microsoft.com)で入手できます。

## <a name="specific-manufacturer-issues"></a>特定の製造元の問題

バージョン 7.0 以上の一部の Android デバイスでは、特定の Android プラットフォームの標準に準拠していない方法でデータを暗号化します。 これらのデバイスは既定で暗号化されているように見えますが、Intune ではこのような方法は、デバイスに物理的にアクセスできる悪意のあるユーザーがデバイスの情報を盗み出す危険性があると認識されます。

> [!Note]
> Microsoft は製造元と協力して、テスト中に見つけた問題やユーザーから報告された問題に対処しています。 新しい情報があるときにはこの記事の内容を更新します。 

## <a name="known-devices"></a>既知のデバイス

### <a name="known-devices-that-can-be-updated-to-fix-this-issue"></a>更新によってこの問題を解決できる既知のデバイス

以下のデバイスのいずれかをお使いの場合は、デバイスを最新バージョンの Android に更新していない場合にこの問題が発生する可能性があります。 **[設定]** > **[更新]** と移動して、これらのデバイスの更新プログラムをインストールできます。 

- [Huawei Honor 8](http://consumer.huawei.com/en/support/mobile-phones/honor8_en-sup.htm)
- [Huawei P9](http://consumer.huawei.com/mobile-phones/p9/index.html)

### <a name="known-devices-that-currently-cannot-be-updated-to-fix-this-issue"></a>更新によってこの問題を解決できない既知のデバイス

- [Huawei Mate 8](http://consumer.huawei.com/en/mobile-phones/mate8/index.htm)
- [Xiaomi Mi スマートフォン](https://xiaomi-mi.com/mi-smartphones/)
