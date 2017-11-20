---
title: "初期エディション"
description: 
keywords: 
author: brenduns
ms.author: brenduns
manager: angrobe
ms.date: 11/6/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f7cc595655950ef1bf2586e939b6f02e270e7afc
ms.sourcegitcommit: 5279a0bb8c5aef79aa57aa247ad95888ffe5a12b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/08/2017
---
# <a name="the-early-edition-for-microsoft-intune---november-2017"></a>Microsoft Intune の初期エディション - 2017 年 11 月

**初期エディション**では、Microsoft Intune の今後のリリースで予定されている新機能の一覧を提供しています。 ここに記載されている情報は、限られた範囲について開示されたものであり、また今後変更される可能性があります。 社外ではこの情報を共有しないでください。 ここに挙げられている機能は、発売日に間に合わない可能性があり、その場合は将来のリリースを待たなければなりません。 正式なリリースに向けてパイロット (フライト) テスト中の機能もあります。 ご不明な点や懸念される事項がある場合は、Microsoft 製品グループにお問い合わせください。

このページは定期的に更新されます。 適宜確認してください。

> [!Note]
>Intune に関して以下の機能が現在開発されています。 最新のハイブリッド機能の詳細については、[ハイブリッド環境の新機能に関するページ](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)を参照してください。

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->


## <a name="intune-in-the-azure-portal"></a>Azure Portal での Intune


### <a name="assign-office-365-mobile-apps-to-ios-and-android-devices-using-built-in-app-type----1332318---"></a>組み込み型のアプリを利用し、iOS デバイスまたは Android デバイスに Office 365 モバイル アプリを割り当てる <!-- 1332318 -->
**組み込み**型のアプリであれば、Office 365 アプリを作成し、管理している iOS または Android デバイスに割り当てることが簡単にできます。 これらのアプリには、Word、Excel、PowerPoint、OneDrive などの 0365 アプリがあります。 アプリの種類に特定のアプリを割り当て、アプリ情報構成を編集できます。

### <a name="single-sign-on-support-for-ios----1333645---"></a>iOS のシングル サインオン サポート <!-- 1333645 -->  
iOS ユーザーのためにシングル サインオンを利用できます。 シングル サインオン ペイロードのユーザー資格情報を探すようにプログラミングされている iOS アプリは、このペイロード構成更新で機能します。 UPN と Intune デバイス ID を利用し、プリンシパル名と領域を構成することもできます。

### <a name="ios-11-app-inventory-api-for-mobile-threat-detection----1391759---"></a>モバイルの脅威を検出するための iOS 11 アプリ インベントリ API <!-- 1391759 -->
Intune は個人のデバイスと会社所有のデバイスの両方からアプリ インベントリ情報を収集し、Lookout for Work など、MTD (Mobile Threat Detection/モバイル脅威検出) プロバイダーが取得できるようにします。 iOS 11 以降のデバイスを所有するユーザーからアプリ インベントリを収集できます。

**アプリ インベントリ**  
iOS 11 以降を内蔵した会社所有デバイスと個人所有デバイスの両方からのインベントリが MTD サービス プロバイダーに送信されます。 アプリ インベントリのデータ:

 - アプリ ID
 - アプリ バージョン
 - アプリ バージョン (短い形式)
 - アプリ名
 - アプリ バンドル サイズ
 - アプリの動的サイズ
 - アプリの有効性が確認されているかどうか
 - アプリが管理されているかどうか

### <a name="audit-updates----1412961---"></a>監査更新 <!-- 1412961 -->  
Intune の監査機能により、Intune に関連する変更操作が記録されます。  あらゆる作成操作、更新操作、削除操作、リモート タスク操作が記録され、1 年間保存されます。  Azure Portal では、ワークロード別の監査データを過去 30 日分表示できます。データの絞り込みも可能です。  対応する Graph API により、前年に格納された監査データを取得できます。 

監査は **[モニター]** グループの下にあります。 ワークロード別に **[監査ログ]** メニュー項目があります。   

