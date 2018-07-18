---
title: Intune とエンド ユーザー アプリの UI の更新
titlesuffix: Microsoft Intune
description: Microsoft Intune を使用したエンド ユーザー デバイスで動作するアプリの UI の変更点について説明します。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 03/29/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: b782e382-8deb-48a7-a437-d7c5a17163f1
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 998df5181b553b33b570cd78d7f0e490336d7e95
ms.sourcegitcommit: 024cce10a99b12a13f32d3995b69c290743cafb8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/14/2018
ms.locfileid: "39039388"
---
# <a name="ui-updates-for-intune-end-user-apps"></a>Intune とエンド ユーザー アプリの UI の更新
このリリースの Microsoft Intune でエンド ユーザーに表示されるアプリの UI に加えられた変更について説明します。 これらの更新を理解すると、ユーザーとの通信や、展開のサポートのために作成したカスタム ドキュメントの更新に役立ちます。 会社のポータルを使用してヘルプデスクにサポートを求める場合に、直面している問題のトラブルシューティングをより適切に行う方法を理解するのにも役立ちます。

<!---End-user messaging for accounts 1573558, 1712; changes to be made for other platforms for 1801 Users of the Company Portal website, will be blocked from taking actions that require write access to your tenant. They will see appropriate error messaging explaining that their account is under maintenance. Similar changes are coming to the Company Portal apps for Android, iOS, macOS, and Windows soon. ![Error message that occurs during account move](./media/account-move-rom-iwp-user-1712.png)--->

