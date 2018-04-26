---
title: Microsoft Intune - Azure で VPN 設定を表示する | Microsoft Docs
description: Microsoft Intune で使用可能な VPN 設定、その用途、実行内容について説明します。これには、トラフィック規則、条件付きアクセス、Windows 10 デバイスと Windows Holographic for Business デバイスの DNS、プロキシ設定が含まれます。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/8/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.reviewer: tycast
ms.custom: intune-azure
ms.openlocfilehash: 787501892d0955e3396bc8f37e5da8ba0d312c74
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="read-about-the-vpn-settings-in-intune"></a>Intune の VPN 設定について

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune を使用して VPN 接続を構成することができます。 この記事では、これらの設定、トラフィック規則、条件付きアクセス、DNS とプロキシの設定について説明します。

これらの設定は次のデバイスに適用されます。

- Windows 10 を実行するデバイス
- Windows Holographic for Business を実行するデバイス

選択する設定によっては、値の一部を構成できない場合があります。

## <a name="base-vpn-settings"></a>基本 VPN 設定

- **[接続名]**: この接続の名前を入力します。 エンド ユーザーがデバイスで利用可能な VPN 接続の一覧を参照するときに、この名前が表示されます。
- **[サーバー]**: デバイスの接続先となる 1 台以上の VPN サーバーを追加します。
  - **[追加]**: **[行の追加]** が開き、次の情報を入力できます。
    - **[説明]**: **Contoso VPN サーバー**など、サーバーを表す名前を入力します。
    - **[IP アドレスまたは FQDN]**: **192.168.1.1** または **vpn.contoso.com** など、デバイスの接続先となる VPN サーバーの IP アドレスまたは完全修飾ドメイン名を入力します。
    - **[既定のサーバー]**: このサーバーを、デバイスで接続を確立するために使用する既定のサーバーとして有効にします。 1 台のサーバーのみを既定のサーバーとして設定してください。
  - **[インポート]**: 説明、IP アドレスまたは FQDN、既定のサーバーという形式の、サーバーのリストを含む、コンマ区切りのファイルを参照します。 **[OK]** を選択すると、これらのサーバーが **[サーバー]** リストにインポートされます。
  - **[エクスポート]**: サーバーのリストをコンマ区切り値 (csv) ファイルにエクスポートします。

**[接続の種類]**: 以下のベンダーのリストから VPN 接続の種類を選択します。

- **Automatic**
- **Check Point Capsule VPN**
- **Citrix VPN**
- **SonicWALL Mobile Connect**
- **F5 Edge Client**
- **IKEv2**
- **L2TP**
- **PPTP**
- **Pulse Secure**

**[ログイン グループまたはドメイン]** (SonicWALL Mobile Connect のみ): VPN プロファイルでこのプロパティを設定することはできません。 代わりに、ユーザー名とドメインが `username@domain` または `DOMAIN\username` 形式で入力されている場合は、Mobile Connect でこの値が解析されます。

