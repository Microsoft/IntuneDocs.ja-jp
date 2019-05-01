---
title: Intune でのデータの保存と処理
description: Intune で個人データがどのように格納され、処理されるかについて学習します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/18/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: edb07842-6a16-482e-8c1d-541a29e169a8
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3b499f3171910f28a2d190d28e8ab6e945fa463a
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61511270"
---
# <a name="data-storage-and-processing-in-intune"></a>Intune でのデータの保存と処理

Intune で[データが収集されると](privacy-data-collect.md)、そのデータの格納と処理は、次のように行われます。

## <a name="storing-personal-data"></a>個人データの格納

収集されたテレメトリ以外のすべてのデータは、Intune サービスを通じて処理され、次の 1 つまたは複数の保存場所に格納されます。 

- SQLAzure 
- リライアブル コレクション (サービス ファブリック)  
- Azure ストレージ 

監視と安定したサービスの提供にとって重要なテレメトリ (サービス ログ、パフォーマンス ログ、エラーなど) は、Microsoft のテレメトリ データ ストアに送信されます。

### <a name="storage-locations"></a>保存場所

Microsoft では、世界中のさまざまな地域で Intune サービスの提供と運用を行っています。 Intune では、顧客データの管理者が選択した保存場所が尊重されます。

詳細については、[Microsoft Intune での顧客データの場所](For more information, see Microsoft Intune Where is my customer data?) に関するページを参照してください。

### <a name="personal-data-retention"></a>個人データ保有期間

通常、個人データは、ユーザーが Intune 管理から削除されてから 30 日が経過するまで Intune で保持されます。

Intune の使用の一環として収集されたテレメトリ データは、最大 30 日間保持されます。

監査ログは、最大 1 年間は保持されます。

## <a name="processing-personal-data"></a>個人データの処理

Intune では、ISO 認定システムを使用して個人データが処理されます。 詳細については、「[Service Trust Portal](https://www.microsoft.com/en-us/TrustCenter/stp)」を参照してください。

### <a name="profiling-and-marketing"></a>プロファイルとマーケティング

Microsoft Intune では、プロファイルまたはマーケティングの目的でサービスを提供する一環として収集された個人データが使用されることはありません。 

### <a name="restrict-processing-of-personal-data"></a>個人データの処理の制限

ユーザーの個人データの処理を制限するため、次の方法でユーザー アカウントを削除することができます。
1. 以下を含む、ユーザーの個人データの電子コピーをエクスポートする
    - アカウント
    - サービス データ
    - 関連付けられているログ
2. Intune からユーザーのアカウントと関連付けられているデータを削除する

## <a name="next-steps"></a>次の手順

Intune が個人データを[保護および共有](privacy-data-secure-share.md)する方法について確認します。 
