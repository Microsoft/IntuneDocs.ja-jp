---
title: 開発中 - Microsoft Intune
titleSuffix: ''
description: Microsoft Intune の開発中の機能
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4bd5392abba3ea22127cb9bcbbb53ec4929f2d5e
ms.sourcegitcommit: 1494ff4b33c13a87f20e0f3315da79a3567db96e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/20/2019
ms.locfileid: "71166324"
---
# <a name="in-development-for-microsoft-intune---september-2019"></a>Microsoft Intune の開発中の機能 - 2019 年 9 月

お客様による準備と計画を支援するため、このページには Intune の UI の更新と、開発中でまだリリースされていない機能がリストされています。 さらに

- お客様による変更前の対処が必要であると予測される場合は、補足の Office メッセージ センター投稿を公開します。
- 機能が運用環境でプレビューまたは一般公開としてリリースされると、機能の説明はこのページから[新機能ページ](whats-new.md)に移されます。
- このページと[新機能ページ](whats-new.md)は定期的に更新されます。 適宜確認してください。
- 戦略的成果物とタイムラインについては、[Microsoft 365 のロードマップ](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS)を参照してください。

> [!Note]
> これらの項目には、将来のリリースで導入される Intune の機能に関する Microsoft の現在の予測が反映されています。 日付と個々の機能は変更されることがあります。 すべての開発中の項目について、このページに機能の説明があるわけではりません。

