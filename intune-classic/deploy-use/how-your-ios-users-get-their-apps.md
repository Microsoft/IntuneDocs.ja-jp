---
title: "iOS ユーザーがアプリを入手する方法 | Microsoft Docs"
description: "エンド ユーザーが iOS アプリを使用できるようにするための方法"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 10/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7e3135c1-df26-48c9-aa4c-cdab6168897a
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 044723afa95fe1b739570239c81311804617199b
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017


---


# <a name="how-your-ios-users-get-their-apps"></a>iOS ユーザーがアプリを入手する方法

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune を通して配布したアプリをエンド ユーザーがどこでどのように取得するかについて説明します。

**必要なアプリ** - 管理者が必須に設定しているアプリと、必要最小限のユーザー操作でデバイスにインストールされるアプリです (プラットフォームによって異なります)。

**使用可能なアプリ** - ポータル サイト アプリの一覧に表示されるアプリおよびユーザーが必要に応じてインストールするアプリです。

**管理対象のアプリ** - ポリシーによって管理できる、Intune によって "ラップされた" アプリまたは Intune モバイル アプリケーション管理 (MAM) ソフトウェア開発キット (SDK) で構築されたアプリです。 これらのアプリは Intune によって管理することができます。また、これらのアプリにはアプリケーション ポリシーを適用することができます。

**管理対象外のアプリ** - ポリシーによって管理でき、Intune によってラップされていないアプリまたは Intune MAM SDK を組み込んでいないアプリです。 これらのアプリにアプリケーション ポリシーを適用することはできません。

Apple の制限により、基幹業務アプリおよび管理対象アプリ ストアのアプリはポータル サイト アプリに表示されません。 この問題を回避するため、iOS 用ポータル サイト アプリのアプリ タイルでは、次のように、ユーザーは単一の場所 (ポータル サイト Web サイト) のさまざまなビューですべてのアプリを確認できます。

登録済みユーザーは、ポータル サイト アプリのアプリ画面で、以下のタイルをタップしてアプリを取得します。

- **[すべてのアプリ]**。[ポータル Web サイト](https://portal.manage.microsoft.com)の [すべて] タブのすべてのアプリのリストをポイントします。

- **[おすすめアプリ]**。ポータル Web サイトの [おすすめ] タブを表示します。

- **[カテゴリ]**。ポータル Web サイトの [カテゴリ] タブをポイントします。


![iOS ポータル サイト アプリの画面](./media/ios-cp-app-main-apps-screen.png)

アプリを追加し、これらのタイルに配置する方法については、「[Intune に登録されたデバイスのアプリを追加する](/intune-classic/deploy-use/add-apps-for-mobile-devices-in-microsoft-intune.md)」を参照してください。

### <a name="see-also"></a>関連項目
[Android ユーザーがアプリを入手する方法](how-your-android-users-get-their-apps.md)

[Windows ユーザーがアプリを入手する方法](how-your-windows-users-get-their-apps.md)

