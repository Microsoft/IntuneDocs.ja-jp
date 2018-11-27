---
title: Microsoft Intune で Windows 10 VPN の設定を構成する - Azure | Microsoft Docs
description: Microsoft Intune で使用可能な VPN 設定、その用途、実行内容について説明します。これには、トラフィック規則、条件付きアクセス、Windows 10 デバイスと Windows Holographic for Business デバイスの DNS、プロキシ設定が含まれます。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 9/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.reviewer: tycast
ms.custom: intune-azure
ms.openlocfilehash: 0fc2ce416459221564f2edf239eb97774d5efdd4
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2018
ms.locfileid: "52187941"
---
# <a name="windows-10-vpn-settings-in-intune"></a>Intune での Windows 10 VPN の設定

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune を使用して VPN 接続を構成することができます。 この記事では、これらの設定、トラフィック規則、条件付きアクセス、DNS とプロキシの設定について説明します。

これらの設定は次のデバイスに適用されます。

- Windows 10 を実行するデバイス
- Windows Holographic for Business を実行するデバイス

選択する設定によっては、値の一部を構成できない場合があります。

## <a name="base-vpn-settings"></a>基本 VPN 設定

- **[接続名]**: この接続の名前を入力します。 エンド ユーザーがデバイスで利用可能な VPN 接続の一覧を参照するときに、この名前が表示されます。
- **[サーバー]**: デバイスの接続先となる 1 台以上の VPN サーバーを追加します。 サーバーを追加するときは、次の情報を入力します。
  - **[説明]**: **Contoso VPN サーバー**など、サーバーを表す名前を入力します。
  - **[IP アドレスまたは FQDN]**: **192.168.1.1** または **vpn.contoso.com** など、デバイスの接続先となる VPN サーバーの IP アドレスまたは完全修飾ドメイン名を入力します。
  - **[既定のサーバー]**: このサーバーを、デバイスで接続を確立するために使用する既定のサーバーとして有効にします。 1 台のサーバーのみを既定のサーバーとして設定してください。
  - **[インポート]**: 説明、IP アドレスまたは FQDN、既定のサーバーという形式のサーバーのリストを含む、コンマ区切りのファイルを参照します。 **[OK]** を選んで、これらのサーバーを **[サーバー]** 一覧にインポートします。
  - **[エクスポート]**: サーバーのリストをコンマ区切り値 (csv) ファイルにエクスポートします。

- **[内部 DNS を持つ IP アドレスを登録します]**: **[有効にする]** を選択すると、内部 DNS で VPN インターフェイスに割り当てられた IP アドレスを動的に登録するように Windows 10 VPN プロファイルが構成されます。 **[無効にする]** を選択すると、IP アドレスは動的に登録されません。

- **[接続の種類]**: 以下のベンダーのリストから VPN 接続の種類を選択します。

  - **Pulse Secure**
  - **F5 Edge Client**
  - **SonicWALL Mobile Connect**
  - **Check Point Capsule VPN**
  - **Citrix**
  - **Palo Alto Networks GlobalProtect**
  - **Automatic**
  - **IKEv2**
  - **L2TP**
  - **PPTP**

  VPN 接続の種類を選択するときに、次の設定を求められる場合があります。  
    - **[Always On]**: 次のようなイベントが発生した場合に、VPN 接続に自動的に接続**できる**ようにします。 
      - ユーザーが自分のデバイスにサインインしたとき
      - デバイスでネットワークが変更されたとき
      - デバイスの画面がオフにされた後でオンに戻されたとき 

    - **[認証方法]**: ユーザーが VPN サーバーに対して認証を行う方法を選びます。 **証明書**を使用すると、ゼロタッチ エクスペリエンス、オンデマンド VPN、アプリごとの VPN などの拡張機能が提供されます。
    - **[ログオンするたびに資格情報を記憶する]**: 認証の資格情報をキャッシュに格納することを選びます。
    - **[カスタム XML]**: VPN 接続を構成する任意のカスタム XML コマンドを入力します。
    - **[EAP XML]**: VPN 接続を構成する任意の EAP XML コマンドを入力します。

#### <a name="pulse-secure-example"></a>Pulse Secure の例

```
<pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>
```

#### <a name="f5-edge-client-example"></a>F5 Edge Client の例

```
<f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>
```

#### <a name="sonicwall-mobile-connect-example"></a>SonicWALL Mobile Connect の例
**[ログイン グループまたはドメイン]**: VPN プロファイルでこのプロパティを設定することはできません。 代わりに、ユーザー名とドメインが `username@domain` または `DOMAIN\username` 形式で入力されている場合は、Mobile Connect でこの値が解析されます。

例:

```
<MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>
```

#### <a name="checkpoint-mobile-vpn-example"></a>CheckPoint Mobile VPN の例

```
<CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />
```

#### <a name="writing-custom-xml"></a>カスタムの XML の作成
カスタム XML コマンドの作成方法については、各製造元の VPN ドキュメントをご覧ください。

