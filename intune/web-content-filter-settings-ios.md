---
title: "iOS デバイス用の Intune Web コンテンツ フィルター設定"
titlesuffix: Azure portal
description: "iOS デバイスからの Web サイトへのアクセスの許可とブロックに使用できる設定について説明します。\""
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 7/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 16aa0f3c-8977-4495-9fbe-ca30ad278c9e
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 89641cee439d7da9f73d56c2ab3d6d8299164700
ms.sourcegitcommit: 3b397b1dcb780e2f82a3d8fba693773f1a9fcde1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/12/2017
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

## <a name="next-steps"></a>次のステップ

選択したグループにデバイス プロファイルを割り当てることができます。 詳しくは、「[デバイス プロファイルを割り当てる方法](device-profile-assign.md)」をご覧ください。
