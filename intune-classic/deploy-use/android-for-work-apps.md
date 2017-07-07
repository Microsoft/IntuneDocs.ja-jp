---
title: "アプリを Android for Work デバイスに展開する"
description: "このトピックでは、Google Play for Work ストアから Android for Work デバイスにアプリを同期してから展開します。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 07/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: cd0bbd90-d3fe-4efc-83fd-d1f3f86800d4
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: adc4a343e610a1a75f8a5bc51a1894f6fcf998bb
ms.sourcegitcommit: c9b3a95bf529b6cb2a2bdacbc49127dfa0c233e5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/05/2017
---
# <a name="how-to-deploy-apps-to-android-for-work-devices-with-intune"></a>Intune を使用してアプリを Android for Work デバイスを展開する方法

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Android for Work デバイスにアプリを展開する方法は、標準の Android デバイスに展開する場合と異なります。 Android for Work 用にインストールするすべてのアプリは、Google Play for Work ストアから入手します。 ストアにログオンし、目的のアプリを検索し、アプリを承認します。
承認したアプリは、Intune コンソールの **[ボリューム購入アプリ]** ノードに表示されます。 ここでアプリの展開を管理する方法は、他のアプリを展開する方法と同じです。

また、独自の基幹業務 (LOB) アプリを作成している場合は、そのアプリを次のように展開できます。
- Google Developer アカウントにサインアップして、Google Play ストアの非公開領域にアプリを公開する。
- そのアプリを Intune と同期する。

## <a name="before-you-start"></a>アップグレードを開始する前に

Intune コンソールの **[管理者]** タブで連携して動作するように、Intune と Android for Work を構成します。

## <a name="synchronize-an-app-from-the-google-play-for-work-store"></a>Google Play for Work ストアのアプリを同期する


1. [Google Play for Work ストア](https://play.google.com/work)にアクセスします。 Intune と Android for Work 間の接続を構成するときに使用したものと同じアカウントでサインインします。
2. Intune を使用して展開するアプリをストアで検索します。
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
6. ストアの **[アプリ]** ノードに、公開したアプリが表示されることを確認します。 Intune と同期するように自動的に承認されます。

## <a name="deploy-an-android-for-work-app"></a>Android for Work アプリを展開する

ストアのアプリを承認しても、**[アプリ]** ワークスペースの **[ボリューム購入アプリ]** ノードに表示されない場合は、次の手順で強制的に即時に同期します。

1. [Intune 管理コンソール](https://manage.microsoft.com)で、**[管理]** > **[モバイル デバイス管理]** > **[Android for Work]** の順に選択します。
2. **[Android for Work モバイル デバイス管理のセットアップ]** ページで、**[今すぐ同期]** を選択します。
3. ページには、前回の同期の時刻と状態も表示されます。

アプリが **[アプリ]** ワークスペースの **[ボリューム購入アプリ]** ノードに表示される場合は、[他のアプリと同様の方法でアプリを展開](deploy-apps-in-microsoft-intune.md)できます。 ユーザーのグループに対してのみアプリを展開することもできます。 現在、**[必須]** アクションと **[アンインストール]** アクションのみを選択できます。

アプリを **[使用可能]** としてデプロイできるため、新しいグループ化とターゲット化エクスペリエンスを適用できます。 この機能はリリース後、新しくプロビジョニングされた Intune サービス アカウントで使用できます。 既存の Intune ユーザーは、テナントが Intune Azure ポータルに移行した後に、この機能を使用できるようになります。 既存のユーザーは、試用の Intune アカウントを作成して、テナントが移行されるまでの間にこの機能を検討しテストすることができます。

アプリを展開すると、アプリは対象のデバイスにインストールされます。 デバイスのユーザーは、承認を求められることはありません。

## <a name="manage-app-permissions"></a>アプリのアクセス許可の管理
Android for Work では、Intune にアプリを同期してユーザーにデプロイする前に、Google が管理する Web コンソールの Play でアプリを承認する必要があります。  Android for Work により、これらのアプリがユーザーのデバイスに通知なしで自動的にプッシュできるようになるため、ユーザー全員に代わってアプリへのアクセスを許可する必要があります。  エンド ユーザーがインストールする際はアプリのアクセス許可に関する表示が行われないため、これらのアクセス許可について学習し、理解する必要があります。

アプリ開発者がアプリの新しいバージョンを公開する際、以前のバージョンのアクセスを許可していても、新しいバージョンのアクセスは自動的に許可されません。 以前のバージョンのアプリを実行しているデバイスでも使用できますが、新しいアクセス許可が承認されるまでアプリはアップグレードされません。 アプリをインストールしていないデバイスでは、アプリの新しくアクセス許可を承認するまでアプリをインストールできません。

### <a name="how-to-update-app-permissions"></a>アプリのアクセス許可を更新する方法

管理対象の Google Play コンソールに定期的にアクセスして、新しいアクセス許可があるかどうか確認してください。 承認済みのアプリに新しいアクセス許可が必要な場合は、Google Play を構成して、自分や他のユーザーあてに電子メールを送信できます。 アプリを割り当ててもデバイスにインストールされていない場合は、まだ許可していないアクセス許可が新しくあるかどうかを、次の手順で確認します。

1. http://play.google.com/work にアクセスします。
2. アプリを公開して承認する際に使用した Google アカウントでサインインします。
3. **[更新]** タブにアクセスして、更新が必要なアプリがないかどうかを確認します。  一覧にあるアプリには新しいアクセス許可が必要で、アクセス許可が適用されるまでアプリは割り当てられません。  

あるいは、Google Play を構成することで、アプリごとにアクセス許可を自動的に再許可できます。 