### <a name="text-protocol-allowed-from-managed-apps----1414050----"></a>管理対象アプリから許可されるテキスト プロトコル <!-- 1414050  -->
Intune App SDK によって管理されるアプリは SMS メッセージを送信できます。

### <a name="remotely-restart-ios-device-supervised-only----1424595---"></a>iOS デバイスをリモート再起動する (監視モードのみ) <!-- 1424595 -->
デバイス アクションを利用し、監視されている iOS 10.3 以降のデバイスを再起動できます。 デバイス再起動アクションの利用方法については、「[Intune でデバイスをリモートで再起動する](device-restart.md)」を参照してください。

> [!Note]  
> このコマンドは、監視されているデバイスと**デバイス ロック** アクセス権を要求します。 デバイスがすぐに再起動します。 パスコードでロックされている iOS デバイスが再起動後に Wi-Fi ネットワークに再び参加することはありません。再起動後、サーバーと通信できないことがあります。

### <a name="remotely-lock-managed-macos-device-with-intune----1437691---"></a>管理されている macOS デバイスを Intune でリモート ロックする <!-- 1437691 -->
紛失した macOS デバイスをロックできます。6 桁の回復用 PIN を設定できます。 ロックされているとき、別のデバイス アクションが送信されるまで、**デバイス概要**ブレードにその PIN が表示されます。

詳細については、「[管理されたデバイスを Intune でリモートからロックする](device-remote-lock.md)」を参照してください。

### <a name="windows-defender-advanced-threat-protection-reporting-frequency-settings------1455974-----"></a>Windows Defender Advanced Threat Protection の報告頻度設定 <!--- 1455974  --->
Windows Defender Advanced Threat Protection (WDATP) サービスを利用するとき、管理者は管理対象デバイスの報告頻度を管理できます。 新しい **[テレメトリの報告頻度を早める]** オプションを利用すると、WDATP はデータを収集し、さらに頻繁にリスクを評価します。 報告の既定値で速度とパフォーマンスが最適化されます。 報告の頻度を増やすことは、リスクの高いデバイスの場合に有益となります。 この設定は **[デバイス構成]** の **[Windows Defender ATP]** プロファイルにあります。

### <a name="assignment-conflict-resolution-has-changed-for-ios-store-apps----1480316---"></a>iOS ストア アプリに関して、割り当て競合の解決が変更されました <!-- 1480316 -->
iOS ストア アプリの入手可能性に関して、変更の影響をエンド ユーザーが受ける可能性があります。 現在のところ、**[Required and Available]\(必須で利用可能\)** と **[適用できません]** で競合する 2 つのグループに割り当てられているアプリは **[Required and Available]\(必須で利用可能\)** に解決されます。 今回の変更で、このような競合が発生していたアプリが **[適用できません]** に解決されるようになります。

この変更は、アプリの意図が異なる複数のグループに 1 つのアプリが割り当てられるときの混乱に対処するものです。

11 月のサービス リリースの前に Information Worker Portal とポータル サイトでアプリを利用できるようにする場合、2 つの選択肢があります。

1. グループの **[適用できません]** 割り当てを削除します。
2. **[Required and Available]\(必須で利用可能\)** が割り当てられているメンバーが含まれない新しいグループを作成し、そのグループに **[適用できません]** を割り当てます。

詳細については、「[How to assign apps to groups with Microsoft Intune](apps-deploy.md)」 (Microsoft Intune を使ってアプリをグループに割り当てる方法) を参照してください。

> [!Note]
> リリース後、Intune クラシック コンソールでは、Mobile Device Management (MDM) アプリ割り当てを表示したり、変更したりできなくなります。 ただし、Azure コンソールまたは Intune Graph API を利用してアプリを割り当てることができます。

### <a name="manage-android-for-work-devices-independently-from-android-devices----1490731---"></a>Android デバイスとは別に Android for Work デバイスを管理する <!-- 1490731 -->
Intune は、Android プラットフォームに依存することなく、Android for Work デバイスの登録を管理できます。 この設定は、**[デバイスの登録]**、**[登録制限]**、**[デバイスの種類の制限]** で管理されます。 (以前の場所は **[デバイス登録]**、**[Android for Work への登録]**、**[Android for Work の登録設定]** でした。)

