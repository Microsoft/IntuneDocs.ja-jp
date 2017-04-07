---
title: "Windows 10 デバイス向けの Intune カスタム設定"
titleSuffix: Intune Azure preview
description: "Intune Azure プレビュー: Windows 10 カスタム プロファイルで使用できる設定について説明します。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7bcea136-7260-4042-b21b-c7dab86b380d
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 647415914fb0f44807eff7baf7a56ea3a382f027
ms.lasthandoff: 02/18/2017


---

# <a name="custom-device-settings-for-windows-10-devices-in-microsoft-intune"></a>Microsoft Intune での Windows 10 デバイス向けのカスタム デバイス設定

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

 Windows 10 と Windows 10 Mobile 用の Microsoft Intune **カスタム** プロファイルを使用して、デバイスで各機能の制御に使用できる OMA-URI (Open Mobile Alliance Uniform Resource Identifier) 設定を展開します。 Windows 10 では、[Policy Configuration Service プロバイダー (Policy CSP)](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers) を通して多くの設定を使用できます。

1. 「[How to configure custom device settings in Microsoft Intune (Microsoft Intune でカスタム デバイス設定を構成する方法)](how-to-configure-custom-settings.md)」の手順に従って開始します。
2. **[プロファイルを作成します]** ブレードで **[設定]** を選択し、1 つまたは複数の OMA-URI 設定を追加します。
3. **[OMA-URI のカスタム設定]** ブレードで **[追加]** をクリックして、新しい値を追加します。 **[エクスポート]** をクリックして、コンマ区切り値 (.csv) ファイルで構成した値の一覧を作成することもできます。
4. 各 OMA-URI 設定を追加するには、次の情報を入力します。 このトピックにあるリストを使用して、使用できる設定の詳細について説明します。
    - **設定名** - OMA-URI 設定の一意の名前を入力すると、設定リスト内で容易に識別できます。
    - **設定の説明** - 必要に応じて、設定の説明を入力します。
    - **データ型** - 以下から選択します。
        - **文字列**
        - **文字列型 (XML)**
        - **日付と時刻**
        - **整数型**
        - **浮動小数点**
        - **ブール型**
    - **OMA-URI (大文字と小文字を区別)** - 設定対象の OMA-URI を指定します。
    - **値** - 入力した OMA-URI に関連付ける値を指定します。
5. 完了したら、**[プロファイルを作成します]** ブレードに戻り、**[作成]** をクリックします。
プロファイルが作成され、プロファイルの一覧ブレードに表示されます。

## <a name="example"></a>例
以下のスクリーン ショットで、**Connectivity/AllowVPNOverCellular** 設定が有効になりました。 これにより、移動体通信ネットワーク上の Windows 10 デバイスで OpenVPN 接続を利用できます。

> ![VPN 設定を含むカスタム ポリシーの例](./media/custom-policy-example.png)


## <a name="policy-settings"></a>ポリシー設定

