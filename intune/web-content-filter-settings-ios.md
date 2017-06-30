---
title: "iOS デバイス用の Intune Web コンテンツ フィルター設定"
titleSuffix: Intune on Azure
description: "iOS デバイスからの Web サイトへのアクセスの許可とブロックに使用できる設定について説明します。&quot;"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 5/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 16aa0f3c-8977-4495-9fbe-ca30ad278c9e
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: 8ecce809acbbcda5773d734b07ad42c71a487920
ms.contentlocale: ja-jp
ms.lasthandoff: 06/08/2017


---

# <a name="web-content-filter-settings-for-ios-devices"></a>iOS デバイス用の Web コンテンツ フィルター設定

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

これらの設定を使用して、Web ブラウザーのエンド ユーザーが iOS デバイス上でアクセスできる、またはできない URL を構成します。 このために使用できる方法は 2 つあります。

- **URL の構成** - Apple の組み込み Web フィルターを使用します。不適切または性的に露骨な言語といった成人向け用語を探すものです。 この関数は、各 Web ページを読み込みながら評価し、不適切なコンテンツの識別とブロックを試みます。 さらに、フィルターでチェックされない URL、またはフィルター設定に関係なく常にブロックされる URL を構成できます。

- **特定の Web サイトのみ** (Safari Web ブラウザーのみ) - これらの URL は Safari ブラウザーのブックマークに追加されます。 ユーザーはこれらのサイトに**のみ**アクセスが許可され、他のサイトにはアクセスできません。 ユーザーがアクセスできる URL の正確な一覧がわかっている場合にのみ、このオプションを使用します。
URL を指定しない場合、エンド ユーザーは、microsoft.com、microsoft.net、apple.com 以外の Web サイトにはアクセスできません。



## <a name="get-started"></a>作業開始

1. **[デバイス機能]** ブレードで、**[Web Content Filter (supervised only)]** (Web コンテンツ フィルター (監視モードのみ)) を選択します。
2. **[Web コンテンツ フィルター]** ブレードで、構成する **[フィルターの種類]** を以下から選択します。
    - **[未構成]** - フィルター処理は行われていません。
    - **[Configure URLs]**(URL の構成)
    - **[Specific websites only]**(特定の Web サイトのみ)
3. 次に、使用しているフィルターの種類に応じて、以下の関連する手順に従います。


## <a name="configure-urls"></a>URL の構成

1. **[Web コンテンツ フィルター]** ブレードで、必要に応じて、次のいずれかを選択します。
    - **許可された URL** - **[Permitted URLs]**(許可された URL) ブレードで、許可する URL (Apple Web フィルターをバイパスする) を入力し、それぞれの後に Enter を押します。
    - **ブロックされた URL** - **[Blocked URLs]**(ブロックされた URL) ブレードで、ブロックする URL を (Apple Web フィルター設定にかかわらず) 入力し、それぞれの後に Enter を押します。
2. 操作が完了したら、 **[OK]**をクリックします。


## <a name="specific-websites-only"></a>特定の Web サイトのみ

1. **[Web コンテンツ フィルター]** ブレードで、許可する Web サイトの各々について、下記を入力します。
    - **[URL]** - 許可する Web サイトの URL (たとえば **http://www.contoso.com**) を入力します。
    - **[Bookmark Path]**(ブックマークのパス) - ブックマークを保存するパス (たとえば **/Contoso/Business Apps**) を入力します。 ブックマークを追加しない場合は、デバイス上の既定のブックマーク フォルダーに追加されます。
    - **[タイトル]** - ブックマークのわかりやすいタイトルを入力します。
2. 各 Web サイトの情報を入力したら、**[追加]** をクリックします。
3. 操作が完了したら、 **[OK]**をクリックします。

>[!IMPORTANT] 
> 次の URL は、Intune によって自動的に許可されます。
> - www.microsoft.com
> - www.microsoft.net
> - www.apple.com

## <a name="finish-up"></a>完了

**[OK]** を選択して **[プロファイルの作成]** ブレードに戻り、**[作成]** を選択します。

