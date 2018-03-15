---
title: "Microsoft Intune のアプリの概要"
titlesuffix: 
description: "従業員が仕事を行えるように、アプリを見つけ、デバイスに追加します。"
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 3/02/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1542fc3-672e-47c1-a21f-82826a2f8ac4
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0185eebbe436da73e1920d7cd834f0897a143894
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2018
---
# <a name="get-started-with-adding-apps-in-microsoft-intune"></a>Microsoft Intune でのアプリ追加の概要

アプリの割り当て、監視、構成、または保護を行うには、対象のアプリを事前に Intune に追加しておく必要があります。 Intune では、異なるいくつかのアプリの種類がサポートされます。 また、使用可能なオプションはアプリの種類ごとに異なります。

Intune では、以下の種類のアプリを追加して、会社のデバイスに割り当てることができます。
- **ストアからのアプリ** - アプリ ストアで入手できるアプリに適用される付加的なモバイル アプリ管理を必要とするデバイスの場合。
- **社内で作成された (基幹業務) アプリ** - ユーザーのデバイスにダウンロードされたファイルをアップロードします。
- **組み込まれているアプリ** - Office 365 アプリなどの精選された管理対象アプリを iOS デバイスと Android デバイスに簡単に割り当てます。 
- **Web 上のアプリ** - Intune によって、デバイスのホーム画面上の Web アプリへのショートカットが作成されます。

## <a name="how-do-i-assign-a-public-store-app"></a>パブリック ストア アプリを割り当てる場合の操作方法

次の例では、Microsoft Intune で iOS アプリを追加する方法を順に説明します。

1. サインイン、 [Azure ポータル](https://portal.azure.com)します。
2. **[すべてのサービス]** > **[Intune]** の順に選択します。 Intune は **[監視 + 管理]** セクションにあります。
3. **[Intune]** ブレードで、**[モバイル アプリ]** を選びます。
4. **[モバイル アプリ]** ワークロードで、**[管理]** セクションの下の **[アプリ]** を選択します。
5. **[アプリ]** ウィンドウの右側で **[追加]**を選択します。
6. **[アプリの種類]** 一覧で、使用可能な **[ストア アプリ]** の種類から **[iOS]** を選択します。
6. **[Search the App Store]\(App Store を検索\)** を選択します。
7. **[Search the App Store]\(App Store を検索\)** ブレードで、まず、アプリ ストアの国のロケールを選択します。
8. 検索ボックスに名前 (または名前の一部) を入力します。 Intune がストアを検索し、関連する結果の一覧を返します。
9. 一覧から目的のアプリを選択し、**[選択]** をクリックします。
10. **[アプリ情報]** を選択して、アプリ情報を構成します。
11. (省略可能) **所有者**、**メモ**、**開発者**、**プライバシー URL** (会社のプライバシー ポリシーを指す) など、このアプリの整理に役立つ詳細を追加します。
12. **[会社のポータルでおすすめアプリとして表示します]** オプションには **[はい]** が選択されています。 
13. 必要なアプリ情報をすべて追加したら、**[OK]** をクリックします。
14. **[アプリの追加]** ブレードで **[追加]** をクリックします。これで、そのアプリの **[概要]** が表示されます。 

## <a name="next-steps"></a>次の手順

Intune にアプリを追加したので、デバイスでアプリを含めることができる従業員のグループを割り当てることができます。

- [アプリをグループに割り当てる方法](apps-deploy.md)
- 
## <a name="learn-more"></a>詳細情報

* [Intune によるアプリ管理とは](app-management.md)
* [アプリのライフサイクルの概要](app-lifecycle.md)
* [アプリ保護ポリシーとは](app-protection-policy.md)
