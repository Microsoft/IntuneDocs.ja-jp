---
title: "アプリを Android for Work デバイスに展開する | Microsoft Docs"
description: "このトピックでは、Google Play for Work ストアから Android for Work デバイスにアプリを同期してから展開します。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 03/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: cd0bbd90-d3fe-4efc-83fd-d1f3f86800d4
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 0936051b5c33a2e98f275ef7a3a32be2e8f5a8b0
ms.openlocfilehash: 3b608d42f04b9fce457b6b61587d05ab5d59bb0a
ms.lasthandoff: 03/10/2017


---

# <a name="how-to-deploy-apps-to-android-for-work-devices-with-intune"></a>Intune を使用してアプリを Android for Work デバイスを展開する方法

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Android for Work デバイスにアプリを展開する方法は、標準の Android デバイスに展開する場合と異なります。 Android for Work 用にインストールするすべてのアプリは、Google Play for Work ストアから入手します。 ストアにログインし、目的のアプリを検索し、承認します。
承認したアプリは、Intune コンソールの **[ボリューム購入アプリ]** ノードに表示されます。 ここでアプリの展開を管理する方法は、他のアプリを展開する方法と同じです。

また、独自の基幹業務 (LOB) アプリを作成している場合、そのアプリも展開できます。 LOB アプリを展開するには、Google Developer アカウントにサインアップする必要があります。サインアップすると、Google Play ストアの非公開領域にアプリを公開し、Intune と同期できるようになります。

## <a name="before-you-start"></a>アップグレードを開始する前に

1. Intune コンソールの **[管理者]** タブで連携して動作するように、Intune と Android for Work を構成します。

## <a name="synchronize-an-app-from-the-google-play-for-work-store"></a>Google Play for Work ストアのアプリを同期する


1. [Google Play for Work ストア](https://play.google.com/work)にアクセスします。 Intune と Android for Work 間の接続を構成するときに使用したものと同じアカウントでサインインします。
2. Intune を使用して展開するアプリをストアで検索します。
3. 選択するアプリのページで、**[承認]** を選択します。 この例では、Microsoft Excel アプリを選択しました。<br>
  ![アプリの承認例](media/approve.png)
4. 多様な操作を実行するアクセス許可をアプリに付与するように求めるウィンドウが開きます。 続行するには、**[承認]** を選択する必要があります。<br>
  ![アプリのアクセス許可の承認例](media/approve-app-permissions.png)
5. しばらくすると、アプリが承認され、IT 管理コンソールで使用できるようになったことを示す確認メッセージが表示されます。

## <a name="publish-then-synchronize-a-line-of-business-app-from-the-google-play-for-work-store"></a>Google Play for Work ストアから基幹業務アプリを公開し、同期する

1. Google Play Developer Console で、[play.google.com/apps/publish](https://play.google.com/apps/publish) を開きます。
2. Intune と Android for Work 間の接続を構成するときに使用したものと同じアカウントでサインインします。 初めてサインインする場合は、Google Developer プログラムに登録し、料金を払ってメンバーになる必要があります。
3. コンソールで、**[Add new application]** (新しいアプリケーションの追加) を選択します。
4. アプリをアップロードし、アプリに関する情報を提供する方法は、アプリを Google Play ストアに公開する方法と同じです。 ただし、次の図のように、[ Only make this application available to my organization (< 組織名 >)** ] \(このアプリケーションを自分の組織 (<組織名>) のみが入手できるようにする) 設定を選択する必要があります。****<br>
  ![組織のみがアプリを入手できるようにするためのオプション](media/restrict.png)<br>
このオプションをオンにすると、自分の組織のみがアプリを入手でき、公開されている Google Play ストアでは入手できないようになります。
Android アプリのアップロードと公開の詳細については、[Google Developer Console のヘルプ](https://support.google.com/googleplay/android-developer/answer/113469)を参照してください。
5. アプリを公開したら、[Google Play for Work ストア](https://play.google.com/work)にアクセスします。 Intune と Android for Work 間の接続を構成するときに使用したものと同じアカウントでサインインします。
6. ストアの **[アプリ]** ノードに、公開したアプリが表示されることを確認します。 アプリは自動的に承認され、Intune と同期されます。

## <a name="deploy-an-android-for-work-app"></a>Android for Work アプリを展開する

ストアのアプリを承認しても、**[アプリ]** ワークスペースの **[ボリューム購入アプリ]** ノードに表示されない場合、次の手順で即時の同期を強制できます。

1. [Intune 管理コンソール](https://manage.microsoft.com)で、**[管理]** > **[モバイル デバイス管理]** > **[Android for Work]** の順に選択します。
2. **[Android for Work モバイル デバイス管理のセットアップ]** ページで、**[今すぐ同期]** を選択します。
3. ページには、前回の同期の時刻と状態も表示されます。

アプリが **[アプリ]** ワークスペースの **[ボリューム購入アプリ]** ノードに表示される場合、[他のアプリと同様の方法でアプリを展開できます](deploy-apps-in-microsoft-intune.md)。 ユーザーのグループに対してのみアプリを展開することもできます。 現在、**[必須]** アクションと **[アンインストール]** アクションのみを選択できます。

アプリを **[使用可能]** としてデプロイできるため、新しいグループ化およびターゲット化エクスペリエンスを活用できます。 この機能はリリース後、新しくプロビジョニングされた Intune サービス アカウントで使用できるようになります。 既存の Intune ユーザーは、テナントが Intune Azure ポータルに移行した後に、この機能を使用できるようになります。 既存のユーザーでも、テナントが移行されるまでに間に、試用の Intune アカウントを作成して、この機能について計画し、機能をテストすることができます。

アプリを展開すると、アプリは対象のデバイスにインストールされます。 デバイスのユーザーには、承認の確認は求められません。

## <a name="manage-app-permissions"></a>アプリのアクセス許可の管理
Android for Work では、Intune にアプリを同期してユーザーにデプロイする前に、Google が管理する Web コンソールの Play でアプリを承認する必要があります。  Android for Work により、これらのアプリがユーザーのデバイスに通知なしで自動的にプッシュできるようになるため、ユーザー全員に代わってアプリへのアクセスを許可する必要があります。  エンド ユーザーにはアプリのアクセス許可について表示されないため、これらのアクセス許可について読み、理解する必要があります。

アプリ開発者がアプリの新しいバージョンを公開する際、以前のバージョンのアクセスを許可していても、新しいバージョンのアクセスは自動的に許可されません。 アプリの以前のバージョンを実行しているデバイスでも使用できますが、新しくアクセス許可が承認されるまでアプリはアップグレードされません。 アプリをインストールしていないデバイスでは、アプリの新しくアクセス許可を承認するまでアプリをインストールできません。

### <a name="how-to-update-app-permissions"></a>アプリのアクセス許可を更新する方法

管理されている Google Play コンソールに定期的にアクセスして、新しく許可していないアクセスがあるかどうか確認してください。 アプリをデプロイしてもデバイスにインストールされていない場合は、まだ許可していないアクセスが新しくあるかどうかを、次の手順で確認します。

1. Http://play.google.com/work にアクセスします。
2. アプリを公開して承認する際に使用した Google アカウントでサインインします。
3. **[更新]** タブにアクセスして、更新が必要なアプリがないかどうかを確認します。  一覧にあるアプリはすべて新しくアクセスを許可する必要があり、許可されるまでデプロイされません。  