**RSS フィード**: ご自身のフィード リーダーに次の URL をコピーして貼り付けることで、このページの更新時に通知を受け取ることができます。`https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->

<!-- Common categories:  
#### App management
#### Device configuration
#### Device enrollment
#### Device management
#### Intune apps
#### Monitor and troubleshoot
#### Role-based access control
#### Security

-->
 
<!-- ***********************************************-->
## <a name="app-management"></a>アプリ管理

### <a name="managed-google-play-private-lob-apps----1464182----"></a>管理された Google Play プライベート LOB アプリ <!-- 1464182  -->
Intune を使用すると、IT 管理者は Intune コンソールに埋め込まれている iframe を使用して、管理対象 Google Play にプライベート Android LOB アプリを発行できます。  現時点では、IT 管理者は、Google の Play 発行コンソールに LOB アプリを直接発行する必要があります。これには多くの手順が必要であり、非常に時間がかかります。  この新機能により、最小限の手順で LOB アプリを簡単に発行できるようになります。 Intune コンソールを離れる必要はありません。  管理された Google Play を使用する Android エンタープライズ管理のシナリオでは、この機能 (仕事用プロファイル、専用、完全に管理されたデバイス、および登録されていないデバイス) を利用できます。  Intune から、**[クライアント アプリ]** > **[アプリ]** > **[追加]** の順に選択します。 次に、 **[アプリの種類]** ボックスの一覧から 管理された **[Google Play]** を選択します。 管理された Google Play アプリの詳細については、「 [Intune を使用して Android Enterprise デバイスに管理対象 Google Play アプリを追加する](apps-add-android-for-work.md)」を参照してください。

### <a name="company-portal-app-installation-status-messages----2514416----"></a>ポータルサイトアプリのインストールステータスメッセージ <!-- 2514416  -->
ポータルサイトアプリには、エンドユーザーに追加のアプリインストールステータスメッセージが表示されます。 新しい Win32 依存関係機能には、次の条件が適用されます。
- アプリをインストールできませんでした。 管理者によって定義された依存関係が満たされませんでした。
- アプリは正常にインストールされましたが、再起動が必要です。
- アプリはインストールの処理中ですが、続行するには再起動が必要です。

### <a name="managed-google-play-iframe-support----2871756----"></a>マネージ Google Play iframe のサポート <!-- 2871756  -->
Intune では、管理された Google Play iframe を使用して、Intune コンソールで直接 web リンクを追加および管理できるようになります。  これにより、IT 管理者は URL とアイコングラフィックを送信し、通常の Android アプリと同じようにデバイスにそれらのリンクを展開できます。 管理された Google Play を使用する Android エンタープライズ管理のシナリオでは、この機能 (仕事用プロファイル、専用、完全に管理されたデバイス、および登録されていないデバイス) を利用できます。  Intune から、**[クライアント アプリ]** > **[アプリ]** > **[追加]** の順に選択します。 次に、 **[アプリの種類]** ボックスの一覧から 管理された **[Google Play]** を選択します。 管理された Google Play アプリの詳細については、「 [Intune を使用して Android Enterprise デバイスに管理対象 Google Play アプリを追加する](apps-add-android-for-work.md)」を参照してください。

### <a name="macos-support-for-vpp-apps----3173501----"></a>VPP アプリの macOS によるサポート <!-- 3173501  -->
Apple Business Manager を使用して購入した macOS アプリは、Intune 内で Apple VPP トークンが同期されるとコンソールに表示されます。 コンソールを使用して、グループに対するデバイスおよびユーザーベースのライセンスの割り当て、取り消し、再割り当てを行うことができます。 Microsoft Intune は、ご自身の会社で使用するために購入した VPP アプリを管理するのに役立ちます。
- アプリ ストアからライセンス情報を報告する。
- 使用しているライセンスの数を追跡記録する。
- 自分が所有している以上のアプリのコピーをインストールしないようにする。
Intune と VPP の詳細については、「[Microsoft Intune によるボリューム購入アプリとブックの管理](vpp-apps.md)」を参照してください。

### <a name="macos-support-for-web-apps----3174427----"></a>Web アプリの macOS によるサポート <!-- 3174427  -->
macOS ポータル サイトを使用して、Dock に Web アプリをインストールできます。これにより Web 上の URL へのショートカットを追加できます。 エンドユーザーは、macOS ポータル サイト内の Web アプリ用のアプリの詳細ページから **[インストール]** アクションにアクセスできます。 **Web リンク**アプリの種類の詳細については、「[アプリを Microsoft Intune に追加する](apps-add.md)」を参照してください。

#### <a name="assign-microsoft-edge-beta-for-macos----4678761----"></a>MacOS 用 Microsoft Edge beta の割り当て <!-- 4678761  -->
最新バージョンの Microsoft Edge ベータ版を macOS デバイス用の Intune に追加して割り当てることができます。 Intune から [**クライアントアプリ** > ] [**アプリ** > ] [**Microsoft Edge-macOS**の**追加** > ] を選択します。 次に、Microsoft Edge beta を目的のグループに割り当てます。 Microsoft AutoUpdate (MAU) は Microsoft Edge を最新の状態に保ちます。 Microsoft Edge の詳細については、「 [Microsoft Intune で Microsoft edge を使用して web アクセスを管理する](manage-microsoft-edge.md)」を参照してください。

### <a name="read-and-write-graph-api-operations-for-intune-apps----5031704----"></a>Intune アプリの Graph API 操作の読み取りと書き込み <!-- 5031704  -->
アプリケーションは、ユーザー資格情報のないアプリ id を使用して、読み取りと書き込みの両方の操作で Intune Graph API を呼び出すことができます。 Microsoft Graph API for Intune にアクセスする方法については、「[Microsoft Graph での Intune の操作](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0)」を参照してください。

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>組織アカウントのアプリ通知コンテンツを構成する <!-- 2576686 -->
Android および iOS デバイスの Intune アプリ保護ポリシー (アプリ) では、組織アカウントのアプリ通知コンテンツを制御できます。 この機能は、アプリケーションからのサポートを必要とし、すべてのアプリ対応アプリケーションで使用できるとは限りません。 アプリの詳細については、「[アプリ保護ポリシーとは](app-protection-policy.md)」を参照してください。

### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956----"></a>Android の仕事用プロファイルに使用できる Google Play アプリのレポート <!-- 3041956  -->
Android の仕事用プロファイル デバイスに使用できるアプリのインストールについては、アプリのインストール状態と managed Google Play アプリのインストール済みバージョンを確認できます。 詳細については、[アプリの保護ポリシーを監視する方法](app-protection-policies-monitor.md)、[Intune を使用した Android の仕事用プロファイル デバイスの管理](android-enterprise-overview.md)、および[マネージド Google Play アプリの種類](apps-add-android-for-work.md#managed-google-play-app-types)に関する記事を参照してください。

<!-- ***********************************************-->
## <a name="device-configuration"></a>デバイス構成

### <a name="device-features-device-restrictions-and-extension-profiles-for-ios-and-macos-settings-are-shown-by-enrollment-type----4886161----"></a>IOS と macOS の設定のデバイス機能、デバイス制限、および拡張機能プロファイルは、登録の種類別に表示されます。 <!-- 4886161  -->

Intune では、ios デバイスと macos デバイス用のプロファイルを作成します (**デバイス構成** > **プロファイル** > では、プラットフォーム > デバイスの機能に対して、**プロファイル** > **iOS**または**macos****を作成します**) 、**デバイスの制限**、またはプロファイルの種類の**拡張機能**) を使用します。 現時点では、これらのプロファイルで使用可能な設定が一覧表示されています。 

今後の更新プログラムでは、Intune ポータルで利用可能な設定は、適用先の登録の種類によって分類されます。

- iOS
  - すべての登録の種類
  - デバイスの登録とデバイスの自動登録
  - 自動デバイス登録

- macOS
  - すべての登録の種類
  - デバイスの登録
  - ユーザーの承認と自動デバイス登録
  - 自動デバイス登録

適用対象:

- iOS
  - [デバイスの機能](ios-device-features-settings.md)
  - [デバイスの制限](device-restrictions-ios.md)

- macOS
  - [デバイスの機能](macos-device-features-settings.md)
  - [デバイスの制限](device-restrictions-macos.md)
  - [拡張機能](kernel-extensions-settings-macos.md)

### <a name="new-voice-control-settings-for-supervised-ios-devices-running-in-kiosk-mode----4892835----"></a>キオスクモードで実行されている監視対象 iOS デバイスの新しい音声制御設定 <!-- 4892835  -->

Intune では、監視対象の ios デバイスをキオスクまたは専用デバイスとして実行するポリシーを作成することができます (**デバイス構成** > **プロファイル** > では、プラットフォーム用の**プロファイル** > **ios**を作成し > **プロファイルの種類** >**キオスク (監視モードのみ)** のデバイスの制限。 

今後の更新では、次のように制御できる新しい設定が追加されます。

- **音声制御**: キオスクモードのときにデバイスの音声制御を有効にします。
- **音声制御の変更**: キオスクモードのときにデバイスの音声制御設定を変更することをユーザーに許可します。

現在の設定を表示するには、[ [IOS キオスク (監視モードのみ)] 設定](device-restrictions-ios.md#kiosk)にアクセスします。

適用対象:

- iOS 13.0 以降

### <a name="use-single-sign-on-for-apps-and-websites-on-your-ios-and-macos-devices----4893175----"></a>IOS および macOS デバイスのアプリと web サイトにシングルサインオンを使用する <!-- 4893175  -->
今後の更新プログラムには、iOS および macos デバイス向けの新しいシングルサインオン設定がいくつかあります (**デバイス構成** > **プロファイル** > では、用に**プロファイル** > **ios**または**macos**を作成します)。プラットフォーム > プロファイルの種類の**デバイス機能**)。

これらの設定を使用して、特に Kerberos 認証を使用するアプリと web サイトのシングルサインオンエクスペリエンスを構成します。 汎用資格情報シングルサインオンアプリ拡張機能と、Apple の組み込み Kerberos 拡張機能のいずれかを選択できます。

構成できる現在のデバイス機能を確認するには、 [iOS デバイスの機能](ios-device-features-settings.md)と[macOS デバイスの機能](macos-device-features-settings.md)に関するページを参照してください。

適用対象:

- iOS 13.0 以降
- macOS 10.15 以降

### <a name="associate-domains-to-apps-on-macos-1015-devices----4898079----"></a>MacOS 10.15 + デバイス上のアプリにドメインを関連付ける <!-- 4898079  -->
MacOS デバイスでは、さまざまな機能を構成し、ポリシーを使用してこれらの機能をデバイスにプッシュできます (**デバイス構成** > **プロファイル** > では、の**プロファイル** > **macOS**を作成します。プラットフォーム > プロファイルの種類の**デバイス機能**)。 今後の更新プログラムでは、ドメインをアプリに関連付けることができます。 この機能は、資格情報をアプリに関連する web サイトと共有するのに役立ち、Apple のシングルサインオン拡張機能、ユニバーサルリンク、パスワードオートコンプリートと共に使用できます。 

構成できる現在の機能を確認するには、「 [Intune の macOS デバイス機能設定](macos-device-features-settings.md)」にアクセスしてください。

適用対象:

- macOS 10.15 以降

### <a name="use-itunes-and-apps-in-the-itunes-app-store-url-when-showing-or-hiding-apps-on-ios-supervised-devices----4928474----"></a>IOS の監視対象デバイスでアプリを表示または非表示にするときに、iTunes アプリストアの URL で "itunes" と "apps" を使用する <!-- 4928474  --> 
Intune では、監視対象の iOS デバイスで**アプリの表示**と非表示を切り替えるポリシーを作成することができます (**デバイス構成** > **プロファイル** > は、プラットフォーム > デバイス用の**プロファイル** > を作成します。 **[プロファイルの種類]** > アプリの表示と非表示を切り替える **(監視モードのみ)** )。 

など、 `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`iTunes APP store の URL を入力できます。 今後の更新プログラムでは、と`apps` `itunes`の両方を URL で使用できるようになります。次に例を示します。

- `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`
- `https://apps.apple.com/us/app/work-folders/id950878067?mt=8`

