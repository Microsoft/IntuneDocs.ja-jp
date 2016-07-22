---
title: "VPN プロファイルのカスタムの構成 |Microsoft Intune"
description: 
keywords: 
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4c0bd439-3b58-420b-9a9a-282886986786
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d5c48a4cead6250864f5b10444d99d062441bd99
ms.openlocfilehash: 7e7c50552b5a61804e759a7ec5443029d4bd4584


---

# VPN プロファイルのカスタム構成

## カスタム構成を作成する
Intune でカスタム構成を使用して VPN プロファイルを作成できます。 カスタム構成を使用するには:

   1. Intune 管理コンソールで、**[ポリシー]** -> **[ポリシーの追加]** -> *<Expand platform>* -> **[カスタム構成]** -> **[ポリシーの作成]** の順に選択します。
   2. ポリシーの名前を指定します。
   3. 各 URI 設定で、**[追加]** をクリックし、必要な情報を指定します。 次に例を示します。

   ![VPN プロファイルのカスタム構成ダイアログ ボックス](./media/Intune_Add_VPN_URI.png)

   4.  すべての URI 設定を入力したら、**[ポリシーの保存]** をクリックした後、ポリシーを展開します。

## 構成ポリシーを展開する

1.   **[ポリシー]** ワークスペースで、展開するポリシーを選択し、 **[展開の管理]**をクリックします。

2.   **[展開の管理]** ダイアログ ボックスで、次の操作を実行します。

    -   **ポリシーを展開するには**、ポリシーを展開する対象となる 1 つ以上のグループを選択して、**[追加]** &gt; **[OK]** をクリックします。

    -   **ポリシーを展開せずにダイアログ ボックスを閉じるには**、**[キャンセル]** をクリックします。

展開済みポリシーを選択すると、ポリシー一覧の下部に展開についての詳細が表示されます。

##カスタム VPN プロファイル構成の URI 設定の例
Contoso という架空の会社で VPN のカスタム構成を作成するための URI 値のエントリの例を次に示します。 各エントリのデータ型などの詳細については、「[VPNv2 CSP](https://msdn.microsoft.com/en-us/library/windows/hardware/dn914776.aspx)」を参照してください。

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

これらの設定の使用方法についてのご質問または設定がどのように機能するかの詳細については、次のCSP のドキュメントを参照してください。https://msdn.microsoft.com/en-us/library/windows/hardware/dn914776(v=vs.85).aspx

## PulseSecure での Android のアプリごとの VPN 用の URI 設定
### パッケージ リスト用の カスタム URI 
-  データ型 = 文字列
-  OMA-URI = ./Vendor/MSFT/VPN/Profile/<Name>/PackageList 
-  値 = 区切り記号で区切られたパッケージ リスト
   - 区切り記号: セミコロン (;)、コロン (:)、コンマ (,)、パイプ (|)

例: 
- com.android.chrome
- com.android.chrome;com.android.browser

### モード用のカスタム URI (省略可能)
- データ型 = 文字列
- OMA-URI = ./Vendor/MSFT/VPN/Profile/NAME/Mode 

> 注
> - カスタム プロファイルに割り当てた*名前*を使用します
> - 指定可能な値: *GLOBAL*、*WHITELIST*、*BLACKLIST*
> - PackageList が指定されていない場合の既定値は *GLOBAL* です (システム全体のプロファイルと下位互換)
> - PackageList が指定されている場合の既定値は *WHITELIST* です


### 関連項目
(Microsoft Intune での VPN 接続)[vpn-connections-in-microsoft-intune.md]



<!--HONumber=Jun16_HO4-->


