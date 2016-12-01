---
title: "初期エディション | Microsoft Intune"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 11/22/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f287a0ad082fa20a2e84abbf8f5585117aae6f57
ms.openlocfilehash: e604b8809bd444d9069d449a6c691a8444296623


---

# <a name="the-early-edition-for-microsoft-intune---december"></a>Microsoft Intune の初期エディション - 12 月

**初期エディション**では、Microsoft Intune の今後のリリースで予定されている新機能を一覧します。 ここに記載されている情報は、秘密保持契約書のもとごく限られた範囲について開示されたものであり、また今後変更される可能性があります。 ここに挙げられている機能は、発売日に間に合わない可能性があり、その場合は将来のリリースを待たなければなりません。 正式なリリースに向けてパイロット (フライト) テスト中の機能もあります。 ご不明な点や懸念される事項がある場合は、Intune の開発チームまたは PM にお問い合わせください。

このページは定期的に更新されます。 適宜確認してください。

Intune に関して以下の機能が現在開発されています。 これらのすべての機能は、最終的にハイブリッド環境 (Configuration Manager と Intune の共存環境) でサポートされるようになります。 最新のハイブリッド機能の詳細については、[ハイブリッド環境の新機能に関するページ](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx)を参照してください。

<!--736542-->
## <a name="public-preview-of-the-new-intune-admin-experience-on-azure"></a>Azure での新しい Intune 管理者エクスペリエンスのパブリック プレビュー

2017 年初めには、すべての管理者エクスペリエンスが Azure に移行され、Graph API を幅広く使用する最新のサービス プラットフォーム上で、EMS の中核的ワークフローの強力な統合管理を利用できるようになります。

今月には、Azure Portal で新しい管理者エクスペリエンスのパブリック プレビューを表示する新しい試用テナントが開始されます。 プレビュー状態では、既存の Intune コンソールでの機能とパリティが繰り返し提供されます。

Azure Portal の管理者エクスペリエンスでは、既に発表されている新しいグループ化とターゲット設定の機能が使用されます。既存のテナントを新しいグループ化エクスペリエンスに移行すると、テナントの管理者エクスペリエンスも新しいプレビュー版に移行されます。 テナントを移行する前に、新しい機能をテストしたり見たりしたい場合は、新しい Intune 試用版アカウントにサインアップするか、新しいドキュメントをご覧ください。

テナント移行のスケジュールに関して質問がある場合は、Microsoft の移行チーム ([intunegrps@microsoft.com](mailto:intunegrps@microsoft.com)) にお問い合わせください。

### <a name="telecom-expense-management-integration-in-public-preview-of-azure-portal--747605--"></a>Azure Portal のパブリック プレビューでの電気通信経費管理の統合<!--747605-->
Azure Portal では、サード パーティの電気通信経費管理 (TEM) サービスとの統合のプレビューが始められています。 Intune を使用して、国内およびローミングのデータ使用量を制限できます。 これらの統合は、[Saaswedo](http://www.saaswedo.com) で始まっています。

## <a name="new-capabilities"></a>新しい機能

### <a name="multi-factor-authentication-across-all-platforms---747590--"></a>すべてのプラットフォームでの多要素認証 <!--747590-->
Azure Active Directory で Microsoft Intune 登録アプリケーションに多要素認証 (MFA) を構成することにより、Azure の管理ポータルから iOS、Android、Windows 8.1+、または Windows Phone 8.1+ デバイスを登録すると、選択したユーザー グループに MFA を適用できます。

### <a name="conditional-access-for-mam-with-sharepoint-online---vso-679339--"></a>SharePoint Online での MAM に対する条件付きアクセス<!--VSO 679339-->
Intune モバイル アプリ管理 (MAM) ポリシーによってサポートされていないアプリによる SharePoint Online へのアクセスをブロックできます。  Intune モバイル アプリ管理は、Azure Portal で使用することができます。 __[設定]__ ブレードの __[条件付きアクセス]__ セクションに SharePoint Online のオプションがあります。 この機能は、サービス リリースの他の部分とは別に出荷されます。

## <a name="notices"></a>通知

### <a name="multi-factor-authentication-on-enrollment-moving-to-the-azure-portal---vso-750545--"></a>Azure Portal に移動する登録での多要素認証 <!--VSO 750545-->
これまで、Intune の登録に MFA を設定するには、Intune コンソールまたは構成マネージャー (リリース 1610 より前) コンソールを使用しました。 この機能更新により、今後は Intune の資格情報で [Microsoft Azure Portal ](https://manage.windowsazure.com)にログインし、Azure AD を使用して MFA の設定を構成するようになります。 詳細については、[こちら](https://aka.ms/mfa_ad)をご覧ください。

### <a name="company-portal-app-for-android-now-available-in-china---vso-658093--"></a>中国で利用可能になった Android 用ポータル サイト アプリ <!--VSO 658093-->
Android 用ポータル サイト アプリが中国でダウンロードできるようになりました。 中国には Google Play ストアがないので、Android デバイスは中国のアプリ マーケットプレースからアプリを入手する必要があります。 Android 用ポータル サイト アプリは、360、Tencent、Xiaomi、Wandoujia、Huawei でダウンロードできます。 

Android 用ポータル サイト アプリは、Google Play 開発者サービスを使って Microsoft Intune サービスと通信します。 中国では Google Play 開発者サービスをまだ利用できないので、次のタスクには最大 8 時間かかることがあります。 

|Intune 管理コンソール| Android 用 Intune ポータル サイト アプリ |Intune ポータル サイト Web サイト|   
|---|---|---|
|フル ワイプ| リモート デバイスの削除| デバイスの削除 (ローカルおよびリモート)|
|選択的ワイプ| デバイスのリセット| デバイスのリセット|
|新規アプリまたは更新アプリの展開| 使用可能な基幹業務アプリのインストール| デバイスのパスコードのリセット|
|リモート ロック|||
|パスコードのリセット|||

## <a name="deprecations"></a>廃止予定

### <a name="removal-of-exchange-online-mobile-inbox-policies---770687--"></a>Exchange Online のモバイル受信トレイ ポリシーの削除 <!--770687-->
12 月以降、管理者は Intune コンソールで Exchange Online (EAS) モバイル メールボックス ポリシーを表示または構成できなくなります。 この変更は、12 月から 1 月にかけてすべての Intune テナントに展開されます。 既存のすべてのポリシー構成は今までどおりですが、新しいポリシーの構成には Exchange 管理シェルを使います。 詳しくは、[こちら](https://technet.microsoft.com/en-us/library/bb123783%28v=exchg.150%29.aspx)をご覧ください。

### <a name="intune-av-player-image-viewer-and-pdf-viewer-apps-are-no-longer-supported-on-android---747553--"></a>Android での Intune AV Player、Image Viewer、PDF Viewer アプリのサポート終了 <!--747553-->
2016 年 12 月中旬以降、Intune AV Player、Image Viewer、PDF Viewer の各アプリを使用できなくなります。 これらのアプリの代わりに、Azure Information Protection アプリが使用できるようになります。 Azure Information Protection アプリについて詳しくは、[こちら](https://docs.microsoft.com/information-protection/rms-client/mobile-app-faq)をご覧ください。

### <a name="see-also"></a>関連項目
最近の開発状況について詳しくは、「[Microsoft Intune の新機能](whats-new-in-microsoft-intune.md)」をご覧ください。



<!--HONumber=Nov16_HO4-->


