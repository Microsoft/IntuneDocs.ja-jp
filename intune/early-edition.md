---
title: 初期エディション
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 99b1436fdf718b54f54f7e90835668d4a632b7ce
ms.sourcegitcommit: 390a4be5aa36007c36fb6a5abcfe8d20bc862a4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2018
---
# <a name="the-early-edition-for-microsoft-intune---march-2018"></a>Microsoft Intune の初期エディション - 2018 年 3 月

**初期エディション**では、Microsoft Intune の今後のリリースで予定されている新機能の一覧を提供しています。 ここに記載されている情報は、限られた範囲について開示されたものであり、また今後変更される可能性があります。 社外ではこの情報を共有しないでください。 ここに挙げられている機能は、発売日に間に合わない可能性があり、その場合は将来のリリースを待たなければなりません。 正式なリリースに向けてパイロット (フライト) テスト中の機能もあります。 ご不明な点や懸念される事項がある場合は、Microsoft 製品グループにお問い合わせください。

このページは定期的に更新されます。 適宜確認してください。

> [!Note]
>Intune に関して以下の機能が現在開発されています。 新しいハイブリッド機能については、[ハイブリッド環境の新機能](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)に関するページをご覧ください。

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->

## <a name="intune-in-the-azure-portal"></a>Azure Portal での Intune

<!-- 1803 start -->

#### <a name="multiple-exchange-connector-support----2070451---"></a>複数の Exchange Connector のサポート <!-- 2070451 -->

テナントごとの Microsoft Intune Exchange Connector の数が 1 個だけという制限がなくなりました。 Intune は複数の Exchange Connector をサポートするようになるので、複数のオンプレミス Exchange の組織で Intune の条件付きアクセスを設定できます。

Intune のオンプレミス Exchange Connector を使うと、デバイスが Intune に登録されているかどうか、およびデバイスが Intune のデバイス コンプライアンス ポリシーに準拠しているかどうかに基づいて、お使いのオンプレミスの Exchange メールボックスに対するデバイス アクセスを管理できます。 コネクタを設定するには、Azure Portal から Intune のオンプレミス Exchange Connector をダウンロードして、Exchange の組織内のサーバーにインストールします。 Microsoft Intune ダッシュ ボードで **[オンプレミス アクセス]** を選択し、**[セットアップ]** で **[Exchange ActiveSync のコネクタ]** を選択します。 Exchange のオンプレミス コネクタをダウンロードし、Exchange の組織内のサーバーにインストールします。 テナントごとに 1 個という Exchange Connector の制限がなくなったので、他に Exchange の組織がある場合は、他の各 Exchange の組織にも同じ手順でコネクタをダウンロードしてインストールできます。

### <a name="support-coming-for-new-cisco-anyconnect-client-for-ios----1333708---"></a>iOS 用の新しい Cisco AnyConnect クライアントのサポート <!-- 1333708 -->

iOS 用の Cisco AnyConnect 向けに作成された新しい VPN プロファイルが、Cisco AnyConnect 4.0.7x 以降で動作するようになります。 既存の iOS Cisco AnyConnect VPN プロファイルは **[Cisco Legacy AnyConnect]** と表示されるようになり、現在と同じように Cisco AnyConnect 4.0.5x で引き続き動作します。

> [!NOTE]
> この変更は iOS に対してのみ有効です。Android、Android for Work、macOS の Cisco AnyConnect オプションは、これまでどおり 1 つだけです。

#### <a name="more-information"></a>詳細情報

新しい Cisco AnyConnect アプリと Cisco Legacy AnyConnect アプリは異なるアプリなので、新しいアプリをサポートするには、新しい iOS Cisco AnyConnect VPN プロファイルを作成する必要があります。 環境内の AnyConnect クライアントを管理している場合は、新しい Cisco AnyConnect アプリを展開する必要もあります。 アップグレードを完了するには、Cisco Legacy AnyConnect VPN プロファイルを削除し、Cisco Legacy AnyConnect アプリを除去する必要もあります。

ネットワーク アクセス制御 (NAC) の統合は、新しい AnyConnect クライアントの初期リリースでは機能しません。 Intune の今後のリリースで NAC 統合を提供できるように、Cisco と協力しています。

### <a name="enhanced-jailbreak-detection----846515---"></a>脱獄の検出の機能強化 <!-- 846515 -->

