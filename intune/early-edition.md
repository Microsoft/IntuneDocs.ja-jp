---
title: "初期エディション"
description: 
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/24/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d4bcabc4d1af4554a3e3bea875be45f9376b4ef7
ms.sourcegitcommit: b982f9d50da4f958fb0c48c56ba46c8ef71500c4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2018
---
# <a name="the-early-edition-for-microsoft-intune---february-2018"></a>Microsoft Intune の初期エディション - 2018 年 2 月

**初期エディション**では、Microsoft Intune の今後のリリースで予定されている新機能の一覧を提供しています。 ここに記載されている情報は、限られた範囲について開示されたものであり、また今後変更される可能性があります。 社外ではこの情報を共有しないでください。 ここに挙げられている機能は、発売日に間に合わない可能性があり、その場合は将来のリリースを待たなければなりません。 正式なリリースに向けてパイロット (フライト) テスト中の機能もあります。 ご不明な点や懸念される事項がある場合は、Microsoft 製品グループにお問い合わせください。

このページは定期的に更新されます。 適宜確認してください。

> [!Note]
>Intune に関して以下の機能が現在開発されています。 最新のハイブリッド機能の詳細については、[ハイブリッド環境の新機能に関するページ](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)を参照してください。

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->

## <a name="intune-in-the-azure-portal"></a>Azure Portal での Intune


<!-- 1802 start -->


### <a name="app-protection-policies-----679615---"></a>アプリ保護ポリシー  <!-- 679615 -->
Intune App Protection ポリシーは、既定のグローバル ポリシーを作成し、テナント全体のすべてのユーザーに保護をすばやく適用する機能を提供します。

### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685---"></a>複数の Apple DEP および Apple School Manager アカウントに対する Intune サポート<!-- 747685 -->

最大 100 個の異なる Apple Device Enrollment Program (DEP) または Apple School Manager アカウントからのデバイス登録が、Intune でサポートされます。 アップロードされる各トークンは、登録プロファイルとデバイスで、別々に管理できます。 アップロードされる DEP および School Manager のトークンごとに、異なる登録プロファイルを自動で割り当てることができます。 複数の School Manager トークンがアップロードされた場合、Microsoft 学校データ同期と共有できるのは、一度に 1 つのみです。

移行後、Graph で Apple DEP および ASM を管理するベータ版の Graph API と公開されたスクリプトは、動作しなくなります。 現在、新しいベータ版の Graph API の開発が進行中で、移行後にリリースされる予定です。

### <a name="windows-defender-health-status-and-threat-status-reports---854704---"></a>Windows Defender の正常性状態レポートと脅威状態レポート<!--854704 -->

Windows Defender の正常性と状態を理解することは、Windows PC の管理において重要なことです。  Intune は、Windows Defender エージェントの状態と正常性に対して新しいレポートやアクションを追加します。 デバイスのポリシー準拠ワークロードの状態ロールアップ レポートを使うと、次のことが必要なデバイスを発見できます。

- 署名の更新
- 再起動
- 手動介入
- フル スキャン
- 介入を必要とする他のエージェント状態

場合によっては、署名更新のトリガーなどのリモート修復アクションを実行できます。  レポートでは、**クリーン**と報告されている PC の数も示されます。

各状態カテゴリのドリルイン レポートでは、注意の必要な PC または**クリーン**と報告されている PC が個別に一覧表示されます。

### <a name="protocol-exceptions-for-applications---1035509-eeready--"></a>アプリケーションのプロトコル例外 <!--1035509 eeready-->

Intune モバイル アプリケーション管理 (MAM) データ転送ポリシーの例外を作成し、特定の管理されていないアプリケーションを開くことができます。 このようなアプリケーションは、IT 担当者によって信頼されている必要があります。 データ転送ポリシーを**管理対象アプリのみ**に設定すると、作成した例外以外については、やはりデータ転送が Intune で管理されているアプリケーションだけに制限されます。 プロトコル (iOS) またはパッケージ (Android) を使って制限を作成することができます。

たとえば、MAM データ転送ポリシーに対する例外として、Webex パッケージを追加できます。 これにより、管理された Outlook メール メッセージ内の Webex リンクを、Webex アプリケーションで直接開くことができます。 他の管理されていないアプリケーションでは、データ転送が制限されます。

### <a name="customize-your-company-portal-themes-with-hex-codes---1049561-eeready--"></a>Intune ポータル サイトのテーマを 16 進コードでカスタマイズする <!--1049561 eeready-->

