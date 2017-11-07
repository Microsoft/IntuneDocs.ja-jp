---
title: "ユーザーを追加してアクセス許可を付与する"
description: "オンプレミス ユーザーと Azure AD を同期し、Intune サブスクリプションに対する管理者権限を付与します"
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 10/31/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6e9ec662-465b-4ed4-94c1-cff0fe18f126
ms.reviewer: angrobe
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 4efc8be824acc3db869529d39617f376327b3193
ms.sourcegitcommit: 94d3d86f8ae9f82a9872384bbaae53580036a4ff
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2017
---
# <a name="add-users-and-give-administrative-permission-to-intune"></a>Intune にユーザーを追加して管理権限を付与する

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

このトピックでは、管理者が Intune にユーザーを追加する方法と、Intune サービスで使用できる管理アクセス許可について説明します。

管理者は、ユーザーを直接追加することも、オンプレミスの Active Directory からユーザーを同期することもできます。 追加されたユーザーは、デバイスを登録し、会社のリソースにアクセスできます。 また、*グローバル管理者*や*サービス管理者*など、追加のアクセス許可をユーザーに与えることができます。

## <a name="add-users-to-intune"></a>Intune にユーザーを追加する
[Office 365 ポータル](https://www.office.com/signin) または [Azure Portal](https://portal.azure.com/#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade/overview) を使って、Intune サブスクリプションにユーザーを手動で追加することができます。 管理者はユーザー アカウントを編集し、Intune ライセンスを割り当てることができます。 Office 365 ポータルまたは Intune Azure ポータルでライセンスを割り当てることができます。 Office 365 ポータルの使い方について詳しくは、「[Office 365 にユーザーを個別に、またはまとめて追加する - 管理者向けヘルプ](https://support.office.com/article/Add-users-individually-or-in-bulk-to-Office-365-Admin-Help-1970f7d6-03b5-442f-b385-5880b9c256ec)」をご覧ください。

### <a name="add-intune-users-in-the-office-365-admin-center"></a>Office 365 管理センターで Intune ユーザーを追加する
1. グローバル管理者またはユーザー管理の管理者アカウントで、[Office 365 ポータル](https://www.office.com/signin)にサインインします。
2. Office 365 メニューで、**[管理者]** を選択します。
3. 管理センターで、**[ユーザーの追加]** を選択します。

  ![Office 365 管理のスクリーンショット](media/office-add-user.png)

4. 次のユーザー詳細を指定します。
  - **名**
  - **姓**
  - **表示名**
  - **ユーザー名** - Azure Active Directory に格納されている、サービスへのアクセスに使われるユニバーサル プリンシパル名 (UPN)
  - **場所**
  - **連絡先の情報** (任意)
  - **パスワード** - 自動生成または指定

     ![Office 365 管理のスクリーンショット](media/office-add-user-details.png)

5. Intune ライセンスを割り当てます。 **[製品ライセンス]** を選択し、製品ライセンスを選択します。 Intune を含むライセンスが必要です。
6. **[追加]** を選択して新しいユーザーを作成します。

### <a name="add-intune-users-in-the-azure-portal"></a>Azure Portal で Intune ユーザーを追加する
1. [Azure Portal](https://portal.azure.com) にサインインし、**[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に移動します。 **Intune** の "*リソースを検索する*" こともできます。
2. **[ユーザー]** を選択します。
3. 管理センターで、**[新しいユーザー]** を選びます。
  ![Office 365 管理のスクリーンショット](media/intune-add-user.png)
4. 次のユーザー詳細を指定します。
  - **名前**
  - **ユーザー名** - Azure Active Directory ポータルの新しい名前 ![Office 365 管理のスクリーンショット](media/intune-add-user-info.png) **[OK]** を選択して続行します。
5. 必要に応じて、次のユーザー プロパティを指定できます。
  - **プロファイル** - **役職**や**部署**などの仕事情報
  -  **グループ** - ユーザーに追加するグループを選択します
  - **ディレクトリ ロール** - Intune サービス管理者ロールを含む管理者アクセス許可をユーザーに与えます。

  **[作成]** を選択し、新しいユーザーを Intune に追加します。
6. **[プロファイル]** を選択し、新しいユーザーの **[利用場所]** を選択します。 新しいユーザーに Intune ライセンスを割り当てるには利用場所が必要です。 **[保存]** を選択して続行します。
    ![Office 365 管理のスクリーンショット](media/intune-add-user-loc.png)
7. **[ライセンス]** を選択し、**[割り当て]** を選択してこのユーザーの Intune ライセンスを割り当てます。 デバイスを登録したり、会社のリソースにアクセスしたりするには、Intune ライセンスが必要です。 **[製品]** を選択し、ライセンスの種類を選択し、**[選択]** を選択し、**[割り当て]** を選択します。

## <a name="grant-admin-permissions"></a>管理者アクセス許可を与える

Intune サブスクリプションにユーザーを追加した後で、ごく一部のユーザーに管理者アクセス許可を付与することをお勧めします。  管理者アクセス許可を付与するには、次の手順のようにします。

### <a name="give-admin-permissions-in-office-365"></a>Office 365 の管理者アクセス許可を付与する
1. グローバル管理者アカウントで [Office 365 ポータル](https://www.office.com/signin)にサインインします。
2. Office 365 メニューで、**[管理者]** を選択します。
3. 管理センターで、**[アクティブなユーザー]** を選び、管理者アクセス許可を付与するユーザーを選びます。
4. **[ロール]** 列で **[編集]** を選びます。
  ![Office 365 のロール割り当て画面のスクリーンショット](./media/office-assign-roles-open.png)
5. 利用可能なロールの一覧から付与する管理者アクセス許可を選びます。
![Office 365 ポータルのロール割り当ての画像。](./media/office-assign-roles.png)
6. **[保存]** を選びます。

### <a name="give-admin-permissions-in-the-azure-portal"></a>Azure Portal で管理者アクセス許可を付与する
1. グローバル管理者アカウントで [Azure Portal](https://www.office.com/signin) にサインインします。
2. Azure Portal で **[ユーザー]** を選び、管理者アクセス許可を付与するユーザーを選びます。
3. **[ディレクトリ ロール]** を選び、アクセス許可を選びます。
  ![スクリーンショット](./media/add-intune-directory-role.png)
4. **[保存]** を選びます。

### <a name="types-of-administrators"></a>管理者の種類

ユーザーに 1 つまたは複数の管理者アクセス許可を割り当てます。 これらのアクセス許可で、ユーザーの管理範囲および管理できるタスクを定義します。 さまざまな Microsoft クラウド サービスで共通の管理者アクセス許可が使われており、一部のサービスではサポートされていないアクセス許可もあります。 Azure Portal と Office 365 ポータルの両方で、Intune で使われていない制限付きの管理者ロールの一覧が表示されます。 Intune の管理者アクセス許可には、次のオプションが含まれます。

- **全体管理者** - (Office 365 と Intune) Intune のすべての管理機能にアクセスできます。 既定では、Intune にサインアップしたユーザーがグローバル管理者になります。他の管理者ロールを割り当てることができる管理者は、グローバル管理者だけです。 組織には複数のグローバル管理者を置くことができます。 ベスト プラクティスとしては、ビジネス リスクを軽減するため、社内の少数のユーザーのみがこのロールを持つようにすることをお勧めします。
- **パスワード管理者** - (Office 365 と Intune) パスワードの再設定、サービス リクエストの管理、およびサービスの正常性の監視を行います。 パスワード管理者は、ユーザーのパスワードのリセットに制限されます。
- **サービス管理者** - (Office 365 と Intune) Microsoft へのサポート要求を開き、サービス ダッシュボードとメッセージ センターを表示します。 サポート チケットを開いて読む場合を除き、"表示のみ" の権限です。
- **課金管理者** - (Office 365 と Intune) 購入、サブスクリプションの管理、サポート チケットの管理、サービスの正常性の監視を行います。
- **ユーザー管理者** - (Office 365 と Intune) パスワードの再設定、サービスの正常性の監視、ユーザー アカウントの追加と削除、サービス要求の管理を行います。 ユーザー管理の管理者は、グローバル管理者の削除、他の管理者ロールの作成、または他の管理者のパスワードの再設定を行うことはできません。
- **Intune サービス管理者** - **[ディレクトリ ロール]** オプションで管理者を作成するアクセス許可を除く、すべての Intune グローバル管理者アクセス許可。

Microsoft Intune サブスクリプションの作成に使うアカウントはグローバル管理者です。 ベスト プラクティスとして、グローバル管理者を日常の管理タスクに使用しないでください。 管理者には、Azure Portal にアクセスするための Intune のライセンスは必要ありません。 

Office 365 ポータルにアクセスするには、アカウントに**サインインが許可されている**必要があります。 Azure Portal の **[プロファイル]** で、**[サインインのブロック]** を **[いいえ]** に設定し、アクセスを許可します。 これは、サブスクリプションのライセンスを与えられていることとは別です。 既定では、すべてのユーザー アカウントは、"**許可済み**" の状態です。 管理者権限を持たないユーザーは、Office 365 ポータルを使って、Intune パスワードをリセットすることができます。

## <a name="sync-active-directory-and-add-users-to-intune"></a>Active Directory を同期化して Intune にユーザーを追加する
ディレクトリの同期化によって、オンプレミスの Active Directory から Intune ユーザーを含む Microsoft Azure Active Directory (Azure AD) に、ユーザー アカウントをインポートできます。 オンプレミスの Active Directory サービスが Azure Active Directory ベースの全サービスに反映され、ユーザー ID の管理が大幅に単純化されます。 また、シングル サインオン機能を構成することによってユーザー認証の利便性を高めることもできます。 同じ [Azure AD テナント](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect/)を複数のサービスとリンクすることにより、前に同期したユーザー アカウントをすべてのクラウド ベース サービスで使用できるようになります。

### <a name="how-to-sync-on-premises-users-with-azure-ad"></a>オンプレミスのユーザーを Azure AD と同期する方法
ユーザー アカウントを Azure AD と同期するために必要なツールは、[Azure AD Connect ウィザード](https://www.microsoft.com/download/details.aspx?id=47594)のみです。 Azure AD Connect ウィザードでは、簡単な画面の指示に従って、オンプレミスの ID インフラストラクチャをクラウドに接続できます。  トポロジと要件 (単一ディレクトリまたは複数ディレクトリ、パスワードの同期またはフェデレーション) を選択します。 ウィザードにより、接続を稼働させるために必要なすべてのコンポーネントがデプロイされて構成されます。 接続した機能が稼働するために必要なすべてのコンポーネントが自動的に展開されて構成されます。

> [!TIP]
> Azure AD Connect には、過去に Dirsync や Azure AD Sync としてリリースされた機能がすべて備わっています。[ディレクトリ統合](http://technet.microsoft.com/library/jj573653.aspx)の詳細を確認してください。 ローカル ディレクトリから Azure AD へのユーザー アカウントの同期について詳しくは、「[Active Directory と Azure AD の類似点](http://technet.microsoft.com/library/dn518177.aspx)」をご覧ください。
