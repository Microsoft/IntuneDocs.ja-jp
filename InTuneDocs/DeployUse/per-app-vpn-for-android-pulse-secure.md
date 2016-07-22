---
title: "Android 用の Pulse Secure を使用したアプリごとの VPN | Microsoft Intune"
description: 
keywords: 
author: nbigman
manager: jeffgilb
ms.date: 05/08/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ac65e906-3922-429f-8d9c-d313d3126645
ms.sourcegitcommit: 40e5602a4675bd92a85001827fb43426c41ed1e3
ms.openlocfilehash: fc58e71a9b2279200dee2630aab7dbab727ea128


---

# カスタム ポリシーを使用して、Android デバイスにアプリごとの VPN プロファイルを作成する

Intune で管理する、アプリごとの VPN プロファイルを Android デバイスに作成できます。 まず、接続の種類として Pulse Secure を使用する VPN プロファイルを作成し、そのプロファイルと特定のアプリを関連付けるカスタム構成ポリシーを作成します。 これらのポリシーを Android デバイスまたはユーザー グループに展開すると、それらのデバイス上の指定されているアプリの 1 つの起動で、そのアプリの VPN 接続が開きます。 

### 手順 1: VPN プロファイルを作成する

1. [Microsoft Intune 管理コンソール](https://manage.microsoft.com)で、**[ポリシー]** > **[ポリシーの追加]** をクリックします。
2. **[Android]** を展開し、**[VPN プロファイル (Android 4 以降)]** を選択して、新しいポリシー用のテンプレートを選択します。

3. テンプレートの **[接続の種類]** に **[Pulse Secure]** を選択します。
4. VPN プロファイルを完了し保存します。 VPN プロファイルの詳細については、「[VPN 接続](vpn-connections-in-microsoft-intune.md)」をご覧ください。

> [!NOTE]
VPN プロファイル名は、次の手順で使用するためメモしておきます。 たとえば、**MyAppVpnProfile** です。
   
### 手順 2: カスタム構成ポリシーを作成する
    
   1. Intune 管理コンソールで、**[ポリシー]** -> **[ポリシーの追加]** -> **[Android]** -> **[カスタム構成]** -> **[ポリシーの作成]** の順に選択します。
   2. ポリシーの名前を指定します。
   3. **[OMA-URI 設定]** の下の **[追加]** をクリックします。
   4. 設定の名前を入力します。
   5. **[データ型]** に **[文字列]** を指定します。
   6. **[OMA-URI]** には、**./Vendor/MSFT/VPN/Profile/*Name*/PackageList** の文字列を指定します。ここの *Name* は手順 1. でメモした VPN プロファイル名です。 この例では、文字列は **./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/PackageList** になります。
   7.   **[値]** には、プロファイルと関連付けるセミコロンで区切られたパッケージの一覧を入力します。  たとえば、Excel と Google Chrome ブラウザーで VPN 接続を使用するには、**com.microsoft.office.excel;com.android.chrome** と入力します。
  

   ![Android のアプリごとの VPN カスタム ポリシーの例](..\media\android_per_app_vpn_oma_uri.png) 
#### アプリの一覧をブラックリストまたはホワイトリストとして設定する (省略可能)
**BLACKLIST** 値を使用すると、アプリの一覧が VPN の使用を許可*しない*よう指定できます。  他のすべてのアプリは、VPN を使用して接続されます。

または、**WHITELIST** の値を使用すると、指定したアプリ*のみ*が VPN 接続を使用できるよう指定できます。
 

1.  [OMA-URI] 設定で **[追加]** をクリックします。
2.  設定の名前を入力します。
3.  **[データ型]** に **[文字列]** を指定します。
4.  **[OMA-URI]** には、**./Vendor/MSFT/VPN/Profile/*Name*/Mode** の文字列を指定します。ここの *Name* は手順 1. でメモした VPN プロファイル名です。 この例では、文字列は **./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/Mode** になります。
5.  **[値]** に **[BLACKLIST]** または **[WHITELIST]** と入力します。 


   
### 手順 3: 両方のポリシーを展開する

*両方*のポリシーは、*同じ* Intune グループに展開する必要があります。

   1.   **[ポリシー]** ワークスペースで、展開するポリシーを選択し、 **[展開の管理]**をクリックします。

2.   **[展開の管理]** ダイアログ ボックスで、次の操作を実行します。

    -   **ポリシーを展開するには**、ポリシーを展開する対象となる 1 つ以上のグループを選択して、**[追加]** &gt; **[OK]** をクリックします。

    -   **ポリシーを展開せずにダイアログ ボックスを閉じるには**、**[キャンセル]** をクリックします。

 **[ポリシー]** ワークスペースの **[概要]** ページに表示されるステータスの概要とアラートを見ると、注意が必要なポリシーの問題を識別できます。 ステータスの概要は [ダッシュボード] ワークスペースにも表示されます。




<!--HONumber=Jul16_HO2-->


