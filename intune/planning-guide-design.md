---
title: "設計の作成"
description: "この記事では、Microsoft Intune のクラウド専用の設計と実装の設計を作成する方法について説明します。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a8e38e29-f5e3-4a71-a170-d3b1a06e37c6
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 3f08f110163159c1219492539107cc6b33c8012d
ms.sourcegitcommit: 79116d4c7f11bafc7c444fc9f5af80fa0b21224e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2017
---
# <a name="create-a-design"></a>設計の作成

[!INCLUDE[note for both-portals](./includes/note-for-both-portals.md)]

このガイドのセクションは、セクション 2 の他のトピックと併せて参照する必要があります。 この設計は、このガイドの前のセクションで収集した情報と決定に基づいています。 この設計セクションでは、Microsoft クラウド ベースのサービスである Intune スタンドアロンに注目します。

オンプレミスのインフラストラクチャに関する最低限の要件はありますが、目標、目的、および要件に合った適切なモバイル デバイス管理ソリューションとなるように設計計画に取り組みましょう。

また、通常、実装およびテスト フェーズの間に設計を変更し、発生した変更とその根拠を文書化します。 設計には、次のような項目が含まれます。

-   現在の環境

-   Intune の展開オプション

-   外部依存関係に対する ID の要件

-   デバイスのプラットフォームに関する考慮事項

-   配布する要件  

これらの各項目について詳しく説明します。 

## <a name="record-your-environment"></a>環境を記録する

設計を作成する前にまず、現在の環境を記録します。 現在の環境は設計上の決定に影響を与える可能性があるので、文書化し、Intune の設計に関する他の決定を行うときに参照する必要があります。 以下は、現在の環境を記録する方法の例です。

-   **クラウド内の ID**

    -   DirSync または Azure Active Directory (Azure AD) Connect を使用しているか

    -   環境がフェデレーションされているか

    -   多要素認証が有効か

-   **メール環境**

    -   Exchange が使われているかどうか、オンプレミスまたはクラウドのどちらか

    -   Exchange をクラウドに移行するプロジェクトの途中か

-   **現在の MDM ソリューション**

    -   他の MDM ソリューションを現在使っているか

    -   会社および BYOD のユース ケース シナリオに対してどのような MDM ソリューションを使っているか

    -   どのような機能を使っているか (例: アプリ デバイスの設定、Wi-Fi の構成など)

    -   どのようなデバイス プラットフォームがサポートされているか

    -   MDM ソリューションを使っているのはどのようなグループで、ユーザー数はどれくらいか

-   **証明書ソリューション**

    -   証明書ソリューションを導入しているか

    -   使っている証明書の種類

-   **システム管理**

    -   PC およびサーバーの環境をどのように管理しているか

    -   System Center Configuration Manager を使っているか サードパーティ製のシステム管理プラットフォームを使っているか

-   **VPN ソリューション**

    -   どのような VPN ソリューションを使っているか

    -   会社と BYOD の両方のユース ケース シナリオに使っているか

現在の MDM 環境を記録するときは、環境を変更する可能性がある実施中のプロジェクトまたは他の計画に注意する必要があります。 Intune の設計を作成するときに役立つ現在の環境の記録方法の例を次に示します。

| **ソリューション項目** | **現在の環境** | **コメント** |
|:---:|:---:|:---:|
| **ID** | Azure AD、Azure AD Connect、フェデレーションなし、MFA なし | 年末まで MFA 有効化プロジェクト実施中 |                 
| **メール環境** | オンプレミスの Exchange、Exchange Online | 現在、オンプレミスの Exchange から Exchange Online に移行中。 メールボックスの 75% を移行済み。 残りの 25% は、Intune の試験運用が開始する前に移行される。 |                
| **SharePoint** | オンプレミスの SharePoint | SharePoint Online への移行計画はなし |  
| **現在の MDM** | Exchange ActiveSync |  |
| **証明書ソリューション** | Microsoft Server 2012 R2、AD 証明書サービス | Web サイト サーバー用に PKI のみを使用 |
| **システム管理** | System Center Configuration Manager CB 1606 | Intune ハイブリッド ソリューションの調査を希望 |
| **VPN ソリューション** | Cisco AnyConnect |  |

