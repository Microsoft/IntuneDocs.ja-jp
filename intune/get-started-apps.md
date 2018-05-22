---
title: Microsoft Intune のアプリの概要
titlesuffix: ''
description: 従業員が仕事を行えるように、アプリを見つけ、デバイスに追加します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a1542fc3-672e-47c1-a21f-82826a2f8ac4
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5d99812c57596e10d0cdfa2c0f4504f8a6ac583c
ms.sourcegitcommit: 34e96e57af6b861ecdfea085acf3c44cff1f3d43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
---
# <a name="get-started-with-adding-apps-in-microsoft-intune"></a>Microsoft Intune でのアプリ追加の概要

アプリの割り当て、監視、構成、または保護を行うには、対象のアプリを事前に Intune に追加しておく必要があります。 Intune では、異なるいくつかのアプリの種類がサポートされます。 また、使用可能なオプションはアプリの種類ごとに異なります。

Intune では、以下の種類のアプリを追加して、会社のデバイスに割り当てることができます。
- **ストアからのアプリ** - アプリ ストアで入手できるアプリに適用される付加的なモバイル アプリ管理を必要とするデバイスの場合。
- **社内で作成された (基幹業務) アプリ** - ユーザーのデバイスにダウンロードされたファイルをアップロードします。
- **組み込まれているアプリ** - Office 365 アプリなどの精選された管理対象アプリを iOS デバイスと Android デバイスに簡単に割り当てます。
- **Web 上のアプリ** - Intune によって、デバイスのホーム画面上の Web アプリへのショートカットが作成されます。

## <a name="how-do-i-assign-a-public-store-app"></a>パブリック ストア アプリを割り当てる場合の操作方法

1. [Azure ポータル](https://portal.azure.com) にサインインします。
2. **すべてのサービス** > **Intune** の順に選択します。 Intune は **[監視 + 管理]** セクションにあります。
3. **[モバイル アプリ]** を選択し、**[アプリ]** を選択します。
4. **[追加]** を選択し、**[アプリの種類]** として **[iOS]** を選びます。
5. **[アプリの選択]** を選んで、**[アプリ ストアを検索します]** ウィンドウを表示します。
6. テキスト ボックスで、デバイスに割り当てるアプリを検索します。 アプリを選び、**[選択]** をクリックします。
7. **[アプリの追加]** ウィンドウで、**[アプリ情報]** を選択し、すべてのアプリ情報に入力されていることを確認します。 このアプリの整理に役立つように他の任意詳細を追加できます。**所有者**、**メモ**、**開発者**、会社のプライバシー ポリシーの**プライバシー URL** などです。
8. **[会社のポータルでおすすめアプリとして表示します]** に **[はい]** が選ばれていることを確認し、**[OK]** を選びます。
9. **[アプリの追加]** ウィンドウで **[追加]** を選んで、アプリを追加します。 この操作により、そのアプリの **[概要]** が表示されます。 **[割り当て]** を選択し、**[グループの追加]** をクリックしてそれをテスト グループに割り当てます。 そのアプリをダウンロード**可能**にします。 これでテスト デバイスにそのアプリが**おすすめアプリ**として表示されます。


- [アプリをグループに割り当てる方法](apps-deploy.md)

## <a name="learn-more"></a>詳細情報

* [Intune によるアプリ管理とは](app-management.md)
* [アプリのライフサイクルの概要](app-lifecycle.md)
* [アプリ保護ポリシーとは](app-protection-policy.md)
