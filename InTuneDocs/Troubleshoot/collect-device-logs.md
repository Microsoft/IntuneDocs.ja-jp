---
title: "デバイス ログを回収する| Microsoft Intune"
description: "管理対象デバイスからログを回収する方法について説明します。"
keywords: 
author: staciebarker
ms.author: staciebarker
manager: angrobe
ms.date: 10/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d97fb610-9d88-40e5-bb06-447eec533630
ms.reviewer: esmich
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 3a081109cd499d3bdda75cb6c8a4dab9d9d28fab
ms.openlocfilehash: ec7d522e8dcff66d1b84fed3c4c0cc708e555e67


---

# <a name="device-logs"></a>デバイス ログ

トラブルシューティングの一環として、ユーザー デバイスからログを回収することがあります。 そのようなログの回収手順についてここで説明します。 一般的に、デバイスへのアクセス権限が必要になります。あるいは、ログを集めて送るようにユーザーに要請する必要があります。

### <a name="android-log-location"></a>Android ログの場所
Android ログは *<Android Device>\Phone\Android\data\com.microsoft.windowsintune.companyportal\files* にあります。 ユーザーはログ ファイルを電子メールでも送信できます。詳細は、「[メールを使用して Android の診断データのログを IT 管理者に送信する](/intune/enduser/send-diagnostic-data-logs-to-your-it-administrator-using-email-android)」を参照してください。

### <a name="ios-logs"></a>iOS ログ

ユーザーは登録エラーを送信できます。詳細は「[IT 管理者に iOS の登録に関するエラーを送信する](/intune/enduser/send-errors-to-your-it-admin-ios)」にあります。

### <a name="mac-os-x-devices"></a>Mac OS X デバイス

1. **[コンソール]** アプリを開きます。
2. **[ファイル]** で **[system.log]** を選択します。
3. 上部のメニュー バーで、**[ファイル]**  >  **[コピーを保存…]** を選択し、 ファイルを保存します。

### <a name="windows-phone"></a>Windows Phone

**[Windows Phone ポータル サイト]** で、ユーザーは **[…]** を選択して メニューにアクセスし、**[ログの送信]** を選択する必要があります。 このオプションは、ポータルのサインインの前後に利用できます。

### <a name="windows"></a>Windows

Windows ポータル サイトの場合、ログは *%localappdata%\Packages\Microsoft.CompanyPortal_8wekyb3d8bbwe\LocalState* にあります。



<!--HONumber=Oct16_HO3-->


