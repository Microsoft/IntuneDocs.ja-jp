---
title: デバイス登録プログラムを使用して iOS デバイスを登録する
titlesuffix: Microsoft Intune
description: Device Enrollment Program を使用して会社所有の iOS デバイスを登録する方法を説明します。"
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/08/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 7981a9c0-168e-4c54-9afd-ac51e895042c
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1dd9fff04ff479844910328d274d6cc4cbe2c14a
ms.sourcegitcommit: 401cedcd7acc6cb3a6f18d4679bdadb0e0cdf443
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="automatically-enroll-ios-devices-by-using-apples-device-enrollment-program"></a>Apple の Device Enrollment Program を使用して iOS デバイスを自動登録する

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

> [!NOTE]
> ### <a name="temporary-user-interface-differences"></a>一時的なユーザー インターフェイスの違い
>
>このページで説明する機能のユーザー インターフェイスは、現在更新中です。 これらの更新は、4 月の終わりまでにすべてのユーザー アカウントにロールアウトされます。
>
>**[デバイス登録]** ページが次の図のようになっている場合、アカウントは新しいユーザー インターフェイスにまだ更新されていません。こちらのヘルプ ページを使用できます。
>
>![以前の Intune のユーザー インターフェイス](./media/appleenroll-oldui.png)
>
>**[デバイス登録]** ページが次の図のようになっている場合、ユーザー インターフェイスは更新済みです。  [こちらのヘルプ ページ](device-enrollment-program-enroll-ios-newui.md)に移動してください。
>
>![新しい Intune のユーザー インターフェイス](./media/appleenroll-newui.png)

