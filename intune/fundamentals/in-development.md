---
title: 開発中 - Microsoft Intune
titleSuffix: ''
description: Microsoft Intune の開発中の機能
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0e7c4e5ed45455dda941fb0c61c989c12c57135d
ms.sourcegitcommit: 29b1113dc04534c4c87c33c773c5a0e24266e042
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "71999329"
---
# <a name="in-development-for-microsoft-intune---october-2019"></a>Microsoft Intune 用に開発中 - 2019 年 10 月

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
## App management
## Device configuration
## Device enrollment
## Device management
## Intune apps
## Monitor and troubleshoot
## Role-based access control
## Security

-->
 
<!-- ***********************************************-->
## <a name="app-management"></a>アプリ管理

### <a name="additional-app-configuration-variable-available----4969237----"></a>追加のアプリ構成変数を使用できます <!-- 4969237  -->
アプリ構成ポリシーを作成するときに、構成設定の一部として `AAD Device ID` 構成変数を含めることができます。 Intune で **[クライアント アプリ]**  >  **[アプリ構成ポリシー]**  >  **[追加]** の順に選択します。 構成ポリシーの詳細を入力し、構成 **[設定]** を選択して、 **[構成設定]** ブレードを表示します。

### <a name="dark-mode-for-ios-company-portal----4911422----"></a>IOS ポータルサイトのダークモード <!-- 4911422  -->
IOS ポータルサイトには、ダークモードが計画されています。 会社のアプリをダウンロードし、デバイスを管理し、好みの配色で IT サポートを受けることができます。 iOS ポータル サイトの詳細については、「[Microsoft Intune ポータル サイト アプリを構成する方法](../apps/company-portal-app.md)」をご覧ください。

### <a name="prevent-installation-of-apps-from-unknown-sources-on-android-enterprise-devices----4760025----"></a>Android Enterprise デバイスで不明なソースからのアプリのインストールを禁止する <!-- 4760025  -->
Android Enterprise work profile デバイスでは、エンドユーザーが不明なソースから仕事用プロファイルにアプリをインストールすることはできません。 必要に応じて、この制限を個人用プロファイルに拡張することもできます。 この制限を有効にすると、Android Enterprise work profile デバイスのエンドユーザーは、不明なソースからのアプリをデバイスの個人側にサイドローディングすることもできなくなります。 

### <a name="update-to-app-protection-ui-and-ios-app-provisioning-ui----4102027-4102029----"></a>アプリ保護 UI と iOS アプリプロビジョニング UI を更新する <!-- 4102027, 4102029  -->
Intune でアプリ保護ポリシーと iOS アプリプロビジョニングプロファイルを作成および編集するための UI が更新されます。 UI に対する次のような変更があります。
- 1つのブレード内で圧縮されたウィザード形式の形式を使用した簡単なエクスペリエンス。 
- 割り当てを含めるように作成フローに対する更新。
- 新しいポリシーを作成する前、またはプロパティを編集する前に、プロパティを表示するときに設定されるすべての項目の概要ページ。 また、プロパティを編集する場合、概要では、編集されているプロパティのカテゴリの項目の一覧のみが表示されます。

### <a name="create-groups-of-management-objects-called-policy-sets----3762880----"></a>ポリシーセットと呼ばれる管理オブジェクトのグループを作成する <!-- 3762880  -->
ポリシーセットを使用すると、1つの概念単位として識別、対象、および監視する必要がある既存の管理エンティティへの参照のバンドルを作成できます。 ポリシーセットは、既存の概念やオブジェクトに代わるものではありません。 管理者は、引き続き個々のオブジェクトを割り当てることができます。 個々のオブジェクトは、ポリシーセットによって参照されます。 そのため、個々のオブジェクトに対する変更は、ポリシーセットに反映されます。  Intune では、 **[ポリシーセット]**  >  選択して、新しいポリシーセット**を作成し**ます。 

