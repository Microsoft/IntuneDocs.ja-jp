---
title: "ポリシーとアプリを展開する"
description: "ポリシー設定を有効にし、デバイスが管理に登録されたらすぐに適用されるアプリを展開することができます。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/14/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e0d8e98f-7dd8-4cbf-887c-a9af63ffe970
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: cf86d82fe636d2641f82ca951e508bea93abf683
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2017
---
# <a name="create-policies-and-publish-apps"></a>ポリシーを作成してアプリを発行する

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

このトピックでは、Intune 管理者がポリシーを作成し、アプリを発行した後、管理対象デバイスにデプロイする方法を説明します。

Intune へのアプリの登録を開始する前に、ポリシー設定とアプリを有効にします。アプリは、デバイスが管理対象になるとすぐに展開されます。 モバイル デバイスのセキュリティ設定を制御したり、コンピューターの Windows ファイアウォールや Endpoint Protection の設定を管理したり、アプリケーションを展開したりする作業は、Intune のポリシー設定を使用して効率的に行うことができます。 ポリシーを構成し、アプリを追加して展開し、Intune に登録されたらすぐにデバイスが設定とアプリを受信するようにすることができます。

ポリシーとアプリはプラットフォームに固有です。

## <a name="manage-device-settings"></a>デバイス設定の管理

 デバイス ポリシー設定は、プラットフォームごとに構成され、管理されます。 次のリンクは、それぞれのプラットフォームで使用できる設定の一覧を提供します。

- [iOS](/intune-classic/deploy-use/ios-policy-settings-in-microsoft-intune)
- [Android および Samsung KNOX Standard](/intune-classic/deploy-use/android-policy-settings-in-microsoft-intune)
- [Android for Work](/intune-classic/deploy-use/android-for-work-policy-settings-in-microsoft-intune)
- [Windows 10 (PC とモバイル)](/intune-classic/deploy-use/windows-10-policy-settings-in-microsoft-intune)
- [Windows 8.1](/intune-classic/deploy-use/windows-configuration-policy-settings-in-microsoft-intune)
- [Windows Phone 8.1](/intune-classic/deploy-use/windows-phone-8-1-policy-settings-in-microsoft-intune)
- [Windows チーム](/intune-classic/deploy-use/windows-team-configuration-policy-settings-in-microsoft-intune)
- [Intune クライアント ソフトウェアを実行している Windows PC](/intune-classic/deploy-use/policies-to-protect-windows-pcs-in-microsoft-intune)

詳細については、「[Microsoft Intune ポリシーを使用してデバイスの設定と機能を管理する](/intune-classic/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies)」を参照してください。

## <a name="add-and-deploy-apps"></a>アプリを追加して展開する

Intune にアプリを追加した後で、次の 2 つの方法で管理対象アプリに展開することができます。
- **必須のインストール** - アプリを自動的に管理対象デバイスにインストールします。
- **利用可能なインストール** - ユーザーがデバイスにインストールするかどうかを選択できるように、Intune ポータル サイトにアプリが表示されます。

### <a name="add-apps"></a>アプリを追加する

まず、次のいずれかの方法で、アプリを Intune で使用できるようにする必要があります。
- [登録デバイスのアプリを追加する](/intune-classic/deploy-use/add-apps-for-mobile-devices-in-microsoft-intune)
- [Intune ソフトウェア クライアント PC のアプリを追加する](/intune-classic/deploy-use/add-apps-for-windows-pcs-in-microsoft-intune)

### <a name="deploy-apps"></a>アプリの展開

これで、アプリが Intune で使用できるようになりました。管理対象デバイスに展開できます。
- [デバイスにアプリを展開する](/intune-classic/deploy-use/deploy-use/deploy-apps-in-microsoft-intune)
- 以下のボリューム購入アプリを展開します。
    - [iOS - ボリューム購入プログラム](/intune-classic/deploy-use/manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune)
    - [ビジネス向け Windows ストア](/intune-classic/deploy-use/manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune)
    - [Android for Work](/intune-classic/deploy-use/android-for-work-apps)

    展開用にアプリを構成したら、[アプリを構成](/intune-classic/deploy-use/monitor-apps-in-microsoft-intune)できます。

>[!div class="step-by-step"]

>[&larr;**ユーザーとデバイスを整理する**](.\start-with-a-paid-subscription-to-microsoft-intune-step-5.md)       [**ポータル サイトをカスタマイズする** &rarr;](/intune/company-portal-customize)  
