---
title: "Microsoft Intune デバイス機能設定を構成する"
titleSuffix: 
description: "Microsoft Intune を使用して管理対象デバイスの機能を構成する方法について説明します。"
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/2/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6cd646976deb1599c4cbc9154b6f2a487029dd79
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2018
---
#<a name="configure-device-feature-settings-in-microsoft-intune"></a>Microsoft Intune でデバイス機能設定を構成する

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

デバイス機能では、AirPrint、通知、共有デバイス構成など、iOS デバイスと macOS デバイスの機能を制御できます。

この記事の情報を使用して、デバイス機能プロファイルを構成する基本的な方法について学習します。その後、デバイスの詳細について、各プラットフォームの記事を参照してください。

## <a name="create-a-device-profile-containing-device-feature-settings"></a>デバイス機能設定を含むデバイス プロファイルを作成する

1. サインイン、 [Azure ポータル](https://portal.azure.com)します。
2. **[すべてのサービス]** > **[Intune]** の順に選択します。 Intune は **[監視 + 管理]** セクションにあります。
3. **[Intune]** ページで、**[デバイス構成]** を選択します。
2. **[デバイス構成]** ページの **[管理]** セクションで、**[プロファイル]** を選択します。
3. プロファイル ページで、**[プロファイルの作成]** を選択します。
4. **[プロファイルの作成]** ページで、デバイス機能プロファイルの **[名前]** と **[説明]** を入力します。
5. **[プラットフォーム]** ドロップダウン リストで、設定を適用するデバイス プラットフォームを選択します。 現時点では、デバイス機能に対応している次のいずれかのプラットフォームを選択できます。
    - **Android**
    - **macOS**
6. **[プロファイルの種類]** ドロップダウン リストで、**[デバイス機能]** を選択します。 
7. 選択したプラットフォームによって構成できる設定が異なります。 各プラットフォームの詳細な設定については、次のいずれかの記事を参照してください。
    - [iOS および macOS 用 AirPrint の設定](air-print-settings-ios-macos.md)
    - [iOS 用 AirPlay の設定](airplay-settings-ios.md)
    - [iOS 用ホーム画面のレイアウト設定](home-screen-settings-ios.md)
    - [iOS 用アプリの通知設定](app-notification-settings-ios.md)
    - [iOS 用共有デバイス構成設定](shared-device-settings-ios.md)
    - [iOS 用 Intune のデバイス シングル サインオンを構成する](sso-ios.md)
    - [iOS 用 Web コンテンツ フィルター設定](web-content-filter-settings-ios.md)

8. 完了したら、**[OK]** を選択し、**[プロファイルの作成]** ページに戻り、**[作成]** を選択します。

プロファイルが作成され、プロファイルの一覧ページに表示されます。
## <a name="next-steps"></a>次の手順

このプロファイルをグループに割り当てる場合は、「[デバイス プロファイルを割り当てる方法](device-profile-assign.md)」を参照してください。



