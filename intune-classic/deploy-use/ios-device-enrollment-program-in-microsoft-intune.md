---
title: "iOS デバイスの Apple DEP 管理 | Microsoft Docs"
description: "Apple デバイスを管理するために、iOS Device Enrollment Program (DEP) を通じて購入した iOS デバイスを登録する登録プロファイルを &quot;無線&quot; で展開します。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 03/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8ff9d9e7-eed8-416c-8508-efc20fca8578
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: d5facd519f53ea8534445ad95ae9221cf537b50a
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017


---

# <a name="enroll-corporate-owned-device-enrollment-program-ios-devices"></a>会社所有のデバイス登録プログラムによる iOS デバイスの登録

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune は、"無線" で Device Enrollment Program (DEP) を通じて購入した iOS デバイスを登録する登録プロファイルを展開できます。 登録パッケージには、デバイスのセットアップ アシスタント オプションを含めることができます。

>[!NOTE]
>DEP 登録は、[デバイス登録マネージャー](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)の方法と同時に使用することはできません。
>また、ユーザーが ( ポータル サイト アプリを使用して) iOS デバイスを登録し、デバイスのシリアル番号がインポートされて DEP プロファイルが割り当てられると、このデバイスは Intune から登録が解除されます。

## <a name="prerequisites-for-enrolling-ios-devices-by-using-apple-dep-management"></a>Apple DEP 管理を使用して iOS デバイスを登録する場合の前提条件

- [APNs 証明書のインストール](set-up-ios-and-mac-management-with-microsoft-intune.md)

