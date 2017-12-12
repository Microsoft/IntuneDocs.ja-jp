---
title: "管理対象の iOS デバイス用アプリ構成ポリシーを追加する | Microsoft Docs"
titlesuffix: Azure portal
description: "アプリ構成ポリシーを使用して、実行時に構成データを iOS アプリに提供する方法について説明します。"
keywords: 
author: erikre
ms.author: erikre
manager: angrobe
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c9163693-d748-46e0-842a-d9ba113ae5a8
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a39b2d120a804d32b93b7a240af246327514b1b7
ms.sourcegitcommit: 67ec0606c5440cffa7734f4eefeb7121e9d4f94f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="add-app-configuration-policies-for-managed-ios-devices"></a>管理対象の iOS デバイス用アプリ構成ポリシーを追加する

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Microsoft Intune のアプリ構成ポリシーを使用して、ユーザーが iOS アプリを実行するときに設定を指定できます。 これらのポリシーをユーザーとデバイスに直接割り当てないでください。 代わりに、ポリシーをアプリに関連付け、そのアプリを割り当てます。 ポリシー設定は、アプリがポリシーをチェックするとき (通常はアプリの初回実行時) に使用されます。

> [!TIP]
> この種類のポリシーは現在、iOS 8.0 以降を実行しているデバイスでのみ有効です。 次の種類のアプリ インストールをサポートします。
>
> -   **App Store の管理対象 iOS アプリ**
> -   **iOS 用アプリ パッケージ**
>
> アプリのインストールの種類の詳細については、「[How to add an app to Microsoft Intune (Microsoft Intune にアプリを追加する方法)](apps-add.md)」を参照してください。

## <a name="create-an-app-configuration-policy"></a>アプリ構成ポリシーを作成する

1. Azure ポータルにサインインします。
2. **[その他のサービス]** > **[監視 + 管理]** + **[Intune]** の順に選択します。
3. **[モバイル アプリ]** ワークロードを選択します。
4. **[管理]** グループの **[アプリ構成ポリシー]** を選択し、**[追加]** を選択します。
5. 次の詳細を設定します。
    - **名前**<br>
      Azure Portal に表示されるプロファイルの名前。
    - **説明**<br>
      Azure Portal に表示されるプロファイルの説明。
    - **デバイス登録の種類**<br>
      **[管理対象デバイス]** を選択します。
6. **[プラットフォーム]** で **[iOS]** を選択します。
7.  **[関連アプリ]** を選択します。 次に、**[関連アプリ]** ブレードで、構成を適用する管理対象アプリを選択します。
8.  **[構成ポリシーの追加]** ブレードで、**[構成設定]** を選択します。
9. **[構成設定の形式]** を選択します。 次のいずれかを選択します。
    - **[[構成デザイナーを使用する]](#Use-the-configuration-designer)**
    - **[XML データを入力する](#enter-xml-data)**
10. **[OK]** を選択してから、**[追加]** を選択します。

## <a name="use-configuration-designer"></a>構成デザイナーの使用

Intune に登録されているデバイスかどうかにかかわらず、アプリには構成デザイナーを使用できます。 デザイナーでは、特定の構成キーと値を構成できます。 各値のデータ型も指定する必要があります。 設定は、アプリのインストール時に自動で行われます。

### <a name="add-a-setting"></a>設定を追加する

1. 構成の各キーと値について、以下を設定します。
   - **構成キー**<br>
     特定の設定構成を一意に識別するキー。
   - **値の型**<br>
     構成値のデータ型。 整数型、実数型、文字列型、またはブール型があります。
   - **構成値**<br>
     構成の値。
2. **[OK]** を選択して構成の設定を行います。

### <a name="delete-a-setting"></a>設定の削除

1. 設定の横の省略記号 (**[...]**) を選択します。
2. **[削除]** を選択します。

\{\{ 文字と \}\} 文字を使用できるのはトークンの種類のみであり、他の目的には使用しないでください。

## <a name="enter-xml-data"></a>XML データを入力する

Intune に登録されているデバイスのアプリ構成設定を含む XML プロパティ リストを入力または貼り付けることができます。 XML プロパティ リストの形式は、構成するアプリによって異なります。 使用する正確な形式の詳細については、アプリの供給元にお問い合わせください。

Intune では XML 形式が検証されます。 ただし、Intune では XML プロパティ リスト (PList) が対象アプリで動作するかどうかは確認されません。

XML プロパティ リストの詳細情報:

  -  「[Microsoft Intune でのモバイル アプリ構成ポリシーを使用した iOS アプリの構成](/intune-classic/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune)」を参照してください。
  -  iOS Developer Library の「[Understand XML Property Lists](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/UnderstandXMLPlist/UnderstandXMLPlist.html)」 (XML プロパティ リストの概要) を参照してください。

### <a name="example-format-for-an-app-configuration-xml-file"></a>アプリ構成 XML ファイルの形式の例

アプリ構成ファイルを作成する場合、この形式を使用して次の値を 1 つ以上指定できます。

```
<dict>
  <key>userprincipalname</key>
  <string>{{userprincipalname}}</string>
  <key>mail</key>
  <string>{{mail}}</string>
  <key>partialupn</key>
  <string>{{partialupn}}</string>
  <key>accountid</key>
  <string>{{accountid}}</string>
  <key>deviceid</key>
  <string>{{deviceid}}</string>
  <key>userid</key>
  <string>{{userid}}</string>
  <key>username</key>
  <string>{{username}}</string>
  <key>serialnumber</key>
  <string>{{serialnumber}}</string>
  <key>serialnumberlast4digits</key>
  <string>{{serialnumberlast4digits}}</string>
  <key>udidlast4digits</key>
  <string>{{udidlast4digits}}</string>
</dict>
```
### <a name="supported-xml-plist-data-types"></a>サポートされている XML PList データ型

Intune は、プロパティ リストで次のデータ型をサポートします。

- &lt;integer&gt;
- &lt;real&gt;
- &lt;string&gt;
- &lt;array&gt;
- &lt;dict&gt;
- &lt;true /&gt; または &lt;false /&gt;

### <a name="tokens-used-in-the-property-list"></a>プロパティ リストで使用されるトークン

また、Intune は次のトークンの種類をプロパティ リストでサポートしています。
- \{\{userprincipalname\}\} — たとえば、**John@contoso.com**
- \{\{mail\}\} — たとえば、**John@contoso.com**
- \{\{partialupn\}\} — たとえば、**John**
- \{\{accountid\}\} — たとえば、**fc0dc142-71d8-4b12-bbea-bae2a8514c81**
- \{\{deviceid\}\} — たとえば、**b9841cd9-9843-405f-be28-b2265c59ef97**
- \{\{userid\}\} — たとえば、**3ec2c00f-b125-4519-acf0-302ac3761822**
- \{\{username\}\} — たとえば、**John Doe**
- \{\{serialnumber\}\} — たとえば、**F4KN99ZUG5V2** (iOS デバイスの場合)
- \{\{serialnumberlast4digits\}\} — たとえば、**G5V2** (iOS デバイスの場合)

## <a name="next-steps"></a>次のステップ

通常どおり、アプリの[割り当て](apps-deploy.md)と[監視](apps-monitor.md)に進みます。