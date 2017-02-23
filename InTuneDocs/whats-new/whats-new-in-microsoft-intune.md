---
title: "新機能 | Microsoft Docs"
description: "Microsoft Intune の今月の新機能と過去のリリースの情報について説明します"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 02/07/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: cacampbell
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 053cf0a1b5d06496397b36cbd1a7ebdce420fed3
ms.openlocfilehash: 5158d58c32066ea720335a878fef87451542c195


---
# <a name="whats-new-in-microsoft-intune---january-2017"></a>Microsoft Intune の新機能 - 2017 年 1 月
Microsoft Intune の今回のリリースの新機能について説明します。 また、過去のリリースに関する情報だけでなく、準備する必要がある今後の変更についても説明します。

> [!Note]
> これらのすべての機能は、最終的にハイブリッド環境 (Configuration Manager と Intune の共存環境) でサポートされるようになります。 最新のハイブリッド機能の詳細については、[ハイブリッド環境の新機能に関するページ](https://docs.microsoft.com/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)を参照してください。

## <a name="new-capabilities"></a>新しい機能

<!--### Actions for non-compliance <!--730266
_Actions for non-compliance_ is a new feature of compliance policies that lets you take action on devices that are out of compliance. You can specify single or multiple actions and specify the time period at which those actions must occur. For example, you can notify users of non-compliant devices immediately after the devices become non-compliant through email, or you can block non-compliant devices from accessing corporate resources after a 3-day grace period via Conditional Access.-->

### <a name="in-console-reports-for-mam-without-enrollment---677961--"></a>登録を必要としない MAM のコンソール内レポート <!--677961-->
登録されているデバイスと登録されていないデバイスの両方に対して、新しいアプリ保護レポートが追加されました。 詳細については、「[Microsoft Intune でのモバイル アプリ管理ポリシーの監視](https://docs.microsoft.com/intune/deploy-use/monitor-mobile-app-management-policies-with-microsoft-intune)」を参照してください。

<!--### Conditional access for MAM with SharePoint Online <!--679339
You can block apps that are not supported by Intune mobile app management (MAM) policies from accessing SharePoint Online.  You can get started using Intune mobile app management in the Azure portal. Look for the __Conditional Access__ section in the __Settings__ blade which will include the option for SharePoint Online. This feature will ship separately from the rest of the service release. <!--Find out more about this new feature [here](https://docs.microsoft.com/intune/deploy-use/mam-ca-for-sharepoint-online).-->

### <a name="android-711-support---694397--"></a>Android 7.1.1 のサポート <!--694397-->
Intune では Android 7.1.1 が完全にサポートされ、管理されるようになりました。

### <a name="resolve-issue-where-ios-devices-are-inactive-or-the-admin-console-cannot-communicate-with-them---unknown--"></a>iOS デバイスが無効か、管理コンソールと通信できない問題を解決 <!--unknown-->
ユーザーのデバイスと Intune の接続が失われるとき、新しいトラブルシューティング手順を指示できます。会社リソースへのアクセスを回復するのに役立ちます。 「[デバイスが無効か、管理コンソールとデバイスが通信できない](/intune/troubleshoot/troubleshoot-device-enrollment-in-intune#devices-are-inactive-or-the-admin-console-cannot-communicate-with-them)」を参照してください。

## <a name="notices"></a>通知

### <a name="defaulting-to-managing-windows-desktop-devices-through-windows-settings---663050--"></a>Windows 設定による Windows デスクトップ デバイスの既定での管理 <!--663050-->
Windows 10 デスクトップを登録するための既定の動作が変わります。 新しい登録では、PC エージェントを使用するのではなく、一般的な MDM エージェント登録フローに従います。

ポータル Web サイトでは、Windows 10 デスクトップのユーザーに登録手順が提供されます。この手順では、Windows 10 デスクトップ コンピューターをモバイル デバイスとして追加するプロセスが示されます。 これは、現在登録されている PC には影響しません。組織では引き続き、[任意の](https://docs.microsoft.com/intune/deploy-use/set-up-windows-device-management-with-microsoft-intune) PC エージェントを使用して Windows 10 デスクトップを管理できます。

<!--### Company Portal for iOS links open inside the app <!--665954
Links inside of the Company Portal app for iOS, including those to documentation and apps, will open directly in the Company Portal app using an in-app view of Safari. This update will ship separately from the service update in January.-->

### <a name="improving-mobile-app-management-support-for-selective-wipe---581242--"></a>選択的ワイプのためのモバイル アプリ管理サポートの向上 <!--581242-->
"アプリのデータがワイプされるまでのオフライン期間" ポリシーにより、職場または学校のデータが自動的に削除された場合に、そのデータへのアクセス権の再取得方法に関する追加のガイダンスがエンド ユーザーに示されます。<!--, or the removal of the Intune Company Portal on Android.-->

### <a name="company-portal-for-ios-links-open-inside-the-app---665954--"></a>iOS 用ポータル サイトのリンクをアプリ内で開く <!--665954-->
iOS 用ポータル サイト内のリンク (ドキュメントとアプリへのリンクを含む) は、Safari のアプリ内ビューを使用して、ポータル サイト アプリに直接開きます。 この更新プログラムは、1 月にサービス更新プログラムとは別に提供されます。

### <a name="modernizing-the-company-portal-website---753980--"></a>ポータル Web サイトの進化 <!--753980-->
2 月から、ポータル Web サイトで管理対象のデバイスを持っていないユーザーを対象とするアプリをサポートします。 この Web サイトは新しいコントラストの配色パターン、動的な図、"ハンバーガー メニュー" (ヘルプデスクの連絡先詳細や既存の管理対象デバイスに関する情報を含む![ポータル Web サイトのハンバーガー メニュー](./media/CP_hamburger_menu.png)) を使用することで、Microsoft の他の製品やサービスと連携します。 ランディング ページはユーザーが利用できるアプリをわかりやすくするために再配置され、おすすめのアプリや最近更新されたアプリはカルーセル ビューで表示されます。 [Intune アプリ UI の新機能](https://docs.microsoft.com/intune/whats-new/whats-new-in-intune-app-ui#January_2017)に関するページで、変更前と変更後の画像を確認できます。

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

<!--### Progress bar when launching the Company Portal on iOS <!--665978
The Company Portal for iOS is introducing a progress bar on the launch screen to provide the user with information about the loading processes that occur. There will be a phased rollout of the progress bar to replace the spinner. This means that some of your users will see the new progress bar while others will continue to see the spinner.-->

### <a name="progress-bar-when-launching-the-company-portal-on-ios---665978--"></a>iOS でのポータル サイトの起動時の進行状況バー <!--665978-->
iOS 用ポータル サイトでは、ユーザーに発生する読み込みプロセスに関する情報を提供する進行状況バーが起動画面に導入されています。 進行状況バーは段階的にロールアウトされ、スピンと置き換えられます。 これは、一部のユーザーには新しい進行状況バーが表示され、他のユーザーにはスピンが引き続き表示されることを意味します。

## <a name="whats-new-in-the-public-preview-of-the-intune-admin-experience-on-azure---736542--"></a>Azure での新しい Intune 管理者エクスペリエンスのパブリック プレビューの新機能<!--736542-->

2017 年初めには、すべての管理者エクスペリエンスが Azure に移行され、Graph API を幅広く使用する最新のサービス プラットフォーム上で、EMS の中核的ワークフローの強力な統合管理を利用できるようになります。

今月には、Azure Portal で新しい管理者エクスペリエンスのパブリック プレビューを表示する新しい試用テナントが開始されます。 プレビュー状態では、既存の Intune コンソールでの機能とパリティが繰り返し提供されます。

Azure Portal の管理者エクスペリエンスでは、既に発表されている新しいグループ化とターゲット設定の機能が使用されます。既存のテナントを新しいグループ化エクスペリエンスに移行すると、テナントの管理者エクスペリエンスも新しいプレビュー版に移行されます。 テナントを移行する前に、新しい機能をテストしたり見たりしたい場合は、新しい Intune 試用版アカウントにサインアップするか、[新しいドキュメント](https://docs.microsoft.com/intune-azure/introduction/what-is-microsoft-intune)をご覧ください。

テナント移行のスケジュールに関して質問がある場合は、Microsoft の移行チーム ([intunegrps@microsoft.com](mailto:intunegrps@microsoft.com)) にお問い合わせください。

Azure の Intune プレビューの新機能は[ここ](https://docs.microsoft.com/intune-azure/introduction/whats-new)で確認できます。

### <a name="see-also"></a>関連項目
* [Microsoft Intune のブログ](http://go.microsoft.com/fwlink/?LinkID=273882)
* [クラウド プラットフォームのロードマップ](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Azure プレビューの新機能](https://docs.microsoft.com/intune-azure/introduction/whats-new)
* [ポータル Web サイトの UI の新機能](https://docs.microsoft.com/intune/whats-new/whats-new-in-company-portal-ui)
* [新機能の公開履歴](whats-new-archive.md)



<!--HONumber=Feb17_HO1-->


