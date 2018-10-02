---
title: Microsoft Intune - Azure での Windows Holographic for Business デバイス用のカスタム設定 | Microsoft Docs
description: カスタム プロファイルを作成して、Microsoft Intune で Windows Holographic for Business を実行しているデバイスに対して OMA-URI 設定を使用します。 AllowFastReconnect、AllowVPN、AllowUpdateService、UpdateServiceURL、RequireUpdatesApproval、ApprovedUpdates、および ApplicationLaunchRestrictions ポリシー構成サービス プロバイダー (CSP) の設定を行うことができます。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 4/26/2018
ms.article: article
ms.prod: ''
ms.service: microsoft-intune
ms.topic: article
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b8ba5078d304c0e9d6b10e4efb868642323c901c
ms.sourcegitcommit: 2795255e89cbe97d0b17383d446cca57c7335016
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/27/2018
ms.locfileid: "47403580"
---
# <a name="custom-device-settings-for-devices-running-windows-holographic-for-business-in-intune"></a>Intune での Windows Holographic for Business を実行しているデバイスに対するカスタム デバイス設定

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

 デバイスで機能の制御に使用できる OMA-URI (Open Mobile Alliance Uniform Resource Identifier) の設定を展開するには、Windows Holographic for Business 用の Microsoft Intune **カスタム** プロファイルを使います。 Windows Holographic for Business では、構成サービス プロバイダー (CSP) の多くの設定を利用できます。 CSP の概要については、「[構成サービス プロバイダー (CSP) の概要 (IT 担当者向け)](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers)」をご覧ください。 Windows Holographic で特定の CSP がサポートされているかどうかについては、「[CSPs supported in Windows Holographic](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens)」(Windows Holographic でサポートされている CSP) をご覧ください。

特定の設定を探している場合、[Windows Holographic for Business デバイス制限プロファイル](device-restrictions-windows-holographic.md)には多くの組み込み設定が含まれ、カスタム値を指定する必要がないことに留意してください。

## <a name="create-the-custom-oma-uri-profile"></a>カスタム OMA-URI プロファイルを作成する

1. [Microsoft Intune でのカスタム デバイス設定の構成](custom-settings-configure.md)に関するページの手順に従って開始します。
2. **[プロファイルの作成]** で **[設定]** を選択し、1 つまたは複数の OMA-URI 設定を追加します。
3. **[OMA-URI のカスタム設定]** で **[追加]** をクリックして、新しい値を追加します。 **[エクスポート]** をクリックして、コンマ区切り値 (.csv) ファイルで構成した値の一覧を作成することもできます。
4. 各 OMA-URI 設定を追加するには、次の情報を入力します。
  - **設定名**: OMA-URI 設定の一意の名前を入力すると、設定リスト内で容易に識別できます。
  - **設定の説明**: 必要に応じて、設定の説明を入力します。
  - **データ型**: 以下から選択します。
    - **文字列**
    - **文字列型 (XML)**
    - **日付と時刻**
    - **整数型**
    - **浮動小数点**
    - **ブール型**
  - **OMA-URI (大文字と小文字を区別)**: 設定対象の OMA-URI を入力します。
  - **値**:入力した OMA-URI に関連付ける値を入力します。
5. 完了したら、**[プロファイルの作成]** に戻り、**[作成]** をクリックします。 プロファイルが作成され、プロファイル一覧に表示されます。

## <a name="recommended-custom-settings"></a>推奨されるカスタム設定

次の設定は、Windows Holographic for Business を実行しているデバイスにも役立ちます。

### <a name="allowfastreconnecthttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-authenticationauthentication-allowfastreconnect"></a>[AllowFastReconnect](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-allowfastreconnect)

> [!div class="mx-tableFixed"]
> |OMA-URI|［データの種類］|
> |---|---|
> |./Vendor/MSFT/Policy/Config/Authentication/AllowFastReconnect|整数<br/>0: 許可しません<br/>1: 許可します (既定)|

