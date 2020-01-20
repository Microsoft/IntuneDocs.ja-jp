---
title: Microsoft Intune で iOS デバイス向けの VPN 設定を構成する - Azure | Microsoft Docs
description: 仮想プライベート ネットワーク (VPN) の構成設定を使用して VPN 構成プロファイルを追加または作成します。iOS を実行するデバイス上の Microsoft Intune での、基本設定での接続の詳細、認証方法、分割トンネリングなど、ID を含むカスタム VPN の設定およびキーと値のペア、Safari URL を含むアプリごとの VPN の設定と SSID または DNS 検索ドメインを含むオンデマンドの VPN、構成スクリプト、IP または FQDN アドレス、TCP ポートを含むプロキシの設定などがあります。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/13/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9eb7ee99d69fd56707bd9dfe5453ffe0bb107bad
ms.sourcegitcommit: 2506cdbfccefd42587a76f14ee50c3849dad1708
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 01/11/2020
ms.locfileid: "75885652"
---
# <a name="add-vpn-settings-on-ios-devices-in-microsoft-intune"></a>Microsoft Intune で iOS デバイス向けの VPN 設定を構成する

Microsoft Intune には、ご利用の iOS デバイスに展開できる VPN 設定が多数含まれています。 これらの設定は、組織のネットワークへの VPN 接続を作成し構成するのに使用されます。 この記事では、これらの設定について説明します。 設定の中には、Citrix や Zscaler などの一部の VPN クライアントでしか利用できないものがあります。

## <a name="before-you-begin"></a>始める前に

[デバイス構成プロファイルを作成します](vpn-settings-configure.md)。

> [!NOTE]
> これらの設定は、すべての登録の種類で使用できます。 登録の種類の詳細については、「 [iOS の登録](../enrollment/ios-enroll.md)」を参照してください。

## <a name="connection-type"></a>接続の種類

以下のベンダーのリストから VPN 接続の種類を選択します。