カスタム EAP XML の作成について詳しくは、「[EAP configuration](https://docs.microsoft.com/windows/client-management/mdm/eap-configuration)」(EAP の構成) をご覧ください。

## <a name="apps-and-traffic-rules"></a>アプリとトラフィックの規則

- **[WIP やアプリをこの VPN に関連付ける]**: 一部のアプリで VPN 接続を使用する場合にのみ、この設定を有効にします。 次のようなオプションがあります。

  - **[WIP をこの接続に関連付ける]**: **この接続の WIP ドメイン**を入力します
  - **[アプリをこの接続に関連付ける]**: **これらのアプリへの VPN 接続を制限**した後、**関連付けるアプリ**を追加することができます。 入力したアプリは、VPN 接続を自動的に使用します。 アプリ ID は、アプリの種類によって決まります。 ユニバーサル アプリの場合は、パッケージのファミリ名を入力します。 デスクトップ アプリの場合は、アプリのファイル パスを入力します。
  >[!IMPORTANT]
  >アプリごとの VPN に対して作成されたすべてのアプリ リストをセキュリティで保護することをお勧めします。 承認されていないユーザーがこのリストを変更し、それをアプリごとの VPN アプリ リストにインポートすると、アクセス権のないアプリへの VPN アクセスが承認される可能性があります。 アプリ リストをセキュリティで保護する 1 つの方法は、アクセス制御リスト (ACL) を使用することです。

- **[この VPN 接続のネットワーク トラフィック規則]**: VPN 接続に対して有効にするプロトコル、ローカル ポートとリモート ポートおよびアドレス範囲を選択します。 ネットワーク トラフィック規則を作成しない場合は、すべてのプロトコル、ポート、アドレス範囲が有効になります。 規則を作成すると、その規則で入力したプロトコル、ポート、アドレス範囲のみが VPN 接続で使用されます。

## <a name="conditional-access"></a>条件付きアクセス

- **[この VPN 接続の条件付きアクセス]**: クライアントからのデバイス コンプライアンス フローを有効にします。 有効にすると、VPN クライアントは Azure Active Directory (AD) と通信し、認証に使用する証明書を取得します。 証明書認証を利用するには、VPN を設定する必要があります。VPN サーバーは、Azure AD が返すサーバーを信頼する必要があります。

- **[代替証明書によるシングル サインオン (SSO)**]: デバイス コンプライアンスの場合、Kerberos 認証のために、VPN 認証証明書とは異なる証明書を使用します。 次の設定で証明書を入力します。

  - **[名前]**: 拡張キー使用法 (EKU) の名前。
  - **オブジェクト識別子**: EKU のオブジェクト識別子。
  - **発行者ハッシュ**: SSO 証明書のサムプリント。

## <a name="dns-settings"></a>DNS の設定

- **[DNS サフィックス検索一覧]**: **[DNS サフィックス]** で、DNS サフィックスを入力して **[追加]** を選択します。 複数のサフィックスを追加できます。

  DNS サフィックスを使用する場合は、完全修飾ドメイン名 (FQDN) ではなく、短い名前を使用してネットワーク リソースを検索できます。 短い名前を使用して検索する場合、DNS サーバーによってサフィックスが自動的に決定されます。 たとえば、`utah.contoso.com` が DNS サフィックスの一覧にあるとします。 `DEV-comp` を ping します。 このシナリオでは、`DEV-comp.utah.contoso.com` に解決されます。

  DNS サフィックスは一覧順に解決されます。この順序は変更できます。 たとえば、`colorado.contoso.com` と `utah.contoso.com` が DNS サフィックスの一覧にあり、両方に `DEV-comp` というリソースがあるとします。 `colorado.contoso.com` は一覧の最初にあるため、`DEV-comp.colorado.contoso.com` として解決されます。
  
  順序を変更するには、DNS サフィックスの左側にあるドットをクリックし、サフィックスを最上部にドラッグします。

  ![3 つのドットを選択し、クリック アンド ドラッグで dns サフィックスを移動する](./media/vpn-settings-windows10-move-dns-suffix.png)

- **[この VPN 接続のドメインとサーバー]**: VPN が使用するドメインと DNS サーバーを追加します。 接続が確立された後に VPN 接続で使用する DNS サーバーを選択できます。 サーバーごとに、以下を入力します。
- **ドメイン**
- **[DNS サーバー]**
- **[プロキシ]**

## <a name="proxy-settings"></a>プロキシの設定

- **[自動構成スクリプト]**: ファイルを使用してプロキシ サーバーを構成します。 構成ファイルを含む、**プロキシ サーバー URL** (`http://proxy.contoso.com` など) を入力します。
- **[アドレス]**: プロキシ サーバーのアドレスを入力します (IP アドレスや `vpn.contoso.com` など)。
- **[ポート番号]**: プロキシ サーバーが使用する TCP ポート番号を入力します。
- **[ローカル アドレスにはプロキシ サーバーを使用しない]**: ローカル アドレスに対してプロキシ サーバーを使用しない場合は、[有効] を選びます。 この設定は、VPN サーバーが接続にプロキシ サーバーを必要とする場合に適用されます。

## <a name="split-tunneling"></a>分割トンネリング

- **[分割トンネリング]**: **[有効]** または **[無効]** にします。これにより、トラフィックに応じて使用する接続をデバイスが判断できます。 たとえば、ホテルにいるユーザーは、業務ファイルへのアクセスに VPN 接続を使用しますが、通常の Web 閲覧にはホテルの標準ネットワークを使用します。
- **[この VPN 接続の分割トンネリング ルート]**: サードパーティ VPN プロバイダー用のオプション ルートを追加します。 各接続の宛先プレフィックスとプレフィックス サイズを入力します。
