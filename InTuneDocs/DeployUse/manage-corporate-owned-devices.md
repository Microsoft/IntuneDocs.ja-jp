---
title: "企業所有のデバイスの管理 | Microsoft Intune"
description: 
keywords: 
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2b60bbff-25e6-489b-9621-c71b4275fa06
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 69cf07aa0747448e0ef3384b5b5132e0e76aed45
ms.openlocfilehash: e07053b9b26afacc03e45f2cb104eda6088a1e05


---

# Microsoft Intune で企業所有のデバイスを登録する
組織または企業所有のデバイス (COD) は、デバイス、購入方法、組織のニーズに応じて多様な方法で Intune の管理対象にすることができます。

## 企業所有の iOS デバイス
これらの登録方法は、組織がユーザーのデバイスを購入し、デバイスの管理は組織が行う "Choose Your Own Device (CYOD)" シナリオに適しています。 組織が iOS デバイスを購入した場合、登録を事前に構成し、ユーザーが初めて起動したときからデバイスを管理対象にすることができます。 Intune は、[Apple のデバイス登録プログラム (DEP)](ios-device-enrollment-program-in-microsoft-intune.md) による登録、または Mac コンピューターで実行されている Apple Configurator ツールを使用した[直接](ios-direct-enrollment-in-microsoft-intune.md)登録、または[セットアップ アシスタント](ios-setup-assistant-enrollment-in-microsoft-intune.md)による登録をサポートしています。

[企業所有の iOS デバイスの登録](enroll-corporate-owned-ios-devices-in-microsoft-intune.md)

## デバイス登録マネージャー
組織は、Intune を使用して、デバイス登録マネージャー アカウントという 1 つのユーザー アカウントで多数のモバイル デバイスを管理できます。 通常のユーザーが登録できる既定の標準デバイス数は 5 台ですが、デバイス登録マネージャー アカウントを作成すると、マネージャーはそのアカウントを使用して 5 台を超える台数を登録できます。 デバイス登録マネージャーを使用したデバイスの登録は、特定のユーザーが使用していないデバイスにのみ利用できます。 このようなデバイスは、たとえば POS アプリやユーティリティ アプリには適していますが、電子メールや会社のリソースにアクセスする必要がある場合には適していません。

[デバイス登録マネージャーを使った企業所有のデバイスの登録](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)

## International Mobile Equipment Identity (IMEI)
一意の IMEI (国際移動体装置識別番号) は、多くのモバイル デバイス製造元が採用している共通のデバイス プロパティです。 Intune 管理者は、会社が所有するデバイスの IMEI をインポートできます。 デバイスが Intune の管理対象になると、企業所有のデバイスというタグを付け、適切なポリシーの対象にすることができます。

[IMEI (国際移動体装置識別番号) を使って企業所有のデバイスを指定する](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md)



<!--HONumber=Jun16_HO5-->


