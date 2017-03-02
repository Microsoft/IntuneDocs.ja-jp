---
title: "初期エディション | Microsoft Docs"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 02/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: d0b3a883bb307fb06cb8d16500798086f328314a
ms.openlocfilehash: eeebf8b6b3bc5c7c35386eb20c96097af1f6769c
ms.lasthandoff: 02/14/2017


---


# <a name="the-early-edition-for-microsoft-intune---february-2017"></a>Microsoft Intune の初期エディション - 2017 年 2 月

**初期エディション**では、Microsoft Intune の今後のリリースで予定されている新機能を一覧します。 ここに記載されている情報は、秘密保持契約書のもとごく限られた範囲について開示されたものであり、また今後変更される可能性があります。 ここに挙げられている機能は、発売日に間に合わない可能性があり、その場合は将来のリリースを待たなければなりません。 正式なリリースに向けてパイロット (フライト) テスト中の機能もあります。 ご不明な点や懸念される事項がある場合は、Intune の開発チームまたは PM にお問い合わせください。

このページは定期的に更新されます。 適宜確認してください。

> [!Note]
> Intune に関して以下の機能が現在開発されています。 これらのすべての機能は、最終的にハイブリッド環境 (Configuration Manager と Intune の共存環境) でサポートされるようになります。 最新のハイブリッド機能の詳細については、[ハイブリッド環境の新機能に関するページ](https://docs.microsoft.com/en-us/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)を参照してください。

## <a name="new-capabilities"></a>新しい機能

### <a name="modernizing-the-company-portal-website---753980--"></a>ポータル Web サイトの進化 <!--753980-->
2 月以降、ポータル Web サイトのデザインは、新しいコントラストの配色パターン、動的な図、"ハンバーガー メニュー" (ヘルプデスクの連絡先詳細や既存の管理対象デバイスに関する情報を含む、![ポータル Web サイトの左上隅に新たに追加されたハンバーガー メニューの小さな画像](./media/CP_hamburger_menu.png)) を使用することで、Microsoft の他の製品やサービスと連携します。 ランディング ページはユーザーが利用できるアプリをわかりやすくするために再配置され、おすすめのアプリや最近更新されたアプリはカルーセル ビューで表示されます。 [UI の更新ページ](https://docs.microsoft.com/intune/whats-new/whats-new-in-intune-app-ui)で、更新前と後のイメージを確認できます。

### <a name="new-guided-experience-for-windows-10-company-portal---713927--"></a>Windows 10 ポータル サイトの新しいガイド機能 <!--713927-->
3 月以降、Windows 10 用のポータル サイトでは、特定されていないデバイスや登録されていないデバイス向けのガイド付き Intune チュートリアルを利用できるようになります。 この新しい機能では、ユーザーの Windows 10 ビルド向けにカスタマイズされた詳しい手順が提供され、これに従ってユーザーは AAD 登録 (条件付きアクセス機能の識別に必要) と MDM 登録 (デバイス管理機能に必要) を実行できます。 ガイド付きチュートリアルにはポータル サイトのホーム ページからアクセスできます。また、これはオプションなので、ユーザーは、登録が完了していなくても、引き続きアプリを使用できます。ただし、使用できる機能は限定される可能性があります。

###

## <a name="notices"></a>通知

### <a name="group-migration-will-not-require-any-updates-to-groups-or-policies-for-ios-devices---898837--"></a>グループの移行に、iOS デバイス用のグループまたはポリシーの更新は不要<!--898837-->
業務用デバイスの登録プロファイルで事前に割り当てられている Intune デバイス グループごとに、Azure Active Directory デバイス グループへの移行時に、業務用デバイスの登録プロファイルの名前に基づいて、AAD に対応する動的デバイス グループが作成されます。 これにより、デバイスは登録時に確実に自動でグループ化され、元の Intune グループと同じポリシーおよびアプリが受信されるようになります。

テナントがグループ化と対象設定のための移行プロセスに入ると、Intune で自動的に動的 AAD グループが作成され、業務用デバイスの登録プロファイルの対象となる Intune グループに対応します。 Intune 管理者が対象となる Intune グループを削除しても、対応する動的 AAD グループは削除されません。 グループのメンバーと動的クエリは消去されますが、グループ自体は、IT 管理者が AAD ポータルで削除するまで残ります。

同様に、IT 管理者が業務用デバイスの登録プロファイルの対象となる Intune グループを変更した場合、Intune では新しいプロファイルの割り当てを反映する新しい動的グループが作成されますが、古い割り当て用に作成された動的グループが削除されることはありません。

### <a name="new-mdm-server-address-for-windows-devices---893007--"></a>Windows デバイス用の新しい MDM サーバー アドレス <!--893007-->
Windows および Windows Phone のユーザーがデバイスを登録しようとして、MDM サーバー アドレスとして (入力を求められた場合に) __manage.microsoft.com__ を入力した場合、登録は失敗します。 MDM サーバー アドレスは、__manage.microsoft.com__ から __enrollment.manage.microsoft.com__ に変更されています。 Windows や Windows Phone デバイスの登録時に、MDM サーバー アドレスの入力を求められた場合は、__enrollment.manage.microsoft.com__ を使用するようにユーザーに通知してください。 この更新プログラムでは、__EnterpriseEnrollment.contoso.com__ を __manage.microsoft.com__ にリダイレクトする DNS の CNAME と、__EnterpriseEnrollment.contoso.com__ を __EnterpriseEnrollment-s.manage.microsoft.com__ にリダイレクトする DNS の CNAME を置き換える必要があります。 この変更の詳細については、[aka.ms/intuneenrollsvrchange](https://aka.ms/intuneenrollsvrchange) を参照してください。

### <a name="new-user-experience-for-the-company-portal-app-for-android---621622--"></a>Android 用ポータル サイト アプリに関する新しいユーザー エクスペリエンス <!--621622-->
3 月以降、Android 用ポータル サイト アプリでは[材料設計ガイドライン](https://material.io/guidelines/material-design/introduction.html)に従って、最新の外観が作成されます。 この改善されたユーザー エクスペリエンスには、次のものが含まれます。

* __色__: タブ ヘッダーを、カスタムの色パレットに従って色付けすることができます。
* __インターフェイス__: [アプリ] タブの [おすすめアプリ] ボタンと [すべてのアプリ] ボタンが更新されました。 [検索] ボタンは浮動アクション ボタンになりました。
* __ナビゲーション__: [すべてのアプリ] で [おすすめ]、[すべて] および [カテゴリ] のタブ付きビューが表示され、移動がより簡単になります。
* __サービス__: [デバイス] タブと [IT に連絡] タブが読みやすくなりました。

[UI の更新ページ](https://docs.microsoft.com/intune/whats-new/whats-new-in-intune-app-ui)で、更新前と後のイメージを確認できます。

### <a name="associate-multiple-management-tools-with-the-windows-store-for-business---926135--"></a>複数の管理ツールとビジネス向け Windows ストアの関連付け <!--926135-->
ビジネス向け Windows ストアのアプリを展開するために複数の管理ツールを使用する場合、これまでは、ビジネス向け Windows ストアにはそのうちの&1; つしか関連付けることはできませんでした。 これからは、複数のツール (Intune や Configuration Manager など) をストアに関連付けることができます。 詳細については、「[ビジネス向け Windows ストアから購入したアプリを Microsoft Intune で管理する](https://docs.microsoft.com/en-us/intune/deploy-use/manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune#associate-your-windows-store-for-business-account-with-intune)」を参照してください。

## <a name="public-preview-of-the-new-intune-admin-experience-on-azure---736542--"></a>Azure での新しい Intune 管理者エクスペリエンスのパブリック プレビュー <!--736542-->

2017 年初めには、すべての管理者エクスペリエンスが Azure に移行され、Graph API を幅広く使用する最新のサービス プラットフォーム上で、EMS の中核的ワークフローの強力な統合管理を利用できるようになります。

今月には、Azure Portal で新しい管理者エクスペリエンスのパブリック プレビューを表示する新しい試用テナントが開始されます。 プレビュー状態では、既存の Intune コンソールでの機能とパリティが繰り返し提供されます。

Azure Portal の管理者エクスペリエンスでは、既に発表されている新しいグループ化とターゲット設定の機能が使用されます。既存のテナントを新しいグループ化エクスペリエンスに移行すると、テナントの管理者エクスペリエンスも新しいプレビュー版に移行されます。 テナントを移行する前に、新しい機能をテストしたり見たりしたい場合は、新しい Intune 試用版アカウントにサインアップするか、[新しいドキュメント](https://docs.microsoft.com/en-us/intune-azure/introduction/what-is-microsoft-intune)をご覧ください。

テナント移行のスケジュールに関して質問がある場合は、Microsoft の移行チーム ([intunegrps@microsoft.com](mailto:intunegrps@microsoft.com)) にお問い合わせください。

### <a name="february-2017"></a>2017 年 2 月

#### <a name="ability-to-restrict-mobile-device-enrollment---747600-795782--"></a>モバイル デバイス登録を制限する機能 <!--747600, 795782-->
Intune では、登録を許可されるモバイル デバイス プラットフォームを制御する新しい登録制限が追加されています。 Intune では、モバイル デバイス プラットフォームが iOS、macOS、Android、Windows、Windows Mobile に分かれています。

* モバイル デバイスの登録を制限しても、PC クライアントの登録は制限されません。  
* iOS と Android のみに、個人所有デバイスの登録をブロックする&1; つの追加オプションがあります。

[この記事](https://docs.microsoft.com/en-us/intune/deploy-use/manage-corporate-owned-devices)で説明されているように、IT 管理者が明示的に会社所有と指定しない限り、Intune はすべての新しいデバイスを個人所有としてマークします。

#### <a name="view-all-actions-on-managed-devices---677150--"></a>管理対象デバイスのすべての操作を表示 <!--677150-->
新しい__デバイス操作__レポートには、デバイスでの出荷時の設定にリセットなどのリモート操作を実行したユーザーが表示され、さらにその操作の状態が表示されます。

#### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>管理されていないデバイスから割り当てられているアプリにアクセス可能 <!--664691-->
ポータル Web サイトでの設計変更に伴い、iOS と Android ユーザーは、管理されていないデバイスで "登録なしで使用可能" として割り当てられているアプリをインストールできるようになります。 Intune 資格情報を使用して、ユーザーはポータル Web サイトにログインし、割り当てられているアプリの一覧を表示することができます。 "登録なしで使用可能" なアプリのアプリ パッケージは、ポータル Web サイトからダウンロードできます。 この変更は、インストールするために登録が必要なアプリには影響しません。そのようなアプリをインストールする場合は、デバイスの登録が求められます。

#### <a name="custom-app-categories---748805--"></a>カスタム アプリのカテゴリ <!--748805-->
Intune に追加するアプリのカテゴリを作成、編集、および割り当てることができるようになりました。 現時点では、カテゴリは英語でのみ指定できます。
[Intune にアプリを追加する方法](/intune-azure/manage-apps/add-apps)に関するページを参照してください。

#### <a name="display-device-categories---814654--"></a>デバイス カテゴリを表示する <!--814654-->
デバイスの一覧に、列としてデバイス カテゴリを表示できるようになりました。 デバイスのプロパティー ブレードのプロパティー セクションからカテゴリを編集することもできます。

### <a name="january-2017"></a>2017 年 1 月

#### <a name="custom-app-categories---748805--"></a>カスタム アプリのカテゴリ <!--748805-->
Intune に追加するアプリのカテゴリを作成、編集、および割り当てることができるようになりました。 現時点では、カテゴリは英語でのみ指定できます。

#### <a name="assign-line-of-business-apps-whether-or-not-devices-are-enrolled---748803--"></a>デバイスの登録に関係なく基幹業務アプリを割り当てられる <!--748803-->
デバイスが Intune に登録されているかどうかに関係なく、基幹業務アプリをストアからユーザーに割り当てられるようになりました。 ユーザーのデバイスが Intune に登録されていない場合は、ポータル サイト アプリではなく、ポータル Web サイトに移動してインストールする必要があります。

### <a name="december-2016"></a>2016 年 12 月

#### <a name="telecom-expense-management-integration-in-public-preview-of-azure-portal--747605--"></a>Azure Portal のパブリック プレビューでの電気通信経費管理の統合<!--747605-->
Azure Portal では、サード パーティの電気通信経費管理 (TEM) サービスとの統合のプレビューが始められています。 Intune を使用して、国内およびローミングのデータ使用量を制限できます。 これらの統合は、[Saaswedo](http://www.saaswedo.com) で始まっています。 試用テナントでこの機能を有効にする場合は、[Microsoft サポートにお問い合わせください](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune)。

### <a name="see-also"></a>関連項目
最近の開発状況について詳しくは、「[Microsoft Intune の新機能](whats-new-in-microsoft-intune.md)」をご覧ください。

