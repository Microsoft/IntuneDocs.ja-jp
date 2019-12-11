---
title: Microsoft 365 でのデバイス管理
description: Microsoft 365 Enterprise には Microsoft Intune が含まれています。 Intune が組織向けにモバイル デバイス管理とモバイル アプリケーション管理をどのように提供しているかについて説明します。 一般的なシナリオを読み、Intune を使用して実際の環境に Microsoft 365 を展開してください。
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/13/2019
ms.topic: conceptual
audience: ITPro
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.technology: ''
ms.custom: intune
ms.assetid: 0649d310-43a7-4b01-85d2-da255d03e1da
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7ab41026cd9b2ceeaaa478fc27c984d0d89db4c5
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74058522"
---
# <a name="device-management-overview"></a>デバイス管理の概要

すべての管理者の重要なタスクは、組織のリソースとデータを保護することです。 このタスクが "*デバイス管理*" です。 ユーザーは多くのデバイスを使用して、個人のファイルを開いて共有したり、Web サイトにアクセスしたり、アプリやゲームをインストールしたりしています。 これらの同じユーザーは、従業員と学生でもあります。 ユーザーは各自のデバイスを使用して、電子メールや OneNote などの仕事や学校のリソースにアクセスしたいと考えます。

組織では、デバイス管理を使い、さまざまなデバイスから、そのリソースとデータを保護し、セキュリティで保護できます。

デバイス管理プロバイダーを使用することで、組織では、承認されたユーザーとデバイスだけが機密情報にアクセスできるようにすることができます。 同様に、デバイスのユーザーは、自分のデバイスが組織のセキュリティ要件を満たしていることがわかっているため、安心して自分の電話から作業データにアクセスできます。 組織には、**リソースを保護するために何を使用すべきか**という疑問があると考えられます。

その答えが [Microsoft Intune](what-is-intune.md) です。 Intune ではモバイル デバイス管理 (MDM) とモバイル アプリケーション管理 (MAM) を行います。 MDM または MAM ソリューションの主要なタスクには次のようなものがあります。

- 多様なモバイル環境をサポートし、iOS、Android、Windows、および macOS デバイスを安全に管理します。
- デバイスやアプリを組織のセキュリティ要件に準拠させます。
- 組織所有のデバイスと個人のデバイスで、組織のデータを安全な状態に保つために役立つポリシーを作成します。
- 1 つの統合されたモバイル ソリューションを使用して、これらのポリシーを適用し、デバイス、アプリ、ユーザー、およびグループの管理に役立てます。
- 従業員が会社のデータにアクセスし、共有する方法を制御することで、会社の情報を保護します。

Intune は Microsoft Azure と Microsoft 365 に含まれ、Azure Active Directory (Azure AD) と統合されます。 Azure AD は、アクセス権を持つユーザーとそれらのユーザーがアクセスできる対象を制御するために役立ちます。

## <a name="microsoft-intune"></a>Microsoft Intune

Microsoft などの多くの組織で、Intune を使用して、ユーザーが会社所有のモバイル デバイスや個人のデバイスからアクセスする機密データをセキュリティ保護しています。 Intune には、デバイスとアプリの構成ポリシー、ソフトウェア更新ポリシー、インストールの状態 (グラフ、テーブル、レポート) などがあり、データ アクセスをセキュリティ保護して、監視するために役立ちます。

ユーザーがさまざまなプラットフォームを使用した複数のデバイスを所有していることはよくあることです。 たとえば、従業員は、仕事に Surface Pro を使用し、個人の生活では Android モバイル デバイスを使用していることがあります。 また、個人がこれらの複数のデバイスから Microsoft Outlook や SharePoint などの組織のリソースにアクセスすることもよくあることです。

Intune により、ユーザーごと、および iOS、macOS、Android、Windows などの各デバイスで実行されるさまざまなプラットフォームごとに、複数のデバイスを管理できます。 Intune では、デバイス プラットフォームによってポリシーと設定が区別されます。 そのため、特定のプラットフォームのデバイスを簡単に管理および表示できます。

**[一般的なシナリオ](common-scenarios.md)** は、モバイル デバイスを使用する際のよくある疑問を Intune によって解決する方法を確認できる優れたリソースです。 以下に関するシナリオを参照できます。  

- オンプレミスの Exchange での電子メールの保護
- Office 365 への安全なアクセス
- 個人のデバイスを使用して、組織のリソースにアクセスする

Intune の詳細については、「 [intune とは](what-is-intune.md)」を参照してください。

## <a name="integration-with-secure-and-protect-services"></a>セキュリティおよび保護サービスとの統合

すべてのデバイス管理ソリューションの主要なタスクは、セキュリティと保護を実現することです。 このタスクを実現するために、Intune は他のサービスとの統合に大きな役割を果たします。 次に例を示します。