強化された脱獄の検出の新しいコンプライアンス設定により、Intune による脱獄されたデバイスの評価方法が向上します。 この設定では、デバイスはこれまでより頻繁に Intune にチェックインされ、このときデバイスの場所サービスを使うので、バッテリの使用量に影響を与えます。

### <a name="ability-to-deploy-required-line-of-business-lob-apps-to-all-users-on-windows-10-desktop-devices----1627835-rs4---"></a>Windows 10 デスクトップ デバイスのすべてのユーザーに対して必要な基幹業務 (LOB) アプリを展開する機能 <!-- 1627835 RS4 -->
お客様は、必要な基幹業務 Windows 10 アプリを展開してデバイス コンテキストにインストールできるようになります。 これにより、デバイスのすべてのユーザーがこれらのアプリを使用できるようになります。 対象は Windows 10 デスクトップ デバイスだけです。

### <a name="expiring-line-of-business-lob-apps-for-microsoft-intune----748789---"></a>Microsoft Intune 用の基幹業務 (LOB) アプリの有効期限切れ <!-- 748789 -->
Azure Portal の Intune では、有効期限が近づいている基幹業務アプリが警告されます。 基幹業務アプリの新しいバージョンをアップロードすると、Intune は有効期限に関する通知をアプリの一覧から削除します。

### <a name="company-portal-enrollment-improved----1874230--"></a>会社ポータルの登録の機能強化 <!-- 1874230-->
Windows 10 ビルド 1703 以降の Intune ポータル サイトを使ってデバイスを登録するユーザーは、アプリを離れることなく登録の最初の手順を完了できます。

### <a name="new-management-name-column----1333586---"></a>新しい [管理名] 列 <!-- 1333586 -->
**[管理名]** という名前の新しい列がデバイス ブレードに追加されます。 これは、次の式に基づいてデバイスごとに割り当てられる、自動生成された編集不可能な名前です。
- すべてのデバイスの既定の名前: <username>_<devicetype>_<enrollmenttimestamp>
- 一括追加デバイスの場合: <PackageId/ProfileId>_<DeviceType>_<EnrollmentTime>

これは、デバイス ブレードの省略可能な列です。 既定では使用できず、列セレクターからのみアクセスできます。 この新しい列によるデバイス名への影響はありません。

### <a name="new-settings-for-windows-defender-security-center-notifications-device-configuration-profile----1631906---"></a>Windows Defender セキュリティ センター通知デバイス構成プロファイルの新しい設定 <!-- 1631906 -->

Windows Defender セキュリティ センター (WDSC) 通知デバイス構成プロファイルに新しい設定が 3 つ追加されます。

管理者は次のことができます。

- ID ピラーを非表示にする
- ハードウェア ピラーとその下位設定を非表示にする
- ランサムウェア ピラーを非表示にする (OneDrive for Business ファイルの復元)

これらのピラーを WDSC アプリから非表示にすると、エンド ユーザーはこれらの設定を構成できなくなり、非表示のコンポーネントに関連するすべての通知は生成されません。

### <a name="mam-policies-targeted-based-on-management-state----1665993---"></a>管理の状態に基づいて対象を指定される MAM ポリシー <!-- 1665993 -->

デバイスの管理の状態に基づいて、MAM ポリシーの対象を設定できるようになります。

- **iOS デバイス** - 管理されていないデバイス (MAM のみ) または Intune で管理されたデバイスを対象にできます。
- **Android デバイス** - 管理されていないデバイス、Intune で管理されたデバイス、Intune で管理された Android Enterprise Profiles (旧称 Android for Work) を対象にできます。

### <a name="configure-gatekeeper-to-control-macos-app-download-source----1690459--"></a>macOS アプリ ダウンロード ソースを制御するための Gatekeeper の構成 <!-- 1690459-->

ダウンロードできるアプリの場所を制御することでアプリからデバイスを保護するように、Gatekeeper を構成することができます。 構成できるダウンロード ソースは、**[Mac App Store]**、**[Mac App Store と識別された開発者]**、または **[どこでも]** です。 また、ユーザーが Ctrl キーを押しながらクリックしてアプリをインストールすることによりこれらの Gatekeeper 制御を無効にできるかどうかも構成できます。

これらの設定は、**[デバイス構成]** -> **[プロファイルの作成]** -> **[macOS]** -> **[Endpoint Protection]** にあります。

