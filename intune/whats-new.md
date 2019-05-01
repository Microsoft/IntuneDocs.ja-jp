---
title: Microsoft Intune の新機能 - Azure | Microsoft Docs
titleSuffix: ''
description: Intune Azure Portal の新機能を確認する
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/22/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6dff7e28daff503570350950b60ae974cd048c5c
ms.sourcegitcommit: 6d6f43d69462f7f8fadc421c4ba566dc6ec20c36
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62426232"
---
# <a name="whats-new-in-microsoft-intune"></a>Microsoft Intune の新機能

週ごとにまとめた、Microsoft Intune の新機能をご覧ください。 [今後の変更](in-development.md)、[重要なお知らせ](#notices)、[過去のリリース](whats-new-archive.md)に関する情報も確認できます。 

> [!Note]
> いくつかの機能については、数週間にわたってロールアウトされ、一部のお客様は最初の週にご利用になれない可能性があります。

**RSS フィード**:ご自身のフィード リーダーに次の URL をコピーして貼り付けることで、このページの更新時に通知を受け取ることができます。`https://docs.microsoft.com/api/search/rss?search=%22What%27s+new+in+microsoft+intune%3F+-+Azure%22&locale=en-us`

<!-- Common categories:  
### App management
### Device configuration
### Device enrollment
### Device management
### Intune apps
### Monitor and troubleshoot
### Role-based access control

-->  

<!-- ########################## -->

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
管理者は、Win32 アプリのインストール前に他のアプリが依存関係としてインストールされていることを要求できます。 つまり、デバイスで Win32 アプリをインストールする前に、依存するアプリをインストールする必要があります。 Intune で、**[クライアント アプリ]** > **[アプリ]** > **[追加]** を選択して **[アプリの追加]** ブレードを表示します。 **[アプリの種類]** として **[Windows アプリ (Win32)]** を選択します。 アプリを追加した後、**[依存関係]** を選択し、Win32 アプリをインストールする前にインストールする必要がある依存するアプリを追加できます。 詳細については、「[Intune スタンドアロン - Win32 アプリ管理](apps-win32-app-management.md)」を参照してください。 この機能は、Intune 管理エージェントが 1904 バージョン (1.18.120.0 以降) にアップグレードされた後にのみ利用でき、それにはサービスの 1904 へのアップグレード後、さらに 1 週間または 2 週間かかる場合があります。

#### <a name="app-version-installation-information-for-microsoft-store-for-business-apps----3537391-----"></a>ビジネス向け Microsoft Store のアプリに関する、アプリのバージョンのインストール情報 <!-- 3537391   -->
アプリ インストール レポートには、ビジネス向け Microsoft Store のアプリのバージョン情報が含まれます。 Intune で、**[クライアント アプリ]** > **[アプリ]** を選択します。 **[ビジネス向け Microsoft Store アプリ]** を選択し、次に **[モニター]** セクションの **[デバイスのインストール状態]** を選択します。

#### <a name="additions-to-win32-apps-requirement-rules----3676883-----"></a>Win32 アプリ要件規則への追加 <!-- 3676883   -->
PowerShell スクリプト、レジストリ値、ファイル システム情報に基づく要件規則を作成できます。 Intune で、**[クライアント アプリ]** > **[アプリ]** > **[追加]** を選択します。 次に、**[アプリの追加]** ブレードで **[アプリの種類]** として **[Windows アプリ (Win32)]** を選択します。  **[要件]** > **[追加]** を選択して追加の要件規則を構成します。 次に、**[ファイルの種類]**、**[レジストリ]**、**[スクリプト]** のいずれかを **[要件の種類]** として選択します。 詳細については、[Win32 アプリ管理](apps-win32-app-management.md)に関するページを参照してください。

 #### <a name="configure-your-win32-apps-to-be-installed-on-intune-enrolled-azure-ad-joined-devices----3695227----"></a>Intune に登録された Azure AD 参加済みデバイスにインストールされるように Win32 アプリを構成する <!-- 3695227  -->
Intune に登録された Azure AD 参加済みデバイスにインストールされるように Win32 アプリを割り当てることができます。 Intune での Win32 アプリの詳細については、[Win32 アプリ管理](apps-win32-app-management.md)に関するページを参照してください。

#### <a name="device-overview-shows-primary-user---794259----"></a>デバイス概要でのプライマリ ユーザーの表示 <!--794259  -->
デバイスの概要ページに、ユーザーとデバイスのアフィニティ ユーザー (UDA) とも呼ばれるプライマリ ユーザーが表示されます。 デバイスのプライマリ ユーザーを表示するには、**[Intune]** > **[デバイス]** > **[すべてのデバイス]** を選択し、デバイスを選びます。 プライマリ ユーザーは、**[概要]** ページの上部近くに表示されます。

#### <a name="additional-managed-google-play-app-reporting-for-android-enterprise-work-profile-devices----4105925----"></a>Android エンタープライズ仕事用プロファイル デバイスに関するマネージド Google Play アプリの追加レポート <!-- 4105925  -->
Android エンタープライズ仕事用プロファイル デバイスに展開されたマネージド Google Play アプリについて、デバイスにインストールされているアプリの特定のバージョン番号を表示できます。 これは必須アプリのみに適用されます。 将来のリリースでは、利用可能なアプリに対して同じ機能が有効になります。 

### <a name="device-configuration"></a>デバイス構成

#### <a name="set-login-settings-and-control-restart-options-on-macos-devices----1210083----"></a>macOS デバイスでログイン設定を行い、再起動オプションを制御する <!-- 1210083  -->
macOS デバイスで、デバイス構成プロファイルを作成できます (**[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** > プラットフォームに **[macOS]** を選択し、プロファイルの種類に **[デバイス機能]** を選択します)。 この更新には、カスタム バナーの表示、ユーザーのサインイン方法の選択、電源設定の表示または非表示などの新しいログイン ウィンドウ設定が含まれています。

これらの設定を表示するには、[macOS デバイスの機能設定](macos-device-features-settings.md)に関するページを参照してください。

#### <a name="configure-wifi-on-android-enterprise-device-owner-dedicated-devices-running-in-multi-app-kiosk-mode---3041940----"></a>マルチアプリ キオスク モードで実行されている Android エンタープライズのデバイスの所有者専用デバイスに対する WiFi の構成 <!--3041940  -->
マルチアプリ キオスク モードで専用デバイスとして実行されている場合、Android エンタープライズのデバイスの所有者に対して設定を有効にできます。 この更新では、ユーザーが WiFi ネットワークを構成して接続できるようにすることができます (**[Intune]** > **[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** > プラットフォームに **[Android エンタープライズ]** > プロファイルの種類に **[デバイスの所有者のみ]、[デバイスの制限]** > **[専用デバイス]** > **[キオスク モード]**: **[複数アプリ]** > **[WiFi 構成]**)。 

構成できるすべての設定を確認するには、[機能を許可または制限する Android エンタープライズ デバイスの設定](device-restrictions-android-for-work.md)に関するページを参照してください。

適用対象:マルチアプリ キオスク モードで実行されている Android エンタープライズ専用デバイス


#### <a name="configure-bluetooth-and-pairing-on-android-enterprise-device-owner-dedicated-devices-running-in-multi-app-kiosk-mode----3041941----"></a>マルチアプリ キオスク モードで実行されている Android エンタープライズのデバイスの所有者専用デバイスに対する Bluetooth とペアリングの構成 <!-- 3041941  -->
マルチアプリ キオスク モードで専用デバイスとして実行されている場合、Android エンタープライズのデバイスの所有者に対して設定を有効にできます。 この更新では、エンドユーザーが Bluetooth を有効にして Bluetooth 経由でデバイスをペアリングすることを許可できます (**[Intune]** > **[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** > プラットフォームに **[Android エンタープライズ]** > プロファイルの種類に **[デバイスの所有者のみ]、[デバイスの制限]** > **[専用デバイス]** > **[キオスク モード]**: **[複数アプリ]** > **[Bluetooth の構成]**)。 

構成できるすべての設定を確認するには、[機能を許可または制限する Android エンタープライズ デバイスの設定](device-restrictions-android-for-work.md)に関するページを参照してください。

適用対象:マルチアプリ キオスク モードで実行されている Android エンタープライズ専用デバイス

#### <a name="create-and-use-oemconfig-device-configuration-profiles-in-intune----3305883----"></a>Intune での OEMConfig デバイス構成プロファイルの作成と使用 <!-- 3305883  -->
この更新では、Intune で OEMConfig を使用した Android エンタープライズ デバイスの構成がサポートされています。 具体的には、デバイス構成プロファイルを作成し、OEMConfig を使用して Android エンタープライズ デバイスに設定を適用できます (**[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** > プラットフォームに **[Android エンタープライズ]**)。

現在、OEM のサポートは OEM ごとになっています。 必要な OEMConfig アプリが OEMConfig アプリの一覧にない場合は、`IntuneOEMConfig@microsoft.com` にお問い合わせください。

この機能の詳細については、「[Use and manage Android Enterprise devices with OEMConfig in Microsoft Intune](android-oem-configuration-overview.md)」(Microsoft Intune での OEMConfig を使用した Android エンタープライズ デバイスの使用と管理) を参照してください。

適用対象:Android エンタープライズ

#### <a name="windows-update-notifications-----3316758-3316782----"></a>Windows Update の通知  <!-- 3316758, 3316782  -->
Windows Update リングの構成に、Intune コンソール内から管理できる*ユーザー エクスペリエンス設定*の 2 つの設定を追加しました。 次のことができるようになりました。
- ユーザーが [Windows 更新プログラムの有無をスキャン](windows-update-settings.md#block-user-from-scanning-for-windows-updates)することをブロックまたは許可する。
- ユーザーが表示できる [Windows Update の通知レベル](windows-update-settings.md#windows-update-notification-level)を管理する。

#### <a name="new-device-restriction-settings-for-android-enterprise-device-owner----3574254----"></a>Android エンタープライズのデバイスの所有者に関する新しいデバイス制限の設定 <!-- 3574254  -->
Android エンタープライズ デバイスでは、機能を許可または制限したり、パスワード規則を設定したりするデバイス制限プロファイルを作成できます (**[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** > プラットフォームに **[Android エンタープライズ]** を選択し、プロファイルの種類に **[デバイスの所有者のみ] > [デバイスの制限]** を選択します)。 

この更新プログラムには、新しいパスワード設定が含まれています。また、この更新プログラムによって、フル マネージド デバイス用に Google Play ストア内のアプリへのフル アクセスができます。 現在の設定一覧を確認するには、[Android エンタープライズ デバイスの機能を許可または制限する設定](device-restrictions-android-for-work.md)に関するページを参照してください。 

適用対象:Android エンタープライズのフル マネージド デバイス

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---"></a>Windows 10 デバイスのコンプライアンス ポリシーでの TPM チップセットのチェック <!-- 3617671 -->

この機能は遅れており、将来のリリースに組み込まれる見込みです。

#### <a name="updated-ui-changes-for-microsoft-edge-browser-on-windows-10-and-later-devices----3775833-----"></a>Windows 10 以降のデバイスでの Microsoft Edge ブラウザーの更新された UI の変更 <!-- 3775833   -->
デバイス構成プロファイルを作成するとき、Windows 10 以降のデバイスで Microsoft Edge の機能を許可または制限することができます (**[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** > プラットフォームに **[Windows 10 以降]** > プロファイルの種類に **[デバイスの制限]** > **[Microsoft Edge ブラウザー]**)。 この更新では、Microsoft Edge の設定がよりわかりやすく、より簡単に理解できるようになっています。 

これらの機能を表示するには、[Microsoft Edge ブラウザーのデバイス制限の設定](device-restrictions-windows-10.md#microsoft-edge-browser)に関するページを参照してください。

適用対象:Windows 10 以降

#### <a name="expanded-support-for-android-enterprise-fully-managed-devices--preview-------3903241-3903244-3903246-----"></a>Android エンタープライズ フル マネージド デバイス向け拡張サポート (プレビュー)  <!--   3903241, 3903244, 3903246   -->
引き続きパブリック プレビュー段階にある Android エンタープライズ フル マネージド デバイスのサポートを、以下を含むように拡張しました ([最初の発表は 2019 年 1 月](whats-new.md#week-of-january-14-2019))。 

- フル マネージドの専用デバイスでは、[コンプライアンス ポリシー](compliance-policy-create-android-for-work.md)を作成してパスワード規則やオペレーティング システムの要件を含めることができます (**[デバイスのポリシー準拠]** > **[ポリシー]** > **[ポリシーの作成]** > プラットフォームに **[Android エンタープライズ]** を選択し、プロファイルの種類に **[デバイスの所有者]** を選択します)。 

  専用デバイスでは、デバイスが **[非準拠]** と表示されることがあります。 条件付きアクセスは、専用デバイスでは使用できません。 専用デバイスを割り当てられたポリシーに準拠させるためのタスクやアクションを必ず完了してください。

- [条件付きアクセス](conditional-access.md) - Android に適用される条件付きアクセスのポリシーは、Android エンタープライズ フル マネージド デバイスにも適用されます。 ユーザーは **Microsoft Intune アプリ**を使用して、自分のフル マネージド デバイスを Azure Active Directory に登録できるようになりました。 そのうえで、コンプライアンスの問題を確認して解決し、組織のリソースにアクセスします。

- 新しいエンド ユーザー アプリ (Microsoft Intune アプリ) - **Microsoft Intune** と呼ばれる、Android フル マネージド デバイス用の新しいエンドユーザー アプリがあります。 この新しいアプリは軽量かつ最新のものであり、ポータル サイト アプリと同様の機能が提供されますが、フル マネージド デバイスの場合です。 詳細については、[Google Play の Microsoft Intune アプリ](https://play.google.com/store/apps/details?id=com.microsoft.intune)に関するページを参照してください。

Android のフル マネージド デバイスを設定するには、**[デバイスの登録]** > **[Android の登録]** > **[Corporate-owned, fully managed user devices]\(会社が所有する完全に管理されたユーザー デバイス\)** に移動します。 フル マネージド Android デバイスのサポートはプレビュー段階であり、一部の Intune 機能は完全に機能しない可能性があります。  

このプレビューの詳細については、「[Microsoft Intune - Preview 2 for Android Enterprise Fully Managed devices](https://aka.ms/preview2_AE_fullymanaged)」(Microsoft Intune - Android エンタープライズ フル マネージド デバイス用プレビュー 2) のブログを参照してください。


### <a name="device-enrollment"></a>デバイスの登録

#### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470--wnstaged--"></a>セットアップ アシスタント中、一部の画面をスキップするようにプロファイルを構成する <!-- 2276470  wnstaged-->
macOS 登録プロファイルを作成するとき、セットアップ アシスタントを使用中のユーザーに表示される次の画面のスキップを構成できます。
- 外観
- ディスプレイの色調
- iCloudStorage 新しいプロファイルを作成するかプロファイルを編集する場合は、選択したスキップする画面が Apple MDM サーバーと同期している必要があります。  ユーザーは、プロファイルの変更を取得するときに遅延が発生しないように、手動でのデバイスの同期を発行できます。
詳しくは、「[Device Enrollment Program または Apple School Manager を使用して macOS デバイスを自動登録する](device-enrollment-program-enroll-macos.md)」をご覧ください。

#### <a name="bulk-device-naming-when-enrolling-corporate-ios-devices--3566569----"></a>企業の iOS デバイスを登録するときのデバイスの一括名前付け<!--3566569  -->
Apple の会社登録方法 (DEP/ABM/ASM) のいずれかを使用する場合、受信 iOS デバイスに自動的に名前を付けるためにデバイス名の形式を設定できます。 テンプレートで、デバイスの種類とシリアル番号を含む形式を指定できます。 これを行うには、**[Intune]** > **[デバイスの登録]** > **[Apple の登録]** > **[Enrollment Program トークン]** > **[トークンの選択]** >**[プロファイルの作成]** > **[Device naming format]\(デバイスの名前付け形式\)** を選択します。 既存のプロファイルを編集できますが、新しく同期されたデバイスのみに名前が適用されます。

#### <a name="updated-default-timeout-message-on-enrollment-status-page----3959331---"></a>登録ステータス ページの更新された既定のタイムアウト メッセージ <!-- 3959331 -->
登録ステータス ページ (ESP) が ESP プロファイルに指定されたタイムアウト値を超えたときにユーザーに表示される、既定のタイムアウト メッセージを更新しました。 新しい既定のメッセージは、ユーザーに表示され、ユーザーが ESP 展開で行う次のアクションを理解するのに役立ちます。  

### <a name="device-management"></a>デバイス管理

#### <a name="retire-noncompliant-devices-----1827291-----"></a>非準拠デバイスをインベントリから削除する  <!-- 1827291   -->
この機能は遅れており、将来のリリースで提供されます。


### <a name="monitor-and-troubleshoot"></a>監視とトラブルシューティング

#### <a name="intune-data-warehouse-v10-changes-reflecting-back-to-beta----4403765---"></a>ベータに反映された Intune データ ウェアハウス V1.0 の変更 <!-- 4403765 -->
V1.0 が 1808 で初めて導入されたとき、ベータ API とはいくつかの重要な点で異なっていました。 1903 では、それらの変更がベータ API バージョンに反映されます。 ベータ API バージョンを使用する重要なレポートがある場合は、破壊的な変更を回避するためにそれらのレポートを V1.0 に切り替えることを強くお勧めします。 詳細については、「[Intune データ ウェアハウス API の変更ログ](reports-changelog.md#1903-part-2)」を参照してください。

#### <a name="monitor-security-baseline-status-public-preview----3082047---"></a>セキュリティ ベースライン状態のモニター (パブリック プレビュー) <!-- 3082047 --> 
セキュリティ ベースラインのモニタリングに[カテゴリごとのビュー](security-baselines-monitor.md#per-category-view)を追加しました  (セキュリティ ベースラインは引き続きプレビュー段階です)。 カテゴリごとのビューには、ベースラインの各カテゴリと、そのカテゴリの各状態グループに分類されるデバイスの割合が表示されます。 個々のカテゴリに一致しない、構成が間違っている、または適用されないデバイスの数を把握できるようになりました。

### <a name="role-based-access-control"></a>ロールベースのアクセス制御

#### <a name="scope-tags-for-apple-vpp-tokens---2371886----"></a>Apple VPP トークンのスコープ タグ <!--2371886  -->
Apple VPP トークンにスコープ タグを追加できるようになりました。 同じスコープ タグを割り当てられたユーザーだけが、そのタグを使用して Apple VPP トークンにアクセスできます。 そのトークンを使用して購入した VPP アプリと電子ブックにスコープ タグが継承されます。 スコープ タグの詳細については、[RBAC とスコープ タグの使用](scope-tags.md)に関するページを参照してください。







## <a name="week-of-april-1-2019"></a>2019 年 4 月 1 日の週

### <a name="device-configuration"></a>デバイス構成

#### <a name="updated-certificate-connectors-----icm-113304612---"></a>更新された証明書コネクタ  <!-- ICM 113304612 -->
[Intune Certificate Connector と PFX 証明書コネクタ](certficates-pfx-configure.md#whats-new-for-connectors)の両方についての更新プログラムをリリースしました。 新しいリリースでは、いくつかの既知の問題を修正しています。  

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
以前、**[Intune データ ウェアハウス]** ブレードの **[Power BI ファイルのダウンロード]** リンクでは、Intune データ ウェアハウス レポート (.pbix ファイル) がダウンロードされていました。 このレポートは Power BI コンプライアンス アプリに置き換えられました。 Power BI コンプライアンス アプリには特別な読み込みまたはセットアップは必要ありません。 Power BI オンライン ポータル上で直接開き、資格情報に基づいて、お使いの Intune テナントのデータを具体的に表示します。 Intune で、[Intune] ブレードの右側にある **[Intune データ ウェアハウスの設定]** リンクを選択します。 次に **[Power BI アプリを取得する]** をクリックします。 詳細については、「[Power BI でデータ ウェアハウスに接続する](reports-proc-get-a-link-powerbi.md)」を参照してください。

## <a name="week-of-march-18-2019"></a>2019 年 3 月 18 日の週

### <a name="app-management"></a>アプリ管理

#### <a name="deploy-microsoft-visio-and-microsoft-project----3725386----"></a>Microsoft Visio と Microsoft Project の展開 <!-- 3725386  -->
Microsoft Intune を使用して、Windows 10 デバイスに Microsoft Visio Pro for Office 365 と Microsoft Project Online デスクトップ クライアントを独立したアプリとして展開できるようになりました (これらのアプリのライセンスを所有している場合)。 Intune で、**[クライアント アプリ]** > **[アプリ]** > **[追加]** を選択して **[アプリの追加]** ブレードを表示します。 **[アプリの追加]** ブレードで、**[アプリの種類]** として **[Windows 10]** を選択します。 次に、**[アプリ スイートの構成]** を選択してインストールするアプリを選びます。 Windows 10 デバイス用 Office 365 アプリの詳細については、「[Microsoft Intune で Windows 10 デバイスに Office 365 アプリを割り当てる](apps-add-office365.md)」を参照してください。

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

> [!Note]
> この機能はまだ、すべてのお客様に対して完全には展開されていません。 一括登録したデバイスでポータル サイトを使用できない場合は、この変更が自分のアカウントにロールアウトされるまで待つ必要があります。

#### <a name="the-microsoft-teams-app-can-be-selected-as-part-of-the-office-app-suite----3828932----"></a>Microsoft Teams アプリを Office アプリ スイートの一部として選択できる <!-- 3828932  -->
Microsoft Teams アプリを Office Pro Plus アプリ スイートのインストールの一部として含めるか除外することができます。 この機能は、Office Pro Plus のビルド番号 16.0.11328.20116 以降で使用できます。 インストールを完了するには、サインアウトしてからデバイスにサインインする必要があります。 Intune で、**[クライアント アプリ]** > **[アプリ]** > **[追加]** を選択します。 **[Office 365 スイート]** アプリの種類の 1 つを選択し、次に **[アプリ スイートの構成]** を選択します。

### <a name="device-configuration"></a>デバイス構成

#### <a name="automatically-start-an-app-when-running-multiple-apps-in-kiosk-mode-on-windows-10-and-later-devices----2351390---"></a>Windows 10 以降のデバイスのキオスク モードで複数のアプリを実行しているときに、アプリを自動的に開始する <!-- 2351390 -->

Windows 10 以降のデバイスでは、デバイスをキオスク モードで実行し、多くのアプリを実行できます。 この更新には、**[自動起動]** 設定があります (**[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** > プラットフォームに **[Windows 10 以降]** > プロファイルの種類に **[キオスク]** > **[複数アプリのキオスク]**)。 この設定を使用して、ユーザーがデバイスにサインインしたときにアプリを自動的に起動できます。

すべてのキオスク設定の説明を見るには、「[Intune で Windows 10 以降のデバイスをキオスクとして実行するための設定](kiosk-settings-windows.md)」を参照してください。

適用対象:Windows 10 以降

#### <a name="operational-logs-also-show-details-on-non-compliant-devices----4063755----"></a>操作ログにも非準拠デバイスの詳細を表示 <!-- 4063755  -->
Intune のログを Azure Monitor の機能にルーティングする場合、操作ログもルーティングすることができます。 この更新では、操作ログで非準拠デバイスに関する情報も提供されます。 

この機能の詳細については、「[Intune でストレージ、イベント ハブ、または Log Analytics にログ データを送信する](review-logs-using-azure-monitor.md)」を参照してください。

#### <a name="route-logs-to-azure-monitor-in-more-intune-workloads----3804627---"></a>より多くの Intune ワークロードで Azure Monitor にログをルーティングする <!-- 3804627 -->
Intune では、監査ログと操作ログを Azure Monitor のイベント ハブ、ストレージ、ログ分析にルーティングできます (**[Intune]** > **[モニター]** > **[診断設定]**)。 この更新では、コンプライアンス、構成、クライアント アプリなど、より多くの Intune ワークロードでこれらのログをルーティングできます。 

Azure Monitor へのログのルーティングの詳細については、「[Intune でストレージ、イベント ハブ、または Log Analytics にログ データを送信する](review-logs-using-azure-monitor.md)」を参照してください。

#### <a name="create-and-use-mobility-extensions-on-android-zebra-devices-in-intune----3305880-----"></a>Intune で Android Zebra デバイス上にモビリティ拡張機能を作成して使用する <!-- 3305880   -->
この更新では、Intune で Android Zebra デバイスの構成がサポートされています。 具体的には、デバイス構成プロファイルを作成し、StageNow によって生成されたモビリティ拡張機能 (MX) プロファイルを使用して Android Zebra デバイスに設定を適用できます (**[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** > プラットフォームに **[Android]** を選択し、プロファイルの種類に **[MX プロファイル (Zebra のみ)]** を選択します)。

この機能の詳細については、[Intune のモビリティ拡張機能による Zebra デバイスの使用と管理](android-zebra-mx-overview.md)に関するページを参照してください。

適用対象:Android

### <a name="device-management"></a>デバイス管理

#### <a name="encryption-report-for-windows-10-devices-in-public-preview---2351538---"></a>Windows 10 デバイスでの暗号化レポート (パブリック プレビュー)<!-- 2351538 -->  
新しい[暗号化レポート (プレビュー)](encryption-monitor.md) を使用して、Windows 10 デバイスの暗号化の状態に関する詳細を確認できます。 利用可能な詳細には、デバイスの TPM バージョン、暗号化の準備と状態、エラー レポートなどが含まれます。  

#### <a name="access-bitlocker-recovery-keys-from-the-intune-portal-in-public-preview----2351547-----"></a>Intune ポータルからの BitLocker 回復キーへのアクセス (パブリック プレビュー) <!-- 2351547   -->  
Intune を使用して、Azure Active Directory から BitLocker キー ID や BitLocker 回復キーに関する[詳細を表示](encryption-monitor.md)できるようになりました。

#### <a name="microsoft-edge-support-for-intune-scenarios-on-ios-and-android-devices----3411007---"></a>iOS および Android デバイスでの Intune シナリオに対する Microsoft Edge サポート <!-- 3411007 -->
Microsoft Edge で、Intune Managed Browser と同じ管理シナリオがすべてサポートされ、エンド ユーザー エクスペリエンスの機能強化が追加されます。 Intune ポリシーで有効になっている Microsoft Edge のエンタープライズ機能には、デュアル ID、アプリ保護ポリシーの統合、Azure アプリケーション プロキシの統合、マネージドのお気に入り、ホーム ページのショートカットが含まれます。 詳細については、[Microsoft Edge のサポート](app-configuration-managed-browser.md#microsoft-edge-support)に関するページを参照してください。

#### <a name="exchange-onlineintune-connector-deprecate-support-for-eas-only-devices---3105122----"></a>EAS 専用デバイスに対する Exchange Online/Intune コネクタのサポート廃止 <!--3105122  -->
Intune コンソールでは、Intune コネクタを使用して Exchange Online に接続されている EAS 専用デバイスの表示と管理がサポートされなくなりました。 代わりに次のオプションがあります。
- モバイルデバイス管理 (MDM) でデバイスを登録する
- Intune App Protection ポリシーを使用してデバイスを管理する
- 「[Exchange Online のクライアントとモバイル](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/clients-and-mobile-in-exchange-online)」で説明されているように Exchange コントロールを使用する

### <a name="search-the-all-devices-page-for-an-exact-device-by-using-name---4254930---"></a>すべてのデバイスの検索ページで [名前] を使用して正確なデバイスを探す <!--4254930 -->
正確なデバイス名を検索できるようになりました。 **[Intune]** > **[デバイス]** > **[すべてのデバイス]** に移動し、検索ボックスでデバイス名を {} で囲って完全一致を検索します。 たとえば、**{Device12345}** のようにします。

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

Intune で、**[クライアント アプリ]** > **[アプリ]** > "アプリ名" > **[デバイスのインストール状態]** の順に選択します。 **[状態の詳細]** 列で新しいエラー メッセージが使用できるようになります。

#### <a name="new-app-categories-screen-in-the-company-portal-app-for-windows-10---3834780----"></a>Windows 10 用ポータル サイト アプリでの新しい [アプリのカテゴリ] 画面<!-- 3834780  -->
**[アプリのカテゴリ]** という新しい画面が追加され、Windows 10 用ポータル サイトでのアプリの参照と選択のエクスペリエンスが向上しました。 ユーザーには、**[おすすめ]**、**[教育]**、**[生産性]** などのカテゴリに並べ替えられたアプリが表示されるようになります。 この変更は、ポータル サイト バージョン 10.3.3451.0 以降で表示されます。 新しい画面を表示するには、「[アプリの UI の新機能](https://docs.microsoft.com/intune/whats-new-app-ui)」を参照してください。 ポータル サイトでのアプリの詳細については、「[デバイスにアプリをインストールして共有する](/intune-user-help/install-apps-cpapp-windows)」を参照してください。  

#### <a name="power-bi-compliance-app----1455231-doc-work-item---"></a>Power BI コンプライアンス アプリ <!-- 1455231 doc-work-item -->
[Intune コンプライアンス (データ ウェアハウス)](https://app.powerbi.com/groups/me/getapps/services/Intune_dw_compliance) アプリを使用して、Power BI Online 内の Intune データ ウェアハウスにアクセスします。 この Power BI アプリを使用すると、設定を行うことも、Web ブラウザーを離れることもなく、事前に作成されたレポートにアクセスし、共有することができます。 詳細については、[変更ログ - Power BI コンプライアンス アプリ](reports-changelog.md#power-bi-compliance-app)に関するページを参照してください。


### <a name="device-configuration"></a>デバイス構成

#### <a name="powershell-scripts-can-run-in-a-64-bit-host-on-64-bit-devices----1862675-----"></a>PowerShell スクリプトが 64 ビット デバイスの 64 ビット ホストで実行できる <!-- 1862675   -->
PowerShell スクリプトをデバイス構成プロファイルに追加すると、64 ビット オペレーティング システムであっても、スクリプトは常に 32 ビットで実行されます。 この更新により、管理者はスクリプトを実行 64 ビット デバイスの 64 ビット PowerShell ホストでスクリプトを実行できます (**[デバイス構成]** > **[PowerShell スクリプト]** > **[追加]** > **[構成]** > **[Run script in 64 bit PowerShell Host]\(64 ビット PowerShell ホストでスクリプトを実行\)**)。

PowerShell の使用に関する詳細については、[Intune での PowerShell スクリプト](intune-management-extension.md)に関するページを参照してください。

適用対象:Windows 10 以降

#### <a name="macos-users-are-prompted-to-update-their-password----1873216---"></a>macOS ユーザーにパスワードの更新を求める <!-- 1873216 -->
Intune では、macOS デバイスに対して **ChangeAtNextAuth** 設定を強制しています。 この設定は、コンプライアンス パスワード ポリシーまたはデバイス制限パスワード プロファイルが設定されているエンドユーザーとデバイスに影響します。 エンド ユーザーはスワードの更新を 1 回求められます。 このプロンプトは、デバイスへのサインインなどの認証を必要とするタスクをユーザーが初めて実行するたびに発生します。 また、キーチェーン アクセスの要求など、管理者特権が必要なことをユーザーが行うときにも、パスワードの更新を求めることができます。 

管理者によって新規または既存のパスワード ポリシーが変更されると、エンドユーザーは再度パスワードの更新を求められます。

適用対象:  
macOS

#### <a name="assign-scep-certificates-to-a-userless-macos-device-----2340521----"></a>ユーザーレス macOS デバイスに SCEP 証明書を割り当てる  <!-- 2340521  -->
ユーザー アフィニティのないデバイスを含む macOS デバイスにデバイス属性を使用して Simple Certificate Enrollment Protocol (SCEP) 証明書を割り当て、その証明書プロファイルを Wi-Fi または VPN プロファイルに関連付けることができます。 これにより既にあるサポートを拡張して、Windows、iOS、Android を実行する[ユーザー アフィニティのあるデバイスまたはユーザー アフィニティのないデバイスに SCEP 証明書を割り当て](certificates-scep-configure.md#create-a-scep-certificate-profile)済みです。  この更新では、macOS の SCEP 証明書プロファイルを構成するときに、*[デバイス]* という証明書の種類を選択するオプションが追加されています。

適用対象: 
- macOS

#### <a name="intune-conditional-access-ui-update------2432313-----"></a>Intune の条件付きアクセスの UI の更新   <!-- 2432313   -->
Intune コンソール内の条件付きアクセスの UI の改善を行いました。 たとえば、次のとおりです。
-  Intune の*条件付きアクセス* ブレードを Azure Active Directory のブレードに置き換え。 これにより、Azure AD テクノロジのまま[条件付きアクセス](conditional-access.md)のすべての設定と構成に Intune コンソール内からアクセスできるようになります。 
- *[オンプレミス アクセス]* ブレードの名前を *[Exchange へのアクセス]* に変更し、*[Exchange サービス コネクタ]* の設定をこの名前変更されたブレードに再配置しました。  この変更により、[Exchange Online とオンプレミスに関する詳細を構成および監視する](exchange-connector-install.md)場所が統合されました。  

#### <a name="kiosk-browser-and-microsoft-edge-browser-apps-can-run-on-windows-10-devices-in-kiosk-mode----2935135-----"></a>キオスク ブラウザーと Microsoft Edge ブラウザー アプリを、キオスク モードの Windows 10 デバイスで実行できる <!-- 2935135   -->
キオスク モードの Windows 10 デバイスを使用して、1 つまたは多数のアプリを実行することができます。 この更新プログラムには、キオスク モードでブラウザー アプリを使用するための次のような複数の変更が含まれています。

- Microsoft Edge ブラウザーまたはキオスク ブラウザーを追加して、キオスク デバイスでアプリとして実行します (**[デバイス構成]** > **[プロファイル]** > **[新しいプロファイル]** >  プラットフォームに **[Windows 10 以降]** を選択し、プロファイルの種類に **[キオスク]** を選択します)。
- 新しい機能や設定を使用して、以下のことを許可または制限できます (**[デバイス構成]** > **[プロファイル]** > **[新しいプロファイル]** >  プラットフォームに **[Windows 10 以降]** を選択し、プロファイルの種類に **[デバイスの制限]** を選択します)。

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
iOS および macOS を実行するデバイスで一部の設定と機能を制限することができます (**[デバイス構成]** > **[プロファイル]** > **[新しいプロファイル]** >  プラットフォームに **[iOS]** または **[macOS]** を選択し、プロファイルの種類に **[デバイスの制限]** を選択します)。 この更新プログラムにより、制御可能な機能と設定がさらに追加されます。これには、画面の表示時間の設定、eSIM 設定とセルラー プランの変更が含まれ、iOS デバイスではその他にもあります。 また、ユーザーへのソフトウェア更新プログラムの表示の遅延や、macOS デバイスでのコンテンツ キャッシュのブロックがあります。 

制限可能な機能と設定を確認するには、次を参照してください。

- [iOS デバイスの制限設定](device-restrictions-ios.md)
- [macOS デバイスの制限設定](device-restrictions-macos.md)

適用対象:

- iOS
- macOS

#### <a name="kiosk-devices-are-now-called-dedicated-devices-on-android-enterprise-devices----3598402-----"></a>Android エンタープライズ デバイスで "キオスク" デバイスが "専用デバイス" と呼ばれるようになった <!-- 3598402   -->
Android の用語に合わせるため、Android エンタープライズ デバイスの**キオスク**は、**専用デバイス**に変更されました (**[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** プラットフォームに **[Android エンタープライズ]** を選択し、**[デバイスの所有者のみ]** > **[デバイスの制限]** > **[専用デバイス]** を選択します)。

使用可能な設定を確認するには、[機能を許可または制限するデバイスの設定](device-restrictions-android-for-work.md#dedicated-device-settings)に関するページを参照してください。

適用対象:  
Android エンタープライズ

#### <a name="safari-and-delaying-user-software-update-visibility-ios-settings-are-moving-in-the-intune-ui----3640850-3803313-----"></a>Safari の設定と、iOS のソフトウェア更新プログラムのユーザーへの表示を遅らせる設定を Intune UI の中で移動 <!-- 3640850, 3803313   -->
iOS デバイスの場合、Safari を設定し、ソフトウェア更新プログラムを構成できます。 この更新プログラムでは、これらの設定が Intune UI のさまざまな部分に移動されています。

- Safari の設定は、**[Safari]** (**[デバイス構成]** > **[プロファイル]** > **[新しいプロファイル]** > プラットフォームに **[iOS]** を選択し、プロファイルの種類に **[デバイスの制限]** を選択します) から **[[組み込みアプリ]](device-restrictions-ios.md#built-in-apps)** に移動されました。
- **[Delaying user software update visibility for supervised iOS devices]\(監視対象の iOS デバイスのソフトウェア更新プログラムのユーザーへの表示を遅らせる\)** 設定 (**[ソフトウェア更新プログラム]** > **[iOS のポリシーを更新する]**) は、**[デバイスの制限]** > **[[全般]](device-restrictions-ios.md#general)** に移動されています。  既存のポリシーへの影響の詳細については、[iOS ソフトウェア更新プログラム](software-updates-ios.md#configure-the-policy)に関するページを参照してください。 

設定の一覧については、次を参照してください。

- [iOS デバイスの制限](device-restrictions-ios.md) 
- [iOS ソフトウェア更新プログラム](software-updates-ios.md)

この機能は、以下に適用されます。 

- iOS

#### <a name="enabling-restrictions-in-the-device-settings-is-renamed-to-screen-time-on-ios-devices----3699164-----"></a>iOS デバイスで、[デバイス設定での制限の有効化] 設定が [画面の表示時間] に名前が変更される <!-- 3699164   -->
監視対象の iOS デバイスで、**[デバイス設定での制限の有効化]** を構成することができます (**[デバイス構成]** > **[プロファイル]** > **[新しいプロファイル]** >  プラットフォームに **[iOS]** を選択し、プロファイルの種類に **[デバイスの制限]** を選択し、**[全般]** を選択します)。 この更新プログラムでは、この設定の名前が **[画面の表示時間 (監視モードのみ)]** に変更されています。 

動作は同じです。 具体的には次のとおりです。 

- iOS 11.4.1 以前のバージョン:**[ブロック]** は、エンド ユーザーがデバイス設定で独自の制限を設定できないようにします。 
- iOS 12.0 以降:**[ブロック]** は、エンド ユーザーがデバイス設定 (コンテンツとプライバシーの制限を含む) で独自の**画面の表示時間**を設定できないようにします。 iOS 12.0 にアップグレードされたデバイスでは、デバイスの設定に制限のタブが表示されなくなります。 これらの設定は **[画面の表示時間]** にあります。 

設定の一覧については、[iOS デバイスの制限事項](device-restrictions-ios.md#general)に関するページを参照してください。

適用対象: 
- iOS


### <a name="device-management"></a>デバイス管理

#### <a name="rename-an-enrolled-windows-device----1911112----"></a>登録済み Windows デバイスの名前変更 <!-- 1911112  -->
登録済み Windows 10 デバイス (RS4 以降) の名前を変更できるようになりました。 これを行うには、**[Intune]** > **[デバイス]** > **[すべてのデバイス]**> デバイスを選択 > **[デバイス名の変更]** の順に選択します。 この機能では、ハイブリッド Azure AD Windows デバイスの名前変更は現在サポートされていません。

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
アプリ割り当てごとに、エンド ユーザーにトースト通知が表示されるのを抑制することができます。 Intune で **[クライアント アプリ]** > **[アプリ]** > アプリを選択 > **[割り当て]** > **[グループを含める]** を選択します。 

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
Microsoft Intune から managed Google Play アプリを削除できます。 managed Google Play アプリを削除するには、Azure portal で Microsoft Intune を開き、**[クライアント アプリ]** > **[アプリ]** の順に選択します。 アプリの一覧から、managed Google Play アプリの右側にある省略記号 (...) を選択し、表示された一覧で **[削除]** を選択します。 アプリの一覧からマネージド Google Play アプリを削除すると、そのマネージド Google Play アプリは自動的に未承認になります。

#### <a name="managed-google-play-app-type----1352580---"></a>managed Google Play アプリの種類 <!-- 1352580 -->
**マネージド Google Play** アプリの種類では、特定の[マネージド Google Play アプリ](https://play.google.com/work/search?q=microsoft&c=apps)を Intune に追加できます。 Intune の管理者は、Intune 内で managed Google Play アプリを参照、検索、承認、同期および割り当てできるようになりました。  managed Google Play コンソールに別途移動する必要はなく、また再認証する必要もありません。  Intune で、**[クライアント アプリ]** > **[アプリ]** > **[追加]** を選択します。 **[アプリケーションの種類]** 一覧で、アプリの種類として **[マネージド Google Play]** を選択します。

### <a name="default-android-pin-keyboard----3802457---"></a>既定の Android PIN キーボード <!-- 3802457 -->
Android デバイスで PIN タイプが "数値" の Intune アプリ保護ポリシー (APP) PIN を設定しているエンド ユーザーの場合、以前の設計のような固定の Android キーボード UI ではなく、既定の Android キーボードが表示されるようになります。 この変更は、"数値" と "パスコード" 両方の PIN タイプについて、既定のキーボードを使用するときの動作が Android と iOS の両方で同じになるようにするために行われました。 Android での APP PIN などのエンド ユーザー アクセス設定について詳しくは、[Android のアクセス要件](app-protection-policy-settings-android.md#access-requirements)に関する記事をご覧ください。

### <a name="device-configuration"></a>デバイス構成

#### <a name="use-microsoft-recommended-settings-with-security-baselines-public-preview----2055484-----"></a>セキュリティ ベースラインを使って Microsoft 推奨の設定を使う (パブリック プレビュー) <!-- 2055484   -->

Intune は、セキュリティに的を絞ったその他のサービス (Windows Defender ATP や Office 365 ATP など) と統合されます。 一般的な戦略と、Microsoft 365 サービス間での結束的なエンドツーエンドのセキュリティ ワークフローをお客様から求められています。 目標としているのは、セキュリティの運用と一般的な管理者タスクをブリッジするソリューションを構築できるように戦略を調整することにあります。 Intune では、Microsoft が推奨する一連の "セキュリティ ベースライン" を公開することによって、この目標の達成を目指しています (**[Intune]** > **セキュリティ ベースライン**)。  管理者はこれらのベースラインから直接セキュリティ ポリシーを作成し、それを各自のユーザーにデプロイできます。 また、ご自分の組織のニーズに合わせてベスト プラクティスのレコメンデーションをカスタマイズすることもできます。 Intune では、これらのベースラインにデバイスが準拠した状態に維持されていることが確認され、管理者には準拠した状態にないユーザーまたはデバイスが通知されます。

この機能はパブリック プレビューなので、現在作成されているプロファイルは、一般提供 (GA) されるセキュリティ ベースラインのテンプレートには引き継がれません。 運用環境でこれらのプレビュー テンプレートを使用することは計画しないでください。

セキュリティ ベースラインについて詳しくは、[Intune での Windows 10 セキュリティ ベースラインの作成](security-baselines-monitor.md)に関する記事をご覧ください。

この機能は、以下に適用されます。Windows 10 以降

#### <a name="non-administrators-can-enable-bitlocker-on-windows-10-devices-joined-to-azure-ad---2147379-----"></a>管理者以外のユーザーが、Azure AD 参加済み Windows 10 デバイスで BitLocker を有効にできる<!-- 2147379   -->
Windows 10 デバイスで BitLocker の設定を有効にすると (**[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** > プラットフォームとして **[Windows 10 以降] を選択** > プロファイルの種類として **[Endpoint Protection]** > **[Windows 暗号化]**)、BitLocker の設定が追加されます。 

この更新には、標準ユーザー (管理者以外) が暗号化を有効にするのを許可する新しい BitLocker の設定が含まれます。 

設定を確認するには、[Windows 10 用の Endpoint Protection 設定](endpoint-protection-windows-10.md#windows-encryption)に関する記事を参照してください。

#### <a name="check-for-configuration-manager-compliance----2192052--eepublished----"></a>Configuration Manager コンプライアンスの確認 <!-- 2192052  eepublished  -->
この更新には、新しい System Center Configuration Manager コンプライアンス設定 (**[デバイスのポリシー準拠]** > **[ポリシー]** > **[ポリシーの作成]** > **[Windows 10 以降]** > **[Configuration Manager のコンプライアンス]**) が含まれます。 Configuration Manager から Intune コンプライアンスにシグナルが送信されます。 この設定を使用して、すべての Configuration Manager シグナルで "準拠" を返すように要求することができます。

たとえば、すべてのソフトウェア更新プログラムをデバイスにインストールすることを要求します。 Configuration Manager では、この要求は "インストール済み" 状態となります。 デバイス上のいずれかのプログラムが不明な状態である場合、Intune ではデバイスが非準拠となります。

この設定については、「[Configuration Manager Compliance (Configuration Manager コンプライアンス)](compliance-policy-create-windows.md#configuration-manager-compliance)」で説明されています。

適用対象:Windows 10 以降

#### <a name="customize-wallpaper-on-supervised-ios-devices-using-a-device-configuration-profile----2809324-----"></a>デバイスの構成プロファイルを使用した監視対象の iOS デバイスの壁紙のカスタマイズ <!-- 2809324   -->
iOS デバイス用のデバイス構成プロファイルを作成するときに、一部の機能をカスタマイズできます (**[デバイスの構成]** > **[プロファイル]** > **[プロファイルの作成]**  >  プラットフォーム用の **iOS** > プロファイルの種類用の **[デバイス機能]**)。 この更新には新しい **[壁紙]** 設定が含まれています。これを使うと、管理者はホーム画面またはロック画面上で .png、.jpg、または .jpeg 画像を使うことができます。 これらの壁紙の設定は、監視対象のデバイスにのみ適用できます。 

これらの設定の一覧については、[iOS デバイスの機能設定](ios-device-features-settings.md)に関する記事をご覧ください。

#### <a name="windows-10-kiosk-is-generally-available----3594661----"></a>Windows 10 キオスクの一般提供 <!-- 3594661  -->
この更新では、Windows 10 以降のデバイスでのキオスク機能が一般提供 (GA) になりました。 追加および構成できるすべての設定については、[Windows 10 (およびそれ以降) のキオスク設定](kiosk-settings.md)に関する記事をご覧ください。

#### <a name="contact-sharing-via-bluetooth-is-removed-in-device-restrictions--device-owner-for-android-enterprise----3598396-----"></a>Android エンタープライズの [デバイスの制限] > [デバイスの所有者] での [Bluetooth 経由での連絡先の共有] の削除 <!-- 3598396   -->
Android エンタープライズ デバイス用にデバイスの制限プロファイルを作成した場合、**[Bluetooth 経由での連絡先の共有 ]** 設定があります。 この更新では、**[Bluetooth 経由での連絡先の共有]** の設定が削除されます (**[デバイスの構成]** > **[プロファイル]** > **[プロファイルの作成]**  >  プラットフォーム用の **Android エンタープライズ** > **[デバイスの制限] > プロファイルの種類の [デバイスの所有者]** > **[全般]**)。 

**[Bluetooth 経由での連絡先の共有]** 設定は、Android エンタープライズのデバイス所有者の管理ではサポートされていません。 したがって、この設定が削除されると、この設定が環境で有効および構成されていた場合でもいかなるデバイスやテナントにも影響はありません。

現在の設定一覧を確認するには、[Android エンタープライズ デバイスの機能を許可または制限する設定](device-restrictions-android-for-work.md)に関するページを参照してください。

適用対象:Android エンタープライズ デバイスの所有者

### <a name="device-management"></a>デバイス管理

#### <a name="selective-wipe-support-for-wip-without-enrollment-devices----1434452---"></a>登録なしの WIP デバイスに対する選択的ワイプのサポート <!-- 1434452 -->
登録なしの Windows Information Protection (WIP-WE) を使うと、MDM への完全な登録を必要とせずに Windows 10 デバイス上の企業データを保護することができます。 WIP-WE ポリシーを使用してドキュメントが保護されると、Intune 管理者は保護されたデータを選択的にワイプすることができます。 ユーザーとデバイスを選択してワイプ要求を送信することにより、WIP-WE ポリシーを介して保護されたデータはすべて使用できなくなります。 Azure portal 内で Intune から、**[モバイル アプリ]** > **[アプリの選択的ワイプ]** の順に選択します。

### <a name="monitor-and-troubleshoot"></a>監視とトラブルシューティング

#### <a name="new-operational-logs-and-ability-to-send-logs-to-azure-monitor-services----3762211----"></a>新しい操作ログ、およびログを Azure Monitor サービスに送信する機能 <!-- 3762211  -->
Intune には、変更が加えられるとイベントを追跡する組み込みの監査ログが備わっています。 この更新には、次の新しいログ記録機能が含まれます。 
- 登録したユーザーおよびデバイスの詳細を示す操作ログ (プレビュー) (成功および失敗した試行を含む)。
- 監査ログと操作ログは Azure Monitor に送信することができます (ストレージ アカウント、イベント ハブ、ログ分析を含む)。 これらのサービスを使うと、保存したり、Splunk や QRadar などの分析を使ったり、ログ データの視覚化を取得したりできます。

この機能について詳しくは、[Intune でのストレージ、イベント ハブ、またはログ分析へのログ データの送信](review-logs-using-azure-monitor.md)に関する記事をご覧ください。

### <a name="skip-more-setup-assistant-screens-on-an-ios-dep-device----2687509----"></a>iOS DEP デバイスでスキップできるセットアップ アシスタントの画面が増える <!-- 2687509  -->
現在スキップすることができる画面に加えて、ユーザーがデバイスを登録するときにセットアップ アシスタント内で次の画面をスキップするように iOS DEP デバイスを設定できます: [ディスプレイの色調]、[プライバシー]、[Android 移行]、[ホーム ボタン]、[iMessage & FaceTime]、[オンボード]、[Watch の移行]、[外観]、[画面の表示時間]、[ソフトウェア更新プログラム]、[SIM のセットアップ]。
スキップする画面を選択するには、**[デバイスの登録]** > **[Apple の登録]** > **[Enrollment Program トークン]** に移動し、トークンを選択します。次に、**[プロファイル]** を選択してプロファイルを選択し、**[プロパティ]** > **[セットアップ アシスタントのカスタマイズ]** を選択し、スキップする画面の **[非表示]** を選択して、**[OK]** を選択します。
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
IT 管理者は、エンド ユーザーによる Intune アプリ PIN の変更が必要になるまでの待機日数を構成できるようになりました。 新しい設定では、*その日数後に PIN がリセットされます*。この設定を使用するには、Azure portal で **[Intune]** > **[クライアント アプリ]** > **[アプリ保護ポリシー]** > **[ポリシーの作成]** > **[設定]** > **[アクセス要件]** の順に選択します。 この機能は、[iOS](app-protection-policy-settings-ios.md) デバイスと [Android](app-protection-policy-settings-android.md) デバイスで使用でき、正の整数値をサポートしています。


#### <a name="intune-device-reporting-fields----2748738---"></a>Intune のデバイス レポートのフィールド <!-- 2748738 -->
Intune では、アプリ登録 ID、Android の製造元、モデル、セキュリティ更新プログラムのバージョン、iOS のモデルなど、デバイス レポートのフィールドが提供されています。 Intune でこれらのフィールドを使用するには、**[クライアント アプリ]** > **[アプリの保護状態]** を選択して、**[アプリ保護レポート: iOS、Android]** を選択します。 さらに、これらのパラメーターは、デバイス製造元 (Android) の**許可**リスト、デバイス モデル (Android および iOS) の**許可**リスト、および Android セキュリティ修正プログラムの最小バージョンの設定を構成するのに役立ちます。 


### <a name="device-configuration"></a>デバイス構成

#### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>管理用テンプレートがパブリック プレビューになり、専用の構成プロファイルに移動される <!-- 3322847 -->

Intune の管理用テンプレート (**[デバイス構成]** > **[管理用テンプレート]**) は現在、パブリック プレビュー段階です。 この更新プログラムでは: 

- 管理用テンプレートには、Intune で管理可能な約 300 の設定が含まれます。 以前は、これらの設定はグループ ポリシー エディターにのみ存在しました。
- 管理用テンプレートはパブリック プレビューで使用できます。
- 管理用テンプレートは、**[デバイス構成]** > **[管理用テンプレート]** から、**[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** を選択し、**[プラットフォーム]** で **[Windows 10 以降]** を選択し、**[プロファイルの種類]** で **[管理用テンプレート]** を選択した場所に移動されています。
- レポートが有効です。

この機能の詳細については、[グループ ポリシー設定を構成するための Windows 10 テンプレート](administrative-templates-windows.md)に関するページを参照してください。

適用対象:Windows 10 以降

#### <a name="use-smime-to-encrypt-and-sign-multiple-devices-for-a-user-----1333642---"></a>S/MIME を使って暗号化し、ユーザーの複数のデバイスに署名する  <!-- 1333642 -->
この更新プログラムには、新しくインポートされる証明書プロファイル (**[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]**、該当するプラットフォーム、**[PKCS のインポートされた証明書]** プロファイルの種類の順に選択) を使用する S/MIME メールの暗号化が含まれます。 Intune では、PFX 形式で証明書をインポートできます。 その後、Intune はその同じ証明書を、単一ユーザーによって登録された複数のデバイスに配信できます。 これには、次のものも含まれます。
- ネイティブ iOS メール プロファイルでは、PFX 形式でインポートされた証明書を使用する S/MIME 暗号化を有効にすることができます。
- Windows Phone 10 デバイス上のネイティブ メール アプリでは、自動的に S/MIME 証明書が使用されます。
- プライベート証明書は複数のプラットフォームに配信できます。 しかし、すべてのメール アプリで S/MIME がサポートされるわけではありません。
- 他のプラットフォームでは、S/MIME を有効にするようにメール アプリを手動で構成する必要がある場合があります。  
- S/MIME 暗号化をサポートするメール アプリでは、発行元の証明書ストアからの読み取りなど、MDM ではサポートできない方法で S/MIME メール暗号化のための証明書の検索を処理する場合があります。
この機能の詳細については、[電子メールの署名と暗号化のための S/MIME の概要](certificates-s-mime-encryption-sign.md)に関するページを参照してください。
サポート対象:Windows、Windows Phone 10、macOS、iOS、Android

#### <a name="new-options-to-automatically-connect-and-persist-rules-when-using-dns-settings-on-windows-10-and-later-devices----1333665-2999078---"></a>Windows 10 以降のデバイスで DNS 設定を使用するときに、自動的に接続してルールを保持する新しいオプション <!-- 1333665, 2999078 -->
Windows 10 以降のデバイスでは、contoso.com などのドメインを解決するための DNS サーバーのリストを含む VPN 構成プロファイルを作成できます。 この更新には、名前解決のための新しい設定が含まれます (**[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** > プラットフォームとして **[Windows 10 以降]** を選択 > プロファイルの種類として **[VPN]** を選択 > **[DNS 設定]** >**[追加]**)。 
- **自動接続**: **有効**にすると、デバイスは、入力された contoso.com などのドメインにアクセスするときに、VPN に自動的に接続します。
- **永続性**: この VPN プロファイルを使用してデバイスに接続している限り、既定で、名前解決ポリシー テーブル (NRPT) のすべてのルールがアクティブになります。 NRPT ルールでこの設定を**有効**にすると、VPN が切断されても、ルールはデバイス上でアクティブなままになります。 VPN プロファイルを削除するか、ルールを手動で削除するまで (PowerShell を使って実行できます)、ルールは保持されます。
[Windows 10 の VPN 設定](vpn-settings-windows-10.md)に関するページでは、これらの設定について説明されています。 

#### <a name="use-trusted-network-detection-for-vpn-profiles-on-windows-10-devices----1500165---"></a>Windows 10 デバイスで VPN プロファイルに対して信頼されたネットワーク検出を使用する <!-- 1500165 -->
信頼されたネットワーク検出を使用すると、ユーザーが信頼されたネットワーク上に既にいるときに、VPN プロファイルで VPN 接続が自動的に作成されるのを防ぐことができます。 この更新により、Windows 10 以降を実行するデバイスでは、DNS サフィックスを追加して信頼されたネットワーク検出を有効にすることができます (**[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** > プラットフォームとして **[Windows 10 以降]** > プロファイルの種類として **[VPN]**)。
[Windows 10 の VPN 設定](vpn-settings-windows-10.md)に関するページには、現在の VPN 設定の一覧があります。

#### <a name="manage-windows-holographic-for-business-devices-used-by-multiple-users----1907917-1063203---"></a>複数のユーザーによって使用される Windows Holographic for Business デバイスを管理する <!-- 1907917, 1063203 -->
現在、共有 PC の設定は、Windows 10 デバイスと Windows Holographic for Business デバイスでカスタム OMA-URI の設定を使用して構成できます。 この更新により、共有デバイスの設定を構成するための新しいプロファイルが追加されます (**[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** > **[Windows 10 以降]** > **[共有のマルチユーザーのデバイス]**)。
この機能の詳細については、[共有デバイスを管理するための Intune の設定](shared-user-device-settings.md)に関するページを参照してください。
適用対象:Windows 10 以降、Windows Holographic for Business

#### <a name="new-windows-10-update-settings---2626030--2512994----"></a>新しい Windows 10 更新プログラムの設定 <!--2626030  2512994  -->
[Windows 10 更新リング](windows-update-for-business-configure.md)で、次の構成を行うことができます。
- **[自動更新の動作]** - 新しいオプション *[既定にリセット]* を使用して、"*2018 年 10 月更新*" を実行している Windows 10 コンピューターで、元の自動更新設定を復元する。
- **[ユーザーによる Windows Update の一時停止をブロックする]** - コンピューターの "*設定*" から、ユーザーによる更新プログラムのインストールの一時停止を許可またはブロックできる、新しいソフトウェア更新プログラムの設定を構成する。 

#### <a name="ios-email-profiles-can-use-smime-signing-and-encryption----2662949---"></a>iOS の電子メール プロファイルで S/MIME の署名と暗号化を使用できる <!-- 2662949 -->
異なる設定を含む電子メール プロファイルを作成することができます。 この更新には、iOS デバイスでのメール通信の署名と暗号化に使用できる S/MIME の設定が含まれます (**[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]**> プラットフォームとして **[iOS]** を選択 > プロファイルの種類として **[電子メール]** を選択)。
[iOS での電子メール構成の設定](email-settings-ios.md)に関するページに、設定の一覧が示されています。

#### <a name="some-bitlocker-settings-support-windows-10-pro-edition---2727036---"></a>BitLocker の一部の設定で Windows 10 Pro エディションがサポートされる<!-- 2727036 -->
Windows 10 デバイスで、BitLocker などの Endpoint Protection の設定を行う構成プロファイルを作成できます。 この更新により、BitLocker の一部の設定に Windows 10 Professional エディションのサポートが追加されます。 これらの保護設定を確認するには、[Windows 10 用の Endpoint Protection 設定](endpoint-protection-windows-10.md#windows-encryption)に関するページを参照してください。

#### <a name="shared-device-configuration-is-renamed-to-lock-screen-message-for-ios-devices-in-the-azure-portal---2809362---"></a>Azure portal で iOS デバイスの共有デバイスの構成が、ロック画面メッセージに名前を変更される<!-- 2809362 -->
iOS デバイス用の構成プロファイルを作成するときに、ロック画面に特定のテキストを表示する**共有デバイス構成**の設定を追加できます。 この更新には、次の変更が含まれます。 
- Azure portal で **[共有デバイスの構成]** 設定の名前が、[Lock Screen Message (supervised only)]\(ロック画面のメッセージ (監視モードのみ)\) に変更されます (**[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]**> プラットフォームとして **[iOS]** を選択 > プロファイルの種類として **[デバイス機能]** を選択 >**[Lock Screen Message]\(ロック画面のメッセージ\)**)。
- ロック画面のメッセージを追加するときは、**[資産タグ情報]** および **[ロック画面の脚注 ]** の変数として、シリアル番号、デバイス名、または別のデバイス固有値を挿入できます。 たとえば、中かっこを使用して `Device name: {{devicename}}` や `Serial number is {{serialnumber}}` などと入力できます。 [iOS トークン](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list)に関するページでは、使用できるトークンの一覧が示されています。
[ロック画面にメッセージを表示するための設定](shared-device-settings-ios.md)に関するページでは、設定の一覧が示されています。

#### <a name="new-app-store-doc-viewing-gaming-device-restriction-settings-added-to-ios-devices----2827760--"></a>iOS デバイスに App Store、ドキュメント表示、ゲーム デバイスの新しい制限の設定が追加される <!-- 2827760-->
**[デバイスの構成]** > **[プロファイル]** > **[プロファイルの作成]** >  プラットフォームとして **[iOS]** を選択 > プロファイルの種類として **[デバイスの制限]** を選択 > **[アプリ ストア、ドキュメント表示、ゲーム]** の順に選択すると、次の設定が追加されます。[Allow managed apps to write contacts to unmanaged contacts accounts]\(マネージド アプリによるアンマネージド連絡先アカウントへの連絡先の書き込みを許可する\)、[Allow unmanaged apps to read from managed contacts accounts]\(アンマネージド アプリによるマネージド連絡先アカウントからの読み取りを許可する\)。これらの設定については、[iOS デバイスの制限](device-restrictions-ios.md#app-store-doc-viewing-gaming)に関するページをご覧ください。

#### <a name="new-notification-hints-and-keyguard-settings-to-android-enterprise-device-owner-devices----3201839-3201843---"></a>Android エンタープライズ デバイス所有者デバイスに対する新しい通知、ヒント、キーガードの設定 <!-- 3201839 3201843 -->
この更新には、デバイス所有者として実行するときの Android エンタープライズ デバイスに関するいくつかの新機能が含まれます。 これらの機能を使用するには、**[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** に移動し、**[プラットフォーム]** で **[Android エンタープライズ]** を選択し、**[プロファイルの種類]** で **[デバイスの所有者のみ]** > **[デバイスの制限]** を選択します。

新機能は次のとおりです。 

- 着信、システム アラート、システム エラーなどのシステム通知の表示を無効にします。
- 初めて開いたアプリのチュートリアルとヒントの開始をスキップすることを提案します。
- カメラ、通知、指紋によるロック解除など、高度なキーガード設定を無効にします。


これらの設定については、[Android エンタープライズ デバイスの制限の設定](device-restrictions-android-for-work.md)に関するページを参照してください。

#### <a name="android-enterprise-device-owner-devices-can-use-always-on-vpn-connections----3202194---"></a>Android エンタープライズ デバイス所有者デバイスで、Always On VPN 接続を使用できる <!-- 3202194 -->
この更新では、Android エンタープライズ デバイス所有者デバイスで常時 VPN 接続を使用できます。 常時 VPN 接続では接続状態が常に維持されるか、ユーザーが自分のデバイスをロックしたとき、デバイスが再起動したとき、ワイヤレス ネットワークに変更があったとき、すぐに再接続されます。 接続を "ロックダウン" モードにすることもできます。このモードでは、VPN 接続が有効になるまですべてのネットワーク トラフィックがブロックされます。
**[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** の順に選択し、プラットフォームとして **[Android エンタープライズ]** を選択し、[デバイスの所有者のみ] として **[デバイスの制限]** を選択し、**[接続]** 設定を選択することで、常時 VPN を有効にできます。 これらの設定については、[Android エンタープライズ デバイスの制限の設定](device-restrictions-android-for-work.md)に関するページを参照してください。

#### <a name="new-setting-to-end-processes-in-task-manager-on-windows-10-devices----3285177---"></a>Windows 10 デバイスのタスク マネージャーでプロセスを終了するための新しい設定 <!-- 3285177 --> 
この更新には、Windows 10 デバイスのタスク マネージャーでプロセスを終了するための新しい設定が含まれます。 デバイス構成プロファイルを使用して (**[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** > **[プラットフォーム]** で **[Windows 10]** を選択 > **[プロファイルの種類]** で **[デバイスの制限]** を選択 > **[全般]** 設定)、この設定の許可または禁止を選択します。
これらの設定については、[Windows 10 デバイスの制限の設定](device-restrictions-windows-10.md)に関するページを参照してください。
適用対象:Windows 10 以降


### <a name="device-enrollment"></a>デバイスの登録

#### <a name="more-detailed-enrollment-restriction-failure-messaging----3111564---"></a>より詳細な登録制限のエラー メッセージ <!-- 3111564 -->
登録の制限が満たされていないときに表示されるエラー メッセージが、より詳細になります。 これらのメッセージを見るには、**[Intune]** > **[トラブルシューティング]** に移動し、[登録エラー] のテーブルを確認します。 詳細については、[登録エラーの一覧](help-desk-operators.md#enrollment-failure-reference)を参照してください。

### <a name="monitor-and-troubleshoot"></a>監視とトラブルシューティング

#### <a name="tenant-status-dashboard-----1124854---"></a>テナントの状態ダッシュボード  <!-- 1124854 -->
新しい [[テナントの状態] ページ](tenant-status.md)では、テナントの状態および関連する詳細を 1 か所に表示できます。  このダッシュボードは、次の 4 つの領域に分かれています。
- **テナントの詳細** - テナントの名前と場所、ご利用の MDM 機関、ご利用のテナントに登録されたデバイスの総数、ご利用のライセンス数などの情報が表示されます。 このセクションには、そのテナントに対する現在のサービス リリースも示されます。
- **コネクタの状態** - 構成済みの使用可能なコネクタに関する情報が表示されるほか、まだ有効にしていないコネクタの一覧も表示できます。  
   各コネクタの現在の状態に基づいて、正常、警告、または異常を示すフラグが付けられます。 コネクタを選択してドリルスルーし、詳細を表示したり、追加情報を構成したりします。
-  **Intune サービスの正常性** - ご利用のテナントでのアクティブなインシデントまたは障害に関する詳細が表示されます。 このセクション内の情報は、Office メッセージ センターから直接取得されます。
-  **Intune ニュース** - テナントのアクティブなメッセージが表示されます。 メッセージには、テナントが Intune の最新の機能を受信する際の通知などが含まれます。  このセクション内の情報は、Office メッセージ センターから直接取得されます。

#### <a name="new-help-and-support-experience-in-company-portal-for-windows-10----1488939--"></a>Windows 10 用ポータル サイトの新しいヘルプとサポート エクスペリエンス <!-- 1488939-->
ポータル サイトの新しい [ヘルプとサポート] ページでは、ユーザーがアプリやアクセスの問題に対して、トラブルシューティングを行ったりヘルプを要求したりできます。 この新しいページで、エラーと診断ログの詳細を電子メールで送信し、組織のヘルプデスクの詳細を確認することができます。 また、関連する Intune ドキュメントへのリンクを含む FAQ セクションもあります。 

#### <a name="new-help-and-support-experience-for-intune------3307080---"></a>Intune の新しいヘルプとサポート エクスペリエンス   <!-- #3307080 -->
今後数日間で、新しいヘルプとサポート エクスペリエンスをすべてのテナントにロールアウトする予定です。 この新しいエクスペリエンスは Intune で利用でき、[Azure portal](https://portal.azure.com/) で Intune のブレードを使用しているときにアクセスできます。
新しいエクスペリエンスでは、自分の言葉で問題を説明し、トラブルシューティングの分析情報と Web ベースの修復コンテンツを受け取ることができます。 これらの解決策は、ユーザーの照会により、ルール ベースの機械学習アルゴリズムを使用して提供されます。 問題固有のガイダンスに加えて、新しいケース作成ワークフローを使用して、電子メールまたは電話でサポート ケースを開きます。 ヘルプとサポートを開いたコンソールの領域に基づいて事前選択されているオプションの静的セットである以前のヘルプとサポート エクスペリエンスが、この新しいエクスペリエンスに置き換えられます。 詳細については、「[Microsoft Intune のサポートを受ける方法](get-support.md)」を参照してください。

### <a name="role-based-access-control"></a>ロールベースのアクセス制御

#### <a name="scope-tags-for-apps----1081941---"></a>アプリのスコープ タグ <!-- 1081941 -->
ロールとアプリへのアクセスを制限するために、スコープのタグを作成できます。 アプリにスコープのタグを追加すると、ロールを持つユーザーのうち、そのスコープのタグも割り当てられているユーザーだけがアプリにアクセスできるようになります。 現在、managed Google Play から Intune に追加されたアプリや、Apple Volume Purchase Program (VPP) を使って購入されたアプリにスコープ タグを割り当てることはできません (ただし、今後サポートされる予定です)。 詳細については、「[スコープのタグを使用してポリシーをフィルター処理する](scope-tags.md)」を参照してください。

<!-- ########################## -->
## <a name="week-of-december-10-2018"></a>2018 年 12 月 10 日の週

### <a name="app-management"></a>アプリ管理

#### <a name="updates-for-application-transport-security----748318---"></a>Application Transport Security 対応のための更新 <!-- 748318 -->

Microsoft Intune では、クラス最高の暗号化を提供する、既定の状態でも安全であることを保証する、また、Microsoft Office 365 などの他の Microsoft サービスと連携することを目的に、トランスポート層セキュリティ (TLS) 1.2 以降をサポートしています。 この要件を満たすために、iOS と macOS のポータル サイトには、やはり TLS 1.2 以降が要求されている Apple の改定後の Application Transport Security (ATS) 要件が適用されます。 ATS では、HTTPS 経由で行われるアプリ通信すべてに、より厳格なセキュリティ保護が適用されます。 この変更により、iOS および macOS のポータル サイト アプリを使用している Intune ユーザーが影響を受けます。 詳しくは、[Intune サポートのブログ](https://aka.ms/compportalats)をご覧ください。

#### <a name="the-intune-app-sdk-will-support-256-bit-encryption-keys----1832174---"></a>256 ビット暗号化キーをサポートするようになる Intune App SDK <!-- 1832174 -->
アプリ保護ポリシーによって暗号化が有効化されると、Android 用 Intune App SDK では現在、256 ビット暗号化キーが使用されます。 古いバージョンの SDK を使用するコンテンツやアプリとの互換性のため、SDK では引き続き 128 ビット キーのサポートが提供されます。

### <a name="microsoft-auto-update-version-450-required-for-macos-devices----3503442---"></a>macOS デバイスに必要な Microsoft Auto Update バージョン 4.5.0 <!-- 3503442 -->
ポータル サイトおよびその他の Office アプリケーション用の更新プログラムの受信を継続するには、Intune によって管理されている macOS デバイスを Microsoft Auto Update 4.5.0 にアップグレードする必要があります。 ユーザーは自分の Office アプリに対してこのバージョンを既に使用している可能性があります。

### <a name="intune-requires-macos-1012-or-later----2827778---"></a>Intune には macOS 10.12 以降が必要 <!-- 2827778 -->
Intune には、macOS バージョン 10.12 以降が必要になりました。 以前の macOS バージョンが使用されているデバイスでは、ポータル サイトを使用して Intune に登録することはできません。 サポートを受けて新しい機能を利用するには、デバイスを macOS 10.12 以降にアップグレードすると共に、ポータル サイト アプリを最新版にアップグレードする必要があります。

<!-- ########################## -->
## <a name="week-of-november-26-2018"></a>2018 年 11 月 26 日の週

### <a name="app-management"></a>アプリ管理

#### <a name="uninstalling-apps-on-corporate-owned-supervised-ios-devices----1281677---"></a>企業所有の監視対象 iOS デバイス上のアプリのアンインストール <!-- 1281677 -->

企業所有の監視対象 iOS デバイス上のアプリを削除できます。 **[アンインストール]** 割り当て種類でユーザーまたはデバイスのグループを対象とすることにより、すべてのアプリを削除できます。 個人所有または監視対象外の iOS デバイスの場合は、引き続き Intune を使用してインストールされたアプリのみを削除できます。

#### <a name="downloading-intune-win32-app-content----2617320---"></a>Intune Win32 アプリのコンテンツのダウンロード <!-- 2617320 -->
Windows 10 RS3 以降のクライアントでは、Windows 10 クライアント上の配信最適化コンポーネントを使用して、Intune Win32 アプリ コンテンツがダウンロードされます。 配信の最適化では、既定で有効になるピア ツー ピア機能が提供されます。 配信の最適化は、グループ ポリシーによって、また将来的には Intune MDM を使用して、構成できます。 詳しくは、[Windows 10 の配信の最適化](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization)に関するページをご覧ください。 

#### <a name="end-user-device-and-app-content-menu----2771453---"></a>エンド ユーザー デバイスとアプリのコンテンツのメニュー <!-- 2771453 -->
エンド ユーザーはデバイス上のコンテキスト メニューとアプリを使用して、デバイスの名前変更、準拠状況の確認などの一般的なアクションをトリガーできるようになりました。

#### <a name="set-custom-background-in-managed-home-screen-app-----3041945---"></a>Managed Home Screen アプリでのカスタム背景の設定  <!-- 3041945 -->
Android エンタープライズのマルチアプリ キオスク モード デバイス上の Managed Home Screen アプリの背景の外観をカスタマイズできる設定が追加されています。  **カスタム URL の背景**を構成するには、Azure portal で Intune に移動し、[デバイス構成] を選択します。 現在のデバイス構成プロファイルを選択するか、新しいプロファイルを作成してキオスク設定を編集します。
キオスクの設定については、[Android エンタープライズ デバイスの制限](device-restrictions-android-for-work.md)に関するページをご覧ください。

#### <a name="app-protection-policy-assignment-save-and-apply----3104570---"></a>アプリ保護ポリシーの割り当ての保存と適用 <!-- 3104570 -->
[アプリ保護ポリシーの割り当て](app-protection-policies.md#deploy-a-policy-to-users)の制御が向上しました。 *[割り当て]* を選んでポリシーの割り当てを設定または編集したときは、変更を適用する前に構成を**保存する**必要があります。 対象リストまたは除外リストに変更を保存しないで、行ったすべての変更をクリアするには、**[破棄]** を使います。  保存または破棄を必要とすることにより、意図したユーザーのみにアプリ保護ポリシーが割り当てられます。

#### <a name="new-microsoft-edge-browser-settings-for-windows-10-and-later----3174639---"></a>Windows 10 以降向けの新しい Microsoft Edge ブラウザー設定 <!-- 3174639 -->
この更新には、デバイス上の Microsoft Edge ブラウザーを制御および管理するための新しい設定が含まれます。 これらの設定の一覧については、[Windows 10 (以降) に対するデバイスの制限](device-restrictions-windows-10.md#microsoft-edge-browser)に関するページをご覧ください。

#### <a name="new-apps-support-with-app-protection-policies----3330037---"></a>アプリ保護ポリシーでの新しいアプリのサポート <!-- 3330037 -->
[Intune アプリ保護ポリシー](app-protection-policies.md)で次のアプリを管理できるようになりました。
- Stream (iOS)
- To DO (Android、iOS)
- PowerApps (Android、iOS)
- Flow (Android、iOS)

これらのアプリでも、他の Intune ポリシーで管理されたアプリと同じように、アプリ保護ポリシーを使って、企業データを保護し、データ転送を制御してください。 注: Flow がまだコンソールに表示されない場合は、アプリ保護ポリシーを作成または編集するときに Flow を追加します。 これを行うには、**[+ その他のアプリ]** オプションを使い、入力フィールドで Flow の *[アプリ ID]* を指定します。 Android の場合は *com.microsoft.flow* を使い、iOS の場合は *com.microsoft.procsimo* を使います。


### <a name="device-configuration"></a>デバイス構成

#### <a name="ios-and-macos-version-numbers-and-build-numbers-are-shown----1892471---"></a>iOS および macOS のバージョン番号とビルド番号が表示される <!-- 1892471 -->
**[デバイスのポリシー準拠]** > **[デバイスのポリシー準拠]** に、iOS および macOS のオペレーティング システム バージョンが表示され、コンプライアンス ポリシーで使用できます。 この更新には、両方のプラットフォームで構成可能なビルド番号が含まれます。
セキュリティ更新がリリースされるとき、Apple は通常、バージョン番号を現状のまま残しますが、ビルド番号を更新します。 コンプライアンス ポリシーでビルド番号を使用することで、脆弱性更新がインストールされているかどうかを簡単に確認できます。
この機能を使うには、[iOS](compliance-policy-create-ios.md#device-health) および [macOS](compliance-policy-create-mac-os.md#device-properties) のコンプライアンス ポリシーをご覧ください。

#### <a name="update-rings-are-being-replaced-with-delivery-optimization-settings-for-windows-10-and-later----2753807---"></a>Windows 10 以降では、更新プログラムのリングが配信の最適化の設定に置き換えられる <!-- 2753807 -->
配信の最適化は、Windows 10 以降での新しい構成プロファイルです。 この機能では、組織内のデバイスにソフトウェア更新プログラムを配信するためのエクスペリエンスが、いっそう合理化されています。 また、この更新では、構成プロファイルを使用して新規および既存の更新プログラムのリングで設定を配信することもできます。
配信の最適化の構成プロファイルを構成するには、[Windows 10 (以降) での配信の最適化の設定](delivery-optimization-windows.md)に関するページをご覧ください。

#### <a name="new-device-restriction-settings-added-to-ios-and-macos-devices----2827760---"></a>iOS および macOS デバイスに追加された新しいデバイス制限の設定 <!-- 2827760 -->
この更新プログラムには、iOS 12 と共にリリースされた iOS および macOS デバイス用の新しい設定が含まれています。

**iOS の設定**:  
- [全般]:アプリ削除をブロックする (監視モードのみ)
- [全般]:USB 制限モードをブロックする (監視モードのみ)
- [全般]:日付と時刻自動設定を強制する (監視モードのみ)
- ［パスワード］:パスワード オートフィルをブロックする (監視モードのみ)
- ［パスワード］:パスワード近接要求をブロックする (監視モードのみ)
- ［パスワード］:パスワード共有をブロックする (監視モードのみ)

**macOS の設定**:  
- ［パスワード］:パスワード オートフィルをブロックする
- ［パスワード］:パスワード近接要求をブロックする
- ［パスワード］:パスワード共有をブロックする

これらの設定の詳細については、[iOS](device-restrictions-ios.md) および [macOS](device-restrictions-macos.md) デバイスの制限の設定を参照してください。

### <a name="device-enrollment"></a>デバイスの登録

#### <a name="select-apps-tracked-on-the-enrollment-status-page---2531007---"></a>登録ステータス ページで追跡するアプリの選択<!-- 2531007 -->
[登録ステータス] ページで追跡するアプリを選択できます。 これらのアプリをインストールするまで、ユーザーはデバイスを使用できません。 詳しくは、「[登録ステータス ページを設定する](windows-enrollment-status.md)」をご覧ください。

#### <a name="search-for-autopilot-device-by-serial-number---2595788---"></a>シリアル番号による Autopilot デバイスの検索 <!--2595788 -->
シリアル番号で Autopilot デバイスを検索できるようになりました。 これを行うには、**[デバイスの登録]** > **[Windows の登録]** > **[デバイス]** の順に選択し、**[シリアル番号による検索]** ボックスにシリアル番号を入力して、Enter キーを押します。

#### <a name="track-installation-of-office-proplus---2620217---"></a>Office ProPlus のインストールの追跡 <!--2620217 -->
ユーザーは、[[登録ステータス] ページ](windows-enrollment-status.md)を使用して、[Office ProPlus](apps-add-office365.md) のインストールの進行状況を追跡できます。 詳しくは、「[登録ステータス ページを設定する](windows-enrollment-status.md)」をご覧ください。

#### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>VPP トークンの期限が切れているか、ポータル サイトのライセンスが不足している場合のアラート <!-- 2237572 -->
Volume Purchase Program (VPP) を使用して、DEP 登録時にポータル サイトを事前プロビジョニングする場合、Intune では、VPP トークンの有効期限が近づいている場合やポータル サイトのライセンスが不足している場合にアラートが表示されます。

### <a name="macos-device-enrollment-program-support-for-apple-school-manager-accounts---3006133---"></a>Apple School Manager アカウントに対する macOS Device Enrollment Program のサポート <!--3006133 -->
Intune では、macOS デバイスで Apple School Manager アカウントに対する Device Enrollment Program の使用がサポートされるようになりました。  詳しくは、「[Device Enrollment Program または Apple School Manager を使用して macOS デバイスを自動登録する](device-enrollment-program-enroll-macos.md)」をご覧ください。

### <a name="new-intune-device-subscription-sku---3312071--"></a>Intune デバイスの新しいサブスクリプション <!--3312071-->
企業でのデバイスの管理コストの削減に役立つ、デバイスに基づく新しいサブスクリプション SKU がご利用いただけるようになりました。 この Intune デバイス SKU は、月単位でのデバイスごとのライセンスです。 価格はライセンス プログラムによって変わります。 これは、Microsoft 365 管理センターを通して直接入手することも、[Enterprise Agreement](https://www.microsoft.com/licensing/licensing-programs/enterprise?activetab=enterprise-tab:primaryr2) (EA)、[Microsoft Products and Services Agreement](https://www.microsoft.com/licensing/mpsa/default) (MPSA)、[Microsoft Open Agreement](https://partner.microsoft.com/licensing/licensing-agreements)、および[クラウド ソリューション プロバイダー](https://www.microsoftpartnercommunity.com/t5/Partnership-101/What-is-the-Cloud-Solution-Provider-CSP-program/td-p/2453) (CSP) を通して入手することもできます。

### <a name="device-management"></a>デバイス管理

#### <a name="temporarily-pause-kiosk-mode-on-android-devices-to-make-changes----3041935---"></a>Android デバイスで変更を行うためのキオスク モードの一時停止 <!-- 3041935 -->
IT 管理者は、マルチアプリ キオスク モードで使用している Android デバイスの変更が必要になることがあります。 この更新には、IT 管理者が PIN を使用してキオスク モードを一時的に停止し、デバイス全体にアクセスすることができる、新しいマルチアプリ キオスクの設定が含まれます。
キオスクの設定については、[Android エンタープライズ デバイスの制限](device-restrictions-android-for-work.md)に関するページをご覧ください。

#### <a name="enable-virtual-home-button-on-android-enterprise-kiosk-devices-----3042021---"></a>Android エンタープライズ キオスク デバイスでの仮想ホーム ボタンの有効化  <!-- 3042021 -->
新しい設定により、ユーザーは、デバイスのソフトキー ボタンをタップして、マルチアプリ キオスク デバイスの Managed Home Screen アプリと他の割り当て済みアプリを切り替えることができるようになります。 この設定は、ユーザーのキオスク アプリが戻るボタンに適切に応答しない状況で特に役に立ちます。 この設定は、企業所有の単一ユーザー Android デバイスに対して構成することができます。 **[仮想ホーム ボタン]** を有効または無効にするには、Azure portal で Intune に移動し、[デバイス構成] を選択します。 現在のデバイス構成プロファイルを選択するか、新しいプロファイルを作成してキオスク設定を編集します。
キオスクの設定については、[Android エンタープライズ デバイスの制限](device-restrictions-android-for-work.md)に関するページをご覧ください。

<!-- ########################## -->
## <a name="week-of-november-12-2018"></a>2018 年 11 月 12 日の週

### <a name="network-access-control-nac-support-for-citrix-sso-for-ios----3259404---"></a>iOS 用 Citrix SSO に向けたネットワーク アクセス制御 (NAC) のサポート <!-- 3259404 -->

Citrix によって Citrix ゲートウェイの更新プログラムがリリースされ、Intune で iOS 用 Citrix SSO のネットワーク アクセス制御 (NAC) を使用できるようになりました。 Intune で VPN プロファイル内にデバイス ID を含めることを選択し、このプロファイルを iOS デバイスにプッシュすることができます。 この機能を使用するには、Citrix ゲートウェイに対する最新の更新プログラムをインストールする必要があります。

追加の要件など、NAC の使用に関する詳細については、[iOS デバイスに対する VPN 設定の構成](vpn-settings-ios.md#base-vpn-settings)に関する記事をご覧ください。 

<!-- ########################## -->
## <a name="week-of-november-5-2018"></a>2018 年 11 月 5 日の週

### <a name="support-for-ios-12-oauth-in-ios-email-profiles---2155106---"></a>iOS 電子メール プロファイルでの iOS 12 OAuth のサポート <!--2155106 -->

Intune の iOS 電子メール プロファイルでは、iOS 12 Open Authorization (OAuth) がサポートされています。 この機能を確認するには、新しいプロファイルを作成するか (**[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** >  プラットフォームで **[iOS]** > プロファイルの種類で **[電子メール]**)、既存の iOS 電子メール プロファイルを更新します。 ユーザーに既にデプロイされているプロファイルで OAuth を有効にした場合、ユーザーは再認証し、電子メールをもう一度ダウンロードすることを求められます。

[iOS での電子メール プロファイル](email-settings-ios.md)に関するページには、電子メール プロファイルでの OAuth の使用に関する詳細情報があります。

### <a name="autopilot-support-for-hybrid-azure-active-directory-joined-devices-preview----1048100--"></a>ハイブリッド Azure AD 参加済みデバイスに対する Autopilot のサポート (プレビュー) <!-- 1048100-->
Autopilot を使用してハイブリッド Azure AD 参加済みデバイスを設定できるようになります。 ハイブリッド Autopilot 機能を使用するには、デバイスを組織のネットワークに参加させる必要があります。 詳しくは、「[Intune と Windows Autopilot を使用してハイブリッド Azure AD 参加済みデバイスをデプロイする](windows-autopilot-hybrid.md)」をご覧ください。
この機能は、今後数日にわたってユーザー ベース全体にロールアウトされます。 そのため、自分のアカウントにロールアウトされるまで、以下の手順を実行できない可能性があります。

<!-- ########################## -->
## <a name="week-of-october-29-2018"></a>2018 年 10 月 29 日の週

### <a name="app-management"></a>アプリ管理

#### <a name="require-non-biometric-pin-after-a-specified-timeout----1506985---"></a>指定したタイムアウト後に生体認証以外の PIN を要求する <!-- 1506985 -->
管理者指定のタイムアウト後に生体認証以外の PIN を要求することにより、Intune では、企業データ アクセス用の生体認証 ID の使用を制限することで、モバイル アプリケーション管理 (MAM) が有効になっているアプリのセキュリティが強化されます。 この設定は、Touch ID (iOS)、Face ID (iOS)、Android バイオメトリック、またはその他の将来の生体認証方法に依存して APP/MAM が有効なアプリケーションにアクセスするユーザーに影響します。 これらの設定により、Intune 管理者は、ユーザー アクセスをいっそうきめ細かく制御し、複数のフィンガープリントまたは他の生体認証アクセス方法を使うデバイスによって不適切なユーザーに会社のデータが公開されるのを防ぐことができます。 Azure Portal で **Microsoft Intune** を開きます。 **[クライアント アプリ]** > **[アプリ保護ポリシー]** > **[ポリシーの追加]** > **[設定]** の順に選択します。 特定の設定の **[アクセス]** セクションを探します。 アクセスの設定については、「[iOS の設定](app-protection-policy-settings-ios.md#access-requirements)」および「[Android の設定](app-protection-policy-settings-android.md#access-requirements)」をご覧ください。

#### <a name="intune-app-data-transfer-settings-on-ios-mdm-enrolled-devices----2244713---"></a>iOS MDM に登録されたデバイスに対する Intune APP データ転送設定 <!-- 2244713 -->
登録されたユーザーの ID (ユーザー プリンシパル名 (UPN) とも呼ばれます) を指定することにより、iOS MDM に登録されたデバイスに対する Intune APP データ転送設定の制御を区別することができます。 IntuneMAMUPN を使用しない管理者に、動作の変更は表示されなくなります。 この機能が使用できるようになると、登録されたデバイス上でのデータ転送動作を制御するために IntuneMAMUPN を使用する管理者は、新しい設定を確認し、必要に応じて、自分の APP 設定を更新する必要があります。

#### <a name="windows-10-win32-apps----2617325---"></a>Windows 10 Win32 アプリ <!-- 2617325 -->
デバイスのすべてのユーザー用にアプリをインストールするのではなく、個別のユーザーに対するユーザー コンテキストにインストールされるように、Win32 アプリを構成できます。

#### <a name="windows-win32-apps-and-powershell-scripts----2617330---"></a>Windows Win32 アプリと PowerShell スクリプト <!-- 2617330 -->
エンド ユーザーは、Win32 アプリをインストールしたり、PowerShell スクリプトを実行したりするために、デバイスにログインする必要がなくなります。 

#### <a name="troubleshooting-client-app-installation----1363711---"></a>クライアント アプリのインストールのトラブルシューティング <!-- 1363711 -->
**[トラブルシューティング]** ブレードの **[アプリのインストール]** 列を調べることで、クライアント アプリのインストールの成功をトラブルシューティングできます。 **[トラブルシューティング]** ブレードを表示するには、Intune ポータルで **[ヘルプとサポート]** の **[トラブルシューティング]** を選択します。

### <a name="device-configuration"></a>デバイス構成

#### <a name="network-access-control-support-on-ios-vpn-clients----1333693---"></a>iOS VPN クライアントでのネットワーク アクセス制御のサポート <!-- 1333693 -->
この更新では、Cisco AnyConnect、F5 Access、Citrix SSO for iOS 用の VPN 構成プロファイルを作成するときに、ネットワーク アクセス制御 (NAC) を有効にするための新しい設定があります。 この設定では、デバイスの NAC ID を VPN プロファイルに含めることができます。 現時点では、この新しい NAC ID をサポートする VPN クライアントまたは NAC パートナー ソリューションはありませんが、サポートされるようになったら[サポートのブログ投稿](ttps://aka.ms/iOS12_and_vpn)でお知らせします。

NAC を使用するには、以下のことが必要です。
1. デバイス ID を VPN プロファイルに含めることを Intune に許可します
2. NAC プロバイダーから直接提供されるガイダンスを使用して、NAC プロバイダーのソフトウェア/ファームウェアを更新します

iOS VPN プロファイルでのこの設定については、「[Microsoft Intune で iOS デバイスに対する VPN 設定を構成する](vpn-settings-ios.md)」をご覧ください。 ネットワーク アクセス制御について詳しくは、「[ネットワーク アクセス制御 (NAC) と Intune の統合](network-access-control-integrate.md)」をご覧ください。 

適用対象: iOS

#### <a name="remove-an-email-profile-from-a-device-even-when-theres-only-one-email-profile----1818139---"></a>メール プロファイルが 1 つだけの場合でも、デバイスからメール プロファイルを削除する <!-- 1818139 -->
以前は、電子メール プロファイルが 1 つしかない*場合*、デバイスからその電子メール プロファイルを削除することはできませんでした。 今回の更新では、この動作が変更されました。 デバイス上に 1 つしかない電子メール プロファイルでも削除できるようになりました。 詳細については、「[Microsoft Intune で電子メールの設定を構成する方法](email-settings-configure.md)」をご覧ください。

#### <a name="powershell-scripts-and-aad----2309469---"></a>PowerShell スクリプトと AAD <!-- 2309469 -->
Intune 内の PowerShell スクリプトは、AAD デバイスのセキュリティ グループを対象にすることができます。

#### <a name="new-required-password-type-default-setting-for-android-android-enterprise---2649963---"></a>Android および Android エンタープライズでの [必要なパスワードの種類] の新しい既定値の設定<!-- 2649963 -->
新しいコンプライアンス ポリシーを作成すると (**[Intune]** > **[デバイスのポリシー準拠]** > **[ポリシー]** > **[ポリシーの作成]** > **[Android]**、または [プラットフォーム] > [システム セキュリティ] の **[Android エンタープライズ]**)、**[必要なパスワードの種類]** の既定値が変更されます。

開始:デバイスの既定値:最小数の数字

適用対象:Android、Android Enterprise

これらの設定については、[Android](compliance-policy-create-android.md) および [Android エンタープライズ](compliance-policy-create-android-for-work.md)のページをご覧ください。

#### <a name="use-a-pre-shared-key-in-a-windows-10-wi-fi-profile----2662938---"></a>Windows 10 Wi-Fi プロファイル内で事前共有キーを使用する <!-- 2662938 -->
この更新では、事前共有キー (PSK) を WPA/WPA2-パーソナル セキュリティ プロトコルと一緒に使用することで、Windows 10 向け Wi-Fi 構成プロファイルを認証できるようになります。 また、2018 年 10 月更新の Windows 10 上のデバイスに対して従量制課金接続のコストの構成を指定することもできます。

現時点では、Wi-Fi プロファイルをインポートするか、またはカスタム プロファイルを作成して事前共有キーを使用する必要があります。 [Windows 10 向けの Wi-Fi 設定](wi-fi-settings-windows.md)に関するページに現在の設定が一覧されています。 

#### <a name="remove-pkcs-and-scep-certificates-from-your-devices----3218390---"></a>デバイスから PKCS および SCEP 証明書を削除する <!-- 3218390 -->
一部のシナリオでは、グループからポリシーを削除したり、構成またはコンプライアンスの展開を削除したり、既存の SCEP プロファイルまたは PKCS プロファイルを管理者が更新したりした場合でも、PKCS 証明書および SCEP 証明書がデバイス上に残りました。 今回の更新ではこの動作が変更されます。 PKCS 証明書および SCEP 証明書がデバイスから削除されるシナリオと、証明書がデバイス上に残るシナリオが存在します。 各シナリオについては、「[Microsoft Intune で SCEP 証明書と PKCS 証明書を削除する](remove-certificates.md)」をご覧ください。

#### <a name="use-gatekeeper-on-macos-devices-for-compliance----2504381---"></a>コンプライアンスのために macOS デバイスでゲートキーパーを使用する <!-- 2504381 -->
この更新には、デバイスのコンプライアンスを評価するための macOS ゲートキーパーが含まれています。 ゲートキーパーの正しい設定については、「[Intune で macOS デバイス用のデバイス コンプライアンス ポリシーを追加する](compliance-policy-create-mac-os.md)」をご覧ください。


### <a name="device-enrollment"></a>デバイスの登録

#### <a name="enrollment-abandonment-report----1382924---"></a>登録の破棄に関するレポート <!-- 1382924 -->
破棄された登録の詳細を示す新しいレポートを使用できます。**[デバイスの登録]** > **[モニター]** の順に移動します。 詳しくは、「[ポータル サイトの破棄レポート](enrollment-report-company-portal-abandon.md)」をご覧ください。

#### <a name="new-azure-active-directory-terms-of-use-feature----2870393---"></a>新しい Azure Active Directory Terms of Use 機能 <!-- 2870393 -->
Azure Active Directory では、既存の Intune の使用条件の代わりに使用できる terms of use 機能が用意されます。 Azure AD terms of use 機能では、どの使用条件をどのタイミングで表示するかについての柔軟性が高くなり、ローカライズのサポートが強化され、使用条件の表示方法をより細かく制御でき、レポート機能が改善されています。 Azure AD terms of use 機能を使用するには、Enterprise Mobility + Security E3 スイートにも含まれている Azure Active Directory Premium P1 が必要です。 詳しくは、「[ユーザー アクセスに関する会社の使用条件を管理する](terms-and-conditions-create.md)」をご覧ください。

#### <a name="android-device-owner-mode-support---3188762--"></a>Android デバイス所有者モードのサポート <!--3188762-->
Samsung Knox Mobile Enrollment について、Android デバイス所有者管理モードへのデバイスの登録を Intune がサポートするようになりました。 WiFi または移動体通信ネットワークのユーザーは、初めてデバイスをオンにしたときに、ほんの数タップで登録できます。 詳しくは、「[Samsung の Knox Mobile Enrollment を使用して Android デバイスを自動的に登録する](android-samsung-knox-mobile-enroll.md)」をご覧ください。

### <a name="device-management"></a>デバイス管理
#### <a name="new-settings-for-software-updates------1907869---"></a>ソフトウェア更新プログラムの新しい設定   <!-- 1907869 -->  
- 最新のソフトウェア更新プログラムのインストールを完了するのに必要な再起動に関して、エンドユーザーに警告するための通知を構成できるようになりました。   
- 勤務時間外に実行される再起動に対して表示する再起動警告メッセージを構成できるようになりました。これにより、BYOD シナリオがサポートされます。

#### <a name="group-windows-autopilot-enrolled-devices-by-correlator-id----2075110---"></a>Windows Autopilot に登録されたデバイスを correlator ID によってグループ化する <!-- 2075110 -->
Configuration Manager で [既存デバイス向け Autopilot](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430) を使用することによって登録するとき、correlator ID による Windows デバイスのグループ化が Intune によってサポートされます。 correlator ID は、Autopilot 構成ファイルのパラメーターです。 Intune では [Azure AD デバイス属性 enrollmentProfileName](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#using-attributes-to-create-rules-for-device-objects) が等しい "OfflineAutopilotprofile-<correlator ID>" に自動的に設定されます。 これにより、オフライン Autopilot 登録用の enrollmentprofileName 属性を介して、correlator ID に基づく任意の Azure AD 動的グループを作成することができます。 詳しくは、「[既存のデバイス向けの Windows Autopilot](enrollment-autopilot.md#windows-autopilot-for-existing-devices)」をご覧ください。

#### <a name="intune-app-protection-policies----2984657---"></a>Intune のアプリ保護ポリシー <!-- 2984657 -->
Intune アプリ保護ポリシーを使用すると、Microsoft Outlook や Microsoft Word など、Intune で保護されているアプリに対するさまざまなデータ保護設定を構成できます。 [iOS](app-protection-policy-settings-ios.md) と [Android](app-protection-policy-settings-android.md) 両方でのこれらの設定のルック アンド フィールが、個々の設定を見つけやすいように変更されました。 ポリシー設定にはカテゴリが 3 つあります。
- **データ再配置** - このグループには、切り取り、コピー、貼り付け、名前を付けて保存の制限など、データ損失防止 (DLP) コントロールが含まれます。 これらの設定によって、アプリでユーザーがデータを操作する方法が決定されます。
- **アクセス要件** - このグループには、エンド ユーザーが仕事でアプリにアクセスする方法を決定するアプリ別の PIN オプションが含まれます。  
- **条件付き起動** - このグループには、最小 OS 設定、脱獄またはルート化されたデバイスの検出、オフライン猶予期間などの設定が含まれます。  
  
設定の機能は変更されていませんが、ポリシー作成フローで作業するときに、設定を見つけやすくなります。

### <a name="intune-apps"></a>Intune アプリ

#### <a name="intune-will-support-a-maximum-package-size-of-8-gb-for-lob-apps----1727158---"></a>Intune でサポートされる LOB アプリの最大パッケージ サイズが 8 GB になる <!-- 1727158 -->
Intune では、基幹業務 (LOB) アプリの最大パッケージ サイズが 8 GB に増加します。 詳しくは、「[Microsoft Intune にアプリを追加する](apps-add.md)」をご覧ください。

#### <a name="add-custom-brand-image-for-company-portal-app----1916266---"></a>ポータル サイト アプリ用のカスタム ブランド イメージを追加する <!-- 1916266 -->
Microsoft Intune 管理者は、iOS ポータル サイト アプリ内のユーザーのプロファイル ページに背景イメージとして表示されるカスタム ブランド イメージをアップロードできるようになります。 ポータル サイト アプリの構成方法の詳細については、「[Microsoft Intune ポータル サイト アプリを構成する方法](company-portal-app.md)」を参照してください。

#### <a name="intune-will-maintain-the-office-localized-language-when-updating-office-on-end-users-machines----2971030---"></a>エンドユーザーのコンピューター上で Office を更新するとき、Office のローカライズされた言語は Intune によって維持される <!-- 2971030 -->
エンドユーザーのコンピューターに Office が Intune によってインストールされる場合、エンド ユーザーには前の .MSI Office インストールで使用していたのと同じ言語パックが自動的に提供されます。 詳しくは、「[Microsoft Intune で Windows 10 デバイスに Office 365 アプリを割り当てる](apps-add-office365.md)」をご覧ください。

### <a name="monitor-and-troubleshoot"></a>監視とトラブルシューティング

#### <a name="new-intune-support-experience-in-the-microsoft-365-device-management-portal----3076965---"></a>Microsoft 365 デバイス管理ポータルでの新しい Intune サポート エクスペリエンス <!-- 3076965 -->
[Microsoft 365 デバイス管理ポータル]( http://devicemanagement.microsoft.com)での Intune の新しいヘルプとサポート エクスペリエンスがロールアウトされています。 新しいエクスペリエンスでは、自分の言葉で問題を説明し、トラブルシューティングの分析情報と Web ベースの修復コンテンツを受け取ることができます。 これらの解決策は、ユーザーの照会により、ルール ベースの機械学習アルゴリズムを使用して提供されます。  

問題固有のガイダンスに加えて、新しいケース作成ワークフローを使用して、メールまたは電話でサポート ケースを開くこともできます。  

ロールアウトの一部であるお客様の場合、ヘルプとサポートを開いたコンソールの領域に基づいて事前選択されているオプションの静的セットである現在のヘルプとサポート エクスペリエンスが、この新しいエクスペリエンスに置き換えられます。  

*この新しいヘルプとサポート エクスペリエンスは、全部ではなく一部のテナントにロールアウトされており、デバイス管理ポータルで使用できます。この新しいエクスペリエンスの参加者は、利用可能な Intune テナントからランダムに選択されます。ロールアウトが拡張されると、新しいテナントが追加されます。*  

詳細については、「Microsoft Intune のサポートを受ける方法」の「[新しいヘルプとサポート エクスペリエンス](get-support.md#help-and-support-experience)」を参照してください。  

### <a name="powershell-module-for-intune--preview-available----951068---"></a>Intune 用の PowerShell モジュール – プレビュー版 <!-- 951068 -->
Microsoft Graph を通じて Intune API のサポートを提供する新しい PowerShell モジュールのプレビュー版が、[GitHub]( https://aka.ms/intunepowershell) で利用可能になりました。 このモジュールの使用方法について詳しくは、その場所にある README ファイルをご覧ください。 


<!-- ########################## -->
## <a name="week-of-october-15-2018"></a>2018 年 10 月 15 日の週

### <a name="pin-prompt-when-you-change-fingerprints-or-face-id-on-an-ios-device-----2637704----"></a>iOS デバイス上での指紋または Face ID の変更時の PIN プロンプト  <!-- 2637704  -->
iOS デバイス上での生体認証の変更後、ユーザーに PIN の入力が求められるようになりました。 これには、登録済みの指紋や Face ID の変更が含まれます。 プロンプトのタイミングは、*[アクセス要件を再確認するまでの時間 (分)]* の構成によって異なります。  PIN が設定されていない場合は、ユーザーに設定を求められます。 
 
この機能は iOS でのみ使用可能で、iOS 向け Intune App SDK のバージョン 9.0.1 以降を統合するアプリケーションの参加が必要です。 SDK の統合は、対象のアプリケーション上で動作を適用するために必要です。 この統合は、ローリング方式で行われ、特定のアプリケーション チームに依存します。 参加するアプリケーションには、WXP、Outlook、Managed Browser、Yammer などが含まれます。


<!-- ########################## -->
## <a name="week-of-october-1-2018"></a>2018 年 10 月 1 日の週

### <a name="app-management"></a>アプリ管理

#### <a name="access-to-key-profile-properties-using-the-company-portal-app----772203---"></a>ポータル サイト アプリを使用したキーのプロファイル プロパティへのアクセス <!-- 772203 -->
エンド ユーザーがポータル サイト アプリからキー アカウントのプロパティと、パスワード リセットなどのアクションにアクセスできるようになりました。 

#### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>iOS でのアプリ設定によりサード パーティ製キーボードをブロックできる <!-- 1248481 -->
Intune 管理者は、iOS デバイスで、ポリシーによって保護されているアプリ内の組織データにアクセスするときのサード パーティ製キーボードの使用をブロックできます。 サード パーティ製キーボードをブロックするようにアプリケーション保護ポリシー (APP) が設定されていると、デバイス ユーザーは、サード パーティ製キーボードを使って初めて企業データを操作するときに、メッセージを受け取ります。 ネイティブ キーボード以外のすべてのオプションはブロックされ、デバイスのユーザーに表示されません。 デバイス ユーザーにこのダイアログ メッセージが表示されるのは 1 回だけです。 

#### <a name="user-account-access-of-intune-apps-on-managed-android-and-ios-devices----1248496---"></a>管理対象の Android デバイスと iOS デバイスでの Intune アプリのユーザー アカウント アクセス <!-- 1248496 -->
Microsoft Intune 管理者は、マネージド デバイス上の Microsoft Office アプリケーションにどのユーザー アカウントを追加するかを制御することができます。 許可されている組織ユーザー アカウントのみにアクセスを制限したり、登録済みデバイス上の個人アカウントをブロックしたりできます。 

#### <a name="outlook-ios-and-android-app-configuration-policy---1828527---"></a>iOS と Android 向けの Outlook アプリの構成ポリシー <!--1828527 -->
基本認証と ActiveSync プロトコルを活用するオンプレミス ユーザーのために、iOS と Android 向けの Outlook アプリの構成ポリシーを作成できるようになりました。 追加の構成設定は iOS と Android 向けの Outlook に対して有効になったときに追加されます。

#### <a name="office-365-pro-plus-language-packs----1833450---"></a>Office 365 Pro Plus 言語パック <!-- 1833450 -->
Intune 管理者は、Intune によって管理されている Office 365 Pro Plus アプリに追加の言語を展開することができます。 使用可能な言語のリストには、言語パックの **種類** (コア、部分、校正) が含まれます。 Azure Portal で、**[Microsoft Intune]** > **[クライアント アプリ]** > **[アプリ]** > **[追加]** の順に選びます。 **[アプリの追加]** ブレードの **[アプリの種類]** 一覧で、**[Office 365 スイート]** の **[Windows 10]** を選びます。 **[アプリ スイートの設定]** ブレードで **[言語]** を選びます。

####  <a name="windows-line-of-business-lob-apps-file-extensions----1884873---"></a>Windows 基幹業務 (LOB) アプリのファイル拡張子 <!-- 1884873 -->
Windows LOB アプリのファイル拡張子に、*.msi*、*.appx*、*.appxbundle*、*.msix*、および *.msixbundle* が含まれるようになりました。 Microsoft Intune にアプリを追加するには、**[クライアント アプリ]** > **[アプリ]** > **[追加]** の順に選択します。 **[アプリの追加]** ウィンドウが表示され、そこで **[アプリの種類]** を選択できます。 Windows LOB アプリの場合は、アプリの種類として **[基幹業務]** アプリを選び、**[アプリのパッケージ ファイル]** を選択して、適切な拡張子を持つインストール ファイルを入力します。

#### <a name="windows-10-app-deployment-using-intune----2309001---"></a>Intune を使用する Windows 10 アプリの展開 <!-- 2309001 -->
管理者は Intune を利用することで、基幹業務 (LOB) と Microsoft Store for Business アプリの既存サポートを基盤に、組織の既存アプリケーションの多くを Windows 10 デバイスのエンド ユーザーにデプロイできます。 管理者は、MSI、Setup.exe、MSP など、さまざまな形式で Windows 10 ユーザー用のアプリケーションを追加、インストール、アンインストールできます。 Intune は要件ルールを評価してからダウンロードとインストールを開始し、Windows 10 Action Center を利用して状態や再起動の必要性をエンド ユーザーに通知します。 この機能によって、このワークロードを Intune やクラウドに移行することに関心がある組織に対してブロックが効果的に解除されます。 この機能は現在パブリック プレビューの段階にあり、これから数か月の間に重要な新機能を追加する予定です。 

#### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>Web データ用のアプリ保護ポリシー (APP) 設定 <!-- 2662995 -->
Android デバイスと iOS デバイスの両方での Web コンテンツに対する APP ポリシー設定は、http リンクと https Web リンクの両方の処理、ならびに iOS ユニバーサル リンクおよび Android アプリ リンクを介したデータ転送の処理をより適切に行えるように更新されます。 

#### <a name="end-user-device-and-app-content-menu----2771453---"></a>エンド ユーザー デバイスとアプリのコンテンツのメニュー <!-- 2771453 -->
エンド ユーザーはデバイス上のコンテキスト メニューとアプリを使用して、デバイスの名前変更、準拠状況の確認などの一般的なアクションをトリガーできるようになりました。 

#### <a name="windows-company-portal-keyboard-shortcuts----2771518---"></a>Windows ポータル サイトのキーボード ショートカット <!-- 2771518 -->
エンドユーザーは、Windows ポータル サイトでキーボード ショートカット (アクセラレータ) を使用してアプリとデバイスのアクションをトリガーできるようになりました。

### <a name="device-configuration"></a>デバイス構成

#### <a name="create-dns-suffixes-in-vpn-configuration-profiles-on-devices-running-windows-10---1333668---"></a>Windows 10 を実行するデバイスの VPN 構成プロファイルで DNS サフィックスを作成する<!-- 1333668 -->
VPN デバイス構成プロファイルを作成するとき (**[デバイス構成]**、**[プロファイル]**、**[プロファイルの作成]** の順に選択し、プラットフォームに **[Windows 10 以降]** を選択し、プロファイルの種類に **[VPN]** を選択します)、DNS 設定を入力します。 この更新プログラムでは、Intune で **DNS サフィックス**を複数入力することもできるようになりました。 DNS サフィックスを使用する場合は、完全修飾ドメイン名 (FQDN) ではなく、短い名前を使用してネットワーク リソースを検索できます。 この更新プログラムでは、Intune で DNS サフィックスの順序を変更することもできます。
[Windows 10 VPN 設定](vpn-settings-windows-10.md#dns-settings)によって、現在の DNS 設定が一覧表示されます。
適用対象:Windows 10 デバイス

#### <a name="support-for-always-on-vpn-for-android-enterprise-work-profiles----1333705---"></a>Android エンタープライズ作業プロファイル向けの常時 VPN のサポート <!-- 1333705 -->
この更新プログラムでは、管理対象の作業プロファイルが与えられた Android エンタープライズ デバイスで常時 VPN 接続を使用できます。 常時 VPN 接続では接続状態が常に維持されるか、ユーザーが自分のデバイスをロックしたとき、デバイスが再起動したとき、ワイヤレス ネットワークに変更があったとき、すぐに再接続されます。 接続を "ロックダウン" モードにすることもできます。このモードでは、VPN 接続が有効になるまですべてのネットワーク トラフィックがブロックされます。
**[デバイス構成]**、**[プロファイル]**、**[プロファイルの作成]** の順に選択し、プラットフォームに **[Android エンタープライズ]** を選択し、**[デバイスの制限]** を選択し、設定に **[接続]** を選択することで常時 VPN を有効にできます。

#### <a name="issue-scep-certificates-to-user-less-devices----1744554---"></a>ユーザーのいないデバイスに SCEP 証明書を発行する <!-- 1744554 -->
現在のところ、証明書はユーザーに発行されます。 この更新プログラムでは、キオスクのようなユーザーのいないデバイスも含め、デバイスに SCEP 証明書を発行できます (**[デバイス構成]**、**[プロファイル]**、**[プロファイルの作成]** の順に選択し、プラットフォームに **[Windows 10 以降]** を選択し、プロファイルに **[SCEP 証明書]** を選択します)。 その他の更新プログラム:
- SCEP プロファイルの**サブジェクト** プロパティがカスタム テキストボックスになり、新しい変数を含めることができます。 
- SCEP プロファイルの**サブジェクト代替名 (SAN)** プロパティが表形式になり、新しい変数を含めることができます。 この表では、管理者は属性を追加し、カスタム テキストボックスに値を入力できます。 SAN では次の属性がサポートされます。 
  - DNS
  - 電子メール アドレス
  - UPN

  これらの新しい変数は、カスタム値ボックスに静的テキストで追加できます。 たとえば、`DNS = {{AzureADDeviceId}}.domain.com` という DNS 属性を追加できます。

  > [!NOTE]
  > SAN の静的テキストの場合、中かっこ { }、セミコロン ;、パイプ記号 | は使用できません。 `Subject` または `Subject alternative name` に受け取らせるには、中かっこで囲む新しいデバイスの証明書変数を 1 つに限る必要があります。 

新しいデバイスの証明書変数:  

```
"{{AAD_Device_ID}}",
"{{Device_Serial}}",
"{{Device_IMEI}}",
"{{SerialNumber}}",
"{{IMEINumber}}",
"{{AzureADDeviceId}}",
"{{WiFiMacAddress}}",
"{{IMEI}}",
"{{DeviceName}}",
"{{FullyQualifiedDomainName}}",
"{{MEID}}",
```

> [!NOTE]
>  - `{{FullyQualifiedDomainName}}` は Windows とドメインに参加しているデバイスでのみ機能します。 
>  -  サブジェクトまたは SAN の IMEI、シリアル番号、完全修飾ドメイン名などのデバイスのプロパティをデバイス証明書に指定する場合、これらのプロパティは、デバイスにアクセスできる人物が偽装する可能性があることに注意してください。 

[[SCEP 証明書プロファイルを作成する]](certificates-scep-configure.md#create-a-scep-certificate-profile) には、SCEP 構成プロファイルの作成時、現在の変数が一覧表示されます。 

適用対象:Windows 10 以降と iOS、Wi-Fi でサポート。

#### <a name="remotely-lock-uncompliant-devices----2064495---"></a>非準拠デバイスのリモート ロック <!-- 2064495 -->
デバイスが非準拠のとき、そのデバイスをリモートでロックするアクションをコンプライアンス ポリシーで作成できます。 Intune で **[デバイスのポリシー準拠]** を選択して新しいポリシーを作成するか、既存のポリシーを選択し、**[プロパティ]** を選択します。 **[コンプライアンス非対応に対するアクション]**、**[追加]** の順に選択し、デバイスのリモート ロックを選択します。
サポート対象: 
- Android
- iOS
- macOS
- Windows 10 Mobile 
- Windows Phone 8.1 以降 

#### <a name="windows-10-and-later-kiosk-profile-improvements-in-the-azure-portal----2748224---"></a>Azure portal で Windows 10 以降のキオスク プロファイルを改善 <!-- 2748224 -->
この更新プログラムでは、Windows 10 キオスク デバイスの構成プロファイルが次のように改善されています (**[デバイス構成]**、**[プロファイル]**、**[プロファイルの作成]** の順に選択し、プラットフォームに **[Windows 10 以降]** を選択し、プロファイルの種類に **[キオスク プレビュー]** を選択します)。 
- 現在のところ、同じデバイスで複数のキオスク プロファイルを作成できます。 この更新プログラムで Intune はデバイスあたりキオスク プロファイルを 1 つだけサポートするようになります。 1 台のデバイスに複数のキオスク プロファイルが必要な場合は、カスタム URI を使用できます。
- **マルチアプリ キオスク** プロファイルでは、アプリケーション グリッドの**スタート メニュー レイアウト**でアプリケーション タイルのサイズと順序を選択できます。 さらにカスタマイズする場合、続けて XML ファイルをアップロードできます。
- キオスク ブラウザーの設定が**キオスク**設定に移動します。 現在のところ、Azure portal には**キオスク Web ブラウザー**設定に独自のカテゴリがあります。
適用対象:Windows 10 以降




### <a name="device-enrollment"></a>デバイスの登録

#### <a name="apply-autopilot-profile-to-enrolled-win-10-devices-not-already-registered-for-autopilot----1558983---"></a>Autopilot に関してまだ登録されていない登録 Win 10 デバイスに Autopilot プロファイルを適用する <!-- 1558983 -->
Autopilot に関してまだ登録されていない登録 Win 10 デバイスに Autopilo プロファイルを適用できます。 Autopilot プロファイルで **[すべての対象デバイスを Autopilot に変換する]** オプションを選択し、非 Autopilot デバイスを Autopilot デプロイ サービスに自動登録します。 登録が処理されるまで 48 時間待ちます。 デバイスが登録解除されリセットされると、Autopilot によってそのデバイスがプロビジョニングされます。

#### <a name="create-and-assign-multiple-enrollment-status--page-profiles-to-azure-ad-groups----2526564---"></a>登録ステータス ページ プロファイルを複数作成し、Azure AD グループに割り当てる <!-- 2526564 -->
登録ステータス ページ プロファイルを複数[作成し、Azure AD グループに割り当てる](windows-enrollment-status.md)ことができるようになりました。

#### <a name="migration-from-device-enrollment-program-to-apple-business-manager-in-intune---2748613--"></a>Intune で Device Enrollment Program から Apple Business Manager に移行する <!--2748613-->
Apple Business Manager (ABM) は Intune で動作します。Device Enrollment Program (DEP) から ABM にアカウントをアップグレードできます。 Intune でのプロセスは同じです。 DEP から ABM に Apple をアップグレードするには、[ https://support.apple.com/en-us/HT208817]( https://support.apple.com/en-us/HT208817) に移動します。

### <a name="alert-and-enrollment-status-tabs-on-the-device-enrollment-overview-page---2748656--"></a>デバイス登録概要ページのアラートと登録ステータスのタブ <!--2748656-->
デバイス登録概要ページでは、アラートや登録エラーが別々のタブに表示されるようになりました。

### <a name="device-management"></a>デバイス管理

#### <a name="restricts-apps-and-block-access-to-company-resources-on-android-devices----2451462----"></a>Android デバイスでアプリを制限し、会社のリソースへのアクセスをブロックする <!-- 2451462  -->  
**[デバイス コンプライアンス]**、**[ポリシー]**、**[ポリシーの作成]**、**[Android]**、**[システム セキュリティ]** の順に選択すると、*[デバイス セキュリティ]* セクションの下に **[制限付きアプリ]** という新しい設定が表示されます。 **[制限付きアプリ]** 設定ではコンプライアンス ポリシーが使用され、特定のアプリがデバイスにインストールされている場合、会社のリソースへのアクセスがブロックされます。 制限付きアプリケーションがデバイスから削除されるまで、デバイスは非準拠と見なされます。
適用対象: 
- Android

<!-- ########################### -->
## <a name="notices"></a>通知

[!INCLUDE [Intune notices](./includes/intune-notices.md)]
