---
title: Microsoft Intune - Azure での証明書プロファイルの作成 | Microsoft Docs
description: デバイスに対して、SCEP または PKCS 証明書の環境を構成して証明書プロファイルを追加または作成し、パブリック証明書をエクスポートし、Azure Portal でプロファイルを作成してから、Azure Portal の Microsoft Intune で証明書プロファイルに SCEP または PKCS を割り当てます
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 04/08/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5eccfa11-52ab-49eb-afef-a185b4dccde1
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 569ddd9be0c59cf9a4bd7ba1f8b114183ce46d7d
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61508275"
---
# <a name="configure-a-certificate-profile-for-your-devices-in-microsoft-intune"></a>Microsoft Intune でデバイスの証明書プロファイルを構成する

VPN、Wi-Fi、または電子メール プロファイルを介して、企業リソースへのアクセス権をユーザーに付与します。 証明書を使用すると、これらの接続を認証できます。 証明書を使用すると、エンド ユーザーが認証のためにユーザー名とパスワードを入力する必要がなくなります。

Intune を使用して、管理するデバイスに証明書を割り当てることができます。 Intune では、次の種類の証明書の割り当てと管理がサポートされています。

- Simple Certificate Enrollment Protocol (SCEP)
- PKCS#12 (または PFX)

これらの証明書の種類には、それぞれ独自の前提条件とインフラストラクチャの要件があります。


## <a name="overview"></a>概要

1. 適切な証明書インフラストラクチャが設定されていることを確認します。 [SCEP 証明書](certificates-scep-configure.md)および [PKCS 証明書](certficates-pfx-configure.md)を使用できます。

2. 各デバイスにルート証明書または中間証明機関 (CA) 証明書をインストールして、デバイスが CA の正当性を認識できるようにします。 証明書をインストールするには、**信頼された証明書プロファイル**を作成して各デバイスに割り当てます。 このプロファイルを割り当てると、Intune マネージド デバイスはルート証明書を要求し、受信します。 プラットフォームごとに別個のプロファイルを作成する必要があります。 信頼された証明書プロファイルは、次のプラットフォームで使用できます。

    - iOS 8.0 以降
    - macOS 10.11 以降
    - Android 4.0 以降
    - Android エンタープライズ  
    - Windows 8.1 以降
    - Windows Phone 8.1 以降
    - Windows 10 以降

    > [!NOTE]  
    > 証明書プロファイルは、*専用デバイス用に Android エンタープライズ*を実行しているデバイスではサポートされていません。

3. デバイスが VPN、Wi-Fi、電子メールによるアクセスの認証に使用する証明書を要求するように、証明書プロファイルを作成します。 次のプロファイルの種類は、さまざまなプラットフォーム向けに使用できます。  

   | プラットフォーム     |PKCS 証明書|SCEP 証明書| PKCS のインポートされた証明書 | 
   |--------------|----------------|----------------|-------------------|
   | Android                | はい    | はい    | はい    |
   | Android エンタープライズ     | はい    | はい    | はい    |
   | iOS                    | はい    | はい    | はい    |
   | macOS                  |        | はい    | はい    |
   | Windows Phone 8.1      |        | はい    | はい    |
   | Windows 8.1 以降  |        | はい    |        |
   | Windows 10 以降   | はい    | はい    | はい    |

   必ず、デバイス プラットフォームごとに別個のプロファイルを作成してください。 プロファイルを作成したら、それを既に作成済みの信頼されたルート証明書プロファイルに関連付けます。

### <a name="further-considerations"></a>その他の注意事項

- エンタープライズ証明機関がない場合は、作成する必要があります。
- SCEP プロファイルを使用する場合は、ネットワーク デバイス登録サービス (NDES) サーバーを構成します。
- SCEP プロファイルと PKCS プロファイルのどちらを使用する場合でも、Microsoft Intune 証明書コネクタをダウンロードして構成します。


## <a name="step-1-configure-your-certificate-infrastructure"></a>手順 1.証明書インフラストラクチャを構成する

