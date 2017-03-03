---
title: "Microsoft Intune で使用条件を設定する | Intune Azure プレビュー | Microsoft Docs"
description: "Intune Azure プレビュー: Intune 用ポータル サイトでユーザーに表示する使用条件を設定します。 "
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4a3a11a8-9c0c-4334-8c6b-6fea4d0a2efb
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 08dad848a48adad7d9c6f0b5b3286f6550a266bd
ms.openlocfilehash: f7d6ebc9d71a077492ab615a3bc5397e092b1deb
ms.lasthandoff: 02/15/2017

---

# <a name="set-terms-and-conditions"></a>使用条件を設定する 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Intune の使用条件をユーザー グループに展開すると、登録、会社のリソースへのアクセス、ポータル サイト アプリによるデバイスとユーザーへの影響を説明できます。 ユーザーは、会社のポータルを使用して登録したり作業にアクセスしたりする前に、使用条件に同意する必要があります。

さまざまな使用条件を含む複数のポリシーを作成して展開できます。 また、同じ使用条件のさまざまな言語のバージョンを作成し、適切なグループに展開することもできます。

**使用条件を作成するには**:

1. Azure Portal で、**[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。

2. [Intune] ブレードで **[デバイスの登録]** を選択し、**[使用条件]** を選択します。

3. **[作成]** を選択します。

4. **[使用条件の作成]** ブレードで、次の情報を指定します。

   - **[表示名]**: 使用条件の名前。 この名前は、ポータル サイト アプリに表示されます。

   - **[説明]**: (省略可能) Azure Portal でポリシーを識別するための詳細。

5. [Define terms of use (使用条件の定義)] の横にある矢印を選択し、[使用条件] ブレードを開いて、次の情報を入力します。

   - **[タイトル]**: ポータル サイトに表示されるタイトル。

   - **[使用条件の概要]**: ユーザーによる使用条件への同意の意味を説明するテキスト。

   - **[使用条件]**: ユーザーに表示され、ユーザーが同意または拒否する必要がある法的ラベル。"使用条件に同意します" など。

6. **[OK]** を選択します。

