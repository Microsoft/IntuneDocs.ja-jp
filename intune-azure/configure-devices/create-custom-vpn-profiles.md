---
title: "Microsoft Intune でカスタム VPN プロファイルを作成する方法"
titleSuffix: Intune Azure preview
description: "Intune でカスタム構成を使用して VPN プロファイルを作成します。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4c0bd439-3b58-420b-9a9a-282886986786
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 132844bb1d1119390b7f55cca58cecbd5b8ee90a
ms.lasthandoff: 02/18/2017


---

# <a name="how-to-create-custom-vpn-profiles-in-microsoft-intune"></a>Microsoft Intune でカスタム VPN プロファイルを作成する方法

## <a name="create-a-custom-configuration"></a>カスタム構成を作成する
Intune のカスタム構成ポリシーを使用して、以下の VPN プロファイルを作成できます。

* Android 4 以降が実行されているデバイス
* Windows 8.1 以降を実行する登録済みのデバイス
* Windows Phone 8.1 以降が実行されているデバイス
* Windows 10 デスクトップを実行する登録済みのデバイス 
* Windows 10 Mobile を実行するデバイス

この種のポリシーは、標準的な Intune VPN ポリシーに、使用する設定が含まれていない場合に役立ちます。

## <a name="to-create-a-custom-configuration-policy"></a>カスタム構成ポリシーを作成するには:

1. Azure ポータルにサインインします。
2. **[その他のサービス]** > **[その他]** > **[Intune]** の順に選択します。
3. **[Intune]** ブレードで、**[デバイスの構成]** を選択します。
4. **[デバイス構成]** ブレードで、**[管理]** > **[プロファイル]** の順に選択します。
5. [プロファイル] ブレードで、**[プロファイルを作成します]** を選択します。
6. **[プロファイルを作成します]** ブレードで、VPN プロファイルの**名前**と**説明**を入力します。
7. **[プラットフォーム]** ドロップダウン リストで、VPN 設定を適用するデバイス プラットフォームを選択します。 現時点では、カスタム デバイス設定に対応している次のいずれかのプラットフォームを選択できます。
    - **Android**
    - **iOS** (Apple Configurator からエクスポートしたファイルを使用して構成済み)。
    - **macOS** (Apple Configurator からエクスポートしたファイルを使用して構成済み)。
    - **Windows Phone 8.1**
    - **Windows 10 以降**
6. **[プロファイルの種類]** ドロップダウン リストで、**[カスタム]** を選択します。
7. **[OMA-URI のカスタム設定]** ブレードで、指定する URI 設定ごとに **[追加]** を選択し、必要な情報を入力して、**[OK]** を選択します。 次に例を示します。

   ![VPN プロファイルのカスタム構成ダイアログ ボックス](./media/Intune_Add_VPN_URI.png)

4.  必要な URI 設定をすべて入力したら **[OK]** を選択し、**[プロファイルを作成します]** ブレードで **[作成]** を選択します。

プロファイルが作成され、プロファイルの一覧ブレードに表示されます。
このプロファイルをグループに割り当てる場合は、[デバイス プロファイルを割り当てる方法](how-to-assign-device-profiles.md)に関する記事を参照してください。

## <a name="example-uri-settings"></a>URI 設定の例

