---
title: "macOS デバイス向けの Intune カスタム設定 | Intune Azure プレビュー | Microsoft Docs"
description: "Intune Azure プレビュー: macOS カスタム プロファイルで使用できる設定について説明します。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 68100ea5-7d9b-4c0b-8df7-b9a24b2442c8
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4d095506215b775d56d172e9aabae1737757310
ms.openlocfilehash: 13648aa35057201ac7420e2f1d334aee206605fe
ms.lasthandoff: 02/16/2017


---

# <a name="custom-settings-for-macos-devices-in-microsoft-intune"></a>Microsoft Intune での macOS デバイス向けのカスタム設定

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Microsoft Intune の macOS カスタム プロファイルを使用して、[Apple Configurator ツール](https://itunes.apple.com/app/apple-configurator-2/id1037126344?mt=12)で作成した設定を macOS デバイスに展開します。 このツールを使用すると、これらのデバイスの動作を制御する多くの設定を作成し、構成プロファイルにエクスポートすることができます。 その後、この構成プロファイルを Intune macOS カスタム プロファイルにインポートし、組織内のユーザーとデバイスに設定を割り当てることができます。

この機能を使用すれば、他の Intune プロファイルの種類で構成できない macOS 設定を展開することができます。


1. 「[How to configure custom device settings in Microsoft Intune (Microsoft Intune でカスタム デバイス設定を構成する方法)](how-to-configure-custom-settings.md)」の手順に従って開始します。
2. **[プロファイルを作成します]** ブレードで、次を指定します。

- **[カスタム構成プロファイル名]** - プロファイルの名前を指定します。この名前が、デバイスや Intune の状態に表示されます。
- **[構成プロファイル名]** - Apple Configurator を使用して作成した構成プロファイルを指定します。
Apple Configurator ツールからエクスポートした設定に、macOS カスタム ポリシーを展開するデバイス上の macOS のバージョンとの互換性があることを確認します。 互換性のない設定を解決する方法については、[Apple 開発者](https://developer.apple.com/) Web サイトで「**Configuration Profile Reference**」 (構成プロファイル リファレンス) および「**Mobile Device Management Protocol Reference**」 (モバイル デバイス管理プロトコル リファレンス) を検索してください。

インポートしたファイルは、ブレードの **[ファイルの内容]** 領域に表示されます。

