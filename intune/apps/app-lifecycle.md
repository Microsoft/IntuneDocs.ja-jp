---
title: Microsoft Intune のアプリ ライフサイクルの概要
description: Microsoft Intune で管理するアプリのライフ サイクルについて説明します。 アプリのライフ サイクルには、アプリの追加、配置、構成、保護、削除があります。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/27/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 60347012-bc3f-4b9a-a4f4-6d3c5021a6e6
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: apps; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 569906cea8467d568d302f4e44b26c3394213b62
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/17/2020
ms.locfileid: "77414978"
---
# <a name="overview-of-the-app-lifecycle-in-microsoft-intune"></a>Microsoft Intune のアプリ ライフサイクルの概要

Microsoft Intune のアプリ ライフサイクルは、アプリが追加されると開始し、アプリを削除するまで以降のフェーズに従って進行します。 各フェーズを理解することで、Intune でアプリ管理を始めるために必要な知識が得られます。

![アプリのライフサイクル - 追加、展開、構成、保護、インベントリから削除。](./media/app-lifecycle/app-lifecycle.png "Intune アプリのライフサイクル")

## <a name="add"></a>追加

アプリ展開の最初のステップは、管理と割り当てを行うアプリを Intune に追加することです。 使用できるアプリの種類はさまざまですが、基本的な手順は同じです。 Intune では、社内で開発されたアプリ (基幹業務)、ストアから入手したアプリ、組み込みアプリ、Web 上のアプリなど、さまざま種類のアプリを追加できます。 アプリの種類については、「[アプリを Microsoft Intune に追加する方法](apps-add.md)」を参照してください。

## <a name="deploy"></a>デプロイ

Intune にアプリを追加したら、[それを管理対象のユーザーとデバイスに割り当てる](apps-deploy.md)ことができます。 Intune でこのプロセスが簡単になります。アプリを展開した後、Azure portal 内の Intune から展開の[成功を監視](apps-monitor.md)できます。 さらに、[Apple](vpp-apps-ios.md) や [Windows](windows-store-for-business.md) アプリ ストアなどの一部のアプリ ストアでは、会社用にアプリのライセンスを一括購入できます。 Intune では、これらのストアとデータを同期して、Intune 管理コンソールからこの種のアプリのライセンスを展開して使用状況を追跡できます。

## <a name="configure"></a>構成

アプリのライフサイクルの一環として、アプリの新しいバージョンが定期的にリリースされます。 Intune には、展開した[アプリを新しいバージョンに簡単に更新](apps-add.md)できるツールがあります。 さらに、一部のアプリでは次のような追加機能を構成できます。

- [iOS アプリ構成ポリシー](app-configuration-policies-use-ios.md)では、アプリの実行時に使用される互換性のある iOS/iPadOS アプリの設定を指定できます。 たとえば、アプリには特定のブランド設定や、接続するサーバーの名前が必要な場合があります。
- [Managed Browser ポリシー](app-configuration-managed-browser.md)を使って [Microsoft Edge](~/apps/apps-supported-intune-apps.md#microsoft-apps) の設定を構成することができます。これにより、既定のデバイス ブラウザーを置き換え、ユーザーがアクセスできる Web サイトを制限できます。

## <a name="protect"></a>保護

Intune では、さまざまな方法でアプリのデータを保護できます。 主な方法は次のとおりです。

- [条件付きアクセス](../protect/conditional-access.md)では、ユーザーが指定した条件に基づいて、メールや他のサービスへのアクセスが制御されます。 条件としては、デバイスの種類や、ユーザーが展開した[デバイス コンプライアンス ポリシー](../protect/device-compliance-get-started.md)への準拠などがあります。
- [アプリ保護ポリシー](app-protection-policy.md)は、個々のアプリと連携して、アプリが使用する会社のデータを保護します。 たとえば、管理対象外アプリと管理対象アプリの間でのデータのコピーを制限したり、脱獄またはルート化されたデバイスでのアプリの実行を禁止したりできます。

## <a name="retire"></a>インベントリから削除

通常は、最終的に、展開したアプリは古くなり、削除する必要があります。 Intune では、簡単に[サービスからアプリを削除](../remote-actions/device-management.md)できます。

## <a name="next-steps"></a>次のステップ

- [Microsoft Intune のアプリ管理](app-management.md)について学習する
