---
title: ネットワーク アクセス制御と Microsoft Intune - Azure の統合 | Microsoft Docs
description: ネットワーク アクセス制御 (NAC) ソリューションでは、Intune でデバイスの登録とコンプライアンスをチェックします。 NAC には特定の動作が含まれ、条件付きアクセスと連携します。 オンボードの手順を確認し、パートナー ソリューションの一覧を取得します。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 04/25/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: aa7ecff7-8579-4009-8fd6-e17074df67de
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 142d24452c401f83322b71a104ed47759eb6179f
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509096"
---
# <a name="network-access-control-nac-integration-with-intune"></a>ネットワーク アクセス制御 (NAC) と Intune の統合

Intune はネットワーク アクセス制御パートナーと統合して、デバイスがオンプレミスのリソースにアクセスするときに、会社のデータが保護されるようにします。

## <a name="how-do-intune-and-nac-solutions-help-protect-your-organization-resources"></a>Intune と NAC ソリューションが組織のリソースを保護する方法

NAC ソリューションでは、Intune でデバイスの登録とコンプライアンスの状態をチェックして、アクセス制御の決定を行います。 デバイスが登録されていない場合、または登録されていても Intune のデバイス コンプライアンス ポリシーに準拠していない場合は、登録またはデバイスのコンプライアンス チェックのために、そのデバイスを Intune にリダイレクトする必要があります。

### <a name="example"></a>例

デバイスが登録されていて Intune に準拠している場合は、NAC ソリューションはデバイスによる会社リソースへのアクセスを許可する必要があります。 たとえば、会社の Wi-Fi リソースまたは VPN リソースにアクセスしようとするユーザーを許可または拒否することができます。

## <a name="feature-behaviors"></a>機能の動作

Intune とアクティブに同期しているデバイスは、**準拠** / **非準拠**から**未同期** (または**不明**) に移動することはできません。 **不明**の状態は、コンプライアンス対応状態がまだ評価されていない、新たに登録されたデバイスであることを示しています。

