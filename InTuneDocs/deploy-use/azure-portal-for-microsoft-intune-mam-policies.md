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
translationtype: Human Translation
ms.sourcegitcommit: 9e208608d50c9b5f7fe66743de0d3c7e741dbfbd
ms.openlocfilehash: 423f525be6ff9fb72542af46ff18a57d00d04d79


---

# <a name="azure-portal-for-microsoft-intune-mam-policies"></a>Azure ポータルの Microsoft Intune MAM ポリシー対応

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

## <a name="use-the-azure-portal"></a>Azure ポータルを使用する
Azure ポータルでは、モバイル アプリ管理ポリシー (MAM) を作成して管理できます。

Azure ポータルでは、次の MAM ポリシーの作成をサポートしています。
- **Intune で登録および管理されている**デバイスで実行中のアプリ

- どの MDM ソリューションにも**登録していない**デバイスで実行中のアプリ
- **サード パーティの MDM ソリューションに登録済み**のデバイスで実行中のアプリ

>[!IMPORTANT]


> Intune 管理コンソールを使用してデバイスを管理している場合は、Intune に登録済みのデバイスのアプリをサポートする MAM ポリシーを [Intune 管理コンソール](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md)を使用して作成できます。

> Intune 管理コンソールでは、MAM ポリシー設定の一部が表示されない可能性があります。 Azure ポータルは MAM ポリシーを作成するための新しい管理コンソールです。 Intune 管理コンソールと Azure ポータルの両方で MAM ポリシーを作成した場合、Azure ポータルのポリシーがアプリに適用され、ユーザーに展開されます。


## <a name="sign-in-to-the-azure-portal-and-customize-your-start-page"></a>Azure ポータルにサインインし、スタート ページをカスタマイズする

1.  [Azure ポータル](https://portal.azure.com)に移動し、[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 資格情報でサインインします。

    ![Azure ポータルのサインイン ページのスクリーンショット](../media/AppManagement/AzurePortal_MAMSigninPage.png)

2.  正常にサインインすると、**ダッシュボード**が開きます。 **ダッシュボード** ページはカスタマイズできます。

    ![Azure ポータルのダッシュボードのスクリーンショット](../media/AppManagement/AzurePortal_MAMStartboard_NoMAM.png)

3.  **[参照]** メニューで、**[Intune]** を探します。![[Intune] が強調表示されている [参照] メニューのスクリーンショット](../media/AppManagement/AzurePortal_MAM_Browse_Intune.png)

4.  **[Intune]** > **[Intune モバイル アプリケーション管理]** > **[設定]** の順に選択します。

    ![[Intune モバイル アプリケーション管理] ブレードのスクリーンショット](../media/AppManagement/AzurePortal_MAM_Mainblade.png)

    > [!TIP]

    > ブレードを **[開始]** ページにピン留めするには、ブレードの **[ピン留め]** オプションを使用できます。 **[Intune モバイル アプリケーション管理ブレード]**のピン アイコンをクリックして、そのブレードを **[開始]** ページにピン留めします。

    ![ピン アイコンが強調表示されている [Intune モバイル アプリケーション管理] ブレードのスクリーンショット](../media/AppManagement/AzurePortal_MAM_PinBladeAction.png)

    ![Intune タイルが固定されているダッシュボードのスクリーンショット](../media/AppManagement/AzurePortal_MAM_Startboard_withMAM.png)
## <a name="next-steps"></a>次のステップ
[モバイル アプリ管理ポリシーの作成と展開](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Dec16_HO3-->


