---
# required metadata

title: ポリシーを作成してアプリを発行する | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: e0d8e98f-7dd8-4cbf-887c-a9af63ffe970

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# ポリシーを作成してアプリを発行する
モバイル デバイスのセキュリティ設定を制御したり、コンピューターの Windows ファイアウォールや Endpoint Protection の設定を管理したり、アプリケーションを展開したりする作業は、Intune のポリシー設定を使用して効率的に行うことができます。 詳細については、「[Microsoft Intune ポリシーを使用してデバイスの設定と機能を管理する](/Intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies)」および「[Microsoft Intune の Endpoint Protection を使用して Windows PC を保護する](/Intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)」を参照してください。

Intune で実行できるアプリのインストールには 2 種類あります。 1 つは " **必須のインストール**" です。この場合アプリは、管理対象コンピューターに自動的に展開されます。 もう 1 つは "**利用可能なインストール**" です。この場合、Intune ポータル サイトにアプリ (またはアプリへのリンク) が展開され、コンピューターとモバイル デバイスのどちらにインストールするかをユーザーが選択できます。

<!-- this section really isn't necessary and confuses a lot of people because most mobile device apps aren't licensed this way (and our licensing/reporting features aren't super helpful). I think it's best to avoid this during a quick start guide.

Before using Intune to deploy apps, make sure that you have the appropriate licenses to publish, distribute, and use the app. The Licenses workspace lets you add and manage license agreement information for apps or software purchased through Microsoft Volume Licensing agreements, and for Microsoft or non-Microsoft software that was purchased by other means. You can then create license reports that display managed license usage information throughout your company to stay informed of license usage activity.
-->

次の手順では、モバイル デバイスの構成ポリシーと PC の Windows ファイアウォール ポリシーを設定し、登録済みのモバイル デバイスに対する "利用可能なインストール" として Skype を構成できます。

> [!TIP]
> 新しいポリシーを追加して展開すると、その設定がベースライン ポリシーとして、ポリシーの展開先となるグループのすべてのユーザーまたはデバイスに継承されます。 これらのポリシーの細かな内容は、[ポリシー] ワークスペースからいつでも確認し、編集することができます。


## モバイル デバイス構成ポリシーを作成して展開する

1.  [Intune 管理コンソール](https://manage.microsoft.com/)を開きます。

2.  左側のウィンドウで、**[ポリシー]** アイコンを選択します。

    ![admin-console-policy-workspace](./media/policy.png)

3.  **[ポリシーの概要]** ページで、**[タスク]** の一覧にある **[ポリシーの追加]** をクリックします。

4.  ポリシーの作成対象とするプラットフォームをポリシーの一覧で展開し、**[全般構成]** > **[推奨設定を使用してポリシーを作成および展開する]** > **[ポリシーを作成する]** の順に選択します。

5.  **このポリシーを展開するグループを選択する**よう求められたら、利用可能なグループの一覧から **[Intune Users]** (前の手順で作成したグループ) を選択し、**[追加]** > **[OK]** の順に選択します。

ポリシーが構成ポリシーの一覧に表示され、**Intune Users** グループに展開されます。 ポリシーをダブルクリックしてその設定を表示します。

## モバイル デバイスの Skype アプリを発行する

1.  [Intune 管理コンソール](https://manage.microsoft.com/)で、**[アプリ]** アイコンをクリックしてから、**[アプリ]** > **[アプリの追加]** の順にクリックします。 メッセージが表示されたら、[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] の資格情報を入力します。

    ![admin-console-apps-workspace](./media/apps.png)

    > [!NOTE] **Intune ソフトウェア パブリッシャー**を初めて起動するときは、アプリケーションがインストールされるため、しばらく時間がかかることがあります。

2.  セキュリティの警告を確認し、**[実行]** を選択します。

3.  **[開始する前に]** ページで、**[次へ]** を選択します。

4.  **[ソフトウェア セットアップ]** ページの **[このソフトウェアをデバイスに配布する方法]** で、**[外部リンク]** を選択します。

5.  **[URL の指定]** にソフトウェアの外部リンクを入力し、**[次へ]** を選択します。 URL の先頭に **http://** が付いていることを確認してください。 Skype アプリには、ご利用のモバイル デバイス プラットフォームに該当するリンクを以下から選んで使用してください。

    -   **iOS:**   [https://itunes.apple.com/us/app/skype-for-iphone/id304878510?mt%3D8](https://itunes.apple.com/us/app/skype-for-iphone/id304878510?mt%3D8)

    -   **Android:**  [https://play.google.com/store/apps/details?id=com.skype.raider](https://play.google.com/store/apps/details?id=com.skype.raider)

    -   **Windows Phone 8 または Windows Phone 8.1:**  [http://www.windowsphone.com/en-us/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51](http://www.windowsphone.com/en-us/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51)

6.  **[ソフトウェアの説明]** ページで、ポータル サイトでユーザーに対して表示するソフトウェアの情報を指定し、**[次へ]** をクリックします。 次の設定を使用できます (この例は Skype を対象としています)。

    -   **発行元:** 発行元の名前 ("Microsoft") を入力します。

    -   **名前:** 「 **Skype**

    -   **説明:** 「 **Skype 通信アプリ**

    -   **カテゴリ:** このソフトウェアに最適なカテゴリを選択します (例: **コラボレーション**)

    -   **このアプリをポータル サイトでおすすめアプリとして強調表示します:** モバイル デバイスのポータル サイトで、アプリを目立つように表示する場合、このオプションを選択します。

    -   **アイコン:** アイコンをソフトウェアに関連付けるかどうかを選択します。 オプションのアイコンの最大サイズは 250 x 250 ピクセルで、推奨されるサイズは 32 x 32 ピクセルです。

7.  **[概要ページ]** で、ソフトウェア情報を確認し、**[アップロード]** をクリックします。 **[閉じる]** を選択してウィザードを終了します。

8.  [Intune 管理コンソール](https://manage.microsoft.com/)で、**[アプリ]** > **[アプリ]** > **[Skype]** > **[展開の管理]** を選択します。

9. **[グループの選択]** ページで、**[Intune Users]** を選択して、そのユーザー グループにソフトウェアを展開し、**[追加]** > **[次へ]** の順に選択します。

10. **[展開アクション]** ページで、各グループの **[承認]** 列から **[利用可能なインストール]** を選択します。

11. **[完了]** をクリックします。

これでポータル サイトからモバイル デバイスに Skype アプリをインストールできる状態となりましたが、最初に自分が [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] ソフトウェアをコンピューターとモバイル デバイスにインストールする必要があります。


### 次のステップ
これで終了です。 *Intune のクイック スタート ガイド*の手順 6. が完了しました。

>[!div class="step-by-step"]

>[&larr;**ユーザーとデバイスを整理する**](.\start-with-a-paid-subscription-to-microsoft-intune-step-5.md)       [**ポータル サイトをカスタマイズする** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-7.md)  


<!--HONumber=May16_HO3-->


