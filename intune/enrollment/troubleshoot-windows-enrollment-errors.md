---
title: Microsoft Intune での Windows デバイスの登録に関する問題のトラブルシューティング
titleSuffix: Microsoft Intune
description: Intune で Windows デバイスを登録するときに発生する最も一般的な問題のトラブルシューティングに関する推奨事項。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/29/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: dae8e92209a8640ab3254e073d3043d390c3791b
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514253"
---
# <a name="troubleshoot-windows-device-enrollment-problems-in-microsoft-intune"></a>Microsoft Intune での Windows デバイスの登録に関する問題のトラブルシューティング

この記事は、Intune 管理者が Windows デバイスを Intune に登録するときに発生する問題を理解し、トラブルシューティングするのに役立ちます。

## <a name="prerequisites"></a>[前提条件]
トラブルシューティングを開始する前に、いくつかの基本的な情報を収集することが重要です。 この情報は、問題の理解を深め、解決策を見つけるための時間を短縮するのに役立ちます。

問題に関する次の情報を収集します。
- 有効な Intune ライセンスがユーザーに割り当てられていますか?  ユーザーは自分のデバイスを登録する前に、必要なライセンスが割り当てられている必要があります。
- Windows デバイスに最新の更新プログラムがインストールされていますか?  Intune の一部の機能は、最新バージョンの Windows でのみ動作します。 Windows Update では、既知の問題について多くの修正が行われています。 多くの場合、最新の更新プログラムをすべて適用すると、Windows デバイスの登録に関する問題は解決されます。 
- 正確なエラー メッセージは何ですか?
- エラー メッセージはどこに表示されますか?
- 問題が発生し始めたのはいつですか? 登録は成功しましたか? 
- どのプラットフォーム (Android、iOS、iPadOS、Windows) に問題がありますか?
- 影響を受けているユーザーの数はどれくらいですか? すべてのユーザーに影響がありますか、それとも一部だけですか?
- 影響を受けているデバイスの数はどれくらいですか? すべてのデバイスですか、一部だけですか?
- MDM 機関は何ですか?
- 登録はどのように実行されますか?  "Bring Your Own Device" (BYOD) ですか、または登録プロファイルを使用する Apple Device Enrollment Program (DEP) ですか?

## <a name="error-messages"></a>エラー メッセージ

### <a name="this-user-is-not-authorized-to-enroll"></a>ユーザーは登録する権限がありません。

エラー 0x801c003: "ユーザーは登録する権限がありません。 もう一度やり直すか、エラー コード (0x801c0003) についてシステム管理者に問い合わせてください。"
エラー 80180003:"問題が発生しました。 ユーザーは登録する権限がありません。 もう一度やり直すか、エラー コード 80180003 についてシステム管理者に問い合わせてください。"

**原因:** 以下のいずれかの条件: 

- ユーザーは、Intune で許可されている最大数のデバイスを既に登録しています。    
- デバイスは、デバイスの種類の制限によってブロックされています。    
- コンピューターで Windows 10 Home が実行されています。 しかし、Intune への登録または Azure AD への参加は、Windows 10 Pro 以上のエディションでのみサポートされます。

#### <a name="resolution"></a>解決策
この問題には、いくつかの解決策が考えられます。

##### <a name="remove-devices-that-were-enrolled"></a>登録されているデバイスを削除する
1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。    
2. **[ユーザー]** > **[すべてのユーザー]** に移動します。    
3. 影響を受けているユーザー アカウントを選択し、**[デバイス]** をクリックします。    
4. 使っていないデバイスまたは不要なデバイスを選択し、**[削除]** をクリックします。 

##### <a name="increase-the-device-enrollment-limit"></a>デバイス登録制限の引き上げ

> [!NOTE]
> この方法では、影響を受けているユーザーだけでなく、すべてのユーザーのデバイス登録制限が増えます。

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。
2. **[デバイス]** > **[登録制限]** > **[既定値]** (**[デバイスの上限数の制限]** の下) > **[プロパティ]** > **[編集]** (**[デバイスの上限数]** の隣) の順に選択し、**[デバイスの上限数]** を増やして (最大 15)、**[レビューと保存]** を選択します。    
 