### <a name="allowupdateservicehttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-updateupdate-allowupdateservice"></a>[AllowUpdateService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowupdateservice)

> [!div class="mx-tableFixed"]
> |OMA-URI|［データの種類］|
> |---|---|
> |./Vendor/MSFT/Policy/Config/Update/AllowUpdateService|整数<br/>0: 更新サービスは許可されません <br/>1: 更新サービスは許可されます (既定)。|

### <a name="allowvpnhttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-settingssettings-allowvpn"></a>[AllowVPN](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-settings#settings-allowvpn)

> [!div class="mx-tableFixed"]
> |OMA-URI|［データの種類］|
> |---|---|
> |./Vendor/MSFT/Policy/Config/Settings/AllowVPN|整数<br/>0: 許可しません<br/>1: 許可します (既定)|

### <a name="requireupdatesapprovalhttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-updateupdate-requireupdateapproval"></a>[RequireUpdatesApproval](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-requireupdateapproval)

> [!div class="mx-tableFixed"]
> |OMA-URI|［データの種類］|
> |---|---|
> |./Vendor/MSFT/Policy/Config/Update/RequireUpdateApproval|整数<br/>0: 構成されていません デバイスは、適用可能なすべての更新プログラムをインストールします。<br/>1: デバイスは、適用可能で、[承認された更新プログラム] リストに表示される更新プログラムのみをインストールします。 展開前にテストが必要な場合など、IT 部門がデバイス上の更新プログラムの展開を制御する場合は、このポリシーを 1 に設定します。|

### <a name="scheduledinstalltimehttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-updateupdate-scheduledinstalltime"></a>[ScheduledInstallTime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-scheduledinstalltime)

> [!div class="mx-tableFixed"]
> |OMA-URI|［データの種類］|
> |---|---|
> |./Vendor/MSFT/Policy/Config/Update/ScheduledInstallTime|Integer 0-23、ここで 0=12AM および 23=11PM<br/>既定値は 3 です。|

### <a name="updateserviceurlhttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-updateupdate-updateserviceurl"></a>[UpdateServiceURL](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-updateserviceurl)

> [!div class="mx-tableFixed"]
> |OMA-URI|［データの種類］|
> |---|---|
> |./Vendor/MSFT/Policy/Config/Update/UpdateServiceUrl|文字列型<br/>URL: デバイスは、指定された URL にある WSUS サーバーから更新プログラムを確認します。<br/>未構成: デバイスは、Microsoft Update から更新プログラムを確認します。|

### <a name="approvedupdateshttpsdocsmicrosoftcomwindowsclient-managementmdmupdate-csp"></a>[ApprovedUpdates](https://docs.microsoft.com/windows/client-management/mdm/update-csp)

> [!div class="mx-tableFixed"]
> |OMA-URI|［データの種類］|
> |---|---|
> |./Vendor/MSFT/Update/ApprovedUpdates/*GUID*<br/><br/>**重要**<br/>管理者は、エンド ユーザーの代わりに更新プログラムの EULA を読み、同意する必要があります。 この手順を怠ると、法律または契約上の義務に違反することになります。|エンド ユーザーの代理で行う更新プログラムの承認および EULA 同意のためのノード。<br/><br/>詳細については、「[Update CSP](https://docs.microsoft.com/windows/client-management/mdm/update-csp)」(CSP の更新) を参照してください。|

### <a name="applicationlaunchrestrictionshttpsdocsmicrosoftcomwindowsclient-managementmdmapplocker-csp"></a>[ApplicationLaunchRestrictions](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp)

> [!div class="mx-tableFixed"]
> |OMA-URI|［データの種類］|
> |----|---|
> |./Vendor/MSFT/AppLocker/ApplicationLaunchRestrictions/*Grouping*/*ApplicationType*/Policy<br/><br/>**重要**<br/>AppLocker CSP の記事では、エスケープされた XML の例を使用しています。 Intune カスタム プロファイルを含む設定を構成するには、プレーン XML を使用する必要があります。|文字列型<br/>詳細については、「[AppLocker CSP](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp)」を参照してください。|

