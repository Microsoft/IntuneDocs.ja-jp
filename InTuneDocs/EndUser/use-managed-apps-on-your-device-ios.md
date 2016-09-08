---
title: "iOS デバイスで管理対象アプリを使用する | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3232c5c1-cb9f-45ca-806f-7e74eeb3533e
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: maxles
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 38301b4e6964550008b08e99bf7016f1cc2561c3
ms.openlocfilehash: 178d46860774d2595f06316f84fd1940c12c025f


---


# iOS デバイスで管理対象アプリを使用する

管理対象アプリとは、そのアプリでアクセス可能な会社のデータを保護できるよう IT 管理者が構成可能なアプリです。 管理対象アプリ内の会社のデータに iOS デバイスでアクセスする場合、アプリの動作が予期したものとは少し異なる場合があります。 たとえば、保護された会社のデータをコピーして貼り付けできない、またはそのデータを特定の場所に保存できない場合があります。

また、異なる管理対象アプリがデバイス上で連携して動作し、会社のデータを保護しながら、日常のタスクを実行することもできます。 たとえば、1 つの管理対象アプリで会社のファイルを開き、別の管理対象アプリでそのファイルを表示する必要がある場合、ファイルを表示できるようにする管理対象アプリが自動的に開きます。 必要なアプリが使用できない場合、管理されているドキュメント内からドキュメントを開くまたは Web リンクにアクセスするなどの特定の操作が行えない可能性があります。

管理対象アプリで会社のデータにアクセスすると、開こうとしているアプリが管理されていることを通知する以下のようなメッセージが表示されます。

![managed-apps-message-ios](./media/managed-apps-message.png)

### 管理対象アプリを取得する方法
管理対象アプリはいくつかの方法で取得できます。

-   デバイスが Microsoft Intune に登録されるときに、会社のポータル アプリまたは会社のポータル Web サイトからアプリをインストールするか、または IT 管理者がアプリをデバイスにインストールする場合があります。 登録については、「[Intune に iOS デバイスを登録する](enroll-your-device-in-intune-ios.md)」または「[Intune に Mac OS X デバイスを登録する](enroll-your-device-in-intune-mac-os-x.md)」を参照してください。

-   アプリ ストアからアプリをインストールし、Intune で管理されている会社のユーザー アカウントでサインインします。

### IT 管理者がアプリで管理できるもの
以下は、IT 管理者がアプリで管理でき、デバイス上での会社データとのやり取りに影響するオプションの例です。

-   特定の web サイトへのアクセス

-   アプリケーション間のデータ転送

-   ファイルの保存

-   コピーと貼り付けの操作

-   暗証番号 (pin) のアクセスの要件

-   会社の資格情報を使用したログイン

-   クラウドへのバックアップ機能

-   スクリーン ショットを撮る機能

-   データの暗号化の要件


デバイスの管理対象アプリの詳細については、IT 管理者にお問い合わせください。 連絡先情報については、[ポータル サイト Web サイト](http://portal.manage.microsoft.com)をご確認ください。





<!--HONumber=Aug16_HO5-->


