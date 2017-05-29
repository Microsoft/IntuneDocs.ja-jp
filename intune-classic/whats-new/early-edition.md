---
title: "初期エディション | Microsoft Docs"
description: 
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 05/04/2017
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
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 249a902e6e10f799dcff4e1c46da90cd62f2c125
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017


---

# <a name="the-early-edition-for-microsoft-intune---may-2017"></a>Microsoft Intune の初期エディション - 2017 年 5 月

**初期エディション**では、Microsoft Intune の今後のリリースで予定されている新機能を一覧します。 ここに記載されている情報は、秘密保持契約書のもとごく限られた範囲について開示されたものであり、また今後変更される可能性があります。 ここに挙げられている機能は、発売日に間に合わない可能性があり、その場合は将来のリリースを待たなければなりません。 正式なリリースに向けてパイロット (フライト) テスト中の機能もあります。 ご不明な点や懸念される事項がある場合は、Intune の開発チームまたは PM にお問い合わせください。

このページは定期的に更新されます。 適宜確認してください。

> [!Note]
> Intune に関して以下の機能が現在開発されています。 これらのすべての機能は、最終的にハイブリッド環境 (Configuration Manager と Intune の共存環境) でサポートされるようになります。 最新のハイブリッド機能の詳細については、[ハイブリッド環境の新機能に関するページ](https://docs.microsoft.com/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)を参照してください。

## <a name="new-capabilities"></a>新しい機能

### <a name="single-sign-on-support-from-the-company-portal-for-ios-to-outlook-for-ios---834012--"></a>iOS 用のポータル サイトおよび Outlook からのシングル サインオンのサポート <!--834012-->

iOS 用のポータル サイト アプリに既にサインインしているユーザーは、同じデバイス上の同じアカウントを使う Outlook アプリであればサインインしなおす必要はありません。 Outlook アプリを起動するときに、自分のアカウントを選んで自動的にサインインできます。 現在、他の Microsoft アプリにこの機能を追加する作業を進めています。

### <a name="improved-notification-for-samsung-knox-startup-pins---1087143--"></a>Samsung KNOX 起動 PIN の通知機能強化 <!--1087143-->

暗号化に対応する目的でエンド ユーザーが Samsung KNOX デバイスに起動 PIN を設定する必要があるとき、エンド ユーザーに表示される通知をタップすると、設定アプリ内の設定場所に移動します。  以前は、エンド ユーザーは通知からパスワード変更画面に進むことができました。

### <a name="promoting-the-most-current-version-of-the-company-portal-for-android---1098661--"></a>Company Portal for Android の最新版の奨励 <!--1098661-->

アプリの通知画面で、Company Portal for Android アプリの最新推奨版がリリースされたとき、エンド ユーザーにアプリ内通知が表示されます。 この通知はユーザーに "ポータル サイトの更新版が利用できる" ことを伝えます。 通知をタップすると、Web ページが開きます。そのページに、更新版をダウンロードできるアプリ ストアの一覧が表示されます。 

### <a name="improvements-to-app-syncing-with-windows-10-creators-update----676505---"></a>Windows 10 Creators Update とアプリを同期する機能の強化 <!-- 676505 -->

Company Portal for Windows 10 は、Windows 10 Creators Update (1704) がインストールされているデバイスのアプリ インストール要求の同期を自動的に開始します。 "同期保留中" 状態中、アプリ インストールが止まる問題を減らします。 また、ユーザーはアプリ内から同期を手動で開始できます。 

Company Portal for Windows 10 には、更新ボタンもあります。ユーザーは必要なときにアプリのコンテンツを更新できます。 

## <a name="notices"></a>通知

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple の要求による Application Transport Security 対応のための更新<!--748318-->

Apple は、2017 年春より Application Transport Security (ATS) の特定の要件を適用すると発表しました。 ATS では、HTTPS 経由で行われるアプリ通信すべてに、より厳格なセキュリティ保護が適用されます。 この変更により、iOS ポータル サイト アプリを使用している Intune ユーザーが影響を受けます。 詳細については、[Intune サポートのブログ](https://aka.ms/compportalats)をご覧ください。

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Apple 登録シナリオへの直接アクセス <!--951869-->

Intune では、2017 年 1 月以降に作成された Intune アカウントについて、Azure プレビュー ポータルの Enroll Devices ワークロードを使用して、Apple 登録シナリオに直接アクセスできるようになりました。 これまでは、Apple 登録プレビューはクラシックの Intune ポータルのリンクからのみアクセスが可能でした。 2017 年 1 月より前に作成された Intune アカウントの場合は、これらの機能が Azure で利用可能になるまでの間、1 回限りの移行が必要です。 移行スケジュールはまだ発表されていませんが、詳細はできる限り早く発表します。 既存のアカウントでプレビューにアクセスできない場合は、試用アカウントを作成して、新しいエクスペリエンスをテストすることを強くお勧めします。

### <a name="whats-coming-for-appx-in-intune-on-azure----1000270---"></a>Intune on Azure での appx に予定されている新機能 <!-- 1000270 -->

Intune on Azure への移行の一環として、appx に関して次の 3 つの変更が行われています。

1. MDM 登録デバイスに対してのみ展開できる新しい appx アプリの種類を、クラシック Intune コンソールに追加します。
2. 既存の appx アプリの種類を、Intune PC エージェントによって管理される PC のみを対象とするように用途を変更します。
3. 移行において、すべての既存 appx を MDM appx に変換します。

Intune PC エージェントによって管理されるデバイスへの既存の展開に対する影響はありません。 ただし、移行後に、これらの移行された appx を、Intune PC エージェントによって管理される、以前は対象になっていなかった新しいデバイスに展開することはできません。

移行終了後、新しい PC 展開を行いたい場合は、appx を PC appx として再アップロードする必要があります。 詳しくは、Intune サポート チーム ブログの「[Appx changes in Intune on Azure](https://aka.ms/appxchange)」 (Intune on Azure での appx の変更) をご覧ください。  


## <a name="public-preview-of-the-new-intune-admin-experience-on-azure---736542--"></a>Azure での新しい Intune 管理者エクスペリエンスのパブリック プレビュー <!--736542-->

2017 年初めには、すべての管理者エクスペリエンスが Azure に移行され、Graph API を幅広く使用する最新のサービス プラットフォーム上で、EMS の中核的ワークフローの強力な統合管理を利用できるようになります。

今月には、Azure Portal で新しい管理者エクスペリエンスのパブリック プレビューを表示する新しい試用テナントが開始されます。 プレビュー状態では、既存の Intune コンソールでの機能とパリティが繰り返し提供されます。

Azure Portal の管理者エクスペリエンスでは、既に発表されている新しいグループ化とターゲット設定の機能が使用されます。既存のテナントを新しいグループ化エクスペリエンスに移行すると、テナントの管理者エクスペリエンスも新しいプレビュー版に移行されます。 テナントを移行する前に、新しい機能をテストしたり見たりしたい場合は、新しい Intune 試用版アカウントにサインアップするか、[新しいドキュメント](https://docs.microsoft.com/intune/what-is-intune)をご覧ください。

### <a name="support-for-managed-configuration-options-for-android-apps----621621---"></a>Android アプリ向けの管理対象構成オプションのサポート<!-- 621621 -->

管理対象構成オプションをサポートする Play ストアの Android アプリを構成できます。  この機能は、アプリによってサポートされる構成値の一覧を表示できるようにし、値を構成できるガイド付きの使いやすい UI を提供します。

### <a name="remote-assistance-for-android-devices----675418---"></a>Android デバイスのリモート アシスタンス <!-- 675418 -->

Intune では、別売りの [TeamViewer](https://www.teamviewer.com) ソフトウェアを利用して、Android デバイスを使用するユーザーにリモート アシスタンスを提供できます。

### <a name="preconfigure-device-permissions-for-android-for-work-apps----621614---"></a>Android for Work アプリのデバイス アクセス許可の事前構成 <!-- 621614 -->

Android for Work デバイス作業プロファイルに展開したアプリの場合、個々のアプリのアクセス許可状態を構成できます。 既定では、場所やデバイス カメラへのアクセスなど、デバイスのアクセス許可を必要とする Android アプリはアクセス許可の承諾または拒否をユーザーに求めます。  たとえば、アプリでデバイスのマイクが使用される場合、そのマイクを使用するアクセス許可をアプリに与えるようにエンド ユーザーに求められます。 この機能を利用すると、エンド ユーザーの代わりにアクセス許可を定義できます。  管理者は次のアクセス許可を構成できます。

- ユーザーに通知することなく自動的に拒否する
- ユーザーに通知することなく自動的に承諾する
- 承諾または拒否をユーザーに求める

### <a name="define-app-specific-pin-for-android-for-work-devices---728976--"></a>Android for Work デバイスのアプリ固有 PIN を定義する <!--728976-->

Android for Work デバイスとして管理されている Android 7.0 以上のデバイスの作業プロファイルで、アプリにのみ適用されるパスコード ポリシーを定義できます。  次のオプションがあります。

- デバイス全体のパスコード ポリシーだけを定義する - これは、デバイス全体のロックを解除するためにエンド ユーザーが使用しなければならないパスコードです。
- 作業プロファイルのパスコード ポリシーだけを定義する - 作業プロファイルのアプリを起動するたびに、エンド ユーザーにパスコードの入力が求められます。
- デバイスと作業プロファイル ポリシーの両方を定義する - IT 部署はデバイスのパスコード ポリシーと作業プロファイルのパスコード ポリシーのいずれも異なる強度で定義できます。たとえば、デバイスのロック解除に 4 桁の PIN を要求し、作業アプリの起動に 6 桁の PIN を要求します。

>[!NOTE]
> この機能は Android 7.0 以降でのみ利用できます。  既定では、エンド ユーザーは別々に定義された 2 つの PIN を利用できます。あるいは、定義された 2 つの PIN のうちの強いほうを選択できます。

### <a name="manage-password-and-other-android-for-work-settings---1102534--"></a>パスワードとその他の Android for Work 設定の管理 <!--1102534-->

Android for Work デバイスでのパスワードと仕事用プロファイルの設定を管理できる、新しい Android for Work デバイス制限ポリシーを追加しました。

###  <a name="new-web-content-filter-policy-for-ios-devices----723832---"></a>iOS デバイス用の新しい Web コンテンツ フィルター ポリシー <!-- 723832 -->

iOS デバイスのユーザーがアクセスできる Web サイトを次の 2 つの方法を使って制御できます。

  - Apple の組み込み Web コンテンツ フィルターを使って、許可される URL またはブロックされる URL を追加します。
  - Safari ブラウザーによるアクセスを許可する Web サイトを指定します。 指定した各サイトについて、Safari にブックマークが作成されます。

### <a name="apple-school-manager-asm-support---748864--"></a>Apple School Manager (ASM) サポート <!--748864-->

Intune では、Apple Device Enrollment Program の代わりに Apple School Manager (ASM) を使用できるようになりました。すぐに iOS デバイスを登録できます。 共有 iPad で Classroom アプリを使用するには ASM オンボードが必要です。これは、Microsoft School Data Sync (SDS) 経由で ASM から Azure Active Directory へのデータ同期を有効にする際にも必要です。  

### <a name="shared-ipad-support---770395-1044681---"></a>共有 iPad サポート <!--770395, 1044681 -->

Intune では、Apple の Device Enrollment Program または Apple School Manager の登録プロファイルで共有 iPad モードを構成できます。 この設定では、管理されている複数の Apple ID で同じデバイスにサインインできます。

Microsoft はまた、自分で管理している Apple ID を利用して共有 iPad にログインする生徒を追加するために、iOS Classroom アプリの管理サポートを拡張しています。

### <a name="new-windows-device-restriction-settings---978585--"></a>新しい Windows デバイス制限設定 <!--978585-->

Microsoft は、無線ディスプレイ、デバイス検出、タスク切り替え、SIM カード エラー メッセージなどの機能を制御する設定を Windows デバイス制限プロファイルに追加しています。

### <a name="office-365-proplus-app-available-for-windows-10-devices---1121362--"></a>Windows 10 デバイスで Office 365 ProPlus アプリが使用可能に <!--1121362-->

Microsoft は新しい種類の Office 365 ProPlus アプリを追加します。Office 365 ProPlus アプリを Windows 10 デバイスに割り当てる作業が簡単になります。 また、ライセンスを所有している場合、Microsoft Project や Microsoft Visio をインストールすることもできます。 必要なアプリがバンドルされ、Intune コンソールのアプリ一覧に 1 つのアプリとして表示されます。

### <a name="new-allowblock-list-for-the-managed-browser---682960--"></a>Managed Browser 用の新しい許可/禁止リスト <!--682960-->

Azure Portal の Intune アプリケーション構成設定で Managed Browser のドメインと URL の許可/禁止リストを構成できます。 管理されているデバイスで使用されているか、管理されていないデバイスで使用されているかに関係なく、Managed Browser に対して構成できます。

### <a name="new-app-configuration-capabilities----677969---"></a>新しいアプリ構成機能 <!-- 677969 -->

この機能はモバイル デバイス管理 (MDM) のアプリ構成に相当します。 管理者は登録チャネルなしで、MAM のアプリ保護ポリシーで利用できるアプリ構成値以上のアプリ構成値を適用できます。

### <a name="new-app-protection-policies-conditions-for-mam---679864--"></a>MAM の新しいアプリ保護ポリシー条件 <!--679864-->

登録ユーザーなしで、次を強制する MAM の要件を管理コンソール経由で設定できます。

- アプリケーションの最小バージョン
- オペレーティング システムの最小バージョン
- 対象アプリケーションの最小 Intune APP SDK バージョン (iOS のみ)

この機能は、Android と iOS の両方で使うことができます。 Intune は、OS プラットフォーム バージョン、アプリケーション バージョン、Intune APP SDK の最小バージョン強制に対応しています。 iOS の場合、SDK が統合されているアプリケーションでも SDK レベルで最小バージョン強制を設定できます。

アプリ保護ポリシーの最小要件が上述の 3 つの異なるレベルで満たされていない場合、ユーザーは対象アプリケーションにアクセスできません。 この時点で、ユーザーはアカウントを削除するか (複数 ID アプリケーションの場合)、アプリケーションを閉じるか、OS またはアプリケーションのバージョンを更新して要件を満たすことができます。

さらに、管理コンソールで、OS またはアプリケーションのアップグレードを推奨するブロック不可の通知を表示するように追加設定することもできます。 この通知は閉じて、アプリケーションを普段どおり使用できます。

### <a name="change-your-mdm-authority-without-unenrolling-managed-devices---1103950--"></a>管理対象デバイスの登録を解除せず、MDM 機関を変更する <!--1103950-->

Microsoft サポートに問い合わせずに、また、既存の管理対象デバイスの登録解除と再登録を行わずに MDM 機関を変更できます。 Configuration Manager コンソールで、[Configuration Manager に設定] (ハイブリッド) から [Microsoft Intune] (スタンドアロン) に、またはその逆に MDM 機関を変更できます。


### <a name="see-also"></a>関連項目
最近の開発状況について詳しくは、「[Microsoft Intune の新機能](whats-new-in-microsoft-intune.md)」をご覧ください。

