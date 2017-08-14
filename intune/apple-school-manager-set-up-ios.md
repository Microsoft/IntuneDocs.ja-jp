---
title: "iOS デバイスのための Apple School Manager プログラム登録の設定"
titleSuffix: Intune on Azure
description: "企業所有の iOS デバイスを Intune で登録するために、Apple School Manager プログラム登録を設定する方法について説明します。\""
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 07/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7981a9c0-168e-4c54-9afd-ac51e895042c
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7079a22afc04b5674eb8f12a2833961e86939a28
ms.sourcegitcommit: 79116d4c7f11bafc7c444fc9f5af80fa0b21224e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2017
---
# <a name="enable-ios-device-enrollment-with-apple-school-manager"></a>Apple School Manager での iOS デバイス登録の有効化

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

このトピックは、IT 管理者が [Apple School Manager](https://school.apple.com/) プログラムで購入したデバイスの iOS デバイス登録を有効にする場合に役立ちます。 Microsoft Intune では登録プロファイルを "無線で" 展開して、Apple School Manager デバイスを管理対象として登録することができます。 管理者は、管理された各デバイスに触れる必要はありません。 登録プロファイルには、セットアップ アシスタント オプションなどの、登録時にデバイスに適用される管理設定が含まれています。

**Apple School Manager 登録の手順**
1. [Apple School Manager トークンを取得し、デバイスを割り当てる](#get-the-apple-token-and-assign-devices)
2. [登録プロファイルの作成](#create-an-apple-enrollment-profile)
3. [School Data Sync の接続](#connect-school-data-sync) (省略可能)
4. [Apple School Manager 管理デバイスを同期する](#sync-managed-devices)
5. [Apple School Manager プロファイルをデバイスに割り当てる](#assign-a-profile-to-devices)
6. [デバイスをユーザーに配布する](#distribute-devices-to-users)

>[!NOTE]
>Apple School Manager 登録を、[Apple の DEP](device-enrollment-program-enroll-ios.md) や[デバイス登録マネージャー](device-enrollment-manager-enroll.md)で使用することはできません。

## <a name="get-the-apple-token-and-assign-devices"></a>Apple トークンを取得し、デバイスを割り当てる

Apple School Manager で企業所有の iOS デバイスを登録するには、Apple のトークン (.p7m) ファイルが必要です。 このトークンにより、Intune は Apple School Manager 参加デバイスに関する情報を同期できるようになります。 また、Intune は Apple への登録プロファイルのアップロードを実行して、デバイスをそれらのプロファイルに割り当てられるようになります。 Apple ポータルでは、管理するデバイスのシリアル番号も割り当てることができます。

**必要条件**
- [Apple MDM プッシュ証明書](apple-mdm-push-certificate-get.md)
- [Apple School Management](http://school.apple.com) へのサインアップ

**手順 1: Apple トークンを作成するために必要な Intune 公開キー証明書をダウンロードします。**<br>
1. Azure [Intune ポータル](https://aka.ms/intuneportal)で **[デバイスの登録]** を選択し、**[Enrollment Program トークン]** を選択します。
2. **[Enrollment Program トークン]** ブレードで、**[公開キーをダウンロードします]** を選択して、暗号化キー (.pem) ファイルをダウンロードし、ローカルに保存します。 .pem ファイルは、Apple School Manager ポータルから信頼関係証明書を要求するために使用します。

**手順 2:トークンをダウンロードしてデバイスを割り当てます。**<br>
**[Apple School Manager を使用してトークンを作成します]** を選択し、会社の Apple ID でサインインします。 この Apple ID を使用して、Apple School Manager トークンを更新することができます。

   1.  [Apple School Manager ポータル](https://school.apple.com)で、**[MDM Servers]\(MDM サーバー\)** に移動し、**[Add MDM Server]\(MDM サーバーの追加\)** (右上) を選択します。
   2.  **MDM サーバー名**を入力します。 サーバー名は、自分がモバイル デバイス管理 (MDM) サーバーを識別できるようにするための名前です。 Microsoft Intune サーバーの名前または URL ではありません。
   3.  Apple ポータルで **[ファイルのアップロード...]** を選択し、.pem ファイルを参照して、**[Save MDM Server]\(MDM サーバーの保存\)** (右下) を選択します。
   4.  **[Get Token]\(トークンの取得\)** を選択し、サーバー トークン (.p7m) ファイルをコンピューターにダウンロードします。
   5. **[デバイスの割り当て]** に移動し、**シリアル番号**、**注文番号** を手動で入力するか、**CSV ファイルのアップロード**で **[デバイスの選択]** を行います。
   6.   **[Assign to Server]\(サーバーに割り当てる\)** を選択し、作成した **MDM サーバー** を選択します。
   7. **デバイスの選択**方法を指定してから、デバイス情報と詳細を提供します。
   8. **[Assign to Server]** (サーバーに割り当てる) を選択し、Microsoft Intune に指定した &lt;ServerName&gt; を選択して、**[OK]** を選択します。

**手順 3:Apple School Manager トークンの作成に使用した Apple ID を入力します。**<br>この ID は Apple School Manager トークンの更新に使用する必要があるため、今後の参照用に保存されます。

**手順 4:トークンを検索してアップロードします。**<br>
証明書 (.p7m) ファイルに移動し、**[開く]** を選択して、**[アップロード]** を選択します。 Intune は、Apple の Apple School Manager デバイスを自動的に同期します。

## <a name="create-an-apple-enrollment-profile"></a>Apple 登録プロファイルの作成
デバイス登録プロファイルで、デバイス グループに対して登録時に適用する設定を定義します。

1. Intune ポータルで **[デバイスの登録]** を選択し、**[Apple の登録]** を選択します。
2. **[Enrollment Program]** で、**[Enrollment Program プロファイル]** を選択します。
3. **[Enrollment Program プロファイル]** ブレードで、**[作成]** を選択します。
4. **[登録プロファイルの作成]** ブレードで、Intune ポータルに表示されるプロファイルの**名前**と**説明**を入力します。
5. **[ユーザー アフィニティ]** で、このプロファイルに対応するデバイスをユーザー アフィニティとともに登録するかどうかを選択します。

 - **ユーザー アフィニティとともに登録する** - セットアップ中にデバイスとユーザーを関連付けます。

 >[!NOTE]
 >多要素認証 (MFA) は、ユーザー アフィニティを使用して Apple School Manager デバイスに登録している間は動作しません。 DEP デバイスに登録が完了すると、MFA は期待どおりに動作します。

  Apple School Manager の [共有 iPad] モードでは、ユーザーはユーザー アフィニティなしで登録する必要があります。

 >[!NOTE]
    >ユーザー アフィニティが設定された Apple School Manager でユーザー トークンを要求するには、[WS-Trust 1.3 Username/Mixed エンドポイント](https://technet.microsoft.com/library/adfs2-help-endpoints)を有効にする必要があります。 WS-Trust 1.3 について詳しくは、[こちら](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint)をご覧ください。

 - **[ユーザー アフィニティなしで登録する]** - デバイスは、ユーザーと関連付けられません。 このデバイス関連付け情報を使用すると、ローカルのユーザー データにアクセスしなくてもタスクを実行できます。 ユーザー アフィニティが必要なアプリ (基幹業務アプリのインストールに使用されるポータル サイト アプリを含む) は機能しません。

6. **[デバイス管理の設定]** を選択します。 これらの項目はアクティブ化のときに設定され、項目を変更するには出荷時の設定に戻す必要があります。 次のプロファイル設定を構成して、**[保存]** を選択します。

    - **[監督下]** - より多くの管理オプションが使用可能な管理モードです。既定でアクティベーション ロックは無効になります。 このチェック ボックスをオフのままにすると、管理機能が制限されます。

    - **[ロックされた登録]** - ([管理モード] を [監督下] にする必要があります) 管理プロファイルの削除を許可する iOS 設定を無効にします。 このチェック ボックスをオフのままにすると、[設定] メニューから管理プロファイルを削除できます。

  - **[共有 iPad]** - (**[ユーザー アフィニティなしで登録する]** と **[監視下]** モードが必要です。)管理された Apple ID を使用して、複数のユーザーが登録済みの iPad にログオンすることを許可します。 管理された Apple ID は、Apple School Manager ポータルで作成されます。

  >[!NOTE]
  >**[ユーザー アフィニティ]** を **[With user affinity]\(ユーザー アフィニティあり\)** に設定するか、**[監視下]** モードを **[オフ]** に設定すると、登録プロファイルの [共有 iPad] モードは無効になります。

  - **[キャッシュされたユーザーの最大数]** - (**[共有 iPad]** = **[はい]** にする必要があります) 各ユーザーのデバイスにパーティションを作成します。 推奨値は、期間中にデバイスを使用する可能性がある学生の数です。 たとえば、平日に頻繁にデバイスを使用する学生が 6 人いる場合は、この数を 6 に設定します。  

    - **[ペアリングの許可]** - iOS デバイスをコンピューターと同期できるかどうかを指定します。 **[証明書による Apple Configurator の許可]** を選択した場合は、**[Apple Configurator の証明書]** で証明書を選択する必要があります。

    - **[Apple Configurator の証明書]** - **[ペアリングの許可]** で **[証明書による Apple Configurator の許可]** を選択した場合は、インポートする Apple Configurator の証明書を選択します。

7. **[セットアップ アシスタントの設定]** を選択し、次のプロファイル設定を構成して、**[保存]** を選択します。

    - **[部署名]** - アクティブ化中にユーザーが **[About Configuration (構成について)]** をタップすると表示されます。

    - **[部署の電話番号]** - アクティブ化中にユーザーが [ヘルプが必要ですか] ボタンをクリックすると表示されます。
    - **[Setup Assistant Options]\(セットアップ アシスタントのオプション\)** - セットアップ アシスタントのオプションから除外した場合、これらの設定は後で iOS の **[設定]** メニューで設定できます。
        - **パスコード** - アクティブ化時にパスコードの入力を求めます。 デバイスがセキュリティで保護される場合や、他の何らかの方法 (デバイスを 1 つのアプリに制限するキオスク モードなど) でアクセスが制御されている場合を除き、パスコードは常に必須にしてください。
        - **位置情報サービス** - 有効にすると、アクティブ化時に、セットアップ アシスタントによってサービスがプロンプトされます
        - **復元** - 有効にすると、アクティブ化時に、セットアップ アシスタントによって iCloud バックアップがプロンプトされます
        - **[Apple ID]** - 有効にすると、Intune で ID を指定せずにアプリをインストールしようとするときに iOS によって Apple ID の入力を求められます。 Intune でインストールされるアプリを含め、iOS App Store アプリをダウンロードする際に Apple ID が必須になります。
        - **使用条件** - 有効にすると、アクティブ化時に、セットアップ アシスタントによって Apple の使用条件に同意するように求められます
        - **タッチ ID** - 有効にすると、アクティブ化時に、セットアップ アシスタントによってこのサービスがプロンプトされます
        - **Apple Pay** - 有効にすると、アクティブ化時に、セットアップ アシスタントによってこのサービスがプロンプトされます
        - **ズーム** - 有効にすると、アクティブ化時に、セットアップ アシスタントによってこのサービスがプロンプトされます
        - **Siri** - 有効にすると、アクティブ化時に、セットアップ アシスタントによってこのサービスがプロンプトされます
        - **[診断データ]** - 有効にすると、アクティブ化時に、セットアップ アシスタントによってこのサービスがプロンプトされます

8. プロファイルの設定を保存するには、**[登録プロファイルの作成]** ブレードで **[作成]** を選択します。

## <a name="connect-school-data-sync"></a>School Data Sync の接続
(省略可能) Apple School Manager では、Microsoft School Data Sync (SDS) を使用した Azure Active Directory (AD) へのクラス リスト データの同期がサポートされています。 SDS を使用して学校のデータを同期するには、次の手順を完了します。

1. **[Enrollment Program トークン]** ブレードで、青色の情報バナーまたは **[SDS の接続]** を選択します。
2. **[Microsoft School Data Sync でこのトークンを使用できるようにする]** を選択し、**[許可]** に設定します。 この設定により、Intune は Office 365 で SDS に接続できます。
3. Apple School Manager と Azure AD の間の接続を有効にするには、**[Microsoft School Data Sync の設定]** を選択します。 [School Data Sync の設定方法](https://support.office.com/article/Install-the-School-Data-Sync-Toolkit-8e27426c-8c46-416e-b0df-c29b5f3f62e1)について詳しく学びます。
4. **[OK]** をクリックし、設定を保存して続行します。

## <a name="sync-managed-devices"></a>管理対象デバイスを同期する
Intune に Apple School Manager デバイスを管理するアクセス許可を割り当てたので、Intune と Apple サービスを同期し、管理されたデバイスを Intune ポータルに表示できます。

1. Intune ポータルで **[デバイスの登録]** を選択し、**[Apple の登録]** を選択します。
2. **[Enrollment Program デバイス]** で、**[同期]** を選択します。 進行状況バーには、もう一度同期が要求されるまでの待ち時間が表示されます。

    許容されるトラフィックについての Apple の規約に準拠するため、Intune では次の制限が課せられます。
     -  完全な同期は 7 日に 1 回だけ実行できます。 完全同期時に、Intune は Apple が Intune に割り当てたすべてのシリアル番号を、シリアルが以前に同期されているかどうかに関係なく更新します。 前回の完全同期の 7 日以内に完全同期が試みられると、Intune は Intune にまだ一覧表示されていないシリアル番号のみを更新します。
     -  すべての同期要求は、完了までに 15 分与えられます。 この時間中または要求が成功するまで、**[同期]** ボタンは無効にされます。

>[!NOTE]
>**[Enrollment Program デバイス]** ブレードで、Apple School Manager のシリアル番号をプロファイルに割り当てることもできます。

## <a name="assign-a-profile-to-devices"></a>デバイスにプロファイルを割り当てる
Intune によって管理される Apple School Manager デバイスを登録する前に、デバイスに登録プロファイルを割り当てる必要があります。

1. Intune ポータルで **[デバイスの登録]** > **[Apple の登録]** の順に選択し、**[Enrollment Program プロファイル]** を選択します。
2. **[Enrollment Program プロファイル]** の一覧からデバイスに割り当てるプロファイルを選択し、**[デバイスの割り当て]** を選択します。
3. **[割り当て]** を選択し、このプロファイルを割り当てる Apple School Manager デバイスを選択します。 フィルターを適用して使用可能なデバイスを表示できます。
  - **未割り当て**
  - **任意**
  - **&lt;Apple School Manager プロファイルの名前&gt;**
4. 割り当てるデバイスを選択します。 列の上のチェック ボックスで、一覧表示されたデバイスを最大 1,000 まで選択します。 **[割り当て]** をクリックします。 1,000 を超えるデバイスを登録するには、すべてのデバイスに登録プロファイルを割り当てるまで割り当て手順を繰り返します。

## <a name="distribute-devices-to-users"></a>デバイスをユーザーに配布する

これで、会社が所有するデバイスをユーザーに配布できるようになりました。 iOS Apple School Manager デバイスの電源をオンにすると、それが Intune の管理対象として登録されます。 デバイスがアクティブ化されて使用中の場合、デバイスを工場出荷時の状態にリセットするまで、プロファイルを適用できません。

### <a name="how-users-install-and-use-the-company-portal-on-their-devices"></a>デバイスにポータル サイト アプリをインストールして使用する方法

ユーザー アフィニティが構成されたデバイスでは、ポータル サイト アプリをインストールして実行し、アプリをダウンロードしてデバイスを管理できます。 ユーザーは、デバイスを受け取った後、セットアップ アシスタントを実行してポータル サイト アプリをインストールする必要があります。
