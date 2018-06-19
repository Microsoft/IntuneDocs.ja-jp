---
title: Microsoft Intune - Azure での証明書プロファイルの作成 | Microsoft Docs
description: デバイスに対して、SCEP または PKCS 証明書の環境を構成して証明書プロファイルを追加または作成し、パブリック証明書をエクスポートし、Azure Portal でプロファイルを作成してから、Azure Portal の Microsoft Intune で証明書プロファイルに SCEP または PKCS を割り当てます
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5eccfa11-52ab-49eb-afef-a185b4dccde1
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 89f8ddc105787bc7ff4f7cfc1e226d28589ecbbf
ms.sourcegitcommit: 9536300a6211bac4bdc733593a40c1ae47611de3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2018
ms.locfileid: "31771807"
---
# <a name="configure-a-certificate-profile-for-your-devices-in-microsoft-intune"></a>Microsoft Intune でデバイスの証明書プロファイルを構成する

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

VPN、Wi-Fi、または電子メール プロファイル経由でユーザーが企業リソースへアクセスできるようにする場合、証明書を使用してこれらの接続を認証することができます。 証明書を使用する場合は、接続の認証にユーザー名とパスワードを入力する必要はありません。

Intune を使用して、管理するデバイスに証明書を割り当てることができます。 Intune では、次の種類の証明書の割り当てと管理がサポートされています。

- Simple Certificate Enrollment Protocol (SCEP)
- PKCS#12 (または PFX)

これらの証明書の種類には、それぞれ独自の前提条件とインフラストラクチャの要件があります。

## <a name="overview"></a>概要

1. 適切な証明書インフラストラクチャを構成します。 [SCEP 証明書](certificates-scep-configure.md)および [PKCS 証明書](certficates-pfx-configure.md)を使用できます。

2. 各デバイスにルート証明書または中間証明機関 (CA) 証明書をインストールして、デバイスが CA の正当性を認識できるようにします。 これを行うには、**信頼された証明書プロファイル**を作成して割り当てます。 このプロファイルを割り当てると、Intune で管理しているデバイスがルート証明書を要求して受け取ります。 プラットフォームごとに別個のプロファイルを作成する必要があります。 信頼された証明書プロファイルは、次のプラットフォームで使用できます。

    - iOS 8.0 以降
    - macOS 10.11 以降
    - Android 4.0 以降
    - Android for Work
    - Windows 8.1 以降
    - Windows Phone 8.1 以降
    - Windows 10 以降

3. デバイスが VPN、Wi-Fi、電子メールによるアクセスの認証に使用する証明書を要求するように、証明書プロファイルを作成します。 次のプラットフォームを実行するデバイスに対しては、**PKCS** または **SCEP** 証明書プロファイルを作成して割り当てることができます。

   - iOS 8.0 以降
   - Android 4.0 以降
   - Android for Work
   - Windows 10 (Desktop および Mobile) 以降

   次のプラットフォームを実行するデバイスの場合は、**SCEP** 証明書プロファイルのみを使用できます。

   - macOS 10.9 以降
   - Windows Phone 8.1 以降

必ず、デバイス プラットフォームごとに別個のプロファイルを作成してください。 プロファイルを作成したら、それを既に作成済みの信頼されたルート証明書プロファイルに関連付けます。

### <a name="further-considerations"></a>その他の注意事項

- エンタープライズ証明機関がない場合は、作成する必要があります。
- SCEP プロファイルを使用する場合は、ネットワーク デバイス登録サービス (NDES) サーバーを構成します。
- SCEP プロファイルと PKCS プロファイルのどちらを使用する場合でも、Microsoft Intune 証明書コネクタをダウンロードして構成します。


## <a name="step-1-configure-your-certificate-infrastructure"></a>手順 1- 証明書インフラストラクチャを構成する

インフラストラクチャの構成については、証明書プロファイルの種類に応じて次のトピックのいずれかを参照してください。

