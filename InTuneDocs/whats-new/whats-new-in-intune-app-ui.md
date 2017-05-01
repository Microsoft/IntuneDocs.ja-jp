---
title: "Intune とエンド ユーザー アプリの UI の更新 | Microsoft Docs"
description: "Intune を使用したエンド ユーザー デバイスで動作するアプリの UI の変更点について説明します。"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 04/20/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b782e382-8deb-48a7-a437-d7c5a17163f1
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 62dcb40ad5a7921c514a9d41da14b991e39f3bcd
ms.openlocfilehash: f4a48b889702147abe20fd513fdb0f774020a54a
ms.lasthandoff: 04/20/2017


---
# <a name="ui-updates-for-intune-end-user-apps"></a>Intune とエンド ユーザー アプリの UI の更新
このリリースの Microsoft Intune でエンド ユーザーに表示されるアプリの UI に加えられた変更について説明します。 これは、ユーザーとの通信や、展開のサポートのために作成したカスタム ドキュメントの更新に役立ちます。 会社のポータルを使用してヘルプデスクにサポートを求める場合に、直面している問題のトラブルシューティングをより適切に行う方法を理解するのにも役立ちます。

> [!Note]
> 次のイメージはプレビューであり、発表される製品は示されているバージョンとは異なる場合があることに注意してください。

## <a name="april-2017"></a>2017 年 4 月

### <a name="improved-sign-in-experience-across-company-portal-apps-for-all-platforms---user-story-1132123--"></a>すべてのプラットフォームでのポータル サイト アプリのサインイン操作の改善<!--User Story 1132123-->

Android、iOS、Windows の Intune ポータル サイト アプリのサインイン エクスペリエンスを改善中です。  Azure AD でこの変更が行われ次第、自動的にすべてのプラットフォームでポータル サイト アプリのユーザー エクスペリエンスが一新される予定です。 また、自動生成される一時使用コードを使用して、別のデバイスからポータル サイトにサインインできるようになりました。 この機能は、資格情報を使用せずにサインインする必要がある場合には特に便利です。  

以下に、従来のサインイン、資格情報を使用した新たなサインイン、別のデバイスからのサインインをそれぞれ以下に示します。

__従来のサインイン エクスペリエンス__

![Web サイトのイメージ図の前にユーザーのアイコンが表示されたポータル サイトのサインイン ページ。 アイコンの下に [サインイン] ボタンが表示されています。 下部にあるリンクから Microsoft のプライバシーと Cookie に関する情報にアクセスできます。](./media/cp_ios_aad_signin_before_1704_001.png)

![[サインイン] をタップした後に、このページで資格情報を入力します。電子メールとパスワードが要求され、パスワードのエラーを解決する方法も提供されます。](./media/cp_ios_aad_signin_before_1704_002.png)

![パスワードを入力すると、ポータル サイト アプリはサインインを行い、読み込みバーが表示されます。](./media/cp_ios_aad_signin_before_1704_003.png)

__新たなサインイン エクスペリエンス__

![Web サイトのイメージ図の前にユーザーのアイコンが表示されたポータル サイトのサインイン ページ。 アイコンの下に [サインイン] ボタンが表示されています。 下部にあるリンクから Microsoft のプライバシーと Cookie に関する情報にアクセスできます。](./media/cp_ios_aad_signin_after_1704_001.png)

![画面は同じですが電子メールとパスワードではなく、電子メールのみを入力するように要求されます。](./media/cp_ios_aad_signin_after_1704_002.png)

![電子メールが承認されると、パスワードの入力が要求されます。](./media/cp_ios_aad_signin_after_1704_003.png)

__別のデバイスからサインインする際の新たなサインイン エクスペリエンス__

![Web サイトのイメージ図の前にユーザーのアイコンが表示されたポータル サイトのサインイン ページ。 アイコンの下に [サインイン] ボタンが表示されています。 下部にあるリンクから Microsoft のプライバシーと Cookie に関する情報にアクセスできます。](./media/cp_ios_aad_signin_from_another_device_after_1704_001.png)

__[別のデバイスからサインインする]__ リンクをタップします。

![画面は同じですが電子メールとパスワードではなく、電子メールのみを入力するように要求されます。 [別のデバイスからサインインする] リンクが、電子メール フィールドの下に表示されます。](./media/cp_ios_aad_signin_from_another_device_after_1704_002.png)

![会社のコンピューターから固有のパスワードで aka.ms/devicelogin ページにアクセスし、コードを使用してサインインするように指示されます。](./media/cp_ios_aad_signin_from_another_device_after_1704_003.png)

