---
title: "データ暗号化で会社のデータを保護する"
description: "このガイドでは、モバイル アプリでポリシーを使用してパスコードとデータ暗号化を強制することによりデータ損失から会社を保護する方法を説明します。"
keywords: "暗号化, PIN, データ"
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 11/22/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b1e84ef8-a260-4e3d-aaf1-8b3facfecafa
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: pchacon
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f6e61015883d4c747b5a433c349501b81671a17f
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/10/2017
---
# <a name="quick-start-guide-protect-company-data-with-data-encryption"></a>クイック スタート ガイド: データの暗号化により会社のデータを保護する

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune は、次のようなさまざまな方法で Office モバイル アプリからデータ損失を防ぐのに役立ちます。
- IOS および Android で提供される最高レベルのデバイス暗号化で企業のデータを暗号化。
- プライバシーや法的要件のためにモバイル デバイス管理ソリューションに登録できない IOS および Android デバイス。

Microsoft Intune は、iOS または Android モバイル デバイスを完全なモバイル デバイス管理に登録することなく Office モバイル アプリからのデータ損失を回避して Office 365 (O365) データを保護するのにも役立ちます。 管理対象モバイル デバイスにサード パーティ製のモバイル デバイス管理ソリューションを使用している場合でも同じです。

## <a name="is-this-quick-start-guide-right-for-me"></a>このクイック スタート ガイドの対象読者
次の前提条件を満たしている場合、このクイック スタート ガイドは適切なリソースです。
- O365 ライセンスを既に使用しているか、使用するために入手してあり、Office モバイル アプリを管理している。
- IOS または Android で Office モバイル アプリを使用する予定である。
- Microsoft または Microsoft 以外の何らかのモバイル デバイス管理ソリューションを使用している。 法的な規則のためにモバイル デバイス管理ソリューションを使用できない場合は、このガイドを使用できます。

> [!NOTE]
> Windows は、まだ Office モバイル アプリに対してサポートされているプラットフォームではありません。 登録不要のモバイル アプリケーション管理は、まだオンプレミスの Exchange または SharePoint と互換性がありません。 保護できるのはオンライン バージョンでホストされているデータだけです。

このガイドでは、デバイス管理ソリューションへの完全な登録を必要とせずに、機密データにアクセスするために従業員が使用しているモバイル アプリでポリシーを使用してパスコードとデータ暗号化を強制することにより、データ損失から会社を保護する方法を説明します。 Microsoft Intune では、[iOS](https://products.office.com/mobile/office-mobile-apps-for-ios) および [Android](https://products.office.com/mobile/office-mobile-apps-for-android) 用の Office モバイル アプリにモバイル アプリケーション管理 (MAM) ポリシーを設定できます。 これにより、モバイル デバイス管理ソリューションへのデバイスの登録をユーザーに要求しなくても O365 のデータを保護することができ、Office モバイル アプリの優れたエンド ユーザー エクスペリエンスを維持できます。

## <a name="how-do-i-do-it"></a>実行方法
1.  [アプリ データを保護する方法を確認する](/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)
2.  [モバイル アプリ管理ポリシーを構成する準備](/intune-classic/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune)
3.  [モバイル アプリ管理ポリシーの作成および展開](/intune-classic/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune)

## <a name="additional-information"></a>追加情報:
- [Microsoft Intune での MAM 対応アプリのエンド ユーザー エクスペリエンスについて確認します。](/intune-classic/eploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune)
- [Microsoft Intune によるモバイル アプリケーション管理のためにアプリを準備する方法を決めます。](/intune/apps-prepare-mobile-application-management)
- [Microsoft Intune アプリケーション パートナー一覧を確認します。](https://www.microsoft.com/cloud-platform/microsoft-intune-partners)