|ポリシー名と URI|説明|
|---------------|------------|-----------|
|**自動更新を許可する**<br>./Vendor/MSFT/Policy/Config/Update/AllowAutoUpdate|デスクトップのみ<br>**データ型:** 整数<br />**値:** **0** - **5** (既定: **1**)|
|**インストール日のスケジュール設定**<br>./Vendor/MSFT/Policy/Config/Update/ScheduledInstallDay|モバイルのみ<br>**データ型:** 整数<br />**値:**<br>**0** : 毎日 (既定値)<br>**1**: 日曜日<br>**2**: 月曜日<br>**3**: 火曜日<br>**4**: 水曜日<br>**5**: 木曜日<br>**6**: 金曜日<br>**7**: 土曜日|
|**インストール時刻のスケジュール設定**<br>./Vendor/MSFT/Policy/Config/Update/ScheduledInstallTime|デスクトップおよびモバイル<br />**データ型:** 整数<br />**値:** **0** ～ **23** 時間 (**0** は午前&0; 時) (既定: **3**)|
|**DeviceLock/AllowIdleReturnWithoutPassword**<br>./Vendor/MSFT/Policy/Config/DeviceLock/AllowIdleReturnWithoutPassword|モバイルのみ<br />**データ型:** 整数<br />**値:**<br>**0**: ユーザーはパスワードの猶予期間タイマーを設定できず、値は "毎回" に設定されます。<br>**1**: ユーザーがパスワードの猶予期間タイマーを設定できます (既定)。|
|**WiFi/AllowWiFi**<br>./Vendor/MSFT/Policy/Config/WiFi/AllowWiFi|モバイルのみ<br />**データ型:** 整数<br />**値:**<br>**0**: **Wi-Fi 接続の使用**を許可しません。<br>**1**: **Wi-Fi 接続の使用を許可** します (既定)。|
|**WiFi/AllowInternetSharing**<br>./Vendor/MSFT/Policy/Config/WiFi/AllowInternetSharing|デスクトップおよびモバイル<br>**データ型:** 整数<br />**値:** **0**: インターネット共有を許可しません。**1**: インターネット共有を許可します (既定)。|
|**WiFi/AllowAutoConnectToWiFiSenseHotspots**<br>./Vendor/MSFT/Policy/Config/WiFi/AllowAutoConnectToWiFiSenseHotspots|デスクトップおよびモバイル<br />**データ型:** 整数<br />**値:** **0**: 許可しません。**1**: 許可します (既定)。|
|**WiFi/AllowManualWiFiConfiguration**<br>./Vendor/MSFT/Policy/Config/WiFi/AllowManualWiFiConfiguration|モバイルのみ<br />**データ型:** 整数<br />**値:**<br>**0**: MDM でプロビジョニングされていない Wi-Fi 接続を許可しません。<br>**1**: MDM で既にプロビジョニングされたネットワーク SSID 以外の新しいネットワーク SSID の追加を許可します (既定)。|
|**System/AllowLocation**<br>./Vendor/MSFT/Policy/Config/System/AllowLocation|デスクトップおよびモバイル<br />**データ型:** 整数<br />**値:** **0**: 許可しません。**1**: 許可します (既定)。|
|**System/AllowTelemetry**<br>./Vendor/MSFT/Policy/Config/System/AllowTelemetry|デスクトップおよびモバイル<br>**データ型:** 整数<br />**値:**<br>**0** : 許可しません (Enterprise のみの設定)<br>**1** : 制限あり<br>**2**: すべて (既定)<br>**3**: すべてと診断情報|
|**System/AllowExperimentation**<br>./Vendor/MSFT/Policy/Config/System/AllowExperimentation|デスクトップおよびモバイル<br />**データ型:** 整数<br />**値:**<br>**0** : 許可しません。<br>**1**: 設定のみ (既定)<br>**2**: 設定と実験|
|**Security/AntiTheftMode**<br>./Vendor/MSFT/Policy/Config/Security/AntiTheftMode|モバイルのみ<br />**データ型:** 整数<br />**値:**<br>**0**: 盗難防止モードを許可しません。<br>**1**: ユーザーの設定 (既定)|
|**Connectivity/AllowUSBConnection**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowUSBConnection|モバイルのみ<br />**データ型:** 整数<br />**値:** **0**: 許可しません。**1**: 許可します (既定)。|
|**System/AllowUserToResetPhone**<br>./Vendor/MSFT/Policy/Config/System/AllowUserToResetPhone|モバイルのみ<br />**データ型:** 整数<br />**値:** **0**: 許可しません。**1**: 許可します (既定)。|
|**Connectivity/AllowCellularDataRoaming**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowCellularDataRoaming|デスクトップおよびモバイル<br />**データ型:** 整数<br />**値:** **0**: 許可しません。**1**: 許可します (既定)。|
|**Connectivity/AllowVPNOverCellular**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNOverCellular|デスクトップおよびモバイル<br />**データ型:** 整数<br />**値:**<br>**0**: VPN で携帯電話による接続を許可しません。<br>**1**: VPN で携帯電話を含む任意の接続を使用できます (既定)。|
|**Connectivity/AllowVPNRoamingOverCellular**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNRoamingOverCellular|モバイルのみ<br />**データ型:** 整数<br />**値:** **0**: 許可しません。**1**: 許可します (既定)。|
|**Connectivity/AllowVPNRoamingOverCellular**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNRoamingOverCellular|モバイルのみ<br />**データ型:** 整数<br />**値:** **0**: 許可しません。**1**: 許可します (既定)。|
|**Connectivity/AllowBluetooth**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowBluetooth|デスクトップおよびモバイル<br />**データ型:** 整数<br />**値:**<br>**0**: ユーザーが Bluetooth を有効にすることを許可しません。<br>**1**: 予約済み。 ユーザーが Bluetooth を有効にして構成することができます (Windows Phone 8.1 (MDM または EAS 対応)、Windows 10 デスクトップ、Windows 10 Mobile ではサポートされていません)。<br>**2**: 許可済み。 ユーザーが Bluetooth を有効にして構成することができます (既定)。|
|**Experience/AllowScreenCapture**<br>./Vendor/MSFT/Policy/Config/Experience/AllowScreenCapture|モバイルのみ<br />**データ型:** 整数<br />**値:** **0**: 許可しません。**1**: 許可します (既定)。|
|**Experience/AllowTaskSwitcher**<br>./Vendor/MSFT/Policy/Config/Experience/AllowTaskSwitcher|モバイルのみ<br />**データ型:** 整数<br />**値:** **0**: 許可しません。**1**: 許可します (既定)。|
|**Experience/AllowVoiceRecording**<br>./Vendor/MSFT/Policy/Config/Experience/AllowVoiceRecording|モバイルのみ<br />**データ型:** 整数<br />**値:** **0**: 許可しません。**1**: 許可します (既定)。|
|**Experience/AllowSyncMySettings**<br>./Vendor/MSFT/Policy/Config/Experience/AllowSyncMySettings|モバイルのみ<br />**データ型:** 整数<br />**値:** **0**: ローミングを許可しません。**1**: ローミングを許可します (既定)。|
|**Experience/AllowManualMDMUnenrollment**<br>./Vendor/MSFT/Policy/Config/Experience/AllowManualMDMUnenrollment|デスクトップおよびモバイル<br />**データ型:** 整数<br />**値:** **0**: 許可しません。**1**: 許可します (既定)。|
|**Accounts/AllowMicrosoftAccountConnection**<br>./Vendor/MSFT/Policy/Config/Accounts/AllowMicrosoftAccountConnection|デスクトップおよびモバイル<br />**データ型:** 整数<br />**値:** **0**: 許可しません。**1**: 許可します (既定)。|
|**Accounts/AllowAddingNonMicrosoftAccountsManually**<br>./Vendor/MSFT/Policy/Config/Accounts/AllowAddingNonMicrosoftAccountsManually|デスクトップおよびモバイル<br />**データ型:** 整数<br />**値:** **0**: 許可しません。**1**: 許可します (既定)。|
|**Security/AllowManualRootCertificateInstallation**<br>./Vendor/MSFT/Policy/Config/Security/AllowManualRootCertificateInstallation|モバイルのみ<br />**データ型:** 整数<br />**値:** **0**: 許可しません。**1**: 許可します (既定)。|
|**Security/AllowAddProvisioningPackages**<br>./Vendor/MSFT/Policy/Config/Security/AllowAddProvisioningPackages|デスクトップおよびモバイル<br />**データ型:** 整数<br />**値:** **0**: 許可しません。**1**: 許可します (既定)。|
|**Search/DisableBackoff**<br>./Vendor/MSFT/Policy/Config/Search/DisableBackoff|デスクトップおよびモバイル<br />**データ型:** 整数<br />**値:** **0** (既定)、**1**|
|**Search/PreventRemoteQueries**<br>./Vendor/MSFT/Policy/Config/Search/PreventRemoteQueries|デスクトップおよびモバイル<br />**データ型:** 整数<br />**値:** **0**、**1**(既定)|
|**Search/AllowUsingDiacritics**<br>./Vendor/MSFT/Policy/Config/Search/AllowUsingDiacritics|デスクトップおよびモバイル<br />**データ型:** 整数<br />**値:** **0** (既定)、**1**|
|**Search/AlwaysUseAutoLangDetection**<br>./Vendor/MSFT/Policy/Config/Search/AlwaysUseAutoLangDetection|デスクトップおよびモバイル<br />**データ型:** 整数<br />**値:** **0** (既定)、**1**|
|**Search/DisableRemovableDriveIndexing**<br>./Vendor/MSFT/Policy/Config/Search/DisableRemovableDriveIndexing|デスクトップおよびモバイル<br />**データ型:** 整数<br />**値:** **0** (既定)、**1**|
|**Search/PreventIndexingLowDiskSpaceMB**<br>./Vendor/MSFT/Policy/Config/Search/PreventIndexingLowDiskSpaceMB|デスクトップおよびモバイル<br />**データ型:** 整数<br />**値:** **0**、**1**(既定)|
|**Search/AllowIndexingEncryptedStoresOrItems**<br>./Vendor/MSFT/Policy/Config/Search/AllowIndexingEncryptedStoresOrItems|デスクトップおよびモバイル<br />**データ型:** 整数<br />**値:** **0** (既定)、**1**|
|**Security/AllowRemoveProvisioningPackage**<br>./Vendor/MSFT/Policy/Config/Security/AllowRemoveProvisioningPackage|デスクトップおよびモバイル<br />**データ型:** 整数<br />**値:** **0**: 許可しません。**1**: 許可します (既定)。|
|**Security/RequireProvisioningPackageSignature**<br>./Vendor/MSFT/Policy/Config/Security/RequireProvisioningPackageSignature|デスクトップおよびモバイル<br />**データ型:** 整数<br />**値:** **0** (既定)、**1**|
|**AboveLock/AllowActionCenterNotifications**<br>./Vendor/MSFT/Policy/Config/AboveLock/AllowActionCenterNotifications|デスクトップおよびモバイル<br />**データ型:** 整数<br />**値:** **0**: 許可しません。**1**: 許可します (既定)。|
|**TextInput/AllowIMENetworkAccess**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowIMENetworkAccess|デスクトップのみ<br />**データ型:** 整数<br />**値:**<br>**0** : 許可しません。<br>オープン拡張辞書がオフになります。<br>ユーザーは次の操作を実行できません。<br>- 新しいオープン拡張辞書を追加する<br />- 新しい検索統合構成ファイルを追加する<br>- クラウドの候補機能を使用する<br>- ユーザーが登録した単語を送信する<br>**1**: 許可します。<br>オープン拡張辞書を追加して、既定で使用できます。 既定で検索統合機能も使用できます。<br>ユーザーは次の操作を実行できます。<br>クラウドの候補機能を使用する。|
|**TextInput/AllowIMELogging**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowIMELogging|デスクトップのみ<br />**データ型:** 整数<br />**値:**<br>**0**: 誤変換記録機能が無効になります。<br>**1**: 誤変換記録機能が有効になります (既定)。|
|**TextInput/AllowJapaneseNonPublishingStandardGlyph**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseNonPublishingStandardGlyph|デスクトップのみ<br />**データ型:** 整数<br />**値:** **0**: 許可しません。**1**: 許可します (既定)。|
|**TextInput/AllowJapaneseIVSCharacters**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseIVSCharacters|デスクトップのみ<br />**データ型:** 整数<br />**値:** **0**: 許可しません。**1**: 許可します (既定)。|
|**TextInput/AllowJapaneseUserDictionary**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseUserDictionary|デスクトップのみ<br />**データ型:** 整数<br />**値:** **0**: 許可しません。**1**: 許可します (既定)。|
|**TextInput/AllowJapaneseIMESurrogatePairCharacters**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseIMESurrogatePairCharacters|デスクトップのみ<br />**データ型:** 整数<br />**値:** **0**: 許可しません。**1**: 許可します (既定)。|
|**TextInput/ExcludeJapaneseIMEExceptShiftJIS**<br>./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptShiftJIS|デスクトップのみ<br />**データ型:** 整数<br />**値:**<br>**0**: 文字はフィルター処理されません (既定)。<br>**1**: Shift JIS の文字を除くすべての文字をフィルター処理します。|
|**TextInput/ExcludeJapaneseIMEExceptJIS0208**<br>./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptJIS0208|デスクトップのみ<br />**データ型:** 整数<br />**値:**<br />**0**: 文字はフィルター処理されません (既定)。<br>**1**: JIS0208 の文字を除くすべての文字をフィルター処理します。|
|**TextInput/ExcludeJapaneseIMEExceptJIS0208andEUDC**<br>./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptJIS0208andEUDC|デスクトップのみ<br />**データ型:** 整数<br />**値:**<br>**0**: 文字はフィルター処理されません (既定)。<br>**1**: JIS0208 の文字または外字の文字を除くすべての文字をフィルター処理します。|
|**TextInput/AllowInputPanel**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowInputPanel|デスクトップのみ<br />**データ型:** 整数<br />**値:** **0**: 許可しません。**1**: 許可します (既定)。|
|**Bluetooth/AllowDiscoverableMode**<br>./Vendor/MSFT/Policy/Config/Bluetooth/AllowDiscoverableMode|デスクトップおよびモバイル<br />**データ型:** 整数<br />**値:** **0**: 許可しません。**1**: 許可します (既定)。|
|**Bluetooth/AllowAdvertising**<br>./Vendor/MSFT/Policy/Config/Bluetooth/AllowAdvertising|デスクトップおよびモバイル<br />**データ型:** 整数<br />**値:** **0**: 許可しません。**1**: 許可します (既定)。|
|**Settings/AllowDataSense**<br>./Vendor/MSFT/Policy/Config/Settings/AllowDataSense|デスクトップおよびモバイル<br />**データ型:** 整数<br />**値:** **0**: 許可しません。**1**: 許可します (既定)。|
|**Settings/AllowVPN**<br>./Vendor/MSFT/Policy/Config/Settings/AllowVPN|デスクトップおよびモバイル<br />**データ型:** 整数<br />**値:** **0**: 許可しません。**1**: 許可します (既定)。|
|**Settings/AllowWorkplace**<br>./Vendor/MSFT/Policy/Config/Settings/AllowWorkplace|デスクトップのみ<br />**データ型:** 整数<br />**値:** **0**: 許可しません。**1**: 許可します (既定)。|
|**Settings/AllowDateTime**<br>./Vendor/MSFT/Policy/Config/Settings/AllowDateTime|デスクトップおよびモバイル<br />**データ型:** 整数<br />**値:** **0**: 許可しません。**1**: 許可します (既定)。|
|**Settings/AllowLanguage**<br>./Vendor/MSFT/Policy/Config/Settings/AllowLanguage|デスクトップのみ<br />**データ型:** 整数<br />**値:** **0**: 許可しません。**1**: 許可します (既定)。|
|**Settings/AllowRegion**<br>./Vendor/MSFT/Policy/Config/Settings/AllowRegion|デスクトップのみ<br />**データ型:** 整数<br />**値:** **0**: 許可しません。**1**: 許可します (既定)。|
|**Settings/AllowSignInOptions**<br>./Vendor/MSFT/Policy/Config/Settings/AllowSignInOptions|デスクトップのみ<br />**データ型:** 整数<br />**値:** **0**: 許可しません。**1**: 許可します (既定)。|
|**Settings/AllowYourAccount**<br>./Vendor/MSFT/Policy/Config/Settings/AllowYourAccount|デスクトップおよびモバイル<br />**データ型:** 整数<br />**値:** **0**: 許可しません。**1**: 許可します (既定)。|
|**Settings/AllowPowerSleep**<br>./Vendor/MSFT/Policy/Config/Settings/AllowPowerSleep|デスクトップのみ<br />**データ型:** 整数<br />**値:** **0**: 許可しません。**1**: 許可します (既定)。|
|**Settings/AllowAutoPlay**<br>./Vendor/MSFT/Policy/Config/Settings/AllowAutoPlay|デスクトップのみ<br />**データ型:** 整数<br />**値:** **0**: 許可しません。**1**: 許可します (既定)。|
|**Experience/AllowCortana**<br>./Vendor/MSFT/Policy/Config/Experience/AllowCortana|デスクトップおよびモバイル<br />**データ型:** 整数<br />**値:** **0**: 許可しません。**1**: 許可します (既定)。|
|**Search/SafeSearchPermissions**<br>./Vendor/MSFT/Policy/Config/Search/SafeSearchPermissions|モバイルのみ<br />**データ型:** 整数<br />**値:**<br>**0** : 厳密。成人向けコンテンツに対して最高レベルのフィルター処理を実行します。<br>**1**: 中程度。成人向けコンテンツに対して中程度のフィルター処理を実行します (有効な検索結果はフィルター処理されません) (既定)。|
|**Experience/AllowCopyPaste**<br>./Vendor/MSFT/Policy/Config/Experience/AllowCopyPaste|デスクトップのみ<br />**データ型:** 整数<br />**値:** **0**: 許可しません。**1**: 許可します (既定)。|
|**Force Start Size**<br>./Vendor/MSFT/Policy/Config/Start/ForceStartSize|モバイルのみ<br />**データ型:** 整数<br />**値:**<br>**0**: ユーザーによるサイズ変更を許可します (既定)。<br>**1**: 非全画面表示を強制します。<br>**2**: 全画面表示を強制します。|
|**Update/RequireDeferUpgrade**<br>./Vendor/MSFT/Policy/Config/Update/RequireDeferUpgrade|デスクトップおよびモバイル<br />**データ型:** 整数<br />**値:**<br>**0**: アップグレードを遅延せず、CB (現在のブランチ) を維持します (既定)。<br>**1**: 更新とアップグレードの遅延を有効にします。デバイスは CBB (ビジネスの現在のブランチ) の規則に従います。<br />詳細については、以下を参照してください。<br>[Windows 10 サービスの概要](https://technet.microsoft.com/library/mt598226.aspx)<br>[Windows 10 の展開計画](https://technet.microsoft.com/library/mt574241.aspx)|
|**Update/DeferUpdatePeriod**<br>./Vendor/MSFT/Policy/Config/Update/DeferUpdatePeriod|デスクトップおよびモバイル<br>**説明:** ソフトウェアの更新を最大 4 週間遅延させるポリシー。<br />**データ型:** 整数<br />**値:**<br> **0**: 直ちに更新プログラムを適用します (既定)。<br>**1 ** - **4**: ソフトウェアの更新を遅延する期間 (週)。<br />詳細については、以下を参照してください。<br>[Windows 10 サービスの概要](https://technet.microsoft.com/library/mt598226.aspx)<br>[Windows 10 の展開計画](https://technet.microsoft.com/library/mt574241.aspx)|
|**Update/DeferUpgradePeriod**<br>./Vendor/MSFT/Policy/Config/Update/DeferUpgradePeriod|デスクトップおよびモバイル<br>**説明:** 機能のアップグレードを最大 8 か月間遅延させるポリシー。<br />**データ型:** 整数<br />**値:**<br>**0**: 直ちに更新プログラムを適用します (既定)。<br>**1** - **8**: 機能のアップグレードを遅延する期間 (月)。<br />詳細については、以下を参照してください。<br>[Windows 10 サービスの概要](https://technet.microsoft.com/library/mt598226.aspx)<br>[Windows 10 の展開計画](https://technet.microsoft.com/library/mt574241.aspx)|
|**Update/PauseDeferrals**<br>./Vendor/MSFT/Policy/Config/Update/PauseDeferrals|デスクトップおよびモバイル<br>**説明:** デバイスが更新とアップグレードの受信を 5 週間停止できるようにします。<br />**データ型:** 整数<br />**値:**<br>**0**: 直ちに更新プログラムを適用します (既定)。<br>**1**: 更新とアップグレードを一時停止します (一時停止の期限は 5 週間です)。|

## <a name="windows-defender-settings"></a>Windows Defender の設定

|ポリシー名と URI|説明|
|---------------|-----------|
|**AllowRealtimeMonitoring**<br>./Vendor/MSFT/Policy/Config/Defender/AllowRealtimeMonitoring|デスクトップのみ<br />**データ型:** 整数<br />**値:** **0**: 許可しません。**1**: 許可します (既定)。|
|**AllowBehaviorMonitoring**<br>./Vendor/MSFT/Policy/Config/Defender/AllowBehaviorMonitoring|デスクトップのみ<br />**データ型:** 整数<br />**値:** **0**: 許可しません。**1**: 許可します (既定)。|
|**AllowIntrusionPreventionSystem**<br>./Vendor/MSFT/Policy/Config/Defender/AllowIntrusionPreventionSystem|デスクトップのみ<br />**データ型:** 整数<br />**値:** **0**: 許可しません。**1**: 許可します (既定)。|
|**AllowIOAVProtection**<br>./Vendor/MSFT/Policy/Config/Defender/AllowIOAVProtection|デスクトップのみ<br />**データ型:** 整数<br />**値:** **0**: 許可しません。**1**: 許可します (既定)。|
|**AllowScriptScanning**<br>./Vendor/MSFT/Policy/Config/Defender/AllowScriptScanning|デスクトップのみ<br />**データ型:** 整数<br />**値:** **0**: 許可しません。**1**: 許可します (既定)。|
|**AllowOnAccessProtection**<br>./Vendor/MSFT/Policy/Config/Defender/AllowOnAccessProtection|デスクトップのみ<br />**データ型:** 整数<br />**値:** **0**: 許可しません。**1**: 許可します (既定)。|
|**RealTimeScanDirection**<br>./Vendor/MSFT/Policy/Config/Defender/RealTimeScanDirection|デスクトップのみ<br />**データ型:** 整数<br />**値:**<br>**0**: 全ファイルの監視 (既定)<br>**1** : 受信ファイルの監視<br>**2** : 送信ファイルの監視|
|**DaysToRetainCleanedMalware**<br>./Vendor/MSFT/Policy/Config/Defender/DaysToRetainCleanedMalware|デスクトップのみ<br />**データ型:** 整数<br />**値:**<br>**0**  -  **90**: マルウェアを保持する時間を表します。<br>**既定値:** **0**: 永続的に検疫フォルダー内に保持します。自動的に削除しません。|
|**AllowUserUIAccess**<br>./Vendor/MSFT/Policy/Config/Defender/AllowUserUIAccess|デスクトップのみ<br />**データ型:** 整数<br />**値:** **0**: 許可しません。**1**: 許可します (既定)。|
|**ScanParameter**<br>./Vendor/MSFT/Policy/Config/Defender/ScanParameter|デスクトップのみ<br />**データ型:** 整数<br />**値:**<br>**1**: クイック スキャン (既定)<br>**2**: フル スキャン|
|**ScheduleScanDay**<br>./Vendor/MSFT/Policy/Config/Defender/ScheduleScanDay|デスクトップのみ<br />**データ型:** 整数<br />**値:**<br>**0**: 毎日 (既定)<br>**1**: 月曜日<br>**2**: 火曜日<br>**3**: 水曜日<br>**4**: 木曜日<br>**5**: 金曜日<br>**6**: 土曜日<br>**7**: 日曜日<br>**8** : スキャンはスケジュールされません|
|**ScheduleScanTime**<br>./Vendor/MSFT/Policy/Config/Defender/ScheduleScanTime|デスクトップのみ<br />**データ型:** 整数<br />**値:**<br>**0**: 午前 12:00<br>**60** : 午前 1:00<br>**120**: 午前 2:00 (既定)<br>**180** : 午前 3:00<br>**240** : 午前 4:00<br>**300** : 午前 5:00<br>**360** : 午前 6:00<br>**420** : 午前 7:00<br>**480** : 午前 8:00<br>**540** : 午前 9:00<br>**600** : 午前 10:00<br>**660** : 午前 11:00<br>**720** : 午後 0:00<br>**780** : 午後 1:00<br>**840** : 午後 2:00<br>**900** : 午後 3:00<br>**960** : 午後 4:00<br>**1020** : 午後 5:00<br>**1080** : 午後 6:00<br>**1140** : 午後 7:00<br>**1200** : 午後 8:00<br>**1260** : 午後 9:00<br>**1320** : 午後 10:00<br>**1381** : メンテナンス期間|
|**ScheduleQuickScanTime**<br>./Vendor/MSFT/Policy/Config/Defender/ScheduleQuickScanTime|デスクトップのみ<br>**データ型:** 整数<br />**値:**<br>**0**: 午前 12:00<br>**60** : 午前 1:00<br>**120**: 午前 2:00 (既定)<br>**180** : 午前 3:00<br>**240** : 午前 4:00<br>**300** : 午前 5:00<br>**360** : 午前 6:00<br>**420** : 午前 7:00<br>**480** : 午前 8:00<br>**540** : 午前 9:00<br>**600** : 午前 10:00<br>**660** : 午前 11:00<br>**720** : 午後 0:00<br>**780** : 午後 1:00<br>**840** : 午後 2:00<br>**900** : 午後 3:00<br>**960** : 午後 4:00<br>**1020** : 午後 5:00<br>**1080** : 午後 6:00<br>**1140** : 午後 7:00<br>**1200** : 午後 8:00<br>**1260** : 午後 9:00<br>**1320** : 午後 10:00<br>**1380** : 午後 11:00|
|**AVGCPULoadFactor**<br>./Vendor/MSFT/Policy/Config/Defender/AVGCPULoadFactor|デスクトップのみ<br />**データ型:** 整数<br />**値:** **0** - **100** (既定: **50**)|
|**AllowArchiveScanning**<br>./Vendor/MSFT/Policy/Config/Defender/AllowArchiveScanning|デスクトップのみ<br />**データ型:** 整数<br />**値:** **0**: 許可しません。**1**: 許可します (既定)。|
|**AllowEmailScanning**<br>./Vendor/MSFT/Policy/Config/Defender/AllowEmailScanning|デスクトップのみ<br />**データ型:** 整数<br>**値:** **0** : 許可しない (既定)、**1** : 許可する|
|**AllowFullScanRemovableDriveScanning**<br>./Vendor/MSFT/Policy/Config/Defender/AllowFullScanRemovableDriveScanning|デスクトップのみ<br />**データ型:** 整数<br />**値:** **0** : 許可しない (既定)、**1** : 許可する|
|**AllowFullScanOnMappedNetworkDrives**<br>./Vendor/MSFT/Policy/Config/Defender/AllowFullScanOnMappedNetworkDrives|デスクトップのみ<br />**データ型:** 整数<br />**値:** **0**: 許可しません。**1**: 許可します (既定)。|
|**AllowScanningNetworkFiles**<br>./Vendor/MSFT/Policy/Config/Defender/AllowScanningNetworkFiles|デスクトップのみ<br />**データ型:** 整数<br />**値:** **0**: 許可しません。**1**: 許可します (既定)。許可に設定されている場合は、RTP がオンのときにも実行されます。|
|**SignatureUpdateInterval**<br>./Vendor/MSFT/Policy/Config/Defender/SignatureUpdateInterval|デスクトップのみ<br />**データ型:** 整数<br />**値:**<br>**0**: 定期的に署名を確認しません。<br>**1**:&1; 時間ごとにシグネチャを確認します。<br>**2**: 2 時間ごとなどに確認します。<br>**24**: 毎日確認します。<br>**既定値:** 8: 8 時間ごとに確認します。|
|**AllowCloudProtection**<br>./Vendor/MSFT/Policy/Config/Defender/AllowCloudProtection|デスクトップのみ<br />**データ型:** 整数<br />**値:** **0**: 許可しません。**1**: 許可します (既定)。|
|**SubmitSamplesConsent**<br>./Vendor/MSFT/Policy/Config/Defender/SubmitSamplesConsent|デスクトップのみ<br />**データ型:** 整数<br />**値:**<br>**0**: 常に確認のメッセージを表示します (既定)。<br>**1** : 安全なサンプルを自動的に送信します。<br>**2** : 送信することはありません。<br>**3** : すべてのサンプルを自動的に送信します。|
|**ExcludedExtensions**<br>./Vendor/MSFT/Policy/Config/Defender/ExcludedExtensions|デスクトップのみ<br />**データ型:** 文字列<br />**値:**<br>*&lt;セミコロンで区切られた拡張子の一覧&gt;* 例:  **obj; lib**<br>**既定値:** 拡張子は除外されません。|
|**ExcludedPaths**<br>./Vendor/MSFT/Policy/Config/Defender/ExcludedPaths|デスクトップのみ<br />**データ型:** 文字列<br />**値:**<br />*&lt;セミコロンで区切られたパスの一覧&gt;*<br />例: **c:\test;c:\test1.exe**<br />**既定値:** 除外されるパスはありません。|
|**ExcludedProcesses**<br>./Vendor/MSFT/Policy/Config/Defender/ExcludedProcesses|デスクトップのみ<br />**データ型:** 文字列<br />**値:**<br>*&lt;セミコロンで区切られたパスの一覧&gt;*<br>例: **c:\test.exe;c:\test1.exe**<br>**既定値:** 除外されるプロセスはありません。|

## <a name="edge-browser-settings"></a>Edge ブラウザーの設定

|ポリシー名と URI|説明|
|---------------|------------|-----------|
|**ブラウズを許可する**<br>./Vendor/MSFT/Policy/Config/Browser/AllowBrowser|モバイルのみ<br />**データ型:** 整数<br />**値:** **0**: 参照しません。**1**: 参照します (既定)。|
|**AllowSearchSuggestionsinAddressBar**<br>./Vendor/MSFT/Policy/Config/Browser/AllowSearchSuggestionsinAddressBar|デスクトップおよびモバイル<br />**データ型:** 整数<br />**値:** **0**: 候補を表示しません。**1** : 候補を表示します (既定)。|
|**SendIntranetTraffictoInternetExplorer**<br>./Vendor/MSFT/Policy/Config/Browser/SendIntranetTraffictoInternetExplorer|デスクトップのみ<br />**データ型:** 整数<br />**値:**<br>**0**: 無効 (Edge ブラウザーでイントラネット サイトを開きます) (既定)。<br>**1**: 有効 (Internet Explorer でイントラネット サイトを開きます)。|
|**追跡禁止を許可する**<br>./Vendor/MSFT/Policy/Config/Browser/AllowDoNotTrack|デスクトップおよびモバイル)<br />**データ型:** 整数<br />**値:** **0**: 無効 (DNT を送信しない: 既定)。**1**: 有効 (DNT を送信)。|
|**SmartScreen を構成する**<br>./Vendor/MSFT/Policy/Config/Browser/AllowSmartScreen|デスクトップおよびモバイル<br />**データ型:** 整数<br />**値:** **0**: 許可しません。**1**: 許可します (既定)。|
|**ポップアップを許可する**<br>./Vendor/MSFT/Policy/Config/Browser/AllowPopups|デスクトップのみ<br />**データ型:** 整数<br />**値:** **0**: ポップアップをブロックします (既定)。**1**: ポップアップを許可します。|
|**Cookie を使用する**<br>./Vendor/MSFT/Policy/Config/Browser/AllowCookies|デスクトップおよびモバイル<br />**データ型:** 整数<br />**値:**<br>**0**: すべての Web サイトの Cookie を許可します (既定)。<br>**1**: サード パーティの Cookie のみブロックします。<br>**2**: すべての Cookie をブロックします。|
|**パスワードの保存を許可する**<br>./Vendor/MSFT/Policy/Config/Browser/AllowPasswordManager|デスクトップおよびモバイル<br />**データ型:** 整数<br />**値:**<br>**0**: Password Manager を無効にします。 <br>**1**: Password Manager を有効にします (既定)。|
|**オートコンプリートを使用する**<br>./Vendor/MSFT/Policy/Config/Browser/AllowAutofill|デスクトップのみ<br />**データ型:** 整数<br />**値:** **0** : 無効 (既定)。**1** :有効。|
|**エンタープライズ サイトのリストを構成する**<br>./Vendor/MSFT/Policy/Config/Browser/EnterpriseModeSiteList|デスクトップのみ<br />**データ型:** 文字列<br />**値:<br>**0**: 構成されていません。<br>**1**: IE のエンタープライズ モード サイト リストが構成されている場合は使用します (既定)。<br>**2** : エンタープライズ サイト リストの場所を指定します。|

