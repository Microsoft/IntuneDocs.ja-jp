---
title: Android ユーザーがアプリを入手する方法
description: エンド ユーザーが Android アプリを入手する方法
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/21/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f33d1684-b1b5-44f7-9aac-c6d5186a5d7c
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 878e4d0854722d82eab0545cf3a1ba743f2c52db
ms.sourcegitcommit: 2198a39ae48beca5fc74316976bc3fc9db363659
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38224722"
---
# <a name="how-your-android-users-get-their-apps"></a>Android ユーザーがアプリを入手する方法

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Microsoft Intune を通して配布したアプリを Android エンド ユーザーがどこでどのように取得するかについて説明します。 この情報はデバイスの種類 (Android ネイティブ デバイスや Samsung Knox Standard デバイス) によって異なる可能性があります。

## <a name="native-non-samsung-knox-standard-android-devices"></a>ネイティブ (Samsung KNOX Standard 以外) Android デバイス

| アプリの種類 | 基幹業務 (LOB) アプリ | Play ストア アプリ  |
| ------------- |-------------| -----|
| Available apps      | ポータル サイトで **[インストール]** をタップします。 通知が表示されます。この通知をタップしてインストールを開始します。 インストールが成功すると、通知は表示されなくなります。 | ポータル サイトでアプリをタップすると、Play ストアでアプリのページが表示され、インストールを開始することができます。|
| Required apps      | アプリをインストールする必要があることを示す通知が表示されます。この通知は非表示にすることはできません。 通知をタップしてインストールを開始します。 インストールが成功すると、通知は表示されなくなります。    | アプリをインストールする必要があることを示す通知が表示されます。この通知は非表示にすることはできません。 通知をタップすると、Play ストアのアプリのページが表示され、インストールを開始することができます。 インストールが成功すると、通知は表示されなくなります。 |

[LOB アプリ](lob-apps-android.md)をインストールするには、エンド ユーザーは、不明なソースからのインストールを許可する必要があります。 通常、設定には 2 つの場所があります。

* **Android 7.1.2 以前**: **[設定]** > **[セキュリティ]** > **[不明なソース]**
* **Android 8.0 以降**: **[設定]** > **[Apps & notifications]\(アプリと通知\)** > **[Special app access]\(特別なアプリ アクセス\)** > **[Install unknown apps]\(不明なアプリのインストール\)** > **[ポータル サイト]** > **[Allow from this source]\(このソースからは許可する\)**

許可が必要になった場合、ポータル サイト アプリがエンド ユーザーに通知し、該当する設定画面まで直接誘導します。 


## <a name="samsung-knox-standard-android-devices"></a>Samsung KNOX Standard Android デバイス

| アプリの種類 | 基幹業務 (LOB) アプリ | Play ストア アプリ  |
| ------------- |-------------| -----|
| Available apps      | ポータル サイトで **[インストール]** をタップします。 アプリがインストールされます。ユーザーによる操作は不要です。 | ポータル サイトでアプリをタップすると、Play ストアでアプリのページが表示され、インストールを開始することができます。|
| Required apps      | アプリがインストールされます。ユーザーによる操作は不要です。    | アプリをインストールする必要があることを示す通知が表示されます。この通知は非表示にすることはできません。 通知をタップすると、Play ストアのアプリのページが表示され、インストールを開始することができます。 インストールが成功すると、通知は表示されなくなります。 |

アプリは、以下に示すように管理することも管理外にすることも可能です。 アプリを管理するプロセスは、すべての種類の Android デバイスで共通です。


  **管理対象のアプリ** - ポリシーで管理できるアプリです。 Intune で "ラップ" されているか、Intune App SDK で構築されています。 These apps can be managed by Intune, and application policies can be applied to them.


  **管理対象外のアプリ** - ポリシーで管理できないアプリです。 Intune によってラップされていないか、Intune アプリ SDK を組み込んでいません。 これらのアプリにアプリケーション ポリシーを適用することはできません。

### <a name="see-also"></a>関連項目
[Microsoft Intune でアプリを追加する](apps-add.md)

[iOS ユーザーがアプリを入手する方法](end-user-apps-ios.md)

[Windows ユーザーがアプリを入手する方法](end-user-apps-windows.md)
