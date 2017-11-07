---
title: "Intune の導入プロセス"
description: "この記事では、Intune クラウド専用ソリューションを環境に導入するときに考慮するべき事項について詳しく説明します。"
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ac7bd764-5365-4920-8fd0-ea57d5ebe039
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: aab3c202272d91f9e1596eae6f740f68f049a657
ms.sourcegitcommit: 94d3d86f8ae9f82a9872384bbaae53580036a4ff
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2017
---
# <a name="implement-your-intune-plan"></a>Intune の計画を実装する

導入フェーズでは、Intune を運用環境に展開します。 この実装プロセスでは、[ユース ケースの要件](planning-guide-requirements.md)に基づいて Intune と外部依存関係 (必要な場合) を設定し、構成します。

次のセクションでは、要件や大まかな作業分類など、Intune 実装プロセスの概要を提供します。

## <a name="intune-requirements"></a>Intune 要件

Intune スタンドアロンの主な要件は次のようになります。

-   Enterprise Mobility + Security (EMS)/Intune のサブスクリプション

-   Office 365 サブスクリプション (Office アプリとアプリ保護ポリシー管理アプリ用)

-   Apple APNs 証明書 (iOS デバイス プラットフォーム管理を有効にします)

-   Azure AD Connect (ディレクトリ同期用)

-   Intune On-Premises Connector for Exchange (必要な場合、Exchange On-Premises の条件付きアクセス用)

-   Intune Certificate Connector (必要な場合、SCEP 証明書展開用)

>[!TIP]
> Intune で管理できるデバイスの完全な一覧については、[サポートされるデバイス](supported-devices-browsers.md)の一覧をご覧ください。

## <a name="intune-implementation-process"></a>Intune 実装プロセス

Intune の展開の実装に関しては、13 の個別タスクが識別されています。 ビジネス要件、既存のインフラストラクチャ、およびデバイス管理戦略によっては、一部のタスクは既に完了している場合があります。 タスクによっては計画に適用されないものもあります。

### <a name="task-1-get-an-intune-subscription"></a>タスク 1: Intune サブスクリプションを入手する

前の Intune 要件セクションで示されているように、EMS または Intune のサブスクリプションが必要です。 組織がどちらも持っていない場合、Microsoft または組織の Microsoft アカウント チームに問い合わせ、Enterprise Mobility + Security (EMS) または Intune の購入に関心があることを伝えてください。

