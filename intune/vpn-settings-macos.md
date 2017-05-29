---
title: "macOS デバイス向けの Intune VPN 設定 | Microsoft Docs"
titleSuffix: Intune Azure preview
description: "Intune Azure プレビュー: macOS デバイスで VPN 接続を構成するために使用できる Intune 設定について説明します。"
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 05/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d203a70d-37df-4195-85f7-ad5ef14ac2a1
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 4737fc863e3eda92eafd0536a07abf4100ebe9cc
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017


---

# <a name="vpn-settings-for-macos-devices-in-microsoft-intune"></a>Microsoft Intune での macOS デバイス向けの VPN 設定

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

選択する設定によっては、以下の一覧に記載されている値の一部を構成できない場合もあります。

## <a name="base-vpn-settings"></a>**基本 VPN 設定**

**[接続名]** - この接続の名前を入力します。 エンド ユーザーがデバイスで利用可能な VPN 接続の一覧を参照するときに、この名前が表示されます。
- **[IP アドレスまたは FQDN]** - デバイスが接続する VPN サーバーの IP アドレスまたは完全修飾ドメイン名を指定します。 例: **192.168.1.1**、**vpn.contoso.com**。
- **[認証方法]** - VPN サーバーに対するデバイスの認証方法として、以下のいずれかを選択します。
    - **[証明書]** - **[認証証明書]** で、接続を認証するために事前に作成した SCEP または PKCS 証明書プロファイルを選択します。 証明書プロファイルの詳細については、[証明書の構成方法](certificates-configure.md)に関するページを参照してください。
    - **[ユーザー名とパスワード]** - エンド ユーザーは VPN サーバーにログインするためにユーザー名とパスワードを入力する必要があります。
- **[接続の種類]** - 以下のベンダーの一覧から VPN 接続の種類を選択します。
    - **Check Point Capsule VPN**
    - **Cisco AnyConnect**
    - **Dell SonicWALL Mobile Connect**
    - **F5 Edge Client**
    - **Pulse Secure**
    - **Custom VPN**
- **[分割トンネリング]** - このオプションを **[有効]** または **[無効]** にします。これを有効にすると、使用する接続をトラフィックに応じてデバイスが判断するようになります。 たとえば、ホテルにいるユーザーは、業務ファイルへのアクセスに VPN 接続を使用しますが、通常の Web 閲覧にはホテルの標準ネットワークを使用します。

<!--- **Per-app VPN** - Select this option if you want to associate this VPN connection with an iOS or macOS app so that the connection will be opened when the app is run. You can associate the VPN profile with an app when you assign the software. For more information, see [How to assign and monitor apps](apps-deploy.md). --->

## <a name="custom-vpn-settings"></a>カスタム VPN 設定

**[カスタム VPN]** を選択した場合は、以下の追加設定を構成します。

- **[VPN 識別子]** - これは使用している VPN アプリの識別子であり、VPN プロバイダーから提供されます。
- **[カスタム VPN 属性に対してキーと値を入力します]** - VPN 接続をカスタマイズする**キー**と**値**を追加またはインポートします。 これらの値も、通常は VPN プロバイダーから提供されます。


## <a name="proxy-settings"></a>プロキシの設定

- **[自動構成スクリプト]** - ファイルを使用してプロキシ サーバーを構成します。 構成ファイルが格納されている**プロキシ サーバーの URL** を入力します (たとえば、**http://proxy.contoso.com**)。
- **[アドレス]** - プロキシ サーバーのアドレスを (IP アドレスとして) 入力します。
- **[ポート番号]** - プロキシ サーバーに関連付けられているポート番号を入力します。

