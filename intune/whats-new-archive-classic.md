---
title: "新機能の公開履歴"
description: "Microsoft Intune の新機能に関するお知らせの公開履歴"
keywords: 
author: brenduns
ms.author: brenduns
manager: angrobe
ms.date: 06/08/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ed2db991-4729-49a7-a1e6-be2ffa0d03d1
ROBOTS: noindex,nofollow
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: b4d83b8b83cba0dab1fc089309201aa591b3d26e
ms.sourcegitcommit: f3b8fb8c47fd2c9941ebbe2c047b7d0a093e5a83
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/11/2017
---
# <a name="whats-new-in-the-intune-classic-portal---previous-months"></a>Intune クラシック ポータルの新機能 (過去数か月)

[!INCLUDE[classic-portal](./includes/classic-portal.md)]

このページには、Intune クラシック ポータルの[新機能](whats-new.md)に関するページで以前にお知らせした機能と通知が表示されます。

## <a name="april-2017"></a>2017 年 4 月

### <a name="new-capabilities"></a>新しい機能

#### <a name="myapps-available-for-managed-browser---822308-822303--"></a>Managed Browser に使用できる MyApps <!--822308, 822303-->

Managed Browser での Microsoft MyApps のサポートが向上します。 管理の対象になっていない Managed Browser ユーザーは、MyApps サービスに直接送られ、そこで管理者がプロビジョニングした SaaS アプリにアクセスできます。 Intune の管理の対象になっているユーザーは、引き続き組み込みの Managed Browser ブックマークから MyApps にアクセスできます。

#### <a name="new-icons-for-the-managed-browser-and-the-company-portal---918433-918431-971473--"></a>Managed Browser とポータル サイトの新しいアイコン <!--918433, 918431, 971473-->

Managed Browser の Android バージョンと iOS バージョンのアイコンが更新されます。 新しいアイコンには、Enterprise Mobility + Security (EM+S) での他のアプリとの一貫性が向上した新しい Intune バッジが含まれます。 Managed Browser 用の新しいアイコンは、[Intune アプリ UI の新機能に関するページ](whats-new-app-ui.md)でご覧いただけます。

Android、iOS、Windows でのポータル サイト アプリのアイコンも更新されて、EM+S での他のアプリとの一貫性が向上します。 これらのアイコンは、4 月から 5 月末にかけて段階的にプラットフォーム全体にリリースされます。

#### <a name="sign-in-progress-indicator-in-android-company-portal---953374--"></a>Android 用ポータル サイトでのサインイン進行状況インジケーター<!--953374-->

Android 用ポータル サイト アプリが更新されて、起動または再開時にサインイン進行状況インジケーターが表示されるようになります。 ユーザーがアプリへのアクセスを許可されるまでにインジケーターに順番に表示される新しいステータスは、[接続中...]、[サインイン中...]、[Checking for security requirements... (セキュリティ要件確認中...)] です。 Android 用ポータル サイト アプリの新しい画面は、[Intune アプリ UI の新機能](whats-new-app-ui.md)に関するページでご覧いただけます。

#### <a name="block-apps-from-accessing-sharepoint-online----679339---"></a>アプリの SharePoint Online へのアクセスをブロック<!-- 679339 -->

アプリ ベースの条件付きアクセス ポリシーを作成して、アプリ保護ポリシーが適用されていないアプリが [SharePoint Online](/intune-classic/deploy-use/mam-ca-for-sharepoint-online) にアクセスするのをブロックできるようになりました。 アプリ ベースの条件付きアクセスのシナリオでは、Azure Portal を使用して SharePoint Online にアクセスするアプリを指定できます。

#### <a name="single-sign-on-support-from-the-company-portal-for-ios-to-outlook-for-ios---834012--"></a>iOS 用のポータル サイトおよび Outlook からのシングル サインオンのサポート <!--834012-->
iOS 用のポータル サイト アプリに既にサインインしているユーザーは、同じデバイス上の同じアカウントを使う Outlook アプリであればサインインしなおす必要はありません。 Outlook アプリを起動するときに、自分のアカウントを選んで自動的にサインインできます。 現在、他の Microsoft アプリにこの機能を追加する作業を進めています。

#### <a name="improved-status-messaging-in-the-company-portal-app-for-ios---744866--"></a>iOS 用ポータル サイト アプリでの状態メッセージの向上<!--744866-->
デバイスで起きていることがよくわかる情報を提供する、新しい具体的なエラー メッセージが iOS 用のポータル サイト アプリに表示されるようになります。 これらのエラー情報は、これまでは "ポータル サイトは一時的に使用できません" というタイトルの一般的なエラー メッセージに含まれていました。 さらに、ユーザーがインターネットに接続できないときに iOS でポータル サイトを開始した場合は、"インターネットに接続されていません" という内容の固定ステータス バーがホーム ページに表示されるようになります。

#### <a name="improved-app-install-status-for-the-windows-10-company-portal-app---676495--"></a>Windows 10 ポータル サイト アプリのアプリ インストール状態の向上<!--676495-->

Windows 10 ポータル サイト アプリで開始されるアプリ インストールの新しい改善点は次のとおりです。
-   MSI パッケージのインストール進行状況レポートの高速化
-   Windows 10 Anniversary Update 以降を実行するデバイス上の先進アプリのインストール進行状況レポートの高速化
-   Windows 10 Anniversary Update 以降を実行するデバイス上の先進アプリのインストールで使用される新しい進行状況バー

