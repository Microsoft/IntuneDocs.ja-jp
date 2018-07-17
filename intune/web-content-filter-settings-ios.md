---
title: iOS デバイス用の Microsoft Intune Web コンテンツ フィルター設定
titlesuffix: ''
description: iOS を実行するデバイスからの Web サイトへのアクセスの許可とブロックに使用できる Microsoft Intune 設定について説明します。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 24be76637257a3252d6660e8912d7fd2e214dccf
ms.sourcegitcommit: 4ef14cc543b73191862201c1e0bae44dddd7d9f6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/09/2018
ms.locfileid: "37921350"
---
# <a name="web-content-filter-settings-for-ios-devices"></a>iOS デバイス用の Web コンテンツ フィルター設定

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

この記事では、iOS を実行するデバイスからのブラウザーの URL アクセスの制御に使用できる Microsoft Intune 設定を示します。

URL の構成に使用できる次の 2 つの方法があります。

- **URL の構成** - Apple の組み込み Web フィルターを使用します。不適切または性的に露骨な言語といった成人向け用語を探すものです。 この関数は、各 Web ページを読み込みながら評価し、不適切なコンテンツの識別とブロックを試みます。 フィルターでチェックされない URL、またはフィルター設定に関係なくブロックされる URL を構成することもできます。

- **特定の Web サイトのみ** (Safari Web ブラウザーのみ) - これらの URL は Safari ブラウザーのブックマークに追加されます。 ユーザーはこれらのサイトに**のみ**アクセスが許可され、他のサイトにはアクセスできません。 このオプションは、ユーザーがアクセスできる URL の正確な一覧がわかっている場合にのみ使います。
URL を指定しない場合、エンド ユーザーは、microsoft.com、microsoft.net、apple.com 以外の Web サイトにはアクセスできません。

## <a name="get-started"></a>作業開始

1. [デバイス機能] ページで、**[Web コンテンツ フィルター (監視モードのみ)]** を選択します。
2. **[Web コンテンツ フィルター]** ページで、構成する **[フィルターの種類]** を以下から選択します。
    - **[未構成]** - フィルター処理は行われていません。
    - **[Configure URLs]**(URL の構成)
    - **[Specific websites only]**(特定の Web サイトのみ)
3. 次に、使っているフィルターの種類に応じて、次のいずれかの手順を使います。


## <a name="configure-urls"></a>URL の構成

1. **[Web コンテンツ フィルター]** ページで、必要に応じて次のいずれかの設定を選択します。
   - **[許可する URL]** - **[許可する URL]** ページで、許可する URL (Apple Web フィルターをバイパスする) を入力し、それぞれの後に Enter を押します。
     > [!NOTE]
     > ここで指定する URL は、Apple Web フィルターの対象にしない URL です。 これらの URL は、許可されている Web サイトのみの一覧ではありません。 そのような Web サイトを指定する場合は、**[特定の Web サイトのみ]** を使用します。

   - **[ブロックする URL]** - **[ブロックする URL]** ページで、ブロックする URL (Apple Web フィルター設定にかかわらず) を入力し、それぞれの後に Enter を押します。
2. 操作が完了したら、 **[OK]** をクリックします。


## <a name="specific-websites-only"></a>特定の Web サイトのみ

1. **[Web コンテンツ フィルター]** ウィンドウで、許可する Web サイトごとに、以下の設定を構成します。
    - **[URL]** - 許可する Web サイトの URL (たとえば `https://www.contoso.com`) を入力します。
    - **[Bookmark Path]**(ブックマークのパス) - ブックマークを保存するパス (たとえば **/Contoso/Business Apps**) を入力します。 パスを追加しないと、デバイス上の既定のブックマーク フォルダーにブックマークが追加されます。
    - **[タイトル]** - ブックマークのわかりやすいタイトルを入力します。
2. 各 Web サイトの情報を入力したら、**[追加]** をクリックします。
3. 操作が完了したら、 **[OK]** をクリックします。

> [!IMPORTANT]
> 次の URL は、Intune によって自動的に許可されます。
> - <www.microsoft.com>
> - <www.microsoft.net>
> - <www.apple.com>

## <a name="finish-up"></a>完了

**[OK]** を選択して **[プロファイルの作成]** ウィンドウに戻り、**[作成]** を選択します。

## <a name="next-steps"></a>次の手順

選択したグループにデバイス プロファイルを割り当てることができます。 詳しくは、「[デバイス プロファイルを割り当てる方法](device-profile-assign.md)」をご覧ください。
