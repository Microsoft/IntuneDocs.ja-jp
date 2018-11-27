---
title: モバイル デバイス管理のために Intune を準備する
titlesuffix: Microsoft Intune
description: Microsoft Intune に移行する前に、ビジネス要件と技術的な要件を評価します。
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 58591442-6606-4f39-a06b-f17a1f25af25
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.openlocfilehash: 1e21fef5102b22dfe698a9adb73736508452acfe
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2018
ms.locfileid: "52186377"
---
# <a name="phase-1-prepare-microsoft-intune-for-mobile-device-management-mdm"></a>フェーズ 1: モバイル デバイス管理 (MDM) に Microsoft Intune を準備する

Intune の設定の詳細について説明する前に、組織のモバイル デバイス管理の要件を確認しておきましょう。 現在の MDM プロバイダーでアクティブなユーザーのレポートを実行して重要なユーザー グループを識別すると役立つ場合があります。 その後、「[MDM 要件を評価する](migration-guide-prepare.md#assess-mdm-requirements)」セクションの質問に答えることができます。

## <a name="assess-mdm-requirements"></a>MDM 要件を評価する

### <a name="what-kinds-of-devices-do-you-need-to-manage"></a>管理が必要なデバイスの種類について

-   どの[プラットフォーム](supported-devices-browsers.md)をサポートする必要がありますか。

-   サポートする必要があるのは、企業所有デバイスですか個人のデバイスですか。

-   どのような種類の接続を使用しますか。 Wi-Fi、移動体通信、VPN ですか。

### <a name="what-do-your-users-need-to-do-on-managed-devices"></a>マネージド デバイスでユーザーが行う作業

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

- デバイス レベルの暗号化が必要ですか。

- 現在のデバイスのパスコード/PIN コードはどれくらいの長さですか。

- デバイスの機能を無効にしたり、特定のデバイスの動作を制限する必要がありますか。 デバイス構成プロファイルを使用して、プラットフォーム固有のさまざまな設定を制御することができます。
    - カメラの無効化
    - 単一アプリ モードにロック<br/>

- どのような種類の認証をサポートする必要がありますか。 証明書ベースの認証が必要な場合、どのような種類の証明書をプロビジョニングする必要がありますか。
  - Intune では、リソース アクセス プロファイルを使用して、登録されたデバイスに証明書をプロビジョニングします。
  -   どのような種類の公開キー基盤 (PKI) インフラをサポートする必要がありますか。
  <br></br>
- デバイスまたはアプリケーション レベルで、仮想プライベート ネットワーク (VPN) をサポートする必要がありますか。

  -   Intune では、サードパーティ VPN プロバイダー向けの VPN 構成をプロビジョニングします。
  <br/><br/>
- ダウンタイムを回避するために、特定の要件に対して一時的な例外を設定できますか。 それともアクセスが許可されたデバイスは、常にすべてのセキュリティ要件を遵守する必要がありますか。

## <a name="next-steps"></a>次の手順
さまざまな業界セクターの[ケース スタディ](https://customers.microsoft.com/story/mwh-global-now-part-of-stantec-secures-mobile-devices-with-intune)を参照して、モバイル デバイス管理の要件をどのように評価したかを確認してください。

[Intune の基本的なセットアップ](migration-guide-setup.md)を確認してください。
