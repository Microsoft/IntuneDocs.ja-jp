---
title: "管理者アカウント、Web サイト、アクセス許可 | Microsoft Intune"
description: "管理アカウント、アクセス許可、Web サイト"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: db3075e7-38fd-4dfe-b266-26aed10ac8ea
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9d44a6494bed0758b9768045bd204ea0eb481636
ms.openlocfilehash: e5282defb4560fee028e16d6526037c848678d1a


---

# <a name="administrative-accounts-websites-and-permissions-in-microsoft-intune"></a>Microsoft Intune の管理者アカウント、Web サイト、アクセス許可

Microsoft Intune をセットアップする前に、このトピックと「[What to know before you start Microsoft Intune](what-to-know-before-you-start-microsoft-intune.md)」 (Microsoft Intune を開始する前に理解しておくこと) に挙げられているその他の要件を確認してください。

Intune を管理するには、以下を使用します。
- 2 種類の管理者アカウント
- 追加のアクセス許可を持つユーザー アカウント
- 管理項目へのアクセス許可を管理者に付与するための 2 つの Web ベースの管理コンソール/ポータル。

以下のセクションで、これらのアカウントとポータルについて説明します。

## <a name="administrator-accounts-and-user-accounts-with-special-permissions"></a>特別なアクセス許可を持つ管理者アカウントとユーザー アカウント

次に、Intune で使用するアカウントとアクセス許可を示します。

### <a name="tenant-administrator"></a>テナント管理者
|アクセス許可のレベル|説明|
|--------------------------|-------------------------|
|テナント管理者には、管理者の役割が割り当てられます。管理者の役割は、そのユーザーの管理範囲と、管理できるタスクを定義します。<br /><br />さまざまな Microsoft クラウド サービスで共通の管理者ロールが使用されていますが、一部のサービスではサポートされていないロールもあります。<br /><br /> Microsoft Intune では、次の役割を使用します。<br /><br />- 全体管理者<br />- 課金管理者<br />- パスワード管理者<br />- サービス サポート管理者<br />- ユーザー管理の管理者|既定では、Microsoft Intune サブスクリプションの作成に使用するアカウントは、全体管理者の役割を持つテナント管理者です。<br /></br>  テナント管理者として、[!INCLUDE[wit_icp_1](../includes/wit_icp_1_md.md)] を使用して、[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] のサブスクリプションを管理し、[!INCLUDE[wit_icp_2](../includes/wit_icp_2_md.md)] からテナント管理者を割り当てます。<br /><br />全体管理者の役割を持つテナント管理者を使用して [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)]にアクセスし、最初のサービス管理者を割り当てます。 ベスト プラクティスとして、テナント管理者を日常の管理タスクに使用しないでください。 テナント管理者には、[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] にアクセスする際 [!INCLUDE[wit_icp_2](../includes/wit_icp_2_md.md)] のライセンスは必要ありません。<br /><br />テナント管理者は、Microsoft クラウド サービスで共通の概念です。 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] にサブスクライブするときに使用するサービスは、Microsoft Azure AD のテナントです。 「[Azure AD ディレクトリとは](http://technet.microsoft.com/library/jj573650.aspx)」の Azure AD テナントに関するセクションを参照してください。|


### <a name="service-administrator"></a>サービス管理者
|アクセス許可のレベル|説明|
|--------------------------|-------------------------|
|サービス管理者には、次の権限の 1 つが割り当てられます。<br /><br />**フル アクセス**: 制限なく [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)] のすべての領域にアクセスする権限を付与します。 他のサービス管理者を追加および管理することもできます。<br /><br />**読み取り専用アクセス**: [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)] のすべての領域への読み取りアクセス許可を付与します。 読み取り専用サービス管理者は、データを変更できませんが、レポートを実行することはできます。<br /><br />**ヘルプデスク - グループ ノード**: サービス管理者に、通常はヘルプデスクのシナリオに関連付けられている一連のタスクのみを実行できるアクセス許可を付与します。 このアクセス許可セットの詳細については、「[管理者の役割に応じて Intune コンソール ビューをカスタマイズする](/intune/deploy-use/control-what-admins-can-see-in-the-microsoft-intune-admin-console)」を参照してください。|既定では、[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] はサービス管理者を割り当てません。 代わりに、全体管理者の役割を持つテナント管理者を使用して、サブスクリプション用の最初のサービス管理者を割り当てる必要があります。 </br></br> サービス管理者として、[!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)] を使用して、[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] の日常のタスクを管理します。<br /><br />サービス管理者は、管理コンソール内から割り当てます。 サービス管理者のアカウントが管理コンソールにアクセスするには、[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] のライセンスが必要です。|



