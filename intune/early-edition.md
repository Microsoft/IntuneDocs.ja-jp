---
title: "初期エディション"
description: 
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 06/08/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: 6b098720df2897bc814c94bb1245cffd36439014
ms.contentlocale: ja-jp
ms.lasthandoff: 06/08/2017


---

# <a name="the-early-edition-for-microsoft-intune---june-2017"></a>Microsoft Intune の初期エディション - 2017 年 6 月

**初期エディション**では、Microsoft Intune の今後のリリースで予定されている新機能の一覧を提供しています。 ここに記載されている情報は、ごく限られた範囲について開示されたものであり、また今後変更される可能性があります。 社外ではこの情報を共有しないでください。 ここに挙げられている機能は、発売日に間に合わない可能性があり、その場合は将来のリリースを待たなければなりません。 正式なリリースに向けてパイロット (フライト) テスト中の機能もあります。 ご不明な点や懸念される事項がある場合は、Microsoft 製品グループにお問い合わせください。 

このページは定期的に更新されます。 適宜確認してください。 

> [!Note]
>Intune に関して以下の機能が現在開発されています。 最新のハイブリッド機能の詳細については、[ハイブリッド環境の新機能に関するページ](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)を参照してください。


## <a name="whats-coming-to-intune-on-the-azure-portal"></a>Azure Portal での Intune の新機能

### <a name="new-app-configuration-settings-for-the-intune-managed-browser-----682951----"></a>Intune Managed Browser の新しいアプリ構成設定 <!--- 682951 --->

Intune Managed Browser アプリに新しい構成を追加する予定です。 アプリ構成ポリシーを使用して、ブラウザーの既定のホーム ページとブックマークを構成できるようになります。 

### <a name="restrict-android-device-enrollment-restriction-by-os-version----747620---"></a>Android デバイスの OS のバージョンによる登録制限 <!-- 747620 -->

オペレーティング システムのバージョン番号によって Android の登録を制限できる機能を Intune に追加する予定です。 **[デバイスの種類の制限]** で、IT 管理者は、プラットフォーム構成を設定して、オペレーティング システムのバージョン番号の最小値から最大値までの間に登録を制限できます。 オペレーティング システムのバージョンは、Major.Minor.Build.Rev の形式で指定する必要があります (Minor、Build、Rev は任意)。

>[!NOTE]
>これはセキュリティ機能ではありません。危険性のあるデバイスは、オペレーティング システムのバージョン情報を偽って示すことができるためです。 この機能は、悪意のないユーザーにとって最善の防御策となります。

### <a name="android-for-work-support-for-lookout----1087312---"></a>Lookout の Android for Work サポート <!-- 1087312 -->

Lookout を備えた Intune コネクタでは、Lookout for Work アプリの使用時、Android for Work デバイスをサポートします。 コンテナーの内外に Lookout アプリを展開できるようになる予定です。

### <a name="support-for-offline-apps-from-the-windows-store-for-business-----777044----"></a>ビジネス向け Windows ストアから入手したオフライン アプリのサポート <!--- 777044 --->

ビジネス向け Windows ストアから入手したオフライン アプリが Intune ポータルに同期されます。 また、これらのアプリをデバイス グループまたはユーザー グループに展開できるようになる予定です。 オフライン アプリはストアではなく Intune でインストールします。

### <a name="new-settings-for-windows-10-device-restriction-profile-----978527--978550-978569-978575-1050031-1058611-1124583----"></a>Windows 10 デバイス制限プロファイルの新しい設定 <!--- 978527,  978550, 978569, 978575, 1050031, 1058611, 1124583 --->

Windows 10 デバイス制限プロファイルで、以下の設定が可能になります。

- Windows Defender
- 携帯ネットワークと接続性
- ロック画面
- プライバシー
- 検索
- レポートと遠隔測定
- Windows スポットライト
- Edge ブラウザー

### <a name="support-for-shared-ipads-with-the-ios-classroom-app----1044681-854689---"></a>iOS Classroom アプリによる共有 iPad のサポート <!-- 1044681, 854689 -->

Microsoft は、iOS Classroom アプリの管理サポートを拡張し、自分で管理している Apple ID を使用して共有 iPad にログインする生徒を追加できるようにする予定です。