これらの設定の詳細について[は、「アプリを表示または非表示にする](device-restrictions-ios.md#show-or-hide-apps)」を参照してください。

適用対象:

- iOS

### <a name="support-for-ikev2-vpn-profiles-for-ios----1943438---"></a>iOS 用の IKEv2 VPN プロファイルのサポート <!-- 1943438 -->
IKEv2 プロトコルを使用して、iOS ネイティブ VPN クライアント用の VPN プロファイルを作成できるようになります。 IKEv2 は、**[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** > **プラットフォームに [iOS]** > プラットフォームの種類に **[VPN]** > **[設定]** の新しい接続の種類です。

これらの VPN プロファイルではネイティブ VPN クライアントを構成します。 そのため、VPN クライアント アプリはマネージド デバイスにインストールまたはプッシュされません。 この機能を使用するには、デバイスを Intune に登録する必要があります (MDM 登録)。

現在構成できる VPN 設定については、「[Microsoft Intune で iOS デバイスに対する VPN 設定を構成する](vpn-settings-ios.md)」を参照してください。

適用対象: iOS


<!-- ***********************************************-->
## <a name="device-enrollment"></a>デバイスの登録

### <a name="new-tenants-will-default-away-from-android-device-administrator-management----4869790----"></a>新しいテナントは既定で Android デバイス管理者の管理から離れます <!-- 4869790  -->
Android Enterprise では、android のデバイス管理機能が置き換えられています。 そのため、代わりに新しい登録に Android Enterprise を使用することをお勧めします。 今後の更新では、デバイス管理者の管理を使用するために、新しいテナントは android の登録で次の前提条件の手順を完了する必要があります。 **Intune** > **デバイス登録** > **Android の登録**にアクセスするデバイス管理特権 > **を持つ個人および会社所有のデバイスは、** デバイス管理**者を使用してデバイスを管理**します。  > 

既存のテナントでは、環境が変更されることはありません。 

Intune での Android デバイス管理者の詳細については、「 [android デバイス管理者の登録](android-enroll-device-administrator.md)」を参照してください。

### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal----4394993----"></a>iOS デバイスの場合は、ポータル サイトの登録プロセスのプライバシー画面をカスタマイズします <!-- 4394993  -->
マークダウンを使用して、iOS の登録時にエンド ユーザーに表示されるポータル サイトのプライバシー画面をカスタマイズできます。 具体的には、組織がデバイス上で参照または実行できない項目の一覧をカスタマイズできます。

<!-- ***********************************************-->
## <a name="device-management"></a>デバイス管理

### <a name="deploy-software-updates-to-macos-devices----3194876---"></a>MacOS デバイスへのソフトウェア更新プログラムの展開 <!-- 3194876 -->
MacOS デバイスのグループにソフトウェア更新プログラムを展開できるようになります。 この機能には、重要な、ファームウェア、構成ファイル、およびその他の更新プログラムが含まれます。 次のデバイスのチェックイン時に更新プログラムを送信したり、設定した時間帯に更新プログラムを展開する週単位のスケジュールを選択したりすることができます。 これは、標準の勤務時間外にデバイスを更新する場合や、ヘルプデスクのスタッフが完全に仕事をしている場合に役立ちます。 また、更新プログラムが展開されているすべての macOS デバイスの詳細なレポートも取得します。 デバイスごとにレポートをドリルダウンして、特定の更新の状態を確認することができます。

### <a name="send-custom-notifications-to-a-device----4928910----"></a>カスタム通知をデバイスに送信する <!-- 4928910  -->
ポータルサイトまたは Intune アプリがインストールされている特定のデバイスにカスタム通知を送信することができます。 これを行うには、 **[Intune** > **デバイス** > ] **[すべてのデバイス]** の順に選択し、デバイス >**より詳細** > な**送信カスタム通知**を選択 > ます。 

### <a name="updates-to-android-enterprise-fully-managed-features----3464667-5227935-4062195-4631425-4631440---"></a>Android Enterprise の完全に管理された機能の更新 <!-- 3464667, 5227935, 4062195, 4631425, 4631440 -->

Android の完全に管理されたデバイスについて、次のサポートを追加します。

- 完全に管理された Android 用の SCEP 証明書は、デバイス所有者として管理されているデバイスで、証明書認証に使用できます。 SCEP 証明書は、仕事用プロファイルデバイスで既にサポートされています。  デバイス所有者の SCEP 証明書を使用すると、次のことが可能になります。 <!-- 5227935 -->
    - Android Enterprise の [DO] セクションで SCEP プロファイルを作成する
    - SCEP 証明書を認証のために Wi-fi プロファイルにリンクする
    - 認証に VPN プロファイルを使用するように SCEP 証明書をリンクする
    - SCEP 証明書を認証用の電子メールプロファイルにリンクする (アプリ構成を使用)
- システムアプリは Android エンタープライズデバイスでサポートされます。 Intune では、[**クライアントアプリ** > ] [**アプリ** > ] **[追加]** の順に選択して、Android エンタープライズシステムアプリを追加します。 **[アプリの種類]** ボックスの一覧で、 **[Android エンタープライズシステムアプリ]** を選択します。 Intune にアプリを追加する方法の詳細については、「[Microsoft Intune にアプリを追加する](apps-add.md)」を参照してください。 <!-- 4062195 -->
- [**デバイスコンプライアンス** > ] [**Android Enterprise** > **デバイスの所有者**] で、Google saf etynet 構成証明レベルを設定するコンプライアンスポリシーを作成できます。   <!-- 4631425 -->
- Android Enterprise の完全管理型デバイスでは、モバイル脅威防御プロバイダーがサポートされます。 [**デバイスコンプライアンス** > ] [**Android エンタープライズ** > **デバイス所有者**] で、許容可能な脅威レベルを選択できます。 <!-- 4631440 --> [Intune を使用してデバイスを準拠または非準拠としてマークするための Android エンタープライズ設定](compliance-policy-create-android-for-work.md#device-owner)に関するページに、現在の設定が記載されています。


適用対象: 
- Android エンタープライズのフル マネージド デバイス

<!-- ***********************************************-->
## <a name="monitor-and-troubleshoot"></a>監視とトラブルシューティング

### <a name="updated-support-experience-------5012398------"></a>更新されたサポートエクスペリエンス   <!--  5012398    -->
継続的な改善の一環として、Intune のコンソール内サポートエクスペリエンスを更新します。  一般的な問題についてコンソール内での検索とフィードバックを改善し、ワークフローを合理化してサポートに連絡します。     

<!-- ***********************************************-->
## <a name="security"></a>セキュリティ

### <a name="tamper-protection-for-windows-defender-antivirus-----4705448---------"></a>Windows Defender ウイルス対策の改ざん防止  <!-- 4705448       -->
Windows Defender ウイルス対策のために Intune で管理できる設定に、*改ざん防止機能*を追加します。 Windows 10 endpoint protection のデバイス構成プロファイルを使用して、改ざん防止をオンまたはオフにすることができます。  改ざん防止の詳細については、Windows ドキュメントの「[改ざん防止によるセキュリティ設定の変更の防止](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/prevent-changes-to-security-settings-with-tamper-protection)」を参照してください。 


<!-- ***********************************************-->
## <a name="notices"></a>通知

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

## <a name="see-also"></a>関連項目
最近の開発状況について詳しくは、「[Microsoft Intune の新機能](whats-new.md)」をご覧ください。




