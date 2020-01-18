---
title: Microsoft Intune で macOS デバイス向けの VPN 設定を構成する - Azure | Microsoft Docs
description: 仮想プライベートネットワーク (VPN) 構成プロファイルを追加または作成します。これには、接続の詳細、分割トンネリング、識別子を使用したカスタム VPN 設定、キーと値のペア、構成スクリプトを使用したプロキシ設定、IP または FQDN アドレス、の TCP ポートが含まれます。MacOS を実行しているデバイスで Microsoft Intune します。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/09/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e0bb2cb757e944369642807f117683dad3a9805a
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2019
ms.locfileid: "75206263"
---
# <a name="add-vpn-settings-on-macos-devices-in-microsoft-intune"></a>Microsoft Intune で macOS デバイス向けの VPN 設定を追加する



この記事では、macOS を実行するデバイスでの VPN 接続の構成に使用できる Intune 設定を示します。

選択した設定によっては、次の一覧に記載されている値の一部を構成できない場合があります。

## <a name="before-you-begin"></a>始める前に

[デバイス構成プロファイルを作成します](vpn-settings-configure.md)。

> [!NOTE]
> これらの設定は、すべての登録の種類で使用できます。 登録の種類の詳細については、「 [macOS の登録](../enrollment/macos-enroll.md)」を参照してください。

## <a name="base-vpn-settings"></a>基本 VPN 設定

**[接続名]** :この接続の名前を入力します。 エンド ユーザーがデバイスで利用可能な VPN 接続の一覧を参照するときに、この名前が表示されます。
- **[IP アドレスまたは FQDN]** :デバイスが接続される VPN サーバーの IP アドレスまたは完全修飾ドメイン名を指定します。 例:**192.168.1.1**、**vpn.contoso.com**。
- **[認証方法]** :VPN サーバーに対するデバイスの認証方法として、以下のいずれかを選択します。
  - **証明書**: **[認証証明書]** で、接続を認証するために事前に作成した SCEP または PKCS 証明書プロファイルを選択します。 証明書プロファイルの詳細については、[証明書の構成方法](../protect/certificates-configure.md)に関するページを参照してください。
  - **[ユーザー名とパスワード]** :エンド ユーザーは VPN サーバーにログインするためにユーザー名とパスワードを入力する必要があります。
- **接続の種類**:以下のベンダーのリストから VPN 接続の種類を選択します。
  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**
  - **SonicWall Mobile Connect**
  - **F5 Edge Client**
  - **Pulse Secure**
  - **Custom VPN**
- **[分割トンネリング]** :このオプションを **[有効]** または **[無効]** にします。これにより、トラフィックに応じて使用する接続をデバイスが判断できます。 たとえば、ホテルにいるユーザーは、業務ファイルへのアクセスに VPN 接続を使用しますが、通常の Web 閲覧にはホテルの標準ネットワークを使用します。

<!--- **Per-app VPN** - Select this option if you want to associate this VPN connection with an iOS or macOS app so that the connection will be opened when the app is run. You can associate the VPN profile with an app when you assign the software. For more information, see [How to assign and monitor apps](../apps/apps-deploy.md). --->

## <a name="custom-vpn-settings"></a>カスタム VPN 設定

**[カスタム VPN]** を選択した場合は、以下の追加設定を構成します。

- **Vpn 識別子**: 使用している vpn アプリの識別子を入力します。 この識別子は、VPN プロバイダーによって指定されます。
- **[カスタム VPN 属性に対してキーと値を入力します]** :VPN 接続をカスタマイズするための**キー**と**値**を追加またはインポートします。 これらの値は、通常は VPN プロバイダーから提供されます。

## <a name="proxy-settings"></a>プロキシの設定

- **[自動構成スクリプト]** :ファイルを使用してプロキシ サーバーを構成します。 構成ファイルを含む**プロキシ サーバー URL** を入力します。 たとえば、「`http://proxy.contoso.com`」と入力します。
- **[アドレス]** :プロキシ サーバーのアドレスを (IP アドレスとして) 入力します。
- **[ポート番号]** :プロキシ サーバーに関連付けられているポート番号を入力します。

## <a name="next-steps"></a>次のステップ

プロファイルは作成されましたが、まだ何も行われていません。 次に、[プロファイルを割り当て](device-profile-assign.md)、[その状態を監視](device-profile-monitor.md)します。

[Android](vpn-settings-android.md)、 [android Enterprise](vpn-settings-android-enterprise.md)、 [iOS](vpn-settings-ios.md)、および[Windows 10](vpn-settings-windows-10.md)デバイスで VPN 設定を構成します。
