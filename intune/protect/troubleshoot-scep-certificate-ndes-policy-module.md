---
title: Microsoft Intune Certificate Connector ポリシー モジュールのトラブルシューティング | Microsoft Docs
description: SCEP 証明書プロファイルを使用して Intune で証明書を展開する場合に、モジュールで証明書の要求を処理するときの NDES ポリシー モジュールの操作をトラブルシューティングします。
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
ms.openlocfilehash: be53f6102226b004cab2bd953357e8c360a00f67
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2020
ms.locfileid: "76915838"
---
# <a name="troubleshoot-the-ndes-policy-module-in-microsoft-intune"></a>Microsoft Intune の NDES ポリシー モジュールのトラブルシューティング

この記事の情報は、Microsoft Intune Certificate Connector と共にインストールされるネットワーク デバイス登録サービス (NDES) ポリシー モジュールの操作を検証するために役立ちます。 NDES では、証明書の要求を受信すると、要求がポリシー モジュールに転送されます。これにより、要求がデバイスに対して有効かどうかが検証されます。 検証が完了すると、NDES から証明機関 (CA) に接続され、デバイスの代わりに証明書が要求されます。

この記事は、[SCEP 通信ワークフロー](troubleshoot-scep-certificate-profiles.md)の手順 3 と手順 4 の両方に適用されます。

## <a name="ndes-communication-to-the-policy-module"></a>NDES からポリシー モジュールへの通信

デバイスから証明書要求を受信した後、NDES では、Microsoft Intune Certificate Connector と共にインストールされるポリシー モジュールを介して Intune を使用してその要求が検証されます。 これらのエントリは、*証明書登録ポイント*を示しています。

**成功を示すログ エントリ**:

検証要求がモジュールに送信されたことを確認するには、NDES サーバーのログで次の例のようなエントリを探します。

- **IIS ログ**:

  ```
  fe80::f53d:89b8:c3e8:5fec%13 POST /CertificateRegistrationSvc/Certificate/VerifyRequest - 443 - 
  fe80::f53d:89b8:c3e8:5fec%13 NDES_Plugin - 201 0 0 341 875
  ```

- **NDESPlugin ログ**:

  ```
  Calling VerifyRequest ...  
  Sending request to certificate registration point.
  ```

  次の例は、デバイスのチャレンジ要求の検証が成功し、NDES から CA に接続できることを示しています。

  ```
  Verify challenge returns true
  Exiting VerifyRequest with 0x0
  ```

- **CertificateRegistrationPoint.svclog**:

  `Validation Phase 1 finished with status True.`  
  `Validation Phase 3 finished with status True.`  
  `VerifyRequest Finished with status True`


**成功のインジケーターが存在しない場合**:

