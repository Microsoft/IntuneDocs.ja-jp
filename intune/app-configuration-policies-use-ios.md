---
title: "iOS 用 Intune アプリ構成ポリシーを使用する方法"
titleSuffix: Intune on Azure
description: "アプリ構成ポリシーを使用して、実行時に構成データを iOS アプリに提供する方法について説明します。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 06/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c9163693-d748-46e0-842a-d9ba113ae5a8
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 77277069a8c436c09be3940493a2c3e7b5dd8dc4
ms.openlocfilehash: 260c859ae95efb4a38feb0b0ddcd28b92e228f04
ms.contentlocale: ja-jp
ms.lasthandoff: 06/19/2017

---

# <a name="how-to-use-microsoft-intune-app-configuration-policies-for-ios"></a>iOS 用 Microsoft Intune アプリ構成ポリシーを使用する方法

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Microsoft Intune のアプリ構成ポリシーを使用して、ユーザーが iOS アプリを実行するときに必要となる可能性がある設定を指定できます。 たとえば、アプリは次の内容を指定することをユーザーに要求することがあります。

-   カスタム ポート番号。

-   言語設定。

-   セキュリティ設定。

-   会社のロゴなどのブランドの設定。

ユーザーがこれらの設定を誤って入力すると、ヘルプ デスクの負荷が増加し、新しいアプリの採用が遅くなる可能性もあります。

アプリ構成ポリシーを使用すると、ユーザーがアプリを実行する前にこれらの設定をポリシー内のユーザーに割り当てることができるため、上記の問題を排除するのに役立ちます。 設定が自動的に指定されるため、ユーザーの操作は不要です。

これらのポリシーをユーザーとデバイスに直接割り当てないでください。 代わりに、ポリシーをアプリに関連付け、そのアプリを割り当てます。 ポリシー設定は、アプリがポリシーを確認する際に (通常は初めて実行したときに) 必ず使用されます。

> [!TIP]
> この種類のポリシーは現在、iOS 8.0 以降を実行しているデバイスでのみ有効です。 次の種類のアプリ インストールをサポートします。
>
> -   **App Store の管理対象 iOS アプリ**
> -   **iOS 用アプリ パッケージ**
>
> アプリのインストールの種類の詳細については、「[How to add an app to Microsoft Intune (Microsoft Intune にアプリを追加する方法)](apps-add.md)」を参照してください。

## <a name="create-an-app-configuration-policy"></a>アプリ構成ポリシーを作成する

1. Azure ポータルにサインインします。
2. **[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
3. **[Intune]** ブレードで、**[モバイル アプリ]** を選択します。
1.  **[モバイル アプリ]** ワークロードで、**[管理]** > **[アプリの構成ポリシー]** の順に選びます。

2.  ポリシーの一覧ブレードで、**[追加]** を選択します。

3.  **[構成ポリシーの追加]** ブレードで、アプリ構成ポリシーの名前と説明 (省略可能) を入力します。
4.  **[関連アプリ]** を選択し、**[関連アプリ]** ブレードで、構成を適用する管理対象アプリを選択します。
5.  **[構成ポリシーの追加]** ブレードで **[構成設定]** を選択し、[構成設定] ブレードから、構成プロファイルを構成する XML 値を指定する方法を選択します。
    - **[XML データを入力する]** - 必要なアプリ構成設定を含む XML プロパティの一覧を入力するか貼り付けます。 XML プロパティ リストの形式は、構成するアプリによって異なります。 使用する形式の詳細については、アプリの供給元にお問い合わせください。
    Intune によって、入力した XML が有効な形式であるかどうかがチェックされます。 XML プロパティ リストが関連付けられているアプリで動作するかどうかはチェックされません。
    XML プロパティ リストの詳細については、iOS 開発者ライブラリの [XML プロパティ リスト](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/UnderstandXMLPlist/UnderstandXMLPlist.html)に関するページを参照してください。
    - **[構成デザイナーを使用する]** - XML キーと値のペアをポータルで直接指定できます。
8. 完了したら、**[構成ポリシーの追加]** ブレードに戻り、**[作成]** をクリックします。

ポリシーが作成され、ポリシーの一覧ブレードが表示されます。

その後、通常どおり、アプリの[割り当て](apps-deploy.md)と[監視](apps-monitor.md)に進みます。

割り当てたアプリをデバイスで実行すると、アプリ構成ポリシーで構成した設定を使用して実行されます。

> [!TIP]
> 1 つ以上のアプリ構成ポリシーが競合する場合は、どちらのポリシーも適用されません。

## <a name="create-a-mam-targeted-configuration-policy"></a>MAM 対象の構成ポリシーを作成する
MAM 対象の構成では、ユーザーによって定義された設定を通常の MAM-WE 操作に統合することができます。 たとえば、これらの設定はユーザーのコンソールで定義されている場合があります。 MAM 対象の構成データは、MAM サービスを通じて MAM-WE 対応のアプリケーションに提供されます。 アプリケーション構成データは、MDM チャネルではなく MAM サービスを通して直接アプリにプッシュされます。 MDM アプリ構成ポリシー (前述の説明) は、MDM を使用したネイティブ ソリューションです。 MAM 対象の構成との主な違いは、アプリを実行するデバイスを MDM に登録する必要がない点です。 MAM 対象の構成は、iOS と Android で使用できます。 iOS の場合は、アプリに iOS 向け Intune App SDK (バージョン 7.0.1) が組み込まれている必要があります。 MAM 対象の構成ポリシーを作成する手順は、次の通りです。 
1. サインイン、 **Azure ポータル**します。

2. **[Intune] > [モバイル アプリ - アプリ構成ポリシー]** の順に選択します。

3. **[アプリ構成ポリシー]** ブレードで、**[追加]** を選択します。

4. **[名前]**、および必要に応じてアプリ構成設定の **[説明]** を入力し、**[Intune に未登録]** を選択します。

5. **[必要なアプリの選択]** を選択し、**[対象]** アプリ ブレードで、プラットフォームのアプリを選択します。 <br> 
**注:** LOB アプリの場合は、**[その他のアプリ]** を選択してください。 アプリケーションのパッケージ ID を入力します。

6. **[OK]** を選択し、**[アプリの構成を追加する]** ブレードに戻ります。

7. **[構成の定義]** を選択します。 **[構成]** ブレードで、構成を指定するキーと値のペアを定義します。

8. 終了したら、**[OK]** を選択します。

9. **[アプリの構成を追加する]** ブレードで、**[作成]** を選択します。

新しい構成が作成され、[アプリの構成] ブレードに表示されます。 

その後、通常どおり、アプリの[割り当て](apps-deploy.md)と[監視](apps-monitor.md)に進みます。

割り当てられたアプリ (Intune App SDK に統合) をデバイスで実行すると、MAM 対象の構成ポリシーで構成した設定を使用して実行されます。 割り当てられたアプリは、Intune App SDK のサポート対象バージョンに統合されている必要があります。 MAM 対象の構成ポリシーを使用するためのアプリ開発要件について詳しくは、[iOS と Intune App SDK の統合ガイド](https://docs.microsoft.com/en-us/intune/app-sdk-ios)に関するページを参照してください。

MAM 対象の構成値に関する Graph API の機能について詳しくは、[Graph API リファレンスの MAM 対象の構成](https://graph.microsoft.io/en-us/docs/api-reference/beta/api/intune_mam_targetedmanagedappconfiguration_create)に関するページをご覧ください。

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

