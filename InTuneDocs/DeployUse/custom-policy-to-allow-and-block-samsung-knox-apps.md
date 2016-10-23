---
title: "KNOX が許可するアプリとブロックするアプリ |Microsoft Intune"
description: "KNOX が許可するアプリとブロックするアプリの一覧を作成するためのカスタム プロファイル。"
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 10/10/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bbc8e0df-7bf3-494e-8bc4-dac59a98ab41
ms.reviewer: chrisbal
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c7679d624ba22b2a062ef2534a642e38a5f57fde
ms.openlocfilehash: 273627573f58e1bde4fd19c548ce87639f25ca4b



---
# カスタム ポリシーを使用して、Samsung KNOX デバイス用のアプリを許可またはブロックする

次のいずれかを作成する Microsoft Intune のカスタム ポリシーを作成するには、このトピックの手順を使用します。

- デバイスでの実行をブロックするアプリの一覧。 この一覧のアプリは、ポリシー適用時に既にインストールされていた場合でも、実行をブロックされます。
- デバイスのユーザーが Google Play ストアからインストールできるアプリの一覧。 一覧のアプリのみをインストールできます。 他のアプリはストアからインストールできません。

これらの設定は、Samsung KNOX を実行するデバイスでのみ使用できます。

## 許可するアプリ一覧またはブロックするアプリ一覧を作成するには

1. [Microsoft Intune 管理コンソール](https://manage.microsoft.com/)で、**[ポリシー]、** &gt; **[構成ポリシー]** &gt; **[追加]** の順に選択します。
2. **[新しいポリシーの作成]** ダイアログ ボックスで、**[Android]** を展開し、**[カスタム構成]** を選んで、**[ポリシーを作成する]** を選びます。
3. ポリシーの名前と説明 (オプション) を指定し、**[OMA-URI 設定]** セクションで **[追加]** を選びます。
4. **[OMA-URI 設定の追加または編集]** ダイアログ ボックスで以下を指定します。デバイスでの実行をブロックするアプリの一覧の場合:
    
    - **設定の名前:** 「**PreventStartPackages**」と入力します。
    - **設定の説明:** "実行をブロックするアプリの一覧" のようなオプションの説明を入力します。
    -   **データの種類:** ドロップダウン リストで **[文字列]** を選びます。
    -   **OMA-URI:** 「**./Vendor/MSFT/PolicyManager/My/ApplicationManagement/PreventStartPackages**」と入力します。
    -   **値:** ブロックするアプリ パッケージ名の一覧を入力します。 区切り記号としては、**; : , ****|** を使用できます。 (例: package1;package2;)

    他のすべてのアプリの実行中にユーザーが Google Play ストアからインストールできるアプリの一覧の場合:

    - **設定の名前:** 「**AllowInstallPackages**」と入力します。
    - **設定の説明:** "ユーザーが Google Play からインストールできるアプリの一覧" といったオプションの説明を入力します。
    - **データの種類:** ドロップダウン リストで **[文字列]** を選びます。
    - **OMA-URI:** 「**./Vendor/MSFT/PolicyManager/My/ApplicationManagement/AllowInstallPackages**」と入力します。
    - **値:** ブロックするアプリ パッケージ名の一覧を入力します。 区切り記号としては、**; : , ****|** を使用できます。 (例: package1;package2;)

4. **[OK]** をクリックし、**[ポリシーの保存]** をクリックします。 

>[!TIP]
> Google Play ストアでアプリを参照して、アプリのパッケージ ID を確認できます。 パッケージ ID は、アプリのページの URL に含まれます。 たとえば、Microsoft Word アプリのパッケージ ID は **com.microsoft.office.word** です。

各対象デバイスの次のチェックイン時に、アプリの設定が適用されます。


## ポリシーの展開

1.   **[ポリシー]** ワークスペースで、展開するポリシーを選択し、 **[展開の管理]**をクリックします。

2.  **[展開の管理]** ダイアログ ボックスで、ポリシーを展開するユーザー グループを 1 つまたは複数選び、**[追加]** &gt; **[OK]** をクリックします。

 
展開済みポリシーを選択すると、ポリシー一覧の下部に展開についての詳細が表示されます。

### 関連項目
[Microsoft Intune の Android および Samsung KNOX 構成ポリシー設定](android-policy-settings-in-microsoft-intune.md)



<!--HONumber=Oct16_HO2-->


