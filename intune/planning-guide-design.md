---
title: "設計の作成"
description: "この記事では、Microsoft Intune のクラウド専用の設計と実装の設計を作成する方法について説明します。"
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a8e38e29-f5e3-4a71-a170-d3b1a06e37c6
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.custom: 
ms.openlocfilehash: bd8f3372f3546b5fba20a253611e382f780b3236
ms.sourcegitcommit: 94d3d86f8ae9f82a9872384bbaae53580036a4ff
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2017
---
# <a name="create-a-design"></a>設計の作成

Intune の設計は、[このガイドの他のセクション](planning-guide.md)で収集した情報と行った決定に基づいています。 次のものを統合するのに役立ちます。

-   現在の環境

-   Intune の展開オプション

-   外部依存関係に対する ID の要件

-   デバイスのプラットフォームに関する考慮事項

-   配布する要件  

オンプレミスのインフラストラクチャに関する最低限の要件はあるものの、設計計画があれば、目標、目的、および要件に合った適切なモバイル デバイス管理ソリューションを手に入れるために役立ちます。

これらの各項目について詳しく説明します。 

## <a name="record-your-current-environment"></a>現在の環境を記録する
また、実装とテストのフェーズで設計に変更が発生することはよくあります。 設計計画を使用して、そのような変更が発生した場合に変更の内容とその背後にある論理的根拠を文書化します。

現在の環境は設計上の決定に影響を与える可能性があるので、文書化し、Intune の設計に関する他の決定を行うときに参照する必要があります。 以下は、現在の環境を記録する方法の例です。

-   **クラウド内の ID**

    -   DirSync または Azure Active Directory (Azure AD) Connect を使用しているか

    -   環境がフェデレーションされているか

    -   多要素認証 (MFA) が有効になっているか

-   **メール環境**

    -   Exchange を使っているか それはオンプレミスか、クラウドか

    -   Exchange をクラウドに移行するプロジェクトの途中か

-   **現在のモバイル デバイス管理 (MDM) ソリューション**

    -   他の MDM ソリューションを現在使っているか

    -   会社および BYOD のユース ケース シナリオに対してどのような MDM ソリューションを使っているか

    -   どのような機能を使っているか (例: アプリ デバイスの設定、Wi-Fi の構成)

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

現在の MDM 環境を記録するときは、環境に影響を与える可能性がある実施中のプロジェクトまたは他の計画に注意する必要があります。 Intune の設計を作成するときに現在の環境を記録する方法の例を次に示します。

| **ソリューション項目** | **現在の環境** | **コメント** |
|---|---|---|
| **ID** | Azure AD、Azure AD Connect、フェデレーションなし、MFA なし | 年末まで MFA 有効化プロジェクト実施中 |                 
| **メール環境** | オンプレミスの Exchange、Exchange Online | 現在、オンプレミスの Exchange から Exchange Online に移行中。 メールボックスの 75% を移行済み。 残りの 25% は、Intune の試験運用が開始する前に移行される。 |                
| **SharePoint** | オンプレミスの SharePoint | SharePoint Online への移行計画はなし |  
| **現在の MDM** | Exchange ActiveSync |  |
| **証明書ソリューション** | Microsoft Server 2012 R2、AD 証明書サービス | Web サイト サーバー用に PKI のみを使用 |
| **システム管理** | System Center Configuration Manager CB 1606 | Intune ハイブリッド ソリューションの調査を希望 |
| **VPN ソリューション** | Cisco AnyConnect |  |


[上記の表のテンプレートをダウンロード](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0)して Intune 設計計画を作成することができます。

## <a name="choose-an-intune-deployment-option"></a>Intune の展開オプションを選択する

