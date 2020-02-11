---
title: Microsoft Intune で SCEP を使用する場合に証明書をデバイスに配信する際のトラブルシューティング | Microsoft Docs
description: Intune で SCEP 証明書プロファイルを使用して証明書を展開する場合に CA からデバイスへ証明書を配信する際のトラブルシューティングを行います。
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
ms.openlocfilehash: 77be59d126dc7e73bee468ca938938c6bb1b2e1a
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2020
ms.locfileid: "76915877"
---
# <a name="troubleshoot-the-delivery-of-certificates-provisioned-by-scep-to-devices-in-microsoft-intune"></a>Microsoft Intune で SCEP によってプロビジョニングされた証明書をデバイスに配信する際のトラブルシューティング

この記事の情報は、Simple Certificate Enrollment Protocol (SCEP) を使用して Intune で証明書をプロビジョニングするときに、デバイスへの証明書の配信を調査するために役立ちます。 ネットワーク デバイス登録サービス (NDES) サーバーでは、証明機関 (CA) からデバイスに対して要求された証明書を受信すると、その証明書がデバイスに渡されます。

この記事は、[SCEP 通信ワークフロー](troubleshoot-scep-certificate-profiles.md)の手順 5 (証明書要求を送信したデバイスへの証明書の配信) に適用されます。

## <a name="review-the-certification-authority"></a>証明機関を確認する

CA から証明書が発行されると、CA で次の例のようなエントリを確認できます。

![発行された証明書の例](../protect/media/troubleshoot-scep-certificate-delivery/certificate-authority.png)

## <a name="review-the-device"></a>デバイスを確認する

### <a name="android"></a>Android

デバイス管理者がデバイスを登録した場合、次の画像のように、証明書をインストールするように求める通知が表示されます。

![Android の通知](../protect/media/troubleshoot-scep-certificate-delivery/android-notification.png)

Android Enterprise または Samsung Knox の場合、証明書のインストールは、自動的に、サイレントで行われます。

Android にインストールされている証明書を表示するには、サード パーティ製の証明書表示アプリを使用します。

