---
title: "PSK を使用する Wi-Fi"
description: "カスタム構成を使用して、事前共有キーを使用した Wi-Fi プロファイルを作成します。"
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 10/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e977c7c7-e204-47a6-b851-7ad7673ceaab
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 1f9fe19e251788185b5f06bc7d9851041a02e2b2
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/10/2017
---
# <a name="use-a-custom-policy-to-create-a-wi-fi-profile-with-a-pre-shared-key"></a>カスタム ポリシーを使用して、事前共有キーを使用した Wi-Fi プロファイルを作成する

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune の**カスタム構成**を使用して、事前共有キーを使用した Wi-Fi プロファイルを作成する方法を次に示します。 このトピックでは、EAP ベースの Wi-Fi プロファイルを作成する方法の例も示します。

> [!NOTE]
-   以下のように、そのネットワークに接続しているコンピューターからコードをコピーした方が簡単な場合があります。
- Android では、Johnathon Biersack 氏が提供しているこの [Android PSK Generator](http://johnathonb.com/2015/05/intune-android-pre-shared-key-generator/) を使用することも可能です。
-   OMA-URI 設定をさらに追加することにより、複数のネットワークとキーを追加できます。
-  iOS でプロファイルを構成するには、Mac ステーションで Apple Configurator を使用します。 また、Johnathon Biersack 氏が提供する [iOS PSK Mobile Config Generator](http://johnathonb.com/2015/05/intune-ios-psk-mobile-config-generator/) を使用します。


1.  Android または Windows 用に事前共有キーを使用した Wi-Fi プロファイル、または EAP ベースの Wi-Fi プロファイルを作成する場合、ポリシーを作成するときに、Wi-Fi プロファイルではなく、そのデバイスのプラットフォーム用の**カスタム構成**を選択します。

2.  名前と説明を入力します。
3.  新しい OMA-URI 設定を追加します。

   a.   この Wi-Fi ネットワーク設定の名前を入力します。

   b.   OMA-URI 設定の説明を入力するか、空白のままにします。

   c.   **データ型**: "String(XML)" に設定

   d.   **OMA-URI**:

    - **Android の場合**: ./Vendor/MSFT/WiFi/Profile/<SSID>/Settings
    - **Windows の場合**: ./Vendor/MSFT/WiFi/Profile/MyNetwork/WlanXml

    > [!NOTE]
先頭にピリオドを必ず入力してください。

    SSID は、作成しているポリシーの SSID です。 たとえば、`./Vendor/MSFT/WiFi/Profile/Hotspot-1/Settings` と記述します。

  e. **値フィールド**に、XML コードを貼り付けます。 次に例を示します。 それぞれの値は、ネットワーク設定に適したものにする必要があります。 一部のポインターのコードについては、コメント セクションをご覧ください。
4. **[OK]** を選択して、保存し、ポリシーをデプロイします。

    > [!NOTE]
    > このポリシーは、ユーザー グループにのみデプロイできます。

次回各デバイスがチェックインするときに、ポリシーは適用され、そのデバイスに Wi-Fi プロファイルが作成されます。 デバイスは自動的にネットワークに接続できるようになります。
## <a name="android-or-windows-wi-fi-profile"></a>Android または Windows の Wi-Fi プロファイル

次に、Android または Windows の Wi-Fi プロファイルの XML コードの例を示します。

> [!IMPORTANT]
> 
> `<protected>false</protected>` を **false** に設定する必要があります。**true** に設定すると、デバイスはパスワードが暗号化されていると見なし、暗号化の解除を試みます。その結果、接続が失敗する場合があります。
> 
>  `<hex>53534944</hex>` は、`<name><SSID of wifi profile></name>` の 16 進値に設定する必要があります。
>  Windows 10 デバイスは、"*0x87D1FDE8 修復できませんでした*" という間違ったエラーを返す場合があります。それでも、これまでどおり、プロファイルでプロビジョニングすることができます。

```
<!--
<Name of wifi profile> = Name of profile
<SSID of wifi profile> = Plain text of SSID. Does not need to be escaped, could be <name>Your Company's Network</name>
<nonBroadcast><true/false></nonBroadcast>
<Type of authentication> = Type of authentication used by the network, such as WPA2PSK.
<Type of encryption> = Type of encryption used by the network
<protected>false</protected> do not change this value, as true could cause device to expect an encrypted password and then try to decrypt it, which may result in a failed connection.
<password> = Password to connect to the network
<hex>53534944</hex> should be set to the hexadecimal value of <name><SSID of wifi profile></name>
-->
<WLANProfile
xmlns="http://www.microsoft.com/networking/WLAN/profile/v1">
  <name><Name of wifi profile></name>
  <SSIDConfig>
    <SSID>
      <hex>53534944</hex>
 <name><SSID of wifi profile></name>        </SSID>
        <nonBroadcast>false</nonBroadcast>
      </SSIDConfig>
      <connectionType>ESS</connectionType>
      <connectionMode>auto</connectionMode>
      <autoSwitch>false</autoSwitch>
      <MSM>
        <security>
          <authEncryption>
            <authentication><Type of authentication></authentication>
            <encryption><Type of encryption></encryption>
            <useOneX>false</useOneX>
          </authEncryption>
          <sharedKey>
            <keyType>networkKey</keyType>
            <protected>false</protected>
            <keyMaterial>MyPassword</keyMaterial>
          </sharedKey>
          <keyIndex>0</keyIndex>
        </security>
      </MSM>
    </WLANProfile>
```

## <a name="eap-based-wi-fi-profile"></a>EAP ベースの Wi-Fi プロファイル
次に、EAP ベースの Wi-Fi プロファイルの XML コードの例を示します。

```
    <WLANProfile xmlns="http://www.microsoft.com/networking/WLAN/profile/v1">
      <name>testcert</name>
      <SSIDConfig>
        <SSID>
          <hex>7465737463657274</hex>
          <name>testcert</name>
        </SSID>
        <nonBroadcast>true</nonBroadcast>
      </SSIDConfig>
      <connectionType>ESS</connectionType>
      <connectionMode>auto</connectionMode>
      <autoSwitch>false</autoSwitch>
      <MSM>
        <security>
          <authEncryption>
            <authentication>WPA2</authentication>
            <encryption>AES</encryption>
            <useOneX>true</useOneX>
            <FIPSMode     xmlns="http://www.microsoft.com/networking/WLAN/profile/v2">false</FIPSMode>
          </authEncryption>
          <PMKCacheMode>disabled</PMKCacheMode>
          <OneX xmlns="http://www.microsoft.com/networking/OneX/v1">
            <cacheUserData>false</cacheUserData>
            <authMode>user</authMode>
            <EAPConfig>
              <EapHostConfig     xmlns="http://www.microsoft.com/provisioning/EapHostConfig">
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
                      <PerformServerValidation xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">false</PerformServerValidation>
                      <AcceptServerName xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">false</AcceptServerName>
                      <TLSExtensions xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">
                        <FilteringInfo xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV3">
                          <AllPurposeEnabled>true</AllPurposeEnabled>
                          <CAHashList Enabled="true">
                            <IssuerHash>75 f5 06 9c a4 12 0e 9b db bc a1 d9 9d d0 f0 75 fa 3b b8 78 </IssuerHash>
                          </CAHashList>
                          <EKUMapping>
                            <EKUMap>
                              <EKUName>Client Authentication</EKUName>
                              <EKUOID>1.3.6.1.5.5.7.3.2</EKUOID>
                            </EKUMap>
                          </EKUMapping>
                          <ClientAuthEKUList Enabled="true"/>
                          <AnyPurposeEKUList Enabled="false">
                            <EKUMapInList>
                              <EKUName>Client Authentication</EKUName>
                            </EKUMapInList>
                          </AnyPurposeEKUList>
                        </FilteringInfo>
                      </TLSExtensions>
                    </EapType>
                  </Eap>
                </Config>
              </EapHostConfig>
            </EAPConfig>
          </OneX>
        </security>
      </MSM>
    </WLANProfile>
```

## <a name="create-the-xml-file-from-an-existing-wi-fi-connection"></a>既存の Wi-Fi 接続からの XML ファイルの作成
次のように、既存の Wi-Fi 接続から XML ファイルを作成することもできます。
1. ワイヤレス ネットワークに接続中のコンピューターまたは最近接続されたコンピューターの、C:\ProgramData\Microsoft\Wlansvc\Profiles\Interfaces\{guid} のフォルダーを開きます。

    すべての中から正しいプロファイルを探す必要があるため、多数のワイヤレス ネットワークに接続したことのないコンピューターを使用するのが最良です。
3.     XML ファイルを検索し、正しい名前のファイルを探します。
4.     正しい XML ファイルを見つけたら、OMA-URI の設定ページの [データ] フィールドに、XML コードをコピーして貼り付けます。

## <a name="deploy-the-policy"></a>ポリシーの展開

1.  **[ポリシー]** ワークスペースで、展開するポリシーを選び、**[展開の管理]** を選びます。

2.  **[展開の管理]** ダイアログ ボックスで、次の操作を実行します。

    -   **ポリシーを展開するには** - ポリシーを展開する対象となる 1 つ以上のグループを選択して、**[追加]** &gt; **[OK]** の順に選択します。

    -   **ポリシーを展開せずにダイアログ ボックスを閉じるには**、**[キャンセル]** を選択します。

デプロイ済みポリシーを選択すると、ポリシー一覧の下部にデプロイについての詳細が表示されます。

### <a name="see-also"></a>関連項目
[Microsoft Intune での Wi-Fi 接続](wi-fi-connections-in-microsoft-intune.md)
