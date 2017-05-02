---
title: "Azure Portal プレビューでの Intune の概要"
titleSuffix: Intune Azure preview
description: "Intune Azure プレビュー: Azure Portal プレビューでの Intune の基本と、Intune を利用してデバイスを管理する方法について説明します。"
keywords: 
author: robstackmsft
ms.author: robstack
nmanager: angrobe
ms.date: 04/24/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4a085264-232a-4af0-97f1-747496c44517
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 8b2bd3ecba0b597bc742ea08872ffe8fc58155cf
ms.openlocfilehash: 92e07a49205ffaf287fc3aa2da6a6376b75fda4f
ms.lasthandoff: 04/24/2017


---


# <a name="introduction-to-microsoft-intune-in-the-azure-portal-preview"></a>Azure Portal プレビューでの Microsoft Intune の概要


[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Microsoft Intune は Azure Portal への移行中であり、これまでの使い慣れたワークフローと機能には変更が加えられることになります。
新しいポータルでは、Azure Portal の新機能と更新された機能のプレビューが提供されており、組織で所有するモバイル デバイス、PC、アプリの管理に利用できます。
最終的には Intune のすべての機能が Azure に移行しますが、現時点での Azure Portal では特定の Intune タスクのみを実行できます。 この新しいエクスペリエンスはプレビュー段階にあり、一部の機能はまだポータル上に存在しない場合があります。 詳細については、「[新機能](#what's-new)」セクションを参照してください。

> [!IMPORTANT]
> **新しいポータルがまだ表示されない場合**<br>
> 一部のテナントに対して、既にプレビュー版のロールアウトが開始されています。 2017 年の初めには、新しいエクスペリエンスへの既存テナントの移行が開始される予定です。 ご利用のテナントが移行される際は、事前に Office メッセージ センターに通知が届きます。


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

### <a name="introduction-and-get-started"></a>概要と作業開始
このセクションには、Intune の[新機能](/intune-azure/introduction/whats-new)、[既知の問題](/intune-azure/introduction/known-issues-in-the-intune-preview)、[サポートを受ける方法](/intune-azure/introduction/how-to-get-support-for-microsoft-intune)、[無料評価版を開始](/intune-azure/introduction/sign-up-free-trial-microsoft-intune)する方法に関する情報が含まれています。
### <a name="plan-and-design"></a>計画と設計
Intune 環境の[計画と設計](/intune-azure/plan-and-design/get-started)に役立つ情報が含まれています。
### <a name="device-enrollment"></a>デバイスの登録
[デバイスを Intune の管理対象にする方法](/intune-azure/enroll-devices/what-is)。
### <a name="device-compliance"></a>デバイスのポリシー準拠
[デバイスのコンプライアンス レベルを定義し、準拠していないデバイスについてのレポートを作成します](/intune-azure/set-device-compliance/what-is-device-compliance)。
### <a name="device-configuration"></a>デバイス構成
[管理対象のデバイスで設定と機能を構成するために使用できるプロファイルについて理解します](/intune-azure/configure-devices/what-are-device-profiles)。
### <a name="devices"></a>[デバイス]
[インベントリとレポートによって管理対象デバイスの情報を把握します](/intune-azure/manage-devices/what-is)。
### <a name="mobile-apps"></a>モバイル アプリ
[アプリの発行、管理、構成、および保護方法](/intune-azure/manage-apps/what-is-app-management)。
### <a name="conditional-access"></a>条件付きアクセス
[指定した条件に応じて Exchange サービスへのアクセスを制限します](/intune-azure/conditional-access/what-is-conditional-access)。
### <a name="on-premises-access"></a>オンプレミスのアクセス
[Exchange ActiveSync および Exchange On-premises へのアクセスを構成します](/intune/deploy-use/mobile-device-management-with-exchange-activesync-and-microsoft-intune)
### <a name="users"></a>Users
[リソースを管理し、グループに分類するデバイスのユーザーについて](/intune-azure/manage-users/what-is)説明します。
### <a name="groups"></a>[グループ]
[Intune で Azure Active Directory グループを使用する方法について説明します](/intune-azure/manage-users/get-started-with-groups)
### <a name="intune-roles"></a>Intune ロール
[Intune の各種アクションを実行できるユーザーと、それらのアクションの適用先となるユーザーを制御します](/intune-azure/access-control/role-based-access-control)。 一般的な Intune シナリオを対象とする組み込みロールを使用するか、独自のロールを作成することができます。
### <a name="software-updates"></a>ソフトウェア更新プログラム
[Windows 10 デバイスのソフトウェア更新を構成する方法について説明します](/intune-azure/configure-devices/how-to-configure-windows-update-for-business)。



## <a name="whats-new"></a>新機能

プレビュー リリースの新機能については、[こちら](/intune-azure/introduction/whats-new)を参照してください。