このトピックは、Apple の [Device Enrollment Program (DEP)](https://deploy.apple.com) で購入したデバイスの iOS デバイス登録を有効にする場合に役立ちます。 自動で多数のデバイスの DEP 登録を行うことができます。 iPhone や iPad などのデバイスを直接ユーザーに配信できます。 ユーザーがデバイスの電源をオンにすると、セットアップ アシスタントが構成済み設定で実行され、デバイスが管理対象として登録されます。

DEP 登録を有効にするには、Intune ポータルと Apple DEP ポータルの両方を使います。 管理するために Intune にデバイスを割り当てられるように、シリアル番号のリストまたは注文番号が必要になります。 登録時にデバイスに適用された設定を含む DEP 登録プロファイルを作成します。

DEP 登録は[デバイス登録マネージャー](device-enrollment-manager-enroll.md)では動作しません。 また、macOS では現在、DEP はサポートされていません。

## <a name="what-is-supervised-mode"></a>監視モードとは何か。
Apple は iOS 5 で監視モードを導入しました。 監視モードの iOS デバイスは、さらに細かく制御できます。 そのため、企業所有のデバイスで特に役立ちます。 Intune は Apple Device Enrollment Program (DEP) の一部としてデバイスの監視モードを設定できます。

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

> [!NOTE]
> 多要素認証 (MFA) は、ユーザー アフィニティの DEP 登録セットアップ中は動作しません。 登録後、MFA はデバイスで期待どおりに動作します。 デバイスでは、最初のサインイン時にパスワードの変更が必要なユーザーにプロンプトを表示することができません。 さらに、パスワードの有効期限が切れているユーザーには、登録時にパスワードのリセットは求められません。 ユーザーは別のデバイスを使用してパスワードをリセットする必要があります。

## <a name="get-the-apple-dep-token"></a>Apple DEP トークンを取得する

DEP に iOS デバイスを登録するには、Apple の DEP トークン (.p7m) ファイルが必要です。 このトークンにより、Intune は企業所有の DEP デバイスに関する情報を同期できるようになります。 また、Intune は Apple に登録プロファイルをアップロードして、デバイスをそれらのプロファイルに割り当てられるようになります。

DEP トークンを作成する場合は、Apple DEP ポータルを使用します。 また、管理のためにデバイスを Intune に割り当てる場合にも DEP ポータルを使用します。

> [!NOTE]
> Azure に移行する前に Intune クラシック ポータルからトークンを削除すると、削除された Apple DEP トークンが Intune で復元される場合があります。 Azure Portal から DEP トークンを再び削除できます。 Azure Portal から DEP トークンを再び削除できます。

**手順 1: Apple DEP トークンを作成するために必要な Intune 公開キー証明書をダウンロードします。**<br>

1. [Azure Portal の Intune](https://aka.ms/intuneportal) で、**[デバイスの登録]** > **[Apple の登録]** > **[Enrollment Program トークン]** の順に選びます。

   ![[Apple 証明書] ワークスペースの [Enrollment Program トークン] ウィンドウ](./media/enrollment-program-token-add.png)

2. **[公開キーをダウンロードします]** を選択し、暗号化キー (.pem) ファイルをダウンロードしてローカルに保存します。 .pem ファイルは、Apple Device Enrollment Program ポータルから信頼関係証明書を要求するために使用します。

   ![公開キーをダウンロードするための [Apple 証明書] ワークスペースの [Enrollment Program トークン] ウィンドウ](./media/enrollment-program-token-download.png)

**手順 2:Apple DEP トークンを作成し、ダウンロードします。**<br>
1. **[Apple Device Enrollment Program を使用してトークンを作成します]** を選択して Apple の Deployment Program ポータルを開き、会社の Apple ID でサインインします。 この Apple ID を使って、DEP トークンを更新できます。
2.  Apple の [Deployment Programs ポータル](https://deploy.apple.com) で、**[Device Enrollment Program]** の **[開始]** を選択します。

3. **[Manage Servers\(サーバーの管理\)]** ページで、**[Add MDM Server\(MDM サーバーの追加\)]** を選びます。
4. **MDM サーバー名**を入力し、**[Next]** (次へ) をクリックします。 サーバー名は、自分がモバイル デバイス管理 (MDM) サーバーを識別できるようにするための名前です。 Microsoft Intune サーバーの名前または URL ではありません。

   ![DEP の MDM サーバー名を追加して [次へ] をクリック](./media/enrollment-program-token-add-server.png)

5. **[Add &lt;ServerName&gt;\(<サーバー名> の追加\)]** ダイアログ ボックスが開き、**[Upload Your Public Key\(公開キーをアップロードする\)]** と表示されます。 **[Choose File]** (ファイルを選択) をクリックして .pem ファイルをアップロードし、**[Next]** (次へ) を選択します。  

6. **[Deployment Programs] (展開プログラム)** &gt; **[Device Enrollment Program]** &gt; **[Manage Devices] (デバイスの管理)** の順に移動します。
7. **[Choose Devices By\(デバイスの選択方法\)]** で、デバイスを識別する方法を指定します。
    - **Serial Number\(シリアル番号\)**
    - **Order Number\(注文番号\)**
    - **Upload CSV File\(CSV ファイルのアップロード\)**

   ![シリアル番号でデバイスを選択するように指定し、アクションの選択でサーバーへの割り当てを設定し、サーバー名を選択](./media/enrollment-program-token-specify-serial.png)

8. **[アクションの選択]** で **[Assign to Server]\(サーバーに割り当てる\)** を選択し、Microsoft Intune に指定した **ServerName** を選択して、&lt;[OK]&gt; を選択します。 指定したデバイスが管理用に Intune サーバーに割り当てられて、**[Assignment Complete\(割り当て完了\)]** と表示されます。

   Apple ポータルで、**[Deployment Programs\(配備プログラム\)]** &gt; **[Device Enrollment Program\(Device Enrollment Program\)]** &gt; **[View Assignment History\(割り当て履歴の表示\)]** の順に移動して、デバイスとその MDM サーバーの割り当てのリストを表示します。

**手順 3:Enrollment Program トークンの作成に使った Apple ID を入力します。**<br>Azure ポータルの Intune で、後で参照するための Apple ID を指定します。

![Enrollment Program トークンの作成に使った Apple ID の指定と、Enrollment Program トークンの参照](./media/enrollment-program-token-apple-id.png)

**手順 4:アップロードする Enrollment Program トークンを参照します。**<br>
証明書 (.pem) ファイルに移動し、**[開く]** を選択して、**[アップロード]** を選択します。 このプッシュ証明書を使用して、Intune はモバイル デバイスを登録し、登録したモバイル デバイスにポリシーを適用して iOS デバイスを管理できます。 Intune は、Apple と自動的に同期して、Enrollment Program アカウントを表示します。

## <a name="create-an-apple-enrollment-profile"></a>Apple 登録プロファイルの作成

これでトークンがインストールされました。DEP デバイスの登録プロファイルを作成することができます。 デバイス登録プロファイルで、デバイス グループに対して登録時に適用する設定を定義します。

1. [Azure Portal の Intune](https://aka.ms/intuneportal) で、**[デバイスの登録]** > **[Apple の登録]** の順に選択します。
2. **[Apple の Enrollment Program]** で、**[Enrollment Program プロファイル]** > **[作成]** の順に選択します。
3. **[登録プロファイルの作成]** で、管理用にプロファイルの **[名前]** と **[説明]** を入力します。 ユーザーにはこれらの詳細は表示されません。 この **[名前]** フィールドを使用して、Azure Active Directory で動的グループを作成できます。 この登録プロファイルに対応するデバイスを割り当てるために enrollmentProfileName パラメーターを定義する場合はプロファイル名を使用します。 Azure Active Directory の動的グループの詳細については[こちら](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal#using-attributes-to-create-rules-for-device-objects)を参照してください。

   **[ユーザー アフィニティ]** で、このプロファイルに対応するデバイスを割り当て済みユーザーとともに登録するかどうかを選択します。

   - **[ユーザー アフィニティとともに登録する]** - ユーザーに属していて、アプリのインストールなどのサービスにポータル サイトを使用する必要があるデバイスの場合に選択します。 ユーザー アフィニティには [WS-Trust 1.3 Username/Mixed エンドポイント](https://technet.microsoft.com/library/adfs2-help-endpoints)が必要です。 [詳細については、ここをクリック](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint)してください。

   - **[ユーザー アフィニティなしで登録する]** - 1 人のユーザーに関連付けられていないデバイスの場合に選択します。 ローカルのユーザー データにアクセスせずにタスクを実行するデバイスで使用します。 ポータル サイト アプリなどのアプリは動作しません。

4. **[デバイス管理の設定]** を選択し、次のプロファイル設定を構成します。

   ![管理モードの選択](./media/enrollment-program-profile-mode.png)
   - **[監督下]** - より多くの管理オプションが使用可能な管理モードです。既定でアクティベーション ロックは無効になります。 このチェック ボックスをオフのままにすると、管理機能が制限されます。 Microsoft は、多数の iOS デバイスを展開する組織に対して特に、監視モードを有効にするメカニズムとして DPE の利用を推奨しています。

   > [!NOTE]
   > デバイスの登録後、Intune を利用してデバイスの監視モードを設定することはできません。 登録後に監視モードを有効にする唯一の方法は、USB ケーブルで iOS デバイスを Mac に接続し、Apple Configurator を使用することです。 デバイスがリセットされ、監視モードで構成されます。 詳細については、[Apple Configurator ドキュメント](http://help.apple.com/configurator/mac/2.3)を参照してください。監視対象となったデバイスのロック画面には、"この iPhone は Contoso が管理しています" と表示されます。 また、"この iPhone は監視されています。 Contoso はインターネット トラフィックを監視し、このデバイスの位置を特定できます。" と、 **[設定]**、**[全般]**、**[情報]** の順に選択すると表示されます。

   - **[ロックされた登録]** - ([管理モード] を [監督下] にする必要があります) 管理プロファイルの削除を許可する iOS 設定を無効にします。 このチェック ボックスをオフのままにすると、[設定] メニューから管理プロファイルを削除できます。 デバイスの登録後は、デバイスを出荷時の設定にリセットしないと、この設定を変更することができません。

   - **[有効な Shared iPad]** - Apple の Device Enrollment Program は共有の iPad をサポートしていません。

   - **[ペアリングの許可]** - iOS デバイスをコンピューターと同期できるかどうかを指定します。 **[証明書による Apple Configurator の許可]** を選択した場合は、**[Apple Configurator の証明書]** で証明書を選択する必要があります。

   - **[Apple Configurator の証明書]** - **[ペアリングの許可]** で **[証明書による Apple Configurator の許可]** を選択した場合は、インポートする Apple Configurator の証明書を選択します。

   **[保存]** を選びます。

5. **[セットアップ アシスタントの設定]** を選択し、次のプロファイル設定を構成します。

   ![新しい Enrollment Program プロファイルで使用可能な設定が選択されている構成設定](./media/enrollment-program-profile-settings.png)
   - **[部署名]** - アクティブ化中にユーザーが **[About Configuration (構成について)]** をタップすると表示されます。

   - **[部署の電話番号]** - アクティブ化中にユーザーが **[ヘルプが必要ですか]** ボタンをクリックすると表示されます。
     - **セットアップ アシスタントのオプション** - これらの省略可能な設定は、後で iOS の **[設定]** メニューで設定できます。
        - **パスコード**
        - **ロケーション サービス**
        - **復元**
        - **Apple ID**
        - **使用条件**
        - **Touch ID**
        - **Apple Pay**
        - **Zoom**
        - **Siri**
        - **診断データ**

     **[保存]** を選びます。

>[!NOTE]
>iOS 11 以降では、iCloud バックアップから復元できるようにする場合、セットアップ アシスタントのオプションで "復元" と "Apple ID" の両方を表示する必要があります。

6. プロファイルの設定を保存するには、**[登録プロファイルの作成]** ブレードで **[作成]** を選択します。 登録プロファイルが、[Apple Enrollment Program 登録プロファイル] の一覧に表示されます。

## <a name="sync-managed-devices"></a>管理対象デバイスを同期する
デバイスを管理するアクセス許可を Intune に割り当てたので、Intune と Apple を同期して、管理対象デバイスを Azure ポータルの Intune に表示できます。

1. [Azure Portal の Intune](https://aka.ms/intuneportal) で、**[デバイスの登録]** > **[Apple の登録]** > **[Enrollment Program デバイス]** > **[同期]** の順に選択します。進行状況バーには、もう一度同期が要求されるまでの待ち時間が表示されます。

   ![[Enrollment Program デバイス] ノードと [同期] リンクの選択](./media/enrollment-program-device-sync.png)

2. **[同期]** ブレードで、**[同期を要求]** を選択します。進行状況バーには、もう一度同期が要求されるまでの待ち時間が表示されます。

   ![[同期を要求] リンクが選ばれている [同期] ブレード](./media/enrollment-program-device-request-sync.png)

   許容される Enrollment Program トラフィックについての Apple の規約に準拠するため、Intune では次の制限が課せられます。
     -  完全な同期は 7 日に 1 回だけ実行できます。 Intune は、完全な同期中に、Intune に割り当てられているすべての Apple シリアル番号を更新します。 前回の完全同期の 7 日以内に完全同期が試みられると、Intune は Intune にまだ一覧表示されていないシリアル番号のみを更新します。
     -  すべての同期要求は、完了までに 15 分与えられます。 この時間中または要求が成功するまで、**[同期]** ボタンは無効にされます。
     - Intune は、24 時間ごとに新規のデバイスと削除されたデバイスを Apple と同期します。

3. [Enrollment Program デバイス] ワークスペースで、**[更新]** を選んでデバイスを表示します。

## <a name="assign-an-enrollment-profile-to-devices"></a>登録プロファイルをデバイスに割り当てる
登録する前に、Enrollment Program プロファイルをデバイスに割り当てる必要があります。

>[!NOTE]
>**[Apple Serial Numbers\(Apple シリアル番号\)]** ブレードでプロファイルにシリアル番号を割り当てることもできます。

1. [Azure Portal の Intune](https://aka.ms/intuneportal) で **[デバイスの登録]** > **[Apple の登録]** の順に選択し、**[Enrollment Program プロファイル]** を選択します。
2. **[Enrollment Program プロファイル]** の一覧から、デバイスに割り当てるプロファイルを選択し、**[デバイスの割り当て]** を選択します。

   ![[割り当て] が選択された [デバイスの割り当て]](./media/enrollment-program-device-assign.png)

3. **[割り当て]** を選択し、このプロファイルを割り当てるデバイスを選択します。 フィルターを適用して使用可能なデバイスを表示できます。
   - **未割り当て**
   - **任意**
   - **&lt;プロファイル名&gt;**
4. 割り当てるデバイスを選択します。 列の上のチェック ボックスで最大 1,000 のデバイスを選び、**[割り当て]** をクリックします。 1,000 を超えるデバイスを登録するには、すべてのデバイスに登録プロファイルを割り当てるまで割り当て手順を繰り返します。

   ![Intune で Enrollment Program プロファイルを割り当てるための [割り当て] ボタン](media/dep-profile-assignment.png)

## <a name="distribute-devices"></a>デバイスを配布する
Apple と Intune の間の同期と管理を有効にし、DEP デバイスを登録できるようにプロファイルを割り当てました。 ユーザーにデバイスを配布できるようになりました。 ユーザー アフィニティがあるデバイスでは、各ユーザーに Intune ライセンスを割り当てる必要があります。 ユーザー アフィニティがないデバイスでは、デバイスのライセンスが必要です。 デバイスが出荷時の設定にリセットされるまで、アクティブ化されたデバイスは登録プロファイルを適用できません。

「[Intune で iOS デバイスを Device Enrollment Program に登録する](/intune-user-help/enroll-your-device-dep-ios)」を参照してください。
