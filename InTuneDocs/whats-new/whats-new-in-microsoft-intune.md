---
title: "新機能 | Microsoft Docs"
description: "Microsoft Intune の今月の新機能と過去のリリースの情報について説明します"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 02/17/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: cb1679deda0ba325ee3bd7288713f12317489006
ms.openlocfilehash: 37d44dc2752815ef7abf47e5d4a658a126892a86
ms.lasthandoff: 02/18/2017


---
# <a name="whats-new-in-microsoft-intune---february-2017"></a>Microsoft Intune の新機能 - 2017 年 2 月
Microsoft Intune の今回のリリースの新機能について説明します。 また、過去のリリースに関する情報だけでなく、準備する必要がある今後の変更についても説明します。

> [!Note]
> これらのすべての機能は、最終的にハイブリッド環境 (Configuration Manager と Intune の共存環境) でサポートされるようになります。 最新のハイブリッド機能の詳細については、[ハイブリッド環境の新機能に関するページ](https://docs.microsoft.com/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)を参照してください。

## <a name="new-capabilities"></a>新しい機能

### <a name="modernizing-the-company-portal-website---753980--"></a>ポータル Web サイトの進化 <!--753980-->
ポータル Web サイトで管理対象のデバイスを持っていないユーザーを対象とするアプリをサポートします。 この Web サイトは新しいコントラストの配色パターン、動的な図、"ハンバーガー メニュー" (ヘルプデスクの連絡先詳細や既存の管理対象デバイスに関する情報を含む ![ポータル Web サイトの左上隅に新たに追加されたハンバーガー メニューの小さなイメージ](./media/CP_hamburger_menu.png)) を使用することで、Microsoft の他の製品やサービスと連携します。 ランディング ページはユーザーが利用できるアプリをわかりやすくするために再配置され、おすすめのアプリや最近更新されたアプリはカルーセル ビューで表示されます。 [UI の更新ページ](https://docs.microsoft.com/intune/whats-new/whats-new-in-intune-app-ui)で、更新前と後のイメージを確認できます。

### <a name="new-guided-experience-for-windows-10-company-portal---713927--"></a>Windows 10 ポータル サイトの新しいガイド機能 <!--713927-->
3 月以降、Windows 10 用のポータル サイトでは、特定されていないデバイスや登録されていないデバイス向けのガイド付き Intune チュートリアルを利用できるようになります。 この新しい機能では、ユーザーの Windows 10 ビルド向けにカスタマイズされた詳しい手順が提供され、これに従ってユーザーは AAD 登録 (条件付きアクセス機能の識別に必要) と MDM 登録 (デバイス管理機能に必要) を実行できます。 ガイド付きチュートリアルにはポータル サイトのホーム ページからアクセスできます。また、これはオプションなので、ユーザーは、登録が完了していなくても、引き続きアプリを使用できます。ただし、使用できる機能は限定される可能性があります。

## <a name="notices"></a>通知

### <a name="group-migration-will-not-require-any-updates-to-groups-or-policies-for-ios-devices---898837--"></a>グループの移行に、iOS デバイス用のグループまたはポリシーの更新は不要<!--898837-->
業務用デバイスの登録プロファイルで事前に割り当てられている Intune デバイス グループごとに、Azure Active Directory デバイス グループへの移行時に、業務用デバイスの登録プロファイルの名前に基づいて、AAD に対応する動的デバイス グループが作成されます。 これにより、デバイスは登録時に確実に自動でグループ化され、元の Intune グループと同じポリシーおよびアプリが受信されるようになります。

テナントがグループ化と対象設定のための移行プロセスに入ると、Intune で自動的に動的 AAD グループが作成され、業務用デバイスの登録プロファイルの対象となる Intune グループに対応します。 Intune 管理者が対象となる Intune グループを削除しても、対応する動的 AAD グループは削除されません。 グループのメンバーと動的クエリは消去されますが、グループ自体は、IT 管理者が AAD ポータルで削除するまで残ります。

同様に、IT 管理者が業務用デバイスの登録プロファイルの対象となる Intune グループを変更した場合、Intune では新しいプロファイルの割り当てを反映する新しい動的グループが作成されますが、古い割り当て用に作成された動的グループが削除されることはありません。

### <a name="defaulting-to-managing-windows-desktop-devices-through-windows-settings---663050--"></a>Windows 設定による Windows デスクトップ デバイスの既定での管理 <!--663050-->
Windows 10 デスクトップを登録するための既定の動作が変わります。 新しい登録では、PC エージェントを使用するのではなく、一般的な MDM エージェント登録フローに従います。 ポータル Web サイトでは、Windows 10 デスクトップのユーザーに登録手順が提供されます。この手順では、Windows 10 デスクトップ コンピューターをモバイル デバイスとして追加するプロセスが示されます。 これは、現在登録されている PC には影響しません。組織では引き続き、[任意の](https://docs.microsoft.com/intune/deploy-use/set-up-windows-device-management-with-microsoft-intune) PC エージェントを使用して Windows 10 デスクトップを管理できます。

### <a name="improving-mobile-app-management-support-for-selective-wipe---581242--"></a>選択的ワイプのためのモバイル アプリ管理サポートの向上 <!--581242-->
"アプリのデータがワイプされるまでのオフライン期間" ポリシーにより、職場または学校のデータが自動的に削除された場合に、そのデータへのアクセス権の再取得方法に関する追加のガイダンスがエンド ユーザーに示されます。<!--, or the removal of the Intune Company Portal on Android.-->

### <a name="company-portal-for-ios-links-open-inside-the-app---665954--"></a>iOS 用ポータル サイトのリンクをアプリ内で開く <!--665954-->
iOS 用ポータル サイト内のリンク (ドキュメントとアプリへのリンクを含む) は、Safari のアプリ内ビューを使用して、ポータル サイト アプリに直接開きます。 この更新プログラムは、1 月にサービス更新プログラムとは別に提供されます。

### <a name="new-mdm-server-address-for-windows-devices---893007--"></a>Windows デバイス用の新しい MDM サーバー アドレス <!--893007-->
Windows および Windows Phone のユーザーがデバイスを登録しようとして、MDM サーバー アドレスとして (入力を求められた場合に) __manage.microsoft.com__ を入力した場合、登録は失敗します。 MDM サーバー アドレスは、__manage.microsoft.com__ から __enrollment.manage.microsoft.com__ に変更されています。 Windows や Windows Phone デバイスの登録時に、MDM サーバー アドレスの入力を求められた場合は、__enrollment.manage.microsoft.com__ を使用するようにユーザーに通知してください。 CNAME 設定に変更は必要ありません。 この変更の詳細については、[aka.ms/intuneenrollsvrchange](https://aka.ms/intuneenrollsvrchange) を参照してください。

### <a name="new-user-experience-for-the-company-portal-app-for-android---621622--"></a>Android 用ポータル サイト アプリに関する新しいユーザー エクスペリエンス <!--621622-->
3 月以降、Android 用ポータル サイト アプリでは[材料設計ガイドライン](https://material.io/guidelines/material-design/introduction.html)に従って、最新の外観が作成されます。 この改善されたユーザー エクスペリエンスには、次のものが含まれます。

* __色__: タブ ヘッダーを、カスタムの色パレットに従って色付けすることができます。
* __インターフェイス__: [アプリ] タブの [おすすめアプリ] ボタンと [すべてのアプリ] ボタンが更新されました。 [検索] ボタンは浮動アクション ボタンになりました。
* __ナビゲーション__: [すべてのアプリ] で [おすすめ]、[すべて] および [カテゴリ] のタブ付きビューが表示され、移動がより簡単になります。
* __サービス__: [デバイス] タブと [IT に連絡] タブが読みやすくなりました。

[UI の更新ページ](https://docs.microsoft.com/intune/whats-new/whats-new-in-intune-app-ui)で、更新前と後のイメージを確認できます。

### <a name="associate-multiple-management-tools-with-the-windows-store-for-business---926135--"></a>複数の管理ツールとビジネス向け Windows ストアの関連付け <!--926135-->
ビジネス向け Windows ストアのアプリを展開するために複数の管理ツールを使用する場合、これまでは、ビジネス向け Windows ストアにはそのうちの&1; つしか関連付けることはできませんでした。 これからは、複数のツール (Intune や Configuration Manager など) をストアに関連付けることができます。 詳細については、「[ビジネス向け Windows ストアから購入したアプリを Microsoft Intune で管理する](https://docs.microsoft.com/en-us/intune/deploy-use/manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune#associate-your-windows-store-for-business-account-with-intune)」を参照してください。

## <a name="whats-new-in-the-public-preview-of-the-intune-admin-experience-on-azure---736542--"></a>Azure での新しい Intune 管理者エクスペリエンスのパブリック プレビューの新機能<!--736542-->

2017 年初めには、すべての管理者エクスペリエンスが Azure に移行され、Graph API を幅広く使用する最新のサービス プラットフォーム上で、EMS の中核的ワークフローの強力な統合管理を利用できるようになります。

今月には、Azure Portal で新しい管理者エクスペリエンスのパブリック プレビューを表示する新しい試用テナントが開始されます。 プレビュー状態では、既存の Intune コンソールでの機能とパリティが繰り返し提供されます。

Azure Portal の管理者エクスペリエンスでは、既に発表されている新しいグループ化とターゲット設定の機能が使用されます。既存のテナントを新しいグループ化エクスペリエンスに移行すると、テナントの管理者エクスペリエンスも新しいプレビュー版に移行されます。 テナントを移行する前に、新しい機能をテストしたり見たりしたい場合は、新しい Intune 試用版アカウントにサインアップするか、[新しいドキュメント](https://docs.microsoft.com/intune-azure/introduction/whats-new)をご覧ください。

テナント移行のスケジュールに関して質問がある場合は、Microsoft の移行チーム ([intunegrps@microsoft.com](mailto:intunegrps@microsoft.com)) にお問い合わせください。

Azure の Intune プレビューの新機能は[ここ](https://docs.microsoft.com/intune-azure/introduction/whats-new)で確認できます。

### <a name="see-also"></a>関連項目
* [Microsoft Intune のブログ](http://go.microsoft.com/fwlink/?LinkID=273882)
* [クラウド プラットフォームのロードマップ](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Azure プレビューの新機能](https://docs.microsoft.com/intune-azure/introduction/whats-new)
* [ポータル Web サイトの UI の新機能](https://docs.microsoft.com/intune/whats-new/whats-new-in-company-portal-ui)
* [新機能の公開履歴](whats-new-archive.md)

