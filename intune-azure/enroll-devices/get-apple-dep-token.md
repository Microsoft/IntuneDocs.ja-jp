---
title: "Intune の Apple DEP 証明書を取得する | Intune Azure プレビュー | Microsoft Docs"
description: "Intune Azure プレビュー: Intune で Apple デバイスを管理するための前提条件である MDM プッシュ証明書を構成してアップロードするための手順。 "
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 02/03/17
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7e5c79c5-2883-4841-9be6-74cba16ee447
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 08dad848a48adad7d9c6f0b5b3286f6550a266bd
ms.openlocfilehash: b2c79e92f6378825bdaac03d2d9be699bdaca95b
ms.lasthandoff: 02/15/2017

---

# <a name="get-an-apple-dep-certificate"></a>Apple DEP 証明書を取得する 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

DEP に企業所有の iOS デバイスを登録するには、Apple の DEP トークンが必要です。 このトークンにより、Intune は企業所有の DEP 参加デバイスに関する情報を同期できるようになります。 また、Intune は Apple への登録プロファイルのアップロードを実行して、デバイスをそれらのプロファイルに割り当てられるようになります。

Apple の Device Enrollment Program (DEP) を使用して企業所有の iOS デバイスを管理するには、組織が Apple DEP に参加し、そのプログラムを使用してデバイスを取得する必要があります。 そのプロセスの詳細については、https://deploy.apple.com を参照してください。 このプログラムの利点には、各デバイスをコンピューターに USB ケーブルを使用して接続することなく、デバイスを楽に設定できる点があります。

> [!NOTE]
> Intune 管理コンソールから Azure Portal に移行した場合のみ、この注を読んでください。 移行期間中に Intune 管理コンソールから Apple DEP トークンを削除した場合は、Intune アカウントに DEP トークンが復元されていることがあります。 その場合は、Azure Portal から DEP トークンを削除します。 

**Apple DEP 証明書を取得するには**</br>
Azure Portal で、**[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。 [Intune] ブレードで、**[デバイスの登録]** > **[Apple DEP トークン]** の順に選択し、Azure Portal で次に示す番号付きの手順に従います。

**手順 1: Apple DEP トークンを作成するために必要な Intune 公開キー証明書をダウンロードします。**<br>
**[Download your public key (公開キーをダウンロードする)]** を選択して、暗号化キー (.pem) ファイルをダウンロードし、ローカルに保存します。 .pem ファイルは、Apple Device Enrollment Program ポータルから信頼関係証明書を要求するために使用します。

**手順 2:適切な Apple の Web サイトから、Apple DEP トークンをダウンロードします。**<br>
[[Apple 展開プログラムを使用して DEP のトークンを作成します]](https://deploy.apple.com) (https://deploy.apple.com) を選択し、会社の Apple ID でサインインします。 この Apple ID は、DEP トークンを更新するために使用する必要があります。

   1.  [Device Enrollment Program ポータル](https://deploy.apple.com)で **[Device Enrollment Program]** &gt; **[Manage Servers]** (サーバーの管理) に移動して、**[Add MDM Server]** (MDM サーバーの追加) を選択します。

   2.  **MDM サーバー名**を入力し、**[Next]** (次へ) をクリックします。 サーバー名は、自分がモバイル デバイス管理 (MDM) サーバーを識別できるようにするための名前です。 Microsoft Intune サーバーの名前または URL ではありません。

   3.  **[Add &lt;ServerName&gt;]** ダイアログ ボックスが開きます。 **[Choose File]** (ファイルを選択) をクリックして .pem ファイルをアップロードし、**[Next]** (次へ) を選択します。

   4.  **[Add &lt;ServerName&gt;]** (<サーバー名> の追加) ダイアログ ボックスに、**[Your Server Token]** (サーバー トークン) リンクが表示されます。 サーバー トークン (.p7m) ファイルをコンピューターにダウンロードした後、**[Done]** (完了) を選択します。

    この証明書 (.p7m) ファイルは、Intune と Apple の Device Enrollment Program サーバーとの間に信頼関係を確立するために使用されます。

**手順 3:Apple DEP トークンの作成に使用する Apple ID を入力します。この ID は、Apple DEP トークンを更新するために使用できます。**

**手順 4:アップロードする Apple DEP トークンを参照します。Intune は自動的に DEP アカウントと同期します。**<br>
証明書 (.pem) ファイルに移動し、**[開く]** を選択して、**[アップロード]** を選択します。 このプッシュ証明書を使用して、Intune はモバイル デバイスを登録し、登録したモバイル デバイスにポリシーを適用して iOS デバイスを管理できます。

