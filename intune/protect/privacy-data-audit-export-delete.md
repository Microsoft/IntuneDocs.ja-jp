---
title: 個人データの監査、エクスポート、または削除
titleSuffix: Microsoft Intune
description: 個人データの監査、エクスポート、または削除方法について説明します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 96990be0-eb1e-43a4-a0e4-09c7dbdc2bf4
ms.reviewer: kerimh
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4cfb0f69d74cc6146b2497cd53be3e123f79cc70
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "72504350"
---
# <a name="audit-export-or-delete-personal-data-in-intune"></a>Intune での個人データの監査、エクスポート、または削除

Intune 管理者は、監査ログを使用して個人データに関連するアクティビティを追跡できます。 また、管理者は個人データをエクスポートおよび削除することもできます。

[!INCLUDE [GDPR-related guidance](../includes/gdpr-intro-sentence.md)]

## <a name="audit-personal-data"></a>個人データの監査

テナント管理者は監査ログを使用して、Microsoft Intune で変更を行うアクティビティを記録できます。 監査ログは、多くの管理アクティビティに利用できますが、通常は作成、更新 (編集)、削除、割り当てアクションに利用されます。 監査イベントを生成するリモート タスクも確認することができます。 これらの監査ログには、デバイスが Intune に登録されているユーザーの個人データが含まれる場合があります。  

セキュリティ上の目的から、Intune はユーザーとデバイスのアクションの監査ログを 1 年間保持することができます。 これらのログは、1 年間の保有期間の後に自動的に削除されます。

監査ログを確認する方法については、「[Intune のアクティビティの監査ログ](../fundamentals/monitor-audit-logs.md)」を参照してください。 

管理者は監査ログを削除できません。

これらの監査イベントは 1 年間保持されます。 テナント管理者は、[このサポート リクエスト フォーム](https://privacy.microsoft.com/en-US/privacy-questions?)を使用して監査ログを要求できます。

## <a name="export-personal-data"></a>個人データのエクスポート

管理者は、データ主体の権利要求に準拠するために、アカウント、サービス データ、関連ログを含むエンド ユーザーの個人データをエクスポートすることができます。 データ主体に個人データのコピーを提供するかどうか、またはそれを保留する正当なビジネス上の理由があるかどうかは、管理者と組織の判断に委ねられます。 提供する場合は、実際のドキュメントのコピー、適切に修正されたバージョン、または共有することが適切と思われる部分のスクリーンショットを提供することができます。

ユーザーの個人データをエクスポートするには、以下を使用できます。 
- デバイスの一覧をエクスポートする Intune MDM デバイス ブレード。 また、デバイス データを直接コピーすることもできます。
- [Export-IntuneData.ps1 スクリプト](https://aka.ms/intunedataexport)。

## <a name="delete-end-user-personal-data"></a>エンド ユーザーの個人データを削除する

Intune による管理から個人データを削除するには、3 つの方法があります。
- Azure Active Directory からユーザーを削除する
- デバイスを出荷時設定にリセットする
- ユーザー自身が削除する

### <a name="delete-a-user-from-intune"></a>Intune からユーザーを削除する

Intune からエンド ユーザーの個人データを削除するには、管理者が [Azure Active Directory (AAD)](https://docs.microsoft.com/azure/active-directory/fundamentals/add-users-azure-active-directory#delete-a-user) からユーザーを削除する必要があります。 ユーザーが AAD から削除 (物理的に削除) されると、Intune は AAD から削除信号を受信し、自動的にそのユーザーのすべての個人データを Intune サービスから消去し始めます。 ユーザーの情報は、削除アクションから 30 日以内に Intune サービスから削除されます。

### <a name="reset-device-to-factory-settings"></a>デバイスを出荷時設定にリセットする
出荷時設定にリセットすると、会社と個人のデータと設定はすべて元の出荷時設定に復元されます。 この方法は、次の従業員にデバイスを提供する場合に便利です。 ユーザー ファイル、ユーザーがインストールしたアプリケーション、および既定以外の設定は削除されます。このデータは、削除アクションから 30 日以内に Intune サービスから削除されます。

### <a name="user-self-removal-from-intune-management"></a>ユーザー自身が Intune による管理から削除する
ユーザーは、管理者の支援を受けずに Intune による管理から自分の [Android、Apple、または Windows](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-android) の個人用デバイスを削除できます。   

### <a name="retire"></a>インベントリから削除
**インベントリから削除**すると、会社のアプリケーション、Intune が管理しているアプリに関するデータ、ポリシー設定、Intune でプロビジョニングされた電子メール プロファイルなど、Intune でプロビジョニングされたデータが削除されます。 このアクションでは、ユーザーの個人データはデバイス上にそのまま保持されます。

### <a name="delete-a-tenant-from-microsoft-intune"></a>Microsoft Intune からテナントを削除する

Intune テナントの顧客が Intune アカウントをキャンセルすると、顧客が Intune アカウントを閉鎖してから 180 日以内にすべてのテナント データが削除されます。 AAD テナントが他の Microsoft エンタープライズ サブスクリプション (Azure、Office 365) に関連付けられている場合、Intune の顧客データのみが削除されます。 AAD テナント リソースは、他のサブスクリプションで使用するために維持されます。 Intune アカウントが AAD テナントに関連付けられている唯一のサブスクリプションの場合、テナントは削除され、すべてのリソースと顧客データも削除されます。

### <a name="delete-a-user-in-a-hybrid-mobile-device-management-mdm-environment"></a>ハイブリッド モバイル デバイス管理 (MDM) 環境でユーザーを削除する
ハイブリッド MDM 環境 (Configuration Manager と統合された Intune) がある場合、ユーザーを完全に削除し、ローカルの Active Directory、Configuration Manager、および Intune から完全に削除するには、次のアクションを (順番に) 実行する必要があります。

1. ローカルの Active Directory (AD) からユーザーを削除します。 この結果、ユーザーは Azure AD に同期されなくなり、Configuration Manager の検出機能からも検出されなくなります。 
2. Configuration Manager コンソールからユーザーを削除して、Configuration Manager からユーザーと関連データを削除します。 コンソールで **[資産とコンプライアンス]**  >  **[ユーザー]** に移動し、削除するユーザーを右クリックし、 **[削除]** をクリックします。
3. [AAD からユーザーを削除します](https://docs.microsoft.com/azure/active-directory/fundamentals/add-users-azure-active-directory#delete-a-user)。これにより、Azure Active Directory と Intune の両方からユーザーと関連データが同時に削除されます。 ユーザーが AAD から削除 (物理的に削除) されると、Intune は AAD から削除信号を受信し、自動的にそのユーザーのすべての個人データを Intune サービスから消去し始めます。 ユーザーの情報は、削除アクションから 30 日以内に Intune サービスから削除されます。

> [!Important]
>新規のハイブリッド MDM の顧客のオンボーディングは非推奨となりました。 詳細については、「[Move from Hybrid Mobile Device Management to Intune on Azure](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Move-from-Hybrid-Mobile-Device-Management-to-Intune-on-Azure/ba-p/280150)」 (ハイブリッド MDM から Azure での Intune に移行する) のブログ記事を参照してください。

## <a name="next-steps"></a>次の手順

Intune で個人データを[監査、エクスポート、または削除](privacy-data-audit-export-delete.md)する方法について確認します。
