---
title: Windows 10 を実行するデバイス向けの Microsoft Intune の電子メール設定
titleSuffix: ''
description: Windows 10 を実行しているデバイスで電子メール設定の構成に使用できる Microsoft Intune 設定について説明します。
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4a0c3eaf0643ede02b8c084d172b7a51d251b3a3
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="email-profile-settings-in-microsoft-intune-for-devices-running-windows-10"></a>Windows 10 を実行するデバイス向けの Microsoft Intune 電子メール プロファイル設定

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

この記事では、Windows 10 を実行しているデバイス用に構成できる電子メール プロファイル設定を示します。


- **[電子メール サーバー]** - Exchange サーバーのホスト名。
- **[アカウント名]** - ユーザーのデバイスに表示される電子メール アカウントの表示名。
- **[AAD からのユーザー名の属性]** - この電子メール プロファイルのユーザー名を生成するために使用される Active Directory (AD) または Azure AD の属性です。 **プライマリ SMTP アドレス** (**user1@contoso.com** など) または**ユーザー プリンシパル名** (**user1**、**user1@contoso.com** など) を選択します。
- **[AAD からのメール アドレス属性]** - 各デバイスでユーザーの電子メール アドレスを生成する方法。 Exchange へのログインにプライマリ SMTP アドレスを使用する場合は **[プライマリ SMTP アドレス]** を選択し、完全プリンシパル名を電子メール アドレスとして使用する場合は **[ユーザー プリンシパル名]** を使用します。


## <a name="security-settings"></a>セキュリティ設定

- **[SSL]** - 電子メールの送受信および Exchange サーバーとの通信に、SSL (Secure Sockets Layer) 通信を使用します。



## <a name="synchronization-settings"></a>同期設定

- **[同期するメールの量]** - 同期する電子メールの日数を選択するか、利用可能なすべての電子メールを同期する場合は **[無制限]** を選択します。
- **[同期スケジュール]** - デバイスが Exchange サーバーからデータを同期するスケジュールを選択します。 **[メッセージが到着したとき]** を選択すると、電子メールが届いたらすぐにデータが同期されます。**[手動]** を選択した場合は、デバイスのユーザーが同期を開始する必要があります。

## <a name="content-sync-settings"></a>コンテンツ同期設定

- **[同期するコンテンツの種類]** - デバイスに同期するコンテンツの種類を選択します。
    - **連絡先**
    - **カレンダー**
    - **タスク**
