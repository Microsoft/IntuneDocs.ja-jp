---
title: 管理対象の iOS デバイス用アプリ構成ポリシーを追加する
titleSuffix: Microsoft Intune
description: アプリ構成ポリシーを使用して、実行時に構成データを iOS アプリに提供する方法について説明します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/12/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c9163693-d748-46e0-842a-d9ba113ae5a8
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9273d547d72fd6cf10d2addc5efff2eba8e18205
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/01/2019
ms.locfileid: "59568363"
---
# <a name="add-app-configuration-policies-for-managed-ios-devices"></a>管理対象の iOS デバイス用アプリ構成ポリシーを追加する

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Microsoft Intune のアプリ構成ポリシーを使用して、iOS アプリのカスタム構成を設定できます。 これらの構成設定では、サプライヤーの指示に基づいてアプリをカスタマイズすることができます。 これらの構成設定 (キーと値) は、アプリのサプライヤーから取得する必要があります。 アプリを構成するには、キーと値として、またはキーと値を含む XML として設定を指定します。 また、これらの構成ポリシーはユーザーとデバイスに直接割り当てないでください。 代わりに、構成ポリシーをアプリに関連付け、そのアプリを割り当てます。 構成ポリシー設定は、アプリがポリシーをチェックするとき (通常はアプリの初回実行時) に使用されます。

アプリ構成ポリシーを追加すると、アプリ構成ポリシーの割り当てを設定できます。 ポリシーの割り当てを設定するときに、ポリシーを適用するユーザーのグループを含めたり、除外したりできます。 含めるグループを選ぶとき、含める特定のグループを選ぶか、組み込みグループを選ぶことができます。 組み込みグループには、**すべてのユーザー**、**すべてのデバイス**、**すべてのユーザーとすべてのデバイス**が含まれます。 

>[!NOTE]
>Intune では、便利なように、最適化が組み込まれた **[すべてのユーザー]** グループと **[すべてのデバイス]** グループがコンソールで提供されています。 "すべてのユーザー" または "すべてのデバイス" グループを自分で作るのではなく、これらのグループを使ってすべてのユーザーおよびすべてのデバイスを対象にすることを強くお勧めします。<p></p>
>Microsoft Intune 管理者は、マネージド デバイス上の Microsoft Office アプリケーションにどのユーザー アカウントを追加するかを制御することができます。 許可されている組織ユーザー アカウントのみにアクセスを制限したり、登録済みデバイス上の個人アカウントをブロックしたりできます。 サポートされているアプリケーションがアプリの構成を処理し、未承認のアカウントを削除してブロックします。

アプリケーション構成ポリシーの含まれるグループを選ぶと、除外される特定のグループも選べます。 詳細については、「[Microsoft Intune でのアプリ割り当ての組み込みと除外](apps-inc-exl-assignments.md)」を参照してください。

> [!TIP]
> この種類のポリシーは現在、iOS 8.0 以降を実行しているデバイスでのみ有効です。 次の種類のアプリ インストールをサポートします。
>
> -   **App Store の管理対象 iOS アプリ**
> -   **iOS 用アプリ パッケージ**
>
> アプリのインストールの種類の詳細については、「[How to add an app to Microsoft Intune (Microsoft Intune にアプリを追加する方法)](apps-add.md)」を参照してください。

## <a name="create-an-app-configuration-policy"></a>アプリ構成ポリシーを作成する

