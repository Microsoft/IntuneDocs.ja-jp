---
title: "新機能の公開履歴 | Microsoft Intune"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 11/11/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ed2db991-4729-49a7-a1e6-be2ffa0d03d1
ROBOTS: noindex,nofollow
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 861b5ea3bb0772d2853942e2b3f11f607dad3774
ms.openlocfilehash: 25128cfe93280e38a03779a7e6f38ddeb3c15612


---
# <a name="whats-new-archive"></a>新機能の公開履歴

このページでは、「[Microsoft Intune の新機能](whats-new-in-microsoft-intune.md)」で最近行われた発表をアーカイブしています。

## <a name="september-2016"></a>2016 年 9 月
### <a name="new-features-announcements-and-information"></a>新しい機能、お知らせ、情報
* [Windows の条件付きアクセス](#windows-conditional-access)
* [iOS 10 のサポート](#ios-10-support)
* [Android と iOS のデバイス登録がなくても、アプリ ラッピング ツールで MAM がサポートされます](#app-wrapping-tool-supports-mam-without-device-enrollment-for-android-and-ios)
* [9 月に Intune グループから Azure Active Directory への移行が開始されます](#intune-groups-begin-transitioning-to-azure-active-directory-in-september)
* [Android デバイスを保護するため Lookout が統合されます](#lookout-integration-to-protect-android-devices)
* [Android、iOS、および Windows 用のポータル サイトの更新](#company-portal-updates)
* [Intune の用語集](#intune-glossary)
* [今後の更新情報](#whats-coming)

### <a name="windows-conditional-access"></a>Windows の条件付きアクセス
Intune 管理コンソールを通して条件付きアクセス ポリシーを作成することで、Windows PC が Exchange Online および SharePoint Online にアクセスするのをブロックできるようになりました。 また、Office デスクトップおよびユニバーサル アプリケーションへのアクセスをブロックする条件付きアクセス ポリシーを作成することもできます。

### <a name="ios-10-support"></a>iOS 10 のサポート
既存の Intune MDM と MAM のシナリオには、iOS 10 との互換性があります。 ヒントについては、[Intune サポート チームのブログ](https://blogs.technet.microsoft.com/intunesupport/2016/09/13/support-tip-intune-support-for-ios-10/)を参照してください。

### <a name="app-wrapping-tool-supports-mam-without-device-enrollment-for-android-and-ios"></a>Android と iOS のデバイス登録がなくても、アプリ ラッピング ツールで MAM がサポートされます
Intune のアプリ ラッピング ツールは、iOS と Android の基幹業務 (LOB) アプリで Intune MAM を有効にするために使用するコマンド ライン ツールです。 Intune MAM SDK をお使いのアプリに組み込み、アプリが Intune を使用して展開された MAM ポリシーを適用できるようにするには、この方法が最も簡単です。 MAM ポリシーを使用すると、以下の操作を実行できます。

1. アプリのデータを暗号化します。
2. インフォメーション ワーカーがアプリを起動するときに PIN の入力を求めます。
3. アプリに対し、他の管理対象アプリにのみデータの転送を許可します。
4. アプリが Android、iTunes、および iCloud にデータをバックアップしないようにします。
5. 他の管理対象アプリとの間で切り取り、コピー、貼り付けのみを許可します。

新しくなった Intune のアプリ ラッピング ツールのパブリック プレビューでは、iOS および Android の内部 LOB アプリにデバイスを登録しなくても MAM がサポートされるようになりました。 つまり、エンドユーザーは MAM の有効な LOB アプリを使用するために、デバイスを Intune に登録する必要はありません。

誰でもパブリック プレビューのソフトウェアをテストしたり、次の msintuneappsdk の GitHub にある、役に立つドキュメントを参照したりできます。

<p style="margin-left: 40px">http://www.github.com/msintuneappsdk/intune-app-wrapper-ios-preview

<p style="margin-left: 40px">http://www.github.com/msintuneappsdk/intune-app-wrapper-android-preview

Android および iOS のプレリリース版 Microsoft Intune アプリのラッパーをインストールして使用するには、次を実行しておく必要があります。

* Android および iOS のプレリリース版 Microsoft Intune アプリ ラッピング ツールに関するマイクロソフト ソフトウェア ライセンス条項を確認します。
* 記録用にライセンス条項を印刷し、保持します。 Android のプレリリース版 Microsoft Intune アプリ ラッピング ツールをダウンロードして使用することで、このライセンス条項に同意することになります。 本ライセンス条項に同意されない場合、お客様は本ソフトウェアを使用できません。
<!---TFS 1235607--->

### <a name="intune-groups-begin-transitioning-to-azure-active-directory-in-september"></a>9 月に Intune グループから Azure Active Directory への移行が開始されます
一部の新しい Intune アカウントが Intune ユーザー グループではなく Azure Active Directory セキュリティ グループを使用します。 セキュリティ グループで作業していることは、Intune ポータル グループ ページに Azure 管理ポータルにリダイレクトするリンクが表示されることで確認できます。

### <a name="lookout-integration-to-protect-android-devices"></a>Android デバイスを保護するため Lookout が統合されます
Microsoft は、デバイス上のマルウェアやリスクの高いアプリなどを検出して Android モバイル デバイスを保護するため、Lookout のモバイル脅威保護ソリューションに統合します。 Lookout のソリューションにより、構成可能な脅威レベルを決定できます。 Intune に、Lookout によるリスク評価に基づいてデバイスのコンプライアンスを判断するためのコンプライアンス ポリシー ルールを作成できます。 条件付きアクセス ポリシーを使用すると、デバイスのコンプライアンス状態に基づいて、会社のリソースへのアクセスを許可したりブロックしたりできます。

非準拠デバイスのエンド ユーザーは登録が求められ、アクセス権を得るには Android デバイスへの Lookout for Work アプリケーションのインストール、アプリのアクティブ化、Lookout for Work アプリケーションで報告された驚異の修復が必要となります。 詳細については、「[Restrict access based on device, network, and application risk](restrict-access-based-on-device-network-app-risk.md)」 (デバイス、ネットワーク、アプリケーションのリスクに基づいてアクセスを制限する) を参照してください。


### <a name="company-portal-updates"></a>ポータル サイトの更新

__Android__

<p style="margin-left: 40px">**Android 用ポータル サイトへの "通知" の追加**<br/>
<p style="margin-left: 40px">Android 用ポータル サイトのホームページに新しい通知アイコンが追加されました。 このアイコンをタップすると [通知] ページが開き、ポータル サイト アプリの中でエンドユーザーが注目する必要のある項目がすべて表示されます。たとえば、デバイスのコンプライアンス非対応、登録の更新、登録のアクティブ化です。 iOS 版のポータル サイト アプリには既に、この通知機能が追加されています。 この新しい [通知] ページの導入に伴い、[会社アクセスのセットアップ] ページがポータル サイトの起動または再開のたびに表示されることはなくなりました (ただし、デバイスが登録済みである場合)。 管理者が独自にエンド ユーザー向けガイドを作成している場合は、必要に応じてこの変更をドキュメントに反映してください。 更新後のスクリーン ショットは[こちら](https://aka.ms/androidcpupdate)にあります。  

__iOS__
<p style="margin-left: 40px">**iOS ポータル サイト アプリのサポートの変更**<br/>
<p style="margin-left: 40px">iOS 用 Microsoft Intune ポータル サイト アプリのすべてのユーザーが、最新バージョンのアプリを使用するように要求されます。 新しいユーザーは最新バージョンのみをダウンロードでき、現在のユーザーは最新バージョンへの更新を求められます。 最新バージョンを使用するには iOS 8.0 以降が必要であり、デバイスで以前の iOS バージョンを実行している場合は、デバイスを iOS 8.0 以降に更新したうえでポータル サイト アプリを最新バージョンに更新するまで、ポータル サイトを使用できず、登録することもできません。 iOS 8.0 以前のバージョンを実行している登録済みのデバイスは、引き続き管理対象であり、Intune 管理コンソールに表示されます。
<!---TFS 1283165--->

<p style="margin-left: 40px">**iOS エンドユーザーのアプリ取得方法の改善**<br/>
<p style="margin-left: 40px">iOS 用ポータル サイト アプリのアプリ タイルに以下のような変更が行われ、ユーザーは単一の場所 (ポータル サイト Web サイト) のさまざまなビューですべてのアプリを確認できるようになりました。 Apple の制限では、基幹業務および管理対象アプリのストア アプリをポータル サイト アプリに一覧表示することが禁止されており、ユーザーが自分のすべてのアプリを見るには異なるビューを表示する必要があります。

<p style="margin-left: 40px">これまで **[会社のアプリ]** タイルはポータル サイト Web サイトの [すべて] タブにあるすべてのアプリの一覧と関連付けられており、今後も機能は同じです。 このタイル名は **[すべてのアプリ]** に変更されました。

<p style="margin-left: 40px">**[その他のアプリ]** タイルはこれまで、Apple がポータル サイト アプリに表示を許可しているすべてのアプリを一覧表示する、ポータル サイト アプリ内のビューに関連付けられていました。 このタイル名は **[おすすめアプリ]** に変更され、ユーザーがこのタイルをタップするとポータル サイト Web サイトの [おすすめ] タブが表示されるようになりました。

<p style="margin-left: 40px">**[カテゴリ]** タイルはこれまで、アプリのカテゴリを一覧表示する、ポータル サイト アプリ内のビューに関連付けられていました。 このタイル名は変更されませんが、ポータル サイト Web サイトの [カテゴリ] タブに関連付けられるようになりました。 更新後のスクリーン ショットは[こちら](https://gallery.technet.microsoft.com/Improvements-in-how-iOS-d1104186)で確認することができます。
  <!---TFS 1317133--->

<p style="margin-left: 40px">**IT プロフェッショナルが iOS の管理対象ブラウザー アプリをインストールするようにアプリの要件を設定している場合は、そのダイアログを表示する**<br/>
<p style="margin-left: 40px">管理対象ブラウザーでのみ Web クリップを開くように構成したものの、管理対象ブラウザーがデバイスにインストールされていない場合に、デバイスのポータル サイト アプリがユーザーに Web クリップをインストールする前に管理対象ブラウザーをインストールするように求めるダイアログが表示されるようになります。
  <!---TFS 1228570--->

__Windows__
<p style="margin-left: 40px">**フィードバック ボタンを Windows Phone 8.1 ポータル サイト アプリに追加**<br/>
<p style="margin-left: 40px">Windows Phone 8.1 ポータル サイト アプリでは、エンド ユーザーが新しい [フィードバックの送信] ボタンを使用してアプリに関するフィードバックを送ることができます。 フィードバックを送信するには、ポータル サイト アプリの画面の右下にある "..." メニューをタップし、[**フィードバックの送信**] をタップします。 フィードバックは匿名化して収集され、ポータル サイト アプリのユーザー エクスペリエンス向上に役立てられます。
<!---TFS 1317806--->

### <a name="intune-glossarybr"></a>Intune の用語集</br>
Intune 製品で使用されている用語を説明する新しい[用語集トピック](https://docs.microsoft.com/intune/understand-explore/intune-glossary)をライブラリに追加しました。

### <a name="see-also"></a>関連項目
最近の開発状況について詳しくは、「[Microsoft Intune の新機能](whats-new-in-microsoft-intune.md)」をご覧ください。



<!--HONumber=Nov16_HO2-->


