---
title: macOS デバイスの登録 - Device Enrollment Program
titleSuffix: Microsoft Intune
description: Device Enrollment Program を使用して企業が所有する macOS デバイスを登録する方法を説明します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/13/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d6f9035b5a31d04e7d6ec6c5ec5b8f69a7c0943f
ms.sourcegitcommit: 0ac196d1d06f4f52f01610eb26060419d248168b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/13/2018
ms.locfileid: "40090138"
---
# <a name="automatically-enroll-macos-devices-with-apples-device-enrollment-program"></a>Apple の Device Enrollment Program を使用して macOS デバイスを自動登録する

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

この記事は、Apple の [Device Enrollment Program (DEP)](https://deploy.apple.com) で購入したデバイスの macOS デバイス登録を設定するのに役立ちます。 自動で多数のデバイスの DEP 登録を設定できます。 ユーザーに直接 macOS デバイスを出荷できます。 ユーザーがデバイスの電源をオンにすると、セットアップ アシスタントが構成済み設定で実行され、デバイスが Intune の管理として登録されます。

DEP 登録を設定するには、Intune ポータルと Apple DEP ポータルの両方を使います。 登録時にデバイスに適用された設定を含む DEP 登録プロファイルを作成します。

なお、DEP 登録は[デバイス登録マネージャー](device-enrollment-manager-enroll.md)では動作しません。

<!--
**Steps to enable enrollment programs from Apple**
1. [Get an Apple DEP token and assign devices](#get-the-apple-dep-token)
2. [Create an enrollment profile](#create-an-apple-enrollment-profile)
3. [Synchronize DEP-managed devices](#sync-managed-device)
4. [Assign DEP profile to devices](#assign-an-enrollment-profile-to-devices)
5. [Distribute devices to users](#end-user-experience-with-managed-devices)
-->
## <a name="prerequisites"></a>必要条件
- [Apple の Device Enrollment Program](http://deploy.apple.com) で購入したデバイス
- シリアル番号や注文書番号の一覧。 
- [MDM 機関](mdm-authority-set.md)
- [Apple MDM プッシュ証明書](apple-mdm-push-certificate-get.md)

## <a name="get-an-apple-dep-token"></a>Apple DEP トークンを取得する

DEP に macOS デバイスを登録するには、Apple の DEP トークン (.p7m) ファイルが必要です。 このトークンにより、Intune は企業所有の DEP デバイスに関する情報を同期できるようになります。 また、これによって Intune では、Apple およびデバイスに対するそれらのプロファイルに登録プロファイルをアップロードできるようになります。

DEP トークンを作成する場合は、Apple DEP ポータルを使用します。 また、管理のためにデバイスを Intune に割り当てる場合にも DEP ポータルを使用します。

> [!NOTE]
> Azure に移行する前に Intune クラシック ポータルからトークンを削除すると、削除された Apple DEP トークンが Intune で復元される場合があります。 Azure Portal から DEP トークンを再び削除できます。

### <a name="step-1-download-the-intune-public-key-certificate-required-to-create-the-token"></a>手順 1. トークンを作成するために必要な Intune 公開キー証明書をダウンロードする

1. [Azure Portal の Intune](https://aka.ms/intuneportal) で、**[デバイスの登録]** > **[Apple の登録]** > **[Enrollment Program トークン]** > **[追加]** の順に選択します。

    ![Enrollment Program トークンを取得します。](./media/device-enrollment-program-enroll-ios/image01.png)

2. **[同意する]** を選択して、Microsoft がユーザーとデバイスの情報を Apple に送信できるようにします。

   ![公開キーをダウンロードするための [Apple 証明書] ワークスペースの [Enrollment Program トークン] のスクリーンショット。](./media/device-enrollment-program-enroll-ios-newui/add-enrollment-program-token-pane.png)

3. **[公開キーをダウンロードします]** を選択し、暗号化キー (.pem) ファイルをダウンロードしてローカルに保存します。 .pem ファイルは、Apple Device Enrollment Program ポータルから信頼関係証明書を要求するために使用します。


### <a name="step-2-use-your-key-to-download-a-token-from-apple"></a>手順 2. キーを使用して Apple からトークンをダウンロードする

1. **[Create a token for Apple's Device Enrollment Program]\(Apple Device Enrollment Program 用のトークンを作成します\)** を選択して Apple の Deployment Program ポータルを開き、会社の Apple ID でサインインします。 この Apple ID を使って、DEP トークンを更新できます。
2.  Apple の [Deployment Programs ポータル](https://deploy.apple.com) で、**[Device Enrollment Program]** の **[開始]** を選択します。

3. **[Manage Servers\(サーバーの管理\)]** ページで、**[Add MDM Server\(MDM サーバーの追加\)]** を選びます。
4. **MDM サーバー名**を入力し、**[Next]** (次へ) をクリックします。 サーバー名は、自分がモバイル デバイス管理 (MDM) サーバーを識別できるようにするための名前です。 Microsoft Intune サーバーの名前または URL ではありません。

5. **[Add &lt;ServerName&gt;\(<サーバー名> の追加\)]** ダイアログ ボックスが開き、**[Upload Your Public Key\(公開キーをアップロードする\)]** と表示されます。 **[Choose File]** (ファイルを選択) をクリックして .pem ファイルをアップロードし、**[Next]** (次へ) を選択します。

6. **[Deployment Programs] (展開プログラム)** &gt; **[Device Enrollment Program]** &gt; **[Manage Devices] (デバイスの管理)** の順に移動します。
7. **[Choose Devices By\(デバイスの選択方法\)]** で、デバイスを識別する方法を指定します。
    - **Serial Number\(シリアル番号\)**
    - **Order Number\(注文番号\)**
    - **Upload CSV File\(CSV ファイルのアップロード\)**

   ![シリアル番号でデバイスを選択するように指定し、アクションの選択でサーバーへの割り当てを設定し、サーバー名を選択したスクリーンショット。](./media/enrollment-program-token-specify-serial.png)

8. **[アクションの選択]** で **[Assign to Server]\(サーバーに割り当てる\)** を選択し、Microsoft Intune に指定した **ServerName** を選択して、&lt;[OK]&gt; を選択します。 指定したデバイスが管理用に Intune サーバーに割り当てられて、**[Assignment Complete\(割り当て完了\)]** と表示されます。

   Apple ポータルで、**[Deployment Programs\(配備プログラム\)]** &gt; **[Device Enrollment Program\(Device Enrollment Program\)]** &gt; **[View Assignment History\(割り当て履歴の表示\)]** の順に移動して、デバイスとその MDM サーバーの割り当てのリストを表示します。

### <a name="step-3-save-the-apple-id-used-to-create-this-token"></a>手順 3. このトークンの作成に使用した Apple ID を保存する

Azure ポータルの Intune で、後で参照するための Apple ID を指定します。

![Enrollment Program トークンの作成に使った Apple ID の指定と、Enrollment Program トークンの参照のスクリーンショット。](./media/device-enrollment-program-enroll-ios/image03.png)

### <a name="step-4-upload-your-token"></a>手順 4. トークンをアップロードする
**[Apple トークン]** ボックスで、証明書 (.pem) ファイルを参照し、**[開く]** を選択して、**[作成]** を選択します。 このプッシュ証明書を使用して、Intune はデバイスを登録し、登録したデバイスにポリシーを適用して macOS デバイスを管理できます。 Intune は、Apple と自動的に同期して、Enrollment Program アカウントを表示します。

## <a name="create-an-apple-enrollment-profile"></a>Apple 登録プロファイルの作成

これでトークンがインストールされました。DEP デバイスの登録プロファイルを作成することができます。 デバイス登録プロファイルで、デバイス グループに対して登録時に適用する設定を定義します。

1. Azure Portal の Intune で、**[デバイスの登録]** > **[Apple の登録]** > **[Enrollment Program トークン]** の順に選択します。
2. トークンを選択し、**[プロファイル]** を選択し、**[プロファイルの作成]** を選択します。

    ![[プロファイルの作成] のスクリーンショット。](./media/device-enrollment-program-enroll-ios/image04.png)

3. **[プロファイルの作成]** で、管理用にプロファイルの **[名前]** と **[説明]** を入力します。 ユーザーにはこれらの詳細は表示されません。 この **[名前]** フィールドを使用して、Azure Active Directory で動的グループを作成できます。 この登録プロファイルに対応するデバイスを割り当てるために enrollmentProfileName パラメーターを定義する場合はプロファイル名を使用します。 Azure Active Directory の動的グループの詳細については[こちら](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal#using-attributes-to-create-rules-for-device-objects)を参照してください。

    ![プロファイル名と説明。](./media/device-enrollment-program-enroll-macos/createprofile.png)

4. **[プラットフォーム]** で **[macOS]** を選びます。

5. **[ユーザー アフィニティ]** で、このプロファイルに対応するデバイスを割り当て済みユーザーとともに登録する必要があるかどうかを選択します。
    - **[ユーザー アフィニティとともに登録する]** - このオプションは、ユーザーに属しているデバイスであって、かつアプリのインストールなどのサービスにポータル サイトのアプリを使用する必要があるデバイスの場合に選択します。 ADFS を使用している場合、ユーザー アフィニティには [WS-Trust 1.3 Username/Mixed エンドポイント](https://technet.microsoft.com/library/adfs2-help-endpoints)が必要です。 [詳細情報](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint)。多要素認証は、ユーザー アフィニティが有効な macOS DEP デバイスではサポートされません。

    - **[ユーザー アフィニティなしで登録する]** - このオプションは、1 人のユーザーに関連付けられていないデバイスの場合に選択します。 ローカルのユーザー データにアクセスせずにタスクを実行するデバイスで使用します。 ポータル サイト アプリなどのアプリは動作しません。

6. **[デバイス管理の設定]** を選択し、このプロファイルを使用するデバイスに対して、ロックされた登録を使用するかどうかを選択します。 **[ロックされた登録]** を選択すると、**[システム環境設定]** メニューから、または**ターミナル**を通じて管理プロファイルの削除を許可する macOS 設定が、無効になります。 デバイスの登録後は、デバイスを出荷時の設定にリセットしないと、この設定を変更することができません。

    ![[デバイス管理の設定] のスクリーンショット。](./media/device-enrollment-program-enroll-macos/devicemanagementsettingsblade-macos.png)
 
7. **[OK]** を選びます。

8. **[セットアップ アシスタントの設定]** を選択し、次のプロファイル設定を構成します。![[セットアップ アシスタントのカスタマイズ]](./media/device-enrollment-program-enroll-macos/setupassistantcustom-macos.png)。


    |                 Setting                  |                                                                                               説明                                                                                               |
    |------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    |     <strong>部門名</strong>     |                                                             アクティブ化中にユーザーが <strong>[構成について]</strong> をタップすると表示されます。                                                              |
    |    <strong>部署の電話番号</strong>     |                                                          アクティブ化中にユーザーが <strong>[ヘルプが必要ですか]</strong> ボタンをクリックすると表示されます。                                                          |
    | <strong>セットアップ アシスタントのオプション</strong> |                                                     次の省略可能な設定は、後で macOS の <strong>[設定]</strong> メニューで設定できます。                                                      |
    |        <strong>パスコード</strong>         | アクティブ化時にパスコードの入力を求めます。 デバイスがセキュリティで保護される場合や、他の何らかの方法 (デバイスを 1 つのアプリに制限するキオスク モードなど) でアクセスが制御されている場合を除き、パスコードは常に必須にしてください。 |
    |    <strong>ロケーション サービス</strong>    |                                                                 有効にすると、アクティブ化時に、セットアップ アシスタントによってこのサービスがプロンプトされます。                                                                  |
    |         <strong>復元</strong>         |                                                                有効にすると、アクティブ化時に、セットアップ アシスタントによって iCloud バックアップがプロンプトされます。                                                                 |
    |   <strong>iCloud と Apple ID</strong>   |                         有効にすると、セットアップ アシスタントによって Apple ID でサインインするように求められ、[アプリとデータ] 画面で iCloud バックアップからデバイスを復元できるようになります。                         |
    |  <strong>使用条件</strong>   |                                                   有効にすると、アクティブ化時に、セットアップ アシスタントによって Apple の使用条件に同意するように求められます。                                                   |
    |        <strong>Touch ID</strong>         |                                                                 有効にすると、アクティブ化時に、セットアップ アシスタントによってこのサービスがプロンプトされます。                                                                 |
    |        <strong>Apple Pay</strong>        |                                                                 有効にすると、アクティブ化時に、セットアップ アシスタントによってこのサービスがプロンプトされます。                                                                 |
    |          <strong>Zoom</strong>           |                                                                 有効にすると、アクティブ化時に、セットアップ アシスタントによってこのサービスがプロンプトされます。                                                                 |
    |          <strong>Siri</strong>           |                                                                 有効にすると、アクティブ化時に、セットアップ アシスタントによってこのサービスがプロンプトされます。                                                                 |
    |     <strong>診断データ</strong>     |                                                                 有効にすると、アクティブ化時に、セットアップ アシスタントによってこのサービスがプロンプトされます。                                                                 |
    |     <strong>FileVault</strong>           |  |
    |     <strong>iCloud 診断</strong>  |  |
    |     <strong>登録</strong>        |  |


10. **[OK]** を選びます。

11. プロファイルを保存するには、**[作成]** を選択します。

## <a name="sync-managed-devices"></a>マネージド デバイスを同期する
デバイスを管理するアクセス許可を Intune に割り当てたので、Intune と Apple を同期して、マネージド デバイスを Azure ポータルの Intune に表示できます。

1. Azure ポータルの Intune で、**[デバイスの登録]**>**[Apple の登録]**>**[Enrollment Program トークン]** の順に選択し、リスト内でトークンを選択し、**[デバイス]**>**[同期]** の順に選択します。![[Enrollment Program デバイス] ノードと [同期] リンクが選ばれているスクリーンショット。](./media/device-enrollment-program-enroll-ios/image06.png)

   許容される Enrollment Program トラフィックについての Apple の規約に準拠するため、Intune では次の制限が課せられます。
   - 完全な同期は 7 日に 1 回だけ実行できます。 完全な同期中に、Intune に接続された Apple MDM サーバーに割り当てられているシリアル番号の完全な最新の一覧を Intune がフェッチします。 DEP ポータルで Apple MDM サーバーからの割り当てを解除せずに Intune ポータルから Enrollment Program デバイスが削除されると、完全同期が実行されるまで Intune に再インポートされません。   
   - 同期は 24 時間ごとに自動的に実行されます。 **[同期]** ボタンをクリックして同期することもできます (15 分以内に 2 回以上は同期できません)。 すべての同期要求は、完了までに 15 分与えられます。 同期が完了するまで、**[同期]** ボタンは無効になっています。 この同期により、既存のデバイスの状態が更新され、Apple MDM サーバーに割り当てられている新しいデバイスがインポートされます。   


## <a name="assign-an-enrollment-profile-to-devices"></a>登録プロファイルをデバイスに割り当てる
登録する前に、Enrollment Program プロファイルをデバイスに割り当てる必要があります。

1. Intune で、**[デバイスの登録]** > **[Apple の登録]** > **[Enrollment Program トークン]** の順に選択し、リスト内でトークンを選択します。
2. **[デバイス]** を選択し、リスト内でデバイスを選択し、**[プロファイルの割り当て]** を選択します。
3. **[プロファイルの割り当て]** で、デバイス用のプロファイルを選択し、**[割り当て]** を選択します。

### <a name="assign-a-default-profile"></a>既定のプロファイルを割り当てる

特定のトークンを使用して登録するすべてのデバイスに適用される、macOS と iOS の既定のプロファイルを選択することができます。 

1. Azure Portal の Intune で、**[デバイスの登録]** > **[Apple の登録]** > **[Enrollment Program トークン]** の順に選択し、リスト内でトークンを選択します。
2. **[既定のプロファイルの設定]** を選択し、ドロップダウン リストでプロファイルを選択し、**[保存]** を選択します。 このプロファイルは、トークンに登録されたすべてのデバイスに適用されます。

## <a name="distribute-devices"></a>デバイスを配布する
Apple と Intune の間の同期と管理を有効にし、DEP デバイスを登録できるようにプロファイルを割り当てました。 ユーザーにデバイスを配布できるようになりました。 ユーザー アフィニティがあるデバイスでは、各ユーザーに Intune ライセンスを割り当てる必要があります。 ユーザー アフィニティがないデバイスでは、デバイスのライセンスが必要です。 デバイスが出荷時の設定にリセットされるまで、アクティブ化されたデバイスは登録プロファイルを適用できません。

## <a name="renew-a-dep-token"></a>DEP トークンを更新する  
1. deploy.apple.com に移動します。  
2. **[サーバーの管理]** で、更新するトークン ファイルに関連付けられた MDM サーバーを選択します。
3. **[新しいトークンの生成]** を選択します。

    ![生成された新しいトークンのスクリーンショット。](./media/device-enrollment-program-enroll-ios/generatenewtoken.png)

4. **[Your Server Token]\(サーバー トークン\)** を選択します。  
5. [Azure portal の Intune](https://aka.ms/intuneportal) で、**[デバイスの登録]** > **[Apple の登録]** > **[Enrollment Program トークン]**、トークンの順に選択します。
    ![Enrollment Program トークンのスクリーンショット。](./media/device-enrollment-program-enroll-ios/enrollmentprogramtokens.png)

6. **[トークンを更新する]** を選択し、元のトークンの作成に使用した Apple ID を入力します。  
    ![生成された新しいトークンのスクリーンショット。](./media/device-enrollment-program-enroll-ios/renewtoken.png)

8. 新しくダウンロードしたトークンをアップロードします。  
9. **[トークンを更新する]** を選択します。 トークンが更新されたことの確認が表示されます。   
    ![確認のスクリーンショット。](./media/device-enrollment-program-enroll-ios/confirmation.png)

## <a name="next-steps"></a>次の手順

macOS デバイスを登録したら、[それらの管理](device-management.md)を開始できます。