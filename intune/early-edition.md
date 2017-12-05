---
title: "初期エディション"
description: 
keywords: 
author: ErikjeMS
ms.author: erikje
manager: angrobe
ms.date: 11/29/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 1ea734e83cfab3fff22c775764ac9814012d52b6
ms.sourcegitcommit: 70dc0aaad51b447e173b663d1092d993dc81ffdd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="the-early-edition-for-microsoft-intune---december-2017"></a>Microsoft Intune の初期エディション - 2017 年 12 月

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

### <a name="app-protection-policies-----679615---"></a>アプリ保護ポリシー  <!-- 679615 -->
Intune App Protection ポリシーは、既定のグローバル ポリシーを作成し、テナント全体のすべてのユーザーに保護をすばやく適用する機能を提供します。

### <a name="revoking-ios-volume-purchase-program-apps-----820863---"></a>iOS Volume-Purchase Program アプリの取り消し  <!-- 820863 -->
1 つ以上の iOS Volume-Purchase Program (VPP) アプリがインストールされた特定のデバイスでは、そのデバイスで関連付けられているデバイス ベース アプリのライセンスを取り消すことができます。 アプリのライセンスを取り消しても、関連する VPP アプリがデバイスからアンインストールされるわけではありません。 VPP アプリをアンインストールするには、割り当てアクションを **[アンインストール]** に変更する必要があります。 詳細については、「[Volume Purchase Program で購入した iOS アプリを Microsoft Intune で管理する方法](vpp-apps-ios.md)」をご覧ください。

### <a name="revoke-licenses-for-an-ios-volume-purchasing-program-token----820870---"></a>iOS Volume Purchasing Program トークンのライセンスの取り消し <!-- 820870 -->
特定の VPP トークンのすべての iOS Volume Purchasing Program (VPP) アプリのライセンスを取り消すことができます。

### <a name="delete-an-ios--volume-purchasing-program-token----820879---"></a>iOS Volume Purchasing Program トークンのライセンスの削除 <!-- 820879 -->
コンソールを使用して、iOS Volume Purchasing Program (VPP) トークンを削除できます。 VPP トークンのインスタンスが重複している場合に、これが必要になることがあります。

### <a name="network-access-control-nac-device-check-in-reporting-----1232250---"></a>ネットワーク アクセス制御 (NAC) デバイス チェックイン レポート <!-- 1232250 -->
この変更の前には、IT 管理者は NAC で管理されているデバイスが NAC ソリューションと通信しているかどうかを Intune 側から判断することができませんでした。 NAC で管理されているデバイスが NAC ソリューションと通信していない場合、そのデバイスは NAC ソリューションに非準拠のデバイスとみなされます。そのため、NAC で管理されているデバイスは NAC ソリューション自体にブロックされ、その後デバイスの準拠状態に依存する条件付きアクセス ポリシーによってブロックされます。

今回の変更により、IT 管理者はどの NAC で管理されているデバイスが NAC ソリューションと正常に通信したかを確認できるようになります。 この新機能は、Intune 内のデバイス準拠ワークロードに配置された 2 つの新しい監視機能で構成され、次のように統計が表示されます。
- **過去 1 時間の NAC 呼び出しの平均**
- **最後の NAC 受信要求 (日付/時刻)**

### <a name="new-ios-device-action------1244701---"></a>新しい iOS デバイス アクション <!-- 1244701 -->
iOS 10.3 監視下のデバイスをシャット ダウンできます。 このアクションでは、エンド ユーザーへの警告なしにデバイスが即時シャットダウンされます。 **シャット ダウン (監視モードのみ)** アクションは、**デバイス** ワークロードでデバイスを選択した場合に、デバイス プロパティに表示されます。

### <a name="palo-alto-vpn-now-supported----1333680-eeready---"></a>Palo Alto VPN がサポートされるようになりました <!-- 1333680 eeready -->
ベースの VPN の構成時、**接続の種類**リストに Palo Alto VPN が表示されます。

### <a name="multiple-connector-support-for-scep-and-pfx-certificate-handling----1361755-eeready---"></a>SCEP の複数コネクタ サポートと PFX 証明書処理 <!-- 1361755 eeready -->
オンプレミス NDES コネクタを使用してデバイスに証明書を配信するお客様は、1 つのテナントに複数のコネクタを構成できます。

この新しい機能では、次のシナリオがサポートされています。

- **高可用性**

    各 NDES コネクタは、Intune から証明書の要求を取得します。  1 つの NDES コネクタがオフラインになっても、その他のコネクタは要求の処理を続行できます。

### <a name="new-automatic-redeployment-setting----1469168---"></a>新しい自動再配置設定 <!-- 1469168 -->
この設定では、管理権限を持つユーザーが、デバイス ロック画面で **CTRL + Win + R** を使用してすべてのユーザー データとユーザー設定を削除できます。 このデバイスは自動的に再構成され、管理対象に再登録されます。

