---
title: "初期エディション"
description: 
keywords: 
author: brenduns
ms.author: brenduns
manager: angrobe
ms.date: 8/3/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 5861c999752bfef05b8a33161d0bf75a6d4daf59
ms.sourcegitcommit: 18cdbdc226f64368de892a8c5cff157c37986c57
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2017
---
# <a name="the-early-edition-for-microsoft-intune---august-2017"></a>Microsoft Intune の初期エディション - 2017 年 8 月

**初期エディション**では、Microsoft Intune の今後のリリースで予定されている新機能の一覧を提供しています。 ここに記載されている情報は、限られた範囲について開示されたものであり、また今後変更される可能性があります。 社外ではこの情報を共有しないでください。 ここに挙げられている機能は、発売日に間に合わない可能性があり、その場合は将来のリリースを待たなければなりません。 正式なリリースに向けてパイロット (フライト) テスト中の機能もあります。 ご不明な点や懸念される事項がある場合は、Microsoft 製品グループにお問い合わせください。

このページは定期的に更新されます。 適宜確認してください。

> [!Note]
>Intune に関して以下の機能が現在開発されています。 最新のハイブリッド機能の詳細については、[ハイブリッド環境の新機能に関するページ](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)を参照してください。

<!--

## What's coming to Intune on the Azure portal  
## What's coming to Intune apps
## Notices

-->



## <a name="intune-on-the-azure-portal"></a>Azure Portal での Intune




### <a name="new-device-action-to-force-devices-to-sync-with-intune----711369---"></a>デバイスを Intune と強制同期する新しいデバイス アクション<!-- 711369 -->    
選択したデバイスの Intune への即座のチェックインを強制する新しいデバイス アクションが追加されます。 チェックインしたデバイスには、それに対して保留中のアクションまたはポリシーが即座に割り当てられます。  このアクションにより、次のスケジュールされたチェックインを待つことなく、割り当てられたポリシーの検証およびトラブルシューティングを即座に実行できるようになります。

### <a name="actions-for-non-compliance----730266--"></a>コンプライアンス非対応に対するアクション <!--730266-->     
*コンプライアンス非対応に対するアクション*は、コンプライアンス非対応のデバイスに対してアクションを実行できるようにするコンプライアンス ポリシーの新しい機能です。 単一または複数のアクションを指定できます。また、実行する必要があるアクションの期間を指定することもできます。 たとえば、デバイスが非対応になった直後に電子メールで、その非対応デバイスのユーザーに通知することができます。あるいは、非対応デバイスに対して、条件付きアクセスで 3 日間の猶予期間後の企業リソースへのアクセスをブロックすることができます。


### <a name="restrict-android-and-ios-device-enrollment-restriction-by-os-version------1333256--1245463----"></a>Android および iOS デバイスの OS のバージョンによる登録制限 <!--- 1333256,  1245463 --->  
オペレーティング システムのバージョン番号によって iOS と Android の登録を制限する機能が追加されました。 [**Intune**] > [**登録の制限**] > [**デバイスの種類の制限**] > [**既定**] > [**プラットフォームの制限**] で、IT 管理者は、オペレーティング システムのバージョン番号の最小値から最大値をプラットフォーム構成して、登録を制限できるようになりました。 Android オペレーティング システムのバージョンは、Major.Minor.Build.Rev の形式で指定する必要があります (Build、Rev は任意)。 iOS オペレーティング システムのバージョンは、Major.Minor.Build の形式で指定する必要があります (Build は任意)。

>[!NOTE]
>この設定は、Apple Device Enrollment Program や Apple School Manager や Apple Configurator など、Apple の登録プログラムを介した登録は制限しません。

### <a name="restrict-android-ios-and-macos-device-personally-owned-device-enrollment------1333272--1333275-1245709----"></a>個人所有の Android、iOS、および macOS デバイスの登録を制限する<!--- 1333272,  1333275, 1245709 --->
Intune では、デバイスのシリアル番号を使用して、個人所有の iOS、Android、および macOS デバイスの登録を制限できるようになりました。 一部のデバイスは、シリアル番号を報告しません。 詳細については、デバイスの製造元にお問い合わせください。 Intune にデバイスのシリアル番号をアップロードし、それを企業所有として事前に宣言できます。 登録の制限を使用すると、個人所有のデバイス (BYOD) をブロックして、企業所有のデバイスのみの登録を許可することができます。