##### <a name="check-device-type-restrictions"></a>デバイスの種類の制限を確認する
1. グローバル管理者アカウントを使用して、[Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。
2. **[デバイス]** > **[登録制限]** に移動し、**[デバイスの種類の制限]** で **[既定値]** の制限を選択します。    
3. **[プラットフォーム]** を選択し、**[Windows (MDM)]** に対して **[許可]** を選択します。

    > [!IMPORTANT]
    > 現在の設定が既に **[許可]** の場合は、それを **[ブロック]** に変更し、設定を保存してから、**[許可]** に戻して設定を再度保存します。 これにより、登録設定がリセットされます。

4. 約 15 分間待ってから、影響を受けたデバイスをもう一度登録します。    

##### <a name="upgrade-windows-10-home"></a>Windows 10 Home のアップグレード
[Windows 10 Home を Windows 10 Pro またはそれ以上のエディションにアップグレードします](https://support.microsoft.com/help/12384/windows-10-upgrading-home-to-pro)。 



### <a name="this-user-is-not-allowed-to-enroll"></a>This user is not allowed to enroll. (このユーザーは登録を許可されていません。)

エラー 0x801c0003: "This user is not allowed to enroll. You can try again or contact your system administrator with the error code 801c0003." (このユーザーは登録を許可されていません。もう一度やり直すか、エラー コード 801c0003 についてシステム管理者に問い合わせてください。)

**原因:** **[ユーザーはデバイスを Azure AD に参加させることができます]** の設定が **[なし]** に設定されています。 これにより、新しいユーザーは自分のデバイスを Azure AD に参加させることができません。 そのため、Intune の登録に失敗します。

#### <a name="resolution"></a>解決策
1. 管理者として [Azure portal](https://portal.azure.com/) にサインインします。    
2. **Azure Active Directory** > **デバイスの** > **デバイス設定**にアクセスします。    
3. **[ユーザーはデバイスを Azure AD に参加させることができます]** を **[すべて]** に設定します。    
4. デバイスを再登録します。   

### <a name="the-device-is-already-enrolled"></a>デバイスは既に登録されています。

エラー 8018000a: "問題が発生しました。 デバイスは既に登録されています。  エラー コード 8018000a についてシステム管理者に問い合わせてください。"

**原因:** 次の条件のいずれかに該当している場合。
- 別のユーザーが既にデバイスを Intune に登録しているか、デバイスを Azure AD に参加させています。 この問題が該当するかどうかを判断するには、**[設定]** > **[アカウント]** > **[職場のアクセス]** に移動します。 次のようなメッセージを探します: "システム上の他のユーザーが既に職場または学校に接続しています。 その職場または学校への接続を削除してから、やり直してください。"    

#### <a name="resolution"></a>解決策

この問題を解決するには、以下のいずれかの方法を使用します。

##### <a name="remove-the-other-work-or-school-account"></a>他の職場または学校アカウントを削除する
1. Windows からサインアウトし、デバイスの登録または参加を行った別のアカウントを使用してサインインします。    
2. **[設定]** > **[アカウント]** > **[職場のアクセス]** に移動し、職場または学校アカウントを削除します。
3. Windows からサインアウトした後、自分のアカウントを使用してサインインします。    
4. デバイスを Intune に登録するか、デバイスを Azure AD に参加させます。 



### <a name="this-account-is-not-allowed-on-this-phone"></a>This account is not allowed on this phone. (このアカウントは、この電話では許可されていません。)

エラー: "This account is not allowed on this phone. Make sure the information you provided is correct, and then try again or request support from your company." (このアカウントは、この電話では許可されていません。入力した情報が正しいことを確認してから、もう一度やり直すか、会社のサポートを依頼してください。)

**原因:** デバイスを登録しようとしたユーザーに、有効な Intune ライセンスがありません。

#### <a name="resolution"></a>解決策
有効な Intune ライセンスをユーザーに割り当ててから、デバイスを登録します。


### <a name="looks-like-the-mdm-terms-of-use-endpoint-is-not-correctly-configured"></a>MDM の利用規約エンドポイントが正しく構成されていないようです。

**原因:** 次の条件のいずれかに該当している場合。 
 - テナントで Office 365 用モバイル デバイス管理 (MDM) と Intune の両方が使用されていて、デバイスを登録しようとしているユーザーに、有効な Intune ライセンスまたは Office 365 ライセンスがありません。     
- Azure AD の MDM 使用条件が空白であるか、正しい URL が含まれていません。    

#### <a name="resolution"></a>解決策

この問題を解決するには、次のいずれかの方法を使用します。 
 
##### <a name="assign-a-valid-license-to-the-user"></a>ユーザーに有効なライセンスを割り当てる
[Microsoft 365 管理センター](https://portal.office.com/adminportal/home)にアクセスし、Intune または Office 365 のライセンスをユーザーに割り当てます。

##### <a name="correct-the-mdm-terms-of-use-url"></a>MDM 利用規約 URL を修正する
  1. [Azure portal](https://portal.azure.com/) にサインインしてから、**[Azure Active Directory]** を選択します。    
  2. **[モビリティ (MDM および MAM)]** を選択し、**[Microsoft Intune]** をクリックします。    
  3. **[既定の MDM URL を復元する]** を選択し、**[MDM 利用規約 URL]** が **https://portal.manage.microsoft.com/TermsofUse.aspx** に設定されていることを確認します。    
  4. **[保存]** を選びます。    


### <a name="something-went-wrong"></a>問題が発生しました。

エラー 80180026:"問題が発生しました。 正しいサインイン情報を使用し、組織でこの機能を使用していることを確認してください。 もう一度やり直すか、エラー コード 80180026 についてシステム管理者に問い合わせてください。"

**原因:** このエラーは、Windows 10 コンピューターを Azure AD に参加させようとしていて、次の両方の条件が当てはまる場合に、発生する可能性があります。 
- Azure で MDM の自動登録が有効になっています。    
- Intune PC クライアント (Intune PC エージェント) が、Windows 10 コンピューターにインストールされています。

#### <a name="resolution"></a>解決策
この問題をに対処するには、以下のいずれかの方法を使用します。

##### <a name="disable-mdm-automatic-enrollment-in-azure"></a>Azure で MDM の自動登録を無効にします。
1. [Azure portal](https://portal.azure.com/) にサインインします。    
2. **[Azure Active Directory]** > **[モビリティ (MDM および MAM)]** > **[Microsoft Intune]** に移動します。    
3. **[MDM ユーザー スコープ]** を **[なし]** に設定して、**[保存]** をクリックします。    
     
##### <a name="uninstall"></a>アンインストール
コンピューターから Intune PC クライアント エージェントをアンインストールします。    

### <a name="the-software-cannot-be-installed"></a>ソフトウェアをインストールできません。

エラー: "ソフトウェアをインストールできません。0x80cf4017。"

**原因:** クライアント ソフトウェアが最新ではありません。

#### <a name="resolution"></a>解決策
1. [https://admin.manage.microsoft.com](https://admin.manage.microsoft.com) にサインインします。    
2. **[管理]** > **[クライアント ソフトウェアのダウンロード]** に移動し、**[クライアント ソフトウェアのダウンロード]** をクリックします。    
3. インストール パッケージを保存してから、クライアント ソフトウェアをインストールします。 


### <a name="the-account-certificate-is-not-valid-and-may-be-expired"></a>アカウント証明書が無効です。期限が切れている可能性があります。[2]。

エラー:"アカウント証明書が無効です。期限が切れている可能性があります。0x80cf4017。"

**原因:** クライアント ソフトウェアが最新ではありません。

#### <a name="resolution"></a>解決策
1. [https://admin.manage.microsoft.com](https://admin.manage.microsoft.com) にサインインします。    
2. **[管理]** > **[クライアント ソフトウェアのダウンロード]** に移動し、**[クライアント ソフトウェアのダウンロード]** をクリックします。    
3. インストール パッケージを保存してから、クライアント ソフトウェアをインストールします。    

### <a name="your-organization-does-not-support-this-version-of-windows"></a>組織がこのバージョンの Windows をサポートしていません。 

エラー: "問題が発生しました。 組織がこのバージョンの Windows をサポートしていません。  (0x80180014)"

**原因:** Intune テナントで Windows MDM の登録が無効になっています。

#### <a name="resolution"></a>解決策
スタンドアロンの Intune 環境でこの問題を解決するには、次の手順のようにします。 
 
1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)で、**[デバイス]** > **[登録制限]** を選択し、デバイスの種類の制限を選択します。    
2. **[プロパティ]** を選択し、 **[プラットフォームの設定**] の横にある [ > ] **をクリックして**、[Windows に対して**許可** **(MDM)** ] > ます     
3. **[レビューと保存]** をクリックします。    

### <a name="a-setup-failure-has-occurred-during-bulk-enrollment"></a>一括登録中にセットアップ エラーが発生しました。

**原因:** 各プロビジョニング パッケージに対するアカウント パッケージ (Package_GUID) の Azure AD ユーザー アカウントが、Azure AD へのデバイスの参加を許可されていません。 これらの Azure AD アカウントは、Windows 構成デザイナー (WCD) または学校用 PC のセットアップ アプリを使用してプロビジョニング パッケージを設定するときに自動的に作成され、デバイスを Azure AD に参加させるために使用されます。

#### <a name="resolution"></a>解決策
1. 管理者として [Azure portal](https://portal.azure.com/) にサインインします。    
2. **[Azure Active Directory] > [デバイス] > [デバイスの設定]** に移動します。    
3. **[ユーザーはデバイスを Azure AD に参加させることができます]** を **[すべて]** または **[選択済み]** に設定します。

   **[選択済み]** を選択する場合は、**[選択済み]** をクリックしてから **[メンバーの追加]** をクリックし、Azure AD にデバイスを参加させることができるすべてのユーザーを追加します。 プロビジョニング パッケージのすべての Azure AD アカウントが追加されていることを確認します。
 
Windows 構成デザイナー用のプロビジョニング パッケージを作成する方法について詳しくは、「[Windows 10 向けのプロビジョニング パッケージの作成](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-create-package)」を参照してください。

学校用 PC のセットアップ アプリについて詳しくは、「[学校用 PC のセットアップ アプリを使用する](https://docs.microsoft.com/education/windows/use-set-up-school-pcs-app)」を参照してください。


### <a name="auto-mdm-enroll-failed"></a>MDM の自動登録: 失敗 

グループ ポリシーを使用して Windows 10 デバイスを自動的に登録しようとすると、次の問題が発生します。 
- タスク スケジューラの **[Microsoft]** > **[Windows]** > **[EnterpriseMgmt]** で、**AAD から MDM への自動登録のために登録クライアントによって作成されたスケジュール**の前回の実行結果が、次のようになります: **Event 76 Auto MDM Enroll: Failed (Unknown Win32 Error code: 0x8018002b)** (イベント 76 自動 MDM 登録: 失敗 (不明 Win32 エラー コード: 0x8018002b))       
- イベント ビューアーでは、**[アプリケーションとサービス ログ] > [Microsoft] > [Windows] > [DeviceManagement-Enterprise-Diagnostics-Provider] > [Admin]** の下に次のイベントが記録されます。   
    ```asciidoc
    Log Name: Microsoft-Windows-DeviceManagement-Enterprise-Diagnostics-Provider/Admin
    Source: DeviceManagement-Enterprise-Diagnostics-Provider
    Event ID: 76
    Level: Error
    Description: Auto MDM Enroll: Failed (Unknown Win32 Error code: 0x80180002b)
    ```
**原因:** 次の条件のいずれかに該当している場合。 
- UPN に、.local (joe@contoso.local など) のような未確認またはルーティング不可能なドメインが含まれています。    
- **[MDM ユーザー スコープ]** が **[なし]** に設定されています。 

#### <a name="resolution"></a>解決策
UPN に未確認またはルーティング不可能なドメインが含まれている場合は、次の手順のようにします。 

1. Active Directory Domain Services (AD DS) が実行されているサーバーで、**[ファイル名を指定して実行]** ダイアログボックスに「**dsa.msc**」と入力して **[Active Directory ユーザーとコンピューター]** を開き、**[OK]** をクリックします。    
2. お使いのドメインの下にある **[ユーザー]** をクリックしてから、次のようにします。  
    - 影響を受けるユーザーが 1 人だけの場合は、そのユーザーを右クリックし、**[プロパティ]** をクリックします。 **[アカウント]** タブの **[ユーザー ログオン名]** の下にある UPN サフィックス ドロップダウン リストで、contoso.com などの有効な UPN サフィックスを選択し、**[OK]** をクリックします。    
    - 複数のユーザーが影響を受ける場合は、それらのユーザーを選択して、**[操作]** メニューの **[プロパティ]** をクリックします。 **[アカウント]** タブの **[UPN サフィックス]** チェック ボックスをオンにし、ドロップダウン リストで contoso.com などの有効な UPN サフィックスを選択して、**[OK]** をクリックします。
3. 次の同期を待つか、管理者特権の PowerShell プロンプトで次のコマンドを実行して、同期サーバーから差分同期を強制実行します。
    ```powershell
    Import-Module ADSync
    Start-ADSyncSyncCycle -PolicyType Delta
    ```

**[MDM ユーザー スコープ]** が **[なし]** に設定されている場合は、次の手順のようにします。 
 
1. [Azure portal](https://portal.azure.com/) にサインインしてから、**[Azure Active Directory]** を選択します。
2. **[モビリティ (MDM および MAM)]** を選択し、**[Microsoft Intune]** を選択します。    
3. **[MDM ユーザー スコープ]** を **[すべて]** に設定します。 または、**[MDM ユーザー スコープ]** を **[一部]** に設定し、Windows 10 デバイスを自動的に登録できるグループを選択します。    
4. **[MAM ユーザー スコープ]** を **[なし]** に設定します。


### <a name="an-error-occurred-while-creating-autopilot-profile"></a>Autopilot プロファイルの作成中にエラーが発生しました。

**原因:** デバイス名テンプレートで指定されている名前付け形式が要件を満たしていません。 たとえば、シリアル マクロに小文字を使用しています (たとえば、%SERIAL% ではなく %serial%)。

#### <a name="resolution"></a>解決策

名前付け形式が次の要件を満たしていることを確認します。

- デバイスの一意の名前を作成します。 名前は 15 文字以下にする必要があります。また、文字 (a-z、A-z)、数字 (0-9)、ハイフン (‐) を含めることができます。
- 数字だけで名前を作ることはできません。
- 名前に空白を含めることはできません。
- %SERIAL% マクロを使用し、ハードウェア固有のシリアル番号を追加します。 または、%RAND:<# of digits>% マクロを使用してランダムな数値の文字列を追加します。文字列は <# of digits> 桁になります。 たとえば、MYPC-%RAND:6% では、MYPC-123456 などの名前が生成されます。

### <a name="something-went-wrong-oobeidps"></a>問題が発生しました。 OOBEIDPS。

**原因:** この問題は、ID プロバイダー (IdP) へのアクセスをブロックしているプロキシ、ファイアウォール、または他のネットワーク デバイスがある場合に発生します。

#### <a name="resolution"></a>解決策
Autopilot 用のインターネット ベースのサービスに対して必要なアクセスがブロックされていないことを確認します。 詳しくは、[Windows Autopilot ネットワークの要件](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-requirements-network)に関する記事を参照してください。


### <a name="registering-your-device-for-mobile-management-failed3-0x801c03ea"></a>モバイル管理用のデバイスの登録 (失敗: 3、0x801C03EA)。

**原因:** デバイスにはバージョン 2.0 をサポートする TPM チップが搭載されていますが、まだバージョン 2.0 にアップグレードされていません。

#### <a name="resolution"></a>解決策
TPM チップをバージョン 2.0 にアップグレードします。

問題が解決しない場合は、同じデバイスが 2 つのグループに割り当てられていて、各グループに異なる Autopilot プロファイルが割り当てられてないかどうか確認します。 2 つのグループに属している場合は、どちらの Autopilot プロファイルをデバイスに適用するかを決定し、他のプロファイルの割り当てを削除します。

Autopilot を使用してキオスク モードで Windows デバイスを展開する方法について詳しくは、「[Windows Autopilot を使用したキオスクの展開](https://blogs.technet.microsoft.com/mniehaus/2018/06/07/deploying-a-kiosk-using-windows-autopilot/)」を参照してください。


### <a name="securing-your-hardware-failed-0x800705b4"></a>ハードウェアのセキュリティ保護 (失敗: 0x800705b4)。

エラー 800705b4: 
```
Securing your hardware (Failed: 0x800705b4)
Joining your organization's network (Previous step failed)
Registering your device for mobile management (Previous step failed)
```

**原因:** 対象となる Windows デバイスが、次のいずれかの要件を満たしていません。

- デバイスに、TPM 2.0 物理チップが搭載されている必要があります。 仮想 TPM (Hyper-V VM など) または TPM 1.2 チップを使用するデバイスは、自己展開モードでは動作しません。
- デバイスで、次のいずれかのバージョンの Windows が実行されている必要があります。
    - Windows 10 ビルド 1703 以降のバージョン。
    - Hybrid Azure AD Join が使用されている場合は、Windows 10 ビルド 1809 以降のバージョン。


#### <a name="resolution"></a>解決策
対象デバイスが、「**原因**」セクションで説明されている両方の要件を満たしていることを確認します。

Autopilot を使用してキオスク モードで Windows デバイスを展開する方法について詳しくは、「[Windows Autopilot を使用したキオスクの展開](https://blogs.technet.microsoft.com/mniehaus/2018/06/07/deploying-a-kiosk-using-windows-autopilot/)」を参照してください。


### <a name="something-went-wrong-error-code-80070774"></a>問題が発生しました。 エラー コード 80070774。

エラー 0x80070774: 問題が発生しました。 正しいサインイン情報を使用し、組織でこの機能を使用していることを確認してください。 もう一度やり直すか、エラー コード 80070774 についてシステム管理者に問い合わせてください。

この問題が発生するのは、通常、デバイスが初期サインイン画面でタイムアウトし、Hybrid Azure AD Autopilot シナリオでデバイスが再起動される前です。 これは、ドメイン コントローラーが見つからないか、または接続の問題のためにドメイン コントローラーに正常にアクセスできないことを意味します。 または、デバイスがドメインに参加できない状態になっています。

**原因:** 最も一般的な原因は、Hybrid Azure AD Join が使用されていて、ユーザーの割り当て機能が Autopilot プロファイルで構成されていることです。 ユーザーの割り当て機能を使用すると、初期サインイン画面の間にデバイスで Azure AD Join が実行され、デバイスはオンプレミス ドメインに参加できない状態になります。 そのため、ユーザーの割り当て機能は、標準の Azure AD Join Autopilot シナリオでのみ使用してください。  この機能は、Hybrid Azure AD Join シナリオでは使用しないでください。

#### <a name="resolution"></a>解決策

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)で、**[デバイス]** > **[Windows]** > **[Windows デバイス]** を選択します。
2. 問題が発生しているデバイスを選択し、右端にある省略記号 [...] をクリックします。
3. **[ユーザーの割り当て解除]** を選択し、プロセスが終了するまで待ちます。
4. Hybrid Azure AD Autopilot プロファイルが割り当てられていることを確認してから、OOBE を再試行します。

#### <a name="second-resolution"></a>2 番目の解決策
問題が解決しない場合は、オフライン ドメイン参加 Intune コネクタがホストされているサーバーで、ODJ Connector サービス ログにイベント ID 30312 が記録されているかどうかを確認します。 イベント 30312 は次のようなものです。

```
Log Name:      ODJ Connector Service
Source:        ODJ Connector Service Source
Event ID:      30132
Level:         Error
Description:
{
          "Metric":{
                   "Dimensions":{
                             "RequestId":"<RequestId>",
                             "DeviceId":"<DeviceId>",
                             "DomainName":"contoso.com",
                             "ErrorCode":"5",
                             "RetryCount":"1",
                              "ErrorDescription":"Failed to get the ODJ Blob. The ODJ connector does not have sufficient privileges to complete the operation",
                              "InstanceId":"<InstanceId>",
                              "DiagnosticCode":"0x00000800",
                              "DiagnosticText":"Failed to get the ODJ Blob. The ODJ connector does not have sufficient privileges to complete the operation [Exception Message: \"DiagnosticException: 0x00000800. Failed to get the ODJ Blob. The ODJ connector does not have sufficient privileges to complete the operation\"] [Exception Message: \"Failed to call NetProvisionComputerAccount machineName=<ComputerName>\"]"
                   },
                   "Name":"RequestOfflineDomainJoinBlob_Failure",
                   "Value":0
          }
}
```

この問題は、通常、Windows Autopilot デバイスが作成される組織単位にアクセス許可を誤って委任することにより発生します。 詳しくは、「[組織単位でコンピューター アカウントの上限を増やす](windows-autopilot-hybrid.md#increase-the-computer-account-limit-in-the-organizational-unit)」を参照してください。

1. **[Active Directory ユーザーとコンピューター]** (DSA.msc) を開きます。
2. ハイブリッド Azure AD に参加しているコンピューターを作成するために使用する組織単位を右クリックして、**[制御の委任]** を選択します。
3. **制御の委任**ウィザードで、**[次へ]** > **[追加]** > **[オブジェクトの種類]** を選択します。
4. **[オブジェクトの種類]** ウィンドウで、**[コンピューター]** チェック ボックスをオンにして、**[OK]** を選択します。
5. **[ユーザー]**、**[コンピューター]**、または **[グループ]** のいずれかのウィンドウの **[選択するオブジェクト名を入力してください]** ボックスに、コネクタがインストールされている場所コンピューターの名前を入力します。
6. **名前の確認** を選択して入力を検証 > **OK** > **次へ**をクリックします。
7. **[委任するカスタム タスクを作成する]** > **[次へ]** を選択します。
8. **[フォルダー内の次のオブジェクトのみ]** チェック ボックスをオンにし、**[コンピューター オブジェクト]**、**[選択されたオブジェクトをこのフォルダーに作成する]**、および **[選択されたオブジェクトをこのフォルダーから削除する]** チェック ボックスをオンにします。
9. **[次へ]** を選択します。
10. **[アクセス許可]** で、**[フル コントロール]** チェック ボックスをオンにします。 この操作で、他のすべてのオプションが選択されます。
11. **[次へ]** > **[完了]** を選択します。

### <a name="the-enrollment-status-page-times-out-before-the-sign-in-screen"></a>サインイン画面の前に [登録ステータス] ページがタイムアウトする

**原因:** この問題は、次の条件がすべて該当した場合に、発生する可能性があります。
- [登録ステータス] ページを使用して、ビジネス向け Microsoft ストア アプリを追跡している。
- [デバイスは準拠としてマーク済みである必要があります] コントロールを使用する Azure AD 条件付きアクセス ポリシーがある。
- ポリシーがすべてのクラウド アプリと Windows に適用される。

#### <a name="resolution"></a>解決策:
次のどちらかを実行します。
- デバイスを Intune コンプライアンス ポリシーの対象にします。 ユーザーがログオンする前に、コンプライアンスを確認できることを確認します。
- ストア アプリに対してオフライン ライセンスを使用します。 これにより、Windows クライアントはデバイスのコンプライアンスを確認する前に、Microsoft Store をチェックする必要がなくなります。



## <a name="next-steps"></a>次のステップ

- [Intune のデバイス登録に関するトラブルシューティング](../troubleshoot-device-enrollment-in-intune.md)
- [Intune フォーラムで質問する](https://social.technet.microsoft.com/Forums/%7Blang-locale%7D/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)
- [Microsoft Intune サポート チームのブログを読む](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)
- [Microsoft Enterprise Mobility and Security チームのブログを読む](https://techcommunity.microsoft.com/t5/Azure-Active-Directory-Identity/Announcing-the-public-preview-of-Azure-AD-group-based-license/ba-p/245210)
- [Microsoft Intune のサポートを受ける](../fundamentals/get-support.md)
- [共同管理の登録エラーを調べる](https://docs.microsoft.com/configmgr/comanage/how-to-monitor#enrollment-errors)
