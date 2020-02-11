---
title: Microsoft Intune を使用したデバイスへの SCEP 証明書プロファイルの展開に関するトラブルシューティング | Microsoft Docs
description: Intune を使用してデバイスに SCEP 証明書プロファイルを送信する際のトラブルシューティングを行います。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/30/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3dae74321b6825a1b94551addfd7621450fd8ae4
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2020
ms.locfileid: "76916046"
---
# <a name="troubleshoot-deployment-of-a-scep-certificate-profile-to-devices-in-microsoft-intune"></a>Microsoft Intune でのデバイスへの SCEP 証明書プロファイルの展開に関するトラブルシューティング

次の情報を使用して、Intune を使用した Simple Certificate Enrollment Protocol (SCEP) 証明書プロファイルの展開に関するトラブルシューティングを行うことができます。

この記事では、[SCEP 通信フローの概要](troubleshoot-scep-certificate-profiles.md)に関する記事の手順 1 が参照されます。


## <a name="android"></a>Android

Android の SCEP 証明書プロファイルは SyncML としてデバイスに送信され、[OMADM log](troubleshoot-scep-certificate-profiles.md#logs-for-android-devices) に記録されます。

### <a name="validate-that-the-android-device-was-sent-the-policy"></a>Android デバイスがポリシーに送信されたことを検証する

プロファイルが目的のデバイスに送信されたことを確認するには、[Microsoft Endpoint Manager admin center](https://go.microsoft.com/fwlink/?linkid=2109431) で **[トラブルシューティング + サポート]**  >  **[トラブルシューティング]** に移動します。  *[トラブルシューティング]* ウィンドウで、 **[割り当て]** を **[構成プロファイル]** に設定し、次の構成を検証します。

1. SCEP 証明書プロファイルを受信する [ユーザー] を指定します。

2. ユーザーの [グループ メンバーシップ] を見て、SCEP 証明書プロファイルで使用したセキュリティ グループに属していることを確認します。

3. Intune でデバイスが最後にチェックインされた日時を確認します。

![ポリシーを検証する](../protect/media/troubleshoot-scep-certificate-profile-deployment/validate-policy-android.png)

### <a name="validate-the-policy-reached-the-android-device"></a>ポリシーが Android デバイスに到達したことを検証する

[デバイスの OMADM ログ](troubleshoot-scep-certificate-profiles.md#logs-for-android-devices)を確認します。 次のようなエントリを探します。これらは、デバイスで Intune からプロファイルを取得されたときにログに記録されます。

```
Time    VERB    Event     com.microsoft.omadm.syncml.SyncmlSession     9595        9    <?xml version="1.0" encoding="utf-8"?><SyncML xmlns="SYNCML:SYNCML1.2"><SyncHdr><VerDTD>1.2</VerDTD><VerProto>DM/1.2</VerProto><SessionID>1</SessionID><MsgID>6</MsgID><Target><LocURI>urn:uuid:UUID</LocURI></Target><Source><LocURI>https://a.manage.microsoft.com/devicegatewayproxy/AndroidHandler.ashx</LocURI></Source><Meta><MaxMsgSize xmlns="syncml:metinf">524288</MaxMsgSize></Meta></SyncHdr><SyncBody><Status><CmdID>1</CmdID><MsgRef>6</MsgRef><CmdRef>0</CmdRef><Cmd>SyncHdr</Cmd><Data>200</Data></Status><Replace><CmdID>2</CmdID><Item><Target><LocURI>./Vendor/MSFT/Scheduler/IntervalDurationSeconds</LocURI></Target><Meta><Format xmlns="syncml:metinf">int</Format><Type xmlns="syncml:metinf">text/plain</Type></Meta><Data>28800</Data></Item></Replace><Replace><CmdID>3</CmdID><Item><Target><LocURI>./Vendor/MSFT/EnterpriseAppManagement/EnterpriseIDs</LocURI></Target><Data>contoso.onmicrosoft.com</Data></Item></Replace><Exec><CmdID>4</CmdID><Item><Target><LocURI>./Vendor/MSFT/EnterpriseAppManagement/EnterpriseApps/ClearNotifications</LocURI></Target></Item></Exec><Add><CmdID>5</CmdID><Item><Target><LocURI>./Vendor/MSFT/CertificateStore/Root/{GUID}/EncodedCertificate</LocURI></Target><Data>Data</Data></Item></Add><Add><CmdID>6</CmdID><Item><Target><LocURI>./Vendor/MSFT/CertificateStore/Enroll/ModelName=AC_51…%2FLogicalName_39907…%3BHash=-1518303401/Install</LocURI></Target><Meta><Format xmlns="syncml:metinf">xml</Format><Type xmlns="syncml:metinf">text/plain</Type></Meta><Data>&lt;CertificateRequest&gt;&lt;ConfigurationParametersDocument&gt;&amp;lt;ConfigurationParameters xmlns="http://schemas.microsoft.com/SystemCenterConfigurationManager/2012/03/07/CertificateEnrollment/ConfigurationParameters"&amp;gt;&amp;lt;ExpirationThreshold&amp;gt;20&amp;lt;/ExpirationThreshold&amp;gt;&amp;lt;RetryCount&amp;gt;3&amp;lt;/RetryCount&amp;gt;&amp;lt;RetryDelay&amp;gt;1&amp;lt;/RetryDelay&amp;gt;&amp;lt;TemplateName /&amp;gt;&amp;lt;SubjectNameFormat&amp;gt;{ID}&amp;lt;/SubjectNameFormat&amp;gt;&amp;lt;SubjectAlternativeNameFormat&amp;gt;{ID}&amp;lt;/SubjectAlternativeNameFormat&amp;gt;&amp;lt;KeyStorageProviderSetting&amp;gt;0&amp;lt;/KeyStorageProviderSetting&amp;gt;&amp;lt;KeyUsage&amp;gt;32&amp;lt;/KeyUsage&amp;gt;&amp;lt;KeyLength&amp;gt;2048&amp;lt;/KeyLength&amp;gt;&amp;lt;HashAlgorithms&amp;gt;&amp;lt;HashAlgorithm&amp;gt;SHA-1&amp;lt;/HashAlgorithm&amp;gt;&amp;lt;HashAlgorithm&amp;gt;SHA-2&amp;lt;/HashAlgorithm&amp;gt;&amp;lt;/HashAlgorithms&amp;gt;&amp;lt;NDESUrls&amp;gt;&amp;lt;NDESUrl&amp;gt;https://breezeappproxy-contoso.msappproxy.net/certsrv/mscep/mscep.dll&amp;lt;/NDESUrl&amp;gt;&amp;lt;/NDESUrls&amp;gt;&amp;lt;CAThumbprint&amp;gt;{GUID}&amp;lt;/CAThumbprint&amp;gt;&amp;lt;ValidityPeriod&amp;gt;2&amp;lt;/ValidityPeriod&amp;gt;&amp;lt;ValidityPeriodUnit&amp;gt;Years&amp;lt;/ValidityPeriodUnit&amp;gt;&amp;lt;EKUMapping&amp;gt;&amp;lt;EKUMap&amp;gt;&amp;lt;EKUName&amp;gt;Client Authentication&amp;lt;/EKUName&amp;gt;&amp;lt;EKUOID&amp;gt;1.3.6.1.5.5.7.3.2&amp;lt;/EKUOID&amp;gt;&amp;lt;/EKUMap&amp;gt;&amp;lt;/EKUMapping&amp;gt;&amp;lt;/ConfigurationParameters&amp;gt;&lt;/ConfigurationParametersDocument&gt;&lt;RequestParameters&gt;&lt;CertificateRequestToken&gt;PENlcnRFbn... Hash: 1,010,143,298&lt;/CertificateRequestToken&gt;&lt;SubjectName&gt;CN=name&lt;/SubjectName&gt;&lt;Issuers&gt;CN=FourthCoffee CA; DC=fourthcoffee; DC=local&lt;/Issuers&gt;&lt;SubjectAlternativeName&gt;&lt;SANs&gt;&lt;SAN NameFormat="ID" AltNameType="2" OID="{OID}"&gt;&lt;/SAN&gt;&lt;SAN NameFormat="ID" AltNameType="11" OID="{OID}"&gt;john@contoso.onmicrosoft.com&lt;/SAN&gt;&lt;/SANs&gt;&lt;/SubjectAlternativeName&gt;&lt;NDESUrl&gt;https://breezeappproxy-contoso.msappproxy.net/certsrv/mscep/mscep.dll&lt;/NDESUrl&gt;&lt;/RequestParameters&gt;&lt;/CertificateRequest&gt;</Data></Item></Add><Get><CmdID>7</CmdID><Item><Target><LocURI>./Vendor/MSFT/CertificateStore/SCEP</LocURI></Target></Item></Get><Add><CmdID>8</CmdID><Item><Target><LocURI>./Vendor/MSFT/GCM</LocURI></Target><Data>Data</Data></Item></Add><Replace><CmdID>9</CmdID><Item><Target><LocURI>./Vendor/MSFT/GCM</LocURI></Target><Data>Data</Data></Item></Replace><Get><CmdID>10</CmdID><Item><Target><LocURI>./Vendor/MSFT/NodeCache/SCConfigMgr</LocURI></Target></Item></Get><Get><CmdID>11</CmdID><Item><Target><LocURI>./Vendor/MSFT/NodeCache/SCConfigMgr/CacheVersion</LocURI></Target></Item></Get><Get><CmdID>12</CmdID><Item><Target><LocURI>./Vendor/MSFT/NodeCache/SCConfigMgr/ChangedNodes</LocURI></Target></Item></Get><Get><CmdID>13</CmdID><Item><Target><LocURI>./DevDetail/Ext/Microsoft/LocalTime</LocURI></Target></Item></Get><Get><CmdID>14</CmdID><Item><Target><LocURI>./Vendor/MSFT/DeviceLock/DevicePolicyManager/IsActivePasswordSufficient</LocURI></Target></Item></Get><Get><CmdID>15</CmdID><Item><Target><LocURI>./Vendor/MSFT/WorkProfileLock/DevicePolicyManager/IsActivePasswordSufficient</LocURI></Target></Item></Get><Final /></SyncBody></SyncML>
```

キー エントリの例:

- `ModelName=AC_51bad41f-3854-4eb5-a2f2-0f7a94034ee8%2FLogicalName_39907e78_e61b_4730_b9fa_d44a53e4111c%3BHash=-1518303401`
- `NDESUrls&amp;gt;&amp;lt;NDESUrl&amp;gt;https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll&amp;lt;/NDESUrl&amp;gt;&amp;lt;/NDESUrls`

## <a name="ios-and-ipados"></a>iOS と iPadOS

### <a name="validate-that-the-ios-or-ipados-device-was-sent-the-policy"></a>iOS または iPadOS デバイスがポリシーに送信されたことを検証する

プロファイルが目的のデバイスに送信されたことを確認するには、[Microsoft Endpoint Manager admin center](https://go.microsoft.com/fwlink/?linkid=2109431) で **[トラブルシューティング + サポート]**  >  **[トラブルシューティング]** に移動します。  *[トラブルシューティング]* ウィンドウで、 **[割り当て]** を **[構成プロファイル]** に設定し、次の構成を検証します。

1. SCEP 証明書プロファイルを受信する [ユーザー] を指定します。

2. ユーザーの [グループ メンバーシップ] を見て、SCEP 証明書プロファイルで使用したセキュリティ グループに属していることを確認します。

3. Intune でデバイスが最後にチェックインされた日時を確認します。

![ポリシーを検証する](../protect/media/troubleshoot-scep-certificate-profile-deployment/validate-policy-ios.png)

### <a name="validate-the-policy-reached-the-ios-or-ipados-device"></a>ポリシーが iOS または iPadOS デバイスに到達したことを検証する

[デバイスのデバッグ ログ](troubleshoot-scep-certificate-profiles.md#logs-for-ios-and-ipados-devices)を確認します。 次のようなエントリを探します。これらは、デバイスで Intune からプロファイルを取得されたときにログに記録されます。

```
debug    18:30:54.638009 -0500    profiled    Adding dependent ModelName=AC_51bad41f.../LogicalName_1892fe4c...;Hash=-912418295 to parent 636572740000000000000012 in domain PayloadDependencyDomainCertificate to system\
```

キー エントリの例:

- `ModelName=AC_51bad41f.../LogicalName_1892fe4c...;Hash=-912418295`
- `PayloadDependencyDomainCertificate`

## <a name="windows"></a>Windows

### <a name="validate-that-the-windows-device-was-sent-the-policy"></a>Windows デバイスにポリシーが送信されたことを検証する

プロファイルが目的のデバイスに送信されたことを確認するには、[Microsoft Endpoint Manager admin center](https://go.microsoft.com/fwlink/?linkid=2109431)[Microsoft Endpoint Manager admin center](https://go.microsoft.com/fwlink/?linkid=2109431) で、 **[トラブルシューティング + サポート]**  >  **[トラブルシューティング]** に移動します。  *[トラブルシューティング]* ウィンドウで、 **[割り当て]** を **[構成プロファイル]** に設定し、次の構成を検証します。

1. SCEP 証明書プロファイルを受信する [ユーザー] を指定します。

2. ユーザーの [グループ メンバーシップ] を見て、SCEP 証明書プロファイルで使用したセキュリティ グループに属していることを確認します。

3. Intune でデバイスが最後にチェックインされた日時を確認します。

![ポリシーを検証する](../protect/media/troubleshoot-scep-certificate-profile-deployment/validate-policy-windows.png)

### <a name="validate-the-policy-reached-the-windows-device"></a>ポリシーが Windows デバイスに到達したことを検証する

プロファイルのポリシーの到達は、Windows デバイスの *[DeviceManagement-Enterprise-Diagnostics-Provider]*  >  **[Admin]** ログにイベント ID **306** で記録されます。 

ログは次の方法で開きます。

1. デバイス上で **eventvwr.msc** を実行し、Windows イベント ビューアーを開きます。

2. **[アプリケーションとサービス ログ]**  >  **[Microsoft]**  >  **[Windows]**  >  **[DeviceManagement-Enterprise-Diagnostic-Provider]**  >  **[Admin]** を展開します。

3. 次の例のように、イベント **306** を探します。

   ```
   Event ID:      306
   Task Category: None
   Level:         Information
   User:          SYSTEM
   Computer:      <Computer Name>
   Description:
   SCEP: CspExecute for UniqueId : (ModelName_<ModelName>_LogicalName_<LogicalName>_Hash_<Hash>) InstallUserSid : (<UserSid>) InstallLocation : (user) NodePath : (clientinstall)  KeyProtection: (0x2) Result : (Unknown Win32 Error code: 0x2ab0003).
   ```

   エラー コード **0x2ab0003** は **DM_S_ACCEPTED_FOR_PROCESSING** に変換されます。

   失敗のエラー コードは、根底に問題があることを示している可能性があります。

## <a name="next-steps"></a>次のステップ

プロファイルがデバイスに到達した場合は、次の手順として、[デバイスから NDES サーバーへの通信](troubleshoot-scep-certificate-device-to-ndes.md)を確認します。
