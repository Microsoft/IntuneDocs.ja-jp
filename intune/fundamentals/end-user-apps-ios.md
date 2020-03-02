---
title: iOS/iPadOS のユーザーがアプリを入手する方法
description: エンド ユーザーが iOS/iPadOS アプリを使用できるようにするための方法
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 05/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 7e3135c1-df26-48c9-aa4c-cdab6168897a
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 344c2e3f3ed53852aa6b749c9ebf6d451dd313ff
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514389"
---
# <a name="how-your-iosipados-users-get-their-apps"></a>iOS/iPadOS のユーザーがアプリを入手する方法

Microsoft Intune を通して配布したアプリをエンド ユーザーがどこでどのように取得するかについて説明します。

**必要なアプリ** - 管理者が必須に設定しているアプリと、必要最小限のユーザー操作でデバイスにインストールされるアプリです (プラットフォームによって異なります)。

**使用可能なアプリ** - ポータル サイト アプリの一覧に表示されるアプリおよびユーザーが必要に応じてインストールするアプリです。

**管理対象のアプリ** -- ポリシーによって管理できて、Intune によって "ラップされた" アプリまたは Intune アプリ ソフトウェア開発キット (SDK) で構築されたアプリです。 これらのアプリは Intune によって管理することができます。また、これらのアプリにはアプリ保護ポリシーを適用することができます。

**アンマネージド アプリ** -- Intune アプリ SDK と統合されていない iOS/iPadOS の App Store からユーザーがダウンロードできるアプリです。 Intune では、これらのアプリの配布、管理、または選択的ワイプを制御することはできません。  

Apple の制限により、基幹業務アプリおよび管理対象アプリ ストアのアプリはポータル サイト アプリに表示されません。 この問題を回避するため、iOS/iPadOS 用ポータル サイト アプリのタイルでは、ユーザーに単一の場所 (ポータル サイト Web サイト) ですべてのアプリに対するさまざまなビューが表示されます。

登録済みユーザーは、ポータル サイト アプリのアプリ画面で、以下のタイルをタップしてアプリを取得します。

- **[すべてのアプリ]** 。[ポータル Web サイト](https://portal.manage.microsoft.com)の [すべて] タブのすべてのアプリのリストをポイントします。

- **[おすすめアプリ]** 。ポータル Web サイトの [おすすめ] タブを表示します。

- **[カテゴリ]** 。ポータル Web サイトの [カテゴリ] タブをポイントします。

![iOS ポータル サイト アプリの画面](./media/end-user-apps-ios/ios-cp-app-main-apps-screen.png)

アプリを追加する方法の詳細については、「[アプリを Microsoft Intune に追加する方法](../apps/apps-add.md)」を参照してください。

## <a name="see-also"></a>関連項目

[Android ユーザーがアプリを入手する方法](end-user-apps-android.md)

[Windows ユーザーがアプリを入手する方法](end-user-apps-windows.md)
