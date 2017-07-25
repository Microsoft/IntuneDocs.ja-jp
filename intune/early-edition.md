---
title: "初期エディション"
description: 
keywords: 
author: brenduns
ms.author: brenduns
manager: angrobe
ms.date: 07/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: b8d281e3af2458bd5ab343dfa5123b31075d28ed
ms.sourcegitcommit: 2a6ad3c233d15a9fb441362105f64b2bdd550c34
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/13/2017
---
# <a name="the-early-edition-for-microsoft-intune---july-2017"></a>Microsoft Intune の初期エディション - 2017 年 7 月

**初期エディション**では、Microsoft Intune の今後のリリースで予定されている新機能の一覧を提供しています。 ここに記載されている情報は、ごく限られた範囲について開示されたものであり、また今後変更される可能性があります。 社外ではこの情報を共有しないでください。 ここに挙げられている機能は、発売日に間に合わない可能性があり、その場合は将来のリリースを待たなければなりません。 正式なリリースに向けてパイロット (フライト) テスト中の機能もあります。 ご不明な点や懸念される事項がある場合は、Microsoft 製品グループにお問い合わせください。

このページは定期的に更新されます。 適宜確認してください。

> [!Note]
>Intune に関して以下の機能が現在開発されています。 最新のハイブリッド機能の詳細については、[ハイブリッド環境の新機能に関するページ](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)を参照してください。

<!--

## What's coming to Intune on the Azure portal  
## What's coming to Intune apps
## Notices

-->



## <a name="intune-on-the-azure-portal"></a>Azure Portal での Intune

### <a name="easier-installation-of-office-365-apps-----1121362----"></a>Office 365 アプリをより簡単にインストールする<!--- 1121362 --->
新しいタイプの **Office 365 ProPlus** アプリでは、最新バージョンの Windows 10 を実行する管理対象のデバイスに、Office 365 ProPlus アプリを簡単に割り当てることができます。 また、ライセンスを所有している場合、Microsoft Project や Microsoft Visio をインストールすることができます。 必要なアプリはバンドルされ、Intune コンソールのアプリ一覧に 1 つのアプリとして表示されます。


### <a name="new-device-action-to-force-devices-to-sync-with-intune----711369---"></a>デバイスを Intune と強制同期する新しいデバイス アクション<!-- 711369 -->    
選択したデバイスの Intune への即座のチェックインを強制する新しいデバイス アクションが追加されます。 チェックインしたデバイスには、それに対して保留中のアクションまたはポリシーが即座に割り当てられます。  このアクションにより、次のスケジュールされたチェックインを待つことなく、割り当てられたポリシーの検証およびトラブルシューティングを即座に実行できるようになります。

### <a name="actions-for-non-compliance----730266--"></a>コンプライアンス非対応に対するアクション <!--730266-->     
*コンプライアンス非対応に対するアクション*は、コンプライアンス非対応のデバイスに対してアクションを実行できるようにするコンプライアンス ポリシーの新しい機能です。 単一または複数のアクションを指定できます。また、実行する必要があるアクションの期間を指定することもできます。 たとえば、デバイスが非対応になった直後に電子メールで、その非対応デバイスのユーザーに通知することができます。あるいは、非対応デバイスに対して、条件付きアクセスで 3 日間の猶予期間後の企業リソースへのアクセスをブロックすることができます。

### <a name="new-app-configuration-settings-for-the-intune-managed-browser-----682951----"></a>Intune Managed Browser の新しいアプリ構成設定 <!--- 682951 --->
Intune Managed Browser アプリに新しい構成を追加する予定です。 アプリ構成ポリシーを使用して、ブラウザーの既定のホーム ページとブックマークを構成できるようになります。

### <a name="restrict-android-and-ios-device-enrollment-restriction-by-os-version------1333256--1245463----"></a>Android および iOS デバイスの OS のバージョンによる登録制限 <!--- 1333256,  1245463 --->  
オペレーティング システムのバージョン番号によって iOS と Android の登録を制限する機能が追加されました。 [**Intune**] > [**登録の制限**] > [**デバイスの種類の制限**] > [**既定**] > [**プラットフォームの制限**] で、IT 管理者は、オペレーティング システムのバージョン番号の最小値から最大値をプラットフォーム構成して、登録を制限できるようになりました。 Android オペレーティング システムのバージョンは、Major.Minor.Build.Rev の形式で指定する必要があります (Build、Rev は任意)。 iOS オペレーティング システムのバージョンは、Major.Minor.Build の形式で指定する必要があります (Build は任意)。

