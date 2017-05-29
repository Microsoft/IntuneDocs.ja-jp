---
title: "アプリを Android for Work デバイスに割り当てる | Microsoft Docs"
titleSuffix: Intune Azure preview
description: "Intune Azure プレビュー: このトピックでは、Google Play for Work ストアから Android for Work デバイスにアプリを同期し、割り当てます。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2f6c06bf-e29a-4715-937b-1d2c7cf663d4
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 49e86ab665d9022739c0330092734ba897ea3b02
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017


---

# <a name="how-to-assign-apps-to-android-for-work-devices-with-intune"></a>Intune を使用してアプリを Android for Work デバイスに割り当てる方法

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Android for Work デバイスにアプリを割り当てる方法は、標準の Android デバイスに割り当てる場合と異なります。 Android for Work 用にインストールするすべてのアプリは、Google Play for Work ストアから入手します。 ストアにログインし、目的のアプリを検索し、承認します。
Intune ポータルの **[ライセンスされたアプリ]** ノードにアプリが表示されます。 ここでアプリの割り当てを管理する方法は、他のアプリを割り当てる方法と同じです。

また、独自の基幹業務 (LOB) アプリを作成している場合、そのアプリも割り当てることができます。 LOB アプリを展開するには、Google Developer アカウントにサインアップする必要があります。サインアップすると、Google Play ストアの非公開領域にアプリを公開し、Intune と同期できるようになります。

## <a name="before-you-start"></a>アップグレードを開始する前に

Intune ポータルの **[デバイスの登録]** ワークロードで連携して動作するように、Intune と Android for Work を構成します。

## <a name="synchronize-an-app-from-the-google-play-for-work-store"></a>Google Play for Work ストアのアプリを同期する


1. [Google Play for Work ストア](https://play.google.com/work)にアクセスします。 Intune と Android for Work 間の接続を構成するときに使用したものと同じアカウントでサインインします。
2. Intune を使用して割り当てるアプリをストアで検索します。
3. 選択するアプリのページで、**[承認]** を選択します。 この例では、Microsoft Excel アプリを選択しました。<br>
  ![アプリの承認例](media/approve.png)
4. 多様な操作を実行するアクセス許可をアプリに付与するように求めるウィンドウが開きます。 続行するには、**[承認]** を選択する必要があります。<br>
  ![アプリのアクセス許可の承認例](media/approve-app-permissions.png)
5. しばらくすると、アプリが承認され、IT 管理コンソールで使用できるようになったことを示す確認メッセージが表示されます。

## <a name="publish-then-synchronize-a-line-of-business-app-from-the-google-play-for-work-store"></a>Google Play for Work ストアから基幹業務アプリを公開し、同期する

1. Google Play Developer Console で、[play.google.com/apps/publish](https://play.google.com/apps/publish) を開きます。
2. Intune と Android for Work 間の接続を構成するときに使用したものと同じアカウントでサインインします。 初めてサインインする場合は、Google Developer プログラムに登録し、料金を払ってメンバーになる必要があります。
3. コンソールで、**[Add new application]** (新しいアプリケーションの追加) を選択します。
4. アプリをアップロードし、アプリに関する情報を提供する方法は、アプリを Google Play ストアに公開する方法と同じです。 ただし、次の図のように、 **[ Only make this application available to my organization (<* 組織名* >) ]** \(このアプリケーションを自分の組織 (<組織名>) のみが入手できるようにする) 設定を選択する必要があります。 <br>
  ![組織のみがアプリを入手できるようにするためのオプション](media/restrict.png)<br>
このオプションをオンにすると、自分の組織のみがアプリを入手でき、公開されている Google Play ストアでは入手できないようになります。
Android アプリのアップロードと公開の詳細については、[Google Developer Console のヘルプ](https://support.google.com/googleplay/android-developer/answer/113469)を参照してください。
5. アプリを公開したら、[Google Play for Work ストア](https://play.google.com/work)にアクセスします。 Intune と Android for Work 間の接続を構成するときに使用したものと同じアカウントでサインインします。
6. ストアの **[アプリ]** ノードに、公開したアプリが表示されることを確認します。 アプリは自動的に承認され、Intune と同期されます。

## <a name="assign-an-android-for-work-app"></a>Android for Work アプリを割り当てる

ストアのアプリを承認しても、**[モバイル アプリ]** ワークロードの **[ライセンスされたアプリ]** ノードに表示されない場合、次の手順で即時の同期を強制できます。

1. Azure ポータルにサインインします。
2. **[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
3. **[Intune]** ブレードで、**[モバイル アプリ]** を選択します。
4. **[モバイル アプリ]** ワークロードで、**[セットアップ]** > **[Android for Work]** の順に選択します。
5. [Android for Work] ブレードです、**[今すぐ同期]** を選択します。
6. ページには、前回の同期の時刻と状態も表示されます。

アプリが **[モバイル アプリ]** ワークロードの **[ライセンスされたアプリ]** ノードに表示される場合、[他のアプリと同様の方法でアプリを割り当てることができます](/intune-azure/manage-apps/deploy-apps)。 ユーザーのグループに対してのみアプリを割り当てることができます。

アプリを割り当てると、アプリは対象のデバイスにインストールされます。 デバイスのユーザーにインストールの承認が求められることはありません。

## <a name="manage-app-permissions"></a>アプリのアクセス許可の管理
Android for Work では、Intune にアプリを同期してユーザーに割り当てる前に、Google が管理する Web コンソールの Play でアプリを承認する必要があります。  Android for Work により、これらのアプリがユーザーのデバイスに通知なしで自動的にプッシュできるようになるため、ユーザー全員に代わってアプリへのアクセスを許可する必要があります。  エンド ユーザーにはアプリのアクセス許可について表示されないため、これらのアクセス許可について読み、理解する必要があります。

アプリ開発者がアプリの新しいバージョンを公開する際、以前のバージョンのアクセスを許可していても、新しいバージョンのアクセスは自動的に許可されません。 アプリの以前のバージョンを実行しているデバイスでも使用できますが、新しくアクセス許可が承認されるまでアプリはアップグレードされません。 アプリをインストールしていないデバイスでは、アプリの新しくアクセス許可を承認するまでアプリをインストールできません。

### <a name="how-to-update-app-permissions"></a>アプリのアクセス許可を更新する方法

管理されている Google Play コンソールに定期的にアクセスして、新しく許可していないアクセスがあるかどうか確認してください。 アプリを割り当ててもデバイスにインストールされていない場合は、まだ許可していないアクセス許可が新しくあるかどうかを、次の手順で確認します。

1. Http://play.google.com/work にアクセスします。
2. アプリを公開して承認する際に使用した Google アカウントでサインインします。
3. **[更新]** タブにアクセスして、更新が必要なアプリがないかどうかを確認します。  一覧にあるアプリでは新しいアクセス許可が必要になります。適用されるまで、割り当てられません。  

