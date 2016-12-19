---
title: "ユーザーを追加して権限を付与する | Microsoft Intune"
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
ms.reviewer: angrobe
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: 18d31a306549bae6dd44ab78d1dd08649ee71158


---

# <a name="add-users-and-give-administrative-permission-to-intune"></a>Intune にユーザーを追加して管理権限を付与する

管理者は、ユーザーを直接追加することも、オンプレミスの Active Directory からユーザーを同期することもできます。 追加されたユーザーは、デバイスを登録し、会社のリソースにアクセスできます。 また、*テナント管理者*、*サービス管理者*、*デバイス登録マネージャー*などの追加権限を、ユーザーに付与することもできます。

このトピックの内容は次のとおりです。

- [Intune にユーザーを追加する](#add-users-to-intune)
- 次のような [Intune の追加権限を付与する](#grant-intune-permissions)
  - [テナント管理者](#tenant-administrator)
  - [サービス管理者](#service-administrator)
  - [デバイス登録マネージャー](#device-enrollment-managers)

## <a name="add-users-to-intune"></a>Intune にユーザーを追加する
[Office 365 ポータル](http://go.microsoft.com/fwlink/p/?LinkId=698854)から Intune サブスクリプションにユーザーを手動で追加することができます。ユーザーに Intune ライセンスが自動的に割り当てられることはありません。 代わりに、後で Intune テナント管理者が Office 365 ポータルでユーザー アカウントを編集して、ユーザーにライセンスを割り当てる必要があります。 ガイダンスについては、「[Office 365 にユーザーを個別に、またはまとめて追加する - 管理者向けヘルプ](https://support.office.com/article/Add-users-individually-or-in-bulk-to-Office-365-Admin-Help-1970f7d6-03b5-442f-b385-5880b9c256ec)」をご覧ください。

### <a name="sync-active-directory-and-add-users-to-intune"></a>Active Directory を同期化して Intune にユーザーを追加する
ディレクトリの同期化によって、オンプレミスの Active Directory から Intune ユーザーを含む Microsoft Azure Active Directory (Azure AD) に、ユーザー アカウントをインポートできます。 オンプレミスの Active Directory サービスが Azure Active Directory ベースの全サービスに反映され、ユーザー ID の管理が大幅に単純化されます。 また、シングル サインオン機能を構成することによってユーザー認証の利便性を高めることもできます。 同じ [Azure AD テナント](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect/)を複数のサービスとリンクすることにより、前に同期したユーザー アカウントをすべてのクラウド ベース サービスで使用できるようになります。

### <a name="how-to-sync-on-premises-users-with-azure-ad"></a>オンプレミスのユーザーを Azure AD と同期する方法
ユーザー アカウントを Azure AD と同期するために必要なツールは、[Azure AD Connect ウィザード](https://www.microsoft.com/download/details.aspx?id=47594)のみです。 Azure AD Connect ウィザードでは、簡単な画面の指示に従って、オンプレミスの ID インフラストラクチャをクラウドに接続できます。  目的のトポロジと要件 (単一ディレクトリと複数ディレクトリ、パスワードの同期、フェデレーションなど) を選ぶと、同期サービスや Active Directory フェデレーション サービス (AD FS)、Azure AD PowerShell モジュールなど、 接続した機能が稼働するために必要なすべてのコンポーネントが自動的に展開されて構成されます。

> [!TIP]
> Azure AD Connect には、過去に Dirsync や Azure AD Sync としてリリースされた機能がすべて備わっています。 [ディレクトリ統合](http://technet.microsoft.com/library/jj573653.aspx)の詳細を確認してください。 ローカル ディレクトリから Azure AD にユーザー アカウントを同期する利点の詳細については、「[Active Directory と Azure AD の類似点](http://technet.microsoft.com/library/dn518177.aspx)」をご覧ください。

## <a name="grant-intune-permissions"></a>Intune の権限を付与する

Intune サブスクリプションにユーザーを追加した後で、ごく一部のユーザー アカウントに管理者権限を付与することをお勧めします。 Intune を管理するには、3 種類の Intune 権限をユーザーに付与できます。
-   **テナント管理者**: 請求、クラウドの記憶域、Intune を使用できるユーザーの管理など、サブスクリプションを管理するには、Office 365 ポータルを使用して、この種類の管理者を割り当てます。
-   **サービス管理者**: デバイスとコンピューターの管理、ポリシーとアプリの展開、レポートの実行など、日常のタスクを管理するには、Microsoft Intune 管理者コンソールを使用して、この種類の管理者を割り当てます。
-   **デバイス登録マネージャー**: デバイスとコンピューターの管理、ポリシーとアプリの展開、レポートの実行など、日常のタスクを管理するには、Microsoft Intune 管理者コンソールを使用して、この種類の管理者を割り当てます。


### <a name="tenant-administrator"></a>テナント管理者


テナント管理者には、管理者の役割が割り当てられます。管理者の役割は、そのユーザーの管理範囲と、管理できるタスクを定義します。 さまざまな Microsoft クラウド サービスで共通の管理者ロールが使用されていますが、一部のサービスではサポートされていないロールもあります。 Intune では、以下のロールを使用します。
- **グローバル管理者** - Intune のすべての管理機能にアクセスできます。 既定では、Intune にサインアップしたユーザーがグローバル管理者になります。 他の管理者ロールを割り当てることができる管理者は、グローバル管理者だけです。 組織には複数のグローバル管理者を置くことができます。 ベスト プラクティスとしては、ビジネス リスクを軽減するため、社内の少数のユーザーのみがこのロールを持つようにすることをお勧めします。
- **課金管理者** - 購入、サブスクリプションの管理、サポート チケットの管理、サービスの正常性の監視を行います。
- **パスワード管理者** - パスワードの再設定、サービス リクエストの管理、およびサービスの正常性の監視を行います。 パスワード管理者は、ユーザーのパスワードのリセットに制限されます。
- **サービス サポート管理者** - Microsoft へのサポート要求を開き、サービス ダッシュボードとメッセージ センターを表示します。 サポート チケットを開いて読む場合を除き、"表示のみ" の権限です。
- **ユーザー管理の管理者** - パスワードの再設定、サービスの正常性の監視、ユーザー アカウントの追加と削除、サービス リクエストの管理を行います。 ユーザー管理の管理者は、グローバル管理者の削除、他の管理者ロールの作成、または課金管理者、グローバル管理者、サービス管理者のパスワードの再設定を行うことはできません。

既定では、Microsoft Intune サブスクリプションの作成に使用するアカウントは、全体管理者の役割を持つテナント管理者です。 テナント管理者は、Intune 管理者コンソールを使って、Intune のサブスクリプションを管理し、[Office 365 ポータル](http://go.microsoft.com/fwlink/p/?LinkId=698854)からテナント管理者を割り当てます。 全体管理者の役割を持つテナント管理者を使用してポータルにアクセスし、最初のサービス管理者を割り当てます。 ベスト プラクティスとして、テナント管理者を日常の管理タスクに使用しないでください。 テナント管理者は、Intune 管理者コンソールにアクセスするときに、Intune のライセンスは必要ありません。 テナント管理者は、Microsoft クラウド サービスで共通の概念です。 Intune にサブスクライブするときに使用するサービスは、Azure AD のテナントです。 詳しくは、「[Azure AD ディレクトリとは](http://technet.microsoft.com/library/jj573650.aspx)」の Azure AD テナントに関するセクションをご覧ください。

テナント管理者は、[Office 365 ポータル](http://go.microsoft.com/fwlink/p/?LinkId=698854)を使用してサブスクリプションを管理します。また、管理者の役割で許可されている場合、次のタスクを管理できます。

- ユーザー アカウントを管理し、社内 Active Directory のディレクトリとの同期を構成する
- セキュリティ グループと呼ばれる、ユーザーのグループを管理する
- Intune のユーザー ライセンスを割り当てる
- ユーザーがサインインするときに使用する、サブスクリプションのドメイン名 (contoso.com など) を構成する
- ライセンスやクラウドの記憶域スペースなどの、課金と購入を管理する
- Intune サービスの正常性を表示するリンクを探す

Office 365 ポータルにアクセスするには、アカウントのサインイン状態が "**許可済み**" になっている必要があります。 これは、サブスクリプションのライセンスを与えられていることとは別です。 既定では、すべてのユーザー アカウントは、"**許可済み**" の状態です。 管理者権限を持たないユーザーは、Office 365 ポータルを使って、Intune パスワードをリセットすることができます。

### <a name="service-administrator"></a>サービス管理者

既定では、Intune はサービス管理者を割り当てません。 代わりに、全体管理者の役割を持つテナント管理者を使用して、サブスクリプション用の最初のサービス管理者を割り当てる必要があります。 サービス管理者は、[Intune 管理コンソール](https://manage.microsoft.com/)を使って、Intune の日常のタスクを管理します。 サービス管理者は、管理コンソール内から割り当てます。 サービス管理者が管理コンソールにアクセスするには、Intune のライセンスが必要です。

サービス管理者には、次の権限の 1 つが割り当てられます。
- **フル アクセス**: Intune 管理コンソールのあらゆる部分に無制限にアクセスでき、他のサービス管理者を追加および管理できます
- **読み取り専用アクセス**: Intune 管理コンソールのすべての部分に対する読み取り権限であり、データを変更することはできませんが、レポートは実行できます
- **ヘルプデスク - グループ ノード**: この権限を持つサービス管理者は、ヘルプデスクのシナリオに関するタスクだけを実行できます。「[管理者の役割に応じて Intune コンソール ビューをカスタマイズする](/intune/deploy-use/control-what-admins-can-see-in-the-microsoft-intune-admin-console)」をご覧ください

サービス管理者として、このポータルを使用して、次のような日常のタスクを管理します。

- コンピューターとモバイル デバイスのポリシーを作成して管理する
- ソフトウェアの更新プログラムとアプリをアップロードして展開する
- コンピューターの Endpoint Protection を管理する
- デバイスの状態を表示し、レポートを実行する

### <a name="device-enrollment-managers"></a>デバイス登録マネージャー

デバイス登録マネージャーは、より多くのユーザーレス デバイスを登録するための追加の権限を持つ標準ユーザー アカウントです。 既定では、各 Intune ユーザーが登録できるデバイスは最大 15 台までです。 管理者は、ユーザー アカウントにデバイス登録マネージャーの権限を付与できます。 そのアカウントは、企業が所有する多数のデバイスを登録できます。 これは、一時的にデバイスをユーザーに割り当てる可能性がある場合や、ユーザーとデバイスの関連付けが必要ないキオスク モードで使用する場合に役立ちます。 詳しくは、「[Microsoft Intune のデバイス登録マネージャーを使用した企業所有デバイスの登録](https://docs.microsoft.com/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune)」をご覧ください。

>[!div class="step-by-step"]

>[&larr;**ドメイン設定**](.\start-with-a-paid-subscription-to-microsoft-intune-step-2.md)     [**Intune のライセンスを管理する**&rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-4.md)  



<!--HONumber=Dec16_HO2-->


