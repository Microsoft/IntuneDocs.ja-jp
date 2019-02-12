---
title: Microsoft Intune ポリシーによる Samsung KNOX 用アプリの許可/禁止
titlesuffix: ''
description: カスタム プロファイルを作成して、Samsung KNOX Standard デバイス用のアプリを許可またはブロックします。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/5/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e7c40f17ba05c19cd1bc0967f6d343e5871c0388
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2019
ms.locfileid: "55845688"
---
# <a name="use-custom-policies-in-microsoft-intune-to-allow-and-block-apps-for-samsung-knox-standard-devices"></a>Microsoft Intune でカスタム ポリシーを使用して Samsung KNOX Standard デバイス用のアプリを許可またはブロックする 

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

次のいずれかを作成する Microsoft Intune のカスタム ポリシーを作成するには、この記事の手順を使用します。

- デバイスでの実行をブロックするアプリの一覧。 この一覧のアプリは、ポリシー適用時に既にインストールされていた場合でも、実行をブロックされます。
- デバイスのユーザーが Google Play ストアからインストールできるアプリの一覧。 一覧のアプリのみをインストールできます。 他のアプリはストアからインストールできません。

これらの設定は、Samsung KNOX Standard を実行するデバイスでのみ使用できます。

## <a name="create-an-allowed-or-blocked-app-list"></a>許可されているアプリまたはブロックされているアプリの一覧の作成

1. [Azure ポータル](https://portal.azure.com) にサインインします。
2. **すべてのサービス** > **Intune** の順に選択します。 Intune は **[監視 + 管理]** セクションにあります。
3. **[Intune]** ウィンドウで、**[デバイス構成]** を選択します。
2. **[デバイス構成]** ウィンドウで、**[管理]**、**[プロファイル]** の順に選択します。
2. プロファイルの一覧ウィンドウで、**[プロファイルの作成]** を選択します。
3. **[プロファイルを作成します]** ウィンドウで、デバイス プロファイルの**名前**と省略可能な**説明**を入力します。
2. **[プラットフォーム]** には **[Android]** を、**[プロファイルの種類]** には **[カスタム]** を選択します。
3. **[設定]** をクリックします。
3. **[OMA-URI のカスタム設定]** ウィンドウで、**[追加]** を選択します。
4. **[OMA-URI 設定の追加または編集]** ダイアログ ボックスで、次の設定を指定します。

   デバイスでの実行がブロックされているアプリの一覧の場合:

   - **[名前]** - 「**PreventStartPackages**」と入力します。
   - **[説明]** - "実行されないようにブロックされているアプリの一覧" のような説明 (省略可能) を入力します。
   -    **[データ型]** - ドロップダウン リストで **[文字列]** を選択します。
   -    **[OMA-URI]** - 「**./Vendor/MSFT/PolicyManager/My/ApplicationManagement/PreventStartPackages**」と入力します
   -    **[値]** - ブロックするアプリ パッケージ名の一覧を入力します。 区切り記号としては、**; : ,** **|** を使用できます。 (例: package1;package2;)

   他のすべてのアプリの実行中にユーザーが Google Play ストアからインストールできるアプリの一覧の場合:
   - **[名前]** - 「**AllowInstallPackages**」と入力します。
   - **[説明]**: "ユーザーが Google Play からインストールできるアプリの一覧" のような説明 (省略可能) を入力します。
   - **[データ型]** - ドロップダウン リストで **[文字列]** を選択します。
   - **[OMA-URI]** - 「**./Vendor/MSFT/PolicyManager/My/ApplicationManagement/AllowInstallPackages**」と入力します
   - **[値]** - 許可するアプリ パッケージ名の一覧を入力します。 区切り記号としては、**; : ,** **|** を使用できます。 (例: package1;package2;)

4. **[OK]** をクリックし、**[プロファイルを作成します]** ウィンドウで **[作成]** を選択します。

>[!TIP]
> Google Play ストアでアプリを参照して、アプリのパッケージ ID を確認できます。 パッケージ ID は、アプリのページの URL に含まれます。 たとえば、Microsoft Word アプリのパッケージ ID は **com.microsoft.office.word** です。

各対象デバイスの次のチェックイン時に、アプリの設定が適用されます。


<!---## Assign the custom profile--->
