---
title: "Apple MDM プッシュ証明書を取得する"
titleSuffix: Intune Azure preview
description: "Intune Azure プレビュー: Intune で iOS デバイスを管理するために Apple MDM プッシュ証明書を取得する手順を説明します。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 03/14/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: e3ff50fa65eff897147081f2ec9ab366dbf50140
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017


---

# <a name="get-an-apple-mdm-push-certificate"></a>Apple MDM プッシュ証明書を取得する

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Intune では、iPad、iPhone、および Mac コンピューターのモバイル デバイス管理 (MDM) が有効になり、会社の電子メールおよびアプリへのアクセス権がユーザーに付与されます。 Intune で iOS および Mac デバイスを管理するには、MDM プッシュ証明書が必要です。 証明書を Intune に追加すると、ユーザーがポータル サイト アプリをインストールして自分のデバイスを登録できます。 管理者が、Apple の Device Enrollment Program を使用して企業所有の iOS デバイス管理をセットアップしたり、Apple Configurator を使用してデバイスを登録したりすることもできます。 登録オプションについて詳しくは、「[iOS デバイスの登録方法を選択する](enrollment-method-choose-ios.md)」をご覧ください。

## <a name="steps-to-get-your-certificate"></a>証明書を取得する手順
Azure Portal で、**[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。 [Intune] ブレードで、**[デバイスの登録]**、**[Apple の登録]**、**[Apple MDM プッシュ証明書]** の順に選択し、Azure Portal で次に示す番号付きの手順に従います。

**手順 1: Apple MDM プッシュ証明書の作成に必要な Intune 証明書署名要求をダウンロードします。**<br>
**[CSR のダウンロード]** を選択して、.csr ファイルをダウンロードし、ローカルに保存します。 .csr ファイルは、Apple Push Certificates Portal からの信頼関係証明書を要求するために使用します。

**手順 2:Apple MDM プッシュ証明書を取得します。**<br>
**[MDM プッシュ証明書を作成する]** を選択して、Apple Push Certificates Portal に移動します。 会社の Apple ID でサインインし、.csr ファイルを使用してプッシュ証明書を作成します。 Apple Push Certificate Portal で **[Upload (アップロード)]** を選択すると、.json ファイルを受け取ります。 プッシュ証明書にこのファイルを使用しないでください。 ダウンロードが完了したら、Apple Push Certificates Portal に戻り、[Certificates for Third-Party Servers]\(サード パーティのサーバーの証明書) で、**[Download]** (ダウンロード) を選択します。 プッシュ証明書 (.pem ファイル) をダウンロードして、ローカルに保存します。

> [!NOTE]
> 証明書は、証明書の作成に使用した Apple ID と関連付けられています。 ベスト プラクティスとして、管理タスクには会社の Apple ID を使用してください。 個人の Apple ID は使用しないでください。

**手順 3:Apple MDM プッシュ証明書の作成に使用する Apple ID を入力します。**

**手順 4:アップロードする Apple MDM プッシュ証明書を参照します。**<br>
証明書 (.pem) ファイルに移動し、**[開く]** を選択して、**[アップロード]** を選択します。 このプッシュ証明書を使用して、Intune はモバイル デバイスを登録し、登録したモバイル デバイスにポリシーを適用して iOS デバイスを管理できます。

## <a name="renew-apple-mdm-push-certificate"></a>Apple MDM プッシュ証明書を更新する
Apple MDM プッシュ証明書の有効期間は 1 年間です。iOS と macOS のデバイス管理を維持するには毎年更新する必要があります。 証明書の有効期限が切れると、登録されている Apple デバイスに接続できなくなります。

証明書は、証明書の作成に使用した Apple ID と関連付けられています。 MDM プッシュ証明書を更新するには、作成時と同じ Apple ID を使用してください。

> [!NOTE]
> 証明書は、証明書の作成に使用した Apple ID と関連付けられています。 ベスト プラクティスとして、管理タスクには会社の Apple ID を使用してください。 個人の Apple ID は使用しないでください。

1. [Azure Intune Portal](https://portal.azure.com) で **[デバイスの登録]** > **[Apple の登録]** の順に選択し、**[Apple MDM プッシュ通知]** を選択します。
2. **[CSR のダウンロード]** を選択して、.csr ファイルをダウンロードし、ローカルに保存します。 .csr ファイルは、Apple Push Certificates Portal からの信頼関係証明書を要求するために使用します。
3. 更新する証明書を検索し、**[更新]** を選択します。
4. **[Renew Push Certificate]\(プッシュ証明書の更新)** 画面で、今後証明書を識別しやすいようにメモを入力し、**[ファイルの選択]** を選択して、ダウンロードした新しい .csr ファイルを参照し、**[アップロード]** を選択します。
5. **[確認]** 画面で **[ダウンロード]** を選択し、.pem ファイルをローカルに保存します。
6. Azure Intune ポータルで **[Apple MDM プッシュ証明書]** 参照アイコンを選択し、Apple からダウンロードした .pem ファイルを選択し、**[アップロード]** を選択します。

Apple MDM プッシュ証明書は **[有効]** と表示され、有効期限まで 365 日と表示されます。