Intune ポータルにシリアル番号をインポートするには、[**デバイスの登録**] > [**Corporate device identifiers**]\(企業のデバイス識別子\) に進み、[**追加**] をクリックし、CSV ファイルをアップロードします。 このファイルには、ヘッダーを含めず、シリアル番号と IMEI 番号などの詳細のために列を 2 つ用意する必要があります。  個人所有のデバイスを制限するには、[**デバイスの登録**] > [**登録制限**] に移動します。 [**デバイスの種類の制限**] から [**既定**] を選択し、[**プラットフォーム構成**] を選択します。 個人所有の iOS、Android、および macOS デバイスを [**許可**] または [**ブロック**] できます。 

### <a name="force-supervised-ios-devices-to-automatically-install-the-latest-available-software-update----777100---"></a>監督下の iOS デバイスに利用可能な最新のソフトウェア更新プログラムを強制的に自動インストールする<!-- 777100 -->   
ソフトウェアの更新プログラム ワークスペースに用意された新しいポリシーを使用すると、監督下の iOS デバイスに利用可能な最新のソフトウェア更新プログラムを強制的に自動インストールできます。 また旧バージョンの iOS デバイスが列挙された新しいレポートを参照することもできます。そこには、デバイスが最新でない理由の概要が記載されています。

### <a name="new-report-that-lists-ios-devices-with-older-ios-versions------1352223---"></a>古い iOS バージョンの iOS デバイス一覧が記載された新しいレポート<!-- 1352223 -->
[**ソフトウェア更新プログラム**] ワークスペースから [**Out-of-date iOS Devices**]\(古い iOS デバイス\) レポートを利用できるようになります。 このレポートには、iOS の更新ポリシーが対象とする監視対象の iOS デバイスの一覧と利用可能な更新が表示されます。 デバイスごとに、デバイスが自動的に更新されない理由のステータスを確認できます。 

### <a name="new-settings-to-allow-and-block-apps-on-samsung-knox-standard-devices-----822899--1305423--"></a>Samsung KNOX Standard デバイス用のアプリを許可またはブロックするための新しい設定<!-- 822899,  1305423-->   
次のアプリ一覧を指定できる[デバイスの制限設定](device-restrictions-android.md)が新規に追加されます。
  - ユーザーがインストールを許可されているアプリ
  - ユーザーが実行をブロックされているアプリ
  - デバイスのユーザーに非表示となっているアプリ  

アプリは、URL、パッケージ名、管理対象のアプリ一覧から指定できます。

### <a name="new-settings-for-windows-10-device-restriction-profile"></a>Windows 10 デバイス制限プロファイルの新しい設定
<!--- 978575, 1308849, 1308850 -->
Windows Defender SmartScreen カテゴリの Windows 10 デバイス制限プロファイルに新しい設定が追加されます。

Windows 10 デバイス制限のプロファイルの詳細については、「[Windows 10 以降のデバイスの制限設定]( device-restrictions-windows-10.md)」を参照してください。

### <a name="new-device-restriction-settings-for-windows-10------1063965---"></a>Windows 10 の新しいデバイスの制限設定   <!-- 1063965 -->
次のカテゴリに [Windows 10 デバイス制限プロファイル](/intune/device-restrictions-windows-10)の新しい設定が追加されます。
- Windows Defender SmartScreen
- アプリ ストア


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

### <a name="conditional-access-support-for-mac-devices-----720172---"></a>Mac デバイスの条件付きアクセスのサポート<!-- 720172 -->   
Mac デバイスを Intune に登録し、そのデバイス コンプライアンス ポリシーに準拠することを求める条件付きアクセス ポリシーを間もなく設定できるようになります。 たとえば、ユーザーは macOS 用の Intune ポータル サイト アプリをダウンロードして、Mac デバイスを Intune に登録します。 Intune は、暗証番号 (PIN)、暗号化、OS バージョン、およびシステムの整合性などの要件にその Mac デバイスが準拠しているかどうかを評価します。

### <a name="end-of-support-for-ios-80----1164477---"></a>iOS 8.0 のサポートの終了 <!---1164477--->
iOS 用の管理対象アプリとポータル サイト アプリから会社のリソースにアクセスするには、iOS 9.0 以降を使用している必要があります。 この 9 月までに更新されないデバイスは、ポータル サイトまたはそれらのアプリにアクセスできなくなります。 12 月には、電子メールを含む、会社のリソースにすべてアクセスできなくなります。 