### <a name="win32-apps-on-windows-10-s-mode-devices----3747604----"></a>Windows 10 S モードデバイス上の Win32 アプリ <!-- 3747604  --> 
Win32 アプリは、Windows 10 のモードで管理されたデバイスにインストールして実行できます。 Windows Defender Application Control (WDAC) PowerShell ツールを使用して、S モード用に1つ以上の補足ポリシーを作成できます。 Device Guard 署名ポータルを使用して追加のポリシーに署名し、Intune を使用してポリシーをアップロードして配布します。 Intune では、[**クライアントアプリ** > **Windows 10 S 補足ポリシー**] を選択してこの機能を確認できます。 

### <a name="set-app-availability-based-on-a-date-and-time----3510685----"></a>日付と時刻に基づいてアプリの可用性を設定する <!-- 3510685  -->
管理者は、必要なアプリの開始時刻と期限の時間を構成できます。 開始時に、Intune 管理拡張機能によってアプリのコンテンツのダウンロードとキャッシュが開始されます。 アプリは期限時にインストールされます。 利用可能なアプリの場合、開始時刻によって、アプリがポータルサイトに表示されるタイミングが決まります。 Intune で、 **[クライアント アプリ]**  >  **[アプリ]** を選択します。 次に、一覧から特定のアプリを選択するか、 **[追加]** を選択して新しいアプリを追加します。 アプリブレードで **[割り当て]** を選択し  >  **[グループの追加]** を選択します。 **[割り当ての種類]** を **[必須]** に設定し、 **[含まれているグループ]** を選択します。 **[すべてのユーザーに対してこのアプリを必須]** にする を [**はい]** に設定し、 **[編集]** を選択して**エンドユーザーエクスペリエンス**のオプションを変更します。 **[エンドユーザーエクスペリエンス]** ブレードで、必要に応じて**ソフトウェアの使用可能な時間**を設定します。 アプリを追加する方法の詳細については、「[Microsoft Intune にアプリを追加する](../apps/apps-add.md)」を参照してください。

### <a name="require-win32-apps-to-restart----3136567----"></a>Win32 アプリの再起動が必要 <!-- 3136567  -->
インストールが正常に完了したら、Win32 アプリを再起動する必要があります。 また、再起動が必要になるまでの時間 (猶予期間) を選択することもできます。

### <a name="company-portal-app-on-windows----1808082----"></a>Windows でのアプリのポータルサイト <!-- 1808082  -->
Windows デバイス上のポータルサイトアプリが更新され、アプリケーションが閉じられた場合でも、ユーザーにトースト通知が表示されるようになります。 更新プログラムでは、インストールの状態が [完了] または [失敗] の場合にのみ、利用可能なアプリの通知のみが表示されます。 ポータルサイトアプリには、必要なアプリケーションの通知は表示されません。

### <a name="company-portal-app-installation-status-messages----2514416----"></a>ポータルサイトアプリのインストールステータスメッセージ <!-- 2514416  -->
ポータルサイトアプリには、エンドユーザーに追加のアプリインストールステータスメッセージが表示されます。 新しい Win32 依存関係機能には、次の条件が適用されます。
- アプリをインストールできませんでした。 管理者によって定義された依存関係が満たされませんでした。
- アプリは正常にインストールされましたが、再起動が必要です。
- アプリはインストールの処理中ですが、続行するには再起動が必要です。

