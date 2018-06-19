---
title: Android を実行するデバイス用の Microsoft Intune の VPN 設定
titlesuffix: ''
description: Android を実行するデバイスでの VPN 接続の構成に使用できる Intune 設定について説明します
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/2/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6753e0232548d862b46a273f1be0105ad7f16d63
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31831947"
---
# <a name="configure-vpn-settings-in-microsoft-intune-for-devices-running-android"></a>Android を実行するデバイス用の Microsoft Intune で VPN 設定を構成する 

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

この記事では、Android を実行するデバイスでの VPN 接続の構成に使用できる Intune 設定を示します。


次のプラットフォーム用に VPN 設定を構成できます。

- [Android](#android-vpn-settings)
- [Android for Work](#android-for-work-vpn-settings)

選択した設定によっては、次の一部の値を構成できない場合があります。

## <a name="android-vpn-settings"></a>Android の VPN 設定
**[接続名]** - この接続の名前を入力します。 エンド ユーザーがデバイスで利用可能な VPN 接続の一覧を参照するときに、この名前が表示されます。
- **[IP アドレスまたは FQDN]** - デバイスが接続する VPN サーバーの IP アドレスまたは完全修飾ドメイン名を指定します。 例: **192.168.1.1**、**vpn.contoso.com**。
- **[認証方法]** - VPN サーバーに対するデバイスの認証方法として、以下のいずれかを選択します。
    - **[証明書]** - 接続を認証するために事前に作成した SCEP または PKCS 証明書プロファイルを選択します。 証明書プロファイルの詳細については、[証明書の構成方法](certificates-configure.md)に関するページを参照してください。
    - **[ユーザー名とパスワード]** - エンド ユーザーは VPN サーバーにログインするためにユーザー名とパスワードを入力する必要があります。
- **[接続の種類]** - 以下のベンダーの一覧から VPN 接続の種類を選択します。
    - **Check Point Capsule VPN**
    - **Cisco AnyConnect**
    - **SonicWall Mobile Connect**
    - **F5 Edge Client**
    - **Pulse Secure**
    - **Citrix**

- **[指紋]** (Check Point Capsule VPN のみ) - 信頼できる VPN サーバーであることを確認するために使用される文字列 (たとえば、"Contoso 指紋コード") を指定します。 指紋をクライアントに送信することにより、クライアントは、接続するときに同じ指紋を示すすべてのサーバーを信頼します。 デバイスにまだ指紋がない場合、接続先の VPN サーバーを信頼するように促すメッセージと共にその指紋が表示されます (ユーザーは手動で指紋を検証し、接続先を信頼することを選択する必要があります)。
- **[Citrix VPN 属性に対してキーと値を入力します]** (Citrix のみ) - VPN 接続のプロパティを構成するために、Citrix から提供されたキーと値のペアを入力します。

## <a name="android-for-work-vpn-settings"></a>Android for Work の VPN 設定

**[接続名]** - この接続の名前を入力します。 エンド ユーザーがデバイスで利用可能な VPN 接続の一覧を参照するときに、この名前が表示されます。
- **[IP アドレスまたは FQDN]** - デバイスが接続する VPN サーバーの IP アドレスまたは完全修飾ドメイン名を指定します。 例: **192.168.1.1**、**vpn.contoso.com**。
- **[認証方法]** - VPN サーバーに対するデバイスの認証方法として、以下のいずれかを選択します。
    - **[証明書]** - 接続を認証するために事前に作成した SCEP または PKCS 証明書プロファイルを選択します。 証明書プロファイルの詳細については、[証明書の構成方法](certificates-configure.md)に関するページを参照してください。
    - **[ユーザー名とパスワード]** - エンド ユーザーは VPN サーバーにログインするためにユーザー名とパスワードを入力する必要があります。
- **[接続の種類]** - 以下のベンダーの一覧から VPN 接続の種類を選択します。
    - **Check Point Capsule VPN**
    - **Cisco AnyConnect**
    - **SonicWall Mobile Connect**
    - **F5 Edge Client**
    - **Pulse Secure**

