---
title: "Windows ユーザーがアプリを入手する方法"
description: "ユーザーが Windows アプリを使用できるようにするための方法"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 12/05/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e471fed8-19f0-4b37-aaa2-65f28a6b4794
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 3f49003e927acb14982de0210c8e5a5291c334aa
ms.sourcegitcommit: d44c32aad3e84f6c0b296bdb010981d3a818befb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2018
---
# <a name="how-your-windows-users-get-their-apps"></a>Windows ユーザーがアプリを入手する方法

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

Microsoft Intune を通して配布したアプリをユーザーがどこでどのように取得するかについて説明します。

**必要なアプリ**は、管理者によって必要とされ、必要最小限のユーザー操作でデバイスにインストールされるアプリです (プラットフォームによって異なります)。

**使用可能なアプリ**は、ポータル サイト アプリの一覧に表示され、ユーザーがインストールを選択できるアプリです。

**管理対象のアプリ**は、ポリシーによって管理でき、Intune によって "ラップ" されているか、Intune アプリ ソフトウェア開発キット (SDK) で構築されています。 これらのアプリは Intune によって管理することができます。また、これらのアプリにはアプリ保護ポリシーを適用することができます。

**管理対象外のアプリ**は、ポリシーによって管理でき、Intune によってラップされていないアプリまたは Intune アプリ SDK を組み込んでいないアプリです。 アプリ保護にアプリケーション ポリシーを適用することはできません。

### <a name="see-also"></a>関連項目
[Android ユーザーがアプリを入手する方法](end-user-apps-android.md)
[iOS ユーザーがアプリを入手する方法](end-user-apps-android.md)
