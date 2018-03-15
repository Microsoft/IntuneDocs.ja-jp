---
title: "Azure Portal での Intune の概要"
titlesuffix: 
description: "Microsoft Intune は、Azure Portal で使用できます。 Azure Portal での Intune の概要について説明します。"
keywords: 
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 02/28/2018
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4a085264-232a-4af0-97f1-747496c44517
ms.suite: ems
ms.custom: 
ms.openlocfilehash: c9c8485a3ab68be745c8903659df0fd35af2a644
ms.sourcegitcommit: aafed032492c1b5861d7097a335f9bbb29ce3221
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/02/2018
---
# <a name="introduction-to-microsoft-intune-in-the-azure-portal"></a>Azure Portal での Microsoft Intune の概要


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

他の Azure サービスと同様に、Microsoft Intune は Azure Portal で使用できます。 Azure Portal で **[Intune]** を選択すると、組織のモバイル デバイス、PC、およびアプリを管理することができます。

>[!NOTE] 
> 以前のバージョンの Microsoft Intune を使用している場合は、次の情報が役立ちます。
    * [Azure での Intune の機能の移動先](ui-changes.md)は、Azure への移行で変更された特定のワークフローと UI を示すリファレンスです。
    * [Azure Portal での Intune クラシック グループ](groups-get-started.md)は、グループを管理するための Azure Active Directory セキュリティ グループへの切り替えの影響について説明します。

Azure Portal での Microsoft Intune のエクスペリエンスの概要を以下に示します。

- すべての Enterprise Mobility + Security (EMS) コンポーネント用の統合コンソール
- Web 標準に基づく HTML ベースのコンソール
- 多数のアクションを自動化するために Microsoft Graph API をサポート
- Azure Active Directory (AD) グループによってすべての Azure アプリケーション間での互換性を提供
- 最新の Web ブラウザーの大部分に対応

## <a name="before-you-start"></a>開始する前に

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

## <a name="microsoft-intune-in-the-azure-portal"></a>Azure Portal の Microsoft Intune

[Azure Portal](https://portal.azure.com) は、Microsoft Intune サービスのある場所です。 Azure には複数のサービスがありますが、その多くはおそらく、日常的に使用されることがありません。 ポータルのエクスペリエンスをカスタマイズするクイック ガイドについては、「[Azure Portal で Intune を始める](get-started-azure.md)」を参照してください。

## <a name="the-microsoft-intune-documentation"></a>Microsoft Intune のドキュメント

このトピック、および Microsoft Intune のドキュメント セット全体は、継続的に更新されています。 内容についてご提案がございましたら、トピックのコメント欄にフィードバックをお寄せください。 ご意見をお待ちしております。

必要な情報を見つけやすくするため、ドキュメントには Azure Portal での Microsoft Intune のレイアウト (下図参照) が反映されています。

![Azure Portal のワークロード](./media/azure-portal-workloads.png)

### <a name="documentation-guide"></a>ドキュメント ガイド

次の表を使用して、Microsoft Intune の主要な領域をすばやく検索して、理解してください。

| セクション                                                      | 説明                                                                                                                                                                                                                                                                                      |
|--------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [概要と作業開始](introduction-intune.md)       | 以下を含む Intune の基礎を理解します。<br /> - 一般的なソリューション<br /> - Microsoft Intune のしくみ<br /> - Intune でのデバイス管理<br /> - Intune でのアプリ管理<br /> - デバイス登録を使用したまたは使用しないエンタープライズ モビリティ管理 (EMM)                                                         |
| [計画と設計](planning-guide.md)                         | Microsoft Intune 環境の計画と設計を成功させるために役立つガイダンスです。                                                                                                                                                                                                             |
| [デバイスの登録](device-enrollment.md)                    | Intune サービスにデバイスを登録することで、Microsoft Intune が従業員のデバイスの管理にどのように役立つかを理解します。 従業員のデバイスを登録する方法は複数あります。                                                                                                         |
| [デバイスのポリシー準拠](device-compliance.md)                    | Intune のデバイス コンプライアンス ポリシーは、デバイスが Microsoft Intune によって "準拠している" と見なされるために遵守する必要がある規則および設定を定義します。 たとえば、デバイス アクセスにパスワードを要求したり、最小 OS バージョンを要求することは、すべてコンプライアンスの例です。 |
| [デバイス構成](device-profiles.md)                   | デバイス プロファイルを作成することで、Microsoft Intune を使用して管理するすべてのデバイスに対して、設定と機能を構成します。 たとえば、通知、データの共有、電子メールのサポート、Wi-Fi 接続、証明書、および Endpoint Protection などの機能を構成できます。              |
| [デバイス](device-management.md)                              | データをリスクから保護しながら、エンド ユーザーが作業するために必要なリソースが、管理するデバイスから確実に提供されるようにします。 従業員のデバイスのインベントリを確認し、リモート デバイスの操作を実行して、デバイスを管理します。                                                      |
| [モバイル アプリ](app-management.md)                             | アプリの追加、展開、監視、構成、および保護の方法を理解します。                                                                                                                                                                                                                             |
| [条件付きアクセス](conditional-access.md)                  | 会社のデータへのアクセスを制限する、デバイスベースおよびアプリベースの条件を定義します。                                                                                                                                                                                                            |
| [ユーザー](users-add.md)                                        | 管理するデバイスおよびアプリのユーザーを追加する方法を説明します。                                                                                                                                                                                                                                           |
| [グループ](groups-get-started.md)                              | Intune を使用したグループの作成方法と管理方法について説明します。 グループを使用すると、デバイスとアプリの構成と保護ポリシーをすばやく割り当てることができます。                                                                                                                                             |
| [Intune ロール](role-based-access-control.md)                 | Intune の各種アクションを実行できるユーザーの制御方法と、それらのアクションの適用方法について説明します。 一般的な Intune シナリオを対象とする組み込みロールを使用するか、独自のロールを作成することができます。                                                                                 |
| [ソフトウェア更新プログラム](windows-update-for-business-configure.md) | Windows 10 デバイスのソフトウェア更新を構成する方法について説明します。                                                                                                                                                                                                                                  |

## <a name="whats-new"></a>新機能

Microsoft Intune の最新機能については、「[Microsoft Intune の新機能](whats-new.md)」を参照してください。
