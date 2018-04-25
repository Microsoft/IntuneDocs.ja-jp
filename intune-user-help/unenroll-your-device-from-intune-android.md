---
title: Intune から Android デバイスを削除する方法 | Microsoft Docs
description: Intune から Android デバイスの登録を解除する方法について説明します
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 03/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f40aab26-7613-48cc-a74e-de83df9465a4
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: ec3c0a1c8ce4e04f4d23fb01e7c2525d8f2eed5b
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-remove-your-android-device-from-intune"></a>Intune から Android デバイスを削除する方法

Intune から Android デバイスを削除した後は、会社のリソースにアクセスできなくなります。  管理からデバイスを削除した場合の詳細については、「[Intune からデバイスの登録を解除するとどうなりますか。](what-happens-if-you-unenroll-your-device-from-intune-android.md)」を参照してください。

## <a name="removing-the-device-from-the-company-portal-app"></a>ポータル サイト アプリからデバイスを削除する

Intune とポータル サイト アプリからデバイスを削除するには、以下の手順に従います。

1. ポータル サイト アプリの右上隅にある垂直に並んだ 3 つのドットをタップして、**アクション メニュー**を開きます。

   ![右上隅にアクション メニューが開いた Android 用ポータル サイト アプリの画像です。 [マイ プロファイル]、[設定] の下と、[使用条件]、[ヘルプとフィードバック]、[概要] の上に、新しい [ポータル サイトの削除] オプションが 3 つ目のオプションとして表示されます。](./media/android_remove_cp_menu_action_after_1705.png)

2. **[ポータル サイトの削除]** をタップします。

3. ポータル サイトを削除してよいかを確認する確認メッセージが表示されます。 デバイスを登録解除するとどうなるかについての情報も表示されます。 このメッセージを確認したら、**[OK]** をタップしてアプリを削除します。

   ![アクション メニューから新しい [ポータル サイトの削除] オプションを選択した後に表示される確認ダイアログの画像です。 "ポータル サイトの削除により、デバイスは会社のサポートによる管理を離れ、会社のデータ、会社のアプリ、会社の電子メールに対するデバイスのアクセス権限が削除される可能性がある" ことを示すダイアログが表示されます。 [はい] を選択すると、ポータル サイト アプリを削除するか確認するメッセージが表示されます。](./media/android_remove_cp_menu_confirmation_after_1705.png)

## <a name="removing-data-collected-by-the-company-portal-app"></a>ポータル サイト アプリによって収集されたデータを削除する

Android 用のポータル サイト アプリによってお使いのデバイスに格納されているすべてのデータを削除するには:

-   [アプリケーション] でアプリをクリックし、"データの消去" ボタンをクリックし、アプリ データを消去します。
-   フォルダー '\storage\internal storage\Android\data\com.microsoft.windowsintune.companyportal' を削除します。

サポートが必要な場合は、 社内サポートに問い合わせてください。 連絡先情報については、[ポータル サイト Web サイト](https://portal.manage.microsoft.com#HelpDeskDialog)をご確認ください。
