---
title: "Microsoft Intune とは"
description: "Intune が Enterprise Mobility + Security ソリューションでモバイル デバイスを管理し、会社のデータを保護するしくみについて説明します。"
keywords: "Intune の概要"
author: Lindavr
ms.author: lindavr
manager: angrobe
ms.date: 07/28/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b4e778d-ac13-4c23-974f-5122f74626bc
ms.reviewer: pmay
ms.suite: ems
ms.custom: 
ms.openlocfilehash: 53115eba5e5150139b8ff0f359cde279df297d47
ms.sourcegitcommit: 79116d4c7f11bafc7c444fc9f5af80fa0b21224e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2017
---
# <a name="what-is-intune"></a>Intune とは何か

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

Intune はクラウドベースのエンタープライズ モビリティ管理 (EMM) サービスであり、会社のデータを守りながら、社員に生産的に働いてもらうことができます。 Intune では次のことができます。
* 社員が会社のデータにアクセスするために利用するモバイル デバイスを管理します。
* 社員が利用するモバイル アプリを管理します。
* 社員が会社の情報にアクセスし、共有する方法を制御し、会社の情報を保護します。
* デバイスやアプリが会社のセキュリティ要件に準拠するように管理します。

Intune は ID とアクセス制御のために Azure Active Directory (Azure AD) と、データ保護のために Azure Information Protection と密接に統合されます。

Office 365 と EMS の連携で、社員があらゆるデバイスを生産的に活用し、同時に会社の情報を保護することができます。 Office 365 と EMS の組み合わせで、生産性、ID、アクセス制御、管理、データ保護を含む Enterprise Mobility の完全な統合スイートとなります。 これにより、効果的にモビリティ ソリューションを組織に展開し、運用することができます。

## <a name="how-does-intune-work"></a>Intune のしくみ
Intune は、モバイル デバイス管理 (MDM) とモバイル アプリ管理 (MAM) を提供します。 そして Intune の MDM 機能と MAM 機能がデータの保護とコンプライアンスのシナリオの EMS スイートに貢献します。  

