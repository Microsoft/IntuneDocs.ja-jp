---
title: "iOS デバイス向けの Intune VPN 設定"
titlesuffix: Azure portal
description: "iOS デバイスでの VPN 接続の構成に使用できる Intune 設定について説明します。\""
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1447c123-ea33-4ea0-aab4-69577cdb8d00
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 27b29c7e7dd256484763b9a0cbe9e76f32fe74d8
ms.sourcegitcommit: 3b397b1dcb780e2f82a3d8fba693773f1a9fcde1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/12/2017
---
# <a name="vpn-settings-for-ios-devices-in-microsoft-intune"></a>Microsoft Intune での iOS デバイス向けの VPN 設定

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

選択した設定によっては、次の一覧に記載されている値の一部を構成できない場合があります。

## <a name="base-vpn-settings"></a>基本 VPN 設定


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
    - **Cisco (IPSec)**
    - **Citrix**
    - **Custom VPN**
- **[分割トンネリング]**  -  このオプションを **[有効]** または **[無効]** にします。これを有効にすると、使用する接続をトラフィックに応じてデバイスが判断するようになります。 たとえば、ホテルにいるユーザーは、業務ファイルへのアクセスに VPN 接続を使用しますが、通常の Web 閲覧にはホテルの標準ネットワークを使用します。


## <a name="custom-vpn-settings"></a>カスタム VPN 設定

接続の種類として **[カスタム VPN]** を選択した場合は、以下の追加設定を構成します。

- **[VPN 識別子]** - これは使用している VPN アプリの識別子であり、VPN プロバイダーから提供されます。
- **[カスタム VPN 属性に対してキーと値を入力します]** - VPN 接続をカスタマイズする**キー**と**値**を追加またはインポートします。 これらの値も、通常は VPN プロバイダーから提供されます。

## <a name="apps-per-app-vpn-settings"></a>アプリ (アプリごとの VPN) 設定

- **[アプリごとの VPN]** - Safari ブラウザーからのアクセス時に VPN 接続を有効にする URL が必要な場合は、このオプションを有効にします。 これを構成するには、基本 VPN 設定の認証方法として **[証明書]** を選択している必要があります。
- **[Safari ブラウザーを使用しているときに VPN 接続を有効にする URL を指定します]** - [追加] をクリックして 1 つ以上の Web サイト URL を追加します。 これらの URL にアクセスすると、VPN 接続が有効になります。

- **[On-demand rules (オンデマンド ルール)]** - この設定を使用すると、VPN 接続が開始されるタイミングを制御する条件付き規則を構成できます。 たとえば、デバイスが会社の Wi-Fi ネットワークに接続されていない場合にのみ VPN 接続を使用するというような条件を作成できます。 また、指定した DNS 検索ドメインにデバイスがアクセスできない場合には VPN 接続を開始しないといった条件を作成することもできます。

    - **[SSID または DNS 検索ドメイン]** - この条件でワイヤレス ネットワークの **SSID** を使用するか、**DNS 検索ドメイン**を使用するかを選択します。 1 つ以上の SSID または検索ドメインを構成するには、[追加] を選択します。
    - **[URL 文字列プローブ]** - 必要に応じて、規則によってテストとして使用する URL を指定します。 このプロファイルがインストールされているデバイスがリダイレクトなしでこの URL にアクセスできる場合は、VPN 接続が開始され、デバイスがターゲット URL に接続されます。 ユーザーには、URL 文字列プローブ サイトは表示されません。 URL 文字列プローブの例としては、VPN への接続前にデバイスのポリシー準拠を確認する監査 Web サーバーのアドレスがあります。 別の例としては、デバイスを VPN 経由でターゲット URL に接続する前に、サイトに接続する VPN の機能をテストする URL があります。
    - **[ドメインのアクション]** - 以下のいずれかの項目を選択します。
        - [必要な場合に接続する] 
        - [接続しない] 
    - **[アクション]** - 以下のいずれかの項目を選択します。
        - [接続] 
        - [接続の評価] 
        - [無視] 
        - [切断] 


## <a name="proxy-settings"></a>プロキシの設定

- **[自動構成スクリプト]** - ファイルを使用してプロキシ サーバーを構成します。 構成ファイルが格納されている**プロキシ サーバーの URL** を入力します (たとえば、**http://proxy.contoso.com**)。
- **[アドレス]** - プロキシ サーバーのアドレスを (IP アドレスとして) 入力します。
- **[ポート番号]** - プロキシ サーバーに関連付けられているポート番号を入力します。