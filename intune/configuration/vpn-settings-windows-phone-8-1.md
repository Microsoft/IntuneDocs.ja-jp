---
title: Windows Phone 8.1 デバイス用の Microsoft Intune の VPN 設定
titleSuffix: ''
description: Windows Phone 8.1 を実行するデバイスでの VPN 接続の構成に使用できる Intune 設定について説明します。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 69de660e65ed2a0f3b6c9c7e4ce774a6fcde2676
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "72506508"
---
# <a name="configure-vpn-settings-in-microsoft-intune-for-devices-running-windows-phone-81"></a>Windows Phone 8.1 を実行するデバイス用に Microsoft Intune で VPN 設定を構成する

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

この記事では、Windows Phone 8.1 を実行するデバイスでの VPN 接続の構成に使用できる Intune 設定を示します。


選択した設定によっては、次の一覧に記載されている値の一部を構成できない場合があります。

## <a name="base-vpn-settings"></a>基本 VPN 設定

- **[Apply all settings to Windows Phone 8.1 only (すべての設定を Windows Phone 8.1 のみに適用する)]** - これは、Intune クラシック ポータルで構成できる設定です。 Azure Portal では、この設定は変更できません。 これが **[構成済み]** に設定されている場合は、すべての設定が Windows Phone 8.1 デバイスのみに適用されます。 **[未構成]** に設定されている場合、これらの設定は Windows 10 Mobile デバイスにも適用されます。
- **[接続名]** - この接続の名前を入力します。 ユーザーがデバイスで使用可能な VPN 接続の一覧を参照するときに、この名前が表示されます。
- **[認証方法]** - VPN サーバーに対するデバイスの認証方法として、以下のいずれかを選択します。
  - **[証明書]** - **[認証証明書]** で、接続を認証するために事前に作成した SCEP または PKCS 証明書プロファイルを選択します。 証明書プロファイルの詳細については、[証明書の構成方法](../protect/certificates-configure.md)に関するページを参照してください。
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
  - **SonicWall Mobile Connect**
  - **F5 Edge Client**
  - **Pulse Secure**

- **[ログイン グループまたはドメイン]** (SonicWall Mobile Connect のみ) - 接続先のログイン グループまたはドメインの名前を指定します。
- **[ロール]** (Pulse Secure のみ) - この接続に対するアクセス権を持つユーザー ロールの名前を指定します。 ユーザー ロールを使用して、個人の設定とオプションを定義し、特定のアクセス機能を有効または無効にします。
- **[領域]** (Pulse Secure のみ) - 使用する認証領域の名前を指定します。 認証領域とは、接続の種類が [Pulse Secure] の場合に使用される認証リソースのグループを表します。

- **[DNS サフィックス検索一覧]**  - 1 つ以上の DNS サフィックスを**追加**します。 短い名前を使用して Web サイトに接続するときに、指定した各 DNS サフィックスが検索されます。 たとえば、**domain1.contoso.com** と **domain2.contoso.com** の DNS サフィックスを指定して、URL `http://mywebsite` にアクセスします。この場合、URL `http://mywebsite.domain1.contoso.com` および `http://mywebsite.domain2.contoso.com` が検索されます。

- **[カスタム XML]** - VPN 接続を構成する任意のカスタム XML コマンドを指定します。

    **Pulse Secure の例:**

```xml
    <pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>
```

**CheckPoint Mobile VPN の例:**

```xml
    <CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />
```

**SonicWall Mobile Connect の例:**

```xml
<MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>
```

**F5 Edge Client の例:**

```xml
    <f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>
```

カスタムの XML コマンドの記述方法については、各製造元の VPN に関するマニュアルを参照してください。

- **[分割トンネリング]**  -  このオプションを **[有効]** または **[無効]** にします。これにより、トラフィックに応じて使用する接続をデバイスが判断できます。 たとえば、ホテルにいるユーザーは、業務ファイルへのアクセスに VPN 接続を使用しますが、通常の Web 閲覧にはホテルの標準ネットワークを使用します。




## <a name="proxy-settings"></a>プロキシの設定

- **[自動的にプロキシ設定を検出する]** - VPN サーバーが接続にプロキシ サーバーを必要とする場合は、デバイスで接続の設定を自動的に検出するかどうかを指定します。 詳細については、Windows Server のマニュアルを参照してください。
- **[自動構成スクリプト]** - ファイルを使用してプロキシ サーバーを構成します。 構成ファイルが格納されている**プロキシ サーバーの URL** を入力します (例: `http://proxy.contoso.com`)。
- **[プロキシ サーバーを使用する]** - プロキシ サーバーの設定を手動で入力する場合は、このオプションを有効にします。
  - **[アドレス]** - プロキシ サーバーのアドレスを (IP アドレスとして) 入力します。
  - **[ポート番号]** - プロキシ サーバーに関連付けられているポート番号を入力します。
- **[ローカル アドレスにはプロキシ サーバーを使用しない]** - VPN サーバーが接続にプロキシ サーバーを必要とする場合、指定したローカル アドレスに対してプロキシ サーバーを使用しないようにするには、このオプションを選択します。 詳細については、Windows Server のマニュアルを参照してください。
