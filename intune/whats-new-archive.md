---
title: "Microsoft Intune の過去数か月の新機能"
titlesuffix: Azure portal
description: "Intune の新機能に関するページの過去の通知を確認する"
keywords: 
author: brenduns
ms.author: brenduns
manager: angrobe
ms.date: 10/19/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9ba01d60-4a03-4e3e-9aba-8be905c0054c
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5b935f4dc3def1c7b22298f3ec9105e0b2f306d8
ms.sourcegitcommit: 2b35c99ca7d3dbafe2dfe1e0b9de29573db403b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2017
---
# <a name="whats-new-in-the-microsoft-intune---previous-months"></a>Microsoft Intune の新機能 (過去数か月)

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="september-2017"></a>2017 年 9 月

### <a name="inform-end-users-what-device-information-can-be-seen-for-ios---739894--"></a>確認可能な iOS デバイス情報のエンドユーザーへの通知<!--739894-->

iOS 用ポータル サイト アプリの [デバイスの詳細] 画面に **[Ownership Type]\(所有権の種類\)** が追加されました。 これにより、ユーザーはこのページから直接、Intune のエンド ユーザー ドキュメントにあるプライバシーの詳細を参照できます。この情報は、[バージョン情報] 画面でも確認できます。

### <a name="allow-end-users-to-access-the-company-portal-app-for-android-without-enrollment----1169910---"></a>エンドユーザーの Android 用のポータル サイト アプリへのアクセスを登録なしで許可する<!---1169910--->

エンドユーザーは間もなく Android 用のポータル サイト アプリにアクセスするために、デバイスを登録しなくて済むようになります。 アプリの保護ポリシーを使用する組織のエンドユーザーが、ポータル サイト アプリを開いたときに、デバイスの登録を求めるプロンプトが表示されなくなります。 エンドユーザーはデバイスを登録することなく、ポータル サイトからアプリをインストールできるようにもなります。 


### <a name="easier-to-understand-phrasing-for-the-company-portal-app-for-android----1396349---"></a>Android 用ポータル サイト アプリの文言をわかりやすいように変更 <!---1396349--->  

