---
title: Microsoft Intune でデバイスを構成するための Graph Api-Azure |Microsoft Docs
titleSuffix: ''
description: Microsoft Intune でデバイスを構成するときに使用される Windows 10 デバイス上の Windows CSP とオフセット URI が一致するすべての Graph API エンティティの一覧を表示します。 共有 Pc の照合 API と CSP、endpoint protection、Microsoft Defender advanced threat protection、identity protection、Windows 10 Teams、キオスク、Windows Update for Business をご覧ください。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/04/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9db6be9c61455056f7ad32a9dba3fa6be9f6f5c3
ms.sourcegitcommit: 614c4c36cfe544569db998e17e29feeaefbb7a2e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68427281"
---
# <a name="graph-apis-and-matching-windows-10-csps-used-in-intune"></a>Intune で使用される Graph Api と照合 Windows 10 Csp

Microsoft Intune は、 [Graph API エンティティ](https://docs.microsoft.com/graph/api/resources/intune-graph-overview)(別の Docs サイトを開きます) を使用して、Windows 10 以降を実行しているデバイス (**Intune** > **デバイス構成**) を構成します。 Graph API は、構成サービスプロバイダー (Csp) を使用して、デバイスの構成設定の読み取り、設定、変更、削除を行います。

この一覧の適用対象:

- Windows 10 以降

この記事では、グラフエンティティと、それに対応する Windows 10 Csp およびオフセット Uri の一覧を示します。

この情報は、さまざまなシナリオで役立ちます。 たとえば、「Intune で使用されるもの」、「カスタム OMA-URI 構成に含める設定」を参照してください。 

## <a name="windows-10-csps"></a>Windows 10 Csp

Windows 10 構成サービスプロバイダーの詳細については、[構成サービスプロバイダーのリファレンス](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference)(別のドキュメントサイトを開きます) を参照してください。

## <a name="graph-api-properties-to-csp-mapping"></a>CSP マッピングへのプロパティの Graph API

次の一覧は、Windows 10 デバイス構成の Microsoft Intune で使用される Graph API エンティティの大部分を示しています。 また、対応する Windows 10 CSP とオフセット URI も表示されます。

Windows 10 のバージョンを確認するには、次の Api が適用されます。 Windows 10[構成サービスプロバイダーのリファレンス](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference)を使用してください (別の Docs サイトを開きます)。

### <a name="editionupgradeconfigurationlicense"></a>EditionUpgradeConfiguration 
**CSP**: ./Device/Vendor/MSFT/WindowsLicensing  
**オフセット URI**:/UpgradeEditionWithLicense

### <a name="editionupgradeconfigurationlicensetype"></a>EditionUpgradeConfiguration の種類 
**CSP**: ./Device/Vendor/MSFT/WindowsLicensing  
**オフセット URI**:/licensekeytype

### <a name="editionupgradeconfigurationproductkey"></a>EditionUpgradeConfiguration ProductKey 
**CSP**: ./Device/Vendor/MSFT/WindowsLicensing  
**オフセット URI**:/UpgradeEditionWithProductKey

### <a name="editionupgradeconfigurationwindowssmode"></a>EditionUpgradeConfiguration. WindowsSMode 
**CSP**: ./Device/Vendor/MSFT/WindowsLicensing  
**オフセット URI**:/SMode/SwitchingPolicy

### <a name="sharedpcconfigurationaccountmanagerpolicy"></a>SharedPCConfiguration.AccountManagerPolicy 
**CSP**:./Vendor/MSFT/SharedPC  
**オフセット URI**:/DeletionPolicy、/disklevelcache、/InactiveThreshold、/diskleveldelete

### <a name="sharedpcconfigurationaccountmanagerpolicy-windows-holographic-for-business-edition-targeted-devices"></a>SharedPCConfiguration. AccountManagerPolicy (Windows Holographic for Business edition ターゲットデバイス) 
**CSP**:./Vendor/MSFT/AccountManagement  
**オフセット URI**:/DeletionPolicy、/storagecapacitystartdelete、/dns、/dns しきい値、/profileinactivitythreshold

### <a name="sharedpcconfigurationallowedaccounts"></a>SharedPCConfiguration. AllowedAccounts 
**CSP**:./Vendor/MSFT/SharedPC  
**オフセット URI**:/accountmodel

### <a name="sharedpcconfigurationallowlocalstorage"></a>SharedPCConfiguration。 AllowLocalStorage 
**CSP**:./Vendor/MSFT/SharedPC  
**オフセット URI**:/RestrictLocalStorage

### <a name="sharedpcconfigurationdisableaccountmanager"></a>SharedPCConfiguration. DisableAccountManager 
**CSP**:./Vendor/MSFT/SharedPC  
**オフセット URI**:/enableaccountmanager

### <a name="sharedpcconfigurationdisableedupolicies"></a>SharedPCConfiguration. DisableEduPolicies 
**CSP**:./Vendor/MSFT/SharedPC  
**オフセット URI**:/SetEduPolicies

### <a name="sharedpcconfigurationdisablepowerpolicies"></a>SharedPCConfiguration. DisablePowerPolicies 
**CSP**:./Vendor/MSFT/SharedPC  
**オフセット URI**:/SetPowerPolicies

### <a name="sharedpcconfigurationdisablesigninonresume"></a>SharedPCConfiguration. DisableSignInOnResume 
**CSP**:./Vendor/MSFT/SharedPC  
**オフセット URI**:/SignInOnResume

### <a name="sharedpcconfigurationenabled"></a>SharedPCConfiguration。有効 
**CSP**:./Vendor/MSFT/SharedPC  
**オフセット URI**:/EnableSharedPCMode

### <a name="sharedpcconfigurationidletimebeforesleepinseconds"></a>SharedPCConfiguration. IdleTimeBeforeSleepInSeconds 
**CSP**:./Vendor/MSFT/SharedPC  
**オフセット URI**:/InactiveThreshold

### <a name="sharedpcconfigurationkioskappdisplayname"></a>SharedPCConfiguration. KioskAppDisplayName 
**CSP**:./Vendor/MSFT/SharedPC  
**オフセット URI**:/KioskModeUserTileDisplayText

### <a name="sharedpcconfigurationkioskappusermodelid"></a>SharedPCConfiguration. KioskAppUserModelId 
**CSP**:./Vendor/MSFT/SharedPC  
**オフセット URI**:/KioskModeAUMID

### <a name="sharedpcconfigurationlocalstorage"></a>SharedPCConfiguration. LocalStorage 
**CSP**:./Vendor/MSFT/SharedPC  
**オフセット URI**:/RestrictLocalStorage

### <a name="sharedpcconfigurationmaintenancestarttime"></a>SharedPCConfiguration.MaintenanceStartTime 
**CSP**:./Vendor/MSFT/SharedPC  
**オフセット URI**:/MaintenanceStartTime

### <a name="sharedpcconfigurationsetaccountmanager"></a>SharedPCConfiguration. SetAccountManager
**CSP**:./Vendor/MSFT/SharedPC  
**オフセット URI**:/enableaccountmanager

### <a name="sharedpcconfigurationsetedupolicies"></a>SharedPCConfiguration. SetEduPolicies 
**CSP**:./Vendor/MSFT/SharedPC  
**オフセット URI**:/SetEduPolicies

### <a name="sharedpcconfigurationsetpowerpolicies"></a>SharedPCConfiguration. SetPowerPolicies 
**CSP**:./Vendor/MSFT/SharedPC  
**オフセット URI**:/SetPowerPolicies

### <a name="sharedpcconfigurationsigninonresume"></a>SharedPCConfiguration. SignInOnResume 
**CSP**:./Vendor/MSFT/SharedPC  
**オフセット URI**:/SignInOnResume

### <a name="windows10endpointconfigurationsmartscreenblockoverrideforfiles"></a>Windows10endpointconfiguration.smartScreenBlockOverrideForFiles 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/SmartScreen/PreventOverrideForFilesInShell

### <a name="windows10endpointprotectionconfigurationapplicationguardallowfilesaveonhost"></a>Windows10EndpointProtectionConfiguration.ApplicationGuardAllowFileSaveOnHost 
**CSP**: ./Device/Vendor/MSFT/WindowsDefenderApplicationGuard  
**オフセット URI**:/Settings/SaveFilesToHost

### <a name="windows10endpointprotectionconfigurationapplicationguardallowpersistence"></a>Windows10EndpointProtectionConfiguration の保存 
**CSP**: ./Device/Vendor/MSFT/WindowsDefenderApplicationGuard  
**オフセット URI**:/Settings/allowpersistence

### <a name="windows10endpointprotectionconfigurationapplicationguardallowprinttolocalprinters"></a>Windows10EndpointProtectionConfiguration. Applicationguの Allowprinttolocalprinters 
**CSP**: ./Device/Vendor/MSFT/WindowsDefenderApplicationGuard  
**オフセット URI**:/設定

### <a name="windows10endpointprotectionconfigurationapplicationguardallowprinttonetworkprinters"></a>Windows10EndpointProtectionConfiguration.ApplicationGuardAllowPrintToNetworkPrinters 
**CSP**: ./Device/Vendor/MSFT/WindowsDefenderApplicationGuard  
**オフセット URI**:/設定

### <a name="windows10endpointprotectionconfigurationapplicationguardallowprinttopdf"></a>Windows10EndpointProtectionConfiguration. Applicationgu/Allowprinttopdf 
**CSP**: ./Device/Vendor/MSFT/WindowsDefenderApplicationGuard  
**オフセット URI**:/設定

### <a name="windows10endpointprotectionconfigurationapplicationguardallowprinttoxps"></a>Windows10EndpointProtectionConfiguration (アプリケーションの構築) 
**CSP**: ./Device/Vendor/MSFT/WindowsDefenderApplicationGuard  
**オフセット URI**:/設定

### <a name="windows10endpointprotectionconfigurationapplicationguardallowvirtualgpu"></a>Windows10EndpointProtectionConfiguration.ApplicationGuardAllowVirtualGPU 
**CSP**: ./Device/Vendor/MSFT/WindowsDefenderApplicationGuard  
**オフセット URI**:/Settings/AllowVirtualGPU

### <a name="windows10endpointprotectionconfigurationapplicationguardblockclipboardsharing"></a>Windows10EndpointProtectionConfiguration クリップボードの共有 
**CSP**: ./Device/Vendor/MSFT/WindowsDefenderApplicationGuard  
**オフセット URI**:/設定/クリップボードの設定

### <a name="windows10endpointprotectionconfigurationapplicationguardblockfiletransfer"></a>Windows10EndpointProtectionConfiguration のファイル転送 
**CSP**: ./Device/Vendor/MSFT/WindowsDefenderApplicationGuard  
**オフセット URI**:/またはクリップボードの filetype

### <a name="windows10endpointprotectionconfigurationapplicationguardblocknonenterprisecontent"></a>Windows10EndpointProtectionConfiguration.ApplicationGuardBlockNonEnterpriseContent 
**CSP**: ./Device/Vendor/MSFT/WindowsDefenderApplicationGuard  
**オフセット URI**:/Settings/BlockNonEnterpriseContent

### <a name="windows10endpointprotectionconfigurationapplicationguardenabled"></a>Windows10EndpointProtectionConfiguration を有効にします。 
**CSP**: ./Device/Vendor/MSFT/WindowsDefenderApplicationGuard  
**オフセット URI**:/Settings/allowwindowsdefenderapplicationguard

### <a name="windows10endpointprotectionconfigurationapplicationguardforceauditing"></a>Windows10EndpointProtectionConfiguration の監査 
**CSP**: ./Device/Vendor/MSFT/WindowsDefenderApplicationGuard  
**オフセット URI**:/Audit/auditapplicationguard

### <a name="windows10endpointprotectionconfigurationbitlockerallowstandarduserencryption"></a>Windows10EndpointProtectionConfiguration. Bitkerallowstandarduserencryption 
**CSP**: ./Device/Vendor/MSFT/BitLocker  
**オフセット URI**:/allowstandarduserencryption

### <a name="windows10endpointprotectionconfigurationbitlockerdisablewarningforotherdiskencryption"></a>Windows10EndpointProtectionConfiguration-Otherdiskencryption の警告 
**CSP**: ./Device/Vendor/MSFT/BitLocker  
**オフセット URI**:/allowwarnings forotherdiskencryption

### <a name="windows10endpointprotectionconfigurationbitlockerenablestoragecardencryptiononmobile"></a>Windows10EndpointProtectionConfiguration. Bitkerenablestoragecencryptionencryptiononmobile 
**CSP**: ./Device/Vendor/MSFT/BitLocker  
**オフセット URI**:/requirestoragecシャード暗号化

### <a name="windows10endpointprotectionconfigurationbitlockerencryptdevice"></a>Windows10EndpointProtectionConfiguration.BitLockerEncryptDevice 
**CSP**: ./Device/Vendor/MSFT/BitLocker  
**オフセット URI**:/requiredeviceencryption

### <a name="windows10endpointprotectionconfigurationbitlockerfixeddrivepolicy"></a>Windows10EndpointProtectionConfiguration のドライブポリシー 
**CSP**: ./Device/Vendor/MSFT/BitLocker  
**オフセット URI**:/encryptionmethodbydrivetype、/fixedjobs requireencryption、/fixedjobs recoveryoptions

### <a name="windows10endpointprotectionconfigurationbitlockerremovabledrivepolicy"></a>Windows10EndpointProtectionConfiguration. Bitkerremovablefile ポリシー 
**CSP**: ./Device/Vendor/MSFT/BitLocker  
**オフセット URI**:/encryptionmethodbydrivetype、/RemovableDrivesRequireEncryption

### <a name="windows10endpointprotectionconfigurationbitlockersystemdrivepolicy"></a>Windows10EndpointProtectionConfiguration のシステムドライブポリシー 
**CSP**: ./Device/Vendor/MSFT/BitLocker  
**オフセット URI**:/encryptionmethodbydrivetype、/systemjobs requirestartupauthentication、/systemjobs minimumpinlength、/systemjobs recoverymessage、/systemjobs recoveryoptions

### <a name="windows10endpointprotectionconfigurationclientconnectionencryptionlevel"></a>windows10endpointprotectionconfiguration.clientConnectionEncryptionLevel 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/RemoteDesktopServices/ClientConnectionEncryptionLevel

### <a name="windows10endpointprotectionconfigurationconfiguresmbv1clientdriver"></a>windows10endpointprotectionconfiguration.configureSMBV1ClientDriver 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/MSSecurityGuide/ConfigureSMBV1ClientDriver

### <a name="windows10endpointprotectionconfigurationconnectivitydownloadingofprintdriversoverhttp"></a>Windows10EndpointProtectionConfiguration.ConnectivityDownloadingOfPrintDriversOverHttp 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Connectivity/DisableDownloadingOfPrintDriversOverHTTP

### <a name="windows10endpointprotectionconfigurationconnectivityhardeneduncpaths"></a>Windows10EndpointProtectionConfiguration.ConnectivityHardenedUncPaths 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Connectivity/HardenedUNCPaths

### <a name="windows10endpointprotectionconfigurationconnectivityinternetdownloadforwebpublishingandonlineorderingwizards"></a>Windows10EndpointProtectionConfiguration.ConnectivityInternetDownloadForWebPublishingAndOnlineOrderingWizards 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Connectivity/DisableInternetDownloadForWebPublishingAndOnlineOrderingWizards

### <a name="windows10endpointprotectionconfigurationconnectivityprintingoverhttp"></a>Windows10EndpointProtectionConfiguration.ConnectivityPrintingOverHttp 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Connectivity/DiablePrintingOverHTTP

### <a name="windows10endpointprotectionconfigurationcredentialsuienumerateadministrators"></a>Windows10EndpointProtectionConfiguration.CredentialsUIEnumerateAdministrators 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/CredentialsUI/EnumerateAdministrators

### <a name="windows10endpointprotectionconfigurationdefenderadditionalguardedfolders"></a>Windows10EndpointProtectionConfiguration.DefenderAdditionalGuardedFolders 
**CSP**:./DEVICE/VENDOR/MSFT/POLICY **Offset URI**:/Config/Defender/ControlledFolderAccessProtectedFolders

### <a name="windows10endpointprotectionconfigurationdefenderadvancedransomewareprotectiontype"></a>Windows10EndpointProtectionConfiguration.DefenderAdvancedRansomewareProtectionType 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Defender/AttackSurfaceReductionRules

### <a name="windows10endpointprotectionconfigurationdefenderattacksurfacereductionexcludedpaths"></a>Windows10EndpointProtectionConfiguration.DefenderAttackSurfaceReductionExcludedPaths 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Defender/AttackSurfaceReductionOnlyExclusions

### <a name="windows10endpointprotectionconfigurationdefenderemailcontentexecution"></a>Windows10EndpointProtectionConfiguration を実行します。 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/defenderscanning

### <a name="windows10endpointprotectionconfigurationdefenderemailcontentexecutiontype"></a>Windows10EndpointProtectionConfiguration. DefenderEmailContentExecutionType 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/CONFIG/DEFENDER/ATTACKSURFACEREDUCTIONRULES (CSP/構成にはグラフのプロパティが必要: Windows10endpointprotection/defenderOfficeAppsOtherProcessInjectionType, windows10endpointprotection/DefenderOfficeAppsExecutableContentCreationOrLaunchType、windows10endpointprotection/Configuration. defenderOfficeAppsLaunchChildProcessType、windows10endpointprotection/DefenderOfficeMacroCodeAllowWin32ImportsType、windows10endpointprotection/defenderScriptObfuscatedMacroCodeType、windows10endpointprotection//defenderScriptDownloadedPayloadExecutionType、windows10endpointprotection/Configuration. defenderEmailContentExecutionType、windows10endpointprotection/defenderPreventCredentialStealingType、windows10endpointprotection/構成. defenderUntrustedUSBProcessType

### <a name="windows10endpointprotectionconfigurationdefenderexploitprotectionxml"></a>Windows10EndpointProtectionConfiguration.DefenderExploitProtectionXml 
**CSP**:./DEVICE/VENDOR/MSFT/POLICY **Offset URI**:/Config/ExploitGuard/ExploitProtectionSettings

### <a name="windows10endpointprotectionconfigurationdefenderexploitprotectionxmlfilename"></a>Windows10EndpointProtectionConfiguration.DefenderExploitProtectionXmlFileName 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/ExploitGuard/ExploitProtectionSettings

### <a name="windows10endpointprotectionconfigurationdefenderguardedfoldersallowedapppaths"></a>Windows10EndpointProtectionConfiguration.DefenderGuardedFoldersAllowedAppPaths 
**CSP**:./DEVICE/VENDOR/MSFT/POLICY **Offset URI**:/Config/defenderの accessallowedapplications

### <a name="windows10endpointprotectionconfigurationdefenderguardmyfolderstype"></a>Windows10EndpointProtectionConfiguration. Defenderguシャード Myfolderstype 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Defender/EnableControlledFolderAccess

### <a name="windows10endpointprotectionconfigurationdefendernetworkprotectiontype"></a>Windows10EndpointProtectionConfiguration. DefenderNetworkProtectionType 
**CSP**:./DEVICE/VENDOR/MSFT/POLICY **Offset URI**:/Config/Defender/EnableNetworkProtection

### <a name="windows10endpointprotectionconfigurationdefenderofficeappsexecutablecontentcreationorlaunch"></a>Windows10EndpointProtectionConfiguration.DefenderOfficeAppsExecutableContentCreationOrLaunch 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Defender/AttackSurfaceReductionRules

### <a name="windows10endpointprotectionconfigurationdefenderofficeappsexecutablecontentcreationorlaunchtype"></a>Windows10EndpointProtectionConfiguration.DefenderOfficeAppsExecutableContentCreationOrLaunchType
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/CONFIG/DEFENDER/ATTACKSURFACEREDUCTIONRULES (CSP/構成にはグラフのプロパティが必要: Windows10endpointprotection/defenderOfficeAppsOtherProcessInjectionType, windows10endpointprotection/DefenderOfficeAppsExecutableContentCreationOrLaunchType、windows10endpointprotection/Configuration. defenderOfficeAppsLaunchChildProcessType、windows10endpointprotection/DefenderOfficeMacroCodeAllowWin32ImportsType、windows10endpointprotection/defenderScriptObfuscatedMacroCodeType、windows10endpointprotection//defenderScriptDownloadedPayloadExecutionType、windows10endpointprotection/Configuration. defenderEmailContentExecutionType、windows10endpointprotection/defenderPreventCredentialStealingType、windows10endpointprotection/構成. defenderUntrustedUSBProcessType

### <a name="windows10endpointprotectionconfigurationdefenderofficeappslaunchchildprocess"></a>Windows10EndpointProtectionConfiguration. DefenderOfficeAppsLaunchChildProcess 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Defender/AttackSurfaceReductionRules

### <a name="windows10endpointprotectionconfigurationdefenderofficeappslaunchchildprocesstype"></a>Windows10EndpointProtectionConfiguration. DefenderOfficeAppsLaunchChildProcessType 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/CONFIG/DEFENDER/ATTACKSURFACEREDUCTIONRULES (CSP/構成にはグラフのプロパティが必要: Windows10endpointprotection/defenderOfficeAppsOtherProcessInjectionType, windows10endpointprotection/DefenderOfficeAppsExecutableContentCreationOrLaunchType、windows10endpointprotection/Configuration. defenderOfficeAppsLaunchChildProcessType、windows10endpointprotection/DefenderOfficeMacroCodeAllowWin32ImportsType、windows10endpointprotection/defenderScriptObfuscatedMacroCodeType、windows10endpointprotection//defenderScriptDownloadedPayloadExecutionType、windows10endpointprotection/Configuration. defenderEmailContentExecutionType、windows10endpointprotection/defenderPreventCredentialStealingType、windows10endpointprotection/構成. defenderUntrustedUSBProcessType

### <a name="windows10endpointprotectionconfigurationdefenderofficeappsotherprocessinjection"></a>Windows10EndpointProtectionConfiguration. Defenderofficeappsoprocessインジェクション 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Defender/AttackSurfaceReductionRules

### <a name="windows10endpointprotectionconfigurationdefenderofficeappsotherprocessinjectiontype"></a>Windows10EndpointProtectionConfiguration.DefenderOfficeAppsOtherProcessInjectionType 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/CONFIG/DEFENDER/ATTACKSURFACEREDUCTIONRULES (CSP/構成にはグラフのプロパティが必要: Windows10endpointprotection/defenderOfficeAppsOtherProcessInjectionType, windows10endpointprotection/DefenderOfficeAppsExecutableContentCreationOrLaunchType、windows10endpointprotection/Configuration. defenderOfficeAppsLaunchChildProcessType、windows10endpointprotection/DefenderOfficeMacroCodeAllowWin32ImportsType、windows10endpointprotection/defenderScriptObfuscatedMacroCodeType、windows10endpointprotection//defenderScriptDownloadedPayloadExecutionType、windows10endpointprotection/Configuration. defenderEmailContentExecutionType、windows10endpointprotection/defenderPreventCredentialStealingType、windows10endpointprotection/構成. defenderUntrustedUSBProcessType 

### <a name="windows10endpointprotectionconfigurationdefenderofficemacrocodeallowwin32imports"></a>Windows10EndpointProtectionConfiguration.DefenderOfficeMacroCodeAllowWin32Imports 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Defender/AttackSurfaceReductionRules

### <a name="windows10endpointprotectionconfigurationdefenderofficemacrocodeallowwin32importstype"></a>Windows10EndpointProtectionConfiguration.DefenderOfficeMacroCodeAllowWin32ImportsType 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/CONFIG/DEFENDER/ATTACKSURFACEREDUCTIONRULES (CSP/構成にはグラフのプロパティが必要: Windows10endpointprotection/defenderOfficeAppsOtherProcessInjectionType, windows10endpointprotection/DefenderOfficeAppsExecutableContentCreationOrLaunchType、windows10endpointprotection/Configuration. defenderOfficeAppsLaunchChildProcessType、windows10endpointprotection/DefenderOfficeMacroCodeAllowWin32ImportsType、windows10endpointprotection/defenderScriptObfuscatedMacroCodeType、windows10endpointprotection//defenderScriptDownloadedPayloadExecutionType、windows10endpointprotection/Configuration. defenderEmailContentExecutionType、windows10endpointprotection/defenderPreventCredentialStealingType、windows10endpointprotection/構成. defenderUntrustedUSBProcessType

### <a name="windows10endpointprotectionconfigurationdefenderpreventcredentialstealingtype"></a>Windows10EndpointProtectionConfiguration.DefenderPreventCredentialStealingType 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/CONFIG/DEFENDER/ATTACKSURFACEREDUCTIONRULES (CSP/構成にはグラフのプロパティが必要: Windows10endpointprotection/defenderOfficeAppsOtherProcessInjectionType, windows10endpointprotection/DefenderOfficeAppsExecutableContentCreationOrLaunchType、windows10endpointprotection/Configuration. defenderOfficeAppsLaunchChildProcessType、windows10endpointprotection/DefenderOfficeMacroCodeAllowWin32ImportsType、windows10endpointprotection/defenderScriptObfuscatedMacroCodeType、windows10endpointprotection//defenderScriptDownloadedPayloadExecutionType、windows10endpointprotection/Configuration. defenderEmailContentExecutionType、windows10endpointprotection/defenderPreventCredentialStealingType、windows10endpointprotection/構成. defenderUntrustedUSBProcessType

### <a name="windows10endpointprotectionconfigurationdefenderprocesscreation"></a>Windows10EndpointProtectionConfiguration. DefenderProcessCreation 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Defender/AttackSurfaceReductionRules

### <a name="windows10endpointprotectionconfigurationdefenderprocesscreationtype"></a>Windows10EndpointProtectionConfiguration.DefenderProcessCreationType 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Defender/AttackSurfaceReductionRules

### <a name="windows10endpointprotectionconfigurationdefenderprotectagainstpotentiallyunwantedapplications"></a>Windows10EndpointProtectionConfiguration.DefenderProtectAgainstPotentiallyUnwantedApplications 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/MSSecurityGuide/TurnOnWindowsDefenderProtectionAgainstPotentiallyUnwantedApplications

### <a name="windows10endpointprotectionconfigurationdefenderscriptdownloadedpayloadexecution"></a>Windows10EndpointProtectionConfiguration.DefenderScriptDownloadedPayloadExecution 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Defender/AttackSurfaceReductionRules

### <a name="windows10endpointprotectionconfigurationdefenderscriptdownloadedpayloadexecutiontype"></a>Windows10EndpointProtectionConfiguration.DefenderScriptDownloadedPayloadExecutionType 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/CONFIG/DEFENDER/ATTACKSURFACEREDUCTIONRULES (CSP/構成にはグラフのプロパティが必要: Windows10endpointprotection/defenderOfficeAppsOtherProcessInjectionType, windows10endpointprotection/DefenderOfficeAppsExecutableContentCreationOrLaunchType、windows10endpointprotection/Configuration. defenderOfficeAppsLaunchChildProcessType、windows10endpointprotection/DefenderOfficeMacroCodeAllowWin32ImportsType、windows10endpointprotection/defenderScriptObfuscatedMacroCodeType、windows10endpointprotection//defenderScriptDownloadedPayloadExecutionType、windows10endpointprotection/Configuration. defenderEmailContentExecutionType、windows10endpointprotection/defenderPreventCredentialStealingType、windows10endpointprotection/構成. defenderUntrustedUSBProcessType

### <a name="windows10endpointprotectionconfigurationdefenderscriptobfuscatedmacrocode"></a>Windows10EndpointProtectionConfiguration.DefenderScriptObfuscatedMacroCode 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Defender/AttackSurfaceReductionRules

### <a name="windows10endpointprotectionconfigurationdefenderscriptobfuscatedmacrocodetype"></a>Windows10EndpointProtectionConfiguration.DefenderScriptObfuscatedMacroCodeType 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/CONFIG/DEFENDER/ATTACKSURFACEREDUCTIONRULES (CSP/構成にはグラフのプロパティが必要: Windows10endpointprotection/defenderOfficeAppsOtherProcessInjectionType, windows10endpointprotection/DefenderOfficeAppsExecutableContentCreationOrLaunchType、windows10endpointprotection/Configuration. defenderOfficeAppsLaunchChildProcessType、windows10endpointprotection/DefenderOfficeMacroCodeAllowWin32ImportsType、windows10endpointprotection/defenderScriptObfuscatedMacroCodeType、windows10endpointprotection//defenderScriptDownloadedPayloadExecutionType、windows10endpointprotection/Configuration. defenderEmailContentExecutionType、windows10endpointprotection/defenderPreventCredentialStealingType、windows10endpointprotection/構成. defenderUntrustedUSBProcessType

### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterblockexploitprotectionoverride"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterBlockExploitProtectionOverride 
**CSP**:./DEVICE/VENDOR/MSFT/POLICY **Offset URI**:/Config/WindowsDefenderSecurityCenter/DisallowExploitProtectionOverride

### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterdisableaccountui"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterDisableAccountUI 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/windowsdefendersecurityセンター/disableaccountprotectionui

### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterdisableappbrowserui"></a>Windows10EndpointProtectionConfiguration. Defendersecurityセンター Disableappbrowserui 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/windowsdefendersecurityセンター/disableappbrowserui

### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterdisablefamilyui"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterDisableFamilyUI 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/WindowsDefenderSecurityCenter/DisableFamilyUI

### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterdisablehealthui"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterDisableHealthUI 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/WindowsDefenderSecurityCenter/DisableHealthUI

### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterdisablenetworkui"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterDisableNetworkUI 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/WindowsDefenderSecurityCenter/DisableNetworkUI

### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterdisablesecurebootui"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterDisableSecureBootUI 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/WindowsDefenderSecurityCenter/HideSecureBoot

### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterdisabletroubleshootingui"></a>Windows10EndpointProtectionConfiguration. Defendersecurityセンター Disableのトラブルシューティング Ui 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/WindowsDefenderSecurityCenter/HideTPMTroubleshooting

### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterdisablevirusui"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterDisableVirusUI 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/WindowsDefenderSecurityCenter/DisableVirusUI

### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterhelpemail"></a>Windows10EndpointProtectionConfiguration. Defendersecurityセンター Helpemail 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/windowsdefendersecurityセンター/電子メール

### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterhelpphone"></a>Windows10EndpointProtectionConfiguration. Defendersecurityセンター Helpphone 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/windowsdefendersecurityセンター/電話

### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterhelpurl"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterHelpURL 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/WindowsDefenderSecurityCenter/URL

### <a name="windows10endpointprotectionconfigurationdefendersecuritycenteritcontactdisplay"></a>Windows10EndpointProtectionConfiguration. Defendersecurityセンター Itcontactdisplay 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/WindowsDefenderSecurityCenter/EnableCustomizedToasts、/windowsdefendersecurityセンター/enableinappcustomization

### <a name="windows10endpointprotectionconfigurationdefendersecuritycenternotificationsfromapp"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterNotificationsFromApp 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Windowsdefendersecuritymanag/hidewindowssecuritynotificationare、

### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterorganizationdisplayname"></a>Windows10EndpointProtectionConfiguration. Defendersecurityセンター組織名 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/windowsdefendersecurityセンター/CompanyName

### <a name="windows10endpointprotectionconfigurationdefenderuntrustedexecutable"></a>Windows10EndpointProtectionConfiguration.DefenderUntrustedExecutable 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Defender/AttackSurfaceReductionRules

### <a name="windows10endpointprotectionconfigurationdefenderuntrustedexecutabletype"></a>Windows10EndpointProtectionConfiguration.DefenderUntrustedExecutableType 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Defender/AttackSurfaceReductionRules

### <a name="windows10endpointprotectionconfigurationdefenderuntrustedusbprocess"></a>Windows10EndpointProtectionConfiguration. DefenderUntrustedUSBProcess 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Defender/AttackSurfaceReductionRules

### <a name="windows10endpointprotectionconfigurationdefenderuntrustedusbprocesstype"></a>Windows10EndpointProtectionConfiguration. DefenderUntrustedUSBProcessType 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/CONFIG/DEFENDER/ATTACKSURFACEREDUCTIONRULES (CSP/構成にはグラフのプロパティが必要: Windows10endpointprotection/defenderOfficeAppsOtherProcessInjectionType, windows10endpointprotection/DefenderOfficeAppsExecutableContentCreationOrLaunchType、windows10endpointprotection/Configuration. defenderOfficeAppsLaunchChildProcessType、windows10endpointprotection/DefenderOfficeMacroCodeAllowWin32ImportsType、windows10endpointprotection/defenderScriptObfuscatedMacroCodeType、windows10endpointprotection//defenderScriptDownloadedPayloadExecutionType、windows10endpointprotection/Configuration. defenderEmailContentExecutionType、windows10endpointprotection/defenderPreventCredentialStealingType、windows10endpointprotection/構成. defenderUntrustedUSBProcessType

### <a name="windows10endpointprotectionconfigurationdeviceguardenablesecurebootwithdma"></a>Windows10EndpointProtectionConfiguration.DeviceGuardEnableSecureBootWithDMA 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/DeviceGuard/RequirePlatformSecurityFeatures

### <a name="windows10endpointprotectionconfigurationdeviceguardenablevirtualizationbasedsecurity"></a>Windows10EndpointProtectionConfiguration.DeviceGuardEnableVirtualizationBasedSecurity 
**CSP**:./DEVICE/VENDOR/MSFT/POLICY **Offset URI**:/Config/DeviceGuard/EnableVirtualizationBasedSecurity

### <a name="windows10endpointprotectionconfigurationdeviceguardlaunchsystemguard"></a>Windows10EndpointProtectionConfiguration. Deviceguシャード Systemguard 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/DeviceGuard/ConfigureSystemGuardLaunch

### <a name="windows10endpointprotectionconfigurationdeviceguardlocalsystemauthoritycredentialguardsettings"></a>Windows10EndpointProtectionConfiguration.DeviceGuardLocalSystemAuthorityCredentialGuardSettings 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/DeviceGuard/LsaCfgFlags

### <a name="windows10endpointprotectionconfigurationdmaguarddeviceenumerationpolicy"></a>Windows10EndpointProtectionConfiguration.DmaGuardDeviceEnumerationPolicy 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/DmaGuard/DeviceEnumerationPolicy

### <a name="windows10endpointprotectionconfigurationeventlogserviceapplicationlogmaximumfilesizeinkb"></a>Windows10EndpointProtectionConfiguration.EventLogServiceApplicationLogMaximumFileSizeInKb 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/EventLogService/SpecifyMaximumFileSizeApplicationLog

### <a name="windows10endpointprotectionconfigurationeventlogservicesecuritylogmaximumfilesizeinkb"></a>Windows10EndpointProtectionConfiguration.EventLogServiceSecurityLogMaximumFileSizeInKb 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/EventLogService/SpecifyMaximumFileSizeSecurityLog

### <a name="windows10endpointprotectionconfigurationeventlogservicesystemlogmaximumfilesizeinkb"></a>Windows10EndpointProtectionConfiguration.EventLogServiceSystemLogMaximumFileSizeInKb 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/EventLogService/SpecifyMaximumFileSizeSystemLog

### <a name="windows10endpointprotectionconfigurationexplorerdataexecutionprevention"></a>Windows10EndpointProtectionConfiguration.ExplorerDataExecutionPrevention 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/FileExplorer/TurnOffDataExecutionPreventionForExplorer

### <a name="windows10endpointprotectionconfigurationexplorerheapterminationoncorruption"></a>Windows10EndpointProtectionConfiguration.ExplorerHeapTerminationOnCorruption 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/FileExplorer/TurnOffHeapTerminationOnCorruption

### <a name="windows10endpointprotectionconfigurationfirewallblockstatefulftp"></a>Windows10EndpointProtectionConfiguration.FirewallBlockStatefulFTP 
**CSP**:./Vendor/MSFT/Firewall  
**オフセット URI**:/MdmStore/Global/DisableStatefulFtp

### <a name="windows10endpointprotectionconfigurationfirewallcertificaterevocationlistcheckmethod"></a>Windows10EndpointProtectionConfiguration.FirewallCertificateRevocationListCheckMethod 
**CSP**:./Vendor/MSFT/Firewall  
**オフセット URI**:/MdmStore/Global/CRLcheck

### <a name="windows10endpointprotectionconfigurationfirewallidletimeoutforsecurityassociationinseconds"></a>Windows10EndpointProtectionConfiguration.FirewallIdleTimeoutForSecurityAssociationInSeconds 
**CSP**:./Vendor/MSFT/Firewall  
**オフセット URI**:/MdmStore/Global/SaIdleTime

### <a name="windows10endpointprotectionconfigurationfirewallipsecexemptionsallowdhcp"></a>Windows10EndpointProtectionConfiguration.FirewallIPSecExemptionsAllowDHCP 
**CSP**:./Vendor/MSFT/Firewall  
**オフセット URI**:/MdmStore/Global/IPsecExempt

### <a name="windows10endpointprotectionconfigurationfirewallipsecexemptionsallowicmp"></a>Windows10EndpointProtectionConfiguration.FirewallIPSecExemptionsAllowICMP 
**CSP**:./Vendor/MSFT/Firewall  
**オフセット URI**:/MdmStore/Global/IPsecExempt

### <a name="windows10endpointprotectionconfigurationfirewallipsecexemptionsallowneighbordiscovery"></a>Windows10EndpointProtectionConfiguration.FirewallIPSecExemptionsAllowNeighborDiscovery 
**CSP**:./Vendor/MSFT/Firewall  
**オフセット URI**:/MdmStore/Global/IPsecExempt

### <a name="windows10endpointprotectionconfigurationfirewallipsecexemptionsallowrouterdiscovery"></a>Windows10EndpointProtectionConfiguration.FirewallIPSecExemptionsAllowRouterDiscovery 
**CSP**:./Vendor/MSFT/Firewall  
**オフセット URI**:/MdmStore/Global/IPsecExempt

### <a name="windows10endpointprotectionconfigurationfirewallmergekeyingmodulesettings"></a>Windows10EndpointProtectionConfiguration.FirewallMergeKeyingModuleSettings 
**CSP**:./Vendor/MSFT/Firewall  
**オフセット URI**:/MdmStore/Global/OpportunisticallyMatchAuthSetPerKM

### <a name="windows10endpointprotectionconfigurationfirewallpacketqueueingmethod"></a>Windows10EndpointProtectionConfiguration.FirewallPacketQueueingMethod 
**CSP**:./Vendor/MSFT/Firewall  
**オフセット URI**:/MdmStore/Global/EnablePacketQueue

### <a name="windows10endpointprotectionconfigurationfirewallpresharedkeyencodingmethod"></a>Windows10EndpointProtectionConfiguration.FirewallPreSharedKeyEncodingMethod 
**CSP**:./Vendor/MSFT/Firewall  
**オフセット URI**:/MdmStore/Global/PresharedKeyEncoding

### <a name="windows10endpointprotectionconfigurationfirewallprofiledomain"></a>Windows10EndpointProtectionConfiguration.FirewallProfileDomain 
**CSP**:./Vendor/MSFT/Firewall  
**オフセット URI**:/enablefirewall、/DisableStealthMode、/シールド、/DisableUnicastResponsesToMulticastBroadcast、/DisableInboundNotifications、/AuthAppsAllowUserPrefMerge、/GlobalPortsAllowUserPrefMerge、/allowlocalpolicymerge、/DefaultOutboundAction、/Defaul/DisableStealthModeIpsecSecuredPacketExemption boundaction、、/allowlocalipsecpolicymerge

### <a name="windows10endpointprotectionconfigurationfirewallprofiledomaininboundconnectionsblocked"></a>windows10endpointprotectionconfiguration.firewallProfileDomain.inboundConnectionsBlocked 
**CSP**:./Device/Vendor/MSFT/Firewall  
**オフセット URI**:/MdmStore/DomainProfile/DefaultInboundAction

### <a name="windows10endpointprotectionconfigurationfirewallprofiledomaininboundnotificationsblocked"></a>windows10endpointprotectionconfiguration.firewallProfileDomain.inboundNotificationsBlocked 
**CSP**:./Device/Vendor/MSFT/Firewall  
**オフセット URI**:/MdmStore/DomainProfile/DisableInboundNotifications

### <a name="windows10endpointprotectionconfigurationfirewallprofiledomaininboundnotificationsblocked"></a>windows10endpointprotectionconfiguration.firewallProfileDomain.inboundNotificationsBlocked 
**CSP**:./Device/Vendor/MSFT/Firewall  
**オフセット URI**:/MdmStore/DomainProfile/EnableFirewall

### <a name="windows10endpointprotectionconfigurationfirewallprofiledomainoutboundconnectionsblocked"></a>windows10endpointprotectionconfiguration.firewallProfileDomain.outboundConnectionsBlocked 
**CSP**:./Device/Vendor/MSFT/Firewall  
**オフセット URI**:/MdmStore/DomainProfile/DefaultOutboundAction

### <a name="windows10endpointprotectionconfigurationfirewallprofileprivate"></a>Windows10EndpointProtectionConfiguration.FirewallProfilePrivate 
**CSP**:./Vendor/MSFT/Firewall  
**オフセット URI**:/enablefirewall、/DisableStealthMode、/シールド、/DisableUnicastResponsesToMulticastBroadcast、/DisableInboundNotifications、/AuthAppsAllowUserPrefMerge、/GlobalPortsAllowUserPrefMerge、/allowlocalpolicymerge、/DefaultOutboundAction、/Defaul/DisableStealthModeIpsecSecuredPacketExemption boundaction、、/allowlocalipsecpolicymerge

### <a name="windows10endpointprotectionconfigurationfirewallprofileprivatefirewallenabled"></a>windows10endpointprotectionconfiguration.firewallProfilePrivate.firewallEnabled 
**CSP**:./Device/Vendor/MSFT/Firewall  
**オフセット URI**:/MdmStore/PrivateProfile/EnableFirewall

### <a name="windows10endpointprotectionconfigurationfirewallprofileprivateinboundconnectionsblocked"></a>windows10endpointprotectionconfiguration.firewallProfilePrivate.inboundConnectionsBlocked 
**CSP**:./Device/Vendor/MSFT/Firewall  
**オフセット URI**:/MdmStore/PrivateProfile/DefaultInboundAction

### <a name="windows10endpointprotectionconfigurationfirewallprofileprivateinboundnotificationsblocked"></a>windows10endpointprotectionconfiguration.firewallProfilePrivate.inboundNotificationsBlocked 
**CSP**:./Device/Vendor/MSFT/Firewall  
**オフセット URI**:/MdmStore/PrivateProfile/DisableInboundNotifications

### <a name="windows10endpointprotectionconfigurationfirewallprofileprivateoutboundconnectionsblocked"></a>windows10endpointprotectionconfiguration.firewallProfilePrivate.outboundConnectionsBlocked 
**CSP**:./Device/Vendor/MSFT/Firewall  
**オフセット URI**:/MdmStore/PrivateProfile/DefaultOutboundAction

### <a name="windows10endpointprotectionconfigurationfirewallprofilepublic"></a>Windows10EndpointProtectionConfiguration.FirewallProfilePublic 
**CSP**:./Vendor/MSFT/Firewall  
**オフセット URI**:/enablefirewall、/DisableStealthMode、/シールド、/DisableUnicastResponsesToMulticastBroadcast、/DisableInboundNotifications、/AuthAppsAllowUserPrefMerge、/GlobalPortsAllowUserPrefMerge、/allowlocalpolicymerge、/DefaultOutboundAction、/Defaul/DisableStealthModeIpsecSecuredPacketExemption boundaction、、/allowlocalipsecpolicymerge

### <a name="windows10endpointprotectionconfigurationfirewallprofilepublicconnectionsecurityrulesfromgrouppolicymerged"></a>windows10endpointprotectionconfiguration. firewallProfilePublic | マージされた 
**CSP**:./Device/Vendor/MSFT/Firewall  
**オフセット URI**:/MdmStore/PublicProfile/AllowLocalIpsecPolicyMerge

### <a name="windows10endpointprotectionconfigurationfirewallprofilepublicfirewallenabled"></a>windows10endpointprotectionconfiguration.firewallProfilePublic.firewallEnabled 
**CSP**:./Device/Vendor/MSFT/Firewall  
**オフセット URI**:/MdmStore/PublicProfile/EnableFirewall

### <a name="windows10endpointprotectionconfigurationfirewallprofilepublicinboundconnectionsblocked"></a>windows10endpointprotectionconfiguration.firewallProfilePublic.inboundConnectionsBlocked 
**CSP**:./Device/Vendor/MSFT/Firewall  
**オフセット URI**:/MdmStore/PublicProfile/DefaultInboundAction

### <a name="windows10endpointprotectionconfigurationfirewallprofilepublicinboundnotificationsblocked"></a>windows10endpointprotectionconfiguration.firewallProfilePublic.inboundNotificationsBlocked 
**CSP**:./Device/Vendor/MSFT/Firewall  
**オフセット URI**:/MdmStore/PublicProfile/DisableInboundNotifications

### <a name="windows10endpointprotectionconfigurationfirewallprofilepublicoutboundconnectionsblocked"></a>windows10endpointprotectionconfiguration.firewallProfilePublic.outboundConnectionsBlocked 
**CSP**:./Device/Vendor/MSFT/Firewall  
**オフセット URI**:/MdmStore/PublicProfile/DefaultOutboundAction

### <a name="windows10endpointprotectionconfigurationfirewallprofilepublicpolicyrulesfromgrouppolicymerged"></a>windows10endpointprotectionconfiguration firewallProfilePublic/Grouppolicyマージされた 
**CSP**:./Device/Vendor/MSFT/Firewall  
**オフセット URI**:/MdmStore/PublicProfile/AllowLocalPolicyMerge

### <a name="windows10endpointprotectionconfigurationlanmanagerauthenticationlevel"></a>Windows10EndpointProtectionConfiguration. LanManagerAuthenticationLevel 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/LocalPoliciesSecurityOptions/NetworkSecurity\_lanmanagerauthenticationlevel

### <a name="windows10endpointprotectionconfigurationlanmanagerworkstationdisableinsecureguestlogons"></a>Windows10EndpointProtectionConfiguration ワークステーションの Disableinsecureguestログオン 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/LanmanWorkstation/EnableInsecureGuestLogons

### <a name="windows10endpointprotectionconfigurationlanmanagerworkstationenableinsecureguestlogons"></a>Windows10EndpointProtectionConfiguration ワークステーションの Enableinsecureguestログオン 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/LanmanWorkstation/EnableInsecureGuestLogons

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsadministratoraccountname"></a>Windows10EndpointProtectionConfiguration. Localsecurityoptionsaccountname 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/LocalPoliciesSecurityOptions/Accounts\_renameアドミニストレーターアカウント

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsadministratorelevationpromptbehavior"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsAdministratorElevationPromptBehavior
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/LocalPoliciesSecurityOptions/UserAccountControl\_BehaviorOfTheElevationPromptForAdministrators

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsallowanonymousenumerationofsamaccountsandshares"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsAllowAnonymousEnumerationOfSAMAccountsAndShares 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/LocalPoliciesSecurityOptions/NetworkAccess\_DoNotAllowAnonymousEnumerationOfSamAccountsAndShares

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsallowpku2uauthenticationrequests"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsAllowPKU2UAuthenticationRequests 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/LocalPoliciesSecurityOptions/NetworkSecurity\_AllowPKU2UAuthenticationRequests

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsallowremotecallstosecurityaccountsmanager"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsAllowRemoteCallsToSecurityAccountsManager 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/LocalPoliciesSecurityOptions/NetworkAccess\_RestrictClientsAllowedToMakeRemoteCallsToSAM

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsallowremotecallstosecurityaccountsmanagerhelperbool"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsAllowRemoteCallsToSecurityAccountsManagerHelperBool 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/LocalPoliciesSecurityOptions/NetworkAccess\_RestrictClientsAllowedToMakeRemoteCallsToSAM

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsallowsystemtobeshutdownwithouthavingtologon"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsAllowSystemToBeShutDownWithoutHavingToLogOn 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/LocalPoliciesSecurityOptions/Shutdown\_AllowSystemToBeShutDownWithoutHavingToLogOn

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsallowuiaccessapplicationelevation"></a>Windows10EndpointProtectionConfiguration. LocalSecurityOptionsAllowUIAccessApplicationElevation 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/LocalPoliciesSecurityOptions/UserAccountControl\_allowuiaccessapplicationstopromptforelevation

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsallowuiaccessapplicationsforsecurelocations"></a>Windows10EndpointProtectionConfiguration. Localsecurityoptionsallowuiaccessの場所 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/LocalPoliciesSecurityOptions/UserAccountControl\_OnlyElevateUIAccessApplicationsThatAreInstalledInSecureLocations

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsallowundockwithouthavingtologon"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsAllowUndockWithoutHavingToLogon 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/LocalPoliciesSecurityOptions/Devices\_AllowUndockWithoutHavingToLogon

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsblockmicrosoftaccounts"></a>Windows10EndpointProtectionConfiguration. Localsecurityoptionsblockmicrosoft アカウント 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/LocalPoliciesSecurityOptions/Accounts\_blockmicrosoft Accounts

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsblockremotelogonwithblankpassword"></a>Windows10EndpointProtectionConfiguration. Localsecurityoptionsblockremotelogonwithpassword 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/LocalPoliciesSecurityOptions/Accounts\_LimitLocalAccountUseOfBlankPasswordsToConsoleLogonOnly

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsblockremoteopticaldriveaccess"></a>Windows10EndpointProtectionConfiguration. Localsecurityoptionsblockremoteop・ドライブアクセス 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/LocalPoliciesSecurityOptions/Devices\_RestrictCDROMAccessToLocallyLoggedOnUserOnly

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsblockusersinstallingprinterdrivers"></a>Windows10EndpointProtectionConfiguration. Localsecurityoptionsblockのドライバー 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/LocalPoliciesSecurityOptions/Devices\_PreventUsersFromInstallingPrinterDriversWhenConnectingToSharedPrinters

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsclearvirtualmemorypagefile"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsClearVirtualMemoryPageFile 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/LocalPoliciesSecurityOptions/Shutdown\_ClearVirtualMemoryPageFile

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsclientdigitallysigncommunicationsalways"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsClientDigitallySignCommunicationsAlways 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/LocalPoliciesSecurityOptions/MicrosoftNetworkClient\_DigitallySignCommunicationsAlways

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsclientsendunencryptedpasswordtothirdpartysmbservers"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsClientSendUnencryptedPasswordToThirdPartySMBServers 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/LocalPoliciesSecurityOptions/MicrosoftNetworkClient\_SendUnencryptedPasswordToThirdPartySMBServers

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsdetectapplicationinstallationsandpromptforelevation"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsDetectApplicationInstallationsAndPromptForElevation 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/LocalPoliciesSecurityOptions/UserAccountControl\_DetectApplicationInstallationsAndPromptForElevation

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsdisableadministratoraccount"></a>Windows10EndpointProtectionConfiguration. Localsecurityoptionsdisableアドミニストレーターアカウント 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/LocalPoliciesSecurityOptions/Accounts\_enableアドミニストレーター accountstatus

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsdisableclientdigitallysigncommunicationsifserveragrees"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsDisableClientDigitallySignCommunicationsIfServerAgrees 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/LocalPoliciesSecurityOptions/MicrosoftNetworkClient\_DigitallySignCommunicationsIfServerAgrees

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsdisableguestaccount"></a>Windows10EndpointProtectionConfiguration. LocalSecurityOptionsDisableGuestAccount 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/LocalPoliciesSecurityOptions/Accounts\_enableguestaccountstatus

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsdisableserverdigitallysigncommunicationsalways"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsDisableServerDigitallySignCommunicationsAlways 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/LocalPoliciesSecurityOptions/MicrosoftNetworkServer\_DigitallySignCommunicationsAlways

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsdisableserverdigitallysigncommunicationsifclientagrees"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsDisableServerDigitallySignCommunicationsIfClientAgrees 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/LocalPoliciesSecurityOptions/MicrosoftNetworkServer\_DigitallySignCommunicationsIfClientAgrees

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsdonotallowanonymousenumerationofsamaccounts"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsDoNotAllowAnonymousEnumerationOfSAMAccounts 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/LocalPoliciesSecurityOptions/NetworkAccess\_DoNotAllowAnonymousEnumerationOfSAMAccounts

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsdonotrequirectrlaltdel"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsDoNotRequireCtrlAltDel 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/LocalPoliciesSecurityOptions/InteractiveLogon\_DoNotRequireCTRLALTDEL

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsdonotstorelanmanagerhashvalueonnextpasswordchange"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsDoNotStoreLANManagerHashValueOnNextPasswordChange 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/LocalPoliciesSecurityOptions/NetworkSecurity\_DoNotStoreLANManagerHashValueOnNextPasswordChange

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsenableadministratoraccount"></a>Windows10EndpointProtectionConfiguration. Localsecurityoptionsenablelocalhost アカウント 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/LocalPoliciesSecurityOptions/Accounts\_enableアドミニストレーター accountstatus

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsenableguestaccount"></a>Windows10EndpointProtectionConfiguration. LocalSecurityOptionsEnableGuestAccount 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/LocalPoliciesSecurityOptions/Accounts\_enableguestaccountstatus

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsformatandejectofremovablemediaalloweduser"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsFormatAndEjectOfRemovableMediaAllowedUser 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/LocalPoliciesSecurityOptions/Devices\_AllowedToFormatAndEjectRemovableMedia

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsguestaccountname"></a>Windows10EndpointProtectionConfiguration. LocalSecurityOptionsGuestAccountName 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/LocalPoliciesSecurityOptions/Accounts\_renameguestaccount

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionshidelastsignedinuser"></a>Windows10EndpointProtectionConfiguration. Localsecurityoption佐々木 Delastsignedinuser 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/LocalPoliciesSecurityOptions/InteractiveLogon\_は、

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionshideusernameatsignin"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsHideUsernameAtSignIn 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/LocalPoliciesSecurityOptions/InteractiveLogon\_DoNotDisplayUsernameAtSignIn

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsinformationdisplayedonlockscreen"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsInformationDisplayedOnLockScreen 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/LocalPoliciesSecurityOptions/InteractiveLogon\_displayuserinformationwhenthesessionislocked

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsinformationshownonlockscreen"></a>Windows10EndpointProtectionConfiguration. LocalSecurityOptionsInformationShownOnLockScreen ロック 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/LocalPoliciesSecurityOptions/InteractiveLogon\_displayuserinformationwhenthesessionislocked

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionslogonmessagetext"></a>Windows10EndpointProtectionConfiguration. LocalSecurityOptionsLogOnMessageText 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/LocalPoliciesSecurityOptions/InteractiveLogon\_MessageTextForUsersAttemptingToLogOn

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionslogonmessagetitle"></a>Windows10EndpointProtectionConfiguration. LocalSecurityOptionsLogOnMessageTitle 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/LocalPoliciesSecurityOptions/InteractiveLogon\_MessageTitleForUsersAttemptingToLogOn

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsmachineinactivitylimit"></a>Windows10EndpointProtectionConfiguration. LocalSecurityOptionsMachineInactivityLimit 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/LocalPoliciesSecurityOptions/InteractiveLogon\_machineinactivitylimit

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsmachineinactivitylimitinminutes"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsMachineInactivityLimitInMinutes 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/LocalPoliciesSecurityOptions/InteractiveLogon\_machineinactivitylimit

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsminimumsessionsecurityforntlmsspbasedclients"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsMinimumSessionSecurityForNtlmSspBasedClients 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/LocalPoliciesSecurityOptions/NetworkSecurity\_MinimumSessionSecurityForNTLMSSPBasedClients

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsminimumsessionsecurityforntlmsspbasedservers"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsMinimumSessionSecurityForNtlmSspBasedServers 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/LocalPoliciesSecurityOptions/NetworkSecurity\_MinimumSessionSecurityForNTLMSSPBasedServers

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsonlyelevatesignedexecutables"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsOnlyElevateSignedExecutables 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/LocalPoliciesSecurityOptions/UserAccountControl\_OnlyElevateExecutableFilesThatAreSignedAndValidated

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsrestrictanonymousaccesstonamedpipesandshares"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsRestrictAnonymousAccessToNamedPipesAndShares 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/LocalPoliciesSecurityOptions/NetworkAccess\_RestrictAnonymousAccessToNamedPipesAndShares

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionssmartcardremovalbehavior"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsSmartCardRemovalBehavior 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/LocalPoliciesSecurityOptions/InteractiveLogon\_SmartCardRemovalBehavior

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsstandarduserelevationpromptbehavior"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsStandardUserElevationPromptBehavior 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/LocalPoliciesSecurityOptions/UserAccountControl\_BehaviorOfTheElevationPromptForStandardUsers

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsswitchtosecuredesktopwhenpromptingforelevation"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsSwitchToSecureDesktopWhenPromptingForElevation 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/LocalPoliciesSecurityOptions/UserAccountControl\_SwitchToTheSecureDesktopWhenPromptingForElevation

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsuseadminapprovalmode"></a>Windows10EndpointProtectionConfiguration. LocalSecurityOptionsUseAdminApprovalMode 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/LocalPoliciesSecurityOptions/UserAccountControl\_useadminapprovalmode

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsuseadminapprovalmodeforadministrators"></a>Windows10EndpointProtectionConfiguration. LocalSecurityOptionsUseAdminApprovalModeForAdministrators 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/LocalPoliciesSecurityOptions/UserAccountControl\_runalladministratorsinadminapprovalmode

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsvirtualizefileandregistrywritefailurestoperuserlocations"></a>Windows10EndpointProtectionConfiguration. LocalSecurityOptionsVirtualizeFileAndRegistryWriteFailuresToPerUserLocations 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/LocalPoliciesSecurityOptions/UserAccountControl\_virtualizefileandregistrywritefailurestoperuserlocations

### <a name="windows10endpointprotectionconfigurationnetworkicmpredirectsoverrideospfgeneratedroutes"></a>Windows10EndpointProtectionConfiguration.NetworkIcmpRedirectsOverrideOspfGeneratedRoutes 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/MSSLegacy/AllowICMPRedirectsToOverrideOSPFGeneratedRoutes

### <a name="windows10endpointprotectionconfigurationnetworkignorenetbiosnamereleaserequestsexceptfromwinsservers"></a>Windows10EndpointProtectionConfiguration.NetworkIgnoreNetBiosNameReleaseRequestsExceptFromWinsServers 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/MSSLegacy/AllowTheComputerToIgnoreNetBIOSNameReleaseRequestsExceptFromWINSServers

### <a name="windows10endpointprotectionconfigurationnetworkipsourceroutingprotectionlevel"></a>Windows10EndpointProtectionConfiguration.NetworkIpSourceRoutingProtectionLevel 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/MSSLegacy/IPSourceRoutingProtectionLevel

### <a name="windows10endpointprotectionconfigurationnetworkipv6sourceroutingprotectionlevel"></a>Windows10EndpointProtectionConfiguration.NetworkIpV6SourceRoutingProtectionLevel 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/MSSLegacy/IPv6SourceRoutingProtectionLevel

### <a name="windows10endpointprotectionconfigurationpasswordpinlogon"></a>Windows10EndpointProtectionConfiguration ログオン 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/CredentialProviders/AllowPINLogon

### <a name="windows10endpointprotectionconfigurationpowershellshellscriptblocklogging"></a>Windows10EndpointProtectionConfiguration. PowerShellShellScriptBlockLogging 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Windowspowershell/turnonpowershellscriptblocklogging

### <a name="windows10endpointprotectionconfigurationremoteassistancesolicitedsetting"></a>Windows10EndpointProtectionConfiguration.RemoteAssistanceSolicitedSetting 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Connectivity/HardenedUNCPaths

### <a name="windows10endpointprotectionconfigurationremotedesktopservicesclientconnectionencryptionlevel"></a>Windows10EndpointProtectionConfiguration.RemoteDesktopServicesClientConnectionEncryptionLevel 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/RemoteDesktopServices/ClientConnectionEncryptionLevel

### <a name="windows10endpointprotectionconfigurationremotedesktopservicesdriveredirection"></a>Windows10EndpointProtectionConfiguration. Remotedesktopサービス Driveredirection 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Dns/remoteallowdriveredirection

### <a name="windows10endpointprotectionconfigurationremotedesktopservicespasswordsaving"></a>Windows10EndpointProtectionConfiguration. Remotedesktopサービス Password保存 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/remotedesktopの保存

### <a name="windows10endpointprotectionconfigurationremotedesktopservicespromptforpassworduponconnection"></a>Windows10EndpointProtectionConfiguration.RemoteDesktopServicesPromptForPasswordUponConnection 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/RemoteDesktopServices/PromptForPasswordUponConnection

### <a name="windows10endpointprotectionconfigurationremotedesktopservicessecurerpccommunication"></a>Windows10EndpointProtectionConfiguration. Remotedesktopサービスの通信 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/RemoteDesktopServices/RequireSecureRPCCommunication

### <a name="windows10endpointprotectionconfigurationremotehostdelegationofnonexportablecredentials"></a>Windows10EndpointProtectionConfiguration.RemoteHostDelegationOfNonExportableCredentials 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/CredentialsDelegation/RemoteHostAllowsDelegationOfNonExportableCredentials

### <a name="windows10endpointprotectionconfigurationremotemanagementclientbasicauthentication"></a>Windows10EndpointProtectionConfiguration.RemoteManagementClientBasicAuthentication 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/RemoteManagement/AllowBasicAuthentication\_Client

### <a name="windows10endpointprotectionconfigurationremotemanagementclientdigestauthentication"></a>Windows10EndpointProtectionConfiguration.RemoteManagementClientDigestAuthentication 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/RemoteManagement/DisallowDigestAuthentication

### <a name="windows10endpointprotectionconfigurationremotemanagementclientunencryptedtraffic"></a>Windows10EndpointProtectionConfiguration.RemoteManagementClientUnencryptedTraffic 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/RemoteManagement/AllowUnencryptedTraffic\_Client

### <a name="windows10endpointprotectionconfigurationremotemanagementservicebasicauthentication"></a>Windows10EndpointProtectionConfiguration.RemoteManagementServiceBasicAuthentication 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/RemoteManagement/AllowBasicAuthentication\_Service

### <a name="windows10endpointprotectionconfigurationremotemanagementservicestoringrunascredentials"></a>Windows10EndpointProtectionConfiguration.RemoteManagementServiceStoringRunAsCredentials 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/RemoteManagement/DisallowStoringOfRunAsCredentials

### <a name="windows10endpointprotectionconfigurationremotemanagementserviceunencryptedtraffic"></a>Windows10EndpointProtectionConfiguration.RemoteManagementServiceUnencryptedTraffic 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/RemoteManagement/AllowUnencryptedTraffic\_Service

### <a name="windows10endpointprotectionconfigurationrpcunauthenticatedclientoptions"></a>Windows10EndpointProtectionConfiguration.RpcUnauthenticatedClientOptions 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/RemoteProcedureCall/RestrictUnauthenticatedRPCClients

### <a name="windows10endpointprotectionconfigurationsecurityguideapplyuacrestrictionstolocalaccountsonnetworklogon"></a>Windows10EndpointProtectionConfiguration.SecurityGuideApplyUacRestrictionsToLocalAccountsOnNetworkLogon 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/MSSecurityGuide/ApplyUACRestrictionsToLocalAccountsOnNetworkLogon

### <a name="windows10endpointprotectionconfigurationsecurityguidesmbv1clientdriverstartconfiguration"></a>Windows10EndpointProtectionConfiguration.SecurityGuideSmbV1ClientDriverStartConfiguration 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/MSSecurityGuide/ConfigureSMBV1ClientDriver

### <a name="windows10endpointprotectionconfigurationsecurityguidesmbv1server"></a>Windows10EndpointProtectionConfiguration.SecurityGuideSmbV1Server 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/MSSecurityGuide/ConfigureSMBV1Server

### <a name="windows10endpointprotectionconfigurationsecurityguidestructuredexceptionhandlingoverwriteprotection"></a>Windows10EndpointProtectionConfiguration.SecurityGuideStructuredExceptionHandlingOverwriteProtection 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/MSSecurityGuide/EnableStructuredExceptionHandlingOverwriteProtection

### <a name="windows10endpointprotectionconfigurationsecurityguidewdigestauthentication"></a>Windows10EndpointProtectionConfiguration.SecurityGuideWDigestAuthentication 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/MSSecurityGuide/WDigestAuthentication

### <a name="windows10endpointprotectionconfigurationsmartscreenblockoverrideforfiles"></a>Windows10EndpointProtectionConfiguration.SmartScreenBlockOverrideForFiles 
**CSP**:./DEVICE/VENDOR/MSFT/POLICY **Offset URI**:/Config/DeviceGuard/RequirePlatformSecurityFeatures

### <a name="windows10endpointprotectionconfigurationsmartscreenenableinshell"></a>Windows10EndpointProtectionConfiguration のスクリーンショット 
**CSP**:./DEVICE/VENDOR/MSFT/POLICY **Offset URI**:/Config/SmartScreen/EnableSmartScreenInShell

### <a name="windows10endpointprotectionconfigurationsolicitedremoteassistance"></a>windows10endpointprotectionconfiguration.solicitedRemoteAssistance 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/RemoteAssistance/SolicitedRemoteAssistance

### <a name="windows10endpointprotectionconfigurationuserrightsaccesscredentialmanagerastrustedcaller"></a>Windows10EndpointProtectionConfiguration.UserRightsAccessCredentialManagerAsTrustedCaller 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/UserRights/AccessCredentialManagerAsTrustedCaller

### <a name="windows10endpointprotectionconfigurationuserrightsaccessfromnetwork"></a>windows10EndpointProtectionConfiguration.UserRightsAccessFromNetwork 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/UserRights/AccessFromNetwork

### <a name="windows10endpointprotectionconfigurationuserrightsactaspartoftheoperatingsystem"></a>Windows10EndpointProtectionConfiguration.userRightsActAsPartOfTheOperatingSystem 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/UserRights/ActAsPartOfTheOperatingSystem

### <a name="windows10endpointprotectionconfigurationuserrightsallowaccessfromnetwork"></a>Windows10EndpointProtectionConfiguration.UserRightsAllowAccessFromNetwork 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/UserRights/AccessFromNetwork

### <a name="windows10endpointprotectionconfigurationuserrightsbackupdata"></a>Windows10EndpointProtectionConfiguration.UserRightsBackupData 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/UserRights/BackupFilesAndDirectories

### <a name="windows10endpointprotectionconfigurationuserrightsblockaccessfromnetwork"></a>Windows10EndpointProtectionConfiguration.UserRightsBlockAccessFromNetwork 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/UserRights/DenyAccessFromNetwork

### <a name="windows10endpointprotectionconfigurationuserrightschangesystemtime"></a>Windows10EndpointProtectionConfiguration.UserRightsChangeSystemTime 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/UserRights/ChangeSystemTime

### <a name="windows10endpointprotectionconfigurationuserrightscreateglobalobjects"></a>Windows10EndpointProtectionConfiguration.UserRightsCreateGlobalObjects 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/UserRights/CreateGlobalObjects

### <a name="windows10endpointprotectionconfigurationuserrightscreatepagefile"></a>Windows10EndpointProtectionConfiguration.UserRightsCreatePageFile 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/UserRights/CreatePageFile

### <a name="windows10endpointprotectionconfigurationuserrightscreatepermanentsharedobjects"></a>Windows10EndpointProtectionConfiguration.UserRightsCreatePermanentSharedObjects 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/UserRights/CreatePermanentSharedObjects

### <a name="windows10endpointprotectionconfigurationuserrightscreatesymboliclinks"></a>Windows10EndpointProtectionConfiguration.UserRightsCreateSymbolicLinks 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/UserRights/CreateSymbolicLinks

### <a name="windows10endpointprotectionconfigurationuserrightscreatetoken"></a>Windows10EndpointProtectionConfiguration.UserRightsCreateToken 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/UserRights/CreateToken

### <a name="windows10endpointprotectionconfigurationuserrightsdebugprograms"></a>Windows10EndpointProtectionConfiguration.UserRightsDebugPrograms 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/UserRights/DebugPrograms

### <a name="windows10endpointprotectionconfigurationuserrightsdelegation"></a>Windows10EndpointProtectionConfiguration.UserRightsDelegation 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/UserRights/EnableDelegation

### <a name="windows10endpointprotectionconfigurationuserrightsdenyaccessfromnetwork"></a>windows10EndpointProtectionConfiguration.UserRightsDenyAccessFromNetwork 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/UserRights/DenyAccessFromNetwork

### <a name="windows10endpointprotectionconfigurationuserrightsgeneratesecurityaudits"></a>Windows10EndpointProtectionConfiguration.UserRightsGenerateSecurityAudits 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/UserRights/GenerateSecurityAudits

### <a name="windows10endpointprotectionconfigurationuserrightsimpersonateclient"></a>Windows10EndpointProtectionConfiguration のようになります。 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/UserRights/ImpersonateClient

### <a name="windows10endpointprotectionconfigurationuserrightsincreaseschedulingpriority"></a>Windows10EndpointProtectionConfiguration.UserRightsIncreaseSchedulingPriority 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/UserRights/IncreaseSchedulingPriority

### <a name="windows10endpointprotectionconfigurationuserrightsloadunloaddrivers"></a>Windows10EndpointProtectionConfiguration.UserRightsLoadUnloadDrivers 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/UserRights/LoadUnloadDeviceDrivers

### <a name="windows10endpointprotectionconfigurationuserrightslocallogon"></a>Windows10EndpointProtectionConfiguration.UserRightsLocalLogOn 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/UserRights/AllowLocalLogOn

### <a name="windows10endpointprotectionconfigurationuserrightslockmemory"></a>Windows10EndpointProtectionConfiguration.UserRightsLockMemory 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/UserRights/LockMemory

### <a name="windows10endpointprotectionconfigurationuserrightsmanageauditingandsecuritylogs"></a>Windows10EndpointProtectionConfiguration.UserRightsManageAuditingAndSecurityLogs 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/UserRights/ManageAuditingAndSecurityLog

### <a name="windows10endpointprotectionconfigurationuserrightsmanagevolumes"></a>Windows10EndpointProtectionConfiguration.UserRightsManageVolumes 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/UserRights/ManageVolume

### <a name="windows10endpointprotectionconfigurationuserrightsmodifyfirmwareenvironment"></a>Windows10EndpointProtectionConfiguration.UserRightsModifyFirmwareEnvironment 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/UserRights/ModifyFirmwareEnvironment

### <a name="windows10endpointprotectionconfigurationuserrightsmodifyobjectlabels"></a>Windows10EndpointProtectionConfiguration.UserRightsModifyObjectLabels 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/UserRights/ModifyObjectLabel

### <a name="windows10endpointprotectionconfigurationuserrightsprofilesingleprocess"></a>Windows10EndpointProtectionConfiguration.UserRightsProfileSingleProcess 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/UserRights/ProfileSingleProcess

### <a name="windows10endpointprotectionconfigurationuserrightsregisterprocessasservice"></a>Windows10EndpointProtectionConfiguration.UserRightsRegisterProcessAsService 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/UserRights/DenyLocalLogOn

### <a name="windows10endpointprotectionconfigurationuserrightsremotedesktopserviceslogon"></a>Windows10EndpointProtectionConfiguration.UserRightsRemoteDesktopServicesLogOn 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/UserRights/DenyRemoteDesktopServicesLogOn

### <a name="windows10endpointprotectionconfigurationuserrightsremoteshutdown"></a>Windows10EndpointProtectionConfiguration.UserRightsRemoteShutdown 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/UserRights/RemoteShutdown

### <a name="windows10endpointprotectionconfigurationuserrightsrestoredata"></a>Windows10EndpointProtectionConfiguration.UserRightsRestoreData 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/UserRights/RestoreFilesAndDirectories

### <a name="windows10endpointprotectionconfigurationuserrightstakeownership"></a>Windows10EndpointProtectionConfiguration.UserRightsTakeOwnership 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/UserRights/TakeOwnership

### <a name="windows10endpointprotectionconfigurationwindowsconnectionmanagerconnectiontonondomainnetworks"></a>Windows10EndpointProtectionConfiguration. WindowsConnectionManagerConnectionToNonDomainNetworks 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/WindowsConnectionManager/ProhitConnectionToNonDomainNetworksWhenConnectedToDomainAuthenticatedNetwork

### <a name="windows10endpointprotectionconfigurationwindowslogonsigninlastinteractiveuseraftersysteminitiatedrestart"></a>Windows10EndpointProtectionConfiguration.WindowsLogOnSignInLastInteractiveUserAfterSystemInitiatedRestart 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/WindowsLogon/SignInLastInteractiveUserAutomaticallyAfterASystemInitiatedRestart

### <a name="windows10endpointprotectionconfigurationxboxservicesaccessorymanagementservicestartupmode"></a>Windows10EndpointProtectionConfiguration.XboxServicesAccessoryManagementServiceStartupMode 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/SystemServices/ConfigureXboxAccessoryManagementServiceStartupMode

### <a name="windows10endpointprotectionconfigurationxboxservicesenablexboxgamesavetask"></a>Windows10EndpointProtectionConfiguration.XboxServicesEnableXboxGameSaveTask 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/TaskScheduler/EnableXboxGameSaveTask

### <a name="windows10endpointprotectionconfigurationxboxservicesliveauthmanagerservicestartupmode"></a>Windows10EndpointProtectionConfiguration.XboxServicesLiveAuthManagerServiceStartupMode 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/SystemServices/ConfigureXboxLiveAuthManagerServiceStartupMode

### <a name="windows10endpointprotectionconfigurationxboxserviceslivegamesaveservicestartupmode"></a>Windows10EndpointProtectionConfiguration.XboxServicesLiveGameSaveServiceStartupMode 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/SystemServices/XboxServicesLiveGameSaveServiceStartupMode

### <a name="windows10endpointprotectionconfigurationxboxserviceslivenetworkingservicestartupmode"></a>Windows10EndpointProtectionConfiguration.XboxServicesLiveNetworkingServiceStartupMode 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/SystemServices/ConfigureXboxLiveNetworkingServiceStartupMode

### <a name="windows10enterprisemodernappmanagementconfigurationuninstallbuiltinapps"></a>Windows10EnterpriseModernAppManagementConfiguration.UninstallBuiltInApps
**CSP**:N/A Graph API**オフセット URI**のみを呼び出します。N/A Graph API 呼び出しのみ

### <a name="windows10generalconfigurationaccountsblockaddingnonmicrosoftaccountemail"></a>Windows10GeneralConfiguration.AccountsBlockAddingNonMicrosoftAccountEmail 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Accounts/AllowAddingNonMicrosoftAccountsManually

### <a name="windows10generalconfigurationantitheftmodeblocked"></a>Windows10GeneralConfiguration.AntiTheftModeBlocked 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Security/AntiTheftMode

### <a name="windows10generalconfigurationappmanagementmsiallowusercontroloverinstall"></a>Windows10GeneralConfiguration. AppManagementMSIAllowUserControlOverInstall 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/ApplicationManagement/MSIAllowUserControlOverInstall

### <a name="windows10generalconfigurationappmanagementmsialwaysinstallwithelevatedprivileges"></a>Windows10GeneralConfiguration.AppManagementMSIAlwaysInstallWithElevatedPrivileges 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/ApplicationManagement/MSIAlwaysInstallWithElevatedPrivileges

### <a name="windows10generalconfigurationappsallowtrustedappssideloading"></a>Windows10GeneralConfiguration (AppsAllowTrustedAppsSideloading ローディング) 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/config/Applicationmanagement/allowalltrustedapps

### <a name="windows10generalconfigurationappsblockwindowsstoreoriginatedapps"></a>Windows10GeneralConfiguration. AppsBlockWindowsStoreOriginatedApps 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/アプリケーション管理/disablestoreatedatedapps

### <a name="windows10generalconfigurationappsmicrosoftaccountsoptional"></a>Windows10GeneralConfiguration.AppsMicrosoftAccountsOptional 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/dns/allowmicrosoft accountstobeoptional

### <a name="windows10generalconfigurationassignedaccessmultimodeprofiles"></a>Windows10GeneralConfiguration.AssignedAccessMultiModeProfiles 
**CSP**:./Device/Vendor/MSFT/AssignedAccess  
**オフセット URI**:/構成

### <a name="windows10generalconfigurationassignedaccesssinglemodeappusermodelid"></a>Windows10GeneralConfiguration.AssignedAccessSingleModeAppUserModelId 
**CSP**:./Device/Vendor/MSFT/AssignedAccess  
**オフセット URI**:/構成

### <a name="windows10generalconfigurationassignedaccesssinglemodeusername"></a>Windows10GeneralConfiguration.AssignedAccessSingleModeUserName 
**CSP**:./Device/Vendor/MSFT/AssignedAccess  
**オフセット URI**:/構成

### <a name="windows10generalconfigurationauthenticationallowfidodevice"></a>Windows10GeneralConfiguration. AuthenticationAllowFIDODevice 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/config/認証/allowfidojobs ignon

### <a name="windows10generalconfigurationauthenticationallowsecondarydevice"></a>Windows10GeneralConfiguration デバイス 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/authenticationsecondaryauthenticationdevice

### <a name="windows10generalconfigurationauthenticationpreferredazureadtenantdomainname"></a>Windows10GeneralConfiguration.AuthenticationPreferredAzureADTenantDomainName 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Authentication/PreferredAadTenantDomainName

### <a name="windows10generalconfigurationauthenticationwebsignin"></a>Windows10GeneralConfiguration 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/authenticationwebサインイン

### <a name="windows10generalconfigurationautoplaydefaultautorunbehavior"></a>Windows10GeneralConfiguration.AutoPlayDefaultAutoRunBehavior 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Autoplay/SetDefaultAutoRunBehavior

### <a name="windows10generalconfigurationautoplayfornonvolumedevices"></a>Windows10GeneralConfiguration. AutoPlayForNonVolumeDevices 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Autoplay/DisallowAutoplayForNonVolumeDevices

### <a name="windows10generalconfigurationautoplaymode"></a>Windows10GeneralConfiguration モード 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Autoplay/TurnOffAutoPlay

### <a name="windows10generalconfigurationbluetoothallowedservices"></a>Windows10GeneralConfiguration.BluetoothAllowedServices 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Bluetooth/ServicesAllowedList

### <a name="windows10generalconfigurationbluetoothblockadvertising"></a>Windows10GeneralConfiguration.BluetoothBlockAdvertising 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Bluetooth/AllowAdvertising

### <a name="windows10generalconfigurationbluetoothblockdiscoverablemode"></a>Windows10GeneralConfiguration.BluetoothBlockDiscoverableMode 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Bluetooth/AllowDiscoverableMode

### <a name="windows10generalconfigurationbluetoothblocked"></a>Windows10GeneralConfiguration.BluetoothBlocked 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Connectivity/AllowBluetooth

### <a name="windows10generalconfigurationbluetoothblockprepairing"></a>Windows10GeneralConfiguration.BluetoothBlockPrePairing 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Bluetooth/AllowPrepairing

### <a name="windows10generalconfigurationbluetoothblockpromptedproximalconnections"></a>Windows10GeneralConfiguration.BluetoothBlockPromptedProximalConnections 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Bluetooth/AllowPromptedProximalConnections

### <a name="windows10generalconfigurationbluetoothdevicename"></a>Windows10GeneralConfiguration.BluetoothDeviceName 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Bluetooth/LocalDeviceName

### <a name="windows10generalconfigurationbootstartdriverinitialization"></a>windows10generalconfiguration の初期化 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/System/BootStartDriverInitialization

### <a name="windows10generalconfigurationcamerablocked"></a>Windows10GeneralConfiguration.CameraBlocked 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Camera/AllowCamera

### <a name="windows10generalconfigurationcellularblockdatawhenroaming"></a>Windows10GeneralConfiguration. CellularBlockDataWhenRoaming 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Connectivity/AllowCellularDataRoaming

### <a name="windows10generalconfigurationcellularblockvpn"></a>Windows10GeneralConfiguration. CellularBlockVpn 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Connectivity/AllowVPNOverCellular

### <a name="windows10generalconfigurationcellularblockvpnwhenroaming"></a>Windows10GeneralConfiguration. CellularBlockVpnWhenRoaming 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Connectivity/AllowVPNRoamingOverCellular

### <a name="windows10generalconfigurationcellulardata"></a>Windows10GeneralConfiguration データ 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Connectivity/AllowCellularData

### <a name="windows10generalconfigurationcertificatesblockmanualrootcertificateinstallation"></a>Windows10GeneralConfiguration.CertificatesBlockManualRootCertificateInstallation 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/securitycertificateinstallation

### <a name="windows10generalconfigurationconnecteddevicesserviceblocked"></a>Windows10GeneralConfiguration サービスがブロックされました 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Connectivity/AllowConnectedDevices

### <a name="windows10generalconfigurationcopypasteblocked"></a>Windows10GeneralConfiguration.CopyPasteBlocked 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Experience/AllowCopyPaste

### <a name="windows10generalconfigurationcortanablocked"></a>Windows10GeneralConfiguration.CortanaBlocked 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/AboveLock/AllowCortanaAboveLock

### <a name="windows10generalconfigurationcryptographyallowfipsalgorithmpolicy"></a>Windows10GeneralConfiguration.CryptographyAllowFipsAlgorithmPolicy 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Cryptography/AllowFipsAlgorithmPolicy

### <a name="windows10generalconfigurationdataprotectionblockdirectmemoryaccess"></a>Windows10GeneralConfiguration.DataProtectionBlockDirectMemoryAccess 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Dataprotection/allowdirectmemoryaccess

### <a name="windows10generalconfigurationdefenderblockenduseraccess"></a>Windows10GeneralConfiguration. DefenderBlockEndUserAccess 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Defender/allowuseruiaccess

### <a name="windows10generalconfigurationdefenderblockonaccessprotection"></a>Windows10GeneralConfiguration. DefenderBlockOnAccessProtection 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/dns/allowonaccessprotection

### <a name="windows10generalconfigurationdefendercloudblocklevel"></a>Windows10GeneralConfiguration. DefenderCloudBlockLevel 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/defblocklevel

### <a name="windows10generalconfigurationdefendercloudextendedtimeout"></a>Windows10GeneralConfiguration.DefenderCloudExtendedTimeout 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Defender/CloudExtendedTimeout

### <a name="windows10generalconfigurationdefendercloudextendedtimeoutinseconds"></a>Windows10GeneralConfiguration.DefenderCloudExtendedTimeoutInSeconds 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Defender/CloudExtendedTimeout

### <a name="windows10generalconfigurationdefenderdaysbeforedeletingquarantinedmalware"></a>Windows10GeneralConfiguration.DefenderDaysBeforeDeletingQuarantinedMalware 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/defenderedマルウェア

### <a name="windows10generalconfigurationdefenderdetectedmalwareactions"></a>Windows10GeneralConfiguration.DefenderDetectedMalwareActions 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Defender/ThreatSeverityDefaultAction

### <a name="windows10generalconfigurationdefenderfileextensionstoexclude"></a>Windows10GeneralConfiguration. DefenderFileExtensionsToExclude 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Defender/ExcludedExtensions

### <a name="windows10generalconfigurationdefenderfilesandfolderstoexclude"></a>Windows10GeneralConfiguration. DefenderFilesAndFoldersToExclude 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Defender/ExcludedPaths

### <a name="windows10generalconfigurationdefendermonitorfileactivity"></a>Windows10GeneralConfiguration. DefenderMonitorFileActivity 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Defender/AllowRealtimeMonitoring

### <a name="windows10generalconfigurationdefenderpotentiallyunwantedappaction"></a>Windows10GeneralConfiguration.DefenderPotentiallyUnwantedAppAction 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/config/defaprotection

### <a name="windows10generalconfigurationdefenderpotentiallyunwantedappactionsetting"></a>Windows10GeneralConfiguration.DefenderPotentiallyUnwantedAppActionSetting 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/config/defaprotection

### <a name="windows10generalconfigurationdefenderprocessestoexclude"></a>Windows10GeneralConfiguration. DefenderProcessesToExclude 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Defender/ExcludedProcesses

### <a name="windows10generalconfigurationdefenderpromptforsamplesubmission"></a>Windows10GeneralConfiguration.DefenderPromptForSampleSubmission 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Defender/SubmitSamplesConsent

### <a name="windows10generalconfigurationdefenderrequirebehaviormonitoring"></a>Windows10GeneralConfiguration. Defenderrequiremonitoring 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/config/defendermonitoring

### <a name="windows10generalconfigurationdefenderrequirecloudprotection"></a>Windows10GeneralConfiguration.DefenderRequireCloudProtection 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/config/defenderprotection

### <a name="windows10generalconfigurationdefenderrequirenetworkinspectionsystem"></a>Windows10GeneralConfiguration.DefenderRequireNetworkInspectionSystem 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Defender/AllowIntrusionPreventionSystem

### <a name="windows10generalconfigurationdefenderrequirerealtimemonitoring"></a>Windows10GeneralConfiguration.DefenderRequireRealTimeMonitoring 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Defender/AllowRealtimeMonitoring

### <a name="windows10generalconfigurationdefenderscanarchivefiles"></a>Windows10GeneralConfiguration. Defenderscanアーカイブファイル 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Defender/allowアーカイブ

### <a name="windows10generalconfigurationdefenderscandownloads"></a>Windows10GeneralConfiguration のダウンロード 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Def/合金保護

### <a name="windows10generalconfigurationdefenderscanincomingmail"></a>Windows10GeneralConfiguration.DefenderScanIncomingMail 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Defender/AllowScanningNetworkFiles

### <a name="windows10generalconfigurationdefenderscanmappednetworkdrivesduringfullscan"></a>Windows10GeneralConfiguration.DefenderScanMappedNetworkDrivesDuringFullScan 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Defender/AllowFullScanOnMappedNetworkDrives

### <a name="windows10generalconfigurationdefenderscanmaxcpu"></a>Windows10GeneralConfiguration. DefenderScanMaxCpu 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Defender/AvgCPULoadFactor

### <a name="windows10generalconfigurationdefenderscannetworkfiles"></a>Windows10GeneralConfiguration. DefenderScanNetworkFiles 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Defender/AllowScanningNetworkFiles

### <a name="windows10generalconfigurationdefenderscanremovabledrivesduringfullscan"></a>Windows10GeneralConfiguration.DefenderScanRemovableDrivesDuringFullScan 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Defender/AllowFullScanRemovableDriveScanning

### <a name="windows10generalconfigurationdefenderscanscriptsloadedininternetexplorer"></a>Windows10GeneralConfiguration.DefenderScanScriptsLoadedInInternetExplorer 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/defenderscanning

### <a name="windows10generalconfigurationdefenderscantype"></a>Windows10GeneralConfiguration. DefenderScanType 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Defender/ScanParameter

### <a name="windows10generalconfigurationdefenderscheduledquickscantime"></a>Windows10GeneralConfiguration. DefenderScheduledQuickScanTime 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Defender/ScheduleQuickScanTime

### <a name="windows10generalconfigurationdefenderscheduledscantime"></a>Windows10GeneralConfiguration. DefenderScheduledScanTime 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Defender/ScheduleScanTime

### <a name="windows10generalconfigurationdefenderschedulescanday"></a>Windows10GeneralConfiguration.DefenderScheduleScanDay 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Defender/ScheduleScanDay

### <a name="windows10generalconfigurationdefendersignatureupdateintervalinhours"></a>Windows10GeneralConfiguration. DefenderSignatureUpdateIntervalInHours 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/config/Def/signatureupdateinterval

### <a name="windows10generalconfigurationdefendersubmitsamplesconsenttype"></a>Windows10GeneralConfiguration.DefenderSubmitSamplesConsentType 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Defender/SubmitSamplesConsent

### <a name="windows10generalconfigurationdefendersystemscanschedule"></a>Windows10GeneralConfiguration. DefenderSystemScanSchedule 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Defender/ScheduleScanDay

### <a name="windows10generalconfigurationdeveloperunlocksetting"></a>Windows10GeneralConfiguration.DeveloperUnlockSetting 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/ApplicationManagement/AllowDeveloperUnlock

### <a name="windows10generalconfigurationdevicemanagementblockfactoryresetonmobile"></a>Windows10GeneralConfiguration.DeviceManagementBlockFactoryResetOnMobile 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/dns setphone

### <a name="windows10generalconfigurationdevicemanagementblockmanualunenroll"></a>Windows10GeneralConfiguration. DeviceManagementBlockManualUnenroll 解除 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Experience/AllowManualMDMUnenrollment

### <a name="windows10generalconfigurationdiagnosticsdatasubmissionmode"></a>Windows10GeneralConfiguration.DiagnosticsDataSubmissionMode 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/systemテレメトリ

### <a name="windows10generalconfigurationdisplayapplistwithgdidpiscalingturnedoff"></a>Windows10GeneralConfiguration.DisplayAppListWithGdiDPIScalingTurnedOff 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Display/TurnOffGdiDPIScalingForApps

### <a name="windows10generalconfigurationdisplayapplistwithgdidpiscalingturnedon"></a>Windows10GeneralConfiguration.DisplayAppListWithGdiDPIScalingTurnedOn 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Display/TurnOnGdiDPIScalingForApps

### <a name="windows10generalconfigurationedgeallowstartpagesmodification"></a>Windows10GeneralConfiguration.EdgeAllowStartPagesModification 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Browser/HomePages

### <a name="windows10generalconfigurationedgeblockaccesstoaboutflags"></a>Windows10GeneralConfiguration.EdgeBlockAccessToAboutFlags 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Browser/PreventAccessToAboutFlagsInMicrosoftEdge

### <a name="windows10generalconfigurationedgeblockaddressbardropdown"></a>Windows10GeneralConfiguration.EdgeBlockAddressBarDropdown 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Browser/AllowAddressBarDropdown

### <a name="windows10generalconfigurationedgeblockautofill"></a>Windows10GeneralConfiguration.EdgeBlockAutofill 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/オートフィル

### <a name="windows10generalconfigurationedgeblockcompatibilitylist"></a>Windows10GeneralConfiguration.EdgeBlockCompatibilityList 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/ブラウザー/allowmicrosoft 互換性リスト

### <a name="windows10generalconfigurationedgeblockdevelopertools"></a>Windows10GeneralConfiguration.EdgeBlockDeveloperTools 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Browser/AllowDeveloperTools

### <a name="windows10generalconfigurationedgeblocked"></a>Windows10GeneralConfiguration.EdgeBlocked 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/ブラウザー/allowbrowser

### <a name="windows10generalconfigurationedgeblockeditfavorites"></a>Windows10GeneralConfiguration.EdgeBlockEditFavorites 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/ブラウザー/lockdownfavorites

### <a name="windows10generalconfigurationedgeblockextensions"></a>Windows10GeneralConfiguration.EdgeBlockExtensions 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/browserextensions

### <a name="windows10generalconfigurationedgeblockfullscreenmode"></a>Windows10GeneralConfiguration.EdgeBlockFullScreenMode 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Browser/AllowFullScreenMode

### <a name="windows10generalconfigurationedgeblockinprivatebrowsing"></a>Windows10GeneralConfiguration.EdgeBlockInPrivateBrowsing 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Browser/allowinprivate

### <a name="windows10generalconfigurationedgeblocklivetiledatacollection"></a>Windows10GeneralConfiguration.EdgeBlockLiveTileDataCollection 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Browser/PreventLiveTileDataCollection

### <a name="windows10generalconfigurationedgeblockpasswordmanager"></a>Windows10GeneralConfiguration.EdgeBlockPasswordManager 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Browser/allowpasswordmanager

### <a name="windows10generalconfigurationedgeblockpopups"></a>Windows10GeneralConfiguration.EdgeBlockPopups 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/allowpopup

### <a name="windows10generalconfigurationedgeblockprelaunch"></a>Windows10GeneralConfiguration.EdgeBlockPrelaunch 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/allow事前起動

### <a name="windows10generalconfigurationedgeblockprinting"></a>Windows10GeneralConfiguration.EdgeBlockPrinting 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/ブラウザー/allow印刷

### <a name="windows10generalconfigurationedgeblocksavinghistory"></a>Windows10GeneralConfiguration.EdgeBlockSavingHistory 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Browser/AllowSavingHistory

### <a name="windows10generalconfigurationedgeblocksearchsuggestions"></a>Windows10GeneralConfiguration.EdgeBlockSearchSuggestions 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Browser/AllowSearchSuggestionsinAddressBar

### <a name="windows10generalconfigurationedgeblocksendingdonottrackheader"></a>Windows10GeneralConfiguration.EdgeBlockSendingDoNotTrackHeader 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/browsertrack

### <a name="windows10generalconfigurationedgeblocksendingintranettraffictointernetexplorer"></a>Windows10GeneralConfiguration.EdgeBlockSendingIntranetTrafficToInternetExplorer 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Browser/SendIntranetTraffictoInternetExplorer

### <a name="windows10generalconfigurationedgeblocksideloadingextensions"></a>Windows10GeneralConfiguration.EdgeBlockSideloadingExtensions 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/ブラウザー/allowsideloadingofextensions

### <a name="windows10generalconfigurationedgeblocktabpreloading"></a>Windows10GeneralConfiguration.EdgeBlockTabPreloading 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/allowtabプリロード

### <a name="windows10generalconfigurationedgeblockwebcontentonnewtabpage"></a>Windows10GeneralConfiguration.EdgeBlockWebContentOnNewTabPage 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Browser/AllowWebContentOnNewTabPage

### <a name="windows10generalconfigurationedgeclearbrowsingdataonexit"></a>Windows10GeneralConfiguration.EdgeClearBrowsingDataOnExit 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Browser/ClearBrowsingDataOnExit

### <a name="windows10generalconfigurationedgecookiepolicy"></a>Windows10GeneralConfiguration.EdgeCookiePolicy 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/allowcookies

### <a name="windows10generalconfigurationedgedisablefirstrunpage"></a>Windows10GeneralConfiguration.EdgeDisableFirstRunPage 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Browser/PreventFirstRunPage

### <a name="windows10generalconfigurationedgeenterprisemodesitelistlocation"></a>Windows10GeneralConfiguration.EdgeEnterpriseModeSiteListLocation 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Browser/EnterpriseSiteListServiceUrl

### <a name="windows10generalconfigurationedgefavoritesbarvisibility"></a>Windows10GeneralConfiguration.EdgeFavoritesBarVisibility 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Browser/ConfigureFavoritesBar

### <a name="windows10generalconfigurationedgefavoriteslistlocation"></a>Windows10GeneralConfiguration.EdgeFavoritesListLocation 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Browser/ProvisionFavorites

### <a name="windows10generalconfigurationedgefirstrunurl"></a>Windows10GeneralConfiguration.EdgeFirstRunUrl 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/browserstrunurl

### <a name="windows10generalconfigurationedgehomebuttonconfiguration"></a>Windows10GeneralConfiguration.EdgeHomeButtonConfiguration 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/dns/sethomebuttonurl

### <a name="windows10generalconfigurationedgehomebuttonconfigurationenabled"></a>Windows10GeneralConfiguration.EdgeHomeButtonConfigurationEnabled 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Browser/ConfigureHomeButton

### <a name="windows10generalconfigurationedgehomepageurls"></a>Windows10GeneralConfiguration.EdgeHomepageUrls 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/dns/sethomebuttonurl

### <a name="windows10generalconfigurationedgenewtabpageurl"></a>Windows10GeneralConfiguration.EdgeNewTabPageURL 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Browser/SetNewTabPageURL

### <a name="windows10generalconfigurationedgeopenswith"></a>Windows10GeneralConfiguration.EdgeOpensWith 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Browser/ConfigureOpenMicrosoftEdgeWith

### <a name="windows10generalconfigurationedgepreventcertificateerroroverride"></a>Windows10GeneralConfiguration.EdgePreventCertificateErrorOverride 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Browser/PreventCertErrorOverrides

### <a name="windows10generalconfigurationedgerequiresmartscreen"></a>Windows10GeneralConfiguration.EdgeRequireSmartScreen 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/ブラウザー/allowsmartscreen

### <a name="windows10generalconfigurationedgesearchengine"></a>Windows10GeneralConfiguration.EdgeSearchEngine 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Browser/SetDefaultSearchEngine

### <a name="windows10generalconfigurationedgesendintranettraffictointernetexplorer"></a>Windows10GeneralConfiguration.EdgeSendIntranetTrafficToInternetExplorer 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Browser/SendIntranetTraffictoInternetExplorer

### <a name="windows10generalconfigurationedgeshowmessagewhenopeninginternetexplorersites"></a>Windows10GeneralConfiguration.EdgeShowMessageWhenOpeningInternetExplorerSites 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Browser/ShowMessageWhenOpeningSitesInInternetExplorer

### <a name="windows10generalconfigurationedgesyncfavoriteswithinternetexplorer"></a>Windows10GeneralConfiguration.EdgeSyncFavoritesWithInternetExplorer 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Browser/SyncFavoritesBetweenIEAndMicrosoftEdge

### <a name="windows10generalconfigurationedgetelemetryformicrosoft365analytics"></a>Windows10GeneralConfiguration.EdgeTelemetryForMicrosoft365Analytics 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Browser/ConfigureTelemetryForMicrosoft365Analytics

### <a name="windows10generalconfigurationenableautomaticredeployment"></a>Windows10GeneralConfiguration 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/CredentialProviders/DisableAutomaticReDeploymentCredentials

### <a name="windows10generalconfigurationenterprisecloudprintdiscoveryendpoint"></a>Windows10GeneralConfiguration.EnterpriseCloudPrintDiscoveryEndPoint 
**CSP**:./User/Vendor/MSFT/Policy  
**オフセット URI**:/Config/EnterpriseCloudPrint/CloudPrinterDiscoveryEndPoint

### <a name="windows10generalconfigurationenterprisecloudprintdiscoverymaxlimit"></a>Windows10GeneralConfiguration.EnterpriseCloudPrintDiscoveryMaxLimit 
**CSP**:./User/Vendor/MSFT/Policy  
**オフセット URI**:/Config/EnterpriseCloudPrint/DiscoveryMaxPrinterLimit

### <a name="windows10generalconfigurationenterprisecloudprintmopriadiscoveryresourceidentifier"></a>Windows10GeneralConfiguration.EnterpriseCloudPrintMopriaDiscoveryResourceIdentifier 
**CSP**:./User/Vendor/MSFT/Policy  
**オフセット URI**:/Config/EnterpriseCloudPrint/MopriaDiscoveryResourceId

### <a name="windows10generalconfigurationenterprisecloudprintoauthauthority"></a>Windows10GeneralConfiguration.EnterpriseCloudPrintOAuthAuthority 
**CSP**:./User/Vendor/MSFT/Policy  
**オフセット URI**:/Config/EnterpriseCloudPrint/CloudPrintOAuthAuthority

### <a name="windows10generalconfigurationenterprisecloudprintoauthclientidentifier"></a>Windows10GeneralConfiguration.EnterpriseCloudPrintOAuthClientIdentifier 
**CSP**:./User/Vendor/MSFT/Policy  
**オフセット URI**:/Config/EnterpriseCloudPrint/CloudPrintOAuthAuthority

### <a name="windows10generalconfigurationenterprisecloudprintresourceidentifier"></a>Windows10GeneralConfiguration.EnterpriseCloudPrintResourceIdentifier 
**CSP**:./User/Vendor/MSFT/Policy  
**オフセット URI**:/Config/EnterpriseCloudPrint/CloudPrintResourceId

### <a name="windows10generalconfigurationexperienceblockconsumerspecificfeatures"></a>Windows10GeneralConfiguration.ExperienceBlockConsumerSpecificFeatures 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Experience/AllowWindowsConsumerFeatures

### <a name="windows10generalconfigurationexperienceblockdevicediscovery"></a>Windows10GeneralConfiguration.ExperienceBlockDeviceDiscovery 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Experience/AllowDeviceDiscovery

### <a name="windows10generalconfigurationexperienceblockerrordialogwhennosim"></a>Windows10GeneralConfiguration.ExperienceBlockErrorDialogWhenNoSIM 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Experience/AllowSIMErrorDialogPromptWhenNoSIM

### <a name="windows10generalconfigurationexperienceblocktaskswitcher"></a>Windows10GeneralConfiguration.ExperienceBlockTaskSwitcher 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Experience/AllowTaskSwitcher

### <a name="windows10generalconfigurationexperienceblockwindowsspotlight"></a>Windows10GeneralConfiguration.ExperienceBlockWindowsSpotlight 
**CSP**:./User/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Experience/AllowWindowsSpotlight

### <a name="windows10generalconfigurationexperiencedonotsyncbrowsersettings"></a>Windows10GeneralConfiguration.ExperienceDoNotSyncBrowserSettings 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Experience/DoNotSyncBrowserSettings

### <a name="windows10generalconfigurationgamedvrblocked"></a>ブロックされた Windows10GeneralConfiguration 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Applicationmanagement/allowの場合

### <a name="windows10generalconfigurationhardwaredeviceinstallationbydeviceidentifiers"></a>Windows10GeneralConfiguration.HardwareDeviceInstallationByDeviceIdentifiers 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/DeviceInstallation/PreventInstallationOfMatchingDeviceIDs

### <a name="windows10generalconfigurationhardwaredeviceinstallationbysetupclasses"></a>Windows10GeneralConfiguration Deviceinstallationbysetupclasses 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/DeviceInstallation/PreventInstallationOfMatchingDeviceSetupClasses

### <a name="windows10generalconfigurationinkworkspaceaccess"></a>Windows10GeneralConfiguration.InkWorkspaceAccess 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/WindowsInkWorkspace/AllowWindowsInkWorkspace

### <a name="windows10generalconfigurationinkworkspaceaccessstate"></a>Windows10GeneralConfiguration.InkWorkspaceAccessState 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/WindowsInkWorkspace/AllowWindowsInkWorkspace

### <a name="windows10generalconfigurationinkworkspaceblocksuggestedapps"></a>Windows10GeneralConfiguration.InkWorkspaceBlockSuggestedApps 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/WindowsInkWorkspace/AllowSuggestedAppsInWindowsInkWorkspace

### <a name="windows10generalconfigurationinternetexploreractivexcontrolsinprotectedmode"></a>Windows10GeneralConfiguration.InternetExplorerActiveXControlsInProtectedMode 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/DoNotAllowActiveXControlsInProtectedMode

### <a name="windows10generalconfigurationinternetexplorerautocomplete"></a>Windows10GeneralConfiguration.InternetExplorerAutoComplete 
**CSP**:./User/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/AllowAutoComplete

### <a name="windows10generalconfigurationinternetexplorerblockoutdatedactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerBlockOutdatedActiveXControls 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/DoNotBlockOutdatedActiveXControls

### <a name="windows10generalconfigurationinternetexplorerbypasssmartscreenwarnings"></a>Windows10GeneralConfiguration.InternetExplorerBypassSmartScreenWarnings 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/DisableBypassOfSmartScreenWarnings

### <a name="windows10generalconfigurationinternetexplorerbypasssmartscreenwarningsaboutuncommonfiles"></a>Windows10GeneralConfiguration.InternetExplorerBypassSmartScreenWarningsAboutUncommonFiles 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/DisableBypassOfSmartScreenWarningsAboutUncommonFiles

### <a name="windows10generalconfigurationinternetexplorercertificateaddressmismatchwarning"></a>Windows10GeneralConfiguration.InternetExplorerCertificateAddressMismatchWarning 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/AllowCertificateAddressMismatchWarning

### <a name="windows10generalconfigurationinternetexplorercheckservercertificaterevocation"></a>Windows10GeneralConfiguration.InternetExplorerCheckServerCertificateRevocation 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/CheckServerCertificateRevocation

### <a name="windows10generalconfigurationinternetexplorerchecksignaturesondownloadedprograms"></a>Windows10GeneralConfiguration.InternetExplorerCheckSignaturesOnDownloadedPrograms 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/CheckSignaturesOnDownloadedPrograms

### <a name="windows10generalconfigurationinternetexplorercrashdetection"></a>Windows10GeneralConfiguration.InternetExplorerCrashDetection 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/DisableCrashDetection

### <a name="windows10generalconfigurationinternetexplorerdisableprocessesinenhancedprotectedmode"></a>Windows10GeneralConfiguration.InternetExplorerDisableProcessesInEnhancedProtectedMode 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/DisableProcessesInEnhancedProtectedMode

### <a name="windows10generalconfigurationinternetexplorerdownloadenclosures"></a>Windows10GeneralConfiguration.InternetExplorerDownloadEnclosures 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/DisableEnclosureDownloading

### <a name="windows10generalconfigurationinternetexplorerencryptionsupport"></a>Windows10GeneralConfiguration.InternetExplorerEncryptionSupport 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/DisableEncryptionSupport

### <a name="windows10generalconfigurationinternetexplorerenhancedprotectedmode"></a>Windows10GeneralConfiguration.InternetExplorerEnhancedProtectedMode 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/AllowEnhancedProtectedMode

### <a name="windows10generalconfigurationinternetexplorerfallbacktossl3"></a>Windows10GeneralConfiguration.InternetExplorerFallbackToSsl3 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/AllowFallbackToSSL3

### <a name="windows10generalconfigurationinternetexplorerignorecertificateerrors"></a>Windows10GeneralConfiguration.InternetExplorerIgnoreCertificateErrors 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/DisableIgnoringCertificateErrors

### <a name="windows10generalconfigurationinternetexplorerincludeallnetworkpaths"></a>Windows10GeneralConfiguration.InternetExplorerIncludeAllNetworkPaths 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/IncludeAllNetworkPaths

### <a name="windows10generalconfigurationinternetexplorerinternetzoneaccesstodatasources"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneAccessToDataSources 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/InternetZoneAllowAccessToDataSources

### <a name="windows10generalconfigurationinternetexplorerinternetzoneallowonlyapproveddomainstouseactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneAllowOnlyApprovedDomainsToUseActiveXControls 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/InternetZoneAllowOnlyApprovedDomainsToUseActiveXControls

### <a name="windows10generalconfigurationinternetexplorerinternetzoneallowonlyapproveddomainstousetdcactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneAllowOnlyApprovedDomainsToUseTdcActiveXControls 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/InternetZoneAllowOnlyApprovedDomainsToUseTDCActiveXControl

### <a name="windows10generalconfigurationinternetexplorerinternetzoneallowvbscripttorun"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneAllowVBScriptToRun 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/InternetZoneAllowVBScriptToRunInInternetExplorer

### <a name="windows10generalconfigurationinternetexplorerinternetzoneautomaticpromptforfiledownloads"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneAutomaticPromptForFileDownloads 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/InternetZoneAllowAutomaticPromptingForFileDownloads

### <a name="windows10generalconfigurationinternetexplorerinternetzonecopyandpasteviascript"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneCopyAndPasteViaScript 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/InternetZoneAllowCopyPasteViaScript

### <a name="windows10generalconfigurationinternetexplorerinternetzonecrosssitescriptingfilter"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneCrossSiteScriptingFilter 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/InternetZoneEnableCrossSiteScriptingFilter

### <a name="windows10generalconfigurationinternetexplorerinternetzonedonotrunantimalwareagainstactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneDoNotRunAntimalwareAgainstActiveXControls 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/InternetZoneDoNotRunAntimalwareAgainstActiveXControls

### <a name="windows10generalconfigurationinternetexplorerinternetzonedotnetframeworkreliantcomponents"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneDotNetFrameworkReliantComponents 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/InternetZoneAllowNETFrameworkReliantComponents

### <a name="windows10generalconfigurationinternetexplorerinternetzonedownloadsignedactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneDownloadSignedActiveXControls 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/InternetZoneDownloadSignedActiveXControls

### <a name="windows10generalconfigurationinternetexplorerinternetzonedownloadunsignedactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneDownloadUnsignedActiveXControls 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/InternetZoneDownloadUnsignedActiveXControls

### <a name="windows10generalconfigurationinternetexplorerinternetzonedraganddroporcopyandpastefiles"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneDragAndDropOrCopyAndPasteFiles 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/InternetZoneAllowDragAndDropCopyAndPasteFiles

### <a name="windows10generalconfigurationinternetexplorerinternetzonedragcontentfromdifferentdomainsacrosswindows"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneDragContentFromDifferentDomainsAcrossWindows 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/InternetZoneEnableDraggingOfContentFromDifferentDomainsAcrossWindows

### <a name="windows10generalconfigurationinternetexplorerinternetzonedragcontentfromdifferentdomainswithinwindows"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneDragContentFromDifferentDomainsWithinWindows 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/InternetZoneEnableDraggingOfContentFromDifferentDomainsWithinWindows

### <a name="windows10generalconfigurationinternetexplorerinternetzoneincludelocalpathwhenuploadingfilestoserver"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneIncludeLocalPathWhenUploadingFilesToServer 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/InternetZoneIncludeLocalPathWhenUploadingFilesToServer

### <a name="windows10generalconfigurationinternetexplorerinternetzoneinitializeandscriptactivexcontrolsnotmarkedassafe"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneInitializeAndScriptActiveXControlsNotMarkedAsSafe 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/InternetZoneInitializeAndScriptActiveXControls

### <a name="windows10generalconfigurationinternetexplorerinternetzonejavapermissions"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneJavaPermissions 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/InternetZoneJavaPermissions


### <a name="windows10generalconfigurationinternetexplorerinternetzonelaunchapplicationsandfilesinaniframe"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneLaunchApplicationsAndFilesInAnIFrame 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/InternetZoneLaunchingApplicationsAndFilesInIFRAME

### <a name="windows10generalconfigurationinternetexplorerinternetzonelessprivilegedsites"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneLessPrivilegedSites 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/InternetZoneAllowLessPrivilegedSites

### <a name="windows10generalconfigurationinternetexplorerinternetzoneloadingofxamlfiles"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneLoadingOfXamlFiles 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/InternetZoneAllowLoadingOfXAMLFiles

### <a name="windows10generalconfigurationinternetexplorerinternetzonelogonoptions"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneLogonOptions 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/InternetZoneLogonOptions

### <a name="windows10generalconfigurationinternetexplorerinternetzonenavigatewindowsandframesacrossdifferentdomains"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneNavigateWindowsAndFramesAcrossDifferentDomains 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/InternetZoneNavigateWindowsAndFrames

### <a name="windows10generalconfigurationinternetexplorerinternetzonepopupblocker"></a>Windows10GeneralConfiguration.InternetExplorerInternetZonePopupBlocker 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/InternetZoneUsePopupBlocker

### <a name="windows10generalconfigurationinternetexplorerinternetzoneprotectedmode"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneProtectedMode 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/InternetZoneEnableProtectedMode

### <a name="windows10generalconfigurationinternetexplorerinternetzonerundotnetframeworkreliantcomponentssignedwithauthenticode"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneRunDotNetFrameworkReliantComponentsSignedWithAuthenticode 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/InternetZoneRunNETFrameworkReliantComponentsSignedWithAuthenticode

### <a name="windows10generalconfigurationinternetexplorerinternetzonescriptingofwebbrowsercontrols"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneScriptingOfWebBrowserControls 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/InternetZoneAllowScriptingOfInternetExplorerWebBrowserControls

### <a name="windows10generalconfigurationinternetexplorerinternetzonescriptinitiatedwindows"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneScriptInitiatedWindows 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/InternetZoneAllowScriptInitiatedWindows

### <a name="windows10generalconfigurationinternetexplorerinternetzonescriptlets"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneScriptlets 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/InternetZoneAllowScriptlets

### <a name="windows10generalconfigurationinternetexplorerinternetzonesecuritywarningforpotentiallyunsafefiles"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneSecurityWarningForPotentiallyUnsafeFiles 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/InternetZoneShowSecurityWarningForPotentiallyUnsafeFiles

### <a name="windows10generalconfigurationinternetexplorerinternetzonesmartscreen"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneSmartScreen 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/InternetZoneAllowSmartScreenIE

### <a name="windows10generalconfigurationinternetexplorerinternetzoneupdatestostatusbarviascript"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneUpdatesToStatusBarViaScript 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/InternetZoneAllowUpdatesToStatusBarViaScript

### <a name="windows10generalconfigurationinternetexplorerinternetzoneuserdatapersistence"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneUserDataPersistence 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/InternetZoneAllowUserDataPersistence

### <a name="windows10generalconfigurationinternetexplorerintranetzonedonotrunantimalwareagainstactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerIntranetZoneDoNotRunAntimalwareAgainstActiveXControls 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/IntranetZoneDoNotRunAntimalwareAgainstActiveXControls

### <a name="windows10generalconfigurationinternetexplorerintranetzoneinitializeandscriptactivexcontrolsnotmarkedassafe"></a>Windows10GeneralConfiguration.InternetExplorerIntranetZoneInitializeAndScriptActiveXControlsNotMarkedAsSafe 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/IntranetZoneInitializeAndScriptActiveXControls

### <a name="windows10generalconfigurationinternetexplorerintranetzonejavapermissions"></a>Windows10GeneralConfiguration.InternetExplorerIntranetZoneJavaPermissions 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/IntranetZoneJavaPermissions

### <a name="windows10generalconfigurationinternetexplorerlocalmachinezonedonotrunantimalwareagainstactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerLocalMachineZoneDoNotRunAntimalwareAgainstActiveXControls 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/LocalMachineZoneDoNotRunAntimalwareAgainstActiveXControls

### <a name="windows10generalconfigurationinternetexplorerlocalmachinezonejavapermissions"></a>Windows10GeneralConfiguration.InternetExplorerLocalMachineZoneJavaPermissions 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/LocalMachineZoneJavaPermissions

### <a name="windows10generalconfigurationinternetexplorerlockeddowninternetzonesmartscreen"></a>Windows10GeneralConfiguration.InternetExplorerLockedDownInternetZoneSmartScreen 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/LockedDownInternetZoneAllowSmartScreenIE

### <a name="windows10generalconfigurationinternetexplorerlockeddownintranetzonejavapermissions"></a>Windows10GeneralConfiguration.InternetExplorerLockedDownIntranetZoneJavaPermissions 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/LockedDownIntranetJavaPermissions

### <a name="windows10generalconfigurationinternetexplorerlockeddownlocalmachinezonejavapermissions"></a>Windows10GeneralConfiguration.InternetExplorerLockedDownLocalMachineZoneJavaPermissions 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/LockedDownLocalMachineZoneJavaPermissions

### <a name="windows10generalconfigurationinternetexplorerlockeddownrestrictedzonejavapermissions"></a>Windows10GeneralConfiguration.InternetExplorerLockedDownRestrictedZoneJavaPermissions 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/LockedDownRestrictedSitesZoneJavaPermissions

### <a name="windows10generalconfigurationinternetexplorerlockeddownrestrictedzonesmartscreen"></a>Windows10GeneralConfiguration.InternetExplorerLockedDownRestrictedZoneSmartScreen 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/LockedDownRestrictedSitesZoneAllowSmartScreenIE

### <a name="windows10generalconfigurationinternetexplorerlockeddowntrustedzonejavapermissions"></a>Windows10GeneralConfiguration.InternetExplorerLockedDownTrustedZoneJavaPermissions 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/LockedDownTrustedSitesZoneJavaPermissions

### <a name="windows10generalconfigurationinternetexplorerpreventmanagingsmartscreenfilter"></a>Windows10GeneralConfiguration.InternetExplorerPreventManagingSmartScreenFilter 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/PreventManagingSmartScreenFilter

### <a name="windows10generalconfigurationinternetexplorerpreventperuserinstallationofactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerPreventPerUserInstallationOfActiveXControls 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/PreventPerUserInstallationOfActiveXControls

### <a name="windows10generalconfigurationinternetexplorerprocessesconsistentmimehandling"></a>Windows10GeneralConfiguration.InternetExplorerProcessesConsistentMimeHandling 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/ConsistentMimeHandlingInternetExplorerProcesses

### <a name="windows10generalconfigurationinternetexplorerprocessesmimesniffingsafetyfeature"></a>Windows10GeneralConfiguration.InternetExplorerProcessesMimeSniffingSafetyFeature 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/MimeSniffingSafetyFeatureInternetExplorerProcesses

### <a name="windows10generalconfigurationinternetexplorerprocessesmkprotocolsecurityrestriction"></a>Windows10GeneralConfiguration.InternetExplorerProcessesMKProtocolSecurityRestriction 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/MKProtocolSecurityRestrictionInternetExplorerProcesses

### <a name="windows10generalconfigurationinternetexplorerprocessesnotificationbar"></a>Windows10GeneralConfiguration.InternetExplorerProcessesNotificationBar 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/NotificationBarInternetExplorerProcesses

### <a name="windows10generalconfigurationinternetexplorerprocessesprotectionfromzoneelevation"></a>Windows10GeneralConfiguration.InternetExplorerProcessesProtectionFromZoneElevation 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/ProtectionFromZoneElevationInternetExplorerProcesses

### <a name="windows10generalconfigurationinternetexplorerprocessesrestrictactivexinstall"></a>Windows10GeneralConfiguration.InternetExplorerProcessesRestrictActiveXInstall 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/RestrictActiveXInstallInternetExplorerProcesses

### <a name="windows10generalconfigurationinternetexplorerprocessesrestrictfiledownload"></a>Windows10GeneralConfiguration.InternetExplorerProcessesRestrictFileDownload 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/RestrictFileDownloadInternetExplorerProcesses

### <a name="windows10generalconfigurationinternetexplorerprocessesscriptedwindowsecurityrestrictions"></a>Windows10GeneralConfiguration.InternetExplorerProcessesScriptedWindowSecurityRestrictions 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/ScriptedWindowSecurityRestrictionsInternetExplorerProcesses

### <a name="windows10generalconfigurationinternetexplorerremoverunthistimebuttonforoutdatedactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerRemoveRunThisTimeButtonForOutdatedActiveXControls 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/RemoveRunThisTimeButtonForOutdatedActiveXControls

### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneaccesstodatasources"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneAccessToDataSources 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/RestrictedSitesZoneAllowAccessToDataSources

### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneactivescripting"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneActiveScripting 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/RestrictedSitesZoneAllowActiveScripting

### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneallowonlyapproveddomainstouseactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneAllowOnlyApprovedDomainsToUseActiveXControls 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/RestrictedSitesZoneAllowOnlyApprovedDomainsToUseActiveXControls

### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneallowonlyapproveddomainstousetdcactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneAllowOnlyApprovedDomainsToUseTdcActiveXControls 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/RestrictedSitesZoneAllowOnlyApprovedDomainsToUseTDCActiveXControl

### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneallowvbscripttorun"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneAllowVBScriptToRun 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/RestrictedSitesZoneAllowVBScriptToRunInInternetExplorer

### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneautomaticpromptforfiledownloads"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneAutomaticPromptForFileDownloads 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/RestrictedSitesZoneAllowAutomaticPromptingForFileDownloads

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonebinaryandscriptbehaviors"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneBinaryAndScriptBehaviors 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/RestrictedSitesZoneAllowBinaryAndScriptBehaviors

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonecopyandpasteviascript"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneCopyAndPasteViaScript 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/RestrictedSitesZoneAllowCopyPasteViaScript

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonecrosssitescriptingfilter"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneCrossSiteScriptingFilter 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/RestrictedSitesZoneEnableCrossSiteScriptingFilter

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonedonotrunantimalwareagainstactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneDoNotRunAntimalwareAgainstActiveXControls 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/RestrictedSitesZoneDoNotRunAntimalwareAgainstActiveXControls

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonedotnetframeworkreliantcomponents"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneDotNetFrameworkReliantComponents 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/RestrictedSitesZoneAllowNETFrameworkReliantComponents

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonedownloadsignedactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneDownloadSignedActiveXControls 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/RestrictedSitesZoneDownloadSignedActiveXControls

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonedownloadunsignedactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneDownloadUnsignedActiveXControls 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/RestrictedSitesZoneDownloadUnsignedActiveXControls

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonedraganddroporcopyandpastefiles"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneDragAndDropOrCopyAndPasteFiles 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/RestrictedSitesZoneAllowDragAndDropCopyAndPasteFiles

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonedragcontentfromdifferentdomainsacrosswindows"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneDragContentFromDifferentDomainsAcrossWindows 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/RestrictedSitesZoneEnableDraggingOfContentFromDifferentDomainsAcrossWindows

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonedragcontentfromdifferentdomainswithinwindows"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneDragContentFromDifferentDomainsWithinWindows 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/RestrictedSitesZoneEnableDraggingOfContentFromDifferentDomainsWithinWindows

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonefiledownloads"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneFileDownloads 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/RestrictedSitesZoneAllowFileDownloads

### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneincludelocalpathwhenuploadingfilestoserver"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneIncludeLocalPathWhenUploadingFilesToServer 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/RestrictedSitesZoneIncludeLocalPathWhenUploadingFilesToServer

### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneinitializeandscriptactivexcontrolsnotmarkedassafe"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneInitializeAndScriptActiveXControlsNotMarkedAsSafe 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/RestrictedSitesZoneInitializeAndScriptActiveXControls

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonejavapermissions"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneJavaPermissions 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/RestrictedSitesZoneJavaPermissions

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonelaunchapplicationsandfilesinaniframe"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneLaunchApplicationsAndFilesInAnIFrame 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/RestrictedSitesZoneLaunchingApplicationsAndFilesInIFRAME

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonelessprivilegedsites"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneLessPrivilegedSites 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/RestrictedSitesZoneAllowLessPrivilegedSites

### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneloadingofxamlfiles"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneLoadingOfXamlFiles 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/RestrictedSitesZoneAllowLoadingOfXAMLFiles

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonelogonoptions"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneLogonOptions 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/RestrictedSitesZoneLogonOptions

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonemetarefresh"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneMetaRefresh 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/RestrictedSitesZoneAllowMETAREFRESH

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonenavigatewindowsandframesacrossdifferentdomains"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneNavigateWindowsAndFramesAcrossDifferentDomains 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/RestrictedSitesZoneNavigateWindowsAndFrames

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonepopupblocker"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZonePopupBlocker 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/RestrictedSitesZoneUsePopupBlocker

### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneprotectedmode"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneProtectedMode 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/RestrictedSitesZoneTurnOnProtectedMode

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonerunactivexcontrolsandplugins"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneRunActiveXControlsAndPlugins 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/RestrictedSitesZoneRunActiveXControlsAndPlugins

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonerundotnetframeworkreliantcomponentssignedwithauthenticode"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneRunDotNetFrameworkReliantComponentsSignedWithAuthenticode 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/RestrictedSitesZoneRunNETFrameworkReliantComponentsSignedWithAuthenticode

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonescriptactivexcontrolsmarkedsafeforscripting"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneScriptActiveXControlsMarkedSafeForScripting 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/RestrictedSitesZoneScriptActiveXControlsMarkedSafeForScripting

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonescriptingofjavaapplets"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneScriptingOfJavaApplets 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/RestrictedSitesZoneScriptingOfJavaApplets

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonescriptingofwebbrowsercontrols"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneScriptingOfWebBrowserControls 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/RestrictedSitesZoneAllowScriptingOfInternetExplorerWebBrowserControls

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonescriptinitiatedwindows"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneScriptInitiatedWindows 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/RestrictedSitesZoneAllowScriptInitiatedWindows

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonescriptlets"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneScriptlets 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/RestrictedSitesZoneAllowScriptlets

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonesecuritywarningforpotentiallyunsafefiles"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneSecurityWarningForPotentiallyUnsafeFiles 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/RestrictedSitesZoneShowSecurityWarningForPotentiallyUnsafeFiles

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonesmartscreen"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneSmartScreen 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/RestrictedSitesZoneAllowSmartScreenIE

### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneupdatestostatusbarviascript"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneUpdatesToStatusBarViaScript 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/RestrictedSitesZoneAllowUpdatesToStatusBarViaScript

### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneuserdatapersistence"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneUserDataPersistence 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/RestrictedSitesZoneAllowUserDataPersistence

### <a name="windows10generalconfigurationinternetexplorersecuritysettingscheck"></a>Windows10GeneralConfiguration.InternetExplorerSecuritySettingsCheck 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/DisableSecuritySettingsCheck

### <a name="windows10generalconfigurationinternetexplorersecurityzonesuseonlymachinesettings"></a>Windows10GeneralConfiguration.InternetExplorerSecurityZonesUseOnlyMachineSettings 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/SecurityZonesUseOnlyMachineSettings

### <a name="windows10generalconfigurationinternetexplorersoftwarewhensignatureisinvalid"></a>Windows10GeneralConfiguration.InternetExplorerSoftwareWhenSignatureIsInvalid 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/AllowSoftwareWhenSignatureIsInvalid

### <a name="windows10generalconfigurationinternetexplorertrustedzonedonotrunantimalwareagainstactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerTrustedZoneDoNotRunAntimalwareAgainstActiveXControls 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/TrustedSitesZoneDoNotRunAntimalwareAgainstActiveXControls

### <a name="windows10generalconfigurationinternetexplorertrustedzoneinitializeandscriptactivexcontrolsnotmarkedassafe"></a>Windows10GeneralConfiguration.InternetExplorerTrustedZoneInitializeAndScriptActiveXControlsNotMarkedAsSafe 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/TrustedSitesZoneInitializeAndScriptActiveXControls

### <a name="windows10generalconfigurationinternetexplorertrustedzonejavapermissions"></a>Windows10GeneralConfiguration.InternetExplorerTrustedZoneJavaPermissions 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/TrustedSitesZoneJavaPermissions

### <a name="windows10generalconfigurationinternetexploreruseactivexinstallerservice"></a>Windows10GeneralConfiguration.InternetExplorerUseActiveXInstallerService 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/SpecifyUseOfActiveXInstallerService

### <a name="windows10generalconfigurationinternetexplorerusersaddingsites"></a>Windows10GeneralConfiguration.InternetExplorerUsersAddingSites 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/DoNotAllowUsersToAddSites

### <a name="windows10generalconfigurationinternetexploreruserschangingpolicies"></a>Windows10GeneralConfiguration.InternetExplorerUsersChangingPolicies 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/InternetExplorer/DoNotAllowUsersToChangePolicies

### <a name="windows10generalconfigurationinternetsharingblocked"></a>Windows10GeneralConfiguration がブロックされました 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/WiFi/AllowInternetSharing

### <a name="windows10generalconfigurationlocationservicesblocked"></a>Windows10GeneralConfiguration がブロックされました 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/system/allowlocation

### <a name="windows10generalconfigurationlockscreenallowtimeoutconfiguration"></a>Windows10GeneralConfiguration. LockScreenAllowTimeoutConfiguration 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/DeviceLock/AllowScreenTimeoutWhileLockedUser/Config

### <a name="windows10generalconfigurationlockscreenblockactioncenternotifications"></a>Windows10GeneralConfiguration 通知のロック 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/AboveLock/AllowActionCenterNotifications

### <a name="windows10generalconfigurationlockscreenblockcortana"></a>Windows10GeneralConfiguration. LockScreenBlockCortana 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/AboveLock/AllowCortanaAboveLock

### <a name="windows10generalconfigurationlockscreenblocktoastnotifications"></a>Windows10GeneralConfiguration 通知 (LockScreenBlockToastNotifications) 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/AboveLock/AllowToasts

### <a name="windows10generalconfigurationlockscreencamera"></a>Windows10GeneralConfiguration.LockScreenCamera 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/DeviceLock/PreventEnablingLockScreenCamera

### <a name="windows10generalconfigurationlockscreenhidenetworkselectionui"></a>Windows10GeneralConfiguration.LockScreenHideNetworkSelectionUI 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/WindowsLogon/DontDisplayNetworkSelectionUI

### <a name="windows10generalconfigurationlockscreenslideshow"></a>Windows10GeneralConfiguration 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/DeviceLock/PreventLockScreenSlideShow

### <a name="windows10generalconfigurationlockscreentimeoutinseconds"></a>Windows10GeneralConfiguration.LockScreenTimeoutInSeconds 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/DeviceLock/ScreenTimeoutWhileLocked

### <a name="windows10generalconfigurationlogonblockfastuserswitching"></a>Windows10GeneralConfiguration Fastuser交代 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/windowslogonastuser切り替わる

### <a name="windows10generalconfigurationmessagingblockmms"></a>Windows10GeneralConfiguration (Mms) 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Messaging/allowmms

### <a name="windows10generalconfigurationmessagingblockrichcommunicationservices"></a>Windows10GeneralConfiguration.MessagingBlockRichCommunicationServices 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/config/Messaging/allowrcs

### <a name="windows10generalconfigurationmessagingblocksync"></a>Windows10GeneralConfiguration Sync 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Messaging/AllowMessageSync

### <a name="windows10generalconfigurationmicrosoftaccountblocked"></a>Windows10GeneralConfiguration 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Accounts/AllowMicrosoftAccountConnection

### <a name="windows10generalconfigurationmicrosoftaccountblocksettingssync"></a>Windows10GeneralConfiguration. Microsoft Accountblocksettingssync 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Experience/AllowSyncMySettings

### <a name="windows10generalconfigurationmicrosoftaccountsigninassistantsettings"></a>Windows10GeneralConfiguration.MicrosoftAccountSignInAssistantSettings 
**CSP**:./Device/Vendor/MSFT/Accounts  
**オフセット URI**:/AllowMicrosoftAccountSignInAssistant

### <a name="windows10generalconfigurationnetworkproxyapplysettingsdevicewide"></a>Windows10GeneralConfiguration. NetworkProxyApplySettingsDeviceWide 
**CSP**:./Device/Vendor/MSFT/NetworkProxy  
**オフセット URI**:/ProxySettingsPerUser

### <a name="windows10generalconfigurationnetworkproxyautomaticconfigurationurl"></a>Windows10GeneralConfiguration.NetworkProxyAutomaticConfigurationUrl 
**CSP**:./Device/Vendor/MSFT/NetworkProxy  
**オフセット URI**:/setupscripturl

### <a name="windows10generalconfigurationnetworkproxydisableautodetect"></a>Windows10GeneralConfiguration 自動検出 
**CSP**:./Device/Vendor/MSFT/NetworkProxy  
**オフセット URI**:/AutoDetect

### <a name="windows10generalconfigurationnetworkproxyserver"></a>Windows10GeneralConfiguration.NetworkProxyServer 
**CSP**:./Vendor/MSFT/NetworkProxy  
**オフセット URI**:/ProxyAddress,/例外と/UseProxyForLocalAddresses

### <a name="windows10generalconfigurationnfcblocked"></a>Windows10GeneralConfiguration 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Connectivity/AllowNFC

### <a name="windows10generalconfigurationonedrivedisablefilesync"></a>Windows10GeneralConfiguration.OneDriveDisableFileSync 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/System/DisableOneDriveFileSync

### <a name="windows10generalconfigurationpasswordblocksimple"></a>Windows10GeneralConfiguration 単純 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/config/Devicelock/allowsimpledevicepassword

### <a name="windows10generalconfigurationpasswordexpirationdays"></a>Windows10GeneralConfiguration.PasswordExpirationDays 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/DeviceLock/DevicePasswordExpiration

### <a name="windows10generalconfigurationpasswordminimumageindays"></a>Windows10GeneralConfiguration. PasswordMinimumAgeInDays 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Dns/configpasswordage

### <a name="windows10generalconfigurationpasswordminimumcharactersetcount"></a>Windows10GeneralConfiguration Setcount 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Devicelock/mindevicepasswordcomplexcharacters

### <a name="windows10generalconfigurationpasswordminimumlength"></a>Windows10GeneralConfiguration 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/config/Devicelock/mindevicepasswordlength

### <a name="windows10generalconfigurationpasswordminutesofinactivitybeforescreentimeout"></a>Windows10GeneralConfiguration.PasswordMinutesOfInactivityBeforeScreenTimeout 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/DeviceLock/MaxInactivityTimeDeviceLock

### <a name="windows10generalconfigurationpasswordpreviouspasswordblockcount"></a>Windows10GeneralConfiguration.PasswordPreviousPasswordBlockCount 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/config/Devicelock/devicepasswordhistory

### <a name="windows10generalconfigurationpasswordrequired"></a>Windows10GeneralConfiguration が必要です 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/config/dns/devicepasswordenabled

### <a name="windows10generalconfigurationpasswordrequiredtype"></a>Windows10GeneralConfiguration. PasswordRequiredType 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/DeviceLock/AlphanumericDevicePasswordRequired

### <a name="windows10generalconfigurationpasswordrequirewhenresumefromidlestate"></a>Windows10GeneralConfiguration.PasswordRequireWhenResumeFromIdleState 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/DeviceLock/AllowIdleReturnWithoutPassword

### <a name="windows10generalconfigurationpasswordsigninfailurecountbeforefactoryreset"></a>Windows10GeneralConfiguration.PasswordSignInFailureCountBeforeFactoryReset 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/DeviceLock/MaxDevicePasswordFailedAttempts

### <a name="windows10generalconfigurationpersonalizationdesktopimageurl"></a>Windows10GeneralConfiguration。 
**CSP**:./Device/Vendor/MSFT/Personalization  
**オフセット URI**:/desktopimageurl

### <a name="windows10generalconfigurationpersonalizationlockscreenimageurl"></a>Windows10GeneralConfiguration./Izationlockscreenimageurl 
**CSP**:./Device/Vendor/MSFT/Personalization  
**オフセット URI**:/lockscreenimageurl

### <a name="windows10generalconfigurationpowerrequirepasswordonwakewhileonbattery"></a>Windows10GeneralConfiguration.PowerRequirePasswordOnWakeWhileOnBattery 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/powerpasswordwhencomputerwakesonバッテリ

### <a name="windows10generalconfigurationpowerrequirepasswordonwakewhilepluggedin"></a>Windows10GeneralConfiguration.PowerRequirePasswordOnWakeWhilePluggedIn 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Power/RequirePasswordWhenComputerWakesPluggedIn

### <a name="windows10generalconfigurationpowerstandbystateswhensleepingwhileonbattery"></a>Windows10GeneralConfiguration.PowerStandbyStatesWhenSleepingWhileOnBattery 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Power/AllowStandbyStatesWhenSleepingOnBattery

### <a name="windows10generalconfigurationpowerstandbystateswhensleepingwhilepluggedin"></a>Windows10GeneralConfiguration.PowerStandbyStatesWhenSleepingWhilePluggedIn 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Power/AllowStandbyWhenSleepingPluggedIn

### <a name="windows10generalconfigurationpreventinstallationofmatchingdeviceids"></a>windows10generalconfiguration.preventInstallationOfMatchingDeviceIDs 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/DeviceInstallation/PreventInstallationOfMatchingDeviceIDs

### <a name="windows10generalconfigurationpreventinstallationofmatchingdevicesetupclasses"></a>windows10generalconfiguration.preventInstallationOfMatchingDeviceSetupClasses 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/DeviceInstallation/PreventInstallationOfMatchingDeviceSetupClasses

### <a name="windows10generalconfigurationprinterblockaddition"></a>Windows10GeneralConfiguration の追加 
**CSP**:./User/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Education/PreventAddingNewPrinters

### <a name="windows10generalconfigurationprinterdefaultname"></a>Windows10GeneralConfiguration 
**CSP**:./User/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Education/DefaultPrinterName

### <a name="windows10generalconfigurationprinternames"></a>Windows10GeneralConfiguration 
**CSP**:./User/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Education/PrinterNames

### <a name="windows10generalconfigurationprivacyadvertisingid"></a>Windows10GeneralConfiguration.PrivacyAdvertisingId 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Privacy/DisableAdvertisingID

### <a name="windows10generalconfigurationprivacyautoacceptpairingandconsentprompts"></a>Windows10GeneralConfiguration.PrivacyAutoAcceptPairingAndConsentPrompts 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Privacy/AllowAutoAcceptPairingAndPrivacyConsentPrompts

### <a name="windows10generalconfigurationprivacyblockactivityfeed"></a>Windows10GeneralConfiguration Blockactivityfeed 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/privacyfeed フィード

### <a name="windows10generalconfigurationprivacyblockinputpersonalization"></a>Windows10GeneralConfiguration.PrivacyBlockInputPersonalization 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Privacy/allowinputパーソナル化

### <a name="windows10generalconfigurationprivacyblockpublishuseractivities"></a>Windows10GeneralConfiguration Blockpublishuserアクティビティ 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/privacyuserアクティビティ

### <a name="windows10generalconfigurationsafesearchfilter"></a>Windows10GeneralConfiguration 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/safesearchpermissions

### <a name="windows10generalconfigurationscreencaptureblocked"></a>Windows10GeneralConfiguration.ScreenCaptureBlocked 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Experience/AllowScreenCapture

### <a name="windows10generalconfigurationsearchblockdiacritics"></a>Windows10GeneralConfiguration 分音文字 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:///分音文字の利用

### <a name="windows10generalconfigurationsearchblockwebresults"></a>Windows10GeneralConfiguration Webresults 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/config/searchusewebresults

### <a name="windows10generalconfigurationsearchdisableautolanguagedetection"></a>Windows10GeneralConfiguration.SearchDisableAutoLanguageDetection 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Search/AlwaysUseAutoLangDetection

### <a name="windows10generalconfigurationsearchdisableindexerbackoff"></a>Windows10GeneralConfiguration. SearchDisableIndexerBackoff オフ 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/disableバックオフ

### <a name="windows10generalconfigurationsearchdisableindexingencrypteditems"></a>Windows10GeneralConfiguration.SearchDisableIndexingEncryptedItems 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Search/AllowIndexingEncryptedStoresOrItems

### <a name="windows10generalconfigurationsearchdisableindexingremovabledrive"></a>Windows10GeneralConfiguration.SearchDisableIndexingRemovableDrive 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/config/disableremovableドライブのインデックス作成

### <a name="windows10generalconfigurationsearchdisablelocation"></a>Windows10GeneralConfiguration の場所 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Search/AllowSearchToUseLocation

### <a name="windows10generalconfigurationsearchdisableuselocation"></a>Windows10GeneralConfiguration. SearchDisableUseLocation 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Search/AllowSearchToUseLocation

### <a name="windows10generalconfigurationsearchenableautomaticindexsizemanangement"></a>Windows10GeneralConfiguration.SearchEnableAutomaticIndexSizeManangement 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Search/PreventIndexingLowDiskSpaceMB

### <a name="windows10generalconfigurationsearchenableremotequeries"></a>Windows10GeneralConfiguration.SearchEnableRemoteQueries 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Search/PreventRemoteQueries

### <a name="windows10generalconfigurationsecurityblockazureadjoineddevicesautoencryption"></a>Windows10GeneralConfiguration.SecurityBlockAzureADJoinedDevicesAutoEncryption 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Security/PreventAutomaticDeviceEncryptionForAzureADJoinedDevices

### <a name="windows10generalconfigurationsettingsblockaccountspage"></a>Windows10GeneralConfiguration.SettingsBlockAccountsPage 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Settings/PageVisibilityList

### <a name="windows10generalconfigurationsettingsblockaddprovisioningpackage"></a>Windows10GeneralConfiguration の Addblockpackage 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Dns/securityaddconfigpackage

### <a name="windows10generalconfigurationsettingsblockappspage"></a>Windows10GeneralConfiguration.SettingsBlockAppsPage 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Settings/PageVisibilityList

### <a name="windows10generalconfigurationsettingsblockchangelanguage"></a>Windows10GeneralConfiguration.SettingsBlockChangeLanguage 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/allowlanguage

### <a name="windows10generalconfigurationsettingsblockchangepowersleep"></a>Windows10GeneralConfiguration. SettingsBlockChangePowerSleep 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/allowpowersleep

### <a name="windows10generalconfigurationsettingsblockchangeregion"></a>Windows10GeneralConfiguration.SettingsBlockChangeRegion 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/allowregion

### <a name="windows10generalconfigurationsettingsblockchangesystemtime"></a>Windows10GeneralConfiguration.SettingsBlockChangeSystemTime 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/allowdatetime

### <a name="windows10generalconfigurationsettingsblockdevicespage"></a>Windows10GeneralConfiguration ページ 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Settings/PageVisibilityList

### <a name="windows10generalconfigurationsettingsblockeaseofaccesspage"></a>Windows10GeneralConfiguration.SettingsBlockEaseOfAccessPage 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Settings/PageVisibilityList

### <a name="windows10generalconfigurationsettingsblockeditdevicename"></a>Windows10GeneralConfiguration.SettingsBlockEditDeviceName 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Settings/alloweditdevicename

### <a name="windows10generalconfigurationsettingsblockgamingpage"></a>Windows10GeneralConfiguration.SettingsBlockGamingPage 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Settings/PageVisibilityList

### <a name="windows10generalconfigurationsettingsblocknetworkinternetpage"></a>Windows10GeneralConfiguration. SettingsBlockNetworkInternetPage 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Settings/PageVisibilityList

### <a name="windows10generalconfigurationsettingsblockpersonalizationpage"></a>Windows10GeneralConfiguration のページ 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Settings/PageVisibilityList

### <a name="windows10generalconfigurationsettingsblockprivacypage"></a>Windows10GeneralConfiguration.SettingsBlockPrivacyPage 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Settings/PageVisibilityList

### <a name="windows10generalconfigurationsettingsblockremoveprovisioningpackage"></a>Windows10GeneralConfiguration Removeblockpackage 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/securityremovepackage

### <a name="windows10generalconfigurationsettingsblocksystempage"></a>Windows10GeneralConfiguration ページ 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Settings/PageVisibilityList

### <a name="windows10generalconfigurationsettingsblocktimelanguagepage"></a>Windows10GeneralConfiguration.SettingsBlockTimeLanguagePage 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Settings/PageVisibilityList

### <a name="windows10generalconfigurationsettingsblockupdatesecuritypage"></a>Windows10GeneralConfiguration.SettingsBlockUpdateSecurityPage 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Settings/PageVisibilityList

### <a name="windows10generalconfigurationshareduserappdataallowed"></a>Windows10GeneralConfiguration. SharedUserAppDataAllowed 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Applicationmanagement/allowshareduserappdata

### <a name="windows10generalconfigurationsmartscreenblockpromptoverride"></a>Windows10GeneralConfiguration.SmartScreenBlockPromptOverride 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Browser/PreventSmartScreenPromptOverride

### <a name="windows10generalconfigurationsmartscreenblockpromptoverrideforfiles"></a>Windows10GeneralConfiguration.SmartScreenBlockPromptOverrideForFiles 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Browser/PreventSmartScreenPromptOverrideForFiles

### <a name="windows10generalconfigurationsmartscreenenableappinstallcontrol"></a>Windows10GeneralConfiguration. SmartScreenEnableAppInstallControl 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Smartscreen/enableappinstallcontrol

### <a name="windows10generalconfigurationstartblockunpinningappsfromtaskbar"></a>Windows10GeneralConfiguration.StartBlockUnpinningAppsFromTaskbar 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Start/NoPinningToTaskbar

### <a name="windows10generalconfigurationstartmenuapplistvisibility"></a>Windows10GeneralConfiguration を参照してください。 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/config////////

### <a name="windows10generalconfigurationstartmenuhidechangeaccountsettings"></a>Windows10GeneralConfiguration.StartMenuHideChangeAccountSettings 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Start/HideChangeAccountSettings

### <a name="windows10generalconfigurationstartmenuhidefrequentlyusedapps"></a>Windows10GeneralConfiguration.StartMenuHideFrequentlyUsedApps 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Start/HideFrequentlyUsedApps

### <a name="windows10generalconfigurationstartmenuhidehibernate"></a>Windows10GeneralConfiguration. StartMenuHideHibernate 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/config//hidehibernate

### <a name="windows10generalconfigurationstartmenuhidelock"></a>Windows10GeneralConfiguration. StartMenuHideLock 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:////のロック

### <a name="windows10generalconfigurationstartmenuhidepowerbutton"></a>Windows10GeneralConfiguration. StartMenuHidePowerButton 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config//hidepowerbutton

### <a name="windows10generalconfigurationstartmenuhiderecentjumplists"></a>Windows10GeneralConfiguration.StartMenuHideRecentJumpLists 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Start/HideRecentJumplists

### <a name="windows10generalconfigurationstartmenuhiderecentlyaddedapps"></a>Windows10GeneralConfiguration.StartMenuHideRecentlyAddedApps 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Start/HideRecentlyAddedApps

### <a name="windows10generalconfigurationstartmenuhiderestartoptions"></a>Windows10GeneralConfiguration.StartMenuHideRestartOptions 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/starterestart

### <a name="windows10generalconfigurationstartmenuhideshutdown"></a>Windows10GeneralConfiguration.StartMenuHideShutDown 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Start/HideShutDown

### <a name="windows10generalconfigurationstartmenuhidesignout"></a>Windows10GeneralConfiguration を終了します。 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/startdesignout

### <a name="windows10generalconfigurationstartmenuhidesleep"></a>Windows10GeneralConfiguration.StartMenuHideSleep 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Start/HideSleep

### <a name="windows10generalconfigurationstartmenuhideswitchaccount"></a>Windows10GeneralConfiguration. Startmenuhides Chaccount 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/startのアカウント

### <a name="windows10generalconfigurationstartmenuhideusertile"></a>Windows10GeneralConfiguration. StartMenuHideUserTile 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/startusertile

### <a name="windows10generalconfigurationstartmenulayoutedgeassetsxml"></a>Windows10GeneralConfiguration.StartMenuLayoutEdgeAssetsXml 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Start/ImportEdgeAssets

### <a name="windows10generalconfigurationstartmenulayoutxml"></a>Windows10GeneralConfiguration.StartMenuLayoutXml 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/startlayout

### <a name="windows10generalconfigurationstartmenumode"></a>Windows10GeneralConfiguration モード 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Start/ForceStartSize

### <a name="windows10generalconfigurationstartmenupinnedfolderdocuments"></a>Windows10GeneralConfiguration.StartMenuPinnedFolderDocuments 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Start/AllowPinnedFolderDocuments

### <a name="windows10generalconfigurationstartmenupinnedfolderdownloads"></a>Windows10GeneralConfiguration.StartMenuPinnedFolderDownloads 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Start/AllowPinnedFolderDownloads

### <a name="windows10generalconfigurationstartmenupinnedfolderfileexplorer"></a>Windows10GeneralConfiguration.StartMenuPinnedFolderFileExplorer 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Start/AllowPinnedFolderFileExplorer

### <a name="windows10generalconfigurationstartmenupinnedfolderhomegroup"></a>Windows10GeneralConfiguration.StartMenuPinnedFolderHomeGroup 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Start/AllowPinnedFolderHomeGroup

### <a name="windows10generalconfigurationstartmenupinnedfoldermusic"></a>Windows10GeneralConfiguration.StartMenuPinnedFolderMusic 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Start/AllowPinnedFolderMusic

### <a name="windows10generalconfigurationstartmenupinnedfoldernetwork"></a>Windows10GeneralConfiguration.StartMenuPinnedFolderNetwork 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Start/AllowPinnedFolderNetwork

### <a name="windows10generalconfigurationstartmenupinnedfolderpersonalfolder"></a>Windows10GeneralConfiguration.StartMenuPinnedFolderPersonalFolder 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Start/AllowPinnedFolderPersonalFolder

### <a name="windows10generalconfigurationstartmenupinnedfolderpictures"></a>Windows10GeneralConfiguration.StartMenuPinnedFolderPictures 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Start/AllowPinnedFolderPictures

### <a name="windows10generalconfigurationstartmenupinnedfoldersettings"></a>Windows10GeneralConfiguration.StartMenuPinnedFolderSettings 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Start/AllowPinnedFolderSettings

### <a name="windows10generalconfigurationstartmenupinnedfoldervideos"></a>Windows10GeneralConfiguration.StartMenuPinnedFolderVideos 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Start/AllowPinnedFolderVideos

### <a name="windows10generalconfigurationstorageblockremovablestorage"></a>Windows10GeneralConfiguration (StorageBlockRemovableStorage) 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/System/AllowStorageCard

### <a name="windows10generalconfigurationstoragerequiremobiledeviceencryption"></a>Windows10GeneralConfiguration.StorageRequireMobileDeviceEncryption 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/securitydeviceencryption

### <a name="windows10generalconfigurationstoragerestrictappdatatosystemvolume"></a>Windows10GeneralConfiguration.StorageRestrictAppDataToSystemVolume 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/ApplicationManagement/RestrictAppDataToSystemVolume

### <a name="windows10generalconfigurationstoragerestrictappinstalltosystemvolume"></a>Windows10GeneralConfiguration.StorageRestrictAppInstallToSystemVolume 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/ApplicationManagement/RestrictAppToSystemVolume

### <a name="windows10generalconfigurationsystembootstartdriverinitialization"></a>Windows10GeneralConfiguration. SystemBootStartDriverInitialization 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/System/BootStartDriverInitialization

### <a name="windows10generalconfigurationsystemtelemetryproxyserver"></a>Windows10GeneralConfiguration.SystemTelemetryProxyServer 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/System/TelemetryProxy

### <a name="windows10generalconfigurationtaskmanagerblockendtask"></a>Windows10GeneralConfiguration のタスクマネージャー 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Taskmanager/allowendtask

### <a name="windows10generalconfigurationtenantlockdownrequirenetworkduringoutofboxexperience"></a>Windows10GeneralConfiguration.TenantLockdownRequireNetworkDuringOutOfBoxExperience 
**CSP**:./Vendor/MSFT/TenantLockdown  
**オフセット URI**:/RequireNetworkInOOBE

### <a name="windows10generalconfigurationusbblocked"></a>Windows10GeneralConfiguration がブロックされました 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Connectivity/AllowUSBConnection

### <a name="windows10generalconfigurationvoicerecordingblocked"></a>Windows10GeneralConfiguration.VoiceRecordingBlocked 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Experience/AllowVoiceRecording

### <a name="windows10generalconfigurationwebrtcblocklocalhostipaddress"></a>Windows10GeneralConfiguration.WebRtcBlockLocalhostIpAddress 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Browser/PreventUsingLocalHostIPAddressForWebRTC

### <a name="windows10generalconfigurationwifiblockautomaticconnecthotspots"></a>Windows10GeneralConfiguration.WiFiBlockAutomaticConnectHotspots 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/WiFi/AllowAutoConnectToWiFiSenseHotspots

### <a name="windows10generalconfigurationwifiblocked"></a>Windows10GeneralConfiguration.WiFiBlocked 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Wifi/AllowWiFi

### <a name="windows10generalconfigurationwifiblockmanualconfiguration"></a>Windows10GeneralConfiguration.WiFiBlockManualConfiguration 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/WiFi/AllowManualWiFi/Configuration

### <a name="windows10generalconfigurationwifiscaninterval"></a>Windows10GeneralConfiguration.WiFiScanInterval 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/WiFi/WLANScanMode

### <a name="windows10generalconfigurationwindowslogonlocalusersondomainjoinedcomputers"></a>Windows10GeneralConfiguration. WindowsLogOnLocalUsersOnDomainJoinedComputers 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/WindowsLogon/EnumerateLocalUsersOnDomainJoinedComputers

### <a name="windows10generalconfigurationwindowsspotlightblockconsumerspecificfeatures"></a>Windows10GeneralConfiguration.WindowsSpotlightBlockConsumerSpecificFeatures 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Experience/AllowWindowsConsumerFeatures

### <a name="windows10generalconfigurationwindowsspotlightblocked"></a>ブロックされた Windows10GeneralConfiguration 
**CSP**:./User/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Experience/AllowWindowsSpotlight

### <a name="windows10generalconfigurationwindowsspotlightblockonactioncenter"></a>Windows10GeneralConfiguration ライト Blockonactioncenter 
**CSP**:./User/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Experience/AllowWindowsSpotlightOnActionCenter

### <a name="windows10generalconfigurationwindowsspotlightblocktailoredexperiences"></a>Windows10GeneralConfiguration.WindowsSpotlightBlockTailoredExperiences 
**CSP**:./User/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Experience/AllowTailoredExperiencesWithDiagnosticData

### <a name="windows10generalconfigurationwindowsspotlightblockthirdpartynotifications"></a>Windows10GeneralConfiguration.WindowsSpotlightBlockThirdPartyNotifications 
**CSP**:./User/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Experience/AllowThirdPartySuggestionsInWindowsSpotlight

### <a name="windows10generalconfigurationwindowsspotlightblockwelcomeexperience"></a>Windows10GeneralConfiguration.WindowsSpotlightBlockWelcomeExperience 
**CSP**:./User/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Experience/AllowWindowsSpotlightWindowsWelcomeExperience

### <a name="windows10generalconfigurationwindowsspotlightblockwindowstips"></a>Windows10GeneralConfiguration ライト Blockwindowinps 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Experience/AllowWindowsTips

### <a name="windows10generalconfigurationwindowsspotlightconfigureonlockscreen"></a>Windows10GeneralConfiguration.WindowsSpotlightConfigureOnLockScreen 
**CSP**:./User/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Experience/ConfigureWindowsSpotlightOnLockScreen

### <a name="windows10generalconfigurationwindowsstoreblockautoupdate"></a>Windows10GeneralConfiguration. WindowsStoreBlockAutoUpdate 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Applicationmanagement/allowappstoreautoupdate

### <a name="windows10generalconfigurationwindowsstoreblocked"></a>Windows10GeneralConfiguration がブロックされました 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Applicationmanagement/allowstore

### <a name="windows10generalconfigurationwindowsstoreenableprivatestoreonly"></a>Windows10GeneralConfiguration. WindowsStoreEnablePrivateStoreOnly 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Applicationmanagement/requireprivatestoreonly

### <a name="windows10generalconfigurationwirelessdisplayblockprojectiontothisdevice"></a>Windows10GeneralConfiguration.WirelessDisplayBlockProjectionToThisDevice 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/WirelessDisplay/AllowProjectionToPC

### <a name="windows10generalconfigurationwirelessdisplayblockuserinputfromreceiver"></a>Windows10GeneralConfiguration.WirelessDisplayBlockUserInputFromReceiver 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/WirelessDisplay/AllowUserInputFromWirelessDisplayReceiver

### <a name="windows10generalconfigurationwirelessdisplayrequirepinforpairing"></a>Windows10GeneralConfiguration.WirelessDisplayRequirePinForPairing 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/WirelessDisplay/RequirePINForPairing

### <a name="windows10networkboundaryconfigurationwindowsnetworkisolationpolicy"></a>Windows10NetworkBoundaryConfiguration.WindowsNetworkIsolationPolicy 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/NetworkIsolation/EnterpriseCloudResources、/Config/NetworkIsolation/EnterpriseIPRange、/Config/NetworkIsolation/EnterpriseIPRangesAreAuthoritative、/Config/NetworkIsolation/EnterpriseInternalProxyServers、/Config/NetworkIsolation/EnterpriseNetworkDomainNames、/Config/NetworkIsolation/EnterpriseProxyServers、/Config/NetworkIsolation/EnterpriseProxyServersAreAuthoritative、/Config/NetworkIsolation/NeutralResources

### <a name="windows10policyoverrideconfigurationprefermdmovergrouppolicy"></a>Windows10PolicyOverrideConfiguration.PreferMdmOverGroupPolicy 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/ControlPolicyConflict/MDMWinsOverGP

### <a name="windows10secureassessmentconfigurationallowprinting"></a>Windows10SecureAssessmentConfiguration 
**CSP**:./Vendor/MSFT/SecureAssessment  
**オフセット URI**:/require印刷

### <a name="windows10secureassessmentconfigurationallowscreencapture"></a>Windows10SecureAssessmentConfiguration.AllowScreenCapture 
**CSP**:./Vendor/MSFT/SecureAssessment  
**オフセット URI**:/allowscreenmonitoring

### <a name="windows10secureassessmentconfigurationallowtextsuggestion"></a>Windows10SecureAssessmentConfiguration 
**CSP**:./Vendor/MSFT/SecureAssessment  
**オフセット URI**:/allowtext提案

### <a name="windows10secureassessmentconfigurationconfigurationaccount"></a>Windows10SecureAssessmentConfiguration 
**CSP**:./Vendor/MSFT/SecureAssessment  
**オフセット URI**:/teaccount

### <a name="windows10secureassessmentconfigurationconfigurationaccounttype"></a>Windows10SecureAssessmentConfiguration 
**CSP**:./Vendor/MSFT/SecureAssessment  
**オフセット URI**:/teaccount

### <a name="windows10secureassessmentconfigurationlaunchuri"></a>Windows10SecureAssessmentConfiguration 
**CSP**:./Vendor/MSFT/SecureAssessment  
**オフセット uri**:/launchuri

### <a name="windows10teamgeneralconfigurationazureoperationalinsightsblocktelemetry"></a>Windows10TeamGeneralConfiguration.AzureOperationalInsightsBlockTelemetry 
**CSP**:./Vendor/MSFT/SurfaceHub  
**オフセット URI**:/MOMAgent/WorkspaceID と/MOMAgent/WorkspaceKey

### <a name="windows10teamgeneralconfigurationazureoperationalinsightsworkspaceid"></a>Windows10TeamGeneralConfiguration.AzureOperationalInsightsWorkspaceId 
**CSP**:./Vendor/MSFT/SurfaceHub  
**オフセット URI**:/MOMAgent/WorkspaceID

### <a name="windows10teamgeneralconfigurationazureoperationalinsightsworkspacekey"></a>Windows10TeamGeneralConfiguration.AzureOperationalInsightsWorkspaceKey 
**CSP**:./Vendor/MSFT/SurfaceHub  
**オフセット URI**:/MOMAgent/WorkspaceKey

### <a name="windows10teamgeneralconfigurationconnectappblockautolaunch"></a>Windows10TeamGeneralConfiguration.ConnectAppBlockAutoLaunch 
**CSP**:./Vendor/MSFT/SurfaceHub  
**オフセット URI**:/InBoxApps/Connect/AutoLaunch

### <a name="windows10teamgeneralconfigurationdeviceaccountblockexchangeservices"></a>Windows10TeamGeneralConfiguration.DeviceAccountBlockExchangeServices 
**CSP**:./Vendor/MSFT/SurfaceHub  
**オフセット URI**:/Deviceaccount/Email

### <a name="windows10teamgeneralconfigurationdeviceaccountemailaddress"></a>Windows10TeamGeneralConfiguration.DeviceAccountEmailAddress 
**CSP**:./Vendor/MSFT/SurfaceHub  
**オフセット URI**:/Deviceaccount/Email

### <a name="windows10teamgeneralconfigurationdeviceaccountexchangeserveraddress"></a>Windows10TeamGeneralConfiguration.DeviceAccountExchangeServerAddress 
**CSP**:./Vendor/MSFT/SurfaceHub  
**オフセット URI**:/DeviceAccount/ExchangeServer

### <a name="windows10teamgeneralconfigurationdeviceaccountrequirepasswordrotation"></a>Windows10TeamGeneralConfiguration.DeviceAccountRequirePasswordRotation 
**CSP**:./Vendor/MSFT/SurfaceHub  
**オフセット URI**:/DeviceAccount/PasswordRotationEnabled

### <a name="windows10teamgeneralconfigurationdeviceaccountsessioninitiationprotocoladdress"></a>Windows10TeamGeneralConfiguration. DeviceAccountSessionInitiationProtocolAddress 
**CSP**:./Vendor/MSFT/SurfaceHub  
**オフセット URI**:/DeviceAccount/SipAddress

### <a name="windows10teamgeneralconfigurationmaintenancewindowblocked"></a>Windows10TeamGeneralConfiguration.MaintenanceWindowBlocked 
**CSP**:./Vendor/MSFT/SurfaceHub  
**オフセット URI**:/MaintenanceHoursSimple/Hours/Duration と/MaintenanceHoursSimple/Hours/StartTime

### <a name="windows10teamgeneralconfigurationmaintenancewindowdurationinhours"></a>Windows10TeamGeneralConfiguration.MaintenanceWindowDurationInHours 
**CSP**:./Vendor/MSFT/SurfaceHub  
**オフセット URI**:/MaintenanceHoursSimple/Hours/Duration

### <a name="windows10teamgeneralconfigurationmaintenancewindowstarttime"></a>Windows10TeamGeneralConfiguration.MaintenanceWindowStartTime 
**CSP**:./Vendor/MSFT/SurfaceHub  
**オフセット URI**:/MaintenanceHoursSimple/Hours/StartTime

### <a name="windows10teamgeneralconfigurationmiracastblocked"></a>Windows10TeamGeneralConfiguration.MiracastBlocked 
**CSP**:./Vendor/MSFT/SurfaceHub  
**オフセット URI**:/InBoxApps/WirelessProjection/Enabled

### <a name="windows10teamgeneralconfigurationmiracastchannel"></a>Windows10TeamGeneralConfiguration.MiracastChannel 
**CSP**:./Vendor/MSFT/SurfaceHub  
**オフセット URI**:/InBoxApps/WirelessProjection/Channel

### <a name="windows10teamgeneralconfigurationmiracastrequirepin"></a>Windows10TeamGeneralConfiguration.MiracastRequirePin 
**CSP**:./Vendor/MSFT/SurfaceHub  
**オフセット URI**:/InBoxApps/WirelessProjection/PINRequired

### <a name="windows10teamgeneralconfigurationsettingsblockmymeetingsandfiles"></a>Windows10TeamGeneralConfiguration.SettingsBlockMyMeetingsAndFiles 
**CSP**:./Vendor/MSFT/SurfaceHub  
**オフセット URI**:/Properties/DoNotShowMyMeetingsAndFiles

### <a name="windows10teamgeneralconfigurationsettingsblocksessionresume"></a>Windows10TeamGeneralConfiguration のセッション再開 
**CSP**:./Vendor/MSFT/SurfaceHub  
**オフセット URI**:/プロパティ/allowsessionresume

### <a name="windows10teamgeneralconfigurationsettingsblocksigninsuggestions"></a>Windows10TeamGeneralConfiguration.SettingsBlockSigninSuggestions 
**CSP**:./Vendor/MSFT/SurfaceHub  
**オフセット URI**:/プロパティ/disablesignin候補

### <a name="windows10teamgeneralconfigurationsettingsdefaultvolume"></a>Windows10TeamGeneralConfiguration 
**CSP**:./Vendor/MSFT/SurfaceHub  
**オフセット URI**:/プロパティ/defaultvolume

### <a name="windows10teamgeneralconfigurationsettingsscreentimeoutinminutes"></a>Windows10TeamGeneralConfiguration.SettingsScreenTimeoutInMinutes 
**CSP**:./Vendor/MSFT/SurfaceHub  
**オフセット URI**:/Properties/ScreenTimeout

### <a name="windows10teamgeneralconfigurationsettingssessiontimeoutinminutes"></a>Windows10TeamGeneralConfiguration.SettingsSessionTimeoutInMinutes 
**CSP**:./Vendor/MSFT/SurfaceHub  
**オフセット URI**:/Properties/SessionTimeout

### <a name="windows10teamgeneralconfigurationsettingssleeptimeoutinminutes"></a>Windows10TeamGeneralConfiguration.SettingsSleepTimeoutInMinutes 
**CSP**:./Vendor/MSFT/SurfaceHub  
**オフセット URI**:/Properties/SleepTimeout

### <a name="windows10teamgeneralconfigurationwelcomescreenbackgroundimageurl"></a>Windows10TeamGeneralConfiguration.WelcomeScreenBackgroundImageUrl 
**CSP**:./Vendor/MSFT/SurfaceHub  
**オフセット URI**:/InBoxApps/Welcome/CurrentBackgroundPath

### <a name="windows10teamgeneralconfigurationwelcomescreenblockautomaticwakeup"></a>Windows10TeamGeneralConfiguration.WelcomeScreenBlockAutomaticWakeUp 
**CSP**:./Vendor/MSFT/SurfaceHub  
**オフセット URI**:/InBoxApps/Welcome/AutoWakeScreen

### <a name="windows10teamgeneralconfigurationwelcomescreenmeetinginformation"></a>Windows10TeamGeneralConfiguration.WelcomeScreenMeetingInformation 
**CSP**:./Vendor/MSFT/SurfaceHub  
**オフセット URI**:/InBoxApps/Welcome/MeetingInfoOption

### <a name="windowsdefenderadvancedthreatprotectionconfigurationadvancedthreatprotectionoffboardingblob"></a>WindowsDefenderAdvancedThreatProtectionConfiguration.AdvancedThreatProtectionOffboardingBlob 
**CSP**: ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection  
**オフセット URI**:/オフボード 

### <a name="windowsdefenderadvancedthreatprotectionconfigurationadvancedthreatprotectionoffboardingfilename"></a>WindowsDefenderAdvancedThreatProtectionConfiguration.AdvancedThreatProtectionOffboardingFilename
**CSP**: ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection  
**オフセット URI**:/オフボード 

### <a name="windowsdefenderadvancedthreatprotectionconfigurationadvancedthreatprotectiononboardingblob"></a>WindowsDefenderAdvancedThreatProtectionConfiguration.AdvancedThreatProtectionOnboardingBlob 
**CSP**: ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection  
**オフセット URI**:/オンボード 

### <a name="windowsdefenderadvancedthreatprotectionconfigurationadvancedthreatprotectiononboardingfilename"></a>WindowsDefenderAdvancedThreatProtectionConfiguration.AdvancedThreatProtectionOnboardingFilename 
**CSP**: ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection  
**オフセット URI**:/オンボード 

### <a name="windowsdefenderadvancedthreatprotectionconfigurationallowsamplesharing"></a>WindowsDefenderAdvancedThreatProtectionConfiguration.AllowSampleSharing 
**CSP**: ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection  
**オフセット URI**:/Configuration/SampleSharing

### <a name="windowsdefenderadvancedthreatprotectionconfigurationenableexpeditedtelemetryreporting"></a>WindowsDefenderAdvancedThreatProtectionConfiguration.EnableExpeditedTelemetryReporting 
**CSP**: ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection  
**オフセット URI**:/Configuration/TelemetryReportingFrequency

### <a name="windowsdeliveryoptimizationconfigurationdeliveryoptimizationmode"></a>WindowsDeliveryOptimizationConfiguration.DeliveryOptimizationMode 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/DeliveryOptimization/DODownloadMode

### <a name="windowsidentityprotectionconfigurationenhancedantispoofingforfacialfeaturesenabled"></a>WindowsIdentityProtectionConfiguration.EnhancedAntiSpoofingForFacialFeaturesEnabled 
**CSP**:./Device/Vendor/MSFT/PassportForWork  
**オフセット URI**:/Biometrics/FacialFeaturesUseEnhancedAntiSpoofing

### <a name="windowsidentityprotectionconfigurationpinexpirationindays"></a>WindowsIdentityProtectionConfiguration.PinExpirationInDays 
**CSP**:./Vendor/MSFT/PassportForWork  
**オフセット URI**:/{AADTenantId}/Policies/PINComplexity/Expiration

### <a name="windowsidentityprotectionconfigurationpinlowercasecharactersusage"></a>WindowsIdentityProtectionConfiguration.PinLowercaseCharactersUsage 
**CSP**:./Vendor/MSFT/PassportForWork  
**オフセット URI**:/{AADTenantId}/Policies/PINComplexity/LowercaseLetters

### <a name="windowsidentityprotectionconfigurationpinmaximumlength"></a>WindowsIdentityProtectionConfiguration 
**CSP**:./Vendor/MSFT/PassportForWork  
**オフセット URI**:/{AADTenantId}/Policies/PINComplexity/MaximumPINLength

### <a name="windowsidentityprotectionconfigurationpinminimumlength"></a>WindowsIdentityProtectionConfiguration 
**CSP**:./Vendor/MSFT/PassportForWork  
**オフセット URI**:/{AADTenantId}/Policies/PINComplexity/MinimumPINLength

### <a name="windowsidentityprotectionconfigurationpinpreviousblockcount"></a>WindowsIdentityProtectionConfiguration の前のブロック数 
**CSP**:./Vendor/MSFT/PassportForWork  
**オフセット URI**:/{AADTenantId}/Policies/PINComplexity/History

### <a name="windowsidentityprotectionconfigurationpinrecoveryenabled"></a>WindowsIdentityProtectionConfiguration を有効にします。 
**CSP**:./Vendor/MSFT/PassportForWork  
**オフセット URI**:/{AADTenantId}/Policies/EnablePinRecovery

### <a name="windowsidentityprotectionconfigurationpinspecialcharactersusage"></a>WindowsIdentityProtectionConfiguration の使用法 
**CSP**:./Vendor/MSFT/PassportForWork  
**オフセット URI**:/{AADTenantId}/Policies/PINComplexity/SpecialCharacters

### <a name="windowsidentityprotectionconfigurationpinuppercasecharactersusage"></a>WindowsIdentityProtectionConfiguration.PinUppercaseCharactersUsage
**CSP**:./Vendor/MSFT/PassportForWork  
**オフセット URI**:/{AADTenantId}/Policies/PINComplexity/UppercaseLetters

### <a name="windowsidentityprotectionconfigurationsecuritydevicerequired"></a>WindowsIdentityProtectionConfiguration.SecurityDeviceRequired 
**CSP**:./Vendor/MSFT/PassportForWork  
**オフセット URI**:/{AADTenantId}/Policies/RequireSecurityDevice

### <a name="windowsidentityprotectionconfigurationunlockwithbiometricsenabled"></a>WindowsIdentityProtectionConfiguration.UnlockWithBiometricsEnabled 
**CSP**:./Device/Vendor/MSFT/PassportForWork  
**オフセット URI**:/Biometrics/UseBiometrics

### <a name="windowsidentityprotectionconfigurationusecertificatesforonpremisesauthenabled"></a>WindowsIdentityProtectionConfiguration.UseCertificatesForOnPremisesAuthEnabled 
**CSP**:./Device/Vendor/MSFT/PassportForWork  
**オフセット URI**:/{AADTenantId}/Policies/UseCertificateForOnPremAuth

### <a name="windowsidentityprotectionconfigurationwindowshelloforbusinessblocked"></a>WindowsIdentityProtectionConfiguration.WindowsHelloForBusinessBlocked 
**CSP**:./Vendor/MSFT/PassportForWork  
**オフセット URI**:/{AADTenantId}/Policies/UsePassportForWork

### <a name="windowskioskconfigurationedgekioskenablepublicbrowsing"></a>WindowsKioskConfiguration. EdgeKioskEnablePublicBrowsing 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Browser/ConfigureKioskMode

### <a name="windowskioskconfigurationedgekioskresetafteridletimeinminutes"></a>WindowsKioskConfiguration. EdgeKioskResetAfterIdleTimeInMinutes 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/Config/Browser/ConfigureKioskResetAfterIdleTimeout

### <a name="windowskioskconfigurationkioskbrowserblockedurlexceptions"></a>WindowsKioskConfiguration. KioskBrowserBlockedUrlExceptions 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/KioskBrowser/BlockedUrlExceptions

### <a name="windowskioskconfigurationkioskbrowserblockedurls"></a>WindowsKioskConfiguration. KioskBrowserBlockedURLs 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/KioskBrowser/BlockedUrls

### <a name="windowskioskconfigurationkioskbrowserdefaulturl"></a>WindowsKioskConfiguration. KioskBrowserDefaultUrl 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/KioskBrowser/DefaultUrl

### <a name="windowskioskconfigurationkioskbrowserenableendsessionbutton"></a>WindowsKioskConfiguration. KioskBrowserEnableEndSessionButton 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/KioskBrowser/EnableEndSessionButton

### <a name="windowskioskconfigurationkioskbrowserenablehomebutton"></a>WindowsKioskConfiguration. KioskBrowserEnableHomeButton 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/KioskBrowser/EnableHomeButton

### <a name="windowskioskconfigurationkioskbrowserenablenavigationbuttons"></a>WindowsKioskConfiguration. KioskBrowserEnableNavigationButtons 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/KioskBrowser/EnableNavigationButtons

### <a name="windowskioskconfigurationkioskbrowserrestartonidletimeinminutes"></a>WindowsKioskConfiguration. KioskBrowserRestartOnIdleTimeInMinutes 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/KioskBrowser/KioskBrowserRestartOnIdleTimeInMinutes

### <a name="windowsupdateforbusinessconfigurationautomaticupdatemode"></a>WindowsUpdateForBusinessConfiguration 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/更新

### <a name="windowsupdateforbusinessconfigurationautorestartnotificationdismissal"></a>WindowsUpdateForBusinessConfiguration.AutoRestartNotificationDismissal 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Update/AutoRestartRequiredNotificationDismissal

### <a name="windowsupdateforbusinessconfigurationbusinessreadyupdatesonly"></a>WindowsUpdateForBusinessConfiguration.BusinessReadyUpdatesOnly 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Update/BranchReadinessLevel

### <a name="windowsupdateforbusinessconfigurationdeliveryoptimizationmode"></a>WindowsUpdateForBusinessConfiguration.DeliveryOptimizationMode 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/DeliveryOptimization/DODownloadMode

### <a name="windowsupdateforbusinessconfigurationdriversexcluded"></a>WindowsUpdateForBusinessConfiguration.DriversExcluded 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Update/ExcludeWUDriversInQualityUpdate

### <a name="windowsupdateforbusinessconfigurationengagedrestartdeadlineforfeatureupdatesindays"></a>WindowsUpdateForBusinessConfiguration.EngagedRestartDeadlineForFeatureUpdatesInDays 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Update/EngagedRestartDeadlineForFeatureUpdates

### <a name="windowsupdateforbusinessconfigurationengagedrestartdeadlineindays"></a>WindowsUpdateForBusinessConfiguration.EngagedRestartDeadlineInDays 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Update/EngagedRestartDeadline

### <a name="windowsupdateforbusinessconfigurationengagedrestartsnoozescheduleforfeatureupdatesindays"></a>WindowsUpdateForBusinessConfiguration.EngagedRestartSnoozeScheduleForFeatureUpdatesInDays 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Update/EngagedRestartSnoozeScheduleForFeatureUpdates

### <a name="windowsupdateforbusinessconfigurationengagedrestartsnoozescheduleindays"></a>WindowsUpdateForBusinessConfiguration.EngagedRestartSnoozeScheduleInDays 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Update/EngagedRestartSnoozeSchedule

### <a name="windowsupdateforbusinessconfigurationengagedrestarttransitionscheduleforfeatureupdatesindays"></a>WindowsUpdateForBusinessConfiguration.EngagedRestartTransitionScheduleForFeatureUpdatesInDays 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Update/EngagedRestartTransitionScheduleForFeatureUpdates

### <a name="windowsupdateforbusinessconfigurationengagedrestarttransitionscheduleindays"></a>WindowsUpdateForBusinessConfiguration.EngagedRestartTransitionScheduleInDays 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Update/EngagedRestartTransitionSchedule

### <a name="windowsupdateforbusinessconfigurationfeatureupdatesdeferralperiodindays"></a>WindowsUpdateForBusinessConfiguration.FeatureUpdatesDeferralPeriodInDays 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Update/DeferFeatureUpdatesPeriodInDays

### <a name="windowsupdateforbusinessconfigurationfeatureupdatespaused"></a>WindowsUpdateForBusinessConfiguration の一時停止 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Update/PauseFeatureUpdates

### <a name="windowsupdateforbusinessconfigurationfeatureupdatespausestartdatetime"></a>WindowsUpdateForBusinessConfiguration.FeatureUpdatesPauseStartDateTime 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Update/PauseFeatureUpdatesStartTime

### <a name="windowsupdateforbusinessconfigurationfeatureupdatesrollbackstartdatetime"></a>WindowsUpdateForBusinessConfiguration.FeatureUpdatesRollbackStartDateTime
**CSP**:N/A-**オフセット URI**のみを Graph API します。N/A-Graph API のみ

### <a name="windowsupdateforbusinessconfigurationfeatureupdateswillberolledback"></a>WindowsUpdateForBusinessConfiguration によって元に戻されます。 
**CSP**:N/A-**オフセット URI**のみを Graph API します。N/A-Graph API のみ

### <a name="windowsupdateforbusinessconfigurationfeatureupdatesrollbackwindowindays"></a>WindowsUpdateForBusinessConfiguration.FeatureUpdatesRollbackWindowInDays
**CSP**:N/A-**オフセット URI**のみを Graph API します。N/A-Graph API のみ

### <a name="windowsupdateforbusinessconfigurationinstallationschedule"></a>WindowsUpdateForBusinessConfiguration
**CSP**:./DEVICE/VENDOR/MSFT/POLICY **Offset URI**:/Config/Update/activetime start、/Config/update/active、/Config/Update/scheduledinstallday、/config/scheduledinstalltime

### <a name="windowsupdateforbusinessconfigurationmicrosoftupdateserviceallowed"></a>WindowsUpdateForBusinessConfiguration.MicrosoftUpdateServiceAllowed 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:///または、

### <a name="windowsupdateforbusinessconfigurationpreviewbuildsetting"></a>WindowsUpdateForBusinessConfiguration Buildsetting 
**CSP**:./Vendor/MSFT/Policy  
**オフセット URI**:/config/manageプレビュービルド

### <a name="windowsupdateforbusinessconfigurationqualityupdatesdeferralperiodindays"></a>WindowsUpdateForBusinessConfiguration.QualityUpdatesDeferralPeriodInDays 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Update/DeferQualityUpdatesPeriodInDays

### <a name="windowsupdateforbusinessconfigurationqualityupdatespaused"></a>WindowsUpdateForBusinessConfiguration.QualityUpdatesPaused 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Update/PauseQualityUpdates

### <a name="windowsupdateforbusinessconfigurationqualityupdatespausestartdatetime"></a>WindowsUpdateForBusinessConfiguration.QualityUpdatesPauseStartDateTime 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Update/PauseQualityUpdatesStartTime

### <a name="windowsupdateforbusinessconfigurationqualityupdatesrollbackstartdatetime"></a>WindowsUpdateForBusinessConfiguration.QualityUpdatesRollbackStartDateTime
**CSP**:N/A-**オフセット URI**のみを Graph API します。N/A-Graph API のみ

### <a name="windowsupdateforbusinessconfigurationqualityupdateswillberolledback"></a>WindowsUpdateForBusinessConfiguration.QualityUpdatesWillBeRolledBack 
**CSP**:N/A-**オフセット URI**のみを Graph API します。N/A-Graph API のみ

### <a name="windowsupdateforbusinessconfigurationscheduleimminentrestartwarninginminutes"></a>WindowsUpdateForBusinessConfiguration.ScheduleImminentRestartWarningInMinutes 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Update/ScheduleImminentRestartWarning

### <a name="windowsupdateforbusinessconfigurationschedulerestartwarninginhours"></a>WindowsUpdateForBusinessConfiguration.ScheduleRestartWarningInHours 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Update/ScheduleRestartWarning

### <a name="windowsupdateforbusinessconfigurationskipchecksbeforerestart"></a>WindowsUpdateForBusinessConfiguration。 SkipChecksBeforeRestart 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Update/SetEDURestart

### <a name="windowsupdateforbusinessconfigurationupdateweeks"></a>WindowsUpdateForBusinessConfiguration 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Update/ScheduledInstallEveryWeek、/Config/アップデート/scheduledinstallfirstweek、/Config/Update/scheduledinstall4 thweek、/Dns/アップデート/scheduledinstallweek、/Config/Update/ScheduledInstallThirdWeek

### <a name="windowsupdateforbusinessconfigurationuserpauseaccess"></a>WindowsUpdateForBusinessConfiguration.UserPauseAccess 
**CSP**:./Device/Vendor/MSFT/Policy  
**オフセット URI**:/Config/Update/SetDisablePauseUXAccess


## <a name="next-steps"></a>次の手順

- [デバイス構成の概要](device-profiles.md)
- [構成サービスプロバイダーのリファレンス](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference)(別の Docs サイトを開きます)
