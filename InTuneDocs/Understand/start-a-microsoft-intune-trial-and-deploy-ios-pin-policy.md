---
title: "Microsoft Intune の試用を開始し、iOS PIN ポリシーを展開する | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 06cb9a73-0f17-44b3-b334-86c98020316e
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7f3985b10ac9612c8c1efc4756eb25cdcf29b023
ms.openlocfilehash: 6787d0c35621b2bc94bfe376dfd1669e9dfe46db


---

# Microsoft Intune の試用を開始し、iOS PIN ポリシーを展開する
ここでは、Intune 試用版のセットアップと、iOS デバイスの PIN ポリシーを構成する方法について、ステップ バイ ステップで説明します。 試用できるその他の一般的な Intune 評価タスクの一覧は、「[Microsoft Intune の一般的な評価タスク](common-microsoft-intune-evaluation-tasks.md)」をご覧ください。



## このタスクの前提条件を確認する

-   Internet Explorer を搭載した Windows PC (管理作業を実行する)

-   iOS 7.1 以降のデバイス (ユーザー ポリシーの検証をテストする)

-   携帯電話 (試用のサインアップ中に自分自身を認証する)

## Intune の無料の試用アカウントを作成する
> [!NOTE]
> 既に Intune サブスクリプションがある場合は、このセクションをスキップして次のセクションに進んでください。

1.  Windows PC を使用して、**Internet Explorer** (IE) を右クリックし、**[InPrivate ブラウズ]** を選びます。

    ![InPrivate ブラウズの開始](../media/30-day-trial-walkthrus/30day-start-trial-1-InPrivate.png)

2.  [Intune のサインアップ ポータル](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1)にアクセスし、必要な情報を入力して、**[次へ]** をクリックします。

    ![アカウントの登録](../media/30-day-trial-walkthrus/30day-start-trial-2-abt-you.png)

3.  管理者アカウントのユーザー ID とパスワードを入力し、**[次へ]** をクリックします。 今後は、この ID を使用して Intune ポータルにログインし、管理タスクを実行します。

    ![ID の作成](../media/30-day-trial-walkthrus/30day-start-trial-3-createID.png)

4.  携帯電話番号を入力し、**[テキスト メッセージを送信する]** をクリックして、携帯電話番号を検証します。

    ![詳細の検証](../media/30-day-trial-walkthrus/30day-start-trial-4-textme.png)

5.  画面に表示されている情報を保存し、**[準備ができました]** をクリックします。

    ![準備完了](../media/30-day-trial-walkthrus/30day-start-trial-5-ReadyToGo.png)

## テスト ユーザーを作成する

1.  Windows PC を使用し、**[開始]** をクリックしてユーザーの管理ページに移動します。

    ![ユーザーの管理ページに移動](../media/30-day-trial-walkthrus/30day-crt-user-6-click-start.png)

2.  **[+]** ボタンをクリックして、ユーザーを追加します。

    ![ユーザーの追加](../media/30-day-trial-walkthrus/30day-crt-user-7-click-plus.png)

3.  **[新しいユーザー アカウントの作成]** ページで、次の手順を実行します。

    1.  テスト ユーザーの情報を指定します。

    2.  **[パスワードの入力]** オプションを選びます。

    3.  **[このユーザーが次にサインインした時にパスワードを変更する]** チェック ボックスをオフにします。

    4.  **[作成]** をクリックします。

    ![新しいユーザー アカウントを作成する](../media/30-day-trial-walkthrus/30day-crt-user-8-add-user-info.png)

4.  ユーザー作成の確認ページで、**[閉じる]** をクリックします。

    ![ユーザー作成の確認ページ](../media/30-day-trial-walkthrus/30day-crt-user-9-close-confirm.png)

5.  **[最新の情報に更新]** ボタンをクリックして、作成したテスト ユーザーを表示します。

    ![アカウントの確認](../media/30-day-trial-walkthrus/30day-crt-user-10-refresh-user.png)

## テスト ユーザーの iOS PIN ポリシーを構成する