### <a name="office-365-proplus-app-available-for-windows-10-devices---1121362--"></a>Windows 10 デバイスで Office 365 ProPlus アプリが使用可能に <!--1121362-->

Microsoft は新しい種類の Office 365 ProPlus アプリを追加します。Office 365 ProPlus アプリを Windows 10 デバイスに割り当てる作業が簡単になります。 また、ライセンスを所有している場合、Microsoft Project や Microsoft Visio をインストールすることもできます。 必要なアプリがバンドルされ、Intune コンソールのアプリ一覧に 1 つのアプリとして表示されます。

### <a name="tag-corporate-owned-devices-with-serial-number----1215070---"></a>会社所有のデバイスにシリアル番号をタグ付けする <!-- 1215070 -->

Intune では、iOS、macOS、Android のシリアル番号を会社所有デバイスの識別子としてアップロードできる機能がサポートされる予定です。 この新機能では、シリアル番号を使用して個人用デバイスの登録をブロックすることはできません。登録中はシリアル番号が検証されないためです。 シリアル番号を使用して個人用デバイスをブロックする機能は、近いうちにリリースされる予定です。

### <a name="scom-management-pack-for-exchange-connector----885457---"></a>Exchange Connector 用の SCOM 管理パック <!-- 885457 -->

Exchange Connector 用の System Center Operations Manager (SCOM) 管理パックを Exchange Connector のログ解析に利用できるようになります。 問題のトラブルシューティングを行う必要がある場合、この機能によって別の方法で Intune を監視できます。

### <a name="new-role-based-administration-access-for-intune-admins----1099990---"></a>Intune 管理者のための新しいロール ベース管理アクセス <!-- 1099990 -->

Azure AD の条件付きアクセス ポリシーを表示、作成、変更、削除できる新しい条件付きアクセス管理者ロールが追加されます。 以前は、このアクセス許可を持つのは、グローバル管理者とセキュリティ管理者のみでした。 条件付きアクセス ポリシーにアクセスできるように、Intune 管理者にこのロールのアクセス許可が付与されます。

### <a name="app-based-conditional-access-for-microsoft-teams----1257019---"></a>Microsoft Teams へのアプリ ベースの条件付きアクセス <!-- 1257019 -->

iOS と Android 用の Microsoft Teams アプリは、Exchange と SharePoint Online のアプリ ベースの条件付きアクセス ポリシー向けの承認済みアプリの一部です。 アプリ ベースの条件付きアクセスを使用して、Azure Portal の Intune アプリ保護ブレードで、すべてのテナントにアプリを構成できるようになります。

## <a name="whats-coming-to-intune-apps"></a>Intune アプリの新機能

### <a name="improved-notification-for-samsung-knox-startup-pins---1087143--"></a>Samsung KNOX 起動 PIN の通知機能強化 <!--1087143-->

暗号化に対応する目的でエンド ユーザーが Samsung KNOX デバイスに起動 PIN を設定する必要があるとき、エンド ユーザーに表示される通知をタップすると、設定アプリ内の設定場所に移動します。  以前は、エンド ユーザーは通知からパスワード変更画面に進むことができました。

### <a name="promoting-the-most-current-version-of-the-company-portal-for-android---1098661--"></a>Company Portal for Android の最新版の奨励 <!--1098661-->

アプリの通知画面で、Company Portal for Android アプリの最新推奨版がリリースされたとき、エンド ユーザーにアプリ内通知が表示されます。 この通知はユーザーに "ポータル サイトの更新版が利用できる" ことを伝えます。 通知をタップすると、Web ページが開きます。そのページに、更新版をダウンロードできるアプリ ストアの一覧が表示されます。 

### <a name="improvements-to-app-syncing-with-windows-10-creators-update----676505---"></a>Windows 10 Creators Update とアプリを同期する機能の強化 <!-- 676505 -->

Company Portal for Windows 10 は、Windows 10 Creators Update (1704) がインストールされているデバイスのアプリ インストール要求の同期を自動的に開始します。 "同期保留中" 状態中、アプリ インストールが止まる問題を減らします。 また、ユーザーはアプリ内から同期を手動で開始できます。 

