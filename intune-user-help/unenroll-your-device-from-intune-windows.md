---
title: Intune から Windows デバイスを削除する | Microsoft Docs
description: Intune から Windows デバイスを削除する方法について説明します
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 03/28/2018
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
ms.openlocfilehash: 89a69f7d5cda31658cc9faf068a2a37698fdd93c
ms.sourcegitcommit: 4c06fa8e9932575e546ef2e880d96e96a0618673
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="remove-your-windows-device-from-intune"></a>Intune から Windows デバイスを削除する

お使いの Windows デバイスを Intune に登録しているが、そのデバイスで職場や学校のメール、アプリ、その他のリソースにアクセスする必要がなくなった場合、そのデバイスを管理から削除する必要があります。 Intune からお使いのデバイスを削除すると、その後はリソースにアクセスできなくなります。 管理からデバイスを削除した場合の詳細については、「[Intune からデバイスの登録を解除するとどうなりますか。](what-happens-if-you-unenroll-your-device-from-intune-windows.md)」を参照してください。

## <a name="remove-your-windows-10-device"></a>Windows 10 デバイスを削除する

1.  アプリの一覧で、 **ポータル サイト** アプリをタップします。

2.  職場または学校の資格情報でサインインします。

3.  **[デバイス]** で、登録を解除するデバイスを選択します。

4.  **[削除]** &gt; **[削除]** の順にタップします。

## <a name="remove-your-windows-81-computer"></a>Windows 8.1 コンピューターを削除する

1.  **[PC 設定]** &gt; **[ネットワーク]** &gt; **[ワークプレース]** の順に移動します。

2.  **[社内ネットワークへの参加]** で **[参加をやめる]** を選択します。

3.  **[デバイス管理をオンにする]** で、**[オフにする]** を選択します。

4.  開いたポップアップ ウィンドウで、**[オフにする]** を選択します。

## <a name="remove-your-windows-phone-81-mobile-device"></a>Windows Phone 8.1 モバイル デバイスを削除する

1.  **[設定]** &gt; **[社内]** の順にタップします。

2.  登録解除する職場のアカウントをタップします。

3.  画面の下部にある **[削除]** をタップします。

4.  **[アカウントの削除]** ダイアログで、**[削除]** をタップします。

## <a name="removing-your-personal-information-after-removing-the-company-portal"></a>ポータル サイトの削除後に個人情報を削除する

お使いの Windows デバイスでは、ポータル サイトによって 2 種類のデータが格納されます。

-   **診断ログ**: アプリを起動していた時間やクラッシュの発生など、Microsoft によって回収された標準的なアプリ アクティビティ データは、ポータル サイト アプリがアンインストールされたときに自動的に消去されます。
-   **アプリケーション キャッシュ**: アプリが動作するには、アイコンや設定など、特定のサポート ファイルを格納する必要があります。

この情報を完全に削除するには、いくつかの手順を踏む必要があります。

### <a name="uninstall-the-company-portal"></a>ポータル サイトをアンインストールする  

[ポータル サイト アプリをアンインストールする](https://support.microsoft.com/help/4028003/windows-10-uninstall-apps-and-programs)と、お使いのデバイスに格納されているアプリ データの一部が削除されます。  

### <a name="reset-the-company-portal"></a>ポータル サイトをリセットする

[設定] でアプリをリセットすることで、ポータル サイトのアプリ データの残りをリセットできます。 **[設定]**、**[アプリと機能]**、**[ポータル サイト]**、**[詳細オプション]**、**[リセット]** の順に開きます。

サポートが必要な場合は、 社内サポートに問い合わせてください。 連絡先情報については、[ポータル サイト Web サイト](https://portal.manage.microsoft.com#HelpDeskDialog)をご確認ください。