インフラストラクチャの構成については、証明書プロファイルの種類に応じて次の記事のいずれかを参照してください。

- [Intune で SCEP 証明書を構成して管理する](certificates-scep-configure.md)
- [Intune で PKCS 証明書を構成して管理する](certficates-pfx-configure.md)


## <a name="step-2-export-your-trusted-root-ca-certificate"></a>手順 2: 信頼されたルート CA 証明書をエクスポートする

発行元 CA、または発行元 CA を信頼するデバイスから、信頼されたルート証明機関 (CA) 証明書をパブリック証明書 (.cer) としてエクスポートします。 秘密キー (.pfx) をエクスポートしないでください。

信頼された証明書プロファイルを構成するときにこの証明書をインポートします。

## <a name="step-3-create-trusted-certificate-profiles"></a>手順 3: 信頼された証明書プロファイルを作成する
SCEP または PKCS 証明書プロファイルを作成する前に、信頼された証明書プロファイルを作成します。 デバイス プラットフォームごとに、信頼された証明書プロファイルと SCEP または PKCS プロファイルが必要です。 信頼された証明書を作成する手順は、どのデバイス プラットフォームでも同様です。

1. [Azure ポータル](https://portal.azure.com)にサインインします。
2. **[すべてのサービス]** を選択し、**[Intune]** をフィルターとして適用し、**[Microsoft Intune]** を選択します。
3. **[デバイス構成]** > **[管理]** > **[プロファイル]** > **[プロファイルの作成]** の順に選択します。
4. 信頼された証明書プロファイルの **[名前]** と **[説明]** を入力します。
5. **[プラットフォーム]** ドロップダウン リストで、この信頼された証明書のデバイス プラットフォームを選択します。 次のようなオプションがあります。

    - **Android**
    - **Android エンタープライズ**
    - **Android**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 以降**
    - **Windows 10 以降**

6. **[プロファイルの種類]** ドロップダウン リストで、**[信頼済み証明書]** を選択します。
7. 「[手順 2:信頼されたルート CA 証明書をエクスポートする](#step-2-export-your-trusted-root-ca-certificate)」で保存した証明書を参照し、**[OK]** をクリックします。
8. Windows 8.1 および Windows 10 デバイスの場合のみ、信頼された証明書の**保存先ストア**を以下から選択します。

    - **コンピューター証明書ストア - ルート**
    - **コンピューター証明書ストア - 中間**
    - **ユーザー証明書ストア - 中間**

9. 完了したら、**[OK]** を選択し、**[プロファイルの作成]** ウィンドウに戻り、**[作成]** を選択します。

プロファイルが作成され、リストに表示されます。 このプロファイルをグループに割り当てる場合は、[デバイス プロファイルの割り当て](device-profile-assign.md)に関するページを参照してください。

   >[!NOTE]
   > Android デバイスでは、サードパーティにより信頼できる証明書がインストールされたことを知らせるメッセージが表示される場合があります。

## <a name="step-4-create-scep-or-pkcs-certificate-profiles"></a>手順 4:SCEP または PKCS 証明書プロファイルを作成する

各種類の証明書プロファイルの構成と割り当てについては、次の記事のいずれかを参照してください。

- [Intune で SCEP 証明書を構成して管理する](certificates-scep-configure.md)
- [Intune で PKCS 証明書を構成して管理する](certficates-pfx-configure.md)

信頼された証明書プロファイルを作成した後、使用する各プラットフォーム用の SCEP または PKCS 証明書プロファイルを作成します。 SCEP 証明書プロファイルを作成する場合は、その同じプラットフォームに対する信頼された証明書プロファイルを入力します。 この手順により 2 つの証明書プロファイルがリンクされますが、それでも各プロファイルを個別に割り当てる必要があります。

## <a name="next-steps"></a>次の手順
[デバイス プロファイルを割り当てる](device-profile-assign.md)  
[S/MIME を使用して電子メールに署名し、暗号化する](certificates-s-mime-encryption-sign.md)  
[サードパーティの証明機関を使用する](certificate-authority-add-scep-overview.md)
