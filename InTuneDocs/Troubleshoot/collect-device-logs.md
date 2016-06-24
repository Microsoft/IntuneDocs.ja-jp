---
# required metadata

title: デバイス ログを回収する| Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 06/01/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: d97fb610-9d88-40e5-bb06-447eec533630

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# デバイス ログ

トラブルシューティングの一環として、ユーザー デバイスからログを回収することがあります。 そのようなログの回収手順についてここで説明します。 一般的に、デバイスへのアクセス権限が必要になります。あるいは、ログを集めて送るようにユーザーに要請する必要があります。 

### Android ログの場所
Android ログは *<Android Device>\Phone\Android\data\com.microsoft.windowsintune.companyportal\files* にあります。 ユーザーはログ ファイルを電子メールでも送信できます。詳細は、「[メールを使用して Android の診断データのログを IT 管理者に送信する](/intune/enduser/send-diagnostic-data-logs-to-your-it-administrator-using-email-android)」を参照してください。

### iOS ログ

ユーザーは登録エラーを送信できます。詳細は「[IT 管理者に iOS の登録に関するエラーを送信する](/intune/enduser/send-errors-to-your-it-admin-ios)」にあります。

### Mac OS X デバイス

1. **[コンソール]** アプリを開きます。
2. **[ファイル]** で **[system.log]** を選択します。
3. 上部のメニュー バーで、**[ファイル]**  >  **[コピーを保存…]** を選択し、 ファイルを保存します。

### Windows Phone

**[Windows Phone ポータル サイト]** で、ユーザーは **[…]** を選択して メニューにアクセスし、**[ログの送信]** を選択する必要があります。 このオプションは、ポータルのサインインの前後に利用できます。

### Windows

Windows ポータル サイトの場合、ログは *%localappdata%\Packages\Microsoft.CompanyPortal_8wekyb3d8bbwe\LocalState* にあります。


<!--HONumber=Jun16_HO1-->


