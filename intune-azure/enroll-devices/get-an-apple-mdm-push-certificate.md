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
translationtype: Human Translation
ms.sourcegitcommit: 82585886bb053d5b6b5981f61d0337fc6feffea4
ms.openlocfilehash: b26d66d557e084b5b328aec2222c50c2db254bf7
ms.lasthandoff: 03/14/2017


---

# <a name="get-an-apple-mdm-push-certificate"></a>Apple MDM プッシュ証明書を取得する

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Intune では、iPad、iPhone、および Mac コンピューターのモバイル デバイス管理 (MDM) が有効になり、会社の電子メールおよびアプリへのアクセス権がユーザーに付与されます。 Intune で iOS および Mac デバイスを管理するには、MDM プッシュ証明書が必要です。 証明書を Intune に追加すると、ユーザーがポータル サイト アプリをインストールして自分のデバイスを登録できます。 管理者が、Apple の Device Enrollment Program を使用して企業所有の iOS デバイス管理をセットアップしたり、Apple Configurator を使用してデバイスを登録したりすることもできます。 登録オプションについて詳しくは、「[iOS デバイスの登録方法を選択する](https://docs.microsoft.com/intune-azure/enroll-devices/choose-ios-enrollment-method)」をご覧ください。

## <a name="steps-to-get-your-certificate"></a>証明書を取得する手順
Azure Portal で、**[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。 [Intune] ブレードで、**[デバイスの登録]**、**[Apple の登録]**、**[Apple MDM プッシュ証明書]** の順に選択し、Azure Portal で次に示す番号付きの手順に従います。

**手順 1: Apple MDM プッシュ証明書の作成に必要な Intune 証明書署名要求をダウンロードします。**<br>
**[CSR のダウンロード]** を選択して、.csr ファイルをダウンロードし、ローカルに保存します。 .csr ファイルは、Apple Push Certificates Portal からの信頼関係証明書を要求するために使用します。

**手順 2:Apple MDM プッシュ証明書を取得します。**<br>
**[MDM プッシュ証明書を作成する]** を選択して、Apple Push Certificates Portal に移動します。 会社の Apple ID でサインインし、.csr ファイルを使用してプッシュ証明書を作成します。 Apple Push Certificate Portal で **[Upload (アップロード)]** を選択すると、.json ファイルを受け取ります。 プッシュ証明書にこのファイルを使用しないでください。 ダウンロードが完了したら、Apple Push Certificates Portal に戻り、[Certificates for Third-Party Servers] (サード パーティのサーバーの証明書) で、**[Download]** (ダウンロード) を選択します。 プッシュ証明書 (.pem ファイル) をダウンロードして、ローカルに保存します。
メモ

**手順 3:Apple MDM プッシュ証明書の作成に使用する Apple ID を入力します。**

**手順 4:アップロードする Apple MDM プッシュ証明書を参照します。**<br>
証明書 (.pem) ファイルに移動し、**[開く]** を選択して、**[アップロード]** を選択します。 このプッシュ証明書を使用して、Intune はモバイル デバイスを登録し、登録したモバイル デバイスにポリシーを適用して iOS デバイスを管理できます。

