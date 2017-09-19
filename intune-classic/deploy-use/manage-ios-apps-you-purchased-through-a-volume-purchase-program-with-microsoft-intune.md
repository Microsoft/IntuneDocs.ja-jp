---
title: "ボリューム購入した iOS アプリを管理する"
description: "Intune は、アプリ ストアからライセンス情報をインポートし、使用したライセンスの数を追跡し、所有しているより多くのアプリをインストールできないようにすることで、Apple からボリューム購入したアプリを管理するために使用します。"
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 09/07/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1dafc28a-7f8b-4fe0-8619-f977c93d1140
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: bbb67c9225ef99f57f12c839b81b95a1956b70f3
ms.sourcegitcommit: cf7f7e7c9e9cde5b030cf5fae26a5e8f4d269b0d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/14/2017
---
# <a name="manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune"></a>Volume Purchase Program で購入した iOS アプリを Microsoft Intune を使って管理する

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

iOS アプリ ストアでは、社内で実行するアプリの複数のライセンスを購入できます。 これは、購入したアプリの複数コピーを追跡する管理オーバーヘッドを削減するのに役立ちます。

Microsoft Intune では、このプログラムを通じて購入したアプリを管理するために、アプリ ストアからライセンス情報をインポートし、使用したライセンスの数を追跡し、所有しているより多くのアプリをインストールできないようにします。

> [!Important]
> 現在、Intune は、デバイスではなくユーザーに iOS Volume Purchase Program for Business (VPP) アプリ ライセンスを割り当てます。 そのため、ユーザーは、アプリをインストールするために Apple ID パスワードを入力する必要があります。
> 教育向け Apple Volume Purchase Program と B2B アプリは、このリリースではサポートされていません。

## <a name="manage-volume-purchased-apps-for-ios-devices"></a>iOS デバイス用のボリューム購入アプリの管理
iOS アプリの複数のライセンスを購入するには、[Apple Volume Purchase Program for Business](http://www.apple.com/business/vpp/) を利用します。 このためには、Apple Web サイトから Apple VPP アカウントをセットアップし、Apple VPP トークンの Intune へのアップロードを行います。  その後、ボリューム購入情報を Intune と同期し、ボリューム購入アプリの使用を追跡することができます。

## <a name="before-you-start"></a>アップグレードを開始する前に
開始する前に、Apple から VPP トークンを取得し、これを Intune アカウントにアップロードする必要があります。 さらに、次の点を理解する必要があります。

* Intune は最大 256 VPP トークンの追加をサポートしています。
* 以前に異なる製品で VPP トークンを使用していた場合は、Intune で使用するための新しい VPP トークンを生成する必要があります。
* 各トークンは、1 年間有効です。
* 既定では、Intune は 1 日に 2 回、Apple VPP サービスと同期します。 いつでも手動での同期を開始できます。
* Intune に VPP トークンをインポートした後、同じトークンを他のデバイス管理ソリューションにインポートすることはできません。 これを行うと、ライセンスの割り当てとユーザー レコードが失われる恐れがあります。
* Intune で iOS VPP の使用を開始する前に、他のモバイル デバイス管理 (MDM) ベンダーで作成された既存の VPP ユーザー アカウントを削除してください。 Intune は、セキュリティ対策として、そのようなユーザー アカウントを Intune と同期しません。 Intune は、Intune によって作成された Apple VPP サービスからのデータのみを同期します。
* デバイスのユーザー アフィニティが構成されている場合、Device Enrollment Protocol (DEP) を使用して登録されたユーザーのデバイスにのみ iOS VPP アプリを展開することができます。

## <a name="to-get-and-upload-an-apple-vpp-token"></a>Apple VPP トークンを取得およびアップロードするには

1.  [Microsoft Intune 管理コンソール](https://manage.microsoft.com)で、**[管理者]** &gt; **[iOS および Mac OS X]**&gt;**、[Volume Purchase Program]** の順に選択します。

2.  **[Apple VPP アカウント]** リンクを選択します。 サインアップしていない場合は、Volume Purchase Program for Business にサインアップします。 サインアップした後、アカウントの Apple VPP トークンをダウンロードします。

3.  Intune コンソールの **[Apple Volume Purchase Program (VPP) の管理]** ページで、**[VPP トークンのアップロード]** を選択します。

4.  **[VPP トークンのアップロード]** ダイアログ ボックスで、VPP トークンの名前と Apple ID を入力または貼り付けて、**[アップロード]** を選択します。

5.  警告ダイアログ ボックスで、後で異なる VPP アカウントに変更できないことを理解していることを示すボックスをオンにして、**[はい]** を選択します。

**[Volume Purchase Program]** ページに、Apple VPP トークンに関する情報として、最終更新時刻や有効期限、Intune との最終同期時刻などが表示されます。

**[今すぐ同期]** を選択すると、いつでも、Apple が保持しているデータと Intune を同期することができます。

## <a name="to-deploy-a-volume-purchased-app"></a>ボリューム購入アプリを展開するには

1.  [Microsoft Intune 管理コンソール](https://manage.microsoft.com)で、**[アプリ]** &gt; **[アプリ]** &gt; **[ボリューム購入されたアプリ]** の順に選択します。 この一覧には、Apple VPP サービスから同期されたアプリがすべて表示されます。

2.  展開するアプリを選択し、**[展開の管理]** を選択して、「[Microsoft Intune でアプリを展開する](deploy-apps-in-microsoft-intune.md)」トピックの手順に従って、アプリのアップロード、作成、展開を完了します。

> [!TIP]
> **[必須]** の展開操作を選択する必要があります。 使用可能なインストールは現在サポートされていません。 さらに、アプリを展開できるのはユーザー グループに対してだけです。

アプリを **[必須]** インストールとして展開すると、アプリをインストールする各ユーザーがライセンスを使用します。

ライセンスを再利用するには、展開アクションを **[アンインストール]** に変更する必要があります。 アプリをアンインストールすると、ライセンスは回収されます。

対象となるデバイスを持つユーザーが初めて VPP アプリをインストールしようとすると、Apple Volume Purchase Program に参加するように求められます。 アプリのインストールを実行する前に、このプログラムに参加する必要があります。

それ以上使用できるライセンスがない場合、展開は失敗します。

## <a name="to-monitor-apple-vpp-apps"></a>Apple VPP アプリを監視するには
**[ボリューム購入されたアプリ]** ノードの **[アプリ]** ワークスペースを使って、展開されている VPP アプリおよび使われているライセンスの数を監視できます。

> [!TIP]
> また、アプリの **[フィルター]** を使って、各アプリのインストールの状態を調べることもできます。

### <a name="see-also"></a>関連項目
[Microsoft Intune でアプリを展開する](deploy-apps-in-microsoft-intune.md)
