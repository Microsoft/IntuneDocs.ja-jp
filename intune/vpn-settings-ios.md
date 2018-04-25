---
title: Microsoft Intune での iOS デバイスに対する VPN の設定 - Azure | Microsoft Docs
description: 使用可能な仮想プライベート ネットワーク (VPN) の構成を示します。iOS を実行するデバイス上の Microsoft Intune での、基本設定での接続の詳細、認証方法、分割トンネリングなど、ID を含むカスタム VPN の設定およびキーと値のペア、Safari URL を含むアプリごとの VPN の設定と SSID または DNS 検索ドメインを含むオンデマンドの VPN、構成スクリプト、IP または FQDN アドレス、TCP ポートを含むプロキシの設定などがあります。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3ce970f942d8ea20eb9ea593c23160757122926e
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="configure-vpn-settings-in-microsoft-intune-for-devices-running-ios"></a>iOS を実行するデバイス用に Microsoft Intune で VPN 設定を構成する

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

この記事では、iOS を実行するデバイスでの VPN 接続の構成に使用できる Intune 設定を示します。

選択した設定によっては、次の一覧に記載されている値の一部を構成できない場合があります。

## <a name="base-vpn-settings"></a>基本 VPN 設定

- **[接続名]**: この接続の名前を入力します。 エンド ユーザーがデバイスで利用可能な VPN 接続の一覧を参照するときに、この名前が表示されます。
- **[IP アドレスまたは FQDN]**: デバイスが接続する VPN サーバーの IP アドレスまたは完全修飾ドメイン名 (FQDN) を入力します。 たとえば、「**192.168.1.1**」や「**vpn.contoso.com**」などと入力します。
- **[認証方法]**: VPN サーバーに対するデバイスの認証方法として、以下のいずれかを選択します。
  - **[証明書]**: **[認証証明書]** で、接続を認証するための既存の SCEP または PKCS 証明書プロファイルを選択します。 [証明書の構成](certificates-configure.md)に関するページでは、証明書プロファイルについてのガイダンスが提供されています。
  - **[ユーザー名とパスワード]**: エンド ユーザーは VPN サーバーにサインインするためにユーザー名とパスワードを入力する必要があります。
- **[接続の種類]**: 以下のベンダーのリストから VPN 接続の種類を選択します。
  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**
  - **SonicWall Mobile Connect**
  - **F5 Edge Client**
  - **Pulse Secure**
  - **Cisco (IPSec)**
  - **Citrix**
  - **Custom VPN**

- **[分割トンネリング]**: **[有効]** または **[無効]** にします。これにより、トラフィックに応じて使用する接続をデバイスが判断できます。 たとえば、ホテルにいるユーザーは、業務ファイルへのアクセスに VPN 接続を使用しますが、通常の Web 閲覧にはホテルの標準ネットワークを使用します。

## <a name="custom-vpn-settings"></a>カスタム VPN 設定

接続の種類として **[カスタム VPN]** を選択した場合は、以下の追加設定も構成します。

- **[VPN 識別子]**: これは使用している VPN アプリの識別子であり、VPN プロバイダーから提供されます。
- **[カスタム VPN 属性に対してキーと値を入力します]**: VPN 接続をカスタマイズする**キー**と**値**を追加またはインポートします。 これらの値も、通常は VPN プロバイダーから提供されます。

## <a name="apps-per-app-vpn-settings"></a>アプリ (アプリごとの VPN) 設定

- **[アプリごとの VPN]**: Safari ブラウザーからのアクセス時に VPN 接続を有効にする URL を使用するには、このオプションを有効にします。 アプリごとの VPN を構成するには、基本 VPN 設定の認証方法として **[証明書]** を選択する必要があります。
  - **[この VPN をトリガーする Safari URL]**: Web サイトの URL を追加する場合に選択します。 これらの URL にアクセスすると、VPN 接続が有効になります。

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

- **[自動構成スクリプト]**: ファイルを使用してプロキシ サーバーを構成します。 構成ファイルが格納されている**プロキシ サーバーの URL** を入力します (例: **http://proxy.contoso.com**)。
- **[アドレス]**: プロキシ サーバーの完全修飾ホスト名の IP アドレスを入力します。
- **[ポート番号]**: プロキシ サーバーに関連付けられているポート番号を入力します。
