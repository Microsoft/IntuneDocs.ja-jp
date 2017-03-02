---
title: "iOS デバイスを登録する - Apple Configurator セットアップ アシスタント | Intune Azure プレビュー | Microsoft Docs"
description: "Intune Azure プレビュー: Apple Configurator でセットアップ アシスタントを使用して会社が所有している iOS デバイスを登録する方法について説明します。"
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6d384cd0-b662-41e7-94f5-0c96790ab20a
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 08dad848a48adad7d9c6f0b5b3286f6550a266bd
ms.openlocfilehash: 888e7b7af7dcca4154f67a1de781eb7908d9a187
ms.lasthandoff: 02/15/2017


---

# <a name="enroll-ios-devices-with-apple-configurator-and-setup-assistant"></a>Apple Configurator とセットアップ アシスタントを使用して iOS デバイスを登録する 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Intune は、Mac コンピューターで実行される [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) を使用した、企業所有の iOS デバイスの登録をサポートします。 このプロセスでは、デバイスを工場出荷時の設定にリセットし、セットアップ アシスタントを実行するための準備を行い、デバイスの新しいユーザー用に会社のポリシーをインストールします。

>[!NOTE]
>この登録方法は、[デバイス登録マネージャー](enroll-devices-using-device-enrollment-manager.md)の方法と同時に使用することはできません。

Apple Configurator を使用して、iOS デバイスを工場出荷時の設定にリセットし、デバイスの新しいユーザー用にセットアップするための準備を行うことができます。 この方法では、USB を使用して iOS デバイスを Mac コンピューターに接続し、会社の登録をセットアップする必要があります。この方法では、Apple Configurator 2.0 の使用を想定しています。 ほとんどのシナリオでは、Intune ポータル サイト アプリを有効にするため、iOS デバイスに適用されるポリシーにユーザー アフィニティが含まれている必要があります。

iOS デバイスの他の登録方法については、[Intune での iOS デバイスの登録方法の選択](choose-ios-enrollment-method.md)に関するページを参照してください。

## <a name="prerequisites"></a>必要条件

iOS デバイスの登録を設定する前に、以下の前提条件を満たしている必要があります。