この設定には、[Windows 10] -> [デバイスの制限] -> [全般] -> [Automatic redeployment]\(自動再デプロイ\) でアクセスできます。

### <a name="install-office-apps-on-macos-devices----1494311---"></a>macOS デバイスでの Office アプリのインストール <!-- 1494311 -->
macOS デバイスで Office アプリをインストールできるようになります。 この新しい種類のアプリでは、Word、Excel、PowerPoint、Outlook、OneNote をインストールできます。 これらのアプリには Microsoft AutoUpdater (MAU) も付属しており、アプリを安全かつ最新に保つことができます。

### <a name="surface-hub-resource-account-supported----1566442-eeready---"></a>サポートされる Surface Hub リソース アカウント <!-- 1566442 eeready -->
管理者が Surface Hub に関連付けられたリソース アカウントを定義、更新できる新しいデバイス アクションが追加されます。

このリソース アカウントは、Skype または Exchange でミーティングに参加できるように認証する場合に Surface Hub で使用されます。 Surface Hub がミーティングで会議室として表示されるように、一意のリソース アカウントを作成できます。 たとえば、リソース アカウントは*会議室 B41/6233* と表示されます。 Surface Hub のリソース アカウント (デバイス アカウントと呼ばれる) は通常、会議室の場所や、他のリソース アカウントのパラメーターをいつ変更するかを構成するのに必要となります。

管理者はデバイスでリソース アカウントを更新する場合、デバイスに関連付けられた現在の Active Directory または Azure Active Directory 資格情報を指定する必要があります。 デバイスでパスワードのローテーションがオンに設定されている場合には、管理者は Azure Active Directory に移動してパスワードを検索する必要があります。

> [!NOTE]
> すべてのフィールドがまとめて送信され、以前に構成されたすべてのフィールドを上書きします。 また、空のフィールドも既存のフィールドを上書きします。

管理者が行える構成は次のとおりです。

- **リソース アカウント**  

   - **Active Directory ユーザー**   
   Domainname\username、またはユーザー プリンシパル名: user@domainname.com
   - **パスワード**


- **オプションのリソース アカウント パラメーター** (指定されたリソース アカウントを使用して設定する必要があります)
   - **パスワードのローテーション期間**   
     アカウントのパスワードは、セキュリティ上の理由から、毎週 Surface Hub によって自動的に更新されます。 これを有効にした後にパラメーターを構成するには、最初に Azure Active Directory のアカウントのパスワードをリセットする必要があります。

   - **SIP (セッション開始プロトコル) アドレス**    
     自動検出が失敗した場合にのみ使用されます。

   - **電子メール**    
     デバイス アカウントまたはリソース アカウントの電子メール アドレス。

   - **Exchange サーバー**    
     自動検出が失敗した場合のみ必要です。

   - **予定表の同期**    
     予定表の同期と他の Exchange サーバー サービスが有効かどうかを指定します。 たとえば、ミーティングの同期などです。

### <a name="intune-now-provides-the-account-move-operation-----1573558-1579830---"></a>Intune で、アカウントの移動操作が使用できるようになりました。<!-- 1573558, 1579830 -->
**アカウントの移動**を行うと、Azure スケール ユニット (ASU) 間でテナントが移動します。 お客様が Intune サポート チームに連絡してアカウントの移動をリクエストする、お客様が開始するシナリオと、Microsoft でバックエンドでのサービスの調整が必要な、Microsoft 主導のシナリオの両方で**アカウントの移動**を使用できます。 **アカウントの移動**中は、テナントは読み取り専用モード (ROM) になります。 ROM 期間中は、デバイスの登録や名前変更、コンプライアンス状態の更新などのサービス操作が失敗します。

### <a name="new-windows-defender-security-center-wdsc-device-configuration-profile-settings----1335507---"></a>新しい Windows Defender セキュリティ センター (WDSC) デバイス構成プロファイルの設定 <!-- 1335507 -->
Intune の **Windows Defender セキュリティ センター**という名前の Endpoint Protection に、デバイス構成プロファイル設定の新しいセクションが追加されます。 IT 管理者は、Windows Defender セキュリティ センター アプリで、エンドユーザーがどの機能にアクセス可能かを構成できます。 IT 管理者が Windows Defender セキュリティ センター アプリで、ある機能を非表示にすると、ユーザーのデバイスで、その機能に関連するすべての通知が非表示になります。

管理者が Windows Defender セキュリティ センター デバイス構成プロファイル設定で非表示にできる機能は、以下のとおりです。
- ウイルスと脅威の防止
- デバイスのパフォーマンスと正常性
- ファイアウォールとネットワーク保護
- アプリとブラウザー コントロール
- ファミリー オプション

