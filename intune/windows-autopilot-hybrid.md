---
title: Windows Autopilot を使用してハイブリッド Active Directory 参加済みデバイスの Intune 登録を設定する
titleSuffix: Microsoft Intune
description: Windows Autopilot を使用してハイブリッド Active Directory 参加済みデバイスを Intune に登録します
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/2/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8518d8fa-a0de-449d-89b6-8a33fad7b3eb
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1a10d434fbdb5d827c7ecb89d1ae2f7e43c0f951
ms.sourcegitcommit: 1e6fee4032c50ab41a5166db39fbea80a731c541
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/14/2018
ms.locfileid: "51654910"
---
# <a name="deploy-hybrid-azure-ad-joined-devices-using-intune-and-windows-autopilot-preview"></a>Intune と Windows Autopilot を使用してハイブリッド Azure AD 参加済みデバイスをデプロイする (プレビュー)
Intune と Windows Autopilot を使用して、ハイブリッド Azure Active Directory 参加済みデバイスを設定できます。 そのためには、以下の手順のようにします。

> [!NOTE]
> この機能は、今後数日にわたってユーザー ベース全体にロールアウトされます。 そのため、自分のアカウントにロールアウトされるまで、以下の手順を実行できない可能性があります。

## <a name="prerequisites"></a>必要条件

