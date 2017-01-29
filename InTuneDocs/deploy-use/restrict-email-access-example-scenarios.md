---
title: "電子メールの保護に関するシナリオ | Microsoft Docs"
description: "いくつかのシナリオ例と、条件付きアクセスを使用した場合の実装方法。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 01/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 454eab79-b620-42c9-b8e6-fada6e719fcd
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9f05e516723976dcf6862475dbb78f9dce2913be
ms.openlocfilehash: c02961aa984f8041394639a872bf4cfcdfc0be91


---

# <a name="protect-access-to-email-with-microsoft-intune-example-scenarios"></a>Microsoft Intune で電子メールへのアクセスを保護する: シナリオ例

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

## <a name="scenario-1-block-users-from-using-noncompliant-devices-to-access-exchange-online"></a>シナリオ 1: 非準拠のデバイスを使用して Exchange Online にアクセスするユーザーをブロックする
### <a name="scenario-requirements"></a>シナリオの要件
- 展開したコンプライアンス ポリシーにデバイスが準拠していない場合、**[アカウンティング]** Azure Active Directory セキュリティ グループ内のすべてのユーザーの Exchange Online へのアクセスをブロックする必要があります。
- このグループ内に [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] によってデバイスがサポートされていないユーザーが存在する場合、それらのデバイスでのユーザーによる Exchange Online へのアクセスをブロックする必要があります。
- **[ファイナンス]** Azure Active Directory セキュリティ グループに属するユーザーはいずれも、さらに **[アカウンティング]** セキュリティ グループに属していたとしても、ポリシーから除外する必要があります。

これらを実現するためには、次の設定で Exchange Online の条件付きアクセス ポリシーを構成します。

- **[条件付きアクセス ポリシーを有効にする]** をオンにします。

- 先進認証を使用したアプリからのアクセスを許可するプラットフォームを選択します。
- Exchange ActiveSync アプリの場合は、**[Microsoft Intune がサポートするプラットフォームの非準拠デバイスをブロックします]** と **[Microsoft Intune がサポートしていないプラットフォームにあるその他のデバイスをすべてブロックします]** をオンにします。
-   **[対象グループ]** セクションの **[選択されているセキュリティ グループ]** で、**[アカウンティング]** ユーザー グループを選択します。

-   **[例外グループ]** セクションの **[選択されているセキュリティ グループ]** で、**[ファイナンス]** ユーザー グループを選択します。


このシナリオでは、Exchange Online にアクセスできるデバイスを決定するために、次のフローが使われています。

![デバイス アクセス フロー](./media/ConditionalAccess8-5.png)

## <a name="scenario-2-all-ios-devices-that-access-exchange-on-premises-must-be-managed-by-intune"></a>シナリオ 2: Exchange On-premises にアクセスするすべての iOS デバイスを Intune で管理する必要がある
### <a name="scenario-requirements"></a>シナリオの要件
- iOS を実行しているデバイスだけが Exchange On-premises にアクセスできるようにする必要があります。
- デバイスを Exchange へのアクセスに使用するには、それらのデバイスが Intune に登録され、コンプライアンス ポリシーのルールに準拠している必要があります。

これらを実現するためには、次の設定で Exchange On-premises の条件付きアクセス ポリシーを構成します。

-   **[デバイスが Microsoft Intune に準拠していない場合や、登録されていない場合に、電子メール アプリから Exchange On-premises へのアクセスをブロックします]** をオンにします。 このオプションを選択すると、条件付きアクセス ポリシーが有効になり、Exchange にアクセスするすべてのデバイスは、Microsoft Intune に登録され、コンプライアンス ポリシーのルールに準拠していることが必要になります。

-   Exchange Active Sync の詳細設定で、以下を作成します。

  -   iOS を実行するデバイスで Exchange にアクセスできるプラットフォームの例外。   

  -   デバイスがプラットフォームの例外ルールの対象とならない場合は Exchange へのアクセスをブロックするよう指定する既定のルール。 このルールによって、iOS を実行していないデバイスは Exchange へのアクセスがブロックされるようになります。

次のフローを使用して、Exchange にアクセスできるデバイスを決定します。

![デバイス アクセス フロー](./media/ConditionalAccess8-3.png)

## <a name="scenario-3-no-android-devices-can-access-exchange-on-premises"></a>シナリオ 3: Android デバイスは Exchange On-premises にアクセスできない
### <a name="scenario-requirements"></a>シナリオの要件
- すべての Android デバイスに対して Exchange へのアクセスをブロックする必要があります。
- その他すべてのサポートされるデバイスは、[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] で管理されている限り Exchange にアクセスできます。

これらを実現するためには、次の設定で Exchange On-premises の条件付きアクセス ポリシーを構成します。

-   **[デバイスが Microsoft Intune に準拠していない場合や、登録されていない場合に、電子メール アプリから Exchange On-premises へのアクセスをブロックします]** をオンにします。 このオプションを選択すると、すべてのデバイスが Intune に登録され、コンプライアンス ポリシーのルールを満たしていることが必要になります。

- Exchange Active Sync の詳細設定で、以下を作成します。
  -   Android を実行するデバイスが Exchange にアクセスできないようにブロックするプラットフォームの例外。 このルールによって、Android デバイスは Exchange へのアクセスに使用できなくなります。

  -   デバイスが他のルールの対象にならない場合に、Exchange へのアクセスが許可されることを指定する既定のルール。 この既定のルールによって、Android 以外のプラットフォームを実行していて、Microsoft Intune でサポートされているデバイスは、Exchange へのアクセスに使用できるようになります。 ただし、それらのデバイスは Intune に登録され、コンプライアンス ポリシーのルールを満たしている必要があります。

次のフローを使用して、Exchange にアクセスできるデバイスを決定します。

![デバイス アクセス フロー](./media/ConditionalAccess8-4.png)



<!--HONumber=Jan17_HO4-->


