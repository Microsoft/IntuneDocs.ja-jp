---
title: "Microsoft Intune のドメイン名 | Microsoft Intune"
description: 
keywords: 
author: andredm7
manager: swadhwa
ms.date: 06/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c3c136f0-330d-432a-a91f-16f7dd097e55
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 3d99669f90fe7ebec7854b7a800b09b0685c314e
ms.openlocfilehash: aaede1500f28c6eb8c2a21924d7c3b7f633eca26


---



# Microsoft Intune を使用してカスタム ドメインを管理する

カスタム ドメインを追加し、確認する手順は、[Azure Active Directory でも実行できます](https://azure.microsoft.com/en-us/documentation/articles/active-directory-add-domain/)。

組織が Intune などの Microsoft のクラウド ベース サービスにサインアップすると、**yourdomain.onmicrosoft.com** のように Azure Active Directory でホストされる最初のドメイン名が付与されます。 この例で、**yourdomain** はサインアップ時に選択したドメイン名、**onmicrosoft.com** はサブスクリプションに追加するアカウントに割り当てられるサフィックスです。

この最初のドメイン名を変更または削除することはできません。 ただし、Intune で使用するカスタム ドメイン名を追加、確認、または削除することはできます。カスタム ドメインがあると、ビジネス アイデンティティを維持するために役立ちます。

## カスタム ドメインを追加して確認するには 

1. [Office 365 管理ポータル](https://portal.office.com/Admin/Default.aspx)を開き、管理者アカウントにサインインします。
    > [!IMPORTANT]
    > Microsoft Intune ユーザー、グループ、ドメインを管理する場所の詳細については、「    [Intune アカウント ポータルは、Office 365 管理ポータルに統合されています](https://docs.microsoft.com/en-us/intune/deploy-use/account-portal-merged-with-Office-365)」というお知らせを参照してください。
2. ナビゲーション ウィンドウの **[設定]** &gt; **[ドメイン]** を選択します。
3. **[ドメインの追加]** を選択し、カスタム ドメイン名を入力します。
4. **[ドメインの確認]** ダイアログ ボックスが開き、DNS ホスティング プロバイダーに TXT レコードを作成する値が表示されます。
    > [!TIP]
    > GoDaddy ドメインを使用している場合、Office 365 管理ポータルから GoDaddy のログイン ページにリダイレクトされます。 資格情報を入力し、ドメインの変更アクセス許可に同意すると、TXT レコードが自動的に作成されます。
    > 
    > また、[GoDaddy ドメインを使用している場合、この手順で確認できる値に基づいて TXT レコードを手動で作成する](https://support.office.com/en-us/article/Create-DNS-records-at-GoDaddy-for-Office-365-f40a9185-b6d5-4a80-bb31-aa3bb0cab48a?ui=en-US&rs=en-US&ad=US)こともできます。

    > [!NOTE]
    > Register.com ドメインを使用している場合、この手順で確認できる値に基づき、[こちらの手順](https://support.office.com/en-us/article/Create-DNS-records-at-Register-com-for-Office-365-55bd8c38-3316-48ae-a368-4959b2c1684e?ui=en-US&rs=en-US&ad=US#BKMK_verify)従って TXT レコードを作成してください。

5. 必ず [Windows デバイス登録](https://docs.microsoft.com/en-us/intune/deploy-use/set-up-windows-phone-management-with-microsoft-intune)用に DNS エイリアス (CNAME) を作成し、さらに DNS ホスティング プロバイダーでも変更します。

ハイブリッド クラウド シナリオでは、カスタム ドメイン名を追加し、組織がドメインを所有していることを確認した後は、オンプレミス Active Directory でユーザー アカウントの管理を継続し、Azure AD と同期することができます。

## オンプレミスのユーザーを Azure AD と同期するには##

1. オンプレミス Active Directory でカスタム ドメインの [UPN サフィックスを追加します](https://technet.microsoft.com/en-us/library/cc772007.aspx)。
2. インポートする予定のオンプレミス ユーザー用に新しい UPN サフィックスを設定します。
3. [Azure AD Connect Sync](https://azure.microsoft.com/en-us/documentation/articles/active-directory-aadconnect/) を実行して、オンプレミス ユーザーを Azure AD と統合します。
4. ユーザー アカウント情報が正常に同期したら、[Office 365 管理ポータル](https://portal.office.com/Admin/Default.aspx)を使用して Microsoft Intune ライセンスを割り当てることができます。

### 関連項目

[Office 365 の最初の onmicrosoft.com ドメインの概要](https://support.office.com/en-us/article/About-your-initial-onmicrosoft-com-domain-in-Office-365-B9FC3018-8844-43F3-8DB1-1B3A8E9CFD5A?ui=en-US&rs=en-US&ad=US)

[Microsoft Intune を使い始める前に](what-to-know-before-you-start-microsoft-intune.md)



<!--HONumber=Jun16_HO5-->


