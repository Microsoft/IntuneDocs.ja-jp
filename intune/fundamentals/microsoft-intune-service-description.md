---
title: Microsoft Intune サービスの説明
description: Microsoft Intune は、クラウドベースのサービスであり、Windows、iOS、Mac OS X、Android、および Windows Mobile デバイスを管理するのに便利です。
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 05/30/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.assetid: 40fa5a2e-6c0f-4150-9740-d5ddc0cdbda0
ms.reviewer: cacamp
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7744fe217f39436e91f90fdf567f469c01986da4
ms.sourcegitcommit: 2506cdbfccefd42587a76f14ee50c3849dad1708
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/11/2020
ms.locfileid: "75885659"
---
# <a name="microsoft-intune-service-description"></a>Microsoft Intune サービスの説明

Intune はクラウドベースのエンタープライズ モビリティ管理 (EMM) サービスであり、会社のデータを守りながら、社員に生産的に働いてもらうことができます。 Intune では次のことができます。
* 社員が会社のデータにアクセスするために利用するモバイル デバイスを管理します。
* 社員が利用するクライアント アプリを管理します。
* 社員が会社の情報にアクセスし、共有する方法を制御し、会社の情報を保護します。
* デバイスやアプリが会社のセキュリティ要件に準拠するように管理します。

Intune は ID とアクセス制御のために Azure Active Directory (Azure AD) と、データ保護のために Azure Information Protection と密接に統合されます。 Configuration Manager と統合して管理機能を拡張することもできます。

Intune でデバイス、アプリ、企業データを管理し、保護する方法については、[Intune 文書](../index.yml)をご覧ください。

