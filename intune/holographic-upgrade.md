---
title: Windows Holographic for Business へのアップグレード
titleSuffix: Microsoft Intune
description: Windows Holographic を実行するデバイスを Windows Holographic for Business にアップグレードする方法について説明します
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1c6a2f4fc3e3cae171cea96520d075a659d4d1ca
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2019
ms.locfileid: "57566337"
---
# <a name="upgrade-devices-running-windows-holographic-to-windows-holographic-for-business"></a>Windows Holographic を実行するデバイスを Windows Holographic for Business にアップグレードする

Microsoft Intune には、デバイスの管理と保護に役立つ多くの設定が含まれています。 この記事では、Windows Holographic デバイスを Windows Holographic for Business にアップグレードするための設定の一覧を示して説明します。 このような設定は、デバイスにプッシュまたは展開される Intune のアップグレード構成プロファイルに作成されます。

モバイル デバイス管理 (MDM) ソリューションの一部として、これらの設定を使用して Windows Holographic デバイスをアップグレードします。 Microsoft HoloLens の場合、Commercial Suite を購入してアップグレードに必要なライセンスを入手できます。 詳細については、「[Windows Holographic for Business 機能のロック解除](https://docs.microsoft.com/hololens/hololens-upgrade-enterprise)」を参照してください。

この機能の詳細については、[Windows 10 エディションのアップグレードまたは S モードの有効化](edition-upgrade-configure-windows-10.md)に関するページを参照してください。

## <a name="before-you-begin"></a>始める前に

[デバイス構成プロファイルを作成します](edition-upgrade-configure-windows-10.md#create-the-profile)。

## <a name="edition-upgrade"></a>エディションのアップグレード

- **アップグレード後のエディション**: 選択**Windows 10 Holographic for Business**します。
- **[ライセンス ファイル]**: 提供された XML ライセンス ファイルを参照して選びます。

  ![Holographic for Business のライセンス情報を含む XML ファイル名を入力します](media/Holographic-edition-upgrade.png)
 
## <a name="next-steps"></a>次の手順

プロファイルは作成されましたが、まだ何も実行できない可能性があります。 必ず[プロファイルを割り当て](device-profile-assign.md)、[その状態を監視](device-profile-monitor.md)してください。

[Windows 10 以降](edition-upgrade-windows-settings.md)のデバイス用にエディションのアップグレード プロファイルを作成することもできます。