### <a name="end-of-support-for-android-43-and-lower----1171127-1326920----"></a>Android 4.3 以前のサポートの終了<!---1171127, 1326920 --->
Android 用の管理対象アプリとポータル サイト アプリで会社のリソースにアクセスするには、Android 4.4 以降を使用している必要があります。 10 月の初めまでにデバイスを更新しないと、ポータル サイトまたはそれらのアプリにアクセスできなくなります。 12 月には、登録されているすべてのデバイスがインベントリから削除され、会社のリソースにアクセスできなくなります。 MDM を使わずにアプリの保護ポリシーを使用している場合、アプリは更新プログラムを受信できなくなり、時間の経過と共にエクスペリエンスの質が低下していきます。


### <a name="platform-support-reminder-windows-phone-81-mainstream-support-will-end-july-11-2017----1327781---"></a>プラットフォームのサポートのお知らせ: Windows Phone 8.1 メインストリーム サポートの 2017 年 7 月 11 日の終了 <!-- 1327781 -->  
2017 年 7 月 11 日をもって、Windows Phone 8.1 プラットフォームのメインストリーム サポートは終了します。 Windows 8.1 PC のサポートには影響ありません。

Intune サービスによって管理されている Windows Phone 8.1 デバイスへの直接的な影響はありません。 登録されているデバイスは引き続き機能し、すべてのポリシー、構成、およびアプリは引き続き正常に動作します。 Intune サービスの Windows Phone 8.1 プラットフォームおよび Windows Phone 8.1 ポータル サイト アプリを対象とする機能強化は行われません。

できるだけ早い機会に、対象となる Windows Phone 8.1 デバイスを Windows 10 Mobile にアップグレードすることをお勧めします。 




## <a name="intune-apps"></a>Intune アプリ

### <a name="light-and-dark-modes-available-for-the-company-portal-app-for-windows-10----676547---"></a>Windows 10 のポータル サイト アプリで利用可能なライト モードとダーク モード<!---676547--->
エンドユーザーは Windows 10 のポータル サイト アプリのカラー モードをカスタマイズできるようになります。 ユーザーはポータル サイト アプリの [設定] セクションでこの変更をできるようになります。 変更はユーザーがアプリを再起動した後に反映されます。 Windows 10 のバージョン 1607 以降では、アプリの既定のモードはシステム設定になります。 Windows 10 のバージョン 1511 以降を実行するデスクトップでは、アプリの既定のモードはライト モードです。

### <a name="allow-end-users-to-access-the-company-portal-app-for-android-without-enrollment----1169910---"></a>エンドユーザーの Android 用のポータル サイト アプリへのアクセスを登録なしで許可する<!---1169910--->  
エンドユーザーは間もなく Android 用のポータル サイト アプリにアクセスするために、デバイスを登録しなくて済むようになります。 アプリの保護ポリシーを使用する組織のエンドユーザーが、ポータル サイト アプリを開いたときに、デバイスの登録を求めるプロンプトが表示されなくなります。 エンドユーザーはデバイスを登録することなく、ポータル サイトからアプリをインストールできるようにもなります。 

### <a name="improved-error-message-for-when-a-user-reaches-the-maximum-number-of-devices-allowed-to-enroll----1270370---"></a>ユーザーが登録できるデバイスの最大数に達したときのエラー メッセージの向上<!-- 1270370 -->
エンドユーザーに一般的なエラー メッセージでなく、「IT 管理者が許可している数よりも多くのデバイスが登録されています。 登録したデバイスを削除するか、IT 管理者に支援を求めてください。」という分かりやすい、実践的なエラー メッセージが表示されるようになりました。

### <a name="new-signed-in-experience-for-android-company-portal-users-and-app-protection-policy-users----621669---"></a>Android ポータル サイト ユーザーおよびアプリ保護ポリシー ユーザーに対する新しいサインイン エクスペリエンス<!-- 621669 -->
エンドユーザーは、Android デバイスを登録することなく、Android ポータル サイトを使用して、アプリの参照、デバイスの管理および IT 連絡先情報を参照できます。 また、エンドユーザーが既に Intune アプリ保護ポリシーによって保護されているアプリを使用しているときに、Android ポータル サイトを起動した場合、エンドユーザーに、デバイスの登録をするプロンプトが表示されなくなりました。 

