---
title: 初期エディション - Microsoft Intune
titlesuffix: ''
description: Microsoft Intune の初期エディション
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/04/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 19994745a232a362d6bba0f09ed3934e492a17ed
ms.sourcegitcommit: 2f431f122ce3ee6b5d0cdb04a0b748d00f83e295
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2019
ms.locfileid: "56265674"
---
# <a name="the-early-edition-for-microsoft-intune---february-2019"></a>Microsoft Intune の初期エディション - 2019 年 2 月

> [!Note]
> NDA 通知: Intune に関して以下の機能が現在開発されています。 この情報は、NDA に基づき、非常に限られた範囲で共有されます。 Twitter、UserVoice、Reddit などの、ソーシャル メディアやパブリック Web サイトには、この情報を投稿しないでください。 

**初期エディション**では、Microsoft Intune の今後のリリースで予定されている、NDA に基づいて共有される新機能のリストを提供します。 ここに記載されている情報は、限られた範囲について開示されたものであり、また今後変更される可能性があります。 ツイート、UserVoice への投稿、またそれ以外の方法で、社外でこの情報を共有したりしないでください。 ここに挙げられている機能は、発売日に間に合わない可能性があり、その場合は将来のリリースを待たなければなりません。 正式なリリースに向けてパイロット (フライト) テスト中の機能もあります。 ご不明な点や懸念される事項がある場合は、Microsoft 製品グループにお問い合わせください。

このページは定期的に更新されます。 適宜確認してください。

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Azure Portal での Intune
<!-- 1902 start-->

### <a name="powershell-scripts-can-run-in-a-64-bit-host-on-64-bit-devices----1862675----"></a>PowerShell スクリプトが 64 ビット デバイスの 64 ビット ホストで実行できる <!-- 1862675  -->
PowerShell スクリプトをデバイス構成プロファイルに追加すると、64 ビット オペレーティング システムであっても、スクリプトは常に 32 ビットで実行されます。 この更新により、管理者はスクリプトを実行 64 ビット デバイスの 64 ビット PowerShell ホストでスクリプトを実行できます (**[デバイス構成]** > **[PowerShell スクリプト]** > **[追加]** > **[構成]** > **[Run script in 64 bit PowerShell Host]\(64 ビット PowerShell ホストでスクリプトを実行\)**)。
PowerShell の使用に関する詳細については、[Intune での PowerShell スクリプト](intune-management-extension.md)に関するページを参照してください。
適用先:Windows 10 以降

### <a name="rename-an-enrolled-windows-device----1911112----"></a>登録済み Windows デバイスの名前変更 <!-- 1911112  -->
登録済み Windows 10 デバイス (RS4 以降) の名前を変更できるようになります。 これを行うには、**[Intune]** > **[デバイス]** > **[すべてのデバイス]**> デバイスを選択 > **[デバイス名の変更]** の順に選択します。

