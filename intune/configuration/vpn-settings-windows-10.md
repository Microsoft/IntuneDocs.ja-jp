---
title: Microsoft Intune での Windows 10 VPN の設定 - Azure | Microsoft Docs
description: Microsoft Intune で使用可能なすべての VPN 設定、その用途、実行内容について説明します。これには、Windows 10 デバイスと Windows Holographic for Business デバイスのトラフィック規則、条件付きアクセス、DNS、プロキシ設定が含まれます。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/12/2018
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.reviewer: tycast
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5d5bd16964162bd30e1c246215ce5fafd23df5dd
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2019
ms.locfileid: "71734129"
---
# <a name="windows-10-and-windows-holographic-device-settings-to-add-vpn-connections-using-intune"></a>Intune を使用して VPN 接続を追加するための Windows 10 デバイスと Windows Holographic デバイスの設定

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Microsoft Intune を使用して、デバイスの VPN 接続を追加および構成できます。 この記事では、仮想プライベート ネットワーク (VPN) の作成時に一般的に使用される設定および機能の一覧を示して説明します。 これらの VPN 設定および機能は、デバイスにプッシュまたは展開されている、Intune のデバイス構成プロファイルで使用されます。

モバイル デバイス管理 (MDM) ソリューションの一部として、これらの設定を使用して、VPN ベンダーの使用、Always On、DNS の使用、プロキシの追加などの機能を有効化または無効化します。

これらの設定は、次を実行するデバイスのみに適用されます。

- Windows 10
- Windows Holographic for Business

選択する設定によっては、値の一部を構成できない場合があります。

## <a name="before-you-begin"></a>始める前に

[VPN デバイス構成プロファイルを作成します](vpn-settings-configure.md)。

## <a name="base-vpn-settings"></a>基本 VPN 設定

- **[接続名]** : この接続の名前を入力します。 エンド ユーザーがデバイスで利用可能な VPN 接続の一覧を参照するときに、この名前が表示されます。
- **[サーバー]** : デバイスの接続先となる 1 台以上の VPN サーバーを追加します。 サーバーを追加するときは、次の情報を入力します。
  - **[説明]** : **Contoso VPN サーバー**など、サーバーを表す名前を入力します。
  - **[IP アドレスまたは FQDN]** : **192.168.1.1** または **vpn.contoso.com** など、デバイスの接続先となる VPN サーバーの IP アドレスまたは完全修飾ドメイン名 (FQDN) を入力します
  - **[既定のサーバー]** : このサーバーを、デバイスで接続を確立するために使用する既定のサーバーとして有効にします。 1 台のサーバーのみを既定のサーバーとして設定してください。
  - **[インポート]** : 説明、IP アドレスまたは FQDN、既定のサーバーという形式のサーバーのリストを含む、コンマ区切りのファイルを参照します。 **[OK]** を選んで、これらのサーバーを **[サーバー]** 一覧にインポートします。
  - **[エクスポート]** : サーバーのリストをコンマ区切り値 (csv) ファイルにエクスポートします。

- **[内部 DNS を持つ IP アドレスを登録します]** : **[有効にする]** を選択すると、内部 DNS で VPN インターフェイスに割り当てられた IP アドレスを動的に登録するように Windows 10 VPN プロファイルが構成されます。 **[無効にする]** を選択すると、IP アドレスは動的に登録されません。

- **[接続の種類]** : 以下のベンダーのリストから VPN 接続の種類を選択します。

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
  - **[常時接続]** : **[有効にする]** を選択すると、次のようなイベントが発生した場合に VPN 接続に自動的に接続されます。 
    - ユーザーが自分のデバイスにサインインしたとき
    - デバイスでネットワークが変更されたとき
    - デバイスの画面がオフにされた後でオンに戻されたとき 

  - **[認証方法]** : ユーザーが VPN サーバーに対して認証を行う方法を選びます。 **証明書**を使用すると、ゼロタッチ エクスペリエンス、オンデマンド VPN、アプリごとの VPN などの拡張機能が提供されます。
  - **[ログオンするたびに資格情報を記憶する]** : 認証の資格情報をキャッシュに格納することを選びます。
  - **[カスタム XML]** : VPN 接続を構成する任意のカスタム XML コマンドを入力します。
  - **[EAP XML]** : VPN 接続を構成する任意の EAP XML コマンドを入力します。

### <a name="pulse-secure-example"></a>Pulse Secure の例

```
<pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>
```

### <a name="f5-edge-client-example"></a>F5 Edge Client の例

```
<f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>
```

