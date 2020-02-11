---
title: Microsoft Intune で SCEP を使用する場合にデバイスへの証明書の展開が成功したというレポートのトラブルシューティング | Microsoft Docs
description: SCEP 証明書プロファイルを使用してプロビジョニングされた証明書の展開の成功に関する NDES およびコネクタから Intune へのレポートのトラブルシューティングを行います。
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
ms.openlocfilehash: 2ccc738626efc140efca46d1b997164ed36dd37f
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2020
ms.locfileid: "76916020"
---
# <a name="troubleshoot-ndes-reporting-of-certificate-deployments-in-microsoft-intune"></a>Microsoft Intune での証明書の展開の NDES レポートのトラブルシューティング

次の情報を使用して、デバイスに証明書が配信されたことが、NDES および Microsoft Intune Certificate Connector から Intune へ正常に報告されていることを確認します。 Intune へのレポートは、SCEP 証明書プロファイルを使用して Windows デバイスに証明書をプロビジョニングする処理の最後のフェーズです。

この記事は、[SCEP 通信ワークフロー](troubleshoot-scep-certificate-profiles.md)の手順 6 に適用されます。

## <a name="review-for-signs-of-successful-reporting"></a>成功したレポートの署名を確認する

レポートが成功した場合は、NDES サーバー上で次の例のようなエントリが見つかります。

- **IIS ログ**:

  `fe80::f53d:89b8:c3e8:5fec%13 POST /CertificateRegistrationSvc/Certificate/Notify - 443 - fe80::f53d:89b8:c3e8:5fec%13 NDES_Plugin - 204 0 0 277 62`

- **NDESPlugin.log**:

  ```
  Calling Notifyrequest ...
  Sending request to certificate registration point.
  Exiting Notify with 0x0
  ```

- **CertificateRegistrationPoint.svclog**:

  ![Intune Certificate Connector ログ](../protect/media/troubleshoot-scep-certificate-reporting/certificate-registration-point-log.png)

- **NDESConnector.svclog**:

  ![Intune Certificate Connector ログ](../protect/media/troubleshoot-scep-certificate-reporting/ndesconnector-log.png)

- **CertificateRequestStatus**:

  *%ProgramFiles%\Microsoft Intune\CertificateRequestStatus* フォルダーに移動します。ここには、証明書要求の状況ファイルを含む **Failed**、**Processing**、および **Succeed** フォルダーがあります。

  証明書要求が正常に処理されると、**Succeed** フォルダーに新しいファイルが表示されます。 *Notepad.exe* を使用してファイルを開き、Intune Certificate Connector によって Intune サービスにアップロードされたデータを確認できます。 アップロードされるデータには、**CertificateSerialNumber**、**UserID**、**DeviceID**、**Thumbprint** などの詳細が含まれています。

### <a name="troubleshoot-stuck-files"></a>スタック ファイルのトラブルシューティング

*Succeed* フォルダーに新しいファイルが作成されていない場合は、*Processing* フォルダーにファイルがスタックしていないかどうかを確認します。

Intune コネクタ サービスが NDES サーバー上で開始されていることと、Ndesconnector.svclog にエラーがないことを確認します。

## <a name="next-steps"></a>次のステップ

[Microsoft Intune のサポートを受ける方法](../fundamentals/get-support.md)
