---
title: "企業所有のデバイスの管理 | Microsoft Intune"
description: "企業所有のデバイス (COD) を、デバイスや購入方法、組織のニーズに応じて多様な方法で管理対象にする。"
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2b60bbff-25e6-489b-9621-c71b4275fa06
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ecfeb73efed4a47256275120c52de232c556adfe
ms.openlocfilehash: 58efadf2f9fc34a31070aff93e86083583630caa


---

# Microsoft Intune で企業所有のデバイスを登録する
組織または企業所有のデバイス (COD) は、デバイス、購入方法、組織のニーズに応じて多様な方法で Intune の管理対象にすることができます。 また、企業所有のデバイスは、ポータル サイト アプリを "Bring Your Own Device" (BYOD) シナリオでインストールすることで登録および管理できます。

## 企業所有の iOS デバイス
これらの登録方法は、組織がユーザーのデバイスを購入し、デバイスの管理は組織が行う "Choose Your Own Device (CYOD)" シナリオに適しています。 組織が iOS デバイスを購入した場合、登録を事前に構成し、ユーザーが初めて起動したときからデバイスを管理対象にすることができます。 Intune は、[Apple のデバイス登録プログラム (DEP)](ios-device-enrollment-program-in-microsoft-intune.md) による登録、または Mac コンピューターで実行されている Apple Configurator ツールを使用した[直接](ios-direct-enrollment-in-microsoft-intune.md)登録、または[セットアップ アシスタント](ios-setup-assistant-enrollment-in-microsoft-intune.md)による登録をサポートしています。

[企業所有の iOS デバイスの登録](enroll-corporate-owned-ios-devices-in-microsoft-intune.md)

## デバイス登録マネージャー
組織は、Intune を使用して、デバイス登録マネージャー アカウントという 1 つのユーザー アカウントで多数のモバイル デバイスを管理できます。 通常のユーザーが登録できる既定の標準デバイス数は 5 台ですが、デバイス登録マネージャー アカウントを作成すると、マネージャーはそのアカウントを使用して 5 台を超える台数を登録できます。 デバイス登録マネージャーを使用したデバイスの登録は、特定のユーザーが使用していないデバイスにのみ利用できます。 このようなデバイスは、たとえば POS アプリやユーティリティ アプリには適していますが、電子メールや会社のリソースにアクセスする必要がある場合には適していません。

[デバイス登録マネージャーを使った企業所有のデバイスの登録](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)

## 企業所有の Windows 10 デスクトップの登録

組織で Azure Active Directory Premium (AADP) または Enterprise Management Suite (EMS) を所有している場合は、[エンタープライズ向け Windows 10 を登録](https://docs.microsoft.com/active-directory/active-directory-azureadjoin-windows10-devices-overview)でき、ユーザーが職場または学校アカウントを追加するときに、これらは自動的に "企業所有" としてタグ付けされます。

## デバイスの企業所有としての識別

企業所有のデバイスは、デバイス一覧の **[Ownership (所有権)]** で **[Corporate (会社)]** として一覧表示されます。 企業所有のデバイスは次の方法で識別できます。

 - [デバイス登録マネージャー (DEM) を使用した登録](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)
 - Apple の [デバイス登録プログラム (DEP)](ios-device-enrollment-program-in-microsoft-intune.md) または [Apple Configurator](ios-setup-assistant-enrollment-in-microsoft-intune.md) を使用した登録
 - [IMEI 番号を使用したデバイスの事前宣言](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md)
 - [Windows 10 デバイスの Azure Active Directory/Enterprise Management Suite 登録](https://docs.microsoft.com/active-directory/active-directory-azureadjoin-windows10-devices-overview)

### International Mobile Equipment Identity (IMEI)

一意の IMEI (国際移動体装置識別番号) は、多くのモバイル デバイス製造元が採用している共通のデバイス プロパティです。 Intune 管理者は、会社が所有するデバイスの IMEI をインポートできます。 デバイスが Intune の管理対象になると、企業所有のデバイスとしてタグ付けされます。

[IMEI (国際移動体装置識別番号) を使って企業所有のデバイスを指定する](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md)



<!--HONumber=Jul16_HO4-->


