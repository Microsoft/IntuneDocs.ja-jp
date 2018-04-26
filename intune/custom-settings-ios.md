---
title: iOS を実行するデバイス向けの Microsoft Intune のカスタム設定
titleSuffix: ''
description: Microsoft Intune の iOS カスタム プロファイルで使用できる設定について説明します。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e0ae4e757264465043ee6992033710c5a81d7157
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="microsoft-intune-custom-device-settings-for-devices-running-ios"></a>iOS を実行するデバイス向けの Microsoft Intune カスタム デバイス設定

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Microsoft Intune の iOS カスタム プロファイルを使用して、[Apple Configurator ツール](https://itunes.apple.com/app/apple-configurator-2/id1037126344?mt=12)で作成した設定を iOS デバイスに割り当てます。 このツールを使用すると、これらのデバイスの動作を制御する多くの設定を作成し、構成プロファイルにエクスポートすることができます。 その後、この構成プロファイルを Intune iOS カスタム プロファイルにインポートし、組織内のユーザーとデバイスに設定を割り当てることができます。

この機能を使用すれば、他の Intune プロファイルの種類で構成できない iOS 設定を割り当てることができます。


1. 「[How to configure custom device settings in Microsoft Intune (Microsoft Intune でカスタム デバイス設定を構成する方法)](custom-settings-configure.md)」の手順に従って開始します。
2. **[カスタム構成プロファイル]** ウィンドウで、次の設定をそれぞれ構成します。

- **[カスタム構成プロファイル名]** - プロファイルの名前を指定します。この名前がデバイスや Intune の状態に表示されます。
- **[構成プロファイル名]** - Apple Configurator を使用して作成した構成プロファイルを指定します。
Apple Configurator ツールからエクスポートした設定に、iOS カスタム ポリシーを割り当てるデバイス上の iOS のバージョンとの互換性があることを確認します。 互換性のない設定を解決する方法については、[Apple 開発者](https://developer.apple.com/) Web サイトで「**Configuration Profile Reference**」 (構成プロファイル リファレンス) および「**Mobile Device Management Protocol Reference**」 (モバイル デバイス管理プロトコル リファレンス) を検索してください。

インポートしたファイルは、ウィンドウの **[ファイルの内容]** 領域に表示されます。
