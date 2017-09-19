---
title: "アプリのライフサイクルの概要"
description: "追加から最終的な提供終了までの、Intune 管理対象アプリのライフサイクルについて説明します。"
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 06/07/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 60347012-bc3f-4b9a-a4f4-6d3c5021a6e6
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 01648e20704c9cfc0121ded3b95d99e4661f4f53
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2017
---
# <a name="overview-of-the-app-lifecycle"></a>アプリのライフサイクルの概要

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

Intune のアプリのライフサイクルは、アプリが追加されると開始し、アプリを削除するまで以降のフェーズに従って進行します。

![アプリのライフサイクル](./media/app-lifecycle.png "Intune アプリのライフサイクル")

## <a name="add"></a>追加

アプリ展開の最初のステップは、管理と割り当てを行うアプリを Intune に追加することです。 使用できるアプリの種類はさまざまですが、基本的な手順は同じです。 Intune では、[登録されたデバイス](apps-add.md) ([クラシック ポータル](/intune-classic/deploy-use/add-apps-for-mobile-devices-in-microsoft-intune)) と、[Intune クライアント ソフトウェアで管理する Windows PC](/intune-classic/deploy-use/add-apps-for-windows-pcs-in-microsoft-intune) の両方に、アプリを追加できます。

## <a name="deploy"></a>デプロイ

Intune にアプリを追加したら、[それを管理対象のユーザーとデバイスに割り当てる](apps-deploy.md)ことができます ([クラシック ポータル](/intune-classic/deploy-use/deploy-apps))。 Intune を使用すればこのプロセスは簡単になり、アプリを展開した後は、Intune 管理コンソールから展開が[成功したことを監視](apps-monitor.md) ([クラシック ポータル](/intune-classic/deploy-use/monitor-apps-in-microsoft-intune)) できます。 さらに、[Apple](vpp-apps-ios.md) ([クラシック ポータル](/intune-classic/deploy-use/manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune)) や [Windows](windows-store-for-business.md) ([クラシック ポータル](/intune-classic/deploy-use/manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune)) アプリ ストアといった一部のアプリ ストアでは、会社用にアプリのライセンスを一括購入できます。 Intune では、これらのストアとデータを同期して、Intune 管理コンソールからこの種のアプリのライセンスを展開して使用状況を追跡できます。

## <a name="configure"></a>構成

アプリのライフサイクルの一環として、アプリの新しいバージョンが定期的にリリースされます。 Intune には、展開した[アプリを新しいバージョンに簡単に更新](apps-add.md) ([クラシック ポータル](/intune-classic/deploy-use/update-apps-using-microsoft-intune)) できるツールがあります。 さらに、一部のアプリでは次のような追加機能を構成できます。
- [iOS アプリ構成ポリシー](app-configuration-policies-use-ios.md) ([クラシック ポータル](/intune-classic/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune)) には、互換性のある iOS アプリの設定があり、そのアプリの実行時に使用されます。 たとえば、アプリには特定のブランド設定や、接続するサーバーの名前が必要な場合があります。
- [管理対象ブラウザー ポリシー](app-configuration-managed-browser.md) ([クラシック ポータル](/intune-classic/deploy-use/manage-internet-access-using-managed-browser-policies)) では、Intune 管理ブラウザーの設定を構成して、デバイスの既定ブラウザーを置き換えたりユーザーがアクセスできる Web サイトを制限したりできます。

## <a name="protect"></a>保護

Intune では、さまざまな方法でアプリのデータを保護できます。 主な方法は次のとおりです。
- [条件付きアクセス](conditional-access.md) ([クラシック ポータル](/intune-classic/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune)) は、指定した条件に基づいてメールと他のサービスへのアクセスを制御します。 条件としては、デバイスの種類や、展開した[デバイス コンプライアンス ポリシー](device-compliance.md) ([クラシック ポータル](/intune-classic/deploy-use/introduction-to-device-compliance-policies-in-microsoft-intune)) へのコンプライアンスなどがあります。
- [アプリ保護ポリシー](app-protection-policy.md) ([クラシック ポータル](/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)) は、個々のアプリと連携して、アプリが使用する会社のデータを保護します。 たとえば、管理対象外アプリと管理対象アプリの間でのデータのコピーを制限したり、脱獄またはルート化されたデバイスでのアプリの実行を禁止したりできます。

## <a name="retire"></a>インベントリから削除

通常は、最終的に、展開したアプリは古くなり、削除する必要があります。 Intune では、簡単に[サービスからアプリを削除](device-management.md) ([クラシック ポータル](/intune-classic/deploy-use/retire-apps-using-microsoft-intune)) できます。
