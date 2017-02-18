---
title: "セットアップ アシスタントを使用した iOS デバイスの登録 | Microsoft Docs"
description: "Apple Configurator ツールを使用して企業所有の iOS デバイスを登録し、デバイスを工場出荷時の設定にリセットして、セットアップ アシスタントを実行する準備をします。"
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 02/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 46e5b027-4280-4809-b45f-651a6ab6d0cd
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: a2e840797c06322b9efc59438e0675e57b7cdb24
ms.openlocfilehash: facae5f49b52760dcea0653bd261e16e13e11bbf


---

# <a name="enroll-ios-devices-with-apple-configurator-by-using-setup-assistant"></a>Apple Configurator でセットアップ アシスタントを使用して iOS デバイスを登録する

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune は、Mac コンピューターで実行される [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) を使用した、企業所有の iOS デバイスの登録をサポートします。 このプロセスではデバイスを工場出荷時の設定にリセットし、セットアップ アシスタントを実行してデバイスの新しいユーザー用に会社のポリシーをインストールするための準備を行います。

>[!NOTE]
>この登録方法は、[デバイス登録マネージャー](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)の方法と同時に使用することはできません。

Apple Configurator を使用して、iOS デバイスを工場出荷時の設定にリセットし、デバイスの新しいユーザー用にセットアップするための準備を行うことができます。 この方法では、USB を使用して iOS デバイスを Mac コンピューターに接続し、会社の登録をセットアップする必要があります。この方法では、Apple Configurator 2.0 の使用を想定しています。 ほとんどのシナリオでは、Intune ポータル サイト アプリを有効にするため、iOS デバイスに適用されるポリシーに**ユーザー アフィニティ**が含まれている必要があります。

## <a name="prerequisites-for-enrolling-ios-devices-by-using-apple-configurator-with-setup-assistant"></a>Apple Configurator とセットアップ アシスタント使用して iOS デバイスを登録する場合の前提条件

- [APNs 証明書のインストール](set-up-ios-and-mac-management-with-microsoft-intune.md)

- iOS デバイスに物理的にアクセスできることを確認する &mdash; デバイスを、パスワードで保護されていない工場出荷時の設定にリセットする必要があります。

