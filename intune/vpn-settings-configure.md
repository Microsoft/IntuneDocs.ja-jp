---
title: Microsoft Intune で VPN デバイス プロファイルを作成する - Azure | Microsoft Docs
description: iOS デバイスについて、仮想プライベート ネットワーク (VPN) 接続の種類を表示し、Azure Portal で VPN デバイス プロファイルを作成し、Microsoft Intune で証明書またはユーザー名とパスワードを使って VPN プロファイルをセキュリティで保護するオプションを確認します。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/25/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 11684ceea5aafa7de5a2663e5a69bbbe7367b655
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2019
ms.locfileid: "57394040"
---
# <a name="create-vpn-profiles-in-intune"></a>Intune で VPN プロファイルを作成する

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

仮想プライベート ネットワーク (VPN) を使用すると、会社のユーザーが社内ネットワークにリモート アクセスする際にセキュリティで保護することができます。 デバイスは、VPN 接続プロファイルを使用して、VPN サーバーとの接続を開始します。 Microsoft Intune の **VPN プロファイル**を使用して、VPN 設定を組織内のユーザーとデバイスに割り当て、社内ネットワークに簡単かつ安全に接続できるようにします。

たとえば、すべての iOS デバイスに対して、企業ネットワーク上のファイル共有に接続するために必要な設定をプロビジョニングするとします。 会社のネットワークに接続するための設定が含まれる VPN プロファイルを作成します。 その後、iOS デバイスを持っているすべてのユーザーにこのプロファイルを割り当てます。 使用できるネットワークの一覧に VPN 接続が表示されるので、ユーザーは最小限の労力で接続できます。

Intune のカスタム構成ポリシーを使用して、次のプラットフォームの VPN プロファイルを作成できます。

* Android 4 以降
* Windows 8.1 以降を実行する登録済みのデバイス
* Windows Phone 8.1 以降
* Windows 10 デスクトップを実行する登録済みのデバイス
* Windows 10 Mobile
* Windows Holographic for Business

## <a name="vpn-connection-types"></a>VPN 接続の種類

次の接続の種類を使用して、VPN プロファイルを作成できます。

|接続の種類|Android<br>Android 仕事用プロファイル|iOS|macOS|Windows Phone 8。1|Windows 8.1|Windows 10|
|-|-|-|-|-|-|-|
|自動|[いいえ]|[いいえ]|[いいえ]|[いいえ]|[いいえ]|はい|
|Check Point Capsule VPN|はい|はい|はい|はい|はい|はい|
|Cisco AnyConnect|はい|はい|はい|いいえ|[いいえ]|[いいえ]|
|SonicWall Mobile Connect|はい|はい|はい|はい|はい|はい|
|F5 Edge Client|はい|はい|はい|はい|はい|はい|
|Palo Alto Networks GlobalProtect|[いいえ]|はい|いいえ|[いいえ]|[いいえ]|はい|
|Pulse Secure|はい|はい|はい|はい|はい|はい|
|Cisco (IPSec)|[いいえ]|はい|いいえ|[いいえ]|[いいえ]|[いいえ]|
|Citrix|○ (Android のみ)|はい|いいえ|[いいえ]|[いいえ]|はい|
|IKEv2|[いいえ]|[いいえ]|[いいえ]|[いいえ]|[いいえ]|はい|
|L2TP|[いいえ]|[いいえ]|[いいえ]|[いいえ]|[いいえ]|はい|
|PPTP|[いいえ]|[いいえ]|[いいえ]|[いいえ]|[いいえ]|はい|
|Zscaler|[いいえ]|はい|いいえ|[いいえ]|[いいえ]|[いいえ]|
|カスタム VPN|[いいえ]|はい|はい|いいえ|[いいえ]|[いいえ]|

> [!IMPORTANT]
> デバイスに割り当てられた VPN プロファイルを使用する前に、プロファイル用の該当する VPN アプリをインストールする必要があります。 [Microsoft Intune でのアプリ管理の概要](app-management.md)に関する記事の情報を参考にして、Intune を使ってアプリを割り当ててください。  

URI の設定を使ってカスタム VPN プロファイルを作成する方法については、[カスタム VPN プロファイルの作成](custom-settings-configure.md)に関するページをご覧ください。

## <a name="create-a-device-profile-containing-vpn-settings"></a>VPN 設定を含むデバイス プロファイルの作成

1. [Azure ポータル](https://portal.azure.com)にサインインします。
2. **[すべてのサービス]** を選択し、**[Intune]** をフィルターとして適用し、**[Microsoft Intune]** を選択します。
3. **[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** の順に選択します。
4. VPN プロファイルの **[名前]** と **[説明]** を入力します。
5. **[プラットフォーム]** ドロップダウン リストで、VPN 設定を適用するデバイス プラットフォームを選択します。 現時点では、VPN デバイス設定に対応している次のいずれかのプラットフォームを選択できます。
   - **Android**
   - **Android エンタープライズ**
   - **Android**
   - **macOS**
   - **Windows Phone 8.1**
   - **Windows 8.1 以降**
   - **Windows 10 以降**
6. **[プロファイルの種類]** ドロップダウン リストで、**[VPN]** を選択します。
7. 選択したプラットフォームによって構成できる設定が異なります。 各プラットフォームの詳細な設定については、次のいずれかのトピックを参照してください。
   - [Android および Android 仕事用プロファイルの設定](vpn-settings-android.md)
   - [iOS の設定](vpn-settings-ios.md)
   - [macOS の設定](vpn-settings-macos.md)
   - [Windows Phone 8.1 の設定](vpn-settings-windows-phone-8-1.md)
   - [Windows 8.1 の設定](vpn-settings-windows-8-1.md)
   - [Windows 10 の設定](vpn-settings-windows-10.md) (Windows Holographic for Business を含む)
8. 完了したら、プロファイルを **[作成]** します

プロファイルが作成され、プロファイル一覧に表示されます。 このプロファイルをグループに割り当てる場合は、[デバイス プロファイルの割り当て](device-profile-assign.md)に関するページを参照してください。

## <a name="methods-of-securing-vpn-profiles"></a>VPN プロファイルをセキュリティで保護する方法

VPN プロファイルは、さまざまな製造元から提供される多くの異なる接続の種類およびプロトコルに対応しています。 これらの接続は、通常、次の 2 つの方法のどちらかを使用してセキュリティで保護されます。

### <a name="certificates"></a>証明書

VPN プロファイルを作成するときに、Intune で事前に作成した SCEP または PKCS の証明書プロファイルを選択します。 このプロファイルは ID 証明書と呼ばれます。 ユーザーのデバイスの接続を許可するために作成した信頼済み証明書プロファイル (または、"*ルート証明書*") に対して認証を行うために使用されます。 信頼できる証明書は、VPN 接続を認証するコンピューター (通常は VPN サーバー) に割り当てられます。

Intune で証明書プロファイルを作成および使用する方法の詳細については、[Microsoft Intune で証明書を構成する方法](certificates-configure.md)に関する記事を参照してください。

### <a name="user-name-and-password"></a>ユーザー名とパスワード

ユーザーは、ユーザー名とパスワードを提供することにより、VPN サーバーに対して認証を行います。