### <a name="device-enrollment-managers"></a>デバイス登録マネージャー
|アクセス許可のレベル|詳細情報|
|--------------------------|-------------------------|
|デバイス登録マネージャーは、15 台を超えるデバイスを登録するための追加の権限を持つ標準ユーザー アカウントです。|既定では、各 [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] ユーザーは最大 15 台のデバイスを登録できます。 ただし、ユーザー アカウントにデバイス登録マネージャーのアクセス許可を与えると、そのアカウントを使用して企業所有のデバイスの大規模なグループを登録できます。 これは、一時的にデバイスをユーザーに割り当てる可能性がある場合や、ユーザーとデバイスの関連付けが必要ないキオスク モードで使用する場合に役立ちます。|


## <a name="administrative-websites-for-intune"></a>Intune の管理 Web サイト
 さまざまな管理タスクを行うには、次の管理 Web サイトを使用する必要があります。これらのサイトには、[サポートされている Web ブラウザー](supported-web-browsers.md)からアクセスできます。

- [Office 365 ポータル](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Microsoft Intune 管理コンソール](https://admin.manage.microsoft.com/)

### <a name="office-365-portalhttpgomicrosoftcomfwlinkplinkid698854"></a>[Office 365 ポータル](http://go.microsoft.com/fwlink/p/?LinkId=698854)

**テナント管理者として、このポータルを使用してサブスクリプションを管理します**。また、管理者の役割で許可されている場合、次のタスクを管理できます。

- サブスクリプションのユーザー アカウントを管理し、社内 Active Directory のディレクトリとの同期を構成する。
- セキュリティ グループと呼ばれる、ユーザーのグループを管理する。
- ユーザーに [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] を使用するためのライセンスを割り当てる。
- サブスクリプションで使用するドメイン名を構成する。 ドメイン名は、ユーザーがサインインに使用するアカウントを定義します。
- 保有するライセンス数や、使用できるクラウドの記憶域の量など、サブスクリプションの請求と購入の詳細を管理する。
- [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] サービスのヘルスを表示するリンクを探す。
- アカウントに [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] を使用するライセンスが割り当てられていない場合でも、テナント管理者として、Office 365 ポータルにサインインしてサブスクリプションを管理できます。
- Intune のライセンスを持つ、管理者以外のユーザーは、このポータルを使用して、自分のパスワードをリセットしたり、プロファイルを編集したりできます。
- Office 365 ポータルにアクセスするには、アカウントのサインイン状態が "**許可済み**" になっている必要があります。 これは、サブスクリプションのライセンスを与えられていることとは別です。 既定では、すべてのユーザー アカウントは、"**許可済み**" の状態です。


### <a name="microsoft-intune-administrator-consolehttpsadminmanagemicrosoftcom"></a>[Microsoft Intune 管理コンソール](https://admin.manage.microsoft.com/)

**サービス管理者として、このポータルを使用して、次のような日常のタスクを管理します**。

- コンピューターとモバイル デバイスのポリシーを設定する。
- ソフトウェアの更新プログラムやアプリなどのソフトウェアを、アップロードして展開する。
- コンピューターの [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] Endpoint Protection を管理する。
- デバイスの状態を表示し、レポートを実行する。
- このポータルにサインインする。 このポータルにサインインするには、サービス管理者のアクセス許可があるか、または全体管理者の役割を持つテナント管理者である必要があります。


このポータルには、サービス管理者のアクセス許可を持つユーザーまたは全体管理者の役割を持つテナント管理者のみがサインインできます。 管理コンソールにアクセスするには、アカウントに [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] を使用するライセンスがあり、サインイン状態が "**許可済み**" になっている必要があります。

[サブスクリプションのユーザーの追加](start-with-a-paid-subscription-to-microsoft-intune-step-3.md)や[サブスクリプションのライセンスの割り当て](start-with-a-paid-subscription-to-microsoft-intune-step-4.md)について、詳細をご確認ください。

 ### <a name="see-also"></a>関連項目
 [Microsoft Intune を使い始める前に](what-to-know-before-you-start-microsoft-intune.md)



<!--HONumber=Nov16_HO2-->