>[!NOTE]
>この設定は、Apple Device Enrollment Program や Apple School Manager や Apple Configurator など、Apple の登録プログラムを介した登録は制限しません。

### <a name="restrict-android-ios-and-macos-device-personally-owned-device-enrollment------1333272--1333275-1245709----"></a>個人所有の Android、iOS、および macOS デバイスの登録を制限する<!--- 1333272,  1333275, 1245709 --->
Intune では、デバイスのシリアル番号を使用して、個人所有の iOS、Android、および macOS デバイスの登録を制限できるようになりました。 一部のデバイスは、シリアル番号を報告しません。 詳細については、デバイスの製造元にお問い合わせください。 Intune にデバイスのシリアル番号をアップロードし、それを企業所有として事前に宣言できます。 登録の制限を使用すると、個人所有のデバイス (BYOD) をブロックして、企業所有のデバイスのみの登録を許可することができます。

Intune ポータルにシリアル番号をインポートするには、[**デバイスの登録**] > [**Corporate device identifiers**]\(企業のデバイス識別子\) に進み、[**追加**] をクリックし、(ヘッダーはない、シリアル番号と IMEI 番号など詳細情報がある 2 つの列の) CSV ファイルをアップロードします。  個人所有のデバイスを制限するには、[**デバイスの登録**] > [**登録制限**] に移動します。 [**デバイスの種類の制限**] から [**既定**] を選択し、[**プラットフォーム構成**] を選択します。 個人所有の iOS、Android、および macOS デバイスを [**許可**] または [**ブロック**] できます。 

### <a name="force-supervised-ios-devices-to-automatically-install-the-latest-available-software-update----777100---"></a>監督下の iOS デバイスに利用可能な最新のソフトウェア更新プログラムを強制的に自動インストールする<!-- 777100 -->   
ソフトウェアの更新プログラム ワークスペースに用意された新しいポリシーを使用すると、監督下の iOS デバイスに利用可能な最新のソフトウェア更新プログラムを強制的に自動インストールできます。 また旧バージョンの iOS デバイスが列挙された新しいレポートを参照することもできます。そこには、デバイスが最新でない理由の概要が記載されています。

### <a name="new-settings-to-allow-and-block-apps-on-samsung-knox-standard-devices-----822899--1305423--"></a>Samsung KNOX Standard デバイス用のアプリを許可またはブロックするための新しい設定<!-- 822899,  1305423-->   
次のアプリ一覧を指定できる[デバイスの制限設定](device-restrictions-android.md)が新規に追加されます。
  - ユーザーがインストールを許可されているアプリ
  - ユーザーが実行をブロックされているアプリ
  - デバイスのユーザーに非表示となっているアプリ  

アプリは、URL、パッケージ名、管理対象のアプリ一覧から指定できます。

### <a name="android-for-work-support-for-lookout----1087312---"></a>Lookout の Android for Work サポート <!-- 1087312 -->   
Lookout を備えた Intune コネクタでは、Lookout for Work アプリの使用時、Android for Work デバイスをサポートします。 コンテナーの内外に Lookout アプリを展開できるようになる予定です。


### <a name="check-point-sandblast-mobile---new-mobile-threat-defense-partner-----954651--and--1172027----"></a>チェック ポイント SandBlast Mobile - 新しい Mobile Threat Defense パートナー<!-- 954651  and  1172027 ? -->  
Microsoft Intune に統合された Mobile Threat Defense ソリューションであるチェック ポイントの SandBlast Mobile によって実行されるリスク評価に基づき、条件付きアクセスを利用し、モバイル デバイスから会社のリソースへのアクセスを制御できます。

#### <a name="how-integration-with-intune-works"></a>Intune との統合のしくみ
リスクは、チェック ポイントの SandBlast Mobile を実行するデバイスから収集される製品利用統計情報に基づいて評価されます。 Intune のデバイス コンプライアンス ポリシーにより有効になったチェック ポイントの SandBlast Mobile のリスク評価に基づいて、EMS の条件付きアクセス ポリシーを構成できます。 検出された脅威に基づき、非準拠デバイスの企業リソースへのアクセスを許可またはブロックすることができます。

### <a name="zimperium---new-mobile-threat-defense-partner------954681---"></a>Zimperium - 新しい Mobile Threat Defense パートナー   <!-- 954681 -->
Microsoft Intune に統合された Mobile Threat Defense である Zimperium によって実行されるリスク評価に基づき、条件付きアクセスを利用し、モバイル デバイスから会社のリソースへのアクセスを制御できます。

