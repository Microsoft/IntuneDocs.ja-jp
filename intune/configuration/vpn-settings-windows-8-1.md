---
title: Microsoft Intune で Windows 8.1 デバイスでの VPN 設定を構成する - Azure | Microsoft Docs
description: 仮想プライベートネットワーク (VPN) 構成設定を使用して VPN 構成プロファイルを追加または作成します。これには、接続の詳細や、IP アドレスまたは FQDN アドレスを含めるためのプロキシ設定、Windows 8.1 を実行しているデバイスの Microsoft Intune の TCP ポートなどが含まれます。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/19/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9f9a1399d5474d79ac8fd48a8aa3a844f20eb640
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207045"
---
# <a name="add-vpn-settings-on-windows-81-devices-in-microsoft-intune"></a>Microsoft Intune で Windows 8.1 デバイスでの VPN 設定を追加する



この記事では、Windows 8.1 を実行するデバイスでの VPN 接続の構成に使用できる Intune 設定を示します。

選択した設定によっては、次の一覧に記載されている値の一部を構成できない場合があります。

## <a name="base-vpn-settings"></a>基本 VPN 設定

- **すべての設定を Windows 8.1 に適用する**: Intune クラシックポータルでこの設定を構成します。 Microsoft Endpoint Manager 管理センターでは、この設定を変更することはできません。 **[構成済み]** に設定されている場合は、すべての設定が Windows 8.1 デバイスのみに適用されます。 **[未構成]** に設定されている場合、これらの設定は Windows 10 デバイスにも適用されます。
- **[接続名]** :この接続の名前を入力します。 ユーザーがデバイスで使用可能な VPN 接続の一覧を参照するときに、この名前が表示されます。
- **サーバー**: デバイスの接続先となる 1 台以上の VPN サーバーを追加します。
  - **[追加]** : **[行の追加]** ページが開き、以下の情報を指定できます。
    - **説明**:**Contoso VPN サーバー**のような、サーバーを表す名前を指定します。
    - **[IP アドレスまたは FQDN]** :デバイスが接続される VPN サーバーの IP アドレスまたは完全修飾ドメイン名を指定します。 例:**192.168.1.1**、**vpn.contoso.com**。
    - **[既定のサーバー]** :このサーバーを、デバイスで接続を確立するために使用する既定のサーバーとして有効にします。 既定のサーバーとして設定するサーバーの数は 1 台のみにしてください。
  - **インポート**: 説明、IP アドレスまたは FQDN、既定のサーバーという形式のサーバーのリストを含む、コンマ区切りのファイルを参照します。 **[OK]** を選んで、これらのサーバーを **[サーバー]** 一覧にインポートします。
  - **エクスポート**:サーバーのリストをコンマ区切り値 (csv) ファイルにエクスポートします。

- **接続の種類**:以下のベンダーのリストから VPN 接続の種類を選択します。
  - **Check Point Capsule VPN**
  - **SonicWall Mobile Connect**
  - **F5 Edge Client**
  - **Pulse Secure**

<!--- **Fingerprint** (Check Point Capsule VPN only): Specify a string (for example, "Contoso Fingerprint Code") that will be used to verify that the VPN server can be trusted. A fingerprint can be sent to the client so it knows to trust any server that presents the same fingerprint when connecting. If the device doesn’t already have the fingerprint, it will prompt the user to trust the VPN server that they are connecting to while showing the fingerprint. (The user manually verifies the fingerprint and chooses **trust** to connect.) --->

- **[ログイン グループまたはドメイン]** (SonicWall Mobile Connect のみ):接続するログイン グループまたはドメインの名前を指定します。

- **[ロール]** (Pulse Secure のみ):この接続に対するアクセス権を持つユーザー ロールの名前を指定します。 ユーザー ロールを使用して、個人の設定とオプションを定義し、特定のアクセス機能を有効または無効にします。

- **[領域]** (Pulse Secure のみ):使用する認証領域の名前を指定します。 認証領域とは、接続の種類が [Pulse Secure] の場合に使用される認証リソースのグループを表します。

- **[カスタム XML]** :VPN 接続を構成する任意のカスタム XML コマンドを指定します。

  **Pulse Secure の例**:

  ```xml
  <pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>
  ```

  **CheckPoint Mobile VPN の例**:

  ```xml
  <CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />
  ```

  **SonicWall Mobile Connect の例**:

  ```xml
  <MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>
  ```

  **F5 Edge Client の例**:

  ```xml
  <f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>
  ```

  カスタム XML コマンドの作成方法については、製造元の VPN ドキュメントをご覧ください。

## <a name="proxy-settings"></a>プロキシの設定

- **[自動的にプロキシ設定を検出する]** :VPN サーバーが接続にプロキシ サーバーを必要とする場合は、デバイスで接続の設定を自動的に検出するかどうかを指定します。
- **[自動構成スクリプト]** :ファイルを使用してプロキシ サーバーを構成します。 構成ファイルを含む**プロキシ サーバー URL** を入力します。 たとえば、「`http://proxy.contoso.com`」と入力します。
- **[プロキシ サーバーを使用する]** :プロキシ サーバーの設定を手動で入力する場合は、このオプションを有効にします。
  - **[アドレス]** :プロキシ サーバーのアドレスを (IP アドレスとして) 入力します。
  - **[ポート番号]** :プロキシ サーバーに関連付けられているポート番号を入力します。
- **[ローカル アドレスにはプロキシ サーバーを使用しない]** :VPN サーバーが接続にプロキシ サーバーを必要とする場合に、入力したローカル アドレスに対してプロキシ サーバーを使用しないようにするには、このオプションを選択します。

## <a name="next-steps"></a>次のステップ

プロファイルは作成されましたが、まだ何も行われていません。 次に、[プロファイルを割り当て](device-profile-assign.md)、[その状態を監視](device-profile-monitor.md)します。

[Android](vpn-settings-android.md)、 [android Enterprise](vpn-settings-android-enterprise.md)、 [macOS](vpn-settings-macos.md)、および[Windows 10](vpn-settings-windows-10.md)デバイスで VPN 設定を構成します。