これらの設定は、Contoso という架空の会社で VPN のカスタム構成を作成する場合に使用できます。
使用できるすべての設定の詳細については、「[VPNv2 CSP](https://msdn.microsoft.com/en-us/library/windows/hardware/dn914776.aspx)」を参照してください。

Contoso のネイティブ VPN (IKEv2): ./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Servers

vpn.contoso.com ./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/NativeProtocolType

Ikev2 ./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/RoutingPolicyType

SplitTunnel ./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Authentication/UserMethod

Eap ./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Authentication/Eap/Configuration &lt;EapHostConfig xmlns="http://www.microsoft.com/provisioning/EapHostConfig"&gt;&lt;EapMethod&gt;&lt;Type xmlns="http://www.microsoft.com/provisioning/EapCommon"&gt;13&lt;/Type&gt;&lt;VendorId xmlns="http://www.microsoft.com/provisioning/EapCommon"&gt;0&lt;/VendorId&gt;&lt;VendorType xmlns="http://www.microsoft.com/provisioning/EapCommon"&gt;0&lt;/VendorType&gt;&lt;AuthorId xmlns="http://www.microsoft.com/provisioning/EapCommon"&gt;0&lt;/AuthorId&gt;&lt;/EapMethod&gt;&lt;Config xmlns="http://www.microsoft.com/provisioning/EapHostConfig"&gt;&lt;Eap xmlns="http://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1"&gt;&lt;Type&gt;13&lt;/Type&gt;&lt;EapType xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV1"&gt;&lt;CredentialsSource&gt;&lt;CertificateStore&gt;&lt;SimpleCertSelection&gt;true&lt;/SimpleCertSelection&gt;&lt;/CertificateStore&gt;&lt;/CredentialsSource&gt;&lt;ServerValidation&gt;&lt;DisableUserPromptForServerValidation&gt;false&lt;/DisableUserPromptForServerValidation&gt;&lt;ServerNames&gt;&lt;/ServerNames&gt;&lt;/ServerValidation&gt;&lt;DifferentUsername&gt;false&lt;/DifferentUsername&gt;&lt;PerformServerValidation xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2"&gt;false&lt;/PerformServerValidation&gt;&lt;AcceptServerName xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2"&gt;false&lt;/AcceptServerName&gt;&lt;/EapType&gt;&lt;/Eap&gt;&lt;/Config&gt;&lt;/EapHostConfig&gt;

**./Vendor/MSFT/VPNv2/ContosoVPN/ByPassForLocal** True

**./Vendor/MSFT/VPNv2/ContosoVPN/RememberCredentials** 1

**./Vendor/MSFT/VPNv2/ContosoVPN/DomainNameInformationList/1/DomainName** Corp.Contoso.com

**./Vendor/MSFT/VPNv2/ContosoVPN/DnsSuffix** Corp.Contoso.com

**./Vendor/MSFT/VPNv2/ContosoVPN/TrustedNetworkDetection** Corp.Contoso.com

**./Vendor/MSFT/VPNv2/ContosoVPN/RouteList/1/Address** 10.0.0.0

**./Vendor/MSFT/VPNv2/ContosoVPN/RouteList/1/PrefixSize** 8

**./Vendor/MSFT/VPNv2/ContosoVPN/AlwaysOn** true

**./Vendor/MSFT/VPNv2/ContosoVPN/AppTriggerList/0/App/Id** %PROGRAMFILES%\Internet Explorer\iexplore.exe

**./Vendor/MSFT/VPNv2/ContosoVPN/AppTriggerList/1/App/Id** %PROGRAMFILES% (x86)\Internet Explorer\iexplore.exe

**./Vendor/MSFT/VPNv2/ContosoVPN/AppTriggerList/2/App/Id** Microsoft.MicrosoftEdge_8wekyb3d8bbwe

**./Vendor/MSFT/VPNv2/ContosoVPN/TrafficFilterList/0/App/Id** %PROGRAMFILES% (x86)\Internet Explorer\iexplore.exe

**./Vendor/MSFT/VPNv2/ContosoVPN/TrafficFilterList/1/App/Id** Microsoft.MicrosoftEdge_8wekyb3d8bbwe

これらの設定の使用方法についてのご質問または設定がどのように機能するかの詳細については、次の構成サービス プロバイダー (CSP) のドキュメントを参照してください。https://msdn.microsoft.com/en-us/library/windows/hardware/dn914776(v=vs.85).aspx

## <a name="uri-settings-for-android-per-app-vpn-on-pulsesecure"></a>PulseSecure での Android のアプリごとの VPN 用の URI 設定
### <a name="custom-uri-for-package-list"></a>パッケージ リスト用のカスタム URI
-  データ型 = 文字列
-  OMA-URI = ./Vendor/MSFT/VPN/Profile/Name/PackageList
-  値 = 区切り記号で区切られたパッケージ リスト
   - 区切り記号: セミコロン (;)、コロン (:)、コンマ (,)、パイプ (|)

例:
- com.android.chrome
- com.android.chrome;com.android.browser

### <a name="custom-uri-for-mode-optional"></a>モード用のカスタム URI (省略可能)
- データ型 = 文字列
- OMA-URI = ./Vendor/MSFT/VPN/Profile/NAME/Mode

> 注
> - カスタム プロファイルに割り当てた*名前*を使用します
> - 指定可能な値: *GLOBAL*、*WHITELIST*、*BLACKLIST*
> - PackageList が指定されていない場合の既定値は *GLOBAL* です (システム全体のプロファイルと下位互換)
> - PackageList が指定されている場合の既定値は *WHITELIST* です




