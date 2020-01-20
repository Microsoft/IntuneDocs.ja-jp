---
title: Microsoft Intune ポリシーによる Samsung KNOX 用アプリの許可/禁止
titleSuffix: ''
description: カスタム プロファイルを作成して、Samsung KNOX Standard デバイス用のアプリを許可またはブロックします。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/18/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4b83a0339d87375502159467af323fceae5eb6e2
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207079"
---
# <a name="use-custom-policies-in-microsoft-intune-to-allow-and-block-apps-for-samsung-knox-standard-devices"></a>Microsoft Intune でカスタム ポリシーを使用して Samsung KNOX Standard デバイス用のアプリを許可またはブロックする 

次のいずれかを作成する Microsoft Intune のカスタム ポリシーを作成するには、この記事の手順を使用します。

- デバイスでの実行をブロックするアプリの一覧。 この一覧のアプリは、ポリシー適用時に既にインストールされていた場合でも、実行をブロックされます。
- デバイスのユーザーが Google Play ストアからインストールできるアプリの一覧。 一覧のアプリのみをインストールできます。 他のアプリはストアからインストールできません。

これらの設定は、Samsung KNOX Standard を実行するデバイスでのみ使用できます。

## <a name="create-an-allowed-or-blocked-app-list"></a>許可されているアプリまたはブロックされているアプリの一覧の作成

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。
2. **[デバイス]** 、 **[構成プロファイル]** 、 **[プロファイルの作成]** の順に選択します。
3. 次の設定を入力します。

    - **名前**:プロファイルのわかりやすい名前を入力します。 後で簡単に識別できるよう、プロファイルに名前を付けます。 たとえば、適切なプロファイル名は**Windows phone カスタムプロファイル**です。
    - **説明**:設定の概要および他の重要な詳細がわかる説明を入力します。
    - **[プラットフォーム]** : **[Android]** を選択します。
    - **プロファイルの種類**: **[カスタム]** を選択します。

4. **[OMA-URI のカスタム設定]** で、 **[追加]** を選択します。 次の設定を入力します。

    デバイスでの実行がブロックされているアプリの一覧の場合:

    - **名前**:「**PreventStartPackages**」と入力します。
    - **説明**:設定の概要と、プロファイルを特定するために役立つその他の関連情報についての説明を入力します。 たとえば、**実行がブロックされているアプリの一覧**を入力します。
    - **[OMA-URI]** (大文字と小文字を区別):「 **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/PreventStartPackages**」と入力します。
    - **[データ型]** : **[文字列]** を選択します。
    - **値**:ブロックするアプリ パッケージ名の一覧を入力します。 区切り記号としては、`;`、`:`、または `|` を使用できます。 たとえば、「`package1;package2;`」と入力します。

   他のすべてのアプリの実行中にユーザーが Google Play ストアからインストールできるアプリの一覧の場合:

    - **名前**:「**AllowInstallPackages**」と入力します。
    - **[説明]** : 設定の概要と、プロファイルを特定するために役立つその他の関連情報についての説明を入力します。 たとえば、ユーザーが**Google Play からインストールできるアプリの一覧**を入力します。
    - **[OMA-URI]** (大文字と小文字を区別):「 **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/AllowInstallPackages**」と入力します。
    - **[データ型]** : **[文字列]** を選択します。
    - **値**:ブロックするアプリ パッケージ名の一覧を入力します。 区切り記号としては、`;`、`:`、または `|` を使用できます。 たとえば、「`package1;package2;`」と入力します。

5. **[OK]** を選択して変更を保存します。
6. 終わったら、 **[OK]**  >  **[作成]** の順に選択して Intune プロファイルを作成します。 完了すると、プロファイルが **[デバイス - 構成プロファイル]** の一覧に表示されます。

>[!TIP]
> Google Play ストアでアプリを参照して、アプリのパッケージ ID を確認できます。 パッケージ ID は、アプリのページの URL に含まれます。 たとえば、Microsoft Word アプリのパッケージ ID は **com.microsoft.office.word** です。

各対象デバイスの次のチェックイン時に、アプリの設定が適用されます。

## <a name="next-steps"></a>次のステップ

プロファイルは作成されましたが、まだ何も行われていません。 次に、[プロファイルを割り当て](../device-profile-assign.md)、[その状態を監視](device-profile-monitor.md)します。
