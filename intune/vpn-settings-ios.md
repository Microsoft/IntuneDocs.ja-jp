---
title: Microsoft Intune での iOS デバイスに対する VPN の設定 - Azure | Microsoft Docs
description: 使用可能な仮想プライベート ネットワーク (VPN) の構成を示します。iOS を実行するデバイス上の Microsoft Intune での、基本設定での接続の詳細、認証方法、分割トンネリングなど、ID を含むカスタム VPN の設定およびキーと値のペア、Safari URL を含むアプリごとの VPN の設定と SSID または DNS 検索ドメインを含むオンデマンドの VPN、構成スクリプト、IP または FQDN アドレス、TCP ポートを含むプロキシの設定などがあります。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 8/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: deb6a230573ff20237e6eee386052baba472832a
ms.sourcegitcommit: 4d314df59747800169090b3a870ffbacfab1f5ed
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/30/2018
ms.locfileid: "43313872"
---
# <a name="configure-vpn-settings-in-microsoft-intune-for-devices-running-ios"></a>iOS を実行するデバイス用に Microsoft Intune で VPN 設定を構成する

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

この記事では、iOS を実行するデバイスでの VPN 接続の構成に使用できる Intune 設定を示します。

選択した設定によっては、次の一覧に記載されている値の一部を構成できない場合があります。

## <a name="base-vpn-settings"></a>基本 VPN 設定
以下の一覧にある設定のうち、実際に表示される設定は、選択した VPN 接続の種類によって決まります。  
- **[接続名]**: エンド ユーザーがデバイスで利用可能な VPN 接続の一覧を参照するときに、この名前が表示されます。
- **[カスタム ドメイン名]** (Zscaler のみ): Zscaler アプリのサインイン フィールドに、ユーザーが属するドメインが事前入力されます。 たとえば、ユーザー名が **Joe@contoso.net** であれば、アプリを開いたとき、フィールドにドメイン **contoso.net** が固定値として表示されます。 ドメイン名を入力しない場合、Azure Active Directory に登録されている UPN のドメイン部分が使用されます。
- **[IP アドレスまたは FQDN]**: デバイスが接続する VPN サーバーの IP アドレスまたは完全修飾ドメイン名 (FQDN)。 たとえば、「**192.168.1.1**」や「**vpn.contoso.com**」などと入力します。 
- **[組織のクラウド名]** (Zscaler のみ): 組織がプロビジョニングされているクラウドの名前を入力します。 名前を見つけるには、Zscaler へのサインインに使用する URL を調べます。  
- **[認証方法]**: VPN サーバーに対するデバイスの認証方法として、以下のいずれかを選択します。 
  - **[証明書]**: **[認証証明書]** で、接続を認証するための既存の SCEP または PKCS 証明書プロファイルを選択します。 「[証明書の構成](certificates-configure.md)」では、証明書プロファイルについてのガイダンスが提供されています。
  - **[ユーザー名とパスワード]**: エンド ユーザーは VPN サーバーにサインインするためにユーザー名とパスワードを入力する必要があります。  

    > [!NOTE]
    > Cisco IPsec VPN の認証方法としてユーザー名とパスワードが使われている場合は、カスタム Apple Configurator プロファイルで SharedSecret を配布する必要があります。
  
