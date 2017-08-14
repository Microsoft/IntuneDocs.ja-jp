---
title: "Intune とエンド ユーザー アプリの UI の更新"
description: "Intune を使用したエンド ユーザー デバイスで動作するアプリの UI の変更点について説明します。"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 08/01/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b782e382-8deb-48a7-a437-d7c5a17163f1
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 948a7d2e4e0ad80088d864708db5733f08db77c5
ms.sourcegitcommit: 79116d4c7f11bafc7c444fc9f5af80fa0b21224e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2017
---
# <a name="ui-updates-for-intune-end-user-apps"></a>Intune とエンド ユーザー アプリの UI の更新
このリリースの Microsoft Intune でエンド ユーザーに表示されるアプリの UI に加えられた変更について説明します。 これは、ユーザーとの通信や、展開のサポートのために作成したカスタム ドキュメントの更新に役立ちます。 会社のポータルを使用してヘルプデスクにサポートを求める場合に、直面している問題のトラブルシューティングをより適切に行う方法を理解するのにも役立ちます。

## <a name="week-of-july-31-2017"></a>2017 年 7 月 31 日の週

### <a name="improved-sign-in-experience-across-company-portal-apps-for-all-platforms---user-story-1132123--"></a>すべてのプラットフォームでのポータル サイト アプリのサインイン操作の改善<!--User Story 1132123-->

Android、iOS、Windows での Intune ポータル サイト アプリのサインイン エクスペリエンス向上のために、今後数か月間に予定されている変更についてお知らせします。 Azure AD でこの変更が行われ次第、自動的にすべてのプラットフォームでポータル サイト アプリのユーザー エクスペリエンスが一新される予定です。 また、自動生成される一時使用コードを使用して、別のデバイスからポータル サイトにサインインできるようになりました。 この機能は、資格情報を使用せずにサインインする必要がある場合には特に便利です。  

以下に、従来のサインイン、資格情報を使用した新たなサインイン、別のデバイスからのサインインをそれぞれ以下に示します。

__従来のサインイン エクスペリエンス__

![Web サイトのイメージ図の前にユーザーのアイコンが表示されたポータル サイトのサインイン ページ。 アイコンの下に [サインイン] ボタンが表示されています。 下部にあるリンクから Microsoft のプライバシーと Cookie に関する情報にアクセスできます。](./media/cp_ios_aad_signin_before_1704_001.png)

![[サインイン] をタップした後に、このページで資格情報を入力します。電子メールとパスワードが要求され、パスワードのエラーを解決する方法も提供されます。](./media/cp_ios_aad_signin_before_1704_002.png)

![パスワードを入力すると、ポータル サイト アプリはサインインを行い、読み込みバーが表示されます。](./media/cp_ios_aad_signin_before_1704_003.png)

__新たなサインイン エクスペリエンス__

![Web サイトのイメージ図の前にユーザーのアイコンが表示されたポータル サイトのサインイン ページ。 アイコンの下に [サインイン] ボタンが表示されています。 下部にあるリンクから Microsoft のプライバシーと Cookie に関する情報にアクセスできます。](./media/cp_ios_aad_signin_after_1704_001.png)

![画面は同じですが電子メールとパスワードではなく、電子メールのみを入力するように要求されます。](./media/cp_ios_aad_signin_after_1704_002.png)

![電子メールが承認されると、パスワードの入力が要求されます。](./media/cp_ios_aad_signin_after_1704_003.png)

![認証プロセスが終了すると、ポータル サイト アプリはサインインを行い、読み込みバーが表示されます。](./media/cp_ios_aad_signin_from_another_device_after_1704_007.png)

__別のデバイスからサインインする際の新たなサインイン エクスペリエンス__

![Web サイトのイメージ図の前にユーザーのアイコンが表示されたポータル サイトのサインイン ページ。 アイコンの下に [サインイン] ボタンが表示されています。 下部にあるリンクから Microsoft のプライバシーと Cookie に関する情報にアクセスできます。](./media/cp_ios_aad_signin_from_another_device_after_1704_001.png)

__[別のデバイスからサインインする]__ リンクをタップします。

![会社のコンピューターから固有のパスワードで aka.ms/devicelogin ページにアクセスし、コードを使用してサインインするように指示されます。](./media/cp_ios_aad_signin_from_another_device_after_1704_003.png)