- [ドメインを構成する](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-2)
- [MDM 機関を設定する](set-mdm-authority.md)
- [グループの作成](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-5)
- [ポータル サイト アプリを構成する](/intune-azure/manage-apps/company-portal-app.md)
- [Office 365 ポータル](http://go.microsoft.com/fwlink/p/?LinkId=698854)でユーザー ライセンスを割り当てる
- [Apple MDM プッシュ証明書を取得する](get-an-apple-mdm-push-certificate.md)
- iOS デバイスに物理的にアクセスできることを確認する
- デバイスのシリアル番号を確認する ([iOS のシリアル番号の確認方法](https://support.apple.com//HT204308)に関するページを参照してください)
- USB 接続ケーブルを手元に置いておく。
- Mac PC に [Apple Configurator 2.0](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) をインストールしておく
- [Apple Configurator のシリアル番号を追加する](add-apple-configurator-serial-numbers.md)


## <a name="create-an-apple-configurator-profile-for-devices"></a>デバイスの Apple Configurator プロファイルを作成する

デバイス登録プロファイルで、デバイスのグループに適用する設定を定義します。 以下の手順は、Apple Configurator を使用して登録される iOS デバイス用のデバイス登録プロファイルを作成する方法を示しています。

1. Azure Portal で、**[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。

2. [Intune] ブレードで **[デバイスの登録]** を選択し、**[Apple の登録]** を選択します。

3. **[Apple Configurator 登録設定の管理]** で **[AC プロファイル]** を選択します。

4. **[Apple Configurator の登録プロファイル]** ブレードで、**[作成]** を選択します。

5. **[登録プロファイルの作成]** ブレードで、プロファイルの名前と説明を入力します。

6. **[ユーザー アフィニティ]** で、このプロファイルに対応するデバイスをユーザー アフィニティと共に登録するかどうかを選択します。

   - **[ユーザー アフィニティとともに登録する]** - 初回セットアップ時にデバイスをユーザーに関連付ける必要があります。その後、デバイスは企業のデータや電子メールにアクセスすることが許可されます。 ユーザーに属していて、アプリのインストールなどのサービスにポータル サイトを使用する必要がある DEP 管理対象のデバイスの場合、ユーザー アフィニティを選択する必要があります。

   - **[ユーザー アフィニティなしで登録する]** - デバイスは、ユーザーと関連付けられません。 このデバイス関連付け情報を使用すると、ローカルのユーザー データにアクセスしなくてもタスクを実行できます。 ユーザー アフィリエーションが必要なアプリ (基幹業務アプリのインストールに使用されるポータル サイト アプリを含む) は機能しません。

7. **[作成]** を選択してプロファイルを保存します。

## <a name="assign-serial-numbers-to-an-apple-configurator-profile"></a>Apple Configurator プロファイルにシリアル番号を割り当てる

Apple Configurator プロファイルを作成した後、デバイスのシリアル番号をプロファイルに割り当てることができます。 シリアル番号を割り当てるには、最初に「[Apple Configurator のシリアル番号を追加する](add-apple-configurator-serial-numbers.md)」の手順に従って、Intune にシリアル番号を追加する必要があります。

### <a name="assign-serial-numbers-to-apple-configurator-profiles"></a>Apple Configurator プロファイルにシリアル番号を割り当てる

1. Azure Portal で、**[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。

2. **[Apple Configurator の登録プロファイル]** ブレードで、シリアル番号を割り当てるプロファイルを選択します。

3. プロファイルの名前が付いたブレードで、**[シリアル番号]** > **[割り当て]** の順に選択します。

4. プロファイルに割り当てるシリアル番号を選択し、**[割り当て]** を選択します。

## <a name="export-the-profile-to-ios-devices"></a>プロファイルを iOS デバイスにエクスポートする

プロファイルを作成してシリアル番号を割り当てたら、プロファイルを URL または以下で説明する形式のファイルとして Intune からエクスポートする必要があります。 その後、そのプロファイルを Mac 上の Apple Configurator プログラムに手動でインポートすると、Apple Configurator プログラムによってデバイスに展開されます。

### <a name="export-a-profile-using-setup-assistant-enrollment"></a>セットアップ アシスタントの登録を使用してプロファイルをエクスポートする

1. Azure Portal で、**[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。

2. **[Apple Configurator の登録プロファイル]** ブレードで、エクスポートするプロファイルを選択します。

3. プロファイルのブレードで、**[プロファイルのエクスポート]** を選択します。

4. iOS デバイスが接続されている [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) にプロファイル URL をコピーします。 Apple Configurator を使用してこれを後でアップロードして、iOS デバイスで使用する Intune プロファイルを定義します。

  Apple Configurator 2 をサポートするには、2.0 プロファイルの URL を編集する必要があります。 これを行うには、
    ```
    https://manage.microsoft.com/EnrollmentServer/Discovery.svc/iOS/ESProxy?id=
    ```
    上記のコードを以下のコードに置き換えます。

    ```
    https://appleconfigurator2.manage.microsoft.com/MDMServiceConfig?id=
    ```

   iOS デバイスで使用される Intune プロファイルを定義するには、以下の手順で Apple Configurator を使用して Apple DEP サービスにこのプロファイル URL をアップロードします。

5. Apple Configurator を使用して Apple DEP サービスにこのプロファイル URL をアップロードして、iOS デバイスで使用される Intune プロファイルを定義します。


    1.  Mac コンピューターで **Apple Configurator 2** を開きます。 メニュー バーで、**[Apple Configurator 2]** を選択し、**[基本設定]** を選択します。

         > [!WARNING]
         > デバイスは、登録プロセス中に、出荷時の構成にリセットされます。 ベスト プラクティスとして、デバイスをリセットし、オンにします。 デバイスを接続するときはデバイスの **[こんにちは]** 画面を表示する必要があります。

    2. **基本設定**ウィンドウで **[サーバー]** を選択し、プラス記号 (+) を選択して MDM サーバー ウィザードを起動します。 **[次へ]** を選択します。

    3. 「Microsoft Intune での iOS デバイスのセットアップ アシスタントを使用した登録」の手順 6 の MDM サーバーの**名前**と**登録 URL** を入力します。 登録 URL には、Intune からエクスポートされた登録プロファイル URL を入力します。 **[次へ]** を選択します。  

       "サーバー URL が検証されていない" ことを示す警告は、無視して構いません。 操作を続行するには、ウィザードが完了するまで **[次へ]** を選択します。

    4.  USB アダプターを使用して iOS モバイル デバイスを Mac コンピューターに接続します。

        > [!WARNING]
        > デバイスは、登録プロセス中に、出荷時の構成にリセットされます。 ベスト プラクティスとして、デバイスをリセットし、オンにします。 セットアップ アシスタントを開始するとデバイスに **[こんにちは]** 画面が表示されます。

    5.  **[準備]** を選択します。 **[iOS デバイスを準備]** ウィンドウで、**[手動]** を選択してから **[次へ]** を選択します。

    6. **[MDM サーバーに登録]** ウィンドウで、作成したサーバーの名前を選択してから **[次へ]** を選択します。

    7. **[デバイスを監視]** ウィンドウで、監視レベルを選択してから **[次へ]** を選択します。

    8. **[組織を作成]** ウィンドウで、**[組織]** を選択するか、新しい組織を作成して **[次へ]** を選択します。

    9. **[iOS 設定アシスタントを構成]** ウィンドウで、ユーザーに表示する手順を選択し、**[準備]** を選択します。 メッセージが表示されたら、認証して信頼の設定を更新します。  

    10. iOS デバイスの準備が完了したら、USB ケーブルを取り外します。  

6.  **デバイスを配布します**。
    これで、デバイスを企業登録できるようになりました。 デバイスをオフにし、ユーザーにデバイスを配布します。 ユーザーがデバイスをオンにすると、セットアップ アシスタントが起動します。

## <a name="how-users-install-and-use-the-company-portal-on-their-devices"></a>デバイスにポータル サイト アプリをインストールして使用する方法

ユーザー アフィニティが構成されたデバイスでは、ポータル サイト アプリをインストールして実行し、アプリをダウンロードしてデバイスを管理できます。 ユーザーは、デバイスを受け取った後、セットアップ アシスタントを完了してポータル サイト アプリをインストールするために、次に示す追加の手順を完了する必要があります。

### <a name="how-users-enroll-corporate-owned-ios-devices-with-user-affinity"></a>ユーザー アフィニティありで企業所有 iOS デバイスを登録する方法

1. ユーザーは、デバイスの電源をオンにすると、セットアップ アシスタントを完了するように求められます。 セットアップ中にユーザーは資格情報を要求されます。 Intune のサブスクリプションに関連付けられている資格情報 (つまり一意の個人名または UPN) を使用する必要があります。

2. セットアップ中にユーザーは Apple ID を要求されます。 デバイスでポータル サイトをインストールできるように、Apple ID を入力する必要があります。 この ID は、セットアップの完了後に iOS の設定メニューから入力することもできます。

3. セットアップが完了したら、iOS デバイスで App Store からポータル サイト アプリをインストールする必要があります。

4. これでユーザーは、デバイスを設定するときに使用した UPN を使用して、ポータル サイトにサインインできるようになります。

5. ユーザーはログインすると、デバイスを登録するように求められます。 最初の手順は、デバイスを指定することです。 アプリには、ユーザーの Intune アカウントに割り当てられている企業登録済みの iOS デバイスの一覧が表示されます。 一致するデバイスを選択する必要があります。 ユーザーのデバイスがまだ企業登録済みでない場合は、[新しいデバイス] を選択して標準の登録フローを行う必要があります。

6. 次の画面で、ユーザーは、新しいデバイスのシリアル番号を確認する必要があります。 シリアル番号は、[シリアル番号を確認] リンクをタップして設定アプリを起動すると確認できます。 その後、ポータル サイト アプリにシリアル番号の最後の&4; 文字を入力する必要があります。

    この手順では、デバイスが Intune に登録されている会社のデバイスであることが確認されます。 デバイスのシリアル番号が一致しない場合は、間違ったデバイスが選択されています。 その場合は、前の画面に戻って、別のデバイスを選択する必要があります。

7. シリアル番号が確認されると、ポータル サイト アプリはポータル サイトの Web サイトにリダイレクトされ、登録の最終処理が行われます。 Web サイトでは、ユーザーにアプリに戻るように促すメッセージが表示されます。

これで、登録が完了し、ユーザーはこのデバイスのすべての機能を使用できるようになります。

