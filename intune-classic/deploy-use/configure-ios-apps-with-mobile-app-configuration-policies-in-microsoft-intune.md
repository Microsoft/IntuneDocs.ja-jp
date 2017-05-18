---
title: "iOS モバイル アプリ構成ポリシーを使用する | Microsoft Docs"
description: "Intune のモバイル アプリ構成ポリシーを使用して、ユーザーが iOS アプリを実行するときに必要となる可能性がある設定を指定できます。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fc6b645a-e837-4b2a-a10f-144065cbd8dd
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: e7d1760a10e63233fe7cc7f6fd57a68c5283647c
ms.openlocfilehash: dfc76481a673dff5dd8be40659cc267a792760ec


---

# <a name="configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune"></a>Microsoft Intune でのモバイル アプリ構成ポリシーを使用した iOS アプリの構成

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune のモバイル アプリ構成ポリシーを使用して、ユーザーがアプリを実行するときに必要となる可能性がある設定を指定できます。 たとえば、アプリは次の内容を指定することをユーザーに要求することがあります。

-   カスタム ポート番号。

-   言語設定。

-   セキュリティ設定。

-   会社のロゴなどのブランドの設定。

ユーザーがこれらの設定を誤って入力すると、ヘルプ デスクの負荷が増加し、新しいアプリの採用が遅くなる可能性もあります。

モバイル アプリ構成ポリシーを使用すると、アプリを実行する前にこれらの設定をポリシー内のユーザーに展開することで、これらの問題を排除できます。 設定が自動的に指定されるため、ユーザーの操作は不要です。

これらのポリシーをユーザーやデバイスに直接展開しないでください。 代わりに、ポリシーをアプリに関連付け、そのアプリを展開します。 ポリシー設定は、アプリがポリシーを確認する際に (通常は初めて実行したときに) 必ず使用されます。

> [!TIP]
> この種類のポリシーは現在、iOS 8.0 以降を実行しているデバイスでのみ有効です。 次の種類のアプリ インストールをサポートします。
>
> -   **App Store の管理対象 iOS アプリ**
> -   **iOS 用アプリ パッケージ**
>
> アプリのインストールの種類の詳細については、「[Deploy apps with Microsoft Intune](deploy-apps.md)」(Microsoft Intune でアプリを展開する) を参照してください。

## <a name="configure-a-mobile-app-configuration-policy"></a>モバイル アプリ構成ポリシーを構成する

1.  [Microsoft Intune 管理コンソール](https://manage.microsoft.com)で、**[ポリシー]** &gt; **[概要]** &gt; **[ポリシーの追加]** の順に選択します。

2.  ポリシーの一覧で、**[iOS]**を展開し、**[モバイル アプリの構成]**、**[ポリシーの作成]** の順に選択します。

    > [!TIP]
    > この種類のポリシーではカスタム設定のみを構成できます。 推奨設定はありません。

3.  **[ポリシーの作成]** ページの **[全般]** セクションで、名前とモバイル アプリ構成ポリシーのオプションの説明を指定します。

4.  このページの **[モバイル アプリ構成ポリシー]** セクションで、必要なアプリの構成設定を含む XML プロパティ リストをボックスに入力するか貼り付けます。 XML プロパティ リストの形式は、構成するアプリによって異なります。 使用する形式の詳細については、アプリの供給元にお問い合わせください。

    > [!TIP]
    > XML プロパティ リストの詳細については、iOS 開発者ライブラリの [XML プロパティ リスト](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/UnderstandXMLPlist/UnderstandXMLPlist.html)に関するページを参照してください。

5.  **[検証]** をクリックして、入力した XML が有効なプロパティ リスト形式であることを確認します。

    > [!IMPORTANT]
    > **[検証]** をクリックすると、Intune によって、入力した XML が有効な形式であるかどうかがチェックされます。 XML プロパティ リストが関連付けられているアプリで動作するかどうかはチェックされません。

6.  終了したら、 **[ポリシーの保存]**をクリックします。

新しいポリシーは、 **[構成ポリシー]** ノードに表示されます。

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

## <a name="associate-a-mobile-app-configuration-policy-with-an-app"></a>モバイル アプリ構成ポリシーをアプリに関連付ける
モバイル アプリ構成ポリシーを作成したら、この構成ポリシーの設定を適用する iOS アプリに関連付ける必要があります。

これを行うには、「[Microsoft Intune でモバイル デバイスにアプリを展開する](add-apps-for-mobile-devices-in-microsoft-intune.md)」と「[Microsoft Intune を使用してアプリを展開する](deploy-apps-in-microsoft-intune.md)」で説明されているアプリの展開を作成する手順に従います。 ウィザードの **[モバイル アプリの構成]** ページに達したら、**[アプリ構成ポリシー]** ドロップダウン リストからアプリに関連付けるポリシーを選択します。

その後、引き続き展開し、通常どおりアプリの展開をモニタリングしてください。

展開したアプリをデバイスで実行すると、モバイル アプリ構成ポリシーで構成した設定を使用して実行されます。

> [!TIP]
> 1 つまたは複数のモバイル アプリ構成ポリシーが競合する場合は、どちらのポリシーも適用されません。 競合は Intune 管理コンソールの**ダッシュボード**に報告されます。

## <a name="example-format-for-a-mobile-app-configuration-xml-file"></a>モバイル アプリ構成 XML ファイルの形式の例

モバイル アプリ構成ファイルを作成する場合、この形式を使用して次の値を 1 つ以上指定できます。

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



<!--HONumber=Dec16_HO5-->


