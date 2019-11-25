---
title: Microsoft Intune の新機能 - Azure | Microsoft Docs
titleSuffix: ''
description: Intune Azure Portal の新機能を確認する
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 71045489ac703860073a3023e6d6170778117d33
ms.sourcegitcommit: 01fb3d844958a0e66c7b87623160982868e675b0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2019
ms.locfileid: "74199286"
---
# <a name="whats-new-in-microsoft-intune"></a>Microsoft Intune の新機能

週ごとにまとめた、Microsoft Intune の新機能をご覧ください。 また、[重要なお知らせ](#notices)、[過去のリリース](whats-new-archive.md)、および [Intune サービスの更新プログラムのリリース方法](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728)に関する情報もあります。

> [!Note]
> 個々の[マンスリー更新プログラム](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728)は、展開に最大 3 日かかることがあります。順序は次のとおりです。
>
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

## <a name="week-of-november-18-2019"></a>2019 年 11 月 18 日の週

### <a name="device-configuration"></a>デバイス構成

#### <a name="windows-10-feature-updates-public-preview---2384877---"></a>Windows 10 機能更新プログラム (パブリック プレビュー)<!-- 2384877 -->

[Windows 10 機能更新プログラム](../protect/windows-update-for-business-configure.md#windows-10-feature-updates)を Windows 10 デバイスに展開できるようになりました。 Windows 10 機能更新プログラムは、デバイスにインストールして維持する必要がある Windows 10 のバージョンを設定できる、新しいソフトウェア更新プログラムのポリシーです。 この新しいポリシーの種類は、既存の Windows 10 更新プログラムのリングと共に使用できます。

Windows 10 機能更新ポリシーを受け取ったデバイスでは、指定されたバージョンの Windows がインストールされ、そのポリシーが編集または削除されるまでそのバージョンにとどまります。 より新しいバージョンの Windows を稼働しているデバイスは、その現在のバージョンにとどまります。 Windows の特定のバージョンで固定されているデバイスでも、Windows 10 更新プログラムのリングから、そのバージョンの品質更新プログラムおよびセキュリティ更新プログラムをインストールできます。

この新しい種類のポリシーは、今週テナントへのロールアウトが開始されます。 ご自分のテナントでまだこのポリシーを使用できない場合は、間もなく使用できるようになります。

### <a name="monitor-and-troubleshoot"></a>監視とトラブルシューティング

#### <a name="updated-support-experience---5012398---"></a>更新されたサポート エクスペリエンス<!-- 5012398 -->

本日から、[Intune のヘルプとサポートの取得](get-support.md)に関する、更新および合理化されたコンソール内のエクスペリエンスがテナントにロールアウトされます。 お客様がまだこの新しいエクスペリエンスを利用できない場合は、間もなく利用できるようになります。

コンソール内でのよくあるイシューの検索とフィードバック、およびサポートへの問い合わせに使用するワークフローが改善されました。 サポート イシューを作成するときに、コールバックまたはメールの返信をいつ受け取ることができるのかについての推定が、リアルタイムで表示されます。また、Premier および統合サポートのお客様は、より迅速なサポートを受けるために、それぞれのイシューについて、簡単に重大度を指定できます。

## <a name="week-of-november-11-2019"></a>2019 年 11 月 11 日の週  

### <a name="app-management"></a>アプリ管理  

#### <a name="improved-macos-enrollment-experience-in-company-portal----5074349-wnready---"></a>ポータル サイトにおける macOS の登録エクスペリエンスの改善 <!-- 5074349 WNready -->  
macOS の登録エクスペリエンス用のポータル サイトには、よりシンプルな登録プロセスが備わっています。これにより、iOS の登録エクスペリエンス用のポータル サイトと、より厳密な一致がとれます。 デバイス ユーザーに次が表示されるようになりました。  

* より洗練されたユーザー インターフェイス。  
* 強化された登録チェックリスト。  
* デバイスの登録方法に関するより明確な説明。  
* 強化されたトラブルシューティング オプション。  

#### <a name="web-apps-launched-from-the-windows-company-portal-app---5030972---"></a>Windows ポータル サイト アプリから起動する Web アプリ<!-- 5030972 -->
エンドユーザーは、Windows ポータル サイト アプリから直接 Web アプリを起動できるようになりました。 エンドユーザーは、Web アプリを選択してから、 **[ブラウザーで開く]** オプションを選択できます。 発行された Web URL は、Web ブラウザー内で直接開かれます。 この機能は、来週にわたってロールアウトされます。 Web アプリの詳細については、「[Web アプリを Microsoft Intune に追加する](~/apps/web-app.md)」をご覧ください。  


#### <a name="new-assignment-type-column-in-company-portal-for-windows-10----5459950-wnready---"></a>Windows 10 のポータル サイトにおける新しい割り当ての種類の列 <!-- 5459950 WNready -->
ポータル サイト > **[インストール済みアプリ]**  >  **[割り当ての種類]** 列の名前が、 **[組織で必要]** に変更されました。  その列の下に、アプリが組織によって必須、省略可能のいずれに設定されているかを示す **[はい]** または **[いいえ]** の値がユーザーに表示されます。 デバイス ユーザーが利用可能なアプリの概念について混乱していたため、このような変更が行われました。 ユーザーは、「[デバイスにアプリをインストールして共有する](/intune-user-help/install-apps-cpapp-windows)」で、ポータル サイトからのアプリのインストールに関する詳細情報を参照できます。 ユーザーに対するポータル サイト アプリの構成方法の詳細については、「[Microsoft Intune ポータル サイト アプリを構成する方法](~/apps/company-portal-app.md)」をご覧ください。  


## <a name="week-of-november-4-2019"></a>2019 年 11 月 4 日の週

### <a name="device-security"></a>デバイス セキュリティ

#### <a name="security-baselines-are-supported-on-microsoft-azure-government---4062552---"></a>セキュリティ ベースラインが Microsoft Azure Government でサポートされる<!-- 4062552 -->

*Microsoft Azure Government* でホストされている Intune のインスタンスで、[セキュリティ ベースライン](../protect/security-baselines.md)を使用して、ユーザーとデバイスのセキュリティ保護と保護を行えるようになりました。

## <a name="week-of-october-28-2019"></a>2019 年 10 月 28 日の週

### <a name="app-management"></a>アプリ管理

#### <a name="improved-checklist-design-in-company-portal-app-for-android---5550857---"></a>Android 用 Intune ポータル サイト アプリでのチェックリストの設計の改良<!-- 5550857 -->  
Android 用 Intune ポータル サイト アプリのセットアップ チェックリストが、軽量のデザインと新しいアイコンによって更新されました。 この変更は、iOS 用 Intune ポータル サイト アプリに対して行われた最近の更新に合わせたものです。 変更の比較については、「[アプリの UI の新機能](whats-new-app-ui.md)」を参照してください。 更新された登録手順の詳細については、「[Android 仕事用プロファイルを使用して登録する](/intune-user-help/enroll-device-android-work-profile)」および「[Android デバイスを登録する](/intune-user-help/enroll-device-android-company-portal)」をご覧ください。  

#### <a name="win32-apps-on-windows-10-s-mode-devices---3747604---"></a>Windows 10 S モード デバイス上の Win32 アプリ<!-- 3747604 --> 
Windows 10 S モードのマネージド デバイスに Win32 アプリをインストールして実行できます。 そのために、Windows Defender アプリケーション制御 (WDAC) PowerShell ツールを使用して、S モード用の補足ポリシーを作成できます。 Device Guard 署名ポータルで補足ポリシーに署名した後、Intune 経由でポリシーをアップロードして配布します。 Intune でこの機能を利用するには、 **[クライアント アプリ]**  >  **[Windows 10S 補足ポリシー]** を選択します。 詳しくは、「[S モード デバイスで Win32 アプリを有効にする](~/apps/apps-win32-s-mode.md)」をご覧ください。

#### <a name="set-win32-app-availability-based-on-a-date-and-time---3510685---"></a>日付と時刻に基づいて Win32 アプリの可用性を設定する<!-- 3510685 -->
管理者は、必須 Win32 アプリの開始時刻と期限の時刻を構成できます。 開始時刻になると、Intune 管理拡張機能によってアプリのコンテンツのダウンロードが開始されて、キャッシュされます。 期限時刻になると、アプリはインストールされます。 利用可能なアプリの場合、開始時刻はアプリが Intune ポータル サイトに表示されるタイミングを示します。 詳細については、[Intune の Win32 アプリの管理](~/apps/apps-win32-app-management.md#set-win32-app-availability-and-notifications)に関する記事を参照してください。

#### <a name="require-device-restart-based-on-grace-period-after-win32-app-install---3136567---"></a>Win32 アプリのインストール後に猶予期間に基づいてデバイスの再起動を必要にする<!-- 3136567 -->
Win32 アプリが正常にインストールされた後でデバイスを再起動することを必要にできます。 詳細については、「[Win32 アプリ管理 - アプリのインストール情報を構成する](~/apps/apps-win32-app-management.md#step-4-configure-app-installation-details)」を参照してください。

#### <a name="dark-mode-for-ios-company-portal---4911422---"></a>iOS ポータル サイトのダーク モード<!-- 4911422 -->
iOS ポータル サイトでダーク モードを使用できます。 ユーザーは、デバイス設定に基づく任意の配色で、会社のアプリをダウンロードし、デバイスを管理し、IT サポートを受けることができます。 iOS ポータル サイトは、ダーク モードまたはライト モードについて、エンド ユーザーのデバイス設定に自動的に一致します。 詳細については、「[iOS 用 Microsoft Intune ポータル サイトのダーク モードの概要](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Introducing-dark-mode-on-Microsoft-Intune-Company-Portal-for-iOS/ba-p/918453)」をご覧ください。 iOS ポータル サイトの詳細については、「[Microsoft Intune ポータル サイト アプリを構成する方法](~/apps/company-portal-app.md)」をご覧ください。

#### <a name="android-company-portal-enforced-minimum-app-version---2378776---"></a>Android ポータル サイトでの最小アプリ バージョンの適用<!-- 2378776 -->
アプリ保護ポリシーの **[ポータル サイトの最小バージョン]** 設定を使用することにより、エンド ユーザーのデバイスに適用される、ポータル サイトの特定の定義済み最小バージョンを指定できます。 この条件付き起動の設定を使用すると、その値が満たされなかった場合に、実行可能なアクションとして **[アクセスのブロック]** 、 **[データのワイプ]** 、 **[警告]** を行うことができます。 この値に使用できる形式は、" *[メジャー].[マイナー]* "、" *[メジャー].[マイナー].[ビルド]* "、または " *[メジャー].[マイナー].[ビルド].[リビジョン]* " というパターンに従います。

**[ポータル サイトの最小バージョン]** 設定を構成した場合、バージョン 5.0.4560.0 のポータル サイトおよび今後のバージョンのポータル サイトを取得したすべてのエンド ユーザーに影響があります。 この設定は、この機能がリリースされたバージョンより古いバージョンのポータル サイトを使用しているユーザーには影響しません。 デバイス上でアプリの自動更新を使用しているエンド ユーザーは、おそらく最新バージョンのポータル サイトを使用しているため、この機能のダイアログが表示されない可能性があります。 この設定は、登録済みのデバイスと未登録のデバイスのアプリ保護と共に、Android に対してのみ使用できます。 詳細については、[Android アプリ保護ポリシー設定 - 条件付き起動](~/apps/app-protection-policy-settings-android.md#conditional-launch)に関する記事をご覧ください。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->

### <a name="microsoft-365-device-management"></a>Microsoft 365 デバイス管理

#### <a name="introducing-endpoint-security-node-in-microsoft-365-device-management---5630102---"></a>Microsoft 365 デバイス管理のエンドポイント セキュリティ ノードの概要<!-- 5630102 -->

Microsoft 365 デバイス管理のスペシャリスト向けワークスペース (https://devicemanagement.microsoft.com ) で、**エンドポイント セキュリティ** ノードの一般提供が開始されました。これにより、エンドポイントをセキュリティで保護するための次のような機能がまとめてグループ化されます。

- セキュリティ ベースライン:Microsoft によって推奨される設定および規定値の既知のグループを適用するのに役立つ、事前構成された設定のグループ。

- セキュリティ タスク:Microsoft Defender ATP の Threat and Vulnerability Management (TVM) の利用と Intune の使用により、エンドポイントの脆弱性を修復します。

- Microsoft Defender ATP:セキュリティ違反を防ぐのに役立つ、統合された Microsoft Defender Advanced Threat Protection (ATP)。

これらの設定は、デバイスなどの他の適用可能なノードから、引き続きアクセスできます。また、どこでこれらの機能にアクセスし、有効化したかに関係なく、現在構成されている状態は同じになります。

これらの機能強化の詳細については、Microsoft Tech Community の Web サイトの [Intune Customer Success に関するブログ記事](https://aka.ms/Endpoint_security_node)をご覧ください。

### <a name="device-management"></a>デバイス管理

#### <a name="intune-supports-ios-11-and-later---4665324----"></a>Intune による iOS 11 以降のサポート<!-- 4665324  -->

Intune の登録とポータル サイトで、iOS バージョン 11 以降がサポートされるようになりました。 以前のバージョンはサポートされません。

### <a name="device-security"></a>デバイス セキュリティ

#### <a name="microsoft-edge-baseline-preview----3787164----"></a>Microsoft Edge のベースライン (プレビュー)<!--  3787164  -->

[Microsoft Edge の設定](../protect/security-baseline-settings-edge.md)に対してセキュリティのベースライン (プレビュー) を追加しました。 

<!-- ########################## -->
## <a name="week-of-october-21-2019"></a>2019 年 10 月 21 日の週

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="microsoft-365-device-management"></a>Microsoft 365 デバイス管理

#### <a name="improved-administration-experience-in-microsoft-365-device-management---5551239---"></a>Microsoft 365 デバイス管理の管理エクスペリエンスの改善<!-- 5551239 -->

Microsoft 365 デバイス管理のスペシャリスト向けワークスペース ([https://devicemanagement.microsoft.com](https://devicemanagement.microsoft.com)) で、更新され合理化された管理エクスペリエンスの一般提供が開始されました。これには以下が含まれます。

- **更新されたナビゲーション**:機能が論理的にグループ化される、簡略化された第 1 レベルのナビゲーションが提供されます。
- **新しいプラットフォーム フィルター**:[デバイスとアプリ] ページで、単一のプラットフォームを選択できます。これにより、選択したプラットフォームのポリシーとアプリだけが表示されます。
- **新しいホーム ページ**:新しいホーム ページでは、サービスの正常性、テナントの状態、ニュースなどを、すばやく確認できます。

これらの機能強化の詳細については、Microsoft Tech Community の Web サイトの [Enterprise Mobility + Security に関するブログ記事](https://go.microsoft.com/fwlink/?linkid=2109094)をご覧ください。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>アプリ管理

#### <a name="add-mobile-threat-defense-apps-to-unenrolled-devices---3005337---"></a>Mobile Threat Defense アプリを未登録のデバイスに追加する<!-- 3005337 -->
お客様は、デバイスの正常性に基づいてユーザーの会社データをブロックしたり、選択的にワイプしたりすることができる、Intune アプリ保護ポリシーを作成できます。 デバイスの正常性は、お客様が選択した Mobile Threat Defense (MTD) ソリューションを使って判断されます。 現在、この機能は、Intune に登録されたデバイスで、デバイス コンプライアンス設定として使用できます。 この新機能では、脅威検出が Mobile Threat Defense ベンダーから拡張され、未登録デバイス上で機能するようになります。 Android でこの機能を使用するには、デバイス上に最新の Intune ポータル サイトが必要です。 iOS では、アプリに最新の Intune SDK (v 12.0.15+) が統合されている場合に、この機能を使用できるようになります。 最新の Intune SDK が最初のアプリで採用されたときに、新機能に関するトピックが更新されます。 残りのアプリは、ローリング方式で利用可能になっていきます。 詳細については、「[Intune で Mobile Threat Defense アプリ保護ポリシーを作成する](~/protect/mtd-app-protection-policy.md)」をご覧ください。

### <a name="device-configuration"></a>デバイス構成

#### <a name="new-device-firmware-configuration-interface-profile-for-windows-10-and-later-devices-public-preview---2266073----"></a>Windows 10 以降のデバイス用の新しいデバイス ファームウェア構成インターフェイス プロファイル (パブリック プレビュー)<!-- 2266073  -->

Windows 10 以降では、デバイス構成プロファイルを作成し、設定と機能を制御できます ( **[デバイスの構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  >  **[Windows 10 以降]** (プラットフォーム))。 この更新には、Intune で UEFI (BIOS) 設定の管理を可能にする新しいデバイス ファームウェア構成インターフェイスがあります。

この機能の詳細については、「[Microsoft Intune で Windows デバイスの DFCI プロファイルを使用する](../configuration/device-firmware-configuration-interface-windows.md)」を参照してください。

適用対象:
- Windows 10 RS5 (1809) 以降でサポートされているファームウェア

### <a name="device-enrollment"></a>デバイスの登録

#### <a name="toggle-to-only-show-enrollment-status-page-on-devices-provisioned-by-out-of-box-experience-oobe--3959566--"></a>out-of-box experience (OOBE) によってプロビジョニングされたデバイスにのみ登録ステータス ページを表示するように切り替える<!--3959566-->
Autopilot OOBE によってプロビジョニングされたデバイスにのみ、登録ステータス ページを表示するように選択できるようになりました。

新しい切り替えを表示するには、 **[Intune]**  >  **[デバイスの登録]**  >  **[Windows の登録]**  >  **[登録ステータス ページ]**  >  **[プロファイルの作成]**  >  **[設定]**  >  **[out-of-box experience (OOBE) でプロビジョニングされたデバイスにのみページを表示する]** の順に選択します。


<!-- ########################## -->
## <a name="week-of-october-14-2019"></a>2019 年 10 月 14 日の週

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>アプリ管理 

#### <a name="available-google-play-app-reporting-for-android-work-profiles---3041956-----"></a>Android の仕事用プロファイルに使用できる Google Play アプリのレポート<!-- 3041956   -->
Android Enterprise の仕事用プロファイル デバイス、専用デバイス、フル マネージド デバイスに使用できるアプリのインストールについては、アプリのインストール状態とマネージド Google Play アプリのインストール バージョンを確認できます。 詳細については、[アプリの保護ポリシーを監視する方法](~/apps/app-protection-policies-monitor.md)、[Intune を使用した Android の仕事用プロファイル デバイスの管理](~/enrollment/android-enterprise-overview.md)、および[マネージド Google Play アプリの種類](~/apps/apps-add-android-for-work.md#managed-google-play-app-types)に関する記事を参照してください。

#### <a name="microsoft-edge-version-77-and-later-for-windows-10-and-macos-public-preview---3872025-4678761----"></a>Windows 10 と macOS 向けの Microsoft Edge バージョン 77 以降 (パブリック プレビュー)<!-- 3872025, 4678761  -->
Microsoft Edge バージョン 77 以降は、Windows 10 と macOS を稼働している PC に展開できるようになります。 

パブリック プレビューからは、Windows 10 の **Dev** チャンネルと **Beta** チャンネルが、macOS の **Beta** チャンネルが提供されます。 展開は英語版 (EN) のみですが、エンド ユーザーはブラウザーの **[設定]**  >  **[言語]** で表示言語を変更することができます。 Microsoft Edge は、システム コンテキスト、およびアーキテクチャに合わせてインストールされる Win32 アプリです (x86 OS の場合は x86、x64 OS の場合は x64)。 さらに、ブラウザーの自動更新は既定で**オン**になっています。また、Microsoft Edge はアンインストールできません。 詳細については、「[Microsoft Edge for Windows 10 を Microsoft Intune に追加する](~/apps/apps-windows-edge.md)」と「[Microsoft Edge ドキュメント](https://go.microsoft.com/fwlink/?linkid=2103823)」を参照してください。

#### <a name="update-to-app-protection-ui-and-ios-app-provisioning-ui---4102027-4102029-----"></a>アプリ保護 UI と iOS アプリ プロビジョニング UI の更新<!-- 4102027, 4102029   -->
Intune でアプリ保護ポリシーと iOS アプリ プロビジョニング プロファイルを作成し、編集するための UI が更新されました。 UI に対する次のような変更があります。
- ウィザード方式による簡単操作が 1 つのブレード内に凝縮されました。 
- 作成フローを更新し、割り当てを含めました。
- プロパティを表示するときに、新しいポリシーを作成する前に、プロパティを編集するときに、まとめページに全部設定されます。 また、プロパティを編集するとき、編集されるプロパティのカテゴリから項目の一覧のみがまとめに表示されます。

詳細については、「[アプリ保護ポリシーを作成して割り当てる方法](~/apps/app-protection-policies.md)」と「[iOS アプリ プロビジョニング プロファイルを使用する](~/apps/app-provisioning-profile-ios.md)」を参照してください。

#### <a name="intune-guided-scenarios---4850318-4831296-3610611----"></a>Intune のガイド付きシナリオ<!-- 4850318, 4831296, 3610611  -->
Intune では、Intune 内で特定のタスクまたは一連のタスクを完了するのに役立つガイド付きシナリオが提供されるようになりました。 ガイド付きシナリオは、1 つのエンドツーエンドのユースケースを中心にカスタマイズされた一連の手順 (ワークフロー) です。 一般的なシナリオは、組織内で管理者、ユーザー、またはデバイスが果たす役割に基づいて定義されます。 これらのワークフローでは通常、最適なユーザーエクスペリエンスとセキュリティを提供するために、慎重に調整されたプロファイル、設定、アプリケーション、セキュリティ制御のコレクションが必要です。 新しいガイド付きシナリオは次のとおりです。
- [Microsoft Edge for Mobile を展開する](~/fundamentals/guided-scenarios-edge.md)
- [Secure Microsoft Office モバイル アプリ](~/fundamentals/guided-scenarios-office-mobile.md) 
- [クラウドで管理される最新式のデスクトップ](~/fundamentals/guided-scenarios-cloud-managed-pc.md)

詳細については、「[Intune のガイド付きシナリオの概要](guided-scenarios-overview.md)」を参照してください。

#### <a name="additional-app-configuration-variable-available---4969237-----"></a>追加のアプリ構成変数を利用できる<!-- 4969237   -->
アプリ構成ポリシーを作成するとき、構成設定の一部として `AAD Device ID` 構成変数を含めることができます。 Intune で **[クライアント アプリ]**  >  **[アプリ構成ポリシー]**  >  **[追加]** の順に選択します。 構成ポリシーの詳細を入力し、 **[構成設定]** を選択して **[構成設定]** ブレードを表示します。 詳細については、「マネージド Android Enterprise デバイス用にアプリ構成ポリシーを追加する」の「[構成デザイナーを使用する](~/apps/app-configuration-policies-use-android.md#use-the-configuration-designer)」を参照してください。


#### <a name="create-groups-of-management-objects-called-policy-sets---3762880----"></a>ポリシー セットと呼ばれる管理オブジェクトのグループを作成する<!-- 3762880  -->
ポリシー セットを使用すると、1 つの概念単位として識別、対象化、監視する必要がある既存の管理エンティティへの参照のバンドルを作成できます。 ポリシー セットによって、既存の概念やオブジェクトが置き換えられることはありません。 Intune で引き続き個々のオブジェクトを割り当てることができて、ポリシー セットの一部として個々のオブジェクトを参照できます。 そのため、個々のオブジェクトに対する変更は、ポリシー セットに反映されます。  Intune では、 **[ポリシーセット]** 、 **[作成]** の順に選択し、新しいポリシー セットを作成します。 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>デバイス構成

#### <a name="ui-update-for-creating-and-editing-windows-10-update-rings---4099089-----------"></a>Windows 10 更新プログラム リングを作成し、編集するための UI 更新プログラム<!-- 4099089         -->
Intune 用に [Windows 10 更新プログラム リングを作成し、編集する](../protect/windows-update-for-business-configure.md#create-and-assign-update-rings)ための UI エクスペリエンスが更新されました。 UI の変更点は次のとおりです。  
- ウィザード形式が 1 つのコンソール ブレードに凝縮されました。更新プログラム リングを構成するとき、以前見られたようにブレードがまとまりなく広がることがなくなりました。   
- 変更後のワークフローでは、リングの初期構成を完了する前に割り当てが追加されました。
- 概要ページを利用し、行った構成をすべて見直してから新しい更新プログラム リングを保存したり、展開したりできます。 更新プログラム リングの編集時、編集中のプロパティのカテゴリ内に設定されている項目のみがまとめに一覧表示されます。

#### <a name="ui-update-for-creating-and-editing-ios-software-update-policy---4099090---------"></a>iOS ソフトウェアの更新ポリシーを作成し、編集するための UI の更新<!-- 4099090       --> 
Intune 用に iOS ソフトウェアの更新ポリシーを[作成](../protect/software-updates-ios.md#configure-the-policy)し、[編集](../protect/software-updates-ios.md#edit-a-policy)するための UI エクスペリエンスが更新されました。  UI の変更点は次のとおりです。  
- ウィザード形式が 1 つのコンソール ブレードに凝縮されました。更新プログラム ポリシーを構成するとき、以前見られたようにブレードがまとまりなく広がることがなくなりました。   
- 変更後のワークフローでは、ポリシーの初期構成を完了する前に割り当てが追加されました。
- 概要ページを利用し、行った構成をすべて見直してから新しいポリシーを保存したり、展開したりできます。 ポリシーの編集時、編集中のプロパティのカテゴリ内に設定されている項目のみがまとめに一覧表示されます。

#### <a name="engaged-restart-settings-are-removed-from-windows-update-rings----4464404---wnready-----"></a>Windows 更新プログラム リングから再起動猶予期間設定が削除された<!--  4464404   WNReady   -->
前に発表したように、Intune の Windows 10 更新プログラム リングでは、[期限の設定がサポート](../protect/windows-update-settings.md)されるようになり、*再起動猶予期間*はサポートされなくなりました。 Intune で更新プログラム リングを構成または管理するときに、*再起動猶予期間*の設定は利用できなくなりました。  

この変更は、最近の [Windows サービス変更](https://docs.microsoft.com//windows/whats-new/whats-new-windows-10-version-1903#servicing)に合わせるためのものであり、Windows 10 1903 以降で実行されるデバイスでは、*期限*が*再起動猶予期間*の構成より優先されます。

#### <a name="prevent-installation-of-apps-from-unknown-sources-on-android-enterprise-work-profile-devices---4760025-----"></a>Android Enterprise の仕事用プロファイル デバイスに不明ソースからアプリをインストールできなくする<!-- 4760025   -->
Android Enterprise の仕事用プロファイル デバイスでは、ユーザーは不明ソースからアプリをインストールできなくなりました。 この更新プログラムには、**個人プロファイルでは、不明ソースからのアプリ インストールが禁止される**という新しい設定があります。 既定では、この設定により、ユーザーはデバイスで不明ソースから個人プロファイルにアプリをサイドロードできなくなります。

構成できる設定を確認する方法については、「[Intune を使用して機能を許可または制限するための Android エンタープライズ デバイス設定](../configuration/device-restrictions-android-for-work.md)」を参照してください。

適用対象:
- Android Enterprise 仕事用プロファイル

#### <a name="create-a-global-http-proxy-on-android-enterprise-device-owner-devices---4816339-----"></a>Android エンタープライズ デバイス所有者デバイスでグローバル HTTP プロキシを作成する<!-- 4816339   -->
Android Enterprise デバイスでは、組織の Web 閲覧標準を満たすようにグローバル HTTP プロキシを構成できます ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  >  **[Android Enterprise]** > **[デバイス所有者] > [デバイスの制限]** (プロファイルの種類) > **[接続]** )。 構成後、すべての HTTP トラフィックでこのプロキシが使用されます。

この機能を構成し、構成したすべての設定を表示する方法については、「[Intune を使用して機能を許可または制限するための Android エンタープライズ デバイス設定](../configuration/device-restrictions-android-for-work.md)」を参照してください。

適用対象:
- Android Enterprise デバイス所有者

#### <a name="connect-automatically-setting-is-removed-in-wi-fi-profiles-on-android-device-administrator-and-android-enterprise---5021055-----"></a>Android デバイス管理者と Android Enterprise の Wi-Fi プロファイルで [自動的に接続する] 設定が削除される<!-- 5021055   -->
Android デバイス管理者と Android Enterprise デバイスで、Wi-Fi プロファイルを作成し、さまざまな設定を構成できます ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  >  **[Android デバイス管理者]** または **[Android Enterprise]** (プラットフォーム) > **[Wi-Fi]** (プロファイルの種類))。 この更新プログラムでは、[Android ではサポートされていない](https://developer.android.com/reference/android/net/wifi/WifiManager.html#enableNetwork%28int%2c%20boolean%29)ため、 **[自動的に接続する]** 設定が削除されます。 

Wi-Fi プロファイルでこの設定を使用すると、 **[自動的に接続する]** が機能しないことに気付くことがあります。 何の措置もとる必要はありませんが、この設定は Intune ユーザー インターフェイスから削除されることにご留意ください。

現在の設定を表示するには、[Android Wi-Fi 設定](../configuration/wi-fi-settings-android.md)に関するページか、[Android Enterprise Wi-Fi 設定](../configuration/wi-fi-settings-android-enterprise.md)に関するページをご覧ください。

適用対象:
- Android デバイス管理者 
- Android エンタープライズ


#### <a name="new-device-configuration-settings-for-supervised-ios-and-ipados-devices---5199328-----"></a>監視対象の iOS デバイスと iPadOS デバイスの新しいデバイス構成設定<!-- 5199328   -->
iOS デバイスと iPadOS デバイスでは、デバイス上の機能と設定を制限するプロファイルを作成できます ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  >  **[iOS/iPadOS]** (プラットフォーム) > **[デバイスの制限]** (プロファイルの種類))。 この更新では、制御できる新しい設定があります。 
- Files アプリでネットワーク ドライブにアクセスする  
- Files アプリで USB ドライブにアクセスする 
- Wi-Fi を常にオンにする 

これらの設定を確認するには、「[Intune を使用して機能を許可または制限するように iOS デバイスを設定する](../configuration/device-restrictions-ios.md)」を参照してください。

適用対象:
- iOS 13.0 以降
- iPadOS 13.0 以降

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>デバイスの登録

#### <a name="specify-which-android-device-operating-system-versions-enroll-with-work-profile-or-device-administrator-enrollment---4350697-----"></a>仕事用プロファイルまたはデバイス管理者の登録で登録する Android デバイスのオペレーティング システムのバージョンを指定する<!-- 4350697   -->
Intune のデバイスの種類の制限を利用し、Android Enterprise 仕事用プロファイルの登録または Android デバイス管理者の登録を使用するユーザー デバイスをデバイスの OS バージョンで指定できます。  詳細は、「[登録制限を設定する](../enrollment/enrollment-restrictions-set.md)」を参照してください。

#### <a name="windows-autopilot-deployment-reports---3856172---"></a>Windows Autopilot 配置レポート<!-- 3856172 -->
新しいレポートでは、Windows Autopilot によって展開された各デバイスについて詳しく報告されます。 詳しくは、[Autopilot の展開レポート](../enrollment/enrollment-autopilot.md#autopilot-deployments-report)に関するページをご覧ください。 この機能をすべてのお客様にロールアウトしている最中であり、来週の終わりまでに完了する予定です。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>デバイス管理

#### <a name="new-restrictions-for-renaming-windows-devices---3478938----"></a>Windows デバイスの名前変更に関する新しい制限<!-- 3478938  -->
Windows デバイスの名前を変更するとき、新しい規則に従う必要があります。
- 15 文字以下 (後続の NULL を除き、63 バイト以下にする必要があります)
- null または空の文字列にしない
- 許可される ASCII: 文字 (a-z、A-Z)、数字 (0-9)、ハイフン
- 許可される Unicode: 文字数 >= 0x80、有効な UTF8 であることが必須、IDN マッピング可能であることが必須 (つまり、RtlIdnToNameprepUnicode は合格です。RFC 3492 参照)
- 名前は数字だけにすることができない
- 名前にスペースを使用できない
- 許可されていない文字: { | } ~ [ \ ] ^ ' : ; < = > ? & @ ! " # $ % ` ( ) + / , . _ *)

 詳細については、「[Intune 上でデバイスの名前を変更する](../remote-actions/device-rename.md)」を参照してください。

### <a name="new-android-report-on-devices-overview-page---4924364---"></a>デバイス概要ページの新しい Android レポート<!-- 4924364 -->
デバイス概要ページの新しいレポートには、登録されている Android デバイスの数がデバイス管理ソリューションごとに表示されます。 このグラフには、仕事用プロファイル デバイス、フル マネージド デバイス、専用デバイス、デバイス管理者登録デバイスの数が表示されます。 レポートを表示するには、 **[Intune]** 、 **[デバイス]** 、 **[概要]** を選択します。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>デバイス セキュリティ

#### <a name="pkcs-certificates-for-macos---1333650---------"></a>macOS の PKCS 証明書<!-- 1333650       -->
[macOS で PKCS 証明書を利用](../protect/certficates-pfx-configure.md#create-a-pkcs-certificate-profile)できるようになりました。 macOS のプロファイルの種類として PKCS 証明書を選択し、[サブジェクトとサブジェクト代替名のフィールドがカスタマイズ](../protect/certficates-pfx-configure.md#subject-name-format-for-macos)されているユーザーおよびデバイス証明書を展開できます。  

macOS 向け PKCS 証明書では、_すべてのアプリ アクセスを許可する_新しい設定もサポートされています。 この設定により、証明書の秘密鍵に関連付けられているすべてのアプリ アクセスを有効にできます。  この設定に関する詳細については、 https://developer.apple.com/business/documentation/Configuration-Profile-Reference.pdf にある Apple ドキュメントを参照してください。

####   <a name="derived-credentials-to-provision-ios-mobile-devices-with-certificates----1736036-1736037-1772050-2777333-----------"></a>証明書で iOS モバイル デバイスをプロビジョニングするための派生資格情報<!--  1736036, 1736037, 1772050, 2777333         -->  
Intune では、認証方法として、また、iOS デバイスの S/MIME の署名と暗号化のために[派生資格情報](../protect/derived-credentials.md)を使用できます。 派生資格情報は、証明書をデバイスに展開するための *アメリカ国立標準技術研究所 (NIST) 800-157* 標準を実装したものです。  

派生資格情報は、スマート カードのように、Personal Identity Verification (PIV) または Common Access Card (CAC) カードの使用に依存します。 モバイル デバイスのために派生資格情報を得るには、ユーザーはポータル サイト アプリから開始し、使用しているプロバイダーに固有の登録ワークフローに従います。  すべてのプロバイダーに共通することは、コンピューターのスマート カードを使用し、派生資格情報プロバイダーに対して認証するという要件です。 そのプロバイダーはその後、ユーザーのスマート カードから誘導されたデバイスに証明書を発行します。  

Intune では、次の派生資格情報プロバイダーがサポートされています。
- DISA Purebred
- Entrust Datacard
- Intercede

VPN、Wi-Fi、電子メールのデバイス構成プロファイル用の認証方法として派生資格情報を使用します。 アプリ認証や S/MIME 署名と暗号化にも使用できます。  

この標準に関する詳細については、www.nccoe.nist.gov にある「[Derived PIV Credentials](https://www.nccoe.nist.gov/projects/building-blocks/piv-credentials)」を参照してください。

#### <a name="use-graph-api-to-specify-a-on-premises-user-principal-name-as-a-variable-for-scep-certificates----5437939----------"></a>Graph API を使用し、SCEP 証明書の変数としてオンプレミスのユーザー プリンシパル名を指定します。<!--  5437939        -->  
[Intune Graph API](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0) を使用するとき、SCEP 証明書のサブジェクト代替名 (SAN) の変数として onPremisesUserPrincipalName を指定できます。



<!-- ########################## -->

## <a name="week-of-september-23-2019"></a>2019 年 9 月 23 日の週

#### <a name="ios-user-enrollment-in-preview---4817900---"></a>iOS ユーザー登録 (プレビュー)<!-- 4817900 -->
Apple の iOS 13.1 リリースには、iOS デバイス用の新しい形式の簡易管理である、ユーザー登録が含まれています。 個人所有のデバイスでは、Device Enrollment や Automated Device Enrollment (旧称 Device Enrollment Program) の代わりに使用できます。 Intune のプレビューでは、この機能セットがサポートされており、次のことが可能です。

- User Enrollment の対象をユーザー グループにする。
- エンド ユーザーが、デバイスの登録時により軽量な User Enrollment とより強固な Device Enrollment のどちらかを選択できる。

iOS 13.1 のリリースがあった 2019 年 9 月 24 日より、これらの更新プログラムをすべてのお客様にロールアウトしており、来週の終わりまでに完了する見込みです。
適用対象:

iOS 13.1 以降

#### <a name="intune-support-for-ipados-and-ios-131-devices--5439574--"></a>iPadOS および iOS 13.1 デバイスでの Intune サポート<!--5439574-->
Intune では、iPadOS および iOS 13.1 デバイス両方の管理がサポートされています。 詳細については、[このブログ投稿](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Support-for-iOS-13-1-and-iPadOS/ba-p/873094)を参照してください。

<!-- ########################## -->

## <a name="week-of-september-16-2019"></a>2019 年 9 月 16 日の週

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>アプリ管理 

#### <a name="managed-google-play-private-lob-apps---1464182----"></a>マネージド Google Play プライベート LOB アプリ<!-- 1464182  -->
Intune では、IT 管理者は、Intune コンソールに埋め込まれた iframe を使用して、マネージド Google Play にプライベート Android LOB アプリを発行できるようになりました。  以前は、IT 管理者は、Google の Play 発行コンソールに LOB アプリを直接発行する必要がありました。これにはいくつかの手順が必要で、時間がかかりました。 この新機能により、最小限の手順で LOB アプリを簡単に発行できるようになります。Intune コンソールを離れる必要はありません。  管理者は、Google を使用して開発者として手動で登録する必要がなくなり、Google の 25 ドルの登録手数料の支払いは不要になります。  マネージド Google Play を使用する Android Enterprise の管理シナリオでは、この機能 (仕事用プロファイル デバイス、専用デバイス、フル マネージド デバイス、および登録されていないデバイス) を利用できます。 Intune から、 **[クライアント アプリ]**  >  **[アプリ]**  >  **[追加]** の順に選択します。 その後、 **[アプリの種類]** の一覧から **[マネージド Google Play]** を選択します。 マネージド Google Play アプリについて詳しくは、「[Intune で managed Google Play アプリを Android エンタープライズ デバイスに追加する](../apps/apps-add-android-for-work.md)」をご覧ください。

#### <a name="windows-company-portal-experience---1473353-3598357---"></a>Windows ポータル サイトのエクスペリエンス<!-- 1473353, 3598357 -->
Windows ポータル サイトが更新されています。 Windows ポータル サイト内の [アプリ] ページでは、複数のフィルターを使用できるようになります。 [デバイスの詳細] ページも向上したユーザー エクスペリエンスで更新されています。 これらの更新をすべてのお客様にロールアウトしている最中であり、来週の終わりまでに完了する予定です。

#### <a name="macos-support-for-web-apps---3174427---"></a>Web アプリの macOS によるサポート<!-- 3174427 -->
Web アプリは、Web 上の URL へのショートカットを追加できるようにするもので、macOS ポータル サイトを使用して Dock にインストールできます。 エンド ユーザーは、macOS ポータル サイト内の Web アプリ用のアプリの詳細ページから **[インストール]** アクションにアクセスできます。 **Web リンク** アプリの種類について詳しくは、「[Microsoft Intune にアプリを追加する](../apps/apps-add.md)」と「[Web アプリを Microsoft Intune に追加する](../apps/web-app.md)」をご覧ください。

#### <a name="macos-support-for-vpp-apps---3173501----"></a>VPP アプリの macOS によるサポート<!-- 3173501  -->
Apple Business Manager を使用して購入した macOS アプリは、Intune 内で Apple VPP トークンが同期されるとコンソールに表示されます。 Intune コンソールを使用して、グループのデバイスおよびユーザーベースのライセンスの割り当て、取り消し、再割り当てを行うことができます。 Microsoft Intune は、ご自身の会社で使用するために購入した VPP アプリを管理するのに役立ちます。

- アプリ ストアからライセンス情報を報告する。
- 使用しているライセンスの数を追跡記録する。
- 所有しているより多くアプリのコピーをインストールできないようにする。

Intune と VPP の詳細については、「[Microsoft Intune によるボリューム購入アプリとブックの管理](../apps/vpp-apps.md)」を参照してください。

#### <a name="managed-google-play-iframe-support---2871756----"></a>マネージド Google Play iframe のサポート<!-- 2871756  -->
Intune では、マネージド Google Play iframe を使用して Intune コンソールに直接 Web リンクを追加したり管理したりできるようになりました。  これにより、IT 管理者は URL とアイコンのグラフィックを送信し、通常の Android アプリと同じようにデバイスにそれらのリンクを展開できます。 マネージド Google Play を使用する Android Enterprise の管理シナリオでは、この機能 (仕事用プロファイル デバイス、専用デバイス、フル マネージド デバイス、および登録されていないデバイス) を利用できます。 Intune から、 **[クライアント アプリ]**  >  **[アプリ]**  >  **[追加]** の順に選択します。 その後、 **[アプリの種類]** の一覧から **[マネージド Google Play]** を選択します。 マネージド Google Play アプリについて詳しくは、「[Intune で managed Google Play アプリを Android エンタープライズ デバイスに追加する](../apps/apps-add-android-for-work.md)」をご覧ください。

#### <a name="silently-install-android-lob-apps-on-zebra-devices---4252734----"></a>Android LOB アプリを Zebra デバイスにサイレント インストールする<!-- 4252734  -->
Android 基幹業務 (LOB) アプリを [Zebra デバイス](../configuration/android-zebra-mx-overview.md)にインストールするときに、LOB アプリのダウンロードとインストールの両方を求められるのではなく、サイレント モードでアプリをインストールできるようになります。 Intune で、 **[クライアント アプリ]**  >  **[アプリ]**  >  **[追加]** を選択します。 **[アプリの追加]** ウィンドウで、 **[基幹業務アプリ]** を選択します。 詳しくは、「[Android の基幹業務アプリを Microsoft Intune に追加する](../apps/lob-apps-android.md)」をご覧ください。

現時点では、LOB アプリがダウンロードされると、ユーザーのデバイスに**ダウンロード成功**通知が表示されます。 通知を閉じることができるのは、通知の網掛けで **[すべてクリア]** をタップした場合のみです。 この通知の問題は今後のリリースで修正される予定であり、視覚的なインジケーターなしで完全にサイレント モードでインストールされます。

#### <a name="read-and-write-graph-api-operations-for-intune-apps---5031704----"></a>Intune アプリの Graph API 操作の読み取りと書き込み<!-- 5031704  -->
アプリケーションでは、ユーザー資格情報がなくても、アプリの ID を使用して、読み取りと書き込み両方の操作で Intune Graph API を呼び出すことができます。 Microsoft Graph API for Intune にアクセスする方法については、「[Microsoft Graph での Intune の操作](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0)」を参照してください。

#### <a name="protected-data-sharing-and-encryption-for-intune-app-sdk-for-ios---3586942----"></a>iOS 用 Intune App SDK での保護されたデータ共有と暗号化<!-- 3586942  -->
アプリ保護ポリシーによって暗号化が有効にされると、iOS 用 Intune App SDK では 256 ビット暗号化キーが使用されるようになります。 すべてのアプリでは、保護されたデータの共有を許可するために、SDK バージョン 8.1.1 が必要になります。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>デバイス構成

#### <a name="support-for-ikev2-vpn-profiles-for-ios---1943438-----"></a>iOS 用の IKEv2 VPN プロファイルのサポート<!-- 1943438   -->
この更新では、IKEv2 プロトコルを使用して、iOS ネイティブ VPN クライアント用の VPN プロファイルを作成できます。 IKEv2 は、 **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  >  **[iOS]** (プラットフォーム) > **[VPN]** (プロファイルの種類) > **[接続の種類]** での、新しい接続の種類です。

これらの VPN プロファイルではネイティブ VPN クライアントが構成されるので、マネージド デバイスに対して VPN クライアント アプリがインストールまたはプッシュされることはありません。 この機能を使用するには、デバイスを Intune に登録する必要があります (MDM 登録)。

現在構成できる VPN 設定については、[iOS デバイスでの VPN 設定の構成](../configuration/vpn-settings-ios.md)に関する記事をご覧ください。

適用対象:
- iOS

#### <a name="device-features-device-restrictions-and-extension-profiles-for-ios-and-macos-settings-are-shown-by-enrollment-type---4886161-----"></a>iOS と macOS の設定のデバイス機能、デバイス制限、および拡張機能プロファイルは、登録の種類別に表示されます<!-- 4886161   -->

Intune で、iOS デバイスおよび macOS デバイス用のプロファイルを作成します ( **[デバイスの構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  >  **[iOS]** または **[macOS]** (プラットフォーム) > **[デバイス機能]** 、 **[デバイスの制限]** 、または **[拡張機能]** (プロファイルの種類))。 

この更新では、Intune ポータルで利用可能な設定は、適用対象の登録の種類によって分類されます。

- iOS
  - ユーザー登録
  - デバイスの登録
  - デバイスの自動登録 (監視)
  - すべての登録の種類

- macOS
  - ユーザー承認済み
  - デバイスの登録
  - デバイスの自動登録
  - すべての登録の種類

適用対象:
- iOS

#### <a name="new-voice-control-settings-for-supervised-ios-devices-running-in-kiosk-mode---4892835-----"></a>キオスク モードで実行されている監視対象 iOS デバイスの新しい音声制御設定<!-- 4892835   -->
Intune では、監視対象の iOS デバイスをキオスクまたは専用デバイスとして実行するポリシーを作成することができます ( **[デバイスの構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  >  **[iOS]** (プラットフォーム) > **[デバイスの制限]** (プロファイルの種類) > **[キオスク]** )。

この更新では、制御できる新しい設定があります。
- **音声制御**: キオスク モードのときにデバイスでの音声制御を有効にします。
- **音声制御の変更**: キオスク モードのときに、ユーザーはデバイスで音声制御の設定を変更できます。

現在の設定を見るには、[iOS キオスクの設定](../configuration/device-restrictions-ios.md#kiosk)に関する記事をご覧ください。

適用対象:
- iOS 13.0 以降

#### <a name="use-single-sign-on-for-apps-and-websites-on-your-ios-and-macos-devices---4893175-----"></a>iOS および macOS デバイスでアプリと Web サイトに対するシングル サインオンを使用する<!-- 4893175   -->
この更新では、iOS デバイスおよび macOS デバイス用にいくつかの新しいシングル サインオン設定があります ( **[デバイスの構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  >  **[iOS]** または **[macOS]** (プラットフォーム) > **[デバイス機能]** (プロファイルの種類))。

これらの設定を使用して、シングル サインオン エクスペリエンスを構成します (特に、Kerberos 認証を使用するアプリと Web サイトの場合)。 汎用資格情報シングル サインオン アプリ拡張機能と、Apple の組み込み Kerberos 拡張機能のいずれかを選択できます。

構成できる現在のデバイス機能を確認するには、[iOS デバイスの機能](../configuration/ios-device-features-settings.md)および [macOS デバイスの機能](../configuration/macos-device-features-settings.md)に関する記事をご覧ください。

適用対象:
- iOS 13.0 以降
- macOS 10.15 以降

#### <a name="associate-domains-to-apps-on-macos-1015-devices---4898079-----"></a>macOS 10.15 以降のデバイス上のアプリにドメインを関連付ける<!-- 4898079   -->
macOS デバイスでは、さまざまな機能を構成し、ポリシーを使用してこれらの機能をデバイスにプッシュすることができます ( **[デバイスの構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  >  **[macOS]** (プラットフォーム) > **[デバイス機能]** (プロファイルの種類))。 この更新では、ドメインをアプリに関連付けることができます。 この機能は、資格情報をアプリに関連する Web サイトと共有するのに役立ち、Apple のシングル サインオン拡張機能、ユニバーサル リンク、パスワード オートフィルで使用できます。 

構成できる現在の機能を確認するには、「[Intune での macOS デバイスの機能設定](../configuration/macos-device-features-settings.md)」をご覧ください。

適用対象:
- macOS 10.15 以降

#### <a name="use-itunes-and-apps-in-the-itunes-app-store-url-when-showing-or-hiding-apps-on-ios-supervised-devices---4928474-----"></a>iOS 監視対象デバイスでアプリを表示または非表示にするときは、iTunes App ストアの URL で "iTunes" と "apps" を使用する<!-- 4928474   --> 
Intune では、監視対象の iOS デバイスでアプリの表示と非表示を切り替えるポリシーを作成することができます ( **[デバイスの構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  >  **[iOS]** (プラットフォーム) > **[デバイスの制限]** (プロファイルの種類) > **[アプリの表示/非表示]** )。 

`https://itunes.apple.com/us/app/work-folders/id950878067?mt=8` などの iTunes App ストア URL を入力できます。 この更新では、次のように、`apps` と `itunes` の両方を URL で使用できます。
- `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`
- `https://apps.apple.com/us/app/work-folders/id950878067?mt=8`

これらの設定の詳細については、「[アプリの表示/非表示](../configuration/device-restrictions-ios.md#show-or-hide-apps)」を参照してください。

適用対象:
- iOS

#### <a name="windows-10-compliance-policy-password-type-values-are-clearer-and-match-csp---5138985---"></a>Windows 10 コンプライアンス ポリシーのパスワードの種類の値が、より明確になり、CSP と一致する<!-- 5138985 -->
Windows 10 デバイスでは、特定のパスワード機能を必要とするコンプライアンス ポリシーを作成できます ( **[デバイスのポリシー準拠]**  >  **[ポリシー]**  >  **[ポリシーの作成]**  >  **[Windows 10 以降]** (プラットフォーム) > **[システム セキュリティ]** )。 この更新では:
- **[パスワードの種類]** の値がより明確になり、[DeviceLock/AlphanumericDevicePasswordRequired CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-alphanumericdevicepasswordrequired) と一致するように更新されています。
- **[パスワードの有効期限 (日数)]** の設定が、1 - 730 日の値を指定できるように更新されています。 

Windows 10 のコンプライアンス設定について詳しくは、「[Intune を使用してデバイスを準拠または非準拠としてマークするための Windows 10 以降の設定](../protect/compliance-policy-create-windows.md)」をご覧ください。 

適用対象:
- Windows 10 以降

 #### <a name="updated-ui-for-configuring-microsoft-exchange-on-premises-access---4092920---"></a>Microsoft Exchange のオンプレミス アクセスを構成するための更新された UI<!-- 4092920 -->  
[Microsoft Exchange のオンプレミス アクセスを構成する](../protect/conditional-access-exchange-create.md)コンソールを更新しました。 Exchange オンプレミス アクセスのすべての構成を、"*Exchange オンプレミス アクセス制御を有効にする*" コンソールの同じウィンドウで使用できるようになりました。  

#### <a name="allow-or-restrict-adding-app-widgets-to-the-home-screen-on-android-enterprise-work-profile-devices---1109650----"></a>Android Enterprise 仕事用プロファイル デバイスのホーム画面へのアプリ ウィジェットの追加を許可または制限する<!-- 1109650  --> 
Android Enterprise デバイスでは、仕事用プロファイルで機能を構成することができます ( **[デバイスの構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  >  **[Android Enterprise]** (プラットフォーム) > **[仕事用プロファイルのみ] > [デバイスの制限]** (プロファイルの種類))。 この更新では、仕事用プロファイル アプリによって公開されているウィジェットをデバイスのホーム画面に追加することを、ユーザーに許可できます。

構成できる設定を確認するには、「[Intune を使用して機能を許可または制限するように Android エンタープライズ デバイスを設定する](../configuration/device-restrictions-android-for-work.md)」をご覧ください。

適用対象:
- Android Enterprise 仕事用プロファイル

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>デバイスの登録

#### <a name="new-tenants-will-default-away-from-android-device-administrator-management---4869790-----"></a>新しいテナントは既定で Android デバイス管理者の管理から外れる<!-- 4869790   -->
Android のデバイス管理者の機能は、Android Enterprise によって置き換えられています。 そのため、新しい登録には代わりに Android Enterprise を使用することをお勧めします。 今後の更新では、新しいテナントでデバイス管理者の管理を使用するには、Android の登録で次の前提条件手順を完了する必要があります。 **[Intune]**  >  **[デバイスの登録]**  >  **[Android の登録]**  >  **[デバイス管理者特権を持つ個人所有のデバイスと会社所有のデバイス]**  >  **[デバイス管理者によってデバイスを管理します]** に移動します。

既存テナントの環境は変更されません。

Intune での Android デバイス管理者について詳しくは、「[Android デバイス管理者の登録](https://docs.microsoft.com/intune/android-enroll-device-administrator)」をご覧ください。

#### <a name="list-of-dep-devices-associated-with-a-profile---5012045-idmiss---"></a>プロファイルに関連付けられている DEP デバイスの一覧<!-- 5012045 idmiss -->
プロファイルに関連付けられている Apple Automated Device Enrollment Program (DEP) デバイスのページ分割された一覧が表示されるようになりました。 一覧の任意のページから一覧を検索できます。 一覧を表示するには、 **[Intune]**  >  **[デバイスの登録]**  >  **[Apple の登録]**  >  **[Enrollment Program トークン]** > トークンを選択 > **[プロファイル]** > プロファイルを選択 > **[割り当てられたデバイス]** ( **[監視]** の下) に移動します。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>デバイス管理

#### <a name="more-android-fully-managed-support---3464667-4631425-4631440-5227935-4062195-----"></a>Android フル マネージドのサポートの向上<!-- 3464667, 4631425, 4631440, 5227935, 4062195   -->
Android フル マネージド デバイスに対して次のサポートが追加されました。

- フル マネージド Android 用の SCEP 証明書を、デバイス所有者として管理されているデバイスでの証明書認証に使用できます。 SCEP 証明書は、仕事用プロファイル デバイスで既にサポートされています。  デバイス所有者の SCEP 証明書を使用すると、次のことが可能になります。 <!-- 5227935 -->
    - Android Enterprise の DO セクションで SCEP プロファイルを作成する
    - 認証用の DO Wi-Fi プロファイルに SCEP 証明書をリンクする
    - 認証用の DO VPN プロファイルに SCEP 証明書をリンクする
    - 認証用の DO 電子メール プロファイルに SCEP 証明書をリンクする (AppConfig を使用)
- システム アプリは Android Enterprise デバイスでサポートされています。 Intune で、 **[クライアント アプリ]**  >  **[アプリ]**  >  **[追加]** を選択して、Android Enterprise システム アプリを追加します。 **[アプリの種類]** の一覧で、 **[Android Enterprise システム アプリ]** を選択します。 詳しくは、「[Microsoft Intune に Android Enterprise システム アプリを追加する](../apps/apps-ae-system.md)」をご覧ください。 <!-- 4062195 -->
- **[デバイスのポリシー準拠]**  >  **[Android Enterprise]**  >  **[デバイスの所有者]** で、Google SafetyNet 構成証明レベルを設定するコンプライアンス ポリシーを作成できます。   <!-- 4631425 -->
- Android Enterprise フル マネージド デバイスでは、モバイル脅威防御プロバイダーがサポートされています。 **[デバイスのポリシー準拠]**  >  **[Android Enterprise]**  >  **[デバイスの所有者]** では、許容される脅威レベルを選択できます。 <!-- 4631440 --> [Intune を使用してデバイスを準拠または非準拠としてマークするための Android エンタープライズ設定](../protect/compliance-policy-create-android-for-work.md#device-owner)に関するページに、現在の設定が記載されています。
- Android Enterprise フル マネージド デバイスでは、アプリ構成ポリシーを使用して Microsoft Launcher アプリを構成し、フル マネージド デバイスでの標準化されたエンド ユーザー エクスペリエンスを実現できるようになりました。 Microsoft Launcher アプリを使用して、Android デバイスを個人用に設定することができます。 Microsoft アカウントまたは職場/学校アカウントでアプリを使用して、カスタマイズしたフィード内で予定表、ドキュメント、最近のアクティビティにアクセスできます。 <!-- 5334044 -->

この更新では、Android Enterprise フル マネージドに対する Intune のサポートが一般提供になったことをお知らせします。

適用対象:

- Android エンタープライズのフル マネージド デバイス

#### <a name="send-custom-notifications-to-a-single-device---4928910---"></a>1 台のデバイスにカスタム通知を送信する<!-- 4928910 -->
1 台のデバイスを選択してから、リモート デバイス操作を使用して、[そのデバイスだけにカスタム通知を送信する](../remote-actions/custom-notifications.md#send-a-custom-notification-to-a-single-device)ことができるようになりました。

#### <a name="wipe-and-passcode-reset-actions-arent-available-for-ios-devices-that-are-enrolled-by-using-user-enrollment---4950491---"></a>ユーザー登録を使用して登録された iOS デバイスでは、ワイプとパスコードのリセット操作は使用できません<!-- 4950491 -->
ユーザー登録は、新しい種類の Apple デバイス登録です。 ユーザー登録を使用してデバイスを登録すると、そのようなデバイスではワイプとパスコードのリセットのリモート操作を実行できなくなります。

#### <a name="intune-support-for-ios-13-and-macos-catalina-devices---4665317---"></a>Intune での iOS 13 および macOS Catalina デバイスのサポート<!-- 4665317 -->
Intune では、iOS 13 デバイスと macOS Catalina デバイス両方の管理がサポートされるようになりました。
詳しくは、[iOS 13 と iPadOS の Microsoft Intune サポートに関するブログ投稿](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Support-for-iOS-13-and-iPadOS/ba-p/861998)をご覧ください。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>デバイス セキュリティ

#### <a name="bitlocker-support-for-client-driven-recovery-password-rotation----3444125---"></a>クライアント主導の回復パスワード ローテーションの BitLocker サポート<!--  3444125 -->
Intune Endpoint Protection の設定を使用して、Windows バージョン 1909 以降が実行されているデバイス上の BitLocker に対する[クライアント主導の回復パスワード ローテーション](../protect/endpoint-protection-windows-10.md#windows-encryption)を構成します。

この設定により、OS ドライブの復旧 (bootmgr または WinRE を使用して) および固定データ ドライブでの回復パスワードのロック解除の後で、クライアント主導の回復パスワード更新が開始します。 この設定により、使用されていた特定の回復パスワードは更新され、ボリューム上の他の未使用のパスワードは変更されません。 詳しくは、[ConfigureRecoveryPasswordRotation](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) に関する BitLocker CSP のドキュメントをご覧ください。

#### <a name="tamper-protection-for-windows-defender-antivirus---4705448----------"></a>Windows Defender ウイルス対策の改ざん保護<!-- 4705448        -->
Intune を使用して、Windows Defender ウイルス対策の "*改ざん保護*" を管理します。 Windows 10 エンドポイント保護用のデバイス構成プロファイルを使用するときに、Microsoft Defender セキュリティ センター グループで[改ざん保護の設定](../protect/endpoint-protection-windows-10.md#microsoft-defender-security-center)を探します。 改ざん保護を "*有効*" に設定すると改ざん保護の制限をオンにでき、"*無効*" に設定するとオフにでき、"*未構成*" に設定するとデバイスを現在の構成のままにすることができます。  

改ざん保護について詳しくは、Windows ドキュメントの「[改ざん防止機能によってセキュリティ設定の変更を防止する](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/prevent-changes-to-security-settings-with-tamper-protection)」をご覧ください。

#### <a name="advanced-settings-for-windows-defender-firewall-are-now-generally-available----5317392---------"></a>Windows Defender ファイアウォールの詳細設定が一般提供されるようになった<!--  5317392       -->  
デバイス構成プロファイルの一部として構成する[エンドポイント保護用の Windows Defender カスタム ファイアウォール規則](../protect/endpoint-protection-configure.md#add-custom-firewall-rules-for-windows-10-devices)は、パブリック プレビューを終了し、一般提供 (GA) されています。  これらの規則を使用して、アプリケーション、ネットワーク、アドレス、ポートに対する受信と送信の動作を指定できます。 これらの規則は、7 月にパブリック プレビューとしてリリースされました。 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>ロールベースのアクセス制御

#### <a name="scope-tags-now-support-terms-of-use-policies---2358863-idmiss---"></a>スコープ タグで使用条件ポリシーがサポートされるようになりました<!-- 2358863 idmiss -->
[スコープ タグ](scope-tags.md)を使用条件ポリシーに割り当てることができるようになりました。 これを行うには、 **[Intune]**  >  **[デバイスの登録]**  >  **[使用条件]** > 一覧の項目を選択 > **[プロパティ]**  >  **[スコープ タグ]** に移動し、スコープ タグを選択します。

## <a name="week-of-september-9-2019"></a>2019 年 9 月 9 日の週

### <a name="app-management"></a>アプリ管理

#### <a name="updates-to-microsoft-intune-app---4997846---"></a>Microsoft Intune アプリに対する更新<!-- 4997846 -->
次の機能強化によって Android 用の Microsoft Intune アプリが更新されています。
- 最も重要な操作のための下部ナビゲーションが含まれるように、レイアウトの更新と強化が行われました。
- ユーザーのプロファイルを表示するページが追加されました。
- ユーザーがアクション可能な通知 (例: デバイス設定の更新が必要) の表示がアプリに追加されました。
- カスタム プッシュ通知の表示がサポートされるようになり、iOS と Android 用のポータル サイト アプリに最近追加されたサポートと連携します。 詳細は、「[Intune でカスタム通知を送信する](../remote-actions/custom-notifications.md)」を参照してください。

#### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal---4394993---"></a>iOS デバイスの場合は、ポータル サイトの登録プロセスのプライバシー画面をカスタマイズします<!-- 4394993 -->
Markdown を使用すると、iOS の登録時にエンド ユーザーに表示されるポータル サイトのプライバシー画面をカスタマイズできます。 具体的には、組織がデバイス上で参照または実行できない項目の一覧をカスタマイズできます。 詳しくは、[Intune ポータル サイト アプリを構成する方法](../apps/company-portal-app.md#privacy-statement-customization)に関するページをご覧ください。


## <a name="week-of-september-2-2019"></a>2019 年 9 月 2 日の週

### <a name="monitor-and-troubleshoot"></a>監視とトラブルシューティング

#### <a name="intune-user-interface-update--tenant-status-dashboard---5273210----"></a>Intune ユーザー インターフェイスの更新 – テナントの状態ダッシュボード<!-- 5273210  -->
テナントの状態ダッシュボード用のユーザー インターフェイスが、Azure ユーザー インターフェイスの形式に準拠するように更新されました。 詳しくは、[テナントの状態](../tenant-status.md)に関する記事をご覧ください。

## <a name="week-of-august-26-2019"></a>2019 年 8 月 26 日の週

### <a name="configure-microsoft-edge-settings-using-administrative-templates-for-windows-10-and-newer---5228061---"></a>Windows 10 以降向けの管理用テンプレートを使用し、Microsoft Edge 設定を構成する<!-- 5228061 -->

Windows 10 以降のデバイスでは、Intune でグループポリシー設定を構成するための管理用テンプレートを作成できます。 この更新プログラムでは、Microsoft Edge バージョン 77 以降に適用される設定を構成できます。

管理用テンプレートの詳細については、[Windows 10 テンプレートを使用し、Intune でグループ ポリシー設定を構成する方法](../configuration/administrative-templates-windows.md)に関するページを参照してください。

適用対象:

- Windows 10 以降 (Windows RS4 +)

## <a name="week-of-august-12-2019"></a>2019 年 8 月 12 日の週

### <a name="app-management"></a>アプリ管理

#### <a name="control-ios-app-uninstall-behavior-at-device-unenrollment---3504144-----"></a>デバイス登録解除時の iOS アプリのアンインストール動作を制御する<!-- 3504144   -->
管理者は、ユーザーまたはデバイス グループ レベルでデバイスが登録解除された場合に、デバイス上のアプリを削除するか保持するかを管理できます。 

#### <a name="categorize-microsoft-store-for-business-apps---3926922---"></a>ビジネス向け Microsoft Store アプリの分類<!-- 3926922 -->
ビジネス向け Microsoft ストア アプリを分類できます。 これを行うには、 **[Intune]**  >  **[クライアント アプリ]**  >  **[アプリ]** > [Select a Microsoft Store for Business app]\(ビジネス向け Microsoft ストア アプリを選択する\) > **[アプリ情報]**  >  **[カテゴリ]** の順に選択します。 ドロップダウン メニュー上で、カテゴリを割り当てます。

#### <a name="customized-notifications-for-microsoft-intune-app-users---4843354----"></a>Microsoft Intune アプリ ユーザー向けにカスタマイズされた通知<!-- 4843354  -->
Microsoft Intune の Android 用アプリでは、カスタム プッシュ通知の表示がサポートされるようになりました。iOS および Android 用のポータル サイト アプリに最近追加されたサポートと連携しています。 詳細は、「[Intune でカスタム通知を送信する](../remote-actions/custom-notifications.md)」を参照してください。

### <a name="device-configuration"></a>デバイス構成

#### <a name="new-features-for-android-enterprise-dedicated-devices-in-multi-app-mode---3755304-3041943-3041946-----"></a>マルチアプリ モードでの Android エンタープライズ専用デバイスの新機能<!-- 3755304 3041943 3041946   -->

Intune では、Android エンタープライズ専用デバイス上のキオスク スタイルのエクスペリエンスの機能と設定を制御できます ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  >  **[Android エンタープライズ] (プラットフォーム)** > **[デバイスの所有者のみ]、[デバイスの制限]** (プロファイルの種類))。

この更新プログラムでは、次の機能が追加されています。

- **[専用デバイス]**  >  **[複数アプリ]** : **[仮想ホーム ボタン]** は、デバイス上で上方向にスワイプするか、またはユーザーが移動できるように画面上でのフローティングによって、表示できます。
- **[専用デバイス]**  >  **[複数アプリ]** : **[懐中電灯へのアクセス]** を利用すると、ユーザーは懐中電灯を使用できます。 
- **[専用デバイス]**  >  **[複数アプリ]** : **[メディア ボリューム コントロール]** を利用すると、ユーザーはスライダーを使用してデバイスのメディア ボリュームを制御できます。 
- **[専用デバイス]**  >  **[複数アプリ]** : **[Enable a screensaver]\(スクリーンセーバーを有効にする\)** では、カスタム画像をアップロードして、スクリーンセーバーが表示されるタイミングを制御します。

現在の設定を確認するには、[Intune を使用して Android エンタープライズ デバイスの機能を許可または制限する設定](../configuration/device-restrictions-android-for-work.md#dedicated-device-settings)に関するページを参照してください。

適用対象:

- Android Enterprise 専用デバイス

#### <a name="new-app-and-configuration-profiles-for-android-enterprise-fully-managed-devices---3574215-3574238-3574235-3574232-----"></a>Android エンタープライズのフル マネージド デバイスにおける新しいアプリと構成プロファイル<!-- 3574215 3574238 3574235 3574232   -->
プロファイルを使用して、Android エンタープライズ デバイスの所有者 (フル マネージド) デバイスに VPN、電子メール、および Wi-Fi 設定を適用する設定を構成できます。 この更新プログラムでは、次のことができます。

- [アプリ構成ポリシー](../apps/app-configuration-policies-use-android.md)を使用して、Outlook、Gmail、および Nine Work 電子メールの設定を展開します。
- デバイス構成プロファイルを使用して、[信頼されたルート証明書の設定](../protect/certificates-configure.md)を展開します。
- デバイス構成プロファイルを使用して、[VPN](../configuration/vpn-settings-android-enterprise.md) および [Wi-Fi](../configuration/wi-fi-settings-android-enterprise.md) 設定を展開します。

> [!IMPORTANT]
> この機能を使用すると、ユーザーは VPN、Wi-Fi、および電子メール プロファイル用のユーザー名とパスワードを使って認証されます。 現時点では、証明書ベースの認証は使用できません。

適用対象:  
- Android エンタープライズ デバイス所有者 (フル マネージド)

#### <a name="control-the-apps-files-documents-and-folders-that-open-when-users-sign-in-to-macos-devices--3914202-----"></a>ユーザーが macOS デバイスにサインインするときに開くアプリ、ファイル、ドキュメント、およびフォルダーを制御する<!--3914202   -->
macOS デバイス上で機能を有効にして構成できます ( **[デバイスの構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  >  **[macOS]** (プラットフォーム) > **[デバイス機能]** (プロファイルの種類))。 

この更新プログラムには、登録済みデバイスにユーザーがサインインするときにどのアプリ、ファイル、ドキュメント、フォルダーが開かれるかを制御するために、新しい [ログイン項目] 設定があります。 

現在の設定を確認するには、「[Intune での macOS デバイスの機能設定](../configuration/macos-device-features-settings.md)」を参照してください。

適用対象:  
- macOS

#### <a name="deadlines-replace-engaged-restart-settings-for-windows-update-rings---4464404----------"></a>Windows Update リングでの再起動猶予期間の設定が [期限] に置き換わった<!-- 4464404        -->
最近の [Windows サービスの変更](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1903#servicing)に合わせて、Intune の Windows 10 更新リングでは[期限の設定がサポートされる](../protect/windows-update-settings.md)ようになりました。 "*期限*" によって、デバイスに機能とセキュリティの更新プログラムがインストールされるタイミングが決まります。  Windows 10 1903 以降を実行しているデバイス上では、"*期限*" が "*再起動猶予期間*" の構成よりも優先されます。  将来は、Windows 10 の以前のバージョンでも、"*期限*" が "*再起動猶予期間*" よりも優先される予定です。  

"*期限*" を構成しない場合、デバイスでは引き続き "*再起動猶予期間*" の設定が使用されますが、将来の更新プログラムでは Intune による再起動猶予期間の設定のサポートは廃止される予定です。  

お使いのすべての Windows 10 デバイスに対して、"*期限*" を使用することを計画してください。 "*期限*" の設定が行われたら、"*再起動猶予期間*" に関する Intune の構成を未構成に変更できます。 未構成に設定されている場合、Intune ではデバイス上のそれらの設定の管理を停止しますが、その設定に対応する最後の構成をデバイスから削除することはありません。 そのため、"*再起動猶予期間*" に設定された最後の構成は、それらの設定が Intune 以外の方法によって変更されるまで、デバイス上でアクティブに使用されたままになります。 その後、Windows のデバイス バージョンが変更された場合、または "*期限*" に対する Intune のサポートがそのデバイスの Windows バージョンまで拡張された場合、デバイスでは、既に設定されている新しい設定の使用が開始されます。

#### <a name="support-for-multiple-microsoft-intune-certificate-connectors-----4704642--------"></a>複数の Microsoft Intune Certificate Connector のサポート<!--   4704642      -->
Intune では、[PKCS 操作に対応した Microsoft Intune Certificate Connector ](../protect/certficates-pfx-configure.md) の複数のインストールと使用がサポートされるようになりました。 この変更により、コネクタの負荷分散と高可用性がサポートされます。 各コネクタ インスタンスでは、Intune からの証明書要求を処理できます。  1 つのコネクタが使用できない場合は、それ以外のコネクタが引き続き要求を処理します。

複数のコネクタを使用するために、最新バージョンのコネクタ ソフトウェアにアップグレードする必要はありません。  

#### <a name="new-settings-and-changes-to-existing-settings-to-restrict-features-on-ios-and-macos-devices---4867699-4867709-----"></a>iOS および macOS デバイス上で機能を制限するための新しい設定と既存の設定の変更<!-- 4867699 4867709   -->
プロファイルを作成して iOS および macOS を実行するデバイス上での設定を制限できます ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  >  **[iOS]** または **[macOS]** (プラットフォームの種類) > **[デバイスの制限]** )。 この更新プログラムには、次の機能が含まれます。

- **[macOS]**  >  **[デバイスの制限]**  >  **[クラウドとストレージ]** で、新しい **[ハンドオフ]** 設定を使用して、1 つの macOS デバイス上でユーザーによる作業の開始をブロックし、別の macOS または iOS デバイス上で作業を続行します。

  現在の設定を確認するには、「[Intune を使用して機能を許可または制限するように macOS デバイスを設定する](../configuration/device-restrictions-macos.md)」を参照してください。

- **[iOS]**  >  **[デバイスの制限]** には、いくつかの変更点があります。

  - **[組み込みアプリ]**  >  **[iPhone を探す (監視モードのみ)]** :Find My アプリ機能にあるこの機能をブロックするための新しい設定。 
  - **[組み込みアプリ]**  >  **[友達を探す (監視モードのみ)]** :Find My アプリ機能にあるこの機能をブロックするための新しい設定。 
  - **[ワイヤレス]**  >  **[Wi-Fi 状態の変更 (監視モードのみ)]** :ユーザーがデバイス上で Wi-Fi をオンまたはオフにできないようにする新しい設定。
  - **[キーボードと辞書]**  >  **[QuickPath (監視モードのみ)]** :QuickPath 機能をブロックする新しい設定。
  - **[クラウドとストレージ]** : **[アクティビティの継続]** は **[ハンドオフ]** に名称変更されました。

  現在の設定を確認するには、「[Intune を使用して機能を許可または制限するように iOS デバイスを設定する](../configuration/device-restrictions-ios.md)」を参照してください。

適用対象:  
- macOS 10.15 以降
- iOS 13 以降

#### <a name="some-unsupervised-ios-device-restrictions-will-become-supervised-only-with-the-ios-130-release---4867809-----"></a>監視されていない一部の iOS デバイスの制限が iOS 13.0 リリースでは監視モードのみになる<!-- 4867809   -->
この更新プログラムでは、iOS 13.0 リリースによって一部の設定は監視モードのみのデバイスに適用されます。 これらの設定が構成済みであり、iOS 13.0 リリースより前の監視されていないデバイスに割り当てられている場合は、監視されていないそれらのデバイスに引き続き設定が適用されます。 また、デバイスが iOS 13.0 にアップグレードされた後も、引き続き適用されます。 バックアップおよび復元された監視されていないデバイス上では、これらの制限は削除されます。

設定は次のとおりです。

- アプリ ストア、ドキュメント表示、ゲーム
  - アプリ ストア
  - 成人指定の iTunes ミュージック、ポッドキャスト、またはニュース コンテンツ
  - Game Center の友だちの追加
  - マルチプレイヤー ゲーム
- 組み込みアプリ
  - カメラ
    - FaceTime
  - Safari
    - オートフィル
- クラウドとストレージ
  - iCloud へのバックアップ
  - iCloud ドキュメントの同期のブロック
  - iCloud キーチェーンの同期をブロックする

現在の設定を確認するには、「[Intune を使用して機能を許可または制限するように iOS デバイスを設定する](../configuration/device-restrictions-ios.md)」を参照してください。

適用対象:  
- iOS 13.0 以降

#### <a name="improved-device-status-for-macos-filevault-encryption---4944983-----------"></a>macOS の FileVault 暗号化に対するデバイス ステータスの改善<!-- 4944983         -->
macOS デバイス上での FileVault 暗号化に対する[デバイス ステータス メッセージ](../protect/encryption-monitor.md#device-encryption-status)が、いくつか更新されました。

#### <a name="some-windows-defender-antivirus-scan-settings-in-the-reporting-show-a-failed-status---5119229---"></a>レポート内の一部の Windows Defender ウイルス対策スキャンの設定に失敗のステータスが表示される<!-- 5119229 -->
Intune では、Windows Defender ウィルス対策を使用するポリシーを作成して、お使いの Windows 10 デバイスをスキャンできます ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  >  **[Windows 10 以降]** (プラットフォーム) > **[デバイスの制限]** (プロファイルの種類) > **[Windows Defender ウィルス対策]** )。 **[Time to perform a daily quick scan]\(毎日のクイック スキャンを実行する時刻\)** および **[Type of system scan to perform]\(実行するシステム スキャンの種類\)** のレポートで、実際には成功のステータスになる場合に、失敗のステータスが表示されます。 

この更新プログラムでは、この動作は変更されています。 そのため、 **[Time to perform a daily quick scan]\(毎日のクイック スキャンを実行する時刻\)** と **[Type of system scan to perform]\(実行するシステム スキャンの種類\)** の設定には、スキャンが正常に終了した場合には成功ステータスが表示され、設定の適用に失敗した場合には失敗のステータスが表示されます。

Windows Defender ウイルス対策の設定の詳細については、[Intune を使用して機能を許可または制限する Windows 10 (以降) のデバイス設定](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus)に関するページを参照してください。

### <a name="device-enrollment"></a>デバイスの登録

#### <a name="default-scope-tags---3702875----"></a>既定のスコープ タグ<!-- 3702875  -->
新しい組み込みの既定のスコープ タグを使用できるようになりました。 スコープ タグをサポートしているタグ付けされていないすべての Intune オブジェクトが、自動的に既定のスコープ タグに割り当てられます。 現在の管理エクスペリエンスに合うように、**既定**のスコープ タグがすべての既存のロール割り当てに追加されます。 既定のスコープ タグが付与された Intune オブジェクトを管理者に表示しないようにする場合は、ロールの割り当てから既定のスコープ タグを削除します。 この機能は System Center Configuration Manager のセキュリティ スコープ機能とほぼ同じです。 詳細については、[分散型 IT での RBAC とスコープ タグの使用](scope-tags.md)に関するページを参照してください。

#### <a name="android-enrollment-device-administrator-support---4869749-----"></a>Android 登録のデバイス管理者のサポート<!-- 4869749   -->
Android デバイス管理者の登録オプションが、[Android 登録] ページに追加されました ( **[Intune]**  >  **[デバイスの登録]**  >  **[Android の登録]** )。 Android デバイス管理者は引き続き、すべてのテナントに対して既定で有効になります。  詳細については、「[Android デバイス管理者の登録](../enrollment/android-enroll-device-administrator.md)」を参照してください。

#### <a name="skip-more-screens-in-setup-assistant---4877451----"></a>セットアップ アシスタントにある画面をさらにスキップする <!--4877451  -->
Device Enrollment Program プロファイルを設定して、次のセットアップ アシスタントの画面をスキップできます。
- iOS の場合
    - 表示形式
    - 簡易言語
    - 優先する言語
    - デバイスからデバイスへの移行
- macOS の場合
    - 画面の表示時間
    - Touch ID の設定

セットアップ アシスタントのカスタマイズの詳細については、[iOS 用の Apple 登録プロファイルの作成](../enrollment/device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile)および [macOS 用の Apple 登録プロファイルの作成](../enrollment/device-enrollment-program-enroll-macos.md#create-an-apple-enrollment-profile)に関するページを参照してください。

#### <a name="add-a-user-column-to-the-autopilot-device-csv-upload-process---3823054---"></a>Autopilot デバイスの CSV アップロード プロセスにユーザー列を追加する<!-- 3823054 -->
Autopilot デバイスの CSV アップロードにユーザー列を追加できるようになりました。 これにより、CSV をインポートするときにユーザーを一括で割り当てることができます。 詳細については、「[Windows Autopilot を使用して Intune に Windows デバイスを登録する](../enrollment/enrollment-autopilot.md)」を参照してください。


### <a name="device-management"></a>デバイス管理

#### <a name="configure-automatic-device-clean-up-time-limit-down-to-30-days--4231059----"></a>自動デバイス クリーンアップの制限時間を 30 日まで短く構成する<!--4231059  -->
自動デバイス クリーンアップの制限時間を、最後にサインインしてから 30 日 (以前の制限は 90 日) に短縮して設定できます。 これを行うには、 **[Intune]**  >  **[デバイス]**  >  **[セットアップ]**  >  **[デバイスのクリーン アップ ルール]** に移動します。

#### <a name="build-number-included-on-android-device-hardware-page---4461910-----"></a>Android デバイスの [ハードウェア] ページに含まれるビルド番号<!-- 4461910   -->
各 Android デバイスの [ハードウェア] ページにある新しい項目には、デバイスのオペレーティング システムのビルド番号が含まれます。 詳細については、「[Intune でデバイスの詳細を確認する](../remote-actions/device-inventory.md)」を参照してください。


<!-- ########################## -->

## <a name="week-of-august-5-2019"></a>2019 年 8 月 5 日の週

### <a name="zebra-technologies-is-a-supported-oem-for-oemconfig-on-android-enterprise-devices---4843713---"></a>Android エンタープライズ デバイス上で Zebra Technologies 社が OEMConfig に対してサポートされている OEM となる<!-- 4843713 -->

Intune では、デバイス構成プロファイルを作成して、OEMConfig を使用する Android エンタープライズ デバイスに設定を適用できます (**デバイス構成** >  **[プロファイル]**  >  **[プロファイルの作成]**  >  **[Android エンタープライズ]** (プラットフォーム) > **[OEMConfig]** (プロファイルの種類))。

この更新プログラムでは、Zebra Technologies 社は、OEMConfig に対してサポートされている Original Equipment Manufacturer (OEM) です。 OEMConfig の詳細については、「[OEMConfig を利用して Android エンタープライズ デバイスを使用および管理する](../configuration/android-oem-configuration-overview.md)」を参照してください。

適用対象:  
- Android エンタープライズ

<!-- ########################## -->

## <a name="week-of-july-22-2019"></a>2019 年 7 月 22 日の週 

### <a name="app-management"></a>アプリ管理

#### <a name="customized-notifications-for-users-and-groups---16766574------------"></a>ユーザーとグループ向けにカスタマイズされた通知<!-- 16766574          -->
Intune で管理している iOS デバイスと Android デバイスで、ポータル サイト アプリケーションからユーザーに宛て、カスタムのプッシュ通知を送信します。 このようなモバイル プッシュ通知は自由形式のテキストで高度なカスタマイズが可能であり、あらゆる目的に使用できます。 組織のさまざまなユーザー グループに通知の対象を設定できます。 詳細は、「[カスタム通知](../remote-actions/custom-notifications.md)」を参照してください。

#### <a name="googles-device-policy-controller-app---3041950----"></a>Google のデバイス ポリシー コントローラー アプリ<!-- 3041950  -->
マネージド ホーム スクリーン アプリで、Google の Android デバイス ポリシー アプリにアクセスできるようになりました。 マネージド ホーム スクリーン アプリは、マルチアプリ キオスク モードを使用する Android Enterprise (AE) 専用デバイスとして Intune に登録されているデバイスで使用されるカスタム ランチャーです。 Android デバイス ポリシー アプリにアクセスしたり、ユーザーを Android デバイス ポリシー アプリに案内したりして、サポートとデバッグを行うことができます。 この起動機能は、デバイスが登録され、マネージド ホーム スクリーンにロックされているときに使用できます。 この機能を使用するために追加のインストールは必要ありません。

#### <a name="outlook-protection-settings-for-ios-and-android-devices---3212619---"></a>iOS デバイスと Android デバイスの Outlook 保護設定<!-- 3212619 -->
デバイスを登録しなくても、シンプルな Intune 管理者コントロールを利用し、iOS と Android を対象に Outlook の一般アプリ設定とデータ保護設定の両方を構成できるようになりました。 一般的なアプリ構成設定からは、登録したデバイスで iOS 向け Outlook か Android 向け Outlook を管理するときに管理者が有効にできるものと同じような設定が与えられます。 Outlook 設定の詳細は、[iOS と Android 用 Outlook のアプリ構成設定の展開](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune)に関する記事をご覧ください。

### <a name="device-configuration"></a>デバイス構成

#### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910-eeready---idstaged---"></a>Windows 10 デバイス構成プロファイルを作成するときは "適用規則" を使用する <!-- 2549910 eeready   idstaged -->

Windows 10 デバイス構成プロファイルを作成します ( **[デバイスの構成]** 、 **[プロファイル]** 、 **[プロファイルの作成]** の順に選択し、プラットフォームに **[Windows 10]** を選択し、 **[適用規則]** を選択します)。 今回の更新で、**適用規則**を作成し、プロファイルが特定のエディションまたは特定のバージョンにのみ適用されるようにすることができます。 たとえば、いくつかの BitLocker 設定を有効にするプロファイルを作成します。 プロファイルを追加したら、適用規則を使用して Windows 10 Enterprise を実行しているデバイスにのみプロファイルを適用します。

適用規則を追加するには、「[適用規則](../configuration/device-profile-create.md#applicability-rules)」を参照してください。

適用対象:Windows 10 以降

#### <a name="use-tokens-to-add-device-specific-information-in-custom-profiles-for-ios-and-macos-devices---3330008----"></a>トークンを利用し、iOS デバイスと macOS デバイス向けのカスタム プロファイルでデバイス固有の情報を追加します<!-- 3330008  -->
iOS デバイスと macOS デバイスでカスタム プロファイルを利用し、Intune には組み込まれていない設定や機能を構成できます ( **[デバイス構成]** 、 **[プロファイル]** 、 **[プロファイルの作成]** の順に選択し、プラットフォームに **[iOS]** または **[macOS]** を選択し、プロファイルの種類に **[カスタム]** を選択します)。 今回の更新では、トークンを `.mobileconfig` ファイルに追加し、デバイス固有の情報を追加できます。 たとえば、デバイスのシリアル番号を表示する目的で構成ファイルに `Serial Number: {{serialnumber}}` を追加できます。

カスタム プロファイルを作成するには、「[iOS カスタム設定](../configuration/custom-settings-ios.md)」または「[macOS カスタム設定](../configuration/custom-settings-macos.md)」を参照してください。

適用対象:
- iOS
- macOS

#### <a name="new-configuration-designer-when-creating-an-oemconfig-profile-for-android-enterprise---3712769-----"></a>Android Enterprise 向けに OEMConfig プロファイルを作成するときの新しい構成デザイナー<!-- 3712769   -->
Intune では、OEMConfig アプリを使用するデバイス構成プロファイルを作成できます ([デバイス構成]、[プロファイル]、[プロファイルの作成] の順に選択し、プラットフォームに [Android Enterprise] を選択し、プロファイルの種類に [OEMConfig] を選択します)。 これを行うと、JSON エディターが開き、テンプレートと値を変更できます。 

今回の更新には、使い勝手が改善された構成デザイナーが含まれています。タイトルや説明など、アプリに組み込まれた詳細が表示されます。 JSON エディターも引き続き使用できます。構成デザイナーで行ったすべての変更が表示されます。

現在の設定を確認するには、「[OEMConfig で Android Enterprise デバイスを使用し、管理する](../configuration/android-oem-configuration-overview.md)」を参照してください。

適用対象:Android エンタープライズ

#### <a name="updated-ui-for-configuring-windows-hello---4089576--------------"></a>Windows Hello を構成する目的で更新された UI<!-- 4089576            -->
[Windows Hello for Business を使用するように Intune を構成する](../protect/windows-hello.md)コンソールを更新しました。 構成設定はすべて、Windows Hello のサポートを有効にしたコンソールの同じウィンドウで利用できるようになりました。

#### <a name="intune-powershell-sdk---4924113---"></a>Intune PowerShell SDK<!-- 4924113 --> 
Microsoft Graph 経由で Intune API のサポートを提供する Intune PowerShell SDK がバージョン 6.1907.1.0 に更新されました。 SDK で以下がサポートされるようになりました。
- Azure Automation と連動します。
- アプリ専用の認証読み取り操作をサポートします。 
- わかりやすく省略した名前を別名としてサポートします。
- PowerShell の名前付け規則に準拠します。 具体的には、`PSCredential` パラメーター (`Connect-MSGraph` コマンドレット) の名前が `Credential` に変更されました。
- `Invoke-MSGraphRequest` コマンドレットの使用時、`Content-Type` ヘッダーの値を手動で指定できるようになりました。

詳細は、「[PowerShell SDK for Microsoft Intune Graph API](https://www.powershellgallery.com/packages/Microsoft.Graph.Intune)」を参照してください。


### <a name="device-enrollment"></a>デバイスの登録

#### <a name="updates-for-enrollment-restrictions---2871968---"></a>登録制限の更新<!-- 2871968 -->
Android Enterprise の仕事用プロファイルが既定で許可されるように、新しいテナントの登録制限が更新されました。 既存のテナントは変更の萍郷を受けません。 Android Enterprise の仕事用プロファイルを使用するには、[Managed Google Play アカウントに Intune アカウントを接続する](../enrollment/connect-intune-android-enterprise.md)必要があります。

#### <a name="ui-updates-for-apple-enrollment-and-enrollment-restrictions--4089575-4089579----"></a>Apple 登録と登録制限の UI 更新<!--4089575, 4089579  -->
次の両方のプロセスでウィザードスタイルのユーザー インターフェイスが使用されます。
- Apple デバイス登録。 詳細は、「[Apple の Device Enrollment Program を使用して iOS デバイスを自動登録する](../enrollment/device-enrollment-program-enroll-ios.md)」を参照してください。
- 登録制限の作成。 詳細は、「[登録制限を設定する](../enrollment/enrollment-restrictions-set.md)」を参照してください。

#### <a name="handling-pre-configuration-of-corporate-device-identifiers-for-android-q-devices---4711509--idmiss---"></a>Android Q デバイスの会社デバイス ID の事前構成を処理する<!-- 4711509  idmiss -->
Google は Android Q (v10) で、レガシ マネージド (デバイス管理者) Android デバイスの MDM エージェントでデバイス ID 情報を収集する機能を削除しました。  Intune には、デバイスに会社所有のタグを自動的に付ける目的で、IT 管理者が[デバイス シリアル番号または IMEI の一覧を事前構成](../enrollment/corporate-identifiers-add.md#identify-corporate-owned-devices-with-imei-or-serial-number)できる機能が与えられています。 この機能は、デバイス管理者によって管理される Android Q デバイスでは作動しません。  デバイスのシリアル番号または IMEI に関係なく、Intune 登録中、デバイスは常に個人所有として見なされます。  登録後、会社に所有権を手動で切り替えることができます。  これは新しい登録のみに関係します。登録済みのデバイスは影響を受けません。  仕事用プロファイルで管理される Android デバイスはこの変更の影響を受けません。今後も今までどおり動作します。  また、デバイス管理者として登録されている Android Q デバイスでは、Intune コンソールでシリアル番号または IMEI をデバイス プロパティとして報告できなくなります。

#### <a name="icons-have-changed-for-android-enterprise-enrollments-work-profile-dedicated-devices-and-fully-managed-devices---4977730---"></a>Android Enterprise 登録のアイコンが変更されました (仕事用プロファイル、専用デバイス、完全に管理されるデバイス)。<!-- 4977730 -->
Android Enterprise 登録プロファイルのアイコンが変更されました。 新しいアイコンを見るには、 **[Intune]** 、 **[登録]** 、 **[Android 登録]** の順に進み、 **[登録プロファイル]** の下を探してください。


#### <a name="windows-diagnostic-data-collection-change---4113859---"></a>Windows 診断データ収集の変更<!-- 4113859 -->
Windows 10 バージョン 1903 以降を実行するデバイスに関して、診断データ収集の既定値が変更されました。 Windows 10 1903 より、診断データ収集は既定で有効になります。 Windows 診断データは、Windows デバイスから取得される、デバイスと、Windows と関連ソフトウェアの性能に関する極めて重要な技術データです。 詳しくは、「[組織内の Windows 診断データの構成](https://docs.microsoft.com/windows/privacy/configure-windows-diagnostic-data-in-your-organization)」をご覧ください。 AutoPilot デバイスでも、[System/AllowTelemetry](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-allowtelemetry) で AutoPilot プロファイルに完全以外が設定されていない限り、"完全な" テレメトリが選択されます。

### <a name="device-management"></a>デバイス管理

#### <a name="improve-device-location---3855417----"></a>デバイスの位置検索機能の向上<!-- 3855417  -->
**[デバイスを検索する]** アクションを使用し、デバイスの正確な座標にズームインできます。 紛失した iOS デバイスの位置を見つける方法については、[紛失した iOS デバイスを見つける方法](../remote-actions/device-locate.md)に関するページを参照してください。

### <a name="device-security"></a>デバイス セキュリティ

#### <a name="advanced-settings-for-windows-defender-firewall--public-preview----1311949-------"></a>Windows Defender ファイアウォールの詳細設定 (パブリック プレビュー)<!--  1311949     -->  
Windows 10 のエンドポイント保護として[デバイス構成プロファイルの一部としてカスタム ファイアウォール規則](../protect/endpoint-protection-configure.md#add-custom-firewall-rules-for-windows-10-devices)を管理するには、Intune を使用します。 規則では、アプリケーション、ネットワーク、アドレス、ポートに対する受信と送信の動作を指定できます。 

#### <a name="updated-ui-for-managing-security-baselines---4091125-------"></a>セキュリティ ベースラインを管理するための UI が更新されました<!-- 4091125     -->
Intune コンソールでセキュリティ ベースラインを[作成し、編集するエクスペリエンス](../protect/security-baselines.md#create-the-profile) を更新しました。 変更内容:

ウィザードスタイルの形式がシングル ブレードに圧縮され、わかりやすくなりました。 1 つのブレードに収まるようになりました。 ブレードがスプロールしていると IT の専門家は複数の個別ウィンドウにドリルダウンしなければなりませんが、この新しい設計ではそれがなくなりました。  
作成または編集の間に割り当てを作成できるようになりました。後で割り当てベースラインに戻る必要がありません。 設定のまとめを追加しました。新しいベースラインを作成する前に、あるいは既存のベースラインを編集するときに表示できます。 編集時、編集中のプロパティの 1 カテゴリ内に設定されているアイテムのみがまとめに一覧表示されます。

<!-- ########################## -->

## <a name="week-of-july-15-2019"></a>2019 年 7 月 15 日の週 

### <a name="app-management"></a>アプリ管理

#### <a name="managed-home-screen-and-managed-settings-icons---4918107---"></a>マネージド ホーム スクリーンとマネージド設定のアイコン<!-- 4918107 -->
[マネージド ホーム スクリーン] アプリ アイコンと **[マネージド設定]** のアイコンが更新されました。 [マネージド ホーム スクリーン] アプリは、Android Enterprise (AE) 専用デバイスとして Intune に登録され、マルチアプリ キオスク モードで実行されるデバイスでのみ使用されます。 [マネージド ホーム スクリーン] アプリの詳細は、「[Android Enterprise 用 Microsoft Managed Home Screen アプリを構成する](../apps/app-configuration-managed-home-screen-app.md)」を参照してください。

#### <a name="android-device-policy-on-android-enterprise-dedicated-devices---4918136---"></a>Android Enterprise 専用デバイスの Android デバイス ポリシー<!-- 4918136 -->
[マネージド ホーム スクリーン] アプリのデバッグ画面から Android デバイス ポリシー アプリケーションにアクセスできます。 [マネージド ホーム スクリーン] アプリは、Android Enterprise (AE) 専用デバイスとして Intune に登録され、マルチアプリ キオスク モードで実行されるデバイスでのみ使用されます。 詳細は、「[Android Enterprise 用 Microsoft Managed Home Screen アプリを構成する](../apps/app-configuration-managed-home-screen-app.md)」を参照してください。

#### <a name="ios-company-portal-updates---3902931---"></a>iOS ポータル サイトの更新<!-- 3902931 -->
iOS アプリ管理プロンプトの会社名が現在の "i.manage.microsoft.com" テキストに取って代わります。 たとえば、ユーザーがポータル サイトから iOS アプリをインストールしようとすると、あるいはユーザーがアプリの管理を許可すると、"i.manage.microsoft.com" ではなく、会社名がユーザーに表示されます。 これは、今後数日間にわたってすべてのお客様にロールアウトされます。

### <a name="device-configuration"></a>デバイス構成

#### <a name="manage-filevault-for-macos----3858502--4557986--1210104----"></a>macOS 向け FileVault の管理<!--  3858502 + 4557986 + 1210104  -->
Intune を使用し、[macOS デバイスの FileVault キー暗号化を管理](../protect/encrypt-devices.md)できます。 デバイスを暗号化するには、エンドポイント保護デバイス構成プロファイルを使用します。

FileVault のサポートには、暗号化されていないデバイスの暗号化、デバイスの個人用回復キーのエスクロー、個人用暗号化キーの自動または手動ローテーション、会社デバイスのキー取得が含まれます。 エンド ユーザーはポータル サイト Web サイトを使用し、暗号化している自分のデバイスの個人用回復キーを取得することもできます。

また、デバイス暗号化に関するすべての詳細を 1 か所で表示できるように、BitLocker に関する情報に加えて、[FileVault に関する情報](../protect/encryption-monitor.md)が含まれるよう、暗号化レポートを拡張しました。

### <a name="device-enrollment"></a>デバイスの登録

#### <a name="windows-autopilot-reset-removes-the-devices-primary-user---4156123---"></a>Windows AutoPilot リセットを実行すると、デバイスのプライマリ ユーザーが削除されます。<!-- 4156123 -->
AutoPilot リセットがデバイスで使用されると、デバイスのプライマリ ユーザーが削除されます。 リセット後に初めてサインインしたユーザーがプライマリ ユーザーとして設定されます。 この機能は、今後数日間にわたってすべてのお客様にロールアウトされます。

## <a name="week-of-july-8-2019"></a>2019 年 7 月 8 日の週

### <a name="new-office-windows-and-onedrive-settings-in-windows-10-administrative-templates----3510695---"></a>Windows 10 管理用テンプレートの新しい Office、Windows、OneDrive の設定 <!-- 3510695 -->

オンプレミス グループ ポリシー管理を模倣する管理用テンプレートを Intune で作成できます ( **[デバイス管理]** 、 **[プロファイル]** 、 **[プロファイルの作成]** の順に選択し、プラットフォームに **[Windows 10 以降]** を選択し、プロファイルの種類に **[管理用テンプレート]** を選択します)。

この更新には、テンプレートに追加できる Office 設定、Windows 設定、OneDrive 設定が含まれています。 このような新しい設定を利用することで、100% クラウドベースの 2500 を超える設定を構成できるようになりました。

この機能の詳細については、[Windows 10 テンプレートを使用し、Intune でグループ ポリシー設定を構成する方法](../configuration/administrative-templates-windows.md)に関するページを参照してください。

適用対象:Windows 10 以降

## <a name="week-of-july-1-2019"></a>2019 年 7 月 1 日の週 

### <a name="app-management"></a>アプリ管理

#### <a name="aad-and-app-on-android-enterprise-devices---3574267---"></a>Android Enterprise デバイスの AAD と APP<!-- 3574267 -->
完全管理の Android Enterprise デバイスをオンボードするとき、ユーザーは新しい (工場出荷時の状態の) デバイスの初回セットアップ中、Azure Active Directory (AAD) に登録するようになりました。 以前は、フル マネージド デバイスの場合、セットアップの完了後、ユーザーは手動で Microsoft Intune アプリを起動し、AAD 登録を開始する必要がありました。 今後は、初回セットアップ後、ユーザーがデバイスのホーム ページを開くと、デバイスの登録も完了しています。

AAD 更新プログラムに加え、Intune アプリ保護ポリシー (APP) が完全管理 Android Enterprise デバイスでサポートされるようになりました。 ロールアウト次第、この機能は利用できるようになります。詳細は、「[Intune で managed Google Play アプリを Android エンタープライズ デバイスに追加する](../apps/apps-add-android-for-work.md)」を参照してください。

## <a name="week-of-june-24-2019"></a>2019 年 6 月 24 日の週

### <a name="app-management"></a>アプリ管理

#### <a name="configure-which-browser-is-allowed-to-link-to-organization-data---3145939---"></a>組織データへのリンクを許可するブラウザーを構成する<!-- 3145939 -->
Android と iOS デバイスで Intune App Protection ポリシー (APP) を使用すると、組織の Web リンクを Intune Managed Browser または Microsoft Edge 以外の特定のブラウザーに転送できるようになりました。  アプリの詳細については、「[アプリ保護ポリシーとは](../apps/app-protection-policy.md)」を参照してください。

#### <a name="all-apps-page-identifies-onlineoffline-microsoft-store-for-business-apps--4089647---"></a>[すべてのアプリ] ページでは、オンライン/オフラインの Microsoft Store for Business アプリが識別されます。<!--4089647 -->
**[すべてのアプリ]** ページには、Microsoft Store for Business (MSFB) アプリをオンラインまたはオフライン アプリとして識別するためのラベル付けが含まれるようになりました。 各 MSFB アプリには、 **[オンライン]** か **[オフライン]** の接尾辞が含まれるようになりました。 [アプリの詳細] ページには、**ライセンスの種類**と**デバイス コンテキスト インストールのサポート** (オフラインの認可アプリのみ) に関する情報も含まれています。

#### <a name="company-portal-app-on-windows-shared-devices--4393553---"></a>Windows 共有デバイスのポータル サイト アプリ<!--4393553 -->
ユーザーは Windows 共有デバイスでポータル サイト アプリにアクセスできるようになりました。 エンドユーザーには、デバイス タイルで**共有**ラベルが表示されます。 これは、Windows ポータルサイト アプリ バージョン 10.3.45609.0 以降に適用されます。

#### <a name="view-all-installed-apps-from-new-company-portal-web-page---4224326---"></a>新しいポータル サイト Web ページにインストールされたすべてのアプリが表示<!-- 4224326 -->
ポータル サイト Web サイトの新しい **[インストール済みアプリ]** ページに、ユーザーのデバイスにインストールされているすべてのマネージド アプリ (必須および使用可能の両方) が一覧表示されます。 割り当ての種類だけでなく、アプリの発行元、発行日、現在のインストール状態も表示されます。 ユーザーに対して必須または使用可能とされているアプリがない場合は、会社アプリがインストールされていないというメッセージが表示されます。 Web 上で新しいページを参照するには、[ポータル サイト Web サイト](https://portal.manage.microsoft.com)に移動して、 **[インストール済みアプリ]** をクリックします。  

#### <a name="new-view-lets-app-users-see-all-managed-apps-installed-on-device---2352913---"></a>新しいビューでデバイスにインストールされているすべてのマネージド アプリが表示可能に<!-- 2352913 -->  
Windows 用ポータル サイトのアプリに、ユーザーのデバイスにインストールされているすべてのマネージド アプリ (必須および使用可能の両方) が一覧表示されるようになりました。 ユーザーは、試行した、および保留中のアプリのインストールと、それらの現在の状態も確認できます。 ユーザーに対して必須または使用可能とされているアプリがない場合は、アプリがインストールされていないというメッセージが表示されます。 新しいビューを表示するには、ポータル サイトのナビゲーション ウィンドウに移動し、 **[アプリ]**  >  **[インストール済みアプリ]** の順に選択します。

### <a name="device-configuration"></a>デバイス構成

#### <a name="configure-settings-for-kernel-extensions-on-macos-devices---2043024---"></a>macOS デバイスのカーネル拡張機能の設定を構成する<!-- 2043024 -->
macOS デバイスで、デバイス構成プロファイルを作成できます ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]** > プラットフォームに **[macOS]** を選択します)。 この更新プログラムには、デバイスのカーネル拡張機能を構成して使用することができる新しい設定のグループが含まれます。 特定の拡張機能を追加したり、特定のパートナーまたは開発者からの拡張機能をすべて許可したりすることができます。

この機能の詳細については、[カーネル拡張機能の概要](../configuration/kernel-extensions-overview-macos.md)と[カーネル拡張機能の設定](../configuration/kernel-extensions-settings-macos.md)に関するページを参照してください。

適用対象: macOS 10.13.2 以降

#### <a name="apps-from-the-store-only-setting-for-windows-10-devices-includes-more-configuration-options---2697002---"></a>Windows 10 デバイスのストアのアプリのみ設定に含まれるその他の構成オプション<!-- 2697002 -->
ユーザーが Windows アプリ ストアからのみアプリをインストールするように、Windows デバイス用のデバイス制限プロファイルを作成するときに **[Apps from the store only]** (ストアのアプリのみ) 設定を使用することがでます ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  >  プラットフォームに **[Windows 10 以降]** > プロファイルの種類に **[デバイスの制限]** )。 この更新では、この設定はより多くのオプションをサポートするように拡張されています。

新しい設定を確認するには、[機能を許可または制限する Windows 10 (以降) デバイス設定](../configuration/device-restrictions-windows-10.md#app-store)に関するページを参照してください。

適用対象:Windows 10 以降

#### <a name="deploy-multiple-zebra-mobility-extensions-device-profiles-to-a-device-same-user-group-or-same-devices-group---4089955---"></a>複数の Zebra モビリティ拡張機能デバイス プロファイルを 1 つのデバイス、同じユーザー グループ、または同じデバイス グループに展開する<!-- 4089955 -->
Intune では、デバイス構成プロファイル内で Zebra モビリティ拡張機能 (MX) を使用し、Intune に組み込まれていない Zebra デバイス向けに設定をカスタマイズできます。 現在、1 つのデバイスに 1 つのプロファイルを展開できます。 今回の更新では、以下に複数のプロファイルを展開できます。
- 同じユーザー グループ
- 同じデバイス グループ
- 1 つのデバイス

「[Microsoft Intune で Zebra モビリティ拡張機能を備えた Zebra デバイスを使用および管理する](../configuration/android-zebra-mx-overview.md)」には、Intune で MX を使用する方法が説明されています。

適用対象:Android

#### <a name="some-kiosk-settings-on-ios-devices-are-set-using-block-replacing-allow---4404075----"></a>iOS デバイス上の一部のキオスク設定は、[許可] の代わりに [ブロック] を使用して設定されています。<!-- 4404075  -->
iOS デバイス上にデバイス制限プロファイルを作成した場合は ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  > プラットフォームに **[iOS]** > プロファイルの種類に **[デバイスの制限]** > **[キオスク]** )、 **[自動ロック]** 、 **[着信音スイッチ]** 、 **[画面の回転]** 、 **[画面スリープ ボタン]** 、および **[音量ボタン]** を設定します。

今回の更新で、値は **[ブロック]** (機能をブロックする) と **[未構成]** (機能を許可する) になりました。 設定を確認するには、[機能を許可または制限する iOS デバイスの設定](../configuration/device-restrictions-ios.md#kiosk)に関するページを参照してください。

適用対象: iOS

#### <a name="use-face-id-for-password-authentication-on-ios-devices---4490704---"></a>iOS デバイスのパスワード認証に Face ID を使用する<!-- 4490704 -->
iOS デバイス用のデバイス制限プロファイルを作成するときは、パスワードに指紋を使用できます。 今回の更新では、指紋のパスワード設定でも顔認識が可能になりました ( **[デバイス構成]** 、 **[プロファイル]** 、 **[プロファイルの作成]** の順に選択し、プラットフォームに **[iOS]** を選択し、プロファイルの種類に **[デバイスの制限]** を選択し、 **[パスワード]** を選択します)。 その結果、次の設定が変更されています。

- **[指紋によるロック解除]** は **[Touch ID と Face ID のロック解除]** になりました。
- **[指紋の変更 (管理モードのみ)]** は **[Touch ID と Face ID の変更 (監視モードのみ)]** になりました。

Face ID は iOS 11.0 以降で使用できます。 設定を確認するには、「[Intune を使用して機能を許可または制限するように iOS デバイスを設定する](../configuration/device-restrictions-ios.md#password)」を参照してください。

適用対象: iOS

#### <a name="restricting-gaming-and-app-store-features-on-ios-devices-is-now-dependent-on-ratings-region---4593948---"></a>iOS デバイスでのゲームやアプリ ストアの機能制限が年齢区分の地域によって異なるようになりました<!-- 4593948 -->
iOS デバイスでは、ゲーム、アプリ ストア、およびドキュメントの表示に関連する機能を許可または制限できます ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  > プラットフォームに **[iOS]** > プロファイルの種類に **[デバイスの制限]** > **[アプリ ストア、ドキュメント表示、ゲーム]** )。 米国などの年齢区分の地域を選択することもできます。

今回の更新では、 **[アプリ]** 機能が **[年齢区分の地域]** の子に移動され、 **[年齢区分の地域]** に依存するようになりました。 設定を確認するには、「[Intune を使用して機能を許可または制限するように iOS デバイスを設定する](../configuration/device-restrictions-ios.md#app-store-doc-viewing-gaming)」を参照してください。

適用対象: iOS

### <a name="device-enrollment"></a>デバイスの登録

#### <a name="windows-autopilot-support-for-hybrid-azure-ad-join---4809146--"></a>Hybrid Azure AD Join の Windows AutoPilot サポート<!-- 4809146-->
既存デバイスの Windows AutoPilot で、(既存の Azure AD Join サポートに加え) Hybrid Azure AD Join がサポートされるようになりました。 Windows 10 バージョン 1809 以降のデバイスに適用されます。 詳細は、[既存のデバイスの Windows AutoPilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/existing-devices) に関するページを参照してください。

### <a name="device-management"></a>デバイス管理

#### <a name="see-the-security-patch-level-for-android-devices---4461911---"></a>Android デバイス用のセキュリティ パッチ レベルを確認する<!-- 4461911 -->
Android デバイスのセキュリティ パッチ レベルを確認できるようになりました。 これを行うには、 **[Intune]** 、 **[デバイス]** 、 **[すべてのデバイス]** の順に進んでデバイスを選択し、 **[ハードウェア]** を選択します。
パッチ レベルの一覧は **[オペレーティング システム]** セクションにあります。

#### <a name="assign-scope-tags-to-all-managed-devices-in-a-security-group---3173810---"></a>セキュリティ グループ内のすべてのマネージド デバイスにスコープ タグを割り当てる<!-- 3173810 -->
スコープ タグをセキュリティ グループに割り当てられるようになりました。セキュリティ グループのすべてのデバイスもそのスコープ タグに関連付けられます。 これらのグループ内のすべてのデバイスにもスコープ タグが割り当てられます。 この機能で設定されたスコープ タグによって、現在のデバイス スコープ タグ フローで設定されたスコープ タグは上書きされる予定です。 詳細は、[分散 IT に RBAC とスコープ タグを使用する方法](scope-tags.md)に関するページを参照してください。

### <a name="device-security"></a>デバイス セキュリティ

#### <a name="use-keyword-search-with-security-baselines------"></a>セキュリティ ベースラインでキーワード検索を使用する<!--  -->
[セキュリティ ベースライン プロファイル](../protect/security-baselines.md#create-the-profile)を作成または編集するとき、新しい *[検索]* バーにキーワードを指定し、利用できる設定グループを検索基準に含まれるグループに絞り込むことができるようになりました。

#### <a name="the-security-baselines-feature-is-now-generally-available---3785395---"></a>セキュリティ ベースライン機能の一般提供が開始されました<!-- 3785395 -->
**セキュリティ ベースライン**機能のプレビューが終わり、一般提供 (GA) になりました。  これは、機能が運用環境で使用できる状態であることを意味します。 ただし、個々のベースライン テンプレートはプレビューのままであり、独自のスケジュールに基づいて評価され、GA リリースされます。

#### <a name="the-mdm-security-baseline-template-is-now-generally-available---3794072-4217151--3534649---"></a>MDM セキュリティ ベースライン テンプレートが一般提供になりました<!-- 3794072, 4217151,  3534649 -->
MDM セキュリティ ベースラインのプレビューが終わり、一般提供 (GA) になりました。 GA テンプレートは、**2019 年 5 月の MDM セキュリティ ベースライン**として識別されています。  これは新しいテンプレートであり、前のバージョンからのアップグレードではありません。  新しいテンプレートであるため、[それに含まれる設定](../protect/security-baseline-settings-mdm.md)を確認する必要があり、その後、新しいプロファイルを作成し、テンプレートをデバイスに配備する必要があります。 その他のセキュリティ ベースライン テンプレートはプレビューのままでも構いません。 利用できるベースラインの一覧は、「[使用可能なセキュリティ ベースライン](../protect/security-baselines.md#available-security-baselines)」を参照してください。  

新しいテンプレートであるだけではなく、*2019 年 5 月の MDM セキュリティ ベースライン* テンプレートには、"開発中" 記事で最近告知した 2 つの設定が含まれています。  
- Above Lock (ロックの上から):ロックされた画面から音声でアプリを起動します  
- DeviceGuard:仮想化ベースのセキュリティ (VBS) をデバイスの次回起動で使用します  

*2019 年 5 月の MDM セキュリティ ベースライン*には、新しい設定がさらにいくつか追加されています。また、削除された設定もあり、設定の既定値が見直されたものもあります。 プレビューから GA に変更された機能の詳しい一覧は、**新しいテンプレートで変更された箇所**に関するページを参照してください。

#### <a name="security-baseline-versioning---3194322---"></a>セキュリティ ベースラインのバージョン管理<!-- 3194322 -->
Intune のセキュリティ ベースラインはバージョン管理に対応しています。 バージョン管理に対応していることで、セキュリティ ベースラインの新しいバージョンがリリースされるたびに、新しいベースラインを一から作り直して配備しなくても、最新のベースライン バージョンを使用するように、既存のセキュリティ ベースライン プロファイルを更新できます。 また、Intune コンソールでは、ベースラインが使用される個別プロファイルの数、プロファイルで使用されるさまざまなベースライン バージョンの数、特定のセキュリティ ベースラインの最新リリースの日付など、各ベースラインに関する情報を表示できます。  詳細は、「**セキュリティ ベースライン**」を参照してください。

#### <a name="the-use-security-keys-for-sign-in-setting-has-moved---4501151---"></a>[サインインのセキュリティ キーを使用] 設定が移動しました<!-- 4501151 -->
**サインインのセキュリティ キーを使用**という名称の ID 保護用デバイス構成設定は、「*Windows Hello for Business の構成*」の下位設定から削除されました。 Windows Hello for Business の使用を有効にしなくても、常に使用できる最上位の設定になりました。 詳細は、「[ID 保護](../protect/identity-protection-windows-settings.md)」を参照してください。

### <a name="role-based-access-control"></a>ロールベースのアクセス制御

#### <a name="new-permissions-for-assigned-group-admins---4504437-----"></a>割り当てられたグループ管理者の新しいアクセス許可<!-- 4504437   -->
Intune の組み込み学校管理者ロールに管理対象アプリに対する作成、読み取り、更新、削除 (CRUD) のアクセス許可が付与されるようになりました。 今回の更新は、教育機関向け Intune のグループ管理者として任命されたとき、[自分に与えられているすべての既存のアクセス許可](https://docs.microsoft.com/intune-education/group-admin-delegate#group-admin-permissions)と共に、iOS MDM プッシュ通知証明書、iOS MDM サーバー トークン、iOS VPP トークンを作成、表示、更新、削除できるようになりました。 これらのアクションを実行するには、 **[テナント設定]** 、 **[iOS デバイス管理]** の順に進みます。  

#### <a name="applications-can-use-the-graph-api-to-call-read-operations-without-user-credentials---4655885---"></a>アプリケーションでは Graph API を利用し、ユーザー資格情報なしで読み取り操作を呼び出すことができます。<!-- 4655885 -->
アプリケーションでは、ユーザー資格情報がなくても、アプリの ID で Intune Graph API 読み取り操作を呼び出すことができます。 Microsoft Graph API for Intune にアクセスする方法については、「[Microsoft Graph での Intune の操作](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0)」を参照してください。

#### <a name="apply-scope-tags-to-microsoft-store-for-business-apps---4392555---"></a>Microsoft Store for Business アプリにスコープ タグを適用する<!-- 4392555 -->
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

#### <a name="new-sample-apps-showing-intune-sdk-integration-available-on-github---2653471---"></a>GitHub で入手できる Intune SDK 統合を示す新しいサンプル アプリ<!-- 2653471 -->
msintuneappsdk GitHub アカウントで、iOS (Swift)、Android、Xamarin.iOS、Xamarin Forms、Xamarin.Android 向けの新しいサンプル アプリケーションが追加されました。 これらのアプリの目的は、既存のドキュメントを補完し、Intune APP SDK をお客様のモバイル アプリに統合する方法のデモを提供することです。 Intune SDK の追加のガイダンスが必要なアプリ開発者の場合は、次のリンク先のサンプルを参照してください。
- [Chatr](https://github.com/msintuneappsdk/Chatr-Sample-Intune-iOS-App) - 仲介型認証に Azure Active Directory 認証ライブラリ (ADAL) を使用するネイティブ iOS (Swift) インスタント メッセージング アプリ。
- [Taskr](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Android-App) - 仲介型認証に ADAL を使用するネイティブの Android todo リスト アプリ。
- [Taskr](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Xamarin-Android-Apps) - 仲介型認証に ADAL を使用する Xamarin.Android の todo リスト アプリ。このリポジトリには Xamarin.Forms アプリもあります。
- [Xamarin.iOS サンプル アプリ](https://github.com/msintuneappsdk/sample-intune-xamarin-ios) - 必要最低限の Xamarin.iOS サンプル アプリ。

## <a name="week-of-may-27-2019"></a>2019 年 5 月 27 日の週

### <a name="app-management"></a>アプリ管理

#### <a name="reporting-for-potentially-harmful-apps-on-android-devices---4223162---"></a>Android デバイス上の有害な可能性のあるアプリについてのレポート<!-- 4223162 -->
Intune により、Android デバイス上の有害な可能性のあるアプリに関する追加レポート情報が提供されるようになりました。 

## <a name="week-of-may-20-2019"></a>2019 年 5 月 20 日の週

### <a name="app-management"></a>アプリ管理

#### <a name="windows-company-portal-app---3316993---"></a>Microsoft ポータル サイト アプリ<!-- 3316993 -->
Windows ポータル サイト アプリには、 **[デバイス]** とラベル付けされた新しいページが設けられました。 **[デバイス]** ページには、登録されているデバイスのすべてのエンド ユーザーが表示されます。 バージョン 10.3.4291.0 以降を使用している場合、ユーザーはポータル サイト上でこの変更を確認できます。 ポータル サイトの構成方法については、「[Microsoft Intune ポータル サイト アプリを構成する方法](../apps/company-portal-app.md)」をご覧ください。

### <a name="device-enrollment"></a>デバイスの登録

#### <a name="autopilot-device-orderid-attribute-name-changed-to-group-tag----4659453---"></a>Autopilot デバイスの OrderID 属性の名前がグループ タグに変更された <!-- 4659453 -->

直感的にわかりやすくするために、Autopilot デバイス上での **OrderID** 属性の名前が、**グループ タグ**に変更されました。 Autopilot デバイス情報をアップロードするために CSV を使用する場合は、OrderID ではなく、列ヘッダーとしてグループ タグを使用する必要があります。  

## <a name="week-of-may-13-2019"></a>2019 年 5 月 13 日の週

### <a name="app-management"></a>アプリ管理

#### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation---1927359----"></a>Intune ポリシーによって認証方法とポータル サイト アプリのインストールを更新する<!-- 1927359  -->
Apple の会社用デバイスの登録方法のいずれかを使ってセットアップ アシスタント経由で既に登録されているデバイスの場合、Intune では、特定のデバイスで App Store からインストールされる場合に、ポータル サイト アプリがサポートされなくなります。 この変更は、登録時に Apple セットアップ アシスタントで認証を行う場合にのみ関係があります。 また、この変更は、以下から登録される iOS デバイスのみに影響します。  
* Apple Configurator

* Apple Business Manager

* Apple School Manager

* Apple Device Enrollment Program (DEP)

App Store からポータル サイト アプリをインストールした後、これらのデバイスを登録しようとすると、エラーが発生します。 登録時に Intune によって自動的にプッシュされた場合、これらのデバイスではポータル サイトだけを使用することが期待されます。 Azure portal での Intune の登録プロファイルは、デバイスの認証方法およびポータル サイト アプリを受信するかどうかを指定できるように更新されます。 DEP デバイス ユーザーがポータル サイトを使用するようにしたい場合は、登録プロファイルでユーザー設定を指定する必要があります。 

さらに、iOS ポータル サイト内の **[デバイスの特定]** 画面は、削除される予定です。 そのため、条件付きアクセスの有効化または業務用アプリのデプロイを行う管理者は、DEP 登録プロファイルを更新する必要があります。 この要件は、DEP 登録が設定アシスタントによって認証された場合にのみ、適用されます。 その場合、デバイス上にポータル サイトをプッシュする必要があります。 これを行うには、 **[Intune]**  >  **[デバイスの登録]**  >  **[Apple の登録]**  >  **[Enrollment Program トークン]** の順に選択し、1 つのトークンを選んで **[プロファイル]** から 1 つのプロファイルを選択し、 **[プロパティ]** から **[ポータル サイトのインストール]** を **[はい]** に設定します。

既に登録されている DEP デバイス上にポータル サイトをインストールするには、Intune 上で [クライアント アプリ] に移動し、アプリ構成ポリシーを利用してマネージド アプリとしてプッシュする必要があります。 

#### <a name="configure-how-end-users-update-a-line-of-business-lob-app-using-an-app-protection-policy---3568384---"></a>アプリ保護ポリシーを利用してエンド ユーザーが基幹業務 (LOB) アプリを更新する方法を構成する<!-- 3568384 -->
エンド ユーザーが基幹業務 (LOB) アプリの更新バージョンを取得できる場所を構成できるようになりました。 この機能がエンド ユーザーに対して表示されるのは **[アプリの最小バージョン]** 条件付き起動ダイアログであり、エンド ユーザーは最小バージョンの LOB アプリに更新することを求められます。 LOB アプリ保護ポリシー (APP) の一部として、これらの更新の詳細を提供する必要があります。 この機能は iOS および Android 上で使用できます。 iOS の場合、この機能ではアプリを統合する (または、ラッピング ツールを使用しラップする) ことが必要になります。その際に利用するのは、iOS 用の Intune SDK 10.0.7 以降です。 Android の場合、この機能では最新のポータル サイトが必要になります。 エンド ユーザーが LOB アプリを更新する方法を構成するには、キー `com.microsoft.intune.myappstore` を含むマネージド アプリ構成ポリシーをアプリに送信する必要があります。 送信される値により、エンド ユーザーがアプリをダウンロードするストアが定義されます。 アプリがポータル サイト経由で展開される場合、値は `CompanyPortal` である必要があります。 他のストアの場合は、完全な URL を入力する必要があります。

#### <a name="intune-management-extension-powershell-scripts---3734186----"></a>Intune 管理拡張機能の PowerShell スクリプト<!-- 3734186  -->
ユーザーの管理者特権を使用してデバイス上で実行するように、PowerShell スクリプトを構成できます。 詳しくは、「[Intune で Windows 10 デバイスに対して PowerShell スクリプトを使用する](../apps/intune-management-extension.md)」と、[Win32 アプリ管理](../apps/app-management.md)に関するページをご覧ください。

#### <a name="android-enterprise-app-management---4459905---"></a>Android Enterprise アプリの管理<!-- 4459905 -->
IT 管理者がより簡単に Android Enterprise 管理を構成および使用できるよう、Intune では 4 つの一般的な Android Enterprise 関連のアプリが Intune 管理コンソールに自動的に追加されます。 この 4 つの Android Enterprise アプリは次のアプリです。

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** - Android Enterprise フル マネージド シナリオで使用されます。
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** - 2 要素認証を使用している場合、アカウントへのサインインを支援します。
- **[Intune ポータル サイト](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** - アプリ保護ポリシー (APP) と Android Enterprise 仕事用プロファイルのシナリオで使用されます。
- [Managed Home Screen](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise) - Android Enterprise 専用またはキオスクのシナリオで使用されます。

以前は、IT 管理者はセットアップの一部として、手動でこれらのアプリを [Managed Google Play ストア](https://play.google.com/store/apps)で探して承認する必要がありました。 この変更により、以前の手動による手順は不要となり、お客様は Android Enterprise 管理をより簡単に素早く使用できるようになります。

管理者は Intune テナントを Managed Google Play に最初に接続したときに、これらの 4 つのアプリが自動的に Intune アプリ一覧に追加されていることを確認できます。 詳細については、[Managed Google Play アカウントへの Intune アカウントの接続](../enrollment/connect-intune-android-enterprise.md)に関するページを参照してください。 自分のテナントを既に接続済みであるか、Android Enterprise を既に使用済みのテナントの場合、管理者が行う必要のある処理はありません。 以上の 4 つのアプリは、2019 年 5 月のサービス ロールアウトの完了から 7 日以内に自動的に表示されます。

### <a name="device-configuration"></a>デバイス構成

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune---1533038---"></a>PFX Certificate Connector for Microsoft Intune の更新<!-- 1533038 -->
新しい要求の処理を停止するコネクタの原因である、既存の PFX 証明書の再処理が続行する問題に対処する、[Microsoft Intune の PFX 証明書コネクタ](../protect/certficates-pfx-configure.md#whats-new-for-connectors)の更新プログラムをリリースしました。

#### <a name="intune-security-tasks-for-defender-atp-in-public-preview---3208597---"></a>Defender ATP 用の Intune セキュリティ タスク (パブリック プレビュー)<!-- 3208597 -->
パブリック プレビューでは、Intune を使用して [Microsoft Defender Advanced Threat Protection (ATP) 用のセキュリティ タスクを管理できます](../protect/atp-manage-vulnerabilities.md)。 この ATP との統合によってリスク ベースの手法が追加され、エンドポイントの脆弱性や誤設定を検出し、優先度を付けて修復できるようになり、検出から軽減までにかかる時間が短縮されます。

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy---3617671---idstaged--"></a>Windows 10 デバイスのコンプライアンス ポリシーでの TPM チップセットのチェック<!-- 3617671   idstaged-->
Windows 10 以降のデバイスの多くには、トラステッド プラットフォーム モジュール (TPM) チップセットが含まれています。 この更新プログラムには、デバイスの TPM チップのバージョンを確認する新しいコンプライアンス設定が含まれています。

[Windows 10 以降のコンプライアンス ポリシー設定](../protect/compliance-policy-create-windows.md#device-security)で、この設定が説明されています。

適用対象:Windows 10 以降

#### <a name="prevent-end-users-from-modifying-their-personal-hotspot-and-disable-siri-server-logging-on-ios-devices---4097904-----"></a>エンド ユーザーによる個人用ホットスポットの変更を防止し、iOS デバイス上での Siri サーバーのログ記録を無効にする<!-- 4097904   -->  
iOS デバイス上にデバイスの制限プロファイルを作成します ( **[デバイスの構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  >  **[iOS]** (プラットフォーム) > **[デバイスの制限]** (プロファイルの種類))。 この更新プログラムには構成できる新しい設定が含まれています。

- **組み込みアプリ**:Siri コマンドに対するサーバー側のログ記録
- **ワイヤレス**:個人用ホットスポットのユーザー変更 (監視モードのみ)

これらの設定を確認するには、[iOS 用の組み込みのアプリ設定](../configuration/device-restrictions-ios.md#built-in-apps)と [iOS 用のワイヤレス設定](../configuration/device-restrictions-ios.md#wireless)に移動します。

iOS デバイス 12.2 以降に適用されます。

#### <a name="new-classroom-app-device-restriction-settings-for-macos-devices---4097905-----"></a>macOS デバイス用の新しい Classroom アプリ デバイス制限の設定<!-- 4097905   --> 
macOS デバイス用のデバイス構成プロファイルを作成できます ( **[デバイスの構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  >  **[macOS]** (プラットフォーム) > **[デバイスの制限]** (プロファイルの種類))。 この更新には、新しい教室アプリ設定、スクリーンショットをブロックするオプション、iCloud フォト ライブラリを無効にするオプションが含まれています。

現在の設定を確認するには、「[Intune を使用して機能を許可または制限するように macOS デバイスを設定する](../configuration/device-restrictions-macos.md)」を参照してください。

適用対象: macOS

#### <a name="the-ios-password-to-access-app-store-setting-is-renamed---4557891----"></a>iOS の [アプリ ストアにアクセスするためのパスワード] 設定の名前が変更される<!-- 4557891  -->
**[アプリ ストアにアクセスするためのパスワード]** 設定の名前が、 **[すべての購入に iTunes Store パスワードを要求します]** に変更されています ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  >  **[iOS]** (プラットフォーム) > **[デバイスの制限]** (プロファイルの種類) > **[アプリ ストア、ドキュメント表示、ゲーム] )** 。

使用可能な設定を確認するには、[[アプリ ストア、ドキュメントの表示、ゲーム] の iOS 設定](../configuration/device-restrictions-ios.md#app-store-doc-viewing-gaming)に移動します。

適用対象: iOS

#### <a name="microsoft-defender-advanced-threat-protection--baseline--preview----3754134---"></a>Microsoft Defender Advanced Threat Protection のベースライン (プレビュー)<!--  3754134 -->
[Microsoft Defender Advanced Threat Protection](../protect/security-baseline-settings-defender-atp.md) の設定に、セキュリティ ベースラインのプレビューを追加しました。 ご使用の環境が [Microsoft Defender Advanced Threat Protection](../protect/advanced-threat-protection.md#prerequisites) を使用するための前提条件を満たしている場合は、このベースラインを使用できます。

### <a name="device-enrollment"></a>デバイスの登録

#### <a name="windows-enrollment-status-page-esp-is-now-generally-available---3605348---"></a>Windows 登録ステータス ページ (ESP) が一般提供される<!-- 3605348 -->
登録ステータス ページがプレビューではなくなりました。 詳しくは、「[登録ステータス ページを設定する](../enrollment/windows-enrollment-status.md)」をご覧ください。


#### <a name="intune-user-interface-update---autopilot-enrollment-profile-creation---4593669---"></a>Intune ユーザー インターフェイスの更新 - Autopilot 登録プロファイルの作成<!-- 4593669 -->
Autopilot 登録プロファイルを作成するためのユーザー インターフェイスが、Azure ユーザー インターフェイスの形式に準拠するように更新されました。 詳細は、[AutoPilot 登録プロファイルの作成](../enrollment/enrollment-autopilot.md#create-an-autopilot-deployment-profile)に関するページを参照してください。 Intune の追加のシナリオでは、今後はこの新しい UI 形式に更新されます。

#### <a name="enable-autopilot-reset-for-all-windows-devices---4225665---"></a>すべての Windows デバイスに対して Autopilot リセットを有効にする<!-- 4225665 -->
登録ステータス ページを使用するように構成されていない場合であっても、AutoPilot リセットがすべての Windows デバイスにおいて有効になりました。 初期のデバイス登録時に、登録ステータス ページがデバイスに対して構成されていなかった場合、デバイスではサインイン後、デスクトップへと直接移動します。 同期して Intune 内での適合が確認できるまでに、最大で 8 時間かかる場合があります。 詳しくは、「[Windows Autopilot のリセット](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-reset-remote)」をご覧ください。

#### <a name="exact-imei-format-not-required-when-searching-all-devices--30407680---"></a>[すべてのデバイス] を検索する場合に厳密な IMEI 形式を必須としない<!--30407680 -->
**[すべてのデバイス]** を検索するときに、IMEI 番号にスペースを含める必要がなくなります。

#### <a name="deleting-a-device-in-the-apple-portal-will-be-reflected-in-the-intune-portal--2489996---"></a>Apple ポータルでデバイスを削除すると、Intune ポータルに反映される<!--2489996 -->
Apple の Device Enrollment Program または Apple Business Manager ポータルからデバイスが削除されると、そのデバイスは Intune から次回の同期中に自動的に削除されます。

### <a name="the-enrollment-status-page-now-tracks-win32-apps---2714451---"></a>登録ステータス ページによる Win32 アプリの追跡<!-- 2714451 -->
これは、Windows 10 バージョン 1903 以降を稼働しているデバイスにのみ適用されます。 詳しくは、「[登録ステータス ページを設定する](../enrollment/windows-enrollment-status.md)」をご覧ください。

### <a name="device-management"></a>デバイス管理

#### <a name="reset-and-wipe-devices-in-bulk-by-using-the-graph-api---3295288---"></a>Graph API を使用してデバイスを一括でリセットおよびワイプする<!-- 3295288 -->
Graph API を使用して 100 台までのデバイスを一括でリセットおよびワイプできるようになりました。

### <a name="monitor-and-troubleshoot"></a>監視とトラブルシューティング

#### <a name="the-encryption-report-is-out-of-public-preview---4587546--------"></a>暗号化レポートのパブリック プレビューが終了する<!-- 4587546      -->
[BitLocker およびデバイス暗号化用のレポート](../protect/encryption-monitor.md)が一般提供されるようになり、パブリック プレビュー段階ではなくなりました。

<!-- ########################## -->

#### <a name="outlook-signature-and-biometric-settings-for--ios-and-android-devices---4050557---"></a>iOS および Android デバイス用の Outlook 署名と生体認証の設定<!-- 4050557 -->
iOS および Android デバイス上では、Outlook 内で既定の署名を有効にするかどうかを指定できるようになりました。 さらに、iOS 上の Outlook では、ユーザーによる生体認証設定の変更を許可する選択ができるようになっています。

## <a name="week-of-may-6-2019"></a>2019 年 5 月 6 日の週

### <a name="device-configuration"></a>デバイス構成

#### <a name="network-access-control-nac-support-for-f5-access-for-ios-devices---4500808---"></a>iOS デバイス用 F5 Access に向けたネットワーク アクセス制御 (NAC) のサポート<!-- 4500808 -->

F5 は、iOS 上の Intune に、F5 Access で NAC 機能を許可する BIG-IP 13 の更新プログラムをリリースしました。 この機能を使用するには、以下を行います。

- BIG-IP を 13.1.1.5 refresh に更新します。 BIG-IP 14 はサポートされていません。
- NAC 用に Intune に BIG-IP を統合します。 「[Overview:Configuring APM for device posture checks with endpoint management systems](https://techdocs.f5.com/kb/en-us/products/big-ip_apm/manuals/product/apm-client-configuration-7-1-6/6.html)」 (概要: エンドポイント管理システムを使用したデバイス ポスチャ チェック用の APM の構成) の手順。
- Intune の VPN プロファイルの **Enable Network Access Control (NAC)** 設定を確認します。

利用できる設定については、[iOS デバイスへの VPN 設定の構成](../configuration/vpn-settings-ios.md)に関する記事を参照してください。

適用対象: iOS

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune---doc-vso-1521237----"></a>PFX Certificate Connector for Microsoft Intune の更新<!-- doc-vso 1521237  -->  
ポーリング間隔を 5 分から 30 秒に減らす [PFX Certificate Connector for Microsoft Intune](../protect/certficates-pfx-configure.md#whats-new-for-connectors) の更新プログラムをリリースしました。




## <a name="notices"></a>通知

[!INCLUDE [Intune notices](../includes/intune-notices.md)]
