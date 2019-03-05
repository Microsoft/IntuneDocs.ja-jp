---
title: iOS ユーザーがアプリを入手する方法
description: エンド ユーザーが iOS アプリを使用できるようにするための方法
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/28/2016
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 7e3135c1-df26-48c9-aa4c-cdab6168897a
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1928af6db94993cd385faa01473cacc6cab7fd2b
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/02/2019
ms.locfileid: "57236706"
---
# <a name="how-your-ios-users-get-their-apps"></a>iOS ユーザーがアプリを入手する方法

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

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

アプリを追加する方法の詳細については、「[アプリを Microsoft Intune に追加する方法](apps-add.md)」を参照してください。

### <a name="see-also"></a>関連項目
[Android ユーザーがアプリを入手する方法](end-user-apps-android.md)

[Windows ユーザーがアプリを入手する方法](end-user-apps-windows.md)
