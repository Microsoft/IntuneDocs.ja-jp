---
title: "Android デバイス向けの Intune 電子メール設定 | Intune Azure プレビュー | Microsoft Docs"
description: "Intune Azure プレビュー: Android デバイスで電子メール接続を構成するために使用できる Intune 設定について説明します。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4d3458cc-fcaa-4648-b13f-bf1f0616c1c5
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4d095506215b775d56d172e9aabae1737757310
ms.openlocfilehash: 29a4346a04470192553ad2d4f0962a2a21d637ec
ms.lasthandoff: 02/16/2017


---

# <a name="email-profile-settings-for-android-devices-in-microsoft-intune"></a>Microsoft Intune での Android デバイス向けの電子メール プロファイル設定

[!INCLUDE[azure_preview](../includes/azure_preview.md)]



- **[電子メール サーバー]** - Exchange サーバーのホスト名。
- **[アカウント名]** - ユーザーのデバイスに表示される電子メール アカウントの表示名。
- **[AAD からのユーザー名の属性]** - この電子メール プロファイルのユーザー名を生成するために使用される Active Directory (AD) または Azure AD の属性です。 **プライマリ SMTP アドレス** (user1@contoso.com など) または**ユーザー プリンシパル名** (user1、user1@contoso.com など) を選択します。
- **[AAD からのメール アドレス属性]** - 各デバイスでユーザーの電子メール アドレスを生成する方法。 Exchange へのログインにプライマリ SMTP アドレスを使用する場合は **[プライマリ SMTP アドレス]** を選択し、完全プリンシパル名を電子メール アドレスとして使用する場合は **[ユーザー プリンシパル名]** を使用します。
- **[認証方法]** - 電子メール プロファイルで使用する認証方法として、**[ユーザー名とパスワード]** または **[証明書]** を選択します。
    - **[証明書]** を選択した場合は、Exchange 接続の認証に使用するために事前に作成しておいたクライアント SCEP または PKCS 証明書プロファイルを選択します。

## <a name="security-settings"></a>セキュリティ設定

- **[SSL]** - 電子メールの送受信および Exchange サーバーとの通信に、SSL (Secure Sockets Layer) 通信を使用します。
- **[S/MIME]** - S/MIME 暗号化を使用して電子メールを送信します。
    - **[証明書]** を選択した場合は、Exchange 接続の認証に使用するために事前に作成しておいたクライアント SCEP または PKCS 証明書プロファイルを選択します。

## <a name="synchronization-settings"></a>同期設定

- **[同期するメールの量]** - 同期する電子メールの日数を選択するか、利用可能なすべての電子メールを同期する場合は **[無制限]** を選択します。
- **[同期スケジュール]** - デバイスが Exchange サーバーからデータを同期するスケジュールを選択します。 **[メッセージが到着したとき]** を選択すると、電子メールが届いたらすぐにデータが同期されます。**[手動]** を選択した場合は、デバイスのユーザーが同期を開始する必要があります。

## <a name="content-sync-settings"></a>コンテンツ同期設定

- **[同期するコンテンツの種類]** - デバイスに同期するコンテンツの種類を選択します。
    - **連絡先**
    - **カレンダー**
    - **タスク**

