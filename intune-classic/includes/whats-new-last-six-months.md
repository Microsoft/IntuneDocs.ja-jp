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

これらの変更について詳しくは、「[Intune とエンド ユーザー アプリの UI の更新](/intune-classic/whats-new/whats-new-in-intune-app-ui)」をご覧ください。

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
ポータル Web サイトで管理対象のデバイスを持っていないユーザーを対象とするアプリをサポートします。 この Web サイトは、新しいコントラストの配色パターン、動的な図、および "ハンバーガー メニュー"  ![(ヘルプデスクの連絡先詳細や既存の管理対象デバイスに関する情報を含む、](/intune-classic/whats-new/whats-new-in-intune-app-ui)。

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
Windows および Windows Phone のユーザーがデバイスを登録しようとして、MDM サーバー アドレスとして (入力を求められた場合に) __manage.microsoft.com__ を入力した場合、登録は失敗します。 MDM サーバー アドレスは、__manage.microsoft.com__ から __enrollment.manage.microsoft.com__ に変更されています。 Windows や Windows Phone デバイスの登録時に、MDM サーバー アドレスの入力を求められた場合は、__enrollment.manage.microsoft.com__ を使用するようにユーザーに通知してください。 CNAME 設定に変更は必要ありません。 この変更の詳細については、[aka.ms/intuneenrollsvrchange](https://aka.ms/intuneenrollsvrchange) を参照してください。

#### <a name="new-user-experience-for-the-company-portal-app-for-android---621622--"></a>Android 用ポータル サイト アプリに関する新しいユーザー エクスペリエンス <!--621622-->
3 月以降、Android 用ポータル サイト アプリでは[材料設計ガイドライン](https://material.io/guidelines/material-design/introduction.html)に従って、最新の外観が作成されます。 この改善されたユーザー エクスペリエンスには、次のものが含まれます。

* __色__: タブ ヘッダーを、カスタムの色パレットに従って色付けすることができます。
* __インターフェイス__: [アプリ] タブの [おすすめアプリ] ボタンと [すべてのアプリ] ボタンが更新されました。 [検索] ボタンは浮動アクション ボタンになりました。
* __ナビゲーション__: [すべてのアプリ] で [おすすめ]、[すべて] および [カテゴリ] のタブ付きビューが表示され、移動がより簡単になります。
* __サービス__: [デバイス] タブと [IT に連絡] タブが読みやすくなりました。

[UI の更新ページ](/intune-classic/whats-new/whats-new-in-intune-app-ui)で、更新前と後のイメージを確認できます。

### <a name="associate-multiple-management-tools-with-the-windows-store-for-business---926135--"></a>複数の管理ツールとビジネス向け Windows ストアの関連付け <!--926135-->
ビジネス向け Windows ストアのアプリを展開するために複数の管理ツールを使用する場合、これまでは、ビジネス向け Windows ストアにはそのうちの 1 つしか関連付けることはできませんでした。 これからは、複数のツール (Intune や Configuration Manager など) をストアに関連付けることができます。 詳細については、「[ビジネス向け Windows ストアから購入したアプリを Microsoft Intune で管理する](/intune-classic/deploy-use/manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune#associate-your-windows-store-for-business-account-with-intune)」を参照してください。

## <a name="whats-new-in-the-public-preview-of-the-intune-admin-experience-on-azure---736542--"></a>Azure での新しい Intune 管理者エクスペリエンスのパブリック プレビューの新機能<!--736542-->

2017 年初めには、すべての管理者エクスペリエンスが Azure に移行され、Graph API を幅広く使用する最新のサービス プラットフォーム上で、EMS の中核的ワークフローの強力な統合管理を利用できるようになります。

今月には、Azure Portal で新しい管理者エクスペリエンスのパブリック プレビューを表示する新しい試用テナントが開始されます。 プレビュー状態では、既存の Intune コンソールでの機能とパリティが繰り返し提供されます。

Azure Portal の管理者エクスペリエンスでは、既に発表されている新しいグループ化とターゲット設定の機能が使用されます。既存のテナントを新しいグループ化エクスペリエンスに移行すると、テナントの管理者エクスペリエンスも新しいプレビュー版に移行されます。 テナントを移行する前に、新しい機能をテストしたり見たりしたい場合は、新しい Intune 試用版アカウントにサインアップするか、[新しいドキュメント](/intune/whats-new)をご覧ください。

Azure の Intune プレビューの新機能は[ここ](/intune/whats-new)で確認できます。

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
2 月から、ポータル Web サイトで管理対象のデバイスを持っていないユーザーを対象とするアプリをサポートします。 この Web サイトは、新しいコントラストの配色パターン、動的な図、および "ハンバーガー メニュー"  ![ポータル サイトのハンバーガー メニュー](/intune-classic/whats-new/whats-new-in-intune-app-ui)。

#### <a name="new-documentation-for-app-protection-policies---583398--"></a>アプリの保護ポリシーに関する新しいドキュメント <!--583398-->
Intune アプリ ラッピング ツールまたは Intune アプリ SDK を使用して、iOS および Android アプリでアプリ保護ポリシー (MAM ポリシーとして知られる) を有効にする必要がある管理者やアプリ開発者用のドキュメントを更新しました。

次の記事が更新されました。

* [Microsoft Intune によるモバイル アプリケーション管理のためにアプリを準備する方法を決める](/intune-classic/deploy-use/decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune)
* [Intune アプリ ラッピング ツールでモバイル アプリケーションを管理するために iOS アプリを準備する](/intune-classic/deploy-use/prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)
* [Microsoft Intune アプリ SDK の概要](/intune-classic/develop/intune-app-sdk-get-started)
* [iOS 用 Intune アプリ SDK 開発者ガイド](/intune-classic/develop/intune-app-sdk-ios)

次の記事がドキュメント ライブラリに新たに追加されました。

* [Intune App SDK Cordova プラグイン](/intune-classic/develop/intune-app-sdk-cordova)
* [Intune App SDK Xamarin コンポーネント](/intune-classic/develop/intune-app-sdk-xamarin)

#### <a name="progress-bar-when-launching-the-company-portal-on-ios---665978--"></a>iOS でのポータル サイトの起動時の進行状況バー <!--665978-->
iOS 用ポータル サイトでは、ユーザーに発生する読み込みプロセスに関する情報を提供する進行状況バーが起動画面に導入されています。 進行状況バーは段階的にロールアウトされ、スピンと置き換えられます。 これは、一部のユーザーには新しい進行状況バーが表示され、他のユーザーにはスピンが引き続き表示されることを意味します。

## <a name="december-2016"></a>2016 年 12 月

### <a name="public-preview-of-the-new-intune-admin-experience-on-azure---736542--"></a>Azure での新しい Intune 管理者エクスペリエンスのパブリック プレビュー <!--736542-->
2017 年初めには、すべての管理者エクスペリエンスが Azure に移行され、Graph API を幅広く使用する最新のサービス プラットフォーム上で、EMS の中核的ワークフローの強力な統合管理を利用できるようになります。 すべての Intune テナントでこのポータルが広く利用できるようになりますが、それに先立ち、今月中にこの新しい管理者エクスペリエンスのプレビューを一部のテナントに提供することを謹んでお伝えします。

Azure Portal の管理者エクスペリエンスでは、既に発表されている新しいグループ化とターゲット設定の機能が使用されます。既存のテナントを新しいグループ化エクスペリエンスに移行すると、テナントの管理者エクスペリエンスも新しいプレビュー版に移行されます。 それまでの間、Azure Portal で Microsoft Intune のために用意しているものを[新しいドキュメント](/intune/what-is-intune)でご確認いただけます。

__Azure Portal のパブリック プレビューでの電気通信経費管理の統合__ <!--747605--> Azure Portal では、サード パーティの電気通信経費管理 (TEM) サービスとの統合のプレビューが始められています。Intune を使用して、国内およびローミングのデータ使用量を制限できます。

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

この新しいアプリでは、ユーザーは、Windows 10 デバイスでのシングル サインオン (SSO) や証明書ベースの認証など、追加のプラットフォーム機能も利用することができます。 アプリは、既存の Windows 8.1 ポータル サイトおよび Windows Phone 8.1 ポータル サイトのインストールのアップグレードとして Windows ストアから入手できるようになります。 詳細については、[aka.ms/intunecp_universalapp](http://aka.ms/intunecp_universalapp) を参照してください。

> [!IMPORTANT]
> __Intune と Android for Work の更新プログラム__ __[必須]__ の操作を使用して Android for Work アプリを展開できますが、Intune グループが新しい Azure AD グループ エクスペリエンスに移行された場合、__[利用可能]__ としてのみアプリを展開できます。

__Cordova プラグイン用 Intune アプリ SDK で登録なしの MAM をサポート開始__ アプリ開発者は、Cordova プラグイン用 Intune アプリ SDK を使用して、Android および iOS 用の Cordova ベースのアプリでデバイス登録を行わずに MAM 機能を有効化できるようになりました。 Cordova プラグイン用の Intune アプリ SDK は[こちら](https://github.com/msintuneappsdk/cordova-plugin-ms-intune-mam)にあります。

__Intune アプリ SDK Xamarin コンポーネントで登録なしの MAM のサポート開始__ アプリ開発者は、Intune アプリ SDK Xamarin コンポーネントを使用して、Android および iOS 用の Xamarin ベースのアプリでデバイス登録を行わずに MAM 機能を有効化できるようになりました。 Intune アプリ SDK Xamarin コンポーネントは[こちら](https://github.com/msintuneappsdk/intune-app-sdk-xamarin)にあります。

### <a name="notices"></a>通知

__Symantec 署名証明書のアップロードで署名済みの Windows Phone 8 ポータル サイトが不要に__ Symantec 署名証明書のアップロード時に、署名済みの Windows Phone 8 ポータル サイト アプリが不要になりました。 証明書は単独でアップロードできます。

###<a name="deprecations"></a>廃止予定

__Windows Phone 8 ポータル サイトのサポート__ Windows Phone 8 ポータル サイトのサポートは廃止されます。 2016 年 10 月に Windows Phone 8 プラットフォームおよび Windows RT プラットフォームのサポートが廃止されました。 また、2016 年 10 月に Windows Phone 8 ポータル サイトのサポートも廃止されました。

## <a name="october-2016"></a>2016 年 10 月

### <a name="conditional-access-for-mobile-application-management"></a>モバイル アプリケーションを管理するための条件付きアクセス
Exchange Online へのアクセスを制限して、Intune モバイル アプリケーション管理ポリシーをサポートするアプリ (Outlook など) からのアクセスのみを許可することができます。 [この新機能](/intune-classic/deploy-use/allow-policy-managed-apps-access-to-o365)は組み込みのメール クライアントや Intune MAM ポリシーが構成されていない他のアプリへのアクセスをブロックできるため、Intune のモバイル アプリ管理 (MAM) ポリシーと組み合わせると効果的です。 これにより、ユーザーが組織のデータにアクセスする際に、Intune MAM を使用して保護できるアプリを使用するようになります。 Intune モバイル アプリ管理は、Azure ポータルから使用することができます。 [設定] ブレードの新しい [条件付きアクセス] セクションを探してください。

### <a name="conditional-access-for-windows-pcs"></a>Windows PC の条件付きアクセス
Intune 管理コンソールを通して条件付きアクセス ポリシーを作成することで、Windows PC が [Exchange Online](/intune-classic/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune) にアクセスするのをブロックできるようになりました。 また、Office デスクトップおよびユニバーサル アプリケーションへのアクセスをブロックする条件付きアクセス ポリシーを作成することもできます。

### <a name="android-for-work-support"></a>Android for Work のサポート

> [!IMPORTANT]

> __[必須]__ の操作を使用して Android for Work アプリを展開できますが、Intune グループが新しい Azure AD グループ エクスペリエンスに移行された場合、__[利用可能]__ としてのみアプリを展開できます。

Intune は、現在、Android for Work (AfW) プログラムの一部となっています。 今月から数か月をかけて AfW 機能のサポートを展開する予定です。 ただし、AfW の使用可能なアプリの展開では、新しいグループ化とターゲット設定を利用します。 新しくプロビジョニングされる Intune サービス アカウントがこの機能を使用できるようになるのは、AfW が使用できるようになった後です。

[Android for Work の Intune サポートに関する Microsoft からのお知らせをお読みください](https://blogs.technet.microsoft.com/enterprisemobility/2016/09/12/microsoft-intune-support-for-android-for-work/)。

次の Intune トピックは、Android for Work に関する新しい情報と更新情報を扱っています。

IT プロフェッショナル向け:
- [Android for Work のセットアップ](/intune-classic/deploy-use/set-up-android-for-work)
- [Intune で Exchange Online と新しい Exchange Online Dedicated への電子メール アクセスを制限する](/intune-classic/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune)
- [Intune で Exchange On-premises と従来の Exchange Online Dedicated への電子メール アクセスを制限する](/intune-classic/deploy-use/restrict-access-to-exchange-onpremises-with-microsoft-intune)
- [Android for Work のコンプライアンス ポリシー設定](/intune-classic/deploy-use/afw-compliance-policy-settings-in-microsoft-intune)
- [Android for Work アプリを展開する方法](/intune-classic/deploy-use/android-for-work-apps)
- [モバイル アプリ構成ポリシーを使用した Android for Work アプリの構成](/intune-classic/deploy-use/afw-app-configuration-policy)
- [Android for Work のポリシー設定](/intune-classic/deploy-use/android-for-work-policy-settings-in-microsoft-intune)

エンド ユーザー向け:
- [仕事用プロファイルを作成するとどうなりますか](/intune-user-help/what-happens-when-you-create-a-work-profile-android)
- [Intune での仕事用プロファイルの作成とデバイスの登録](/intune-user-help/create-a-work-profile-and-enroll-your-device-in-intune-android)

### <a name="lookout-integration-to-protect-ios-devices"></a>iOS デバイスを保護するため Lookout 統合
10 月、Microsoft は、デバイス上のマルウェアやリスクの高いアプリなどを検出して iOS モバイル デバイスを保護するため、Lookout のモバイル脅威保護ソリューションに統合します。 Lookout のソリューションにより、構成可能な脅威レベルを決定できます。 Intune に、Lookout によるリスク評価に基づいてデバイスのコンプライアンスを判断するためのコンプライアンス ポリシー ルールを作成できます。 条件付きアクセス ポリシーを使用すると、デバイスのコンプライアンス状態に基づいて、会社のリソースへのアクセスを許可したりブロックしたりできます。

非準拠 iOS デバイスのエンド ユーザーは登録が求められ、会社のデータへのアクセス権を得るにはデバイスへの Lookout for Work アプリケーションのインストール、アプリのアクティブ化、Lookout for Work アプリケーションで報告された驚異の修復が必要となります。 [Lookout for Work アプリを構成して展開する](/intune-classic/deploy-use/configure-and-deploy-lookout-for-work-apps)方法について説明します。
<!--TFS 1319493-->

### <a name="intune-app-wrapping-tool-for-android"></a>Android 用 Intune アプリ ラッピング ツール
Intune アプリ ラッピング ツールを使うと、アプリで Intune モバイル アプリケーション管理 (MAM) ポリシーを使用できるようになります。 デバイスの登録を必要としない Intune MAM ポリシーのサポートが開始されました。

### <a name="manage-printing-from-apps-managed-using-mam-policies"></a>MAM ポリシーを使用して管理されたアプリケーションから印刷する
MAM ポリシーを使用しているアプリから会社データが印刷されるのを防ぐことができるようになりました。 この設定は、[Azure Portal](/intune-classic/deploy-use/android-mam-policy-settings) デバイスで使用できます。
<!--TFS 1014328-->

### <a name="support-for-fingerprints-on-android-devices"></a>Android デバイスでの指紋のサポート
Android モバイル アプリ管理 (MAM) ポリシーを使用すると、PIN を入力するのではなく、指紋でアプリにアクセスできるようになります。この機能と、他の Android 用モバイル アプリ管理ポリシー設定については、https://docs.microsoft.com/ja-jp/intune-classic/deploy-use/android-mam-policy-settings を参照してください。

### <a name="notices"></a>通知

__Android Samsung KNOX と Intune の互換性__ スマートフォン Samsung Galaxy Ace の特定のモデルは、Samsung KNOX デバイスとして Intune で管理することができません。 これらのデバイスは、Intune に登録すると、標準の Android デバイスとして管理されます。

該当するモデルの番号は次のとおりです。

* SM-G313HU
* SM-G313HY
* SM-G313M
* SM-G313MY
* SM-G313U

お客様とエンドユーザーは、これ以上操作を行う必要はありません。 詳細については、[Samsung KNOX](https://www.samsungknox.com) の Web サイトをご覧ください。

__Windows 8 のポータル サイト アプリは廃止されています。Windows Phone 8 および Windows RT プラットフォームのサポートは廃止される予定です__ 2016 年 10 月以降、Microsoft Intune は Windows 8 ポータル サイトのサポートを廃止します。 Microsoft Intune は、Windows Phone 8 プラットフォームおよび Windows RT プラットフォームのサポートも廃止します。 その結果、Windows Phone 8 デバイスまたは Windows RT デバイスの登録または更新はできなくなります。

既に登録されている Windows Phone 8 デバイス、Windows RT デバイス、Windows 8 デバイスは継続して管理できます。 デバイスへのアプリの配布を中断することなく続行するには、Windows Phone 8 および Windows 8 デバイスを Windows 8.1 および Windows Phone 8.1 に更新し、対応する Windows 8.1 および Windows Phone 8.1 のポータル サイト アプリを使用します。

2016 年 11 月以降、Windows Phone 8 ポータル サイトのサポートは廃止されます。
<!--TFS 1255391-->

### <a name="whats-coming"></a>今後の更新情報

__Windows 10 デバイスで使用可能な新しい Microsoft Intune ポータル サイト__ Microsoft は、Windows 10 デバイス用に新しい Microsoft Intune ポータル サイトをリリースします。 このアプリでは新しい Windows 10 ユニバーサル形式を利用します。このアプリ内ではユーザーに対して更新されたユーザー エクスペリエンスが提供され、すべての Windows 10 デバイスで同じエクスペリエンスが提供されます。現在使用されている機能はすべて引き続き利用できます。

この新しいアプリでは、ユーザーは、Windows 10 デバイスでのシングル サインオン (SSO) や証明書ベースの認証など、追加のプラットフォーム機能も利用することができます。 アプリは、既存の Windows 8.1 ポータル サイトおよび Windows Phone 8.1 ポータル サイトのインストールのアップグレードとして Windows ストアから入手できるようになります。 詳細については、[aka.ms/intunecp_universalapp](http://aka.ms/intunecp_universalapp) を参照してください。
<!--TFS 1016502-->

## <a name="september-2016"></a>2016 年 9 月
### <a name="new-features-announcements-and-information"></a>新しい機能、お知らせ、情報
* [Windows の条件付きアクセス](#windows-conditional-access)
* [iOS 10 のサポート](#ios-10-support)
* [Android と iOS のデバイス登録がなくても、アプリ ラッピング ツールで MAM がサポートされます](#app-wrapping-tool-supports-mam-without-device-enrollment-for-android-and-ios)
* [9 月に Intune グループから Azure Active Directory への移行が開始されます](#intune-groups-begin-transitioning-to-azure-active-directory-in-september)
* [Android デバイスを保護するため Lookout が統合されます](#lookout-integration-to-protect-android-devices)
* [Android、iOS、および Windows 用のポータル サイトの更新](#company-portal-updates)
* [Intune の用語集](#intune-glossary)
* [今後の更新情報](#whats-coming)

### <a name="windows-conditional-access"></a>Windows の条件付きアクセス
Intune 管理コンソールを通して条件付きアクセス ポリシーを作成することで、Windows PC が Exchange Online および SharePoint Online にアクセスするのをブロックできるようになりました。 また、Office デスクトップおよびユニバーサル アプリケーションへのアクセスをブロックする条件付きアクセス ポリシーを作成することもできます。

### <a name="ios-10-support"></a>iOS 10 のサポート
既存の Intune MDM と MAM のシナリオには、iOS 10 との互換性があります。 ヒントについては、[Intune サポート チームのブログ](https://blogs.technet.microsoft.com/intunesupport/2016/09/13/support-tip-intune-support-for-ios-10/)を参照してください。

### <a name="app-wrapping-tool-supports-mam-without-device-enrollment-for-android-and-ios"></a>Android と iOS のデバイス登録がなくても、アプリ ラッピング ツールで MAM がサポートされます
Intune のアプリ ラッピング ツールは、iOS と Android の基幹業務 (LOB) アプリで Intune MAM を有効にするために使用するコマンド ライン ツールです。 Intune MAM SDK をお使いのアプリに組み込み、アプリが Intune を使用して展開された MAM ポリシーを適用できるようにするには、この方法が最も簡単です。 MAM ポリシーを使用すると、以下の操作を実行できます。

1. アプリのデータを暗号化します。
2. インフォメーション ワーカーがアプリを起動するときに PIN の入力を求めます。
3. アプリに対し、他の管理対象アプリにのみデータの転送を許可します。
4. アプリが Android、iTunes、および iCloud にデータをバックアップしないようにします。
5. 他の管理対象アプリとの間で切り取り、コピー、貼り付けのみを許可します。

新しくなった Intune のアプリ ラッピング ツールのパブリック プレビューでは、iOS および Android の内部 LOB アプリにデバイスを登録しなくても MAM がサポートされるようになりました。 つまり、エンドユーザーは MAM の有効な LOB アプリを使用するために、デバイスを Intune に登録する必要はありません。

誰でもパブリック プレビューのソフトウェアをテストしたり、次の msintuneappsdk の GitHub にある、役に立つドキュメントを参照したりできます。

<p style="margin-left: 40px">http://www.github.com/msintuneappsdk/intune-app-wrapper-ios-preview

<p style="margin-left: 40px">http://www.github.com/msintuneappsdk/intune-app-wrapper-android-preview

Android および iOS のプレリリース版 Microsoft Intune アプリのラッパーをインストールして使用するには、次を実行しておく必要があります。

* Android および iOS のプレリリース版 Microsoft Intune アプリ ラッピング ツールに関するマイクロソフト ソフトウェア ライセンス条項を確認します。
* 記録用にライセンス条項を印刷し、保持します。 Android のプレリリース版 Microsoft Intune アプリ ラッピング ツールをダウンロードして使用することで、このライセンス条項に同意することになります。 本ライセンス条項に同意されない場合、お客様は本ソフトウェアを使用できません。
<!---TFS 1235607--->

### <a name="intune-groups-begin-transitioning-to-azure-active-directory-in-september"></a>9 月に Intune グループから Azure Active Directory への移行が開始されます
一部の新しい Intune アカウントが Intune ユーザー グループではなく Azure Active Directory セキュリティ グループを使用します。 セキュリティ グループで作業していることは、Intune ポータル グループ ページに Azure 管理ポータルにリダイレクトするリンクが表示されることで確認できます。

### <a name="lookout-integration-to-protect-android-devices"></a>Android デバイスを保護するため Lookout が統合されます
Microsoft は、デバイス上のマルウェアやリスクの高いアプリなどを検出して Android モバイル デバイスを保護するため、Lookout のモバイル脅威保護ソリューションに統合します。 Lookout のソリューションにより、構成可能な脅威レベルを決定できます。 Intune に、Lookout によるリスク評価に基づいてデバイスのコンプライアンスを判断するためのコンプライアンス ポリシー ルールを作成できます。 条件付きアクセス ポリシーを使用すると、デバイスのコンプライアンス状態に基づいて、会社のリソースへのアクセスを許可したりブロックしたりできます。

非準拠デバイスのエンド ユーザーは登録が求められ、アクセス権を得るには Android デバイスへの Lookout for Work アプリケーションのインストール、アプリのアクティブ化、Lookout for Work アプリケーションで報告された驚異の修復が必要となります。 詳細については、「[Restrict access based on device, network, and application risk](/intune-classic/deploy-use/device-threat-protection)」 (デバイス、ネットワーク、アプリケーションのリスクに基づいてアクセスを制限する) を参照してください。


### <a name="company-portal-updates"></a>ポータル サイトの更新

__Android__

<p style="margin-left: 40px">**Android 用ポータル サイトへの "通知" の追加**<br/>
<p style="margin-left: 40px">Android 用ポータル サイトのホームページに新しい通知アイコンが追加されました。 このアイコンをタップすると [通知] ページが開き、ポータル サイト アプリの中でエンドユーザーが注目する必要のある項目がすべて表示されます。たとえば、デバイスのコンプライアンス非対応、登録の更新、登録のアクティブ化です。 iOS 版のポータル サイト アプリには既に、この通知機能が追加されています。 この新しい [通知] ページの導入に伴い、[会社アクセスのセットアップ] ページがポータル サイトの起動または再開のたびに表示されることはなくなりました (ただし、デバイスが登録済みである場合)。 管理者が独自にエンド ユーザー向けガイドを作成している場合は、必要に応じてこの変更をドキュメントに反映してください。 更新後のスクリーン ショットは[こちら](https://aka.ms/androidcpupdate)にあります。  

__iOS__
<p style="margin-left: 40px">**iOS ポータル サイト アプリのサポートの変更**<br/>
<p style="margin-left: 40px">iOS 用 Microsoft Intune ポータル サイト アプリのすべてのユーザーが、最新バージョンのアプリを使用するように要求されます。 新しいユーザーは最新バージョンのみをダウンロードでき、現在のユーザーは最新バージョンへの更新を求められます。 最新バージョンを使用するには iOS 8.0 以降が必要であり、デバイスで以前の iOS バージョンを実行している場合は、デバイスを iOS 8.0 以降に更新したうえでポータル サイト アプリを最新バージョンに更新するまで、ポータル サイトを使用できず、登録することもできません。 iOS 8.0 以前のバージョンを実行している登録済みのデバイスは、引き続き管理対象であり、Intune 管理コンソールに表示されます。
<!---TFS 1283165--->

<p style="margin-left: 40px">**iOS エンドユーザーのアプリ取得方法の改善**<br/>
<p style="margin-left: 40px">iOS 用ポータル サイト アプリのアプリ タイルに以下のような変更が行われ、ユーザーは単一の場所 (ポータル サイト Web サイト) のさまざまなビューですべてのアプリを確認できるようになりました。 Apple の制限では、基幹業務および管理対象アプリのストア アプリをポータル サイト アプリに一覧表示することが禁止されており、ユーザーが自分のすべてのアプリを見るには異なるビューを表示する必要があります。

<p style="margin-left: 40px">これまで **[会社のアプリ]** タイルはポータル サイト Web サイトの [すべて] タブにあるすべてのアプリの一覧と関連付けられており、今後も機能は同じです。 このタイル名は **[すべてのアプリ]** に変更されました。

<p style="margin-left: 40px">**[その他のアプリ]** タイルはこれまで、Apple がポータル サイト アプリに表示を許可しているすべてのアプリを一覧表示する、ポータル サイト アプリ内のビューに関連付けられていました。 このタイル名は **[おすすめアプリ]** に変更され、ユーザーがこのタイルをタップするとポータル サイト Web サイトの [おすすめ] タブが表示されるようになりました。

<p style="margin-left: 40px">**[カテゴリ]** タイルはこれまで、アプリのカテゴリを一覧表示する、ポータル サイト アプリ内のビューに関連付けられていました。 このタイル名は変更されませんが、ポータル サイト Web サイトの [カテゴリ] タブに関連付けられるようになりました。 更新後のスクリーン ショットは[こちら](https://gallery.technet.microsoft.com/Improvements-in-how-iOS-d1104186)で確認することができます。
  <!---TFS 1317133--->

<p style="margin-left: 40px">**IT プロフェッショナルが iOS の管理対象ブラウザー アプリをインストールするようにアプリの要件を設定している場合は、そのダイアログを表示する**<br/>
<p style="margin-left: 40px">管理対象ブラウザーでのみ Web クリップを開くように構成したものの、管理対象ブラウザーがデバイスにインストールされていない場合に、デバイスのポータル サイト アプリがユーザーに Web クリップをインストールする前に管理対象ブラウザーをインストールするように求めるダイアログが表示されるようになります。
  <!---TFS 1228570--->

__Windows__
<p style="margin-left: 40px">**フィードバック ボタンを Windows Phone 8.1 ポータル サイト アプリに追加**<br/>
<p style="margin-left: 40px">Windows Phone 8.1 ポータル サイト アプリでは、エンド ユーザーが新しい [フィードバックの送信] ボタンを使用してアプリに関するフィードバックを送ることができます。 フィードバックを送信するには、ポータル サイト アプリの画面の右下にある "..." メニューをタップし、[**フィードバックの送信**] をタップします。 フィードバックは匿名化して収集され、ポータル サイト アプリのユーザー エクスペリエンス向上に役立てられます。
<!---TFS 1317806--->

### <a name="intune-glossarybr"></a>Intune の用語集</br>
Intune 製品で使用されている用語を説明する新しい[用語集トピック](/intune-classic/understand-explore/intune-glossary)をライブラリに追加しました。

## <a name="august-2016"></a>2016 年 8 月
### <a name="app-management"></a>アプリ管理

__iOS 9.3 で表示されないアプリと表示されるアプリ__ iOS 9.3 以降を実行するデバイスでは、iOS の一般構成ポリシーの表示されないアプリと表示されるアプリのリストを使用して次のことができます。
- ユーザーに対して表示されないアプリの一覧を指定します。 ユーザーはこのようなアプリを表示または起動できません。
- ユーザーが表示および起動できるアプリの一覧を指定します。 他のアプリは表示または起動できません。

ユーザー自身が展開したアプリと、Messages や Notes などの iOS 組み込みアプリの両方を指定できます。 詳細については、「[Microsoft Intune の iOS ポリシー設定](/intune-classic/deploy-use/ios-policy-settings-in-microsoft-intune)」を参照してください。
<!---TFS 1279009 checked--->
__Samsung KNOX デバイスでの許可するアプリとブロックするアプリのポリシー__Samsung KNOX デバイスでは、次のいずれかを作成できるカスタム ポリシーを構成できます。
- デバイスでの実行をブロックするアプリの一覧。 ブロック リストで定義されているアプリは、インストールされている場合でも、デバイスでアクティブにできません。
- デバイスのユーザーが Google Play ストアからインストールできるアプリの一覧。 他のアプリはストアからインストールできません。

これらの設定は、Samsung KNOX を実行するデバイスでのみ使用できます。
詳細については、「[カスタム ポリシーを使用して、Samsung KNOX デバイス用のアプリを許可またはブロックする](/intune-classic/deploy-use/custom-policy-to-allow-and-block-samsung-knox-apps)」を参照してください。
<!---TFS 1311629 checked --->

__モバイル アプリケーション管理 (MAM) ポリシーと互換性のある新しいアプリ__ [iOS](/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune) 向けの Yammer アプリは、デバイスが登録されていてもいなくても互換性があります。

MAM と互換性のある全アプリの一覧については、[Microsoft Intune アプリケーション パートナー](https://www.microsoft.com/cloud-platform/microsoft-intune-partners)のサイトをご覧ください。
<!--- TFS 1252335 & 1252336 checked--->

__Intune Viewer アプリ__ 新しい RMS 共有アプリのリリースに伴い、2016 年 8 月以降、次の Intune Viewer アプリを削除する予定です。
- Intune AV Viewer
- Intune PDF Viewer
- Google Play の Android 用 Intune Image Viewer

Intune Viewer アプリを使用せずに、新しい Android 用 Rights Management アプリ (RMS 共有) を使用することをお勧めします。こうすることで、Android デバイスに 3 つのアプリを個々に展開するのではなく、1 つのアプリだけで、会社のファイルを安全に表示できるようになります。 Intune Viewer アプリがサポートされなくなると、Google ストアから削除され、その後使用することができなくなります。

### <a name="device-management"></a>デバイス管理
__Android 7.0 のサポート__ Intune は近日公開予定のモバイル デバイス向け Android 7.0 オペレーティング システムの "Day 0" サポートを提供します。
<!---TFS 1262053--->
### <a name="google-removal-of-remote-passcode-reset-capability-on-android-70-devices"></a>Google による Android 7.0 デバイスでのリモート パスコード リセット機能の削除
Google は、IT 管理者やエンド ユーザーが Android 7.0 デバイスのパスコードをリモートでリセットする機能を削除しています。 これまでは、IT 管理者はユーザーのパスコードをリモートでリセットでき、エンド ユーザーはポータル サイトから自分のパスコードをリセットできました。



### <a name="company-portal-updates"></a>ポータル サイトの更新
__ポータル Web サイト__
- **ポータル サイトから Microsoft へのフィードバック リンク** <br/>
ポータル サイトの Web サイトでは、エンドユーザーはページの下部にある新しい [フィードバック] リンクをタップして、サイトの操作性に関するフィードバックを Microsoft に送信できるようになります。 収集されて匿名化されたフィードバックは、Microsoft がポータル サイトの Web サイトについてユーザーの操作性を向上させるのに役立ちます。
<!--- TFS 1313657 checked--->

__iOS__
- **iOS Managed Browser の最小バージョンの 8.0 への更新**<br/>
iOS 用の Microsoft Intune Managed Browser アプリは、iOS 8.0 以降を実行するデバイスをサポートするように更新されました。 iOS 7.1 デバイスでは、既存の Managed Browser アプリを使用することができますが、新しい Managed Browser の機能にアクセスしてフル活用できるように、ユーザーに iOS 8.0 以降に更新することをお勧めしてください。  
<!---TFS 1313253 checked--->

### <a name="whats-coming"></a>今後の更新情報
__Intune グループから Azure Active Directory グループへの移行 (2016 年 9 月以降)__ Intune は、Intune でのユーザーとデバイスのグループとして Azure Active Directory (AAD) のセキュリティ グループを使用する、新しいグループ管理エクスペリエンスを作成しています。 これらのグループは、**新しい Azure ベースの Intune 管理ポータルの導入時**に、すべてのグループの管理、ポリシーの展開、およびプロファイルの展開に使用されます。

この新しいエクスペリエンスにより、サービス間でグループを複製する必要がなくなり、**新しい Azure Active Directory Premium (AADP) グループ機能の一部にアクセスすることができ**、PowerShell および Graph を使用して拡張機能を提供します。 またこれにより、エンタープライズ モビリティ管理でのグループ管理エクスペリエンスも統合されます。

セキュリティ グループへの移行を有効にするため、**現在の管理コンソール**のエクスペリエンスにいくつかの変更が施されます。 **これらの変更と、AAD セキュリティ グループの使用については、Intune のドキュメントに記録されます**。

Intune の新規のお客様には、**現在のテナントに表示される前に、セキュリティ グループの変更の一部**が表示されます。

グループ管理の変更に加えて、**次の機能が廃止される予定です**。
- 新規グループ作成時のメンバーまたはグループの除外
- **グループ化を解除されたユーザー**と**グループ化を解除されたデバイス**のグループ
- サービス管理者の役割での**グループの管理**
- 通知ルールに対するカスタム グループベースの警告
- レポート内のグループのピボット
<!--- TFS 1295329--->

__Android 用ポータル サイトへの "通知" の追加__ Microsoft は、Android 用ポータル サイトに対する更新を 9 月にリリースし、ホームページ上に新しい**通知**アイコンを導入します。 このアイコンをタップすると、**通知**ページにアクセスし、デバイスのコンプライアンス非対応、登録の更新、および登録のアクティブ化などのポータル サイト アプリで注意が必要なすべての項目をエンド ユーザーに表示します。 iOS 用ポータル サイト アプリも使用している場合は、通知エクスペリエンスがすでに表示されます。 **通知**ページの導入に伴い、デバイスがすでに登録されている限り、Android 用ポータル サイトを起動または再開するたびに**会社アクセスのセットアップ**ページが表示されることはなくなります。 Microsoft は、多くのお客様がエンドユーザー ガイダンスを作成していることを把握しており、ガイダンスとスクリーンショットの更新が必要になる場合に事前に通知くださることに感謝いたします。 ドキュメントに今後のエクスペリエンスの変更を反映し、更新してください。 最新のスクリーンショットは、https://aka.ms/androidcpupdate でご確認いただけます。  

### <a name="service-deprecation"></a>廃止予定のサービス

- **iOS ポータル サイト アプリのサポートの変更**<br/>
9 月には、iOS 用 Microsoft Intune ポータル サイト アプリのすべてのユーザーが、アプリの最新バージョンを使用するように要求されます。 新しいユーザーは最新バージョンのみをダウンロードでき、現在のユーザーは最新バージョンへの更新を求められます。 最新バージョンを使用するには iOS 8.0 以降が必要であり、デバイスで以前の iOS バージョンを実行している場合は、デバイスを iOS 8.0 以降に更新したうえでポータル サイト アプリを最新バージョンに更新するまで、ポータル サイトを使用できず、登録することもできません。 iOS 8.0 以前のバージョンを実行している登録済みのデバイスは、引き続き管理対象であり、Intune 管理コンソールに表示されます。  

- **iOS Managed Browser の最小バージョンの 8.0 への更新**<br/>
8 月、Intune は iOS 8.0 以降を実行するデバイスのみをサポートする、iOS 用の最新の Microsoft Intune Managed Browser アプリをリリースします。 iOS 7.1 デバイスでは、既存の Managed Browser アプリを使用することができますが、新しい Managed Browser の機能にアクセスしてフル活用できるように、ユーザーに iOS 8.0 以降に更新することをお勧めしてください。  
<!---TFS 1313253--->

- **Windows 8 および Windows Phone 8 用のポータル サイト アプリは、2016 年 9 月以降非推奨になります** <br/>
Microsoft Intune は、2016 年 9 月以降、Windows Phone 8 および Windows 8 プラットフォーム用 Microsoft Intune ポータル サイト アプリのサポートを終了します。 デバイスを Windows 8.1 および Windows Phone 8.1 に更新し、対応する Windows 8.1 および Windows Phone 8.1 のポータル サイト アプリを使用して、更新したデバイスへのアプリの配布を続行します。
<!---TFS 1255391--->
