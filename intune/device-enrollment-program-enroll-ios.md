---
title: iOS デバイスの登録 - Device Enrollment Program
titleSuffix: Microsoft Intune
description: Device Enrollment Program を使用して企業が所有する iOS デバイスを登録する方法を説明します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 7ddbf360-0c61-11e8-ba89-0ed5f89f718b
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: af1804f657041055467e302c4dc8913e1035749d
ms.sourcegitcommit: 28262384ec94e43970cc7a33e5d9063972bdf468
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/04/2018
ms.locfileid: "48799661"
---
# <a name="automatically-enroll-ios-devices-with-apples-device-enrollment-program"></a>Apple の Device Enrollment Program を使用して iOS デバイスを自動登録する

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

この記事は、Apple の [Device Enrollment Program (DEP)](https://deploy.apple.com) で購入したデバイスの iOS デバイス登録を有効にする場合に役立ちます。 自動で多数のデバイスの DEP 登録を行うことができます。 iPhone や iPad などのデバイスを直接ユーザーに配信できます。 ユーザーがデバイスの電源をオンにすると、セットアップ アシスタントが構成済み設定で実行され、デバイスが管理対象として登録されます。

DEP 登録を有効にするには、Intune ポータルと Apple DEP ポータルの両方を使います。 管理するために Intune にデバイスを割り当てられるように、シリアル番号のリストまたは注文番号が必要になります。 登録時にデバイスに適用された設定を含む DEP 登録プロファイルを作成します。

なお、DEP 登録は[デバイス登録マネージャー](device-enrollment-manager-enroll.md)では動作しません。

## <a name="what-is-supervised-mode"></a>監視モードとは何か。
Apple は iOS 5 で監視モードを導入しました。 監視モードの iOS デバイスは、さらに細かく制御できます。 そのため、企業所有のデバイスで特に役立ちます。 Intune は Apple Device Enrollment Program (DEP) の一部としてデバイスの監視モードを設定できます。 

監視されていない DEP デバイスのサポートは、iOS 11 で非推奨となりました。 iOS 11 以降では、DEP 構成済みデバイスを常に監視する必要があります。 DEP の is_supervised フラグは、iOS の将来のリリースでは無視されます。

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
- [MDM 機関](mdm-authority-set.md)
- [Apple MDM プッシュ証明書](apple-mdm-push-certificate-get.md)

## <a name="get-an-apple-dep-token"></a>Apple DEP トークンを取得する

DEP に iOS デバイスを登録するには、Apple の DEP トークン (.p7m) ファイルが必要です。 このトークンにより、Intune は企業所有の DEP デバイスに関する情報を同期できるようになります。 また、Intune は Apple に登録プロファイルをアップロードして、デバイスをそれらのプロファイルに割り当てられるようになります。

DEP トークンを作成する場合は、Apple DEP ポータルを使用します。 また、管理のためにデバイスを Intune に割り当てる場合にも DEP ポータルを使用します。

> [!NOTE]
> Azure に移行する前に Intune クラシック ポータルからトークンを削除すると、削除された Apple DEP トークンが Intune で復元される場合があります。 Azure Portal から DEP トークンを再び削除できます。

### <a name="step-1-download-the-intune-public-key-certificate-required-to-create-the-token"></a>手順 1. トークンを作成するために必要な Intune 公開キー証明書をダウンロードする

1. [Azure portal の Intune](https://aka.ms/intuneportal) で、**[デバイスの登録]** > **[Apple の登録]** > **[Enrollment Program トークン]** > **[追加]** の順に選択します。

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
**[Apple トークン]** ボックスで、証明書 (.pem) ファイルを参照し、**[開く]** を選択して、**[作成]** を選択します。 このプッシュ証明書を使用して、Intune はモバイル デバイスを登録し、登録したモバイル デバイスにポリシーを適用して iOS デバイスを管理できます。 Intune は、Apple と自動的に同期して、Enrollment Program アカウントを表示します。

## <a name="create-an-apple-enrollment-profile"></a>Apple 登録プロファイルの作成

これでトークンがインストールされました。DEP デバイスの登録プロファイルを作成することができます。 デバイス登録プロファイルで、デバイス グループに対して登録時に適用する設定を定義します。

1. Azure Portal の Intune で、**[デバイスの登録]** > **[Apple の登録]** > **[Enrollment Program トークン]** の順に選択します。
2. トークンを選択し、**[プロファイル]** を選択し、**[プロファイルの作成]** を選択します。

    ![プロファイルの作成のスクリーンショット。](./media/device-enrollment-program-enroll-ios/image04.png)

3. **[プロファイルの作成]** で、管理用にプロファイルの **[名前]** と **[説明]** を入力します。 ユーザーにはこれらの詳細は表示されません。 この **[名前]** フィールドを使用して、Azure Active Directory で動的グループを作成できます。 この登録プロファイルに対応するデバイスを割り当てるために enrollmentProfileName パラメーターを定義する場合はプロファイル名を使用します。 Azure Active Directory の動的グループの詳細については[こちら](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal#using-attributes-to-create-rules-for-device-objects)を参照してください。

    ![プロファイル名と説明。](./media/device-enrollment-program-enroll-ios/image05.png)

4. **[ユーザー アフィニティ]** で、このプロファイルに対応するデバイスを割り当て済みユーザーとともに登録する必要があるかどうかを選択します。
    - **[ユーザー アフィニティとともに登録する]** - このオプションは、ユーザーに属しているデバイスであって、かつアプリのインストールなどのサービスにポータル サイトを使用する必要があるデバイスの場合に選択します。 ADFS と登録プロファイルの使用によって、**[Apple セットアップ アシスタントの代わりにポータル サイトで認証します]** が **[いいえ]** に設定されている場合、[WS-Trust 1.3 Username/Mixed エンドポイント](https://technet.microsoft.com/library/adfs2-help-endpoints) ([詳細情報](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint)) が必要です。

    - **[ユーザー アフィニティなしで登録する]** - このオプションは、1 人のユーザーに関連付けられていないデバイスの場合に選択します。 このオプションは、ローカルのユーザー データにアクセスせずにタスクを実行するデバイスで使用します。 ポータル サイト アプリなどのアプリは動作しません。

5. **[ユーザー アフィニティとともに登録する]** を選択した場合は、Apple セットアップ アシスタントではなく、ポータル サイトでユーザーに認証を行わせるオプションがあります。

    ![ポータル サイトで認証します。](./media/device-enrollment-program-enroll-ios/authenticatewithcompanyportal.png)

    > [!NOTE]
    > 次のいずれかを実行する場合は、**[Apple セットアップ アシスタントの代わりにポータル サイトで認証します]** を **[はい]** に設定します。
    >    - 多要素認証の使用
    >    - 最初のサインイン時にパスワードの変更が必要なユーザーにプロンプトを表示する
    >    - 登録の間に有効期限が切れたパスワードのリセットをユーザーに求める
    >
    > Apple セットアップ アシスタントで認証を行っているときは、これらはサポートされません。

6. **[Apple セットアップ アシスタントの代わりにポータル サイトで認証します]** で **[はい]** を選択した場合、ユーザーが Apple ID を指定しなくても、Volume Purchase Program (VPP) トークンを使用して自動的に Intune ポータル サイトをデバイスにインストールできます。 VPP トークンを使用して Intune ポータル サイトをインストールするには、**[VPP によるポータル サイトのインストール]** でトークンを選択します。 トークンの期限が切れていないことと、ポータル サイト アプリの十分なデバイス ライセンスがあることを確認してください。 トークンの期限が切れているか、ライセンスが不足している場合、Intune は代わりに App Store ポータル サイトをインストールし、Apple ID の入力を求めます。

    ![[VPP によるポータル サイトのインストール] のスクリーンショット。](./media/device-enrollment-program-enroll-ios/install-cp-with-vpp.png)

7. **[VPP によるポータル サイトのインストール]** にトークンを選択した場合、セットアップ アシスタントの完了直後、シングル アプリ モードでデバイスをロックできます (具体的には、ポータル サイト アプリ)。 **[Run Company Portal in Single App Mode until authentication]\(認証されるまでシングル アプリ モードでポータル サイトを実行する\)** に **[はい]** を選択すると、このオプションが設定されます。 デバイスを使用するには、ポータル サイトを使用したサインインで最初に認証する必要があります。
    この機能は iOS 11.3.1 以降で最適に動作します。 以前のバージョンを使用すると、インストールに長い時間がかかる場合があります。

8. **[デバイス管理の設定]** を選択し、このプロファイルを使用するデバイスを監視するかどうかを選択します。

    ![[デバイス管理の設定] のスクリーンショット。](./media/device-enrollment-program-enroll-ios/devicemanagementsettingsblade.png)

    **[監視下]** デバイスでは、より多くの管理オプションを使用できるようになり、既定で [アクティベーション ロック] は無効になります。 Microsoft は、多数の iOS デバイスを展開する組織に対して特に、監視モードを有効にするメカニズムとして DPE の利用を推奨しています。

    デバイスが監視対象であることは次の 2 つの方法でユーザーに通知されます。

   - ロック画面に "この iPhone は Contoso によって管理されています" という内容のメッセージが表示されます。
   - **[設定]** > **[全般]** > **[情報]** 画面に、"この iPhone は監視されています" という内容のメッセージが表示されます。 Contoso はインターネット トラフィックを監視し、このデバイスの位置を特定できます。" と、

     > [!NOTE]
     > 監視なしで登録されているデバイスは、Apple Configurator でのみ監視対象にリセットすることができます。 この方法でデバイスをリセットするには、USB ケーブルを使用して iOS デバイスを Mac に接続する必要があります。 詳細については、[Apple Configurator ドキュメント](http://help.apple.com/configurator/mac/2.3)を参照してください。

9. このプロファイルを使用するデバイスの登録をロックする必要があるかどうかを選択します。 **[ロックされた登録]** を選択すると、**[設定]** メニューから管理プロファイルを削除する操作を許可する iOS 設定が無効になります。 デバイスの登録後は、デバイスをワイプしないと、この設定を変更することができません。 そのようなデバイスについては、**[監視下]** 管理モードを *[はい]* に設定する必要があります。 

10. このプロファイルを使用したデバイスを**コンピューターと同期**できるようにするかどうかを選択します。 **[証明書による Apple Configurator の許可]** を選択した場合は、**[Apple Configurator の証明書]** で証明書を選択する必要があります。

11. 前の手順で **[証明書による Apple Configurator の許可]** を選択した場合は、インポートする Apple Configurator の証明書を選択します。

12. **[OK]** を選びます。

13. **[セットアップ アシスタントのカスタマイズ]** を選択し、次のプロファイル設定を構成します: ![[セットアップ アシスタントのカスタマイズ]](./media/device-enrollment-program-enroll-ios/setupassistantcustom.png)。


    | 部門の設定 | 説明 |
    |---|---|
    | <strong>部門名</strong> | アクティブ化中にユーザーが <strong>[構成について]</strong> をタップすると表示されます。 |
    |    <strong>部署の電話番号</strong>     | アクティブ化中にユーザーが <strong>[ヘルプが必要ですか]</strong> ボタンをクリックすると表示されます。 |

  ユーザーがデバイスを設定するときに使用するセットアップ アシスタントのさまざまな画面の表示または非表示を選択できます。
  - **[非表示]** を選択した場合、セットアップ時に画面は表示されません。 その場合でも、デバイスを設定した後、ユーザーは **[設定]** メニューから機能を設定できます。
  - **[表示]** を選択した場合、セットアップ時に画面が表示されます。 ユーザーは、何も行わずに画面をスキップできる場合があります。 しかし、後でデバイスの **[設定]** メニューから機能を設定できます。 


    | セットアップ アシスタントの画面の設定 | **[表示]** を選択した場合の、セットアップ時のデバイスの動作... |
    |------------------------------------------|------------------------------------------|
    | <strong>パスコード</strong> | ユーザーにパスコードの入力を求めます。 デバイスがセキュリティで保護される場合や、他の何らかの方法 (デバイスを 1 つのアプリに制限するキオスク モードなど) でアクセスが制御されている場合を除き、パスコードは常に必須にしてください。 |
    | <strong>ロケーション サービス</strong> | ユーザーに場所の指定を求めます。 |
    | <strong>復元</strong> | **[アプリとデータ]** 画面が表示されます。 この画面では、ユーザーはデバイスを設定するときに iCloud Backup からデータを復元または転送できます。 |
    | <strong>iCloud と Apple ID</strong> | ユーザーは、自分の **Apple ID** でサインインして、**iCloud** を使用することができます。                         |
    | <strong>使用条件</strong> | ユーザーに Apple の使用条件への同意を求めます。 |
    | <strong>Touch ID</strong> | ユーザーに、デバイスの指紋識別を設定するオプションを表示します。 |
    | <strong>Apple Pay</strong> | ユーザーに、デバイスで Apple Pay を設定するオプションを表示します。 |
    | <strong>Zoom</strong> | ユーザーに、デバイスを設定するときに表示を拡大するオプションを表示します。 |
    | <strong>Siri</strong> | ユーザーに、Siri を設定するオプションを表示します。 |
    | <strong>診断データ</strong> | **[診断]** 画面をユーザーに表示します。 この画面では、ユーザーは Apple に診断データを送信できます。 |


14. **[OK]** を選びます。

15. プロファイルを保存するには、**[作成]** を選択します。

## <a name="sync-managed-devices"></a>マネージド デバイスを同期する
デバイスを管理するアクセス許可を Intune に割り当てたので、Intune と Apple を同期して、マネージド デバイスを Azure ポータルの Intune に表示できます。

1. Azure ポータルの Intune で、**[デバイスの登録]**>**[Apple の登録]**>**[Enrollment Program トークン]** の順に選択し、リスト内でトークンを選択し、**[デバイス]**>**[同期]** の順に選択します。![[Enrollment Program デバイス] ノードと [同期] リンクが選ばれているスクリーンショット。](./media/device-enrollment-program-enroll-ios/image06.png)

   許容される Enrollment Program トラフィックについての Apple の規約に準拠するため、Intune では次の制限が課せられます。
   - 完全な同期は 7 日に 1 回だけ実行できます。 完全な同期中に、Intune に接続された Apple MDM サーバーに割り当てられているシリアル番号の完全な最新の一覧を Intune がフェッチします。 DEP ポータルで Apple MDM サーバーからの割り当てを解除せずに Intune ポータルから Enrollment Program デバイスが削除されると、完全同期が実行されるまで Intune に再インポートされません。   
   - 同期は 24 時間ごとに自動的に実行されます。 **[同期]** ボタンをクリックして同期することもできます (15 分以内に 2 回以上は同期できません)。 すべての同期要求は、完了までに 15 分与えられます。 同期が完了するまで、**[同期]** ボタンは無効になっています。 この同期により、既存のデバイスの状態が更新され、Apple MDM サーバーに割り当てられている新しいデバイスがインポートされます。   


## <a name="assign-an-enrollment-profile-to-devices"></a>登録プロファイルをデバイスに割り当てる
登録する前に、Enrollment Program プロファイルをデバイスに割り当てる必要があります。

>[!NOTE]
>**[Apple Serial Numbers\(Apple シリアル番号\)]** ブレードでプロファイルにシリアル番号を割り当てることもできます。

1. Intune で、**[デバイスの登録]** > **[Apple の登録]** > **[Enrollment Program トークン]** の順に選択し、リスト内でトークンを選択します。
2. **[デバイス]** を選択し、リスト内でデバイスを選択し、**[プロファイルの割り当て]** を選択します。
3. **[プロファイルの割り当て]** の下でデバイス用のプロファイルを選択し、**[割り当て]** を選択します。

### <a name="assign-a-default-profile"></a>既定のプロファイルを割り当てる

特定のトークンを使用して登録するすべてのデバイスに適用される既定のプロファイルを選択することができます。

1. Intune で、**[デバイスの登録]** > **[Apple の登録]** > **[Enrollment Program トークン]** の順に選択し、リスト内でトークンを選択します。
2. **[既定のプロファイルの設定]** を選択し、ドロップダウン リストでプロファイルを選択し、**[保存]** を選択します。 このプロファイルは、トークンに登録されたすべてのデバイスに適用されます。

## <a name="distribute-devices"></a>デバイスを配布する
Apple と Intune の間の同期と管理を有効にし、DEP デバイスを登録できるようにプロファイルを割り当てました。 ユーザーにデバイスを配布できるようになりました。 ユーザー アフィニティがあるデバイスでは、各ユーザーに Intune ライセンスを割り当てる必要があります。 ユーザー アフィニティがないデバイスでは、デバイスのライセンスが必要です。 デバイスがワイプされるまで、アクティブ化されたデバイスは登録プロファイルを適用できません。

「[Intune で iOS デバイスを Device Enrollment Program に登録する](/intune-user-help/enroll-your-device-dep-ios)」を参照してください。

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
