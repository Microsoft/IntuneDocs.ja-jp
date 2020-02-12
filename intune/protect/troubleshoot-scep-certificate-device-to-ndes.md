---
title: Microsoft Intune でマネージド デバイスから NDES への通信をトラブルシューティングする | Microsoft Docs
description: Intune で SCEP 証明書プロファイルを使用して証明書を展開するときのマネージド デバイスから NDES サーバーへの通信をトラブルシューティングします。
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
ms.openlocfilehash: 8c81fa9b521b0d950fb69c29f7625981e709863d
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2020
ms.locfileid: "76916111"
---
# <a name="troubleshoot-device-to-ndes-server-communication-for-scep-certificate-profiles-in-microsoft-intune"></a>Microsoft Intune で SCEP 証明書プロファイルのためのデバイスから NDES サーバーへの通信をトラブルシューティングする

次の情報を使用して、Intune の Simple Certificate Enrollment Protocol (SCEP) 証明書プロファイルを受信して処理するデバイスが、ネットワーク デバイス登録サービスに正常に接続してチャレンジを提示できるかどうかを判断します。 デバイス上では秘密キーが生成され、証明書署名要求 (CSR) とチャレンジがデバイスから NDES サーバーに渡されます。 デバイスでは、NDES サーバーに接続するために、SCEP 証明書プロファイルから取得した URI が使用されます。

この記事では、[SCEP 通信フローの概要](troubleshoot-scep-certificate-profiles.md)に関する記事の手順 2 が参照されます。

## <a name="review-iis-logs-for-a-connection-from-the-device"></a>IIS ログでデバイスからの接続を確認する

IIS ログには、すべてのプラットフォームに対して同じ種類のエントリが含まれています。


1. NDES サーバー上で、次のフォルダーにある最新の IIS ログ ファイルを開きます:   *%SystemDrive%\inetpub\logs\logfiles\w3svc1*

2. ログで次の例のようなエントリを探します。 どちらの例にも状態 **200** が含まれています (これは末尾の近くに表示されます)。

   `fe80::f53d:89b8:c3e8:5fec%13 GET /certsrv/mscep/mscep.dll/pkiclient.exe operation=GetCACaps&message=default 80 - fe80::f53d:89b8:c3e8:5fec%13 Mozilla/4.0+(compatible;+Win32;+NDES+client) - 200 0 0 186 0.`

   および

   `fe80::f53d:89b8:c3e8:5fec%13 GET /certsrv/mscep/mscep.dll/pkiclient.exe operation=GetCACert&message=default 80 - fe80::f53d:89b8:c3e8:5fec%13 Mozilla/4.0+(compatible;+Win32;+NDES+client) - 200 0 0 3567 0`

