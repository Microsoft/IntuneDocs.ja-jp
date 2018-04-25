---
title: 初期エディション
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/03/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: b6ca8108924c6c062da0d0ef56ab5b68635dd9ca
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="the-early-edition-for-microsoft-intune---april-2018"></a>Microsoft Intune の初期エディション - 2018 年 4 月

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

<!-- 1804 start -->

### <a name="new-windows-defender-credential-guard-settings-added-to-endpoint-protection-settings---1102252-----from-1802--"></a>Endpoint Protection の設定に追加された新しい Windows Defender Credential Guard の設定 <!--1102252 --><!--from 1802-->

新しい [Windows Defender Credential Guard](https://docs.microsoft.com/windows/access-protection/credential-guard/credential-guard) 設定が、**[デバイス構成]** > **[プロファイル]** > **[Endpoint Protection]** に追加されます。 次の設定が追加されます。

- プラットフォームのセキュリティ レベル: 次の再起動時にプラットフォームのセキュリティ レベルを有効にするかどうかを指定します。 仮想化ベースのセキュリティには、セキュア ブートが必要です。 仮想化ベースのセキュリティは、ダイレクト メモリ アクセス (DMA) 保護を使って、必要に応じて有効にすることができます。 DMA 保護は、ハードウェアのサポートを必要とし、正しく構成されたデバイスでのみ有効にされます。
- 仮想化ベースのセキュリティ: 次の再起動時に仮想化ベースのセキュリティを有効にするかどうかを指定します。
- Windows Defender Credential Guard: プラットフォームのセキュリティ レベルとセキュア ブートおよび仮想化ベースのセキュリティがどちらも有効な次の再起動時に、仮想化ベースのセキュリティで Credential Guard を有効にして資格情報を保護します。 使用できるオプションは、**[無効]**、**[UEFI ロックで有効化]**、**[ロックなしで有効化]**、**[未構成]** です。
  - [無効] オプションは、以前に Credential Guard が [ロックなしで有効化] オプションで有効になっていた場合に、Credential Guard をリモートで無効にします。

  - [UEFI ロックで有効化] オプションは、レジストリ キーまたはグループ ポリシーを使って Credential Guard を無効にできないようにします。 この設定を使った後で Credential Guard を無効にするには、グループ ポリシーを "無効" に設定し、ユーザーが直接各コンピューターからセキュリティ機能を削除して、UEFI に保持されている構成をクリアする必要があります。 UEFI の構成が保持されている限り、Credential Guard は有効になっています。

  - [ロックなしで有効化] オプションは、グループ ポリシーを使ってリモートで Credential Guard を無効にできるようにします。 この設定を使うデバイスは、Windows 10 (バージョン 1511) 以降を実行している必要があります。

  - [未構成] オプションは、ポリシー設定を未定義のままにします。 グループ ポリシーはレジストリにポリシー設定を書き込まないので、コンピューターまたはユーザーに影響はありません。 現在レジストリ内の設定がある場合、それは変更されません。

### <a name="passcode-support-for-mam-pin-on-android---1438086---"></a>Android での MAM PIN のパスコードのサポート<!-- 1438086 -->

Intune 管理者は、アプリケーション起動要件を設定して、数値の MAM PIN の代わりにパスコードを強制することができます。 構成した場合、ユーザーは、MAM 対応のアプリケーションにアクセスする前に、要求された時点で、パスコードを設定および使用する必要があります。 パスコードは、少なくとも 1 つの特殊文字または大文字/小文字アルファベットを含む数値 PIN と定義されます。 Intune によるパスコードのサポート方法は既存の数値 PIN と似ており、管理コンソールで最小の長さを設定したり、文字やシーケンスの繰り返しを許可したりできます。 この機能を利用するには、Android に最新バージョンの Intune ポータル サイトが必要です。 この機能は、iOS では既に利用できます。

###  <a name="block-camera-and-screen-captures-on-android-for-work----1098977-eeready--"></a>Android for Work でカメラと画面キャプチャをブロックする <!-- 1098977 eeready-->
Android デバイスのデバイス制限を構成するときに、2 つの新しいプロパティをブロックに利用できます。 
- カメラ: デバイスのすべてのカメラへのアクセスを禁止します
- 画面キャプチャ: 画面のキャプチャをブロックし、セキュリティで保護されたビデオ出力を持たないディスプレイ デバイスにコンテンツが表示されないようにします

Android for Work に適用されます。

### <a name="line-of-business-lob-app-support-for-macos----1473977---"></a>macOS の基幹業務 (LOB) アプリのサポート <!-- 1473977 -->
Microsoft Intune では、Azure Portal から macOS LOB アプリをインストールできます。 GitHub で利用可能なツールを使って前処理した macOS LOB アプリを、Intune に追加できます。 Azure Portal で、**[Intune]** ブレードから **[Mobile Apps]** を選択します。 **[Mobile Apps]** ブレードで、**[アプリ]** > **[追加]** を選択します。 **[アプリの追加]** ブレードで、**[基幹業務アプリ]** を選択します。 

### <a name="support-for-user-less-devices----1637553---"></a>ユーザーのいないデバイスのサポート <!-- 1637553 -->
Intune は、Microsoft Surface Hub など、ユーザーのいないデバイスでコンプライアンスを評価する機能をサポートします。 コンプライアンス ポリシーは、特定のデバイスを対象にすることができます。 したがって、ユーザーが関連付けられていないデバイスのコンプライアンス (および非コンプライアンス) を判断できます。

### <a name="additions-to-local-device-security-options-settings----1403702---"></a>ローカル デバイス セキュリティ オプションの設定への追加 <!-- 1403702 -->
Windows 10 デバイスに対して追加のローカル デバイス セキュリティ オプションの設定を構成することができます。 追加設定を利用できるのは、Microsoft ネットワーク クライアント、Microsoft ネットワーク サーバー、ネットワーク アクセスとセキュリティ、および対話型ログオンなどに関する部分です。 これらの設定は、Windows 10 デバイスの構成ポリシーを作成するときに、[Endpoint Protection] カテゴリに表示されます。

### <a name="require-installation-of-policies-apps-certificate-and-network-profiles----1553555---"></a>ポリシー、アプリ、証明書、およびネットワーク プロファイルのインストールを必要にする <!-- 1553555 -->
管理者は、AutoPilot デバイスのプロビジョニングの間、Intune がポリシー、アプリ、証明書、ネットワーク プロファイルをインストールするまで、エンド ユーザーによる Windows 10 RS4 デスクトップへのアクセスをブロックすることができます。

### <a name="rules-for-removing-devices----1609459---"></a>デバイス削除のルール <!-- 1609459 -->
設定した日数の間チェックインしていないデバイスを自動的に削除する新しい規則を使用できます。 新しいルールを表示するには、**[Intune]** ウィンドウ、**[デバイス]**、**[Device removal rules]\(デバイス削除ルール\)** の順に選択します。

### <a name="prevent-consumer-apps-and-experiences-on-windows-10-enterprise-rs4-autopilot-devices---1621980---"></a>Windows 10 Enterprise RS4 Autopilot デバイスでのコンシューマー アプリおよびエクスペリエンスの禁止<!-- 1621980 -->
Windows 10 Enterprise RS4 Autopilot デバイスへのコンシューマー アプリおよびエクスペリエンスのインストールを禁止することができます。 この機能を表示するには、**[Intune]** > **[デバイスの登録]** > **[Windows の登録]** > **[Windows AutoPilot profiles]\(Windows AutoPilot プロファイル\)** > **[新規作成]** > **[登録設定]** の順に移動します。 

### <a name="advanced-threat-protection-integrated-with-intune----1629303---"></a>Intune と統合された高度な脅威保護 <!-- 1629303 -->
[Advanced Threat Protection (ATP)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/dashboard-windows-defender-advanced-threat-protection) では、Windows 10 デバイスのリスク レベルが表示されます。 Intune が Windows 10 デバイスのコンプライアンスを評価するときは、ATP リスク スコアがこの評価に含まれます。 条件付きアクセスで ATP を使って、ネットワークの保護を強化できます。

### <a name="new-enrollment-steps-for-users-on-devices-with-macos-high-sierra-10132---1734567---"></a>macOS High Sierra 10.13.2 以降のデバイスでのユーザーの新しい登録手順 <!--1734567 -->
macOS High Sierra 10.13.2 では、"ユーザー承認済み" MDM 登録の概念が導入されました。 今後、承認済みの登録では、セキュリティ上重要な一部の設定の Intune による管理が許可されます。 詳細については、Apple のサポート ドキュメント https://support.apple.com/HT208019 をご覧ください。

macOS ポータル サイトを使って登録されたデバイスは、エンド ユーザーがシステム環境設定を開いて手動で承認しない限り、"ユーザー承認されていない" ものとみなされます。 そのため、macOS ポータル サイトでは、macOS 10.13.2 以降のユーザーは、登録プロセスの最後に、登録の手動承認に移動するようになりました。 Intune 管理コンソールでは、登録されているデバイスがユーザー承認済みかどうかが示されます。

### <a name="delete-autopilot-devices----1713650---"></a>Autopilot デバイスの削除 <!-- 1713650 -->
Intune 管理者は、Autopilot デバイスを削除することができます。

### <a name="built-in-all-users-and-all-devices-group-for-android-for-work-afw-app-assignment----1813073---"></a>Android for Work (AFW) のアプリの割り当てに対する組み込みのすべてのユーザー グループとすべてのデバイス グループ <!-- 1813073 -->
組み込みの**すべてのユーザー** グループと**すべてのデバイス** グループを AFW アプリの割り当てに利用できるようになります。 詳細については、「[Microsoft Intune でのアプリ割り当ての組み込みと除外](apps-inc-exl-assignments.md)」を参照してください。

### <a name="improved-device-deletion-experience---1832333---"></a>デバイス削除エクスペリエンスの向上 <!--1832333 -->
Intune からデバイスを削除する前に、会社のデータを削除したり、デバイスを工場出荷時の状態にリセットしたりする必要はなくなります。

新しいエクスペリエンスを表示するには、Intune にサインインし、**[デバイス]** > **[すべてのデバイス]** > デバイスの名前 > **[削除]** の順に選びます。

 ワイプ/使用停止の確認が必要な場合は、**[削除]** の前に **[会社データを削除する]** と **[出荷時の設定にリセット]** を実行して、標準のデバイス ライフサイクル ルートを使うことができます。 

### <a name="autopilot-profiles-moving-to-group-targeting----1877935---"></a>Autopilot プロファイルの対象がグループに移動 <!-- 1877935 -->
現在は、AutoPilot のデプロイ プロファイルは選択したデバイスに割り当てることができます。 4 月末にかけて、これらのプロファイルの割り当て方法は次のようになります。
- AutoPilot デバイスを含む (Azure AD) グループを作成します
- 目的のプロファイルを Azure AD グループに割り当てます。 AutoPilot プロファイルは、そのグループ内の AutoPilot デバイスに割り当てられるようになります。

### <a name="play-sounds-on-ios-when-in-lost-mode----1629303---"></a>紛失モードになったときに iOS で音を鳴らす <!-- 1629303 -->
監視対象の iOS デバイスがモバイル デバイス管理 (MDM) の[紛失モード](device-lost-mode.md)になったときに、音を鳴らすことができます (**[デバイス]** > **[すべてのデバイス]** > iOS デバイスを選択 > **[概要]** > **[詳細]**)。 音は、デバイスが紛失モードではなくなるまで、またはユーザーがデバイスで音を無効にするまで、鳴り続けます。 iOS デバイス 9.3 以降に適用されます。

### <a name="use-a-custom-subject-name-on-scep-certificate----2064190---"></a>SCEP 証明書でのカスタム サブジェクト名の使用 <!-- 2064190 -->
SCEP 証明書プロファイルでカスタム サブジェクトの共通名 **OnPremisesSamAccountName** を使うことができるようになります。 たとえば、`CN={OnPremisesSamAccountName})` のように使用できます。

### <a name="send-diagnostic-reports-in-company-portal-app-for-macos----2216677---"></a>macOS のポータル サイト アプリでの診断レポートの送信 <!-- 2216677 -->
macOS デバイスのポータル サイト アプリが更新され、ユーザーは Intune 関連のエラーを報告しやすくなります。 従業員は、ポータル サイト アプリから次のことをできるようになります。
- Microsoft 開発チームに診断レポートを直接アップロードします。
- 会社の IT サポート チームにインシデント ID をメールで送ります。

### <a name="always-on-vpn-for-windows-10---1333666---"></a>Windows 10 の Always On VPN <!--1333666 -->

現在、[Always On](https://docs.microsoft.com/windows/security/identity-protection/vpn/vpn-auto-trigger-profile#always-on) は、OMA-URI を使って作成されたカスタム仮想プライベート ネットワーク (VPN) プロファイルを使うことで、Windows 10 デバイスで使用できます。

この更新では、管理者は Azure Portal の Intune で直接、Windows 10 VPN プロファイルに対する Always On を有効にできるようになります。 Always On VPN プロファイルは、次のときに自動的に接続します。

- ユーザーが自分のデバイスにサインインしたとき
- デバイスでネットワークが変更されたとき
- デバイスの画面がオフにされた後でオンに戻されたとき

### <a name="improved-error-messaging-for-apple-mdm-push-certificate-upload-failure----2172331---"></a>Apple MDM プッシュ通知証明書のアップロード失敗のエラー メッセージの改善 <!-- 2172331 -->

既存の MDM 証明書を更新するときは同じ Apple ID を使う必要があることが、エラー メッセージで説明されるようになります。

###  <a name="device-profile-chart-and-status-list-show-all-devices-in-a-group----1449153-eeready---"></a>デバイス プロファイル チャートと状態リストでグループ内のすべてのデバイスが表示されるようになる <!-- 1449153 eeready -->
デバイス プロファイルを構成するときは (**[デバイス構成]** > **[プロファイル]**)、iOS などのデバイス プロファイルを選択します。 このプロファイルを、iOS デバイスと iOS 以外のデバイスを含むグループに割り当てます。 グラフィカル チャートの数では、プロファイルが iOS デバイス "*および*" iOS 以外のデバイスに適用されているように示されます (**[デバイス構成]** > **[プロファイル]** > 既存のプロファイルを選択 > **[概要]**)。 **[概要]** タブでグラフィカル チャートを選択すると、**[デバイスの状態]** に、iOS デバイスだけではなく、グループ内のすべてのデバイスが一覧表示されます。 

この更新により、グラフィカル チャート (**[デバイス構成]** > **[プロファイル]** > 既存のプロファイルを選択 > **[概要]**) では、特定のデバイス プロファイルの数のみが表示されるようになります。 たとえば、構成デバイス プロファイルが iOS デバイスに適用される場合、チャートの一覧には iOS デバイスの数だけが表示されます。 グラフィカル チャートを選択すると開く **[デバイスの状態]** では、iOS デバイスだけが一覧表示されます。

この更新が行われている間、グラフィカル ユーザー チャートは一時的に削除されます。 


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

### <a name="ability-to-deploy-required-line-of-business-lob-apps-to-all-users-on-windows-10-desktop-devices----1627835-rs4---"></a>Windows 10 デスクトップ デバイスのすべてのユーザーに対して必要な基幹業務 (LOB) アプリを展開する機能 <!-- 1627835 RS4 -->
お客様は、必要な基幹業務 Windows 10 アプリを展開してデバイス コンテキストにインストールできるようになります。 これにより、デバイスのすべてのユーザーがこれらのアプリを使用できるようになります。 対象は Windows 10 デスクトップ デバイスだけです。

### <a name="company-portal-enrollment-improved----1874230--"></a>会社ポータルの登録の機能強化 <!-- 1874230-->
Windows 10 ビルド 1703 以降の Intune ポータル サイトを使ってデバイスを登録するユーザーは、アプリを離れることなく登録の最初の手順を完了できます。

### <a name="updating-the-help-and-feedback-experience-on-company-portal-app-for-android---1631531---"></a>Android 用 Intune ポータル サイト アプリでのヘルプとフィードバックのエクスペリエンスの更新 <!--1631531 -->

Android アプリのベスト プラクティスに合うように、Android 用 Intune ポータル サイト アプリのヘルプとフィードバックのエクスペリエンスが更新されます。 今後数か月かけて Android 用 Intune ポータル サイト アプリが更新され、**[ヘルプとフィードバック]** メニュー項目が **[ヘルプ]** と **[フィードバックの送信]** の異なるメニュー項目に分割されます。 **[ヘルプ]** ページには **[よく寄せられる質問]** セクションと **[メールでサポートに問い合わせる]** ボタンがあり、エンド ユーザーは Microsoft にログをアップロードしたり、会社のサポート部門に問題を説明するメールを送信したりできます。 **[フィードバックの送信]** では Microsoft の標準的なフィードバック送信を利用でき、"気に入った機能"、"気に入らない機能"、"アイデア" を選択できます。

<!-- 1802 start -->

### <a name="new-printer-settings-for-education-profiles----1308900---"></a>教育プロファイル用の新しいプリンター設定 <!-- 1308900 -->

教育プロファイルの場合、**[プリンター]** カテゴリで新しい設定 **[プリンター]**、**[通常使うプリンター]**、**[新しいプリンターの追加]** を利用できます。

<!-- the following are present prior to 1801 -->

### <a name="app-protection-policies-----679615---"></a>アプリ保護ポリシー  <!-- 679615 -->
Intune App Protection ポリシーは、既定のグローバル ポリシーを作成し、テナント全体のすべてのユーザーに保護をすばやく適用する機能を提供します。

<!-- the following are present prior to 1711 -->

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Azure Active Directory の Web サイトでは、Intune Managed Browser アプリを要求し、Managed Browser (パブリック プレビュー) に対するシングル サインオンをサポートすることができる <!-- 710595 -->   
Azure Active Directory (Azure AD) を使っている場合、モバイル デバイスでの Web サイトへのアクセスを、Intune Managed Browser アプリに制限することができます。 Managed Browser では、Web サイトのデータは安全性を維持され、エンド ユーザーの個人データと分離されます。 さらに、Managed Browser は、Azure AD によって保護されているサイトに対するシングル サインオン機能をサポートします。 Managed Browser にサインインすると、または Intune によって管理されている別のアプリでデバイスの Managed Browser を使うと、ユーザーが資格情報を入力しなくても、Managed Browser は Azure AD によって保護されている会社サイトにアクセスできます。 この機能は、Outlook Web Access (OWA) や SharePoint Online などのサイトだけでなく、Azure App プロキシ経由でアクセスされるイントラネット リソースのような他の企業サイトにも適用されます。




## <a name="notices"></a>通知

現在のところ、アクティブな通知はありません。


### <a name="see-also"></a>関連項目
最近の開発状況について詳しくは、「[Microsoft Intune の新機能](whats-new.md)」をご覧ください。


