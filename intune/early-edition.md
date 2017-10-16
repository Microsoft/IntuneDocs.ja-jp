---
title: "初期エディション"
description: 
keywords: 
author: brenduns
ms.author: brenduns
manager: angrobe
ms.date: 09/29/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f2e11a7fbe226932206f6946ef0603307e76c69c
ms.sourcegitcommit: 4184db38d1a9a223e680bcb4c9b732f7069bf510
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2017
---
# <a name="the-early-edition-for-microsoft-intune---september-2017"></a>Microsoft Intune の初期エディション - 2017 年 9 月

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


### <a name="google-play-protect-support-on-android----908720----"></a>Android の Google Play Protect サポート <!-- 908720  -->  
Android Oreo のリリースに伴い、セキュリティで保護されたアプリおよび Android イメージをユーザーや組織が実行できる、Google Play Protect という一連のセキュリティ機能が Google より提供されました。 Intune では、SafetyNet リモート構成証明をはじめとした Google Play Protect の各機能をサポートします。  管理者は、Google Play Protect が構成され正常な状態であることが求められるコンプライアンス ポリシー要件を設定できます。 **[SafetyNet デバイスの構成証明]** 設定では、デバイスが正常な状態であり危険にさらされていないことを確認するために、デバイスを Google サービスに接続する必要があります。 管理者は、インストール済みのアプリが Google Play 開発者サービスによって検証されることを必須にする、Android for Work の構成プロファイル設定を設定することもできます。  条件付きアクセスでは、デバイスが Google Play Protect の要件に準拠していない場合に、ユーザーが企業リソースにアクセスできなくなる可能性があります。 

### <a name="prevent-users-of-android-devices-from-changing-their-device-date-and-time-----1333292---"></a>Android デバイス ユーザーによるデバイスの日付と時刻の変更を防止する <!-- 1333292 -->
[Android カスタム デバイス ポリシー](custom-settings-android.md)を使用して、Android デバイス ユーザーがデバイスの日付や時刻を変更できないように設定できます。
この設定を行うには、./Vendor/MSFT/PolicyManager/My/System/AllowDateTimeChange の設定 URI を使用して Android カスタム ポリシーを構成し、これを **TRUE** に設定して該当のグループに割り当てます。

### <a name="view-app-protection-policy-assignments-for-troubleshooting-----1475003---"></a>トラブルシューティングのアプリ保護ポリシー割り当てを確認する <!--  1475003 -->
今後のリリースでは、トラブルシューティング ブレードにある **[割り当て]** ボックスの一覧に、**[App protection policy]\(アプリの保護ポリシー\)** オプションが追加される予定です。 アプリの保護ポリシーを選んで、特定のユーザーに割り当てられているアプリ保護ポリシーを確認できるようになります。

### <a name="create-ios-apps-limited-to-specific-regional-apple-app-stores----1281692---"></a>特定地域の Apple App Store のみを対象とした iOS アプリを作成する <!-- 1281692 -->
Apple App Store 管理対象アプリの作成時に、国のロケールを指定できるようになります。

> [!NOTE]  
> 現在、Apple App Store の管理対象アプリは、米国のストアで販売されるものしか作成できません。

### <a name="select-apple-country-store-to-sync-vpp-apps-----1332311---"></a>Apple の国別ストアを選択して VPP アプリを同期する <!-- 1332311 -->  
Volume Purchase Program (VPP) トークンをアップロードする際に、VPP 国別ストアを構成できます。 指定された VPP 国別ストアにある全ロケールに対応した VPP アプリが、Intune によって同期されます。

> [!NOTE]  
> 現在、Intune で同期されるのは、Intune テナントが作成された Intune ロケールに一致する VPP 国別ストアの VPP アプリのみです。

###  <a name="update-ios-vpp-user-and-device-licensed-apps-----1305564---"></a>iOS VPP ユーザーとデバイスにライセンスされたアプリを更新する <!-- 1305564 -->  
Intune サービスを介して特定の iOS VPP トークンに対して購入されたすべてのアプリを更新するように、トークンを構成できるようになります。 アプリ ストア内の VPP アプリ更新プログラムが Intune によって検出され、デバイスのチェックイン時に自動的にデバイスにプッシュされます。

