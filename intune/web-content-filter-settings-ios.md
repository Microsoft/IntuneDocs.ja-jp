---
title: "iOS デバイス用の Intune Web コンテンツ フィルター設定"
titlesuffix: Azure portal
description: "iOS デバイスからの Web サイトへのアクセスの許可とブロックに使用できる設定について説明します。\""
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 1/18/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 54202baa7871f38581f4828bb80213be0f88ef61
ms.sourcegitcommit: 1a390b47b91e743fb0fe82e88be93a8d837e8b6a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="web-content-filter-settings-for-ios-devices"></a>iOS デバイス用の Web コンテンツ フィルター設定

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

これらの設定を使用して、Web ブラウザーのエンド ユーザーが iOS デバイス上でアクセスできる、またはできない URL を構成します。 URL を構成する方法には 2 つあります。

- **URL の構成** - Apple の組み込み Web フィルターを使用します。不適切または性的に露骨な言語といった成人向け用語を探すものです。 この関数は、各 Web ページを読み込みながら評価し、不適切なコンテンツの識別とブロックを試みます。 フィルターでチェックされない URL、またはフィルター設定に関係なくブロックされる URL を構成することもできます。

- **特定の Web サイトのみ** (Safari Web ブラウザーのみ) - これらの URL は Safari ブラウザーのブックマークに追加されます。 ユーザーはこれらのサイトに**のみ**アクセスが許可され、他のサイトにはアクセスできません。 このオプションは、ユーザーがアクセスできる URL の正確な一覧がわかっている場合にのみ使います。
URL を指定しない場合、エンド ユーザーは、microsoft.com、microsoft.net、apple.com 以外の Web サイトにはアクセスできません。



## <a name="get-started"></a>作業開始

1. [デバイス機能] ブレードで、**[Web コンテンツ フィルター (監視モードのみ)]** を選びます。
2. **[Web コンテンツ フィルター]** ブレードで、構成する **[フィルターの種類]** を以下から選択します。
    - **[未構成]** - フィルター処理は行われていません。
    - **[Configure URLs]**(URL の構成)
    - **[Specific websites only]**(特定の Web サイトのみ)
3. 次に、使っているフィルターの種類に応じて、次のいずれかの手順を使います。


## <a name="configure-urls"></a>URL の構成

1. **[Web コンテンツ フィルター]** ブレードで、必要に応じて次のいずれかの設定を選びます。
   - **許可された URL** - **[Permitted URLs]**(許可された URL) ブレードで、許可する URL (Apple Web フィルターをバイパスする) を入力し、それぞれの後に Enter を押します。
     > [!NOTE]
     > ここで指定する URL は、Apple Web フィルターの対象にしない URL です。 これらの URL は、許可されている Web サイトのみの一覧ではありません。 そのような Web サイトを指定する場合は、**[特定の Web サイトのみ]** を使用します。

   - **ブロックされた URL** - **[Blocked URLs]**(ブロックされた URL) ブレードで、ブロックする URL を (Apple Web フィルター設定にかかわらず) 入力し、それぞれの後に Enter を押します。
2. 操作が完了したら、 **[OK]**をクリックします。


## <a name="specific-websites-only"></a>特定の Web サイトのみ

1. **[Web コンテンツ フィルター]** ブレードで、許可する Web サイトごとに、以下の設定を構成します。
    - **[URL]** - 許可する Web サイトの URL (たとえば **http://www.contoso.com**) を入力します。
    - **[Bookmark Path]**(ブックマークのパス) - ブックマークを保存するパス (たとえば **/Contoso/Business Apps**) を入力します。 パスを追加しないと、デバイス上の既定のブックマーク フォルダーにブックマークが追加されます。
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

## <a name="next-steps"></a>次の手順

選択したグループにデバイス プロファイルを割り当てることができます。 詳しくは、「[デバイス プロファイルを割り当てる方法](device-profile-assign.md)」をご覧ください。
