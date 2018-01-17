---
title: "Web アプリを Intune に追加する方法"
titleSuffix: Azure portal
description: "Web アプリを Intune に追加する方法について説明します。\""
keywords: 
author: erikre
ms.author: erikre
manager: angrobe
ms.date: 12/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5f08752f-0e87-4ad9-a34c-4991b3150775
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6da1441b16a43b5e22bedd9e87970f3388b11b9e
ms.sourcegitcommit: a3a744ea55f38a360ca9f788c77a5b3018d1add5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/30/2017
---
# <a name="how-to-add-web-apps-to-microsoft-intune"></a>Web アプリを Microsoft Intune に追加する方法

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

ユーザー用アプリを管理して割り当てるには、そのアプリを Intune に追加します。 Intune では、Web アプリなど、さまざまなアプリの種類がサポートされています。

> [!Note]
> Web アプリは、Android for Work デバイスではサポートされていません。

Web 上のアプリへのショートカットとしてアプリを Intune に追加するには、次の手順を実行します。

1. Azure Portal にサインインします。
2. **[More resources]\(その他のリソース\)** で、**[Intune]** を検索して選択します。
3. **[Microsoft Intune]** ブレードで、**[モバイル アプリ]** を選択します。
4. **[モバイル アプリ]** ブレードで、**[アプリ]** を選択します。
5. アプリの一覧の上にある **[追加]** を選択します。 **[アプリの追加]** ブレードが表示されます。
6. **[アプリの追加]** ブレードで、**[アプリの種類]** ドロップダウン リストから **[Web アプリ]** という種類を選択します。
7. **[構成]** オプションを選択して **[アプリ情報]** ブレードを表示します。
8. **[アプリ情報]** ブレードで、以下の情報を追加します。
    - **名前** - アプリの名前を入力します。この名前は会社のポータルに表示されます。
    - **説明** - アプリの説明を入力します。 これは会社のポータルでエンド ユーザーに表示されます。
    - **[発行元]** - このアプリの発行元の名前を入力します。
    - **[アプリ URL]** - 割り当てるアプリをホストする Web サイトの URL を入力します。
    - **[カテゴリ]** (省略可能) - 1 つ以上の組み込みアプリ カテゴリ、または作成したカテゴリを選択します。 このように選択すると、会社のポータルを閲覧するとき、ユーザーがアプリを探しやすくなります。
    - **[会社のポータルでおすすめアプリとして表示します]** - ユーザーがアプリを探す際に、会社のポータルのメイン ページでアプリを目立つように表示します。
    - **[このリンクを開くには Managed Browser が必要です]** - Web サイトまたは Web アプリへのリンクをユーザーに割り当てると、ユーザーは Intune Managed Browser でリンクを開けるようになります。 このブラウザーをデバイスにインストールする必要があります。
    - **ロゴ** - アプリに関連付けるロゴをアップロードします。 このロゴは、ユーザーが会社のポータルを閲覧するとき、アプリに表示されるロゴになります。
9. 完了したら、**[情報の追加]** ブレードで、**[OK]** を選択します。
10. 次に、**[アプリの追加]** ブレードで **[追加]** を選択します。

作成したアプリはアプリの一覧に表示され、選択したグループに割り当てることができるようになります。 詳細については、[アプリをグループに割り当てる方法](apps-deploy.md)に関するページを参照してください。