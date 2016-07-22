---
title: "Android ユーザーがアプリを入手する方法 | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f33d1684-b1b5-44f7-9aac-c6d5186a5d7c
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d3bcf89636f9da8fd8bfa5cc52391742a9ce9f92
ms.openlocfilehash: 25571ce1b214c927f3dc2ea3968d00970621e474


---


# Android ユーザーがアプリを入手する方法
Microsoft Intune を通して配布したアプリをエンド ユーザーがどこでどのように取得するかについて説明します。 

**必要なアプリ** - 管理者によって必要とされるアプリおよび必要最小限のユーザー操作でデバイスにインストールされるアプリです (プラットフォームによって異なる)。
 
- **Samsung Knox デバイス**: 必要なアプリを Samsung Knox デバイスに展開する場合、デバイスに自動的にサイレント インストールされます。
- **ネイティブ (Samsung Knox ではないデバイス)**: 必要なアプリを Samsung Knox ではないデバイスに展開する場合、ユーザーのデバイスに自動インストールされることはありません。 代わりに、ユーザーはアプリをインストールするように求められます。 プロンプトを承認すると、アプリがダウンロードされます。インストールする必要があることを伝える通知がユーザーに届きます。 

**使用可能なアプリ** - ポータル サイト アプリの一覧に表示されるアプリおよびユーザーが必要に応じてインストールするアプリです。

**管理されているアプリ** - ポリシーによって管理できる、Intune によって "ラップされた" アプリまたは Intune モバイル アプリケーション管理 (MAM) ソフトウェア開発キット (SDK) で構築されたアプリです。 これらのアプリは Intune によって管理することができます。また、これらのアプリにはアプリケーション ポリシーを適用することができます。

**管理されていないアプリ** - ポリシーによって管理でき、Intune によってラップされていないアプリまたは Intune MAM SDK を組み込んでいないアプリです。 これらのアプリにアプリケーション ポリシーを適用することはできません。

###関連項目
[Microsoft Intune でアプリを追加する](/intune/deploy-use/add-apps)
[iOS ユーザーがアプリを入手する方法](how-your-ios-users-get-their-apps.md)
[Windows ユーザーがアプリを入手する方法](how-your-windows-users-get-their-apps.md)


<!--HONumber=Jul16_HO1-->