既定では、Android for Work デバイス設定は Android デバイスの設定と同じになります。 ただし、Android for Work 設定を変更した後は、同じではなくなります。
 
個人の Android for Work 登録をブロックした場合、会社の Android デバイスのみを Android for Work として登録できます。

新しい設定を使用する場合、次の点を考慮してください。

#### <a name="if-you-have-never-previously-onboarded-android-for-work-enrollment"></a>以前に Android for Work 登録をオンボードしたことがない
新しい Android for Work プラットフォームは、既定の [デバイスの種類の制限] でブロックされます。 この機能をオンボードした後は、デバイスを Android for Work に登録できます。 そのためには、既定値を変更するか、新しい [デバイスの種類の制限] を作成して既定の [デバイスの種類の制限] に代えます。

#### <a name="if-you-have-onboarded-android-for-work-enrollment"></a>Android for Work 登録をオンボードした
以前にオンボードしている場合、状況は選んだ設定によって変わります。

| Setting | 既定の [デバイスの種類の制限] の Android for Work の状態 | 注 |
| --- | --- | --- |
| **すべてのデバイスを Android として管理する** | ［ブロック済み］ | すべての Android デバイスを Android for Work なしで登録する必要があります。 |
| **サポートされているデバイスを Android for Work として管理する** | 許可済み | Android for Work 対応のすべての Android デバイスを Android for Work に登録する必要があります。 |
| **これらのグループに所属するユーザーのサポートされているデバイスのみを Android for Work として管理する** | ［ブロック済み］ | 既定値をオーバーライドする別個の [デバイスの種類の制限] ポリシーが作成されました。 このポリシーによって、以前に選択したグループで Android for Work 登録が許可されます。 選択されたグループ内のユーザーには、Android for Work デバイスの登録が引き続き許可されます。 その他すべてのユーザーには、Android for Work の登録が禁止されます。 |

いずれの場合でも、意図した規制が維持されます。 自分の環境で Android for Work のグローバル許可またはグループ別許可を維持するための操作は必要ありません。

以上の変更は 11 月の更新をもってロールアウトが開始されます。ただし、自分のアカウントでは実行に時間がかかることがあります。 変更が自分のアカウントに適用されると、Office 365 ポータルで確認通知が届きます。

### <a name="support-for-multiple-network-device-enrollment-service-ndes-connectors----1528104---"></a>複数のネットワーク デバイス登録サービス (NDES) コネクタのサポート <!-- 1528104 -->
NDES を利用すれば、ドメイン資格情報なしでモバイル デバイスを実行し、Simple Certificate Enrollment Protocol (SCEP) に基づいて証明書を取得できます。 今回の更新で、複数の NDES コネクタがサポートされるようになります。

### <a name="new-scep-profile-details-supported----1559808---"></a>サポートされる新しい SCEP プロファイル詳細 <!-- 1559808 -->
Windows、iOS、macOS、Android プラットフォームで SCEP プロファイルを作成するとき、管理者は追加設定を設定できます。  管理者は、IMEI、シリアル番号、あるいはサブジェクト名の形式の電子メールなど、一般名を設定できます。

### <a name="configure-an-ios-app-pin----1586774---"></a>iOS アプリ PIN を構成する <!-- 1586774 -->
間もなく、対象の iOS アプリで PIN を要求できるようになります。 Azure Portal で PIN 要件と有効期限 (日数) を構成できます。 必須にすると、iOS アプリにアクセスする前に、新しい PIN を設定して使用するようにユーザーが要求されます。 Intune App SDK によるアプリ保護を有効にしている iOS アプリでのみこの機能がサポートされます。

