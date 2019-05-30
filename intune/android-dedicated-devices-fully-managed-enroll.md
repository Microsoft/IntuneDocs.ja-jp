---
title: Intune で Android Enterprise の専用デバイスまたはフル マネージド デバイスを登録する
titleSuffix: Microsoft Intune
description: Intune で Android Enterprise 専用デバイスまたはフル マネージド デバイスを登録する方法について説明します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 1/15/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: d81f28b03a41bcdc8b6c9f18ef58e6a42346ba7d
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66049981"
---
# <a name="enroll-your-android-enterprise-dedicated-devices-or-fully-managed-devices-preview"></a>Android Enterprise 専用デバイスまたはフル マネージド デバイスを登録する (プレビュー)

Intune で [Android Enterprise 専用デバイス](android-kiosk-enroll.md)または[フル マネージド デバイス](android-fully-managed-enroll.md)を設定した後、デバイスを登録できます。 Android Enterprise デバイスの登録方法は、オペレーティング システムによって異なります。

| 登録方法 | 専用およびフル マネージド デバイスの最小 Android OS バージョン |
| ----- | ----- |
| 近距離無線通信 | 5.1 |
| トークン エントリ | 6.0 |
| QR コード | 7.0 |
| ゼロ タッチ  | 8.0\* |

\* 参加製造元で。

### <a name="enroll-by-using-near-field-communication-nfc"></a>近距離無線通信 (NFC) を利用して登録する

NFC 対応のデバイスについては、特殊な形式の NFC タグでデバイスにプロビジョニングできます。 独自のアプリや任意の NFC タグ作成ツールを利用できます。 詳細については、「[C-based Android Enterprise device enrollment with Microsoft Intune](https://blogs.technet.microsoft.com/cbernier/2018/10/15/nfc-based-android-enterprise-device-enrollment-with-microsoft-intune/)」 (C ベースの Android エンタープライズ デバイスを Microsoft Intune で登録する) と「[Google's Android Management API documentation](https://developers.google.com/android/management/provision-device#nfc_method)」 (Google の Android 管理 API ドキュメント) を参照してください。

### <a name="enroll-by-using-a-token"></a>トークンを利用して登録する

Android 6 以降のデバイスについては、トークンを利用してデバイスを登録できます。 Android 6.1 以降のバージョンでは、**afw#setup** の登録方法を使用して QR コードのスキャンを活用することもできます。

1. ワイプされたデバイスをオンにします。
2. **[ようこそ]** 画面で、言語を選択します。
3. お使いの **Wifi** に接続し、**[次へ]** を選択します。
4. Google の利用規約に同意し、**[次へ]** を選択します。
5. Google サインイン画面で、Gmail アカウントの代わりに「**afw#setup**」を入力し、**[次へ]** を選択します。
6. **Android デバイス ポリシー** アプリの **[インストール]** を選択します。
7. このポリシーのインストールを続行します。  一部のデバイスでは、追加の規約同意が要求されることがあります。 
8. **[このデバイスを登録]** 画面で、QR コードのスキャンをデバイスに許可するか、トークンの手動入力を選択します。
9. 画面の指示に従って登録を完了します。 

### <a name="enroll-by-using-a-qr-code"></a>QR コードを利用して登録する

Android 7 以降のデバイスでは、登録プロファイルから QR コードをスキャンすることでデバイスを登録できます。

> [!Note]
> ブラウザーをズームすると、デバイスが QR コードをスキャンできない可能性があります。 ブラウザーをさらにズームすると、問題が解決します。

1. Android デバイスで QR 読み取りを起動するには、ワイプした後、最初に表示される画面を複数回タップします。
2. Android 7 デバイスと Android 8 デバイスの場合、QR リーダーをインストールするように求められます。 Android 9 以降のデバイスの場合、QR リーダーが既にインストールされています。
3. QR リーダーを使用して登録プロファイルの QR コードをスキャンし、画面の指示に従って登録します。

### <a name="enroll-by-using-google-zero-touch"></a>Google ゼロ タッチを使用して登録する

Google のゼロ タッチ システムを使用するには、デバイスがそれに対応している必要があり、サービスに関与しているサプライヤーとの提携が必要です。  詳細については、[Google のゼロ タッチ プログラム Web サイト](https://www.android.com/enterprise/management/zero-touch/)をご覧ください。 

1. ゼロ タッチ コンソールで新しい構成を作成します。
2. EMM DPC ドロップダウンから **[Microsoft Intune]** を選択します。
3. Google のゼロ タッチ コンソールで、次の JSON をコピーして DPC 追加フィールドに貼り付けます。 *YourEnrollmentToken* 文字列を、登録プロファイルの一部として作成した登録トークンに置き換えます。 登録トークンは二重引用符で囲んでください。

```
{ 
    "android.app.extra.PROVISIONING_DEVICE_ADMIN_COMPONENT_NAME": "com.google.android.apps.work.clouddpc/.receivers.CloudDeviceAdminReceiver", 

    "android.app.extra.PROVISIONING_DEVICE_ADMIN_SIGNATURE_CHECKSUM": "I5YvS0O5hXY46mb01BlRjq4oJJGs2kuUcHvVkAPEXlg", 

    "android.app.extra.PROVISIONING_DEVICE_ADMIN_PACKAGE_DOWNLOAD_LOCATION": "https://play.google.com/managed/downloadManagingApp?identifier=setup", 

    "android.app.extra.PROVISIONING_ADMIN_EXTRAS_BUNDLE": { 
        "com.google.android.apps.work.clouddpc.EXTRA_ENROLLMENT_TOKEN": "YourEnrollmentToken" 
    } 
} 
```
4. **[適用]** を選択します。


## <a name="next-steps"></a>次の手順
- [Android アプリを展開する](apps-deploy.md)
- [Android 構成ポリシーを追加する](device-profiles.md)

