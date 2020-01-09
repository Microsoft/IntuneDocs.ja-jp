---
title: Microsoft Intune デバイスに VPN 設定を追加する - Azure | Microsoft Docs
description: Android、Android Enterprise、iOS、macOS、および Windows デバイスでは、組み込みの設定を使用して Microsoft Intune で仮想プライベートネットワーク (VPN) 接続を作成します。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b11cbd3427b3b8e0a43a6e6e2af5fa80da45e16a
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2019
ms.locfileid: "75206280"
---
# <a name="create-vpn-profiles-to-connect-to-vpn-servers-in-intune"></a>Intune で VPN サーバーに接続するための VPN プロファイルを作成する



仮想プライベート ネットワーク (VPN) を使用すると、組織のユーザーが組織のネットワークにリモート アクセスする際にセキュリティで保護することができます。 デバイスでは、VPN 接続プロファイルを使用して VPN サーバーとの接続が開始されます。 Microsoft Intune の **VPN プロファイル**によって組織内のユーザーとデバイスに VPN 設定を割り当て、組織のネットワークに簡単かつ安全に接続できるようにします。

たとえば、組織のネットワーク上のファイル共有に接続するために必要な設定をすべての iOS デバイスに構成したいとします。 これらの設定を含む VPN プロファイルを作成します。 その後、iOS デバイスを持っているすべてのユーザーにこのプロファイルを割り当てます。 使用できるネットワークの一覧に VPN 接続が表示されるので、ユーザーは最小限の労力で接続できます。

> [!NOTE]
> [Intune のカスタム構成ポリシー](custom-settings-configure.md)を使用して、次のプラットフォーム用の VPN プロファイルを作成できます。
>
> * Android 4 以降
> * Windows 8.1 以降を実行する登録済みのデバイス
> * Windows Phone 8.1 以降
> * Windows 10 デスクトップを実行する登録済みのデバイス
> * Windows 10 Mobile
> * Windows Holographic for Business

## <a name="vpn-connection-types"></a>VPN 接続の種類

次の接続の種類を使用して、VPN プロファイルを作成できます。

|接続の種類|プラットフォーム|
|-|-|
|自動|Windows 10|
|Check Point Capsule VPN|- Android<br/>- Android エンタープライズ仕事用プロファイル<br/>- iOS<br/>- macOS<br/>- Windows 10<br/>- Windows 8.1<br/>- Windows Phone 8.1|
|Cisco AnyConnect|- Android<br/>- Android エンタープライズ仕事用プロファイル<br/>- Android エンタープライズ デバイス所有者 (フル マネージド)<br/>- iOS<br/>- macOS|
|Cisco (IPSec)|iOS|
|Citrix SSO|- Android<br/>- Android エンタープライズ仕事用プロファイル:[アプリ構成ポリシー](../apps/app-configuration-policies-use-android.md)を使用する<br/>- Android エンタープライズ デバイス所有者 (フル マネージド):[アプリ構成ポリシー](../apps/app-configuration-policies-use-android.md)を使用する<br/>- iOS<br/>- Windows 10|
|カスタム VPN|- iOS<br/>- macOS|
|F5 Access|- Android<br/>- Android エンタープライズ仕事用プロファイル<br/>- Android エンタープライズ デバイス所有者 (フル マネージド)<br/>- iOS<br/>- macOS<br/>- Windows 10<br/>- Windows 8.1<br/>- Windows Phone 8.1|
|IKEv2| - iOS<br/>- Windows 10|
|L2TP|Windows 10|
|Palo Alto Networks GlobalProtect|- Android エンタープライズ仕事用プロファイル:[アプリ構成ポリシー](../apps/app-configuration-policies-use-android.md)を使用する<br/>- iOS<br/>- Windows 10|
|PPTP|Windows 10|
|Pulse Secure|- Android<br/>- Android エンタープライズ仕事用プロファイル<br/>- Android エンタープライズ デバイス所有者 (フル マネージド)<br/>- iOS<br/>- macOS<br/>- Windows 10<br/>- Windows 8.1<br/>- Windows Phone 8.1|
|SonicWall Mobile Connect|- Android<br/>- Android エンタープライズ仕事用プロファイル<br/>- iOS<br/>- macOS<br/>- Windows 10<br/>- Windows 8.1<br/>- Windows Phone 8.1|
|Zscaler|- Android エンタープライズ仕事用プロファイル:[アプリ構成ポリシー](../apps/app-configuration-policies-use-android.md)を使用する<br/>- iOS|