#### <a name="how-integration-with-intune-works"></a>Intune との統合のしくみ
リスクは、Zimperium を実行するデバイスから収集される製品利用統計情報に基づいて評価されます。 Intune デバイス コンプライアンス ポリシーで有効にした Zimperium リスク評価に基づき、EMS 条件付きアクセスのポリシーを構成できます。Intune デバイス コンプライアンス ポリシーは、検出された脅威に基づき、非準拠デバイスから企業リソースへのアクセスを許可したり、拒否したりするために利用できます。

### <a name="on-premises-exchange-connector-high-availability-support-----676614---"></a>オンプレミスの Exchange Connector の高可用性のサポート  <!-- 676614 -->   
オンプレミスの Exchange Connector に複数のクライアント アクセス サーバー (CAS) ロールを持たせることができます。 たとえば、メインの CAS に障害が発生した場合、他の CAS にフォールバックするクエリを Exchange Connector が受信するようにできます。 この機能により、サービスが中断されないことが保証されます。

### <a name="system-center-operations-manager-management-pack-for-exchange-connector----885457---"></a>Exchange Connector 用の System Center Operations Manager 管理パック <!-- 885457 -->   
Exchange Connector 用の System Center Operations Manager 管理パックが Exchange Connector のログ解析に利用できるようになります。 問題のトラブルシューティングを行う必要がある場合、この機能によって別の方法で Intune を監視できます。

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

### <a name="improved-sign-in-experience-across-company-portal-apps-for-all-platforms---user-story-1132123--"></a>すべてのプラットフォームでのポータル サイト アプリのサインイン操作の改善<!--User Story 1132123-->    
Android、iOS、Windows での Intune ポータル サイト アプリのサインイン エクスペリエンス向上のために、今後数か月間に予定されている変更についてお知らせします。 Azure AD でこの変更が行われ次第、自動的にすべてのプラットフォームでポータル サイト アプリのユーザー エクスペリエンスが一新される予定です。 また、自動生成される一時使用コードを使用して、別のデバイスからポータル サイトにサインインできるようになりました。 これは、資格情報を使用せずにサインインする必要がある場合には特に便利です。

以前のサインイン エクスペリエンス、資格情報を使用した新たなエクスペリエンス、別のデバイスからのエクスペリエンスのスクリーンショットを [アプリ UI の新機能](whats-new-app-ui.md)に関するページで確認できます。

### <a name="light-and-dark-modes-available-for-the-company-portal-app-for-windows-10----676547---"></a>Windows 10 のポータル サイト アプリで利用可能なライト モードとダーク モード<!---676547--->
エンドユーザーは Windows 10 のポータル サイト アプリのカラー モードをカスタマイズできるようになります。 ユーザーはポータル サイト アプリの [設定] セクションでこの変更をできるようになります。 変更はユーザーがアプリを再起動した後に反映されます。 Windows 10 のバージョン 1607 以降では、アプリの既定のモードはシステム設定になります。 Windows 10 のバージョン 1511 以降を実行するデスクトップでは、アプリの既定のモードはライト モードです。

### <a name="enable-end-users-to-tag-their-device-group-in-the-company-portal-app-for-windows-10----807046--"></a>エンドユーザーは Windows 10 用のポータル サイト アプリでデバイス グループをタグ付けできる<!---807046-->    
エンドユーザーは Windows 10 のポータル サイト アプリから直接タグ付けすることにより、デバイスの所属グループを選択することができます。

### <a name="allow-end-users-to-access-the-company-portal-app-for-android-without-enrollment----1169910---"></a>エンドユーザーの Android 用のポータル サイト アプリへのアクセスを登録なしで許可する<!---1169910--->  
エンドユーザーは間もなく Android 用のポータル サイト アプリにアクセスするために、デバイスを登録しなくて済むようになります。 アプリの保護ポリシーを使用する組織のエンドユーザーが、ポータル サイト アプリを開いたときに、デバイスの登録を求めるプロンプトが表示されなくなります。 エンドユーザーはデバイスを登録することなく、ポータル サイトからアプリをインストールできるようにもなります。 

### <a name="users-who-are-signed-in-to-exchange-can-automatically-access-the-company-portal-website-on-windows-10-devices---1323204--"></a>Exchange にサインインしているユーザーは、Windows 10 デバイスからポータル サイトの Web サイトに自動的にアクセスできる<!--1323204-->  
条件付きアクセスの検疫メールを受信し、メール内のリンクをクリックした、既に Exchange で認証されている Windows 10 ユーザーは、ブラウザーで再認証を行う必要なく、会社アクセスのセットアップを開始できるようになります。


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
