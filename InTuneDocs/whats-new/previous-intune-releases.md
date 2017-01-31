---
title: "以前のリリース | Microsoft Docs"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 01/11/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 45dad14a-d412-488d-bb1e-ad990ea503df
ROBOTS: noindex,nofollow
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 0e4d08c4fd66bb1ae3fe683db503915725bc3134
ms.openlocfilehash: 5f09c46e7dcd5aabc603838ce60a1e8e7fed694e


---

# <a name="previous-intune-releases"></a>以前の Intune のリリース

このページは、「[Microsoft Intune の新機能](whats-new-in-microsoft-intune.md)」で発表された内容の一覧です。

[!INCLUDE[wit_nextref](../includes/whats-new-last-six-months.md)]

## <a name="june-2016"></a>2016 年 6 月
### <a name="intune-service-health"></a>Intune のサービス正常性
Intune のサービス正常性に関する情報は他の Microsoft サービスと共に中央の場所に移動されました。 そのため、この情報は Office 365 管理ポータルの [サービス正常性] で参照できるようになりました。 詳細については、[このブログ投稿](https://blogs.technet.microsoft.com/enterprisemobility/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/)を参照してください。

### <a name="app-management"></a>アプリ管理
- **Windows 10 の強化されたエンタープライズ データ ポリシー構成のエクスペリエンス。** Windows 10 のエンタープライズ データ保護ポリシー構成のエクスペリエンスが、アプリ規則の作成、ネットワーク境界の定義の指定、その他のエンタープライズ データ保護の設定などにおいて強化されました。 詳細については、「[Create an enterprise data protection (EDP) policy using Microsoft Intune](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-intune)」(Microsoft Intune を使用してエンタープライズ データ保護 (EDP) ポリシーを作成する) を参照してください。


### <a name="device-management"></a>デバイス管理
- **望ましくない可能性があるアプリから保護するための Windows Defender ポリシー設定。** **望ましくない可能性があるアプリケーションの検出**という名前の新しい Windows Defender 設定が、Windows 10 Desktop と Mobile の全般構成ポリシーに追加されました。 この設定を使えば、Windows Defender によって望ましくない可能性があると判断されたソフトウェアの実行から、登録済みの Windows デスクトップ コンピューターを保護することができます。 このようなアプリケーションの実行からコンピューターを保護したり、望ましくない可能性があるアプリケーションがいつインストールされたのかを監査モードでレポートしたりできます。 詳細については、「[Microsoft Intune の Windows 10 ポリシー設定](https://docs.microsoft.com/en-us/intune/deploy-use/windows-10-policy-settings-in-microsoft-intune)」を参照してください。
<!---TFS 1244478--->

### <a name="conditional-access"></a>条件付きアクセス
- **Intune の Cisco ISE ネットワーク アクセス制御ポリシー。**  Cisco Identity Service Engine (ISE) 2.1 と Microsoft Intune の両方を使用する場合、ISE でネットワーク アクセス制御ポリシーを設定できます。

    このポリシーを使用すると、WiFi または VPN でネットワークに接続するデバイスは、アクセスが許可される前に、次の条件を満たすことが必要になります。

    * Intune で管理されていること
    * 展開されているすべての Intune コンプライアンス ポリシーに準拠していること

 準拠していないデバイスのエンド ユーザーは、アクセスを取得するために、デバイスを登録することと、コンプライアンス関連の問題を修正することを求められます。
- **ブラウザーの条件付きアクセス。** [Exchange Online](/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune) と [SharePoint Online](/intune/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune) 用の条件付きアクセス ポリシーを設定すると、管理下にあって、かつ条件を満たした iOS デバイスと Android デバイス上のサポートされる Web ブラウザーに、Exchange Online と SharePoint Online へのアクセスを限定することができます。 Outlook Web Access (OWA) や SharePoint サイトにエンド ユーザーが iOS または Android デバイスでサインインしようとすると、そのデバイスを Intune に登録するよう求めるメッセージが表示されます。また条件を満たしていないことが問題になっている場合は、その問題を解消してから、サインインを試行するように求められます。
<!---TFS 1175844--->

- **Dynamics CRM Online では、条件付きアクセスをサポートしています。** [Dynamics CRM Online](/intune/deploy-use/restrict-access-to-dynamics-crm-online-with-microsoft-intune) 用の条件付きアクセス ポリシーを設定すると、管理下にあって、かつ条件を満たした iOS デバイスと Android デバイスに、Dynamics CRM Online へのアクセスを限定することができます。 Dynamics CRM モバイル アプリにエンド ユーザーが iOS または Android でサインインしようとすると、Intune に登録するよう求めるメッセージが表示されます。また条件を満たしていないことが問題になっている場合は、その問題を修正してから、サインインを試行するように求められます。
<!---TFS1295358--->

### <a name="intune-company-portal-updates"></a>Intune 会社のポータルの更新

__Android 用ポータル サイト アプリ__

- IT 管理者が新しい [不明なソースからのアプリのインストールをデバイスが禁止することを必須にする (Android 4.0 以上)] ポリシーを適用すると、Android 4.0 以降のデバイスを使用するエンド ユーザーには、"不明なソースからのインストールを無効にする必要があります" というメッセージが表示されます。 ユーザーは、**[設定]** > **[セキュリティ]** を選択し、**[不明なソース]** を無効にする必要があります。 ユーザーは、コンプライアンス メッセージのリンクをクリックして、メッセージと、設定を無効にする必要がある理由に関する詳細[情報](/Intune/EndUser/you-are-asked-to-turn-off-unknown-sources-android)を確認できます。

- IT 管理者が新しい [セキュリティ上の脅威に対してデバイスがアプリのスキャンを有効にすることを必須にする (Android 4.0 以上)] ポリシーを適用すると、Android 4.0 以降のデバイスを使用するエンド ユーザーには、"端末をスキャンしてセキュリティ上の脅威を確認" というメッセージが表示されます。 ユーザーは、**[設定]** > **[Google]** > **[セキュリティ]** を選択し、**[端末をスキャンしてセキュリティ上の脅威を確認]** をオンにする必要があります。 ユーザーは、コンプライアンス メッセージのリンクをクリックして、メッセージと、設定を有効にする必要がある理由に関する詳細[情報](/Intune/EndUser/you-are-asked-to-turn-on-scan-device-for-security-threats-android)を確認できます。

- IT 管理者が新しい [USB デバッグの無効化を必須にする (Android 4.2 以上)] ポリシーを適用すると、Android 4.2 以降のデバイスを使用するエンド ユーザーには、"USB デバッグを無効にする必要があります" というメッセージが表示されます。 ユーザーは、**[設定]** > **[開発者オプション]** を選択し、**[USB デバッグ]** を無効にする必要があります。 ユーザーは、コンプライアンス メッセージのリンクをクリックして、メッセージと、設定を無効にする必要がある理由に関する詳細[情報](/Intune/EndUser/you-are-asked-to-turn-off-usb-debugging-android)を確認できます。

- IT 管理者が新しい [最低限の Android セキュリティ パッチ レベル (Android 6.0 以上)] ポリシーを適用すると、Android 6.0 以降のデバイスを使用するエンド ユーザーには、"このデバイスは Android の最小セキュリティ パッチ レベルを満たしていません" というメッセージが表示されます。 ユーザーは必要なセキュリティ パッチをインストールする必要があります。 ユーザーは、コンプライアンス メッセージのリンクをクリックして、必要なセキュリティ パッチをインストールする方法と、現在インストールされているセキュリティ パッチに関する[情報](/Intune/EndUser/you-are-asked-to-turn-on-scan-device-for-security-threats-android)を確認できます。

__iOS ポータル サイト アプリ__

- エンド ユーザーが基幹業務アプリをインストールするときの操作性が向上しています。 アプリのインストールに時間がかかる場合、ユーザーがデバイスを手動で同期させることによって、強制的に同期処理を再開することができます。 エンド ユーザー向けの手順については、「[デバイスを手動で同期する](/Intune/EndUser/sync-your-device-manually-ios)」を参照してください。

- iOS 向けの Microsoft Intune ポータル サイト アプリが更新され、iOS Version 8.0 以降をサポートするようになりました。 この更新は、デバイスで iOS Version 8.0 以降が実行されている場合にのみ、エンド ユーザーがポータル サイト アプリをインストールして Intune に新しいデバイスを登録できることを意味します。 サポートされていないバージョンの iOS が実行されているデバイスを登録済みの場合、ユーザーはそのデバイス上のポータル サイト アプリを引き続き使用できます。

## <a name="may-2016"></a>2016 年 5 月
これらの機能はすべて、Configuration Manager と Intune のハイブリッド環境でもサポートされます。 新しいハイブリッド機能の詳細については、[ハイブリッド環境の新機能](https://technet.microsoft.com/en-us/library/mt718155.aspx)に関するページを参照してください。

### <a name="documentation"></a>ドキュメント
プレビュー バージョンの [docs.microsoft.com](https://docs.microsoft.com/en-us/intune) へようこそ。
これはまったく新しい最新コンテンツのプラットフォームです。お客様がより簡単に Intune を理解し、使用できるように設計されています。
すべての新しい機能については、「[Introducing docs.microsoft.com](https://docs.microsoft.com/teamblog/introducing-docs-microsoft-com/)」 (docs.microsoft.com の概要) を参照してください。

### <a name="intune-service-health"></a>Intune のサービス正常性
Intune のサービス正常性に関する情報は他の Microsoft サービスと共に中央の場所に移動されました。 そのため、この情報は [Office 365 管理ポータル](https://portal.office.com/Admin/Default.aspx)の **[サービス正常性]** で参照できるようになりました。
詳細については、[このブログ投稿](https://blogs.technet.microsoft.com/microsoftintune/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/)を参照してください。

### <a name="app-management"></a>アプリ管理
- **MAM SDK: PIN の長さの構成に対応。** デバイス PIN と同様、MAM アプリに使用する PIN の長さを指定できるようになります。 この場合エンド ユーザーは、管理者が設定した新しい制限に従う必要があります。 入力文字数が増える分、PIN 画面の外観が若干調整されます。 詳細については、「[MAM policy settings for Android](/intune/deploy-use/android-mam-policy-settings)」 (Android 用 MAM ポリシー設定) および「[MAM policy settings for iOS](/intune/deploy-use/ios-mam-policy-settings)」 (iOS 用 MAM ポリシー設定) を参照してください。

- **iOS および Android 用 Skype for Business。** Skype for Business を [MAM の対象にできるようになりました (登録ポリシー不要)](/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune)。 ユーザーがログインすると、MAM ポリシーが適用されます。

- **MAM ポリシーで管理できるようになった新しいアプリ。** Android 用の Microsoft Word、Excel、および PowerPoint の各アプリを、Intune に登録されていないデバイス上の MAM ポリシーに関連付けられるようになりました。 サポートされているアプリの完全なリストについては、[Microsoft Intune アプリケーション パートナー](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx) ページの Microsoft Intune モバイル アプリケーション ギャラリーを参照してください。


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
Azure Active Directory (AAD) テナント内の任意のユーザーについて、アプリケーション管理ポリシーの[状態](/intune/deploy-use/monitor-mobile-app-management-policies-with-Microsoft-Intune)を表示できるようになりました。 以下は、必要な操作の例です。
   - [デバイス]
   - デバイス上のアプリ

   ステータス値:

   **チェックイン**: ポリシーがユーザーに展開されていること、仕事のコンテキストでアプリが使用されていること、正常にポリシーが配信されたことを示します。

    **チェックイン未**: ポリシーはユーザーに展開されましたが、それ以降にアプリが仕事のコンテキストで使用されていないことを示します。


- **Outlook 連絡先の同期 (Android) ができないよう MAM によって制御。**
[モバイル アプリケーションの管理](/intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune)に、デバイスを登録せずに行える新しい設定が追加されました。 この設定を使用して、Android デバイス上のネイティブのアドレス帳と連絡先との同期をアプリケーションに禁止することができます。 この設定を有効にすると、対象アプリケーションはネイティブのアドレス帳に連絡先を保存できなくなります。 この設定を無効にすると、対象アプリケーションはネイティブのアドレス帳に連絡先を保存できるようになります。 [デバイスまたはアプリをリモートからワイプ](/intune/deploy-use/wipe-managed-company-app-data-with-Microsoft-Intune)すると、ネイティブのアドレス帳に保存されているすべての連絡先が削除されます。 この新しい設定は最初に、Android デバイスの Outlook アプリケーションでサポートされます。

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



<!--HONumber=Jan17_HO5-->