Intune には、スタンドアロンとハイブリッドの 2 種類の展開オプションがあります。 スタンドアロンとはクラウドで実行されている Intune サービスのことであり、ハイブリッドとは Intune と System Center Configuration Manager が統合されたものです。 このガイドは、基本的にスタンドアロン オプション用です。 [どちらのオプションがビジネス要件に合うかを判断する](https://docs.microsoft.com/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management)には、こちらをご覧ください。

## <a name="intune-tenant-location"></a>Intune テナントの場所

世界的に展開している組織の場合、サービスに登録するときにテナントが存在する場所を確実に計画してください。 Intune のサブスクリプションに初めてサインアップするときに国を定義し、以下に示す世界中の地域にマップします。

-   北米

-   ヨーロッパ、中東、およびアフリカ

-   アジアおよび太平洋

>[!IMPORTANT]
> 国やテナントの場所を後で変更することはできません。

## <a name="external-dependencies"></a>外部依存関係

外部依存関係は Intune とは別のサービスや製品ですが、Intune の必要条件であるか、または Intune と統合される場合があります。 外部依存関係の要件およびその構成方法を明らかにすることが重要です。 一般的な外部依存関係の例を以下に示します。

-   ID

-   ユーザーとデバイス グループ

-   公開キー基盤 (PKI)

以下ではこれらの一般的な外部依存関係について詳しく説明します。

### <a name="identity"></a>ID

ID は、組織に属している、デバイスに登録されているユーザーを識別する方法です。 Intune では、ユーザー ID プロバイダーとして Azure Active Directory (Azure AD) が必要です。 このサービスを既に使っている場合は、クラウドの既存の ID を利用できます。 さらに、オンプレミスのユーザー ID を Microsoft クラウド サービスと同期するには、Azure AD Connect が推奨されるツールです。 組織が Office 365 を既に使っている場合は、Intune でも同じ Azure AD 環境を使うことが重要です。

次に示す Intune の ID 要件に関する詳細情報をご確認ください。

- [ID の要件](https://docs.microsoft.com/en-us/azure/active-directory/understand-azure-identity-solutions)については、こちらをご覧ください。

- [ディレクトリ同期の要件](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnect)については、こちらをご覧ください。

- [多要素認証の要件](https://docs.microsoft.com/en-us/azure/multi-factor-authentication/multi-factor-authentication-get-started-cloud)については、こちらをご覧ください。

### <a name="user-and-device-groups"></a>ユーザーとデバイス グループ

ユーザー グループとデバイス グループによって、ポリシー、アプリケーション、プロファイルなどを展開する対象が決まります。 どのようなユーザー グループとデバイス グループが必要になるかを決定する必要があります。

すべてのグループをオンプレミスの Active Directory 内に作成してから、Azure AD に同期することをお勧めします。 ユーザー グループとデバイス グループの計画と作成については、次の情報を参照してください。

-   [ユーザーとデバイス グループを計画する](users-add.md)

-   [ユーザー グループとデバイス グループを作成する](groups-add.md)

### <a name="public-key-infrastructure-pki"></a>公開キー基盤 (PKI)
公開キー基盤は、サービスに対する認証を安全に行うための証明書をデバイスまたはユーザーに提供します。 Intune は、Microsoft PKI インフラストラクチャをサポートします。 デバイスとユーザーの証明書をモバイル デバイスに発行し、証明書ベースの認証要件を満たすことができます。 証明書を使用する前に、証明書が必要かどうか、ネットワーク インフラストラクチャが証明書ベースの認証をサポートできるかどうか、および既存の環境で証明書が現在使用されているかどうかを、確認する必要があります。

VPN、Wi-Fi、または Intune での電子メール プロファイルで証明書を使うことを計画している場合は、サポートされる [PKI インフラストラクチャが存在](certificates-configure.md)し、証明書プロファイルを作成して展開する準備ができていることを、確認する必要があります。

さらに、SCEP 証明書を発行する場合は、ネットワーク デバイス登録サービス (NDES) 機能をホストするサーバーおよび通信の実行方法を決定する必要があります。

詳細については、下記のリンクをクリックしてください。

-   [Intune 証明書プロファイルを構成する方法](certificates-configure.md)

-   [SCEP 用の証明書インフラストラクチャを構成する方法](certificates-scep-configure.md)についてはこちらをご覧ください。

-   [PFX 用の証明書インフラストラクチャを構成する方法](certficates-pfx-configure.md)




## <a name="device-platform-considerations"></a>デバイスのプラットフォームに関する考慮事項

デバイスの次の側面について詳細に検討し、デバイスを正しく管理する方法を理解してください。

-   サポートされるデバイス プラットフォーム

-   [デバイス]

-   デバイスの所有権

-   一括登録

これらの項目について詳しく説明します。

### <a name="determine-supported-device-platforms"></a>サポートされるデバイス プラットフォームの決定

環境内に存在するデバイスを把握し、設計を作成するときにデバイスが Intune によってサポートされるかどうかを確認する必要があります。 Intune は、IOS、Android、Windows の各プラットフォームをサポートしています。

[Intune でサポートされているデバイスの完全な一覧](supported-devices-browsers.md)については、こちらをご覧ください。

### <a name="devices"></a>[デバイス]

Intune は、モバイル デバイスを管理して、企業のデータをセキュリティで保護し、エンド ユーザーがより多くの場所から作業できるようにします。 Intune は多数のデバイス プラットフォームをサポートしているので、組織の設計でサポートされるデバイスおよび OS プラットフォームとバージョンを文書化することをお勧めします。 たとえば、

| **デバイスのプラットフォーム** | **OS のバージョン** |
|:---:|:---:|
| iOS - iPhone | 9.0 以上 |                
| iOS - iPad | 8.0 以上 |               
| Android – Samsung Knox Standard | 4.0 以上 |
| Windows 10 タブレット | 10 以上 |


[上記の表のテンプレートをダウンロード](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0)してデバイスの一覧を作成することができます。
### <a name="device-ownership"></a>デバイスの所有権

Intune は、企業所有のデバイスと個人のデバイスの両方をサポートします。 デバイス登録マネージャーまたは Device Enrollment Program によって登録されるデバイスは企業所有と見なされます。 たとえば、Apple Device Enrollment Program (DEP) でデバイスを登録し、企業所有とマークして、対象を絞った企業ポリシーとアプリを受け取るデバイス グループに配置できます。

企業と BYOD のユース ケースについて詳しくは、「[セクション 3: ユース ケースのシナリオの要件を決定する](planning-guide-requirements.md)」をご覧ください。

### <a name="bulk-enrollment"></a>一括登録

 プラットフォームに応じたさまざまな方法でデバイスを一括登録できます。 一括登録が必要な場合は、まず[一括登録方法を決定](device-enrollment.md)し、設計に組み込みます。

## <a name="feature-requirements"></a>機能の要件

以下では、ユース ケース シナリオの要件に対応する次の機能について説明します。

-   使用条件ポリシー

-   構成ポリシー

-   リソース プロファイル

-   アプリ

-   コンプライアンス ポリシー

-   条件付きアクセス

これらの各項目について詳しく説明します。

### <a name="terms-and-conditions-policies"></a>使用条件ポリシー

[使用条件](terms-and-conditions-create.md)を使って、デバイスを登録する前にエンド ユーザーが受け入れる必要のあるポリシーまたは条件を説明できます。 Intune では、複数の使用条件ポリシーをユーザー グループに追加して展開できます。

使用条件ポリシーが必要かどうかを決定する必要があります。 必要な場合は、組織でこの情報を提供する責任者を決定します。 使用条件ポリシーを文書化する方法の例を次に示します。

| **使用条件名** | **ユース ケース** | **対象グループ** |
|:---:|:---:|:---:|
| Corporate T&C | 企業 | 企業ユーザー |                 
| BYOD T&C | BYOD | BYOD ユーザー |                


[上記の表のテンプレートをダウンロード](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0)して、使用条件をユーザー グループにマップすることができます。

### <a name="configuration-policies"></a>構成ポリシー

構成ポリシーを使用して、デバイスのセキュリティ設定と機能を管理します。 構成ポリシーを設計するときは、ユース ケース要件セクションを参照して、Intune デバイスに必要な構成を決定します。 設定とその構成方法を文書化します。 また、それらの構成がどのユーザー グループまたはデバイス グループを対象とするかも文書化します。

プラットフォームごとに少なくとも 1 つの構成ポリシーを作成する必要があります。 必要な場合は、プラットフォームごとに複数の構成ポリシーを作成できます。 次に示すのは、異なるプラットフォームとユース ケース シナリオに対して 4 つの異なる構成ポリシーを設計する例です。

| **ポリシー名** | **デバイスのプラットフォーム** | **設定** | **対象グループ** |   
|:---:|:---:|:---:|:---:|
| 企業 - iOS | iOS | PIN 必要、長さ: 6、クラウド バックアップの制限 | 企業デバイス |                                                           
| 企業 - Android | Android | PIN 必要、長さ: 6、クラウド バックアップの制限 | 企業デバイス |                                                           
| BYOD – iOS  | iOS | PIN 必要、長さ: 4 | BYOD デバイス |
| BYOD – Android  | Android | PIN 必要、長さ: 4 | BYOD デバイス |


[上記の表のテンプレートをダウンロード](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0)して、構成ポリシーのニーズを確認することができます。

### <a name="profiles"></a>Profiles

プロファイルを使用して、エンド ユーザーが会社データに接続するのを補助します。 Intune は、さまざまな種類のプロファイルをサポートします。 ユース ケースと要件を参照して、どのような場合にプロファイルを構成するかを確認してください。 すべてのデバイス プロファイルは、プラットフォームの種類によって分類され、設計ドキュメントに含まれる必要があります。

-   証明書プロファイル

-   Wi-Fi プロファイル

-   VPN プロファイル

-   電子メールのプロファイル

プロファイルの各種類についてさらに詳しく説明します。

#### <a name="certificate-profiles"></a>証明書プロファイル

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


[上記の表のテンプレートをダウンロード](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0)して、証明書プロファイルのニーズを確認することができます。

#### <a name="wi-fi-profile"></a>Wi-Fi プロファイル

Wi-Fi プロファイルは、モバイル デバイスをワイヤレス ネットワークに自動的に接続するために使われます。 Intune では、サポートされるすべてのプラットフォームに Wi-Fi プロファイルを展開できます。 詳しくは、「[デバイスを構成すると、会社の Wi-Fi ネットワークに接続できます](wi-fi-settings-configure.md)」をご覧ください。

Wi-Fi プロファイルの設計の例を次に示します。

| **種類** | **プロファイル名** | **デバイスのプラットフォーム** | **ユース ケース** |   
|:---:|:---:|:---:|:---:|
| Wi-Fi | アジア Wi-Fi プロファイル | Android | 企業、BYOD アジア地域|                                                           
| Wi-Fi | 北米 Wi-Fi プロファイル | Android、iOS、Windows 10 Mobile | 企業、BYOD 北米地域 |                                                           


[上記の表のテンプレートをダウンロード](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0)して、Wi-Fi プロファイルのニーズを確認することができます。

#### <a name="vpn-profile"></a>VPN プロファイル

VPN プロファイルを使うと、ユーザーはリモートの場所からネットワークに安全にアクセスできます。 Intune は、ネイティブ モバイル VPN 接続およびサード パーティ ベンダーからの VPN プロファイルをサポートします。 詳しくは、「[VPN connections in Microsoft Intune](vpn-settings-configure.md)」 (Microsoft Intune での VPN 接続) をご覧ください。

VPN プロファイルの設計を文書化する例を次に示します。

| **種類** | **プロファイル名** | **デバイスのプラットフォーム** | **ユース ケース** |   
|:---:|:---:|:---:|:---:|
| VPN | VPN Cisco any connect Profile | Android、iOS、Windows 10 Mobile | 企業、BYOD 北米およびドイツ|                                                           
| VPN | Pulse Secure | Android | 企業、BYOD アジア地域 |                                                           


[上記の表のテンプレートをダウンロード](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0)して、VPN プロファイルのニーズを確認することができます。
#### <a name="email-profile"></a>電子メールのプロファイル

電子メール プロファイルを使うと、メール クライアントを接続情報とメール構成で自動的にセットアップできます。 Intune は、一部のデバイスで電子メール プロファイルをサポートします。 [電子メール プロファイルとサポートされるプラットフォーム](email-settings-configure.md)の詳細を参照してください。

電子メール プロファイルの設計を文書化する例を次に示します。

| **種類** | **プロファイル名** | **デバイスのプラットフォーム** | **ユース ケース** |   
|:---:|:---:|:---:|:---:|
| 電子メールのプロファイル | iOS email profile | iOS | 企業 – 情報ワーカー BYOD |                                                           
| 電子メールのプロファイル | Android Knox email profile | Android Knox | BYOD |


[上記の表のテンプレートをダウンロード](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0)して、電子メール プロファイルのニーズを確認することができます。
### <a name="apps"></a>アプリ

Intune では、複数の方法でユーザーまたはデバイスにアプリを提供できます。 アプリの種類は、ソフトウェア インストーラー アプリ、パブリック アプリ ストアからのアプリ、外部リンク、管理対象 iOS アプリなどです。 個々のアプリの展開だけでなく、iOS および Windows のボリューム購入プログラムを利用して、ボリューム購入アプリを管理および展開することもできます。 詳細については、下記のリンクをクリックしてください。

-   [提供できるアプリの種類](app-management.md)

-   [ビジネス向け iOS Volume Purchase Program (VPP)](vpp-apps-ios.md)

-   [ビジネス向け Windows ストアのアプリ](windows-store-for-business.md)

#### <a name="app-type-requirements"></a>アプリの種類の要件

アプリはユーザーとデバイスに展開できるので、どのアプリケーションを Intune で管理するか決めることをお勧めします。 リストを収集するときは、次の点を確認します。

-   アプリは、クラウド サービスとの統合を必要としますか。

-   すべてのアプリを BYOD 利用可能にしますか。

-   これらのアプリに使用できる展開オプションにはどのようなものがありますか。

-   会社では、パートナーの SaaS (サービスとしてのソフトウェア) アプリのデータにアクセスできるようにする必要はありますか。

-   アプリにはユーザーのデバイスからインターネットでアクセスする必要がありますか。

-   アプリは、アプリ ストアで一般に利用可能なものですか、またはカスタム基幹業務 (LOB) アプリですか。


#### <a name="app-protection-policies"></a>アプリ保護ポリシー

アプリ保護ポリシーは、アプリケーションが企業データを管理する方法を定義することによって、データの損失を最小限に抑えます。 Intune は、モバイル アプリ管理で機能するように構築された任意のアプリケーションのアプリ保護ポリシーをサポートします。 アプリ保護ポリシーを設計するときは、特定のアプリで会社のデータに設ける制限を決める必要があります。 [アプリ保護ポリシー](app-protection-policy.md)がどのように機能するか確認することをお勧めします。 既存のアプリケーションおよび必要な保護を文書化する方法の例を以下に示します。

| **アプリケーション** | **目的** | **プラットフォーム** | **ユース ケース** | **アプリ保護ポリシー** |
|:---:|:---:|:---:|:---:|:---:|
| Outlook Mobile  | 利用可能 | iOS | 企業 - エグゼクティブ | 脱獄不可、ファイルを暗号化 |                                                         
| Word | 利用可能 | iOS、Android - Samsung Knox、非 Knox、Windows 10 Mobile | 企業、BYOD | 脱獄不可、ファイルを暗号化 |                                                         


[上記の表のテンプレートをダウンロード](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0)して、アプリ保護ポリシーのニーズを確認することができます。
#### <a name="compliance-policies"></a>Compliance ポリシー

コンプライアンス ポリシーは、デバイスが特定の要件に準拠しているかどうかを決定します。 Intune では、コンプライアンス ポリシーを使って、デバイスが準拠または非準拠のどちらと見なされるかを判断します。 準拠状態は、企業リソースへのアクセスを制限または許可するために使用できます。 条件付きアクセスが必要な場合は、[デバイス コンプライアンス ポリシー](device-compliance.md)を設計することをお勧めします。

要件とユース ケースを参照し、必要なデバイス コンプライアンス ポリシーの数、および対象となるユーザー グループを決定します。 さらに、非準拠と見なされる前に、デバイスがチェックインせずにオフラインでいられる時間を決める必要があります。

コンプライアンス ポリシーの設計方法の例を次に示します。

| **ポリシー名** | **デバイスのプラットフォーム** | **設定** | **対象グループ** |   
|:---:|:---:|:---:|:---:|
| コンプライアンス ポリシー | iOS、Android - Samsung Knox、非 Knox、Windows 10 Mobile | PIN - 必要、脱獄不可 | 企業、BYOD |


[上記の表のテンプレートをダウンロード](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0)して、コンプライアンス ポリシーのニーズを確認することができます。
#### <a name="conditional-access-policies"></a>条件付きアクセス ポリシー

条件付きアクセスは、準拠デバイスのみに電子メールやその他の企業リソースへのアクセスを許可するために使用します。 Intune は、Enterprise Mobility + Security (EMS) と連携して、企業リソースへのアクセスを制御します。 条件付きアクセスが必要かどうか、および何をセキュリティで保護する必要があるかを、決める必要があります。 条件付きアクセスの詳細については、[ここ](conditional-access.md)をご覧ください。

オンライン アクセスについては、条件付きアクセス ポリシーの対象となるプラットフォームおよびユーザー グループを決めます。 また、Exchange Online またはオンプレミスの Exchange 用の Intune サービス間コネクタをインストールして構成する必要があるかどうかを判断します。 Intune サービス間コネクタをインストールして構成する方法の詳細については、以下をご覧ください。<!---these links are correct--->

-   [Exchange Online](/intune-classic/deploy-use/intune-service-to-service-exchange-connector)

-   [Exchange On-premises](exchange-connector-install.md)

条件付きアクセス ポリシーを文書化する方法の例を次に示します。

| **サービス** | **先進認証用プラットフォーム** | **基本認証** | **ユース ケース** |   
|:---:|:---:|:---:|:---:|
| Exchange Online | iOS、Android | Intune がサポートするプラットフォームの非準拠デバイスをブロックする | 企業、BYOD |
| SharePoint Online | iOS、Android |  | 企業、BYOD |

[上記の表のテンプレートをダウンロード](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0)して、条件付きアクセス ポリシーのニーズを確認することができます。

## <a name="next-steps"></a>次のステップ

次のセクションでは、[Intune の実装プロセス](planning-guide-onboarding.md)に関するガイダンスについて説明します。
