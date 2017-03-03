---
title: "企業所有のデバイスの管理 | Microsoft Docs"
description: "企業所有のデバイスを、デバイスの種類、購入方法、組織のニーズに応じて、さまざまな方法で登録します。"
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 01/29/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2b60bbff-25e6-489b-9621-c71b4275fa06
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 521a37044d6721fe905db7740329688ba2c24b35
ms.openlocfilehash: ae077d80e05b33d625285d796917f4f6c153ca3f


---

# <a name="enroll-corporate-owned-devices-by-using-intune"></a>Intune を使用して企業所有のデバイスを登録する

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

組織所有または企業所有のデバイスを登録し、デバイスの種類、デバイスの購入方法、組織のニーズに応じて、さまざまな方法により Intune で管理することができます。 また、ポータル サイト アプリをインストールし、"Bring Your Own Device" (BYOD) シナリオのように、企業所有のデバイスを登録して管理することもできます。

既定では、すべてのプラットフォーム用のデバイスを Intune に登録することができます。 デバイスの登録をブロックするには、管理者資格情報を使用して [Microsoft Intune 管理ポータル](http://manage.microsoft.com)にサインインします。 **[管理]** > **[モバイル デバイス管理]** > **[登録ルール]** の順に選択し、登録をブロックするプラットフォームの該当するチェック ボックスをオフにします。

## <a name="enroll-corporate-owned-ios-devices"></a>企業所有の iOS デバイスの登録

企業所有デバイスの登録方法は、"Choose Your Own Device" (CYOD) シナリオに適しています。 CYOD 環境では、組織はユーザーが選択したデバイスに対する支払いと管理を行います。

ユーザーが複数の iOS デバイスから選択できるようにすれば、登録を事前に構成できるため、デバイスはユーザーが初めてオンにした時点から Intune で管理されます。 Intune は、[Apple のデバイス登録プログラム (DEP)](ios-device-enrollment-program-in-microsoft-intune.md) による登録、または Mac コンピューター上の Apple Configurator ツールを使用した[直接](ios-direct-enrollment-in-microsoft-intune.md)登録、または[セットアップ アシスタント](ios-setup-assistant-enrollment-in-microsoft-intune.md)による登録をサポートしています。

企業所有の iOS デバイスの登録方法については、[こちら](enroll-corporate-owned-ios-devices-in-microsoft-intune.md)を参照してください。

## <a name="create-a-device-enrollment-manager-account"></a>デバイス登録マネージャー アカウントを作成する

Intune で単一のユーザー デバイス登録マネージャー (DEM) アカウントを作成し、組織の多数のモバイル デバイスを管理することができます。 DEM アカウントを作成すると、指定されたアカウント マネージャーは、標準ユーザーが登録できる 15 台を超えるデバイスを登録できます。

DEM アカウントを使用すれば、単一の特定ユーザーが使用していないデバイスのみを登録することできます。 この種のデバイスは、POS アプリやユーティリティ アプリなどには適していますが、電子メールや会社のリソースにアクセスする必要があるユーザーには適していません。

[DEM アカウントを使用して企業所有のデバイスを登録する方法については、こちら](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)を参照してください。

## <a name="enroll-corporate-owned-windows-10-enterprise-devices"></a>企業所有の Windows 10 Enterprise デバイスの登録

組織で Azure Active Directory Premium または Microsoft Enterprise Mobility Suite を使用している場合は、[Windows 10 Enterprise デバイスを登録](https://docs.microsoft.com/active-directory/active-directory-azureadjoin-windows10-devices-overview)できます。 ユーザーがデバイスで職場または学校アカウントを追加すると、デバイスは自動的に "企業所有" としてタグ付けされます。

## <a name="import-imei-numbers"></a>IMEI 番号のインポート

多くのモバイル デバイス製造元が、デバイスに IMEI (International Mobile Equipment Identity) という一意の番号を使用しています。 組織が所有するデバイスの IMEI 番号をインポートすることができます。 デバイスが Intune の管理対象になると、企業所有のデバイスとしてタグ付けされます。

IMEI 番号を使用して企業所有のデバイスにタグを付ける方法については、[こちら](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md)を参照してください。

## <a name="identify-a-device-as-corporate-owned"></a>デバイスの企業所有としての識別

Intune は、次のいずれかの条件を満たす場合、デバイスを "企業" と認識します。

 - デバイスが [DEM アカウントを使用して登録](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)されている (すべてのプラットフォーム)。
 - デバイスが [Apple DEP](ios-device-enrollment-program-in-microsoft-intune.md) または [Apple Configurator](ios-setup-assistant-enrollment-in-microsoft-intune.md) を使用して登録されている (iOS のみ)。
 - デバイスの製造元が [IMEI 番号を使用してデバイスを事前に宣言している](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md) (IMEI 番号を使用するすべてのプラットフォーム)。
 - デバイスが [Azure Active Directory または Enterprise Mobility Suite に Windows 10 Enterprise デバイスとして](https://docs.microsoft.com/active-directory/active-directory-azureadjoin-windows10-devices-overview)登録されている (Windows 10 のみ)。

デバイスに企業とタグが付けられると、管理コンソールのそのデバイス レコードの **[所有権]** 列に **[企業]** と表示されます。 



<!--HONumber=Jan17_HO5-->


