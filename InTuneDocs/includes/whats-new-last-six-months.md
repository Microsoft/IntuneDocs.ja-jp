## <a name="december-2016"></a>2016 年 12 月

### <a name="public-preview-of-the-new-intune-admin-experience-on-azure--736542--"></a>Azure での新しい Intune 管理者エクスペリエンスのパブリック プレビュー<!--736542-->
2017 年初めには、すべての管理者エクスペリエンスが Azure に移行され、Graph API を幅広く使用する最新のサービス プラットフォーム上で、EMS の中核的ワークフローの強力な統合管理を利用できるようになります。 すべての Intune テナントでこのポータルが広く利用できるようになりますが、それに先立ち、今月中にこの新しい管理者エクスペリエンスのプレビューを一部のテナントに提供することを謹んでお伝えします。

Azure Portal の管理者エクスペリエンスでは、既に発表されている新しいグループ化とターゲット設定の機能が使用されます。既存のテナントを新しいグループ化エクスペリエンスに移行すると、テナントの管理者エクスペリエンスも新しいプレビュー版に移行されます。 それまでの間、Azure Portal で Microsoft Intune のために用意しているものを[新しいドキュメント](https://docs.microsoft.com/intune-azure/introduction/what-is-microsoft-intune)でご確認いただけます。

テナント移行のスケジュールに関して質問がある場合は、Microsoft の移行チーム ([intunegrps@microsoft.com](mailto:intunegrps@microsoft.com)) にお問い合わせください。

__Azure Portal のパブリック プレビューでの電気通信経費管理の統合__ <!--747605--> Azure Portal では、サード パーティの電気通信経費管理 (TEM) サービスとの統合のプレビューが始められています。 Intune を使用して、国内およびローミングのデータ使用量を制限できます。 これらの統合は、[Saaswedo](http://www.saaswedo.com) で始まっています。 試用テナントでこの機能を有効にする場合は、[Microsoft サポートにお問い合わせください](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune)。

### <a name="new-capabilities"></a>新しい機能

__すべてのプラットフォームでの多要素認証__ <!--747590--> Azure Active Directory で Microsoft Intune 登録アプリケーションに多要素認証 (MFA) を構成することにより、Azure の管理ポータルから iOS、Android、Windows 8.1+、または Windows Phone 8.1+ デバイスを登録すると、選択したユーザー グループに MFA を適用できます。

__モバイル デバイス登録を制限する機能__ <!--747596--> Intune では、登録を許可されるモバイル デバイス プラットフォームを制御する新しい登録制限が追加されています。 Intune では、モバイル デバイス プラットフォームが iOS、macOS、Android、Windows、Windows Mobile に分かれています。
* モバイル デバイスの登録を制限しても、PC クライアントの登録は制限されません。
* iOS のみについては、個人所有デバイスの登録をブロックする 1 つの追加オプションがあります。

[この記事](https://docs.microsoft.com/en-us/intune/deploy-use/manage-corporate-owned-devices)で説明されているように、IT 管理者が明示的に会社所有と指定しない限り、Intune はすべての新しいデバイスを個人所有としてマークします。

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

__Firefox による Silverlight のサポート終了__ <!--VSO TBA--> Mozilla では、2017 年 3 月をもって、[Firefox ブラウザー](https://www.mozilla.org/firefox)のバージョン 52 で Silverlight のサポートを終了します。 結果として、バージョンが 51 より後の Firefox では既存の Intune コンソールにログインできなくなります。 管理コンソールにアクセスするときは、Internet Explorer 10 または 11 を使用するか、[バージョンが 52 より前の Firefox](https://ftp.mozilla.org/pub/firefox/releases/) を使用することが推奨されます。 Intune を Azure Portal に移行することで、Silverlight を利用しなくてもさまざまな[最新ブラウザー](https://docs.microsoft.com/en-us/azure/azure-preview-portal-supported-browsers-devices)に対応します。

__Exchange Online モバイル受信トレイ ポリシーの削除__ <!--770687--> 12 月以降、管理者は Intune コンソールで Exchange Online (EAS) モバイル メールボックス ポリシーを表示または構成できなくなります。 この変更は、12 月から 1 月にかけてすべての Intune テナントに展開されます。 既存のすべてのポリシー構成は今までどおりですが、新しいポリシーの構成には Exchange 管理シェルを使います。 詳しくは、[こちら](https://technet.microsoft.com/en-us/library/bb123783%28v=exchg.150%29.aspx)をご覧ください。

__Android での Intune AV Player、Image Viewer、PDF Viewer アプリのサポート終了__<!--747553--> 2016 年 12 月中旬以降、Intune AV Player、Image Viewer、PDF Viewer の各アプリが使用できなくなります。 これらのアプリの代わりに、Azure Information Protection アプリが使用できるようになります。 Azure Information Protection アプリについて詳しくは、[こちら](https://docs.microsoft.com/information-protection/rms-client/mobile-app-faq)をご覧ください。

## <a name="november-2016"></a>2016 年 11 月

### <a name="new-capabilities"></a>新しい機能

<!--### View App States for All Platforms in Real Time
App installation status is now shown in real-time in the console. When you previously deployed an app, you had to wait for a targeted device to report back before the app install status was displayed in the Intune console.

### Streamline iOS App Management for your End Users
Intune can now automatically take over management of the previously installed app and no end user action is required.

Previously, if the end user of an enrolled iOS device installed an app from the App Store before you deployed that same app with a deployment action of __Available__, then the end user had to:

1. Open the __Company Portal__.
2. Select the app.
3. Tap __Install__ to enable Intune to take over management of the app.-->

__Windows 10 デバイスで使用可能な新しい Microsoft Intune ポータル サイト__ Microsoft は、[Windows 10 デバイス用に新しい Microsoft Intune ポータル サイト アプリ](https://www.microsoft.com/store/apps/9wzdncrfj3pz)をリリースします。 このアプリでは新しい Windows 10 ユニバーサル形式を利用します。このアプリ内ではユーザーに対して更新されたユーザー エクスペリエンスが提供され、すべての Windows 10 デバイスで同じエクスペリエンスが提供されます。現在使用されている機能はすべて引き続き利用できます。

この新しいアプリでは、ユーザーは、Windows 10 デバイスでのシングル サインオン (SSO) や証明書ベースの認証など、追加のプラットフォーム機能も利用することができます。 アプリは、既存の Windows 8.1 ポータル サイトおよび Windows Phone 8.1 ポータル サイトのインストールのアップグレードとして Windows ストアから入手できるようになります。 詳細については、[aka.ms/intunecp_universalapp](http://aka.ms/intunecp_universalapp) を参照してください。

<!--### Support for Windows Store for Business Apps Being Deployed as Available
You can now deploy apps you synchronized from the Windows Store for Business (WSfB) with a deployment action of __Available__ or __Required__. After syncing WSfB apps into Intune, administrators will be able to target those apps as available installs to groups of users. End users will see the deployed WSfB apps as available for install in the Universal Company Portal, where they can choose whether they would like to acquire the apps.

### Conditional Access for MAM with SharePoint Online

You can block apps that are not supported by Intune mobile app management (MAM) policies from accessing SharePoint online.  You can get started in Intune mobile app management via the Azure portal. Look for the  Conditional Access section in the “Settings” blade which now includes the option for SharePoint online.-->

> [!IMPORTANT]

> __Intune と Android for Work の更新プログラム__

> __[必須]__ の操作を使用して Android for Work アプリを展開できますが、Intune グループが新しい Azure AD グループ エクスペリエンスに移行された場合、__[利用可能]__ としてのみアプリを展開できます。

__Cordova プラグイン用 Intune アプリ SDK で登録なしの MAM をサポート開始__ アプリ開発者は、Cordova プラグイン用 Intune アプリ SDK を使用して、Android および iOS 用の Cordova ベースのアプリでデバイス登録を行わずに MAM 機能を有効化できるようになりました。 Cordova プラグイン用の Intune アプリ SDK は[こちら](https://github.com/msintuneappsdk/cordova-plugin-ms-intune-mam)にあります。

__Intune アプリ SDK Xamarin コンポーネントで登録なしの MAM のサポート開始__ アプリ開発者は、Intune アプリ SDK Xamarin コンポーネントを使用して、Android および iOS 用の Xamarin ベースのアプリでデバイス登録を行わずに MAM 機能を有効化できるようになりました。 Intune アプリ SDK Xamarin コンポーネントは[こちら](https://github.com/msintuneappsdk/intune-app-sdk-xamarin)にあります。

### <a name="notices"></a>通知

__Symantec 署名証明書のアップロードで署名済みの Windows Phone 8 ポータル サイトが不要に__ Symantec 署名証明書のアップロード時に、署名済みの Windows Phone 8 ポータル サイト アプリが不要になりました。 証明書は単独でアップロードできます。

###<a name="deprecations"></a>廃止予定

__Windows Phone 8 ポータル サイトのサポート__ Windows Phone 8 ポータル サイトのサポートは廃止されます。 2016 年 10 月に Windows Phone 8 プラットフォームおよび Windows RT プラットフォームのサポートが廃止されました。 また、2016 年 10 月に Windows Phone 8 ポータル サイトのサポートも廃止されました。

## <a name="october-2016"></a>2016 年 10 月

### <a name="conditional-access-for-mobile-application-management"></a>モバイル アプリケーションを管理するための条件付きアクセス
Exchange Online へのアクセスを制限して、Intune モバイル アプリケーション管理ポリシーをサポートするアプリ (Outlook など) からのアクセスのみを許可することができます。 [この新機能](/intune/deploy-use/allow-policy-managed-apps-access-to-o365)は組み込みのメール クライアントや Intune MAM ポリシーが構成されていない他のアプリへのアクセスをブロックできるため、Intune のモバイル アプリ管理 (MAM) ポリシーと組み合わせると効果的です。 これにより、ユーザーが組織のデータにアクセスする際に、Intune MAM を使用して保護できるアプリを使用するようになります。 Intune モバイル アプリ管理は、Azure ポータルから使用することができます。 [設定] ブレードの新しい [条件付きアクセス] セクションを探してください。

### <a name="conditional-access-for-windows-pcs"></a>Windows PC の条件付きアクセス
Intune 管理コンソールを通して条件付きアクセス ポリシーを作成することで、Windows PC が [Exchange Online](/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune) および [SharePoint Online](/intune/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune) にアクセスするのをブロックできるようになりました。 また、Office デスクトップおよびユニバーサル アプリケーションへのアクセスをブロックする条件付きアクセス ポリシーを作成することもできます。

### <a name="android-for-work-support"></a>Android for Work のサポート

> [!IMPORTANT]

> __[必須]__ の操作を使用して Android for Work アプリを展開できますが、Intune グループが新しい Azure AD グループ エクスペリエンスに移行された場合、__[利用可能]__ としてのみアプリを展開できます。

Intune は、現在、Android for Work (AfW) プログラムの一部となっています。 今月から数か月をかけて AfW 機能のサポートを展開する予定です。 ただし、AfW の使用可能なアプリの展開では、新しいグループ化とターゲット設定を利用します。 新しくプロビジョニングされる Intune サービス アカウントがこの機能を使用できるようになるのは、AfW が使用できるようになった後です。

<!--Existing Intune customers can use this feature in production once their tenant has been migrated. Existing customers are welcome to create a trial Intune account to plan for and test this feature until their tenant has been migrated. Any questions on grouping and targeting timelines, please contact our [migration team](mailto:intunegrps@microsoft.com).-->

[Android for Work の Intune サポートに関する Microsoft からのお知らせをお読みください](https://blogs.technet.microsoft.com/enterprisemobility/2016/09/12/microsoft-intune-support-for-android-for-work/)。

次の Intune トピックは、Android for Work に関する新しい情報と更新情報を扱っています。

IT プロフェッショナル向け:
- [Android for Work のセットアップ](/intune/deploy-use/set-up-android-for-work)
<!--- [Nathan Bigman's resource access topics]()-->
- [Intune で Exchange Online と新しい Exchange Online Dedicated への電子メール アクセスを制限する](/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune)
- [Intune で Exchange On-premises と従来の Exchange Online Dedicated への電子メール アクセスを制限する](/intune/deploy-use/restrict-access-to-exchange-onpremises-with-microsoft-intune)
- [Android for Work のコンプライアンス ポリシー設定](/intune/deploy-use/afw-compliance-policy-settings-in-microsoft-intune)
- [Android for Work アプリを展開する方法](/intune/deploy-use/android-for-work-apps)
- [モバイル アプリ構成ポリシーを使用した Android for Work アプリの構成](/intune/deploy-use/afw-app-configuration-policy)
- [Android for Work のポリシー設定](/intune/deploy-use/android-for-work-policy-settings-in-microsoft-intune)

エンド ユーザー向け:
- [仕事用プロファイルを作成するとどうなりますか](/intune/enduser/what-happens-when-you-create-a-work-profile-android)
- [Intune での仕事用プロファイルの作成とデバイスの登録](/intune/enduser/create-a-work-profile-and-enroll-your-device-in-intune-android)

### <a name="lookout-integration-to-protect-ios-devices"></a>iOS デバイスを保護するため Lookout 統合
10 月、Microsoft は、デバイス上のマルウェアやリスクの高いアプリなどを検出して iOS モバイル デバイスを保護するため、Lookout のモバイル脅威保護ソリューションに統合します。 Lookout のソリューションにより、構成可能な脅威レベルを決定できます。 Intune に、Lookout によるリスク評価に基づいてデバイスのコンプライアンスを判断するためのコンプライアンス ポリシー ルールを作成できます。 条件付きアクセス ポリシーを使用すると、デバイスのコンプライアンス状態に基づいて、会社のリソースへのアクセスを許可したりブロックしたりできます。

非準拠 iOS デバイスのエンド ユーザーは登録が求められ、会社のデータへのアクセス権を得るにはデバイスへの Lookout for Work アプリケーションのインストール、アプリのアクティブ化、Lookout for Work アプリケーションで報告された驚異の修復が必要となります。 [Lookout for Work アプリを構成して展開する](/intune/deploy-use/configure-and-deploy-lookout-for-work-apps)方法について説明します。
<!--TFS 1319493-->

<!--### New Microsoft Intune Company Portal available for Windows 10 devices
Microsoft is releasing a new [Microsoft Intune Company Portal for Windows 10 devices](https://go.microsoft.com/fwlink/?linkid=830663). This app, which leverages the new Windows 10 Universal format, will provide the user with an updated user experience within the app and identical experiences across all Windows 10 devices, PC and Mobile alike, while still enabling all the same functionality that they are using today.

The new app will also allow users to leverage additional platform features like single sign-on (SSO) and certificate-based authentication on Windows 10 devices. The app will be made available as an upgrade to the existing Windows 8.1 Company Portal and Windows Phone 8.1 Company Portal installs from the Windows Store.-->

### <a name="intune-app-wrapping-tool-for-android"></a>Android 用 Intune アプリ ラッピング ツール
Intune アプリ ラッピング ツールを使うと、アプリで Intune モバイル アプリケーション管理 (MAM) ポリシーを使用できるようになります。 デバイスの登録を必要としない Intune MAM ポリシーのサポートが開始されました。

### <a name="manage-printing-from-apps-managed-using-mam-policies"></a>MAM ポリシーを使用して管理されたアプリケーションから印刷する
MAM ポリシーを使用しているアプリから会社データが印刷されるのを防ぐことができるようになりました。 この設定は、[Azure ポータル](/Intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune)で利用することができ、[iOS](/Intune/deploy-use/ios-mam-policy-settings) デバイスと [Android](/Intune/deploy-use/android-mam-policy-settings) デバイスの両方でサポートされています。
<!--TFS 1014328-->

### <a name="support-for-fingerprints-on-android-devices"></a>Android デバイスでの指紋のサポート
Android モバイル アプリ管理 (MAM) ポリシーでは、ユーザーの PIN を入力するのではなく、ユーザーの指紋を使用してアプリにアクセスできるようになりました。 このポリシー、および他の [Android 用モバイル アプリ管理ポリシーの設定についてはここ](/Intune/deploy-use/android-mam-policy-settings)を参照してください。

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

非準拠デバイスのエンド ユーザーは登録が求められ、アクセス権を得るには Android デバイスへの Lookout for Work アプリケーションのインストール、アプリのアクティブ化、Lookout for Work アプリケーションで報告された驚異の修復が必要となります。 詳細については、「[Restrict access based on device, network, and application risk](https://docs.microsoft.com/en-us/intune/deploy-use/restrict-access-based-on-device-network-app-risk)」 (デバイス、ネットワーク、アプリケーションのリスクに基づいてアクセスを制限する) を参照してください。


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
Intune 製品で使用されている用語を説明する新しい[用語集トピック](https://docs.microsoft.com/intune/understand-explore/intune-glossary)をライブラリに追加しました。

## <a name="august-2016"></a>2016 年 8 月
### <a name="app-management"></a>アプリ管理
<!---@Barry, I created the buckets of App management, Device management, etc but am not tied to them. Just wanted to break up and organize the feature list. If you're going to take over the Company Portal section, please talk to Stacie about how she's been organizing it. --->

__iOS 9.3 で表示されないアプリと表示されるアプリ__ iOS 9.3 以降を実行するデバイスでは、iOS の一般構成ポリシーの表示されないアプリと表示されるアプリのリストを使用して次のことができます。
- ユーザーに対して表示されないアプリの一覧を指定します。 ユーザーはこのようなアプリを表示または起動できません。
- ユーザーが表示および起動できるアプリの一覧を指定します。 他のアプリは表示または起動できません。

ユーザー自身が展開したアプリと、Messages や Notes などの iOS 組み込みアプリの両方を指定できます。 詳細については、「[Microsoft Intune の iOS ポリシー設定](https://docs.microsoft.com/intune/deploy-use/ios-policy-settings-in-microsoft-intune)」を参照してください。
<!---TFS 1279009 checked--->
__Samsung KNOX デバイスでの許可するアプリとブロックするアプリのポリシー__Samsung KNOX デバイスでは、次のいずれかを作成できるカスタム ポリシーを構成できます。
- デバイスでの実行をブロックするアプリの一覧。 ブロック リストで定義されているアプリは、インストールされている場合でも、デバイスでアクティブにできません。
- デバイスのユーザーが Google Play ストアからインストールできるアプリの一覧。 他のアプリはストアからインストールできません。

これらの設定は、Samsung KNOX を実行するデバイスでのみ使用できます。
詳細については、「[カスタム ポリシーを使用して、Samsung KNOX デバイス用のアプリを許可またはブロックする](https://docs.microsoft.com/en-us/intune/deploy-use/custom-policy-to-allow-and-block-samsung-knox-apps)」を参照してください。
<!---TFS 1311629 checked --->

__モバイル アプリケーション管理 (MAM) ポリシーと互換性のある新しいアプリ__ [iOS](https://itunes.apple.com/app/yammer/id289559439?mt=8) および [Android](https://play.google.com/store/apps/details?id=com.yammer.v1) 向けの Yammer アプリは、デバイスが登録されていてもいなくても、[Intune モバイル アプリケーション管理 (MAM) ポリシーと](/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)互換性があります。

MAM と互換性のある全アプリの一覧については、[Microsoft Intune アプリケーション パートナー](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-partners)のサイトをご覧ください。
<!--- TFS 1252335 & 1252336 checked--->


<!--- I started putting TFS numbers in the What's Coming topic and found it helpful when updating the What's New. Up to you if you want to continue. --->

__Intune Viewer アプリ__ 新しい RMS 共有アプリのリリースに伴い、2016 年 8 月以降、次の Intune Viewer アプリを削除する予定です。
- Intune AV Viewer
- Intune PDF Viewer
- Google Play の Android 用 Intune Image Viewer

Intune Viewer アプリを使用する代わりに、[Android 用の新しい Rights Management アプリ (RMS 共有) ](https://docs.microsoft.com/en-us/intune/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune#viewing-media-files-with-the-rights-management-sharing-app)を使用することをお勧めします。そうすることで、3 つのアプリを個別にではなく、1 つのアプリを展開して、Android デバイス上の企業ファイルを安全に表示することができます。 Intune Viewer アプリがサポートされなくなると、Google ストアから削除され、その後使用することができなくなります。

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
__Intune グループから Azure Active Directory グループへの移行 (2016年 9 月以降)__ Intune は、Intune でのユーザーとデバイスのグループとして Azure Active Directory (AAD) のセキュリティ グループを使用する、新しいグループ管理エクスペリエンスを作成しています。 これらのグループは、**新しい Azure ベースの Intune 管理ポータルの導入時**に、すべてのグループの管理、ポリシーの展開、およびプロファイルの展開に使用されます。

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
<!---@Barry, we started listing service deprecations earlier this summer. --->
- **iOS ポータル サイト アプリのサポートの変更**<br/>
9 月には、iOS 用 Microsoft Intune ポータル サイト アプリのすべてのユーザーが、アプリの最新バージョンを使用するように要求されます。 新しいユーザーは最新バージョンのみをダウンロードでき、現在のユーザーは最新バージョンへの更新を求められます。 最新バージョンを使用するには iOS 8.0 以降が必要であり、デバイスで以前の iOS バージョンを実行している場合は、デバイスを iOS 8.0 以降に更新したうえでポータル サイト アプリを最新バージョンに更新するまで、ポータル サイトを使用できず、登録することもできません。 iOS 8.0 以前のバージョンを実行している登録済みのデバイスは、引き続き管理対象であり、Intune 管理コンソールに表示されます。  

- **iOS Managed Browser の最小バージョンの 8.0 への更新**<br/>
8 月、Intune は iOS 8.0 以降を実行するデバイスのみをサポートする、iOS 用の最新の Microsoft Intune Managed Browser アプリをリリースします。 iOS 7.1 デバイスでは、既存の Managed Browser アプリを使用することができますが、新しい Managed Browser の機能にアクセスしてフル活用できるように、ユーザーに iOS 8.0 以降に更新することをお勧めしてください。  
<!---TFS 1313253--->

- **Windows 8 および Windows Phone 8 用のポータル サイト アプリは、2016 年 9 月以降非推奨になります** <br/>
Microsoft Intune は、2016 年 9 月以降、Windows Phone 8 および Windows 8 プラットフォーム用 Microsoft Intune ポータル サイト アプリのサポートを終了します。 デバイスを Windows 8.1 および Windows Phone 8.1 に更新し、対応する Windows 8.1 および Windows Phone 8.1 のポータル サイト アプリを使用して、更新したデバイスへのアプリの配布を続行します。
<!---TFS 1255391--->

<!--- - **Custom Group Targeting of Notification Rules Removal.**<br/>
Intune notification rules define who an email alert will be sent to from Intune. Currently, you can configure notification rules to send emails to all users of devices in an Intune device group that you created. From around June 1st 2016 moving forward, targeting user-created groups will no longer be supported.

    Today, to target a notification rule to a group you created from the Microsoft Intune administration console, you would take the following steps:

    In the **Admin** workspace, click **Notification Rules** > **Create New Rule**

    In step two of the Create Notification Rule Wizard, select the device groups which the rule will target. This step, “select device groups”, is being removed from the Intune Console.

    The preliminary timeline for this change is as follows:
    - In August, 2016, new tenants will not see step two of the Create Notification Rule Wizard. Exiting tenants are unaffected.
    - Around September, 2016, some existing tenants will not see the “select device groups” in the wizard.
    - Around November, 2016, we expect that all tenants will not see the “select device groups” in the wizard.

--->
## <a name="july-2016"></a>2016 年 7 月
### <a name="app-management"></a>アプリ管理

__アプリのプロビジョニング プロファイルの更新エクスペリエンスを向上__ Apple iOS 基幹業務モバイル アプリは、プロビジョニング プロファイルを含み、証明書で署名されたコードと共に構築されます。 iOS デバイスでアプリを実行すると、iOS により iOS アプリの整合性の確認と、プロビジョニング プロファイルで定義されたポリシーの施行が行われます。

アプリの署名に使用するエンタープライズ署名証明書は、通常 3 年間は継続します。 ただし、プロビジョニング プロファイルは 1 年後に期限が切れます。 この更新により、証明書がまだ有効である期間中、Intune には、有効期限が近づいているアプリを持つデバイスに新しいプロビジョニング プロファイルのポリシーを事前に展開するツールが用意されます。 詳細については、「[Use iOS mobile provisioning profile policies to keep your line of business apps up to date (基幹業務アプリケーションを常に最新の状態に保つために iOS モバイル プロビジョニング プロファイル ポリシーを使用する)](/intune/deploy-use/ios-mobile-app-provisioning-profiles)」を参照してください。
<!--- TFS 1280247--->

__Intune アプリ用の Xamarin SDK の提供開始__ Intune アプリ SDK Xamarin コンポーネントを使用すると、Xamarin でビルドされたモバイル iOS および Android アプリで Intune のモバイル アプリ管理機能を有効にすることができます。 [Xamarin ストア](https://components.xamarin.com/view/Microsoft.Intune.MAM)または、[Microsoft Intune の Github ページ](https://github.com/msintuneappsdk)でコンポーネントを見つけることができます。
<!--- TFS 1061478 --->

### <a name="device-management"></a>デバイス管理
__デバイス登録数上限の増加__ Intune は、構成可能なデバイスの最大登録数をユーザーごとに 5 から 15 デバイスまで増加しました。
<!---TFS 1289896 --->

__Intune クライアント ソフトウェアを実行する Windows PC のための TeamViewer の統合__
 Intune クライアントを実行する Windows PC の [TeamViewer](https://www.teamviewer.com) 統合により、Windows PC とのリモート アシスタント セッションを確立して、エンド ユーザーのヘルプ デスク部門をサポートできるようになります。 Windows 7、8、8.1、10 が対象となります。 詳細については、「[Microsoft Intune コンピューター クライアントを使用した一般的な Windows PC 管理タスク](/intune/deploy-use/common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client)」を参照してください。
<!---TFS 1284856--->

### <a name="company-portal-updates"></a>ポータル サイトの更新

__ポータル Web サイト__
- **Windows デバイス登録時のエンドユーザー エクスペリエンスの向上**<br/>
条件付きアクセスを使用している場合の、ポータル サイト Web サイトで Windows 8.1、Windows 10 デスクトップ、および Windows 10 Mobile の登録手順が明確化されました。 今後は、「デバイス登録」および「社内参加」の手順が個別に表示されます。そのため、社内参加 (WPJ) の失敗後にデバイスの状態を確認し、プロセスを完了することが簡単になります。 この手順の分離により、IT 管理者のトラブルシューティングのプロセスも簡略化されることが見込まれます。 これまで、エンド ユーザーが登録しようとして、WPJ を除くすべての登録が成功した場合、登録されたデバイスがデバイス一覧に表示されないため識別できず、ユーザーの混乱の原因となっていました。

__Android__
- **Android 用ポータル サイト アプリ**<br/>
Android エンド ユーザーに自分のデバイスに必要な証明書がないことを示すエラー メッセージが表示される場合、[How to resolve this (この問題解決する方法)] ボタンをタップすると、欠落している証明書をインストールするための[手順](/intune/enduser/your-device-is-missing-a-required-certificate-android#your-device-is-missing-a-certificate-required-by-your-it-administrator)を取得できます。 ユーザーが手順を完了しても、追加の「証明書が見つかりません」というエラー メッセージが表示される場合は、IT 管理者に連絡し、この[リンク](/intune/troubleshoot/troubleshoot-device-enrollment-in-intune#android-certificate-issues)を提供することが求められます。このリンクには、証明書の問題を解決するために IT 管理者が使用できる手順が含まれています。

- **登録済みデバイスへのサイド ロード アプリのインストールの制限**<br/>
Android 用 Intune ポータル サイト アプリを使用してデバイスを Intune に登録している場合を除き、Android デバイスは、ポータル サイト Web サイトを通じてアプリケーションをインストールすることができなくなります。
<!---TFS 1299082--->

__iOS__
- **iOS ポータル サイト アプリのデバイス登録マネージャー アカウントへの変更**<br/>
パフォーマンスと拡張性を高めるために、Intune において、iOS のポータル サイト アプリの [**デバイス**] ウィンドウには今後、デバイス登録マネージャー (DEM) のデバイスの一部が表示されなくなります。 アプリを実行しているローカル デバイスのみ、ポータル サイト アプリ経由で登録されている場合にだけ表示されます。

ローカル デバイスに対する操作は DEM で実行できますが、他の登録デバイスのリモート管理は、Intune 管理コンソールから実行する必要があります。 また、Apple Device Enrollment Program または Apple Configurator ツールでの DEM アカウントの使用は廃止されます。 共有 iOS デバイスに関しては、どちらの登録手段も既にユーザーレスの登録がサポートされています。

共有デバイスのユーザーレスの登録が利用できない場合のみ DEM アカウントを使用してください。 詳細については、「[Microsoft Intune のデバイス登録マネージャーを使用した企業所有のデバイスの登録](https://docs.microsoft.com/en-us/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune)」を参照してください。
<!---TFS 1233681--->

### <a name="change-of-names-for-windows-features"></a>Windows 機能の名前の変更
- [Microsoft Passport for Windows](/intune/deploy-use/control-microsoft-passport-settings-on-devices-with-microsoft-intune) は **Windows Hello for Business** と呼ばれるようになりました。
- [エンタープライズ データ保護](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-intune)は **Windows Information Protection** と呼ばれるようになりました。


<!--HONumber=Jan17_HO2-->


