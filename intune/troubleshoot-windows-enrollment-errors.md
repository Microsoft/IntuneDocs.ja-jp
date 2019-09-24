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
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0f78f069f46ce036752fde80519abc03dc7c424c
ms.sourcegitcommit: 1494ff4b33c13a87f20e0f3315da79a3567db96e
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 09/20/2019
ms.locfileid: "71167778"
---
# <a name="troubleshoot-windows-device-enrollment-problems-in-microsoft-intune"></a>Microsoft Intune での Windows デバイスの登録に関する問題のトラブルシューティング

この記事は、intune 管理者が Windows デバイスを Intune に登録するときに発生する問題を理解し、トラブルシューティングするのに役立ちます。

## <a name="prerequisites"></a>必要条件
トラブルシューティングを開始する前に、いくつかの基本的な情報を収集することが重要です。 この情報は、問題の理解を深め、解決策を見つけるための時間を短縮するのに役立ちます。

問題に関する次の情報を収集します。
- 有効な Intune ライセンスがユーザーに割り当てられていますか? ユーザーは自分のデバイスを登録する前に、必要なライセンスが割り当てられている必要があります。
- Windows デバイスに最新の更新プログラムがインストールされているかどうか。 Intune の一部の機能は、最新バージョンの Windows でのみ動作します。 Windows Update では、既知の問題について多くの修正が行われています。 多くの場合、最新の更新プログラムをすべて適用すると、Windows デバイスの登録に関する問題が解決されます。 
- 正確なエラー メッセージは何ですか?
- エラー メッセージはどこに表示されますか?
- 問題が発生し始めたのはいつですか? 登録は成功しましたか? 
- どのプラットフォーム (Android、iOS、Windows) に問題がありますか。
- 影響を受けるユーザーの数を確認できます。 すべてのユーザーに影響があるのか、それともほんの一部であるか。
- 影響を受けるデバイスの数を確認できます。 すべてのデバイスが影響を受けていますか。
- MDM 機関とは System Center Configuration Manager ている場合は、どのバージョンの Configuration Manager を使用していますか。
- 登録はどのように実行されますか? 登録プロファイルを使用して "自分のデバイスを持ち込む" (BYOD) または Apple Device Enrollment Program (DEP) ですか。

## <a name="error-messages"></a>エラー メッセージ

### <a name="this-user-is-not-authorized-to-enroll"></a>このユーザーには登録を許可されていません。

エラー 0x801c003: "このユーザーの登録は許可されていません。 この操作をもう一度試すか、エラーコード (0x801c0003) を使用してシステム管理者に連絡してください。 "
エラー 80180003: "問題が発生しました。 このユーザーには登録を許可されていません。 この操作をもう一度試すか、エラーコード80180003を使用してシステム管理者に連絡してください。 "

**原因:** 次のいずれかの条件に該当します。 

- ユーザーは、Intune で許可されているデバイスの最大数を既に登録しています。    
- デバイスは、デバイスの種類の制限によってブロックされます。    
- コンピューターで Windows 10 Home が実行されている。 ただし、Intune への登録または Azure AD への参加は、Windows 10 Pro 以上のエディションでのみサポートされています。

#### <a name="resolution"></a>解決策
この問題には、いくつかの解決策が考えられます。

