---
title: "Azure ポータルの MAM ポリシー対応 | Microsoft Docs"
description: "Azure ポータルを使用してモバイル アプリ管理ポリシーを作成します。 ここで作成したポリシーは、Intune に登録されているデバイスにも未登録のデバイスにも適用できます。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 10/22/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7d6dae94-a833-40b7-9016-14ea234bb33c
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 2b064d14e8a46c19c0eafc3276b470dead114438
ms.openlocfilehash: e7fd0a83e21d499da39bd65502d8981bc3b1f61c
ms.contentlocale: ja-jp
ms.lasthandoff: 05/06/2017


---

# <a name="azure-portal-for-intune-app-protection-policies"></a>Intune アプリ保護ポリシーの Azure ポータル

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Azure ポータルを使用して、次のようなアプリに対してアプリ保護ポリシー作成して管理できます。

- **Intune で登録および管理されている**デバイスで実行中のアプリ

- どの MDM ソリューションにも**登録していない**デバイスで実行中のアプリ
- **サード パーティの MDM ソリューションに登録済み**のデバイスで実行中のアプリ

>[!IMPORTANT]
> Azure ポータルはアプリ保護ポリシーを作成するための新しい管理コンソールです。ただし、MDM シナリオの [Intune 管理コンソール](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md)を利用し、Intune に登録したデバイスのアプリをサポートするアプリ保護ポリシーを作成することもできます。

> Intune 管理コンソールでは、アプリ保護ポリシー設定の一部が利用できない可能性があります。 また、Intune 管理コンソールと Azure ポータルの両方でアプリ保護ポリシーを作成した場合、Azure ポータルで作成されたポリシーは、Intune 管理コンソールで作成されたポリシーに優先します。 このシナリオでは、Azure ポータルアプリ保護ポリシーはアプリに適用され、ユーザーにデプロイされます。


## <a name="sign-in-to-the-azure-portal-and-customize-your-start-page"></a>Azure ポータルにサインインし、スタート ページをカスタマイズする

1.  [Azure Portal](https://portal.azure.com) に移動し、Intune 資格情報でサインインします。

    ![Azure ポータルのサインイン ページのスクリーンショット](../media/AppManagement/AzurePortal_MAMSigninPage.png)

2.  正常にサインインすると、**ダッシュボード**が開きます。 **ダッシュボード** ページはカスタマイズできます。

    ![Azure ポータルのダッシュボードのスクリーンショット](../media/AppManagement/AzurePortal_MAMStartboard_NoMAM.png)

3.  左側のメニューから **[その他のサービス]** を選択し、テキスト ボックス フィルターに「**Intune**」と入力します。

    ![[参照] メニューのスクリーンショット、[Intune] が強調表示されています](../media/AppManagement/MAM-Azure-Portal-1.png)

4.  **[Intune アプリ保護]** > **[Intune モバイル アプリケーション管理]** > **[すべての設定]** の順に選択します。

    ![[Intune モバイル アプリケーション管理] ブレードのスクリーンショット](../media/AppManagement/MAM-Azure-Portal-2.png)

5. (任意): ブレードを **[開始]** ページにピン留めするには、ブレードの **[ピン留め]** オプションを使用できます。 **[Intune モバイル アプリケーション管理ブレード]**のピン アイコンをクリックして、そのブレードを **[開始]** ページにピン留めします。

    ![ピン アイコンが強調表示されている [Intune モバイル アプリケーション管理] ブレードのスクリーンショット](../media/AppManagement/AzurePortal_MAM_PinBladeAction.png)

    ![Intune タイルが固定されているダッシュボードのスクリーンショット](../media/AppManagement/AzurePortal_MAM_Startboard_withMAM.png)

## <a name="next-steps"></a>次のステップ
[アプリ保護ポリシーを構成する準備をする](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)