### <a name="retain-data-during-a-factory-reset-----1588489---"></a>工場出荷時の設定へのリセット中にデータを保持する <!-- 1588489 -->
Windows の工場出荷時の設定へのリセットに新しい機能を追加します。 工場出荷時の設定へのリセット中、デバイス登録やプロビジョニングされているその他のデータを保持するかどうかを管理者は指定できるようになります。 
 
工場出荷時の状態にリセットしても、次のデータが維持されます。
- デバイスに関連付けられているユーザー アカウント
- マシンの状態 (ドメイン参加、AADJ)
- MDM 登録
- OEM でインストールされたアプリ (ストア アプリと Win32 アプリ)
- ユーザー プロファイル
- ユーザー プロファイル以外のユーザー データ
- ユーザー自動ログオン
 
次のデータは維持されません。
- ユーザー ファイル
- ユーザーがインストールしたアプリ (ストア アプリと Win32 アプリ)
- 初期値ではないデバイス設定 

### <a name="app-install-status-report-now-a-bar-chart----1249446---"></a>アプリのインストール状態レポートが棒グラフに <!-- 1249446 -->  
**[モバイル アプリ]** ワークロードの **[アプリ]** 一覧から表示できるアプリ別の **[アプリ インストールの状態]** レポートが棒グラフで表示されるようになります。

### <a name="add-find-my-iphone-for-personal-devices---1427287--"></a>個人デバイスの "iPhone を探す" を追加 <!--1427287-->
iOS デバイスのアクティベーション ロックがオンになっているかどうかを表示できるようになります。 この機能は以前、クラシック ポータルの Intune にありました。

### <a name="group-assigned-enrollment-restrictions----747598---"></a>グループ割り当て登録制限 <!-- 747598 -->
Intune 管理者はユーザー グループに対してカスタムの登録制限として [デバイスの種類] と [デバイスの上限数] を作成できるようになります。
 
Intune Azure Portal で、制限タイプごとに最大 25 個のインスタンスを作成できます。作成したインスタンスはユーザー グループに割り当てることができます。 グループに割り当てられた制限は既定の制限をオーバーライドします。
 
制限タイプのすべてのインスタンスは、厳密に順序付けられた一覧で保守管理されます。 この順序により、競合解決の優先度の値が決まります。 複数の制限インスタンスの影響を受けるユーザーは、優先度の値が最も高いインスタンスによって制限されます。 インスタンスの優先度は、一覧内の別の位置にドラッグすることによって変更できます。 
 
Android For Work 登録メニューから登録制限メニューに Android For Work 設定が移行されたとき、この機能が使えるようになります。 この移行には数日かかる場合があります。11 月リリースのその他の部分に関してアカウントがアップグレードされた後に、登録制限のグループ割り当てが有効になる場合があります。

### <a name="windows-10-update-ring-assignments-are-displayed----1621837---"></a>Windows 10 更新プログラム リング割り当てが表示される <!-- 1621837 -->
**トラブルシューティング**時、表示しているユーザーに関して、Windows 10 更新プログラム リング割り当てを表示できるようになります。  



<!-- the following are present prior to 1711 -->

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Azure Active Directory の Web サイトでは、Intune Managed Browser アプリを要求し、Managed Browser (パブリック プレビュー) に対するシングル サインオンをサポートすることができる <!-- 710595 -->   
Azure Active Directory (Azure AD) を使っている場合、モバイル デバイスでの Web サイトへのアクセスを、Intune Managed Browser アプリに制限することができます。 Managed Browser では、Web サイトのデータは安全性を維持され、エンド ユーザーの個人データと分離されます。 さらに、Managed Browser は、Azure AD によって保護されているサイトに対するシングル サインオン機能をサポートします。 Managed Browser にサインインすると、または Intune によって管理されている別のアプリでデバイスの Managed Browser を使うと、ユーザーが資格情報を入力しなくても、Managed Browser は Azure AD によって保護されている会社サイトにアクセスできます。 この機能は、Outlook Web Access (OWA) や SharePoint Online などのサイトだけでなく、Azure App プロキシ経由でアクセスされるイントラネット リソースのような他の企業サイトにも適用されます。

