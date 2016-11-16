---
title: "以前のリリース |Microsoft Intune"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 10/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 45dad14a-d412-488d-bb1e-ad990ea503df
ROBOTS: noindex,nofollow
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 1360a23647d6e66ba682548ad2b158bb9047265d
ms.openlocfilehash: ec1b118b2c7681f351d83f469b8c32e95f8fa71f


---

# 以前の Intune のリリース

## 2016 年 9 月
### 新しい機能、お知らせ、情報
* [Windows の条件付きアクセス](#windows-conditional-access)
* [iOS 10 のサポート](#ios-10-support)
* [Android と iOS のデバイス登録がなくても、アプリ ラッピング ツールで MAM がサポートされます](#app-wrapping-tool-supports-mam-without-device-enrollment-for-android-and-ios)
* [9 月に Intune グループから Azure Active Directory への移行が開始されます](#intune-groups-begin-transitioning-to-azure-active-directory-in-september)
* [Android デバイスを保護するため Lookout が統合されます](#lookout-integration-to-protect-android-devices)
* [Android、iOS、および Windows 用のポータル サイトの更新](#company-portal-updates)
* [Intune の用語集](#intune-glossary)
* [今後の更新情報](#whats-coming)

### Windows の条件付きアクセス
Intune 管理コンソールを通して条件付きアクセス ポリシーを作成することで、Windows PC が Exchange Online および SharePoint Online にアクセスするのをブロックできるようになりました。 また、Office デスクトップおよびユニバーサル アプリケーションへのアクセスをブロックする条件付きアクセス ポリシーを作成することもできます。

### iOS 10 のサポート
既存の Intune MDM と MAM のシナリオには、iOS 10 との互換性があります。 ヒントについては、[Intune サポート チームのブログ](https://blogs.technet.microsoft.com/intunesupport/2016/09/13/support-tip-intune-support-for-ios-10/)を参照してください。

### Android と iOS のデバイス登録がなくても、アプリ ラッピング ツールで MAM がサポートされます
Intune のアプリ ラッピング ツールは、iOS と Android の基幹業務 (LOB) アプリで Intune MAM を有効にするために使用するコマンド ライン ツールです。 Intune MAM SDK をお使いのアプリに組み込み、アプリが Intune を使用して展開された MAM ポリシーを適用できるようにするには、この方法が最も簡単です。 MAM ポリシーを使用すると、以下の操作を実行できます。

1. アプリのデータを暗号化します。
2. インフォメーション ワーカーがアプリを起動するときに PIN の入力を求めます。
3. アプリに対し、他の管理対象アプリにのみデータの転送を許可します。
4. アプリが Android、iTunes、および iCloud にデータをバックアップしないようにします。
5. 他の管理対象アプリとの間で切り取り、コピー、貼り付けのみを許可します。

新しくなった Intune のアプリ ラッピング ツールのパブリック プレビューでは、iOS および Android の内部 LOB アプリにデバイスを登録しなくても MAM がサポートされるようになりました。 つまり、エンドユーザーは MAM の有効な LOB アプリを使用するために、デバイスを Intune に登録する必要はありません。

誰でもパブリック プレビューのソフトウェアをテストしたり、次の msintuneappsdk の GitHub にある、役に立つドキュメントを参照したりできます。

http://www.github.com/msintuneappsdk/intune-app-wrapper-ios-preview

http://www.github.com/msintuneappsdk/intune-app-wrapper-android-preview

Android および iOS のプレリリース版 Microsoft Intune アプリのラッパーをインストールして使用するには、次を実行しておく必要があります。

* Android および iOS のプレリリース版 Microsoft Intune アプリ ラッピング ツールに関するマイクロソフト ソフトウェア ライセンス条項を確認します。
* 記録用にライセンス条項を印刷し、保持します。 Android のプレリリース版 Microsoft Intune アプリ ラッピング ツールをダウンロードして使用することで、このライセンス条項に同意することになります。 本ライセンス条項に同意されない場合、お客様は本ソフトウェアを使用できません。
<!---TFS 1235607--->

### 9 月に Intune グループから Azure Active Directory への移行が開始されます
一部の新しい Intune アカウントが Intune ユーザー グループではなく Azure Active Directory セキュリティ グループを使用します。 セキュリティ グループで作業していることは、Intune ポータル グループ ページに Azure 管理ポータルにリダイレクトするリンクが表示されることで確認できます。

### Android デバイスを保護するため Lookout が統合されます
Microsoft は、デバイス上のマルウェアやリスクの高いアプリなどを検出して Android モバイル デバイスを保護するため、Lookout のモバイル脅威保護ソリューションに統合します。 Lookout のソリューションにより、構成可能な脅威レベルを決定できます。 Intune に、Lookout によるリスク評価に基づいてデバイスのコンプライアンスを判断するためのコンプライアンス ポリシー ルールを作成できます。 条件付きアクセス ポリシーを使用すると、デバイスのコンプライアンス状態に基づいて、会社のリソースへのアクセスを許可したりブロックしたりできます。

非準拠デバイスのエンド ユーザーは登録が求められ、アクセス権を得るには Android デバイスへの Lookout for Work アプリケーションのインストール、アプリのアクティブ化、Lookout for Work アプリケーションで報告された驚異の修復が必要となります。 詳細については、「[Restrict access based on device, network, and application risk](restrict-access-based-on-device-network-app-risk.md)」 (デバイス、ネットワーク、アプリケーションのリスクに基づいてアクセスを制限する) を参照してください。


### ポータル サイトの更新

### Android
**Android 用ポータル サイトへの "通知" の追加**<br/>
Android 用ポータル サイトのホームページに新しい通知アイコンが追加されました。 このアイコンをタップすると [通知] ページが開き、ポータル サイト アプリの中でエンドユーザーが注目する必要のある項目がすべて表示されます。たとえば、デバイスのコンプライアンス非対応、登録の更新、登録のアクティブ化です。 iOS 版のポータル サイト アプリには既に、この通知機能が追加されています。 この新しい [通知] ページの導入に伴い、[会社アクセスのセットアップ] ページがポータル サイトの起動または再開のたびに表示されることはなくなりました (ただし、デバイスが登録済みである場合)。 管理者が独自にエンド ユーザー向けガイドを作成している場合は、必要に応じてこの変更をドキュメントに反映してください。 更新後のスクリーン ショットは[こちら](https://aka.ms/androidcpupdate)にあります。  
<!---TFS 1095560--->

**Company Portal for Android でフィードバックを送信する**</br>
Company Portal for Android のメニューには新しい項目が追加されています。 **[ヘルプとフィードバック]** をタップすると、次の 3 つのアクションが表示されます。
* **[ヘルプの表示]** を使用して、ポータル サイトに関する問題を IT 部門に報告します。 IT 部門では、電子メール クライアントを使用してメールを作成し、ポータル サイトのログをそのメールに添付します。 **[ヘルプの表示]** は **[設定]** ページの **[データを送信する]** 機能の代わりに使用されます。
* **[フィードバックの送信]** を使用して、ポータル サイト チームにフィードバックを送信します。
* **[アプリを評価]** を使用して、Google Play でポータル サイト アプリを評価またはレビューの対象のままとします。

### iOS
**iOS ポータル サイト アプリのサポートの変更**<br/>
iOS 用 Microsoft Intune ポータル サイト アプリのすべてのユーザーが、最新バージョンのアプリを使用するように要求されます。 新しいユーザーは最新バージョンのみをダウンロードでき、現在のユーザーは最新バージョンへの更新を求められます。 最新バージョンを使用するには iOS 8.0 以降が必要であり、デバイスで以前の iOS バージョンを実行している場合は、デバイスを iOS 8.0 以降に更新したうえでポータル サイト アプリを最新バージョンに更新するまで、ポータル サイトを使用できず、登録することもできません。 iOS 8.0 以前のバージョンを実行している登録済みのデバイスは、引き続き管理対象であり、Intune 管理コンソールに表示されます。
<!---TFS 1283165--->

**iOS エンドユーザーのアプリ取得方法の改善**<br/>
iOS 用ポータル サイト アプリのアプリ タイルに以下のような変更が行われ、ユーザーは単一の場所 (ポータル サイト Web サイト) のさまざまなビューですべてのアプリを確認できるようになりました。 Apple の制限では、基幹業務および管理対象アプリのストア アプリをポータル サイト アプリに一覧表示することが禁止されており、ユーザーが自分のすべてのアプリを見るには異なるビューを表示する必要があります。

- これまで **[会社のアプリ]** タイルはポータル サイト Web サイトの [すべて] タブにあるすべてのアプリの一覧と関連付けられており、今後も機能は同じです。 このタイル名は **[すべてのアプリ]** に変更されました。
- **[その他のアプリ]** タイルはこれまで、Apple がポータル サイト アプリに表示を許可しているすべてのアプリを一覧表示する、ポータル サイト アプリ内のビューに関連付けられていました。 このタイル名は **[おすすめアプリ]** に変更され、ユーザーがこのタイルをタップするとポータル サイト Web サイトの [おすすめ] タブが表示されるようになりました。
-  **[カテゴリ]** タイルはこれまで、アプリのカテゴリを一覧表示する、ポータル サイト アプリ内のビューに関連付けられていました。 このタイル名は変更されませんが、ポータル サイト Web サイトの [カテゴリ] タブに関連付けられるようになりました。
更新後のスクリーン ショットは[こちら](https://gallery.technet.microsoft.com/Improvements-in-how-iOS-d1104186)で確認することができます。
<!---TFS 1317133--->

**IT プロフェッショナルが iOS の管理対象ブラウザー アプリをインストールするようにアプリの要件を設定している場合は、そのダイアログを表示する**<br/>
管理対象ブラウザーでのみ Web クリップを開くように構成したものの、管理対象ブラウザーがデバイスにインストールされていない場合に、デバイスのポータル サイト アプリがユーザーに Web クリップをインストールする前に管理対象ブラウザーをインストールするように求めるダイアログが表示されるようになります。
<!---TFS 1228570--->

### Windows
**フィードバック ボタンを Windows Phone 8.1 ポータル サイト アプリに追加**<br/>
Windows Phone 8.1 ポータル サイト アプリでは、エンド ユーザーが新しい [フィードバックの送信] ボタンを使用してアプリに関するフィードバックを送ることができます。 フィードバックを送信するには、ポータル サイト アプリの画面の右下にある "..." メニューをタップし、[**フィードバックの送信**] をタップします。 フィードバックは匿名化して収集され、ポータル サイト アプリのユーザー エクスペリエンス向上に役立てられます。
<!---TFS 1317806--->

### Intune の用語集</br>
Intune 製品で使用されている用語を説明する新しい[用語集トピック](https://docs.microsoft.com/intune/understand-explore/intune-glossary)をライブラリに追加しました。


## 2016 年 8 月
### アプリ管理
<!---@Barry, I created the buckets of App management, Device management, etc but am not tied to them. Just wanted to break up and organize the feature list. If you're going to take over the Company Portal section, please talk to Stacie about how she's been organizing it. --->

__iOS 9.3 で表示されないアプリと表示されるアプリ__ iOS 9.3 以降を実行する監視対象デバイスでは、iOS の一般構成ポリシーの表示されないアプリと表示されるアプリのリストを使用して次のことができます。
- ユーザーに対して表示されないアプリの一覧を指定します。 ユーザーはこのようなアプリを表示または起動できません。
- ユーザーが表示および起動できるアプリの一覧を指定します。 他のアプリは表示または起動できません。

ユーザー自身が展開したアプリと、Messages や Notes などの iOS 組み込みアプリの両方を指定できます。 詳細については、「[Microsoft Intune の iOS ポリシー設定]( /intune/deploy-use/ios-policy-settings-in-microsoft-intune)」を参照してください。
<!---TFS 1279009 checked--->
__Samsung KNOX デバイスでの許可するアプリとブロックするアプリのポリシー__Samsung KNOX デバイスでは、次のいずれかを作成できるカスタム ポリシーを構成できます。
- デバイスでの実行をブロックするアプリの一覧。 ブロック リストで定義されているアプリは、インストールされている場合でも、デバイスでアクティブにできません。
- デバイスのユーザーが Google Play ストアからインストールできるアプリの一覧。 他のアプリはストアからインストールできません。

これらの設定は、Samsung KNOX を実行するデバイスでのみ使用できます。
詳細については、「[カスタム ポリシーを使用して、Samsung KNOX デバイス用のアプリを許可またはブロックする](/intune/deploy-use/custom-policy-to-allow-and-block-samsung-knox-apps)」を参照してください。
<!---TFS 1311629 checked --->
__モバイル アプリケーション管理 (MAM) ポリシーと互換性のある新しいアプリ__ [iOS](https://itunes.apple.com/app/yammer/id289559439?mt=8) および [Android](https://play.google.com/store/apps/details?id=com.yammer.v1) 向けの Yammer アプリは、デバイスが登録されていてもいなくても、[Intune モバイル アプリケーション管理 (MAM) ポリシーと](/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)互換性があります。

MAM と互換性のある全アプリの一覧については、[Microsoft Intune アプリケーション パートナー](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-partners)のサイトをご覧ください。
<!--- TFS 1252335 & 1252336 checked--->

<!--- I started putting TFS numbers in the What's Coming topic and found it helpful when updating the What's New. Up to you if you want to continue. --->

__Intune Viewer アプリ__ 新しい RMS 共有アプリのリリースに伴い、2016 年 8 月以降、次の Intune Viewer アプリを削除する予定です。
- Intune AV Viewer
- Intune PDF Viewer
- Google Play の Android 用 Intune Image Viewer

Intune Viewer アプリを使用する代わりに、[Android 用の新しい Rights Management アプリ (RMS 共有) ](/intune/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune#viewing-media-files-with-the-rights-management-sharing-app)を使用することをお勧めします。そうすることで、3 つのアプリを個別にではなく、1 つのアプリを展開して、Android デバイス上の企業ファイルを安全に表示することができます。 Intune Viewer アプリがサポートされなくなると、Google ストアから削除され、その後使用することができなくなります。

### デバイス管理
__Android 7.0 のサポート__ Intune は近日公開予定のモバイル デバイス向け Android 7.0 オペレーティング システムの "Day 0" サポートを提供します。
<!---TFS 1262053--->

__Google による Android 7.0 デバイスでのリモート パスコード リセット機能の削除__ Google は、IT 管理者やエンド ユーザーが Android 7.0 デバイスのパスコードをリモートでリセットする機能を削除しています。 これまでは、IT 管理者はユーザーのパスコードをリモートでリセットでき、エンド ユーザーはポータル サイトから自分のパスコードをリセットできました。

### ポータル サイトの更新
__ポータル Web サイト__
- **ポータル サイトから Microsoft へのフィードバック リンク** <br/>
ポータル サイトの Web サイトでは、エンドユーザーはページの下部にある新しい [フィードバック] リンクをタップして、サイトの操作性に関するフィードバックを Microsoft に送信できるようになります。 収集されて匿名化されたフィードバックは、Microsoft がポータル サイトの Web サイトについてユーザーの操作性を向上させるのに役立ちます。
<!--- TFS 1313657 checked--->

__iOS__
- **iOS Managed Browser の最小バージョンの 8.0 への更新**<br/>
iOS 用の Microsoft Intune Managed Browser アプリは、iOS 8.0 以降を実行するデバイスをサポートするように更新されました。 iOS 7.1 デバイスでは、既存の Managed Browser アプリを使用することができますが、新しい Managed Browser の機能にアクセスしてフル活用できるように、ユーザーに iOS 8.0 以降に更新することをお勧めしてください。  
<!---TFS 1313253 checked--->

### 今後の更新情報

__iOS 10 のサポート__ Intune は iOS 10 を完全サポートする予定です。 詳細については、iOS 10 のパブリック リリース後にお知らせします。

__Intune グループから Azure Active Directory グループへの移行 (2016年 9 月以降)__ Intune は、Intune でのユーザーとデバイスのグループとして Azure Active Directory (AAD) のセキュリティ グループを使用する、新しいグループ管理エクスペリエンスを作成しています。 これらのグループは、**新しい Azure ベースの Intune 管理ポータルの導入時**に、すべてのグループの管理、ポリシーの展開、およびプロファイルの展開に使用されます。

この新しいエクスペリエンスにより、サービス間でグループを複製する必要がなくなり、**新しい Azure Active Directory Premium (AADP) グループ機能の一部にアクセスすることができ** 、PowerShell および Graph を使用して拡張機能を提供します。 またこれにより、エンタープライズ モビリティ管理でのグループ管理エクスペリエンスも統合されます。

セキュリティ グループへの移行を有効にするため、**現在の管理コンソール**のエクスペリエンスにいくつかの変更が施されます。 **これらの変更と、AAD セキュリティ グループの使用については、Intune のドキュメントに記録されます**。

Intune の新規のお客様には、**現在のテナントに表示される前に、セキュリティ グループの変更の一部**が表示されます。

グループ管理の変更に加えて、**次の機能が廃止される予定です**。
- 新規グループ作成時のメンバーまたはグループの除外
- **グループ化を解除されたユーザー**と**グループ化を解除されたデバイス**のグループ
- サービス管理者の役割での**グループの管理**
- 通知ルールに対するカスタム グループベースの警告
- レポート内のグループのピボット
<!--- TFS 1295329--->

__Android 用ポータル サイトへの "通知" の追加__ Microsoft は、Android 用ポータル サイトに対する更新を 9 月にリリースし、ホームページ上に新しい**通知**アイコンを導入します。 このアイコンをタップすると、**通知**ページにアクセスし、デバイスのコンプライアンス非対応、登録の更新、および登録のアクティブ化などのポータル サイト アプリで注意が必要なすべての項目をエンド ユーザーに表示します。 iOS 用ポータル サイト アプリも使用している場合は、通知エクスペリエンスがすでに表示されます。 **通知**ページの導入に伴い、デバイスがすでに登録されている限り、Android 用ポータル サイトを起動または再開するたびに**会社アクセスのセットアップ**ページが表示されることはなくなります。 Microsoft は、多くのお客様がエンドユーザー ガイダンスを作成していることを把握しており、ガイダンスとスクリーンショットの更新が必要になる場合に事前に通知くださることに感謝いたします。 ドキュメントに今後のエクスペリエンスの変更を反映し、更新してください。 最新のスクリーンショットは、 https://aka.ms/androidcpupdate でご確認いただけます。  

__iOS エンドユーザーのアプリ取得方法の改善__ 9 月に、iOS 用ポータル サイト アプリのアプリ タイルに以下のような変更が行われ、ユーザーは単一の場所 (ポータル サイト Web サイト) のさまざまなビューですべてのアプリを確認できるようになる予定です。 現在、Apple の制限では、基幹業務および管理対象アプリのストア アプリをポータル サイト アプリに一覧表示することが禁止されており、ユーザーが自分のすべてのアプリを見るには異なるビューを表示する必要があります。

- 現時点では、**[会社のアプリ]** タイルはポータル サイト Web サイトの [すべて] タブにあるすべてのアプリのリストと関連付けられており、今後も機能は同じです。 このタイル名が **[すべてのアプリ]** に変更されます。
- **[その他のアプリ]** タイルは、現在、Apple がポータル サイト アプリに表示を許可しているすべてのアプリを一覧表示する、ポータル サイト アプリ内のビューに関連付けられています。 このタイル名は **[おすすめアプリ]** に変更され、ユーザーがこのタイルをタップするとポータル サイト Web サイトの [おすすめ] タブが表示されるようになります。
-  **[カテゴリ]** タイルは、現在、アプリのカテゴリを一覧表示する、ポータル サイト アプリ内のビューに関連付けられています。 このタイル名は変更されませんが、ポータル サイト Web サイトの [カテゴリ] タブに関連付けられるようになります。 更新後のスクリーン ショットは[こちら](https://gallery.technet.microsoft.com/Improvements-in-how-iOS-d1104186)で確認することができます。
<!---TFS 1317133--->

### クラウドのロードマップ
[クラウド プラットフォームのロードマップ](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)では、Intune の今後の開発に関する情報を入手できます。

### 廃止予定のサービス
<!---@Barry, we started listing service deprecations earlier this summer. --->
- **iOS ポータル サイト アプリのサポートの変更**<br/>
9 月には、iOS 用 Microsoft Intune ポータル サイト アプリのすべてのユーザーが、アプリの最新バージョンを使用するように要求されます。 新しいユーザーは最新バージョンのみをダウンロードでき、現在のユーザーは最新バージョンへの更新を求められます。 最新バージョンを使用するには iOS 8.0 以降が必要であり、デバイスで以前の iOS バージョンを実行している場合は、デバイスを iOS 8.0 以降に更新したうえでポータル サイト アプリを最新バージョンに更新するまで、ポータル サイトを使用できず、登録することもできません。 iOS 8.0 以前のバージョンを実行している登録済みのデバイスは、引き続き管理対象であり、Intune 管理コンソールに表示されます。  

- **iOS Managed Browser の最小バージョンの 8.0 への更新**<br/>
8 月、Intune は iOS 8.0 以降を実行するデバイスのみをサポートする、iOS 用の最新の Microsoft Intune Managed Browser アプリをリリースします。 iOS 7.1 デバイスでは、既存の Managed Browser アプリを使用することができますが、新しい Managed Browser の機能にアクセスしてフル活用できるように、ユーザーに iOS 8.0 以降に更新することをお勧めしてください。  
<!---TFS 1313253--->

- **Windows 8 および Windows Phone 8 用のポータル サイト アプリの廃止** <br/>
2016年 10 月以降、Microsoft Intune は Windows 8 および Windows Phone 8 ポータル サイト アプリのサポートを廃止します。 Microsoft Intune は、Windows Phone 8 プラットフォームのサポートも廃止します。 その結果、Windows Phone 8 デバイスの登録または更新はできなくなります。 既に登録されている Windows Phone 8 および Windows 8 デバイスは継続して管理できます。 デバイスへのアプリの配布を中断することなく続行するには、Windows Phone 8 および Windows 8 デバイスを Windows 8.1 および Windows Phone 8.1 に更新し、対応する Windows 8.1 および Windows Phone 8.1 のポータル サイト アプリを使用します。
<!---TFS 1255391--->

<!--- - **Custom Group Targeting of Notification Rules Removal.**<br/>
Intune notification rules define who an email alert will be sent to from Intune. Currently, you can configure notification rules to send emails to all users of devices in an Intune device group that you created. From around June 1st 2016 moving forward, targeting user-created groups will no longer be supported.

    Today, to target a notification rule to a group you created from the Microsoft Intune administration console, you would take the following steps:

    In the **Admin** workspace, click **Notification Rules** > **Create New Rule**

    In step two of the Create Notification Rule Wizard, select the device groups which the rule will target. This step, “select device groups”, is being removed from the Intune Console.

    The preliminary timeline for this change is as follows:
    - In August, 2016, new tenants will not see step two of the Create Notification Rule Wizard. Exiting tenants are unaffected.
    - Around September, 2016, some existing tenants will not see the “select device groups” in the wizard.
    - Around November, 2016, we expect that all tenants will not see the “select device groups” in the wizard.

--->

## 2016 年 7 月
### アプリ管理

__アプリのプロビジョニング プロファイルの更新エクスペリエンスを向上__ Apple iOS 基幹業務モバイル アプリは、プロビジョニング プロファイルを含み、証明書で署名されたコードと共に構築されます。 iOS デバイスでアプリを実行すると、iOS により iOS アプリの整合性の確認と、プロビジョニング プロファイルで定義されたポリシーの施行が行われます。

アプリの署名に使用するエンタープライズ署名証明書は、通常 3 年間は継続します。 ただし、プロビジョニング プロファイルは 1 年後に期限が切れます。 この更新により、証明書がまだ有効である期間中、Intune には、有効期限が近づいているアプリを持つデバイスに新しいプロビジョニング プロファイルのポリシーを事前に展開するツールが用意されます。 詳細については、「[Use iOS mobile provisioning profile policies to keep your line of business apps up to date (基幹業務アプリケーションを常に最新の状態に保つために iOS モバイル プロビジョニング プロファイル ポリシーを使用する)](/intune/deploy-use/ios-mobile-app-provisioning-profiles)」を参照してください。
<!--- TFS 1280247--->

__Intune アプリ用の Xamarin SDK の提供開始__ Intune アプリ SDK Xamarin コンポーネントを使用すると、Xamarin でビルドされたモバイル iOS および Android アプリで Intune のモバイル アプリ管理機能を有効にすることができます。 [Xamarin ストア](https://components.xamarin.com/view/Microsoft.Intune.MAM)または、[Microsoft Intune の Github ページ](https://github.com/msintuneappsdk)でコンポーネントを見つけることができます。
<!--- TFS 1061478 --->

### デバイス管理
__デバイス登録数上限の増加__ Intune は、構成可能なデバイスの最大登録数をユーザーごとに 5 から 15 デバイスまで増加しました。
<!---TFS 1289896 --->

__Intune クライアント ソフトウェアを実行する Windows PC のための TeamViewer の統合__
 Intune クライアントを実行する Windows PC の [TeamViewer](https://www.teamviewer.com) 統合により、Windows PC とのリモート アシスタント セッションを確立して、エンド ユーザーのヘルプ デスク部門をサポートできるようになります。 Windows 7、8、8.1、10 が対象となります。 詳細については、「[Microsoft Intune コンピューター クライアントを使用した一般的な Windows PC 管理タスク](/intune/deploy-use/common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client)」を参照してください。
<!---TFS 1284856--->

### ポータル サイトの更新

__ポータル Web サイト__
- **Windows デバイス登録時のエンドユーザー エクスペリエンスの向上**<br/>
条件付きアクセスを使用している場合の、ポータル サイト Web サイトで Windows 8.1、Windows 10 デスクトップ、および Windows 10 Mobile の登録手順が明確化されました。 今後は、「デバイス登録」および「社内参加」の手順が個別に表示されます。そのため、社内参加 (WPJ) の失敗後にデバイスの状態を確認し、プロセスを完了することが簡単になります。 この手順の分離により、IT 管理者のトラブルシューティングのプロセスも簡略化されることが見込まれます。 これまで、エンド ユーザーが登録しようとして、WPJ を除くすべての登録が成功した場合、登録されたデバイスがデバイス一覧に表示されないため識別できず、ユーザーの混乱の原因となっていました。

__Android__
- **Android 用ポータル サイト アプリ**<br/>
Android エンド ユーザーに自分のデバイスに必要な証明書がないことを示すエラー メッセージが表示される場合、[How to resolve this (この問題解決する方法)] ボタンをタップすると、欠落している証明書をインストールするための[手順](/intune/enduser/your-device-is-missing-a-required-certificate-android#your-device-is-missing-a-certificate-required-by-your-it-administrator)を取得できます。 ユーザーが手順を完了しても、追加の「証明書が見つかりません」というエラー メッセージが表示される場合は、IT 管理者に連絡し、この[リンク](/intune/troubleshoot/troubleshoot-device-enrollment-in-intune#android-certificate-issues)を提供することが求められます。このリンクには、証明書の問題を解決するために IT 管理者が使用できる手順が含まれています。

- **登録済みデバイスへのサイド ロード アプリのインストールの制限**<br/>
Android 用 Intune ポータル サイト アプリを使用してデバイスを Intune に登録している場合を除き、Android デバイスは、ポータル サイト Web サイトを通じてアプリケーションをインストールすることができなくなります。
<!---TFS 1299082--->

__iOS__
- **iOS ポータル サイト アプリのデバイス登録マネージャー アカウントへの変更**<br/>
パフォーマンスと拡張性を高めるために、Intune において、iOS のポータル サイト アプリの [**デバイス**] ウィンドウには今後、デバイス登録マネージャー (DEM) のデバイスの一部が表示されなくなります。 アプリを実行しているローカル デバイスのみ、ポータル サイト アプリ経由で登録されている場合にだけ表示されます。

ローカル デバイスに対する操作は DEM で実行できますが、他の登録デバイスのリモート管理は、Intune 管理コンソールから実行する必要があります。 また、Apple Device Enrollment Program または Apple Configurator ツールでの DEM アカウントの使用は廃止されます。 共有 iOS デバイスに関しては、どちらの登録手段も既にユーザーレスの登録がサポートされています。

共有デバイスのユーザーレスの登録が利用できない場合のみ DEM アカウントを使用してください。 詳細については、「[Microsoft Intune のデバイス登録マネージャーを使用した企業所有のデバイスの登録](https://docs.microsoft.com/en-us/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune)」を参照してください。
<!---TFS 1233681--->

### Windows 機能の名前の変更
- [Microsoft Passport for Windows](/intune/deploy-use/control-microsoft-passport-settings-on-devices-with-microsoft-intune) は **Windows Hello for Business** と呼ばれるようになりました。
- [エンタープライズ データ保護](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-intune)は **Windows Information Protection** と呼ばれるようになりました。

## 2016 年 6 月
### Intune のサービス正常性
Intune のサービス正常性に関する情報は他の Microsoft サービスと共に中央の場所に移動されました。 そのため、この情報は Office 365 管理ポータルの [サービス正常性] で参照できるようになりました。 詳細については、[このブログ投稿](https://blogs.technet.microsoft.com/enterprisemobility/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/)を参照してください。

### アプリ管理
- **Windows 10 の強化されたエンタープライズ データ ポリシー構成のエクスペリエンス。** Windows 10 のエンタープライズ データ保護ポリシー構成のエクスペリエンスが、アプリ規則の作成、ネットワーク境界の定義の指定、その他のエンタープライズ データ保護の設定などにおいて強化されました。 詳細については、「[Create an enterprise data protection (EDP) policy using Microsoft Intune](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-intune)」(Microsoft Intune を使用してエンタープライズ データ保護 (EDP) ポリシーを作成する) を参照してください。


### デバイス管理
- **望ましくない可能性があるアプリから保護するための Windows Defender ポリシー設定。** **望ましくない可能性があるアプリケーションの検出**という名前の新しい Windows Defender 設定が、Windows 10 Desktop と Mobile の全般構成ポリシーに追加されました。 この設定を使えば、Windows Defender によって望ましくない可能性があると判断されたソフトウェアの実行から、登録済みの Windows デスクトップ コンピューターを保護することができます。 このようなアプリケーションの実行からコンピューターを保護したり、望ましくない可能性があるアプリケーションがいつインストールされたのかを監査モードでレポートしたりできます。 詳細については、「[Microsoft Intune の Windows 10 ポリシー設定](https://docs.microsoft.com/en-us/intune/deploy-use/windows-10-policy-settings-in-microsoft-intune)」を参照してください。
<!---TFS 1244478--->

### 条件付きアクセス
- **Intune の Cisco ISE ネットワーク アクセス制御ポリシー。**  Cisco Identity Service Engine (ISE) 2.1 と Microsoft Intune の両方を使用する場合、ISE でネットワーク アクセス制御ポリシーを設定できます。

    このポリシーを使用すると、WiFi または VPN でネットワークに接続するデバイスは、アクセスが許可される前に、次の条件を満たすことが必要になります。

    * Intune で管理されていること
    * 展開されているすべての Intune コンプライアンス ポリシーに準拠していること

 準拠していないデバイスのエンド ユーザーは、アクセスを取得するために、デバイスを登録することと、コンプライアンス関連の問題を修正することを求められます。
- **ブラウザーの条件付きアクセス。** [Exchange Online](/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune) と [SharePoint Online](/intune/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune) 用の条件付きアクセス ポリシーを設定すると、管理下にあって、かつ条件を満たした iOS デバイスと Android デバイス上のサポートされる Web ブラウザーに、Exchange Online と SharePoint Online へのアクセスを限定することができます。 Outlook Web Access (OWA) や SharePoint サイトにエンド ユーザーが iOS または Android デバイスでサインインしようとすると、そのデバイスを Intune に登録するよう求めるメッセージが表示されます。また条件を満たしていないことが問題になっている場合は、その問題を解消してから、サインインを試行するように求められます。
<!---TFS 1175844--->

- **Dynamics CRM Online では、条件付きアクセスをサポートしています。** [Dynamics CRM Online](/intune/deploy-use/restrict-access-to-dynamics-crm-online-with-microsoft-intune) 用の条件付きアクセス ポリシーを設定すると、管理下にあって、かつ条件を満たした iOS デバイスと Android デバイスに、Dynamics CRM Online へのアクセスを限定することができます。 Dynamics CRM モバイル アプリにエンド ユーザーが iOS または Android でサインインしようとすると、Intune に登録するよう求めるメッセージが表示されます。また条件を満たしていないことが問題になっている場合は、その問題を修正してから、サインインを試行するように求められます。
<!---TFS1295358--->

### Intune 会社のポータルの更新

__Android 用ポータル サイト アプリ__

- IT 管理者が新しい [不明なソースからのアプリのインストールをデバイスが禁止することを必須にする (Android 4.0 以上)] ポリシーを適用すると、Android 4.0 以降のデバイスを使用するエンド ユーザーには、"不明なソースからのインストールを無効にする必要があります" というメッセージが表示されます。 ユーザーは、**[設定]** > **[セキュリティ]** を選択し、**[不明なソース]** を無効にする必要があります。 ユーザーは、コンプライアンス メッセージのリンクをクリックして、メッセージと、設定を無効にする必要がある理由に関する詳細[情報](/Intune/EndUser/you-are-asked-to-turn-off-unknown-sources-android)を確認できます。

- IT 管理者が新しい [セキュリティ上の脅威に対してデバイスがアプリのスキャンを有効にすることを必須にする (Android 4.0 以上)] ポリシーを適用すると、Android 4.0 以降のデバイスを使用するエンド ユーザーには、"端末をスキャンしてセキュリティ上の脅威を確認" というメッセージが表示されます。 ユーザーは、**[設定]** > **[Google]** > **[セキュリティ]** を選択し、**[端末をスキャンしてセキュリティ上の脅威を確認]** をオンにする必要があります。 ユーザーは、コンプライアンス メッセージのリンクをクリックして、メッセージと、設定を有効にする必要がある理由に関する詳細[情報](/Intune/EndUser/you-are-asked-to-turn-on-scan-device-for-security-threats-android)を確認できます。

- IT 管理者が新しい [USB デバッグの無効化を必須にする (Android 4.2 以上)] ポリシーを適用すると、Android 4.2 以降のデバイスを使用するエンド ユーザーには、"USB デバッグを無効にする必要があります" というメッセージが表示されます。 ユーザーは、**[設定]** > **[開発者オプション]** を選択し、**[USB デバッグ]** を無効にする必要があります。 ユーザーは、コンプライアンス メッセージのリンクをクリックして、メッセージと、設定を無効にする必要がある理由に関する詳細[情報](/Intune/EndUser/you-are-asked-to-turn-off-usb-debugging-android)を確認できます。

- IT 管理者が新しい [最低限の Android セキュリティ パッチ レベル (Android 6.0 以上)] ポリシーを適用すると、Android 6.0 以降のデバイスを使用するエンド ユーザーには、"このデバイスは Android の最小セキュリティ パッチ レベルを満たしていません" というメッセージが表示されます。 ユーザーは必要なセキュリティ パッチをインストールする必要があります。 ユーザーは、コンプライアンス メッセージのリンクをクリックして、必要なセキュリティ パッチをインストールする方法と、現在インストールされているセキュリティ パッチに関する[情報](/Intune/EndUser/you-are-asked-to-turn-on-scan-device-for-security-threats-android)を確認できます。

__iOS ポータル サイト アプリ__

- エンド ユーザーが基幹業務アプリをインストールするときの操作性が向上しています。 アプリのインストールに時間がかかる場合、ユーザーがデバイスを手動で同期させることによって、強制的に同期処理を再開することができます。 エンド ユーザー向けの手順については、「[デバイスを手動で同期する](/Intune/EndUser/sync-your-device-manually-ios)」を参照してください。

- iOS 向けの Microsoft Intune ポータル サイト アプリが更新され、iOS Version 8.0 以降をサポートするようになりました。 この更新は、デバイスで iOS Version 8.0 以降が実行されている場合にのみ、エンド ユーザーがポータル サイト アプリをインストールして Intune に新しいデバイスを登録できることを意味します。 サポートされていないバージョンの iOS が実行されているデバイスを登録済みの場合、ユーザーはそのデバイス上のポータル サイト アプリを引き続き使用できます。


## 2016 年 5 月
これらの機能はすべて、Configuration Manager と Intune のハイブリッド環境でもサポートされます。 新しいハイブリッド機能の詳細については、[ハイブリッド環境の新機能](https://technet.microsoft.com/en-us/library/mt718155.aspx)に関するページを参照してください。

### ドキュメント
プレビュー バージョンの [docs.microsoft.com](https://docs.microsoft.com/en-us/intune) へようこそ。
これはまったく新しい最新コンテンツのプラットフォームです。お客様がより簡単に Intune を理解し、使用できるように設計されています。
すべての新しい機能については、「[Introducing docs.microsoft.com](https://docs.microsoft.com/teamblog/introducing-docs-microsoft-com/)」 (docs.microsoft.com の概要) を参照してください。

### Intune のサービス正常性
Intune のサービス正常性に関する情報は他の Microsoft サービスと共に中央の場所に移動されました。 そのため、この情報は [Office 365 管理ポータル](https://portal.office.com/Admin/Default.aspx)の **[サービス正常性]** で参照できるようになりました。
詳細については、[このブログ投稿](https://blogs.technet.microsoft.com/microsoftintune/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/)を参照してください。


### アプリ管理
- **MAM SDK: PIN の長さの構成に対応。** デバイス PIN と同様、MAM アプリに使用する PIN の長さを指定できるようになります。 この場合エンド ユーザーは、管理者が設定した新しい制限に従う必要があります。 入力文字数が増える分、PIN 画面の外観が若干調整されます。 詳細については、「[MAM policy settings for Android](/intune/deploy-use/android-mam-policy-settings)」 (Android 用 MAM ポリシー設定) および「[MAM policy settings for iOS](/intune/deploy-use/ios-mam-policy-settings)」 (iOS 用 MAM ポリシー設定) を参照してください。

- **iOS および Android 用 Skype for Business。** Skype for Business を [MAM の対象にできるようになりました (登録ポリシー不要)](/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune)。 ユーザーがログインすると、MAM ポリシーが適用されます。

- **MAM ポリシーで管理できるようになった新しいアプリ。** Android 用の Microsoft Word、Excel、および PowerPoint の各アプリを、Intune に登録されていないデバイス上の MAM ポリシーに関連付けられるようになりました。 サポートされているアプリの完全なリストについては、[Microsoft Intune アプリケーション パートナー](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx) ページの Microsoft Intune モバイル アプリケーション ギャラリーを参照してください。


### ポータル サイトの更新

#### Android 用ポータル サイト アプリ
- **エンドユーザーへのトースト通知**: エンドユーザーがポータル サイトからデバイスの登録または削除を行う際に、Android ポータル サイト アプリからのトースト通知が表示されるようになりました。

- **Android ポータル サイト アプリでのデバイス登録マネージャー アカウントへの変更。** パフォーマンスと拡張性を高めるために、Intune の Android ポータル サイト アプリの [デバイス] ペインには、すべてのデバイス登録マネージャー (DEM) デバイスが表示されなくなります。 アプリを実行しているローカル デバイスのみ、ポータル サイト アプリ経由で登録されている場合にだけ表示されます。 ローカル デバイスに対する操作は DEM で実行できますが、他の登録デバイスのリモート管理は、Intune 管理コンソールから実行する必要があります。

#### ポータル Web サイト
- **ポータル Web サイト: デバイス ID バナーによってエンド ユーザーへの情報提供を拡充。** エンド ユーザーは、ポータル Web サイトを使用する際に選択したデバイスをより簡単に特定できるようになりました。 間違ったデバイスを選択した場合は、ホーム ページ バナーの **[ここをタップ]** リンクをタップして正しいデバイスを選択できます。

### 廃止予定のサービス
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


## 2016 年 4 月
これらの機能はすべて、Configuration Manager と Intune のハイブリッド環境でもサポートされます。

### アプリ管理
- **MAM ユーザー コンプライアンス。**
Azure Active Directory (AAD) テナント内の任意のユーザーについて、アプリケーション管理ポリシーの[状態](/intune/deploy-use/monitor-mobile-app-management-policies-with-Microsoft-Intune)を表示できるようになりました。 以下は、必要な操作の例です。
   - [デバイス]
   - デバイス上のアプリ

   ステータス値:

   **チェックイン**: ポリシーがユーザーに展開されていること、仕事のコンテキストでアプリが使用されていること、正常にポリシーが配信されたことを示します。

    **チェックイン未**: ポリシーはユーザーに展開されましたが、それ以降にアプリが仕事のコンテキストで使用されていないことを示します。


- **Outlook 連絡先の同期 (Android) ができないよう MAM によって制御。**
[モバイル アプリケーションの管理](/intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune)に、デバイスを登録せずに行える新しい設定が追加されました。 この設定を使用して、Android デバイス上のネイティブのアドレス帳と連絡先との同期をアプリケーションに禁止することができます。 この設定を有効にすると、対象アプリケーションはネイティブのアドレス帳に連絡先を保存できなくなります。 この設定を無効にすると、対象アプリケーションはネイティブのアドレス帳に連絡先を保存できるようになります。 [デバイスまたはアプリをリモートからワイプ](/intune/deploy-use/wipe-managed-company-app-data-with-Microsoft-Intune)すると、ネイティブのアドレス帳に保存されているすべての連絡先が削除されます。 この新しい設定は最初に、Android デバイスの Outlook アプリケーションでサポートされます。

### デバイス管理
- **会社が所有するデバイスの電話番号の識別。** 会社の所有として分類される電話は今後、完全な電話番号で識別されます (モバイル デバイスのインベントリ レポートを実行するときなど)。 BYOD デバイスの電話番号は引き続き **** でマスクされ、表示されるのは最後の 4 桁のみとなります。


### ポータル サイトの更新
**Android 用ポータル サイト アプリ** まだ Intune にデバイスを登録していないユーザーや適切な証明書がインストールされていないユーザーには、"必要な証明書がデバイスに見つからないため、サインインできません" というメッセージが表示され、Android ポータル サイト アプリにサインインできなくなります。 このメッセージには "この問題を解決する方法" というリンクが表示され、ユーザーはこれをタップして証明書のインストール手順を参照できます。 エンド ユーザーが問題を解決するための手順については、「[デバイスに必要な証明書がない](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_cert_missing)」を参照してください。

**iOS ポータル サイト アプリ** 引き下げて更新する操作に対応しました。ホーム画面上のコンテンツ (アプリやデバイスの一覧、IT 連絡先情報など) をこの操作で最新の情報に更新することができます。 準拠状況やポリシー情報については、引き下げて更新する操作ではチェックされません。これらの情報をチェックするには、現在のデバイスのタイルを選択し、**[同期]** ボタンをタップしてください。

**Windows 10 Mobile と Windows Phone 8.1 ポータル サイト アプリ** エンド ユーザーが基幹業務アプリをインストールするときの操作性が向上しています。 アプリのインストールに時間がかかる場合、ユーザーがデバイスを手動で同期させることによって、強制的に同期処理を再開することができます。 エンド ユーザー向けの手順については、[デバイスを手動で同期させることによってアプリのインストールを高速化する方法](https://technet.microsoft.com/library/mt427782.aspx#BKMK_win10m_wp81_sync_manually)に関するページを参照してください。

**ポータル サイト Web サイト** Windows 10 Mobile ユーザーまたは Windows Phone 8.1 ユーザーが基幹業務アプリをインストールするときに、今後は新しく以下のステータスが表示されます。これらのステータスによって、インストールの状態を従来よりも詳しく知ることができます。

* **[デバイスが同期されるのを待機しています]** – ユーザーが [インストール] をタップした後、デバイスが Intune インフラストラクチャとの同期を試みます。 インストールが完了するためには、同期が完了している必要があります。 "デバイスが同期されるのを待機しています" のメッセージはリンクになっていて、同期処理に時間がかかっていたり、途中で止まったりした場合に、ユーザーがこのリンクをタップすると、デバイスを手動で Intune と同期させるための[手順](https://technet.microsoft.com/library/mt590895.aspx#BKMK_iwp_sync_manually)が表示されます。
* **[ダウンロード中]** – ユーザーのダウンロード要求が処理されています。デバイスは、アプリのダウンロードとインストールを実行しています。

これらのステータスが追加されるまでは、表示されるステータスが "インストール中" のみで、これが何時間も画面に表示された状態に陥ることもあったため、アプリのインストールに時間がかかった場合にユーザーが混乱する原因となっていました。 新しくステータスが追加されることで、ユーザーはサポートに問い合わせなくても、"デバイスが同期されるのを待機しています" のリンクをタップし、画面の指示に従うことで同期処理を強制的に再開できるようになります。

>[!div class="step-by-step"]

>[&larr; **Intune の新機能**](whats-new-in-microsoft-intune.md)    



<!--HONumber=Oct16_HO3-->


