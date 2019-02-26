---
title: 初期エディション - Microsoft Intune
titlesuffix: ''
description: Microsoft Intune の初期エディション
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/04/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: b1ff65e1b48815cd5964aa7498fa6ba54df50e09
ms.sourcegitcommit: e5f501b396cb8743a8a9dea33381a16caadc51a9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/23/2019
ms.locfileid: "56742297"
---
# <a name="the-early-edition-for-microsoft-intune---february-2019"></a>Microsoft Intune の初期エディション - 2019 年 2 月

> [!Note]
> NDA 通知: Intune に関して以下の機能が現在開発されています。 この情報は、NDA に基づき、非常に限られた範囲で共有されます。 Twitter、UserVoice、Reddit などの、ソーシャル メディアやパブリック Web サイトには、この情報を投稿しないでください。 

**初期エディション**では、Microsoft Intune の今後のリリースで予定されている、NDA に基づいて共有される新機能のリストを提供します。 ここに記載されている情報は、限られた範囲について開示されたものであり、また今後変更される可能性があります。 ツイート、UserVoice への投稿、またそれ以外の方法で、社外でこの情報を共有したりしないでください。 ここに挙げられている機能は、発売日に間に合わない可能性があり、その場合は将来のリリースを待たなければなりません。 正式なリリースに向けてパイロット (フライト) テスト中の機能もあります。 ご不明な点や懸念される事項がある場合は、Microsoft 製品グループにお問い合わせください。

このページは定期的に更新されます。 適宜確認してください。

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Azure Portal での Intune
<!-- 1902 start-->


<!-- 1901 start -->

### <a name="deployment-of-online-licensed-microsoft-store-for-business-apps----1672660----"></a>オンラインでライセンスされたビジネス向け Microsoft Store アプリの展開 <!-- 1672660  -->
オンラインでライセンスされた必要なビジネス向け Microsoft Store アプリをデバイスのコンテキストで割り当てることができます。 このようにして、ビジネス向け Microsoft Store アプリを展開すると、デバイス上のすべてのユーザーにアプリをインストールできます。 対象は Windows 10 RS4 以上のデスクトップ デバイスのみです。 デバイスのコンテキストでインストールするオプションは、MSFB オンラインのライセンスされたアプリのクライアント アプリの割り当てページにあります。

<!-- 1812 start -->

### <a name="android-enterprise-app-we-app-deployment----1171203---"></a>Android エンタープライズ APP-WE アプリの展開 <!-- 1171203 -->
登録のないアプリ保護ポリシー (APP-WE) の展開シナリオでの Android では、managed Google Play を使用してストア アプリと LOB アプリをユーザーに展開できます。 具体的には、IT はエンド ユーザーに、不明なソースからのインストールを許可することによってデバイスのセキュリティ状態を損なう必要がないアプリ カタログとインストール エクスペリエンスを提供できます。 さらに、この展開シナリオでは、向上したエンド ユーザー エクスペリエンスが提供されます。

### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation-----1927359---"></a>Intune ポリシーでの認証方法とポータル サイト アプリのインストールの更新 <!-- 1927359 -->
Apple の会社用デバイスの登録方法のいずれかを使ってセットアップ アシスタント経由で既に登録されているデバイスの場合、Intune では、特定のデバイスで App Store からインストールされる場合に、ポータル サイト アプリがサポートされなくなります。 この変更は、登録時に Apple セットアップ アシスタントで認証を行う場合にのみ関係があります。 また、この変更は、以下から登録される iOS デバイスのみに影響します。  
* Apple Configurator
* Apple Business Manager
* Apple School Manager
* Apple Device Enrollment Program (DEP)

App Store からポータル サイト アプリをインストールした後、これらのデバイスを登録しようとすると、エラーが発生します。 登録時に Intune によって自動的にプッシュされた場合、これらのデバイスはポータル サイトだけを使用することが期待されます。 Azure portal での Intune の登録プロファイルは、デバイスの認証方法およびポータル サイト アプリを受信するかどうかを指定できるように更新されます。 DEP デバイス ユーザーがポータル サイトを使用するようにしたい場合は、登録プロファイルでユーザー設定を指定する必要があります。 さらに、ポータル サイト アプリの **[デバイスの特定]** 画面はまもなく古くなります。  
既に登録されている DEP デバイスにポータル サイトをインストールするには、Intune で [クライアント アプリ] に移動し、アプリ構成ポリシーでマネージド アプリとしてプッシュする必要があります。 これらの手順を実行する方法の詳細については、将来のドキュメントで説明します。

### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>管理用テンプレートがパブリック プレビューになり、専用の構成プロファイルに移動される <!-- 3322847 -->
Intune の管理用テンプレート (**[デバイス構成]** > **[管理用テンプレート]**) は現在、プライベート プレビュー段階です。 この更新プログラムでは: 管理用テンプレートには Intune で管理可能な約 300 の設定が含まれます。 以前は、これらの設定はグループ ポリシー エディターにのみ存在しました。
管理用テンプレートはパブリック プレビューで使用できます。管理用テンプレートは、**[デバイス構成]** > **[管理用テンプレート]** から、**[デバイス構成]** > **[プロファイル]** >**[プロファイルの作成]** を選択し、**[プラットフォーム]** で **[Windows 10 以降]** を選択し、**[プロファイルの種類]** で **[管理用テンプレート]** を選択した場所に移動されています。
レポートが有効にされます。適用先: Windows 10 以降

### <a name="intune-macos-company-portal-dark-mode----3300524---"></a>Intune の macOS ポータル サイトのダーク モード <!-- 3300524 -->
Intune の macOS ポータル サイトで、macOS 用にダーク モードがサポートされるようになりました。 macOS 10.14 以降のデバイスでダーク モードを有効にすると、Intune ポータル サイトではそのモードの色に外観が調整されます。

<!-- 1809 start -->  

### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>Web データ用のアプリ保護ポリシー (APP) 設定 <!-- 2662995 -->
Android デバイスと iOS デバイスの両方での Web コンテンツに対する APP ポリシー設定は、http リンクと https Web リンクの両方の処理、ならびに iOS ユニバーサル リンクおよび Android アプリ リンクを介したデータ転送の処理をより適切に行えるように更新されます。  

<!-- 1808 start -->

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>別の MDM によって使用される Apple VPP トークン <!-- 1488946 -->
Intune では、Apple のボリューム購入プログラム (VPP) トークンが Intune と別の MDM の両方で使用されている場合、詳細が検出され、表示されます。

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>[デバイスのポリシー準拠] ダッシュボードのデバイスが廃止に <!-- 1981119 -->
今後の更新で、廃止になっているデバイスが [デバイスのポリシー準拠] ダッシュボードから削除されます。 それにより、コンプライアンス番号が変更されます。

## <a name="notices"></a>通知

現在のところ、アクティブな通知はありません。

### <a name="see-also"></a>関連項目
最近の開発状況について詳しくは、「[Microsoft Intune の新機能](whats-new.md)」をご覧ください。