Android 用ポータル サイト アプリについて、エンドユーザーが登録しやすくなるよう、テキストを変更して登録プロセスを簡易化しました。 カスタム登録ドキュメントをお持ちの場合は、ドキュメントを更新して新しい画面を反映したいと思われるかもしれません。 サンプル画像は「[Intune とエンドユーザー アプリの UI の更新](whats-new-app-ui.md#week-of-september-11-2017)」のページにあります。

### <a name="windows-10-company-portal-app-added-to-windows-information-protection-allow-policy----677129---"></a>Windows 情報保護許可ポリシーに追加された Windows 10 ポータル サイト アプリ <!-- 677129 -->

Windows 10 ポータル サイト アプリが更新され、Windows 情報保護 (WIP) がサポートされます。 WIP 許可ポリシーにアプリを追加できます。 この変更により、アプリを **[除外対象]** ボックスの一覧に追加する必要がなくなります。


## <a name="august-2017"></a>2017 年 8 月

### <a name="improvements-to-device-overview----1404453---"></a>デバイス機能強化の概要 <!-- 1404453 -->  
デバイス機能強化の概要に、登録済みデバイスが表示されるようになりましたが、Exchange ActiveSync で管理されるデバイスは除外されます。 Exchange ActiveSync デバイスには、登録済みデバイスと同じ管理オプションがありません。 Azure Portal の Intune で、登録済みデバイスの数とプラットフォーム別登録済みデバイスの数を表示するには、**[デバイス]**、**[概要]** の順に進みます。

### <a name="improvements-to-device-inventory-collected-by-intune"></a>Intune で収集されるデバイス インベントリの機能強化
<!-- 961134, 1104426, 1281327, 1333543 -->
今回のリリースでは、ユーザーが管理するデバイスで収集されるインベントリ情報が次のように改善されました。
 
-   Android devices デバイスの場合、各デバイスの最新パッチ レベルを示す列をデバイス インベントリに追加できるようになりました。 デバイスの一覧に **[セキュリティ パッチ レベル]** 列を追加し、これを表示します。
-   デバイス ビューにフィルターを適用するとき、登録日付でデバイスを絞り込めるようになりました。 たとえば、指定した日付の後に登録されたデバイスのみを表示できます。
-   **[Last Check-in Date]\(最終チェックイン日付\)** 項目で使用されるフィルターを改善しました。
-   デバイスの一覧で、会社所有デバイスの電話番号を表示できるようになりました。
さらに、フィルター ウィンドウを利用し、電話番号でデバイスを検索できます。
 
デバイス インベントリの詳細については、「[Intune デバイス インベントリを表示する方法](device-inventory.md)」を参照してください。

### <a name="conditional-access-support-for-macos-devices"></a>macOS デバイスの条件付きアクセスのサポート 
<!-- 720172 -->
Mac デバイスを Intune に登録し、そのデバイス コンプライアンス ポリシーに準拠することを求める条件付きアクセス ポリシーを設定できるようになりました。 たとえば、ユーザーは macOS 用の Intune ポータル サイト アプリをダウンロードして、Mac デバイスを Intune に登録します。 Intune は、暗証番号 (PIN)、暗号化、OS バージョン、およびシステムの整合性などの要件にその Mac デバイスが準拠しているかどうかを評価します。

- macOS デバイスの条件付きアクセスのサポートについて詳しくは、[こちら](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)をご覧ください。

### <a name="company-portal-app-for-macos-is-in-public-preview----1484796---"></a>macOS 用ポータル サイト アプリはパブリック レビュー中です <!---1484796--->
macOS 用ポータル サイト アプリが Enterprise Mobility + Security の条件付きアクセス向けパブリック レビューの一部として利用可能になりました。 このリリースでは macOS 10.11 以降をサポートしています。 [https://aka.ms/macOScompanyportal](https://aka.ms/macOScompanyportal) から入手してください。 


### <a name="new-device-restriction-settings-for-windows-10"></a>Windows 10 の新しいデバイスの制限設定    
<!--1063965, 1308850  -->
このリリースでは、次のカテゴリに [Windows 10 デバイス制限プロファイル](/intune/device-restrictions-windows-10)の新しい設定が追加されました。

-   Windows Defender SmartScreen
-   アプリ ストア

### <a name="updates-to-the-windows-10-endpoint-protection-device-profile-for-bitlocker-settings"></a>Windows 10 エンドポイント保護デバイス プロファイルの BitLocker 設定の更新
<!--1459533 -->    
今回のリリースでは、Windows 10 エンドポイント保護デバイス プロファイルにおける BitLocker 設定の動作が次のように改善されました。
 
**[BitLocker OS ドライブの設定]** の **[互換性のない TPM チップでの BitLocker]** 設定で **[ブロック]** を選択すると、以前は、BitLocker が実際には許可されていました。 ブロックを選択すると BitLocker がブロックされるように修正されました。
**[BitLocker OS ドライブの設定]** の **[証明書ベースのデータ回復エージェント]** 設定で、証明書ベースのデータ回復エージェントを明示的にブロックできるようになりました。 ただし、既定では、エージェントが許可されます。
**[BitLocker 固定データ ドライブの設定]** の **[データ回復エージェント]** 設定で、データ回復エージェントを明示的にブロックできるようになりました。
詳しくは、「[Microsoft Intune での Windows 10 以降用の Endpoint Protection 設定](endpoint-protection-windows-10.md)」をご覧ください。


### <a name="new-signed-in-experience-for-android-company-portal-users-and-app-protection-policy-users----621669---"></a>Android ポータル サイト ユーザーおよびアプリ保護ポリシー ユーザーに対する新しいサインイン エクスペリエンス<!-- 621669 -->
エンドユーザーは、Android デバイスを登録しなくても、Android ポータル サイト アプリを使用して、今すぐにアプリを閲覧したり、デバイスを管理したり、IT 連絡先情報を確認したりできます。 また、エンドユーザーが既に Intune App Protection ポリシーによって保護されているアプリを使用しているときに、Android ポータル サイトを起動した場合、エンドユーザーに、デバイスの登録をするプロンプトが表示されなくなりました。

### <a name="new-setting-in-the-android-company-portal-app-to-toggle-battery-optimization---1405990--"></a>Android ポータル サイト アプリのバッテリの最適化を切り替える新しい設定<!--1405990-->
Android ポータル サイト アプリの **[設定]** ページには、ポータル サイトと Microsoft Authenticator アプリのバッテリ最適化をユーザーが簡単にオフにできる新しい設定があります。 この設定で表示されるアプリ名は、どのアプリが職場アカウントを管理しているかによって異なります。 電子メールとデータを同期する職場アプリのパフォーマンスの向上には、バッテリの最適化をオフにすることをお勧めします。 

### <a name="multi-identity-support-for-onenote-for-ios---------1234281---"></a>OneNote for iOS の複数 ID のサポート      <!-- 1234281 -->
エンド ユーザーは Microsoft OneNote for iOS で複数のアカウントを利用できるようになりました (職場用と個人用)。 アプリ保護ポリシーを、個人のノートブックに適用することなく、職場のノートブックの企業データに適用できます。 たとえば、職場のノートブックでは情報を検索できるが、職場のノートブックから個人のノートブックに企業データをコピーして貼り付ける行為は禁止するポリシーを適用できます。
 
- Intune で [アプリ保護と複数の ID](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) をサポートするアプリについての詳細を参照してください。

### <a name="new-settings-to-allow-and-block-apps-on-samsung-knox-standard-devices"></a>Samsung KNOX Standard デバイス用のアプリを許可またはブロックするための新しい設定
<!-- 1305423 822899-->  
このリリースでは、次のアプリ一覧を指定できる[デバイスの制限設定](device-restrictions-android.md)が新規に追加されています。
 
- ユーザーがインストールを許可されているアプリ
- ユーザーが実行をブロックされているアプリ
- デバイスのユーザーに非表示となっているアプリ
 
アプリは、URL、パッケージ名、管理対象のアプリ一覧から指定できます。

### <a name="new-azure-ad-app-based-conditional-access-policy-ui-link-from-intune"></a>Intune からリンクされる新しい Azure AD のアプリ ベースの条件付きアクセス ポリシーの UI
<!-- 1016201 -->
IT 管理者が、Azure AD のワークロードで新しい条件付きアクセス ポリシーの UI を使用してアプリ ベースの条件付きポリシーを設定できるようになりました。 Azure Portal の Intune App Protection セクションにあるアプリ ベースの条件付きアクセス ポリシーは当面そのまま残り、サイド バイ サイドで強制されます。 また、Intune ワークロードから新しい条件付きアクセス ポリシー UI への便利なリンクもあります。

- Azure AD のアプリ ベースの条件付きアクセスについて詳しくは、[こちら](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-technical-reference)をご覧ください。



## <a name="july-2017"></a>2017 年 7 月

### <a name="restrict-android-and-ios-device-enrollment-restriction-by-os-version------1333256--1245463----"></a>Android および iOS デバイスの OS のバージョンによる登録制限 <!--- 1333256,  1245463 --->
オペレーティング システムのバージョン番号によって iOS と Android の登録を制限する機能が追加されました。 **[デバイスの種類の制限]** で、IT 管理者は、プラットフォーム構成を設定して、オペレーティング システムのバージョン番号の最小値から最大値までの間に登録を制限できるようになりました。 Android オペレーティング システムのバージョンは、Major.Minor.Build.Rev の形式で指定する必要があります (Minor、Build、Rev は任意)。 iOS のバージョンは、Major.Minor.Build の形式で指定する必要があります (Minor と Build は任意)。 [デバイス登録の制限](enrollment-restrictions-set.md)の詳細については、こちらを参照してください。

>[!NOTE]
>Apple の登録プログラムまたは Apple Configurator では、登録は制限されません。

### <a name="restrict-android-ios-and-macos-device-personally-owned-device-enrollment------1333272--1333275-1245709----"></a>個人所有の Android、iOS、および macOS デバイスの登録を制限する<!--- 1333272,  1333275, 1245709 --->
Intune では、会社デバイスの IMEI 番号のホワイトリストを作成して、個人用デバイスの登録を制限できます。 Intune では、デバイス シリアル番号を使って、この機能を iOS、Android、macOS に拡張しています。 Intune にデバイスのシリアル番号をアップロードし、それを企業所有として事前に宣言できます。 登録の制限を使用すると、個人所有のデバイス (BYOD) をブロックして、企業所有のデバイスのみの登録を許可することができます。 [デバイス登録の制限](enrollment-restrictions-set.md)の詳細については、こちらを参照してください。

シリアル番号をインポートするには、**[デバイスの登録]** > **[業務用デバイスの ID]** に進み、**[追加]** をクリックし、(ヘッダーはない、シリアル番号と IMEI 番号など詳細情報がある 2 つの列の) CSV ファイルをアップロードします。  個人所有のデバイスを制限するには、**[デバイスの登録]** > **[登録制限]** に移動します。 **[デバイスの種類の制限]** から **[既定]** を選択し、**[プラットフォーム構成]** を選択します。 個人所有の iOS、Android、および macOS デバイスを **[許可]** または **[ブロック]** できます。 


### <a name="new-device-action-to-force-devices-to-sync-with-intune----711369---"></a>デバイスを Intune と強制同期する新しいデバイス アクション<!-- 711369 -->
このリリースでは、選択したデバイスの Intune への即座のチェックインを強制する新しいデバイス アクションが追加されています。 チェックインしたデバイスには、それに対して保留中のアクションまたはポリシーが即座に割り当てられます。  このアクションにより、次のスケジュールされたチェックインを待つことなく、割り当てられたポリシーの検証およびトラブルシューティングを即座に実行できるようになります。
詳細については、「[同期デバイス](device-sync.md)」を参照してください。

### <a name="force-supervised-ios-devices-to-automatically-install-the-latest-available-software-update----777100---"></a>監督下の iOS デバイスに利用可能な最新のソフトウェア更新プログラムを強制的に自動インストールする<!-- 777100 -->
ソフトウェアの更新プログラム ワークスペースに用意された新しいポリシーを使用すると、監督下の iOS デバイスに利用可能な最新のソフトウェア更新プログラムを強制的に自動インストールできます。 詳細については、「[Configure iOS update policies](/intune/software-updates-ios)」 (iOS 更新プログラム ポリシーの構成) を参照してください。

### <a name="check-point-sandblast-mobile---new-mobile-threat-defense-partner-----954651-1172027---"></a>チェック ポイント SandBlast Mobile - 新しい Mobile Threat Defense パートナー<!-- 954651, 1172027 -->
Microsoft Intune に統合された Mobile Threat Defense ソリューションであるチェックポイントの SandBlast Mobile によって実行されるリスク評価に基づき、条件付きアクセスを利用し、モバイル デバイスから会社のリソースへのアクセスを制御できます。

#### <a name="how-integration-with-intune-works"></a>Intune との統合のしくみ
リスクは、チェックポイントの SandBlast Mobile を実行するデバイスから収集される製品利用統計情報に基づいて評価されます。 Intune のデバイス コンプライアンス ポリシーにより有効になったチェックポイントの SandBlast Mobile のリスク評価に基づいて、EMS の条件付きアクセス ポリシーを構成できます。 検出された脅威に基づき、非準拠デバイスの企業リソースへのアクセスを許可またはブロックすることができます。


### <a name="deploy-an-app-as-available-in-the-microsoft-store-for-business----748101---"></a>ビジネス向け Microsoft ストアで利用可能なアプリを展開する <!-- 748101 -->
このリリースでは、管理者はビジネス向け Microsoft ストアを使用可能として割り当てることができるようになりました。 使用可能として設定すると、エンドユーザーは、Microsoft ストアにリダイレクトされることなく、ポータル サイトのアプリまたは Web サイトからアプリをインストールできます。

### <a name="ui-updates-to-the-company-portal-website---1313244-part-1--"></a>ポータル Web サイトの UI の更新 <!--1313244 part 1-->
エンド ユーザー エクスペリエンスを向上させるために、[ポータル Web サイト](https://portal.manage.microsoft.com)の UI をいくつか更新しました。

- __アプリ タイルの機能強化__: アプリ アイコンが、アイコンの主調色に基づいて自動生成される背景で表示されます (アイコンを検出できた場合)。 適用できる場合は、アプリ タイルで以前表示されていた灰色の枠線が、この背景に代わります。

    ポータル サイト Web サイトでは、今後のリリースで可能なときには常に大きなアイコンで表示されます。 IT 管理者は、最小サイズが 120 x 120 ピクセルの高解像度アイコンを使用して、アプリを公開することをお勧めします。 

- __ナビゲーションの変更__: ナビゲーション バーの項目が、左上のハンバーガー メニューに移動されています。 カテゴリのページは削除されています。 ユーザーは参照中にカテゴリでコンテンツをフィルター処理できるようになりました。

- __おすすめアプリの更新__: サイトにおすすめとして選択したアプリを参照できる専用ページを追加し、ホームページのおすすめセクションでいくつかの UI の修正を行いました。

### <a name="ibooks-support-for-the-company-portal-website---1231841--"></a>ポータル サイト Web サイトでの iBooks のサポート<!--1231841-->
ポータル サイトの Web サイトにユーザーが iBooks を参照してダウンロードできる専用ページを追加しました。 


### <a name="additional-help-desk-troubleshooting-details------applies-to-1263399-1326964-1341642----"></a>ヘルプ デスク トラブルシューティングの追加詳細 <!---  Applies to 1263399, 1326964, 1341642 --->
Intune では、トラブルシューティング ディスプレイを更新し、管理者やヘルプ デスク スタッフ向けの情報を追加しました。 グループのメンバーシップに基づいてユーザーの全割り当てをまとめた**割り当て**テーブルが表示されます。 この一覧の内容:
- モバイル アプリ
- Compliance ポリシー
- 構成プロファイル
 
また、**デバイス** テーブルに **[Azure AD 結合の種類]** 列と **[Azure AD 準拠]** 列が追加されました。 詳細については「[問題のトラブルシューティングの方法](help-desk-operators.md)」を参照してください。



### <a name="intune-data-warehouse-public-preview"></a>Intune データ ウェアハウス (パブリック プレビュー)
Intune データ ウェアハウスは、データを毎日サンプリングし、テナントの履歴ビューを提供します。 多くの分析ツールと互換性がある OData リンクである Power BI ファイル (PBIX) を使用するか、REST API と対話して、データにアクセスできます。 詳細については、「[Intune データ ウェアハウスを使用する](reports-nav-create-intune-reports.md)」を参照してください。


### <a name="light-and-dark-modes-available-for-the-company-portal-app-for-windows-10----676547---"></a>Windows 10 のポータル サイト アプリで利用可能なライト モードとダーク モード<!---676547--->
エンドユーザーは Windows 10 のポータル サイト アプリのカラー モードをカスタマイズできるようになります。 ユーザーはポータル サイト アプリの [設定] セクションでこの変更をできるようになります。 変更はユーザーがアプリを再起動した後に反映されます。 Windows 10 のバージョン 1607 以降では、アプリ モードは既定でシステム設定になります。 Windows 10 のバージョン 1511 以前では、アプリ モードは既定でライト モードになります。

### <a name="enable-end-users-to-tag-their-device-group-in-the-company-portal-app-for-windows-10----807046--"></a>エンドユーザーは Windows 10 用のポータル サイト アプリでデバイス グループをタグ付けできる<!---807046-->
エンドユーザーは Windows 10 のポータル サイト アプリから直接タグ付けすることにより、デバイスの所属グループを選択できるようになりました。



## <a name="june-2017"></a>2017 年 6 月

### <a name="new-role-based-administration-access-for-intune-admins------1099990---"></a>Intune 管理者のための新しいロール ベース管理アクセス   <!-- 1099990 -->  
Azure AD の条件付きアクセス ポリシーを表示、作成、変更、削除できる新しい条件付きアクセス管理者ロールが追加されます。 以前は、このアクセス許可を持つのは、グローバル管理者とセキュリティ管理者のみでした。 条件付きアクセス ポリシーにアクセスできるように、Intune 管理者にこのロールのアクセス許可が付与されます。


### <a name="tag-corporate-owned-devices-with-serial-number----1215070---"></a>会社所有のデバイスにシリアル番号をタグ付けする <!-- 1215070 -->  
Intune では、iOS、macOS、Android のシリアル番号を会社デバイスの識別子としてアップロードできるようになりました。 この新機能では、シリアル番号を使用して個人用デバイスの登録をブロックすることはできません。登録中はシリアル番号が検証されないためです。 シリアル番号を使用して個人用デバイスをブロックする機能は、近いうちにリリースされる予定です。


### <a name="new-remote-actions-for-ios-devices----854689---"></a>iOS デバイスの新しいリモート操作 <!-- 854689 -->
このリリースでは Apple Classroom アプリを管理する新しいリモート デバイス アクションを共有の iPad デバイスに追加しました。

-   [[現在のユーザーのログアウト]](device-logout-user.md) - 選択した iOS デバイスの現在のユーザーをログアウトさせます。
-   [[ユーザーの削除]](device-remove-user.md) - iOS デバイスのローカル キャッシュから選択したユーザーを削除します。


### <a name="support-for-shared-ipads-with-the-ios-classroom-app----1044681---"></a>iOS Classroom アプリによる共有 iPad のサポート <!-- 1044681 -->
このリリースでは、iOS Classroom アプリの管理サポートが拡張され、自分で管理している Apple ID を使って共有 iPad にログインする生徒を含めることができるようになっています。


### <a name="changes-to-intune-built-in-apps----1332306---"></a>Intune の組み込みアプリの変更 <!-- 1332306 -->
以前は、Intune に簡単に割り当てができる組み込みのアプリが多数含まれていました。 お客様からのフィードバックに基づき、この一覧を削除しました。組み込みのアプリは今後表示されません。
ただし、組み込みのすべてのアプリが既に割り当てられている場合、そのアプリはアプリの一覧に引き続き表示されます。 これらのアプリの割り当ては必要に応じて続行することができます。
今後のリリースでは、Azure Portal から組み込みのアプリをより簡単に選択して割り当てる方法を追加する予定です。

### <a name="easier-installation-of-office-365-apps-----1121362----"></a>Office 365 アプリをより簡単にインストールする<!--- 1121362 --->
新しいタイプの **Office 365 ProPlus** アプリでは、最新バージョンの Windows 10 を実行する管理対象のデバイスに、Office 365 ProPlus 2016 アプリを簡単に割り当てることができます。 また、ライセンスを所有している場合、Microsoft Project や Microsoft Visio をインストールすることもできます。 必要なアプリはバンドルされ、Intune コンソールのアプリ一覧に 1 つのアプリとして表示されます。
詳細については、「[Windows 10 用の Office 365 アプリを追加する方法](apps-add-office365.md)」を参照してください。


### <a name="support-for-offline-apps-from-the-microsoft-store-for-business-----777044----"></a>ビジネス向け Microsoft ストアから入手したオフライン アプリのサポート <!--- 777044 --->
ビジネス向け Microsoft ストアから購入したオフライン アプリが Azure Portal に同期されます。 その後、これらのアプリをデバイス グループまたはユーザー グループに展開できます。 オフライン アプリはストアではなく Intune でインストールします。

### <a name="microsoft-teams-is-now-part-of-the-app-based-ca-list-of-approved-apps------1257019---"></a>Microsoft Teams が承認済みアプリのアプリ ベース CA 一覧の一部になった   <!-- 1257019 -->
iOS と Android 用の Microsoft Teams アプリが、Exchange と SharePoint Online のアプリ ベースの条件付きアクセス ポリシー向けの承認済みアプリの一部になりました。 Azure Portal の Intune アプリ保護ブレードで、現在アプリ ベースの条件付きアクセスを使っているすべてのテナントにアプリを構成できます。

### <a name="managed-browser-and-app-proxy-integration----1287310---"></a>管理対象ブラウザーとアプリ プロキシの統合<!-- 1287310 -->
Intune Managed Browser は Azure AD アプリケーション プロキシと統合できるようになり、ユーザーはリモートで作業しているときでも内部 Web サイトにアクセスできます。 ブラウザーのユーザーが通常と同じようにサイトの URL を単に入力すると、Managed Browser はアプリケーション プロキシの Web ゲートウェイを介して要求をルーティングします。 詳しくは、「[Managed Browser ポリシーを使用したインターネット アクセスの管理](app-configuration-managed-browser.md)」をご覧ください。

### <a name="new-app-configuration-settings-for-the-intune-managed-browser----682951---"></a>Intune Managed Browser の新しいアプリ構成設定 <!-- 682951 -->
このリリースでは、iOS および Android 用の Intune Managed Browser アプリに構成が追加されました。 アプリ構成ポリシーを使って、ブラウザーの既定のホーム ページとブックマークを構成できます。
詳しくは、「[Managed Browser ポリシーを使用したインターネット アクセスの管理](app-configuration-managed-browser.md)」をご覧ください。

### <a name="bitlocker-settings-for-windows-10-----951707---"></a>Windows 10 用の BitLocker の設定  <!-- 951707 -->
新しい Intune デバイス プロファイルを使って、Windows 10 デバイス用の BitLocker の設定を構成できます。 たとえば、デバイスの暗号化を要求でき、BitLocker が有効になっているときに適用される設定をさらに構成することもできます。
詳しくは、「[Microsoft Intune での Windows 10 以降用の Endpoint Protection 設定](endpoint-protection-windows-10.md)」をご覧ください。

### <a name="new-settings-for-windows-10-device-restriction-profile-----978527--978550-978569-1050031-1058611-----"></a>Windows 10 デバイス制限プロファイルの新しい設定 <!--- 978527,  978550, 978569, 1050031, 1058611,  --->
このリリースでは、次のカテゴリに Windows 10 デバイス制限プロファイルの新しい設定が追加されました。

-  Windows Defender
-  携帯ネットワークと接続性
-  ロック画面
-  プライバシー
-  検索
-  Windows スポットライト
-  Edge ブラウザー

Windows 10 の設定について詳しくは、「[Microsoft Intune での Windows 10 以降のデバイスの制限設定](device-restrictions-windows-10.md)」をご覧ください。


### <a name="company-portal-app-for-android-now-has-a-new-end-user-experience-for-app-protection-policies---1305217--"></a>Android 用ポータル サイト アプリのアプリ保護ポリシーの新しいエンド ユーザー エクスペリエンス <!--1305217-->
ユーザーのフィードバックに基づいて、Android 用ポータル サイト アプリに **[会社のコンテンツにアクセスする]** ボタンが表示されるようになりました。 このボタンの目的は、Intune モバイル アプリケーション管理の機能であるアプリ保護ポリシーをサポートするアプリにアクセスすることだけが必要なユーザーが、不要な登録プロセスを経なくて済むようにすることです。 これらの変更については、「[アプリ UI の新機能](whats-new-app-ui.md)」ページをご覧ください。

### <a name="new-menu-action-to-easily-remove-company-portal---1164569--"></a>ポータル サイトを簡単に削除できるアクション メニューの追加<!--1164569-->
Android 用ポータル サイト アプリでは、ユーザーからのフィードバックに基づき、デバイスからポータル サイトの削除を開始できる新しいアクション メニューが追加されました。 この操作では Intune の管理対象からデバイスが削除されるため、ユーザーはデバイスからアプリを削除できるようになります。 これらの変更については、[Android エンド ユーザー向けドキュメント](/intune-user-help/unenroll-your-device-from-intune-android)の[アプリ UI の新機能](whats-new-app-ui.md)に関するページで確認できます。

### <a name="improvements-to-app-syncing-with-windows-10-creators-update---676505--"></a>Windows 10 Creators Update とアプリを同期する機能の強化 <!--676505-->
Windows 10 用ポータル サイト アプリでは、Windows 10 Creators Update (バージョン 1703) がインストールされているデバイスのアプリ インストール要求の同期が自動的に開始されるようになりました。 "同期保留中" 状態中、アプリ インストールが止まる問題を減らします。 また、ユーザーはアプリ内から同期を手動で開始できます。 これらの変更については、「[アプリ UI の新機能](whats-new-app-ui.md)」ページをご覧ください。

### <a name="new-guided-experience-for-windows-10-company-portal----1058938---"></a>Windows 10 ポータル サイトの新しいガイド機能 <!---1058938--->
Windows 10 用のポータル サイト アプリで、特定または登録されていないデバイス向けのガイド付き Intune チュートリアルを利用できるようになります。 ユーザーは新たな段階的手順に従って、Azure Active Directory (条件付きアクセス機能のために必要) と MDM (デバイス管理機能のために必要) に登録できます。 このガイドには、ポータル サイトのホーム ページからアクセスできます。 ユーザーは登録が完了していなくても引き続きアプリを使用できますが、機能は制限されます。

この更新は、Windows 10 Anniversary Update (ビルド 1607) 以降を実行しているデバイスのみで表示されます。 これらの変更については、「[アプリ UI の新機能](whats-new-app-ui.md)」ページをご覧ください。


### <a name="microsoft-intune-and-conditional-access-admin-consoles-are-generally-available"></a>Microsoft Intune 管理コンソールと条件付きアクセス管理コンソールの一般提供開始
Azure Portal の新しい Intune 管理コンソールと、条件付きアクセス管理コンソールの一般提供開始が発表されました。 Azure Portal で Intune を利用することで、Intune MAM および MDM のすべての機能を統合された 1 つの管理者エクスペリエンスで管理し、Azure AD のグループとターゲットを利用できるようになりました。 Azure の条件付きアクセスにより、Azure AD と Intune の豊富な機能が一元化されたコンソールに統合されます。 また管理者エクスペリエンスから Azure プラットフォームに移動して、最新のブラウザーを使用できます。

Intune は、**[プレビュー]** ラベルが外れた状態で Azure Portal (portal.azure.com) に表示されるようになりました。

メッセージ センターの一連のメッセージのうち、グループを移行できるようにお客様の対応をお願いするメッセージを受信された場合を除き、現時点で既存のお客様にしていただくことはありません。 こちらのバグにより、移行に時間がかかることをお知らせする通知がメッセージ センターから送信されている場合もあります。 Microsoft では、影響を受けたユーザーを移行する作業に引き続き取り組んでまいります。

### <a name="improvements-to-the-app-tiles-in-the-company-portal-app-for-ios"></a>iOS 用ポータル サイト アプリのアプリ タイルを改善
ポータル サイトに設定したブランド カラーが反映されるよう、ホーム ページのアプリ タイルのデザインを一新しました。 詳細については、[アプリ UI の新機能](whats-new-app-ui.md)に関するページをご覧ください。

### <a name="account-picker-now-available-for-the-company-portal-app-for-ios"></a>iOS 用ポータル サイト アプリでアカウント選択の提供を開始
iOS デバイスのユーザーが、職場または学校アカウントを使用して別の Microsoft アプリにサインインしているときに、ポータル サイトにサインインしようとすると、新しいアカウントの選択が表示される場合があります。 詳細については、[アプリ UI の新機能](whats-new-app-ui.md)に関するページをご覧ください。

## <a name="may-2017"></a>2017 年 5 月

### <a name="change-your-mdm-authority-without-unenrolling-managed-devices---1103950--"></a>管理対象デバイスの登録を解除せず、MDM 機関を変更する <!--1103950-->
Microsoft サポートに問い合わせずに、また、既存の管理されたデバイスの登録解除と再登録を行わずに MDM 機関を変更できるようになりました。 Configuration Manager コンソールで、[Configuration Manager に設定]\(ハイブリッド\) から [Microsoft Intune]\(スタンドアロン\) に、またはその逆に [MDM 機関を変更](/sccm/mdm/deploy-use/change-mdm-authority)できます。


### <a name="improved-notification-for-samsung-knox-startup-pins---1087143--"></a>Samsung KNOX 起動 PIN の通知機能強化 <!--1087143-->
暗号化に対応する目的でエンド ユーザーが Samsung KNOX デバイスに起動 PIN を設定する必要があるとき、エンド ユーザーに表示される通知をタップすると、設定アプリ内の設定場所に移動します。  以前は、エンド ユーザーは通知からパスワード変更画面に進むことができました。

### <a name="device-enrollment"></a>デバイスの登録

#### <a name="apple-school-manager-asm-support-with-shared-ipad----748864-770395--"></a>共有 iPad での Apple School Manager (ASM) のサポート <!-- 748864, 770395-->

Intune では、Apple Device Enrollment Program の代わりに Apple School Manager (ASM) を使用できるようになりました。すぐに iOS デバイスを登録できます。 共有 iPad で Classroom アプリを使用するには ASM オンボードが必要です。これは、Microsoft School Data Sync (SDS) 経由で ASM から Azure Active Directory へのデータ同期を有効にする際にも必要です。 詳細については、「[Enable iOS device enrollment with Apple School Manager (Apple School Manager での iOS デバイス登録の有効化)](apple-school-manager-set-up-ios.md)」をご覧ください。

> [!NOTE]
> 共有 iPad で Classroom アプリを使用できるように構成するには、Azure に iOS 向けの Education の構成が必要ですが、現時点では提供されていません。  この機能は、近日中に追加される予定です。

### <a name="device-management"></a>デバイス管理

#### <a name="provide-remote-assistance-to-android-devices-using-teamviewer----675418---"></a>TeamViewer を利用して Android デバイスにリモート アシスタンスを提供<!-- 675418 -->

Intune では、別売りの [TeamViewer](https://www.teamviewer.com) ソフトウェアを利用して、Android デバイスを使用するユーザーにリモート アシスタンスを提供できるようになりました。 詳細については、「[Provide remote assistance for Intune managed Android devices (Intune 管理対象の Android デバイスにリモート アシスタンスを提供)](device-profile-android-teamviewer.md)」をご覧ください。

### <a name="app-management"></a>アプリ管理

#### <a name="new-app-protection-policies-conditions-for-mam----679864---"></a>MAM の新しいアプリ保護ポリシー条件 <!-- 679864 -->

登録ユーザーなしで、次のポリシーを強制する MAM の要件を設定できるようになりました。

- アプリケーションの最小バージョン
- オペレーティング システムの最小バージョン
- 対象アプリケーションの最小 Intune APP SDK バージョン (iOS のみ)

この機能は、Android と iOS の両方で使うことができます。 Intune は、OS プラットフォーム バージョン、アプリケーション バージョン、Intune APP SDK の最小バージョン強制に対応しています。 iOS の場合、SDK が統合されているアプリケーションでも SDK レベルで最小バージョン強制を設定できます。 アプリ保護ポリシーの最小要件が上述の 3 つの異なるレベルで満たされていない場合、ユーザーは対象アプリケーションにアクセスできません。 この時点で、ユーザーはアカウントを削除するか (複数 ID アプリケーションの場合)、アプリケーションを閉じるか、OS またはアプリケーションのバージョンを更新できます。

また、OS またはアプリケーションのアップグレードを推奨するブロック不可の通知を表示するように追加設定することもできます。 この通知は閉じて、アプリケーションを普段どおり使用できます。

詳細については、「[iOS アプリ保護ポリシー設定](app-protection-policy-settings-ios.md)」と「[Android アプリ保護ポリシー設定](app-protection-policy-settings-android.md)」をご覧ください。

#### <a name="configure-app-configurations-for-android-for-work----621621---"></a>Android for Work 用のアプリ構成の設定<!-- 621621 -->
ストアの一部の Android アプリは管理対象の構成オプションをサポートしているため、IT 管理者は作業プロファイルでアプリの実行方法を制御できます。 Intune では、Azure Portal からアプリがサポートする構成を表示し、構成デザイナーまたは JSON エディターを使用してこれらの構成を設定できるようになりました。 詳細については、[Android for Work 用のアプリ構成の使用](app-configuration-policies-use-android.md)に関するページをご覧ください。

#### <a name="new-app-configuration-capability-for-mam-without-enrollment----677969---"></a>登録なしで利用できる MAM の新しいアプリ構成機能<!-- 677969 -->
登録チャネルがなくても MAM からアプリ構成ポリシーを作成できるようになりました。 これは、モバイル デバイス管理 (MDM) のアプリ構成で使用できるアプリ構成ポリシーと同等の機能です。 登録せずに MAM を使用してアプリを構成する例については、「[Manage Internet access using Managed browser policies with Microsoft Intune (Microsoft Intune と Managed Browser のポリシーを使用したインターネット アクセスの管理)](app-configuration-managed-browser.md)」をご覧ください。

#### <a name="configure-allowed-and-blocked-url-lists-for-the-managed-browser----682960---"></a>Managed Browser で許可される URL とブロックされる URL 一覧の構成<!-- 682960 -->
Azure Portal のアプリ構成設定を使用して、Intune Managed Browser で許可またはブロックされるドメインおよび URL の一覧を構成できるようになりました。 これらの設定は、管理されたデバイスで使用されているか、管理されていないデバイスで使用されているかに関係なく構成できます。 詳細については、「[Manage Internet access using Managed browser policies with Microsoft Intune (Microsoft Intune と Managed Browser のポリシーを使用したインターネット アクセスの管理)](app-configuration-managed-browser.md)」をご覧ください。

#### <a name="app-protection-policy-helpdesk-view----1069473---"></a>アプリ保護ポリシー ヘルプデスクのビュー<!-- 1069473 -->
IT ヘルプデスクのユーザーは、[トラブルシューティング] ブレードで、ユーザー ライセンスの状態と、ユーザーに割り当てられているアプリのアプリ保護ポリシーの状態を確認できるようになりました。 詳細については、[トラブルシューティング](./help-desk-operators.md)に関するページをご覧ください。

### <a name="device-configuration"></a>デバイス構成

#### <a name="control-website-visits-on-ios-devices----723832---"></a>iOS デバイスの Web サイト アクセスの制御<!-- 723832 -->
iOS デバイスのユーザーがアクセスできる Web サイトを次の 2 つの方法を使って制御できるようになりました。

- Apple の組み込み Web コンテンツ フィルターを使って、許可される URL またはブロックされる URL を追加します。

- Safari ブラウザーによるアクセスを許可する Web サイトを指定します。 指定した各サイトについて、Safari にブックマークが作成されます。

詳細については、「[Web content filter settings for iOS devices (iOS デバイス用の Web コンテンツ フィルター設定)](web-content-filter-settings-ios.md)」をご覧ください。

#### <a name="preconfigure-device-permissions-for-android-for-work-apps----621614---"></a>Android for Work アプリのデバイス アクセス許可の事前構成 <!-- 621614 -->
Android for Work デバイスの作業プロファイルに展開したアプリの場合、個々のアプリのアクセス許可状態を構成できるようになりました。  既定では、場所やデバイス カメラへのアクセスなど、デバイスのアクセス許可を必要とする Android アプリはアクセス許可の承諾または拒否をユーザーに求めます。  たとえば、アプリでデバイスのマイクが使用される場合、そのマイクを使用するアクセス許可をアプリに与えるようにエンド ユーザーに求められます。 この機能を利用すると、エンド ユーザーの代わりにアクセス許可を定義できます。  アクセス許可は、a) ユーザーに通知することなく自動的に拒否する、b) ユーザーに通知することなく自動的に承諾する、c) 承諾または拒否をユーザーに求めるのいずれかに構成できます。 詳細については、「[Microsoft Intune での Android for Work デバイスの制限設定](device-restrictions-android-for-work.md)」をご覧ください。

#### <a name="define-app-specific-pin-for-android-for-work-devices----728976-1102534---"></a>Android for Work デバイスのアプリ固有 PIN を定義する <!-- 728976, 1102534 -->
管理者は、Android for Work デバイスとして管理されている Android 7.0 以上のデバイスの作業プロファイルで、作業プロファイルのアプリにのみ適用されるパスコード ポリシーを定義できます。  次のオプションがあります。

- デバイス全体のパスコード ポリシーだけを定義する - これは、デバイス全体のロックを解除するためにユーザーが使用しなければならないパスコードです。
- 作業プロファイルのパスコード ポリシーだけを定義する - 作業プロファイルのアプリを起動するたびに、ユーザーにパスコードの入力が求められます。
- デバイスと作業プロファイル ポリシーの両方を定義する - IT 管理者はデバイスのパスコード ポリシーと作業プロファイルのパスコード ポリシーをいずれも異なる強度で定義できます。たとえば、デバイスのロック解除に 4 桁の PIN を要求し、作業アプリの起動に 6 桁の PIN を要求します。

詳細については、「[Microsoft Intune での Android for Work デバイスの制限設定](device-restrictions-android-for-work.md)」をご覧ください。

> [!NOTE]
> この機能は Android 7.0 以降でのみ利用できます。  既定では、エンド ユーザーは別々に定義された 2 つの PIN を利用できます。あるいは、定義された 2 つの PIN のうちの強いほうを選択できます。

#### <a name="new-settings-for-windows-10-devices----978585---"></a>Windows 10 デバイスの新しい設定<!-- 978585 -->
Microsoft は、無線ディスプレイ、デバイス検出、タスク切り替え、SIM カード エラー メッセージなどの機能を制御する新しい [Windows デバイス制限設定](device-restrictions-windows-10.md)を追加しています。

#### <a name="updates-to-certificate-configuration----918991-and-823198---"></a>証明書の構成の更新<!-- 918991 and 823198 -->
SCEP 証明書プロファイルを作成するときに、**[サブジェクト名の形式]**で、**[カスタム]** オプションを iOS、Android、および Windows デバイスでご利用いただけます。 今回の更新までは、**[カスタム]** フィールドを使用できるのは iOS デバイスだけでした。 詳細については、「SCEP 証明書プロファイルを作成する方法」(certificates-scep-configure.md#how-to-create-a-scep-certificate-profile) をご覧ください。

PKCS 証明書プロファイルを作成するときに、**[サブジェクトの別名]** で、**[Custom Azure AD attribute]\(Azure AD のカスタム属性\)** をご使用いただけます。 **[Custom Azure AD attribute]\(Azure AD のカスタム属性\)** を選択すると、**[部門]** オプションが使用できます。 詳細については、[PKCS 証明書プロファイルを作成する方法](certficates-pfx-configure.md#create-a-device-configuration-profile)に関するページをご覧ください。

#### <a name="configure-multiple-apps-that-can-run-when-an-android-device-is-in-kiosk-mode----662059---"></a>Android デバイスがキオスク モードのときに実行できる複数アプリの構成<!-- 662059 -->
これまでは、Android デバイスがキオスク モードのときに実行できるアプリは 1 つしか設定できませんでした。 アプリ ID やストアの URL を使用するか、すでに管理している Android アプリを選択して、複数のアプリを設定できるようになりました。 詳細については、[キオスク モードの設定](device-restrictions-android.md#kiosk)に関するページをご覧ください。



## <a name="april-2017"></a>2017 年 4 月

### <a name="support-for-managing-the-apple-classroom-app"></a>Apple Classroom アプリの管理のサポート
iPad デバイスで iOS Classroom アプリを管理できるようになりました。 クラスと学生の正しいデータで教師の iPad に Classroom アプリをセットアップした後、アプリを使って制御できるように、クラスに登録されている学生の iPad を構成します。
詳しくは、「[Configure iOS education settings](education-settings-configure-ios.md)」 (iOS の教育設定を構成する) をご覧ください。

### <a name="support-for-managed-configuration-options-for-android-apps----621621---"></a>Android アプリ向けの管理対象構成オプションのサポート<!-- 621621 -->
管理対象構成オプションをサポートする Play ストアの Android アプリを、Intune で構成できるようになりました。  この機能は、アプリによってサポートされる構成値の一覧を表示できるようにし、値を構成できるガイド付きの使いやすい UI を提供します。

### <a name="new-android-policy-for-complex-pins----722069---"></a>複雑な暗証番号 (PIN) に対する新しい Android ポリシー <!-- 722069 -->
Android 5.0 以降を搭載しているデバイスの Android デバイス プロファイルに、数値複素数タイプの必須[パスワード](device-restrictions-android.md#password)を設定できるようになりました。  反復する値や連続する値 (1111 や 1234 など) を含む暗証番号 (PIN) をデバイスのユーザーが作成しないようにするには、この設定を使います。

### <a name="additional-support-for-android-for-work-devices"></a>Android for Work デバイスの追加サポート
- **パスワードと仕事用プロファイルの設定を管理する** <!-- 612808 -->

  この新しい Android for Work デバイス制限ポリシーにより、管理対象の Android for Work デバイスで、パスワードと仕事用プロファイルの設定を管理できるようになりました。

- **仕事用プロファイルと個人プロファイル間でのデータ共有を許可する** <!-- 1045102 -->

この Android for Work デバイス制限プロファイルには、仕事用プロファイルと個人用プロファイルでのデータ共有の設定ができる新しいオプションが用意されました。

- **仕事用プロファイルと個人プロファイルの間でのコピーと貼り付けを制限する** <!-- 1046094 -->

  Android for Work デバイス用の新しいカスタム デバイス プロファイルでは、仕事用アプリと個人用アプリの間でのコピーと貼り付け操作を許可するかどうかを制限できます。

詳細については、[Android for Work 用のデバイスの制限](device-restrictions-android-for-work.md)に関するページをご覧ください。

### <a name="assign-lob-apps-to-ios-and-android-devices----1057568---"></a>iOS デバイスと Android デバイスに LOB アプリを割り当てる <!-- 1057568 -->
[iOS](lob-apps-ios.md) 用 (.ipa ファイル) と [Android](lob-apps-android.md) 用 (.apk ファイル) の基幹業務 (LOB) アプリを、ユーザーまたはデバイスに割り当てることができるようになりました。


###  <a name="new-device-policies-for-ios----723774-723815-723826-723830---"></a>iOS 用の新しいデバイス ポリシー <!-- 723774, 723815, 723826, 723830 -->
- **ホーム画面のアプリ** - [iOS デバイスのホーム画面](home-screen-settings-ios.md)に表示されるアプリを制御します。 このポリシーはホーム画面のレイアウトを変更しますが、アプリの展開は行いません。

- **AirPrint デバイスへの接続** - iOS デバイスのエンド ユーザーが接続できる [AirPrint デバイス](air-print-settings-ios-macos.md) (ネットワーク プリンター) を制御します。

- **AirPlay デバイスへの接続** - iOS デバイスのエンド ユーザーが接続できる [AirPlay デバイス](airplay-settings-ios.md) (Apple TV など) を制御します。

- **ロック画面のカスタム メッセージ** - ユーザーの iOS デバイスのロック画面に表示されるカスタム メッセージを構成して、既定のメッセージと置き換えます。 詳しくは、「[iOS デバイスで紛失モードをアクティブ化する](device-lost-mode.md)」を参照してください。

### <a name="restrict-push-notifications-for-ios-apps----723767---"></a>iOS アプリのプッシュ通知を制限する <!-- 723767 -->
Intune のデバイス制限プロファイルでは、iOS デバイスに対して次の[通知設定](app-notification-settings-ios.md)を構成できるようになりました。

- 指定したアプリの通知を完全に有効または無効にします。
- 指定したアプリの通知センターでの通知を有効または無効にします。
- アラートの種類を、**なし**、**バナー**、または**モーダル アラート**に指定します。
- このアプリに対してバッジを許可するかどうかを指定します。
- 通知サウンドを許可するかどうかを指定します。

### <a name="configure-ios-apps-to-run-in-single-app-mode-autonomously----737837---"></a>単一アプリ モードで自律的に実行するように iOS アプリを構成する<!-- 737837 -->
Intune のデバイス プロファイルを使って、[自律的シングル App モード](device-restrictions-ios.md#autonomous-single-app-mode-supervised-only)で指定したアプリを実行するように iOS デバイスを構成できるようになりました。 このモードを構成した場合、指定したアプリが実行されると、デバイスはそのアプリだけを実行できるようにロックされます。 たとえば、ユーザーがデバイスでテストを受けられるようにアプリを構成するような場合です。 アプリのアクションが完了した場合、または管理者がこのポリシーを削除した場合、デバイスは通常の状態に戻ります。

### <a name="configure-trusted-domains-for-email-and-web-browsing-on-ios-devices----723765---"></a>iOS デバイスでメールと Web ブラウザー用の信頼されたドメインを構成する <!-- 723765 -->
iOS デバイス制限プロファイルから、次の[ドメイン設定](device-restrictions-ios.md#domains)を構成できるようになりました。

- **[マークされていないメール ドメイン]** - ユーザーが送信または受信するメールのうち、ここで指定したドメインと一致しないものは、信頼されていないメールとしてマークされます。

- **[管理された Web ドメイン]** - ここで指定した URL からダウンロードされたドキュメントは、管理されているものと見なされます (Safari のみ)。  

- **[Safari パスワードの自動入力ドメイン]** - ユーザーは、ここで指定したパターンに一致する URL からのパスワードのみを Safari に保存できます。 この設定を使うには、デバイスが監視モードであり、複数ユーザー用に構成されていない必要があります。 (iOS 9.3 以降)


### <a name="vpp-apps-available-in-ios-company-portal----748782---"></a>iOS ポータル サイトで使用できる VPP アプリ <!-- 748782 -->
**利用可能な**インストールとして、iOS ボリューム購入 (VPP) アプリをエンド ユーザーに割り当てられるようになりました。 エンド ユーザーがアプリをインストールするには、Apple ストア アカウントが必要です。

### <a name="synchronize-ebooks-from-apple-vpp-store----800878---"></a>Apple VPP ストアから電子ブックを同期する <!-- 800878 -->
Intune と、Apple ボリューム購入プログラム ストアから購入した[本を同期](vpp-apps-ios.md)し、ユーザーに割り当てることができるようになりました。

### <a name="multi-user-management-for-samsung-knox-standard-devices----971988---"></a>Samsung KNOX Standard デバイスのマルチ ユーザー管理 <!-- 971988 -->
Samsung KNOX Standard を実行するデバイスが、Intune による[マルチ ユーザー管理](android-enroll.md)のサポート対象になりました。 つまり、エンド ユーザーは Azure Active Directory の資格情報を使ってデバイスのサインインとサインアウトを行うことができ、デバイスは使用中かどうかに関わらず一元管理されます。  サインインしたエンド ユーザーはアプリにアクセスできます。ポリシーがあれば、それが適用されます。 ユーザーがサインアウトすると、すべてのアプリ データがクリアされます。

### <a name="additional-windows-device-restriction-settings----818566---"></a>追加の Windows デバイス制限設定 <!-- 818566 -->
追加の Edge ブラウザー サポート、デバイス ロック画面のカスタマイズ、スタート メニューのカスタマイズ、Windows スポットライト検索セットの壁紙、プロキシ設定など、追加の [Windows デバイス制限設定](device-restrictions-windows-10.md)のサポートが追加されました。

### <a name="multi-user-support-for-windows-10-creators-update----822547---"></a>Windows 10 Creators Update のマルチユーザー サポート <!-- 822547 -->
Windows 10 Creators Update を実行し Azure Active Directory ドメインに参加しているデバイスの[マルチユーザー管理](windows-enroll.md)のサポートが追加されました。 つまり、異なる標準ユーザーが Azure AD 資格情報でデバイスにログインすると、ユーザー名に割り当てられているすべてのアプリとポリシーを受け取ります。 現時点では、アプリのインストールのようなセルフサービスのシナリオにポータル サイトは使用できません。

### <a name="fresh-start-for-windows-10-pcs---1004830---"></a>Windows 10 PC の Fresh Start <!-- 1004830 -->
Windows 10 PC で、新しい [Fresh Start デバイス アクション](device-fresh-start.md)が使用できるようになりました。  このアクションを発行すると、PC にインストールされたすべてのアプリが削除され、PC は Windows の最新バージョンに自動的に更新されます。 この機能は、新しい PC に付属することの多い事前インストール済み OEM アプリを削除するのに使うことができます。 このデバイス アクションを発行するときにユーザー データを保持するかどうかを構成できます。

### <a name="additional-windows-10-upgrade-paths----903672---"></a>Windows 10 の追加アップグレード パス <!-- 903672 -->
以下のエディションの Windows 10 にも、[エディション アップグレード ポリシーの作成によりデバイスをアップグレード](edition-upgrade-configure-windows-10.md)できるようになりました。

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N

### <a name="bulk-enroll-windows-10-devices----747607---"></a>Windows 10 デバイスを一括登録する <!-- 747607 -->
Windows 構成デザイナー (WCD) で Azure Active Directory と Intune に Windows 10 Creators Update を実行する多数のデバイスを参加させることができるようになりました。 Azure AD テナントの [一括 MDM 登録](windows-bulk-enroll.md) を有効にするには、Windows 構成デザイナーを使用して Azure AD テナントにデバイスを参加させるプロビジョニング パッケージを作成し、一括登録と管理を行う会社所有のデバイスにパッケージを適用します。 パッケージがデバイスに適用されると、デバイスは Azure AD に参加し、Intune に登録され、Azure AD ユーザーがログオンできる状態になります。  Azure AD ユーザーはこれらのデバイス上の標準ユーザーであり、割り当て済みのポリシーと必須アプリを受け取ります。 現在のところ、セルフ サービスとポータル サイトのシナリオはサポートされていません。

### <a name="new-mam-settings-for-pin-and-managed-storage-locations----581122-736644---"></a>暗証番号 (PIN) および管理対象記憶域の場所に対する新しい MAM 設定<!-- 581122, 736644 -->
モバイル アプリケーション管理 (MAM) シナリオに役立つ 2 つの新しいアプリ設定が使用できるようになりました。

- **[Disable app PIN when device PIN is managed (デバイスの PIN が管理されるときはアプリの PIN を無効にする)]** - 登録されたデバイスにデバイス暗証番号 (PIN) が存在するかどうかを検出し、存在する場合は、アプリ保護ポリシーによってトリガーされるアプリ PIN をバイパスします。 この設定を使うと、登録されたデバイスで MAM が有効なアプリケーションを開くユーザーに対して表示される PIN 要求の回数を減らすことができます。 この機能は、Android と iOS の両方で使うことができます。

- **[会社のデータを保存できるストレージ サービスの選択]** - 会社のデータを保存する記憶域の場所を指定できます。 ユーザーは選択したストレージ ロケーション サービスに保存できます。つまり、表示されていない他のすべてのストレージ ロケーション サービスはブロックされます。

  サポートされるストレージ ロケーション サービスの一覧は次のとおりです。

  - OneDrive
  - Business SharePoint Online
  - ローカル ストレージ

### <a name="help-desk-troubleshooting-portal----907448---"></a>ヘルプ デスクのトラブルシューティング ポータル<!-- 907448 -->
新しい[トラブルシューティング ポータル](help-desk-operators.md)を使用すると、ヘルプ デスクと Intune 管理者は、ユーザーと彼らのデバイスを表示して、Intune の技術的な問題を解決するタスクを実行できます。

## <a name="march-2017"></a>2017 年 3 月

### <a name="support-for-ios-lost-mode---431695--"></a>iOS 紛失モードのサポート<!--431695-->
iOS 9.3 以降のデバイスについて、Intune で**紛失モード**のサポートが追加されました。 デバイスをロックダウンしてすべての使用を回避し、デバイスのロック画面のメッセージおよび連絡先の電話番号を表示できるようになりました。

エンドユーザーは、管理者が紛失モードを無効にするまで、デバイスのロックを解除することはできません。 紛失モードを有効にした場合、**デバイスを探索する**アクションを使用して、Intune コンソールでマップ上にデバイスの地理的な場所を表示することができます。

会社所有の iOS デバイスを DEP で登録し、監視モードに設定している必要があります。

詳細については、「[Microsoft Intune デバイスの管理とは](device-management.md)」を参照してください。

### <a name="improvements-to-device-actions-report---677150--"></a>Device Actions レポートの機能強化 <!--677150-->
Device Actions レポートの機能が強化され、パフォーマンスが向上しました。 さらに、レポートを状態別にフィルター処理できるようになりました。 たとえば、レポートをフィルター処理して、完了したデバイス アクションのみを表示できます。

### <a name="custom-app-categories---748805--"></a>カスタム アプリのカテゴリ <!--748805-->
Intune に追加するアプリのカテゴリを作成、編集、および割り当てることができるようになりました。 現時点では、カテゴリは英語でのみ指定できます。
[Intune にアプリを追加する方法](apps-add.md)に関するページを参照してください。

### <a name="assign-lob-apps-to-users-with-unenrolled-devices---748823--"></a>登録していないデバイスを使用しているユーザーに LOB アプリを割り当てる <!--748823-->
デバイスが Intune に登録されているかどうかに関係なく、基幹業務アプリをストアからユーザーに割り当てられるようになりました。 ユーザーのデバイスが Intune に登録されていない場合は、ポータル サイト アプリではなく、ポータル Web サイトに移動してインストールする必要があります。

### <a name="new-compliance-reports---846671--"></a>新しいコンプライアンス レポート <!--846671-->
コンプライアンス レポートにより、会社内のコンプライアンスの状況を表示して、社内のユーザーがコンプライアンス関連の問題に直面したときに迅速にトラブルシューティングできるようになりました。 次の情報を表示できます。

- デバイスの総合的なコンプライアンスの状態
- 設定別のコンプライアンスの状態
- ポリシー別のコンプライアンスの状態

これらのレポートを使用して個々のデバイスをドリルダウンし、そのデバイスに影響を与えている特定の設定およびポリシーを確認することもできます。

<!--- You can now create an edition upgrade policy to upgrade devices to the following additional Windows 10 editions:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N --->

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Apple 登録シナリオへの直接アクセス <!--951869-->
Intune では、2017 年 1 月以降に作成された Intune アカウントについて、Azure Portal の Enroll Devices ワークロードを使用して、Apple 登録シナリオに直接アクセスできるようになりました。 これまでは、Apple 登録プレビューは Azure Portal のリンクからのみアクセスが可能でした。 2017 年 1 月より前に作成された Intune アカウントの場合は、これらの機能が Azure で利用可能になるまでの間、1 回限りの移行が必要です。 移行スケジュールはまだ発表されていませんが、詳細はできる限り早く発表します。 既存のアカウントでプレビューにアクセスできない場合は、試用アカウントを作成して、新しいエクスペリエンスをテストすることを強くお勧めします。


## <a name="february-2017"></a>2017 年 2 月

### <a name="ability-to-restrict-mobile-device-enrollment---747600-795782--"></a>モバイル デバイス登録を制限する機能 <!--747600, 795782-->
Intune では、登録を許可されるモバイル デバイス プラットフォームを制御する新しい登録制限が追加されています。 Intune では、モバイル デバイス プラットフォームが iOS、macOS、Android、Windows、Windows Mobile に分かれています。

* モバイル デバイスの登録を制限しても、PC クライアントの登録は制限されません。  
* iOS と Android のみに、個人所有デバイスの登録をブロックする 1 つの追加オプションがあります。

[この記事](https://docs.microsoft.com/intune-classic/deploy-use/manage-corporate-owned-devices)で説明されているように、IT 管理者が明示的に会社所有と指定しない限り、Intune はすべての新しいデバイスを個人所有としてマークします。

### <a name="view-all-actions-on-managed-devices---677150--"></a>管理対象デバイスのすべての操作を表示 <!--677150-->
新しい__デバイス操作__レポートには、デバイスでの出荷時の設定にリセットなどのリモート操作を実行したユーザーが表示され、さらにその操作の状態が表示されます。 「[デバイス管理とは](device-management.md)」を参照してください。

### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>管理されていないデバイスから割り当てられているアプリにアクセス可能 <!--664691-->
ポータル Web サイトでの設計変更に伴い、iOS と Android ユーザーは、管理されていないデバイスで "登録なしで使用可能" として割り当てられているアプリをインストールできるようになります。 Intune 資格情報を使用して、ユーザーはポータル Web サイトにログインし、割り当てられているアプリの一覧を表示することができます。 "登録なしで使用可能" なアプリのアプリ パッケージは、ポータル Web サイトからダウンロードできます。 この変更は、インストールするために登録が必要なアプリには影響しません。そのようなアプリをインストールする場合は、デバイスの登録が求められます。

### <a name="custom-app-categories---748805--"></a>カスタム アプリのカテゴリ <!--748805-->
Intune に追加するアプリのカテゴリを作成、編集、および割り当てることができるようになりました。 現時点では、カテゴリは英語でのみ指定できます。
[Intune にアプリを追加する方法](apps-add.md)に関するページを参照してください。

### <a name="display-device-categories---814654--"></a>デバイス カテゴリを表示する <!--814654-->
デバイスの一覧に、列としてデバイス カテゴリを表示できるようになりました。 デバイスのプロパティー ブレードのプロパティー セクションからカテゴリを編集することもできます。 [Intune にアプリを追加する方法](apps-add.md)に関するページを参照してください。

### <a name="configure-windows-update-for-business-settings---776716--"></a>ビジネス設定向けの Windows Update の構成<!--776716-->

サービスとしての Windows は、Windows 10 の更新プログラムを提供するための新しい方法です。 Windows 10 以降、すべての新しい機能更新プログラムと品質更新プログラムには、以前の更新プログラムすべての内容が含まれます。 つまり、最新の更新プログラムをインストールしている限り、Windows 10 デバイスが完全に最新の状態であることを把握できます。 以前のバージョンの Windows とは異なり、更新プログラムの一部ではなく全体をインストールすることが必要になります。

Windows Update for Business を使用することで、デバイスのグループに対して個々の更新プログラムを承認する必要がなくなるため、更新プログラム管理エクスペリエンスを簡略化できます。 更新プログラムの展開戦略を構成することで環境内のリスクを引き続き管理でき、さらに Windows Update により更新プログラムが適切なタイミングでインストールされるようになります。 Microsoft Intune では、デバイスでの更新プログラムの設定を構成でき、また更新プログラムのインストールを遅らせることができます。 Intune では更新プログラムは格納されず、更新プログラムのポリシー割り当てのみが格納されます。 デバイスは更新プログラムのため Windows Update に直接アクセスします。**Windows 10 更新プログラム リング**を構成し管理するには Intune を使用します。 更新プログラム リングには、Windows 10 更新プログラムがインストールされるタイミングと方法を構成する設定のグループが含まれています。 詳しくは、「[ビジネス設定向けの Windows Update の構成](windows-update-for-business-configure.md)」をご覧ください。
