---
title: "初期エディション"
description: 
keywords: 
author: brenduns
ms.author: brenduns
manager: angrobe
ms.date: 10/19/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: a2e6fd2381286aa652a04b5ed34ab21c57ed85f6
ms.sourcegitcommit: bb2c181fd6de929cf1e5d3856e048d617eb72063
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/20/2017
---
# <a name="the-early-edition-for-microsoft-intune---october-2017"></a>Microsoft Intune の初期エディション - 2017 年 10 月

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

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Azure Active Directory の Web サイトでは、Intune Managed Browser アプリを要求し、Managed Browser (パブリック プレビュー) に対するシングル サインオンをサポートすることができる <!-- 710595 -->   
Azure Active Directory (Azure AD) を使っている場合、モバイル デバイスでの Web サイトへのアクセスを、Intune Managed Browser アプリに制限することができます。 Managed Browser では、Web サイトのデータは安全性を維持され、エンド ユーザーの個人データと分離されます。 さらに、Managed Browser は、Azure AD によって保護されているサイトに対するシングル サインオン機能をサポートします。 Managed Browser にサインインすると、または Intune によって管理されている別のアプリでデバイスの Managed Browser を使うと、ユーザーが資格情報を入力しなくても、Managed Browser は Azure AD によって保護されている会社サイトにアクセスできます。 この機能は、Outlook Web Access (OWA) や SharePoint Online などのサイトだけでなく、Azure App プロキシ経由でアクセスされるイントラネット リソースのような他の企業サイトにも適用されます。

### <a name="troubleshoot-enrollment-issues------746324----"></a>登録に関する問題をトラブルシューティングする <!--- 746324 --->  
トラブルシューティング ワークスペースには、ユーザーの登録に関する問題が表示されます。 問題に関する詳細と推奨される修復手順は、管理者およびヘルプ デスクのオペレーターが問題をトラブルシューティングするのに役立ちます。 登録に関する特定の問題はキャプチャされず、一部のエラーには推奨される修復方法がない場合があります。

### <a name="admins-can-now-configure-the-firewall-settings-on-a-device-using-a-device-configuration-profile----951708---"></a>管理者は、デバイス構成プロファイルを使ってデバイスでのファイアウォールの設定を構成できるようになる <!-- 951708 -->   
管理者は、デバイスのファイアウォールを有効にすることができ、ドメイン ネットワーク、プライベート ネットワーク、パブリック ネットワークのさまざまなプロトコルを構成することもできます。  これらのファイアウォールの設定は、"Endpoint Protection" プロファイルで確認できます。

### <a name="windows-defender-application-guard-helps-protect-devices-from-untrusted-websites-as-defined-by-your-organization----958257---"></a>Windows Defender Application Guard は、組織での定義に従って、信頼されていない Web サイトからデバイスを保護する <!-- 958257 -->   
管理者は、Windows Information Protection ワークフローまたはデバイス構成の新しい "ネットワーク境界" プロファイルを使って、"信頼できる" サイトまたは "企業" サイトを定義できます。 64 ビット Windows 10 デバイスの信頼されたネットワーク境界内にないすべてのサイトは、Microsoft Edge で表示された場合、代わりに Hyper-V 仮想コンピューター内のブラウザーで開かれます。

Application Guard は、"Endpoint Protection" プロファイル内のデバイス構成プロファイルで確認できます。 デバイス構成プロファイルでは、管理者は、仮想化されたブラウザーとホスト マシンの相互作用、信頼されないサイトと信頼されるサイト、および仮想化されたブラウザーで生成されたファイルの保存を構成することができます。 デバイスで Application Guard を使うには、最初にネットワーク境界を構成する必要があります。 デバイスごとにネットワーク境界を 1 つだけ定義することが重要です。  

### <a name="windows-defender-application-guard-on-windows-10-enterprise-provides-mode-to-trust-only-authorized-apps----1031096---"></a>Windows 10 Enterprise の Windows Defender Application Guard は、承認されたアプリのみを信頼するモードを提供する <!-- 1031096 -->    
毎日何千もの悪意あるファイルが作成される状況においては、ウイルス対策の署名ベースの検出を使ってマルウェアに対抗するのでは、新しい攻撃を十分に防ぐことができない可能性があります。 Windows 10 Enterprise の Windows Defender Application Guard を使うと、ウイルス対策ソフトウェアや他のセキュリティ ソリューションによってブロックされない限りアプリを信頼するモードから、企業によって承認されたアプリのみをオペレーティング システムが信頼するモードにデバイスの構成を変更できます。 Windows Defender Application Guard でアプリに信頼を割り当てます。

