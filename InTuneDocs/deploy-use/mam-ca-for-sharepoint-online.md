---
title: "SharePoint Online のアプリ アクセスの構成"
description: 
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 531b09bb-ddfd-498f-8ee3-6675d2466208
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e5dd7cb5b320df7f443b52a1b502027fa3c4acaf
ms.openlocfilehash: 992273f88e4bbe234f11f936d6416dbaf0d394e9
ms.lasthandoff: 04/19/2017


---

# <a name="create-a-sharepoint-online-conditional-access-policy-to-only-allow-apps-supported-by-mam"></a>MAM でサポートされているアプリのみを許可する SharePoint Online の条件付きアクセス ポリシーを作成する
このトピックでは、Intune モバイル アプリ管理 (MAM) ポリシーをサポートするモバイル アプリのみを許可するように Exchange Online の条件付きアクセスをセットアップする手順について説明します。

## <a name="configure-a-sharepoint-online-policy"></a>SharePoint Online ポリシーを構成する
**手順 1:** アプリのアクセス機能が含まれる [Azure Portal](https://portal.azure.com) にサインインします。 Azure ポータルを初めて使用する場合は、「[Azure ポータルの Microsoft Intune MAM ポリシー対応](azure-portal-for-microsoft-intune-mam-policies.md)」トピックを参照してください。

**手順 2:** **[参照] > [Intune] > [Intune モバイル アプリケーション管理] ブレード > [設定]** の順に移動し、**[条件付きアクセス]** セクションで **[SharePoint Online]** を選択します。

![[条件付きアクセス] セクションと [SharePoint Online] ブレードが開かれていることを示す [設定] ブレードのスクリーンショット](../media/mam-ca-settings-spo.png)

**手順 3:** **[許可されたアプリ]** ブレードの **[Intune アプリ ポリシーをサポートするアプリを許可する]** オプションを選択して、SharePoint Online へのアクセスを Intune MAM ポリシーでサポートされているアプリにのみ許可します。 Intune MAM ポリシーでサポートされているアプリのみを許可するオプションを選択すると、サポートされているアプリの一覧が表示されます。

![アプリの一覧を示す [許可されたアプリ] ブレードのスクリーンショット](../media/mam-ca-spo-allowed-apps.png)

**手順 4:** このポリシーをユーザーに適用するには、**[制限対象のユーザー グループ]** ブレードを開き、**[ユーザー グループの追加]** を選択します。 このポリシーを適用する 1 つまたは複数のユーザー グループを選択します。

![[ユーザー グループの追加] オプションが強調表示されている [制限対象のユーザー グループ] ブレードのスクリーンショット](../media/mam-ca-spo-restricted-groups.png)


**手順 5:** 前の手順で選択したユーザー グループに、このポリシーの影響を受けないようにしたいユーザーがいるとします。 このような場合、ユーザーのグループを除外ユーザー グループ一覧に追加します。 **[SharePoint Online]** ブレードで、**[Exempted user groups] (除外するユーザー グループ)** を選択します。 **[ユーザー グループの追加]** を選択してユーザー グループの一覧を開きます。 このポリシーから除外するグループを選択します。  

## <a name="modifying-an-existing-policy"></a>既存のポリシーの変更
### <a name="adding-or-deleting-user-groups"></a>ユーザー グループの追加または削除
**[制限対象のユーザー グループ]** 一覧から**ユーザー グループを削除**するには、[制限対象のユーザー グループ] ブレードを開き、削除するユーザー グループを選択し、... をクリックします。 [削除] が表示されます。 **[削除]** を選択すると、一覧からユーザー グループが削除されます。 手順は、**[制限対象のユーザー グループ]** 一覧からユーザー グループを削除する手順と同じです。


## <a name="next-steps"></a>次のステップ
[Exchange Online のアプリのアクセス権を構成する](mam-ca-for-exchange-online.md)

[最新の認証を使用していないアプリをブロックする](block-apps-with-no-modern-authentication.md)

### <a name="see-also"></a>関連項目

[MAM ポリシーでアプリ データを保護する](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)