### <a name="assign-scep-certificates-to-a-userless-macos-device-------2340521-----"></a>ユーザーレス macOS デバイスに SCEP 証明書を割り当てる    <!-- 2340521   -->
Simple Certificate Enrollment Protocol (SCEP) 証明書をユーザーレス macOS デバイスに割り当てて、証明書を Wi-Fi または VPN プロファイルに関連付けることができるようになります。 これにより既にある既存のサポートを拡張して [Windows、iOS、Android を実行するユーザーレス デバイスに証明書を割り当て](certificates-scep-configure.md#create-a-scep-certificate-profile)ます。

### <a name="intune-conditional-access-ui-update------2432313----"></a>Intune の条件付きアクセスの UI の更新   <!-- 2432313  -->
Intune コンソール内の条件付きアクセスの UI の改善を行っています。 たとえば、次のとおりです。
- Intune の *条件付きアクセス* ブレードを Azure Active Directory のブレードに置き換え。 これにより、Azure AD テクノロジのまま条件付きアクセスのすべての設定と構成にアクセスできるようになります。
- *Exchange サービス コネクタ*のセットアップを現在の*オンプレミス アクセス* ブレードに再配置。 ブレードの名称も *Exchange へのアクセス* に変更されています。 この変更は、Exchange Online とオンプレミスに関する詳細を構成および監視する場所に統合されます。

### <a name="intune-will-leverage-google-play-protect-apis-on-android-devices----2577355----"></a>Android デバイスで Intune が Google Play Protect API を利用する <!-- 2577355  -->
一部の IT 管理者は、エンド ユーザーが自身の携帯電話を root 化したり脱獄させたりする可能性がある BYOD 環境に直面しています。 この行動は、悪意のないものであっても、エンド ユーザーのデバイス上にある組織のデータを保護するために設定されている多くの Intune ポリシーをバイパスする結果となります。 したがって、Intune では、登録済みのデバイスと未登録のデバイスの両方にルート化および脱獄の検出を提供しています。 このリリースでは、Intune は未登録のデバイスに対する既存のルート検出チェックに追加するため、Google Play Protect API を利用します。 Google では発生するルート検出チェックのすべてを共有していませんが、これらの API により、デバイスのカスタマイズ化から何らかの理由で自身のデバイスをルート化しているユーザーを検出して、古いデバイスで新しい OS の更新プログラムを取得できるようにすることを想定しています。 これにより、これらのユーザーが会社のデータにアクセスすることをブロックしたり、これらのユーザーの会社のアカウントをポリシーを有効にしたアプリからワイプしたりすることができます。 付加価値として、IT 管理者は Intune App Protection ブレード内で複数の更新されたレポートが使用できるようになります。"フラグ付きのユーザー" レポートでは、Google Play Protect の SafetyNet API スキャンにより検出されたユーザーが示されます。"潜在的に有害なアプリ" レポートでは、Google の Verify Apps API スキャンにより検出されたアプリが示されます。 この機能は Android で使用できます。 

### <a name="win32-app-information-available-in-troubleshooting-blade----2617342------"></a>トラブルシューティング ブレードで利用可能な Win32 アプリ情報 <!-- 2617342    -->
Intune のアプリの**トラブルシューティング** ブレードから、Win32 アプリのインストールのエラー ログ ファイルを収集できるようになります。 アプリのインストールに関するトラブルシューティングについて詳しくは、「[アプリのインストールに関する問題のトラブルシューティング](troubleshoot-app-install.md)」をご覧ください。

### <a name="kiosk-browser-and-microsoft-edge-browser-apps-can-run-on-windows-10-devices-in-kiosk-mode----2935135----"></a>キオスク ブラウザーと Microsoft Edge ブラウザー アプリを、キオスク モードの Windows 10 デバイスで実行できる <!-- 2935135  -->
キオスク モードの Windows 10 デバイスを使用して、1 つまたは複数のアプリを実行することができます。 この更新プログラムには、キオスク モードでブラウザー アプリを使用するための次のような複数の変更が含まれています。

- Microsoft Edge ブラウザーまたはキオスク ブラウザーを追加して、キオスク デバイスでアプリとして実行します (**[デバイス構成]** > **[プロファイル]** > **[新しいプロファイル]** >  プラットフォームに **[Windows 10 以降]** を選択し、プロファイルの種類に **[キオスク]** を選択します)。
- Microsoft Edge をキオスク モードで実行できる (またはできない) ように制限します (**[デバイス構成]** > **[プロファイル]** > **[新しいプロファイル]** >  プラットフォームに **[Windows 10 以降]** を選択し、プロファイルの種類に **[デバイスの制限]** を選択し、**[Microsoft Edge ブラウザー]** を選択します)。 キオスク モードで実行されていない場合、エンド ユーザーが Microsoft Edge の設定を変更できます。

現在の設定の一覧については、次を参照してください。

- [Windows 10 以降のデバイスをキオスクとして実行するための設定](kiosk-settings-windows.md)
- [Microsoft Edge ブラウザー デバイスの制限](device-restrictions-windows-10.md#microsoft-edge-browser)

適用先:Windows 10 以降

### <a name="auto-assign-scope-tags-to-resources-created-by-an-admin-with-that-scope----3173823----"></a>自動割り当てスコープにより、そのスコープを使用して管理者によって作成されたリソースにタグが割り当てられる <!-- 3173823  -->
管理者がリソースを作成するときに、管理者に割り当てられた任意のスコープのタグが自動的にこれらの新しいリソースに割り当てられます。

### <a name="new-device-restriction-settings-for-ios-and-macos-devices----3448774---"></a>iOS および macOS デバイスの新しいデバイス制限の設定 <!-- 3448774 -->
iOS および macOS を実行するデバイスで一部の設定と機能を制限することができます (**[デバイス構成]** > **[プロファイル]** > **[新しいプロファイル]** >  プラットフォームに **[iOS]** または **[macOS]** を選択し、プロファイルの種類に **[デバイスの制限]** を選択します)。 この更新プログラムにより、制御可能な機能と設定がさらに追加されます。これには、画面の表示時間の設定、eSIM 設定とセルラー プランの変更、ソフトウェア更新プログラムに関するユーザーへの表示の遅延、コンテンツ キャッシングのブロックなどが含まれます。
制限可能な現在の機能と設定を確認するには、次を参照してください。
- [iOS デバイスの制限設定](device-restrictions-ios.md)
- [macOS デバイスの制限設定](device-restrictions-macos.md)

適用先:
- iOS
- macOS

### <a name="failed-enrollment-report-moves-to-the-device-enrollment-blade----3560202---"></a>失敗した登録レポートをデバイスの登録ブレードに移動 <!-- 3560202 -->
**失敗した登録**レポートは、**デバイスの登録**ブレードの **[監視]** セクションに移動されます。 2 つの新しい列 ([登録方法] と [OS のバージョン]) も追加されます。

### <a name="change-kiosk-to-dedicated-devices----3598402----"></a>"キオスク" を "専用デバイス" に変更 <!-- 3598402  -->
Android の用語と合わせるため、**[Android エンタープライズ]** > **[デバイスの所有者]** > **[デバイスの制限]** のデバイス構成プロファイルの下の **[キオスク]** は、**[専用デバイス]** に変更されます。

### <a name="safari-and-delaying-user-software-update-visibility-ios-settings-are-moving-in-the-intune-ui----3640850--3803313----"></a>Safari の設定と、iOS のソフトウェア更新プログラムのユーザーへの表示を遅らせる設定を Intune UI の中で移動<!-- 3640850, , 3803313  -->
iOS デバイスの場合、Safari を設定し、ソフトウェア更新プログラムを構成できます。 この更新プログラムでは、これらの設定が Intune UI のさまざまな部分に移動されています。

- Safari の設定は、**[Safari]** (**[デバイス構成]** > **[プロファイル]** > **[新しいプロファイル]** >  プラットフォームに **[iOS]** を選択し、プロファイルの種類に **[デバイスの制限]** を選択します) から **[組み込みアプリ]** に移動されています。 
- **[Delaying user software update visibility for supervised iOS devices]\(監視対象の iOS デバイスのソフトウェア更新プログラムのユーザーへの表示を遅らせる\)** 設定 (**[ソフトウェア更新プログラム]** >  **[iOS のポリシーを更新する]**) は、**[デバイスの制限]** > **[全般]** に移動されています。

現在の設定の一覧については、[iOS デバイスの制限事項](device-restrictions-ios.md)と[iOS ソフトウェアの更新プログラム](software-updates-ios.md)に関するページを参照してください。

適用先: 
- iOS

### <a name="enabling-restrictions-in-the-device-settings-is-renamed-to-screen-time-on-ios-devices----3699164----"></a>iOS デバイスで、[デバイス設定での制限の有効化] 設定が [画面の表示時間] に名前が変更される <!-- 3699164  -->
監視対象の iOS デバイスで、**[デバイス設定での制限の有効化]** を構成することができます (**[デバイス構成]** > **[プロファイル]** > **[新しいプロファイル]** >  プラットフォームに **[iOS]** を選択し、プロファイルの種類に **[デバイスの制限]** を選択し、**[全般]** を選択します)。 この更新プログラムでは、この設定の名前が **[画面の表示時間 (監視モードのみ)]** に変更されています。 動作は同じです。 具体的には次のとおりです。 

- iOS 11.4.1 以前のバージョン:**[ブロック]** は、エンド ユーザーがデバイス設定で独自の制限を設定できないようにします。 
- iOS 12.0 以降:**[ブロック]** は、エンド ユーザーがデバイス設定 (コンテンツとプライバシーの制限を含む) で独自の**画面の表示時間**を設定できないようにします。 iOS 12.0 にアップグレードされたデバイスでは、デバイスの設定に制限のタブが表示されなくなります。 これらの設定は **[画面の表示時間]** にあります。 

現在の設定の一覧については、[iOS デバイスの制限事項](device-restrictions-ios.md)に関するページを参照してください。

適用先: 
- iOS

### <a name="app-status-details-for-ios-apps----3761235----"></a>iOS アプリの状態の詳細 <!-- 3761235  -->
以下に関するアプリのインストールの新しいエラー メッセージが追加されます。
- 共有 iPad に VPP アプリをインストールするときのエラー
- アプリ ストアが無効になっているときのエラー
- アプリの VPP ライセンスが見つからない
- MDM プロバイダーでシステム アプリのインストールが失敗する
- デバイスが紛失モードまたはキオスク モードの場合に、アプリのインストールが失敗する
- ユーザーが App Store にサインインしていないときに、アプリのインストールが失敗する

Intune で、**[クライアント アプリ]** > **[アプリ]** > "アプリ名" > **[デバイスのインストール状態]** の順に選択します。 **[状態の詳細]** 列で新しいエラー メッセージが使用できるようになります。

<!-- 1901 start -->

### <a name="deployment-of-online-licensed-microsoft-store-for-business-apps----1672660----"></a>オンラインでライセンスされたビジネス向け Microsoft Store アプリの展開 <!-- 1672660  -->
オンラインでライセンスされた必要なビジネス向け Microsoft Store アプリをデバイスのコンテキストで割り当てることができます。 このようにして、ビジネス向け Microsoft Store アプリを展開すると、デバイス上のすべてのユーザーにアプリをインストールできます。 対象は Windows 10 RS4 以上のデスクトップ デバイスのみです。 デバイスのコンテキストでインストールするオプションは、MSFB オンラインのライセンスされたアプリのクライアント アプリの割り当てページにあります。

<!-- 1812 start -->

### <a name="android-enterprise-app-we-app-deployment----1171203---"></a>Android エンタープライズ APP-WE アプリの展開 <!-- 1171203 -->
登録のないアプリ保護ポリシー (APP-WE) の展開シナリオでの Android では、managed Google Play を使用してストア アプリと LOB アプリをユーザーに展開できます。 具体的には、IT はエンド ユーザーに、不明なソースからのインストールを許可することによってデバイスのセキュリティ状態を損なう必要がないアプリ カタログとインストール エクスペリエンスを提供できます。 さらに、この展開シナリオでは、向上したエンド ユーザー エクスペリエンスが提供されます。

### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation-----1927359---"></a>Intune ポリシーでの認証方法とポータル サイト アプリのインストールの更新 <!-- 1927359 -->
Apple の会社用デバイスの登録方法のいずれかを使ってセットアップ アシスタント経由で既に登録されているデバイスの場合、Intune では、特定のデバイスで App Store からインストールされる場合に、ポータル サイト アプリがサポートされなくなります。 この変更は、登録時に Apple セットアップ アシスタントで認証を行う場合にのみ関係があります。 また、この変更は、以下から登録される iOS デバイスのみに影響します。  
* Apple Configurator
* Apple Business Manager
* Apple School Manager
* Apple Device Enrollment Program (DEP)

App Store からポータル サイト アプリをインストールした後、これらのデバイスを登録しようとすると、エラーが発生します。 登録時に Intune によって自動的にプッシュされた場合、これらのデバイスはポータル サイトだけを使用することが期待されます。 Azure portal での Intune の登録プロファイルは、デバイスの認証方法およびポータル サイト アプリを受信するかどうかを指定できるように更新されます。 DEP デバイス ユーザーがポータル サイトを使用するようにしたい場合は、登録プロファイルでユーザー設定を指定する必要があります。 さらに、ポータル サイト アプリの **[デバイスの特定]** 画面はまもなく古くなります。  
既に登録されている DEP デバイスにポータル サイトをインストールするには、Intune で [クライアント アプリ] に移動し、アプリ構成ポリシーでマネージド アプリとしてプッシュする必要があります。 これらの手順を実行する方法の詳細については、将来のドキュメントで説明します。

### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>管理用テンプレートがパブリック プレビューになり、専用の構成プロファイルに移動される <!-- 3322847 -->
Intune の管理用テンプレート (**[デバイス構成]** > **[管理用テンプレート]**) は現在、プライベート プレビュー段階です。 この更新プログラムでは: 管理用テンプレートには Intune で管理可能な約 300 の設定が含まれます。 以前は、これらの設定はグループ ポリシー エディターにのみ存在しました。
管理用テンプレートはパブリック プレビューで使用できます。管理用テンプレートは、**[デバイス構成]** > **[管理用テンプレート]** から、**[デバイス構成]** > **[プロファイル]** >**[プロファイルの作成]** を選択し、**[プラットフォーム]** で **[Windows 10 以降]** を選択し、**[プロファイルの種類]** で **[管理用テンプレート]** を選択した場所に移動されています。
レポートが有効にされます。適用先: Windows 10 以降

### <a name="intune-macos-company-portal-dark-mode----3300524---"></a>Intune の macOS ポータル サイトのダーク モード <!-- 3300524 -->
Intune の macOS ポータル サイトで、macOS 用にダーク モードがサポートされるようになりました。 macOS 10.14 以降のデバイスでダーク モードを有効にすると、Intune ポータル サイトではそのモードの色に外観が調整されます。

<!-- 1809 start -->  

### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>Web データ用のアプリ保護ポリシー (APP) 設定 <!-- 2662995 -->
Android デバイスと iOS デバイスの両方での Web コンテンツに対する APP ポリシー設定は、http リンクと https Web リンクの両方の処理、ならびに iOS ユニバーサル リンクおよび Android アプリ リンクを介したデータ転送の処理をより適切に行えるように更新されます。  

<!-- 1808 start -->

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>別の MDM によって使用される Apple VPP トークン <!-- 1488946 -->
Intune では、Apple のボリューム購入プログラム (VPP) トークンが Intune と別の MDM の両方で使用されている場合、詳細が検出され、表示されます。

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>[デバイスのポリシー準拠] ダッシュボードのデバイスが廃止に <!-- 1981119 -->
今後の更新で、廃止になっているデバイスが [デバイスのポリシー準拠] ダッシュボードから削除されます。 それにより、コンプライアンス番号が変更されます。

## <a name="notices"></a>通知

現在のところ、アクティブな通知はありません。

### <a name="see-also"></a>関連項目
最近の開発状況について詳しくは、「[Microsoft Intune の新機能](whats-new.md)」をご覧ください。
