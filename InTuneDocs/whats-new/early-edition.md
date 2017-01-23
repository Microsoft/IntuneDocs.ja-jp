---
title: "初期エディション | Microsoft Docs"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 12/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 18d47678b0fbdbd98502f2d3b469b202b567b2e7
ms.openlocfilehash: 3c7edc236878232c6f4c0ae993733c967946e765


---

# <a name="the-early-edition-for-microsoft-intune---january"></a>Microsoft Intune の初期エディション - 1 月

**初期エディション**では、Microsoft Intune の今後のリリースで予定されている新機能を一覧します。 ここに記載されている情報は、秘密保持契約書のもとごく限られた範囲について開示されたものであり、また今後変更される可能性があります。 ここに挙げられている機能は、発売日に間に合わない可能性があり、その場合は将来のリリースを待たなければなりません。 正式なリリースに向けてパイロット (フライト) テスト中の機能もあります。 ご不明な点や懸念される事項がある場合は、Intune の開発チームまたは PM にお問い合わせください。

このページは定期的に更新されます。 適宜確認してください。

> [!Note]
> Intune に関して以下の機能が現在開発されています。 これらのすべての機能は、最終的にハイブリッド環境 (Configuration Manager と Intune の共存環境) でサポートされるようになります。 最新のハイブリッド機能の詳細については、[ハイブリッド環境の新機能に関するページ](https://docs.microsoft.com/en-us/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)を参照してください。

## <a name="new-capabilities"></a>新しい機能

### <a name="actions-for-non-compliance---730266--"></a>コンプライアンス非対応に対するアクション <!--730266-->
_コンプライアンス非対応に対するアクション_は、コンプライアンス非対応のデバイスに対してアクションを実行できるようにするコンプライアンス ポリシーの新しい機能です。 単一または複数のアクションを指定できます。また、実行する必要があるアクションの期間を指定することもできます。 たとえば、デバイスが非対応になった直後に電子メールで、その非対応デバイスのユーザーに通知することができます。あるいは、非対応デバイスに対して、条件付きアクセスで 3 日間の猶予期間後の企業リソースへのアクセスをブロックすることができます。

### <a name="in-console-reports-for-mam-without-enrollment---677961--"></a>登録を必要としない MAM のコンソール内レポート <!--677961-->
登録されているデバイスと登録されていないデバイスの両方に対して、新しいアプリ保護レポートが追加されました。 詳細については、「[Microsoft Intune でのモバイル アプリ管理ポリシーの監視](https://docs.microsoft.com/en-us/intune/deploy-use/monitor-mobile-app-management-policies-with-microsoft-intune)」を参照してください。

### <a name="conditional-access-for-mam-with-sharepoint-online---679339--"></a>SharePoint Online での MAM に対する条件付きアクセス<!--679339-->
Intune モバイル アプリ管理 (MAM) ポリシーによってサポートされていないアプリによる SharePoint Online へのアクセスをブロックできます。  Intune モバイル アプリ管理は、Azure Portal で使用することができます。 __[設定]__ ブレードの __[条件付きアクセス]__ セクションに SharePoint Online のオプションがあります。 この機能は、サービス リリースの他の部分とは別に出荷されます。 <!--Find out more about this new feature [here](https://docs.microsoft.com/intune/deploy-use/mam-ca-for-sharepoint-online).-->

### <a name="android-711-support---694397--"></a>Android 7.1.1 のサポート <!--694397-->
Intune では Android 7.1.1 が完全にサポートされ、管理されるようになりました。

## <a name="notices"></a>通知

### <a name="defaulting-to-managing-windows-desktop-devices-through-windows-settings---663050--"></a>Windows 設定による Windows デスクトップ デバイスの既定での管理 <!--663050-->
Windows 10 デスクトップを登録するための既定の動作が変わります。 新しい登録では、PC エージェントを使用するのではなく、一般的な MDM エージェント登録フローに従います。

ポータル Web サイトでは、Windows 10 デスクトップのユーザーに登録手順が提供されます。この手順では、Windows 10 デスクトップ コンピューターをモバイル デバイスとして追加するプロセスが示されます。 これは、現在登録されている PC には影響しません。組織では引き続き、[任意の](https://docs.microsoft.com/en-us/intune/deploy-use/set-up-windows-device-management-with-microsoft-intune) PC エージェントを使用して Windows 10 デスクトップを管理できます。

### <a name="company-portal-for-ios-links-open-inside-the-app---665954--"></a>iOS 用ポータル サイトのリンクをアプリ内で開く <!--665954-->
iOS 用ポータル サイト内のリンク (ドキュメントとアプリへのリンクを含む) は、Safari のアプリ内ビューを使用して、ポータル サイト アプリに直接開きます。 この更新プログラムは、1 月にサービス更新プログラムとは別に提供されます。

### <a name="improving-mobile-app-management-support-for-selective-wipe---581242--"></a>選択的ワイプのためのモバイル アプリ管理サポートの向上 <!--581242-->
"アプリのデータがワイプされるまでのオフライン期間" ポリシーにより、職場または学校のデータが自動的に削除された場合に、そのデータへのアクセス権の再取得方法に関する追加のガイダンスがエンド ユーザーに示されます。<!--, or the removal of the Intune Company Portal on Android.-->

### <a name="new-documentation-for-app-protection-policies---583398--"></a>アプリの保護ポリシーに関する新しいドキュメント <!--583398-->
Intune アプリ ラッピング ツールまたは Intune アプリ SDK を使用して、iOS および Android アプリでアプリ保護ポリシー (MAM ポリシーとして知られる) を有効にする必要がある管理者やアプリ開発者用のドキュメントを更新しました。

次の記事が更新されました。

* [Microsoft Intune によるモバイル アプリケーション管理のためにアプリを準備する方法を決める](https://docs.microsoft.com/intune/deploy-use/decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune)
* [Intune アプリ ラッピング ツールでモバイル アプリケーションを管理するために iOS アプリを準備する](https://docs.microsoft.com/intune/deploy-use/prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)
* [Microsoft Intune アプリ SDK の概要](https://docs.microsoft.com/intune/develop/intune-app-sdk-get-started)
* [iOS 用 Intune アプリ SDK 開発者ガイド](https://docs.microsoft.com/intune/develop/intune-app-sdk-ios)

次の記事がドキュメント ライブラリに新たに追加されました。

* [Intune App SDK Cordova プラグイン](https://docs.microsoft.com/intune/develop/intune-app-sdk-cordova)
* [Intune App SDK Xamarin コンポーネント](https://docs.microsoft.com/intune/develop/intune-app-sdk-xamarin)

### <a name="progress-bar-when-launching-the-company-portal-on-ios---665978--"></a>iOS でのポータル サイトの起動時の進行状況バー <!--665978-->
iOS 用ポータル サイトでは、ユーザーに発生する読み込みプロセスに関する情報を提供する進行状況バーが起動画面に導入されています。 進行状況バーは段階的にロールアウトされ、スピンと置き換えられます。 これは、一部のユーザーには新しい進行状況バーが表示され、他のユーザーにはスピンが引き続き表示されることを意味します。

## <a name="public-preview-of-the-new-intune-admin-experience-on-azure---736542--"></a>Azure での新しい Intune 管理者エクスペリエンスのパブリック プレビュー <!--736542-->

2017 年初めには、すべての管理者エクスペリエンスが Azure に移行され、Graph API を幅広く使用する最新のサービス プラットフォーム上で、EMS の中核的ワークフローの強力な統合管理を利用できるようになります。

今月には、Azure Portal で新しい管理者エクスペリエンスのパブリック プレビューを表示する新しい試用テナントが開始されます。 プレビュー状態では、既存の Intune コンソールでの機能とパリティが繰り返し提供されます。

Azure Portal の管理者エクスペリエンスでは、既に発表されている新しいグループ化とターゲット設定の機能が使用されます。既存のテナントを新しいグループ化エクスペリエンスに移行すると、テナントの管理者エクスペリエンスも新しいプレビュー版に移行されます。 テナントを移行する前に、新しい機能をテストしたり見たりしたい場合は、新しい Intune 試用版アカウントにサインアップするか、[新しいドキュメント](https://docs.microsoft.com/en-us/intune-azure/introduction/what-is-microsoft-intune)をご覧ください。

テナント移行のスケジュールに関して質問がある場合は、Microsoft の移行チーム ([intunegrps@microsoft.com](mailto:intunegrps@microsoft.com)) にお問い合わせください。

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



<!--HONumber=Dec16_HO4-->


