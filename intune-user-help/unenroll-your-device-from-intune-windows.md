---
title: Intune 管理から Windows デバイスを削除する
description: Intune の管理から Windows デバイスを削除する方法について説明します
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/03/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 018bda65-7238-41f5-b92a-e5f67b7fe085
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: 4540c4d58bebcbec06e73eaf51d91d6685d0243b
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2020
ms.locfileid: "75859000"
---
# <a name="remove-your-windows-device-from-management"></a>管理から Windows デバイスを削除する

次のようなことが不要になった、登録済みの Windows デバイスを管理から削除します。  
* デバイスを職場または学校で使用する。 
* 職場または学校の電子メール、アプリ、またはその他のリソースにアクセスする。

デバイスの登録を解除すると、デバイスから学校または職場のリソースにアクセスできなくなります。 次の Windows デバイスを管理から削除できます。  
* Windows 10 デバイス 
* Windows 8.1 コンピューター
* Windows 8.1 電話
 
管理からデバイスを削除した後に何が起きるかについては、「[Intune からデバイスの登録を解除するとどうなりますか。](what-happens-if-you-unenroll-your-device-from-intune-windows.md)」を参照してください。  

## <a name="remove-your-windows-10-device"></a>Windows 10 デバイスを削除する
Windows 10 デバイスを管理から削除するには、次の手順を完了します。

### <a name="remove-in-company-portal-app-home-page"></a>ポータル サイト アプリの **[ホーム]** ページで削除する  

1. ポータル サイト アプリを開きます。
2. **[ホーム] ページ**で下の **[デバイス]** セクションまで移動します。
3. 削除するデバイスを選択します。
3. アプリの右上隅で、 **[詳細表示]** アイコンを選びます。
4. **[削除]** を選びます。 
5. デバイスの削除を確定するには、 **[削除]** を選びます。  

### <a name="remove-in-company-portal-app-device-context-menu"></a>ポータル サイト アプリのデバイス コンテキスト メニューで削除する  

1. ポータル サイト アプリを開き、 **[デバイス]** に移動します。

    ![[デバイス] セクションが強調表示された、Windows 用ポータル サイト アプリの [ホーム] ページのサンプル スクリーンショット。](./media/1809_CheckAccess_Context_Select_Device.png)

2. デバイスを右クリックするか、デバイスを押したままにしてその[コンテキスト メニュー](https://docs.microsoft.com//windows/uwp/design/controls-and-patterns/menus)を開きます。  

3. **[削除]** を選びます。  

    ![Windows 用ポータル サイト アプリの [ホーム] ページのサンプル スクリーンショット。 デバイスのコンテキスト メニューは、ページの **[デバイス]** セクションに表示され、[名前の変更]、[削除]、[アクセスの確認] アクションが表示されます。](./media/1809_DeviceContextMenu_Windows_CP.png)  

5. 確認ダイアログで、 **[詳細]** をクリックして、職場および学校のリソースへのアクセスがどのように変わる可能性があるかを確認します。 デバイスの削除を確定するには、 **[削除]** を選びます。   

     ![Windows 用ポータル サイト アプリの [ホーム] ページのサンプル スクリーンショット。 デバイスの上に [名前の変更] フィールドが表示されます。ここで、ユーザーが新しい名前を入力して [名前の変更] または [キャンセル] をクリックすることができます。](./media/1808_RemoveDevice_Popup.png)  


### <a name="remove-in-device-settings-app"></a>デバイス設定アプリでの削除
1. [設定] アプリを開きます。 
2. **[アカウント]**  >  **[職場または学校にアクセスする]** の順に移動します。
3. 接続されている、削除したいアカウントで、 **[切断]** を選びます。
4. デバイスの削除を確認するには、 **[はい]** を選びます。

## <a name="remove-your-windows-81-computer"></a>Windows 8.1 コンピューターを削除する
Windows 8.1 コンピューターを Intune から削除するには、次の手順を完了します。

1. **[PC 設定]**  >  **[ネットワーク]**  >  **[社内ネットワーク]** の順に移動します。
2. **[社内ネットワークへの参加]** で **[参加をやめる]** を選択します。
3. **[デバイス管理をオンにする]** で、 **[オフにする]** を選択します。
4. 開いたポップアップ ウィンドウで、 **[オフにする]** を選択します。

## <a name="remove-your-windows-81-phone"></a>Windows 8.1 電話を削除する
Windows 8.1 電話を Intune から削除するには、次の手順を完了します。

1. **[設定]**  >  **[社内ネットワーク]** の順に移動します。
2. 登録解除する職場のアカウントをタップします。
3. 画面の下部にある **[削除]** をタップします。
4. **[アカウントの削除]** ダイアログで、 **[削除]** をタップします。  
## <a name="removing-your-personal-information-after-removing-the-company-portal"></a>ポータル サイトの削除後に個人情報を削除する  

お使いの Windows デバイスでは、ポータル サイトによって 2 種類のデータが格納されます。

- **診断ログ**:Microsoft によって収集される標準的なアプリ アクティビティ データ。 これは、ポータル サイト アプリをアンインストールするときに自動的に消去されます。 アプリ アクティビティ データとは、たとえばアプリが開いていた時間や、アプリがクラッシュしたかどうかに関するデータです。
- **アプリケーション キャッシュ**:アイコンや設定など、アプリが動作するために必要なサポート ファイル。

格納されているログとキャッシュを削除するには、次の手順のいずれかを実行します。

* [ポータル サイト アプリをアンインストールします](https://support.microsoft.com/help/4028003/windows-10-uninstall-apps-and-programs) 

* ポータル サイト アプリをリセットします。 **[設定]** アプリを開き、 **[アプリ]**  >  **[ポータル サイト]**  >  **[詳細設定オプション]**  >  **[リセット]** の順に選びます。 

サポートが必要な場合は、 社内サポートに問い合わせてください。 連絡先情報については、[ポータル サイト Web サイト](https://go.microsoft.com/fwlink/?linkid=2010980)をご確認ください。
