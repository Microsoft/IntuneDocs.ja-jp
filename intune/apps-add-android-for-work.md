---
title: マネージド Google Play アプリを Android エンタープライズ デバイスに割り当てる
titleSuffix: Microsoft Intune
description: マネージド Google Play ストアから Android エンタープライズ デバイスにアプリを同期してから割り当てる方法について説明します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/15/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2f6c06bf-e29a-4715-937b-1d2c7cf663d4
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1ad07252ccf10fefdd1c753ab103eb91a2789c39
ms.sourcegitcommit: 8c795b041cd39e3896595f64f53ace48be0ec84c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2019
ms.locfileid: "59587350"
---
# <a name="add-managed-google-play-apps-to-android-enterprise-devices-with-intune"></a>Intune で managed Google Play アプリを Android エンタープライズ デバイスに追加する

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Android エンタープライズは、Android 仕事用プロファイル デバイス、専用/キオスク デバイス、および完全に管理されたデバイス用のプログラムです。 Android 仕事用プロファイルのデバイスの場合、Android Enterprise は、仕事用のアプリとデータから個人用のアプリとデータを分離する機能とサービスのセットです。 Android Enterprise は、ユーザーが仕事に Android デバイスを使用するときの追加の管理オプションとプライバシーを提供します。 Intune を使用すると、アプリと設定を Android 仕事用プロファイルのデバイスに展開し、仕事の情報と個人の情報を分けることができます。 Android 仕事用プロファイルのデバイスにインストールするすべてのアプリは、Managed Google Play ストアから入手します。 Android 仕事用プロファイルのデバイスにアプリを割り当てる方法は、標準の Android デバイスに割り当てる場合と異なります。 ストアにサインインし、目的のアプリを検索し、アプリを承認します。 承認後、アプリが Azure Portal の **[ライセンスされたアプリ]** ノードに表示されます。他のアプリと同様にアプリの割り当てを管理できます。

また、独自の基幹業務 (LOB) アプリを作成している場合は、以下の手順でアプリを割り当てることができます。
- Google Play ストアの非公開領域にアプリを公開できる Google Developer アカウントにサインアップする。
- そのアプリを Intune と同期する。

## <a name="before-you-start"></a>開始する前に

Intune と Android 仕事用プロファイルが Azure Portal の **[デバイスの登録]** ワークロードで連携するように構成されていることを確認します。 詳細については、「[Android デバイスの登録](android-work-profile-enroll.md)」を参照してください。

>[!NOTE]
>Microsoft Intune を使うときは、Microsoft Edge または Google Chrome ブラウザーを使うことをお勧めします。

