---
title: Intune から Android デバイスを削除する方法 | Microsoft Docs
description: Intune ポータル サイトから Android デバイスを削除する
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: f40aab26-7613-48cc-a74e-de83df9465a4
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: be980a8cd2eb7f0cbe40002f73f9bc36a36d1193
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2020
ms.locfileid: "75859068"
---
# <a name="unenroll-your-android-device-from-management"></a>管理から Android デバイスの登録を解除する  

登録されている Android デバイスを削除し、組織によって管理されないようにします。 この記事では、ポータル サイト アプリからデバイスを削除する方法について説明します。 デバイスを削除すると次のようになります。  

* そのデバイスでは、組織の保護されたデータとリソースにアクセスできなくなります。
* そのデバイスはポータル サイトに表示されなくなります。
* ポータル サイトからアプリをインストールできなくなります。
* 追加時にデバイスで変更した設定がある場合 (カメラを無効にする、特定のパスワードの長さを必須にするなど)、その設定は適用されなくなります。  

> [!NOTE]
> Microsoft Intune アプリから会社所有のデバイスの登録を解除したり、削除したりすることはできません。 デバイスは、初期デバイスのセットアップ中に登録されており、組織のリソースにアクセスするために登録する必要があります。  

1. ポータル サイトで、右上隅にある縦に並んだ 3 つのドットをタップします。 操作メニューが開きます。

   ![右上隅にアクション メニューが開いた Android 用ポータル サイト アプリのスクリーンショット。 [マイ プロファイル]、[設定] の下と、[使用条件]、[ヘルプとフィードバック]、[概要] の上に、新しい [ポータル サイトの削除] オプションが 3 つ目のオプションとして表示されます。](./media/android_remove_cp_menu_action_after_1705.png)

2. **[ポータル サイトの削除]** をタップします。  

3. デバイスを登録解除した後どうなるかについてのメッセージが表示されます。 **[OK]** をタップし、ポータル サイトからデバイスを削除することを確認します。

   ![アクション メニューから新しい [ポータル サイトの削除] オプションを選択した後に表示される確認のスクリーンショット。](./media/android_remove_cp_menu_confirmation_after_1705.png)

## <a name="remove-data-collected-by-the-company-portal-app"></a>ポータル サイト アプリによって収集されたデータを削除する  

Android 用のポータル サイト アプリによってお使いのデバイスに格納されているすべてのデータを削除するには:

- アプリ データを消去するには、 **[アプリケーション]**  >  **<*アプリの名前*>**  >  **[データの消去]** をタップします。
- \storage\internal storage\Android\data\com.microsoft.windowsintune.companyportal フォルダーを削除します。

## <a name="uninstall-the-company-portal-app"></a>ポータル サイト アプリをアンインストールする

ポータル サイトは、デバイス管理アプリです。 ポータル サイトは、デバイスをその管理から登録解除するまでアンインストールすることはできません。 それが完了した後、ポータル サイト アプリのアイコンを **[アンインストール]** と表示されるまで長押しします。 **[アンインストール]** をタップしてデバイスからアプリを削除します。  

または、 **[設定]**  >  **[アプリ]**  >  **[ポータル サイト]**  >  **[アンインストール]** の順にタップします。  

### <a name="remove-the-company-portal-app-as-a-device-administrator"></a>デバイス管理者としてポータル サイト アプリを削除する

最後の手段として、デバイス管理者としてデバイスからアプリをアンインストールできます。  

会社所有のデバイスがある場合、ポータル サイトがデバイスに常にあることが組織から求められる場合があります。 ポータル サイトをアンインストールすると、アプリを再インストールするまで、電子メール、アプリ、Wi-Fi、VPN などの保護された会社のリソースにアクセスできなくなる可能性があります。 必要なアプリのインストール、更新、または削除の詳細については、「[Microsoft Intune にアプリを追加する](/intune/apps/apps-add#apps-that-are-added-automatically-by-intune)」を参照してください。

デバイス管理者としてポータル サイトを無効にする方法は、次のとおりです。 各設定の実際の名前は、Android デバイスで異なる場合があります。  

**オプション 1**:  

1. **[設定]**  >  **[セキュリティ]**  >  **[追加のセキュリティ設定]**  >  **[デバイス管理者]** の順に選択します。  
2. **[ポータル サイト]** の選択を解除します。  

**オプション 2**:

1. **[設定]**  >  **[ロック画面とセキュリティ]**  >  **[他のセキュリティ設定]**  > **デバイス管理者アプリ**の順に選択します。
2. **[ポータル サイト]** の選択を解除します。

サポートが必要な場合は、 社内サポートに問い合わせてください。 連絡先情報については、[ポータル サイト Web サイト](https://go.microsoft.com/fwlink/?linkid=2010980)をご確認ください。
