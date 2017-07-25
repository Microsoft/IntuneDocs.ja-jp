---
title: "iOS デバイスの登録 - Device Enrollment Program"
titleSuffix: Intune on Azure
description: "Device Enrollment Program を使用して会社所有の iOS デバイスを登録する方法を説明します。\""
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 07/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7981a9c0-168e-4c54-9afd-ac51e895042c
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 654a19dd6f1e5f4fd2bda771b0df95b87944db75
ms.sourcegitcommit: 2a6ad3c233d15a9fb441362105f64b2bdd550c34
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/13/2017
---
# <a name="set-up-ios-device-enrollment-with-device-enrollment-program"></a>Device Enrollment Program を使用して iOS デバイスの登録をセットアップする

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

このトピックでは、IT 管理者が Apple の [Device Enrollment Program (DEP)](https://deploy.apple.com) で購入したデバイスの iOS デバイス登録を有効にする方法について説明します。 Microsoft Intune は、DEP で購入されたデバイスに、登録プロファイルを "無線" で展開できます。 管理者は、管理された各デバイスに触れる必要はありません。 DEP プロファイルには、セットアップ アシスタント オプションなどの、登録時にデバイスに適用される管理設定が含まれています。

DEP 登録を有効にするには、Intune ポータルと Apple DEP ポータルの両方を使います。 Apple ポータルで管理するために Intune にデバイスを割り当てることができるよう、ID のリストまたは注文番号も必要になります。

>[!NOTE]
>DEP 登録は、[デバイス登録マネージャー](device-enrollment-manager-enroll.md)と同時に使うことはできません。

**Apple からの Enrollment Program を有効にする手順**
1. [Apple DEP トークンを取得し、デバイスを割り当てる](#get-the-apple-dep-token)
2. [登録プロファイルの作成](#create-an-apple-enrollment-profile)
3. [DEP 管理対象デバイスを同期する](#sync-managed-device)
4. [デバイスに DEP プロファイルを割り当てる](#assign-an-enrollment-profile-to-devices)
5. [デバイスをユーザーに配布する](#end-user-experience-with-managed-devices)

## <a name="get-the-apple-dep-token"></a>Apple DEP トークンを取得する

DEP に会社所有の iOS デバイスを登録するには、Apple の Device Enrollment Program (DEP) トークン (.p7m) ファイルが必要です。 このトークンにより、Intune は企業所有の DEP 参加デバイスに関する情報を同期できるようになります。 また、Intune は Apple への登録プロファイルのアップロードを実行して、デバイスをそれらのプロファイルに割り当てられるようになります。

> [!NOTE]
> Azure に移行する前にクラシックの Intune コンソールからトークンを削除すると、Intune で削除された Apple DEP トークンが復元される場合があります。 Azure Portal から DEP トークンを再び削除できます。 Azure Portal から DEP トークンを再び削除できます。

**必要条件**
- [Apple MDM プッシュ証明書](apple-mdm-push-certificate-get.md)
- [Apple の Device Enrollment Program](http://deploy.apple.com) にサインアップする

**手順 1: Apple DEP トークンを作成するために必要な Intune 公開キー証明書をダウンロードします。**<br>
1. Intune ポータルで、**[デバイスの登録]**、**[Apple の登録]**、**[Enrollment Program トークン]** の順に選びます。

  ![[Apple 証明書] ワークスペースの [Enrollment Program トークン] のスクリーンショット。](./media/enrollment-program-token-add.png)

2. **[Download your public key (公開キーをダウンロードする)]** を選択して、暗号化キー (.pem) ファイルをダウンロードし、ローカルに保存します。 .pem ファイルは、Apple Device Enrollment Program ポータルから信頼関係証明書を要求するために使用します。

  ![公開キーをダウンロードするための [Apple 証明書] ワークスペースの [Enrollment Program トークン] のスクリーンショット。](./media/enrollment-program-token-download.png)

**手順 2:Apple DEP トークンを作成し、ダウンロードします。**<br>
1. **[Apple Device Enrollment Program を使用してトークンを作成します]** を選んで Apple の Deployment Program ポータルを開き、会社の Apple ID でサインインします。 この Apple ID を使って、DEP トークンを更新できます。

  ![[Apple 証明書] ワークスペースの [Enrollment Program トークン] のスクリーンショット。](./media/enrollment-program-token-create.png)

  ![公開キーをダウンロードするための [Apple 証明書] ワークスペースの [Enrollment Program トークン] のスクリーンショット。](./media/enrollment-program-token-sign.png)
2.  Apple の [Deployment Programs ポータル](https://deploy.apple.com) で、**[Device Enrollment Program]** の **[Get Started\(開始\)]** を選びます。

   ![[Device Enrollment Program] の [Get Started\(開始\)] をクリックした Enrollment Program のスクリーンショット。](./media/enrollment-program-token-started.png)

3. **[Manage Servers\(サーバーの管理\)]** ページで、**[Add MDM Server\(MDM サーバーの追加\)]** を選びます。
4. **MDM サーバー名**を入力し、**[Next]** (次へ) をクリックします。 サーバー名は、自分がモバイル デバイス管理 (MDM) サーバーを識別できるようにするための名前です。 Microsoft Intune サーバーの名前または URL ではありません。

   ![DEP の MDM サーバー名を追加して [次へ] をクリックしたスクリーンショット。](./media/enrollment-program-token-add-server.png)

5. **[Add &lt;ServerName&gt;\(<サーバー名> の追加\)]** ダイアログ ボックスが開き、**[Upload Your Public Key\(公開キーをアップロードする\)]** と表示されます。 **[Choose File]** (ファイルを選択) をクリックして .pem ファイルをアップロードし、**[Next]** (次へ) を選択します。

   ![公開キー ファイル ボタンを選んで [次へ] をクリックしたスクリーンショット。](./media/enrollment-program-token-choose-file.png)
6.  **[Add &lt;ServerName&gt;]** (<サーバー名> の追加) ダイアログ ボックスに、**[Your Server Token]** (サーバー トークン) リンクが表示されます。 サーバー トークン (.p7m) ファイルをコンピューターにダウンロードした後、**[Done]** (完了) を選択します。
   ![公開キー ファイル ボタンを選んで [次へ] をクリックしたスクリーンショット。](./media/enrollment-program-token-your-token.png)
7. **[Deployment Programs](展開プログラム)** &gt; **[Device Enrollment Program]** &gt; **[Manage Devices](デバイスの管理)** の順に移動します。
8. **[Choose Devices By\(デバイスの選択方法\)]** で、デバイスを識別する方法を指定します。
    - **Serial Number\(シリアル番号\)**
    - **Order Number\(注文番号\)**
    - **Upload CSV File\(CSV ファイルのアップロード\)**

   ![シリアル番号でデバイスを選択するように指定し、アクションの選択でサーバーへの割り当てを設定し、サーバー名を選択したスクリーンショット。](./media/enrollment-program-token-specify-serial.png)

9. **[Choose Action\(アクションの選択\)]** で **[Assign to Server\(サーバーへの割り当て\)]** を選び、Microsoft Intune に対して指定した &lt;サーバー名&gt; を選んで、**[OK]** を選びます。 指定したデバイスが管理用に Intune サーバーに割り当てられて、**[Assignment Complete\(割り当て完了\)]** と表示されます。

   Apple ポータルで、**[Deployment Programs\(配備プログラム\)]** &gt; **[Device Enrollment Program\(Device Enrollment Program\)]** &gt; **[View Assignment History\(割り当て履歴の表示\)]** の順に移動して、デバイスとその MDM サーバーの割り当てのリストを表示します。

**手順 3:Enrollment Program トークンの作成に使った Apple ID を入力します。**<br>Intune ポータルで、後で参照するための Apple ID を指定します。 すべてのデバイスを再登録しなくて済むように、Enrollment Program トークンを更新するときは、この ID を使います。

![Enrollment Program トークンの作成に使った Apple ID の指定と、Enrollment Program トークンの参照のスクリーンショット。](./media/enrollment-program-token-apple-id.png)

**手順 4:アップロードする Enrollment Program トークンを参照します。**<br>
証明書 (.pem) ファイルに移動し、**[開く]** を選択して、**[アップロード]** を選択します。 このプッシュ証明書を使用して、Intune はモバイル デバイスを登録し、登録したモバイル デバイスにポリシーを適用して iOS デバイスを管理できます。 Intune は、Apple と自動的に同期して、Enrollment Program アカウントを表示します。

## <a name="create-an-apple-enrollment-profile"></a>Apple 登録プロファイルの作成

デバイス登録プロファイルで、デバイス グループに対して登録時に適用する設定を定義します。

1. Intune ポータルで **[デバイスの登録]** を選択し、**[Apple の登録]** を選択します。
2. **[Apple の Enrollment Program]** で **[Enrollment Program プロファイル]** を選び、**[Enrollment Program プロファイル]** ブレードで **[作成]** を選びます。

  ![新しい Enrollment Program プロファイルを作成するための作成リンクを選んだスクリーンショット。](./media/enrollment-program-profile-create.png)

3. **[登録プロファイルの作成]** ブレードで、管理用にプロファイルの **[名前]** と **[説明]** を入力します。 ユーザーにはこれらの詳細は表示されません。

  ![新しい Enrollment Program プロファイルの名前と説明を指定し、[ユーザー アフィニティとともに登録する] を選んだスクリーンショット。](./media/enrollment-program-profile-name.png)
**[ユーザー アフィニティ]** で、このプロファイルに対応するデバイスをユーザー アフィニティとともに登録するかどうかを選択します。

 - **[ユーザー アフィニティとともに登録する]** - ユーザーは、セットアップ時にデバイスと関連付けられた後、会社のデータやメールへのアクセスを許可されます。 ユーザーに属していて、アプリのインストールなどのサービスにポータル サイトを使用する必要があるデバイスの、**ユーザー アフィニティ**を選択します。

 > [!NOTE]
 > 多要素認証 (MFA) は、ユーザー アフィニティを使って Enrollment Program で管理されたデバイスに登録している間は動作しません。 DEP デバイスに登録が完了すると、MFA は期待どおりに動作します。 最初にサインインするときにパスワードを変更する必要がある新しいユーザーには、デバイスの登録時にプロンプトを表示することはできません。 さらに、パスワードの有効期限が切れているユーザーには、登録時にパスワードのリセットは求められません。このユーザーは別のデバイスからパスワードをリセットする必要があります。

 >[!NOTE]
 >ユーザー アフィニティが設定された Enrollment Program 管理デバイスでユーザー トークンを要求するには、[WS-Trust 1.3 Username/Mixed エンドポイント](https://technet.microsoft.com/library/adfs2-help-endpoints)を有効にする必要があります。 WS-Trust 1.3 について詳しくは、[こちら](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint)をご覧ください。

 - **[ユーザー アフィニティなしで登録する]** - デバイスは、ユーザーと関連付けられません。 このデバイス関連付け情報を使用すると、ローカルのユーザー データにアクセスしなくてもタスクを実行できます。 ユーザー アフィリエーションが必要なアプリ (基幹業務アプリのインストールに使用されるポータル サイト アプリを含む) は機能しません。

4. **[デバイス管理の設定]** を選択し、次のプロファイル設定を構成します。

  ![管理モードが選択されているスクリーン ショット。 デバイスには [監督下]、[ロックされた登録]、[ペアリングの許可] ([すべて拒否] に設定されている) の設定があります。 [Apple Configurator の証明書] は、新しい Enrollment Program プロファイルでは淡色表示されています。](./media/enrollment-program-profile-mode.png)
    - **[監督下]** - より多くの管理オプションが使用可能な管理モードです。既定でアクティベーション ロックは無効になります。 このチェック ボックスをオフのままにすると、管理機能が制限されます。

    - **[ロックされた登録]** - ([管理モード] を [監督下] にする必要があります) 管理プロファイルの削除を許可する iOS 設定を無効にします。 このチェック ボックスをオフのままにすると、[設定] メニューから管理プロファイルを削除できます。 デバイスの登録後は、デバイスを出荷時の設定にリセットしないと、この設定を変更することができません。

    - **[ペアリングの許可]** - iOS デバイスをコンピューターと同期できるかどうかを指定します。 **[証明書による Apple Configurator の許可]** を選択した場合は、**[Apple Configurator の証明書]** で証明書を選択する必要があります。

    - **[Apple Configurator の証明書]** - **[ペアリングの許可]** で **[証明書による Apple Configurator の許可]** を選択した場合は、インポートする Apple Configurator の証明書を選択します。

  **[保存]** を選びます。

5. **[セットアップ アシスタントの設定]** を選択し、次のプロファイル設定を構成します。

  ![新しい Enrollment Program プロファイルで使用可能な設定が選択されている構成設定のスクリーンショット。](./media/enrollment-program-profile-settings.png)
    - **[部署名]** - アクティブ化中にユーザーが **[About Configuration (構成について)]** をタップすると表示されます。

    - **[部署の電話番号]** - アクティブ化中にユーザーが **[ヘルプが必要ですか]** ボタンをクリックすると表示されます。
    - **セットアップ アシスタントのオプション** - これらの省略可能な設定は、後で iOS の **[設定]** メニューで設定できます。
        - **パスコード** - アクティブ化時にパスコードの入力を求めます。 デバイスがセキュリティで保護される場合や、他の何らかの方法でアクセスが制御されている場合を除き、パスコードは常に必須にしてください。 たとえば、キオスク モードでは、デバイスのアプリは 1 つに制限されます。
        - **位置情報サービス** - 有効にすると、アクティブ化時に、セットアップ アシスタントによってサービスがプロンプトされます
        - **復元** - 有効にすると、アクティブ化時に、セットアップ アシスタントによって iCloud バックアップがプロンプトされます
        - **[Apple ID]** - 有効にすると、Intune で ID を指定せずにアプリをインストールしようとするときに iOS によって Apple ID の入力を求められます。 Intune でインストールされるアプリを含め、iOS App Store アプリをダウンロードするには Apple ID が必要です。
        - **使用条件** - 有効にすると、アクティブ化時に、セットアップ アシスタントによって Apple の使用条件に同意するように求められます
        - **タッチ ID** - 有効にすると、アクティブ化時に、セットアップ アシスタントによってこのサービスがプロンプトされます
        - **Apple Pay** - 有効にすると、アクティブ化時に、セットアップ アシスタントによってこのサービスがプロンプトされます
        - **ズーム** - 有効にすると、アクティブ化時に、セットアップ アシスタントによってこのサービスがプロンプトされます
        - **Siri** - 有効にすると、アクティブ化時に、セットアップ アシスタントによってこのサービスがプロンプトされます
        - **[診断データ]** - 有効にすると、アクティブ化時に、セットアップ アシスタントによってこのサービスがプロンプトされます

    **[保存]** を選びます。
9. プロファイルの設定を保存するには、**[登録プロファイルの作成]** ブレードで **[作成]** を選択します。 登録プロファイルが、[Apple Enrollment Program 登録プロファイル] の一覧に表示されます。

## <a name="sync-managed-devices"></a>管理対象デバイスを同期する
デバイスを管理するアクセス許可を Intune に割り当てたので、Intune と Apple を同期して、管理対象デバイスを Intune ポータルに表示できます。

1. Intune ポータルで **[デバイスの登録]** &gt; **[Apple の登録]** &gt; **[Enrollment Program デバイス]** の順に選びます。
2. **[Enrollment Program デバイス]** で、**[同期]** を選択します。 **[同期]** ブレードが表示されます。

  ![[Enrollment Program デバイス] ノードと [同期] リンクが選ばれているスクリーンショット。](./media/enrollment-program-device-sync.png)
3. **[同期]**ブレードで、**[同期を要求]** を選択します。 進行状況バーには、もう一度同期が要求されるまでの待ち時間が表示されます。

  ![[同期を要求] リンクが選ばれている [同期] ブレードのスクリーンショット。](./media/enrollment-program-device-request-sync.png)

  許容される Enrollment Program トラフィックについての Apple の規約に準拠するため、Intune では次の制限が課せられます。
     -  完全な同期は 7 日に 1 回だけ実行できます。 Intune は、完全な同期中に、Intune に割り当てられているすべての Apple シリアル番号を更新します。 前回の完全同期の 7 日以内に完全同期が試みられると、Intune は Intune にまだ一覧表示されていないシリアル番号のみを更新します。
     -  すべての同期要求は、完了までに 15 分与えられます。 この時間中または要求が成功するまで、**[同期]** ボタンは無効にされます。
     - Intune は、24 時間ごとに新規のデバイスと削除されたデバイスを Apple と同期します。
     
4. [Enrollment Program デバイス] ワークスペースで、**[更新]** を選んでデバイスを表示します。

## <a name="assign-an-enrollment-profile-to-devices"></a>登録プロファイルをデバイスに割り当てる
登録する前に、Enrollment Program プロファイルをデバイスに割り当てる必要があります。

>[!NOTE]
>**[Apple Serial Numbers\(Apple シリアル番号\)]** ブレードでプロファイルにシリアル番号を割り当てることもできます。

1. Intune ポータルで **[デバイスの登録]** > **[Apple の登録]** の順に選択し、**[Enrollment Program プロファイル]** を選択します。
2. **[Enrollment Program プロファイル]** の一覧からデバイスに割り当てるプロファイルを選び、**[デバイスの割り当て]** を選びます。

 ![[同期を要求] リンクが選ばれている [同期] ブレードのスクリーンショット。](./media/enrollment-program-device-assign.png)

3. **[割り当て]** を選び、このプロファイルを割り当てるデバイスを選びます。 フィルターを適用して使用可能なデバイスを表示できます。
  - **未割り当て**
  - **任意**
  - **&lt;プロファイル名&gt;**
4. 割り当てるデバイスを選択します。 列の上のチェック ボックスで最大 1,000 のデバイスを選び、**[割り当て]** をクリックします。 1,000 を超えるデバイスを登録するには、すべてのデバイスに登録プロファイルを割り当てるまで割り当て手順を繰り返します。

  ![Intune ポータルで Enrollment Program プロファイルを割り当てるための [割り当て] ボタンのスクリーンショット](media/dep-profile-assignment.png)

## <a name="end-user-experience-with-managed-devices"></a>管理対象デバイスでのエンド ユーザー エクスペリエンス

ユーザーにデバイスを配布できるようになりました。 ユーザー アフィニティがあるデバイスでは、各ユーザーに Intune ライセンスを割り当てる必要があります。 デバイスが出荷時の設定にリセットされるまで、アクティブ化されたデバイスは登録プロファイルを適用できません。 Enrollment Program で管理された iOS デバイスを有効にするとき、ユーザーのデバイスには次のオプションが表示されます。  

1. **[Set Up iOS device\(iOS デバイスの設定\)]** - 次のオプションから選択できます。
  - **Set Up as New device\(新しいデバイスとして設定する\)**
  - **Restore from iCloud Backup\(iCloud のバックアップから復元する\)**
  - **Restore from iTunes Backup\(iTunes のバックアップから復元する\)**
2. **&lt;組織が&gt;デバイスを自動的に構成することがユーザーに通知されます。** 構成についてはさらに次の詳細も表示されます。

  **Configuration allows &lt;Your Organization&gt; to manage this device over the air.\(構成により組織はデバイスを無線で管理できます。\)**

  **An administrator can help you set up email and network accounts, install and configure apps, and manage settings remotely.\(メール アカウントとネットワーク アカウントの設定、アプリのインストールと構成、設定のリモート管理については、管理者が支援します。\)**

  **An administrator may disable features, install and remove apps, monitor and restrict your Internet traffic and remotely erase this device.\(管理者は、機能の無効化、アプリのインストールと削除、インターネット トラフィックの監視と制限、このデバイスのリモート消去を行うことができます。\)**

  **Configuration is provided by:<br> &lt;Your organization&gt; iOS Team<br> &lt;Address&gt;**\(構成の提供元: <組織> iOS チーム <アドレス>\)

3. ユーザーは、職場または学校のユーザー名とパスワードの入力を求められます。
4. ユーザーは Apple ID の入力を求められます。 Intune ポータル サイト アプリと他のアプリをインストールするには、Apple ID が必要です。 資格情報を指定した、デバイスによってインストールされる管理プロファイルは削除できません。 Intune 管理プロファイルは、デバイスの **[設定]** > **[全般]** > **[デバイス管理]** で表示されます。

ユーザーは、Intune ポータル サイトまたは Apple Setup Assistant を使って、会社所有のデバイスを設定できます。
