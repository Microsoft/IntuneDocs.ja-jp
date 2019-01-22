---
title: Intune に Android エンタープライズ キオスク デバイスを登録する
titlesuffix: Microsoft Intune
description: Intune に Android エンタープライズ キオスク デバイスを登録する方法について説明します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 6/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: 5a84bcd820b7596d1b1df01342604562c7853140
ms.sourcegitcommit: a44359b426e19b8bf4b99eca6af2755c6d3c6fb8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54098319"
---
# <a name="set-up-intune-enrollment-of-android-enterprise-kiosk-devices"></a>Android エンタープライズ キオスク デバイスの Intune 登録の設定

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Android は、[専用デバイス](https://developers.google.com/android/work/overview#company-owned-devices-for-dedicated-use)のソリューションが設定されたキオスク スタイルのデバイスに対応しています。 そのようなデバイスは、デジタル サイネージ、チケット印刷、在庫管理など、1 つの目的のために使用されます。 管理者はデバイスの使用を厳しく管理し、限られたアプリと Web リンクのみ許可します。 また、ユーザーがデバイスに他のアプリを追加したり、他の操作を行ったりできないようになっています。

Intune では、Android キオスク デバイスにアプリや設定を展開できます。 Android エンタープライズに関する特定の詳細については、「[Android enterprise requirements](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012)」 (Android エンタープライズの要件) を参照してください。

この方法で管理するデバイスはユーザー アカウントなしで Intune に登録され、エンド ユーザーとは関連付けられません。 個人向けアプリや、Outlook や Gmail など、ユーザー固有アカウント データに対して厳密な要件のあるアプリの使用を意図していません。

## <a name="device-requirements"></a>デバイスの要件

デバイスを Android エンタープライズ キオスク デバイスとして管理するには、以下の要件を満たす必要があります。

- Android OS バージョン 5.1 以降。
- デバイスは、Google Mobile Services (GMS) に接続できる Android ディストリビューションを実行する必要があります。 デバイスで GMS が利用できて、GMS に接続できる必要があります。

## <a name="set-up-android-kiosk-management"></a>Android キオスクの管理を設定する

Android キオスクの管理を設定するには、次の手順に従います。

1. モバイル デバイス管理の準備として、[MDM (モバイル デバイス管理) 機関を **Microsoft Intune** に設定](mdm-authority-set.md)し、そこに指示を求める必要があります。 この項目は、モバイル デバイス管理について初めて Intune を設定するときに一度だけ設定します。
2. [Android エンタープライズ アカウントに Intune テナント アカウントを接続します](connect-intune-android-enterprise.md)。
3. [登録プロファイルを作成します](#create-an-enrollment-profile)。
4. [デバイス グループを作成します](#create-a-device-group)。
5. [キオスク デバイスを登録します](#enroll-the-kiosk-devices)。

### <a name="create-an-enrollment-profile"></a>登録プロファイルの作成

キオスク デバイスを登録できるように、登録プロファイルを作成する必要があります。 プロファイルが作成されると、登録トークン (ランダムな文字列) と QR コードが与えられます。 デバイスの Android OS とバージョンに基づき、トークンか QR コードのいずれかを利用して[キオスク デバイスを登録](#enroll-the-kiosk-devices)できます。

1. [Intune ポータル](https://portal.azure.com)に移動し、**[デバイスの登録]** > **[Android の登録]** > **[キオスクおよびタスク デバイス登録]** の順に進みます。
2. **[作成]** を選択し、必須フィールドに入力します。
    - **[名前]**:動的デバイス グループにプロファイルを割り当てるときに使用する名前を入力します。
    - **[トークンの有効期限]**:トークンの有効期限が切れる日付。 Google は最大 90 日間を強制します。
3. **[作成]** を選択してプロファイルを保存します。

### <a name="create-a-device-group"></a>デバイス グループを作成する

アプリとポリシーの対象を、割り当てたデバイス グループか動的デバイス グループに設定できます。 特定の登録プロファイルで登録されているデバイスに自動でデータを入力するように、次の手順で動的 AAD デバイス グループを構成できます。

1. [Intune ポータル](https://portal.azure.com)に移動し、**[グループ]** > **[すべてのグループ]** > **[新しいグループ]** の順に選択します。
2. **[グループ]** ブレードで、次のように必須フィールドに入力します。
    - **[グループの種類]**:セキュリティ
    - **[グループ名]**:わかりやすい名前を入力します (Factory 1 デバイスなど)
    - **[メンバーシップの種類]**:動的デバイス
3. **[動的クエリの追加]** を選択します。
4. **[動的メンバーシップ ルール]** ブレードで、次のようにフィールドに入力します。
    - **[動的メンバーシップ ルールの追加]**:簡易ルール
    - **[追加するデバイスの場所]**: enrollmentProfileName
    - 中央のボックスで **[一致]** を選択します。
    - 最後のフィールドには、先ほど作成した登録プロファイル名を入力します。
    動的メンバーシップ ルールの詳細については、[AAD 内のグループに対する動的メンバーシップ ルール](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership)に関する記事を参照してください。 
5. **[クエリの追加]** > **[作成]** を選択します。

### <a name="replace-or-remove-tokens"></a>トークンを置換または削除する

トークンと QR コードを置換または削除できます。

- **[トークンの置換]**:[トークンの置換] を利用することで、有効期限が近づいたとき、新しいトークン/QR コードを生成できます。
- **[トークンの取り消し]**:トークン/QR コードをただちに失効させることができます。 取り消した時点から、トークンまたは QR コードは使用できなくなります。 次の場合にこのオプションを使用できます。
    - 認められていない団体と誤ってトークン/QR コードを共有した
    - 登録がすべて完了し、トークン/QR コードが不要になった

トークン/QR コードを取り替えたり、取り消したりしても、登録済みにデバイスに影響が出ることはありません。

1. [Intune ポータル](https://portal.azure.com)に移動し、**[デバイスの登録]** > **[Android の登録]** > **[キオスクおよびタスク デバイス登録]** の順に進みます。
2. 置き換えるか取り消すプロファイルを選択します。
3. **[トークン]** を選択します。
4. トークンを置換するには、**[トークンの置換]** を選択します。
5. トークンを取り消すには、**[トークンの取り消し]** を選択します。

## <a name="enroll-the-kiosk-devices"></a>キオスク デバイスを登録する

登録プロファイルと動的デバイス グループを作成したら、キオスク デバイスを登録できます。 Android デバイスの登録方法は、オペレーティング システムによって異なります。

| 登録方法 | サポートされている最小 Android OS バージョン |
| ----- | ----- |
| 近距離無線通信 | 5.1 |
| トークン エントリ | 6.0 |
| QR コード | 7.0 |
| ゼロ タッチ | 8.0、参加製造元で |

### <a name="enroll-by-using-near-field-communication-nfc"></a>近距離無線通信 (NFC) を利用して登録する

NFC 対応の Android 5.1 以降のデバイスについては、特殊な形式の NFC タグでデバイスにプロビジョニングできます。 独自のアプリや任意の NFC タグ作成ツールを利用できます。 詳細については、[Google の Android 管理 API ドキュメント](https://developers.google.com/android/management/provision-device#nfc_method)をご覧ください。

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

## <a name="managing-apps-on-android-kiosk-devices"></a>Android キオスク デバイスでアプリを管理する

割り当ての種類が [[必須]](apps-deploy.md#to-assign-an-app) に設定されているアプリのみ、Android キオスク デバイスにインストールできます。 アプリは、Android 仕事用プロファイル デバイスと同じ方法で managed Google Play ストアからインストールされます。

アプリは、アプリ開発者が更新版を Google Play に公開したとき、管理対象デバイスで自動的に更新されます。

Android キオスク デバイスからアプリを削除するには、次のいずれかの操作を行います。
-   要求されたアプリの展開を削除します。
-   アプリのアンインストール展開を作成します。


## <a name="next-steps"></a>次の手順
- [Android キオスク アプリを展開する](apps-deploy.md)
- [Android キオスク構成ポリシーを追加する](device-profiles.md)
