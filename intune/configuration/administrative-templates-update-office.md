---
title: Microsoft Intune で管理用テンプレートを使用して Office 365 を更新する - Azure |Microsoft Docs
description: Microsoft Intune の管理用テンプレートを使用して、Office 365 アプリを最新バージョンに更新し、Office が更新プログラムをチェックする頻度を選択します。 Office 更新プログラムへの Intune ポリシーが適用されたときに更新されるデバイス レジストリ キーを確認します。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: cf872387d6e6f4f91af9f074f54695b081b79119
ms.sourcegitcommit: 23e9c48348a6eba494d072a2665b7481e5b5c84e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2019
ms.locfileid: "74549110"
---
# <a name="use-update-channel-and-target-version-settings-to-update-office-365-with-microsoft-intune-administrative-templates"></a>更新プログラム チャネルとターゲット バージョンの設定を使用して、Microsoft Intune 管理用テンプレートで Office 365 を更新する

Intune では [Windows 10 テンプレートを使用してグループ ポリシー設定を構成](administrative-templates-windows.md)することができます。 この記事では、Intune で管理用テンプレートを使用して Office 365 を更新する方法について説明します。 また、ポリシーが正常に適用されることを確認するためのガイダンスも提供します。 この情報は、トラブルシューティング時にも役立ちます。

このシナリオでは、デバイス上の Office 365 を更新する管理用テンプレートを Intune で作成します。

管理用テンプレートの詳細については、[Windows 10 テンプレートを使用したグループ ポリシー設定の構成](administrative-templates-windows.md)に関するページを参照してください。

適用対象:

- Windows 10 以降
- Office 365

## <a name="prerequisites"></a>必要条件

