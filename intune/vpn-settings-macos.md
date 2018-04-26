---
title: macOS デバイス用の Microsoft Intune VPN 設定
titlesuffix: ''
description: macOS デバイスでの VPN 接続の構成に使用できる Intune 設定について説明します。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d1224c00a1f7e8cf303304b3a0f038ade79b9633
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="configure-vpn-settings-in-microsoft-intune-for-devices-running-macos"></a>macOS を実行するデバイス用に Microsoft Intune で VPN 設定を構成する

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

この記事では、macOS を実行するデバイスでの VPN 接続の構成に使用できる Intune 設定を示します。

選択した設定によっては、次の一覧に記載されている値の一部を構成できない場合があります。

## <a name="base-vpn-settings"></a>基本 VPN 設定

**[接続名]** - この接続の名前を入力します。 エンド ユーザーがデバイスで利用可能な VPN 接続の一覧を参照するときに、この名前が表示されます。
- **[IP アドレスまたは FQDN]** - デバイスが接続する VPN サーバーの IP アドレスまたは完全修飾ドメイン名を指定します。 例: **192.168.1.1**、**vpn.contoso.com**。
- **[認証方法]** - VPN サーバーに対するデバイスの認証方法として、以下のいずれかを選択します。
    - **[証明書]** - **[認証証明書]** で、接続を認証するために事前に作成した SCEP または PKCS 証明書プロファイルを選択します。 証明書プロファイルの詳細については、[証明書の構成方法](certificates-configure.md)に関するページを参照してください。
    - **[ユーザー名とパスワード]** - エンド ユーザーは VPN サーバーにログインするためにユーザー名とパスワードを入力する必要があります。
- **[接続の種類]** - 以下のベンダーの一覧から VPN 接続の種類を選択します。
    - **Check Point Capsule VPN**
    - **Cisco AnyConnect**
    - **SonicWall Mobile Connect**
    - **F5 Edge Client**
    - **Pulse Secure**
    - **Custom VPN**
- **[分割トンネリング]** -  このオプションを **[有効]** または **[無効]** にします。これにより、トラフィックに応じて使用する接続をデバイスが判断できます。 たとえば、ホテルにいるユーザーは、業務ファイルへのアクセスに VPN 接続を使用しますが、通常の Web 閲覧にはホテルの標準ネットワークを使用します。

<!--- **Per-app VPN** - Select this option if you want to associate this VPN connection with an iOS or macOS app so that the connection will be opened when the app is run. You can associate the VPN profile with an app when you assign the software. For more information, see [How to assign and monitor apps](apps-deploy.md). --->

## <a name="custom-vpn-settings"></a>カスタム VPN 設定

**[カスタム VPN]** を選択した場合は、以下の追加設定を構成します。

- **[VPN 識別子]** - これは使用している VPN アプリの識別子であり、VPN プロバイダーから提供されます。
- **[カスタム VPN 属性に対してキーと値を入力します]** - VPN 接続をカスタマイズする**キー**と**値**を追加またはインポートします。 これらの値も、通常は VPN プロバイダーから提供されます。


## <a name="proxy-settings"></a>プロキシの設定

- **[自動構成スクリプト]** - ファイルを使用してプロキシ サーバーを構成します。 構成ファイルが格納されている**プロキシ サーバーの URL** を入力します (例: **http://proxy.contoso.com**)。
- **[アドレス]** - プロキシ サーバーのアドレスを (IP アドレスとして) 入力します。
- **[ポート番号]** - プロキシ サーバーに関連付けられているポート番号を入力します。
