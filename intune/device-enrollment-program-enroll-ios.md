---
title: "iOS デバイスの登録 - Device Enrollment Program"
titleSuffix: Intune Azure preview
description: "Intune Azure プレビュー: Device Enrollment Program を使用して会社が所有している iOS デバイスを登録する方法について説明します。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 04/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7981a9c0-168e-4c54-9afd-ac51e895042c
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 5144b9e7c17a3323667b9ca68cb47829d69866c3
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017


---

# <a name="enroll-ios-devices-using-device-enrollment-program"></a>Device Enrollment Program を使用して iOS デバイスを登録する

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

このトピックでは、IT 管理者が [Apple の Device Enrollment Program (DEP)](https://deploy.apple.com) で購入した会社所有の iOS デバイスを登録する方法について説明します。 Microsoft Intune は DEP を "無線" で登録する登録プロファイルを展開できるので、管理者が各管理対象デバイスを操作する必要はありません。 DEP プロファイルには、登録の間にデバイスに適用する管理設定が含まれています。 登録パッケージには、デバイスのセットアップ アシスタント オプションを含めることができます。

>[!NOTE]
>DEP 登録は、[デバイス登録マネージャー](device-enrollment-manager-enroll.md)と同時に使うことはできません。
>また、ユーザーがポータル サイト アプリを使って iOS デバイスを登録し、デバイスのシリアル番号がインポートされて DEP プロファイルが割り当てられると、このデバイスは Intune から登録解除されます。

**DEP 登録手順**
1. [Apple DEP トークンを取得する](#get-the-apple-dep-certificate)
2. [DEP プロファイルを作成する](#create-an-apple-dep-profile)
3. [Intune サーバーに Apple DEP シリアル番号を割り当てる](#assign-apple-dep-serial-numbers-to-your-mdm-server)
4. [DEP 管理対象デバイスを同期する](#synchronize-dep-managed-devices)
5. [デバイスに DEP プロファイルを割り当てる](#assign-a-dep-profile-to-devices)
6. [デバイスをユーザーに配布する](#distribute-devices-to-users)

## <a name="get-the-apple-dep-certificate"></a>Apple DEP 証明書を取得する
Apple の Device Enrollment Program (DEP) に会社所有の iOS デバイスを登録するには、Apple から提供される DEP 証明書 (.p7m) ファイルが必要です。 このトークンにより、Intune は企業所有の DEP 参加デバイスに関する情報を同期できるようになります。 また、Intune は Apple への登録プロファイルのアップロードを実行して、デバイスをそれらのプロファイルに割り当てられるようになります。

DEP を使用して企業所有の iOS デバイスを管理するには、組織が Apple DEP に参加し、そのプログラムを使用してデバイスを取得する必要があります。 そのプロセスの詳細については、https://deploy.apple.com を参照してください。 このプログラムの利点には、各デバイスをコンピューターに USB ケーブルを使用して接続することなく、デバイスを楽に設定できる点があります。

> [!NOTE]
> Intune テナントを Intune クラシック コンソールから Azure Portal に移行し、移行の間に Apple DEP トークンを Intune 管理コンソールから削除した場合、その DEP トークンは Intune アカウントに復元されていない可能性があります。 Azure Portal から DEP トークンを再び削除できます。

**手順 1: Apple DEP トークンを作成するために必要な Intune 公開キー証明書をダウンロードします。**<br>
1. Azure Portal で、**[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。 Intune ブレードで、**[デバイスの登録]** > **[Apple DEP トークン]** の順に選びます。
2. **[Download your public key (公開キーをダウンロードする)]** を選択して、暗号化キー (.pem) ファイルをダウンロードし、ローカルに保存します。 .pem ファイルは、Apple Device Enrollment Program ポータルから信頼関係証明書を要求するために使用します。

**手順 2:適切な Apple の Web サイトから、Apple DEP トークンをダウンロードします。**<br>
[[Apple 展開プログラムを使用して DEP のトークンを作成します]](https://deploy.apple.com) (https://deploy.apple.com) を選択し、会社の Apple ID でサインインします。 この Apple ID を使って、DEP トークンを更新できます。

   1.  Apple の [Device Enrollment Program Portal](https://deploy.apple.com) で、**[Device Enrollment Program]** &gt; **[Manage Servers (サーバーの管理)]** の順に移動し、**[Add MDM Server (MDM サーバーの追加)]** を選びます。
   2.  **MDM サーバー名**を入力し、**[Next]** (次へ) をクリックします。 サーバー名は、自分がモバイル デバイス管理 (MDM) サーバーを識別できるようにするための名前です。 Microsoft Intune サーバーの名前または URL ではありません。
   3.  **[Add &lt;ServerName&gt;]** ダイアログ ボックスが開きます。 **[Choose File]** (ファイルを選択) をクリックして .pem ファイルをアップロードし、**[Next]** (次へ) を選択します。
   4.  **[Add &lt;ServerName&gt;]** (<サーバー名> の追加) ダイアログ ボックスに、**[Your Server Token]** (サーバー トークン) リンクが表示されます。 サーバー トークン (.p7m) ファイルをコンピューターにダウンロードした後、**[Done]** (完了) を選択します。

**手順 3:Apple DEP トークンの作成に使用する Apple ID を入力します。この ID は、Apple DEP トークンを更新するために使用できます。**

**手順 4:アップロードする Apple DEP トークンを参照します。Intune は自動的に DEP アカウントと同期します。**<br>
証明書 (.pem) ファイルに移動し、**[開く]** を選択して、**[アップロード]** を選択します。 このプッシュ証明書を使用して、Intune はモバイル デバイスを登録し、登録したモバイル デバイスにポリシーを適用して iOS デバイスを管理できます。

## <a name="create-an-apple-dep-profile"></a>Apple DEP プロファイルを作成する

デバイス登録プロファイルで、デバイスのグループに適用する設定を定義します。 以下の手順では、DEP を使用して登録される iOS デバイス用のデバイス登録プロファイルを作成する方法を示しています。

1. Azure Portal で、**[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
2. [Intune] ブレードで **[デバイスの登録]** を選択し、**[Apple の登録]** を選択します。
3. **[Apple Device Enrollment Program (DEP) 設定の管理]** で、**[DEP プロファイル]** を選択します。
4. **[Apple DEP Profiles (Apple DEP プロファイル)]** ブレードで、**[作成]** を選択します。
5. **[登録プロファイルの作成]** ブレードで、プロファイルの名前と説明を入力します。
6. **[ユーザー アフィニティ]** で、このプロファイルに対応するデバイスをユーザー アフィニティと共に登録するかどうかを選択します。

 - **[ユーザー アフィニティとともに登録する]** - 初回セットアップ時にデバイスをユーザーに関連付ける必要があります。その後、デバイスは企業のデータや電子メールにアクセスすることが許可されます。 ユーザーに属していて、アプリのインストールなどのサービスにポータル サイトを使用する必要がある DEP 管理対象のデバイスの場合、ユーザー アフィニティを選択する必要があります。 多要素認証 (MFA) は、ユーザー アフィニティを使用して DEP デバイスに登録しているときに動作しないことに注意してください。 DEP デバイスに登録が完了すると、MFA は期待どおりに動作します。 最初にサインインするときにパスワードを変更する必要がある新しいユーザーには、DEP デバイスの登録時にプロンプトを表示することはできません。 さらに、パスワードの有効期限が切れているユーザーには、DEP 登録時にパスワードのリセットは求められません。このユーザーは別のデバイスからパスワードをリセットする必要があります。

    >[!NOTE]
    >ユーザー アフィニティが設定された DEP でユーザー トークンを要求するには、[WS-Trust 1.3 Username/Mixed エンドポイント](https://technet.microsoft.com/en-us/library/adfs2-help-endpoints)を有効にする必要があります。 WS-Trust 1.3 について詳しくは、[こちら](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint)をご覧ください。

 - **[ユーザー アフィニティなしで登録する]** - デバイスは、ユーザーと関連付けられません。 このデバイス関連付け情報を使用すると、ローカルのユーザー データにアクセスしなくてもタスクを実行できます。 ユーザー アフィリエーションが必要なアプリ (基幹業務アプリのインストールに使用されるポータル サイト アプリを含む) は機能しません。

7. **[デバイス管理の設定]** を選択し、次のプロファイル設定を構成して、**[保存]** を選択します。

    - **[監督下]** - より多くの管理オプションが使用可能な管理モードです。既定でアクティベーション ロックは無効になります。 このチェック ボックスをオフのままにすると、管理機能が制限されます。

    - **[ロックされた登録]** - ([管理モード] を [監督下] にする必要があります) 管理プロファイルの削除を許可する iOS 設定を無効にします。 このチェック ボックスをオフのままにすると、[設定] メニューから管理プロファイルを削除できます。 この項目は、アクティブ化中に設定され、工場出荷時の設定へのリセット以外の方法では変更できません。

    - **[ペアリングの許可]** - iOS デバイスをコンピューターと同期できるかどうかを指定します。 **[証明書による Apple Configurator の許可]** を選択した場合は、**[Apple Configurator の証明書]** で証明書を選択する必要があります。

    - **[Apple Configurator の証明書]** - **[ペアリングの許可]** で **[証明書による Apple Configurator の許可]** を選択した場合は、インポートする Apple Configurator の証明書を選択します。

8. **[セットアップ アシスタントの設定]** を選択し、次のプロファイル設定を構成して、**[保存]** を選択します。

    - **[部署名]** - アクティブ化中にユーザーが **[About Configuration (構成について)]** をタップすると表示されます。

    - **[部署の電話番号]** - アクティブ化中にユーザーが [ヘルプが必要ですか] ボタンをクリックすると表示されます。
    - **セットアップ アシスタントのオプション** - これらの省略可能な設定は、後で iOS の **[設定]** メニューで設定できます。
        - **パスコード** - アクティブ化時にパスコードの入力を求めます。 デバイスがセキュリティで保護される場合や、他の何らかの方法 (デバイスを 1 つのアプリに制限するキオスク モードなど) でアクセスが制御されている場合を除き、パスコードは常に必須にしてください。
        - **位置情報サービス** - 有効にすると、アクティブ化時に、セットアップ アシスタントによってサービスがプロンプトされます
        - **復元** - 有効にすると、アクティブ化時に、セットアップ アシスタントによって iCloud バックアップがプロンプトされます
        - **Apple ID** - 有効にして、Intune で ID を指定せずにアプリをインストールしようとすると、Apple ID の入力が求められます。 Intune でインストールされるアプリを含め、iOS App Store アプリをダウンロードする際に Apple ID が必須になります。
        - **使用条件** - 有効にすると、アクティブ化時に、セットアップ アシスタントによって Apple の使用条件に同意するように求められます
        - **タッチ ID** - 有効にすると、アクティブ化時に、セットアップ アシスタントによってこのサービスがプロンプトされます
        - **Apple Pay** - 有効にすると、アクティブ化時に、セットアップ アシスタントによってこのサービスがプロンプトされます
        - **ズーム** - 有効にすると、アクティブ化時に、セットアップ アシスタントによってこのサービスがプロンプトされます
        - **Siri** - 有効にすると、アクティブ化時に、セットアップ アシスタントによってこのサービスがプロンプトされます
        - **[診断データ]** - 有効にすると、アクティブ化時に、セットアップ アシスタントによってこのサービスがプロンプトされます

9. プロファイルの設定を保存するには、**[登録プロファイルの作成]** ブレードで **[作成]** を選択します。

## <a name="assign-apple-dep-serial-numbers-to-your-mdm-server"></a>MDM サーバーに Apple DEP シリアル番号を割り当てる
Intune でデバイスを管理できるようにするには、Apple DEP Web ポータルで、デバイスのシリアル番号を Intune MDM サーバーに割り当てる必要があります。

1. [Device Enrollment Program ポータル](https://deploy.apple.com) (https://deploy.apple.com) に移動し、会社の Apple ID でサインインします。

2. **[Deployment Program]** (展開プログラム) &gt; **[Device Enrollment Program]** (デバイス登録プログラム) &gt; **[Manage Devices]** (デバイスの管理) の順に移動します。

3. **デバイスの選択**方法を指定し、デバイス情報を入力して、デバイスの**シリアル番号**、**注文番号**、または **CSV ファイルのアップロード**で詳細を指定します。

4. **[Assign to Server]** (サーバーに割り当てる) を選択し、Microsoft Intune に指定した &lt;ServerName&gt; を選択して、**[OK]** を選択します。

## <a name="synchronize-dep-managed-devices"></a>DEP 管理対象デバイスを同期する
DEP デバイスを管理するアクセス許可を Intune に割り当てたので、Intune と DEP サービスを同期し、管理対象デバイスを Intune ポータルに表示できます。

1. Azure Portal で、**[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。

2. Azure Portal の [Intune] ブレードで **[デバイスの登録]** を選択し、**[Apple の登録]** を選択します。

3. **[Apple Device Enrollment Program (DEP) 設定の管理]** で、**[DEP シリアル番号]** を選択します。

4. **[Apple DEP シリアル番号]** ブレードで **[同期]** を選択します。

5. **[同期]**ブレードで、**[同期を要求]** を選択します。 進行状況バーには、もう一度同期が要求されるまでの待ち時間が表示されます。

    許容される DEP トラフィックについての Apple の規約に準拠するため、Intune では次の制限が課せられます。
     -    完全な DEP 同期は 7 日ごとに 1 回以上実行できません。 完全同期時に、Intune は Apple が Intune に割り当てたすべてのシリアル番号を、シリアルが以前に同期されているかどうかに関係なく更新します。 前回の完全同期の 7 日以内に完全同期が試みられると、Intune は Intune にまだ一覧表示されていないシリアル番号のみを更新します。
     -    すべての同期要求は、完了までに 10 分与えられます。 この時間中または要求が成功するまで、**[同期]** ボタンは無効にされます。

>[!NOTE]
>**[Apple DEP シリアル番号]** ブレードでプロファイルに DEP シリアル番号を割り当てることもできます。

## <a name="assign-a-dep-profile-to-devices"></a>デバイスに DEP プロファイルを割り当てる
Intune によって管理される DEP デバイスを登録する前に、デバイスに DEP プロファイルを割り当てる必要があります。

1. Azure Portal で、**[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。

2. Azure Portal の [Intune] ブレードで **[デバイスの登録]** > **[Apple の登録]** の順に選択し、**[DEP プロファイル]** を選択します。

3. **[Apple DEP 登録プロファイル]** の一覧からデバイスに割り当てるプロファイルを選択し、**[デバイスの割り当て]** を選択します。

4. **[割り当て]** を選択し、このプロファイルを割り当てる DEP デバイスを選択します。 フィルターを適用して DEP の使用可能なデバイスを表示できます。
  - **未割り当て**
  - **任意**
  - **&lt;DEP プロファイル名&gt;**

  ![Intune ポータルで DEP プロファイルを割り当てるための [割り当て] ボタンのスクリーンショット](media/dep-profile-assignment.png)

5. 割り当てるデバイスを選択します。 列の上のチェック ボックスで最大 1,000 のデバイスを選び、**[割り当て]** をクリックします。 1,000 を超えるデバイスを登録するには、すべてのデバイスに DEP プロファイルを割り当てるまで割り当て手順を繰り返します。

## <a name="distribute-devices-to-users"></a>デバイスをユーザーに配布する

これで、会社が所有するデバイスをユーザーに配布できるようになりました。 iOS DEP デバイスの電源をオンにすると、iOS DEP デバイスが Intune の管理対象として登録されます。 デバイスがアクティブ化されて使用中の場合、デバイスを工場出荷時の状態にリセットするまで、プロファイルを適用できません。

「[Microsoft Intune に関してエンド ユーザーを教育する方法](https://docs.microsoft.com/intune/deploy-use/how-to-educate-your-end-users-about-microsoft-intune)」を参照してください。 「[iOS デバイスまたは macOS デバイスを Intune で使用する](https://docs.microsoft.com/intune/deploy-use/how-to-educate-your-end-users-about-microsoft-intune)」にエンド ユーザーを誘導することもできます。 

### <a name="how-users-install-and-use-the-company-portal-on-their-devices"></a>デバイスにポータル サイト アプリをインストールして使用する方法

ユーザー アフィニティが構成されたデバイスでは、ポータル サイト アプリをインストールして実行し、アプリをダウンロードしてデバイスを管理できます。 ユーザーは、デバイスを受け取った後、セットアップ アシスタントを完了してポータル サイト アプリをインストールするために、次に示す追加の手順を完了する必要があります。

