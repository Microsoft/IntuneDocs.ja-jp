---
title: "初期エディション"
description: 
keywords: 
author: ErikjeMS
ms.author: erikje
manager: angrobe
ms.date: 01/02/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: ac9cb0ad7d1b5e2c29e80f16c172f41c08d3a15d
ms.sourcegitcommit: 5fd17a57989c6da3d325ed2e0018ce16fe20bb79
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/04/2018
---
# <a name="the-early-edition-for-microsoft-intune---january-2018"></a>Microsoft Intune の初期エディション - 2018 年 1 月

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

### <a name="easier-resolution-of-compliance-issues-for-the-company-portal-app-for-windows-10---676546---"></a>Windows 10 でポータル サイト アプリのコンプライアンスの問題解決が簡単に<!--676546 -->

Windows デバイスを持つエンド ユーザーは、ポータル サイト アプリのコンプライアンス非対応の理由をタップできます。 可能であれば、問題を解決するのに適切な、設定アプリ内の場所がエンド ユーザーに直接表示されます。 

### <a name="new-option-for-user-authentication-for-apple-bulk-enrollment----747625---"></a>Apple の一括登録に対するユーザー認証の新しいオプション<!-- 747625 -->
Intune では、次の登録方法について、ポータル サイト アプリを使用してデバイスを認証できます。

- Apple Device Enrollment Program
- Apple School Manager
- Apple Configurator Enrollment

このポータル サイト オプションを使用すると、これらの登録方法をブロックすることなく、Azure Active Directory の多要素認証を強制できます。

このポータル サイト オプションを使用する場合、iOS 設定アシスタントでの、ユーザー アフィニティ登録用のユーザー認証がスキップされます。 つまり、このデバイスは、最初はユーザーのいないデバイスとして登録されるため、ユーザー グループの構成やポリシーは受信しません。 デバイス グループの構成とポリシーのみを受信します。 ただし、ポータル サイト アプリは自動的にデバイスにインストールされます。 ポータル サイト アプリを最初に起動してサインインするユーザーは、Intune でそのデバイスと関連付けられます。 この時点で、ユーザー グループの構成とポリシーが、このユーザーに送信されます。 ユーザーの関連付けを変更するには、再登録が必要です。

### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685---"></a>複数の Apple DEP および Apple School Manager アカウントに対する Intune サポート<!-- 747685 -->
最大 100 個の異なる Apple Device Enrollment Program (DEP) または Apple School Manager アカウントからのデバイス登録が、Intune でサポートされます。 アップロードされる各トークンは、登録プロファイルとデバイスで、別々に管理できます。 アップロードされる DEP および School Manager のトークンごとに、異なる登録プロファイルを自動で割り当てることができます。 複数の School Manager トークンがアップロードされた場合、Microsoft 学校データ同期と共有できるのは、一度に 1 つのみです。

移行後、Graph で Apple DEP および ASM を管理するベータ版の Graph API と公開されたスクリプトは、動作しなくなります。 現在、新しいベータ版の Graph API の開発が進行中で、移行後にリリースされる予定です。

