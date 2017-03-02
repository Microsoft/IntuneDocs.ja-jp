---
title: "Azure Portal プレビューでの Intune の概要"
titleSuffix: Intune Azure preview
description: "Intune Azure プレビュー: Azure Portal プレビューでの Intune の基本と、Intune を利用してデバイスを管理する方法について説明します。"
keywords: 
author: robstackmsft
ms.author: robstack
nmanager: angrobe
ms.date: 02/15/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4a085264-232a-4af0-97f1-747496c44517
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 851ed5e9967939a930d6d9c22a23d7c72a7b52a7
ms.openlocfilehash: f6f8babaca68fdb75ab6ff36d931f8dbd734acf0
ms.lasthandoff: 02/16/2017


---


# <a name="introduction-to-microsoft-intune-in-the-azure-portal-preview"></a>Azure Portal プレビューでの Microsoft Intune の概要


[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Microsoft Intune は Azure Portal への移行中であり、これまでの使い慣れたワークフローと機能には変更が加えられることになります。
新しいポータルでは、Azure Portal の新機能と更新された機能のプレビューが提供されており、組織で所有するモバイル デバイス、PC、アプリの管理に利用できます。
最終的には Intune のすべての機能が Azure に移行しますが、現時点での Azure Portal では特定の Intune タスクのみを実行できます。 この新しいエクスペリエンスはプレビュー段階にあり、一部の機能はまだポータル上に存在しない場合があります。 詳細については、「[新機能](#what's-new-in-the-preview)」セクションを参照してください。

> [!IMPORTANT]
> **新しいポータルがまだ表示されない場合**<br>
> 一部のテナントに対して、既にプレビュー版のロールアウトが開始されています。 2017 年の初めには、新しいエクスペリエンスへの既存テナントの移行が開始される予定です。 ご利用のテナントが移行される際は、事前に Office メッセージ センターに通知が届きます。 テナント移行のスケジュールに関して質問がある場合は、Microsoft の移行チーム ([intunegrps@microsoft.com](mailto:intunegrps@microsoft.com)) にお問い合わせください。


このライブラリには新しい製品ドキュメントが追加され、プレビュー期間中に随時更新されます。 ドキュメントの内容についてご提案がございましたら、トピックのコメント欄にフィードバックをお寄せください。 ご意見をお待ちしております。

<!--- You can view the new Intune technical preview console in Azure at [portal.azure.com]. --->

新しいエクスペリエンスの概要を以下に示します。

- すべての Enterprise Mobility + Security (EMS) コンポーネント用の統合コンソール
- Web 標準に基づく HTML ベースのコンソール
- 多数のアクションを自動化するために Microsoft Graph API をサポート
- Azure Active Directory (AD) グループによってすべての Azure アプリケーション間での互換性を提供
- 最新の Web ブラウザーの大部分に対応

クラシック Intune コンソールに関するドキュメントをお探しの場合は、[Intune ドキュメント ライブラリ](https://docs.microsoft.com/en-us/intune/)を参照してください。

## <a name="before-you-start"></a>アップグレードを開始する前に

Azure Portal で Intune を使用するには、Intune の管理者およびテナント アカウントが必要です。 まだお持ちでない場合は、[アカウントにサインアップ](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20)してください。

## <a name="supported-web-browsers-for-the-azure-portal"></a>Azure Portal でサポートされている Web ブラウザー

Azure Portal は、ほとんどの最新 PC、Mac、タブレットで動作します。 携帯電話はサポート対象外です。
現時点では、以下のブラウザーがサポートされています。

- Microsoft Edge (最新バージョン)
- Microsoft Internet Explorer 11
- Safari (最新バージョン、Mac のみ)
- Chrome (最新バージョン)
- Firefox (最新バージョン)

サポート対象のブラウザーに関する最新情報については、[Azure Portal に関するページ](https://docs.microsoft.com/azure/azure-preview-portal-supported-browsers-devices)を参照してください。

## <a name="whats-in-this-library"></a>このライブラリの内容

必要な情報が見つけやすくなるように、ドキュメントには Intune ポータルのレイアウトが反映されています。

![Azure Portal のワークロード](./media/azure-portal-workloads.png)

<!--- ### Plan and design
Information to help you plan and design your Intune environment.
[Read more](/intune-azure/plan-and-design/get-started) --->
### <a name="enroll-devices"></a>デバイスの登録
[デバイスを Intune の管理対象にする方法](/intune-azure/enroll-devices/what-is)。
### <a name="devices--groups"></a>デバイスとグループ
[インベントリとレポートによって管理対象デバイスの情報を把握します](/intune-azure/manage-devices/what-is)。
### <a name="manage-users"></a>ユーザーの管理
[管理対象デバイスのユーザーの情報が得られます](/intune-azure/manage-users/what-is)。
### <a name="manage-apps"></a>アプリを管理する
[アプリの発行、管理、構成、および保護方法](/intune-azure/manage-apps/what-is-app-management)。
### <a name="configure-devices"></a>デバイスの構成
[管理対象のデバイスで設定と機能を構成するために使用できるプロファイルについて理解します](/intune-azure/configure-devices/what-are-device-profiles)。
### <a name="set-device-compliance"></a>デバイス コンプライアンスの設定
[デバイスのコンプライアンス レベルを定義し、準拠していないデバイスについてのレポートを作成します](/intune-azure/set-device-compliance/what-is-device-compliance)。
### <a name="conditional-access"></a>条件付きアクセス
[指定した条件に応じて Exchange サービスへのアクセスを制限します](/intune-azure/conditional-access/what-is-conditional-access)。
### <a name="access-control"></a>アクセス制御
[Intune の各種アクションを実行できるユーザーと、それらのアクションの適用先となるユーザーを制御します](/intune-azure/access-control/role-based-access-control)。 一般的な Intune シナリオを対象とする組み込みロールを使用するか、独自のロールを作成することができます。



## <a name="whats-new"></a>新機能

プレビュー リリースの新機能については、[こちら](/intune-azure/introduction/whats-new)を参照してください。

