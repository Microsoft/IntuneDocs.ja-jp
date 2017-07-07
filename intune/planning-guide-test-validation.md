---
title: "Intune のテストと検証"
description: "この記事では、Intune クラウド専用ソリューションを環境でテストし、検証するときに考慮するべき事項について詳しく説明します。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4f82ee0c-4bd6-4623-9b10-9249d316ccf5
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 4ea2974c4724564cd8f9972fdb238b06d1b100e6
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2017
---
# <a name="intune-testing-and-validation"></a>Intune のテストと検証

[!INCLUDE[note for both-portals](./includes/note-for-both-portals.md)]

テスト段階は、実装段階の途中と後に行ってください。以前に確認した、必要なすべての IT (管理者) とエンド ユーザー (ユース ケース) のシナリオをテストするには、テスト用のアカウント、グループ、デバイスが必要です。

サポート ドキュメントが作成され、IT サポートやヘルプデスクのスタッフが快適に製品をサポートできるように、IT サポート/ヘルプデスクのスタッフをテスト段階に組み入れることが推奨されます。 部品やシナリオがユース ケースに基づいて機能しない場合、必要な変更を記録し、変更が行われた理由を追加してください。

## <a name="before-you-begin"></a>始める前に

次の内容を記録しておくことが推奨されます。

-   **テスト条件:** 測定水準とするベンチマークを特定します。

-   **設計部品:** 1 つ以上のテスト条件に存在する必要があります。

ある設計部品が、要件またはシナリオに合わせて調整される 1 つ以上のテスト条件に存在しない場合、その設計部品が必要がどうかを検討してください。 また、次の項目を用意する必要があります。

-   **アカウント:** テストで使用するアカウントは、あらゆるユース ケース シナリオをテストするために EMS や Office 365 にライセンス供与されているテスト アカウントにしてください。

-   **デバイス:** この時点で使用するデバイスは、データが消去されたり、出荷時の既定値にリセットされたりしてもかまわないテスト デバイスにしてください。

-   **統合コンポーネント:** あらゆる統合コンポーネント (Certificate Connector、ホスト型 Exchange 用 Intune Service to Service Connector、Intune On-Premises Exchange Connector) を必要に応じてインストールし、構成する必要があります。

予想外の問題に対処するために、設計を変更しなければならないことがあります。 また、設計変更はすべて、その理由と共に完全に記録してください。 たとえば、次のような変更が行われます。

-   Network Device Enrollment Service (NDES) の要件が満たされないことに気付きましたが、VPN プロファイルと Wi-Fi プロファイルをルート CA で構成すれば、NDES を実装しなくても同じ要件を満たせることを知ります。

テストや検証のプロセスで、技術的な指南や特別なトラブルシューティングが必要な問題に遭遇することがあります。 Microsoft サポート チャンネルのサポートを利用することが推奨されます。

-   [Intune サポートの利用方法の詳細](/intune-classic/troubleshoot/how-to-get-support-for-microsoft-intune)

-   [Microsoft Intune の一般的なトラブルシューティングのヒント](/intune-classic/troubleshoot/general-troubleshooting-tips-for-microsoft-intune)

-   [Microsoft Intune のサポートを受ける方法](/intune-classic/troubleshoot/how-to-get-support-for-microsoft-intune)

-   [Microsoft Intune のサポートの電話番号](/intune-classic/troubleshoot/contact-assisted-phone-support-for-microsoft-intune)

## <a name="functional-validation-testing"></a>機能検証テスト

機能検証では、各要素と構成をテストし、それが適切に動作していることを確認する作業が行われます。 検証テストの例が下の表にあります。

![セクション 9 表 1](./media/section-9-image-1-table.PNG)

## <a name="use-case-validation-testing"></a>ユース ケース検証テスト

ユース ケース検証テストを実行し、シナリオが完全であり、機能することを確認してください。 ユース ケース シナリオには 2 つの種類があります。IT 管理者とエンド ユーザーです。

### <a name="it-admin"></a>IT 管理者

IT 管理者の検証テストを実行し、あるデバイスまたはユーザーに対して実行した管理アクションが正しく動作することを確認します。 下は、IT 管理者のエンドツーエンド検証シナリオの例です。

![セクション 9 表 2](./media/section-9-image-2-table.PNG)

### <a name="end-user"></a>エンド ユーザー

エンド ユーザー検証テストを実行し、エンド ユーザー側の操作性が予想どおりであり、あらゆるユーザー コミュニケーションで正しく表示されることを確認してください。 検証でエラーが出た場合、普及率が下がり、ヘルプデスクに大量の問い合わせが発生することになるため、エンド ユーザー側で正しい操作が行われることを確認することは重要です。

![セクション 9 表 3](./media/section-9-image-3-table.PNG)

## <a name="next-steps"></a>次の手順

Intune の動作とユース ケース シナリオをテストし、確認しました。これで Intune 運用のロールアウトに移ることができます。 詳細については、「[Additional resources](planning-guide-resources.md)」 (その他のリソース) を参照してください。