### <a name="inform-end-users-what-device-information-can-be-seen-for-ios---739894--"></a>確認可能な iOS デバイス情報のエンドユーザーへの通知<!--739894-->
iOS 用ポータル サイト アプリの [デバイスの詳細] 画面に **[Ownership Type]\(所有権の種類\)** が追加されます。 これにより、ユーザーは、Intune エンドユーザー ドキュメントのこのページから直接プライバシーの詳細を確認できます。 この情報は、[バージョン情報] 画面でも確認できます。

### <a name="apps-details-pages-display-new-information-for-android-devices---1287476--"></a>[アプリの詳細] ページでの Android デバイスの新しい情報の表示<!--1287476-->
Android 用のポータル サイト アプリのアプリの詳細ページには、IT 管理者がそのアプリに対して定義したアプリのカテゴリが表示されます。

### <a name="intune-mobile-application-management-mam-dialog-boxes-now-have-a-modern-interface----1199015---"></a>新しくなった Intune モバイル アプリケーション管理 (MAM) ダイアログ ボックスのインターフェイス<!-- 1199015 -->
Intune モバイル アプリケーション管理 (MAM) ダイアログ ボックスの外観が更新されました。 このダイアログ ボックスは、以前と同じように使用できます。

最新の Android デバイスの Intune のエラーまたは通知ダイアログの外観と雰囲気が更新されています。

### <a name="new-setting-in-the-android-company-portal-app-to-toggle-battery-optimization---1405990--"></a>Android ポータル サイト アプリのバッテリの最適化を切り替える新しい設定<!--1405990-->
Android ポータル サイト アプリの [**設定**] ページには、ポータル サイトと Microsoft Authenticator アプリのバッテリ最適化をユーザーが簡単にオフにできる新しい設定があります。 この設定で表示されるアプリ名は、どのアプリが職場アカウントを管理しているかによって異なります。 電子メールとデータを同期する職場アプリのパフォーマンスの向上には、バッテリの最適化をオフにすることをお勧めします。 




## <a name="notices"></a>通知

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple の要求による Application Transport Security 対応のための更新<!--748318-->   
Apple は、2017 年春より Application Transport Security (ATS) の特定の要件を適用すると発表しました。 ATS では、HTTPS 経由で行われるアプリ通信すべてに、より厳格なセキュリティ保護が適用されます。 この変更により、iOS ポータル サイト アプリを使用している Intune ユーザーが影響を受けます。 詳細については、[Intune サポートのブログ](https://aka.ms/compportalats)をご覧ください。

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Apple 登録シナリオへの直接アクセス <!--951869-->   
Intune では、2017 年 1 月以降に作成された Intune アカウントについて、Azure プレビュー ポータルの Enroll Devices ワークロードを使用して、Apple 登録シナリオに直接アクセスできるようになりました。 これまでは、Apple 登録プレビューはクラシックの Intune ポータルのリンクからのみアクセスが可能でした。 2017 年 1 月より前に作成された Intune アカウントの場合は、これらの機能が Azure で利用可能になるまでの間、1 回限りの移行が必要です。 移行スケジュールはまだ発表されていませんが、詳細はできる限り早く発表します。 既存のアカウントでプレビューにアクセスできない場合は、試用アカウントを作成して、新しいエクスペリエンスをテストすることを強くお勧めします。

### <a name="plan-for-change-intune-is-changing-the-intune-partner-portal-experience----1050016---"></a>変更の計画: Intune で Intune パートナー ポータル エクスペリエンスが変更されます<!-- 1050016 -->
2017 年 5 月中旬のサービス更新で、Intune パートナーのページが manage.microsoft.com から削除されます。  

お客様がパートナーの管理者である場合は、Intune パートナーのページで顧客に代わって閲覧したり、操作したりすることができなくなります。代わりに、マイクロソフトの他の 2 つのパートナー ポータルのいずれかでサインインする必要があります。

[Microsoft パートナー センター](https://partnercenter.microsoft.com/)と [Microsoft Office 365 パートナー管理センター](https://portal.office.com/)の両方で、管理している顧客アカウントにサインインできます。 パートナーとして前進するために、これらのサイトのいずれかを使用して顧客の管理を行いましょう。



### <a name="see-also"></a>関連項目
最近の開発状況について詳しくは、「[Microsoft Intune の新機能](whats-new.md)」をご覧ください。
