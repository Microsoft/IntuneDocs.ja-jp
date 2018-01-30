---
title: "アプリの概要"
titlesuffix: Azure portal
description: "社員が仕事を行えるように、アプリを見つけ、デバイスに追加します。"
keywords: 
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 12/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1542fc3-672e-47c1-a21f-82826a2f8ac4
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c1838f1d856efdebb7e2114cb61dd8d88ca100f7
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
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
4. **[追加]** を選択し、**[アプリの種類]** として **[ストア アプリ]** の **[iOS]** を選びます。
5. **[アプリの選択]** を選んで、**[アプリ ストアを検索します]** ブレードを表示します。
6. テキスト ボックスで、デバイスに割り当てるアプリを検索します。 アプリを選び、**[選択]** をクリックします。
7. **[アプリの追加]** ブレードで、**[アプリ情報]** を選択し、すべてのアプリ情報に入力されていることを確認します。 このアプリの整理に役立つように他の任意詳細を追加できます。**所有者**、**メモ**、**開発者**、会社のプライバシー ポリシーの**プライバシー URL** などです。
8. **[会社のポータルでおすすめアプリとして表示します]** に **[はい]** が選ばれていることを確認し、**[OK]** を選びます。
9. **[アプリの追加]** ブレードで **[追加]** を選んで、アプリを追加します。 そのアプリの **[概要]** が表示されます。 **[割り当て]** を選択し、**[グループの選択]** をクリックしてそれをテスト グループに割り当てます。 そのアプリをダウンロード**可能**にします。 これでテスト デバイスにそのアプリが**おすすめアプリ**として表示されます。

## <a name="learn-more"></a>詳細情報

* [Intune によるアプリ管理とは](app-management.md)
* [アプリのライフサイクルの概要](app-lifecycle.md)
* [アプリ保護ポリシーとは](app-protection-policy.md)
