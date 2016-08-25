---
title: "Android ユーザーがアプリを入手する方法 | Microsoft Intune"
description: "エンド ユーザーが Android アプリを入手する方法"
keywords: 
author: Staciebarker
manager: angrobe
ms.date: 7/7/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f33d1684-b1b5-44f7-9aac-c6d5186a5d7c
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 300df17fd5844589a1e81552d2d590aee5615897
ms.openlocfilehash: 90f50d14fac0e335f3b7c5e0825b0bb243b7a532


---


# Android ユーザーがアプリを入手する方法
Microsoft Intune を通して配布したアプリを Android エンド ユーザーがどこでどのように取得するかについて説明します。 情報は、Samsung KNOX デバイスとネイティブの Android デバイスでは異なる場合があります。

## ネイティブの Android デバイス (Samsung KNOX 以外)

| アプリの種類 | 基幹業務 (LOB) アプリ | Play ストア アプリ  |
| ------------- |-------------| -----|
| Available apps      | ポータル サイトで **[インストール]** をタップします。 通知が表示されます。この通知をタップしてインストールを開始します。 インストールが成功すると、通知は表示されなくなります。 | ポータル サイトでアプリをタップすると、Play ストアでアプリのページが表示され、インストールを開始することができます。|
| Required apps      | アプリをインストールする必要があることを示す通知が表示されます。この通知は非表示にすることはできません。 通知をタップしてインストールを開始します。 インストールが成功すると、通知は表示されなくなります。    | アプリをインストールする必要があることを示す通知が表示されます。この通知は非表示にすることはできません。 通知をタップすると、Play ストアのアプリのページが表示され、インストールを開始することができます。 インストールが成功すると、通知は表示されなくなります。 |

## Samsung KNOX Android デバイス

| アプリの種類 | 基幹業務 (LOB) アプリ | Play ストア アプリ  |
| ------------- |-------------| -----|
| Available apps      | ポータル サイトで **[インストール]** をタップします。 アプリがインストールされます。ユーザーによる操作は不要です。 | ポータル サイトでアプリをタップすると、Play ストアでアプリのページが表示され、インストールを開始することができます。|
| Required apps      | アプリがインストールされます。ユーザーによる操作は不要です。    | アプリをインストールする必要があることを示す通知が表示されます。この通知は非表示にすることはできません。 通知をタップすると、Play ストアのアプリのページが表示され、インストールを開始することができます。 インストールが成功すると、通知は表示されなくなります。 |

アプリは、以下に示すように管理することも管理外にすることも可能です。 アプリを管理するプロセスは、すべての種類の Android デバイスで共通です。

**管理されているアプリ** - ポリシーによって管理できる、Intune によって "ラップされた" アプリまたは Intune モバイル アプリケーション管理 (MAM) ソフトウェア開発キット (SDK) で構築されたアプリです。 これらのアプリは Intune によって管理することができます。また、これらのアプリにはアプリケーション ポリシーを適用することができます。

**管理されていないアプリ** - ポリシーによって管理でき、Intune によってラップされていないアプリまたは Intune MAM SDK を組み込んでいないアプリです。 これらのアプリにアプリケーション ポリシーを適用することはできません。

### 関連項目
[Microsoft Intune でアプリを追加する](/intune/deploy-use/add-apps)
[iOS ユーザーがアプリを入手する方法](how-your-ios-users-get-their-apps.md)
[Windows ユーザーがアプリを入手する方法](how-your-windows-users-get-their-apps.md)



<!--HONumber=Jul16_HO4-->


