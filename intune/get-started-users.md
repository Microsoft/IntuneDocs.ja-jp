---
title: "ユーザーの概要"
titlesuffix: Azure portal
description: "Intune にユーザーを追加し、モバイル デバイスで会社のリソースにアクセスできるようにします。"
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 08/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 22a232de-ab93-44ab-b0b5-d2b3ccb007fe
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a33eb2d5dc96a2647cf2582bbc6cd4ba2d9c0961
ms.sourcegitcommit: fa6aaf12611c3e03e38e467806fc30b1d0255e88
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2017
---
# <a name="get-started-with-managing-users"></a>ユーザー管理の概要

組織のさまざまな人間について考えてください。 会社のデータを利用するすべての人間が Intune でデータにアクセスするためにユーザーを必要とします。

## <a name="how-do-i-create-a-user"></a>ユーザーの作成方法

1. [Azure ポータル](https://portal.azure.com)にサインインします。
2. **[リソースの検索]** を利用し、**[Intune]** を探します。
3. **[Microsoft Intune]** ブレードを開いたら、**[ユーザー]** を選択します。 **[すべてのユーザー]** ページで、**[+ 新しいユーザー]** を選択します。
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

## <a name="next-steps"></a>次のステップ

[グループの概要](get-started-groups.md) - ユーザーをグループにまとめ、ユーザーがアクセスできるポリシーやアプリの管理を簡単にします。
