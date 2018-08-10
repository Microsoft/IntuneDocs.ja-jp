---
title: Intune から Windows デバイスを削除する
description: Intune から Windows デバイスを削除する方法について説明します
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 018bda65-7238-41f5-b92a-e5f67b7fe085
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 980b7d9f221fd1a1ae12f27743757d5b3bd53492
ms.sourcegitcommit: 5f6117b83f96f7d93dde3685c2ff2b67ae53740b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2018
ms.locfileid: "39481191"
---
# <a name="remove-your-windows-device-from-intune-management"></a>Intune 管理から Windows デバイスを削除する

次のようなことが不要になった、登録済みの Windows デバイスを Intune から削除します。  
* デバイスを職場または学校で使用する。 
* 職場または学校の電子メール、アプリ、またはその他のリソースにアクセスする。

職場または学校のリソースは、削除されるとデバイスからアクセスできなくなります。 次のような Windows デバイスを Intune から削除することができます。  
* Windows 10 デバイス 
* Windows 8.1 コンピューター
* Windows 8.1 モバイル デバイス
 
Intune 管理からデバイスを削除した後に何が起きるかについては、「[Intune からデバイスの登録を解除するとどうなりますか。](what-happens-if-you-unenroll-your-device-from-intune-windows.md)」を参照してください。

## <a name="remove-your-windows-10-device"></a>Windows 10 デバイスを削除する
Windows 10 デバイスを Intune から削除するには、次の手順を完了します。

### <a name="via-the-company-portal-app"></a>ポータル サイト アプリを使用する

1. ポータル サイト アプリを開きます。
2. 職場または学校の資格情報でサインインします。
3. **[デバイス]** で、削除するデバイスを選びます。
4. アプリの右上隅で、**[詳細表示]** アイコンを選びます。
5. **[削除]** を選びます。 
6. デバイスの削除を確認するには、**[デバイスの削除]** を選びます。

### <a name="via-device-settings-app"></a>デバイス設定アプリを使用する
1. [設定] アプリを開きます。 
2. **[アカウント]** > **[職場または学校にアクセスする]** の順に移動します。
3. 接続されている、削除したいアカウントで、**[切断]** を選びます。
4. デバイスの削除を確認するには、**[はい]** を選びます。

## <a name="remove-your-windows-81-computer"></a>Windows 8.1 コンピューターを削除する
Windows 8.1 コンピューターを Intune から削除するには、次の手順を完了します。

1.  **[PC 設定]** > **[ネットワーク]** > **[社内ネットワーク]** の順に移動します。
2.  **[社内ネットワークへの参加]** で **[参加をやめる]** を選択します。
3.  **[デバイス管理をオンにする]** で、**[オフにする]** を選択します。
4.  開いたポップアップ ウィンドウで、**[オフにする]** を選択します。

## <a name="remove-your-windows-81-mobile-device"></a>Windows 8.1 モバイル デバイスを削除する
Windows 8.1 モバイル デバイスを Intune から削除するには、次の手順を完了します。

1.  **[設定]** > **[社内ネットワーク]** の順に移動します。
2.  登録解除する職場のアカウントをタップします。
3.  画面の下部にある **[削除]** をタップします。
4.  **[アカウントの削除]** ダイアログで、**[削除]** をタップします。  
## <a name="removing-your-personal-information-after-removing-the-company-portal"></a>ポータル サイトの削除後に個人情報を削除する
お使いの Windows デバイスでは、ポータル サイトによって 2 種類のデータが格納されます。

-   **診断ログ**: Microsoft によって収集される標準的なアプリ アクティビティ データ。 これは、ポータル サイト アプリをアンインストールするときに自動的に消去されます。 アプリ アクティビティ データとは、たとえばアプリが開いていた時間や、アプリがクラッシュしたかどうかに関するデータです。
-   **アプリケーション キャッシュ**: アイコンや設定など、アプリが動作するために必要なサポート ファイルです。

格納されているログとキャッシュを削除するには、次の手順のいずれかを実行します。

* [ポータル サイト アプリをアンインストールします](https://support.microsoft.com/help/4028003/windows-10-uninstall-apps-and-programs) 

* ポータル サイト アプリをリセットします。 **[設定]** アプリを開き、**[アプリ]** > **[ポータル サイト]** > **[詳細設定オプション]** > **[リセット]** の順に選びます。 

サポートが必要な場合は、 社内サポートに問い合わせてください。 連絡先情報については、[ポータル サイト Web サイト](https://portal.manage.microsoft.com#HelpDeskDialog)をご確認ください。
