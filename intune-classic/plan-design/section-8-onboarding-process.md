---
title: "Intune オンボード プロセス | Microsoft Docs"
description: "この記事では、Intune クラウド専用ソリューションを環境に導入するときに考慮するべき事項について詳しく説明します。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ac7bd764-5365-4920-8fd0-ea57d5ebe039
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 562e24af8058df56f1b952c82fefe62d38388ec3
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017


---

# <a name="intune-implementation"></a>Intune を実装する

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

オンボード段階では、Intune を運用環境に実装します。 この実装プロセスでは、このガイドの前のセクションで確認した[ユース ケースの要件](section-3-determine-use-case-requirements.md)に基づき、Intune と外部依存性 (必要な場合) を設定し、構成します。

次のセクションでは、要件や大まかな作業分類など、Intune 実装プロセスの概要を提供します。

>[!TIP]
> Intune 実装プロセスの詳細については、「[Additional resources](additional-resources.md)」 (その他のリソース) をご覧ください。

## <a name="intune-requirements"></a>Intune 要件

Intune スタンドアロンの主な要件は次のようになります。

-   EMS/Intune サブスクリプション

-   Office 365 サブスクリプション (Office アプリと MAM ポリシー管理アプリ)

-   Apple APNs 証明書 (iOS デバイス プラットフォーム管理を有効にします)

-   Azure AD Connect (ディレクトリ同期用)

-   Intune On-Premises Connector for Exchange (必要な場合、Exchange On-Premises の CA 用)

-   Intune Certificate Connector (必要な場合、SCEP 証明書展開用)

>[!TIP]
> Intune スタンドアロン要件の詳細については、[ここ](/intune-classic/get-started/what-to-know-before-you-start-microsoft-intune)をご覧ください。

## <a name="intune-implementation-process"></a>Intune 実装プロセス

### <a name="overview-of-implementation-tasks"></a>実装タスクの概要

Intune を実装するときの各作業の概要は次のようになります。

#### <a name="task-1-add-intune-subscription"></a>作業 1: Intune サブスクリプションを追加する

前の要件セクションで確認したように、EMS または Intune サブスクリプションが必要です。 組織が EMS または Intune サブスクリプションを持っていない場合、Microsoft または組織の Microsoft アカウント チームに問い合わせ、Enterprise Mobility + Security (EMS) または Intune の購入に関心がある旨をお伝えください。