- 組織は Apple DEP に参加し、そのプログラムでデバイスを取得する必要があります。 そのプロセスの詳細については、  [https://deploy.apple.com](https://deploy.apple.com)を参照してください。 このプログラムの利点には、各デバイスをコンピューターに USB ケーブルを使用して接続することなく、デバイスを楽に設定できる点があります。

- DEP に企業所有の iOS デバイスを登録するには、Apple の DEP トークンが必要です。 このトークンにより、Intune は企業所有の DEP 参加デバイスに関する情報を同期できるようになります。 また、Intune は Apple への登録プロファイルのアップロードを実行して、デバイスをそれらのプロファイルに割り当てられるようになります。

## <a name="steps-to-enroll-ios-devices-by-using-apple-dep-management"></a>Apple DEP 管理を使用して iOS デバイスを登録する手順

次の手順では、Apple DEP 管理を使用して iOS デバイスを登録するための準備方法を説明します。 組織でデバイスが追加および削除された場合、以下に示すように、シリアル番号の追加や削除など、いくつかの手順を繰り返すことがあります。

### <a name="get-an-encryption-key"></a>暗号化キーを取得する

1. 管理者ユーザーとして、[Microsoft Intune の管理コンソール](https://manage.microsoft.com)を開き、**[管理]** &gt; **[モバイル デバイス管理]** &gt; **[iOS]** &gt; **[デバイス登録プログラム]** の順に移動して、**[暗号化キーのダウンロード]** を選択します。

2. 暗号化キー (.pem) ファイルをローカルに保存します。 .pem ファイルは、Apple Device Enrollment Program ポータルから信頼関係証明書を要求するために使用します。

![Device Enrollment Program のトークンの更新](../media/dev-sa-ios-dep.png)

### <a name="get-a-device-enrollment-program-token"></a>Device Enrollment Program のトークンを取得する

1. [Device Enrollment Program ポータル](https://deploy.apple.com) (https://deploy.apple.com) に移動し、会社の Apple ID でサインインします。 この Apple ID は、将来 DEP トークンを更新するために使用する必要があります。

2.  デバイス登録プログラム ポータルで、**[デバイス登録プログラム]** &gt; **[サーバーの管理]** の順に移動して、**[MDM サーバーの追加]** を選択します。

3.  **MDM サーバー名**を入力し、**[Next]** (次へ) をクリックします。 サーバー名は、自分がモバイル デバイス管理 (MDM) サーバーを識別できるようにするための名前です。 Microsoft Intune サーバーの名前または URL ではありません。

4.  **[Add &lt;ServerName&gt;]** ダイアログ ボックスが開きます。 **[Choose File]** (ファイルを選択) をクリックして .pem ファイルをアップロードし、**[Next]** (次へ) を選択します。

5.  **[Add &lt;ServerName&gt;]** (<サーバー名> の追加) ダイアログ ボックスに、**[Your Server Token]** (サーバー トークン) リンクが表示されます。 サーバー トークン (.p7m) ファイルをコンピューターにダウンロードした後、**[Done]** (完了) を選択します。

   この証明書 (.p7m) ファイルは、Intune と Apple の Device Enrollment Program サーバーとの間に信頼関係を確立するために使用されます。

### <a name="add-the-dep-token-to-intune"></a>Intune に DEP トークンを追加する

1. [Microsoft Intune 管理コンソール](https://manage.microsoft.com)で、**[管理]** &gt; **[モバイル デバイス管理]** &gt; **[iOS]** &gt; **[デバイス登録プログラム]** の順に移動します。

2. **[DEP トークンをアップロードする]** を選択します。 証明書 (.p7m) ファイルを**参照**し、**Apple ID** を入力して、**[アップロード]** を選択します。

### <a name="add-the-corporate-device-enrollment-policy"></a>業務用デバイスの登録ポリシーを追加する

1. [Microsoft Intune 管理コンソール](https://manage.microsoft.com)で、**[ポリシー]** &gt; **[業務用デバイスの登録]** の順に選択し、**[追加]** を選択します。

2. **[名前]** や **[説明]** などの **[全般]** の各項目を入力し、次のように、プロファイルに割り当てられているデバイスにユーザー アフィニティがあるか、グループに属するかを指定します。

   - **ユーザー アフィニティを要求する**: 初回セットアップ時にデバイスをユーザーに関連付ける必要があります。その後、デバイスはそのユーザーとして企業のデータやメールにアクセスすることが許可されます。 ユーザーに属し、ポータル サイトを使用する必要がある (つまりアプリをインストールする必要がある) DEP 管理対象のデバイスの場合、**[ユーザー アフィニティ]** を設定する必要があります。 多要素認証 (MFA) は、ユーザー アフィニティを使用して DEP デバイスに登録しているときに動作しません。 DEP デバイスに登録が完了すると、MFA は期待どおりに動作します。 最初にサインインするときにパスワードを変更する必要がある新しいユーザーには、DEP デバイスの登録時にプロンプトを表示することはできません。 さらに、パスワードの有効期限が切れているユーザーには、DEP 登録時にパスワードのリセットは求められません。このユーザーは別のデバイスからパスワードをリセットする必要があります。

       >[!NOTE]
       >ユーザー アフィニティが設定された DEP でユーザー トークンを要求するには、[WS-Trust 1.3 Username/Mixed エンドポイント](https://technet.microsoft.com/en-us/library/adfs2-help-endpoints)を有効にする必要があります。 WS-Trust 1.3 について詳しくは、[こちら](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint)をご覧ください。

   - **ユーザー アフィニティがありません**: デバイスは、ユーザーと関連付けられません。 このデバイス関連付け情報を使用すると、ローカルのユーザー データにアクセスしなくてもタスクを実行できます。 基幹業務アプリのインストールに使用されるポータル サイト アプリなど、ユーザー アフィリエーションが必要なアプリは機能しません。

   **デバイスを次のグループに割り当てる**こともできます。 **[選択...]** を選択して、グループを選択します。

   > [!Important]
   > グループの割り当てが Intune から Azure Active Directory に移動します。 Intune アカウントで適用可能な更新プログラムが受信されると、**[デバイスを次のグループに割り当てる]** オプションは表示されません。 [詳細については、ここをクリック](/intune-classic/deploy-use/ios-device-enrollment-program-in-microsoft-intune#changes-to-intune-group-assignments)してください。

3. **[このポリシーのデバイス登録プログラムの設定を構成します]** を有効にして DEP をサポートします。

      ![[セットアップ アシスタント] ウィンドウ](../media/pol-sa-corp-enroll.png)

   次の設定を DEP 管理対象デバイスに使用できます。

   - **部門** - アクティブ化中にユーザーが **[構成について]** をタップすると表示されます
   - **サポート電話番号** - アクティブ化中にユーザーが **[ヘルプが必要ですか]** ボタンをクリックすると表示されます
   - **準備モード** - アクティブ化中に設定し、デバイスの工場出荷時設定以外では変更できません。
       - **監督解除済み** - 管理機能が制限されます
       - **監督下** - より多くの管理オプションが使用可能になり、既定で [アクティブ化ロック] は無効になります
   - **デバイスへの登録プロファイルのロック** - アクティブ化中に設定し、デバイスの工場出荷時設定以外では変更できません
       - **無効** - **[設定]** メニューから管理プロファイルを削除できます
       - **有効** - (**[準備モード]**  =  **[監督下]** にする必要があります) 管理プロファイルを削除する iOS 設定メニューのオプションを無効にします
   - **セットアップ アシスタントのオプション** - これらの省略可能な設定は、後で iOS の **[設定]** メニューで設定できます。
        - **パスコード** - アクティブ化時にパスコードの入力を求めます。 デバイスがセキュリティで保護される場合や、他の何らかの方法 (デバイスを 1 つのアプリに制限するキオスク モードなど) でアクセスが制御されている場合を除き、パスコードは常に必須にしてください
       - **位置情報サービス** - 有効にすると、アクティブ化時に、セットアップ アシスタントによってサービスがプロンプトされます
       - **復元** - 有効にすると、アクティブ化時に、セットアップ アシスタントによって iCloud バックアップがプロンプトされます
       - **Apple ID** - 有効にして、Intune で ID を指定せずにアプリをインストールしようとすると、Apple ID の入力が求められます。 Intune でインストールされるアプリを含め、iOS App Store アプリをダウンロードする際に Apple ID が必須になります。
       - **使用条件** - 有効にすると、アクティブ化時に、セットアップ アシスタントによって Apple の使用条件に同意するように求められます
       - **タッチ ID** - 有効にすると、アクティブ化時に、セットアップ アシスタントによってこのサービスがプロンプトされます
       - **Apple Pay** - 有効にすると、アクティブ化時に、セットアップ アシスタントによってこのサービスがプロンプトされます
       - **ズーム** - 有効にすると、アクティブ化時に、セットアップ アシスタントによってこのサービスがプロンプトされます
       - **Siri** - 有効にすると、アクティブ化時に、セットアップ アシスタントによってこのサービスがプロンプトされます
       - **Apple に診断データを送信する** - 有効にすると、アクティブ化時に、セットアップ アシスタントによってこのサービスがプロンプトされます
   -  **追加の Apple Configurator の管理を有効にします** - Apple Configurator 経由で iTunes または管理とファイルが同期されないようにするには、**[許可しない]** に設定します。 **[許可しない]** を使用して証明書ありまたは証明書なしの手動の展開を許可するのではなく、[許可しない] を選択して、Apple Configurator からその他の構成をエクスポートし、Intune 経由でカスタム iOS 構成プロファイルとして展開することをお勧めします。
       - **許可しない** - デバイスの USB 経由の通信を禁止します (ペアリングを無効にします)
       - **許可する** - デバイスに PC または Mac との USB 接続での通信を許可します
       - **証明書が必要** - 登録プロファイルにインポートされた証明書を使用した Mac とのペアリングを許可します

### <a name="assign-the-profile-to-devices"></a>デバイスにプロファイルを割り当てる

1. [Microsoft Intune 管理コンソール](https://manage.microsoft.com)で、**[ポリシー]** &gt; **[業務用デバイスの登録]** の順に移動し、**[割り当て]** を選択します。

2. 作成したプロファイルを割り当てるデバイスを選択します。 **[すべてのデバイス]** を選択することも、特定のデバイスを選択することもできます。その後、**[追加]** を選択します。

> [!Important]
> 現在、Intune では "既定の" デバイス登録プロファイルを指定できます。つまり、新しいシリアル番号は、Apple DEP サービスと同期するときに、その既定のプロファイルに自動的に割り当てられます。 今後、新しい Azure Portal にテナントが移行された場合、既定のプロファイルを設定し、そのプロファイルにシリアル番号を自動で割り当てられなくなります。 したがって、ユーザーが自分でシリアル番号を特定のプロファイルに割り当てる必要があります。 [詳細情報](https://docs.microsoft.com/intune/device-enrollment-program-enroll-ios)

### <a name="assign-dep-devices-for-management"></a>管理対象の DEP デバイスを割り当てる

1. [Device Enrollment Program ポータル](https://deploy.apple.com) (https://deploy.apple.com) に移動し、会社の Apple ID でサインインします。

2. **[Deployment Program]** (展開プログラム) &gt; **[Device Enrollment Program]** (デバイス登録プログラム) &gt; **[Manage Devices]** (デバイスの管理) の順に移動します。

3. **デバイスの選択**方法を指定し、デバイス情報を入力して、デバイスの **シリアル番号**、 **注文番号**、または **CSV ファイルのアップロード**で詳細を指定します。

4. **[Assign to Server]** (サーバーに割り当てる) を選択し、Microsoft Intune に指定した &lt;ServerName&gt; を選択して、**[OK]** を選択します。

### <a name="synchronize-dep-managed-devices"></a>DEP 管理対象デバイスを同期する

この手順では、デバイスを Apple DEP サービスと同期し、そのデバイスが Intune コンソールに表示されるようにします。

1. 管理者ユーザーとして、[Microsoft Intune の管理コンソール](https://manage.microsoft.com)を開き、**[管理]** &gt; **[モバイル デバイス管理]** &gt; **[iOS]** &gt; **[デバイス登録プログラム]** の順に移動して、**[今すぐ同期]** を選択します。 同期要求が Apple に送信されます。

2. 同期後に DEP 管理対象デバイスを表示するには、[Microsoft Intune 管理コンソール](https://manage.microsoft.com)で、**[グループ]** &gt; **[すべてのデバイス]** &gt; **[会社の事前登録済みデバイス]** &gt; **[iOS シリアル番号を使用]** の順に移動します。 デバイスの電源を入れ、セットアップ アシスタントを実行して、デバイスを登録するまで、**[iOS シリアル番号を使用]** ワークスペースには管理対象デバイスの **[状態]** が "未接続" と表示されます。

   許容される DEP トラフィックについての Apple の規約に準拠するため、Intune では次の制限が課せられます。

   - 完全な DEP 同期は 7 日ごとに 1 回以上実行できません。 完全同期時に、Intune は Apple が Intune に割り当てたすべてのシリアル番号を、シリアルが以前に同期されているかどうかに関係なく更新します。 前回の完全同期の 7 日以内に完全同期が試みられると、Intune は Intune にまだ一覧表示されていないシリアル番号のみを更新します。

   - すべての同期要求は、完了までに 10 分与えられます。 この時間中または要求が成功するまで、**[同期]** ボタンは無効にされます。

### <a name="distribute-devices-to-users"></a>デバイスをユーザーに配布する

これで、会社が所有するデバイスをユーザーに配布できるようになりました。 iOS デバイスの電源をオンにすると、iOS デバイスが Intune の管理対象として登録されます。 DEP 管理対象デバイスに、ユーザー デバイスの制限が適用されます。

>[!NOTE]
>DEP デバイスを登録しようとしてデバイスの制限を超えた場合、登録は失敗しますがユーザーへの警告はありません。

## <a name="changes-to-intune-group-assignments"></a>Intune グループ割り当ての変更

2017 年 4 月から、デバイス グループの管理は Azure Active Directory に移行されます。 Azure Active Directory グループに切り替えた後は、グループの割り当ては企業の登録プロファイルのオプションに表示されません。 この変更は数か月間にわたりロールアウトされるため、変更はすぐに表示されないことがあります。 新しいポータルに移動した後、会社の登録プロファイルの名前に基づいて動的なデバイス グループの割り当てを定義できます。

移行時に、業務用デバイスの登録プロファイルで事前に割り当てられている Intune デバイス グループごとに、業務用デバイスの登録プロファイルの名前に基づいて、Azure AD に対応する動的デバイス グループが作成されます。 新しいプロファイル名のフォーマットは、*EnrollmentProfile:&lt;関連付けられているプロファイルの名前&gt;* です。 このプロセスにより、デバイス グループに既に割り当てられているデバイスが、ポリシーおよびデプロイされたアプリと共にグループに自動的に登録されることが保証されます。

この自動グループ作成は、グループの移行中に 1 回だけ実行されます。 移行後は、Intune 管理者が Azure Portal を使用してグループを作成する必要があります。 会社所有の iOS デバイスの登録に与える影響の詳細については、「[Changes to Automatic Grouping for Corporate Pre-enrolled iOS Devices](https://blogs.technet.microsoft.com/intunesupport/2017/04/19/changes-to-automatic-grouping-for-corporate-pre-enrolled-ios-devices/)(会社の事前登録済み iOS デバイスに対する自動グループ化の変更)」を参照してください。

[Azure Active Directory グループの詳細について学習する](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-manage-groups/)こともできます。

### <a name="see-also"></a>関連項目
[デバイスを登録するための前提条件](prerequisites-for-enrollment.md)

