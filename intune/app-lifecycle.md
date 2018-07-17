---
title: Microsoft Intune のアプリ ライフサイクルの概要
description: Microsoft Intune で管理するアプリのライフ サイクルについて説明します。 アプリのライフ サイクルには、アプリの追加、配置、構成、保護、削除があります。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 60347012-bc3f-4b9a-a4f4-6d3c5021a6e6
ms.reviewer: mghadial
ms.suite: ems
ms.custom: apps
ms.openlocfilehash: 69bf4b1dc85a8a17312fe78b6a17564a8a6ff642
ms.sourcegitcommit: 2198a39ae48beca5fc74316976bc3fc9db363659
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38225393"
---
# <a name="overview-of-the-app-lifecycle-in-microsoft-intune"></a>Microsoft Intune のアプリ ライフサイクルの概要

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Microsoft Intune のアプリ ライフサイクルは、アプリが追加されると開始し、アプリを削除するまで以降のフェーズに従って進行します。 各フェーズを理解することで、Intune でアプリ管理を始めるために必要な知識が得られます。

![アプリのライフサイクル](./media/app-lifecycle.png "Intune アプリのライフサイクル")

## <a name="add"></a>追加

アプリ展開の最初のステップは、管理と割り当てを行うアプリを Intune に追加することです。 使用できるアプリの種類はさまざまですが、基本的な手順は同じです。 Intune では、社内で開発されたアプリ (基幹業務)、ストアから入手したアプリ、組み込みアプリ、Web 上のアプリなど、さまざま種類のアプリを追加できます。 アプリの種類については、「[アプリを Microsoft Intune に追加する方法](apps-add.md)」を参照してください。 

## <a name="deploy"></a>[展開]

Intune にアプリを追加したら、[それを管理対象のユーザーとデバイスに割り当てる](apps-deploy.md)ことができます。 Intune でこのプロセスが簡単になります。アプリの展開後、Azure Portal 内の Intune から展開が[成功したことを監視](apps-monitor.md)できます。 さらに、[Apple](vpp-apps-ios.md) や [Windows](windows-store-for-business.md) アプリ ストアなどの一部のアプリ ストアでは、会社用にアプリのライセンスを一括購入できます。 Intune では、これらのストアとデータを同期して、Intune 管理コンソールからこの種のアプリのライセンスを展開して使用状況を追跡できます。

## <a name="configure"></a>構成

アプリのライフサイクルの一環として、アプリの新しいバージョンが定期的にリリースされます。 Intune には、展開した[アプリを新しいバージョンに簡単に更新](apps-add.md)できるツールがあります。 さらに、一部のアプリでは次のような追加機能を構成できます。
- [iOS アプリ構成ポリシー](app-configuration-policies-use-ios.md)では、アプリの実行時に使用される互換性のある iOS アプリの設定を指定できます。 たとえば、アプリには特定のブランド設定や、接続するサーバーの名前が必要な場合があります。
- 
  [管理対象ブラウザー ポリシー](app-configuration-managed-browser.md)では、デバイスの既定ブラウザーを置き換えて、ユーザーがアクセスできる Web サイトを制限できる、Intune 管理ブラウザーの設定を構成できます。

## <a name="protect"></a>保護

Intune では、さまざまな方法でアプリのデータを保護できます。 主な方法は次のとおりです。
- [条件付きアクセス](conditional-access.md)は、ユーザーが指定した条件に基づいてメールや他のサービスへのアクセスを制御します。 条件としては、デバイスの種類や、ユーザーが展開した[デバイス コンプライアンス ポリシー](device-compliance.md)への準拠などがあります。
- [アプリ保護ポリシー](app-protection-policy.md)は、個々のアプリと連携して、アプリが使用する会社のデータを保護します。 たとえば、管理対象外アプリと管理対象アプリの間でのデータのコピーを制限したり、脱獄またはルート化されたデバイスでのアプリの実行を禁止したりできます。

## <a name="retire"></a>インベントリから削除

通常は、最終的に、展開したアプリは古くなり、削除する必要があります。 Intune では、簡単に[サービスからアプリを削除](device-management.md)できます。

## <a name="next-steps"></a>次の手順

- [Microsoft Intune のアプリ管理](app-management.md)について学習する