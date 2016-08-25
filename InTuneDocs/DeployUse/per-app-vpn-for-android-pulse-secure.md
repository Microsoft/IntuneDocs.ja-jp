---
title: "Android 用の Pulse Secure を使用したアプリごとの VPN | Microsoft Intune"
description: "Intune で管理する、アプリごとの VPN プロファイルを Android デバイスに作成できます。"
keywords: 
author: nbigman
manager: angrobe
ms.date: 07/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ac65e906-3922-429f-8d9c-d313d3126645
ms.reviewer: chrisbal
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a2464a9d2276319f75a3da7db70c2613152bed9b
ms.openlocfilehash: 177ed5f693b8f1ce16d96e1b3e729630d661475f


---

# カスタム ポリシーを使用して、Android デバイスにアプリごとの VPN プロファイルを作成する

Intune で管理される Android デバイス用にアプリごとの VPN プロファイルを作成できます。 最初に、Pulse Secure 接続の種類を使用する VPN プロファイルを作成します。 次に、特定のアプリと VPN プロファイルを関連付けるカスタム構成ポリシーを作成します。 ポリシーを Android デバイスまたはユーザー グループに展開した後は、ユーザーがそれらのデバイス上の指定されているアプリの 1 つの起動すると、そのアプリの VPN 接続が開きます。

> [!NOTE]
>
> このプロファイルに対しては Pulse Secure 接続タイプのみがサポートされます。


### 手順 1: VPN プロファイルを作成する

1. [Microsoft Intune 管理コンソール](https://manage.microsoft.com)で、**[ポリシー]**  >  **[ポリシーの追加]** を選択します。
2. 新しいポリシー用のテンプレートを選ぶには、**[Android]** を展開し、**[VPN プロファイル (Android 4 以降)]** を選びます。
3. テンプレートの **[接続の種類]** に **[Pulse Secure]** を選択します。
4. VPN プロファイルの作成を終了して保存します。 VPN プロファイルの詳細については、「[VPN 接続](../deploy-use/vpn-connections-in-microsoft-intune.md)」をご覧ください。

> [!NOTE]
>
> VPN プロファイル名は、次の手順で使用するためメモしておきます。 たとえば、MyAppVpnProfile などです。

### 手順 2: カスタム構成ポリシーを作成する

   1. Intune 管理コンソールで、**[ポリシー]** > **[ポリシーの追加]** > **[Android]** > **[カスタム構成]** > **[ポリシーの作成]** の順に選択します。
   2. ポリシーの名前を入力します。
   3. **[OMA-URI 設定]**で **[追加]** を選択します。
   4. 設定の名前を入力します。
   5. **[データ型]** に **[文字列]** を指定します。
   6. **[OMA-URI]** には、**./Vendor/MSFT/VPN/Profile/*Name*/PackageList** の文字列を指定します。ここの *Name* は手順 1 でメモした VPN プロファイル名です。 この例では、文字列は **./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/PackageList** になります。
   7.   **[値]** には、プロファイルと関連付けるセミコロンで区切られたパッケージの一覧を入力します。 たとえば、Excel と Google Chrome ブラウザーで VPN 接続を使用するには、「**com.microsoft.office.excel;com.android.chrome**」と入力します。


    ![Android のアプリごとの VPN カスタム ポリシーの例](..\media\android_per_app_vpn_oma_uri.png)

#### アプリの一覧をブラックリストまたはホワイトリストとして設定する (省略可能)
  **BLACKLIST** 値を使用すると、VPN 接続を使用*できない*アプリの一覧を指定できます。 他のすべてのアプリは、VPN を使用して接続されます。
または、**WHITELIST** 値を使用して、VPN 接続を使用*できる*アプリの一覧を指定することもできます。 一覧に含まれないアプリは、VPN 経由で接続しません。
  1.    **[OMA-URI 設定]**で **[追加]** を選択します。
  2.    設定の名前を入力します。
  3.    **[データ型]** に **[文字列]** を指定します。
  4.    **[OMA-URI]** には、**./Vendor/MSFT/VPN/Profile/*Name*/Mode** の文字列を使用します。ここの *Name* は手順 1 でメモした VPN プロファイル名です。 この例では、文字列は **./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/Mode** になります。
  5.    **[値]** には、「**BLACKLIST**」または「**WHITELIST**」と入力します。



### 手順 3: 両方のポリシーを展開する

*両方*のポリシーは、*同じ* Intune グループに展開する必要があります。

1.  **[ポリシー]** ワークスペースで、展開するポリシーを選び、**[展開の管理]** を選びます。
2.   **[展開の管理]** ダイアログ ボックスで、次の操作を実行します。
    -   **ポリシーを展開するには**、ポリシーを展開する 1 つ以上のグループを選択して、**[追加]** > **[OK]** の順に選択します。
    -   **ポリシーを展開せずにダイアログ ボックスを閉じるには**、**[キャンセル]** を選択します。

 **[ポリシー]** ワークスペースの **[概要]** ページに表示されるステータスの概要とアラートを見ると、注意が必要なポリシーの問題を識別できます。 ステータスの概要は **[ダッシュボード]** ワークスペースにも表示されます。



<!--HONumber=Aug16_HO3-->