## <a name="30-day-free-trial"></a>30 日間の無料評価版
Intune は、100 ユーザー ライセンスを含む 30 日間の無料試用版で使用することができます。 無料試用版を開始する場合は、[Intune のサインアップ ページ](https://admin.microsoft.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20)にアクセスしてください。 お客様の組織が Enterprise Agreement または同等のボリューム ライセンス契約を結んでいる場合は、Microsoft 担当者に連絡して無料試用版の設定を依頼してください。

> [!NOTE]
> お客様の組織が Microsoft Online Services の職場や学校用アカウントをお持ちで、試用期間の終了後に Intune サブスクリプションを本番環境で継続して使用する場合、ページで **[サインイン]** オプションを選択し、組織のグローバル管理者アカウントを使用して認証を受けてください。 こうすることで、Intune 試用版が既存の職場や学校用アカウントと関連付けられます。

<!--- For a list of settings that you can set up on mobile devices, see:

- [Enrolled device management capabilities of Microsoft Intune](introduction-intune.md)

--->
## <a name="intune-onboarding-benefit"></a>Intune のオンボーディング特典
Microsoft では、Intune オンボーディング特典で、適格なプランの適格なサービスをオファーします。 オンボーディング特典では、Intune 環境を使用できるようにするために、Microsoft の専門家がリモートでお手伝いします。 オンボーディング特典の詳細については、「[Enterprise Mobility の FastTrack プログラム](https://go.microsoft.com/fwlink/?LinkId=619281)」を参照してください。


## <a name="learn-how-intune-service-updates-affect-you"></a>Intune サービスの更新が及ぼす影響

モバイル デバイス管理のエコシステムがオペレーティング システムの更新プログラムやモバイル アプリのリリースに合わせて頻繁に変更されるため、Microsoft は Intune を定期的に更新しています。 Intune サービスの変更内容について知る方法は 3 つあります。

- [Microsoft Intune の新機能](whats-new.md) このトピックは、月ごとのサービス更新で更新されます。また、ポータル サイト アプリなどのアプリがリリースされた場合には週ごとに更新されます。

- 重要なサービスの更新情報も、[Microsoft 365 管理センター](https://admin.microsoft.com/)のメッセージ センターで告知されます。 コンパニオン [Office 365 Admin Mobile アプリ](https://support.office.com/article/Office-365-Admin-Mobile-App-e16f6421-2a1a-4142-bf9d-9846600a060a)をインストールしている場合、モバイル デバイスで通知を受け取ることができます。 Office 365 メッセージ センターの利用方法については[こちら](https://support.office.com/client/results?Shownav=true&ns=O365ENTADMIN&version=15&ver=15&HelpID=O365E_MCManageUpdates)をご覧ください。

  いくつかの役立つヒント:

  - Office 365 メッセージ センターのメッセージは、対象を絞っています。 つまり、Intune for EDU のオファーを受けない企業に対して、Intune for EDU に関するメッセージは送信されません。

  - メッセージには有効期限があります。 たとえば、最新機能ページへのリンクを含む、サービス更新に関する通知は、次のサービス更新の通知が送信される前に期限切れになる可能性があります。 そのようにしないと、関連のない投稿のバックログが大量に増えることになります。

  - Office 365 Admin Mobile アプリでは、すべてのメッセージを検索し、組織内の同僚と共有したい場合は通知を転送できます。

  - [Edit message center preferences]\(メッセージ センターの設定の編集\) で最終的に **Intune** の切り替え機能を提供し、Intune サブスクリプションに投稿されたメッセージをユーザーが確認できるようにする予定です。 Office 365 の Mobile Device Management が表示されても、これは Intune ではなく別のサービスです。

- Microsoft では次の 2 つのブログを利用し、EMS のメッセージと Intune サポートのベスト プラクティスを共有しています。

  - [Enterprise Mobility + Security のブログ](https://blogs.technet.microsoft.com/enterprisemobility/)

  - [Intune サポートのブログ](https://blogs.technet.microsoft.com/intunesupport/)

> [!Note]
> Intune のサービス正常性は、[Microsoft 365 管理センター](https://admin.microsoft.com)で監視できます。 左側のウィンドウで **[サービス正常性]** を選択します。 また、[Office 365 Admin Mobile アプリ](https://support.office.com/article/Office-365-Admin-Mobile-App-e16f6421-2a1a-4142-bf9d-9846600a060a)を使用して、サービスの正常性を表示することもできます。

## <a name="types-of-notices-microsoft-provides-about-the-intune-service"></a>Intune サービスに関して Microsoft が提供する通知の種類

サービスの変更に関する計画を立てられるように、サービスの変更が行われる少なくとも 7 ～ 90 日前に通知します。変更が及ぼす影響の大きさによって異なります。 これらの変更には、以下のようなものがあります。

- ヘルプデスク スタッフまたはエンド ユーザーと共有する、エンド ユーザー エクスペリエンスの変更。 通常これらの変更が行われる 7 ～ 30 日前に通知します。変更は [Intune アプリ UI の新機能](whats-new-app-ui.md)に関するページに掲載されます。 スペル ミスの修正などは、通常ドキュメントでお知らせしません。 一方、エンド ユーザーの登録エクスペリエンスの変更は UI に大きな影響を及ぼすため、Microsoft では Office 365 メッセージ センターにお客様へのメッセージを投稿するとともに、Intune アプリ UI の新機能に関するページでも変更内容をお知らせします。これによりお客様は、実稼働環境に変更内容が適用される前に、エンド ユーザー向けガイダンスを評価し、更新する時間を持つことができます。

- お客様にご対応いただく必要がある変更は**変更の計画**と呼ばれ、通常、変更が行われる約 30 日前にお知らせします。 Office 365 メッセージ センターでは、このカテゴリは特別に [変更の計画] と表示されます。実稼働環境に変更内容が適用される日付が確定している場合は、感嘆符 (!) 付きで **Act By (対応期限)** の日付も表示され、視覚的な目印が提供されます。

- 廃止予定の機能については、通常、廃止の 90 日前に通知されます。 たとえば、IE の特定バージョンのサポートを終了する場合、Microsoft ではサポート終了の 90 日前にお知らせすることを目標にしています。 ただし、別の会社によって廃止予定が発表された場合は、廃止予定のお知らせが複雑になります。 たとえば、あるブラウザーが最新ビルドで Silverlight をサポートしないと通知してきた場合、Microsoft はそのブラウザーのサポート終了をお客様にお知らせしますが、この場合は通知のタイミングが 90 日以内になることがあります。

- Intune サービスの提供が終了する場合は、12 か月前に通知されます。

最後に、まれなケースですが、サービスを正常な状態に戻すためにインシデント後の措置が必要な場合や、ユーザーからのフィードバックに基づいたサービス中断の可能性がある大規模な変更については、Microsoft は [Office 365 の通信設定](https://support.office.com/article/Change-your-contact-preferences-for-communications-from-Microsoft-6f70de1b-a64d-4498-bfbd-be8c83a9c0fc)と、有効な電子メール アドレス (職場の電子メール アドレスが望ましい) が指定されているかに基づいて、サービス管理者にメールをお送りします。  


<!--- ## Choose the management solution that’s right for you
You can set up Intune in several ways to manage and help protect your company's mobile devices and computers (referred to as **devices** in this article).

- **Intune stand-alone configuration.** Use the web-based admin console in Intune to manage devices in your organization. Intune can be used without any on-premises IT infrastructure. If you use Intune with Active Directory Domain Services, you can use domain user accounts that you manage with Domain Services with Intune.

--->

## <a name="language-support"></a>言語サポート
Intune は Azure portal で実行されていますが、Azure portal によりサポートされている言語は、簡体中国語、繁体中国語、チェコ語、オランダ語、英語、ドイツ語、ハンガリー語、イタリア語、日本語、ポルトガル (ブラジル) 語、ポルトガル (ポルトガル) 語、ロシア語、スペイン語、英語、フランス語、韓国語、ポーランド語、スウェーデン語、トルコ語です。

Intune 管理コンソールとユーザーが対面するモバイル エクスペリエンスでは、Azure ポータルでサポートされている言語だけでなくデンマーク語、ギリシャ語、フィンランド語、ノルウェー語、およびルーマニア語もサポートしています。

<!--- ## Learn more about Intune
Use these resources to learn more about Intune:

- The [Microsoft Intune Trust Center](https://www.microsoft.com/server-cloud/products/intune-trust-center/) provides information about the security, privacy, and compliance practices of Intune, and it describes some of Intune's certifications.

- [Enrolled device management capabilities of Microsoft Intune](introduction-intune.md)--->