## <a name="choose-an-intune-deployment-option"></a>Intune の展開オプションを選択する

Intune には、スタンドアロンとハイブリッドの 2 種類の展開オプションがあります。 どちらがビジネス要件に合うかを判断します。 スタンドアロンとはクラウドで実行されている Intune サービスのことであり、ハイブリッドとは Intune と System Center Configuration Manager が統合されたものです。

- 詳しくは、「[Microsoft Intune スタンドアロンか System Center Configuration Manager を使用するハイブリッド モバイル デバイス管理を選択する](https://docs.microsoft.com/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management)」をご覧ください。

## <a name="intune-tenant-location"></a>Intune テナントの場所

世界的に展開している組織の場合、サービスに登録するときに確実にテナントが存在する場所を計画してください。 Intune のサブスクリプションに初めてサインアップするときに国を定義し、以下に示す世界中の地域にマップします。

-   北米

-   ヨーロッパ、中東、およびアフリカ

-   アジアおよび太平洋

>[!IMPORTANT]
> 国やテナントの場所を後で変更することはできません。

## <a name="external-dependencies"></a>外部依存関係

外部依存関係は Intune とは別のサービスや製品ですが、Intune の必要条件であるか、または Intune と統合される場合があります。 外部依存関係の要件およびその構成方法を知ることが重要です。 一般的な外部依存関係の例を以下に示します。

-   ID

-   ユーザーとデバイス グループ

-   PKI

以下ではこれらの一般的な外部依存関係について詳しく説明します。

### <a name="identity"></a>ID

ID は、組織に属している、デバイスに登録されているユーザーを識別する方法です。 Intune では、ユーザー ID プロバイダーとして Azure Active Directory (Azure AD) が必要です。 このサービスを既に使っている場合は、クラウドの既存の ID を利用できます。 さらに、オンプレミスのユーザー ID を Microsoft クラウド サービスと同期するには、Azure AD Connect が推奨されるツールです。 組織が Office 365 を既に使っている場合は、Intune でも同じ Azure Active Directory 環境を使うことが重要です。

Intune の ID 要件に関する詳細については、以下をご覧ください。

-   [ID の要件](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-overview#design-considerations-overview)についてはこちらをご覧ください。

-   [ディレクトリ同期の要件](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-directory-sync-requirements)についてはこちらをご覧ください。

-   [多要素認証の要件](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-multifactor-auth-requirements)についてはこちらをご覧ください。

### <a name="user-and-device-groups"></a>ユーザーとデバイス グループ

ユーザーとデバイス グループは、展開の対象を決定します。 これには、ポリシー、アプリケーション、プロファイルの展開対象が含まれます。 Intune クラウドは、ユーザーとデバイス グループのみをサポートします。必要なユーザーとデバイス グループを決定する必要があります。 すべてのグループをオンプレミスの Active Directory 内に作成してから、Azure Active Directory に同期することをお勧めします。 ユーザーおよびデバイス グループの計画と作成の詳細については、以下をご覧ください。

-   [ユーザーとデバイス グループの計画](/intune-classic/deploy-use/plan-your-user-and-device-groups)についてはこちらをご覧ください。

-   [ユーザーとデバイス グループを作成する方法](/intune-classic/deploy-use/use-groups-to-manage-users-and-devices-with-microsoft-intune)についてはこちらをご覧ください。

### <a name="public-key-infrastructure-pki"></a>公開キー基盤 (PKI)

公開キー基盤は、サービスに対する認証を安全に行うための証明書をデバイスまたはユーザーに提供します。 Intune は、Microsoft PKI インフラストラクチャをサポートします。 デバイスとユーザーの証明書をモバイル デバイスに発行し、証明書ベースの認証要件を満たすことができます。 証明書を実装する前に、証明書が必要かどうか、ネットワーク インフラストラクチャが証明書ベースの認証をサポートできるかどうか、および既存の環境で証明書が現在使用されているかどうかを、確認する必要があります。

VPN、Wi-Fi、または Intune でのメール プロファイルで証明書を使うことを計画している場合は、サポートされる [PKI インフラストラクチャが存在](/intune-classic/deploy-use/secure-resource-access-with-certificate-profiles)し、証明書プロファイルを作成して展開する準備ができていることを、確認する必要があります。

さらに、SCEP 証明書を発行する場合は、ネットワーク デバイス登録サービス (NDES) 機能をホストするサーバーおよび通信の実行方法を決定する必要があります。

Intune で証明書を構成する方法の詳細については、以下をご覧ください。

-   [SCEP 用の証明書インフラストラクチャを構成する方法](/intune-classic/deploy-use/configure-certificate-infrastructure-for-scep)についてはこちらをご覧ください。

-   [PFX 用の証明書インフラストラクチャを構成する方法](/intune-classic/deploy-use/configure-certificate-infrastructure-for-pfx)についてはこちらをご覧ください。

-   [Intune 証明書プロファイルを構成する方法](/intune-classic/deploy-use/configure-intune-certificate-profiles)についてはこちらをご覧ください。

-   [リソース アクセス ポリシーを構成する方法](/intune-classic/deploy-use/enable-access-to-company-resources-with-microsoft-intune)についてはこちらをご覧ください。

## <a name="device-platform-considerations"></a>デバイスのプラットフォームに関する考慮事項

デバイスを詳しく調べて次の正しい方法を理解する必要があります。

-   サポートされるデバイス プラットフォームの決定

-   [デバイス]

-   デバイスの所有権

-   一括登録

これらの項目について詳しく説明します。

### <a name="determine-supported-device-platforms"></a>サポートされるデバイス プラットフォームの決定

環境内に存在するデバイスを把握し、設計を作成するときにデバイスが Intune によってサポートされるかどうかを確認する必要があります。 Intune は、IOS、Android、Windows の各プラットフォームをサポートしています。

-   詳しくは、「[Intune 対応デバイス](/intune/supported-devices-browsers)」をご覧ください。

### <a name="devices"></a>[デバイス]

Intune は、モバイル デバイスを管理して、企業のデータをセキュリティで保護し、エンド ユーザーがより多くの場所から作業できるようにします。 Intune は複数のデバイス プラットフォームをサポートしているので、組織の設計でサポートされるデバイスおよび OS プラットフォームを文書化することをお勧めします。 ユース ケース要件のセクションで作成したデバイスとプラットフォームについて詳しく説明します。

また、OS プラットフォームとバージョンでデバイスの機能を確認するときにリストを参照するためのバージョンを知っていることもお勧めします。 次に例を示します。

| **デバイスのプラットフォーム** | **OS のバージョン** |
|:---:|:---:|
| iOS - iPhone | 9.0 以上 |                
| iOS - iPad | 8.0 以上 |               
| Android – Samsung Knox Standard | 4.0 以上 |
| Windows 10 タブレット | 10 以上 |

### <a name="device-ownership"></a>デバイスの所有権

Intune は、企業所有と BYOD 所有権の両方をサポートします。 デバイス登録マネージャーまたはデバイス登録プログラムによって登録されるデバイスは企業所有と見なされます。 たとえば、Apple DEP でデバイスを登録し、企業所有としてマークして、対象を絞った企業ポリシーとアプリを受け取るデバイス グループに配置できます。

企業と BYOD のユース ケースについて詳しくは、「[セクション 3: ユース ケースのシナリオの要件を決定する](planning-guide-requirements.md)」をご覧ください。

### <a name="bulk-enrollment"></a>一括登録

ポータル サイトでのセルフ サービス登録を補完するため、Intune にはデバイスの登録に使用できる複数の登録オプションがあります。 一括登録はプラットフォームに応じてさまざまな方法で実現できます。 一括登録が必要な場合は、まず一括登録方法を決定し、設計に組み込みます。 一括登録のさまざまな方法について詳しくは、以下をご覧ください。

-   [一括登録](/intune-classic/deploy-use/enroll-devices-in-microsoft-intune)。

## <a name="feature-requirements"></a>機能の要件

以下では、ユース ケース シナリオの要件に対応する次の機能について説明します。

-   使用条件ポリシー

-   [ポリシー]

-   リソース プロファイル

-   アプリ

-   コンプライアンス ポリシー

-   条件付きアクセス

これらの各項目について詳しく説明します。

### <a name="terms-and-conditions-policies"></a>使用条件ポリシー

使用条件を使って、登録する前にエンド ユーザーが受け入れる必要のあるポリシーまたは条件を説明できます。 Intune では、複数の使用条件ポリシーをユーザー グループに追加して展開できます。 使用条件ポリシーが必要かどうかを決定する必要があります。 必要な場合は、組織でこの情報を提供する責任者を決定します。

-   詳しくは、「[Microsoft Intune の使用条件ポリシー設定](/intune-classic/deploy-use/terms-and-condition-policy-settings-in-microsoft-intune)」をご覧ください。 使用条件ポリシーを文書化する方法の例を次に示します。

| **使用条件名** | **ユース ケース** | **対象グループ** |
|:---:|:---:|:---:|
| Corporate T&C | 企業 | 企業ユーザー |                 
| BYOD T&C | BYOD | BYOD ユーザー |                

### <a name="configuration-policies"></a>構成ポリシー

構成ポリシーは、デバイスのセキュリティ設定と機能を管理するために使われます。 構成ポリシーを設計するときは、ユース ケース要件セクションを参照して、Intune デバイスに必要な構成を決定します。 どの設定をどのように構成する必要があるか、およびその対象となるユーザーまたはデバイス グループを文書化します。

プラットフォームごとに少なくとも 1 つの構成ポリシーを作成する必要があります。 必要な場合は、プラットフォームごとに複数の構成ポリシーを作成できます。 次に示すのは、異なるプラットフォームとユース ケース シナリオに対して 4 つの異なる構成ポリシーを設計する例です。

| **ポリシー名** | **デバイスのプラットフォーム** | **設定** | **対象グループ** |   
|:---:|:---:|:---:|:---:|
| 企業 - iOS | iOS | PIN 必要、長さ: 6、クラウド バックアップの制限 | 企業デバイス |                                                           
| 企業 - Android | Android | PIN 必要、長さ: 6、クラウド バックアップの制限 | 企業デバイス |                                                           
| BYOD – iOS  | iOS | PIN 必要、長さ: 4 | BYOD デバイス |
| BYOD – Android  | Android | PIN 必要、長さ: 4 | BYOD デバイス |

### <a name="profiles"></a>Profiles

プロファイルは、エンド ユーザーが企業データに接続するのを補助するために使われます。 Intune は、さまざまな種類のプロファイルをサポートします。 [プロファイル](/intune-classic/deploy-use/enable-access-to-company-resources-with-microsoft-intune)を構成するときは、決定するユース ケースと要件を参照します。 すべてのデバイス プロファイルはプラットフォームの種類ごとに分類され、設計ドキュメントに含める必要があります。

-   証明書プロファイル

-   Wi-Fi プロファイル

-   VPN プロファイル

-   電子メールのプロファイル

プロファイルの各種類についてさらに詳しく説明します。

##### <a name="certificate-profiles"></a>証明書プロファイル

証明書プロファイルを使って、Intune はユーザーまたはデバイスに証明書を発行します。 Intune は以下をサポートします。

-   Simple Certificate Enrollment Protocol (SCEP)

-   信頼されたルート証明書

-   PFX 証明書

証明書が必要なユーザー グループ、必要な証明書プロファイルの数、証明書を展開するユーザー グループを、文書化することをお勧めします。

>[!NOTE]
> SCEP 証明書には信頼されたルート証明書が必要なので、SCEP 証明書の対象となるすべてのユーザーも信頼されたルート証明書を受け取る必要があります。 SCEP 証明書が必要な場合は、必要な SCEP 証明書テンプレートを設計して文書化します。

設計時に証明書を文書化する方法の例を次に示します。

| **種類** | **プロファイル名** | **デバイスのプラットフォーム** | **ユース ケース** |   
|:---:|:---:|:---:|:---:|
| ルート CA | 企業ルート CA | Android、iOS、Windows Mobile | 企業、BYOD  |                                                           
| SCEP | ユーザー証明書 | Android、iOS、Windows Mobile | 企業、BYOD |                                                           

##### <a name="wi-fi-profile"></a>Wi-Fi プロファイル

Wi-Fi プロファイルは、モバイル デバイスをワイヤレス ネットワークに自動的に接続するために使われます。 Intune では、サポートされるすべてのプラットフォームに Wi-Fi プロファイルを展開できます。

-   詳しくは、「[デバイスを構成すると、会社の Wi-Fi ネットワークに接続できます](/intune-classic/deploy-use/wi-fi-connections-in-microsoft-intune)」をご覧ください。

Wi-Fi プロファイルの設計の例を次に示します。

| **種類** | **プロファイル名** | **デバイスのプラットフォーム** | **ユース ケース** |   
|:---:|:---:|:---:|:---:|
| Wi-Fi | アジア Wi-Fi プロファイル | Android | 企業、BYOD アジア地域|                                                           
| Wi-Fi | 北米 Wi-Fi プロファイル | Android、iOS、Windows 10 Mobile | 企業、BYOD 北米地域 |                                                           

##### <a name="vpn-profile"></a>VPN プロファイル

VPN プロファイルを使うと、ユーザーはリモートの場所からネットワークに安全にアクセスできます。 Intune は、ネイティブ モバイル VPN 接続およびサード パーティ ベンダーからの VPN プロファイルをサポートします。

-   詳しくは、「[VPN connections in Microsoft Intune](/intune-classic/deploy-use/vpn-connections-in-microsoft-intune)」 (Microsoft Intune での VPN 接続) をご覧ください。

VPN プロファイルの設計を文書化する例を次に示します。

| **種類** | **プロファイル名** | **デバイスのプラットフォーム** | **ユース ケース** |   
|:---:|:---:|:---:|:---:|
| VPN | VPN Cisco any connect Profile | Android、iOS、Windows 10 Mobile | 企業、BYOD 北米およびドイツ|                                                           
| VPN | Pulse Secure | Android | 企業、BYOD アジア地域 |                                                           

##### <a name="email-profile"></a>電子メールのプロファイル

電子メール プロファイルを使うと、メール クライアントを接続情報とメール構成で自動的にセットアップできます。 Intune は、一部のデバイスで電子メール プロファイルをサポートします。

-   [電子メール プロファイル](/intune-classic/deploy-use/configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune)とサポートされるプラットフォームの詳細を参照してください。

電子メール プロファイルの設計を文書化する例を次に示します。

| **種類** | **プロファイル名** | **デバイスのプラットフォーム** | **ユース ケース** |   
|:---:|:---:|:---:|:---:|
| 電子メールのプロファイル | iOS email profile | iOS | 企業 – 情報ワーカー BYOD |                                                           
| 電子メールのプロファイル | Android Knox email profile | Android Knox | BYOD |

### <a name="apps"></a>アプリ

Intune では、複数の方法でユーザーまたはデバイスにアプリを提供できます。 提供できるアプリの種類は、ソフトウェア インストーラー アプリ、パブリック アプリ ストアからのアプリ、外部リンク、管理対象 iOS アプリなどです。 個々のアプリの展開だけでなく、iOS および Windows のボリューム購入プログラムを利用して、ボリューム購入アプリを管理および展開することもできます。 Intune によるアプリおよびボリューム購入プログラムのサポートについて詳しくは、以下をご覧ください。

-   [アプリの種類](/intune-classic/deploy-use/enroll-devices-in-microsoft-intune)についてはこちらをご覧ください。

-   [ビジネス向け iOS Volume Purchase Program (VPP)](/intune-classic/deploy-use/manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune) についてはこちらをご覧ください。

-   [ビジネス向け Windows ストア](/intune-classic/deploy-use/manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune)についてはこちらをご覧ください。

#### <a name="app-type-requirements"></a>アプリの種類の要件

アプリはユーザーとデバイスに展開できるので、どのアプリケーションを Intune で管理するか決めることをお勧めします。 リストを収集するときは、次の点を確認します。

-   アプリは、クラウド サービスとの統合を必要としますか。

-   すべてのアプリを BYOD 利用可能にしますか。

-   これらのアプリに使用できる展開オプションにはどのようなものがありますか。

-   会社では、パートナーの SaaS (サービスとしてのソフトウェア) アプリのデータにアクセスできるようにする必要はありますか。

-   アプリにはユーザーのデバイスからインターネットでアクセスする必要がありますか。

-   アプリは、アプリ ストアで一般に利用可能なものですか、またはカスタム基幹業務アプリですか。


>[!TIP]
> [Intune がサポートするアプリケーションの種類](/intune-classic/deploy-use/add-apps)を確認してください。

#### <a name="app-protection-policies"></a>アプリ保護ポリシー

アプリ保護ポリシーは、アプリケーションが企業データを管理する方法を定義することによって、データの損失を最小限に抑えます。 Intune は、モバイル アプリ管理で機能するように構築された任意のアプリケーションのアプリ保護ポリシーをサポートします。 アプリ保護ポリシーを設計するときは、特定のアプリで企業データに設ける制限を決める必要があります。 詳しくは、「[Microsoft Intune でモバイル アプリケーション管理ポリシーを使用してアプリ データを保護する](/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)」をご覧ください。 既存のアプリケーションおよび必要な保護を文書化する方法の例を以下に示します。

| **アプリケーション** | **目的** | **プラットフォーム** | **ユース ケース** | **アプリ保護ポリシー** |
|:---:|:---:|:---:|:---:|:---:|
| Outlook Mobile  | 利用可能 | iOS | 企業 - エグゼクティブ | 脱獄不可、ファイルを暗号化 |                                                         
| Word | 利用可能 | iOS、Android - Samsung Knox、非 Knox、Windows 10 Mobile | 企業、BYOD | 脱獄不可、ファイルを暗号化 |                                                         

#### <a name="compliance-policies"></a>Compliance ポリシー

コンプライアンス ポリシーは、デバイスが特定の要件に準拠しているかどうかを決定します。 Intune では、コンプライアンス ポリシーを使って、デバイスが準拠または非準拠のどちらと見なされるかを判断します。 準拠状態は、企業リソースへのアクセス制限に使用できます。 条件付きアクセスが必要な場合は、[デバイス コンプライアンス ポリシー](/intune-classic/deploy-use/introduction-to-device-compliance-policies-in-microsoft-intune)を設計することをお勧めします。 要件とユース ケースを参照し、必要なデバイス コンプライアンス ポリシーの数、および対象となるユーザー グループを決定します。 さらに、非準拠と見なされる前に、デバイスがチェックインせずにオフラインでいられる時間を決める必要があります。

コンプライアンス ポリシーの設計方法の例を次に示します。

| **ポリシー名** | **デバイスのプラットフォーム** | **設定** | **対象グループ** |   
|:---:|:---:|:---:|:---:|
| コンプライアンス ポリシー | iOS、Android - Samsung Knox、非 Knox、Windows 10 Mobile | PIN - 必要、脱獄不可 | 企業、BYOD |

#### <a name="conditional-access-policies"></a>条件付きアクセス ポリシー

条件付きアクセスは、準拠デバイスのみに企業リソースへのアクセスを許可するために使用します。 Intune は、Enterprise Mobility + Security (EMS) 全体と連携して、企業リソースへのアクセスを制御します。 条件付きアクセスが必要かどうか、およびセキュリティで保護する必要があるものを、決める必要があります。

-   詳しくは、「[Microsoft Intune で電子メール、Office 365、およびその他のサービスへのアクセスを制限する](/intune-classic/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune)」をご覧ください。

オンライン アクセスについては、条件付きアクセス ポリシーの対象となるプラットフォームおよびユーザー グループを決めます。

さらに、Exchange Online またはオンプレミスの Exchange 用の Intune サービス間コネクタをインストールして構成する必要があるかどうかを判断する必要があります。

Intune サービス間コネクタをインストールして構成する方法の詳細については、以下をご覧ください。

-   [Exchange Online](/intune-classic/deploy-use/intune-service-to-service-exchange-connector)

-   [Exchange On-premises](/intune-classic/deploy-use/intune-on-premises-exchange-connector)

条件付きアクセス ポリシーを文書化する方法の例を次に示します。

| **サービス** | **先進認証用プラットフォーム** | **基本認証** | **ユース ケース** |   
|:---:|:---:|:---:|:---:|
| Exchange Online | iOS、Android | Intune がサポートするプラットフォームの非準拠デバイスをブロックする | 企業、BYOD |
| SharePoint Online | iOS、Android |  | 企業、BYOD |

## <a name="next-section"></a>次のセクション

次のセクションでは、[Intune の実装プロセス](planning-guide-onboarding.md)に関するガイダンスについて説明します。
