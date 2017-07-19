---
title: "Azure Portal での Intune の概要"
titleSuffix: Intune on Azure
description: "Azure Portal での Intune の基本と、Intune を利用してデバイスを管理する方法について説明します。\""
keywords: 
author: robstackmsft
ms.author: robstack
nmanager: angrobe
ms.date: 06/13/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4a085264-232a-4af0-97f1-747496c44517
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ae42ab64945982fedc2d6858e2f3eca8fbed334c
ms.sourcegitcommit: 3b21f20108e2bf1cf47c141b36a7bdae609c4ec3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2017
---
# <a name="introduction-to-microsoft-intune-in-the-azure-portal"></a>Azure Portal での Microsoft Intune の概要


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Microsoft Intune は Azure Portal に含まれるようになり、これまで使い慣れたワークフローと機能は変更されました。
新しいポータルでは、Azure Portal の新機能と更新された機能が提供されており、組織のモバイル デバイス、PC、アプリを管理できます。

> [!IMPORTANT]
> **新しいポータルがまだ表示されない場合**<br>
> 既存のテナントは、新しいエクスペリエンスに移行中です。 お使いのテナントが移行される前に、Office メッセージ センターに通知が表示されます。
>
> 2017 年 1 月より前に作成された Intune アカウントの場合は、Apple Enrollment ワークフローが Azure で利用可能になる前に一度移行する必要があります。 移行のスケジュールはまだ発表されていません。 既存のアカウントで Azure Portal にアクセスできない場合は、試用アカウントを作成することをお勧めします。
>
> 潜在的な障壁の一覧については次のページをご覧ください: https://blogs.technet.microsoft.com/intunesupport/2017/05/17/intune-migration-blockers-for-grouping-targeting/


このライブラリでは新しいポータルに関する情報を参照でき、情報は継続的に更新されます。 内容についてご提案がございましたら、トピックのコメント欄にフィードバックをお寄せください。 ご意見をお待ちしております。

新しいエクスペリエンスの概要を以下に示します。

- すべての Enterprise Mobility + Security (EMS) コンポーネント用の統合コンソール
- Web 標準に基づく HTML ベースのコンソール
- 多数のアクションを自動化するために Microsoft Graph API をサポート
- Azure Active Directory (AD) グループによってすべての Azure アプリケーション間での互換性を提供
- 最新の Web ブラウザーの大部分に対応

クラシック Intune コンソールに関するドキュメントをお探しの場合は、[Intune ドキュメント ライブラリ](https://docs.microsoft.com/intune-classic/)を参照してください。

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
このセクションでは、Intune の使用開始にあたって役に立つ[概要情報](introduction-intune.md)について説明します。
### <a name="plan-and-design"></a>計画と設計
Intune 環境の[計画と設計](/intune-classic/plan-design/introduction)に役立つ情報が含まれています。
### <a name="device-enrollment"></a>デバイスの登録
[デバイスを Intune の管理対象にする方法](device-enrollment.md)。
### <a name="device-compliance"></a>デバイスのポリシー準拠
[デバイスのコンプライアンス レベルを定義し、準拠していないデバイスをレポートします](device-compliance.md)。
### <a name="device-configuration"></a>デバイス構成
[管理対象のデバイスで設定と機能を構成するために使用できるプロファイルについて理解します](device-profiles.md)。
### <a name="devices"></a>[デバイス]
[インベントリとレポートによって管理対象デバイスの情報を把握します](device-management.md)。
### <a name="mobile-apps"></a>モバイル アプリ
[アプリの発行、管理、構成、および保護方法](app-management.md)。
### <a name="conditional-access"></a>条件付きアクセス
[指定した条件に応じて Exchange サービスへのアクセスを制限します](conditional-access.md)。
### <a name="on-premises-access"></a>オンプレミスのアクセス
[Exchange ActiveSync および Exchange On-premises へのアクセスを構成します](/intune-classic/deploy-use/mobile-device-management-with-exchange-activesync-and-microsoft-intune)
### <a name="users"></a>Users
[リソースを管理し、グループに分類するデバイスのユーザーについて](users-add.md)説明します。
### <a name="groups"></a>[グループ]
[Intune で Azure Active Directory グループを使用する方法について説明します](groups-get-started.md)
### <a name="intune-roles"></a>Intune ロール
[Intune の各種アクションを実行できるユーザーと、それらのアクションの適用先となるユーザーを制御します](role-based-access-control.md)。 一般的な Intune シナリオを対象とする組み込みロールを使用するか、独自のロールを作成することができます。
### <a name="software-updates"></a>ソフトウェア更新プログラム
[Windows 10 デバイスのソフトウェア更新を構成する方法について説明します](windows-update-for-business-configure.md)。



## <a name="whats-new"></a>新機能

[Intune の新機能をご確認ください](whats-new.md)。
