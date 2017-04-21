---
title: "モバイル デバイス管理 (MDM) に Intune を準備する | Microsoft Docs"
description: "この記事は、Intune への移行前にビジネス要件と技術的要件を評価するうえで役立ちます。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 58591442-6606-4f39-a06b-f17a1f25af25
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: ab6d9b6b296fb4e1fb0aaa9496fede28976728dc
ms.openlocfilehash: 4bf9bd15f3f22e0609c4f56f5651454a62dbb7a8
ms.lasthandoff: 04/14/2017


---

# <a name="phase-1-prepare-intune-for-mobile-device-management-mdm"></a>フェーズ 1: モバイル デバイス管理 (MDM) に Intune を準備する

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

Intune の設定の詳細について説明する前に、組織のモバイル デバイス管理の要件を確認しておきましょう。 現在の MDM プロバイダーでのアクティブ ユーザーに関するレポートを実施すると、重要なユーザー グループの特定に役立ち、「[MDM 要件を評価する](https://docs.microsoft.com/intune/plan-design/migration-phase1-prepare-intune-for-mobile-device-management#assess-mdm-requirements)」の質問に答えることができます。

## <a name="assess-mdm-requirements"></a>MDM 要件を評価する

### <a name="what-kinds-of-devices-do-you-need-to-manage"></a>管理が必要なデバイスの種類について

-   どの[プラットフォーム](https://docs.microsoft.com/intune/get-started/supported-mobile-devices-and-computers)をサポートする必要がありますか。

-   サポートする必要があるのは、企業所有デバイスまたは BYOD ですか。

-   どのような種類の接続を使用しますか。 Wi-Fi、移動体通信、VPN ですか。

### <a name="what-do-your-users-need-to-do-on-managed-devices"></a>管理対象デバイスでユーザーが行う作業

-   エンド ユーザーにアプリをプロビジョニングする必要がありますか。

-   カスタムの基幹業務アプリを使用しますか。 それともパブリックなストア アプリのみ必要ですか。

-   電子メール アカウントをプロビジョニングする必要がありますか。

### <a name="what-kinds-of-users"></a>ユーザーの種類について

-   1 つのデバイスを使用するユーザー数は何人ですか。

-   どのような使用条件が必要ですか。

    -   これについては早い段階で法務部門が関与するようにします。

    -   どのようなローカライズが必要ですか。

-   一般的に、ユーザーは技術と IT についてよく理解していますか。

### <a name="what-is-your-device-security-policy"></a>デバイスのセキュリティ ポリシーについて

-   デバイス レベルの暗号化が必要ですか。

-   デバイスのパスコード/PIN コードの長さはどうですか。

-   デバイスの機能を無効にしたり、特定のデバイスの動作を制限する必要がありますか。

    -   デバイス構成プロファイルを使用して、プラットフォーム固有のさまざまな設定を制御することができます (例: カメラの無効化、単一アプリ モードへのロック)。
<br></br>
-   どのような種類の認証をサポートする必要がありますか。

    -   証明書ベースの認証が必要な場合、どのような種類の証明書をプロビジョニングする必要がありますか。

        -   Intune では、リソース アクセス プロファイルを使用して、登録されたデバイスに証明書をプロビジョニングします。
<br></br>
    -   どのような種類の公開キー基盤 (PKI) インフラをサポートする必要がありますか。
<br></br>
-   デバイスまたはアプリケーション レベルで、仮想プライベート ネットワーク (VPN) をサポートする必要がありますか。

    -   Intune では、サードパーティ VPN プロバイダー向けの VPN 構成をプロビジョニングします。
<br></br>
-   ダウンタイムを回避するために、特定の要件に対して一時的な例外を設定できますか。 それともアクセスが許可されたデバイスは、常にすべてのセキュリティ要件を遵守する必要がありますか。

## <a name="additional-information"></a>追加情報

-   詳細な例については、さまざまな業界セクターの[ケース スタディ](https://customers.microsoft.com/story/mwh-global-now-part-of-stantec-secures-mobile-devices-with-intune)を参照して、モバイル デバイス管理の要件をどのように評価したかを確認してください。

## <a name="next-steps"></a>次のステップ

[フェーズ 1: 基本的なセットアップ](https://docs.microsoft.com/intune/plan-design/migration-phase1-basic-setup)