-   Microsoft Intune の購入方法については[こちら](https://www.microsoft.com/cloud-platform/microsoft-intune-pricing)をご覧ください。

### <a name="task-2-add-office-365-subscription"></a>作業 2: Office 365 サブスクリプションを追加する

この手順は省略可能です。 Exchange Online を使い、アプリ保護ポリシーで Office モバイル アプリを管理する予定の場合は、Office 365 のサブスクリプションが必要です。 組織が Office 365 サブスクリプションを持っていない場合、Microsoft または組織の Microsoft アカウント チームに問い合わせ、Office 365 の購入に関心があることを伝えてください。

-   Office 365 の購入方法については[ここ](https://products.office.com/business/compare-office-365-for-business-plans)をご覧ください。

### <a name="task-3-add-users-groups-in-azure-ad"></a>作業 3: Azure AD にユーザー グループを追加する

Intune 展開のユース ケース シナリオや要件によっては、Active Directory または Azure Active Directory にユーザーやセキュリティのグループを追加する必要があります。 Active Directory または Azure Active Directory で現在のユーザー グループとセキュリティ グループを確認し、ニーズが完全に満たされているかどうか判断します。 新しいユーザーとセキュリティ グループを追加するときは、Active Directory で追加し、Azure AD Connect を使って Azure Active Directory と同期することをお勧めします。


-   Intune にユーザーまたはグループを追加する方法については、[ここ](users-permissions-add.md)をご覧ください。
<!---why not send them to the AAD connect topic? Question out to Andre: https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnect--->



### <a name="task-4-assign-intune-and-office-365-user-licenses"></a>作業 4: Intune と Office 365 のユーザー ライセンスを割り当てる

EMS/Intune や Office 365 の展開の対象になるすべてのユーザーに、ライセンスを割り当てる必要があります。 EMS/Intune と Office 365 のライセンスの割り当ては、Office 365 管理センター ポータルで行うことができます。

-   Intune ライセンスの割り当て方法については[ここ](licenses-assign.md)をご覧ください。

### <a name="task-5-set-mobile-device-management-authority-to-intune"></a>作業 5: モバイル デバイス管理機関を Intune に設定する

Intune でデバイスの設定、構成、管理、登録を始める前に、デバイス管理機関を Intune に設定する必要があります。

-   詳しくは、[モバイル デバイス管理機関を設定する方法](mdm-authority-set.md)に関する記事をご覧ください。

### <a name="task-6-enable-device-platforms"></a>タスク 6: デバイス プラットフォームを有効にする

既定では、Apple デバイス (iOS と Mac) を除く、ほとんどのデバイス プラットフォームが有効になっています。 iOS デバイスを Intune で登録し、管理するには、デバイス プラットフォームを有効にする必要があります。 そのためには、MDM プッシュ証明書を作成し、Intune に追加する必要があります。

-   詳しくは、[Apple デバイスの登録を有効にする方法](apple-mdm-push-certificate-get.md)に関する記事をご覧ください。

### <a name="task-7-add-and-deploy-terms-and-conditions-policies"></a>作業 7: 使用条件ポリシーを追加し、展開する

Intune は使用条件ポリシーをサポートしています。 Intune 展開のユース ケースと要件に基づき、使用条件ポリシーを適宜追加し、対象グループに展開します。

-   使用条件ポリシーの追加と展開方法の詳細については、[ここ](terms-and-conditions-create.md)をご覧ください。

### <a name="task-8-add-and-deploy-configuration-policies"></a>作業 8: 構成ポリシーを追加し、展開する

Intune では、標準とカスタムの 2 種類の構成ポリシーがサポートされています。 Intune 展開のユース ケースと要件に基づき、構成ポリシーを適宜追加し、対象グループに展開します。

-   構成ポリシーの追加と展開方法の詳細については、[ここ](device-profiles.md)をご覧ください。

### <a name="task-9-add-and-deploy-resource-profiles"></a>作業 9: リソース プロファイルを追加し、展開する

Intune は、メール、Wi-Fi、VPN のプロファイルに対応しています。 Intune 展開のユース ケースと要件に基づき、プロファイルを適宜追加し、対象グループに展開します。

-   詳しくは、[Intune で会社のリソースへのアクセスを有効にする方法](device-profiles.md)に関する記事をご覧ください。

### <a name="task-10-add-and-deploy-apps"></a>作業 10: アプリを追加して展開する

Intune は、Web アプリ、基幹業務アプリ、パブリック ストア アプリの展開をサポートしています。 また、アプリ保護ポリシーと関連付けることで、Intune SDK を統合しているアプリを管理できます。 Intune 展開のユース ケースと要件に基づき、アプリを適宜追加し、対象グループに展開します。

-   詳しくは、[アプリの追加と展開](app-management.md)に関する記事をご覧ください。

### <a name="task-11-add-and-deploy-compliance-policies"></a>作業 11: コンプライアンス ポリシーを追加し、展開する

Intune はコンプライアンス ポリシーに対応しています。 Intune 展開のユース ケースと要件に基づき、コンプライアンス ポリシーを適宜追加し、対象グループに展開します。

-   コンプライアンス ポリシーの詳細については、[ここ](device-compliance.md)をご覧ください。

### <a name="task-12-enable-conditional-access-policies"></a>作業 12: 条件付きアクセス ポリシーを有効にする

Intune は、Exchange Online、Exchange オンプレミス、SharePoint Online、Skype for Business Online、Dynamics CRM Online の条件付きアクセスに対応しています。 Intune 展開のユース ケースと要件に基づき、条件付きアクセスを有効にして構成します。

-   条件付きアクセスの詳細については、[ここ](conditional-access.md)をご覧ください。

### <a name="task-13-enroll-devices"></a>作業 13: デバイスを登録する

Intune は、iOS、Mac OS、Android、Windows デスクトップ、Windows モバイル デバイス プラットフォームに対応しています。 Intune 展開のユース ケースと要件に基づき、モバイル デバイス プラットフォームを適宜登録します。

-   デバイスの登録方法については[ここ](device-enrollment.md)をご覧ください。


## <a name="next-steps"></a>次のステップ

Intune 実装プロセスの詳細については、この [Microsoft Virtual Academy Intune セッション モジュール](https://mva.microsoft.com/en-US/training-courses/deploying-microsoft-enterprise-mobility-suite-16408)をご覧ください。


[Intune 展開のテストと検証](planning-guide-test-validation.md)に関するガイダンスをご覧ください。