### <a name="configure-the-mac-application-firewall----1690461---"></a>Mac アプリケーションのファイアウォールの構成 <!-- 1690461 -->

Mac アプリケーションのファイアウォールを構成することができます。 これを使って、ポートごとではなく、アプリケーションごとに接続を制御できます。 これにより、ファイアウォールによる保護を簡単に利用できるようになり、正当なアプリ用に開かれているネットワーク ポートを望ましくないアプリが制御するのを防ぐのに役立ちます。

この設定は、**[デバイス構成]** -> **[プロファイルの作成]** -> **[macOS]** -> **[Endpoint Protection]** にあります。

ファイアウォールの設定を有効にすると、2 つの戦略を使ってファイアウォールを構成できます。

- すべての着信接続をブロックする

   対象デバイスに対するすべての着信接続をブロックすることができます。 この方法を選択した場合、すべてのアプリの着信接続がブロックされます。

- 特定のアプリを許可またはブロックする

   特定のアプリからの着信接続の受信を許可またはブロックできます。 ステルス モードを有効にして、プローブ要求への応答を防ぐこともできます。

#### <a name="more-information"></a>詳細情報

- すべての着信接続をブロックする

   すべての共有サービス (ファイル共有や画面共有など) が着信接続を受信するのをブロックします。 その場合でも、次のシステム サービスは着信接続を受信できます。
   - configd - DHCP および他のネットワーク構成サービスを実装します
   - mDNSResponder - Bonjour を実装します
   - racoon - IPSec を実装します

   共有サービスを使うには、**[着信接続]** を (**[ブロック]** ではなく) **[未構成]** に設定します。

- ステルス モード

   これを有効にすると、コンピューターはプローブ要求に応答しなくなります。 その場合でも、コンピューターは承認されたアプリの着信要求には応答します。 ICMP (ping) などの予期しない要求は無視されます。


### <a name="updating-the-help-and-feedback-experience-on-company-portal-app-for-android---1631531---"></a>Android 用 Intune ポータル サイト アプリでのヘルプとフィードバックのエクスペリエンスの更新 <!--1631531 -->

Android アプリのベスト プラクティスに合うように、Android 用 Intune ポータル サイト アプリのヘルプとフィードバックのエクスペリエンスが更新されます。 今後数か月かけて Android 用 Intune ポータル サイト アプリが更新され、**[ヘルプとフィードバック]** メニュー項目が **[ヘルプ]** と **[フィードバックの送信]** の異なるメニュー項目に分割されます。 **[ヘルプ]** ページには **[よく寄せられる質問]** セクションと **[メールでサポートに問い合わせる]** ボタンがあり、エンド ユーザーは Microsoft にログをアップロードしたり、会社のサポート部門に問題を説明するメールを送信したりできます。 **[フィードバックの送信]** では Microsoft の標準的なフィードバック送信を利用でき、"気に入った機能"、"気に入らない機能"、"アイデア" を選択できます。

### <a name="custom-book-categories-for-volume-purchase-program-vpp-ebooks----1488911---"></a>ボリューム購入プログラム (VPP) 電子ブックのカスタム ブック カテゴリ <!-- 1488911 -->
電子ブックのカスタム カテゴリを作成し、VPP の電子ブックをカスタム電子ブック カテゴリに割り当てることができます。 エンド ユーザーは、新しく作成された電子ブック カテゴリとそのカテゴリに割り当てられているブックを見ることができます。

### <a name="hololens-and-surface-hub-now-appear-in-device-lists---1725868--"></a>HoloLens と Surface Hub がデバイス リストに表示されるようになった <!--1725868-->

Intune に登録された HoloLens および Surface Hub のデバイスを Android 用ポータル サイト アプリに表示するためのサポートが追加されています。

### <a name="edge-mobile-support-for-intune-app-protection-policies----1817882---"></a>Edge モバイルでの Intune アプリ保護ポリシーのサポート <!-- 1817882 -->

モバイル デバイス向けの Microsoft Edge ブラウザーで、Intune で定義されるアプリ保護ポリシーがサポートされます。

