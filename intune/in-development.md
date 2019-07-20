---
title: 開発中 - Microsoft Intune
titleSuffix: ''
description: Microsoft Intune の開発中の機能
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6ee62213c9ef23302de7fa7342569e1903514699
ms.sourcegitcommit: 11a31cd39b727f2254e2705b07d18924e103bd2e
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/19/2019
ms.locfileid: "68341346"
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


### <a name="customized-notifications-for-users-and-groups-------16766574-----"></a>ユーザーとグループのためのカスタマイズされた通知    <!-- 16766574   -->
Intune で管理する iOS デバイスと Android デバイスのユーザーに、ポータルサイトアプリケーションからカスタムアドホックプッシュ通知をすぐに送信できるようになります。 これらのカスタム通知は、特定の Intune 機能に関連付けられておらず、一部またはすべての従業員に送信する一般的な通知など、必要な目的に使用できます。  

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>組織アカウントのアプリ通知コンテンツを構成する <!-- 2576686 -->
Android および iOS デバイスの Intune アプリ保護ポリシー (アプリ) では、組織アカウントのアプリ通知コンテンツを制御できます。 この機能は、アプリケーションからのサポートを必要とし、すべてのアプリ対応アプリケーションで使用できるとは限りません。 アプリの詳細については、「[アプリ保護ポリシーとは](app-protection-policy.md)」を参照してください。

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

### <a name="advanced-settings-for-windows-defender-firewall-------1311949-------"></a>Windows Defender ファイアウォールの詳細設定   <!--  1311949     -->
まもなく、パブリック プレビューとして、Intune を使って Windows Defender 用のクライアント上のカスタム ファイアウォール規則を管理することができるようになります。  

### <a name="new-configuration-designer-when-creating-an-oemconfig-profile-for-android-enterprise----3712769----"></a>Android Enterprise 用の OEMConfig プロファイルを作成するときの新しい構成デザイナー <!-- 3712769  -->
Intune では、OEMConfig アプリを使用するデバイス構成プロファイルを作成できます (デバイス構成 > プロファイル > プロファイルの作成 > Android enterprise for platform > [プロファイルの種類] の [OEMConfig])。 これを行うと、JSON エディターが開き、テンプレートと値を変更できます。 この更新プログラムには、タイトルや説明など、アプリに埋め込まれた詳細を表示する、ユーザーエクスペリエンスが向上した構成デザイナーが含まれています。 JSON エディターは引き続き使用でき、構成デザイナーで行ったすべての変更が表示されます。

現在の設定を確認するには、「 [OEMConfig を使用した Android Enterprise デバイスの使用と管理](android-oem-configuration-overview.md)」を参照してください。

適用対象: Android エンタープライズ


<!-- ***********************************************-->
## <a name="device-management"></a>デバイス管理

### <a name="improve-device-location---3855417---"></a>デバイスの場所を改善する<!-- 3855417 -->
**デバイスの検索**アクションを使用して、デバイスの正確な座標を拡大することができます。 紛失した iOS デバイスを特定する方法の詳細については、「紛失した[ios デバイスの検出](device-locate.md)」を参照してください。

### <a name="configure-automatic-device-clean-up-time-limit-down-to-30-days---4231059----"></a>自動デバイスクリーンアップの時間制限を30日に設定する <!--4231059  -->
最後にサインインした後に、デバイスの自動クリーンアップ時間の制限を30日 (現在の制限である90日よりも短く) に設定することができます。 これを行うには、 **Intune** > **デバイス** > **セットアップ** > **デバイスのクリーンアップルール**に関するページを参照してください。


<!-- ***********************************************-->
## <a name="security"></a>セキュリティ

### <a name="import-and-export-security-baselines------3408610------------"></a>セキュリティベースラインのインポートとエクスポート    <!--3408610          -->  
カスタマイズを可能にし、Intune 環境間で共有できるように、セキュリティベースラインをエクスポートおよびインポートする機能を追加しています。



<!-- ***********************************************-->
## <a name="notices"></a>通知

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

## <a name="see-also"></a>関連項目
最近の開発状況について詳しくは、「[Microsoft Intune の新機能](whats-new.md)」をご覧ください。


