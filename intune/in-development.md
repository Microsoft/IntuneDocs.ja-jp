---
title: 開発中 - Microsoft Intune
titleSuffix: ''
description: Microsoft Intune の開発中の機能
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/28/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 633bf52084ad261f768cb4e59aaf4ce0ab5cd5bc
ms.sourcegitcommit: 46f4d3d160e18aeab9de7477eedc8351fbb78c85
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2019
ms.locfileid: "67468728"
---
# <a name="in-development-for-microsoft-intune---july-2019"></a>Microsoft Intune 用に開発中 - 2019 年 7 月

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

### <a name="device-users-can-view-all-managed-apps-theyve-installed-or-tried-to-install----2352913---"></a>デバイスのユーザーは、インストール済みまたはインストールしようとしたすべての管理対象アプリを表示できる <!-- 2352913 -->
Windows 用ポータル サイトに、ユーザーのデバイスにインストールされているすべてのマネージド アプリ (必須および使用可能の両方) が一覧表示されます。 ユーザーは、試行した、および保留中のアプリのインストールと、それらの現在の状態を表示することができるようになります。 組織でアプリが必須または使用可能とされていない場合、会社のアプリは全くインストールされていないというメッセージがユーザーに表示されます。 ユーザーはまた、インストールの状態でアプリを並べ替えまたはフィルタリングすることができます。

### <a name="customized-notifications-for-users-and-groups-------16766574-----"></a>ユーザーとグループのカスタマイズされた通知    <!-- 16766574   -->
さらに、iOS および Android デバイスを Intune で管理する上のユーザーがポータル サイト アプリケーションからカスタムの一時的なプッシュ通知を送信することが間もなくなります。 これらのカスタム通知が特定の Intune 機能に関連付けられていないの一部を送信する一般的な通知など、必要な目的に使用できるすべての従業員またはします。  

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>組織のアカウントのアプリの通知のコンテンツを構成します。 <!-- 2576686 -->
Android および iOS デバイスで Intune アプリ保護ポリシー (アプリ) を使用するアプリの通知のコンテンツをコントロールに組織のアカウント。 この機能では、アプリケーションからのサポートは必要とし、すべてのアプリを有効になっているアプリケーションで使用できることができない可能性があります。 アプリの詳細については、「[アプリ保護ポリシーとは](app-protection-policy.md)」を参照してください。

### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956----"></a>Android の仕事用プロファイルに使用できる Google Play アプリのレポート <!-- 3041956  -->
Android の仕事用プロファイル デバイスに使用できるアプリのインストールについては、アプリのインストール状態と managed Google Play アプリのインストール済みバージョンを確認できます。 詳細については、[アプリの保護ポリシーを監視する方法](app-protection-policies-monitor.md)、[Intune を使用した Android の仕事用プロファイル デバイスの管理](android-enterprise-overview.md)、および[マネージド Google Play アプリの種類](apps-add-android-for-work.md#managed-google-play-app-type)に関する記事を参照してください。

<!-- ***********************************************-->
## <a name="device-configuration"></a>デバイス構成


### <a name="support-for-ikev2-vpn-profiles-for-ios----1943438---"></a>iOS 用の IKEv2 VPN プロファイルのサポート <!-- 1943438 -->
IKEv2 プロトコルを使用して、iOS ネイティブ VPN クライアント用の VPN プロファイルを作成できるようになります。 IKEv2 は、 **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  > **プラットフォームに [iOS]** > プラットフォームの種類に **[VPN]** > **[設定]** の新しい接続の種類です。

これらの VPN プロファイルではネイティブ VPN クライアントを構成します。 そのため、VPN クライアント アプリはマネージド デバイスにインストールまたはプッシュされません。 この機能を使用するには、デバイスを Intune に登録する必要があります (MDM 登録)。

現在構成できる VPN 設定については、「[Microsoft Intune で iOS デバイスに対する VPN 設定を構成する](vpn-settings-ios.md)」を参照してください。

適用対象: iOS

### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910---"></a>Windows 10 デバイス構成プロファイルを作成するときは "適用規則" を使用する <!-- 2549910 -->
Windows 10 デバイス構成プロファイルを作成します ( **[デバイスの構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  >  **[Windows 10]** (プラットフォーム))。 **適用規則**を作成し、プロファイルが特定のエディションまたは特定のバージョンにのみ適用されるようにすることができます。 たとえば、いくつかの BitLocker 設定を有効にするプロファイルを作成します。 プロファイルを追加したら、適用規則を使用して Windows 10 Enterprise を実行しているデバイスにのみプロファイルを適用します。

適用対象: 
- Windows 10 以降

### <a name="administrative-templates-for-group-policy---------3510695---"></a>グループ ポリシーの管理用テンプレート     <!--  3510695 -->
クラウド内のデバイスのセキュリティを向上するために、Intune を使用して Windows PC 用に選択したグループ ポリシー設定を構成することができる管理用テンプレートをリリースする予定です。  これらのテンプレートでは、Office、Windows、および OneDrive の最大 2,500 個の追加設定を提供するためにポリシー構成サービス プロバイダー (CSP) を使用します。

### <a name="manage-filevault-for-macos-------3858502--1210104-----"></a>MacOS 用の FileVault を管理します。   <!--  3858502 + 1210104   -->
Intune endpoint protection のデバイス構成プロファイルを使用して macOS デバイス向けの FileVault キー暗号化を管理することができます。 これには、表示と、会社のデバイスの暗号化キーの回転のエスクローが含まれます。 エンドユーザーはポータル サイト web サイトを通じてこれらのキーを取得することになります。

### <a name="advanced-settings-for-windows-defender-firewall-------1311949-------"></a>Windows Defender ファイアウォールの詳細設定   <!--  1311949     -->
まもなく、パブリック プレビューとして、Intune を使って Windows Defender 用のクライアント上のカスタム ファイアウォール規則を管理することができるようになります。  

### <a name="new-configuration-designer-when-creating-an-oemconfig-profile-for-android-enterprise----3712769----"></a>Android Enterprise に対する OEMConfig プロファイルを作成するときに、新しい構成デザイナー <!-- 3712769  -->
Intune では、OEMConfig アプリを使用するデバイス構成プロファイルを作成することができます (デバイスの構成 > プロファイル > プロファイルを作成 > プラットフォーム用の Android エンタープライズ > プロファイルの種類の OEMConfig)。 これを行うときにテンプレートを変更するための値と JSON エディターが開きます。 この更新プログラムには、タイトルや説明などを含めて、アプリに埋め込まれている詳細情報を示すより優れたユーザー エクスペリエンスを持つ構成デザイナーが含まれています。 JSON エディターは、引き続き使用できますが、構成デザイナーで行った変更を示しています。

現在の設定を確認するには[使用 OEMConfig による Android エンタープライズ デバイスの管理と](android-oem-configuration-overview.md)します。

適用対象: Android エンタープライズ


<!-- ***********************************************-->
## <a name="device-management"></a>デバイス管理

### <a name="improve-device-location---3855417---"></a>デバイスの場所を向上させる<!-- 3855417 -->
使用して、デバイスの正確な座標を拡大できる、**デバイスを検索**アクション。 紛失した iOS デバイスを見つける方法についての詳細については、次を参照してください。 [iOS デバイスを紛失検索](device-locate.md)します。

### <a name="configure-automatic-device-clean-up-time-limit-down-to-30-days---4231059----"></a>30 日間までのデバイスの自動クリーンアップ時間制限を構成します。 <!--4231059  -->
デバイスの自動クリーンアップの最後のサインイン後に (90 日間の現在の制限) ではなく 30 日間の短い時間制限を設定することができます。 これを行うに移動**Intune** > **デバイス** > **セットアップ** > **デバイス クリーン アップ ルール**します。


<!-- ***********************************************-->
## <a name="security"></a>セキュリティ

### <a name="import-and-export-security-baselines------3408610------------"></a>セキュリティ基準のインポートとエクスポート    <!--3408610          -->  
エクスポートしたカスタマイズを実行し、Intune 環境間で共有できるように、セキュリティ基準をインポートし、機能を追加いたします。



<!-- ***********************************************-->
## <a name="notices"></a>通知

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

## <a name="see-also"></a>関連項目
最近の開発状況について詳しくは、「[Microsoft Intune の新機能](whats-new.md)」をご覧ください。


