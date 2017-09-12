---
title: "Intune VPN 設定を構成する方法"
titleSuffix: Azure portal
description: "Intune を使用して、管理対象デバイスの VPN 接続を構成する方法について説明します。\""
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 06/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 42f9b104-c1f6-4dfc-8aa4-1d33e1eaf61f
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c894a0314af1967dce67a7ffc5b3279bff6125f4
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/09/2017
---
# <a name="how-to-configure-vpn-settings-in-microsoft-intune"></a>Microsoft Intune で VPN の設定を構成する方法

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

仮想プライベート ネットワーク (VPN) を使用すると、会社のユーザーが社内ネットワークにリモート アクセスする際にセキュリティで保護することができます。 デバイスは、VPN 接続プロファイルを使用して、VPN サーバーとの接続を開始します。 Microsoft Intune の **VPN プロファイル**を使用して、VPN 設定を組織内のユーザーとデバイスに割り当て、社内ネットワークに簡単かつ安全に接続できるようにします。

たとえば、すべての iOS デバイスに対して、企業ネットワーク上のファイル共有に接続するために必要な設定をプロビジョニングするとします。 企業ネットワークに接続するために必要な設定を含む VPN プロファイルを作成し、そのプロファイルを iOS デバイスを使用しているすべてのユーザーに割り当てます。 使用できるネットワークの一覧に VPN 接続が表示されるので、ユーザーは最小限の労力で接続できます。

## <a name="vpn-connection-types"></a>VPN 接続の種類

次の接続の種類を使用して、VPN プロファイルを作成できます。

|接続の種類|Android<br>Android for Work|iOS|macOS|Windows Phone 8。1|Windows 8.1|Windows 10|
|-|-|-|-|-|-|-|
|Pulse Secure|○|○|○|○|○|[はい]|
|Cisco (IPSec)|いいえ|○|[いいえ]|いいえ|いいえ|いいえ|
|Citrix|○ (Android のみ)|Yes|[いいえ]|いいえ|いいえ|いいえ|
|F5 Edge Client|○|○|○|○|○|○|
|Dell SonicWALL Mobile Connect|○|○|○|○|○|[はい]|
|Check Point Capsule VPN|Yes|○|○|○|○|[はい]|
|Cisco AnyConnect|○|○|○|[いいえ]|いいえ|いいえ|
|自動|いいえ|いいえ|いいえ|いいえ|[いいえ]|Yes|
|IKEv2|いいえ|いいえ|いいえ|いいえ|[いいえ]|○|
|L2TP|いいえ|いいえ|いいえ|いいえ|[いいえ]|[はい]|
|PPTP|いいえ|いいえ|いいえ|いいえ|[いいえ]|Yes|
|カスタム|いいえ|○|○|[いいえ]|いいえ|いいえ|


> [!IMPORTANT]
> デバイスに割り当てられた VPN プロファイルを使用する前に、プロファイル用の該当する VPN アプリをインストールする必要があります。 [Microsoft Intune でのアプリ管理の概要](app-management.md)に関する記事の情報を参考にして、Intune を使ってアプリを割り当ててください。  

[カスタム VPN プロファイルの作成](custom-vpn-profiles-create.md)に関する記事では、URI 設定を使用してカスタム VPN プロファイルを作成する方法について説明しています。     

## <a name="create-a-device-profile-containing-vpn-settings"></a>VPN 設定を含むデバイス プロファイルの作成

1. Azure ポータルにサインインします。
2. **[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
3. **[Intune]** ブレードで、**[デバイス構成]** を選択します。
2. **[デバイス構成]** ブレードで、**[管理]** > **[プロファイル]** の順に選択します。
3. [プロファイル] ブレードで、**[プロファイルを作成します]** を選択します。
4. **[プロファイルを作成します]** ブレードで、VPN プロファイルの**名前**と**説明**を入力します。
5. **[プラットフォーム]** ドロップダウン リストで、VPN 設定を適用するデバイス プラットフォームを選択します。 現時点では、VPN デバイス設定に対応している次のいずれかのプラットフォームを選択できます。
    - **Android**
    - **Android for Work**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 以降**
    - **Windows 10 以降**
6. **[プロファイルの種類]** ドロップダウン リストで、**[VPN]** を選択します。
7. 選択したプラットフォームによって構成できる設定が異なります。 各プラットフォームの詳細な設定については、次のいずれかのトピックを参照してください。
    - [Android と Android for Work の設定](vpn-settings-android.md)
    - [iOS の設定](vpn-settings-ios.md)
    - [macOS の設定](vpn-settings-macos.md)
    - [Windows Phone 8.1 の設定](vpn-settings-windows-phone-8-1.md)
    - [Windows 8.1 の設定](vpn-settings-windows-8-1.md)
    - [Windows 10 の設定](vpn-settings-windows-10.md)
8. 完了したら、**[プロファイルを作成します]** ブレードに戻り、**[作成]** をクリックします。

プロファイルが作成され、プロファイルの一覧ブレードに表示されます。
このプロファイルをグループに割り当てる場合は、[デバイス プロファイルを割り当てる方法](device-profile-assign.md)に関する記事を参照してください。


## <a name="methods-of-securing-vpn-profiles"></a>VPN プロファイルをセキュリティで保護する方法

VPN プロファイルは、さまざまな製造元から提供される多くの異なる接続の種類およびプロトコルに対応しています。 これらの接続は、通常、次の 2 つの方法のどちらかを使用してセキュリティで保護されます。

### <a name="certificates"></a>証明書

VPN プロファイルを作成するときに、Intune で事前に作成した SCEP または PKCS の証明書プロファイルを選択します。 これは ID 証明書と呼ばれます。 ユーザーのデバイスが接続を許可されていることを示すために作成した信頼済み証明書プロファイル (または、*ルート証明書*) に対して認証を行うために使用されます。 信頼できる証明書は、VPN 接続を認証するコンピューター (通常は VPN サーバー) に割り当てられます。

Intune で証明書プロファイルを作成および使用する方法の詳細については、[Microsoft Intune で証明書を構成する方法](certificates-configure.md)に関する記事を参照してください。

### <a name="user-name-and-password"></a>ユーザー名とパスワード

ユーザーは、ユーザー名とパスワードを提供することにより、VPN サーバーに対して認証を行います。
