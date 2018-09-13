---
title: Android 仕事用プロファイルのデバイスにアプリを割り当てる
titlesuffix: Microsoft Intune
description: Managed Google Play ストアから Android 仕事用プロファイルのデバイスにアプリを同期してから割り当てる方法を説明します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 06/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 2f6c06bf-e29a-4715-937b-1d2c7cf663d4
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: faa8918441bd705875fcdc72d3717af001ab2b85
ms.sourcegitcommit: e814cfbbefe818be3254ef6f859a7bf5f5b99123
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/31/2018
ms.locfileid: "43329872"
---
# <a name="assign-apps-to-android-work-profile-devices-with-intune"></a>Intune で Android 仕事用プロファイルのデバイスにアプリを割り当てる

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Android Enterprise は、Android 仕事用プロファイルのデバイスおよび Kiosk デバイス用のプログラムです。 Android 仕事用プロファイルのデバイスの場合、Android Enterprise は、仕事用のアプリとデータから個人用のアプリとデータを分離する機能とサービスのセットです。 Android Enterprise は、ユーザーが仕事に Android デバイスを使用するときの追加の管理オプションとプライバシーを提供します。 Intune を使用すると、アプリと設定を Android 仕事用プロファイルのデバイスに展開し、仕事の情報と個人の情報を分けることができます。 Android 仕事用プロファイルのデバイスにインストールするすべてのアプリは、Managed Google Play ストアから入手します。 Android 仕事用プロファイルのデバイスにアプリを割り当てる方法は、標準の Android デバイスに割り当てる場合と異なります。 ストアにサインインし、目的のアプリを検索し、アプリを承認します。 承認後、アプリが Azure Portal の **[ライセンスされたアプリ]** ノードに表示されます。他のアプリと同様にアプリの割り当てを管理できます。

また、独自の基幹業務 (LOB) アプリを作成している場合は、以下の手順でアプリを割り当てることができます。
- Google Play ストアの非公開領域にアプリを公開できる Google Developer アカウントにサインアップする。
- そのアプリを Intune と同期する。

## <a name="before-you-start"></a>開始する前に

Intune と Android 仕事用プロファイルが Azure Portal の **[デバイスの登録]** ワークロードで連携するように構成されていることを確認します。 詳細については、「[Android デバイスの登録](android-work-profile-enroll.md)」を参照してください。

## <a name="synchronize-an-app-from-the-managed-google-play-store"></a>Managed Google Play ストアのアプリを同期する

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

    アプリは承認され、IT 管理者コンソールに表示されます。 次に、[Intune と Android 仕事用プロファイルのアプリを同期する](apps-add-android-for-work.md#sync-an-android-for-work-app-with-intune)ことができます。 

## <a name="sync-a-managed-google-play-app-with-intune"></a>Intune で Managed Google Play のアプリを同期する

ストアのアプリを承認しても、**[クライアント アプリ]** ワークロードの **[ライセンスされたアプリ]** ノードに表示されない場合は、次の手順で強制的に即時に同期します。

1. [Azure ポータル](https://portal.azure.com)にサインインします。
2. **[すべてのサービス]** > **[Intune]** の順に選択します。 Intune は **[監視 + 管理]** セクションにあります。
3. **[Intune]** ウィンドウで、**[クライアント アプリ]** を選択します。
4. **[クライアント アプリ]** ワークロード ウィンドウの **[セットアップ]** で **[Managed Google Play]** を選択します。
5. **[Managed Google Play]** ウィンドウで、**[更新]** を選択します。  
    ページで、前回の同期の時刻と状態が更新されます。
6. **[クライアント アプリ]** ワークロード ウィンドウで、**[アプリ]** を選択します。  
    新しく使用可能になった Managed Google Play アプリが表示されます。

アプリが **[クライアント アプリ]** ワークロード ウィンドウの **[アプリ ライセンス]** ノードに表示される場合は、[他のアプリの割り当てと同様の方法でアプリを割り当てることができます](/intune-azure/manage-apps/deploy-apps)。 ユーザーのグループに対してのみアプリを割り当てることができます。

アプリを割り当てると、アプリは対象のデバイスにインストールされます。 デバイスのユーザーがインストールの承認を求められることはありません。

## <a name="manage-android-enterprise-app-permissions"></a>Android Enterprise アプリのアクセス許可の管理
Android Enterprise では、Intune にアプリを同期してユーザーに割り当てる前に、managed Google Play Web コンソールでアプリを承認する必要があります。 Android Enterprise により、これらのアプリがユーザーのデバイスに通知なしで自動的にプッシュできるようになるため、ユーザー全員に代わってアプリへのアクセスを許可する必要があります。 ユーザーがアプリをインストールする際はアプリのアクセス許可に関する表示が行われないため、これらのアクセス許可について理解する必要があります。

アプリ開発者がアプリの新しいバージョンでアクセス許可を更新した場合、以前のアクセス許可を承認していても、アクセスは自動的に許可されません。 以前のバージョンのアプリを実行しているデバイスは、そのアプリを引き続き使用できます。 ただし、新しいアクセス許可が承認されるまで、アプリはアップグレードされません。 アプリをインストールしていないデバイスでは、アプリの新しいアクセス許可を承認するまで、アプリをインストールしません。

### <a name="update-app-permissions"></a>アプリのアクセス許可を更新する

管理対象の Google Play コンソールに定期的にアクセスして、新しいアクセス許可があるかどうか確認してください。 承認されたアプリに新しいアクセス許可が必要な場合は、自分や他のユーザーに電子メールを送信するように Google Play を構成できます。 アプリを割り当ててもデバイスにインストールされていない場合は、次の手順を実行して新しいアクセス許可を確認します。

1. [Google Play](http://play.google.com/work) に移動します。
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

## <a name="next-steps"></a>次の手順

- [アプリをグループに割り当てる](apps-deploy.md) 

