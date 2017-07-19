---
title: "アプリの概要"
titleSuffix: Intune on Azure
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 06/27/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1542fc3-672e-47c1-a21f-82826a2f8ac4
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a086da185681a91daad214f1be2d4ff0e2827fbb
ms.sourcegitcommit: fd2e8f6f8761fdd65b49f6e4223c2d4a013dd6d9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2017
---
# <a name="getting-started-with-apps"></a>アプリの概要

![Microsoft Word アプリの追加の画像。](/intune/media/generic-add-apps.png)

正しいアプリが搭載されていなければ、仕事のデバイスは役に立ちません。 Intune では、いくつかの方法で企業デバイスにアプリを展開できます。

* **ソフトウェア インストーラー**: ユーザーのデバイスにダウンロードされたファイルをアップロードします
* __外部リンク__: パブリック アプリ ストアのアプリや Web アプリを持っている場合
* **管理対象アプリ**: アプリ ストアで入手できるアプリに適用される付加的なモバイル アプリ管理を必要とする iOS デバイスの場合

パブリック ストア アプリを割り当てることで、迅速なアプリケーション展開方法の 1 つを行います。

__パブリック ストア アプリを割り当てる方法__

1. [Azure ポータル](https://portal.azure.com)にサインインします。
2. **[リソースの検索]** を利用し、**[Intune]** を探します。
3. **[モバイル アプリ]** を選択し、**[アプリ]** を選択します。
4. **[追加]** を選択し、**[アプリの種類]** として **[iOS ストア アプリ]** を選択します。
5. テキスト ボックスで、デバイスに割り当てるアプリを検索します。 アプリを選択し、**[OK]** を選択します。
6. **[アプリの追加]** ブレードで、**[アプリ情報]** を選択し、すべてのアプリ情報に入力されていることを確認します。 このアプリの整理に役立つように他の任意詳細を追加できます。**所有者**、**メモ**、**開発者**、会社のプライバシー ポリシーの**プライバシー URL** などです。
7. [会社のポータルでおすすめアプリとして表示します] に [はい] が選択されていることを確認し、[OK] を選択します。
8. **[追加]** を選択してアプリを追加します。 そのアプリの **[概要]** が表示されます。 **[割り当て]** を選択し、**[グループの選択]** をクリックしてそれをテスト グループに割り当てます。 そのアプリをダウンロード**可能**にします。 これでテスト デバイスにそのアプリが**おすすめアプリ**として表示されます。