### <a name="troubleshoot-enrollment-issues------746324----"></a>登録に関する問題をトラブルシューティングする <!--- 746324 --->  
トラブルシューティング ワークスペースには、ユーザーの登録に関する問題が表示されます。 問題に関する詳細と推奨される修復手順は、管理者およびヘルプ デスクのオペレーターが問題をトラブルシューティングするのに役立ちます。 登録に関する特定の問題はキャプチャされず、一部のエラーには推奨される修復方法がない場合があります。


















<!-- the following are present prior to 1710 -->



### <a name="support-for-windows-10-edition-upgrade-policy------903672archived-1119689---"></a>Windows 10 エディション アップグレード ポリシーのサポート <!-- 903672(archived), 1119689 -->  
Windows 10 デバイスを Windows 10 Education、Windows 10 Education N、Windows 10 Professional、Windows 10 Professional N、Windows 10 Professional Education、Windows 10 Professional Education N にアップグレードする Windows 10 エディション アップグレード ポリシーを作成できます。Windows 10 エディション アップグレードの詳細については、[Windows 10 エディションのアップグレードを構成する方法](edition-upgrade-configure-windows-10.md)に関するページを参照してください。




<!-- the following are present prior to 1709 -->



### <a name="android-for-work-support-for-lookout----1087312---"></a>Lookout の Android for Work サポート <!-- 1087312 -->   
Lookout を備えた Intune コネクタでは、Lookout for Work アプリの使用時、Android for Work デバイスをサポートします。 コンテナーの内外に Lookout アプリを展開できるようになる予定です。

### <a name="intune-app-protection-and-citrix-mdx-development-tools----709185---"></a>Intune App Protection と Citrix MDX 開発ツール<!-- 709185 -->
Citrix XenMobile MDX と Microsoft Intune を組み合わせ、デバイスとアプリを管理することができます。 これにより、Citrix の mVPN テクノロジを使用し、Intune アプリの保護ポリシーでアプリを管理できるようになります。

Citrix の MDX mVPN テクノロジとの統合を可能にする iOS および Android 用の Intune アプリ ラッピング ツールと Intune アプリ SDK を含むコード リポジトリを見つけることができるはずです。


### <a name="on-premises-exchange-connector-high-availability-support-----676614---"></a>オンプレミスの Exchange Connector の高可用性のサポート  <!-- 676614 -->   
オンプレミスの Exchange Connector に複数のクライアント アクセス サーバー (CAS) ロールを持たせることができます。 たとえば、メインの CAS に障害が発生した場合、他の CAS にフォールバックするクエリを Exchange Connector が受信するようにできます。 この機能により、サービスが中断されないことが保証されます。

### <a name="system-center-operations-manager-management-pack-for-exchange-connector----885457---"></a>Exchange Connector 用の System Center Operations Manager 管理パック <!-- 885457 -->   
Exchange Connector 用の System Center Operations Manager 管理パックが Exchange Connector のログ解析に利用できるようになります。 問題のトラブルシューティングを行う必要がある場合、この管理パックによって別の方法で Intune を監視できます。





## <a name="intune-apps"></a>Intune アプリ

### <a name="helping-your-users-help-themselves-with-the-company-portal-app-for-android----1573324-1573150-1558616-1564878---"></a>Android 向けポータル サイト アプリに関してユーザーの自己解決をサポートする <!---1573324, 1573150, 1558616, 1564878--->
Android 向けのポータル サイト アプリでは、エンド ユーザー向けの指示が追加されます。その指示は新しいユース ケースの理解に役立ち、新しい使用事例を自分で解決できる場合もあります。 

