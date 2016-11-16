---
experimental: true
experiment_id: kgremban_images_080416
title: "Microsoft Intune の概要 | Microsoft Intune"
description: "Intune が Enterprise Mobility および Security ソリューションでどのようにしてモバイル デバイスを管理するかについて説明します。"
keywords: 
author: Lindavr
ms.author: lindavr
manager: angrobe
ms.date: 08/10/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b4e778d-ac13-4c23-974f-5122f74626bc
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b3b46c1025ad0792ed4623656c878c53bd69d6cb
ms.openlocfilehash: f2f5d901ae3b6ffb298b56eef4ae593842b80cfb


---

# <a name="introduction-to-intune"></a>Intune の概要
Microsoft Intune は、Microsoft Enterprise Mobility + Security (EMS、旧称 Enterprise Mobility Suite) の管理部門です。 Enterprise Mobility とは、組織の情報を保護しつつ、従業員がデバイスで生産性を高められるようにすることです。  

EMS は、生産性、ID、アクセス制御、管理、データ保護を含む Enterprise Mobility の完全な統合スイートです。 これにより、効果的にモビリティ ソリューションを組織に展開し、運用することができます。  

![Enterprise Mobility ビジョンの画像](..\media\em-vision.png)

Intune では、モバイル デバイスとモバイル アプリを管理できます。 Intune は ID とアクセス制御のために Azure Active Directory (Azure AD)、およびデータ保護のために Azure Rights Management (Azure RMS) と密接に統合されます。  

Intune が解決に役立つ一般的なビジネス問題を次に示します。

* インターネット上のモバイル デバイスやアプリによってアクセスできるように、社内の電子メールとコラボレーション インフラストラクチャをセキュリティ保護する
* インターネット上のモバイル デバイスやアプリによって安全にアクセスできるように、Office 365 インフラストラクチャをセキュリティ保護する
* 組織が従業員に携帯電話を支給できるようにする
* 組織がタスク ワーカーに "共有デバイス" の制限付き利用を提供できるようにする
* 組織がセキュリティで保護された "Bring Your Own Device (BYOD)" または個人のデバイス戦略を実装できるようにする
* 組織が展示会のロビーにあるキオスクなどの制御しないデバイスやアプリから Office 365 にアクセスする従業員をサポートできるようにする

Intune が提供する主なツールには次のものがあります。
* **モバイル デバイス管理 (MDM)**: プロビジョニング、構成、監視、およびデバイスのワイプなどのアクションをデバイスで実行できるように、それらのデバイスを Intune に登録する機能。
* **モバイル アプリケーション管理 (MAM)**: ユーザーのモバイル アプリを公開、プッシュ、構成、セキュリティ保護、監視、および更新する機能。
* **モバイル アプリケーションのセキュリティ**: モバイル アプリの管理の一部として、会社のデータから個人のデータを分離し、会社のデータを選択的にワイプできるようにして、モバイル データをセキュリティ保護する機能。

これらのツールをさまざまに組み合わせて使用することで、上記の一般的なビジネス シナリオを可能にします。 たとえば、共有デバイスのシナリオでは、MDM を頻繁に使用します。 BYOD のシナリオは一般に MAM に依存します。 会社の電話のシナリオは両方に基づいて構築します。 ほとんどすべてのシナリオで、モバイル アプリケーションのセキュリティを利用します。

このドキュメント全体で、Intune が提供するツールを使用して、ビジネス シナリオをサポートする方法を説明しています。  さらに、Office 365、Azure AD、Azure RMS、および Microsoft Mobility Suite のその他の部分とこれらのツールを使用する方法についても説明します。 テクノロジの一般的な使用方法と環境で役立てる方法の大まかな概要に加えて、それらを実装する手順も提供します。 テクノロジ自体は柔軟性があるため、ここで説明しているもの以外にも、あらゆる種類のシナリオに適応できます。

### <a name="next-steps"></a>次のステップ
* [Intune の一般的な使用方法](common-ways-to-use-intune.md)を読む
* [Intune の 30 日間の評価版](get-started-with-a-30-day-trial-of-microsoft-intune.md)を使用して製品の理解を深める
* Intune の[技術的要件と機能](/intune/get-started/what-to-know-before-you-start-microsoft-intune)を調べる



<!--HONumber=Nov16_HO2-->


