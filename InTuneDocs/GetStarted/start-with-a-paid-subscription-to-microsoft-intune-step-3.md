---
title: "Active Directory を同期化して Intune にユーザーを追加する | Microsoft Intune"
description: "オンプレミス ユーザーと Azure AD を同期し、Intune サブスクリプションに対する管理者権限を付与します"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/22/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6e9ec662-465b-4ed4-94c1-cff0fe18f126
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 29b6e5a3d319c741482fcc2b600842e2e42b96e2
ms.openlocfilehash: 33534c685ad3a4ddfd4b605e088132f2b8ff2c36


---


# <a name="sync-active-directory-and-add-users-to-intune"></a>Active Directory を同期化して Intune にユーザーを追加する
ディレクトリの同期化によって、オンプレミスの Active Directory から Microsoft Azure Active Directory (Azure AD) にユーザー アカウントをインポートできます。 オンプレミスの Active Directory サービスが Azure Active Directory ベースの全サービスに反映され、ユーザー ID の管理が大幅に単純化されます。 また、シングル サインオン機能を構成することによってユーザー認証の利便性を高めることもできます。

より利便性を高めるには、同じ [Azure AD テナント](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect/)で複数のサービスを使用します。そうすると、以前に同期したユーザー アカウントを、同じ Azure AD テナントのサブスクリプションを共有するすべてのクラウドベースのサービスで利用できます。