> [!IMPORTANT]
> デバイスに割り当てられた VPN プロファイルを使用する前に、プロファイル用の該当する VPN アプリをインストールする必要があります。 [Microsoft Intune でのアプリ管理の概要](../apps/app-management.md)に関する記事の情報を参考にして、Intune を使ってアプリを割り当ててください。  

URI の設定を使ってカスタム VPN プロファイルを作成する方法については、[カスタム VPN プロファイルの作成](custom-settings-configure.md)に関するページをご覧ください。

## <a name="create-a-device-profile"></a>デバイス プロファイルの作成

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。
2. **[デバイス]** 、 **[構成プロファイル]** 、 **[プロファイルの作成]** の順に選択します。
3. 次のプロパティを入力します。

    - **名前**:プロファイルのわかりやすい名前を入力します。 後で簡単に識別できるよう、プロファイルに名前を付けます。 たとえば、「**会社全体の VPN プロファイル**」は適切なプロファイル名です。
    - **説明**:プロファイルの説明を入力します。 この設定は省略可能ですが、推奨されます。
    - **[プラットフォーム]** :デバイスのプラットフォームを選択します。 次のようなオプションがあります。

      - **Android**
      - **[Android エンタープライズ]**  >  **[デバイスの所有者のみ]**
      - **[Android エンタープライズ]**  >  **[仕事用プロファイルのみ]**
      - **iOS/iPadOS**
      - **macOS**
      - **Windows Phone 8.1**
      - **Windows 8.1 以降**
      - **Windows 10 以降**

    - **[プロファイルの種類]** : **[VPN]** を選択します。

4. 選択したプラットフォームによって構成できる設定が異なります。 各プラットフォームの詳細な設定については、次の記事を参照してください。

    - [Android の設定](vpn-settings-android.md)
    - [Android エンタープライズの設定](vpn-settings-android-enterprise.md)
    - [iOS/iPadOS の設定](vpn-settings-ios.md)
    - [macOS の設定](vpn-settings-macos.md)
    - [Windows Phone 8.1 の設定](vpn-settings-windows-phone-8-1.md)
    - [Windows 8.1 の設定](vpn-settings-windows-8-1.md)
    - [Windows 10 の設定](vpn-settings-windows-10.md) (Windows Holographic for Business を含む)

5. 完了したら、 **[OK]**  >  **[作成]** を選択して変更を保存します。

プロファイルが作成され、プロファイル一覧に表示されます。 このプロファイルをグループに割り当てる場合は、[デバイス プロファイルの割り当て](device-profile-assign.md)に関するページを参照してください。

## <a name="secure-your-vpn-profiles"></a>VPN プロファイルをセキュリティで保護する

VPN プロファイルは、さまざまな製造元から提供される多くの異なる接続の種類およびプロトコルに対応しています。 これらの接続は、通常、次の方法を通じてセキュリティで保護されます。

### <a name="certificates"></a>証明書

VPN プロファイルを作成するときに、Intune で事前に作成した SCEP または PKCS の証明書プロファイルを選択します。 このプロファイルは ID 証明書と呼ばれます。 ユーザーのデバイスの接続を許可するために作成した信頼済み証明書プロファイル (または、"*ルート証明書*") に対して認証を行うために使用されます。 信頼できる証明書は、VPN 接続を認証するコンピューター (通常は VPN サーバー) に割り当てられます。

Intune で証明書プロファイルを作成および使用する方法の詳細については、[Microsoft Intune で証明書を構成する方法](../protect/certificates-configure.md)に関する記事を参照してください。

### <a name="user-name-and-password"></a>ユーザー名とパスワード

ユーザーは、ユーザー名とパスワードを提供することにより、VPN サーバーに対して認証を行います。

## <a name="next-steps"></a>次のステップ

プロファイルを作成しましたが、まだ何も行っていません。 次に、[デバイスにプロファイルを割り当てます](device-profile-assign.md)。

[Android](android-pulse-secure-per-app-vpn.md) デバイスと [iOS](vpn-setting-configure-per-app.md) デバイスでは、アプリごとの VPN を作成して使用することもできます。