IT 管理者は、ユーザーが受け取る通知をカスタマイズすることもできます。 たとえば、ユーザーが WDSC に表示される機能で生成されたすべての通知を受け取るか、または重要な通知のみを受け取るかを構成できます。 重要度の低い通知には、Windows Defender Antivirus のアクティビティに関する定期的な概要や、スキャン完了時の通知があります。 その他のすべての通知は重要とみなされます。 さらに、通知の内容自体をカスタマイズすることもできます。たとえば、IT 担当の連絡先情報を、ユーザーのデバイスに表示される通知に組み込むなどです。




<!-- the following are present prior to 1712 -->
### <a name="assign-office-365-mobile-apps-to-ios-and-android-devices-using-built-in-app-type----1332318---"></a>組み込み型のアプリを利用し、iOS デバイスまたは Android デバイスに Office 365 モバイル アプリを割り当てる <!-- 1332318 -->
**組み込み**型のアプリであれば、Office 365 アプリを作成し、管理している iOS または Android デバイスに割り当てることが簡単にできます。 これらのアプリには、Word、Excel、PowerPoint、OneDrive などの 0365 アプリがあります。 アプリの種類に特定のアプリを割り当て、アプリ情報構成を編集できます。

### <a name="single-sign-on-support-for-ios----1333645---"></a>iOS のシングル サインオン サポート <!-- 1333645 -->  
iOS ユーザーのためにシングル サインオンを利用できます。 シングル サインオン ペイロードのユーザー資格情報を探すようにプログラミングされている iOS アプリは、このペイロード構成更新で機能します。 UPN と Intune デバイス ID を利用し、プリンシパル名と領域を構成することもできます。

### <a name="text-protocol-allowed-from-managed-apps----1414050----"></a>管理対象アプリから許可されるテキスト プロトコル <!-- 1414050  -->
Intune App SDK によって管理されるアプリは SMS メッセージを送信できます。

### <a name="remotely-lock-managed-macos-device-with-intune----1437691---"></a>管理されている macOS デバイスを Intune でリモート ロックする <!-- 1437691 -->
紛失した macOS デバイスをロックできます。6 桁の回復用 PIN を設定できます。 ロックされているとき、別のデバイス アクションが送信されるまで、**デバイス概要**ブレードにその PIN が表示されます。

詳細については、「[管理されたデバイスを Intune でリモートからロックする](device-remote-lock.md)」を参照してください。


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
Intune は、Android プラットフォームに依存することなく、Android for Work デバイスの登録を管理できます。 この設定は、**[デバイスの登録]**、 > **[登録制限]**、 > **[デバイスの種類の制限]** で管理されます。 (以前の場所は **[デバイス登録]**、 > **[Android for Work への登録]**、 > **[Android for Work の登録設定]** でした。)

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


### <a name="configure-an-ios-app-pin----1586774---"></a>iOS アプリ PIN を構成する <!-- 1586774 -->
間もなく、対象の iOS アプリで PIN を要求できるようになります。 Azure Portal で PIN 要件と有効期限 (日数) を構成できます。 必須にすると、iOS アプリにアクセスする前に、新しい PIN を設定して使用するようにユーザーが要求されます。 Intune App SDK によるアプリ保護を有効にしている iOS アプリでのみこの機能がサポートされます。

### <a name="add-find-my-iphone-for-personal-devices---1427287--"></a>個人デバイスの "iPhone を探す" を追加 <!--1427287-->
iOS デバイスのアクティベーション ロックがオンになっているかどうかを表示できるようになります。 この機能は以前、クラシック ポータルの Intune にありました。

<!-- the following are present prior to 1711 -->

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Azure Active Directory の Web サイトでは、Intune Managed Browser アプリを要求し、Managed Browser (パブリック プレビュー) に対するシングル サインオンをサポートすることができる <!-- 710595 -->   
Azure Active Directory (Azure AD) を使っている場合、モバイル デバイスでの Web サイトへのアクセスを、Intune Managed Browser アプリに制限することができます。 Managed Browser では、Web サイトのデータは安全性を維持され、エンド ユーザーの個人データと分離されます。 さらに、Managed Browser は、Azure AD によって保護されているサイトに対するシングル サインオン機能をサポートします。 Managed Browser にサインインすると、または Intune によって管理されている別のアプリでデバイスの Managed Browser を使うと、ユーザーが資格情報を入力しなくても、Managed Browser は Azure AD によって保護されている会社サイトにアクセスできます。 この機能は、Outlook Web Access (OWA) や SharePoint Online などのサイトだけでなく、Azure App プロキシ経由でアクセスされるイントラネット リソースのような他の企業サイトにも適用されます。


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
