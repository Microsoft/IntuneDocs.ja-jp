---
title: "アプリを展開する方法 | Microsoft Intune"
description: "このトピックの情報を使用して、Microsoft Intune でアプリを展開できます。"
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b42019e-73da-4538-a496-212f11d5bf9b
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6b6a5e2435a3cdffeaf27b0045dee9b8263cdc7a
ms.openlocfilehash: 1e6e0656fb3da0d77dab10736e7b1607d77e6335

---
# Deploy apps in Microsoft Intune (Microsoft Intune でアプリを展開する)

このトピックの情報を使用して、Microsoft Intune でアプリを展開できます。


## アプリを展開する
この手順では、選択したデバイスまたはユーザーのグループにアプリを展開します。

### アプリを展開するには

1. [Microsoft Intune 管理コンソール](https://manage.microsoft.com)で、**[アプリ]** &gt; **[アプリ]** の順にクリックし、管理するアプリの一覧を表示します。

2.  展開するアプリを選択し、**[展開の管理]** をクリックします。

3.  *[&lt;アプリ名&gt;]* ダイアログ ボックスで、**[グループの選択]** ページで、アプリを展開するユーザー グループまたはデバイス グループを選択します。

4.  **[展開アクション]** ページで、次を構成します。

    - **承認** - 展開の詳細を選択します。
        - **[必須]** (インストール必須)
        - **[使用可能]** (必要に応じて、ユーザーは会社のポータルからインストールします)
        - **[該当なし]** (アプリは会社のポータルにはインストールされていないか、表示されません)
        - **[アンインストール]** (アプリは対象となるデバイスからアンインストールされます)
    - **期限** - 必要なインストールに対し、アプリをいつ展開するかを選択します。 定義済みの値から選択するか、**[カスタム]** を選択し、独自の期限を構成できます。

5. 展開するアプリがモバイル アプリケーション管理ポリシーで構成できる場合、**[モバイル アプリの管理]** ページが表示されます。 このページで、このアプリに関連付けるモバイル アプリケーションの管理ポリシーを選択します。

    [モバイル アプリケーション管理ポリシーに対応する Microsoft アプリを確認してください。](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx)

6. 展開するアプリに Intune VPN プロファイルとの互換性がある場合、**[VPN プロファイル]** ページが表示されます。 このページで、展開した VPN プロファイルに iOS アプリを関連付けることができます。 アプリを起動すると、VPN 接続が自動的に開きます。 VPN プロファイルを使用できるようにするには、**アプリごとの VPN** プロファイル設定を有効にする必要があります。
 プロファイルをアプリと関連付ける方法に関する情報など、VPN プロファイルを構成する方法については、「[Microsoft Intune での VPN 接続](vpn-connections-in-microsoft-intune.md)」をご覧ください。

## 例

この例では、アプリを **[使用可能]** として iOS デバイスに展開します。
ユーザーのデバイスでポータル サイトにアプリが表示され、そこからアプリをインストールできます。

たとえば、このスクリーンショットでは、**[外部リンク]** インストール タイプとカスタム アイコンを使用して Bing for iOS アプリを展開しています。 **[このアプリをポータル サイトでおすすめアプリとして強調表示する]** オプションが選択されています。  
![iOS の使用可能アプリ](./media/available-install-on-iOS.png)

アプリを **[必須]** として iOS デバイスに展開した場合は、アプリがインストール可能になったことを知らせる通知がユーザーに届きます。 たとえば、このスクリーンショットでは、種類が **[アプリ ストアの管理されている iOS アプリ]** のインストールで Work Folders for iOS アプリが展開されました。  
![iOS の必須アプリ](./media/iOS-Required-install.PNG)

## 次のステップ

アプリケーションを展開した後、その進行状況を監視できます。 詳細については、「[Monitor apps in Microsoft Intune](monitor-apps-in-microsoft-intune.md)」 (Microsoft Intune でアプリを監視する) を参照してください。



<!--HONumber=Aug16_HO5-->


