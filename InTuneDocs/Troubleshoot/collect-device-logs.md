---
title: "デバイス ログを回収する | Microsoft Docs"
description: "管理対象デバイスからログを回収する方法について説明します。"
keywords: 
author: staciebarker
ms.author: staciebarker
manager: angrobe
ms.date: 02/07/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d97fb610-9d88-40e5-bb06-447eec533630
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 211b996263aae7a42f8370eb343c7e759ef87790
ms.openlocfilehash: 5aae8edd2b851eb94156e82bc9b6e604644cb900


---

# <a name="device-logs"></a>デバイス ログ

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

トラブルシューティングの一環として、ユーザー デバイスからログを回収することがあります。 そのようなログの回収手順についてここで説明します。 通常は、デバイスにアクセスしてログを取得するか、ログを集めて送るようにユーザーに要請する必要があります。

### <a name="android-logs"></a>Android のログ
Android ログは *<Android Device>\Phone\Android\data\com.microsoft.windowsintune.companyportal\files* にあります。

新型の Android デバイスなどではこのファイルが表示されない場合があります。 この場合は、ユーザーに Android 用の会社のポータル アプリを開いてもらいます。 その後、**[設定]** > **[ログのコピー]** を選択して、デバイスを再起動してもらいます。

ユーザーからデータ ログを送信してもらう方法については、次の記事を参照してください。

- [詳細ログ記録を使用して、デバイスの問題解決に役立つ情報を IT 管理者に提供する](/intune/enduser/use-verbose-logging-to-help-your-it-administrator-fix-device-issues-android): 詳細ログ機能を有効にする方法について説明しています。この機能により、ユーザーのすべてのデータ ログが自動で送信されます。 詳細ログは、既定で有効になっています。

- [電子メールを使用して Android 診断データのログを IT 管理者に送信する](/intune/enduser/send-logs-to-your-it-admin-by-email-android)

- [診断データのログを USB ケーブルを使用して IT 管理者に送信する](/intune/enduser/send-diagnostic-data-logs-to-your-it-administrator-using-a-usb-cable-android)

### <a name="ios-logs"></a>iOS ログ

ユーザーは登録エラーを送信できます。詳細は「[IT 管理者に iOS の登録に関するエラーを送信する](/intune/enduser/send-errors-to-your-it-admin-ios)」にあります。

### <a name="mac-os-x-logs"></a>Mac OS X のログ

1. **[コンソール]** アプリを開きます。
2. **[ファイル]** で **[system.log]** を選択します。
3. 上部のメニュー バーで、**[ファイル]**  >  **[コピーを保存]** を選択し、 ファイルを保存します。

### <a name="windows-phone"></a>Windows Phone

Windows Phone の会社のポータル アプリで、ユーザーは省略記号 **[...]** を選択してメニューにアクセスし、**[ログの送信]** を選択します。 このオプションは、会社のポータル アプリへのサインイン前と後のどちらでも利用できます。

### <a name="windows"></a>Windows

Windows ポータル サイトの場合、ログは *%localappdata%\Packages\Microsoft.CompanyPortal_8wekyb3d8bbwe\LocalState* にあります。



<!--HONumber=Feb17_HO2-->