1.  Windows PC を使用して、Intune にする MDM 機関を設定します。

    1.  [Intune 管理コンソール](http://manage.microsoft.com/)に移動し、管理者アカウントでログインし、**[モバイル デバイスの管理を開始する]** をクリックします。 [モバイル デバイス管理機関] ページが開きます。

        ![Intune コンソールの開始](../media/30-day-trial-walkthrus/30day-cfg-pol-11-start-mg-mobl-dev.png)

    2.  **[モバイル デバイス管理機関の設定]** リンクをクリックします。

        ![モバイル デバイス管理機関の設定](../media/30-day-trial-walkthrus/30day-cfg-pol-12-link-set-mdm.png)

2.  iOS デバイスの登録を有効化します。 このプロセスは、Apple Push Notification サービス (APNs) と Intune サブスクリプションの間の信頼された証明書をセットアップします。

    1.  **[iOS および Mac OS X プラットフォームを有効にする]** をクリックします。

        ![iOS および Mac OS X プラットフォームを有効にする](../media/30-day-trial-walkthrus/30day-cfg-pol-13-enbl-ios-plat.png)

    2.  **[APNs 証明書要求のダウンロード]** をクリックします。

        ![APNs 証明書のダウンロード](../media/30-day-trial-walkthrus/30day-cfg-pol-14-dwnld-cert-reqst.png)

    3.  証明書署名要求 (CSR) のファイル名と場所を指定し、**[保存]** をクリックします。 このファイルは、Intune のサブスクリプションによって保持されている秘密キーに対応する公開キーを保持します。

        ![証明書署名要求の指定](../media/30-day-trial-walkthrus/30day-cfg-pol-15-cert-name-loc.png)

    4.  **[Apple Push Certificates Portal]** をクリックして、新しいタブを開きます。

        ![APNs 証明書ページの表示](../media/30-day-trial-walkthrus/30day-cfg-pol-16-cert-portl-link.png)

    5.  Apple ID とパスワードを入力し、**[サインイン]** をクリックします。 この ID には、iOS App Store からアプリを取得するために iOS デバイスで使用した ID を使うことができます。

        ![Apple Push Certificates Portal へのサインイン](../media/30-day-trial-walkthrus/30day-cfg-pol-17-id-passw-signin.png)

    6.  **[証明書の作成]** をクリックします。

        ![APNs 証明書の作成](../media/30-day-trial-walkthrus/30day-cfg-pol-18-create-cert.png)

    7.  Apple の使用条件を読み、チェック ボックスを選び、**[同意する]** をクリックします。

        ![使用条件への同意](../media/30-day-trial-walkthrus/30day-cfg-pol-19-TOU.png)

    8.  **[参照]** をクリックします。

        ![証明書を保存した場所の参照](../media/30-day-trial-walkthrus/30day-cfg-pol-20-browse.png)

    9. 前に保存した CSR ファイルを選び、**[開く]** をクリックします。

        ![証明書を開く](../media/30-day-trial-walkthrus/30day-cfg-pol-21-CSRfile-open.png)

    10. **[アップロード]** ボタンをクリックします。

        ![証明書のアップロード](../media/30-day-trial-walkthrus/30day-cfg-pol-22-upld-reqst.png)

    11. JSON ファイルをダウンロードするメッセージが表示されたら、**[名前を付けて保存]** をクリックします。

        ![JSON ファイルの保存](../media/30-day-trial-walkthrus/30day-cfg-pol-23-json-saveas.png)

    12. JSON ファイルの場所を指定し、**[保存]** をクリックします。

        ![JSON ファイルの保存場所の指定](../media/30-day-trial-walkthrus/30day-cfg-pol-24-json-save-loc.png)

        数秒後にページが自動的にリダイレクトしない場合は、**[キャンセル]** をクリックします。

        ![ページがリダイレクトしない場合はキャンセル](../media/30-day-trial-walkthrus/30day-cfg-pol-25-json-pg-cancel.png)

    13. 新しく作成された証明書ファイルを取得するには、**[ダウンロード]** をクリックします。

        ![証明書のダウンロード](../media/30-day-trial-walkthrus/30day-cfg-pol-26-dwnld-retrv-cert.png)

    14. PEM ファイルをダウンロードするメッセージが表示されたら、**[名前を付けて保存]** をクリックします。

        ![PEM ファイルのダウンロード](../media/30-day-trial-walkthrus/30day-cfg-pol-27-pem-saveas.png)

    15. PEM ファイルの場所を指定し、**[保存]** をクリックします。

        ![PEM ファイルの保存](../media/30-day-trial-walkthrus/30day-cfg-pol-28-pem-save-loc.png)

    16. Intune 管理コンソール タブに戻り、**[APNs 証明書のアップロード]** をクリックします。

        ![APNs 証明書のアップロード](../media/30-day-trial-walkthrus/30day-cfg-pol-29-upld-cert.png)

    17. Apple ID を入力し、**[参照]** をクリックします。

        ![Apple ID の入力](../media/30-day-trial-walkthrus/30day-cfg-pol-30-app-id-browse.png)

    18. いま保存した PEM ファイルを選び、**[開く]** をクリックします。

        ![PEM ファイルを開く](../media/30-day-trial-walkthrus/30day-cfg-pol-31-sel-pem-open.png)

    19. **[アップロード]** をクリックします。

        ![PEM ファイルのアップロード](../media/30-day-trial-walkthrus/30day-cfg-pol-32-pem-upload.png)

        これで、APNs 証明書が構成されました。

        ![APNs 証明書の構成の完了](../media/30-day-trial-walkthrus/30day-cfg-pol-33-apns-confgd.png)

3.  ポリシーの対象とするテスト ユーザー グループを作成します。

    1.  左側のウィンドウで、**[グループ]** をクリックします。

        ![グループを開く](../media/30-day-trial-walkthrus/30day-cfg-pol-34-clk-groups.png)

    2.  右端にある **[グループの作成]** をクリックします。

        ![グループの作成](../media/30-day-trial-walkthrus/30day-cfg-pol-35-crt-group.png)

    3.  グループ名を指定し、親グループとして **[すべてのユーザー]** を選び、**[次へ]** をクリックします。

        ![親グループとしてすべてのユーザーを選択](../media/30-day-trial-walkthrus/30day-cfg-pol-36-name-group.png)

    4.  **[グループのメンバーシップ]** フィールドで **[親グループのすべてのユーザー]** を選び、**[完了]** をクリックします。

        ![親グループのメンバーシップの開始](../media/30-day-trial-walkthrus/30day-cfg-pol-37-all-users-group.png)

4.  iOS PIN ポリシーを作成し、テスト ユーザー グループを対象にします。

    1.  左側のウィンドウで **[ポリシー]** をクリックします。

        ![ポリシー ワークスペースを開く](../media/30-day-trial-walkthrus/30day-cfg-pol-38-clk-policy.png)

    2.  右端にある **[ポリシーの追加]** をクリックします。

        ![ポリシーの追加](../media/30-day-trial-walkthrus/30day-cfg-pol-39-add-policy.png)

    3.  iOS のノードを展開し、**[全般構成]** の行を選び、**[ポリシーを作成する]** をクリックします。

        ![iOS 全般構成ポリシーの作成](../media/30-day-trial-walkthrus/30day-cfg-pol-40-gen_cfg_pol.png)

    4.  ポリシーの名前を入力し、**[モバイル デバイスのロック解除にパスワードを必要とする]** オプションをオンにし、**[パスワードの最小文字数]** を **4** に設定します。

        ![パスワード設定の構成](../media/30-day-trial-walkthrus/30day-cfg-pol-41-name-policy.png)

    5.  ポリシーを展開するには、**[はい]** をクリックします。

        ![ポリシーの展開](../media/30-day-trial-walkthrus/30day-cfg-pol-42-yes-deploy-pol.png)

    6.  以前に作成したユーザー グループをクリックし、**[追加]** をクリックし、**[OK]** をクリックします。

        ![ポリシーのグループの選択](../media/30-day-trial-walkthrus/30day-cfg-pol-43-add-pol-to-grp.png)

        これで、テスト ユーザー グループを対象とする iOS PIN ポリシーが完成しました。

        ![ポリシーのセットアップの完了](../media/30-day-trial-walkthrus/30day-cfg-pol-44-policy-applied.png)

## iOS デバイスにポリシーが適用されていることを検証する

1.  iPad で、iOS App Store を起動し、無料の **Microsoft Intune ポータル サイト** アプリをインストールして、そのアプリを開きます。

    ![ポータル サイトのインストール](../media/30-day-trial-walkthrus/30day-cfg-pol-45-cportal-installed.png)

2.  テスト ユーザー アカウント名とパスワードを入力し、**[サインイン]** をタップします。

    ![資格情報の入力](../media/30-day-trial-walkthrus/30day-cfg-pol-46-cportal-signin.png)

3.  **[登録]** をタップして、Intune でデバイスの登録を開始します。

    ![登録の開始](../media/30-day-trial-walkthrus/30day-cfg-pol-47-tap-enroll.jpg)

4.  **[プロファイルのインストール]** 画面で、**[インストール]** をタップします。

    ![プロファイルのインストール](../media/30-day-trial-walkthrus/30day-cfg-pol-48-profile-install-1.jpg)

5.  **[プロファイルのインストール]** ダイアログで、**[インストール]** をタップします。

    ![プロファイルのインストールの続行](../media/30-day-trial-walkthrus/30day-cfg-pol-49-profile-install-2.jpg)

6.  **[警告]** 画面で、**[インストール]** をタップします。

    ![警告メッセージの確認](../media/30-day-trial-walkthrus/30day-cfg-pol-50-warning-install-3.png)

7.  **[リモート管理]** ダイアログで、**[信頼する]** をタップします。

    ![リモート管理の信頼](../media/30-day-trial-walkthrus/30day-cfg-pol-51-remt-mgmt-trust.jpg)

8.  管理プロファイルのインストールが完了したら、**[完了]** をタップします。 これで、登録が完了しました。

    ![登録の完了](../media/30-day-trial-walkthrus/30day-cfg-pol-52-profile-done.jpg)

9. 登録が完了したら、**[OK]** をタップし、ポータル サイト アプリを閉じます。

    ![[OK] をタップしてポータル サイト アプリを閉じる](../media/30-day-trial-walkthrus/30day-cfg-pol-53-devc-enrolled-ok.png)

10. パスコードを構成するようにとのメッセージが表示されたら、**[続行]** をタップします。

    ![パスコードの構成を求めるメッセージの確認](../media/30-day-trial-walkthrus/30day-cfg-pol-54-passcode-req-cont.png)

11. パスコードを入力し、**[続行]** をタップします。もう一度パスコードを入力し、**[保存]** をタップします。

    ![パスコードの入力](../media/30-day-trial-walkthrus/30day-cfg-pol-55-passcode-enter.jpg)

12. 電源ボタンを押して iPad をロックし、スライドしてロックを解除します。このとき、デバイスのロックを解除するためにパスコードを入力する必要があることを確認してください。

### 関連項目
[Intune の評価ガイド](get-started-with-a-30-day-trial-of-microsoft-intune.md)



<!--HONumber=Jun16_HO4-->


