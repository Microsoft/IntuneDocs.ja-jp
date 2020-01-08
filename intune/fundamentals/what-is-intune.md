---
title: Microsoft Intune の概要 - Azure | Microsoft Docs
description: Microsoft Intune が Enterprise Mobility + Security ソリューションのモバイル デバイス管理 (MDM) とモバイル アプリ管理 (MAM) コンポーネントとしてどのように機能するか、およびそれが会社のデータを保護するしくみについて説明します。
keywords: Intune の概要
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 10/14/2019
ms.topic: overview
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3b4e778d-ac13-4c23-974f-5122f74626bc
ms.reviewer: pmay
ms.suite: ems
search.appverid: MET150
ms.custom: get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6d24d1c7dbae12fb33ec277419b1bbfd47b46b07
ms.sourcegitcommit: a82d25d98fdf0ba766f8f074871d4f13725e23f9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/31/2019
ms.locfileid: "75548062"
---
# <a name="microsoft-intune-is-an-mdm-and-mam-provider-for-your-devices"></a>Microsoft Intune はデバイスの MDM および MAM プロバイダーです

Microsoft Intune は、モバイル デバイス管理 (MDM) とモバイル アプリケーション管理 (MAM) を中心にしたクラウドベースのサービスです。 Intune は、Microsoft の [Enterprise Mobility + Security (EMS) スイート](https://www.microsoft.com/microsoft-365/enterprise-mobility-security)に含まれており、組織のデータを保護したまま、ユーザーの生産性を高めることができます。 Microsoft 365 や Azure Active Directory (Azure AD) などの他のサービスと統合されており、誰がアクセスできるか、何にアクセスできるか、そしてデータ保護のために Azure Information Protection を制御します。 これを Microsoft 365 と共に使う場合、従業員が各自のデバイスを生産的に活用できるようにしながら、同時に組織の情報を保護することができます。

![Intune アーキテクチャのイメージ](./media/what-is-intune/intunearch_sm.png)

[ここ](./media/what-is-intune/intunearchitecture.svg)をクリックすると、Intune アーキテクチャ ダイアグラムが大きな画像で表示されます。

Intune では次のことができます。

- Intune を使用した 100% のクラウドにするか、Configuration Manager と Intune を使用した[共同管理](https://docs.microsoft.com/configmgr/comanage/overview)にするかを選択する。
- 個人および組織所有のデバイスで、データとネットワークにアクセスするルールを設定し、設定を構成する。
- オンプレミスとモバイルのデバイスにアプリを展開し、認証する。
- ユーザーが情報にアクセスして共有する方法を制御して、会社情報を保護する。
- デバイスやアプリをセキュリティ要件に準拠させる。

## <a name="manage-devices"></a>デバイスの管理

Intune では、ご自分に適したアプローチを使用してデバイスを管理します。 組織が所有するデバイスの場合、設定、機能、セキュリティなど、デバイスに対するフル コントロールが必要になることがあります。 このアプローチの場合、このようなデバイスのデバイスとユーザーが Intune に "登録" されます。 登録すると、Intune で構成されたポリシーを介してルールと設定が送信されます。 たとえば、パスワードと PIN の要件の設定、VPN 接続の作成、脅威の保護の設定などを行うことができます。

個人用デバイスまたは Bring-Your-Own Device (BYOD) の場合、ユーザーは組織の管理者にフル コントロールを持たせたくないことがあります。 このアプローチの場合は、ユーザーに選択肢を与えます。 たとえば、組織のリソースにフル アクセスする場合は、ユーザーが自分のデバイスを[登録](../enrollment/device-enrollment.md)します。 また、このようなユーザーがメールまたは Microsoft Teams へのアクセスのみを必要としている場合は、多要素認証 (MFA) が必須のアプリ保護ポリシーを使用して、これらのアプリを使用します。

Intune にデバイスを登録して管理すると、管理者は次のことを行えます。

- 登録されているデバイスを確認し、組織のリソースにアクセスするデバイスのインベントリを取得する。
- セキュリティと正常性の標準を満たすようにデバイスを構成する。 たとえば、脱獄されたデバイスをブロックする場合があります。
- ユーザーが Wi-Fi ネットワークに簡単にアクセスできるように、または VPN を使用してネットワークに接続できるように、デバイスに証明書をプッシュする。
- 準拠および非準拠のユーザーとデバイスに関するレポートを表示する。
- デバイスが紛失された、盗難された、または使用されなくなった場合に組織のデータを削除する。

**オンライン リソース**:

- [デバイスの登録とは](../enrollment/device-enrollment.md)

- [デバイス プロファイルを使用してデバイスに機能と設定を適用する](../configuration/device-profiles.md)

- [Microsoft Intune でデバイスを保護する](../protect/device-protect.md)

## <a name="manage-apps"></a>アプリを管理する

Intune のモバイル アプリケーション管理 (MAM) は、カスタム アプリやストア アプリなど、アプリケーション レベルで組織のデータを保護するように設計されています。 アプリ管理は、組織所有のデバイスと個人用デバイスで使用できます。

アプリが Intune で管理されている場合、管理者は次のことを実行できます。

- 特定のグループのユーザー、特定のグループ内のデバイスなど、ユーザー グループとデバイスにモバイル アプリを追加して割り当てる。
- 特定の設定を有効にしてアプリを開始または実行するように構成し、デバイスに既に存在するアプリを更新する。
- 使用されているアプリに関するレポートを表示し、その使用状況を追跡する。
- アプリから組織のデータのみを削除して選択的ワイプを実行する。

Intune がモバイル アプリ セキュリティを提供する方法の 1 つとして、 **[アプリの保護ポリシー](../apps/app-protection-policy.md)** があります。 アプリ保護ポリシー:

- Azure AD ID を使用して、個人のデータから組織のデータを分離する。 そのため、個人情報は組織の IT の認知から分離されます。 組織の資格情報を使用してアクセスされるデータには、追加のセキュリティ保護が適用されます。
- ユーザーが実行できる操作 (コピーと貼り付け、保存、表示など) を制限することで、個人用デバイスでのアクセスをセキュリティで保護する。
- 作成して、Intune に登録されているデバイス、別の MDM サービスに登録されているデバイス、またはどの MDM サービスにも登録されていないデバイスに展開できます。 登録済みのデバイスでは、アプリ保護ポリシーによって追加の保護レイヤーを追加できます。

たとえば、ユーザーは、組織の資格情報を使用してデバイスにサインインします。 組織の ID を使用して、個人の ID に対して拒否されたデータにアクセスできます。 組織のデータが使用されると、アプリ保護ポリシーによってデータの保存方法と共有方法が制御されます。 ユーザーが個人の ID でサインインした場合、同じ保護は適用されません。 このようにして、IT 部門が組織のデータを制御すると同時に、エンド ユーザーは個人データの制御とプライバシーを維持します。

また、EMS の他のサービスでも Intune を使用できます。 この機能は、オペレーティング システムやアプリに含まれているものを超えて、組織のモバイル アプリにセキュリティを提供します。 EMS で管理されているアプリから、より幅広いモバイル アプリとデータ保護の機能にアクセスできます。

![アプリ管理データ セキュリティのレベルを示す画像](./media/what-is-intune/managing-mobile-apps.png)

## <a name="compliance-and-conditional-access"></a>コンプライアンスと条件付きアクセス

Intune は Azure AD と連携し、さまざまなアクセス制御シナリオを可能にします。 たとえば、モバイル デバイスがメールや SharePoint などのネットワーク リソースにアクセスする前に、Intune で定義されている組織の標準に準拠することを必須にします。 同様に、サービスをロックダウンして、特定のモバイル アプリ セットでのみ使用できるようにすることもできます。 たとえば、Exchange Online へのアクセスを Outlook または Outlook Mobile だけに制限できます。

**オンライン リソース**:

- [組織のリソースへのアクセスを許可するようにデバイスのルールを設定する](../protect/device-compliance-get-started.md)

- [Intune での条件付きアクセスの一般的な使用方法](../protect/conditional-access-intune-common-ways-use.md)

## <a name="how-to-get-intune"></a>Intune を取得する方法

Intune は次のように利用できます。

- スタンドアロン [Azure サービス](https://go.microsoft.com/fwlink/?linkid=2090973)として
- [Microsoft 365](https://www.microsoft.com/microsoft-365/enterprise-mobility-security/microsoft-intune) および[政府機関向け Microsoft 365](https://www.microsoft.com/microsoft-365/government) に付属している機能
- いくつかの限られた Intune 機能で構成されている [Office 365 のモバイル デバイス管理](https://support.office.com/article/choose-between-mdm-for-office-365-and-microsoft-intune-c93d9ab9-efb2-4349-9b93-30c30562ee22)として

Intune は多くの部門で使用されています。たとえば、[政府機関](https://docs.microsoft.com/enterprise-mobility-security/solutions/ems-govt-service-description)、[教育機関](https://www.microsoft.com/en-us/education/intune)、[キオスクまたは専用デバイス](../configuration/kiosk-settings.md) (製造および小売用) などです。

## <a name="next-steps"></a>次のステップ

- [Intune が解決に役立つ一般的なビジネス問題](https://docs.microsoft.com/intune/common-scenarios)のいくつかを参照してください。
- [Intune の 30 日の試用](free-trial-sign-up.md)を開始します。
- [Intune への移行](migration-guide.md)を計画します。
- 無料試用版またはサブスクリプションを使用して、次の手順を実行します。「[クイックスタート:iOS 用の電子メール デバイス プロファイルを作成する](../configuration/quickstart-email-profile.md)」の手順に従って、iOS デバイス用のテスト デバイス プロファイルを作成します。
