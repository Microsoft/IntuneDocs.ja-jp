---
# required metadata

title: サービスの説明 | Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 40fa5a2e-6c0f-4150-9740-d5ddc0cdbda0

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Microsoft Intune サービスの説明

Microsoft Intune は、クラウドベースのサービスであり、Windows PC に加えて、iOS、Mac OS X、Android、および Windows のモバイル デバイスを管理するのに便利です。 Intune では、会社のアプリケーションとデータを保護することもできます。 Intune 単独で使用することも、System Center 2012 R2 Configuration Manager と統合して管理機能を拡張することもできます。

Microsoft では、Intune オンボーディング特典で、適格なプランの適格なサービスを提供します。 オンボーディング特典では、Intune 環境を使用できるようにするために、Microsoft の専門家がリモートでお手伝いします。 詳細については、[Microsoft Intune オンボーディング特典の説明](http://go.microsoft.com/fwlink/?LinkId=619281)のページを参照してください。

Intune は、100 ユーザー ライセンスを含む 30 日間の無料試用版で使用することができます。 無料試用版を使用するには、[ここをクリックして Intune のサインアップ ページ](http://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/)にアクセスしてください。 お客様の組織が Enterprise Agreement または同等のボリューム ライセンス契約を結んでいる場合は、Microsoft 担当者に連絡して無料試用版の設定を依頼してください。

> [!NOTE]
> お客様の組織が Microsoft Online Services の職場や学校用アカウントをお持ちで、試用期間の終了後に Intune サブスクリプションを本番環境で継続して使用する場合、ページで **[サインイン]** オプションをクリックし、組織のグローバル管理者アカウントを使用して認証を受けてください。 こうすることで、Intune 試用版が既存の職場や学校用アカウントと関連付けられます。

モバイル デバイスで構成できる設定の一覧については、次のページを参照してください。

-   [Microsoft Intune のモバイル デバイス管理機能](mobile-device-management-capabilities-in-microsoft-intune.md)

-   [Configuration Manager でのモバイル デバイスの全般設定](https://technet.microsoft.com/en-us/library/dn376523.aspx)

System Center 2012 R2 Configuration Manager については、「[System Center 2012 Configuration Manager のドキュメント ライブラリ](https://technet.microsoft.com/library/gg682041.aspx)」を参照してください。

## Intune サービスの更新が及ぼす影響
Intune はオンライン サービスであるため、Microsoft によって定期的に更新される可能性があります。

このトピックでは、これらのサービスが更新される頻度について、またサービスの更新がサービスの使用に影響を及ぼす可能性がある場合に届く事前通知について有用な情報を提供します。

Intune サービスの変更点については、「[Microsoft Intune の新機能](/intune/deploy-use/Whats-new-in-microsoft-intune.md)」を参照してください。 [Microsoft Intune ブログ](http://blogs.technet.com/b/microsoftintune/)でも、サービスの変更について取り上げており、Intune を最大限に利用するのに役立つヒントを提供しています。

重要なサービスの更新情報も、[Office 365 管理ポータル](https://portal.office.com/Admin/Default.aspx)のメッセージ センターでユーザーに公開されます。 コンパニオン [Office 365 Admin Mobile アプリ](https://support.office.com/en-us/article/Office-365-Admin-Mobile-App-e16f6421-2a1a-4142-bf9d-9846600a060a)をインストールしている場合、モバイル デバイスで通知を受け取ることができます。

> [!NOTE] Intune のサービス正常性は、[Office 365 管理ポータル](https://portal.office.com/Admin/Default.aspx)で監視できます。 左側のウィンドウで **[サービス正常性]** を選択します。  

Intune サービスに関して、Microsoft からは次のような通知が提供されます。
-   サービスの変更に関する計画を立てられるように、サービスのアップグレードが行われる少なくとも 30 ～ 90 日前に通知します。変更が及ぼす影響の大きさによって異なります。 掲示板アラートのような、製品に組み込まれている通信チャネルを使用して通知されます。 次のような変更が含まれます。
* コンプライアンスまたは法規制に影響を及ぼす可能性がある更新プログラム
* ユーザー エクスペリエンス、ユーザー インターフェイス、およびワークフローへの変更
* 新しいAPI または変更された API – カスタム アプリの旧バージョンとの互換性を確保するためのテストが必要であることを通知します。
* システム要件に対する変更。たとえば、最低限必要なブラウザー バージョンの変更。
* 機能を有効にするため措置、またはサービスが機能を中断するのを回避するための措置を講じることが求められる更新。
-   Microsoft は、毎月のサービス更新で、新機能および既存機能に対する拡張に関する情報を提供します。 一般に、Microsoft は、各月の中旬頃にサービスの更新をロールアウトします。 更新プログラムについては、「[Microsoft Intune の新機能](/intune/deploy-use/whats-new-in-microsoft-intune.md)」を参照してください。
-   Intune サービスの提供が終了する場合は、12 か月前に通知されます。

## 適切な管理ソリューションの選択
Intune には、会社のモバイル デバイスとコンピューター (このドキュメントでは**デバイス**と呼びます) を管理および保護するさまざまな構成方法があります。

-   **Intune スタンドアロン構成。** Intune の Web ベースの管理コンソールを使用して組織内のデバイスを管理します。 Intune を使用するときに社内の IT インフラストラクチャを使用する必要はありませんが、Intune と Active Directory ドメイン サービスを使用している場合は、ドメイン サービスで管理しているドメイン ユーザー アカウントを Intune に使用できます。

-   **Intune と System Center Configuration Manager。** Configuration Manager の管理コンソールを使うと、企業のコンピューターやモバイル デバイスを管理できます。 この構成を利用すると、Configuration Manager 管理コンソールという 1 つのコンソールで、すべての組織のデバイスを管理することができます。 Configuration Manager は、多数のモバイル デバイス、サーバー、コンピューターをサポートしています。 詳細については、「[System Center 2012 Configuration Manager のドキュメント ライブラリ](https://technet.microsoft.com/library/gg682041.aspx)」の [Configuration Manager と Microsoft Intune を使用してモバイル デバイスを管理する方法](http://go.microsoft.com/fwlink/?LinkID=271118)に関するページを参照してください。  適切な方法を判断するのに役立つ情報については、「[エンタープライズ モビリティを実現する方法](/intune/plan-design/ways-to-do-enterprise-mobility.md)」を参照してください。

-   Office 365 でサポートされているモバイル デバイス管理。「[エンタープライズ モビリティを実現する方法](/intune/plan-design/ways-to-do-enterprise-mobility.md)」を参照してください。

## Intune の詳細
Intune の詳細については、次のリソースを参照してください。

-   [Microsoft Intune セキュリティ センター](http://www.microsoft.com/en-us/server-cloud/products/intune-trust-center/)では、Intune のセキュリティ、プライバシー、およびコンプライアンスのプラクティスに関する情報を提供しているほか、Intune の認定資格の一部についても説明しています。

-   [Microsoft Intune のモバイル デバイス管理機能](/intune/understand-explore/mobile-device-management-capabilities-in-microsoft-intune.md)

### 関連項目
[Microsoft Intune](https://docs.microsoft.com/intune/)
[System Center 2012 Configuration Manager のドキュメント ライブラリ](https://technet.microsoft.com/library/gg682041.aspx)

[Microsoft Intune の新機能](/intune/deploy-use/whats-new-in-microsoft-intune.md)


<!--HONumber=May16_HO3-->


