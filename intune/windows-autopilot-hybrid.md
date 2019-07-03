---
title: Hybrid Azure AD 参加済みデバイスの登録 - Windows Autopilot
titleSuffix: ''
description: Windows Autopilot を使用して Hybrid Azure AD 参加済みデバイスを Microsoft Intune に登録します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/06/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 8518d8fa-a0de-449d-89b6-8a33fad7b3eb
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: cb9d1f52ccb147dc9a412f3cb7b601e3b18f214a
ms.sourcegitcommit: a63b9eaa59867ab2b0a6aa415c19d9fff4fda874
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/25/2019
ms.locfileid: "67389320"
---
# <a name="deploy-hybrid-azure-ad-joined-devices-by-using-intune-and-windows-autopilot"></a>Intune と Windows Autopilot を使用して Hybrid Azure AD 参加済みデバイスをデプロイする
Intune と Windows Autopilot を使用して、Hybrid Azure Active Directory (Azure AD) 参加済みデバイスを設定できます。 そのためには、この記事の手順のようにします。

## <a name="prerequisites"></a>必要条件

[Hybrid Azure AD 参加済みデバイス](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-plan)を正しく構成します。 Get-MsolDevice コマンドレットを使用して、[デバイスの登録を確認]( https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-managed-domains#verify-the-registration)します。

登録するデバイスでは次のことも必要です。
- Windows 10 v1809 以降を実行している。
- インターネットにアクセスできる。
- Active Directory にアクセスできる (現時点では VPN 接続は非サポート)。
- OOBE (Out-of-Box Experience) を使用している。
- 参加を試みるドメインのドメイン コントローラーを ping できる。

## <a name="set-up-windows-10-automatic-enrollment"></a>Windows 10 の自動登録を設定する

1. [Azure portal](https://portal.azure.com) にサインインし、左側のウィンドウで **[Azure Active Directory]** を選択します。

   ![Azure portal](./media/auto-enroll-azure-main.png)

1. **[モビリティ (MDM と MAM)]** を選択します。

   ![[Azure Active Directory] ウィンドウ](./media/auto-enroll-mdm.png)

1. **Microsoft Intune** を選択します。

   ![[モビリティ (MDM および MAM)] ウィンドウ](./media/auto-enroll-intune.png)

1. Intune と Windows を使用して Azure AD 参加済みデバイスをデプロイするユーザーが、**MDM ユーザー スコープ**に含まれるグループのメンバーであることを確認します。

   ![[モビリティ (MDM および MAM)] の [構成] ウィンドウ](./media/auto-enroll-scope.png)

1. **[MDM 利用規約 URL]** 、 **[MDM 探索 URL]** 、 **[MDM 準拠 URL]** の各ボックスには既定値を使用して、 **[保存]** を選択します。

## <a name="increase-the-computer-account-limit-in-the-organizational-unit"></a>組織単位でコンピューター アカウントの上限を増やす

Active Directory 用の Intune コネクタでは、オンプレミスの Active directory ドメインに Autopilot 登録済みコンピューターが作成されます。 Intune コネクタをホストするコンピューターには、ドメイン内にコンピューター オブジェクトを作成する権限が必要です。 

一部のドメインでは、コンピューターにはコンピューターを作成する権限が付与されません。 また、ドメインには組み込みの制限 (既定値は 10) があり、コンピューター オブジェクトの作成権限を委任されていないすべてのユーザーとコンピューターに適用されます。 そのため、Intune コネクタをホストし、Hybrid Azure AD 参加済みデバイスを作成する組織単位のコンピューターに、この権限を委任する必要があります。

コンピューター作成権限を付与される組織単位は、次のどちらかと一致している必要があります。
- ドメイン参加プロファイルで入力された組織単位。
- プロファイルが選択されていない場合は、お使いのドメインに対するコンピューターのドメイン名。

1. **[Active Directory ユーザーとコンピューター]** (DSA.msc) を開きます。

1. Hybrid Azure AD 参加済みコンピューターの作成に使用する組織単位を右クリックして、 **[制御の委任]** を選択します。

    ![[制御の委任] コマンド](media/windows-autopilot-hybrid/delegate-control.png)

1. **制御の委任**ウィザードで、 **[次へ]**  >  **[追加]**  >  **[オブジェクトの種類]** を選択します。

1. **[オブジェクトの種類]** ウィンドウで、 **[コンピューター]** チェック ボックスをオンにして、 **[OK]** を選択します。

    ![[オブジェクトの種類] ウィンドウ](media/windows-autopilot-hybrid/object-types-computers.png)

1. **[ユーザー、コンピューター、またはグループの選択]** ウィンドウの **[選択するオブジェクト名を入力してください]** ボックスに、コネクタをインストールするコンピューターの名前を入力します。

    ![[ユーザー、コンピューター、またはグループの選択] ウィンドウ](media/windows-autopilot-hybrid/enter-object-names.png)

1. **[名前の確認]** を選択して入力を検証し、 **[OK]** を選択してから、 **[次へ]** を選択します。

1. **[委任するカスタム タスクを作成する]**  >  **[次へ]** を選択します。

1. **[フォルダー内の次のオブジェクトのみ]** チェック ボックスをオンにし、 **[コンピューター オブジェクト]** 、 **[選択されたオブジェクトをこのフォルダーに作成する]** 、および **[選択されたオブジェクトをこのフォルダーから削除する]** チェック ボックスをオンにします。

    ![[Active Directory オブジェクトの種類] ウィンドウ](media/windows-autopilot-hybrid/only-following-objects.png)
    
1. **[次へ]** を選択します。

1. **[アクセス許可]** で、 **[フル コントロール]** チェック ボックスをオンにします。  
    この操作で、他のすべてのオプションが選択されます。

    ![[アクセス許可] ウィンドウ](media/windows-autopilot-hybrid/full-control.png)

1. **[次へ]** を選択し、 **[完了]** を選択します。

## <a name="install-the-intune-connector"></a>Intune コネクタをインストールする

Active Directory 用の Intune コネクタは、Windows Server 2016 以降を実行しているコンピューターにインストールする必要があります。 コンピューターは、インターネットとお使いの Active Directory にもアクセスできる必要があります。 スケールと可用性を高めたり、複数の Active Directory ドメインをサポートしたりするため、環境内に複数のコネクタをインストールできます。 コネクタは、他の Intune コネクタが実行されていないサーバーにインストールすることをお勧めします。

1. 言語パックをインストールし、「[Intune コネクタ (プレビュー) の言語の要件](https://docs.microsoft.com/windows/deployment/windows-autopilot/intune-connector)」の説明に従って構成したことを確認します。
2. [Intune](https://aka.ms/intuneportal) で、 **[デバイスの登録]**  >  **[Windows の登録]**  >  **[Active Directory の Intune コネクタ (プレビュー)]**  >  **[コネクタの追加]** を選択します。 
3. 手順に従ってコネクタをダウンロードします。
4. ダウンロードしたコネクタのセットアップ ファイル *ODJConnectorBootstrapper.exe* を開いて、コネクタをインストールします。
5. セットアップの最後に、 **[構成]** を選択します。
6. **[サインイン]** を選択します。
7. ユーザーのグローバル管理者ロールまたは Intune 管理者ロールの資格情報を入力します。  
   ユーザー アカウントに Intune ライセンスが割り当てられている必要があります。
8. **[デバイスの登録]**  >  **[Windows の登録]**  >  **[Active Directory の Intune コネクタ (プレビュー)]** に移動し、接続の状態が **[アクティブ]** であることを確認します。

> [!NOTE]
> コネクタにサインインした後、それが [Intune](https://aka.ms/intuneportal) に表示されるまでに数分かかる場合があります。 Intune サービスと正常に通信できる場合にのみ表示されます。

### <a name="turn-off-ie-enhanced-security-configuration"></a>[IE セキュリティ強化の構成] をオフにする
Windows Server では既定で、Internet Explorer セキュリティ強化の構成がオンになっています。 Intune Connector for Active Directory にサインインできない場合、管理者向けの [IE セキュリティ強化の構成] をオフにします。 「[How To Turn Off Internet Explorer Enhanced Security Configuration (Internet Explorer セキュリティ強化の構成をオフにする方法)](https://blogs.technet.microsoft.com/chenley/2011/03/10/how-to-turn-off-internet-explorer-enhanced-security-configuration)」

### <a name="configure-web-proxy-settings"></a>Web プロキシ設定の構成

ネットワーク環境に Web プロキシがある場合は、「[既存のオンプレミス プロキシ サーバーと連携する](autopilot-hybrid-connector-proxy.md)」を参照して、Active Directory 用の Intune コネクタが正しく動作することを確認します。


## <a name="create-a-device-group"></a>デバイス グループを作成する
1. [Intune](https://aka.ms/intuneportal) で、 **[グループ]**  >  **[新しいグループ]** の順に選択します。

1. **[グループ]** ウィンドウで、次のようにします。

    」を参照します。 **[グループの種類]** で、 **[セキュリティ]** を選択します。

    b. **[グループ名]** と **[グループの説明]** を入力します。

    c. **[メンバーシップの種類]** を選択します。

1. メンバーシップの種類で **[動的デバイス]** を選択した場合は、 **[グループ]** ウィンドウで **[動的なデバイス メンバー]** を選択し、 **[高度なルール]** ボックスで次のいずれかのようにします。
    - すべての Autopilot デバイスを含むグループを作成するには、「`(device.devicePhysicalIDs -any _ -contains "[ZTDId]")`」と入力します。
    - Intune のグループ タグ フィールドは、Azure AD デバイス上の OrderID 属性にマップされます。 特定のグループ タグ (OrderID) を使って Autopilot デバイスをすべて含むグループを作成する場合は、「 `(device.devicePhysicalIds -any _ -eq "[OrderID]:179887111881")`」と入力する必要があります
    - 特定の注文書 ID のすべての Autopilot デバイスを含むグループを作成するには、「`(device.devicePhysicalIds -any _ -eq "[PurchaseOrderId]:76222342342")`」と入力します。
    
1. **[保存]** を選択します。

1. **[作成]** を選択します。  

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

"*登録*" が済んだ Autopilot デバイスは、Intune に登録される前に、次の 3 つの場所に表示されます (名前はシリアル番号に設定されます)。
- Azure portal の Intune の **[Autopilot デバイス]** ウィンドウ。 **[デバイスの登録]**  >  **[Windows の登録]**  >  **[デバイス]** を選択します。
- Azure portal の Intune の **[Azure AD デバイス]** ウィンドウ。 **[デバイス]**  >  **[Azure AD デバイス]** を選択します。
- Azure portal の Azure Active Directory の **[Azure AD All Devices]\(Azure AD のすべてのデバイス\)** ウィンドウ ( **[デバイス]**  >  **[すべてのデバイス]** )。

Autopilot デバイスが "*登録*" された後は、次の 4 つの場所に表示されます。
- Azure portal の Intune の **[Autopilot デバイス]** ウィンドウ。 **[デバイスの登録]**  >  **[Windows の登録]**  >  **[デバイス]** を選択します。
- Azure portal の Intune の **[Azure AD デバイス]** ウィンドウ。 **[デバイス]**  >  **[Azure AD デバイス]** を選択します。
- Azure portal の Azure Active Directory の **[Azure AD All Devices]\(Azure AD のすべてのデバイス\)** ウィンドウ。 **[デバイス]**  >  **[すべてのデバイス]** を選択します。
- Azure portal の Intune の **[すべてのデバイス]** ウィンドウ。 **[デバイス]**  >  **[すべてのデバイス]** を選択します。

登録後の Autopilot デバイスの名前は、デバイスのホスト名になります。 既定では、ホスト名は *DESKTOP-* で始まります。


## <a name="create-and-assign-an-autopilot-deployment-profile"></a>AutoPilot Deployment プロファイルを作成して割り当てる
Autopilot Deployment プロファイルは、Autopilot デバイスを構成する場合に使用されます。

1. [Intune](https://aka.ms/intuneportal) で、 **[デバイスの登録]**  >  **[Windows の登録]**  >  **[デプロイ プロファイル]**  >  **[プロファイルの作成]** の順に選択します。
1. **[名前]** を入力し、必要に応じて **[説明]** を入力します。
1. **[配置モード]** では、 **[ユーザー ドリブン]** を選択します。
1. **[Azure AD への参加の種類]** ボックスで、 **[ハイブリッド Azure AD 参加済み (プレビュー)]** を選択します。
1. **[Out-of-box experience (OOBE)]** を選択し、必要に応じてオプションを構成して、 **[保存]** を選択します。
1. **[作成]** を選択して、プロファイルを作成します。 
1. プロファイル ウィンドウで、 **[割り当て]** を選択します。
1. **[グループの選択]** を選択します。
1. **[グループの選択]** ウィンドウで、デバイス グループを選択して、 **[選択]** をクリックします。

デバイス プロファイルの状態が *[未割り当て]* から *[割り当て中]* を経て最後に *[割り当て済み]* に変わるまでに、約 15 分かかります。

## <a name="optional-turn-on-the-enrollment-status-page"></a>(省略可能) 登録状態ページを有効にする

1. [Intune](https://aka.ms/intuneportal) で、 **[デバイスの登録]**  >  **[Windows の登録]**  >  **[登録ステータス ページ]** の順に選択します。
1. **[登録ステータス ページ]** ウィンドウで、 **[既定]**  >  **[設定]** の順に選択します。
1. **[アプリとプロファイルのインストール進行状況を表示する]** ボックスで、 **[はい]** を選択します。
1. 必要に応じて、他のオプションを構成します。
1. **[保存]** を選択します。

## <a name="create-and-assign-a-domain-join-profile"></a>ドメイン参加プロファイルを作成して割り当てる

1. [Intune](https://aka.ms/intuneportal) で、 **[デバイスの構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]** の順に選択します。
1. 次のプロパティを入力します。
   - **[名前]** :新しいプロファイルのわかりやすい名前を入力します。
   - **説明**:プロファイルの説明を入力します。
   - **[プラットフォーム]** : **[Windows 10 以降]** を選択します。
   - **[プロファイルの種類]** : **[ドメイン参加 (プレビュー)]** を選択します。
1. **[設定]** を選択し、 **[コンピューター名のプレフィックス]** 、 **[ドメイン名]** 、および [DN 形式](https://docs.microsoft.com/windows/desktop/ad/object-names-and-identities#distinguished-name)の **[組織単位]** (省略可能) を指定します。 
1. **[OK]**  >  **[作成]** を選択します。  
    プロファイルが作成されて、一覧に表示されます。
1. プロファイルを割り当てるには、「[デバイス プロファイルを割り当てる](device-profile-assign.md#assign-a-device-profile)」の手順に従って、この「[デバイス グループを作成する](windows-autopilot-hybrid.md#create-a-device-group)」の手順で使用したのと同じグループにプロファイルを割り当てます。
   - 複数のドメイン参加プロファイルを展開する
   
     」を参照します。 特定の Autopilot Deployment プロファイルを持つすべての Autopilot デバイスを含む動的グループを作成し、(device.enrollmentProfileName -eq "Autopilot Profile Name") を入力します。 
     
     b. 'Autopilot Profile Name' を、「[AutoPilot Deployment プロファイルを作成して割り当てる](windows-autopilot-hybrid.md#create-and-assign-an-autopilot-deployment-profile)」で作成したプロファイルの表示名に置き換えます。 
     
     c. 複数の Autopilot Deployment プロファイルを作成し、そのデバイスをこの動的グループで指定したプロファイルに割り当てます。

> [!NOTE]
> Hybrid Azure AD Join 用の Windows Autopilot の名前付け機能では、%SERIAL% などの変数はサポートされません。サポートされるのは、コンピューター名のプレフィックスのみです。

## <a name="next-steps"></a>次の手順

Windows Autopilot を構成した後は、これらのデバイスを管理する方法を学習します。 詳細については、「[Microsoft Intune デバイスの管理とは](device-management.md)」を参照してください。
