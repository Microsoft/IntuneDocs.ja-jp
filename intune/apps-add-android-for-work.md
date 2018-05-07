---
title: Android for Work デバイスへのアプリの割り当て
titlesuffix: Microsoft Intune
description: このトピックでは、Google Play for Work ストアから Android for Work デバイスにアプリを同期してから割り当てる方法を説明します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 2f6c06bf-e29a-4715-937b-1d2c7cf663d4
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 1742c33642667a9e7b8ca2f780094345959cd86c
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="assign-apps-to-android-for-work-devices-with-intune"></a>Intune を使用してアプリを Android for Work デバイスに割り当てる

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Android for Work とは、Android デバイス用のプログラムです。 Android for Work デバイスにインストールするすべてのアプリは、Google Play for Work ストアから入手します。 Android for Work デバイスにアプリを割り当てる方法は、標準の Android デバイスに割り当てる場合と異なります。 ストアにサインインし、目的のアプリを検索し、アプリを承認します。 承認後、アプリが Azure Portal の **[ライセンスされたアプリ]** ノードに表示されます。他のアプリと同様にアプリの割り当てを管理できます。

また、独自の基幹業務 (LOB) アプリを作成している場合は、以下の手順でアプリを割り当てることができます。
- Google Play ストアの非公開領域にアプリを公開できる Google Developer アカウントにサインアップする。
- そのアプリを Intune と同期する。

## <a name="before-you-start"></a>開始する前に

Intune と Android for Work が Azure Portal の **[デバイスの登録]** ワークロードで連携するように構成されていることを確認します。

## <a name="synchronize-an-app-from-the-google-play-for-work-store"></a>Google Play for Work ストアのアプリを同期する