### <a name="sonicwall-mobile-connect-example"></a>SonicWALL Mobile Connect の例
**[ログイン グループまたはドメイン]** : VPN プロファイルでこのプロパティを設定することはできません。 代わりに、ユーザー名とドメインが `username@domain` または `DOMAIN\username` 形式で入力されている場合は、Mobile Connect でこの値が解析されます。

例:

```
<MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>
```

### <a name="checkpoint-mobile-vpn-example"></a>CheckPoint Mobile VPN の例

```
<CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />
```

### <a name="writing-custom-xml"></a>カスタムの XML の作成
カスタム XML コマンドの作成方法については、各製造元の VPN ドキュメントをご覧ください。

カスタム EAP XML の作成について詳しくは、「[EAP configuration](https://docs.microsoft.com/windows/client-management/mdm/eap-configuration)」(EAP の構成) をご覧ください。

## <a name="apps-and-traffic-rules"></a>アプリとトラフィックの規則

- **[WIP やアプリをこの VPN に関連付ける]** : 一部のアプリで VPN 接続を使用する場合にのみ、この設定を有効にします。 次のようなオプションがあります。

  - **[WIP をこの接続に関連付ける]** : **この接続の WIP ドメイン**を入力します
  - **[アプリをこの接続に関連付ける]** : **これらのアプリへの VPN 接続を制限**した後、**関連付けるアプリ**を追加することができます。 入力したアプリは、VPN 接続を自動的に使用します。 アプリ ID は、アプリの種類によって決まります。 ユニバーサル アプリの場合は、パッケージのファミリ名を入力します。 デスクトップ アプリの場合は、アプリのファイル パスを入力します。
  >[!IMPORTANT]
  >アプリごとの VPN に対して作成されたすべてのアプリ リストをセキュリティで保護することをお勧めします。 承認されていないユーザーがこのリストを変更し、それをアプリごとの VPN アプリ リストにインポートすると、アクセス権のないアプリへの VPN アクセスが承認される可能性があります。 アプリ リストをセキュリティで保護する 1 つの方法は、アクセス制御リスト (ACL) を使用することです。

- **[この VPN 接続のネットワーク トラフィック規則]** : VPN 接続に対して有効にするプロトコル、ローカル ポートとリモート ポートおよびアドレス範囲を選択します。 ネットワーク トラフィック規則を作成しない場合は、すべてのプロトコル、ポート、アドレス範囲が有効になります。 規則を作成すると、その規則で入力したプロトコル、ポート、アドレス範囲のみが VPN 接続で使用されます。

## <a name="conditional-access"></a>条件付きアクセス

- **[この VPN 接続の条件付きアクセス]** : クライアントからのデバイス コンプライアンス フローを有効にします。 有効にすると、VPN クライアントは Azure Active Directory (AD) と通信し、認証に使用する証明書を取得します。 証明書認証を利用するには、VPN を設定する必要があります。VPN サーバーは、Azure AD が返すサーバーを信頼する必要があります。

- **[代替証明書によるシングル サインオン (SSO)** ]: デバイス コンプライアンスの場合、Kerberos 認証のために、VPN 認証証明書とは異なる証明書を使用します。 次の設定で証明書を入力します。

  - **[名前]** : 拡張キー使用法 (EKU) の名前。
  - **オブジェクト識別子**: EKU のオブジェクト識別子。
  - **発行者ハッシュ**: SSO 証明書のサムプリント。

## <a name="dns-settings"></a>DNS の設定

- **[DNS サフィックス検索一覧]** : **[DNS サフィックス]** で、DNS サフィックスを入力して **[追加]** を選択します。 さまざまなサフィックスを追加できます。

  DNS サフィックスを使用する場合は、完全修飾ドメイン名 (FQDN) ではなく、短い名前を使用してネットワーク リソースを検索できます。 短い名前を使用して検索する場合、DNS サーバーによってサフィックスが自動的に決定されます。 たとえば、`utah.contoso.com` が DNS サフィックスの一覧にあるとします。 `DEV-comp` を ping します。 このシナリオでは、`DEV-comp.utah.contoso.com` に解決されます。

  DNS サフィックスは一覧順に解決されます。この順序は変更できます。 たとえば、`colorado.contoso.com` と `utah.contoso.com` が DNS サフィックスの一覧にあり、両方に `DEV-comp` というリソースがあるとします。 `colorado.contoso.com` は一覧の最初にあるため、`DEV-comp.colorado.contoso.com` として解決されます。
  
  順序を変更するには、DNS サフィックスの左側にあるドットをクリックし、サフィックスを最上部にドラッグします。

  ![3 つのドットを選択し、クリック アンド ドラッグで dns サフィックスを移動する](./media/vpn-settings-windows-10/vpn-settings-windows10-move-dns-suffix.png)

- **名前解決ポリシーテーブル (nrpt) 規則**: 名前解決ポリシーテーブル (nrpt) 規則は、VPN への接続時に DNS が名前を解決する方法を定義します。 VPN 接続が確立された後に、VPN 接続で使用する DNS サーバーを選択できます。

  入力したドメインを解決するために、ドメイン、DNS サーバー、プロキシ、およびその他の詳細が含まれているテーブルに規則を追加できます。 VPN 接続は、入力されたドメインにユーザーが接続するときに、これらの規則を使用します。

  **[追加]** を選択して、新しい規則を追加します。 サーバーごとに、以下を入力します。

  - **[ドメイン]** : 規則を適用する完全修飾ドメイン名 (FQDN) または DNS サフィックスを入力します。 DNS サフィックスの先頭にピリオド (.) を入力することもできます。 たとえば、「`contoso.com`」や「`.allcontososubdomains.com`」と入力します。
  - **[DNS サーバー]** : ドメインを解決する IP アドレスまたは DNS サーバーを入力します。 たとえば、「`10.0.0.3`」や「`vpn.contoso.com`」と入力します。
  - **[プロキシ]** : ドメインを解決する Web プロキシ サーバーを入力します。 たとえば、「`http://proxy.com`」と入力します。
  - **[自動接続]** : **有効**にすると、デバイスは、ユーザーが入力した `contoso.com` などのドメインに接続するときに、VPN に自動的に接続されます。 **[未構成]** (既定) にすると、デバイスは VPN に自動的には接続されません。
  - **[永続]** : **[有効]** に設定すると、規則は、VPN 接続が切断された後も、デバイスから手動で削除されるまで名前解決ポリシー テーブル (NRPT) 内に留まります。 **[未構成]** (既定) に設定すると、VPN プロファイルの NRPT 規則は、VPN が切断されるとデバイスから削除されます。

## <a name="proxy-settings"></a>プロキシの設定

- **[自動構成スクリプト]** : ファイルを使用してプロキシ サーバーを構成します。 構成ファイルを含む、**プロキシ サーバー URL** (`http://proxy.contoso.com` など) を入力します。
- **[アドレス]** : プロキシ サーバーのアドレスを入力します (IP アドレスや `vpn.contoso.com` など)。
- **[ポート番号]** : プロキシ サーバーが使用する TCP ポート番号を入力します。
- **[ローカル アドレスにはプロキシ サーバーを使用しない]** : ローカル アドレスに対してプロキシ サーバーを使用しない場合は、[有効] を選びます。 この設定は、VPN サーバーが接続にプロキシ サーバーを必要とする場合に適用されます。

## <a name="split-tunneling"></a>分割トンネリング

- **[分割トンネリング]** : **[有効]** または **[無効]** にします。これにより、トラフィックに応じて使用する接続をデバイスが判断できます。 たとえば、ホテルにいるユーザーは、業務ファイルへのアクセスに VPN 接続を使用しますが、通常の Web 閲覧にはホテルの標準ネットワークを使用します。
- **[この VPN 接続の分割トンネリング ルート]** : サードパーティ VPN プロバイダー用のオプション ルートを追加します。 各接続の宛先プレフィックスとプレフィックス サイズを入力します。

## <a name="trusted-network-detection"></a>信頼できるネットワーク検出

**[信頼されたネットワークの DNS サフィックス]** : 信頼できるネットワークにユーザーが既に接続されている場合は、デバイスが別の VPN 接続に自動的に接続されるのを防ぐことができます。

**[DNS サフィックス]** に、信頼したい DNS サフィックス (contoso.com など) を入力し、 **[追加]** を選択します。 必要な任意の数のサフィックスを追加できます。

リスト内の DNS サフィックスにユーザーが接続されている場合、ユーザーは別の VPN 接続に自動的には接続されません。 ユーザーは、入力された DNS サフィックスの信頼できるリストを引き続き使用します。 自動トリガーが設定されている場合でも、信頼できるネットワークが引き続き使用されます。

たとえば、信頼できる DNS サフィックスにユーザーが既に接続されている場合、次の自動トリガーが無視されます。 具体的には、リスト内の DNS サフィックスが、次を含む他のすべての接続自動トリガーをキャンセルします。

- 常にオン
- アプリ ベースのトリガー
- DNS 自動トリガー

## <a name="next-steps"></a>次の手順

プロファイルは作成されましたが、まだ何も行われていません。 次に、[プロファイルを割り当て](device-profile-assign.md)、[その状態を監視](device-profile-monitor.md)します。

[Android](vpn-settings-android.md)、[iOS](vpn-settings-ios.md)、および [macOS](vpn-settings-macos.md) デバイスで VPN 設定を構成します。
