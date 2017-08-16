---
title: "Microsoft Intune の新機能"
titleSuffix: Intune on Azure
description: "Intune Azure Portal の新機能を確認する"
keywords: 
author: brenduns
ms.author: brenduns
manager: angrobe
ms.date: 08/10/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f915c805b20e88c661ad52e280a31054bbebce02
ms.sourcegitcommit: 2ed8d1c39d4b3e3282111f1d758afb3a50f19f8f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/10/2017
---
# <a name="whats-new-in-microsoft-intune"></a>Microsoft Intune の新機能

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

週ごとにまとめた、Microsoft Intune の新機能をご覧ください。 [今後の変更](#whats-coming)、サービスに関する[重要なお知らせ](#notices)、[過去のリリース](whats-new-archive.md)に関する情報も確認できます。

> [!Note]
> これらの機能の多くは、最終的に Configuration Manager とのハイブリッド環境でサポートされるようになります。 最新のハイブリッド機能の詳細については、[ハイブリッド環境の新機能に関するページ](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)を参照してください。


<!-- Common categories:  
  ### Role-based access control
  ### Device enrollment
  ### Device management
  ### App management
  ### Device configuration
  ### Intune apps
-->   

## <a name="week-of-july-31-2017"></a>2017 年 7 月 31 日の週

### <a name="device-enrollment"></a>デバイスの登録  

#### <a name="restrict-android-and-ios-device-enrollment-restriction-by-os-version------1333256--1245463----"></a>Android および iOS デバイスの OS のバージョンによる登録制限 <!--- 1333256,  1245463 --->
オペレーティング システムのバージョン番号によって iOS と Android の登録を制限する機能が追加されました。 **[デバイスの種類の制限]** で、IT 管理者は、プラットフォーム構成を設定して、オペレーティング システムのバージョン番号の最小値から最大値までの間に登録を制限できるようになりました。 Android オペレーティング システムのバージョンは、Major.Minor.Build.Rev の形式で指定する必要があります (Minor、Build、Rev は任意)。 iOS のバージョンは、Major.Minor.Build の形式で指定する必要があります (Minor と Build は任意)。 [デバイス登録の制限](enrollment-restrictions-set.md)の詳細については、こちらを参照してください。

>[!NOTE]
>Apple の登録プログラムまたは Apple Configurator では、登録は制限されません。

#### <a name="restrict-android-ios-and-macos-device-personally-owned-device-enrollment------1333272--1333275-1245709----"></a>個人所有の Android、iOS、および macOS デバイスの登録を制限する<!--- 1333272,  1333275, 1245709 --->
Intune では、会社デバイスの IMEI 番号のホワイトリストを作成して、個人用デバイスの登録を制限できます。 Intune では、デバイス シリアル番号を使って、この機能を iOS、Android、macOS に拡張しています。 Intune にデバイスのシリアル番号をアップロードし、それを企業所有として事前に宣言できます。 登録の制限を使用すると、個人所有のデバイス (BYOD) をブロックして、企業所有のデバイスのみの登録を許可することができます。 [デバイス登録の制限](enrollment-restrictions-set.md)の詳細については、こちらを参照してください。

シリアル番号をインポートするには、[**デバイスの登録**] > [**業務用デバイスの ID**] に進み、[**追加**] をクリックし、(ヘッダーはない、シリアル番号と IMEI 番号など詳細情報がある 2 つの列の) CSV ファイルをアップロードします。  個人所有のデバイスを制限するには、[**デバイスの登録**] > [**登録制限**] に移動します。 [**デバイスの種類の制限**] から [**既定**] を選択し、[**プラットフォーム構成**] を選択します。 個人所有の iOS、Android、および macOS デバイスを [**許可**] または [**ブロック**] できます。 


### <a name="device-management"></a>デバイス管理   

#### <a name="new-device-action-to-force-devices-to-sync-with-intune----711369---"></a>デバイスを Intune と強制同期する新しいデバイス アクション<!-- 711369 -->
このリリースでは、選択したデバイスの Intune への即座のチェックインを強制する新しいデバイス アクションが追加されています。 チェックインしたデバイスには、それに対して保留中のアクションまたはポリシーが即座に割り当てられます。  このアクションにより、次のスケジュールされたチェックインを待つことなく、割り当てられたポリシーの検証およびトラブルシューティングを即座に実行できるようになります。
詳細については、「[同期デバイス](device-sync.md)」を参照してください。

#### <a name="force-supervised-ios-devices-to-automatically-install-the-latest-available-software-update----777100---"></a>監督下の iOS デバイスに利用可能な最新のソフトウェア更新プログラムを強制的に自動インストールする<!-- 777100 -->
ソフトウェアの更新プログラム ワークスペースに用意された新しいポリシーを使用すると、監督下の iOS デバイスに利用可能な最新のソフトウェア更新プログラムを強制的に自動インストールできます。 詳細については、「[Configure iOS update policies](/intune/software-updates-ios)」 (iOS 更新プログラム ポリシーの構成) を参照してください。


#### <a name="check-point-sandblast-mobile---new-mobile-threat-defense-partner-----954651-1172027---"></a>チェック ポイント SandBlast Mobile - 新しい Mobile Threat Defense パートナー<!-- 954651, 1172027 -->
Microsoft Intune に統合された Mobile Threat Defense ソリューションであるチェックポイントの SandBlast Mobile によって実行されるリスク評価に基づき、条件付きアクセスを利用し、モバイル デバイスから会社のリソースへのアクセスを制御できます。

##### <a name="how-integration-with-intune-works"></a>Intune との統合のしくみ
リスクは、チェックポイントの SandBlast Mobile を実行するデバイスから収集される製品利用統計情報に基づいて評価されます。 Intune のデバイス コンプライアンス ポリシーにより有効になったチェックポイントの SandBlast Mobile のリスク評価に基づいて、EMS の条件付きアクセス ポリシーを構成できます。 検出された脅威に基づき、非準拠デバイスの企業リソースへのアクセスを許可またはブロックすることができます。


### <a name="app-management"></a>アプリ管理

#### <a name="deploy-an-app-as-available-in-the-microsoft-store-for-business----748101---"></a>ビジネス向け Microsoft ストアで利用可能なアプリを展開する <!-- 748101 -->
このリリースでは、管理者はビジネス向け Microsoft ストアを使用可能として割り当てることができるようになりました。 使用可能として設定すると、エンドユーザーは、Microsoft ストアにリダイレクトされることなく、ポータル サイトのアプリまたは Web サイトからアプリをインストールできます。


### <a name="intune-apps"></a>Intune アプリ  

#### <a name="ui-updates-to-the-company-portal-website---1313244-part-1--"></a>ポータル Web サイトの UI の更新 <!--1313244 part 1-->
エンド ユーザー エクスペリエンスを向上させるために、[ポータル Web サイト](https://portal.manage.microsoft.com)の UI をいくつか更新しました。

- __アプリ タイルの機能強化__: アプリ アイコンが、アイコンの主調色に基づいて自動生成される背景で表示されます (アイコンを検出できた場合)。 適用できる場合は、アプリ タイルで以前表示されていた灰色の枠線が、この背景に代わります。

    ポータル サイト Web サイトでは、今後のリリースで可能なときには常に大きなアイコンで表示されます。 IT 管理者は、最小サイズが 120 x 120 ピクセルの高解像度アイコンを使用して、アプリを公開することをお勧めします。 

- __ナビゲーションの変更__: ナビゲーション バーの項目が、左上のハンバーガー メニューに移動されています。 カテゴリのページは削除されています。 ユーザーは参照中にカテゴリでコンテンツをフィルター処理できるようになりました。

- __おすすめアプリの更新__: サイトにおすすめとして選択したアプリを参照できる専用ページを追加し、ホームページのおすすめセクションでいくつかの UI の修正を行いました。

#### <a name="ibooks-support-for-the-company-portal-website---1231841--"></a>ポータル サイト Web サイトでの iBooks のサポート<!--1231841-->
ポータル サイトの Web サイトにユーザーが iBooks を参照してダウンロードできる専用ページを追加しました。 

### <a name="reporting"></a>レポート

#### <a name="intune-data-warehouse-public-preview"></a>Intune データ ウェアハウス (パブリック プレビュー)

Intune データ ウェアハウスは、データを毎日サンプリングし、テナントの履歴ビューを提供します。 多くの分析ツールと互換性がある OData リンクである Power BI ファイル (PBIX) を使用するか、REST API と対話して、データにアクセスできます。 詳細については、「[Intune データ ウェアハウスを使用する](reports-nav-create-intune-reports.md)」を参照してください。


## <a name="week-of-july-23rd-2017"></a>2017 年 7 月 23 日の週

### <a name="light-and-dark-modes-available-for-the-company-portal-app-for-windows-10----676547---"></a>Windows 10 のポータル サイト アプリで利用可能なライト モードとダーク モード<!---676547--->
エンドユーザーは Windows 10 のポータル サイト アプリのカラー モードをカスタマイズできるようになります。 ユーザーはポータル サイト アプリの [設定] セクションでこの変更をできるようになります。 変更はユーザーがアプリを再起動した後に反映されます。 Windows 10 のバージョン 1607 以降では、アプリ モードは既定でシステム設定になります。 Windows 10 のバージョン 1511 以前では、アプリ モードは既定でライト モードになります。

### <a name="enable-end-users-to-tag-their-device-group-in-the-company-portal-app-for-windows-10----807046--"></a>エンドユーザーは Windows 10 用のポータル サイト アプリでデバイス グループをタグ付けできる<!---807046-->
エンドユーザーは Windows 10 のポータル サイト アプリから直接タグ付けすることにより、デバイスの所属グループを選択できるようになりました。




## <a name="notices"></a>通知

### <a name="ip-addresses-for-intune-updated----1175274---"></a>Intune の IP アドレスの更新<!-- 1175274 -->
[DNS 名と IP アドレスの更新された一覧](/intune/network-bandwidth-use)を、ファイアウォールのプロキシ設定に使用できます。

### <a name="use-azure-active-directory-for-conditional-access----967947---"></a>Azure Active Directory で条件付きアクセスを使用<!-- 967947 -->
Azure コンソールの Azure Active Directory セクションで条件付きアクセスが使用できるようになりました。Office 365 Exchange Online や SharePoint Online などのクラウド アプリのポリシー設定のための、強力かつ柔軟なフレームワークをご利用いただけます。  クラシックの Intune コンソールの代わりに **[Conditional access in Azure Active Directory]\(Azure Active Directory の条件付きアクセス\)** ブレードを使用して、ポリシーを構成します。 クラシックの Intune コンソールで作成した既存のポリシーは、Azure コンソールで再作成する必要があります。 詳細については、「[Create Azure AD conditional access policies (Azure AD の条件付きアクセス ポリシーを作成する)](/intune/conditional-access-exchange-create.md#create-azure-ad-conditional-access-policies-in-intune-azure-preview)」をご覧ください。

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Apple 登録シナリオへの直接アクセス <!--951869-->
Intune では、2017 年 1 月以降に作成された Intune アカウントについて、Azure Portal の Enroll Devices ワークロードを使用して、Apple 登録シナリオに直接アクセスできるようになりました。 これまでは、Apple 登録プレビューはクラシックの Intune ポータルのリンクからのみアクセスが可能でした。 2017 年 1 月より前に作成された Intune アカウントの場合は、これらの機能が Azure で利用可能になるまでの間、1 回限りの移行が必要です。 移行スケジュールはまだ発表されていませんが、詳細はできる限り早く発表します。 既存のアカウントで Azure Portal にアクセスできない場合は、試用アカウントを作成して、新しいエクスペリエンスをテストすることを強くお勧めします。

### <a name="administration-roles-being-replaced-in-azure-portal"></a>Azure Portal で置き換えられる管理ロール
Intune クラシック ポータル (Silverlight) で使用される既存のモバイル アプリケーション管理 (MAM) の管理ロール (共同作成者、所有者、および読み取り専用) は、Intune Azure Portal の新しいロール ベースの管理制御 (RBAC) の完全なセットで置き換えられます。 Azure Portal に移行すると、管理者をこれらの新しい管理ロールに割り当て直す必要があります。 RBAC と新しいロールの詳細については、[Microsoft Intune のロール ベースのアクセス制御](/intune/role-based-access-control)に関する記事を参照してください。



## <a name="whats-coming"></a>今後の更新情報

### <a name="end-of-support-for-ios-80----1164477---"></a>iOS 8.0 のサポートの終了 <!---1164477--->
iOS 用の管理対象アプリとポータル サイト アプリから会社のリソースにアクセスするには、iOS 9.0 以降を使用している必要があります。 この 9 月までに更新されないデバイスは、ポータル サイトまたはそれらのアプリにアクセスできなくなります。 

### <a name="ui-updates-to-the-company-portal-website---1313244-part-2--"></a>ポータル Web サイトの UI の更新 <!--1313244 part 2-->
__おすすめアプリの更新__  
機能を選択したアプリをユーザーが参照できる専用ページをサイトに追加し、ホームページのおすすめセクションでいくつかの UI の修正を行いました。 これらの変更後の外観は、「[アプリ UI の新機能](whats-new-app-ui.md)」ページで確認できます。


### <a name="end-of-support-for-android-43-and-lower----1171127-1326920----"></a>Android 4.3 以前のサポートの終了<!---1171127, 1326920 --->
Android 用の管理対象アプリとポータル サイト アプリで会社のリソースにアクセスするには、Android 4.4 以降を使用している必要があります。 10 月の初めまでにデバイスを更新しないと、ポータル サイトまたはそれらのアプリにアクセスできなくなります。 12 月には、登録されているすべてのデバイスがインベントリから削除され、会社のリソースにアクセスできなくなります。 MDM を使わずにアプリの保護ポリシーを使用している場合、アプリは更新プログラムを受信できなくなり、時間の経過と共にエクスペリエンスの質が低下していきます。


### <a name="platform-support-reminder-windows-phone-81-mainstream-support-ended-july-11-2017"></a>プラットフォーム サポートのお知らせ: Windows Phone 8.1 のメインストリーム サポートが 2017 年 7 月 11 日に終了
<!-- 1327781 -->
2017 年 7 月 11 日に、Windows Phone 8.1 プラットフォームのメインストリーム サポートは終了しました。 Windows 8.1 PC のサポートには影響ありません。

Intune サービスによって管理されている Windows Phone 8.1 デバイスへの直接的な影響はありません。 登録されているデバイスは引き続き機能し、すべてのポリシー、構成、およびアプリは引き続き正常に動作します。 Intune サービスの Windows Phone 8.1 プラットフォームおよび Windows Phone 8.1 ポータル サイト アプリを対象とする機能強化は行われません。

できるだけ早い機会に、対象となる Windows Phone 8.1 デバイスを Windows 10 Mobile にアップグレードすることをお勧めします。 

### <a name="changes-in-support-for-the-intune-ios-company-portal-app-----1164474----"></a>Intune iOS ポータル サイト アプリのサポートの変更  <!-- 1164474  -->
間もなく、iOS 用 Microsoft Intune ポータル サイト アプリが新しいバージョンになり、iOS 9.0 以降を実行しているデバイスのみがサポートされるようになります。 iOS 8 をサポートするバージョンのポータル サイトは、今後、非常に短い時間だけ使用を続けることができます。 ただし、MAM が有効な iOS アプリも使っている場合は、iOS 9.0 以降しかサポートされないので、エンド ユーザーを最新の OS に更新させる必要があります。 

#### <a name="how-does-this-affect-me"></a>ユーザーへの影響
具体的な日付は決まっていませんが、計画できるように事前にお知らせします。 ユーザーが iOS 9 以降に更新したことを確認し、ポータル サイト アプリのリリース時にはポータル サイト アプリを更新するようエンドユーザーに要求してください。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>この変更に対して必要な準備
新しい Intune の機能を最大限に活用するには iOS 9.0 以降に更新するようユーザーに推奨します。  新しいバージョンのポータル サイトをインストールして新しい機能を活用するようユーザーに推奨します。

Azure Portal の Intune で [デバイス] の [すべてのデバイス] に移動し、iOS のバージョンでフィルター処理して、現在 iOS 9 より前のオペレーティング システムを使っているデバイスを確認します。

### <a name="plan-for-change-intune-is-changing-the-intune-partner-portal-experience----1050016---"></a>変更の計画: Intune で Intune パートナー ポータル エクスペリエンスが変更されます<!-- 1050016 -->
2017 年 5 月中旬のサービス更新で、Intune パートナーのページが manage.microsoft.com から削除されます。  

お客様がパートナーの管理者である場合は、Intune パートナーのページで顧客に代わって閲覧したり、操作したりすることができなくなります。代わりに、マイクロソフトの他の 2 つのパートナー ポータルのいずれかでサインインする必要があります。

[Microsoft パートナー センター](https://partnercenter.microsoft.com/)と [Microsoft Office 365 パートナー管理センター](https://portal.office.com/)の両方で、管理している顧客アカウントにサインインできます。 パートナーとして前進するために、これらのサイトのいずれかを使用して顧客の管理を行いましょう。


### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple の要求による Application Transport Security 対応のための更新<!--748318-->
Apple は、Application Transport Security (ATS) の特定の要件を適用すると発表しました。 ATS では、HTTPS 経由で行われるアプリ通信すべてに、より厳格なセキュリティ保護が適用されます。 この変更により、iOS ポータル サイト アプリを使用している Intune ユーザーが影響を受けます。

Microsoft では、新しい ATS 要件を適用する Apple TestFlight プログラムから、iOS 用ポータル サイト アプリのバージョンを入手できるようにしています。 ATS コンプライアンスをテストできるように、このバージョンを試す場合は、お客様の姓名、電子メール アドレス、および会社名を <a href="mailto:CompanyPortalBeta@microsoft.com?subject=Register to TestFlight ATS Company Portal app">CompanyPortalBeta@microsoft.com</a> に電子メールで送信してください。 詳細については、[Intune サポートのブログ](https://aka.ms/compportalats)をご覧ください。

### <a name="see-also"></a>関連項目
* [Microsoft Intune のブログ](http://go.microsoft.com/fwlink/?LinkID=273882)
* [クラウド プラットフォームのロードマップ](https://www.microsoft.com/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [ポータル Web サイトの UI の新機能](whats-new-app-ui.md)
* [以前の月の新機能](whats-new-archive.md)