リソースへのアクセスがブロックされているデバイスの場合、ブロックしているサービスが、すべてのユーザーを[管理ポータル](https://portal.manage.microsoft.com)にリダイレクトし、デバイスがブロックされている理由を特定します。  ユーザーがこのページにアクセスすると、デバイスのコンプライアンス対応状態が、同期的に再評価されます。

## <a name="nac-and-conditional-access"></a>NAC と条件付きアクセス

NAC は条件付きアクセスと連携して、アクセス制御の決定を提供します。 詳細については、「[Intune での条件付きアクセスの一般的な使用方法](conditional-access-intune-common-ways-use.md)」を参照してください。

## <a name="how-the-nac-integration-works"></a>NAC 統合のしくみ

以下の一覧には、Intune と統合されたときの NAC 統合のしくみの概要が示されています。 最初の 3 つの手順 (1 - 3) では、オンボード プロセスについて説明します。 手順 4 から 9 では、NAC ソリューションが Intune と統合された後の継続的な動作について説明します。

![NAC が Intune と連携する方法の概念図](./media/network-access-control-integrate/ca-intune-common-ways-2.png)

1. NAC パートナー ソリューションを Azure Active Directory (AAD) に登録し、Intune NAC API への委任されたアクセス許可を付与します。
2. Intune 検出 URL などの適切な設定で、NAC パートナー ソリューションを構成します。
3. 証明書認証用に NAC パートナー ソリューションを構成します。
4. ユーザーが、会社の Wi-Fi アクセス ポイントに接続するか、VPN 接続要求を行います。
5. NAC パートナー ソリューションは、Intune にデバイス情報を転送し、デバイスの登録とコンプライアンスの状態を Intune に問い合わせます。
6. デバイスが準拠していないか、登録されていない場合は、NAC パートナー ソリューションはユーザーに登録またはデバイスのコンプライアンスの修正を指示します。
7. デバイスは、該当する場合にそのコンプライアンスおよび登録状態の再検証を試みます。
8. デバイスが登録されて準拠するようになると、NAC パートナー ソリューションは Intune から状態を取得します。
9. 接続が正常に確立されて、デバイスは会社のリソースにアクセスできるようになります。

## <a name="use-nac-for-vpn-on-your-ios-devices"></a>iOS デバイス上で VPN 用に NAC を使用する  

- NAC を VPN プロファイルで有効にしなくても、NAC は次の VPN で使用できます。

  - NAC for Cisco Legacy AnyConnect
  - F5 Access Legacy
  - Citrix VPN

- NAC は、Citrix SSO および F5 Access でも使用できます。 Citrix SSO で NAC を有効にするには:

  - Citrix ゲートウェイ 12.0.59 以上を使用します。  
  - ユーザーは Citrix SSO 1.1.6 以降をインストールしている必要があります。
  - Citrix の製品ドキュメントの説明に従って、[NAC のために NetScaler を Inture と統合します](https://docs.citrix.com/en-us/netscaler-gateway/12/microsoft-intune-integration/configuring-network-access-control-device-check-for-netscaler-gateway-virtual-server-for-single-factor-authentication-deployment.html)。
  - VPN プロファイルで **[Base setting]** \(基本設定\) >  **[ネットワーク アクセス制御 (NAC) を有効にする]** を選択し、 **[同意する]** を選択します。

  VPN 接続は、セキュリティ上の理由により 24 時間ごとに切断されます。 VPN はすぐに再接続できます。

- F5 Access で NAC を有効にするには:

  - F5 BIG-IP 13.1.1.5 を使用します。 BIG-IP 14 はサポートされていません。
  - NAC 用に Intune に BIG-IP を統合します。 「[Overview:Configuring APM for device posture checks with endpoint management systems](https://support.f5.com/kb/en-us/products/big-ip_apm/manuals/product/apm-client-configuration-7-1-6/6.html#guid-0bd12e12-8107-40ec-979d-c44779a8cc89)」 (エンドポイント管理システムを使用したデバイス ポスチャ チェック用の APM の構成) の F5 のガイドに手順があります。
  - VPN プロファイルで **[Base setting]** \(基本設定\) >  **[ネットワーク アクセス制御 (NAC) を有効にする]** を選択し、 **[同意する]** を選択します。

  VPN 接続は、セキュリティ上の理由により 24 時間ごとに切断されます。 VPN はすぐに再接続できます。

- iOS 上の次の VPN クライアントでは、ネットワーク アクセス制御はサポートされていません。
  - Cisco AnyConnect

これらの新しいクライアント用の NAC ソリューションをリリースするために、パートナーと協力して作業しています。 この記事は、ソリューションの準備が整ったら、情報を追加して更新されます。

## <a name="next-steps"></a>次の手順

- [Cisco ISE と Intune を統合する](https://www.cisco.com/c/en/us/td/docs/security/ise/2-1/admin_guide/b_ise_admin_guide_21/b_ise_admin_guide_20_chapter_01000.html)
- [Citrix NetScaler と Intune を統合する](https://docs.citrix.com/en-us/netscaler-gateway/12/microsoft-intune-integration/configuring-network-access-control-device-check-for-netscaler-gateway-virtual-server-for-single-factor-authentication-deployment.html)
- [Intune に F5 BIG-IP Access Policy Manager を統合する](https://support.f5.com/kb/en-us/products/big-ip_apm/manuals/product/apm-client-configuration-13-0-0/6.html)
- [HP Aruba ClearPass と Intune を統合する](https://support.arubanetworks.com/Documentation/tabid/77/DMXModule/512/Command/Core_Download/Default.aspx?EntryId=31271)
- [Squadra の secRMM (security Removable Media Manager) と Intune を統合する](http://www.squadratechnologies.com/StaticContent/ProductDownload/secRMM/9.9.0.0/secRMMIntuneAccessControlSetupGuide.pdf)
