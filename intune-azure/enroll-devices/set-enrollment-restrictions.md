---
title: "Intune で登録制限を設定する | Intune Azure プレビュー | Microsoft Docs"
description: "Intune Azure プレビュー: Intune でプラットフォームごとに登録を制限し、デバイス登録の上限数を設定します。 "
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 11/30/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 990062ecf03a117dad74eb71e3f40abb79f22be6
ms.openlocfilehash: 1bdefce35c20ce24b94ee701a2d13b5408f435ce

---

# <a name="set-enrollment-restrictions"></a>登録制限を設定する 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

使用可能なプラットフォームを指定することにより、Intune で登録できるデバイスの種類を制限できます。 また、ユーザーが登録できるデバイスの最大数を設定することもできます。

## <a name="set-device-type-restrictions"></a>デバイスの種類の制限を設定する

1. Azure Portal で、**[その他のサービス]** を選択し、テキスト ボックスに「**Intune**」と入力して、**[その他]** > **[Intune]** の順に選択します。

2. [Intune] ブレードで **[デバイスの登録]** を選択し、**[登録の制限]** を選択します。

3. **[デバイスの種類の制限]** で、**[既定]** を選択します。

4. **[すべてのユーザー]** ブレードで、**[プラットフォーム]** を選択します。

5. Intune で登録できるようにするプラットフォームに対して、**[許可]** を選択します。 登録できないようにするプラットフォームに対しては、**[ブロック]** を選択します。

6. **[保存]** を選択します。

7. **[プラットフォーム構成]** を選択します。

8. 個人所有の iOS デバイスの登録を許可するかブロックするかを選択します。

9. **[保存]** を選択します。

## <a name="set-device-limit-restrictions"></a>デバイス数の制限を設定する

1. Azure Portal の [Intune] ブレードで **[デバイスの登録]** を選択し、**[登録の制限]** を選択します。

2. **[デバイス数の制限]** で、**[既定]** を選択します。

3. **[すべてのユーザー]** ブレードで、**[デバイスの上限数]** を選択します。

4. ユーザーが登録できるデバイスの最大数を選択し、**[保存]** を選択します。



<!--HONumber=Feb17_HO1-->


