---
title: Intune から Android デバイスを削除する方法 | Microsoft Docs
description: Intune から Android デバイスの登録を解除する方法について説明します
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/23/2018
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
ms.openlocfilehash: d932005c955afed7f16e9766b559b77b2cd43182
ms.sourcegitcommit: 604b29c480b24270b5debc3e5f3141c8149ee6ed
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/24/2018
ms.locfileid: "49959487"
---
# <a name="unenroll-your-android-device-from-management"></a>管理から Android デバイスの登録を解除する  

登録されている Android デバイスを削除し、組織によって管理されないようにします。 この記事では、ポータル サイト アプリからデバイスを削除する方法について説明します。 デバイスを削除すると次のようになります。  

* そのデバイスでは、組織の保護されたデータとリソースにアクセスできなくなります。
* そのデバイスはポータル サイトに表示されなくなります。
* ポータル サイトからアプリをインストールできなくなります。
* 追加時にデバイスで変更した設定がある場合 (カメラを無効にする、特定のパスワードの長さを必須にするなど)、その設定は適用されなくなります。  

1. ポータル サイトで、右上隅にある縦に並んだ 3 つのドットをタップします。 操作メニューが開きます。

   ![右上隅にアクション メニューが開いた Android 用ポータル サイト アプリの画像です。 [マイ プロファイル]、[設定] の下と、[使用条件]、[ヘルプとフィードバック]、[概要] の上に、新しい [ポータル サイトの削除] オプションが 3 つ目のオプションとして表示されます。](./media/android_remove_cp_menu_action_after_1705.png)

2. **[ポータル サイトの削除]** をタップします。  

3. デバイスを登録解除した後どうなるかについてのメッセージが表示されます。 **[OK]** をタップし、ポータル サイトからデバイスを削除することを確認します。

   ![アクション メニューから新しい [ポータル サイトの削除] オプションを選択した後に表示される確認ダイアログの画像です。 "ポータル サイトの削除により、デバイスは会社のサポートによる管理を離れ、会社のデータ、会社のアプリ、会社の電子メールに対するデバイスのアクセス権限が削除される可能性がある" ことを示すダイアログが表示されます。 [はい] を選択すると、ポータル サイト アプリを削除するか確認するメッセージが表示されます。](./media/android_remove_cp_menu_confirmation_after_1705.png)

## <a name="removing-data-collected-by-the-company-portal-app"></a>ポータル サイト アプリによって収集されたデータを削除する  

Android 用のポータル サイト アプリによってお使いのデバイスに格納されているすべてのデータを削除するには:

-   [アプリケーション] でアプリをクリックし、"データの消去" ボタンをクリックし、アプリ データを消去します。
-   フォルダー '\storage\internal storage\Android\data\com.microsoft.windowsintune.companyportal' を削除します。

## <a name="uninstall-the-company-portal-app"></a>ポータル サイト アプリをアンインストールする  
ポータル サイトはデバイス管理アプリなので、[デバイスをその管理から登録解除する](unenroll-your-device-from-intune-android.md#unenroll-your-android-device-from-management)までアンインストールすることはできません。 それが完了した後、ポータル サイト アプリのアイコンを **[アンインストール]** と表示されるまで長押しします。 **[アンインストール]** をタップしてデバイスからアプリを削除します。  

または、**[設定]** > **[アプリ]** > **[ポータル サイト]** > **[アンインストール]** の順にタップします。  

サポートが必要な場合は、 社内サポートに問い合わせてください。 連絡先情報については、[ポータル サイト Web サイト](https://go.microsoft.com/fwlink/?linkid=2010980)をご確認ください。
