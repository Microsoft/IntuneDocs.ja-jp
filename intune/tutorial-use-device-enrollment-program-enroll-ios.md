---
title: チュートリアル - Device Enrollment Program を使用して、iOS デバイスを Intune に登録する
titleSuffix: Microsoft Intune
description: このチュートリアルでは、Intune に iOS デバイスを登録するように Apple の DEP を設定します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 1/30/2019
ms.topic: tutorial
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
Customer intent: As an Intune admin, I want to set up the Device Enrollment Program so that users can automatically enroll in Intune.
ms.openlocfilehash: d3fd7d860661f7b97e1191b1977b7f75ca02730f
ms.sourcegitcommit: bd5d0bde931cbd3a31ddaeb91a934068cb8a5da8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2019
ms.locfileid: "55482561"
---
# <a name="tutorial-use-the-device-enrollment-program-to-enroll-ios-devices-in-intune"></a>チュートリアル: Device Enrollment Program を使用して Intune に iOS デバイスを登録する
Apple の Device Enrollment Program (DEP) によって、デバイスの登録が簡略化されます。 Microsoft Intune と DEP では、最初にユーザーがデバイスをオンにしたときに、デバイスが自動的に登録されます。 そのため、各デバイスを個別に設定することなく、デバイスを多くのユーザーに配送できます。 

このチュートリアルでは、次の方法について説明します。
> [!div class="checklist"]
> * Apple DEP トークンを取得する
> * Autopilot デバイス グループを作成する
> * Autopilot Deployment プロファイルを作成する
> * Autopilot Deployment プロファイルをデバイス グループに割り当てる
> * Windows デバイスをユーザーに配布する

Intune サブスクリプションがない場合は、[無料試用版アカウントにサインアップ](free-trial-sign-up.md)します。