- **[接続の種類]**: 以下のベンダーのリストから VPN 接続の種類を選択します。
  - **Check Point Capsule VPN**
  - **[Cisco Legacy AnyConnect]**: 4.0.5x 以前のバージョンの [Cisco Legacy AnyConnect](https://itunes.apple.com/app/cisco-legacy-anyconnect/id392790924) アプリに適用できます。
  - **[Cisco AnyConnect]**: 4.0.7x 以降のバージョンの [Cisco AnyConnect](https://itunes.apple.com/app/cisco-anyconnect/id1135064690) アプリに適用できます。
  - **SonicWall Mobile Connect**
  - **[F5 Access Legacy]**: バージョンが 2.1 以前の F5 Access アプリに適用できます。
  - **[F5 Access]**: バージョンが 3.0 以降の F5 Access アプリに適用できます。
  - **[Palo Alto Networks GlobalProtect (Legacy)]**: バージョンが 4.1 以前の Palo Alto Networks GlobalProtect アプリに適用できます。
  - **[Palo Alto Networks GlobalProtect]**: バージョンが 5.0 以降の Palo Alto Networks GlobalProtect アプリに適用できます。
  - **Pulse Secure**
  - **Cisco (IPSec)**
  - **Citrix VPN**
  - **Citrix SSO**
  - **[Zscaler]**: Zscaler Private Access (ZPA) とお使いの Azure Active Directory アカウントを統合することが必要になります。 詳しい手順については、[Zscaler ドキュメント](https://help.zscaler.com/zpa/configuration-example-microsoft-azure-ad#Azure_UserSSO)をご覧ください。 
  - **Custom VPN**    

    > [!NOTE]
    > Cisco、Citrix、F5、Palo Alto については、これからリリースされる iOS 12 ではレガシー クライアントが動作しないことが発表されています。 できるだけ早く、新しいアプリに移行してください。 詳細については、[Microsoft Intune サポート チームのブログ](https://go.microsoft.com/fwlink/?linkid=2013806&clcid=0x409)を参照してください。

* **[除外された URL]** (Zscaler のみ): Zscaler VPN に接続されると、一覧にある URL には Zscaler クラウドの外からアクセスできます。 

- **[分割トンネリング]**: **[有効]** または **[無効]** にします。これにより、トラフィックに応じて使用する接続がデバイスで判断されます。 たとえば、ホテルにいるユーザーは、業務ファイルへのアクセスに VPN 接続を使用しますが、通常の Web 閲覧にはホテルの標準ネットワークを使用します。   

## <a name="custom-vpn-settings"></a>カスタム VPN 設定

接続の種類として **[カスタム VPN]** を選択した場合、以下の追加設定を構成します。 Zscaler 接続と Citrix 接続でも、これらの設定が表示されます。

- **[VPN 識別子]**: これは使用している VPN アプリの識別子であり、VPN プロバイダーから提供されます。
- **[Enter key/value pairs for your organization's custom VPN attributes]\(組織のカスタム VPN 属性に対してキーと値のペアを入力します\)**: VPN 接続をカスタマイズする**キー**と**値**を追加またはインポートします。 これらの値も、通常は VPN プロバイダーから提供されます。

## <a name="automatic-vpn-settings"></a>自動 VPN 設定

- **[アプリごとの VPN]**: このオプションを選択すると、アプリごとの VPN が有効になり、特定のアプリが開いたときに自動的に VPN 接続がトリガされるようにできます。 このオプションを選択するだけでなく、アプリをこの VPN プロファイルに関連付ける必要があります。 詳細については、[iOS のアプリごとの VPN の設定手順](vpn-setting-configure-per-app.md)に関するページを参照してください。 
  - **[プロバイダーの種類]** 設定は、Pulse Secure と Custom VPN でのみ利用できます。
  - Pulse Secure または Custom VPN を含む iOS の**アプリごとの VPN** プロファイルを使用するときに、アプリ層トンネリング (アプリプロキシ) またはパケット レベル トンネリング (パケットトンネル) を使用することを選択できます。 **[ProviderType]** 値に、アプリ層トンネリングには **[app-proxy]** を設定し、パケット層トンネリングには **[packet-tunnel]** を設定します。使用する値がわからない場合、VPN プロバイダーのドキュメントを参照してください。 
  - **[この VPN をトリガーする Safari URL]**: Web サイトの URL を追加する場合に選択します。 これらの URL にデバイスの Safari ブラウザーを使用してアクセスすると、VPN 接続が自動的に確立されます。

- **[オンデマンド VPN]**- VPN 接続が開始されるタイミングを制御する条件付き規則を構成します。 たとえば、デバイスが会社の Wi-Fi ネットワークに接続されていない場合にのみ VPN 接続を使用するというような条件を作成します。 または、指定した DNS 検索ドメインにデバイスがアクセスできない場合には VPN 接続を開始しないといった条件を作成します。

  - **[SSID または DNS 検索ドメイン]**: この条件でワイヤレス ネットワークの **SSID** を使用するか、**DNS 検索ドメイン**を使用するかを選択します。 1 つ以上の SSID または検索ドメインを構成するには、**[追加]** を選択します。
  - **[URL string probe]\(URL 文字列プローブ\)**: 省略可能です。 ルールがテストとして使う URL を入力します。 このプロファイルがインストールされているデバイスがリダイレクトなしでこの URL にアクセスできる場合は、VPN 接続が開始され、デバイスがターゲット URL に接続されます。 ユーザーには、URL 文字列プローブ サイトは表示されません。 URL 文字列プローブの例としては、VPN への接続前にデバイスのポリシー準拠を確認する監査 Web サーバーのアドレスがあります。 別の例としては、デバイスを VPN 経由でターゲット URL に接続する前に、サイトに接続する VPN の機能をテストする URL があります。
  - **[ドメインのアクション]**: 以下のいずれかの項目を選択します。
    - 必要な場合に接続する
    - 接続しない
  - **[アクション]**: 以下のいずれかの項目を選択します。
    - 接続
    - 接続の評価
    - 無視
    - 切断

## <a name="proxy-settings"></a>プロキシの設定
プロキシを使用している場合、次の設定を構成します。 Zscaler VPN 接続の場合、プロキシ設定は利用できません。  

- **[自動構成スクリプト]**: ファイルを使用してプロキシ サーバーを構成します。 構成ファイルが格納されている**プロキシ サーバーの URL** を入力します (例: **http://proxy.contoso.com**)。
- **[アドレス]**: プロキシ サーバーの完全修飾ホスト名の IP アドレスを入力します。
- **[ポート番号]**: プロキシ サーバーに関連付けられているポート番号を入力します。

## <a name="next-step"></a>次の手順
[Intune で VPN プロファイルを作成する](vpn-settings-configure.md)  