- [Intune で SCEP 証明書を構成して管理する](certificates-scep-configure.md)
- [Intune で PKCS 証明書を構成して管理する](certficates-pfx-configure.md)


## <a name="step-2-export-your-trusted-root-ca-certificate"></a>手順 2 - 信頼されたルート CA 証明書をエクスポートする

発行元 CA、または発行元 CA を信頼するデバイスから、信頼されたルート証明機関 (CA) 証明書をパブリック証明書 (.cer) としてエクスポートします。 秘密キー (.pfx) をエクスポートしないでください。

信頼された証明書プロファイルを構成するときにこの証明書をインポートします。

## <a name="step-3-create-trusted-certificate-profiles"></a>手順 3 - 信頼された証明書プロファイルを作成する
SCEP または PKCS 証明書プロファイルを作成する前に、信頼された証明書プロファイルを作成します。 デバイス プラットフォームごとに、信頼された証明書プロファイルと SCEP または PKCS プロファイルが必要です。 信頼された証明書を作成する手順は、各デバイス プラットフォームで同様です。

1. サインイン、 [Azure ポータル](https://portal.azure.com)します。
2. **[すべてのサービス]**、**[Intune]** の順に選択します。 Intune は **[監視 + 管理]** セクションにあります。
3. **[Intune]** ウィンドウで、**[デバイス構成]** を選択します。
2. **[デバイス構成]** ウィンドウで、**[管理]** > **[プロファイル]** の順に選択します。
3. [プロファイル] ウィンドウで **[プロファイルの作成]** を選択します。
4. **[プロファイルを作成します]** ウィンドウで、信頼された証明書プロファイルの**名前**と**説明**を入力します。
5. **[プラットフォーム]** ドロップダウン リストで、この信頼された証明書のデバイス プラットフォームを選択します。 現時点では、証明書設定に対応している次のいずれかのプラットフォームを選択できます。

    - **Android**
    - **Android for Work**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 以降**
    - **Windows 10 以降**

6. **[プロファイルの種類]** ドロップダウン リストで、**[信頼済み証明書]** を選択します。
7. タスク 1 で保存した証明書を参照し、**[OK]** をクリックします。
8. Windows 8.1 および Windows 10 デバイスの場合のみ、信頼された証明書の**保存先ストア**を以下から選択します。
    - **コンピューター証明書ストア - ルート**
    - **コンピューター証明書ストア - 中間**
    - **ユーザー証明書ストア - 中間**
8. 完了したら、**[OK]** を選択し、**[プロファイルの作成]** ウィンドウに戻り、**[作成]** を選択します。

プロファイルが作成され、リストに表示されます。 このプロファイルをグループに割り当てる場合は、[デバイス プロファイルの割り当て](device-profile-assign.md)に関するページを参照してください。

Android デバイスでは、サードパーティにより信頼できる証明書がインストールされたことを知らせるメッセージが表示される場合があります。

## <a name="step-4-create-scep-or-pkcs-certificate-profiles"></a>手順 4 – SCEP または PKCS 証明書プロファイルを作成する

各種類の証明書プロファイルの構成と割り当てについては、次のトピックのいずれかを参照してください。

- [Intune で SCEP 証明書を構成して管理する](certificates-scep-configure.md)
- [Intune で PKCS 証明書を構成して管理する](certficates-pfx-configure.md)

信頼された証明書プロファイルを作成した後、使用する各プラットフォーム用の SCEP または PKCS 証明書プロファイルを作成します。 SCEP 証明書プロファイルを作成する場合は、その同じプラットフォームに対する信頼された証明書プロファイルを入力します。 この手順により 2 つの証明書プロファイルがリンクされますが、それでも各プロファイルを個別に割り当てる必要があります。

## <a name="next-steps"></a>次の手順
デバイス プロファイルを割り当てる方法に関する一般的な情報については、[デバイス プロファイルを割り当てる方法](device-profile-assign.md)に関する記事を参照してください。