## <a name="prerequisites"></a>必要条件
- [Apple の Device Enrollment Program](http://deploy.apple.com) で購入したデバイス
- [[モバイル デバイス管理機関]](mdm-authority-set.md) を設定する
- [[Apple MDM プッシュ通知証明書]](apple-mdm-push-certificate-get.md) を取得する

## <a name="get-an-apple-dep-token"></a>Apple DEP トークンを取得する
DEP で iOS デバイスを登録する前に、Apple DEP トークン (.pem) ファイルが必要です。 このトークンにより、Intune は企業所有の DEP デバイスに関する情報を同期できるようになります。 また、Intune は Apple に登録プロファイルをアップロードして、デバイスをそれらのプロファイルに割り当てられるようになります。

DEP トークンを作成する場合は、Apple DEP ポータルを使用します。 また、管理のためにデバイスを Intune に割り当てる場合にも DEP ポータルを使用します。

1. [Azure portal の Intune](https://aka.ms/intuneportal) で、**[デバイスの登録]** > **[Apple の登録]** > **[Enrollment Program トークン]** > **[追加]** の順に選択します。

2. **[同意する]** を選択して、Microsoft がユーザーとデバイスの情報を Apple に送信できるようにします。

   ![公開キーをダウンロードするための [Apple 証明書] ワークスペースの [Enrollment Program トークン] のスクリーンショット。](./media/device-enrollment-program-enroll-ios-newui/add-enrollment-program-token-pane.png)

3. **[公開キーをダウンロードします]** を選択し、暗号化キー (.pem) ファイルをダウンロードしてローカルに保存します。 .pem ファイルは、Apple Device Enrollment Program ポータルから信頼関係証明書を要求するために使用します。

4. **[Create a token for Apple's Device Enrollment Program]\(Apple Device Enrollment Program 用のトークンを作成します\)** を選択して Apple の Deployment Program ポータルを開き、会社の Apple ID でサインインします。 この Apple ID を使って、DEP トークンを更新できます。

5.  Apple の [Deployment Programs ポータル](https://deploy.apple.com) で、**[Device Enrollment Program]** の **[開始]** を選択します。

4. **[Manage Servers\(サーバーの管理\)]** ページで、**[Add MDM Server\(MDM サーバーの追加\)]** を選びます。

5. **[MDM Server Name]\(MDM サーバー名\)** に、「*TestMDMServer*」と入力して **[次へ]** を選びます。 サーバー名は、自分がモバイル デバイス管理 (MDM) サーバーを識別できるようにするための名前です。 Microsoft Intune サーバーの名前または URL ではありません。

6. **[Add &lt;ServerName&gt;\(<サーバー名> の追加\)]** ダイアログ ボックスが開き、**[Upload Your Public Key\(公開キーをアップロードする\)]** と表示されます。 **[Choose File]** (ファイルを選択) をクリックして .pem ファイルをアップロードし、**[Next]** (次へ) を選択します。

6. **[Deployment Programs]** > **[Device Enrollment Program]** > **[デバイスの管理]** に移動します。
7. **[Choose Devices By]\(デバイスの選択基準\)** で、**[シリアル番号]** を選びます。 <!--ask Tiffany about this-->

8. **[アクションの選択]** で **[Assign to Server]\(サーバーに割り当てる\)** を選択し、Microsoft Intune に指定した **ServerName** を選択して、&lt;[OK]&gt; を選択します。 指定したデバイスが管理用に Intune サーバーに割り当てられて、**[Assignment Complete\(割り当て完了\)]** と表示されます。

   Apple ポータルで、**[Deployment Programs\(配備プログラム\)]** &gt; **[Device Enrollment Program\(Device Enrollment Program\)]** &gt; **[View Assignment History\(割り当て履歴の表示\)]** の順に移動して、デバイスとその MDM サーバーの割り当てのリストを表示します。

9. 後で参照するために、Azure portal の Intune で、このトークンを作成するために使用した Apple ID を指定します。

    ![Enrollment Program トークンの作成に使った Apple ID の指定と、Enrollment Program トークンの参照のスクリーンショット。](./media/device-enrollment-program-enroll-ios/image03.png)

10. **[Apple トークン]** ボックスで、証明書 (.pem) ファイルを参照し、**[開く]** を選択して、**[作成]** を選択します。 

## <a name="create-an-apple-enrollment-profile"></a>Apple 登録プロファイルの作成
これでトークンがインストールされました。DEP デバイスの登録プロファイルを作成することができます。 デバイス登録プロファイルで、デバイス グループに対して登録時に適用する設定を定義します。

1. Azure Portal の Intune で、**[デバイスの登録]** > **[Apple の登録]** > **[Enrollment Program トークン]** の順に選択します。

2. インストールしたトークンを選択し、**[プロファイル]** > **[プロファイルの作成]** を選びます。

3. **[プロファイルの作成]** で、**[名前]** に「*TestDEPProfile*」、**[説明]** に「*iOS デバイス用の DEP のテスト*」と入力します。 ユーザーにはこれらの詳細は表示されません。

4. **[ユーザー アフィニティ]** で **[ユーザー アフィニティとともに登録する]** を選びます。 このオプションは、アプリのインストールなどのサービスにポータル サイトを使用する必要がある、ユーザーに属しているデバイス用のものです。

5. **[Apple セットアップ アシスタントの代わりにポータル サイトで認証します]** で **[いいえ]** を選びます。

6. **[デバイス管理の設定]** を選んで、**[監視下]** で **[いいえ]** を選びます。 監視されたデバイスでは、さらに管理オプションが提供されますが、このチュートリアルで使用することはありません。

7. **[OK]** を選びます。

8. **[セットアップ アシスタントのカスタマイズ]** を選んで、**[部署名]** に「*チュートリアル部門*」と入力します。 この文字列は、デバイスのアクティブ化中にユーザーが **[About configuration]\(構成について\)** をタップすると表示される内容です。

9. **[部署の電話番号]** に電話番号を入力します。 この番号は、アクティブ化中にユーザーが **[ヘルプが必要ですか]** ボタンをタップすると表示されます。

10. デバイスのアクティブ化中にさまざまな画面を**表示**したり、**非表示**にしたりすることができます。 このチュートリアルの目的で、**[パスコード]** を **[表示]** に設定して、その他すべてを **[非表示]** に設定します。

11. **[OK]** > **[作成]** の順に選択します。

## <a name="sync-managed-devices"></a>マネージド デバイスを同期する

このトークンに割り当てられたデバイスを表示できるようになりました。

1. Azure portal の Intune で、**[デバイスの登録]** > **[Apple の登録]** > **[Enrollment Program トークン]** の順に選択し、リスト内でトークン、**[デバイス]** > **[同期]** の順に選択します。

## <a name="assign-an-enrollment-profile-to-ios-devices"></a>登録プロファイルを iOS デバイスに割り当てる

登録する前に、Enrollment Program プロファイルをデバイスに割り当てる必要があります。

1. Azure portal の Intune で、**[デバイスの登録]** > **[Apple の登録]** > **[Enrollment Program トークン]** の順に選択し、リスト内で自分のトークンを選択します。
2. **[デバイス]** を選択し、リスト内でデバイスを選択し、**[プロファイルの割り当て]** を選択します。
3. **[プロファイルの割り当て]** の下でデバイス用のプロファイルを選択し、**[割り当て]** を選択します。

## <a name="distribute-devices-to-users"></a>デバイスをユーザーに配布する

Apple と Intune の間の同期と管理を設定し、DEP デバイスを登録できるようにプロファイルを割り当てました。 ユーザーにデバイスを配布できるようになりました。 ユーザー アフィニティがあるデバイスでは、各ユーザーに Intune ライセンスを割り当てる必要があります。

## <a name="clean-up-resources"></a>リソースをクリーンアップする

Autopilot デバイスを使用しなくなった場合は、それらを削除できます。

- デバイスが Intune に登録されている場合、最初に [Azure Active Directory ポータルから削除する](devices-wipe.md#delete-devices-from-the-azure-active-directory-portal)必要があります。

<!--ask tiffany how to do this-->

## <a name="next-steps"></a>次の手順

iOS デバイスの登録に使用できる他のオプションについての詳細を確認できます。

> [!div class="nextstepaction"]
> [iOS DEP の登録に関する詳細な記事](device-enrollment-program-enroll-ios.md)