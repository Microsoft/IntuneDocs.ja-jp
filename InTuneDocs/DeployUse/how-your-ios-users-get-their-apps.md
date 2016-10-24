---
title: "iOS ユーザーがアプリを入手する方法 | Microsoft Intune"
description: "エンド ユーザーが iOS アプリを使用できるようにするための方法"
keywords: 
author: Staciebarker
ms.author: stabar
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
ms.sourcegitcommit: 37841027c7ae040163440a19f9e163fb4eb87233
ms.openlocfilehash: ad780fb3403f6caaee1218d785a5cad326c18df5


---


# iOS ユーザーがアプリを入手する方法

Microsoft Intune を通して配布したアプリをエンド ユーザーがどこでどのように取得するかについて説明します。

**必要なアプリ** - 管理者が必須に設定しているアプリと、必要最小限のユーザー操作でデバイスにインストールされるアプリです (プラットフォームによって異なります)。

**使用可能なアプリ** - ポータル サイト アプリの一覧に表示されるアプリおよびユーザーが必要に応じてインストールするアプリです。

**管理対象のアプリ** - ポリシーによって管理できる、Intune によって "ラップされた" アプリまたは Intune モバイル アプリケーション管理 (MAM) ソフトウェア開発キット (SDK) で構築されたアプリです。 これらのアプリは Intune によって管理することができます。また、これらのアプリにはアプリケーション ポリシーを適用することができます。

**管理対象外のアプリ** - ポリシーによって管理でき、Intune によってラップされていないアプリまたは Intune MAM SDK を組み込んでいないアプリです。 これらのアプリにアプリケーション ポリシーを適用することはできません。

Apple の制限により、基幹業務アプリおよび管理対象アプリ ストアのアプリはポータル サイト アプリに表示されません。 この問題を回避するため、iOS 用ポータル サイト アプリのアプリ タイルでは、次のように、ユーザーは単一の場所 (ポータル サイト Web サイト) のさまざまなビューですべてのアプリを確認できます。

- これまで **[会社のアプリ]** は[ポータル サイト Web サイト](http://portal.manage.microsoft.com)の [すべて] タブにあるすべてのアプリの一覧と関連付けられており、今後も機能は同じです。 このタイル名は **[すべてのアプリ]** に変更されました。

- **[その他のアプリ]** はこれまで、Apple がポータル サイト アプリに表示を許可しているすべてのアプリを一覧表示する、ポータル サイト アプリ内のビューに関連付けられていました。 このタイル名は **[おすすめアプリ]** に変更され、ユーザーがこのタイルをタップするとポータル サイト Web サイトの [おすすめ] タブが表示されるようになりました。

-  **[カテゴリ]** はこれまで、アプリのカテゴリを一覧表示する、ポータル サイト アプリ内のビューに関連付けられていました。 このタイル名は変更されませんが、ポータル サイト Web サイトの [カテゴリ] タブに関連付けられるようになりました。
最新のスクリーンショットについては、「[Improvements in how iOS end users get their apps](https://gallery.technet.microsoft.com/Improvements-in-how-iOS-d1104186)」(iOS エンドユーザーのアプリ取得方法の改善) を参照してください。



### 関連項目
[Android ユーザーがアプリを入手する方法](how-your-android-users-get-their-apps.md)

[Windows ユーザーがアプリを入手する方法](how-your-windows-users-get-their-apps.md)



<!--HONumber=Oct16_HO2-->


