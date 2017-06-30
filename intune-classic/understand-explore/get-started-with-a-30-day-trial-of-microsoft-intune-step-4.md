---
title: "ポリシーを作成してユーザーにアプリを発行する"
description: "Intune の 30 日間無料試用版にサインアップするときに、ポリシーを作成しアプリを発行する方法"
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 12/12/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c3a17884-442a-44f5-bc81-4589e823f65e
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: 335d91cd6583052bfcc72fc018b387eed8823b7e
ms.contentlocale: ja-jp
ms.lasthandoff: 06/08/2017


---


# <a name="create-policies-and-publish-an-app-to-evaluation-users"></a>ポリシーを作成してアプリを評価ユーザーに発行する

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

モバイル デバイスのセキュリティ設定を制御したり、コンピューターの Windows ファイアウォールや Endpoint Protection の設定を管理したり、アプリケーションを展開したりする作業は、Intune のポリシー設定を使用して効率的に行うことができます。 評価の後、本番用途で構成するデバイスに Intune を使用することを計画している場合、「[Microsoft Intune ポリシーを使用してデバイスの設定と機能を管理する](/intune-classic/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)」に書かれた手順に従うことが不可欠となります。

Intune で実行できるアプリのインストールには 2 種類あります。 1 つは**必須のインストール**です。この場合、アプリは管理対象デバイスに自動的に展開されます。 もう 1 つは "**利用可能なインストール**" です。この場合、Intune ポータル サイトにアプリ (またはアプリへのリンク) が展開され、コンピューターとモバイル デバイスのどちらにインストールするかをユーザーが選択できます。

Intune を使ってアプリをデプロイする前に、アプリの発行、配布、使用に必要なライセンスがあることを確認してください。 Microsoft ボリューム ライセンス契約で購入したアプリとソフトウェア、さらに、それ以外の方法で購入した Microsoft または Microsoft 以外のアプリとソフトウェアのライセンス契約情報は、**[ライセンス]** ワークスペースで追加、管理できます。 そのうえでライセンス レポートを作成すると、管理下にあるライセンス使用情報を社内に提示できるため、ライセンス使用アクティビティを常時公開することができます。

Skype は、以上の手順で、モバイル デバイスの構成ポリシーとコンピューターの Windows ファイアウォール ポリシーを設定し、登録済みのモバイル デバイスに対する "利用可能なインストール" として構成します。 新しいポリシーを追加して展開すると、その設定がベースライン ポリシーとして、ポリシーの展開先となるグループのすべてのユーザーまたはデバイスに継承されます。 これらのポリシーの細かな内容は、管理コンソールの **[ポリシー]** ワークスペースからいつでも確認し、編集することができます。

## <a name="create-and-deploy-a-mobile-device-configuration-policy"></a>モバイル デバイス構成ポリシーを作成して展開する

1.  [Intune 管理コンソール](https://manage.microsoft.com/)を開きます。

2.  左側のウィンドウで、**[ポリシー]** アイコンを選択します。

3.  **[ポリシーの概要]** ページで、**[タスク]** の一覧にある **[ポリシーの追加]** をクリックします。

4.  ポリシーの作成対象とするプラットフォームをポリシーの一覧で展開し、**[全般構成]**、**[カスタム ポリシーの作成と展開]**、**[ポリシーを作成する]** の順に選択します。

5.  **ポリシーの展開先となるグループを選択**するように求められたら、ボックスの一覧から **[My Trial Users]** を選択し、**[追加]** &gt; **[OK]** を選択します。

ポリシーが構成ポリシーの一覧に表示され、 **[My Trial Users]** グループにデプロイされます。 ポリシーをダブルクリックしてその設定を表示します。

## <a name="publish-the-skype-app-for-mobile-devices"></a>モバイル デバイスの Skype アプリを発行する

1.  [Intune 管理コンソール](https://manage.microsoft.com/)で、**[アプリ]** アイコンをクリックしてから、**[アプリ]** &gt; **[アプリの追加]** の順にクリックします。 メッセージが表示されたら、Intune の資格情報を入力します。

    > [!NOTE]
    > **Intune ソフトウェア パブリッシャー** を初めて起動するときは、アプリケーションがインストールされるため、しばらく時間がかかることがあります。

2.  セキュリティの警告を確認し、**[実行]** を選択します。

3.  **[開始する前に]** ページで、**[次へ]** を選択します。

4.  **[ソフトウェア セットアップ]** ページの **[このソフトウェアをデバイスに配布する方法]**で、 **[外部リンク]**を選択します。

5.  **[URL の指定]** にソフトウェアの外部リンクを入力し、**[次へ]** を選択します。 URL の先頭に **https://** が付いていることを確認してください。 Skype アプリには、ご利用のモバイル デバイス プラットフォームに該当するリンクを以下から選んで使用してください。

    -   **iOS:** [https://itunes.apple.com/us/app/skype-for-iphone/id304878510?mt%3D8](https://itunes.apple.com/us/app/skype-for-iphone/id304878510?mt%3D8)

    -   **Android:** [https://play.google.com/store/apps/details?id=com.skype.raider](https://play.google.com/store/apps/details?id=com.skype.raider)

    -   **Windows Phone 8.1:** [http://www.windowsphone.com/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51](http://www.windowsphone.com/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51)

6.  **[ソフトウェアの説明]** ページで、ポータル サイトでユーザーに対して表示するソフトウェアの情報を指定し、**[次へ]** をクリックします。 次の設定を使用できます (この例は Skype を対象としています)。

    -   **発行元:** 発行元の名前 (**Microsoft**) を入力します。

    -   **名前:** 「**Skype**」と入力します。

    -   **説明:** 「 **Skype 通信アプリ**

    -   **カテゴリ:** このソフトウェアに最適なカテゴリを選択します (例: **コラボレーション**)

    -   **このアプリをポータル サイトでおすすめアプリとして強調表示します:** モバイル デバイスのポータル サイトで、アプリを目立つように表示する場合、このオプションを選択します。

    -   **アイコン:**  (オプション) アイコンをソフトウェアに関連付けるかどうかを選択します。 最大アイコン サイズは 250 x 250 ピクセルですが、推奨されるアイコン サイズは 32 x 32 ピクセルです。

7.  **[概要ページ]** で、ソフトウェア情報を確認し、**[アップロード]** を選択します。 **[閉じる]** を選択してウィザードを終了します。

8.  [Intune 管理コンソール](https://manage.microsoft.com/)で、**[アプリ]** &gt; **[アプリ]** &gt; **[Skype]** &gt; **[展開の管理]** の順にクリックします。

9. **[グループの選択]** ページで、**[My Trial Users]** を選択して、そのユーザー グループにソフトウェアを展開し、**[追加]** &gt; **[次へ]** を選択します。

10. **[展開アクション]** ページで、各グループの **[承認]** 列から **[利用可能なインストール]** を選択します。

11. **[完了]** をクリックします。

## <a name="install-the-skype-app"></a>Skype アプリをインストールする
モバイル デバイスで会社のポータルを開き、**[アプリ]** を選択して、Microsoft Skype をインストールします。

以上で Intune モバイル デバイス管理ガイドは終わりですが、「次のステップ」セクションのリンクから Intune についてさらに学習できます。
## <a name="next-steps"></a>次のステップ
他の [Intune の機能](get-started-with-a-30-day-trial-of-microsoft-intune-step-6.md)についてさらに学習する

[Intune の一般的な使用方法](/intune/common-scenarios)を読む

[有料サブスクリプション](get-started-with-a-30-day-trial-of-microsoft-intune-step-7.md)に切り替える