新しい進行状況バーは、[Intune アプリ UI の新機能に関するページ](whats-new-app-ui.md)で確認できます。

#### <a name="bulk-enroll-windows-10-devices----747607---"></a>Windows 10 デバイスを一括登録する <!-- 747607 -->

Windows 構成デザイナー (WCD) で Azure Active Directory と Intune に Windows 10 Creators Update を実行する多数のデバイスを参加させることができるようになりました。 Azure AD テナントの [一括 MDM 登録](/intune-classic/deploy-use/bulk-enroll-windows) を有効にするには、Windows 構成デザイナーを使用して Azure AD テナントにデバイスを参加させるプロビジョニング パッケージを作成し、一括登録と管理を行う会社所有のデバイスにパッケージを適用します。 パッケージがデバイスに適用されると、デバイスは Azure AD に参加し、Intune に登録され、Azure AD ユーザーがログオンできる状態になります。  Azure AD ユーザーはこれらのデバイス上の標準ユーザーであり、割り当て済みのポリシーと必須アプリを受け取ります。 この時点では、セルフ サービスとポータル サイトのシナリオはサポートされていません。

### <a name="whats-new-in-the-public-preview-of-intune-in-the-azure-portal--736542--"></a>Azure Portal での Intune のパブリック プレビューの新機能<!--736542-->

2017 年初めには、すべての管理者エクスペリエンスが Azure に移行され、Graph API を幅広く使用する最新のサービス プラットフォーム上で、EMS の中核的ワークフローの強力な統合管理を利用できるようになります。

今月には、Azure Portal で新しい管理者エクスペリエンスのパブリック プレビューを表示する新しい試用テナントが開始されます。 プレビュー状態では、既存の Intune コンソールでの機能とパリティが繰り返し提供されます。

Azure Portal の管理者エクスペリエンスでは、既に発表されている新しいグループ化とターゲット設定の機能が使用されます。既存のテナントを新しいグループ化エクスペリエンスに移行すると、テナントの管理者エクスペリエンスも新しいプレビュー版に移行されます。 テナントを移行する前に、新しい機能をテストしたり見たりしたい場合は、新しい Intune 試用版アカウントにサインアップするか、[新しいドキュメント](whats-new.md)をご覧ください。

Azure の Intune プレビューの新機能は[ここ](whats-new.md)で確認できます。

### <a name="notices"></a>通知

#### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Apple 登録シナリオへの直接アクセス <!--951869-->

Intune では、2017 年 1 月以降に作成された Intune アカウントについて、Azure プレビュー ポータルの Enroll Devices ワークロードを使用して、Apple 登録シナリオに直接アクセスできるようになりました。 これまでは、Apple 登録プレビューは Azure Portal のリンクからのみアクセスが可能でした。 2017 年 1 月より前に作成された Intune アカウントの場合は、これらの機能が Azure で利用可能になるまでの間、1 回限りの移行が必要です。 移行スケジュールはまだ発表されていませんが、詳細はできる限り早く発表します。 既存のアカウントでプレビューにアクセスできない場合は、試用アカウントを作成して、新しいエクスペリエンスをテストすることを強くお勧めします。

#### <a name="whats-coming-for-appx-in-intune-in-the-azure-portal----1000270---"></a>Azure Portal 内の Intune の appx に予定されている新機能 <!-- 1000270 -->

Azure Portal 内の Intune への移行の一環として、appx に関して次の 3 つの変更が行われています。

1. MDM 登録デバイスに対してのみ展開できる新しい appx アプリの種類を、Intune コンソールに追加します。
2. 既存の appx アプリの種類を、Intune PC エージェントによって管理される PC のみを対象とするように用途を変更します。
3. 移行において、すべての既存 appx を MDM appx に変換します。

##### <a name="how-does-this-affect-me"></a>ユーザーへの影響

Intune PC エージェントによって管理されるデバイスへの既存の展開に対する影響はありません。 ただし、移行後に、これらの移行された appx を、Intune PC エージェントによって管理される、以前は対象になっていなかった新しいデバイスに展開することはできません。

##### <a name="what-action-do-i-need-to-take"></a>実行する必要があるアクション

