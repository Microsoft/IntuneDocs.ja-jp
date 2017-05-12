---
title: "新機能 | Microsoft Docs"
description: "Microsoft Intune の今月の新機能と過去のリリースの情報について説明します"
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 04/20/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 8b2bd3ecba0b597bc742ea08872ffe8fc58155cf
ms.openlocfilehash: 0dc3fd3b4cc355bc95677ca648efdee07d1066b2
ms.contentlocale: ja-jp
ms.lasthandoff: 04/24/2017


---
# <a name="whats-new-in-microsoft-intune---april-2017"></a>Microsoft Intune の新機能 - 2017 年 4 月
Microsoft Intune の今回のリリースの新機能について説明します。 また、過去のリリースに関する情報だけでなく、準備する必要がある今後の変更についても説明します。

> [!Note]
> これらのすべての機能は、最終的にハイブリッド環境 (Configuration Manager と Intune の共存環境) でサポートされるようになります。 最新のハイブリッド機能の詳細については、[ハイブリッド環境の新機能に関するページ](https://docs.microsoft.com/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)を参照してください。

## <a name="new-capabilities"></a>新しい機能

### <a name="improved-sign-in-experience-across-company-portal-apps-for-all-platforms---user-story-1132123--"></a>すべてのプラットフォームでのポータル サイト アプリのサインイン操作の改善<!--User Story 1132123-->

Android、iOS、Windows の Intune ポータル サイト アプリのサインイン エクスペリエンスを改善中です。 Azure AD でこの変更が行われ次第、自動的にすべてのプラットフォームでポータル サイト アプリのユーザー エクスペリエンスが一新される予定です。 また、自動生成される一時使用コードを使用して、別のデバイスからポータル サイトにサインインできるようになりました。 これは、資格情報を使用せずにサインインする必要がある場合には特に便利です。

以前のサインイン エクスペリエンス、資格情報を使用した新たなエクスペリエンス、別のデバイスからのエクスペリエンスのスクリーンショットを [アプリ UI の新機能](whats-new-in-intune-app-ui.md)に関するページで確認できます。

### <a name="myapps-available-for-managed-browser---822308-822303--"></a>Managed Browser に使用できる MyApps <!--822308, 822303-->

Managed Browser での Microsoft MyApps のサポートが向上します。 管理の対象になっていない Managed Browser ユーザーは、MyApps サービスに直接送られ、そこで管理者がプロビジョニングした SaaS アプリにアクセスできます。 Intune の管理の対象になっているユーザーは、引き続き組み込みの Managed Browser ブックマークから MyApps にアクセスできます。

### <a name="new-icons-for-the-managed-browser-and-the-company-portal---918433-918431-971473--"></a>Managed Browser とポータル サイトの新しいアイコン <!--918433, 918431, 971473-->

Managed Browser の Android バージョンと iOS バージョンのアイコンが更新されます。 新しいアイコンには、Enterprise Mobility + Security (EM+S) での他のアプリとの一貫性が向上した新しい Intune バッジが含まれます。 Managed Browser 用の新しいアイコンは、[Intune アプリ UI の新機能に関するページ](whats-new-in-intune-app-ui.md)でご覧いただけます。

Android、iOS、Windows でのポータル サイト アプリのアイコンも更新されて、EM+S での他のアプリとの一貫性が向上します。 これらのアイコンは、4 月から 5 月末にかけて段階的にプラットフォーム全体にリリースされます。

### <a name="sign-in-progress-indicator-in-android-company-portal---953374--"></a>Android 用ポータル サイトでのサインイン進行状況インジケーター<!--953374-->

Android 用ポータル サイト アプリが更新されて、起動または再開時にサインイン進行状況インジケーターが表示されるようになります。 ユーザーがアプリへのアクセスを許可されるまでにインジケーターに順番に表示される新しいステータスは、[接続中...]、[サインイン中...]、[Checking for security requirements... (セキュリティ要件確認中...)] です。 Android 用ポータル サイト アプリの新しい画面は、[Intune アプリ UI の新機能](whats-new-in-intune-app-ui.md)に関するページでご覧いただけます。

### <a name="block-apps-from-accessing-sharepoint-online----679339---"></a>アプリの SharePoint Online へのアクセスをブロック<!-- 679339 -->

アプリ ベースの条件付きアクセス ポリシーを作成して、アプリ保護ポリシーが適用されていないアプリが [SharePoint Online](/InTune/deploy-use/mam-ca-for-sharepoint-online) にアクセスするのをブロックできるようになりました。 アプリ ベースの条件付きアクセスのシナリオでは、Azure Portal を使用して SharePoint Online にアクセスするアプリを指定できます。

### <a name="bulk-enroll-windows-10-devices----747607---"></a>Windows 10 デバイスを一括登録する <!-- 747607 -->

Windows 構成デザイナー (WCD) で Azure Active Directory と Intune に Windows 10 Creators Update を実行する多数のデバイスを参加させることができるようになりました。 Azure AD テナントの [一括 MDM 登録](/intune/deploy-use/bulk-enroll-windows) を有効にするには、Windows 構成デザイナーを使用して Azure AD テナントにデバイスを参加させるプロビジョニング パッケージを作成し、一括登録と管理を行う会社所有のデバイスにパッケージを適用します。 パッケージがデバイスに適用されると、デバイスは Azure AD に参加し、Intune に登録され、Azure AD ユーザーがログオンできる状態になります。  Azure AD ユーザーはこれらのデバイス上の標準ユーザーであり、割り当て済みのポリシーと必須アプリを受け取ります。 この時点では、セルフ サービスと会社ポータルのシナリオはサポートされていません。

## <a name="notices"></a>通知

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Apple 登録シナリオへの直接アクセス <!--951869-->

Intune では、2017 年 1 月以降に作成された Intune アカウントについて、Azure プレビュー ポータルの Enroll Devices ワークロードを使用して、Apple 登録シナリオに直接アクセスできるようになりました。 これまでは、Apple 登録プレビューはクラシックの Intune ポータルのリンクからのみアクセスが可能でした。 2017 年 1 月より前に作成された Intune アカウントの場合は、これらの機能が Azure で利用可能になるまでの間、1 回限りの移行が必要です。 移行スケジュールはまだ発表されていませんが、詳細はできる限り早く発表します。 既存のアカウントでプレビューにアクセスできない場合は、試用アカウントを作成して、新しいエクスペリエンスをテストすることを強くお勧めします。

### <a name="whats-coming-for-appx-in-intune-on-azure----1000270---"></a>Intune on Azure での appx に予定されている新機能 <!-- 1000270 -->

Intune on Azure への移行の一環として、appx に関して次の 3 つの変更が行われています。

1. MDM 登録デバイスに対してのみ展開できる新しい appx アプリの種類を、クラシック Intune コンソールに追加します。
2. 既存の appx アプリの種類を、Intune PC エージェントによって管理される PC のみを対象とするように用途を変更します。
3. 移行において、すべての既存 appx を MDM appx に変換します。

#### <a name="how-does-this-affect-me"></a>ユーザーへの影響

Intune PC エージェントによって管理されるデバイスへの既存の展開に対する影響はありません。 ただし、移行後に、これらの移行された appx を、Intune PC エージェントによって管理される、以前は対象になっていなかった新しいデバイスに展開することはできません。

#### <a name="what-action-do-i-need-to-take"></a>実行する必要があるアクション

移行終了後、新しい PC 展開を行いたい場合は、appx を PC appx として再アップロードする必要があります。 詳しくは、Intune サポート チーム ブログの「[Appx changes in Intune on Azure](https://aka.ms/appxchange)」 (Intune on Azure での appx の変更) をご覧ください。  


## <a name="whats-new-in-the-public-preview-of-the-intune-admin-experience-on-azure---736542--"></a>Azure での新しい Intune 管理者エクスペリエンスのパブリック プレビューの新機能<!--736542-->

2017 年初めには、すべての管理者エクスペリエンスが Azure に移行され、Graph API を幅広く使用する最新のサービス プラットフォーム上で、EMS の中核的ワークフローの強力な統合管理を利用できるようになります。

今月には、Azure Portal で新しい管理者エクスペリエンスのパブリック プレビューを表示する新しい試用テナントが開始されます。 プレビュー状態では、既存の Intune コンソールでの機能とパリティが繰り返し提供されます。

Azure Portal の管理者エクスペリエンスでは、既に発表されている新しいグループ化とターゲット設定の機能が使用されます。既存のテナントを新しいグループ化エクスペリエンスに移行すると、テナントの管理者エクスペリエンスも新しいプレビュー版に移行されます。 テナントを移行する前に、新しい機能をテストしたり見たりしたい場合は、新しい Intune 試用版アカウントにサインアップするか、[新しいドキュメント](/intune-azure/introduction/whats-new)をご覧ください。

> [!Note]
> Azure Portal プレビューについて、今月の更新プログラムを展開しています。 ただし、Intune サービスの展開方法により、変更はすぐに入手できない場合があります。  新しいポータル機能を入手できるようになる前に、サービスのいくつかのコンポーネントを順次更新する必要があります。 今後、今月ロールアウトされる Azure Portal プレビューの変更を随時ご確認ください。 変更の詳細な一覧については、「[Microsoft Intune プレビューの新機能](/intune-azure/introduction/whats-new)」をご覧ください。

### <a name="administration-roles-being-replaced-in-azure-portal"></a>Azure Portal で置き換えられる管理ロール

Intune クラシック ポータル (Silverlight) で使用される既存のモバイル アプリケーション管理 (MAM) の管理ロール (共同作成者、所有者、および読み取り専用) は、Intune Azure Portal の新しいロール ベースの管理制御 (RBAC) の完全なセットで置き換えられます。 Azure Portal に移行すると、管理者をこれらの新しい管理ロールに割り当て直す必要があります。 RBAC と新しいロールの詳細については、[Microsoft Intune のロール ベースのアクセス制御](/intune-azure/access-control/role-based-access-control)に関する記事を参照してください。


## <a name="whats-coming"></a>今後の更新情報

### <a name="plan-for-change-intune-is-changing-the-intune-partner-portal-experience----1050016---"></a>変更の計画: Intune で Intune パートナー ポータル エクスペリエンスが変更されます<!-- 1050016 -->

2017 年 5 月中旬のサービス更新で、Intune パートナーのページが manage.microsoft.com から削除されます。  

お客様がパートナーの管理者である場合は、Intune パートナーのページで顧客に代わって閲覧したり、操作したりすることができなくなります。代わりに、マイクロソフトの他の 2 つのパートナー ポータルのいずれかでサインインする必要があります。

[Microsoft パートナー センター](https://partnercenter.microsoft.com/)と [Microsoft Office 365 パートナー管理センター](https://portal.office.com/)の両方で、管理している顧客アカウントにサインインできます。 パートナーとして前進するために、これらのサイトのいずれかを使用して顧客の管理を行いましょう。 


### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple の要求による Application Transport Security 対応のための更新<!--748318-->

Apple は、2017 年春より Application Transport Security (ATS) の特定の要件を適用すると発表しました。 ATS では、HTTPS 経由で行われるアプリ通信すべてに、より厳格なセキュリティ保護が適用されます。 この変更により、iOS ポータル サイト アプリを使用している Intune ユーザーが影響を受けます。 詳細については、[Intune サポートのブログ](https://aka.ms/compportalats)をご覧ください。

### <a name="see-also"></a>関連項目
* [Microsoft Intune のブログ](http://go.microsoft.com/fwlink/?LinkID=273882)
* [クラウド プラットフォームのロードマップ](https://www.microsoft.com/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Azure プレビューの新機能](https://docs.microsoft.com/intune-azure/introduction/whats-new)
* [ポータル Web サイトの UI の新機能](https://docs.microsoft.com/intune/whats-new/whats-new-in-company-portal-ui)
* [新機能の公開履歴](whats-new-archive.md)

