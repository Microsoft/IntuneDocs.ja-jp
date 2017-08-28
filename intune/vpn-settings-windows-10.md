---
title: "Windows 10 デバイス向けの Intune の VPN 設定"
titleSuffix: Intune on Azure
description: "Windows 10 デバイスで VPN 接続の構成に使用できる Intune 設定について説明します。\""
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 495e4ed6-b2ef-47cc-a110-13fa9b5f85a6
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8e7fb7697f50706566210063605e9b5d750e0c90
ms.sourcegitcommit: 5a4529aae710ca2abac5b4d2cfd92cb2df7e67cb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2017
---
# <a name="vpn-settings-for-windows-10-devices-in-microsoft-intune"></a>Microsoft Intune での Windows 10 デバイス向けの VPN 設定

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

選択する設定によっては、以下の一覧に記載されている値の一部を構成できない場合もあります。


## <a name="base-vpn-settings"></a>基本 VPN 設定


- **[接続名]** - この接続の名前を入力します。 エンド ユーザーがデバイスで利用可能な VPN 接続の一覧を参照するときに、この名前が表示されます。
- **[サーバー]** - デバイスの接続先とする 1 台以上の VPN サーバーを追加します。
    - **[追加]** - **[行の追加]** ブレードが開き、以下の情報を指定できます。
        - **[説明]** - **Contoso VPN サーバー**のような、サーバーを表す名前を指定します。
        - **[IP アドレスまたは FQDN]** - デバイスが接続する VPN サーバーの IP アドレスまたは完全修飾ドメイン名を指定します。 例: **192.168.1.1**、**vpn.contoso.com**。
        - **[既定のサーバー]** - このサーバーを、デバイスで接続を確立するために使用する既定のサーバーとして有効にします。 既定のサーバーとして設定するサーバーの数は 1 台のみにしてください。
    - **[インポート]** - 説明、IP アドレスまたは FQDN、既定のサーバーという形式でまとめられた、コンマ区切りのサーバーのリストを含むファイルを参照します。 **[OK]** を選択すると、これらが **[サーバー]** リストにインポートされます。
    - **[エクスポート]** - サーバーのリストをコンマ区切り値 (csv) ファイルにエクスポートします。

**[接続の種類]** - 以下のベンダーの一覧から VPN 接続の種類を選択します。
- **Pulse Secure**
- **F5 Edge Client**
- **Dell SonicWALL Mobile Connect**
- **Check Point Capsule VPN**
- **Automatic**
- **IKEv2**
- **L2TP**
- **PPTP**

**[ログイン グループまたはドメイン]** (Dell SonicWALL Mobile Connect のみ) - 接続先のログイン グループまたはドメインの名前を指定します。

**[カスタム XML]**/**[EAP XML]** - VPN 接続を構成する任意のカスタム XML コマンドを指定します。

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

**[分割トンネリング]** - このオプションを **[有効]** または **[無効]** にします。これを有効にすると、使用する接続をトラフィックに応じてデバイスが判断するようになります。 たとえば、ホテルにいるユーザーは、業務ファイルへのアクセスに VPN 接続を使用しますが、通常の Web 閲覧にはホテルの標準ネットワークを使用します。
- **[この VPN 接続の分割トンネリング ルート]** - サードパーティ VPN プロバイダー用のオプション ルートを追加します。 各ルートの宛先プレフィックスとプレフィックス サイズを指定します。

## <a name="apps-and-traffic-rules"></a>アプリとトラフィックの規則

**[これらのアプリへの VPN 接続を制限する]** - 指定したアプリでのみ VPN 接続を使用したい場合にこのオプションを有効にします。
**[関連付けられているアプリ]** - 自動的に VPN 接続を使用するアプリのリストを指定します。 アプリ ID は、アプリの種類によって決まります。 ユニバーサル アプリの場合、パッケージのファミリ名を指定します。 デスクトップ アプリの場合、アプリのファイル パスを指定します。

>[!IMPORTANT]
>アプリごとの VPN の構成で使用するためにコンパイルするアプリのすべてのリストをセキュリティで保護することをお勧めします。 承認されていないユーザーが変更したリストをアプリごとの VPN アプリ リストにインポートすると、アクセス権のないアプリへの VPN アクセスが承認される可能性があります。 アプリ リストをセキュリティで保護する 1 つの方法は、アクセス制御リスト (ACL) を使用することです。

**[この VPN 接続のネットワーク トラフィック規則]** - VPN 接続に対して有効にするプロトコル、ローカル ポートとリモート ポート、アドレス範囲を選択します。 ネットワーク トラフィック規則を作成しない場合は、すべてのプロトコル、ポート、およびアドレス範囲が有効になります。 規則を作成すると、その規則で指定したプロトコル、ポート、およびアドレス範囲だけが、VPN 接続で使用されます。


## <a name="conditional-access"></a>条件付きアクセス

**この VPN 接続の条件付きアクセス** - クライアントからのデバイス コンプライアンス フローを有効にします。 有効にすると、VPN クライアントは Azure Active Directory と通信し、認証に使用する証明書の取得を試行します。 証明書認証を利用するには、VPN を設定する必要があります。VPN サーバーは、Azure Active Directory が返すサーバーを信頼する必要があります。

**代替証明書によるシングル サインオン (SSO)** - デバイス コンプライアンスの場合、Kerberos 認証のために、VPN 認証証明書とは異なる証明書を利用します。 次の設定で証明書を指定します。 

- **拡張キー使用法** - 拡張キー使用法 (EKU) の名前。
- **オブジェクト識別子** - EKU のオブジェクト識別子。
- **発行者ハッシュ** - SSO 証明書のサムプリント。

## <a name="dns-settings"></a>DNS の設定

**[この VPN 接続の DNS 名と DNS サーバー]** - 接続が確立された後に VPN 接続で使用する DNS サーバーを選択します。
サーバーごとに、 次の値を指定します。
- **[DNS 名]**
- **[DNS サーバー]**
- **[プロキシ]**

## <a name="proxy-settings"></a>プロキシの設定

- **[自動的にプロキシ設定を検出する]** - VPN サーバーが接続にプロキシ サーバーを必要とする場合は、デバイスで接続の設定を自動的に検出するかどうかを指定します。 詳細については、Windows Server のマニュアルを参照してください。
- **[自動構成スクリプト]** - ファイルを使用してプロキシ サーバーを構成します。 構成ファイルが格納されている**プロキシ サーバーの URL** を入力します (たとえば、**http://proxy.contoso.com**)。
- **[プロキシ サーバーを使用する]** - プロキシ サーバーの設定を手動で入力する場合は、このオプションを有効にします。
    - **[アドレス]** - プロキシ サーバーのアドレスを (IP アドレスとして) 入力します。
    - **[ポート番号]** - プロキシ サーバーに関連付けられているポート番号を入力します。
- **[ローカル アドレスにはプロキシ サーバーを使用しない]** - VPN サーバーが接続にプロキシ サーバーを必要とする場合、指定したローカル アドレスに対してプロキシ サーバーを使用しないようにするには、このオプションを選択します。 詳細については、Windows Server のマニュアルを参照してください。
