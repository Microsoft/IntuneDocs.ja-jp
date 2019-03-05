---
title: Microsoft Intune で Android デバイス向けの VPN 設定を構成する - Azure | Microsoft Docs
description: Android および Android for Work デバイス用の VPN 構成プロファイルを作成する場合は、接続名、VPN サーバーの IP アドレスまたは FQDN を入力し、ユーザーが VPN サーバーの認証を受ける方法を選択してから、Citrix、SonicWall、Check Point Capsule、Pulse Secure、Microsoft Edge の接続の種類を選択します。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: aff0aad055aee08dfbf17622e3d9f9c3061165b8
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/02/2019
ms.locfileid: "57233969"
---
# <a name="configure-vpn-settings-for-devices-running-android-in-intune"></a>Intune で Android を実行するデバイスの VPN 設定を構成する

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

この記事では、Android を実行するデバイスでの VPN 接続の構成に使用できる Intune 設定を示します。

次のプラットフォーム用に VPN 設定を構成できます。

- [Android](#android-vpn-settings)
- [Android エンタープライズ](#android-enterprise-vpn-settings)

選択した設定によっては、次の一部の値を構成できない場合があります。

## <a name="android-vpn-settings"></a>Android の VPN 設定

- **[接続名]**:この接続の名前を入力します。 エンド ユーザーがデバイスで利用可能な VPN 接続を参照するときに、この名前が表示されます。
- **[IP アドレスまたは FQDN]**:デバイスが接続する VPN サーバーの IP アドレスまたは完全修飾ドメイン名 (FQDN) を入力します。 たとえば、「**192.168.1.1**」や「**vpn.contoso.com**」などと入力します。

  - **[認証方法]**:VPN サーバーに対するデバイスの認証方法として、以下のいずれかを選択します。 次のようなオプションがあります。

    - **[証明書]**:接続を認証するための既存の SCEP または PKCS 証明書プロファイルを選択します。 証明書プロファイルを作成する手順については、[証明書の構成](certificates-configure.md)に関するページを参照してください。
    - **[ユーザー名とパスワード]**:VPN サーバーにサインインするときに、エンド ユーザーはユーザー名とパスワードの入力を求められます。

- **接続の種類**:VPN 接続の種類を選択します。 次のようなオプションがあります。

  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**
  - **SonicWall Mobile Connect**
  - **F5 Edge Client**
  - **Pulse Secure**
  - **Citrix**

- **[指紋]** (Check Point Capsule VPN のみ):信頼できる VPN サーバーであることを確認するために文字列 (たとえば、「**Contoso 指紋コード**」) を入力します。 指紋をクライアントに送信することにより、クライアントは、接続するときに同じ指紋を示すすべてのサーバーを信頼します。 デバイスに指紋が設定されていない場合、デバイスは指紋を表示すると共に、VPN サーバーを信頼するようにユーザーを促します ユーザーは手動で指紋を検証し、[信頼する] を選択して接続します。
- **[Citrix VPN 属性に対してキーと値を入力します]** (Citrix のみ):Citrix から提供されたキーと値のペアを入力します。 これらの値で、VPN 接続のプロパティを構成します。

## <a name="android-enterprise-vpn-settings"></a>Android エンタープライズの VPN の設定

- **[接続名]**:この接続の名前を入力します。 エンド ユーザーがデバイスで利用可能な VPN 接続を参照するときに、この名前が表示されます。
- **[IP アドレスまたは FQDN]**:デバイスが接続する VPN サーバーの IP アドレスまたは完全修飾ドメイン名 (FQDN) を入力します。 たとえば、「**192.168.1.1**」や「**vpn.contoso.com**」などと入力します。

  - **[認証方法]**:VPN サーバーに対するデバイスの認証方法として、以下のいずれかを選択します。 次のようなオプションがあります。
  
    - **[証明書]**:接続を認証するための既存の SCEP または PKCS 証明書プロファイルを選択します。 証明書プロファイルを作成する手順については、[証明書の構成](certificates-configure.md)に関するページを参照してください。
    - **[ユーザー名とパスワード]**:VPN サーバーにサインインするときに、エンド ユーザーはユーザー名とパスワードの入力を求められます。

- **接続の種類**:VPN 接続の種類を選択します。 次のようなオプションがあります。

  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**
  - **SonicWall Mobile Connect**
  - **F5 Access**
  - **Pulse Secure**

## <a name="next-steps"></a>次の手順
[Intune の VPN プロファイル](vpn-settings-configure.md)
