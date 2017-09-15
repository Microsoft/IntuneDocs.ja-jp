---
title: "Android for Work デバイスへのアプリの割り当て"
titlesuffix: Azure portal
description: "このトピックでは、Google Play for Work ストアから Android for Work デバイスにアプリを同期してから割り当てます。\""
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 06/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2f6c06bf-e29a-4715-937b-1d2c7cf663d4
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 803f1475a220e52a0f7d8a41d58f0a5337ff6555
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/09/2017
---
# <a name="how-to-assign-apps-to-android-for-work-devices-with-intune"></a>Intune を使用してアプリを Android for Work デバイスに割り当てる方法

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Android for Work デバイスにアプリを割り当てる方法は、標準の Android デバイスに割り当てる場合と異なります。 Android for Work 用にインストールするすべてのアプリは、Google Play for Work ストアから入手します。 ストアにログオンし、目的のアプリを検索し、アプリを承認します。
Azure Portal の **[ライセンスされたアプリ]** ノードにアプリが表示されます。 ここでアプリの割り当てを管理する方法は、他のアプリを割り当てる方法と同じです。

また、独自の基幹業務 (LOB) アプリを作成している場合は、以下の手順でアプリを割り当てることができます。
- Google Play ストアの非公開領域にアプリを公開できる Google Developer アカウントにサインアップする。
- そのアプリを Intune と同期する。

## <a name="before-you-start"></a>アップグレードを開始する前に

Intune と Android for Work が Azure Portal の **[デバイスの登録]** ワークロードで連携するように構成されていることを確認します。

## <a name="synchronize-an-app-from-the-google-play-for-work-store"></a>Google Play for Work ストアのアプリを同期する

1. [Google Play for Work ストア](https://play.google.com/work)にアクセスします。 Intune と Android for Work 間の接続を構成するときに使用したものと同じアカウントでサインインします。
2. Intune を使用して割り当てるアプリをストアで検索します。
3. 選択するアプリのページで、**[承認]** を選択します。 この例では、Microsoft Excel アプリを選択しました。<br>
  ![アプリの承認例](media/approve.png)
4. 多様な操作を実行するアクセス許可をアプリに付与するように求めるウィンドウが開きます。 続行するには、**[承認]** を選択します。<br>
  ![アプリのアクセス許可の承認例](media/approve-app-permissions.png)
5. アプリは承認され、IT 管理者コンソールに表示されます。

## <a name="publish-then-synchronize-a-line-of-business-app-from-the-google-play-for-work-store"></a>Google Play for Work ストアから基幹業務アプリを公開し、同期する

1. Google Play Developer Console で、[play.google.com/apps/publish](https://play.google.com/apps/publish) を開きます。
2. Intune と Android for Work 間の接続を構成するときに使用したものと同じアカウントでサインインします。 初めてサインインする場合は、Google Developer プログラムに登録し、料金を払ってメンバーになる必要があります。
3. コンソールで、**[Add new application]** (新しいアプリケーションの追加) を選択します。
4. アプリをアップロードし、アプリに関する情報を提供する方法は、アプリを Google Play ストアに公開する方法と同じです。 ただし、**[Only make this application available to my organization (<*organization name*>)]\(このアプリケーションを自分の組織 (<組織名>) のみが入手できるようにする\) の設定を選択する必要があります**。<br>
  ![組織のみがアプリを入手できるようにするためのオプション](media/restrict.png)<br>
この操作により、自分の組織のみがアプリを入手でき、公開されている Google Play ストアでは入手できないようになります。
Android アプリのアップロードと公開の詳細については、[Google Developer Console のヘルプ](https://support.google.com/googleplay/android-developer/answer/113469)を参照してください。
5. アプリを公開したら、[Google Play for Work ストア](https://play.google.com/work)にアクセスします。 Intune と Android for Work 間の接続を構成するときに使用したものと同じアカウントでサインインします。
6. ストアの **[アプリ]** ノードに、公開したアプリが表示されることを確認します。 アプリは自動的に承認され、Intune と同期されます。

## <a name="assign-an-android-for-work-app"></a>Android for Work アプリを割り当てる

ストアのアプリを承認しても、**[モバイル アプリ]** ワークロードの **[ライセンスされたアプリ]** ノードに表示されない場合は、次の手順で強制的に即時に同期します。

1. Azure ポータルにサインインします。
2. **[Intune]** ブレードで、**[モバイル アプリ]** を選択します。
3. **[モバイル アプリ]** ワークロードで、**[セットアップ]** > **[Android for Work]** の順に選択します。
4. [Android for Work] ブレードです、**[今すぐ同期]** を選択します。
5. ページには、前回の同期の時刻と状態も表示されます。

アプリが **[モバイル アプリ]** ワークロードの **[ライセンスされたアプリ]** ノードに表示される場合は、[他のアプリの割り当てと同様の方法でアプリを割り当てることができます](/intune-azure/manage-apps/deploy-apps)。 ユーザーのグループに対してのみアプリを割り当てることができます。

アプリを割り当てると、アプリは対象のデバイスにインストールされます。 デバイスのユーザーがインストールの承認を求められることはありません。

## <a name="manage-android-for-work-app-permissions"></a>Android for Work アプリのアクセス許可の管理
Android for Work では、Intune にアプリを同期してユーザーに割り当てる前に、Google が管理する Web コンソールの Play でアプリを承認する必要があります。  Android for Work により、これらのアプリがユーザーのデバイスに通知なしで自動的にプッシュできるようになるため、ユーザー全員に代わってアプリへのアクセスを許可する必要があります。  エンド ユーザーがインストールする際はアプリのアクセス許可に関する表示が行われないため、これらのアクセス許可について学習し、理解する必要があります。

アプリ開発者がアプリの新しいバージョンを公開する際、以前のバージョンのアクセスを許可していても、新しいバージョンのアクセスは自動的に許可されません。 古いバージョンのアプリを実行しているデバイスは、そのアプリを引き続き使用できます。 ただし、新しいアクセス許可が承認されるまで、アプリはアップグレードされません。 アプリをインストールしていないデバイスでは、アプリの新しいアクセス許可を承認するまで、アプリをインストールしません。

### <a name="how-to-update-app-permissions"></a>アプリのアクセス許可を更新する方法

管理対象の Google Play コンソールに定期的にアクセスして、新しいアクセス許可があるかどうか確認してください。 承認済みのアプリに新しいアクセス許可が必要な場合は、Google Play を構成して、自分や他のユーザーあてに電子メールを送信できます。 アプリを割り当ててもデバイスにインストールされていない場合は、まだ許可していないアクセス許可が新しくあるかどうかを、次の手順で確認します。

1. http://play.google.com/work にアクセスします。
2. アプリを公開して承認する際に使用した Google アカウントでサインインします。
3. **[更新]** タブにアクセスして、更新が必要なアプリがないかどうかを確認します。  一覧にあるアプリでは新しいアクセス許可が必要で、それらが適用されるまで割り当てられません。  

あるいは、Google Play を構成することで、アプリごとにアクセス許可を自動的に再許可できます。 



