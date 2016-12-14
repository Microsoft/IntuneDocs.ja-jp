---
title: "アプリを Android for Work デバイスに展開する | Microsoft Intune"
description: "このトピックでは、Google Play for Work ストアから Android for Work デバイスにアプリを同期してから展開します。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/6/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: cd0bbd90-d3fe-4efc-83fd-d1f3f86800d4
ms.reviewer: chrisbal
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: 35ee89248e42c67f48d4607f5d415896e35b90e9


---

# <a name="how-to-deploy-apps-to-android-for-work-devices-with-intune"></a>Intune を使用してアプリを Android for Work デバイスを展開する方法

[!INCLUDE[wit_nextref](../includes/afw_rollout_disclaimer.md)]

Android for Work デバイスにアプリを展開する方法は、標準の Android デバイスに展開する場合と異なります。 Android for Work 用にインストールするすべてのアプリは、Google Play for Work ストアから入手します。 ストアにログインし、目的のアプリを検索し、承認します。
承認したアプリは、Intune コンソールの **[ボリューム購入アプリ]** ノードに表示されます。 ここでアプリの展開を管理する方法は、他のアプリを展開する方法と同じです。
また、独自の基幹業務 (LOB) アプリを作成している場合、そのアプリも展開できます。 LOB アプリを展開するには、Google Developer アカウントにサインアップする必要があります。サインアップすると、Google Play ストアの非公開領域にアプリを公開し、Intune と同期できるようになります。

## <a name="before-you-start"></a>アップグレードを開始する前に

1. Intune コンソールの **[管理者]** タブで連携して動作するように、Intune と Android for Work を構成します。

## <a name="synchronize-an-app-from-the-google-play-for-work-store"></a>Google Play for Work ストアのアプリを同期する


1. [Google Play for Work ストア](https://play.google.com/work)にアクセスします。 Intune と Android for Work 間の接続を構成するときに使用したものと同じアカウントでサインインします。
2. Intune を使用して展開するアプリをストアで検索します。
3. 選択するアプリのページで、**[承認]** を選択します。 この例では、Microsoft Excel アプリを選択しました。<br>
  ![アプリの承認例](/intune/deploy-use/media/approve.png)
4. 多様な操作を実行するアクセス許可をアプリに付与するように求めるウィンドウが開きます。 続行するには、**[承認]** を選択する必要があります。<br>
  ![アプリのアクセス許可の承認例](/intune/deploy-use/media/approve-app-permissions.png)
5. しばらくすると、アプリが承認され、IT 管理コンソールで使用できるようになったことを示す確認メッセージが表示されます。

## <a name="publish-then-synchronize-a-line-of-business-app-from-the-google-play-for-work-store"></a>Google Play for Work ストアから基幹業務アプリを公開し、同期する

1. Google Play Developer Console で、[play.google.com/apps/publish](https://play.google.com/apps/publish) を開きます。
2. Intune と Android for Work 間の接続を構成するときに使用したものと同じアカウントでサインインします。 初めてサインインする場合は、Google Developer プログラムに登録し、料金を払ってメンバーになる必要があります。
3. コンソールで、**[Add new application]** (新しいアプリケーションの追加) を選択します。
4. アプリをアップロードし、アプリに関する情報を提供する方法は、アプリを Google Play ストアに公開する方法と同じです。 ただし、次の図のように、*[*Only make this application available to my organization (<*組織名*>)**] (このアプリケーションを自分の組織 (<組織名>) のみが入手できるようにする) 設定を選択する必要があります。<br>
  ![組織のみがアプリを入手できるようにするためのオプション](/intune/deploy-use/media/restrict.png)<br>
このオプションをオンにすると、自分の組織のみがアプリを入手でき、公開されている Google Play ストアでは入手できないようになります。
Android アプリのアップロードと公開の詳細については、[Google Developer Console のヘルプ](https://support.google.com/googleplay/android-developer/answer/113469)を参照してください。
5. アプリを公開したら、[Google Play for Work ストア](https://play.google.com/work)にアクセスします。 Intune と Android for Work 間の接続を構成するときに使用したものと同じアカウントでサインインします。
6. ストアの **[アプリ]** ノードに、公開したアプリが表示されることを確認します。 アプリは自動的に承認され、Intune と同期されます。

## <a name="deploy-an-android-for-work-app"></a>Android for Work アプリを展開する

通常、Intune は Google Play for Work ストアと 1 日に 2 回同期します。 ストアのアプリを承認しても、**[アプリ]** ワークスペースの **[ボリューム購入アプリ]** ノードに表示されない場合、次の手順で即時の同期を強制できます。

1. [Intune 管理コンソール](https://manage.microsoft.com)で、**[管理]** > **[モバイル デバイス管理]** > **[Android for Work]** の順に選択します。
2. **[Android for Work モバイル デバイス管理のセットアップ]** ページで、**[今すぐ同期]** を選択します。
3. ページには、前回の同期の時刻と状態も表示されます。

アプリが **[アプリ]** ワークスペースの **[ボリューム購入アプリ]** ノードに表示される場合、[他のアプリと同様の方法でアプリを展開できます](deploy-apps-in-microsoft-intune.md)。 ユーザーのグループに対してのみアプリを展開することもできます。 現在、**[必須]** アクションと **[アンインストール]** アクションのみを選択できます。 2016 年 10 月以降、新しいテナントに **[利用可能]** 展開アクションを追加する予定です。

アプリを展開すると、アプリは対象のデバイスにインストールされます。 デバイスのユーザーには、承認の確認は求められません。



<!--HONumber=Dec16_HO2-->


