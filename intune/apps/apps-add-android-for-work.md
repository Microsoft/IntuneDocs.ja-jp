---
title: マネージド Google Play アプリを Android Enterprise デバイスに割り当てる
titleSuffix: Microsoft Intune
description: マネージド Google Play ストアから Android Enterprise デバイスにアプリを同期して割り当てる方法について説明します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/22/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2f6c06bf-e29a-4715-937b-1d2c7cf663d4
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 126ea5a1798252f29e988553edfea462eff2fd7e
ms.sourcegitcommit: a25f556aa9df4fcd9fdacccd12c9029bc6c5fe20
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/03/2020
ms.locfileid: "78256460"
---
# <a name="add-managed-google-play-apps-to-android-enterprise-devices-with-intune"></a>Intune を使ってマネージド Google Play アプリを Android Enterprise デバイスに追加する

マネージド Google Play は、Google のエンタープライズ アプリ ストアであり、Android Enterprise 用の唯一のアプリケーション ソースです。 Intune を使用すると、任意の Android Enterprise シナリオ (仕事用プロファイル、専用、およびフル マネージド登録など) に対して、マネージド Google Play 経由でのアプリの展開を調整できます。 マネージド Google Play アプリを Intune に追加する方法は、Android アプリを Android Enterprise 以外に追加する方法とは異なります。 ストア アプリ、基幹業務 (LOB) アプリ、および Web アプリは、マネージド Google Play に承認または追加され、Intune に同期されてクライアント アプリの一覧に表示されます。 クライアント アプリの一覧に表示されたら、他のアプリの場合と同様に、任意のマネージド Google Play アプリの割り当てを管理できます。

