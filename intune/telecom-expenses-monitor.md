---
title: 通信費管理サービスをセットアップする
titleSuffix: Microsoft Intune
description: Intune を Saaswedo 通信費管理サービスと統合します。
keywords: Saaswedo
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/28/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: b7bf5802-4b65-4aeb-ac99-8e639dd89c2a
ms.reviewer: sumitp
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 031db83302dfef8b99fc83ab7975e233c3eeb799
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2019
ms.locfileid: "57396864"
---
# <a name="set-up-a-telecom-expense-management-service-in-intune"></a>Intune で通信費管理サービスをセットアップする
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune を使用して、企業所有のモバイル デバイスでのデータの使用から発生する通信費を管理することができます。 この機能を有効にするために、Intune は、サードパーティのソフトウェア開発企業である Saaswedo の [Datalert 通信費管理](http://datalert.biz/get-started)ソリューションと統合されています。 Datalert は、通信データの使用状況を管理できるリアルタイム通信費管理ソフトウェアです。 お使いの Intune で管理されているデバイスのコストのかかるデータや予期しないデータおよびローミングの超過を回避できます。

Intune と Datalert の統合により、ローミングや国内のデータ使用料の上限を一元的に設定、監視、適用できるようになります。 定義済みのしきい値を超えると、自動的にアラートがトリガーされます。 さまざまなアクション (ローミングの無効化やしきい値の超過など) を個々のエンド ユーザーやそのグループに適用するように、サービスを構成できます。 Datalert 管理コンソールでは、データ使用量と監視情報を示すレポートが利用できます。

次の図は、Intune が Datalert とどのように統合されているかを示しています。

  ![Intune と Datalert の統合図](./media/tem-datalert-intune-solution-diagram.png)

Datalert サービスを Intune で使用するには、Datalert コンソールと Intune で設定を構成する必要があります。 Datalert サービスと Intune の接続を有効にする必要があります。 Datalert 側の接続が有効になっていても Intune 側が有効になっていない場合、Intune は通信を受け入れますが無視します。

## <a name="supported-platforms"></a>サポートされているプラットフォーム

- Samsung KNOX
- iOS 8.0 以降

## <a name="prerequisites"></a>必要条件

- Microsoft Intune のサブスクリプションおよび Azure Portal へのアクセス。
- Datalert 通信費管理サービスのサブスクリプション

## <a name="list-of-telecom-expense-management-providers"></a>通信費管理プロバイダーの一覧

Intune は、現時点で以下の通信費管理プロバイダーと統合されています。

[Saaswedo Datalert 通信費管理サービス](http://www.datalert.biz/)

## <a name="deploy-the-intune-and-datalert-integrated-solution"></a>Intune と Datalert の統合ソリューションをデプロイする

開始する前に、Intune および Datalert 通信費管理サービスのサブスクリプションがあることを確認します。

### <a name="step-1-connect-the-datalert-service-to-microsoft-intune"></a>手順 1.Datalert サービスを Microsoft Intune に接続する

1. 管理者資格情報を使用して Datalert 管理コンソールにサインインします。

2. Datalert 管理コンソールで、 **[Settings (設定)]** タブに移動し、さらに **[MDM configuration (MDM の構成)]** に移動します。

3. ページの下部にある **[Unblock]\(ブロック解除\)** を選択すると、ページの設定を変更できるようになります。

4. **[Intune / Datalert Connection]\(Intune/Datalert 接続\)** セクションの **[Server MDM]\(サーバー MDM\)** で、 **[Microsoft Intune]** を選択します。    

5. **[Azure AD domain]\(Azure AD ドメイン\)** に Azure テナント ID を入力し、 **[Connection]\(接続\)** をクリックします。

    **[Connection]\(接続\)** を選択すると、Datalert と Intune の間に既存の接続がないことを確認するために、Datalert サービスによって Intune へのチェックインが行われます。 数秒後に Microsoft ログイン ページが表示され、その後に Datalert Azure 認証が行われます。

6. Microsoft 認証ページで、 **[Accept (同意する)]** を選択します。 Datalert の **[thank you]\(ありがとうございます\)** ページにリダイレクトされ、数秒後にそのページが閉じます。 Datalert によって接続が検証され、検証済みの項目一覧の横に緑色のチェック マークが表示されます。 検証が失敗した場合、赤色でメッセージが表示され、対処について Datalert サポートに問い合わせる必要があります。

    次のスクリーン ショットは、接続に成功した場合に表示されることが期待できる緑色のチェック マークを示しています。

   ![接続が成功したことを示す Datalert ページ](./media/tem-datalert-connection.png)

7. **[Datalert App / ADAL Consent]\(Datalert アプリ/ADAL 同意\)** セクションで、スイッチを **[オン]** に設定します。 Microsoft 認証ページで、 **[Accept (同意する)]** を選択します。 Datalert の **[thank you]\(ありがとうございます\)** ページにリダイレクトされ、数秒後にそのページが閉じます。 Datalert によって接続が検証され、検証済みの項目一覧の横に緑色のチェック マークが表示されます。 検証が失敗した場合、赤色でメッセージが表示され、対処について Datalert サポートに問い合わせる必要があります。    

    次のスクリーン ショットは、接続に成功した場合に表示されることが期待できる緑色のチェック マークを示しています。

   ![接続が成功したことを示す Datalert ページ](./media/tem-datalert-adal-consent.png)

8. **[MDM Profiles management (optional)]\(MDM プロファイル管理 (オプション)\)** セクションでスイッチを **[オン]** に設定し、ユーザーによるポリシーの設定をサポートするため Datalert が Intune で使用可能なプロファイルを読み取れるようにします。 Microsoft 認証ページで、 **[Accept (同意する)]** を選択します。 Datalert の **[thank you]\(ありがとうございます\)** ページにリダイレクトされ、数秒後にそのページが閉じます。 Datalert によって接続が検証され、検証済みの項目一覧の横に緑色のチェック マークが表示されます。 検証が失敗した場合、赤色でメッセージが表示され、対処について Datalert サポートに問い合わせる必要があります。    

    次のスクリーン ショットは、接続に成功した場合に表示されることが期待できる緑色のチェック マークを示しています。

   ![接続が成功したことを示す Datalert ページ](./media/tem-datalert-mdm-profiles.png)

### <a name="step-2-check-that-the-telecom-expense-management-feature-is-active-in-intune"></a>手順 2: 通信費管理機能が Intune でアクティブであることを確認する

上記の手順 1 を完了すると、接続が自動的に有効になり、接続状態 **[アクティブ]** が Azure Portal に表示されます。 次の手順は、 **[アクティブ]** 状態を確認する方法を示しています。

1. [Azure ポータル](https://portal.azure.com) にサインインします。

2. **[すべてのサービス]**  >  **[Intune]** の順に選択します。 Intune は **[監視 + 管理]** セクションにあります。

3. **[Intune]** ウィンドウで、 **[デバイス構成]** を選択します。

4. **[デバイス構成]** ウィンドウで、 **[セットアップ]**  >  **[通信費管理]** を選択します。

   ページの上部に表示されている接続状態が **[アクティブ]** になっていることを確認します。

   ![Datalert との接続状態がアクティブであることを示している Intune ページ](./media/tem-azure-portal-enable-service.png)

### <a name="step-3-deploy-the-datalert-app-to-corporate-enrolled-devices"></a>手順 3: Datalert アプリを企業登録デバイスにデプロイする

企業が所有する回線だけからデータ使用量が収集されるようにするには、2 つの設定を行う必要があります。
- Intune でデバイス カテゴリを作成します
- Datalert アプリの対象を会社の電話だけに設定します

#### <a name="define-device-categories-and-device-groups-mapped-to-the-categories"></a>デバイスのカテゴリと各カテゴリにマップされるデバイス グループを定義する

組織のニーズに従って、少なくとも 2 つのデバイス カテゴリ (たとえば、企業と個人) を作成します。 次に、各カテゴリの動的なデバイス グループを作成します。 必要に応じて、組織用のその他のカテゴリを作成できます。

これらのカテゴリは、登録時にユーザーに表示されます。 ユーザーが選択したカテゴリに応じて、登録デバイスは該当するデバイス グループに移動されます。 デバイスのカテゴリを作成する方法の手順については、「[Map devices to groups](device-group-mapping.md)」(デバイスをグループにマップする) を参照してください。

  ![[ポリシーの追加] ウィンドウのスクリーンショット](./media/tem-dynamic-membership-rules.png)

#### <a name="create-the-datalert-app-in-intune"></a>Intune で Datalert アプリを作成する

次の手順に従って、プラットフォームごとに、Intune で Datalert アプリを作成します。 次の手順では、例として iOS を使用します。

1. [Azure portal](https://portal.azure.com) の **[Intune]** ウィンドウで、 **[クライアント アプリ]** を選択します。

2. **[クライアント アプリ]** ウィンドウで、 **[管理]**  >  **[アプリ]** の順に選択します。

3. **[追加]** を選択してアプリを追加します。

4. アプリの種類を選択します。 たとえば、iOS の場合は、 **[iOS ストア アプリ]** を選択します。

5. **[アプリ ストアを検索します]** で、検索ウィンドウに「**Datalert**」と入力して、Datalert アプリを検索します。

6. **Datalert** アプリを選択し、 **[選択]** を選択します。

   ![[ポリシーの追加] ウィンドウのスクリーンショット](./media/tem-select-app-from-apple-app-store.png)

7. 残りの手順を完了して、IOS 用アプリを作成します。

   ![[ポリシーの追加] ウィンドウのスクリーンショット](./media/tem-steps-to-create-the-app.png)

#### <a name="assign-the-datalert-app-to-the-corporate-device-group"></a>Datalert アプリを企業のデバイス グループに割り当てる

1. **[クライアント アプリ] - [アプリ]** ウィンドウで、前の手順で作成した iOS Datalert アプリを選択します。

2. **[アプリ]** ウィンドウで、 **[管理]**  >  **[割り当て]** を選択します。

3. **[グループの追加]** を選択し、企業のデバイス グループを選択する手順に従います。

4. グループにとってアプリのインストールが必須であるか省略可能であるかを選択します。 次の例のスクリーンショットは、インストールが必須であることを示しています。つまり、ユーザーは、自分のデバイスを登録した後、Datalert アプリをインストールする必要があります。

   ![[ポリシーの追加] ウィンドウのスクリーンショット](./media/tem-assign-datalert-app-to-device-group.png)

### <a name="step-4-add-corporate-paid-phone-lines-to-the-datalert-console"></a>手順 4:企業が料金を支払う電話回線を Datalert コンソールに追加する

これで、Intune サービスと Datalert サービスが互いに通信するように構成されました。 次に、企業が料金を支払う電話回線を Datalert コンソールに追加し、携帯データまたはローミング データの使用量違反に対するしきい値と動作を定義する必要があります。 企業が料金を支払う電話回線を手動で Datalert コンソールに追加するか、またはデバイスが Intune に登録されたら自動的に追加することができます。

これらの項目を設定するには、[Microsoft Intune 用の Datalert のセットアップ ページ](http://www.datalert.fr/microsoft-intune/intune-setup) (http://www.datalert.fr/microsoft-intune/intune-setup)) に移動し、 **[Settings]** タブでセットアップ ウィザードの手順に従います。

  ![[ポリシーの追加] ウィンドウのスクリーンショット](./media/tem-add-phone-lines-to-datalert-console.png)


これで Datalert サービスがアクティブになってデータ使用量の監視が開始され、デバイスでの構成済み使用量制限を超える携帯データおよびローミング データが無効化されるようになります。

## <a name="client-enrollment-experience"></a>クライアント登録のエクスペリエンス
クライアント登録のエクスペリエンスについては、以下をご覧ください。
-   [通信費管理サービスに iOS デバイスを登録する](https://docs.microsoft.com/intune-user-help/enroll-your-device-with-telecom-expense-management-ios)
-   [通信費管理サービスに Android デバイスを登録する](https://docs.microsoft.com/intune-user-help/enroll-your-device-with-telecom-expense-management-android)

## <a name="turning-off-the-datalert-service"></a>Datalert サービスを無効にする

Azure Portal で Datalert サービスを無効にすると、以下のような影響があります。

- 過去の使用量制限の違反によってデバイスに適用されたすべてのアクションが取り消されます。
- ユーザーによるデータ アクセスとローミングがブロックされなくなります。
- Intune は引き続きサービスからの信号を受け入れますが、それらを無視するようになります。

**サービスを無効にするには**

1. Azure Portal の **[通信費管理]** ウィンドウで、 **[無効]** を選択します。

2. **[保存]** を選択します。

## <a name="viewing-data-usage-and-roaming-reports"></a>データ使用量およびローミング レポートを表示する

現時点では、Saaswedo の Datalert 管理コンソールでのみデータ使用量のレポートを利用できます。

エンドユーザーが Datalert アプリをインストールするための手順はまもなく追加されます。