Intune の MDM/MAM 機能と EMS データ保護の利用方法は、[解決しようとしているビジネス上の問題](#common-business-problems-that-intune-helps-solve)によって異なります。 たとえば、
* 小売店の交代勤務従業員に共有させる単回使用デバイスのプールを作成する場合、MDM をかなり利用することになります。
* 個人のデバイスで企業データにアクセスすること (BYOD) を社員に許可する場合、MAM とデータ保護に頼ります。  
* 情報作業者に会社の電話を与える場合、この技術のすべてに大きく依存します。

## <a name="intune-mobile-device-management-mdm-explained"></a>Intune のモバイル デバイス管理 (MDM) の説明
MDM は、モバイル オペレーティング システムで利用できるプロトコルまたは API を利用して動作します。 含まれるタスク:
* デバイスを登録して管理し、企業サービスにアクセスしているデバイスの目録を IT に与える
* 会社のセキュリティ/健全性基準を満たすようにデバイスを構成する
* 企業サービスにアクセスするための証明書と Wi-Fi/VPN プロファイルを提供する
* 企業基準に対するデバイスの準拠状況を測定し、報告する
* 管理対象のデバイスから会社のデータを削除する  

**企業データのアクセス制御**は MDM 機能であると考える人がいます。 Microsoft の考え方は違います。それはモバイル オペレーティング システムが提供する機能ではないからです。 それはむしろ、ID プロバイダーが提供するサービスです。 この場合、ID プロバイダーは、Microsoft の ID/アクセス管理システムである、Azure Active Directory (Azure AD) です。  

Intune は Azure AD と連携し、さまざまなアクセス制御シナリオを可能にします。 たとえば、Exchange のような企業サービスにデバイスでアクセスするには、モバイル デバイスが企業基準に準拠する必要があるように設定できます。 同様に、特定のモバイル アプリに企業サービスを制限できます。 たとえば、Exchange Online へのアクセスを Outlook または Outlook Mobile だけに制限できます。

## <a name="intune-mobile-app-management-mam-explained"></a>Intune モバイル アプリ管理 (MAM) の説明
MAM について話すとき、Microsoft ソリューションが可能にする、IT プロフェッショナルがモバイル アプリで行う次のような作業が話題に上ります。
* モバイル アプリを従業員に発行する
* アプリを構成する
* モバイル アプリによる企業データの使用と共有を制御する
* モバイル アプリから会社のデータを削除する   
* モバイル アプリを更新する
* モバイル アプリ インベントリについて報告する
* モバイル アプリの使用状況を追跡する

MAM という用語は、上記のいずれかを表す言葉として、または特定の組み合わせを表す言葉として使用されています。 特に、アプリ構成の概念 (つまり、[iOS で管理対象アプリ構成](https://developer.apple.com/library/content/samplecode/sc2279/Introduction/Intro.html)のような技術を使用すること) とモバイル アプリ内の企業データ セキュリティの概念は一般的に混同されています。 一部のモバイル アプリで、データ セキュリティ機能の構成を許可する設定が露出するためです。

これがオペレーティング システムのデータ保護機能 (例: Windows 10 の Windows 情報保護など、MDM 機能) と組み合わさることで、モバイル デバイスがさまざまな方法で保護されます。

EMS の他のサービスと共に Intune を使用すると、モバイルオペレーティング システムとモバイル アプリ自体がアプリ構成を介して提供するセキュリティに加え、組織のモバイル アプリ セキュリティを提供できます。 EMS で管理されるアプリには、次のようなさまざまなモバイル アプリへのアクセスとデータ保護が与えられます。

* [シングル サインオン](https://docs.microsoft.com/azure/active-directory/active-directory-appssoaccess-whatis)  
*   [多要素認証](https://docs.microsoft.com/multi-factor-authentication/multi-factor-authentication)
* [アプリの条件付きアクセス (モバイル アプリに企業データが含まれる場合、アクセスを許可する)](app-based-conditional-access-intune.md)
* [同じアプリ内で企業データと個人データを分離する](app-protection-policy.md)
* [アプリの保護ポリシー (PIN、暗号化、名前を付けて保存、クリップボードなど)](app-protection-policies.md)
* [モバイル アプリから企業データを消去する](apps-selective-wipe.md)
* [Rights Management の保護](https://docs.microsoft.com/information-protection/understand-explore/what-is-azure-rms)

![アプリ管理データ セキュリティのレベルを示す画像](./media/managing-mobile-apps.png)

### <a name="intune-mobile-app-security"></a>Intune モバイル アプリ セキュリティ
アプリ セキュリティの提供は MAM の一部です。Intune では、モバイル アプリ セキュリティは次のような意味になります。
* 企業の IT 認識と個人情報を分離すること
* コピー、切り取り/貼り付け、保存、表示など、企業情報に対してユーザーが行う操作を制限すること
* モバイル アプリから企業データを削除すること (選択的なワイプや企業ワイプとも呼ばれています)

Intune がモバイル アプリ セキュリティを提供する方法の 1 つとして、**アプリの保護ポリシー**機能があります。 アプリの保護ポリシーでは、Azure AD ID を利用し、個人データと企業データが分離されます。 企業の資格情報を利用してアクセスされるデータには、追加の企業保護機能が与えられます。

ユーザーが自分の企業資格情報で自分のデバイスにログオンすると、そのユーザーの企業 ID により、自分の個人 ID では拒否されるデータにアクセスできます。 その企業データが使用されるとき、Intune とその他の EMS 技術によりその保存と共有が制御されます。 ユーザーが自分のデバイスに自分の個人 ID でログオンするときにアクセスされるデータには同じ保護機能は適用されません。 このように、IT 部署が企業データを管理し、エンド ユーザーが個人データを管理し、プライバシーを保護します。

## <a name="emm-with-and-without-device-enrollment"></a>デバイス登録あり/なしの EMM
ほとんどの企業向けモバイル管理ソリューションで、基本的なモバイル デバイス技術とモバイル アプリ技術に対応しています。 そのようなソリューションは、通常、組織の MDM ソリューションに登録されているデバイスに関連します。 Intune はこれらのシナリオをサポートし、さらに、多くの “登録なし” シナリオに対応しています。  

組織が “登録なし” シナリオを採用する程度はさまざまです。 それを標準とする組織もあります。 個人のタブレットなど、コンパニオン デバイスでそれを許可する組織もあります。 まったくサポートしない組織もあります。 まったくサポートせず、従業員のすべてのデバイスに MDM 登録を要求する場合でも、通常、コントラクター、ベンダー、特定の例外を持つその他のデバイスに関して、"登録なし" シナリオがサポートされます。

登録済みデバイスでも Intune の “登録なし” 技術を利用できます。 たとえば、MDM に登録されているデバイスには、モバイル オペレーティング システムによりオープンイン保護が与えられていることがあります。 (オープンイン保護は、Outlook などの 1 つのアプリから Word などの別のアプリで、両方のアプリが MDM プロバイダーによって管理されている場合を除き、ドキュメントを開くことを制限する iOS の機能です。)さらに、IT 部署はアプリの保護ポリシーを EMS で管理するモバイル アプリに提供し、名前を付けて保存を制御したり、多要素認証を提供したりすることがあります。

組織がモバイル デバイスやモバイル アプリを登録する場合でも登録しない場合でも、Intune は、EMS の一部として、社員の生産性を強化し、同時に企業データを保護するためのツールを提供します。

## <a name="common-business-problems-that-intune-helps-solve"></a>Intune が解決に役立つ一般的なビジネス問題
次のビジネス問題の一覧は、Microsoft が提供するソリューションに関する詳細情報にリンクしています。 最後の項目だけ、ソリューションの一部として MDM 登録が要求されます。

* [モバイル デバイスでアクセスできるようにオンプレミスの電子メールとデータを保護する](common-scenarios.md#protecting-your-on-premises-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices)
* [モバイル デバイスで安全にアクセスできるように Office 365 の電子メールとデータを保護する](common-scenarios.md#protecting-your-office-365-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices)
* [社員向けに企業所有の携帯電話を用意する](common-scenarios.md#issue-corporate-owned-phones-to-your-employees)
* [すべての従業員に "Bring your own device" (BYOD) プログラムという個人デバイス プログラムを提供する](common-scenarios.md#offer-a-bring-your-own-device-program-to-all-employees)
* [公共の場所から Office 365 に安全にアクセスできるようにする](common-scenarios.md#enable-your-employees-to-securely-access-office-365-from-an-unmanaged-public-kiosk)
* [タスク ワーカー向けに制限付きの共有タブレットを用意する](common-scenarios.md#issue-limited-use-shared-tablets-to-your-employees)

### <a name="next-steps"></a>次のステップ
* [Intune の一般的な使用方法](common-scenarios.md)を読む
* [Intune の 30 日間の評価版](free-trial-sign-up.md)を使用して製品の理解を深める
* Intune の[技術的要件と機能](supported-devices-browsers.md)を調べる