##### <a name="remove-devices-that-were-enrolled"></a>登録されたデバイスの削除
1. [Azure ポータル](https://portal.azure.com/?Microsoft_Intune=1&Microsoft_Intune_DeviceSettings=true&Microsoft_Intune_Enrollment=true&Microsoft_Intune_Apps=true&Microsoft_Intune_Devices=true#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade/overview)にサインインします。    
2. [**ユーザー** > ] **[すべてのユーザー]** にアクセスします。    
3. 影響を受けるユーザーアカウントを選択し、 **[デバイス]** をクリックします。    
4. 未使用または不要なデバイスを選択し、 **[削除]** をクリックします。 

##### <a name="increase-the-device-enrollment-limit"></a>デバイス登録制限の引き上げ

> [!NOTE]
> このメソッドは、影響を受けるユーザーだけでなく、すべてのユーザーのデバイス登録制限を増やします。

1. [Azure ポータル](https://portal.azure.com/?Microsoft_Intune=1&Microsoft_Intune_DeviceSettings=true&Microsoft_Intune_Enrollment=true&Microsoft_Intune_Apps=true&Microsoft_Intune_Devices=true#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade/overview)にサインインします。
2. [**デバイスの登録** > ] **[登録の制限]** にアクセスし、デバイスの **[制限]** の制限 を選択します。    
3. **デバイスの制限**値を増やす。 

##### <a name="check-device-type-restrictions"></a>デバイスの種類の制限を確認する
1. グローバル管理者アカウントで [Intune ポータル](https://portal.azure.com/?Microsoft_Intune=1&Microsoft_Intune_DeviceSettings=true&Microsoft_Intune_Enrollment=true&Microsoft_Intune_Apps=true&Microsoft_Intune_Devices=true#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade/overview)にサインインします。
2. [**デバイスの登録** > ] **[登録の制限]** にアクセスし、デバイスの **[種類の制限]** で**既定**の制限を選択します。    
3. **[プラットフォーム]** を選択し、[Windows に対して**許可** **(MDM)** ] を選択します。

    > [!IMPORTANT]
    > 現在の設定が既に**許可**されている場合は、 **[ブロック]** に変更し、設定を保存してから、 **[許可]** に戻して設定を再度保存します。 これにより、登録設定がリセットされます。

4. 約15分間待ってから、影響を受けたデバイスをもう一度登録します。    

##### <a name="upgrade-windows-10-home"></a>Windows 10 Home のアップグレード
[Windows 10 Home を windows 10 Pro](https://support.microsoft.com/help/12384/windows-10-upgrading-home-to-pro)またはそれ以降のエディションにアップグレードします。 



### <a name="this-user-is-not-allowed-to-enroll"></a>このユーザーの登録は許可されていません。

エラー 0x801c0003: "このユーザーの登録は許可されていません。 もう一度やり直すか、エラーコード801c0003 を使用してシステム管理者に連絡してください。 "

**原因:** [**ユーザーはデバイスを Azure AD に参加**させることができます] 設定は **[なし**] に設定されます。 これにより、新しいユーザーは自分のデバイスを Azure AD に参加させることができなくなります。 そのため、Intune の登録に失敗します。

#### <a name="resolution"></a>解決策
1. 管理者として [Azure portal](https://portal.azure.com/) にサインインします。    
2. **Azure Active Directory**  >  **デバイスの**  >  **デバイス設定**にアクセスします。    
3. **[ユーザーはデバイスを Azure AD に参加させることができます]** を **[すべて]** に設定します。    
4. デバイスを再登録します。   

### <a name="the-device-is-already-enrolled"></a>デバイスは既に登録されています。

エラー 8018000a: "問題が発生しました。 デバイスは既に登録されています。  エラーコード8018000a を使用して、システム管理者に連絡できます。 "

**原因:** 次のいずれかの条件に該当します。
- 別のユーザーが既にデバイスを Intune に登録しているか、デバイスを Azure AD に参加させています。 この状況に該当するかどうかを判断するには、[**設定** > ] [**アカウント** > ] **[職場のアクセス]** にアクセスします。 次のようなメッセージを探します。 "システム上の別のユーザーが既に職場または学校に接続されています。 職場または学校の接続を削除してから、もう一度お試しください。 "    
- Configuration Manager クライアントエージェントがコンピューターにインストールされています。    

#### <a name="resolution"></a>解決策

この問題を解決するには、次のいずれかの方法を使用します。

##### <a name="remove-the-other-work-or-school-account"></a>他の職場または学校アカウントを削除する
1. Windows からサインアウトし、デバイスに登録または参加したもう1つのアカウントを使用してサインインします。    
2. [**設定** > ] [**アカウント** > ] **[職場のアクセス]** の順に選択し、職場または学校のアカウントを削除します。
3. Windows からサインアウトし、アカウントを使用してサインインします。    
4. デバイスを Intune に登録するか、デバイスを Azure AD に参加させます。 

##### <a name="remove-the-configuration-manager-client"></a>Configuration Manager クライアントの削除
Configuration Manager クライアントを削除してから、デバイスをもう一度登録してください。



### <a name="this-account-is-not-allowed-on-this-phone"></a>このアカウントは、この電話では許可されていません。

エラー: "このアカウントはこの電話では許可されていません。 入力した情報が正しいことを確認してから、もう一度やり直すか、会社のサポートを依頼してください。 "

**原因:** デバイスを登録しようとしたユーザーには、有効な Intune ライセンスがありません。

#### <a name="resolution"></a>解決策
有効な Intune ライセンスをユーザーに割り当て、デバイスを登録します。


### <a name="looks-like-the-mdm-terms-of-use-endpoint-is-not-correctly-configured"></a>MDM 使用条件エンドポイントが正しく構成されていない可能性があります。

**原因:** 次のいずれかの条件に該当します。 
 - Office 365 用のモバイルデバイス管理 (MDM) とテナントの Intune の両方を使用します。デバイスを登録しようとするユーザーには、有効な Intune ライセンスまたは Office 365 ライセンスがありません。     
- Azure AD の MDM 使用条件が空白であるか、正しい URL が含まれていません。    

#### <a name="resolution"></a>解決策

この問題を解決するには、次のいずれかの方法を使用します。 
 
##### <a name="assign-a-valid-license-to-the-user"></a>ユーザーに有効なライセンスを割り当てる
[Microsoft 365 管理センター](https://portal.office.com/adminportal/home)にアクセスし、Intune または Office 365 のライセンスをユーザーに割り当てます。

##### <a name="correct-the-mdm-terms-of-use-url"></a>MDM 使用条件 URL を修正する
  1. [Azure portal](https://portal.azure.com/) にサインインしてから、 **[Azure Active Directory]** を選択します。    
  2. **[モビリティ (MDM および MAM)]** を選択し、 **[Microsoft Intune]** をクリックします。    
  3. **[既定の Mdm url の復元]** を選択し、 **MDM 使用条件 url**が **https://portal.manage.microsoft.com/TermsofUse.aspx** に設定されていることを確認します。    
  4. **[保存]** を選びます。    


### <a name="something-went-wrong"></a>問題が発生しました。

エラー 80180026: "問題が発生しました。 正しいサインイン情報が使用されていること、および組織がこの機能を使用していることを確認します。 この操作をもう一度試すか、エラーコード80180026を使用してシステム管理者に連絡してください。 "

**原因:** このエラーは、Windows 10 コンピューターを Azure AD に参加させようとしたときに、次の両方の条件が当てはまる場合に発生する可能性があります。 
- MDM の自動登録は Azure で有効になっています。    
- Windows 10 コンピューターに、Intune PC クライアント (Intune PC エージェント) または Configuration Manager クライアントエージェントがインストールされている。

#### <a name="resolution"></a>解決策
この問題に対処するには、次のいずれかの方法を使用します。

##### <a name="disable-mdm-automatic-enrollment-in-azure"></a>Azure での MDM 自動登録を無効にします。
1. [Azure ポータル](https://portal.azure.com/)にサインインします。    
2.  >  **Azure Active Directory** > **モビリティ (MDM および MAM)** **Microsoft Intune**に移動します。    
3. **[MDM ユーザースコープ]** を **[なし]** に設定し、 **[保存]** をクリックします。    
     
##### <a name="uninstall"></a>アンインストール
コンピューターから Intune PC クライアントまたは Configuration Manager クライアントエージェントをアンインストールします。    

### <a name="the-software-cannot-be-installed"></a>ソフトウェアをインストールできません。

エラー: "ソフトウェアをインストールできません。 0x80cf4017"

**原因:** クライアントソフトウェアが最新ではありません。

#### <a name="resolution"></a>解決策
1. [https://admin.manage.microsoft.com](https://admin.manage.microsoft.com) にサインインします。    
2. [**管理** > **クライアントソフトウェアのダウンロード**] にアクセスし、 **[クライアントソフトウェアのダウンロード]** をクリックします。    
3. インストールパッケージを保存してから、クライアントソフトウェアをインストールします。 


### <a name="the-account-certificate-is-not-valid-and-may-be-expired"></a>アカウント証明書が無効です。期限が切れている可能性があります。[2]。

エラー: "アカウント証明書が無効です。期限が切れている可能性があります。0x80cf4017。"

**原因:** クライアントソフトウェアが最新ではありません。

#### <a name="resolution"></a>解決策
1. [https://admin.manage.microsoft.com](https://admin.manage.microsoft.com) にサインインします。    
2. [**管理** > **クライアントソフトウェアのダウンロード**] にアクセスし、 **[クライアントソフトウェアのダウンロード]** をクリックします。    
3. インストールパッケージを保存してから、クライアントソフトウェアをインストールします。    

### <a name="your-organization-does-not-support-this-version-of-windows"></a>組織では、このバージョンの Windows はサポートされていません。 

エラー: "問題が発生しました。 組織では、このバージョンの Windows はサポートされていません。  (0x80180014) "

**原因:** Intune テナントで Windows MDM の登録が無効になっています。

#### <a name="resolution"></a>解決策
スタンドアロンの Intune 環境でこの問題を解決するには、次の手順を実行します。 
 
1. 管理者として [Azure portal](https://portal.azure.com/) にサインインします。    
2. 左側の **[Intune]** を選択し、[**デバイスの登録** > ] **[登録の制限]** に移動します。    
3. **[デバイスの種類の制限]** で、 **[プラットフォーム]** をクリックし、[Windows に対して**許可** **(MDM)** ] を選択します。    
4. **[Save]** (保存) をクリックします。    
 
Intune と Configuration Manager のハイブリッド MDM でこの問題を解決するには、次の手順を実行します。 
1. Configuration Manager コンソールを開きます。    
2. **[管理]** を選択し、 **[Cloud Services]** を選択します。    
3. **[Microsoft Intune サブスクリプション]** を右クリックし、 **[プラットフォーム > Windows の構成]** を選択します。    
4. **[** **Windows 登録** > を有効にする **]** チェックボックスをオンにし > ます。  


### <a name="a-setup-failure-has-occurred-during-bulk-enrollment"></a>一括登録中にセットアップエラーが発生しました。

**原因:** 各プロビジョニングパッケージのアカウントパッケージ (Package_GUID) の Azure AD ユーザーアカウントは、デバイスを Azure AD に参加させることはできません。 これらの Azure AD アカウントは、Windows 構成デザイナー (WCD) またはセットアップ School Pc アプリを使用してプロビジョニングパッケージを設定するときに自動的に作成されます。これらのアカウントは、デバイスを Azure AD に参加させるために使用されます。

#### <a name="resolution"></a>解決策
1. 管理者として [Azure portal](https://portal.azure.com/) にサインインします。    
2. **Azure Active Directory > デバイス > デバイス設定** にアクセスします。    
3. **[ユーザーはデバイスを Azure AD に参加させることができます]** を **[すべて]** または **[選択済み]** に設定します。

   **[選択]** 済み を選択した場合は、 **[選択済み]** をクリックし、 **[メンバーの追加]** をクリックして、Azure AD にデバイスを参加させることができるすべてのユーザーを追加します。 プロビジョニングパッケージの Azure AD アカウントがすべて追加されていることを確認します。
 
Windows 構成デザイナーのプロビジョニングパッケージを作成する方法の詳細については、「 [windows 10 用のプロビジョニングパッケージを作成](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-create-package)する」を参照してください。

School Pc のセットアップアプリの詳細については、「 [School pc アプリのセットアップ](https://docs.microsoft.com/education/windows/use-set-up-school-pcs-app)」を参照してください。


### <a name="auto-mdm-enroll-failed"></a>MDM の自動登録: 失敗 

グループポリシーを使用して Windows 10 デバイスを自動的に登録しようとすると、次の問題が発生します。 
- タスクスケジューラの [ **Microsoft** > **Windows** > **EnterpriseMgmt**] では、**登録クライアントによって作成されたスケジュールの最後の実行結果が AAD から MDM に自動的に登録**されるようになりました。次に例を示します。**イベント76自動 MDM 登録: 失敗しました (不明な Win32 エラーコード: 0x8018002b)**       
- イベントビューアーでは、[**アプリケーションとサービスログ]/[Microsoft]/[Windows]/[デバイス/Admin**] の下に次のイベントが記録されます。   
    ```asciidoc
    Log Name: Microsoft-Windows-DeviceManagement-Enterprise-Diagnostics-Provider/Admin
    Source: DeviceManagement-Enterprise-Diagnostics-Provider
    Event ID: 76
    Level: Error
    Description: Auto MDM Enroll: Failed (Unknown Win32 Error code: 0x80180002b)
    ```
**原因:** 次のいずれかの条件に該当します。 
- UPN に、未確認またはルーティング不可能なドメイン ( joe@contoso.localなど) が含まれています。    
- **MDM ユーザースコープ**が**None**に設定されています。 

#### <a name="resolution"></a>解決策
UPN に検証されていないドメインまたはルーティング不可能なドメインが含まれている場合は、次の手順を実行します。 

1. Active Directory Domain Services (AD DS) が実行されているサーバーで、[ファイル名を指定して**実行**] ダイアログボックスに **「** **dsa.msc** 」と入力して**Active Directory ユーザーとコンピューター**を開き、[OK] をクリックします。    
2. ドメインの下にある **[ユーザー]** をクリックし、次の操作を行います。  
    - 影響を受けるユーザーが1人だけの場合は、そのユーザーを右クリックし、 **[プロパティ]** をクリックします。 **アカウント** タブの **ユーザーログオン名** の下にある upn サフィックス ドロップダウンリストで、contoso.com などの有効な upn サフィックスを選択し、 **OK**をクリックします。    
    - 影響を受けるユーザーが複数ある場合は、ユーザーを選択し、 **[操作]** メニューの **[プロパティ]** をクリックします。 **[アカウント]** タブで、 **[UPN サフィックス]** チェックボックスをオンにし、ドロップダウンリストで有効な upn サフィックス (contoso.com など) を選択して、 **[OK]** をクリックします。
3. 管理者特権の PowerShell プロンプトで次のコマンドを実行して、次の同期を待つか、同期サーバーから差分同期を強制実行します。
    ```powershell
    Import-Module ADSync
    Start-ADSyncSyncCycle -PolicyType Delta
    ```

**[MDM ユーザースコープ]** が **[なし**] に設定されている場合は、次の手順を実行します。 
 
1. [Azure portal](https://portal.azure.com/) にサインインしてから、 **[Azure Active Directory]** を選択します。
2. **[モビリティ (MDM および MAM)]** を選択し、 **[Microsoft Intune]** を選択します。    
3. **MDM ユーザースコープ**を**All**に設定します。 または、 **[MDM ユーザースコープ]** を **[一部]** に設定し、Windows 10 デバイスを自動的に登録できるグループを選択します。    
4. **[MAM ユーザースコープ]** を **[なし**] に設定します。


### <a name="an-error-occurred-while-creating-autopilot-profile"></a>自動操縦プロファイルの作成中にエラーが発生しました。

**原因:** デバイス名テンプレートの指定された名前付け形式が要件を満たしていません。 たとえば、シリアルマクロには小文字 (% serial% ではなく% serial% など) を使用します。

#### <a name="resolution"></a>解決策

名前付け形式が次の要件を満たしていることを確認します。

- デバイスの一意の名前を作成します。 名前は 15 文字以下にする必要があります。また、文字 (a-z、A-z)、数字 (0-9)、ハイフン (‐) を含めることができます。
- 数字だけで名前を作ることはできません。
- 名前に空白を含めることはできません。
- %SERIAL% マクロを使用し、ハードウェア固有のシリアル番号を追加します。 または、% RAND: < # of digits >% マクロを使用してランダムな数値の文字列を追加します。文字列には < > 桁の数字が含まれています。 たとえば、MYPC-% RAND: 6% は、MYPC-123456 のような名前を生成します。

### <a name="something-went-wrong-oobeidps"></a>問題が発生しました。 OOBEIDPS.

**原因:** この問題は、Id プロバイダー (IdP) へのアクセスをブロックしているプロキシ、ファイアウォール、またはその他のネットワークデバイスがある場合に発生します。

#### <a name="resolution"></a>解決策
自動操縦用インターネットベースのサービスへの必要なアクセスがブロックされていないことを確認します。 詳細については、「 [Windows 自動操縦ネットワークの要件](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-requirements-network)」を参照してください。


### <a name="registering-your-device-for-mobile-management-failed3-0x801c03ea"></a>モバイル管理用にデバイスを登録しています (失敗: 3、0x801C03EA)。

**原因:** デバイスは、バージョン2.0 をサポートする TPM チップを搭載していますが、バージョン2.0 にアップグレードされていません。

#### <a name="resolution"></a>解決策
TPM チップをバージョン2.0 にアップグレードします。

問題が解決しない場合は、同じデバイスが2つのグループに割り当てられているかどうかを確認し、各グループには異なる自動操縦プロファイルが割り当てられていることを確認します。 2つのグループに属する場合は、デバイスに適用する自動操縦プロファイルを決定し、その他のプロファイルの割り当てを削除します。

自動操縦を使用してキオスクモードで Windows デバイスを展開する方法の詳細については、「 [Windows 自動操縦を使用したキオスクの展開](https://blogs.technet.microsoft.com/mniehaus/2018/06/07/deploying-a-kiosk-using-windows-autopilot/)」を参照してください。


### <a name="securing-your-hardware-failed-0x800705b4"></a>ハードウェアをセキュリティで保護する (Failed: 0x800705b4)。

エラー 800705b4: 
```
Securing your hardware (Failed: 0x800705b4)
Joining your organization's network (Previous step failed)
Registering your device for mobile management (Previous step failed)
```

**原因:** 対象となる Windows デバイスが、次のいずれかの要件を満たしていません。

- デバイスは、物理的な TPM 2.0 チップを搭載している必要があります。 Virtual Tpm (Hyper-v Vm など) または TPM 1.2 チップを持つデバイスは、自己展開モードでは動作しません。
- デバイスは、次のいずれかのバージョンの Windows を実行している必要があります。
    - Windows 10 ビルド1703以降のバージョン。
    - Hybrid Azure AD Join が使用されている場合、Windows 10 ビルド1809以降のバージョン。


#### <a name="resolution"></a>解決策
ターゲットデバイスが、「**原因**」セクションで説明されている両方の要件を満たしていることを確認します。

自動操縦を使用してキオスクモードで Windows デバイスを展開する方法の詳細については、「 [Windows 自動操縦を使用したキオスクの展開](https://blogs.technet.microsoft.com/mniehaus/2018/06/07/deploying-a-kiosk-using-windows-autopilot/)」を参照してください。


### <a name="something-went-wrong-error-code-80070774"></a>問題が発生しました。 エラー コード 80070774。

エラー 0x80070774: 問題が発生しました。 正しいサインイン情報が使用されていること、および組織がこの機能を使用していることを確認します。 この操作をもう一度実行するか、エラーコード80070774を使用してシステム管理者に連絡してください。

この問題が発生するのは、通常、デバイスが初期サインイン画面でタイムアウトしたときに、Hybrid Azure AD の再起動シナリオでデバイスが再起動される前です。 これは、接続の問題のためにドメインコントローラが見つからないか、正常に到達できないことを意味します。 または、デバイスがドメインに参加できない状態になりました。

**原因:** 最も一般的な原因は、Hybrid Azure AD Join が使用されていて、ユーザーの割り当て機能が自動操縦プロファイルで構成されていることです。 ユーザーの割り当て機能を使用すると、初期サインイン画面中にデバイスで Azure AD 結合が実行され、デバイスがオンプレミスドメインに参加できない状態になります。 そのため、ユーザーの割り当て機能は、標準 Azure AD 参加の自動操縦のシナリオでのみ使用してください。  この機能は Hybrid Azure AD Join シナリオでは使用しないようにしてください。

#### <a name="resolution"></a>解決策

1. [ **Intune** >  ] [**デバイスの登録** > ] [**Windows の登録** > ] **[デバイス]** にアクセスします。
2. 問題が発生しているデバイスを選択し > 右端にある省略記号 ([...]) をクリックします。
3. **[ユーザーの割り当て解除]** を選択し、プロセスが終了するまで待ちます。
4. OOBE を再試行する前に、Hybrid Azure AD の自動操縦プロファイルが割り当てられていることを確認してください。

#### <a name="second-resolution"></a>2番目の解決方法
問題が引き続き発生する場合は、Offline Domain Join Intune コネクタをホストするサーバーで、ODJ Connector サービスログ内にイベント ID 30312 が記録されているかどうかを確認します。 イベント30312は次のようになります。

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

この問題は、通常、Windows 自動操縦デバイスが作成される組織単位にアクセス許可を委任することによって発生します。 詳細については、「[組織単位でのコンピューターアカウントの制限の引き上げ](windows-autopilot-hybrid.md#increase-the-computer-account-limit-in-the-organizational-unit)」を参照してください。

1. **[Active Directory ユーザーとコンピューター]** (DSA.msc) を開きます。
2. ハイブリッド Azure AD に参加しているコンピューターを作成するために使用する組織単位を右クリックして、 **[制御の委任]** を選択します。
3. **制御の委任**ウィザードで、 **[次へ]**  >  **[追加]**  >  **[オブジェクトの種類]** を選択します。
4. **[オブジェクトの種類]** ウィンドウで、 **[コンピューター]** チェック ボックスをオンにして、 **[OK]** を選択します。
5. **[ユーザー]** 、 **[コンピューター]** 、または **[グループ]** のいずれかのウィンドウの **[選択するオブジェクト名を入力してください]** ボックスに、コネクタがインストールされている場所コンピューターの名前を入力します。
6. **名前の確認** を選択して入力を検証 > **OK** > をクリック**します。**
7. **[委任するカスタム タスクを作成する]**  >  **[次へ]** を選択します。
8. **[フォルダー内の次のオブジェクトのみ]** チェック ボックスをオンにし、 **[コンピューター オブジェクト]** 、 **[選択されたオブジェクトをこのフォルダーに作成する]** 、および **[選択されたオブジェクトをこのフォルダーから削除する]** チェック ボックスをオンにします。
9. **[次へ]** を選択します。
10. **[アクセス許可]** で、 **[フル コントロール]** チェック ボックスをオンにします。 この操作で、他のすべてのオプションが選択されます。
11. [**次** > の**完了**] を選択します。

## <a name="next-steps"></a>次の手順

- [Intune のデバイス登録に関するトラブルシューティング](troubleshoot-device-enrollment-in-intune.md)
- [Intune フォーラムで質問する](https://social.technet.microsoft.com/Forums/%7Blang-locale%7D/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)
- [Microsoft Intune サポートチームのブログを確認する](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)
- [Microsoft Enterprise Mobility and Security のブログを確認する](https://techcommunity.microsoft.com/t5/Azure-Active-Directory-Identity/Announcing-the-public-preview-of-Azure-AD-group-based-license/ba-p/245210)
- [Microsoft Intune のサポートを受ける](get-support.md)
