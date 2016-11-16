---
title: "データ暗号化で会社のデータを保護する | Microsoft Intune"
description: "このガイドでは、モバイル アプリでポリシーを使用してパスコードとデータ暗号化を強制することによりデータ損失から会社を保護する方法を説明します。"
keywords: "暗号化, PIN, データ"
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 10/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b1e84ef8-a260-4e3d-aaf1-8b3facfecafa
ms.reviewer: pchacon
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b7d4f7d48e14a7d4f6a19cf3c459406ce241647a
ms.openlocfilehash: 0dd683017028dc594fc2326df7f8592c706843a2


---

# クイック スタート ガイド: データの暗号化により会社のデータを保護する
Microsoft Intune は、次のようなさまざまな方法で Office モバイル アプリからデータ損失を防ぐのに役立ちます。
- IOS および Android で提供される最高レベルのデバイス暗号化で企業のデータを暗号化。
- プライバシーや法的要件のためにモバイル デバイス管理ソリューションに登録できない IOS および Android デバイス。

Microsoft Intune は、iOS または Android モバイル デバイスを完全なモバイル デバイス管理に登録することなく Office モバイル アプリからのデータ損失を回避して Office 365 (O365) データを保護するのにも役立ちます。 管理対象モバイル デバイスにサード パーティ製のモバイル デバイス管理ソリューションを使用している場合でも同じです。 

## このクイック スタート ガイドの対象読者
次の前提条件を満たしている場合、このクイック スタート ガイドは適切なリソースです。
- O365 ライセンスを既に使用しているか、使用するために入手してあり、Office モバイル アプリを管理している。
- IOS または Android で Office モバイル アプリを使用する予定である。 
- Microsoft または Microsoft 以外の何らかのモバイル デバイス管理ソリューションを使用している。 法的な規則のためにモバイル デバイス管理ソリューションを使用できない場合は、このガイドを使用できます。 

> [!NOTE] 
> Windows は、まだ Office モバイル アプリに対してサポートされているプラットフォームではありません。 登録不要のモバイル アプリケーション管理は、まだオンプレミスの Exchange または SharePoint と互換性がありません。 保護できるのはオンライン バージョンでホストされているデータだけです。

このガイドでは、デバイス管理ソリューションへの完全な登録を必要とせずに、機密データにアクセスするために従業員が使用しているモバイル アプリでポリシーを使用してパスコードとデータ暗号化を強制することにより、データ損失から会社を保護する方法を説明します。 Microsoft Intune では、[iOS](https://products.office.com/en-us/mobile/office-mobile-apps-for-ios) および [Android](https://products.office.com/en-us/mobile/office-mobile-apps-for-android) 用の Office モバイル アプリにモバイル アプリケーション管理 (MAM) ポリシーを設定できます。 これにより、モバイル デバイス管理ソリューションへのデバイスの登録をユーザーに要求しなくても O365 のデータを保護することができ、Office モバイル アプリの優れたエンド ユーザー エクスペリエンスを維持できます。 

## 実行方法
1.  [アプリ データを保護する方法を確認する](/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune) 
2.  [Get ready to configure mobile app management policies (モバイル アプリ管理ポリシーの展開)](/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune) 
3.  [モバイル アプリ管理ポリシーの作成および展開](/intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune) 

## 追加情報:
- [Microsoft Intune での MAM 対応アプリのエンド ユーザー エクスペリエンスについて確認します。](/intune/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune)
- [Microsoft Intune によるモバイル アプリケーション管理のためにアプリを準備する方法を決めます。](/intune/deploy-use/decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune)
- [Microsoft Intune アプリケーション パートナー一覧を見ます。](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-partners)



<!--HONumber=Oct16_HO3-->


