---
title: "Intune デバイス機能設定の構成"
titleSuffix: Azure portal
description: "Intune を使用して管理対象デバイスの機能を構成する方法について説明します。\""
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 12/7/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 42f9b104-c1f6-4dfc-8aa4-1d33e1eaf61f
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ea280ac6858485aa4e3d64d11835f002c5bb35ca
ms.sourcegitcommit: 3b397b1dcb780e2f82a3d8fba693773f1a9fcde1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/12/2017
---
# <a name="how-to-configure-device-feature-settings-in-microsoft-intune"></a>Microsoft Intune でデバイスの機能設定を構成する方法

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

デバイス制約では、AirPrint、通知、共有デバイス構成など、iOS デバイスと macOS デバイスの機能を制御できます。

このトピックでは、デバイスの機能プロファイルを構成する基本的な方法について説明します。その後、デバイスごとの詳細については、各プラットフォームのトピックを参照してください。

## <a name="create-a-device-profile-containing-device-restriction-settings"></a>デバイスの制限設定を含むデバイス プロファイルの作成

1. Azure ポータルにサインインします。
2. **[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
3. **[Intune]** ブレードで、**[デバイス構成]** を選択します。
2. **[デバイス構成]** ブレードで、**[管理]** > **[プロファイル]** の順に選択します。
3. [プロファイル] ブレードで、**[プロファイルを作成します]** を選択します。
4. **[プロファイルを作成します]** ブレードで、デバイスの機能プロファイルの**名前**と**説明**を入力します。
5. **[プラットフォーム]** ドロップダウン リストで、設定を適用するデバイス プラットフォームを選択します。 現時点では、デバイス機能に対応している次のいずれかのプラットフォームを選択できます。
    - **iOS**
    - **macOS**
6. **[プロファイルの種類]** ドロップダウン リストで、**[デバイス機能]** を選択します。 
7. 選択したプラットフォームによって構成できる設定が異なります。 各プラットフォームの詳細な設定については、次のいずれかのトピックを参照してください。
    - [iOS および macOS 用 AirPrint の設定](air-print-settings-ios-macos.md)
    - [iOS 用 AirPlay の設定](airplay-settings-ios.md)
    - [iOS 用ホーム画面のレイアウト設定](home-screen-settings-ios.md)
    - [iOS 用アプリの通知設定](app-notification-settings-ios.md)
    - [iOS 用共有デバイス構成設定](shared-device-settings-ios.md)
    - [iOS 用 Intune のデバイス シングル サインオンを構成する](sso-ios.md)
    - [iOS 用 Web コンテンツ フィルター設定](web-content-filter-settings-ios.md)

8. 完了したら、**[プロファイルの作成]** ブレードに戻り、**[作成]** をクリックします。

プロファイルが作成され、プロファイルの一覧ブレードに表示されます。
このプロファイルをグループに割り当てる場合は、[デバイス プロファイルを割り当てる方法](device-profile-assign.md)に関する記事を参照してください。