ブラウザーを起動して、[http://aka.ms/devicelogin](https://aka.ms/devicelogin) にアクセスします。

![ポータル サイト アプリの画像ではなく会社のコンピューターのブラウザーの画像です。 [デバイス ログイン] ページが表示され、ポータル サイト アプリで取得したコードを入力するように要求されます。](./media/cp_ios_aad_signin_from_another_device_after_1704_004.png)

ポータル サイト アプリで表示されたコードを入力します。 __[続行]__ を選択すると、スマートカードなど、お客様の会社でサポートされている任意の方法を使用して認証を行うことができます。

![固有のコードをフィールドに入力すると、[デバイス ログイン] サイトから、Intune ポータル サイトがサインインを許可してよい適切なアプリであることを確認されます。](./media/cp_ios_aad_signin_from_another_device_after_1704_005.png)

![デバイスでポータル サイト アプリへのログインが完了したことと、このページを閉じることができることを示す確認ページ。](./media/cp_ios_aad_signin_from_another_device_after_1704_006.png)

ポータル サイト アプリがサインインを開始します。

![認証プロセスが終了すると、ポータル サイト アプリはサインインを行い、読み込みバーが表示されます。](./media/cp_ios_aad_signin_from_another_device_after_1704_007.png)

### <a name="new-icons-for-the-managed-browser-and-the-company-portal---918433-918431--"></a>Managed Browser とポータル サイトの新しいアイコン <!--918433, 918431-->

Managed Browser の Android バージョンと iOS バージョンのアイコンが更新されます。 新しいアイコンには、Enterprise Mobility + Security (EM+S) での他のアプリとの一貫性が向上した新しい Intune バッジが含まれます。

<html>
<body>
   <table id="wrapper">
      <tr>
         <td>
            <img src="https://docs.microsoft.com/InTune/whats-new/media/cp_manbro_before_042017.png" alt="The previous version of the Managed Browser app icon." width=200 height=366 align=center>
          </td>
          <td>
             <img src="https://docs.microsoft.com/InTune/whats-new/media/cp_manbro_after_042017.png" alt="The updated version of the Managed Browser app icon." width=200 height=366 align=center>
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
            <img src="https://docs.microsoft.com/InTune/whats-new/media/cp_android_signing_in_042017.png" alt="The Company Portal app for Android sign in screen that shows a partially filled loading bar with the phrase 'Connecting' underneath it." width=200 height=366 align=center>
          </td>
          <td>
             <img src="https://docs.microsoft.com/InTune/whats-new/media/cp_android_checking_security_reqs_042017.png" alt="The Company Portal app for Android sign in screen that shows a partially filled loading bar with the phrase 'Signing in' underneath it." width=200 height=366 align=center>
           </td>
           <td>
              <img src="https://docs.microsoft.com/InTune/whats-new/media/cp_android_connecting_042017.png" alt="The Company Portal app for Android sign in screen that shows a partially filled loading bar with the phrase 'Checking for security requirements' underneath it." width=200 height=366 align=center>
           </td>
      </tr>
   </table>
</body>
</html>

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
            <img src="https://docs.microsoft.com/InTune/whats-new/media/cp_android_contactit_after.png" alt="The Company Portal app for Android displaying an updated version of the Contact IT tab. The tab shows available contact information for IT, including phone number, email address, IT website, and IT contact information." width=200 height=366 align=center>
          </td>
      </tr>
   </table>
</body>
</html>

## <a name="january-2017"></a>2017 年 1 月

### <a name="modernizing-the-company-portal-website---753980-announced-1701--"></a>ポータル Web サイトの進化 <!--753980, announced 1701-->
2 月から、ポータル Web サイトで管理対象のデバイスを持っていないユーザーを対象とするアプリをサポートします。 この Web サイトは、新しいコントラストの配色パターン、動的な図、および "ハンバーガー メニュー"  ![(ヘルプデスクの連絡先詳細や既存の管理対象デバイスに関する情報を含む、](./media/CP_hamburger_menu.png) ポータル Web サイトの左上隅に新たに追加されたハンバーガー メニューの小さなイメージ) を使用することで、Microsoft の他の製品やサービスと連携します。 ランディング ページはユーザーが利用できるアプリをわかりやすくするために再配置され、おすすめのアプリや最近更新されたアプリはカルーセル ビューで表示されます。

![左側は、以前のバージョンの [アプリ]、[デバイス]、[おすすめ] ビュー、[カテゴリ] ビューが表示された、会社のポータル Web サイトの現在のバージョンのイメージです。 右側は、更新されたアプリ カルーセル、[Recently Published apps (最近公開されたアプリ)] のリスト、更新された [カテゴリ] ビューが表示された、会社のポータル Web サイトの更新バージョンのイメージです。](./media/CP_Website_BeforeAfter_Feb2016.png)


### <a name="see-also"></a>関連項目
* [Microsoft Intune のブログ](http://go.microsoft.com/fwlink/?LinkID=273882)
* [クラウド プラットフォームのロードマップ](https://www.microsoft.com/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Azure プレビューの新機能](https://docs.microsoft.com/intune-azure/introduction/whats-new)
* [新機能の公開履歴](whats-new-archive.md)