3. デバイスが IIS に接続すると、mscep.dll に対する HTTP GET 要求がログに記録されます。

   この要求の末尾近くにある状態コードを確認します。
   - **状態コード 200**:この状態は、NDES サーバーとの接続が成功したことを示します。
   - **状態コード 500**:IIS_IURS グループに適切なアクセス許可が付与されていない可能性があります。 この記事の後半の「[状態コード 500](#status-code-500)」を参照してください。
   - 状態コードが 200 でも 500 でもない場合:

     - この記事の後半の「[SCEP サーバーの URL をテストする](#test-the-scep-server-url)」を参照して、構成を検証してください。

     - 「[IIS 7 以降のバージョンの HTTP 状態コード](https://support.microsoft.com/help/943891)」を参照して、一般的でないエラー コードの詳細を確認してください。

   接続要求がまったくログに記録されていない場合は、デバイスからの通信が、デバイスと NDES サーバー間のネットワークでブロックされている可能性があります。

## <a name="review-device-logs-for-connections-to-ndes"></a>デバイスのログで NDES への接続を確認する

### <a name="android-devices"></a>Android デバイス

[デバイスの OMADM ログ](troubleshoot-scep-certificate-profiles.md#logs-for-android-devices)を確認します。 次のようなエントリを探します。これは、デバイスが NDES に接続したときにログに記録されます。

```
2018-02-27T05:16:08.2500000  VERB  Event  com.microsoft.omadm.platforms.android.certmgr.CertificateEnrollmentManager  18327    10  There are 1 requests
2018-02-27T05:16:08.2500000  VERB  Event  com.microsoft.omadm.platforms.android.certmgr.CertificateEnrollmentManager  18327    10  Trying to enroll certificate request: ModelName=AC_51bad41f-3854-4eb5-a2f2-0f7a94034ee8%2FLogicalName_39907e78_e61b_4730_b9fa_d44a53e4111c;Hash=1677525787
2018-02-27T05:16:09.5530000  VERB  Event  org.jscep.transport.UrlConnectionGetTransport  18327    10  Sending GetCACaps(ca) to https://<server>.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=ca
2018-02-27T05:16:14.6440000  VERB  Event  org.jscep.transport.UrlConnectionGetTransport  18327    10  Received '200 OK' when sending GetCACaps(ca) to https://<server>.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=ca
2018-02-27T05:16:21.8220000  VERB  Event  org.jscep.message.PkiMessageEncoder  18327     10 Encoding message: org.jscep.message.PkcsReq@2b06f45f[messageData=org.<server>.pkcs.PKCS10CertificationRequest@699b3cd,messageType=PKCS_REQ,senderNonce=Nonce [D447AE9955E624A56A09D64E2B3AE76E],transId=251E592A777C82996C7CF96F3AAADCF996FC31FF]
2018-02-27T05:16:21.8790000  VERB  Event  org.jscep.message.PkiMessageEncoder  18327     10  Signing pkiMessage using key belonging to [dn=CN=<uesrname>; serial=1]
2018-02-27T05:16:21.9580000  VERB  Event  org.jscep.transaction.EnrollmentTransaction  18327     10  Sending org.<server>.cms.CMSSignedData@ad57775
```

キー エントリには、次のサンプル テキスト文字列が含まれています。

- There are 1 requests
- Received '200 OK' when sending GetCACaps(ca) to https://\<サーバー>.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=ca
- Signing pkiMessage using key belonging to [dn=CN=\<ユーザー名>; serial=1]


接続のログは IIS でも記録されます。これは NDES サーバーの %SystemDrive%\inetpub\logs\LogFiles\W3SVC1\ フォルダーにあります。 次に例を示します。

```
fe80::f53d:89b8:c3e8:5fec%13 GET /certsrv/mscep/mscep.dll operation=GetCACert&message=ca 443 - 
fe80::f53d:89b8:c3e8:5fec%13 Dalvik/2.1.0+(Linux;+U;+Android+5.0;+P01M+Build/LRX21V) - 200 0 0 3909 0
fe80::f53d:89b8:c3e8:5fec%13 GET /certsrv/mscep/mscep.dll operation=GetCACaps&message=ca 443 - 
fe80::f53d:89b8:c3e8:5fec%13 Dalvik/2.1.0+(Linux;+U;+Android+5.0;+P01M+Build/LRX21V) - 200 0 0 421 
```

### <a name="ios-and-ipados-devices"></a>iOS および iPadOS デバイス

[デバイスのデバッグ ログ](troubleshoot-scep-certificate-profiles.md#logs-for-ios-and-ipados-devices)を確認します。 次のようなエントリを探します。これは、デバイスが NDES に接続したときにログに記録されます。

```
debug    18:30:53.691033 -0500    profiled    Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACert&message=SCEP%20Authority\ 
debug    18:30:54.640644 -0500    profiled    Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=SCEP%20Authority\ 
default    18:30:55.483977 -0500    profiled    Attempting to retrieve issued certificate...\ 
debug    18:30:55.487798 -0500    profiled    Sending CSR via GET.\  
debug    18:30:55.487908 -0500    profiled    Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=PKIOperation&message=MIAGCSqGSIb3DQEHAqCAMIACAQExDzANBglghkgBZQMEAgMFADCABgkqhkiG9w0BBwGggCSABIIZfzCABgkqhkiG9w0BBwOggDCAAgEAMYIBgjCCAX4CAQAwZjBPMRUwEwYKCZImiZPyLGQBGRYFbG9jYWwxHDAaBgoJkiaJk/IsZAEZFgxmb3VydGhjb2ZmZWUxGDAWBgNVBAMTD0ZvdXJ0aENvZmZlZSBDQQITaAAAAAmaneVjEPlcTwAAAAAACTANBgkqhkiG9w0BAQEFAASCAQCqfsOYpuBToerQLkw/tl4tH9E+97TBTjGQN9NCjSgb78fF6edY0pNDU+PH4RB356wv3rfZi5IiNrVu5Od4k6uK4w0582ZM2n8NJFRY7KWSNHsmTIWlo/Vcr4laAtq5rw+CygaYcefptcaamkjdLj07e/Uk4KsetGo7ztPVjSEFwfRIfKv474dLDmPqp0ZwEWRQGZwmPoqFMbX3g85CJT8khPaqFW05yGDTPSX9YpuEE0Bmtht9EwOpOZe6O7sd77IhfFZVmHmwy5mIYN7K6mpx/4Cb5zcNmY3wmTBlKEkDQpZDRf5PpVQ3bmQ3we9XxeK1S4UsAXHVdYGD+bg/bCafMIAGCSqGSIb3DQEHATAUBggqhkiG9w0DBwQI5D5J2lwZS5OggASCF6jSG9iZA/EJ93fEvZYLV0v7GVo3JAsR11O7DlmkIqvkAg5iC6DQvXO1j88T/MS3wV+rqUbEhktr8Xyf4sAAPI4M6HMfVENCJTStJw1PzaGwUJHEasq39793nw4k268UV5XHXvzZoF3Os2OxUHSfHECOj
```

キー エントリには、次のサンプル テキスト文字列が含まれています。

- operation=GetCACert
- Attempting to retrieve issued certificate
- Sending CSR via GET
- operation=PKIOperation

### <a name="windows-devices"></a>Windows デバイス

NDES に接続する Windows デバイスでは、デバイスの Windows イベント ビューアーを表示して、接続の成功を示す記録を探すことができます。 接続は、イベント ID **36** として、デバイスの *[DeviceManagement-Enterprise-Diagnostics-Provide]* > **[Admin]** ログに記録されます。

ログを開くには、次の操作を行います。

1. デバイス上で **eventvwr.msc** を実行し、Windows イベント ビューアーを開きます。

2. **[アプリケーションとサービス ログ]** > **[Microsoft]** > **[Windows]** > **[DeviceManagement-Enterprise-Diagnostic-Provider]** > **[Admin]** を展開します。

3. 次の例のようなイベント **36** を探します。これには次のキー行が含まれます: **SCEP:Certificate request generated successfully**。

   ```
   Event ID:      36
   Task Category: None
   Level:         Information
   Keywords:
   User:          <UserSid>
   Computer:      <Computer Name>
   Description:
   SCEP: Certificate request generated successfully. Enhanced Key Usage: (1.3.6.1.5.5.7.3.2), NDES URL: (https://<server>/certsrv/mscep/mscep.dll/pkiclient.exe), Container Name: (), KSP Setting: (0x2), Store Location: (0x1).
   ```

## <a name="troubleshoot-common-errors"></a>一般的なエラーのトラブルシューティング

次のセクションでは、すべてのデバイス プラットフォームから NDES への接続に関する一般的な問題について説明します。

### <a name="status-code-500"></a>状態コード 500

次の例のような接続 (状態コード 500) は、NDES サーバー上で IIS_IURS グループに "*認証後にクライアントを偽装*" ユーザー権利が割り当てられていないことを示しています。 状態の値 **500** は末尾に表示されます。

```
2017-08-08 20:22:16 IP_address GET /certsrv/mscep/mscep.dll operation=GetCACert&message=SCEP%20Authority 443 - 10.5.14.22 profiled/1.0+CFNetwork/811.5.4+Darwin/16.6.0 - 500 0 1346 31
```

**この問題を解決するには**:

1. NDES サーバー上で **secpol.msc** を実行し、ローカル セキュリティ ポリシーを開きます。

2. **[ローカル ポリシー]** を展開し、**[ユーザー権利の割り当て]** をクリックします。

3. 右側のペインの **[認証後にクライアントを偽装]** をダブルクリックします。

4. **[ユーザーまたはグループの追加...]** をクリックし、**[選択するオブジェクト名を入力してください]** に「**IIS_IURS**」と入力した後、**[OK]** をクリックします。

5. [ **OK**] をクリックします。

6. コンピューターを再起動した後、デバイスからの接続を再試行します。

### <a name="test-the-scep-server-url"></a>SCEP サーバーの URL をテストする

次の手順にしたがって、SCEP 証明書プロファイルで指定されている URL をテストします。

1. Intune で、SCEP 証明書プロファイルを編集し、サーバーの URL をコピーします。 URL は *https://contoso.com/certsrv/mscep/msecp.dll* に似ています。

2. Web ブラウザーを開き、その SCEP サーバーの URL に移動します。 結果は次のようになるはずです:**HTTP エラー 403.0 – Forbidden**。 この結果は、URL が正常に機能していることを示しています。

   このエラーが表示されない場合は、表示されたエラーに似ているリンクを次から選択して、問題に固有のガイダンスを参照してください。
   - [ネットワーク デバイス登録サービスの一般的なメッセージが表示される](#general-ndes-message)
   - ["HTTP エラー503。サービスを利用できません" と表示される](#http-error-503)
   - ["GatewayTimeout" エラーが表示される](#gatewaytimeout)
   - ["HTTP 414 要求 URI が長すぎます" と表示される](#http-414-request-uri-too-long)
   - ["このページは表示できません" と表示される](#this-page-cant-be-displayed)
   - ["500 - 内部サーバー エラー" と表示される](#internal-server-error)

#### <a name="general-ndes-message"></a>一般的な NDES メッセージ

SCEP サーバーの URL に移動すると、次のネットワーク デバイス登録サービスのメッセージが表示されます。

![SCEP サーバーの URL](../protect/media/troubleshoot-scep-certificate-device-to-ndes/ndes-server-url-message.png)

- **原因**:この問題が発生する場合は、通常、Microsoft Intune コネクタのインストールに問題があります。

  これが正しくインストールされている場合、ISAPI 拡張機能である mscep.dll によって受信要求がインターセプトされ、HTTP 403 エラーが表示されます。
  
  **解決方法**:*SetupMsi.log* ファイルを調べて、Microsoft Intune コネクタが正常にインストールされているかどうかを確認します。 次の例では、*Installation completed successfully* と *Installation success or error status:0* がインストールの成功を示しています。

  ```
  MSI (c) (28:54) [16:13:11:905]: Product: Microsoft Intune Connector -- Installation completed successfully.
  MSI (c) (28:54) [16:13:11:999]: Windows Installer installed the product. Product Name: Microsoft Intune Connector. Product Version: 6.1711.4.0. Product Language: 1033. Manufacturer: Microsoft Corporation. Installation success or error status: 0.
  ```

  インストールが失敗した場合は、Microsoft Intune コネクタを削除してから再インストールしてください。

#### <a name="http-error-503"></a>HTTP エラー 503

SCEP サーバーの URL に移動すると、次のエラーが表示されます。

![HTTP エラー 503。 サービスを利用できません](../protect/media/troubleshoot-scep-certificate-device-to-ndes/service-unavailable.png)

この問題は、通常、IIS で **SCEP** アプリケーション プールが開始されていないことが原因で発生します。 NDES サーバー上で **IIS マネージャー**を開き、**[アプリケーション プール]** に移動します。 **SCEP** アプリケーション プールを見つけて、それが開始されていることを確認します。

SCEP アプリケーション プールが開始されていない場合は、サーバーのアプリケーション イベント ログを確認します。

1. デバイス上で **eventvwr.msc** を実行して**イベント ビューアー**を開き、**[Windows ログ]** > **[アプリケーション]** に移動します。

2. 次の例のようなイベントを探します。これは、要求の受信時にアプリケーション プールがクラッシュしたことを意味しています。

   ```
   Log Name:      Application
   Source:        Application Error
   Event ID:      1000
   Task Category: Application Crashing Events
   Level:         Error
   Keywords:      Classic
   Description: Faulting application name: w3wp.exe, version: 8.5.9600.16384, time stamp: 0x5215df96
   Faulting module name: ntdll.dll, version: 6.3.9600.18821, time stamp: 0x59ba86db
   Exception code: 0xc0000005
   ```

**アプリケーション プールのクラッシュの一般的な原因**:

- **原因 1**:NDES サーバーの [信頼されたルート証明機関] 証明書ストアに、(自己署名でない) 中間 CA 証明書があります。

  **解決方法**:[信頼されたルート証明機関] 証明書ストアから中間証明書を削除し、NDES サーバーを再起動します。
  
  [信頼されたルート証明機関] 証明書ストア内のすべての中間証明書を特定するには、次の PowerShell コマンドレットを実行します: `Get-Childitem -Path cert:\LocalMachine\root -Recurse | Where-Object {$_.Issuer -ne $_.Subject}`

  **[発行先]** と **[発行元]** の値が同じである証明書は、ルート証明書です。 そうでない場合は、中間証明書です。

  証明書を削除してサーバーを再起動した後、PowerShell コマンドレットをもう一度実行して、中間証明書がないことを確認します。 存在した場合は、グループ ポリシーによって NDES サーバーに中間証明書がプッシュされているかどうかを確認します。 その場合は、NDES サーバーをグループ ポリシーから除外し、中間証明書をもう一度削除します。

- **原因 2**:証明書失効リスト (CRL) 内の URL がブロックされているか、Intune Certificate Connector で使用される証明書からアクセスできません。

  **解決方法**:詳細情報を収集するために、追加のログ記録を有効にします。
  1. イベント ビューアーを開き、**[表示]** をクリックして、**[分析およびデバッグ ログの表示]** オプションがオンになっていることを確認します。
  2. **[アプリケーションとサービス ログ]** > **[Microsoft]** > **[Windows]** > **[CAPI2]** > **[稼働中]** に移動し、**[稼働中]** を右クリックして、**[ログを有効にする]** をクリックします。
  3. CAPI2 ログ記録を有効にした後、問題を再現し、イベント ログを調べて問題のトラブルシューティングを行います。

- **原因 3**:**CertificateRegistrationSvc** に対する IIS のアクセス許可で、**[Windows 認証]** が有効になっています。

  **解決方法**:**[匿名認証]** を有効にし、**[Windows 認証]** を無効にしてから、NDES サーバーを再起動します。

  ![IIS のアクセス許可](../protect/media/troubleshoot-scep-certificate-device-to-ndes/iis-permissions.png)

#### <a name="gatewaytimeout"></a>GatewayTimeout

SCEP サーバーの URL に移動すると、次のエラーが表示されます。

![Gatewaytimeout エラー](../protect/media/troubleshoot-scep-certificate-device-to-ndes/gateway-timeout.png)

- **原因**:**Microsoft AAD Application Proxy Connector** サービスが開始されていません。

  **解決方法**:**services.msc** を実行し、**Microsoft AAD Application Proxy Connector** サービスが実行されていることと、**[スタートアップの種類]** が **[自動]** に設定されていることを確認します。

#### <a name="http-414-request-uri-too-long"></a>HTTP 414 要求 URI が長すぎます

SCEP サーバーの URL に移動すると、次のエラーが表示されます: `HTTP 414 Request-URI Too Long`

- **原因**:NDES サービスが受信する長い URL (クエリ) をサポートするように IIS の要求フィルター処理が構成されていません。 このサポートは、SCEP のインフラストラクチャで使用するために [NDES サービスを構成する](certificates-scep-configure.md#configure-the-ndes-service)ときに構成します。

- **解決方法**:長い URL のサポートを構成します。

  1. NDES サーバー上で、IIS マネージャーを開き、**[既定の Web サイト]** > **[要求のフィルタリング]** > **[機能設定の編集]** の順に選択して、**[要求フィルター設定の編集]** ページを開きます。

  2. 次の設定を構成します。
     - **URL の最大長 (バイト)** = 65534
     - **クエリ文字列の最大長 (バイト)** = 65534

  3. **[OK]** を選択してこの構成を保存し、IIS マネージャーを閉じます。

  4. 次のレジストリ キーを見つけて、指定された値があることを確認することで、この構成を検証します。

     HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\HTTP\Parameters

     次の値がダブルワード エントリとして設定されていることを確認します。
     - 名前:**MaxFieldLength**、十進数 **65534**
     - 名前:**MaxRequestBytes**、十進数 **65534**

  5. NDES サーバーを再起動します。

#### <a name="this-page-cant-be-displayed"></a>このページは表示できません

Azure AD アプリケーション プロキシを構成しました。 SCEP サーバーの URL に移動すると、次のエラーが表示されます。

`This page can't be displayed`

- **原因**:この問題は、アプリケーション プロキシ構成の SCEP の外部 URL が正しくない場合に発生します。 この URL の例は、https://contoso.com/certsrv/mscep/mscep.dll などです。

  **解決方法**:アプリケーション プロキシ構成で、SCEP の外部 URL に対して規定のドメイン *yourtenant.msappproxy.net* を使用します。

#### <a name="internal-server-error"></a>500 - 内部サーバー エラー

SCEP サーバーの URL に移動すると、次のエラーが表示されます。

![500 - 内部サーバー エラー](../protect/media/troubleshoot-scep-certificate-device-to-ndes/500-internal-server-error.png)

- **原因 1**:NDES サービス アカウントがロックされているか、そのパスワードの有効期限が切れています。

  **解決方法**:アカウントのロックを解除するか、パスワードをリセットします。

- **原因 2**:MSCEP-RA 証明書の有効期限が切れています。

  **解決方法**:MSCEP-RA 証明書の有効期限が切れている場合は、NDES の役割を再インストールするか、新しい CEP 暗号化証明書および Exchange 登録エージェント (オフライン要求) 証明書を要求します。

  新しい証明書を要求するには、次の手順を実行します。

  1. 証明機関 (CA) または発行元 CA で、証明書テンプレート MMC を開きます。 ログインしているユーザーと NDES サーバーが、CEP 暗号化証明書および Exchange 登録エージェント (オフライン要求) 証明書のテンプレートに対する **[読み取り]** および **[登録]** アクセス許可を持っていることを確認します。

  2. NDES サーバー上で期限切れの証明書を確認し、その証明書の **[サブジェクト]** 情報をコピーします。

  3. **[コンピューター アカウント]** の証明書 MMC を開きます。

  4. **[個人]** を展開し、**[証明書]** を右クリックして、**[すべてのタスク]** > **[新しい証明書の要求]** を選択します。

  5. **[証明書の要求]** ページで、**[CEP 暗号化]** を選択して、**[この証明書を登録するには情報が不足しています。設定を構成するには、ここをクリックしてください]** をクリックします。

     ![CEP 暗号化を選択する](../protect/media/troubleshoot-scep-certificate-device-to-ndes/select-scep-encryption.png)

  6. **[証明書のプロパティ]** で、**[サブジェクト]** タブをクリックし、手順 2 で収集した情報を **[サブジェクト名]** に入力して **[追加]** をクリックした後、**[OK]** をクリックします。

  7. 証明書の登録を完了します。

  8. **[ユーザー アカウント]** の証明書 MMC を開きます。

     Exchange 登録エージェント (オフライン要求) 証明書の登録は、ユーザー コンテキストで実行する必要があります。 この証明書テンプレートの **[サブジェクトの種類]** は **[ユーザー]** に設定されているためです。

  9. **[個人]** を展開し、**[証明書]** を右クリックして、**[すべてのタスク]** > **[新しい証明書の要求]** を選択します。

  10. **[証明書の要求]** ページで、**[Exchange 登録エージェント (オフライン要求)]** を選択して、次をクリックします: **この証明書を登録するには情報が不足しています。** 設定を構成するにはここをクリックします。

      ![Exchange 登録エージェントを選択する](../protect/media/troubleshoot-scep-certificate-device-to-ndes/select-exchange-enrollment-agent.png)

  11. **[証明書のプロパティ]** で、**[サブジェクト]** タブをクリックし、手順 2 で収集した情報を **[サブジェクト名]** に入力して、**[追加]** をクリックします。

      ![証明書のプロパティ](../protect/media/troubleshoot-scep-certificate-device-to-ndes/certificate-properties.png)

      **[秘密キー]** タブを選択し、**[秘密キーをエクスポート可能にする]** を選択して、**[OK]** をクリックします。

      ![秘密キー](../protect/media/troubleshoot-scep-certificate-device-to-ndes/private-key.png)

  12. 証明書の登録を完了します。

  13. 現在のユーザー証明書ストアから、Exchange 登録エージェント (オフライン要求) 証明書をエクスポートします。 [証明書のエクスポート ウィザード] で、**[はい、秘密キーをエクスポートします]** を選択します。

  14. 証明書をローカル コンピューターの証明書ストアにインポートします。

  15. 証明書 MMC で、新しい証明書ごとに次の操作を行います。

      証明書を右クリックし、**[すべてのタスク]** > **[秘密キーの管理]** をクリックして、NDES サービス アカウントに **[読み取り]** アクセス許可を追加します。

  16. **iisreset** コマンドを実行して IIS を再起動します。

## <a name="next-steps"></a>次のステップ

デバイスが NDES サーバーに正常にアクセスし、証明書の要求を提示できたら、次の手順として [Intune Certificate Connectors のポリシー モジュール](troubleshoot-scep-certificate-ndes-policy-module.md)に関する記事を確認してください。