Intune を使って、アプリケーション制御ポリシーを "監査のみ" モードまたは強制モードに構成できます。 "監査のみ" モードで実行している場合、アプリはブロックされません。 "監査のみ" モードでは、すべてのイベントがローカル クライアント ログに記録されます。 また、Windows コンポーネントと Windows ストア アプリの実行のみを許可するか、またはインテリジェント セキュリティ グラフで定義されている評判の良いアプリの実行も許可するかを構成することもできます。

### <a name="new-enrollment-status-page-for-windows-10-enrollments---1063201--"></a>Windows 10 の登録の新しい登録状態ページ<!--1063201-->    
ユーザーが Windows 10 デバイスを登録したときに表示される案内メッセージを構成できるようになりました。 **登録ステータス画面**を使って、Windows 10 デバイスを登録するときにエンド ユーザーに表示されるカスタム メッセージとハイパーリンクを構成します。  **登録ステータス画面**では、デバイスに適用されているポリシー設定の進行状況もエンド ユーザーに対して表示されます。  

### <a name="window-defender-exploit-guard-is-a-new-set-of-intrusion-prevention-capabilities-for-windows-10----1063615---"></a>Windows 10 用の新しい侵入防止機能セットである Window Defender Exploit Guard <!-- 1063615 -->   
Window Defender Exploit Guard は、アプリケーションが悪用される可能性を減らすカスタム規則を含み、マクロとスクリプトの脅威を防止し、評判が低い IP アドレスへのネットワーク接続を自動的にブロックして、ランサムウェアや不明の脅威からデータを保護できます。 Windows Defender Exploit Guard は、次のコンポーネントで構成されます。

- **攻撃の回避 (ASR)** は、マクロ、スクリプト、メールの脅威を防ぐことができる規則を提供します。
- **フォルダー アクセスの制御**は、保護されているフォルダーのコンテンツへのアクセスを自動的にブロックします。
- **ネットワーク フィルター**は、アプリから評判の悪い IP/ドメインへの発信接続をブロックします。
- **Exploit Protection** は、アプリケーションを悪用から保護するために使うことができるメモリ、制御フロー、およびポリシーの制限を提供します。

### <a name="app-conditional-launch-support----1193313---"></a>アプリの条件付き起動のサポート <!-- 1193313 -->
IT 管理者は、アプリケーションの起動時にモバイル アプリ管理 (MAM) によって数値の PIN ではなくパスコードを強制する要件を、Azure 管理ポータルで設定できるようになりました。 構成した場合、ユーザーは、MAM 対応のアプリケーションにアクセスする前に、要求された時点で、パスコードを設定および使用する必要があります。 パスコードは、少なくとも 1 つの特殊文字または大文字/小文字アルファベットを含む数値 PIN と定義されます。 Intune の今回のリリースでは、この機能を利用できるのは **iOS のみ**です。 Intune は、数値 PIN に同様の方法でパスコードをサポートし、最小の長さを設定して、文字やシーケンスの繰り返しを許可します。 この機能でパスコードの設定を対象アプリケーションに適用するには、アプリケーション (つまり、 WXP、Outlook、Managed Browser、Yammer) が参加して、Intune APP SDK とこの機能を実行するコードを統合する必要があります。

### <a name="app-version-number-for-line-of-business-in-device-install-status-report----1233999---"></a>デバイス インストール状態レポートでの基幹業務アプリのバージョン番号 <!-- 1233999 -->  
デバイス インストール状態レポートに、iOS および Android 用基幹業務アプリのバージョン番号が表示されます。 この情報を使って、アプリのトラブルシューティングや、古いバージョンのアプリを実行しているデバイスの検索を行うことができます。

