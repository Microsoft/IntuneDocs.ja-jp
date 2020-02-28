---
title: Microsoft Intune で Android デバイス向けの VPN 設定を使用する - Azure | Microsoft Docs
description: Microsoft Intune で Android デバイスに対して VPN 接続を作成するためのすべての設定を確認します。 VPN サーバーの接続名、IP アドレス、または FQDN を入力し、ユーザーの認証方法を選択して、Citrix、SonicWall、Check Point Capsule、および Pulse Secure の接続の種類を選択します。
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
ms.openlocfilehash: 3f82cc74aa2e351ee63ffba2629e9ddddb57fc76
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/20/2020
ms.locfileid: "77512519"
---
# <a name="android-device-settings-to-configure-vpn-in-intune"></a>Intune で VPN を構成するための Android デバイスの設定

この記事では、Android デバイスで制御できるさまざまな VPN 接続の設定の一覧を示して説明します。 モバイル デバイス管理 (MDM) ソリューションの一環として、これらの設定を使用し、VPN 接続の作成、VPN の認証方法の選択、VPN サーバーの種類の選択などを行います。

Intune サービス管理者は、Android デバイスに対して VPN 設定を作成し、割り当てることができます。 

Intune での VPN プロファイルの詳細については、[VPN プロファイル](vpn-settings-configure.md)に関する記事をご覧ください。

## <a name="before-you-begin"></a>始める前に

[デバイス構成プロファイルを作成](vpn-settings-configure.md#create-a-device-profile)し、 **[Android]** を選択します。

## <a name="base-vpn"></a>基本 VPN

- **[接続名]** :この接続の名前を入力します。 エンド ユーザーがデバイスで利用可能な VPN 接続を参照するときに、この名前が表示されます。 たとえば、「`Contoso VPN`」と入力します。
- **[IP アドレスまたは FQDN]** :デバイスが接続する VPN サーバーの IP アドレスまたは完全修飾ドメイン名 (FQDN) を入力します。 たとえば、「**192.168.1.1**」や「**vpn.contoso.com**」などと入力します。

  - **[認証方法]** :VPN サーバーに対するデバイスの認証方法として、以下のいずれかを選択します。 次のようなオプションがあります。

    - **証明書**:接続を認証するための既存の SCEP または PKCS 証明書プロファイルを選択します。 証明書プロファイルを作成する手順については、[証明書の構成](../protect/certificates-configure.md)に関するページを参照してください。
    - **[ユーザー名とパスワード]** :VPN サーバーにサインインするときに、エンド ユーザーはユーザー名とパスワードの入力を求められます。

- **接続の種類**:VPN 接続の種類を選択します。 次のようなオプションがあります。

  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**
  - **SonicWall Mobile Connect**
  - **F5 Access**
  - **Pulse Secure**
  - **Citrix SSO**

- **[指紋]** (Check Point Capsule VPN のみ):信頼できる VPN サーバーであることを確認するために文字列 (たとえば、「**Contoso 指紋コード**」) を入力します。 指紋がクライアントに送信されるので、クライアントでは同じ指紋を持つすべてのサーバーを信頼することができます。 デバイスに指紋が設定されていない場合、デバイスは指紋を表示すると共に、VPN サーバーを信頼するようにユーザーを促します ユーザーは手動で指紋を検証し、[信頼する] を選択して接続します。
- **[Citrix VPN 属性に対してキーと値を入力します]** (Citrix のみ):Citrix から提供されたキーと値のペアを入力します。 これらの値で、VPN 接続のプロパティを構成します。 

  また、キーと値のペアを含むコンマ区切り値ファイル (.csv) を **[インポート]** することもできます。 **[個人用データにヘッダーがあります]** と **[キー]** プロパティを必ず確認してください。

  キーと値のペアを追加した後、 **[エクスポート]** を使用して、データを .csv ファイルにバックアップします。

## <a name="next-steps"></a>次のステップ

[プロファイルを割り当て](device-profile-assign.md)、[その状態を監視](device-profile-monitor.md)します。

また、[Android エンタープライズ](vpn-settings-android-enterprise.md)、[iOS/iPadOS](vpn-settings-ios.md)、[macOS](vpn-settings-macos.md)、[Windows 10 以降](vpn-settings-windows-10.md)、[Windows 8.1](vpn-settings-windows-8-1.md)、および [Windows Phone 8.1](vpn-settings-windows-phone-8-1.md) デバイス用の VPN プロファイルを作成することもできます。
