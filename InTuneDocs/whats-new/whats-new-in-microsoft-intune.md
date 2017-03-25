---
title: "新機能 | Microsoft Docs"
description: "Microsoft Intune の今月の新機能と過去のリリースの情報について説明します"
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 03/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: b6c245d60c661c04b4c4d29c9bdcdd752254d978
ms.openlocfilehash: 2a602b351cf7f345bd56f20394943ea25f2d2060
ms.lasthandoff: 03/15/2017


---
# <a name="whats-new-in-microsoft-intune---march-2017"></a>Microsoft Intune の新機能 - 2017 年 3 月
Microsoft Intune の今回のリリースの新機能について説明します。 また、過去のリリースに関する情報だけでなく、準備する必要がある今後の変更についても説明します。

> [!Note]
> これらのすべての機能は、最終的にハイブリッド環境 (Configuration Manager と Intune の共存環境) でサポートされるようになります。 最新のハイブリッド機能の詳細については、[ハイブリッド環境の新機能に関するページ](https://docs.microsoft.com/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)を参照してください。

## <a name="new-capabilities"></a>新しい機能

### <a name="new-user-experience-for-the-company-portal-app-for-android---621622--"></a>Android 用ポータル サイト アプリに関する新しいユーザー エクスペリエンス <!--621622-->

Android 用ポータル サイト アプリでは、ユーザー インターフェイスが最新の外観となり、ユーザー エクスペリエンスが向上しました。 主な更新内容は次のとおりです。

- 色: ポータル サイトのタブ ヘッダーの色が、IT が定義するブランド色になります。
- アプリ: **[アプリ]** タブの **[おすすめアプリ]** ボタンと **[すべてのアプリ]** ボタンが更新されました。
- 検索: **[アプリ]** タブの **[検索]** ボタンが浮動アクション ボタンになりました。
- ナビゲーション アプリ: **[すべてのアプリ]** ビューで **[おすすめ]**、**[すべて]** および **[カテゴリ]** のタブ付きビューが表示され、移動がより簡単になります。
- サポート: **[デバイス]** タブと **[IT に連絡]** タブが更新されて、読みやすくなりました。

これらの変更について詳しくは、「[Intune とエンド ユーザー アプリの UI の更新](whats-new-in-intune-app-ui.md)」をご覧ください。

### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>管理されていないデバイスから割り当てられているアプリにアクセス可能 <!--664691-->

ポータル Web サイトでの設計変更に伴い、iOS と Android ユーザーは、管理されていないデバイスで "登録なしで使用可能" として割り当てられているアプリをインストールできるようになります。 Intune 資格情報を使用して、ユーザーはポータル Web サイトにログインし、割り当てられているアプリの一覧を表示することができます。 "登録なしで使用可能" なアプリのアプリ パッケージは、ポータル Web サイトからダウンロードできます。 この変更は、インストールするために登録が必要なアプリには影響しません。そのようなアプリをインストールする場合は、デバイスの登録が求められます。

### <a name="signing-script-for-windows-10-company-portal---941642--"></a>Windows 10 ポータル サイトの署名スクリプト<!--941642-->

Windows 10 ポータル サイト アプリのダウンロードおよびサイドロードの必要がある場合に、スクリプトを使用して、組織のアプリ署名プロセスを簡素化および合理化できるようになりました。   スクリプトとこれを使用するための手順をダウンロードするには、TechNet ギャラリーの [Windows 10 ポータル サイトの Microsoft Intune 署名スクリプト](https://aka.ms/win10cpscript)に関する記事をご覧ください。 この発表に関して詳しくは、Intune サポート チームのブログの「[Updating your Windows 10 Company Portal app (Windows 10 ポータル サイト アプリの更新)](https://blogs.technet.microsoft.com/intunesupport/2017/03/13/updating-your-windows-10-company-portal-app/)」をご覧ください。


## <a name="notices"></a>通知

### <a name="improved-support-for-android-users-based-in-china---720444--"></a>中国の Android ユーザー向けのサポートが向上しました <!--720444-->

中国では Google Play ストアを利用できないため、Android デバイスの場合は中国のマーケットプレースからアプリを入手する必要があります。 ポータル サイトでは、中国の Android ユーザーをリダイレクトして、ローカルのアプリ ストアからポータル サイトおよび Outlook のアプリをダウンロードできるようにし、このワークフローをサポートします。 これにより、モバイル デバイス管理およびモバイル アプリケーション管理の両方について、条件アクセス ポリシーが有効な場合に、ユーザー エクスペリエンスが向上します。 Android 用ポータル サイト アプリおよび Outlook アプリは、次の中国のアプリ ストアで入手できます。

- [Baidu](https://go.microsoft.com/fwlink/?linkid=836946)
- [Xiaomi](https://go.microsoft.com/fwlink/?linkid=836947)
- [Tencent](https://go.microsoft.com/fwlink/?linkid=836949)
- [Huawei](https://go.microsoft.com/fwlink/?linkid=836948)
- [Wandoujia](https://go.microsoft.com/fwlink/?linkid=836950)

### <a name="best-practice-make-sure-your-company-portal-apps-are-up-to-date---879465--"></a>ベスト プラクティス: ポータル サイト アプリが最新かどうかを確認する<!--879465-->

2016 年 12 月にマイクロソフトは、ユーザーのグループの iOS、Android、Windows 8.1 以降、または Windows Phone 8.1 以降のデバイスの登録時に、これらのグループへの多要素認証 (MFA) の強制を有効にする更新プログラムをリリースしました。 この機能を使用するには、Android (v5.0.3419.0 以降) および iOS (v2.1.17 以降) 向けのポータル サイト アプリの特定のベースライン バージョンが必要です。

マイクロソフトでは、あらゆるサポートされたプラットフォームでコンソールとポータル サイト アプリの両方に新機能を追加することで Intune の向上に継続的に取り組んでいます。 この結果、マイクロソフトは、現在のバージョンのポータル サイト アプリに見つかった問題のみの修正プログラムをリリースしています。 このため、ユーザー エクスペリエンスを最善にするために、最新バージョンのポータル サイト アプリを使用することをお勧めします。

>[!Tip]
> ユーザーに、適切なアプリ ストアからアプリを自動的に更新するようにデバイスを設定してもらうようにしてください。 Android ポータル サイト アプリをネットワーク共有で使用できるようにしている場合は、[Microsoft ダウンロード センター](https://www.microsoft.com/download/details.aspx?id=49140)から最新バージョンをダウンロードできます。

### <a name="microsoft-teams-is-now-enabled-for-mam-on-ios-and-android"></a>iOS および Android で MAM で利用できるようになった Microsoft Teams

マイクロソフトは、Microsoft Teams の一般公開を発表しました。 更新された iOS および Android 向け Microsoft Teams アプリが Intune モバイル アプリ管理 (MAM) 機能で有効になったため、すべての段階で会話や企業データを保護しながら、デバイスを問わず作業することでチームの生産性をたかめることができるようになりました。 詳しくは、Enterprise Mobility and Security チームのブログの [Microsoft Teams に関するお知らせ](https://blogs.technet.microsoft.com/enterprisemobility/2017/03/14/microsoft-teams-is-now-generally-available-and-mam-enabled-on-ios-and-android/)をご覧ください。


## <a name="whats-new-in-the-public-preview-of-the-intune-admin-experience-on-azure---736542--"></a>Azure での新しい Intune 管理者エクスペリエンスのパブリック プレビューの新機能<!--736542-->

2017 年初めには、すべての管理者エクスペリエンスが Azure に移行され、Graph API を幅広く使用する最新のサービス プラットフォーム上で、EMS の中核的ワークフローの強力な統合管理を利用できるようになります。

今月には、Azure Portal で新しい管理者エクスペリエンスのパブリック プレビューを表示する新しい試用テナントが開始されます。 プレビュー状態では、既存の Intune コンソールでの機能とパリティが繰り返し提供されます。

Azure Portal の管理者エクスペリエンスでは、既に発表されている新しいグループ化とターゲット設定の機能が使用されます。既存のテナントを新しいグループ化エクスペリエンスに移行すると、テナントの管理者エクスペリエンスも新しいプレビュー版に移行されます。 テナントを移行する前に、新しい機能をテストしたり見たりしたい場合は、新しい Intune 試用版アカウントにサインアップするか、[新しいドキュメント](https://docs.microsoft.com/intune-azure/introduction/whats-new)をご覧ください。

> [!Note]
> Azure Portal プレビューについて、今月の更新プログラムを展開しています。 ただし、Intune サービスの展開方法により、変更はすぐに入手できない場合があります。  新しいポータル機能を入手できるようになる前に、サービスのいくつかのコンポーネントを順次更新する必要があります。 今後、今月ロールアウトされる Azure Portal プレビューの変更を随時ご確認ください。 変更の詳細な一覧については、「[Microsoft Intune プレビューの新機能](/intune-azure/introduction/whats-new)」をご覧ください。

## <a name="whats-coming"></a>今後の更新情報

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple の要求による Application Transport Security 対応のための更新<!--748318-->

Apple は、2017 年春より Application Transport Security (ATS) の特定の要件を適用すると発表しました。 ATS では、HTTPS 経由で行われるアプリ通信すべてに、より厳格なセキュリティ保護が適用されます。 この変更により、iOS ポータル サイト アプリを使用している Intune ユーザーが影響を受けます。 詳細については、[Intune サポートのブログ](https://aka.ms/compportalats)をご覧ください。

### <a name="see-also"></a>関連項目
* [Microsoft Intune のブログ](http://go.microsoft.com/fwlink/?LinkID=273882)
* [クラウド プラットフォームのロードマップ](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Azure プレビューの新機能](https://docs.microsoft.com/intune-azure/introduction/whats-new)
* [ポータル Web サイトの UI の新機能](https://docs.microsoft.com/intune/whats-new/whats-new-in-company-portal-ui)
* [新機能の公開履歴](whats-new-archive.md)