### <a name="co-management-for-windows-10-devices-----124445---"></a>Windows 10 デバイスの共同管理 <!-- 124445 -->
共同管理は、従来の管理から最新の管理への橋渡しとなるソリューションであり、段階的なアプローチを使って移行する方向を提示します。 基本的に、共同管理は、Windows 10 デバイスを Configuration Manager と Microsoft Intune で同時に管理すると共に、Active Directory (AD) と Azure Active Directory (Azure AD) に同時に参加させることができるソリューションです。  この構成は、一度にすべてを移行できない組織が適切なペースで時間をかけて最新化するパスを提供します。  

### <a name="set-access-for-apps-by-minimum-android-security-patch-on-the-device---1278463---"></a>デバイスでの最低限の Android セキュリティ パッチによりアプリへのアクセスを設定する <!-- 1278463 -->   
管理者は、管理されたアカウントの管理対象アプリケーションにアクセスするために、デバイスにインストールする必要がある最低限の Android セキュリティ パッチを定義することができます。

> [!Note]  
> この機能は、Google によって Android 6.0 以降のデバイスについてリリースされたセキュリティ パッチだけを制限します。

### <a name="new-device-restriction-settings-for-windows-10---------1308850---"></a>Windows 10 の新しいデバイスの制限設定 <!-- 1308850 -->
-    メッセージング (モバイルのみ) - テストまたは MMS のメッセージを無効化します
-    パスワード - FIPS と、認証用の Windows Hello デバイス セカンダリ デバイスの使用を有効にする設定 
-    ディスプレイ - レガシ アプリの GDI スケーリングをオンまたはオフにする設定


### <a name="windows-10-kiosk-mode-device-restrictions----1308872---"></a>Windows 10 キオスク モード デバイスの制限 <!-- 1308872 -->   
Windows 10 デバイスのユーザーをキオスク モードに制限することができます。これは、一連の定義済みアプリにユーザーを制限します。  そのためには、Windows 10 デバイス制限プロファイルを作成し、キオスク設定を設定します。

キオスク モードは、**シングル アプリ** (1 つのアプリだけの実行をユーザーに許可) または**マルチ アプリ** (アプリのセットへのアクセスを許可) の 2 つのモードをサポートします。  ユーザー アカウントとデバイス名を定義します。これらにより、サポートされるアプリが決まります。  ユーザーはログイン時に定義済みのアプリに制限されます。  詳細については、「[AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp)」を参照してください。 

キオスク モードには以下が必要です。

