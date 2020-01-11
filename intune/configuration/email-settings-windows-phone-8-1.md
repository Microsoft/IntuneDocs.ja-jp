---
title: Windows Phone 8.1 デバイス向けの Microsoft Intune 電子メール設定
titleSuffix: ''
description: Windows Phone 8.1 を実行するデバイスでの電子メール接続の構成に使用できる Intune 設定について説明します。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: aab4379e30397132cead64acbd8d43039b128e02
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2019
ms.locfileid: "75206416"
---
# <a name="email-profile-settings-in-microsoft-intune-for-devices-running-windows-phone-81"></a>Windows Phone 8.1 を実行するデバイス向けの Microsoft Intune 電子メール プロファイル設定



この記事では、Windows Phone 8.1 を実行しているデバイス用に構成できる電子メール プロファイル設定を示します。

>[!IMPORTANT]
>Windows Phone 8.1 電子メールプロファイルは、Windows 10 デバイスにも適用されます。

- **[電子メール サーバー]** - Exchange サーバーのホスト名。
- **[アカウント名]** - ユーザーのデバイスに表示される電子メール アカウントの表示名。
- **[AAD からのユーザー名の属性]** - この電子メール プロファイルのユーザー名を生成するために使用される Active Directory (AD) または Azure AD の属性です。 **プライマリ SMTP アドレス** ( **user1@contoso.com** など) または**ユーザー プリンシパル名** (**user1**、 **user1@contoso.com** など) を選択します。
- **[AAD からのメール アドレス属性]** - 各デバイスでユーザーの電子メール アドレスを生成する方法。 Exchange へのログインにプライマリ SMTP アドレスを使用する場合は **[プライマリ SMTP アドレス]** を選択し、完全プリンシパル名を電子メール アドレスとして使用する場合は **[ユーザー プリンシパル名]** を使用します。


## <a name="security-settings"></a>セキュリティ設定

- **[SSL]** - 電子メールの送受信および Exchange サーバーとの通信に、SSL (Secure Sockets Layer) 通信を使用します。



## <a name="synchronization-settings"></a>同期設定

- **[同期するメールの量]** - 同期する電子メールの日数を選択するか、利用可能なすべての電子メールを同期する場合は **[無制限]** を選択します。
- **[同期スケジュール]** - デバイスが Exchange サーバーからデータを同期するスケジュールを選択します。 **[メッセージが到着したとき]** を選択すると、電子メールが届いたらすぐにデータが同期されます。 **[手動]** を選択した場合は、デバイスのユーザーが同期を開始する必要があります。

## <a name="content-sync-settings"></a>コンテンツ同期設定

- **[同期するコンテンツの種類]** - デバイスに同期するコンテンツの種類を選択します。
  - **連絡先**
  - **カレンダー**
  - **タスク**
