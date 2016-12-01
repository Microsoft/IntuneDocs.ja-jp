---
title: "カスタムのドメイン名を構成する | Microsoft Intune"
description: "Intune サブスクリプションのカスタム ドメイン名を追加します"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/22/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2382f36f-13d8-4a32-81ad-6cfa604889c3
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 29b6e5a3d319c741482fcc2b600842e2e42b96e2
ms.openlocfilehash: 9fe78bca15ffee1e5e0e7e3758ff70b6bc92b619


---


# <a name="configure-a-custom-domain-name"></a>カスタムのドメイン名を構成する

組織が Intune などの Microsoft クラウド ベース サービスにサインアップすると、**yourdomain.onmicrosoft.com** のように Azure Active Directory (AD) でホストされる最初のドメイン名が付与されます。 この例で、**yourdomain** はサインアップ時に選択したドメイン名、**onmicrosoft.com** はサブスクリプションに追加するアカウントに割り当てられるサフィックスです。 組織でカスタムのドメインを保有している場合、Intune のインスタンスを構成して、サブスクリプションで提供されたドメイン名ではなく、カスタムのドメインを使用できます。

ユーザー アカウントを作成する、またはオンプレミスの Active Directory を同期する前に、.onmicrosoft.com ドメインのみを使用するか、1 つ以上のカスタム ドメイン名を追加するかを決定することを強くお勧めします。 ユーザーを追加する前にカスタム ドメインの構成を行い、他のドメイン リソースにアクセスするときと同じ資格情報でユーザーがサインインできるようにしておくと、サブスクリプションのユーザー ID 管理を単純化できます。

Microsoft のクラウドベースのサービスにサブスクライブすると、そのサービスのインスタンスが Microsoft [Azure AD テナント](http://technet.microsoft.com/library/jj573650.aspx#BKMK_WhatIsAnAzureADTenant)になり、Azure AD によって、クラウドベースのサービスの ID サービスとディレクトリ サービスが提供されます。 Intune で組織のカスタム ドメイン名の使用を構成するタスクは、他の Azure AD テナントの場合と同じため、[ドメインの追加](https://azure.microsoft.com/documentation/articles/active-directory-add-domain/)に関する記事の情報と手順を利用できます。

> [!TIP]
> Microsoft のクラウドベースのサービスでカスタム ドメインを使用する方法の詳細については、「[Azure Active Directory でのカスタム ドメイン名の概念の概要](https://azure.microsoft.com/documentation/articles/active-directory-add-domain-concepts/)」をご覧ください。

この最初のドメイン名を変更または削除することはできません。 ただし、Intune で使用するカスタム ドメイン名を追加、確認、または削除することはできます。カスタム ドメインがあると、ビジネス アイデンティティを維持するために役立ちます。

## <a name="to-add-and-verify-your-custom-domain"></a>カスタム ドメインを追加して確認するには

1. [Office 365 管理ポータル](https://portal.office.com/Admin/Default.aspx)を開き、管理者アカウントにサインインします。

2. ナビゲーション ウィンドウの **[設定]** &gt; **[ドメイン]** を選択します。

3. **[ドメインの追加]** を選択し、カスタム ドメイン名を入力します。

4. **[ドメインの確認]** ダイアログ ボックスが開き、DNS ホスティング プロバイダーに TXT レコードを作成する値が表示されます。
    - **GoDaddy ユーザー**: Office 365 管理ポータルから GoDaddy のログイン ページにリダイレクトされます。 資格情報を入力し、ドメインの変更アクセス許可に同意すると、TXT レコードが自動的に作成されます。 または [TXT レコードを作成](https://support.office.com/en-us/article/Create-DNS-records-at-GoDaddy-for-Office-365-f40a9185-b6d5-4a80-bb31-aa3bb0cab48a?ui=en-US&rs=en-US&ad=US)できます。
    - **Register.com ユーザー**: この[ステップ バイ ステップの指示](https://support.office.com/en-us/article/Create-DNS-records-at-Register-com-for-Office-365-55bd8c38-3316-48ae-a368-4959b2c1684e?ui=en-US&rs=en-US&ad=US#BKMK_verify)に従って、TXT レコードを作成します。

    > [!TIP]
    > 必ず [Windows デバイス登録](/Intune/deploy-use/set-up-windows-phone-management-with-microsoft-intune)用に DNS エイリアス (CNAME) を作成し、さらに DNS ホスティング プロバイダーでも変更します。

カスタム ドメインを追加し、確認する手順は、[Azure Active Directory でも実行できます](https://azure.microsoft.com/en-us/documentation/articles/active-directory-add-domain/)。

ハイブリッド クラウド シナリオでは、カスタム ドメイン名を追加し、組織がドメインを所有していることを確認した後は、オンプレミス Active Directory でユーザー アカウントの管理を継続し、Azure AD と同期することができます。

## <a name="to-synchronize-on-premises-users-with-azure-ad"></a>オンプレミスのユーザーを Azure AD と同期するには##

1. オンプレミス Active Directory でカスタム ドメインの [UPN サフィックスを追加します](https://technet.microsoft.com/en-us/library/cc772007.aspx)。
2. インポートする予定のオンプレミス ユーザー用に新しい UPN サフィックスを設定します。
3. [Azure AD Connect Sync](https://azure.microsoft.com/en-us/documentation/articles/active-directory-aadconnect/) を実行して、オンプレミス ユーザーを Azure AD と統合します。
4. ユーザー アカウント情報が正常に同期したら、[Office 365 管理ポータル](https://portal.office.com/Admin/Default.aspx)を使用して Microsoft Intune ライセンスを割り当てることができます。

### <a name="see-also"></a>関連項目

[Office 365 の最初の onmicrosoft.com ドメインの概要](https://support.office.com/en-us/article/About-your-initial-onmicrosoft-com-domain-in-Office-365-B9FC3018-8844-43F3-8DB1-1B3A8E9CFD5A?ui=en-US&rs=en-US&ad=US)

[Microsoft Intune を使い始める前に](what-to-know-before-you-start-microsoft-intune.md)
### <a name="next-steps"></a>次のステップ
これで終了です。 *Intune のクイック スタート ガイド*の手順 2 が完了しました。

>[!div class="step-by-step"]

>[&larr;**Intune にサインインする**](.\start-with-a-paid-subscription-to-microsoft-intune-step-1.md)     [**Intune にユーザーを追加する** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-3.md)  



<!--HONumber=Nov16_HO4-->


