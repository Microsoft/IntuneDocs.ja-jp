---
title: ネットワーク アクセス制御と Microsoft Intune - Azure の統合 | Microsoft Docs
description: ネットワーク アクセス制御 (NAC) ソリューションでは、Intune でデバイスの登録とコンプライアンスをチェックします。 NAC には特定の動作が含まれ、条件付きアクセスと連携します。 オンボードの手順を確認し、パートナー ソリューションの一覧を取得します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/18/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: aa7ecff7-8579-4009-8fd6-e17074df67de
ms.reviewer: davidra
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: bdf6b5b71c71dd8b1a9a5c9154953d1ebc07d0dc
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="network-access-control-nac-integration-with-intune"></a>ネットワーク アクセス制御 (NAC) と Intune の統合

Intune はネットワーク アクセス制御パートナーと統合して、デバイスがオンプレミスのリソースにアクセスするときに、会社のデータが保護されるようにします。

## <a name="how-do-intune-and-nac-solutions-help-protect-your-organization-resources"></a>Intune と NAC ソリューションが組織のリソースを保護する方法

NAC ソリューションでは、Intune でデバイスの登録とコンプライアンスの状態をチェックして、アクセス制御の決定を行います。 デバイスが登録されていない場合、または登録されていても Intune のデバイス コンプライアンス ポリシーに準拠していない場合は、登録および/またはデバイスのコンプライアンス チェックのために、デバイスを Intune にリダイレクトする必要があります。

### <a name="example"></a>例

デバイスが登録されていて Intune に準拠している場合は、NAC ソリューションはデバイスによる会社リソースへのアクセスを許可する必要があります。 たとえば、会社の Wi-Fi リソースまたは VPN リソースにアクセスしようとするユーザーを許可または拒否することができます。

## <a name="feature-behaviors"></a>機能の動作

Intune とアクティブに同期しているデバイスは、**準拠** / **非準拠**から**未同期** (または**不明**) に移動することはできません。 **不明**の状態は、コンプライアンス対応状態がまだ評価されていない、新たに登録されたデバイスであることを示しています。

リソースへのアクセスがブロックされているデバイスの場合、ブロックしているサービスが、すべてのユーザーを[管理ポータル](https://portal.manage.microsoft.com)にリダイレクトし、デバイスがブロックされている理由を特定します。  ユーザーがこのページにアクセスすると、デバイスのコンプライアンス対応状態が、同期的に再評価されます。

## <a name="nac-and-conditional-access"></a>NAC と条件付きアクセス

NAC は条件付きアクセスと連携して、アクセス制御の決定を提供します。 詳細については、「[Intune での条件付きアクセスの一般的な使用方法](conditional-access-intune-common-ways-use.md)」を参照してください。

## <a name="how-the-nac-integration-works"></a>NAC 統合のしくみ

以下の一覧には、Intune と統合されたときの NAC 統合のしくみの概要が示されています。 最初の 3 つの手順 (1 - 3) では、オンボード プロセスについて説明します。 手順 4 から 9 では、NAC ソリューションが Intune と統合された後の継続的な動作について説明します。

![NAC が Intune と連携する方法](./media/ca-intune-common-ways-2.png)

1. NAC パートナー ソリューションを Azure Active Directory (AAD) に登録し、Intune NAC API への委任されたアクセス許可を付与します。
2. Intune 検出 URL などの適切な設定で、NAC パートナー ソリューションを構成します。
3. 証明書認証用に NAC パートナー ソリューションを構成します。
4. ユーザーが、会社の Wi-Fi アクセス ポイントに接続するか、VPN 接続要求を行います。
5. NAC パートナー ソリューションは、Intune にデバイス情報を転送し、デバイスの登録とコンプライアンスの状態を Intune に問い合わせます。
6. デバイスが準拠していないか、登録されていない場合は、NAC パートナー ソリューションはユーザーに登録またはデバイスのコンプライアンスの修正を指示します。
7. デバイスは、コンプライアンスおよび登録状態の再検証を試みます。
8. デバイスが登録されて準拠するようになると、NAC パートナー ソリューションは Intune から状態を取得します。
9. 接続が正常に確立されて、デバイスは会社のリソースにアクセスできるようになります。

## <a name="next-steps"></a>次の手順

- [Cisco ISE と Intune を統合する](http://www.cisco.com/c/en/us/td/docs/security/ise/2-1/admin_guide/b_ise_admin_guide_21/b_ise_admin_guide_20_chapter_01000.html)
- [Citrix NetScaler と Intune を統合する](http://docs.citrix.com/en-us/netscaler-gateway/12/microsoft-intune-integration/configuring-network-access-control-device-check-for-netscaler-gateway-virtual-server-for-single-factor-authentication-deployment.html)
- [HP Aruba Clear Pass と Intune を統合する](https://support.arubanetworks.com/Documentation/tabid/77/DMXModule/512/Command/Core_Download/Default.aspx?EntryId=23757)
- [Squadra の secRMM (security Removable Media Manager) と Intune を統合する](http://www.squadratechnologies.com/StaticContent/ProductDownload/secRMM/9.9.0.0/secRMMIntuneAccessControlSetupGuide.pdf)