### <a name="ios-11-support----1428975---"></a>iOS 11 のサポート <!-- 1428975 -->
Apple からリリースされ次第、Intune では iOS 11 のサポートを開始します。

### <a name="new-settings-for-windows-10-team-device-restriction-profile------1308838----"></a>Windows 10 Team デバイス制限プロファイルの新しい設定 <!--- 1308838  -->
このリリースでは、Surface Hub デバイスの制御に役立つように、Windows 10 Team デバイス制限プロファイルに多数の新しい設定が追加されています。
このプロファイルについて詳しくは、[Windows 10 Team デバイスの制限設定](device-restrictions-windows-10-teams.md)に関するページをご覧ください。

### <a name="support-for-windows-10-edition-upgrade-policy------903672-1119689---"></a>Windows 10 エディション アップグレード ポリシーのサポート <!-- 903672, 1119689 -->  
Windows 10 デバイスを Windows 10 Education、Windows 10 Education N、Windows 10 Professional、Windows 10 Professional N、Windows 10 Professional Education、Windows 10 Professional Education N にアップグレードする Windows 10 エディション アップグレード ポリシーを作成できます。Windows 10 エディション アップグレードについて詳しくは、[Windows 10 エディションのアップグレードを構成する方法](edition-upgrade-configure-windows-10.md)に関するページをご覧ください。

### <a name="review-policy-compliance-for-windows-10-update-rings----1352223---"></a>Windows 10 更新リングのポリシー準拠状況を確認する <!-- 1352223 -->  
**[ソフトウェア更新プログラム]** > **[更新プログラムごとのリングの展開の状態]** から Windows 10 更新リングのポリシー レポートを確認できます。 ポリシー レポートには、構成した更新リングの展開状態が表示されています。 

### <a name="windows-10-company-portal-app-added-to-windows-information-protection-allow-policy----677129---"></a>Windows 情報保護許可ポリシーに追加された Windows 10 ポータル サイト アプリ <!-- 677129 -->  
Windows 10 ポータル サイト アプリが更新され、Windows 情報保護 (WIP) をサポートします。 アプリは、WIP 許可ポリシーに追加できます。 この変更により、アプリを **[除外対象]** ボックスの一覧に追加する必要がなくなります。 

