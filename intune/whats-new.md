---
title: Microsoft Intune の新機能 - Azure | Microsoft Docs
titleSuffix: ''
description: Intune Azure Portal の新機能を確認する
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7f2e4870d1a2614ecccc1647db828e214a6aede8
ms.sourcegitcommit: e9911a6bbfb8532a27e70d70402a214a8b2b6c75
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2019
ms.locfileid: "68818796"
---
# <a name="whats-new-in-microsoft-intune"></a>Microsoft Intune の新機能

週ごとにまとめた、Microsoft Intune の新機能をご覧ください。 また、[重要なお知らせ](#notices)、[過去のリリース](whats-new-archive.md)、および [Intune サービスの更新プログラムのリリース方法](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728)に関する情報もあります。 

> [!Note]
> 個々の[マンスリー更新プログラム](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728)は、展開に最大 3 日かかることがあります。順序は次のとおりです。
> - 1 日目:アジア太平洋 (APAC)
> - 2 日目:ヨーロッパ、中東、アフリカ (EMEA)
> - 3 日目:北米
> 
> いくつかの機能については、数週間にわたってロールアウトされ、一部のお客様は最初の週にご利用になれない可能性があります。
>
> リリースの今後の機能の一覧については、[開発中のページ](in-development.md)を参照してください。

**RSS フィード**:ご自身のフィード リーダーに次の URL をコピーして貼り付けることで、このページの更新時に通知を受け取ることができます。`https://docs.microsoft.com/api/search/rss?search=%22What%27s+new+in+microsoft+intune%3F+-+Azure%22&locale=en-us`

<!-- Common categories:  
### App management
### Device configuration
### Device enrollment
### Device management
### Device security
### Intune apps
### Monitor and troubleshoot
### Role-based access control

-->  

<!-- ########################## -->

## <a name="week-of-july-22-2019"></a>2019 年 7 月 22 日の週 

### <a name="app-management"></a>アプリ管理

#### <a name="customized-notifications-for-users-and-groups-------16766574------------"></a>ユーザーとグループ向けにカスタマイズされた通知    <!-- 16766574          -->
Intune で管理している iOS デバイスと Android デバイスで、ポータル サイト アプリケーションからユーザーに宛て、カスタムのプッシュ通知を送信します。 このようなモバイル プッシュ通知は自由形式のテキストで高度なカスタマイズが可能であり、あらゆる目的に使用できます。 組織のさまざまなユーザー グループに通知の対象を設定できます。 詳細は、「[カスタム通知](custom-notifications.md)」を参照してください。

#### <a name="googles-device-policy-controller-app----3041950----"></a>Google のデバイス ポリシー コントローラー アプリ <!-- 3041950  -->
マネージド ホーム スクリーン アプリで、Google の Android デバイス ポリシー アプリにアクセスできるようになりました。 マネージド ホーム スクリーン アプリは、マルチアプリ キオスク モードを使用する Android Enterprise (AE) 専用デバイスとして Intune に登録されているデバイスで使用されるカスタム ランチャーです。 Android デバイス ポリシー アプリにアクセスしたり、ユーザーを Android デバイス ポリシー アプリに案内したりして、サポートとデバッグを行うことができます。 この起動機能は、デバイスが登録され、マネージド ホーム スクリーンにロックされているときに使用できます。 この機能を使用するために追加のインストールは必要ありません。

#### <a name="outlook-protection-settings-for-ios-and-android-devices----3212619---"></a>iOS デバイスと Android デバイスの Outlook 保護設定 <!-- 3212619 -->
デバイスを登録しなくても、シンプルな Intune 管理者コントロールを利用し、iOS と Android を対象に Outlook の一般アプリ設定とデータ保護設定の両方を構成できるようになりました。 一般的なアプリ構成設定からは、登録したデバイスで iOS 向け Outlook か Android 向け Outlook を管理するときに管理者が有効にできるものと同じような設定が与えられます。 Outlook 設定の詳細は、[iOS と Android 用 Outlook のアプリ構成設定の展開](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune)に関する記事をご覧ください。

### <a name="device-configuration"></a>デバイス構成

#### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910-eeready---idstaged---"></a>Windows 10 デバイス構成プロファイルを作成するときは "適用規則" を使用する <!-- 2549910 eeready   idstaged -->

Windows 10 デバイス構成プロファイルを作成します ( **[デバイスの構成]** 、 **[プロファイル]** 、 **[プロファイルの作成]** の順に選択し、プラットフォームに **[Windows 10]** を選択し、 **[適用規則]** を選択します)。 今回の更新で、**適用規則**を作成し、プロファイルが特定のエディションまたは特定のバージョンにのみ適用されるようにすることができます。 たとえば、いくつかの BitLocker 設定を有効にするプロファイルを作成します。 プロファイルを追加したら、適用規則を使用して Windows 10 Enterprise を実行しているデバイスにのみプロファイルを適用します。

適用規則を追加するには、「[適用規則](device-profile-create.md#applicability-rules)」を参照してください。

適用対象:Windows 10 以降

#### <a name="use-tokens-to-add-device-specific-information-in-custom-profiles-for-ios-and-macos-devices----3330008----"></a>トークンを利用し、iOS デバイスと macOS デバイス向けのカスタム プロファイルでデバイス固有の情報を追加します <!-- 3330008  -->
iOS デバイスと macOS デバイスでカスタム プロファイルを利用し、Intune には組み込まれていない設定や機能を構成できます ( **[デバイス構成]** 、 **[プロファイル]** 、 **[プロファイルの作成]** の順に選択し、プラットフォームに **[iOS]** または **[macOS]** を選択し、プロファイルの種類に **[カスタム]** を選択します)。 今回の更新では、トークンを `.mobileconfig` ファイルに追加し、デバイス固有の情報を追加できます。 たとえば、デバイスのシリアル番号を表示する目的で構成ファイルに `Serial Number: {{serialnumber}}` を追加できます。

カスタム プロファイルを作成するには、「[iOS カスタム設定](custom-settings-ios.md)」または「[macOS カスタム設定](custom-settings-macos.md)」を参照してください。

適用対象:
- iOS
- macOS

#### <a name="new-configuration-designer-when-creating-an-oemconfig-profile-for-android-enterprise----3712769-----"></a>Android Enterprise 向けに OEMConfig プロファイルを作成するときの新しい構成デザイナー <!-- 3712769   -->
Intune では、OEMConfig アプリを使用するデバイス構成プロファイルを作成できます ([デバイス構成]、[プロファイル]、[プロファイルの作成] の順に選択し、プラットフォームに [Android Enterprise] を選択し、プロファイルの種類に [OEMConfig] を選択します)。 これを行うと、JSON エディターが開き、テンプレートと値を変更できます。 

今回の更新には、使い勝手が改善された構成デザイナーが含まれています。タイトルや説明など、アプリに組み込まれた詳細が表示されます。 JSON エディターも引き続き使用できます。構成デザイナーで行ったすべての変更が表示されます。

現在の設定を確認するには、「[OEMConfig で Android Enterprise デバイスを使用し、管理する](android-oem-configuration-overview.md)」を参照してください。

適用対象:Android エンタープライズ

#### <a name="updated-ui-for-configuring-windows-hello-----4089576--------------"></a>Windows Hello を構成する目的で更新された UI  <!-- 4089576            -->
[Windows Hello for Business を使用するように Intune を構成する](windows-hello.md)コンソールを更新しました。 構成設定はすべて、Windows Hello のサポートを有効にしたコンソールの同じウィンドウで利用できるようになりました。 


#### <a name="intune-powershell-sdk----4924113---"></a>Intune PowerShell SDK <!-- 4924113 --> 
Microsoft Graph 経由で Intune API のサポートを提供する Intune PowerShell SDK がバージョン 6.1907.1.0 に更新されました。 SDK で以下がサポートされるようになりました。
- Azure Automation と連動します。
- アプリ専用の認証読み取り操作をサポートします。 
- わかりやすく省略した名前を別名としてサポートします。
- PowerShell の名前付け規則に準拠します。 具体的には、`PSCredential` パラメーター (`Connect-MSGraph` コマンドレット) の名前が `Credential` に変更されました。
- `Invoke-MSGraphRequest` コマンドレットの使用時、`Content-Type` ヘッダーの値を手動で指定できるようになりました。

詳細は、「[PowerShell SDK for Microsoft Intune Graph API](https://www.powershellgallery.com/packages/Microsoft.Graph.Intune)」を参照してください。


### <a name="device-enrollment"></a>デバイスの登録

#### <a name="updates-for-enrollment-restrictions-----2871968---"></a>登録制限の更新  <!-- 2871968 -->
Android Enterprise の仕事用プロファイルが既定で許可されるように、新しいテナントの登録制限が更新されました。 既存のテナントは変更の萍郷を受けません。 Android Enterprise の仕事用プロファイルを使用するには、[Managed Google Play アカウントに Intune アカウントを接続する](https://docs.microsoft.com/intune/connect-intune-android-enterprise)必要があります。

#### <a name="ui-updates-for-apple-enrollment-and-enrollment-restrictions---4089575-4089579----"></a>Apple 登録と登録制限の UI 更新 <!--4089575, 4089579  -->
次の両方のプロセスでウィザードスタイルのユーザー インターフェイスが使用されます。
- Apple デバイス登録。 詳細は、「[Apple の Device Enrollment Program を使用して iOS デバイスを自動登録する](device-enrollment-program-enroll-ios.md)」を参照してください。
- 登録制限の作成。 詳細は、「[登録制限を設定する](enrollment-restrictions-set.md)」を参照してください。

#### <a name="handling-pre-configuration-of-corporate-device-identifiers-for-android-q-devices----4711509--idmiss---"></a>Android Q デバイスの会社デバイス ID の事前構成を処理する <!-- 4711509  idmiss -->
Google は Android Q (v10) で、レガシ マネージド (デバイス管理者) Android デバイスの MDM エージェントでデバイス ID 情報を収集する機能を削除しました。  Intune には、デバイスに会社所有のタグを自動的に付ける目的で、IT 管理者が[デバイス シリアル番号または IMEI の一覧を事前構成](https://docs.microsoft.com/intune/corporate-identifiers-add#identify-corporate-owned-devices-with-imei-or-serial-number)できる機能が与えられています。 この機能は、デバイス管理者によって管理される Android Q デバイスでは作動しません。  デバイスのシリアル番号または IMEI に関係なく、Intune 登録中、デバイスは常に個人所有として見なされます。  登録後、会社に所有権を手動で切り替えることができます。  これは新しい登録のみに関係します。登録済みのデバイスは影響を受けません。  仕事用プロファイルで管理される Android デバイスはこの変更の影響を受けません。今後も今までどおり動作します。  また、デバイス管理者として登録されている Android Q デバイスでは、Intune コンソールでシリアル番号または IMEI をデバイス プロパティとして報告できなくなります。

#### <a name="icons-have-changed-for-android-enterprise-enrollments-work-profile-dedicated-devices-and-fully-managed-devices----4977730---"></a>Android Enterprise 登録のアイコンが変更されました (仕事用プロファイル、専用デバイス、完全に管理されるデバイス)。 <!-- 4977730 -->
Android Enterprise 登録プロファイルのアイコンが変更されました。 新しいアイコンを見るには、 **[Intune]** 、 **[登録]** 、 **[Android 登録]** の順に進み、 **[登録プロファイル]** の下を探してください。


#### <a name="windows-diagnostic-data-collection-change----4113859---"></a>Windows 診断データ収集の変更 <!-- 4113859 -->
Windows 10 バージョン 1903 以降を実行するデバイスに関して、診断データ収集の既定値が変更されました。 Windows 10 1903 より、診断データ収集は既定で有効になります。 Windows 診断データは、Windows デバイスから取得される、デバイスと、Windows と関連ソフトウェアの性能に関する極めて重要な技術データです。 詳しくは、「[組織内の Windows 診断データの構成](https://docs.microsoft.com/windows/privacy/configure-windows-diagnostic-data-in-your-organization)」をご覧ください。 AutoPilot デバイスでも、[System/AllowTelemetry](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-allowtelemetry) で AutoPilot プロファイルに完全以外が設定されていない限り、"完全な" テレメトリが選択されます。

### <a name="device-management"></a>デバイス管理

#### <a name="improve-device-location---3855417----"></a>デバイスの位置検索機能の向上<!-- 3855417  -->
**[デバイスを検索する]** アクションを使用し、デバイスの正確な座標にズームインできます。 紛失した iOS デバイスの位置を見つける方法については、[紛失した iOS デバイスの見つける方法](device-locate.md)に関するページを参照してください。


### <a name="device-security"></a>デバイス セキュリティ

#### <a name="advanced-settings-for-windows-defender-firewall--public-preview-------1311949-------"></a>Windows Defender ファイアウォールの詳細設定 (パブリック プレビュー)  <!--  1311949     -->  
Windows 10 のエンドポイント保護として[デバイス構成プロファイルの一部としてカスタム ファイアウォール規則](endpoint-protection-configure.md#add-custom-firewall-rules-for-windows-10-devices)を管理するには、Intune を使用します。 規則では、アプリケーション、ネットワーク、アドレス、ポートに対する受信と送信の動作を指定できます。 

#### <a name="updated-ui-for-managing-security-baselines------4091125-------"></a>セキュリティ ベースラインを管理するための UI が更新されました   <!-- 4091125     -->
Intune コンソールでセキュリティ ベースラインを[作成し、編集するエクスペリエンス](security-baselines.md#create-the-profile) を更新しました。 変更内容:

ウィザードスタイルの形式がシングル ブレードに圧縮され、わかりやすくなりました。 1 つのブレードに収まるようになりました。 ブレードがスプロールしていると IT の専門家は複数の個別ウィンドウにドリルダウンしなければなりませんが、この新しい設計ではそれがなくなりました。  
作成または編集の間に割り当てを作成できるようになりました。後で割り当てベースラインに戻る必要がありません。 設定のまとめを追加しました。新しいベースラインを作成する前に、あるいは既存のベースラインを編集するときに表示できます。 編集時、編集中のプロパティの 1 カテゴリ内に設定されているアイテムのみがまとめに一覧表示されます。



<!-- ########################## -->

## <a name="week-of-july-15-2019"></a>2019 年 7 月 15 日の週 

### <a name="app-management"></a>アプリ管理

#### <a name="managed-home-screen-and-managed-settings-icons----4918107---"></a>マネージド ホーム スクリーンとマネージド設定のアイコン <!-- 4918107 -->
[マネージド ホーム スクリーン] アプリ アイコンと **[マネージド設定]** のアイコンが更新されました。 [マネージド ホーム スクリーン] アプリは、Android Enterprise (AE) 専用デバイスとして Intune に登録され、マルチアプリ キオスク モードで実行されるデバイスでのみ使用されます。 [マネージド ホーム スクリーン] アプリの詳細は、「[Android Enterprise 用 Microsoft Managed Home Screen アプリを構成する](app-configuration-managed-home-screen-app.md)」を参照してください。

#### <a name="android-device-policy-on-android-enterprise-dedicated-devices----4918136---"></a>Android Enterprise 専用デバイスの Android デバイス ポリシー <!-- 4918136 -->
[マネージド ホーム スクリーン] アプリのデバッグ画面から Android デバイス ポリシー アプリケーションにアクセスできます。 [マネージド ホーム スクリーン] アプリは、Android Enterprise (AE) 専用デバイスとして Intune に登録され、マルチアプリ キオスク モードで実行されるデバイスでのみ使用されます。 詳細は、「[Android Enterprise 用 Microsoft Managed Home Screen アプリを構成する](app-configuration-managed-home-screen-app.md)」を参照してください。

#### <a name="ios-company-portal-updates----3902931---"></a>iOS ポータル サイトの更新 <!-- 3902931 -->
iOS アプリ管理プロンプトの会社名が現在の "i.manage.microsoft.com" テキストに取って代わります。 たとえば、ユーザーがポータル サイトから iOS アプリをインストールしようとすると、あるいはユーザーがアプリの管理を許可すると、"i.manage.microsoft.com" ではなく、会社名がユーザーに表示されます。 これは、今後数日間にわたってすべてのお客様にロールアウトされます。

### <a name="device-configuration"></a>デバイス構成

#### <a name="manage-filevault-for-macos-------3858502--4557986--1210104----"></a>macOS 向け FileVault の管理   <!--  3858502 + 4557986 + 1210104  -->
Intune を使用し、[macOS デバイスの FileVault キー暗号化を管理](encrypt-devices.md)できます。 デバイスを暗号化するには、エンドポイント保護デバイス構成プロファイルを使用します。

FileVault のサポートには、暗号化されていないデバイスの暗号化、デバイスの個人用回復キーのエスクロー、個人用暗号化キーの自動または手動ローテーション、会社デバイスのキー取得が含まれます。 エンド ユーザーはポータル サイト Web サイトを使用し、暗号化している自分のデバイスの個人用回復キーを取得することもできます。 

また、デバイス暗号化に関するすべての詳細を 1 か所で表示できるように、BitLocker に関する情報に加えて、[FileVault に関する情報](encryption-monitor.md)が含まれるよう、暗号化レポートを拡張しました。 

### <a name="device-enrollment"></a>デバイスの登録

#### <a name="windows-autopilot-reset-removes-the-devices-primary-user----4156123---"></a>Windows AutoPilot リセットを実行すると、デバイスのプライマリ ユーザーが削除されます。 <!-- 4156123 -->
AutoPilot リセットがデバイスで使用されると、デバイスのプライマリ ユーザーが削除されます。 リセット後に初めてサインインしたユーザーがプライマリ ユーザーとして設定されます。 この機能は、今後数日間にわたってすべてのお客様にロールアウトされます。

## <a name="week-of-july-8-2019"></a>2019 年 7 月 8 日の週

### <a name="new-office-windows-and-onedrive-settings-in-windows-10-administrative-templates----3510695---"></a>Windows 10 管理用テンプレートの新しい Office、Windows、OneDrive の設定 <!-- 3510695 -->

オンプレミス グループ ポリシー管理を模倣する管理用テンプレートを Intune で作成できます ( **[デバイス管理]** 、 **[プロファイル]** 、 **[プロファイルの作成]** の順に選択し、プラットフォームに **[Windows 10 以降]** を選択し、プロファイルの種類に **[管理用テンプレート]** を選択します)。

この更新には、テンプレートに追加できる Office 設定、Windows 設定、OneDrive 設定が含まれています。 このような新しい設定を利用することで、100% クラウドベースの 2500 を超える設定を構成できるようになりました。

この機能の詳細については、[Windows 10 テンプレートを使用し、Intune でグループ ポリシー設定を構成する方法](administrative-templates-windows.md)に関するページを参照してください。

適用対象:Windows 10 以降

## <a name="week-of-july-1-2019"></a>2019 年 7 月 1 日の週 

### <a name="app-management"></a>アプリ管理

#### <a name="aad-and-app-on-android-enterprise-devices----3574267---"></a>Android Enterprise デバイスの AAD と APP <!-- 3574267 -->
完全管理の Android Enterprise デバイスをオンボードするとき、ユーザーは新しい (工場出荷時の状態の) デバイスの初回セットアップ中、Azure Active Directory (AAD) に登録するようになりました。 以前は、フル マネージド デバイスの場合、セットアップの完了後、ユーザーは手動で Microsoft Intune アプリを起動し、AAD 登録を開始する必要がありました。 今後は、初回セットアップ後、ユーザーがデバイスのホーム ページを開くと、デバイスの登録も完了しています。

AAD 更新プログラムに加え、Intune アプリ保護ポリシー (APP) が完全管理 Android Enterprise デバイスでサポートされるようになりました。 ロールアウト次第、この機能は利用できるようになります。詳細は、「[Intune で managed Google Play アプリを Android エンタープライズ デバイスに追加する](apps-add-android-for-work.md)」を参照してください。

## <a name="week-of-june-24-2019"></a>2019 年 6 月 24 日の週 

### <a name="app-management"></a>アプリ管理

#### <a name="configure-which-browser-is-allowed-to-link-to-organization-data----3145939---"></a>組織データへのリンクを許可するブラウザーを構成する <!-- 3145939 -->
Android と iOS デバイスで Intune App Protection ポリシー (APP) を使用すると、組織の Web リンクを Intune Managed Browser または Microsoft Edge 以外の特定のブラウザーに転送できるようになりました。  アプリの詳細については、「[アプリ保護ポリシーとは](app-protection-policy.md)」を参照してください。

#### <a name="all-apps-page-identifies-onlineoffline-microsoft-store-for-business-apps--4089647---"></a>[すべてのアプリ] ページでは、オンライン/オフラインの Microsoft Store for Business アプリが識別されます。<!--4089647 -->
**[すべてのアプリ]** ページには、Microsoft Store for Business (MSFB) アプリをオンラインまたはオフライン アプリとして識別するためのラベル付けが含まれるようになりました。 各 MSFB アプリには、 **[オンライン]** か **[オフライン]** の接尾辞が含まれるようになりました。 [アプリの詳細] ページには、**ライセンスの種類**と**デバイス コンテキスト インストールのサポート** (オフラインの認可アプリのみ) に関する情報も含まれています。

#### <a name="company-portal-app-on-windows-shared-devices---4393553---"></a>Windows 共有デバイスのポータル サイト アプリ <!--4393553 -->
ユーザーは Windows 共有デバイスでポータル サイト アプリにアクセスできるようになりました。 エンドユーザーには、デバイス タイルで**共有**ラベルが表示されます。 これは、Windows ポータルサイト アプリ バージョン 10.3.45609.0 以降に適用されます。

#### <a name="view-all-installed-apps-from-new-company-portal-web-page----4224326---"></a>新しいポータル サイト Web ページにインストールされたすべてのアプリが表示 <!-- 4224326 -->
ポータル サイト Web サイトの新しい **[インストール済みアプリ]** ページに、ユーザーのデバイスにインストールされているすべてのマネージド アプリ (必須および使用可能の両方) が一覧表示されます。 割り当ての種類だけでなく、アプリの発行元、発行日、現在のインストール状態も表示されます。 ユーザーに対して必須または使用可能とされているアプリがない場合は、会社アプリがインストールされていないというメッセージが表示されます。 Web 上で新しいページを参照するには、[ポータル サイト Web サイト](https://portal.manage.microsoft.com)に移動して、 **[インストール済みアプリ]** をクリックします。  

#### <a name="new-view-lets-app-users-see-all-managed-apps-installed-on-device----2352913---"></a>新しいビューでデバイスにインストールされているすべてのマネージド アプリが表示可能に <!-- 2352913 -->  
Windows 用ポータル サイトのアプリに、ユーザーのデバイスにインストールされているすべてのマネージド アプリ (必須および使用可能の両方) が一覧表示されるようになりました。 ユーザーは、試行した、および保留中のアプリのインストールと、それらの現在の状態も確認できます。 ユーザーに対して必須または使用可能とされているアプリがない場合は、アプリがインストールされていないというメッセージが表示されます。 新しいビューを表示するには、ポータル サイトのナビゲーション ウィンドウに移動し、 **[アプリ]**  >  **[インストール済みアプリ]** の順に選択します。    

### <a name="device-configuration"></a>デバイス構成

#### <a name="configure-settings-for-kernel-extensions-on-macos-devices----2043024---"></a>macOS デバイスのカーネル拡張機能の設定を構成する <!-- 2043024 -->
macOS デバイスで、デバイス構成プロファイルを作成できます ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]** > プラットフォームに **[macOS]** を選択します)。 この更新プログラムには、デバイスのカーネル拡張機能を構成して使用することができる新しい設定のグループが含まれます。 特定の拡張機能を追加したり、特定のパートナーまたは開発者からの拡張機能をすべて許可したりすることができます。

この機能の詳細については、[カーネル拡張機能の概要](kernel-extensions-overview-macos.md)と[カーネル拡張機能の設定](kernel-extensions-settings-macos.md)に関するページを参照してください。

適用対象: macOS 10.13.2 以降

#### <a name="apps-from-the-store-only-setting-for-windows-10-devices-includes-more-configuration-options----2697002---"></a>Windows 10 デバイスのストアのアプリのみ設定に含まれるその他の構成オプション <!-- 2697002 -->
ユーザーが Windows アプリ ストアからのみアプリをインストールするように、Windows デバイス用のデバイス制限プロファイルを作成するときに **[Apps from the store only]\(ストアのアプリのみ\)** 設定を使用することがでます ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  > **プラットフォームに [Windows 10 以降]** > プロファイルの種類に **[デバイスの制限]** )。 この更新では、この設定はより多くのオプションをサポートするように拡張されています。 

新しい設定を確認するには、[機能を許可または制限する Windows 10 (以降) デバイス設定](device-restrictions-windows-10.md#app-store)に関するページを参照してください。

適用対象:Windows 10 以降

#### <a name="deploy-multiple-zebra-mobility-extensions-device-profiles-to-a-device-same-user-group-or-same-devices-group----4089955---"></a>複数の Zebra モビリティ拡張機能デバイス プロファイルを 1 つのデバイス、同じユーザー グループ、または同じデバイス グループに展開する <!-- 4089955 -->
Intune では、デバイス構成プロファイルで Zebra モビリティ拡張機能 (MX) を使用し、Intune に組み込まれていない Zebra デバイス向け設定をカスタマイズできます。 現在、1 つのデバイスに 1 つのプロファイルを展開できます。 今回の更新では、以下に複数のプロファイルを展開できます。
- 同じユーザー グループ
- 同じデバイス グループ
- 1 つのデバイス

「[Microsoft Intune で Zebra モビリティ拡張機能を備えた Zebra デバイスを使用および管理する](android-zebra-mx-overview.md)」には、Intune で MX を使用する方法が説明されています。

適用対象:Android

#### <a name="some-kiosk-settings-on-ios-devices-are-set-using-block-replacing-allow----4404075----"></a>iOS デバイス上の一部のキオスク設定は、[許可] の代わりに [ブロック] を使用して設定されています。 <!-- 4404075  -->
iOS デバイス上にデバイス制限プロファイルを作成した場合は ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  > **プラットフォームに [iOS]** > プロファイルの種類に **[デバイスの制限]** > **[キオスク]** )、 **[自動ロック]** 、 **[着信音スイッチ]** 、 **[画面の回転]** 、 **[画面スリープ ボタン]** 、および **[音量ボタン]** を設定します。 

今回の更新で、値は **[ブロック]** (機能をブロックする) と **[未構成]** (機能を許可する) になりました。 設定を確認するには、[機能を許可または制限する iOS デバイスの設定](device-restrictions-ios.md#kiosk-supervised-only)に関するページを参照してください。 

適用対象: iOS

#### <a name="use-face-id-for-password-authentication-on-ios-devices----4490704---"></a>iOS デバイスのパスワード認証に Face ID を使用する <!-- 4490704 -->
iOS デバイス用のデバイス制限プロファイルを作成するときは、パスワードに指紋を使用できます。 今回の更新では、指紋のパスワード設定でも顔認識が可能になりました ( **[デバイス構成]** 、 **[プロファイル]** 、 **[プロファイルの作成]** の順に選択し、プラットフォームに **[iOS]** を選択し、プロファイルの種類に **[デバイスの制限]** を選択し、 **[パスワード]** を選択します)。 その結果、次の設定が変更されています。

- **[指紋によるロック解除]** は **[Touch ID と Face ID のロック解除]** になりました。
- **[指紋の変更 (管理モードのみ)]** は **[Touch ID と Face ID の変更 (監視モードのみ)]** になりました。

Face ID は iOS 11.0 以降で使用できます。 設定を確認するには、「[Intune を使用して機能を許可または制限するように iOS デバイスを設定する](device-restrictions-ios.md#password)」を参照してください。

適用対象: iOS

#### <a name="restricting-gaming-and-app-store-features-on-ios-devices-is-now-dependent-on-ratings-region----4593948---"></a>iOS デバイスでのゲームやアプリ ストアの機能制限が年齢区分の地域によって異なるようになりました <!-- 4593948 -->
iOS デバイスでは、ゲーム、アプリ ストア、およびドキュメントの表示に関連する機能を許可または制限できます ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  > **プラットフォームに [iOS]** > プロファイルの種類に **[デバイスの制限]** > **[アプリ ストア、ドキュメント表示、ゲーム]** )。 米国などの年齢区分の地域を選択することもできます。 

今回の更新では、 **[アプリ]** 機能が **[年齢区分の地域]** の子に移動され、 **[年齢区分の地域]** に依存するようになりました。 設定を確認するには、「[Intune を使用して機能を許可または制限するように iOS デバイスを設定する](device-restrictions-ios.md#app-store-doc-viewing-gaming)」を参照してください。

適用対象: iOS

### <a name="device-enrollment"></a>デバイスの登録

#### <a name="windows-autopilot-reset-removes-the-devices-primary-user----4156123---"></a>Windows AutoPilot リセットを実行すると、デバイスのプライマリ ユーザーが削除されます。 <!-- 4156123 -->
この機能は遅れており、今後のスプリントでリリースされる予定です。    

#### <a name="windows-autopilot-support-for-hybrid-azure-ad-join----4809146--"></a>Hybrid Azure AD Join の Windows AutoPilot サポート <!-- 4809146-->
既存デバイスの Windows AutoPilot で、(既存の Azure AD Join サポートに加え) Hybrid Azure AD Join がサポートされるようになりました。 Windows 10 バージョン 1809 以降のデバイスに適用されます。 詳細は、[既存のデバイスの Windows AutoPilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/existing-devices) に関するページを参照してください。



### <a name="device-management"></a>デバイス管理

#### <a name="see-the-security-patch-level-for-android-devices----4461911---"></a>Android デバイス用のセキュリティ パッチ レベルを確認する <!-- 4461911 -->
Android デバイスのセキュリティ パッチ レベルを確認できるようになりました。 これを行うには、 **[Intune]** 、 **[デバイス]** 、 **[すべてのデバイス]** の順に進んでデバイスを選択し、 **[ハードウェア]** を選択します。
パッチ レベルの一覧は **[オペレーティング システム]** セクションにあります。

#### <a name="assign-scope-tags-to-all-managed-devices-in-a-security-group----3173810---"></a>セキュリティ グループ内のすべてのマネージド デバイスにスコープ タグを割り当てる <!-- 3173810 -->
スコープ タグをセキュリティ グループに割り当てられるようになりました。セキュリティ グループのすべてのデバイスもそのスコープ タグに関連付けられます。 これらのグループ内のすべてのデバイスにもスコープ タグが割り当てられます。 この機能で設定されたスコープ タグによって、現在のデバイス スコープ タグ フローで設定されたスコープ タグは上書きされる予定です 詳細は、[分散 IT に RBAC とスコープ タグを使用する方法](scope-tags.md)に関するページを参照してください。

### <a name="device-security"></a>デバイス セキュリティ

#### <a name="use-keyword-search-with-security-baselines-------"></a>セキュリティ ベースラインでキーワード検索を使用する <!--  -->
[セキュリティ ベースライン プロファイル](security-baselines.md#create-the-profile)を作成または編集するとき、新しい *[検索]* バーにキーワードを指定し、利用できる設定グループを検索基準に含まれるグループに絞り込むことができるようになりました。 

#### <a name="the-security-baselines-feature-is-now-generally-available-----3785395---"></a>セキュリティ ベースライン機能の一般提供が開始されました  <!-- 3785395 -->
**セキュリティ ベースライン**機能のプレビューが終わり、一般提供 (GA) になりました。  これは、機能が運用環境で使用できる状態であることを意味します。 ただし、個々のベースライン テンプレートはプレビューのままであり、独自のスケジュールに基づいて評価され、GA リリースされます。

#### <a name="the-mdm-security-baseline-template-is-now-generally-available------3794072-4217151--3534649---"></a>MDM セキュリティ ベースライン テンプレートが一般提供になりました   <!-- 3794072, 4217151,  3534649 -->
MDM セキュリティ ベースラインのプレビューが終わり、一般提供 (GA) になりました。 GA テンプレートは、**2019 年 5 月の MDM セキュリティ ベースライン**として識別されています。  これは新しいテンプレートであり、前のバージョンからのアップグレードではありません。  新しいテンプレートであるため、[それに含まれる設定](security-baseline-settings-windows.md)を確認する必要があり、その後、新しいプロファイルを作成し、テンプレートをデバイスに配備する必要があります。 その他のセキュリティ ベースライン テンプレートはプレビューのままでも構いません。 利用できるベースラインの一覧は、「[使用可能なセキュリティ ベースライン](security-baselines.md#available-security-baselines)」を参照してください。  

新しいテンプレートであるだけではなく、*2019 年 5 月の MDM セキュリティ ベースライン* テンプレートには、"開発中" 記事で最近告知した 2 つの設定が含まれています。  
- Above Lock (ロックの上から):ロックされた画面から音声でアプリを起動します  
- DeviceGuard:仮想化ベースのセキュリティ (VBS) をデバイスの次回起動で使用します  

*2019 年 5 月の MDM セキュリティ ベースライン*には、新しい設定がさらにいくつか追加されています。また、削除された設定もあり、設定の既定値が見直されたものもあります。 プレビューから GA に変更された機能の詳しい一覧は、**新しいテンプレートで変更された箇所**に関するページを参照してください。

#### <a name="security-baseline-versioning-----3194322---"></a>セキュリティ ベースラインのバージョン管理  <!-- 3194322 -->
Intune のセキュリティ ベースラインはバージョン管理に対応しています。 バージョン管理に対応していることで、セキュリティ ベースラインの新しいバージョンがリリースされるたびに、新しいベースラインを一から作り直して配備しなくても、最新のベースライン バージョンを使用するように、既存のセキュリティ ベースライン プロファイルを更新できます。 また、Intune コンソールでは、ベースラインが使用される個別プロファイルの数、プロファイルで使用されるさまざまなベースライン バージョンの数、特定のセキュリティ ベースラインの最新リリースの日付など、各ベースラインに関する情報を表示できます。  詳細は、「**セキュリティ ベースライン**」を参照してください。

#### <a name="the-use-security-keys-for-sign-in-setting-has-moved-----4501151---"></a>[サインインのセキュリティ キーを使用] 設定が移動しました  <!-- 4501151 -->
**サインインのセキュリティ キーを使用**という名称の ID 保護用デバイス構成設定は、「*Windows Hello for Business の構成*」の下位設定から削除されました。 Windows Hello for Business の使用を有効にしなくても、常に使用できる最上位の設定になりました。 詳細は、「[ID 保護](identity-protection-windows-settings.md)」を参照してください。

### <a name="role-based-access-control"></a>ロールベースのアクセス制御

#### <a name="new-permissions-for-assigned-group-admins------4504437-----"></a>割り当てられたグループ管理者の新しいアクセス許可   <!-- 4504437   -->
Intune の組み込み学校管理者ロールに管理対象アプリに対する作成、読み取り、更新、削除 (CRUD) のアクセス許可が付与されるようになりました。 今回の更新は、教育機関向け Intune のグループ管理者として任命されたとき、[自分に与えられているすべての既存のアクセス許可](https://docs.microsoft.com/intune-education/group-admin-delegate#group-admin-permissions)と共に、iOS MDM プッシュ通知証明書、iOS MDM サーバー トークン、iOS VPP トークンを作成、表示、更新、削除できるようになりました。 これらのアクションを実行するには、 **[テナント設定]** 、 **[iOS デバイス管理]** の順に進みます。  

#### <a name="applications-can-use-the-graph-api-to-call-read-operations-without-user-credentials----4655885---"></a>アプリケーションでは Graph API を利用し、ユーザー資格情報なしで読み取り操作を呼び出すことができます。 <!-- 4655885 -->
アプリケーションでは、ユーザー資格情報がなくても、アプリの ID で Intune Graph API 読み取り操作を呼び出すことができます。 Microsoft Graph API for Intune にアクセスする方法については、「[Microsoft Graph での Intune の操作](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0)」を参照してください。

#### <a name="apply-scope-tags-to-microsoft-store-for-business-apps----4392555---"></a>Microsoft Store for Business アプリにスコープ タグを適用する <!-- 4392555 -->
Microsoft Store for Business アプリにスコープ タグを適用できるようになりました。 スコープ タグの詳細は、[分散 IT にロールベースのアクセス制御 (RBAC) とスコープ タグを使用する方法](scope-tags.md)に関するページを参照してください。

## <a name="week-of-june-17-2019"></a>2019 年 6 月 17 日の週 

### <a name="app-management"></a>アプリ管理

#### <a name="new-features-in-microsoft-intune-app"></a>Microsoft Intune アプリの新機能
Android 用 Microsoft Intune アプリ (プレビュー) に新機能が追加されました。 フル マネージド Android デバイスのユーザーは次のことが可能になりました。  

* Intune ポータル サイトまたは Microsoft Intune のアプリを介して登録したデバイスを表示して管理する。    
* サポートが必要な場合はお客様の組織に問い合わせてください。    
* Microsoft にフィードバックを送信する。    
* 組織で設定されている場合は、使用条件を表示する。    

## <a name="week-of-june-10-2019"></a>2019 年 6 月 10 日の週 

### <a name="app-management"></a>アプリ管理

#### <a name="new-sample-apps-showing-intune-sdk-integration-available-on-github----2653471---"></a>GitHub で入手できる Intune SDK 統合を示す新しいサンプル アプリ <!-- 2653471 -->
msintuneappsdk GitHub アカウントで、iOS (Swift)、Android、Xamarin.iOS、Xamarin Forms、Xamarin.Android 向けの新しいサンプル アプリケーションが追加されました。 これらのアプリの目的は、既存のドキュメントを補完し、Intune APP SDK をお客様のモバイル アプリに統合する方法のデモを提供することです。 Intune SDK の追加のガイダンスが必要なアプリ開発者の場合は、次のリンク先のサンプルを参照してください。
- [Chatr](https://github.com/msintuneappsdk/Chatr-Sample-Intune-iOS-App) - 仲介型認証に Azure Active Directory 認証ライブラリ (ADAL) を使用するネイティブ iOS (Swift) インスタント メッセージング アプリ。
- [Taskr](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Android-App) - 仲介型認証に ADAL を使用するネイティブの Android todo リスト アプリ。
- [Taskr](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Xamarin-Android-Apps) - 仲介型認証に ADAL を使用する Xamarin.Android の todo リスト アプリ。このリポジトリには Xamarin.Forms アプリもあります。
- [Xamarin.iOS サンプル アプリ](https://github.com/msintuneappsdk/sample-intune-xamarin-ios) - 必要最低限の Xamarin.iOS サンプル アプリ。

## <a name="week-of-may-27-2019"></a>2019 年 5 月 27 日の週 

### <a name="app-management"></a>アプリ管理

#### <a name="reporting-for-potentially-harmful-apps-on-android-devices----4223162---"></a>Android デバイス上の有害な可能性のあるアプリについてのレポート <!-- 4223162 -->
Intune により、Android デバイス上の有害な可能性のあるアプリに関する追加レポート情報が提供されるようになりました。 

## <a name="week-of-may-20-2019"></a>2019 年 5 月 20 日の週 

### <a name="app-management"></a>アプリ管理

#### <a name="windows-company-portal-app----3316993---"></a>Microsoft ポータル サイト アプリ <!-- 3316993 -->
Windows ポータル サイト アプリには、 **[デバイス]** とラベル付けされた新しいページが設けられました。 **[デバイス]** ページには、登録されているデバイスのすべてのエンド ユーザーが表示されます。 バージョン 10.3.4291.0 以降を使用している場合、ユーザーはポータル サイト上でこの変更を確認できます。 ポータル サイトの構成方法については、「[Microsoft Intune ポータル サイト アプリを構成する方法](company-portal-app.md)」をご覧ください。

### <a name="device-enrollment"></a>デバイスの登録

#### <a name="autopilot-device-orderid-attribute-name-changed-to-group-tag----4659453---"></a>Autopilot デバイスの OrderID 属性の名前がグループ タグに変更された <!-- 4659453 -->

直感的にわかりやすくするために、Autopilot デバイス上での **OrderID** 属性の名前が、**グループ タグ**に変更されました。 Autopilot デバイス情報をアップロードするために CSV を使用する場合は、OrderID ではなく、列ヘッダーとしてグループ タグを使用する必要があります。  

## <a name="week-of-may-13-2019"></a>2019 年 5 月 13 日の週 

### <a name="app-management"></a>アプリ管理

#### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation-----1927359----"></a>Intune ポリシーによって認証方法とポータル サイト アプリのインストールを更新する  <!-- 1927359  -->
Apple の会社用デバイスの登録方法のいずれかを使ってセットアップ アシスタント経由で既に登録されているデバイスの場合、Intune では、特定のデバイスで App Store からインストールされる場合に、ポータル サイト アプリがサポートされなくなります。 この変更は、登録時に Apple セットアップ アシスタントで認証を行う場合にのみ関係があります。 また、この変更は、以下から登録される iOS デバイスのみに影響します。  
* Apple Configurator

* Apple Business Manager

* Apple School Manager

* Apple Device Enrollment Program (DEP)

App Store からポータル サイト アプリをインストールした後、これらのデバイスを登録しようとすると、エラーが発生します。 登録時に Intune によって自動的にプッシュされた場合、これらのデバイスではポータル サイトだけを使用することが期待されます。 Azure portal での Intune の登録プロファイルは、デバイスの認証方法およびポータル サイト アプリを受信するかどうかを指定できるように更新されます。 DEP デバイス ユーザーがポータル サイトを使用するようにしたい場合は、登録プロファイルでユーザー設定を指定する必要があります。 

さらに、iOS ポータル サイト内の **[デバイスの特定]** 画面は、削除される予定です。 そのため、条件付きアクセスの有効化または業務用アプリのデプロイを行う管理者は、DEP 登録プロファイルを更新する必要があります。 この要件は、DEP 登録が設定アシスタントによって認証された場合にのみ、適用されます。 その場合、デバイス上にポータル サイトをプッシュする必要があります。 これを行うには、 **[Intune]**  >  **[デバイスの登録]**  >  **[Apple の登録]**  >  **[Enrollment Program トークン]** の順に選択し、1 つのトークンを選んで **[プロファイル]** から 1 つのプロファイルを選択し、 **[プロパティ]** から **[ポータル サイトのインストール]** を **[はい]** に設定します。

既に登録されている DEP デバイス上にポータル サイトをインストールするには、Intune 上で [クライアント アプリ] に移動し、アプリ構成ポリシーを利用してマネージド アプリとしてプッシュする必要があります。 

#### <a name="configure-how-end-users-update-a-line-of-business-lob-app-using-an-app-protection-policy----3568384---"></a>アプリ保護ポリシーを利用してエンド ユーザーが基幹業務 (LOB) アプリを更新する方法を構成する <!-- 3568384 -->
エンド ユーザーが基幹業務 (LOB) アプリの更新バージョンを取得できる場所を構成できるようになりました。 この機能がエンド ユーザーに対して表示されるのは **[アプリの最小バージョン]** 条件付き起動ダイアログであり、エンド ユーザーは最小バージョンの LOB アプリに更新することを求められます。 LOB アプリ保護ポリシー (APP) の一部として、これらの更新の詳細を提供する必要があります。 この機能は iOS および Android 上で使用できます。 iOS の場合、この機能ではアプリを統合する (または、ラッピング ツールを使用しラップする) ことが必要になります。その際に利用するのは、iOS 用の Intune SDK 10.0.7 以降です。 Android の場合、この機能では最新のポータル サイトが必要になります。 エンド ユーザーが LOB アプリを更新する方法を構成するには、キー `com.microsoft.intune.myappstore` を含むマネージド アプリ構成ポリシーをアプリに送信する必要があります。 送信される値により、エンド ユーザーがアプリをダウンロードするストアが定義されます。 アプリがポータル サイト経由で展開される場合、値は `CompanyPortal` である必要があります。 他のストアの場合は、完全な URL を入力する必要があります。

#### <a name="intune-management-extension-powershell-scripts-----3734186----"></a>Intune 管理拡張機能の PowerShell スクリプト  <!-- 3734186  -->
ユーザーの管理者特権を使用してデバイス上で実行するように、PowerShell スクリプトを構成できます。 詳しくは、「[Intune で Windows 10 デバイスに対して PowerShell スクリプトを使用する](intune-management-extension.md)」と、[Win32 アプリ管理](apps-win32-app-management.md)に関するページをご覧ください。

#### <a name="android-enterprise-app-management----4459905---"></a>Android Enterprise アプリの管理 <!-- 4459905 -->
IT 管理者がより簡単に Android Enterprise 管理を構成および使用できるよう、Intune では 4 つの一般的な Android Enterprise 関連のアプリが Intune 管理コンソールに自動的に追加されます。 この 4 つの Android Enterprise アプリは次のアプリです。

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** - Android Enterprise フル マネージド シナリオで使用されます。
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** - 2 要素認証を使用している場合、アカウントへのサインインを支援します。
- **[Intune ポータル サイト](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** - アプリ保護ポリシー (APP) と Android Enterprise 仕事用プロファイルのシナリオで使用されます。
- [Managed Home Screen](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise) - Android Enterprise 専用またはキオスクのシナリオで使用されます。

以前は、IT 管理者はセットアップの一部として、手動でこれらのアプリを [Managed Google Play ストア](https://play.google.com/store/apps)で探して承認する必要がありました。 この変更により、以前の手動による手順は不要となり、お客様は Android Enterprise 管理をより簡単に素早く使用できるようになります。

管理者は Intune テナントを Managed Google Play に最初に接続したときに、これらの 4 つのアプリが自動的に Intune アプリ一覧に追加されていることを確認できます。 詳細については、[Managed Google Play アカウントへの Intune アカウントの接続](connect-intune-android-enterprise.md)に関するページを参照してください。 自分のテナントを既に接続済みであるか、Android Enterprise を既に使用済みのテナントの場合、管理者が行う必要のある処理はありません。 以上の 4 つのアプリは、2019 年 5 月のサービス ロールアウトの完了から 7 日以内に自動的に表示されます。

### <a name="device-configuration"></a>デバイス構成

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune-----1533038---"></a>PFX Certificate Connector for Microsoft Intune の更新  <!-- 1533038 -->
新しい要求の処理を停止するコネクタの原因である、既存の PFX 証明書の再処理が続行する問題に対処する、[Microsoft Intune の PFX 証明書コネクタ](certficates-pfx-configure.md#whats-new-for-connectors)の更新プログラムをリリースしました。

#### <a name="intune-security-tasks-for-defender-atp-in-public-preview--------3208597---"></a>Defender ATP 用の Intune セキュリティ タスク (パブリック プレビュー)     <!-- 3208597 -->
パブリック プレビューでは、Intune を使用して [Microsoft Defender Advanced Threat Protection (ATP) 用のセキュリティ タスクを管理できます](atp-manage-vulnerabilities.md)。 この ATP との統合によってリスク ベースの手法が追加され、エンドポイントの脆弱性や誤設定を検出し、優先度を付けて修復できるようになり、検出から軽減までにかかる時間が短縮されます。

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---idstaged--"></a>Windows 10 デバイスのコンプライアンス ポリシーでの TPM チップセットのチェック <!-- 3617671   idstaged-->
Windows 10 以降のデバイスの多くには、トラステッド プラットフォーム モジュール (TPM) チップセットが含まれています。 この更新プログラムには、デバイスの TPM チップのバージョンを確認する新しいコンプライアンス設定が含まれています。 

[Windows 10 以降のコンプライアンス ポリシー設定](compliance-policy-create-windows.md#device-security)で、この設定が説明されています。

適用対象:Windows 10 以降

#### <a name="prevent-end-users-from-modifying-their-personal-hotspot-and-disable-siri-server-logging-on-ios-devices----4097904-----"></a>エンド ユーザーによる個人用ホットスポットの変更を防止し、iOS デバイス上での Siri サーバーのログ記録を無効にする <!-- 4097904   -->  
iOS デバイス上にデバイスの制限プロファイルを作成します ( **[デバイスの構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  >  **[iOS]** (プラットフォーム) > **[デバイスの制限]** (プロファイルの種類))。 この更新プログラムには構成できる新しい設定が含まれています。

- **組み込みアプリ**:Siri コマンドに対するサーバー側のログ記録
- **ワイヤレス**:個人用ホットスポットのユーザー変更 (監視モードのみ)

これらの設定を確認するには、[iOS 用の組み込みのアプリ設定](device-restrictions-ios.md#built-in-apps)と [iOS 用のワイヤレス設定](device-restrictions-ios.md#wireless)に移動します。

iOS デバイス 12.2 以降に適用されます。

#### <a name="new-classroom-app-device-restriction-settings-for-macos-devices----4097905-----"></a>macOS デバイス用の新しい Classroom アプリ デバイス制限の設定 <!-- 4097905   --> 
macOS デバイス用のデバイス構成プロファイルを作成できます ( **[デバイスの構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  >  **[macOS]** (プラットフォーム) > **[デバイスの制限]** (プロファイルの種類))。 この更新には、新しい教室アプリ設定、スクリーンショットをブロックするオプション、iCloud フォト ライブラリを無効にするオプションが含まれています。

現在の設定を確認するには、「[Intune を使用して機能を許可または制限するように macOS デバイスを設定する](device-restrictions-macos.md)」を参照してください。

適用対象: macOS

#### <a name="the-ios-password-to-access-app-store-setting-is-renamed---4557891----"></a>iOS の [アプリ ストアにアクセスするためのパスワード] 設定の名前が変更される<!-- 4557891  -->
**[アプリ ストアにアクセスするためのパスワード]** 設定の名前が、 **[すべての購入に iTunes Store パスワードを要求します]** に変更されています ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  >  **[iOS]** (プラットフォームに対応) > **[デバイスの制限]** (プロファイルの種類に対応) > **[アプリ ストア、ドキュメント表示、ゲーム]** )。

使用可能な設定を確認するには、[[アプリ ストア、ドキュメントの表示、ゲーム] の iOS 設定](device-restrictions-ios.md#app-store-doc-viewing-gaming)に移動します。

適用対象: iOS

#### <a name="microsoft-defender-advanced-threat-protection--baseline--preview------3754134---"></a>Microsoft Defender Advanced Threat Protection のベースライン (プレビュー)  <!--  3754134 -->
[Microsoft Defender Advanced Threat Protection](security-baseline-settings-defender-atp.md) の設定に、セキュリティ ベースラインのプレビューを追加しました。 ご使用の環境が [Microsoft Defender Advanced Threat Protection](advanced-threat-protection.md#prerequisites) を使用するための前提条件を満たしている場合は、このベースラインを使用できます。

### <a name="device-enrollment"></a>デバイスの登録

#### <a name="windows-enrollment-status-page-esp-is-now-generally-available----3605348---"></a>Windows 登録ステータス ページ (ESP) が一般提供される <!-- 3605348 -->
登録ステータス ページがプレビューではなくなりました。 詳しくは、「[登録ステータス ページを設定する](windows-enrollment-status.md)」をご覧ください。


#### <a name="intune-user-interface-update---autopilot-enrollment-profile-creation-----4593669---"></a>Intune ユーザー インターフェイスの更新 - Autopilot 登録プロファイルの作成  <!-- 4593669 -->
Autopilot 登録プロファイルを作成するためのユーザー インターフェイスが、Azure ユーザー インターフェイスの形式に準拠するように更新されました。 詳細は、[AutoPilot 登録プロファイルの作成](https://docs.microsoft.com/intune/enrollment-autopilot#create-an-autopilot-deployment-profile)に関するページを参照してください。 Intune の追加のシナリオでは、今後はこの新しい UI 形式に更新されます。

#### <a name="enable-autopilot-reset-for-all-windows-devices----4225665---"></a>すべての Windows デバイスに対して Autopilot リセットを有効にする <!-- 4225665 -->
登録ステータス ページを使用するように構成されていない場合であっても、AutoPilot リセットがすべての Windows デバイスにおいて有効になりました。 初期のデバイス登録時に、登録ステータス ページがデバイスに対して構成されていなかった場合、デバイスではサインイン後、デスクトップへと直接移動します。 同期して Intune 内での適合が確認できるまでに、最大で 8 時間かかる場合があります。 詳しくは、「[Windows Autopilot のリセット](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-reset-remote)」をご覧ください。

#### <a name="exact-imei-format-not-required-when-searching-all-devices---30407680---"></a>[すべてのデバイス] を検索する場合に厳密な IMEI 形式を必須としない <!--30407680 -->
**[すべてのデバイス]** を検索するときに、IMEI 番号にスペースを含める必要がなくなります。

#### <a name="deleting-a-device-in-the-apple-portal-will-be-reflected-in-the-intune-portal---2489996---"></a>Apple ポータルでデバイスを削除すると、Intune ポータルに反映される <!--2489996 -->
Apple の Device Enrollment Program または Apple Business Manager ポータルからデバイスが削除されると、そのデバイスは Intune から次回の同期中に自動的に削除されます。

### <a name="the-enrollment-status-page-now-tracks-win32-apps----2714451---"></a>登録ステータス ページによる Win32 アプリの追跡 <!-- 2714451 -->
これは、Windows 10 バージョン 1903 以降を稼働しているデバイスにのみ適用されます。 詳しくは、「[登録ステータス ページを設定する](windows-enrollment-status.md)」をご覧ください。

### <a name="device-management"></a>デバイス管理

#### <a name="reset-and-wipe-devices-in-bulk-by-using-the-graph-api----3295288---"></a>Graph API を使用してデバイスを一括でリセットおよびワイプする <!-- 3295288 -->
Graph API を使用して 100 台までのデバイスを一括でリセットおよびワイプできるようになりました。


### <a name="monitor-and-troubleshoot"></a>監視とトラブルシューティング

#### <a name="the-encryption-report-is-out-of-public-preview------4587546--------"></a>暗号化レポートのパブリック プレビューが終了する   <!-- 4587546      -->
[BitLocker およびデバイス暗号化用のレポート](encryption-monitor.md)が一般提供されるようになり、パブリック プレビュー段階ではなくなりました。 

<!-- ########################## -->

#### <a name="outlook-signature-and-biometric-settings-for--ios-and-android-devices----4050557---"></a>iOS および Android デバイス用の Outlook 署名と生体認証の設定 <!-- 4050557 -->
iOS および Android デバイス上では、Outlook 内で既定の署名を有効にするかどうかを指定できるようになりました。 さらに、iOS 上の Outlook では、ユーザーによる生体認証設定の変更を許可する選択ができるようになっています。

## <a name="week-of-may-6-2019"></a>2019 年 5 月 6 日の週 

### <a name="device-configuration"></a>デバイス構成

#### <a name="network-access-control-nac-support-for-f5-access-for-ios-devices----4500808---"></a>iOS デバイス用 F5 Access に向けたネットワーク アクセス制御 (NAC) のサポート <!-- 4500808 -->

F5 は、iOS 上の Intune に、F5 Access で NAC 機能を許可する BIG-IP 13 の更新プログラムをリリースしました。 この機能を使用するには、以下を行います。

- BIG-IP を 13.1.1.5 refresh に更新します。 BIG-IP 14 はサポートされていません。
- NAC 用に Intune に BIG-IP を統合します。 「[Overview:Configuring APM for device posture checks with endpoint management systems](https://techdocs.f5.com/kb/en-us/products/big-ip_apm/manuals/product/apm-client-configuration-7-1-6/6.html)」 (概要: エンドポイント管理システムを使用したデバイス ポスチャ チェック用の APM の構成) の手順。
- Intune の VPN プロファイルの **Enable Network Access Control (NAC)** 設定を確認します。

利用できる設定については、[iOS デバイスへの VPN 設定の構成](vpn-settings-ios.md)に関する記事を参照してください。

適用対象: iOS

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune----doc-vso-1521237----"></a>PFX Certificate Connector for Microsoft Intune の更新 <!-- doc-vso 1521237  -->  
ポーリング間隔を 5 分から 30 秒に減らす [PFX Certificate Connector for Microsoft Intune](certficates-pfx-configure.md#whats-new-for-connectors) の更新プログラムをリリースしました。

## <a name="week-of-april-22-2019"></a>2019 年 4 月 22 日の週

### <a name="use-compliance-manager-to-create-assessments-for-microsoft-intune---4404750---"></a>コンプライアンス マネージャーを使用した Microsoft Intune の評価の作成<!-- 4404750 -->

[コンプライアンス マネージャー](https://servicetrust.microsoft.com/ComplianceManager) (別の Microsoft サイトが開きます) は、Microsoft Service Trust Portal 上のワークフローベースのリスク評価ツールです。 これを使用すると、Microsoft のサービスに関連する組織の法令遵守活動の追跡、割り当て、検証を行うことができます。 Office 365、Azure、Dynamics、Professional Services、Intune の使用時に独自のコンプライアンス評価を作成できます。 Intune では、FFIEC と GDPR の 2 つの評価が利用可能です。

コンプライアンス マネージャーは、コントロールを Microsoft が管理するコントロールと、組織が管理するコントロールに分類することによって、労力を集中させるのに役立ちます。 評価の完了後、評価をエクスポートして印刷することができます。

[連邦金融機関検査協議会 (FFIEC)](https://www.microsoft.com/trustcenter/compliance/FFIEC) (別の Microsoft サイトが開きます) のコンプライアンスは、FFIEC によって発行されたオンライン バンキングのための一連の規格です。 Intune を使用する金融機関に最も必要とされる評価です。 これにより、パブリック クラウドのワークロードに関連する FFIEC サイバー セキュリティのガイドラインを満たすために、Intune がどのように役立つかが解釈されます。 Intune の FFIEC 評価は、コンプライアンス マネージャーの 2 つ目の FFIEC 評価です。

次の例で FFIEC コントロールの内訳を確認できます。 64 のコントロールが Microsoft によって管理されます。 残りの 12 のコントロールはお客様の責任となります。

![お客様のアクションと Microsoft のアクションを含む、FFIEC に関する Intune の評価のサンプルを参照してください。](./media/intune-ffiec-assessment-status.png)

[一般データ保護規則 (GDPR)](https://www.microsoft.com/trustcenter/privacy/gdpr/gdpr-overview) (別の Microsoft サイトが開きます) は、個人の権利とデータの保護に役立つ欧州連合 (EU) の法律です。 GDPR は、プライバシー規制の遵守に役立てるために最も必要とされる評価です。 

次の例で GDPR コントロールの内訳を確認できます。 49 のコントロールが Microsoft によって管理されます。 残りの 66 のコントロールはお客様の責任となります。

![お客様のアクションと Microsoft のアクションを含む、GDPR に関する Intune の評価のサンプルを参照してください。](./media/intune-assessment-status.png)

## <a name="week-of-april-15-2019"></a>2019 年 4 月 15 日の週

### <a name="app-management"></a>アプリ管理

#### <a name="openssl-encryption-for-android-app-protection-policies----3747362---"></a>Android アプリ保護ポリシー用の OpenSSL 暗号化 <!-- 3747362 -->
Android デバイスに対する Intune アプリ保護ポリシー (APP) で、FIPS 140-2 に準拠した OpenSSL 暗号化ライブラリが使用されるようになりました。 詳細については、「[Microsoft Intune の Android アプリ保護ポリシー設定](app-protection-policy-settings-android.md)」の「[暗号化](app-protection-policy-settings-android.md#encryption)」のセクションを参照してください。

#### <a name="enable-win32-app-dependencies----2617348----"></a>Win32 アプリ依存関係の有効化 <!-- 2617348  -->
管理者は、Win32 アプリのインストール前に他のアプリが依存関係としてインストールされていることを要求できます。 つまり、デバイスで Win32 アプリをインストールする前に、依存するアプリをインストールする必要があります。 Intune で、 **[クライアント アプリ]**  >  **[アプリ]**  >  **[追加]** を選択して **[アプリの追加]** ブレードを表示します。 **[アプリの種類]** として **[Windows アプリ (Win32)]** を選択します。 アプリを追加した後、 **[依存関係]** を選択し、Win32 アプリをインストールする前にインストールする必要がある依存するアプリを追加できます。 詳細については、「[Intune スタンドアロン - Win32 アプリ管理](apps-win32-app-management.md)」を参照してください。 

#### <a name="app-version-installation-information-for-microsoft-store-for-business-apps----3537391-----"></a>ビジネス向け Microsoft Store のアプリに関する、アプリのバージョンのインストール情報 <!-- 3537391   -->
アプリ インストール レポートには、ビジネス向け Microsoft Store のアプリのバージョン情報が含まれます。 Intune で、 **[クライアント アプリ]**  >  **[アプリ]** を選択します。 **[ビジネス向け Microsoft Store アプリ]** を選択し、次に **[モニター]** セクションの **[デバイスのインストール状態]** を選択します。

#### <a name="additions-to-win32-apps-requirement-rules----3676883-----"></a>Win32 アプリ要件規則への追加 <!-- 3676883   -->
PowerShell スクリプト、レジストリ値、ファイル システム情報に基づく要件規則を作成できます。 Intune で、 **[クライアント アプリ]**  >  **[アプリ]**  >  **[追加]** を選択します。 次に、 **[アプリの追加]** ブレードで **[アプリの種類]** として **[Windows アプリ (Win32)]** を選択します。  **[要件]**  >  **[追加]** を選択して追加の要件規則を構成します。 次に、 **[ファイルの種類]** 、 **[レジストリ]** 、 **[スクリプト]** のいずれかを **[要件の種類]** として選択します。 詳細については、[Win32 アプリ管理](apps-win32-app-management.md)に関するページを参照してください。

#### <a name="configure-your-win32-apps-to-be-installed-on-intune-enrolled-azure-ad-joined-devices----3695227----"></a>Intune に登録された Azure AD 参加済みデバイスにインストールされるように Win32 アプリを構成する <!-- 3695227  -->
Intune に登録された Azure AD 参加済みデバイスにインストールされるように Win32 アプリを割り当てることができます。 Intune での Win32 アプリの詳細については、[Win32 アプリ管理](apps-win32-app-management.md)に関するページを参照してください。

#### <a name="device-overview-shows-primary-user---794259----"></a>デバイス概要でのプライマリ ユーザーの表示 <!--794259  -->
デバイスの概要ページに、ユーザーとデバイスのアフィニティ ユーザー (UDA) とも呼ばれるプライマリ ユーザーが表示されます。 デバイスのプライマリ ユーザーを表示するには、 **[Intune]**  >  **[デバイス]**  >  **[すべてのデバイス]** を選択し、デバイスを選びます。 プライマリ ユーザーは、 **[概要]** ページの上部近くに表示されます。

#### <a name="additional-managed-google-play-app-reporting-for-android-enterprise-work-profile-devices----4105925----"></a>Android エンタープライズ仕事用プロファイル デバイスに関するマネージド Google Play アプリの追加レポート <!-- 4105925  -->
Android エンタープライズ仕事用プロファイル デバイスに展開されたマネージド Google Play アプリについて、デバイスにインストールされているアプリの特定のバージョン番号を表示できます。 これは必須アプリのみに適用されます。  

#### <a name="ios-third-party-keyboards----4111843-----"></a>iOS サード パーティ製キーボード <!-- 4111843   -->
iOS 用の**サードパーティ製キーボード**の設定での Intune アプリ保護ポリシー (APP) のサポートは、iOS プラットフォームの変更によりサポートされなくなりました。 この設定は、Intune の管理コンソールからは構成できなくなり、Intune App SDK でクライアントに強制されなくなります。

### <a name="device-configuration"></a>デバイス構成

#### <a name="set-login-settings-and-control-restart-options-on-macos-devices----1210083----"></a>macOS デバイスでログイン設定を行い、再起動オプションを制御する <!-- 1210083  -->
macOS デバイスで、デバイス構成プロファイルを作成できます ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]** > プラットフォームに **[macOS]** を選択し、プロファイルの種類に **[デバイス機能]** を選択します)。 この更新には、カスタム バナーの表示、ユーザーのサインイン方法の選択、電源設定の表示または非表示などの新しいログイン ウィンドウ設定が含まれています。

これらの設定を表示するには、[macOS デバイスの機能設定](macos-device-features-settings.md)に関するページを参照してください。

#### <a name="configure-wifi-on-android-enterprise-device-owner-dedicated-devices-running-in-multi-app-kiosk-mode---3041940----"></a>マルチアプリ キオスク モードで実行されている Android エンタープライズのデバイスの所有者専用デバイスに対する WiFi の構成 <!--3041940  -->
マルチアプリ キオスク モードで専用デバイスとして実行されている場合、Android エンタープライズのデバイスの所有者に対して設定を有効にできます。 この更新では、ユーザーが WiFi ネットワークを構成して接続できるようにすることができます ( **[Intune]**  >  **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  > プラットフォームに **[Android エンタープライズ]** > プロファイルの種類に **[デバイスの所有者のみ]、[デバイスの制限]** > **[専用デバイス]**  >  **[キオスク モード]** : **[複数アプリ]**  >  **[WiFi 構成]** )。 

構成できるすべての設定を確認するには、[機能を許可または制限する Android エンタープライズ デバイスの設定](device-restrictions-android-for-work.md)に関するページを参照してください。

適用対象:マルチアプリ キオスク モードで実行されている Android エンタープライズ専用デバイス


#### <a name="configure-bluetooth-and-pairing-on-android-enterprise-device-owner-dedicated-devices-running-in-multi-app-kiosk-mode----3041941----"></a>マルチアプリ キオスク モードで実行されている Android エンタープライズのデバイスの所有者専用デバイスに対する Bluetooth とペアリングの構成 <!-- 3041941  -->
マルチアプリ キオスク モードで専用デバイスとして実行されている場合、Android エンタープライズのデバイスの所有者に対して設定を有効にできます。 この更新では、エンドユーザーが Bluetooth を有効にして Bluetooth 経由でデバイスをペアリングできるようになります ( **[Intune]**  >  **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  > プラットフォームに **[Android エンタープライズ]** > プロファイルの種類に **[デバイスの所有者のみ]、[デバイスの制限]** > **[専用デバイス]**  >  **[キオスク モード]** : **[複数アプリ]**  >  **[Bluetooth の構成]** )。 

構成できるすべての設定を確認するには、[機能を許可または制限する Android エンタープライズ デバイスの設定](device-restrictions-android-for-work.md)に関するページを参照してください。

適用対象:マルチアプリ キオスク モードで実行されている Android エンタープライズ専用デバイス

#### <a name="create-and-use-oemconfig-device-configuration-profiles-in-intune----3305883----"></a>Intune での OEMConfig デバイス構成プロファイルの作成と使用 <!-- 3305883  -->
この更新では、Intune で OEMConfig を使用した Android エンタープライズ デバイスの構成がサポートされています。 具体的には、デバイス構成プロファイルを作成し、OEMConfig を使用して Android エンタープライズ デバイスに設定を適用できます ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  > プラットフォームに **[Android エンタープライズ]** )。

現在、OEM のサポートは OEM ごとになっています。 必要な OEMConfig アプリが OEMConfig アプリの一覧にない場合は、`IntuneOEMConfig@microsoft.com` にお問い合わせください。

この機能の詳細については、「[Use and manage Android Enterprise devices with OEMConfig in Microsoft Intune](android-oem-configuration-overview.md)」(Microsoft Intune での OEMConfig を使用した Android エンタープライズ デバイスの使用と管理) を参照してください。

適用対象:Android エンタープライズ

#### <a name="windows-update-notifications-----3316758-3316782----"></a>Windows Update の通知  <!-- 3316758, 3316782  -->
Windows Update リングの構成に、Intune コンソール内から管理できる 2 つの*ユーザー エクスペリエンス設定*を追加しました。 次のことができるようになりました。
- ユーザーが [Windows 更新プログラムの有無をスキャン](windows-update-settings.md#block-user-from-scanning-for-windows-updates)することをブロックまたは許可する。
- ユーザーが表示できる [Windows Update の通知レベル](windows-update-settings.md#windows-update-notification-level)を管理する。

#### <a name="new-device-restriction-settings-for-android-enterprise-device-owner----3574254----"></a>Android エンタープライズのデバイスの所有者に関する新しいデバイス制限の設定 <!-- 3574254  -->
Android エンタープライズ デバイスでは、機能を許可または制限したり、パスワード規則を設定したりするデバイス制限プロファイルを作成できます ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]** > プラットフォームに **[Android エンタープライズ]** を選択し、プロファイルの種類に **[デバイスの所有者のみ] > [デバイスの制限]** を選択します)。 

この更新プログラムには、新しいパスワード設定が含まれています。また、この更新プログラムによって、フル マネージド デバイス用に Google Play ストア内のアプリへのフル アクセスができます。 現在の設定一覧を確認するには、[Android エンタープライズ デバイスの機能を許可または制限する設定](device-restrictions-android-for-work.md)に関するページを参照してください。 

適用対象:Android エンタープライズのフル マネージド デバイス

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---"></a>Windows 10 デバイスのコンプライアンス ポリシーでの TPM チップセットのチェック <!-- 3617671 -->

この機能のリリースは遅延しており、もう少し後になる予定です。

#### <a name="updated-ui-changes-for-microsoft-edge-browser-on-windows-10-and-later-devices----3775833-----"></a>Windows 10 以降のデバイスでの Microsoft Edge ブラウザーの更新された UI の変更 <!-- 3775833   -->
デバイス構成プロファイルを作成するとき、Windows 10 以降のデバイスで Microsoft Edge の機能を許可または制限することができます ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  > プラットフォームに **[Windows 10 以降]** > プロファイルの種類に **[デバイスの制限]** > **[Microsoft Edge ブラウザー]** )。 この更新では、Microsoft Edge の設定がよりわかりやすく、より簡単に理解できるようになっています。 

これらの機能を表示するには、[Microsoft Edge ブラウザーのデバイス制限の設定](device-restrictions-windows-10.md#microsoft-edge-browser)に関するページを参照してください。

適用対象:Windows 10 以降

#### <a name="expanded-support-for-android-enterprise-fully-managed-devices--preview-------3903241-3903244-3903246-----"></a>Android エンタープライズ フル マネージド デバイス向け拡張サポート (プレビュー)  <!--   3903241, 3903244, 3903246   -->
引き続きパブリック プレビュー段階にある Android エンタープライズ フル マネージド デバイスのサポートを、以下を含むように拡張しました ([最初の発表は 2019 年 1 月](whats-new.md#week-of-january-14-2019))。 

- フル マネージドの専用デバイスでは、[コンプライアンス ポリシー](compliance-policy-create-android-for-work.md)を作成してパスワード規則やオペレーティング システムの要件を含めることができます ( **[デバイスのポリシー準拠]**  >  **[ポリシー]**  >  **[ポリシーの作成]**  > プラットフォームに **[Android エンタープライズ]** を選択し、プロファイルの種類に **[デバイスの所有者]** を選択します)。 

  専用デバイスでは、デバイスが **[非準拠]** と表示されることがあります。 条件付きアクセスは、専用デバイスでは使用できません。 専用デバイスを割り当てられたポリシーに準拠させるためのタスクやアクションを必ず完了してください。

- [条件付きアクセス](conditional-access.md) - Android に適用される条件付きアクセスのポリシーは、Android エンタープライズ フル マネージド デバイスにも適用されます。 ユーザーは **Microsoft Intune アプリ**を使用して、自分のフル マネージド デバイスを Azure Active Directory に登録できるようになりました。 そのうえで、コンプライアンスの問題を確認して解決し、組織のリソースにアクセスします。

- 新しいエンドユーザー アプリ (Microsoft Intune アプリ) - Android 完全管理対象デバイス向けの新しいエンドユーザー アプリがあります。**Microsoft Intune** という名前です。 この新しいアプリは軽量かつ最新のものであり、ポータル サイト アプリと同様の機能が提供されますが、フル マネージド デバイスの場合です。 詳細については、[Google Play の Microsoft Intune アプリ](https://play.google.com/store/apps/details?id=com.microsoft.intune)に関するページを参照してください。

Android のフル マネージド デバイスを設定するには、 **[デバイスの登録]**  >  **[Android の登録]**  >  **[Corporate-owned, fully managed user devices]\(会社が所有する完全に管理されたユーザー デバイス\)** に移動します。 フル マネージド Android デバイスのサポートはプレビュー段階であり、一部の Intune 機能は完全に機能しない可能性があります。  

このプレビューの詳細については、「[Microsoft Intune - Preview 2 for Android Enterprise Fully Managed devices](https://aka.ms/preview2_AE_fullymanaged)」(Microsoft Intune - Android エンタープライズ フル マネージド デバイス用プレビュー 2) のブログを参照してください。


### <a name="device-enrollment"></a>デバイスの登録

#### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470----"></a>セットアップ アシスタント中、一部の画面をスキップするようにプロファイルを構成する <!-- 2276470  -->
macOS 登録プロファイルを作成するとき、セットアップ アシスタントを使用中のユーザーに表示される次の画面のスキップを構成できます。
- 外観
- ディスプレイの色調
- iCloudStorage 新しいプロファイルを作成するかプロファイルを編集する場合は、選択したスキップする画面が Apple MDM サーバーと同期している必要があります。  ユーザーは、プロファイルの変更を取得するときに遅延が発生しないように、手動でのデバイスの同期を発行できます。
詳しくは、「[Device Enrollment Program または Apple School Manager を使用して macOS デバイスを自動登録する](device-enrollment-program-enroll-macos.md)」をご覧ください。

#### <a name="bulk-device-naming-when-enrolling-corporate-ios-devices--3566569----"></a>企業の iOS デバイスを登録するときのデバイスの一括名前付け<!--3566569  -->
Apple の会社登録方法 (DEP/ABM/ASM) のいずれかを使用する場合、受信 iOS デバイスに自動的に名前を付けるためにデバイス名の形式を設定できます。 テンプレートで、デバイスの種類とシリアル番号を含む形式を指定できます。 これを行うには、 **[Intune]**  >  **[デバイスの登録]**  >  **[Apple の登録]**  >  **[Enrollment Program トークン]**  >  **[トークンの選択]**  > **[プロファイルの作成]**  >  **[Device naming format]\(デバイスの名前付け形式\)** を選択します。 既存のプロファイルを編集できますが、新しく同期されたデバイスのみに名前が適用されます。

#### <a name="updated-default-timeout-message-on-enrollment-status-page----3959331---"></a>登録ステータス ページの更新された既定のタイムアウト メッセージ <!-- 3959331 -->
登録ステータス ページ (ESP) が ESP プロファイルに指定されたタイムアウト値を超えたときにユーザーに表示される、既定のタイムアウト メッセージを更新しました。 新しい既定のメッセージは、ユーザーに表示され、ユーザーが ESP 展開で行う次のアクションを理解するのに役立ちます。  

### <a name="device-management"></a>デバイス管理

#### <a name="retire-noncompliant-devices-----1827291-----"></a>非準拠デバイスをインベントリから削除する  <!-- 1827291   -->
この機能は遅れており、将来のリリースが予定されています。


### <a name="monitor-and-troubleshoot"></a>監視とトラブルシューティング

#### <a name="intune-data-warehouse-v10-changes-reflecting-back-to-beta----4403765---"></a>ベータに反映された Intune データ ウェアハウス V1.0 の変更 <!-- 4403765 -->
V1.0 が 1808 で初めて導入されたとき、ベータ API とはいくつかの重要な点で異なっていました。 1903 では、それらの変更がベータ API バージョンに反映されます。 ベータ API バージョンを使用する重要なレポートがある場合は、破壊的な変更を回避するためにそれらのレポートを V1.0 に切り替えることを強くお勧めします。 詳細については、「[Intune データ ウェアハウス API の変更ログ](reports-changelog.md#1903-part-2)」を参照してください。

#### <a name="monitor-security-baseline-status-public-preview----3082047---"></a>セキュリティ ベースライン状態のモニター (パブリック プレビュー) <!-- 3082047 --> 
セキュリティ ベースラインのモニタリングに[カテゴリごとのビュー](security-baselines-monitor.md#per-category-view)を追加しました (セキュリティ ベースラインは引き続きプレビュー段階です)。 カテゴリごとのビューには、ベースラインの各カテゴリと、そのカテゴリの各状態グループに分類されるデバイスの割合が表示されます。 個々のカテゴリに一致しない、構成が間違っている、または適用されないデバイスの数を把握できるようになりました。

### <a name="role-based-access-control"></a>ロールベースのアクセス制御

#### <a name="scope-tags-for-apple-vpp-tokens---2371886----"></a>Apple VPP トークンのスコープ タグ <!--2371886  -->
Apple VPP トークンにスコープ タグを追加できるようになりました。 同じスコープ タグを割り当てられたユーザーだけが、そのタグを使用して Apple VPP トークンにアクセスできます。 そのトークンを使用して購入した VPP アプリと電子ブックにスコープ タグが継承されます。 スコープ タグの詳細については、[RBAC とスコープ タグの使用](scope-tags.md)に関するページを参照してください。







## <a name="week-of-april-1-2019"></a>2019 年 4 月 1 日の週

### <a name="device-configuration"></a>デバイス構成

#### <a name="updated-certificate-connectors-----icm-113304612---"></a>更新された証明書コネクタ  <!-- ICM 113304612 -->
[Intune Certificate Connector と Microsoft Intune 用 PFX 証明書コネクタ](certficates-pfx-configure.md#whats-new-for-connectors)の両方の更新プログラムをリリースしました。 新しいリリースでは、いくつかの既知の問題を修正しています。  

### <a name="app-management"></a>アプリ管理

#### <a name="user-experience-update-for-the-company-portal-app-for-ios----2536024---"></a>iOS 用ポータル サイト アプリに関するユーザー エクスペリエンスの更新プログラム <!-- 2536024 -->
iOS デバイス用ポータル サイト アプリのホーム ページが再設計されました。 この変更によって、ホーム ページでは iOS UI パターンにより適切に従うようになり、アプリと電子ブックの検出可用性も向上しました。

#### <a name="changes-to-company-portal-enrollment-for-ios-12-device-users---3448635---"></a>iOS 12 デバイス ユーザー用ポータル サイトの登録の変更 <!--3448635 -->  
Apple iOS 12.2 でリリースされた MDM 登録変更に合わせて、iOS 用ポータル サイトの登録画面と手順が更新されました。 更新されたワークフローでは、次のような場合にユーザーにメッセージが表示されます。  

* Safari でポータル Web サイトを開き、ポータル サイト アプリに戻る前に管理プロファイルをダウンロードできるようにする。  
* [設定] アプリを開き、デバイスに管理プロファイルをインストールする。
* ポータル サイト アプリに戻り、登録を完了する。  

更新された登録の手順と画面については、[Intune への iOS デバイスの登録](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios)に関するページを参照してください。  

## <a name="week-of-march-25-2019"></a>2019 年 3 月 25 日の週

### <a name="monitor-and-troubleshoot"></a>監視とトラブルシューティング

### <a name="support-for-the-power-bi-compliance-app-from-the-data-warehouse-blade-in-microsoft-intune----4260871---"></a>Microsoft Intune での Power BI コンプライアンス アプリのデータ ウェアハウス ブレードのサポート <!-- 4260871 -->
以前、 **[Intune データ ウェアハウス]** ブレードの **[Power BI ファイルのダウンロード]** リンクでは、Intune データ ウェアハウス レポート (.pbix ファイル) がダウンロードされていました。 このレポートは Power BI コンプライアンス アプリに置き換えられました。 Power BI コンプライアンス アプリには特別な読み込みまたはセットアップは必要ありません。 Power BI オンライン ポータル上で直接開き、資格情報に基づいて、お使いの Intune テナントのデータを具体的に表示します。 Intune で、[Intune] ブレードの右側にある **[Intune データ ウェアハウスの設定]** リンクを選択します。 次に **[Power BI アプリを取得する]** をクリックします。 詳細については、「[Power BI でデータ ウェアハウスに接続する](reports-proc-get-a-link-powerbi.md)」を参照してください。

## <a name="week-of-march-18-2019"></a>2019 年 3 月 18 日の週

### <a name="app-management"></a>アプリ管理

#### <a name="deploy-microsoft-visio-and-microsoft-project----3725386----"></a>Microsoft Visio と Microsoft Project の展開 <!-- 3725386  -->
Microsoft Intune を使用して、Windows 10 デバイスに Microsoft Visio Pro for Office 365 と Microsoft Project Online デスクトップ クライアントを独立したアプリとして展開できるようになりました (これらのアプリのライセンスを所有している場合)。 Intune で、 **[クライアント アプリ]**  >  **[アプリ]**  >  **[追加]** を選択して **[アプリの追加]** ブレードを表示します。 **[アプリの追加]** ブレードで、 **[アプリの種類]** として **[Windows 10]** を選択します。 次に、 **[アプリ スイートの構成]** を選択してインストールするアプリを選びます。 Windows 10 デバイス用 Office 365 アプリの詳細については、「[Microsoft Intune で Windows 10 デバイスに Office 365 アプリを割り当てる](apps-add-office365.md)」を参照してください。

#### <a name="microsoft-visio-pro-for-office-365-product-name-change----3593653----"></a>Microsoft Visio Pro for Office 365 製品名の変更 <!-- 3593653  -->
**Microsoft Visio Pro for Office 365** は、**Microsoft Visio Online プラン 2** と呼ばれるようになりました。  Microsoft Visio の詳細については、「[Visio Online プラン 2](https://products.office.com/visio/visio-online-plan-2)」を参照してください。 Windows 10 デバイス用 Office 365 アプリの詳細については、「[Microsoft Intune で Windows 10 デバイスに Office 365 アプリを割り当てる](apps-add-office365.md)」を参照してください。

#### <a name="intune-app-protection-policy-app-character-limit-setting----3291302----"></a>Intune アプリ保護ポリシー (APP) の文字制限の設定 <!-- 3291302  -->
Intune 管理者は、Intune APP の **[他のアプリとの間で切り取り、コピー、貼り付けを制限する]** ポリシー設定の例外を指定できます。  管理者は、マネージド アプリから切り取りまたはコピーできる文字数を指定できます。 この設定により、[他のアプリとの間で切り取り、コピー、貼り付けを制限する] 設定に関係なく、指定した文字数を任意のアプリと共有できます。 Android 用 Intune ポータル サイト アプリのバージョンは、バージョン 5.0.4364.0 またはそれ以降である必要があることに注意してください。 詳細については、[iOS のデータの保護](app-protection-policy-settings-ios.md#data-protection)、[Android のデータの保護](app-protection-policy-settings-android.md#data-protection)、および[クライアント アプリの保護ログのレビュー](app-protection-policy-settings-log.md#app-protection-policy-settings)に関するページを参照してください。

#### <a name="office-deployment-tool-odt-xml-for-office-proplus-deployment----3192477-----"></a>Office 展開ツール (ODT) の Office ProPlus 展開用 XML <!-- 3192477   -->
Intune 管理コンソールで Office Pro Plus のインスタンスを作成するときに、Office 展開ツール (ODT) XML を提供できるようになります。 これにより、既存の Intune の UI オプションによってニーズが満たされない場合に、より大きなカスタマイズが可能になります。 詳細については、「[Microsoft Intune で Windows 10 デバイスに Office 365 アプリを割り当てる](https://docs.microsoft.com/intune/apps-add-office365)」と「[Office 展開ツールのオプションの構成](https://docs.microsoft.com/DeployOffice/configuration-options-for-the-office-2016-deployment-tool)」を参照してください。

#### <a name="app-icons-will-now-be-displayed-with-an-automatically-generated-background----1429026----"></a>自動的に生成される背景でのアプリ アイコンの表示 <!-- 1429026  -->
Windows ポータル サイト アプリで、アプリのアイコンが、アイコンの主調色に基づいて自動生成される背景で表示されます (主調色を検出できた場合)。 適用できる場合は、アプリ タイルで以前表示されていた灰色の枠線が、この背景によって置き換えられます。 この変更は、10.3.3451.0 より後のバージョンのポータル サイトでユーザーに表示されます。

#### <a name="install-available-apps-using-the-company-portal-app-after-windows-bulk-enrollment----2751523-----"></a>Windows 一括登録後にポータル サイト アプリを使用して利用可能なアプリをインストールする <!-- 2751523   -->
[Windows 一括登録](windows-bulk-enroll.md) (プロビジョニング パッケージ) を使用して Intune に登録されている Windows デバイスは、ポータル サイト アプリを使用して、使用可能なアプリをインストールできるようになります。 ポータル サイト アプリの詳細については、[手動での Windows 10 ポータル サイトの追加](store-apps-company-portal-app.md)に関するページと、「[Microsoft Intune ポータル サイト アプリを構成する方法](company-portal-app.md)」を参照してください。

#### <a name="the-microsoft-teams-app-can-be-selected-as-part-of-the-office-app-suite----3828932----"></a>Microsoft Teams アプリを Office アプリ スイートの一部として選択できる <!-- 3828932  -->
Microsoft Teams アプリを Office Pro Plus アプリ スイートのインストールの一部として含めるか除外することができます。 この機能は、Office Pro Plus のビルド番号 16.0.11328.20116 以降で使用できます。 インストールを完了するには、サインアウトしてからデバイスにサインインする必要があります。 Intune で、 **[クライアント アプリ]**  >  **[アプリ]**  >  **[追加]** を選択します。 **[Office 365 スイート]** アプリの種類の 1 つを選択し、次に **[アプリ スイートの構成]** を選択します。

### <a name="device-configuration"></a>デバイス構成

#### <a name="automatically-start-an-app-when-running-multiple-apps-in-kiosk-mode-on-windows-10-and-later-devices----2351390---"></a>Windows 10 以降のデバイスのキオスク モードで複数のアプリを実行しているときに、アプリを自動的に開始する <!-- 2351390 -->

Windows 10 以降のデバイスでは、デバイスをキオスク モードで実行し、多くのアプリを実行できます。 この更新には、 **[自動起動]** 設定があります ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  > プラットフォームに **[Windows 10 以降]** > プロファイルの種類に **[キオスク]** > **[複数アプリのキオスク]** )。 この設定を使用して、ユーザーがデバイスにサインインしたときにアプリを自動的に起動できます。

すべてのキオスク設定の説明を見るには、「[Intune で Windows 10 以降のデバイスをキオスクとして実行するための設定](kiosk-settings-windows.md)」を参照してください。

適用対象:Windows 10 以降

#### <a name="operational-logs-also-show-details-on-non-compliant-devices----4063755----"></a>操作ログにも非準拠デバイスの詳細を表示 <!-- 4063755  -->
Intune のログを Azure Monitor の機能にルーティングする場合、操作ログもルーティングすることができます。 この更新では、操作ログで非準拠デバイスに関する情報も提供されます。 

この機能の詳細については、「[Intune でストレージ、イベント ハブ、または Log Analytics にログ データを送信する](review-logs-using-azure-monitor.md)」を参照してください。

#### <a name="route-logs-to-azure-monitor-in-more-intune-workloads----3804627---"></a>より多くの Intune ワークロードで Azure Monitor にログをルーティングする <!-- 3804627 -->
Intune では、監査ログと操作ログを Azure Monitor のイベント ハブ、ストレージ、ログ分析にルーティングできます ( **[Intune]**  >  **[モニター]**  >  **[診断設定]** )。 この更新では、コンプライアンス、構成、クライアント アプリなど、より多くの Intune ワークロードでこれらのログをルーティングできます。 

Azure Monitor へのログのルーティングの詳細については、「[Intune でストレージ、イベント ハブ、または Log Analytics にログ データを送信する](review-logs-using-azure-monitor.md)」を参照してください。

#### <a name="create-and-use-mobility-extensions-on-android-zebra-devices-in-intune----3305880-----"></a>Intune で Android Zebra デバイス上にモビリティ拡張機能を作成して使用する <!-- 3305880   -->
この更新では、Intune で Android Zebra デバイスの構成がサポートされています。 具体的には、デバイス構成プロファイルを作成し、StageNow によって生成されたモビリティ拡張機能 (MX) プロファイルを使用して Android Zebra デバイスに設定を適用できます ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  > プラットフォームに **[Android]** を選択し、プロファイルの種類に **[MX プロファイル (Zebra のみ)]** を選択します)。

この機能の詳細については、[Intune のモビリティ拡張機能による Zebra デバイスの使用と管理](android-zebra-mx-overview.md)に関するページを参照してください。

適用対象:Android

### <a name="device-management"></a>デバイス管理

#### <a name="encryption-report-for-windows-10-devices-in-public-preview---2351538---"></a>Windows 10 デバイスでの暗号化レポート (パブリック プレビュー)<!-- 2351538 -->  
新しい[暗号化レポート (プレビュー)](encryption-monitor.md) を使用して、Windows 10 デバイスの暗号化の状態に関する詳細を確認できます。 利用可能な詳細には、デバイスの TPM バージョン、暗号化の準備と状態、エラー レポートなどが含まれます。  

#### <a name="access-bitlocker-recovery-keys-from-the-intune-portal-in-public-preview----2351547-----"></a>Intune ポータルからの BitLocker 回復キーへのアクセス (パブリック プレビュー) <!-- 2351547   -->  
Intune を使用して、Azure Active Directory から BitLocker キー ID や BitLocker 回復キーに関する[詳細を表示](encryption-monitor.md)できるようになりました。

#### <a name="microsoft-edge-support-for-intune-scenarios-on-ios-and-android-devices----3411007---"></a>iOS および Android デバイスでの Intune シナリオに対する Microsoft Edge サポート <!-- 3411007 -->
エンドユーザー エクスペリエンスが改善されたことで、Microsoft Edge で Intune Managed Browser と同じ管理シナリオがすべてサポートされるようになります。 Intune ポリシーで有効になっている Microsoft Edge のエンタープライズ機能には、デュアル ID、アプリ保護ポリシーの統合、Azure アプリケーション プロキシの統合、マネージドのお気に入り、ホーム ページのショートカットが含まれます。 詳細については、[Microsoft Edge のサポート](app-configuration-managed-browser.md#microsoft-edge-support)に関するページを参照してください。

#### <a name="exchange-onlineintune-connector-deprecate-support-for-eas-only-devices---3105122----"></a>EAS 専用デバイスに対する Exchange Online/Intune コネクタのサポート廃止 <!--3105122  -->
Intune コンソールでは、Intune コネクタを使用して Exchange Online に接続されている EAS 専用デバイスの表示と管理がサポートされなくなりました。 代わりに次のオプションがあります。
- モバイルデバイス管理 (MDM) でデバイスを登録する
- Intune App Protection ポリシーを使用してデバイスを管理する
- 「[Exchange Online のクライアントとモバイル](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/clients-and-mobile-in-exchange-online)」で説明されているように Exchange コントロールを使用する

### <a name="search-the-all-devices-page-for-an-exact-device-by-using-name---4254930---"></a>すべてのデバイスの検索ページで [名前] を使用して正確なデバイスを探す <!--4254930 -->
正確なデバイス名を検索できるようになりました。 **[Intune]**  >  **[デバイス]**  >  **[すべてのデバイス]** に移動し、検索ボックスでデバイス名を {} で囲って完全一致を検索します。 たとえば、 **{Device12345}** のようにします。

### <a name="monitor-and-troubleshoot"></a>監視とトラブルシューティング

#### <a name="support-for-additional-connectors-on-the-tenant-status-page----3617202----"></a>テナントの状態ページでの追加のコネクタのサポート <!-- 3617202  -->
[テナントの状態ページ](tenant-status.md)に、*Windows Defender Advanced Threat Protection* (ATP) やその他の Mobile Threat Defense コネクタなど、追加のコネクタに関する追加情報が表示されるようになりました。

### <a name="role-based-access-control"></a>ロールベースのアクセス制御

#### <a name="granting-intune-read-only-access-to-some-azure-active-directory-roles----3637917----"></a>Intune の読み取り専用アクセス権を一部の Azure Active Directory ロールに付与する <!-- 3637917  -->
Intune の読み取り専用アクセスが次の Azure AD ロールに付与されています。 Azure AD ロールで付与されたアクセス許可は、Intune ロールベース アクセス制御 (RBAC) で付与されたアクセス許可よりも優先されます。

Intune の監査データへの読み取り専用アクセス:

- コンプライアンス管理者
- コンプライアンス データ管理者

すべての Intune データへの読み取り専用アクセス:

- セキュリティ管理者
- セキュリティ オペレーター
- セキュリティ閲覧者

詳細については、[ロールベースのアクセス制御](role-based-access-control.md)に関するページを参照してください。

#### <a name="scope-tags-for-ios-app-provisioning-profiles---2934430-----"></a>iOS アプリ プロビジョニング プロファイルでのスコープのタグ <!--2934430   -->
iOS アプリ プロビジョニング プロファイルにスコープのタグを追加すると、ロールを持つユーザーのうち、そのスコープのタグも割り当てられているユーザーだけが iOS アプリ プロビジョニング プロファイルにアクセスできるようになります。 スコープのタグの詳細については、[RBAC とスコープのタグの使用](scope-tags.md)に関するページを参照してください。

#### <a name="scope-tags-for-app-configuration-policies---2371891-----"></a>アプリ構成ポリシー用のスコープのタグ <!--2371891   -->
アプリ構成ポリシーにスコープのタグを追加すると、ロールを持つユーザーのうち、そのスコープのタグも割り当てられているユーザーだけがアプリ構成ポリシーにアクセスできるようになります。 同じスコープのタグが割り当てられているアプリのみをアプリ構成ポリシーの対象にする、またはアプリ構成ポリシーと関連付けることができます。 スコープのタグの詳細については、[RBAC とスコープのタグの使用](scope-tags.md)に関するページを参照してください。

### <a name="microsoft-edge-support-for-intune-scenarios-on-ios-and-android-devices----3411007---"></a>iOS および Android デバイスでの Intune シナリオに対する Microsoft Edge サポート <!-- 3411007 -->
Microsoft Edge で、Intune Managed Browser と同じ管理シナリオがすべてサポートされ、エンド ユーザー エクスペリエンスの機能強化が追加されます。 Intune ポリシーで有効になっている Microsoft Edge のエンタープライズ機能には、デュアル ID、アプリ保護ポリシーの統合、Azure アプリケーション プロキシの統合、マネージドのお気に入り、ホーム ページのショートカットが含まれます。 詳細については、[Microsoft Edge のサポート](app-configuration-managed-browser.md#microsoft-edge-support)に関するページを参照してください。

## <a name="week-of-february-25-2019"></a>2019 年 2 月 25 日の週

### <a name="device-configuration"></a>デバイス構成

#### <a name="intune-powershell-module----951068----"></a>Intune PowerShell モジュール <!-- 951068  -->
Microsoft Graph を通じて Intune API のサポートを提供する PowerShell モジュールが、[Microsoft PowerShell ギャラリー](https://www.powershellgallery.com/packages/Microsoft.Graph.Intune/6.1902.1.10)で利用可能になりました。

- [このモジュールの使用方法に関する詳細](https://github.com/Microsoft/Intune-PowerShell-SDK/blob/master/README.md)
- [このモジュールを使用するシナリオの例](https://github.com/Microsoft/Intune-PowerShell-SDK/blob/master/Samples/README.md)

#### <a name="improved-support-for-delivery-optimization----3183757----"></a>配信の最適化のサポート強化  <!--3183757  -->
配信の最適化を構成するための Intune でのサポートを拡張しました。 [配信の最適化設定](delivery-optimization-settings.md)の拡張された一覧を構成し、それを Intune コンソールから直接、デバイスに対して指定することができます。


## <a name="week-of-february-18-2019"></a>2019 年 2 月 18 日の週

### <a name="app-management"></a>アプリ管理

#### <a name="intune-will-leverage-google-play-protect-apis-on-android-devices----2577355-----"></a>Android デバイスで Intune が Google Play Protect API を利用する <!-- 2577355   -->
一部の IT 管理者は、エンド ユーザーが自身の携帯電話を root 化したり脱獄させたりする可能性がある BYOD 環境に直面しています。 この行動は、悪意のないものであっても、エンド ユーザーのデバイス上にある組織のデータを保護するために設定されている多くの Intune ポリシーをバイパスする結果となります。 したがって、Intune では、登録済みのデバイスと未登録のデバイスの両方にルート化および脱獄の検出を提供しています。 このリリースでは、Intune は未登録のデバイスに対する既存のルート検出チェックに追加するため、Google Play Protect API を利用します。 Google では発生するルート検出チェックのすべてを共有していませんが、これらの API により、デバイスのカスタマイズ化から何らかの理由で自身のデバイスをルート化しているユーザーを検出して、古いデバイスで新しい OS の更新プログラムを取得できるようにすることを想定しています。 これにより、これらのユーザーが会社のデータにアクセスすることをブロックしたり、これらのユーザーの会社のアカウントをポリシーを有効にしたアプリからワイプしたりすることができます。 付加価値として、IT 管理者は Intune App Protection ブレード内で複数の更新されたレポートが使用できるようになります。"フラグ付きのユーザー" レポートでは、Google Play Protect の SafetyNet API スキャンにより検出されたユーザーが示されます。"潜在的に有害なアプリ" レポートでは、Google の Verify Apps API スキャンにより検出されたアプリが示されます。 この機能は Android で使用できます。

#### <a name="win32-app-information-available-in-troubleshooting-blade----2617342-----"></a>トラブルシューティング ブレードで利用可能な Win32 アプリ情報 <!-- 2617342   -->
Intune のアプリの**トラブルシューティング** ブレードから、Win32 アプリのインストールのエラー ログ ファイルを収集できるようになりました。 アプリのインストールに関するトラブルシューティングについて詳しくは、「[アプリのインストールに関する問題のトラブルシューティング](troubleshoot-app-install.md)」と「[Win32 アプリの問題をトラブルシューティングする](apps-win32-app-management.md#troubleshoot-win32-app-issues)」を参照してください。

#### <a name="app-status-details-for-ios-apps----3761235-----"></a>iOS アプリの状態の詳細 <!-- 3761235   -->
以下に関するアプリのインストールの新しいエラー メッセージが追加されています。
- 共有 iPad に VPP アプリをインストールするときのエラー
- アプリ ストアが無効になっているときのエラー
- アプリの VPP ライセンスが見つからない
- MDM プロバイダーでシステム アプリのインストールが失敗する
- デバイスが紛失モードまたはキオスク モードの場合に、アプリのインストールが失敗する
- ユーザーが App Store にサインインしていないときに、アプリのインストールが失敗する

Intune で、 **[クライアント アプリ]**  >  **[アプリ]** > "アプリ名" > **[デバイスのインストール状態]** の順に選択します。 **[状態の詳細]** 列で新しいエラー メッセージが使用できるようになります。

#### <a name="new-app-categories-screen-in-the-company-portal-app-for-windows-10---3834780----"></a>Windows 10 用ポータル サイト アプリでの新しい [アプリのカテゴリ] 画面<!-- 3834780  -->
**[アプリのカテゴリ]** という新しい画面が追加され、Windows 10 用ポータル サイトでのアプリの参照と選択のエクスペリエンスが向上しました。 ユーザーには、 **[おすすめ]** 、 **[教育]** 、 **[生産性]** などのカテゴリに並べ替えられたアプリが表示されるようになります。 この変更は、ポータル サイト バージョン 10.3.3451.0 以降で表示されます。 新しい画面を表示するには、「[アプリの UI の新機能](https://docs.microsoft.com/intune/whats-new-app-ui)」を参照してください。 ポータル サイトでのアプリの詳細については、「[デバイスにアプリをインストールして共有する](/intune-user-help/install-apps-cpapp-windows)」を参照してください。  

#### <a name="power-bi-compliance-app----1455231-doc-work-item---"></a>Power BI コンプライアンス アプリ <!-- 1455231 doc-work-item -->
[Intune コンプライアンス (データ ウェアハウス)](https://aka.ms/intune/datawarehouseapi/getpowerbiapp) アプリを使用して、Power BI Online 内の Intune データ ウェアハウスにアクセスします。 この Power BI アプリを使用すると、設定を行うことも、Web ブラウザーを離れることもなく、事前に作成されたレポートにアクセスし、共有することができます。 詳細については、[変更ログ - Power BI コンプライアンス アプリ](reports-changelog.md#power-bi-compliance-app)に関するページを参照してください。


### <a name="device-configuration"></a>デバイス構成

#### <a name="powershell-scripts-can-run-in-a-64-bit-host-on-64-bit-devices----1862675-----"></a>PowerShell スクリプトが 64 ビット デバイスの 64 ビット ホストで実行できる <!-- 1862675   -->
PowerShell スクリプトをデバイス構成プロファイルに追加すると、64 ビット オペレーティング システムであっても、スクリプトは常に 32 ビットで実行されます。 この更新により、管理者はスクリプトを実行 64 ビット デバイスの 64 ビット PowerShell ホストでスクリプトを実行できます ( **[デバイス構成]**  >  **[PowerShell スクリプト]**  >  **[追加]**  >  **[構成]**  >  **[Run script in 64 bit PowerShell Host]\(64 ビット PowerShell ホストでスクリプトを実行\)** )。

PowerShell の使用に関する詳細については、[Intune での PowerShell スクリプト](intune-management-extension.md)に関するページを参照してください。

適用対象:Windows 10 以降

#### <a name="macos-users-are-prompted-to-update-their-password----1873216---"></a>macOS ユーザーにパスワードの更新を求める <!-- 1873216 -->
Intune では、macOS デバイスに対して **ChangeAtNextAuth** 設定を強制しています。 この設定は、コンプライアンス パスワード ポリシーまたはデバイス制限パスワード プロファイルが設定されているエンドユーザーとデバイスに影響します。 エンド ユーザーはスワードの更新を 1 回求められます。 このプロンプトは、デバイスへのサインインなどの認証を必要とするタスクをユーザーが初めて実行するたびに発生します。 また、キーチェーン アクセスの要求など、管理者特権が必要なことをユーザーが行うときにも、パスワードの更新を求めることができます。 

管理者によって新規または既存のパスワード ポリシーが変更されると、エンドユーザーは再度パスワードの更新を求められます。

適用対象:  
macOS

#### <a name="assign-scep-certificates-to-a-userless-macos-device-----2340521----"></a>ユーザーレス macOS デバイスに SCEP 証明書を割り当てる  <!-- 2340521  -->
ユーザー アフィニティのないデバイスを含む macOS デバイスにデバイス属性を使用して Simple Certificate Enrollment Protocol (SCEP) 証明書を割り当て、その証明書プロファイルを Wi-Fi または VPN プロファイルに関連付けることができます。 これにより既にあるサポートを拡張して、Windows、iOS、Android を実行する[ユーザー アフィニティのあるデバイスまたはユーザー アフィニティのないデバイスに SCEP 証明書を割り当て](certificates-scep-configure.md#create-a-scep-certificate-profile)済みです。  この更新では、macOS の SCEP 証明書プロファイルを構成するときに、 *[デバイス]* という証明書の種類を選択するオプションが追加されています。

適用対象: 
- macOS

#### <a name="intune-conditional-access-ui-update------2432313-----"></a>Intune の条件付きアクセスの UI の更新   <!-- 2432313   -->
Intune コンソール内の条件付きアクセスの UI の改善を行いました。 たとえば、次のとおりです。
- Intune の "*条件付きアクセス*" ブレードを Azure Active Directory のブレードに置き換え。 これにより、Azure AD テクノロジのまま[条件付きアクセス](conditional-access.md)のすべての設定と構成に Intune コンソール内からアクセスできるようになります。 
- *[オンプレミス アクセス]* ブレードの名前を *[Exchange へのアクセス]* に変更し、 *[Exchange サービス コネクタ]* の設定をこの名前変更されたブレードに再配置しました。  この変更により、[Exchange Online とオンプレミスに関する詳細を構成および監視する](exchange-connector-install.md)場所が統合されました。  

#### <a name="kiosk-browser-and-microsoft-edge-browser-apps-can-run-on-windows-10-devices-in-kiosk-mode----2935135-----"></a>キオスク ブラウザーと Microsoft Edge ブラウザー アプリを、キオスク モードの Windows 10 デバイスで実行できる <!-- 2935135   -->
キオスク モードの Windows 10 デバイスを使用して、1 つまたは多数のアプリを実行することができます。 この更新プログラムには、キオスク モードでブラウザー アプリを使用するための次のような複数の変更が含まれています。

- Microsoft Edge ブラウザーまたはキオスク ブラウザーを追加して、キオスク デバイスでアプリとして実行します ( **[デバイス構成]**  >  **[プロファイル]**  >  **[新しいプロファイル]**  >  プラットフォームに **[Windows 10 以降]** を選択し、プロファイルの種類に **[キオスク]** を選択します)。
- 新しい機能や設定を使用して、以下のことを許可または制限できます ( **[デバイス構成]**  >  **[プロファイル]**  >  **[新しいプロファイル]**  >  プラットフォームに **[Windows 10 以降]** を選択し、プロファイルの種類に **[デバイスの制限]** を選択します)。

- Microsoft Edge ブラウザー:
  - Microsoft Edge キオスク モードを使用する
  - アイドル時間が経過した後、ブラウザーを更新する

- お気に入りおよび検索:
  - 検索エンジンへの変更を許可する

これらの設定の一覧については、次を参照してください。

- [Windows 10 以降のデバイスをキオスクとして実行するための設定](kiosk-settings-windows.md)
- [Microsoft Edge ブラウザー デバイスの制限](device-restrictions-windows-10.md#microsoft-edge-browser)
- [お気に入りと検索のデバイスの制限](device-restrictions-windows-10.md##favorites-and-search)

適用対象:Windows 10 以降

#### <a name="new-device-restriction-settings-for-ios-and-macos-devices----3448774-----"></a>iOS および macOS デバイスの新しいデバイス制限の設定 <!-- 3448774   -->
iOS および macOS を実行するデバイスで一部の設定と機能を制限することができます ( **[デバイス構成]**  >  **[プロファイル]**  >  **[新しいプロファイル]**  >  プラットフォームに **[iOS]** または **[macOS]** を選択し、プロファイルの種類に **[デバイスの制限]** を選択します)。 この更新プログラムにより、制御可能な機能と設定がさらに追加されます。これには、画面の表示時間の設定、eSIM 設定とセルラー プランの変更が含まれ、iOS デバイスではその他にもあります。 また、ユーザーへのソフトウェア更新プログラムの表示の遅延や、macOS デバイスでのコンテンツ キャッシュのブロックがあります。 

制限可能な機能と設定を確認するには、次を参照してください。

- [iOS デバイスの制限設定](device-restrictions-ios.md)
- [macOS デバイスの制限設定](device-restrictions-macos.md)

適用対象:

- iOS
- macOS

#### <a name="kiosk-devices-are-now-called-dedicated-devices-on-android-enterprise-devices----3598402-----"></a>Android エンタープライズ デバイスで "キオスク" デバイスが "専用デバイス" と呼ばれるようになった <!-- 3598402   -->
Android の用語に合わせるため、Android エンタープライズ デバイスの**キオスク**は、**専用デバイス**に変更されました ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]** プラットフォームに **[Android エンタープライズ]** を選択し、 **[デバイスの所有者のみ]**  >  **[デバイスの制限]**  >  **[専用デバイス]** を選択します)。

使用可能な設定を確認するには、[機能を許可または制限するデバイスの設定](device-restrictions-android-for-work.md#dedicated-device-settings)に関するページを参照してください。

適用対象:  
Android エンタープライズ

#### <a name="safari-and-delaying-user-software-update-visibility-ios-settings-are-moving-in-the-intune-ui----3640850-3803313-----"></a>Safari の設定と、iOS のソフトウェア更新プログラムのユーザーへの表示を遅らせる設定を Intune UI の中で移動 <!-- 3640850, 3803313   -->
iOS デバイスの場合、Safari を設定し、ソフトウェア更新プログラムを構成できます。 この更新プログラムでは、これらの設定が Intune UI のさまざまな部分に移動されています。

- Safari の設定は、 **[Safari]** ( **[デバイス構成]**  >  **[プロファイル]**  >  **[新しいプロファイル]**  > プラットフォームに **[iOS]** を選択し、プロファイルの種類に **[デバイスの制限]** を選択します) から **[[組み込みアプリ]](device-restrictions-ios.md#built-in-apps)** に移動されました。
- **[Delaying user software update visibility for supervised iOS devices]\(監視対象の iOS デバイスのソフトウェア更新プログラムのユーザーへの表示を遅らせる\)** 設定 ( **[ソフトウェア更新プログラム]**  >  **[iOS のポリシーを更新する]** ) は、 **[デバイスの制限]**  >  **[[全般]](device-restrictions-ios.md#general)** に移動されています。  既存のポリシーへの影響の詳細については、[iOS ソフトウェア更新プログラム](software-updates-ios.md#configure-the-policy)に関するページを参照してください。 

設定の一覧については、次を参照してください。

- [iOS デバイスの制限](device-restrictions-ios.md) 
- [iOS ソフトウェア更新プログラム](software-updates-ios.md)

この機能は、以下に適用されます。 

- iOS

#### <a name="enabling-restrictions-in-the-device-settings-is-renamed-to-screen-time-on-ios-devices----3699164-----"></a>iOS デバイスで、[デバイス設定での制限の有効化] 設定が [画面の表示時間] に名前が変更される <!-- 3699164   -->
監視対象の iOS デバイスで、 **[デバイス設定での制限の有効化]** を構成することができます ( **[デバイス構成]**  >  **[プロファイル]**  >  **[新しいプロファイル]**  >  プラットフォームに **[iOS]** を選択し、プロファイルの種類に **[デバイスの制限]** を選択し、 **[全般]** を選択します)。 この更新プログラムでは、この設定の名前が **[画面の表示時間 (監視モードのみ)]** に変更されています。 

動作は同じです。 具体的には次のとおりです。 

- iOS 11.4.1 以前のバージョン: **[ブロック]** は、エンド ユーザーがデバイス設定で独自の制限を設定できないようにします。 
- iOS 12.0 以降: **[ブロック]** は、エンド ユーザーがデバイス設定 (コンテンツとプライバシーの制限を含む) で独自の**画面の表示時間**を設定できないようにします。 iOS 12.0 にアップグレードされたデバイスでは、デバイスの設定に制限のタブが表示されなくなります。 これらの設定は **[画面の表示時間]** にあります。 

設定の一覧については、[iOS デバイスの制限事項](device-restrictions-ios.md#general)に関するページを参照してください。

適用対象: 
- iOS


### <a name="device-management"></a>デバイス管理

#### <a name="rename-an-enrolled-windows-device----1911112----"></a>登録済み Windows デバイスの名前変更 <!-- 1911112  -->
登録済み Windows 10 デバイス (RS4 以降) の名前を変更できるようになりました。 これを行うには、 **[Intune]**  >  **[デバイス]**  >  **[すべてのデバイス]** > デバイスを選択 > **[デバイス名の変更]** の順に選択します。 この機能では、ハイブリッド Azure AD Windows デバイスの名前変更は現在サポートされていません。

#### <a name="auto-assign-scope-tags-to-resources-created-by-an-admin-with-that-scope----3173823----"></a>自動割り当てスコープにより、そのスコープを使用して管理者によって作成されたリソースにタグが割り当てられる <!-- 3173823  -->
管理者がリソースを作成するときに、管理者に割り当てられた任意のスコープのタグが自動的にこれらの新しいリソースに割り当てられます。

### <a name="monitor-and-troubleshoot"></a>監視とトラブルシューティング

#### <a name="failed-enrollment-report-moves-to-the-device-enrollment-blade----3560202----"></a>失敗した登録レポートをデバイスの登録ブレードに移動 <!-- 3560202  -->
**失敗した登録**レポートは、**デバイスの登録**ブレードの **[監視]** セクションに移動されました。 2 つの新しい列 ([登録方法] と [OS のバージョン]) も追加されています。

#### <a name="company-portal-abandonment-report-renamed-to-incomplete-user-enrollments---3815076-eemiss---"></a>ポータル サイト破棄レポートの名前が不完全なユーザー登録に変更されました <!--3815076 eemiss -->
**ポータル サイト破棄**レポートの名前が**不完全なユーザー登録**に変更されました。


<!-- ########################## -->
## <a name="week-of-february-4-2019"></a>2019 年 2 月 4 日の週

### <a name="app-management"></a>アプリ管理

#### <a name="intune-macos-company-portal-dark-mode----3300524----"></a>Intune の macOS ポータル サイトのダーク モード <!-- 3300524  -->
Intune の macOS ポータル サイトで、macOS 用にダーク モードがサポートされるようになりました。 macOS 10.14 以降のデバイスでダーク モードを有効にすると、Intune ポータル サイトではそのモードの色に外観が調整されます。

<!-- ########################## -->
## <a name="week-of-january-21-2019"></a>2019 年 1 月 21 日の週

### <a name="app-management"></a>アプリ管理

#### <a name="toast-notifications-for-win32-apps----3136566-----"></a>Win32 アプリのトースト通知 <!-- 3136566   -->
アプリ割り当てごとに、エンド ユーザーにトースト通知が表示されるのを抑制することができます。 Intune で **[クライアント アプリ]**  >  **[アプリ]** > アプリを選択 > **[割り当て]**  >  **[グループを含める]** を選択します。 

#### <a name="intune-app-protection-policies-ui-update----3251427----"></a>Intune アプリ保護ポリシーの UI の更新 <!-- 3251427  -->
Intune のアプリ保護に関する設定とボタンのラベルを、理解しやすいように変更しました。 変更の一部を次に示します。  
- コントロールが、**はい** / **いいえ**から、主として**ブロック** / **許可**および**無効** / **有効**に変更されています。 ラベルも更新されています。  
- 設定は形式が変更されて、設定とそのラベルがコントロールに並べて配置されるようになり、ナビゲーションが容易になっています。   

既定の設定および多くの設定は同じままですが、この変更により、ユーザーは、これまでより簡単に設定を理解し、ナビゲートし、利用して、選択したアプリ保護ポリシーを適用できます。 詳細については、[iOS の設定](app-protection-policy-settings-ios.md)と [Android の設定](app-protection-policy-settings-android.md)に関する記事をご覧ください。

### <a name="additional-settings-for-outlook----3301182----"></a>Outlook の追加設定 <!-- 3301182  -->
Intune を使用して、Outlook for iOS と Outlook for Android の以下の追加設定を構成できるようになりました。

- 職場または学校のアカウントを iOS および Android の Outlook でのみ使用することを許可する
- Office 365 およびハイブリッド先進認証オンプレミス アカウントの先進認証をデプロイする
- 基本認証が選択されている場合に、メール プロファイルのユーザー名フィールドで `SAMAccountName` を使用する
- 連絡先の保存を許可する
- 外部受信者メール ヒントを構成する
- **優先受信トレイ**を構成する
- Outlook for iOS へのアクセスに生体認証を要求する
- 外部の画像をブロックする

> [!NOTE]
> Intune アプリ保護ポリシーを使用して企業 ID のアクセスを管理している場合は、**生体認証を要求する**オプションを有効にしないよう考慮する必要があります。 詳細については、[iOS のアクセス設定](app-protection-policy-settings-ios.md#access-requirements)および [Android のアクセス設定](app-protection-policy-settings-android.md#access-requirements)について、**アクセスのための企業認証情報の要求**に関する記事を参照してください。

詳細については、「[Microsoft Outlook の構成設定](app-configuration-policies-outlook.md)」を参照してください。

#### <a name="delete-android-enterprise-apps----1352553---"></a>Android エンタープライズ アプリを削除する <!-- 1352553 -->
Microsoft Intune から managed Google Play アプリを削除できます。 managed Google Play アプリを削除するには、Azure portal で Microsoft Intune を開き、 **[クライアント アプリ]**  >  **[アプリ]** の順に選択します。 アプリの一覧から、managed Google Play アプリの右側にある省略記号 (...) を選択し、表示された一覧で **[削除]** を選択します。 アプリの一覧からマネージド Google Play アプリを削除すると、そのマネージド Google Play アプリは自動的に未承認になります。

#### <a name="managed-google-play-app-type----1352580---"></a>managed Google Play アプリの種類 <!-- 1352580 -->
**マネージド Google Play** アプリの種類では、特定の[マネージド Google Play アプリ](https://play.google.com/work/search?q=microsoft&c=apps)を Intune に追加できます。 Intune の管理者は、Intune 内で managed Google Play アプリを参照、検索、承認、同期および割り当てできるようになりました。  managed Google Play コンソールに別途移動する必要はなく、また再認証する必要もありません。  Intune で、 **[クライアント アプリ]**  >  **[アプリ]**  >  **[追加]** を選択します。 **[アプリケーションの種類]** 一覧で、アプリの種類として **[マネージド Google Play]** を選択します。

### <a name="default-android-pin-keyboard----3802457---"></a>既定の Android PIN キーボード <!-- 3802457 -->
Android デバイスで PIN タイプが "数値" の Intune アプリ保護ポリシー (APP) PIN を設定しているエンド ユーザーの場合、以前の設計のような固定の Android キーボード UI ではなく、既定の Android キーボードが表示されるようになります。 この変更は、"数値" と "パスコード" 両方の PIN タイプについて、既定のキーボードを使用するときの動作が Android と iOS の両方で同じになるようにするために行われました。 Android での APP PIN などのエンド ユーザー アクセス設定について詳しくは、[Android のアクセス要件](app-protection-policy-settings-android.md#access-requirements)に関する記事をご覧ください。

### <a name="device-configuration"></a>デバイス構成

#### <a name="use-microsoft-recommended-settings-with-security-baselines-public-preview----2055484-----"></a>セキュリティ ベースラインを使って Microsoft 推奨の設定を使う (パブリック プレビュー) <!-- 2055484   -->

Intune は、セキュリティに的を絞ったその他のサービス (Windows Defender ATP や Office 365 ATP など) と統合されます。 一般的な戦略と、Microsoft 365 サービス間での結束的なエンドツーエンドのセキュリティ ワークフローをお客様から求められています。 目標としているのは、セキュリティの運用と一般的な管理者タスクをブリッジするソリューションを構築できるように戦略を調整することにあります。 Intune では、Microsoft が推奨する一連の "セキュリティ ベースライン" を公開することによって、この目標の達成を目指しています ( **[Intune]**  > **セキュリティ ベースライン**)。  管理者はこれらのベースラインから直接セキュリティ ポリシーを作成し、それを各自のユーザーにデプロイできます。 また、ご自分の組織のニーズに合わせてベスト プラクティスのレコメンデーションをカスタマイズすることもできます。 Intune では、これらのベースラインにデバイスが準拠した状態に維持されていることが確認され、管理者には準拠した状態にないユーザーまたはデバイスが通知されます。

この機能はパブリック プレビューなので、現在作成されているプロファイルは、一般提供 (GA) されるセキュリティ ベースラインのテンプレートには引き継がれません。 運用環境でこれらのプレビュー テンプレートを使用することは計画しないでください。

セキュリティ ベースラインについて詳しくは、[Intune での Windows 10 セキュリティ ベースラインの作成](security-baselines-monitor.md)に関する記事をご覧ください。

この機能は、以下に適用されます。Windows 10 以降

#### <a name="non-administrators-can-enable-bitlocker-on-windows-10-devices-joined-to-azure-ad---2147379-----"></a>管理者以外のユーザーが、Azure AD 参加済み Windows 10 デバイスで BitLocker を有効にできる<!-- 2147379   -->
Windows 10 デバイスで BitLocker の設定を有効にすると ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  > プラットフォームとして **[Windows 10 以降] を選択** > プロファイルの種類として **[Endpoint Protection]** > **[Windows 暗号化]** )、BitLocker の設定が追加されます。 

この更新には、標準ユーザー (管理者以外) が暗号化を有効にするのを許可する新しい BitLocker の設定が含まれます。 

設定を確認するには、[Windows 10 用の Endpoint Protection 設定](endpoint-protection-windows-10.md#windows-encryption)に関する記事を参照してください。

#### <a name="check-for-configuration-manager-compliance----2192052--eepublished----"></a>Configuration Manager コンプライアンスの確認 <!-- 2192052  eepublished  -->
この更新には、新しい System Center Configuration Manager コンプライアンス設定 ( **[デバイスのポリシー準拠]**  >  **[ポリシー]**  >  **[ポリシーの作成]**  >  **[Windows 10 以降]**  >  **[Configuration Manager のコンプライアンス]** ) が含まれます。 Configuration Manager から Intune コンプライアンスにシグナルが送信されます。 この設定を使用して、すべての Configuration Manager シグナルで "準拠" を返すように要求することができます。

たとえば、すべてのソフトウェア更新プログラムをデバイスにインストールすることを要求します。 Configuration Manager では、この要求は "インストール済み" 状態となります。 デバイス上のいずれかのプログラムが不明な状態である場合、Intune ではデバイスが非準拠となります。

この設定については、「[Configuration Manager Compliance (Configuration Manager コンプライアンス)](compliance-policy-create-windows.md#configuration-manager-compliance)」で説明されています。

適用対象:Windows 10 以降

#### <a name="customize-wallpaper-on-supervised-ios-devices-using-a-device-configuration-profile----2809324-----"></a>デバイスの構成プロファイルを使用した監視対象の iOS デバイスの壁紙のカスタマイズ <!-- 2809324   -->
iOS デバイス用のデバイス構成プロファイルを作成するときに、一部の機能をカスタマイズできます ( **[デバイスの構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  >  プラットフォーム用の **iOS** > プロファイルの種類用の **[デバイス機能]** )。 この更新には新しい **[壁紙]** 設定が含まれています。これを使うと、管理者はホーム画面またはロック画面上で .png、.jpg、または .jpeg 画像を使うことができます。 これらの壁紙の設定は、監視対象のデバイスにのみ適用できます。 

これらの設定の一覧については、[iOS デバイスの機能設定](ios-device-features-settings.md)に関する記事をご覧ください。

#### <a name="windows-10-kiosk-is-generally-available----3594661----"></a>Windows 10 キオスクの一般提供 <!-- 3594661  -->
この更新では、Windows 10 以降のデバイスでのキオスク機能が一般提供 (GA) になりました。 追加および構成できるすべての設定については、[Windows 10 (およびそれ以降) のキオスク設定](kiosk-settings.md)に関する記事をご覧ください。

#### <a name="contact-sharing-via-bluetooth-is-removed-in-device-restrictions--device-owner-for-android-enterprise----3598396-----"></a>Android エンタープライズの [デバイスの制限] > [デバイスの所有者] での [Bluetooth 経由での連絡先の共有] の削除 <!-- 3598396   -->
Android エンタープライズ デバイス用にデバイスの制限プロファイルを作成した場合、 **[Bluetooth 経由での連絡先の共有 ]** 設定があります。 この更新では、 **[Bluetooth 経由での連絡先の共有]** の設定が削除されます ( **[デバイスの構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  >  プラットフォーム用の **Android エンタープライズ** > **[デバイスの制限] > プロファイルの種類の [デバイスの所有者]** > **[全般]** )。 

**[Bluetooth 経由での連絡先の共有]** 設定は、Android エンタープライズのデバイス所有者の管理ではサポートされていません。 したがって、この設定が削除されると、この設定が環境で有効および構成されていた場合でもいかなるデバイスやテナントにも影響はありません。

現在の設定一覧を確認するには、[Android エンタープライズ デバイスの機能を許可または制限する設定](device-restrictions-android-for-work.md)に関するページを参照してください。

適用対象:Android エンタープライズ デバイスの所有者

### <a name="device-management"></a>デバイス管理

#### <a name="selective-wipe-support-for-wip-without-enrollment-devices----1434452---"></a>登録なしの WIP デバイスに対する選択的ワイプのサポート <!-- 1434452 -->
登録なしの Windows Information Protection (WIP-WE) を使うと、MDM への完全な登録を必要とせずに Windows 10 デバイス上の企業データを保護することができます。 WIP-WE ポリシーを使用してドキュメントが保護されると、Intune 管理者は保護されたデータを選択的にワイプすることができます。 ユーザーとデバイスを選択してワイプ要求を送信することにより、WIP-WE ポリシーを介して保護されたデータはすべて使用できなくなります。 Azure portal 内で Intune から、 **[モバイル アプリ]**  >  **[アプリの選択的ワイプ]** の順に選択します。

### <a name="monitor-and-troubleshoot"></a>監視とトラブルシューティング

#### <a name="new-operational-logs-and-ability-to-send-logs-to-azure-monitor-services----3762211----"></a>新しい操作ログ、およびログを Azure Monitor サービスに送信する機能 <!-- 3762211  -->
Intune には、変更が加えられるとイベントを追跡する組み込みの監査ログが備わっています。 この更新には、次の新しいログ記録機能が含まれます。 
- 登録したユーザーおよびデバイスの詳細を示す操作ログ (プレビュー) (成功および失敗した試行を含む)。
- 監査ログと操作ログは Azure Monitor に送信することができます (ストレージ アカウント、イベント ハブ、ログ分析を含む)。 これらのサービスを使うと、保存したり、Splunk や QRadar などの分析を使ったり、ログ データの視覚化を取得したりできます。

この機能について詳しくは、[Intune でのストレージ、イベント ハブ、またはログ分析へのログ データの送信](review-logs-using-azure-monitor.md)に関する記事をご覧ください。

### <a name="skip-more-setup-assistant-screens-on-an-ios-dep-device----2687509----"></a>iOS DEP デバイスでスキップできるセットアップ アシスタントの画面が増える <!-- 2687509  -->
現在スキップすることができる画面に加えて、ユーザーがデバイスを登録するときにセットアップ アシスタント内で次の画面をスキップするように iOS DEP デバイスを設定できます: [ディスプレイの色調]、[プライバシー]、[Android 移行]、[ホーム ボタン]、[iMessage & FaceTime]、[オンボード]、[Watch の移行]、[外観]、[画面の表示時間]、[ソフトウェア更新プログラム]、[SIM のセットアップ]。
スキップする画面を選択するには、 **[デバイスの登録]**  >  **[Apple の登録]**  >  **[Enrollment Program トークン]** に移動し、トークンを選択します。次に、 **[プロファイル]** を選択してプロファイルを選択し、 **[プロパティ]**  >  **[セットアップ アシスタントのカスタマイズ]** を選択し、スキップする画面の **[非表示]** を選択して、 **[OK]** を選択します。
新しいプロファイルを作成するかプロファイルを編集する場合は、選択したスキップする画面が Apple MDM サーバーと同期している必要があります。 ユーザーは、プロファイルの変更を取得するときに遅延が発生しないように、手動でのデバイスの同期を発行できます。

#### <a name="android-enterprise-app-we-app-deployment----1171203---"></a>Android エンタープライズ APP-WE アプリの展開 <!-- 1171203 -->
登録のないアプリ保護ポリシー (APP-WE) の展開シナリオでの Android デバイスでは、マネージド Google Play を使用してストア アプリと LOB アプリをユーザーに展開できるようになりました。 具体的には、不明なソースからのインストールを許可することによってデバイスのセキュリティ状態を損なう必要がないアプリ カタログとインストール エクスペリエンスをエンド ユーザーに提供できます。 さらに、この展開シナリオでは、向上したエンド ユーザー エクスペリエンスが提供されます。

<!-- ########################## -->
## <a name="week-of-january-14-2019"></a>2019 年 1 月 14 日の週

### <a name="preview-of-support-for-android-corporate-owned-fully-managed-devices----1574342----"></a>会社が所有する完全に管理された Android デバイスのサポートのプレビュー <!-- 1574342  -->
Intune では、フル マネージドの Android デバイス、つまりデバイスが IT によって厳格に管理され、個々のユーザーと関連付けられる、企業所有の "デバイス所有者" のシナリオがサポートされるようになりました。 これにより、管理者は、デバイス全体を管理し、仕事用プロファイルでは利用できない拡張範囲のポリシー制御を適用し、managed Google Play からのみアプリをインストールするようにユーザーを制限することができます。 詳細については、[Android フル マネージド デバイスの Intune 登録の設定](android-fully-managed-enroll.md)および[専用デバイスまたはフル マネージド デバイスの登録](android-dedicated-devices-fully-managed-enroll.md)に関するページをご覧ください。  なお、この機能はプレビュー段階です。 証明書、コンプライアンス、および条件付きのアクセスなど、一部の Intune 機能は、現在 Android の完全に管理されたユーザー デバイスでは利用できません。

<!-- ########################## -->
## <a name="week-of-january-7-2019"></a>2019 年 1 月 7 日の週

### <a name="app-management"></a>アプリ管理

#### <a name="intune-app-pin----2298397---"></a>Intune アプリの PIN <!-- 2298397 -->
IT 管理者は、エンド ユーザーによる Intune アプリ PIN の変更が必要になるまでの待機日数を構成できるようになりました。 新しい設定では、*その日数後に PIN がリセットされます*。この設定を使用するには、Azure portal で **[Intune]**  >  **[クライアント アプリ]**  >  **[アプリ保護ポリシー]**  >  **[ポリシーの作成]**  >  **[設定]**  >  **[アクセス要件]** の順に選択します。 この機能は、[iOS](app-protection-policy-settings-ios.md) デバイスと [Android](app-protection-policy-settings-android.md) デバイスで使用でき、正の整数値をサポートしています。


#### <a name="intune-device-reporting-fields----2748738---"></a>Intune のデバイス レポートのフィールド <!-- 2748738 -->
Intune では、アプリ登録 ID、Android の製造元、モデル、セキュリティ更新プログラムのバージョン、iOS のモデルなど、デバイス レポートのフィールドが提供されています。 Intune でこれらのフィールドを使用するには、 **[クライアント アプリ]**  >  **[アプリの保護状態]** を選択して、 **[アプリ保護レポート: iOS、Android]** を選択します。 さらに、これらのパラメーターは、デバイス製造元 (Android) の**許可**リスト、デバイス モデル (Android および iOS) の**許可**リスト、および Android セキュリティ修正プログラムの最小バージョンの設定を構成するのに役立ちます。 


### <a name="device-configuration"></a>デバイス構成

#### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>管理用テンプレートがパブリック プレビューになり、専用の構成プロファイルに移動される <!-- 3322847 -->

Intune の管理用テンプレート ( **[デバイス構成]**  >  **[管理用テンプレート]** ) は現在、パブリック プレビュー段階です。 この更新プログラムでは:

- 管理用テンプレートには、Intune で管理可能な約 300 の設定が含まれます。 以前は、これらの設定はグループ ポリシー エディターにのみ存在しました。
- 管理用テンプレートはパブリック プレビューで使用できます。
- 管理用テンプレートは、 **[デバイス構成]**  >  **[管理用テンプレート]** から、 **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]** を選択し、 **[プラットフォーム]** で **[Windows 10 以降]** を選択し、 **[プロファイルの種類]** で **[管理用テンプレート]** を選択した場所に移動されています。
- レポートが有効です。

この機能の詳細については、[グループ ポリシー設定を構成するための Windows 10 テンプレート](administrative-templates-windows.md)に関するページを参照してください。

適用対象:Windows 10 以降

#### <a name="use-smime-to-encrypt-and-sign-multiple-devices-for-a-user-----1333642---"></a>S/MIME を使って暗号化し、ユーザーの複数のデバイスに署名する  <!-- 1333642 -->
この更新プログラムには、新しくインポートされる証明書プロファイル ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]** 、該当するプラットフォーム、 **[PKCS のインポートされた証明書]** プロファイルの種類の順に選択) を使用する S/MIME メールの暗号化が含まれます。 Intune では、PFX 形式で証明書をインポートできます。 その後、Intune はその同じ証明書を、単一ユーザーによって登録された複数のデバイスに配信できます。 これには、次のものも含まれます。
- ネイティブ iOS メール プロファイルでは、PFX 形式でインポートされた証明書を使用する S/MIME 暗号化を有効にすることができます。
- Windows Phone 10 デバイス上のネイティブ メール アプリでは、自動的に S/MIME 証明書が使用されます。
- プライベート証明書は複数のプラットフォームに配信できます。 しかし、すべてのメール アプリで S/MIME がサポートされるわけではありません。
- 他のプラットフォームでは、S/MIME を有効にするようにメール アプリを手動で構成する必要がある場合があります。  
- S/MIME 暗号化をサポートするメール アプリでは、発行元の証明書ストアからの読み取りなど、MDM ではサポートできない方法で S/MIME メール暗号化のための証明書の検索を処理する場合があります。
この機能の詳細については、[電子メールの署名と暗号化のための S/MIME の概要](certificates-s-mime-encryption-sign.md)に関するページを参照してください。
サポート対象:Windows、Windows Phone 10、macOS、iOS、Android

#### <a name="new-options-to-automatically-connect-and-persist-rules-when-using-dns-settings-on-windows-10-and-later-devices----1333665-2999078---"></a>Windows 10 以降のデバイスで DNS 設定を使用するときに、自動的に接続してルールを保持する新しいオプション <!-- 1333665, 2999078 -->
Windows 10 以降のデバイスでは、contoso.com などのドメインを解決するための DNS サーバーのリストを含む VPN 構成プロファイルを作成できます。 この更新には、名前解決のための新しい設定が含まれます ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]** > プラットフォームとして **[Windows 10 以降]** を選択 > プロファイルの種類として **[VPN]** を選択 > **[DNS 設定]**  > **[追加]** )。 
- **自動接続**: **有効**にすると、デバイスは、入力された contoso.com などのドメインにアクセスするときに、VPN に自動的に接続します。
- **永続性**: この VPN プロファイルを使用してデバイスに接続している限り、既定で、名前解決ポリシー テーブル (NRPT) のすべてのルールがアクティブになります。 NRPT ルールでこの設定を**有効**にすると、VPN が切断されても、ルールはデバイス上でアクティブなままになります。 VPN プロファイルを削除するか、ルールを手動で削除するまで (PowerShell を使って実行できます)、ルールは保持されます。
[Windows 10 の VPN 設定](vpn-settings-windows-10.md)に関するページでは、これらの設定について説明されています。 

#### <a name="use-trusted-network-detection-for-vpn-profiles-on-windows-10-devices----1500165---"></a>Windows 10 デバイスで VPN プロファイルに対して信頼されたネットワーク検出を使用する <!-- 1500165 -->
信頼されたネットワーク検出を使用すると、ユーザーが信頼されたネットワーク上に既にいるときに、VPN プロファイルで VPN 接続が自動的に作成されるのを防ぐことができます。 この更新により、Windows 10 以降を実行するデバイスでは、DNS サフィックスを追加して信頼されたネットワーク検出を有効にすることができます ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  > プラットフォームとして **[Windows 10 以降]** > プロファイルの種類として **[VPN]** )。
[Windows 10 の VPN 設定](vpn-settings-windows-10.md)に関するページには、現在の VPN 設定の一覧があります。

#### <a name="manage-windows-holographic-for-business-devices-used-by-multiple-users----1907917-1063203---"></a>複数のユーザーによって使用される Windows Holographic for Business デバイスを管理する <!-- 1907917, 1063203 -->
現在、共有 PC の設定は、Windows 10 デバイスと Windows Holographic for Business デバイスでカスタム OMA-URI の設定を使用して構成できます。 この更新により、共有デバイスの設定を構成するための新しいプロファイルが追加されます ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  >  **[Windows 10 以降]**  >  **[共有のマルチユーザーのデバイス]** )。
この機能の詳細については、[共有デバイスを管理するための Intune の設定](shared-user-device-settings.md)に関するページを参照してください。
適用対象:Windows 10 以降、Windows Holographic for Business

#### <a name="new-windows-10-update-settings---2626030--2512994----"></a>新しい Windows 10 更新プログラムの設定 <!--2626030  2512994  -->
[Windows 10 更新リング](windows-update-for-business-configure.md)で、次の構成を行うことができます。
- **[自動更新の動作]** - 新しいオプション *[既定にリセット]* を使用して、"*2018 年 10 月更新*" を実行している Windows 10 コンピューターで、元の自動更新設定を復元する。
- **[ユーザーによる Windows Update の一時停止をブロックする]** - コンピューターの "*設定*" から、ユーザーによる更新プログラムのインストールの一時停止を許可またはブロックできる、新しいソフトウェア更新プログラムの設定を構成する。 

#### <a name="ios-email-profiles-can-use-smime-signing-and-encryption----2662949---"></a>iOS の電子メール プロファイルで S/MIME の署名と暗号化を使用できる <!-- 2662949 -->
異なる設定を含む電子メール プロファイルを作成することができます。 この更新には、iOS デバイスでのメール通信の署名と暗号化に使用できる S/MIME の設定が含まれます ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]** > プラットフォームとして **[iOS]** を選択 > プロファイルの種類として **[電子メール]** を選択)。
[iOS での電子メール構成の設定](email-settings-ios.md)に関するページに、設定の一覧が示されています。

#### <a name="some-bitlocker-settings-support-windows-10-pro-edition---2727036---"></a>BitLocker の一部の設定で Windows 10 Pro エディションがサポートされる<!-- 2727036 -->
Windows 10 デバイスで、BitLocker などの Endpoint Protection の設定を行う構成プロファイルを作成できます。 この更新により、BitLocker の一部の設定に Windows 10 Professional エディションのサポートが追加されます。 これらの保護設定を確認するには、[Windows 10 用の Endpoint Protection 設定](endpoint-protection-windows-10.md#windows-encryption)に関するページを参照してください。

#### <a name="shared-device-configuration-is-renamed-to-lock-screen-message-for-ios-devices-in-the-azure-portal---2809362---"></a>Azure portal で iOS デバイスの共有デバイスの構成が、ロック画面メッセージに名前を変更される<!-- 2809362 -->
iOS デバイス用の構成プロファイルを作成するときに、ロック画面に特定のテキストを表示する**共有デバイス構成**の設定を追加できます。 この更新には、次の変更が含まれます。 
- Azure portal で **[共有デバイスの構成]** 設定の名前が、[Lock Screen Message (supervised only)]\(ロック画面のメッセージ (監視モードのみ)\) に変更されます ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]** > プラットフォームとして **[iOS]** を選択 > プロファイルの種類として **[デバイス機能]** を選択 > **[Lock Screen Message]\(ロック画面のメッセージ\)** )。
- ロック画面のメッセージを追加するときは、 **[資産タグ情報]** および **[ロック画面の脚注 ]** の変数として、シリアル番号、デバイス名、または別のデバイス固有値を挿入できます。 たとえば、中かっこを使用して `Device name: {{devicename}}` や `Serial number is {{serialnumber}}` などと入力できます。 [iOS トークン](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list)に関するページでは、使用できるトークンの一覧が示されています。
[ロック画面にメッセージを表示するための設定](shared-device-settings-ios.md)に関するページでは、設定の一覧が示されています。

#### <a name="new-app-store-doc-viewing-gaming-device-restriction-settings-added-to-ios-devices----2827760--"></a>iOS デバイスに App Store、ドキュメント表示、ゲーム デバイスの新しい制限の設定が追加される <!-- 2827760-->
**[デバイスの構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  >  プラットフォームとして **[iOS]** を選択 > プロファイルの種類として **[デバイスの制限]** を選択 > **[アプリ ストア、ドキュメント表示、ゲーム]** の順に選択すると、次の設定が追加されます。[Allow managed apps to write contacts to unmanaged contacts accounts]\(マネージド アプリによるアンマネージド連絡先アカウントへの連絡先の書き込みを許可する\)、[Allow unmanaged apps to read from managed contacts accounts]\(アンマネージド アプリによるマネージド連絡先アカウントからの読み取りを許可する\)。これらの設定については、[iOS デバイスの制限](device-restrictions-ios.md#app-store-doc-viewing-gaming)に関するページをご覧ください。

#### <a name="new-notification-hints-and-keyguard-settings-to-android-enterprise-device-owner-devices----3201839-3201843---"></a>Android エンタープライズ デバイス所有者デバイスに対する新しい通知、ヒント、キーガードの設定 <!-- 3201839 3201843 -->
この更新には、デバイス所有者として実行するときの Android エンタープライズ デバイスに関するいくつかの新機能が含まれます。 これらの機能を使用するには、 **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]** に移動し、 **[プラットフォーム]** で **[Android エンタープライズ]** を選択し、 **[プロファイルの種類]** で **[デバイスの所有者のみ]**  >  **[デバイスの制限]** を選択します。

新機能は次のとおりです。 

- 着信、システム アラート、システム エラーなどのシステム通知の表示を無効にします。
- 初めて開いたアプリのチュートリアルとヒントの開始をスキップすることを提案します。
- カメラ、通知、指紋によるロック解除など、高度なキーガード設定を無効にします。


これらの設定については、[Android エンタープライズ デバイスの制限の設定](device-restrictions-android-for-work.md)に関するページを参照してください。

#### <a name="android-enterprise-device-owner-devices-can-use-always-on-vpn-connections----3202194---"></a>Android エンタープライズ デバイス所有者デバイスで、Always On VPN 接続を使用できる <!-- 3202194 -->
この更新では、Android エンタープライズ デバイス所有者デバイスで常時 VPN 接続を使用できます。 常時 VPN 接続では接続状態が常に維持されるか、ユーザーが自分のデバイスをロックしたとき、デバイスが再起動したとき、ワイヤレス ネットワークに変更があったとき、すぐに再接続されます。 接続を "ロックダウン" モードにすることもできます。このモードでは、VPN 接続が有効になるまですべてのネットワーク トラフィックがブロックされます。
**[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]** の順に選択し、プラットフォームとして **[Android エンタープライズ]** を選択し、[デバイスの所有者のみ] として **[デバイスの制限]** を選択し、 **[接続]** 設定を選択することで、常時 VPN を有効にできます。 これらの設定については、[Android エンタープライズ デバイスの制限の設定](device-restrictions-android-for-work.md)に関するページを参照してください。

#### <a name="new-setting-to-end-processes-in-task-manager-on-windows-10-devices----3285177---"></a>Windows 10 デバイスのタスク マネージャーでプロセスを終了するための新しい設定 <!-- 3285177 --> 
この更新には、Windows 10 デバイスのタスク マネージャーでプロセスを終了するための新しい設定が含まれます。 デバイス構成プロファイルを使用して ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]** > **[プラットフォーム]** で **[Windows 10]** を選択 > **[プロファイルの種類]** で **[デバイスの制限]** を選択 >  **[全般]** 設定)、この設定の許可または禁止を選択します。
これらの設定については、[Windows 10 デバイスの制限の設定](device-restrictions-windows-10.md)に関するページを参照してください。
適用対象:Windows 10 以降


### <a name="device-enrollment"></a>デバイスの登録

#### <a name="more-detailed-enrollment-restriction-failure-messaging----3111564---"></a>より詳細な登録制限のエラー メッセージ <!-- 3111564 -->
登録の制限が満たされていないときに表示されるエラー メッセージが、より詳細になります。 これらのメッセージを見るには、 **[Intune]**  >  **[トラブルシューティング]** に移動し、[登録エラー] のテーブルを確認します。 詳細については、[登録エラーの一覧](help-desk-operators.md#enrollment-failure-reference)を参照してください。

### <a name="monitor-and-troubleshoot"></a>監視とトラブルシューティング

#### <a name="tenant-status-dashboard-----1124854---"></a>テナントの状態ダッシュボード  <!-- 1124854 -->
新しい [[テナントの状態] ページ](tenant-status.md)では、テナントの状態および関連する詳細を 1 か所に表示できます。  このダッシュボードは、次の 4 つの領域に分かれています。
- **テナントの詳細** - テナントの名前と場所、ご利用の MDM 機関、ご利用のテナントに登録されたデバイスの総数、ご利用のライセンス数などの情報が表示されます。 このセクションには、そのテナントに対する現在のサービス リリースも示されます。
- **コネクタの状態** - 構成済みの使用可能なコネクタに関する情報が表示されるほか、まだ有効にしていないコネクタの一覧も表示できます。  
   各コネクタの現在の状態に基づいて、正常、警告、または異常を示すフラグが付けられます。 コネクタを選択してドリルスルーし、詳細を表示したり、追加情報を構成したりします。
- **Intune サービスの正常性** - ご利用のテナントでのアクティブなインシデントまたは障害に関する詳細が表示されます。 このセクション内の情報は、Office メッセージ センターから直接取得されます。
- **Intune ニュース** - テナントのアクティブなメッセージが表示されます。 メッセージには、テナントが Intune の最新の機能を受信する際の通知などが含まれます。  このセクション内の情報は、Office メッセージ センターから直接取得されます。

#### <a name="new-help-and-support-experience-in-company-portal-for-windows-10----1488939--"></a>Windows 10 用ポータル サイトの新しいヘルプとサポート エクスペリエンス <!-- 1488939-->
ポータル サイトの新しい [ヘルプとサポート] ページでは、ユーザーがアプリやアクセスの問題に対して、トラブルシューティングを行ったりヘルプを要求したりできます。 この新しいページで、エラーと診断ログの詳細を電子メールで送信し、組織のヘルプデスクの詳細を確認することができます。 また、関連する Intune ドキュメントへのリンクを含む FAQ セクションもあります。 

#### <a name="new-help-and-support-experience-for-intune------3307080---"></a>Intune の新しいヘルプとサポート エクスペリエンス   <!-- #3307080 -->
今後数日間で、新しいヘルプとサポート エクスペリエンスをすべてのテナントにロールアウトする予定です。 この新しいエクスペリエンスは Intune で利用でき、[Azure portal](https://portal.azure.com/) で Intune のブレードを使用しているときにアクセスできます。
新しいエクスペリエンスでは、自分の言葉で問題を説明し、トラブルシューティングの分析情報と Web ベースの修復コンテンツを受け取ることができます。 これらの解決策は、ユーザーの照会により、ルール ベースの機械学習アルゴリズムを使用して提供されます。 問題固有のガイダンスに加えて、新しいケース作成ワークフローを使用して、電子メールまたは電話でサポート ケースを開きます。 ヘルプとサポートを開いたコンソールの領域に基づいて事前選択されているオプションの静的セットである以前のヘルプとサポート エクスペリエンスが、この新しいエクスペリエンスに置き換えられます。 詳細については、「[Microsoft Intune のサポートを受ける方法](get-support.md)」を参照してください。

### <a name="role-based-access-control"></a>ロールベースのアクセス制御

#### <a name="scope-tags-for-apps----1081941---"></a>アプリのスコープ タグ <!-- 1081941 -->
ロールとアプリへのアクセスを制限するために、スコープのタグを作成できます。 アプリにスコープのタグを追加すると、ロールを持つユーザーのうち、そのスコープのタグも割り当てられているユーザーだけがアプリにアクセスできるようになります。 現在、managed Google Play から Intune に追加されたアプリや、Apple Volume Purchase Program (VPP) を使って購入されたアプリにスコープ タグを割り当てることはできません (今後のサポートが予定されています)。 詳細については、「[スコープのタグを使用してポリシーをフィルター処理する](scope-tags.md)」を参照してください。

## <a name="notices"></a>通知

[!INCLUDE [Intune notices](./includes/intune-notices.md)]