また、[デバイスの OMADM ログ](troubleshoot-scep-certificate-profiles.md#logs-for-android-devices)を確認することもできます。 証明書のインストール時にログに記録される次のようなエントリを探します。

**ルート証明書**:

```
2018-02-27T04:50:52.1890000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeRootCertInstallStateMachine     9595        9    Root cert '17…' state changed from CERT_INSTALL_REQUESTED to CERT_INSTALL_REQUESTED
2018-02-27T04:53:31.1300000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeRootCertInstallStateMachine     9595        0    Root cert '17…' state changed from CERT_INSTALL_REQUESTED to CERT_INSTALLING
2018-02-27T04:53:32.0390000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeRootCertInstallStateMachine     9595       14    Root cert '17…' state changed from CERT_INSTALLING to CERT_INSTALL_SUCCESS
```

**SCEP を介してプロビジョニングされた証明書**

```
2018-02-27T05:16:08.2500000    VERB    Event     com.microsoft.omadm.platforms.android.certmgr.CertificateEnrollmentManager    18327       10    There are 1 requests
2018-02-27T05:16:08.2500000    VERB    Event     com.microsoft.omadm.platforms.android.certmgr.CertificateEnrollmentManager    18327       10    Trying to enroll certificate request: ModelName=AC_51…%2FLogicalName_39907…;Hash=1677525787
2018-02-27T05:16:20.6150000    VERB    Event     org.jscep.transport.UrlConnectionGetTransport    18327       10    Sending GetCACert(ca) to https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACert&message=ca
2018-02-27T05:16:20.6530000    VERB    Event     org.jscep.transport.UrlConnectionGetTransport    18327       10    Received '200 OK' when sending GetCACert(ca) to https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACert&message=ca
2018-02-27T05:16:21.7460000    VERB    Event     org.jscep.transport.UrlConnectionGetTransport    18327       10    Sending GetCACaps(ca) to https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=ca
2018-02-27T05:16:21.7890000    VERB    Event     org.jscep.transport.UrlConnectionGetTransport    18327       10    Received '200 OK' when sending GetCACaps(ca) to https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=ca
2018-02-27T05:16:28.0340000    VERB    Event     org.jscep.transaction.EnrollmentTransaction    18327       10    Response: org.jscep.message.CertRep@3150777b[failInfo=<null>,pkiStatus=SUCCESS,recipientNonce=Nonce [GUID],messageData=org.spongycastle.cms.CMSSignedData@27cc8998,messageType=CERT_REP,senderNonce=Nonce [GUID],transId=TRANSID]
2018-02-27T05:16:28.2440000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeScepCertInstallStateMachine    18327       10    SCEP cert 'ModelName=AC_51…%2FLogicalName_39907…;Hash=1677525787' state changed from CERT_ENROLLED to CERT_INSTALL_REQUESTED
2018-02-27T05:18:44.9820000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeScepCertInstallStateMachine    18327        0    SCEP cert 'ModelName=AC_51…%2FLogicalName_39907…;Hash=1677525787' state changed from CERT_INSTALL_REQUESTED to CERT_INSTALLING
2018-02-27T05:18:45.3460000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeScepCertInstallStateMachine    18327       14    SCEP cert 'ModelName=AC_51…%2FLogicalName_39907…;Hash=1677525787' state changed from CERT_INSTALLING to CERT_ACCESS_REQUESTED
2018-02-27T05:20:15.3520000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeScepCertInstallStateMachine    18327       21    SCEP cert 'ModelName=AC_51…%2FLogicalName_39907…;Hash=1677525787' state changed from CERT_ACCESS_REQUESTED to CERT_ACCESS_GRANTED
```

### <a name="ios-and-ipados"></a>iOS と iPadOS

iOS または iPadOS デバイスでは、[Device Management Profile]\(デバイス管理プロファイル\) の下に証明書が表示されます。 展開すると、インストールされている証明書の詳細が表示されます。

![iOS 証明書](../protect/media/troubleshoot-scep-certificate-delivery/ios-certificate.png)

[iOS デバッグ ログ](troubleshoot-scep-certificate-profiles.md#logs-for-ios-and-ipados-devices)では、次のようなエントリを見つけることもできます。

```
Debug 18:30:53.691033 -0500 profiled Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACert&message=SCEP%20Authority\  
Debug 18:30:54.640644 -0500 profiled Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=SCEP%20Authority\ 
Debug 18:30:55.487908 -0500 profiled Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=PKIOperation&message=MIAGCSqGSIb3DQEHAqCAMIACAQExDzANBglghkgBZQMEAgMFADCABgkqhkiG9w0BBwGggCSABIIZfzCABgkqhkiG9w0BBwOggDCAAgEAMYIBgjCCAX4CAQAwZjBPMRUwEwYKCZImiZPyLGQBGRYFbG9jYWwxHDAaBgoJkiaJk/IsZAEZFgxmb3VydGhjb2ZmZWUxGDAWBgNVBAMTD0ZvdXJ0aENvZmZlZSBDQQITaAAAAAmaneVjEPlcTwAAAAAACTANBgkqhkiG9w0BAQEFAASCAQCqfsOYpuBToerQLkw/tl4tH9E+97TBTjGQN9NCjSgb78fF6edY0pNDU+PH4RB356wv3rfZi5IiNrVu5Od4k6uK4w0582ZM2n8NJFRY7KWSNHsmTIWlo/Vcr4laAtq5rw+CygaYcefptcaamkjdLj07e/Uk4KsetGo7ztPVjSEFwfRIfKv474dLDmPqp0ZwEWRQG 
Debug 18:30:57.285730 -0500 profiled Adding dependent Microsoft.Profiles.MDM to parent www.windowsintune.com.SCEP.ModelName=AC_51bad41f.../LogicalName_1892fe4c...;Hash=-912418295 in domain ManagedProfileToManagingProfile to system\ 
Default 18:30:57.320616 -0500 profiled Profile \'93www.windowsintune.com.SCEP.ModelName=AC_51bad41f.../LogicalName_1892fe4c...;Hash=-912418295\'94 installed.\ 
```

### <a name="windows"></a>Windows

Windows デバイスで、証明書が配信されたことを確認します。

- **eventvwr.msc** を実行してイベント ビューアーを開きます。 **[アプリケーションとサービス ログ]**  >  **[Microsoft]**  >  **[Windows]**  >  **[DeviceManagement-Enterprise-Diagnostic-Provider]**  >  **[Admin]** に移動し、**イベント 39** を探します。 このイベントには、次のような一般的な説明があります。**SCEP:Certificate installed successfully.** (SCEP: 証明書が正常にインストールされました。)

   ![Windows アプリケーション ログのイベント 39](../protect/media/troubleshoot-scep-certificate-delivery/device-app-log.png)

デバイスの証明書を表示するには、**certmgr.msc** を実行して証明書 MMC を開き、デバイス上の個人用ストアにルート証明書と SCEP 証明書が正しくインストールされていることを確認します。

   1. **[証明書 (ローカル コンピューター)]**  >  **[信頼されたルート証明機関]**  >  **[証明書]** に移動し、CA からのルート証明書が存在することを確認します。 *[発行先]* と *[発行元]* の値は同じになります。
   2. 証明書 MMC で、 **[証明書 - 現在のユーザー]**  >  **[個人]**  >  **[証明書]** に移動し、要求された証明書が存在し、 *[発行元]* が CA の名前と同じであることを確認します。

## <a name="troubleshoot-failures"></a>エラーのトラブルシューティング

### <a name="android"></a>Android

この手順のトラブルシューティングには、OMA DM ログに記録されているエラーを確認します。

### <a name="ios-and-ipados"></a>iOS と iPadOS

この手順のトラブルシューティングには、デバイスのデバッグ ログに記録されているエラーを確認します。

### <a name="windows"></a>Windows

デバイスに証明書がインストールされていない問題をトラブルシューティングするには、Windows イベント ログで問題を示すエラーを探します。

- デバイス上で **eventvwr.msc** を実行してイベント ビューアーを開き、 **[アプリケーションとサービス ログ]**  >  **[Microsoft]**  >  **[Windows]**  >  **[DeviceManagement-Enterprise-Diagnostic-Provider]**  >  **[Admin]** に移動します。

証明書をデバイスに配信してインストールする際のエラーは、通常、Intune ではなく、Windows の操作に関連しています。

## <a name="next-steps"></a>次のステップ

証明書がデバイスに正常に展開されても、Intune で成功と報告されない場合は、[NDES から Intune へ報告](troubleshoot-scep-certificate-reporting.md)に関する記事を参照して、レポートのトラブルシューティングを行ってください。
