---
title: "Intune ポリシーによる Samsung KNOX 用アプリの許可/禁止"
titleSuffix: Intune Azure preview
description: "Intune Azure プレビュー: カスタム プロファイルを作成して、Samsung KNOX Standard デバイス用のアプリを許可またはブロックします。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d035ebf5-85f4-4001-a249-75d24325061a
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: dea090e108d5ea023dc64d8d168b25d30b688cb2
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017



---
# <a name="use-custom-policies-to-allow-and-block-apps-for-samsung-knox-standard-devices-in-microsoft-intune"></a>Microsoft Intune でカスタム ポリシーを使用して Samsung KNOX Standard デバイス用のアプリを許可またはブロックする
[!INCLUDE[azure_preview](./includes/azure_preview.md)]次のいずれかを作成する Microsoft Intune のカスタム ポリシーを作成するには、このトピックの手順を使用します。

- デバイスでの実行をブロックするアプリの一覧。 この一覧のアプリは、ポリシー適用時に既にインストールされていた場合でも、実行をブロックされます。
- デバイスのユーザーが Google Play ストアからインストールできるアプリの一覧。 一覧のアプリのみをインストールできます。 他のアプリはストアからインストールできません。

これらの設定は、Samsung KNOX Standard を実行するデバイスでのみ使用できます。

## <a name="create-an-allowed-or-blocked-app-list"></a>許可されているアプリまたはブロックされているアプリの一覧の作成

1. Azure ポータルにサインインします。
2. **[その他のサービス]** > **[その他]** > **[Intune]** の順に選択します。
3. **[Intune]** ブレードで、**[デバイス構成]** を選択します。
2. **[デバイス構成]** ブレードで、**[管理]** > **[プロファイル]** の順に選択します。
2. プロファイルの一覧ブレードで、**[プロファイルを作成します]** を選択します。
3. **[プロファイルを作成します]** ブレードで、デバイス プロファイルの**名前**と省略可能な**説明**を入力します。
2. **[プラットフォームの種類]** では **[Android]** を、[プロファイルの種類] では **[カスタム]** を選択します。
3. **[設定]** をクリックします。
3. **[OMA-URI のカスタム設定]** ブレードで、**[追加]** を選択します。
4. **[OMA-URI 設定の追加または編集]** ダイアログ ボックスで、以下を指定します。

### <a name="for-a-list-of-apps-that-are-blocked-from-running-on-the-device"></a>デバイスでの実行がブロックされているアプリの一覧の場合:

- **[名前]** - 「**PreventStartPackages**」と入力します。
- **[説明]** - "実行されないようにブロックされているアプリの一覧" のような説明 (省略可能) を入力します。
-     **[データ型]** - ドロップダウン リストで **[文字列]** を選択します。
-     **[OMA-URI]** - 「**./Vendor/MSFT/PolicyManager/My/ApplicationManagement/PreventStartPackages**」と入力します
-     **[値]** - ブロックするアプリ パッケージ名の一覧を入力します。 区切り記号としては、**; : ,** **|** を使用できます。 (例: package1;package2;)

### <a name="for-a-list-of-apps-that-users-are-allowed-to-install-from-the-google-play-store-while-excluding-all-other-apps"></a>他のすべてのアプリの実行中にユーザーが Google Play ストアからインストールできるアプリの一覧の場合:
- **[名前]** - 「**AllowInstallPackages**」と入力します。
- **[説明]**: "ユーザーが Google Play からインストールできるアプリの一覧" のような説明 (省略可能) を入力します。
- **[データ型]** - ドロップダウン リストで **[文字列]** を選択します。
- **[OMA-URI]** - 「**./Vendor/MSFT/PolicyManager/My/ApplicationManagement/AllowInstallPackages**」と入力します
- **[値]** - 許可するアプリ パッケージ名の一覧を入力します。 区切り記号としては、**; : ,** **|** を使用できます。 (例: package1;package2;)

4. **[OK]** をクリックし、**[プロファイルを作成します]** ブレードで **[作成]** を選択します。

>[!TIP]
> Google Play ストアでアプリを参照して、アプリのパッケージ ID を確認できます。 パッケージ ID は、アプリのページの URL に含まれます。 たとえば、Microsoft Word アプリのパッケージ ID は **com.microsoft.office.word** です。

各対象デバイスの次のチェックイン時に、アプリの設定が適用されます。


<!---## Assign the custom profile--->

