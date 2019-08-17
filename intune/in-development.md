---
title: 開発中 - Microsoft Intune
titleSuffix: ''
description: Microsoft Intune の開発中の機能
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3c2b9429bf5b50ac5e416c4a7b356627e9cc9fb1
ms.sourcegitcommit: f75386986d24e7d5dd63a3f1a0a014cb52056063
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 08/16/2019
ms.locfileid: "69560110"
---
# <a name="in-development-for-microsoft-intune---august-2019"></a>Microsoft Intune 用に開発中 - 2019 年 8 月

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

<!-- ***********************************************-->
## <a name="device-enrollment"></a>デバイスの登録

### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal----4394993----"></a>IOS デバイスの場合は、ポータルサイトの [登録プロセスのプライバシー] 画面をカスタマイズします。 <!-- 4394993  -->
Markdown を使用すると、iOS の登録時にエンドユーザーに表示されるポータルサイトのプライバシー画面をカスタマイズできます。 具体的には、組織がデバイスで参照または実行できない項目の一覧をカスタマイズできます。

<!-- ***********************************************-->
## <a name="security"></a>セキュリティ

### <a name="import-and-export-security-baselines------3408610------------"></a>セキュリティベースラインのインポートとエクスポート    <!--3408610          -->  
ここでは、セキュリティベースラインをエクスポートおよびインポートする機能を追加しています。 この機能を使用すると、カスタマイズを行ったり、Intune 環境間で共有したりすることができます。

<!-- ***********************************************-->
## <a name="notices"></a>通知

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

## <a name="see-also"></a>関連項目
最近の開発状況について詳しくは、「[Microsoft Intune の新機能](whats-new.md)」をご覧ください。




