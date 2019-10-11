---
title: Microsoft Intune で通信費管理サービスを設定する - Azure | Microsoft Docs
titleSuffix: ''
description: Microsoft Intune を Saaswedo 通信費管理サービスと統合して、データの使用状況を監視し、Android および iOS デバイスにしきい値または制限を設定します。
keywords: Saaswedo
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/09/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: b7bf5802-4b65-4aeb-ac99-8e639dd89c2a
ms.reviewer: sumitp
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a3e459e4e22c7985e2e68e624c413ce967e1a8ba
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2019
ms.locfileid: "71723854"
---
# <a name="set-up-a-telecom-expense-management-service-in-intune"></a>Intune で通信費管理サービスをセットアップする

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune を使用すると、組織所有のモバイル デバイスでのデータ使用から発生する通信費を管理できます。 Intune は、Saaswedo の [Datalert 通信費管理](http://datalert.biz/get-started)と統合されています。 Datalert は、通信データの使用状況を管理するリアルタイム通信費管理ソリューションです。 お使いの Intune で管理されているデバイスのコストのかかるデータや予期しないデータおよびローミングの料金を回避できます。

Datalert との統合により、ローミングや国内のデータ使用量の上限を設定、監視、適用できます。 定義したしきい値を超えると、自動的にアラートがトリガーされます。 さまざまなアクション (ローミングの無効化やしきい値の超過など) が個人やグループに適用されるように、サービスを構成することもできます。 Datalert 管理コンソールには、データ使用量と監視情報を示すレポートが含まれます。

次の図では、Intune が Datalert とどのように統合されているかを示します。

  ![Intune と Datalert の統合図](./media/telecom-expenses-monitor/tem-datalert-intune-solution-diagram.png)

Datalert サービスを Intune で使用するには、Datalert と Intune でいくつかの構成を設定します。 この記事では、以下の方法を示します。

- Datalert コンソールで Datalert サービスを Intune に接続するための設定を構成します。
- Intune でこの接続がアクティブで有効になっていることを確認します。
- Intune を使用して Datalert アプリをデバイスに追加します。
- Datalert サービスをオフにし、Intune に対して無効にします (省略可能)。

## <a name="supported-platforms"></a>サポートされているプラットフォーム

- Knox (Samsung) 対応の Android 4.4 以降のデバイス

  [Knox がサポートされている Android のバージョン](https://seap.samsung.com/faq/what-versions-android-support-knox-standard-and-knox-premium-sdks-0) (Samsung の Web サイトが開きます) では、Knox でサポートされているバージョンが示されています。

- iOS 8.0 以降

## <a name="prerequisites"></a>必要条件

- Microsoft Intune のサブスクリプションおよび [Azure portal](https://portal.azure.com) へのアクセス
- [Datalert](http://www.datalert.biz/) のサブスクリプション (Datalert の Web サイトが開きます)

## <a name="telecom-expense-management-providers"></a>通信費管理プロバイダー

Intune は、以下の通信費管理プロバイダーと統合されています。

- [Saaswedo Datalert 通信費管理サービス](http://www.datalert.biz/) (Datalert の Web サイトが開きます)

## <a name="deploy-the-intune-and-datalert-solution"></a>Intune と Datalert のソリューションを展開する

### <a name="step-1-connect-the-datalert-service-to-intune"></a>手順 1.Datalert サービスを Intune に接続する

1. 管理者資格情報を使用して Datalert 管理コンソールにサインインします。

2. コンソールで、 **[Settings]\(設定\)** タブの **[MDM configuration]\(MDM の構成\)** に移動します。

3. **[Unblock]\(ブロック解除\)** を選択します。 **[Unblock]\(ブロック解除\)** を選択すると、ページで設定を変更または更新できます。

4. **[Intune / Datalert Connection]\(Intune/Datalert 接続\)**  >  **[Server MDM]\(サーバー MDM\)** で、 **[Microsoft Intune]** を選択します。

5. **[Azure AD domain]\(Azure AD ドメイン\)** に、Azure テナント ID を入力します。 **[Connection]\(接続\)** を選択します。

    **[Connection]\(接続\)** を選択すると、Datalert サービスが Intune にチェックインします。 既存の Datalert 接続がないことが確認されます。 しばらくすると、Microsoft のサインイン ページが表示され、その後で Datalert の Azure 認証が行われます。

6. Microsoft 認証ページで、 **[Accept (同意する)]** を選択します。

    Datalert の **[thank you]\(ありがとうございます\)** ページにリダイレクトされ、そのページはすぐに閉じます。 Datalert によって接続が検証され、検証済みの項目の横に緑色のチェック マークが表示されます。 検証に失敗した場合は、赤色のメッセージが表示されます。 Datalert サポートに問い合わせてください。

    次の図では、接続が成功した場合の緑色のチェック マークが示されています。

      ![接続が成功したことを示す Datalert ページ](./media/telecom-expenses-monitor/tem-datalert-connection.png)

7. **[Datalert App / ADAL Consent]\(Datalert アプリ/ADAL 同意\)** で、スイッチを **[On]\(オン\)** に設定します。 Microsoft 認証ページで、 **[Accept (同意する)]** を選択します。

    Datalert の **[thank you]\(ありがとうございます\)** ページにリダイレクトされ、そのページはすぐに閉じます。 Datalert によって接続が検証され、検証済みの項目の横に緑色のチェック マークが表示されます。 検証に失敗した場合は、赤色のメッセージが表示されます。 Datalert サポートに問い合わせてください。

    次の図では、接続が成功した場合の緑色のチェック マークが示されています。

      ![接続が成功したことを示す Datalert ページ](./media/telecom-expenses-monitor/tem-datalert-adal-consent.png)

8. **[MDM Profiles management (optional)]\(MDM プロファイル管理 (オプション)\)** で、スイッチを **[On]\(オン\)** に設定します。 この設定により、Intune で利用可能なプロファイルが Datalert によって読み取られて、ポリシーを設定できます。 

    Microsoft 認証ページで、 **[Accept (同意する)]** を選択します。

    Datalert の **[thank you]\(ありがとうございます\)** ページにリダイレクトされ、そのページはすぐに閉じます。 Datalert によって接続が検証され、検証済みの項目の横に緑色のチェック マークが表示されます。 検証に失敗した場合は、赤色のメッセージが表示されます。 Datalert サポートに問い合わせてください。

    次の図では、接続が成功した場合の緑色のチェック マークが示されています。

   ![接続が成功したことを示す Datalert ページ](./media/telecom-expenses-monitor/tem-datalert-mdm-profiles.png)

### <a name="step-2-confirm-telecom-expense-management-is-active-in-intune"></a>手順 2: Intune で通信費管理サービスがアクティブになっていることを確認する

手順 1 を完了すると、接続が自動的に有効になります。 Intune では、接続状態が **[アクティブ]** と表示されます。 状態がアクティブであることを確認するには、次の手順のようにします。

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインします。

2. **[デバイス構成]**  >  **[通信費管理]** を選択します。 接続状態が **[アクティブ]** になっていることを確認します。

   ![Datalert との接続状態がアクティブであることを示している Intune ページ](./media/telecom-expenses-monitor/tem-azure-portal-enable-service.png)

### <a name="step-3-deploy-the-datalert-app-to-devices"></a>手順 3: Datalert アプリをデバイスに展開する

データ使用量が組織所有の回線からのみ収集されることを確認するには、必ず次のようにします。

- Intune でデバイス カテゴリを作成します。
- Datalert アプリの対象を組織の電話だけに設定します。

ここでは、これらの手順を示します。

#### <a name="create-device-categories-and-device-groups-mapped-to-your-categories"></a>デバイスのカテゴリとカテゴリにマップされるデバイス グループを作成する

組織のニーズに従って、少なくとも 2 つのデバイス カテゴリ (企業と個人など) を作成します。 次に、各カテゴリの動的なデバイス グループを作成します。 必要に応じて、組織用のその他のカテゴリを作成できます。

Intune でのデバイス カテゴリの作成については、[グループへのデバイスのマップ](../enrollment/device-group-mapping.md)に関する記事をご覧ください。

これらのカテゴリは、登録時にユーザーに表示されます ([Android デバイスを登録する](../enrollment/android-enroll.md))。 ユーザーが選択したカテゴリに応じて、登録デバイスは該当するデバイス グループに移動されます。

  ![[ポリシーの追加] ウィンドウのスクリーンショット](./media/telecom-expenses-monitor/tem-dynamic-membership-rules.png)

#### <a name="add-the-datalert-app-to-intune"></a>Datalert アプリを Intune に追加する

次の手順では、Datalert アプリを追加します。 例として、iOS を使用します。 これらの手順に関するさらに具体的な情報については、[アプリの追加](../apps/apps-add.md)および[スコープのタグの使用](../fundamentals/scope-tags.md)に関する記事をご覧ください。

1. **[Intune](https://go.microsoft.com/fwlink/?linkid=2090973)** で、 **[クライアント アプリ]**  >  **[アプリ]**  >  **[追加]** を選択します。

2. **[アプリの種類]** を選択します。 たとえば、iOS の場合は、 **[ストア アプリ - iOS]** を選択します。

3. **[アプリ ストアを検索します]** で、「**Datalert**」と入力して Datalert アプリを検索します。

4. **Datalert** アプリを選択し、 **[選択]** を選択します。

   ![アプリ ストアから Intune クライアント アプリに Datalert アプリを追加する](./media/telecom-expenses-monitor/tem-select-app-from-apple-app-store.png)

5. アプリ情報やスコープのタグなど、その他のプロパティを入力します。

   ![名前、説明、OS の選択、Intune でのアプリに関するその他の設定など、アプリのプロパティを入力します](./media/telecom-expenses-monitor/tem-steps-to-create-the-app.png)

6. **[OK]**  >  **[追加]** を選択して変更を保存します。 Datalert アプリが一覧に表示されます。

#### <a name="assign-the-datalert-app-to-the-corporate-device-group"></a>Datalert アプリを企業のデバイス グループに割り当てる

1. **[クライアント アプリ - アプリ]** で、前のステップで追加した Datalert アプリを選択します。

2. **[割り当て]**  >  **[グループの追加]** の順に選択します。 アプリの割り当て方法を選択します。 これらの設定について詳しくは、[Intune でのグループへのアプリの割り当て](../apps/apps-deploy.md)に関する記事をご覧ください。

    これらの手順では、グループでアプリのインストールが必須か、省略可能かを選択します。 次の例では、インストールが必須の場合を示します。 必須の場合、ユーザーはデバイスを登録した後で Datalert アプリをインストールする必要があります。

   ![[ポリシーの追加] ウィンドウのスクリーンショット](./media/telecom-expenses-monitor/tem-assign-datalert-app-to-device-group.png)

### <a name="step-4-add-organization-phone-lines-to-the-datalert-console"></a>手順 4:組織の電話回線を Datalert コンソールに追加する

Intune サービスと Datalert サービスは相互に通信するように構成されています。 次に、組織が料金を支払う電話回線を Datalert コンソールに追加します。 また、携帯電話やローミングの使用量に対する違反のしきい値とアクションを入力します。 企業が料金を支払う電話回線を手動で Datalert コンソールに追加するか、またはデバイスが Intune に登録されたら自動的に追加することができます。

これらの項目を設定するには、「[Microsoft Intune 用の Datalert のセットアップ](http://www.datalert.fr/microsoft-intune/intune-setup)」 (Datalert の Web サイトが開きます) をご覧ください。 **[Settings]\(設定\)** タブで、セットアップ ウィザードの手順に従います。

  ![[ポリシーの追加] ウィンドウのスクリーンショット](./media/telecom-expenses-monitor/tem-add-phone-lines-to-datalert-console.png)

Datalert サービスがアクティブになりました。 データ使用量の監視が開始され、デバイスでの構成済み使用量制限を超える携帯データおよびローミング データが無効化されるようになります。

## <a name="end-user-enrollment"></a>ユーザー登録を終了する

エンド ユーザー エクスペリエンスのために、次の記事が役に立ちます。

- [通信費管理サービスに iOS デバイスを登録する](https://docs.microsoft.com/intune-user-help/enroll-your-device-with-telecom-expense-management-ios)
- [通信費管理サービスに Android デバイスを登録する](https://docs.microsoft.com/intune-user-help/enroll-your-device-with-telecom-expense-management-android)

## <a name="turn-off-the-datalert-service"></a>Datalert サービスを無効にする

1. **[Intune](https://go.microsoft.com/fwlink/?linkid=2090973)** で、 **[デバイス構成]**  >  **[通信費管理]** を選択します。
2. **[通信費管理を有効にし、構成した使用量のクォータを超えたデバイスでの携帯データネットワークまたはローミング データをブロックします]** を **[無効]** に設定します。
3. 変更内容を**保存**します。

> [!IMPORTANT]
> Intune で Datalert サービスを無効にした場合:
>
> - 過去の使用量制限の違反によってデバイスに適用されたすべてのアクションが取り消されます。
> - ユーザーによるデータ アクセスとローミングがブロックされなくなります。
> - Intune では、引き続きサービスからの信号が受け入れられますが、無視されるようになります。

## <a name="next-steps"></a>次の手順

Saaswedo の Datalert 管理コンソールでデータ使用量のレポートを利用できます。