**[カスタム XML]**/**[EAP XML]**: VPN 接続を構成する任意のカスタム XML コマンドを入力します。

**Pulse Secure の例:**

```
<pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>
```

**CheckPoint Mobile VPN の例:**

```
<CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />
```

**SonicWALL Mobile Connect の例:**

```
<MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>
```

**F5 Edge Client の例:**

```
<f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>
```

カスタム XML コマンドの作成方法については、各製造元の VPN ドキュメントをご覧ください。

カスタム EAP XML の作成について詳しくは、「[EAP configuration](https://docs.microsoft.com/windows/client-management/mdm/eap-configuration)」(EAP の構成) をご覧ください。

**[分割トンネリング]**: **[有効]** または **[無効]** にします。これにより、トラフィックに応じて使用する接続をデバイスが判断できます。 たとえば、ホテルにいるユーザーは、業務ファイルへのアクセスに VPN 接続を使用しますが、通常の Web 閲覧にはホテルの標準ネットワークを使用します。
- **[この VPN 接続の分割トンネリング ルート]**: サードパーティ VPN プロバイダー用のオプション ルートを追加します。 各ルートの宛先プレフィックスとプレフィックス サイズを入力します。

## <a name="apps-and-traffic-rules"></a>アプリとトラフィックの規則

**[これらのアプリへの VPN 接続を制限する]**: 一部のアプリでのみ VPN 接続を使用する場合は、この設定を有効にします。

**[関連付けられているアプリ]**: 自動的に VPN 接続を使用するアプリのリストを入力します。 アプリ ID は、アプリの種類によって決まります。 ユニバーサル アプリの場合は、パッケージのファミリ名を入力します。 デスクトップ アプリの場合は、アプリのファイル パスを入力します。

>[!IMPORTANT]
>アプリごとの VPN に対して作成されたすべてのアプリ リストをセキュリティで保護することをお勧めします。 承認されていないユーザーがこのリストを変更し、それをアプリごとの VPN アプリ リストにインポートすると、アクセス権のないアプリへの VPN アクセスが承認される可能性があります。 アプリ リストをセキュリティで保護する 1 つの方法は、アクセス制御リスト (ACL) を使用することです。

**[この VPN 接続のネットワーク トラフィック規則]**: VPN 接続に対して有効にするプロトコル、ローカル ポートとリモート ポートおよびアドレス範囲を選択します。 ネットワーク トラフィック規則を作成しない場合は、すべてのプロトコル、ポート、アドレス範囲が有効になります。 規則を作成すると、その規則で入力したプロトコル、ポート、アドレス範囲のみが VPN 接続で使用されます。

## <a name="conditional-access"></a>条件付きアクセス

**[この VPN 接続の条件付きアクセス]**: クライアントからのデバイス コンプライアンス フローを有効にします。 有効にすると、VPN クライアントは Azure Active Directory と通信し、認証に使用する証明書の取得を試行します。 証明書認証を利用するには、VPN を設定する必要があります。VPN サーバーは、Azure Active Directory が返すサーバーを信頼する必要があります。

**[代替証明書によるシングル サインオン (SSO)**]: デバイス コンプライアンスの場合、Kerberos 認証のために、VPN 認証証明書とは異なる証明書を使用します。 次の設定で証明書を入力します。

- **拡張キー使用法**: 拡張キー使用法 (EKU) の名前。
- **オブジェクト識別子**: EKU のオブジェクト識別子。
- **発行者ハッシュ**: SSO 証明書のサムプリント。

## <a name="dns-settings"></a>DNS の設定

**[この VPN 接続の DNS 名と DNS サーバー]**: 接続が確立された後に VPN 接続で使用する DNS サーバーを選択します。
サーバーごとに、以下を入力します。
- **[DNS 名]**
- **[DNS サーバー]**
- **[プロキシ]**

## <a name="proxy-settings"></a>プロキシの設定

- **[自動的にプロキシ設定を検出する]**: VPN サーバーが接続にプロキシ サーバーを必要とする場合は、デバイスで接続の設定を自動的に検出するかどうかを選択します。
- **[自動構成スクリプト]**: ファイルを使用してプロキシ サーバーを構成します。 構成ファイルを含む、**プロキシ サーバー URL** (`http://proxy.contoso.com` など) を入力します。
- **[プロキシ サーバーを使用する]**: プロキシ サーバーの設定を手動で入力するには、このオプションを有効にします。
  - **[アドレス]**: プロキシ サーバーのアドレスを (IP アドレスとして) 入力します。
  - **[ポート番号]**: プロキシ サーバーに関連付けられているポート番号を入力します。
- **[ローカル アドレスにはプロキシ サーバーを使用しない]**: VPN サーバーが接続にプロキシ サーバーを必要とする場合、入力したローカル アドレスに対してプロキシ サーバーを使用しないようにするには、この設定を選択します。
