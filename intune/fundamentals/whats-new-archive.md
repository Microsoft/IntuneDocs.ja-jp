---
title: Microsoft Intune の過去数か月の新機能 - Azure | Microsoft Docs
titleSuffix: ''
description: Intune の新機能に関するページの過去の通知を確認する
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/5/2019
ms.topic: archived
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 9ba01d60-4a03-4e3e-9aba-8be905c0054c
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4a9454d11fd1209e715cbcb1e9d2ce7aae4a003c
ms.sourcegitcommit: 2506cdbfccefd42587a76f14ee50c3849dad1708
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 01/11/2020
ms.locfileid: "75886049"
---
# <a name="whats-new-in-the-microsoft-intune---previous-months"></a>Microsoft Intune の新機能 (過去数か月)

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

<!-- ########################## -->
## <a name="april-2019"></a>2019 年 4 月

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>アプリ管理
#### <a name="user-experience-update-for-the-company-portal-app-for-ios---2536024---"></a>iOS 用ポータル サイト アプリに関するユーザー エクスペリエンスの更新プログラム<!-- 2536024 -->
iOS デバイス用ポータル サイト アプリのホーム ページが再設計されました。 この変更によって、ホーム ページでは iOS UI パターンにより適切に従うようになり、アプリと電子ブックの検出可用性も向上しました。

#### <a name="changes-to-company-portal-enrollment-for-ios-12-device-users--3448635---"></a>iOS 12 デバイス ユーザー用ポータル サイトの登録の変更<!--3448635 -->
Apple iOS 12.2 でリリースされた MDM 登録変更に合わせて、iOS 用ポータル サイトの登録画面と手順が更新されました。 更新されたワークフローでは、次のような場合にユーザーにメッセージが表示されます。  

* Safari でポータル Web サイトを開き、ポータル サイト アプリに戻る前に管理プロファイルをダウンロードできるようにする。  
* [設定] アプリを開き、デバイスに管理プロファイルをインストールする。
* ポータル サイト アプリに戻り、登録を完了する。  

更新された登録の手順と画面については、[Intune への iOS デバイスの登録](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios)に関するページを参照してください。

#### <a name="openssl-encryption-for-android-app-protection-policies---3747362---"></a>Android アプリ保護ポリシー用の OpenSSL 暗号化<!-- 3747362 -->
Android デバイスに対する Intune アプリ保護ポリシー (APP) で、FIPS 140-2 に準拠した OpenSSL 暗号化ライブラリが使用されるようになりました。 詳細については、「[Microsoft Intune の Android アプリ保護ポリシー設定](../apps/app-protection-policy-settings-android.md)」の「[暗号化](../apps/app-protection-policy-settings-android.md#encryption)」のセクションを参照してください。

#### <a name="enable-win32-app-dependencies---2617348----"></a>Win32 アプリ依存関係の有効化<!-- 2617348  -->
管理者は、Win32 アプリのインストール前に他のアプリが依存関係としてインストールされていることを要求できます。 つまり、デバイスで Win32 アプリをインストールする前に、依存するアプリをインストールする必要があります。 Intune で、 **[クライアント アプリ]**  >  **[アプリ]**  >  **[追加]** を選択して **[アプリの追加]** ブレードを表示します。 **[アプリの種類]** として **[Windows アプリ (Win32)]** を選択します。 アプリを追加した後、 **[依存関係]** を選択し、Win32 アプリをインストールする前にインストールする必要がある依存するアプリを追加できます。 詳細については、「[Intune スタンドアロン - Win32 アプリ管理](./../apps/app-management.md)」を参照してください。 

#### <a name="app-version-installation-information-for-microsoft-store-for-business-apps---3537391-----"></a>ビジネス向け Microsoft Store のアプリに関する、アプリのバージョンのインストール情報<!-- 3537391   -->
アプリ インストール レポートには、ビジネス向け Microsoft Store のアプリのバージョン情報が含まれます。 Intune で、 **[クライアント アプリ]**  >  **[アプリ]** を選択します。 **[ビジネス向け Microsoft Store アプリ]** を選択し、次に **[モニター]** セクションの **[デバイスのインストール状態]** を選択します。

#### <a name="additions-to-win32-apps-requirement-rules---3676883-----"></a>Win32 アプリ要件規則への追加<!-- 3676883   -->
PowerShell スクリプト、レジストリ値、ファイル システム情報に基づく要件規則を作成できます。 Intune で、 **[クライアント アプリ]**  >  **[アプリ]**  >  **[追加]** を選択します。 次に、 **[アプリの追加]** ブレードで **[アプリの種類]** として **[Windows アプリ (Win32)]** を選択します。  **[要件]**  >  **[追加]** を選択して追加の要件規則を構成します。 次に、 **[ファイルの種類]** 、 **[レジストリ]** 、 **[スクリプト]** のいずれかを **[要件の種類]** として選択します。 詳細については、[Win32 アプリ管理](./../apps/app-management.md)に関するページを参照してください。

#### <a name="configure-your-win32-apps-to-be-installed-on-intune-enrolled-azure-ad-joined-devices---3695227----"></a>Intune に登録された Azure AD 参加済みデバイスにインストールされるように Win32 アプリを構成する<!-- 3695227  -->
Intune に登録された Azure AD 参加済みデバイスにインストールされるように Win32 アプリを割り当てることができます。 Intune での Win32 アプリの詳細については、[Win32 アプリ管理](./../apps/app-management.md)に関するページを参照してください。

#### <a name="device-overview-shows-primary-user--3794259----"></a>デバイス概要でのプライマリ ユーザーの表示<!--3794259  -->
デバイスの概要ページに、ユーザーとデバイスのアフィニティ ユーザー (UDA) とも呼ばれるプライマリ ユーザーが表示されます。 デバイスのプライマリ ユーザーを表示するには、 **[Intune]**  >  **[デバイス]**  >  **[すべてのデバイス]** を選択し、デバイスを選びます。 プライマリ ユーザーは、 **[概要]** ページの上部近くに表示されます。

#### <a name="additional-managed-google-play-app-reporting-for-android-enterprise-work-profile-devices---4105925----"></a>Android エンタープライズ仕事用プロファイル デバイスに関するマネージド Google Play アプリの追加レポート<!-- 4105925  -->
Android エンタープライズ仕事用プロファイル デバイスに展開されたマネージド Google Play アプリについて、デバイスにインストールされているアプリの特定のバージョン番号を表示できます。 これは必須アプリのみに適用されます。  

#### <a name="ios-third-party-keyboards---4111843-----"></a>iOS サード パーティ製キーボード<!-- 4111843   -->
iOS 用の**サードパーティ製キーボード**の設定での Intune アプリ保護ポリシー (APP) のサポートは、iOS プラットフォームの変更によりサポートされなくなりました。 この設定は、Intune の管理コンソールからは構成できなくなり、Intune App SDK でクライアントに強制されなくなります。


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>デバイスの構成

#### <a name="updated-certificate-connectors---icm-113304612---"></a>更新された証明書コネクタ<!-- ICM 113304612 -->
[Intune Certificate Connector と Microsoft Intune 用 PFX 証明書コネクタ](../protect/certficates-pfx-configure.md#whats-new-for-connectors)の両方の更新プログラムをリリースしました。 新しいリリースでは、いくつかの既知の問題を修正しています。

#### <a name="set-login-settings-and-control-restart-options-on-macos-devices---1210083----"></a>macOS デバイスでログイン設定を行い、再起動オプションを制御する<!-- 1210083  -->
macOS デバイスで、デバイス構成プロファイルを作成できます ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]** > プラットフォームに **[macOS]** を選択し、プロファイルの種類に **[デバイス機能]** を選択します)。 この更新には、カスタム バナーの表示、ユーザーのサインイン方法の選択、電源設定の表示または非表示などの新しいログイン ウィンドウ設定が含まれています。

これらの設定を表示するには、[macOS デバイスの機能設定](../configuration/macos-device-features-settings.md)に関するページを参照してください。

#### <a name="configure-wifi-on-android-enterprise-device-owner-dedicated-devices-running-in-multi-app-kiosk-mode--3041940----"></a>マルチアプリ キオスク モードで実行されている Android エンタープライズのデバイスの所有者専用デバイスに対する WiFi の構成<!--3041940  -->
マルチアプリ キオスク モードで専用デバイスとして実行されている場合、Android エンタープライズのデバイスの所有者に対して設定を有効にできます。 この更新では、ユーザーが WiFi ネットワークを構成して接続できるようにすることができます ( **[Intune]**  >  **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  > プラットフォームに **[Android エンタープライズ]** > プロファイルの種類に **[デバイスの所有者のみ]、[デバイスの制限]** > **[専用デバイス]**  >  **[キオスク モード]** : **[複数アプリ]**  >  **[WiFi 構成]** )。

構成できるすべての設定を確認するには、[機能を許可または制限する Android エンタープライズ デバイスの設定](../configuration/device-restrictions-android-for-work.md)に関するページを参照してください。

適用対象:マルチアプリ キオスク モードで実行されている Android エンタープライズ専用デバイス

#### <a name="configure-bluetooth-and-pairing-on-android-enterprise-device-owner-dedicated-devices-running-in-multi-app-kiosk-mode---3041941----"></a>マルチアプリ キオスク モードで実行されている Android エンタープライズのデバイスの所有者専用デバイスに対する Bluetooth とペアリングの構成<!-- 3041941  -->
マルチアプリ キオスク モードで専用デバイスとして実行されている場合、Android エンタープライズのデバイスの所有者に対して設定を有効にできます。 この更新では、エンドユーザーが Bluetooth を有効にして Bluetooth 経由でデバイスをペアリングできるようになります ( **[Intune]**  >  **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  > プラットフォームに **[Android エンタープライズ]** > プロファイルの種類に **[デバイスの所有者のみ]、[デバイスの制限]** > **[専用デバイス]**  >  **[キオスク モード]** : **[複数アプリ]**  >  **[Bluetooth の構成]** )。

構成できるすべての設定を確認するには、[機能を許可または制限する Android エンタープライズ デバイスの設定](../configuration/device-restrictions-android-for-work.md)に関するページを参照してください。

適用対象:マルチアプリ キオスク モードで実行されている Android エンタープライズ専用デバイス

#### <a name="create-and-use-oemconfig-device-configuration-profiles-in-intune---3305883----"></a>Intune での OEMConfig デバイス構成プロファイルの作成と使用<!-- 3305883  -->
この更新では、Intune で OEMConfig を使用した Android エンタープライズ デバイスの構成がサポートされています。 具体的には、デバイス構成プロファイルを作成し、OEMConfig を使用して Android エンタープライズ デバイスに設定を適用できます ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  > プラットフォームに **[Android エンタープライズ]** )。

現在、OEM のサポートは OEM ごとになっています。 必要な OEMConfig アプリが OEMConfig アプリの一覧にない場合は、`IntuneOEMConfig@microsoft.com` にお問い合わせください。

この機能の詳細については、「[Use and manage Android Enterprise devices with OEMConfig in Microsoft Intune](../configuration/android-oem-configuration-overview.md)」(Microsoft Intune での OEMConfig を使用した Android エンタープライズ デバイスの使用と管理) を参照してください。

適用対象:Android エンタープライズ

#### <a name="windows-update-notifications---3316758-3316782----"></a>Windows Update の通知<!-- 3316758, 3316782  -->
Windows Update リングの構成に、Intune コンソール内から管理できる 2 つの*ユーザー エクスペリエンス設定*を追加しました。 次のことができるようになりました。
- ユーザーが [Windows 更新プログラムの有無をスキャン](../protect/windows-update-settings.md)することをブロックまたは許可する。
- ユーザーが表示できる [Windows Update の通知レベル](../protect/windows-update-settings.md)を管理する。

#### <a name="new-device-restriction-settings-for-android-enterprise-device-owner---3574254----"></a>Android エンタープライズのデバイスの所有者に関する新しいデバイス制限の設定<!-- 3574254  -->
Android エンタープライズ デバイスでは、機能を許可または制限したり、パスワード規則を設定したりするデバイス制限プロファイルを作成できます ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]** > プラットフォームに **[Android エンタープライズ]** を選択し、プロファイルの種類に **[デバイスの所有者のみ] > [デバイスの制限]** を選択します)。 

この更新プログラムには、新しいパスワード設定が含まれています。また、この更新プログラムによって、フル マネージド デバイス用に Google Play ストア内のアプリへのフル アクセスができます。 現在の設定一覧を確認するには、[Android エンタープライズ デバイスの機能を許可または制限する設定](../configuration/device-restrictions-android-for-work.md)に関するページを参照してください。 

適用対象:Android エンタープライズのフル マネージド デバイス

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy---3617671---"></a>Windows 10 デバイスのコンプライアンス ポリシーでの TPM チップセットのチェック<!-- 3617671 -->

この機能のリリースは遅延しており、もう少し後になる予定です。

#### <a name="updated-ui-changes-for-microsoft-edge-browser-on-windows-10-and-later-devices---3775833-----"></a>Windows 10 以降のデバイスでの Microsoft Edge ブラウザーの更新された UI の変更<!-- 3775833   -->
デバイス構成プロファイルを作成するとき、Windows 10 以降のデバイスで Microsoft Edge の機能を許可または制限することができます ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  > プラットフォームに **[Windows 10 以降]** > プロファイルの種類に **[デバイスの制限]** > **[Microsoft Edge ブラウザー]** )。 この更新では、Microsoft Edge の設定がよりわかりやすく、より簡単に理解できるようになっています。

これらの機能を表示するには、[Microsoft Edge ブラウザーのデバイス制限の設定](../configuration/device-restrictions-windows-10.md#microsoft-edge-browser)に関するページを参照してください。

適用対象:Windows 10 以降

#### <a name="expanded-support-for-android-enterprise-fully-managed-devices--preview-----3903241-3903244-3903246-----"></a>Android エンタープライズ フル マネージド デバイス向け拡張サポート (プレビュー)<!--   3903241, 3903244, 3903246   -->
引き続きパブリック プレビュー段階にある Android エンタープライズ フル マネージド デバイスのサポートを、以下を含むように拡張しました (最初の発表は 2019 年 1 月)。

- フル マネージドの専用デバイスでは、[コンプライアンス ポリシー](../protect/compliance-policy-create-android-for-work.md)を作成してパスワード規則やオペレーティング システムの要件を含めることができます ( **[デバイスのポリシー準拠]**  >  **[ポリシー]**  >  **[ポリシーの作成]**  > プラットフォームに **[Android エンタープライズ]** を選択し、プロファイルの種類に **[デバイスの所有者]** を選択します)。

  専用デバイスでは、デバイスが **[非準拠]** と表示されることがあります。 条件付きアクセスは、専用デバイスでは使用できません。 専用デバイスを割り当てられたポリシーに準拠させるためのタスクやアクションを必ず完了してください。

- [条件付きアクセス](../protect/conditional-access.md) - Android に適用される条件付きアクセスのポリシーは、Android エンタープライズ フル マネージド デバイスにも適用されます。 ユーザーは **Microsoft Intune アプリ**を使用して、自分のフル マネージド デバイスを Azure Active Directory に登録できるようになりました。 そのうえで、コンプライアンスの問題を確認して解決し、組織のリソースにアクセスします。

- 新しいエンド ユーザー アプリ (Microsoft Intune アプリ) - Android フル マネージド デバイス向けの新しいエンド ユーザー アプリがあります。**Microsoft Intune** という名前です。 この新しいアプリは軽量かつ最新のものであり、ポータル サイト アプリと同様の機能が提供されますが、フル マネージド デバイスの場合です。 詳細については、[Google Play の Microsoft Intune アプリ](https://play.google.com/store/apps/details?id=com.microsoft.intune)に関するページを参照してください。

Android のフル マネージド デバイスを設定するには、 **[デバイスの登録]**  >  **[Android の登録]**  >  **[Corporate-owned, fully managed user devices]\(会社が所有する完全に管理されたユーザー デバイス\)** に移動します。 フル マネージド Android デバイスのサポートはプレビュー段階であり、一部の Intune 機能は完全に機能しない可能性があります。  

このプレビューの詳細については、「[Microsoft Intune - Preview 2 for Android Enterprise Fully Managed devices](https://aka.ms/preview2_AE_fullymanaged)」(Microsoft Intune - Android エンタープライズ フル マネージド デバイス用プレビュー 2) のブログを参照してください。

#### <a name="use-compliance-manager-to-create-assessments-for-microsoft-intune---4404750---"></a>コンプライアンス マネージャーを使用した Microsoft Intune の評価の作成<!-- 4404750 -->

[コンプライアンス マネージャー](https://servicetrust.microsoft.com/ComplianceManager) (別の Microsoft サイトが開きます) は、Microsoft Service Trust Portal 上のワークフローベースのリスク評価ツールです。 これを使用すると、Microsoft のサービスに関連する組織の法令遵守活動の追跡、割り当て、検証を行うことができます。 Office 365、Azure、Dynamics、Professional Services、Intune の使用時に独自のコンプライアンス評価を作成できます。 Intune では、FFIEC と GDPR の 2 つの評価が利用可能です。

コンプライアンス マネージャーは、コントロールを Microsoft が管理するコントロールと、組織が管理するコントロールに分類することによって、労力を集中させるのに役立ちます。 評価の完了後、評価をエクスポートして印刷することができます。

[連邦金融機関検査協議会 (FFIEC)](https://www.microsoft.com/trustcenter/compliance/FFIEC) (別の Microsoft サイトが開きます) のコンプライアンスは、FFIEC によって発行されたオンライン バンキングのための一連の規格です。 Intune を使用する金融機関に最も必要とされる評価です。 これにより、パブリック クラウドのワークロードに関連する FFIEC サイバー セキュリティのガイドラインを満たすために、Intune がどのように役立つかが解釈されます。 Intune の FFIEC 評価は、コンプライアンス マネージャーの 2 つ目の FFIEC 評価です。

次の例で FFIEC コントロールの内訳を確認できます。 64 のコントロールが Microsoft によって管理されます。 残りの 12 のコントロールはお客様の責任となります。

![お客様のアクションと Microsoft のアクションを含む、FFIEC に関する Intune の評価のサンプルを参照してください。](./media/whats-new/intune-ffiec-assessment-status.png)

[一般データ保護規則 (GDPR)](https://www.microsoft.com/trustcenter/privacy/gdpr/gdpr-overview) (別の Microsoft サイトが開きます) は、個人の権利とデータの保護に役立つ欧州連合 (EU) の法律です。 GDPR は、プライバシー規制の遵守に役立てるために最も必要とされる評価です。 

次の例で GDPR コントロールの内訳を確認できます。 49 のコントロールが Microsoft によって管理されます。 残りの 66 のコントロールはお客様の責任となります。

![お客様のアクションと Microsoft のアクションを含む、GDPR に関する Intune の評価のサンプルを参照してください。](./media/whats-new/intune-assessment-status.png)


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>デバイスの登録

#### <a name="configure-profile-to-skip-some-screens-during-setup-assistant---2276470----"></a>セットアップ アシスタント中、一部の画面をスキップするようにプロファイルを構成する<!-- 2276470  -->
macOS 登録プロファイルを作成するとき、セットアップ アシスタントを使用中のユーザーに表示される次の画面のスキップを構成できます。
- 外観
- ディスプレイの色調
- iCloudStorage 新しいプロファイルを作成するかプロファイルを編集する場合は、選択したスキップする画面が Apple MDM サーバーと同期している必要があります。  ユーザーは、プロファイルの変更を取得するときに遅延が発生しないように、手動でのデバイスの同期を発行できます。
詳しくは、「[Device Enrollment Program または Apple School Manager を使用して macOS デバイスを自動登録する](../enrollment/device-enrollment-program-enroll-macos.md)」をご覧ください。

#### <a name="bulk-device-naming-when-enrolling-corporate-ios-devices--3566569----"></a>企業の iOS デバイスを登録するときのデバイスの一括名前付け<!--3566569  -->
Apple の会社登録方法 (DEP/ABM/ASM) のいずれかを使用する場合、受信 iOS デバイスに自動的に名前を付けるためにデバイス名の形式を設定できます。 テンプレートで、デバイスの種類とシリアル番号を含む形式を指定できます。 これを行うには、 **[Intune]**  >  **[デバイスの登録]**  >  **[Apple の登録]**  >  **[Enrollment Program トークン]**  >  **[トークンの選択]**  > **[プロファイルの作成]**  >  **[Device naming format]\(デバイスの名前付け形式\)** を選択します。 既存のプロファイルを編集できますが、新しく同期されたデバイスのみに名前が適用されます。

#### <a name="updated-default-timeout-message-on-enrollment-status-page---3959331---"></a>登録ステータス ページの更新された既定のタイムアウト メッセージ<!-- 3959331 -->
登録ステータス ページ (ESP) が ESP プロファイルに指定されたタイムアウト値を超えたときにユーザーに表示される、既定のタイムアウト メッセージを更新しました。 新しい既定のメッセージは、ユーザーに表示され、ユーザーが ESP 展開で行う次のアクションを理解するのに役立ちます。  

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>デバイス管理

#### <a name="retire-noncompliant-devices---1827291-----"></a>非準拠デバイスをインベントリから削除する<!-- 1827291   -->
この機能は遅れており、将来のリリースが予定されています。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="monitor-and-troubleshoot"></a>監視とトラブルシューティング

#### <a name="intune-data-warehouse-v10-changes-reflecting-back-to-beta---4403765---"></a>ベータに反映された Intune データ ウェアハウス V1.0 の変更<!-- 4403765 -->
V1.0 が 1808 で初めて導入されたとき、ベータ API とはいくつかの重要な点で異なっていました。 1903 では、それらの変更がベータ API バージョンに反映されます。 ベータ API バージョンを使用する重要なレポートがある場合は、破壊的な変更を回避するためにそれらのレポートを V1.0 に切り替えることを強くお勧めします。 詳細については、「[Intune データ ウェアハウス API の変更ログ](../developer/reports-changelog.md#1903-part-2)」を参照してください。

#### <a name="monitor-security-baseline-status-public-preview----3082047---"></a>セキュリティ ベースライン状態のモニター (パブリック プレビュー) <!-- 3082047 --> 
セキュリティ ベースラインのモニタリングに[カテゴリごとのビュー](../protect/security-baselines-monitor.md#per-category-view)を追加しました (セキュリティ ベースラインは引き続きプレビュー段階です)。 カテゴリごとのビューには、ベースラインの各カテゴリと、そのカテゴリの各状態グループに分類されるデバイスの割合が表示されます。 個々のカテゴリに一致しない、構成が間違っている、または適用されないデバイスの数を把握できるようになりました。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>ロール ベースのアクセス制御

#### <a name="scope-tags-for-apple-vpp-tokens--2371886----"></a>Apple VPP トークンのスコープ タグ<!--2371886  -->
Apple VPP トークンにスコープ タグを追加できるようになりました。 同じスコープ タグを割り当てられたユーザーだけが、そのタグを使用して Apple VPP トークンにアクセスできます。 そのトークンを使用して購入した VPP アプリと電子ブックにスコープ タグが継承されます。 スコープ タグの詳細については、[RBAC とスコープ タグの使用](scope-tags.md)に関するページを参照してください。

<!-- ########################## -->
## <a name="march-2019"></a>2019 年 3 月

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>アプリ管理
#### <a name="deploy-microsoft-visio-and-microsoft-project---3725386----"></a>Microsoft Visio と Microsoft Project の展開<!-- 3725386  -->
Microsoft Intune を使用して、Windows 10 デバイスに Microsoft Visio Pro for Office 365 と Microsoft Project Online デスクトップ クライアントを独立したアプリとして展開できるようになりました (これらのアプリのライセンスを所有している場合)。 Intune で、 **[クライアント アプリ]**  >  **[アプリ]**  >  **[追加]** を選択して **[アプリの追加]** ブレードを表示します。 **[アプリの追加]** ブレードで、 **[アプリの種類]** として **[Windows 10]** を選択します。 次に、 **[アプリ スイートの構成]** を選択してインストールするアプリを選びます。 Windows 10 デバイス用 Office 365 アプリの詳細については、「[Microsoft Intune で Windows 10 デバイスに Office 365 アプリを割り当てる](../apps/apps-add-office365.md)」を参照してください。

#### <a name="microsoft-visio-pro-for-office-365-product-name-change---3593653----"></a>Microsoft Visio Pro for Office 365 製品名の変更<!-- 3593653  -->
**Microsoft Visio Pro for Office 365** は、**Microsoft Visio Online プラン 2** と呼ばれるようになりました。  Microsoft Visio の詳細については、「[Visio Online プラン 2](https://products.office.com/visio/visio-online-plan-2)」を参照してください。 Windows 10 デバイス用 Office 365 アプリの詳細については、「[Microsoft Intune で Windows 10 デバイスに Office 365 アプリを割り当てる](../apps/apps-add-office365.md)」を参照してください。

#### <a name="intune-app-protection-policy-app-character-limit-setting---3291302----"></a>Intune アプリ保護ポリシー (APP) の文字制限の設定<!-- 3291302  -->
Intune 管理者は、Intune APP の **[他のアプリとの間で切り取り、コピー、貼り付けを制限する]** ポリシー設定の例外を指定できます。  管理者は、マネージド アプリから切り取りまたはコピーできる文字数を指定できます。 この設定により、[他のアプリとの間で切り取り、コピー、貼り付けを制限する] 設定に関係なく、指定した文字数を任意のアプリと共有できます。 Android 用 Intune ポータル サイト アプリのバージョンは、バージョン 5.0.4364.0 またはそれ以降である必要があることに注意してください。 詳細については、[iOS のデータの保護](../apps/app-protection-policy-settings-ios.md#data-protection)、[Android のデータの保護](../apps/app-protection-policy-settings-android.md#data-protection)、および[クライアント アプリの保護ログのレビュー](../apps/app-protection-policy-settings-log.md#app-protection-policy-settings)に関するページを参照してください。

#### <a name="office-deployment-tool-odt-xml-for-office-proplus-deployment---3192477-----"></a>Office 展開ツール (ODT) の Office ProPlus 展開用 XML<!-- 3192477   -->
Intune 管理コンソールで Office Pro Plus のインスタンスを作成するときに、Office 展開ツール (ODT) XML を提供できるようになります。 これにより、既存の Intune の UI オプションによってニーズが満たされない場合に、より大きなカスタマイズが可能になります。 詳細については、「[Microsoft Intune で Windows 10 デバイスに Office 365 アプリを割り当てる](../apps/apps-add-office365.md)」と「[Office 展開ツールのオプションの構成](https://docs.microsoft.com/DeployOffice/configuration-options-for-the-office-2016-deployment-tool)」を参照してください。

#### <a name="app-icons-will-now-be-displayed-with-an-automatically-generated-background---1429026----"></a>自動的に生成される背景でのアプリ アイコンの表示<!-- 1429026  -->
Windows ポータル サイト アプリで、アプリのアイコンが、アイコンの主調色に基づいて自動生成される背景で表示されます (主調色を検出できた場合)。 適用できる場合は、アプリ タイルで以前表示されていた灰色の枠線が、この背景によって置き換えられます。 この変更は、10.3.3451.0 より後のバージョンのポータル サイトでユーザーに表示されます。

#### <a name="install-available-apps-using-the-company-portal-app-after-windows-bulk-enrollment---2751523-----"></a>Windows 一括登録後にポータル サイト アプリを使用して利用可能なアプリをインストールする<!-- 2751523   -->
[Windows 一括登録](../enrollment/windows-bulk-enroll.md) (プロビジョニング パッケージ) を使用して Intune に登録されている Windows デバイスは、ポータル サイト アプリを使用して、使用可能なアプリをインストールできるようになります。 ポータル サイト アプリの詳細については、[手動での Windows 10 ポータル サイトの追加](../apps/store-apps-company-portal-app.md)に関するページと、「[Microsoft Intune ポータル サイト アプリを構成する方法](../apps/company-portal-app.md)」を参照してください。

#### <a name="the-microsoft-teams-app-can-be-selected-as-part-of-the-office-app-suite---3828932----"></a>Microsoft Teams アプリを Office アプリ スイートの一部として選択できる<!-- 3828932  -->
Microsoft Teams アプリを Office Pro Plus アプリ スイートのインストールの一部として含めるか除外することができます。 この機能は、Office Pro Plus のビルド番号 16.0.11328.20116 以降で使用できます。 インストールを完了するには、サインアウトしてからデバイスにサインインする必要があります。 Intune で、 **[クライアント アプリ]**  >  **[アプリ]**  >  **[追加]** を選択します。 **[Office 365 スイート]** アプリの種類の 1 つを選択し、次に **[アプリ スイートの構成]** を選択します。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>デバイスの構成

#### <a name="automatically-start-an-app-when-running-multiple-apps-in-kiosk-mode-on-windows-10-and-later-devices---2351390---"></a>Windows 10 以降のデバイスのキオスク モードで複数のアプリを実行しているときに、アプリを自動的に開始する<!-- 2351390 -->

Windows 10 以降のデバイスでは、デバイスをキオスク モードで実行し、多くのアプリを実行できます。 この更新には、 **[自動起動]** 設定があります ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  > プラットフォームに **[Windows 10 以降]** > プロファイルの種類に **[キオスク]** > **[複数アプリのキオスク]** )。 この設定を使用して、ユーザーがデバイスにサインインしたときにアプリを自動的に起動できます。

すべてのキオスク設定の説明を見るには、「[Intune で Windows 10 以降のデバイスをキオスクとして実行するための設定](../configuration/kiosk-settings-windows.md)」を参照してください。

適用対象:Windows 10 以降

#### <a name="operational-logs-also-show-details-on-non-compliant-devices---4063755----"></a>操作ログにも非準拠デバイスの詳細を表示<!-- 4063755  -->
Intune のログを Azure Monitor の機能にルーティングする場合、操作ログもルーティングすることができます。 この更新では、操作ログで非準拠デバイスに関する情報も提供されます。

この機能の詳細については、「[Intune でストレージ、イベント ハブ、または Log Analytics にログ データを送信する](../review-logs-using-azure-monitor.md)」を参照してください。

#### <a name="route-logs-to-azure-monitor-in-more-intune-workloads---3804627---"></a>より多くの Intune ワークロードで Azure Monitor にログをルーティングする<!-- 3804627 -->
Intune では、監査ログと操作ログを Azure Monitor のイベント ハブ、ストレージ、ログ分析にルーティングできます ( **[Intune]**  >  **[モニター]**  >  **[診断設定]** )。 この更新では、コンプライアンス、構成、クライアント アプリなど、より多くの Intune ワークロードでこれらのログをルーティングできます。

Azure Monitor へのログのルーティングの詳細については、「[Intune でストレージ、イベント ハブ、または Log Analytics にログ データを送信する](../review-logs-using-azure-monitor.md)」を参照してください。

#### <a name="create-and-use-mobility-extensions-on-android-zebra-devices-in-intune---3305880-----"></a>Intune で Android Zebra デバイス上にモビリティ拡張機能を作成して使用する<!-- 3305880   -->
この更新では、Intune で Android Zebra デバイスの構成がサポートされています。 具体的には、デバイス構成プロファイルを作成し、StageNow によって生成されたモビリティ拡張機能 (MX) プロファイルを使用して Android Zebra デバイスに設定を適用できます ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  > プラットフォームに **[Android]** を選択し、プロファイルの種類に **[MX プロファイル (Zebra のみ)]** を選択します)。

この機能の詳細については、[Intune のモビリティ拡張機能による Zebra デバイスの使用と管理](../configuration/android-zebra-mx-overview.md)に関するページを参照してください。

適用対象:Android

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>デバイス管理
#### <a name="encryption-report-for-windows-10-devices-in-public-preview---2351538---"></a>Windows 10 デバイスでの暗号化レポート (パブリック プレビュー)<!-- 2351538 -->
新しい[暗号化レポート (プレビュー)](../protect/encryption-monitor.md) を使用して、Windows 10 デバイスの暗号化の状態に関する詳細を確認できます。 利用可能な詳細には、デバイスの TPM バージョン、暗号化の準備と状態、エラー レポートなどが含まれます。  

#### <a name="access-bitlocker-recovery-keys-from-the-intune-portal-in-public-preview---2351547-----"></a>Intune ポータルからの BitLocker 回復キーへのアクセス (パブリック プレビュー)<!-- 2351547   -->
Intune を使用して、Azure Active Directory から BitLocker キー ID や BitLocker 回復キーに関する[詳細を表示](../protect/encryption-monitor.md)できるようになりました。

#### <a name="microsoft-edge-support-for-intune-scenarios-on-ios-and-android-devices---3411007---"></a>iOS および Android デバイスでの Intune シナリオに対する Microsoft Edge サポート<!-- 3411007 -->
エンドユーザー エクスペリエンスが改善されたことで、Microsoft Edge で Intune Managed Browser と同じ管理シナリオがすべてサポートされるようになります。 Intune ポリシーで有効になっている Microsoft Edge のエンタープライズ機能には、デュアル ID、アプリ保護ポリシーの統合、Azure アプリケーション プロキシの統合、マネージドのお気に入り、ホーム ページのショートカットが含まれます。 詳細については、[Microsoft Edge のサポート](../apps/app-configuration-managed-browser.md#microsoft-edge-support)に関するページを参照してください。

#### <a name="exchange-onlineintune-connector-deprecate-support-for-eas-only-devices--3105122----"></a>EAS 専用デバイスに対する Exchange Online/Intune コネクタのサポート廃止<!--3105122  -->
Intune コンソールでは、Intune コネクタを使用して Exchange Online に接続されている EAS 専用デバイスの表示と管理がサポートされなくなりました。 代わりに次のオプションがあります。
- モバイルデバイス管理 (MDM) でデバイスを登録する
- Intune App Protection ポリシーを使用してデバイスを管理する
- 「[Exchange Online のクライアントとモバイル](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/clients-and-mobile-in-exchange-online)」で説明されているように Exchange コントロールを使用する

#### <a name="search-the-all-devices-page-for-an-exact-device-by-using-name--4254930---"></a>すべてのデバイスの検索ページで [名前] を使用して正確なデバイスを探す<!--4254930 -->
正確なデバイス名を検索できるようになりました。 **[Intune]**  >  **[デバイス]**  >  **[すべてのデバイス]** に移動し、検索ボックスでデバイス名を {} で囲って完全一致を検索します。 たとえば、 **{Device12345}** のようにします。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="monitor-and-troubleshoot"></a>監視とトラブルシューティング

#### <a name="support-for-additional-connectors-on-the-tenant-status-page---3617202----"></a>テナントの状態ページでの追加のコネクタのサポート<!-- 3617202  -->
[テナントの状態ページ](../tenant-status.md)に、*Windows Defender Advanced Threat Protection* (ATP) やその他の Mobile Threat Defense コネクタなど、追加のコネクタに関する追加情報が表示されるようになりました。

#### <a name="support-for-the-power-bi-compliance-app-from-the-data-warehouse-blade-in-microsoft-intune---4260871---"></a>Microsoft Intune での Power BI コンプライアンス アプリのデータ ウェアハウス ブレードのサポート<!-- 4260871 -->
以前、 **[Intune データ ウェアハウス]** ブレードの **[Power BI ファイルのダウンロード]** リンクでは、Intune データ ウェアハウス レポート (.pbix ファイル) がダウンロードされていました。 このレポートは Power BI コンプライアンス アプリに置き換えられました。 Power BI コンプライアンス アプリには特別な読み込みまたはセットアップは必要ありません。 Power BI オンライン ポータル上で直接開き、資格情報に基づいて、お使いの Intune テナントのデータを具体的に表示します。 Intune で、[Intune] ブレードの右側にある **[Intune データ ウェアハウスの設定]** リンクを選択します。 次に **[Power BI アプリを取得する]** をクリックします。 詳細については、「[Power BI でデータ ウェアハウスに接続する](../developer/reports-proc-get-a-link-powerbi.md)」を参照してください。


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>ロール ベースのアクセス制御

#### <a name="granting-intune-read-only-access-to-some-azure-active-directory-roles---3637917----"></a>Intune の読み取り専用アクセス権を一部の Azure Active Directory ロールに付与する<!-- 3637917  -->
Intune の読み取り専用アクセス権が次の Azure AD ロールに付与されています。 Azure AD ロールで付与されたアクセス許可は、Intune ロールベース アクセス制御 (RBAC) で付与されたアクセス許可よりも優先されます。

Intune の監査データへの読み取り専用アクセス:

- コンプライアンス管理者
- コンプライアンス データ管理者

すべての Intune データへの読み取り専用アクセス:

- セキュリティ管理者
- セキュリティ オペレーター
- セキュリティ閲覧者

詳細については、[ロールベースのアクセス制御](role-based-access-control.md)に関するページを参照してください。

#### <a name="scope-tags-for-ios-app-provisioning-profiles--2934430-----"></a>iOS アプリ プロビジョニング プロファイルでのスコープのタグ<!--2934430   -->
iOS アプリ プロビジョニング プロファイルにスコープのタグを追加すると、ロールを持つユーザーのうち、そのスコープのタグも割り当てられているユーザーだけが iOS アプリ プロビジョニング プロファイルにアクセスできるようになります。 スコープのタグの詳細については、[RBAC とスコープのタグの使用](scope-tags.md)に関するページを参照してください。

#### <a name="scope-tags-for-app-configuration-policies--2371891-----"></a>アプリ構成ポリシー用のスコープのタグ<!--2371891   -->
アプリ構成ポリシーにスコープのタグを追加すると、ロールを持つユーザーのうち、そのスコープのタグも割り当てられているユーザーだけがアプリ構成ポリシーにアクセスできるようになります。 同じスコープのタグが割り当てられているアプリのみをアプリ構成ポリシーの対象にする、またはアプリ構成ポリシーと関連付けることができます。 スコープのタグの詳細については、[RBAC とスコープのタグの使用](scope-tags.md)に関するページを参照してください。

#### <a name="microsoft-edge-support-for-intune-scenarios-on-ios-and-android-devices---3411007---"></a>iOS および Android デバイスでの Intune シナリオに対する Microsoft Edge サポート<!-- 3411007 -->
Microsoft Edge で、Intune Managed Browser と同じ管理シナリオがすべてサポートされ、エンド ユーザー エクスペリエンスの機能強化が追加されます。 Intune ポリシーで有効になっている Microsoft Edge のエンタープライズ機能には、デュアル ID、アプリ保護ポリシーの統合、Azure アプリケーション プロキシの統合、マネージドのお気に入り、ホーム ページのショートカットが含まれます。 詳細については、[Microsoft Edge のサポート](../apps/app-configuration-managed-browser.md#microsoft-edge-support)に関するページを参照してください。




<!-- ########################## -->
## <a name="february-2019"></a>2019 年 2 月

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>アプリ管理
#### <a name="intune-macos-company-portal-dark-mode---3300524----"></a>Intune の macOS ポータル サイトのダーク モード<!-- 3300524  -->
Intune の macOS ポータル サイトで、macOS 用にダーク モードがサポートされるようになりました。 macOS 10.14 以降のデバイスでダーク モードを有効にすると、Intune ポータル サイトではそのモードの色に外観が調整されます。

#### <a name="intune-will-leverage-google-play-protect-apis-on-android-devices---2577355-----"></a>Android デバイスで Intune が Google Play Protect API を利用する<!-- 2577355   -->
一部の IT 管理者は、エンド ユーザーが自身の携帯電話を root 化したり脱獄させたりする可能性がある BYOD 環境に直面しています。 この行動は、悪意のないものであっても、エンド ユーザーのデバイス上にある組織のデータを保護するために設定されている多くの Intune ポリシーをバイパスする結果となります。 したがって、Intune では、登録済みのデバイスと未登録のデバイスの両方にルート化および脱獄の検出を提供しています。 このリリースでは、Intune は未登録のデバイスに対する既存のルート検出チェックに追加するため、Google Play Protect API を利用します。 Google では発生するルート検出チェックのすべてを共有してはいませんが、これらの API により、デバイスのカスタマイズ化から何らかの理由で自身のデバイスをルート化しているユーザーを検出して、古いデバイスで新しい OS の更新プログラムを取得できるようにすることを想定しています。 これにより、これらのユーザーが会社のデータにアクセスすることをブロックしたり、これらのユーザーの会社のアカウントをポリシーを有効にしたアプリからワイプしたりすることができます。 付加価値として、IT 管理者は Intune App Protection ブレード内で複数の更新されたレポートが使用できるようになります。"フラグ付きのユーザー" レポートでは、Google Play Protect の SafetyNet API スキャンにより検出されたユーザーが示されます。"潜在的に有害なアプリ" レポートでは、Google の Verify Apps API スキャンにより検出されたアプリが示されます。 この機能は Android で使用できます。

#### <a name="win32-app-information-available-in-troubleshooting-blade---2617342-----"></a>トラブルシューティング ブレードで利用可能な Win32 アプリ情報<!-- 2617342   -->
Intune のアプリの**トラブルシューティング** ブレードから、Win32 アプリのインストールのエラー ログ ファイルを収集できるようになりました。 アプリのインストールに関するトラブルシューティングについて詳しくは、「[アプリのインストールに関する問題のトラブルシューティング](./../apps/troubleshoot-app-install.md)」と「[Win32 アプリの問題をトラブルシューティングする](./../apps/troubleshoot-app-install.md#win32-app-installation-troubleshooting)」を参照してください。

#### <a name="app-status-details-for-ios-apps---3761235-----"></a>iOS アプリの状態の詳細<!-- 3761235   -->
以下に関するアプリのインストールの新しいエラー メッセージが追加されています。
- 共有 iPad に VPP アプリをインストールするときのエラー
- アプリ ストアが無効になっているときのエラー
- アプリの VPP ライセンスが見つからない
- MDM プロバイダーでシステム アプリのインストールが失敗する
- デバイスが紛失モードまたはキオスク モードの場合に、アプリのインストールが失敗する
- ユーザーが App Store にサインインしていないときに、アプリのインストールが失敗する

Intune で、 **[クライアント アプリ]**  >  **[アプリ]** > "アプリ名" > **[デバイスのインストール状態]** の順に選択します。 **[状態の詳細]** 列で新しいエラー メッセージが使用できるようになります。

#### <a name="new-app-categories-screen-in-the-company-portal-app-for-windows-10---3834780----"></a>Windows 10 用ポータル サイト アプリでの新しい [アプリのカテゴリ] 画面<!-- 3834780  -->
**[アプリのカテゴリ]** という新しい画面が追加され、Windows 10 用ポータル サイトでのアプリの参照と選択のエクスペリエンスが向上しました。 ユーザーには、 **[おすすめ]** 、 **[教育]** 、 **[生産性]** などのカテゴリに並べ替えられたアプリが表示されるようになります。 この変更は、ポータル サイト バージョン 10.3.3451.0 以降で表示されます。 新しい画面を表示するには、「[アプリの UI の新機能](whats-new-app-ui.md)」を参照してください。 ポータル サイトでのアプリの詳細については、「[デバイスにアプリをインストールして共有する](https://docs.microsoft.com/intune-user-help/install-apps-cpapp-windows)」を参照してください。  

#### <a name="power-bi-compliance-app---1455231-doc-work-item---"></a>Power BI コンプライアンス アプリ<!-- 1455231 doc-work-item -->
[Intune コンプライアンス (データ ウェアハウス)](https://aka.ms/intune/datawarehouseapi/getpowerbiapp) アプリを使用して、Power BI Online 内の Intune データ ウェアハウスにアクセスします。 この Power BI アプリを使用すると、設定を行うことも、Web ブラウザーを離れることもなく、事前に作成されたレポートにアクセスし、共有することができます。 詳細については、[変更ログ - Power BI コンプライアンス アプリ](../developer/reports-changelog.md#power-bi-compliance-app)に関するページを参照してください。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>デバイスの構成

#### <a name="powershell-scripts-can-run-in-a-64-bit-host-on-64-bit-devices---1862675-----"></a>PowerShell スクリプトが 64 ビット デバイスの 64 ビット ホストで実行できる<!-- 1862675   -->
PowerShell スクリプトをデバイス構成プロファイルに追加すると、64 ビット オペレーティング システムであっても、スクリプトは常に 32 ビットで実行されます。 この更新により、管理者はスクリプトを実行 64 ビット デバイスの 64 ビット PowerShell ホストでスクリプトを実行できます ( **[デバイス構成]**  >  **[PowerShell スクリプト]**  >  **[追加]**  >  **[構成]**  >  **[Run script in 64 bit PowerShell Host]\(64 ビット PowerShell ホストでスクリプトを実行\)** )。

PowerShell の使用に関する詳細については、[Intune での PowerShell スクリプト](../apps/intune-management-extension.md)に関するページを参照してください。

適用対象:Windows 10 以降

#### <a name="macos-users-are-prompted-to-update-their-password---1873216---"></a>macOS ユーザーにパスワードの更新を求める<!-- 1873216 -->
Intune では、macOS デバイスに対して **ChangeAtNextAuth** 設定を強制しています。 この設定は、コンプライアンス パスワード ポリシーまたはデバイス制限パスワード プロファイルが設定されているエンドユーザーとデバイスに影響します。 エンド ユーザーはスワードの更新を 1 回求められます。 このプロンプトは、デバイスへのサインインなどの認証を必要とするタスクをユーザーが初めて実行するたびに発生します。 また、キーチェーン アクセスの要求など、管理者特権が必要なことをユーザーが行うときにも、パスワードの更新を求めることができます。

管理者によって新規または既存のパスワード ポリシーが変更されると、エンド ユーザーは再度パスワードの更新を求められます。

適用対象:  
macOS

#### <a name="assign-scep-certificates-to-a-userless-macos-device---2340521------"></a>ユーザーレス macOS デバイスに SCEP 証明書を割り当てる<!-- 2340521    -->
ユーザー アフィニティのないデバイスを含む macOS デバイスにデバイス属性を使用して Simple Certificate Enrollment Protocol (SCEP) 証明書を割り当て、その証明書プロファイルを Wi-Fi または VPN プロファイルに関連付けることができます。 これにより既にあるサポートを拡張して、Windows、iOS、Android を実行する[ユーザー アフィニティのあるデバイスまたはユーザー アフィニティのないデバイスに SCEP 証明書を割り当て](../protect/certificates-profile-scep.md)済みです。  この更新では、macOS の SCEP 証明書プロファイルを構成するときに、 *[デバイス]* という証明書の種類を選択するオプションが追加されています。

適用対象:
- macOS

#### <a name="intune-conditional-access-ui-update---2432313-----"></a>Intune の条件付きアクセスの UI の更新<!-- 2432313   -->
Intune コンソール内の条件付きアクセスの UI の改善を行いました。 次の設定があります。
- Intune の "*条件付きアクセス*" ブレードを Azure Active Directory のブレードに置き換え。 これにより、Azure AD テクノロジのまま[条件付きアクセス](../protect/conditional-access.md)のすべての設定と構成に Intune コンソール内からアクセスできるようになります。 
- *[オンプレミス アクセス]* ブレードの名前を *[Exchange へのアクセス]* に変更し、 *[Exchange サービス コネクタ]* の設定をこの名前変更されたブレードに再配置しました。  この変更により、[Exchange Online とオンプレミスに関する詳細を構成および監視する](../protect/exchange-connector-install.md)場所が統合されました。  

#### <a name="kiosk-browser-and-microsoft-edge-browser-apps-can-run-on-windows-10-devices-in-kiosk-mode---2935135-----"></a>キオスク ブラウザーと Microsoft Edge ブラウザー アプリを、キオスク モードの Windows 10 デバイスで実行できる<!-- 2935135   -->
キオスク モードの Windows 10 デバイスを使用して、1 つまたは多数のアプリを実行することができます。 この更新プログラムには、キオスク モードでブラウザー アプリを使用するための次のような複数の変更が含まれています。

- Microsoft Edge ブラウザーまたはキオスク ブラウザーを追加して、キオスク デバイスでアプリとして実行します ( **[デバイス構成]**  >  **[プロファイル]**  >  **[新しいプロファイル]**  >  プラットフォームに **[Windows 10 以降]** を選択し、プロファイルの種類に **[キオスク]** を選択します)。
- 新しい機能や設定を使用して、以下のことを許可または制限できます ( **[デバイス構成]**  >  **[プロファイル]**  >  **[新しいプロファイル]**  >  プラットフォームに **[Windows 10 以降]** を選択し、プロファイルの種類に **[デバイスの制限]** を選択します)。

- Microsoft Edge ブラウザー:
  - Microsoft Edge キオスク モードを使用する
  - アイドル時間が経過した後、ブラウザーを更新する

- お気に入りおよび検索:
  - 検索エンジンへの変更を許可する

これらの設定の一覧については、次を参照してください。

- [Windows 10 以降のデバイスをキオスクとして実行するための設定](../configuration/kiosk-settings-windows.md)
- [Microsoft Edge ブラウザー デバイスの制限](../configuration/device-restrictions-windows-10.md#microsoft-edge-browser)
- [お気に入りと検索のデバイスの制限](../configuration/device-restrictions-windows-10.md##favorites-and-search)

適用対象:Windows 10 以降

#### <a name="new-device-restriction-settings-for-ios-and-macos-devices---3448774-----"></a>iOS および macOS デバイスの新しいデバイス制限の設定<!-- 3448774   -->
iOS および macOS を実行するデバイスで一部の設定と機能を制限することができます ( **[デバイス構成]**  >  **[プロファイル]**  >  **[新しいプロファイル]**  >  プラットフォームに **[iOS]** または **[macOS]** を選択し、プロファイルの種類に **[デバイスの制限]** を選択します)。 この更新プログラムにより、制御可能な機能と設定がさらに追加されます。これには、画面の表示時間の設定、eSIM 設定とセルラー プランの変更が含まれ、iOS デバイスではその他にもあります。 また、ユーザーへのソフトウェア更新プログラムの表示の遅延や、macOS デバイスでのコンテンツ キャッシュのブロックがあります。

制限可能な機能と設定を確認するには、次を参照してください。

- [iOS デバイスの制限設定](../configuration/device-restrictions-ios.md)
- [macOS デバイスの制限設定](../configuration/device-restrictions-macos.md)

適用対象:

- iOS
- macOS

#### <a name="kiosk-devices-are-now-called-dedicated-devices-on-android-enterprise-devices---3598402-----"></a>Android エンタープライズ デバイスで "キオスク" デバイスが "専用デバイス" と呼ばれるようになった<!-- 3598402   -->
Android の用語に合わせるため、Android エンタープライズ デバイスの**キオスク**は、**専用デバイス**に変更されました ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]** プラットフォームに **[Android エンタープライズ]** を選択し、 **[デバイスの所有者のみ]**  >  **[デバイスの制限]**  >  **[専用デバイス]** を選択します)。

使用可能な設定を確認するには、[機能を許可または制限するデバイスの設定](../configuration/device-restrictions-android-for-work.md#dedicated-device-settings)に関するページを参照してください。

適用対象:  
Android エンタープライズ

#### <a name="safari-and-delaying-user-software-update-visibility-ios-settings-are-moving-in-the-intune-ui---3640850-3803313-----"></a>Safari の設定と、iOS のソフトウェア更新プログラムのユーザーへの表示を遅らせる設定を Intune UI の中で移動<!-- 3640850, 3803313   -->
iOS デバイスの場合、Safari を設定し、ソフトウェア更新プログラムを構成できます。 この更新プログラムでは、これらの設定が Intune UI のさまざまな部分に移動されています。

- Safari の設定は、 **[Safari]** ( **[デバイス構成]**  >  **[プロファイル]**  >  **[新しいプロファイル]**  > プラットフォームに **[iOS]** を選択し、プロファイルの種類に **[デバイスの制限]** を選択します) から **[[組み込みアプリ]](../configuration/device-restrictions-ios.md#built-in-apps)** に移動されました。
- **[Delaying user software update visibility for supervised iOS devices]\(監視対象の iOS デバイスのソフトウェア更新プログラムのユーザーへの表示を遅らせる\)** 設定 ( **[ソフトウェア更新プログラム]**  >  **[iOS のポリシーを更新する]** ) は、 **[デバイスの制限]**  >  **[[全般]](../configuration/device-restrictions-ios.md#general)** に移動されています。  既存のポリシーへの影響の詳細については、[iOS ソフトウェア更新プログラム](../protect/software-updates-ios.md#configure-the-policy)に関するページを参照してください。

設定の一覧については、次を参照してください。

- [iOS デバイスの制限](../configuration/device-restrictions-ios.md) 
- [iOS ソフトウェア更新プログラム](../protect/software-updates-ios.md)

この機能は、以下に適用されます。

- iOS

#### <a name="enabling-restrictions-in-the-device-settings-is-renamed-to-screen-time-on-ios-devices---3699164-----"></a>iOS デバイスで、[デバイス設定での制限の有効化] 設定が [画面の表示時間] に名前が変更される<!-- 3699164   -->
監視対象の iOS デバイスで、 **[デバイス設定での制限の有効化]** を構成することができます ( **[デバイス構成]**  >  **[プロファイル]**  >  **[新しいプロファイル]**  >  プラットフォームに **[iOS]** を選択し、プロファイルの種類に **[デバイスの制限]** を選択し、 **[全般]** を選択します)。 この更新プログラムでは、この設定の名前が **[画面の表示時間 (監視モードのみ)]** に変更されています。

動作は同じです。 具体的には次のとおりです。

- iOS 11.4.1 以前のバージョン: **[ブロック]** は、エンド ユーザーがデバイス設定で独自の制限を設定できないようにします。 
- iOS 12.0 以降: **[ブロック]** は、エンド ユーザーがデバイス設定 (コンテンツとプライバシーの制限を含む) で独自の**画面の表示時間**を設定できないようにします。 iOS 12.0 にアップグレードされたデバイスでは、デバイスの設定に制限のタブが表示されなくなります。 これらの設定は **[画面の表示時間]** にあります。 

設定の一覧については、[iOS デバイスの制限事項](../configuration/device-restrictions-ios.md#general)に関するページを参照してください。

適用対象:
- iOS


#### <a name="intune-powershell-module---951068----"></a>Intune PowerShell モジュール<!-- 951068  -->
Microsoft Graph を通じて Intune API のサポートを提供する PowerShell モジュールが、[Microsoft PowerShell ギャラリー](https://www.powershellgallery.com/packages/Microsoft.Graph.Intune/6.1902.1.10)で利用可能になりました。

- [このモジュールの使用方法に関する詳細](https://github.com/Microsoft/Intune-PowerShell-SDK/blob/master/README.md)
- [このモジュールを使用するシナリオの例](https://github.com/Microsoft/Intune-PowerShell-SDK/blob/master/Samples/README.md)

#### <a name="improved-support-for-delivery-optimization--3183757----"></a>配信の最適化のサポート強化<!--3183757  -->
配信の最適化を構成するための Intune でのサポートを拡張しました。 [配信の最適化設定](../configuration/delivery-optimization-settings.md)の拡張された一覧を構成し、それを Intune コンソールから直接、デバイスに対して指定することができます。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>デバイス管理

#### <a name="rename-an-enrolled-windows-device---1911112----"></a>登録済み Windows デバイスの名前変更<!-- 1911112  -->
登録済み Windows 10 デバイス (RS4 以降) の名前を変更できるようになりました。 これを行うには、 **[Intune]**  >  **[デバイス]**  >  **[すべてのデバイス]** > デバイスを選択 > **[デバイス名の変更]** の順に選択します。 この機能では、ハイブリッド Azure AD Windows デバイスの名前変更は現在サポートされていません。

#### <a name="auto-assign-scope-tags-to-resources-created-by-an-admin-with-that-scope---3173823----"></a>自動割り当てスコープにより、そのスコープを使用して管理者によって作成されたリソースにタグが割り当てられる<!-- 3173823  -->
管理者がリソースを作成するときに、管理者に割り当てられた任意のスコープのタグが自動的にこれらの新しいリソースに割り当てられます。

### <a name="monitor-and-troubleshoot"></a>監視とトラブルシューティング

#### <a name="failed-enrollment-report-moves-to-the-device-enrollment-blade---3560202----"></a>失敗した登録レポートをデバイスの登録ブレードに移動<!-- 3560202  -->
**失敗した登録**レポートは、**デバイスの登録**ブレードの **[監視]** セクションに移動されました。 2 つの新しい列 ([登録方法] と [OS のバージョン]) も追加されています。

#### <a name="company-portal-abandonment-report-renamed-to-incomplete-user-enrollments--3815076-eemiss---"></a>ポータル サイト破棄レポートの名前が不完全なユーザー登録に変更されました<!--3815076 eemiss -->
**ポータル サイト破棄**レポートの名前が**不完全なユーザー登録**に変更されました。






<!-- ########################## -->
## <a name="january-2019"></a>2019 年 1 月

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>アプリ管理

#### <a name="intune-app-pin---2298397---"></a>Intune アプリの PIN<!-- 2298397 -->
IT 管理者は、エンド ユーザーによる Intune アプリ PIN の変更が必要になるまでの待機日数を構成できるようになりました。 新しい設定では、*その日数後に PIN がリセットされます*。この設定を使用するには、Azure portal で **[Intune]**  >  **[クライアント アプリ]**  >  **[アプリ保護ポリシー]**  >  **[ポリシーの作成]**  >  **[設定]**  >  **[アクセス要件]** の順に選択します。 この機能は、[iOS](../apps/app-protection-policy-settings-ios.md) デバイスと [Android](../apps/app-protection-policy-settings-android.md) デバイスで使用でき、正の整数値をサポートしています。

#### <a name="intune-device-reporting-fields---2748738---"></a>Intune のデバイス レポートのフィールド<!-- 2748738 -->
Intune では、アプリ登録 ID、Android の製造元、モデル、セキュリティ更新プログラムのバージョン、iOS のモデルなど、デバイス レポートのフィールドが提供されています。 Intune でこれらのフィールドを使用するには、 **[クライアント アプリ]**  >  **[アプリの保護状態]** を選択して、 **[アプリ保護レポート: iOS、Android]** を選択します。 さらに、これらのパラメーターは、デバイス製造元 (Android) の**許可**リスト、デバイス モデル (Android および iOS) の**許可**リスト、および Android セキュリティ修正プログラムの最小バージョンの設定を構成するのに役立ちます。

#### <a name="toast-notifications-for-win32-apps---3136566-----"></a>Win32 アプリのトースト通知<!-- 3136566   -->
アプリ割り当てごとに、エンド ユーザーにトースト通知が表示されるのを抑制することができます。 Intune で **[クライアント アプリ]**  >  **[アプリ]** > アプリを選択 > **[割り当て]**  >  **[グループを含める]** を選択します。

#### <a name="intune-app-protection-policies-ui-update---3251427----"></a>Intune アプリ保護ポリシーの UI の更新<!-- 3251427  -->
Intune のアプリ保護に関する設定とボタンのラベルを、理解しやすいように変更しました。 変更の一部を次に示します。  
- コントロールが、**はい** / **いいえ**から、主として**ブロック** / **許可**および**無効** / **有効**に変更されています。 ラベルも更新されています。  
- 設定は形式が変更されて、設定とそのラベルがコントロールに並べて配置されるようになり、ナビゲーションが容易になっています。

既定の設定および多くの設定は同じままですが、この変更により、ユーザーは、これまでより簡単に設定を理解し、ナビゲートし、利用して、選択したアプリ保護ポリシーを適用できます。 詳細については、[iOS の設定](../apps/app-protection-policy-settings-ios.md)と [Android の設定](../apps/app-protection-policy-settings-android.md)に関する記事をご覧ください。

#### <a name="additional-settings-for-outlook---3301182----"></a>Outlook の追加設定<!-- 3301182  -->
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
> Intune アプリ保護ポリシーを使用して企業 ID のアクセスを管理している場合は、**生体認証を要求する**オプションを有効にしないよう考慮する必要があります。 詳細については、[iOS のアクセス設定](../apps/app-protection-policy-settings-ios.md#access-requirements)および [Android のアクセス設定](../apps/app-protection-policy-settings-android.md#access-requirements)について、**アクセスのための企業認証情報の要求**に関する記事を参照してください。

詳細については、「[Microsoft Outlook の構成設定](../apps/app-configuration-policies-outlook.md)」を参照してください。

#### <a name="delete-android-enterprise-apps---1352553---"></a>Android エンタープライズ アプリを削除する<!-- 1352553 -->
Microsoft Intune から managed Google Play アプリを削除できます。 managed Google Play アプリを削除するには、Azure portal で Microsoft Intune を開き、 **[クライアント アプリ]**  >  **[アプリ]** の順に選択します。 アプリの一覧から、managed Google Play アプリの右側にある省略記号 (...) を選択し、表示された一覧で **[削除]** を選択します。 アプリの一覧からマネージド Google Play アプリを削除すると、そのマネージド Google Play アプリは自動的に未承認になります。

#### <a name="managed-google-play-app-type---1352580---"></a>managed Google Play アプリの種類<!-- 1352580 -->
**マネージド Google Play** アプリの種類では、特定の[マネージド Google Play アプリ](https://play.google.com/work/search?q=microsoft&c=apps)を Intune に追加できます。 Intune の管理者は、Intune 内で managed Google Play アプリを参照、検索、承認、同期および割り当てできるようになりました。  managed Google Play コンソールに別途移動する必要はなく、また再認証する必要もありません。  Intune で、 **[クライアント アプリ]**  >  **[アプリ]**  >  **[追加]** を選択します。 **[アプリケーションの種類]** 一覧で、アプリの種類として **[マネージド Google Play]** を選択します。

#### <a name="default-android-pin-keyboard---3802457---"></a>既定の Android PIN キーボード<!-- 3802457 -->
Android デバイスで PIN タイプが "数値" の Intune アプリ保護ポリシー (APP) PIN を設定しているエンド ユーザーの場合、以前の設計のような固定の Android キーボード UI ではなく、既定の Android キーボードが表示されるようになります。 この変更は、"数値" と "パスコード" 両方の PIN タイプについて、既定のキーボードを使用するときの動作が Android と iOS の両方で同じになるようにするために行われました。 Android での APP PIN などのエンド ユーザー アクセス設定について詳しくは、[Android のアクセス要件](../apps/app-protection-policy-settings-android.md#access-requirements)に関する記事をご覧ください。


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>デバイスの構成

#### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>管理用テンプレートがパブリック プレビューになり、専用の構成プロファイルに移動される <!-- 3322847 -->

Intune の管理用テンプレート ( **[デバイス構成]**  >  **[管理用テンプレート]** ) は現在、パブリック プレビュー段階です。 この更新プログラムでは:

- 管理用テンプレートには、Intune で管理可能な約 300 の設定が含まれます。 以前は、これらの設定はグループ ポリシー エディターにのみ存在しました。
- 管理用テンプレートはパブリック プレビューで使用できます。
- 管理用テンプレートは、 **[デバイス構成]**  >  **[管理用テンプレート]** から、 **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]** を選択し、 **[プラットフォーム]** で **[Windows 10 以降]** を選択し、 **[プロファイルの種類]** で **[管理用テンプレート]** を選択した場所に移動されています。
- レポートが有効です。

この機能の詳細については、[グループ ポリシー設定を構成するための Windows 10 テンプレート](../configuration/administrative-templates-windows.md)に関するページを参照してください。

適用対象:Windows 10 以降

#### <a name="use-smime-to-encrypt-and-sign-multiple-devices-for-a-user---1333642---"></a>S/MIME を使って暗号化し、ユーザーの複数のデバイスに署名する<!-- 1333642 -->
この更新プログラムには、新しくインポートされる証明書プロファイル ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]** 、該当するプラットフォーム、 **[PKCS のインポートされた証明書]** プロファイルの種類の順に選択) を使用する S/MIME メールの暗号化が含まれます。 Intune では、PFX 形式で証明書をインポートできます。 その後、Intune はその同じ証明書を、単一ユーザーによって登録された複数のデバイスに配信できます。 これには、次のものも含まれます。
- ネイティブ iOS メール プロファイルでは、PFX 形式でインポートされた証明書を使用する S/MIME 暗号化を有効にすることができます。
- Windows Phone 10 デバイス上のネイティブ メール アプリでは、自動的に S/MIME 証明書が使用されます。
- プライベート証明書は複数のプラットフォームに配信できます。 しかし、すべてのメール アプリで S/MIME がサポートされるわけではありません。
- 他のプラットフォームでは、S/MIME を有効にするようにメール アプリを手動で構成する必要がある場合があります。  
- S/MIME 暗号化をサポートするメール アプリでは、発行元の証明書ストアからの読み取りなど、MDM ではサポートできない方法で S/MIME メール暗号化のための証明書の検索を処理する場合があります。
この機能の詳細については、[電子メールの署名と暗号化のための S/MIME の概要](../protect/certificates-s-mime-encryption-sign.md)に関するページを参照してください。
サポート対象:Windows、Windows Phone 10、macOS、iOS、Android

#### <a name="new-options-to-automatically-connect-and-persist-rules-when-using-dns-settings-on-windows-10-and-later-devices---1333665-2999078---"></a>Windows 10 以降のデバイスで DNS 設定を使用するときに、自動的に接続してルールを保持する新しいオプション<!-- 1333665, 2999078 -->
Windows 10 以降のデバイスでは、contoso.com などのドメインを解決するための DNS サーバーのリストを含む VPN 構成プロファイルを作成できます。 この更新には、名前解決のための新しい設定が含まれます ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]** > プラットフォームとして **[Windows 10 以降]** を選択 > プロファイルの種類として **[VPN]** を選択 > **[DNS 設定]**  > **[追加]** )。 
- **自動接続**: **有効**にすると、デバイスは、入力された contoso.com などのドメインにアクセスするときに、VPN に自動的に接続します。
- **永続性**: この VPN プロファイルを使用してデバイスに接続している限り、既定で、名前解決ポリシー テーブル (NRPT) のすべてのルールがアクティブになります。 NRPT ルールでこの設定を**有効**にすると、VPN が切断されても、ルールはデバイス上でアクティブなままになります。 VPN プロファイルを削除するか、ルールを手動で削除するまで (PowerShell を使って実行できます)、ルールは保持されます。
[Windows 10 の VPN 設定](../configuration/vpn-settings-windows-10.md)に関するページでは、これらの設定について説明されています。

#### <a name="use-trusted-network-detection-for-vpn-profiles-on-windows-10-devices---1500165---"></a>Windows 10 デバイスで VPN プロファイルに対して信頼されたネットワーク検出を使用する<!-- 1500165 -->
信頼されたネットワーク検出を使用すると、ユーザーが信頼されたネットワーク上に既にいるときに、VPN プロファイルで VPN 接続が自動的に作成されるのを防ぐことができます。 この更新により、Windows 10 以降を実行するデバイスでは、DNS サフィックスを追加して信頼されたネットワーク検出を有効にすることができます ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  > プラットフォームとして **[Windows 10 以降]** > プロファイルの種類として **[VPN]** )。
[Windows 10 の VPN 設定](../configuration/vpn-settings-windows-10.md)に関するページには、現在の VPN 設定の一覧があります。

#### <a name="manage-windows-holographic-for-business-devices-used-by-multiple-users---1907917-1063203---"></a>複数のユーザーによって使用される Windows Holographic for Business デバイスを管理する<!-- 1907917, 1063203 -->
現在、共有 PC の設定は、Windows 10 デバイスと Windows Holographic for Business デバイスでカスタム OMA-URI の設定を使用して構成できます。 この更新により、共有デバイスの設定を構成するための新しいプロファイルが追加されます ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  >  **[Windows 10 以降]**  >  **[共有のマルチユーザーのデバイス]** )。
この機能の詳細については、[共有デバイスを管理するための Intune の設定](../configuration/shared-user-device-settings.md)に関するページを参照してください。
適用対象:Windows 10 以降、Windows Holographic for Business

#### <a name="new-windows-10-update-settings--2626030--2512994----"></a>新しい Windows 10 更新プログラムの設定<!--2626030  2512994  -->
[Windows 10 更新リング](../protect/windows-update-for-business-configure.md)で、次の構成を行うことができます。
- **[自動更新の動作]** - 新しいオプション *[既定にリセット]* を使用して、"*2018 年 10 月更新*" を実行している Windows 10 コンピューターで、元の自動更新設定を復元する。
- **[ユーザーによる Windows Update の一時停止をブロックする]** - コンピューターの "*設定*" から、ユーザーによる更新プログラムのインストールの一時停止を許可またはブロックできる、新しいソフトウェア更新プログラムの設定を構成する。

#### <a name="ios-email-profiles-can-use-smime-signing-and-encryption---2662949---"></a>iOS の電子メール プロファイルで S/MIME の署名と暗号化を使用できる<!-- 2662949 -->
異なる設定を含む電子メール プロファイルを作成することができます。 この更新には、iOS デバイスでのメール通信の署名と暗号化に使用できる S/MIME の設定が含まれます ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]** > プラットフォームとして **[iOS]** を選択 > プロファイルの種類として **[電子メール]** を選択)。
[iOS での電子メール構成の設定](../configuration/email-settings-ios.md)に関するページに、設定の一覧が示されています。

#### <a name="some-bitlocker-settings-support-windows-10-pro-edition---2727036---"></a>BitLocker の一部の設定で Windows 10 Pro エディションがサポートされる<!-- 2727036 -->
Windows 10 デバイスで、BitLocker などの Endpoint Protection の設定を行う構成プロファイルを作成できます。 この更新により、BitLocker の一部の設定に Windows 10 Professional エディションのサポートが追加されます。
これらの保護設定を確認するには、[Windows 10 用の Endpoint Protection 設定](../protect/endpoint-protection-windows-10.md#windows-encryption)に関するページを参照してください。

#### <a name="shared-device-configuration-is-renamed-to-lock-screen-message-for-ios-devices-in-the-azure-portal---2809362---"></a>Azure portal で iOS デバイスの共有デバイスの構成が、ロック画面メッセージに名前を変更される<!-- 2809362 -->
iOS デバイス用の構成プロファイルを作成するときに、ロック画面に特定のテキストを表示する**共有デバイス構成**の設定を追加できます。 この更新には、次の変更が含まれます。 
- Azure portal で **[共有デバイスの構成]** 設定の名前が、[Lock Screen Message (supervised only)]\(ロック画面のメッセージ (監視モードのみ)\) に変更されます ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]** > プラットフォームとして **[iOS]** を選択 > プロファイルの種類として **[デバイス機能]** を選択 > **[Lock Screen Message]\(ロック画面のメッセージ\)** )。
- ロック画面のメッセージを追加するときは、 **[資産タグ情報]** および **[ロック画面の脚注 ]** の変数として、シリアル番号、デバイス名、または別のデバイス固有値を挿入できます。 たとえば、中かっこを使用して `Device name: {{devicename}}` や `Serial number is {{serialnumber}}` などと入力できます。 [iOS トークン](../apps/app-configuration-policies-use-ios.md#tokens-used-in-the-property-list)に関するページでは、使用できるトークンの一覧が示されています。
[ロック画面にメッセージを表示するための設定](../configuration/ios-device-features-settings.md#lock-screen-message)に関するページでは、設定の一覧が示されています。

#### <a name="new-app-store-doc-viewing-gaming-device-restriction-settings-added-to-ios-devices---2827760--"></a>iOS デバイスに App Store、ドキュメント表示、ゲーム デバイスの新しい制限の設定が追加される<!-- 2827760-->
**デバイスの構成** > **プロファイル > プロファイルの** > **作成**プロファイル > の種類 > **App Store、Doc 表示、ゲーム**では、次の設定が追加されます。管理対象アプリが連絡先を**管理対象外**の連絡先に書き込むことを許可する管理されていないアプリ**が、これら**の設定を確認するには、[ [iOS デバイスの制限](../configuration/device-restrictions-ios.md#app-store-doc-viewing-gaming)] にアクセスします。

#### <a name="new-notification-hints-and-keyguard-settings-to-android-enterprise-device-owner-devices---3201839-3201843---"></a>Android エンタープライズ デバイス所有者デバイスに対する新しい通知、ヒント、キーガードの設定<!-- 3201839 3201843 -->
この更新には、デバイス所有者として実行するときの Android エンタープライズ デバイスに関するいくつかの新機能が含まれます。 これらの機能を使用するには、 **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]** に移動し、 **[プラットフォーム]** で **[Android エンタープライズ]** を選択し、 **[プロファイルの種類]** で **[デバイスの所有者のみ]**  >  **[デバイスの制限]** を選択します。

新機能は次のとおりです。

- 着信、システム アラート、システム エラーなどのシステム通知の表示を無効にします。
- 初めて開いたアプリのチュートリアルとヒントの開始をスキップすることを提案します。
- カメラ、通知、指紋によるロック解除など、高度なキーガード設定を無効にします。

これらの設定については、[Android エンタープライズ デバイスの制限の設定](../configuration/device-restrictions-android-for-work.md)に関するページを参照してください。

#### <a name="android-enterprise-device-owner-devices-can-use-always-on-vpn-connections---3202194---"></a>Android エンタープライズ デバイス所有者デバイスで、Always On VPN 接続を使用できる<!-- 3202194 -->
この更新では、Android エンタープライズ デバイス所有者デバイスで常時 VPN 接続を使用できます。 常時 VPN 接続では接続状態が常に維持されるか、ユーザーが自分のデバイスをロックしたとき、デバイスが再起動したとき、ワイヤレス ネットワークに変更があったとき、すぐに再接続されます。 接続を "ロックダウン" モードにすることもできます。このモードでは、VPN 接続が有効になるまですべてのネットワーク トラフィックがブロックされます。
**[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]** の順に選択し、プラットフォームとして **[Android エンタープライズ]** を選択し、[デバイスの所有者のみ] として **[デバイスの制限]** を選択し、 **[接続]** 設定を選択することで、常時 VPN を有効にできます。 これらの設定については、[Android エンタープライズ デバイスの制限の設定](../configuration/device-restrictions-android-for-work.md)に関するページを参照してください。

#### <a name="new-setting-to-end-processes-in-task-manager-on-windows-10-devices---3285177---"></a>Windows 10 デバイスのタスク マネージャーでプロセスを終了するための新しい設定<!-- 3285177 --> 
この更新には、Windows 10 デバイスのタスク マネージャーでプロセスを終了するための新しい設定が含まれます。 デバイス構成プロファイルを使用して ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]** > **[プラットフォーム]** で **[Windows 10]** を選択 > **[プロファイルの種類]** で **[デバイスの制限]** を選択 >  **[全般]** 設定)、この設定の許可または禁止を選択します。
これらの設定については、[Windows 10 デバイスの制限の設定](../configuration/device-restrictions-windows-10.md)に関するページを参照してください。
適用対象:Windows 10 以降

#### <a name="use-microsoft-recommended-settings-with-security-baselines-public-preview---2055484-----"></a>セキュリティ ベースラインを使って Microsoft 推奨の設定を使う (パブリック プレビュー)<!-- 2055484   -->

Intune は、セキュリティに的を絞ったその他のサービス (Windows Defender ATP や Office 365 ATP など) と統合されます。 一般的な戦略と、Microsoft 365 サービス間での結束的なエンドツーエンドのセキュリティ ワークフローをお客様から求められています。 目標としているのは、セキュリティの運用と一般的な管理者タスクをブリッジするソリューションを構築できるように戦略を調整することにあります。 Intune では、Microsoft が推奨する一連の "セキュリティ ベースライン" を公開することによって、この目標の達成を目指しています ( **[Intune]**  > **セキュリティ ベースライン**)。  管理者はこれらのベースラインから直接セキュリティ ポリシーを作成し、それを各自のユーザーにデプロイできます。 また、ご自分の組織のニーズに合わせてベスト プラクティスのレコメンデーションをカスタマイズすることもできます。 Intune では、これらのベースラインにデバイスが準拠した状態に維持されていることが確認され、管理者には準拠した状態にないユーザーまたはデバイスが通知されます。

この機能はパブリック プレビューなので、現在作成されているプロファイルは、一般提供 (GA) されるセキュリティ ベースラインのテンプレートには引き継がれません。 運用環境でこれらのプレビュー テンプレートを使用することは計画しないでください。

セキュリティ ベースラインについて詳しくは、[Intune での Windows 10 セキュリティ ベースラインの作成](../protect/security-baselines-monitor.md)に関する記事をご覧ください。

この機能は、以下に適用されます。Windows 10 以降

#### <a name="non-administrators-can-enable-bitlocker-on-windows-10-devices-joined-to-azure-ad---2147379-----"></a>管理者以外のユーザーが、Azure AD 参加済み Windows 10 デバイスで BitLocker を有効にできる<!-- 2147379   -->
Windows 10 デバイスで BitLocker の設定を有効にすると ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  > プラットフォームとして **[Windows 10 以降] を選択** > プロファイルの種類として **[Endpoint Protection]** > **[Windows 暗号化]** )、BitLocker の設定が追加されます。

この更新には、標準ユーザー (管理者以外) が暗号化を有効にするのを許可する新しい BitLocker の設定が含まれます。

設定を確認するには、[Windows 10 用の Endpoint Protection 設定](../protect/endpoint-protection-windows-10.md#windows-encryption)に関する記事を参照してください。

#### <a name="check-for-configuration-manager-compliance---2192052--eepublished----"></a>Configuration Manager コンプライアンスの確認<!-- 2192052  eepublished  -->
この更新には、新しい Configuration Manager コンプライアンス設定 ( **[デバイスのポリシー準拠]**  >  **[ポリシー]**  >  **[ポリシーの作成]**  >  **[Windows 10 以降]**  >  **[Configuration Manager のコンプライアンス]** ) が含まれます。 Configuration Manager から Intune コンプライアンスにシグナルが送信されます。 この設定を使用して、すべての Configuration Manager シグナルで "準拠" を返すように要求することができます。

たとえば、すべてのソフトウェア更新プログラムをデバイスにインストールすることを要求します。 Configuration Manager では、この要求は "インストール済み" 状態となります。 デバイス上のいずれかのプログラムが不明な状態である場合、Intune ではデバイスが非準拠となります。

この設定については、「[Configuration Manager Compliance (Configuration Manager コンプライアンス)](../protect/compliance-policy-create-windows.md#configuration-manager-compliance)」で説明されています。

適用対象:Windows 10 以降

#### <a name="customize-wallpaper-on-supervised-ios-devices-using-a-device-configuration-profile---2809324-----"></a>デバイスの構成プロファイルを使用した監視対象の iOS デバイスの壁紙のカスタマイズ<!-- 2809324   -->
iOS デバイス用のデバイス構成プロファイルを作成するときに、一部の機能をカスタマイズできます ( **[デバイスの構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  >  プラットフォームに **[iOS]** > プロファイルの種類に **[デバイス機能]** )。 この更新には新しい **[壁紙]** 設定が含まれています。これを使うと、管理者はホーム画面またはロック画面上で .png、.jpg、または .jpeg 画像を使うことができます。 これらの壁紙の設定は、監視対象のデバイスにのみ適用できます。 

これらの設定の一覧については、[iOS デバイスの機能設定](../configuration/ios-device-features-settings.md)に関する記事をご覧ください。

#### <a name="windows-10-kiosk-is-generally-available---3594661----"></a>Windows 10 キオスクの一般提供<!-- 3594661  -->
この更新では、Windows 10 以降のデバイスでのキオスク機能が一般提供 (GA) になりました。 追加および構成できるすべての設定については、[Windows 10 (およびそれ以降) のキオスク設定](../configuration/kiosk-settings.md)に関する記事をご覧ください。

#### <a name="contact-sharing-via-bluetooth-is-removed-in-device-restrictions--device-owner-for-android-enterprise---3598396-----"></a>Android エンタープライズの [デバイスの制限] > [デバイスの所有者] での [Bluetooth 経由での連絡先の共有] の削除<!-- 3598396   -->
Android エンタープライズ デバイス用にデバイスの制限プロファイルを作成した場合、 **[Bluetooth 経由での連絡先の共有 ]** 設定があります。 この更新では、 **[Bluetooth 経由での連絡先の共有]** の設定が削除されます ( **[デバイスの構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  >  プラットフォーム用の **Android エンタープライズ** > **[デバイスの制限] > プロファイルの種類の [デバイスの所有者]** > **[全般]** )。

**[Bluetooth 経由での連絡先の共有]** 設定は、Android エンタープライズのデバイス所有者の管理ではサポートされていません。 したがって、この設定が削除されると、この設定が環境で有効および構成されていた場合でもいかなるデバイスやテナントにも影響はありません。

現在の設定一覧を確認するには、[Android エンタープライズ デバイスの機能を許可または制限する設定](../configuration/device-restrictions-android-for-work.md)に関するページを参照してください。

適用対象: Android Enterprise デバイス所有者


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>デバイスの登録

#### <a name="more-detailed-enrollment-restriction-failure-messaging---3111564---"></a>より詳細な登録制限のエラー メッセージ<!-- 3111564 -->
登録の制限が満たされていないときに表示されるエラー メッセージが、より詳細になります。 これらのメッセージを見るには、 **[Intune]**  >  **[トラブルシューティング]** に移動し、[登録エラー] のテーブルを確認します。 詳細については、[登録エラーの一覧](help-desk-operators.md#enrollment-failure-reference)を参照してください。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>デバイス管理
#### <a name="preview-of-support-for-android-corporate-owned-fully-managed-devices---1574342----"></a>会社が所有する完全に管理された Android デバイスのサポートのプレビュー<!-- 1574342  -->
Intune では、フル マネージドの Android デバイス、つまりデバイスが IT によって厳格に管理され、個々のユーザーと関連付けられる、企業所有の "デバイス所有者" のシナリオがサポートされるようになりました。 これにより、管理者は、デバイス全体を管理し、仕事用プロファイルでは利用できない拡張範囲のポリシー制御を適用し、managed Google Play からのみアプリをインストールするようにユーザーを制限することができます。 詳細については、[Android フル マネージド デバイスの Intune 登録の設定](../enrollment/android-fully-managed-enroll.md)および[専用デバイスまたはフル マネージド デバイスの登録](../enrollment/android-dedicated-devices-fully-managed-enroll.md)に関するページをご覧ください。  なお、この機能はプレビュー段階です。 証明書、コンプライアンス、および条件付きのアクセスなど、一部の Intune 機能は、現在 Android の完全に管理されたユーザー デバイスでは利用できません。

#### <a name="selective-wipe-support-for-wip-without-enrollment-devices---1434452---"></a>登録なしの WIP デバイスに対する選択的ワイプのサポート<!-- 1434452 -->
登録なしの Windows Information Protection (WIP-WE) を使うと、MDM への完全な登録を必要とせずに Windows 10 デバイス上の企業データを保護することができます。 WIP-WE ポリシーを使用してドキュメントが保護されると、Intune 管理者は保護されたデータを選択的にワイプすることができます。 ユーザーとデバイスを選択してワイプ要求を送信することにより、WIP-WE ポリシーを介して保護されたデータはすべて使用できなくなります。 Azure portal 内で Intune から、 **[モバイル アプリ]**  >  **[アプリの選択的ワイプ]** の順に選択します。


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="monitor-and-troubleshoot"></a>監視とトラブルシューティング

#### <a name="tenant-status-dashboard---1124854---"></a>テナントの状態ダッシュボード<!-- 1124854 -->
新しい [[テナントの状態] ページ](tenant-status.md)では、テナントの状態および関連する詳細を 1 か所に表示できます。  このダッシュボードは、次の 4 つの領域に分かれています。
- **テナントの詳細** - テナントの名前と場所、ご利用の MDM 機関、ご利用のテナントに登録されたデバイスの総数、ご利用のライセンス数などの情報が表示されます。 このセクションには、そのテナントに対する現在のサービス リリースも示されます。
- **コネクタの状態** - 構成済みの使用可能なコネクタに関する情報が表示されるほか、まだ有効にしていないコネクタの一覧も表示できます。  
   各コネクタの現在の状態に基づいて、正常、警告、または異常を示すフラグが付けられます。 コネクタを選択してドリルスルーし、詳細を表示したり、追加情報を構成したりします。
- **Intune サービスの正常性** - ご利用のテナントでのアクティブなインシデントまたは障害に関する詳細が表示されます。 このセクション内の情報は、Office メッセージ センターから直接取得されます。
- **Intune ニュース** - テナントのアクティブなメッセージが表示されます。 メッセージには、テナントが Intune の最新の機能を受信する際の通知などが含まれます。  このセクション内の情報は、Office メッセージ センターから直接取得されます。

#### <a name="new-help-and-support-experience-in-company-portal-for-windows-10---1488939--"></a>Windows 10 用ポータル サイトの新しいヘルプとサポート エクスペリエンス<!-- 1488939-->
ポータル サイトの新しい [ヘルプとサポート] ページでは、ユーザーがアプリやアクセスの問題に対して、トラブルシューティングを行ったりヘルプを要求したりできます。 この新しいページで、エラーと診断ログの詳細を電子メールで送信し、組織のヘルプデスクの詳細を確認することができます。 また、関連する Intune ドキュメントへのリンクを含む FAQ セクションもあります。

#### <a name="new-help-and-support-experience-for-intune---3307080---"></a>Intune の新しいヘルプとサポート エクスペリエンス<!-- #3307080 -->
今後数日間で、新しいヘルプとサポート エクスペリエンスをすべてのテナントにロールアウトする予定です。 この新しいエクスペリエンスは Intune で利用でき、[Azure portal](https://portal.azure.com/) で Intune のブレードを使用しているときにアクセスできます。
新しいエクスペリエンスでは、自分の言葉で問題を説明し、トラブルシューティングの分析情報と Web ベースの修復コンテンツを受け取ることができます。 これらの解決策は、ユーザーの照会により、ルール ベースの機械学習アルゴリズムを使用して提供されます。 問題固有のガイダンスに加えて、新しいケース作成ワークフローを使用して、電子メールまたは電話でサポート ケースを開きます。 ヘルプとサポートを開いたコンソールの領域に基づいて事前選択されているオプションの静的セットである以前のヘルプとサポート エクスペリエンスが、この新しいエクスペリエンスに置き換えられます。
詳細については、「[Microsoft Intune のサポートを受ける方法](get-support.md)」を参照してください。

#### <a name="new-operational-logs-and-ability-to-send-logs-to-azure-monitor-services---3762211----"></a>新しい操作ログ、およびログを Azure Monitor サービスに送信する機能<!-- 3762211  -->
Intune には、変更が加えられるとイベントを追跡する組み込みの監査ログが備わっています。 この更新には、次の新しいログ記録機能が含まれます。 
- 登録したユーザーおよびデバイスの詳細を示す操作ログ (プレビュー) (成功および失敗した試行を含む)。
- 監査ログと操作ログは Azure Monitor に送信することができます (ストレージ アカウント、イベント ハブ、ログ分析を含む)。 これらのサービスを使うと、保存したり、Splunk や QRadar などの分析を使ったり、ログ データの視覚化を取得したりできます。

この機能について詳しくは、[Intune でのストレージ、イベント ハブ、またはログ分析へのログ データの送信](../review-logs-using-azure-monitor.md)に関する記事をご覧ください。

#### <a name="skip-more-setup-assistant-screens-on-an-ios-dep-device---2687509----"></a>iOS DEP デバイスでスキップできるセットアップ アシスタントの画面が増える<!-- 2687509  -->
現在スキップすることができる画面に加えて、ユーザーがデバイスを登録するときにセットアップ アシスタント内で次の画面をスキップするように iOS DEP デバイスを設定できます: [ディスプレイの色調]、[プライバシー]、[Android 移行]、[ホーム ボタン]、[iMessage & FaceTime]、[オンボード]、[Watch の移行]、[外観]、[画面の表示時間]、[ソフトウェア更新プログラム]、[SIM のセットアップ]。
スキップする画面を選択するには、 **[デバイスの登録]**  >  **[Apple の登録]**  >  **[Enrollment Program トークン]** に移動し、トークンを選択します。次に、 **[プロファイル]** を選択してプロファイルを選択し、 **[プロパティ]**  >  **[セットアップ アシスタントのカスタマイズ]** を選択し、スキップする画面の **[非表示]** を選択して、 **[OK]** を選択します。
新しいプロファイルを作成するかプロファイルを編集する場合は、選択したスキップする画面が Apple MDM サーバーと同期している必要があります。 ユーザーは、プロファイルの変更を取得するときに遅延が発生しないように、手動でのデバイスの同期を発行できます。

#### <a name="android-enterprise-app-we-app-deployment---1171203---"></a>Android エンタープライズ APP-WE アプリの展開<!-- 1171203 -->
登録のないアプリ保護ポリシー (APP-WE) の展開シナリオでの Android デバイスでは、マネージド Google Play を使用してストア アプリと LOB アプリをユーザーに展開できるようになりました。 具体的には、不明なソースからのインストールを許可することによってデバイスのセキュリティ状態を損なう必要がないアプリ カタログとインストール エクスペリエンスをエンド ユーザーに提供できます。 さらに、この展開シナリオでは、向上したエンド ユーザー エクスペリエンスが提供されます。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>ロール ベースのアクセス制御

#### <a name="scope-tags-for-apps---1081941---"></a>アプリのスコープ タグ<!-- 1081941 -->
ロールとアプリへのアクセスを制限するために、スコープのタグを作成できます。 アプリにスコープのタグを追加すると、ロールを持つユーザーのうち、そのスコープのタグも割り当てられているユーザーだけがアプリにアクセスできるようになります。 現在、managed Google Play から Intune に追加されたアプリや、Apple Volume Purchase Program (VPP) を使って購入されたアプリにスコープ タグを割り当てることはできません (今後のサポートが予定されています)。 詳細については、「[スコープのタグを使用してポリシーをフィルター処理する](scope-tags.md)」を参照してください。




<!-- ########################## -->
## <a name="december-2018"></a>2018 年 12 月

### <a name="app-management"></a>アプリ管理

#### <a name="updates-for-application-transport-security---748318---"></a>Application Transport Security 対応のための更新<!-- 748318 -->

Microsoft Intune では、クラス最高の暗号化を提供する、既定の状態でも安全であることを保証する、また、Microsoft Office 365 などの他の Microsoft サービスと連携することを目的に、トランスポート層セキュリティ (TLS) 1.2 以降をサポートしています。 この要件を満たすために、iOS と macOS のポータル サイトには、やはり TLS 1.2 以降が要求されている Apple の改定後の Application Transport Security (ATS) 要件が適用されます。 ATS では、HTTPS 経由で行われるアプリ通信すべてに、より厳格なセキュリティ保護が適用されます。 この変更により、iOS および macOS のポータル サイト アプリを使用している Intune ユーザーが影響を受けます。 詳しくは、[Intune サポートのブログ](https://aka.ms/compportalats)をご覧ください。

#### <a name="the-intune-app-sdk-will-support-256-bit-encryption-keys---1832174---"></a>256 ビット暗号化キーをサポートするようになる Intune App SDK<!-- 1832174 -->
アプリ保護ポリシーによって暗号化が有効化されると、Android 用 Intune App SDK では現在、256 ビット暗号化キーが使用されます。 古いバージョンの SDK を使用するコンテンツやアプリとの互換性のため、SDK では引き続き 128 ビット キーのサポートが提供されます。

#### <a name="microsoft-auto-update-version-450-required-for-macos-devices---3503442---"></a>macOS デバイスに必要な Microsoft Auto Update バージョン 4.5.0<!-- 3503442 -->
ポータル サイトおよびその他の Office アプリケーション用の更新プログラムの受信を継続するには、Intune によって管理されている macOS デバイスを Microsoft Auto Update 4.5.0 にアップグレードする必要があります。 ユーザーは自分の Office アプリに対してこのバージョンを既に使用している可能性があります。

### <a name="device-management"></a>デバイス管理

#### <a name="intune-requires-macos-1012-or-later---2827778---"></a>Intune には macOS 10.12 以降が必要<!-- 2827778 -->
Intune には、macOS バージョン 10.12 以降が必要になりました。 以前の macOS バージョンが使用されているデバイスでは、ポータル サイトを使用して Intune に登録することはできません。 サポートを受けて新しい機能を利用するには、デバイスを macOS 10.12 以降にアップグレードすると共に、ポータル サイト アプリを最新版にアップグレードする必要があります。

<!-- ########################## -->
## <a name="november-2018"></a>2018 年 11 月

### <a name="app-management"></a>アプリ管理

#### <a name="uninstalling-apps-on-corporate-owned-supervised-ios-devices---1281677---"></a>企業所有の監視対象 iOS デバイス上のアプリのアンインストール<!-- 1281677 -->
企業所有の監視対象 iOS デバイス上のアプリを削除できます。 **[アンインストール]** 割り当て種類でユーザーまたはデバイスのグループを対象とすることにより、すべてのアプリを削除できます。 個人所有または監視対象外の iOS デバイスの場合は、引き続き Intune を使用してインストールされたアプリのみを削除できます。

#### <a name="downloading-intune-win32-app-content---2617320---"></a>Intune Win32 アプリのコンテンツのダウンロード<!-- 2617320 -->
Windows 10 RS3 以降のクライアントでは、Windows 10 クライアント上の配信最適化コンポーネントを使用して、Intune Win32 アプリ コンテンツがダウンロードされます。 配信の最適化では、既定で有効になるピア ツー ピア機能が提供されます。 現在、配信の最適化は、グループ ポリシーによって構成できます。 詳しくは、[Windows 10 の配信の最適化](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization)に関するページをご覧ください。

#### <a name="end-user-device-and-app-content-menu---2771453---"></a>エンド ユーザー デバイスとアプリのコンテンツのメニュー<!-- 2771453 -->
エンド ユーザーはデバイス上のコンテキスト メニューとアプリを使用して、デバイスの名前変更、準拠状況の確認などの一般的なアクションをトリガーできるようになりました。

#### <a name="set-custom-background-in-managed-home-screen-app----3041945---"></a>Managed Home Screen アプリでのカスタム背景の設定 <!-- 3041945 -->
Android エンタープライズのマルチアプリ キオスク モード デバイス上の Managed Home Screen アプリの背景の外観をカスタマイズできる設定が追加されています。  **カスタム URL の背景**を構成するには、Azure portal で Intune に移動し、[デバイス構成] を選択します。 現在のデバイス構成プロファイルを選択するか、新しいプロファイルを作成してキオスク設定を編集します。
キオスクの設定については、[Android エンタープライズ デバイスの制限](../configuration/device-restrictions-android-for-work.md)に関するページをご覧ください。

#### <a name="app-protection-policy-assignment-save-and-apply---3104570---"></a>アプリ保護ポリシーの割り当ての保存と適用<!-- 3104570 -->
[アプリ保護ポリシーの割り当て](../apps/app-protection-policies.md)の制御が向上しました。 *[割り当て]* を選んでポリシーの割り当てを設定または編集したときは、変更を適用する前に構成を**保存する**必要があります。 対象リストまたは除外リストに変更を保存しないで、行ったすべての変更をクリアするには、 **[破棄]** を使います。  保存または破棄を必要とすることにより、意図したユーザーのみにアプリ保護ポリシーが割り当てられます。

#### <a name="new-microsoft-edge-browser-settings-for-windows-10-and-later---3174639---"></a>Windows 10 以降向けの新しい Microsoft Edge ブラウザー設定<!-- 3174639 -->
この更新には、デバイス上の Microsoft Edge ブラウザーを制御および管理するための新しい設定が含まれます。 これらの設定の一覧については、[Windows 10 (以降) に対するデバイスの制限](../configuration/device-restrictions-windows-10.md#microsoft-edge-browser)に関するページをご覧ください。

#### <a name="new-apps-support-with-app-protection-policies---3330037---"></a>アプリ保護ポリシーでの新しいアプリのサポート<!-- 3330037 -->
[Intune アプリ保護ポリシー](../apps/app-protection-policies.md)で次のアプリを管理できるようになりました。
- Stream (iOS)
- To DO (Android、iOS)
- PowerApps (Android、iOS)
- Flow (Android、iOS)

これらのアプリでも、他の Intune ポリシーで管理されたアプリと同じように、アプリ保護ポリシーを使って、企業データを保護し、データ転送を制御してください。 注:Flow がまだコンソールに表示されない場合は、アプリ保護ポリシーを作成または編集するときに Flow を追加します。 これを行うには、 **[+ その他のアプリ]** オプションを使い、入力フィールドで Flow の *[アプリ ID]* を指定します。 Android の場合は *com.microsoft.flow* を使い、iOS の場合は *com.microsoft.procsimo* を使います。


### <a name="device-configuration"></a>デバイスの構成

#### <a name="support-for-ios-12-oauth-in-ios-email-profiles--2155106---"></a>iOS 電子メール プロファイルでの iOS 12 OAuth のサポート<!--2155106 -->
Intune の iOS 電子メール プロファイルでは、iOS 12 Open Authorization (OAuth) がサポートされています。 この機能を確認するには、新しいプロファイルを作成するか ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  >  プラットフォームで **[iOS]** > プロファイルの種類で **[電子メール]** )、既存の iOS 電子メール プロファイルを更新します。 ユーザーに既にデプロイされているプロファイルで OAuth を有効にした場合、ユーザーは再認証し、電子メールをもう一度ダウンロードすることを求められます。

[iOS での電子メール プロファイル](../configuration/email-settings-ios.md)に関するページには、電子メール プロファイルでの OAuth の使用に関する詳細情報があります。

#### <a name="network-access-control-nac-support-for-citrix-sso-for-ios---3259404---"></a>iOS 用 Citrix SSO に向けたネットワーク アクセス制御 (NAC) のサポート<!-- 3259404 -->
Citrix によって Citrix ゲートウェイの更新プログラムがリリースされ、Intune で iOS 用 Citrix SSO のネットワーク アクセス制御 (NAC) を使用できるようになりました。 Intune で VPN プロファイル内にデバイス ID を含めることを選択し、このプロファイルを iOS デバイスにプッシュすることができます。 この機能を使用するには、Citrix ゲートウェイに対する最新の更新プログラムをインストールする必要があります。

追加の要件など、NAC の使用に関する詳細については、[iOS デバイスに対する VPN 設定の構成](../configuration/vpn-settings-ios.md#base-vpn-settings)に関する記事をご覧ください。 

#### <a name="ios-and-macos-version-numbers-and-build-numbers-are-shown---1892471---"></a>iOS および macOS のバージョン番号とビルド番号が表示される<!-- 1892471 -->
**[デバイスのポリシー準拠]**  >  **[デバイスのポリシー準拠]** に、iOS および macOS のオペレーティング システム バージョンが表示され、コンプライアンス ポリシーで使用できます。 この更新には、両方のプラットフォームで構成可能なビルド番号が含まれます。
セキュリティ更新がリリースされるとき、Apple は通常、バージョン番号を現状のまま残しますが、ビルド番号を更新します。 コンプライアンス ポリシーでビルド番号を使用することで、脆弱性更新がインストールされているかどうかを簡単に確認できます。
この機能を使うには、[iOS](../protect/compliance-policy-create-ios.md#device-health) および [macOS](../protect/compliance-policy-create-mac-os.md#device-properties) のコンプライアンス ポリシーをご覧ください。

#### <a name="update-rings-are-being-replaced-with-delivery-optimization-settings-for-windows-10-and-later---2753807---"></a>Windows 10 以降では、更新プログラムのリングが配信の最適化の設定に置き換えられる<!-- 2753807 -->
配信の最適化は、Windows 10 以降での新しい構成プロファイルです。 この機能では、組織内のデバイスにソフトウェア更新プログラムを配信するためのエクスペリエンスが、いっそう合理化されています。 また、この更新では、構成プロファイルを使用して新規および既存の更新プログラムのリングで設定を配信することもできます。
配信の最適化の構成プロファイルを構成するには、[Windows 10 (以降) での配信の最適化の設定](../configuration/delivery-optimization-windows.md)に関するページをご覧ください。

#### <a name="new-device-restriction-settings-added-to-ios-and-macos-devices---2827760---"></a>iOS および macOS デバイスに追加された新しいデバイス制限の設定<!-- 2827760 -->
この更新プログラムには、iOS 12 と共にリリースされた iOS および macOS デバイス用の新しい設定が含まれています。

**iOS の設定**: 
- [全般]:アプリ削除をブロックする (監視モードのみ)
- [全般]:USB 制限モードをブロックする (監視モードのみ)
- [全般]:日付と時刻自動設定を強制する (監視モードのみ)
- ［パスワード］:パスワード オートフィルをブロックする (監視モードのみ)
- ［パスワード］:パスワード近接要求をブロックする (監視モードのみ)
- ［パスワード］:パスワード共有をブロックする (監視モードのみ)

**macOS の設定**: 
- パスワード: パスワードのオートコンプリートをブロックする
- ［パスワード］:パスワード近接要求をブロックする
- パスワード: パスワードの共有をブロックする

これらの設定の詳細については、[iOS](../configuration/device-restrictions-ios.md) および [macOS](../configuration/device-restrictions-macos.md) デバイスの制限の設定を参照してください。

### <a name="device-enrollment"></a>デバイスの登録

#### <a name="autopilot-support-for-hybrid-azure-active-directory-joined-devices-preview---1048100--"></a>ハイブリッド Azure AD 参加済みデバイスに対する Autopilot のサポート (プレビュー)<!-- 1048100-->
Autopilot を使用してハイブリッド Azure AD 参加済みデバイスを設定できるようになります。 ハイブリッド Autopilot 機能を使用するには、デバイスを組織のネットワークに参加させる必要があります。 詳しくは、「[Intune と Windows Autopilot を使用してハイブリッド Azure AD 参加済みデバイスをデプロイする](../enrollment/windows-autopilot-hybrid.md)」をご覧ください。
この機能は、今後数日にわたってユーザー ベース全体にロールアウトされます。 そのため、自分のアカウントにロールアウトされるまで、以下の手順を実行できない可能性があります。

#### <a name="select-apps-tracked-on-the-enrollment-status-page---2531007---"></a>登録ステータス ページで追跡するアプリの選択<!-- 2531007 -->
[登録ステータス] ページで追跡するアプリを選択できます。 これらのアプリをインストールするまで、ユーザーはデバイスを使用できません。 詳しくは、「[登録ステータス ページを設定する](../enrollment/windows-enrollment-status.md)」をご覧ください。

#### <a name="search-for-autopilot-device-by-serial-number--2595788---"></a>シリアル番号による Autopilot デバイスの検索<!--2595788 -->
シリアル番号で Autopilot デバイスを検索できるようになりました。 これを行うには、 **[デバイスの登録]**  >  **[Windows の登録]**  >  **[デバイス]** の順に選択し、 **[シリアル番号による検索]** ボックスにシリアル番号を入力して、Enter キーを押します。

#### <a name="track-installation-of-office-proplus--2620217---"></a>Office ProPlus のインストールの追跡<!--2620217 -->
ユーザーは、[[登録ステータス] ページ](../enrollment/windows-enrollment-status.md)を使用して、[Office ProPlus](../apps/apps-add-office365.md) のインストールの進行状況を追跡できます。 詳しくは、「[登録ステータス ページを設定する](../enrollment/windows-enrollment-status.md)」をご覧ください。

#### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low---2237572---"></a>VPP トークンの期限が切れているか、ポータル サイトのライセンスが不足している場合のアラート<!-- 2237572 -->
Volume Purchase Program (VPP) を使用して、DEP 登録時にポータル サイトを事前プロビジョニングする場合、Intune では、VPP トークンの有効期限が近づいている場合やポータル サイトのライセンスが不足している場合にアラートが表示されます。

#### <a name="macos-device-enrollment-program-support-for-apple-school-manager-accounts--3006133---"></a>Apple School Manager アカウントに対する macOS Device Enrollment Program のサポート<!--3006133 -->
Intune では、macOS デバイスで Apple School Manager アカウントに対する Device Enrollment Program の使用がサポートされるようになりました。  詳しくは、「[Device Enrollment Program または Apple School Manager を使用して macOS デバイスを自動登録する](../enrollment/device-enrollment-program-enroll-macos.md)」をご覧ください。

#### <a name="new-intune-device-subscription-sku--3312071--"></a>Intune デバイスの新しいサブスクリプション<!--3312071-->
企業でのデバイスの管理コストの削減に役立つ、デバイスに基づく新しいサブスクリプション SKU がご利用いただけるようになりました。 この Intune デバイス SKU は、月単位でのデバイスごとのライセンスです。 価格はライセンス プログラムによって変わります。 これは、Microsoft 365 管理センターを通して直接入手することも、[Enterprise Agreement](https://www.microsoft.com/licensing/licensing-programs/enterprise?activetab=enterprise-tab:primaryr2) (EA)、[Microsoft Products and Services Agreement](https://www.microsoft.com/licensing/mpsa/default) (MPSA)、[Microsoft Open Agreement](https://partner.microsoft.com/licensing/licensing-agreements)、および[クラウド ソリューション プロバイダー](https://www.microsoftpartnercommunity.com/t5/Partnership-101/What-is-the-Cloud-Solution-Provider-CSP-program/td-p/2453) (CSP) を通して入手することもできます。

### <a name="device-management"></a>デバイス管理

#### <a name="temporarily-pause-kiosk-mode-on-android-devices-to-make-changes---3041935---"></a>Android デバイスで変更を行うためのキオスク モードの一時停止<!-- 3041935 -->
IT 管理者は、マルチアプリ キオスク モードで使用している Android デバイスの変更が必要になることがあります。 この更新には、IT 管理者が PIN を使用してキオスク モードを一時的に停止し、デバイス全体にアクセスすることができる、新しいマルチアプリ キオスクの設定が含まれます。
キオスクの設定については、[Android エンタープライズ デバイスの制限](../configuration/device-restrictions-android-for-work.md)に関するページをご覧ください。

#### <a name="enable-virtual-home-button-on-android-enterprise-kiosk-devices----3042021---"></a>Android エンタープライズ キオスク デバイスでの仮想ホーム ボタンの有効化 <!-- 3042021 -->
新しい設定により、ユーザーは、デバイスのソフトキー ボタンをタップして、マルチアプリ キオスク デバイスの Managed Home Screen アプリと他の割り当て済みアプリを切り替えることができるようになります。 この設定は、ユーザーのキオスク アプリが戻るボタンに適切に応答しない状況で特に役に立ちます。 この設定は、企業所有の単一ユーザー Android デバイスに対して構成することができます。 **[仮想ホーム ボタン]** を有効または無効にするには、Azure portal で Intune に移動し、[デバイス構成] を選択します。 現在のデバイス構成プロファイルを選択するか、新しいプロファイルを作成してキオスク設定を編集します。
キオスクの設定については、[Android エンタープライズ デバイスの制限](../configuration/device-restrictions-android-for-work.md)に関するページをご覧ください。




<!-- ########################## -->
## <a name="october-2018"></a>2018 年 10 月

### <a name="app-management"></a>アプリ管理

#### <a name="access-to-key-profile-properties-using-the-company-portal-app---772203---"></a>ポータル サイト アプリを使用したキーのプロファイル プロパティへのアクセス<!-- 772203 -->
エンド ユーザーがポータル サイト アプリからキー アカウントのプロパティと、パスワード リセットなどのアクションにアクセスできるようになりました。 

#### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios---1248481---"></a>iOS でのアプリ設定によりサード パーティ製キーボードをブロックできる<!-- 1248481 -->
Intune 管理者は、iOS デバイスで、ポリシーによって保護されているアプリ内の組織データにアクセスするときのサード パーティ製キーボードの使用をブロックできます。 サード パーティ製キーボードをブロックするようにアプリケーション保護ポリシー (APP) が設定されていると、デバイス ユーザーは、サード パーティ製キーボードを使って初めて企業データを操作するときに、メッセージを受け取ります。 ネイティブ キーボード以外のすべてのオプションはブロックされ、デバイスのユーザーに表示されません。 デバイス ユーザーにこのダイアログ メッセージが表示されるのは 1 回だけです。 

#### <a name="user-account-access-of-intune-apps-on-managed-android-and-ios-devices---1248496---"></a>管理対象の Android デバイスと iOS デバイスでの Intune アプリのユーザー アカウント アクセス<!-- 1248496 -->
Microsoft Intune 管理者は、マネージド デバイス上の Microsoft Office アプリケーションにどのユーザー アカウントを追加するかを制御することができます。 許可されている組織ユーザー アカウントのみにアクセスを制限したり、登録済みデバイス上の個人アカウントをブロックしたりできます。 

#### <a name="outlook-ios-and-android-app-configuration-policy--1828527---"></a>iOS と Android 向けの Outlook アプリの構成ポリシー<!--1828527 -->
基本認証と ActiveSync プロトコルを活用するオンプレミス ユーザーのために、iOS と Android 向けの Outlook アプリの構成ポリシーを作成できるようになりました。 追加の構成設定は iOS と Android 向けの Outlook に対して有効になったときに追加されます。

#### <a name="office-365-pro-plus-language-packs---1833450---"></a>Office 365 Pro Plus 言語パック<!-- 1833450 -->
Intune 管理者は、Intune によって管理されている Office 365 Pro Plus アプリに追加の言語を展開することができます。 使用可能な言語のリストには、言語パックの **種類** (コア、部分、校正) が含まれます。 Azure Portal で、 **[Microsoft Intune]**  >  **[クライアント アプリ]**  >  **[アプリ]**  >  **[追加]** の順に選びます。 **[アプリの追加]** ブレードの **[アプリの種類]** 一覧で、 **[Office 365 スイート]** の **[Windows 10]** を選びます。 **[アプリ スイートの設定]** ブレードで **[言語]** を選びます。

#### <a name="windows-line-of-business-lob-apps-file-extensions---1884873---"></a>Windows 基幹業務 (LOB) アプリのファイル拡張子<!-- 1884873 -->
Windows LOB アプリのファイル拡張子に、 *.msi*、 *.appx*、 *.appxbundle*、 *.msix*、および *.msixbundle* が含まれるようになりました。 Microsoft Intune にアプリを追加するには、 **[クライアント アプリ]**  >  **[アプリ]**  >  **[追加]** の順に選択します。 **[アプリの追加]** ウィンドウが表示され、そこで **[アプリの種類]** を選択できます。 Windows LOB アプリの場合は、アプリの種類として **[基幹業務]** アプリを選び、 **[アプリのパッケージ ファイル]** を選択して、適切な拡張子を持つインストール ファイルを入力します。

#### <a name="windows-10-app-deployment-using-intune---2309001---"></a>Intune を使用する Windows 10 アプリの展開<!-- 2309001 -->
管理者は Intune を利用することで、基幹業務 (LOB) と Microsoft Store for Business アプリの既存サポートを基盤に、組織の既存アプリケーションの多くを Windows 10 デバイスのエンド ユーザーにデプロイできます。 管理者は、MSI、Setup.exe、MSP など、さまざまな形式で Windows 10 ユーザー用のアプリケーションを追加、インストール、アンインストールできます。 Intune は要件ルールを評価してからダウンロードとインストールを開始し、Windows 10 Action Center を利用して状態や再起動の必要性をエンド ユーザーに通知します。 この機能によって、このワークロードを Intune やクラウドに移行することに関心がある組織に対してブロックが効果的に解除されます。 この機能は現在パブリック プレビューの段階にあり、これから数か月の間に重要な新機能を追加する予定です。 

#### <a name="app-protection-policy-app-settings-for-web-data---2662995---"></a>Web データ用のアプリ保護ポリシー (APP) 設定<!-- 2662995 -->
Android デバイスと iOS デバイスの両方での Web コンテンツに対する APP ポリシー設定は、http リンクと https Web リンクの両方の処理、ならびに iOS ユニバーサル リンクおよび Android アプリ リンクを介したデータ転送の処理をより適切に行えるように更新されます。 

#### <a name="end-user-device-and-app-content-menu---2771453---"></a>エンド ユーザー デバイスとアプリのコンテンツのメニュー<!-- 2771453 -->
エンド ユーザーはデバイス上のコンテキスト メニューとアプリを使用して、デバイスの名前変更、準拠状況の確認などの一般的なアクションをトリガーできるようになりました。 

#### <a name="windows-company-portal-keyboard-shortcuts---2771518---"></a>Windows ポータル サイトのキーボード ショートカット<!-- 2771518 -->
エンドユーザーは、Windows ポータル サイトでキーボード ショートカット (アクセラレータ) を使用してアプリとデバイスのアクションをトリガーできるようになりました。

#### <a name="require-non-biometric-pin-after-a-specified-timeout---1506985---"></a>指定したタイムアウト後に生体認証以外の PIN を要求する<!-- 1506985 -->
管理者指定のタイムアウト後に生体認証以外の PIN を要求することにより、Intune では、企業データ アクセス用の生体認証 ID の使用を制限することで、モバイル アプリケーション管理 (MAM) が有効になっているアプリのセキュリティが強化されます。 この設定は、Touch ID (iOS)、Face ID (iOS)、Android バイオメトリック、またはその他の将来の生体認証方法に依存して APP/MAM が有効なアプリケーションにアクセスするユーザーに影響します。 これらの設定により、Intune 管理者は、ユーザー アクセスをいっそうきめ細かく制御し、複数のフィンガープリントまたは他の生体認証アクセス方法を使うデバイスによって不適切なユーザーに会社のデータが公開されるのを防ぐことができます。 Azure Portal で **Microsoft Intune** を開きます。 **[クライアント アプリ]**  >  **[アプリ保護ポリシー]**  >  **[ポリシーの追加]**  >  **[設定]** の順に選択します。 特定の設定の **[アクセス]** セクションを探します。 アクセスの設定については、「[iOS の設定](../apps/app-protection-policy-settings-ios.md#access-requirements)」および「[Android の設定](../apps/app-protection-policy-settings-android.md#access-requirements)」をご覧ください。

#### <a name="intune-app-data-transfer-settings-on-ios-mdm-enrolled-devices---2244713---"></a>iOS MDM に登録されたデバイスに対する Intune APP データ転送設定<!-- 2244713 -->
登録されたユーザーの ID (ユーザー プリンシパル名 (UPN) とも呼ばれます) を指定することにより、iOS MDM に登録されたデバイスに対する Intune APP データ転送設定の制御を区別することができます。 IntuneMAMUPN を使用しない管理者に、動作の変更は表示されなくなります。 この機能が使用できるようになると、登録されたデバイス上でのデータ転送動作を制御するために IntuneMAMUPN を使用する管理者は、新しい設定を確認し、必要に応じて、自分の APP 設定を更新する必要があります。

#### <a name="windows-10-win32-apps---2617325---"></a>Windows 10 Win32 アプリ<!-- 2617325 -->
デバイスのすべてのユーザー用にアプリをインストールするのではなく、個別のユーザーに対するユーザー コンテキストにインストールされるように、Win32 アプリを構成できます。

#### <a name="windows-win32-apps-and-powershell-scripts---2617330---"></a>Windows Win32 アプリと PowerShell スクリプト<!-- 2617330 -->
エンド ユーザーは、Win32 アプリをインストールしたり、PowerShell スクリプトを実行したりするために、デバイスにログインする必要がなくなります。 

#### <a name="troubleshooting-client-app-installation---1363711---"></a>クライアント アプリのインストールのトラブルシューティング<!-- 1363711 -->
**[トラブルシューティング]** ブレードの **[アプリのインストール]** 列を調べることで、クライアント アプリのインストールの成功をトラブルシューティングできます。 **[トラブルシューティング]** ブレードを表示するには、Intune ポータルで **[ヘルプとサポート]** の **[トラブルシューティング]** を選択します。

### <a name="device-configuration"></a>デバイスの構成

#### <a name="create-dns-suffixes-in-vpn-configuration-profiles-on-devices-running-windows-10---1333668---"></a>Windows 10 を実行するデバイスの VPN 構成プロファイルで DNS サフィックスを作成する<!-- 1333668 -->
VPN デバイス構成プロファイルを作成するとき ( **[デバイス構成]** 、 **[プロファイル]** 、 **[プロファイルの作成]** の順に選択し、プラットフォームに **[Windows 10 以降]** を選択し、プロファイルの種類に **[VPN]** を選択します)、DNS 設定を入力します。 この更新プログラムでは、Intune で **DNS サフィックス**を複数入力することもできるようになりました。 DNS サフィックスを使用する場合は、完全修飾ドメイン名 (FQDN) ではなく、短い名前を使用してネットワーク リソースを検索できます。 この更新プログラムでは、Intune で DNS サフィックスの順序を変更することもできます。
[Windows 10 VPN 設定](../configuration/vpn-settings-windows-10.md#dns-settings)によって、現在の DNS 設定が一覧表示されます。
適用対象:Windows 10 デバイス

#### <a name="support-for-always-on-vpn-for-android-enterprise-work-profiles---1333705---"></a>Android エンタープライズ作業プロファイル向けの常時 VPN のサポート<!-- 1333705 -->
この更新プログラムでは、管理対象の作業プロファイルが与えられた Android エンタープライズ デバイスで常時 VPN 接続を使用できます。 常時 VPN 接続では接続状態が常に維持されるか、ユーザーが自分のデバイスをロックしたとき、デバイスが再起動したとき、ワイヤレス ネットワークに変更があったとき、すぐに再接続されます。 接続を "ロックダウン" モードにすることもできます。このモードでは、VPN 接続が有効になるまですべてのネットワーク トラフィックがブロックされます。
**[デバイス構成]** 、 **[プロファイル]** 、 **[プロファイルの作成]** の順に選択し、プラットフォームに **[Android エンタープライズ]** を選択し、 **[デバイスの制限]** を選択し、設定に **[接続]** を選択することで常時 VPN を有効にできます。

#### <a name="issue-scep-certificates-to-user-less-devices---1744554---"></a>ユーザーのいないデバイスに SCEP 証明書を発行する<!-- 1744554 -->
現在のところ、証明書はユーザーに発行されます。 この更新プログラムでは、キオスクのようなユーザーのいないデバイスも含め、デバイスに SCEP 証明書を発行できます ( **[デバイス構成]** 、 **[プロファイル]** 、 **[プロファイルの作成]** の順に選択し、プラットフォームに **[Windows 10 以降]** を選択し、プロファイルに **[SCEP 証明書]** を選択します)。 その他の更新プログラム:
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
> - `{{FullyQualifiedDomainName}}` は Windows とドメインに参加しているデバイスでのみ機能します。 
> - サブジェクトまたは SAN の IMEI、シリアル番号、完全修飾ドメイン名などのデバイスのプロパティをデバイス証明書に指定する場合、これらのプロパティは、デバイスにアクセスできる人物が偽装する可能性があることに注意してください。 

[[SCEP 証明書プロファイルを作成する]](../protect/certificates-profile-scep.md#create-a-scep-certificate-profile) には、SCEP 構成プロファイルの作成時、現在の変数が一覧表示されます。 

適用対象:Windows 10 以降と iOS、Wi-Fi でサポート。

#### <a name="remotely-lock-uncompliant-devices---2064495---"></a>非準拠デバイスのリモート ロック<!-- 2064495 -->
デバイスが非準拠のとき、そのデバイスをリモートでロックするアクションをコンプライアンス ポリシーで作成できます。 Intune で **[デバイスのポリシー準拠]** を選択して新しいポリシーを作成するか、既存のポリシーを選択し、 **[プロパティ]** を選択します。 **[コンプライアンス非対応に対するアクション]** 、 **[追加]** の順に選択し、デバイスのリモート ロックを選択します。
サポート対象: 
- Android
- iOS
- macOS
- Windows 10 Mobile 
- Windows Phone 8.1 以降 

#### <a name="windows-10-and-later-kiosk-profile-improvements-in-the-azure-portal---2748224---"></a>Azure portal で Windows 10 以降のキオスク プロファイルを改善<!-- 2748224 -->
この更新プログラムでは、Windows 10 キオスク デバイスの構成プロファイルが次のように改善されています ( **[デバイス構成]** 、 **[プロファイル]** 、 **[プロファイルの作成]** の順に選択し、プラットフォームに **[Windows 10 以降]** を選択し、プロファイルの種類に **[キオスク プレビュー]** を選択します)。 
- 現在のところ、同じデバイスで複数のキオスク プロファイルを作成できます。 この更新プログラムで Intune はデバイスあたりキオスク プロファイルを 1 つだけサポートするようになります。 1 台のデバイスに複数のキオスク プロファイルが必要な場合は、カスタム URI を使用できます。
- **マルチアプリ キオスク** プロファイルでは、アプリケーション グリッドの**スタート メニュー レイアウト**でアプリケーション タイルのサイズと順序を選択できます。 さらにカスタマイズする場合、続けて XML ファイルをアップロードできます。
- キオスク ブラウザーの設定が**キオスク**設定に移動します。 現在のところ、Azure portal には**キオスク Web ブラウザー**設定に独自のカテゴリがあります。
適用対象:Windows 10 以降

#### <a name="pin-prompt-when-you-change-fingerprints-or-face-id-on-an-ios-device----2637704----"></a>iOS デバイス上での指紋または Face ID の変更時の PIN プロンプト <!-- 2637704  -->
iOS デバイス上での生体認証の変更後、ユーザーに PIN の入力が求められるようになりました。 これには、登録済みの指紋や Face ID の変更が含まれます。 プロンプトのタイミングは、 *[アクセス要件を再確認するまでの時間 (分)]* の構成によって異なります。  PIN が設定されていない場合は、ユーザーに設定を求められます。 
 
この機能は iOS でのみ使用可能で、iOS 向け Intune App SDK のバージョン 9.0.1 以降を統合するアプリケーションの参加が必要です。 SDK の統合は、対象のアプリケーション上で動作を適用するために必要です。 この統合は、ローリング方式で行われ、特定のアプリケーション チームに依存します。 参加するアプリケーションには、WXP、Outlook、Managed Browser、Yammer などが含まれます。

#### <a name="network-access-control-support-on-ios-vpn-clients---1333693---"></a>iOS VPN クライアントでのネットワーク アクセス制御のサポート<!-- 1333693 -->
この更新では、Cisco AnyConnect、F5 Access、Citrix SSO for iOS 用の VPN 構成プロファイルを作成するときに、ネットワーク アクセス制御 (NAC) を有効にするための新しい設定があります。 この設定では、デバイスの NAC ID を VPN プロファイルに含めることができます。 現時点では、この新しい NAC ID をサポートする VPN クライアントまたは NAC パートナー ソリューションはありませんが、サポートされるようになったら[サポートのブログ投稿](ttps://aka.ms/iOS12_and_vpn)でお知らせします。

NAC を使用するには、以下のことが必要です。
1. デバイス ID を VPN プロファイルに含めることを Intune に許可します
2. NAC プロバイダーから直接提供されるガイダンスを使用して、NAC プロバイダーのソフトウェア/ファームウェアを更新します

iOS VPN プロファイルでのこの設定については、「[Microsoft Intune で iOS デバイスに対する VPN 設定を構成する](../configuration/vpn-settings-ios.md)」をご覧ください。 ネットワーク アクセス制御について詳しくは、「[ネットワーク アクセス制御 (NAC) と Intune の統合](../protect/network-access-control-integrate.md)」をご覧ください。 

適用対象: iOS

#### <a name="remove-an-email-profile-from-a-device-even-when-theres-only-one-email-profile---1818139---"></a>メール プロファイルが 1 つだけの場合でも、デバイスからメール プロファイルを削除する<!-- 1818139 -->
以前は、電子メール プロファイルが 1 つしかない*場合*、デバイスからその電子メール プロファイルを削除することはできませんでした。 今回の更新では、この動作が変更されました。 デバイス上に 1 つしかない電子メール プロファイルでも削除できるようになりました。 詳細については、「[Microsoft Intune で電子メールの設定を構成する方法](../configuration/email-settings-configure.md)」をご覧ください。

#### <a name="powershell-scripts-and-aad---2309469---"></a>PowerShell スクリプトと AAD<!-- 2309469 -->
Intune 内の PowerShell スクリプトは、AAD デバイスのセキュリティ グループを対象にすることができます。

#### <a name="new-required-password-type-default-setting-for-android-android-enterprise---2649963---"></a>Android および Android エンタープライズでの [必要なパスワードの種類] の新しい既定値の設定<!-- 2649963 -->
新しいコンプライアンス ポリシーを作成すると ( **[Intune]**  >  **[デバイスのポリシー準拠]**  >  **[ポリシー]**  >  **[ポリシーの作成]**  >  **[Android]** 、または [プラットフォーム] > [システム セキュリティ] の **[Android エンタープライズ]** )、 **[必要なパスワードの種類]** の既定値が変更されます。

開始:デバイスの既定値:最小数の数字

適用対象:Android、Android Enterprise

これらの設定については、[Android](../protect/compliance-policy-create-android.md) および [Android エンタープライズ](../protect/compliance-policy-create-android-for-work.md)のページをご覧ください。

#### <a name="use-a-pre-shared-key-in-a-windows-10-wi-fi-profile---2662938---"></a>Windows 10 Wi-Fi プロファイル内で事前共有キーを使用する<!-- 2662938 -->
この更新では、事前共有キー (PSK) を WPA/WPA2-パーソナル セキュリティ プロトコルと一緒に使用することで、Windows 10 向け Wi-Fi 構成プロファイルを認証できるようになります。 また、2018 年 10 月更新の Windows 10 上のデバイスに対して従量制課金接続のコストの構成を指定することもできます。

現時点では、Wi-Fi プロファイルをインポートするか、またはカスタム プロファイルを作成して事前共有キーを使用する必要があります。 [Windows 10 向けの Wi-Fi 設定](../configuration/wi-fi-settings-windows.md)に関するページに現在の設定が一覧されています。 

#### <a name="remove-pkcs-and-scep-certificates-from-your-devices---3218390---"></a>デバイスから PKCS および SCEP 証明書を削除する<!-- 3218390 -->
一部のシナリオでは、グループからポリシーを削除したり、構成またはコンプライアンスの展開を削除したり、既存の SCEP プロファイルまたは PKCS プロファイルを管理者が更新したりした場合でも、PKCS 証明書および SCEP 証明書がデバイス上に残りました。 今回の更新ではこの動作が変更されます。 PKCS 証明書および SCEP 証明書がデバイスから削除されるシナリオと、証明書がデバイス上に残るシナリオが存在します。 各シナリオについては、「[Microsoft Intune で SCEP 証明書と PKCS 証明書を削除する](../protect/remove-certificates.md)」をご覧ください。

#### <a name="use-gatekeeper-on-macos-devices-for-compliance---2504381---"></a>コンプライアンスのために macOS デバイスでゲートキーパーを使用する<!-- 2504381 -->
この更新には、デバイスのコンプライアンスを評価するための macOS ゲートキーパーが含まれています。 ゲートキーパーの正しい設定については、「[Intune で macOS デバイス用のデバイス コンプライアンス ポリシーを追加する](../protect/compliance-policy-create-mac-os.md)」をご覧ください。


### <a name="device-enrollment"></a>デバイスの登録

#### <a name="apply-autopilot-profile-to-enrolled-win-10-devices-not-already-registered-for-autopilot---1558983---"></a>Autopilot に関してまだ登録されていない登録 Win 10 デバイスに Autopilot プロファイルを適用する<!-- 1558983 -->
Autopilot に関してまだ登録されていない登録 Win 10 デバイスに Autopilo プロファイルを適用できます。 Autopilot プロファイルで **[すべての対象デバイスを Autopilot に変換する]** オプションを選択し、非 Autopilot デバイスを Autopilot デプロイ サービスに自動登録します。 登録が処理されるまで 48 時間待ちます。 デバイスが登録解除されリセットされると、Autopilot によってそのデバイスがプロビジョニングされます。

#### <a name="create-and-assign-multiple-enrollment-status--page-profiles-to-azure-ad-groups---2526564---"></a>登録ステータス ページ プロファイルを複数作成し、Azure AD グループに割り当てる<!-- 2526564 -->
登録ステータス ページ プロファイルを複数[作成し、Azure AD グループに割り当てる](../enrollment/windows-enrollment-status.md)ことができるようになりました。

#### <a name="migration-from-device-enrollment-program-to-apple-business-manager-in-intune--2748613--"></a>Intune で Device Enrollment Program から Apple Business Manager に移行する<!--2748613-->
Apple Business Manager (ABM) は Intune で動作します。Device Enrollment Program (DEP) から ABM にアカウントをアップグレードできます。 Intune でのプロセスは同じです。 DEP から ABM に Apple アカウントをアップグレードするには、[https://support.apple.com/HT208817]( https://support.apple.com/HT208817) に移動します。

#### <a name="alert-and-enrollment-status-tabs-on-the-device-enrollment-overview-page--2748656--"></a>デバイス登録概要ページのアラートと登録ステータスのタブ<!--2748656-->
デバイス登録概要ページでは、アラートや登録エラーが別々のタブに表示されるようになりました。

#### <a name="enrollment-abandonment-report---1382924---"></a>登録の破棄に関するレポート<!-- 1382924 -->
破棄された登録の詳細を示す新しいレポートを使用できます。 **[デバイスの登録]**  >  **[モニター]** の順に移動します。 詳しくは、「[ポータル サイトの破棄レポート](../enrollment/enrollment-report-company-portal-abandon.md)」をご覧ください。

#### <a name="new-azure-active-directory-terms-of-use-feature---2870393---"></a>新しい Azure Active Directory Terms of Use 機能<!-- 2870393 -->
Azure Active Directory では、既存の Intune の使用条件の代わりに使用できる terms of use 機能が用意されます。 Azure AD terms of use 機能では、どの使用条件をどのタイミングで表示するかについての柔軟性が高くなり、ローカライズのサポートが強化され、使用条件の表示方法をより細かく制御でき、レポート機能が改善されています。 Azure AD terms of use 機能を使用するには、Enterprise Mobility + Security E3 スイートにも含まれている Azure Active Directory Premium P1 が必要です。 詳しくは、「[ユーザー アクセスに関する会社の使用条件を管理する](../enrollment/terms-and-conditions-create.md)」をご覧ください。

#### <a name="android-device-owner-mode-support--3188762--"></a>Android デバイス所有者モードのサポート<!--3188762-->
Samsung Knox Mobile Enrollment について、Android デバイス所有者管理モードへのデバイスの登録を Intune がサポートするようになりました。 WiFi または移動体通信ネットワークのユーザーは、初めてデバイスをオンにしたときに、ほんの数タップで登録できます。 詳しくは、「[Samsung の Knox Mobile Enrollment を使用して Android デバイスを自動的に登録する](../enrollment/android-samsung-knox-mobile-enroll.md)」をご覧ください。

### <a name="device-management"></a>デバイス管理
#### <a name="new-settings-for-software-updates-----1907869---"></a>ソフトウェア更新プログラムの新しい設定  <!-- 1907869 -->  
- 最新のソフトウェア更新プログラムのインストールを完了するのに必要な再起動に関して、エンドユーザーに警告するための通知を構成できるようになりました。   
- 勤務時間外に実行される再起動に対して表示する再起動警告メッセージを構成できるようになりました。これにより、BYOD シナリオがサポートされます。

#### <a name="group-windows-autopilot-enrolled-devices-by-correlator-id---2075110---"></a>Windows Autopilot に登録されたデバイスを correlator ID によってグループ化する<!-- 2075110 -->
Configuration Manager で [既存デバイス向け Autopilot](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430) を使用することによって登録するとき、correlator ID による Windows デバイスのグループ化が Intune によってサポートされます。 correlator ID は、Autopilot 構成ファイルのパラメーターです。 Intune では [Azure AD デバイス属性 enrollmentProfileName](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#rules-for-devices) が等しい "OfflineAutopilotprofile-<correlator ID>" に自動的に設定されます。 これにより、オフライン Autopilot 登録用の enrollmentprofileName 属性を介して、correlator ID に基づく任意の Azure AD 動的グループを作成することができます。 詳細については、「[Windows Autopilot for existing devices](../enrollment/enrollment-autopilot.md#windows-autopilot-for-existing-devices)」 (既存のデバイス向け Windows Autopilot) を参照してください。

#### <a name="intune-app-protection-policies---2984657---"></a>Intune のアプリ保護ポリシー<!-- 2984657 -->
Intune アプリ保護ポリシーを使用すると、Microsoft Outlook や Microsoft Word など、Intune で保護されているアプリに対するさまざまなデータ保護設定を構成できます。 [iOS](../apps/app-protection-policy-settings-ios.md) と [Android](../apps/app-protection-policy-settings-android.md) 両方でのこれらの設定のルック アンド フィールが、個々の設定を見つけやすいように変更されました。 ポリシー設定にはカテゴリが 3 つあります。
- **データ再配置** - このグループには、切り取り、コピー、貼り付け、名前を付けて保存の制限など、データ損失防止 (DLP) コントロールが含まれます。 これらの設定によって、アプリでユーザーがデータを操作する方法が決定されます。
- **アクセス要件** - このグループには、エンド ユーザーが仕事でアプリにアクセスする方法を決定するアプリ別の PIN オプションが含まれます。  
- **条件付き起動** - このグループには、最小 OS 設定、脱獄またはルート化されたデバイスの検出、オフライン猶予期間などの設定が含まれます。  
  
設定の機能は変更されていませんが、ポリシー作成フローで作業するときに、設定を見つけやすくなります。

#### <a name="restricts-apps-and-block-access-to-company-resources-on-android-devices---2451462----"></a>Android デバイスでアプリを制限し、会社のリソースへのアクセスをブロックする<!-- 2451462  -->  
**[デバイス コンプライアンス]** 、 **[ポリシー]** 、 **[ポリシーの作成]** 、 **[Android]** 、 **[システム セキュリティ]** の順に選択すると、 *[デバイス セキュリティ]* セクションの下に **[制限付きアプリ]** という新しい設定が表示されます。 **[制限付きアプリ]** 設定ではコンプライアンス ポリシーが使用され、特定のアプリがデバイスにインストールされている場合、会社のリソースへのアクセスがブロックされます。 制限付きアプリケーションがデバイスから削除されるまで、デバイスは非準拠と見なされます。
適用対象: 
- Android

### <a name="intune-apps"></a>Intune アプリ

#### <a name="intune-will-support-a-maximum-package-size-of-8-gb-for-lob-apps---1727158---"></a>Intune でサポートされる LOB アプリの最大パッケージ サイズが 8 GB になる<!-- 1727158 -->
Intune では、基幹業務 (LOB) アプリの最大パッケージ サイズが 8 GB に増加します。 詳しくは、「[Microsoft Intune にアプリを追加する](../apps/apps-add.md)」をご覧ください。

#### <a name="add-custom-brand-image-for-company-portal-app---1916266---"></a>ポータル サイト アプリ用のカスタム ブランド イメージを追加する<!-- 1916266 -->
Microsoft Intune 管理者は、iOS ポータル サイト アプリ内のユーザーのプロファイル ページに背景イメージとして表示されるカスタム ブランド イメージをアップロードできるようになります。 ポータル サイト アプリの構成方法の詳細については、「[Microsoft Intune ポータル サイト アプリを構成する方法](../apps/company-portal-app.md)」を参照してください。

#### <a name="intune-will-maintain-the-office-localized-language-when-updating-office-on-end-users-machines---2971030---"></a>エンドユーザーのコンピューター上で Office を更新するとき、Office のローカライズされた言語は Intune によって維持される<!-- 2971030 -->
エンドユーザーのコンピューターに Office が Intune によってインストールされる場合、エンド ユーザーには前の .MSI Office インストールで使用していたのと同じ言語パックが自動的に提供されます。 詳しくは、「[Microsoft Intune で Windows 10 デバイスに Office 365 アプリを割り当てる](../apps/apps-add-office365.md)」をご覧ください。

### <a name="monitor-and-troubleshoot"></a>監視とトラブルシューティング

#### <a name="new-intune-support-experience-in-the-microsoft-365-device-management-portal---3076965---"></a>Microsoft 365 デバイス管理ポータルでの新しい Intune サポート エクスペリエンス<!-- 3076965 -->
[Microsoft 365 デバイス管理ポータル]( https://devicemanagement.microsoft.com)での Intune の新しいヘルプとサポート エクスペリエンスがロールアウトされています。 新しいエクスペリエンスでは、自分の言葉で問題を説明し、トラブルシューティングの分析情報と Web ベースの修復コンテンツを受け取ることができます。 これらの解決策は、ユーザーの照会により、ルール ベースの機械学習アルゴリズムを使用して提供されます。  

問題固有のガイダンスに加えて、新しいケース作成ワークフローを使用して、メールまたは電話でサポート ケースを開くこともできます。  

ロールアウトの一部であるお客様の場合、ヘルプとサポートを開いたコンソールの領域に基づいて事前選択されているオプションの静的セットである現在のヘルプとサポート エクスペリエンスが、この新しいエクスペリエンスに置き換えられます。  

*この新しいヘルプとサポート エクスペリエンスは、全部ではなく一部のテナントにロールアウトされており、デバイス管理ポータルで使用できます。この新しいエクスペリエンスの参加者は、利用可能な Intune テナントからランダムに選択されます。ロールアウトが拡張されると、新しいテナントが追加されます。*  

詳細については、「Microsoft Intune のサポートを受ける方法」の「[新しいヘルプとサポート エクスペリエンス](get-support.md#help-and-support-experience)」を参照してください。  

#### <a name="powershell-module-for-intune--preview-available---951068---"></a>Intune 用の PowerShell モジュール – プレビュー版<!-- 951068 -->
Microsoft Graph を通じて Intune API のサポートを提供する新しい PowerShell モジュールのプレビュー版が、[GitHub](https://aka.ms/intunepowershell) で利用可能になりました。 このモジュールの使用方法について詳しくは、その場所にある README ファイルをご覧ください。

<!-- ########################## -->
## <a name="september-2018"></a>2018 年 9 月

### <a name="app-management"></a>アプリ管理

#### <a name="remove-duplication-of-app-protection-status-tiles---3083391---"></a>アプリ保護ステータス タイルの重複削除<!-- 3083391 -->
**[iOS のユーザーの状態]** タイルと **[Android のユーザーの状態]** タイルは、 **[クライアント アプリ - 概要]** ページと **[クライアント アプリ - アプリ保護ステータス]** ページの両方に表示されていました。 重複を避けるために、 **[クライアント アプリ - 概要]** ページからステータス タイルが削除されました。 

### <a name="device-configuration"></a>デバイスの構成

#### <a name="support-for-more-third-party-certification-authorities-ca---3093107---"></a>サードパーティ証明書機関 (CA) のサポート追加<!-- 3093107 -->
Simple Certificate Enrollment Protocol (SCEP) を利用することで、Windows、iOS、Android、macOS を搭載するモバイル デバイスで新しい証明書を発行したり、証明書を更新したりできるようになりました。

### <a name="device-enrollment"></a>デバイスの登録

#### <a name="intune-moves-to-support-ios-10-and-later---2454656---"></a>Intune サポートが iOS 10 以降に<!-- 2454656 -->  
今後、Intune の登録、ポータル サイト、Managed Browser は iOS 10 以降を搭載して iOS デバイスのみでサポートされます。 組織で影響を受けるデバイスやユーザーを確認するには、Azure portal で Intune にアクセスし、 **[デバイス]** 、 **[すべてのデバイス]** の順に選択します。 OS で絞り込み、 **[列]** をクリックして OS バージョン詳細を表示します。 サポートされている OS バージョンにデバイスをアップグレードするようにユーザーに依頼します。  

以下に一覧したデバイスのいずれかを所有している場合、または以下に一覧したデバイスのいずれかを登録する場合、それらのデバイスは iOS 9 以前しかサポートしていないので注意してください。  Intune ポータル サイトに引き続きアクセスするには、iOS 10 以降をサポートするデバイスにそれらのデバイスをアップグレードする必要があります。  

* iPhone 4S 
* iPod Touch  
* iPad 2 
* iPad (第 3 世代) 
* iPad Mini (第 1 世代)  

### <a name="device-management"></a>デバイス管理

#### <a name="microsoft-365-device-management-administration-center---3078424---"></a>Microsoft 365 デバイス管理の管理センター<!-- 3078424 -->
Microsoft 365 で Microsoft が約束することの 1 つは簡単な管理です。長年、Intune や Azure AD の条件付きアクセスなどのエンドツーエンド シナリオを届けるべく、Microsoft はバックエンド Microsoft 365 サービスを統合してきました。 新しい [Microsoft 365 管理センター](https://devicemanagement.microsoft.com)は、管理業務を連結、簡素化、統合する場所です。 デバイス管理のスペシャリスト向けワークスペースでは、組織で必要とされるあらゆるデバイス/アプリ管理情報/作業に簡単にアクセスできます。 企業のエンドユーザー コンピューティング チームにとってはこれが主要なクラウド ワークスペースになるものと Microsoft は予想しています。


<!-- ########################## -->
## <a name="august-2018"></a>2018 年 8 月

### <a name="app-management"></a>アプリ管理

#### <a name="packet-tunnel-support-for-ios-per-app-vpn-profiles-for-custom-and-pulse-secure-connection-types---1520957---"></a>接続の種類がカスタムと Pulse Secure の場合における、iOS のアプリごとの VPN プロファイルに対するパケット トンネル サポート<!-- 1520957 -->
iOS のアプリごとの VPN プロファイルを使用するときに、アプリ層トンネリング (アプリプロキシ) またはパケット レベル トンネリング (パケットトンネル) を使用することを選択できます。 これらのオプションは、次の接続の種類で利用できます。
- カスタム VPN
- Pulse Secure: 使用する値がわからない場合、ご利用の VPN プロバイダーのドキュメントを参照してください。

#### <a name="delay-when-ios-software-updates-are-shown-on-the-device---1949583---"></a>iOS ソフトウェア更新がデバイスに表示されるときの遅延<!-- 1949583 -->
Intune の **[ソフトウェアの更新]** の **[iOS のポリシーを更新する]** で、デバイスにあらゆる更新プログラムをインストールしない日時を構成できます。 今後の更新では、1 日から 90 日までの間で、ソフトウェア更新が表示されるタイミングを遅らせることができるようになります。 
[こちら](../protect/software-updates-ios.md)に Microsoft Intune で iOS 更新ポリシーを構成する方法が説明されていますが、ここに現在の設定が一覧になっています。

#### <a name="office-365-proplus-version---2213968---"></a>Office 365 ProPlus バージョン<!-- 2213968 -->
Intune を利用して Office 365 ProPlus アプリを Windows 10 デバイスに割り当てるとき、Office のバージョンを選択できるようになります。 Azure portal で、 **[Microsoft Intune]** 、 **[アプリ]** 、 **[アプリの追加]** の順に選択します。 次に、 **[種類]** ドロップダウン リストから **[Office 365 ProPlus Suite (Windows 10)]** を選択します。 **[アプリ スイートの設定]** を選択し、関連ブレードを表示します。 **[更新チャネル]** を **[毎月]** などの値に設定します。 任意で、 **[はい]** を選択し、エンド ユーザー デバイスから Office のその他のバージョン (msi) を削除します。 **[特定]** を選択すると、選択されているチャネルで特定のバージョンの Office がエンド ユーザー デバイスにインストールされます。 この時点で、使用する**特定のバージョン**の Office を選択できます。 使用できるバージョンは随時変更されます。 そのため、新しいデプロイを作成するとき、利用できるバージョンが新しく、特定の古いバージョンを利用できないことがあります。 現在のデプロイでは引き続き古いバージョンをデプロイできますが、バージョンの一覧はチャネル単位で継続的に更新されます。 詳細については、「[Office 365 ProPlus 更新プログラム チャネルの概要](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus)」をご覧ください。

#### <a name="support-for-register-dns-setting-for-windows-10-vpn---2282852---"></a>Windows 10 VPN の DNS 登録設定をサポート<!-- 2282852 -->
この更新では、カスタム プロファイルを使用しなくても、内部 DNS を使用し、VPN インターフェイスに割り当てられている IP アドレスを動的に登録するように、Windows 10 VPN プロファイルを構成できるようになります。
現在の VPN プロファイルの設定に関する詳細については、「[Intune での Windows 10 VPN の設定](../configuration/vpn-settings-windows-10.md)」を参照してください。

#### <a name="the-macos-company-portal-installer-now-includes-the-version-number-in-the-installer-file-name--2652728--"></a>macOS ポータル インストーラーはインストーラー ファイル名にバージョン番号を含む<!--2652728-->

#### <a name="ios-automatic-app-updates---2729759---"></a>iOS のアプリの自動更新<!-- 2729759 -->
アプリの自動更新は、iOS バージョン 11.0 以上のデバイスとユーザー ライセンスされたアプリの両方で機能します。

### <a name="device-configuration"></a>デバイスの構成

#### <a name="windows-hello-will-target-users-and-devices---1106609---"></a>Windows Hello の対象はユーザーとデバイスになります<!-- 1106609 -->
[Windows Hello for Business](../protect/windows-hello.md) ポリシーを作成すると、そのポリシーは組織内 (テナント全体) のすべてのユーザーに適用されます。 今回の更新によって、デバイス構成ポリシーを使用する特定のユーザーまたは特定のデバイスにもポリシーを適用できるようになりました ( **[デバイス構成]** 、 **[プロファイル]** 、 **[プロファイルの作成]** 、 **[ID 保護]** 、 **[Windows Hello for Business]** )。
Azure portal の Intune では、Windows Hello の構成と設定は、 **[デバイスの登録]** と **[デバイス構成]** の両方に存在するようになりました。 **[デバイスの登録]** の対象は組織全体 (テナント全体) であり、Windows AutoPilot (OOBE) がサポートされます。 **[デバイス構成]** の対象は、チェックイン中に適用されたポリシーを使用するデバイスとユーザーになります。
この機能は、以下に適用されます。  
- Windows 10 以降
- Windows Holographic for Business

#### <a name="zscaler-is-an-available-connection-for-vpn-profiles-on-ios---1769858---"></a>iOS の VPN プロファイルには、Zscaler を接続として利用可能<!-- 1769858 -->
iOS VPN デバイス構成プロファイルを作成するとき ( **[デバイス構成]** 、 **[プロファイル]** 、 **[プロファイルの作成]** の順に選択し、プラットフォームに **iOS** を選択し、プロファイルの種類に **VPN** を選択する)、Cisco や Citrix など、接続の種類がいくつかあります。 この更新では、接続の種類として Zscaler が追加されます。 
[こちらの](../configuration/vpn-settings-ios.md)iOS を実行するデバイスの VPN 設定リストには、利用できる接続の種類がまとめられています。

#### <a name="fips-mode-for-enterprise-wi-fi-profiles-for-windows-10---1879077---"></a>Windows 10 用の Enterprise Wi-Fi プロファイルに対する FIPS モード<!-- 1879077 -->
Intune Azure portal 内の Windows 10 用の Enterprise Wi-Fi プロファイルに対して、Federal Information Processing Standards (FIPS) モードを有効にできるようになりました。 Wi-Fi プロファイルで有効にする場合は、ご使用の Wi-Fi インフラストラクチャで FIPS モードを有効にしていることを確認してください。
「[Intune での Windows 10 以降のデバイス向けの Wi-Fi 設定](../configuration/wi-fi-settings-windows.md)」では、Wi-Fi プロファイルを作成する方法について示します。

#### <a name="control-s-mode-on-windows-10-and-later-devices---public-preview---1958649---"></a>Windows 10 以降のデバイスで S モードを制御する - パブリック プレビュー<!-- 1958649 -->
この機能更新プログラムでは、Windows 10 デバイスの S モードを解除するデバイス構成プロファイルを作成したり、ユーザーがデバイスの S モードを解除することを禁止したりできます。 この機能は Intune の **[デバイス構成]**  >  **[プロファイル]**  >   **[Windows 10 以降]**  >  **[Edition upgrade and mode switch]\(エディション アップグレードとモード切替\)** にあります。
S モードの詳細は「[Windows 10 (S モード) について](https://www.microsoft.com/windows/s-mode)」でご覧いただけます。
適用対象: 一番新しい [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) ビルド (プレビュー段階)。

#### <a name="windows-defender-atp-configuration-package-automatically-added-to-configuration-profile---2144658---"></a>構成プロファイルに自動的に追加される Windows Defender ATP 構成パッケージ<!-- 2144658 -->
Intune で [Advanced Threat Protection を使用してデバイスをオンボードする](../protect/advanced-threat-protection.md#onboard-devices-by-using-a-configuration-profile)場合、前もって構成パッケージをダウンロードし、それを構成プロファイルに追加する必要があります。 この更新では、Intune で Windows Defender Security Center からパッケージを自動的に取得し、それをプロファイルに追加します。
Windows 10 以降に適用されます。

#### <a name="require-users-to-connect-during-device-setup--2311457--"></a>デバイスのセットアップ中に接続するためのユーザーが必要<!--2311457-->
Windows 10 のセットアップ中にネットワーク ページから進む前に、デバイスがネットワークに接続することを要求するように、デバイス プロファイルを設定できるようになりました。 この機能はプレビュー中ですが、Windows Insider ビルド 1809 以降ではこの設定を使用する必要があります。
適用対象: 一番新しい [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) ビルド (プレビュー段階)。

#### <a name="restricts-apps-and-block-access-to-company-resources-on-ios-and-android-enterprise-devices---2451462---"></a>iOS デバイスと Android エンタープライズ デバイスでアプリを制限し、会社のリソースへのアクセスをブロックする<!-- 2451462 -->
**[デバイスのポリシー準拠]**  >  **[ポリシー]**  >  **[ポリシーの作成]**  >  **[iOS]**  >  **[システム セキュリティ]** の順に選択したところに、**制限付きアプリケーション**の新しい設定があります。 この新しい設定ではコンプライアンス ポリシーが使用され、特定のアプリがデバイスにインストールされている場合、会社のリソースへのアクセスがブロックされます。 制限付きアプリケーションがデバイスから削除されるまで、デバイスは非準拠と見なされます。
適用対象: iOS

#### <a name="modern-vpn-support-updates-for-ios---2459928-1819876-and-2650856---"></a>最新の VPN サポートの更新で iOS に対応<!-- 2459928, 1819876, and 2650856 -->
この更新では、次の iOS VPN クライアントがサポート対象になります。
- F5 Access (バージョン 3.0.1 以降)
- Citrix SSO
- Palo Alto Networks GlobalProtect バージョン 5.0 以降。この更新では以下もサポートされます。
- 既存の **F5 Access** の接続の種類は、iOS 用の **F5 Access Legacy** という名前に変更されました。
- 既存の **Palo Alto Networks GlobalProtect** の接続の種類の名前は、iOS 用の **Palo Alto Networks GlobalProtect (Legacy)** に変更されます。
これらの接続の種類を持つ既存のプロファイルは、引き続きそれぞれのレガシ VPN クライアントで動作します。 Cisco Legacy AnyConnect、F5 Access Legacy、Citrix VPN、または Palo Alto Networks GlobalProtect バージョン 4.1 以前を iOS で使用している場合、新しいアプリに移ってください。 iOS 12 に更新されたときに iOS デバイスで VPN アクセスを利用できるように、できるだけ速やかに移ってください。
iOS 12 と VPN プロファイルの詳細については、[Microsoft Intune サポート チームのブログ](https://go.microsoft.com/fwlink/?linkid=2013806)に関するページを参照してください。

#### <a name="export-azure-classic-portal-compliance-policies-to-recreate-these-policies-in-the-intune-azure-portal---2469637---"></a>Azure クラシック ポータルのコンプライアンス ポリシーをエクスポートして、Intune Azure portal でこれらのポリシーを再作成する<!-- 2469637 -->
Azure クラシック ポータルで作成されたコンプライアンス ポリシーは非推奨になる予定です。 既存のコンプライアンス ポリシーは確認したり、削除したりできますが、更新することはできません。 現在の Intune Azure portal に任意のコンプライアンス ポリシーを移行する必要がある場合は、コンマ区切りファイル ( *.csv* ファイル) としてポリシーをエクスポートできます。 その後、ファイルの詳細を使って、Intune Azure portal でこれらのポリシーを再作成します。

> [!IMPORTANT]
> Azure クラシック ポータルが廃止されると、ご自分のコンプライアンス ポリシーにアクセスしたり、表示したりすることはできなくなります。 そのため、Azure クラシック ポータルが廃止される前に、必ずご利用のポリシーをエクスポートし、Azure portal で再作成してください。

#### <a name="better-mobile---new-mobile-threat-defense-partner---22662717---"></a>Better Mobile - 新しい Mobile Threat Defense パートナー<!-- 22662717 -->
Microsoft Intune に統合された Mobile Threat Defense ソリューションである Better Mobile によって実行されるリスク評価に基づき、条件付きアクセスを利用し、モバイル デバイスから会社のリソースへのアクセスを制御できます。

### <a name="device-enrollment"></a>デバイスの登録

#### <a name="lock-the-company-portal-in-single-app-mode-until-user-sign-in--1067692---"></a>ユーザーがサインインするまで、シングル アプリ モードでポータル サイトをロックする<!--1067692 --> 
DEP 登録中、セットアップ アシスタントの代わりに、ポータル サイトを介してユーザーを認証する場合、シングル アプリ モードでポータル サイトを実行するオプションを使用できるようになりました。 このオプションによってセットアップ アシスタントの完了直後にデバイスがロックされます。そのため、デバイスを利用するには、ユーザーはサインインする必要があります。 このプロセスにより、デバイスはオンボードを完了し、ユーザーが関連付けられていない状態で孤立することはありません。

#### <a name="assign-a-user-and-friendly-name-to-an-autopilot-device--1346521---"></a>Autopilot デバイスにユーザーとわかりやすい名前を割り当てる<!--1346521 -->
[ユーザーを 1 つの Autopilot デバイスに割り当てる](../enrollment/enrollment-autopilot.md)ことができるようになりました。 管理者はまた、AutoPilot でデバイスを設定するユーザーにとってわかりやすい名前を与えることができます。
適用対象: 一番新しい [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) ビルド (プレビュー段階)。

#### <a name="use-vpp-device-licenses-to-pre-provision-the-company-portal-during-dep-enrollment---1608345---"></a>VPP デバイス ライセンスを使用して DEP 登録時にポータル サイトを事前プロビジョニングする<!-- 1608345 -->
Volume Purchase Program (VPP) デバイス ライセンスを使用して、Device Enrollment Program (DEP) 登録時にポータル サイトを事前プロビジョニングすることができます。 そのためには、[登録プロファイルを作成または編集する](../enrollment/device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile)ときに、ポータル サイトをインストールするために使用する VPP トークンを指定します。 トークンの期限が切れていないことと、ポータル サイト アプリの十分なライセンスがあることを確認してください。 トークンの期限が切れているか、ライセンスが不足している場合、Intune は代わりに App Store ポータル サイトをプッシュします (この場合、Apple ID の入力が求められます)。

#### <a name="confirmation-required-to-delete-vpp-token-that-is-being-used-for-company-portal-pre-provisioning---2237634---"></a>ポータル サイトの事前プロビジョニングに使用されている VPP トークンを削除するために必要な構成<!-- 2237634 -->
DEP 登録時にポータル サイトの事前プロビジョニングに Volume Purchase Program (VPP) トークンが使用されている場合、そのトークンを削除するための構成が必要になりました。

#### <a name="block-windows-personal-device-enrollments---1849498---"></a>Windows 個人デバイス登録を禁止する<!-- 1849498 -->
Intune の[モバイル デバイス管理](../enrollment/windows-enroll.md)で [Windows 個人デバイスの登録を禁止](../enrollment/enrollment-restrictions-set.md)できます。 [Intune PC エージェント](../manage-windows-pcs-with-microsoft-intune.md)で登録されているデバイスはこの機能でブロックできません。 この機能は次の数週間でロールアウトされます。そのため、ユーザー インターフェイスにはすぐに表示されないことがあります。

#### <a name="specify-machine-name-patterns-in-an-autopilot-profile--1849855--"></a>Autopilot プロファイルにコンピューター名パターンを指定する<!--1849855-->
Autopilot の登録時に、生成する[コンピューター名テンプレートを指定](../enrollment/enrollment-autopilot.md#create-an-autopilot-deployment-profile)したり、[コンピューター名](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp)を設定したりできます。 適用対象: 一番新しい [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) ビルド (プレビュー段階)。

#### <a name="for-windows-autopilot-profiles-hide-the-change-account-options-on-the-company-sign-in-page-and-domain-error-page--1901669---"></a>Windows Autopilot プロファイルの場合、会社のサインイン ページとドメイン エラー ページでアカウント変更オプションを非表示にする<!--1901669 -->
会社のサインイン ページとドメイン エラー ページでアカウント変更オプションを管理者が非表示にするための[新しい Windows Autopilot プロファイル オプション](../enrollment/enrollment-autopilot.md#create-an-autopilot-deployment-profile)があります。 これらのオプションを非表示にするには、Azure Active Directory で会社のブランドを構成する必要があります。 適用対象: 一番新しい [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) ビルド (プレビュー段階)。

### <a name="macos-support-for-apple-device-enrollment-program---747651---"></a>Apple Device Enrollment Program の macOS によるサポート<!-- 747651 -->
Intune は、Apple Device Enrollment Program (DEP) への macOS デバイスの登録をサポートするようになりました。 詳細については、「[Apple の Device Enrollment Program を使用して macOS デバイスを自動登録する](../enrollment/device-enrollment-program-enroll-macos.md)」を参照してください。

### <a name="device-management"></a>デバイス管理

#### <a name="delete-jamf-devices---2653306--"></a>Jamf デバイスを削除する<!-- 2653306-->
**[デバイス]** に移動し、Jamf デバイスを選択して、 **[削除]** を選択することにより、Jamf で管理されたデバイスを削除できます。

#### <a name="change-terminology-to-retire-and-wipe---2175759---"></a>"削除" と "ワイプ" への用語変更<!-- 2175759 -->
Graph API との一貫性を保つために、Intune のユーザー インターフェイスとドキュメントにおいて次の用語が変更されています。
- **[会社データの削除]** は、"廃止" に変更されます
- **[出荷時の設定にリセット]** は **[ワイプ]** に変更されます

#### <a name="confirmation-dialog-if-admin-tries-to-delete-mdm-push-certificate---297909500--"></a>管理者が MDM プッシュ通知証明書を削除しようとする場合の確認ダイアログ<!-- 297909500-->
任意のユーザーが Apple MDM プッシュ通知証明書を削除しようとすると、確認ダイアログ ボックスには関連する iOS と macOS デバイスの数が表示されます。 証明書が削除された場合、これらのデバイスは再登録される必要があります。

#### <a name="additional-security-settings-for-windows-installer---2282430---"></a>Windows インストーラーの追加のセキュリティ設定<!-- 2282430 -->
ユーザーがアプリのインストールを制御することを許可できます。 有効にすると、セキュリティ違反が原因で本来は停止される可能性があるインストールを続行することが許可されます。 Windows インストーラーによってシステムに任意のプログラムをインストールする場合、管理者特権のアクセス許可を使用するよう Windows インストーラーに指示することができます。 さらに、Windows 情報保護 (WIP) アイテムのインデックス付け、および暗号化されていない場所に格納されたそれらのアイテムに関するメタデータを有効にすることができます。 このポリシーが無効な場合、WIP で保護されたアイテムにはインデックスが付けられず、Cortana またはエクスプローラーの結果に表示されません。 既定では、これらのオプションの機能は無効になっています。 

#### <a name="new-user-experience-update-for-the-company-portal-website--2000968---"></a>Intune ポータル サイトの新しいユーザー エクスペリエンスの更新<!--2000968 -->
顧客からのフィードバックに基づいて、Intune ポータル サイト Web サイトに新機能を追加しています。 ご利用のデバイスから、既存の機能と使いやすさの大幅な向上を体験できます。 &ndash;デバイス詳細、フィードバックとサポート、デバイス概要など&ndash;のサイトの領域には、最新の応答性の高いデザインが採用されています。 次の点も改善されています。

- すべてのデバイス プラットフォームにわたる合理化されたワークフロー
- 改善されたデバイスの識別と登録のフロー
- より役立つエラー メッセージ
- 技術的な専門用語を減らした、わかりやすい言語
- アプリへの直接リンクを共有する機能
- 大規模なアプリケーション カタログのパフォーマンスの向上
- すべてのユーザーのアクセシビリティの向上  

[Intune ポータル サイト Web サイトのドキュメント](https://docs.microsoft.com/intune-user-help/using-the-intune-company-portal-website)は、これらの変更を反映するように更新されています。 アプリの拡張機能の例を表示するには、「[Intune とエンド ユーザー アプリの UI の更新](../whats-new-app-ui.md)」を参照してください。  

### <a name="monitor-and-troubleshoot"></a>監視とトラブルシューティング

#### <a name="enhanced-jailbreak-detection-in-compliance-reporting---2198738---"></a>コンプライアンス レポートでの脱獄の高度な検出<!-- 2198738 -->
脱獄の高度な検出の設定の状態は、管理コンソール内のすべてのコンプライアンス レポートに表示されるようになりました。

### <a name="role-based-access-control"></a>ロール ベースのアクセス制御

#### <a name="scope-tags-for-policies--1081974---"></a>ポリシーのスコープ タグ<!--1081974 -->
Intune リソースへのアクセスを制限するために、[スコープのタグを作成](scope-tags.md)できます。 スコープ タグをロールの割り当てに追加し、同じスコープ タグを構成プロファイルに追加します。 そのロールでは、スコープ タグが一致する (あるいはスコープ タグがない) 構成プロファイルを持つリソースにのみアクセスできます。





<!-- ########################## -->
## <a name="july-2018"></a>2018 年 7 月

### <a name="app-management"></a>アプリ管理

#### <a name="line-of-business-lob-app-support-for-macos---1895847---"></a>macOS の基幹業務 (LOB) アプリのサポート<!-- 1895847 -->
Microsoft Intune では、macOS LOB アプリを **[必須]** として、または **[Available with enrollment]\(登録して利用可能\)** として展開することができます。 エンド ユーザーは、macOS 用のポータル サイトまたは[ポータル サイト Web サイト](https://portal.manage.microsoft.com)を使用して、アプリを **[利用可能]** として展開してもらうことができます。

#### <a name="ios-built-in-app-support-for-kiosk-mode---2051098---"></a>キオスク モードに対応する iOS 組み込みアプリのサポート<!-- 2051098 -->
ストア アプリおよび管理対象アプリに加えて、iOS デバイス上でキオスク モードで実行される組み込みアプリ (Safari など) を選択できるようになりました。

#### <a name="edit-your-office-365-pro-plus-app-deployments---2150145---"></a>Office 365 Pro Plus アプリの展開を編集する<!-- 2150145 -->
Microsoft Intune 管理者は、Office 365 Pro Plus アプリのデプロイを編集するための強化された機能を使用できます。 さらに、スイートのいずれかのプロパティを変更するのに、デプロイを削除しなくてもよくなりました。 Azure portal で、 **[Microsoft Intune]**  >  **[クライアント アプリ]**  >  **[アプリ]** の順に選択します。 アプリの一覧から、Office 365 Pro Plus スイートを選択します。  

#### <a name="updated-intune-app-sdk-for-android-is-now-available---2744271--"></a>更新された Android 用の Intune App SDK が利用可能になった<!-- 2744271-->
Android P のリリースをサポートする Android 用 Intune アプリ SDK の更新バージョンが使用可能になりました。 Android 用 Intune SDK を使用しているアプリ開発者は、Intune アプリ SDK の更新バージョンをインストールして、Android P デバイス上でも Android アプリの Intune 機能が正常に動作するようにする必要があります。 このバージョンの Intune アプリ SDK には、SDK の更新を実行する組み込みのプラグインが用意されています。 統合されている既存のコードを書き直す必要はありません。 詳細については、[Android 用 Intune SDK](https://github.com/msintuneappsdk/ms-intune-app-sdk-android) に関するページをご覧ください。 Intune に対して古いバッジのスタイルを使用している場合は、ブリーフケース アイコンを使用することをお勧めします。 ブランド化について詳しくは、[この GitHub リポジトリ](https://github.com/msintuneappsdk/intune-app-partner-badge)をご覧ください。

#### <a name="more-opportunities-to-sync-in-the-company-portal-app-for-windows"></a>Windows 用ポータル サイト アプリでの同期の機会の増加  
Windows 用ポータル サイト アプリでは、Windows タスク バーと [スタート] メニューから直接同期を開始できるようになりました。 この機能は、唯一のタスクがデバイスを同期して、企業リソースへのアクセスを取得することで場合に特に便利です。 この新しい機能にアクセスするには、ご利用のタスク バーまたは [スタート] メニューに固定されているポータル サイト アイコンを右クリックします。 メニュー オプション (ジャンプ リストとも呼ばれる) で、 **[Sync this device]\(このデバイスを同期\)** を選択します。 ポータル サイトが開いて、 **[設定]** ページが表示され、同期が開始されます。新しい機能については、[UI の新機能](../whats-new-app-ui.md)に関するページを参照してください。   

#### <a name="new-browsing-experiences-in-the-company-portal-app-for-windows"></a>Windows 用ポータル サイト アプリでの新しい閲覧エクスペリエンス  
Windows 用ポータル サイト アプリでアプリを参照または検索するときに、既存の **[タイル]** ビューと新しく追加された **[詳細]** ビューを切り替えることができるようになりました。 新しいビューには、名前、発行元、発行日、インストール状態などのアプリケーションの詳細が一覧表示されます。  

**[アプリ]** ページの **[インストール済み]** ビューでは、完了したアプリのインストールと進行中のアプリのインストールに関する詳細を見ることができます。 新しいビューの外観を確認するには、[UI の新機能](../whats-new-app-ui.md)を参照してください。  

#### <a name="improved-company-portal-app-experience-for-device-enrollment-managers"></a>デバイス登録マネージャー向けのポータル サイト アプリの操作性の改善  
デバイス登録マネージャー (DEM) が Windows 用ポータル サイト アプリにサインインすると、アプリには DEM の現在 (実行中のデバイス) のみが一覧表示されるようになります。 この改善により、DEM に登録されたデバイスをすべて表示しようとしたときに以前に発生していたタイムアウトが削減されます。  

#### <a name="block-app-access-based-on-unapproved-device-vendors-and-models----1425689----"></a>未承認のデバイス ベンダーとモデルに基づくアプリのアクセスのブロック <!-- 1425689 ! -->
Intune の IT 管理者は、Intune App Protection ポリシーによって、Android 製造元や iOS モデルの指定された一覧を適用できます。 IT 管理者は、Android ポリシーの製造元と iOS ポリシーのデバイス モデルのセミコロン区切り一覧を提供できます。 Intune App Protection ポリシーは、Android および iOS 専用です。 この指定されたリストでは 2 つの個別操作を実行できます。
- 指定されていないデバイスでのアプリ アクセスからブロック。
- または、指定されていないデバイスでの企業データの選択的ワイプ。 

ユーザーは、ポリシーによる要件が満たされない場合、対象となるアプリケーションにアクセスすることができません。 設定に基づいて、ユーザーは、ブロックされるか、アプリ内の企業データを選択的にワイプされます。 iOS デバイス上でこの機能を利用するには、対象のアプリケーションに適用するこの機能の Intune アプリ SDK を統合するアプリケーション (WXP、Outlook、Managed Browser、Yammer など) の参加が必要となります。 この統合は、ローリング方式で行われ、特定のアプリケーション チームに依存します。 Android でこの機能を利用するには、最新の Intune ポータル サイトが必要です。 

エンド ユーザー デバイスの Intune クライアントは、アプリケーション保護ポリシーに対して Intune ブレードで指定されている文字列の単純一致に基づいてアクションを実行します。 これは、デバイスを報告する値に完全に依存します。 そのため、IT 管理者には、意図した動作が正確であることを確認することをお勧めします。 これは、小さなユーザー グループを対象に、さまざまなデバイス製造元とモデルに基づいてこの設定をテストすることによって実現できます。 Microsoft Intune で、アプリ保護ポリシーを表示および追加するには、 **[クライアント アプリ]**  >  **[アプリ保護ポリシー]** の順に選択します。 アプリ保護ポリシーの詳細については、「[アプリ保護ポリシーとは](../apps/app-protection-policy.md)」および「[Intune でアプリ保護ポリシーのアクセス アクションを利用し、データを選択的にワイプする](../apps/app-protection-policies-access-actions.md)」を参照してください。

#### <a name="access-to-macos-company-portal-pre-release-build---1734766---"></a>macOS ポータル サイトのプレリリース ビルドへのアクセス<!-- 1734766 -->
Microsoft AutoUpdate を使用すれば、Insider Program に参加することにより、早期にビルドを受け取るためにサインアップできます。 サインアップすると、エンド ユーザーが使用できるようになる前に更新されたポータル サイトを使用できます。 詳細については、[Microsoft Intune に関するブログ](https://blogs.technet.microsoft.com/intunesupport/2018/07/13/use-microsoft-autoupdate-for-early-access-to-the-macos-company-portal-app/) を参照してください。

### <a name="device-configuration"></a>デバイスの構成

#### <a name="create-device-compliance-policy-using-firewall-settings-on-macos-devices---1497640---"></a>macOS デバイスでファイアウォール設定を使ってデバイスのコンプライアンス ポリシーを作成する<!-- 1497640 -->
macOS の新しいコンプライアンス ポリシーを作成するとき ( **[デバイスのポリシー準拠]**  >  **[ポリシー]**  >  **[ポリシーの作成]**  >  **[プラットフォーム: macOS]**  >  **[システム セキュリティ]** )、**ファイアウォール**に関するいくつかの新しい設定を使用できます。 

- **ファイアウォール**: ご利用の環境における着信接続の処理方法を構成します。
- **着信接続**: DHCP、Bonjour、IPSec など、基本的なインターネット サービスに必要な接続を除き、すべての着信接続を **[ブロック]** します。 この設定は、すべての共有サービスもブロックします。
- **ステルス モード**: ステルス モードを **[有効]** にして、デバイスがプローブ要求に応答するのを防ぎます。 デバイスは引き続き、許可されているアプリに関する着信要求に応答します。

適用対象: macOS 10.12 以降

#### <a name="new-wi-fi-device-configuration-profile-for-windows-10-and-later---1879077---"></a>Windows 10 以降用の新しい Wi-Fi デバイス構成プロファイル<!-- 1879077 -->
現時点では、XML ファイルを使用して、Wi-Fi プロファイルをインポートおよびエクスポートすることができます。 この更新プログラムを使用すると、他のプラットフォームの場合と同じように、Intune で直接 Wi-Fi デバイス構成プロファイルを作成できるようになります。

プロファイルを作成するには、 **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  >  **[Windows 10 以降]**  >  **[Wi-Fi]** の順に開きます。 

Windows 10 以降に適用されます。

#### <a name="kiosk---obsolete-is-grayed-out-and-cant-be-changed---2149998---"></a>[Kiosk - obsolete]\(キオスク - 古い) が灰色で表示され、変更できない<!-- 2149998 -->
キオスク (プレビュー) の機能 ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  >  **[Windows 10 以降]**  >  **[デバイスの制限]** ) は使用されなくなり、[Windows 10 以降用のキオスク設定](../configuration/kiosk-settings.md)に置き換えられます。 この更新プログラムを使用すると、 **[Kiosk - Obsolete]\(キオスク - 古い)** 機能は灰色で表示され、ユーザー インターフェイスの変更や更新はできません。 

キオスク モードを有効にする場合は、[Windows 10 以降用のキオスクの設定](../configuration/kiosk-settings.md)に関するページを参照してください。

Windows 10 以降、Windows Holographic for Business に適用されます

#### <a name="apis-to-use-3rd-party-certification-authorities---2184013---"></a>サード パーティ証明機関を使用する API<!-- 2184013 -->
この更新プログラムでは、Java API でサード パーティ証明機関を使用して、Intune と SCEP を統合できるようになります。 その後、ユーザーは SCEP 証明書をプロファイルに追加し、MDM を使用してデバイスに適用できます。

現時点では、Intune で [Active Directory 証明書サービスを使用する SCEP 要求](../protect/certificates-scep-configure.md)がサポートされています。

#### <a name="toggle-to-show-or-not-show-the-end-session-button-on-a-kiosk-browser---2455253---"></a>キオスク ブラウザーで [セッションの終了] ボタンの表示と非表示を切り替える<!-- 2455253 -->
キオスク ブラウザーに [セッションの終了] ボタンを表示するかどうかを構成できるようになりました。 コントロールは **[デバイス構成]**  >  **[キオスク (プレビュー)]**  >  **[キオスク Web ブラウザー]** で表示できます。 有効にした場合、ユーザーがボタンをクリックしたときに、アプリでセッションを終了するための構成が求められます。 確認すると、ブラウザーで閲覧データがすべてクリアされ、既定の URL に戻ります。

#### <a name="create-an-esim-cellular-configuration-profile---2564077---"></a>eSIM 携帯電話の構成プロファイルの作成<!-- 2564077 -->
**[デバイス構成]** では、eSIM 携帯電話のプロファイルを作成することができます。 携帯電話会社によって提供される携帯電話のアクティブ化コードを含むファイルをインポートできます。 その後、これらのプロファイルを、Surface Pro LTE やその他の eSIM 対応デバイスなど、eSIM LTE を有効にした Windows 10 デバイスに展開することができます。

ご利用の[デバイスで eSIM プロファイルがサポートされている](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data)かどうかを確認してください。

Windows 10 以降に適用されます。

#### <a name="select-device-categories-by-using-the-access-work-or-school-settings---1058963-eenotready---"></a>[職場または学校にアクセスする] 設定を使用したデバイス カテゴリの選択<!-- 1058963 eenotready --> 
[デバイス グループ マッピング](../enrollment/device-group-mapping.md)を有効にした場合、 **[設定]**  >  **[アカウント]**  >  **[職場または学校にアクセスする]** の **[接続]** から登録後、または Windows 10 のユーザーはデバイス カテゴリの選択を求められるようになります。 

#### <a name="use-samaccountname-as-the-account-username-for-email-profiles---1500307---"></a>電子メール プロファイルのアカウント ユーザー名として sAMAccountName を使用する<!-- 1500307 -->
Android、iOS、および Windows 10 用の電子メール プロファイルのアカウント ユーザー名として、オンプレミスの **sAMAccountName** を使うことができます。 また、Azure Active Directory (Azure AD) の `domain` または `ntdomain` 属性から、ドメインを取得できます。 または、カスタムの静的ドメインを入力します。

この機能を使うには、オンプレミスの Active Directory 環境から Azure AD に `sAMAccountName` 属性を同期する必要があります。

適用対象: [Android](../configuration/email-settings-android.md)、[iOS](../configuration/email-settings-ios.md)、[Windows 10 以降](../configuration/email-settings-windows-10.md)

#### <a name="see-device-configuration-profiles-in-conflict---1556983---"></a>競合しているデバイス構成プロファイルの確認<!-- 1556983 -->
**[デバイス構成]** には、既存のプロファイルのリストが表示されます。 今回の更新プログラムでは、競合しているプロファイルに関する詳細を示す新しい列が追加されます。 競合する行を選択することで、競合しているプロファイルと設定を確認できます。 

詳細については、[構成プロファイルの管理](../configuration/device-profile-monitor.md#view-conflicts)に関するページを参照してください。

#### <a name="new-status-for-devices-in-device-compliance---2308882---"></a>デバイスのポリシー準拠でのデバイスの新しい状態<!-- 2308882 -->
**[デバイスのポリシー準拠]**  >  **[ポリシー]** 、該当するポリシー、 **[概要]** の順に選択すると、次の新しい状態が追加されます。
- 成功
- エラー
- 競合
- pending
- 適用不可。異なるプラットフォームのデバイス数を示すイメージも表示されます。 たとえば、iOS プロファイルを見ている場合、新しいタイルでは、そのプロファイルに割り当てられている iOS 以外のデバイスの数も示されます。 [デバイス コンプライアンス ポリシー](../protect/compliance-policy-monitor.md#view-status-of-device-policies)に関するポリシーを参照してください。

#### <a name="device-compliance-supports-3rd-party-anti-virus-solutions---2325484---"></a>デバイスのコンプライアンスはサード パーティのウイルス対策ソリューションをサポートする<!-- 2325484 -->
デバイス コンプライアンス ポリシーを作成する場合 ( **[デバイスのポリシー準拠]**  >  **[ポリシー]**  >  **[ポリシーの作成]**  >  **[プラットフォーム: Windows 10 以降]**  >  **[設定]**  >  **[システム セキュリティ]** )、新しい **[デバイス セキュリティ](../protect/compliance-policy-create-windows.md)** オプションを利用できます。 
- **[ウイルス対策]** : **[必要]** に設定すると、Windows Security Center に登録されている Symantec や Windows Defender などのウイルス対策ソリューションを使って、コンプライアンスを確認できます。 
- **[スパイウェア対策]** : **[必要]** に設定すると、Windows Security Center に登録されている Symantec や Windows Defender などのスパイウェア対策ソリューションを使って、コンプライアンスを確認できます。 

適用対象:Windows 10 以降 

### <a name="device-enrollment"></a>デバイスの登録

#### <a name="automatically-mark-android-devices-enrolled-by-using-samsung-knox-mobile-enrollment-as-corporate---2404851---"></a>Samsung Knox Mobile Enrollment を使用して登録された Android デバイスを自動的に "企業" としてマークする。<!-- 2404851 -->
既定で、Samsung Knox Mobile Enrollment を使用して登録された Android デバイスは、 **[デバイスの所有権]** に**企業**としてマークされるようになりました。 Knox Mobile Enrollment を使用して登録する前に、IMEI やシリアル番号を使って企業のデバイスを手動で特定する必要はありません。

#### <a name="devices-without-profiles-column-in-the-list-of-enrollment-program-tokens---1853904---"></a>登録プログラム トークンのリスト内にあるプロファイルを持たないデバイスを示す列<!-- 1853904 -->
登録プログラムのトークン リストには、プロファイルが割り当てられていないデバイスの数を示す新しい列があります。 この列は、管理者が、そのようなデバイスをユーザーに渡す前に、プロファイルを割り当てるのに役立ちます。 新しい列を参照するには、 **[デバイスの登録]**  >  **[Apple の登録]**  >  **[Enrollment Program トークン]** の順に選択します。

### <a name="device-management"></a>デバイス管理

#### <a name="bulk-delete-devices-on-devices-blade---1793693---"></a>デバイス ブレードでのデバイスの一括削除<!-- 1793693 -->
[デバイス] ブレードでは、一度に複数のデバイスを削除できるようになりました。 **[デバイス]**  >  **[すべてのデバイス]** 、削除するデバイス、 **[削除]** の順に選択します。 削除できないデバイスについては、アラートが表示されます。

#### <a name="google-name-changes-for-android-for-work-and-play-for-work--842873---"></a>Android for Work および Play for Work の Google 名の変更<!--842873 -->
Intune では、Google ブランドの変更を反映するように "Android for Work" の用語が更新されました。 "Android for Work" および "Play for Work" という用語は使われなくなりました。 コンテキストに応じて異なる用語が使われます。
- "Android エンタープライズ" は、最新の Android 管理スタック全体を指します。
- "Work profile" または "Profile Owner" は、作業プロファイルで管理されている BYOD デバイスを指します。
- "Managed Google Play" は、Google アプリ ストアを指します。

#### <a name="rules-for-removing-devices---1609459---"></a>デバイス削除のルール<!-- 1609459 -->
設定した日数の間チェックインしていないデバイスを自動的に削除する新しいルールを使用できます。 新しいルールを表示するには、 **[Intune]** ウィンドウ、 **[デバイス]** 、 **[デバイスのクリーンアップ ルール]** の順に選択します。

#### <a name="corporate-owned-single-use-support-for-android-devices---1630973---"></a>Android デバイスの会社所有、単一使用のサポート<!-- 1630973 -->

Intune は、高度に管理されてロック ダウンされた、キオスク スタイルの Android デバイスをサポートするようになりました。 これにより、管理者は、デバイスの使用を 1 つのアプリまたはアプリの小さなセットにさらにロックダウンし、ユーザーが他のアプリを有効にしたり、デバイスで他の操作を実行したりすることを禁止できます。 Android キオスクを設定するには、Intune > **[デバイスの登録]**  >  **[Android の登録]**  >  **[Kiosk and task device enrollments]\(キオスクおよびタスク デバイス登録\)** の順に進みます。 詳細については、[Android エンタープライズ キオスク デバイスの登録の設定](../enrollment/android-kiosk-enroll.md)に関するページを参照してください。

#### <a name="per-row-review-of-duplicate-corporate-device-identifiers-uploaded---2203794--"></a>アップロードされた重複する業務用デバイス ID の行ごとのレビュー<!-- 2203794-->
業務用 ID をアップロードすると、重複の一覧が提供され、既存の情報を置き換えるか、保持することができるようになりました。 **[デバイスの登録]**  >  **[業務用デバイスの ID]**  >  **[ID の追加]** を選ぶと、重複がある場合はレポートが表示されます。 

#### <a name="manually-add-corporate-device-identifiers---2203803---"></a>業務用デバイスの ID を手動で追加する<!-- 2203803 -->
業務用デバイスの ID を手動で追加できるようになりました。 **[デバイスの登録]**  >  **[業務用デバイスの ID]**  >  **[追加]** の順に選びます。 


<!-- ########################## -->
## <a name="june-2018"></a>2018 年 6 月

### <a name="app-management"></a>アプリ管理

#### <a name="microsoft-edge-mobile-support-for-intune-app-protection-policies---1817882---"></a>Microsoft Edge モバイルでの Intune アプリ保護ポリシーのサポート<!-- 1817882 -->
モバイル デバイス向けの Microsoft Edge ブラウザーで、Intune で定義されるアプリ保護ポリシーがサポートされるようになりました。

#### <a name="retrieve-the-associated-app-user-model-id-aumid-for-microsoft-store-for-business-apps-in-kiosk-mode---1560077----"></a>キオスク モードのビジネス向け Microsoft Store アプリの関連付けられたアプリ ユーザー モデル ID (AUMID) を取得する<!-- 1560077 ! -->
Intune で、ビジネス向け Microsoft Store (WSfB) アプリのアプリ ユーザー モデル ID (AUMID) を取得して、キオスク プロファイルの構成を改善できるようになりました。

ビジネス向け Microsoft Store アプリについて詳しくは、「[ビジネス向け Microsoft Store からのアプリの管理](../apps/windows-store-for-business.md)」をご覧ください。

#### <a name="new-company-portal-branding-page---1916370---"></a>新しいポータル サイトのブランド化ページ<!-- 1916370 -->
ポータル サイトのブランド化ページには、新しいレイアウト、メッセージ、ヒントがあります。


### <a name="device-configuration"></a>デバイスの構成

#### <a name="pradeo---new-mobile-threat-defense-partner---1169249---"></a>Pradeo - 新しい Mobile Threat Defense パートナー<!-- 1169249 -->
Microsoft Intune に統合されたモバイル脅威保護ソリューションである Pradeo によって実行されるリスク評価に基づき、条件付きアクセスを利用し、モバイル デバイスから会社のリソースへのアクセスを制御できます。

#### <a name="use-fips-mode-with-the-ndes-certificate-connector---1333688---"></a>NDES 証明書コネクタで FIPS モードを使用する<!-- 1333688 -->
Federal Information Processing Standard (FIPS) モードが有効な NDES 証明書コネクタをコンピューターにインストールすると、証明書の発行や無効化が期待どおりに動作しません。 この更新プログラムでは、NDES 証明書コネクタに FIPS のサポートが含まれています。 

この更新プログラムには、次も含まれています。

- NDES 証明書コネクタには、Windows Server 2016 と Windows Server 2012 R2 に自動的に含まれる .NET 4.5 Framework が必要です。 これまでは、最小で .NET 3.5 Framework バージョンが必須でした。
- NDES 証明書コネクタには、TLS 1.2 のサポートが含まれています。 したがって、NDES 証明書コネクタがインストールされているサーバーが TLS 1.2 をサポートする場合、TLS 1.2 が使用されます。 サーバーが TLS 1.2 をサポートしない場合、TLS 1.1 が使用されます。 現在、デバイスとサーバー間の認証には、TLS 1.1 が使用されています。

詳細については、[SCEP 証明書の構成と使用](../protect/certificates-scep-configure.md)と、[PKCS 証明書の構成と使用](../protect/certficates-pfx-configure.md)に関するページを参照してください。

#### <a name="support-for-palo-alto-networks-globalprotect-vpn-profiles---1333680----"></a>Palo Alto Networks GlobalProtect VPN プロファイルのサポート<!-- 1333680 ! -->
今回の更新で、Intune での VPN プロファイルの VPN 接続の種類として、Palo Alto Networks GlobalProtect を選択できるようになりました ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  >  **[プロファイルの種類]**  >  **[VPN]** )。 このリリースでは、次のプラットフォームがサポートされます。 

- iOS
- Windows 10

#### <a name="additions-to-local-device-security-options-settings---1403702---"></a>ローカル デバイス セキュリティ オプションの設定への追加<!-- 1403702 -->
Windows 10 デバイスに対して追加のローカル デバイス セキュリティ オプションの設定を構成できるようになりました。 追加設定を利用できるのは、Microsoft ネットワーク クライアント、Microsoft ネットワーク サーバー、ネットワーク アクセスとセキュリティ、および対話型ログオンなどに関する部分です。 これらの設定は、Windows 10 デバイスの構成ポリシーを作成するときに、[Endpoint Protection] カテゴリに表示されます。

#### <a name="enable-kiosk-mode-on-windows-10-devices---1560072----"></a>Windows 10 デバイスでキオスク モードを有効にする<!-- 1560072 ! -->
Windows 10 デバイスでは、構成プロファイルを作成して、キオスク モードを有効にすることができます ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  >  **[Windows 10]**  >  **[デバイスの制限]**  >  **[キオスク]** )。 この更新では、 **[キオスク (プレビュー)]** の設定の名前が **[キオスク (古い)]** に変更されています。 **[キオスク (古い)]** は使用を推奨されませんが、7 月の更新までは機能し続けます。 **[キオスク (古い)]** は新しい **[キオスク]** プロファイルの種類に置き換えられ ( **[プロファイルの作成]**  >  **[Windows 10]**  >  **[キオスク (プレビュー)]** )、Windows 10 RS4 以降でキオスクを構成する設定が含まれます。

Windows 10 以降に適用されます。

#### <a name="device-profile-graphical-user-chart-is-back---2160133---"></a>デバイス プロファイルのグラフィカル ユーザー グラフが戻った<!-- 2160133 -->
デバイス プロファイルのグラフィカルなグラフに表示される数値カウントの向上で ( **[デバイス構成]**  >  **[プロファイル]** > 既存のプロファイルを選択 > **[概要]** )、グラフィカルなユーザー グラフが一時的に削除されました。

この更新では、グラフィカル ユーザー グラフが元に戻り、Azure portal に表示されます。

### <a name="device-enrollment"></a>デバイスの登録

#### <a name="support-for-windows-autopilot-enrollment-without-user-authentication---1165118---"></a>ユーザー認証なしの Windows Autopilot 登録のサポート<!-- 1165118 -->
Intune では、ユーザー認証なしの Windows Autopilot 登録がサポートされるようになりました。 これは Windows Autopilot Deployment プロファイルの新しいオプションであり、"Autopilot Deployment モード" が "自己配置" に設定されます。  デバイスでは Windows 10 Insider プレビュー ビルド 17672 以降を実行しており、この種類の登録を正常に完了させるために TPM 2.0 チップがある必要があります。 ユーザー認証は不要であるため、このオプションを割り当てる必要があるのは、物理的に制御できるデバイスのみとなります。

#### <a name="new-languageregion-setting-when-configuring-oobe-for-autopilot---1821766---"></a>Autopilot の OOBE を構成するときの新しい言語/リージョンの設定<!-- 1821766 -->
Out of Box Experience (OOBE) の間に、Autopilot プロファイルの言語とリージョンを設定する、新しい構成設定を使用できます。 新しい設定を表示するには、 **[デバイスの登録]**  >  **[Windows の登録]**  >  **[Deployment profiles]\(展開プロファイル\)**  >  **[プロファイルの作成]**  >  **[配置モード]**  =  **[Self-deploying]\(自己配置\)**  >  **[既定値が構成済み]** の順に選択します。

#### <a name="new-setting-for-configuring-device-keyboard---1821768---"></a>デバイス キーボードを構成するための新しい設定<!-- 1821768 -->
Out of Box Experience (OOBE) の間に、Autopilot プロファイルのキーボードを構成する新しい設定を使用できます。 新しい設定を表示するには、 **[デバイスの登録]**  >  **[Windows の登録]**  >  **[Deployment profiles]\(展開プロファイル\)**  >  **[プロファイルの作成]**  >  **[配置モード]**  =  **[Self-deploying]\(自己配置\)**  >  **[既定値が構成済み]** の順に選択します。

#### <a name="autopilot-profiles-moving-to-group-targeting---1877935---"></a>Autopilot プロファイルの対象がグループに移動<!-- 1877935 -->
AutoPilot 展開プロファイルは AutoPilot デバイスを含む Azure AD のグループに割り当てることができます。

### <a name="device-management"></a>デバイス管理

#### <a name="set-compliance-by-device-location---851881----"></a>デバイスの場所によるコンプライアンスの設定<!-- 851881 ! -->
状況によっては、ネットワーク接続で定義される特定の場所に、企業リソースへのアクセスを制限することが必要な場合あります。 デバイスの IP アドレスに基づき、コンプライアンス ポリシーを作成できるようになりました ( **[デバイスのポリシー準拠]**  >  **[場所]** )。 デバイスが IP 範囲外に移動した場合、デバイスは会社のリソースにアクセスできません。

適用対象:Android デバイス 6.0 以降 (ポータル サイト アプリ更新済み)

#### <a name="prevent-consumer-apps-and-experiences-on-windows-10-enterprise-rs4-autopilot-devices---1621980---"></a>Windows 10 Enterprise RS4 Autopilot デバイスでのコンシューマー アプリおよびエクスペリエンスの禁止<!-- 1621980 -->
Windows 10 Enterprise RS4 Autopilot デバイスへのコンシューマー アプリおよびエクスペリエンスのインストールを禁止することができます。 この機能を表示するには、 **[Intune]**  >  **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  >  **[プラットフォーム]**  =  **[Windows 10 or later]\(Windows 10 以降\)**  >  **[プロファイルの種類]**  =  **[デバイスの制限]**  >  **[構成]**  >  **[Windows スポットライト]**  >  **[コンシューマー向けの機能]** の順に移動します。 

#### <a name="uninstall-the-latest-from-windows-10-software-updates---1732948---"></a>Windows 10 ソフトウェア更新プログラムの最新のものをアンインストールする<!-- 1732948 -->
Windows 10 コンピューターで重大な問題が見つかった場合は、最新の機能更新プログラムまたは最新の品質更新プログラムをアンインストール (ロールバック) できます。 機能更新プログラムまたは品質更新プログラムをアンインストールできるのは、デバイスが存在するサービス チャネルの場合のみです。 アンインストールすると、Windows 10 コンピューター上の以前の更新プログラムを復元するためのポリシーがトリガーされます。 機能更新プログラムの場合、最新バージョンのアンインストールを適用できる期間を 2 日から 60 日間で制限できます。 ソフトウェア更新プログラムのアンインストール オプションを設定するには、Azure Portal 内の **[Microsoft Intune]** ブレードで **[ソフトウェア更新プログラム]** を選択します。 次に、 **[ソフトウェア更新プログラム]** ブレードで **[Windows 10 更新プログラムのリング]** を選択します。 これで、 **[概要]** セクションから **[アンインストール]** オプションを選択できます。

#### <a name="search-all-devices-for-imei-and-serial-number---1793685---"></a>すべてのデバイスで IMEI およびシリアル番号を検索する<!-- 1793685 -->
[すべてのデバイス] ブレードで IMEI およびシリアル番号を検索できるようになりました (電子メール、UPN、デバイス名、管理名は引き続き使用できます)。 Intune で、 **[デバイス]**  >  **[すべてのデバイス]** の順に選択し、検索ボックスに検索語句を入力します。

#### <a name="management-name-field-will-be-editable---1875989---"></a>管理名フィールドが編集可能になる<!-- 1875989 -->
デバイスの **[プロパティ]** ブレードで、管理名フィールドを編集できるようになりました。 このフィールドを編集するには、 **[デバイス]**  >  **[すべてのデバイス]** > デバイスを選択 > **[プロパティ]** の順に選びます。 管理名フィールドを使って、デバイスを一意に識別できます。

#### <a name="new-all-devices-filter-device-category---1878520---"></a>新しい [すべてのデバイス] フィルター処理: デバイスのカテゴリ<!-- 1878520 -->
デバイスのカテゴリごとに **[すべてのデバイス]** リストをフィルター処理できるようになりました。 これを行うには、 **[デバイス]**  >  **[すべてのデバイス]**  >  **[フィルター]**  >  **[デバイスのカテゴリ]** の順に選択します。

#### <a name="use-teamviewer-to-screen-share-ios-and-macos-devices---1985547---"></a>TeamViewer を使用して iOS デバイスと MacOS デバイスの画面を共有する<!-- 1985547 -->
管理者は [TeamViewer](../remote-actions/teamviewer-support.md) に接続し、iOS および macOS デバイスとの画面共有セッションを開始できるようになりました。 iPhone、iPad、macOS ユーザーは、他のデスクトップ デバイスまたはモバイル デバイスと画面をライブで共有できます。 

#### <a name="multiple-exchange-connector-support---2070451---"></a>複数の Exchange Connector のサポート<!-- 2070451 -->
テナントごとの Microsoft Intune Exchange Connector の数が 1 個だけという制限がなくなりました。 Intune で複数の Exchange Connector がサポートされ、複数のオンプレミス Exchange の組織で Intune の条件付きアクセスを設定できるようになりました。

Intune のオンプレミス Exchange Connector を使うと、デバイスが Intune に登録されているかどうか、およびデバイスが Intune のデバイス コンプライアンス ポリシーに準拠しているかどうかに基づいて、お使いのオンプレミスの Exchange メールボックスに対するデバイス アクセスを管理できます。 コネクタを設定するには、Azure Portal から Intune のオンプレミス Exchange Connector をダウンロードして、Exchange の組織内のサーバーにインストールします。 Microsoft Intune ダッシュ ボードで **[オンプレミス アクセス]** を選択し、 **[セットアップ]** で **[Exchange ActiveSync のコネクタ]** を選択します。 Exchange のオンプレミス コネクタをダウンロードし、Exchange の組織内のサーバーにインストールします。 テナントごとに 1 個という Exchange Connector の制限がなくなったので、他に Exchange の組織がある場合は、他の各 Exchange の組織にも同じ手順でコネクタをダウンロードしてインストールできます。

#### <a name="new-device-hardware-detail-ccid---2156657---"></a>新しいデバイス ハードウェアの詳細: CCID<!-- 2156657 -->
CCID (Chip Card Interface Device) 情報がデバイスごとに含まれるようになりました。 これを表示するには、 **[デバイス]**  >  **[すべてのデバイス]** の順に選択します。次に、該当するデバイス、 **[ハードウェア]** の順に選び、 **[ネットワークの詳細]** の下を確認します。

#### <a name="assign-all-users-and-all-devices-as-scope-groups---2196803---"></a>スコープ グループとしてすべてのユーザーとすべてのデバイスを割り当てる<!-- 2196803 -->
スコープ グループ内のすべてのユーザー、すべてのデバイス、およびすべてのユーザーとすべてのデバイスを割り当てられるようになりました。 これを行うには、 **[Intune の役割]**  >  **[すべてのロール]**  >  **[Policy and profile manager]\(ポリシーとプロファイル マネージャー\)**  >  **[割り当て]** の順に選び、割り当てを選んで、 **[スコープ (グループ)]** を選びます。

#### <a name="udid-information-now-included-for-ios-and-macos-devices---2219806---"></a>iOS および macOS デバイスの UDID 情報が含まれるようになりました<!-- 2219806 -->
iOS および macOS デバイスの UDID (一意のデバイス識別子) を表示するには、 **[デバイス]**  >  **[すべてのデバイス]** の順に選択します。次に、該当するデバイス、 **[ハードウェア]** の順に選びます。 UDID は会社のデバイスでのみ利用できます ( **[デバイス]**  >  **[すべてのデバイス]** 、該当するデバイス、 **[プロパティ]**  >  **[デバイスの所有権]** の順に選択して設定した場合)。

### <a name="intune-apps"></a>Intune アプリ

#### <a name="improved-troubleshooting-for-app-installation---928990---"></a>アプリのインストールのトラブルシューティングの向上<!-- 928990 -->
Microsoft Intune の MDM で管理されたデバイスでは、アプリのインストールが失敗することがあります。 アプリのインストールが失敗した場合、失敗の理由を理解したり、問題をトラブルシューティングするのが難しい場合があります。 アプリ トラブルシューティング機能のパブリック プレビューが提供されています。 各デバイスの下に **[管理対象アプリ]** という新しいノードがあります。 これには、Intune MDM 経由で配布されたアプリが表示されます。 ノード内では、アプリのインストール状態が一覧表示されます。 個々のアプリを選ぶと、その特定のアプリのトラブルシューティング ビューが表示されます。 トラブルシューティング ビューでは、アプリが作成、変更、ターゲット指定、デバイス配布されたときなど、アプリのエンド ツー エンドのライフサイクルが表示されます。 さらに、アプリのインストールが成功しなかった場合は、エラー コードとエラーの原因に関する便利なメッセージが表示されます。 

#### <a name="intune-app-protection-policies-and-microsoft-edge---1818968---"></a>Intune アプリ保護ポリシーと Microsoft Edge<!-- 1818968 -->
モバイル デバイス (iOS と Android) 向けの Microsoft Edge ブラウザーが Microsoft Intune アプリ保護ポリシー対応になりました。 Microsoft Edge アプリケーションで企業の Azure AD アカウントを使用してサインインした iOS および Android デバイスのユーザーは、Intune によって保護されます。 管理されている iOS デバイスでは、 **[Require managed browser for web content]** \(Web コンテンツに管理されているブラウザーが必要\) ポリシーにより、ユーザーは Microsoft Edge でリンクを開くことができます。

<!-- ########################## -->
## <a name="may-2018"></a>2018 年 5 月

### <a name="app-management"></a>アプリ管理

#### <a name="configuring-your-app-protection-policies---2144597-part-2---"></a>アプリ保護ポリシーの構成<!-- 2144597 Part 2 -->

Azure portal では、Intune App Protection サービス ブレードに移動する代わりに、Intune に移動するようになりました。 Intune 内のアプリ保護ポリシーのための場所は 1 つだけになりました。 すべてのアプリ保護ポリシーが Intune の**アプリ保護ポリシー**の **[モバイル アプリ]** ブレードに置かれていることに注意してください。 この統合は、クラウド管理の簡素化に役立ちます。 ただし、すべてのアプリ保護ポリシーが既に Intune にあり、以前に構成した任意のポリシーを変更することができます。 Intune アプリ ポリシー保護 (APP) および条件付きアクセス (CA) ポリシーは現在、 **[条件付きアクセス]** の下にあります。[条件付きアクセス] は、 **[Microsoft Intune]** ブレードの **[管理]** セクション、または **[Azure Active Directory]** ブレードの **[セキュリティ]** セクションにあります。 条件付きアクセス ポリシーの変更の詳細については、「[Azure Active Directory の条件付きアクセス](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)」を参照してください。 その他の情報については、「[アプリ保護ポリシーとは](../apps/app-protection-policy.md)」をご覧ください。

### <a name="device-configuration"></a>デバイスの構成

#### <a name="require-installation-of-policies-apps-certificate-and-network-profiles---1553555---"></a>ポリシー、アプリ、証明書、およびネットワーク プロファイルのインストールを必要にする<!-- 1553555 -->
管理者は、AutoPilot デバイスのプロビジョニングの間、Intune がポリシー、アプリ、証明書、ネットワーク プロファイルをインストールするまで、エンド ユーザーによる Windows 10 RS4 デスクトップへのアクセスをブロックすることができます。 詳細については、「[登録ステータス ページを設定する](../enrollment/windows-enrollment-status.md)」を参照してください。

### <a name="device-enrollment"></a>デバイスの登録

#### <a name="samsung-knox-mobile-enrollment-support--1112863--"></a>Samsung Knox Mobile Enrollment のサポート<!--1112863-->
Knox Mobile Enrollment (KME) で Intune を使用すると、企業が所有する多数の Android デバイスを登録できます。 WiFi または移動体通信ネットワークのユーザーは、初めてデバイスをオンにしたときに、ほんの数タップで登録できます。 Knox Deployment App を使うと、Bluetooth または NFC を使ってデバイスを登録することもできます。 詳しくは、「[Samsung の Knox Mobile Enrollment を使用して Android デバイスを自動的に登録する](../enrollment/android-samsung-knox-mobile-enroll.md)」をご覧ください。

### <a name="monitor-and-troubleshoot"></a>監視とトラブルシューティング 

#### <a name="requesting-help-in-the-company-portal-for-windows-10---1874137---"></a>Windows 10 ポータル サイト でのヘルプの要求<!-- 1874137 -->
ユーザーが問題に関するヘルプを入手するワークフローを開始すると、Windows 10 用 Intune ポータル サイトは Microsoft に直接アプリのログを送信するようになります。 これにより、Microsoft に問題を送ってすばやくトラブルシューティングして解決できます。

<!-- ########################## -->
## <a name="april-2018"></a>2018 年 4 月

### <a name="app-management"></a>アプリ管理

#### <a name="passcode-support-for-mam-pin-on-android---1438086---"></a>Android での MAM PIN のパスコードのサポート<!-- 1438086 -->

Intune 管理者は、アプリケーション起動要件を設定して、数値の MAM PIN の代わりにパスコードを強制することができます。 構成した場合、ユーザーは、MAM 対応のアプリケーションにアクセスする前に、要求された時点で、パスコードを設定および使用する必要があります。 パスコードは、少なくとも 1 つの特殊文字または大文字/小文字アルファベットを含む数値 PIN と定義されます。 Intune によるパスコードのサポート方法は既存の数値 PIN と似ており、管理コンソールで最小の長さを設定したり、文字やシーケンスの繰り返しを許可したりできます。 この機能を利用するには、Android に最新バージョンの Intune ポータル サイトが必要です。 この機能は、iOS では既に利用できます。

#### <a name="line-of-business-lob-app-support-for-macos---1473977---"></a>macOS の基幹業務 (LOB) アプリのサポート<!-- 1473977 -->
Microsoft Intune では、Azure Portal から macOS LOB アプリをインストールできます。 GitHub で利用可能なツールを使って前処理した macOS LOB アプリを、Intune に追加できます。 Azure portal で、 **[Intune]** ブレードから **[クライアント アプリ]** を選択します。 **[クライアント アプリ]** ブレードで、 **[アプリ]**  >  **[追加]** の順に選択します。 **[アプリの追加]** ブレードで、 **[基幹業務アプリ]** を選択します。 

#### <a name="built-in-all-users-and-all-devices-group-for-android-enterprise-work-profile-app-assignment---1813073---"></a>Android エンタープライズ仕事用プロファイルのアプリの割り当て用の、組み込みのすべてのユーザー グループとすべてのデバイス グループ<!-- 1813073 -->
Android エンタープライズ仕事用プロファイルのアプリの割り当て用に、組み込みの **[すべてのユーザー]** グループと **[すべてのデバイス]** グループを利用できます。 詳細については、「[Microsoft Intune でのアプリ割り当ての組み込みと除外](../apps/apps-inc-exl-assignments.md)」を参照してください。

#### <a name="intune-will-reinstall-required-apps-that-are-uninstalled-by-users---1947010---"></a>ユーザーがアンインストールした必要なアプリは Intune によって再インストールされる<!-- 1947010 -->
エンド ユーザーが必要なアプリをアンインストールした場合、Intune は 7 日間の再評価サイクルを待機するのではなく、24 時間以内に該当するアプリを自動的に再インストールします。

#### <a name="update-where-to-configure-your-app-protection-policies---2144597---"></a>アプリの保護ポリシーを構成する場所を更新<!-- 2144597 -->

Microsoft Intune サービス内の Azure Portal で、ユーザーが一時的に **[Intune App Protection]** サービス ブレードから **[モバイル アプリ]** ブレードにリダイレクトされます。 すべてのアプリ保護ポリシーが Intune のアプリ構成の **[モバイル アプリ]** ブレードに既に置かれていることに注意してください。 Intune App Protection に移動する代わりに、Intune に移動します。 2018 年 4 月にリダイレクトを停止し、 **[Intune App Protection]** サービス ブレードを完全に削除する予定です。したがって、Intune 内のアプリ保護ポリシーのための場所は 1 つだけになります。 

**ユーザーへの影響**
この変更は、Intune スタンドアロンのお客様とハイブリッド (Intune と Configuration Manager) のお客様の両方に影響します。 この統合は、クラウド管理の簡素化に役立ちます。

**この変更に対して必要な準備**
**[Intune App Protection]** サービス ブレードの代わりに **Intune** をお気に入りとして登録し、Intune の **[モバイル アプリ]** ブレードのアプリ保護ポリシーのワークフローを習熟してください。 リダイレクトを短期間行い、その後 **[Intune App Protection]** ブレードを削除します。 すべてのアプリ保護ポリシーが既に Intune にあり、任意の条件付きアクセス ポリシーを変更できることを思い出してください。 条件付きアクセス ポリシーの変更の詳細については、「[Azure Active Directory の条件付きアクセス](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)」を参照してください。 その他の情報については、「[アプリ保護ポリシーとは](../apps/app-protection-policy.md)」をご覧ください。 

### <a name="device-configuration"></a>デバイスの構成

#### <a name="device-profile-chart-and-status-list-show-all-devices-in-a-group---1449153---"></a>デバイス プロファイル チャートと状態リストでグループ内のすべてのデバイスが表示されるようになる<!-- 1449153 -->
デバイス プロファイルを構成するときは ( **[デバイス構成]**  >  **[プロファイル]** )、iOS などのデバイス プロファイルを選択します。 このプロファイルを、iOS デバイスと iOS 以外のデバイスを含むグループに割り当てます。 グラフィカル チャートの数では、プロファイルが iOS デバイス "*および*" iOS 以外のデバイスに適用されているように示されます ( **[デバイス構成]**  >  **[プロファイル]** > 既存のプロファイルを選択 > **[概要]** )。 **[概要]** タブでグラフィカル チャートを選択すると、 **[デバイスの状態]** に、iOS デバイスだけではなく、グループ内のすべてのデバイスが一覧表示されます。 

この更新により、グラフィカル チャート ( **[デバイス構成]**  >  **[プロファイル]** > 既存のプロファイルを選択 > **[概要]** ) では、特定のデバイス プロファイルの数のみが表示されるようになります。 たとえば、構成デバイス プロファイルが iOS デバイスに適用される場合、チャートの一覧には iOS デバイスの数だけが表示されます。 グラフィカル チャートを選択すると開く **[デバイスの状態]** では、iOS デバイスだけが一覧表示されます。

この更新が行われている間、グラフィカル ユーザー チャートは一時的に削除されます。 

#### <a name="always-on-vpn-for-windows-10--1333666---"></a>Windows 10 の Always On VPN<!--1333666 -->

現在、[Always On](https://docs.microsoft.com/windows/security/identity-protection/vpn/vpn-auto-trigger-profile#always-on) は、OMA-URI を使って作成されたカスタム仮想プライベート ネットワーク (VPN) プロファイルを使うことで、Windows 10 デバイスで使用できます。

この更新では、管理者は Azure Portal の Intune で直接、Windows 10 VPN プロファイルに対する Always On を有効にできるようになります。 Always On VPN プロファイルは、次のときに自動的に接続します。

- ユーザーが自分のデバイスにサインインしたとき
- デバイスでネットワークが変更されたとき
- デバイスの画面がオフにされた後でオンに戻されたとき

#### <a name="new-printer-settings-for-education-profiles---1308900---"></a>教育プロファイル用の新しいプリンター設定<!-- 1308900 -->

教育プロファイルの場合、 **[プリンター]** カテゴリで次に示す新しい設定を利用できます: **[プリンター]** 、 **[通常使うプリンター]** 、 **[新しいプリンターの追加]** 。

#### <a name="show-caller-id-in-personal-profile---android-enterprise-work-profile--1098984---"></a>個人プロファイルでの発信者番号通知 - Android エンタープライズ仕事用プロファイル<!--1098984 -->
デバイス上で個人プロファイルを使用する場合、勤務先の作業連絡先からの発信者番号の詳細がエンド ユーザーに表示されない場合があります。 

今回の更新では、 **[Android エンタープライズ]**  >  **[デバイスの制限]**  >  **[仕事用プロファイルの設定]** に新しい設定が表示されます。
- 個人プロファイルに勤務先の連絡先の発信者番号を表示する

有効にすると (構成されていない場合)、勤務先の連絡先の発信者番号の詳細が個人プロファイルに表示されます。 ブロックすると、勤務先の連絡先の発信者番号は個人プロファイルに表示されません。 

適用対象:Android OS v6.0 以降の Android 仕事用プロファイル デバイス

#### <a name="new-windows-defender-credential-guard-settings-added-to-endpoint-protection-settings--1102252-----from-1802-and-1804--"></a>Endpoint Protection の設定に追加された新しい Windows Defender Credential Guard の設定<!--1102252 --><!--from 1802 and 1804-->

この更新により、[Windows Defender Credential Guard](https://docs.microsoft.com/windows/access-protection/credential-guard/credential-guard) ( **[デバイス構成]**  >  **[プロファイル]**  >  **[Endpoint Protection]** ) に、次の設定が含まれます。 

- **Windows Defender Credential Guard**: 仮想化ベースのセキュリティによる Credential Guard が有効になります。 **[Platform Security Level with Secure Boot]\(セキュア ブートでのプラットフォーム セキュリティ レベル\)** と **[仮想化ベースのセキュリティ]** の両方が有効な場合にこの機能を有効にすると、次回の再起動時に資格情報を保護することができます。 次のオプションがあります。
  - **[無効]** : 以前に Credential Guard が **[ロックなしで有効化]** オプションで有効になっていた場合に、Credential Guard をリモートで無効にします。

  - **[UEFI ロックで有効化]** : レジストリ キーまたはグループ ポリシーを使って Credential Guard を無効にできないようにします。 この設定を使用した後に Credential Guard を無効にする場合は、グループ ポリシーを [無効] に設定する必要があります。 次に、実際に存在するユーザーの各コンピューターからセキュリティ機能を削除します。 この手順により、UEFI に存在した構成がクリアされます。 UEFI の構成が保持されている限り、Credential Guard は有効になっています。

  - **[ロックなしで有効化]** : グループ ポリシーを使ってリモートで Credential Guard を無効にできるようにします。 この設定を使うデバイスは、Windows 10 (バージョン 1511) 以降を実行している必要があります。

Credential Guard を構成すると、次の関連するテクノロジが自動的に有効になります。 

- **[仮想化ベースのセキュリティ (VBS) を有効にする]** : 仮想化ベースのセキュリティ (VBS) を次の再起動時にオンにします。 仮想化ベースのセキュリティは、Windows ハイパーバイザーを使用してセキュリティ サービスのサポートを提供し、セキュア ブートを要求します。
- **[セキュア ブートと直接メモリ アクセス (DMA)]** : セキュア ブートと直接メモリ アクセスで VBS をオンにします。 DMA 保護は、ハードウェアのサポートを必要とし、正しく構成されたデバイスでのみ有効にされます。 

#### <a name="use-a-custom-subject-name-on-scep-certificate---2064190---"></a>SCEP 証明書でのカスタム サブジェクト名の使用<!-- 2064190 -->
SCEP 証明書プロファイルでカスタム サブジェクトの共通名 **OnPremisesSamAccountName** を使うことができます。 たとえば、`CN={OnPremisesSamAccountName})` のように使用できます。

#### <a name="block-camera-and-screen-captures-on-android-enterprise-work-profiles---1098977---"></a>Android エンタープライズ仕事用プロファイルでカメラと画面キャプチャをブロックする<!-- 1098977 -->
Android デバイスのデバイス制限を構成するときに、次の 2 つの新しいプロパティをブロックに利用できます。 
- カメラ: デバイス上のすべてのカメラへのアクセスを禁止します
- 画面の取り込み: 画面のキャプチャをブロックし、セキュリティで保護されたビデオ出力を持たないディスプレイ デバイスにコンテンツが表示されないようにします

Android エンタープライズ仕事用プロファイルに適用されます。

#### <a name="use-cisco-anyconnect-client-for-ios---1333708---"></a>iOS 向け Cisco AnyConnect クライアントを使用する<!-- 1333708 -->

iOS 用の VPN プロファイルを新規に作成するときに、次の 2 つのオプションを利用できるようになりました。 **[Cisco AnyConnect]** と **[Cisco Legacy AnyConnect]** 。 Cisco AnyConnect プロファイルは、4.0.7x 以降のバージョンに対応しています。 既存の iOS Cisco AnyConnect VPN プロファイルは **[Cisco Legacy AnyConnect]** と表示されるようになり、現在と同じように Cisco AnyConnect 4.0.5x 以前のバージョンで引き続き動作します。

> [!NOTE]
> この変更は iOS にのみ適用されます。 Android、Android エンタープライズ仕事用プロファイル、macOS プラットフォーム向けの Cisco AnyConnect オプションは、これまでどおり 1 つだけです。


### <a name="device-enrollment"></a>デバイスの登録

#### <a name="new-enrollment-steps-for-users-on-devices-with-macos-high-sierra-10132--1734567---"></a>macOS High Sierra 10.13.2 以降のデバイスでのユーザーの新しい登録手順<!--1734567 -->
macOS High Sierra 10.13.2 では、"ユーザー承認済み" MDM 登録の概念が導入されました。 承認済みの登録で、セキュリティ上重要な一部の設定の Intune による管理が許可されます。 詳細については、Apple のサポート ドキュメント https://support.apple.com/HT208019 をご覧ください。

macOS ポータル サイトを使って登録されたデバイスは、エンド ユーザーがシステム環境設定を開いて手動で承認しない限り、"ユーザー承認されていない" ものと見なされます。 そのため、macOS ポータル サイトでは、macOS 10.13.2 以降のユーザーは、登録プロセスの最後に、登録の手動承認に移動するようになりました。 Intune 管理コンソールでは、登録されているデバイスがユーザー承認済みかどうかが示されます。

#### <a name="jamf-enrolled-macos-devices-can-now-register-with-intune---2370684---"></a>Jamf 登録 macOS デバイスを Intune に登録できるようになりました<!-- 2370684 -->
macOS ポータル サイトのバージョン 1.3 と 1.4 では、Jamf デバイスが Intune に正常に登録されませんでした。 macOS ポータル サイトのバージョン 1.4.2 でこの問題が解決されました。

#### <a name="updated-help-experience-in-company-portal-app-for-android---1631531---"></a>Android 用ポータル サイト アプリでのヘルプ エクスペリエンスの更新<!-- 1631531 -->
Android プラットフォームのベスト プラクティスに合うように、Android 用ポータル サイト アプリのヘルプ エクスペリエンスが更新されました。 ご使用のアプリで問題が発生した場合は、 **[メニュー]**  >  **[ヘルプ]** の順にタップして、次のことが行えます。
- 診断ログを Microsoft にアップロードします。
- 問題とインシデント ID を記載した電子メールを社内のサポート担当者に送信する。  

更新されたヘルプ エクスペリエンスを確認するには、[[Send logs using email]\(メールでログを送信\)](/intune-user-help/send-logs-to-your-it-admin-by-email-android) および [[Send errors to Microsoft]\(エラーを Microsoft に送信\)](/intune-user-help/send-logs-to-microsoft-android) に進みます。


#### <a name="new-enrollment-failure-trend-chart-and-failure-reasons-table---1471783---"></a>新しい登録エラー傾向グラフと失敗の理由テーブル<!-- 1471783 -->
[Enrollment Overview]\(登録の概要\) ページで、登録エラーの傾向と、上位 5 つのエラーの原因を表示することができます。 グラフやテーブルをクリックすると、トラブルシューティングのアドバイスや改善の提案の詳細にドリル ダウンすることができます。


### <a name="device-management"></a>デバイス管理

#### <a name="advanced-threat-protection-atp-and-intune-are-fully-integrated---1629303---"></a>Advanced Threat Protection (ATP) と Intune は完全に統合されています<!-- 1629303 -->

[Advanced Threat Protection (ATP)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/dashboard-windows-defender-advanced-threat-protection) では、Windows 10 デバイスのリスク レベルが表示されます。 Windows Defender Security Center (ATP Portal) では、Microsoft Intune への接続を作成できます。 作成後、許容できる脅威レベルの決定に Intune コンプライアンス ポリシーが使用されます。 その脅威レベルを超えた場合、Azure Active Directory (AD) の条件付きアクセス ポリシーによって、組織内のさまざまなアプリへのアクセスを阻止できます。

この機能によって ATP はファイルをスキャンし、脅威を検出し、Windows 10 デバイス上のあらゆるリスクを報告できます。

[Intune で条件付きアクセスによる ATP を有効にする](../protect/advanced-threat-protection.md)方法に関するページを参照してください。

#### <a name="support-for-user-less-devices---1637553---"></a>ユーザーのいないデバイスのサポート<!-- 1637553 -->
Intune は、Microsoft Surface Hub など、ユーザーのいないデバイスでコンプライアンスを評価する機能をサポートします。 コンプライアンス ポリシーは、特定のデバイスを対象にすることができます。 したがって、ユーザーが関連付けられていないデバイスのコンプライアンス (および非コンプライアンス) を判断できます。

#### <a name="delete-autopilot-devices---1713650---"></a>Autopilot デバイスを削除する<!-- 1713650 -->
Intune 管理者は、[Autopilot デバイスを削除する](../enrollment/enrollment-autopilot.md#delete-autopilot-devices)ことができます。

#### <a name="improved-device-deletion-experience--1832333---"></a>デバイス削除エクスペリエンスの向上<!--1832333 -->
[Intune からデバイスを削除する](../remote-actions/devices-wipe.md#delete-devices-from-the-intune-portal)前に、会社のデータを削除したり、デバイスを工場出荷時の状態にリセットしたりする必要はなくなります。

新しいエクスペリエンスを表示するには、Intune にサインインし、 **[デバイス]**  >  **[すべてのデバイス]** > デバイスの名前 > **[削除]** の順に選びます。

ワイプ/使用停止の確認が必要な場合は、 **[削除]** の前に **[会社データを削除する]** と **[出荷時の設定にリセット]** を実行して、標準のデバイス ライフサイクル ルートを使うことができます。 

#### <a name="play-sounds-on-ios-when-in-lost-mode---1947769---"></a>紛失モードになったときに iOS で音を鳴らす<!-- 1947769 -->
監視対象の iOS デバイスがモバイル デバイス管理 (MDM) の[紛失モード](../remote-actions/device-lost-mode.md)になったときに、[音を鳴らす](../remote-actions/device-locate.md#activate-lost-mode-sound-alert-on-an-ios-device)ことができます ( **[デバイス]**  >  **[すべてのデバイス]** > iOS デバイスを選択 > **[概要]**  >  **[詳細]** )。 音は、デバイスが紛失モードではなくなるまで、またはユーザーがデバイスで音を無効にするまで、鳴り続けます。 iOS デバイス 9.3 以降に適用されます。

#### <a name="block-or-allow-web-results-in-searches-made-on-an-intune-device--1972804--"></a>Intune デバイスで行った Web 検索の結果のブロックまたは許可<!--1972804-->

管理者は、デバイスで行った Web 検索の結果をブロックできるようになりました。

#### <a name="improved-error-messaging-for-apple-mdm-push-certificate-upload-failure---2172331---"></a>Apple MDM プッシュ通知証明書のアップロード失敗のエラー メッセージの改善<!-- 2172331 -->

既存の MDM 証明書を更新するときは同じ Apple ID を使う必要があることが、エラー メッセージで説明されます。

#### <a name="test-the-company-portal-for-macos-on-virtual-machines---2216679---"></a>仮想マシンでの macOS 用ポータル サイトのテスト<!-- 2216679 -->

IT 管理者が Parallels Desktop と VMware Fusion の仮想マシンで macOS 用ポータル サイト アプリをテストする際に役立つガイダンスを公開しました。 詳しくは、「[テスト用に仮想 macOS マシンを登録する](../enrollment/macos-enroll.md#enroll-virtual-macos-machines-for-testing)」を参照してください。

### <a name="intune-apps"></a>Intune アプリ

#### <a name="user-experience-update-for-the-company-portal-app-for-ios--1412866---"></a>iOS 用ポータル サイト アプリに関するユーザー エクスペリエンスの更新プログラム<!--1412866 -->
iOS 用のポータル サイト アプリに対して、主要なユーザー エクスペリエンスの更新プログラムをリリースしました。 この更新プログラムでは、ビジュアル面の完全な再設計により、最新の外観に一新されています。 アプリの機能が更新されていますが、その使いやすさとアクセシビリティも向上しています。  

次の点も改善されています。
- iPhone X のサポート。
- アプリの起動時間と応答の読み込み時間の短縮。
- 最新の状態情報をユーザーに提供する追加の進行状況バー。
- ログのアップロード方法を改善。これにより、問題が生じた場合に、その内容を簡単にレポートできる。  

更新後の外観を確認するには、[アプリの UI の新機能](../whats-new-app-ui.md)に関するページを参照してください。

#### <a name="protect-on-premises-exchange-data-using-intune-app-and-ca---1056954---"></a>Intune APP および CA を使用したオンプレミス Exchange データの保護<!-- 1056954 -->
Intune アプリ ポリシー保護 (APP) および条件付きアクセス (CA) を使用して、Outlook Mobile によるオンプレミスの Exchange データへのアクセスを保護できるようになりました。 Azure portal 内でアプリ保護ポリシーを追加または変更するには、 **[Microsoft Intune]**  >  **[クライアント アプリ]**  >  **[アプリ保護ポリシー]** の順に選択します。 この機能を使用する前に、[iOS および Android 用 Outlook の要件](https://technet.microsoft.com/library/mt846639(v=exchg.160).aspx)を満たしていることを確認します。


### <a name="user-interface"></a>ユーザー インターフェイス

#### <a name="improved-device-tiles-in-the-windows-10-company-portal--2213364---"></a>Windows 10 ポータル サイトのデバイス タイルの改善<!--2213364 -->

視覚障碍のあるユーザーにより簡単にお使いいただけるように、また、画面読み取りツールのパフォーマンスを向上させるためにタイルが更新されました。

#### <a name="send-diagnostic-reports-in-company-portal-app-for-macos---2216677---"></a>macOS 用ポータル サイト アプリでの診断レポートの送信<!-- 2216677 -->
macOS デバイス用ポータル サイト アプリが更新され、ユーザーが Intune に関連するエラーを報告する方法が改善されました。 ポータル サイト アプリから、従業員は次の操作を行うことができます。

- Microsoft 開発者チームに直接診断レポートをアップロードする。
- 会社の IT サポート チームにインシデント ID をメールで送信する。

詳細については、[macOS のエラーの送信](/intune-user-help/send-errors-macos)に関するページを参照してください。

#### <a name="intune-adapts-to-fluent-design-system-in-the-company-portal-app-for-windows-10---1195010---"></a>Intune は、Windows 10 のポータル サイト アプリの Fluent Design System に適合します。<!-- 1195010 -->
Windows 10 の Intune ポータル サイト アプリは、[Fluent Design System のナビゲーション ビュー](https://docs.microsoft.com/windows/uwp/design/basics/navigation-basics)で更新済みです。 アプリの側面だけでなく、すべてのトップ レベルのページに静的な縦方向リストが表示されます。 リンクをクリックすると、ページをすばやく表示したり、ページを切り替えたりできます。 これは現在作成中の更新の一部であり、今後さらにアダプティブで馴染みがあり、使いやすい Intune の機能を提供していきます。 更新後の外観を確認するには、[アプリの UI の新機能](../whats-new-app-ui.md)に関するページを参照してください。

<!-- ########################## -->
## <a name="march-2018"></a>2018 年 3 月

### <a name="app-management"></a>アプリ管理

#### <a name="alerts-for-expiring-ios-line-of-business-lob-apps-for-microsoft-intune---748789---"></a>Microsoft Intune 用の iOS 基幹業務 (LOB) アプリの有効期限切れを示すアラート<!-- 748789 -->

Azure Portal の Intune では、有効期限が近づいている iOS 基幹業務アプリが警告されます。 iOS 基幹業務アプリの新しいバージョンをアップロードすると、有効期限に関する通知が Intune によってアプリ一覧から削除されます。 この有効期限に関する通知は、iOS 基幹業務アプリが新たにアップロードされた場合にのみアクティブになります。 警告が表示されるのは、iOS LOB アプリのプロビジョニング プロファイルの有効期限が切れる 30 日前となります。 有効期限が切れると、アラート表示が "期限切れ" 表示に変わります。

#### <a name="customize-your-company-portal-themes-with-hex-codes--1049561---"></a>Intune ポータル サイトのテーマを 16 進コードでカスタマイズする<!--1049561 -->

Intune ポータル サイト アプリのテーマの色を、16 進コードを使ってカスタマイズできます。 16 進コードを入力すると、Intune はテキストの色と背景の色の間のコントラストが最高レベルになるようにテキストの色を決定します。 **[クライアント アプリ]**  >  **[ポータル サイト]** で、テキストの色および色に対する会社のロゴの両方をプレビューできます。

### <a name="including-and-excluding-app-assignment-based-on-groups-for-android-enterprise---1813081---"></a>Android Enterprise に対するグループに基づくアプリ割り当ての追加と除外<!-- 1813081 -->

Android エンタープライズ (旧称 Android for Work) では、グループの追加と除外をサポートしていますが、事前に作成された**すべてのユーザー**と**すべてのデバイス**の組み込みグループはサポートしていません。 詳細については、「[Microsoft Intune でのアプリ割り当ての組み込みと除外](../apps/apps-inc-exl-assignments.md)」を参照してください。


### <a name="device-management"></a>デバイス管理

### <a name="export-all-devices-into-csv-files-in-ie-microsoft-edge-or-chrome---2258071---"></a>IE、Microsoft Edge、または Chrome ですべてのデバイスを CSV ファイルにエクスポートする<!-- 2258071 -->
**[デバイス]**  >  **[すべてのデバイス]** で、デバイスを CSV 形式の一覧に**エクスポート**することができます。 10,000 を超えるデバイスを持つ Internet Explorer (IE) ユーザーは、デバイスを複数のファイルに正常にエクスポートできます。 各ファイルには、最大 10,000 のデバイスが含まれます。

30,000 を超えるデバイスを持つ Microsoft Edge と Chrome ユーザーは、デバイスを複数のファイルに正常にエクスポートできます。 各ファイルには、最大 30,000 のデバイスが含まれます。

管理するデバイスに対して実行できる操作の詳細については、[デバイスの管理](../remote-actions/device-management.md)に関するページを参照してください。

#### <a name="new-security-enhancements-in-the-intune-service----1637539---"></a>Intune サービスでの新たなセキュリティ強化 <!-- 1637539 -->   

Azure 上の Intune にトグルが導入されました。このスイッチを利用することにより、Intune スタンドアロンのお客様は、ポリシーが割り当てられていないデバイスを **[準拠]** として処理 (セキュリティ機能オフ) することも、そのようなデバイスを **[非準拠]** として処理 (セキュリティ機能オン) することもできます。 これにより、デバイスのポリシー準拠が評価された後でのみ、リソースへのアクセスが保証されます。

この機能がユーザーに及ぼす影響は、コンプライアンス ポリシーが割り当て済みかどうかによって異なります。

- 新しいアカウントまたは既存のアカウントがあるが、コンプライアンス ポリシーをデバイスに割り当てていない場合、トグルは自動的に **[準拠]** に設定されます。 コンソールの既定の設定では、この機能はオフになっています。 エンドユーザーに与える影響はありません。
- 既存のアカウントがあり、デバイスにはコンプライアンス ポリシーが割り当てられている場合、トグルは自動的に **[非準拠]** に設定されます。 この機能は、3 月の更新のロールアウト時に、既定の設定としてオンになっています。

コンプライアンス ポリシーを条件付きアクセス (CA) と共に使用し、この機能がオンになっている場合、少なくとも 1 つのコンプライアンス ポリシーが割り当てられているデバイスは、CA によってブロックされるようになりました。 これらのデバイスに関連付けられていて、以前は電子メールへのアクセスを許可されていたエンド ユーザーは、少なくとも 1 つのコンプライアンス ポリシーをすべてのデバイスに割り当てない限り、アクセスできなくなります。   

Intune サービスの 3 月の更新プログラムにより、既定のトグル状態は UI にすぐに表示されるようになりましたが、このトグル状態はすぐに適用されないので注意してください。 トグルに変更を加えても、アカウントがフライトされて準備が整うまで、デバイスのポリシー準拠に影響はありません。 アカウントのフライトが完了したら、メッセージ センターを介してお知らせします。 これには、3 月の Intune サービスの更新が行われてから、数日かかる場合があります。

**追加情報**: [https://aka.ms/compliance_policies](https://aka.ms/compliance_policies)

#### <a name="enhanced-jailbreak-detection---846515---"></a>脱獄の検出の機能強化<!-- 846515 -->

強化された脱獄の検出の新しいコンプライアンス設定により、Intune による脱獄されたデバイスの評価方法が向上します。 この設定を使用すると、デバイスはこれまでより頻繁に Intune にチェックインされます。このときデバイスの場所サービスが使用されるため、バッテリの使用量に影響を与えます。

#### <a name="reset-passwords-for-android-o-devices---1238299---"></a>Android O デバイスのパスワードをリセットする<!-- 1238299 -->
作業プロファイルで、登録済みの Android 8.0 デバイスのパスワードをリセットできるようになります。 Android 8.0 デバイスに "パスワード リセット" 要求を送信すると、新しいデバイス ロック解除パスワードまたはマネージド プロファイルのチャレンジが、現在のユーザーに設定されます。 パスワードまたはチャレンジが送信され、すぐには有効になります。

#### <a name="targeting-compliance-policies-to-devices-in-device-groups--1307012---"></a>デバイス グループのデバイスへのコンプライアンス ポリシーのターゲット<!--1307012 -->

ユーザー グループ内のユーザーを、コンプライアンス ポリシーのターゲットにすることができます。 この更新プログラムを使用すると、デバイス グループ内のデバイスを、コンプライアンス ポリシーのターゲットにすることができます。 デバイス グループの一部としてターゲットにされたデバイスがコンプライアンス アクションを受け取ることはありません。

#### <a name="new-management-name-column---1333586---"></a>新しい [管理名] 列<!-- 1333586 -->
 **[管理名]** という名前の新しい列がデバイス ブレードで使用できます。 これは、次の式に基づいてデバイスごとに割り当てられる、自動生成された編集不可能な名前です。
- すべてのデバイスの既定の名前: <username><em><devicetype></em><enrollmenttimestamp>
- 一括追加デバイスの場合: <PackageId/ProfileId><em><DeviceType></em><EnrollmentTime>

これは、デバイス ブレードの省略可能な列です。 既定では使用できず、列セレクターを使用してのみアクセスできます。 この新しい列によるデバイス名への影響はありません。

#### <a name="ios-devices-are-prompted-for-a-pin-every-15-minutes--1550837---"></a>iOS デバイスで 15 分ごとに PIN の入力を求める<!--1550837 -->
iOS デバイスにコンプライアンスまたは構成ポリシーが適用されると、ユーザーは 15 分ごとに PIN を設定するように求められます。 PIN を設定するまで継続してユーザーは入力を求められます。

#### <a name="schedule-your-automatic-updates--1805514---"></a>自動更新スケジュールの設定<!--1805514 -->
Intune では、[Windows Update リングの設定](../protect/windows-update-for-business-configure.md)を使用して、自動更新のインストールを制御することができます。 この更新プログラムでは、週、日、時刻などを指定して、繰り返し更新が発生するようスケジュールすることができます。

#### <a name="use-fully-distinguished-name-as-subject-for-scep-certificate--2221763---"></a>SCEP 証明書のサブジェクトとして完全な識別名を使用する<!--2221763 -->
SCEP 証明書プロファイルを作成するときには、サブジェクト名を入力します。 この更新プログラムでは、サブジェクト名として、完全な識別名を使用できるようになります。 **サブジェクト名**に対して **[カスタム]** を選択し、`CN={{OnPrem_Distinguished_Name}}` と入力します。 `{{OnPrem_Distinguished_Name}}` 変数を使用するには、[Azure Active Directory (AD) Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) を使用して、`onpremisesdistingishedname` ユーザー属性を Azure AD と同期させます。

### <a name="device-configuration"></a>デバイスの構成

#### <a name="enable-bluetooth-contact-sharing---android-for-work--1098983---"></a>Bluetooth での連絡先の共有の有効化 - Android for Work<!--1098983 -->
Android の既定では、仕事用プロファイルの連絡先が Bluetooth デバイスと同期することはできません。 その結果、Bluetooth デバイスに対して、仕事用プロファイルの連絡先が発信者 ID に表示されません。

この更新プログラムでは、 **[Android for Work]**  >  **[デバイスの制限]**  >  **[仕事用プロファイルの設定]** に、次の新しい設定が表示されます。
- Bluetooth 経由での連絡先の共有

Intune の管理者は、これらの設定を構成して共有を有効にできます。 これは、デバイスを、ハンズフリー使用のために発信者 ID を表示する、車を拠点とする Bluetooth デバイスとペアリングする場合に便利です。 有効にすると、仕事用プロファイルの連絡先が表示されます。 無効にすると、仕事用プロファイルの連絡先は表示されません。

#### <a name="configure-gatekeeper-to-control-macos-app-download-source---1690459---"></a>macOS アプリ ダウンロード ソースを制御するための Gatekeeper の構成<!-- 1690459 -->

ダウンロードできるアプリの場所を制御することでアプリからデバイスを保護するように、Gatekeeper を構成することができます。 次のダウンロード ソースを構成することができます: **[Mac App Store]** 、 **[Mac App Store と識別された開発者]** 、または **[指定なし]** 。 また、ユーザーが Ctrl キーを押しながらクリックしてアプリをインストールすることによりこれらの Gatekeeper 制御をオーバーライドできるかどうかも構成できます。

これらの設定は、 **[デバイス構成]**  ->  **[プロファイルの作成]**  ->  **[macOS]**  ->  **[Endpoint Protection]** にあります。

#### <a name="configure-the-mac-application-firewall---1690461---"></a>Mac アプリケーションのファイアウォールの構成<!-- 1690461 -->

Mac アプリケーションのファイアウォールを構成できます。 これを使って、ポートごとではなく、アプリケーションごとに接続を制御できます。 これにより、ファイアウォールによる保護を簡単に利用できるようになり、正当なアプリ用に開かれているネットワーク ポートを望ましくないアプリが制御するのを防ぐのに役立ちます。

この設定は、 **[デバイス構成]**  ->  **[プロファイルの作成]**  ->  **[macOS]**  ->  **[Endpoint Protection]** にあります。

ファイアウォールの設定を有効にすると、2 つの戦略を使ってファイアウォールを構成できます。

- すべての着信接続をブロックする

   対象デバイスに対するすべての着信接続をブロックすることができます。 この方法を選択した場合、すべてのアプリの着信接続がブロックされます。

- 特定のアプリを許可またはブロックする

   特定のアプリからの着信接続の受信を許可またはブロックできます。 ステルス モードを有効にして、プローブ要求への応答を防ぐこともできます。

#### <a name="detailed-error-codes-and-messages---1376342---"></a>詳しいエラー コードとメッセージ<!-- 1376342 -->

デバイス構成で、より詳しいエラー コードとエラー メッセージを確認できます。 この改善された報告機能には、設定、設定の状態、トラブルシューティングの詳細が表示されます。

##### <a name="more-information"></a>説明

- すべての着信接続をブロックする

   すべての共有サービス (ファイル共有や画面共有など) が着信接続を受信するのをブロックします。 その場合でも、次のシステム サービスは着信接続を受信できます。
  - configd - DHCP および他のネットワーク構成サービスを実装します
  - mDNSResponder - Bonjour を実装します
  - racoon - IPSec を実装します

    共有サービスを使うには、 **[着信接続]** を ( **[ブロック]** ではなく) **[未構成]** に設定します。

- ステルス モード

   これを有効にすると、コンピューターはプローブ要求に応答しなくなります。 その場合でも、コンピューターは承認されたアプリの着信要求には応答します。 ICMP (ping) などの予期しない要求は無視されます。

#### <a name="disable-checks-on-device-restart--1805490---"></a>デバイス再起動時のチェックの無効化<!--1805490 -->
Intune によって[ソフトウェア更新プログラムの管理](../protect/windows-update-for-business-configure.md)を制御することができます。 この更新プログラムでは、<strong>[再起動チェック]</strong> プロパティが提供され、既定では有効になります。 デバイスを再起動する際に発生する一般的なチェック (アクティブなユーザー、バッテリのレベルなど) をスキップするには、<strong>[スキップ]</strong> を選択します。

#### <a name="new-windows-10-insider-preview-channels-available-for-deployment-rings---1746293---"></a>展開リングで利用できる新しい Windows 10 Insider Preview チャンネル<!-- 1746293 -->
Windows 10 展開リングを作成するときに、次の Windows 10 Insider Preview サービス チャンネルを選択するオプションが使用できるようになりました。
- Windows Insider ビルド - 高速
- Windows Insider ビルド - 低速
- Windows Insider ビルドのリリース 

これらのチャネルの詳細については、「[Insider Preview ビルドの管理](https://insider.windows.com/for-business-organization-admin/)」を参照してください。   
Intune での展開チャネルの作成の詳細については、「[ソフトウェア更新プログラムの管理](../protect/windows-update-for-business-configure.md)」を参照してください。

### <a name="new-windows-defender-exploit-guard-settings---1631893---"></a>Windows Defender Exploit Guard の新しい設定<!-- 1631893 -->

<strong>[攻撃の回避]</strong> の 6 つの新しい設定と、拡張された <strong>[フォルダー アクセスの制御: フォルダーの保護]</strong> 機能が利用できるようになりました。 これらの設定は、Device configuration\Profiles\ にあります。
[プロファイルの作成] > [Endpoint Protection] > [Windows Defender Exploit Guard] にあります。

#### <a name="attack-surface-reduction"></a>攻撃の回避

|設定の名前  |設定オプション  |[説明]  |
|---------|---------|---------|
|Advanced ransomware protection (高度なランサムウェア防止)|有効、監査、未構成|積極的なランサムウェア防止を使います。|
|Flag credential stealing from the Windows local security authority subsystem (Windows ローカル セキュリティ機関サブシステムからの資格情報の盗難にフラグを設定する)|有効、監査、未構成|Windows ローカル セキュリティ機関サブシステム (lsass.exe) からの資格情報の盗難にフラグを設定します。|
|Process creation from PSExec and WMI commands (PSExec および WMI コマンドからのプロセス作成)|ブロック、監査、未構成|PSExec および WMI コマンドから開始されるプロセス作成をブロックします。|
|Untrusted and unsigned processes that run from USB (USB から実行された信頼されていない署名なしのプロセス)|ブロック、監査、未構成|USB から実行された信頼されていない署名なしのプロセスをブロックします。|
|Executables that don’t meet a prevalence, age, or trusted list criteria (普及、経過時間、または信頼されたリストの条件を満たしていない実行可能ファイル)|ブロック、監査、未構成|普及、経過時間、または信頼されたリストの条件を満たしていない実行可能ファイルの実行をブロックします。|

#### <a name="controlled-folder-access"></a>フォルダー アクセスの制御

|              設定の名前               |                                                              設定オプション                                                              | [説明] |
|-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| フォルダーの保護 (実装済み) | 未構成、有効、監査のみ (実装済み)<br><br> <strong>新規</strong><br>Block disk modification (ディスクの変更をブロックする)、Audit disk modification (ディスクの変更を監査する) |             |

ファイルおよびフォルダーを、悪意のあるアプリによる未承認の変更から保護します。<br><br>**有効**: 信頼されていないアプリによって、保護されたフォルダー内のファイルの変更または削除、およびディスク セクターへの書き込みが行われないようにブロックします。<br><br>
**Block disk modification only (ディスクの変更のみをブロック)** :<br>信頼されていないアプリによるディスク セクターへの書き込みをブロックします。 信頼されていないアプリは、保護されたフォルダー内のファイルを変更または削除することはできます。

### <a name="intune-apps"></a>Intune アプリ

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview---710595---"></a>Azure Active Directory の Web サイトでは、Intune Managed Browser アプリを要求し、Managed Browser (パブリック プレビュー) に対するシングル サインオンをサポートすることができる<!-- 710595 -->

Azure Active Directory (Azure AD) を使用している場合、モバイル デバイスでの Web サイトへのアクセスを Intune Managed Browser アプリに制限できるようになりました。 Managed Browser では、Web サイトのデータは安全性が維持され、エンド ユーザーの個人データと分離されます。 さらに、Managed Browser は、Azure AD によって保護されているサイトに対するシングル サインオン機能をサポートします。 Managed Browser にサインインすると、または Intune によって管理されている別のアプリでデバイスの Managed Browser を使うと、ユーザーが資格情報を入力しなくても、Managed Browser は Azure AD によって保護されている会社サイトにアクセスできます。 この機能は、Outlook Web Access (OWA) や SharePoint Online などのサイトだけでなく、Azure App プロキシ経由でアクセスされるイントラネット リソースのような他の企業サイトにも適用されます。 詳細については、「[Azure Active Directory の条件付きアクセスのアクセス制御](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-controls)」を参照してください。

#### <a name="company-portal-app-for-android-visual-updates--976944---"></a>Android 用ポータル サイト アプリのビジュアルの更新<!--976944 -->

Android 用 Intune ポータル サイト アプリを、Android の[マテリアル デザイン](https://material.io/) ガイドラインに合わせて更新しています。 「[アプリ UI の新機能](../whats-new-app-ui.md)」の記事で、新しいアイコンの画像を確認することができます。

#### <a name="company-portal-enrollment-improved---1874230-eeready--"></a>ポータル サイトの登録の機能強化<!-- 1874230 eeready-->
Windows 10 ビルド 1703 以降の Intune ポータル サイトを使ってデバイスを登録するユーザーは、アプリを離れることなく登録の最初の手順を完了できるようになりました。
#### <a name="hololens-and-surface-hub-now-appear-in-device-lists--1725868---"></a>HoloLens と Surface Hub がデバイス リストに表示されるようになった<!--1725868 -->
Intune に登録された HoloLens および Surface Hub のデバイスを Android 用ポータル サイト アプリに表示するためのサポートが追加されました。

#### <a name="custom-book-categories-for-volume-purchase-program-vpp-ebooks---1488911---"></a>ボリューム購入プログラム (VPP) 電子ブックのカスタム ブック カテゴリ<!-- 1488911 -->
電子ブックのカスタム カテゴリを作成し、VPP の電子ブックをカスタム電子ブック カテゴリに割り当てることができます。 エンド ユーザーは、新しく作成された電子ブック カテゴリとそのカテゴリに割り当てられているブックを見ることができます。 詳細については、「[Microsoft Intune によるボリューム購入アプリとブックの管理](../apps/vpp-apps.md)」を参照してください。  

#### <a name="support-changes-for-company-portal-app-for-windows-send-feedback-option---2070166---"></a>Windows 用 Intune ポータル サイト アプリのフィードバック送信オプションのサポートの変更<!-- 2070166 -->
2018 年 4 月 30 日以降、Windows 用 Intune ポータル サイト アプリの **[フィードバックの送信]** オプションは、Windows 10 Anniversary Update (1607) 以降を実行するデバイスでのみ動作します。 次の Windows で Intune ポータル サイト アプリを使用している場合、フィードバック送信オプションはサポートされません。  
- Windows 10、1507 リリース  
- Windows 10、1511 リリース  
- Windows Phone 8.1 

お使いのデバイスが Windows 10 RS1 以降を実行している場合は、Store から最新バージョンの Windows 用 Intune ポータル サイト アプリをダウンロードしてください。 サポートされないバージョンを実行している場合は、引き続き次のチャネルでフィードバックを送信してください。 
- Windows 10 のフィードバック ハブ アプリ
- WinCPfeedback@microsoft.com へのメール  

#### <a name="new-windows-defender-application-guard-settings---1631890---"></a>Windows Defender Application Guard の新しい設定<!-- 1631890 -->

- **グラフィック アクセラレータを有効にする**: 管理者は、Windows Defender Application Guard の仮想グラフィック プロセッサを有効にすることができます。 この設定を使うと、CPU はグラフィックのレンダリングを vGPU にオフロードできます。 これにより、グラフィックが多用されている Web サイトを操作するとき、またはコンテナー内のビデオを見るときのパフォーマンスが向上します。

- **SaveFilestoHost**: 管理者は、コンテナーで実行されている Microsoft Edge からホスト ファイル システムへのファイルの受け渡しを有効にすることができます。 これをオンにすると、ユーザーはコンテナー内の Microsoft Edge からホスト ファイル システムにファイルをダウンロードできます。

#### <a name="mam-protection-policies-targeted-based-on-management-state---1665993---"></a>管理の状態に基づいて対象とされる MAM 保護ポリシー<!-- 1665993 -->
デバイスの管理状態に基づいて、MAM ポリシーを対象とすることができます。
- **Android デバイス** - アンマネージド デバイス、Intune で管理されたデバイス、Intune で管理された Android Enterprise Profiles (旧称 Android for Work) を対象にできます。
- **iOS デバイス** - アンマネージド デバイス (MAM のみ) または Intune で管理されたデバイスを対象にできます。

    > [!NOTE]
    > - この機能用の iOS サポートは、2018 年 4 月を通してロールアウトされます。

詳細については、[デバイス管理状態に基づくターゲット アプリ保護ポリシー](../apps/app-protection-policies.md)に関するページを参照してください。

#### <a name="improvements-to-the-language-in-the-company-portal-app-for-windows---1683758---"></a>Windows 用ポータル サイト アプリの言語を改善<!-- 1683758 -->
ユーザーにわかりやすく、組織に特有の言語となるように、Windows 10 用ポータル サイトの言語に改善を加えました。 改善された内容を示すサンプル画像を確認するには、[アプリ UI の新機能](../whats-new-app-ui.md)に関するページを参照してください。

#### <a name="new-additions-to-our-docs-about-user-privacy---1440709---"></a>ユーザー プライバシーに関する Microsoft ドキュメントへの新規追加<!-- 1440709 -->
エンドユーザーが自身のデータとプライバシーをより厳密に制御できるようにするための Microsoft の取り組みの一環として、ポータル サイト アプリによってローカルに格納されたデータの表示および削除方法を説明した Microsoft ドキュメントに対する更新内容を公開しました。 これらの更新内容は以下で確認できます。

- **Android**: [Intune からご利用の Android デバイスを削除する方法](/intune-user-help/unenroll-your-device-from-intune-android)
- **Android (ユーザーが利用規約を拒否した場合)** : ["利用規約" を拒否した場合にデバイス管理を削除します](/intune-user-help/unenroll-your-device-from-intune-if-you-declined-terms-of-use-android)
- **iOS**: [Intune から iOS デバイスを削除します](/intune-user-help/unenroll-your-device-from-intune-ios)
- **Windows**: [Intune からご利用の Windows デバイスを削除します](/intune-user-help/unenroll-your-device-from-intune-windows)

<!-- ########################## -->
## <a name="february-2018"></a>2018 年 2 月

### <a name="device-enrollment"></a>デバイスの登録

#### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts---747685---"></a>複数の Apple DEP および Apple School Manager アカウントに対する Intune サポート<!-- 747685 -->

最大 100 個の異なる [Apple Device Enrollment Program (DEP)](../enrollment/device-enrollment-program-enroll-ios.md) または [Apple School Manager](../enrollment/apple-school-manager-set-up-ios.md) アカウントからのデバイス登録が、Intune でサポートされます。 アップロードされる各トークンは、登録プロファイルとデバイスで、別々に管理できます。 アップロードされる DEP および School Manager のトークンごとに、異なる登録プロファイルを自動で割り当てることができます。 複数の School Manager トークンがアップロードされた場合、Microsoft 学校データ同期と共有できるのは、一度に 1 つのみです。

移行後、Graph で Apple DEP および ASM を管理するベータ版の Graph API と公開されたスクリプトは、動作しなくなります。 現在、新しいベータ版の Graph API の開発が進行中で、移行後にリリースされる予定です。

#### <a name="see-enrollment-restrictions-per-user---1634444-eeready-wnready---"></a>ユーザーごとに登録の制限を表示する<!-- 1634444 eeready wnready -->
**[トラブルシューティング]** ブレードの **[割り当て]** 一覧から **[登録制限]** を選択すると、各ユーザーに対して有効な[登録制限](../enrollment/enrollment-restrictions-set.md)を参照することができます。

#### <a name="new-option-for-user-authentication-for-apple-bulk-enrollment---747625-eeready---"></a>Apple の一括登録に対するユーザー認証の新しいオプション<!-- 747625 eeready -->

> [!NOTE]
> 新しいテナントでは、これは直ちに表示されます。 既存のテナントでは、この機能は 4 月にロールアウトされます。 このロールアウトが完了するまで、これらの新しい機能にアクセスできないことがあります。

Intune では現在、次の登録方法について、ポータル サイト アプリを使用してデバイスを認証できます。

- Apple Device Enrollment Program
- Apple School Manager
- Apple Configurator Enrollment

このポータル サイト オプションを使用すると、これらの登録方法をブロックすることなく、Azure Active Directory の多要素認証を強制できます。

このポータル サイト オプションを使用する場合、iOS 設定アシスタントでの、ユーザー アフィニティ登録用のユーザー認証がスキップされます。 つまり、このデバイスは、最初はユーザーのいないデバイスとして登録されるため、ユーザー グループの構成やポリシーは受信しません。 デバイス グループの構成とポリシーのみを受信します。 ただし、ポータル サイト アプリは自動的にデバイスにインストールされます。 ポータル サイト アプリを最初に起動してサインインするユーザーは、Intune でそのデバイスと関連付けられます。 この時点で、ユーザー グループの構成とポリシーが、このユーザーに送信されます。 ユーザーの関連付けを変更するには、再登録が必要です。

#### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts---747685-eeready---"></a>複数の Apple DEP および Apple School Manager アカウントに対する Intune サポート<!-- 747685 eeready -->

最大 100 個の異なる Apple Device Enrollment Program (DEP) または Apple School Manager アカウントからのデバイス登録が、Intune でサポートされます。 アップロードされる各トークンは、登録プロファイルとデバイスで、別々に管理できます。 アップロードされる DEP および School Manager のトークンごとに、異なる登録プロファイルを自動で割り当てることができます。 複数の School Manager トークンがアップロードされた場合、Microsoft 学校データ同期と共有できるのは、一度に 1 つのみです。

移行後、Graph で Apple DEP および ASM を管理するベータ版の Graph API と公開されたスクリプトは、動作しなくなります。 現在、新しいベータ版の Graph API の開発が進行中で、移行後にリリースされる予定です。

### <a name="remote-printing-over-a-secure-network---1709994----"></a>セキュリティで保護されたネットワークでのリモート印刷<!-- 1709994  -->
PrinterOn のワイヤレス モバイル印刷ソリューションは、時間や場所を問わない、セキュリティで保護されたネットワークでのリモート印刷を可能にします。 PrinterOn は、iOS 向けと Android 向けのどちらの Intune APP SDK とも統合します。 管理コンソールの Intune の **[アプリ保護ポリシー]** ブレードから、アプリ保護ポリシーのターゲットをこのアプリにすることもできます。 エンド ユーザーは、Play ストア、または iTunes から PrinterOn for Microsoft アプリをダウンロードして、Intune エコシステム内で使用できます。

### <a name="macos-company-portal-support-for-enrollments-that-use-the-device-enrollment-manager---1352411---"></a>デバイス登録マネージャーを使う登録の macOS ポータル サイトによるサポート<!-- 1352411 -->

ユーザーは、macOS ポータル サイトで登録するときに、デバイス登録マネージャーを使うことができるようになりました。

### <a name="device-management"></a>デバイス管理

#### <a name="windows-defender-health-status-and-threat-status-reports--854704---"></a>Windows Defender の正常性状態レポートと脅威状態レポート<!--854704 -->

Windows Defender の正常性と状態を理解することは、Windows PC の管理において重要なことです。  この更新では、Intune に、Windows Defender エージェントの状態と正常性の新しいレポートやアクションが追加されています。 [デバイスのポリシー準拠ワークロード](../protect/compliance-policy-monitor.md)の状態ロールアップ レポートを使用すると、次のことが必要なデバイスを確認できます。
- 署名の更新
- 再起動
- 手動介入
- フル スキャン
- 介入を必要とする他のエージェント状態

各状態カテゴリのドリルイン レポートでは、注意の必要な PC または**クリーン**と報告されている PC が個別に一覧表示されます。

#### <a name="new-privacy-settings-for-device-restrictions--1308926---"></a>デバイス制限のための新しいプライバシー設定<!--1308926 -->
[2 つの新しいプライバシー設定](../configuration/device-restrictions-windows-10.md#privacy)をデバイスで利用できるようになりました。
- **ユーザー アクティビティの公開**: これを **[ブロック]** に設定すると、タスク スイッチャーでの共有エクスペリエンスおよび最近使われたリソースの検出が行われなくなります。
- **ローカル アクティビティの場合のみ**: これを **[ブロック]** に設定すると、ローカル アクティビティのみに基づいて、タスク スイッチャーでの共有エクスペリエンスおよび最近使われたリソースの検出が行われなくなります。

#### <a name="new-settings-for-the-microsoft-edge-browser--1469166---"></a>Microsoft Edge ブラウザーの新しい設定<!--1469166 -->
Microsoft Edge ブラウザーを備えたデバイスで、次の [2 つの新しい設定](../configuration/device-restrictions-windows-10.md#microsoft-edge-browser)が利用できるようになりました: [**Path to favorites file]\(お気に入りファイルへのパス\)** と **[Changes to Favorites]\(お気に入りの変更\)** 。

### <a name="app-management"></a>アプリ管理

#### <a name="protocol-exceptions-for-applications--1035509---"></a>アプリケーションのプロトコル例外<!--1035509 -->

Intune モバイル アプリケーション管理 (MAM) データ転送ポリシーの例外を作成し、特定の管理されていないアプリケーションを開くことができまるようになりました。 このようなアプリケーションは、IT 担当者によって信頼されている必要があります。 データ転送ポリシーを**管理対象アプリのみ**に設定すると、作成した例外以外については、やはりデータ転送が Intune で管理されているアプリケーションだけに制限されます。 プロトコル (iOS) またはパッケージ (Android) を使って制限を作成することができます。

たとえば、MAM データ転送ポリシーに対する例外として、Webex パッケージを追加できます。 これにより、管理された Outlook メール メッセージ内の Webex リンクを、Webex アプリケーションで直接開くことができます。 他の管理されていないアプリケーションでは、データ転送が制限されます。 詳細については、「[Data transfer policy exceptions for apps](../apps/app-protection-policies-exception.md)」(アプリのデータ転送ポリシーの例外) を参照してください。

#### <a name="windows-information-protection-wip-encrypted-data-in-windows-search-results---1469193---"></a>Windows 検索結果の Windows 情報保護 (WIP) 暗号化データ<!-- 1469193 -->
Windows 情報保護 (WIP) ポリシーの設定により、WIP で暗号化されたデータを Windows の検索結果に含めるかどうかを制御できるようになりました。 このアプリ保護ポリシー オプションを設定するには、Windows 情報保護 (WIP) ポリシーの **[詳細設定]** で **[Allow Windows Search Indexer to search encrypted items]** \(暗号化されたアイテムの検索を Windows Search Indexer に許可する\) を選択します。 アプリの保護ポリシーは、 *[Windows 10]* プラットフォームに設定し、アプリ ポリシーの **[登録状態]** は **[With enrollment]** \(登録あり\) に設定する必要があります。 詳細については、「[Allow Windows Search Indexer to search encrypted items](../apps/windows-information-protection-policy-create.md#allow-windows-search-indexer-to-search-encrypted-items)」 (暗号化されたアイテムの検索を Windows Search Indexer に許可する) を参照してください。

#### <a name="configuring-a-self-updating-mobile-msi-app---1740840---"></a>自己更新モバイル MSI アプリの構成<!-- 1740840 -->
バージョン チェック プロセスを無視するように、既知の自己更新モバイル MSI アプリを構成することができます。 この機能は、競合状態になるのを防ぐのに役立ちます。 たとえば、この種類の競合状態は、アプリ開発者によって自動更新されているアプリが、Intune によっても更新されると、発生する可能性があります。 両方が Windows クライアント上のアプリのバージョンを強制しようとして、競合が発生することがあります。 これらの自動更新される MSI アプリには、 **[アプリ情報]** ブレードで **[Ignore app version]** \(アプリのバージョンを無視する\) を設定できます。 この設定を **[はい]** に切り替えると、Microsoft Intune で Windows クライアントにインストールされているアプリのバージョンは無視されます。

#### <a name="related-sets-of-app-licenses-supported-in-intune---1864117---"></a>Intune でサポートされるアプリ ライセンスの関連する設定<!-- 1864117 -->
Azure Portal 内の Intune で、UI の単一アプリ項目として、アプリ ライセンスの関連する設定がサポートされるようになりました。 さらに、ビジネス向け Microsoft Store から同期されるすべてのオフライン ライセンス アプリは単一のアプリ エントリに統合され、個別のパッケージからの展開の詳細は 1 つのエントリに移行されます。 Azure portal でアプリ ライセンスの関連するセットを表示するには、 **[クライアント アプリ]** ブレードから **[アプリ ライセンス]** を選択します。

### <a name="device-configuration"></a>デバイスの構成
#### <a name="windows-information-protection-wip-file-extensions-for-automatic-encryption---1463582---"></a>Windows 情報保護 (WIP) ファイルの自動暗号化用拡張子<!-- 1463582 -->
会社の境界内のサーバー メッセージ ブロック (SMB) 共有からコピーする場合、WIP ポリシーの定義に従って、自動的に暗号化するファイル拡張子を、Windows 情報保護 (WIP) ポリシーで指定できるようになりました。

#### <a name="configure-resource-account-settings-for-surface-hubs"></a>Surface Hub のリソース アカウント設定を構成する

Surface Hub のリソース アカウント設定をリモートで構成することができるようになりました。

このリソース アカウントは、Skype または Exchange でミーティングに参加できるように認証する場合に Surface Hub で使用されます。
Surface Hub がミーティングで会議室として表示されるように、一意のリソース アカウントを作成できます。
たとえば、**会議室 B41/6233** のようなリソース アカウントです。

> [!NOTE]
> - フィールドを空白のままにすると、デバイスで以前に構成された属性がオーバーライドされます。
>
> - リソース アカウントのプロパティは、Surface Hub で動的に変更できます。 たとえば、パスワードのローテーションが有効かどうか、などです。 そのため、Azure コンソールの値が、デバイス上の現実に反映されるまでに時間がかかることがあります。
>
>   Surface Hub での現在の構成を理解するには、リソース アカウント情報をハードウェア インベントリ (既に 7 日間隔になっています) または読み取り専用プロパティに含めることができます。 リモート操作が行われた後の精度を向上させるには、操作実行直後にパラメーターの状態を取得し、Surface Hub のアカウント/パラメーターを更新できます。

##### <a name="attack-surface-reduction"></a>攻撃の回避

|設定の名前  |設定オプション  |[説明]  |
|---------|---------|---------|
|電子メールのパスワードで保護されている実行可能ファイルのコンテンツの実行|ブロック、監査、未構成|メールからのパスワードで保護されている実行可能ファイルのダウンロードを防止します。|
|Advanced ransomware protection (高度なランサムウェア防止)|有効、監査、未構成|積極的なランサムウェア防止を使います。|
|Flag credential stealing from the Windows local security authority subsystem (Windows ローカル セキュリティ機関サブシステムからの資格情報の盗難にフラグを設定する)|有効、監査、未構成|Windows ローカル セキュリティ機関サブシステム (lsass.exe) からの資格情報の盗難にフラグを設定します。|
|Process creation from PSExec and WMI commands (PSExec および WMI コマンドからのプロセス作成)|ブロック、監査、未構成|PSExec および WMI コマンドから開始されるプロセス作成をブロックします。|
|Untrusted and unsigned processes that run from USB (USB から実行された信頼されていない署名なしのプロセス)|ブロック、監査、未構成|USB から実行された信頼されていない署名なしのプロセスをブロックします。|
|Executables that don’t meet a prevalence, age, or trusted list criteria (普及、経過時間、または信頼されたリストの条件を満たしていない実行可能ファイル)|ブロック、監査、未構成|普及、経過時間、または信頼されたリストの条件を満たしていない実行可能ファイルの実行をブロックします。|

##### <a name="controlled-folder-access"></a>フォルダー アクセスの制御

|              設定の名前               |                                                              設定オプション                                                              | [説明] |
|-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| フォルダーの保護 (実装済み) | 未構成、有効、監査のみ (実装済み)<br><br> <strong>新規</strong><br>Block disk modification (ディスクの変更をブロックする)、Audit disk modification (ディスクの変更を監査する) |             |

ファイルおよびフォルダーを、悪意のあるアプリによる未承認の変更から保護します。<br><br>**有効**: 信頼されていないアプリによって、保護されたフォルダー内のファイルの変更または削除、およびディスク セクターへの書き込みが行われないようにブロックします。<br><br>
**Block disk modification only (ディスクの変更のみをブロック)** :<br>信頼されていないアプリによるディスク セクターへの書き込みをブロックします。 信頼されていないアプリは、保護されたフォルダー内のファイルを変更または削除することはできます。

#### <a name="additions-to-system-security-settings-for-windows-10-and-later-compliance-policies--1704133--"></a>Windows 10 以降のコンプライアンス ポリシーのシステム セキュリティ設定への追加<!--1704133-->

ファイアウォールと Windows Defender ウイルス対策の要求など、Windows 10 のコンプライアンス設定への追加機能が使用可能になりました。

### <a name="intune-apps"></a>Intune アプリ

#### <a name="support-for-offline-apps-from-the-microsoft-store-for-business--1222672--"></a>ビジネス向け Microsoft ストアから入手したオフライン アプリのサポート<!--1222672-->
ビジネス向け Microsoft ストアから購入したオフライン アプリが Azure Portal と同期されまるようになりました。 その後、これらのアプリをデバイス グループまたはユーザー グループに展開できます。 オフライン アプリは、ストアからではなく Intune でインストールします。

#### <a name="prevent-end-users-from-manually-adding-or-removing-accounts-in-the-work-profile---1728700---"></a>エンド ユーザーが作業プロファイルのアカウントを手動で追加または削除できないようにする<!-- 1728700 -->

Gmail アプリを Android for Work プロファイルに展開するとき、Android for Work デバイス制限プロファイルで **[Add and remove accounts]\(アカウントを追加および削除する\)** 設定を使うことで、エンド ユーザーが作業プロファイルのアカウントを手動で追加または削除できないようにすることができるようになりました。

<!-- ########################## -->
## <a name="january-2018"></a>2018 年 1 月

### <a name="device-enrollment"></a>デバイスの登録

#### <a name="alerts-for-expired-tokens-and-tokens-that-will-soon-expire---1639263---"></a>期限切れトークンと有効期限が近いトークンのアラート<!-- 1639263 -->
有効期限が切れているトークンと、有効期限が近づいているトークンのアラートが概要ページに表示されるようになりました。 1 つのトークンのアラートをクリックすると、そのトークンの詳細ページに移動します。  複数のトークンのアラートをクリックすると、トークンのステータスが表示された全トークンの一覧に移動します。 管理者は、有効期限が来る前にトークンを更新する必要があります。

### <a name="device-management"></a>デバイス管理

#### <a name="remote-erase-command-support-for-macos-devices---1438084---"></a>macOS デバイスのリモートの "消去" コマンド サポート<!-- 1438084 -->

管理者は、macOS デバイスの消去コマンドをリモートで発行できます。

> [!IMPORTANT]
> 消去コマンドは、元に戻すことができないため、使用する際は注意が必要です。

消去コマンドでは、オペレーティング システムを含むすべてのデータが、デバイスから削除されます。 また、そのデバイスも、Intune 管理から削除されます。 ユーザーに対して警告は表示されません。また、コマンドを発行すると、消去は即座に実行されます。

6 桁の回復用 PIN を構成する必要があります。 この PIN を使用すると、消去されたデバイスのロックが解除され、オペレーティング システムの再インストールが開始されます。 PIN は、消去が開始されると、Intune のデバイスの概要ブレードのステータス バーに表示されます。 消去が完了するまでの間、PIN はずっと表示されます。 消去が完了したら、デバイスは Intune 管理から完全に削除されます。 デバイスを復元する人が誰であっても、そのデバイスを使用できるように、回復用 PIN は必ず記録するようにしてください。

#### <a name="revoke-licenses-for-an-ios-volume-purchasing-program-token---820870---"></a>iOS Volume Purchasing Program トークンのライセンスの取り消し<!-- 820870 -->
特定の VPP トークンのすべての iOS Volume Purchasing Program (VPP) アプリのライセンスを取り消すことができます。

### <a name="app-management"></a>アプリ管理

#### <a name="revoking-ios-volume-purchase-program-apps----820863---"></a>iOS Volume-Purchase Program アプリの取り消し <!-- 820863 -->
1 つ以上の iOS Volume-Purchase Program (VPP) アプリがインストールされた特定のデバイスでは、そのデバイスで関連付けられているデバイス ベース アプリのライセンスを取り消すことができます。 アプリのライセンスを取り消しても、関連する VPP アプリがデバイスからアンインストールされるわけではありません。 VPP アプリをアンインストールするには、割り当てアクションを **[アンインストール]** に変更する必要があります。 詳細については、「[Volume Purchase Program で購入した iOS アプリを Microsoft Intune で管理する方法](../apps/vpp-apps-ios.md)」をご覧ください。

#### <a name="assign-office-365-mobile-apps-to-ios-and-android-devices-using-built-in-app-type---1332318---"></a>組み込み型のアプリを利用し、iOS デバイスまたは Android デバイスに Office 365 モバイル アプリを割り当てる<!-- 1332318 -->
**組み込み**型のアプリであれば、Office 365 アプリを作成し、管理している iOS または Android デバイスに割り当てることが簡単にできます。 これらのアプリには、Word、Excel、PowerPoint、OneDrive などの 0365 アプリがあります。 アプリの種類に特定のアプリを割り当て、アプリ情報構成を編集できます。

#### <a name="including-and-excluding-app-assignment-based-on-groups---1406920---"></a>グループに基づくアプリ割り当ての追加と除外<!-- 1406920 -->

アプリの割り当て時、および割り当ての種類の選択後に、含めるグループと、除外するグループを選択できます。

### <a name="device-configuration"></a>デバイスの構成

#### <a name="you-can-assign-an-application-configuration-policy-to-groups-by-including-and-excluding-assignments----1480316---"></a>割り当てを含めたり除外したりしてグループにアプリケーション構成ポリシーを割り当てることができる <!-- 1480316 -->

含める割り当てと除外する割り当ての組み合わせを使って、ユーザーとデバイスのグループにアプリケーション構成ポリシーを割り当てることができます。 割り当ては、グループのカスタム選択または仮想グループとして選べます。 仮想グループは、**すべてのユーザー**、**すべてのデバイス**、または**すべてのユーザーとすべてのデバイス**を含むことができます。

#### <a name="support-for-windows-10-edition-upgrade-policy-----903672archived-1119689---"></a>Windows 10 エディション アップグレード ポリシーのサポート  <!-- 903672(archived), 1119689 -->  
Windows 10 デバイスを Windows 10 Education、Windows 10 Education N、Windows 10 Professional、Windows 10 Professional N、Windows 10 Professional Education、Windows 10 Professional Education N にアップグレードする Windows 10 エディション アップグレード ポリシーを作成できます。Windows 10 エディションのアップグレードについては、「[Windows 10 エディションのアップグレードを構成する方法](../configuration/edition-upgrade-configure-windows-10.md)」をご覧ください。

#### <a name="conditional-access-policies-for-intune-is-only-available-from-the-azure-portal----1737088-1634311---"></a>Intune の条件付きアクセス ポリシーの利用可能場所が Azure Portal のみに <!-- 1737088 1634311 -->

このリリース以降は、 **[Azure Active Directory]**  >  **[条件付きアクセス]** から [Azure Portal](https://portal.azure.com) の条件付きアクセス ポリシーを構成して管理する必要があります。 便宜上、 **[Intune]**  >  **[条件付きアクセス]** の、Azure Portal 内にある Intune からこのブレードにアクセスすることもできます。

#### <a name="updates-to-compliance-emails--1637547---"></a>コンプライアンスのメールに対する変更<!--1637547 -->

コンプライアンス違反のデバイスを報告するメールが送信される際に、そのコンプライアンス違反のデバイスの詳細が含まれます。

### <a name="intune-apps"></a>Intune アプリ

#### <a name="new-functionality-for-the-resolve-action-for-android-devices--1583480--"></a>Android デバイスの "解決" アクションの新機能<!--1583480-->

Android 用ポータル サイト アプリは、[デバイス暗号化の問題](/intune-user-help/encrypt-your-device-android)を解決するために、 **[デバイス設定の更新]** の "解決" アクションを拡張しています。

#### <a name="remote-lock-available-in-company-portal-app-for-windows-10--676506--"></a>Windows 10 用の Intune ポータル サイトで利用できるリモート ロック<!--676506-->
エンドユーザーは、Windows 10 向けポータル サイト アプリから自分のデバイスをリモートでロックできるようになりました。 この機能はエンド ユーザーがアクティブに使用しているローカル デバイスには表示されません。

#### <a name="easier-resolution-of-compliance-issues-for-the-company-portal-app-for-windows-10--676546--"></a>Windows 10 でポータル サイト アプリのコンプライアンスの問題解決が簡単に<!--676546-->
Windows デバイスを持つエンド ユーザーは、ポータル サイト アプリのコンプライアンス非対応の理由をタップできます。 可能な場合には、問題を解決するために設定アプリの適切な場所に直接移動します。

<!-- ########################## -->
## <a name="december-2017"></a>2017 年 12 月

### <a name="device-configuration"></a>デバイスの構成

#### <a name="new-automatic-redeployment-setting---1469168---"></a>新しい自動再配置設定<!-- 1469168 -->
**自動再展開**設定では、管理権限を持つユーザーが、デバイス ロック画面で **CTRL + Win + R** を使用してすべてのユーザー データとユーザー設定を削除できます。 このデバイスは自動的に再構成され、管理対象に再登録されます。 この設定には、[Windows 10] -> [デバイスの制限] -> [全般] -> [自動再展開] でアクセスできます。 詳細については、[Intune での Windows 10 のデバイス制限設定](../configuration/device-restrictions-windows-10.md#general)に関するページをご覧ください。

#### <a name="support-for-additional-source-editions-in-the-windows-10-edition-upgrade-policy----903672--1119689---"></a>Windows 10 エディションのアップグレード ポリシーにおける、その他のソース エディションのサポート <!-- 903672,  1119689 -->
Windows 10 エディションのアップグレード ポリシーを使用して、Windows 10 の他のエディション (Windows 10 Pro、Windows 10 Pro Education、Windows 10 Cloud など) からアップグレードできるようになりました。 以前のリリースでは、サポートされるエディションのアップグレードのパスは、今よりも限定されていました。 詳細については、[Windows 10 エディションのアップグレードを構成する方法](../configuration/edition-upgrade-configure-windows-10.md)に関するページをご覧ください。

#### <a name="new-windows-defender-security-center-wdsc-device-configuration-profile-settings---1335507---"></a>新しい Windows Defender セキュリティ センター (WDSC) デバイス構成プロファイルの設定<!-- 1335507 -->

Intune の **Windows Defender セキュリティ センター**という名前の Endpoint Protection に、デバイス構成プロファイル設定の新しいセクションが追加されます。 IT 管理者は、Windows Defender セキュリティ センター アプリで、エンドユーザーがどの機能にアクセス可能かを構成できます。 IT 管理者が Windows Defender セキュリティ センター アプリで、ある機能を非表示にすると、ユーザーのデバイスで、その機能に関連するすべての通知が非表示になります。

管理者が Windows Defender セキュリティ センター デバイス構成プロファイル設定で非表示にできる機能は、以下のとおりです。
- ウイルスと脅威の防止
- デバイスのパフォーマンスと正常性
- ファイアウォールとネットワーク保護
- アプリとブラウザー コントロール
- ファミリー オプション

IT 管理者は、ユーザーが受け取る通知をカスタマイズすることもできます。 たとえば、ユーザーが WDSC に表示される機能で生成されたすべての通知を受け取るか、または重要な通知のみを受け取るかを構成できます。 重要度の低い通知には、Windows Defender Antivirus のアクティビティに関する定期的な概要や、スキャン完了時の通知があります。 その他のすべての通知は重要とみなされます。 さらに、通知の内容自体をカスタマイズすることもできます。たとえば、IT 担当の連絡先情報を、ユーザーのデバイスに表示される通知に組み込むなどです。

#### <a name="multiple-connector-support-for-scep-and-pfx-certificate-handling---1361755---"></a>SCEP の複数コネクタ サポートと PFX 証明書処理<!-- 1361755 -->

オンプレミス NDES コネクタを使用してデバイスに証明書を配信するお客様は、1 つのテナントに複数のコネクタを構成できるようになりました。

この新しい機能では、次のシナリオがサポートされています。

- **高可用性**

各 NDES コネクタは、Intune から証明書の要求を取得します。  1 つの NDES コネクタがオフラインになっても、その他のコネクタは要求の処理を続行できます。

#### <a name="customer-subject-name-can-use-aad_device_id-variable----1468599---"></a>カスタム サブジェクト名で AAD_DEVICE_ID 変数が使用可能に <!-- 1468599 -->

Intune で SCEP 証明書プロファイルを作成する際、カスタム サブジェクト名の作成時に AAD_DEVICE_ID 変数を使用できるようになりました。   この SCEP プロファイルを使用して証明書が要求されると、証明書の要求を行っているデバイスの AAD デバイス ID が、この変数に置き換わります。


### <a name="device-management"></a>デバイス管理

#### <a name="manage-jamf-enrolled-macos-devices-with-intunes-device-compliance-engine---1592747---"></a>Intune のデバイス コンプライアンス エンジンを使用した Jamf に登録された macOS デバイスの管理<!-- 1592747 -->
Jamf を使って、macOS デバイスの状態情報を Intune に送信できるようになりました。情報はその後、Intune コンソールで定義されたポリシーに準拠しているかどうかが評価されます。 条件付きアクセスでは、デバイスのコンプライアンス対応状態や、その他の条件 (場所やユーザー リスクなど) に基づいて、Azure AD に接続されたクラウド アプリケーションやオンプレミス アプリケーション (Office 365 など) にアクセスする macOS デバイスにコンプライアンスを適用します。 [Jamf 統合の設定](../protect/conditional-access-integrate-jamf.md)と [Jamf で管理されたデバイスのコンプライアンスの強制](../protect/conditional-access-assign-jamf.md)について、詳細をご覧ください。

#### <a name="new-ios-device-action-----1424701---"></a>新しい iOS デバイス アクション  <!-- 1424701 -->

iOS 10.3 監視下のデバイスをシャット ダウンできるようになりました。 このアクションでは、エンド ユーザーへの警告なしにデバイスが即時シャットダウンされます。 **シャット ダウン (監視モードのみ)** アクションは、**デバイス** ワークロードでデバイスを選択した場合に、デバイス プロパティに表示されます。

#### <a name="disallow-datetime-changes-to-samsung-knox-devices---1468103---"></a>Samsung KNOX デバイスへの日付および時刻の変更禁止<!-- 1468103 -->

Samsung KNOX デバイスでの日付と時刻の変更をブロックできる機能が新たに追加されました。 この機能は、 **[デバイス構成プロファイル]**  >  **[デバイスの制限 (Android)]**  >  **[全般]** にあります。

#### <a name="surface-hub-resource-account-supported---1566442----"></a>サポートされる Surface Hub リソース アカウント<!-- 1566442  -->

Surface Hub に関連付けられたリソース アカウントを、管理者が定義、更新できる新しいデバイス アクションが追加されました。

このリソース アカウントは、Skype または Exchange でミーティングに参加できるように認証する場合に Surface Hub で使用されます。 Surface Hub がミーティングで会議室として表示されるように、一意のリソース アカウントを作成できます。 たとえば、リソース アカウントは*会議室 B41/6233* と表示されます。 Surface Hub のリソース アカウント (デバイス アカウントと呼ばれる) は通常、会議室の場所や、他のリソース アカウントのパラメーターをいつ変更するかを構成するのに必要となります。

管理者はデバイスでリソース アカウントを更新する場合、デバイスに関連付けられた現在の Active Directory または Azure Active Directory 資格情報を指定する必要があります。 デバイスでパスワードのローテーションがオンに設定されている場合には、管理者は Azure Active Directory に移動してパスワードを検索する必要があります。

> [!NOTE]
> すべてのフィールドがまとめて送信され、以前に構成されたすべてのフィールドを上書きします。 また、空のフィールドも既存のフィールドを上書きします。

管理者が行える構成は次のとおりです。

- **リソース アカウント**
  - **Active Directory ユーザー**

    Domainname\username、またはユーザー プリンシパル名: user@domainname.com

  - **パスワード**

- **オプションのリソース アカウント パラメーター** (指定されたリソース アカウントを使用して設定する必要があります)

  - **パスワードのローテーション期間**

    アカウントのパスワードは、セキュリティ上の理由から、毎週 Surface Hub によって自動的に更新されます。 これを有効にした後にパラメーターを構成するには、最初に Azure Active Directory のアカウントのパスワードをリセットする必要があります。

  - **SIP (セッション開始プロトコル) アドレス**

    自動検出が失敗した場合にのみ使用されます。

  - **電子メール**

    デバイス アカウントまたはリソース アカウントの電子メール アドレス。

  - **Exchange サーバー**

    自動検出が失敗した場合のみ必要です。

  - **予定表の同期**

    予定表の同期と他の Exchange サーバー サービスが有効かどうかを指定します。 たとえば、ミーティングの同期などです。

#### <a name="install-office-apps-on-macos-devices---1494311---"></a>macOS デバイスでの Office アプリのインストール<!-- 1494311 -->
macOS デバイスで Office アプリをインストールできるようになりました。 この新しい種類のアプリでは、Word、Excel、PowerPoint、Outlook、OneNote をインストールできます。 これらのアプリには Microsoft AutoUpdate (MAU) も付属しており、アプリを安全かつ最新に保つことができます。

### <a name="app-management"></a>アプリ管理

#### <a name="delete-an-ios--volume-purchasing-program-token---820879---"></a>iOS Volume Purchasing Program トークンのライセンスの削除<!-- 820879 -->
コンソールを使用して、iOS Volume Purchasing Program (VPP) トークンを削除できます。 VPP トークンのインスタンスが重複している場合に、これが必要になることがあります。

### <a name="intune-apps"></a>Intune アプリ


### <a name="role-based-access-control"></a>ロール ベースのアクセス制御

#### <a name="a-new-entity-collection-named-current-user-is-limited-to-currently-active-user-data---1667026---"></a>現在のユーザーという名前の新しいエンティティ コレクションは、現在アクティブなユーザー データに限られています<!-- 1667026 -->

**ユーザー** エンティティ コレクションには、社内のすべての Azure Active Directory (Azure AD) ユーザーと割り当てられているライセンスが表示されます。 たとえば、ユーザーが Intune に追加され、過去 1 か月の過程で削除されたとします。 このユーザーがレポートの時点では存在しない一方で、ユーザーと状態はデータに存在します。 データ内のユーザーの履歴における存在の期間を示すレポートを作成できます。

これに対し、新しい**現在のユーザー** エンティティ コレクションには、削除されていないユーザーのみが含まれています。 **現在のユーザー** エンティティ コレクションには、現在アクティブなユーザーのみが含まれています。 **現在のユーザー** エンティティ コレクションの詳細については、「[現在のユーザー エンティティのリファレンス](../developer/reports-ref-data-model.md)」をご覧ください。

### <a name="updated-graph-apis---1736360---"></a>Graph API の変更<!-- 1736360 -->

このリリースでは、Intune のベータ版の Graph API にいくつか変更を加えました。 詳細については、[Graph API の変更ログ](https://developer.microsoft.com/graph/docs/concepts/changelog)のページ (毎月更新) をご覧ください。

### <a name="monitor-and-troubleshoot"></a>監視とトラブルシューティング

#### <a name="intune-supports-windows-information-protection-wip-denied-apps---1479103---"></a>Intune では Windows Information Protection (WIP) で拒否されたアプリがサポートされる<!-- 1479103 -->
拒否されたアプリを Intune で指定することができます。 アプリが拒否された場合、企業の情報へのアクセスがブロックされます。これは事実上、許可されたアプリ リストの反対です。 詳しくは、[Windows 情報保護の推奨される拒否リスト](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp?f=255&MSPPError=-2147217396#recommended-deny-list-for-windows-information-protection)を参照してください。

<!-- ########################## -->
## <a name="november-2017"></a>2017 年 11 月

### <a name="troubleshoot-enrollment-issues----746324---"></a>登録に関する問題をトラブルシューティングする <!-- 746324 -->

**トラブルシューティング** ワークスペースに、ユーザーの登録に関する問題が表示されるようになりました。 問題に関する詳細と推奨される修復手順は、管理者およびヘルプ デスクのオペレーターが問題をトラブルシューティングするのに役立ちます。 登録に関する特定の問題はキャプチャされず、一部のエラーには推奨される修復方法がない場合があります。

### <a name="group-assigned-enrollment-restrictions---747598---"></a>グループ割り当て登録制限<!-- 747598 -->

Intune 管理者は[ユーザー グループに対してカスタムの登録制限として [デバイスの種類] と [デバイスの上限数] を作成できるようになりました](../enrollment/enrollment-restrictions-set.md)。

Intune Azure ポータルで、制限タイプごとに最大 25 個のインスタンスを作成できます。作成したインスタンスはユーザー グループに割り当てることができます。 グループに割り当てられた制限は既定の制限をオーバーライドします。

制限タイプのすべてのインスタンスは、厳密に順序付けられた一覧で保守管理されます。 この順序により、競合解決の優先度の値が決まります。 複数の制限インスタンスの影響を受けるユーザーは、優先度の値が最も高いインスタンスによって制限されます。 インスタンスの優先度は、一覧内の別の位置にドラッグすることによって変更できます。

Android For Work 登録メニューから登録制限メニューに Android For Work 設定が移行されたとき、この機能が使えるようになります。 この移行には数日かかる場合があります。11 月リリースのその他の部分に関してアカウントがアップグレードされた後に、登録制限のグループ割り当てが有効になる場合があります。

### <a name="support-for-multiple-network-device-enrollment-service-ndes-connectors---1528104---"></a>複数のネットワーク デバイス登録サービス (NDES) コネクタのサポート<!-- 1528104 -->

NDES を利用すれば、ドメイン資格情報なしでモバイル デバイスを実行し、Simple Certificate Enrollment Protocol (SCEP) に基づいて証明書を取得できます。
今回の更新で、複数の NDES コネクタがサポートされるようになりました。

### <a name="manage-android-for-work-devices-independently-from-android-devices---1490731-eeready--"></a>Android デバイスとは別に Android for Work デバイスを管理する<!-- 1490731 EEready-->

Intune は、Android プラットフォームに依存することなく、Android for Work デバイスの登録を管理します。 この設定は、 **[デバイスの登録]** 、 >  **[登録制限]** 、 >  **[デバイスの種類の制限]** で管理されます。 (以前の場所は **[デバイス登録]** 、 >  **[Android for Work への登録]** 、 >  **[Android for Work の登録設定]** でした。)

既定では、Android for Work デバイス設定は Android デバイスの設定と同じになります。 ただし、Android for Work 設定を変更した後は、同じではなくなります。

個人の Android for Work 登録をブロックした場合、会社の Android デバイスのみを Android for Work として登録できます。

新しい設定を使用する場合、次の点を考慮してください。

#### <a name="if-you-have-never-previously-onboarded-android-for-work-enrollment"></a>以前に Android for Work 登録をオンボードしたことがない

新しい Android for Work プラットフォームは、既定の [デバイスの種類の制限] でブロックされます。 この機能をオンボードした後は、デバイスを Android for Work に登録できます。 そのためには、既定値を変更するか、新しい [デバイスの種類の制限] を作成して既定の [デバイスの種類の制限] に代えます。

#### <a name="if-you-have-onboarded-android-for-work-enrollment"></a>Android for Work 登録をオンボードした

以前にオンボードしている場合、状況は選んだ設定によって変わります。

| 設定 | 既定の [デバイスの種類の制限] の Android for Work の状態 | 注 |
| --- | --- | --- |
| **すべてのデバイスを Android として管理する** | ［ブロック済み］ | すべての Android デバイスを Android for Work なしで登録する必要があります。 |
| **サポートされているデバイスを Android for Work として管理する** | 許可されます。 | Android for Work 対応のすべての Android デバイスを Android for Work に登録する必要があります。 |
| **これらのグループに所属するユーザーのサポートされているデバイスのみを Android for Work として管理する** | ［ブロック済み］ | 既定値をオーバーライドする別個の [デバイスの種類の制限] ポリシーが作成されました。 このポリシーによって、以前に選択したグループで Android for Work 登録が許可されます。 選択されたグループ内のユーザーには、Android for Work デバイスの登録が引き続き許可されます。 その他すべてのユーザーには、Android for Work の登録が禁止されます。 |

いずれの場合でも、意図した規制が維持されます。 自分の環境で Android for Work のグローバル許可またはグループ別許可を維持するための操作は必要ありません。

### <a name="google-play-protect-support-on-android---908720---"></a>Android の Google Play Protect サポート<!-- 908720 -->

Android Oreo のリリースに伴い、セキュリティで保護されたアプリおよび Android イメージをユーザーや組織が実行できる、Google Play Protect という一連のセキュリティ機能が Google より提供されました。 Intune では、SafetyNet リモート構成証明をはじめとした Google Play Protect の各機能をサポートするようになりました。 管理者は、Google Play Protect が構成され正常な状態であることが求められるコンプライアンス ポリシー要件を設定できます。
**[SafetyNet デバイスの構成証明]** 設定では、デバイスが正常な状態であり危険にさらされていないことを確認するために、デバイスを Google サービスに接続する必要があります。 管理者は、インストール済みのアプリが Google Play 開発者サービスによって検証されることを必須にする、Android for Work の構成プロファイル設定を設定することもできます。 デバイスが Google Play Protect の要件に準拠していない場合、条件付きアクセスでは、ユーザーが企業リソースにアクセスできなくなる可能性があります。

- 「[デバイスのコンプライアンス ポリシーを作成して Google Play Protect を有効にする方法](../protect/compliance-policy-create-android.md)」を参照してください。

### <a name="text-protocol-allowed-from-managed-apps---1414050----"></a>管理対象アプリから許可されるテキスト プロトコル<!-- 1414050  -->

Intune App SDK によって管理されているアプリは、SMS メッセージを送信できます。


### <a name="app-install-report-updated-to-include-install-pending-status---1249446---"></a>インストール保留中の状態を含むように更新されたアプリ インストール レポート<!-- 1249446 -->  

**[クライアント アプリ]** ワークロードの **[アプリ]** 一覧から表示できるアプリ別の **[アプリ インストールの状態]** レポートでは、ユーザーとデバイスについて **[インストール保留中]** カウントが表示されるようになりました。

### <a name="ios-11-app-inventory-api-for-mobile-threat-detection---1391759---"></a>モバイルの脅威を検出するための iOS 11 アプリ インベントリ API<!-- 1391759 -->

Intune は個人のデバイスと会社所有のデバイスの両方からアプリ インベントリ情報を収集し、Lookout for Work など、MTD (Mobile Threat Detection/モバイル脅威検出) プロバイダーが取得できるようにします。 iOS 11 以降のデバイスを所有するユーザーからアプリ インベントリを収集できます。

**アプリ インベントリ**  
iOS 11 以降を内蔵した会社所有デバイスと個人所有デバイスの両方からのインベントリが MTD サービス プロバイダーに送信されます。 アプリ インベントリのデータ:

- アプリ ID
- アプリ バージョン
- アプリ バージョン (短い形式)
- アプリ名
- アプリ バンドル サイズ
- アプリの動的サイズ
- アプリの有効性が確認されているかどうか
- アプリが管理されているかどうか

### <a name="migrate-hybrid-mdm-users-and-devices-to-intune-standalone---1463747-wnready---"></a>ハイブリッド MDM のユーザーとデバイスを Intune スタンドアロンに移行する<!-- 1463747 wnready -->
ハイブリッド MDM から Azure Portal 内の Intune にユーザーとそのデバイスを移動するための新しいプロセスとツールが利用可能になりました。これにより、次の操作を行うことができます。
- Configuration Manager コンソールから Azure Portal 内の Intune にポリシーとプロファイルをコピーする
- ユーザーのサブセットを Azure Portal 内の Intune に移動し、残りのユーザーをハイブリッド MDM で保持したままにする
- 再登録せずに、Azure Portal 内の Intune にデバイスを移行する

### <a name="on-premises-exchange-connector-high-availability-support----676614---"></a>オンプレミスの Exchange Connector の高可用性のサポート <!-- 676614 -->
Exchange Connector によって、指定のクライアント アクセス サーバー (CAS) で Exchange への接続が作成された後、コネクタで別の CAS も検出できるようになりました。 メインの CAS が利用できなくなった場合、再度利用可能になるまで、コネクタが別の CAS (ある場合) にフェールオーバーします。 詳細については、「[オンプレミスの Exchange Connector の高可用性のサポート](../protect/exchange-connector-install.md#on-premises-intune-exchange-connector-high-availability-support)」をご覧ください。

### <a name="remotely-restart-ios-device-supervised-only---1424595---"></a>iOS デバイスをリモート再起動する (監視モードのみ)<!-- 1424595 -->

デバイス アクションを利用し、監視されている iOS 10.3 以降のデバイスの再起動をトリガーできるようになりました。 デバイス再起動アクションの利用方法については、「[Intune でデバイスをリモートで再起動する](../remote-actions/device-restart.md)」を参照してください。

> [!Note]
> このコマンドは、監視されているデバイスと**デバイス ロック** アクセス権を要求します。 デバイスがすぐに再起動します。 パスコードでロックされている iOS デバイスが再起動後に Wi-Fi ネットワークに再び参加することはありません。再起動後、サーバーと通信できないことがあります。

### <a name="single-sign-on-support-for-ios---1333645---"></a>iOS のシングル サインオン サポート<!-- 1333645 -->  

iOS ユーザーのためにシングル サインオンを使用できます。 シングル サインオン ペイロードのユーザー資格情報を探すようにプログラミングされている iOS アプリは、このペイロード構成更新で機能します。 UPN と Intune デバイス ID を利用し、プリンシパル名と領域を構成することもできます。 詳しくは、「[Configure Intune for iOS device single sign-on](../configuration/ios-device-features-settings.md#single-sign-on)」 (iOS 用 Intune のデバイス シングル サインオンを構成する) を参照してください。

### <a name="add-find-my-iphone-for-personal-devices--1427287--"></a>個人デバイスの "iPhone を探す" を追加<!--1427287-->
iOS デバイスのアクティベーション ロックがオンになっているかどうかを表示できるようになりました。 この機能は以前、クラシック ポータルの Intune にありました。

### <a name="remotely-lock-managed-macos-device-with-intune---1437691---"></a>管理されている macOS デバイスを Intune でリモート ロックする<!-- 1437691 -->

紛失した macOS デバイスをロックできます。6 桁の回復用 PIN を設定できます。 ロックされているとき、別のデバイス アクションが送信されるまで、**デバイス概要**ブレードにその PIN が表示されます。

詳細については、「[マネージド デバイスを Intune でリモートからロックする](../remote-actions/device-remote-lock.md)」を参照してください。

### <a name="new-scep-profile-details-supported---1559808---"></a>サポートされる新しい SCEP プロファイル詳細<!-- 1559808 -->

Windows、iOS、macOS、Android プラットフォームで SCEP プロファイルを作成するとき、管理者は追加設定を設定できるようになりました。  管理者は、IMEI、シリアル番号、あるいはサブジェクト名の形式の電子メールなど、一般名を設定できます。

<!-- #### Update to what device details your company may see -1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources. -->

### <a name="retain-data-during-a-factory-reset---1588489---"></a>工場出荷時の設定へのリセット中にデータを保持する <!--1588489 -->
Windows 10 バージョン 1709 以降を工場出荷時の設定にリセットすると、新しい機能が使用できるようになります。 工場出荷時の設定へのリセット中、デバイス登録やプロビジョニングされているその他のデータを保持するかどうかを管理者は指定することができます。

工場出荷時の状態にリセットしても、次のデータが維持されます。
- デバイスに関連付けられているユーザー アカウント
- コンピューターの状態 (ドメイン参加、Azure Active Directory に参加)
- MDM 登録
- OEM でインストールされたアプリ (ストア アプリと Win32 アプリ)
- ユーザー プロファイル
- ユーザー プロファイル以外のユーザー データ
- ユーザー自動ログオン

次のデータは保持されません。
- ユーザー ファイル
- ユーザーがインストールしたアプリ (ストア アプリと Win32 アプリ)
- 初期値ではないデバイス設定


### <a name="window-10-update-ring-assignments-are-displayed---1621837---"></a>Windows 10 更新プログラム リング割り当てが表示される<!-- 1621837 -->
**トラブルシューティング**時、表示しているユーザーに関して、Windows 10 更新プログラム リング割り当てを表示することができます。  

### <a name="windows-defender-advanced-threat-protection-reporting-frequency-settings----1455974----"></a>Windows Defender Advanced Threat Protection の報告頻度設定 <!-- 1455974  -->
Windows Defender Advanced Threat Protection (WDATP) サービスを利用するとき、管理者はマネージド デバイスの報告頻度を管理できます。 新しい **[テレメトリの報告頻度を早める]** オプションを利用すると、WDATP はデータを収集し、さらに頻繁にリスクを評価します。 報告の既定値で速度とパフォーマンスが最適化されます。 報告の頻度を増やすことは、リスクの高いデバイスの場合に有益となります。 この設定は **[デバイス構成]** の **[Windows Defender ATP]** プロファイルにあります。

### <a name="audit-updates---1412961---"></a>監査更新<!-- 1412961 -->  
Intune の監査機能により、Intune に関連する変更操作が記録されます。  あらゆる作成操作、更新操作、削除操作、リモート タスク操作が記録され、1 年間保存されます。  Azure Portal では、ワークロード別の監査データを過去 30 日分表示できます。データの絞り込みも可能です。  対応する Graph API により、前年に格納された監査データを取得できます。

監査は **[モニター]** グループの下にあります。 ワークロード別に **[監査ログ]** メニュー項目があります。

### <a name="company-portal-app-for-macos-is-available--1541700--"></a>macOS 用ポータル サイト アプリ提供開始<!--1541700-->
macOS での Intune ポータル サイトのエクスペリエンスが更新されました。ユーザーが登録済みのすべてのデバイスで必要となるすべての情報とコンプライアンス通知が明確に表示されるように最適化されました。 また、いったん Intune ポータル サイトをデバイスに展開すると、macOS 用 Microsoft 自動更新から更新プログラムが提供されるようになります。 macOS デバイスから Intune ポータル サイトにログインすることで、新しい macOS 用 Intune ポータル サイトをダウンロードできます。

### <a name="microsoft-planner-is-now-part-of-the-mobile-app-management-mam-list-of-approved-apps----1248473---"></a>Microsoft Planner が承認済みアプリのモバイル アプリ管理 (MAM) リストの一部に <!-- 1248473 -->
iOS および Android 用の Microsoft Planner アプリが、モバイル アプリ管理 (MAM) に対する承認済みアプリの一部となりました。 このアプリは、Azure Portal の Intune App Protection ブレードからすべてのテナントに対して構成できます。
- 詳細については、[承認済みアプリの MAM リスト](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)に関するページをご覧ください。

### <a name="per-app-vpn-requirement-update-frequency-on-ios-devices-----1547061---"></a>iOS デバイスでのアプリごとの VPN 要件の更新頻度  <!-- 1547061 -->  
管理者が iOS デバイス上のアプリでアプリごとの VPN 要件を削除できるようになりました。影響を受けるデバイスでは、次回の Intune チェックイン後、通常 15 分以内に反映されます。  

### <a name="support-for-system-center-operations-manager-management-pack-for-exchange-connector---885457---"></a>Exchange Connector 用 System Center Operations Manager 管理パックのサポート<!-- 885457 -->
Exchange Connector 用 System Center Operations Manager 管理パックを Exchange Connector のログ解析に利用できるようになりました。 この機能により、問題のトラブルシューティングが必要な場合に、別の方法でサービスを監視できるようになります。

### <a name="co-management-for-windows-10-devices----1243445---"></a>Windows 10 デバイスの共同管理 <!-- 1243445 -->
共同管理は、従来の管理から最新の管理への橋渡しとなるソリューションであり、段階的なアプローチを使って移行する方向を提示します。 基本的に、共同管理は、Windows 10 デバイスを Configuration Manager と Microsoft Intune で同時に管理すると共に、Active Directory (AD) と Azure Active Directory (Azure AD) に同時に参加させることができるソリューションです。  この構成は、一度にすべてを移行できない組織が適切なペースで時間をかけて最新化するパスを提供します。  

### <a name="restrict-windows-enrollment-by-os-version---245498---"></a>OS のバージョンによる Windows 登録の制限<!-- 245498 -->
Intune 管理者は、デバイス登録に関して、Windows 10 の最小バージョンと最大バージョンを指定できるようになりました。 これらの制限は **[プラットフォーム構成]** ブレードで設定できます。

Intune では、Windows 8.1 の PC とスマートフォンを引き続き登録できます。 ただし、下限と上限を設定できるのは Windows 10 のバージョンだけです。 8\.1 デバイスの登録を許可するには、下限を空のままにします。

### <a name="alerts-for-windows-autopilot-unassigned-devices----1631236---"></a>Windows Autopilot の未割り当てデバイスのアラート <!-- 1631236 -->
**[Microsoft Intune]** 、 **[デバイス登録]** 、 **[概要]** ページには、Windows AutoPilot の未割り当てデバイスの新しいアラートがあります。 このアラートでは、AutoPilot プログラムからのデバイスで、AutoPilot Deployment プロファイルが割り当てられていないデバイスの数が示されます。 アラート内の情報を利用してプロファイルを作成し、未割り当てデバイスに割り当てます。 アラートをクリックすると、Windows AutoPilot の完全一覧とそれらに関する詳細が表示されます。 詳細については、「[Windows AutoPilot Deployment プログラムを使用して Windows デバイスを登録する](../enrollment/enrollment-autopilot.md)」を参照してください。


### <a name="refresh-button-for-devices-list------1333581---"></a>デバイス一覧の [更新] ボタン   <!-- 1333581 -->
デバイス一覧は自動的に更新されないため、新しい [更新] ボタンを利用し、一覧に表示されるデバイスを更新できます。

### <a name="support-for-symantec-cloud-certification-authority-ca----1333638---"></a>Symantec クラウド証明機関 (CA) のサポート <!-- 1333638 -->    
Intune は Symantec クラウド CA をサポートするようになり、Intune Certificate Connector は Symantec クラウド CA から Intune でマネージド デバイスに PKCS 証明書を発行できます。 Microsoft 証明機関 (CA) で Intune Certificate Connector を既に使っている場合は、Intune Certificate Connector の既存の設定を使用して、Symantec CA のサポートを追加できます。

### <a name="new-items-added-to-device-inventory----1404455---"></a>デバイス インベントリに追加された新しい項目  <!--1404455 -->
[登録デバイスによって取得されるインベントリ](../remote-actions/device-inventory.md)で次の新しい項目を利用できるようになりました。

- Wi-Fi MAC アドレス
- 記憶域の合計容量
- 合計空き容量
- MEID
- 通信事業者

### <a name="set-access-for-apps-by-minimum-android-security-patch-on-the-device---1278463---"></a>デバイスでの最低限の Android セキュリティ パッチによりアプリへのアクセスを設定する<!-- 1278463 -->   
管理者は、管理されたアカウントの管理対象アプリケーションにアクセスするために、デバイスにインストールする必要がある最低限の Android セキュリティ パッチを定義することができます。

> [!Note]  
> この機能は、Google によって Android 6.0 以降のデバイスについてリリースされたセキュリティ パッチだけを制限します。

### <a name="app-conditional-launch-support---1193313---"></a>アプリの条件付き起動のサポート<!-- 1193313 -->
IT 管理者は、アプリケーションの起動時にモバイル アプリ管理 (MAM) によって数値の PIN ではなくパスコードを強制する要件を、Azure 管理ポータルで設定できるようになりました。 構成した場合、ユーザーは、MAM 対応のアプリケーションにアクセスする前に、要求された時点で、パスコードを設定および使用する必要があります。 パスコードは、少なくとも 1 つの特殊文字または大文字/小文字アルファベットを含む数値 PIN と定義されます。 Intune の今回のリリースでは、この機能を利用できるのは **iOS のみ**です。 Intune は、数値 PIN に同様の方法でパスコードをサポートし、最小の長さを設定して、文字やシーケンスの繰り返しを許可します。 この機能では、対象のアプリケーションにパスコード設定を適用するのではなく、Intune アプリ SDK とこの機能のコードとを統合するために、アプリケーション (WXP、Outlook、Managed Browser、Yammer など) の参加が必要となります。

### <a name="app-version-number-for-line-of-business-in-device-install-status-report---1233999---"></a>デバイス インストール状態レポートでの基幹業務アプリのバージョン番号<!-- 1233999 -->
このリリースでは、デバイス インストール状態レポートに、iOS および Android 用基幹業務アプリのバージョン番号が表示されます。 この情報を使って、アプリのトラブルシューティングや、古いバージョンのアプリを実行しているデバイスの検索を行うことができます。

### <a name="admins-can-now-configure-the-firewall-settings-on-a-device-using-a-device-configuration-profile---951708---"></a>管理者は、デバイス構成プロファイルを使ってデバイスでのファイアウォールの設定を構成できるようになる<!-- 951708 -->   
管理者は、デバイスのファイアウォールを有効にすることができ、ドメイン ネットワーク、プライベート ネットワーク、パブリック ネットワークのさまざまなプロトコルを構成することもできます。  これらのファイアウォールの設定は、"Endpoint Protection" プロファイルで確認できます。

### <a name="windows-defender-application-guard-helps-protect-devices-from-untrusted-websites-as-defined-by-your-organization---958257---"></a>Windows Defender Application Guard は、組織での定義に従って、信頼されていない Web サイトからデバイスを保護する<!-- 958257 -->   
管理者は、Windows Information Protection ワークフローまたはデバイス構成の新しい "ネットワーク境界" プロファイルを使って、"信頼できる" サイトまたは "企業" サイトを定義できます。 64 ビット Windows 10 デバイスの信頼されたネットワーク境界内にないすべてのサイトは、Microsoft Edge で表示された場合、代わりに Hyper-V 仮想コンピューター内のブラウザーで開かれます。

Application Guard は、"Endpoint Protection" プロファイル内のデバイス構成プロファイルで確認できます。 デバイス構成プロファイルでは、管理者は、仮想化されたブラウザーとホスト マシンの相互作用、信頼されないサイトと信頼されるサイト、および仮想化されたブラウザーで生成されたファイルの保存を構成することができます。 デバイスで Application Guard を使うには、最初にネットワーク境界を構成する必要があります。 デバイスごとにネットワーク境界を 1 つだけ定義することが重要です。  

### <a name="windows-defender-application-control-on-windows-10-enterprise-provides-mode-to-trust-only-authorized-apps---1031096---"></a>Windows 10 Enterprise の Windows Defender Application Control は、承認されたアプリのみを信頼するモードを提供する<!-- 1031096 -->    
毎日何千もの悪意あるファイルが作成される状況においては、ウイルス対策の署名ベースの検出を使ってマルウェアに対抗するのでは、新しい攻撃を十分に防ぐことができない可能性があります。 Windows 10 Enterprise の Windows Defender Application Control を使うと、ウイルス対策ソフトウェアや他のセキュリティ ソリューションによってブロックされない限りアプリを信頼するモードから、企業によって承認されたアプリのみをオペレーティング システムが信頼するモードにデバイスの構成を変更できます。 Windows Defender Application Control でアプリに信頼を割り当てます。

Intune を使って、アプリケーション制御ポリシーを "監査のみ" モードまたは強制モードに構成できます。 "監査のみ" モードで実行している場合、アプリはブロックされません。 "監査のみ" モードでは、すべてのイベントがローカル クライアント ログに記録されます。 また、Windows コンポーネントと Microsoft Store アプリの実行のみを許可するか、またはインテリジェント セキュリティ グラフで定義されている評判の良いアプリの実行も許可するかを構成することもできます。

### <a name="window-defender-exploit-guard-is-a-new-set-of-intrusion-prevention-capabilities-for-windows-10---1063615---"></a>Windows 10 用の新しい侵入防止機能セットである Window Defender Exploit Guard<!-- 1063615 -->   
Window Defender Exploit Guard は、アプリケーションが悪用される可能性を減らすカスタム規則を含み、マクロとスクリプトの脅威を防止し、評判が低い IP アドレスへのネットワーク接続を自動的にブロックして、ランサムウェアや不明の脅威からデータを保護できます。 Windows Defender Exploit Guard は、次のコンポーネントで構成されます。

- **攻撃の回避**では、マクロ、スクリプト、メールの脅威を防ぐことができる規則を提供します。
- **フォルダー アクセスの制御**は、保護されているフォルダーのコンテンツへのアクセスを自動的にブロックします。
- **ネットワーク フィルター**は、アプリから評判の悪い IP/ドメインへの発信接続をブロックします。
- **Exploit Protection** は、アプリケーションを悪用から保護するために使うことができるメモリ、制御フロー、およびポリシーの制限を提供します。

### <a name="manage-powershell-scripts-in-intune-for-windows-10-devices---790537---"></a>Windows 10 デバイスの Intune で PowerShell スクリプトを管理する<!-- 790537 -->

Intune 管理拡張機能を使用すると、Windows 10 デバイスで実行されている Intune で PowerShell スクリプトをアップロードできます。 この拡張機能は Windows 10 モバイル デバイス管理 (MDM) 機能を補完するもので、最新の管理に簡単に移行できます。 詳細については、「[Windows 10 デバイスの Intune で PowerShell スクリプトを管理する](../apps/intune-management-extension.md)」を参照してください。

### <a name="new-device-restriction-settings-for-windows-10--------1308850---"></a>Windows 10 の新しいデバイスの制限設定     <!-- 1308850 -->
- メッセージング (モバイルのみ) - テストまたは MMS のメッセージを無効化します
- パスワード - FIPS と、認証用の Windows Hello デバイス セカンダリ デバイスの使用を有効にする設定 
- ディスプレイ - レガシ アプリの GDI スケーリングをオンまたはオフにする設定

### <a name="windows-10-kiosk-mode-device-restrictions---1308872---"></a>Windows 10 キオスク モード デバイスの制限<!-- 1308872 -->   
Windows 10 デバイスのユーザーをキオスク モードに制限することができます。これは、一連の定義済みアプリにユーザーを制限します。  そのためには、Windows 10 デバイス制限プロファイルを作成し、キオスク設定を設定します。

キオスク モードは、**シングル アプリ** (1 つのアプリだけの実行をユーザーに許可) または**マルチ アプリ** (アプリのセットへのアクセスを許可) の 2 つのモードをサポートします。  ユーザー アカウントとデバイス名を定義します。これらにより、サポートされるアプリが決まります。  ユーザーはログイン時に定義済みのアプリに制限されます。  詳細については、「[AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp)」を参照してください。 

キオスク モードには以下が必要です。

- Intune が MDM 機関である必要があります。
- アプリは、ターゲット デバイスに既にインストールされている必要があります。
- デバイスは、[適切にプロビジョニングされている](https://docs.microsoft.com/windows/configuration/set-up-a-kiosk-for-windows-10-for-desktop-editions)必要があります。

### <a name="new-device-configuration-profile-for-creating-network-boundaries---1311967---"></a>ネットワーク境界を作成するための新しいデバイス構成プロファイル<!-- 1311967 -->   
**ネットワーク境界**と呼ばれる新しいデバイス構成プロファイルが、他のデバイス構成プロファイルと同じ場所にあります。 このプロファイルを使用して、会社のもので信頼できると見なす必要があるオンライン リソースを定義します。 Windows Defender Application Guard や Windows Information Protection などの機能をデバイスで使用するには、"*事前*" にデバイスに対してネットワーク境界を定義する必要があります。 デバイスごとにネットワーク境界を 1 つだけ定義することが重要です。

信頼できるエンタープライズ クラウド リソース、IP アドレス範囲、内部プロキシ サーバーを定義できます。 定義したネットワーク境界は、Windows Defender Application Guard や Windows Information Protection 保護などの他の機能で使うことができます。

### <a name="two-additional-settings-for-windows-defender-antivirus---1338409---"></a>Windows Defender ウイルス対策用の 2 つの追加設定<!-- 1338409 -->  
**ファイル ブロック レベル**

| | |
|---|---|
| 未構成 | **未構成**は、Windows Defender ウイルス対策の既定のブロック レベルを使用し、正当なファイルが検出されるリスクを高めることなく強力な検出を提供します。 |
| 高 | **高**は、強力なレベルの検出を適用します。
| 高 +  | **高 +** は、高いレベルに加えて、クライアントのパフォーマンスに影響を与える可能性がある保護手段を提供します。
| ゼロ トレランス  | **ゼロ トレランス**は、不明な実行可能ファイルをすべてブロックします。 |

まれですが、**高**に設定すると、一部の正当なファイルが検出される可能性があります。
ファイル ブロック レベルは既定の**未構成**に設定することをお勧めします。

**クラウドによるファイル スキャンの時間延長**  

| | |
|--|--|
| 秒数 (0 - 50) | Windows Defender ウイルス対策がクラウドからの結果の待機中にファイルをブロックする最大時間を指定します。 既定値は 10 秒です。ここで指定した延長時間 (最大 50 秒) は、この 10 秒間に追加されます。 ほとんどの場合、スキャンは最大値よりはるかに短い時間で済みます。 時間を延長すると、クラウドは疑わしいファイルを徹底的に調査できます。 この設定を有効にし、少なくとも 20 秒の追加を指定することをお勧めします。 |

### <a name="citrix-vpn-added-for-windows-10-devices---1512457---"></a>Windows 10 デバイスに追加された Citrix VPN<!-- 1512457 -->  
Windows 10 デバイス用に Citrix VPN を構成できます。 Windows 10 以降用に VPN を構成するときに、 **[基本 VPN]** ブレードの *[接続の種類を選びます]* の一覧で、Citrix VPN を選ぶことができます。

> [!Note]
> Citrix の構成は、iOS および Android 用に存在しました。

### <a name="wi-fi-connections-support-pre-shared-keys-on-ios---1550823---"></a>Wi-Fi 接続は iOS で事前共有キーに対応<!-- 1550823 -->
ユーザーは iOS デバイスで WPA/WPA2 Personal 接続に事前共有キー (PSK) を使用するように Wi-Fi プロファイルを構成できます。 これらのプロファイルは、デバイスが Intune に登録されたとき、ユーザーのデバイスにプッシュされます。

プロファイルがデバイスにプッシュされたとき、次の手順はプロファイル構成によって決まります。  自動的に接続するように設定されている場合、ネットワークが次に必要になったとき、自動的に接続されます。  プロファイルが手動接続になっている場合、ユーザーは接続を手動で開始する必要があります。  

### <a name="access-to-managed-app-logs-for-ios---1469920---"></a>iOS の管理対象アプリ ログにアクセス<!-- 1469920 -->
Managed Browser をインストールしているエンド ユーザーは、Microsoft が公開したすべてのアプリの管理状態を表示し、管理対象 iOS アプリの問題を解消するためにログを送信できるようになりました。

iOS デバイスの Managed Browser でトラブルシューティング モードを有効にする方法については、「[iOS で Managed Browser を使用し、管理対象アプリ ログにアクセスする方法](../apps/app-configuration-managed-browser.md#how-to-access-to-managed-app-logs-using-the-managed-browser-on-ios)」を参照してください。

### <a name="improvements-to-device-setup-workflow-in-the-company-portal-for-ios-in-version-290---1417174---"></a>iOS 用ポータル サイト バージョン 2.9.0 でのデバイスのセットアップ ワークフローの機能強化<!-- 1417174 -->

iOS 用ポータル サイト アプリでのデバイス セットアップ ワークフローが改善されました。 言葉がよりわかりやすくなり、可能な範囲で画面をまとめました。 セットアップのテキスト全体でお客様の会社名を使用することで、表現がより会社に合ったものになっています。 この更新されたワークフローについては、 [アプリ UI ページの新機能](../whats-new-app-ui.md)に関するページをご覧ください。


### <a name="user-entity-contains-latest-user-data-in-data-warehouse-data-model---1544273---"></a>ユーザー エンティティにデータ ウェアハウス データ モデルの最新のユーザー データが含まれている<!-- 1544273 -->
Intune データ ウェアハウス データ モデルの最初のバージョンでは、最近の Intune 履歴データのみが含まれていました。 レポートの作成者は、ユーザーの最新の状態をキャプチャできませんでした。 今回の更新プログラムでは、最新のユーザー データを使用して**ユーザー エンティティ**が設定されます。

<!-- ########################## -->
## <a name="october-2017"></a>2017 年 10 月

### <a name="ios-and-android-line-of-business-app-version-number-is-visible---1380712---"></a>iOS と Android の基幹業務アプリのバージョン番号が表示可能<!-- 1380712 -->

Intune では、iOS と Android の基幹業務アプリのバージョン番号が表示されるようになりました。 Azure Portal のアプリ一覧とアプリ概要ブレードで番号が表示されます。 エンド ユーザーは、ポータル サイト アプリと Web ポータルでアプリ番号を確認できます。

__バージョン番号 (フル)__ このフル バージョン番号はアプリのリリースを特定します。 この番号は _バージョン_(_ビルド_) の形式で表示されます。 たとえば、2.2(2.2.17560800) のようになります。

バージョン番号 (フル) を構成する 2 つの要素:

- **バージョン**  
  バージョン番号は、人間が判読できるアプリのリリース番号です。 エンド ユーザーがアプリの各種リリースを区別するために使用されます。

- **ビルド番号**  
  ビルド番号は、アプリの検出に利用される内部番号です。また、プログラミングでアプリを管理するために利用されます。 ビルド番号は、コードの変更を参照するアプリのイテレーションを参照します。

バージョン番号と基幹業務アプリの開発については、「[Microsoft Intune アプリ SDK の概要](../developer/app-sdk-get-started.md#line-of-business-app-version-numbers)」を参照してください。

### <a name="device-and-app-management-integration---677972---"></a>デバイスとアプリの管理の統合<!-- 677972 -->   
Intune のモバイル デバイス管理 (MDM) とモバイル アプリケーション管理 (MAM) はどちらも Azure Portal からアクセスできるようになり、Intune はアプリケーション管理とデバイス管理に関する IT 管理者エクスペリエンスの統合を開始しました。 これらの変更は、デバイスとアプリの管理エクスペリエンスの簡素化を目的としたものです。

MDM と MAM の変更の詳細については、[Intune サポート チーム ブログ](https://blogs.technet.microsoft.com/intunesupport/2017/09/19/support-tip-setting-up-communication-between-mam-managed-and-mdm-managed-apps/)での案内をご覧ください。

### <a name="new-enrollment-alerts-for-apple-devices---1471790---"></a>Apple デバイスの新しい登録アラート<!-- 1471790 -->
登録の概要ページには、IT 管理者のために、Apple デバイスの管理に便利なアラートが表示されるようになります。 Apple MDM プッシュ証明書の有効期間が近づいたり、既に過ぎているとき、Device Enrollment Program の有効期間が近づいたり、既に過ぎているとき、Device Enrollment Program に未割り当てのデバイスがあるとき、アラートが概要ページに表示されます。

### <a name="support-token-replacement-for-app-configuration-without-device-enrollment---1080364---"></a>デバイス登録のないアプリ構成のトークン置換をサポート<!-- 1080364 -->

登録されていないデバイス上のアプリに関して、アプリ構成の動的な値にトークンを利用できます。 詳細については、「[デバイス登録なしで管理対象アプリ用アプリ構成ポリシーを追加する](../apps/app-configuration-policies-managed-app.md)」を参照してください。

### <a name="updates-to-the-company-portal-app-for-windows-10--1299474--"></a>Windows 10 用ポータル サイト アプリの更新内容<!--1299474-->
Windows 10 用ポータル サイト アプリの [設定] ページが更新され、すべての設定で、設定と目的のユーザー アクションの一貫性が高まっています。 また、その他の Windows アプリのレイアウトと一致させる更新も行われています。 更新前/後のイメージは、[アプリ UI ページの新機能](../whats-new-app-ui.md)に関するページでご覧いただけます。

### <a name="inform-end-users-what-device-information-can-be-seen-for-windows-10-devices--1337920--"></a>Windows 10 デバイスで確認できるデバイス情報のエンドユーザーへの通知<!--1337920-->
Windows 10 用ポータル サイト アプリの [デバイスの詳細] 画面に **[所有権の種類]** が追加されました。 これにより、ユーザーはこのページから直接、Intune のエンド ユーザー ドキュメントにあるプライバシーの詳細を参照できます。この情報は、 **[バージョン情報]** 画面でも確認できます。

### <a name="feedback-prompts-for-the-company-portal-app-for-android--1165249--"></a>Android 用ポータル サイト アプリに関するフィードバック プロンプト<!--1165249-->
Android 用ポータル サイト アプリからエンド ユーザー フィードバックを要求されるようになりました。 このフィードバックは Microsoft に直接送信され、エンドユーザーは一般の Google Play ストアでアプリをレビューできます。 フィードバックは必須ではなく、ユーザーは簡単にこれを拒否して、アプリの使用を続行できます。

<!-- #### Update to what device details an organization can see 1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources.-->

### <a name="helping-your-users-help-themselves-with-the-company-portal-app-for-android---1573324-1573150-1558616-1564878---"></a>Android 向けポータル サイト アプリに関してユーザーの自己解決をサポートする<!-- 1573324, 1573150, 1558616, 1564878 -->

Android 向けポータル サイト アプリでは、エンド ユーザーへの指示が追加されています。それは新しいユース ケースの理解や、可能な場合にはその自己解決にも役立ちます。
- 追加が許されているデバイスの最大数に到達した場合、デバイスを削除するように、エンド ユーザーは [Azure Active Directory ポータル](https://account.activedirectory.windowsazure.com/r/#/profile) に誘導されます。
- [Samsung Knox デバイスのアクティベーション エラーを解消する](https://go.microsoft.com/fwlink/?linkid=859718)か、[節電モードをオフにする](/intune-user-help/power-saving-mode-android)ための手順がエンド ユーザーに表示されます。 いずれの解決策でも問題が解消されない場合、[Microsoft にログを送信する](/intune-user-help/send-logs-to-microsoft-android)方法を説明します。

### <a name="new-resolve-action-available-for-android-devices---1583480---"></a>Android デバイスで利用できる新しい '解決' アクション<!-- 1583480 -->

Android のポータル サイト アプリの _[デバイス設定の更新]_ ページに '解決' アクションが導入されます。 このオプションを選択すると、デバイスの非準拠の原因になっている設定に、エンド ユーザーが直接誘導されます。 Android 向けのポータル サイト アプリでは現在のところ、[デバイス パスコード](/intune-user-help/set-your-pin-or-password-android)、[USB デバッグ](/intune-user-help/you-need-to-turn-off-usb-debugging-android)、[不明なソース](/intune-user-help/you-need-to-turn-off-unknown-sources-android)設定に対してこのアクションがサポートされています。

### <a name="device-setup-progress-indicator-in-android-company-portal---1565657---"></a>Android 用ポータル サイトのデバイスのセットアップ進行状況インジケーター<!-- 1565657 -->
Android 用ポータル サイト アプリでは、ユーザーがデバイスを登録しているときに、デバイスのセットアップ進行状況インジケーターが示されます。 このインジケーターで新しいステータスが表示されます。初めに表示されるものから挙げると、[デバイスをセットアップしています...]、[デバイスを登録しています]、[デバイスの登録を終了しています]、[デバイスのセットアップを終了しています] です。

### <a name="certificate-based-authentication-support-on-the-company-portal-for-ios--1029830--"></a>iOS 用ポータル サイトでの証明書ベースの認証のサポート<!--1029830-->
iOS 用ポータル サイト アプリでの証明書ベースの認証 (CBA) のサポートが追加されました。 CBA を使用するユーザーは、ユーザー名を入力した後、[Sign in with a certificate]\(証明書でサインインする\) リンクをタップします。 Android および Windows 用ポータル サイト アプリでは、既に CBA がサポートされています。 詳細については、[ポータル サイト アプリにサインインする](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal)方法に関するページをご覧ください。

### <a name="apps-that-are-available-with-or-without-enrollment-can-now-be-installed-without-being-prompted-for-enrollment---1334712---"></a>登録の有無にかかわらず利用可能なアプリについて、登録を求められずにインストールできるようになりました。<!-- 1334712 -->

Android ポータル サイト アプリでの登録の有無にかかわらず利用可能な業務用アプリについて、登録を求められずにインストールできます。

### <a name="windows-autopilot-deployment-program-support-in-microsoft-intune----747617----"></a>Microsoft Intune で Windows AutoPilot Deployment プログラムをサポート <!-- 747617  -->
Microsoft Intune と Windows AutoPilot Deployment プログラムを使用して、IT が関与しなくても、ユーザーが自分の会社のデバイスをプロビジョニングできるようになりました。 OOBE (Out-of-Box Experience) をカスタマイズしたり、ユーザーのデバイスの Azure AD への参加および Intune への登録について、ユーザーをガイドすることができます。 Microsoft Intune と Windows AutoPilot を合わせて使用すると、オペレーティング システム イメージを展開、保持、管理する必要がなくなります。 詳細については、「[Windows AutoPilot Deployment プログラムを使用して Windows デバイスを登録する](../enrollment/enrollment-autopilot.md)」を参照してください。

### <a name="quickstart-for-device-enrollment----1425655---"></a>デバイス登録のクイック スタート <!-- 1425655 --> 
**デバイスの登録**でクイック スタートが利用できるようになり、プラットフォームの管理と登録プロセスの構成のための参考資料の表が提供されます。 各項目の簡単な説明と詳細な手順があるドキュメントへのリンクにより、簡単に使用開始するために役立つドキュメントを提供します。

### <a name="device-categorization---1427491---"></a>デバイスのカテゴリ化<!-- 1427491 -->
**[デバイス] > [概要]** ブレードの登録済みデバイス プラットフォームのグラフは、プラットフォーム (Android、iOS、macOS、Windows、Windows Mobile など) ごとにデバイスをまとめています。  他のオペレーティング システムを実行しているデバイスは "その他" にグループ化されています。  これには、Blackberry、NOKIA、およびその他のメーカー製のデバイスが含まれます。  

テナント内で影響を受けるデバイスを把握するには、 **[管理] > [すべてのデバイス]** を選択してから、 **[フィルター]** を使用して **[OS]** フィールドを制限します。

### <a name="zimperium---new-mobile-threat-defense-partner-----954681---"></a>Zimperium - 新しい Mobile Threat Defense パートナー  <!-- 954681 -->  
Microsoft Intune に統合された Mobile Threat Defense ソリューションである Zimperium によって実行されるリスク評価に基づき、条件付きアクセスを利用し、モバイル デバイスから会社のリソースへのアクセスを制御できます。

#### <a name="how-integration-with-intune-works"></a>Intune との統合のしくみ
リスクは、Zimperium を実行するデバイスから収集される製品利用統計情報に基づいて評価されます。 Intune デバイス コンプライアンス ポリシーにより有効になった Zimperium リスク評価に基づいて、EMS 条件付きアクセスのポリシーを構成できます。Intune デバイス コンプライアンス ポリシーは、検出された脅威に基づき、非準拠デバイスから企業リソースへのアクセスを許可したり、拒否したりするために利用できます。

### <a name="new-settings-for-windows-10-device-restriction-profile-----978575-1308849---"></a>Windows 10 デバイス制限プロファイルの新しい設定 <!--- 978575, 1308849, -->  
Windows Defender SmartScreen カテゴリの Windows 10 デバイス制限プロファイルに新しい設定が追加されます。

Windows 10 デバイス制限のプロファイルの詳細については、「[Windows 10 以降のデバイスの制限設定](../configuration/device-restrictions-windows-10.md)」を参照してください。

### <a name="remote-support-for-windows-and-windows-mobile-devices-----1070473---"></a>Windows と Windows Mobile デバイスのリモート サポート  <!-- 1070473 -->  
[TeamViewer](https://www.teamviewer.com) ソフトウェア (別売り) を使用して、Windows と Windows Mobile デバイスを実行するユーザーに Intune でリモート アシスタンスを提供できるようになりました。

### <a name="scan-devices-with-windows-defender---1280988--1280990-----"></a>Windows Defender でデバイスをスキャンする<!-- 1280988  1280990   -->
管理された Windows 10 デバイス上で Windows Defender ウイルス対策を使って **クイック スキャン**、**フル スキャン**、**署名更新**を実行できるようになりました。 デバイスの概要ブレードから、デバイス上で実行するアクションを選びます。 コマンドがデバイスに送信される前に、アクションの確認を求められます。 

**クイック スキャン**: クイック スキャンでは、レジストリ キーや既知の Windows スタートアップ フォルダーなど、マルウェアが起動するように登録されている場所がスキャンされます。 クイック スキャンには、平均 5 分かかります。 クイック スキャンは、ファイルの開閉時やユーザーがフォルダーに移動したときにファイルをスキャンする **[Always-on real-time protection]\(リアルタイム保護を常に有効にする\)** 設定と組み合わせると、システムやカーネル内に存在する可能性があるマルウェアから保護するのに役立ちます。 完了すると、ユーザーのデバイスにスキャン結果が表示されます。 

**フル スキャン**: フル スキャンは、マルウェアの脅威が発生したデバイスで、より徹底的なクリーンアップが必要な非アクティブなコンポーネントがあるかどうかを識別するために使用できます。また、オンデマンド スキャンを実行する場合に便利です。 フル スキャンは、実行に 1 時間かかる場合があります。 完了すると、ユーザーのデバイスにスキャン結果が表示されます。 

**署名更新**: 署名更新コマンドを使用すると、Windows Defender ウイルス対策のマルウェア定義と署名が更新されます。 マルウェア検出における Windows Defender ウイルス対策ソフトウェアの効果を確保するために役立ちます。 この機能は Windows 10 デバイス専用であり、デバイスのインターネット接続を一時中断します。 

### <a name="the-enabledisable-button-is-removed-from-the-intune-certificate-authority-page-of-the-intune-azure-portal----1400455---"></a>Intune Azure Portal の Intune 証明機関のページからの [有効]/[無効] ボタンの削除 <!-- 1400455 -->
 Intune の証明書コネクタの設定で、余分な手順を排除しています。 現在は、証明書コネクタをダウンロードしてから、Intune コンソールでそれを有効にしています。 ただし、Intune コンソールでコネクタを無効にすると、コネクタは証明書の発行に進みます。

#### <a name="how-does-this-affect-me"></a>ユーザーへの影響
10 月以降、Azure Portal の証明機関のページに、[有効]/[無効] ボタンが表示されなくなります。 コネクタ機能は変わりません。 証明書は、Intune に登録したデバイスに引き続き展開されます。 引き続き、証明書コネクタをダウンロードしてインストールすることができます。 証明書の発行を停止するには、証明書コネクタを無効にするのではなく、今すぐアンインストールします。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>この変更に対して必要な準備
現在、無効になっている証明書コネクタがある場合は、それをアンインストールする必要があります。

### <a name="new-settings-for-windows-10-team-device-restriction-profile------1308838---"></a>Windows 10 Team デバイス制限プロファイルの新しい設定  <!--- 1308838 -->
このリリースでは、Surface Hub デバイスの制御に役立つように、Windows 10 Team デバイス制限プロファイルに多数の新しい設定が追加されています。

このプロファイルについて詳しくは、[Windows 10 Team デバイスの制限設定](../configuration/device-restrictions-windows-10-teams.md)に関するページをご覧ください。

### <a name="prevent-users-of-android-devices-from-changing-their-device-date-and-time----1333292---"></a>Android デバイス ユーザーによるデバイスの日付と時刻の変更を防止する <!-- 1333292 -->
[Android カスタム デバイス ポリシー](../configuration/custom-settings-android.md)を使用して、Android デバイス ユーザーがデバイスの日付や時刻を変更できないように設定できます。

この設定を行うには、./Vendor/MSFT/PolicyManager/My/System/AllowDateTimeChange の設定 URI を使用して Android カスタム ポリシーを構成し、これを **TRUE** に設定して該当のグループに割り当てます。

### <a name="bitlocker-device-configuration---1397398---"></a>BitLocker デバイス構成<!-- 1397398 -->
**[Windows 暗号化] > [Base Settings]\(基本設定\)** に、新たに **[他のディスクの暗号化に対する警告]** 設定が追加されました。この設定では、ユーザーのデバイス上で使われている可能性がある、他のディスクの暗号化についての[警告プロンプト](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp#allowwarningforotherdiskencryption)を無効にできます。  警告プロンプトの利用には、デバイス上で BitLocker をセットアップする前にエンド ユーザーの同意が必要であり、エンド ユーザーによって承諾されるまで BitLocker のセットアップはブロックされます。  この新しい設定では、エンド ユーザーに対する警告が無効になります。


### <a name="volume-purchase-program-for-business-apps-will-now-sync-to-your-intune-tenant---800882---"></a>Intune テナントと同期されるようになった Volume Purchase Program for Business アプリ<!-- 800882 -->  
サードパーティの開発者は、iTunes Connect で指定されている承認された Volume Purchase Program (VPP) for Business メンバーにプライベートでアプリを配布できます。 VPP for Business のメンバーは、Volume Purchase Program App Store にサインインし、アプリを購入できます。

このリリースでは、エンド ユーザーが購入した VPP for Business アプリがそのユーザーの Intune テナントに同期されます。

### <a name="select-apple-countryregion-store-to-sync-vpp-apps----1332311---"></a>Apple の国/リージョン別ストアを選択して VPP アプリを同期する <!-- 1332311 -->  
Volume Purchase Program (VPP) トークンをアップロードする際に、VPP 国/リージョン別ストアを構成できます。 指定された VPP 国/リージョン別ストアにある全ロケールに対応した VPP アプリが、Intune によって同期されます。

> [!NOTE]  
> 現在、Intune で同期されるのは、Intune テナントが作成された Intune ロケールに一致する VPP 国/リージョン別ストアの VPP アプリのみです。


### <a name="block-copy-and-paste-between-work-and-personal-profiles-in-android-for-work---1098994---"></a>Android for Work で仕事用プロファイルと個人プロファイルの間でのコピーおよび貼り付けを防ぐ<!-- 1098994 -->
このリリースでは、仕事用アプリと個人用アプリとの間でコピーおよび貼り付けができないように、Android for Work の仕事用プロファイルを構成できます。 この新しい設定は、 **[仕事用プロファイルの設定]** の **[Android for Work]** プラットフォームの **[デバイスの制限]** プロファイルにあります。

### <a name="create-ios-apps-limited-to-specific-regional-apple-app-stores---1281692---"></a>特定地域の Apple App Store のみを対象とした iOS アプリを作成する<!-- 1281692 -->
Apple App Store 管理対象アプリの作成時に、国/リージョンのロケールを指定できるようになります。

> [!Note]  
> 現在、Apple App Store の管理対象アプリは、米国/リージョンのストアで販売されるものしか作成できません。

### <a name="update-ios-vpp-user-and-device-licensed-apps----1305564---"></a>iOS VPP ユーザーとデバイスにライセンスされたアプリを更新する <!-- 1305564 -->  
Intune サービスを介して特定の iOS VPP トークンに対して購入されたすべてのアプリを更新するように、トークンを構成できるようになります。 アプリ ストア内の VPP アプリ更新プログラムが Intune によって検出され、デバイスのチェックイン時に自動的にデバイスにプッシュされます。

VPP トークンを設定して、自動更新を有効にする手順については、「[Volume Purchase Program で購入した iOS アプリを Microsoft Intune で管理する方法] (/intune/vpp-apps-ios)」を参照してください。


### <a name="user-device-association-entity-collection-added-to-intune-data-warehouse-data-model---1187917---"></a>Intune データ ウェアハウスのデータ モデルに追加されたユーザー デバイス関連付けエンティティ コレクション<!-- 1187917 -->
ユーザーとデバイスのエンティティ コレクションを関連付けるユーザー デバイス関連付け情報を使って、レポートやデータの視覚エフェクトを作成できるようになりました。 このデータ モデルは、OData エンドポイントを使うか、カスタム クライアントを開発すると、[Data Warehouse Intune]\(データ ウェアハウス Intune\) ページから取得した Power BI ファイル (PBIX) を使ってアクセスできます。

### <a name="review-policy-compliance-for-windows-10-update-rings---1067886---"></a>Windows 10 更新リングのポリシー準拠状況を確認する<!-- 1067886 -->
[ソフトウェア更新プログラム] > [更新プログラムごとのリングの展開の状態] から Windows 10 更新リングのポリシー レポートを確認できるようになります。 ポリシー レポートには、構成した更新リングの展開状態が表示されています。 

### <a name="new-report-that-lists-ios-devices-with-older-ios-versions-----1352223---"></a>古い iOS バージョンの iOS デバイス一覧が記載された新しいレポート  <!-- 1352223 -->
**[ソフトウェア更新プログラム]** ワークスペースから **[Out-of-date iOS Devices]\(古い iOS デバイス\)** レポートが利用できます。 このレポートには、iOS の更新ポリシーが対象とする監視対象の iOS デバイスの一覧と利用可能な更新が表示されます。 デバイスごとに、デバイスが自動的に更新されない理由のステータスを確認できます。 

### <a name="view-app-protection-policy-assignments-for-troubleshooting----1475003---"></a>トラブルシューティングのアプリ保護ポリシー割り当てを確認する<!--  1475003 -->
今後のリリースでは、トラブルシューティング ブレードにある **[割り当て]** ボックスの一覧に、 **[App protection policy]\(アプリの保護ポリシー\)** オプションが追加される予定です。 アプリの保護ポリシーを選んで、特定のユーザーに割り当てられているアプリ保護ポリシーを確認できるようになります。



### <a name="improvements-to-device-setup-workflow-in-company-portal--1490692--"></a>ポータル サイトでのデバイスのセットアップ ワークフローの機能強化<!--1490692-->
Android 用ポータル サイト アプリにおけるデバイスのセットアップ ワークフローを改善しました。 言語がよりわかりやすく、会社固有のものとなり、可能な範囲で画面をまとめるようにしました。 これらの変更については、「[アプリの UI の新機能](whats-new-app-ui.md#week-of-october-2-2017)」ページで確認できます。

### <a name="improved-guidance-around-the-request-for-access-to-contacts-on-android-devices--1484985--"></a>Android デバイスでの連絡先へのアクセス要求に関するガイダンスの改善<!--1484985-->

Android 用ポータル サイト アプリでは、エンド ユーザーに対して連絡先情報へのアクセス許可を求めることがあります。 エンド ユーザーがこのアクセスを拒否すると、条件付きアクセス用のアクセス許可を付与するように通知するアプリ内通知が表示されるようになります。 

### <a name="secure-startup-remediation-for-android--1490712--"></a>Android でのセキュリティで保護された起動の修復<!--1490712-->

Android デバイスを使用するエンド ユーザーは、ポータル サイト アプリ内で非準拠の理由をタップできるようになりました。 可能な場合には、問題を解決するために設定アプリの適切な場所に直接移動します。 

### <a name="additional-push-notifications-for-end-users-on-the-company-portal-app-for-android-oreo--1475932--"></a>Android Oreo のポータル サイト アプリにエンド ユーザー向けプッシュ通知が追加<!--1475932-->

エンド ユーザーには、Android Oreo のポータル サイト アプリが Intune サービスからのポリシーの取得などのバックグラウンド タスクが実行されているときにそれを示す追加の通知が表示されます。 これにより、ポータル サイトがデバイス上でいつ管理タスクを実行しているかが、エンド ユーザーにとってより分かりやすくなります。 これは、Android Oreo 用のポータル サイト アプリの[ポータル サイト UI の全体的な最適化](https://blogs.technet.microsoft.com/intunesupport/2017/08/21/android-8-0-o-behaviour-changes-and-microsoft-intune)の一部です。 

Android Oreo で有効になっている新しい UI 要素がさらに最適化されています。  エンドユーザーには、ポータル サイトが Intune サービスからのポリシーの取得などのバックグラウンド タスクを実行しているときにそれを示す追加の通知が表示されます。  これにより、ポータル サイトがデバイスで管理タスクをいつ実行しているかがエンド ユーザーにわかりやすくなります。

### <a name="new-behaviors-for-the-company-portal-app-for-android-with-work-profiles---1485783---"></a>仕事用プロファイルを使った Android 用ポータル サイト アプリの新しい動作<!-- 1485783 -->

仕事用プロファイルを使用して Android for Work デバイスを登録した場合は、仕事用プロファイルのポータル サイト アプリでデバイスの管理タスクが実行されます。 

個人用プロファイルの MAM が有効なアプリを使用している場合を除いては、Android 用ポータル サイト アプリを使用することはなくなります。 仕事用プロファイルが正常に登録されると、仕事用プロファイル エクスペリエンスを向上させるために Intune が自動で個人用ポータル サイト アプリを非表示にします。

Android 用ポータル サイト アプリは、ブラウザーで [Play ストアのポータル サイト](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)を表示して **[有効]** をタップすれば、いつでも個人用プロファイル内で有効化できます。

### <a name="company-portal-for-windows-81-and-windows-phone-81-moving-to-sustaining-mode--1428681--"></a>維持モードに移行中の Windows 8.1 および Windows Phone 8.1 用ポータル サイト<!--1428681-->

2017 年 10 月以降、Windows 8.1 および Windows Phone 8.1 用ポータル サイト アプリは維持モードに移行されます。 つまり、アプリや既存のシナリオ (登録やコンプライアンスなど) で、引き続きこれらのプラットフォームがサポートされます。 これらのアプリは引き続き、Microsoft Store などの既存のリリース チャネルからダウンロードできます。 

維持モードになると、当該アプリは、重要なセキュリティ更新プログラムのみを受信するようになります。 追加の更新プログラムや追加機能はリリースされなくなります。 新機能が必要な場合は、デバイスを Windows 10 または Windows 10 Mobile に更新することをおすすめします。 


### <a name="block-unsupported-samsung-knox-device-enrollment----1490695---"></a>サポートされていない Samsung KNOX デバイスの登録をブロックする <!-- 1490695 -->

ポータル サイト アプリは、サポートされている Samsung Knox デバイスのみを登録しようとします。 MDM の登録を妨げる KNOX ライセンス認証エラーの発生を回避するために、登録対象のデバイスが [Samsung によって発行されたデバイス一覧](https://www.samsungknox.com/knox-supported-devices/knox-workspace)に掲載されている場合にのみ、その登録が試行されます。 Samsung デバイスには、KNOX をサポートするモデル番号を持つものがある一方で、そうでないものもあります。 使用するデバイスが Knox に対応しているかどうかを、デバイスを購入したり展開したりする前に販売店に確認してください。 検証済みのデバイスの完全な一覧については、「[Android and Samsung KNOX Standard policy settings (Android および Samsung KNOX Standard のポリシー設定)](supported-devices-browsers.md#intune-supported-web-browsers)」をご覧ください。

### <a name="end-of-support-for-android-43-and-lower---1171126-1326920---"></a>Android 4.3 以前のサポートの終了<!-- 1171126, 1326920 -->
Android の管理対象アプリとポータル サイト アプリから会社のリソースにアクセスするには、Android 4.4 以降が必要になりました。 12 月には、登録されているすべてのデバイスがインベントリから削除され、会社のリソースにアクセスできなくなります。 MDM を使わずにアプリの保護ポリシーを使用している場合、アプリは更新プログラムを受信できなくなり、時間の経過と共にエクスペリエンスの質が低下していきます。

### <a name="inform-end-users-what-device-information-can-be-seen-on-enrolled-devices--1165314--"></a>登録されているデバイスで確認可能なデバイス情報のエンドユーザーへの通知<!--1165314-->
すべてのポータル サイト アプリの [デバイスの詳細] 画面に、 **[所有権の種類]** が追加されます。 これにより、[会社が確認できる情報](/intune-user-help/what-info-can-your-company-see-when-you-enroll-your-device-in-intune)に関するページから直接、プライバシーの詳細を確認できるようになります。 近日中にすべてのポータル サイト アプリにこの機能が追加される予定です。 iOS 用のこの機能については [9 月](#september-2017)にお知らせしました。

<!-- ########################## -->
## <a name="september-2017"></a>2017 年 9 月

### <a name="intune-supports-ios-11--1428975--"></a>Intune が iOS 11 をサポート<!--1428975-->
Intune は iOS 11 をサポートします。 これについては、[Intune サポート ブログ](https://blogs.technet.microsoft.com/intunesupport/2017/09/12/support-tip-intune-support-for-ios-11/)ですでに発表しました。

### <a name="end-of-support-for-ios-80---1164477---"></a>iOS 8.0 のサポートの終了<!-- 1164477 -->
iOS の管理対象アプリとポータル サイト アプリから会社のリソースにアクセスするには、iOS 9.0 以降が必要になりました。 この 9 月までに更新されないデバイスは、ポータル サイトまたはそれらのアプリにアクセスできなくなります。 

### <a name="refresh-action-added-to-the-company-portal-app-for-windows-10--1132468--"></a>Windows 10 用ポータル サイト アプリに追加された更新アクション<!--1132468-->
Windows 10 向けのポータル サイト アプリでは、ユーザーがプルして更新するか、デスクトップで F5 キーを押して、アプリのデータを更新できます。

### <a name="inform-end-users-what-device-information-can-be-seen-for-ios--739894--"></a>確認可能な iOS デバイス情報のエンドユーザーへの通知<!--739894-->

iOS 用ポータル サイト アプリの [デバイスの詳細] 画面に **[所有権の種類]** が追加されました。 これにより、ユーザーはこのページから直接、Intune のエンド ユーザー ドキュメントにあるプライバシーの詳細を参照できます。この情報は [バージョン情報] 画面でも確認できます。

### <a name="allow-end-users-to-access-the-company-portal-app-for-android-without-enrollment---1169910---"></a>エンドユーザーの Android 用のポータル サイト アプリへのアクセスを登録なしで許可する<!---1169910--->

エンドユーザーは間もなく Android 用のポータル サイト アプリにアクセスするために、デバイスを登録しなくて済むようになります。 アプリの保護ポリシーを使用する組織のエンドユーザーが、ポータル サイト アプリを開いたときに、デバイスの登録を求めるプロンプトが表示されなくなります。 エンドユーザーはデバイスを登録することなく、ポータル サイトからアプリをインストールできるようにもなります。 


### <a name="easier-to-understand-phrasing-for-the-company-portal-app-for-android---1396349---"></a>Android 用ポータル サイト アプリの文言をわかりやすいように変更<!---1396349--->  

Android 用ポータル サイト アプリの登録プロセスが簡略化されました。テキストが新しくなり、エンド ユーザーがより簡単に登録できるようになりました。 カスタム登録ドキュメントをお持ちの場合は、ドキュメントを更新して新しい画面を反映したいと思われるかもしれません。 「[Intune とエンド ユーザー アプリの UI の更新](whats-new-app-ui.md#week-of-september-11-2017)」のページにサンプル画像があります。

### <a name="windows-10-company-portal-app-added-to-windows-information-protection-allow-policy---677129---"></a>Windows 情報保護許可ポリシーに追加された Windows 10 ポータル サイト アプリ<!-- 677129 -->

Windows 情報保護 (WIP) をサポートするために、Windows 10 のポータル サイト アプリが更新されました。 WIP 許可ポリシーにアプリを追加できます。 この変更により、アプリを **[適用除外]** 一覧に追加する必要がなくなります。


<!-- ########################## -->
## <a name="august-2017"></a>2017 年 8 月

### <a name="improvements-to-device-overview---1404453---"></a>デバイス機能強化の概要<!-- 1404453 -->  
デバイス機能強化の概要に、登録済みデバイスが表示されるようになりましたが、Exchange ActiveSync で管理されるデバイスは除外されます。 Exchange ActiveSync デバイスには、登録済みデバイスと同じ管理オプションがありません。 Azure Portal の Intune で、登録済みデバイスの数とプラットフォーム別登録済みデバイスの数を表示するには、 **[デバイス]** 、 **[概要]** の順に進みます。

### <a name="improvements-to-device-inventory-collected-by-intune"></a>Intune で収集されるデバイス インベントリの機能強化
<!-- 961134, 1104426, 1281327, 1333543 -->
今回のリリースでは、ユーザーが管理するデバイスで収集されるインベントリ情報が次のように改善されました。
 
- Android devices デバイスの場合、各デバイスの最新パッチ レベルを示す列をデバイス インベントリに追加できるようになりました。 デバイスの一覧に **[セキュリティ パッチ レベル]** 列を追加し、これを表示します。
- デバイス ビューにフィルターを適用するとき、登録日付でデバイスを絞り込めるようになりました。 たとえば、指定した日付の後に登録されたデバイスのみを表示できます。
- **[Last Check-in Date]\(最終チェックイン日付\)** 項目で使用されるフィルターを改善しました。
- デバイスの一覧で、会社所有デバイスの電話番号を表示できるようになりました。
さらに、フィルター ウィンドウを利用し、電話番号でデバイスを検索できます。

デバイス インベントリの詳細については、「[Intune デバイス インベントリを表示する方法](../remote-actions/device-inventory.md)」を参照してください。

### <a name="conditional-access-support-for-macos-devices"></a>macOS デバイスの条件付きアクセスのサポート 
<!-- 720172 -->
Mac デバイスを Intune に登録し、そのデバイス コンプライアンス ポリシーに準拠することを求める条件付きアクセス ポリシーを設定できるようになりました。 たとえば、ユーザーは macOS 用の Intune ポータル サイト アプリをダウンロードして、Mac デバイスを Intune に登録します。 Intune は、暗証番号 (PIN)、暗号化、OS バージョン、およびシステムの整合性などの要件にその Mac デバイスが準拠しているかどうかを評価します。

- [macOS デバイスの条件付きアクセスのサポート](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)の詳細をご覧ください。

### <a name="company-portal-app-for-macos-is-in-public-preview---1484796---"></a>macOS 用ポータル サイト アプリはパブリック レビュー中です<!---1484796--->
macOS 用ポータル サイト アプリが Enterprise Mobility + Security の条件付きアクセス向けパブリック レビューの一部として利用可能になりました。 このリリースでは macOS 10.11 以降をサポートしています。 [https://aka.ms/macOScompanyportal](https://aka.ms/macOScompanyportal) で入手します。 


### <a name="new-device-restriction-settings-for-windows-10"></a>Windows 10 の新しいデバイスの制限設定    
<!--1063965, 1308850  -->
このリリースでは、次のカテゴリに [Windows 10 デバイス制限プロファイル](/intune/device-restrictions-windows-10)の新しい設定が追加されました。

- Windows Defender SmartScreen
- アプリ ストア

### <a name="updates-to-the-windows-10-endpoint-protection-device-profile-for-bitlocker-settings"></a>Windows 10 エンドポイント保護デバイス プロファイルの BitLocker 設定の更新
<!--1459533 -->    
今回のリリースでは、Windows 10 エンドポイント保護デバイス プロファイルにおける BitLocker 設定の動作が次のように改善されました。
 
- **[BitLocker OS ドライブの設定]** の **[互換性のない TPM チップでの BitLocker]** 設定で **[ブロック]** を選択すると、以前は、BitLocker が実際には許可されていました。 ブロックを選択すると BitLocker がブロックされるように修正されました。
- **[BitLocker OS ドライブの設定]** の **[証明書ベースのデータ回復エージェント]** 設定で、証明書ベースのデータ回復エージェントを明示的にブロックできるようになりました。 ただし、既定では、エージェントが許可されます。
- **[BitLocker 固定データ ドライブの設定]** の **[データ回復エージェント]** 設定で、データ回復エージェントを明示的にブロックできるようになりました。
詳しくは、「[Microsoft Intune での Windows 10 以降用の Endpoint Protection 設定](../protect/endpoint-protection-windows-10.md)」をご覧ください。


### <a name="new-signed-in-experience-for-android-company-portal-users-and-app-protection-policy-users---621669---"></a>Android ポータル サイト ユーザーおよびアプリ保護ポリシー ユーザーに対する新しいサインイン エクスペリエンス<!-- 621669 -->
エンドユーザーは、Android デバイスを登録しなくても、Android ポータル サイト アプリを使用して、今すぐにアプリを閲覧したり、デバイスを管理したり、IT 連絡先情報を確認したりできます。 さらに、エンド ユーザーが既に Intune App Protection ポリシーによって保護されているアプリを使用し、Android ポータル サイトを起動している場合、エンド ユーザーがデバイスの登録を要求されることはありません。

### <a name="new-setting-in-the-android-company-portal-app-to-toggle-battery-optimization--1405990--"></a>Android ポータル サイト アプリのバッテリの最適化を切り替える新しい設定<!--1405990-->
Android ポータル サイト アプリの **[設定]** ページには、ポータル サイトと Microsoft Authenticator アプリのバッテリ最適化をユーザーが簡単にオフにできる新しい設定があります。 この設定で表示されるアプリ名は、どのアプリが職場アカウントを管理しているかによって異なります。 電子メールとデータを同期する職場アプリのパフォーマンスの向上には、バッテリの最適化をオフにすることをお勧めします。 

### <a name="multi-identity-support-for-onenote-for-ios--------1234281---"></a>OneNote for iOS の複数 ID のサポート     <!-- 1234281 -->
エンド ユーザーは Microsoft OneNote for iOS で複数のアカウントを利用できるようになりました (職場用と個人用)。 アプリ保護ポリシーを、個人のノートブックに適用することなく、職場のノートブックの企業データに適用できます。 たとえば、職場のノートブックでは情報を検索できるが、職場のノートブックから個人のノートブックに企業データをコピーして貼り付ける行為は禁止するポリシーを適用できます。
 
- Intune で [アプリ保護と複数の ID](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) をサポートするアプリについての詳細を参照してください。

### <a name="new-settings-to-allow-and-block-apps-on-samsung-knox-standard-devices"></a>Samsung KNOX Standard デバイスでアプリを許可またはブロックするための新しい設定
<!-- 1305423 822899-->  
このリリースでは、次のアプリ一覧を指定できる[デバイスの制限設定](../configuration/device-restrictions-android.md)が新規に追加されています。
 
- ユーザーがインストールを許可されているアプリ
- ユーザーが実行をブロックされているアプリ
- デバイスのユーザーに非表示となっているアプリ
 
アプリは、URL、パッケージ名、管理対象のアプリ一覧から指定できます。

### <a name="new-azure-ad-app-based-conditional-access-policy-ui-link-from-intune"></a>Intune からリンクされる新しい Azure AD のアプリ ベースの条件付きアクセス ポリシーの UI
<!-- 1016201 -->
IT 管理者が、Azure AD のワークロードで新しい条件付きアクセス ポリシーの UI を使用して、アプリ ベースの条件付きポリシーを設定できるようになりました。 Azure portal の [Intune App Protection] セクションにあるアプリ ベースの条件付きアクセス ポリシーは当面そのまま残り、サイド バイ サイドで強制されます。 また、Intune ワークロードから新しい条件付きアクセス ポリシー UI への便利なリンクもあります。

- [Azure AD のアプリ ベースの条件付きアクセス](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-technical-reference)の詳細をご覧ください。

<!-- ########################## -->
## <a name="july-2017"></a>2017 年 7 月

### <a name="restrict-android-and-ios-device-enrollment-restriction-by-os-version-----1333256--1245463----"></a>Android および iOS デバイスの OS のバージョンによる登録制限 <!--- 1333256,  1245463 --->
オペレーティング システムのバージョン番号によって iOS と Android の登録を制限する機能が追加されました。 **[デバイスの種類の制限]** で、IT 管理者は、プラットフォーム構成を設定して、オペレーティング システムのバージョン番号の最小値から最大値までの間に登録を制限できるようになりました。 Android オペレーティング システムのバージョンは、Major.Minor.Build.Rev の形式で指定する必要があります (Minor、Build、Rev は任意)。 iOS のバージョンは、Major.Minor.Build の形式で指定する必要があります (Minor と Build は任意)。 [デバイス登録の制限](../enrollment/enrollment-restrictions-set.md)の詳細については、こちらを参照してください。

>[!NOTE]
>Apple の登録プログラムまたは Apple Configurator では、登録は制限されません。

### <a name="restrict-android-ios-and-macos-device-personally-owned-device-enrollment-----1333272--1333275-1245709----"></a>個人所有の Android、iOS、および macOS デバイスの登録を制限する <!--- 1333272,  1333275, 1245709 --->
Intune では、会社デバイスの IMEI 番号のホワイトリストを作成して、個人用デバイスの登録を制限できます。 Intune では、デバイス シリアル番号を使って、この機能を iOS、Android、macOS に拡張しています。 Intune にデバイスのシリアル番号をアップロードし、それを企業所有として事前に宣言できます。 登録の制限を使用すると、個人所有のデバイス (BYOD) をブロックして、企業所有のデバイスのみの登録を許可することができます。 [デバイス登録の制限](../enrollment/enrollment-restrictions-set.md)の詳細については、こちらを参照してください。

シリアル番号をインポートするには、 **[デバイスの登録]**  >  **[業務用デバイスの ID]** に進み、 **[追加]** をクリックし、(ヘッダーはない、シリアル番号と IMEI 番号など詳細情報がある 2 つの列の) CSV ファイルをアップロードします。 個人所有のデバイスを制限するには、 **[デバイスの登録]**  >  **[登録制限]** に移動します。 **[デバイスの種類の制限]** から **[既定]** を選択し、 **[プラットフォーム構成]** を選択します。 個人所有の iOS、Android、および macOS デバイスを **[許可]** または **[ブロック]** できます。


### <a name="new-device-action-to-force-devices-to-sync-with-intune---711369---"></a>デバイスを Intune と強制同期する新しいデバイス アクション<!-- 711369 -->
このリリースでは、選択したデバイスの Intune への即座のチェックインを強制する新しいデバイス アクションが追加されています。 チェックインしたデバイスには、それに対して保留中のアクションまたはポリシーが即座に割り当てられます。  このアクションにより、次のスケジュールされたチェックインを待つことなく、割り当てられたポリシーの検証およびトラブルシューティングを即座に実行できるようになります。
詳細については、「[同期デバイス](../remote-actions/device-sync.md)」を参照してください。

### <a name="force-supervised-ios-devices-to-automatically-install-the-latest-available-software-update---777100---"></a>監督下の iOS デバイスに利用可能な最新のソフトウェア更新プログラムを強制的に自動インストールする<!-- 777100 -->
ソフトウェアの更新プログラム ワークスペースに用意された新しいポリシーを使用すると、監督下の iOS デバイスに利用可能な最新のソフトウェア更新プログラムを強制的に自動インストールできます。 詳細については、「[Configure iOS update policies](/intune/software-updates-ios)」 (iOS 更新プログラム ポリシーの構成) を参照してください。

### <a name="check-point-sandblast-mobile---new-mobile-threat-defense-partner----954651-1172027---"></a>チェック ポイント SandBlast Mobile - 新しい Mobile Threat Defense パートナー <!-- 954651, 1172027 -->
Microsoft Intune に統合された Mobile Threat Defense ソリューションであるチェックポイントの SandBlast Mobile によって実行されるリスク評価に基づき、条件付きアクセスを利用し、モバイル デバイスから会社のリソースへのアクセスを制御できます。

#### <a name="how-integration-with-intune-works"></a>Intune との統合のしくみ
リスクは、チェックポイントの SandBlast Mobile を実行するデバイスから収集される製品利用統計情報に基づいて評価されます。 Intune のデバイス コンプライアンス ポリシーにより有効になったチェックポイントの SandBlast Mobile のリスク評価に基づいて、EMS 条件付きアクセスのポリシーを構成できます。 検出された脅威に基づき、非準拠デバイスの企業リソースへのアクセスを許可またはブロックすることができます。


### <a name="deploy-an-app-as-available-in-the-microsoft-store-for-business---748101---"></a>ビジネス向け Microsoft ストアで利用可能なアプリを展開する<!-- 748101 -->
このリリースでは、管理者はビジネス向け Microsoft ストアを使用可能として割り当てることができるようになりました。 使用可能として設定すると、エンドユーザーは、Microsoft ストアにリダイレクトされることなく、ポータル サイトのアプリまたは Web サイトからアプリをインストールできます。

### <a name="ui-updates-to-the-company-portal-website--1313244-part-1--"></a>ポータル Web サイトの UI の更新<!--1313244 part 1-->
エンド ユーザー エクスペリエンスを向上させるために、[ポータル Web サイト](https://portal.manage.microsoft.com)の UI をいくつか更新しました。

- __アプリ タイルの機能強化__: アプリ アイコンが、アイコンの主調色に基づいて自動生成される背景で表示されるようになります (アイコンを検出できた場合)。 適用できる場合は、アプリ タイルで以前表示されていた灰色の枠線が、この背景に代わります。

    ポータル サイト Web サイトでは、今後のリリースで可能なときには常に大きなアイコンで表示されます。 IT 管理者は、最小サイズが 120 x 120 ピクセルの高解像度アイコンを使用して、アプリを公開することをお勧めします。 

- __ナビゲーションの変更__: ナビゲーション バーの項目が、左上のハンバーガー メニューに移動されています。 カテゴリのページは削除されています。 ユーザーは参照中にカテゴリでコンテンツをフィルター処理できるようになりました。

- __おすすめアプリの更新__: 機能を選択したアプリをユーザーが参照できる専用ページをサイトに追加し、ホームページのおすすめセクションでいくつかの UI の修正を行いました。

### <a name="ibooks-support-for-the-company-portal-website--1231841--"></a>ポータル サイト Web サイトでの iBooks のサポート<!--1231841-->
ポータル サイトの Web サイトにユーザーが iBooks を参照してダウンロードできる専用ページを追加しました。 


### <a name="additional-help-desk-troubleshooting-details-----applies-to-1263399-1326964-1341642----"></a>ヘルプ デスク トラブルシューティングの追加詳細<!---  Applies to 1263399, 1326964, 1341642 --->
Intune では、トラブルシューティング ディスプレイを更新し、管理者やヘルプ デスク スタッフ向けの情報を追加しました。 グループのメンバーシップに基づいてユーザーの全割り当てをまとめた**割り当て**テーブルが表示されます。 この一覧の内容:
- モバイル アプリ
- コンプライアンス ポリシー
- 構成プロファイル

また、**デバイス** テーブルに **[Azure AD 結合の種類]** 列と **[Azure AD 準拠]** 列が追加されました。 詳細については「[問題のトラブルシューティングの方法](../help-desk-operators.md)」を参照してください。



### <a name="intune-data-warehouse-public-preview"></a>Intune データ ウェアハウス (パブリック プレビュー)
Intune データ ウェアハウスは、データを毎日サンプリングし、テナントの履歴ビューを提供します。 多くの分析ツールと互換性がある OData リンクである Power BI ファイル (PBIX) を使用するか、REST API と対話して、データにアクセスできます。 詳細については、「[Intune データ ウェアハウスを使用する](../developer/reports-nav-create-intune-reports.md)」を参照してください。


### <a name="light-and-dark-modes-available-for-the-company-portal-app-for-windows-10---676547---"></a>Windows 10 のポータル サイト アプリで利用可能なライト モードとダーク モード<!---676547--->
エンドユーザーは Windows 10 のポータル サイト アプリのカラー モードをカスタマイズできるようになります。 ユーザーはポータル サイト アプリの [設定] セクションでこの変更をできるようになります。 変更はユーザーがアプリを再起動した後に反映されます。 Windows 10 のバージョン 1607 以降では、アプリ モードは既定でシステム設定になります。 Windows 10 のバージョン 1511 以前では、アプリ モードは既定でライト モードになります。

### <a name="enable-end-users-to-tag-their-device-group-in-the-company-portal-app-for-windows-10---807046--"></a>エンドユーザーは Windows 10 用のポータル サイト アプリでデバイス グループをタグ付けできる<!---807046-->
エンドユーザーは Windows 10 のポータル サイト アプリから直接タグ付けすることにより、デバイスの所属グループを選択できるようになりました。

<!-- ########################## -->
## <a name="june-2017"></a>2017 年 6 月

### <a name="new-role-based-administration-access-for-intune-admins-----1099990---"></a>Intune 管理者のための新しいロール ベース管理アクセス  <!-- 1099990 -->  
Azure AD の条件付きアクセス ポリシーを表示、作成、変更、削除できる新しい条件付きアクセス管理者ロールが追加されます。 以前は、このアクセス許可を持つのは、グローバル管理者とセキュリティ管理者のみでした。 条件付きアクセス ポリシーにアクセスできるように、Intune 管理者にこのロールのアクセス許可が付与されます。


### <a name="tag-corporate-owned-devices-with-serial-number---1215070---"></a>会社所有のデバイスにシリアル番号をタグ付けする<!-- 1215070 -->  
Intune では、iOS、macOS、Android のシリアル番号を会社デバイスの識別子としてアップロードできるようになりました。 この新機能では、シリアル番号を使用して個人用デバイスの登録をブロックすることはできません。登録中はシリアル番号が検証されないためです。 シリアル番号を使用して個人用デバイスをブロックする機能は、近いうちにリリースされる予定です。


### <a name="new-remote-actions-for-ios-devices---854689---"></a>iOS デバイスの新しいリモート操作<!-- 854689 -->
このリリースでは Apple Classroom アプリを管理する新しいリモート デバイス アクションを共有の iPad デバイスに追加しました。

- [[現在のユーザーのログアウト]](../remote-actions/device-logout-user.md) - 選択した iOS デバイスの現在のユーザーをサインアウトさせます。
- [[ユーザーの削除]](../remote-actions/device-remove-user.md) - iOS デバイスのローカル キャッシュから選択したユーザーを削除します。


### <a name="support-for-shared-ipads-with-the-ios-classroom-app---1044681---"></a>iOS Classroom アプリによる共有 iPad のサポート<!-- 1044681 -->
このリリースでは、iOS Classroom アプリの管理サポートが拡張され、自分で管理している Apple ID を使って共有 iPad にログインする生徒を含めることができるようになっています。


### <a name="changes-to-intune-built-in-apps---1332306---"></a>Intune の組み込みアプリの変更<!-- 1332306 -->
以前は、Intune に簡単に割り当てができる組み込みのアプリが多数含まれていました。 お客様からのフィードバックに基づき、この一覧を削除しました。組み込みのアプリは今後表示されません。
ただし、組み込みのすべてのアプリが既に割り当てられている場合、そのアプリはアプリの一覧に引き続き表示されます。 これらのアプリの割り当ては必要に応じて続行することができます。
今後のリリースでは、Azure Portal から組み込みのアプリをより簡単に選択して割り当てる方法を追加する予定です。

### <a name="easier-installation-of-office-365-apps----1121362----"></a>Office 365 アプリをより簡単にインストールする<!--- 1121362 --->
新しいタイプの **Office 365 ProPlus** アプリでは、最新バージョンの Windows 10 を実行する管理対象のデバイスに、Office 365 ProPlus 2016 アプリを簡単に割り当てることができます。 また、ライセンスを所有している場合、Microsoft Project や Microsoft Visio をインストールすることもできます。 必要なアプリはバンドルされ、Intune コンソールのアプリ一覧に 1 つのアプリとして表示されます。
詳細については、「[Windows 10 用の Office 365 アプリを追加する方法](../apps/apps-add-office365.md)」を参照してください。


### <a name="support-for-offline-apps-from-the-microsoft-store-for-business----777044----"></a>ビジネス向け Microsoft ストアから入手したオフライン アプリのサポート<!--- 777044 --->
ビジネス向け Microsoft ストアから購入したオフライン アプリが Azure Portal に同期されます。 その後、これらのアプリをデバイス グループまたはユーザー グループに展開できます。 オフライン アプリはストアではなく Intune でインストールします。

### <a name="microsoft-teams-is-now-part-of-the-app-based-ca-list-of-approved-apps-----1257019---"></a>Microsoft Teams が承認済みアプリのアプリ ベース CA 一覧の一部になった  <!-- 1257019 -->
iOS と Android 用の Microsoft Teams アプリが、Exchange と SharePoint Online のアプリ ベースの条件付きアクセス ポリシー向けの承認済みアプリの一部になりました。 Azure portal の [Intune App Protection] ブレードで、現在アプリ ベースの条件付きアクセスを使っているすべてのテナントにアプリを構成できます。

### <a name="managed-browser-and-app-proxy-integration---1287310---"></a>管理対象ブラウザーとアプリ プロキシの統合<!-- 1287310 -->
Intune Managed Browser は、ユーザーがリモートで作業している場合でも内部の Web サイトにアクセスできるように、Azure AD アプリケーション プロキシ サービスに統合できるようになりました。 ブラウザーのユーザーが、通常と同じようにサイトの URL を入力すると、Managed Browser がアプリケーション プロキシの Web ゲートウェイを介して要求をルーティングします。 詳細については、「[Managed Browser ポリシーを使用したインターネット アクセスの管理](../apps/app-configuration-managed-browser.md)」を参照してください。

### <a name="new-app-configuration-settings-for-the-intune-managed-browser---682951---"></a>Intune Managed Browser の新しいアプリ構成設定<!-- 682951 -->
このリリースでは、iOS および Android 用の Intune Managed Browser アプリに構成が追加されました。 アプリ構成ポリシーを使って、ブラウザーの既定のホーム ページとブックマークを構成できます。
詳しくは、「[Managed Browser ポリシーを使用したインターネット アクセスの管理](../apps/app-configuration-managed-browser.md)」をご覧ください。

### <a name="bitlocker-settings-for-windows-10----951707---"></a>Windows 10 用の BitLocker の設定 <!-- 951707 -->
新しい Intune デバイス プロファイルを使って、Windows 10 デバイス用の BitLocker の設定を構成できます。 たとえば、デバイスの暗号化を要求でき、BitLocker が有効になっているときに適用される設定をさらに構成することもできます。
詳しくは、「[Microsoft Intune での Windows 10 以降用の Endpoint Protection 設定](../protect/endpoint-protection-windows-10.md)」をご覧ください。

### <a name="new-settings-for-windows-10-device-restriction-profile----978527--978550-978569-1050031-1058611-----"></a>Windows 10 デバイス制限プロファイルの新しい設定<!--- 978527,  978550, 978569, 1050031, 1058611,  --->
このリリースでは、次のカテゴリに Windows 10 デバイス制限プロファイルの新しい設定が追加されました。

- Windows Defender
- 携帯ネットワークと接続性
- ロック画面
- プライバシー
- 検索
- Windows スポットライト
- Microsoft Edge ブラウザー

Windows 10 の設定について詳しくは、「[Microsoft Intune での Windows 10 以降のデバイスの制限設定](../configuration/device-restrictions-windows-10.md)」をご覧ください。


### <a name="company-portal-app-for-android-now-has-a-new-end-user-experience-for-app-protection-policies--1305217--"></a>Android 用ポータル サイト アプリのアプリ保護ポリシーの新しいエンド ユーザー エクスペリエンス<!--1305217-->
ユーザーのフィードバックに基づいて、Android 用ポータル サイト アプリに **[会社のコンテンツにアクセスする]** ボタンが表示されるようになりました。 目的は、エンド ユーザーがアプリの保護ポリシーをサポートするアプリ、Intune モバイル アプリケーション管理の機能にのみアクセスする必要があるときに、不要な登録プロセスを経由せずに済むようにすることです。 これらの変更については、「[アプリ UI の新機能](whats-new-app-ui.md)」ページをご覧ください。

### <a name="new-menu-action-to-easily-remove-company-portal--1164569--"></a>ポータル サイトを簡単に削除できるアクション メニューの追加<!--1164569-->
Android 用ポータル サイト アプリでは、ユーザーからのフィードバックに基づき、デバイスからポータル サイトの削除を開始できる新しいアクション メニューが追加されました。 この操作は、ユーザーがデバイスからアプリを削除できるように、Intune の管理からデバイスを削除します。 これらの変更については、[Android エンド ユーザー向けドキュメント](/intune-user-help/unenroll-your-device-from-intune-android)の[アプリ UI の新機能](whats-new-app-ui.md)に関するページで確認できます。

### <a name="improvements-to-app-syncing-with-windows-10-creators-update--676505--"></a>Windows 10 Creators Update とアプリを同期する機能の強化<!--676505-->
Windows 10 用ポータル サイト アプリでは、Windows 10 Creators Update (バージョン 1703) がインストールされているデバイスのアプリ インストール要求の同期が自動的に開始されるようになりました。 "同期保留中" 状態中、アプリ インストールが止まる問題を減らします。 また、ユーザーは、アプリ内からの同期を手動で開始することができます。 これらの変更については、「[アプリ UI の新機能](whats-new-app-ui.md)」ページをご覧ください。

### <a name="new-guided-experience-for-windows-10-company-portal---1058938---"></a>Windows 10 ポータル サイトの新しいガイド機能<!---1058938--->
Windows 10 用のポータル サイト アプリで、特定または登録されていないデバイス向けのガイド付き Intune チュートリアルを利用できるようになります。 ユーザーは新たな段階的手順に従って、Azure Active Directory (条件付きアクセス機能のために必要) と MDM (デバイス管理機能のために必要) に登録できます。 このガイドには、ポータル サイトのホーム ページからアクセスできます。 ユーザーは、これらの登録を完了していない場合でも引き続きアプリを使用できますが、機能が制限されます。

この更新は、Windows 10 Anniversary Update (ビルド 1607) 以降を実行しているデバイスのみで表示されます。 これらの変更については、「[アプリ UI の新機能](whats-new-app-ui.md)」ページをご覧ください。


### <a name="microsoft-intune-and-conditional-access-admin-consoles-are-generally-available"></a>Microsoft Intune 管理コンソールと条件付きアクセス管理コンソールの一般提供開始
Azure Portal の新しい Intune 管理コンソールと、条件付きアクセス管理コンソールの一般提供開始が発表されました。 Azure Portal で Intune を利用することで、Intune MAM および MDM のすべての機能を統合された 1 つの管理者エクスペリエンスで管理し、Azure AD のグループとターゲットを利用できるようになりました。 Azure の条件付きアクセスにより、Azure AD と Intune の豊富な機能が一元化されたコンソールに統合されます。 また管理者エクスペリエンスから Azure プラットフォームに移動して、最新のブラウザーを使用できます。

Intune は、 **[プレビュー]** ラベルが外れた状態で Azure Portal (portal.azure.com) に表示されるようになりました。

メッセージ センターの一連のメッセージのうち、グループを移行できるようにお客様の対応をお願いするメッセージを受信された場合を除き、現時点で既存のお客様にしていただくことはありません。 こちらのバグにより、移行に時間がかかることをお知らせする通知がメッセージ センターから送信されている場合もあります。 Microsoft では、影響を受けたユーザーを移行する作業に引き続き取り組んでまいります。

### <a name="improvements-to-the-app-tiles-in-the-company-portal-app-for-ios"></a>iOS 用ポータル サイト アプリのアプリ タイルを改善
ポータル サイトに設定したブランド カラーが反映されるよう、ホーム ページのアプリ タイルのデザインを一新しました。 詳細については、[アプリ UI の新機能](whats-new-app-ui.md)に関するページをご覧ください。

### <a name="account-picker-now-available-for-the-company-portal-app-for-ios"></a>iOS 用ポータル サイト アプリでアカウント選択の提供を開始
iOS デバイスのユーザーが、職場または学校アカウントを使用して別の Microsoft アプリにサインインしているときに、ポータル サイトにサインインしようとすると、新しいアカウントの選択が表示される場合があります。 詳細については、[アプリ UI の新機能](whats-new-app-ui.md)に関するページをご覧ください。

<!-- ########################## -->
## <a name="may-2017"></a>2017 年 5 月

### <a name="change-your-mdm-authority-without-unenrolling-managed-devices--1103950--"></a>マネージド デバイスの登録を解除せず、MDM 機関を変更する<!--1103950-->
Microsoft サポートに問い合わせずに、また、既存のマネージド デバイスの登録解除と再登録を行わずに MDM 機関を変更できるようになりました。 Configuration Manager コンソールで、[Configuration Manager に設定]\(ハイブリッド) から [Microsoft Intune]\(スタンドアロン) に、またはその逆に MDM 機関を変更できます。


### <a name="improved-notification-for-samsung-knox-startup-pins--1087143--"></a>Samsung KNOX スタートアップ PIN の通知機能の強化<!--1087143-->
暗号化に対応するために、エンド ユーザーが Samsung KNOX デバイスにスタートアップ PIN を設定する必要がある場合、エンド ユーザーに表示される通知をタップすると、設定アプリ内の設定場所に移動します。  以前は、エンド ユーザーは通知からパスワード変更画面に進むことができました。

### <a name="device-enrollment"></a>デバイスの登録

#### <a name="apple-school-manager-asm-support-with-shared-ipad---748864-770395--"></a>共有 iPad での Apple School Manager (ASM) のサポート<!-- 748864, 770395-->

Intune では、Apple Device Enrollment Program の代わりに Apple School Manager (ASM) を使用できるようになりました。すぐに iOS デバイスを登録できます。 共有 iPad で Classroom アプリを使用するには ASM オンボードが必要です。これは、Microsoft School Data Sync (SDS) 経由で ASM から Azure Active Directory へのデータ同期を有効にする際にも必要です。 詳細については、「[Enable iOS device enrollment with Apple School Manager (Apple School Manager での iOS デバイス登録の有効化)](../enrollment/apple-school-manager-set-up-ios.md)」をご覧ください。

> [!NOTE]
> 共有 iPad で Classroom アプリを使用できるように構成するには、Azure に iOS 向けの Education の構成が必要ですが、現時点では提供されていません。  この機能は、近日中に追加される予定です。

### <a name="device-management"></a>デバイス管理

#### <a name="provide-remote-assistance-to-android-devices-using-teamviewer---675418---"></a>TeamViewer を利用して Android デバイスにリモート アシスタンスを提供<!-- 675418 -->

Intune では、別売りの [TeamViewer](https://www.teamviewer.com) ソフトウェアを利用して、Android デバイスを使用するユーザーにリモート アシスタンスを提供できるようになりました。 詳細については、「[Provide remote assistance for Intune managed Android devices (Intune 管理対象の Android デバイスにリモート アシスタンスを提供)](../remote-actions/teamviewer-support.md)」をご覧ください。

### <a name="app-management"></a>アプリ管理

#### <a name="new-app-protection-policies-conditions-for-mam---679864---"></a>MAM の新しいアプリ保護ポリシー条件<!-- 679864 -->

登録ユーザーなしで、次のポリシーを強制する MAM の要件を設定できるようになりました。

- アプリケーションの最小バージョン
- オペレーティング システムの最小バージョン
- 対象アプリケーションの最小 Intune APP SDK バージョン (iOS のみ)

この機能は、Android と iOS の両方で使うことができます。 Intune は、OS プラットフォーム バージョン、アプリケーション バージョン、Intune APP SDK の最小バージョン強制に対応しています。 iOS の場合、SDK が統合されているアプリケーションでも SDK レベルで最小バージョン強制を設定できます。 アプリ保護ポリシーの最小要件が上述の 3 つの異なるレベルで満たされていない場合、ユーザーは対象アプリケーションにアクセスできません。 この時点で、ユーザーはアカウントを削除するか (複数 ID アプリケーションの場合)、アプリケーションを閉じるか、OS またはアプリケーションのバージョンを更新できます。

また、OS またはアプリケーションのアップグレードを推奨するブロック不可の通知を表示するように追加設定することもできます。 この通知は閉じて、アプリケーションを普段どおり使用できます。

詳細については、「[iOS アプリ保護ポリシー設定](../apps/app-protection-policy-settings-ios.md)」と「[Android アプリ保護ポリシー設定](../apps/app-protection-policy-settings-android.md)」をご覧ください。

#### <a name="configure-app-configurations-for-android-for-work---621621---"></a>Android for Work 用のアプリ構成の設定<!-- 621621 -->
ストアの一部の Android アプリは管理対象の構成オプションをサポートしているため、IT 管理者は作業プロファイルでアプリの実行方法を制御できます。 Intune では、Azure Portal からアプリがサポートする構成を表示し、構成デザイナーまたは JSON エディターを使用してこれらの構成を設定できるようになりました。 詳細については、[Android for Work 用のアプリ構成の使用](../apps/app-configuration-policies-use-android.md)に関するページをご覧ください。

#### <a name="new-app-configuration-capability-for-mam-without-enrollment---677969---"></a>登録なしで利用できる MAM の新しいアプリ構成機能<!-- 677969 -->
登録チャネルがなくても MAM からアプリ構成ポリシーを作成できるようになりました。 これは、モバイル デバイス管理 (MDM) のアプリ構成で使用できるアプリ構成ポリシーと同等の機能です。 登録せずに MAM を使用してアプリを構成する例については、「[Manage Internet access using Managed browser policies with Microsoft Intune (Microsoft Intune と Managed Browser のポリシーを使用したインターネット アクセスの管理)](../apps/app-configuration-managed-browser.md)」をご覧ください。

#### <a name="configure-allowed-and-blocked-url-lists-for-the-managed-browser---682960---"></a>Managed Browser で許可される URL とブロックされる URL 一覧の構成<!-- 682960 -->
Azure Portal のアプリ構成設定を使用して、Intune Managed Browser で許可またはブロックされるドメインおよび URL の一覧を構成できるようになりました。 これらの設定は、マネージド デバイスで使用されているか、アンマネージド デバイスで使用されているかに関係なく構成できます。 詳細については、「[Manage Internet access using Managed browser policies with Microsoft Intune (Microsoft Intune と Managed Browser のポリシーを使用したインターネット アクセスの管理)](../apps/app-configuration-managed-browser.md)」をご覧ください。

#### <a name="app-protection-policy-helpdesk-view---1069473---"></a>アプリ保護ポリシー ヘルプデスクのビュー<!-- 1069473 -->
IT ヘルプデスクのユーザーは、[トラブルシューティング] ブレードで、ユーザー ライセンスの状態と、ユーザーに割り当てられているアプリのアプリ保護ポリシーの状態を確認できるようになりました。 詳細については、[トラブルシューティング](./help-desk-operators.md)に関するページをご覧ください。

### <a name="device-configuration"></a>デバイスの構成

#### <a name="control-website-visits-on-ios-devices---723832---"></a>iOS デバイスの Web サイト アクセスの制御<!-- 723832 -->
iOS デバイスのユーザーがアクセスできる Web サイトを次の 2 つの方法を使って制御できるようになりました。

- Apple の組み込み Web コンテンツ フィルターを使って、許可される URL またはブロックされる URL を追加します。

- Safari ブラウザーによるアクセスを許可する Web サイトを指定します。 指定した各サイトについて、Safari にブックマークが作成されます。

詳細については、「[Web content filter settings for iOS devices (iOS デバイス用の Web コンテンツ フィルター設定)](../configuration/ios-device-features-settings.md#web-content-filter)」をご覧ください。

#### <a name="preconfigure-device-permissions-for-android-for-work-apps---621614---"></a>Android for Work アプリのデバイス アクセス許可の事前構成<!-- 621614 -->
Android for Work デバイスの作業プロファイルに展開したアプリの場合、個々のアプリのアクセス許可状態を構成できるようになりました。  既定では、場所やデバイス カメラへのアクセスなど、デバイスのアクセス許可を必要とする Android アプリはアクセス許可の承諾または拒否をユーザーに求めます。  たとえば、アプリでデバイスのマイクが使用される場合、そのマイクを使用するアクセス許可をアプリに与えるようにエンド ユーザーに求められます。 この機能を利用すると、エンド ユーザーの代わりにアクセス許可を定義できます。  アクセス許可は、a) ユーザーに通知することなく自動的に拒否する、b) ユーザーに通知することなく自動的に承諾する、c) 承諾または拒否をユーザーに求めるのいずれかに構成できます。 詳細については、「[Microsoft Intune での Android for Work デバイスの制限設定](../configuration/device-restrictions-android-for-work.md)」をご覧ください。

#### <a name="define-app-specific-pin-for-android-for-work-devices---728976-1102534---"></a>Android for Work デバイスのアプリ固有 PIN を定義する<!-- 728976, 1102534 -->
管理者は、Android for Work デバイスとして管理されている Android 7.0 以上のデバイスの作業プロファイルで、作業プロファイルのアプリにのみ適用されるパスコード ポリシーを定義できます。  次のオプションがあります。

- デバイス全体のパスコード ポリシーだけを定義する - これは、デバイス全体のロックを解除するためにユーザーが使用しなければならないパスコードです。
- 作業プロファイルのパスコード ポリシーだけを定義する - 作業プロファイルのアプリを起動するたびに、ユーザーにパスコードの入力が求められます。
- デバイスと作業プロファイル ポリシーの両方を定義する - IT 管理者はデバイスのパスコード ポリシーと作業プロファイルのパスコード ポリシーをいずれも異なる強度で定義できます。たとえば、デバイスのロック解除に 4 桁の PIN を要求し、作業アプリの起動に 6 桁の PIN を要求します。

詳細については、「[Microsoft Intune での Android for Work デバイスの制限設定](../configuration/device-restrictions-android-for-work.md)」をご覧ください。

> [!NOTE]
> この機能は Android 7.0 以降でのみ利用できます。  既定では、エンド ユーザーは別々に定義された 2 つの PIN を利用できます。あるいは、定義された 2 つの PIN のうちの強いほうを選択できます。

#### <a name="new-settings-for-windows-10-devices---978585---"></a>Windows 10 デバイスの新しい設定<!-- 978585 -->
Microsoft は、無線ディスプレイ、デバイス検出、タスク切り替え、SIM カード エラー メッセージなどの機能を制御する新しい [Windows デバイス制限設定](../configuration/device-restrictions-windows-10.md)を追加しています。

#### <a name="updates-to-certificate-configuration---918991-and-823198---"></a>証明書の構成の更新<!-- 918991 and 823198 -->
SCEP 証明書プロファイルを作成するときに、<strong>[サブジェクト名の形式]</strong>で、<strong>[カスタム]</strong> オプションを iOS、Android、および Windows デバイスでご利用いただけます。 今回の更新までは、<strong>[カスタム]</strong> フィールドを使用できるのは iOS デバイスだけでした。 詳細については、「[SCEP 証明書プロファイルを作成する](../protect/certificates-profile-scep.md)」をご覧ください。

PKCS 証明書プロファイルを作成するときに、 **[サブジェクトの別名]** で、 **[Custom Azure AD attribute]\(Azure AD のカスタム属性\)** をご使用いただけます。 **[Custom Azure AD attribute]\(Azure AD のカスタム属性\)** を選択すると、 **[部門]** オプションが使用できます。 詳細については、「[PKCS 証明書プロファイルを作成する](../protect/certficates-pfx-configure.md#create-a-pkcs-certificate-profile)」をご覧ください。

#### <a name="configure-multiple-apps-that-can-run-when-an-android-device-is-in-kiosk-mode---662059---"></a>Android デバイスがキオスク モードのときに実行できる複数アプリの構成<!-- 662059 -->
これまでは、Android デバイスがキオスク モードのときに実行できるアプリは 1 つしか設定できませんでした。 アプリ ID やストアの URL を使用するか、すでに管理している Android アプリを選択して、複数のアプリを設定できるようになりました。 詳細については、[キオスク モードの設定](../configuration/device-restrictions-android.md#kiosk)に関するページをご覧ください。

<!-- ########################## -->
## <a name="april-2017"></a>2017 年 4 月

### <a name="support-for-managing-the-apple-classroom-app"></a>Apple Classroom アプリの管理のサポート
iPad デバイスで iOS Classroom アプリを管理できるようになりました。 クラスと学生の正しいデータで教師の iPad に Classroom アプリをセットアップした後、アプリを使って制御できるように、クラスに登録されている学生の iPad を構成します。
詳しくは、「[Configure iOS education settings](education-settings-configure-ios.md)」 (iOS の教育設定を構成する) をご覧ください。

### <a name="support-for-managed-configuration-options-for-android-apps---621621---"></a>Android アプリ向けの管理対象構成オプションのサポート<!-- 621621 -->
管理対象構成オプションをサポートする Play ストアの Android アプリを、Intune で構成できるようになりました。  この機能は、アプリによってサポートされる構成値の一覧を表示できるようにし、値を構成できるガイド付きの使いやすい UI を提供します。

### <a name="new-android-policy-for-complex-pins---722069---"></a>複雑な暗証番号 (PIN) に対する新しい Android ポリシー<!-- 722069 -->
Android 5.0 以降を搭載しているデバイスの Android デバイス プロファイルに、数値複素数タイプの必須[パスワード](../configuration/device-restrictions-android.md#password)を設定できるようになりました。  反復する値や連続する値 (1111 や 1234 など) を含む暗証番号 (PIN) をデバイスのユーザーが作成しないようにするには、この設定を使います。

### <a name="additional-support-for-android-for-work-devices"></a>Android for Work デバイスの追加サポート
- **パスワードと仕事用プロファイルの設定を管理する**<!-- 612808 -->

  この新しい Android for Work デバイス制限ポリシーにより、管理対象の Android for Work デバイスで、パスワードと仕事用プロファイルの設定を管理できるようになりました。

- **仕事用プロファイルと個人プロファイル間でのデータ共有を許可する**<!-- 1045102 -->

この Android for Work デバイス制限プロファイルには、仕事用プロファイルと個人用プロファイルでのデータ共有の設定ができる新しいオプションが用意されました。

- **仕事用プロファイルと個人プロファイルの間でのコピーと貼り付けを制限する**<!-- 1046094 -->

  Android for Work デバイス用の新しいカスタム デバイス プロファイルでは、仕事用アプリと個人用アプリの間でのコピーと貼り付け操作を許可するかどうかを制限できます。

詳細については、[Android for Work 用のデバイスの制限](../configuration/device-restrictions-android-for-work.md)に関するページをご覧ください。

### <a name="assign-lob-apps-to-ios-and-android-devices---1057568---"></a>iOS デバイスと Android デバイスに LOB アプリを割り当てる<!-- 1057568 -->
[iOS](../apps/lob-apps-ios.md) 用 (.ipa ファイル) と [Android](../apps/lob-apps-android.md) 用 (.apk ファイル) の基幹業務 (LOB) アプリを、ユーザーまたはデバイスに割り当てることができるようになりました。


### <a name="new-device-policies-for-ios---723774-723815-723826-723830---"></a>iOS 用の新しいデバイス ポリシー<!-- 723774, 723815, 723826, 723830 -->
- **ホーム画面のアプリ** - [iOS デバイスのホーム画面](../configuration/ios-device-features-settings.md#home-screen-layout)に表示されるアプリを制御します。 このポリシーはホーム画面のレイアウトを変更しますが、アプリの展開は行いません。

- **AirPrint デバイスへの接続** - iOS デバイスのエンド ユーザーが接続できる [AirPrint デバイス](../configuration/ios-device-features-settings.md#airprint) (ネットワーク プリンター) を制御します。

- **AirPlay デバイスへの接続** - iOS デバイスのエンド ユーザーが接続できる [AirPlay デバイス](../configuration/ios-device-features-settings.md) (Apple TV など) を制御します。

- **ロック画面のカスタム メッセージ** - ユーザーの iOS デバイスのロック画面に表示されるカスタム メッセージを構成して、既定のメッセージと置き換えます。 詳しくは、「[iOS デバイスで紛失モードをアクティブ化する](../remote-actions/device-lost-mode.md)」を参照してください。

### <a name="restrict-push-notifications-for-ios-apps---723767---"></a>iOS アプリのプッシュ通知を制限する<!-- 723767 -->
Intune のデバイス制限プロファイルでは、iOS デバイスに対して次の[通知設定](../configuration/ios-device-features-settings.md#app-notifications)を構成できるようになりました。

- 指定したアプリの通知を完全に有効または無効にします。
- 指定したアプリの通知センターでの通知を有効または無効にします。
- アラートの種類を、**なし**、**バナー**、または**モーダル アラート**に指定します。
- このアプリに対してバッジを許可するかどうかを指定します。
- 通知サウンドを許可するかどうかを指定します。

### <a name="configure-ios-apps-to-run-in-single-app-mode-autonomously---737837---"></a>単一アプリ モードで自律的に実行するように iOS アプリを構成する<!-- 737837 -->
Intune のデバイス プロファイルを使って、[自律的シングル App モード](../configuration/device-restrictions-ios.md#autonomous-single-app-mode)で指定したアプリを実行するように iOS デバイスを構成できるようになりました。 このモードを構成した場合、指定したアプリが実行されると、デバイスはそのアプリだけを実行できるようにロックされます。 たとえば、ユーザーがデバイスでテストを受けられるようにアプリを構成するような場合です。 アプリのアクションが完了した場合、または管理者がこのポリシーを削除した場合、デバイスは通常の状態に戻ります。

### <a name="configure-trusted-domains-for-email-and-web-browsing-on-ios-devices---723765---"></a>iOS デバイスでメールと Web ブラウザー用の信頼されたドメインを構成する<!-- 723765 -->
iOS デバイス制限プロファイルから、次の[ドメイン設定](../configuration/device-restrictions-ios.md#domains)を構成できるようになりました。

- **[マークされていないメール ドメイン]** - ユーザーが送信または受信するメールのうち、ここで指定したドメインと一致しないものは、信頼されていないメールとしてマークされます。

- **[管理された Web ドメイン]** - ここで指定した URL からダウンロードされたドキュメントは、管理されているものと見なされます (Safari のみ)。  

- **[Safari パスワードの自動入力ドメイン]** - ユーザーは、ここで指定したパターンに一致する URL からのパスワードのみを Safari に保存できます。 この設定を使うには、デバイスが監視モードであり、複数ユーザー用に構成されていない必要があります。 (iOS 9.3 以降)


### <a name="vpp-apps-available-in-ios-company-portal---748782---"></a>iOS ポータル サイトで使用できる VPP アプリ<!-- 748782 -->
**利用可能な**インストールとして、iOS ボリューム購入 (VPP) アプリをエンド ユーザーに割り当てられるようになりました。 エンド ユーザーがアプリをインストールするには、Apple ストア アカウントが必要です。

### <a name="synchronize-ebooks-from-apple-vpp-store---800878---"></a>Apple VPP ストアから電子ブックを同期する<!-- 800878 -->
Intune と、Apple ボリューム購入プログラム ストアから購入した[本を同期](../apps/vpp-apps-ios.md)し、ユーザーに割り当てることができるようになりました。

### <a name="multi-user-management-for-samsung-knox-standard-devices---971988---"></a>Samsung KNOX Standard デバイスのマルチ ユーザー管理<!-- 971988 -->
Samsung KNOX Standard を実行するデバイスが、Intune による[マルチ ユーザー管理](../enrollment/android-enroll.md)のサポート対象になりました。 つまり、エンド ユーザーは Azure Active Directory の資格情報を使ってデバイスのサインインとサインアウトを行うことができ、デバイスは使用中かどうかに関わらず一元管理されます。  サインインしたエンド ユーザーはアプリにアクセスできます。ポリシーがあれば、それが適用されます。 ユーザーがサインアウトすると、すべてのアプリ データがクリアされます。

### <a name="additional-windows-device-restriction-settings---818566---"></a>追加の Windows デバイス制限設定<!-- 818566 -->
追加の Microsoft Edge ブラウザー サポート、デバイス ロック画面のカスタマイズ、スタート メニューのカスタマイズ、Windows スポットライト検索セットの壁紙、プロキシ設定など、追加の [Windows デバイス制限設定](../configuration/device-restrictions-windows-10.md)のサポートが追加されました。

### <a name="multi-user-support-for-windows-10-creators-update---822547---"></a>Windows 10 Creators Update のマルチユーザー サポート<!-- 822547 -->
Windows 10 Creators Update を実行し Azure Active Directory ドメインに参加しているデバイスの[マルチユーザー管理](../enrollment/windows-enroll.md)のサポートが追加されました。 つまり、異なる標準ユーザーが Azure AD 資格情報でデバイスにログインすると、ユーザー名に割り当てられているすべてのアプリとポリシーを受け取ります。 現時点では、アプリのインストールのようなセルフサービスのシナリオにポータル サイトは使用できません。

### <a name="fresh-start-for-windows-10-pcs---1004830---"></a>Windows 10 PC の Fresh Start<!-- 1004830 -->
Windows 10 PC で、新しい [Fresh Start デバイス アクション](../remote-actions/device-fresh-start.md)が使用できるようになりました。  このアクションを発行すると、PC にインストールされたすべてのアプリが削除され、PC は Windows の最新バージョンに自動的に更新されます。 この機能は、新しい PC に付属することの多い事前インストール済み OEM アプリを削除するのに使うことができます。 このデバイス アクションを発行するときにユーザー データを保持するかどうかを構成できます。

### <a name="additional-windows-10-upgrade-paths---903672---"></a>Windows 10 の追加アップグレード パス<!-- 903672 -->
以下のエディションの Windows 10 にも、[エディション アップグレード ポリシーの作成によりデバイスをアップグレード](../configuration/edition-upgrade-configure-windows-10.md)できるようになりました。

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N

### <a name="bulk-enroll-windows-10-devices---747607---"></a>Windows 10 デバイスを一括登録する<!-- 747607 -->
Windows 構成デザイナー (WCD) で Azure Active Directory と Intune に Windows 10 Creators Update を実行する多数のデバイスを参加させることができるようになりました。 Azure AD テナントの [一括 MDM 登録](../enrollment/windows-bulk-enroll.md) を有効にするには、Windows 構成デザイナーを使用して Azure AD テナントにデバイスを参加させるプロビジョニング パッケージを作成し、一括登録と管理を行う会社所有のデバイスにパッケージを適用します。 パッケージがご利用のデバイスに適用されると、デバイスは Azure AD に参加し、Intune に登録され、Azure AD ユーザーがサインインできる状態になります。  Azure AD ユーザーはこれらのデバイス上の標準ユーザーであり、割り当て済みのポリシーと必須アプリを受け取ります。 現在のところ、セルフ サービスとポータル サイトのシナリオはサポートされていません。

### <a name="new-mam-settings-for-pin-and-managed-storage-locations---581122-736644---"></a>暗証番号 (PIN) および管理対象記憶域の場所に対する新しい MAM 設定<!-- 581122, 736644 -->
モバイル アプリケーション管理 (MAM) シナリオに役立つ 2 つの新しいアプリ設定が使用できるようになりました。

- **[Disable app PIN when device PIN is managed (デバイスの PIN が管理されるときはアプリの PIN を無効にする)]** - 登録されたデバイスにデバイス暗証番号 (PIN) が存在するかどうかを検出し、存在する場合は、アプリ保護ポリシーによってトリガーされるアプリ PIN をバイパスします。 この設定を使うと、登録されたデバイスで MAM が有効なアプリケーションを開くユーザーに対して表示される PIN 要求の回数を減らすことができます。 この機能は、Android と iOS の両方で使うことができます。

- **[会社のデータを保存できるストレージ サービスの選択]** - 会社のデータを保存する記憶域の場所を指定できます。 ユーザーは選択したストレージ ロケーション サービスに保存できます。つまり、表示されていない他のすべてのストレージ ロケーション サービスはブロックされます。

  サポートされるストレージ ロケーション サービスの一覧は次のとおりです。

  - OneDrive
  - Business SharePoint Online
  - ローカル ストレージ

### <a name="help-desk-troubleshooting-portal---907448---"></a>ヘルプ デスクのトラブルシューティング ポータル<!-- 907448 -->
新しい[トラブルシューティング ポータル](../help-desk-operators.md)を使用すると、ヘルプ デスクと Intune 管理者は、ユーザーと彼らのデバイスを表示して、Intune の技術的な問題を解決するタスクを実行できます。

<!-- ########################## -->
## <a name="march-2017"></a>2017 年 3 月

### <a name="support-for-ios-lost-mode--431695--"></a>iOS 紛失モードのサポート<!--431695-->
iOS 9.3 以降のデバイスについて、Intune で**紛失モード**のサポートが追加されました。 デバイスをロックダウンしてすべての使用を回避し、デバイスのロック画面のメッセージおよび連絡先の電話番号を表示できるようになりました。

エンドユーザーは、管理者が紛失モードを無効にするまで、デバイスのロックを解除することはできません。 紛失モードを有効にした場合、**デバイスを探索する**アクションを使用して、Intune コンソールでマップ上にデバイスの地理的な場所を表示することができます。

会社所有の iOS デバイスを DEP で登録し、監視モードに設定している必要があります。

詳細については、「[Microsoft Intune デバイスの管理とは](../remote-actions/device-management.md)」を参照してください。

### <a name="improvements-to-device-actions-report--677150--"></a>Device Actions レポートの機能強化<!--677150-->
Device Actions レポートの機能が強化され、パフォーマンスが向上しました。 さらに、レポートを状態別にフィルター処理できるようになりました。 たとえば、レポートをフィルター処理して、完了したデバイス アクションのみを表示できます。

### <a name="custom-app-categories--748805--"></a>カスタム アプリのカテゴリ<!--748805-->
Intune に追加するアプリのカテゴリを作成、編集、および割り当てることができるようになりました。 現時点では、カテゴリは英語でのみ指定できます。
[Intune にアプリを追加する方法](../apps/apps-add.md)に関するページを参照してください。

### <a name="assign-lob-apps-to-users-with-unenrolled-devices--748823--"></a>登録していないデバイスを使用しているユーザーに LOB アプリを割り当てる<!--748823-->
デバイスが Intune に登録されているかどうかに関係なく、基幹業務アプリをストアからユーザーに割り当てられるようになりました。 ユーザーのデバイスが Intune に登録されていない場合は、ポータル サイト アプリではなく、ポータル Web サイトに移動してインストールする必要があります。

### <a name="new-compliance-reports--846671--"></a>新しいコンプライアンス レポート<!--846671-->
コンプライアンス レポートにより、会社内のコンプライアンスの状況を表示して、社内のユーザーがコンプライアンス関連の問題に直面したときに迅速にトラブルシューティングできるようになりました。 次の情報を表示できます。

- デバイスの総合的なコンプライアンスの状態
- 設定別のコンプライアンスの状態
- ポリシー別のコンプライアンスの状態

これらのレポートを使用して個々のデバイスをドリルダウンし、そのデバイスに影響を与えている特定の設定およびポリシーを確認することもできます。

<!--- You can now create an edition upgrade policy to upgrade devices to the following additional Windows 10 editions:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N --->

### <a name="direct-access-to-apple-enrollment-scenarios--951869--"></a>Apple 登録シナリオへの直接アクセス<!--951869-->
Intune では、2017 年 1 月以降に作成された Intune アカウントについて、Azure Portal の Enroll Devices ワークロードを使用して、Apple 登録シナリオに直接アクセスできるようになりました。 これまでは、Apple 登録プレビューは Azure Portal のリンクからのみアクセスが可能でした。 2017 年 1 月より前に作成された Intune アカウントの場合は、これらの機能が Azure で利用可能になるまでの間、1 回限りの移行が必要です。 移行スケジュールはまだ発表されていませんが、詳細はできる限り早く発表します。 既存のアカウントでプレビューにアクセスできない場合は、試用アカウントを作成して、新しいエクスペリエンスをテストすることを強くお勧めします。


<!-- ########################## -->
## <a name="february-2017"></a>2017 年 2 月

### <a name="ability-to-restrict-mobile-device-enrollment--747600-795782--"></a>モバイル デバイス登録を制限する機能<!--747600, 795782-->
Intune では、登録を許可されるモバイル デバイス プラットフォームを制御する新しい登録制限が追加されています。 Intune では、モバイル デバイス プラットフォームが iOS、macOS、Android、Windows、Windows Mobile に分かれています。

- モバイル デバイスの登録を制限しても、PC クライアントの登録は制限されません。  
- iOS と Android のみに、個人所有デバイスの登録をブロックする 1 つの追加オプションがあります。

[この記事](../enrollment/device-enrollment.md)で説明されているように、IT 管理者が明示的に会社所有と指定しない限り、Intune はすべての新しいデバイスを個人所有としてマークします。

### <a name="view-all-actions-on-managed-devices--677150--"></a>マネージド デバイスのすべての操作を表示<!--677150-->
新しい__デバイス操作__レポートには、デバイスでの出荷時の設定にリセットなどのリモート操作を実行したユーザーが表示され、さらにその操作の状態が表示されます。 「[デバイス管理とは](../remote-actions/device-management.md)」を参照してください。

### <a name="non-managed-devices-can-access-assigned-apps--664691--"></a>管理されていないデバイスから割り当てられているアプリにアクセス可能<!--664691-->
ポータル Web サイトでの設計変更に伴い、iOS と Android ユーザーは、管理されていないデバイスで "登録なしで使用可能" として割り当てられているアプリをインストールできるようになります。 Intune 資格情報を使用して、ユーザーはポータル Web サイトにログインし、割り当てられているアプリの一覧を表示することができます。 "登録なしで使用可能" なアプリのアプリ パッケージは、ポータル Web サイトからダウンロードできます。 この変更は、インストールするために登録が必要なアプリには影響しません。そのようなアプリをインストールする場合は、デバイスの登録が求められます。

### <a name="custom-app-categories--748805--"></a>カスタム アプリのカテゴリ<!--748805-->
Intune に追加するアプリのカテゴリを作成、編集、および割り当てることができるようになりました。 現時点では、カテゴリは英語でのみ指定できます。
[Intune にアプリを追加する方法](../apps/apps-add.md)に関するページを参照してください。

### <a name="display-device-categories--814654--"></a>デバイス カテゴリを表示する<!--814654-->
デバイスの一覧に、列としてデバイス カテゴリを表示できるようになりました。 デバイスのプロパティー ブレードのプロパティー セクションからカテゴリを編集することもできます。 [Intune にアプリを追加する方法](../apps/apps-add.md)に関するページを参照してください。

### <a name="configure-windows-update-for-business-settings--776716--"></a>ビジネス設定向けの Windows Update の構成<!--776716-->

サービスとしての Windows は、Windows 10 の更新プログラムを提供するための新しい方法です。 Windows 10 以降、すべての新しい機能更新プログラムと品質更新プログラムには、以前の更新プログラムすべての内容が含まれます。 つまり、最新の更新プログラムをインストールしている限り、Windows 10 デバイスが完全に最新の状態であることを把握できます。 以前のバージョンの Windows とは異なり、更新プログラムの一部ではなく全体をインストールすることが必要になります。

Windows Update for Business を使用することで、デバイスのグループに対して個々の更新プログラムを承認する必要がなくなるため、更新プログラム管理エクスペリエンスを簡略化できます。 更新プログラムの展開戦略を構成することで環境内のリスクを引き続き管理でき、さらに Windows Update により更新プログラムが適切なタイミングでインストールされるようになります。 Microsoft Intune では、デバイスでの更新プログラムの設定を構成でき、また更新プログラムのインストールを遅らせることができます。 Intune では更新プログラムは格納されず、更新プログラムのポリシー割り当てのみが格納されます。 デバイスは更新プログラムのため Windows Update に直接アクセスします。**Windows 10 更新プログラム リング**を構成し管理するには Intune を使用します。 更新プログラム リングには、Windows 10 更新プログラムがインストールされるタイミングと方法を構成する設定のグループが含まれています。 詳しくは、「[ビジネス設定向けの Windows Update の構成](../protect/windows-update-for-business-configure.md)」をご覧ください。
