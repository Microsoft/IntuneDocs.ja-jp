---
title: 開発中 - Microsoft Intune
titleSuffix: ''
description: Microsoft Intune の開発中の機能
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/29/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: ca66a2fa331fe4dcc30c32d369db32a57ba9999c
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66047309"
---
# <a name="in-development-for-microsoft-intune---may-2019"></a>開発中の Microsoft Intune - May 2019 年 5 月

お客様による準備と計画を支援するため、このページには Intune の UI の更新と、開発中でまだリリースされていない機能がリストされています。 さらに

- お客様による変更前の対処が必要であると予測される場合は、補足の Office メッセージ センター投稿を公開します。
- 機能が運用環境でプレビューまたは一般公開としてリリースされると、機能の説明はこのページから[新機能ページ](whats-new.md)に移されます。
- このページと[新機能ページ](whats-new.md)は定期的に更新されます。 適宜確認してください。
- 戦略的成果物とタイムラインについては、[Microsoft 365 のロードマップ](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS)を参照してください。

> [!Note]
> これらの項目には、将来のリリースで導入される Intune の機能に関する Microsoft の現在の予測が反映されています。 日付と個々の機能は変更されることがあります。 すべての開発中の項目について、このページに機能の説明があるわけではりません。

**RSS フィード**: ご自身のフィード リーダーに次の URL をコピーして貼り付けることで、このページの更新時に通知を受け取ることができます。`https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Azure Portal での Intune


<!-- 1905 start-->


### <a name="baseline-support-for-keyword-search-----3082036-----------"></a>キーワード検索のベースライン サポート  <!-- 3082036         -->
まもなく、セキュリティのベースライン プロファイルを作成または編集中、コンソールに表示される設定をフィルター処理するために "*検索*" を使用できるようになります。   

### <a name="reset-and-wipe-devices-in-bulk-by-using-the-graph-api----3295288---"></a>Graph API を使用してデバイスを一括でリセットおよびワイプする <!-- 3295288 -->
Graph API を使用して 100 台までのデバイスを一括でリセットおよびワイプできるようになります。

<!-- 1904 start-->

### <a name="device-users-can-view-all-managed-apps-theyve-installed-or-tried-to-install----2352913---"></a>デバイスのユーザーは、インストール済みまたはインストールしようとしたすべての管理対象アプリを表示できる <!-- 2352913 -->
Windows 用ポータル サイトに、ユーザーのデバイスにインストールされている、必須および使用可能両方のすべての管理対象アプリがリストされます。 ユーザーは、試行した、および保留中のアプリのインストールと、それらの現在の状態を表示することができるようになります。 組織でアプリが必須または使用可能とされていない場合、会社のアプリは全くインストールされていないというメッセージがユーザーに表示されます。 ユーザーはまた、インストールの状態でアプリを並べ替えまたはフィルタリングすることができます。

### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910---"></a>Windows 10 デバイス構成プロファイルを作成するときは "適用規則" を使用する <!-- 2549910 -->
Windows 10 デバイス構成プロファイルを作成します ( **[デバイスの構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  >  **[Windows 10]** (プラットフォーム))。 **適用規則**を作成し、プロファイルが特定のエディションまたは特定のバージョンにのみ適用されるようにすることができます。 たとえば、いくつかの BitLocker 設定を有効にするプロファイルを作成します。 プロファイルを追加したら、適用規則を使用して Windows 10 Enterprise を実行しているデバイスにのみプロファイルを適用します。

適用対象: 
- Windows 10 以降



## <a name="notices"></a>通知

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

### <a name="see-also"></a>関連項目
最近の開発状況について詳しくは、「[Microsoft Intune の新機能](whats-new.md)」をご覧ください。


