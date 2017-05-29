---
title: "Windows Phone 8.1 デバイス向けの Intune VPN 設定"
titleSuffix: Intune Azure preview
description: "Intune Azure プレビュー: Windows Phone 8.1 デバイスで VPN 接続を構成するために使用できる Intune 設定について説明します。"
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c1a9053f-02a7-4735-bc0d-fe4573b31ed4
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: bd6d6debcf2f62599518aec7b6998ecf29c3dd6a
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017


---

# <a name="vpn-settings-for-windows-phone-81-devices-in-microsoft-intune"></a>Microsoft Intune での Windows Phone 8.1 デバイス向けの VPN 設定

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

選択する設定によっては、以下の一覧に記載されている値の一部を構成できない場合もあります。

## <a name="base-vpn-settings"></a>基本 VPN 設定

- **[Apply all settings to Windows Phone 8.1 only (すべての設定を Windows Phone 8.1 のみに適用する)]** - これは、クラシック Intune ポータルで構成できる設定です。 Azure Portal では、この設定は変更できません。 これを **[構成済み]** に設定すると、すべての設定が Windows Phone 8.1 デバイスのみに適用されるようになります。 **[未構成]** に設定されている場合、これらの設定は Windows 10 Mobile デバイスにも適用されます。
- **[接続名]** - この接続の名前を入力します。 エンド ユーザーがデバイスで利用可能な VPN 接続の一覧を参照するときに、この名前が表示されます。
- **[認証方法]** - VPN サーバーに対するデバイスの認証方法として、以下のいずれかを選択します。
    - **[証明書]** - **[認証証明書]** で、接続を認証するために事前に作成した SCEP または PKCS 証明書プロファイルを選択します。 証明書プロファイルの詳細については、[証明書の構成方法](certificates-configure.md)に関するページを参照してください。
    - **[ユーザー名とパスワード]** - エンド ユーザーは VPN サーバーにログインするためにユーザー名とパスワードを入力する必要があります。
- **[サーバー]** - デバイスの接続先とする 1 台以上の VPN サーバーを追加します。
    - **[追加]** - **[行の追加]** ブレードが開き、以下の情報を指定できます。
        - **[説明]** - **Contoso VPN サーバー**のような、サーバーを表す名前を指定します。
        - **[IP アドレスまたは FQDN]** - デバイスが接続する VPN サーバーの IP アドレスまたは完全修飾ドメイン名を指定します。 例: **192.168.1.1**、**vpn.contoso.com**。
        - **[既定のサーバー]** - このサーバーを、デバイスで接続を確立するために使用する既定のサーバーとして有効にします。 既定のサーバーとして設定するサーバーの数は 1 台のみにしてください。
    - **[インポート]** - 説明、IP アドレスまたは FQDN、既定のサーバーという形式でまとめられた、コンマ区切りのサーバーのリストを含むファイルを参照します。 **[OK]** を選択すると、これらが **[サーバー]** リストにインポートされます。
    - **[エクスポート]** - サーバーのリストをコンマ区切り値 (csv) ファイルにエクスポートします。

- **[会社の Wi-Fi ネットワークでは VPN を使用しない]** - デバイスが会社の Wi-Fi ネットワークに接続されている場合に VPN 接続を使用しないように指定するには、このオプションを有効にします。
- **[自宅の Wi-Fi ネットワークでは VPN を使用しない]** - デバイスが自宅の Wi-Fi ネットワークに接続されている場合に VPN 接続を使用しないように指定するには、このオプションを有効にします。

- **[接続の種類]** - 以下のベンダーの一覧から VPN 接続の種類を選択します。
    - **Check Point Capsule VPN**
    - **Dell SonicWALL Mobile Connect**
    - **F5 Edge Client**
    - **Pulse Secure**

- **[ログイン グループまたはドメイン]** (Dell SonicWALL Mobile Connect のみ) - 接続先のログイン グループまたはドメインの名前を指定します。
- **[ロール]** (Pulse Secure のみ) - この接続に対するアクセス権を持つユーザー ロールの名前を指定します。 ユーザー ロールを使用して、個人の設定とオプションを定義し、特定のアクセス機能を有効または無効にします。
- **[領域]** (Pulse Secure のみ) - 使用する認証領域の名前を指定します。 認証領域とは、接続の種類が [Pulse Secure] の場合に使用される認証リソースのグループを表します。

- **[DNS サフィックス検索一覧]** - 1 つ以上の DNS サフィックスを**追加**します。 短い名前を使用して Web サイトに接続するときに、指定した各 DNS サフィックスが検索されます。 たとえば、**domain1.contoso.com** と **domain2.contoso.com** の DNS サフィックスを指定して URL **http://mywebsite** にアクセスすると、URL **http://mywebsite.domain1.contoso.com** と **http://mywebsite.domain2.contoso.com** が検索されます。

- **[カスタム XML]** - VPN 接続を構成する任意のカスタム XML コマンドを指定します。

    **Pulse Secure の例:**

```
    <pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>

```

**CheckPoint Mobile VPN の例:**

```
    <CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />
```

**Dell SonicWALL Mobile Connect の例:**
```
<MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>

```

**F5 Edge Client の例:**
```
    <f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>

```

カスタムの XML コマンドの記述方法については、各製造元の VPN に関するマニュアルを参照してください。

- **[分割トンネリング]** - このオプションを **[有効]** または **[無効]** にします。これを有効にすると、使用する接続をトラフィックに応じてデバイスが判断するようになります。 たとえば、ホテルにいるユーザーは、業務ファイルへのアクセスに VPN 接続を使用しますが、通常の Web 閲覧にはホテルの標準ネットワークを使用します。




## <a name="proxy-settings"></a>プロキシの設定

- **[自動的にプロキシ設定を検出する]** - VPN サーバーが接続にプロキシ サーバーを必要とする場合は、デバイスで接続の設定を自動的に検出するかどうかを指定します。 詳細については、Windows Server のマニュアルを参照してください。
- **[自動構成スクリプト]** - ファイルを使用してプロキシ サーバーを構成します。 構成ファイルが格納されている**プロキシ サーバーの URL** を入力します (たとえば、**http://proxy.contoso.com**)。
- **[プロキシ サーバーを使用する]** - プロキシ サーバーの設定を手動で入力する場合は、このオプションを有効にします。
    - **[アドレス]** - プロキシ サーバーのアドレスを (IP アドレスとして) 入力します。
    - **[ポート番号]** - プロキシ サーバーに関連付けられているポート番号を入力します。
- **[ローカル アドレスにはプロキシ サーバーを使用しない]** - VPN サーバーが接続にプロキシ サーバーを必要とする場合、指定したローカル アドレスに対してプロキシ サーバーを使用しないようにするには、このオプションを選択します。 詳細については、Windows Server のマニュアルを参照してください。

