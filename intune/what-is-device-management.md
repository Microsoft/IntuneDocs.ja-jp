---
title: Microsoft 365 でのデバイス管理
description: Microsoft 365 Enterprise には Microsoft Intune が含まれています。 一般的なシナリオを含め、Intune で組織のデバイス管理とモバイル アプリケーション管理を行う方法と Intune を使用して、環境に Microsoft 365 を展開する方法を説明します。
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/21/2018
ms.topic: conceptual
audience: ITPro
ms.prod: microsoft-365-enterprise
ms.service: ''
ms.technology: ''
ms.custom: intune
ms.assetid: 0649d310-43a7-4b01-85d2-da255d03e1da
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 93e34c3de77dde59b87829617b8cbbd2614f7081
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/02/2019
ms.locfileid: "57231249"
---
# <a name="what-is-device-management"></a>デバイス管理とは 

すべての管理者の重要なタスクは、組織のリソースとデータを保護することです。 このタスクがデバイス管理です。 ユーザーは多くのデバイスを使用して、個人のファイルを開いて共有したり、Web サイトにアクセスしたり、アプリやゲームをインストールしたりしています。 これらの同じユーザーは、従業員や学生でもあり、各自のデバイスを使用して、電子メールや OneNote などの仕事や学校のリソースにアクセスしたいと考えます。 *デバイス管理*を使用して、組織のリソースとデータを保護できます。 

デバイス管理プロバイダーを使用することで、組織では、承認されたユーザーとデバイスだけが機密情報にアクセスできるようにすることができます。 同様に、デバイスのユーザーは、自分のデバイスが組織のセキュリティ要件を満たしていることがわかっているため、安心して自分の電話から作業データにアクセスできます。 組織には、**リソースを保護するために何を使用すべきか**という疑問があると考えられます。