Android Enterprise 管理をより簡単に構成して使用できるように、マネージド Google Play に Intune テナントを接続する際に、Intune では 4 つの一般的な Android Enterprise 関連アプリが Intune 管理コンソールに自動的に追加されます。 次に 4 つのアプリを示します。

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** - Android Enterprise フル マネージド シナリオで使用されます。 このアプリは、デバイス登録プロセスの最中に、フル マネージド デバイスへ自動的にインストールされます。
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** - 2 要素認証を使用している場合、アカウントへのサインインを支援します。 このアプリは、デバイス登録プロセスの最中に、フル マネージド デバイスへ自動的にインストールされます。
- **[Intune ポータル サイト](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** - アプリ保護ポリシー (APP) と Android Enterprise 仕事用プロファイルのシナリオで使用されます。
- **[マネージド ホーム スクリーン](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise)** - Android Enterprise 専用のマルチアプリ キオスクのシナリオに使用されます。 IT 管理者は割り当てを作成して、マルチアプリ キオスクのシナリオに使用される専用デバイス上に、このアプリをインストールする必要があります。

>[!NOTE]
>エンド ユーザーが自身の Android Enterprise フル マネージド デバイスを登録すると、Intune ポータル サイト アプリが自動的にインストールされ、アプリケーションのアイコンがエンド ユーザーに表示されます。 エンド ユーザーが Intune ポータル サイト アプリの起動を試みると、そのエンド ユーザーは Microsoft Intune アプリにリダイレクトされ、以降はポータル サイトのアプリ アイコンが非表示になります。

## <a name="before-you-start"></a>開始する前に
- Intune テナントをマネージド Google Play に接続したことを確認します。  詳細については、[Managed Google Play アカウントへの Intune アカウントの接続](../enrollment/connect-intune-android-enterprise.md)に関するページを参照してください。
- 仕事用プロファイル デバイスの登録を予定している場合は、Intune と Android の仕事用プロファイルが Azure portal の **[デバイスの登録]** ワークロードに連携されるように構成したことを確認します。 詳細については、「[Android デバイスの登録](../enrollment/android-work-profile-enroll.md)」を参照してください。

>[!NOTE]
>Microsoft Intune を使うときは、Microsoft Edge または Google Chrome ブラウザーを使うことをお勧めします。

## <a name="managed-google-play-app-types"></a>マネージド Google Play アプリの種類
マネージド Google Play では、次の 3 種類のアプリを利用できます。

- **マネージド Google Play ストア アプリ** - Play ストア内で一般提供されている公式アプリ。 管理するアプリを参照して承認し、Intune に同期することで、Intune 内でこれらのアプリを管理します。
- **マネージド Google Play プライベート アプリ** - これらは、Intune 管理者によってマネージド Google Play に発行された LOB アプリです。  これらのアプリはプライベートであり、ご自身の Intune テナントのみで利用可能です。 これは、マネージド Google Play および Android Enterprise を使って LOB アプリを管理および展開する方法です。
- **マネージド Google Play Web リンク** - Android Enterprise デバイスに展開できる IT 管理者が定義したアイコン付きの Web リンク。 これらは、デバイス上で、通常のアプリと同じようにデバイスのアプリ一覧内に表示されます。

## <a name="managed-google-play-store-apps"></a>マネージド Google Play ストア アプリ
Intune を使ってマネージド Google Play ストア アプリを参照して承認するには、次の 2 つの方法があります。

1. Intune コンソール内で直接行う - Intune 内でホストされているビューで、ストア アプリを参照して承認します。 これは、Intune コンソール内で直接開かれ、別のアカウントによる再認証が求められることはありません。
1. マネージド Google Play コンソール内で行う - 必要に応じて、マネージド Google Play コンソールを直接開き、そこでアプリを承認することができます。 詳細については、「[Sync a Managed Google Play app with Intune (Intune を使ってマネージド Google Play アプリを同期する)](apps-add-android-for-work.md#sync-a-managed-google-play-app-with-intune)」を参照してください。  これには、Intune テナントをマネージド Google Play に接続するために使ったアカウントを利用して、別のログインが必要になります。

### <a name="add-a-managed-google-play-store-app-directly-in-the-intune-console"></a>マネージド Google Play ストア アプリを Intune コンソール内で直接追加する

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。
2. **[アプリ]**  >  **[すべてのアプリ]**  >  **[追加]** の順に選択します。
3. **[アプリの種類の選択]** ペインの使用できる **[ストア アプリ]** の種類で、 **[managed Google Play アプリ]** を選択します。
4. **[選択]** をクリックします。 **[managed Google Play]** アプリ ストアが表示されます。

    > [!NOTE]
    > managed Google Play ストア アプリを参照するには、Intune テナント アカウントが Android Enterprise アカウントに接続されている必要があります。 詳細については、[Managed Google Play アカウントへの Intune アカウントの接続](../enrollment/connect-intune-android-enterprise.md)に関するページを参照してください。

5. アプリを選択してアプリの詳細を表示します。
6. アプリが表示されたページで、 **[承認]** をクリックします。 多様な操作を実行するアクセス許可をアプリに付与するように求めるウィンドウが開きます。
7. **[承認]** を選択し、アプリのアクセス許可に同意して続行します。
8. **[承認の設定]** タブで **[Keep approved when app requests new permissions]\(アプリから新しいアクセス許可が要求されたときに承認済みのままにする\)** を選択し、 **[完了]** をクリックします。 

    > [!IMPORTANT]
    > このオプションを選択しない場合、アプリの開発者が更新プログラムを発行した場合に、新しいアクセス許可をすべて手動で承認することが必要になります。 これにより、アクセス許可が承認されるまでアプリのインストールと更新が停止されます。 このため、新しいアクセス許可を自動的に承認するオプションを選択することをお勧めします。 

9. **[選択]** をクリックしてアプリを選択します。
10. ブレードの上部にある **[同期]** をクリックして、アプリを managed Google Play サービスと同期します。
11. **[更新]** をクリックしてアプリの一覧を更新し、新しく追加されたアプリを表示します。

### <a name="add-a-managed-google-play-store-app-in-the-managed-google-play-console-alternative"></a>マネージド Google Play コンソールにマネージド Google Play ストア アプリを追加する (別の方法)
Intune を使用して直接追加するのではなく、managed Google Play アプリを Intune と同期する場合は、次の手順を実行します。

> [!IMPORTANT]
> 以下の情報は、前述の Intune を使用した managed Google Play アプリの追加の代替方法です。

1. [Managed Google Play ストア](https://play.google.com/work)に移動します。 Intune と Android Enterprise 間の接続の構成に利用した同一のアカウントを使って、サインインします。
2. Intune を使用して割り当てるアプリをストアで検索します。
3. アプリが表示されたページで、 **[承認]** をクリックします。  
    Microsoft Excel アプリが選択されている例を次に示します。

    ![Managed Google Play ストアの [承認] ボタン](./media/apps-add-android-for-work/approve.png)

   多様な操作を実行するアクセス許可をアプリに付与するように求めるウィンドウが開きます。

4. **[承認]** を選択し、アプリのアクセス許可に同意して続行します。

    ![アプリのアクセス許可の [承認] ボタン](./media/apps-add-android-for-work/approve-app-permissions.png)

5. 新しいアプリのアクセス許可要求を処理するオプションを選択し、 **[保存]** を選択します。

    ![新しいアプリのアクセス許可要求を処理するオプション](./media/apps-add-android-for-work/approve-app-settings.png)

    アプリは承認され、IT 管理者コンソールに表示されます。 次に、[Intune と Android 仕事用プロファイルのアプリを同期する](apps-add-android-for-work.md#sync-a-managed-google-play-app-with-intune)ことができます。

## <a name="managed-google-play-private-lob-apps"></a>マネージド Google Play プライベート (LOB) アプリ

LOB アプリをマネージド Google Play に追加するには、2 つの方法があります。

1. Intune コンソール内で直接行う - これを利用すると、アプリの APK とタイトルだけを送信して、Intune 内で直接 LOB アプリを追加できます。 この方法では、Google 開発者アカウントを保持している必要はなく、開発者として Google に登録料を支払う必要はありません。  この方法は比較的シンプルで手順の数が大幅に少なくなっており、ほんの 10 分程度で LOB アプリを管理できるようになります。
1. Google Play Developer Console 内で行う - Google 開発者アカウントを保持しているか、または Google Play Developer Console 内のみで利用できる高度な配布機能を構成する場合 (追加でアプリのスクリーンショットを付加するなど) は、[Google Play Developer Console](https://play.google.com/apps/publish)を利用できます。 

### <a name="managed-google-play-private-lob-app-publishing-directly-in-the-intune-console"></a>Intune コンソール内でマネージド Google Play プライベート (LOB) アプリを直接発行する

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。
2. **[アプリ]**  >  **[すべてのアプリ]**  >  **[追加]** の順に選択します。
3. **[アプリの種類の選択]** ペインの使用できる **[ストア アプリ]** の種類で、 **[managed Google Play アプリ]** を選択します。
4. **[選択]** をクリックします。 **[managed Google Play]** アプリ ストアが Intune 内に表示されます。
5. [Google Play] ウィンドウで **[Private apps]\(プライベート アプリ\)** ("*ロック*" アイコンの横) を選択します。 
6. 右下にある **[+]** ボタン クリックして新しいアプリを追加します。
7. アプリの **[タイトル]** を追加し、 **[アップロード]** をクリックして APK アプリ パッケージを追加します。
8. **[作成]** をクリックします。
9. アプリの追加が完了したら、[managed Google Play] ペインを閉じます。
10. **[アプリの追加]** ウィンドウの **[同期]** をクリックして、managed Google Play サービスと同期します。 

    > [!NOTE]
    > プライベート アプリを同期できるまでに、数分かかる場合があります。最初に同期を実行したときにアプリが表示されない場合は、数分待ってから新しい同期を開始してください。

FAQ を含むマネージド Google Play プライベート アプリの詳細については、Google のサポート記事 (https://support.google.com/googleplay/work/answer/9146439 ) を参照してください。

>[!IMPORTANT]
>このメソッドを使用して追加されたプライベート アプリは、パブリックにすることはできません。 このアプリが常に組織にとってプライベートであることが確実な場合にのみ、この発行オプションを使用してください。

### <a name="managed-google-play-private-lob-app-publishing-using-the-google-developer-console"></a>Google Developer Console を使用してマネージド Google Play プライベート (LOB) アプリを発行する

1. Intune と Android Enterprise 間の接続の構成に利用した同一のアカウントを使って、[Google Play Developer Console](https://play.google.com/apps/publish) にサインインします。  
    初めてサインインする場合は、Google Developer プログラムに登録し、料金を払ってメンバーになる必要があります。
2. コンソールで、 **[Add new application]\(新しいアプリケーションの追加\)** を選択します。
3. アプリをアップロードし、アプリに関する情報を提供する方法は、アプリを Google Play ストアに公開する方法と同じです。 ただし、 **[Only make this application available to my organization (<*organization name*>)]\(このアプリケーションを自分の組織 (<組織名>) のみが入手できるようにする\)** を選択する必要があります。

    ![組織のみがアプリを入手できるようにする](./media/apps-add-android-for-work/restrict.png)

    この操作により、自分の組織のみがアプリを入手できるようにします。 これは一般の Google Play ストアでは使用できません。

    Android アプリのアップロードと公開の詳細については、[Google Developer Console のヘルプ](https://support.google.com/googleplay/android-developer/answer/113469)を参照してください。
4. アプリを発行したら、Intune と Android Enterprise 間の接続の構成に利用した同一のアカウントを使って、[マネージド Google Play ストア](https://play.google.com/work)にサインインします。
5. ストアの **[アプリ]** ノードに、公開したアプリが表示されることを確認します。  
    アプリは自動的に承認され、Intune と同期されます。

## <a name="managed-google-play-web-links"></a>マネージド Google Play Web リンク

マネージド Google Play Web リンクは、他の Android アプリと同じように、インストールおよび管理することが可能です。 デバイスにインストールすると、インストール済みの他のアプリと共に、ユーザーのアプリ一覧に表示されます。 タップすると、デバイスのブラウザーで起動されます。

Web リンクは、Microsoft Edge または選択して展開したその他のブラウザー アプリを使って開かれます。 Web リンクが適切に開かれるように、少なくとも 1 つのブラウザー アプリをデバイスに展開してください。 ただし、Web リンクに使用できる **[表示]** オプション (全画面、スタンドアロン、および 最小 UI) はすべて、Chrome ブラウザーのみで機能します。 

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。
2. **[アプリ]**  >  **[すべてのアプリ]**  >  **[追加]** の順に選択します。
3. **[アプリの種類の選択]** ペインの使用できる **[ストア アプリ]** の種類で、 **[managed Google Play アプリ]** を選択します。
4. **[選択]** をクリックします。 **[managed Google Play]** アプリ ストアが Intune 内に表示されます。
5. [Google Play] ウィンドウで **[Web アプリ]** ("*地球*" アイコンの横) を選択します。
6. 右下にある **[+]** ボタン クリックして新しいアプリを追加します。
7. アプリの **[タイトル]** と Web アプリの **[URL]** を追加し、アプリの表示方法を選択し、アプリ アイコンを選択します。
8. **[作成]** をクリックします。
9. アプリの追加が完了したら、[managed Google Play] ペインを閉じます。
10. **[アプリの追加]** ウィンドウの **[同期]** をクリックして、managed Google Play サービスと同期します。 

    > [!NOTE]
    > Web アプリを同期できるまでに、数分かかる場合があります。最初に同期を実行したときにアプリが表示されない場合は、数分待ってから新しい同期を開始してください。

## <a name="sync-a-managed-google-play-app-with-intune"></a>Intune で Managed Google Play のアプリを同期する

ストアからのアプリを承認しても、 **[アプリ]** ワークロードに表示されない場合は、次の手順を実行して、即時同期を強制します。

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。
3. **[アプリ]**  >  **[テナント管理]**  >  **[コネクタとトークン]**  >  **[マネージ Google Play]** を選択します。
5. **[Managed Google Play]** ウィンドウで、 **[更新]** を選択します。  
    ページで、前回の同期の時刻と状態が更新されます。
6. Microsoft Endpoint Manager 管理センターで、 **[アプリ]**  >  **[すべてのアプリ]** の順に選択します。  
    新しく使用可能になった Managed Google Play アプリが表示されます。

## <a name="assigning-a-managed-google-play-app-to-android-enterprise-work-profile-devices"></a>マネージド Google Play アプリを Android Enterprise 仕事用プロファイル デバイスに割り当てる

アプリが **[アプリ]** ワークロード ウィンドウの **[アプリ ライセンス]** ノードに表示される場合は、そのアプリをユーザーのグループに割り当てることで、[他のアプリの割り当てと同様の方法で割り当てる](/intune-azure/manage-apps/deploy-apps)ことができます。

アプリを割り当てると、対象のユーザーのデバイス上にインストールされます (あるいは、インストール可能になります)。 デバイスのユーザーがインストールの承認を求められることはありません。 Android Enterprise 仕事用プロファイル デバイスの詳細については、「[Set up enrollment of Android Enterprise work profile devices (Android Enterprise 仕事用プロファイル デバイスの登録を設定する)](../enrollment/android-work-profile-enroll.md)」を参照してください。 

> [!NOTE] 
> エンド ユーザーのマネージド Google Play ストアには、割り当てられたアプリだけが表示されます。 そのため、これはマネージド Google Play を使ってアプリを設定するときに、管理者が行う重要な手順です。

## <a name="assigning-a-managed-google-play-app-to-android-enterprise-fully-managed-devices"></a>マネージド Google Play アプリを Android Enterprise フル マネージド デバイスに割り当てる

[Android Enterprise フル マネージド デバイス](../enrollment/android-fully-managed-enroll.md)は、1 人のユーザーに関連付けられている会社所有のデバイスであり、私用ではなく仕事限定で使用されます。 フル マネージド デバイス上のユーザーは、自身のデバイス上でマネージド Google Play アプリから使用可能な業務用アプリを取得できます。

既定では、Android Enterprise フル マネージド デバイスには、組織によって承認されていないアプリを従業員がインストールすることはできません。 また、従業員は、インストールされているアプリをポリシーに反して削除することはできません。 ユーザーが、マネージド Google Play ストア内で承認されたアプリだけにアクセスするのではなく、完全な Google Play ストアにアクセスしてアプリをインストールできるようにする場合は、 **[Google Play ストア内のすべてのアプリへのアクセスを許可]** を **[許可]** に設定できます。 この設定を利用すると、ユーザーは会社のアカウントを使用して Google Play ストア内のすべてのアプリにアクセスできます。ただし、購入は制限される場合があります。 ユーザーがデバイスに新しいアカウントを追加できるようにすることで、購入を限定する制限を削除できます。 これにより、エンド ユーザーは、個人用アカウントを使用して Google Play ストアからアプリを購入できるだけでなく、アプリ内購入を行うことができます。 詳細については、「[Android Enterprise device settings to allow or restrict features using Intune (Intune を使用して機能を許可または制限する Android Enterprise デバイス設定)](../configuration/device-restrictions-android-for-work.md)」を参照してください。 

> [!NOTE]
> Microsoft Intune アプリおよび Microsoft Authenticator アプリは、オンボード中にすべてのフル マネージド デバイスに必要なアプリとしてインストールされます。 これらのアプリを自動的にインストールすると、条件付きアクセスのサポートが提供され、Microsoft Intune アプリ ユーザーは、コンプライアンスの問題を確認して解決することができます。 

## <a name="manage-android-enterprise-app-permissions"></a>Android Enterprise アプリのアクセス許可の管理
Android Enterprise では、Intune にアプリを同期してユーザーに割り当てる前に、マネージド Google Play Web コンソール内でアプリを承認する必要があります。 Android Enterprise を利用すると、ユーザーのデバイスに通知なしで自動的にアプリをプッシュできるため、すべてのユーザーに代わってアプリへのアクセスを許可する必要があります。 ユーザーがアプリをインストールする際はアプリのアクセス許可に関する表示が行われないため、これらのアクセス許可について理解する必要があります。

アプリ開発者がアプリの新しいバージョンでアクセス許可を更新した場合、以前のアクセス許可を承認していても、アクセスは自動的に許可されません。 以前のバージョンのアプリを実行しているデバイスは、そのアプリを引き続き使用できます。 ただし、新しいアクセス許可が承認されるまで、アプリはアップグレードされません。 アプリをインストールしていないデバイスでは、アプリの新しいアクセス許可を承認するまで、アプリをインストールしません。 

### <a name="update-app-permissions"></a>アプリのアクセス許可を更新する

管理対象の Google Play コンソールに定期的にアクセスして、新しいアクセス許可があるかどうか確認してください。 承認されたアプリに新しいアクセス許可が必要な場合は、自分や他のユーザーに電子メールを送信するように Google Play を構成できます。 アプリを割り当ててもデバイスにインストールされていない場合は、次の手順を実行して新しいアクセス許可を確認します。

1. [Google Play](https://play.google.com/work) に移動します。
2. アプリを公開して承認する際に使用した Google アカウントでサインインします。
3. **[更新]** タブを選択し、更新が必要なアプリがあるかどうかを確認します。  
    一覧にあるアプリでは新しいアクセス許可が必要で、それらが適用されるまで割り当てられません。

あるいは、Google Play を構成することで、アプリごとにアクセス許可を自動的に再許可できます。

## <a name="additional-managed-google-play-app-reporting-for-android-enterprise-work-profile-devices"></a>Android エンタープライズ仕事用プロファイル デバイスに関するマネージド Google Play アプリの追加レポート

Android エンタープライズ仕事用プロファイル デバイスに展開されたマネージド Google Play アプリの場合は、Intune を使用して、デバイスにインストールされたアプリの状態とバージョン番号を表示できます。 

## <a name="delete-managed-google-play-apps"></a>managed Google Play アプリを削除する
必要に応じて、Microsoft Intune から managed Google Play アプリを削除できます。 マネージド Google Play アプリを削除するには、Azure portal で Microsoft Intune を開き、 **[アプリ]**  >  **[すべてのアプリ]** を選択します。 アプリの一覧から、managed Google Play アプリの右側にある省略記号 (...) を選択し、表示された一覧で **[削除]** を選択します。 アプリの一覧からマネージド Google Play アプリを削除すると、そのマネージド Google Play アプリは自動的に未承認になります。

> [!NOTE]
> アプリが承認されていなくても、マネージド Google Play ストアから削除されていても、Intune クライアント アプリの一覧から削除されることはありません。 それにより、アプリが承認されていない場合でも、アンインストール ポリシーの対象をユーザーに設定できます。

## <a name="android-enterprise-system-apps"></a>Android エンタープライズ システム アプリ

[Android Enterprise 専用デバイス](../enrollment/android-kiosk-enroll.md)または[フル マネージド デバイス](../enrollment/android-fully-managed-enroll.md)に対して、Android Enterprise システム アプリを有効化できます。 詳細については、「[Add Android Enterprise system apps to Microsoft Intune (Android Enterprise システム アプリを Microsoft Intune に追加する)](apps-ae-system.md)」を参照してください。

## <a name="next-steps"></a>次のステップ

- [アプリをグループに割り当てる](apps-deploy.md)
