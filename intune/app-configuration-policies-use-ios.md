---
title: "iOS 用 Intune アプリ構成ポリシーを使用する方法"
titleSuffix: Intune on Azure
description: "アプリ構成ポリシーを使用して、実行時に構成データを iOS アプリに提供する方法について説明します。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 07/26/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c9163693-d748-46e0-842a-d9ba113ae5a8
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b261834c85a9dd3cbc6f8fae40933dd7a79acf93
ms.sourcegitcommit: 79116d4c7f11bafc7c444fc9f5af80fa0b21224e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2017
---
# <a name="how-to-use-microsoft-intune-app-configuration-policies-for-ios"></a>iOS 用 Microsoft Intune アプリ構成ポリシーを使用する方法

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Microsoft Intune のアプリ構成ポリシーを使用して、ユーザーが iOS アプリを実行するときに使用される設定を指定できます。 たとえば、アプリは次の内容を指定することをユーザーに要求することがあります。

-   カスタム ポート番号。

-   言語設定。

-   セキュリティ設定。

-   会社のロゴなどのブランドの設定。

ユーザーがこれらの設定を誤って入力すると、ヘルプ デスクの負荷が増加し、新しいアプリの採用が遅くなる可能性もあります。

アプリ構成ポリシーを使用すると、ユーザーがアプリを実行する前にこれらの設定をポリシー内のユーザーに割り当てることができるため、上記の問題を排除するのに役立ちます。 設定が自動的に指定されるため、ユーザーの操作は不要です。 アプリは、アプリ構成の使用をサポートするように作成されている必要があります。 詳細については、アプリのベンダーに問い合わせてください。

これらのポリシーをユーザーとデバイスに直接割り当てないでください。 代わりに、ポリシーをアプリに関連付け、そのアプリを割り当てます。 ポリシー設定は、アプリがポリシーを確認する際に (通常は初めて実行したときに) 必ず使用されます。

> [!TIP]
> この種類のポリシーは現在、iOS 8.0 以降を実行しているデバイスでのみ有効です。 次の種類のアプリ インストールをサポートします。
>
> -   **App Store の管理対象 iOS アプリ**
> -   **iOS 用アプリ パッケージ**
>
> アプリのインストールの種類の詳細については、「[How to add an app to Microsoft Intune (Microsoft Intune にアプリを追加する方法)](apps-add.md)」を参照してください。

## <a name="create-an-app-configuration-policy"></a>アプリ構成ポリシーを作成する
1.  Azure ポータルにサインインします。
2.  **[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
3.  **[Intune]** ブレードで、**[モバイル アプリ]** を選択します。
4.  **[モバイル アプリ]** ワークロードで、**[管理]** > **[アプリの構成ポリシー]** の順に選びます。
5.  ポリシーの一覧ブレードで、**[追加]** を選択します。
6.  **[構成ポリシーの追加]** ブレードで、アプリ構成ポリシーの **[名前]** と **[説明]** (省略可能) を入力します。
7.  **[デバイス登録の種類]** には、次のいずれかを選択します。
    - **[Intune に登録済み]** - Intune によって管理されるアプリの場合。
    - **[Intune に未登録]** - Intune によって管理されないアプリ、または別のソリューションによって管理されるアプリの場合。
8.  **[プラットフォーム]** には、**[iOS]** を選択します (Intune に登録されているデバイスのみ)
9.  **[関連アプリ]** を選択し、**[関連アプリ]** ブレードで、構成を適用する管理対象アプリを選択します。
10. **[構成ポリシーの追加]** ブレードで、**[構成設定]** を選択します
11. **[構成設定]** ブレードで、構成プロファイルを構成する XML 値を指定する方法を選択します。
    - **[XML データを入力する]** (Intune に登録されているデバイスのみ) - 必要なアプリ構成設定を含む XML プロパティの一覧を入力するか貼り付けます。 XML プロパティ リストの形式は、構成するアプリによって異なります。 使用する形式の詳細については、アプリの供給元にお問い合わせください。
Intune によって、入力した XML が有効な形式であるかどうかがチェックされます。 XML プロパティ リストが関連付けられているアプリで動作するかどうかはチェックされません。
XML プロパティ リストの詳細については、iOS 開発者ライブラリの [XML プロパティ リスト](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/UnderstandXMLPlist/UnderstandXMLPlist.html)に関するページを参照してください。
    - **[構成デザイナーを使用する]** (デバイスが Intune に登録されているどうかを問わない) - XML キーと値のペアをポータルで直接指定できます。
11. 完了したら、**[構成ポリシーの追加]** ブレードに戻り、**[作成]** をクリックします。

ポリシーが作成され、ポリシーの一覧ブレードに表示されます。



>[!Note]
>[Intune App SDK](https://docs.microsoft.com/intune/app-sdk-ios) を使用して、デバイスが Intune に登録されているかを問わず、Intune アプリ保護ポリシーおよびアプリ構成ポリシーで管理される基幹業務アプリを準備することができます。 たとえば、アプリ構成ポリシーを使用して [Intune Managed Browser](app-configuration-managed-browser.md) で許可される URL とブロックされる URL を構成することができます。 このような URL はアプリとポリシーが互換した時点で、ポリシーを使用して構成できるようになります。


割り当てたアプリをデバイスで実行すると、アプリ構成ポリシーで構成した設定を使用して実行されます。
1 つまたは複数のアプリ構成ポリシーが競合する場合に発生する事象については、構成しているアプリのドキュメントを参照してください。

>[!Tip]
>これらのタスクは Graph API でも実行することができます。 詳細については、[Graph API のリファレンスの MAM を対象とした構成](https://graph.microsoft.io/docs/api-reference/beta/api/intune_mam_targetedmanagedappconfiguration_create)に関するページを参照してください。


## <a name="information-about-the-xml-file-format"></a>XML ファイル形式に関する情報

Intune は、プロパティ リストで次のデータ型をサポートします。

- &lt;integer&gt;
- &lt;real&gt;
- &lt;string&gt;
- &lt;array&gt;
- &lt;dict&gt;
- &lt;true /&gt; または &lt;false /&gt;

データ型の詳細については、iOS 開発者ライブラリの [プロパティ リスト](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/AboutPropertyLists/AboutPropertyLists.html) に関するページを参照してください。

また、Intune は次のトークンの種類をプロパティ リストでサポートしています。
- \{\{userprincipalname\}\} - (例: **John@contoso.com**)
- \{\{mail\}\} - (例: **John@contoso.com**)
- \{\{partialupn\}\} - (例: **John**)
- \{\{accountid\}\} - (例: **fc0dc142-71d8-4b12-bbea-bae2a8514c81**)
- \{\{deviceid\}\} - (例: **b9841cd9-9843-405f-be28-b2265c59ef97**)
- \{\{userid\}\} - (例: **3ec2c00f-b125-4519-acf0-302ac3761822**)
- \{\{username\}\} - (例: **John Doe**)
- \{\{serialnumber\}\} - (例: **F4KN99ZUG5V2**) iOS デバイスの場合
- \{\{serialnumberlast4digits\}\} - (例: **G5V2**) iOS デバイスの場合

\{\{ 文字と \}\} 文字を使用できるのはトークンの種類のみであり、他の目的には使用しないでください。

## <a name="example-format-for-an-app-configuration-xml-file"></a>アプリ構成 XML ファイルの形式の例

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

## <a name="next-steps"></a>次のステップ

通常どおり、アプリの[割り当て](apps-deploy.md)と[監視](apps-monitor.md)に進みます。