---
title: Microsoft Intune でカスタム デバイス設定を使用する - Azure | Microsoft Docs
description: Microsoft Intune を使用し、Windows Phone、Windows 8.1、Windows 10 以降、Android、Android Enterprise、macOS、iOS デバイスのカスタム設定を使用するプロファイルを追加または作成します
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/05/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1c815a2c911dba6d17fc864b446122931fa88e91
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "73755381"
---
# <a name="create-a-profile-with-custom-settings-in-intune"></a>Intune でカスタム設定を持つプロファイルを作成する

## <a name="what-are-custom-profiles"></a>カスタム プロファイルとは

Microsoft Intune には、デバイスのさまざまな機能を制御する多くの組み込み設定が含まれます。 カスタム プロファイルを作成することもできます。 カスタム プロファイルは、Intune に組み込まれていないデバイスの設定と機能を使用する場合に最適です。 これらのプロファイルには、組織のデバイスを制御するための機能と設定が含まれます。 たとえば、すべての iOS デバイスに対して同じ機能を設定するカスタム プロファイルを作成できます。

構成プロファイルの詳細については、「[Microsoft Intune のデバイス プロファイルとは](device-profiles.md)」をご覧ください。 

この記事には、Android、Android エンタープライズ、iOS、macOS、および Windows 用のカスタム プロファイルの作成に関するリンクが含まれます。

## <a name="available-platforms"></a>使用可能なプラットフォーム

カスタム設定は、プラットフォームごとに構成が異なります。 たとえば、Android デバイスと Windows デバイスで機能を制御するには、Open Mobile Alliance Uniform Resource Identifier (OMA-URI) 値を入力できます。 Apple デバイスでは、[Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) または [Apple Profile Manager](https://support.apple.com/profile-manager) で作成したファイルをインポートできます。

カスタム プロファイルは、組み込みプロファイルと同じように作成され、次のプラットフォームで使用できます。

- [Android](../custom-settings-android.md)
- [Android エンタープライズ](../custom-settings-android-for-work.md)
- [iOS/iPadOS](custom-settings-ios.md)
- [macOS](custom-settings-macos.md)
- [Windows 10](custom-settings-windows-10.md)
- [Windows Holographic for Business](custom-settings-windows-holographic.md)
- [Windows Phone 8.1](custom-settings-windows-phone-8-1.md)

## <a name="next-steps"></a>次の手順

プラットフォームを選択して始めてください。

- [Android](../custom-settings-android.md)
- [Android エンタープライズ](../custom-settings-android-for-work.md)
- [iOS/iPadOS](custom-settings-ios.md)
- [macOS](custom-settings-macos.md)
- [Windows 10](custom-settings-windows-10.md)
- [Windows Holographic for Business](custom-settings-windows-holographic.md)
- [Windows Phone 8.1](custom-settings-windows-phone-8-1.md)
