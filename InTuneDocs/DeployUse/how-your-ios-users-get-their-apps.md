---
title: "iOS ユーザーがアプリを入手する方法 | Microsoft Intune"
description: "エンド ユーザーが iOS アプリを使用できるようにするための方法"
keywords: 
author: Staciebarker
manager: angrobe
ms.date: 08/24/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7e3135c1-df26-48c9-aa4c-cdab6168897a
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9f1946c02c6267a22844106e8f72555ec5e9cabb
ms.openlocfilehash: 212dcd31697180dae61569dda13b56704a079bf4


---


# iOS ユーザーがアプリを入手する方法

Microsoft Intune を通して配布したアプリをエンド ユーザーがどこでどのように取得するかについて説明します。

**必要なアプリ** - 管理者によって必要とされるアプリおよび必要最小限のユーザー操作でデバイスにインストールされるアプリです (プラットフォームによって異なる)。

**使用可能なアプリ** - ポータル サイト アプリの一覧に表示されるアプリおよびユーザーが必要に応じてインストールするアプリです。

**管理されているアプリ** - ポリシーによって管理できる、Intune によって "ラップされた" アプリまたは Intune モバイル アプリケーション管理 (MAM) ソフトウェア開発キット (SDK) で構築されたアプリです。 これらのアプリは Intune によって管理することができます。また、これらのアプリにはアプリケーション ポリシーを適用することができます。

**管理されていないアプリ** - ポリシーによって管理でき、Intune によってラップされていないアプリまたは Intune MAM SDK を組み込んでいないアプリです。 これらのアプリにアプリケーション ポリシーを適用することはできません。

Apple の制限では、基幹業務および管理対象アプリのストア アプリをポータル サイト アプリに一覧表示することが禁止されています。つまり、ユーザーが自分のすべてのアプリを見るには異なるビューを持つ必要があります。 ポータル サイト アプリのアプリ ページに表示されている各タイルのアプリは、次のようにして使用します。

- **[Company Apps (会社のアプリ)]** タイルは、[ポータル サイト Web サイト](http://portal.manage.microsoft.com)の **[すべて]** タブのすべてのアプリの一覧に関連付られています。

- **[その他のアプリ]** タイルは、現在、Apple がポータル サイト アプリに表示を許可しているすべてのアプリを一覧表示する、ポータル サイト アプリ内のビューに関連付られています。 これには、基幹業務および管理対象アプリのストア アプリを除くすべてのアプリが含まれます。

- **[カテゴリ]** タイルは、現在、アプリのカテゴリを一覧表示する、ポータル サイト アプリ内のビューに関連付られています。

    ![ios-how-to-sync-device-with-intune](./media/ios-sync-comp-portal-apps.png)


###関連項目
[Android ユーザーがアプリを入手する方法](how-your-android-users-get-their-apps.md)</br>
[Windows ユーザーがアプリを入手する方法](how-your-windows-users-get-their-apps.md)



<!--HONumber=Aug16_HO4-->


