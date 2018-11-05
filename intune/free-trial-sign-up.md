---
title: 'クイック スタート: Microsoft Intune を無料で試す'
titlesuffix: ''
description: このクイック スタートでは、無料試用版サブスクリプションを作成し、サポートされている構成とネットワーク要件を理解し、必要に応じてドメイン名を構成します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/13/2018
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 195931c0-8208-43bd-b0af-b1f8e469a32c
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 37445cb2536e02937cf3002dc1cb56ab4b78f12f
ms.sourcegitcommit: 27eed5aba5c8bfafb079171081b68f75a6cbffaf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/22/2018
ms.locfileid: "46581395"
---
# <a name="quickstart-try-microsoft-intune-for-free"></a>クイック スタート: Microsoft Intune を無料で試す 

Microsoft Intune でデバイスやアプリケーションを管理すると、従業員の会社データを保護できます。 このクイック スタートでは、Intune をテスト環境で試用する無料のサブスクリプションを作成します。

Intune には、モバイル デバイス管理 (MDM) 機能とモバイル アプリケーション管理 (MAM) 機能があります。これらの機能は、Microsoft Azure portal を使用して管理されているセキュリティで保護されたクラウドベースのサービスで利用できます。 Intune を使用すると、企業のコンプライアンス ポリシーや要件を満たしながら、従業員の会社リソース (データ、デバイス、アプリ) の構成、アクセス、更新を適切に行うことができるようになります。 

## <a name="prerequisites"></a>必要条件
Microsoft Intune を設定する前に、次の要件を確認してください。

   - [サポートされるオペレーティング システムとブラウザー](supported-devices-browsers.md) 
   - [ネットワーク構成の要件と帯域幅](network-bandwidth-use.md)

## <a name="sign-up-for-a-microsoft-intune-free-trial"></a>Microsoft Intune の無料試用版にサインアップ

Intune は 30 日間無料で試用できます。 既に職場または学校アカウントがある場合は、そのアカウントで**サインイン**し、Intune をサブスクリプションに追加します。 それ以外の場合は、新しいアカウントに**サインアップ**して、組織で Intune を使うことができます。

> [!IMPORTANT]
> 新しいアカウントにサインアップした後で、既存の職場または学校アカウントを組み合わせることはできません。

