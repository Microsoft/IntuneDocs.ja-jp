---
title: "Microsoft Intune サービスの説明"
description: "Intune は、クラウドベースのサービスであり、Windows、iOS、Mac OS X、Android、および Windows Mobile デバイスを管理するのに便利です。"
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 06/15/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 40fa5a2e-6c0f-4150-9740-d5ddc0cdbda0
ms.reviewer: cacamp
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 73b43084c28436cb8a7e866dcee2d52694c60f5c
ms.openlocfilehash: 830a23e63536829f3905ff291bff25e0890457e8
ms.contentlocale: ja-jp
ms.lasthandoff: 06/16/2017


---

# <a name="microsoft-intune-service-description"></a>Microsoft Intune サービスの説明

[!INCLUDE[both-portal](./includes/note-for-both-portals.md)]

Microsoft Intune は、クラウドベースのサービスであり、Windows、Mac OS X、iOS、Android、および Windows Mobile を管理するのに便利です。 Intune では、会社のアプリケーションとデータを保護することもできます。 Intune は単独で使用することも、System Center Configuration Manager と統合して管理機能を拡張することもできます。

Microsoft では、Intune オンボーディング特典で、適格なプランの適格なサービスを提供します。 オンボーディング特典では、Intune 環境を使用できるようにするために、Microsoft の専門家がリモートでお手伝いします。 オンボーディング特典の詳細については、「[Enterprise Mobility の FastTrack プログラム](http://go.microsoft.com/fwlink/?LinkId=619281)」を参照してください。

Intune は、100 ユーザー ライセンスを含む 30 日間の無料試用版で使用することができます。 無料試用版を開始する場合は、[Intune のサインアップ ページ](https://www.microsoft.com/server-cloud/products/microsoft-intune/)にアクセスしてください。 お客様の組織が Enterprise Agreement または同等のボリューム ライセンス契約を結んでいる場合は、Microsoft 担当者に連絡して無料試用版の設定を依頼してください。

> [!NOTE]
> お客様の組織が Microsoft Online Services の職場や学校用アカウントをお持ちで、試用期間の終了後に Intune サブスクリプションを本番環境で継続して使用する場合、ページで **[サインイン]** オプションを選択し、組織のグローバル管理者アカウントを使用して認証を受けてください。 こうすることで、Intune 試用版が既存の職場や学校用アカウントと関連付けられます。

モバイル デバイスでセットアップできる設定の一覧については、次のページを参照してください。

-   [Microsoft Intune の登録済みデバイス管理機能](introduction-intune.md)

-   [System Center Configuration Manager と Microsoft Intune を使用するハイブリッド モバイル デバイス管理 (MDM)](/sccm/mdm/understand/hybrid-mobile-device-management)

System Center Configuration Manager については、「[System Center Configuration Manager のドキュメント](/sccm/index)」を参照してください。

## <a name="learn-how-intune-service-updates-affect-you"></a>Intune サービスの更新が及ぼす影響

Intune はオンライン サービスであり、モバイル デバイス OS とモバイル アプリのリリースによって MDM のエコシステムが頻繁に変更されることから、Microsoft では定期的に Intune を更新します。

この記事では、これらのサービスが更新される頻度について、またサービスの更新がサービスの使用に影響を及ぼす可能性がある場合に届く事前通知について有用な情報を提供します。

Intune サービスの変更内容について知る方法は 3 つあります。

- 1 つ目は、「[Microsoft Intune の新機能](whats-new.md)」を確認することです。 この一覧は、月ごとのサービス更新で更新されます。また、ポータル サイト アプリなどのアプリがリリースされた場合には週ごとに更新されます。 

- 2 つ目は、重要なサービスの更新情報です。これは、[Office 365 管理ポータル](https://portal.office.com/Admin/Default.aspx)のメッセージ センターに公開されます。 コンパニオン [Office 365 Admin Mobile アプリ](https://support.office.com/article/Office-365-Admin-Mobile-App-e16f6421-2a1a-4142-bf9d-9846600a060a)をインストールしている場合、モバイル デバイスで通知を受け取ることができます。 Office 365 メッセージ センター内での操作方法の詳細については、[こちら](https://support.office.com/en-US/client/results?Shownav=true&lcid=1033&ns=O365ENTADMIN&version=15&omkt=en-US&ver=15&HelpID=O365E_MCManageUpdates)をご覧ください。 
    
    いくつかの役立つヒント: 

    - Office 365 メッセージ センターのメッセージは、対象を絞っています。 つまり、Intune for EDU のオファーを受けない企業に対して、Intune for EDU に関するメッセージは送信されません。 

    - メッセージには有効期限があります。 たとえば、最新機能ページへのリンクを含む、サービス更新に関する通知は、次のサービス更新の通知が送信される前に期限切れになる可能性があります。 そのようにしないと、関連のない投稿のバックログが大量に増えることになります。

    - Office 365 Admin Mobile アプリでは、すべてのメッセージを検索し、組織内の同僚と共有したい場合は通知を転送できます。

    - [Edit message center preferences]\(メッセージ センターの設定の編集\) で最終的に **Intune** の切り替え機能を提供し、Intune サブスクリプションに投稿されたメッセージをユーザーが確認できるようにする予定です。 Office 365 の Mobile Device Management が表示されても、これは Intune ではなく別のサービスです。

- 3 つ目に、Microsoft では次の 2 つのブログを使用して、EMS のメッセージと Intune サポートのベスト プラクティスを共有しています。 
    
    - [Enterprise Mobility + Security のブログ](https://blogs.technet.microsoft.com/enterprisemobility/) 

    - [Intune サポートのブログ](https://blogs.technet.microsoft.com/intunesupport/) 

>[!Note]
>Intune のサービス正常性は、[Office 365 管理ポータル](https://portal.office.com/Admin/Default.aspx)で監視できます。 左側のウィンドウで **[サービス正常性]** を選択します。 また、[Office 365 Admin Mobile アプリ](https://support.office.com/article/Office-365-Admin-Mobile-App-e16f6421-2a1a-4142-bf9d-9846600a060a)を使用して、サービスの正常性を表示することもできます。

## <a name="types-of-notices-microsoft-provides-about-the-intune-service"></a>Intune サービスに関して Microsoft が提供する通知の種類

サービスの変更に関する計画を立てられるように、サービスの変更が行われる少なくとも 7 ～ 90 日前に通知します。変更が及ぼす影響の大きさによって異なります。 これらの変更には、以下のようなものがあります。

- ヘルプデスク スタッフまたはエンド ユーザーと共有する、エンド ユーザー エクスペリエンスの変更。 通常これらの変更が行われる 7 ～ 30 日前に通知します。変更は [Intune アプリ UI の新機能](whats-new-app-ui.md)に関するページに掲載されます。 スペル ミスの修正などは、通常ドキュメントでお知らせしません。 一方、エンド ユーザーの登録エクスペリエンスの変更は UI に大きな影響を及ぼすため、Microsoft では Office 365 メッセージ センターにお客様へのメッセージを投稿するとともに、Intune アプリ UI の新機能に関するページでも変更内容をお知らせします。これによりお客様は、実稼働環境に変更内容が適用される前に、エンド ユーザー向けガイダンスを評価し、更新する時間を持つことができます。

- お客様にご対応いただく必要がある変更は**変更の計画**と呼ばれ、通常、変更が行われる約 30 日前にお知らせします。 Office 365 メッセージ センターでは、このカテゴリは特別に [変更の計画] と表示されます。実稼働環境に変更内容が適用される日付が確定している場合は、感嘆符 (!) 付きで **Act By (対応期限)** の日付も表示され、視覚的な目印が提供されます。

- 廃止予定の機能については、通常、廃止の 90 日前に通知されます。 たとえば、IE の特定バージョンのサポートを終了する場合、Microsoft ではサポート終了の 90 日前にお知らせすることを目標にしています。 ただし、別の会社によって廃止予定が発表された場合は、廃止予定のお知らせが複雑になります。 たとえば、あるブラウザーが最新ビルドで Silverlight をサポートしないと通知してきた場合、Microsoft はそのブラウザーのサポート終了をお客様にお知らせしますが、この場合は通知のタイミングが 90 日以内になることがあります。

- Intune サービスの提供が終了する場合は、12 か月前に通知されます。

最後に、まれなケースですが、サービスを正常な状態に戻すためにインシデント後の措置が必要な場合や、ユーザーからのフィードバックに基づいたサービス中断の可能性がある大規模な変更については、Microsoft は [Office 365 の通信設定](https://support.office.com/en-us/article/Change-your-contact-preferences-for-communications-from-Microsoft-6f70de1b-a64d-4498-bfbd-be8c83a9c0fc?ui=en-US&rs=en-US&ad=US)と、有効な電子メール アドレス (職場の電子メール アドレスが望ましい) が指定されているかに基づいて、サービス管理者にメールをお送りします。  


## <a name="choose-the-management-solution-thats-right-for-you"></a>適切な管理ソリューションの選択
Intune には、会社のモバイル デバイスとコンピューター (この記事では**デバイス**と呼びます) を管理および保護するさまざまなセットアップ方法があります。

- **Intune スタンドアロン構成。** Intune の Web ベースの管理コンソールを使用して組織内のデバイスを管理します。 オンプレミスの IT インフラストラクチャを使用しなくても Intune を使用できます。 Intune と Active Directory Domain Services を使用している場合は、ドメイン サービスで管理しているドメイン ユーザー アカウントを Intune に使用できます。

- **Intune と System Center Configuration Manager。** Configuration Manager の管理コンソールを使うと、企業のコンピューターやモバイル デバイスを管理できます。 この構成を利用すると、Configuration Manager 管理コンソールという 1 つのコンソールで、すべての組織のデバイスを管理することができます。 Configuration Manager は、多数のモバイル デバイス、サーバー、コンピューターをサポートしています。 Configuration Manager の詳細については、「[System Center Configuration Manager と Microsoft Intune を使用するハイブリッド モバイル デバイス管理 (MDM)](/sccm/mdm/understand/hybrid-mobile-device-management)」を参照してください。 自分に適した手法を決める際は、「[Choose between Microsoft Intune standalone and hybrid mobile device management with Configuration Manager](/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management)」 (Microsoft Intune スタンドアロンを実行するのと Configuration Manager でハイブリッド MDM を実行するのはどちらが良いか) がお役に立ちます。


## <a name="learn-more-about-intune"></a>Intune の詳細
Intune の詳細については、次のリソースを参照してください。

- [Microsoft Intune セキュリティ センター](https://www.microsoft.com/server-cloud/products/intune-trust-center/)では、Intune のセキュリティ、プライバシー、およびコンプライアンスのプラクティスに関する情報を提供しているほか、Intune の認定資格の一部についても説明しています。

- [Microsoft Intune の登録済みデバイス管理機能](introduction-intune.md)

### <a name="see-also"></a>関連項目
[Microsoft Intune](index.md)
[System Center 2012 Configuration Manager のドキュメント ライブラリ](https://technet.microsoft.com/library/gg682041.aspx)

[Microsoft Intune の新機能](whats-new.md)