- 暗号化のコンプライアンス ポリシーが展開されている説明する新しいメッセージが表示されますが、[Google の推奨ガイドライン](https://developer.android.com/reference/android/app/admin/DevicePolicyManager.html#setStorageEncryption(android.content.ComponentName, boolean) に基づき、[デバイス メーカーはデバイスを暗号化しません](/intune-user-help/your-device-appears-encrypted-but-cp-says-otherwise-android)。
- 追加が許されているデバイスの最大数に到達した場合、デバイスを削除するように、エンド ユーザーは (Azure Active Directory ポータル)[https://account.activedirectory.windowsazure.com/r/#/profile] に誘導されます。 
- [Samsung KNOX デバイスのアクティベーション エラーを解消する](https://go.microsoft.com/fwlink/?linkid=859718)か、[節電モードをオフにする](/intune-user-help/power-saving-mode-android)ための手順がエンド ユーザーに表示されます。 いずれの解決策でも問題が解消されない場合、[Microsoft にログを送信する](/intune-user-help/send-logs-to-microsoft-ios)方法を説明します。 


### <a name="new-resolve-action-available-for-android-devices----1583480---"></a>Android デバイスで利用できる新しい '解決' アクション <!---1583480--->
Android のポータル サイト アプリの _[デバイス設定の更新]_ ページに '解決' アクションが導入されます。 このオプションを選択すると、デバイスの非準拠の原因になっている設定にエンド ユーザーが直接誘導されます。 Android 向けのポータル サイト アプリでは現在のところ、[デバイス パスコード](/intune-user-help/set-your-pin-or-password-android)、[デバイスの暗号化](/intune-user-help/encrypt-your-device-android)、[USB デバッグ](/intune-user-help/you-need-to-turn-off-usb-debugging-android)、[不明なソース](/intune-user-help/you-need-to-turn-off-unknown-sources-android)設定に対してこのアクションがサポートされています。 




<!-- the following are present prior to 1711 -->


### <a name="redirecting-macos-users-to-our-new-company-portal-app---1380728--"></a>新しいポータル サイト アプリへの macOS ユーザーのリダイレクト<!--1380728-->   
エンド ユーザーは、ポータル サイトの Web サイトにログインして macOS デバイスを登録するとき、プロセスを完了するために macOS 用の新しいポータル サイト アプリをダウンロードするように指示されます。 これは、OS X El Capitan 10.11 以降を使っている macOS デバイスの場合に発生します。 


<!-- the following are present prior to 1710 -->



### <a name="apps-that-are-available-with-or-without-enrollment-can-now-be-installed-without-being-prompted-for-enrollment----1334712---"></a>登録の有無にかかわらず利用可能なアプリについて、登録を求められずにインストールできるようになりました。 <!-- 1334712 -->
Android ポータル サイト アプリでの登録の有無にかかわらず利用可能な業務用アプリについて、登録を求められずにインストールできます。


<!-- the following are present prior to 1709 -->

### <a name="intune-managed-browser-support-for-ios-and-android----1374196---"></a>iOS および Android <!-- 1374196 --> 用の Intune Managed Browser のサポート
2017 年 10 月の時点で、Android アプリで使用する Intune Managed Browser アプリは、Android 4.4 以降を実行しているデバイスのみをサポートします。 iOS の Intune Managed Browser アプリは、iOS 9.0 以降を実行しているデバイスのみをサポートします。 以前のバージョンの Android および iOS は、Managed Browser の使用を続けることができますが、新しいバージョンのアプリをインストールすることはできません。また、アプリのすべての機能にアクセスできるとは限りません。 サポートされるオペレーティング システム バージョンにこれらのデバイスを更新することをお勧めします。


### <a name="improved-error-message-for-when-a-user-reaches-the-maximum-number-of-devices-allowed-to-enroll----1270370---"></a>ユーザーが登録できるデバイスの最大数に達したときのエラー メッセージの向上<!-- 1270370 -->
エンドユーザーに一般的なエラー メッセージでなく、「IT 管理者が許可している数よりも多くのデバイスが登録されています。登録したデバイスを削除するか、IT 管理者に支援を求めてください。」という分かりやすい、実践的なエラー メッセージが表示されるようになりました。




## <a name="notices"></a>通知

現在のところ、アクティブな通知はありません。




### <a name="see-also"></a>関連項目
最近の開発状況について詳しくは、「[Microsoft Intune の新機能](whats-new.md)」をご覧ください。