ブラウザーを起動して、[https://aka.ms/devicelogin](https://aka.ms/devicelogin) にアクセスします。

![ポータル サイト アプリの画像ではなく会社のコンピューターのブラウザーの画像です。 [デバイス ログイン] ページが表示され、ポータル サイト アプリで取得したコードを入力するように要求されます。](./media/cp_ios_aad_signin_from_another_device_after_1704_004.png)

ポータル サイト アプリで表示されたコードを入力します。 __[続行]__ を選択すると、スマートカードなど、お客様の会社でサポートされている任意の方法を使用して認証を行うことができます。

![固有のコードをフィールドに入力すると、[デバイス ログイン] サイトから、Intune ポータル サイトがサインインを許可してよい適切なアプリであることを確認されます。](./media/cp_ios_aad_signin_from_another_device_after_1704_005.png)

![デバイスでポータル サイト アプリへのログインが完了したことと、このページを閉じることができることを示す確認ページ。](./media/cp_ios_aad_signin_from_another_device_after_1704_006.png)

ポータル サイト アプリがサインインを開始します。

![認証プロセスが終了すると、ポータル サイト アプリはサインインを行い、読み込みバーが表示されます。](./media/cp_ios_aad_signin_from_another_device_after_1704_007.png)

## <a name="week-of-june-12-2017"></a>2017 年 6 月 12 日の週

### <a name="company-portal-app-for-android-now-has-a-new-end-user-experience-for-app-protection-policies---1305217--"></a>Android 用ポータル サイト アプリのアプリ保護ポリシーの新しいエンド ユーザー エクスペリエンス <!--1305217-->
ユーザーのフィードバックに基づいて、Android 用ポータル サイト アプリに **[会社のコンテンツにアクセスする]** ボタンが表示されるようになりました。 このボタンの目的は、Intune モバイル アプリケーション管理の機能であるアプリ保護ポリシーをサポートするアプリにアクセスすることだけが必要なユーザーが、不要な登録プロセスを経なくて済むようにすることです。

ユーザーはデバイスの登録を始める代わりに **[会社のコンテンツにアクセスする]** ボタンをタップします。

![Android ポータル サイト アプリの画像。標準では登録オプションがすぐに表示されますが、ここでは中央に "会社のコンテンツにアクセスする" という大きなテキストを確認できます。](./media/and_access_company_content_after_1706.png)

ポータル Web サイトが表示されるので、デバイスで使用するアプリを承認します。ポータル Web サイトで資格情報が確認されます。

![ポータル Web サイトのサインイン確定画像。](./media/and_iwp_sign_in_auth_page_after_1706.png)

**[アクション]** メニューをタップすれば、引き続き完全管理にデバイスを登録できます。

![Android 向けポータル サイト アプリの画像。画面の右上隅にメニューが表示されています。デバイスを登録するためのオプションがあります。](./media/and_sign_in_menu_after_app_protection_policy_enrolled_after_1706.png)

### <a name="improvements-to-app-syncing-with-windows-10-creators-update---676505--"></a>Windows 10 Creators Update とアプリを同期する機能の強化 <!--676505-->

Windows 10 用ポータル サイト アプリでは、Windows 10 Creators Update (バージョン 1703) がインストールされているデバイスのアプリ インストール要求の同期が自動的に開始されるようになりました。 "同期保留中" 状態中、アプリ インストールが止まる問題を減らします。 また、ユーザーはアプリ内から同期を手動で開始できます。

![Windows 10 ポータル サイト アプリの画像。ポータル サイト アプリ ストアからの Microsoft Word のダウンロードが保留になっています。](./media/w10_download_pending_after_1706.png)

![Windows 10 ポータル サイト アプリの画像。自動同期が新たに行われている状態を確認できます。デバイスが同期中であり、アプリのダウンロードを試行している旨の状態メッセージが表示されています。](./media/w10_download_pending_syncing_after_1706.png)

### <a name="new-guided-experience-for-windows-10-company-portal----1058938---"></a>Windows 10 ポータル サイトの新しいガイド機能 <!---1058938--->
Windows 10 用のポータル サイト アプリで、特定または登録されていないデバイス向けのガイド付き Intune チュートリアルを利用できるようになります。 ユーザーは新たな段階的手順に従って、Azure Active Directory (条件付きアクセス機能のために必要) と MDM (デバイス管理機能のために必要) に登録できます。 このガイドには、ポータル サイトのホーム ページからアクセスできます。 ユーザーは登録が完了していなくても引き続きアプリを使用できますが、機能は制限されます。

この更新は、Windows 10 Anniversary Update (ビルド 1607) 以降を実行しているデバイスのみで表示されます。

![Windows 10 ポータル サイト アプリのランディング ページの画像。"デバイス" リストの中央に状態メッセージが表示されており、会社の使用がまだ設定されておらず、ユーザーはメッセージを選択し、設定を開始してくださいとユーザーに伝えています。](./media/win10_guided_enroll_select_setup_after_1706.png)

![Windows 10 ポータル サイト アプリの設定ページの画像。管理に登録するには、このデバイスに会社のアカウントを追加する必要があるとユーザーに警告しています。](./media/win10_guided_enroll_we_help_setup_after_1706.png)

![Windows 10 ポータル サイト アプリの "このデバイスに会社のアカウントを追加する" ページの画像。設定アプリに進み、"接続" を選択して登録を完了する必要があると伝えています。 その作業の後、ポータル サイト アプリに戻り、登録を完了する必要があることが伝えられます。](./media/win10_guided_enroll_leaving_for_iwp_after_1706.png)

![Windows 10 ポータル サイト アプリの "管理に登録する" 画面の画像。完了状態メッセージを確認できます。ユーザーのデバイスが登録されており、 '次へ' ボタンをタップして続行するように伝えています。](./media/win10_guided_enroll_youre_now_enrolled_after_1706.png)

![Windows 10 ポータル サイト アプリの完了画面の画像。すべて設定済みであり、デバイスに適切に追加された会社のアカウントでデバイスが登録されたことをユーザーに知らせています。](./media/win10_guided_enroll_youre_all_set_after_1706.png)

### <a name="new-menu-action-to-easily-remove-company-portal---1164569--"></a>ポータル サイトを簡単に削除できるアクション メニューの追加<!--1164569-->
Android 用ポータル サイト アプリでは、ユーザーからのフィードバックに基づき、デバイスからポータル サイトの削除を開始できる新しいアクション メニューが追加されました。 この操作では Intune の管理対象からデバイスが削除されるため、ユーザーはデバイスからアプリを削除できるようになります。

![右上隅にアクション メニューが開いた Android 用ポータル サイト アプリの画像です。 [マイ プロファイル]、[設定] の下と、[使用条件]、[ヘルプとフィードバック]、[概要] の上に、新しい [ポータル サイトの削除] オプションが 3 つ目のオプションとして表示されます。](./media/android_remove_cp_menu_action_after_1705.png)

![アクション メニューから新しい [ポータル サイトの削除] オプションを選択した後に表示される確認ダイアログの画像です。 "ポータル サイトの削除により、デバイスは IT 管理者による管理を離れ、会社のデータ、会社のアプリ、会社の電子メールに対するデバイスのアクセス権限が削除される可能性がある" ことを示すダイアログが表示されます。 [はい] を選択すると、ポータル サイト アプリを削除するか確認するメッセージが表示されます。](./media/android_remove_cp_menu_confirmation_after_1705.png)

## <a name="week-of-june-5-2017"></a>2017 年 6 月 5 日の週

### <a name="improvements-to-the-app-tiles-in-the-company-portal-app-for-ios"></a>iOS 用ポータル サイト アプリのアプリ タイルを改善
ポータル サイトに設定したブランド カラーが反映されるよう、ホーム ページのアプリ タイルのデザインを一新しました。

**更新前**

!["すべてのアプリ"、"おすすめアプリ"、"カテゴリ" の事前設定の画像が表示された更新前の iOS 用ポータル サイト アプリの画像。](./media/cp_ios_homepage_before_1705.png)

**更新後**

![組織に関連するカラーを選択できる機能が反映された、更新後の iOS 用ポータル サイト アプリの画像。](./media/cp_ios_homepage_after_1705.png)

### <a name="account-picker-now-available-for-the-company-portal-app-for-ios"></a>iOS 用ポータル サイト アプリでアカウント選択の提供を開始
iOS デバイスで、職場または学校アカウントを使用して別の Microsoft アプリにサインインしたことのあるユーザーが、ポータル サイトに初めてサインインしようとすると、新しいアカウントの選択が表示される場合があります。

![テスト ユーザー "Robin Swanson" が 2 つのメール アドレスのうち 1 つを選択していることを示す、アカウント選択の画像。 2 つのアドレスの下には、ユーザーが別のアカウントでサインインできるボタンがあります。](./media/cp_ios_multi-account-selector-after-1705.png)

## <a name="april-2017"></a>2017 年 4 月

### <a name="new-icons-for-the-managed-browser-and-the-company-portal---918433-918431--"></a>Managed Browser とポータル サイトの新しいアイコン <!--918433, 918431-->

Managed Browser の Android バージョンと iOS バージョンのアイコンが更新されます。 新しいアイコンには、Enterprise Mobility + Security (EM+S) での他のアプリとの一貫性が向上した新しい Intune バッジが含まれます。

<html>
<body>
   <table id="wrapper">
      <tr>
         <td>
            <img src="/intune/media/cp_manbro_before_042017.png" alt="The previous version of the Managed Browser app icon." width=200 height=366 align=center>
          </td>
          <td>
             <img src="/intune/media/cp_manbro_after_042017.png" alt="The updated version of the Managed Browser app icon." width=200 height=366 align=center>
           </td>
      </tr>
   </table>
</body>
</html>

Android、iOS、Windows でのポータル サイト アプリのアイコンも更新されて、EM+S での他のアプリとの一貫性が向上します。 これらのアイコンは、4 月から 5 月末にかけて段階的にプラットフォーム全体にリリースされます。

### <a name="sign-in-progress-indicator-in-android-company-portal---953374--"></a>Android 用ポータル サイトでのサインイン進行状況インジケーター<!--953374-->

Android 用ポータル サイト アプリが更新されて、起動または再開時にサインイン進行状況インジケーターが表示されるようになります。 ユーザーがアプリへのアクセスを許可されるまでにインジケーターに順番に表示される新しいステータスは、[接続中...]、[サインイン中...]、[Checking for security requirements... (セキュリティ要件確認中...)] です。

<html>
<body>
   <table id="wrapper">
      <tr>
         <td>
            <img src="/intune/media/cp_android_connecting_042017.png" alt="The Company Portal app for Android sign in screen that shows a partially filled loading bar with the phrase 'Connecting' underneath it." width=200 height=366 align=center>
          </td>
          <td>
             <img src="/intune/media/cp_android_signing_in_042017.png" alt="The Company Portal app for Android sign in screen that shows a partially filled loading bar with the phrase 'Signing in' underneath it." width=200 height=366 align=center>
           </td>
           <td>
              <img src="/intune/media/cp_android_checking_security_reqs_042017.png" alt="The Company Portal app for Android sign in screen that shows a partially filled loading bar with the phrase 'Checking for security requirements' underneath it." width=200 height=366 align=center>
           </td>
      </tr>
   </table>
</body>
</html>

### <a name="improved-app-install-status-for-the-windows-10-company-portal-app---676495--"></a>Windows 10 ポータル サイト アプリのアプリ インストール状態の向上<!--676495-->
現在の Windows 10 ポータル サイト アプリでは、アプリ詳細ページにインストール進行状況バーが表示されます。 これは、Windows 10 Anniversary Update 以降を実行するデバイスの最新アプリについてサポートされます。

__変更前__ ![変更前のバージョンの読み込み画面の画像。状態は単に 'インストール中' と表示されていました。](./media/cp_win10_install_status_before_1704.png)

__変更後__ ![変更後のバージョンの読み込み画面の画像。インストール進行状況バーが表示されるようになりました。](./media/cp_win10_install_status_after_1704.png)

## <a name="february-2017"></a>2017 年 2 月

### <a name="new-user-experience-for-the-company-portal-app-for-android---621622-announced-1702--"></a>Android 用ポータル サイト アプリに関する新しいユーザー エクスペリエンス <!--621622, announced 1702-->
3 月以降、Android 用ポータル サイト アプリでは[材料設計ガイドライン](https://material.io/guidelines/material-design/introduction.html)に従って、最新の外観が作成されます。 この改善されたユーザー エクスペリエンスには、次のものが含まれます。

* __色__: タブ ヘッダーを、カスタムの色パレットに従って色付けすることができます。

![左側は、更新前の Android 用ポータル サイト アプリのイメージです。 右側は、更新後の Android 用ポータル サイト アプリのイメージです。 両方のイメージに、[アプリ]、[デバイス]、および [IT に連絡] の使用可能な 3 つのタブから選択されたタブとして、[デバイス] タブが示されています。](./media/CP_Android_DevicesTab_BeforeAfter.png)

* __インターフェイス__: __[アプリ]__ タブの __[おすすめアプリ]__ ボタンと __[すべてのアプリ]__ ボタンが更新されました。 __[検索]__ ボタンは浮動アクション ボタンになりました。

![左側は、更新前の Android 用ポータル サイト アプリのイメージです。 右側は、更新後の Android 用ポータル サイト アプリのイメージです。 両方のイメージに、[アプリ]、[デバイス]、および [IT に連絡] の使用可能な 3 つのタブから選択されたタブとして、[アプリ] タブが示されています。](./media/CP_Android_AppsTab_BeforeAfter.png)

* __ナビゲーション__: [すべてのアプリ] で __[おすすめ]__、__[すべて]__ および __[カテゴリ]__ のタブ付きビューが表示され、移動がより簡単になります。 __[IT に連絡]__ が簡素化され、読みやすくなりました。

<html>
<body>
   <table id="wrapper">
      <tr>
         <td>
            <img src="/intune/media/cp_android_contactit_after.png" alt="The Company Portal app for Android displaying an updated version of the Contact IT tab. The tab shows available contact information for IT, including phone number, email address, IT website, and IT contact information." width=200 height=366 align=center>
          </td>
      </tr>
   </table>
</body>
</html>

## <a name="january-2017"></a>2017 年 1 月

### <a name="modernizing-the-company-portal-website---753980-announced-1701--"></a>ポータル Web サイトの進化 <!--753980, announced 1701-->
2 月から、ポータル Web サイトで管理対象のデバイスを持っていないユーザーを対象とするアプリをサポートします。 この Web サイトは、新しいコントラストの配色パターン、動的な図、および "ハンバーガー メニュー"  ![(ヘルプデスクの連絡先詳細や既存の管理対象デバイスに関する情報を含む、](./media/CP_hamburger_menu.png) ポータル Web サイトの左上隅に新たに追加されたハンバーガー メニューの小さなイメージ) を使用することで、Microsoft の他の製品やサービスと連携します。 ランディング ページはユーザーが利用できるアプリをわかりやすくするために再配置され、おすすめのアプリや最近更新されたアプリはカルーセル ビューで表示されます。

![左側は、以前のバージョンの [アプリ]、[デバイス]、[おすすめ] ビュー、[カテゴリ] ビューが表示された、会社のポータル Web サイトの現在のバージョンのイメージです。 右側は、更新されたアプリ カルーセル、[Recently Published apps (最近公開されたアプリ)] のリスト、更新された [カテゴリ] ビューが表示された、会社のポータル Web サイトの更新バージョンのイメージです。](./media/CP_Website_BeforeAfter_Feb2016.png)

## <a name="coming-soon-in-the-ui"></a>UI で近日公開予定
これらは、ユーザー インターフェイスを更新することによってユーザー エクスペリエンスを向上させるために計画されている方法です。

> [!Note]
> 次のイメージはプレビューであり、発表される製品は示されているバージョンとは異なる場合があることに注意してください。

### <a name="ui-updates-to-the-company-portal-website---1313244-part-2--"></a>ポータル Web サイトの UI の更新 <!--1313244 part 2-->

__おすすめアプリの更新__ サイトにおすすめとして選択したアプリを参照できる専用ページを追加し、ホームページのおすすめセクションでいくつかの UI の修正を行いました。

![アプリが表示されたカラフルなタイル。 各アプリの大きな四角形の色は、アプリのロゴに主に使われている色から取られています。 "おすすめアプリ" セクションはポータル サイト アプリの一番上に表示されます。](./media/cp_win10_colorful_tiles_after_1708.png)

### <a name="see-also"></a>関連項目
* [Microsoft Intune のブログ](http://go.microsoft.com/fwlink/?LinkID=273882)
* [クラウド プラットフォームのロードマップ](https://www.microsoft.com/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Intune の新機能](https://docs.microsoft.com/intune/whats-new)
