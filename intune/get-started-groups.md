---
title: Microsoft Intune でグループを作成する
titleSuffix: ''
description: ユーザーをグループにまとめ、ユーザーがアクセスできるポリシーやアプリの管理を簡単にします。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 39a93fb5-d318-4997-a409-b64549a00e7a
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d039cfe5509990ff15fe8a1cb476ad44037d60df
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="create-a-group-to-manage-your-users-and-data-access"></a>ユーザーとデータ アクセスを管理するためのグループを作成する

グループは、ユーザーを管理し、会社のリソースへの従業員のアクセスを制御するために使用されます。 リソースはディレクトリに含まれますが、SaaS アプリや SharePoint サイトなど、外部リソースの場合もあります。

Microsoft Intune は Azure Active Directory (Azure AD) を利用し、会社のリソースへのアクセスを管理します。 このアクセスは、ディレクトリのロールを使用して制御されます。 次に Intune でモバイル デバイスに関してこのアクセスが管理されます。該当グループのメンバーであれば、リソースへのアクセスが許可されます。

## <a name="how-do-i-create-a-group"></a>グループの作成方法

1. [Azure ポータル](https://portal.azure.com)にサインインします。
2. **[すべてのサービス]**、**[Intune]** の順に選択します。 Intune は **[監視 + 管理]** セクションにあります。
3. **[Microsoft Intune]** ウィンドウを開いたら、**[グループ]** を選択します。
4. **[ユーザーとグループ - すべてのグループ]** ウィンドウで、**[新しいグループ]** コマンドを選択します。
5. **[グループ]** ウィンドウで、**[グループの種類]** を選択します。
5. グループの **[名前]** と **[説明]** を追加します。
6. **[メンバーシップの種類]** に **[割り当て済み]** を設定します。 テスト グループに対して **Office 機能は有効にしないでください**。
7. グループの **[メンバー]** を選択します。
7. **[作成]** をクリックします。

グループが作成されたら、**[すべてのグループ]** の一覧に表示されるはずです。 表示されない場合、別のグループを作成してみてください。

## <a name="next-steps"></a>次の手順

[ポリシーの概要](get-started-policies.md) - ユーザーが自分のデバイスで許可のない操作を行うことを禁止する目的でポリシーを作成します。

## <a name="learn-more"></a>詳細情報

* [Intune でグループを利用し、登録制限を設定する](groups-add.md)
* [Azure Active Directory でグループを利用し、会社のリソースへのアクセスを管理する](https://docs.microsoft.com/azure/active-directory/active-directory-manage-groups)