移行終了後、新しい PC 展開を行いたい場合は、appx を PC appx として再アップロードする必要があります。 詳しくは、Intune サポート チーム ブログで [Azure Portal 内の Intune での appx の変更](https://aka.ms/appxchange)に関するページをご覧ください。  

#### <a name="administration-roles-being-replaced-in-azure-portal"></a>Azure Portal で置き換えられる管理ロール

Intune クラシック ポータル (Silverlight) で使用される既存のモバイル アプリケーション管理 (MAM) の管理ロール (共同作成者、所有者、および読み取り専用) は、Intune Azure Portal の新しいロール ベースの管理制御 (RBAC) の完全なセットで置き換えられます。 Azure Portal に移行すると、管理者をこれらの新しい管理ロールに割り当て直す必要があります。 RBAC と新しいロールの詳細については、[Microsoft Intune のロール ベースのアクセス制御](role-based-access-control.md)に関する記事を参照してください。

### <a name="whats-coming"></a>今後の更新情報

#### <a name="improved-sign-in-experience-across-company-portal-apps-for-all-platforms---user-story-1132123--"></a>すべてのプラットフォームでのポータル サイト アプリのサインイン操作の改善<!--User Story 1132123-->

Android、iOS、Windows での Intune ポータル サイト アプリのサインイン エクスペリエンス向上のために、今後数か月間に予定されている変更についてお知らせします。 Azure AD でこの変更が行われ次第、自動的にすべてのプラットフォームでポータル サイト アプリのユーザー エクスペリエンスが一新される予定です。 また、自動生成される一時使用コードを使用して、別のデバイスからポータル サイトにサインインできるようになりました。 これは、資格情報を使用せずにサインインする必要がある場合には特に便利です。

以前のサインイン エクスペリエンス、資格情報を使用した新たなエクスペリエンス、別のデバイスからのエクスペリエンスのスクリーンショットを [アプリ UI の新機能](whats-new-app-ui.md)に関するページで確認できます。

#### <a name="plan-for-change-intune-is-changing-the-intune-partner-portal-experience----1050016---"></a>変更の計画: Intune で Intune パートナー ポータル エクスペリエンスが変更されます<!-- 1050016 -->

2017 年 5 月中旬のサービス更新で、Intune パートナーのページが manage.microsoft.com から削除されます。  

お客様がパートナーの管理者である場合は、Intune パートナーのページで顧客に代わって閲覧したり、操作したりすることができなくなります。代わりに、マイクロソフトの他の 2 つのパートナー ポータルのいずれかでサインインする必要があります。

[Microsoft パートナー センター](https://partnercenter.microsoft.com/)と [Microsoft Office 365 パートナー管理センター](https://portal.office.com/)の両方で、管理している顧客アカウントにサインインできます。 パートナーとして前進するために、これらのサイトのいずれかを使用して顧客の管理を行いましょう。


#### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple の要求による Application Transport Security 対応のための更新<!--748318-->

Apple は、Application Transport Security (ATS) の特定の要件を適用すると発表しました。 ATS では、HTTPS 経由で行われるアプリ通信すべてに、より厳格なセキュリティ保護が適用されます。 この変更により、iOS ポータル サイト アプリを使用している Intune ユーザーが影響を受けます。

Microsoft では、新しい ATS 要件を適用する Apple TestFlight プログラムから、iOS 用ポータル サイト アプリのバージョンを入手できるようにしています。 ATS コンプライアンスをテストできるように、このバージョンを試す場合は、お客様の姓名、電子メール アドレス、および会社名を <a href="mailto:CompanyPortalBeta@microsoft.com?subject=Register to TestFlight ATS Company Portal app">CompanyPortalBeta@microsoft.com</a> に電子メールで送信してください。 詳細については、[Intune サポートのブログ](https://aka.ms/compportalats)をご覧ください。

## <a name="march-2017"></a>2017 年 3 月

### <a name="new-capabilities"></a>新しい機能

#### <a name="support-for-skycure"></a>Skycure のサポート

Microsoft Intune に統合されたモバイル脅威保護ソリューションである Skycure によって実行されるリスク評価に基づき、条件付きアクセスを利用し、モバイル デバイスから会社のリソースへのアクセスを制御できます。 リスクは、Skycure を実行するデバイスから収集される次のような製品利用統計情報に基づいて評価されます。

- 物理的防御
- ネットワーク防御
- アプリケーション防御
- 脆弱性防御

Intune のデバイス コンプライアンス ポリシーにより有効になった Skycure のリスク評価に基づいて、EMS の条件付きアクセス ポリシーを構成できます。 これらのポリシーを使用して、検出された脅威に基づき、非準拠のデバイスによる企業リソースへのアクセスを許可またはブロックすることができます。 詳細については、「[Skycure Mobile Threat Defense コネクター](/intune-classic/deploy-use/skycure-mobile-threat-defense-connector)」を参照してください。

#### <a name="new-user-experience-for-the-company-portal-app-for-android---621622--"></a>Android 用ポータル サイト アプリに関する新しいユーザー エクスペリエンス <!--621622-->

Android 用ポータル サイト アプリでは、ユーザー インターフェイスが最新の外観となり、ユーザー エクスペリエンスが向上しました。 主な更新内容は次のとおりです。

- 色: ポータル サイトのタブ ヘッダーの色が、IT が定義するブランド色になります。
- アプリ: **[アプリ]** タブの **[おすすめアプリ]** ボタンと **[すべてのアプリ]** ボタンが更新されました。
- 検索: **[アプリ]** タブの **[検索]** ボタンが浮動アクション ボタンになりました。
- ナビゲーション アプリ: **[すべてのアプリ]** ビューで **[おすすめ]**、**[すべて]** および **[カテゴリ]** のタブ付きビューが表示され、移動がより簡単になります。
- サポート: **[デバイス]** タブと **[IT に連絡]** タブが更新されて、読みやすくなりました。

これらの変更について詳しくは、「[Intune とエンド ユーザー アプリの UI の更新](whats-new-app-ui.md)」をご覧ください。

#### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>管理されていないデバイスから割り当てられているアプリにアクセス可能 <!--664691-->

ポータル Web サイトでの設計変更に伴い、iOS と Android ユーザーは、管理されていないデバイスで "登録なしで使用可能" として割り当てられているアプリをインストールできるようになります。 Intune 資格情報を使用して、ユーザーはポータル Web サイトにログインし、割り当てられているアプリの一覧を表示することができます。 "登録なしで使用可能" なアプリのアプリ パッケージは、ポータル Web サイトからダウンロードできます。 この変更は、インストールするために登録が必要なアプリには影響しません。そのようなアプリをインストールする場合は、デバイスの登録が求められます。

#### <a name="signing-script-for-windows-10-company-portal---941642--"></a>Windows 10 ポータル サイトの署名スクリプト<!--941642-->

Windows 10 ポータル サイト アプリのダウンロードおよびサイドロードの必要がある場合に、スクリプトを使用して、組織のアプリ署名プロセスを簡素化および合理化できるようになりました。   スクリプトとこれを使用するための手順をダウンロードするには、TechNet ギャラリーの [Windows 10 ポータル サイトの Microsoft Intune 署名スクリプト](https://aka.ms/win10cpscript)に関する記事をご覧ください。 この発表に関して詳しくは、Intune サポート チームのブログの「[Updating your Windows 10 Company Portal app (Windows 10 ポータル サイト アプリの更新)](https://blogs.technet.microsoft.com/intunesupport/2017/03/13/updating-your-windows-10-company-portal-app/)」をご覧ください。


### <a name="notices"></a>通知

#### <a name="support-for-ios-103"></a>iOS 10.3 のサポート

2017 年 3 月 27 日に、iOS ユーザー向けに iOS 10.3 がリリースされました。 既存の Intune MDM と MAM のシナリオには、Apple の最新バージョンの OS との互換性があります。 現在利用できる iOS デバイスを管理するすべて既存の Intune 機能は、ユーザーがデバイスとアプリを iOS 10.3 にアップグレードすることによって機能し続けます。

現時点で共有すべき既知の問題はありません。 iOS 10.3 に関する問題が発生した場合は、[Intune サポート チーム](/intune-classic/troubleshoot/contact-assisted-phone-support-for-microsoft-intune)にお問い合わせください。

#### <a name="improved-support-for-android-users-based-in-china---720444--"></a>中国の Android ユーザー向けのサポートが向上しました <!--720444-->

中国では Google Play ストアを利用できないため、Android デバイスの場合は中国のマーケットプレースからアプリを入手する必要があります。 ポータル サイトでは、中国の Android ユーザーをリダイレクトして、ローカルのアプリ ストアからポータル サイトおよび Outlook のアプリをダウンロードできるようにし、このワークフローをサポートします。 これにより、モバイル デバイス管理およびモバイル アプリケーション管理の両方について、条件アクセス ポリシーが有効な場合に、ユーザー エクスペリエンスが向上します。 Android 用ポータル サイト アプリおよび Outlook アプリは、次の中国のアプリ ストアで入手できます。

- [Baidu](https://go.microsoft.com/fwlink/?linkid=836946)
- [Xiaomi](https://go.microsoft.com/fwlink/?linkid=836947)
- [Tencent](https://go.microsoft.com/fwlink/?linkid=836949)
- [Huawei](https://go.microsoft.com/fwlink/?linkid=836948)
- [Wandoujia](https://go.microsoft.com/fwlink/?linkid=836950)

#### <a name="best-practice-make-sure-your-company-portal-apps-are-up-to-date---879465--"></a>ベスト プラクティス: ポータル サイト アプリが最新かどうかを確認する<!--879465-->

2016 年 12 月にマイクロソフトは、ユーザーのグループの iOS、Android、Windows 8.1 以降、または Windows Phone 8.1 以降のデバイスの登録時に、これらのグループへの多要素認証 (MFA) の強制を有効にする更新プログラムをリリースしました。 この機能を使用するには、Android (v5.0.3419.0 以降) および iOS (v2.1.17 以降) 向けのポータル サイト アプリの特定のベースライン バージョンが必要です。

マイクロソフトでは、あらゆるサポートされたプラットフォームでコンソールとポータル サイト アプリの両方に新機能を追加することで Intune の向上に継続的に取り組んでいます。 この結果、マイクロソフトは、現在のバージョンのポータル サイト アプリに見つかった問題のみの修正プログラムをリリースしています。 このため、ユーザー エクスペリエンスを最善にするために、最新バージョンのポータル サイト アプリを使用することをお勧めします。

>[!Tip]
> ユーザーに、適切なアプリ ストアからアプリを自動的に更新するようにデバイスを設定してもらうようにしてください。 Android ポータル サイト アプリをネットワーク共有で使用できるようにしている場合は、[Microsoft ダウンロード センター](https://www.microsoft.com/download/details.aspx?id=49140)から最新バージョンをダウンロードできます。

#### <a name="microsoft-teams-is-now-enabled-for-mam-on-ios-and-android"></a>iOS および Android で MAM で利用できるようになった Microsoft Teams

マイクロソフトは、Microsoft Teams の一般公開を発表しました。 更新された iOS および Android 向け Microsoft Teams アプリが Intune モバイル アプリ管理 (MAM) 機能で有効になったため、すべての段階で会話や企業データを保護しながら、デバイスを問わず作業することでチームの生産性をたかめることができるようになりました。 詳しくは、Enterprise Mobility and Security チームのブログの [Microsoft Teams に関するお知らせ](https://blogs.technet.microsoft.com/enterprisemobility/2017/03/14/microsoft-teams-is-now-generally-available-and-mam-enabled-on-ios-and-android/)をご覧ください。


## <a name="february-2017"></a>2017 年 2 月

### <a name="new-capabilities"></a>新しい機能

### <a name="modernizing-the-company-portal-website---753980--"></a>ポータル Web サイトの進化 <!--753980-->
ポータル Web サイトで管理対象のデバイスを持っていないユーザーを対象とするアプリをサポートします。 この Web サイトは、新しいコントラストの配色パターン、動的な図、および "ハンバーガー メニュー"  ![(ヘルプデスクの連絡先詳細や既存の管理対象デバイスに関する情報を含む、](./media/CP_hamburger_menu.png)。

### <a name="notices"></a>通知

#### <a name="group-migration-will-not-require-any-updates-to-groups-or-policies-for-ios-devices---898837--"></a>グループの移行に、iOS デバイス用のグループまたはポリシーの更新は不要<!--898837-->
業務用デバイスの登録プロファイルで事前に割り当てられている Intune デバイス グループごとに、Azure Active Directory デバイス グループへの移行時に、業務用デバイスの登録プロファイルの名前に基づいて、AAD に対応する動的デバイス グループが作成されます。 これにより、デバイスは登録時に確実に自動でグループ化され、元の Intune グループと同じポリシーおよびアプリが受信されるようになります。

テナントがグループ化と対象設定のための移行プロセスに入ると、Intune で自動的に動的 AAD グループが作成され、業務用デバイスの登録プロファイルの対象となる Intune グループに対応します。 Intune 管理者が対象となる Intune グループを削除しても、対応する動的 AAD グループは削除されません。 グループのメンバーと動的クエリは消去されますが、グループ自体は、IT 管理者が AAD ポータルで削除するまで残ります。

同様に、IT 管理者が業務用デバイスの登録プロファイルの対象となる Intune グループを変更した場合、Intune では新しいプロファイルの割り当てを反映する新しい動的グループが作成されますが、古い割り当て用に作成された動的グループが削除されることはありません。

### <a name="defaulting-to-managing-windows-desktop-devices-through-windows-settings---663050--"></a>Windows 設定による Windows デスクトップ デバイスの既定での管理 <!--663050-->
Windows 10 デスクトップを登録するための既定の動作が変わります。 新しい登録では、PC エージェントを使用するのではなく、一般的な MDM エージェント登録フローに従います。 ポータル Web サイトでは、Windows 10 デスクトップのユーザーに登録手順が提供されます。この手順では、Windows 10 デスクトップ コンピューターをモバイル デバイスとして追加するプロセスが示されます。 これは、現在登録されている PC には影響しません。組織では引き続き、[任意の](/intune-classic/deploy-use/set-up-windows-device-management-with-microsoft-intune) PC エージェントを使用して Windows 10 デスクトップを管理できます。

#### <a name="improving-mobile-app-management-support-for-selective-wipe---581242--"></a>選択的ワイプのためのモバイル アプリ管理サポートの向上 <!--581242-->
"アプリのデータがワイプされるまでのオフライン期間" ポリシーにより、職場または学校のデータが自動的に削除された場合に、そのデータへのアクセス権の再取得方法に関する追加のガイダンスがエンド ユーザーに示されます。<!--, or the removal of the Intune Company Portal on Android.-->

#### <a name="company-portal-for-ios-links-open-inside-the-app---665954--"></a>iOS 用ポータル サイトのリンクをアプリ内で開く <!--665954-->
iOS 用ポータル サイト内のリンク (ドキュメントとアプリへのリンクを含む) は、Safari のアプリ内ビューを使用して、ポータル サイト アプリに直接開きます。 この更新プログラムは、1 月にサービス更新プログラムとは別に提供されます。

#### <a name="new-mdm-server-address-for-windows-devices---893007--"></a>Windows デバイス用の新しい MDM サーバー アドレス <!--893007-->
Windows および Windows Phone のユーザーがデバイスを登録しようとして、MDM サーバー アドレスとして (入力を求められた場合に) __manage.microsoft.com__ を入力した場合、登録は失敗します。 MDM サーバー アドレスは、__manage.microsoft.com__ から __enrollment.manage.microsoft.com__ に変更されています。Windows や Windows Phone デバイスの登録時に、MDM サーバー アドレスの入力を求められた場合は、__enrollment.manage.microsoft.com__ を使用するようにユーザーに通知してください。 CNAME 設定に変更は必要ありません。 この変更の詳細については、[aka.ms/intuneenrollsvrchange](https://aka.ms/intuneenrollsvrchange) を参照してください。

#### <a name="new-user-experience-for-the-company-portal-app-for-android---621622--"></a>Android 用ポータル サイト アプリに関する新しいユーザー エクスペリエンス <!--621622-->
3 月以降、Android 用ポータル サイト アプリでは[材料設計ガイドライン](https://material.io/guidelines/material-design/introduction.html)に従って、最新の外観が作成されます。 この改善されたユーザー エクスペリエンスには、次のものが含まれます。

* __色__: タブ ヘッダーを、カスタムの色パレットに従って色付けすることができます。
* __インターフェイス__: [アプリ] タブの [おすすめアプリ] ボタンと [すべてのアプリ] ボタンが更新されました。[検索] ボタンは浮動アクション ボタンになりました。
* __ナビゲーション__: [すべてのアプリ] で [おすすめ]、[すべて] および [カテゴリ] のタブ付きビューが表示され、移動がより簡単になります。
* __サービス__: [デバイス] タブと [IT に連絡] タブが読みやすくなりました。

[UI の更新ページ](whats-new-app-ui.md)で、更新前と後のイメージを確認できます。

### <a name="associate-multiple-management-tools-with-the-microsoft-store-for-business---926135--"></a>複数の管理ツールとビジネス向け Microsoft ストアの関連付け <!--926135-->
ビジネス向け Microsoft ストアのアプリを展開するために複数の管理ツールを使用する場合、これまでは、ビジネス向け Microsoft ストアにはそのうちの 1 つしか関連付けることができませんでした。 これからは、複数のツール (Intune や Configuration Manager など) をストアに関連付けることができます。 詳細については、「[ビジネス向け Microsoft ストアから購入したアプリを Microsoft Intune で管理する](/intune-classic/deploy-use/manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune#associate-your-windows-store-for-business-account-with-intune)」を参照してください。

## <a name="whats-new-in-the-public-preview-of-intune-in-the-azure-portal---736542--"></a>Azure Portal での Intune のパブリック プレビューの新機能 <!--736542-->

2017 年初めには、すべての管理者エクスペリエンスが Azure に移行され、Graph API を幅広く使用する最新のサービス プラットフォーム上で、EMS の中核的ワークフローの強力な統合管理を利用できるようになります。

今月には、Azure Portal で新しい管理者エクスペリエンスのパブリック プレビューを表示する新しい試用テナントが開始されます。 プレビュー状態では、既存の Intune コンソールでの機能とパリティが繰り返し提供されます。

Azure Portal の管理者エクスペリエンスでは、既に発表されている新しいグループ化とターゲット設定の機能が使用されます。既存のテナントを新しいグループ化エクスペリエンスに移行すると、テナントの管理者エクスペリエンスも新しいプレビュー版に移行されます。 テナントを移行する前に、新しい機能をテストしたり見たりしたい場合は、新しい Intune 試用版アカウントにサインアップするか、[新しいドキュメント](whats-new.md)をご覧ください。

Azure の Intune プレビューの新機能は[ここ](whats-new.md)で確認できます。

## <a name="january-2017"></a>2017 年 1 月

### <a name="new-capabilities"></a>新しい機能

#### <a name="in-console-reports-for-mam-without-enrollment---677961--"></a>登録を必要としない MAM のコンソール内レポート <!--677961-->
登録されているデバイスと登録されていないデバイスの両方に対して、新しいアプリ保護レポートが追加されました。 詳細については、「[Microsoft Intune でのモバイル アプリ管理ポリシーの監視](/intune-classic/deploy-use/monitor-mobile-app-management-policies-with-microsoft-intune)」を参照してください。

#### <a name="android-711-support---694397--"></a>Android 7.1.1 のサポート <!--694397-->
Intune では Android 7.1.1 が完全にサポートされ、管理されるようになりました。

#### <a name="resolve-issue-where-ios-devices-are-inactive-or-the-admin-console-cannot-communicate-with-them---unknown--"></a>iOS デバイスが無効か、管理コンソールと通信できない問題を解決 <!--unknown-->
ユーザーのデバイスと Intune の接続が失われるとき、新しいトラブルシューティング手順を指示できます。会社リソースへのアクセスを回復するのに役立ちます。 「[デバイスが無効か、管理コンソールとデバイスが通信できない](/intune-classic/troubleshoot/troubleshoot-device-enrollment-in-intune#devices-are-inactive-or-the-admin-console-cannot-communicate-with-them)」を参照してください。

### <a name="notices"></a>通知

#### <a name="defaulting-to-managing-windows-desktop-devices-through-windows-settings---663050--"></a>Windows 設定による Windows デスクトップ デバイスの既定での管理 <!--663050-->
Windows 10 デスクトップを登録するための既定の動作が変わります。 新しい登録では、PC エージェントを使用するのではなく、一般的な MDM エージェント登録フローに従います。

ポータル Web サイトでは、Windows 10 デスクトップのユーザーに登録手順が提供されます。この手順では、Windows 10 デスクトップ コンピューターをモバイル デバイスとして追加するプロセスが示されます。 これは、現在登録されている PC には影響しません。組織では引き続き、[任意の](/intune-classic/deploy-use/set-up-windows-device-management-with-microsoft-intune) PC エージェントを使用して Windows 10 デスクトップを管理できます。

#### <a name="improving-mobile-app-management-support-for-selective-wipe---581242--"></a>選択的ワイプのためのモバイル アプリ管理サポートの向上 <!--581242-->
"アプリのデータがワイプされるまでのオフライン期間" ポリシーにより、職場または学校のデータが自動的に削除された場合に、そのデータへのアクセス権の再取得方法に関する追加のガイダンスがエンド ユーザーに示されます。<!--, or the removal of the Intune Company Portal on Android.-->

#### <a name="company-portal-for-ios-links-open-inside-the-app---665954--"></a>iOS 用ポータル サイトのリンクをアプリ内で開く <!--665954-->
iOS 用ポータル サイト内のリンク (ドキュメントとアプリへのリンクを含む) は、Safari のアプリ内ビューを使用して、ポータル サイト アプリに直接開きます。 この更新プログラムは、1 月にサービス更新プログラムとは別に提供されます。

#### <a name="modernizing-the-company-portal-website---753980--"></a>ポータル Web サイトの進化 <!--753980-->
2 月から、ポータル Web サイトで管理対象のデバイスを持っていないユーザーを対象とするアプリをサポートします。 この Web サイトは、新しいコントラストの配色パターン、動的な図、および "ハンバーガー メニュー"  ![ポータル サイトのハンバーガー メニュー](./media/CP_hamburger_menu.png)。

#### <a name="new-documentation-for-app-protection-policies---583398--"></a>アプリの保護ポリシーに関する新しいドキュメント <!--583398-->
Intune アプリ ラッピング ツールまたは Intune アプリ SDK を使用して、iOS および Android アプリでアプリ保護ポリシー (MAM ポリシーとして知られる) を有効にする必要がある管理者やアプリ開発者用のドキュメントを更新しました。

次の記事が更新されました。

* [Microsoft Intune によるモバイル アプリケーション管理のためにアプリを準備する方法を決める](apps-prepare-mobile-application-management.md)
* [Intune アプリ ラッピング ツールでモバイル アプリケーションを管理するために iOS アプリを準備する](app-wrapper-prepare-ios.md)
* [Microsoft Intune アプリ SDK の概要](/app-sdk-get-started.md)
* [iOS 用 Intune アプリ SDK 開発者ガイド](app-sdk-ios.md)

次の記事がドキュメント ライブラリに新たに追加されました。

* [Intune App SDK Cordova プラグイン](app-sdk-cordova.md)
* [Intune App SDK Xamarin コンポーネント](app-sdk-xamarin.md)

#### <a name="progress-bar-when-launching-the-company-portal-on-ios---665978--"></a>iOS でのポータル サイトの起動時の進行状況バー <!--665978-->
iOS 用ポータル サイトでは、ユーザーに発生する読み込みプロセスに関する情報を提供する進行状況バーが起動画面に導入されています。 進行状況バーは段階的にロールアウトされ、スピンと置き換えられます。 これは、一部のユーザーには新しい進行状況バーが表示され、他のユーザーにはスピンが引き続き表示されることを意味します。

## <a name="december-2016"></a>2016 年 12 月

### <a name="public-preview-of-intune-in-the-azure-portal--736542--"></a>Azure Portal での Intune のパブリック プレビュー<!--736542-->
2017 年初めには、すべての管理者エクスペリエンスが Azure に移行され、Graph API を幅広く使用する最新のサービス プラットフォーム上で、EMS の中核的ワークフローの強力な統合管理を利用できるようになります。 すべての Intune テナントでこのポータルが広く利用できるようになりますが、それに先立ち、今月中にこの新しい管理者エクスペリエンスのプレビューを一部のテナントに提供することを謹んでお伝えします。

Azure Portal の管理者エクスペリエンスでは、既に発表されている新しいグループ化とターゲット設定の機能が使用されます。既存のテナントを新しいグループ化エクスペリエンスに移行すると、テナントの管理者エクスペリエンスも新しいプレビュー版に移行されます。 それまでの間、Azure Portal で Microsoft Intune のために用意しているものを[新しいドキュメント](/intune/what-is-intune)でご確認いただけます。

__Azure Portal のパブリック プレビューでの電気通信経費管理の統合__ <!--747605--> Azure Portal では、サード パーティの電気通信経費管理 (TEM) サービスとの統合のプレビューが始められています。 Intune を使用して、国内およびローミングのデータ使用量を制限できます。 これらの統合は、[Saaswedo](http://www.saaswedo.com/) で始まっています。 試用テナントでこの機能を有効にする場合は、[Microsoft サポートにお問い合わせください](/intune-classic/troubleshoot/how-to-get-support-for-microsoft-intune)。

### <a name="new-capabilities"></a>新しい機能

__すべてのプラットフォームでの多要素認証__ <!--747590--> Azure Active Directory で Microsoft Intune 登録アプリケーションに多要素認証 (MFA) を構成することにより、Azure の管理ポータルから iOS、Android、Windows 8.1+、または Windows Phone 8.1+ デバイスを登録すると、選択したユーザー グループに MFA を適用できます。

__モバイル デバイス登録を制限する機能__ <!--747596--> Intune では、登録を許可されるモバイル デバイス プラットフォームを制御する新しい登録制限が追加されています。 Intune では、モバイル デバイス プラットフォームが iOS、macOS、Android、Windows、Windows Mobile に分かれています。
* モバイル デバイスの登録を制限しても、PC クライアントの登録は制限されません。
* iOS のみについては、個人所有デバイスの登録をブロックする 1 つの追加オプションがあります。

[この記事](/intune-classic/deploy-use/manage-corporate-owned-devices)で説明されているように、IT 管理者が明示的に会社所有と指定しない限り、Intune はすべての新しいデバイスを個人所有としてマークします。

### <a name="notices"></a>通知

__Azure Portal に移動する登録での多要素認証__ <!--VSO 750545--> これまで、Intune の登録に MFA を設定するには、Intune コンソールまたは構成マネージャー (2016 年 10 月のリリースより前) コンソールを使用しました。 この機能更新により、今後は Intune の資格情報で [Microsoft Azure Portal ](https://manage.windowsazure.com)にログインし、Azure AD を使用して MFA の設定を構成するようになります。 詳細については、[こちら](https://aka.ms/mfa_ad)をご覧ください。

__Android 用ポータル サイト アプリが中国で利用可能になる__ <!--VSO 658093--> Android 用ポータル サイト アプリが中国でダウンロードできるようになりました。 中国には Google Play ストアがないので、Android デバイスは中国のアプリ マーケットプレースからアプリを入手する必要があります。 Android 用ポータル サイト アプリは、以下のストアでダウンロードできます。
* [Baidu](https://go.microsoft.com/fwlink/?linkid=836946)
* [Huawei](https://go.microsoft.com/fwlink/?linkid=836948)
* [Tencent](https://go.microsoft.com/fwlink/?linkid=836949)
* [Wandoujia](https://go.microsoft.com/fwlink/?linkid=836950)
* [Xiaomi](https://go.microsoft.com/fwlink/?linkid=836947)

Android 用ポータル サイト アプリは、Google Play 開発者サービスを使って Microsoft Intune サービスと通信します。 中国では Google Play 開発者サービスをまだ利用できないので、次のタスクには最大 8 時間かかることがあります。 

|Intune 管理コンソール| Android 用 Intune ポータル サイト アプリ |Intune ポータル サイト Web サイト|   
|---|---|---|
|フル ワイプ| リモート デバイスの削除| デバイスの削除 (ローカルおよびリモート)|
|選択的ワイプ| デバイスのリセット| デバイスのリセット|
|新規アプリまたは更新アプリの展開| 使用可能な基幹業務アプリのインストール| デバイスのパスコードのリセット|
|リモート ロック|||
|パスコードのリセット|||

### <a name="deprecations"></a>廃止予定

__Firefox による Silverlight のサポート終了__ <!--VSO TBA--> Mozilla では、2017 年 3 月をもって、[Firefox ブラウザー](https://www.mozilla.org/firefox)のバージョン 52 で Silverlight のサポートを終了します。 結果として、バージョンが 51 より後の Firefox では既存の Intune コンソールにログインできなくなります。 管理コンソールにアクセスするときは、Internet Explorer 10 または 11 を使用するか、[バージョンが 52 より前の Firefox](https://ftp.mozilla.org/pub/firefox/releases/) を使用することが推奨されます。 Intune を Azure Portal に移行することで、Silverlight を利用しなくてもさまざまな[最新ブラウザー](/azure/azure-preview-portal-supported-browsers-devices)に対応します。

__Exchange Online モバイル受信トレイ ポリシーの削除__ <!--770687--> 12 月以降、管理者は Intune コンソールで Exchange Online (EAS) モバイル メールボックス ポリシーを表示または構成できなくなります。 この変更は、12 月から 1 月にかけてすべての Intune テナントに展開されます。 既存のすべてのポリシー構成は今までどおりですが、新しいポリシーの構成には Exchange 管理シェルを使います。 詳しくは、[こちら](https://technet.microsoft.com/library/bb123783%28v=exchg.150%29.aspx)をご覧ください。

__Android での Intune AV Player、Image Viewer、PDF Viewer アプリのサポート終了__<!--747553--> 2016 年 12 月中旬以降、Intune AV Player、Image Viewer、PDF Viewer の各アプリが使用できなくなります。 これらのアプリの代わりに、Azure Information Protection アプリが使用できるようになります。 Azure Information Protection アプリについて詳しくは、[こちら](/information-protection/rms-client/mobile-app-faq)をご覧ください。

## <a name="november-2016"></a>2016 年 11 月

### <a name="new-capabilities"></a>新しい機能

__Windows 10 デバイスで使用可能な新しい Microsoft Intune ポータル サイト__ Microsoft は、[Windows 10 デバイス用に新しい Microsoft Intune ポータル サイト アプリ](https://www.microsoft.com/store/apps/9wzdncrfj3pz)をリリースします。 このアプリでは新しい Windows 10 ユニバーサル形式を利用します。このアプリ内ではユーザーに対して更新されたユーザー エクスペリエンスが提供され、すべての Windows 10 デバイスで同じエクスペリエンスが提供されます。現在使用されている機能はすべて引き続き利用できます。

この新しいアプリでは、ユーザーは、Windows 10 デバイスでのシングル サインオン (SSO) や証明書ベースの認証など、追加のプラットフォーム機能も利用することができます。 アプリは、Microsoft ストアからインストールした既存の Windows 8.1 ポータル サイトと Windows Phone 8.1 ポータル サイトへのアップグレードとして利用可能になります。 詳細については、[aka.ms/intunecp_universalapp](http://aka.ms/intunecp_universalapp) を参照してください。

> [!IMPORTANT]
> __Intune と Android for Work の更新プログラム__ __[必須]__ の操作を使用して Android for Work アプリを展開できますが、Intune グループが新しい Azure AD グループ エクスペリエンスに移行された場合、__[利用可能]__ としてのみアプリを展開できます。

__Cordova プラグイン用 Intune アプリ SDK で登録なしの MAM をサポート開始__ アプリ開発者は、Cordova プラグイン用 Intune アプリ SDK を使用して、Android および iOS 用の Cordova ベースのアプリでデバイス登録を行わずに MAM 機能を有効化できるようになりました。 Cordova プラグイン用の Intune アプリ SDK は[こちら](https://github.com/msintuneappsdk/cordova-plugin-ms-intune-mam)にあります。

__Intune アプリ SDK Xamarin コンポーネントで登録なしの MAM のサポート開始__ アプリ開発者は、Intune アプリ SDK Xamarin コンポーネントを使用して、Android および iOS 用の Xamarin ベースのアプリでデバイス登録を行わずに MAM 機能を有効化できるようになりました。 Intune アプリ SDK Xamarin コンポーネントは[こちら](https://github.com/msintuneappsdk/intune-app-sdk-xamarin)にあります。

### <a name="notices"></a>通知

__Symantec 署名証明書のアップロードで署名済みの Windows Phone 8 ポータル サイトが不要に__ Symantec 署名証明書のアップロード時に、署名済みの Windows Phone 8 ポータル サイト アプリが不要になりました。 証明書は単独でアップロードできます。

###<a name="deprecations"></a>廃止予定

__Windows Phone 8 ポータル サイトのサポート__ Windows Phone 8 ポータル サイトのサポートは廃止されます。 2016 年 10 月に Windows Phone 8 プラットフォームおよび Windows RT プラットフォームのサポートが廃止されました。 また、2016 年 10 月に Windows Phone 8 ポータル サイトのサポートも廃止されました。


### <a name="see-also"></a>関連項目
最近の開発状況について詳しくは、「[Microsoft Intune の新機能](whats-new.md)」をご覧ください。
