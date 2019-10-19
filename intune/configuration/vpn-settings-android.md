---
title: Microsoft Intune で Android デバイス向けの VPN 設定を使用する - Azure | Microsoft Docs
description: Microsoft Intune で Android デバイスに VPN 接続を作成するには、すべての設定を参照してください。 VPN サーバーの接続名、IP アドレス、または FQDN を入力し、ユーザーの認証方法を選択して、Citrix、SonicWall、Check Point カプセル、および Pulse Secure 接続の種類を選択します。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/06/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8d9fefc2413e2dafbf5d0ad67ea15f5f8406cc1c
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72506548"
---
# <a name="android-device-settings-to-configure-vpn-in-intune"></a>Intune で VPN を構成するための Android デバイス設定

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

この記事では、Android デバイスで制御できるさまざまな VPN 接続の設定の一覧を示して説明します。 モバイルデバイス管理 (MDM) ソリューションの一部として、これらの設定を使用して VPN 接続を作成し、VPN の認証方法を選択し、VPN サーバーの種類を選択します。

Intune サービス管理者は、Android デバイスに対して VPN 設定を作成し、割り当てることができます。 

Intune での VPN プロファイルの詳細については、 [vpn プロファイル](vpn-settings-configure.md)に関するページを参照してください。

## <a name="before-you-begin"></a>始める前に

[デバイス構成プロファイルを作成](vpn-settings-configure.md#create-a-device-profile)し、 **[Android]** を選択します。

## <a name="base-vpn"></a>ベース VPN

- **[接続名]** : この接続の名前を入力します。 エンド ユーザーがデバイスで利用可能な VPN 接続を参照するときに、この名前が表示されます。 たとえば、「`Contoso VPN`」と入力します。
- **[IP アドレスまたは FQDN]** : デバイスが接続する VPN サーバーの IP アドレスまたは完全修飾ドメイン名 (FQDN) を入力します。 たとえば、「**192.168.1.1**」や「**vpn.contoso.com**」などと入力します。

  - **[認証方法]** : VPN サーバーに対するデバイスの認証方法として、以下のいずれかを選択します。 次のようなオプションがあります。

    - **[証明書]** : 接続を認証するための既存の SCEP または PKCS 証明書プロファイルを選択します。 証明書プロファイルを作成する手順については、[証明書の構成](../protect/certificates-configure.md)に関するページを参照してください。
    - **[ユーザー名とパスワード]** : VPN サーバーにサインインするときに、エンド ユーザーはユーザー名とパスワードの入力を求められます。

- **[接続の種類]** : VPN 接続の種類を選択します。 次のようなオプションがあります。

  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**
  - **SonicWall Mobile Connect**
  - **F5 Access**
  - **Pulse Secure**
  - **Citrix SSO**

- **[指紋]** (Check Point Capsule VPN のみ): 信頼できる VPN サーバーであることを確認するために文字列 (たとえば、「**Contoso 指紋コード**」) を入力します。 指紋がクライアントに送信されるので、クライアントは、同じフィンガープリントを持つすべてのサーバーを信頼することを認識します。 デバイスに指紋が設定されていない場合、デバイスは指紋を表示すると共に、VPN サーバーを信頼するようにユーザーを促します ユーザーは手動で指紋を検証し、[信頼する] を選択して接続します。
- **[Citrix VPN 属性に対してキーと値を入力します]** (Citrix のみ): Citrix から提供されたキーと値のペアを入力します。 これらの値で、VPN 接続のプロパティを構成します。 

  また、キーと値のペアを含むコンマ区切り値ファイル (.csv) を**インポート**することもできます。 **[マイデータ**] のヘッダーと**キー**のプロパティを確認してください。

  キーと値のペアを追加した後、 **Export**を使用してデータを .csv ファイルにバックアップします。

## <a name="next-steps"></a>次の手順

[プロファイルを割り当て](device-profile-assign.md)、[その状態を監視](device-profile-monitor.md)します。

[Android Enterprise](vpn-settings-android-enterprise.md)、 [iOS](vpn-settings-ios.md)、 [macOS](vpn-settings-macos.md)、 [Windows 10 以降](vpn-settings-windows-10.md)、 [Windows 8.1](vpn-settings-windows-8-1.md)、 [Windows Phone 8.1](vpn-settings-windows-phone-8-1.md)デバイス用の VPN プロファイルを作成することもできます。
