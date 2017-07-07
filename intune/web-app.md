---
title: "Web アプリを Intune に追加する方法"
titleSuffix: Intune on Azure
description: "Web アプリを Intune に追加する方法について説明します。\""
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5f08752f-0e87-4ad9-a34c-4991b3150775
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 476e547f2ee21119443b08db0984f66844f701d3
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2017
---
# <a name="how-to-add-web-apps-to-microsoft-intune"></a>Web アプリを Microsoft Intune に追加する方法

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

1. Azure ポータルにサインインします。
2. **[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
3. **[Intune]** ブレードで、**[アプリの管理]** を選択します。
4. **[モバイル アプリ]** ワークロードで、**[管理]** > **[アプリ]** の順に選択します。
5. アプリの一覧の上にある **[追加]** を選択します。
6. **[アプリの追加]** ブレードで、**[アプリ情報]** を選択します。
7. **[アプリの編集]** ブレードで、以下の情報を構成します。 構成が終わったら、**[追加]** をクリックします。
    - **[アプリ URL]** - 割り当てるアプリをホストする Web サイトの URL を入力します。
    - **[アプリ名]** - アプリの名前を入力します。この名前は会社のポータルに表示されます。
    - **[アプリの説明]** - アプリの説明を入力します。 これは会社のポータルでエンド ユーザーに表示されます。
    - **[発行元]** - このアプリの発行元の名前を入力します。
    - **[カテゴリ]** (省略可能) - 1 つ以上の組み込みアプリ カテゴリ、または作成したカテゴリを選択します。 会社のポータルを閲覧するとき、ユーザーにとってアプリを探すのが簡単になります。
    - **[会社のポータルでおすすめアプリとして表示します]** - ユーザーがアプリを探す際に、会社のポータルのメイン ページでアプリを目立つように表示します。
    - **[このリンクを開くには Managed Browser が必要です]** - Web サイトまたは Web アプリへのリンクをユーザーに割り当てると、ユーザーは Intune Managed Browser でのみリンクを開くことができるようになります。 このブラウザーをデバイスにインストールする必要があります。
    - **[アップロード アイコン]** - アプリに関連付けるアイコンをアップロードします。 ユーザーが会社のポータルを参照するとき、アプリにこのアイコンが表示されます。
8. 構成が終了したら、**[アプリの追加]** ブレードで、**[保存]** を選択します。

作成したアプリはアプリの一覧に表示され、選択したグループに割り当てることができるようになります。 詳細については、[アプリをグループに割り当てる方法](apps-deploy.md)に関するページを参照してください。