-   Microsoft Intune の購入方法については[こちら](https://www.microsoft.com/cloud-platform/microsoft-intune-pricing)をご覧ください。

#### <a name="task-2-add-office-365-subscription"></a>作業 2: Office 365 サブスクリプションを追加する

この手順は省略可能です。 前の要件セクションで確認したように、Exchange Online を使用し、MAM ポリシーで Office モバイル アプリを管理する場合、Office 365 サブスクリプションが必要です。 組織が Office 365 サブスクリプションを持っていない場合、Microsoft または組織の Microsoft アカウント チームに問い合わせ、Office 365 の購入に関心がある旨をお伝えください。

-   Office 365 の購入方法については[ここ](https://products.office.com/business/compare-office-365-for-business-plans)をご覧ください。

#### <a name="task-3-add-users-groups-in-azure-ad"></a>作業 3: Azure AD にユーザー グループを追加する

Intune 展開のユース ケース シナリオや要件によっては、AD または ADD にユーザーやセキュリティのグループを追加する必要があります。 Active Directory または Azure Active Directory で現在のユーザー グループとセキュリティ グループを確認し、ニーズが完全に満たされているかどうか判断してください。 新しいユーザー グループまたはセキュリティ グループは、多くの場合、Active Directory に追加され、Azure AD Directory Connect 経由で Azure Active Directory と同期されます。

-   Intune にユーザーまたはグループを追加する方法については、[ここ](/intune-classic/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-3)をご覧ください。

#### <a name="task-4-assign-intune-and-office-365-user-licenses"></a>作業 4: Intune と Office 365 のユーザー ライセンスを割り当てる

EMS/Intune や Office 365 の展開の対象になるすべてのユーザーにライセンスを割り当てる必要があります。 EMS/Intune と Office 365 のライセンス割り当ては、Office 365 管理センター ポータルで行うことができます。

-   Intune ライセンスの割り当て方法については[ここ](/intune-classic/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-4)をご覧ください。

#### <a name="task-5-set-mobile-device-management-authority-to-intune"></a>作業 5: モバイル デバイス管理機関を Intune に設定する

Intune でデバイスの設定、構成、管理、登録を始める前に、デバイス管理機関を Intune に設定する必要があります。 デバイス管理機関を設定する作業は、Intune 管理ポータルの管理ワークスペースで行います。

-   モバイル デバイス管理機関を設定する方法については[ここ](/intune-classic/deploy-use/prerequisites-for-enrollment#step-2-set-mdm-authority)をご覧ください。

#### <a name="task-6-enable-device-platforms"></a>タスク 6: デバイス プラットフォームを有効にする

既定では、Intune 管理コンソールで、Apple デバイス (iOS と Mac) を除く、ほとんどのデバイス プラットフォームが有効になっています。 iOS デバイスを Intune で登録し、管理するには、デバイス プラットフォームを有効にする必要があります。 iOS デバイス プラットフォームを有効にする手順は、3 つのプロセスからなります。APNs 証明書を作成してダウンロードし、Intune にアップロードします。

-   iOS と Mac のデバイス管理設定の詳細については、[ここ]/intune-classic/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune)を参照してください。

#### <a name="task-7-add-and-deploy-terms-and-conditions-policies"></a>作業 7: 使用条件ポリシーを追加し、展開する

Microsoft Intune では、使用条件を追加し、展開できます。 使用条件ポリシーの追加と展開は Intune 管理ポータルのポリシー ワークスペースで行います。 Intune 展開のユース ケースと要件に基づき、使用条件ポリシーを適宜追加し、対象グループに展開します。

-   使用条件ポリシーの追加と展開方法の詳細については、[ここ](/intune-classic/deploy-use/terms-and-condition-policy-settings-in-microsoft-intune)をご覧ください。

#### <a name="task-8-add-and-deploy-configuration-policies"></a>作業 8: 構成ポリシーを追加し、展開する

Microsoft Intune では、2 種類の構成ポリシーを追加し、展開できます。標準とカスタムです。 構成ポリシーの追加と展開は Intune 管理ポータルのポリシー ワークスペースで行います。 Intune 展開のユース ケースと要件に基づき、構成ポリシーを適宜追加し、対象グループに展開します。

-   構成ポリシーの追加と展開方法の詳細については、[ここ](/intune-classic/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies)をご覧ください。

#### <a name="task-9-add-and-deploy-resource-profiles"></a>作業 9: リソース プロファイルを追加し、展開する

Microsoft Intune は、電子メール、Wi-Fi、VPN のプロファイルに対応しています。 プロファイルの追加と展開は Intune 管理ポータルのポリシー ワークスペースで行います。 Intune 展開のユース ケースと要件に基づき、電子メール/Wi-Fi/VPN プロファイルを適宜追加し、対象グループに展開します。

-   Intune で会社のリソースへのアクセスを有効にする方法の詳細については、[ここ](/intune-classic/deploy-use/enable-access-to-company-resources-with-microsoft-intune)をご覧ください。

#### <a name="task-10-add-and-deploy-apps"></a>作業 10: アプリを追加して展開する

Microsoft Intune では、Web、LOB、パブリック ストアのアプリを展開できます。 また、MAM ポリシーと関連付けることで Intune SDK を統合しているアプリを管理できます。 アプリの追加と展開は Intune 管理ポータルのアプリ ワークスペースで行います。 MAM ポリシーの追加は Intune 管理ポータルのポリシー ワークスペースで行います。 Intune 展開のユース ケースと要件に基づき、アプリを適宜追加し、対象グループに展開します。

-   アプリの追加と展開方法の詳細については、[ここ](/intune-classic/deploy-use/deploy-apps)をご覧ください。

#### <a name="task-11-add-and-deploy-compliance-policies"></a>作業 11: コンプライアンス ポリシーを追加し、展開する

Microsoft Intune はコンプライアンス ポリシーに対応しています。 コンプライアンス ポリシーの追加と展開は Intune 管理ポータルのポリシー ワークスペースで行います。 Intune 展開のユース ケースと要件に基づき、コンプライアンス ポリシーを適宜追加し、対象グループに展開します。

-   コンプライアンス ポリシーの詳細については、[ここ](/intune-classic/deploy-use/introduction-to-device-compliance-policies-in-microsoft-intune)をご覧ください。

#### <a name="task-12-enable-conditional-access-policies"></a>作業 12: 条件付きアクセス ポリシーを有効にする

Microsoft Intune は、Exchange Online、Exchange On-premises、SharePoint Online、Skype for Business Online、Dynamics CRM Online の条件付きアクセスに対応しています。 条件付きアクセス ポリシーは、Intune 管理ポリシーのポリシー ワークスペースで有効にします。 [Intune 展開のユース ケースと要件](section-3-determine-use-case-requirements.md)に基づき、条件付きアクセスを有効にして構成します。

-   条件付きアクセスの詳細については、[ここ](/intune-classic/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune)をご覧ください。

#### <a name="task-13-enroll-devices"></a>作業 13: デバイスを登録する

Intune は、iOS、Mac OS、Android、Windows デスクトップ、Windows モバイル デバイス プラットフォームに対応しています。 Intune 展開のユース ケースと要件に基づき、モバイル デバイス プラットフォームを適宜登録します。

-   デバイスの登録方法については[ここ](/intune-classic/deploy-use/enroll-devices-in-microsoft-intune)をご覧ください。

>[!TIP]
> Intune 実装プロセスの詳細については、この [Microsoft Virtual Academy Intune セッション モジュール](https://mva.microsoft.com/training-courses/deploying-microsoft-enterprise-mobility-suite-16408?l=PPWNoZxvD_1404778676)をご覧ください。

## <a name="next-section"></a>次のセクション

次のセクションでは、[Intune 展開をテストし、検証する](section-9-test-and-validation.md)方法について説明します。