- デバイスのシリアル番号を取得する &mdash; [iOS シリアル番号を取得する方法](https://support.apple.com/en-us/HT204308)に関するページを参照してください。

- USB 接続ケーブルを手元に置いておく。

- [Apple Configurator 2.0](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) がインストールされている Mac コンピューターを用意する。


## <a name="steps-to-enroll-ios-devices-by-using-apple-configurator-with-setup-assistant"></a>Apple Configurator とセットアップ アシスタント使用して iOS デバイスを登録する手順

次の手順では、Apple Configurator とセットアップ アシスタントを使用して iOS デバイスを登録するための準備方法を説明します。 組織でデバイスが追加および削除された場合、以下に示すように、シリアル番号の追加や削除など、いくつかの手順を繰り返すことがあります。

### <a name="create-mobile-device-groups-optional"></a>モバイル デバイス グループを作成する (オプション)

企業でデバイスの管理を容易にするためにモバイル デバイス グループが必要な場合は、必要に応じてこれらのグループを作成できます。 詳細については、「[Microsoft Intune でユーザーとデバイスの管理にグループを使用する](use-groups-to-manage-users-and-devices-with-microsoft-intune.md)」を参照してください。

### <a name="create-a-profile-for-devices"></a>デバイスのプロファイルを作成する

デバイス登録プロファイルで、デバイスのグループに適用する設定を定義します。

1. [Microsoft Intune 管理コンソール](http://manage.microsoft.com)で、**[ポリシー]** &gt; **[業務用デバイスの登録]** の順に選択し、**[追加]** を選択します。

  ![デバイス登録プロファイルの作成](../media/pol-sa-corp-enroll.png)

2. デバイス プロファイルの詳細を入力します。

   -   **名前** &mdash; デバイス登録プロファイルの名前 (ユーザーには表示されません)。

   -   **説明** &mdash; デバイス登録プロファイルの説明 (ユーザーには表示されません)。

   -   **登録の詳細** &mdash; デバイスの登録方法を指定します。

       -   **ユーザー アフィニティを要求する** &mdash; 初回セットアップ時にデバイスをユーザーに関連付ける必要があります。その後、デバイスは企業のデータや電子メールにアクセスすることが許可されます。 ユーザーに属し、アプリのインストールなどサービスのポータル サイトを使用する必要がある DEP 管理対象のデバイスの場合、**ユーザー アフィニティ**をセットアップする必要があります。

       -   **ユーザー アフィニティがありません** &mdash; デバイスは、ユーザーと関連付けられません。 このデバイス関連付け情報を使用すると、ローカルのユーザー データにアクセスしなくてもタスクを実行できます。 ユーザー アフィリエーションが必要なアプリ (基幹業務アプリのインストールに使用されるポータル サイト アプリを含む) は機能しません。

   -   **デバイス グループの事前割り当て** &mdash; このプロファイルで展開されているすべてのデバイスは最初にこのグループに属します。 登録後にデバイスの再割り当てができます。

   > [!Important]
   > グループの割り当てが Intune から Azure Active Directory に移動します。 Intune アカウントで適用可能な更新プログラムが受信されると、**[デバイスを次のグループに割り当てる]** オプションは表示されません。 [詳細については、ここをクリック](/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune#changes-to-intune-group-assignments)してください。

   -  **Device Enrollment Program** &mdash; セットアップ アシスタントの登録では、Apple Device Enrollment Program (DEP) を使用できません。 このトグルが**オフ**に設定されていることを確認してください。

3.  **[プロファイルの保存]** を選択してプロファイルを追加します。

### <a name="add-ios-devices-to-enroll-with-setup-assistant"></a>セットアップ アシスタントに登録する iOS デバイスを追加する

1. [Microsoft Intune の管理コンソール](http://manage.microsoft.com)で、**[グループ]**&gt;**[すべてのデバイス]**&gt;**[会社が所有しているすべてのデバイス]**&gt;**[すべてのデバイス]** の順に移動し、**[デバイスの追加]** を選択します。 

   デバイスの追加方法は&2; つあります。

   ![[デバイスの追加] ダイアログ ボックス](../media/pol-SA-enroll-iOS-SetupAssistant.png)

   -  **シリアル番号が含まれている CSV ファイルをアップロード** &mdash; .csv ファイル 1 つあたりデバイス 5,000 個または 5 MB を上限とする、2 つの列を持つヘッダーなしのコンマ区切り値 (.csv) リストを作成します。

    |||
    |-|-|
    |&lt;シリアル 1&gt;|&lt;デバイス 1 の詳細&gt;|
    |&lt;シリアル&2;&gt;|&lt;デバイス 2 の詳細&gt;|

  この .csv ファイルをテキスト エディターで開くと、次のように表示されます。

    ```
    0000000,PO 1234
    111111111,PO 1234
    ```

  -  **デバイスの詳細を手動で追加** &mdash; 最大 15 台のデバイスのシリアル番号とメモまたは詳細を入力します。

  **[デバイスの確認]** ウィンドウで、シリアル番号を確認できます。 再度インポートするシリアル番号の**詳細**を上書きするかどうかを決定することもできます。あるいは、**[上書き]** チェック ボックスをオフにして、現在の詳細を保持することもできます。 

> [!NOTE] 
> 既存の Intune 管理者コンソールでは、管理者はアップロードされた CSV から関連する詳細をそのまま使用し、個々のシリアル番号の既存の詳細を上書きすることができます。 新しい Azure Portal では、単にすべてのシリアル番号の詳細を上書きするか、すべてのシリアル番号の新しい詳細を無視することができます。

  > [!NOTE]
  > 後で Intune 管理対象から会社所有のデバイスを除外する場合は、**[会社の事前登録済みデバイス]** の **[iOS シリアル番号を使用]** デバイス グループに移動し、Intune からデバイスのシリアル番号を削除して、デバイスの登録を無効にする必要がある場合があります。 シリアル番号の削除時またはその前後に Intune が障害復旧手順を実行した場合、アクティブなデバイスのシリアル番号のみがそのグループ内に存在していることを確認する必要があります。

2. **[次へ]** を選択します。

3. 登録するデバイスを選択します。 既に登録されているか、他の方法によって登録済みのシリアル番号はインポートできません。 **[次へ]** をクリックして続行します。

### <a name="assign-a-profile"></a>プロファイルを割り当てる

使用できるプロファイルのリストから、追加するデバイスに割り当てるプロファイルを指定し、**[登録プロファイルの詳細]** を確認し、**[完了]** を選択します。 手動で追加したデバイスは、任意の登録プロファイルに割り当てることができます。

> [!Important]
> 現在、Intune では "既定の" デバイス登録プロファイルを指定できます。つまり、新しいシリアル番号は、Apple DEP サービスと同期するときに、その既定のプロファイルに自動的に割り当てられます。 今後、新しい Azure Portal にテナントが移行された場合、既定のプロファイルを設定し、そのプロファイルにシリアル番号を自動で割り当てられなくなります。 したがって、ユーザーが自分でシリアル番号をプロファイルに割り当てる必要があります。 [詳細情報](https://docs.microsoft.com/intune-azure/enroll-devices/enroll-ios-devices-using-device-enrollment-program)

### <a name="export-a-profile-to-deploy-to-ios-devices"></a>iOS デバイスに展開するプロファイルをエクスポートする

1. [Microsoft Intune の管理コンソール](http://manage.microsoft.com)で、**[ポリシー]**&gt;**[業務用デバイスの登録]** の順に進み、モバイル デバイスに展開するデバイス プロファイルを選択します。 

2. タスク バーの **[エクスポート]** を選択します。 **プロファイルの URL**をコピーおよび保存します。 Apple Configurator を使用してこれを後でアップロードして、iOS デバイスで使用する Intune プロファイルを定義します。

  Apple Configurator 2 をサポートするには、2.0 プロファイルの URL を編集する必要があります。 これを行うには、
    ```
    https://manage.microsoft.com/EnrollmentServer/Discovery.svc/iOS/ESProxy?id=
    ```
    上記のコードを以下のコードに置き換えます。

    ```
    https://appleconfigurator2.manage.microsoft.com/MDMServiceConfig?id=
    ```

   iOS デバイスで使用される Intune プロファイルを定義するには、以下の手順で Apple Configurator を使用して Apple DEP サービスにこのプロファイル URL をアップロードします。



### <a name="prepare-the-device-with-apple-configurator"></a>Apple Configurator を使用してデバイスを準備する

モバイル デバイスを管理するために、iOS デバイスを Mac コンピューターに接続および登録します。

1.  Mac コンピューターで **Apple Configurator 2** を開きます。 メニュー バーで、**[Apple Configurator 2]** を選択し、**[基本設定]** を選択します。

   > [!WARNING]
   > デバイスは、登録プロセス中に、出荷時の構成にリセットされます。 ベスト プラクティスとして、デバイスをリセットし、オンにします。 デバイスを接続するときはデバイスの **[こんにちは]** 画面を表示する必要があります。

2. 基本設定ウィンドウで **[サーバー]** を選択し、プラス記号 (+) を選択して MDM サーバー ウィザードを起動します。 **[次へ]** を選択します。

3. 「Microsoft Intune での iOS デバイスのセットアップ アシスタントを使用した登録」の手順 6 の MDM サーバーの**名前**と**登録 URL** を入力します。 登録 URL には、Intune からエクスポートされた登録プロファイル URL を入力します。 **[次へ]** を選択します。  

   "サーバー URL が検証されていない" ことを示す警告は、無視して構いません。 操作を続行するには、ウィザードが完了するまで **[次へ]** を選択します。

4.  USB アダプターを使用して iOS モバイル デバイスを Mac コンピューターに接続します。

    > [!WARNING]
    > デバイスは、登録プロセス中に、出荷時の構成にリセットされます。 ベスト プラクティスとして、デバイスをリセットし、オンにします。 セットアップ アシスタントを開始するとデバイスに **[こんにちは]** 画面が表示されます。

5.  **[準備]** を選択します。 [iOS デバイスを準備] ウィンドウで、**[手動]** を選択してから **[次へ]** を選択します。

6. [MDM サーバーに登録] ウィンドウで、作成したサーバーの名前を選択してから **[次へ]** を選択します。

7. [デバイスを監視] ウィンドウで、監視レベルを選択してから **[次へ]** を選択します。

8. [組織を作成] ウィンドウで、**[組織]** を選択するか、新しい組織を作成して **[次へ]** を選択します。

9. [iOS 設定アシスタントを構成] ウィンドウで、ユーザーに表示する手順を選択し、**[準備]** を選択します。 メッセージが表示されたら、認証して信頼の設定を更新します。  

10. iOS デバイスの準備が完了したら、USB ケーブルを取り外します。  

### <a name="distribute-devices"></a>デバイスを配布する

これで、デバイスを企業登録できるようになりました。 

デバイスをオフにし、ユーザーにデバイスを配布します。 ユーザーがデバイスをオンにすると、セットアップ アシスタントが起動します。


### <a name="see-also"></a>関連項目
[デバイスを登録するための前提条件](prerequisites-for-enrollment.md)



<!--HONumber=Feb17_HO2-->


