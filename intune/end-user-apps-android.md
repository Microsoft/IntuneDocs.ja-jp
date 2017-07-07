---
title: "Android ユーザーがアプリを入手する方法"
description: "エンド ユーザーが Android アプリを入手する方法"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f33d1684-b1b5-44f7-9aac-c6d5186a5d7c
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 4f0364750edf2e97e2b621c27fb25bea8e0f537c
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2017
---
# <a name="how-your-android-users-get-their-apps"></a>Android ユーザーがアプリを入手する方法

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

Microsoft Intune を通して配布したアプリを Android エンド ユーザーがどこでどのように取得するかについて説明します。 この情報はデバイスの種類 (Android ネイティブ デバイスや Samsung Knox Standard デバイス) によって異なる可能性があります。

## <a name="native-non-samsung-knox-standard-android-devices"></a>ネイティブ (Samsung KNOX Standard 以外) Android デバイス

| アプリの種類 | 基幹業務 (LOB) アプリ | Play ストア アプリ  |
| ------------- |-------------| -----|
| Available apps      | ポータル サイトで **[インストール]** をタップします。 通知が表示されます。この通知をタップしてインストールを開始します。 インストールが成功すると、通知は表示されなくなります。 | ポータル サイトでアプリをタップすると、Play ストアでアプリのページが表示され、インストールを開始することができます。|
| Required apps      | アプリをインストールする必要があることを示す通知が表示されます。この通知は非表示にすることはできません。 通知をタップしてインストールを開始します。 インストールが成功すると、通知は表示されなくなります。    | アプリをインストールする必要があることを示す通知が表示されます。この通知は非表示にすることはできません。 通知をタップすると、Play ストアのアプリのページが表示され、インストールを開始することができます。 インストールが成功すると、通知は表示されなくなります。 |

## <a name="samsung-knox-standard-android-devices"></a>Samsung KNOX Standard Android デバイス

| アプリの種類 | 基幹業務 (LOB) アプリ | Play ストア アプリ  |
| ------------- |-------------| -----|
| Available apps      | ポータル サイトで **[インストール]** をタップします。 アプリがインストールされます。ユーザーによる操作は不要です。 | ポータル サイトでアプリをタップすると、Play ストアでアプリのページが表示され、インストールを開始することができます。|
| Required apps      | アプリがインストールされます。ユーザーによる操作は不要です。    | アプリをインストールする必要があることを示す通知が表示されます。この通知は非表示にすることはできません。 通知をタップすると、Play ストアのアプリのページが表示され、インストールを開始することができます。 インストールが成功すると、通知は表示されなくなります。 |

アプリは、以下に示すように管理することも管理外にすることも可能です。 アプリを管理するプロセスは、すべての種類の Android デバイスで共通です。

**管理対象のアプリ** - ポリシーで管理できるアプリです。 Intune によって "ラップ" されているか、Intune モバイル アプリケーション管理 (MAM) ソフトウェア開発キット (SDK) で構築されています。 これらのアプリは Intune によって管理することができます。また、これらのアプリにはアプリケーション ポリシーを適用することができます。

**管理対象外のアプリ** - ポリシーで管理できないアプリです。 Intune によってラップされていないか、Intune MAM SDK を組み込んでいません。 これらのアプリにアプリケーション ポリシーを適用することはできません。

### <a name="see-also"></a>関連項目
[Microsoft Intune でアプリを追加する](apps-add.md)

[iOS ユーザーがアプリを入手する方法](end-user-apps-ios.md)

[Windows ユーザーがアプリを入手する方法](end-user-apps-windows.md)
