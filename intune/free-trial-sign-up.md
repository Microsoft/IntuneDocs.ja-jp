---
title: 'クイック スタート: Microsoft Intune を無料で試す'
titleSuffix: ''
description: このクイック スタートでは、無料試用版サブスクリプションを作成し、サポートされている構成とネットワーク要件を理解し、必要に応じてドメイン名を構成します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/09/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 195931c0-8208-43bd-b0af-b1f8e469a32c
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2ec03471e4ff3940f09fe4a9bef53b86e32bafa8
ms.sourcegitcommit: 63b55e81122e5c15893302b109ae137c30855b55
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67713339"
---
# <a name="quickstart-try-microsoft-intune-for-free"></a>クイック スタート:Microsoft Intune を無料で試す 

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

2. 会社名に続けて「 **.onmicrosoft.com**」と入力してアカウントを作成します。 

    ![Intune 試用版アカウントの新しい資格情報の手順のスクリーンショット](./media/account-sign-up-site-user-id.png)

    **.onmicrosoft.com** ではない独自のカスタム ドメインを組織で使用したい場合は、この記事で後述する Microsoft 365 管理センターで変更することができます。

3. サインアップ プロセスの最後に新しいアカウント情報が表示されます。

    ![アカウント情報の画像](./media/intune-end-of-sign-up-process.png) 

## <a name="sign-in-to-the-azure-portal"></a>Azure portal にサインインする

1. 新しいブラウザー ウィンドウを開き、アドレスバーに「 **https://portal.azure.com** 」と入力します。 
2. 前述の手順で付与された資格情報を使用してサインインします。

    ![Azure portal のサインイン ページの画像](./media/azure-portal-signin.png)

3. Azure portal で Microsoft Intune を表示するには、ページの左側にあるサイドバーから **[すべてのサービス]** を選択します。
4. フィルター ボックスで **Microsoft Intune** を検索して選択します。
5. **星**マークを選択し、お気に入りサービス一覧の一番下に Intune を追加し、Intune ダッシュボードを開きます。

試用版にサインアップすると、アカウント情報の記載された電子メール メッセージが、サインアップ プロセス中に指定した電子メール アドレスに送信されます。 このメールで、試用版がアクティブになったことが確認されます。

> [!TIP]
> Azure portal を使用するときは、プライベート モードではなく標準モードでブラウザーを使用した方が結果がよくなる場合があります。

## <a name="set-the-mdm-authority-to-intune"></a>MDM 機関を Intune に設定する

Azure portal にサインインして、Intune を選択した後、MDM 機関をまだ設定していないことを示すオレンジのバナーが表示されることがあります。 モバイル デバイス管理 (MDM) 機関の設定によって、デバイスの管理方法が決まります。 MDM 機関を設定してからでないと、ユーザーは管理対象のデバイスを登録できません。

MDM 機関を Intune に設定するには、次の手順を実行します。

1. 新しいブラウザー ウィンドウを開き、アドレスバーに「 **https://portal.azure.com** 」と入力します。 
2. **[すべてのサービス]**  >  **[Microsoft Intune]** を選択します。
3. デバイスの管理を有効にしていないことを示すバナーを選択するか、すぐにバナーが表示されない場合は **[デバイスの登録]** を選択します。 デバイス管理をまだ有効にしていない場合、 **[MDM 機関の選択]** ブレードが表示されます。

    > [!NOTE]
    > MDM 機関を設定した場合に、MDM 機関の値が **[デバイスの登録]** ブレードに表示されます。 オレンジのバナーは、MDM 機関をまだ設定していない場合にのみ表示されます。 

    ![[MDM 機関の選択] ブレードの画像](./media/choose-mdm-authority.png) 

4. MDS 機関が設定されていない場合は、 **[MDM 機関の選択]** で、MDM 機関を **[Intune MDM 機関]** に設定します。

MDM 機関について詳しくは、「[モバイル デバイス管理機関の設定](mdm-authority-set.md)」をご覧ください。

## <a name="configure-your-custom-domain-name-optional"></a>カスタム ドメイン名を構成する (省略可能)

前述のように、 **.onmicrosoft.com** ではない独自のカスタム ドメインを組織で使用したい場合は、Microsoft 365 管理センターで変更することができます。 次の手順に従ってカスタム ドメイン名を追加、確認、および構成できます。  

> [!IMPORTANT]
> *初期*ドメイン名の **onmicrosoft.com** の部分は名前変更または削除できません。 ただし、企業のアイデンティティを明確にするために、Intune で使う*カスタム* ドメイン名を追加、確認、削除することはできます。 詳細については、[カスタム ドメイン名の構成](custom-domain-name-configure.md)に関するページを参照してください。

1. [Microsoft 365 管理センター](https://admin.microsoft.com)を開き、管理者アカウントを使用してサインインします。

2. ナビゲーション ウィンドウで **[セットアップ]**  >  **[ドメイン]**  >  **[ドメイン名の追加]** の順に選択します。

3. カスタム ドメイン名を入力します。 **[次へ]** を選択します。

   ![Microsoft 365 管理センターのスクリーンショット - [ドメイン名の追加]](./media/domain-custom-add.png)

4. 前の手順で入力したドメインの所有者が自分であることを確認します。 
    
    **[メールでコードを送信する]** を選択すると、ドメインの登録済み連絡先にメールが送信されます。 メールを受け取ったら、コードをコピーし、 **[ここに確認コードを入力]** というフィールドに貼り付けます。 確認コードが一致すると、ドメインがテナントに追加されます。 見慣れないメール アドレスが表示されることがあります。 一部のレジストラーは、実際のメール アドレスを表示しません。 また、ドメインの登録時のものとメール アドレスが異なる場合があります。

   ![Microsoft 365 管理センターのスクリーンショット - [ドメイン名の確認]](./media/domain-custom-verify.png)

   > [!NOTE]
   > TXT レコードの検証の詳細については、「[任意の DNS ホスティング プロバイダーで Office 365 用の DNS レコードを作成する](https://support.office.com/article/Create-DNS-records-at-any-DNS-hosting-provider-for-Office-365-7B7B075D-79F9-4E37-8A9E-FB60C1D95166)」を参照してください。

## <a name="admin-experiences"></a>管理者向けの操作性

次の 2 つのポータルを使用できます。
- Azure ([portal.azure.com](https://portal.azure.com)) の Intune ダッシュボードでは、[Intune の各機能](what-is-intune.md)を確認できます。 通常、Intune ダッシュボードで作業します。
- Microsoft 365 管理センター ([admin.microsoft.com](https://admin.microsoft.com)) では、ユーザーの追加と管理を行えます (このために Azure Active Directory を使用していない場合)。 また、課金やサポートなど、アカウントのその他の要素を管理することもできます。

## <a name="next-steps"></a>次の手順

このクイック スタートでは、Intune をテスト環境で試用する無料のサブスクリプションを作成します。 Intune のセットアップについて詳しくは、「[Intune をセットアップする](setup-steps.md)」をご覧ください。

この一連の Intune のクイック スタートに従うには、次のクイック スタートに進んでください。

> [!div class="nextstepaction"]
> [クイック スタート: ユーザーを作成してライセンスを割り当てる](quickstart-create-user.md)
