---
title: "iOS ユーザーがアプリを入手する方法"
description: "エンド ユーザーが iOS アプリを使用できるようにするための方法"
keywords: 
author: barlanmsft
ms.author: barlan
manager: dougeby
ms.date: 10/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7e3135c1-df26-48c9-aa4c-cdab6168897a
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 31bb6cf7d118e121a5a8d8a74f92c2b3cf5da7bc
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="how-your-ios-users-get-their-apps"></a>iOS ユーザーがアプリを入手する方法

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

Microsoft Intune を通して配布したアプリをエンド ユーザーがどこでどのように取得するかについて説明します。

**必要なアプリ** - 管理者が必須に設定しているアプリと、必要最小限のユーザー操作でデバイスにインストールされるアプリです (プラットフォームによって異なります)。

**使用可能なアプリ** - ポータル サイト アプリの一覧に表示されるアプリおよびユーザーが必要に応じてインストールするアプリです。

**管理対象のアプリ** -- ポリシーによって管理できて、Intune によって "ラップされた" アプリまたは Intune アプリ ソフトウェア開発キット (SDK) で構築されたアプリです。 これらのアプリは Intune によって管理することができます。また、これらのアプリにはアプリ保護ポリシーを適用することができます。

**管理対象外のアプリ** -- ポリシーによって管理でき、Intune によってラップされていないアプリまたは Intune アプリ SDK を組み込んでいないアプリです。 これらのアプリにアプリケーション ポリシーを適用することはできません。

Apple の制限により、基幹業務アプリおよび管理対象アプリ ストアのアプリはポータル サイト アプリに表示されません。 この問題を回避するため、iOS 用ポータル サイト アプリのアプリ タイルでは、次のように、ユーザーは単一の場所 (ポータル サイト Web サイト) のさまざまなビューですべてのアプリを確認できます。

登録済みユーザーは、ポータル サイト アプリのアプリ画面で、以下のタイルをタップしてアプリを取得します。

- **[すべてのアプリ]**。[ポータル Web サイト](https://portal.manage.microsoft.com)の [すべて] タブのすべてのアプリのリストをポイントします。

- **[おすすめアプリ]**。ポータル Web サイトの [おすすめ] タブを表示します。

- **[カテゴリ]**。ポータル Web サイトの [カテゴリ] タブをポイントします。


![iOS ポータル サイト アプリの画面](./media/ios-cp-app-main-apps-screen.png)

アプリを追加し、これらのタイルに配置する方法については、「[Intune に登録されたデバイスのアプリを追加する](/intune-classic/deploy-use/add-apps-for-mobile-devices-in-microsoft-intune.md)」を参照してください。

### <a name="see-also"></a>関連項目
[Android ユーザーがアプリを入手する方法](end-user-apps-android.md)

[Windows ユーザーがアプリを入手する方法](end-user-apps-windows.md)
