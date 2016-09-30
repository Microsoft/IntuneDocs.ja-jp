---
title: "新機能 | Microsoft Intune"
description: "Microsoft Intune の今月の新機能と過去のリリースの情報について説明します"
keywords: 
author: barlanmsft
manager: angrobe
ms.date: 09/22/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: mamoriss
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 5b3256852431efb83fb2cc9fa067dd3f4a68a050
ms.openlocfilehash: cef0a26204a22c95d2b639500246e435fcf7f9f7


---

# Microsoft Intune の新機能 -- 9 月
Microsoft Intune の今回のリリースの新機能について説明します。 また、過去のリリースに関する情報だけでなく、準備する必要がある今後の変更についても説明します。

これらのすべての機能は、最終的にハイブリッド環境 (Configuration Manager と Intune の共存環境) でサポートされるようになります。 最新のハイブリッド機能の詳細については、[ハイブリッド環境の新機能に関するページ](https://technet.microsoft.com/library/mt718155.aspx)を参照してください。
<!---@Barry, the above blurb stays in each version, but make sure Tyler signs off each time. Also, remember to set the ms.date in the metadata to the sprint release. --->

>[!IMPORTANT]
>ブログ記事: Ensuring mobile devices are up to date using Microsoft Intune (Microsoft Intune を使ってモバイル デバイスを確実に更新する)<br>
>iOS デバイスへの "Trident" マルウェアによる最近の攻撃を踏まえ、ブログ記事「[Ensuring mobile devices are up to date using Microsoft Intune](https://blogs.technet.microsoft.com/enterprisemobility/2016/08/26/ensuring-mobile-devices-are-up-to-date-using-microsoft-intune/)」(Microsoft Intune でモバイル デバイスを確実に更新する) を新たに公開しました。デバイスを安全に、かつ最新の状態に保つために役立つ Intune のさまざまな使い方について説明しています。

## iOS 10 のサポート
既存の Intune MDM と MAM のシナリオには、iOS 10 との互換性があります。 ヒントについては、[Intune サポート チームのブログ](https://blogs.technet.microsoft.com/intunesupport/2016/09/13/support-tip-intune-support-for-ios-10/)を参照してください。

## Android と iOS のデバイス登録がなくても、アプリ ラッピング ツールで MAM がサポートされます
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

## 9 月に Intune グループから Azure Active Directory への移行が開始されます
一部の新しい Intune アカウントが Intune ユーザー グループではなく Azure Active Directory セキュリティ グループを使用します。 セキュリティ グループで作業していることは、Intune ポータル グループ ページに Azure 管理ポータルにリダイレクトするリンクが表示されることで確認できます。

## Android デバイスを保護するため Lookout が統合されます
Microsoft は、デバイス上のマルウェアやリスクの高いアプリなどを検出して Android モバイル デバイスを保護するため、Lookout のモバイル脅威保護ソリューションに統合します。 Lookout のソリューションにより、構成可能な脅威レベルを決定できます。 Intune に、Lookout によるリスク評価に基づいてデバイスのコンプライアンスを判断するためのコンプライアンス ポリシー ルールを作成できます。 条件付きアクセス ポリシーを使用すると、デバイスのコンプライアンス状態に基づいて、会社のリソースへのアクセスを許可したりブロックしたりできます。

非準拠デバイスのエンド ユーザーは登録が求められ、アクセス権を得るには Android デバイスへの Lookout for Work アプリケーションのインストール、アプリのアクティブ化、Lookout for Work アプリケーションで報告された驚異の修復が必要となります。 詳細については、「[Restrict access based on device, network, and application risk](restrict-access-based-on-device-network-app-risk.md)」 (デバイス、ネットワーク、アプリケーションのリスクに基づいてアクセスを制限する) を参照してください。


## ポータル サイトの更新

### Android

**Android 用ポータル サイトへの "通知" の追加**<br/>
Android 用ポータル サイトのホームページに新しい通知アイコンが追加されました。 このアイコンをタップすると [通知] ページが開き、ポータル サイト アプリの中でエンドユーザーが注目する必要のある項目がすべて表示されます。たとえば、デバイスのコンプライアンス非対応、登録の更新、登録のアクティブ化です。 iOS 版のポータル サイト アプリには既に、この通知機能が追加されています。 この新しい [通知] ページの導入に伴い、[会社アクセスのセットアップ] ページがポータル サイトの起動または再開のたびに表示されることはなくなりました (ただし、デバイスが登録済みである場合)。 管理者が独自にエンド ユーザー向けガイドを作成している場合は、必要に応じてこの変更をドキュメントに反映してください。 更新後のスクリーン ショットは[こちら](https://aka.ms/androidcpupdate)にあります。  
<!---TFS 1095560--->

**Company Portal for Android でフィードバックを送信する**</br>
Company Portal for Android のメニューには新しい項目が追加されています。 **[ヘルプとフィードバック]** をタップすると、次の 3 つのアクションが表示されます。
* **[ヘルプの表示]** を使用して、Company Portal に関する問題を IT 部門に報告します。 IT 部門では、電子メール クライアントを使用してメールを作成し、Company Portal のログをそのメールに添付します。 **[ヘルプの表示]** は **[設定]** ページの **[データを送信する]** 機能の代わりに使用されます。
* **[フィードバックの送信]** を使用して、Company Portal チームにフィードバックを送信します。
* **[アプリを評価]** を使用して、Google Play で Company Portal アプリを評価またはレビューの対象のままとします。

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


## 今後の更新情報

### Intune グループから Azure Active Directory グループへの移行
Intune は、Intune でのユーザーとデバイスのグループとして Azure Active Directory (AAD) のセキュリティ グループを使用する、新しいグループ管理エクスペリエンスを作成しています。 これらのグループは、**新しい Azure ベースの Intune 管理ポータルの導入時**に、すべてのグループの管理、ポリシーの展開、およびプロファイルの展開に使用されます。

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

### Exchange Online および SharePoint Online の新しい条件付きアクセス アプリ ポリシー
Outlook、Word、Excel、OneDrive などの Office モバイル アプリからしかアクセスできないように、Exchange Online と SharePoint Online へのアクセスを制限できるようになります。 この新機能は組み込みのメール クライアントや Intune MAM ポリシーが構成されていない他のアプリへのアクセスをブロックできるため、Intune のモバイル アプリ管理 (MAM) ポリシーと組み合わせると効果的です。 これにより、ユーザーが組織のデータにアクセスする際に、Intune MAM を使用して保護できるアプリを使用するようになります。 Intune モバイル アプリ管理は、Azure ポータルから使用することができます。 [設定] ブレードの新しい [条件付きアクセス] セクションを探してください。



### 廃止予定のサービス

- **Windows 8 および Windows Phone 8 用のポータル サイト アプリの廃止** <br/>
2016年 10 月以降、Microsoft Intune は Windows 8 および Windows Phone 8 ポータル サイト アプリのサポートを廃止します。 Microsoft Intune は、Windows Phone 8 プラットフォームのサポートも廃止します。 その結果、Windows Phone 8 デバイスの登録または更新はできなくなります。 既に登録されている Windows Phone 8 および Windows 8 デバイスは継続して管理できます。 デバイスへのアプリの配布を中断することなく続行するには、Windows Phone 8 および Windows 8 デバイスを Windows 8.1 および Windows Phone 8.1 に更新し、対応する Windows 8.1 および Windows Phone 8.1 のポータル サイト アプリを使用します。



### クラウドのロードマップ
[クラウド プラットフォームのロードマップ](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)では、Intune の今後の開発に関する情報を入手できます。


## 以前の Intune のリリース
過去 6 か月間に公開された Intune のリリースについては、「[以前の Intune のリリース](previous-intune-releases.md)」の記事をご覧ください。

### 関連項目
* [Microsoft Intune のブログ](http://go.microsoft.com/fwlink/?LinkID=273882)
* [クラウド プラットフォームのロードマップ](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)



<!--HONumber=Sep16_HO4-->


