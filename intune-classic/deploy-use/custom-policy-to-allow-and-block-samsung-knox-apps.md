---
title: KNOX が許可するアプリとブロックするアプリ
description: KNOX が許可するアプリとブロックするアプリの一覧を作成するためのカスタム プロファイル。
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 11/02/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: bbc8e0df-7bf3-494e-8bc4-dac59a98ab41
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: a47e1388f640f96c2650e284ae0a5311fd816ba7
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2018
---
# <a name="use-custom-policies-to-allow-and-block-apps-for-samsung-knox-standard-devices"></a>カスタム ポリシーを使用して、Samsung KNOX Standard デバイス用のアプリを許可またはブロックする

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

次のいずれかを作成する Microsoft Intune のカスタム ポリシーを作成するには、このトピックの手順を使用します。

- デバイスでの実行をブロックするアプリの一覧。 この一覧のアプリは、ポリシー適用時に既にインストールされていた場合でも、実行をブロックされます。
- デバイスのユーザーが Google Play ストアからインストールできるアプリの一覧。 一覧のアプリのみをインストールできます。 他のアプリはストアからインストールできません。

これらの設定は、Samsung KNOX Standard を実行するデバイスでのみ使用できます。

## <a name="to-create-an-allowed-or-blocked-app-list"></a>許可するアプリ一覧またはブロックするアプリ一覧を作成するには

1. [Microsoft Intune 管理コンソール](https://manage.microsoft.com/)で、**[ポリシー]、** &gt; **[構成ポリシー]** &gt; **[追加]** の順に選択します。
2. **[新しいポリシーの作成]** ダイアログ ボックスで、**[Android]** を展開し、**[カスタム構成]** を選んで、**[ポリシーを作成する]** を選びます。
3. ポリシーの名前と説明 (オプション) を指定し、**[OMA-URI 設定]** セクションで **[追加]** を選びます。
4. **[OMA-URI 設定の追加または編集]** ダイアログ ボックスで以下を指定します。デバイスでの実行をブロックするアプリの一覧の場合:
    
    - **設定の名前。** 「**PreventStartPackages**」と入力します。
    - **設定の説明。** "実行をブロックするアプリの一覧" のようなオプションの説明を入力します。
    -   **データ型。** ドロップダウン リストで **[文字列]** を選びます。
    -   **OMA-URI。** 「**./Vendor/MSFT/PolicyManager/My/ApplicationManagement/PreventStartPackages**」と入力します。
    -   **値。** ブロックするアプリ パッケージ名の一覧を入力します。 区切り記号としては、**; : ,** **|** を使用できます。 (例: package1;package2;)

    他のすべてのアプリの実行中にユーザーが Google Play ストアからインストールできるアプリの一覧の場合:

    - **設定の名前。** 「**AllowInstallPackages**」と入力します。
    - **設定の説明。** "ユーザーが Google Play からインストールできるアプリの一覧" といったオプションの説明を入力します。
    - **データ型。** ドロップダウン リストで **[文字列]** を選びます。
    - **OMA-URI。** 「**./Vendor/MSFT/PolicyManager/My/ApplicationManagement/AllowInstallPackages**」と入力します。
    - **値。** ブロックするアプリ パッケージ名の一覧を入力します。 区切り記号としては、**; : ,** **|** を使用できます。 (例: package1;package2;)

4. **[OK]** をクリックし、**[ポリシーの保存]** をクリックします。 

>[!TIP]
> Google Play ストアでアプリを参照して、アプリのパッケージ ID を確認できます。 パッケージ ID は、アプリのページの URL に含まれます。 たとえば、Microsoft Word アプリのパッケージ ID は **com.microsoft.office.word** です。

各対象デバイスの次のチェックイン時に、アプリの設定が適用されます。


## <a name="deploy-the-policy"></a>ポリシーの展開

1.  **[ポリシー]** ワークスペースで、展開するポリシーを選択し、 **[展開の管理]**をクリックします。

2.  **[展開の管理]** ダイアログ ボックスで、ポリシーを展開するユーザー グループを 1 つまたは複数選び、**[追加]** &gt; **[OK]** をクリックします。

 
展開済みポリシーを選択すると、ポリシー一覧の下部に展開についての詳細が表示されます。

### <a name="see-also"></a>関連項目
[Microsoft Intune の Android および Samsung KNOX ポリシー設定](android-policy-settings-in-microsoft-intune.md)