### <a name="select-device-categories-by-using-the-access-work-or-school-settings----1058963-eeready---"></a>[職場または学校にアクセスする] 設定を用いたデバイス カテゴリの選択<!-- 1058963 eeready --> 
[デバイス グループ マッピング](https://docs.microsoft.com/en-us/intune/device-group-mapping)を有効にした場合、**[設定]** > **[アカウント]** > **[職場または学校にアクセスする]** の **[接続]** から登録後、または out-of-box experience の際に、Windows 10 のユーザーはデバイス カテゴリの選択を求められます。

### <a name="targeting-compliance-policies-to-devices-in-device-groups---1307012---"></a>デバイス グループのデバイスへのコンプライアンス ポリシーのターゲット<!--1307012 -->

ユーザー グループ内のユーザーを、コンプライアンス ポリシーのターゲットにできます。 デバイス グループ内のデバイスを、コンプライアンス ポリシーのターゲットにできます。 

### <a name="including-and-excluding-app-assignment-based-on-groups----1406920---"></a>グループに基づくアプリ割り当ての追加と除外<!-- 1406920 -->

アプリの割り当て時、および割り当ての種類の選択後に、含めるグループと、除外するグループを選択できます。 含まれるグループとして、あらかじめ作成されているグループ (すべてのユーザー、すべてのデバイス、すべてのユーザーとすべてのデバイス) を使用することもできます。

### <a name="remote-erase-command-support----1438084---"></a>リモートの "消去" コマンド サポート <!-- 1438084 -->

管理者は、消去コマンドをリモートで発行できます。

> [!IMPORTANT]
> 消去コマンドは、元に戻すことができないため、使用する際は注意が必要です。

消去コマンドでは、オペレーティング システムを含むすべてのデータが、デバイスから削除されます。 また、そのデバイスも、Intune 管理から削除されます。 ユーザーに対して警告は表示されません。また、コマンドを発行すると、消去は即座に実行されます。

6 桁の回復用 PIN を構成することができます。 この PIN を使用すると、消去されたデバイスのロックが解除され、オペレーティング システムの再インストールが開始されます。 PIN は、消去が開始されると、Intune のデバイスの概要ブレードのステータス バーに表示されます。 消去が完了するまでの間、PIN はずっと表示されます。 消去が完了したら、デバイスは Intune 管理から完全に削除されます。 デバイスを復元する人が誰であっても、そのデバイスを使用できるように、回復用 PIN は必ず記録するようにしてください。

### <a name="windows-information-protection-wip-encrypted-data-in-windows-search-results----1469193---"></a>Windows 検索結果の Windows 情報保護 (WIP) 暗号化データ<!-- 1469193 -->

Windows 情報保護 (WIP) ポリシーの新しい設定により、WIP で暗号化されたデータを Windows の検索結果に含めるかどうかを制御できます。

### <a name="website-learning-mode----1631908---"></a>Web サイトの学習モード <!-- 1631908 -->

Intune では、Windows 情報保護 (WIP) 学習モードの拡張機能が導入されます。 WIP が有効になっているアプリの情報を表示できるだけでなく、作業データを Web サイトで共有しているデバイスの概要も表示できます。 この情報を使用して、グループおよびユーザーの WIP ポリシーに追加する Web サイトを判断できます。

### <a name="updates-to-compliance-emails---1637547---"></a>コンプライアンスのメールに対する変更 <!--1637547 -->

コンプライアンス違反のデバイスを報告するメールが送信される際、そのコンプライアンス違反のデバイスの詳細が含まれるようになります。 この変更を反映するために、[コンプライアンス違反に対する措置の自動化](#actions-for-noncompliance)に関する記事が更新されます。

### <a name="conditional-access-policies-for-intune-is-only-available-from-the-azure-portal-----1737088-1634311---"></a>Intune の条件付きアクセス ポリシーの利用可能場所が Azure Portal のみに<!-- 1737088 1634311 --> 
条件付きアクセスの構成および管理場所をシンプルにまとめます。 ポリシーの構成や管理を、[Azure Portal](https://portal.azure.com) の **[Azure Active Directory]** > **[条件付きアクセス]** から行えるようになります。 便宜上、**[Intune]** > **[条件付きアクセス]** の、Azure Portal 内にある Intune からこのブレードにアクセスすることもできます。

###  <a name="alerts-for-expired-tokens-and-tokens-that-will-soon-expire----1639263---"></a>期限切れトークンと有効期限が近いトークンのアラート<!-- 1639263 -->
有効期限が切れているトークンと、有効期限が近づいているトークンのアラートが概要ページに表示されます。 1 つのトークンのアラートをクリックすると、そのトークンの詳細ページに移動します。  複数のトークンのアラートをクリックすると、トークンのステータスが表示された全トークンの一覧に移動します。 管理者は、有効期限が来る前にトークンを更新する必要があります。

### <a name="remote-printing-over-a-secure-network----1709994----"></a>セキュリティで保護されたネットワークでのリモート印刷<!-- 1709994  -->
PrinterOn のワイヤレス モバイル印刷ソリューションは、時間や場所を問わない、セキュリティで保護されたネットワークでのリモート印刷を可能にします。 PrinterOn は、iOS 向けと Android 向けのどちらの Intune APP SDK とも統合します。 管理コンソールの Intune の **[アプリ保護ポリシー]** ブレードから、アプリ保護ポリシーのターゲットをこのアプリにすることもできます。 エンド ユーザーは、Play ストア、または iTunes から PrinterOn for Microsoft アプリをダウンロードして、Intune エコシステム内で使用できます。

### <a name="approve-the-company-portal-app-for-android-for-work---1797090---"></a>Android for Work のポータル サイト アプリの承認<!--1797090 -->
Android for Work を使用している組織は、Android 用のポータル サイト アプリを手動で承認して、管理された Google Play ストアから引き続き自動更新を受信できるようにする必要があります。

### <a name="microsoft-graph-api-for-intune---general-availability-----1833289---"></a>Intune の Microsoft Graph API - 一般提供開始  <!-- 1833289 -->
Microsoft Graph の Intune API では、データやメソッドに対してプログラムによってアクセスし、Intune サービスの管理操作を自動化することができます。  この API の**一般提供**開始に伴い、ユーザー、パートナー、および開発者の皆様は、この API を活用して、Intune や、Microsoft Graph で利用可能なその他の Microsoft サービスのサポートと関係のある、またはそのようなサービスのサポートを必要とする、社内のソリューション、または市販のソリューションと統合できます。 

<!-- the following are present prior to 1801 -->

### <a name="app-protection-policies-----679615---"></a>アプリ保護ポリシー  <!-- 679615 -->
Intune App Protection ポリシーは、既定のグローバル ポリシーを作成し、テナント全体のすべてのユーザーに保護をすばやく適用する機能を提供します。

### <a name="revoking-ios-volume-purchase-program-apps-----820863---"></a>iOS Volume-Purchase Program アプリの取り消し  <!-- 820863 -->
1 つ以上の iOS Volume-Purchase Program (VPP) アプリがインストールされた特定のデバイスでは、そのデバイスで関連付けられているデバイス ベース アプリのライセンスを取り消すことができます。 アプリのライセンスを取り消しても、関連する VPP アプリがデバイスからアンインストールされるわけではありません。 VPP アプリをアンインストールするには、割り当てアクションを **[アンインストール]** に変更する必要があります。 詳細については、「[Volume Purchase Program で購入した iOS アプリを Microsoft Intune で管理する方法](vpp-apps-ios.md)」をご覧ください。

### <a name="revoke-licenses-for-an-ios-volume-purchasing-program-token----820870---"></a>iOS Volume Purchasing Program トークンのライセンスの取り消し <!-- 820870 -->
特定の VPP トークンのすべての iOS Volume Purchasing Program (VPP) アプリのライセンスを取り消すことができます。

### <a name="network-access-control-nac-device-check-in-reporting-----1232250---"></a>ネットワーク アクセス制御 (NAC) デバイス チェックイン レポート <!-- 1232250 -->
この変更の前には、IT 管理者は NAC で管理されているデバイスが NAC ソリューションと通信しているかどうかを Intune 側から判断することができませんでした。 NAC で管理されているデバイスが NAC ソリューションと通信していない場合、そのデバイスは NAC ソリューションに非準拠のデバイスとみなされます。そのため、NAC で管理されているデバイスは NAC ソリューション自体にブロックされ、その後デバイスの準拠状態に依存する条件付きアクセス ポリシーによってブロックされます。

今回の変更により、IT 管理者はどの NAC で管理されているデバイスが NAC ソリューションと正常に通信したかを確認できるようになります。 この新機能は、Intune 内のデバイス準拠ワークロードに配置された 2 つの新しい監視機能で構成され、次のように統計が表示されます。
- **過去 1 時間の NAC 呼び出しの平均**
- **最後の NAC 受信要求 (日付/時刻)**

### <a name="new-ios-device-action------1244701---"></a>新しい iOS デバイス アクション <!-- 1244701 -->
iOS 10.3 監視下のデバイスをシャット ダウンできます。 このアクションでは、エンド ユーザーへの警告なしにデバイスが即時シャットダウンされます。 **シャット ダウン (監視モードのみ)** アクションは、**デバイス** ワークロードでデバイスを選択した場合に、デバイス プロパティに表示されます。


### <a name="intune-now-provides-the-account-move-operation-----1573558-1579830---"></a>Intune で、アカウントの移動操作が使用できるようになりました。<!-- 1573558, 1579830 -->
**アカウントの移動**を行うと、Azure スケール ユニット (ASU) 間でテナントが移動します。 お客様が Intune サポート チームに連絡してアカウントの移動をリクエストする、お客様が開始するシナリオと、Microsoft でバックエンドでのサービスの調整が必要な、Microsoft 主導のシナリオの両方で**アカウントの移動**を使用できます。 **アカウントの移動**中は、テナントは読み取り専用モード (ROM) になります。 ROM 期間中は、デバイスの登録や名前変更、コンプライアンス状態の更新などのサービス操作が失敗します。




<!-- the following are present prior to 1712 -->
### <a name="assign-office-365-mobile-apps-to-ios-and-android-devices-using-built-in-app-type----1332318---"></a>組み込み型のアプリを利用し、iOS デバイスまたは Android デバイスに Office 365 モバイル アプリを割り当てる <!-- 1332318 -->
**組み込み**型のアプリであれば、Office 365 アプリを作成し、管理している iOS または Android デバイスに割り当てることが簡単にできます。 これらのアプリには、Word、Excel、PowerPoint、OneDrive などの 0365 アプリがあります。 アプリの種類に特定のアプリを割り当て、アプリ情報構成を編集できます。


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


### <a name="configure-an-ios-app-pin----1586774---"></a>iOS アプリ PIN を構成する <!-- 1586774 -->
間もなく、対象の iOS アプリで PIN を要求できるようになります。 Azure Portal で PIN 要件と有効期限 (日数) を構成できます。 必須にすると、iOS アプリにアクセスする前に、新しい PIN を設定して使用するようにユーザーが要求されます。 Intune App SDK によるアプリ保護を有効にしている iOS アプリでのみこの機能がサポートされます。


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




<!-- the following are present prior to 1711 -->


### <a name="redirecting-macos-users-to-our-new-company-portal-app---1380728--"></a>新しいポータル サイト アプリへの macOS ユーザーのリダイレクト<!--1380728-->   
エンド ユーザーは、ポータル サイトの Web サイトにログインして macOS デバイスを登録するとき、プロセスを完了するために macOS 用の新しいポータル サイト アプリをダウンロードするように指示されます。 これは、OS X El Capitan 10.11 以降を使っている macOS デバイスの場合に発生します。 



<!-- the following are present prior to 1709 -->

### <a name="intune-managed-browser-support-for-ios-and-android----1374196---"></a>iOS および Android <!-- 1374196 --> 用の Intune Managed Browser のサポート
2017 年 10 月の時点で、Android アプリで使用する Intune Managed Browser アプリは、Android 4.4 以降を実行しているデバイスのみをサポートします。 iOS の Intune Managed Browser アプリは、iOS 9.0 以降を実行しているデバイスのみをサポートします。 以前のバージョンの Android および iOS は、Managed Browser の使用を続けることができますが、新しいバージョンのアプリをインストールすることはできません。また、アプリのすべての機能にアクセスできるとは限りません。 サポートされるオペレーティング システム バージョンにこれらのデバイスを更新することをお勧めします。


### <a name="improved-error-message-for-when-a-user-reaches-the-maximum-number-of-devices-allowed-to-enroll----1270370---"></a>ユーザーが登録できるデバイスの最大数に達したときのエラー メッセージの向上<!-- 1270370 -->
Android デバイスのエンド ユーザーに対して、一般的なエラー メッセージでなく、「IT 管理者が許可している数よりも多くのデバイスが登録されています。登録したデバイスを削除するか、IT 管理者に支援を求めてください。」という分かりやすい、実践的なエラー メッセージが表示されるようになりました。




## <a name="notices"></a>通知

現在のところ、アクティブな通知はありません。




### <a name="see-also"></a>関連項目
最近の開発状況について詳しくは、「[Microsoft Intune の新機能](whats-new.md)」をご覧ください。