これらのエントリが見つからない場合は、まず、[デバイスから NDES サーバーへの通信](troubleshoot-scep-certificate-device-to-ndes.md#troubleshoot-common-errors)に関するトラブルシューティングのガイダンスを確認してください。

その記事の情報が問題の解決に役立たない場合は、問題を示す可能性がある以下のその他のエントリを参照してください。

### <a name="ndespluginlog-contains-an-error-12175"></a>NDESPlugin.log にエラー 12175 が含まれている

ログに次のようなエラー 12175 が含まれている場合、SSL 証明書に問題がある可能性があります。

```
WINHTTP_CALLBACK_STATUS_FLAG_CERT_CN_INVALID
Failed to send http request /CertificateRegistrationSvc/Certificate/VerifyRequest. Error 12175
```

*[サブジェクトの別名]* が存在する場合、最新のブラウザーやモバイル デバイス上のブラウザーでは、SSL 証明書の *[共通名]* が無視されます。

**解決方法**: *[共通名]* と *[サブジェクトの別名]* の次の属性を使用して Web サーバー SSL 証明書を発行し、IIS のポート 443 にバインドします。

  - **サブジェクト名**  
    CN = 外部サーバー名
  - **サブジェクトの別名**  
     名前 = 外部サーバー名  
     DNS 名 = 内部サーバー名

### <a name="ndespluginlog-contains-an-error-403--forbidden-access-is-denied"></a>NDESPlugin.log に "エラー 403 - 許可されていません:アクセスが拒否されました" が含まれている。

次のログに次のようなエラー 403 が含まれている場合は、クライアント証明書が信頼されていないか無効である可能性があります。

**NDESPlugin.log**:

```
Sending request to certificate registration point.
Verify challenge returns <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd"> <html xmlns="http://www.w3.org/1999/xhtml"> <head><meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1"/>
<title>403 - Forbidden: Access is denied.</title>
```

**IIS ログ**:

```
POST /CertificateRegistrationSvc/Certificate/VerifyRequest - 443 -<IP_address>
NDES_Plugin - 403 16 2148204809 453  
```

この問題が発生するのは、NDES サーバーの [信頼されたルート証明機関] 証明書ストアに、中間 CA 証明書がある場合です。

証明書の *[発行先]* と *[発行元]* の値が同じである場合は、ルート証明書です。 そうでない場合は、中間証明書です。

**解決方法**:問題を解決するには、信頼されたルート証明機関の証明書ストアから中間 CA 証明書を特定して削除します。

### <a name="ndespluginlog-indicates-the-challenge-returns-false"></a>NDESPlugin.log には、チャレンジから false が返されていることが示されます。

チャレンジの結果から **false** が返された場合は、*CertificateRegistrationPoint.svclog* でエラーを確認します。 たとえば、次のエントリのような "Signing certificate could not be retrieved" (署名証明書を取得できませんでした) というエラーが表示されることがあります。

```
Signing certificate could not be retrieved. System.Security.Cryptography.CryptographicException: m_safeCertContext is an invalid handle. at System.Security.Cryptography.X509Certificates.X509Certificate.ThrowIfContextInvalid() at System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString() at Microsoft.ConfigurationManager.CertRegPoint.CRPCertificate.RetrieveSigningCert(String certThumbprint
```

**解決方法**:コネクタがインストールされているサーバー上でレジストリ エディターを開き、`HKLM\SOFTWARE\Microsoft\MicrosoftIntune\NDESConnector` レジストリ キーを見つけて、SigningCertificate 値が存在するかどうかを確認します。

この値が存在しない場合は、services.msc で Intune コネクタ サービスを再起動し、値がレジストリに存在するかどうかを確認します。 値がまだ存在しない場合、NDES と Intune サービスのサーバー間のネットワーク接続に問題があることがよくある原因です。

## <a name="ndes-passes-the-request-to-issue-the-certificate"></a>NDES からは、証明書を発行する要求が渡されます。

証明書登録ポイント (ポリシー モジュール) による検証が正常に完了すると、NDES からデバイスの代理で CA に証明書の要求が渡されます。

**成功を示すログ エントリ**:

- **NDESPlugin ログ**:

  ```
  Verify challenge returns true
  Exiting VerifyRequest with 0x0
  ```

- **IIS ログ**:

  ```
  fe80::f53d:89b8:c3e8:5fec%13 GET /certsrv/mscep/mscep.dll/pkiclient.exe ... 80 - 
  fe80::f53d:89b8:c3e8:5fec%13 Mozilla/4.0+(compatible;+Win32;+NDES+client) - 200 0 0 2713 1296
  ```

- **CertificateRegistrationPoint.svclog**:

  `Validation Phase 1 finished with status True.`  
  `Validation Phase 3 finished with status True.`  
  `VerifyRequest Finished with status True`

**成功のインジケーターが存在しない場合**:

成功を示すエントリが表示されない場合は、次の手順を実行します。

1. 証明書登録ポイントによってチャレンジが検証されるときに、*CertificateRegistrationPoint.svclog* に記録された問題を探します。 次の行の間のエントリを探します。

   - VerifyRequest Started. (VerifyRequest が開始されました。)
   - VerifyRequest Finished with status False (VerifyRequest が False の状態で完了しました)

2. CA 上で証明機関 MMC を開き、 **[失敗した要求]** を選択して、問題の特定に役立つエラーを探しします。 次の図に例を示します。

   ![失敗した要求の例](../protect/media/troubleshoot-scep-certificate-ndes-policy-module/failed-requests.png)

3. CA のアプリケーション イベント ログでエラーを確認します。 通常、前の手順で **[失敗した要求]** に表示されたエラーを確認できます。 次の図に例を示します。

   ![アプリケーション ログを確認する](../protect/media/troubleshoot-scep-certificate-ndes-policy-module/application-log-errors.png)

## <a name="next-steps"></a>次のステップ

NDES ポリシー モジュールで要求が検証され、要求が証明機関に転送された場合、次の手順は、[デバイスへの証明書の配信](troubleshoot-scep-certificate-delivery.md)を確認することです。