### <a name="use-fully-distinguished-name-as-subject-for-scep-certificate---2221763-eeready--"></a>SCEP 証明書のサブジェクトとして完全な識別名を使用する <!--2221763 eeready-->
SCEP 証明書プロファイルを作成するときには、サブジェクト名を入力します。 サブジェクト名として、完全な識別名を使用できるようになります。 **サブジェクト名**に対して **[カスタム]** を選択し、`CN={{OnPrem_Distinguished_Name}}` と入力します。 `{{OnPrem_Distinguished_Name}}` 変数を使用するには、[Azure Active Directory (AD) Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) を使用して、`onpremisesdistingishedname` ユーザー属性を Azure AD と同期させます。

### <a name="ios-devices-are-prompted-for-a-pin-every-15-minutes---1550837-eeready--"></a>iOS デバイスで 15 分ごとに PIN の入力を求める <!--1550837 eeready-->
iOS デバイスにコンプライアンスまたは構成ポリシーが適用されると、ユーザーは 15 分ごとに PIN を設定するように求められます。 PIN を設定するまで継続してユーザーは入力を求められます。

### <a name="enable-bluetooth-contact-sharing---android-for-work---1098983-eeready--"></a>Bluetooth での連絡先の共有の有効化 - Android for Work <!--1098983 eeready-->
Android の既定では、仕事用プロファイルの連絡先が Bluetooth デバイスと同期することはできません。 その結果、Bluetooth デバイスに対して、仕事用プロファイルの連絡先が発信者 ID に表示されません。

**[Android for Work]** > **[デバイスの制限]** > **[仕事用プロファイルの設定]** に、次の新しい設定が表示されます。
- Bluetooth 経由での連絡先の共有

Intune の管理者は、これらの設定を構成して共有を有効にできます。 これは、デバイスを、ハンズフリー使用のために発信者 ID を表示する、車を拠点とする Bluetooth デバイスとペアリングする場合に便利です。 有効にすると、仕事用プロファイルの連絡先が表示されます。 無効にすると、仕事用プロファイルの連絡先は表示されません。

適用対象: Android OS v6.0 以降の Android 仕事用プロファイル デバイス。

### <a name="schedule-your-automatic-updates---1805514---"></a>自動更新スケジュールの設定 <!--1805514 -->

Intune では、[Windows Update リングの設定](windows-update-for-business-configure.md)を使用して、自動更新のインストールを制御することができます。 週、日、時刻などを指定して、繰り返し更新が発生するようスケジュールすることができます。

### <a name="disable-checks-on-device-restart---1805490---"></a>デバイス再起動時のチェックの無効化 <!--1805490 -->

Intune によって[ソフトウェア更新プログラムの管理](windows-update-for-business-configure.md)を制御することができます。 **再起動チェック** プロパティが追加され、既定で有効になります。 デバイスを再起動する際に発生する一般的なチェック (アクティブなユーザー、バッテリのレベルなど) をスキップするには、**[スキップ]** を選択します。

<!-- 1802 start -->

### <a name="new-enrollment-failure-trend-chart-and-failure-reasons-table----1471783---"></a>新しい登録エラー傾向グラフと失敗の理由テーブル <!-- 1471783 -->

[Enrollment Overview]\(登録の概要\) ページで、登録エラーの傾向と、上位 5 つのエラーの原因を表示することができます。 グラフやテーブルをクリックすると、トラブルシューティングのアドバイスや改善の提案の詳細にドリル ダウンすることができます。

### <a name="customize-your-company-portal-themes-with-hex-codes---1049561---"></a>Intune ポータル サイトのテーマを 16 進コードでカスタマイズする <!--1049561 -->

