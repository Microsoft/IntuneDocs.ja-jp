---
# required metadata

title: Microsoft Intune のドメイン名 | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: c3c136f0-330d-432a-a91f-16f7dd097e55

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---



# Microsoft Intune のドメイン名

Microsoft Intune をセットアップする前に、このトピックと「[What to know before you start Microsoft Intune](what-to-know-before-you-start-microsoft-intune.md)」 (Microsoft Intune を開始する前に理解しておくこと) に挙げられているその他の要件を確認してください。.

組織が Intune のような Microsoft のクラウドベースのサービスにサインアップすると、**contoso.onmicrosoft.com** のような初期のドメイン名が付与されます。 この例で、**contoso** はサインアップ時に選択したドメイン名、**onmicrosoft.com** はサブスクリプションに追加するアカウントに割り当てられるサフィックスです。 サインアップ プロセスが完了した後に、ドメイン名を変更することはできません。 ただし、全体管理者の場合、サービスと共に使用する組織独自のカスタム ドメイン名を追加したり、以前に追加したドメインを削除することもできます。

onmicrosoft ドメインを使用する場合、既定では、インポートした各ユーザーは、ユーザー プリンシパル名 (UPN) のサフィックスとして **onmicrosoft.com** を受け取ります。

サインアップ時に付与されたドメイン名ではなく、独自のドメイン名を使用するには、そのドメイン名を Azure Active Directory に追加できます。 ドメインを追加し、そのドメインを所有していることが検証されたら、DNS ホスティング プロバイダーの DNS リソース レコードを変更してドメイン名を含むアカウントとグループを作成できます。 カスタム ドメインを使用する予定がある場合、ユーザー アカウントの管理を簡易にするには、ローカルの Active Directory からユーザーを同期する前に、サブスクリプションにカスタム ドメイン名を構成します。

Intune 用のドメイン名と DNS リソース レコードの構成は、他の Azure Active Directory テナント用の構成と同じです。 手順については、「[Azure Active Directory へのカスタム ドメイン名の追加](https://azure.microsoft.com/documentation/articles/active-directory-add-domain/)」を参照してください。

### 関連項目
[What to know before you start Microsoft Intune (Microsoft Intune を開始する前に理解しておくこと)](what-to-know-before-you-start-microsoft-intune.md)


<!--HONumber=May16_HO1-->