1. [Microsoft Intune の無料試用版](https://go.microsoft.com/fwlink/?linkid=2019088)ページにアクセスしてフォームに入力してください。

    ![Microsoft Intune 試用版アカウントのサインアップ Web ページのスクリーンショット](./media/account-sign-up-site-full-browser.png)

    IT 運用チームやユーザーの多くが自分と異なるロケールに属している場合は、そのロケールを **[国または地域]** で選択することをお勧めします。 Azure は地域情報を使用して適切なサービスを提供しています。 この設定は後で変更できます。

2. 会社名に続けて「**.onmicrosoft.com**」と入力してアカウントを作成します。 

    ![Microsoft Intune 試用版アカウントのサインアップ Web ページのスクリーンショット](./media/account-sign-up-site-user-id.png)

    **.onmicrosoft.com** ではない独自のカスタム ドメインを組織で使用したい場合は、この記事で後述する Office 365 管理ポータルで変更することができます。

3. サインアップ プロセスの最後に新しいアカウント情報が表示されます。

    ![アカウント情報の画像](./media/intune-end-of-sign-up-process.png) 

## <a name="sign-in-to-the-azure-portal"></a>Azure portal にサインインする

1. 新しいブラウザー ウィンドウを開き、アドレスバーに「**https://portal.azure.com**」と入力します。 
2. 前述の手順で付与された資格情報を使用してサインインします。

    ![Azure portal のサインイン ページの画像](./media/azure-portal-signin.png)

3. Azure portal で Microsoft Intune を表示するには、ページの左側にあるサイドバーから **[すべてのサービス]** を選択します。
4. フィルター ボックスで **Microsoft Intune** を検索して選択します。
5. **星**マークを選択し、お気に入りサービス一覧の一番下に Intune を追加し、Intune ダッシュボードを開きます。

試用版にサインアップすると、アカウント情報の記載された電子メール メッセージが、サインアップ プロセス中に指定した電子メール アドレスに送信されます。 このメールで、試用版がアクティブになったことが確認されます。

## <a name="set-the-mdm-authority-to-intune"></a>MDM 機関を Intune に設定する

モバイル デバイス管理 (MDM) 機関の設定によって、デバイスの管理方法が決まります。 IT 管理者が MDM 機関を設定してからでないと、ユーザーは管理対象のデバイスを登録できません。

MDM 機関を Intune に設定するには、次の手順を実行します。

1. 新しいブラウザー ウィンドウを開き、アドレスバーに「**https://portal.azure.com**」と入力します。 
2. **[すべてのサービス]** > **[Microsoft Intune]** を選択します。
3. オレンジのバナーを選択し、**[モバイル デバイス管理機関]** 設定を開きます。 

    > [!NOTE]
    > オレンジのバナーは、MDM 機関をまだ設定していない場合にのみ表示されます。

4. **[モバイル デバイス管理機関]** で MDM 機関を **[Intune MDM 機関]** に設定します。

## <a name="configure-your-custom-domain-name-optional"></a>カスタム ドメイン名を構成する (省略可能)

前述のように、**.onmicrosoft.com** ではない独自のカスタム ドメインを組織で使用したい場合は、Office 365 管理ポータルで変更することができます。 カスタム ドメイン名を追加し、確認し、構成します。  

> [!IMPORTANT]
> 最初のドメイン名 **onmicrosoft.com** を変更または削除することはできません。 ビジネス ID をクリアにするために、Intune で使われるカスタム ドメイン名を追加、確認、削除することはできます。

1. [Office 365 管理ポータル](https://portal.office.com/Admin/Default.aspx)を開き、管理者アカウントを使用してサインインします。

2. ナビゲーション ウィンドウで **[セットアップ]** > **[ドメイン]** > **[ドメイン名の追加]** の順に選択します。

3. カスタム ドメイン名を入力します。 **[次へ]** を選択します。

   ![[設定] > [ドメイン] を選択して新しいドメイン名を追加した Office 365 管理センターのスクリーンショット](./media/domain-custom-add.png)

4. 前の手順で入力したドメインの所有者であることを確認します。 
    
    **[メールでコードを送信する]** を選択すると、ドメインの登録済み連絡先にメールが送信されます。 メールを受け取ったら、コードをコピーし、**[ここに確認コードを入力]** というフィールドに貼り付けます。 確認コードが一致すると、ドメインがテナントに追加されます。 見慣れないメール アドレスが表示されることがあります。 一部のレジストラーは、実際のメール アドレスと、ドメインの登録時に提供されたものを非表示にすることがあります。

   ![Office 365 管理センターのスクリーンショット - 追加されるドメイン名を確認する](./media/domain-custom-verify.png)

   > [!NOTE]
   > TXT レコードの検証の詳細については、「[任意の DNS ホスティング プロバイダーで Office 365 用の DNS レコードを作成する](https://support.office.com/article/Create-DNS-records-at-any-DNS-hosting-provider-for-Office-365-7B7B075D-79F9-4E37-8A9E-FB60C1D95166)」を参照してください。

## <a name="admin-experiences"></a>管理者向けの操作性

次の 2 つのポータルを使用できます。
- Azure ([portal.azure.com](https://portal.azure.com)) の Intune ダッシュボードでは、[Intune の各機能](what-is-intune.md)を確認できます。 通常、Intune ダッシュボードで作業します。
- Office 365 管理センター ([portal.office.com](https://portal.office.com)) では、ユーザーの追加と管理ができます (Azure Active Directory を使用していない場合)。 また、課金やサポートなど、アカウントのその他の要素を管理することもできます。

## <a name="next-steps"></a>次の手順

このクイック スタートでは、テスト環境で Intune を試用するために無料のサブスクリプションを作成し、カスタム ドメイン名を構成 (省略可能) しました。 Microsoft Intune の詳細については、次のクイック スタートに進んでユーザーを追加し、ライセンスを割り当ててください。

> [!div class="nextstepaction"]
> [ユーザーの作成](get-started-users.md)
