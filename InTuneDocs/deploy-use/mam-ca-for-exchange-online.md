---
title: "Exchange Online のアプリのアクセス権を構成する | Microsoft Docs"
description: "このトピックでは、MAM アプリの条件付きアクセス ポリシーを構成する方法について説明します。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f2cd1a1f-fd29-4081-8dfa-c40993a107d5
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b6d5ea579b675d85d4404f289db83055642ffddd
ms.openlocfilehash: 49b5b50016e2b36a7ad88fdf0a4e3ae2153290ba


---

# <a name="create-an-exchange-online-conditional-access-to-only-allow-apps-supported-by-mam"></a>MAM でサポートされているアプリのみを許可する Exchange Online の条件付きアクセスを作成する

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

このトピックでは、Intune モバイル アプリ管理 (MAM) ポリシーをサポートするモバイル アプリのみを許可するように Exchange Online の条件付きアクセスをセットアップする手順について説明します。


## <a name="create-an-exchange-online-policy"></a>Exchange Online ポリシーを作成する
1.  アプリのアクセス機能が含まれる [Azure ポータル](https://portal.azure.com)にサインインします。 Azure ポータルを初めて使用する場合は、「[Azure ポータルの Microsoft Intune MAM ポリシー対応](azure-portal-for-microsoft-intune-mam-policies.md)」トピックを参照してください。

2.  **[参照] > [Intune] > [Intune モバイル アプリケーション管理] ブレード > [設定]** の順に選択し、**[条件付きアクセス]** セクションで **[Exchange Online]** を選択します。

  ![[条件付きアクセス] セクションの [Exchange Online] オプションが強調表示された設定ブレードのスクリーンショット](../media/mam-ca-settings-exo.png)

3.  **[Allowed apps]** (許可されているアプリ) ブレードの **[Allow apps that support Intune app policies]** (Intune アプリ ポリシーをサポートするアプリを許可する) オプションを選択して、Exchange Online へのアクセスを Intune MAM ポリシーでサポートされているアプリにのみ許可します。 このオプションを選択すると、サポートされるアプリの一覧が表示されます。

  >[!NOTE]
  >iOS と Android の組み込みのメール クライアントを含め、Exchange Online に接続するすべての Exchange Active Sync メール クライアントは、電子メールを送受信できなくなります。 ユーザーには、Outlook メール アプリを使用する必要があることを知らせる 1 通の電子メールが送信されます。 
4.   このポリシーをユーザーに適用するには、**[制限対象のユーザー グループ]** ブレードを開き、**[ユーザー グループの追加]** を選択します。 このポリシーを適用する 1 つまたは複数のユーザー グループを選択します。

  ![[ユーザー グループの追加] オプションが強調表示されている [制限対象のユーザー グループ] ブレードのスクリーンショット](../media/mam-ca-add-user-group.png)

5.  前の手順で選択したユーザー グループのうち、このポリシーの影響を受けないようにするユーザーがいるとします。 このような場合、ユーザーのグループを除外ユーザー グループ一覧に追加します。 **[Exchange Online]** ブレードで、**[Exempted user groups]** (除外するユーザー グループ) を選択します。 **[ユーザー グループの追加]** を選択してユーザー グループの一覧を開きます。 このポリシーから除外するグループを選択します。  

## <a name="modify-an-existing-policy"></a>既存のポリシーを変更する
### <a name="add-or-delete-user-groups"></a>ユーザー グループを追加または削除する

**[制限対象のユーザー グループ]** 一覧から**ユーザー グループを削除**するには、**[制限対象のユーザー グループ]** ブレードを開き、削除するユーザー グループを選択し、**省略記号 (...)** をクリックします。**[削除]** が表示されます。 **[削除]** を選択すると、一覧からユーザー グループが削除されます。 手順は、**[制限対象のユーザー グループ]** 一覧からユーザー グループを削除する手順と同じです。


## <a name="next-steps"></a>次のステップ
[最新の認証を使用していないアプリをブロックする](block-apps-with-no-modern-authentication.md)
### <a name="see-also"></a>関連項目
[MAM ポリシーでアプリ データを保護する](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Dec16_HO2-->


