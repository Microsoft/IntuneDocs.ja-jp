---
title: "グループの概要"
titleSuffix: Azure portal
description: "ユーザーをグループにまとめ、ユーザーがアクセスできるポリシーやアプリの管理を簡単にします。"
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 08/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 39a93fb5-d318-4997-a409-b64549a00e7a
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 705f57eca339f0f70cda9e7db60d33436d8198e7
ms.sourcegitcommit: fa6aaf12611c3e03e38e467806fc30b1d0255e88
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2017
---
# <a name="get-started-with-groups"></a>グループの概要

グループは、ユーザーを管理し、会社のリソースに社員がアクセスする行為を制御するために使用されます。 リソースはディレクトリに含まれますが、SaaS アプリや SharePoint サイトなど、外部リソースの場合もあります。

Microsoft Intune は Azure Active Directory (Azure AD) を利用し、会社のリソースへのアクセスを管理します。 このアクセスは、ディレクトリのロールを使用して制御されます。 次に Intune でモバイル デバイスに関してこのアクセスが管理されます。該当グループのメンバーであれば、リソースへのアクセスが許可されます。

## <a name="how-do-i-create-a-group"></a>グループの作成方法

1. [Azure ポータル](https://portal.azure.com)にサインインします。
2. **[リソースの検索]** を利用し、**[Intune]** を探します。
3. **[Microsoft Intune]** ブレードを開いたら、**[グループ]** を選択します。
4. **[ユーザーとグループ - すべてのグループ]** ブレードで、**[新しいグループ]** コマンドを選択します。
5. **[グループ]** ブレードで、グループの**名前**と**説明**を追加します。
6. **[メンバーシップの種類]** に **[割り当て済み]** を設定します。 テスト グループに対して **Office 機能は有効にしないでください**。
7. **[作成]** をクリックします。

グループが作成されたら、**[すべてのグループ]** の一覧に表示されるはずです。 表示されない場合、別のグループを作成してみてください。

## <a name="next-steps"></a>次のステップ

[ポリシーの概要](get-started-policies.md) - ユーザーが自分のデバイスで許可のない操作を行うことを禁止する目的でポリシーを作成します。

## <a name="learn-more"></a>詳細情報

* [Intune でグループを利用し、登録制限を設定する](groups-add.md)
* [Azure Active Directory でグループを利用し、会社のリソースへのアクセスを管理する](https://docs.microsoft.com/azure/active-directory/active-directory-manage-groups)
