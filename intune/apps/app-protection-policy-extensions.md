---
title: 拡張機能用アプリ保護ポリシー
titleSuffix: Microsoft Intune
description: このトピックでは、拡張機能用アプリ保護ポリシー (APP) について説明します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: demerson
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f38f22d7aaf03f278fad86061aa8198c8e37f31f
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2019
ms.locfileid: "71725492"
---
# <a name="protecting-application-extensions"></a>アプリケーション拡張機能の保護

この記事では、Microsoft Intune の拡張機能用アプリ保護ポリシーについて説明します。

## <a name="add-ins-for-outlook-app"></a>Outlook アプリ用のアドイン

Outlook アドインを使用すると、人気のあるアプリをメール クライアントと統合できます。 Outlook 用のアドインは、Web、Windows、Mac、および Android と iOS 用の Outlook で利用できます。 Intune APP SDK と Intune アプリ保護ポリシーには、Outlook 用のアドインを管理するためのサポートは含まれていませんが、別の方法でその使用を制限できます。 アドインは Microsoft Exchange を介して管理されるため、Exchange でユーザーに対してアドインがオフになっていない限り、ユーザーは Outlook と管理対象外のアドイン アプリケーションの間でデータとメッセージを共有できます。

エンド ユーザーによる Outlook アドインのアクセスとインストールを禁止する場合は (これは Outlook のすべてのクライアントに影響します)、Exchange 管理センターで役割に対して次の変更を行っていることを確認してください。

- ユーザーが Office ストアのアドインをインストールできないようにするには、ユーザーからマイ マーケットプレース役割を削除します。
- ユーザーがアドインをサイド ローディングできないようにするには、ユーザーからマイ カスタム アプリ役割を削除します。
- ユーザーがすべてのアドインをインストールできないようにするには、ユーザーからマイ カスタム アプリ役割とマイ マーケットプレース役割の両方を削除します。

次の手順は、Office 365、Exchange 2016、Exchange 2013 に適用され、Web、Windows、Mac、およびモバイルの Outlook が対象になります。

- Outlook 用アドインの詳細については、[こちら](https://technet.microsoft.com/library/jj943753(v=exchg.150).aspx)を参照してください。
- Outlook アプリ用のアドインをインストールおよび管理できる管理者とユーザーを指定する方法の詳細については、[こちら](https://technet.microsoft.com/library/jj943754(v=exchg.150).aspx)を参照してください。

## <a name="linkedin-account-connections-for-microsoft-apps"></a>Microsoft アプリの LinkedIn アカウントの接続

LinkedIn アカウントの接続では、ユーザーは特定の Microsoft アプリ内の LinkedIn パブリック プロファイル情報を表示することができます。 既定で、ユーザーは LinkedIn と Microsoft の職場または学校アカウントを接続して、追加の LinkedIn プロファイル情報を表示するよう選択できます。 

> [!NOTE]
> LinkedIn 統合は現在、米国政府機関の顧客、およびオーストラリア、カナダ、中国、フランス、ドイツ、インド、韓国、イギリス、日本、南アフリカでホストされている Exchange Online メールボックスを使用する組織では利用できません。

Intune SDK と Intune アプリ保護ポリシーには、LinkedIn アカウントの接続を管理するためのサポートは含まれていませんが、別の方法でそれらを管理できます。 組織全体に対して LinkedIn アカウントの接続を無効にすることも、組織内の選択したユーザー グループに対して LinkedIn アカウントの接続を有効にすることもできます。 これらの設定は、すべてのプラットフォーム (Web、モバイル、デスクトップ) 上の Office 365 アプリ間の LinkedIn 接続に影響します。 次の操作を行います。

- Azure portal で、テナントに対する LinkedIn アカウントの接続を有効または無効にします。 
- グループ ポリシーを使用して、組織の Office 2016 アプリに対する LinkedIn アカウントの接続を有効または無効にします。

テナントに対して LinkedIn 統合が有効になっている場合、組織内のユーザーが LinkedIn および Microsoft の職場または学校アカウントを接続したときに、次の 2 つのオプションを使用できます。 

- 両方のアカウント間でデータを共有するためのアクセス許可を付与することができます。 これは、LinkedIn アカウントに Microsoft の職場または学校アカウントとデータを共有するためのアクセス許可を与え、Microsoft の職場または学校アカウントに LinkedIn アカウントとデータを共有するためのアクセス許可を与えることを意味します。 LinkedIn と共有されるデータは、オンライン サービスを離れます。 
- LinkedIn アカウントからのみデータを共有するためのアクセス許可を、Microsoft の職場または学校アカウントに付与することができます

ユーザーがアカウント間でデータを共有することに同意した場合、Office アドインの場合と同様に、LinkedIn 統合では既存の Microsoft Graph API を使用します。 LinkedIn 統合では Office アドインで利用可能な API のサブセットのみを使用し、さまざまな除外をサポートします。


|Microsoft Graph に対するアクセス許可  |説明  |
|---------|---------|
|[人](https://developer.microsoft.com/graph/docs/concepts/permissions_reference#people-permissions)に対する読み取りアクセス許可     |アプリがサインインしたユーザーに関連する人のスコア付きリストを読み取ることを許可します。 このリストには、ローカルの連絡先、ソーシャル ネットワーキングまたは組織のディレクトリからの連絡先、最近 (メールや Skype などで) 連絡した人が含まれる場合があります。         |
|[予定表](https://developer.microsoft.com/graph/docs/concepts/permissions_reference#calendars-permissions)に対する読み取りアクセス許可     |アプリがユーザーの予定表内のイベントを読み取ることを許可します。 サインインしたユーザーの予定表の会議、その時間、場所、および出席者が含まれます。         |
|[ユーザー プロファイル](https://developer.microsoft.com/graph/docs/concepts/permissions_reference#user-permissions)に対する読み取りアクセス許可     |ユーザーがアプリにサインインすることと、アプリがサインインしたユーザーのプロファイルを読み取ることを許可します。 アプリがサインインしたユーザーの基本的な会社情報を読み取ることも許可します。         |
|Subscriptions     |このスコープは利用できず、まだ使用されていません。 Office 365 などの Microsoft アプリとサービスに対する、ユーザーの組織によって提供されるサブスクリプションが含まれます。         |
|インサイト     |このスコープは利用できず、まだ使用されていません。 Microsoft サービスの使用に基づき、サインインしたユーザーのアカウントに関連付けられている関心が含まれます。         |

### <a name="learn-more"></a>詳細情報

- [Microsoft アプリの LinkedIn の情報と機能](https://go.microsoft.com/fwlink/?linkid=850740)について学習します。
- [Office 365 ロードマップ ページ](https://products.office.com/en-US/business/office-365-roadmap?filters=%26freeformsearch=linkedin#abc)に示されている LinkedIn アカウント接続のリリースについて学習します。 
- [LinkedIn アカウント接続の構成](https://docs.microsoft.com/azure/active-directory/linkedin-integration)について学習します。
- ユーザーの LinkedIn および Microsoft の職場または学校アカウント間で共有されるデータの詳細については、[職場または学校の Microsoft アプリケーションの LinkedIn](https://www.linkedin.com/help/linkedin/answer/84077) に関するページを参照してください。