- [ハイブリッド Azure Active Directory 参加済みデバイス](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-plan)を正常に構成します。
    - [Get-MsolDevice コマンドレットを使用して登録を確認]( https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-managed-domains#verify-the-registration)します。

登録するデバイスでは次のことも必要です。
- [2018 年 10 月更新](https://blogs.windows.com/windowsexperience/2018/10/02/how-to-get-the-windows-10-october-2018-update/)の Windows 10 を実行している。
- インターネットにアクセスできる。
- Active Directory にアクセスできる (VPN 接続は非サポート)。
- OOBE (Out-of-Box Experience) を使用している。

## <a name="set-up-windows-10-automatic-enrollment"></a>Windows 10 の自動登録を設定する

1. [Azure Portal](https://portal.azure.com) にサインインして、 **[Azure Active Directory]** を選択します。

   ![Azure Portal のスクリーンショット](./media/auto-enroll-azure-main.png)

2. **[モビリティ (MDM と MAM)]** を選択します。

   ![Azure Portal のスクリーンショット](./media/auto-enroll-mdm.png)

3. **Microsoft Intune** を選択します。

   ![Azure Portal のスクリーンショット](./media/auto-enroll-intune.png)

4. Intune と Windows を使用して Azure Active Directory 参加済みデバイスをデプロイしているユーザーが、**MDM ユーザー スコープ**に含まれるグループのメンバーであることを確認します。

   ![Azure Portal のスクリーンショット](./media/auto-enroll-scope.png)

5. 次の URL の既定値を使用します。
    - **MDM 使用条件 URL**
    - **MDM 探索 URL**
    - **MDM 準拠 URL**
6. **[保存]** を選びます。

## <a name="increase-the-computer-account-limit-in-the-organizational-unit"></a>組織単位でコンピューター アカウントの上限を増やす

Active Directory の Intune コネクタでは、オンプレミスの Active directory ドメインに Autopilot 登録コンピューターが作成されます。 Intune コネクタをホストするコンピューターには、ドメイン内にコンピューター オブジェクトを作成する権限が必要です。 

一部のドメインでは、コンピューターにはコンピューターを作成する権限が付与されません。 または、管理者がドメイン全体のコンピューター アカウントの上限を増やすことを望まない場合があります。 このような場合は、ハイブリッド Azure AD 参加済みデバイスが作成される組織単位に権限を委任できます。

コンピューター作成権限を付与する組織単位は、次のどちらかと一致している必要があります。
- ドメイン参加プロファイルで入力された組織単位
- または、プロファイルが選択されていない場合は、お使いのドメインに対するコンピューターのドメイン名。

1. **[Active Directory ユーザーとコンピューター]** (DSA.msc) を開きます。

2. ハイブリッド Azure AD 参加済みコンピューターの作成に使用する組織単位を右クリックして、**[制御の委任]** を選択します。

    ![制御の委任のスクリーンショット](media/windows-autopilot-hybrid/delegate-control.png)

3. **制御の委任**ウィザードで、**[次へ]** > **[追加]** > **[オブジェクトの種類]** を選択します。

4. **[オブジェクトの種類]** ダイアログ ボックスで、**[コンピューター]** をオンにして、**[OK]** を選択します。

    ![制御の委任のスクリーンショット](media/windows-autopilot-hybrid/object-types-computers.png)

5. **[ユーザー、コンピューター、またはグループの選択]** ダイアログ ボックスの **[選択するオブジェクト名を入力してください]** ボックスに、コネクタをインストールするコンピューターの名前を入力します。

    ![制御の委任のスクリーンショット](media/windows-autopilot-hybrid/enter-object-names.png)

6. **[名前の確認]** を選択して入力を検証し、**[OK]** > **[次へ]** を選択します。

7. **[委任するカスタム タスクを作成する]** > **[次へ]** を選択します。

8. **[フォルダー内の次のオブジェクトのみ]** を選択し、次のオプションをオンにします。
    - **コンピューター オブジェクト**
    - **選択されたオブジェクトをこのフォルダーに作成する**
    - **選択されたオブジェクトをこのフォルダーから削除する**

    ![制御の委任のスクリーンショット](media/windows-autopilot-hybrid/only-following-objects.png)
    
9. **[次へ]** を選択します。

10. **[アクセス許可]** で **[フル コントロール]** をオンにし (他のすべてのオプションがオンになります)、**[次へ]** > **[完了]** を選択します。

    ![制御の委任のスクリーンショット](media/windows-autopilot-hybrid/full-control.png)

## <a name="install-the-intune-connector"></a>Intune コネクタをインストールする

Active Directory の Intune コネクタを、インターネットと Active Directory にアクセスできる Windows Server 2016 を実行しているコンピューターにインストールする必要があります。 スケールと可用性を高めたり、複数の Active Directory ドメインをサポートしたりするため、環境内に複数のコネクタをインストールできます。 他の Intune コネクタが実行されていないサーバーにインストールすることをお勧めします。

1. 言語パックをインストールし、「[Intune コネクタ (プレビュー) の言語の要件](https://docs.microsoft.com/windows/deployment/windows-autopilot/intune-connector)」の説明に従って構成したことを確認します。
2. [Intune](https://aka.ms/intuneportal) で、**[デバイスの登録]** > **[Windows 登録]** > **[Active Directory の Intune コネクタ (プレビュー)]** > **[コネクタの追加]** を選択します。 
3. 手順に従ってコネクタをダウンロードします。
4. ダウンロードしたコネクタのセットアップ ファイルを開いて、コネクタをインストールします (ODJConnectorBootstrapper.exe)。
5. セットアップの最後で、**[構成]** を選択します。
6. **[サインイン]** を選択します。
7. ユーザーのグローバル管理者ロールまたは Intune 管理者ロールの資格情報を入力します。
8. **[デバイスの登録]** > **[Windows 登録]** > **[Active Directory の Intune コネクタ (プレビュー)]** に移動し、接続の状態が **[アクティブ]** であることを確認します。

### <a name="configure-web-proxy-settings"></a>Web プロキシ設定の構成

ネットワーク環境に Web プロキシがある場合は、「[既存のオンプレミス プロキシ サーバーと連携する](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-configure-connectors-with-proxy-servers)」の手順に従って、Active Directory の Intune コネクタが正しく動作するようにします。


## <a name="create-a-device-group"></a>デバイス グループを作成する
1. [Intune](https://aka.ms/intuneportal) で、**[グループ]** > **[新しいグループ]** の順に選択します。
2. **[グループ]** ブレードで、次の手順を実行します。
    1. **[グループの種類]** で、**[セキュリティ]** を選択します。
    2. **[グループ名]** と **[グループ テキスト]** を入力します。
    3. **[メンバーシップの種類]** を選択します。
3. 上の **[メンバーシップの種類]** で **[動的デバイス]** を選択した場合は、**[グループ]** ブレードで **[動的なデバイス メンバー]** を選択し、**[高度なルール]** ボックスに次のいずれかのコードを入力します。
    - Autopilot デバイスをすべて含むグループを作成する場合は、「`(device.devicePhysicalIDs -any _ -contains "[ZTDId]")`」と入力します
    - 特定の注文 ID の Autopilot デバイスをすべて含むグループを作成する場合は、「`(device.devicePhysicalIds -any _ -eq "[OrderID]:179887111881") `」と入力します
    - 特定の注文書 ID の Autopilot デバイスをすべて含むグループを作成する場合は、「`(device.devicePhysicalIds -any _ -eq "[PurchaseOrderId]:76222342342")`」と入力します
    
    **[高度なルール]** にコードを追加したら、**[保存]** を選択します。
5. **[作成]** を選択します。  

## <a name="register-your-autopilot-devices"></a>Autopilot デバイスを登録する

次の方法のいずれかを選択して Autopilot デバイスを登録します。

### <a name="register-autopilot-devices-that-are-already-enrolled"></a>既に登録されている Autopilot デバイスを登録する

1. **[すべての対象デバイスを Autopilot に変換する]** を **[はい]** に設定して、Autopilot Deployment プロファイルを作成します。 
2. Autopilot で自動的に登録するメンバーが含まれるグループにプロファイルを割り当てます。

詳しくは、「[Autopilot Deployment プロファイルを作成する](enrollment-autopilot.md#create-an-autopilot-deployment-profile)」をご覧ください。

### <a name="register-autopilot-devices-that-arent-enrolled"></a>登録されていない Autopilot デバイスを登録する

デバイスがまだ登録されていない場合は、自分で登録できます。 詳しくは、「[デバイスを追加する](enrollment-autopilot.md#add-devices)」をご覧ください。

### <a name="register-devices-from-an-oem"></a>OEM からデバイスを登録する

新しいデバイスを購入する場合、OEM によってはデバイスを登録できます。 詳しくは、[Windows Autopilot のページ](http://aka.ms/WindowsAutopilot)をご覧ください。

Autopilot デバイスを登録すると (Intune に登録する前)、3 か所にデバイスが表示されます (名前はシリアル番号に設定されます)。
- Azure portal の Intune の Autopilot デバイス ブレード (**[デバイスの登録]** > **[Windows の登録]** > **[デバイス]**)。
- Azure portal の Intune の Azure AD デバイス ブレード (**[デバイス]** > **[Azure AD デバイス]**)。
- Azure portal の Azure Active Directory の AAD のすべてのデバイス ブレード (**[デバイス]** > **[すべてのデバイス]**)。

Autopilot デバイスの登録後は、4 つの場所に表示されます。
- Azure portal の Intune の Autopilot デバイス ブレード (**[デバイスの登録]** > **[Windows の登録]** > **[デバイス]**)。
- Azure portal の Intune の Azure AD デバイス ブレード (**[デバイス]** > **[Azure AD デバイス]**)。
- Azure portal の Azure Active Directory の AAD のすべてのデバイス ブレード (**[デバイス]** > **[すべてのデバイス]**)。
- Azure portal の Intune のすべてのデバイス ブレード (**[デバイス]** > **[すべてのデバイス]**)。

Autopilot デバイスを登録すると、デバイス名はデバイスのホスト名に変わります。 既定では、"DESKTOP-" で始まります。




## <a name="create-and-assign-an-autopilot-deployment-profile"></a>AutoPilot Deployment プロファイルを作成して割り当てる
Autopilot Deployment プロファイルは、Autopilot デバイスを構成する場合に使用されます。

1. [Intune](https://aka.ms/intuneportal) で、**[デバイスの登録]** > **[Windows の登録]** > **[デプロイ プロファイル]** > **[プロファイルの作成]** の順に選択します。
2. **名前**と、必要に応じて**説明**を入力します。
3. **[配置モード]** では、**[ユーザー ドリブン]** を選択します。
4. **[Azure AD への参加の種類]** ボックスで、**[ハイブリッド Azure AD 参加済み (プレビュー)]** を選択します。
5. **[Out-of-box experience (OOBE)]** を選択し、必要に応じてオプションを構成して、**[保存]** を選択します。
6. **[作成]** を選択して、プロファイルを作成します。 
7. プロファイルのブレードで、**[割り当て]** を選択します。
8. **[グループの選択]** を選択し、**[グループの選択]** ブレードでデバイス グループを選択して、**[選択]** を選択します。

デバイス プロファイルの状態が **[割り当てられていません]** から **[割り当て中]** を経て最後に **[割り当て済み]** に変わるまでに、約 15 分かかります。

## <a name="turn-on-the-enrollment-status-page-optional"></a>登録状態ページを有効にする (省略可能)

1. [Intune](https://aka.ms/intuneportal) で、**[デバイス登録]** > **[Windows 登録]** > **[Enrollment Status Page (Preview)]\(登録ステータス ページ (プレビュー)\)** の順に選択します。
2. **[登録ステータス ページ]** ブレードで、**[既定]** > **[設定]** の順に選択します。
3. **[Show app and profile installation progress]\(アプリとプロファイルのインストールの進行状況を表示する\)** で、**[はい]** を選択します。
4. 必要に応じて、他のオプションを構成します。
5. **[保存]** を選びます。

## <a name="create-and-assign-a-domain-join-profile"></a>ドメイン参加プロファイルを作成して割り当てる

1. [Intune](https://aka.ms/intuneportal) で、**[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** の順に選択します。
2. 次のプロパティを入力します。
   - **名前**: 新しいプロファイルのわかりやすい名前を入力します。
   - **説明**: プロファイルの説明を入力します 
   - **[プラットフォーム]**: **[Windows 10 以降]** を選択します。
   - **[プロファイルの種類]**: **[ドメイン参加 (プレビュー)]** を選択します。
3. **[設定]** を選択し、**[コンピューター名のプレフィックス]**、**[ドメイン名]**、**[組織単位]** (省略可能) を指定します。 
4. **[OK]** > **[作成]** の順に選択します。 プロファイルが作成され、リストに表示されます。
5. プロファイルを割り当てるには、「[デバイス プロファイルを割り当てる](device-profile-assign.md#assign-a-device-profile)」の手順のようにします。 

## <a name="next-steps"></a>次の手順

Windows Autopilot を構成した後は、これらのデバイスを管理する方法を学習します。 詳細については、「[Microsoft Intune デバイスの管理とは](device-management.md)」をご覧ください。
