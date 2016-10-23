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
ms.sourcegitcommit: 627914b2ac877c1b5ff5bc95f7f2098ab8988250
ms.openlocfilehash: 98e712fb852c89c1d092b87482f30ada33010a33


---


# Android ユーザーがアプリを入手する方法
Microsoft Intune を通して配布したアプリを Android エンド ユーザーがどこでどのように取得するかについて説明します。 この情報はデバイスの種類 (Android ネイティブ デバイスや Samsung Knox デバイス) によって異なる可能性があります。

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

**管理対象のアプリ** - ポリシーで管理できるアプリです。 Intune によって "ラップ" されているか、Intune モバイル アプリケーション管理 (MAM) ソフトウェア開発キット (SDK) で構築されています。 これらのアプリは Intune によって管理することができます。また、これらのアプリにはアプリケーション ポリシーを適用することができます。

**管理対象外のアプリ** - ポリシーで管理できないアプリです。 Intune によってラップされていないか、Intune MAM SDK を組み込んでいません。 これらのアプリにアプリケーション ポリシーを適用することはできません。

### 関連項目
[Microsoft Intune でアプリを追加する](/intune/deploy-use/add-apps)

[iOS ユーザーがアプリを入手する方法](how-your-ios-users-get-their-apps.md)

[Windows ユーザーがアプリを入手する方法](how-your-windows-users-get-their-apps.md)



<!--HONumber=Oct16_HO2-->


