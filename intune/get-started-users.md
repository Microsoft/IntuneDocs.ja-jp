---
title: "ユーザーの概要"
titleSuffix: Intune on Azure
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 06/27/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 22a232de-ab93-44ab-b0b5-d2b3ccb007fe
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e711f32ebd77a83b17e6db468f8cb23a409c8d31
ms.sourcegitcommit: 79116d4c7f11bafc7c444fc9f5af80fa0b21224e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2017
---
# <a name="get-started-with-users"></a>ユーザーの概要

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Azure Active Directory は、デバイスやアプリなど、組織のオブジェクト グループを管理し、また、ユーザー グループを管理します。 各デバイスを個々に管理する代わりに、ユーザーやデバイスをまとめてグループにすることができます。 大量のユーザーやデバイスにアプリや設定を簡単に割り当てることができます。

## <a name="how-do-i-create-a-user"></a>ユーザーの作成方法

1. [Azure ポータル](https://portal.azure.com)にサインインします。
2. **[リソースの検索]** を利用し、**[ユーザーとグループ]** を検索します。
3. **[ユーザーとグループ]** ブレードを開いたら、**[すべてのユーザー]** を選択し、**[+ 新しいユーザー]** を選択します。
4. **名前**や**ユーザー名**など、ユーザーの詳細を入力します。 ユーザー名のドメイン名の部分は初回の既定ドメイン名である “contoso.onmicrosoft.com” か、“contoso.com” など、検証済みの非フェデレーション ドメイン名にする必要があります。
5. **[グループ]** の下で、ユーザーを追加するテスト グループを選択します。
6. テスト デバイスにログオンするときに利用できるように、自動生成されたユーザー パスワードを保存します。 このパスワードをユーザーに与える必要があります。パスワードを与えられたユーザーは、自分が覚えられるように普通のパスワードに変更できます。
7. **[ユーザー]** ブレードで、**[作成]** を選択します。

## <a name="assigning-licenses-to-users"></a>ユーザーにライセンスを割り当てる

ユーザーを作成したら、[Office 365 ポータル](http://go.microsoft.com/fwlink/p/?LinkId=698854)を利用し、Intune ライセンスをそのユーザーに割り当てる必要があります。 ライセンスを割り当てないと、ユーザーは自分のデバイスを管理に登録できません。

1. Intune にサインインしたときに使用したものと同じ資格情報で [Office 365 ポータル](http://go.microsoft.com/fwlink/p/?LinkId=698854)にサインインします。
2. **[ユーザー]** > **[アクティブなユーザー]** の順に選択し、前に作成したユーザーを選択します。
3. すべてのユーザーの情報が読み込まれるまでしばらくの間待つ必要があります。 読み込まれたら、ユーザーの **[製品ライセンス]** の **[編集]** を選択します。
4. ユーザーに **[場所]** を割り当て、Intune を **[オン]** に切り替えます。

 > [!NOTE]
 > このとき、このユーザーのライセンスの 1 つが使用されます。 ライブ環境を利用している場合、後でこのライセンスの使用をオフにし、実際のユーザーに再度割り当てることができます。

5. **[保存]** を選択します。
