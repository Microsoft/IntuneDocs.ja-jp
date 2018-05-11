---
title: Microsoft Intune の新機能 - Azure | Microsoft Docs
titlesuffix: ''
description: Intune Azure Portal の新機能を確認する
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/02/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
/ms.custom: intune-azure
ms.openlocfilehash: 9004441a41c5e7458447b5c5f7e1d91e630bd412
ms.sourcegitcommit: 2b5d88c434bda7f1cdc32d1ccacc6b341a9a399b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="whats-new-in-microsoft-intune"></a>Microsoft Intune の新機能
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

週ごとにまとめた、Microsoft Intune の新機能をご覧ください。 [今後の変更](#whats-coming)、サービスに関する[重要なお知らせ](#notices)、[過去のリリース](whats-new-archive.md)に関する情報も確認できます。 いくつかの機能については、数週間にわたってロールアウトされ、一部のお客様は最初の週にご利用になれない可能性があります。

> [!Note]
> ハイブリッド モバイル デバイス管理 (MDM) での新機能については、[ハイブリッドの新機能に関するページ](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)を確認してください。


<!-- Common categories:  
  ### App management
  ### Device enrollment
  ### Device management
  ### Device configuration
  ### Intune apps
  ### Monitor and troubleshoot
  ### Role-based access control

-->   

## <a name="week-of-april-23-2018"></a>2018 年 4 月 23 日の週

### <a name="app-management"></a>アプリ管理

#### <a name="passcode-support-for-mam-pin-on-android---1438086---"></a>Android での MAM PIN のパスコードのサポート<!-- 1438086 -->

Intune 管理者は、アプリケーション起動要件を設定して、数値の MAM PIN の代わりにパスコードを強制することができます。 構成した場合、ユーザーは、MAM 対応のアプリケーションにアクセスする前に、要求された時点で、パスコードを設定および使用する必要があります。 パスコードは、少なくとも 1 つの特殊文字または大文字/小文字アルファベットを含む数値 PIN と定義されます。 Intune によるパスコードのサポート方法は既存の数値 PIN と似ており、管理コンソールで最小の長さを設定したり、文字やシーケンスの繰り返しを許可したりできます。 この機能を利用するには、Android に最新バージョンの Intune ポータル サイトが必要です。 この機能は、iOS では既に利用できます。

#### <a name="line-of-business-lob-app-support-for-macos----1473977---"></a>macOS の基幹業務 (LOB) アプリのサポート <!-- 1473977 -->
Microsoft Intune では、Azure Portal から macOS LOB アプリをインストールできます。 GitHub で利用可能なツールを使って前処理した macOS LOB アプリを、Intune に追加できます。 Azure Portal で、**[Intune]** ブレードから **[Mobile Apps]** を選択します。 **[Mobile Apps]** ブレードで、**[アプリ]** > **[追加]** を選択します。 **[アプリの追加]** ブレードで、**[基幹業務アプリ]** を選択します。 

#### <a name="built-in-all-users-and-all-devices-group-for-android-for-work-afw-app-assignment----1813073---"></a>Android for Work (AFW) のアプリの割り当てに対する組み込みのすべてのユーザー グループとすべてのデバイス グループ <!-- 1813073 -->
組み込みの**すべてのユーザー** グループと**すべてのデバイス** グループを AFW アプリの割り当てに利用することができます。 詳細については、「[Microsoft Intune でのアプリ割り当ての組み込みと除外](apps-inc-exl-assignments.md)」を参照してください。

#### <a name="intune-will-reinstall-required-apps-that-are-uninstalled-by-users----1947010---"></a>ユーザーがアンインストールした必要なアプリは Intune によって再インストールされる <!-- 1947010 -->
エンド ユーザーが必要なアプリをアンインストールした場合、Intune は 7 日間の再評価サイクルを待機するのではなく、24 時間以内に該当するアプリを自動的に再インストールします。

### <a name="device-configuration"></a>デバイス構成

####  <a name="device-profile-chart-and-status-list-show-all-devices-in-a-group----1449153-eeready---"></a>デバイス プロファイル チャートと状態リストでグループ内のすべてのデバイスが表示されるようになる <!-- 1449153 eeready -->
デバイス プロファイルを構成するときは (**[デバイス構成]** > **[プロファイル]**)、iOS などのデバイス プロファイルを選択します。 このプロファイルを、iOS デバイスと iOS 以外のデバイスを含むグループに割り当てます。 グラフィカル チャートの数では、プロファイルが iOS デバイス "*および*" iOS 以外のデバイスに適用されているように示されます (**[デバイス構成]** > **[プロファイル]** > 既存のプロファイルを選択 > **[概要]**)。 **[概要]** タブでグラフィカル チャートを選択すると、**[デバイスの状態]** に、iOS デバイスだけではなく、グループ内のすべてのデバイスが一覧表示されます。 

この更新により、グラフィカル チャート (**[デバイス構成]** > **[プロファイル]** > 既存のプロファイルを選択 > **[概要]**) では、特定のデバイス プロファイルの数のみが表示されるようになります。 たとえば、構成デバイス プロファイルが iOS デバイスに適用される場合、チャートの一覧には iOS デバイスの数だけが表示されます。 グラフィカル チャートを選択すると開く **[デバイスの状態]** では、iOS デバイスだけが一覧表示されます。

この更新が行われている間、グラフィカル ユーザー チャートは一時的に削除されます。 

#### <a name="always-on-vpn-for-windows-10---1333666---"></a>Windows 10 の Always On VPN <!--1333666 -->

現在、[Always On](https://docs.microsoft.com/windows/security/identity-protection/vpn/vpn-auto-trigger-profile#always-on) は、OMA-URI を使って作成されたカスタム仮想プライベート ネットワーク (VPN) プロファイルを使うことで、Windows 10 デバイスで使用できます。

この更新では、管理者は Azure Portal の Intune で直接、Windows 10 VPN プロファイルに対する Always On を有効にできるようになります。 Always On VPN プロファイルは、次のときに自動的に接続します。

- ユーザーが自分のデバイスにサインインしたとき
- デバイスでネットワークが変更されたとき
- デバイスの画面がオフにされた後でオンに戻されたとき

#### <a name="new-printer-settings-for-education-profiles----1308900---"></a>教育プロファイル用の新しいプリンター設定 <!-- 1308900 -->

教育プロファイルの場合、**[プリンター]** カテゴリで新しい設定 **[プリンター]**、**[通常使うプリンター]**、**[新しいプリンターの追加]** を利用できます。

#### <a name="show-caller-id-in-personal-profile---android-for-work---1098984---"></a>個人プロファイルでの発信者番号通知 - Android for Work <!--1098984 -->
デバイス上で個人プロファイルを使用する場合、勤務先の作業連絡先からの発信者番号の詳細がエンド ユーザーに表示されない場合があります。 

この更新プログラムでは、**[Android for Work]** > **[デバイスの制限]** > **[仕事用プロファイルの設定]** に、次の新しい設定が表示されます。
- 個人プロファイルに勤務先の連絡先の発信者番号を表示する

有効にすると (構成されていない場合)、勤務先の連絡先の発信者番号の詳細が個人プロファイルに表示されます。 ブロックすると、勤務先の連絡先の発信者番号は個人プロファイルに表示されません。 

適用対象: Android OS v6.0 以降の Android 仕事用プロファイル デバイス

#### <a name="new-windows-defender-credential-guard-settings-added-to-endpoint-protection-settings---1102252-----from-1802-and-1804--"></a>Endpoint Protection の設定に追加された新しい Windows Defender Credential Guard の設定 <!--1102252 --><!--from 1802 and 1804-->

この更新により、[Windows Defender Credential Guard](https://docs.microsoft.com/windows/access-protection/credential-guard/credential-guard) (**[デバイス構成]** > **[プロファイル]** > **[Endpoint Protection]**) に、次の設定が含まれます。 

- **Windows Defender Credential Guard**: 仮想化ベースのセキュリティによる Credential Guard が有効になります。 **[Platform Security Level with Secure Boot]\(セキュア ブートでのプラットフォーム セキュリティ レベル\)** と **[仮想化ベースのセキュリティ]** の両方が有効な場合にこの機能を有効にすると、次回の再起動時に資格情報を保護することができます。 次のオプションがあります。
  - **[無効]**: 以前に Credential Guard が **[ロックなしで有効化]** オプションで有効になっていた場合に、Credential Guard をリモートで無効にします。

  - **[UEFI ロックで有効化]**: レジストリ キーまたはグループ ポリシーを使って Credential Guard を無効にできないようにします。 この設定を使用した後に Credential Guard を無効にする場合は、グループ ポリシーを [無効] に設定する必要があります。 次に、実際に存在するユーザーの各コンピューターからセキュリティ機能を削除します。 この手順により、UEFI に存在した構成がクリアされます。 UEFI の構成が保持されている限り、Credential Guard は有効になっています。

  - **[ロックなしで有効化]**: グループ ポリシーを使ってリモートで Credential Guard を無効にできるようにします。 この設定を使うデバイスは、Windows 10 (バージョン 1511) 以降を実行している必要があります。

Credential Guard を構成すると、次の関連するテクノロジが自動的に有効になります。 

  - **[Enable Virtualization-based Security (VBS)]\(仮想化ベースのセキュリティ (VBS) を有効にする\)**: 次回の再起動で仮想化ベースのセキュリティ (VBS) が有効になります。 仮想化ベースのセキュリティは、Windows ハイパーバイザーを使用してセキュリティ サービスのサポートを提供し、セキュア ブートを要求します。
  - **[Secure Boot with Direct Memory Access (DMA)]\(直接メモリ アクセス (DMA) によるセキュア ブート\)**: セキュア ブートおよび直接メモリ アクセスによる VBS が有効になります。 DMA 保護は、ハードウェアのサポートを必要とし、正しく構成されたデバイスでのみ有効にされます。 

#### <a name="use-a-custom-subject-name-on-scep-certificate----2064190---"></a>SCEP 証明書でのカスタム サブジェクト名の使用 <!-- 2064190 -->
SCEP 証明書プロファイルでカスタム サブジェクトの共通名 **OnPremisesSamAccountName** を使うことができます。 たとえば、`CN={OnPremisesSamAccountName})` のように使用できます。

####  <a name="block-camera-and-screen-captures-on-android-for-work----1098977-eeready--"></a>Android for Work でカメラと画面キャプチャをブロックする <!-- 1098977 eeready-->
Android デバイスのデバイス制限を構成するときに、次の 2 つの新しいプロパティをブロックに利用できます。 
- カメラ: デバイスのすべてのカメラへのアクセスを禁止します
- 画面キャプチャ: 画面のキャプチャをブロックし、セキュリティで保護されたビデオ出力を持たないディスプレイ デバイスにコンテンツが表示されないようにします

Android for Work に適用されます。


### <a name="device-enrollment"></a>デバイスの登録

#### <a name="new-enrollment-steps-for-users-on-devices-with-macos-high-sierra-10132---1734567---"></a>macOS High Sierra 10.13.2 以降のデバイスでのユーザーの新しい登録手順 <!--1734567 -->
macOS High Sierra 10.13.2 では、"ユーザー承認済み" MDM 登録の概念が導入されました。 承認済みの登録で、セキュリティ上重要な一部の設定の Intune による管理が許可されます。 詳細については、Apple のサポート ドキュメント https://support.apple.com/HT208019 をご覧ください。

macOS ポータル サイトを使って登録されたデバイスは、エンド ユーザーがシステム環境設定を開いて手動で承認しない限り、"ユーザー承認されていない" ものと見なされます。 そのため、macOS ポータル サイトでは、macOS 10.13.2 以降のユーザーは、登録プロセスの最後に、登録の手動承認に移動するようになりました。 Intune 管理コンソールでは、登録されているデバイスがユーザー承認済みかどうかが示されます。



### <a name="device-management"></a>デバイス管理

#### <a name="advanced-threat-protection-atp-and-intune-are-fully-integrated----eeready-1629303---"></a>Advanced Threat Protection (ATP) と Intune は完全に統合されています <!-- EEready 1629303 -->

[Advanced Threat Protection (ATP)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/dashboard-windows-defender-advanced-threat-protection) では、Windows 10 デバイスのリスク レベルが表示されます。 Windows Defender Security Center (ATP Portal) では、Microsoft Intune への接続を作成できます。 作成後、許容できる脅威レベルの決定に Intune コンプライアンス ポリシーが使用されます。 その脅威レベルを超えた場合、Azure Active Directory (AD) の条件付きアクセス ポリシーによって、組織内のさまざまなアプリへのアクセスを阻止できます。

この機能によって ATP はファイルをスキャンし、脅威を検出し、Windows 10 デバイス上のあらゆるリスクを報告できます。

[Intune で条件付きアクセスによる ATP を有効にする](advanced-threat-protection.md)方法に関するページを参照してください。

#### <a name="support-for-user-less-devices----1637553---"></a>ユーザーのいないデバイスのサポート <!-- 1637553 -->
Intune は、Microsoft Surface Hub など、ユーザーのいないデバイスでコンプライアンスを評価する機能をサポートします。 コンプライアンス ポリシーは、特定のデバイスを対象にすることができます。 したがって、ユーザーが関連付けられていないデバイスのコンプライアンス (および非コンプライアンス) を判断できます。

#### <a name="delete-autopilot-devices----1713650---"></a>Autopilot デバイスの削除 <!-- 1713650 -->
Intune 管理者は、[Autopilot デバイスを削除する](enrollment-autopilot.md#delete-autopilot-devices)ことができます。

#### <a name="improved-device-deletion-experience---1832333---"></a>デバイス削除エクスペリエンスの向上 <!--1832333 -->
[Intune からデバイスを削除する](devices-wipe.md#delete-devices-from-the-intune-portal)前に、会社のデータを削除したり、デバイスを工場出荷時の状態にリセットしたりする必要はなくなります。

新しいエクスペリエンスを表示するには、Intune にサインインし、**[デバイス]** > **[すべてのデバイス]** > デバイスの名前 > **[削除]** の順に選びます。

ワイプ/使用停止の確認が必要な場合は、**[削除]** の前に **[会社データを削除する]** と **[出荷時の設定にリセット]** を実行して、標準のデバイス ライフサイクル ルートを使うことができます。 

#### <a name="play-sounds-on-ios-when-in-lost-mode----1947769---"></a>紛失モードになったときに iOS で音を鳴らす <!-- 1947769 -->
監視対象の iOS デバイスがモバイル デバイス管理 (MDM) の[紛失モード](device-lost-mode.md)になったときに、[音を鳴らす](device-locate.md#activate-lost-mode-sound-alert-on-an-ios-device)ことができます (**[デバイス]** > **[すべてのデバイス]** > iOS デバイスを選択 > **[概要]** > **[詳細]**)。 音は、デバイスが紛失モードではなくなるまで、またはユーザーがデバイスで音を無効にするまで、鳴り続けます。 iOS デバイス 9.3 以降に適用されます。

#### <a name="block-or-allow-web-results-in-searches-made-on-an-intune-device---1972804--"></a>Intune デバイスで行った Web 検索の結果のブロックまたは許可 <!--1972804-->

管理者は、デバイスで行った Web 検索の結果をブロックできるようになりました。

#### <a name="improved-error-messaging-for-apple-mdm-push-certificate-upload-failure----2172331---"></a>Apple MDM プッシュ通知証明書のアップロード失敗のエラー メッセージの改善 <!-- 2172331 -->

既存の MDM 証明書を更新するときは同じ Apple ID を使う必要があることが、エラー メッセージで説明されます。

#### <a name="test-the-company-portal-for-macos-on-virtual-machines----2216679---"></a>仮想マシンでの macOS 用ポータル サイトのテスト <!-- 2216679 -->

Parallels Desktop と VMware Fusion の仮想マシンで IT 管理者が macOS 用ポータル サイト アプリをテストするために役立つガイドを公開しました。 詳しくは、「[テスト用に仮想 macOS マシンを登録する](macos-enroll.md#enroll-virtual-macos-machines-for-testing)」を参照してください。


### <a name="user-interface"></a>ユーザー インターフェイス

#### <a name="improved-device-tiles-in-the-windows-10-company-portal---2213364---"></a>Windows 10 ポータル サイトのデバイス タイルの改善 <!--2213364 -->

目の不自由なユーザーでもアクセスしやすく、画面読み上げツールでの動作が改善されるように、タイルが更新されました。

#### <a name="send-diagnostic-reports-in-company-portal-app-for-macos----2216677---"></a>macOS のポータル サイト アプリでの診断レポートの送信 <!-- 2216677 -->
macOS デバイスのポータル サイト アプリが更新され、ユーザーが Intune 関連のエラーを報告しやすくなりました。 従業員は、ポータル サイト アプリから次のことができます。

- Microsoft 開発チームに診断レポートを直接アップロードします。
- 会社の IT サポート チームにインシデント ID をメールで送ります。

詳細については、[macOS のエラーの送信](/intune-user-help/send-errors-macos)に関するページを参照してください。

#### <a name="intune-adapts-to-fluent-design-system-in-the-company-portal-app-for-windows-10----1195010-wnready---"></a>Intune が Windows 10 ポータル サイト アプリの Fluent Design System に対応 <!-- 1195010 WNready -->
Windows 10 の Intune ポータル サイト アプリが [Fluent Design System のナビゲーション ビュー](https://docs.microsoft.com/en-us/windows/uwp/design/basics/navigation-basics)に合わせて更新されました。 アプリの側面だけでなく、すべてのトップ レベルのページに静的な縦方向リストが表示されます。 リンクをクリックすると、ページをすばやく表示したり、ページを切り替えたりできます。 これは現在作成中の更新の一部であり、今後さらにアダプティブで馴染みがあり、使いやすい Intune の機能を提供していきます。 更新された外観を確認するには、[アプリ UI の新機能](whats-new-app-ui.md)に関するページを参照してください。

## <a name="week-of-april-16-2018"></a>2018 年 4 月 16 日の週

#### <a name="use-cisco-anyconnect-client-for-ios----eeready-1333708---"></a>iOS 向け Cisco AnyConnect クライアントを使用する <!-- EEready 1333708 -->

iOS 用に新しい VPN プロファイルを作成するとき、**[Cisco AnyConnect]** と **[Cisco Legacy AnyConnect]** の 2 つの選択肢から選択できるようになりました。 Cisco AnyConnect プロファイルは、4.0.7x 以降のバージョンに対応しています。 既存の iOS Cisco AnyConnect VPN プロファイルは **[Cisco Legacy AnyConnect]** と表示されるようになり、現在と同じように Cisco AnyConnect 4.0.5x 以前のバージョンで引き続き動作します。

> [!NOTE]
> この変更は iOS にのみ適用されます。 Android、Android for Work、macOS プラットフォームの Cisco AnyConnect オプションは、これまでどおり 1 つだけです。

#### <a name="jamf-enrolled-macos-devices-can-now-register-with-intune----2370684---"></a>Jamf 登録 macOS デバイスを Intune に登録できるようになりました <!-- 2370684 -->

macOS ポータル サイトのバージョン 1.3 と 1.4 では、Jamf デバイスが Intune に正常に登録されませんでした。 macOS ポータル サイトのバージョン 1.4.2 でこの問題が解決されました。


## <a name="week-of-april-9-2018"></a>2018 年 4 月 9 日の週

#### <a name="updated-help-experience-in-company-portal-app-for-android----1631531---"></a>Android 用ポータル サイト アプリでのヘルプ エクスペリエンスの更新 <!-- 1631531 -->

Android プラットフォームのベスト プラクティスに合うように、Android 用ポータル サイト アプリのヘルプ エクスペリエンスが更新されました。 ご使用のアプリで問題が発生した場合は、**[メニュー]** > **[ヘルプ]** の順にタップして、次のことが行えます。
- 診断ログを Microsoft にアップロードする。
- 問題とインシデント ID を記載した電子メールを社内のサポート担当者に送信する。  

更新されたヘルプ エクスペリエンスを確認するには、[[Send logs using email]\(メールでログを送信\)](/intune-user-help/send-logs-to-your-it-admin-by-email-android) および [[Send errors to Microsoft]\(エラーを Microsoft に送信\)](/intune-user-help/send-logs-to-microsoft-android) に進みます。


#### <a name="new-enrollment-failure-trend-chart-and-failure-reasons-table----1471783---"></a>新しい登録エラー傾向グラフと失敗の理由テーブル <!-- 1471783 -->

[Enrollment Overview]\(登録の概要\) ページで、登録エラーの傾向と、上位 5 つのエラーの原因を表示することができます。 グラフやテーブルをクリックすると、トラブルシューティングのアドバイスや改善の提案の詳細にドリル ダウンすることができます。

#### <a name="update-where-to-configure-your-app-protection-policies----2144597---"></a>アプリの保護ポリシーを構成する場所の更新 <!-- 2144597 -->

Azure Portal の Microsoft Intune サービスで、**[Intune アプリ保護]** サービス ブレードから **[モバイル アプリ]** ブレードに一時的にリダイレクトします。 すべてのアプリ保護ポリシーが Intune のアプリ構成の **[モバイル アプリ]** ブレードに既に置かれていることに注意してください。 Intune App Protection に移動する代わりに、Intune に移動します。 2018 年 4 月にリダイレクトを停止し、**[Intune App Protection]** サービス ブレードを完全に削除する予定です。したがって、Intune 内のアプリ保護ポリシーのための場所は 1 つだけになります。 

**ユーザーへの影響**
この変更は、Intune スタンドアロンのお客様とハイブリッド (Intune と Configuration Manager) のお客様の両方に影響します。 この統合は、クラウド管理の簡素化に役立ちます。

**この変更に対して必要な準備**
**[Intune アプリ保護]** サービス ブレードの代わりにお気に入りとして **Intune** に登録し、Intune の **[モバイル アプリ]** ブレードのアプリ保護ポリシーのワークフローを習熟してください。 リダイレクトを短期間行い、その後 **[アプリ保護]** ブレードを削除します。 ただし、すべてのアプリ保護ポリシーが既に Intune にあり、任意の条件付きアクセス ポリシーを変更することができます。 条件付きアクセス ポリシーの変更の詳細については、「[Azure Active Directory の条件付きアクセス](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)」を参照してください。 詳細については、「[アプリ保護ポリシーとは](app-protection-policy.md)」を参照してください。 


## <a name="week-of-april-2-2018"></a>2018 年 4 月 2 日の週

### <a name="intune-apps"></a>Intune アプリ

#### <a name="user-experience-update-for-the-company-portal-app-for-ios---1412866---"></a>iOS 用ポータル サイト アプリに関するユーザー エクスペリエンスの更新プログラム <!--1412866 -->
iOS 用のポータル サイト アプリに対して、主要なユーザー エクスペリエンスの更新プログラムをリリースする予定です。 この更新プログラムでは、最新のルック アンド フィールを含む完全なビジュアル再設計が行われています。 アプリの機能を維持した上で、操作性とアクセシビリティが向上しています。  

また、次のような更新が行われています。
- iPhone X のサポート。
- アプリの起動および読み込み応答を速くして、ユーザー時間を節約。
- 最新の状態情報をユーザーに提供するための進行状況バーを追加。
- ログのアップロード方法を改善。これにより、問題が生じた場合に、その内容を簡単にレポートできる。  

更新された外観を確認するには、[アプリ UI の新機能](whats-new-app-ui.md)に関するページを参照してください。

#### <a name="protect-on-premise-exchange-data-using-intune-app-and-ca----1056954---"></a>Intune APP および CA を使用したオンプレミス Exchange データの保護 <!-- 1056954 -->
Intune アプリ ポリシー保護 (APP) および条件付きアクセス (CA) を使用して、Outlook Mobile によるオンプレミスの Exchange データへのアクセスを保護できるようになりました。 Azure Portal 内でアプリの保護ポリシーの追加または変更を行うには、**[Microsoft Intune]** > **[モバイル アプリ]** > **[アプリ保護ポリシー]** を選択します。 この機能を使用する前に、[iOS および Android 用 Outlook の要件](https://technet.microsoft.com/en-us/library/mt846639(v=exchg.160).aspx)を満たしていることを確認します。

## <a name="week-of-march-26-2018"></a>2018 年 3 月 26 日の週

### <a name="app-management"></a>アプリ管理

#### <a name="alerts-for-expiring-ios-line-of-business-lob-apps-for-microsoft-intune----748789---"></a>Microsoft Intune 用の iOS 基幹業務 (LOB) アプリの有効期限切れを示すアラート <!-- 748789 -->

Azure Portal の Intune では、有効期限が近づいている iOS 基幹業務アプリが警告されます。 iOS 基幹業務アプリの新しいバージョンをアップロードすると、有効期限に関する通知が Intune によってアプリ一覧から削除されます。 この有効期限に関する通知は、iOS 基幹業務アプリが新たにアップロードされた場合にのみアクティブになります。 警告が表示されるのは、iOS LOB アプリのプロビジョニング プロファイルの有効期限が切れる 30 日前となります。 有効期限が切れると、アラート表示が "期限切れ" 表示に変わります。

#### <a name="customize-your-company-portal-themes-with-hex-codes---1049561---"></a>Intune ポータル サイトのテーマを 16 進コードでカスタマイズする <!--1049561 -->

Intune ポータル サイト アプリのテーマの色を、16 進コードを使ってカスタマイズできます。 16 進コードを入力すると、Intune はテキストの色と背景の色の間のコントラストが最高レベルになるようにテキストの色を決定します。 **[Mobile Apps]** > **[ポータル サイト]** で、テキストの色および色に対する会社のロゴの両方をプレビューできます。

### <a name="including-and-excluding-app-assignment-based-on-groups-for-android-enterprise----1813081---"></a>Android Enterprise に対するグループに基づくアプリ割り当ての追加と除外 <!-- 1813081 -->

Android エンタープライズ (旧称 Android for Work) では、グループの追加と除外をサポートしていますが、事前に作成された**すべてのユーザー**と**すべてのデバイス**の組み込みグループはサポートしていません。 詳細については、「[Microsoft Intune でのアプリ割り当ての組み込みと除外](apps-inc-exl-assignments.md)」を参照してください。


### <a name="device-management"></a>デバイス管理

#### <a name="new-security-enhancements-in-the-intune-service-----1637539---"></a>Intune サービスでの新たなセキュリティ強化  <!-- 1637539 -->   

Azure 上の Intune にトグルが導入されました。このスイッチを利用することにより、Intune スタンドアロンのお客様は、ポリシーが割り当てられていないデバイスを **[準拠]** として処理 (セキュリティ機能オフ) することも、そのようなデバイスを **[非準拠]** として処理 (セキュリティ機能オン) することもできます。 これにより、デバイスのポリシー準拠が評価された後でのみ、リソースへのアクセスが保証されます。

この機能がユーザーに及ぼす影響は、コンプライアンス ポリシーが割り当て済みかどうかによって異なります。

- 新しいアカウントまたは既存のアカウントがあるが、コンプライアンス ポリシーをデバイスに割り当てていない場合、トグルは自動的に **[準拠]** に設定されます。 コンソールの既定の設定では、この機能はオフになっています。 エンドユーザーに与える影響はありません。
- 既存のアカウントがあり、デバイスにはコンプライアンス ポリシーが割り当てられている場合、トグルは自動的に **[非準拠]** に設定されます。 この機能は、3 月の更新のロールアウト時に、既定の設定としてオンになっています。

コンプライアンス ポリシーを条件付きアクセス (CA) と共に使用し、この機能がオンになっている場合、少なくとも 1 つのコンプライアンス ポリシーが割り当てられているデバイスは、CA によってブロックされるようになりました。 これらのデバイスに関連付けられていて、以前は電子メールへのアクセスを許可されていたエンド ユーザーは、少なくとも 1 つのコンプライアンス ポリシーをすべてのデバイスに割り当てない限り、アクセスできなくなります。   

Intune サービスの 3 月の更新プログラムにより、既定のトグル状態は UI にすぐに表示されるようになりましたが、このトグル状態はすぐに適用されないので注意してください。 トグルに変更を加えても、アカウントがフライトされて準備が整うまで、デバイスのポリシー準拠に影響はありません。 アカウントのフライトが完了したら、メッセージ センターを介してお知らせします。 これには、3 月の Intune サービスの更新が行われてから、数日かかる場合があります。

**追加情報**: [https://aka.ms/compliance_policies](https://aka.ms/compliance_policies)

#### <a name="enhanced-jailbreak-detection----846515---"></a>脱獄の検出の機能強化 <!-- 846515 -->

強化された脱獄の検出の新しいコンプライアンス設定により、Intune による脱獄されたデバイスの評価方法が向上します。 この設定を使用すると、デバイスはこれまでより頻繁に Intune にチェックインされます。このときデバイスの場所サービスが使用されるため、バッテリの使用量に影響を与えます。

#### <a name="reset-passwords-for-android-o-devices----1238299---"></a>Android O デバイスのパスワードをリセットする <!-- 1238299 -->
作業プロファイルで、登録済みの Android 8.0 デバイスのパスワードをリセットできるようになります。 Android 8.0 デバイスに "パスワード リセット" 要求を送信すると、新しいデバイス ロック解除パスワードまたはマネージド プロファイルのチャレンジが、現在のユーザーに設定されます。 パスワードまたはチャレンジが送信され、すぐには有効になります。

#### <a name="targeting-compliance-policies-to-devices-in-device-groups---1307012---"></a>デバイス グループのデバイスへのコンプライアンス ポリシーのターゲット<!--1307012 -->

ユーザー グループ内のユーザーを、コンプライアンス ポリシーのターゲットにすることができます。 この更新プログラムを使用すると、デバイス グループ内のデバイスを、コンプライアンス ポリシーのターゲットにすることができます。 デバイス グループの一部としてターゲットにされたデバイスがコンプライアンス アクションを受け取ることはありません。

#### <a name="new-management-name-column----1333586---"></a>新しい [管理名] 列 <!-- 1333586 -->
 **[管理名]** という名前の新しい列がデバイス ブレードで使用できます。 これは、次の式に基づいてデバイスごとに割り当てられる、自動生成された編集不可能な名前です。
- すべてのデバイスの既定の名前: <username><em><devicetype></em><enrollmenttimestamp>
- 一括追加デバイスの場合: <PackageId/ProfileId><em><DeviceType></em><EnrollmentTime>

これは、デバイス ブレードの省略可能な列です。 既定では使用できず、列セレクターを使用してのみアクセスできます。 この新しい列によるデバイス名への影響はありません。

#### <a name="ios-devices-are-prompted-for-a-pin-every-15-minutes---1550837---"></a>iOS デバイスで 15 分ごとに PIN の入力を求める <!--1550837 -->
iOS デバイスにコンプライアンスまたは構成ポリシーが適用されると、ユーザーは 15 分ごとに PIN を設定するように求められます。 PIN を設定するまで継続してユーザーは入力を求められます。

#### <a name="schedule-your-automatic-updates---1805514---"></a>自動更新スケジュールの設定 <!--1805514 -->
Intune では、[Windows Update リングの設定](windows-update-for-business-configure.md)を使用して、自動更新のインストールを制御することができます。 この更新プログラムでは、週、日、時刻などを指定して、繰り返し更新が発生するようスケジュールすることができます。

#### <a name="use-fully-distinguished-name-as-subject-for-scep-certificate---2221763---"></a>SCEP 証明書のサブジェクトとして完全な識別名を使用する <!--2221763 -->
SCEP 証明書プロファイルを作成するときには、サブジェクト名を入力します。 この更新プログラムでは、サブジェクト名として、完全な識別名を使用できるようになります。 **サブジェクト名**に対して **[カスタム]** を選択し、`CN={{OnPrem_Distinguished_Name}}` と入力します。 `{{OnPrem_Distinguished_Name}}` 変数を使用するには、[Azure Active Directory (AD) Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) を使用して、`onpremisesdistingishedname` ユーザー属性を Azure AD と同期させます。

### <a name="device-configuration"></a>デバイス構成

#### <a name="enable-bluetooth-contact-sharing---android-for-work---1098983---"></a>Bluetooth での連絡先の共有の有効化 - Android for Work <!--1098983 -->
Android の既定では、仕事用プロファイルの連絡先が Bluetooth デバイスと同期することはできません。 その結果、Bluetooth デバイスに対して、仕事用プロファイルの連絡先が発信者 ID に表示されません。

この更新プログラムでは、**[Android for Work]** > **[デバイスの制限]** > **[仕事用プロファイルの設定]** に、次の新しい設定が表示されます。
- Bluetooth 経由での連絡先の共有

Intune の管理者は、これらの設定を構成して共有を有効にできます。 これは、デバイスを、ハンズフリー使用のために発信者 ID を表示する、車を拠点とする Bluetooth デバイスとペアリングする場合に便利です。 有効にすると、仕事用プロファイルの連絡先が表示されます。 無効にすると、仕事用プロファイルの連絡先は表示されません。

#### <a name="configure-gatekeeper-to-control-macos-app-download-source----1690459---"></a>macOS アプリ ダウンロード ソースを制御するための Gatekeeper の構成 <!-- 1690459 -->

ダウンロードできるアプリの場所を制御することでアプリからデバイスを保護するように、Gatekeeper を構成することができます。 構成できるダウンロード ソースは、**[Mac App Store]**、**[Mac App Store と識別された開発者]**、または **[どこでも]** となります。 また、ユーザーが Ctrl キーを押しながらクリックしてアプリをインストールすることによりこれらの Gatekeeper 制御を無効にできるかどうかも構成できます。

これらの設定は、**[デバイス構成]** -> **[プロファイルの作成]** -> **[macOS]** -> **[Endpoint Protection]** にあります。

#### <a name="configure-the-mac-application-firewall----1690461---"></a>Mac アプリケーションのファイアウォールの構成 <!-- 1690461 -->

Mac アプリケーションのファイアウォールを構成できます。 これを使って、ポートごとではなく、アプリケーションごとに接続を制御できます。 これにより、ファイアウォールによる保護を簡単に利用できるようになり、正当なアプリ用に開かれているネットワーク ポートを望ましくないアプリが制御するのを防ぐのに役立ちます。

この設定は、**[デバイス構成]** -> **[プロファイルの作成]** -> **[macOS]** -> **[Endpoint Protection]** にあります。

ファイアウォールの設定を有効にすると、2 つの戦略を使ってファイアウォールを構成できます。

- すべての着信接続をブロックする

   対象デバイスに対するすべての着信接続をブロックすることができます。 この方法を選択した場合、すべてのアプリの着信接続がブロックされます。

- 特定のアプリを許可またはブロックする

   特定のアプリからの着信接続の受信を許可またはブロックできます。 ステルス モードを有効にして、プローブ要求への応答を防ぐこともできます。

####  <a name="detailed-error-codes-and-messages----1376342---"></a>詳しいエラー コードとメッセージ <!-- 1376342 -->

デバイス構成で、詳しいエラー コードとエラー メッセージを確認できます。 この改善された報告機能には、設定、設定の状態、トラブルシューティングの詳細が表示されます。

##### <a name="more-information"></a>詳細情報

- すべての着信接続をブロックする

   すべての共有サービス (ファイル共有や画面共有など) が着信接続を受信するのをブロックします。 その場合でも、次のシステム サービスは着信接続を受信できます。
  - configd - DHCP および他のネットワーク構成サービスを実装します
  - mDNSResponder - Bonjour を実装します
  - racoon - IPSec を実装します

    共有サービスを使うには、**[着信接続]** を (**[ブロック]** ではなく) **[未構成]** に設定します。

- ステルス モード

   これを有効にすると、コンピューターはプローブ要求に応答しなくなります。 その場合でも、コンピューターは承認されたアプリの着信要求には応答します。 ICMP (ping) などの予期しない要求は無視されます。

#### <a name="disable-checks-on-device-restart---1805490---"></a>デバイス再起動時のチェックの無効化 <!--1805490 -->
Intune では[ソフトウェア更新プログラムを管理](windows-update-for-business-configure.md)することができる。 この更新プログラムでは、<strong>[再起動チェック]</strong> プロパティが提供され、既定では有効になります。 デバイスを再起動する際に発生する一般的なチェック (アクティブなユーザー、バッテリのレベルなど) をスキップするには、<strong>[スキップ]</strong> を選択します。

#### <a name="new-windows-10-insider-preview-channels-available-for-deployment-rings----1746293---"></a>展開リングで利用できる新しい Windows 10 Insider Preview チャンネル <!-- 1746293 -->
Windows 10 展開リングを作成するときに、次の Windows 10 Insider Preview サービス チャンネルを選択するオプションが使用できるようになりました。
- Windows Insider ビルド - 高速
- Windows Insider ビルド - 低速
- Windows Insider ビルドのリリース 

これらのチャネルの詳細については、「[Insider Preview ビルドの管理](https://insider.windows.com/en-us/for-business-organization-admin/)」を参照してください。   
Intune での展開チャネルの作成の詳細については、「[ソフトウェア更新プログラムの管理](windows-update-for-business-configure.md)」を参照してください。

### <a name="intune-apps"></a>Intune アプリ

#### <a name="company-portal-enrollment-improved----1874230-eeready--"></a>会社ポータルの登録の機能強化 <!-- 1874230 eeready-->
Windows 10 ビルド 1703 以降の Intune ポータル サイトを使ってデバイスを登録するユーザーは、アプリを離れることなく登録の最初の手順を完了できるようになりました。

#### <a name="hololens-and-surface-hub-now-appear-in-device-lists---1725868---"></a>HoloLens と Surface Hub がデバイス リストに表示されるようになった <!--1725868 -->
Intune に登録された HoloLens および Surface Hub のデバイスを Android 用ポータル サイト アプリに表示するためのサポートが追加されました。

#### <a name="custom-book-categories-for-volume-purchase-progream-vpp-ebooks----1488911---"></a>ボリューム購入プログラム (VPP) 電子ブックのカスタム ブック カテゴリ <!-- 1488911 -->
電子ブックのカスタム カテゴリを作成し、VPP の電子ブックをカスタム電子ブック カテゴリに割り当てることができます。 エンド ユーザーは、新しく作成された電子ブック カテゴリとそのカテゴリに割り当てられているブックを見ることができます。 詳細については、「[Microsoft Intune によるボリューム購入アプリとブックの管理](vpp-apps.md)」を参照してください。

#### <a name="new-windows-defender-application-guard-settings----1631890---"></a>Windows Defender Application Guard の新しい設定 <!-- 1631890 -->

- **グラフィック アクセラレータを有効にする**: 管理者は、Windows Defender Application Guard に対して仮想グラフィック プロセッサを有効にすることができます。 この設定を使うと、CPU はグラフィックのレンダリングを vGPU にオフロードできます。 これにより、グラフィックが多用されている Web サイトを操作するとき、またはコンテナー内のビデオを見るときのパフォーマンスが向上します。

- **SaveFilestoHost**: 管理者は、コンテナーで実行されている Microsoft Edge からホスト ファイル システムへのファイルの受け渡しを有効にすることができます。 これをオンにすると、ユーザーはコンテナー内の Microsoft Edge からホスト ファイル システムにファイルをダウンロードできます。

#### <a name="mam-protection-policies-targeted-based-on-management-state----1665993---"></a>管理の状態に基づいて対象とされる MAM 保護ポリシー <!-- 1665993 -->
デバイスの管理状態に基づいて、MAM ポリシーを対象とすることができます。
- **Android デバイス** - 管理されていないデバイス、Intune で管理されたデバイス、Intune で管理された Android Enterprise Profiles (旧称 Android for Work) を対象にできます。
- **iOS デバイス** - 管理されていないデバイス (MAM のみ) または Intune で管理されたデバイスを対象にできます。

    > [!NOTE]
    > - この機能用の iOS サポートは、2018 年 4 月を通してロールアウトされます。

詳細については、[デバイス管理状態に基づくターゲット アプリ保護ポリシー](app-protection-policies.md)に関するページを参照してください。

#### <a name="improvements-to-the-language-in-the-company-portal-app-for-windows----1683758---"></a>Windows 用ポータル サイト アプリの言語を改善 <!-- 1683758 -->
ユーザーにわかりやすく、組織に特有の言語となるように、Windows 10 用ポータル サイトの言語に改善を加えました。 改善された内容を示すサンプル画像を確認するには、[アプリ UI の新機能](whats-new-app-ui.md)に関するページを参照してください。

#### <a name="new-additions-to-our-docs-about-user-privacy----1440709---"></a>ユーザー プライバシーに関する Microsoft ドキュメントへの新規追加 <!-- 1440709 -->
エンドユーザーが自身のデータとプライバシーをより厳密に制御できるようにするための Microsoft の取り組みの一環として、ポータル サイト アプリによってローカルに格納されたデータの表示および削除方法を説明した Microsoft ドキュメントに対する更新内容を公開しました。 これらの更新内容は以下で確認できます。

- **Android**: [Intune から Android デバイスを削除する方法](/intune-user-help/unenroll-your-device-from-intune-android.md)
- **Android (ユーザーが使用条件を拒否した場合)**: ["使用条件" が拒否された場合にデバイス管理を削除する](/intune-user-help/unenroll-your-device-from-intune-if-you-declined-terms-of-use-android.md)
- **iOS**: [Intune から iOS デバイスを削除する](/intune-user-help/unenroll-your-device-from-intune-ios.md)
- **Windows**: [Intune から Windows デバイスを削除する](/intune-user-help/unenroll-your-device-from-intune-windows.md)

## <a name="week-of-march-19-2018"></a>2018 年 3 月 19 日の週

### <a name="export-all-devices-into-csv-files-in-ie-edge-or-chrome----2258071---"></a>IE、Edge、または Chrome ですべてのデバイスを CSV ファイルにエクスポートする <!-- 2258071 -->
**[デバイス]** > **[すべてのデバイス]** で、デバイスを CSV 形式の一覧に**エクスポート**することができます。 10,000 を超えるデバイスを持つ Internet Explorer (IE) ユーザーは、デバイスを複数のファイルに正常にエクスポートできます。 各ファイルには、最大 10,000 のデバイスが含まれます。

30,000 を超えるデバイスを持つユーザーは、デバイスを複数のファイルに正常にエクスポートできます。 各ファイルには、最大 30,000 のデバイスが含まれます。

管理するデバイスに対して実行できる操作の詳細については、[デバイスの管理](device-management.md)に関するページを参照してください。

## <a name="week-of-march-12-2018"></a>2018 年 3 月 12 日の週

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Azure Active Directory の Web サイトでは、Intune Managed Browser アプリを要求し、Managed Browser (パブリック プレビュー) に対するシングル サインオンをサポートすることができる <!-- 710595 -->

Azure Active Directory (Azure AD) を使用している場合、モバイル デバイスでの Web サイトへのアクセスを Intune Managed Browser アプリに制限できるようになりました。 Managed Browser では、Web サイトのデータは安全性が維持され、エンド ユーザーの個人データと分離されます。 さらに、Managed Browser は、Azure AD によって保護されているサイトに対するシングル サインオン機能をサポートします。 Managed Browser にサインインすると、または Intune によって管理されている別のアプリでデバイスの Managed Browser を使うと、ユーザーが資格情報を入力しなくても、Managed Browser は Azure AD によって保護されている会社サイトにアクセスできます。 この機能は、Outlook Web Access (OWA) や SharePoint Online などのサイトだけでなく、Azure App プロキシ経由でアクセスされるイントラネット リソースのような他の企業サイトにも適用されます。

#### <a name="company-portal-app-for-android-visual-updates---976944---"></a>Android 用ポータル サイト アプリのビジュアルの更新 <!--976944 -->

Android 用 Intune ポータル サイト アプリを、Android の[マテリアル デザイン](https://material.io/) ガイドラインに合わせて更新しています。 「[アプリ UI の新機能](whats-new-app-ui.md)」の記事で、新しいアイコンの画像を確認することができます。

### <a name="new-windows-defender-exploit-guard-settings----1631893---"></a>Windows Defender Exploit Guard の新しい設定 <!-- 1631893 -->

<strong>[攻撃の回避]</strong> の 6 つの新しい設定と、拡張された <strong>[フォルダー アクセスの制御: フォルダーの保護]</strong> 機能が利用できるようになりました。 これらの設定は、[デバイス構成] > [プロファイル] > 
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

|              設定の名前               |                                                              設定オプション                                                              | 説明 |
|-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| フォルダーの保護 (実装済み) | 未構成、有効、監査のみ (実装済み)<br><br> <strong>新規</strong><br>Block disk modification (ディスクの変更をブロックする)、Audit disk modification (ディスクの変更を監査する) |             |

ファイルおよびフォルダーを、悪意のあるアプリによる未承認の変更から保護します。<br><br>**有効**: 信頼されていないアプリによる、保護されたフォルダー内のファイルの変更または削除、およびディスク セクターへの書き込みを、禁止します。<br><br>
**Block disk modification only (ディスクの変更のみをブロック)**:<br>信頼されていないアプリによるディスク セクターへの書き込みをブロックします。 信頼されていないアプリは、保護されたフォルダー内のファイルを変更または削除することはできます。

## <a name="week-of-february-19-2018"></a>2018 年 2 月 19 日の週

### <a name="device-enrollment"></a>デバイスの登録

#### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685---"></a>複数の Apple DEP および Apple School Manager アカウントに対する Intune サポート<!-- 747685 -->

最大 100 個の異なる [Apple Device Enrollment Program (DEP)](device-enrollment-program-enroll-ios.md) または [Apple School Manager](apple-school-manager-set-up-ios.md) アカウントからのデバイス登録が、Intune でサポートされます。 アップロードされる各トークンは、登録プロファイルとデバイスで、別々に管理できます。 アップロードされる DEP および School Manager のトークンごとに、異なる登録プロファイルを自動で割り当てることができます。 複数の School Manager トークンがアップロードされた場合、Microsoft 学校データ同期と共有できるのは、一度に 1 つのみです。

移行後、Graph で Apple DEP および ASM を管理するベータ版の Graph API と公開されたスクリプトは、動作しなくなります。 現在、新しいベータ版の Graph API の開発が進行中で、移行後にリリースされる予定です。

#### <a name="see-enrollment-restrictions-per-user----1634444-eeready-wnready---"></a>ユーザーごとに登録の制限を表示する <!-- 1634444 eeready wnready -->
**[トラブルシューティング]** ブレードの **[割り当て]** 一覧から **[登録制限]** を選択すると、各ユーザーに対して有効な[登録制限](enrollment-restrictions-set.md)を参照することができます。

### <a name="device-management"></a>デバイス管理
#### <a name="windows-defender-health-status-and-threat-status-reports---854704---"></a>Windows Defender の正常性状態レポートと脅威状態レポート<!--854704 -->

Windows Defender の正常性と状態を理解することは、Windows PC の管理において重要なことです。  この更新では、Intune に、Windows Defender エージェントの状態と正常性の新しいレポートやアクションが追加されています。 [デバイスのポリシー準拠ワークロード](compliance-policy-monitor.md)の状態ロールアップ レポートを使うと、次のことが必要なデバイスを発見できます。
- 署名の更新
- 再起動
- 手動介入
- フル スキャン
- 介入を必要とする他のエージェント状態

各状態カテゴリのドリルイン レポートでは、注意の必要な PC または**クリーン**と報告されている PC が個別に一覧表示されます。

#### <a name="new-privacy-settings-for-device-restrictions---1308926---"></a>デバイス制限のための新しいプライバシー設定 <!--1308926 -->
[2 つの新しいプライバシー設定](device-restrictions-windows-10.md#privacy)をデバイスで利用できるようになりました。
- **ユーザー アクティビティの公開**: これを **[ブロック]** に設定すると、タスク スイッチャーでの共有エクスペリエンスおよび最近使われたリソースの検出が行われなくなります。
- **ローカル アクティビティの場合のみ**: これを **[ブロック]** に設定すると、ローカル アクティビティのみに基づいて、タスク スイッチャーでの共有エクスペリエンスおよび最近使われたリソースの検出が行われなくなります。

#### <a name="new-settings-for-the-edge-browser---1469166---"></a>Microsoft Edge ブラウザーの新しい設定 <!--1469166 -->
Microsoft Edge ブラウザーを備えたデバイスで、[2 つの新しい設定](device-restrictions-windows-10.md#edge-browser) **[Path to favorites file]\(お気に入りファイルへのパス\)** と **[Changes to Favorites]\(お気に入りへの変更\)** が利用できるようになりました。

### <a name="app-management"></a>アプリ管理
#### <a name="protocol-exceptions-for-applications---1035509---"></a>アプリケーションのプロトコル例外 <!--1035509 -->

Intune モバイル アプリケーション管理 (MAM) データ転送ポリシーの例外を作成し、特定の管理されていないアプリケーションを開くことができまるようになりました。 このようなアプリケーションは、IT 担当者によって信頼されている必要があります。 データ転送ポリシーを**管理対象アプリのみ**に設定すると、作成した例外以外については、やはりデータ転送が Intune で管理されているアプリケーションだけに制限されます。 プロトコル (iOS) またはパッケージ (Android) を使って制限を作成することができます。

たとえば、MAM データ転送ポリシーに対する例外として、Webex パッケージを追加できます。 これにより、管理された Outlook メール メッセージ内の Webex リンクを、Webex アプリケーションで直接開くことができます。 他の管理されていないアプリケーションでは、データ転送が制限されます。 詳細については、「[Data transfer policy exceptions for apps](app-protection-policies-exception.md)」(アプリのデータ転送ポリシーの例外) を参照してください。

#### <a name="windows-information-protection-wip-encrypted-data-in-windows-search-results----1469193---"></a>Windows 検索結果の Windows 情報保護 (WIP) 暗号化データ<!-- 1469193 -->
Windows 情報保護 (WIP) ポリシーの設定により、WIP で暗号化されたデータを Windows の検索結果に含めるかどうかを制御できるようになりました。 このアプリ保護ポリシー オプションを設定するには、Windows 情報保護 (WIP) ポリシーの **[詳細設定]** で **[Allow Windows Search Indexer to search encrypted items]** \(暗号化されたアイテムの検索を Windows Search Indexer に許可する\) を選択します。 アプリの保護ポリシーは、*[Windows 10]* プラットフォームに設定し、アプリ ポリシーの **[登録状態]** は **[With enrollment]** \(登録あり\) に設定する必要があります。 詳細については、「[Allow Windows Search Indexer to search encrypted items](windows-information-protection-policy-create.md#allow-windows-search-indexer-to-search-encrypted-items)」 (暗号化されたアイテムの検索を Windows Search Indexer に許可する) を参照してください。

#### <a name="configuring-a-self-updating-mobile-msi-app----1740840---"></a>自己更新モバイル MSI アプリの構成 <!-- 1740840 -->
バージョン チェック プロセスを無視するように、既知の自己更新モバイル MSI アプリを構成することができます。 この機能は、競合状態になるのを防ぐのに役立ちます。 たとえば、この種類の競合状態は、アプリ開発者によって自動更新されているアプリが、Intune によっても更新されると、発生する可能性があります。 両方が Windows クライアント上のアプリのバージョンを強制しようとして、競合が発生することがあります。 これらの自動更新される MSI アプリには、**[アプリ情報]** ブレードで **[Ignore app version]** \(アプリのバージョンを無視する\) を設定できます。 この設定を **[はい]** に切り替えると、Microsoft Intune で Windows クライアントにインストールされているアプリのバージョンは無視されます。

#### <a name="related-sets-of-app-licenses-supported-in-intune----1864117---"></a>Intune でサポートされるアプリ ライセンスの関連する設定 <!-- 1864117 -->
Azure Portal 内の Intune で、UI の単一アプリ項目として、アプリ ライセンスの関連する設定がサポートされるようになりました。 さらに、ビジネス向け Microsoft Store から同期されるすべてのオフライン ライセンス アプリは単一のアプリ エントリに統合され、個別のパッケージからの展開の詳細は 1 つのエントリに移行されます。 Azure Portal でアプリ ライセンスの関連する設定を表示するには、**[Mobile Apps]** ブレードから **[アプリ ライセンス]** を選びます。

### <a name="device-configuration"></a>デバイス構成
#### <a name="windows-information-protection-wip-file-extensions-for-automatic-encryption----1463582---"></a>Windows 情報保護 (WIP) ファイルの自動暗号化用拡張子<!-- 1463582 -->
会社の境界内のサーバー メッセージ ブロック (SMB) 共有からコピーする場合、WIP ポリシーの定義に従って、自動的に暗号化するファイル拡張子を、Windows 情報保護 (WIP) ポリシーで指定できるようになりました。

#### <a name="configure-resource-account-settings-for-surface-hubs"></a>Surface Hub のリソース アカウント設定を構成する

Surface Hub のリソース アカウント設定をリモートで構成することができるようになりました。

このリソース アカウントは、Skype または Exchange でミーティングに参加できるように認証する場合に Surface Hub で使用されます。
Surface Hub がミーティングで会議室として表示されるように、一意のリソース アカウントを作成できます。
たとえば、**会議室 B41/6233** のようなリソース アカウントです。

> [!NOTE]
> - フィールドを空白のままにすると、デバイスで以前に構成された属性が上書きされます。
>
> - リソース アカウントのプロパティは、Surface Hub で動的に変更できます。 たとえば、パスワードのローテーションが有効かどうか、などです。 そのため、Azure コンソールの値が、デバイス上の現実に反映されるまでに時間がかかることがあります。
>
>   Surface Hub での現在の構成を理解するには、リソース アカウント情報をハードウェア インベントリ (既に 7 日間隔になっています) または読み取り専用プロパティに含めることができます。 リモート操作が行われた後の精度を向上させるには、操作実行直後にパラメーターの状態を取得し、Surface Hub のアカウント/パラメーターを更新できます。


##### <a name="attack-surface-reduction"></a>攻撃の回避


|設定の名前  |設定オプション  |説明  |
|---------|---------|---------|
|電子メールのパスワードで保護されている実行可能ファイルのコンテンツの実行|ブロック、監査、未構成|メールからのパスワードで保護されている実行可能ファイルのダウンロードを防止します。|
|Advanced ransomware protection (高度なランサムウェア防止)|有効、監査、未構成|積極的なランサムウェア防止を使います。|
|Flag credential stealing from the Windows local security authority subsystem (Windows ローカル セキュリティ機関サブシステムからの資格情報の盗難にフラグを設定する)|有効、監査、未構成|Windows ローカル セキュリティ機関サブシステム (lsass.exe) からの資格情報の盗難にフラグを設定します。|
|Process creation from PSExec and WMI commands (PSExec および WMI コマンドからのプロセス作成)|ブロック、監査、未構成|PSExec および WMI コマンドから開始されるプロセス作成をブロックします。|
|Untrusted and unsigned processes that run from USB (USB から実行された信頼されていない署名なしのプロセス)|ブロック、監査、未構成|USB から実行された信頼されていない署名なしのプロセスをブロックします。|
|Executables that don’t meet a prevalence, age, or trusted list criteria (普及、経過時間、または信頼されたリストの条件を満たしていない実行可能ファイル)|ブロック、監査、未構成|普及、経過時間、または信頼されたリストの条件を満たしていない実行可能ファイルの実行をブロックします。|

##### <a name="controlled-folder-access"></a>フォルダー アクセスの制御

|              設定の名前               |                                                              設定オプション                                                              | 説明 |
|-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| フォルダーの保護 (実装済み) | 未構成、有効、監査のみ (実装済み)<br><br> <strong>新規</strong><br>Block disk modification (ディスクの変更をブロックする)、Audit disk modification (ディスクの変更を監査する) |             |

ファイルおよびフォルダーを、悪意のあるアプリによる未承認の変更から保護します。<br><br>**有効**: 信頼されていないアプリによる、保護されたフォルダー内のファイルの変更または削除、およびディスク セクターへの書き込みを、禁止します。<br><br>
**Block disk modification only (ディスクの変更のみをブロック)**:<br>信頼されていないアプリによるディスク セクターへの書き込みをブロックします。 信頼されていないアプリは、保護されたフォルダー内のファイルを変更または削除することはできます。

#### <a name="additions-to-system-security-settings-for-windows-10-and-later-compliance-policies---1704133--"></a>Windows 10 以降のコンプライアンス ポリシーのシステム セキュリティ設定への追加 <!--1704133-->

ファイアウォールと Windows Defender ウイルス対策の要求など、Windows 10 のコンプライアンス設定への追加機能が使用可能になりました。


### <a name="role-based-access-control"></a>ロールベースのアクセス制御
### <a name="intune-apps"></a>Intune アプリ
#### <a name="support-for-offline-apps-from-the-microsoft-store-for-business---1222672--"></a>ビジネス向け Microsoft ストアから入手したオフライン アプリのサポート <!--1222672-->
ビジネス向け Microsoft ストアから購入したオフライン アプリが Azure Portal と同期されまるようになりました。 その後、これらのアプリをデバイス グループまたはユーザー グループに展開できます。 オフライン アプリは、ストアからではなく Intune でインストールします。

#### <a name="prevent-end-users-from-manually-adding-or-removing-accounts-in-the-work-profile----1728700---"></a>エンド ユーザーが作業プロファイルのアカウントを手動で追加または削除できないようにする <!-- 1728700 -->

Gmail アプリを Android for Work プロファイルに展開するとき、Android for Work デバイス制限プロファイルで **[Add and remove accounts]\(アカウントを追加および削除する\)** 設定を使うことで、エンド ユーザーが作業プロファイルのアカウントを手動で追加または削除できないようにすることができるようになりました。

## <a name="week-of-february-5-2018"></a>2018 年 2 月 5 日の週

### <a name="device-enrollment"></a>デバイスの登録

#### <a name="new-option-for-user-authentication-for-apple-bulk-enrollment----747625-eeready---"></a>Apple の一括登録に対するユーザー認証の新しいオプション<!-- 747625 eeready -->

> [!NOTE]
> 新しいテナントでは、これは直ちに表示されます。 既存のテナントでは、この機能は 4 月にロールアウトされます。 このロールアウトが完了するまで、これらの新しい機能にアクセスできないことがあります。

Intune では現在、次の登録方法について、ポータル サイト アプリを使用してデバイスを認証できます。

- Apple Device Enrollment Program
- Apple School Manager
- Apple Configurator Enrollment

このポータル サイト オプションを使用すると、これらの登録方法をブロックすることなく、Azure Active Directory の多要素認証を強制できます。

このポータル サイト オプションを使用する場合、iOS 設定アシスタントでの、ユーザー アフィニティ登録用のユーザー認証がスキップされます。 つまり、このデバイスは、最初はユーザーのいないデバイスとして登録されるため、ユーザー グループの構成やポリシーは受信しません。 デバイス グループの構成とポリシーのみを受信します。 ただし、ポータル サイト アプリは自動的にデバイスにインストールされます。 ポータル サイト アプリを最初に起動してサインインするユーザーは、Intune でそのデバイスと関連付けられます。 この時点で、ユーザー グループの構成とポリシーが、このユーザーに送信されます。 ユーザーの関連付けを変更するには、再登録が必要です。

#### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685-eeready---"></a>複数の Apple DEP および Apple School Manager アカウントに対する Intune サポート<!-- 747685 eeready -->

最大 100 個の異なる Apple Device Enrollment Program (DEP) または Apple School Manager アカウントからのデバイス登録が、Intune でサポートされます。 アップロードされる各トークンは、登録プロファイルとデバイスで、別々に管理できます。 アップロードされる DEP および School Manager のトークンごとに、異なる登録プロファイルを自動で割り当てることができます。 複数の School Manager トークンがアップロードされた場合、Microsoft 学校データ同期と共有できるのは、一度に 1 つのみです。

移行後、Graph で Apple DEP および ASM を管理するベータ版の Graph API と公開されたスクリプトは、動作しなくなります。 現在、新しいベータ版の Graph API の開発が進行中で、移行後にリリースされる予定です。

### <a name="remote-printing-over-a-secure-network----1709994----"></a>セキュリティで保護されたネットワークでのリモート印刷<!-- 1709994  -->
PrinterOn のワイヤレス モバイル印刷ソリューションは、時間や場所を問わない、セキュリティで保護されたネットワークでのリモート印刷を可能にします。 PrinterOn は、iOS 向けと Android 向けのどちらの Intune APP SDK とも統合します。 管理コンソールの Intune の **[アプリ保護ポリシー]** ブレードから、アプリ保護ポリシーのターゲットをこのアプリにすることもできます。 エンド ユーザーは、Play ストア、または iTunes から PrinterOn for Microsoft アプリをダウンロードして、Intune エコシステム内で使用できます。

### <a name="macos-company-portal-support-for-enrollments-that-use-the-device-enrollment-manager----1352411---"></a>デバイス登録マネージャーを使う登録の macOS ポータル サイトによるサポート <!-- 1352411 -->

ユーザーは、macOS ポータル サイトで登録するときに、デバイス登録マネージャーを使うことができるようになりました。

## <a name="week-of-january-29-2018"></a>2018 年 1 月 29 日の週

### <a name="device-enrollment"></a>デバイスの登録

#### <a name="alerts-for-expired-tokens-and-tokens-that-will-soon-expire----1639263---"></a>期限切れトークンと有効期限が近いトークンのアラート<!-- 1639263 -->
有効期限が切れているトークンと、有効期限が近づいているトークンのアラートが概要ページに表示されるようになりました。 1 つのトークンのアラートをクリックすると、そのトークンの詳細ページに移動します。  複数のトークンのアラートをクリックすると、トークンのステータスが表示された全トークンの一覧に移動します。 管理者は、有効期限が来る前にトークンを更新する必要があります。

### <a name="device-management"></a>デバイス管理

#### <a name="remote-erase-command-support-for-macos-devices----1438084---"></a>macOS デバイスのリモートの "消去" コマンド サポート <!-- 1438084 -->

管理者は、macOS デバイスの消去コマンドをリモートで発行できます。

> [!IMPORTANT]
> 消去コマンドは、元に戻すことができないため、使用する際は注意が必要です。

消去コマンドでは、オペレーティング システムを含むすべてのデータが、デバイスから削除されます。 また、そのデバイスも、Intune 管理から削除されます。 ユーザーに対して警告は表示されません。また、コマンドを発行すると、消去は即座に実行されます。

6 桁の回復用 PIN を構成する必要があります。 この PIN を使用すると、消去されたデバイスのロックが解除され、オペレーティング システムの再インストールが開始されます。 PIN は、消去が開始されると、Intune のデバイスの概要ブレードのステータス バーに表示されます。 消去が完了するまでの間、PIN はずっと表示されます。 消去が完了したら、デバイスは Intune 管理から完全に削除されます。 デバイスを復元する人が誰であっても、そのデバイスを使用できるように、回復用 PIN は必ず記録するようにしてください。

#### <a name="revoke-licenses-for-an-ios-volume-purchasing-program-token----820870---"></a>iOS Volume Purchasing Program トークンのライセンスの取り消し <!-- 820870 -->
特定の VPP トークンのすべての iOS Volume Purchasing Program (VPP) アプリのライセンスを取り消すことができます。

### <a name="app-management"></a>アプリ管理

#### <a name="revoking-ios-volume-purchase-program-apps-----820863---"></a>iOS Volume-Purchase Program アプリの取り消し  <!-- 820863 -->
1 つ以上の iOS Volume-Purchase Program (VPP) アプリがインストールされた特定のデバイスでは、そのデバイスで関連付けられているデバイス ベース アプリのライセンスを取り消すことができます。 アプリのライセンスを取り消しても、関連する VPP アプリがデバイスからアンインストールされるわけではありません。 VPP アプリをアンインストールするには、割り当てアクションを **[アンインストール]** に変更する必要があります。 詳細については、「[Volume Purchase Program で購入した iOS アプリを Microsoft Intune で管理する方法](vpp-apps-ios.md)」をご覧ください。

#### <a name="assign-office-365-mobile-apps-to-ios-and-android-devices-using-built-in-app-type----1332318---"></a>組み込み型のアプリを利用し、iOS デバイスまたは Android デバイスに Office 365 モバイル アプリを割り当てる <!-- 1332318 -->
**組み込み**型のアプリであれば、Office 365 アプリを作成し、管理している iOS または Android デバイスに割り当てることが簡単にできます。 これらのアプリには、Word、Excel、PowerPoint、OneDrive などの 0365 アプリがあります。 アプリの種類に特定のアプリを割り当て、アプリ情報構成を編集できます。

#### <a name="including-and-excluding-app-assignment-based-on-groups----1406920---"></a>グループに基づくアプリ割り当ての追加と除外<!-- 1406920 -->

アプリの割り当て時、および割り当ての種類の選択後に、含めるグループと、除外するグループを選択できます。

### <a name="device-configuration"></a>デバイス構成

#### <a name="you-can-assign-an-application-configuration-policy-to-groups-by-including-and-excluding-assignments-----1480316---"></a>割り当てを含めたり除外したりしてグループにアプリケーション構成ポリシーを割り当てることができる <!-- 1480316 -->

含める割り当てと除外する割り当ての組み合わせを使って、ユーザーとデバイスのグループにアプリケーション構成ポリシーを割り当てることができます。 割り当ては、グループのカスタム選択または仮想グループとして選べます。 仮想グループは、**すべてのユーザー**、**すべてのデバイス**、または**すべてのユーザーとすべてのデバイス**を含むことができます。

#### <a name="support-for-windows-10-edition-upgrade-policy------903672archived-1119689---"></a>Windows 10 エディション アップグレード ポリシーのサポート <!-- 903672(archived), 1119689 -->  
Windows 10 デバイスを Windows 10 Education、Windows 10 Education N、Windows 10 Professional、Windows 10 Professional N、Windows 10 Professional Education、Windows 10 Professional Education N にアップグレードする Windows 10 エディション アップグレード ポリシーを作成できます。Windows 10 エディションのアップグレードについては、「[Windows 10 エディションのアップグレードを構成する方法](edition-upgrade-configure-windows-10.md)」をご覧ください。

#### <a name="conditional-access-policies-for-intune-is-only-available-from-the-azure-portal-----1737088-1634311---"></a>Intune の条件付きアクセス ポリシーの利用可能場所が Azure Portal のみに<!-- 1737088 1634311 -->

このリリース以降では、[Azure Portal](https://portal.azure.com) の **[Azure Active Directory]** > **[条件付きアクセス]** から条件付きアクセス ポリシーを構成および管理する必要があります。 便宜上、**[Intune]**  >  **[条件付きアクセス]** の、Azure Portal 内にある Intune からこのブレードにアクセスすることもできます。

#### <a name="updates-to-compliance-emails---1637547---"></a>コンプライアンスのメールに対する変更 <!--1637547 -->

コンプライアンス違反のデバイスを報告するメールが送信される際、そのコンプライアンス違反のデバイスの詳細が含まれるようになります。


## <a name="week-of-january-22-2018"></a>2018 年 1 月 22 日の週

### <a name="intune-apps"></a>Intune アプリ

#### <a name="new-functionality-for-the-resolve-action-for-android-devices---1583480--"></a>Android デバイスの "解決" アクションの新機能 <!--1583480-->

Android 用ポータル サイト アプリは、[デバイス暗号化の問題](/intune-user-help/encrypt-your-device-android)を解決するために、**[デバイス設定の更新]** の "解決" アクションを拡張しています。

#### <a name="remote-lock-available-in-company-portal-app-for-windows-10---676506--"></a>Windows 10 用の Intune ポータル サイトで利用できるリモート ロック <!--676506-->
エンドユーザーは、Windows 10 向けポータル サイト アプリから自分のデバイスをリモートでロックできるようになりました。 この機能はエンド ユーザーがアクティブに使用しているローカル デバイスには表示されません。

#### <a name="easier-resolution-of-compliance-issues-for-the-company-portal-app-for-windows-10---676546--"></a>Windows 10 でポータル サイト アプリのコンプライアンスの問題解決が簡単に<!--676546-->
Windows デバイスを持つエンド ユーザーは、ポータル サイト アプリのコンプライアンス非対応の理由をタップできます。 可能であれば、問題を解決するのに適切な、設定アプリ内の場所がエンド ユーザーに直接表示されます。

## <a name="week-of-december-11-2017"></a>2017 年 12 月 11 日の週

### <a name="device-configuration"></a>デバイス構成

#### <a name="new-automatic-redeployment-setting----1469168---"></a>新しい自動再配置設定 <!-- 1469168 -->
**自動再展開**設定では、管理権限を持つユーザーが、デバイス ロック画面で **CTRL + Win + R** を使用してすべてのユーザー データとユーザー設定を削除できます。 このデバイスは自動的に再構成され、管理対象に再登録されます。 この設定には、[Windows 10] -> [デバイスの制限] -> [全般] -> [自動再展開] でアクセスできます。 詳細については、[Intune での Windows 10 のデバイス制限設定](device-restrictions-windows-10.md#general)に関するページをご覧ください。

#### <a name="support-for-additional-source-editions-in-the-windows-10-edition-upgrade-policy-----903672--1119689---"></a>Windows 10 エディションのアップグレード ポリシーにおける、その他のソース エディションのサポート<!-- 903672,  1119689 -->
Windows 10 エディションのアップグレード ポリシーを使用して、Windows 10 の他のエディション (Windows 10 Pro、Windows 10 Pro Education、Windows 10 Cloud など) からアップグレードできるようになりました。 以前のリリースでは、サポートされるエディションのアップグレードのパスは、今よりも限定されていました。 詳細については、[Windows 10 エディションのアップグレードを構成する方法](edition-upgrade-configure-windows-10.md)に関するページをご覧ください。

#### <a name="new-windows-defender-security-center-wdsc-device-configuration-profile-settings----1335507---"></a>新しい Windows Defender セキュリティ センター (WDSC) デバイス構成プロファイルの設定 <!-- 1335507 -->

Intune の **Windows Defender セキュリティ センター**という名前の Endpoint Protection に、デバイス構成プロファイル設定の新しいセクションが追加されます。 IT 管理者は、Windows Defender セキュリティ センター アプリで、エンドユーザーがどの機能にアクセス可能かを構成できます。 IT 管理者が Windows Defender セキュリティ センター アプリで、ある機能を非表示にすると、ユーザーのデバイスで、その機能に関連するすべての通知が非表示になります。

管理者が Windows Defender セキュリティ センター デバイス構成プロファイル設定で非表示にできる機能は、以下のとおりです。
- ウイルスと脅威の防止
- デバイスのパフォーマンスと正常性
- ファイアウォールとネットワーク保護
- アプリとブラウザー コントロール
- ファミリー オプション

IT 管理者は、ユーザーが受け取る通知をカスタマイズすることもできます。 たとえば、ユーザーが WDSC に表示される機能で生成されたすべての通知を受け取るか、または重要な通知のみを受け取るかを構成できます。 重要度の低い通知には、Windows Defender Antivirus のアクティビティに関する定期的な概要や、スキャン完了時の通知があります。 その他のすべての通知は重要とみなされます。 さらに、通知の内容自体をカスタマイズすることもできます。たとえば、IT 担当の連絡先情報を、ユーザーのデバイスに表示される通知に組み込むなどです。

#### <a name="multiple-connector-support-for-scep-and-pfx-certificate-handling----1361755---"></a>SCEP の複数コネクタ サポートと PFX 証明書処理 <!-- 1361755 -->

オンプレミス NDES コネクタを使用してデバイスに証明書を配信するお客様は、1 つのテナントに複数のコネクタを構成できるようになりました。

この新しい機能では、次のシナリオがサポートされています。

- **高可用性**

各 NDES コネクタは、Intune から証明書の要求を取得します。  1 つの NDES コネクタがオフラインになっても、その他のコネクタは要求の処理を続行できます。

#### <a name="customer-subject-name-can-use-aaddeviceid-variable-----1468599---"></a>カスタム サブジェクト名で AAD_DEVICE_ID 変数が使用可能に<!-- 1468599 -->

Intune で SCEP 証明書プロファイルを作成する際、カスタム サブジェクト名の作成時に AAD_DEVICE_ID 変数を使用できるようになりました。   この SCEP プロファイルを使用して証明書が要求されると、証明書の要求を行っているデバイスの AAD デバイス ID が、この変数に置き換わります。


### <a name="device-management"></a>デバイス管理

#### <a name="manage-jamf-enrolled-macos-devices-with-intunes-device-compliance-engine----1592747---"></a>Intune のデバイス コンプライアンス エンジンを使用した Jamf に登録された macOS デバイスの管理 <!-- 1592747 -->
Jamf を使って、macOS デバイスの状態情報を Intune に送信できるようになりました。情報はその後、Intune コンソールで定義されたポリシーに準拠しているかどうかが評価されます。 条件付きアクセスでは、デバイスのコンプライアンス対応状態や、その他の条件 (場所やユーザー リスクなど) に基づいて、Azure AD に接続されたクラウド アプリケーションやオンプレミス アプリケーション (Office 365 など) にアクセスする macOS デバイスにコンプライアンスを適用します。 [Jamf 統合の設定](conditional-access-integrate-jamf.md)と [Jamf で管理されたデバイスのコンプライアンスの強制](conditional-access-assign-jamf.md)について、詳細をご覧ください。

#### <a name="new-ios-device-action------1424701---"></a>新しい iOS デバイス アクション <!-- 1424701 -->

iOS 10.3 監視下のデバイスをシャット ダウンできるようになりました。 このアクションでは、エンド ユーザーへの警告なしにデバイスが即時シャットダウンされます。 **シャット ダウン (監視モードのみ)** アクションは、**デバイス** ワークロードでデバイスを選択した場合に、デバイス プロパティに表示されます。

#### <a name="disallow-datetime-changes-to-samsung-knox-devices----1468103---"></a>Samsung KNOX デバイスへの日付および時刻の変更禁止 <!-- 1468103 -->

Samsung KNOX デバイスでの日付と時刻の変更をブロックできる機能が新たに追加されました。 この機能は、**[デバイス構成プロファイル]** > **[デバイスの制限 (Android)]** > **[全般]** にあります。

#### <a name="surface-hub-resource-account-supported----1566442----"></a>サポートされる Surface Hub リソース アカウント <!-- 1566442  -->

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

#### <a name="install-office-apps-on-macos-devices----1494311---"></a>macOS デバイスでの Office アプリのインストール <!-- 1494311 -->
macOS デバイスで Office アプリをインストールできるようになりました。 この新しい種類のアプリでは、Word、Excel、PowerPoint、Outlook、OneNote をインストールできます。 これらのアプリには Microsoft AutoUpdate (MAU) も付属しており、アプリを安全かつ最新に保つことができます。

### <a name="app-management"></a>アプリ管理

#### <a name="delete-an-ios--volume-purchasing-program-token----820879---"></a>iOS Volume Purchasing Program トークンのライセンスの削除 <!-- 820879 -->
コンソールを使用して、iOS Volume Purchasing Program (VPP) トークンを削除できます。 VPP トークンのインスタンスが重複している場合に、これが必要になることがあります。

### <a name="intune-apps"></a>Intune アプリ


### <a name="role-based-access-control"></a>ロールベースのアクセス制御

#### <a name="a-new-entity-collection-named-current-user-is-limited-to-currently-active-user-data----1667026---"></a>現在のユーザーという名前の新しいエンティティ コレクションは、現在アクティブなユーザー データに限られています <!-- 1667026 -->

**ユーザー** エンティティ コレクションには、社内のすべての Azure Active Directory (Azure AD) ユーザーと割り当てられているライセンスが表示されます。 たとえば、ユーザーが Intune に追加され、過去 1 か月の過程で削除されたとします。 このユーザーがレポートの時点では存在しない一方で、ユーザーと状態はデータに存在します。 データ内のユーザーの履歴における存在の期間を示すレポートを作成できます。

これに対し、新しい**現在のユーザー** エンティティ コレクションには、削除されていないユーザーのみが含まれています。 **現在のユーザー** エンティティ コレクションには、現在アクティブなユーザーのみが含まれています。 **現在のユーザー** エンティティ コレクションの詳細については、「[現在のユーザー エンティティのリファレンス](reports-ref-current-user.md)」をご覧ください。


### <a name="updated-graph-apis----1736360---"></a>Graph API の変更 <!-- 1736360 -->

このリリースでは、Intune のベータ版の Graph API にいくつか変更を加えました。 詳細については、[Graph API の変更ログ](https://developer.microsoft.com/graph/docs/concepts/changelog)のページ (毎月更新) をご覧ください。

## <a name="week-of-december-4-2017"></a>2017 年 12 月 4 日の週

### <a name="monitor-and-troubleshoot"></a>監視とトラブルシューティング

#### <a name="intune-supports-windows-information-protection-wip-denied-apps----1479103---"></a>Intune では Windows Information Protection (WIP) で拒否されたアプリがサポートされる<!-- 1479103 -->
拒否されたアプリを Intune で指定することができます。 アプリが拒否された場合、企業の情報へのアクセスがブロックされます。これは事実上、許可されたアプリ リストの反対です。 詳しくは、[Windows 情報保護の推奨される拒否リスト](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp?f=255&MSPPError=-2147217396#recommended-deny-list-for-windows-information-protection)を参照してください。


## <a name="week-of-november-27-2017"></a>2017 年 11 月 27 日の週

### <a name="device-enrollment"></a>デバイスの登録

#### <a name="troubleshoot-enrollment-issues-----746324---"></a>登録に関する問題をトラブルシューティングする <!-- 746324 -->

**トラブルシューティング** ワークスペースに、ユーザーの登録に関する問題が表示されるようになりました。 問題に関する詳細と推奨される修復手順は、管理者およびヘルプ デスクのオペレーターが問題をトラブルシューティングするのに役立ちます。 登録に関する特定の問題はキャプチャされず、一部のエラーには推奨される修復方法がない場合があります。

#### <a name="group-assigned-enrollment-restrictions----747598---"></a>グループ割り当て登録制限 <!-- 747598 -->

Intune 管理者は[ユーザー グループに対してカスタムの登録制限として [デバイスの種類] と [デバイスの上限数] を作成できるようになりました](enrollment-restrictions-set.md)。

Intune Azure ポータルで、制限タイプごとに最大 25 個のインスタンスを作成できます。作成したインスタンスはユーザー グループに割り当てることができます。 グループに割り当てられた制限は既定の制限をオーバーライドします。

制限タイプのすべてのインスタンスは、厳密に順序付けられた一覧で保守管理されます。 この順序により、競合解決の優先度の値が決まります。 複数の制限インスタンスの影響を受けるユーザーは、優先度の値が最も高いインスタンスによって制限されます。 インスタンスの優先度は、一覧内の別の位置にドラッグすることによって変更できます。

Android For Work 登録メニューから登録制限メニューに Android For Work 設定が移行されたとき、この機能が使えるようになります。 この移行には数日かかる場合があります。11 月リリースのその他の部分に関してアカウントがアップグレードされた後に、登録制限のグループ割り当てが有効になる場合があります。

#### <a name="support-for-multiple-network-device-enrollment-service-ndes-connectors----1528104---"></a>複数のネットワーク デバイス登録サービス (NDES) コネクタのサポート <!-- 1528104 -->

NDES を利用すれば、ドメイン資格情報なしでモバイル デバイスを実行し、Simple Certificate Enrollment Protocol (SCEP) に基づいて証明書を取得できます。
今回の更新で、複数の NDES コネクタがサポートされるようになりました。

#### <a name="manage-android-for-work-devices-independently-from-android-devices----1490731-eeready--"></a>Android デバイスとは別に Android for Work デバイスを管理する <!-- 1490731 EEready-->

Intune は、Android プラットフォームに依存することなく、Android for Work デバイスの登録を管理します。 この設定は、**[デバイスの登録]**、 > **[登録制限]**、 > **[デバイスの種類の制限]** で管理されます。 (以前の場所は **[デバイス登録]**、 > **[Android for Work への登録]**、 > **[Android for Work の登録設定]** でした。)

既定では、Android for Work デバイス設定は Android デバイスの設定と同じになります。 ただし、Android for Work 設定を変更した後は、同じではなくなります。

個人の Android for Work 登録をブロックした場合、会社の Android デバイスのみを Android for Work として登録できます。

新しい設定を使用する場合、次の点を考慮してください。

##### <a name="if-you-have-never-previously-onboarded-android-for-work-enrollment"></a>以前に Android for Work 登録をオンボードしたことがない

新しい Android for Work プラットフォームは、既定の [デバイスの種類の制限] でブロックされます。 この機能をオンボードした後は、デバイスを Android for Work に登録できます。 そのためには、既定値を変更するか、新しい [デバイスの種類の制限] を作成して既定の [デバイスの種類の制限] に代えます。

##### <a name="if-you-have-onboarded-android-for-work-enrollment"></a>Android for Work 登録をオンボードした

以前にオンボードしている場合、状況は選んだ設定によって変わります。

| Setting | 既定の [デバイスの種類の制限] の Android for Work の状態 | 注 |
| --- | --- | --- |
| **すべてのデバイスを Android として管理する** | ［ブロック済み］ | すべての Android デバイスを Android for Work なしで登録する必要があります。 |
| **サポートされているデバイスを Android for Work として管理する** | 許可済み | Android for Work 対応のすべての Android デバイスを Android for Work に登録する必要があります。 |
| **これらのグループに所属するユーザーのサポートされているデバイスのみを Android for Work として管理する** | ［ブロック済み］ | 既定値をオーバーライドする別個の [デバイスの種類の制限] ポリシーが作成されました。 このポリシーによって、以前に選択したグループで Android for Work 登録が許可されます。 選択されたグループ内のユーザーには、Android for Work デバイスの登録が引き続き許可されます。 その他すべてのユーザーには、Android for Work の登録が禁止されます。 |

いずれの場合でも、意図した規制が維持されます。 自分の環境で Android for Work のグローバル許可またはグループ別許可を維持するための操作は必要ありません。

### <a name="app-management"></a>アプリ管理

#### <a name="app-install-report-updated-to-include-install-pending-status----1249446---"></a>インストール保留中の状態を含むように更新されたアプリ インストール レポート<!-- 1249446 -->  

**[モバイル アプリ]** ワークロードの **[アプリ]** 一覧から表示できるアプリ別の **[アプリ インストールの状態]** レポートが、ユーザーとデバイスについて **[インストール保留中]** カウントを表示するようになりました。

#### <a name="ios-11-app-inventory-api-for-mobile-threat-detection----1391759---"></a>モバイルの脅威を検出するための iOS 11 アプリ インベントリ API <!-- 1391759 -->

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


### <a name="device-management"></a>デバイス管理

#### <a name="migrate-hybrid-mdm-users-and-devices-to-intune-standalone----1463747-wnready---"></a>ハイブリッド MDM のユーザーとデバイスを Intune スタンドアロンに移行する<!-- 1463747 wnready -->
ハイブリッド MDM から Azure Portal 内の Intune にユーザーとそのデバイスを移動するための新しいプロセスとツールが利用可能になりました。これにより、次の操作を行うことができます。
- Configuration Manager コンソールから Azure Portal 内の Intune にポリシーとプロファイルをコピーする
- ユーザーのサブセットを Azure Portal 内の Intune に移動し、残りのユーザーをハイブリッド MDM で保持したままにする
- 再登録せずに、Azure Portal 内の Intune にデバイスを移行する

詳しくは、「[ハイブリッド MDM のユーザーとデバイスを Intune スタンドアロンに移行する](https://docs.microsoft.com/sccm/mdm/deploy-use/migrate-hybridmdm-to-intunesa)」を参照してください。

#### <a name="on-premises-exchange-connector-high-availability-support-----676614---"></a>オンプレミスの Exchange Connector の高可用性のサポート  <!-- 676614 -->
Exchange Connector によって、指定の CAS で Exchange への接続が作成された後、コネクタで別の CAS も検出できるようになりました。 メインの CAS が利用できなくなった場合、再度利用可能になるまで、コネクタが別の CAS (ある場合) にフェールオーバーします。 詳細については、「[オンプレミスの Exchange Connector の高可用性のサポート](exchange-connector-install.md#on-premises-exchange-connector-high-availability-support)」をご覧ください。

#### <a name="remotely-restart-ios-device-supervised-only----1424595---"></a>iOS デバイスをリモート再起動する (監視モードのみ) <!-- 1424595 -->

デバイス アクションを利用し、監視されている iOS 10.3 以降のデバイスの再起動をトリガーできるようになりました。 デバイス再起動アクションの利用方法については、「[Intune でデバイスをリモートで再起動する](device-restart.md)」を参照してください。

> [!Note]
> このコマンドは、監視されているデバイスと**デバイス ロック** アクセス権を要求します。 デバイスがすぐに再起動します。 パスコードでロックされている iOS デバイスが再起動後に Wi-Fi ネットワークに再び参加することはありません。再起動後、サーバーと通信できないことがあります。

#### <a name="single-sign-on-support-for-ios----1333645---"></a>iOS のシングル サインオン サポート <!-- 1333645 -->  

iOS ユーザーのためにシングル サインオンを使用できます。 シングル サインオン ペイロードのユーザー資格情報を探すようにプログラミングされている iOS アプリは、このペイロード構成更新で機能します。 UPN と Intune デバイス ID を利用し、プリンシパル名と領域を構成することもできます。 詳しくは、「[Configure Intune for iOS device single sign-on](sso-ios.md)」 (iOS 用 Intune のデバイス シングル サインオンを構成する) を参照してください。

#### <a name="add-find-my-iphone-for-personal-devices---1427287--"></a>個人デバイスの "iPhone を探す" を追加 <!--1427287-->
iOS デバイスのアクティベーション ロックがオンになっているかどうかを表示できるようになりました。 この機能は以前、クラシック ポータルの Intune にありました。


#### <a name="remotely-lock-managed-macos-device-with-intune----1437691---"></a>管理されている macOS デバイスを Intune でリモート ロックする <!-- 1437691 -->

紛失した macOS デバイスをロックできます。6 桁の回復用 PIN を設定できます。 ロックされているとき、別のデバイス アクションが送信されるまで、**デバイス概要**ブレードにその PIN が表示されます。

詳細については、「[管理されたデバイスを Intune でリモートからロックする](device-remote-lock.md)」を参照してください。

#### <a name="new-scep-profile-details-supported----1559808---"></a>サポートされる新しい SCEP プロファイル詳細 <!-- 1559808 -->

Windows、iOS、macOS、Android プラットフォームで SCEP プロファイルを作成するとき、管理者は追加設定を設定できるようになりました。  管理者は、IMEI、シリアル番号、あるいはサブジェクト名の形式の電子メールなど、一般名を設定できます。

<!-- #### Update to what device details your company may see -1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources. -->

#### <a name="retain-data-during-a-factory-reset----1588489---"></a>工場出荷時の設定へのリセット中にデータを保持する <!--1588489 -->
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

### <a name="monitor-and-troubleshoot"></a>監視とトラブルシューティング
#### <a name="window-10-update-ring-assignments-are-displayed----1621837---"></a>Windows 10 更新プログラム リング割り当てが表示される <!-- 1621837 -->
**トラブルシューティング**時、表示しているユーザーに関して、Windows 10 更新プログラム リング割り当てを表示することができます。  

#### <a name="windows-defender-advanced-threat-protection-reporting-frequency-settings-----1455974----"></a>Windows Defender Advanced Threat Protection の報告頻度設定 <!-- 1455974  -->
Windows Defender Advanced Threat Protection (WDATP) サービスを利用するとき、管理者は管理対象デバイスの報告頻度を管理できます。 新しい **[テレメトリの報告頻度を早める]** オプションを利用すると、WDATP はデータを収集し、さらに頻繁にリスクを評価します。 報告の既定値で速度とパフォーマンスが最適化されます。 報告の頻度を増やすことは、リスクの高いデバイスの場合に有益となります。 この設定は **[デバイス構成]** の **[Windows Defender ATP]** プロファイルにあります。

#### <a name="audit-updates----1412961---"></a>監査更新 <!-- 1412961 -->  
Intune の監査機能により、Intune に関連する変更操作が記録されます。  あらゆる作成操作、更新操作、削除操作、リモート タスク操作が記録され、1 年間保存されます。  Azure Portal では、ワークロード別の監査データを過去 30 日分表示できます。データの絞り込みも可能です。  対応する Graph API により、前年に格納された監査データを取得できます。

監査は **[モニター]** グループの下にあります。 ワークロード別に **[監査ログ]** メニュー項目があります。




## <a name="week-of-november-20-2017"></a>2017 年 11 月 20 日の週

### <a name="app-management"></a>アプリ管理

#### <a name="google-play-protect-support-on-android----908720---"></a>Android の Google Play Protect サポート <!-- 908720 -->

Android Oreo のリリースに伴い、セキュリティで保護されたアプリおよび Android イメージをユーザーや組織が実行できる、Google Play Protect という一連のセキュリティ機能が Google より提供されました。 Intune では、SafetyNet リモート構成証明をはじめとした Google Play Protect の各機能をサポートするようになりました。 管理者は、Google Play Protect が構成され正常な状態であることが求められるコンプライアンス ポリシー要件を設定できます。
**[SafetyNet デバイスの構成証明]** 設定では、デバイスが正常な状態であり危険にさらされていないことを確認するために、デバイスを Google サービスに接続する必要があります。 管理者は、インストール済みのアプリが Google Play 開発者サービスによって検証されることを必須にする、Android for Work の構成プロファイル設定を設定することもできます。 デバイスが Google Play Protect の要件に準拠していない場合、条件付きアクセスでは、ユーザーが企業リソースにアクセスできなくなる可能性があります。

- 「[デバイスのコンプライアンス ポリシーを作成して Google Play Protect を有効にする方法](https://docs.microsoft.com/intune/compliance-policy-create-google-play-protect)」を参照してください。

#### <a name="text-protocol-allowed-from-managed-apps----1414050----"></a>管理対象アプリから許可されるテキスト プロトコル <!-- 1414050  -->

Intune App SDK によって管理されているアプリは、SMS メッセージを送信できます。

## <a name="week-of-november-13-2017"></a>2017 年 11 月 13 日の週

### <a name="intune-apps"></a>Intune アプリ
#### <a name="company-portal-app-for-macos-is-available---1541700--"></a>macOS 用ポータル サイト アプリ提供開始 <!--1541700-->
macOS での Intune ポータル サイトのエクスペリエンスが更新されました。ユーザーが登録済みのすべてのデバイスで必要となるすべての情報とコンプライアンス通知が明確に表示されるように最適化されました。 また、いったん Intune ポータル サイトをデバイスに展開すると、macOS 用 Microsoft 自動更新から更新プログラムが提供されるようになります。 macOS デバイスから Intune ポータル サイトにログインすることで、新しい macOS 用 Intune ポータル サイトをダウンロードできます。

#### <a name="microsoft-planner-is-now-part-of-the-mobile-app-management-mam-list-of-approved-apps-----1248473---"></a>Microsoft Planner が承認済みアプリのモバイル アプリ管理 (MAM) リストの一部に <!-- 1248473 -->
iOS および Android 用の Microsoft Planner アプリが、承認済みアプリのモバイル アプリ管理 (MAM) の一部となりました。 このアプリは、Azure Portal の Intune App Protection ブレードからすべてのテナントに対して構成できます。
- 詳細については、[承認済みアプリの MAM リスト](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)に関するページをご覧ください。

#### <a name="per-app-vpn-requirement-update-frequency-on-ios-devices------1547061---"></a>iOS デバイスでのアプリごとの VPN 要件の更新頻度 <!-- 1547061 -->  
管理者が iOS デバイス上のアプリでアプリごとの VPN 要件を削除できるようになりました。影響を受けるデバイスでは、次回の Intune チェックイン後、通常 15 分以内に反映されます。  

### <a name="monitor-and-troubleshoot"></a>監視とトラブルシューティング
#### <a name="support-for-system-center-operations-manager-management-pack-for-exchange-connector----885457---"></a>Exchange Connector 用 System Center Operations Manager 管理パックのサポート <!-- 885457 -->
Exchange Connector 用 System Center Operations Manager (SCOM) 管理パックを Exchange Connector のログ解析に利用できるようになります。 この機能により、問題のトラブルシューティングが必要な場合に、別の方法でサービスを監視できるようになります。

## <a name="week-of-november-6-2017"></a>2017 年 11 月 6 日の週

### <a name="device-enrollment"></a>デバイスの登録
#### <a name="co-management-for-windows-10-devices-----1243445---"></a>Windows 10 デバイスの共同管理 <!-- 1243445 -->
共同管理は、従来の管理から最新の管理への橋渡しとなるソリューションであり、段階的なアプローチを使って移行する方向を提示します。 基本的に、共同管理は、Windows 10 デバイスを Configuration Manager と Microsoft Intune で同時に管理すると共に、Active Directory (AD) と Azure Active Directory (Azure AD) に同時に参加させることができるソリューションです。  この構成は、一度にすべてを移行できない組織が適切なペースで時間をかけて最新化するパスを提供します。  

#### <a name="restrict-windows-enrollment-by-os-version----245498---"></a>OS のバージョンによる Windows 登録の制限 <!-- 245498 -->
Intune 管理者は、デバイス登録に関して、Windows 10 の最小バージョンと最大バージョンを指定できるようになりました。 これらの制限は **[プラットフォーム構成]** ブレードで設定できます。

Intune では、Windows 8.1 の PC とスマートフォンを引き続き登録できます。 ただし、下限と上限を設定できるのは Windows 10 のバージョンだけです。 8.1 デバイスの登録を許可するには、下限を空のままにします。

#### <a name="alerts-for-windows-autopilot-unassigned-devices-----1631236---"></a>Windows AutoPilot の未割り当てデバイスのアラート <!-- 1631236 -->
**[Microsoft Intune]**、**[デバイス登録]**、**[概要]** ページには、Windows AutoPilot の未割り当てデバイスの新しいアラートがあります。 このアラートでは、AutoPilot プログラムからのデバイスで、AutoPilot Deployment プロファイルが割り当てられていないデバイスの数が示されます。 アラート内の情報を利用してプロファイルを作成し、未割り当てデバイスに割り当てます。 アラートをクリックすると、Windows AutoPilot の完全一覧とそれらに関する詳細が表示されます。 詳細については、「[Windows AutoPilot Deployment プログラムを使用して Windows デバイスを登録する](https://docs.microsoft.com/intune/enrollment-autopilot)」を参照してください。

### <a name="device-management"></a>デバイス管理

#### <a name="refresh-button-for-devices-list-------1333581---"></a>デバイス一覧の [更新] ボタン <!-- 1333581 -->
デバイス一覧は自動的に更新されないため、新しい [更新] ボタンを利用し、一覧に表示されるデバイスを更新できます。

#### <a name="support-for-symantec-cloud-certification-authority-ca-----1333638---"></a>Symantec クラウド証明機関 (CA) のサポート <!-- 1333638 -->    
Intune は Symantec クラウド CA をサポートするようになり、Intune Certificate Connector は Symantec クラウド CA から Intune で管理対象デバイスに PKCS 証明書を発行できます。 Microsoft 証明機関 (CA) で Intune Certificate Connector を既に使っている場合は、Intune Certificate Connector の既存の設定を使用して、Symantec CA のサポートを追加できます。

#### <a name="new-items-added-to-device-inventory-----1404455---"></a>デバイス インベントリに追加された新しい項目 <!--1404455 -->
[登録デバイスによって取得されるインベントリ](device-inventory.md)で次の新しい項目を利用できるようになりました。

- Wi-Fi MAC アドレス
- 記憶域の合計容量
- 合計空き容量
- MEID
- 通信事業者


### <a name="app-management"></a>アプリ管理
#### <a name="set-access-for-apps-by-minimum-android-security-patch-on-the-device---1278463---"></a>デバイスでの最低限の Android セキュリティ パッチによりアプリへのアクセスを設定する <!-- 1278463 -->   
管理者は、管理されたアカウントの管理対象アプリケーションにアクセスするために、デバイスにインストールする必要がある最低限の Android セキュリティ パッチを定義することができます。

> [!Note]  
> この機能は、Google によって Android 6.0 以降のデバイスについてリリースされたセキュリティ パッチだけを制限します。

#### <a name="app-conditional-launch-support----1193313---"></a>アプリの条件付き起動のサポート <!-- 1193313 -->
IT 管理者は、アプリケーションの起動時にモバイル アプリ管理 (MAM) によって数値の PIN ではなくパスコードを強制する要件を、Azure 管理ポータルで設定できるようになりました。 構成した場合、ユーザーは、MAM 対応のアプリケーションにアクセスする前に、要求された時点で、パスコードを設定および使用する必要があります。 パスコードは、少なくとも 1 つの特殊文字または大文字/小文字アルファベットを含む数値 PIN と定義されます。 Intune の今回のリリースでは、この機能を利用できるのは **iOS のみ**です。 Intune は、数値 PIN に同様の方法でパスコードをサポートし、最小の長さを設定して、文字やシーケンスの繰り返しを許可します。 この機能では、対象のアプリケーションにパスコード設定を適用するのではなく、Intune アプリ SDK とこの機能のコードとを統合するために、アプリケーション (WXP、Outlook、Managed Browser、Yammer など) の参加が必要となります。

#### <a name="app-version-number-for-line-of-business-in-device-install-status-report----1233999---"></a>デバイス インストール状態レポートでの基幹業務アプリのバージョン番号 <!-- 1233999 -->
このリリースでは、デバイス インストール状態レポートに、iOS および Android 用基幹業務アプリのバージョン番号が表示されます。 この情報を使って、アプリのトラブルシューティングや、古いバージョンのアプリを実行しているデバイスの検索を行うことができます。


### <a name="device-configuration"></a>デバイス構成
#### <a name="admins-can-now-configure-the-firewall-settings-on-a-device-using-a-device-configuration-profile----951708---"></a>管理者は、デバイス構成プロファイルを使ってデバイスでのファイアウォールの設定を構成できるようになる <!-- 951708 -->   
管理者は、デバイスのファイアウォールを有効にすることができ、ドメイン ネットワーク、プライベート ネットワーク、パブリック ネットワークのさまざまなプロトコルを構成することもできます。  これらのファイアウォールの設定は、"Endpoint Protection" プロファイルで確認できます。

#### <a name="windows-defender-application-guard-helps-protect-devices-from-untrusted-websites-as-defined-by-your-organization----958257---"></a>Windows Defender Application Guard は、組織での定義に従って、信頼されていない Web サイトからデバイスを保護する <!-- 958257 -->   
管理者は、Windows Information Protection ワークフローまたはデバイス構成の新しい "ネットワーク境界" プロファイルを使って、"信頼できる" サイトまたは "企業" サイトを定義できます。 64 ビット Windows 10 デバイスの信頼されたネットワーク境界内にないすべてのサイトは、Microsoft Edge で表示された場合、代わりに Hyper-V 仮想コンピューター内のブラウザーで開かれます。

Application Guard は、"Endpoint Protection" プロファイル内のデバイス構成プロファイルで確認できます。 デバイス構成プロファイルでは、管理者は、仮想化されたブラウザーとホスト マシンの相互作用、信頼されないサイトと信頼されるサイト、および仮想化されたブラウザーで生成されたファイルの保存を構成することができます。 デバイスで Application Guard を使うには、最初にネットワーク境界を構成する必要があります。 デバイスごとにネットワーク境界を 1 つだけ定義することが重要です。  

#### <a name="windows-defender-application-control-on-windows-10-enterprise-provides-mode-to-trust-only-authorized-apps----1031096---"></a>Windows 10 Enterprise の Windows Defender Application Control は、承認されたアプリのみを信頼するモードを提供する <!-- 1031096 -->    
毎日何千もの悪意あるファイルが作成される状況においては、ウイルス対策の署名ベースの検出を使ってマルウェアに対抗するのでは、新しい攻撃を十分に防ぐことができない可能性があります。 Windows 10 Enterprise の Windows Defender Application Control を使うと、ウイルス対策ソフトウェアや他のセキュリティ ソリューションによってブロックされない限りアプリを信頼するモードから、企業によって承認されたアプリのみをオペレーティング システムが信頼するモードにデバイスの構成を変更できます。 Windows Defender Application Control でアプリに信頼を割り当てます。

Intune を使って、アプリケーション制御ポリシーを "監査のみ" モードまたは強制モードに構成できます。 "監査のみ" モードで実行している場合、アプリはブロックされません。 "監査のみ" モードでは、すべてのイベントがローカル クライアント ログに記録されます。 また、Windows コンポーネントと Microsoft Store アプリの実行のみを許可するか、またはインテリジェント セキュリティ グラフで定義されている評判の良いアプリの実行も許可するかを構成することもできます。

#### <a name="window-defender-exploit-guard-is-a-new-set-of-intrusion-prevention-capabilities-for-windows-10----1063615---"></a>Windows 10 用の新しい侵入防止機能セットである Window Defender Exploit Guard <!-- 1063615 -->   
Window Defender Exploit Guard は、アプリケーションが悪用される可能性を減らすカスタム規則を含み、マクロとスクリプトの脅威を防止し、評判が低い IP アドレスへのネットワーク接続を自動的にブロックして、ランサムウェアや不明の脅威からデータを保護できます。 Windows Defender Exploit Guard は、次のコンポーネントで構成されます。

- **攻撃の回避 (ASR)** は、マクロ、スクリプト、メールの脅威を防ぐことができる規則を提供します。
- **フォルダー アクセスの制御**は、保護されているフォルダーのコンテンツへのアクセスを自動的にブロックします。
- **ネットワーク フィルター**は、アプリから評判の悪い IP/ドメインへの発信接続をブロックします。
- **Exploit Protection** は、アプリケーションを悪用から保護するために使うことができるメモリ、制御フロー、およびポリシーの制限を提供します。


#### <a name="manage-powershell-scripts-in-intune-for-windows-10-devices----790537---"></a>Windows 10 デバイスの Intune で PowerShell スクリプトを管理する <!-- 790537 -->

Intune 管理拡張機能を使用すると、Windows 10 デバイスで実行されている Intune で PowerShell スクリプトをアップロードできます。 この拡張機能は Windows 10 モバイル デバイス管理 (MDM) 機能を補完するもので、最新の管理に簡単に移行できます。 詳細については、「[Windows 10 デバイスの Intune で PowerShell スクリプトを管理する](intune-management-extension.md)」を参照してください。

#### <a name="new-device-restriction-settings-for-windows-10---------1308850---"></a>Windows 10 の新しいデバイスの制限設定 <!-- 1308850 -->
-    メッセージング (モバイルのみ) - テストまたは MMS のメッセージを無効化します
-    パスワード - FIPS と、認証用の Windows Hello デバイス セカンダリ デバイスの使用を有効にする設定 
-    ディスプレイ - レガシ アプリの GDI スケーリングをオンまたはオフにする設定

#### <a name="windows-10-kiosk-mode-device-restrictions----1308872---"></a>Windows 10 キオスク モード デバイスの制限 <!-- 1308872 -->   
Windows 10 デバイスのユーザーをキオスク モードに制限することができます。これは、一連の定義済みアプリにユーザーを制限します。  そのためには、Windows 10 デバイス制限プロファイルを作成し、キオスク設定を設定します。

キオスク モードは、**シングル アプリ** (1 つのアプリだけの実行をユーザーに許可) または**マルチ アプリ** (アプリのセットへのアクセスを許可) の 2 つのモードをサポートします。  ユーザー アカウントとデバイス名を定義します。これらにより、サポートされるアプリが決まります。  ユーザーはログイン時に定義済みのアプリに制限されます。  詳細については、「[AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp)」を参照してください。 

キオスク モードには以下が必要です。

- Intune が MDM 機関である必要があります。
- アプリは、ターゲット デバイスに既にインストールされている必要があります。
- デバイスは、[適切にプロビジョニングされている](https://docs.microsoft.com/windows/configuration/set-up-a-kiosk-for-windows-10-for-desktop-editions)必要があります。

#### <a name="new-device-configuration-profile-for-creating-network-boundaries----1311967---"></a>ネットワーク境界を作成するための新しいデバイス構成プロファイル <!-- 1311967 -->   
**ネットワーク境界**と呼ばれる新しいデバイス構成プロファイルが、他のデバイス構成プロファイルと同じ場所にあります。 このプロファイルを使用して、会社のもので信頼できると見なす必要があるオンライン リソースを定義します。 Windows Defender Application Guard や Windows Information Protection などの機能をデバイスで使用するには、"*事前*" にデバイスに対してネットワーク境界を定義する必要があります。 デバイスごとにネットワーク境界を 1 つだけ定義することが重要です。

信頼できるエンタープライズ クラウド リソース、IP アドレス範囲、内部プロキシ サーバーを定義できます。 定義したネットワーク境界は、Windows Defender Application Guard や Windows Information Protection 保護などの他の機能で使うことができます。

####  <a name="two-additional-settings-for-windows-defender-antivirus----1338409---"></a>Windows Defender ウイルス対策用の 2 つの追加設定<!-- 1338409 -->  
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

#### <a name="citrix-vpn-added-for-windows-10-devices----1512457---"></a>Windows 10 デバイスに追加された Citrix VPN <!-- 1512457 -->  
Windows 10 デバイス用に Citrix VPN を構成できます。 Windows 10 以降用に VPN を構成するときに、**[基本 VPN]** ブレードの *[接続の種類を選びます]* の一覧で、Citrix VPN を選ぶことができます。

> [!Note]
> Citrix の構成は、iOS および Android 用に存在しました。

#### <a name="wi-fi-connections-support-pre-shared-keys-on-ios----1550823---"></a>Wi-Fi 接続は iOS で事前共有キーに対応 <!-- 1550823 -->
ユーザーは iOS デバイスで WPA/WPA2 Personal 接続に事前共有キー (PSK) を使用するように Wi-Fi プロファイルを構成できます。 これらのプロファイルは、デバイスが Intune に登録されたとき、ユーザーのデバイスにプッシュされます。

プロファイルがデバイスにプッシュされたとき、次の手順はプロファイル構成によって決まります。  自動的に接続するように設定されている場合、ネットワークが次に必要になったとき、自動的に接続されます。  プロファイルが手動接続になっている場合、ユーザーは接続を手動で開始する必要があります。  

### <a name="intune-apps"></a>Intune アプリ

#### <a name="access-to-managed-app-logs-for-ios----1469920---"></a>iOS の管理対象アプリ ログにアクセス <!-- 1469920 -->
Managed Browser をインストールしているエンド ユーザーは、Microsoft が公開したあらゆるアプリの管理状態を表示し、管理対象 iOS アプリの問題を解消するためにログを送信できるようになりました。

iOS デバイスの Managed Browser でトラブルシューティング モードを有効にする方法については、「[iOS で Managed Browser を使用し、管理対象アプリ ログにアクセスする方法](app-configuration-managed-browser.md#how-to-access-to-managed-app-logs-using-the-managed-browser-on-ios)」を参照してください。

#### <a name="improvements-to-device-setup-workflow-in-the-company-portal-for-ios-in-version-290----1417174---"></a>iOS 用ポータル サイト バージョン 2.9.0 でのデバイスのセットアップ ワークフローの機能強化<!-- 1417174 -->

iOS 用ポータル サイト アプリでのデバイス セットアップ ワークフローが改善されました。 言葉がよりわかりやすくなり、可能な範囲で画面をまとめました。 セットアップのテキスト全体でお客様の会社名を使用することで、表現がより会社に合ったものになっています。 この更新されたワークフローについては、 [アプリ UI ページの新機能](whats-new-app-ui.md)に関するページをご覧ください。

### <a name="monitor-and-troubleshoot"></a>監視とトラブルシューティング

#### <a name="user-entity-contains-latest-user-data-in-data-warehouse-data-model----1544273---"></a>ユーザー エンティティにデータ ウェアハウス データ モデルの最新のユーザー データが含まれている<!-- 1544273 -->
Intune データ ウェアハウス データ モデルの最初のバージョンでは、最近の Intune 履歴データのみが含まれていました。 レポートの作成者は、ユーザーの最新の状態をキャプチャできませんでした。 今回の更新プログラムでは、最新のユーザー データを使用して**ユーザー エンティティ**が設定されます。


## <a name="notices"></a>通知

### <a name="plan-for-change-new-windows-10-setting-for-kiosk-configuration-in-intune----1560072---"></a>変更の計画: Intune でのキオスク構成のための新しい Windows 10 設定 <!-- 1560072 -->
Intune Azure Portal で Windows 10 1709 以降 (RS3 以降) のデスクトップを構成する方法および場所を変更中です。

#### <a name="how-does-this-affect-me"></a>ユーザーへの影響 
記録では、[Windows 10] > [デバイスの制限] > [キオスク (プレビュー)] 設定が使用されていることになっています。 これは 5 月の時点で、UI の名前が [Windows 10] > [デバイスの制限] > [Kiosk (obsolete)]\(キオスク (廃止)\) に変更されます。このことは使用をお勧めしないことを示します。 ただし、Intune に対する 7 月の更新プログラムまでは引き続き機能します。 その後、バックエンドで廃止され、機能しなくなります。 代わりに、新しいデバイス構成プロファイルを 5 月にリリースします: [Windows 10] > [キオスク]。これには、Windows 10 RS4 以降でキオスクを構成する設定が含まれています。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>この変更に対して必要な準備  
5 月の末に Intune の 5 月のサービス更新プログラムがリリースされましたら、Windows 10 RS3 から Windows 10 RS4 へのキオスク構成の移行が可能なことをテストおよび検証する手順を共有する予定です。 その手順に従い、キオスクの新しいデバイス構成プロファイルを使用するキオスクとしてデバイスを構成してください。

#### <a name="how-does-this-affect-me"></a>ユーザーへの影響
この変更は、Intune スタンドアロンのお客様とハイブリッド (Intune と Configuration Manager) のお客様の両方に影響します。 この統合は、クラウド管理の簡素化に役立ちます。 ここで、Azure での移動先のブレードは 1 つだけであり、そこでグループ、ポリシー、アプリ、およびモバイル デバイスを管理します。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>この変更に対して必要な準備
Intune アプリ保護サービス ブレードの代わりにお気に入りとして登録し、Intune のモバイル アプリ ブレードのアプリ保護ポリシーのワークフローを習熟してください。 リダイレクトを短期間行い、その後アプリ保護ブレードを削除します。 ただし、すべてのアプリ保護ポリシーが既に Intune にあり、[https://aka.ms/azuread_ca](https://aka.ms/azuread_ca) にあるドキュメントに従って、任意の条件付きアクセス ポリシーを変更できます。

**追加情報**: [https://aka.ms/intuneapppolicy](https://aka.ms/intuneapppolicy)

### <a name="plan-for-change-windows-company-portal-send-feedback-option-may-no-longer-work"></a>変更の計画: Windows ポータル サイトの [フィードバックの送信] オプションは今後機能しない場合がある  
Windows ポータル サイト アプリには、アプリに関するフィードバックを Microsoft に送信できるように **[フィードバックの送信]** オプションがあります。 2018 年 4 月 30 日から、Windows 10 1607 (Anniversary Update) 以降を実行している Windows 10 ポータル サイト アプリでのみ、このオプションが引き続きサポートされます。  

#### <a name="how-does-this-affect-me"></a>ユーザーへの影響  
エンド ユーザーに Windows ポータル サイト アプリをインストールしていない場合、このメッセージは無視してください。 エンド ユーザーの中にポータル サイト アプリをインストールしている人がいる場合、次のシナリオにおいて、4 月 30 日から **[フィードバックの送信]** ボタンが機能しなくなることに注意してください。  
- Windows 10 のリリース 1507 および 1511 リリースで使用する場合の Windows 10 ポータル サイト アプリ  
- Windows Phone Windows 8.1 ポータル サイト アプリ  

影響を受けるデバイスの場合、**[フィードバックの送信]** オプションは機能せず、再試行でも動作しません。 影響を受けるデバイスで発生した現象について Microsoft にフィードバックを送信するには、以下に一覧した代替フィードバック チャネルをご利用ください。  

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>この変更に対して必要な準備  
ユーザーにこの変更を通知し、必要に応じてユーザー ガイダンスを更新してください。 Windows Phone 8.1、Windows 10 1507、Windows 10 1511 でポータル サイトを利用しているエンド ユーザーに 2 つの代替フィードバック チャネルを利用できることをお知らせください。 代替フィードバック方法:  
- Windows 10 でフィードバック ハブ アプリを使用する
- WinCPfeedback@microsoft.com に電子メールを送信する  

Windows 10 RS1 以降を利用しているエンド ユーザーに Microsoft Store で入手できる Windows ポータル サイトの最新版に更新するように要請します。

### <a name="plan-for-change-change-in-support-for-the-microsoft-intune-app-sdk-for-cordova-plugin"></a>変更計画: Microsoft Intune App SDK for Cordova プラグインのサポートでの変更
Intune による [Microsoft Intune App SDK Cordova プラグイン](app-sdk-cordova.md)のサポートは、2018 年 5 月 1 日で終了します。 代わりに Intune アプリ ラッピング ツールを使って、Cordova ベースのアプリの Intune での管理性と可用性の準備をすることをお勧めします。 この変更が有効になると、Microsoft Intune APP SDK for Cordova プラグインは保守されたり更新プログラムを受け取ったりしなくなります。 アプリ開発者はこのプラグインを使えなくなります。 Intune は、Cordova でのアプリ構築のサポートを続ける予定です。 ただし、Microsoft Intune APP SDK for Cordova プラグインを使って作成されたアプリは、Intune での機能が制限されるようになります。 Intune アプリ ラッピング ツールでラップした後は、通常どおりにアプリをエンド ユーザーに展開できます。 Google Play Store にリリースされた Cordova ベースの Android アプリの場合:
- エンド ユーザーは、初めて起動するときに Intune ポリシーを受け取るために資格情報を求められます。
- アプリは、Intune ユーザーが対象のアプリ ストアにリリースされる必要があります ("Contoso App for Intune" など)。

アプリ ラッピング ツールについては、[iOS 用アプリ ラッピング ツール](app-wrapper-prepare-ios.md)および [Android 用アプリ ラッピング ツール](app-wrapper-prepare-android.md)に関する説明をご覧ください。 問題または質問がある場合は、[msintuneappsdk@microsoft.com](mailto:msintuneappsdk@microsoft.com) にお問い合わせください。

### <a name="plan-for-change-use-intune-on-azure-now-for-your-mdm-management----1227338---"></a>変更の計画: MDM 管理に今すぐ Azure で Intune を使用する <!-- 1227338 -->
1 年以上前、[Azure の Intune のパブリック プレビュー](https://cloudblogs.microsoft.com/enterprisemobility/2016/12/07/public-preview-of-intune-on-azure/)を発表し、その後、6 か月前に Intune の[新しい管理者エクスペリエンスを一般公開](https://cloudblogs.microsoft.com/enterprisemobility/2017/06/08/the-new-intune-and-conditional-access-admin-consoles-are-ga/)しました。 Intune スタンドアロンをご利用の場合、2018 年 8 月 31 日以降、従来の Silverlight コンソールではモバイル デバイス管理 (MDM) を使用できなくなります。 MDM が必要な場合は、代わりに [Azure 上の Intune](https://aka.ms/Intune_on_Azure) を使用できます。 まだ MDM に従来のコンソールを使用している場合は、使用を止め、Azure 上の Intune に慣れてください。 この変更によるエンド ユーザーへの影響はない予定です。 従来の PC 管理は Silverlight に残ります。 この変更とその影響については、[こちら](https://aka.ms/Intune_on_Azure_mdm)を参照してください。

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Apple 登録シナリオへの直接アクセス <!--951869-->
Intune では、2017 年 1 月以降に作成された Intune アカウントについて、Azure Portal の Enroll Devices ワークロードを使用して、Apple 登録シナリオに直接アクセスできるようになりました。 これまでは、Apple 登録プレビューは Intune クラシック ポータルのリンクからのみアクセスが可能でした。 2017 年 1 月より前に作成された Intune アカウントの場合は、これらの機能が Azure で利用可能になるまでの間、1 回限りの移行が必要です。 移行スケジュールはまだ発表されていませんが、詳細はできる限り早く発表します。 既存のアカウントで Azure Portal にアクセスできない場合は、試用アカウントを作成して、新しいエクスペリエンスをテストすることを強くお勧めします。

## <a name="whats-coming"></a>今後の更新情報

### <a name="local-device-security-option-settings----1251887---"></a>ローカル デバイス セキュリティ オプションの設定 <!-- 1251887 -->
新しいローカル デバイス セキュリティ オプションの設定を使って、Windows 10 デバイスのセキュリティ設定を有効にできます。 これらの設定は、Windows 10 デバイスの構成ポリシーを作成するときに、[Endpoint Protection] カテゴリに表示されます。

### <a name="new-user-experience-update-for-the-company-portal-website---2000968--"></a>ポータル Web サイトの新しいユーザー エクスペリエンスの更新<!--2000968-->

UI を更新し、ワークフローの簡素化とユーザー補助機能を改善した、新しいポータル Web サイトのエクスペリエンスを 4 月に導入します。 これには、アプリ共有などのお客様の要望に基づいた機能拡張や、よりユーザー フレンドリなエクスペリエンスを提供するための全体的なパフォーマンスの向上などが含まれます。
お客様からのフィードバックに基づいて、既存の機能と使いやすさを大幅に向上させる新しい機能もいくつか追加されています。

-   Web サイト全体の UI の機能強化
-   アプリへの直接リンクを共有する機能
- 大規模なアプリケーション カタログのパフォーマンスの向上

この変更の準備のために何かを行う必要はありません。 更新されたポータル Web サイトが利用可能になったら、お知らせいたします。 ただし、最終的には、更新されたスクリーンショットを使用して、エンド ユーザーのドキュメントを更新する必要があります。 また、Web サイトは iOS アプリの **[アプリ]** セクションに影響するため、iOS のポータル サイト アプリのドキュメントも更新する必要があることに注意してください。 このサンプル イメージは、[アプリ UI の新機能](whats-new-app-ui.md)のページでご覧になれます。

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple の要求による Application Transport Security 対応のための更新<!--748318-->
Apple は、Application Transport Security (ATS) の特定の要件を適用すると発表しました。 ATS では、HTTPS 経由で行われるアプリ通信すべてに、より厳格なセキュリティ保護が適用されます。 この変更により、iOS ポータル サイト アプリを使用している Intune ユーザーが影響を受けます。 詳細については、[Intune サポート ブログ](https://aka.ms/compportalats)を参照してください。



## <a name="see-also"></a>関連項目
* [Microsoft Intune のブログ](http://go.microsoft.com/fwlink/?LinkID=273882)
* [クラウド プラットフォームのロードマップ](https://www.microsoft.com/cloud-platform/roadmap)
* [ポータル Web サイトの UI の新機能](whats-new-app-ui.md)
* [以前の月の新機能](whats-new-archive.md)