1. [Google Play for Work ストア](https://play.google.com/work)にアクセスします。 Intune と Android for Work 間の接続を構成するときに使用したものと同じアカウントでサインインします。
2. Intune を使用して割り当てるアプリをストアで検索します。
3. アプリが表示されるページで、**[承認]** を選択します。  
    Microsoft Excel アプリが選択されている例を次に示します。

    ![Google Play for Work ストアの [承認] ボタン](media/approve.png)
    
   多様な操作を実行するアクセス許可をアプリに付与するように求めるウィンドウが開きます。 

4. **[承認]** を選択し、アプリのアクセス許可に同意して続行します。

    ![アプリのアクセス許可の [承認] ボタン](media/approve-app-permissions.png)

5. 新しいアプリのアクセス許可要求を処理するオプションを選択し、**[保存]** を選択します。

    ![新しいアプリのアクセス許可要求を処理するオプション](media/approve-app-settings.png)

    アプリは承認され、IT 管理者コンソールに表示されます。 次に、[Intune と Android for Work アプリを同期する](apps-add-android-for-work.md#sync-an-android-for-work-app-with-intune)ことができます。 

## <a name="sync-an-android-for-work-app-with-intune"></a>Intune と Android for Work アプリを同期する

ストアのアプリを承認しても、**[モバイル アプリ]** ワークロードの **[ライセンスされたアプリ]** ノードに表示されない場合は、次の手順で強制的に即時に同期します。

1. [Azure ポータル](https://portal.azure.com)にサインインします。
2. **[すべてのサービス]** > **[Intune]** の順に選択します。 Intune は **[監視 + 管理]** セクションにあります。
3. **[Intune]** ウィンドウで、**[モバイル アプリ]** を選択します。
4. **[モバイル アプリ]** ワークロード ウィンドウの **[設定]** で **[Android for Work]** を選択します。
5. **[Android for Work]** ウィンドウで、**[同期]** を選択します。  
    ページで、前回の同期の時刻と状態が更新されます。
6. **[モバイル アプリ]** ワークロード ウィンドウで、**[アプリ]** を選択します。  
    新しく使用できるようになった Android for Work アプリが表示されます。

アプリが **[モバイル アプリ]** ワークロード ウィンドウの **[アプリ ライセンス]** ノードに表示される場合は、[他のアプリの割り当てと同様の方法でアプリを割り当てることができます](/intune-azure/manage-apps/deploy-apps)。 ユーザーのグループに対してのみアプリを割り当てることができます。

アプリを割り当てると、アプリは対象のデバイスにインストールされます。 デバイスのユーザーがインストールの承認を求められることはありません。

## <a name="manage-android-for-work-app-permissions"></a>Android for Work アプリのアクセス許可の管理
Android for Work では、Intune にアプリを同期してユーザーに割り当てる前に、管理対象の Google Play Web コンソールでアプリを承認する必要があります。 Android for Work により、これらのアプリがユーザーのデバイスに通知なしで自動的にプッシュできるようになるため、ユーザー全員に代わってアプリへのアクセスを許可する必要があります。 ユーザーがアプリをインストールする際はアプリのアクセス許可に関する表示が行われないため、これらのアクセス許可について学習し、理解する必要があります。

アプリ開発者がアプリの新しいバージョンを公開する際、以前のバージョンのアクセスを許可していても、新しいバージョンのアクセスは自動的に許可されません。 以前のバージョンのアプリを実行しているデバイスは、そのアプリを引き続き使用できます。 ただし、新しいアクセス許可が承認されるまで、アプリはアップグレードされません。 アプリをインストールしていないデバイスでは、アプリの新しいアクセス許可を承認するまで、アプリをインストールしません。

### <a name="update-app-permissions"></a>アプリのアクセス許可を更新する

管理対象の Google Play コンソールに定期的にアクセスして、新しいアクセス許可があるかどうか確認してください。 承認されたアプリに新しいアクセス許可が必要な場合は、自分や他のユーザーに電子メールを送信するように Google Play を構成できます。 アプリを割り当ててもデバイスにインストールされていない場合は、次の手順を実行して新しいアクセス許可を確認します。

1. [Google Play](http://play.google.com/work) に移動します。
2. アプリを公開して承認する際に使用した Google アカウントでサインインします。
3. **[更新]** タブを選択し、更新が必要なアプリがあるかどうかを確認します。  
    一覧にあるアプリでは新しいアクセス許可が必要で、それらが適用されるまで割り当てられません。

あるいは、Google Play を構成することで、アプリごとにアクセス許可を自動的に再許可できます。 

## <a name="working-with-a-line-of-business-app-from-the-google-play-for-work-store"></a>Google Play for Work ストアの基幹業務アプリを使用する

1. Intune と Android for Work 間の接続を構成するときに使用したものと同じアカウントで、[Google Play Developer Console](https://play.google.com/apps/publish) にサインインします。  
    初めてサインインする場合は、Google Developer プログラムに登録し、料金を払ってメンバーになる必要があります。
2. コンソールで、**[Add new application]\(新しいアプリケーションの追加\)** を選択します。
3. アプリをアップロードし、アプリに関する情報を提供する方法は、アプリを Google Play ストアに公開する方法と同じです。 ただし、**[Only make this application available to my organization (<*organization name*>)]\(このアプリケーションを自分の組織 (<組織名>) のみが入手できるようにする\)** を選択する必要があります。

    ![組織のみがアプリを入手できるようにする](media/restrict.png)

    この操作により、自分の組織のみがアプリを入手でき、公開されている Google Play ストアでは入手できないようになります。

    Android アプリのアップロードと公開の詳細については、[Google Developer Console のヘルプ](https://support.google.com/googleplay/android-developer/answer/113469)を参照してください。
4. アプリを公開したら、Intune と Android for Work 間の接続を構成したときと同じアカウントを使用して [Google Play for Work ストア](https://play.google.com/work)にログインします。
5. ストアの **[アプリ]** ノードに、公開したアプリが表示されることを確認します。  
    アプリは自動的に承認され、Intune と同期されます。

## <a name="next-steps"></a>次の手順

- [アプリをグループに割り当てる](apps-deploy.md) 

