---
title: "iOS デバイス向けの Intune 電子メール設定"
titleSuffix: Intune on Azure
description: "iOS デバイスでの電子メール接続の構成に使用できる Intune 設定について説明します。&quot;"
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 02/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9f0fa6af-3669-439a-bd0d-75d8b1a0b135
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: dcac410ae5c20b5942bf37f5eaa9a46205a4cc07
ms.contentlocale: ja-jp
ms.lasthandoff: 06/08/2017


---

# <a name="email-profile-settings-for-ios-devices-in-microsoft-intune"></a>Microsoft Intune での iOS デバイス向けの電子メール プロファイル設定

[!INCLUDE[azure_portal](./includes/azure_portal.md)]



- **[電子メール サーバー]** - Exchange サーバーのホスト名。
- **[アカウント名]** - ユーザーのデバイスに表示される電子メール アカウントの表示名。
- **[AAD からのユーザー名の属性]** - この電子メール プロファイルのユーザー名を生成するために使用される Active Directory (AD) または Azure AD の属性です。 **プライマリ SMTP アドレス** (**user1@contoso.com** など) または**ユーザー プリンシパル名** (**user1**、**user1@contoso.com** など) を選択します。
- **[AAD からのメール アドレス属性]** - 各デバイスでユーザーの電子メール アドレスを生成する方法。 Exchange へのログインにプライマリ SMTP アドレスを使用する場合は **[プライマリ SMTP アドレス]** を選択し、完全プリンシパル名を電子メール アドレスとして使用する場合は **[ユーザー プリンシパル名]** を使用します。
- **[認証方法]** - 電子メール プロファイルで使用する認証方法として、**[ユーザー名とパスワード]** または **[証明書]** を選択します。
    - **[証明書]** を選択した場合は、Exchange 接続の認証に使用するために事前に作成しておいたクライアント SCEP または PKCS 証明書プロファイルを選択します。
- **[SSL]** - 電子メールの送受信および Exchange サーバーとの通信に、SSL (Secure Sockets Layer) 通信を使用します。
- **[S/MIME]** - S/MIME 署名を使用して送信メールを送信します。
    - **[証明書]** を選択した場合は、Exchange 接続の認証に使用するために事前に作成しておいたクライアント SCEP または PKCS 証明書プロファイルを選択します。
- **[同期するメールの量]** - 同期する電子メールの日数を選択するか、利用可能なすべての電子メールを同期する場合は **[無制限]** を選択します。
- **[他の電子メール アカウントにメッセージを移動することを許可する]** - デバイスで構成されている複数のアカウント間で、ユーザーが電子メール メッセージを移動できるようにします。
- **[サード パーティ アプリケーションから電子メールを送信できるようにする]** - 電子メールを送信するための既定のアカウントとしてこのプロファイルを選択することをユーザーに許可し、(たとえば、ファイルを電子メールに添付する目的で) ネイティブの電子メール アプリで電子メールを開くことをサードパーティ製アプリに許可します。
- **[最近使用した電子メール アドレスを同期する]** - この機能を使用すると、ユーザーは、デバイスで最近使用された電子メール アドレスのリストをサーバーと同期できるようになります。

