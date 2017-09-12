---
title: "アプリの概要"
titlesuffix: Azure portal
description: "社員が仕事を行えるように、アプリを見つけ、デバイスに追加します。"
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 08/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1542fc3-672e-47c1-a21f-82826a2f8ac4
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 28bc8547d56073a2175ca57e03dbd9b94fc03ba9
ms.sourcegitcommit: fa6aaf12611c3e03e38e467806fc30b1d0255e88
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2017
---
# <a name="get-started-with-adding-apps"></a>アプリ追加の概要

Intune では、いくつかの方法で企業デバイスにアプリを展開できます。

* **ソフトウェア インストーラー**: ユーザーのデバイスにダウンロードされたファイルをアップロードします
* __外部リンク__: パブリック アプリ ストアのアプリや Web アプリを持っている場合
* **管理対象アプリ**: アプリ ストアで入手できるアプリに適用される付加的なモバイル アプリ管理を必要とする iOS デバイスの場合

パブリック ストア アプリを割り当てることで、迅速なアプリケーション展開方法の 1 つを行います。

## <a name="how-do-i-assign-a-public-store-app"></a>パブリック ストア アプリを割り当てる場合の操作方法

1. [Azure ポータル](https://portal.azure.com)にサインインします。
2. **[リソースの検索]** を利用し、**[Intune]** を探します。
3. **[モバイル アプリ]** を選択し、**[アプリ]** を選択します。
4. **[追加]** を選択し、**[アプリの種類]** として **[iOS ストア アプリ]** を選択します。
5. テキスト ボックスで、デバイスに割り当てるアプリを検索します。 アプリを選択し、**[OK]** を選択します。
6. **[アプリの追加]** ブレードで、**[アプリ情報]** を選択し、すべてのアプリ情報に入力されていることを確認します。 このアプリの整理に役立つように他の任意詳細を追加できます。**所有者**、**メモ**、**開発者**、会社のプライバシー ポリシーの**プライバシー URL** などです。
7. [会社のポータルでおすすめアプリとして表示します] に [はい] が選択されていることを確認し、[OK] を選択します。
8. **[追加]** を選択してアプリを追加します。 そのアプリの **[概要]** が表示されます。 **[割り当て]** を選択し、**[グループの選択]** をクリックしてそれをテスト グループに割り当てます。 そのアプリをダウンロード**可能**にします。 これでテスト デバイスにそのアプリが**おすすめアプリ**として表示されます。

## <a name="learn-more"></a>詳細情報

* [Intune によるアプリ管理とは](app-management.md)
* [アプリのライフサイクルの概要](app-lifecycle.md)
* [アプリ保護ポリシーとは](app-protection-policy.md)
