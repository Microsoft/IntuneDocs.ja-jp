---
title: "初期エディション | Microsoft Docs"
description: 
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 04/25/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 5f172290d493717308446c4f9e2313a03ba8f3aa
ms.openlocfilehash: d7f25657fc7cfb9298809f76f198810718e58c39
ms.lasthandoff: 04/27/2017


---


# <a name="the-early-edition-for-microsoft-intune---april-2017"></a>Microsoft Intune の初期エディション - 2017 年 4 月

**初期エディション**では、Microsoft Intune の今後のリリースで予定されている新機能を一覧します。 ここに記載されている情報は、秘密保持契約書のもとごく限られた範囲について開示されたものであり、また今後変更される可能性があります。 ここに挙げられている機能は、発売日に間に合わない可能性があり、その場合は将来のリリースを待たなければなりません。 正式なリリースに向けてパイロット (フライト) テスト中の機能もあります。 ご不明な点や懸念される事項がある場合は、Intune の開発チームまたは PM にお問い合わせください。

このページは定期的に更新されます。 適宜確認してください。

> [!Note]
> Intune に関して以下の機能が現在開発されています。 これらのすべての機能は、最終的にハイブリッド環境 (Configuration Manager と Intune の共存環境) でサポートされるようになります。 最新のハイブリッド機能の詳細については、[ハイブリッド環境の新機能に関するページ](https://docs.microsoft.com/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)を参照してください。

## <a name="new-capabilities"></a>新しい機能

### <a name="improved-app-install-status-for-the-windows-10-company-portal-app---676495--"></a>Windows 10 ポータル サイト アプリのアプリ インストール状態の向上<!--676495-->

Windows 10 のポータル サイト アプリでは、ポータル サイトから開始されたすべての最新アプリのインストールに対し、アプリ インストール進行状況バーが表示されようになります。 Windows 10 のポータル サイト アプリの新しい状態メッセージは、[Windows 10 アプリ UI の新機能に関するページ](whats-new-in-intune-app-ui.md)で見ることができます。

### <a name="improved-status-messaging-in-the-company-portal-app-for-ios---744866--"></a>iOS 用ポータル サイト アプリでの状態メッセージの向上<!--744866-->

デバイスで起きていることがよくわかる情報を提供する、新しい具体的なエラー メッセージが iOS 用のポータル サイト アプリに表示されるようになります。 これらのエラー情報は、これまでは "ポータル サイトは一時的に使用できません" というタイトルの一般的なエラー メッセージに含まれていました。 さらに、ユーザーがインターネットに接続できないときに iOS でポータル サイトを開始した場合は、"インターネットに接続されていません" という内容の固定ステータス バーがホーム ページに表示されるようになります。

### <a name="myapps-available-for-managed-browser---822308-822303--"></a>Managed Browser に使用できる MyApps <!--822308, 822303-->

Managed Browser での Microsoft MyApps のサポートが向上します。 管理の対象になっていない Managed Browser ユーザーは、MyApps サービスに直接送られ、そこで管理者がプロビジョニングした SaaS アプリにアクセスできます。 Intune の管理の対象になっているユーザーは、引き続き組み込みの Managed Browser ブックマークから MyApps にアクセスできます。

### <a name="new-icons-for-the-managed-browser-and-the-company-portal---918433-918431--"></a>Managed Browser とポータル サイトの新しいアイコン <!--918433, 918431-->

Managed Browser の Android バージョンと iOS バージョンのアイコンが更新されます。 新しいアイコンには、Enterprise Mobility + Security (EM+S) での他のアプリとの一貫性が向上した新しい Intune バッジが含まれます。 Managed Browser 用の新しいアイコンは、[Intune アプリ UI の新機能に関するページ](whats-new-in-intune-app-ui.md)でご覧いただけます。

Android、iOS、Windows でのポータル サイト アプリのアイコンも更新されて、EM+S での他のアプリとの一貫性が向上します。 これらのアイコンは、4 月から 5 月末にかけて段階的にプラットフォーム全体にリリースされます。

### <a name="single-sign-on-support-from-the-company-portal-for-ios-to-outlook-for-ios---834012--"></a>iOS 用のポータル サイトおよび Outlook からのシングル サインオンのサポート <!--834012-->

iOS 用のポータル サイト アプリに既にサインインしているユーザーは、同じデバイス上の同じアカウントを使う Outlook アプリであればサインインしなおす必要はありません。 Outlook アプリを起動するときに、自分のアカウントを選んで自動的にサインインできます。 現在、他の Microsoft アプリにこの機能を追加する作業を進めています。

### <a name="sign-in-progress-indicator-in-android-company-portal---953374--"></a>Android 用ポータル サイトでのサインイン進行状況インジケーター<!--953374-->

Android 用ポータル サイト アプリが更新されて、起動または再開時にサインイン進行状況インジケーターが表示されるようになります。 ユーザーがアプリへのアクセスを許可されるまでにインジケーターに順番に表示される新しいステータスは、[接続中...]、[サインイン中...]、[Checking for security requirements... (セキュリティ要件確認中...)] です。 Android 用ポータル サイト アプリの新しい画面は、[Intune アプリ UI の新機能に関するページ](whats-new-in-intune-app-ui.md)でご覧いただけます。


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

#### <a name="how-does-this-affect-me"></a>ユーザーへの影響

Intune PC エージェントによって管理されるデバイスへの既存の展開に対する影響はありません。 ただし、移行後に、これらの移行された appx を、Intune PC エージェントによって管理される、以前は対象になっていなかった新しいデバイスに展開することはできません。

#### <a name="what-action-do-i-need-to-take"></a>実行する必要があるアクション

移行終了後、新しい PC 展開を行いたい場合は、appx を PC appx として再アップロードする必要があります。 詳しくは、Intune サポート チーム ブログの「[Appx changes in Intune on Azure](https://aka.ms/appxchange)」 (Intune on Azure での appx の変更) をご覧ください。  


## <a name="public-preview-of-the-new-intune-admin-experience-on-azure---736542--"></a>Azure での新しい Intune 管理者エクスペリエンスのパブリック プレビュー <!--736542-->

2017 年初めには、すべての管理者エクスペリエンスが Azure に移行され、Graph API を幅広く使用する最新のサービス プラットフォーム上で、EMS の中核的ワークフローの強力な統合管理を利用できるようになります。

今月には、Azure Portal で新しい管理者エクスペリエンスのパブリック プレビューを表示する新しい試用テナントが開始されます。 プレビュー状態では、既存の Intune コンソールでの機能とパリティが繰り返し提供されます。

Azure Portal の管理者エクスペリエンスでは、既に発表されている新しいグループ化とターゲット設定の機能が使用されます。既存のテナントを新しいグループ化エクスペリエンスに移行すると、テナントの管理者エクスペリエンスも新しいプレビュー版に移行されます。 テナントを移行する前に、新しい機能をテストしたり見たりしたい場合は、新しい Intune 試用版アカウントにサインアップするか、[新しいドキュメント](https://docs.microsoft.com/intune-azure/introduction/what-is-microsoft-intune)をご覧ください。

### <a name="support-for-managed-configuration-options-for-android-apps----621621---"></a>Android アプリ向けの管理対象構成オプションのサポート<!-- 621621 -->

管理対象構成オプションをサポートする Play ストアの Android アプリを、Intune で構成できます。  この機能は、アプリによってサポートされる構成値の一覧を表示できるようにし、値を構成できるガイド付きの使いやすい UI を提供します。

### <a name="remote-assistance-for-android-devices----675418---"></a>Android デバイスのリモート アシスタンス <!-- 675418 -->

Intune では、別売りの [TeamViewer](https://www.teamviewer.com) ソフトウェアを利用して、Android デバイスを使用するユーザーにリモート アシスタンスを提供できます。

### <a name="new-android-policy-for-complex-pins----722069---"></a>複雑な暗証番号 (PIN) に対する新しい Android ポリシー <!-- 722069 -->

Android 5.0 以降を搭載しているデバイスの Android デバイス プロファイルに必要な数値複素数タイプのパスワードを設定できます。  反復する値や連続する値 (1111 や 1234 など) を含む暗証番号 (PIN) をデバイスのユーザーが作成しないようにするには、この設定を使います。

### <a name="additional-support-for-android-for-work-devices"></a>Android for Work デバイスの追加サポート

- **パスワードと仕事用プロファイルの設定を管理する** <!-- 612808 -->

  管理対象の Android for Work デバイスでのパスワードと仕事用プロファイルの設定を管理できる、新しい Android for Work デバイス制限ポリシーを追加しました。

- **仕事用プロファイルと個人プロファイル間でのデータ共有を許可する** <!-- 1045102 -->

  Android for Work デバイス制限プロファイルの **[仕事用プロファイルと個人プロファイル間のデータ共有]** の設定を更新し、仕事用プロファイルと個人プロファイルの間でのデータ共有の構成を支援する新しいオプションを加えました。

- **仕事用プロファイルと個人プロファイルの間でのコピーと貼り付けを制限する** <!-- 1046094 -->

  Intune で Android for Work デバイスを管理するときは、仕事用アプリと個人用アプリの間でのコピーおよび貼り付け操作が許可されます。 仕事用アプリと個人用アプリの間でのコピーおよび貼り付け操作を許可するかどうかを制限できる、Android for Work デバイス用のカスタム デバイス プロファイルを追加しました。

### <a name="assign-lob-apps-to-ios-and-android-devices----1057568---"></a>iOS デバイスと Android デバイスに LOB アプリを割り当てる <!-- 1057568 -->

iOS 用 (.ipa ファイル) および Android 用 (.apk ファイル) の基幹業務アプリを、ユーザーまたはデバイスに割り当てることができます。

###  <a name="new-policies-for-ios-devices----723774-723815-723826-723830-723832---"></a>iOS デバイス用の新しいポリシー <!-- 723774, 723815, 723826, 723830, 723832 -->

- **ホーム画面のアプリ** - デバイス ポリシーを使って、iOS デバイスのホーム画面に表示されるアプリを制御できます。 このポリシーは、ホーム画面のレイアウトを変更しますが、管理者によって指定されたインストールされていないアプリの展開は行いません。

- **AirPrint デバイスへの接続** - Intune のデバイス ポリシーを使って、iOS デバイスのエンド ユーザーが接続できる AirPrint デバイス (ネットワーク プリンター) を制御できます。

- **AirPlay デバイスへの接続** - Intune のデバイス ポリシーを使って、iOS デバイスのエンド ユーザーが接続できる AirPlay デバイス (Apple TV など) を制御できます。

- **ロック画面のカスタム メッセージ** - iOS デバイスのロック画面に表示されるユーザー向けの既定のロック画面メッセージの代わりに、カスタム メッセージを構成できます。

- **Web コンテンツ フィルター** - iOS デバイスのユーザーがアクセスできる Web サイトを、次の 2 つの方法を使って制御できます。

  - Apple の組み込み Web コンテンツ フィルターを使って、許可される URL またはブロックされる URL を追加します。
  - Safari ブラウザーによるアクセスを許可する Web サイトを指定します。 指定した各サイトについて、Safari にブックマークが作成されます。


### <a name="restrict-push-notifications-for-ios-apps----723767---"></a>iOS アプリのプッシュ通知を制限する <!-- 723767 -->

Intune のデバイス制限プロファイルでは、iOS デバイスに対する次の通知設定を構成できます。

- 指定したアプリの通知を完全に有効または無効にします。
- 指定したアプリの通知センターでの通知を有効または無効にします。
- アラートの種類を、**なし**、**バナー**、または**モーダル アラート**に指定します。
- このアプリに対してバッジを許可するかどうかを指定します。
- 通知サウンドを許可するかどうかを指定します。

### <a name="configure-ios-apps-to-run-in-single-app-mode-autonomously----737837---"></a>単一アプリ モードで自律的に実行するように iOS アプリを構成する<!-- 737837 -->

Intune のデバイス プロファイルを使って、自律単一アプリ モードで指定したアプリを実行するように iOS デバイスを構成できます。 このモードを構成した場合、指定したアプリが実行されると、デバイスはそのアプリだけを実行できるようにロックされます。 たとえば、ユーザーがデバイスでテストを受けられるようにアプリを構成するような場合です。 アプリのアクションが完了した場合、または管理者がこのポリシーを削除した場合、デバイスは通常の状態に戻ります。

### <a name="configure-trusted-domains-for-email-and-web-browsing-on-ios-devices----723765---"></a>iOS デバイスでメールと Web ブラウザー用の信頼されたドメインを構成する <!-- 723765 -->

iOS デバイス制限プロファイルでは、次のドメイン設定を構成できます。

- **[マークされていないメール ドメイン]** - ユーザーが送信または受信するメールのうち、ここで指定したドメインと一致しないものは、信頼されていないメールとしてマークされます。

- **[管理された Web ドメイン]** - ここで指定した URL からダウンロードされたドキュメントは、管理されているものと見なされます (Safari のみ)。  

- **[Safari パスワードの自動入力ドメイン]** - ユーザーは、ここで指定したパターンに一致する URL からのパスワードのみを Safari に保存できます。 この設定を使うには、デバイスが監視モードであり、複数ユーザー用に構成されていない必要があります。 (iOS 9.3 以降)


### <a name="vpp-apps-available-in-ios-company-portal----748782---"></a>iOS ポータル サイトで使用できる VPP アプリ <!-- 748782 -->

iOS ボリューム購入 (VPP) アプリを、エンド ユーザーが**利用可能な**インストールとして割り当てることができます。 エンド ユーザーがアプリをインストールするには、Apple ストア アカウントが必要です。

### <a name="synchronize-ebooks-from-apple-vpp-store----800878---"></a>Apple VPP ストアから電子ブックを同期する <!-- 800878 -->

Apple ボリューム購入プログラム ストアから購入した本を Intune と同期し、ユーザーに割り当てることができます。

### <a name="multi-user-management-for-samsung-knox-standard-devices----971988---"></a>Samsung KNOX Standard デバイスのマルチ ユーザー管理 <!-- 971988 -->

Samsung KNOX Standard を実行するデバイスが、Intune によるマルチ ユーザー サポートの対象になりました。 つまり、エンド ユーザーは Azure Active Directory の資格情報を使ってデバイスのサインインとサインアウトを行うことができ、デバイスは使用中かどうかに関わらず一元管理されます。  サインインしたエンド ユーザーはアプリにアクセスでき、適用されるポリシーをさらに受け取ります。 ユーザーがサインアウトすると、すべてのアプリ データがクリアされます。

### <a name="additional-windows-device-restriction-settings----818566---"></a>追加の Windows デバイス制限設定 <!-- 818566 -->

追加の Edge ブラウザー サポート、デバイス ロック画面のカスタマイズ、スタート メニューのカスタマイズ、Windows スポットライト検索セットの壁紙、プロキシ設定など、追加の Windows デバイス制限設定のサポートが追加されました。

### <a name="multi-user-support-for-windows-10-creators-update----822547---"></a>Windows 10 Creators Update のマルチユーザー サポート <!-- 822547 -->

Windows 10 Creators Update を実行し Azure Active Directory ドメインに参加しているデバイスのマルチユーザー管理のサポートが追加されました。 異なる標準ユーザーが Azure AD 資格情報でデバイスにログオンすると、ユーザー名に割り当てられているすべてのアプリとポリシーを受け取ります。 現時点では、アプリのインストールのようなセルフサービスのシナリオにポータル サイトは使用できません。

### <a name="fresh-start-for-windows-10-pcs---1004830---"></a>Windows 10 PC の Fresh Start <!-- 1004830 -->

このリリースでは、Windows 10 PC に新しい Fresh Start デバイス アクションが追加されました。  このアクションを発行すると、PC にインストールされたすべてのアプリが削除され、PC は Windows の最新バージョンに自動的に更新されます。 この機能は、新しい PC に付属することの多い事前インストール済み OEM アプリを削除するのに使うことができます。 このデバイス アクションを発行するときにユーザー データを保持するかどうかを構成できます。

### <a name="additional-windows-10-upgrade-paths----903672---"></a>Windows 10 の追加アップグレード パス <!-- 903672 -->

エディション アップグレード ポリシーを作成して、次のエディションの Windows 10 にもデバイスをアップグレードできるようになりました。

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N

### <a name="bulk-enroll-windows-10-devices----747607---"></a>Windows 10 デバイスを一括登録する <!-- 747607 -->

Windows Configuration Designer (WCD) を使用すると、Windows 10 Creators Update を実行する多数のデバイスを Azure Active Directory と Intune へ登録することができます。 Azure AD テナントの自動 MDM 登録を有効にするには、Windows Configuration Designer を使用してデバイスを Azure AD テナントに参加させるプロビジョニング パッケージを作成し、一括登録と管理の対象となる会社所有のデバイスにパッケージを適用します。 パッケージがデバイスに適用されると、デバイスは Azure AD に参加し、Intune に登録され、Azure AD ユーザーがログオンできる状態になります。  Azure AD ユーザーはこれらのデバイス上の標準ユーザーであり、割り当て済みのポリシーと必須アプリを受け取ります。 現時点では、セルフサービスとポータル サイトのシナリオはサポートされていません。

### <a name="new-mam-settings-for-pin-and-managed-storage-locations----58112-736644---"></a>暗証番号 (PIN) および管理対象記憶域の場所に対する新しい MAM 設定<!-- 58112, 736644 -->

モバイル アプリケーション管理 (MAM) シナリオに役立つ 2 つの新しいアプリ設定を使用できます。

- **[Disable app PIN when device PIN is managed (デバイスの PIN が管理されるときはアプリの PIN を無効にする)]** - 登録されたデバイスにデバイス暗証番号 (PIN) が存在するかどうかを検出し、存在する場合は、アプリ保護ポリシーによってトリガーされるアプリ PIN をバイパスします。 この設定を使うと、登録されたデバイスで MAM が有効なアプリケーションを開くユーザーに対して表示される PIN 要求の回数を減らすことができます。 この機能は、Android と iOS の両方で使うことができます。

- **[会社のデータを保存できるストレージ サービスの選択]** - 会社のデータを保存する記憶域の場所を指定できます。 ユーザーは選択したストレージ ロケーション サービスに保存できます。つまり、表示されていない他のすべてのストレージ ロケーション サービスはブロックされます。

  サポートされるストレージ ロケーション サービスの一覧は次のとおりです。

  - OneDrive
  - Business SharePoint Online
  - ローカル ストレージ


### <a name="see-also"></a>関連項目
最近の開発状況について詳しくは、「[Microsoft Intune の新機能](whats-new-in-microsoft-intune.md)」をご覧ください。