この点で、[Microsoft Intune](https://docs.microsoft.com/intune/introduction-intune) が役立ちます。 Intune ではモバイル デバイス管理 (MDM) とモバイル アプリケーション管理 (MAM) を行います。 MDM または MAM ソリューションの主要なタスクには次のようなものがあります。

- 多様なモバイル環境のサポート &mdash; iOS、Android、Windows、および macOS デバイスを安全に管理します
- デバイスやアプリを組織のセキュリティ要件に準拠させます
- 会社所有のデバイスと個人のデバイスで、組織のデータの安全を確保するために役立つポリシーを作成します
- 1 つの統合されたモバイル ソリューションを使用して、これらのポリシーを適用し、デバイス、アプリ、ユーザー、およびグループの管理に役立てます。

Intune は Microsoft 365 に含まれ、Azure Active Directory (Azure AD) と統合されます。 Azure AD は、アクセス権を持つユーザーとそれらのユーザーがアクセスできる対象を制御するために役立ちます。

## <a name="hello-intune"></a>Intune の紹介
Microsoft などの多くの組織で、Intune を使用して、ユーザーが会社所有のモバイル デバイスや個人のデバイスからアクセスする機密データをセキュリティ保護しています。 Intune には、デバイスとアプリの構成ポリシー、ソフトウェア更新ポリシー、インストールの状態 (およびグラフ、テーブル、レポート) などの機能を備え、データ アクセスをセキュリティ保護して、監視するために役立ちます。

ユーザーがさまざまなプラットフォームを使用した複数のデバイスを所有していることはよくあることです。 たとえば、従業員は、仕事に Surface Pro を使用し、個人の生活では Android モバイル デバイスを使用していることがあります。 また、個人がこれらの複数のデバイスから Microsoft Outlook や SharePoint などの組織のリソースにアクセスすることもよくあることです。

Intune により、ユーザーごと、および iOS、macOS、Android、Windows などの各デバイスで実行されるさまざまなプラットフォームごとに、複数のデバイスを管理できます。 Intune では、デバイス プラットフォーム別にポリシーと設定が分別されるため、特定のプラットフォームのデバイスを簡単に管理し、表示できます。

**[一般的なシナリオ](https://docs.microsoft.com/intune/common-scenarios)** は、モバイル デバイスを使用する際のよくある疑問を Intune によって解決する方法を確認できる優れたリソースです。 以下に関するシナリオを参照できます。  
- オンプレミスの Exchange での電子メールの保護
- Office 365 への安全なアクセス
- 個人のデバイスを使用して、組織のリソースにアクセスする

## <a name="integration-with-secure-and-protect-services"></a>セキュリティおよび保護サービスとの統合
すべてのデバイス管理ソリューションの主要なタスクは、セキュリティと保護を実現することです。 このタスクを実現するために、Intune は他のサービスとの統合に大きな役割を果たします。 次に例を示します。

- **Microsoft 365** は一般的な IT タスクを簡略化する重要なコンポーネントです。 Microsoft 365 管理センターを使用することで、ユーザーの作成、グループの管理、Intune や Azure Active Directory などの他のサービスへのアクセスが可能になります。 たとえば、Microsoft 365 で iOS デバイス グループを作成できます。 さらに、Intune を使用して、アプリ ストアへのアクセス、AirDrop の使用、iCloud へのバックアップ、Apple の Web フィルターの使用などの iOS 機能に焦点を合わせたポリシーを iOS デバイス グループにプッシュできます。

- **Windows Defender** には、Windows 10 デバイスを保護するための多くのセキュリティ機能が含まれています。 たとえば、Intune と Windows Defender を一緒に使用すると、次のことができます。 

    - [Windows Defender SmartScreen](https://docs.microsoft.com/intune/endpoint-protection-windows-10) を有効にして、モバイル デバイス上のファイルとアプリでの不審なアクティビティを検索できます。 
    - [Windows Defender Advanced Threat Protection (ATP)](https://docs.microsoft.com/intune/advanced-threat-protection) を使用して、モバイル デバイスでのセキュリティ違反を防止し、会社のリソースからユーザーをブロックすることによって、セキュリティ違反の影響を制限できます。

- **条件付きアクセス**は、Azure Active Directory の機能で、Intune と適切に統合します。 [条件付きアクセス](https://docs.microsoft.com/intune/conditional-access)を使用すると、準拠しているデバイスだけが電子メール、SharePoint、およびその他のアプリへのアクセスが許可されていることを確信できます。 

## <a name="choose-the-device-management-solution-thats-right-for-you"></a>適切なデバイス管理ソリューションの選択

デバイス管理にアプローチする方法はいくつかあります。 1 つ目は、Intune に組み込まれているすべての機能を使用してデバイスのすべての側面を管理できます。 これは、**モバイル デバイス管理 (MDM):** と呼ばれます。 このアプローチでは、ユーザーが自分のデバイスを "登録" し、証明書を使用して Intune と通信します。 IT 管理者は、デバイスでアプリをプッシュしたり、デバイスを特定のオペレーティング システムに限定したり、個人のデバイスをブロックしたりすることができます。 デバイスの紛失や盗難時は、デバイスからすべてのデータを削除することもできます。 

2 つ目のアプローチとして、デバイス上のアプリを管理します。 これは、**モバイル アプリケーション管理 (MAM)** と呼ばれます。 このアプローチでは、ユーザーは、個人のデバイスを使用して、組織のリソースにアクセスにできます。 電子メールや SharePoint などのアプリを開くときに、ユーザーは追加の認証を求められます。 デバイスの紛失や盗難時には、デバイスからすべての組織のデータを削除できます。 

[MDM と MAM](https://docs.microsoft.com/intune/byod-technology-decisions) を組み合わせて使用することもできます。

Intune をセットアップするときに、Azure portal でのみ作業してデバイスを管理するか、または Intune と Microsoft 365 を一緒に使用してデバイスを管理するかを選択することもできます。 「[Migrating mobile device management to Intune in the Azure portal](https://www.microsoft.com/itshowcase/Article/Content/1042/Migrating-mobile-device-management-to-Intune-in-the-Azure-portal)」 (Azure portal でモバイル デバイス管理を Intune に移行する) で、Microsoft IT が最新のデバイス管理アプローチを選択した状況と学んだ教訓についてご覧ください。 

## <a name="simplify-it-tasks-using-the-device-management-dashboard"></a>デバイス管理ダッシュ ボードを使用して IT タスクを簡略化する

[デバイス管理ダッシュ ボード](https://devicemanagement.portal.azure.com/)は、モバイル デバイスに関するタスクを管理し、実行するためのワンストップ ショップです。 このダッシュ ボードには、Intune や Azure Active Directory などのデバイス管理とクライアント アプリを管理するために使用するサービスが含まれています。 

デバイス管理ダッシュボードでは、次のことができます。

- [デバイスの登録](https://docs.microsoft.com/intune/device-enrollment)
- [デバイス コンプライアンスの設定](https://docs.microsoft.com/intune/device-compliance-get-started)
- [デバイスの管理](https://docs.microsoft.com/intune/device-management)
- [アプリの管理](https://docs.microsoft.com/intune/app-management)  
- [iOS 電子ブック](https://docs.microsoft.com/intune/vpp-ebooks-ios)  
- [Exchange On-premises Connector をインストールする](https://docs.microsoft.com/intune/exchange-connector-install)  
- [ロールの管理](https://docs.microsoft.com/intune/role-based-access-control)  
- ソフトウェア更新プログラムの管理
  - [Windows 10 更新の管理](https://docs.microsoft.com/intune/windows-update-for-business-configure)  
  - [iOS 更新の管理](https://docs.microsoft.com/intune/software-updates-ios)  
- [Azure Active Directory](https://docs.microsoft.com/azure/active-directory)  
- [ユーザーの管理](https://docs.microsoft.com/azure/active-directory/fundamentals/add-users-azure-active-directory)
- [グループとメンバーの管理](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-manage-groups)
- [トラブルシューティング](https://docs.microsoft.com/intune/help-desk-operators)

## <a name="next-step"></a>次の手順
MDM または MAM ソリューションの使用を開始する準備ができたら、Intune のセットアップ、デバイスの登録、およびポリシーの作成開始のためのさまざまな手順を進めます。[Microsoft 365 のモバイル デバイス管理](https://docs.microsoft.com/microsoft-365/enterprise/mobility-infrastructure)に関する記事を参照してください。 