Company Portal for Windows 10 には、更新ボタンもあります。ユーザーは必要なときにアプリのコンテンツを更新できます。 

### <a name="new-guided-experience-for-windows-10-company-portal----1058938---"></a>Windows 10 ポータル サイトの新しいガイド機能 <!-- 1058938 -->

Windows 10 用のポータル サイト アプリで、特定または登録されていないデバイス向けのガイド付き Intune チュートリアルを利用できるようになります。 ユーザーは新たな段階的手順に従って、Azure Active Directory (条件付きアクセス機能のために必要) と MDM (デバイス管理機能のために必要) に登録できます。 このガイドには、ポータル サイトのホーム ページからアクセスできます。 ユーザーは登録が完了していなくても引き続きアプリを使用できますが、機能は制限されます。

### <a name="improved-sign-in-experience-across-company-portal-apps-for-all-platforms---user-story-1132123--"></a>すべてのプラットフォームでのポータル サイト アプリのサインイン操作の改善<!--User Story 1132123-->

Android、iOS、Windows での Intune ポータル サイト アプリのサインイン エクスペリエンス向上のために、今後数か月間に予定されている変更についてお知らせします。 Azure AD でこの変更が行われ次第、自動的にすべてのプラットフォームでポータル サイト アプリのユーザー エクスペリエンスが一新される予定です。 また、自動生成される一時使用コードを使用して、別のデバイスからポータル サイトにサインインできるようになりました。 これは、資格情報を使用せずにサインインする必要がある場合には特に便利です。

以前のサインイン エクスペリエンス、資格情報を使用した新たなエクスペリエンス、別のデバイスからのエクスペリエンスのスクリーンショットを [アプリ UI の新機能](whats-new-app-ui.md)に関するページで確認できます。


## <a name="notices"></a>通知

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple の要求による Application Transport Security 対応のための更新<!--748318-->

Apple は、2017 年春より Application Transport Security (ATS) の特定の要件を適用すると発表しました。 ATS では、HTTPS 経由で行われるアプリ通信すべてに、より厳格なセキュリティ保護が適用されます。 この変更により、iOS ポータル サイト アプリを使用している Intune ユーザーが影響を受けます。 詳細については、[Intune サポートのブログ](https://aka.ms/compportalats)をご覧ください。

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Apple 登録シナリオへの直接アクセス <!--951869-->

Intune では、2017 年 1 月以降に作成された Intune アカウントについて、Azure プレビュー ポータルの Enroll Devices ワークロードを使用して、Apple 登録シナリオに直接アクセスできるようになりました。 これまでは、Apple 登録プレビューはクラシックの Intune ポータルのリンクからのみアクセスが可能でした。 2017 年 1 月より前に作成された Intune アカウントの場合は、これらの機能が Azure で利用可能になるまでの間、1 回限りの移行が必要です。 移行スケジュールはまだ発表されていませんが、詳細はできる限り早く発表します。 既存のアカウントでプレビューにアクセスできない場合は、試用アカウントを作成して、新しいエクスペリエンスをテストすることを強くお勧めします。

### <a name="plan-for-change-intune-is-changing-the-intune-partner-portal-experience----1050016---"></a>変更の計画: Intune で Intune パートナー ポータル エクスペリエンスが変更されます<!-- 1050016 -->

2017 年 5 月中旬のサービス更新で、Intune パートナーのページが manage.microsoft.com から削除されます。  

お客様がパートナーの管理者である場合は、Intune パートナーのページで顧客に代わって閲覧したり、操作したりすることができなくなります。代わりに、マイクロソフトの他の 2 つのパートナー ポータルのいずれかでサインインする必要があります。

[Microsoft パートナー センター](https://partnercenter.microsoft.com/)と [Microsoft Office 365 パートナー管理センター](https://portal.office.com/)の両方で、管理している顧客アカウントにサインインできます。 パートナーとして前進するために、これらのサイトのいずれかを使用して顧客の管理を行いましょう。

### <a name="see-also"></a>関連項目
最近の開発状況について詳しくは、「[Microsoft Intune の新機能](whats-new.md)」をご覧ください。

