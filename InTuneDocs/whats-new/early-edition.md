---
title: "初期エディション | Microsoft Docs"
description: 
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 03/09/2017
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
ms.sourcegitcommit: 0936051b5c33a2e98f275ef7a3a32be2e8f5a8b0
ms.openlocfilehash: 0ba6695b595849f72eb44d8e6f095e8b1aae39eb
ms.lasthandoff: 03/10/2017


---


# <a name="the-early-edition-for-microsoft-intune---march-2017"></a>Microsoft Intune の初期エディション - 2017 年 3 月

**初期エディション**では、Microsoft Intune の今後のリリースで予定されている新機能を一覧します。 ここに記載されている情報は、秘密保持契約書のもとごく限られた範囲について開示されたものであり、また今後変更される可能性があります。 ここに挙げられている機能は、発売日に間に合わない可能性があり、その場合は将来のリリースを待たなければなりません。 正式なリリースに向けてパイロット (フライト) テスト中の機能もあります。 ご不明な点や懸念される事項がある場合は、Intune の開発チームまたは PM にお問い合わせください。

このページは定期的に更新されます。 適宜確認してください。

> [!Note]
> Intune に関して以下の機能が現在開発されています。 これらのすべての機能は、最終的にハイブリッド環境 (Configuration Manager と Intune の共存環境) でサポートされるようになります。 最新のハイブリッド機能の詳細については、[ハイブリッド環境の新機能に関するページ](https://docs.microsoft.com/en-us/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)を参照してください。

## <a name="new-capabilities"></a>新しい機能

### <a name="new-user-experience-for-the-company-portal-app-for-android---621622--"></a>Android 用ポータル サイト アプリに関する新しいユーザー エクスペリエンス <!--621622-->

Android 用ポータル サイト アプリでは、ユーザー インターフェイスが最新の外観となり、ユーザー エクスペリエンスが向上しました。 主な更新内容は次のとおりです。

- 色: ポータル サイトのタブ ヘッダーの色が、IT が定義するブランド色になります。
- アプリ: **[アプリ]** タブの **[おすすめアプリ]** ボタンと **[すべてのアプリ]** ボタンが更新されました。
- 検索: **[アプリ]** タブの **[検索]** ボタンが浮動アクション ボタンになりました。
- ナビゲーション アプリ: **[すべてのアプリ]** ビューで **[おすすめ]**、**[すべて]** および **[カテゴリ]** のタブ付きビューが表示され、移動がより簡単になります。
- サポート: **[デバイス]** タブと **[IT に連絡]** タブが更新されて、読みやすくなりました。

これらの変更に関する詳細は、[app UI updates page](whats-new-in-intune-app-ui.md] でご覧ください。

## <a name="notices"></a>通知

### <a name="improved-support-for-android-users-based-in-china---720444--"></a>中国の Android ユーザー向けのサポートが向上しました <!--720444-->

中国では Google Play ストアを利用できないため、Android デバイスの場合は中国のマーケットプレースからアプリを入手する必要があります。 ポータル サイトでは、中国の Android ユーザーをリダイレクトして、ローカルのアプリ ストアからポータル サイトおよび Outlook のアプリをダウンロードできるようにし、このワークフローをサポートします。 これにより、モバイル デバイス管理およびモバイル アプリケーション管理の両方について、条件アクセス ポリシーが有効な場合に、ユーザー エクスペリエンスが向上します。 Android 用ポータル サイト アプリおよび Outlook アプリは、次の中国のアプリ ストアで入手できます。 

- [Baidu](https://go.microsoft.com/fwlink/?linkid=836946)
- [Xiaomi](https://go.microsoft.com/fwlink/?linkid=836947)
- [Tencent](https://go.microsoft.com/fwlink/?linkid=836949)
- [Huawei](https://go.microsoft.com/fwlink/?linkid=836948)
- [Wandoujia](https://go.microsoft.com/fwlink/?linkid=836950)

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple の要求による Application Transport Security 対応のための更新<!--748318-->

Apple は、2017 年春より Application Transport Security (ATS) の特定の要件を適用すると発表しました。 ATS では、HTTPS 経由で行われるアプリ通信すべてに、より厳格なセキュリティ保護が適用されます。 この変更により、iOS/macOS ポータル サイト アプリを使用している Intune ユーザーが影響を受けます。 詳細については、[Intune サポートのブログ](https://aka.ms/compportalats)をご覧ください。

## <a name="public-preview-of-the-new-intune-admin-experience-on-azure---736542--"></a>Azure での新しい Intune 管理者エクスペリエンスのパブリック プレビュー <!--736542-->

2017 年初めには、すべての管理者エクスペリエンスが Azure に移行され、Graph API を幅広く使用する最新のサービス プラットフォーム上で、EMS の中核的ワークフローの強力な統合管理を利用できるようになります。

今月には、Azure Portal で新しい管理者エクスペリエンスのパブリック プレビューを表示する新しい試用テナントが開始されます。 プレビュー状態では、既存の Intune コンソールでの機能とパリティが繰り返し提供されます。

Azure Portal の管理者エクスペリエンスでは、既に発表されている新しいグループ化とターゲット設定の機能が使用されます。既存のテナントを新しいグループ化エクスペリエンスに移行すると、テナントの管理者エクスペリエンスも新しいプレビュー版に移行されます。 テナントを移行する前に、新しい機能をテストしたり見たりしたい場合は、新しい Intune 試用版アカウントにサインアップするか、[新しいドキュメント](https://docs.microsoft.com/en-us/intune-azure/introduction/what-is-microsoft-intune)をご覧ください。

テナント移行のスケジュールに関して質問がある場合は、Microsoft の移行チーム ([intunegrps@microsoft.com](mailto:intunegrps@microsoft.com)) にお問い合わせください。

### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>管理されていないデバイスから割り当てられているアプリにアクセス可能 <!--664691-->

ポータル Web サイトでの設計変更に伴い、iOS と Android ユーザーは、管理されていないデバイスで "登録なしで使用可能" として割り当てられているアプリをインストールできるようになります。 Intune 資格情報を使用して、ユーザーはポータル Web サイトにログインし、割り当てられているアプリの一覧を表示することができます。 "登録なしで使用可能" なアプリのアプリ パッケージは、ポータル Web サイトからダウンロードできます。 この変更は、インストールするために登録が必要なアプリには影響しません。そのようなアプリをインストールする場合は、デバイスの登録が求められます。

### <a name="improvements-to-device-actions-report---677150--"></a>Device Actions レポートの機能強化 <!--677150-->

Device Actions レポートの機能が強化され、パフォーマンスが向上しました。 さらに、レポートを状態別にフィルター処理できるようになりました。 たとえば、レポートをフィルター処理して、完了したデバイス アクションのみを表示できます。

### <a name="actions-for-non-compliance---730266--"></a>コンプライアンス非対応に対するアクション <!--730266-->

**コンプライアンス非対応に対するアクション**は、コンプライアンス非対応のデバイスに対してアクションを実行できるようにするコンプライアンス ポリシーの新しい機能です。 単一または複数のアクションを指定できます。また、実行する必要があるアクションの期間を指定することもできます。 たとえば、デバイスが非対応になった直後に電子メールで、その非対応デバイスのユーザーに通知することができます。あるいは、非対応デバイスに対して、条件付きアクセスで 3 日間の猶予期間後の企業リソースへのアクセスをブロックすることができます。

### <a name="custom-app-categories---748805--"></a>カスタム アプリのカテゴリ <!--748805-->

Intune に追加するアプリのカテゴリを作成、編集、および割り当てることができるようになりました。 現時点では、カテゴリは英語でのみ指定できます。
[Intune にアプリを追加する方法](/intune-azure/manage-apps/add-apps)に関するページを参照してください。

### <a name="assign-lob-apps-to-users-with-unenrolled-devices---748823--"></a>登録していないデバイスを使用しているユーザーに LOB アプリを割り当てる <!--748823-->

デバイスが Intune に登録されているかどうかに関係なく、基幹業務アプリをストアからユーザーに割り当てられるようになりました。 ユーザーのデバイスが Intune に登録されていない場合は、ポータル サイト アプリではなく、ポータル Web サイトに移動してインストールする必要があります。

### <a name="new-compliance-reports---846671--"></a>新しいコンプライアンス レポート <!--846671-->

コンプライアンス レポートにより、会社内のコンプライアンスの状況を表示して、社内のユーザーがコンプライアンス関連の問題に直面したときに迅速にトラブルシューティングできるようになりました。 次の情報を表示できます。

- デバイスの総合的なコンプライアンスの状態
- 設定別のコンプライアンスの状態
- ポリシー別のコンプライアンスの状態

これらのレポートを使用して個々のデバイスをドリルダウンし、そのデバイスに影響を与えている特定の設定およびポリシーを確認することもできます。

### <a name="additional-windows-10-upgrade-paths---903672--"></a>Windows 10 の追加アップグレード パス <!--903672-->

エディション アップグレード ポリシーを作成して、次のエディションの Windows 10 にもデバイスをアップグレードできるようになりました。

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N


### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Apple 登録シナリオへの直接アクセス <!--951869-->

Intune では、2017 年 1 月以降に作成された Intune アカウントについて、Azure プレビュー ポータルの Enroll Devices ワークロードを使用して、Apple 登録シナリオに直接アクセスできるようになりました。 これまでは、Apple 登録プレビューはクラシックの Intune ポータルのリンクからのみアクセスが可能でした。 2017 年 1 月より前に作成された Intune アカウントの場合は、これらの機能が Azure で利用可能になるまでの間、1 回限りの移行が必要です。 移行スケジュールはまだ発表されていませんが、詳細はできる限り早く発表します。 既存のアカウントでプレビューにアクセスできない場合は、試用アカウントを作成して、新しいエクスペリエンスをテストすることを強くお勧めします。

### <a name="see-also"></a>関連項目
最近の開発状況について詳しくは、「[Microsoft Intune の新機能](whats-new-in-microsoft-intune.md)」をご覧ください。

