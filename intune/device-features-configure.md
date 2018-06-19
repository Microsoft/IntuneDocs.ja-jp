---
title: Microsoft Intune - Azure での iOS または macOS デバイス プロファイルの作成 | Microsoft Docs
description: Microsoft Intune で iOS または macOS デバイス プロファイルを追加または作成し、AirPrint、AirPlay、ホーム画面のレイアウト、アプリの通知、共有デバイス、シングル サインイン、Web コンテンツ フィルター設定を構成します。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d823a7f8d3478c0ff6c0049a6bbaa76bb4247479
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31022035"
---
# <a name="add-ios-or-macos-device-feature-settings-in-intune"></a>Intune での iOS または macOS デバイスの機能設定の追加

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

デバイスの機能を使用して、次のような iOS と macOS デバイスの多くの設定と機能を制御することができます。

- AirPrint と AirPlay の設定
- ホーム画面のレイアウト
- アプリからの通知
- 共有デバイスの構成
- シングル サインオンのセットアップ
- Web コンテンツのフィルター処理

この記事では、iOS デバイスの機能とプロファイルの基本的な構成方法について説明します。 その後で、他の記事を参照して、デバイスのプラットフォームに固有の設定を構成することができます。

## <a name="create-a-device-profile"></a>デバイス プロファイルの作成

1. [Azure ポータル](https://portal.azure.com)にサインインします。
2. **[すべてのサービス]** を選択し、**[Intune]** をフィルターとして適用し、**[Microsoft Intune]** を選択します。
3. **[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** の順に選択します。
4. 次のプロパティを入力します。

   - **名前**: 新しいプロファイルのわかりやすい名前を入力します。
   - **説明**: プロファイルの説明を入力します  (これは省略可能ですが、入力することをお勧めします)。
   - **プラットフォーム**: プラットフォームの種類を選択します。
     - **Android**
     - **macOS**
   - **プロファイルの種類**: **[デバイス機能]** を選択します。
   - **設定**: 設定は、選択したプラットフォームによって異なります。 次の記事では、ファイルの種類ごとの設定について説明します。

     - [iOS および macOS 用 AirPrint の設定](air-print-settings-ios-macos.md)
     - [iOS 用 AirPlay の設定](airplay-settings-ios.md)
     - [iOS 用ホーム画面のレイアウト設定](home-screen-settings-ios.md)
     - [iOS 用アプリの通知設定](app-notification-settings-ios.md)
     - [iOS 用共有デバイス構成設定](shared-device-settings-ios.md)
     - [iOS 用 Intune のデバイス シングル サインオンを構成する](sso-ios.md)
     - [iOS 用 Web コンテンツ フィルター設定](web-content-filter-settings-ios.md)

5. 完了したら、**[OK]** を選択し、**[作成]** を選択して変更を保存します。

プロファイルが作成され、リストに表示されます。

## <a name="next-step"></a>次の手順

このプロファイルをグループに割り当てるには、[デバイス プロファイルを割り当てる方法](device-profile-assign.md)に関するページを参照してください。