## <a name="week-of-april-23-2018"></a>2018 年 4 月 23 日の週
#### <a name="updated-navigation-view-in-the-company-portal-app-for-windows-10----1195010---"></a>Windows 10 用の Intune ポータル サイト アプリでのナビゲーション ビューの更新 <!-- 1195010 -->
Windows 10 の Intune ポータル サイト アプリが [Fluent Design System のナビゲーション ビュー](https://docs.microsoft.com/windows/uwp/design/basics/navigation-basics)に合わせて更新されました。 アプリの側面だけでなく、すべてのトップ レベルのページに静的な縦方向リストが表示されます。 リンクをクリックすると、ページをすばやく表示したり、ページを切り替えたりできます。 これは現在作成中の更新の一部であり、今後さらにアダプティブで馴染みがあり、使いやすい Intune の機能を提供していきます。 

![Fluent デザイン ナビゲーション ビューが示されている Intune ポータル サイト アプリのダッシュボードのスクリーンショット](./media/1804_WindowsCP_Fluent_01.png)


## <a name="week-of-april-2-2018"></a>2018 年 4 月 2 日の週

#### <a name="user-experience-update-for-the-company-portal-app-for-ios----1412866---"></a>iOS 用ポータル サイト アプリに関するユーザー エクスペリエンスの更新プログラム <!-- 1412866 -->
iOS 用のポータル サイト アプリに対して、主要なユーザー エクスペリエンスの更新プログラムをリリースする予定です。 この更新プログラムでは、最新のルック アンド フィールを含む完全なビジュアル再設計が行われています。 アプリの機能を維持した上で、操作性とアクセシビリティが向上しています。  

また、次のような更新が行われています。
- iPhone X のサポート。
- アプリの起動および読み込み応答を速くして、ユーザー時間を節約。
- 最新の状態情報をユーザーに提供するための進行状況バーを追加。
- ログのアップロード方法を改善。これにより、問題が生じた場合に、その内容を簡単にレポートできる。  

|以前|これらの手順の完了後、|
|---|---|
|![01](/intune/media/cp_iosRedesign_before_1803_01.png)|![01](/intune/media/cp_iosRedesign_after_1803_01.png)|
|*前のステップと結合*|![02](/intune/media/cp_iosRedesign_after_1803_02.png)|
|![03](/intune/media/cp_iosRedesign_before_1803_02.png)|![03](/intune/media/cp_iosRedesign_after_1803_03.png)|

#### <a name="improvements-to-the-language-in-the-company-portal-app-for-windows----1683758---"></a>Windows 用ポータル サイト アプリの言語を改善 <!---1683758--->
ユーザーにわかりやすく、組織に特有の言語となるように、Windows 10 用ポータル サイトの言語に改善を加えました。

|以前|これらの手順の完了後、|
|---|---|
|![01](./media/windows_enroll_before_1803.png)|![01](./media/windows_enroll_after_1803.png)|
|![02](./media/windows_view_policy_issues_before_1803.png)|![02](./media/windows_view_policy_issues_after_1803.png)

## <a name="week-of-march-12-2018"></a>2018 年 3 月 12 日の週

#### <a name="company-portal-for-android-visual-updates---976944---"></a>Android 用 Intune ポータル サイトのビジュアルの更新 <!--976944 -->

Android 用 Intune ポータル サイト アプリを、Android の[マテリアル デザイン](https://material.io/) ガイドラインに合わせて更新しています。

|以前|これらの手順の完了後、|
|---|---|
|![01](./media/android_about_before_1803.png)|![01](./media/androidCP_about_after_1803.png)|
|![02](./media/android_contact_it_before_1803.png)|![02](./media/android_contact_it_after_1803.png)|
|![03](./media/android_devices_before_1803.png)|![03](./media/androidCP_devicelist_after_1803.png)|
|![04](./media/android_device_details_before_1803.png)|![05](./media/androidCP_devicedetails_1_after1803.png)|
|![05](./media/android_device_details_update_settings_before_1803.png)|![05](./media/androidCP_devicedetails_red_box_2_after1803.png)|
|![06](./media/android_profile_before_1803.png)|![06](./media/android_profile_after_1803.png)|
|![07](./media/androidCP_Setup01_before_1803.png)|![07](./media/androidCP_Setup01_after_1803.png)|


## <a name="week-of-november-27-2017"></a>2017 年 11 月 27 日の週

### <a name="new-device-categories-step-in-guided-setup-for-the-company-portal-app-for-windows-10----1335292---"></a>Windows 10 用ポータル サイト アプリのガイド付きセットアップでの新しい [デバイス カテゴリ] ステップ <!---1335292--->

[デバイス グループ マッピング](device-group-mapping.md)が有効になっている場合、Windows 10 用ポータル サイト アプリのセットアップで、ユーザーはデバイスを登録した後にデバイスのカテゴリを選ぶようになりました。

![デバイス グループ マッピングのカテゴリ](./media/w10_cp_category_device_setup_after_1711.png)

## <a name="week-of-november-13-2017"></a>2017 年 11 月 13 日の週

### <a name="improvements-to-device-setup-workflow-in-the-company-portal-for-ios-in-version-290----1417174---"></a>iOS 用ポータル サイト バージョン 2.9.0 でのデバイスのセットアップ ワークフローの機能強化<!-- 1417174 -->

iOS 用ポータル サイト アプリでのデバイス セットアップ ワークフローを改善しました。 言葉がよりわかりやすくなり、可能な範囲で画面をまとめました。 また、セットアップのテキスト全体でお客様の会社名を使用することで、表現がより会社に合ったものになっています。

> [!NOTE]
> **[Microsoft Intune]** > **[モバイル アプリ]** > **[ポータル サイトのブランド化]** > **[会社名]** の Azure Portal で設定した会社名が使用されています。 この値を設定していない場合、**[Azure Active Directory]** > **[プロパティ]** > **[名前]** で設定したテナント名が使用されます。 [ポータル サイトのブランド化] で会社名を設定しておらず、テナント名を表示させたくない場合は、[ポータル サイトのブランド化] タブで会社名を設定することをお勧めします。この文字列をポータル サイトのヘッダーに表示させたくない場合は、[Show company name next to logo]\(ロゴの横に会社名を表示する\) チェックボックスをオフにすることができます。

|以前|これらの手順の完了後、|
|---|---|
|![01](./media/ios_cp_enroll_01_before_1711.png)|![01](./media/ios_cp_enroll_01_after_1711.png)|
|![02](./media/ios_cp_enroll_02_before_1711.png)|*前のステップと結合*|
|![03](./media/ios_cp_enroll_03_before_1711.png)|![03](./media/ios_cp_enroll_03_after_1711.png)|
|![04](./media/ios_cp_enroll_04_before_1711.png)|![04](./media/ios_cp_enroll_04_after_1711.png)|
|![05](./media/ios_cp_enroll_05_before_1711.png)|![05](./media/ios_cp_enroll_05_after_1711.png)|
|![06](./media/ios_cp_enroll_06_before_1711.png)|![06](./media/ios_cp_enroll_06_after_1711.png)|
|![07](./media/ios_cp_enroll_07_before_1711.png)|![07](./media/ios_cp_enroll_07_after_1711.png)|


## <a name="week-of-november-6-2017"></a>2017 年 11 月 6 日の週

### <a name="updates-to-the-company-portal-app-for-windows-10---1299474--"></a>Windows 10 用ポータル サイト アプリの更新内容 <!--1299474-->
Windows 10 用ポータル サイト アプリの [設定] ページが更新され、すべての設定で、設定と目的のユーザー アクションの一貫性が高まっています。 また、その他の Windows アプリのレイアウトと一致させる更新も行われています。

|以前|これらの手順の完了後、|
|---|---|
|![01](./media/w10-share-logs.png)|![02](./media/w10-share-logs-after-1711.png)|


### <a name="search-improvements-to-the-company-portal-apps-and-website---1418189--"></a>ポータル サイト アプリおよび Web サイトの検索機能強化 <!--1418189-->
ポータル サイト アプリでは、アプリのカテゴリ、名前、説明で検索できるようになりました。 結果は関連性の高い順に並べ替えられます。 これらの更新は、[ポータル Web サイト](https://portal.manage.microsoft.com)でも利用可能です。

マイクロソフトは関連性の追跡方法を微調整しています。ポータル Web サイトの一番下にある "フィードバック" リンクから調整具合をお知らせください。

## <a name="week-of-october-16-2017"></a>2017 年 10 月 16 日の週

### <a name="search-improvements-to-the-company-portal-website---1331697--"></a>ポータル Web サイトの検索機能強化 <!--1331697-->
マイクロソフトはアプリの検索機能を強化しています。その最初が[ポータル Web サイト](https://portal.manage.microsoft.com)です。 名前フィールドや説明フィールドだけでなく、アプリ カテゴリでも検索できるようになりました。 結果は既定で、関連性の降順で並べ替えられます。 

iOS ユーザーもこの変更の影響を受けます。ポータル Web サイトは、iOS のポータル サイト アプリの一部としても利用されるためです。 Android と Windows のポータル サイト アプリも数か月後に同じように更新されます。

マイクロソフトは関連性の追跡方法を微調整しています。ポータル Web サイトの一番下にある "フィードバック" リンクから調整具合をお知らせください。


### <a name="ios-company-portal-displays-large-icons----1454593---"></a>iOS ポータル サイトでの大きいアイコンの表示 <!-- 1454593 -->
このリリースでは、iOS ポータル サイトのアプリ タイルでのアイコンの表示方法に関する既知の問題が修正されました。 現在は、120 x 120 ピクセル以上のアプリ アイコンをアップロードすると、[ポータル Web サイト](https://portal.manage.microsoft.com)内と iOS ポータル サイトのアプリ ページ内で、アプリ タイルのフル サイズで表示されます。


## <a name="week-of-october-2-2017"></a>2017 年 10 月 2 日の週

#### <a name="improvements-to-device-setup-workflow-in-company-portal---1490692--"></a>ポータル サイトでのデバイスのセットアップ ワークフローの機能強化<!--1490692-->
Android 用のポータル サイト アプリでデバイスのセットアップ ワークフローを改良しました。 言語がよりわかりやすく、会社固有のものとなり、可能な範囲で画面をまとめるようにしました。 

|以前|これらの手順の完了後、|
|---|---|
|![01](./media/android_cp_enroll_01_post_1709.png)|![01](./media/android_cp_enroll_01_1709_new.png)|
|![01a](./media/android_cp_enroll_01_before_1710.png)| *前のステップと結合* |
|![02](./media/android_cp_enroll_02_before_1710.png)|![02](./media/android_cp_enroll_02_after_1710.png)|
|![03](./media/android_cp_enroll_03_before_1710.png)|![03](./media/android_cp_enroll_03_after_1710.png)|

Android 仕事用プロファイル デバイスで追加のステップが強化されました。

|以前|これらの手順の完了後、|
|---|---|
|![04](./media/android_work_cp_enroll_01_before_1710.png)|![04](./media/android_work_cp_enroll_01_after_1710.png)|
|![05](./media/android_work_cp_enroll_02_before_1710.png)| *前のステップと結合* |
|![06](./media/android_work_cp_enroll_03_before_1710.png)|![06](./media/android_work_cp_enroll_03_after_1710.png)|
|![07](./media/android_work_cp_enroll_04_before_1710.png)|![07](./media/android_work_cp_enroll_04_after_1710.png)|
|![08](./media/android_work_cp_enroll_05_before_1710.png)| *前のステップと結合* |


電子メールへの条件付きアクセスのアクティブ化画面も更新しました。

|以前|これらの手順の完了後、|
|---|---|
|![06](./media/android_conditional_access_email_before_1710.png)|![06](./media/android_conditional_access_email_after_1710.png)

## <a name="week-of-september-11-2017"></a>2017 年 9 月 11 日の週

### <a name="easier-to-understand-phrasing-for-the-company-portal-app-for-android----1396349---"></a>Android 用ポータル サイト アプリの文言をわかりやすいように変更 <!---1396349--->  

Android 用ポータル サイト アプリについて、エンドユーザーが登録しやすくなるよう、テキストを変更して登録プロセスを簡易化しました。 カスタム登録ドキュメントがある場合は、新しい画面が反映されるように更新できます。 以下でサンプル画像を確認できます。

|以前|これらの手順の完了後、|
|---|---|
|![01](./media/android_cp_enroll_01_before_1709.png)|![01](./media/android_cp_enroll_01_post_1709.png)|
|![02](./media/android_cp_enroll_02_before_1709.png)|![02](./media/android_cp_enroll_02_post_1709.png)|
|![03](./media/android_cp_enroll_03_before_1709.png)|![03](./media/android_cp_enroll_03_post_1709.png)|
|![04](./media/android_cp_enroll_04_before_1709.png)|![04](./media/android_cp_enroll_04_post_1709.png)|
|![05](./media/android_cp_enroll_05_before_1709.png)|![05](./media/android_cp_enroll_05_post_1709.png)|


## <a name="august-2017"></a>2017 年 8 月

### <a name="ios-11-mail-app-will-support-oauth----1196951---"></a>iOS 11 のメール アプリが OAuth をサポート <!---1196951--->

Intune での条件付きアクセスで、OAuth を使用した iOS デバイスのより安全な認証がサポートされます。 これをサポートし、より安全な認証を可能にするため、iOS のポータル サイト アプリに異なるフローが生成されます。 エンドユーザーがメール アプリで新しい Exchange アカウントにサインインしようとすると、Web ビューのプロンプトが表示されます。 Intune に登録すると、ネイティブのメール アプリによる証明書へのアクセスを許可するプロンプトがユーザーに表示されます。 ほとんどのエンドユーザーにはそれ以上の検疫済みメールは表示されません。 既存のメール アカウントは引き続き基本認証プロトコルを使用するため、これに該当するユーザーには検疫済みメールが配信されます。 このエンド ユーザー向けサインイン エクスペリエンスは Office モバイル アプリの場合と似ています。

![ネイティブ メール アプリでアカウントの種類を選択します。](./media/ios-11-ca-email-after-1708-01.png)

![Exchange を選択すると、iOS デバイスのプロンプトで電子メール アドレスとアカウント名が求められます。](./media/ios-11-ca-email-after-1708-02.png)

![電子メール アドレスとアカウント名を入力します。](./media/ios-11-ca-email-after-1708-03.png)

![Microsoft の外部ログイン ページに移動します。](./media/ios-11-ca-email-after-1708-04.png)

![Microsoft のページでパスワードを入力します。](./media/ios-11-ca-email-after-1708-05.png)

![Microsoft からユーザーに管理するデバイスを登録するように求められます。](./media/ios-11-ca-email-after-1708-06.png)

![ユーザーはポータル Web サイトから登録するように求められます。](./media/ios-11-ca-email-after-1708-07.png)



### <a name="intune-mobile-application-management-mam-dialog-boxes-will-have-a-modern-interface----1199015---"></a>Intune モバイル アプリケーション管理 (MAM) ダイアログ ボックスの現代的インターフェイス <!-- 1199015 -->

Intune モバイル アプリケーション管理 (MAM) ダイアログ ボックスが現代的な外観に変更されます。 このダイアログ ボックスは、以前と同じように使用できます。

**以前の操作性**

![以前のインターフェイス](./media/NewUI_Old_AttachFileHandler.jpg)

**現代的な操作性**

![現代的なインターフェイス](./media/NewUI_Modern_AttachFileHandler.jpg)


### <a name="updates-to-the-device-details-page-on-the-company-portal-app-for-windows-10----1287448---"></a>Windows 10 のポータル サイト アプリの "デバイスの詳細" ページの更新 <!---1287448--->

Windows 10 のポータル サイト アプリで、__[デバイスの詳細]__ ページで __[カテゴリ]__ タグがタイトルの下からプロパティに移動しました。

![Windows ポータル サイト アプリの "デバイスの詳細" 画面。"カテゴリ" フィールドが画面のタイトルのすぐ下ではなく、プロパティとして表示されています。](./media/cp_win10_category_tag_move_after_1708.png)

## <a name="july-2017"></a>2017 年 7 月

### <a name="apps-details-pages-will-display-new-information-for-android-devices---1287476--"></a>[アプリの詳細] ページでの Android デバイスの新しい情報の表示 <!--1287476-->

Android 用のポータル サイト アプリのアプリの詳細ページに、IT 管理者がそのアプリに対して定義したアプリのカテゴリが表示されるようになります。

![新しいアプリの詳細ポリシー](./media/cp_android_appdetails_after_1708.png)

### <a name="improved-sign-in-experience-across-company-portal-apps-for-all-platforms---user-story-1132123--"></a>すべてのプラットフォームでのポータル サイト アプリのサインイン操作の改善<!--User Story 1132123-->

Android、iOS、Windows 用の Intune ポータル サイト アプリのサインイン エクスペリエンス向上のために、今後数か月間に予定されている変更についてお知らせします。 Azure AD でこの変更が行われ次第、自動的にすべてのプラットフォームでポータル サイト アプリのユーザー エクスペリエンスが一新される予定です。 また、自動生成される一時使用コードを使用して、別のデバイスからポータル サイトにサインインできるようになりました。 これは、資格情報を使用せずにサインインする必要がある場合には特に便利です。  

以下に、従来のサインイン、資格情報を使用した新たなサインイン、別のデバイスからのサインインをそれぞれ以下に示します。

__従来のサインイン エクスペリエンス__

![Web サイトのイメージ図の前にユーザーのアイコンが表示されたポータル サイトのサインイン ページ。 その下に [サインイン] ボタンが表示されています。 下部にあるリンクから Microsoft のプライバシーと Cookie に関する情報にアクセスできます。](./media/cp_ios_aad_signin_before_1704_001.png)

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

ブラウザーを起動し、[https://aka.ms/devicelogin](https://aka.ms/devicelogin) に移動します。

![ポータル サイト アプリの画像ではなく会社のコンピューターのブラウザーの画像です。 [デバイス ログイン] ページが表示され、ポータル サイト アプリで取得したコードを入力するように要求されます。](./media/cp_ios_aad_signin_from_another_device_after_1704_004.png)

ポータル サイト アプリで表示されたコードを入力します。 __[続行]__ を選択すると、スマートカードなど、お客様の会社でサポートされている任意の方法を使用して認証を行うことができます。

![固有のコードをフィールドに入力すると、[デバイス ログイン] サイトから、Intune ポータル サイトがサインインを許可してよい適切なアプリであることを確認されます。](./media/cp_ios_aad_signin_from_another_device_after_1704_005.png)

![デバイスでポータル サイト アプリへのログインが完了したことと、このページを閉じることができることを示す確認ページ。](./media/cp_ios_aad_signin_from_another_device_after_1704_006.png)

ポータル サイト アプリがサインインを開始します。

![認証プロセスが終了すると、ポータル サイト アプリはサインインを行い、読み込みバーが表示されます。](./media/cp_ios_aad_signin_from_another_device_after_1704_007.png)

## <a name="june-2017"></a>2017 年 6 月

### <a name="company-portal-app-for-android-now-has-a-new-end-user-experience-for-app-protection-policies"></a>Android 用ポータル サイト アプリのアプリ保護ポリシーの新しいエンド ユーザー エクスペリエンス
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
Windows 10 用のポータル サイト アプリで、特定または登録されていないデバイス向けのガイド付き Intune チュートリアルを利用できるようになります。 ユーザーは新たな段階的手順に従って、Azure Active Directory (条件付きアクセス機能のために必要) と MDM (デバイス管理機能のために必要) に登録できます。 このガイドには、ポータル サイトのホーム ページからアクセスできます。 ユーザーは、これらの登録を完了していない場合でも引き続きアプリを使用できますが、機能が制限されます。

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

### <a name="improvements-to-the-app-tiles-in-the-company-portal-app-for-ios---1230777--"></a>iOS 用ポータル サイト アプリのアプリ タイルを改善 <!--1230777-->
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
            <img src="/intune/media/cp_manbro_before_042017.png" alt="The previous version of the Managed Browser app icon." width="200" height="366" align="center">
          </td>
          <td>
             <img src="/intune/media/cp_manbro_after_042017.png" alt="The updated version of the Managed Browser app icon." width="200" height="366" align="center">
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
            <img src="/intune/media/cp_android_connecting_042017.png" alt="The Company Portal app for Android sign-in screen that shows a partially filled loading bar with the phrase 'Connecting' underneath it." width="200" height="366" align="center">
          </td>
          <td>
             <img src="/intune/media/cp_android_signing_in_042017.png" alt="The Company Portal app for Android sign-in screen that shows a partially filled loading bar with the phrase 'Signing in' underneath it." width="200" height="366" align="center">
           </td>
           <td>
              <img src="/intune/media/cp_android_checking_security_reqs_042017.png" alt="The Company Portal app for Android sign-in screen that shows a partially filled loading bar with the phrase 'Checking for security requirements' underneath it." width="200" height="366" align="center">
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

* __インターフェイス__: __[アプリ]__ タブの __[おすすめアプリ]__ ボタンと __[すべてのアプリ]__ ボタンが更新されました。__[検索]__ ボタンは浮動アクション ボタンになりました。

![左側は、更新前の Android 用ポータル サイト アプリのイメージです。 右側は、更新後の Android 用ポータル サイト アプリのイメージです。 両方のイメージに、[アプリ]、[デバイス]、および [IT に連絡] の使用可能な 3 つのタブから選択されたタブとして、[アプリ] タブが示されています。](./media/CP_Android_AppsTab_BeforeAfter.png)

* __ナビゲーション__: [すべてのアプリ] で __[おすすめ]__、__[すべて]__ および __[カテゴリ]__ のタブ付きビューが表示され、移動がより簡単になります。 __[IT に連絡]__ が簡素化され、読みやすくなりました。

<html>
<body>
   <table id="wrapper">
      <tr>
         <td>
            <img src="/intune/media/cp_android_contactit_after.png" alt="The Company Portal app for Android displaying an updated version of the Contact IT tab. The tab shows available contact information for IT, including phone number, email address, IT website, and IT contact information." width="200" height="366" align="center">
          </td>
      </tr>
   </table>
</body>
</html>

## <a name="january-2017"></a>2017 年 1 月

### <a name="modernizing-the-company-portal-website---753980-announced-1701--"></a>ポータル Web サイトの進化 <!--753980, announced 1701-->
2 月から、ポータル Web サイトでマネージド デバイスを持っていないユーザーを対象とするアプリをサポートします。 この Web サイトは、新しいコントラストの配色パターン、動的な図、および "ハンバーガー メニュー"  ![(ヘルプデスクの連絡先詳細や既存の管理対象デバイスに関する情報を含む、](./media/CP_hamburger_menu.png) ポータル Web サイトの左上隅に新たに追加されたハンバーガー メニューの小さなイメージ) を使用することで、Microsoft の他の製品やサービスと連携します。 ランディング ページはユーザーが利用できるアプリをわかりやすくするために再配置され、おすすめのアプリや最近更新されたアプリはカルーセル ビューで表示されます。

![左側は、以前のバージョンの [アプリ]、[デバイス]、[おすすめ] ビュー、[カテゴリ] ビューが表示された、会社のポータル Web サイトの現在のバージョンのイメージです。 右側は、更新されたアプリ カルーセル、[Recently Published apps (最近公開されたアプリ)] のリスト、更新された [カテゴリ] ビューが表示された、会社のポータル Web サイトの更新バージョンのイメージです。](./media/CP_Website_BeforeAfter_Feb2016.png)

## <a name="coming-soon-in-the-ui"></a>UI で近日公開予定
これらは、ユーザー インターフェイスを更新することによってユーザー エクスペリエンスを向上させるために計画されている方法です。

> [!Note]
> 次のイメージはプレビューであり、発表される製品は示されているバージョンとは異なる場合があることに注意してください。

### <a name="ui-iwp"></a>ポータル Web サイトの新しいユーザー エクスペリエンスの更新<!--2000968-->

UI の更新、ワークフローの簡素化、ユーザー補助機能の改善を備えた新しいポータル Web サイトのエクスペリエンスを、8 月から導入します。 これには、アプリ共有などのお客様の要望に基づいた機能拡張や、よりユーザー フレンドリなエクスペリエンスを提供するための全体的なパフォーマンスの向上などが含まれます。

お客様からのフィードバックに基づいて、既存の機能と使いやすさを大幅に向上させる新しい機能もいくつか追加されています。

-   Web サイト全体の UI の機能強化
-   アプリへの直接リンクを共有する機能
- 大規模なアプリケーション カタログのパフォーマンスの向上

この変更の準備のために何かを行う必要はありません。 更新されたポータル Web サイトが利用可能になったら、お知らせいたします。 ただし、最終的には、更新されたスクリーンショットを使用して、エンド ユーザーのドキュメントを更新する必要があります。 また、Web サイトは iOS アプリの **[アプリ]** セクションに影響するため、iOS のポータル サイト アプリのドキュメントも更新する必要があることに注意してください。

|更新済み|前へ|
|---|---|
|![更新済みのデバイス ページでは、デバイスが完全なリストの上にポップアップ表示されるのではなく、デバイス情報の上にきれいに配置されて表示されます。](./media/iwp-device-after-1803.png)|![以前のバージョンのデバイス ページ。](./media/iwp-device-before-1803.png)|
|![更新されたアプリのインストール ページには、説明とさまざまなインストール情報 (発行日、バージョン、およびアプリの種類など) の上に、そのアプリがわかりやすく表示されます。](./media/iwp-app-install-after-1803.png)|![以前のバージョンのアプリのインストール ページ。](./media/iwp-app-install-before-1803.png)|

### <a name="ui-updates-to-the-company-portal-website---1313244-part-2--"></a>ポータル Web サイトの UI の更新 <!--1313244 part 2-->

__おすすめアプリの更新__ サイトにおすすめとして選択したアプリを参照できる専用ページを追加し、ホームページのおすすめセクションでいくつかの UI の修正を行いました。

![アプリが表示されたカラフルなタイル。 各アプリの大きな四角形の色は、アプリのロゴに主に使われている色から取られています。 "おすすめアプリ" セクションはポータル サイト アプリの一番上に表示されます。](./media/cp_win10_colorful_tiles_after_1708.png)



### <a name="see-also"></a>関連項目
* [Microsoft Intune のブログ](http://go.microsoft.com/fwlink/?LinkID=273882)
* [クラウド プラットフォームのロードマップ](https://www.microsoft.com/cloud-platform/roadmap)
* [Intune の新機能](https://docs.microsoft.com/intune/whats-new)