Office アプリの [Office 365 ProPlus 自動更新を有効にする](https://docs.microsoft.com/deployoffice/configure-update-settings-for-office-365-proplus)ようにしてください。 これは、グループ ポリシーまたは Intune Office 2016 ADMX テンプレートを使用して行うことができます。

![Intune 管理用テンプレートで、Office の [自動更新を有効にする] 設定を設定する](./media/administrative-templates-update-office/admx-enable-automatic-updates.png)

## <a name="set-the-update-channel-in-the-intune-administrative-template"></a>Intune 管理用テンプレートで更新プログラム チャネルを設定する

1. [Intune 管理用テンプレート](administrative-templates-windows.md#create-a-template)で、 **[更新プログラム チャネル]** 設定にアクセスして、必要なチャネルを入力します。 たとえば、`Semi-Annual Channel` を選択します。

    ![Intune 管理用テンプレートで、Office の [更新プログラム チャネル] 設定を設定する](./media/administrative-templates-update-office/admx-enable-update-channel-setting.png)

    > [!NOTE]
    > より頻繁に更新することをお勧めします。 半期は、単に例として使用されています。

2. 必ず、Windows 10 デバイスに[ポリシーを割り当て](device-profile-assign.md)てください。 ポリシーをより早くテストするために、ポリシーを同期することもできます。

    - [Intune でポリシーを同期する](../remote-actions/device-sync.md)
    - [デバイスでポリシーを手動で同期する](https://docs.microsoft.com/intune-user-help/sync-your-device-manually-windows#sync-from-settings-app)

## <a name="check-the-intune-registry-keys"></a>Intune のレジストリ キーを確認する

ポリシーを割り当ててデバイスを同期した後、ポリシーが適用されていることを確認できます。

1. デバイスで、**レジストリ エディター** アプリを開きます。
2. Intune ポリシー パス: `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PolicyManager\Providers\<Provider ID>\default\Device\office16~Policy~L_MicrosoftOfficemachine~L_Updates` にアクセスします。

    > [!TIP]
    > レジストリ キーの `<Provider ID>` が変更されます。 デバイスのプロバイダー ID を検索するには、**レジストリ エディター** アプリを開き、`Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PolicyManager\AdmxInstalled` にアクセスします。 プロバイダー ID が表示されます。

    ポリシーを適用すると、次のレジストリ キーが表示されます。

    - `L_UpdateBranch`
    - `L_UpdateTargetVersion`

    次の例を見ると、`L_UpdateBranch` に `<enabled /><data id="L_UpdateBranchID" value="Deferred" />` のような値が含まれていることがわかります。 この値は、半期チャネルに設定されていることを意味します。

    ![管理用テンプレート L_Updatebranch レジストリ キーの例](./media/administrative-templates-update-office/admx-update-branch-registry-key.png)

    > [!TIP]
    > [Configuration Manager を使用した Office 365 ProPlus の管理](https://docs.microsoft.com/sccm/sum/deploy-use/manage-office-365-proplus-updates#change-the-update-channel-after-you-enable-office-365-clients-to-receive-updates-from-configuration-manager)で、値とその意味が一覧表示されます。 レジストリ値は、選択した配布チャネルに基づきます。
    >
    >- 月次チャネル - value="Current"
    >- 月次チャネル (対象指定) - value="Current"
    >- 半期チャネル-値 - value="Current"
    >- 半期チャネル (対象指定) - 値 = value="FirstReleaseDeferred"
    >- Insider ファースト - value="InsiderFast"

この時点で、Intune ポリシーがデバイスに正常に適用されます。

## <a name="check-the-office-registry-keys"></a>Office のレジストリ キーを確認する

1. デバイスで、**レジストリ エディター** アプリを開きます。
2. Office ポリシー パス: `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\ClickToRun\Configuration` にアクセスします。

    次のレジストリ キーが表示されます。

    - `UpdateChannel`: 構成された設定に応じて変更される動的キー。
    - `CDNBaseUrl`: Office 365 をデバイスにインストールするときに設定します。

3. `UpdateChannel` 値を確認します。 この値は、Office が更新される頻度を示します。 [Configuration Manager を使用した Office 365 ProPlus の管理](https://docs.microsoft.com/sccm/sum/deploy-use/manage-office-365-proplus-updates#change-the-update-channel-after-you-enable-office-365-clients-to-receive-updates-from-configuration-manager)で、値と設定内容が一覧表示されます。

    次の例を見ると、`UpdateChannel` が `http://officecdn.microsoft.com/pr/492350f6-3a01-4f97-b9c0-c7c6ddf67d60` に設定されていることがわかります。これは、**毎月**です。

    ![管理用テンプレート Office 更新プログラム チャネル レジストリ キーの例](./media/administrative-templates-update-office/admx-update-channel-office-registry-key.png)

    この例は、ポリシーがまだ適用されていないことを意味しています。これは、**半年**ではなく、まだ**毎月**に設定されているためです。

このレジストリ キーは、 **[タスク スケジューラ]**  >  **[Office の自動更新 2.0]** を実行したとき、またはユーザーがデバイスにサインインしたときに更新されます。 確認するには、 **[Office 自動更新 2.0]** タスク > **[トリガー]** を開きます。 トリガーによっては、`UpdateChannel` レジストリ キーが更新されるまでに少なくとも 1 日以上かかることがあります。

## <a name="force-office-automatic-updates-to-run"></a>Office 自動更新を強制的に実行する

ポリシーをテストするには、デバイスでポリシー設定を強制することができます。 次の手順でレジストリを更新します。 いつもと同様に、レジストリを更新するときは慎重に行います。

1. レジストリ キーをクリアします。

    1. 「 `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\ClickToRun\Updates` 」を参照してください。
    2. `UpdateDetectionLastRunTime` キーをダブル選択し、値のデータを削除して **[OK]** を選択します。

2. Office 自動更新タスクを実行します。

    1. デバイスで**タスク スケジューラ** アプリを開きます。
    2. **[タスク スケジューラ ライブラリ]**  >  **[Microsoft]**  >  **[Office]** を展開します。
    3. **[Office 自動更新 2.0]**  >  **[実行]** を選択します。

        ![タスク スケジュールを開き、Office 自動更新を実行する](./media/administrative-templates-update-office/admx-task-scheduler-office-automatic-updates.png)

        タスクが完了するのを待ちます。これには数分かかることがあります。

3. **レジストリ エディター** アプリで、`Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\ClickToRun\Configuration` にアクセスします。 `UpdateChannel` 値を確認します。

    ポリシーに設定されている値で更新される必要があります。 この例では、値は `http://officecdn.microsoft.com/pr/7ffbc6bf-bc32-4f92-8982-f9dd17fd3114` に設定される必要があります。

この時点で、デバイスで Office 更新プログラム チャネルが正常に変更されています。 この更新プログラムを受信して状態を確認するユーザーに対して、Office 365 アプリを開くことができます。

## <a name="force-the-office-synchronization-to-update-account-information"></a>Office の同期を強制してアカウント情報を更新する  

さらに多くを行う場合は、Office で最新バージョンの更新プログラムを取得するように強制できます。 次の手順は、確認として、またはデバイスがそのチャネルから最新バージョンの更新プログラムを迅速に取得する必要がある場合にのみ実行してください。 それ以外の場合は、Office でジョブを実行させ、自動的に更新します。

### <a name="step-1-force-the-office-version-to-update"></a>手順 1.Office のバージョンを強制的に更新する

1. 選択している更新プログラム チャネルが Office バージョンでサポートされていることを確認します。 [Office 365 ProPlus の更新履歴](https://docs.microsoft.com/officeupdates/update-history-office365-proplus-by-date)では、さまざまな更新チャネルをサポートするビルド番号が一覧表示されます。

2. [Intune 管理用テンプレート](administrative-templates-windows.md#create-a-template)で、 **[ターゲット バージョン]** 設定にアクセスして、必要なバージョンを入力します。

    **[ターゲット バージョン]** 設定は、次の設定のようになります。

    ![Intune 管理用テンプレートで、Office の [ターゲット バージョン] 設定を設定する](./media/administrative-templates-update-office/admx-enable-target-version-setting.png)

> [!IMPORTANT]
>
> - 必ずポリシーを割り当ててください。
> - 既存のポリシーを変更すると、変更は、割り当てられているすべてのユーザーに影響します。
> - この機能をテストしている場合は、テスト ポリシーを作成し、そのポリシーをユーザーのテスト グループに割り当てることをお勧めします。

### <a name="step-2-check-the-office-version"></a>手順 2: Office のバージョンを確認する

ポリシーをすべてのユーザーに展開する前に、次の手順を使用してポリシーをテストすることを検討してください。

1. **レジストリ エディター** アプリで、`Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PolicyManager\Providers\<Provider ID>\default\Device\office16~Policy~L_MicrosoftOfficemachine~L_Updates` にアクセスします

2. `L_UpdateTargetVersion` 値を確認します。 ポリシーが適用されると、値は、`<enabled /><data id="L_UpdateTargetVersionID" value="16.0.10730.20344" />` のように、入力したバージョンに設定されます。

    この時点で、Intune ポリシーがデバイスに正常に適用されます。

3. 次に、Office を強制的に更新できます。 Excel などの Office アプリを開きます。 (おそらくは **[アカウント]** メニュー内で) 今すぐ更新することを選択します。

    更新には数分かかります。 Office が、入力したバージョンを取得しようとしていることを確認できます。

      1. デバイスで、`C:\Program Files (x86)\Microsoft Office\Updates\Detection\Version` にアクセスします。
      2. `VersionDescriptor.xml` ファイルを開き、`<Version>` セクションに移動します。 使用可能なバージョンは、Intune ポリシーで入力したものと同じバージョンである必要があります。次に例を示します。

          ![バージョン記述子 Office XML ファイルのバージョン セクションを確認する](./media/administrative-templates-update-office/office-version-descriptor-xml-example.png)

4. 更新プログラムをインストールすると、Office アプリに新しいバージョンが表示されます (たとえば、 **[アカウント]** メニューで)

## <a name="next-steps"></a>次の手順

[Office 365 クライアントの更新プログラム チャネル値の更新](https://docs.microsoft.com/sccm/sum/deploy-use/manage-office-365-proplus-updates#change-the-update-channel-after-you-enable-office-365-clients-to-receive-updates-from-configuration-manager)

[Office 365 ProPlus の Office クラウド ポリシー サービスの概要](https://docs.microsoft.com/deployoffice/overview-office-cloud-policy-service)

[Windows 10 テンプレートを使用し、Microsoft Intune でグループ ポリシー設定を構成する](administrative-templates-windows.md)