### <a name="deletionpolicyhttpsdocsmicrosoftcomwindowsclient-managementmdmaccountmanagement-csp"></a>[DeletionPolicy](https://docs.microsoft.com/windows/client-management/mdm/accountmanagement-csp)

> [!div class="mx-tableFixed"]
> |OMA-URI|［データの種類］|
> |----|---|
> |./Vendor/MSFT/AccountManagement/UserProfileManagement/DeletionPolicy|整数<br/>0 - デバイスが現在アクティブなユーザーがいない状態に戻るとすぐに削除します<br/>1 - ストレージ容量のしきい値に達したときに削除します (既定)<br/>2 - ストレージ容量のしきい値とプロファイルの非アクティブな時間のしきい値の両方に達したときに削除します|

### <a name="enableprofilemanagerhttpsdocsmicrosoftcomwindowsclient-managementmdmaccountmanagement-csp"></a>[EnableProfileManager](https://docs.microsoft.com/windows/client-management/mdm/accountmanagement-csp)

> [!div class="mx-tableFixed"]
> |OMA-URI|［データの種類］|
> |----|---|
> |./Vendor/MSFT/AccountManagement/UserProfileManagement/EnableProfileManager|ブール型<br/>True - 有効<br/>False - 無効 (既定)|

### <a name="profileinactivitythresholdhttpsdocsmicrosoftcomwindowsclient-managementmdmaccountmanagement-csp"></a>[ProfileInactivityThreshold](https://docs.microsoft.com/windows/client-management/mdm/accountmanagement-csp)

> [!div class="mx-tableFixed"]
> |OMA-URI|［データの種類］|
> |----|---|
> |./Vendor/MSFT/AccountManagement/UserProfileManagement/ProfileInactivityThreshold|整数<br/>既定値は 30 です。|


### <a name="storagecapacitystartdeletionhttpsdocsmicrosoftcomwindowsclient-managementmdmaccountmanagement-csp"></a>[StorageCapacityStartDeletion](https://docs.microsoft.com/windows/client-management/mdm/accountmanagement-csp)

> [!div class="mx-tableFixed"]
> |OMA-URI|［データの種類］|
> |----|---|
> |./Vendor/MSFT/AccountManagement/UserProfileManagement/StorageCapacityStartDeletion|整数<br/>既定値は 25 です。|

### <a name="storagecapacitystopdeletionhttpsdocsmicrosoftcomwindowsclient-managementmdmaccountmanagement-csp"></a>[StorageCapacityStopDeletion](https://docs.microsoft.com/windows/client-management/mdm/accountmanagement-csp)

> [!div class="mx-tableFixed"]
> |OMA-URI|［データの種類］|
> |----|---|
> |./Vendor/MSFT/AccountManagement/UserProfileManagement/StorageCapacityStopDeletion|整数<br/>既定値は 50 です。|

## <a name="find-the-policies-you-can-configure"></a>構成できるポリシーを見つける

「[CSPs supported in Windows Holographic](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens)」(Windows Holographic でサポートされている CSP) で、Windows Holographic によってサポートされているすべての構成サービス プロバイダー (CSP) の完全な一覧がわかります。 Windows Holographic のバージョンによっては、一部の設定に互換性がありません。 Windows 記事の表を見れば、各 CSP でサポートされているバージョンを確認できます。

また、記事の一覧にある設定の一部は Intune でサポートされていません。 Intune で必要な設定がサポートされているかどうかを確認するには、その設定の記事を開きます。 各設定ページには、サポートされている操作が示されます。 Intune で利用するには、その設定で**追加**操作または**置換**操作がサポートされている必要があります。