#### <a name="assign-microsoft-edge-beta-for-macos----4678761----"></a>MacOS 用 Microsoft Edge beta の割り当て <!-- 4678761  -->
最新バージョンの Microsoft Edge ベータ版を macOS デバイス用の Intune に追加して割り当てることができます。 Intune から、**クライアントアプリ** を選択し  > **アプリ** > **アプリの追加** > **Microsoft Edge-macOS** を選択します。 次に、Microsoft Edge beta を目的のグループに割り当てます。 Microsoft AutoUpdate (MAU) は Microsoft Edge を最新の状態に保ちます。 Microsoft Edge の詳細については、「 [Microsoft Intune で Microsoft edge を使用して web アクセスを管理する](../apps/manage-microsoft-edge.md)」を参照してください。

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>組織アカウントのアプリ通知コンテンツを構成する <!-- 2576686 -->
Android および iOS デバイスの Intune アプリ保護ポリシー (アプリ) では、組織アカウントのアプリ通知コンテンツを制御できます。 この機能は、アプリケーションからのサポートを必要とし、すべてのアプリ対応アプリケーションで使用できるとは限りません。 アプリの詳細については、「[アプリ保護ポリシーとは](../apps/app-protection-policy.md)」を参照してください。

### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956----"></a>Android の仕事用プロファイルに使用できる Google Play アプリのレポート <!-- 3041956  -->
Android の仕事用プロファイル デバイスに使用できるアプリのインストールについては、アプリのインストール状態と managed Google Play アプリのインストール済みバージョンを確認できます。 詳細については、[アプリの保護ポリシーを監視する方法](../apps/app-protection-policies-monitor.md)、[Intune を使用した Android の仕事用プロファイル デバイスの管理](../enrollment/android-enterprise-overview.md)、および[マネージド Google Play アプリの種類](../apps/apps-add-android-for-work.md#managed-google-play-app-types)に関する記事を参照してください。

<!-- ***********************************************-->
## <a name="device-configuration"></a>デバイス構成


### <a name="new-device-configuration-settings-for-supervised-ios-and-ipados-devices----5199328----"></a>監視対象の iOS および iPadOS デバイス用の新しいデバイス構成設定 <!-- 5199328  -->
IOS および iPadOS デバイスでは、デバイスの機能と設定を制限するプロファイルを作成できます (**デバイスの構成** > **プロファイル** > **作成プロファイル** > **iOS/ipados** (platform >**デバイス)** プロファイルの種類に関する制限。 制御できる新しい設定があります。 
- ファイルアプリのネットワークドライブへのアクセス  
- ファイルアプリ内の USB ドライブへのアクセス 
- Wi-fi は常にオンになっています 

現在の設定を確認するには、「[Intune を使用して機能を許可または制限するように iOS デバイスを設定する](../configuration/device-restrictions-ios.md)」を参照してください。

適用対象:
- iOS 13.0 以降
- iPadOS 13.0 以降

### <a name="connect-automatically-setting-is-removed-in-wi-fi-profiles-on-android-and-android-enterprise----5021055----"></a>Android および Android Enterprise の Wi-fi プロファイルで [自動的に接続する] 設定が削除される <!-- 5021055  -->
Android および Android エンタープライズデバイスでは、Wi-fi プロファイルを作成してさまざまな設定を構成できます (**デバイスの構成** > **プロファイル** > **プロファイルの作成** > **android**または**android enterprise)** プラットフォーム >、プロファイルの種類**と**して wi-fi) を使用します。 [Android でサポートされていない](https://developer.android.com/reference/android/net/wifi/WifiManager.html#enableNetwork%28int%2c%20boolean%29)ため、[**自動的に接続**する] 設定は削除されます。 

Wi-fi プロファイルでこの設定を使用すると、**接続が自動的に**機能しなくなる場合があります。 操作を行う必要はありませんが、Intune のユーザーインターフェイスではこの設定が削除されていることに注意してください。

現在の設定を表示するには、 [Android wi-fi 設定](../configuration/wi-fi-settings-android.md)または[android Enterprise wi-fi 設定](../configuration/wi-fi-settings-android-enterprise.md)にアクセスします。

適用対象:
- Android
- Android エンタープライズ

### <a name="create-a-global-http-proxy-on-android-enterprise-device-owner-devices----4816339----"></a>Android エンタープライズデバイス所有者デバイスでグローバル HTTP プロキシを作成する <!-- 4816339  -->
Android Enterprise デバイスでは、グローバル HTTP プロキシを構成して、組織の web 閲覧標準 (**デバイスの構成** > **プロファイル** > **プロファイルの作成** > **Android enterprise** forプラットフォーム >**デバイス所有者**は、プロファイルの種類 >**接続**) に関するデバイスの制限を > ます。 構成が完了すると、すべての HTTP トラフィックがこのプロキシを使用します。

適用対象:
- Android エンタープライズ デバイスの所有者

### <a name="new-device-firmware-configuration-interface-profile-for-windows-10-and-later-devices----2266073----"></a>Windows 10 以降のデバイス用の新しいデバイスファームウェア構成インターフェイスプロファイル <!-- 2266073  -->
Windows 10 以降では、デバイス構成プロファイルを作成して設定と機能を制御できます (**デバイスの構成** > **プロファイル** > **プロファイルの作成** > **Windows 10 以降**のプラットフォーム)。 Intune で UEFI (BIOS) 設定を管理できるようにする新しいデバイスファームウェア構成インターフェイスの種類が追加されます。

構成できるすべての現在の設定の概要については、「 [Microsoft Intune のデバイスプロファイルを使用してデバイスの機能と設定を適用](../configuration/device-profiles.md)する」を参照してください。

適用対象:
- Windows 10 RS5 (1809) 以降のデバイスの選択

### <a name="pkcs-certificates-for-macos-----1333650------------------"></a>MacOS 用の PKCS 証明書  <!-- 1333650                -->
MacOS を実行するデバイスには、PKCS 証明書の完全なサポートを追加します。 ユーザーは、[カスタマイズの件名] フィールドと [サブジェクトの別名] フィールドを使用して、ユーザーとデバイスの証明書を展開できるようになります。 また、すべてのアプリへのアクセスを許可する新しい設定が追加されます。これにより、関連付けられているすべてのアプリが秘密キーにアクセスできるようになります。 この設定の詳細については、次の Apple ドキュメントを参照してください: https://developer.apple.com/business/documentation/Configuration-Profile-Reference.pdf 。

###   <a name="derived-credentials-to-provision-mobile-devices-with-certificates----------1736036-1736037-1772050--------"></a>証明書を使用してモバイルデバイスをプロビジョニングするために取得される資格情報      <!--  1736036, 1736037, 1772050      --> 
デバイスに証明書を展開するための*米国国立標準技術研究所 (NIST) 800-157*標準をサポートする、派生された資格情報のサポートを追加します。  派生された資格情報は、スマートカードのように、個人 Id の確認 (PIV) カードまたはコモンアクセスカード (CAC) カードの使用に依存します。 ユーザーは、コンピューターのスマートカードを使用して認証を行い、派生した資格情報プロバイダーが必要とするプロセスに従って、管理対象デバイスの証明書の要求を送信します。   

派生した資格情報を使用して証明書を取得するプロセスは、SCEP または PKCS 証明書プロファイルを使用する場合とは異なりますが、最終的な結果は、アプリ認証、VPN、Wi-fi、または電子メールに使用できる認証用の証明書を持つモバイルデバイスと同じです。プロファイル.   

詳細については、「 [DERIVED PIV Credentials](https://www.nccoe.nist.gov/projects/building-blocks/piv-credentials) in www.nccoe.nist.gov」を参照してください。

派生した資格情報の最初のリリースでは、iOS での Entrust Datacard、仲裁、DISA Purebred がサポートされます。 追加のプラットフォームと派生した資格情報プロバイダーは、今後のリリースでサポートされる予定です。   

<!-- ***********************************************-->
## <a name="device-enrollment"></a>デバイスの登録

### <a name="specify-which-android-device-operating-system-versions-enroll-with-work-profile-or-device-administrator-enrollment----4350697---"></a>仕事用プロファイルまたはデバイス管理者の登録で登録する Android デバイスのオペレーティングシステムのバージョンを指定する <!-- 4350697 -->
Intune のデバイスの種類の制限を使用すると、デバイスの OS バージョンを使用して、Android Enterprise work profile の登録または Android デバイス管理者の登録を使用するユーザーデバイスを指定することができます。 これを行うには、 **Intune** > **device enrollment** >  の**登録制限** > **Create restriction** > **デバイスの種類の制限** >  プラットフォームの**設定**を参照してください。

### <a name="edit-device-name-value-for-autopilot-devices----4816775---"></a>自動操縦デバイスのデバイス名の値を編集する <!-- 4816775 -->
Azure AD に参加している自動操縦デバイスのデバイス名の値を編集できるようになります。 これを行うには、 **Intune** > **device enrollment** > **Windows enrollment** > **Windows の自動操縦** > **デバイス**を選択 > 右側のウィンドウでデバイス名の値を変更 > **[保存]** .

### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal----4394993----"></a>iOS デバイスの場合は、ポータル サイトの登録プロセスのプライバシー画面をカスタマイズします <!-- 4394993  -->
マークダウンを使用して、iOS の登録時にエンド ユーザーに表示されるポータル サイトのプライバシー画面をカスタマイズできます。 具体的には、組織がデバイス上で参照または実行できない項目の一覧をカスタマイズできます。

<!-- ***********************************************-->
## <a name="device-management"></a>デバイス管理


### <a name="edit-group-tag-value-for-autopilot-devices---4816775---"></a>自動操縦デバイスのグループタグ値の編集<!-- 4816775 -->
自動操縦用デバイスのグループタグの値を編集できます。 これを行うには、 **Intune** > **device enrollment** > **Windows enrollment** > **Windows の自動操縦** > **デバイス**を選択 > 右側のウィンドウのグループタグの値を変更 >**保存 >** .

### <a name="ui-update-for-creating-and-editing-windows-10-update-rings-----4099089------------"></a>Windows 10 更新プログラムリングを作成および編集するための UI 更新プログラム  <!-- 4099089          -->   
Intune の Windows 10 更新プログラムリング用の更新された作成と編集の UI エクスペリエンスをロールアウトします。  UI の変更内容は次のとおりです。  
- 1つのブレード内で圧縮されたウィザードスタイルの書式を使用して、既存のエクスペリエンスを簡略化します。 この UI 更新は、ブレードが密になっているため、IT 担当者がディープブレード体験にドリルダウンする必要があります。   
- 割り当てを含むように作成フローを変更します。  
- プロパティを表示するとき、新しい更新プログラムのリングを作成する前、およびプロパティを編集するときに設定されるすべての項目の概要ページが追加されます。 編集時、編集中のプロパティの 1 カテゴリ内に設定されているアイテムのみがまとめに一覧表示されます。

### <a name="ui-update-for-creating-and-editing-ios-software-updates-----4099090----------"></a>IOS ソフトウェア更新プログラムを作成および編集するための UI 更新プログラム  <!-- 4099090        -->   
Intune に対する iOS ソフトウェア更新プログラムの更新された作成と編集の UI エクスペリエンスをロールアウトします。 UI の変更内容は次のとおりです。
- 1つのブレード内で圧縮されたウィザードスタイルの書式を使用して、既存のエクスペリエンスを簡略化します。 この UI 更新は、ブレードが密になっているため、IT 担当者がディープブレード体験にドリルダウンする必要があります。  
- IOS ソフトウェア更新ポリシーの作成フローは、割り当てを含むように更新されます 
- IOS ソフトウェア更新ポリシーには、新しいポリシーを作成する前とプロパティを編集する前に、プロパティを表示するときに設定されるすべての項目の概要ページが含まれます。 編集時、編集中のプロパティの 1 カテゴリ内に設定されているアイテムのみがまとめに一覧表示されます。

### <a name="target-macos-user-groups-to-require-jamf-management----4061739---"></a>Jamf の管理を必要とする macOS ユーザーグループをターゲットにする <!-- 4061739 -->
特定のユーザーグループを対象にして、macOS デバイスが Jamf で管理されるようにすることができます。 このターゲット設定を使用すると、Jamf コンプライアンス統合を macOS デバイスのサブセットに適用できますが、他のデバイスは Intune によって引き続き管理されます。 また、ユーザーのデバイスを別の MDM に段階的に移行することもできます。

### <a name="new-restrictions-for-renaming-windows-devices----3478938---"></a>Windows デバイスの名前変更に関する新しい制限事項 <!-- 3478938 -->
デバイス名は、次の規則に従う必要があります。
- 15文字以下 (後続の NULL を含まない、63バイト以下でなければなりません)
- null 以外または空の文字列
- 使用できる ASCII: 文字 (a-z、a-z)、数字 (0-9)、およびハイフン
- 使用できる Unicode: 文字 > = 0x80、有効な UTF8 である必要があります。 IDN マッピングである必要があります (RtlIdnToNameprepUnicode は成功します。 RFC 3492 を参照)。
- 名前には数字のみを使用することも、数字で始めることもできません
- 名前にスペースがありません
- 許可されていない文字: {|} ~ [\] ^ ':;< = > ですか? &AMP; @! " # $ % ` ( ) + / , . _ *)

### <a name="deploy-software-updates-to-macos-devices----3194876---"></a>MacOS デバイスへのソフトウェア更新プログラムの展開 <!-- 3194876 -->
MacOS デバイスのグループにソフトウェア更新プログラムを展開できるようになります。 この機能には、重要な、ファームウェア、構成ファイル、およびその他の更新プログラムが含まれます。 次のデバイスのチェックイン時に更新プログラムを送信したり、設定した時間帯に更新プログラムを展開する週単位のスケジュールを選択したりすることができます。 この機能は、標準の勤務時間外にデバイスを更新する場合や、ヘルプデスクのスタッフが完全に仕事をしている場合に役立ちます。 また、更新プログラムが展開されているすべての macOS デバイスの詳細なレポートも取得します。 デバイスごとにレポートをドリルダウンして、特定の更新の状態を確認することができます。

<!-- ***********************************************-->
## <a name="monitor-and-troubleshoot"></a>監視とトラブルシューティング

### <a name="new-android-report-on-devices-overview-page----2984353----"></a>デバイスの新しい Android レポートの概要ページ <!-- 2984353  -->
各デバイス管理ソリューションに登録されている Android デバイスの数を表示する、[デバイスの概要] ページに新しいレポートを追加します。 このグラフには、仕事用プロファイル、完全管理型、専用デバイス、およびデバイス管理者が登録したデバイスの数が表示されます。 レポートを表示するには、[ **Intune** >  台の**デバイス** >  の**概要**] を選択します。

### <a name="windows-autopilot-deployment-reports----3856172----"></a>Windows Autopilot 配置レポート <!-- 3856172  -->
新しいレポートでは、Windows 自動操縦によって展開された各デバイスの詳細が表示されます。 このデータは、デプロイ後30日後に使用できるようになります。 レポートを表示するには、 **Intune** > **Device enrollment** > **Monitor** > **自動操縦の展開**を監視します。

### <a name="updated-support-experience-------5012398------"></a>更新されたサポートエクスペリエンス   <!--  5012398    -->
継続的な改善の一環として、Intune のコンソール内サポートエクスペリエンスを更新します。  一般的な問題についてコンソール内での検索とフィードバックを改善し、ワークフローを合理化してサポートに連絡します。     

<!-- ***********************************************-->
<!--## Security-->


<!-- ***********************************************-->
## <a name="notices"></a>通知

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>関連項目
最近の開発状況について詳しくは、「[Microsoft Intune の新機能](whats-new.md)」をご覧ください。