1. [Azure ポータル](https://portal.azure.com) にサインインします。
2. **[すべてのサービス]** > **[Intune]** の順に選択します。 Intune は **[監視 + 管理]** セクションにあります。
3. **[クライアント アプリ]** ワークロードを選択します。
4. **[管理]** グループの **[アプリ構成ポリシー]** を選択し、**[追加]** を選択します。
5. 次の詳細を設定します。
    - **名前**: Azure portal に表示されるプロファイルの名前。
    - **説明**: Azure portal に表示されるプロファイルの説明。
    - **デバイス登録の種類** - **[マネージド デバイス]** を選択します。
6. **[プラットフォーム]** で **[iOS]** を選択します。
7.  **[関連アプリ]** を選択します。 次に、**[関連アプリ]** ウィンドウで、構成を適用する管理対象アプリを選択して **[OK]** を選択します。
8.  **[構成ポリシーの追加]** ウィンドウで、**[構成設定]** を選択します。
9. **[構成設定の形式]** を選択します。 XML 情報を追加するには、次のいずれかを選択します。
    - **構成デザイナーを使用する**
    - **XML データを入力する**<br><br>
    構成デザイナーの使用の詳細については、「[構成デザイナーの使用](#use-configuration-designer)」を参照してください。 XML データの入力の詳細については、「[XML データを入力する](#enter-xml-data)」を参照してください。 
10. XML 情報を追加したら、**[OK]** を選び、**[追加]** を選んで構成ポリシーを追加します。 構成ポリシーの概要ウィンドウが表示されます。
11. **[割り当て]** を選んで、含めるオプションと除外するオプションを表示します。 

    ![ポリシーの割り当ての [含める] タブのスクリーンショット](./media/app-config-policy01.png)
12. **[必要]** タブの **[すべてのユーザー]** を選びます。

    ![ポリシーの割り当ての [すべてのユーザー] ドロップダウン オプションのスクリーンショット](./media/app-config-policy02.png)
13. **[必要なし]** タブを選びます。 
14. **[含めないグループを選択]** をクリックして、関連するウィンドウを表示します。

    ![ポリシーの割り当ての [含めないグループを選択] ウィンドウのスクリーンショット](./media/app-config-policy03.png)
15. 除外するグループを選んで、**[選択]** をクリックします。

    >[!NOTE]
    >グループを追加するときに、他のグループが特定の割り当て種類に既に含まれる場合は、あらかじめ選択されており、他の含める割り当て種類には変更できません。 そのため、使われているそのグループは、含まれないグループとして使えません。
16. **[Save]**(保存) をクリックします。

## <a name="use-configuration-designer"></a>構成デザイナーの使用

Microsoft Intune には、アプリに固有の構成設定が用意されています。 Microsoft Intune に登録されているデバイスかどうかにかかわらず、アプリには構成デザイナーを使用できます。 デザイナーでは、基になる XML の作成に役立つ特定の構成キーと値を構成できます。 各値のデータ型も指定する必要があります。 これらの設定は、アプリのインストール時に自動で行われます。

### <a name="add-a-setting"></a>設定を追加する

1. 構成の各キーと値について、以下を設定します。
   - **構成キー**: 特定の設定構成を一意に識別するキー。
   - **値の型:** 構成値のデータ型。 整数型、実数型、文字列型、またはブール型があります。
   - **構成値**: 構成の値。
2. **[OK]** を選択して構成の設定を行います。

### <a name="delete-a-setting"></a>設定の削除

1. 設定の横の省略記号 (**[...]**) を選択します。
2. **[削除]** を選択します。

\{\{ 文字と \}\} 文字を使用できるのはトークンの種類のみであり、他の目的には使用しないでください。

### <a name="allow-only-configured-organization-accounts-in-multi-identity-apps"></a>複数 ID アプリで構成済みの組織アカウントのみを許可する 

iOS デバイスでは、次のキー/値ペアを使用します。

| **Key** | IntuneMAMAllowedAccountsOnly |
|--------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **値** | <ul><li>**有効**: [IntuneMAMUPN](data-transfer-between-apps-manage-ios.md#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm) キーによって定義されたマネージド ユーザー アカウントのみが許可されます。</li><li>**[無効]** (**[有効]** と大文字小文字を問わず一致しないすべての値): すべてのアカウントが許可されます。</li></ul> |。

   > [!NOTE]
   > 複数 ID で構成された組織アカウントのみを許可する場合は、必ず OneDrive for iOS 10.34 以降、および Outlook for iOS 2.99.0 以降を使用すると共に、アプリが [Intune アプリ保護ポリシー](app-protection-policy.md)の対象になっている必要があります。

## <a name="enter-xml-data"></a>XML データを入力する

Intune に登録されているデバイスのアプリ構成設定を含む XML プロパティ リストを入力または貼り付けることができます。 XML プロパティ リストの形式は、構成するアプリによって異なります。 使用する正確な形式の詳細については、アプリの供給元にお問い合わせください。

Intune では XML 形式が検証されます。 ただし、Intune では XML プロパティ リスト (PList) が対象アプリで動作するかどうかは確認されません。

XML プロパティ リストの詳細情報:

  -  iOS Developer Library の「[Understand XML Property Lists](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/UnderstandXMLPlist/UnderstandXMLPlist.html)」 (XML プロパティ リストの概要) を参照してください。

### <a name="example-format-for-an-app-configuration-xml-file"></a>アプリ構成 XML ファイルの形式の例

アプリ構成ファイルを作成する場合、この形式を使用して次の値を 1 つ以上指定できます。

```xml
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
  <key>aaddeviceid</key>
  <string>{{aaddeviceid}}</string>
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
- \{\{aaddeviceid\}\} — たとえば、**ab0dc123-45d6-7e89-aabb-cde0a1234b56**

## <a name="monitor-ios--app-configuration-status-per-device"></a>デバイスごとに iOS アプリ構成の状態を監視する 
構成ポリシーが割り当てられたら、マネージド デバイスごとに iOS アプリ構成の状態を監視することができます。 Azure Portal の **[Microsoft Intune]** から、**[デバイス]** > **[すべてのデバイス]** の順に選びます。 管理対象デバイスの一覧から、デバイスのブレードを表示する特定のデバイスを選びます。 デバイスのブレードで、**[アプリの構成]** を選びます。  

## <a name="next-steps"></a>次の手順

アプリの[割り当て](apps-deploy.md)と[監視](apps-monitor.md)に進みます。
