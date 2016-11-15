---
title: "デバイス ログを回収する| Microsoft Intune"
description: "管理対象デバイスからログを回収する方法について説明します。"
keywords: 
author: staciebarker
ms.author: staciebarker
manager: angrobe
ms.date: 11/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d97fb610-9d88-40e5-bb06-447eec533630
ms.reviewer: esmich
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 19b0b502d2c8c261947c461f27a0e8153df5b186
ms.openlocfilehash: 1e65c1fa25e273ba03218f79ebeff611138e8013


---

# <a name="device-logs"></a>デバイス ログ

トラブルシューティングの一環として、ユーザー デバイスからログを回収することがあります。 そのようなログの回収手順についてここで説明します。 一般的に、デバイスへのアクセス権限が必要になります。あるいは、ログを集めて送るようにユーザーに要請する必要があります。

### <a name="android-logs"></a>Android のログ
Android ログは *<Android Device>\Phone\Android\data\com.microsoft.windowsintune.companyportal\files* にあります。 

新型の Android デバイスなどではこのファイルが表示されない場合があります。 その場合は、エンド ユーザーに Android のポータル サイト アプリを開き、**[設定]** に移動して **[ログのコピー]** をタップしてから、デバイスを再起動してもらってください。 

ユーザーからデータ ログを送信してもらう方法については、次の記事を参照してください。

- [詳細ログ記録を使用して、デバイスの問題解決に役立つ情報を IT 管理者に提供する](/intune/enduser/use-verbose-logging-to-help-your-it-administrator-fix-device-issues-android) - 詳細ログ機能を有効にする方法について説明しています。この機能により、ユーザーのすべてのデータ ログが自動で送信されます。 詳細ログは、既定で有効になっています。

- [電子メールを使用して Android 診断データのログを IT 管理者に送信する](/intune/enduser/send-diagnostic-data-logs-to-your-it-administrator-using-email-android) 

- [診断データのログを USB ケーブルを使用して IT 管理者に送信する](/intune/enduser/send-diagnostic-data-logs-to-your-it-administrator-using-a-usb-cable-android)

### <a name="ios-logs"></a>iOS ログ

ユーザーは登録エラーを送信できます。詳細は「[IT 管理者に iOS の登録に関するエラーを送信する](/intune/enduser/send-errors-to-your-it-admin-ios)」にあります。

### <a name="mac-os-x-logs"></a>Mac OS X のログ

1. **[コンソール]** アプリを開きます。
2. **[ファイル]** で **[system.log]** を選択します。
3. 上部のメニュー バーで、**[ファイル]**  >  **[コピーを保存…]** を選択し、 ファイルを保存します。

### <a name="windows-phone"></a>Windows Phone

Windows Phone ポータル サイト アプリケーションで、ユーザーが **[...]** を選択して メニューにアクセスし、**[ログの送信]** を選択する必要があります。 このオプションは、会社のポータル アプリへのサインイン前と後のどちらでも利用できます。

### <a name="windows"></a>Windows

Windows ポータル サイトの場合、ログは *%localappdata%\Packages\Microsoft.CompanyPortal_8wekyb3d8bbwe\LocalState* にあります。



<!--HONumber=Nov16_HO2-->