Intune ポータル サイト アプリのテーマの色を、16 進コードを使ってカスタマイズできます。 16 進コードを入力すると、Intune は、[WCAG 2.0 標準](http://www.w3.org/TR/WCAG20)に従って、テキストの色と背景の色の間のコントラストが最高レベルになるようにテキストの色を決定します。 **[Mobile Apps]** > **[ポータル サイト]** で、テキストの色および色に対する会社のロゴの両方をプレビューできます。 

### <a name="select-device-categories-by-using-the-access-work-or-school-settings----1058963---"></a>[職場または学校にアクセスする] 設定を用いたデバイス カテゴリの選択<!-- 1058963 --> 
[デバイス グループ マッピング](https://docs.microsoft.com/en-us/intune/device-group-mapping)を有効にした場合、**[設定]** > **[アカウント]** > **[職場または学校にアクセスする]** の **[接続]** から登録後、または out-of-box experience の際に、Windows 10 のユーザーはデバイス カテゴリの選択を求められます。

### <a name="new-windows-defender-credential-guard-settings-added-to-endpoint-protection-settings---1102252---"></a>Endpoint Protection の設定に追加された新しい Windows Defender Credential Guard の設定<!--1102252 --> 

新しい [Windows Defender Credential Guard](https://docs.microsoft.com/windows/access-protection/credential-guard/credential-guard) の設定が、**[デバイス構成]** > **[プロファイル]** > **[Endpoint Protection]** に追加されます。 次の設定が追加されます。 

- プラットフォームのセキュリティ レベル: 次の再起動時にプラットフォームのセキュリティ レベルを有効にするかどうかを指定します。 仮想化ベースのセキュリティには、セキュア ブートが必要です。 仮想化ベースのセキュリティは、ダイレクト メモリ アクセス (DMA) 保護を使って、必要に応じて有効にすることができます。 DMA 保護は、ハードウェアのサポートを必要とし、正しく構成されたデバイスでのみ有効にされます。
- 仮想化ベースのセキュリティ: 次の再起動時に仮想化ベースのセキュリティを有効にするかどうかを指定します。 
- Windows Defender Credential Guard: プラットフォームのセキュリティ レベルとセキュア ブートおよび仮想化ベースのセキュリティがどちらも有効な次の再起動時に、仮想化ベースのセキュリティで Credential Guard を有効にして資格情報を保護します。 使用できるオプションは、**[無効]**、**[UEFI ロックで有効化]**、**[ロックなしで有効化]**、**[未構成]** です。 
  - [無効] オプションは、以前に Credential Guard が [ロックなしで有効化] オプションで有効になっていた場合に、Credential Guard をリモートで無効にします。

  - [UEFI ロックで有効化] オプションは、レジストリ キーまたはグループ ポリシーを使って Credential Guard を無効にできないようにします。 この設定を使った後で Credential Guard を無効にするには、グループ ポリシーを "無効" に設定し、ユーザーが直接各コンピューターからセキュリティ機能を削除して、UEFI に保持されている構成をクリアする必要があります。 UEFI の構成が保持されている限り、Credential Guard は有効になっています。

  - [ロックなしで有効化] オプションは、グループ ポリシーを使ってリモートで Credential Guard を無効にできるようにします。 この設定を使うデバイスは、Windows 10 (バージョン 1511) 以降を実行している必要があります。

  - [未構成] オプションは、ポリシー設定を未定義のままにします。 グループ ポリシーはレジストリにポリシー設定を書き込まないので、コンピューターまたはユーザーに影響はありません。 現在レジストリ内の設定がある場合、それは変更されません。

### <a name="synchronize-and-deploy-sparsely-bundled-windows-store-for-business-apps---1222672---"></a>疎にバンドルされているビジネス向け Windows ストア アプリを同期および展開する <!--1222672 -->
ビジネス向け Windows ストアから購入されたオフライン アプリが、Intune ポータルに同期されるようになります。 その後、これらのアプリをデバイス グループまたはユーザー グループに展開できます。 オフライン アプリはストアではなく Intune によってインストールされます。

### <a name="reset-passwords-for-android-o-devices----1238299---"></a>Android O デバイスのパスワードをリセットする <!-- 1238299 -->
登録済みの Android O デバイスのパスワードをリセットできるようになります。 Android O デバイスに "パスワード リセット" 要求を送信すると、新しいデバイス ロック解除パスワードまたはマネージ プロファイルのチャレンジが、現在のユーザーに設定されます。 パスワードまたはチャレンジは、デバイスにプロファイル所有者またはデバイス所有者がいるかどうかに基づいて送信され、すぐに有効になります。

### <a name="local-device-security-option-settings----1251887---"></a>ローカル デバイス セキュリティ オプションの設定 <!-- 1251887 -->
新しいローカル デバイス セキュリティ オプションの設定を使って、Windows 10 デバイスのセキュリティ設定を有効にできます。 これらの設定は、Windows 10 デバイスの構成ポリシーを作成するときに、[Endpoint Protection] カテゴリに表示されます。

### <a name="new-printer-settings-for-education-profiles----1308900---"></a>教育プロファイル用の新しいプリンター設定 <!-- 1308900 -->

教育プロファイルの場合、**[プリンター]** カテゴリで新しい設定 **[プリンター]**、**[通常使うプリンター]**、**[新しいプリンターの追加]** を利用できます。 

### <a name="new-privacy-settings-for-device-restrictions---1308926---"></a>デバイス制限のための新しいプライバシー設定 <!--1308926 -->

2 つの新しいプライバシー設定をデバイスで利用できます。

- **ユーザー アクティビティの公開**: これを **[ブロック]** に設定すると、タスク スイッチャーでの共有エクスペリエンスおよび最近使われたリソースの検出が行われなくなります。

- **ローカル アクティビティの場合のみ**: これを **[ブロック]** に設定すると、ローカル アクティビティのみに基づいて、タスク スイッチャーでの共有エクスペリエンスおよび最近使われたリソースの検出が行われなくなります。

### <a name="macos-company-portal-support-for-enrollments-that-use-the-device-enrollment-manager----1352411---"></a>デバイス登録マネージャーを使う登録の macOS ポータル サイトによるサポート <!-- 1352411 -->

ユーザーは、macOS ポータル サイトで登録するときに、デバイス登録マネージャーを使うことができます。

#### <a name="new-settings-for-the-edge-browser---1469166---"></a>Edge ブラウザーの新しい設定 <!--1469166 -->

Edge ブラウザーを備えたデバイスで、2 つの新しい設定 **[Path to favorites file]\(お気に入りファイルへのパス\)** と **[Changes to Favorites]\(お気に入りへの変更\)** を利用できるようになります。 

### <a name="windows-information-protection-wip-encrypted-data-in-windows-search-results----1469193---"></a>Windows 検索結果の Windows 情報保護 (WIP) 暗号化データ<!-- 1469193 -->

Windows 情報保護 (WIP) ポリシーの新しい設定により、WIP で暗号化されたデータを Windows の検索結果に含めるかどうかを制御できます。

### <a name="line-of-business-lob-app-support-for-macos----1473977---"></a>macOS の基幹業務 (LOB) アプリのサポート <!-- 1473977 -->
Intune は、macOS LOB アプリをインストールする機能を提供します。 LOB アプリとは、インストール ファイルが提供され、Intune を使ってデバイスにインストールされるアプリです。 macOS LOB アプリのサポートの一環として、macOS 用の Microsoft Intune アプリ ラッピング ツールを使って、macOS 基幹業務 (LOB) アプリを前処理する必要があります。

### <a name="configure-resource-account-settings-for-surface-hubs----1475674---"></a>Surface Hub のリソース アカウント設定を構成する <!-- 1475674 -->

Surface Hub のリソース アカウント設定をリモートで構成することができます。

このリソース アカウントは、Skype または Exchange でミーティングに参加できるように認証する場合に Surface Hub で使用されます。 Surface Hub がミーティングで会議室として表示されるように、一意のリソース アカウントを作成できます。 たとえば、**会議室 B41/6233** のようなリソース アカウントです。

> [!NOTE]
> - フィールドを空白のままにすると、デバイスで以前に構成された属性が上書きされます。
>
> - リソース アカウントのプロパティは、Surface Hub で動的に変更できます。 たとえば、パスワードのローテーションが有効かどうか、などです。 そのため、Azure コンソールの値が、デバイス上の現実に反映されるまでに時間がかかることがあります。 
>
>   Surface Hub での現在の構成を理解するには、リソース アカウント情報をハードウェア インベントリ (既に 7 日間隔になっています) または読み取り専用プロパティに含めることができます。 リモート操作が行われた後の精度を向上させるには、操作実行直後にパラメーターの状態を取得し、Surface Hub のアカウント/パラメーターを更新できます。

### <a name="ios-app-provisioning-configuration----1581650---"></a>iOS アプリのプロビジョニングの構成 <!-- 1581650 -->
iOS アプリにプロビジョニング プロファイルを割り当てて、セキュリティ グループを包含または除外することで、アプリが期限切れにならないようにすることができます。

### <a name="new-windows-defender-exploit-guard-settings----631893---"></a>Windows Defender Exploit Guard の新しい設定 <!-- 631893 -->

**[攻撃の回避]** の 6 つの新しい設定と、拡張された **[フォルダー アクセスの制御: フォルダーの保護]** 機能を利用できます。 これらの設定は、[デバイス構成] > [プロファイル] > 
[プロファイルの作成] > [Endpoint Protection] > [Windows Defender Exploit Guard] にあります。

#### <a name="attack-surface-reduction"></a>攻撃の回避

|設定の名前  |設定オプション  |説明  |
|---------|---------|---------|
|Advanced ransomware protection (高度なランサムウェア防止)|有効、監査、未構成|積極的なランサムウェア防止を使います。|
|Flag credential stealing from the Windows local security authority subsystem (Windows ローカル セキュリティ機関サブシステムからの資格情報の盗難にフラグを設定する)|有効、監査、未構成|Windows ローカル セキュリティ機関サブシステム (lsass.exe) からの資格情報の盗難にフラグを設定します。|
|Process creation from PSExec and WMI commands (PSExec および WMI コマンドからのプロセス作成)|ブロック、監査、未構成|PSExec および WMI コマンドから開始されるプロセス作成をブロックします。|
|Untrusted and unsigned processes that run from USB (USB から実行された信頼されていない署名なしのプロセス)|ブロック、監査、未構成|USB から実行された信頼されていない署名なしのプロセスをブロックします。|
|Executables that don’t meet a prevalence, age, or trusted list criteria (普及、経過時間、または信頼されたリストの条件を満たしていない実行可能ファイル)|ブロック、監査、未構成|普及、経過時間、または信頼されたリストの条件を満たしていない実行可能ファイルの実行をブロックします。|

#### <a name="controlled-folder-access"></a>フォルダー アクセスの制御

|設定の名前  |設定オプション  |説明  |
|---------|---------|---------|
|フォルダーの保護 (実装済み)|未構成、有効、監査のみ (実装済み)<br><br> **新規**<br>Block disk modification (ディスクの変更をブロックする)、Audit disk modification (ディスクの変更を監査する)|
ファイルおよびフォルダーを、悪意のあるアプリによる未承認の変更から保護します。<br><br>**有効**: 信頼されていないアプリによる、保護されたフォルダー内のファイルの変更または削除、およびディスク セクターへの書き込みを、禁止します。<br><br>
**Block disk modification only (ディスクの変更のみをブロック)**:<br>信頼されていないアプリによるディスク セクターへの書き込みをブロックします。 信頼されていないアプリは、保護されたフォルダー内のファイルを変更または削除することはできます。

### <a name="new-windows-defender-application-guard-settings----1631890---"></a>Windows Defender Application Guard の新しい設定 <!-- 1631890 -->

- **Enable graphics acceleration (グラフィック アクセラレータを有効にする)**

管理者は、Windows Defender Application Guard の仮想グラフィック プロセッサを有効にすることができます。 この設定を使うと、CPU はグラフィックのレンダリングを vGPU にオフロードできます。 これにより、グラフィックが多用されている Web サイトを操作するとき、またはコンテナー内のビデオを見るときのパフォーマンスが向上します。

- **SaveFilestoHost**

管理者は、コンテナーで実行されている Microsoft Edge からホスト ファイル システムへのファイルの受け渡しを有効にすることができます。 これをオンにすると、ユーザーは、コンテナー内の Microsoft Edge からホスト ファイル システムにファイルをダウンロードできます。

### <a name="see-enrollment-restrictions-per-user----1634444---"></a>ユーザーごとに登録の制限を表示する <!-- 1634444 -->
トラブルシューティング ブレードで、ユーザーごとに有効になっている登録の制限を表示することができます。

### <a name="configuring-a-self-updating-mobile-msi-app----1740840---"></a>自己更新モバイル MSI アプリの構成 <!-- 1740840 -->
バージョン チェック プロセスを無視するように、既知の自己更新モバイル MSI アプリを構成することができます。 この機能は、競合状態になるのを防ぐのに役立ちます。 たとえば、アプリ開発者によって自動更新されているアプリが、Intune によっても更新されると、競合状態が発生する可能性があります。 両方が Windows クライアント上のアプリのバージョンを強制しようとして、競合が発生することがあります。

### <a name="additions-to-system-security-settings-for-windows-10-and-later-compliance-policies---1704133---"></a>Windows 10 以降のコンプライアンス ポリシーのシステム セキュリティ設定への追加 <!--1704133 -->

ファイアウォールと Windows Defender ウイルス対策の要求など、Windows 10 のコンプライアンス設定への追加機能が使用可能になります。

### <a name="including-and-excluding-app-assignment-based-on-groups-for-android-enterprise----1813081---"></a>Android Enterprise に対するグループに基づくアプリ割り当ての追加と除外 <!-- 1813081 -->
Android Enterprise (旧称 Android for Work) は、アプリの割り当て中、および割り当て種類の選択後の除外機能をサポートします。


### <a name="related-sets-of-app-licenses-supported-in-intune----1864117---"></a>Intune でサポートされるアプリ ライセンスの関連する設定 <!-- 1864117 -->
Azure Portal 内の Intune は、UI の単一アプリ項目として、アプリ ライセンスの関連する設定をサポートします。 さらに、ビジネス向け Microsoft Store から同期されるすべてのオフライン ライセンス アプリは単一のアプリ エントリに統合され、個別のパッケージからの展開の詳細は 1 つのエントリに移行されます。 Azure Portal でアプリ ライセンスの関連する設定を表示するには、**[Mobile Apps]** ブレードから **[アプリ ライセンス]** を選びます。

<!-- the following are present prior to 1802 -->

### <a name="new-option-for-user-authentication-for-apple-bulk-enrollment----747625---"></a>Apple の一括登録に対するユーザー認証の新しいオプション<!-- 747625 -->
Intune では、次の登録方法について、ポータル サイト アプリを使用してデバイスを認証できます。

- Apple Device Enrollment Program
- Apple School Manager
- Apple Configurator Enrollment

このポータル サイト オプションを使用すると、これらの登録方法をブロックすることなく、Azure Active Directory の多要素認証を強制できます。

このポータル サイト オプションを使用する場合、iOS 設定アシスタントでの、ユーザー アフィニティ登録用のユーザー認証がスキップされます。 つまり、このデバイスは、最初はユーザーのいないデバイスとして登録されるため、ユーザー グループの構成やポリシーは受信しません。 デバイス グループの構成とポリシーのみを受信します。 ただし、ポータル サイト アプリは自動的にデバイスにインストールされます。 ポータル サイト アプリを最初に起動してサインインするユーザーは、Intune でそのデバイスと関連付けられます。 この時点で、ユーザー グループの構成とポリシーが、このユーザーに送信されます。 ユーザーの関連付けを変更するには、再登録が必要です。

### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685---"></a>複数の Apple DEP および Apple School Manager アカウントに対する Intune サポート<!-- 747685 -->
最大 100 個の異なる Apple Device Enrollment Program (DEP) または Apple School Manager アカウントからのデバイス登録が、Intune でサポートされます。 アップロードされる各トークンは、登録プロファイルとデバイスで、別々に管理できます。 アップロードされる DEP および School Manager のトークンごとに、異なる登録プロファイルを自動で割り当てることができます。 複数の School Manager トークンがアップロードされた場合、Microsoft 学校データ同期と共有できるのは、一度に 1 つのみです。

移行後、Graph で Apple DEP および ASM を管理するベータ版の Graph API と公開されたスクリプトは、動作しなくなります。 現在、新しいベータ版の Graph API の開発が進行中で、移行後にリリースされる予定です。

### <a name="select-device-categories-by-using-the-access-work-or-school-settings----1058963---"></a>[職場または学校にアクセスする] 設定を用いたデバイス カテゴリの選択<!-- 1058963 -->
[デバイス グループ マッピング](https://docs.microsoft.com/en-us/intune/device-group-mapping)を有効にした場合、**[設定]** > **[アカウント]** > **[職場または学校にアクセスする]** の **[接続]** から登録後、または out-of-box experience の際に、Windows 10 のユーザーはデバイス カテゴリの選択を求められます。

### <a name="targeting-compliance-policies-to-devices-in-device-groups---1307012---"></a>デバイス グループのデバイスへのコンプライアンス ポリシーのターゲット<!--1307012 -->

ユーザー グループ内のユーザーを、コンプライアンス ポリシーのターゲットにできます。 デバイス グループ内のデバイスを、コンプライアンス ポリシーのターゲットにできます。

### <a name="including-and-excluding-app-assignment-based-on-groups----1406920---"></a>グループに基づくアプリ割り当ての追加と除外<!-- 1406920 -->

アプリの割り当て時、および割り当ての種類の選択後に、含めるグループと、除外するグループを選択できます。

### <a name="remote-erase-command-support----1438084---"></a>リモートの "消去" コマンド サポート <!-- 1438084 -->

管理者は、消去コマンドをリモートで発行できます。

> [!IMPORTANT]
> 消去コマンドは、元に戻すことができないため、使用する際は注意が必要です。

消去コマンドでは、オペレーティング システムを含むすべてのデータが、デバイスから削除されます。 また、そのデバイスも、Intune 管理から削除されます。 ユーザーに対して警告は表示されません。また、コマンドを発行すると、消去は即座に実行されます。

6 桁の回復用 PIN を構成することができます。 この PIN を使用すると、消去されたデバイスのロックが解除され、オペレーティング システムの再インストールが開始されます。 PIN は、消去が開始されると、Intune のデバイスの概要ブレードのステータス バーに表示されます。 消去が完了するまでの間、PIN はずっと表示されます。 消去が完了したら、デバイスは Intune 管理から完全に削除されます。 デバイスを復元する人が誰であっても、そのデバイスを使用できるように、回復用 PIN は必ず記録するようにしてください。

### <a name="windows-information-protection-wip-encrypted-data-in-windows-search-results----1469193---"></a>Windows 検索結果の Windows 情報保護 (WIP) 暗号化データ<!-- 1469193 -->

Windows 情報保護 (WIP) ポリシーの新しい設定により、WIP で暗号化されたデータを Windows の検索結果に含めるかどうかを制御できます。

### <a name="website-learning-mode----1631908---"></a>Web サイトの学習モード <!-- 1631908 -->

Intune では、Windows 情報保護 (WIP) 学習モードの拡張機能が導入されます。 WIP が有効になっているアプリの情報を表示できるだけでなく、作業データを Web サイトで共有しているデバイスの概要も表示できます。 この情報を使用して、グループおよびユーザーの WIP ポリシーに追加する Web サイトを判断できます。

### <a name="updates-to-compliance-emails---1637547---"></a>コンプライアンスのメールに対する変更 <!--1637547 -->

コンプライアンス違反のデバイスを報告するメールが送信される際、そのコンプライアンス違反のデバイスの詳細が含まれるようになります。 この変更を反映するために、[コンプライアンス違反に対する措置の自動化](#actions-for-noncompliance)に関する記事が更新されます。

###  <a name="alerts-for-expired-tokens-and-tokens-that-will-soon-expire----1639263---"></a>期限切れトークンと有効期限が近いトークンのアラート<!-- 1639263 -->
有効期限が切れているトークンと、有効期限が近づいているトークンのアラートが概要ページに表示されます。 1 つのトークンのアラートをクリックすると、そのトークンの詳細ページに移動します。  複数のトークンのアラートをクリックすると、トークンのステータスが表示された全トークンの一覧に移動します。 管理者は、有効期限が来る前にトークンを更新する必要があります。

### <a name="remote-printing-over-a-secure-network----1709994----"></a>セキュリティで保護されたネットワークでのリモート印刷<!-- 1709994  -->
PrinterOn のワイヤレス モバイル印刷ソリューションは、時間や場所を問わない、セキュリティで保護されたネットワークでのリモート印刷を可能にします。 PrinterOn は、iOS 向けと Android 向けのどちらの Intune APP SDK とも統合します。 管理コンソールの Intune の **[アプリ保護ポリシー]** ブレードから、アプリ保護ポリシーのターゲットをこのアプリにすることもできます。 エンド ユーザーは、Play ストア、または iTunes から PrinterOn for Microsoft アプリをダウンロードして、Intune エコシステム内で使用できます。

### <a name="approve-the-company-portal-app-for-android-for-work---1797090---"></a>Android for Work のポータル サイト アプリの承認<!--1797090 -->
Android for Work を使用している組織は、Android 用のポータル サイト アプリを手動で承認して、管理された Google Play ストアから引き続き自動更新を受信できるようにする必要があります。

### <a name="faceid-on-ios-devices----1807377---"></a>iOS デバイスの FaceID <!-- 1807377 -->
Intune アプリ保護ポリシーは、iOS デバイスの FaceID を制御する設定をサポートするようになりました。 この設定は、FaceID 機能をサポートするデバイス (現在は iPhone X のみ) 用です。 この設定は、現在サポートされている TouchID コントロールとは異なります。 組織は、TouchID コントロールの代替として有効な PIN プロンプトとして FaceID を信頼するかどうかを選択することができます。

### <a name="microsoft-graph-api-for-intune---general-availability-----1833289---"></a>Intune の Microsoft Graph API - 一般提供開始  <!-- 1833289 -->
Microsoft Graph の Intune API では、データやメソッドに対してプログラムによってアクセスし、Intune サービスの管理操作を自動化することができます。  この API の**一般提供**開始に伴い、ユーザー、パートナー、および開発者の皆様は、この API を活用して、Intune や、Microsoft Graph で利用可能なその他の Microsoft サービスのサポートと関係のある、またはそのようなサービスのサポートを必要とする、社内のソリューション、または市販のソリューションと統合できます。

<!-- the following are present prior to 1801 -->

### <a name="app-protection-policies-----679615---"></a>アプリ保護ポリシー  <!-- 679615 -->
Intune App Protection ポリシーは、既定のグローバル ポリシーを作成し、テナント全体のすべてのユーザーに保護をすばやく適用する機能を提供します。

### <a name="revoking-ios-volume-purchase-program-apps-----820863---"></a>iOS Volume-Purchase Program アプリの取り消し  <!-- 820863 -->
1 つ以上の iOS Volume-Purchase Program (VPP) アプリがインストールされた特定のデバイスでは、そのデバイスで関連付けられているデバイス ベース アプリのライセンスを取り消すことができます。 アプリのライセンスを取り消しても、関連する VPP アプリがデバイスからアンインストールされるわけではありません。 VPP アプリをアンインストールするには、割り当てアクションを **[アンインストール]** に変更する必要があります。 詳細については、「[Volume Purchase Program で購入した iOS アプリを Microsoft Intune で管理する方法](vpp-apps-ios.md)」をご覧ください。

### <a name="revoke-licenses-for-an-ios-volume-purchasing-program-token----820870---"></a>iOS Volume Purchasing Program トークンのライセンスの取り消し <!-- 820870 -->
特定の VPP トークンのすべての iOS Volume Purchasing Program (VPP) アプリのライセンスを取り消すことができます。

### <a name="new-ios-device-action------1244701---"></a>新しい iOS デバイス アクション <!-- 1244701 -->
iOS 10.3 監視下のデバイスをシャット ダウンできます。 このアクションでは、エンド ユーザーへの警告なしにデバイスが即時シャットダウンされます。 **シャット ダウン (監視モードのみ)** アクションは、**デバイス** ワークロードでデバイスを選択した場合に、デバイス プロパティに表示されます。

### <a name="intune-provides-the-account-move-operation-----1573558-1579830---"></a>Intune でアカウントの移動操作を使用できます <!-- 1573558, 1579830 -->
**アカウントの移動**を行うと、Azure スケール ユニット (ASU) 間でテナントが移動します。 お客様が Intune サポート チームに連絡してアカウントの移動をリクエストする、お客様が開始するシナリオと、Microsoft でバックエンドでのサービスの調整が必要な、Microsoft 主導のシナリオの両方で**アカウントの移動**を使用できます。 **アカウントの移動**中は、テナントは読み取り専用モード (ROM) になります。 ROM 期間中は、デバイスの登録や名前変更、コンプライアンス状態の更新などのサービス操作が失敗します。



<!-- the following are present prior to 1712 -->
### <a name="assign-office-365-mobile-apps-to-ios-and-android-devices-using-built-in-app-type----1332318---"></a>組み込み型のアプリを利用し、iOS デバイスまたは Android デバイスに Office 365 モバイル アプリを割り当てる <!-- 1332318 -->
**組み込み**型のアプリであれば、Office 365 アプリを作成し、管理している iOS または Android デバイスに割り当てることが簡単にできます。 これらのアプリには、Word、Excel、PowerPoint、OneDrive などの 0365 アプリがあります。 アプリの種類に特定のアプリを割り当て、アプリ情報構成を編集できます。

### <a name="assignment-conflict-resolution-has-changed-for-ios-store-apps----1480316---"></a>iOS ストア アプリに関して、割り当て競合の解決が変更されました <!-- 1480316 -->
iOS ストア アプリの入手可能性に関して、変更の影響をエンド ユーザーが受ける可能性があります。 現在のところ、**[Required and Available]\(必須で利用可能\)** と **[適用できません]** で競合する 2 つのグループに割り当てられているアプリは **[Required and Available]\(必須で利用可能\)** に解決されます。 今回の変更で、このような競合が発生していたアプリが **[適用できません]** に解決されるようになります。

この変更は、アプリの意図が異なる複数のグループに 1 つのアプリが割り当てられるときの混乱に対処するものです。

11 月のサービス リリースの前に Information Worker Portal とポータル サイトでアプリを利用できるようにする場合、2 つの選択肢があります。

1. グループの **[適用できません]** 割り当てを削除します。
2. **[Required and Available]\(必須で利用可能\)** が割り当てられているメンバーが含まれない新しいグループを作成し、そのグループに **[適用できません]** を割り当てます。

詳細については、「[How to assign apps to groups with Microsoft Intune](apps-deploy.md)」 (Microsoft Intune を使ってアプリをグループに割り当てる方法) を参照してください。

> [!Note]
> リリース後、Intune クラシック コンソールでは、Mobile Device Management (MDM) アプリ割り当てを表示したり、変更したりできなくなります。 ただし、Azure コンソールまたは Intune Graph API を利用してアプリを割り当てることができます。

### <a name="configure-an-ios-app-pin----1586774---"></a>iOS アプリ PIN を構成する <!-- 1586774 -->
間もなく、対象の iOS アプリで PIN を要求できるようになります。 Azure Portal で PIN 要件と有効期限 (日数) を構成できます。 必須にすると、iOS アプリにアクセスする前に、新しい PIN を設定して使用するようにユーザーが要求されます。 Intune App SDK によるアプリ保護を有効にしている iOS アプリでのみこの機能がサポートされます。

### <a name="user-experience-update-for-the-company-portal-app-for-ios---1412866--"></a>iOS 用ポータル サイト アプリに関するユーザー エクスペリエンスの更新プログラム <!--1412866-->

iOS 用のポータル サイト アプリに対して、主要なユーザー エクスペリエンスの更新プログラムをリリースする予定です。 この更新プログラムは、新しいルック アンド フィール、使いやすさとアクセシビリティの向上を含め、ビジュアル デザインの刷新が特徴です。 現在の iOS ポータル サイト機能はすべて維持されます。

お客様がフィードバックを使用および送信できるように、Apple TestFlight プログラムを使用して iOS 用の更新されたポータル サイト アプリのプレリリース バージョンを提供しています。 TestFlight にアクセスするには、https://aka.ms/intune_ios_cp_testflight にサインアップしてください。 

![新しい iOS ポータル サイト アプリのティーザー画像](./media/ios-cp-app-redesign-1801-teaser.png)

<!-- the following are present prior to 1711 -->

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Azure Active Directory の Web サイトでは、Intune Managed Browser アプリを要求し、Managed Browser (パブリック プレビュー) に対するシングル サインオンをサポートすることができる <!-- 710595 -->   
Azure Active Directory (Azure AD) を使っている場合、モバイル デバイスでの Web サイトへのアクセスを、Intune Managed Browser アプリに制限することができます。 Managed Browser では、Web サイトのデータは安全性を維持され、エンド ユーザーの個人データと分離されます。 さらに、Managed Browser は、Azure AD によって保護されているサイトに対するシングル サインオン機能をサポートします。 Managed Browser にサインインすると、または Intune によって管理されている別のアプリでデバイスの Managed Browser を使うと、ユーザーが資格情報を入力しなくても、Managed Browser は Azure AD によって保護されている会社サイトにアクセスできます。 この機能は、Outlook Web Access (OWA) や SharePoint Online などのサイトだけでなく、Azure App プロキシ経由でアクセスされるイントラネット リソースのような他の企業サイトにも適用されます。

<!-- the following are present prior to 1711 -->

### <a name="redirecting-macos-users-to-our-new-company-portal-app---1380728--"></a>新しいポータル サイト アプリへの macOS ユーザーのリダイレクト<!--1380728-->   
エンド ユーザーは、ポータル サイトの Web サイトにログインして macOS デバイスを登録するとき、プロセスを完了するために macOS 用の新しいポータル サイト アプリをダウンロードするように指示されます。 これは、OS X El Capitan 10.11 以降を使っている macOS デバイスの場合に発生します。 


<!-- the following are present prior to 1709 -->

### <a name="intune-managed-browser-support-for-ios-and-android----1374196---"></a>iOS および Android <!-- 1374196 --> 用の Intune Managed Browser のサポート
2017 年 10 月の時点で、Android アプリで使用する Intune Managed Browser アプリは、Android 4.4 以降を実行しているデバイスのみをサポートします。 iOS の Intune Managed Browser アプリは、iOS 9.0 以降を実行しているデバイスのみをサポートします。 以前のバージョンの Android および iOS は、Managed Browser の使用を続けることができますが、新しいバージョンのアプリをインストールすることはできません。また、アプリのすべての機能にアクセスできるとは限りません。 サポートされるオペレーティング システム バージョンにこれらのデバイスを更新することをお勧めします。

### <a name="improved-error-message-for-when-a-user-reaches-the-maximum-number-of-devices-allowed-to-enroll----1270370---"></a>ユーザーが登録できるデバイスの最大数に達したときのエラー メッセージの向上<!-- 1270370 -->
Android デバイスのエンド ユーザーに対して、一般的なエラー メッセージでなく、「IT 管理者が許可している数よりも多くのデバイスが登録されています。登録したデバイスを削除するか、IT 管理者に支援を求めてください。」という分かりやすい、実践的なエラー メッセージが表示されるようになりました。



## <a name="notices"></a>通知

現在のところ、アクティブな通知はありません。



### <a name="see-also"></a>関連項目
最近の開発状況について詳しくは、「[Microsoft Intune の新機能](whats-new.md)」をご覧ください。