- Intune が MDM 機関である必要があります。
- アプリは、ターゲット デバイスに既にインストールされている必要があります。
- デバイスは、[適切にプロビジョニングされている](https://docs.microsoft.com/windows/configuration/set-up-a-kiosk-for-windows-10-for-desktop-editions)必要があります。

### <a name="new-device-configuration-profile-for-creating-network-boundaries----1311967---"></a>ネットワーク境界を作成するための新しいデバイス構成プロファイル <!-- 1311967 -->   
**ネットワーク境界**と呼ばれるデバイス構成プロファイルを作成しました。他のデバイス構成プロファイルと同じ場所にあります。 このプロファイルを使用して、会社のもので信頼できると見なす必要があるオンライン リソースを定義します。 Windows Defender Application Guard や Windows Information Protection などの機能をデバイスで使用するには、"*事前*" にデバイスに対してネットワーク境界を定義する必要があります。 デバイスごとにネットワーク境界を 1 つだけ定義することが重要です。

信頼できるエンタープライズ クラウド リソース、IP アドレス範囲、内部プロキシ サーバーを定義できます。 定義したネットワーク境界は、Windows Defender Application Guard や Windows Information Protection 保護などの他の機能で使うことができます。

###  <a name="two-additional-settings-for-windows-defender-antivirus----1338409---"></a>Windows Defender ウイルス対策用の 2 つの追加設定<!-- 1338409 -->  
**ファイル ブロック レベル**

| | |
|---|---|
| 未構成 | **未構成**は、Windows Defender ウイルス対策の既定のブロック レベルを使用し、正当なファイルが検出されるリスクを高めることなく強力な検出を提供します。 |
| 高 | **高**は、強力なレベルの検出を適用します。
| 高 +  | **高 +** は、高いレベルに加えて、クライアントのパフォーマンスに影響を与える可能性がある保護手段を提供します。
| ゼロ トレランス  | **ゼロ トレランス**は、不明な実行可能ファイルをすべてブロックします。 |

まれですが、**高**に設定すると、一部の正当なファイルが検出される可能性があります。
ファイル ブロック レベルは既定の**未構成**に設定することをお勧めします。

**クラウドによるファイル スキャンの時間延長**  

| | |
|--|--|
| 秒数 (0 - 50) | Windows Defender ウイルス対策がクラウドからの結果の待機中にファイルをブロックする最大時間を指定します。 既定値は 10 秒です。ここで指定した延長時間 (最大 50 秒) は、この 10 秒間に追加されます。 ほとんどの場合、スキャンは最大値よりはるかに短い時間で済みます。 時間を延長すると、クラウドは疑わしいファイルを徹底的に調査できます。 この設定を有効にし、少なくとも 20 秒の追加を指定することをお勧めします。 |


### <a name="support-for-symantec-cloud-certification-authority-ca-----1333638---"></a>Symantec クラウド証明機関 (CA) のサポート <!-- 1333638 -->    
Intune は Symantec クラウド CA をサポートするようになり、Intune Certificate Connector は Symantec クラウド CA から Intune で管理対象デバイスに PKCS 証明書を発行できます。 Microsoft 証明機関 (CA) で Intune Certificate Connector を既に使っている場合は、Intune Certificate Connector の既存の設定を利用して、Symantec CA のサポートを追加できます。



### <a name="citrix-vpn-added-for-windows-10-devices----1512457---"></a>Windows 10 デバイスに追加された Citrix VPN <!-- 1512457 -->  
ユーザーは、Windows 10 デバイス用に Citrix VPN を構成することができます。 Windows 10 以降用に VPN を構成するときに、**[基本 VPN]** ブレードの *[接続の種類を選びます]* の一覧で、Citrix VPN を選ぶことができます。

> [!Note]
> Citrix の構成は、iOS および Android 用に存在しました。





<!-- the following are present prior to 1710 -->

### <a name="google-play-protect-support-on-android----908720----"></a>Android の Google Play Protect サポート <!-- 908720  -->  
Android Oreo のリリースに伴い、セキュリティで保護されたアプリおよび Android イメージをユーザーや組織が実行できる、Google Play Protect という一連のセキュリティ機能が Google より提供されました。 Intune では、SafetyNet リモート構成証明をはじめとした Google Play Protect の各機能をサポートします。  管理者は、Google Play Protect が構成され正常な状態であることが求められるコンプライアンス ポリシー要件を設定できます。 **[SafetyNet デバイスの構成証明]** 設定では、デバイスが正常な状態であり危険にさらされていないことを確認するために、デバイスを Google サービスに接続する必要があります。 管理者は、インストール済みのアプリが Google Play 開発者サービスによって検証されることを必須にする、Android for Work の構成プロファイル設定を設定することもできます。  条件付きアクセスでは、デバイスが Google Play Protect の要件に準拠していない場合に、ユーザーが企業リソースにアクセスできなくなる可能性があります。 


### <a name="support-for-windows-10-edition-upgrade-policy------903672archived-1119689---"></a>Windows 10 エディション アップグレード ポリシーのサポート <!-- 903672(archived), 1119689 -->  
Windows 10 デバイスを Windows 10 Education、Windows 10 Education N、Windows 10 Professional、Windows 10 Professional N、Windows 10 Professional Education、Windows 10 Professional Education N にアップグレードする Windows 10 エディション アップグレード ポリシーを作成できます。Windows 10 エディション アップグレードの詳細については、[Windows 10 エディションのアップグレードを構成する方法](edition-upgrade-configure-windows-10.md)に関するページを参照してください。


### <a name="intune-mam-and-outlook-for-android-add-ins-----1450688---"></a>Android 用 Intune MAM および Outlook のアドイン  <!-- 1450688 -->
数週間以内に、Office チームによって Android 版 Outlook のアドインが発表されます。 このアドインの機能セットは、Windows、iOS、Web、および Mac 版の Outlook で既にリリース済みのものです。 アドインは Exchange を介して管理されるため、Exchange 管理者がアドインへのアクセスを無効にしていない限り、ユーザーは Outlook と管理対象外のアドイン アプリケーションとの間でデータとメッセージをコピーおよび共有できるようになります。 

アドインへのユーザーのアクセス許可を管理するには、Exchange 管理者と協力して、MAM データ保護ポリシーがアドインに必ず適用されるようにしてください。

#### <a name="how-does-this-affect-me"></a>ユーザーへの影響
Exchange ポリシーが、既にアドインのサイド ローディングやアドインのインストールを防ぐように設定されている場合は、これ以上読む必要はありません。 MAM ポリシーは、想定どおりに適用されます。 ただし、Android 版 Outlook 内での切り取り、コピー、貼り付け操作を制限するように MAM 内のポリシーを設定してあり、Exchange でアドイン ポリシーを設定していない場合は、既定ではユーザーが Outlook にアドインをインストールできるということを覚えておく必要があります。 これらのアドインでは、メッセージ本文、件名、その他のメッセージ プロパティにアクセスできます。 Exchange 管理者に "自分の Marketplace アプリ" の役割と "自分のカスタム アプリ" の役割を削除してもらうと、ユーザーがアドインをインストールできないようにすることができます。

Exchange の設定を変更すると、Windows 版、iOS 版、Web 版、Mac 版、モバイル版のすべての Outlook に適用されます。 

#### <a name="what-do-i-need-to-do"></a>必要な作業
現在の Exchange ポリシーを確認します。 IT 部門とヘルプ デスクのスタッフに知らせます。 特定の質問や懸念事項をサポート チームに問い合わせます。 




<!-- the following are present prior to 1709 -->

### <a name="actions-for-non-compliance----730266--846515---"></a>コンプライアンス非対応に対するアクション <!--730266  846515 -->     
"*コンプライアンス非対応に対するアクション*" は、コンプライアンス非対応のデバイスに対してアクションを実行できるようにするコンプライアンス ポリシーの新しい機能です。 単一または複数のアクションを指定できます。また、実行する必要があるアクションの期間を指定することもできます。 たとえば、デバイスが非対応になった直後に電子メールで、その非対応デバイスのユーザーに通知することができます。あるいは、非対応デバイスに対して、条件付きアクセスで 3 日間の猶予期間後の企業リソースへのアクセスをブロックすることができます。

### <a name="android-for-work-support-for-lookout----1087312---"></a>Lookout の Android for Work サポート <!-- 1087312 -->   
Lookout を備えた Intune コネクタでは、Lookout for Work アプリの使用時、Android for Work デバイスをサポートします。 コンテナーの内外に Lookout アプリを展開できるようになる予定です。

### <a name="intune-app-protection-and-citrix-mdx-development-tools----709185---"></a>Intune App Protection と Citrix MDX 開発ツール<!-- 709185 -->
Citrix XenMobile MDX と Microsoft Intune を組み合わせ、デバイスとアプリを管理することができます。 これにより、Citrix の mVPN テクノロジを使用し、Intune アプリの保護ポリシーでアプリを管理できるようになります。

Citrix の MDX mVPN テクノロジとの統合を可能にする iOS および Android 用の Intune アプリ ラッピング ツールと Intune アプリ SDK を含むコード リポジトリを見つけることができるはずです。

#### <a name="how-integration-with-intune-works"></a>Intune との統合のしくみ
リスクは、Zimperium を実行するデバイスから収集される製品利用統計情報に基づいて評価されます。 Intune デバイス コンプライアンス ポリシーで有効にした Zimperium リスク評価に基づき、EMS 条件付きアクセスのポリシーを構成できます。Intune デバイス コンプライアンス ポリシーは、検出された脅威に基づき、非準拠デバイスから企業リソースへのアクセスを許可したり、拒否したりするために利用できます。

### <a name="on-premises-exchange-connector-high-availability-support-----676614---"></a>オンプレミスの Exchange Connector の高可用性のサポート  <!-- 676614 -->   
オンプレミスの Exchange Connector に複数のクライアント アクセス サーバー (CAS) ロールを持たせることができます。 たとえば、メインの CAS に障害が発生した場合、他の CAS にフォールバックするクエリを Exchange Connector が受信するようにできます。 この機能により、サービスが中断されないことが保証されます。

### <a name="system-center-operations-manager-management-pack-for-exchange-connector----885457---"></a>Exchange Connector 用の System Center Operations Manager 管理パック <!-- 885457 -->   
Exchange Connector 用の System Center Operations Manager 管理パックが Exchange Connector のログ解析に利用できるようになります。 問題のトラブルシューティングを行う必要がある場合、この管理パックによって別の方法で Intune を監視できます。


## <a name="intune-apps"></a>Intune アプリ


### <a name="redirecting-macos-users-to-our-new-company-portal-app---1380728--"></a>新しいポータル サイト アプリへの macOS ユーザーのリダイレクト<!--1380728-->   
エンド ユーザーは、ポータル サイトの Web サイトにログインして macOS デバイスを登録するとき、プロセスを完了するために macOS 用の新しいポータル サイト アプリをダウンロードするように指示されます。 これは、OS X El Capitan 10.11 以降を使っている macOS デバイスの場合に発生します。 

### <a name="certificate-based-authentication-support-on-the-company-portal-for-ios---1029830--"></a>iOS 用ポータル サイトでの証明書ベースの認証のサポート <!--1029830-->
iOS 用ポータル サイト アプリでの証明書ベースの認証 (CBA) のサポートが追加されました。 CBA を使用するユーザーは、ユーザー名を入力した後、[Sign in with a certificate]\(証明書でサインインする\) リンクをタップします。 CBA は、Android および Windows 用のポータル サイト アプリで既にサポートされています。 詳細については、「[ポータル サイト アプリにサインインするには](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal)」を参照してください。

<!-- the following are present prior to 1710 -->



### <a name="apps-that-are-available-with-or-without-enrollment-can-now-be-installed-without-being-prompted-for-enrollment----1334712---"></a>登録の有無にかかわらず利用可能なアプリについて、登録を求められずにインストールできるようになりました。 <!-- 1334712 -->
Android ポータル サイト アプリでの登録の有無にかかわらず利用可能な業務用アプリについて、登録を求められずにインストールできます。


<!-- the following are present prior to 1709 -->

### <a name="intune-managed-browser-support-for-ios-and-android----1374196---"></a>iOS および Android <!-- 1374196 --> 用の Intune Managed Browser のサポート
2017 年 10 月の時点で、Android アプリで使用する Intune Managed Browser アプリは、Android 4.4 以降を実行しているデバイスのみをサポートします。 iOS の Intune Managed Browser アプリは、iOS 9.0 以降を実行しているデバイスのみをサポートします。 以前のバージョンの Android および iOS は、Managed Browser の使用を続けることができますが、新しいバージョンのアプリをインストールすることはできません。また、アプリのすべての機能にアクセスできるとは限りません。 サポートされるオペレーティング システム バージョンにこれらのデバイスを更新することをお勧めします。


### <a name="improved-error-message-for-when-a-user-reaches-the-maximum-number-of-devices-allowed-to-enroll----1270370---"></a>ユーザーが登録できるデバイスの最大数に達したときのエラー メッセージの向上<!-- 1270370 -->
エンドユーザーに一般的なエラー メッセージでなく、「IT 管理者が許可している数よりも多くのデバイスが登録されています。登録したデバイスを削除するか、IT 管理者に支援を求めてください。」という分かりやすい、実践的なエラー メッセージが表示されるようになりました。




## <a name="notices"></a>通知

### <a name="device-and-app-management-integration----677972---"></a>デバイスとアプリの管理の統合 <!-- 677972 -->   
Intune のモバイル デバイス管理 (MDM) とモバイル アプリケーション管理 (MAM) はどちらも Azure Portal からアクセスできるようになり、Intune はアプリケーション管理とデバイス管理に関する IT 管理者エクスペリエンスの統合を開始しました。 これらの変更は、デバイスとアプリの管理エクスペリエンスの簡素化を目的としたものです。

MDM と MAM の変更の詳細については、[Intune サポート チーム ブログ](https://blogs.technet.microsoft.com/intunesupport/2017/09/19/support-tip-setting-up-communication-between-mam-managed-and-mdm-managed-apps/)での案内をご覧ください。




### <a name="see-also"></a>関連項目
最近の開発状況について詳しくは、「[Microsoft Intune の新機能](whats-new.md)」をご覧ください。
