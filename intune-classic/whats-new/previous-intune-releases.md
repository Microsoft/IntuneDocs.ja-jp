---
title: 以前のリリース
description: ''
keywords: ''
author: barlanmsft
ms.author: barlan
manager: dougeby
ms.date: 02/13/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 45dad14a-d412-488d-bb1e-ad990ea503df
ROBOTS: NOINDEX,NOFOLLOW
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 76e53cabba9b684170d659ae5b8ef884bfe9abaa
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2018
---
# <a name="previous-intune-releases"></a>以前の Intune のリリース

このページは、「[Microsoft Intune の新機能](whats-new-in-microsoft-intune.md)」で発表された内容の一覧です。

[!INCLUDE[wit_nextref](../includes/whats-new-last-six-months.md)]

## <a name="july-2016"></a>2016 年 7 月

### <a name="app-management"></a>アプリ管理

__アプリのプロビジョニング プロファイルの更新エクスペリエンスを向上__ Apple iOS 基幹業務モバイル アプリは、プロビジョニング プロファイルを含み、証明書で署名されたコードと共に構築されます。 iOS デバイスでアプリを実行すると、iOS により iOS アプリの整合性の確認と、プロビジョニング プロファイルで定義されたポリシーの施行が行われます。

アプリの署名に使用するエンタープライズ署名証明書は、通常 3 年間は継続します。 ただし、プロビジョニング プロファイルは 1 年後に期限が切れます。 この更新により、証明書がまだ有効である期間中、Intune には、有効期限が近づいているアプリを持つデバイスに新しいプロビジョニング プロファイルのポリシーを事前に展開するツールが用意されます。 詳細については、「[Use iOS mobile provisioning profile policies to keep your line of business apps up to date](/intune-classic/deploy-use/ios-mobile-app-provisioning-profiles)」(基幹業務アプリケーションを常に最新の状態に保つために iOS モバイル プロビジョニング プロファイル ポリシーを使用する) を参照してください。
<!--- TFS 1280247--->

