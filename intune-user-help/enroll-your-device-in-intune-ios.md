---
title: "会社のリソースへのアクセスを設定する | Microsoft Docs"
description: "iOS デバイスを Intune で管理する方法について説明します"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 11/14/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6eeec7aa-1b07-4ce3-894c-13e09b89bdd4
searchScope: User help
ROBOTS: 
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: ee4275ec7b9b455cf6ebf032123127fde97a9a74
ms.sourcegitcommit: 0b96ae18524eb976df01a5340631ef331357e666
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2017
---
# <a name="set-up-access-to-your-company-resources"></a>会社のリソースへのアクセスを設定する

お客様の会社には、電子メール、ファイル、ネットワークなど、たくさんの機密情報があります。 お客様が iOS デバイスからそれらの情報にアクセスする場合に、会社は Microsoft Intune を使用して、情報を保護できます。 これにより、会社はそれらのリソースを管理してより安全に保つことができ、お客様は作業するのにお好きなデバイスを使用する自由が得られます。

> [!VIDEO https://channel9.msdn.com/Series/IntuneEnrollment/iOS-Enrollment/player]

> [!NOTE]
> メール アプリで会社の電子メールにアクセスしようとしている場合は、セキュリティを保つためにデバイスの管理を求められる可能性があります。 iOS デバイスから電子メールやその他の会社リソースにアクセスするには、以下の手順に従います。

## <a name="before-you-start"></a>アップグレードを開始する前に

- 開始したら、プロセス全体を完了するようにしてください。 通常、数分以上一時停止すると進行状況が停止し、やり直しが必要になります。
- このプロセスが失敗した場合は、ポータル サイト アプリに戻り、やり直す必要があります。
- Wi-Fi が使えており、お使いのデバイス上で Safari が動作していることを確認してください。
- [Intune ポータル サイト アプリ](install-and-sign-in-to-the-intune-company-portal-app-ios.md)をダウンロードして、インストールします。


## <a name="using-the-company-portal-app-to-set-up-access-to-company-resources"></a>ポータル サイト アプリを使用して会社のリソースへのアクセスを設定する

|表示される内容|説明|
|---|---|
|![下部に [サインイン] ボタンがある、ポータル サイトのサインイン画面。](./media/ios-0-cp-enroll-1711.png)|ポータル サイト アプリを開いて、**[サインイン]** をタップします。|
|![Azure AD サインイン プロンプト。](./media/ios-0a-cp-enroll-1711.png)|会社の電子メール アドレスを入力し、**[次へ]** をタップします。|
|![Azure AD パスワード プロンプト。](./media/ios-0b-cp-enroll-1711.png)|パスワードを入力し、**[サインイン]** をタップします。|
|![[Loading company resources]\(会社のリソースを読み込んでいます\) スプラッシュ スクリーン。](./media/ios-1-cp-enroll-1711.png)|読み込まれるのを待ちます。|
|![使用条件。](./media/ios-2-cp-enroll-1711.png)|使用条件を読み、**すべて同意**します。|
|![[会社アクセスのセットアップ] 画面。 現在、管理と設定の両方で解決が必要です。](./media/ios-3-cp-enroll-1711.png)|**[Get your device managed]\(デバイスを管理する\)** をタップして、お使いのデバイスから会社のリソースへアクセスできるようにするプロセスを始めます。 これを今すぐ行うことができない場合は、プロセスを **[延期]** できますが、その場合は電子メールやドキュメントなどを取得できません。|
|![[What can my company see]\(会社で表示できるリソース\) 画面。](./media/ios-4-cp-enroll-1711.png)|下部のリンクをタップして、会社で表示できるリソースの **[詳細情報]** を確認できます。 それ以外の場合は、**[続行]** をタップします。|
|![[次のステップ] 画面。](./media/ios-5-cp-enroll-1711.png)|この画面では、セットアップ時に何が行われるかについて説明します。 このプロセスを完了するには、Safari、設定アプリおよびポータル サイト アプリを使用します。 **[次へ]** をタップします。|
|![[次のステップ] で [次へ] をタップした後の読み込み画面。](./media/ios-6-cp-enroll-1711.png)||
|![登録を行うため、Safari に切り替わります。](./media/ios-7-cp-enroll-1711.png)|お使いのデバイスの管理情報を取得するため、Safari に切り替わります。|
|![設定アプリの起動を要求するシステム プロンプト。](./media/ios-8-cp-enroll-1711.png)|**[許可]** をタップして設定アプリを開き、構成プロファイルをダウンロードします。 これをインストールして、会社が企業の情報をお使いのデバイスで管理できるようにします。|
|![設定で開いたプロファイル。](./media/ios-9-cp-enroll-1711.png)|**[インストール]** をタップします。|
|![画面の下部にある [Installing profile]\(プロファイルのインストール\) モーダル ダイアログ。](./media/ios-10-cp-enroll-1711.png)|**[インストール]** をタップします。|
|![[Profile is installing]\(プロファイルをインストールしています\) 読み込み画面。](./media/ios-11-cp-enroll-1711.png)|読み込まれるのを待ちます。|
|![[プロファイル管理] 警告画面。](./media/ios-12-cp-enroll-1711.png)|Apple によって書かれたこの警告は、管理下のデバイスで行うことができる操作の種類の詳細を示します。 詳細については、[会社が確認できる情報](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md)に関するページをご覧ください。|
|![リモート管理の信頼について質問するシステム プロンプト。](./media/ios-13-cp-enroll-1711.png)|**[信頼する]** をタップして、お使いのデバイスで会社が企業の情報および設定の管理を行うことを許可します。|
|![[Profile finishing installing]\(プロファイルのインストールを終了しています\) 読み込み画面。](./media/ios-14-cp-enroll-1711.png)|読み込まれるのを待ちます。|
|![[Profile installed]\(プロファイルがインストールされました\) 画面。](./media/ios-15-cp-enroll-1711.png)|プロファイルがインストールされ、もうじきデバイスの企業の情報と設定が管理できるようになります。|
|![登録を行うため、Safari に切り替わります。](./media/ios-16-cp-enroll-1711.png)|お使いのデバイスの管理情報の取得を終了するため、Safari に再び切り替わります。 |
|![ポータル サイトを開くシステム プロンプト。](./media/ios-17-cp-enroll-1711.png)|**[開く]** をタップします。|
|![[Loading company resources]\(会社のリソースを読み込んでいます\) 画面。](./media/ios-18-cp-enroll-1711.png)|読み込まれるのを待ちます。|
|![ポータル サイト アプリでデバイス カテゴリを選択します。](./media/ios-19-cp-enroll-1711.png)|お使いのデバイスに最も適したカテゴリを選択します。 これは、通常、デバイスの所有者や、普段使用する場所に関連します。|
|![カテゴリ選択。](./media/ios-20-cp-enroll-1711.png)||
|![デバイス管理が正常に行われました。設定を更新する必要があります。](./media/ios-21-cp-enroll-1711.png)|デバイスを管理する処理が正常に行われました。 パスワードの長さなど、会社が更新を必要とする追加の設定がある可能性があります。 **[デバイス設定の更新]** をタップして続行します。|
|![デバイス設定を確認しています。](./media/ios-22-cp-enroll-1711.png)|ポータル サイトは、更新を必要とする設定があるかどうか確認します。|
|![設定の確認が終了しましたが、OS バージョンが正しくありません](./media/ios-23-cp-enroll-1711.png)|ポータル サイトでは、設定に関する問題を解決する方法の指示が提供されます。 問題の修正が完了したら、**[Check Settings]\(設定の確認\)** をタップします。|
|![[Confirming device settings]\(デバイス設定を確認しています\) 読み込み画面。](./media/ios-24-cp-enroll-1711.png)|デバイスは、設定が会社のリソースにアクセスするのに十分安全であるかどうかを確認します。|
|![正常に登録され更新された設定](./media/ios-25-cp-enroll-1711.png)|これで終了です。 これでデバイスが Intune に登録されました。|

> [!Note]
> デバイスを完全に管理する前に、完了する必要のある手順がさらにいくつかある場合があります。 詳しくは、[通信費管理を使ったデバイスの登録](enroll-your-device-with-telecom-expense-management-ios.md)に関する記事をご覧ください。 組織が Apple の Device Enrollment Program を使っている場合は、[こちら](enroll-your-device-dep-ios.md)で詳細をご覧ください。

サポートが必要な場合は、 社内サポートに問い合わせてください。 連絡先情報については、[ポータル サイト Web サイト](https://portal.manage.microsoft.com)をご確認ください。