## <a name="managed-google-play-app-type"></a>managed Google Play アプリの種類
アプリの種類を **[managed Google Play]** にすると、特定の [managed Google Play アプリ](https://play.google.com/work/search?q=microsoft&c=apps)を Intune に追加できます。 Intune の管理者は、Intune 内で managed Google Play アプリを参照、検索、承認、同期および割り当てできるようになりました。  managed Google Play コンソールに別途移動する必要はなく、また再認証する必要もありません。

> [!NOTE]
> managed Google Play アプリと Intune を同期させる場合は、[「managed Google Play アプリを Intune と同期する」](apps-add-android-for-work.md#synchronize-a-managed-google-play-app-with-intune-alternative)を参照してください。

## <a name="add-a-managed-google-play-app-using-intune"></a>Intune を使用して managed Google Play アプリを追加する

1. [Azure ポータル](https://portal.azure.com)にサインインします。
2. **[すべてのサービス]** > **[Intune]** の順に選択します。  
    Intune は **[監視 + 管理]** セクションにあります。
3. **[Intune]** ウィンドウで、**[クライアント アプリ]** > **[アプリ]** の順に選択します。
5. **[アプリ]** ウィンドウで **[追加]** を選択します。
6. **[アプリケーションの種類]** ドロップダウン ボックスで、**[managed Google Play]** を選択します。
7. **[Managed Google Play - Approve]\(managed Google Play - 承認\)** を選択して、managed Google Play カタログを開きます。
8. 検索ボックスを使って、追加するアプリを検索します。
9. **[承認]** をクリックして managed Google Play 内のアプリを承認し、**[承認]** をクリックしてアプリのアクセス許可を受け入れます。
10. [承認の設定] ウィンドウで **[Keep approved when app requests new permissions]\(アプリが新しいアクセス許可を要求したときに承認済みのままにする\)** を選び、**[保存]** をクリックします。 このオプションを選択しない場合、アプリの開発者が更新プログラムを発行した場合に、新しいアクセス許可をすべて手動で承認することが必要になります。  これにより、アクセス許可が承認されるまでアプリのインストールと更新が停止されます。 このため、新しいアクセス許可を自動的に承認するオプションを選択することをお勧めします。 
11. **[OK]** をクリックして、承認済みのアプリを追加します。
12. **[アプリの追加]** ウィンドウの **[同期]** をクリックして、managed Google Play サービスと同期します。

## <a name="synchronize-a-managed-google-play-app-with-intune-alternative"></a>managed Google Play アプリを Intune と同期する (代替)
Intune を使用して直接追加するのではなく、managed Google Play アプリを Intune と同期する場合は、次の手順を実行します。

> [!IMPORTANT]
> 以下の情報は、前述の Intune を使用した managed Google Play アプリの追加の代替方法です。

### <a name="synchronize-an-app-from-the-managed-google-play-store"></a>Managed Google Play ストアのアプリを同期する

1. [Managed Google Play ストア](https://play.google.com/work)に移動します。 Intune と Android Enterprise 間の接続を構成するときに使用したものと同じアカウントでサインインします。
2. Intune を使用して割り当てるアプリをストアで検索します。
3. アプリが表示されるページで、**[承認]** を選択します。  
    Microsoft Excel アプリが選択されている例を次に示します。

    ![Managed Google Play ストアの [承認] ボタン](media/approve.png)

   多様な操作を実行するアクセス許可をアプリに付与するように求めるウィンドウが開きます。

4. **[承認]** を選択し、アプリのアクセス許可に同意して続行します。

    ![アプリのアクセス許可の [承認] ボタン](media/approve-app-permissions.png)

5. 新しいアプリのアクセス許可要求を処理するオプションを選択し、**[保存]** を選択します。

    ![新しいアプリのアクセス許可要求を処理するオプション](media/approve-app-settings.png)

    アプリは承認され、IT 管理者コンソールに表示されます。 次に、[Intune と Android 仕事用プロファイルのアプリを同期する](apps-add-android-for-work.md#sync-a-managed-google-play-app-with-intune)ことができます。

### <a name="sync-a-managed-google-play-app-with-intune"></a>Intune で Managed Google Play のアプリを同期する

ストアのアプリを承認しても、**[クライアント アプリ]** ワークロードの **[ライセンスされたアプリ]** ノードに表示されない場合は、次の手順で強制的に即時に同期します。

1. [Azure ポータル](https://portal.azure.com)にサインインします。
2. **[すべてのサービス]** > **[Intune]** の順に選択します。 Intune は **[監視 + 管理]** セクションにあります。
3. **[Intune]** ウィンドウで、**[クライアント アプリ]** を選択します。
4. **[クライアント アプリ]** ワークロード ウィンドウの **[セットアップ]** で **[Managed Google Play]** を選択します。
5. **[Managed Google Play]** ウィンドウで、**[更新]** を選択します。  
    ページで、前回の同期の時刻と状態が更新されます。
6. **[クライアント アプリ]** ワークロード ウィンドウで、**[アプリ]** を選択します。  
    新しく使用可能になった Managed Google Play アプリが表示されます。

## <a name="assigning-the-managed-google-play-app"></a>managed Google Play ストアの割り当て

アプリが **[クライアント アプリ]** ワークロード ウィンドウの **[アプリ ライセンス]** ノードに表示される場合は、アプリをユーザーのグループに割り当てることで、[他のアプリの割り当てと同様の方法でアプリを割り当てることができます](/intune-azure/manage-apps/deploy-apps)。

アプリを割り当てると、アプリは対象のデバイスにインストールされます。 デバイスのユーザーがインストールの承認を求められることはありません。

## <a name="manage-android-enterprise-app-permissions"></a>Android Enterprise アプリのアクセス許可の管理
Android Enterprise では、Intune にアプリを同期してユーザーに割り当てる前に、managed Google Play Web コンソールでアプリを承認する必要があります。 Android Enterprise により、これらのアプリがユーザーのデバイスに通知なしで自動的にプッシュできるようになるため、ユーザー全員に代わってアプリへのアクセスを許可する必要があります。 ユーザーがアプリをインストールする際はアプリのアクセス許可に関する表示が行われないため、これらのアクセス許可について理解する必要があります。

アプリ開発者がアプリの新しいバージョンでアクセス許可を更新した場合、以前のアクセス許可を承認していても、アクセスは自動的に許可されません。 以前のバージョンのアプリを実行しているデバイスは、そのアプリを引き続き使用できます。 ただし、新しいアクセス許可が承認されるまで、アプリはアップグレードされません。 アプリをインストールしていないデバイスでは、アプリの新しいアクセス許可を承認するまで、アプリをインストールしません。

### <a name="update-app-permissions"></a>アプリのアクセス許可を更新する

管理対象の Google Play コンソールに定期的にアクセスして、新しいアクセス許可があるかどうか確認してください。 承認されたアプリに新しいアクセス許可が必要な場合は、自分や他のユーザーに電子メールを送信するように Google Play を構成できます。 アプリを割り当ててもデバイスにインストールされていない場合は、次の手順を実行して新しいアクセス許可を確認します。

1. [Google Play](https://play.google.com/work) に移動します。
2. アプリを公開して承認する際に使用した Google アカウントでサインインします。
3. **[更新]** タブを選択し、更新が必要なアプリがあるかどうかを確認します。  
    一覧にあるアプリでは新しいアクセス許可が必要で、それらが適用されるまで割り当てられません。

あるいは、Google Play を構成することで、アプリごとにアクセス許可を自動的に再許可できます。

## <a name="working-with-a-line-of-business-app-from-the-managed-google-play-store"></a>Managed Google Play ストアの基幹業務アプリを使用する

1. Intune と Android Enterprise 間の接続を構成するときに使用したものと同じアカウントで、[Google Play Developer Console](https://play.google.com/apps/publish) にサインインします。  
    初めてサインインする場合は、Google Developer プログラムに登録し、料金を払ってメンバーになる必要があります。
2. コンソールで、**[Add new application]\(新しいアプリケーションの追加\)** を選択します。
3. アプリをアップロードし、アプリに関する情報を提供する方法は、アプリを Google Play ストアに公開する方法と同じです。 ただし、**[Only make this application available to my organization (<*organization name*>)]\(このアプリケーションを自分の組織 (<組織名>) のみが入手できるようにする\)** を選択する必要があります。

    ![組織のみがアプリを入手できるようにする](media/restrict.png)

    この操作により、自分の組織のみがアプリを入手できるようにします。 これは一般の Google Play ストアでは使用できません。

    Android アプリのアップロードと公開の詳細については、[Google Developer Console のヘルプ](https://support.google.com/googleplay/android-developer/answer/113469)を参照してください。
4. アプリを公開したら、Intune と Android Enterprise 間の接続を構成したときと同じアカウントを使用して [Managed Google Play ストア](https://play.google.com/work)にログインします。
5. ストアの **[アプリ]** ノードに、公開したアプリが表示されることを確認します。  
    アプリは自動的に承認され、Intune と同期されます。

## <a name="delete-managed-google-play-apps"></a>managed Google Play アプリを削除する
必要に応じて、Microsoft Intune から managed Google Play アプリを削除できます。 managed Google Play アプリを削除するには、Azure portal で Microsoft Intune を開き、**[クライアント アプリ]** > **[アプリ]** の順に選択します。 アプリの一覧から、managed Google Play アプリの右側にある省略記号 (...) を選択し、表示された一覧で **[削除]** を選択します。 アプリの一覧からマネージド Google Play アプリを削除すると、そのマネージド Google Play アプリは自動的に未承認になります。

## <a name="next-steps"></a>次の手順

- [アプリをグループに割り当てる](apps-deploy.md)
