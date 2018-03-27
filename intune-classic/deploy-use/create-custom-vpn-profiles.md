---
title: Microsoft Intune VPN プロファイルのカスタム構成
description: Intune でカスタム構成を使用して VPN プロファイルを作成します。
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 12/15/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4c0bd439-3b58-420b-9a9a-282886986786
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 6139b656c69b58bdbdd02e296f8a061dd598a1c6
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2018
---
# <a name="custom-configurations-for-microsoft-intune-vpn-profiles"></a>Microsoft Intune VPN プロファイルのカスタム構成

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

## <a name="create-a-custom-configuration"></a>カスタム構成を作成する
Intune のカスタム構成ポリシーを使用して、以下の VPN プロファイルを作成できます。

* Android 4 以降が実行されているデバイス
* Android for Work デバイス
* Windows 8.1 以降を実行する登録済みのデバイス
* Windows Phone 8.1 以降が実行されているデバイス
* Windows 10 デスクトップを実行する登録済みのデバイス
* Windows 10 Mobile を実行するデバイス

この種のポリシーは、標準的な Intune VPN ポリシーに、使用する設定が含まれていない場合に役立ちます。

## <a name="to-create-a-custom-configuration-policy"></a>カスタム構成ポリシーを作成するには:

   1. [Intune 管理コンソール](https://manage.microsoft.com)で、**[ポリシー]** > **[ポリシーの追加]** > *<プラットフォームを展開>* > **[カスタム構成]** > **[ポリシーの作成]** の順に選択します。
   2. ポリシーの名前を入力します。
   3. 指定する必要がある URI の設定ごとに、**[追加]** を選択し、必要な情報を指定します。 次に例を示します。

   ![VPN プロファイルのカスタム構成ダイアログ ボックス](./media/Intune_Add_VPN_URI.png)

   4.  すべての URI 設定を入力したら、**[ポリシーの保存]** を選択した後、ポリシーを展開します。

その後、通常どおり[ポリシーを展開](/intune-classic/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies#deploy-a-configuration-policy)します。

## <a name="example-uri-settings"></a>URI 設定の例

これらの設定は、Contoso という架空の会社で VPN のカスタム構成を作成する場合に使用できます。
使用できるすべての設定の詳細については、「[VPNv2 CSP](https://msdn.microsoft.com/library/windows/hardware/dn914776.aspx)」を参照してください。

**Contoso のネイティブ VPN (IKEv2):**<br />
./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Servers

**vpn.contoso.com**<br />
./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/NativeProtocolType

**Ikev2<br />** ./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/RoutingPolicyType

**SplitTunnel**<br />
./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Authentication/UserMethod

**Eap**<br />
./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Authentication/Eap/Configuration
``` xml
<EapHostConfig xmlns="http://www.microsoft.com/provisioning/EapHostConfig">
   <EapMethod>
      <Type xmlns="http://www.microsoft.com/provisioning/EapCommon">13</Type>
      <VendorId xmlns="http://www.microsoft.com/provisioning/EapCommon">0</VendorId>
      <VendorType xmlns="http://www.microsoft.com/provisioning/EapCommon">0</VendorType>
      <AuthorId xmlns="http://www.microsoft.com/provisioning/EapCommon">0</AuthorId>
   </EapMethod>
   <Config xmlns="http://www.microsoft.com/provisioning/EapHostConfig">
      <Eap xmlns="http://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1">
         <Type>13</Type>
         <EapType xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV1">
            <CredentialsSource>
               <CertificateStore>
                  <SimpleCertSelection>true</SimpleCertSelection>
               </CertificateStore>
            </CredentialsSource>
            <ServerValidation>
               <DisableUserPromptForServerValidation>false</DisableUserPromptForServerValidation>
               <ServerNames></ServerNames>
            </ServerValidation>
            <DifferentUsername>false</DifferentUsername>
            <PerformServerValidation xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">
               false
            </PerformServerValidation>
            <AcceptServerName xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">
               false
            </AcceptServerName>
         </EapType>
      </Eap>
   </Config>
</EapHostConfig>
```
**./Vendor/MSFT/VPNv2/ContosoVPN/ByPassForLocal**<br />
True

**./Vendor/MSFT/VPNv2/ContosoVPN/RememberCredentials**<br />
1

**./Vendor/MSFT/VPNv2/ContosoVPN/DomainNameInformationList/1/DomainName**<br />
Corp.Contoso.com

**./Vendor/MSFT/VPNv2/ContosoVPN/DnsSuffix**<br />
Corp.Contoso.com

**./Vendor/MSFT/VPNv2/ContosoVPN/TrustedNetworkDetection**<br />
Corp.Contoso.com

**./Vendor/MSFT/VPNv2/ContosoVPN/RouteList/1/Address**<br />
10.0.0.0

**./Vendor/MSFT/VPNv2/ContosoVPN/RouteList/1/PrefixSize**<br />
8

**./Vendor/MSFT/VPNv2/ContosoVPN/AlwaysOn**<br />
true

**./Vendor/MSFT/VPNv2/ContosoVPN/AppTriggerList/0/App/Id**<br />
%PROGRAMFILES%\Internet Explorer\iexplore.exe

**./Vendor/MSFT/VPNv2/ContosoVPN/AppTriggerList/1/App/Id**<br />
%PROGRAMFILES% (x86)\Internet Explorer\iexplore.exe

**./Vendor/MSFT/VPNv2/ContosoVPN/AppTriggerList/2/App/Id**<br />
Microsoft.MicrosoftEdge_8wekyb3d8bbwe

**./Vendor/MSFT/VPNv2/ContosoVPN/TrafficFilterList/0/App/Id**<br />
%PROGRAMFILES% (x86)\Internet Explorer\iexplore.exe

**./Vendor/MSFT/VPNv2/ContosoVPN/TrafficFilterList/1/App/Id**<br />
Microsoft.MicrosoftEdge_8wekyb3d8bbwe

これらの設定の使用方法に関するご質問、またはこれらの設定により行われることの詳細については、[構成サービス プロバイダー (CSP) に関するドキュメント](https://msdn.microsoft.com/library/windows/hardware/dn914776(v=vs.85).aspx)を参照してください。

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


### <a name="see-also"></a>関連項目
[Microsoft Intune での VPN 接続](vpn-connections-in-microsoft-intune.md)