### <a name="remote-support-for-windows-and-windows-mobile-devices-----1070473---"></a>Windows と Windows Mobile デバイスのリモート サポート <!-- 1070473 -->    
[TeamViewer](https://www.teamviewer.com) ソフトウェア (別売り) を使用して、Windows と Windows Mobile デバイスを実行するユーザーに Intune で リモート アシスタンスを提供できるようになります。

### <a name="scan-devices-with-windows-defender----1280988--1280990-----"></a>Windows Defender でデバイスをスキャンする <!-- 1280988  1280990   -->
管理された Windows 10 デバイス上で Windows Defender ウイルス対策を使って **クイック スキャン**、**フル スキャン**、**署名更新**を実行できるようになります。 デバイスの概要ブレードから、デバイス上で実行するアクションを選びます。 コマンドがデバイスに送信される前に、アクションの確認を求められます。 

**クイック スキャン**: クイック スキャンでは、レジストリ キーや既知の Windows スタートアップ フォルダーなど、マルウェアが起動するように登録されている場所がスキャンされます。 クイック スキャンには、平均 5 分かかります。 クイック スキャンは、ファイルの開閉時やユーザーがフォルダーに移動したときにファイルをスキャンする **[Always-on real-time protection]\(リアルタイム保護を常に有効にする\)** 設定と組み合わせると、システムやカーネル内に存在する可能性があるマルウェアから保護するのに役立ちます。 完了すると、ユーザーのデバイスにスキャン結果が表示されます。 

**フル スキャン**: フル スキャンは、マルウェアの脅威が発生したデバイスで、徹底的なクリーンアップが必要な非アクティブなコンポーネントがあるかどうかを識別するために使用できます。また、オンデマンド スキャンを実行する場合に便利です。 フル スキャンは、実行に 1 時間かかる場合があります。 完了すると、ユーザーのデバイスにスキャン結果が表示されます。 

**署名更新**: 署名更新コマンドを使用すると、Windows Defender ウイルス対策のマルウェア定義と署名が更新されます。 マルウェア検出における Windows Defender ウイルス対策ソフトウェアの効果を確保するために役立ちます。 この機能は Windows 10 デバイス専用であり、デバイスのインターネット接続を一時中断します。 

### <a name="bitlocker-device-configuration----1397398---"></a>BitLocker デバイス構成 <!-- 1397398 -->  
**[Windows 暗号化] > [Base Settings]\(基本設定\)** に、新たに **[他のディスクの暗号化に対する警告]** 設定が追加されます。この設定では、ユーザーのデバイス上で使われている可能性がある、他のディスクの暗号化についての[警告プロンプト](https://docs.microsoft.com/en-us/windows/client-management/mdm/bitlocker-csp#allowarningforotherdiskencryption)を無効にできます。  警告プロンプトの利用には、デバイス上で BitLocker をセットアップする前にエンドユーザーの同意が必要であり、エンドユーザーによって承諾されるまで BitLocker のセットアップはブロックされます。  この新しい設定では、エンドユーザーに対する警告が無効になります。

### <a name="company-portal-for-windows-81-and-windows-phone-81-moving-to-sustaining-mode---1428681--"></a>Windows 8.1 および Windows Phone 8.1 のポータル サイトの維持モードへの移行 <!--1428681-->
2017 年 10 月より、Windows 8.1 および Windows Phone 8.1 用ポータル サイト アプリは、維持モードに移行されます。 つまり、当該アプリに加え、登録やコンプライアンスといった既存のシナリオは、これらのプラットフォームで引き続きサポートされます。 当該アプリは、Microsoft Store など、既存のリリース チャネル経由で引き続きダウンロード可能です。 

維持モードになると、当該アプリは、重要なセキュリティ更新プログラムのみを受信するようになります。 当該アプリの更新プログラムや機能が追加でリリースされることはありません。 新機能を使用するには、デバイスを Windows 10 や Windows 10 Mobile に更新することをお勧めします。 

###  <a name="block-copy-and-paste-between-work-and-personal-profiles-in-android-for-work----1098994---"></a>Android for Work で仕事用プロファイルと個人プロファイルの間でのコピーおよび貼り付けを防ぐ <!-- 1098994 -->   
このリリースでは、仕事用アプリと個人用アプリとの間でコピーおよび貼り付けができないように、Android for Work の仕事用プロファイルを構成できます。 この新しい設定は、**[仕事用プロファイルの設定]** の **[Android for Work]** プラットフォームの **[デバイスの制限]** プロファイルにあります。

### <a name="new-behaviors-for-the-company-portal-app-for-android-with-work-profiles----1485783---"></a>仕事用プロファイルを使った Android 用ポータル サイト アプリの新しい動作 <!---1485783--->
仕事用プロファイルがある Android for Work デバイスを登録すると、仕事用プロファイル内のポータル サイト アプリによって、そのデバイス上での管理タスクが実行されます。 個人プロファイルで MAM 対応アプリを使っている場合を除き、Android 用ポータル サイト アプリを使用する機会がなくなります。 仕事用プロファイルのエクスペリエンスを向上させるために、Intune では仕事用プロファイルの登録が正常に完了した後、個人用ポータル サイト アプリが自動的に非表示になります。

Android 用ポータル サイト アプリは、[Play ストアでポータル サイト](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) を参照して **[Enable]\(有効化\)** をタップすると、個人プロファイルでいつでも有効にできます。

### <a name="intune-mam--outlook-for-android-add-ins-----1450688---"></a>Android 用 Intune MAM および Outlook のアドイン <!-- 1450688 -->
数週間以内に、Office チームによって Android 版 Outlook のアドインが発表されます。 このアドインの機能セットは、Windows、iOS、Web、および Mac 版の Outlook で既にリリース済みのものです。 アドインは Exchange を介して管理されるため、Exchange 管理者がアドインへのアクセスを無効にしていない限り、ユーザーは Outlook と管理対象外のアドイン アプリケーションとの間でデータとメッセージをコピーおよび共有できるようになります。 

アドインへのユーザーのアクセス許可を管理するには、Exchange 管理者と協力して、MAM データ保護ポリシーがアドインに必ず適用されるようにしてください。

#### <a name="how-does-this-affect-me"></a>ユーザーへの影響
Exchange ポリシーが、既にアドインのサイド ローディングやアドインのインストールを防ぐように設定されている場合は、これ以上読む必要はありません。 MAM ポリシーは、想定どおりに適用されます。 ただし、Android 版 Outlook 内での切り取り、コピー、貼り付け操作を制限するように MAM 内のポリシーを設定してあり、Exchange でアドイン ポリシーを設定していない場合は、既定ではユーザーが Outlook にアドインをインストールできるということを覚えておく必要があります。 これらのアドインでは、メッセージ本文、件名、その他のメッセージ プロパティにアクセスできます。 Exchange 管理者に [My Marketplace Apps]\(自分の Marketplace アプリ\) の役割と [My Custom Apps]\(自分のカスタム アプリ\) の役割を削除してもらうと、エンドユーザーがアドインをインストールできないようにすることができます。 詳しくは、その他の情報に関する以下の共有リンクをご覧ください。

Exchange の設定を変更すると、Windows 版、iOS 版、Web 版、Mac 版、モバイル版のすべての Outlook に適用されることに注意してください。 

#### <a name="what-do-i-need-to-do"></a>必要な作業
現在の Exchange ポリシーを確認します。 IT 部門とヘルプ デスクのスタッフに知らせます。 特定の質問や懸念事項をサポート チームに問い合わせます。 

### <a name="user-device-association-entity-collection-added-to-intune-data-warehouse-data-model----1187917---"></a>Intune データ ウェアハウスのデータ モデルに追加されたユーザー デバイス関連付けエンティティ コレクション <!-- 1187917 -->
ユーザーとデバイスのエンティティ コレクションを関連付けるユーザー デバイス関連付け情報を使って、レポートやデータの視覚エフェクトを作成できるようになります。 このデータ モデルは、OData エンドポイントを使うか、カスタム クライアントを開発すると、[Data Warehouse Intune]\(データ ウェアハウス Intune\) ページから取得した Power BI ファイル (PBIX) を使ってアクセスできます。


<!-- the following are present prior to 1709 -->

### <a name="actions-for-non-compliance----730266--"></a>コンプライアンス非対応に対するアクション <!--730266-->     
*コンプライアンス非対応に対するアクション*は、コンプライアンス非対応のデバイスに対してアクションを実行できるようにするコンプライアンス ポリシーの新しい機能です。 単一または複数のアクションを指定できます。また、実行する必要があるアクションの期間を指定することもできます。 たとえば、デバイスが非対応になった直後に電子メールで、その非対応デバイスのユーザーに通知することができます。あるいは、非対応デバイスに対して、条件付きアクセスで 3 日間の猶予期間後の企業リソースへのアクセスをブロックすることができます。

### <a name="new-report-that-lists-ios-devices-with-older-ios-versions------1352223---"></a>古い iOS バージョンの iOS デバイス一覧が記載された新しいレポート<!-- 1352223 -->
[**ソフトウェア更新プログラム**] ワークスペースから [**Out-of-date iOS Devices**]\(古い iOS デバイス\) レポートを利用できるようになります。 このレポートには、iOS の更新ポリシーが対象とする監視対象の iOS デバイスの一覧と利用可能な更新が表示されます。 デバイスごとに、デバイスが自動的に更新されない理由のステータスを確認できます。 

### <a name="new-settings-for-windows-10-device-restriction-profile"></a>Windows 10 デバイス制限プロファイルの新しい設定
<!--- 978575, 1308849, -->
Windows Defender SmartScreen カテゴリの Windows 10 デバイス制限プロファイルに新しい設定が追加されます。

Windows 10 デバイス制限のプロファイルの詳細については、「[Windows 10 以降のデバイスの制限設定]( device-restrictions-windows-10.md)」を参照してください。

### <a name="android-for-work-support-for-lookout----1087312---"></a>Lookout の Android for Work サポート <!-- 1087312 -->   
Lookout を備えた Intune コネクタでは、Lookout for Work アプリの使用時、Android for Work デバイスをサポートします。 コンテナーの内外に Lookout アプリを展開できるようになる予定です。

### <a name="intune-app-protection-and-citrix-mdx-development-tools----709185---"></a>Intune App Protection と Citrix MDX 開発ツール<!-- 709185 -->
Citrix XenMobile MDX と Microsoft Intune を組み合わせ、デバイスとアプリを管理することができます。 これにより、Citrix の mVPN テクノロジを使用し、Intune アプリの保護ポリシーでアプリを管理できるようになります。

Citrix の MDX mVPN テクノロジとの統合を可能にする iOS および Android 用の Intune アプリ ラッピング ツールと Intune アプリ SDK を含むコード リポジトリを見つけることができるはずです。

### <a name="zimperium---new-mobile-threat-defense-partner------954681---"></a>Zimperium - 新しい Mobile Threat Defense パートナー   <!-- 954681 -->
Microsoft Intune に統合された Mobile Threat Defense である Zimperium によって実行されるリスク評価に基づき、条件付きアクセスを利用し、モバイル デバイスから会社のリソースへのアクセスを制御できます。

#### <a name="how-integration-with-intune-works"></a>Intune との統合のしくみ
リスクは、Zimperium を実行するデバイスから収集される製品利用統計情報に基づいて評価されます。 Intune デバイス コンプライアンス ポリシーで有効にした Zimperium リスク評価に基づき、EMS 条件付きアクセスのポリシーを構成できます。Intune デバイス コンプライアンス ポリシーは、検出された脅威に基づき、非準拠デバイスから企業リソースへのアクセスを許可したり、拒否したりするために利用できます。

### <a name="new-azure-ad-conditional-access-policy-ui-link-from-intune-----1016201---"></a>Intune からリンクされる新しい Azure AD の条件付きアクセス ポリシーの UI  <!-- 1016201 -->
IT 管理者は、Azure AD のワークロードで新しい条件付きアクセス ポリシーの UI を使用してアプリ ベースの条件付きポリシーを設定できます。 Azure の Intune App Protection セクションにあるアプリに基づく条件付きアクセス ポリシーは当面そのまま残り、サイド バイ サイドで強制されます。 また、Intune ワークロードから Azure AD の新しい条件付きアクセス ポリシー UI への便利なリンクもあります。

### <a name="on-premises-exchange-connector-high-availability-support-----676614---"></a>オンプレミスの Exchange Connector の高可用性のサポート  <!-- 676614 -->   
オンプレミスの Exchange Connector に複数のクライアント アクセス サーバー (CAS) ロールを持たせることができます。 たとえば、メインの CAS に障害が発生した場合、他の CAS にフォールバックするクエリを Exchange Connector が受信するようにできます。 この機能により、サービスが中断されないことが保証されます。

### <a name="system-center-operations-manager-management-pack-for-exchange-connector----885457---"></a>Exchange Connector 用の System Center Operations Manager 管理パック <!-- 885457 -->   
Exchange Connector 用の System Center Operations Manager 管理パックが Exchange Connector のログ解析に利用できるようになります。 問題のトラブルシューティングを行う必要がある場合、この管理パックによって別の方法で Intune を監視できます。

### <a name="end-of-support-for-ios-80----1164477---"></a>iOS 8.0 のサポートの終了 <!---1164477--->
iOS 用の管理対象アプリとポータル サイト アプリから会社のリソースにアクセスするには、iOS 9.0 以降を使用している必要があります。 この 9 月までに更新されないデバイスは、ポータル サイトまたはそれらのアプリにアクセスできなくなります。  

### <a name="end-of-support-for-android-43-and-lower----1171127-1326920----"></a>Android 4.3 以前のサポートの終了<!---1171127, 1326920 --->
Android 用の管理対象アプリとポータル サイト アプリで会社のリソースにアクセスするには、Android 4.4 以降を使用している必要があります。 10 月の初めまでにデバイスを更新しないと、ポータル サイトまたはそれらのアプリにアクセスできなくなります。 12 月には、登録されているすべてのデバイスがインベントリから削除され、会社のリソースにアクセスできなくなります。 MDM を使わずにアプリの保護ポリシーを使用している場合、アプリは更新プログラムを受信できなくなり、時間の経過と共にエクスペリエンスの質が低下していきます。

### <a name="platform-support-reminder-windows-phone-81-mainstream-support-will-end-july-11-2017----1327781---"></a>プラットフォームのサポートのお知らせ: Windows Phone 8.1 メインストリーム サポートの 2017 年 7 月 11 日の終了 <!-- 1327781 -->  
2017 年 7 月 11 日をもって、Windows Phone 8.1 プラットフォームのメインストリーム サポートは終了します。 Windows 8.1 PC のサポートには影響ありません。

Intune サービスによって管理されている Windows Phone 8.1 デバイスへの直接的な影響はありません。 登録されているデバイスは引き続き機能し、すべてのポリシー、構成、およびアプリは引き続き正常に動作します。 Intune サービスの Windows Phone 8.1 プラットフォームおよび Windows Phone 8.1 ポータル サイト アプリを対象とする機能強化は行われません。

できるだけ早い機会に、対象となる Windows Phone 8.1 デバイスを Windows 10 Mobile にアップグレードすることをお勧めします。 





## <a name="intune-apps"></a>Intune アプリ

### <a name="search-improvements-to-the-company-portal-website---1331697--"></a>ポータル Web サイトの検索機能強化 <!--1331697-->
マイクロソフトはアプリの検索機能を強化しています。その最初が[ポータル Web サイト](https://portal.manage.microsoft.com)です。 名前フィールドや説明フィールドだけでなく、アプリ カテゴリでも検索できるようになりました。 結果は既定で、関連性の降順で並べ替えられます。 

iOS ユーザーもこの変更の影響を受けます。ポータル Web サイトは、iOS のポータル サイト アプリの一部としても利用されるためです。 Android と Windows のポータル サイト アプリも数か月後に同じように更新されます。 

マイクロソフトは関連性の追跡方法を微調整しています。ポータル Web サイトの一番下にある "フィードバック" リンクから調整具合をお知らせください。

### <a name="refresh-action-added-to-the-company-portal-app-for-windows-10---1132468--"></a>Windows 10 用ポータル サイト アプリに追加された更新アクション <!--1132468-->
Windows 10 用ポータル サイト アプリで、アプリ内のデータを更新するには、下に引いて更新するか、デスクトップでは F5 キーを押します。


### <a name="apps-that-are-available-with-or-without-enrollment-can-now-be-installed-without-being-prompted-for-enrollment----1334712---"></a>登録の有無にかかわらず利用可能なアプリについて、登録を求められずにインストールできるようになりました。 <!-- 1334712 -->
Android ポータル サイト アプリでの登録の有無にかかわらず利用可能な業務用アプリについて、登録を求められずにインストールできます。

### <a name="ios-company-portal-display-large-icons----1454593---"></a>iOS ポータル サイトでの大きいアイコンの表示 <!-- 1454593 -->
iOS ポータル サイトのアプリ タイルでのアイコンの表示方法に関する既知の問題は修正中です。 現在は、120 x 120 ピクセル以上のアプリ アイコンをアップロードすると、ポータル Web サイト (https://portal.manage.microsoft.com) 内と iOS ポータル サイトのアプリ ページ内で、アプリ タイルのフル サイズで表示されます。

### <a name="easier-to-understand-phrasing-for-the-company-portal-app-for-android------1396349---"></a>Android 用ポータル サイト アプリの文言をわかりやすいように変更 <!---1396349--->    
Android 用ポータル サイト アプリについて、エンドユーザーが登録しやすくなるよう、テキストを変更して登録プロセスを簡易化しました。 


<!-- the following are present prior to 1709 -->


### <a name="intune-managed-browser-support-for-ios-and-android----1374196---"></a>iOS および Android <!---1374196---> 用の Intune Managed Browser のサポート
2017 年 10 月の時点で、Android アプリで使用する Intune Managed Browser アプリは、Android 4.4 以降を実行しているデバイスのみをサポートします。 iOS の Intune Managed Browser アプリは、iOS 9.0 以降を実行しているデバイスのみをサポートします。 以前のバージョンの Android および iOS は、Managed Browser の使用を続けることができますが、新しいバージョンのアプリをインストールすることはできません。また、アプリのすべての機能にアクセスできるとは限りません。 サポートされるオペレーティング システム バージョンにこれらのデバイスを更新することをお勧めします。

### <a name="allow-end-users-to-access-the-company-portal-app-for-android-without-enrollment----1169910---"></a>エンドユーザーの Android 用のポータル サイト アプリへのアクセスを登録なしで許可する<!---1169910--->  
エンドユーザーは間もなく Android 用のポータル サイト アプリにアクセスするために、デバイスを登録しなくて済むようになります。 アプリの保護ポリシーを使用する組織のエンドユーザーが、ポータル サイト アプリを開いたときに、デバイスの登録を求めるプロンプトが表示されなくなります。 エンドユーザーはデバイスを登録することなく、ポータル サイトからアプリをインストールできるようにもなります。 

### <a name="improved-error-message-for-when-a-user-reaches-the-maximum-number-of-devices-allowed-to-enroll----1270370---"></a>ユーザーが登録できるデバイスの最大数に達したときのエラー メッセージの向上<!-- 1270370 -->
エンドユーザーに一般的なエラー メッセージでなく、「IT 管理者が許可している数よりも多くのデバイスが登録されています。登録したデバイスを削除するか、IT 管理者に支援を求めてください。」という分かりやすい、実践的なエラー メッセージが表示されるようになりました。

### <a name="inform-end-users-what-device-information-can-be-seen-for-ios---739894--"></a>確認可能な iOS デバイス情報のエンドユーザーへの通知<!--739894-->
iOS 用ポータル サイト アプリの [デバイスの詳細] 画面に **[Ownership Type]\(所有権の種類\)** が追加されます。 これにより、ユーザーは、Intune エンドユーザー ドキュメントのこのページから直接プライバシーの詳細を確認できます。この情報は、[バージョン情報] 画面でも確認できます。

### <a name="apps-details-pages-display-new-information-for-android-devices---1287476--"></a>[アプリの詳細] ページでの Android デバイスの新しい情報の表示<!--1287476-->
Android 用のポータル サイト アプリのアプリの詳細ページには、IT 管理者がそのアプリに対して定義したアプリのカテゴリが表示されます。

### <a name="intune-mobile-application-management-mam-dialog-boxes-now-have-a-modern-interface----1199015---"></a>新しくなった Intune モバイル アプリケーション管理 (MAM) ダイアログ ボックスのインターフェイス<!-- 1199015 -->
Intune モバイル アプリケーション管理 (MAM) ダイアログ ボックスの外観が更新されました。 このダイアログ ボックスは、以前と同じように使用できます。

最新の Android デバイスの Intune のエラーまたは通知ダイアログの外観と雰囲気が更新されています。



## <a name="notices"></a>通知
### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple の要求による Application Transport Security 対応のための更新<!--748318-->   
Apple は、2017 年春より Application Transport Security (ATS) の特定の要件を適用すると発表しました。 ATS では、HTTPS 経由で行われるアプリ通信すべてに、より厳格なセキュリティ保護が適用されます。 この変更により、iOS ポータル サイト アプリを使用している Intune ユーザーが影響を受けます。 詳細については、[Intune サポートのブログ](https://aka.ms/compportalats)をご覧ください。

### <a name="plan-for-change-intune-is-changing-the-intune-partner-portal-experience----1050016---"></a>変更の計画: Intune で Intune パートナー ポータル エクスペリエンスが変更されます<!-- 1050016 -->
2017 年 5 月中旬のサービス更新で、Intune パートナーのページが manage.microsoft.com から削除されます。  

お客様がパートナーの管理者である場合は、Intune パートナーのページで顧客に代わって閲覧したり、操作したりすることができなくなります。代わりに、マイクロソフトの他の 2 つのパートナー ポータルのいずれかでサインインする必要があります。

[Microsoft パートナー センター](https://partnercenter.microsoft.com/)と [Microsoft Office 365 パートナー管理センター](https://portal.office.com/)の両方で、管理している顧客アカウントにサインインできます。 パートナーとして前進するために、これらのサイトのいずれかを使用して顧客の管理を行いましょう。



### <a name="see-also"></a>関連項目
最近の開発状況について詳しくは、「[Microsoft Intune の新機能](whats-new.md)」をご覧ください。
