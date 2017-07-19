---
title: "グループの概要"
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
ms.assetid: 39a93fb5-d318-4997-a409-b64549a00e7a
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 04843a918a3c661ab69dfa711f4d22a8feedf5f3
ms.sourcegitcommit: fd2e8f6f8761fdd65b49f6e4223c2d4a013dd6d9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2017
---
# <a name="get-started-with-groups"></a>グループの概要

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

[](./media/generic-users-groups.png)

Microsoft Intune は Azure Active Directory (Azure AD) を利用し、[会社のリソースへのアクセスを管理](https://docs.microsoft.com/azure/active-directory/active-directory-manage-groups)します。 このアクセスは、ディレクトリのロールを使用して制御されます。 次に Intune でモバイル デバイスに関してこのアクセスが管理されます。該当グループのメンバーであれば、リソースへのアクセスが許可されます。

__グループの作成方法__

1. [Azure ポータル](https://portal.azure.com)にサインインします。
2. **[リソースの検索]** を利用し、**[ユーザーとグループ]** を検索します。
3. **[ユーザーとグループ]** ブレードを開いたら、**[すべてのグループ]** を選択します。
4. **[ユーザーとグループ - すべてのグループ]** ブレードで、**[新しいグループ]** コマンドを選択します。
5. **[グループ]** ブレードで、グループの**名前**と**説明**を追加します。
6. **[メンバーシップの種類]** に **[割り当て済み]** を設定します。 テスト グループに対して **Office 機能は有効にしないでください**。
7. **[作成]** をクリックします。

グループが作成されたら、**[すべてのグループ]** の一覧に表示されるはずです。 表示されない場合、別のグループを作成してみてください。
