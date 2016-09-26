---
title: "Lookout for Work アプリを展開する | Microsoft Intune"
description: "Android 用の Lookout for Work アプリを構成して展開します。"
author: karthikaraman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 524c4209-ad57-4d35-955e-a00d796bf858
ms.reviewer: sandera
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9c2ffb5fe497d56d8250fe3dec7db606c2067a1c
ms.openlocfilehash: c43104ff199e1800bfded35154d2be0cfd0c40f3


---

# Lookout for Work アプリを構成して展開する
このリリースでは、Android 4.1 を実行するデバイス上の Lookout for Work がサポートされます。
## Android
このセクションでは、Intune に登録されている Android デバイス用に Lookout for Work アプリケーションを構成して展開する方法について説明します。  
* 手順 1:   [Microsoft Intune 管理者コンソール](https://manage.microsoft.com)で、**[アプリ]** に移動し、**[アプリの追加]** を選択します。   
* 手順 2:   発行元の **[ソフトウェア セットアップ]** ページで、**[外部リンク]** を選択し、URL "https://play.google.com/store/apps/details?id=com.lookout.enterprise" を指定します。
>[!NOTE]
>Managed Browser を要求するボックスをオンにしないでください。

* 手順 3:   **[ソフトウェアの説明]** ページで、次の情報を入力します。
  * **[発行元]:** Lookout Mobile Security
  * **[名前]:**   Lookout for Work
  * **[説明]:**  Lookout はモバイルの脅威に対する最適な保護を提供し、モバイル デバイスの安全を保ちます。 デバイスにインストールされた Lookout アプリは、デバイスを脅威から保護し、検出された脅威を管理者に通知します。
  * **[カテゴリ]:** コンピューターの管理
* 手順 4:  正常に完了すると、**[Microsoft Intune にデータが正常にアップロードされました]** というメッセージが表示されます。

Intune コンソールで **[アプリ]** をクリックすると、Lookout for Work アプリが一覧に表示されます。![Intune 管理者コンソールのアプリ ページの一覧に表示された Lookout for Work アプリのスクリーンショット](../media/mtp/lookout-app-listed-intune-console.png)

手順 5: この時点で、Intune には Lookout for Work Android アプリの展開方法がわかっています。   上の画面に表示されている Lookout for Work アプリを選択して **[展開の管理]** をクリックすることで、アプリをユーザーに展開できます。

Lookout MTP コンソールの [Enrollment Management] (登録管理) オプションで追加したものと同じユーザーを選択する必要があります。  Lookout MTP へのユーザー グループの追加の詳細については、「[Lookout MTP でサブスクリプションを構成する](set-up-your-subscription-with-lookout-mtp#configure-your-subscription-with-lookout-mtp)」セクションの手順 3 をご覧ください。
>[!IMPORTANT]
> Intune アプリ展開ウィザードは Azure AD のユーザー グループを認識せず、代わりに Intune のユーザー グループを使用します。 したがって、Lookout MTP コンソールで登録されている Azure AD のユーザー グループに基づいて Intune のユーザー グループを作成する必要があります ([こちら](plan-your-user-and-device-groups.md)のトピックを参照)。

手順 6: **[必須のインストール]** オプションを選択し、Lookout アプリがユーザーのデバイスに必ずインストールされるようにします。

### デバイスのアクティブ化
展開で **[必須のインストール]** オプションを選択すると、Lookout for Work アプリケーションがデバイスにプッシュされます。   

ユーザーがデバイスで Lookout for Work を開くと、アプリをアクティブ化し、[Sign in with Azure Active Directory] (Azure Active Directory でサインインする) オプションを選択するように求められます。 エンド ユーザーの詳細な手順については、次のトピックをご覧ください。

* [Android デバイスで Lookout for Work のインストールを求められる](http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android)

* [Android デバイスで Lookout for Work が検出した脅威を解決する必要がある](http://docs.microsoft.com/intune/enduser/you-need-to-resolve-a-threat-found-by-lookout-for-work-android)

## 次のステップ
* [コンプライアンス ポリシーでデバイスの脅威防御ルールを有効にする](enable-device-threat-protection-rule-in-compliance-policy.md)



<!--HONumber=Sep16_HO2-->


