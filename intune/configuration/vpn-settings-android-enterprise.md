---
title: Microsoft Intune で Android Enterprise 向けの VPN 設定を使用する - Azure | Microsoft Docs
description: Microsoft Intune で Android エンタープライズ デバイスに対して VPN 接続を作成するためのすべての設定を確認します。 VPN サーバーの接続名、IP アドレス、または FQDN を入力し、ユーザーの認証方法を選択して、Citrix、SonicWall、Check Point Capsule、および Pulse Secure の接続の種類を選択します。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 81300651355e52f438ea2a314eeb1d0d48e3fcbc
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/20/2020
ms.locfileid: "77510866"
---
# <a name="android-enterprise-device-settings-to-configure-vpn-in-intune"></a>Intune で VPN を構成するための Android エンタープライズ デバイスの設定

この記事では、Android Enterprise で制御できるさまざまな VPN 接続の設定の一覧を示して説明します。 モバイル デバイス管理 (MDM) ソリューションの一環として、これらの設定を使用し、VPN 接続の作成、VPN の認証方法の選択、VPN サーバーの種類の選択などを行います。

Intune 管理者は、Android Enterprise デバイスに対して VPN 設定を作成し、割り当てることができます。 

Intune での VPN プロファイルの詳細については、[VPN プロファイル](vpn-settings-configure.md)に関する記事をご覧ください。

> [!NOTE]
> Always-On VPN を構成するには、VPN プロファイルを作成するだけでなく、Always-On VPN 設定を構成した[デバイスの制限](device-restrictions-android-for-work.md#connectivity)プロファイルを作成する必要もあります。

## <a name="before-you-begin"></a>始める前に

[デバイス構成プロファイルを作成](vpn-settings-configure.md#create-a-device-profile)し、 **[Android Enterprise]** を選択します。

## <a name="device-owner-only"></a>デバイスの所有者のみ

- **[接続名]** :この接続の名前を入力します。 エンド ユーザーがデバイスで利用可能な VPN 接続を参照するときに、この名前が表示されます。 たとえば、「`Contoso VPN`」と入力します。
- **[IP アドレスまたは FQDN]** :デバイスが接続する VPN サーバーの IP アドレスまたは完全修飾ドメイン名 (FQDN) を入力します。 たとえば、「**192.168.1.1**」や「**vpn.contoso.com**」などと入力します。

  - **[認証方法]** :VPN サーバーに対するデバイスの認証方法として、以下のいずれかを選択します。 次のようなオプションがあります。
  
    - **証明書**:接続を認証するための既存の SCEP または PKCS 証明書プロファイルを選択します。 証明書プロファイルを作成する手順については、[証明書の構成](../protect/certificates-configure.md)に関するページを参照してください。
    - **[ユーザー名とパスワード]** :VPN サーバーにサインインするときに、エンド ユーザーはユーザー名とパスワードの入力を求められます。

- **接続の種類**:VPN 接続の種類を選択します。 次のようなオプションがあります。

  - **Cisco AnyConnect**
  - **F5 Access**
  - **Pulse Secure**

## <a name="work-profile-only"></a>仕事用プロファイルのみ

- **[接続名]** :この接続の名前を入力します。 エンド ユーザーがデバイスで利用可能な VPN 接続を参照するときに、この名前が表示されます。 たとえば、「`Contoso VPN`」と入力します。
- **[IP アドレスまたは FQDN]** :デバイスが接続する VPN サーバーの IP アドレスまたは完全修飾ドメイン名 (FQDN) を入力します。 たとえば、「**192.168.1.1**」や「**vpn.contoso.com**」などと入力します。

  - **[認証方法]** :VPN サーバーに対するデバイスの認証方法として、以下のいずれかを選択します。 次のようなオプションがあります。
  
    - **証明書**:接続を認証するための既存の SCEP または PKCS 証明書プロファイルを選択します。 証明書プロファイルを作成する手順については、[証明書の構成](../protect/certificates-configure.md)に関するページを参照してください。
    - **[ユーザー名とパスワード]** :VPN サーバーにサインインするときに、エンド ユーザーはユーザー名とパスワードの入力を求められます。

- **接続の種類**:VPN 接続の種類を選択します。 次のようなオプションがあります。

  - **Cisco AnyConnect**
  - **F5 Access**
  - **Pulse Secure**
  - **SonicWall Mobile Connect**
  - **Check Point Capsule VPN**

## <a name="next-steps"></a>次のステップ

[プロファイルを割り当て](device-profile-assign.md)、[その状態を監視](device-profile-monitor.md)します。

また、[Android](vpn-settings-android.md)、[iOS/iPadOS](vpn-settings-ios.md)、[macOS](vpn-settings-macos.md)、[Windows 10 以降](vpn-settings-windows-10.md)、[Windows 8.1](vpn-settings-windows-8-1.md)、および [Windows Phone 8.1](vpn-settings-windows-phone-8-1.md) デバイス用の VPN プロファイルを作成することもできます。