__Intune アプリ用の Xamarin SDK の提供開始__ Intune App SDK Xamarin コンポーネントを使用すると、Xamarin でビルドされたモバイル iOS および Android アプリで Intune のモバイル アプリ管理機能を有効にすることができます。 [Xamarin ストア](https://components.xamarin.com/view/Microsoft.Intune.MAM)または、[Microsoft Intune の Github ページ](https://github.com/msintuneappsdk)でコンポーネントを見つけることができます。
<!--- TFS 1061478 --->

### <a name="device-management"></a>デバイス管理
__デバイス登録数上限の増加__ Intune は、構成可能なデバイスの最大登録数をユーザーごとに 5 から 15 デバイスまで増加しました。
<!---TFS 1289896 --->

__Intune クライアント ソフトウェアを実行する Windows PC のための TeamViewer の統合__
[TeamViewer](/intune-classic/deploy-use/common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client)。
<!---TFS 1284856--->

### <a name="company-portal-updates"></a>ポータル サイトの更新

__ポータル Web サイト__
- **Windows デバイス登録時のエンドユーザー エクスペリエンスの向上**<br/>
条件付きアクセスを使用している場合の、ポータル サイト Web サイトで Windows 8.1、Windows 10 デスクトップ、および Windows 10 Mobile の登録手順が明確化されました。 今後は、「デバイス登録」および「社内参加」の手順が個別に表示されます。そのため、社内参加 (WPJ) の失敗後にデバイスの状態を確認し、プロセスを完了することが簡単になります。 この手順の分離により、IT 管理者のトラブルシューティングのプロセスも簡略化されることが見込まれます。 これまで、エンド ユーザーが登録しようとして、WPJ を除くすべての登録が成功した場合、登録されたデバイスがデバイス一覧に表示されないため識別できず、ユーザーの混乱の原因となっていました。

__Android__
- **Android 用ポータル サイト アプリ**<br/>
Android エンド ユーザーに自分のデバイスに必要な証明書がないことを示すエラー メッセージが表示される場合、[How to resolve this (この問題解決する方法)] ボタンをタップすると、[手順](/intune-classic/troubleshoot/troubleshoot-device-enrollment-in-intune#android-certificate-issues)を取得できます。IT 管理者が証明書の問題を解決するために利用できる手順が記載されています。

- **登録済みデバイスへのサイド ロード アプリのインストールの制限**<br/>
Android 用 Intune ポータル サイト アプリを使用してデバイスを Intune に登録している場合を除き、Android デバイスは、ポータル サイト Web サイトを通じてアプリケーションをインストールすることができなくなります。
<!---TFS 1299082--->

__Android__
- **iOS ポータル サイト アプリのデバイス登録マネージャー アカウントへの変更**<br/>
パフォーマンスと拡張性を高めるために、Intune において、iOS のポータル サイト アプリの **[デバイス]** ウィンドウには今後、デバイス登録マネージャー (DEM) のデバイスの一部が表示されなくなります。 アプリを実行しているローカル デバイスのみ、ポータル サイト アプリ経由で登録されている場合にだけ表示されます。

ローカル デバイスに対する操作は DEM で実行できますが、他の登録デバイスのリモート管理は、Intune 管理コンソールから実行する必要があります。 また、Apple Device Enrollment Program または Apple Configurator ツールでの DEM アカウントの使用は廃止されます。 これらの両方の登録方法では、ユーザーを介さない共有 iOS デバイスの登録が既にサポートされています。

共有デバイスのユーザーレスの登録が利用できない場合のみ DEM アカウントを使用してください。 詳細については、「[Microsoft Intune のデバイス登録マネージャーを使用した企業所有のデバイスの登録](/intune-classic/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune)」を参照してください。
<!---TFS 1233681--->

### <a name="change-of-names-for-windows-features"></a>Windows 機能の名前の変更
- [Microsoft Passport for Windows](/intune-classic/deploy-use/control-microsoft-passport-settings-on-devices-with-microsoft-intune) は **Windows Hello for Business** と呼ばれるようになりました。
- [エンタープライズ データ保護](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-intune)は **Windows Information Protection** と呼ばれるようになりました。


## <a name="june-2016"></a>2016 年 6 月
### <a name="intune-service-health"></a>Intune のサービス正常性
Intune のサービス正常性に関する情報は他の Microsoft サービスと共に中央の場所に移動されました。 そのため、この情報は Office 365 管理ポータルの [サービス正常性] で参照できるようになりました。 詳細については、[このブログ投稿](https://blogs.technet.microsoft.com/enterprisemobility/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/)を参照してください。

### <a name="app-management"></a>アプリ管理
- **Windows 10 の強化されたエンタープライズ データ ポリシー構成のエクスペリエンス。** Windows 10 のエンタープライズ データ保護ポリシー構成のエクスペリエンスが、アプリ規則の作成、ネットワーク境界の定義の指定、その他のエンタープライズ データ保護の設定などにおいて強化されました。 詳細については、「[Create an enterprise data protection (EDP) policy using Microsoft Intune](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-intune)」(Microsoft Intune を使用してエンタープライズ データ保護 (EDP) ポリシーを作成する) を参照してください。


### <a name="device-management"></a>デバイス管理
- **望ましくない可能性があるアプリから保護するための Windows Defender ポリシー設定。** **望ましくない可能性があるアプリケーションの検出**という名前の新しい Windows Defender 設定が、Windows 10 Desktop と Mobile の全般構成ポリシーに追加されました。 この設定を使えば、Windows Defender によって望ましくない可能性があると判断されたソフトウェアの実行から、登録済みの Windows デスクトップ コンピューターを保護することができます。 このようなアプリケーションの実行からコンピューターを保護したり、望ましくない可能性があるアプリケーションがいつインストールされたのかを監査モードでレポートしたりできます。 詳細については、「[Microsoft Intune の Windows 10 ポリシー設定](/intune-classic/deploy-use/windows-10-policy-settings-in-microsoft-intune)」を参照してください。
<!---TFS 1244478--->

### <a name="conditional-access"></a>条件付きアクセス
- **Intune の Cisco ISE ネットワーク アクセス制御ポリシー。**  Cisco Identity Service Engine (ISE) 2.1 と Microsoft Intune の両方を使用する場合、ISE でネットワーク アクセス制御ポリシーを設定できます。

    このポリシーを使用すると、WiFi または VPN でネットワークに接続するデバイスは、アクセスが許可される前に、次の条件を満たすことが必要になります。

    * Intune で管理されていること
    * 展開されているすべての Intune コンプライアンス ポリシーに準拠していること

 準拠していないデバイスのエンド ユーザーは、アクセスを取得するために、デバイスを登録することと、コンプライアンス関連の問題を修正することを求められます。
- **ブラウザーの条件付きアクセス。** [Exchange Online](/intune-classic/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune) 用の条件付きアクセス ポリシーを設定すると、管理下にあって、かつ条件を満たした iOS デバイスと Android デバイス上のサポートされる Web ブラウザーに、Exchange Online と SharePoint Online へのアクセスを限定することができます。 Outlook Web Access (OWA) や SharePoint サイトにエンド ユーザーが iOS または Android デバイスでサインインしようとすると、そのデバイスを Intune に登録するよう求めるメッセージが表示されます。また条件を満たしていないことが問題になっている場合は、その問題を解消してから、サインインを試行するように求められます。
<!---TFS 1175844--->

- **Dynamics CRM Online では、条件付きアクセスをサポートしています。** [Dynamics CRM Online](/intune-classic/deploy-use/restrict-access-to-dynamics-crm-online-with-microsoft-intune) 用の条件付きアクセス ポリシーを設定すると、管理下にあって、かつ条件を満たした iOS デバイスと Android デバイスに、Dynamics CRM Online へのアクセスを限定することができます。 Dynamics CRM モバイル アプリにエンド ユーザーが iOS または Android でサインインしようとすると、Intune に登録するよう求めるメッセージが表示されます。また条件を満たしていないことが問題になっている場合は、その問題を修正してから、サインインを試行するように求められます。
<!---TFS1295358--->

### <a name="intune-company-portal-updates"></a>Intune 会社のポータルの更新

__Android 用ポータル サイト アプリ__

- IT 管理者が新しい [不明なソースからのアプリのインストールをデバイスが禁止することを必須にする (Android 4.0 以上)] ポリシーを適用すると、Android 4.0 以降のデバイスを使用するエンド ユーザーには、"不明なソースからのインストールを無効にする必要があります" というメッセージが表示されます。 ユーザーは、**[設定]** > **[セキュリティ]** を選択し、**[不明なソース]** を無効にする必要があります。 ユーザーは、コンプライアンス メッセージのリンクをクリックして、メッセージと、設定を無効にする必要がある理由に関する詳細[情報](/intune-user-help/you-are-asked-to-turn-off-unknown-sources-android)を確認できます。

- IT 管理者が新しい [セキュリティ上の脅威に対してデバイスがアプリのスキャンを有効にすることを必須にする (Android 4.0 以上)] ポリシーを適用すると、Android 4.0 以降のデバイスを使用するエンド ユーザーには、"端末をスキャンしてセキュリティ上の脅威を確認" というメッセージが表示されます。 ユーザーは、**[設定]** > **[Google]** > **[セキュリティ]** を選択し、**[端末をスキャンしてセキュリティ上の脅威を確認]** をオンにする必要があります。 ユーザーは、コンプライアンス メッセージのリンクをクリックして、メッセージと、設定を有効にする必要がある理由に関する詳細[情報](/intune-user-help/you-are-asked-to-turn-on-scan-device-for-security-threats-android)を確認できます。

- IT 管理者が新しい [USB デバッグの無効化を必須にする (Android 4.2 以上)] ポリシーを適用すると、Android 4.2 以降のデバイスを使用するエンド ユーザーには、"USB デバッグを無効にする必要があります" というメッセージが表示されます。 ユーザーは、**[設定]** > **[開発者オプション]** を選択し、**[USB デバッグ]** を無効にする必要があります。 ユーザーは、コンプライアンス メッセージのリンクをクリックして、メッセージと、設定を無効にする必要がある理由に関する詳細[情報](/intune-user-help/you-are-asked-to-turn-off-usb-debugging-android)を確認できます。

- IT 管理者が新しい [最低限の Android セキュリティ パッチ レベル (Android 6.0 以上)] ポリシーを適用すると、Android 6.0 以降のデバイスを使用するエンド ユーザーには、"このデバイスは Android の最小セキュリティ パッチ レベルを満たしていません" というメッセージが表示されます。 ユーザーは必要なセキュリティ パッチをインストールする必要があります。 ユーザーは、コンプライアンス メッセージのリンクをクリックして、必要なセキュリティ パッチをインストールする方法と、現在インストールされているセキュリティ パッチに関する[情報](/intune-user-help/you-are-asked-to-turn-on-scan-device-for-security-threats-android)を確認できます。

__iOS ポータル サイト アプリ__

- エンド ユーザーが基幹業務アプリをインストールするときの操作性が向上しています。 アプリのインストールに時間がかかる場合、ユーザーがデバイスを手動で同期させることによって、強制的に同期処理を再開することができます。 エンド ユーザー向けの手順については、「[デバイスを手動で同期する](/intune-user-help/sync-your-device-manually-ios)」を参照してください。

- iOS 向けの Microsoft Intune ポータル サイト アプリが更新され、iOS Version 8.0 以降をサポートするようになりました。 この更新は、デバイスで iOS Version 8.0 以降が実行されている場合にのみ、エンド ユーザーがポータル サイト アプリをインストールして Intune に新しいデバイスを登録できることを意味します。 サポートされていないバージョンの iOS が実行されているデバイスを登録済みの場合、ユーザーはそのデバイス上のポータル サイト アプリを引き続き使用できます。

## <a name="may-2016"></a>2016 年 5 月
これらの機能はすべて、Configuration Manager と Intune のハイブリッド環境でもサポートされます。 新しいハイブリッド機能の詳細については、[ハイブリッド環境の新機能](https://technet.microsoft.com/library/mt718155.aspx)に関するページを参照してください。

### <a name="documentation"></a>ドキュメント
プレビュー バージョンの [docs.microsoft.com](https://docs.microsoft.com/intune) へようこそ。
これはまったく新しい最新コンテンツのプラットフォームです。お客様がより簡単に Intune を理解し、使用できるように設計されています。
すべての新しい機能については、「[Introducing docs.microsoft.com](https://docs.microsoft.com/teamblog/introducing-docs-microsoft-com/)」 (docs.microsoft.com の概要) を参照してください。

### <a name="intune-service-health"></a>Intune のサービス正常性
Intune のサービス正常性に関する情報は他の Microsoft サービスと共に中央の場所に移動されました。 そのため、この情報は [Office 365 管理ポータル](https://portal.office.com/Admin/Default.aspx)の **[サービス正常性]** で参照できるようになりました。
詳細については、[このブログ投稿](https://blogs.technet.microsoft.com/microsoftintune/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/)を参照してください。

### <a name="app-management"></a>アプリ管理
- **MAM SDK: PIN の長さの構成に対応。** デバイス PIN と同様、MAM アプリに使用する PIN の長さを指定できるようになります。 この場合エンド ユーザーは、管理者が設定した新しい制限に従う必要があります。 入力文字数が増える分、PIN 画面の外観が若干調整されます。 詳細については、「[MAM policy settings for Android](/intune-classic/deploy-use/ios-mam-policy-settings)」(Android の MAM ポリシー設定) を参照してください。

- **iOS および Android 用 Skype for Business。** Skype for Business を [MAM の対象にできるようになりました (登録ポリシー不要)](/intune-classic/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune)。 ユーザーがログインすると、MAM ポリシーが適用されます。

- **MAM ポリシーで管理できるようになった新しいアプリ。** Android 用の Microsoft Word、Excel、および PowerPoint の各アプリを、Intune に登録されていないデバイス上の MAM ポリシーに関連付けられるようになりました。 サポートされているアプリの完全なリストについては、[Microsoft Intune アプリケーション パートナー](https://www.microsoft.com/server-cloud/products/microsoft-intune/partners.aspx) ページの Microsoft Intune モバイル アプリケーション ギャラリーを参照してください。


### <a name="company-portal-updates"></a>ポータル サイトの更新

#### <a name="android-company-portal-app"></a>Android 用ポータル サイト アプリ
- **エンドユーザーへのトースト通知**: エンドユーザーがポータル サイトからデバイスの登録または削除を行う際に、Android ポータル サイト アプリからのトースト通知が表示されるようになりました。

- **Android ポータル サイト アプリでのデバイス登録マネージャー アカウントへの変更。** パフォーマンスと拡張性を高めるために、Intune の Android ポータル サイト アプリの [デバイス] ペインには、すべてのデバイス登録マネージャー (DEM) デバイスが表示されなくなります。 アプリを実行しているローカル デバイスのみ、ポータル サイト アプリ経由で登録されている場合にだけ表示されます。 ローカル デバイスに対する操作は DEM で実行できますが、他の登録デバイスのリモート管理は、Intune 管理コンソールから実行する必要があります。

#### <a name="company-portal-website"></a>ポータル Web サイト
- **ポータル Web サイト: デバイス ID バナーによってエンド ユーザーへの情報提供を拡充。** エンド ユーザーは、ポータル Web サイトを使用する際に選択したデバイスをより簡単に特定できるようになりました。 間違ったデバイスを選択した場合は、ホーム ページ バナーの **[ここをタップ]** リンクをタップして正しいデバイスを選択できます。

### <a name="service-deprecation"></a>廃止予定のサービス
- **Intune Viewer アプリ。** 新しい RMS 共有アプリのリリースに伴い、2016 年 8 月以降、次の Intune Viewer アプリを削除する予定です。
    - Intune AV Viewer
    - Intune PDF Viewer
    - Google Play の Android 用 Intune Image Viewer

  Intune Viewer アプリを使用する代わりに、Android 用の新しい Rights Management アプリ (RMS 共有) を使用することをお勧めします。そうすることで、3 つのアプリを個別にではなく、1 つのアプリを展開して、Android デバイス上の企業ファイルを安全に表示することができます。 RMS 共有アプリ (ドキュメントへのリンクを含む) の詳細を確認してください。

- **カスタム グループを対象とした通知規則の廃止。**
Intune の通知規則では、Intune からの電子メール アラートの送信先が定義されます。 現時点では、作成した Intune デバイス グループ内のデバイスのすべてのユーザーに電子メールを送信するように通知規則を構成することができます。 2016 年 6 月 1 日頃以降、ユーザーが作成したグループを対象とすることはできなくなります。

    現在、Microsoft Intune 管理コンソールから作成したグループを通知規則の対象とするには、以下の手順を実行します。

    **[管理者]** ワークスペースで、**[通知規則]** > **[新しい規則の作成]** の順にクリックします。

    通知規則の作成ウィザードの手順 2. で、規則の対象とするデバイス グループを選択します。 この "デバイス グループの選択" の手順は Intune コンソールから削除されます。

    この変更に向けた準備は次のように予定されています。
    - 2016 年 6 月に、新しいテナントでは通知規則の作成ウィザードの手順 2. が表示されなくなります。 既存のテナントは影響を受けません。
    - 2016 年 8 月頃に、既存の一部のテナントではウィザードの "デバイス グループの選択" が表示されなくなります。
    - 2016 年 10 月頃には、すべてのテナントでウィザードの "デバイス グループの選択" が表示されなくなる予定です。


- **iOS ポータル サイト アプリのサポートの変更**。 今後数か月で、iOS 用 Microsoft Intune ポータル サイト アプリが更新され、iOS 8.0 以降を実行しているデバイスのみがサポートされるようになります。 したがって、ユーザーは iOS 8.0 より前のバージョンを実行する新しいデバイスを登録できなくなります。 iOS 8.0 より前のバージョンを実行している登録済みのデバイスは引き続き管理されます。また、期間限定で、ポータル サイト アプリも引き続き使用できます。 ただし、最新バージョンのポータル サイト アプリにアクセスする場合、デバイスは iOS 8.0 以降にある必要があります。 新しい Intune の機能を最大限に活用するには、iOS 8.0 以降に更新するようユーザーに通知することをお勧めします。  


## <a name="april-2016"></a>2016 年 4 月
これらの機能はすべて、Configuration Manager と Intune のハイブリッド環境でもサポートされます。

### <a name="app-management"></a>アプリ管理
- **MAM ユーザー コンプライアンス。**
Azure Active Directory (AAD) テナント内の任意のユーザーについて、アプリケーション管理ポリシーの[状態](/intune-classic/deploy-use/monitor-mobile-app-management-policies-with-Microsoft-Intune)を表示できるようになりました。 以下は、必要な操作の例です。
   - [デバイス]
   - デバイス上のアプリ

   ステータス値:

   **チェックイン**: ポリシーがユーザーに展開されていること、仕事のコンテキストでアプリが使用されていること、正常にポリシーが配信されたことを示します。

    **チェックイン未**: ポリシーはユーザーに展開されましたが、それ以降にアプリが仕事のコンテキストで使用されていないことを示します。


- **Outlook 連絡先の同期 (Android) ができないよう MAM によって制御。**
[モバイル アプリケーション管理](/intune-classic/deploy-use/wipe-managed-company-app-data-with-Microsoft-Intune)の新しい設定を使用できます。ネイティブ アドレス帳に既に保存されている連絡先は削除されます。 この新しい設定は最初に、Android デバイスの Outlook アプリケーションでサポートされます。

### <a name="device-management"></a>デバイス管理
- **会社が所有するデバイスの電話番号の識別。** 会社の所有として分類される電話は今後、完全な電話番号で識別されます (モバイル デバイスのインベントリ レポートを実行するときなど)。 BYOD デバイスの電話番号は引き続き **** でマスクされ、表示されるのは最後の 4 桁のみとなります。


### <a name="company-portal-updates"></a>ポータル サイトの更新
**Android 用ポータル サイト アプリ** まだ Intune にデバイスを登録していないユーザーや適切な証明書がインストールされていないユーザーには、"必要な証明書がデバイスに見つからないため、サインインできません" というメッセージが表示され、Android ポータル サイト アプリにサインインできなくなります。 このメッセージには "この問題を解決する方法" というリンクが表示され、ユーザーはこれをタップして証明書のインストール手順を参照できます。 エンド ユーザーが問題を解決するための手順については、「[デバイスに必要な証明書がない](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_cert_missing)」を参照してください。

**iOS ポータル サイト アプリ** 引き下げて更新する操作に対応しました。ホーム画面上のコンテンツ (アプリやデバイスの一覧、IT 連絡先情報など) をこの操作で最新の情報に更新することができます。 準拠状況やポリシー情報については、引き下げて更新する操作ではチェックされません。これらの情報をチェックするには、現在のデバイスのタイルを選択し、**[同期]** ボタンをタップしてください。

**Windows 10 Mobile と Windows Phone 8.1 ポータル サイト アプリ** エンド ユーザーが基幹業務アプリをインストールするときの操作性が向上しています。 アプリのインストールに時間がかかる場合、ユーザーがデバイスを手動で同期させることによって、強制的に同期処理を再開することができます。 エンド ユーザー向けの手順については、[デバイスを手動で同期させることによってアプリのインストールを高速化する方法](https://technet.microsoft.com/library/mt427782.aspx#BKMK_win10m_wp81_sync_manually)に関するページを参照してください。

**ポータル サイト Web サイト** Windows 10 Mobile ユーザーまたは Windows Phone 8.1 ユーザーが基幹業務アプリをインストールするときに、今後は新しく以下のステータスが表示されます。これらのステータスによって、インストールの状態を従来よりも詳しく知ることができます。

* **[デバイスが同期されるのを待機しています]** – ユーザーが [インストール] をタップした後、デバイスが Intune インフラストラクチャとの同期を試みます。 インストールが完了するためには、同期が完了している必要があります。 "デバイスが同期されるのを待機しています" のメッセージはリンクになっていて、同期処理に時間がかかっていたり、途中で止まったりした場合に、ユーザーがこのリンクをタップすると、デバイスを手動で Intune と同期させるための[手順](https://technet.microsoft.com/library/mt590895.aspx#BKMK_iwp_sync_manually)が表示されます。
* **[ダウンロード中]** – ユーザーのダウンロード要求が処理されています。デバイスは、アプリのダウンロードとインストールを実行しています。

これらのステータスが追加されるまでは、表示されるステータスが "インストール中" のみで、これが何時間も画面に表示された状態に陥ることもあったため、アプリのインストールに時間がかかった場合にユーザーが混乱する原因となっていました。 新しくステータスが追加されることで、ユーザーはサポートに問い合わせなくても、"デバイスが同期されるのを待機しています" のリンクをタップし、画面の指示に従うことで同期処理を強制的に再開できるようになります。

>[!div class="step-by-step"]

>[&larr;**Intune の新機能**](whats-new-in-microsoft-intune.md)    