## <a name="synchronize-on-premises-users-with-azure-ad"></a>オンプレミスのユーザーを Azure AD と同期する
ユーザー アカウントを Azure AD と同期するために必要なツールは、[Azure AD Connect ウィザード](https://www.microsoft.com/download/details.aspx?id=47594)のみです。 Azure AD Connect ウィザードでは、簡単な画面の指示に従って、オンプレミスの ID インフラストラクチャをクラウドに接続できます。  目的のトポロジと要件 (単一ディレクトリと複数ディレクトリ、パスワードの同期、フェデレーションなど) を選ぶと、同期サービスや Active Directory フェデレーション サービス (AD FS)、Azure AD PowerShell モジュールなど、 接続した機能が稼働するために必要なすべてのコンポーネントが自動的に展開されて構成されます。

> [!TIP]
> Azure AD Connect には、過去に Dirsync や Azure AD Sync としてリリースされた機能がすべて備わっています。 [ディレクトリ統合](http://technet.microsoft.com/library/jj573653.aspx)の詳細を確認してください。 ローカル ディレクトリから Azure AD にユーザー アカウントを同期する利点の詳細については、「[Active Directory と Azure AD の類似点](http://technet.microsoft.com/library/dn518177.aspx)」をご覧ください。

## <a name="grant-administrator-permissions"></a>管理者権限を付与する

Intune を管理するには、以下を使用します。
- 2 種類の管理者アカウント
- 追加のアクセス許可を持つユーザー アカウント
- 管理項目へのアクセス許可を管理者に付与するための 2 つの Web ベースの管理コンソール/ポータル。

Intune サブスクリプションにユーザーを追加した後で、ごく一部のユーザー アカウントに管理者資格情報を付与することをお勧めします。 管理者資格情報を割り当てるときに使うコンソールは、割り当てる管理者の種類によって異なります。

-   **テナント管理者**: 請求、クラウドの記憶域、Intune を使用できるユーザーの管理など、サブスクリプションを管理するには、**Microsoft Intune アカウント ポータル**を使用して、この種類の管理者を割り当てます。

-   **サービス管理者**: モバイル デバイスまたはコンピューターの管理、ポリシーまたはソフトウェアの展開、レポートの実行など、日常のタスクを管理するには、**Microsoft Intune 管理者コンソール**を使用して、この種類の管理者を割り当てます。

以下のセクションで、これらのアカウントとポータルについて説明します。

## <a name="administrator-accounts-and-user-accounts-with-special-permissions"></a>特別なアクセス許可を持つ管理者アカウントとユーザー アカウント

次に、Intune で使用するアカウントとアクセス許可を示します。

### <a name="tenant-administrator"></a>テナント管理者
|アクセス許可のレベル|説明|
|--------------------------|-------------------------|
|テナント管理者には、管理者の役割が割り当てられます。管理者の役割は、そのユーザーの管理範囲と、管理できるタスクを定義します。<br /><br />さまざまな Microsoft クラウド サービスで共通の管理者ロールが使用されていますが、一部のサービスではサポートされていないロールもあります。<br /><br /> Microsoft Intune では、次の役割を使用します。<br /><br />- 全体管理者<br />- 課金管理者<br />- パスワード管理者<br />- サービス サポート管理者<br />- ユーザー管理の管理者|既定では、Microsoft Intune サブスクリプションの作成に使用するアカウントは、全体管理者の役割を持つテナント管理者です。<br /></br>  テナント管理者として、[!INCLUDE[wit_icp_1](../includes/wit_icp_1_md.md)] を使用して、Intune のサブスクリプションを管理し、[!INCLUDE[wit_icp_2](../includes/wit_icp_2_md.md)] からテナント管理者を割り当てます。<br /><br />全体管理者の役割を持つテナント管理者を使用して [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)]にアクセスし、最初のサービス管理者を割り当てます。 ベスト プラクティスとして、テナント管理者を日常の管理タスクに使用しないでください。 テナント管理者には、[!INCLUDE[wit_icp_2](../includes/wit_icp_2_md.md)] にアクセスする際 Intune のライセンスは必要ありません。<br /><br />テナント管理者は、Microsoft クラウド サービスで共通の概念です。 Intune にサブスクライブするときに使用するサービスは、Microsoft Azure AD のテナントです。 「[Azure AD ディレクトリとは](http://technet.microsoft.com/library/jj573650.aspx)」の Azure AD テナントに関するセクションを参照してください。|


### <a name="service-administrator"></a>サービス管理者
|アクセス許可のレベル|説明|
|--------------------------|-------------------------|
|サービス管理者には、次の権限の 1 つが割り当てられます。<br /><br />**フル アクセス**: 制限なく [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)] のすべての領域にアクセスする権限を付与します。 他のサービス管理者を追加および管理することもできます。<br /><br />**読み取り専用アクセス**: [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)] のすべての領域への読み取りアクセス許可を付与します。 読み取り専用サービス管理者は、データを変更できませんが、レポートを実行することはできます。<br /><br />**ヘルプデスク - グループ ノード**: サービス管理者に、通常はヘルプデスクのシナリオに関連付けられている一連のタスクのみを実行できるアクセス許可を付与します。 このアクセス許可セットの詳細については、「[管理者の役割に応じて Intune コンソール ビューをカスタマイズする](/intune/deploy-use/control-what-admins-can-see-in-the-microsoft-intune-admin-console)」を参照してください。|既定では、Intune はサービス管理者を割り当てません。 代わりに、全体管理者の役割を持つテナント管理者を使用して、サブスクリプション用の最初のサービス管理者を割り当てる必要があります。 </br></br> サービス管理者として、[!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)] を使用して、Intune の日常のタスクを管理します。<br /><br />サービス管理者は、管理コンソール内から割り当てます。 サービス管理者のアカウントで管理コンソールにアクセスするには、Intune のライセンスが必要です。|



### <a name="device-enrollment-managers"></a>デバイス登録マネージャー
|アクセス許可のレベル|説明|
|--------------------------|-------------------------|
|デバイス登録マネージャーは、5 つを超えるデバイスを登録するための追加の権限を持つ標準ユーザー アカウントです。|既定では、各 [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] ユーザーは最大 5 つのデバイスを登録できます。 ただし、ユーザー アカウントにデバイス登録マネージャーのアクセス許可を与えると、そのアカウントを使用して企業所有のデバイスの大規模なグループを登録できます。 これは、一時的にデバイスをユーザーに割り当てる可能性がある場合や、ユーザーとデバイスの関連付けが必要ないキオスク モードで使用する場合に役立ちます。|




>[!div class="step-by-step"]

>[&larr;**ドメイン設定**](.\start-with-a-paid-subscription-to-microsoft-intune-step-2.md)     [**Intune のライセンスを管理する**&rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-4.md)  



<!--HONumber=Nov16_HO4-->


