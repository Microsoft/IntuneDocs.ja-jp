---
title: "Android デバイス向けの Intune VPN 設定"
titlesuffix: Azure portal
description: "Android デバイスでの VPN 接続の構成に使用できる Intune 設定について説明します"
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 06/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 16c056ca-320e-4107-ad03-a0cf96c28885
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 23d898df90313a1a342c5a8898afea55e50dd705
ms.sourcegitcommit: 3b397b1dcb780e2f82a3d8fba693773f1a9fcde1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/12/2017
---
# <a name="vpn-settings-for-android-devices-in-microsoft-intune"></a>Microsoft Intune での Android デバイス向けの VPN 設定

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune 管理者は、次のプラットフォーム向けの VPN 設定を構成できます。

- [Android](#android-vpn-settings)
- [Android for Work](#android-for-work-vpn-settings)

選択する設定によっては、以下の一覧に記載されている値の一部を構成できない場合もあります。

## <a name="android-vpn-settings"></a>Android の VPN 設定
**[接続名]** - この接続の名前を入力します。 エンド ユーザーがデバイスで利用可能な VPN 接続の一覧を参照するときに、この名前が表示されます。
- **[IP アドレスまたは FQDN]** - デバイスが接続する VPN サーバーの IP アドレスまたは完全修飾ドメイン名を指定します。 例: **192.168.1.1**、**vpn.contoso.com**。
- **[認証方法]** - VPN サーバーに対するデバイスの認証方法として、以下のいずれかを選択します。
    - **[証明書]** - 接続を認証するために事前に作成した SCEP または PKCS 証明書プロファイルを選択します。 証明書プロファイルの詳細については、[証明書の構成方法](certificates-configure.md)に関するページを参照してください。
    - **[ユーザー名とパスワード]** - エンド ユーザーは VPN サーバーにログインするためにユーザー名とパスワードを入力する必要があります。
- **[接続の種類]** - 以下のベンダーの一覧から VPN 接続の種類を選択します。
    - **Check Point Capsule VPN**
    - **Cisco AnyConnect**
    - **Dell SonicWALL Mobile Connect**
    - **F5 Edge Client**
    - **Pulse Secure**
    - **Citrix**

- **[指紋]** (Check Point Capsule VPN のみ) - 信頼できる VPN サーバーであることを確認するために使用される文字列を指定します (たとえば、"Contoso 指紋コード")。 指紋をクライアントに送信することにより、クライアントは、接続するときに同じ指紋を示すすべてのサーバーを信頼します。 デバイスにまだ指紋がない場合、接続先の VPN サーバーを信頼するように促すメッセージと共にその指紋が表示されます (ユーザーは手動で指紋を検証し、接続先を信頼することを選択する必要があります)。
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
    - **Dell SonicWALL Mobile Connect**
    - **F5 Edge Client**
    - **Pulse Secure**

- **分割トンネリング** - 他のトラフィックがインターネットを使用しているときに、特定の Web トラフィックが VPN 接続を使用できるようにします。 VPN がアクティブな場合にすべてのトラフィックで VPN を使用するには、この設定を無効にします。