- **Microsoft 365** は一般的な IT タスクを簡略化する重要なコンポーネントです。 Microsoft 365 管理センターでは、ユーザーを作成し、グループを管理します。 また、Intune、Azure AD などの他のサービスにもアクセスできます。

  たとえば、Microsoft 365 で iOS デバイス グループを作成します。 さらに、Intune を使用して、アプリ ストアへのアクセス、AirDrop の使用、iCloud へのバックアップ、Apple の Web フィルターの使用などの iOS 機能に焦点を合わせたポリシーを iOS デバイス グループにプッシュできます。

- **Windows Defender** には、Windows 10 デバイスを保護するための多くのセキュリティ機能が含まれています。 たとえば、Intune と Windows Defender を一緒に使用すると、次のことができます。

  - [Windows Defender SmartScreen](../protect/endpoint-protection-windows-10.md) を有効にして、モバイル デバイス上のファイルとアプリでの不審なアクティビティを検索できます。
  - [Microsoft Defender Advanced Threat Protection (ATP)](../protect/advanced-threat-protection.md) を使用して、モバイル デバイスに対するセキュリティ侵害を防ぐことができます。 また、ユーザーを企業リソースからブロックすることで、セキュリティ侵害の影響を抑えるために役立ちます。

- **条件付きアクセス**は、Azure Active Directory の機能で、Intune とうまく統合されます。 [条件付きアクセス](../protect/conditional-access.md)を使用することで、確実に準拠しているデバイスのみに電子メール、SharePoint、およびその他のアプリへのアクセスを許可します。

## <a name="choose-the-device-management-solution-thats-right-for-you"></a>適切なデバイス管理ソリューションの選択

デバイス管理にアプローチする方法はいくつかあります。 1 つ目は、Intune に組み込まれている機能を使用してデバイスのさまざまな側面を管理できます。 このアプローチは、**モバイル デバイス管理 (MDM)** と呼ばれます。 ユーザーは自分のデバイスを "登録" し、証明書を使用して Intune と通信します。 IT 管理者は、デバイス上のアプリをプッシュする、デバイスを特定のオペレーティング システムに限定する、個人のデバイスをブロックするなどを行います。 デバイスの紛失や盗難時は、デバイスからすべてのデータを削除することもできます。

2 つ目のアプローチとして、デバイス上のアプリを管理します。 このアプローチは、**モバイル アプリケーション管理 (MAM)** と呼ばれます。 ユーザーは、個人のデバイスを使用して組織のリソースにアクセスにできます。 電子メールや SharePoint などのアプリを開くときに、ユーザーは追加の認証を求められます。 デバイスの紛失や盗難時には、デバイスからすべての組織のデータを削除できます。

[MDM と MAM](byod-technology-decisions.md) を組み合わせて使用することもできます。

Intune をセットアップするときに、Azure portal でのみ作業してデバイスを管理するか、または Intune と Microsoft 365 を一緒に使用してデバイスを管理するかを選択することもできます。 「[Migrating mobile device management to Intune in the Azure portal](https://www.microsoft.com/itshowcase/Article/Content/1042/Migrating-mobile-device-management-to-Intune-in-the-Azure-portal)」(Azure portal でモバイル デバイス管理を Intune に移行する) は Microsoft IT のケース スタディです。 このケース スタディでは、Microsoft IT が最新のデバイス管理アプローチをどのように選択したかを参照し、得られた教訓をお読みください。

## <a name="simplify-it-tasks-using-the-device-management-admin-center"></a>デバイス管理の管理センターを使用して IT タスクを簡略化する

[Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)は、モバイル デバイスに関するタスクの管理と実行を行うためのワンストップ ショップです。 このワークスペースには、デバイス管理のために使用するサービス (Intune や Azure Active Directory など) と、クライアント アプリの管理のために使用するサービスが含まれています。

デバイス管理の管理センターでは、次のことができます。

- [デバイスの登録](../enrollment/device-enrollment.md)
- [デバイス コンプライアンスの設定](../protect/device-compliance-get-started.md)
- [デバイスの管理](../remote-actions/device-management.md)
- [アプリの管理](../apps/app-management.md)  
- [iOS 電子ブック](../apps/vpp-ebooks-ios.md)  
- [Exchange On-premises Connector をインストールする](../protect/exchange-connector-install.md)  
- [ロールの管理](role-based-access-control.md)  
- ソフトウェア更新プログラムの管理
  - [Windows 10 更新の管理](../protect/windows-update-for-business-configure.md)  
  - [iOS 更新の管理](../protect/software-updates-ios.md)  
- [Azure Active Directory](https://docs.microsoft.com/azure/active-directory)  
- [ユーザーの管理](https://docs.microsoft.com/azure/active-directory/fundamentals/add-users-azure-active-directory)
- [グループとメンバーの管理](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-manage-groups)
- [トラブルシューティング](help-desk-operators.md)

## <a name="next-steps"></a>次の手順

MDM または MAM ソリューションの使用を開始する準備ができたら、Intune のセットアップ、デバイスの登録、およびポリシーの作成開始のためのさまざまな手順を進めます。 [Microsoft 365 のモバイル デバイス管理](https://docs.microsoft.com/microsoft-365/enterprise/mobility-infrastructure)に関する記事も推奨されるリソースです。