- **Check Point Capsule VPN**
- **Cisco Legacy AnyConnect**:4.0.5x 以前のバージョンの [Cisco Legacy AnyConnect](https://itunes.apple.com/app/cisco-legacy-anyconnect/id392790924) アプリに適用できます。
- **Cisco AnyConnect**:4.0.7x 以降のバージョンの [Cisco AnyConnect](https://itunes.apple.com/app/cisco-anyconnect/id1135064690) アプリに適用できます。
- **SonicWall Mobile Connect**
- **F5 Access Legacy**:バージョンが 2.1 以前の F5 Access アプリに適用できます。
- **F5 Access**:バージョンが 3.0 以降の F5 Access アプリに適用できます。
- **Palo Alto Networks GlobalProtect (レガシ)** :バージョンが 4.1 以前の Palo Alto Networks GlobalProtect アプリに適用できます。
- **Palo Alto Networks GlobalProtect**:バージョンが 5.0 以降の Palo Alto Networks GlobalProtect アプリに適用できます。
- **Pulse Secure**
- **Cisco (IPSec)**
- **Citrix VPN**
- **Citrix SSO**
- **Zscaler**:条件付きアクセスを使用する、またはユーザーが Zscaler サインイン画面をバイパスできるようにするには、Zscaler Private Access (ZPA) をご使用の Azure AD アカウントと統合する必要があります。 詳しい手順については、[Zscaler ドキュメント](https://help.zscaler.com/zpa/configuration-example-microsoft-azure-ad)をご覧ください。 
- **Ikev2**: [ikev2 設定](#ikev2-settings)(この記事では) は、プロパティについて説明します。
- **Custom VPN**

> [!NOTE]
> Cisco、Citrix、F5、Palo Alto については、iOS 12 ではそれらのレガシー クライアントが動作しないことが発表されています。 できるだけ早く、新しいアプリに移行してください。 詳細については、[Microsoft Intune サポート チームのブログ](https://go.microsoft.com/fwlink/?linkid=2013806&clcid=0x409)を参照してください。

## <a name="base-vpn-settings"></a>基本 VPN 設定

以下の一覧に示した設定は、選択した VPN 接続の種類によって決まります。  

- **[接続名]** :エンド ユーザーがデバイスで利用可能な VPN 接続の一覧を参照するときに、この名前が表示されます。
- **[カスタム ドメイン名]** (Zscaler のみ):Zscaler アプリのサインイン フィールドに、ユーザーが属するドメインが事前入力されます。 たとえば、ユーザー名が `Joe@contoso.net` であれば、アプリを開いたとき、フィールドにドメイン `contoso.net` が固定値として表示されます。 ドメイン名を入力しない場合は、Azure Active Directory (AD) に登録されている UPN のドメイン部分が使用されます。
- **[IP アドレスまたは FQDN]** :デバイスが接続する VPN サーバーの IP アドレスまたは完全修飾ドメイン名 (FQDN)。 たとえば、「`192.168.1.1`」や「`vpn.contoso.com`」と入力します。
- **[組織のクラウド名]** (Zscaler のみ):組織がプロビジョニングされているクラウドの名前を入力します。 Zscaler へのサインインに使用する URL に、その名前が含まれています。  
- **[認証方法]** :VPN サーバーに対するデバイスの認証方法として、以下のいずれかを選択します。 
  - **証明書**: **[認証証明書]** で、接続を認証するための既存の SCEP または PKCS 証明書プロファイルを選択します。 「[証明書の構成](../protect/certificates-configure.md)」では、証明書プロファイルについてのガイダンスが提供されています。
  - **[ユーザー名とパスワード]** :エンド ユーザーは VPN サーバーにサインインするためにユーザー名とパスワードを入力する必要があります。  

    > [!NOTE]
    > Cisco IPsec VPN の認証方法としてユーザー名とパスワードが使われている場合は、カスタム Apple Configurator プロファイルで SharedSecret を配布する必要があります。

  - 派生された**資格情報**: ユーザーのスマートカードから派生した証明書を使用します。 派生した資格情報発行者が構成されていない場合は、Intune によって追加するように求められます。 詳細については、「 [Microsoft Intune での派生資格情報の使用](../protect/derived-credentials.md)」を参照してください。

- **[除外された URL]** (Zscaler のみ):Zscaler VPN に接続されると、一覧にある URL には Zscaler クラウドの外からアクセスできます。 

- **[分割トンネリング]** : **[有効]** または **[無効]** にします。これにより、トラフィックに応じて使用する接続がデバイスで判断されます。 たとえば、ホテルにいるユーザーは、業務ファイルへのアクセスに VPN 接続を使用しますが、通常の Web 閲覧にはホテルの標準ネットワークを使用します。

- **[VPN 識別子]** (Custom VPN、Zscaler、Citrix):使用している VPN アプリの識別子。VPN プロバイダーから提供されます。
  - **[Enter key/value pairs for your organization's custom VPN attributes]\(組織のカスタム VPN 属性に対してキーまたは値を入力\)** :VPN 接続をカスタマイズするための**キー**と**値**を追加またはインポートします。 これらの値は、通常、ご利用の VPN プロバイダーから提供されることに注意してください。

- **[ネットワーク アクセス制御 (NAC) を有効にする]** (Citrix SSO、F5 Access): **[同意する]** を選択すると、このデバイス ID が VPN プロファイルに含められます。 VPN への認証用にこの ID を使用して、ネットワーク アクセスを許可または禁止することができます。

  **F5 Access を使用するときは**、必ず次の操作を行ってください。

  - F5 BIG-IP 13.1.1.5 を使用していることを確認します。 BIG-IP 14 はサポートされていません。
  - NAC 用に Intune に BIG-IP を統合します。 「[Overview:Configuring APM for device posture checks with endpoint management systems](https://support.f5.com/kb/en-us/products/big-ip_apm/manuals/product/apm-client-configuration-7-1-6/6.html#guid-0bd12e12-8107-40ec-979d-c44779a8cc89)」 (概要: エンドポイント管理システムを使用したデバイス ポスチャ チェック用の APM の構成) F5 ガイドを参照してください。
  - VPN プロファイルで NAC を有効にします。

  **ゲートウェイと共に Citrix SSO を使用する場合**、必ず次の操作を行ってください。

  - Citrix ゲートウェイ 12.0.59 以上を使用していることを確認します。
  - ユーザーが各自のデバイスに Citrix SSO 1.1.6 以降をインストール済みであることを確認します。
  - Citrix Gateway と Intune for NAC を統合します。 Citrix の配置に関するガイド「[Integrating Microsoft Intune/Enterprise Mobility Suite with NetScaler (LDAP+OTP Scenario)](https://www.citrix.com/content/dam/citrix/en_us/documents/guide/integrating-microsoft-intune-enterprise-mobility-suite-with-netscaler.pdf)」(Microsoft Intune/Enterprise Mobility Suite と NetScaler との統合 (LDAP + OTP のシナリオ)) を参照してください。
  - VPN プロファイルで NAC を有効にします。

  **重要な詳細情報**:  

  - NAC を有効にすると、VPN は 24 時間ごとに切断されます。 VPN はすぐに再接続できます。
  - デバイス ID はプロファイルの一部ですが、Intune 内には表示されません。 この ID は Microsoft によっていずれの場所にも格納されず、Microsoft によって共有されていません。

  デバイス ID をサポートする VPN パートナーについては、Citrix SSO などの VPN クライアントが ID を取得できます。 その後、そのデバイスが登録されていることの確認、さらに VPN プロファイルが準拠しているか準拠していないかの確認のために Intune に対してクエリが実行されます。

  - この設定を削除するには、プロファイルを再作成し、 **[同意する]** は選択しないでください。 次に、プロファイルを再割り当てします。

## <a name="ikev2-settings"></a>IKEv2 設定

これらの設定は、**接続の種類** > **IKEv2**を選択した場合に適用されます。

- **[リモート識別子]** : IKEv2 サーバーのネットワーク IP アドレス、Fqdn、userfqdn、または ASN1DN を入力します。 たとえば、「`10.0.0.3`」や「`vpn.contoso.com`」と入力します。 通常は、[**接続名**](#base-vpn-settings)と同じ値を入力します (この記事をご覧ください)。 ただし、これは IKEv2 サーバーの設定によって異なります。

- **[クライアント認証の種類]** : vpn クライアントが vpn に対して認証する方法を選択します。 次のようなオプションがあります。
  - **ユーザー認証**(既定): ユーザー資格情報が VPN に対して認証されます。
  - **コンピューター認証**: デバイスの資格情報が VPN に対して認証されます。

- **認証方法**: サーバーに送信するクライアント資格情報の種類を選択します。 次のようなオプションがあります。
  - **証明書**: 既存の証明書プロファイルを使用して VPN に対する認証を行います。 この証明書プロファイルがユーザーまたはデバイスに既に割り当てられていることを確認してください。 それ以外の場合、VPN 接続は失敗します。
    - **証明書の種類**: 証明書によって使用される暗号化の種類を選択します。 VPN サーバーがこの種類の証明書を受け入れるように構成されていることを確認してください。 次のようなオプションがあります。
      - **RSA** (既定値)
      - **ECDSA256**
      - **ECDSA384**
      - **ECDSA521**

  - ユーザー**名とパスワード**(ユーザー認証のみ): ユーザーが VPN に接続すると、ユーザー名とパスワードを入力するように求められます。
  - [**共有シークレット**(コンピューター認証のみ)]: VPN サーバーに送信する共有シークレットを入力できます。
    - **[共有シークレット]** : 共有シークレット (事前共有キー (PSK) とも呼ばれます) を入力します。 値が VPN サーバーで構成されている共有シークレットと一致していることを確認してください。

- **サーバー証明書発行者の共通名**: vpn サーバーが vpn クライアントに対して認証できるようにします。 デバイス上の VPN クライアントに送信される VPN サーバー証明書の証明書発行者の共通名 (CN) を入力します。 CN の値が VPN サーバーの構成と一致していることを確認してください。 それ以外の場合、VPN 接続は失敗します。
- **サーバー証明書の共通名**: 証明書の CN を入力します。 空白のままにすると、リモート識別子の値が使用されます。

- **[配信不能ピア検出率]** : vpn トンネルがアクティブであるかどうかを vpn クライアントが確認する頻度を選択します。 次のようなオプションがあります。
  - **未構成**: iOS システムの既定値を使用します。これは、 **[中]** を選択する場合と同じです。
  - **None**: dead ピア検出を無効にします。
  - **Low**:30 分ごとに keepalive メッセージを送信します。
  - **Medium** (既定値):10 分ごとに keepalive メッセージを送信します。
  - **High**:60 秒ごとに keepalive メッセージを送信します。

- **Tls のバージョン範囲の最小値**: 使用する最小 tls バージョンを入力します。 `1.0`、`1.1`、または `1.2`を入力します。 空白のままにすると、`1.0` の既定値が使用されます。
- **Tls のバージョン範囲の最大値**: 使用する tls の最大バージョンを入力します。 `1.0`、`1.1`、または `1.2`を入力します。 空白のままにすると、`1.2` の既定値が使用されます。

> [!NOTE]
> ユーザー認証と証明書を使用する場合は、TLS バージョン範囲の最小値と最大値を設定する必要があります。

- **完全な転送用機密性**: **[有効]** を選択して、完全転送機密性 (PFS) を有効にします。 PFS は、セッションキーが侵害された場合の影響を軽減する IP セキュリティ機能です。 **Disable** (既定値) は PFS を使用しません。
- **証明書失効確認**: VPN 接続を成功させるために証明書が失効していないことを確認するには、[**有効**にする] を選択します。 このチェックはベストエフォートです。 証明書が失効しているかどうかを判断する前に VPN サーバーがタイムアウトした場合は、アクセス権が付与されます。 **無効化**(既定) は、失効した証明書を確認しません。

- **セキュリティアソシエーションパラメーターの構成**: 未構成 (既定) では、iOS システムの既定値が使用**さ**れます。 VPN サーバーとのセキュリティアソシエーションを作成するときに使用するパラメーターを入力するには、[**有効**にする] を選択します。
  - **暗号化アルゴリズム**: 目的のアルゴリズムを選択します。
    - DES
    - 3DES
    - AES-128
    - AES-256 (既定値)
    - AES-128-GCM
    - AES-256-GCM
  - **整合性アルゴリズム**: 必要なアルゴリズムを選択します。
    - SHA1-96
    - SHA1-160
    - SHA2-256 (既定値)
    - SHA2-384
    - SHA2-512
  - **Diffie-hellman グループ**: 目的のグループを選択します。 既定値はグループ `2`です。
  - **有効期間**(分): キーがローテーションされるまで、セキュリティアソシエーションがアクティブなままになる期間を選択します。 `10` と `1440` の間に値全体を入力します (1440 分は24時間です)。 既定値は `1440`です。

- **子セキュリティアソシエーション用に個別のパラメーターセットを構成**する: iOS では、IKE 接続とすべての子接続に対して別々のパラメーターを構成できます。 

  **未構成**(既定) では、 **[セキュリティアソシエーションパラメーターの構成]** 設定で入力した値が使用されます。 VPN サーバーとの*子*セキュリティアソシエーションを作成するときに使用するパラメーターを入力するには、[**有効**にする] を選択します。
  - **暗号化アルゴリズム**: 目的のアルゴリズムを選択します。
    - DES
    - 3DES
    - AES-128
    - AES-256 (既定値)
    - AES-128-GCM
    - AES-256-GCM
  - **整合性アルゴリズム**: 必要なアルゴリズムを選択します。
    - SHA1-96
    - SHA1-160
    - SHA2-256 (既定値)
    - SHA2-384
    - SHA2-512
  - **Diffie-hellman グループ**: 目的のグループを選択します。 既定値はグループ `2`です。
  - **有効期間**(分): キーがローテーションされるまで、セキュリティアソシエーションがアクティブなままになる期間を選択します。 `10` と `1440` の間に値全体を入力します (1440 分は24時間です)。 既定値は `1440`です。

## <a name="automatic-vpn-settings"></a>自動 VPN 設定

- **アプリごとの VPN**:アプリごとの VPN を有効にします。 特定のアプリを開いたときに VPN 接続が自動的にトリガーされるのを許可します。 また、アプリをこの VPN プロファイルに関連付けます。 アプリごとの VPN は IKEv2 ではサポートされていません。 詳細については、[iOS のアプリごとの VPN の設定手順](vpn-setting-configure-per-app.md)に関するページを参照してください。 
  - **プロバイダーの種類**:Pulse Secure と Custom VPN でのみ利用できます。
  - Pulse Secure または Custom VPN を含む iOS の**アプリごとの VPN** プロファイルを使用するときに、アプリ層トンネリング (アプリプロキシ) またはパケット レベル トンネリング (パケットトンネル) を選択できます。 **[ProviderType]** 値には、アプリ層トンネリングの場合は **[app-proxy]** を設定し、パケット層トンネリングの場合は **[packet-tunnel]** を設定します。 使用すべき値がわからない場合、ご利用の VPN プロバイダーのドキュメントを参照してください。
  - **この VPN をトリガーする Safari URL**:1 つまたは複数の Web サイト URL を追加します。 これらの URL にデバイスの Safari ブラウザーを使用してアクセスすると、VPN 接続が自動的に確立されます。

- **オンデマンド VPN**:VPN 接続が開始されるタイミングを制御する条件付き規則を構成します。 たとえば、デバイスが会社の Wi-Fi ネットワークに接続されていない場合にのみ VPN 接続を使用するというような条件を作成します。 または、条件を作成します。 たとえば、入力した DNS 検索ドメインにデバイスがアクセスできない場合には VPN 接続を開始しません。

  - **[SSID または DNS 検索ドメイン]** :この条件でワイヤレス ネットワークの **SSID** を使用するか、**DNS 検索ドメイン**を使用するかを選択します。 1 つ以上の SSID または検索ドメインを構成するには、 **[追加]** を選択します。
  - **[URL 文字列プローブ]** :任意。 ルールがテストとして使う URL を入力します。 デバイスによって、この URL がリダイレクトなしにアクセスされた場合は、VPN 接続が開始されます。 さらに、デバイスがターゲット URL に接続されます。 ユーザーには、URL 文字列プローブ サイトは表示されません。

    たとえば、URL 文字列プローブは、VPN への接続前にデバイスのポリシー準拠を確認する監査 Web サーバーの URL です。 または、URL は、vpn 経由でデバイスをターゲット URL に接続する前に、サイトに接続する VPN の機能をテストします。
。
  - **ドメインのアクション**:以下のいずれかの項目を選択します。
    - 必要な場合に接続する
    - 接続しない
  - **[操作]** :以下のいずれかの項目を選択します。
    - 接続
    - 接続の評価
    - 無視
    - 切断

## <a name="proxy-settings"></a>プロキシの設定

プロキシを使用している場合、次の設定を構成します。 Zscaler VPN 接続の場合、プロキシ設定は利用できません。  

- **[自動構成スクリプト]** :ファイルを使用してプロキシ サーバーを構成します。 構成ファイルが含められている **[プロキシ サーバーの URL]** を入力します (例: `http://proxy.contoso.com`)。
- **[アドレス]** :プロキシ サーバーの完全修飾ホスト名の IP アドレスを入力します。
- **[ポート番号]** :プロキシ サーバーに関連付けられているポート番号を入力します。

## <a name="next-steps"></a>次のステップ

プロファイルは作成されましたが、まだ何も行われていません。 次に、[プロファイルを割り当て](device-profile-assign.md)、[その状態を監視](device-profile-monitor.md)します。

[Android](vpn-settings-android.md)、 [android Enterprise](vpn-settings-android-enterprise.md)、 [macOS](vpn-settings-macos.md)、および[Windows 10](vpn-settings-windows-10.md)デバイスで VPN 設定を構成します。
