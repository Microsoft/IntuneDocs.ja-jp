---
title: Microsoft Intune Certificate Connector とイベント ID のトラブルシューティング | Microsoft Docs
titleSuffix: Microsoft Intune
description: イベント ID と説明を確認して Microsoft Intune Certificate Connector をトラブルシューティングし、Intune Certificate Connector の診断コードを確認します。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 05/01/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2d798f22ee4e0f11f46626eec01ad3b739d61467
ms.sourcegitcommit: dd6755383ba89824d1cc128698a65fde6bb2de55
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/14/2019
ms.locfileid: "72306709"
---
# <a name="intune-certificate-connector-events-and-diagnostic-codes"></a>Intune Certificate Connector のイベントと診断コード

バージョン 6.1806.x.x 以降の Intune コネクタ サービスは、**イベント ビューアー** ( **[アプリケーションとサービス ログ]**  >  **[Microsoft Intune コネクタ]** ) にイベントを記録します。 これらのイベントを使うと、Intune コネクタの構成の潜在的な問題のトラブルシューティングに役立ちます。 これらのイベントには、操作の成功と失敗が記録され、IT 管理者によるトラブルシューティングに役立つ診断コードとメッセージも含まれます。

> [!TIP]  
> 問題をトラブルシューティングし、Intune Connector の設定を確認するには、[証明機関のスクリプトのサンプル](https://aka.ms/intuneconnectorverificationscript)に関するページを参照してください。

## <a name="event-ids-and-descriptions"></a>イベント ID と説明

| イベント ID      | イベント名    | イベントの説明 | 関連する診断コード |
| ------------- | ------------- | -------------     | -------------            |
| 10010 | StartedConnectorService  | コネクタ サービスが開始しました | 0x00000000、0x0FFFFFFF |
| 10020 | StoppedConnectorService  | コネクタ サービスが停止しました | 0x00000000、0x0FFFFFFF |
| 10100 | CertificateRenewal_Success  | コネクタの登録証明書が正常に更新されました | 0x00000000、0x0FFFFFFF |
| 10102 | CertificateRenewal_Failure  | コネクタの登録証明書の更新が失敗しました。 コネクタを再インストールしてください。 | 0x00000000、0x00000405、0x0FFFFFFF |
| 10302 | RetrieveCertificate_Error  | レジストリからコネクタの登録証明書を取得できませんでした。 このイベントに関連する証明書のサムプリントに対するイベントの詳細を確認してください。 | 0x00000000、0x00000404、0x0FFFFFFF |
| 10301 | RetrieveCertificate_Warning  | イベントの詳細で診断情報を確認してください。 | 0x00000000、0x00000403、0x0FFFFFFF |
| 20100 | PkcsCertIssue_Success  | PKCS 証明書を正常に発行しました。 このイベントに関連するデバイス ID、ユーザー ID、CA 名、証明書テンプレート名、および証明書のサムプリントについては、イベントの詳細を確認してください。 | 0x00000000、0x0FFFFFFF |
| 20102 | PkcsCertIssue_Failure  | PKCS 証明書を発行できませんでした このイベントに関連するデバイス ID、ユーザー ID、CA 名、証明書テンプレート名、および証明書のサムプリントについては、イベントの詳細を確認してください。 | 0x00000000、0x00000400、0x00000401、0x0FFFFFFF |
| 20200 | RevokeCert_Success  | 証明書が正常に取り消されました。 このイベントに関連するデバイス ID、ユーザー ID、CA 名、および証明書シリアル番号については、イベントの詳細を確認してください。 | 0x00000000、0x0FFFFFFF |
| 20202 | RevokeCert_Failure | 証明書を取り消すことができませんでした。 このイベントに関連するデバイス ID、ユーザー ID、CA 名、および証明書シリアル番号については、イベントの詳細を確認してください。 詳細については、NDES SVC のログを参照してください。   | 0x00000000、0x00000402、0x0FFFFFFF |
| 20300 | Upload_Success | 証明書の要求または取り消しのデータが、正常にアップロードされました。 アップロードの詳細については、イベントの詳細を確認してください。 | 0x00000000、0x0FFFFFFF |
| 20302 | Upload_Failure | 証明書の要求または取り消しのデータをアップロードできませんでした。 障害発生時点を特定するには、イベントの詳細のアップロード状態を確認してください。| 0x00000000、0x0FFFFFFF |
| 20400 | Download_Success | 証明書の署名、クライアント証明書のダウンロード、または証明書の取り消しの要求が、正常にダウンロードされました。 ダウンロードの詳細については、イベントの詳細を確認してください。  | 0x00000000、0x0FFFFFFF |
| 20402 | Download_Failure | 証明書の署名、クライアント証明書のダウンロード、または証明書の取り消しの要求を、ダウンロードできませんでした。 ダウンロードの詳細については、イベントの詳細を確認してください。 | 0x00000000、0x0FFFFFFF |
| 20500 | CRPVerifyMetric_Success  | 証明書登録ポイントがクライアントのチャレンジを正常に検証しました | 0x00000000、0x0FFFFFFF |
| 20501 | CRPVerifyMetric_Warning  | 証明書登録ポイントは完了しましたが、要求を拒否しました。 詳細については、診断コードとメッセージを参照してください。 | 0x00000000、0x00000411、0x0FFFFFFF |
| 20502 | CRPVerifyMetric_Failure  | 証明書登録ポイントがクライアントのチャレンジを検証できませんでした。 詳細については、診断コードとメッセージを参照してください。 チャレンジに対応するデバイス ID については、イベント メッセージの詳細を参照してください。 | 0x00000000、0x00000408、0x00000409、0x00000410、0x0FFFFFFF |
| 20600 | CRPNotifyMetric_Success  | 証明書登録ポイントが通知プロセスを正常に完了し、クライアント デバイスに証明書を送信しました。 | 0x00000000、0x0FFFFFFF |
| 20602 | CRPNotifyMetric_Failure  | 証明書登録ポイントが通知プロセスを完了できませんでした。 要求については、イベント メッセージの詳細を参照してください。 NDES サーバーと CA の間の接続を確認してください。 | 0x00000000、0x0FFFFFFF |

## <a name="diagnostic-codes"></a>診断コード

| 診断コード | 診断名 | 診断メッセージ |
| -------------   | -------------   | -------------      |
| 0x00000000 | 成功  | 成功 |
| 0x00000400 | PKCS_Issue_CA_Unavailable  | 証明機関は有効ではないか、到達可能ではありません。 証明機関が使用可能であること、およびサーバーが証明機関と通信できることを確認してください。 |
| 0x00000401 | Symantec_ClientAuthCertNotFound  | Symantec クライアント認証証明書がローカル証明書ストアに見つかりませんでした。 詳細については、「[Symantec 登録承認証明書のインストール](certificates-digicert-configure.md#install-the-digicert-ra-certificate)」をご覧ください。  |
| 0x00000402 | RevokeCert_AccessDenied  | 指定されたアカウントには、CA から証明書を取り消すアクセス許可がありません。 発行元 CA を特定するには、イベント メッセージの詳細の CA 名フィールドを参照してください。  |
| 0x00000403 | CertThumbprint_NotFound  | 入力に一致する証明書を見つけられませんでした。 証明書コネクタを登録してからやり直してください。 |
| 0x00000404 | Certificate_NotFound  | 提供された入力に一致する証明書を見つけられませんでした。 証明書コネクタを再登録してからやり直してください。 |
| 0x00000405 | Certificate_Expired  | 証明書の有効期限が切れました。 証明書コネクタを再登録して証明書を更新してからやり直してください。 |
| 0x00000408 | CRPSCEPCert_NotFound  | CRP 暗号化証明書が見つかりませんでした。 NDES と Intune コネクタが正しくセットアップされていることを確認してください。 |
| 0x00000409 | CRPSCEPSigningCert_NotFound  | 署名証明書を取得できませんでした。 Intune コネクタ サービスが正しく構成されていて動作していることを確認してください。 また、証明書ダウンロード イベントが成功したことを確認してください。 |
| 0x00000410 | CRPSCEPDeserialize_Failed  | SCEP チャレンジ要求の逆シリアル化が失敗しました。 NDES と Intune コネクタが正しくセットアップされていることを確認してください。 |
| 0x00000411 | CRPSCEPChallenge_Expired  | 証明書チャレンジ期限切れのため、要求は拒否されました。 クライアント デバイスは、管理サーバーから新しいチャレンジを取得した後で再試行できます。 |
| 0x0FFFFFFFF | Unknown_Error  | サーバー側でエラーが発生したため、要求を完了できません。 もう一度やり直してください。 |


## <a name="next-steps"></a>次の手順
詳細については、「[Microsoft Intune の SCEP 証明書プロファイルの展開のトラブルシューティング](https://support.microsoft.com/help/4457481/troubleshooting-scep-certificate-profile-deployment-in-intune)」のガイドを参照してください。