Intune ポータル サイト アプリのテーマの色を、16 進コードを使ってカスタマイズできます。 16 進コードを入力すると、Intune は、[WCAG 2.0 標準](http://www.w3.org/TR/WCAG20)に従って、テキストの色と背景の色の間のコントラストが最高レベルになるようにテキストの色を決定します。 **[Mobile Apps]** > **[ポータル サイト]** で、テキストの色および色に対する会社のロゴの両方をプレビューできます。

### <a name="new-windows-defender-credential-guard-settings-added-to-endpoint-protection-settings---1102252---"></a>Endpoint Protection の設定に追加された新しい Windows Defender Credential Guard の設定<!--1102252 -->

新しい [Windows Defender Credential Guard](https://docs.microsoft.com/windows/access-protection/credential-guard/credential-guard] 設定が、**[デバイス構成]** > **[プロファイル]** > **[Endpoint Protection]** に追加されます。 次の設定が追加されます。

- プラットフォームのセキュリティ レベル: 次の再起動時にプラットフォームのセキュリティ レベルを有効にするかどうかを指定します。 仮想化ベースのセキュリティには、セキュア ブートが必要です。 仮想化ベースのセキュリティは、ダイレクト メモリ アクセス (DMA) 保護を使って、必要に応じて有効にすることができます。 DMA 保護は、ハードウェアのサポートを必要とし、正しく構成されたデバイスでのみ有効にされます。
- 仮想化ベースのセキュリティ: 次の再起動時に仮想化ベースのセキュリティを有効にするかどうかを指定します。
- Windows Defender Credential Guard: プラットフォームのセキュリティ レベルとセキュア ブートおよび仮想化ベースのセキュリティがどちらも有効な次の再起動時に、仮想化ベースのセキュリティで Credential Guard を有効にして資格情報を保護します。 使用できるオプションは、**[無効]**、**[UEFI ロックで有効化]**、**[ロックなしで有効化]**、**[未構成]** です。
  - [無効] オプションは、以前に Credential Guard が [ロックなしで有効化] オプションで有効になっていた場合に、Credential Guard をリモートで無効にします。

  - [UEFI ロックで有効化] オプションは、レジストリ キーまたはグループ ポリシーを使って Credential Guard を無効にできないようにします。 この設定を使った後で Credential Guard を無効にするには、グループ ポリシーを "無効" に設定し、ユーザーが直接各コンピューターからセキュリティ機能を削除して、UEFI に保持されている構成をクリアする必要があります。 UEFI の構成が保持されている限り、Credential Guard は有効になっています。

  - [ロックなしで有効化] オプションは、グループ ポリシーを使ってリモートで Credential Guard を無効にできるようにします。 この設定を使うデバイスは、Windows 10 (バージョン 1511) 以降を実行している必要があります。

  - [未構成] オプションは、ポリシー設定を未定義のままにします。 グループ ポリシーはレジストリにポリシー設定を書き込まないので、コンピューターまたはユーザーに影響はありません。 現在レジストリ内の設定がある場合、それは変更されません。

### <a name="reset-passwords-for-android-o-devices----1238299---"></a>Android O デバイスのパスワードをリセットする <!-- 1238299 -->
登録済みの Android O デバイスのパスワードをリセットできるようになります。 Android O デバイスに "パスワード リセット" 要求を送信すると、新しいデバイス ロック解除パスワードまたはマネージ プロファイルのチャレンジが、現在のユーザーに設定されます。 パスワードまたはチャレンジは、デバイスにプロファイル所有者またはデバイス所有者がいるかどうかに基づいて送信され、すぐに有効になります。

### <a name="local-device-security-option-settings----1251887---"></a>ローカル デバイス セキュリティ オプションの設定 <!-- 1251887 -->
新しいローカル デバイス セキュリティ オプションの設定を使って、Windows 10 デバイスのセキュリティ設定を有効にできます。 これらの設定は、Windows 10 デバイスの構成ポリシーを作成するときに、[Endpoint Protection] カテゴリに表示されます。

### <a name="new-printer-settings-for-education-profiles----1308900---"></a>教育プロファイル用の新しいプリンター設定 <!-- 1308900 -->

教育プロファイルの場合、**[プリンター]** カテゴリで新しい設定 **[プリンター]**、**[通常使うプリンター]**、**[新しいプリンターの追加]** を利用できます。

### <a name="ios-app-provisioning-configuration----1581650---"></a>iOS アプリのプロビジョニングの構成 <!-- 1581650 -->
iOS アプリにプロビジョニング プロファイルを割り当てて、セキュリティ グループを包含または除外することで、アプリが期限切れにならないようにすることができます。

### <a name="new-windows-defender-application-guard-settings----1631890---"></a>Windows Defender Application Guard の新しい設定 <!-- 1631890 -->

- **Enable graphics acceleration (グラフィック アクセラレータを有効にする)**

管理者は、Windows Defender Application Guard の仮想グラフィック プロセッサを有効にすることができます。 この設定を使うと、CPU はグラフィックのレンダリングを vGPU にオフロードできます。 これにより、グラフィックが多用されている Web サイトを操作するとき、またはコンテナー内のビデオを見るときのパフォーマンスが向上します。

- **SaveFilestoHost**

管理者は、コンテナーで実行されている Microsoft Edge からホスト ファイル システムへのファイルの受け渡しを有効にすることができます。 これをオンにすると、ユーザーは、コンテナー内の Microsoft Edge からホスト ファイル システムにファイルをダウンロードできます。

### <a name="including-and-excluding-app-assignment-based-on-groups-for-android-enterprise----1813081---"></a>Android Enterprise に対するグループに基づくアプリ割り当ての追加と除外 <!-- 1813081 -->
Android Enterprise (旧称 Android for Work) は、アプリの割り当て中、および割り当て種類の選択後の除外機能をサポートします。

<!-- the following are present prior to 1802 -->

### <a name="targeting-compliance-policies-to-devices-in-device-groups---1307012---"></a>デバイス グループのデバイスへのコンプライアンス ポリシーのターゲット<!--1307012 -->

ユーザー グループ内のユーザーを、コンプライアンス ポリシーのターゲットにできます。 デバイス グループ内のデバイスを、コンプライアンス ポリシーのターゲットにできます。

<!-- the following are present prior to 1801 -->

### <a name="app-protection-policies-----679615---"></a>アプリ保護ポリシー  <!-- 679615 -->
Intune App Protection ポリシーは、既定のグローバル ポリシーを作成し、テナント全体のすべてのユーザーに保護をすばやく適用する機能を提供します。

### <a name="configure-an-ios-app-pin----1586774---"></a>iOS アプリ PIN を構成する <!-- 1586774 -->
間もなく、対象の iOS アプリで PIN を要求できるようになります。 Azure Portal で PIN 要件と有効期限 (日数) を構成できます。 必須にすると、iOS アプリにアクセスする前に、新しい PIN を設定して使用するようにユーザーが要求されます。 Intune App SDK によるアプリ保護を有効にしている iOS アプリでのみこの機能がサポートされます。

<!-- the following are present prior to 1711 -->

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Azure Active Directory の Web サイトでは、Intune Managed Browser アプリを要求し、Managed Browser (パブリック プレビュー) に対するシングル サインオンをサポートすることができる <!-- 710595 -->   
Azure Active Directory (Azure AD) を使っている場合、モバイル デバイスでの Web サイトへのアクセスを、Intune Managed Browser アプリに制限することができます。 Managed Browser では、Web サイトのデータは安全性を維持され、エンド ユーザーの個人データと分離されます。 さらに、Managed Browser は、Azure AD によって保護されているサイトに対するシングル サインオン機能をサポートします。 Managed Browser にサインインすると、または Intune によって管理されている別のアプリでデバイスの Managed Browser を使うと、ユーザーが資格情報を入力しなくても、Managed Browser は Azure AD によって保護されている会社サイトにアクセスできます。 この機能は、Outlook Web Access (OWA) や SharePoint Online などのサイトだけでなく、Azure App プロキシ経由でアクセスされるイントラネット リソースのような他の企業サイトにも適用されます。

<!-- the following are present prior to 1711 -->

### <a name="redirecting-macos-users-to-the-new-company-portal-app---1380728--"></a>新しいポータル サイト アプリへの macOS ユーザーのリダイレクト<!--1380728-->   
エンド ユーザーは、ポータル サイトの Web サイトにログインして macOS デバイスを登録するとき、プロセスを完了するために macOS 用の新しいポータル サイト アプリをダウンロードするように指示されます。 これは、OS X El Capitan 10.11 以降を使っている macOS デバイスの場合に発生します。 

<!-- the following are present prior to 1709 -->

### <a name="improved-error-message-for-when-a-user-reaches-the-maximum-number-of-devices-allowed-to-enroll----1270370---"></a>ユーザーが登録できるデバイスの最大数に達したときのエラー メッセージの向上<!-- 1270370 -->
Android デバイスのエンド ユーザーに対して、一般的なエラー メッセージでなく、「IT 管理者が許可している数よりも多くのデバイスが登録されています。登録したデバイスを削除するか、IT 管理者に支援を求めてください。」という分かりやすい、実践的なエラー メッセージが表示されるようになりました。



## <a name="notices"></a>通知

現在のところ、アクティブな通知はありません。



### <a name="see-also"></a>関連項目
最近の開発状況について詳しくは、「[Microsoft Intune の新機能](whats-new.md)」をご覧ください。
